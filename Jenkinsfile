pipeline {
    agent any
    tools {
        maven 'maven3'
    }
    // options {
    //     buildDiscarder logRotator(daysToKeepStr: '5', numToKeepStr: '7')
    // }
    stages{
        stage('Build'){
            steps{
                //  sh script: 'mvn clean package'
                //  archiveArtifacts artifacts: 'target/*.war', onlyIfSuccessful: true
                nexusArtifactUploader artifacts: [
                    [
                        artifactId: 'simple-app', 
                        classifier: '', 
                        file: 'target.simple-app-1.0.0.war', 
                        type: 'war'
                        ]
                    ], 
                    credentialsId: 'nexus3', 
                    groupId: 'in.javahome', 
                    nexusUrl: '172.31.41.79:8081', 
                    nexusVersion: 'nexus3', 
                    protocol: 'http', 
                    repository: 'http://3.8.165.94:8081/repository/simpleapp-release', 
                    version: '1.0.0'
            }
        }
        // stage('Upload War To Nexus'){
        //     steps{
        //         script{

        //             def mavenPom = readMavenPom file: 'pom.xml'
        //             def nexusRepoName = mavenPom.version.endsWith("SNAPSHOT") ? "simpleapp-snapshot" : "simpleapp-release"
        //             nexusArtifactUploader artifacts: [
        //                 [
        //                     artifactId: 'simple-app', 
        //                     classifier: '', 
        //                     file: "target/simple-app-${mavenPom.version}.war", 
        //                     type: 'war'
        //                 ]
        //             ], 
        //             credentialsId: 'nexus3', 
        //             groupId: 'in.javahome', 
        //             nexusUrl: '172.31.15.204:8081', 
        //             nexusVersion: 'nexus3', 
        //             protocol: 'http', 
        //             repository: nexusRepoName, 
        //             version: "${mavenPom.version}"
        //             }
        //     }
        // }
    }
}