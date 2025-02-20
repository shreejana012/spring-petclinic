pipeline {
    agent any
    triggers {
        cron('H/3 * * * 4')
    }
    stages {
        stage('Checkout') {
            steps {
                echo 'Checking out the code from GitHub...'
                git 'https://github.com/shreejana012/spring-petclinic'
            }
        }
        stage('Build') {
            steps {
                echo 'Building the project using Maven...'
                script {
                    sh './mvnw clean install'
                }
            }
        }
        stage('Generate Jacoco Code Coverage') {
            steps {
                echo 'Running tests to generate Jacoco code coverage report...'
                script {
                    sh './mvnw test'
                }
            }
        }
        stage('Archive Jacoco Report') {
            steps {
                echo 'Archiving the Jacoco code coverage report...'
                archiveArtifacts '**/target/site/jacoco/*.xml'
            }
        }
    }
}
