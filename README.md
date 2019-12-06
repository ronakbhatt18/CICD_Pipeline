# CICD_Pipeline
Sample Jenkins Pipeline

This Reposatiry contains a  simple Java Web Application, which outputs the string
"Hello world!"  
This project uses maven tool to test & package this application
A WAR is generated at 'target/project.war'

## Jenkins Pipeline
This Reposatory also contains `Jenkinsfile`, Pipeline script for build, test & deploy in sequence

## Jenkins Project URL
[Jenkins Project](http://ec2-35-174-168-193.compute-1.amazonaws.com:8080/job/Test-Project/)

# Server Setup Process
I created an EC2 server with ubuntu AMI in public subnet, with public ip enabled and 8080, 8888 security group open to all
I installed Jenkins, Maven and Tomcat. 
below are detailed steps

## 1. Jenkins installation
commands for installation
```
sudo apt-get update
sudo apt-get install default-jre
sudo apt-get install default-jdk
sudo add-apt-repository ppa:webupd8team/java
sudo apt-get update
sudo apt-get install oracle-java8-installer

sudo update-alternatives --config java
sudo vi /etc/environment
add this line ----- JAVA_HOME="/usr/lib/jvm/java-8-oracle" #(if it is java-8-oracle)
echo $JAVA_HOME

wget -q -O - https://pkg.jenkins.io/debian/jenkins-ci.org.key | sudo apt-key add -
echo deb https://pkg.jenkins.io/debian-stable binary/ | sudo tee /etc/apt/sources.list.d/jenkins.list
sudo apt-get update

sudo apt-get install jenkins=2.176.3  (for specific version)
sudo systemctl start jenkins
sudo systemctl status jenkins
```

## 2. Maven Installation
```
sudo apt-get install maven
```
## 3. Tomcat Installation
```
mkdir -p /opt/tomcat/
wget http://mirrors.estointernet.in/apache/tomcat/tomcat-8/v8.5.49/bin/apache-tomcat-8.5.49.tar.gz
tar -xvf apache-tomcat-8.5.49.tar.gz
export CATALINA_HOME=/opt/tomcat/apache-tomcat-8.5.49
export JAVA_HOME=/usr
```
Check tomcat logs at /opt/tomcat/apache-tomcat-8.5.49/logs/catalina.out.

Edited  conf/server.xml to change tomcat port from 8080 to 8888
Startup script
```
apache-tomcat-8.5.49/startup.sh
```




