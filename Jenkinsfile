pipeline {
  agent any

  tools {
    maven 'M3'
  }

  stages {
    stage('Build') {
      steps {
        sh 'mvn -v'
        sh 'mvn -Dmaven.test.failure.ignore=false clean test'
      }
    }
  }

  post {
    always {
      junit 'target/surefire-reports/*.xml'
      archiveArtifacts artifacts: 'target/*.jar', fingerprint: true
    }
  }
}
