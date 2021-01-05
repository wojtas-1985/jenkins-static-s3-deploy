pipeline {
    agent any

    stages{
        stage('deploy to S3'){
            steps{
                sh 'aws s3 cp public/index.html s3://mytestweb-v1.1.com.s3-website-us-west-2.amazonaws.com'
                sh 'aws s3api put-object-acl --bucket mytestweb-v1.1.com.s3-website-us-west-2.amazonaws.com --key index.html --acl public-read'
                sh 'aws s3 cp public/error.html s3://mytestweb-v1.1.com.s3-website-us-west-2.amazonaws.com'
                sh 'aws s3api put-object-acl --bucket mytestweb-v1.1.com.s3-website-us-west-2.amazonaws.com --key error.html --acl public-read'
            }
        }
    }
    post{
        always{
            cleanWs disableDeferredWipeout: true, deleteDirs: true
        }
    }

}
