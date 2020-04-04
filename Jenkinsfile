pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                sh "mvn sonar:sonar   -Dsonar.projectKey=test   -Dsonar.host.url=http://34.69.247.160:9000   -Dsonar.login=325a98e8391c03cce8dc019a4a9193011863b42a"
            }
        }
        stage('Test') {
            steps {
                sh 'mvn test'
            }
            post {
                always {
                    junit 'target/surefire-reports/*.xml'
                }
            }
        }
        stage('Deliver') {
            steps {
                sh './jenkins/scripts/deliver.sh'
            }
        }
    }
}
