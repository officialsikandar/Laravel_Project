# Laravel_Project




Deploy Laravel Application on Ubuntu Server

No Commentson Deploy Laravel Application on Ubuntu Server
Deploy Laravel Application on Ubuntu Server
In this blog, I will show you How to deploy Laravel or PHP Application on Ubuntu Server. You can get Ubuntu server from any Hosting provider. The process will be the same for any Ubuntu instance. We will see How Ubuntu server setup properly. How can you install PHP, MYSQL, and PHPMyAdmin. I will use AWS Ubuntu Instance.

Prerequisites
Before starting to deploy, We have to fulfill all the requirements










1 . Create Ubuntu EC2 instance in AWS

Login to your AWS Account

Go to the Ec2 tab and Click on the new Launch Instance button. After that, we have to select a machine type. Search ubuntu in search bar and click on Select button on Ubuntu Server 18.04 LTS.


Next we have to choose instance type I will select t2.micro because it is free. You can select according to your need. Click on Configure Instance Details button.


In Configure instance details page, You have to change according to your needs. I don’t need to change anything so Click on Add Storage.


Next we have to provide storage details, In this section You can change Storage type and size. I don’t need to change anything so I will go to next section. Click on Add Tags button.


In Add Tags section, You can provide any tag and their value. Click on Configure security group.


In Configure security group, You can select existing security group but I will always prefer to create a new security group for a new instance. Create a new Security group and Allow Http protocol 80. Click on Review and Launch button.


In Review section, You can check all the configuration which your provide before to your new ubuntu server. If you want to change anything you can go back and update that configuration. Click on Launch button.


After clicking on Launch button, popup appears for selecting a key pair for your instance. You can create a new Key pair or use existing one. Don’t forget to Download the new Key pair. Click on Launch Instance.


After some minutes your Ubuntu server is ready for action. You can check your server in EC2 instances. Server DNS is in Red Circle.


Server is ready. Let’s deploy the Laravel project on it steps by steps.

Step 1 — Connect Server with Terminal
I’m on Windows so I’m using putty terminal for connecting server. Open putty, Enter hostname.

ubuntu@ServerDNS

For Connection, You have to convert PEM file to PPK. You can use PUTTYGEN software to convert PEM file.

Now we have to attach PPK file to Putty. In left pane of Putty, Connection → SSH → AUTH

Select Auth, In the right, Browse ppk file and attach it.


Click Open.













Step 2 — Install Apache on Server
The Apache web server is among the most popular web servers in the world. It’s well-documented and has been in wide use for much of the history of the web, which makes it a great default choice for hosting a website.

First, we have to update all the modules and then upgrade our server. For that you have to enter this command :

sudo apt-get update
sudo apt-get upgrade
Install zip extension with below command

sudo apt install zip unzip
Install Apache web server with below command

sudo apt install apache2
After that command Apache web server installed successfully. Restart the Apache web server.

sudo service apache2 restart
Let’s check apache web server is installed or not. Copy your server dns and paste it in browser url. If you get this page it means Apache web server installed successfully.












Step 3 — Install MySQL Server
Now that you have your web server up and running, it is time to install MySQL. MySQL is a database management system. Basically, it will organize and provide access to databases where your site can store information.

Install MySQL Server with below command:

sudo apt install mysql-server
When you run this command It will show you some packages that will be installed. Enter Y to Continue. After MySQL server installed, We have to set the Root Password for that You have to enter below command.

sudo mysql_secure_installation
Press Y for setup Validate password plugin.

There are three levels of password validation policy:

LOW    Length >= 8
MEDIUM Length >= 8, numeric, mixed case, and special characters
STRONG Length >= 8, numeric, mixed case, special characters and dictionary

Please enter 0 = LOW, 1 = MEDIUM and 2 = STRONG:
Press key according to your password which you want to set.

Enter Your password. After that you have to confirm your password.

After Confirming password It will show you your password strength and then ask for Continue with password. Press Y button

Then Ask for removing anonymous user Press Y button

Ask for Disallow root login remotely Press N button. Next press accordingly if you want to access the test database of mysql. Press Y for reload Privileges tables.

MySQL Server setup successfully.










Step 4 — Install PHP
PHP is the component of your setup that will process code to display dynamic content. It can run scripts, connect to your MySQL databases to get information, and hand the processed content over to your web server to display.

For PHP Installation Enter the below command, It will install all the modules of php.


**************
sudo apt install php libapache2-mod-php php-mbstring php-xmlrpc php-soap php-gd php-xml php-cli php-zip php-bcmath php-tokenizer php-json php-pear php-mysql php-gettext php-curl php-memcached php-xdebug php-intl php-fpm php-pgsql php-imap
**************



Press Y for install all the modules of php.

It will take some seconds to install php and their modules. After installation of php. You can check php version with this command.

php -v
Now php is installed in our server. Let’s upload the Laravel project, before that update all the modules of server and restart apache server with the below command.

sudo apt-get update
sudo service apache2 restart












Step 5 — Deploy Laravel Project on Server
We can upload the project with two approaches :-

Using Github
Upload project through Filezilla
We will using Filezilla approach. If you want to know How to use Github to upload the project you can comment it in comment section i will help you.

Using Filezilla approach, You have to download Filezilla software. You can download from here according to your system – Click here

Next, Connect our server to filezilla. For that, open filezilla software.

File → Site Manager → New Site

For creating a connection, You have to enter below details. You can create Server PPK file through PEM file using PUTTYGEN Software.

Protocol – SFTP – SSH File Transfer Protocol
Host – ServerDNS
Port – 22
Logon Type – Key file
User – ubuntu
KeyFile – Server PPK File

For uploading laravel project you have to watch my video.


Conclusion
I hope, now you setup ubuntu server easily if you have any query you can ask me in the comment section.

I would like to hear your thoughts or suggestions in the comment section.
