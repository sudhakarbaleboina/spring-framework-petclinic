pipeline {
  agent any
  stages {
    stage('check out') {
      steps {
        git(url: 'git@github.com:sudhakarbaleboina/spring-framework-petclinic.git', branch: 'master')
      }
    }

    stage('build') {
      steps {
        sh '''#!/bin/bash
/opt/maven/bin/mvn clean package -P MySQL'''
      }
    }

    stage('deploy') {
      steps {
        sh '''#!/bin/bash
scp target/petclinic.war root@10.0.20.176:/opt/tomcat/webapps'''
      }
    }

    stage('testing') {
      steps {
        sh '''#!/bin/bash
curl -I https://10.0.20.176:8080/petclinic'''
      }
    }

  }
}