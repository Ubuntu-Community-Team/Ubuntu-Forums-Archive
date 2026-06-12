---
title: "Cannot install ubuntu 9.04"
date: 2009-04-23
forum: Installation &amp; Upgrades
---

### Post by mkoonstra on 2009-04-23
I have tried updating to Ubuntu 9.04 by using the install cd, as I would like to use ext4 on my new system (the root should be ext4). However, everytime I run the installation, it quits with the following message:

[Errno 5] Input/output error: '/rofs/usr/share/app-install/dekstop/amide.desktop'

It says something more about the cd being defect, but the disc check utility says it is OK. Can anybody help me?

---

### Post by cariboo on 2009-04-23
What is it exactly that you are trying to do? To be able to use Ext4, you either have to convert your root partiition using this [thread=1115253]howto[/thread] or reformat the drive during installation.

---

### Post by mkoonstra on 2009-04-23
I am reformatting it during a new installation. However, this error keeps popping up after all the questions have been asked and the system is formatted.

---

### Post by wpshooter on 2009-04-23
If you don't have anything on the drive that you need to keep/save, then get [www.killdisk.com](www.killdisk.com) and WIPE the drive completely clean, then retry doing the installation.

---

