---
title: "External HD"
date: 2012-12-15
forum: Hardware
---

### Post by RenanRocha92 on 2012-12-15
Hi,

I've bought a Seagate external HD and it was working fine until I deleted a file.

After that My Ubuntu laptop refused to mount it again. I tested in a windows PC but to no luck, the windows too didn't mount it anymore.

Here's the result of the lsusb command:

"Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 0402:5606 ALi Corp. M5606 Video Camera Controller [UVC]
Bus 004 Device 002: ID 147e:2016 Upek Biometric Touchchip/Touchstrip Fingerprint Sensor
Bus 006 Device 002: ID 1c4f:0002 SiGma Micro Keyboard TRACER Gamma Ivory
Bus 005 Device 003: ID 2166:6649  
Bus 002 Device 011: ID 0bc2:2300 Seagate RSS LLC"

Is there any possible way i could recover the files in it?

Thx.

---

### Post by ahallubuntu on 2012-12-15
Does the drive make any noise at all when on?

Sometimes the enclosures in these things fail.  Sometimes the drive itself fails.  Hard drives fail all the time, so it wouldn't be a big surprise.

I would check S.M.A.R.T. status with GSmartControl (something you can install in Ubuntu).  Look at the Attributes tab (if you can get anything to show up at all).  Anything show up highlighted in red?

If there seem to be no apparent S.M.A.R.T. issues, open a terminal and type this:

```
sudo fdisk -l
```

Anything show up for sdb (assuming /dev/sda is your main hard drive)?  If so, maybe you can check the filesystem.  If it's still in Windows format (NTFS or FAT32), you should use Windows to check it (chkdsk).

---

