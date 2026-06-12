---
title: "can't install driver for asus en8400gs"
date: 2009-01-03
forum: Hardware
---

### Post by Afkpuz on 2009-01-03
So, I've just assembled a new computer and am hung up on my video card.  Aparently, the geforce 8400gs is not as easy to use with ubuntu as my other nvidia cards.  Anyway, after installing the propritary driver via hardware drivers, the driver won't take.  Upon reboot, I can't even start X.  Very frustrating as I found a compatibility hole that I've never had to deal with.  Can anyone help with this?  Also, I'm running ubuntu 8.10

---

### Post by Pilo on 2009-02-05
The same thing is happening to me, were you able to solve your problem?  In my Xorg.0.log:
(II) NVIDIA dlloader X Driver 177.82 Tue Nov 4 16:56:15 pst 2008
(II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
(II) Primary Device is:
(EE) No devices detected.

Obviously at that point X fails to load.  This is with a clean install of 8.10 just hours ago.  I installed, updated, rebooted, enabled nvidia drivers, rebooted and had this problem (I didn't modify xorg.conf or anything else).

Any suggestions would be appreciated, thanks.

---

### Post by Pilo on 2009-02-06
I fixed my problem, it was an incorrect BIOS setting (I had to set the default video card to pci-express instead of pci and disable sharing video processing with the onboard chipset).

Hopefully that may save someone else's headache.

---

### Post by Francewhoa on 2009-05-23
[Click here for ***      HOWTO: Install video card Asus EN8400GS Silent on Ubuntu 8.0.4 Desktop***]("http://ubuntuforums.org/showthread.php?t=1164800")

---

