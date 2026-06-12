---
title: "Install fails on SDHC-Card"
date: 2009-01-23
forum: Installation &amp; Upgrades
---

### Post by Smokeympot on 2009-01-23
hi,
i try to install ubuntu 8.10 from live_cd on my HP 2530p elitebook (support sdhc).
the installer can format the device and start the installation. 
it fails at the end of the installation "Could not install grub".

i found an topic about the problem -> **"Debian cannot be installed on bootable SD cards"** [http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=498568](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=498568)
the problem is the wrong mapped "SDHC-Device" 

**ubuntu maping: /dev/mmcXXXX and it should be /dev/sdX **

i have already install the new debian installer without any difference. :(

hope anybody could help me

---

