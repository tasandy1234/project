pipeline {
  agent any
  tools {
    Maven 'maven 3.8.8'
  }

  stages {
      stage('clone repo') {
            steps {
              git branch: 'main', url: 'https://github.com/tasandy1234/project.git'
            }
      }
      stage('Build Artifact') {
            steps {
              sh "mvn clean package -DskipTests=true"
              archive 'target/*.jar' 
            }  
       }
      stage('Test Maven - JUnit') {
            steps {
              sh "mvn test"
            }
            post{
              always{
                junit 'target/surefire-reports/*.xml'
              }
            }
        }
        

     }
}
