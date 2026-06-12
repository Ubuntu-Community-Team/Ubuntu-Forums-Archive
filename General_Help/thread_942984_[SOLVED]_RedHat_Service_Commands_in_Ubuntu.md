---
title: "[SOLVED] RedHat Service Commands in Ubuntu"
date: 2008-10-09
forum: General Help
---

### Post by tommygunner on 2008-10-09
I'm trying to run Redhat style service commands such as:

service httpd stop

As I understand there is a app I can install that will do something like this in Ubuntu, but I lost my notes. Does anyone know what the app is called?

---

### Post by porchrat on 2008-10-09
I think what you're looking for is /etc/init.d

Commands are something along the lines of:

sudo /etc/init.d/./httpd stop

Of course httpd can be substituted for whatever daemon you're manipulating.  Other arguments include start and restart, but there are a few more...can't remember them all.

---

### Post by ww711 on 2008-10-09
service commands in ubuntu/debian are in

sudo /etc/init.d/nameoftheservice start|stop|restart 

apache, mysqld, network...

Not sure if there is a graphical front end yet...

Lots of discussion about it here -> [http://brainstorm.ubuntu.com/idea/68/](http://brainstorm.ubuntu.com/idea/68/)

---

### Post by tommygunner on 2008-10-09
Yes, I know how to run the commands that way, but there is a shortcut way in Centos that allows you to type:

service httpd stop|start| 

In Centos this can be typed anywhere. I can be in my home folder, type this and it does what I want.

I saw something about a package download that basically adds this functionality to Ubuntu so that you don't have to keep going to:
/etc/init.d/ everytime you want to run a command. I'm trying to find what the package is called.

---

### Post by tommygunner on 2008-10-09
Ok, I found it. It is called sysvconfig.

---

