pipeline{
    agent any
    stages{
        stage("Pull images"){
            steps{
                bat "docker pull samirshh9/apiapp-docker:latest"
                bat "docker pull samirshh9/restassured-docker:latest"
            }
        }
        stage("Run API App"){
            steps{
                bat "docker-compose up -d apiapp"
            }
        }
        stage("Run API Tests"){
            steps{
                bat "docker-compose up restassured"
            }
        }
    }
    post{
        always{
            archiveArtifacts artifacts: 'Artifacts/**'
            bat "docker-compose down"
        }
    }
}