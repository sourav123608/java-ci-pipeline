pipeline {

    agent any

        tools {
        jdk 'Java21'
        maven 'Maven3'
    }


    stages {

        stage('Checkout SCM') {
            steps {
                git 'https://github.com/sourav123608/java-ci-pipeline.git'
            }
        }

        stage('Build') {
            steps {
                sh 'mvn clean package -DskipTests'
            }
        }

        stage('Test') {
            steps {
                sh 'mvn test'
            }
        }

        stage('Archive Artifact') {
            steps {
                archiveArtifacts artifacts: 'target/*.jar',
                             fingerprint: true
            }
        }

    }

    post {

        success {
            echo 'CI Pipeline completed successfully!'
        }

        failure {
            echo 'CI Pipeline failed!'
        }

        always {
            junit 'target/surefire-reports/*.xml'
        }

    }
}
