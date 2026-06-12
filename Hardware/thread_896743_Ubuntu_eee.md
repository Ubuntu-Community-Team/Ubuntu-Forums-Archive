---
title: "Ubuntu eee"
date: 2008-08-21
forum: Hardware
---

### Post by sonnenschein on 2008-08-21
I  was thinking of installing Ubuntu eee on my new eee pc....
Can I get any feedback from Ubuntu eee users on bugs and how well it runs and if it is worth it and all that jazz?

---

### Post by RedPandaFox on 2008-08-21
I haven't tried eeeUbuntu yet, I like the idea of the remix on it though, I have it downloaded but haven't tried it on my eee yet. I run Ubuntu 8.10 off an external onto my eeepc atm. (2GB surf)

---

### Post by linux_tech on 2008-08-21
Here is a guide to help install-
[http://www.simplehelp.net/2008/07/28/a-step-by-step-guide-to-installing-ubuntu-804-hardy-heron-on-your-eee-pc/](http://www.simplehelp.net/2008/07/28/a-step-by-step-guide-to-installing-ubuntu-804-hardy-heron-on-your-eee-pc/)

---

### Post by SEMW on 2008-08-22
Personally, I checked it out and thought that beyond the patched kernel, the improvements didn't seem worth deviating from vanilla Ubuntu (everything's applyable by hand later if necessary anyway, and I'd rather know the exact areas which I'm changing from normal Ubuntu).  So I got hold of the patched kernel [seperately]("http://www.array.org/ubuntu/") and applied to to a normal Hardy installation.

(Depending on the model you may not be able to access the internet at all with the vanilla kernel, either wired or wireless; but the author of the patched kernel [gives deb packages]("http://www.array.org/ubuntu/setup901.html") that you can download seperately and put on whatever USB stick you're installing Ubuntu from.)

---

### Post by Poeli on 2008-08-22
I've installed it on my EEE pc900. I sometimes have internet problems (that it doesn't connect to my network). But for the rest I'm very happy with it. My EEE pc's battery life is now 2hrs30minuts, thats 1 hour longer than when i had windows on it.
Another problem is that I have problems with opening my hard drive of 8 gb. It always says that it isn't mounted or something...
Does anyone knows a solution to those problems?

---

### Post by SEMW on 2008-08-22
> **Poeli said:**
> 
Another problem is that I have problems with opening my hard drive of 8 gb. It always says that it isn't mounted or something...
Does anyone knows a solution to those problems?

First type ```
df
``` into a terminal to work out what the device name of the 8GB drive is (it's a flash drive, BTW, not a hard drive).  I'll assume it's /dev/sdb1.  Then type ```
sudo gedit /etc/fstab
```.  It will look something resembling this:

```
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=8b914ae5-a4ef-4528-b79e-e2e4882e0db9 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=66c82cc6-4def-4baa-b63c-5836bd4e2f93 none            swap    sw              0       0
/dev/sdc1       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd0       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0
```

Add the following line to the bottom:

```
/dev/sdb1        /media/storage     ext3        defaults,relatime,errors=remount-ro 0       2
```
Replacing /dev/sdb1 with whatever the 8GB drive is, and "storage" with whatever you want to call it.  Make sure the directory you're mounting it in exists!  ("sudo mkdir /media/storage").  (Personally, I'm mounting it as /home, but that's a little complicated to set up; Google around for a guide if you want to do this).

Whilst you're at it, comment out the cdrom rows (prepend #), to stop Ubuntu trying to find and mount nonexistent CD drives.

---

### Post by scottuss on 2008-09-02
Hi guys, I have used vanilla Ubuntu and the patched kernel, and now sometimes my Internet connection doesn't work too. I am connected to my network but pages will more often than not fail to load. Any ideas?

---

### Post by VMan on 2008-09-03
I put Ubuntu 8.04.1 on my EeePC 1000H.  Using adamm's kernel (mentioned and linked to in previous post), everything works great.  I have not had any problems yet. . . not do I expect any:guitar:

---

