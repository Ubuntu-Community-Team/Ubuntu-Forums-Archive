---
title: "Laptop hardware incompatible?"
date: 2008-12-29
forum: Hardware
---

### Post by Zim05 on 2008-12-29
For Christmas I got this HP laptop [http://www.circuitcity.com/ssm/HP-G60-127NR-15-6-Widescreen-Laptop-G60-127NR/sem/rpsm/oid/228105/catOid/-18746/rpem/ccd/productDetail.do#proddesc](http://www.circuitcity.com/ssm/HP-G60-127NR-15-6-Widescreen-Laptop-G60-127NR/sem/rpsm/oid/228105/catOid/-18746/rpem/ccd/productDetail.do#proddesc) . I was going to install Ubuntu as my main operating system instead of Vista. To test out Ubuntu for the first time I used Wubi and It seems to lag a lot. I'm guessing it might have to do with the Ubuntu not being compatible with the graphics card because it seems like the screen has a really slow refresh rate. Hopefully this has to do with Wubi =/. I was just wondering if Ubuntu is capable with all of the hardware on my Laptop before I replace Vista with Ubuntu.

---

### Post by Zim05 on 2008-12-29
Sorry to bump but its been 5 hours and the thread went to the third page :(

---

### Post by IQRules on 2008-12-29
I think the lag issue, indicates you might need Nvidia Proprietary driver.
I just fixed it on my FX 1400 by using EnvyNG tool. 
$ apt-cache search envyng
envyng-core - install the ATI or the NVIDIA driver
envyng-gtk - dummy package to envyng-core
envyng-qt - install the ATI or the NVIDIA driver

It can take some time to fix anything up. Good luck.

---

