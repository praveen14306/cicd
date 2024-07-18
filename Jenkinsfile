pipeline {
    agent any

    environment {
        KONG_ADMIN_URL = "http://localhost:8001"
    }


    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('SonarQube Analysis') {
            steps {
                }
            }
        }

        stage('Validate Configuration') {
            steps {
                sh 'deck validate kong.yml'
            }
        }

        stage('Deploy Configuration') {
            steps {
                sh 'docker cp kong.yml kong:/etc/kong/kong.yml'
                sh 'docker exec kong kong reload -c /etc/kong/kong.yml'
            }
        }
    }
}
