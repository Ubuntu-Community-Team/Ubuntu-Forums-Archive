---
title: "Kernel panic - encrypted LVM?"
date: 2008-09-30
forum: General Help
---

### Post by TygerFish on 2008-09-30
I just started running 64-bit hardy with an encrypted LVM on the OS hard drive.  Initially, everything ran okay.  But after updates, I started getting a strange error on boot complaining of an invalid compressed image format followed by a kernel panic.

This is the expanded error output:
```
/build/buildd/linux-2.6.24/drivers/rtc/hctosys.c: unable to open rtc device (rtc0)
BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
EDD information not available
RAMDISK: Compressed image found at block 0
invalid compressed format (err=2)
VFS: Cannot open root device "mapper/{this computer}-root" or unknown block(0,0)
Please append a correct "root=" boot option; here are the available partitions:
Kernel panic - not syncing: VFS: Unable to mount root fs on unknown-block(0,0)
```

---

### Post by TygerFish on 2008-09-30
After a few more reboots,the "invalid compressed format (err=2)" line has been replaced by the following:

```
invalid compressed format (err=1)
```

---

### Post by TygerFish on 2008-10-02
This has only been happening occasionally as of late, and when the computer starts up it runs flawlessly from 4-12 hours, at which point the filesystem on the encrypted drive appears to become read-only (which I first notice from Azureus popups complaining about it). 

Is this just imminent hard drive failure?  Or is it driver fatigue?  I've had the latter with video drivers before.

---

