---
title: "Ubuntu 8.04 on compaq cq50 110em problems"
date: 2008-10-06
forum: Hardware
---

### Post by Dean Man on 2008-10-06
Wondering if anyone could help me fix some of my problems on my laptop. Just bought a compaq 110em that has a nivida 8200m graphics chhip on it and a athores 5007 wireless card. I got the graphics working ok..ish, there are no proper drivers for it but one seems to work for it, but it is not great. My real problem is the wireless card, cant get it working no matter what i do, tried using the program in system-administration that uses vista's drivers..that didnt work. Tried madwifi but nothing seems to work. 
Does anyone else have this laptop working with ubuntu 8.04?

I do have ubuntu installed on my pc and everything is working GREAT, not one problem apart from my sound but everything else is working ok. 

Any help would be much obliged.

---

### Post by valavanisalex on 2008-10-29
I didn't get Hardy to install, but i386 Intrepid beta works fine if you use the alternative installation CD.

Once you've got it installed, connect it to a wired network and install linux-backports-modules-intrepid.  This will add the ath5k kernel module, which you need for the Atheros wireless LAN adapter.  Reboot, and hopefully it'll work.

I'm really not a linux expert so if this method doesn't work, I can't really add any further suggestions!  I'd appreciate any advice about getting the AMD64 installation CD to work.  At the moment, it appears to kernel panic when booting the installer.

---

### Post by drmato on 2008-10-31
Same problem with 8.04 and 8.10, AMD64 versions...

My laptop is Compaq CQ50 115... :confused:

---

### Post by Dean Man on 2008-11-01
got both of them working now. 
I would really go for the 32bit versions guys as 64bit is pretty unstable at the minute, and there is not really much of a difference in speed between the two versions.

---

### Post by fuzzyworbles on 2008-12-07
yeah, i get a kernel panic w/ 8.10 AMD64 on a compaq cq50-116LA too... installing 8.04.1 i386 right now.

my model uses a 64bit chip, so i dunno what's up. does the ubuntu installer warn the user if they're attempting to install on a non-64 bit platform, or does it just freak out like this instead?

---

