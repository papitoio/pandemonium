pipeline {
   agent {
       docker {
           image "qaninja/pyrobot2"
       }
   }

   stages {
      stage("Build") {
          steps {
              sh "pip install -r requirements.txt"
          }
      }
      stage("Tests") {
         steps {
            sh "robot -d ./logs -i smoke tests"
         }
         post {
            always {
               robot otherFiles: '**/*.png', outputPath: 'results'
            }
         }
      }
   }
}