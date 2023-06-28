pipeline { 
  agent any 
  options {
        skipStagesAfterUnstable()
        disableConcurrentBuilds()
  }
  stages {
     stage('Clone the repo') { 
       steps {
         script {
            //Clone the repository and checkout the Pull Request branch
           checkout([
             $class: 'GitSCM',
             branches: [
               [name: "*/PR-${env.CHANGE_ID}"]
             ],
             extensions: [
               [$class: 'CloneOption', depth: 1]
             ],
             userRemoteConfigs: [
               [
                 credentialsId: 'githubpat',
                 url: 'https://github.com/venkatzgithub/fluffy-telegram.git'
               ]
             ]
           ])
         }
       }
     }
    stage('PR') {
      steps {
        // sh 'cat Dockerfile'
       echo "print target branch: ${env.CHANGE_ID}"
      }
    }
  }
}
