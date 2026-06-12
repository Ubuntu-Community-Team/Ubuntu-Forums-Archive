---
title: "Network problems causing boot issues"
date: 2007-03-19
forum: Hardware &amp; Laptops
---

### Post by McLaughysSN on 2007-03-19
Hey Guys,

My Laptop (Acer Asipire 5672wlmi) is having a few problems. Most noteably is startup and shutdown, As stated below the startup will stall out but i can get it to boot through with ctrl+c. The laptop has to be hard shutdown which is a pain and not so healthy. 

When i run recovery mode this is where it first stalls out

[17179588.658000] IPv6 over IPv4 Tunneling driver
FATAL: Module cman not found
Warning unable to load cman kernel moduleFATAL: Module dlm not found
Warning unable to load dlm kernel modulecman_tool: can't open /proc/cluster/status, cman not running
Starting cluster managercman_tool: can't open /proc/clsuter/status, cman not running


*Then i press ctrl+c and get the following (then it stalls again):


Starting lock_gulmd:/etc/cluster/cluster.conf was not detected
Starting global network block device server: No configured exports.
Starting global network block device client: Starting Cluster LVM Daemon


*I press ctrl+c a second time and the system comes to the following:

Give root password for maintenance
(or type Control-D to continue):


*I enter the password and boots to root terminal as expected and hit ctrl+d and everything boots to the gui as normal. The OS works perfectly fine and runs as normal, including the networking.

Shutdown Problem
When i shut down (this of course in recovery mode) I get the following:


Stopping apache 2.0 web server... [ OK ]
apache2: Could not determine the server's fullt qualified domain name, using 127.0.0.1 for Servername


*From here the system does nothing and I have to power down the laptop
Edit/Delete Message 

Thanks in advance.. I've posted in a another thread a few times but have No responses

Thanks!

---

### Post by apjone on 2007-03-20
The apache problem should not cause the system not to shutdown. 

you may want to check dmesg or /var/log/messages to see if you can find anymore info . aslo check out

[https://answers.launchpad.net/ubuntu/+ticket/3586](https://answers.launchpad.net/ubuntu/+ticket/3586)

---

### Post by McLaughysSN on 2007-03-20
Thanks for the repsonse

seems the link is dead or has a temp.problem

---

### Post by apjone on 2007-03-20
post the out put of 
```

whereis cman

```

please

---

### Post by McLaughysSN on 2007-03-20
This is what I get from that command

cman: /usr/share/man/man5/cman.5.g

---

### Post by apjone on 2007-03-20
do you run a network cluster??

---

### Post by McLaughysSN on 2007-03-20
Regarding networking, I run nm-applet. Everything else is just little programs like ethereal, dirftnet, etc. I do have jffnms as well but dont use it.

---

### Post by apjone on 2007-03-20
You may try to remove the package cman with

sudo dpkg --remove cman

and if that has problems

     sudo dpkg --remove --force-all cman

(The package is the cluster manager, I don't believe you run a cluster
here, so you shouldn't need it anyway)

After this you should 

     sudo apt-get update
     sudo dpkg --configure -a
     sudo apt-get dist-upgrade

---

### Post by McLaughysSN on 2007-03-21
Hey, just wanted to say thanks for the help so far!

I had multiple errors in just running apt-get update. I will post the output tonight when i get home.

---

