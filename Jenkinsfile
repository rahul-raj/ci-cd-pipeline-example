pipeline {

    agent any

    stages {

        stage ('Build') {
            steps {
                withMaven(maven: 'maven_3_6_3') {
                    sh 'mvn clean package'
                }
            }
        }

        stage ('Deploy') {
            steps {

                withCredentials([[$class          : 'UsernamePasswordMultiBinding',
                                  credentialsId   : 'CloudFoundry-Credentials',
                                  usernameVariable: 'USERNAME',
                                  passwordVariable: 'PASSWORD']]) {

                    bat 'C:/Users/320089371/CloudFoundry/cf login -a http://api.run.pivotal.io -u $USERNAME -p $PASSWORD'
                    bat 'C:/Users/320089371/CloudFoundry/cf push'
                }
            }

        }

    }

}