pipeline {
    agent {
        docker {
            image 'python:3.11'
        }
    }

    stages {

        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Install dependencies') {
            steps {
                sh '''
                    python -m pip install --upgrade pip
                    pip install -r requirements.txt
                '''
            }
        }

        stage('Run tests') {
            steps {
                sh 'pytest -v'
            }
        }
    }

    post {
        success {
            echo '✅ Tests passed'
        }
        failure {
            echo '❌ Tests failed'
        }
    }
}
