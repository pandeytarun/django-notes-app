@Library("shared") _
pipeline{
    agent{label "Vinod"}
    
    stages{
        
        stage("hello"){
            steps{
                script{
                    hello()
                }
            }
        }
        stage("code"){
            steps{
                script{
                 clone("https://github.com/pandeytarun/django-notes-app.git" ,"main")    
                }
            }
        }
        stage("Build"){
            steps{
                script{
                    docker_build("notesapp","latest","tarunpandey")
                }
            }
        }
        stage("Push to DockerHub"){
            steps{
                script{
                    docker_push("notesapp","latest","tarunpandey")
                }
            }
        }
        stage("Deploy"){
            steps{
                echo "this is Deploying the code"
                sh "docker compose down && docker compose up -d"
            }
        }
    }
}
