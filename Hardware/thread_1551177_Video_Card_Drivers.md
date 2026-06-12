---
title: "Video Card Drivers"
date: 2010-08-11
forum: Hardware
---

### Post by gerowen on 2010-08-11
I recently reinstalled Ubuntu 10.04 64 bit on a desktop of mine.  I had loaned it to a school my wife was working for and just got it back so I just wiped it so I can use it as my work/school computer.  When I installed Ubuntu before (same version) it detected my ATI video card and installed proprietary drivers.  This time, it's not detecting that there are any proprietary drivers to install.  This is causing some programs not to start up such as Google Earth.  I tried manually installing fglrx and the xorg ati driver and neither of those actually worked.  I tried starting the Catalyst control center and got a message telling me the driver wasn't loaded or the hardware wasn't present.  Can anybody help me out?  I'm not exactly certain what video card it has, it's one that was added by a person who owned the machine before me, but I do remember the last time I installed it Ubuntu said it was an ATI card.

---

### Post by Fafler on 2010-08-12
So the kids swapped out your card for an older one? ;-)

No, do a lspci | grep VGA to identify your card.

---

### Post by cascade9 on 2010-08-12
> **Fafler said:**
> No, do a lspci | grep VGA to identify your card.

+1. 

Its probably an ATI GPU that is no longer supported by the ATI fglrx drivers.

---

### Post by gerowen on 2010-08-12
OK, so I have, according to Ubuntu:

```

ATI Technologies Inc RV380 [Radeon X600 (PCIE)]

```

So I went to ati.com and downloaded the Catalyst drivers recommended for the X6xx series of ATI Radeon cards, but when I try installing it the installer crashes early on with the following:

```

Error: ./default_policy.sh does not support version
default:v2:x86_64:lib32::none:2.6.32-24-generic; make sure that the version is being
correctly set by --iscurrentdistro

```

Just looking at this leads me to believe that it's not liking the new kernel I recently upgraded to.  Any ideas?

---

### Post by Yellow Pasque on 2010-08-12
Remove fglrx and don't install it again. Your card is no longer supported...
[http://wiki.cchtml.com/index.php/Ubuntu_Lucid_Installation_Guide#Removing_the_Driver](http://wiki.cchtml.com/index.php/Ubuntu_Lucid_Installation_Guide#Removing_the_Driver)

---

### Post by csvinter on 2010-08-13
Hi Gerowen, I think you have to remove the previous version first before installing the new one. Previously, I had a resolution problem (low resolution with low color bits), I removed all the Nvidia related installed packages and restarted the system again, Ubuntu prompts to load in the correct version after that. Not sure this would be able to help you.

---

