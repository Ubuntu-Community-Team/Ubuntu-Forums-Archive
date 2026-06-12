---
title: "possible partition table failure"
date: 2009-03-13
forum: Hardware
---

### Post by greeker on 2009-03-13
hi, 

i have 2 hdd's on my pc that worked correctly till yesterday. i decided to switch to windows, so there partition magic suggested i fix an error on my harddisk that has winxp installed on it. and that was my false. i think partition magic got wrong and so i destroyed my partition table on that disk.

now:
(1)when i try to boot into windows it is not possible with my "defect" drive although i have winxp installed on both disks. when i plug out the defect disk, the other boots correctly.

(2)
i can only boot into ubuntu with both disks pluged in but there i see 10 partitions instead of 2 that really exist. 

So:
(1) i tried to chkdsk the defect harddisk under dos but the disk remains unrecognizable.
(2) under ubuntu i tried the commands:
- sudo ntfsfix
but it responds with 
"refusing to operate on read-write mounted device ..."

i have really important data on that disk
tnx a lot in advance

---

### Post by acidPython on 2009-03-13
What makes you think its your parition table? You could try using gparted/fdisk to check.

Personally i would try unmounting it/remounting it with ntfs-3g

---

### Post by greeker on 2009-03-13
i thing its the partition table cause partition magic said it would try to fix the partition table and i accepted.... bad decision... i am not sure what you mean with ntfs-3g... is it a different command??

---

### Post by greeker on 2009-03-14
is there any way to read any harddisk as long as the bios recongnizes it (like it is in my case) ??

tnx

---

