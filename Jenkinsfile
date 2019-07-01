pipeline {
	  agent {
	    docker {
	      image 'node:10-alpine'
	      args '-p 20001-20100:3000'
	    }
	  }
	  environment {
	    CI = 'true'
	    HOME = '.'
	    npm_config_cache = 'npm-cache'
	  }
	  stages {
	    stage('Install Packages') {
	      steps {
	        //sh 'npm install'
	      }
	    }
	   stage('Test and Build') {
	      parallel {
	        stage('Run Tests') {
	          steps {
	            //sh 'npm run test'
	          }
	        }
	        stage('Create Build Artifacts') {
	          steps {
	            //sh 'npm run build'
	          }
	        }
	      }
	    }
	    stage('Deployment') {
	      parallel {
	        stage('Staging') {
	          /*when {
	            branch 'staging'
	          }
	          steps {
	            withAWS(region:'<your-bucket-region>',credentials:'<AWS-Staging-Jenkins-Credential-ID>') {
	              s3Delete(bucket: '<bucket-name>', path:'**/*')
	              s3Upload(bucket: '<bucket-name>', workingDir:'build', includePathPattern:'**/*');
	            }
				*/
	            mail(subject: 'Staging Build', body: 'New Deployment to Staging', to: 'sriswaminathan.vanarasi@ge.com')
	          }
	        }
	        stage('Production') {
	          /*when {
	            branch 'master'
	          }*/
	          steps {
	            
	            }
	            mail(subject: 'Production Build', body: 'New Deployment to Production', to: 'sriswaminathan.vanarasi@ge.com')
	          }
	        }
	      }
	    }
	  }
	}


