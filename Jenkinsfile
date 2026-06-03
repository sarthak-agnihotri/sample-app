pipeline {
    agent any

    parameters {
        string(name: 'GIT_BRANCH', defaultValue: 'main')
        string(name: 'APP_VERSION', defaultValue: '1.0')
    }

    environment {
        BUILD_DIR='target'
    }

    stages {

        stage('Checkout') {
            steps {
                echo "Checking out ${params.GIT_BRANCH}"
            }
        }

        stage('Build') {
            steps {
                bat 'mvn clean compile'
            }
        }

        stage('Unit Testing') {
            steps {
                bat 'mvn test'
            }
        }

        stage('Code Quality Check') {
            steps {
                bat 'mvn verify'
            }
        }

        stage('Package') {
            steps {
                bat 'mvn package'
            }
        }

        stage('Archive Artifact') {
            steps {
                archiveArtifacts artifacts: 'target/*.jar'
            }
        }
    }
}