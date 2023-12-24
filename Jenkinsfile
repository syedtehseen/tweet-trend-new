pipeline {
    agent {
        node {
            label 'maven'
        }
    }

    stages {
        stage('Clone Repo') {
            steps {
                git branch: 'main', url: 'https://github.com/ravdy/tweet-trend-new.git'
            }
        }

        stage('SonarQube Analysis') {
            environment {
                scannerHome = tool 'dops-sonar-scanner'
            }
            steps{
                withSonarQubeEnv('dops-sonarcube-server') {
                    sh "${scannerHome}/bin/sonar-scanner"
                }
            }
        }
    }
}
