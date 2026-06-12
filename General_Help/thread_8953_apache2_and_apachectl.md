---
title: "apache2 and apachectl?"
date: 2004-12-22
forum: General Help
---

### Post by BillDrew on 2004-12-22
How do I run apachectl from the command line?  All I get is command not found.  I am probalby not in the right directory.  Also, how do I get apache2 to work as a service so that it starts up when I boot up?  Be gentle.  I am a newbie to linux.

Bill Drew

---

### Post by Razvan on 2004-12-22
[QUOTE=BillDrew]How do I run apachectl from the command line?  All I get is command not found.  I am probalby not in the right directory.  Also, how do I get apache2 to work as a service so that it starts up when I boot up?  Be gentle.  I am a newbie to linux.

Bill Drew[/QUOTE]
 apache2 should be run as a saemon by default after you installed the packet

have you tried opening [http://127.0.0.1](http://127.0.0.1) in firefox?

do 
```

ps -d | grep apache 

```
in a console, if apache2 gets listed, it's running

i havent been playing with apachectl yet...in fact i dont even know what it is :-)

good luck, Martin

---

### Post by mpjbrennan on 2004-12-26
Hi Bill

It's now called **apache2ctl** - type apache2ctl help in a terminal window to get the correct usage.

But as Razvan says, the server should start up when you boot.

patrick

---

### Post by nikopol on 2005-01-07
I've also got trouble getting apache2 to run at bootup 
If I do 
```
ps -d | grep apache
```
I get nothing. I can however start it with 
```
sudo apache2ctl start
```but not by calling anything in init.d - how would I go about making it do the apache2ctl call on bootup? Remove everything in the Apache2 init script or just make up a new one /etc/init.d/myApacheStart with just ```
sudo apache2ctl start
``` in it?

---

### Post by fng on 2005-01-07
sudo update-rc.d apache2ctl defaults

---

### Post by nikopol on 2005-01-07
[QUOTE=fng]sudo update-rc.d apache2ctl defaults[/QUOTE]

Gives me a 
update-rc.d: /etc/init.d/apache2ctl: file does not exist

Thanks for the tip all the same :)

---

### Post by daniels on 2005-01-07
Actually, it's sudo update-rc.d apache2 defaults.  But I suspect the problem is that it's set to not start at boot -- edit /etc/default/apache2, and change NO_START=1 to NO_START=0, then run sudo invoke-rc.d apache2 start.

---

### Post by nikopol on 2005-01-08
Ah thanks - there's so many files associated with Apache2 it's hard to know where they all are...

---

### Post by daniels on 2005-01-09
dpkg -L apache2-common apache2-mpm-prefork, may help.

BTW, the idea behind apache2ctl is to work with apache1 -- from the very first packages of apache2, being able to parallel-install with apache was an unassailable priority.

---

### Post by Ack99 on 2006-10-16
You shold try
```
sudo ./httpd
```

---

