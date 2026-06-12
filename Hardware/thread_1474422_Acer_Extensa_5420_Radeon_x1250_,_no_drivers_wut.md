---
title: "Acer Extensa 5420 Radeon x1250 , no drivers wut?"
date: 2010-05-06
forum: Hardware
---

### Post by FlapBags on 2010-05-06
Ok, ATI has a driver listed for Linux x64 for the Radeon x1250 and this is what happens when you run it, I got the same results with Fedora 12 also.

  Ubuntu runs GREAT on my laptop, but 3D acceleration would be nice, if I can get this driver, I will be set free of Microsoft almost completely. Any ideas? Please do not suggest I buy a new laptop, its a Turon X2 and its powerful enough for me. Thanks!

Acer Extensa 5420  
Turion 64 X-2 TL-58 @1.9ghz
ATI Embedded Mobile Radeon x1250
2gb DDR2 
160gb Toshiba MK series, the ones with bad sectors ;( <-- direct decendant of the IBM "DeathStar" Series of drives
Atheros Mini PCIx
Marvell GB Ethernet

This is the wonderful surprise I get when I run ATi`s recommended driver.

root@Ubuntu-acer:~# sh /home/devadmin/Downloads/ati-driver-installer-9-3-x86.x86_64.run
Created directory fglrx-install.zL6f67
Verifying archive integrity... All good.
Uncompressing ATI Proprietary Linux Driver-8.593...........................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................
==================================================
 ATI Technologies Linux Driver Installer/Packager 
==================================================

Error: ./default_policy.sh does not support version
default:v2:x86_64:lib32::none:2.6.32-21-generic; make sure that the version is being
correctly set by --iscurrentdistro

Removing temporary directory: fglrx-install.zL6f67
root@Ubuntu-acer:~#

---

### Post by FlapBags on 2010-05-06
Shameless bump...

Anyone know of  another source for drivers?

---

### Post by Braik on 2010-05-07
Hi, I have the same issue with my ATI X1300, what your output tells you is that your UBUNTU distro (it is Karmic, or Lucid) is no more supported by the drivers they propose.
 
Don't try to force the installation, it would stop your display.
 
Since ATI have stopped the support it is to Canonical to support your card drivers, but by the moment it does not work for me either but if I find a solution I will tell you.
 
Cheers

---

### Post by Omega420 on 2011-12-18
I got to bump this its over a year old and no help yet? i got this same laptop and am trying to update the hardware for it, im currently running Fedora 16 cuz its the only linux that has the wifi drivers for it! lol i would LOVE to use Linux mint but no wifi drivers come with the DVD 64 download. and in order to GET the drivers i need to be online to download the wifi drivers, and with no land line for this laptop thats a problem. (but not this threads problem) anyway is there a place where i can get all the drivers that work THIS laptops hardware? i also need to get my webcam (Crystal Eye) working BEFORE Xmas so i can skype my Family in the mainland.

---

### Post by MoreOrLess on 2011-12-18
I could HELP you IF you didn't TYPE like THIS....

---

### Post by overdrank on 2011-12-18
Hi and welcome. Please start a new thread with your issues. Back to sleep thread :)

---

