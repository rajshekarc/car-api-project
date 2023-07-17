pipeline{
    agent any
    tools{
        maven "Qprofiles-maven"
    }
    stages{
        stage("Fetch the data from github"){
            steps{
                git url: "https://github.com/rajshekarc/car-api-project.git"
            }
        }
        stage("compile the ccode"){
            steps{
                sh 'mvn compile'
            }
        }
        stage("Test the compiled code"){
            steps{
                sh 'mvn test'
                echo 'To test the print'
            }
        }
        stage("QA of the code"){
            steps{
                sh 'mvn pmd:pmd'
                recordIssues(tools: [pmdParser()])
            }
        }
        stage("Package the code"){
            steps{
                sh 'mvn package'
            }
        }
    }
}
