---
title: "Can not reinstall fglrx driver after 2.6.20-16 update"
date: 2007-06-05
forum: Hardware &amp; Laptops
---

### Post by grahams on 2007-06-05
After the update to 2.6.20-16 last week I have not been able to reinstall the fglrx driver and I'm running out of ideas.

I have a x1600 ATI controller which needs the ATI restricted driver. I was using 2.6.20-15 and the fglrx 8.36.5 (installed following this guide [http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide)), and everything was working well, 3D & beryl.

After the update to 2.6.20-16 the fglrx fails to start and my system can now only the vesa driver, which make it almost unusable. 

I have completely removed xorg-driver-fglrx and fglrx-kernel-source and then installed 8.36.5 again, following the above guide. The install appears to work, but fglrx is not loaded. lsmod |grep fglrx shows nothing, even after a modprobe. 

2nd attempt, remove all fglrx again and install old fglrx driver via synaptic. Again the install appears to work but fglrx driver is not loaded.

3rd attempt remove xorg-driver-fglrx etc. and install latest 8.37.6 driver. Same deal no fglrx driver. 

Does anyone know what I'm missing?

Also how can a kernel update screw up my system so badly? This update also blew away my swap space until I fix the partition's UUID.

---

### Post by grahams on 2007-06-05
Finally fixed !

I tried the standard ATI install method i.e. sh ./ati-driver-installer-8.37.6-x86.x86_64.run and all is running correctly. 

I'm not sure what was broken with the ubuntu package for fglrx and 2.6.20-16, but using the vendors install scrip works.

---

