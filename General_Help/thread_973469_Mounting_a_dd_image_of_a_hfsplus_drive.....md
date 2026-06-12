---
title: "Mounting a dd image of a hfsplus drive...."
date: 2008-11-06
forum: General Help
---

### Post by ragtag on 2008-11-06
I've been helping a friend recover lost data from his MacBook, and ran dd to copy the entire machine to my Ubuntu 8.04 machine. I've recovered most of the files (testdive and photorec are great), but when I try to mount the dd image with loopback using:

```
sudo mount -thfsplus -o loop diskimage /media/mntpoint
```

It doesn't work. I tried both with -thfs and -thfsplus, but neither does the job. A tail of /var/log/syslog ouputs.

Nov  6 23:24:26 vintage kernel: [107269.950673] hfs: can't find a HFS filesystem on dev loop0.
Nov  6 23:24:32 vintage kernel: [107275.600749] hfs: unable to find HFS+ superblock

Depending on which type of mount I tried.

I assume this is failing, because the image is the entire drive, and not a single partition. Is there any way to mount this on my machine?

---

### Post by uljanow on 2008-11-06
You could try to ignore the MBR of the disc and mount diskimage.part .
```
dd if=diskimage of=diskimage.part bs=512 count=1
```

---

### Post by dcstar on 2008-11-06
> **ragtag said:**
> I've been helping a friend recover lost data from his MacBook, and ran dd to copy the entire machine to my Ubuntu 8.04 machine. I've recovered most of the files (testdive and photorec are great), but when I try to mount the dd image with loopback using:

```
sudo mount -thfsplus -o loop diskimage /media/mntpoint
```
........
I assume this is failing, because the image is the entire drive, and not a single partition. Is there any way to mount this on my machine?

AFAIK the "loop" option mounts ISO images, not raw disk partition images.

The simplest option would be to create a new partition and then "dd" the image file to that new partition.

---

