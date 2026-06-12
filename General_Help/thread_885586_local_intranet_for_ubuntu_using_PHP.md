---
title: "local intranet for ubuntu using PHP"
date: 2008-08-10
forum: General Help
---

### Post by ayet on 2008-08-10
I want to setup a local intranet that runs PHP what program should i install?

---

### Post by markkie on 2008-08-10
Hi,

You will need a web server and PHP installed.  Would need more information to guide you further,  however there are loads of Google entries for your quest.

Ciao,

Markkie

---

### Post by ayet on 2008-08-10
i tried this guide
[https://help.ubuntu.com/6.06/ubuntu/serverguide/C/httpd.html]("https://help.ubuntu.com/6.06/ubuntu/serverguide/C/httpd.html")

and got the following on terminal

ayet@ayet-desktop:~$ sudo apt-get install apache2
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
ayet@ayet-desktop:~$

---

### Post by ayet on 2008-08-10
already installed it using this guide

[http://devolio.com/blog/archives/221-How-to-install-Apache,-MySQL-and-PHP-LAMP-in-Ubuntu-7.10.html]("http://devolio.com/blog/archives/221-How-to-install-Apache,-MySQL-and-PHP-LAMP-in-Ubuntu-7.10.html")

my problem is now everytime i run [http://locahost](http://locahost) or [http://127.0.1.1/](http://127.0.1.1/)

i get an error on firefox




Failed to Connect

Firefox can't establish a connection to the server at 127.0.1.1.

Though the site seems valid, the browser was unable to establish a connection.

    * Could the site be temporarily unavailable? Try again later.
    * Are you unable to browse other sites?  Check the computer's network connection.
    * Is your computer or network protected by a firewall or proxy? Incorrect settings can interfere with Web browsing.

---

### Post by ayet on 2008-08-10
some terminal displays when i restart apache

ayet@ayet-desktop:~$ sudo /etc/init.d/apache2 restart
 * Restarting web server apache2                                                apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName


how do i resolve this?

---

### Post by dexter.deepak on 2008-08-10
> **ayet said:**
> some terminal displays when i restart apache

ayet@ayet-desktop:~$ sudo /etc/init.d/apache2 restart
 * Restarting web server apache2                                                apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName


how do i resolve this?

you have to edit the /etc/apache2/apache2.conf and, at the end of the file, add: 

# added servername to avoid the could not determine fqdn error 
servername myserver 

place your server name in place of myserver.
restart apache.

---

### Post by GCoffee on 2008-08-10
If I am right, If you install Apache, PHP ETC and not forward port 80 only pc's connected to the network will be able to login? then you put in say:

[http://ubuntu/](http://ubuntu/) and as long as ubuntu is turned on, and the pc is connected to your network it should work?

GC.

---

