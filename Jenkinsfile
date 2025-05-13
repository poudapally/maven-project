pipeline {
    agent any
    environment {
        PATH = "/opt/maven/bin:$PATH"
    }
    stages {
        stage("build") {
            steps {
                sh 'mvn clean install'

            }
        }
        stage('SonarQube analysis') {
            environment {
                scannerHome = tool 'Jenkins-sonarQube scanner'
            }
            steps {
                withSonarQubeEnv('Jenkins-sonarqube') {
                    sh "${scannerHome}/bin/sonar-scanner"
                }
            }
        }
    }
}
