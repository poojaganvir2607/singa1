pipeline {
    agent any 
    environment {
        IMAGE_NAME = "myapp"
        IMAGE_TAG = "${BUILD_NUMBER}"
        CONTAINER_NAME = "my-container"
    }
    stages {
        stage("checkout code") {
            steps {
                git branch: 'main', url: 'https://github.com/poojaganvir2607/singa1.git'
            }
        }
        stage("build docker image") {
            steps {
                sh "docker build -t ${IMAGE_NAME}:${IMAGE_TAG} ."
            }
        }
        stage("build docker container") {
            steps {
                sh """
                  docker run -d \
                  --name ${CONTAINER_NAME} \
                  -p 8080:80 \
                  ${IMAGE_NAME}:${IMAGE_TAG}
                  """
            }
        }
    }
    
}
