---
title: "Acer Aspire One Webcam Won't Work"
date: 2008-12-26
forum: Hardware
---

### Post by Coder543 on 2008-12-26
Greetings, I have been pleased with Ubuntu being run on my Acer Aspire One. However, it has come to my attention that neither Cheese nor Camorama will display the video feed from my webcam even though they claim that they are. Also worth noting is that luvcview will display the feed. Please, I would like to use something *better* than luvcview to use my webcam. Cheese and Camorama are much more developed.

---

### Post by Coder543 on 2008-12-26
(bump)

---

### Post by OutOfReach on 2008-12-26
I would like to know too, luvcview works like a charm but Cheese seems more 'easier to use', Since I will not be the one using the Aspire One.

---

### Post by geraldo.medrano on 2009-01-04
In Cheese, try setting the resolution to 176 x 144:

Edit -> Preferences -> Resolution

---

### Post by rhy on 2009-01-15
> **geraldo.medrano said:**
> In Cheese, try setting the resolution to 176 x 144:

Edit -> Preferences -> Resolution

Works for me.

---

### Post by stratosgear on 2010-03-02
Cheese on the 9.10 live cd of ubuntu works fine.

On the installed version (on the same netbook) leaves me with cheese (or camorama) not working.

luvcview is working though...

I have no idea what's wrong or how to bebug it... :(

---

### Post by Jragon on 2010-12-26
It does not work on 10.10 with the resolution a 176 by 144

---

### Post by ki4jgt on 2011-04-16
BUMP. . . It also does not work for adobe flash??? I can see a very unclear image of myself.

---

### Post by moondog20 on 2011-11-11
Even on Ubuntu 11.10 my webcam doesn't work. I know that jiggling my screen helps... Sometimes it'll work, but the vast majority of the time it will not.


kyle@science:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 003: ID 064e:d101 Suyin Corp. Acer CrystalEye Webcam
Bus 001 Device 003: ID 05ac:129e Apple, Inc. iPod Touch 

I know that it's being recognized, but it will not work with any application.

---

### Post by ki4jgt on 2011-11-23
Anyone have a fix for this? It's been broken since I graduated and I REALLY would like to use my inbuilt webcam.

---

### Post by ki4jgt on 2011-11-23
FIXED: Guys, apparently the contrast is set VERY HIGH on the camera. To get it working, you simply turn the contrast down.

---

