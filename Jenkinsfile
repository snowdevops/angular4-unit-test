pipeline {
    agent any
    stages {
        stage("Checkout code") {
            steps {
                snDevOpsStep()
                checkout scm
            }
        }
        stage("Build and unit test") {
            steps {
                snDevOpsStep()
                sh 'ng build'
                sh 'ng test'
            }
            post {
       		   always {
          		    junit '**/build/reports/e2e/*.xml'
        	    }
            }
        } 
        stage("e2e test") {
            steps {
                snDevOpsStep()
                sh 'ng serve'
                sh 'ng e2e'
            }
            post {
       		   always {
          		    junit '**/build/reports/e2e/*.xml'
        	    }
            }
        }      
    }    
}
