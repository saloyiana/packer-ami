pipeline{
agent{
   kubernetes {
      yaml """
apiVersion: v1
kind: Pod
metadata:
  labels:
    some-label: some-label-value
spec:
  containers:
  - name: packer
    image: hashicorp/packer 
    command: 
    - bash
    tty: true
"""
    }
}
environment {
CREDS = credentials('sara-aws')
AWS_ACCESS_KEY_ID="${CREDS_USR}"
AWS_SECRET_ACCESS_KEY="${CREDS_PSW}"
OWNER="alpha"
PROJECT_NAME="alpha-project"
TF_NAMESPACE="sarah"
}
stages{
stage('build'){
steps{ 
 container('packer') 
{
sh '''
cd packer-ami/
packer build packer.json
'''
 }
} }}
}
