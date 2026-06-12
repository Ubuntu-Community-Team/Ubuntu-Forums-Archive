---
title: "problem to mount external hard disk"
date: 2009-09-16
forum: Hardware
---

### Post by esmailgad on 2009-09-16
Hi guys
Firstly I had a problem that my external hard disk is mounted as read only and I can not make any changes on it. With the mount command I tried to solve the prblem and now it is worth, Hardy refuse to mount it at all. Hardy says confusion in the premissions on this gard disk.
So what is the problem and, if possible,what is the solution
Best regards

---

### Post by ChumleyEX on 2009-09-16
What file system is it using?

---

### Post by esmailgad on 2009-09-16
I do not understand your question, but the error message that I obtain is " Invalid mount option when attempting to mount the volume 'Elements'".

---

### Post by ChumleyEX on 2009-09-16
um go to the terminal and type in 

```
sudo fdisk -l
```

This should list all of the drives attached to the computer.. Here is part of mine. (I have 10 drives)

```
Disk /dev/sdg: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xf7305a10

   Device Boot      Start         End      Blocks   Id  System
/dev/sdg1               1       19457   156288321   83  Linux

Disk /dev/sdh: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa4b57300

   Device Boot      Start         End      Blocks   Id  System
/dev/sdh1               1       60801   488384001    7  HPFS/NTFS

```


notice where is says System and then below is HPFS/NTFS 

Thats what I'm thinking you have, which isn't 100% compatible with ubuntu.. There should be a way to force it if you his details on the error. 

Something like this will help you out. If you don't use windows at all I would just partition it to ext3.. Have fun.

---

### Post by Keith Hedger on 2009-09-16
can you write to the drive as root? eg ```
sudo mkdir testfolder
```
try unmounting the drive and running fsck

---

