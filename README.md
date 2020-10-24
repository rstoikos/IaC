# IaC
test infrastructure as code

Followed https://cloudacademy.com/blog/introducing-iac-tools-within-aws/ excellent tutorial and modified
some errors in the proccess.

steps are:

a) create conf for wordpress
b) create the IAM role that we will use with CodePipeline:

aws iam create-role --role-name MyPipelineRole  --assume-role-policy file://pipeline-trust-policy.json

c) grant the appropriate accesses to our new IAM role:

aws iam put-role-policy --role-name MyPipelineRole --policy-name MyPipelinePolicy --policy-document file://pipeline-role-policy.json

d) create our new IAM role:

aws iam create-role --role-name MyCloudFormationRole --assume-role-policy file://cfn-trust-policy.json

e) attach the policy to our new IAM role:

aws iam put-role-policy --role-name MyCloudFormationRole  --policy-name MyCloudFormationPolicy --policy-document file://cfn-role-policy.json

some minor errors included policy rights fails , had to recreate the stack , recreate the github connection , delete some line from template json as seen in git history.

FInally load balancer couldnt see the host and changed health check
