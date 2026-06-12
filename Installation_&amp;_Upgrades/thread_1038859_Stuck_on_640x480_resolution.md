---
title: "Stuck on 640x480 resolution"
date: 2009-01-14
forum: Installation &amp; Upgrades
---

### Post by M_Mungo on 2009-01-14
HELP!  I'm currently displaying advanced symptoms for frustration.  I cannot adjust my resolution after trying for over 1 month.

I began with a Dell Dimension 2300:

P4 1.8Ghz
1GB RAM
Newly formatted 80GB HD

No Video Card:
* 00:02.0 VGA compatible controller: Intel Corporation 82845G/GL {Brookdale-G}/
GE Chipset Integrated Graphics Device (rev 01)

I was able to install Ubuntu 8.10 using only "safe of low graphics mode" so,
I assume this is due to the lack of a good graphics card.  I purchase a new Radeon 9000 256MB (which is supported according to previous messages written on this site) in an effort to correct the issue.

* I cannot find an up to date driver from AMD/ATI that is compatible with XORG 7.4

* I cannot seem to get the open source driver.

* I cannot work on a simple word document, while being able to view less than 25% of it at one time, without grinding my teeth.

I'm very new to Linux and could really use some direction.  I would prefer to become more proficient with Ubuntu and open source.  My goal (if possible) is Compiz.  Can someone help or - recommend a good dentist?

Thanks

---

### Post by holy1crusader on 2009-01-15
I also have a Dell Dimension 2300 with a similar setup and the same problem with the onboard graphics.  Can boot in safe graphics mode, but when booting normally I can only see my mouse cursor and either a tan or black screen. I feel your frustration!

---

### Post by DocHoliday52090 on 2009-01-15
We're all stuck here with the same problem (except the person above me). 

Radeons R300 and below are suffering because fglrx isn't working correctly and the open source drivers aren't detecting the correct resolution.

---

### Post by holy1crusader on 2009-01-19
UPDATE:
I tried to install Fedora 10 and encountered the same problem as with Ubuntu.  I then installed OpenGEU with no graphic issues and it is working great!:D

---

