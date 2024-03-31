pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                script {
                    container('maven') {
                        sh 'mvn compile'
                    }
                }
            }
        }
        stage('Test') {
            steps {
                script {
                    container('maven') {
                        sh 'mvn test'
                    }
                }
            }
        }
        stage('Package') {
            steps {
                script {
                    container('maven') {
                        sh 'mvn package -DskipTests'
                    }
                }
            }
        }
        stage('Deploy to Dev') {
            steps {
                script {
                    sh "echo done"
                }
            }
        }
    }

    post {
        always {
            archiveArtifacts allowEmptyArchive: true, artifacts: 'target/*.jar'
        }
    }
}
