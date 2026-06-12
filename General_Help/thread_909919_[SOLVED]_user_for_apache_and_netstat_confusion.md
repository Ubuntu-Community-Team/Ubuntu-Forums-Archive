---
title: "[SOLVED] user for apache and netstat confusion"
date: 2008-09-04
forum: General Help
---

### Post by grindedrick on 2008-09-04
Hello,
I have been trying to install apache for weeks now.
I downloaded it, configured it, compiled it and installed it.
However, I can't run it under the user that I put into the httpd.conf file. 
I keep getting:
(13) permission denied make sock
So, I check ownership and the owner is the user edited in the httpd.conf file 
(though I did install apache as root, I couldn't figure out how to install it with any other user)
So, I figured maybe port 80 is being used.
So I run netstat and I have thousands of connections all of protocol Unix2 and Unix3?
No port numbers are listed either?

Can somebody explain this?
I'm not familiar with these results nor am I making any progress installing and running apache.
Thanks for being patient with another noob.

---

### Post by cariboo on 2008-09-04
Is there some reason why you didn't install it from the repositories, that way you have apache2 set up for your system.

Jim

---

### Post by grindedrick on 2008-09-04
I thought I'd start fresh straight from the source. This gave me a chance to use gpg for the first time as well as make. The documentation seemed to be more thorough and straight forward from apache.org anyways. I figured I'd do it step x step.

*and weeks means an hour here and there for 2 weeks* 

I'm on a huge learning curve here using user management commands for the first time as well. I logged most everything I did but it might take up some space. 

I dl'd server, installed as root, created new group and users to run it, chown on apache2 to the new user, then tried several different ways to start it. Mostly focused on apachectl start.

If you want syntax of commands I used I can dig it up.

*I'd also like to add, it runs as root but I don't want it to!*

---

### Post by grindedrick on 2008-09-04
I still haven't got this working.
I've noticed a lot of talk around the user www-data but you shouldn't have to use this user should you?

I created a user named wbm that belongs to a group www.
I then ran:
```

chown -R wbm apache2

```
Do I need to run one for the group as well? 
My intention was to allow this user to run apache.
I went to /usr/local/apache2/conf/httpd.conf and edited the lines:
> 
User wbm
Group www
 
and saved.
Is there more I need to do?
I found in /etc/apache2/apache2.conf 
my changes are visible as well.
I read it's a good idea to delete the other 2 configuration files and use httpd.conf but haven't done so yet.
Why are there 2 httpd.conf files? One under /usr/local/apache2/conf/
yet another empty one under /etc/apache2/
then you have apache2.conf which shows all the configuration settings ???:confused:
Heres the error I keep getting running as wbm for ./apachectl start:
> 
(13) Permission denied: make_sock could not bind to address [::]:80
no listening sockets available, shutting down
Unable to open logs

I also tried running chmod to ensure there were execution settings for the apache2 directory.
I also ran nmap to see of port 80 was open and it appears that it is.
I'm getting a little impatient here and don't feel this should be such an ordeal. I haven't found anybody with the same problem.
Does anybody know more?
Please?

---

### Post by grindedrick on 2008-09-04
Wait wait Wait.
If I set the User and Group in httpd.conf to the desired user and group and run "sudo apachectl start"
Is this running as root or my user specified?
Is there a command to check to see if apache or a program is running as root?

---

### Post by grindedrick on 2008-09-04
DANG!
At least a F RTFM would have been nice!
I never made it to starting apache cause I thought I was goofing something up in Linux and went on a googling extravaganza.

If anybody else has this problem:
Apache MUST run in root if the default port is used or any port under 1024 for that matter.
You can go to httpd.conf and edit Listen 80 to another TCP port and it should run.
13 hours since this was posted! I think I'm going to be sick.
Mostly my fault I know.
HURL

---

