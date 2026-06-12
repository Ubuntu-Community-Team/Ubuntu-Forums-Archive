---
title: "Dell Optiplex gx270 Install faults - ubuntu 9.04"
date: 2009-09-23
forum: Installation &amp; Upgrades
---

### Post by evilpsych on 2009-09-23
Ok. I've got a Dell Optiplex GX270 (actually i have 6 identical ones with same problem) with latest (A07) bios, 500gb SATA hd, 512Mb RAM. These units have been running XP fine for months. Today I've attempted to install ubuntu 9.04 on these units. This installs just fine on older hardware than the Dells with no issue. I have attempted the standard install - which hangs before any installation can take place... so no successful installation there. 

I do get apparent successful installations with both the alternate install CD and the Dell Factory Reinstall  of 9.04 via USB Key. The system appears to be running fine and then it gets to the user login screen, whereupon i hear a system speaker 'ding' or 'donk' and the mouse freezes, keyboard freezes, and you cannot login. 

All of these systems have the integrated intel graphics chips, and by the looks of the login screen, the resolution appears to be just fine... As the gx270 seems to have had successful installations in the past by all HCL lists i've been able to find.. does anyone have an idea on this intriguing issue? 

I haven't ruled out the video card just yet (these are compact machines and I don't have a half-height AGP card), but flat out hardware failure doesn't seem to be a problem, more of a incompatibility?

---

### Post by evilpsych on 2009-09-24
I've tracked the issue down to the SATA Harddrive i'm using - a Samsung 500gb drive that's brand new. This is odd because the installs have not havd a problem seeing the drive, just booting from it.

---

### Post by BuntuFreak on 2009-12-22
> **evilpsych said:**
> I've tracked the issue down to the SATA Harddrive i'm using - a Samsung 500gb drive that's brand new. This is odd because the installs have not havd a problem seeing the drive, just booting from it.

Okay, I just picked up a Optiplex gx270 minitower used. It has 3 IDE drives : Seagate(500GB) and 2 x Samsung(160GB). Wanted to ask if you resolved your issue. I plan to use this machine as a file server. Did you narrow down the problem to the SATA or Samsung? I ask because I also plan to install a 250GB SATA to give me upwards of 1 TB of storage :-)

Thanks in advance.
P.S. I'll probably go with Ubuntu 9.10 but I'm thinking it doesn't matter.

---

