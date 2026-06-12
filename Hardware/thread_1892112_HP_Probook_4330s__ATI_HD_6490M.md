---
title: "HP Probook 4330s / ATI HD 6490M"
date: 2011-12-07
forum: Hardware
---

### Post by tomtomtomp on 2011-12-07
Hi I am trying to install ati ddrivers for this notebook. I tried via aditional drivers manualy and then reinstalling to linux mint 12 and again, but nothing works. Install goes fine but when I reboot multiple things happens randomly. Ubuntu loads up in low graphics mode and glxinfo reports error or booting hangs at checking batery state or it just hangs with [OK]... I tried reinstalling system and drivers like 7 times but nothing changed :S

Anyone can help? :)

---

### Post by BC59 on 2011-12-07
Look to this thread for the solution of the problem:

[http://ubuntuforums.org/showthread.php?t=1834732&page=2](http://ubuntuforums.org/showthread.php?t=1834732&page=2)

---

### Post by tomtomtomp on 2011-12-07
hmm... I didnt find any solution there. I want to make ati drivers work wit my graphics card not intel.

EDIT: i will try upgrading my BIOS :D

---

### Post by BC59 on 2011-12-07
I don't know if you installed the latest ATI driver

[http://linux.softpedia.com/progDownload/ATI-Radeon-Linux-Display-Drivers-Download-6719.html](http://linux.softpedia.com/progDownload/ATI-Radeon-Linux-Display-Drivers-Download-6719.html)

Worked for me.

---

### Post by tomtomtomp on 2011-12-07
Yes, I downloaded and compiled newest version of drivers and catalyst.

---

### Post by MoreOrLess on 2011-12-07
You probably have hybrid graphics and the proprietary ati driver won't work unless you can disable the intel IGP in the BIOS. So.. don't install the "additional drivers" when prompted. You may want to uninstall jockey altogether since it make makes nonsensical recommendations on hybrid GPU systems.

---

### Post by tomtomtomp on 2011-12-08
Yes, there are hybrid graphics and I can turn it off in BIOS but then Intel works and AMD is off :P ... is there any ways to install ati drivers for hybrid?

---

### Post by MoreOrLess on 2011-12-08
It's supposed to work with aticonfig in theory, but I don't recall too many reports of it actually working. [http://wiki.cchtml.com/index.php/Ubuntu_Oneiric_Installation_Guide#Hybrid_Graphics_and_Catalyst](http://wiki.cchtml.com/index.php/Ubuntu_Oneiric_Installation_Guide#Hybrid_Graphics_and_Catalyst)

---

### Post by tomtomtomp on 2011-12-09
Would it help if I turn off kernel module for intel integrated graphics?

---

### Post by tomtomtomp on 2011-12-09
Bump! :)

---

