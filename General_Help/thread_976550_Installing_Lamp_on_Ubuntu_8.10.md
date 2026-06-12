---
title: "Installing Lamp on Ubuntu 8.10"
date: 2008-11-09
forum: General Help
---

### Post by Rinox on 2008-11-09
Hello! I'm completely new to ubuntu, and I have been using windows until now. I used wamp at my windows computer and now I need Lamp on my ubuntu computer, but since I'm completely new to linux, many of the guides I find are hard to understand. I hope someone can explain how to do this to me or direct me to a good guide. I have ubuntu 8.10 by the way. Thank you :)

---

### Post by Ryadt on 2008-11-09
Installing LAMP is easy. Go in System > Administration > Synaptic, under edit select 'Mark packages by task. Then select the LAMP server and you are done.

---

### Post by Rinox on 2008-11-09
Thanks, I did that but the task seemed to already be marked and done. I tried this guide before I posted here. Maybe that's why? [http://www.youtube.com/watch?v=LI5ZYfZGQ_U](http://www.youtube.com/watch?v=LI5ZYfZGQ_U)

However, if I go to localhost in my browser I get a page load error.. Do anyone know how to delete what I've done so I can do it all through Synaptic?

Thanks :)

---

### Post by Ryadt on 2008-11-09
I personally prefer to use xampp. Download it from the xampp website and install it. It is easier to use.

---

### Post by Diabolis on 2008-11-09
Since you have already worked with a WAMP, maybe my notes will be enough. This notes do not pretend to be a guide, but a quick way for me to remember what it takes to setup a LAMP.
[php]
sudo apt-get install apache2

# this command restarts apache
sudo apache2ctl restart

# Possible error
# apache2: Could not reliably determine the server's fully qualified domain name, using 0.0.9.116 for ServerName
# Solution: http://www.linuxquestions.org/questions/linux-server-73/apache-giving-the-error-could-not-determine-the-servers-fully-qualified-domain-name-280677/#post1438486

sudo aptitiude install php5 libapache2-mod-php5

# load the php module
sudo a2enmod php5

# MySQL documentation
# https://help.ubuntu.com/8.04/serverguide/C/mysql.html

sudo apt-get install mysql-server-5.0

# Check if MySQL is running
sudo netstat -tap | grep mysql

# This comand will restart the MySQL service
sudo /etc/init.d/mysql restart
[/php]

---

### Post by Rinox on 2008-11-09
I've downloaded xampp in a tar.gz file, but now I wonder how I install it... I don't know where to unpack it or how to install it...

---

### Post by Ryadt on 2008-11-09
[http://www.apachefriends.org/en/xampp-linux.html](http://www.apachefriends.org/en/xampp-linux.html)

---

### Post by Rinox on 2008-11-09
Thanks! :) Now I found it, but the only problem now is that when I type su in the terminal it asks me for a password. I typed in the password for my one and only user but then it says: "su: Authentication failure"

Hope you can help me with this :)

---

### Post by Ryadt on 2008-11-09
Do ```
sudo -s
``` instead.

---

### Post by CaseWestern on 2008-11-09
> **Rinox said:**
> Thanks! :) Now I found it, but the only problem now is that when I type su in the terminal it asks me for a password. I typed in the password for my one and only user but then it says: "su: Authentication failure"

Hope you can help me with this :)

Thats because you didnt setup root account for your machine.  Go to System -> Administration->Users and Groups . Select root and then click unlock.  Then it will ask you to enter your user password.  After that you would be able to set a password for your root by clicking on properties tab.

After that go to terminal and type ```
su
``` and enter the newly setup password for root.

---

### Post by gpsmikey on 2008-11-09
With "su", you are trying to change to root, which is, by default, disabled.  The "sudo" command gives you root rights but you are still using your account, so your password words for that.  There is a good tutorial on "sudo" out there, but I don't have it handy right now - basically, you need to be in the sudo users list as well (which the first account you set up should be).

mikey

---

### Post by Rinox on 2008-11-09
Thanks! That worked :) I finally made it! But now to the last questions... I did access localhost now, and lampp was installed in /opt but where is the folder where is the root folder that contains all of the files that are shown on localhost? In wamp the folder was called "www"

Also I wonder if I have to use the terminal everytime I want to start apache, php, and mysql? Is there an easier way?

And do you guys know of a good place to learn how to use the terminal?

Thanks :)

---

### Post by Ryadt on 2008-11-09
The localhost folder is htdocs in /opt/lampp.

---

### Post by Rinox on 2008-11-09
Thanks! :) Do you know the answer for any of the other questions as well?

---

### Post by Ryadt on 2008-11-09
You will have to do the command everytime you want to start xampp. That's the easiest way.
Here is a link to use command line:[http://linuxcommand.org/index.php](http://linuxcommand.org/index.php)

---

### Post by ubunken on 2008-11-10
> **Ryadt said:**
> Installing LAMP is easy. Go in System > Administration > Synaptic, under edit select 'Mark packages by task. Then select the LAMP server and you are done.

Hi i am completely new to Linux and am also trying to install LAMP however after navigating to System> Administration>... I was unable to find the LAMP server package. Is there any pre-requisite that i have to do?:confused:

---

### Post by Ryadt on 2008-11-10
Can you get in 'Mark packages by task'?

---

### Post by utnubuuser on 2008-11-10
There is also a good video tutorial at: [www.lullabot.com/node/289](www.lullabot.com/node/289)

---

### Post by mlotfi on 2008-11-12
I just installed LAMP using System > Administration > Synaptic

How to test Apache , Mysql and PHP  are all working fine.?
Thanks

---

### Post by Diabolis on 2008-11-12
[php]
# Check if MySQL is running
sudo netstat -tap | grep mysql [/php]

Open firefox and type **localhost**. A page that says **it works!** will appear if apache is running.

Write any php script and try to open it with firefox, if it executes then its running. If a download window appears, then its not working.

put this:
[php]<?php phpinfo();?>[/php]

in a file with extension .php and try to open it with firefox

---

### Post by mlotfi on 2008-11-13
1)Where apache is installed in ubuntu ?

2)is there any way to find out where are the application installed in ubuntu ?

Thanks

---

### Post by Madvil on 2008-11-19
> **mlotfi said:**
> 1)Where apache is installed in ubuntu ?

2)is there any way to find out where are the application installed in ubuntu ?

Thanks

Did you installed lamp-server?

---

### Post by Jive Turkey on 2008-11-19
> **mlotfi said:**
> 1)Where apache is installed in ubuntu ?

2)is there any way to find out where are the application installed in ubuntu ?

Thanks

I think that where it is installed is not going to be that helpful to you but if you type ```
whereis <name-of-program-or-file>
``` in a terminal it should tell you where a file with a similar name is.

I think you will probably find the webmin package on sourceforge helpful, download the *.deb for it [here]("http://sourceforge.net/projects/webadmin/")

---

### Post by BukEye on 2008-12-01
The video utnubuuser posted was very helpful but when during the video did she get the apache2-common and the link to phpmydmin directories in the var/www directory? That configuration is allot more useful than "It works!":)

---

