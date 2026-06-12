---
title: "hard drive setup - 4096B sectors, WD EARS"
date: 2011-02-18
forum: Hardware
---

### Post by Zenze on 2011-02-18
I am trying to set up a new hard drive I got for my machine but and running into some issues. The drive is a new WD EARS drive that uses 4096B sectors, instead of 512B sectors. I heard that Ubuntu 10.10 was patched to work with this, but I don't know if thats true or not.

I have been reading a few guides in order to partition the drive correctly, however I don't think that I did everything right.

Here is what I get from fdisk:

```
Disk /dev/sdc: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0004956b

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1              63  3907024064  1953512001   83  Linux

```

This seems to be incorrect to me. My understanding is the main thing needed to get drives set up correctly for 4096B sectors is having the start and end sectors be divisible by 8 (no idea why this is so important though), which my start sector is obviously not.

Where do I go from here? I really need to get this drive working correctly.

---

### Post by finite9 on 2011-06-08
read this article, which should give you the info you need:

[http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/index.html?ca=dgr-lnxw074KB-Disksdth-LX]("http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/index.html?ca=dgr-lnxw074KB-Disksdth-LX")

---

### Post by mastablasta on 2011-06-08
apparently this is available since 10.04 see release notes: [https://wiki.ubuntu.com/LucidLynx/ReleaseNotes](https://wiki.ubuntu.com/LucidLynx/ReleaseNotes)
 
Under partition alignment.

---

