pipeline {
    agent {
        kubernetes {
            yaml '''
                apiVersion: v1
                kind: Pod
                spec:
                  containers:
                    - name: maven
                      image: maven:3.9.5-eclipse-temurin-17-alpine
                      command:
                        - sleep
                      args:
                        - 9999999
                 '''
            defaultContainer 'maven'
        }
    }
    stages {
        stage('Build') {
            steps {           
                sh "mvn -X clean install -Dmaven.repo.local=/tmp/m2 -s settings.xml"
                // archiveArtifacts "target/*.war"
            }
        }
    }
}


