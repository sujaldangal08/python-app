pipeline {
    agent docker-agent
    
    environment {
        // Define your environment variable for docker-compose file location
        DOCKER_COMPOSE_FILE = 'docker-compose.yml'
    }

    stages {
        stage('Checkout Code') {
            steps {
                // Checkout the code from your GitHub repository
                git 'https://github.com/sujaldangal08/python-app.git'
            }
        }

        stage('Run Docker Compose') {
            steps {
                script {
                    // Run docker-compose up in detached mode
                    sh 'docker-compose -f $DOCKER_COMPOSE_FILE up -d'
                }
            }
        }
    }

    post {
        success {
            // Actions after a successful build
            echo 'Docker Compose services started successfully!'
        }
        failure {
            // Actions if the build fails
            echo 'Failed to start Docker Compose services.'
        }
        always {
            // Always run for cleanup or other final actions
            echo 'Pipeline complete.'
        }
    }
}

