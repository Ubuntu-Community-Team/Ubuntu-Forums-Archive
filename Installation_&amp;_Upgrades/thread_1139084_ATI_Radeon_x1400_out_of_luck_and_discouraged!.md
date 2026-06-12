---
title: "ATI Radeon x1400 out of luck and discouraged!"
date: 2009-04-26
forum: Installation &amp; Upgrades
---

### Post by nelsonhogg on 2009-04-26
For the first time in several upgrades, I am very disappointed with ubuntu and have to either downgrade or seek another distro. My Lenovo T60 with radeon x1400 is stops at the mangled login screen. There seems to be no solution to this problem that I can find other than waiting but my functioning 8.10 system is now history. Why couldn't the installation warned of this problem? No wonder people avoid linux.

---

### Post by Mark Phelps on 2009-04-27
Sorry, think you're basically out of luck regarding any ATI driver support.  I have an X1600 and as of Catalyst 9.4, ATI is no longer supporting my card.  So, it's open source or nothing.

As to downgrading, there's no simple way to do that.  You would have to reinstall an older version to go backward.

As to autodetecting problems to prevent installation, that's what the LiveCD environment is for -- to boot from it and see how well the new version behaves with your machine.  If you skip that option and go straight to upgrade, you then have only two choices -- fix the problem or reinstall the old version.

---

### Post by Cybie257 on 2009-04-27
> **nelsonhogg said:**
> For the first time in several upgrades, I am very disappointed with ubuntu and have to either downgrade or seek another distro. My Lenovo T60 with radeon x1400 is stops at the mangled login screen. There seems to be no solution to this problem that I can find other than waiting but my functioning 8.10 system is now history. Why couldn't the installation warned of this problem? No wonder people avoid linux.

There is a reason the any *nix system will tell you to avoid "Upgrading", rather than a fresh install. Sure, upgrades *WILL* work, but they do require some tinkering. 

I have an X1300 ATI and attempted to switch to nVidia (which had some interesting issues - another story). When switching cards, I encountered the screen you are referring to. I've also encountered that with upgrades in the past. Here's what you can do (and will most likely work, hopefully).

Reboot and go into the (mind blank) "Safe Mode" option. It's not called that, but I'm blanking on the actual name. Then when it loads up, scroll the options screen down to "Try to auto fix x". This will re-write your X Configuration to some defaults based on the installation. You should then be able to continue to boot and have your new desktop show up. 

Try this and report back on any outcomes. 

-Cybie

---

### Post by nelsonhogg on 2009-04-27
> **Cybie257 said:**
> There is a reason the any *nix system will tell you to avoid "Upgrading", rather than a fresh install. Sure, upgrades *WILL* work, but they do require some tinkering. 

I have an X1300 ATI and attempted to switch to nVidia (which had some interesting issues - another story). When switching cards, I encountered the screen you are referring to. I've also encountered that with upgrades in the past. Here's what you can do (and will most likely work, hopefully).

Reboot and go into the (mind blank) "Safe Mode" option. It's not called that, but I'm blanking on the actual name. Then when it loads up, scroll the options screen down to "Try to auto fix x". This will re-write your X Configuration to some defaults based on the installation. You should then be able to continue to boot and have your new desktop show up. 

Try this and report back on any outcomes. 

-Cybie

Well, the outcomes are mixed. Booting the live CD works flawlessly. No video problems whatsoever. However, when I choose to use the "recovery mode" and "fix X" I'm no further ahead - still a garbled login screen.

I thought I would try a fresh install but, for reasons unknown to me, it thinks my disk is unpartitioned and I'm afraid it will overwrite the windows partitions (I dual boot).

Thanks for the suggestions. Nelson

---

### Post by StuartN on 2009-04-27
If you were using the proprietary ATI Catalyst driver (fglrx) in Ubuntu 8.10 and upgraded, then Ubuntu 9.04 will have switched to the open source ATI driver. The old fglrx installation may interfere with the new open source, in which case this guide might help:
[https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver](https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver)

---

### Post by nelsonhogg on 2009-04-27
> **StuartN said:**
> If you were using the proprietary ATI Catalyst driver (fglrx) in Ubuntu 8.10 and upgraded, then Ubuntu 9.04 will have switched to the open source ATI driver. The old fglrx installation may interfere with the new open source, in which case this guide might help:
[https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver](https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver)

That did it! Thanks so much. All seems to  be fine, at least for now.:)

---

### Post by Zebediah49 on 2009-04-28
I have a T60 with the X1400, still on 8.10 (it said that I couldn't use fglrx if I updated, so I said 'no'), and am wondering: with the open source driver, how is the performance on 3D stuff (games, etc.)?

---

### Post by Elfy on 2009-04-28
as far as I know the opensource driver is 2D only. I've not used ATi cards but I bookmarked this earlier [http://ubuntuforums.org/showpost.php?p=7165636&postcount=14](http://ubuntuforums.org/showpost.php?p=7165636&postcount=14)

---

### Post by Scooby1 on 2009-04-28
I am using open source driver on x850.  Can run all desktop effects in compiz smoothly. Never play graphics intensive games so dont know how it is for that. But you do get "good" 3D acceleration. From RadeonDriver wiki:

**Accelerated 3D support (r300, r400 and r500 series)**

 All these cards and derivatives have good 3D acceleration support 

9500 / R300 based cards
9600 / rv350 or rv360 based cards
9700 / R300 based cards
9800 / R350 or R360 based cards
X300 / rv370 based cards
X600 / rv380 based cards
X700 / rv410 based cards
X800 / R420 or R423 or R430 or R480 based cards
X850 / R480 or R481 based cards
X1050 / rv370 based cards
X1300 / R515 based cards
X1600 / R530 based cards
X1800 / R520 based cards
X1900 / R580 based cards
Xpress 200 / RS480 IGP
Xpress 200 / RS482 IGP for Intel
Xpress 200M / RS482 IGP
Xpress 1100 / RS482 IGP
Xpress 1150 / RS485 IGP
Xpress 1200 / AMD 690V / RS690C IGP
Xpress 1200 / AMD M690V / RS690MC IGP
Xpress 1250 / AMD 690G / RS690 IGP
Xpress 1250 / AMD M690 / RS690M IGP
Xpress 1250 / AMD 690G / RS600 IGP for Intel
Xpress 1270 / AMD M690T / RS690T IGP

HOWEVER, when upgrading to Jaunty I couldn't use the new EXA acceleration without X crashing. Had to go into xorg.config and put:

Option "AccelMethod" "XAA"

under devices. After that system is smooth as butter...

---

### Post by Elfy on 2009-04-28
> **Scooby1 said:**
> I am using open source driver on x850.  Can run all desktop effects in compiz smoothly. Never play graphics intensive games so dont know how it is for that. But you do get "good" 3D acceleration. From RadeonDriver wiki:

**Accelerated 3D support (r300, r400 and r500 series)**

 All these cards and derivatives have good 3D acceleration support 

9500 / R300 based cards
9600 / rv350 or rv360 based cards
9700 / R300 based cards
9800 / R350 or R360 based cards
X300 / rv370 based cards
X600 / rv380 based cards
X700 / rv410 based cards
X800 / R420 or R423 or R430 or R480 based cards
X850 / R480 or R481 based cards
X1050 / rv370 based cards
X1300 / R515 based cards
X1600 / R530 based cards
X1800 / R520 based cards
X1900 / R580 based cards
Xpress 200 / RS480 IGP
Xpress 200 / RS482 IGP for Intel
Xpress 200M / RS482 IGP
Xpress 1100 / RS482 IGP
Xpress 1150 / RS485 IGP
Xpress 1200 / AMD 690V / RS690C IGP
Xpress 1200 / AMD M690V / RS690MC IGP
Xpress 1250 / AMD 690G / RS690 IGP
Xpress 1250 / AMD M690 / RS690M IGP
Xpress 1250 / AMD 690G / RS600 IGP for Intel
Xpress 1270 / AMD M690T / RS690T IGP

HOWEVER, when upgrading to Jaunty I couldn't use the new EXA acceleration without X crashing. Had to go into xorg.config and put:

Option "AccelMethod" "XAA"

under devices. After that system is smooth as butter...

I'll be bookmarking that as well then :)

---

### Post by mongolianfireoil on 2009-05-01
Getting 1200 - 1400 fps with fglxgears using default driver for x1400 in jaunty. The desktop effects all work fine, in fact better than with the fglrx drivers. H.264 is a bit problamatic though. 
 
I won't be going back to the previous ubuntu because bluez works so amazingly well with jaunty. my bluetooth headset works flawlessly with skype and thats more important than watching h.264 movies.

---

