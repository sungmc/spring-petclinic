pipeline {
  agent { docker 'maven:3.5-alpine'}
  tools {
    maven 'Maven_3.5' 
  }
  stages {
    stage ('Checkout') {
      steps {
        git 'https://github.com/sungmc/spring-petclinic.git'
      }
    }
    stage ('Build') {
      steps {
        sh 'mvn clean package'
        junit '**/target/surefire-reports/TEST-*.xml'
        archieveArtifacts artifacts: 'target/*.jar', fingerprint: true  
      }
    }
  }
}
