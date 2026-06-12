---
title: "Cannot Mount External Hard Drive!"
date: 2007-11-15
forum: Hardware &amp; Laptops
---

### Post by bokorpop on 2007-11-15
[IMG]http://i235.photobucket.com/albums/ee27/bokorpop1/nomount.jpg[/IMG]

What now?

---

### Post by mdpalow on 2007-11-16
what does " sudo fdisk -l " give you? Post results here and tell us which drive you are wanting to be mounted....

...

---

### Post by bokorpop on 2007-11-16
After typing what you said I got this: 
----------------------
Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x04480448

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       30024   241167748+  83  Linux
/dev/sda2           30025       30401     3028252+   5  Extended
/dev/sda5           30025       30401     3028221   82  Linux swap / Solaris

Disk /dev/sdf: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1671954a

   Device Boot      Start         End      Blocks   Id  System
/dev/sdf1               2        4864    39062047+   f  W95 Ext'd (LBA)
/dev/sdf5               2        4864    39062016    7  HPFS/NTFS
-----------------
I want to mount the 40 GB drive.

---

### Post by mdpalow on 2007-11-16
sorry, should have asked for this too...

Can you post what your /etc/fstab   file says?

Thanks..

---

### Post by taurus on 2007-11-16
You cannot mount /dev/sdf1 since it's an extended partition!  You need to mount /dev/sdf5 instead.

```
sudo mkdir /media/sdf5
sudo mount -t ntfs /dev/sdf5 /media/sdf5
df -h
```

---

### Post by mdl76 on 2008-02-15
i love how people never finish these threads!!! 

what a waste.

---

