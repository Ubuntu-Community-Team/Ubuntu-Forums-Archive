---
title: "Ubuntu 8.10 installation help."
date: 2009-02-14
forum: Installation &amp; Upgrades
---

### Post by thorosius on 2009-02-14
HY!
 
I'v not been an ubuntu user for the last 5-6 months so I'v forgotten somethings. I wanted to try the 8.10 release. So I was able to install Ubuntu last time by setting a swap partition before starting the installation. This helped me to make up for my 256MB ram. But I forgot how did I do it. Any help?

---

### Post by DeMus on 2009-02-14
> **thorosius said:**
> HY!
 
I'v not been an ubuntu user for the last 5-6 months so I'v forgotten somethings. I wanted to try the 8.10 release. So I was able to install Ubuntu last time by setting a swap partition before starting the installation. This helped me to make up for my 256MB ram. But I forgot how did I do it. Any help?

Have a look here, where the installation process is described:
[https://help.ubuntu.com/8.10/installation-guide/i386/howto-getting-images.html]()
I hope this will help you.
Success.

---

### Post by thorosius on 2009-02-15
Thnx but I already figured it out. 
 
1. Boot the live CD with safe mode.
2. Let the X load upto the desktop (this is gonna take some time).
3. Press Alt+F1. This goes into command line mode.
4. Run cfdisk and create a swap partition.
5. Execute sudo swapon /dev/hda* (* is the partition number. Also make sure that its hda or sda in /dev)
6. Again go into X by Alt+F7.
 
Ur set.

---

