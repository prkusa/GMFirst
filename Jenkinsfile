node
{
   def tomcatWeb = 'C:\\Tomcat 8.5\\webapps'
   def tomcatBin = 'C:\\Tomcat 8.5\\bin'
   def tomcatStatus = ''
   stage('SCM Checkout')
   {
     git 'https://github.com/prkusa/GMFirst.git'
   }
   stage('Compile-Package-create-war-file')
   {
      // Get maven home path
      def mvnHome =  tool name: 'maven3', type: 'maven'   
      bat "${'mvnHome'}/bin/mvn package"
   }
   stage('Deploy to Tomcat')
   {
     bat "copy target\\GMFirst.war \"${tomcatWeb}\\GMFirst.war\""
   }
    stage ('Start Tomcat Server') 
   {
         sleep(time:5,unit:"SECONDS") 
         bat "${tomcatBin}\\startup.bat"
         sleep(time:100,unit:"SECONDS")
   }
}
