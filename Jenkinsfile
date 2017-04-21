echo 'Hello from Pipeline Demo'
 stage 'Compile'
 node {
 git url: 'https://github.com/mitesh51/spring-petclinic.git'
 def mvnHome = tool 'maven3'
 bat "${mvnHome}\\bin\\mvn -B compile"
 }
 stage 'Test'
 node('test') {
 git url: 'https://github.com/mitesh51/spring-petclinic.git'
 def mvnHome = tool 'maven3'
 bat "${mvnHome}\\bin\\mvn -B verify"
 step([$class: 'ArtifactArchiver', artifacts: '**/target/*.war',
fingerprint: true])
 step([$class: 'JUnitResultArchiver', testResults:
'**/target/surefire-reports/TEST-*.xml'])

}