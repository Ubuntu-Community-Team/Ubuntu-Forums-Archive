---
title: "Ubuntu hanging on boot with SCSI jukebox attached"
date: 2008-06-15
forum: Hardware
---

### Post by mjbraun on 2008-06-15
I have a [JVC MC-1200 cdrom jukebox ]("http://www.kintronics.com/JVC/spec1000.htm") attached to an Adaptec 2940UW series SCSI controller. This is on Hardy with kernel 2.6.24-18-generic. 
While I can boot with the jukebox disconnected, when it is connected, the boot process hangs.

I used to not have this problem until I upgraded from a previous kernel (which one, I cannot remember). The Adaptec identifies the Jukebox, and the device begins to initialize (which takes awhile as it has to check the state of the 200 cd slots). On the console it reads:

```
Begin: Waiting for root file system... ...
Done.
     Check root= bootarg cat /proc/cmdline
     or missing modules, devices: cat /proc/modules ls /dv
ALERT! /dev/disk/by-uuid/5767f0bf-9340-4c3a-9e2b-7afe3b1114e5 does not exist. Dropping to a shell.

```


How should I proceed to diagnose and troubleshoot this problem? Any suggestions?

---

### Post by jackhe22 on 2008-06-15
Ubuntu thinks its the drive with Ubuntu on it... I reccomend new boot perameters, but not being a Linux genius, I cant give accurate perameters.

---

### Post by mjbraun on 2008-06-15
By the by: I should mention that for some reason kernel 2.6.22.-14-generic boots just fine. I suspect part of the problem is that the system hangs while the jukebox initializes (which takes on the order of 5 minutes). Why could have changed to permit one kernel to work but subsequent kernels to cease being functional?

---

