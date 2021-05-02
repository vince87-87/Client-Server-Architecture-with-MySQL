# Update latest patches on both client and server
Sudo apt-get update -y
 
![image](https://user-images.githubusercontent.com/49937302/116799516-957f7100-ab2c-11eb-90a3-6f4db9a551a9.png)

![image](https://user-images.githubusercontent.com/49937302/116799520-99ab8e80-ab2c-11eb-9a67-d1cefed49f72.png)

 # Install mysql server
Sudo apt install mysql-server -y

![image](https://user-images.githubusercontent.com/49937302/116799531-a8924100-ab2c-11eb-9560-79d4521092cf.png)

# start services
 
![image](https://user-images.githubusercontent.com/49937302/116799539-be076b00-ab2c-11eb-98d3-d97ac4300652.png)

# Install mysql client
Sudo apt install mysql-client -y

![image](https://user-images.githubusercontent.com/49937302/116799542-c5c70f80-ab2c-11eb-8c96-b2e729f22a6f.png)

# Allow SQL Client ip on the security group

![image](https://user-images.githubusercontent.com/49937302/116799543-ce1f4a80-ab2c-11eb-8611-37153df7b4d7.png)

# Secure mysql
sudo mysql_secure_installation

![image](https://user-images.githubusercontent.com/49937302/116799546-d6778580-ab2c-11eb-9bad-c7b4015bce1b.png)
 
# configure mysql database, user and grant access to the db

# Create user client user and grant any ip with the defined password
CREATE USER 'client_user'@'%' IDENTIFIED WITH mysql_native_password BY 'We!C0Me2MySQ!@123';
# create database mysql_db
CREATE DATABASE MYSQL_DB;
# grant mysql_db to client_user
GRANT ALL ON MYSQL_DB.* To 'client_user'@'%' WITH GRANT OPTION;
# reloads the grant tables in the mysql database enabling the changes to take effect without reloading or restarting mysql service
FLUSH PRIVILEGES;

![image](https://user-images.githubusercontent.com/49937302/116799559-e5f6ce80-ab2c-11eb-81ee-4b0de8ac3d30.png)

# change bind address in order to connect client to mysql server

![image](https://user-images.githubusercontent.com/49937302/116799561-ebecaf80-ab2c-11eb-8b34-626e1c3aed6c.png)


# restart mysql service
 
![image](https://user-images.githubusercontent.com/49937302/116799564-f1e29080-ab2c-11eb-8c49-bb6240c9dc2a.png)
 
# do a telnet from client to ensure its successful
telnet 172.31.26.76 3306
 
![image](https://user-images.githubusercontent.com/49937302/116799569-fb6bf880-ab2c-11eb-9cfe-7d0a6637c6ca.png)
  
# Connect mysql from client server
sudo mysql -u client_user -h 172.31.26.76 -p
We!C0Me2MySQ!@123

![image](https://user-images.githubusercontent.com/49937302/116799572-032b9d00-ab2d-11eb-911b-d1eea741e042.png)

# check that you can show to mysql_db
Show databases;
 
![image](https://user-images.githubusercontent.com/49937302/116799575-09217e00-ab2d-11eb-89fd-a94c4cbfc61c.png)
