pipeline {
    agent any
    triggers {
        cron('@weekly')
    }
    stages {
        stage('checkout') {
            steps {
                checkout scm
            }
        }
        stage('semgrep-scan') {
            when {
                allOf {
                    branch 'main'
                    anyOf {
                        triggeredBy 'TimerTrigger'
                        triggeredBy cause: "UserIdCause"
                    }
                }
            }
            steps {
                // your scan code here
                sh 'echo hello world'
            }
        }
    }
}