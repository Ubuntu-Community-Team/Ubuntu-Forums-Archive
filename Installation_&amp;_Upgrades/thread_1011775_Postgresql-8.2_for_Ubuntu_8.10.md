---
title: "Postgresql-8.2 for Ubuntu 8.10?"
date: 2008-12-15
forum: Installation &amp; Upgrades
---

### Post by PaulusEm on 2008-12-15
How can i install postgresql-8.2 on Ubuntu 8.10?
When i use:
sudo apt-get install postgresql-8.2

it cant find the package, but when i do:
sudo apt-get install postgresql-8.3

it installs 8.3, but i need 8.2

I hope somebody can help me :)

-Paul

---

### Post by ibutho on 2008-12-15
Apparently there are no postgresql-8.2 packages in Ubuntu 8.10. You could compile from source, use Ubuntu 8.04 or see if you can use the 8.04 packages in 8.10 (you may need to add the 8.04 repos to your 8.10 sources.list).

---

### Post by PaulusEm on 2008-12-15
> **ibutho said:**
> Apparently there are no postgresql-8.2 packages in Ubuntu 8.10. You could compile from source, use Ubuntu 8.04 or see if you can use the 8.04 packages in 8.10 (you may need to add the 8.04 repos to your 8.10 sources.list).
Thanks for your reply, can you maybe explain me how i can add the 8.04 packages in 8.10? I'm a newbie with Ubuntu, only know how to use standard things (A)

---

### Post by ibutho on 2008-12-15
You simply add the Ubuntu 8.04 repos to the /etc/apt/sources.list of your Ubuntu 8.10 installation. This involves using an editor like nano e.g. "sudo nano /etc/apt/sources.list" and adding something like
```
deb http://us.archive.ubuntu.com/ubuntu/ hardy main restricted
deb http://us.archive.ubuntu.com/ubuntu/ hardy-updates main restricted

```
After that you would need to update your sources using "sudo apt-get update" and then install the version of postgresql you need. I am not sure how smooth the process will go, but its worth a shot.

---

### Post by PaulusEm on 2008-12-15
> **ibutho said:**
> You simply add the Ubuntu 8.04 repos to the /etc/apt/sources.list of your Ubuntu 8.10 installation. This involves using an editor like nano e.g. "sudo nano /etc/apt/sources.list" and adding something like
```
deb http://us.archive.ubuntu.com/ubuntu/ hardy main restricted
deb http://us.archive.ubuntu.com/ubuntu/ hardy-updates main restricted

```
After that you would need to update your sources using "sudo apt-get update" and then install the version of postgresql you need. I am not sure how smooth the process will go, but its worth a shot.Thanks, but still not working for me. I did exactly what you said.. :(
Any other ideas?

---

### Post by PaulusEm on 2008-12-15
Solved by installing the following packages:
[http://packages.ubuntu.com/hardy/postgresql-client-8.2](http://packages.ubuntu.com/hardy/postgresql-client-8.2)
[http://packages.ubuntu.com/hardy/postgresql-8.2](http://packages.ubuntu.com/hardy/postgresql-8.2)

---

### Post by BryanKeith on 2009-03-02
> **PaulusEm said:**
> Solved by installing the following packages:
[http://packages.ubuntu.com/hardy/postgresql-client-8.2](http://packages.ubuntu.com/hardy/postgresql-client-8.2)
[http://packages.ubuntu.com/hardy/postgresql-8.2](http://packages.ubuntu.com/hardy/postgresql-8.2)

Yes, I can see that installing these packages is the solution to your problem, but how did you install these packages?

Bryan

---

### Post by PaulusEm on 2009-03-06
Hey Bryan,

Just go in your browser to:
[http://packages.ubuntu.com/hardy/postgresql-client-8.2](http://packages.ubuntu.com/hardy/postgresql-client-8.2)

Scroll down to the bottom and download the i386 or amd64 file (according to your file system).
You can run these files in your package manager.

Do the same for the package postgresql-8.3 ;)

---

### Post by Kingz747 on 2009-06-11
[SIZE=5][FONT=Arial Black][SIZE=2]HI,

when i type in the terminal:

sudo apt-get install postgresql-8.3 - i get this - E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. now i have become a super user and tried to sort it but when i do:root@one-laptop:/home/one# dpkg --configure -a
Setting up postgresql-8.3 (8.3.7-0ubuntu8.10.1) ...
 * Starting PostgreSQL 8.3 database server                                       * Error: Could not create log file /var/log/postgresql/postgresql-8.3-main.log
                                                                         [fail]
invoke-rc.d: initscript postgresql-8.3, action "start" failed.
dpkg: error processing postgresql-8.3 (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of postgresql:
 postgresql depends on postgresql-8.3; however:
  Package postgresql-8.3 is not configured yet.
dpkg: error processing postgresql (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 postgresql-8.3
 postgresql

Please help because im trying to install java to play runescape but to do that i need to sort out the two problems

1. Postgresql 8.3 
2. dpkg error

Thanks Gabe :guitar:

[/SIZE] 

[/FONT][/SIZE]

---

