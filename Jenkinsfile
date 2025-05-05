pipeline {
    agent any
    
    tools {
        maven 'Maven 3.8.1'  // Must match Jenkins Maven installation
        jdk 'jdk11'          // Must match Jenkins JDK installation
    }

    stages {
        stage('Checkout') {
            steps {
                checkout scm  // Automatically checks out your repo
            }
        }
        
        stage('Build & Test') {
            steps {
                sh 'mvn clean test'
            }
            post {
                always {
                    junit '**/target/surefire-reports/*.xml'
                }
            }
        }
    }
    
    post {
        always {
            echo 'Pipeline completed. See test results above.'
        }
    }
}
