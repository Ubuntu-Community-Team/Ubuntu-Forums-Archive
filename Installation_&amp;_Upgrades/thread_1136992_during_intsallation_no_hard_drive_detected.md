---
title: "during intsallation no hard drive detected"
date: 2009-04-25
forum: Installation &amp; Upgrades
---

### Post by araghia04 on 2009-04-25
_**Helllpppppppp.**_
Im trying to install ubuntu on my system
xfx 750a mobo
amd x2 64
3gb ram
250gb samsung sata
320gb maxtor sata

when it gets to the fourth out of the seventh stage in installation it boots up the disk partioner but no hard drives are detected. i have tries it with one hard drive at a time as well but still same result.
Any ideas. 
Thanks In Advance x

---

### Post by sandbird on 2009-04-25
Linux is not working with SATA disks right out of the box.
You'll need to have either a PATA disk or to install it on VMWARE or something.

---

### Post by louieb on 2009-04-25
Did you browse your hard drive prior to the install? That will mount the drive and confuse the installer.  Try running the installer option off the 1st menu.

Another reason is a non-standard partition table.  Some partition editors can create partitions in a way that the Ubuntu installer doesn't like. 

IF you have internet with the live CD. Open applications>accessories>terminal and run 
```
sudo fdisk -l
``` 
lowercase L at the end. This will display your hard drives partition table. 
copy and paste the output in your next post. (enclose it in code tags - use the # symbol to do that.

---

### Post by autocrosser on 2009-04-25
Also look at my comment in this thread:  [http://ubuntuforums.org/showthread.php?t=1137167](http://ubuntuforums.org/showthread.php?t=1137167)

---

