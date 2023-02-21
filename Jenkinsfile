pipeline {
  agent any
  // any, none, label, node, docker, dockerfile, kubernetes
  tools {
    maven 'my_maven'
    // 플러그인 설치후 글로벌 설정에서 만든 빌드명.
  }
  environment {
<<<<<<< HEAD
    gitName = 'wodb777'
    gitEmail = 'wodb777@gmail.com'
    githubCredential = 'git_cre'
    dockerHubRegistry = 'wodb73/sbimage'
=======
    gitName = 'pcmin929'
    gitEmail = 'pcmin929@gmail.com'
    githubCredential = 'git_cre'
    dockerHubRegistry = 'oolralra/sbimage'
>>>>>>> upstream/main
    dockerHubRegistryCredential = 'docker_cre'
  }
  stages {
    stage('Checkout Github') {
      steps {
<<<<<<< HEAD
          checkout([$class: 'GitSCM', branches: [[name: '*/main']], extensions: [], userRemoteConfigs: [[credentialsId: githubCredential, url: 'https://github.com/aeokseung/sb_code.git']]])
=======
          checkout([$class: 'GitSCM', branches: [[name: '*/main']], extensions: [], userRemoteConfigs: [[credentialsId: githubCredential, url: 'https://github.com/pcmin929/sb_code.git']]])
>>>>>>> upstream/main
          }
      post {
        failure {
          echo 'Repository clone failure'
        }
        success {
<<<<<<< HEAD
          echo 'Repository clone success'
        }
      }
    }
=======
          echo 'Repository clone success'  
        }
      }
    }

>>>>>>> upstream/main
    stage('Maven Build') {
      steps {
          sh 'mvn clean install'
          // maven integration , maven invoker 플러그인이 설치되어있어야함.
          }
      post {
        failure {
          echo 'Maven jar build failure'
        }
        success {
<<<<<<< HEAD
          echo 'Repository clone success'
=======
          echo 'Repository clone success'  
>>>>>>> upstream/main
        }
      }
    }
    stage('Docker Image Build') {
      steps {
          sh "docker build -t ${dockerHubRegistry}:${currentBuild.number} ."
          sh "docker build -t ${dockerHubRegistry}:latest ."
          // dockerHubRegistry 위에서 선언한 변수, 내 저장소.
          // currentBuild.number 젠킨스가 제공하는 변수. 빌드넘버를 받아옴.
          }
      post {
        failure {
          echo 'Docker Image Build failure'
        }
        success {
<<<<<<< HEAD
          echo 'Docker Image Build success'
=======
          echo 'Docker Image Build success'  
>>>>>>> upstream/main
        }
      }
    }
    stage('Docker Image Push') {
      steps {
          // 도커 허브의 크리덴셜
          withDockerRegistry(credentialsId: dockerHubRegistryCredential, url: '') {
          // withDockerRegistry : docker pipeline 플러그인 설치시 사용가능.
<<<<<<< HEAD
          // dockerHubRegistryCredential : environment에서 선언한 docker_cre
            sh "docker push ${dockerHubRegistry}:${currentBuild.number}"
            sh "docker push ${dockerHubRegistry}:latest"
          }
=======
          // dockerHubRegistryCredential : environment에서 선언한 docker_cre  
            sh "docker push ${dockerHubRegistry}:${currentBuild.number}"
            sh "docker push ${dockerHubRegistry}:latest"
          }  
>>>>>>> upstream/main
      }
      post {
        failure {
          echo 'Docker Image Push failure'
          sh "docker rmi ${dockerHubRegistry}:${currentBuild.number}"
          sh "docker rmi ${dockerHubRegistry}:latest"
        }
        success {
          echo 'Docker Image Push success'
          sh "docker rmi ${dockerHubRegistry}:${currentBuild.number}"
          sh "docker rmi ${dockerHubRegistry}:latest"
          slackSend (color: '#0AC9FF', message: "SUCCESS: Docker Image Push '${env.JOB_NAME} [${env.BUILD_NUMBER}]' (${env.BUILD_URL})")
        }
      }
    }
    stage('Docker Container Deploy') {
      steps {
          sh "docker rm -f spring"
          sh "docker run -dp 7979:8085 --name spring ${dockerHubRegistry}:${currentBuild.number}"
<<<<<<< HEAD
          }
=======
      }
>>>>>>> upstream/main
      post {
        failure {
          echo 'Container Deploy failure'
        }
        success {
<<<<<<< HEAD
          echo 'Container Deploy success'
        }
      }
    }
=======
          echo 'Container Deploy success'  
        }
      }
    }
      
>>>>>>> upstream/main
  }
}
