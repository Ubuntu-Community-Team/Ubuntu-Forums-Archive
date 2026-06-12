---
title: "ubuntu 10.10 cannot find old nvidia graphics card"
date: 2010-10-10
forum: Hardware
---

### Post by fishkid257936 on 2010-10-10
I just installed ubuntu 10.10 and is not able to find my old nivdia graphics card. So, I installed the nvidia-96 package but still did not work (so I removed it.) Is Ubuntu 10.10 not supported with old drivers yet? Is there a way I can get it to work?

EDIT: After looking though my old posts, I found out that my driver is a *                 GeForce2 MX/MX 40.             *

---

### Post by xingular on 2010-10-10
Same problem here with a GeForce 3...

I think the old drivers were the -71, not the -96. 

I can't find them in sinayptic or Ubuntu Software Center.

No 3D, no openGL, no googleearth :(

---

### Post by davidmohammed on 2010-10-10
such old cards are not supported by the X system in meerkat - see [here]("http://ubuntuforums.org/showthread.php?t=1589796").  Looks like you'll just have to wait for the compatibility to be sorted... or go back to 10.04.

---

### Post by yo2boy on 2010-10-10
I guess I have to go back to 10.04 :(

---

### Post by Yellow Pasque on 2010-10-10
> **davidmohammed said:**
> Looks like you'll just have to wait for the compatibility to be sorted... or go back to 10.04.
..or just use open-source nouveau driver.

---

### Post by xingular on 2010-10-10
> **Temüjin said:**
> ..or just use open-source nouveau driver.

How to use? 

When nvidia-96 is not active I can't have hardware aceleration, desktop effects... When nvidia-96 is not active... is noveau working?

My situation is the same with privative or with nouveau :)

P. S. Noob here... hehehe.

---

### Post by cgroza on 2010-10-10
Any way to get 3d with nouveau?

---

### Post by davidmohammed on 2010-10-12
report [here]("http://ubuntuforums.org/showpost.php?p=9955270&postcount=6") of someone who has got these old graphics cards working with 10.10 - hope this works for you.

---

### Post by yo2boy on 2010-10-12
I also found this: [http://www.nvnews.net/vbulletin/showpost.php?p=2326233&postcount=5](http://www.nvnews.net/vbulletin/showpost.php?p=2326233&postcount=5)

---

### Post by fishkid257936 on 2010-10-13
nope. Still not working.

---

### Post by Laspac on 2010-10-14
I had the same problem with my Geforce fx 5200.
This driver solved it for me :
[https://edge.launchpad.net/ubuntu/maverick/+source/nvidia-graphics-drivers-173/173.14.28-0ubuntu1](https://edge.launchpad.net/ubuntu/maverick/+source/nvidia-graphics-drivers-173/173.14.28-0ubuntu1)

---

### Post by cascade9 on 2010-10-14
> **yo2boy said:**
> I also found this: [http://www.nvnews.net/vbulletin/showpost.php?p=2326233&postcount=5](http://www.nvnews.net/vbulletin/showpost.php?p=2326233&postcount=5)

Yep, the 96.xx drivers are going to work with xorg 1.9 (as used by 10.10)...... eventually. 

> **xingular said:**
> Same problem here with a GeForce 3...

I think the old drivers were the -71, not the -96. 

I can't find them in sinayptic or Ubuntu Software Center.

No 3D, no openGL, no googleearth :sad:

Geforce 3 should have been using 96.xx drivers. The 71.xx driver would work, but the 96.xx drivers are better for the GF3.

---

### Post by termin on 2010-10-14
same here, i went on "additional drivers" and it didn't detect it, and really wanna play some movies and games very badly

---

### Post by christian.remboldt on 2010-10-16
I have compiz working. check this out.
[http://ubuntuforums.org/showthread.php?t=1590367](http://ubuntuforums.org/showthread.php?t=1590367)

---

