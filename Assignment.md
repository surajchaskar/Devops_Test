## Linux
**1. Write a crontab that will run on each sunday at 10.10 AM.** <br/>
**Ans:**    10 10 * * 7 <br/>
            10 10 * * sun
      
**2. What are the kinds of permissions under linux and how can you change permissions and owner of any file/directory** <br/>
**Ans:**  Read, Write,Execute this are permissions under Linux<br/>
      Change permission:<br/>
     ``` chmod [OPTION] OCTAL-MODE FILE_NAME/DIR_NAME ```<br/>
      example: ``` chmod  -R 655 test ```<br/>
      ``` chown [OPTION] [OWNER][:[GROUP]] FILE_NAME/DIR_NAME ```<br/>
      example: ``` chown root:test test ```<br/>
      
**3. Write a command to find a string “red” and replace it with “blue” in particular file.**<br/>
**Ans:** ``` sed -i 's/red/blue/g' file_name ```<br/>
      If you want change in multiple files then give the pattern<br/>
      ``` sed -i 's/red/blue/g' *_blue_* ```<br/>
      
**4. Write commands to check free memory, load average, available disk**<br/>
**Ans:** ``` top ```: load average,free memory<br/>
      ``` free -g ```: free memory<br/>
    ```df -h```: available disk<br/>
    
**5. How will you check nginx process is running or not on machine? Write a command to find port number of nginx**<br/>
**Ans:**  Check the nginx process status:<br/>
      ```systemctl status nginx```<br/>
      OR<br/>
      ```service nginx status```<br/>
      ```ps -ef | grep nginx```<br/>
      Check the nginx port:<br/>
      ```netstat -tulpn | grep nginx```<br/>
 
**6. Write a command to check list of disks attached to machine, format the disk and mount it on any folder.** <br/>
**Ans:**  Check list of disks attached: <br/>
        ```lsblk ```<br/>
      format disk and mount:<br/>
        ```1)mkfs.ext3 /dev/sdb1```<br/>
        ```2)mkdir -p /mnt/data ```
        ```3) sudo mount -o /dev/sda1 /mnt/data```<br/>


## Docker
**1. Write commands to get list of images and list of all containers on a machine** <br/>
**Ans:**  List the all Images: <br/>
        ```docker image ls --all``` <br/>
      List the all Container: <br/>
        ```docker container ls  --all``` <br/>

**2. How will you check container logs?** <br/>
**Ans:** ``` docker logs [OPTION]  ContainerName/ContainerID``` <br/>
      ```docker logs --tail 500 ContainerName/ContainerID``` <br/>
 
**3. What is the method for creating a Docker container?** <br/>
**Ans:** ``` docker create [OPTIONS] IMAGE [COMMAND] [ARG...]```
      ```docker create -t -i ubuntu```

**4. Suppose you have 3 containers running and out of these, you wish to access one of them. How do you access a running container?** <br/>
**Ans:**  ```docker ps``` <br/>
      ```docker exec -it <container name> /bin/bash``` <br/>
      
**5. Explain Dockerfile commands** <br/>
**Ans:** FROM: creates a layer from the ubuntu:18.04 Docker image. <br/>
        ```FROM ubuntu:18.04```<br/>
      COPY: adds files from your Docker client’s current directory.<br/>
        ``` COPY . /app```<br/>
      RUN: builds your application with make.<br/>
        ```RUN make /app```<br/>
      CMD: specifies what command to run within the container.<br/>
        ```CMD bash /app/app.sh```<br/>

## AWS
**1. Write a command to upload any file to s3 bucket.** <br/>
**Ans:** ```aws s3 cp test.txt s3://my-bucket/path/```<br/>

**2. List AWS services that you worked on. Explain in brief.**<br/>
**Ans:** 
* EC2: It computes service. we have created for launching our pelican application on it. also, we have set up the Cassandra database on EC2 <br/>
* EMR: Use for the Hadoop application. <br/>
* RDS: For the relational database we have used Amazon RDS<br/>
* DynomoDB: for managing our terraform state lock<br/>
* Networking: For network setup<br/>
* S3: for data storage.<br/>
* Amazon Redshift: It is a fully managed data warehouse service in the cloud. Redshift gives you to access structured data from the existing SQL, ODBC, and JDBC<br/>
* cloud watch: For monitoring and operational data in the form of logs, metrics, and events of AWS resources, applications, and services that run on AWS and on-premises servers.<br/>
* Cloud trail: For enables governance, compliance, operational auditing, and risk auditing of the AWS account.<br/>
 
**3. How will you fix below error:** <br/>
![Image description](https://lh3.googleusercontent.com/ZmHtRo_IXjiSwEY-fWrqGzBcjhTP5M8pOSJ5xcNSAb4dO-8xoReOEgm-SWLfE79x2Gj8ClQ21mSuWb0XSqG--vvH7OkqE3Yg0MV2mJwMuEMLkqF8CQ6n2CQ2jC_U=w605)<br/>
**Ans:** ``` chmod 0400 ./ssh/my_private_key.pem```<br/>

**4.How can you convert a public subnet to private subnet?**<br/>
**Ans:**  
* Confirm there is already an IGW (Internet Gateway) attached to the VPC. This should be the case since you already have the public subnet.<br/>
* Update the route table applied to the subnet (AWS Management Console -> VPC -> Route Tables) to include a route to 0.0.0.0/0 -> IGW.<br/>
* Assign public IP addresses to your resources.
   
**5. Is it possible to reduce a EBS volume?**<br/>
**Ans:**  No<br/>

**6.Which of the following is not an option in security groups?**<br/>
**Ans:** List of users<br/>


## GIT
**1. What is the function of ‘GIT PUSH’ in GIT?**<br/>
Ans:** The git push command is used to upload local repository content to a remote repository.<br/>

**2. What is the purpose of branching in GIT? Write a command to create a new branch**<br/>
**Ans:**  Git is normally used in a collaborative environment, where multiple people work on a common goal, but in batches or steps. Each step could be a branch, branching divides the code into a separate, completely independent units, where each unit is potentially the entire application and allows for testing and debugging without affecting the main code. <br/>
      It also overcomes the conflicts of code <br/>
      Create new branch:<br/>
        ```git pull```<br/>
        ```git checkout -b [NAME_OF_YOUR_BRANCH]```<br/>
**3. Write down the steps to push your code on specific branch**<br/>
**Ans:**  
* I'll check out the first master branch to get the latest pull of master branch : <br/>
          ```git checkout master```<br/>
          ```git pull```<br/>
          and now master branch has the latest code<br/>
* I'll check out to a specific feature branch where I wanted to push the code. bt before that I ll merge latest master changes to feature branch so that my feature branch has now latest code : <br/>
    ```git checkout <feature_branch>```<br/>
            ``` git pull```<br/>
            ```git merge master```<br/>
* ```git commit -m "commit message"```<br/> 
* I'll push my code of the feature branch up to the central repository (origin) using : <br/>
            ```git push -u origin new-feature```<br/>

## Jenkins
**1. What Are The Most Useful Plugins In Jenkins?**<br/>
**Ans:**<br/>
- Build Flow
- Build Monitor
- Build Name Setter
- Build Pipeline
- Build Timeout
- Cucumber Test Result
- Delivery Pipeline
- Email Extension
- Git
- JaCoCo
- Parameterized Trigger
- SSH Agent
- SCM
- xUnit
- SSH Slaves
- SSH agent
- SSH
- Kubernetes Plugin
- Amazon ECS Container Service
      
**2. How to restart jenkins from UI?**<br/>
**Ans:**  To restart Jenkins manually, we can use either of the following commands (by entering their URL in a browser):<br/>
        ```(jenkins_url)/safeRestart``` - Allows all running jobs to complete. New jobs will remain in the queue to run after the restart is complete.<br/>
        ```(jenkins_url)/restart``` - Forces a restart without waiting for builds to complete.<br/>
        
 
## Configuration Management / Orchestration

**1. Which of Following Orchestration tool you used ?**<br/>
**Ans:**  Kubernetes(Elementory)<br/>

**2. Which of following CM tool you used**<br/>
**Ans:**  Ansible<br/>
