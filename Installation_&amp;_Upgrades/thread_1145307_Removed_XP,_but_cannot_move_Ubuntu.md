---
title: "Removed XP, but cannot move Ubuntu"
date: 2009-05-01
forum: Installation &amp; Upgrades
---

### Post by sidewalkcynic on 2009-05-01
So I successfully removed Windows XP with GParted - I don't use it, and I heard that I can get faster response if the operating system is located at the beginning of the Hard Drive.
...And of course I don't want to go through the hassle of re-installing

I put the live disk in and get to the GParted application, and graphically move the /dev/sda2 over, but it returns an error after about ten minutes. I saved the report, but lost it because I thought it was saved to my root, and not some convoluted live disk root...

Anyway, any body have any tips for repartitioning to maximize speed?

I have an old laptop with only 256 Mb RAM, and I heard I should have double that in swap space, and I was wondering if that should go right next to the ext2?

I would also like to do the partitioning the home, and I have another partition I would like to make, as well - to hold, basically, pages from Wikipedia - it's a reference library I have.

Any ideas?

---

### Post by sidewalkcynic on 2009-05-01
```
fdisk -l
Disk /dev/sda: 10.0 GB, 10056130560 bytes
240 heads, 63 sectors/track, 1299 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes
Disk identifier: 0x65e032e4

   Device Boot      Start         End      Blocks   Id  System
/dev/sda2             407        1254     6410880   83  Linux
/dev/sda3            1255        1299      340200    5  Extended
/dev/sda5            1255        1299      340168+  82  Linux swap / Solaris

``````
fdisk -lu

Disk /dev/sda: 10.0 GB, 10056130560 bytes
240 heads, 63 sectors/track, 1299 cylinders, total 19640880 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x65e032e4

   Device Boot      Start         End      Blocks   Id  System
/dev/sda2         6138720    18960479     6410880   83  Linux
/dev/sda3        18960480    19640879      340200    5  Extended
/dev/sda5        18960543    19640879      340168+  82  Linux swap / Solaris

```

---

### Post by logos34 on 2009-05-01
> **sidewalkcynic said:**
> I put the live disk in and get to the GParted application, and graphically move the /dev/sda2 over, but it returns an error after about ten minutes. 

try using the [official Gparted live cd/usb.]("http://gparted.sourceforge.net/livecd.php")  Sometimes it works where the version on the ubuntu live cd fails.

---

### Post by Mark Phelps on 2009-05-01
Second what logos34 said.

The version of GParted on the Ubuntu LiveCD is updated only when the CD image is generated bu Canonical, whereas the version on the GParted LiveCD is constantly being updated -- adding new features and fixing bugs.

You may have better experience with the latest version of the GParted LiveCD.  You can get it from distrowatch.com.

However, that said, be prepared to wait a long time for the partitioning to be done -- maybe, several HOURS. The screen will blank after a while.  Pressing the space bar will restore the screen.  But, don't interrupt it or abort it or you'll be left with a mess you may not be able to fix.

---

### Post by sidewalkcynic on 2009-05-01
Well, if it's going to take hours, I just as well, just do a re-install.

---

