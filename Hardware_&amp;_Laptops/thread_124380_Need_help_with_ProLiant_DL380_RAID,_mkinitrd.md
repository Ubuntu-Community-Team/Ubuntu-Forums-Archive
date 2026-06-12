---
title: "Need help with ProLiant DL380 RAID, mkinitrd"
date: 2006-02-01
forum: Hardware &amp; Laptops
---

### Post by kmcgregor-cow on 2006-02-01
We have a Compaq ProLiant DL380 (G1, 2xPentium III) with two 36 GB drives on one RAID controller (the built-in one) and four 145 GB drives on the auxilliary RAID controller. The Ubuntu Server 5.10 installer detects all hardware correctly, and installs Linux on the first drive (RAID 1 volume, the two 36 GB disks).

After reboot, the error message reads
```
Loading, please wait...
ALERT! /dev/ida/c0d0p1 does not exist. Dropping to a shell!
```

I'm guessing the stock kernel doesn't contain a driver for the RAID cards we have. Would it help to create a initrd which contained it? Would someone please give me some help in setting this up? I've done some reading on mkinitrd, but I haven't tried it, and I'm unsure when or how I would put it on a partially installed system.

Thanks for any help!

---

### Post by Adam B. on 2006-02-23
Bump.

I'm having this same exact problem.  Has anyone found a solution?

---

### Post by kmcgregor-cow on 2006-02-24
There's a workaround or two described in this thread:
[http://ubuntuforums.org/showthread.php?t=82466](http://ubuntuforums.org/showthread.php?t=82466)

I also found it in the Ubuntu bug-tracking system here:
[https://launchpad.net/distros/ubuntu/+source/initramfs-tools/+bug/26632](https://launchpad.net/distros/ubuntu/+source/initramfs-tools/+bug/26632)

---

