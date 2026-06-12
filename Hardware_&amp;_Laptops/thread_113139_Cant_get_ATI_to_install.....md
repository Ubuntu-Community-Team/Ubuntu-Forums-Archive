---
title: "Cant get ATI to install...."
date: 2006-01-05
forum: Hardware &amp; Laptops
---

### Post by Bytebull on 2006-01-05
hi, I have been dabbling with linux for about a year. I'm a 4th semester college student at A.S.U majoring in Applied Science with minors in Digital Electronics Technology ( cisco networking certs, A+hardware certs, analog/digital certs, etc).

I am having a problem with ubuntu video driver installation. I have the following packages downloaded and have tried the official ATI recommendations for the command line installation and have hit a brick wall.

I have installed numerous packages using the command line or add applications app, but this one install has me against the wall. Details below.


ati-driver-installer-8.20.8-i386.run

fglrx_6_8_0-8.20.8-1.i386.rpm.

***** Ati's instructions ******
# Launch the Terminal Application/Window and navigate to the ATI Proprietary Linux driver you have downloaded
# Enter the command ./ati-driver-installer-8.20.8.run to begin the installation.

****************************************


I have tried and tried and searched the internet for sites and have found much information and tried all of it, but to no avail I cannot get my ATI Radeon 9700 drivers installed for this linux OS.

I would appreciate any help from any knowledgable Ubuntu users on this topic.

thank you.

./ edit

Inspiron 9100 laptop DELL
2.9 Dual processor w/Hyper Thread
1Gb RAM DDR
ATI Radeon 9700 mobility

---

### Post by Sef on 2006-01-05
Read this link:  [http://ubuntuforums.org/showthread.php?t=112079]("http://ubuntuforums.org/showthread.php?t=112079")

Then this link:  [http://ubuntuforums.org/showthread.php?p=423584]("http://ubuntuforums.org/showthread.php?p=423584")

That should get you going.

---

### Post by Bytebull on 2006-01-06
thanks

---

### Post by Bytebull on 2006-01-06
done all that...

I have a laptop... and it's not working for My ATI...


sheeeeevo.

---

### Post by ysse on 2006-01-06
ATI graphic cards aren't the easiest thing to get working, believe me. But now I have  a laptop, 2.0 GHz Pentium M, ATI Mobility 9700, with 3D-acceleration and working hibernate + suspend.

Witn **nothing** but Ubuntu packages installed using synaptic.

Kernel version is 2.6.12-10-686.
ATI driver package: xorg-driver-fglrx version 6.8.0-8.16.20-0ubuntu16.1

After installing the xorg-driver-fglrx, all I did was save a copy of my /etc/X11/xorg.conf, and then run sudo fglrxconfig, mostly with default answers. That gave me a working screen setup, but trashed touchpad settings, so I manually put back the inputdevice sections from my saved xorg.conf.

I admit that it isn't the latest driver, but it works!

---

