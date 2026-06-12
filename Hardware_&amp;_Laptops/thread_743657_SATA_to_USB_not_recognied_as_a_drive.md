---
title: "SATA to USB not recognied as a drive"
date: 2008-04-02
forum: Hardware &amp; Laptops
---

### Post by lsutiger on 2008-04-02
Here is the problem:
I have a new hard drive that I want to clone to. I have a USB to IDE/SATA connector that works flawlessly when I have and IDE hard drive connected. Now I have a SATA drive connected, but it does not register as a drive in nautilus. But here is response from the CLI:
```
complexity@linux-1501:~$ sudo fdisk -l
[sudo] password for complexity:

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xf0000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1216     9767488+  83  Linux
/dev/sda2            1217        9483    66404677+  83  Linux
/dev/sda3            9484        9729     1975995   82  Linux swap / Solaris

Disk /dev/sdb: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

Disk /dev/sdb doesn't contain a valid partition table

```

I am at a loss here...google returns too much non relevant info.So the OS understands that the drive is there but how do I format it/make a partition table?

Any help is well appreciated!

EDIT: I formated and it is now seen as a disk in Nautilus, but I am getting the same response from fdisk

---

### Post by cairnsww on 2008-07-17
I have the same problem. Surely it can't be difficult?

---

### Post by lsutiger on 2008-07-17
After I formatted, I cloned the disk and all went well! So try formatting.

---

### Post by cairnsww on 2008-07-18
How do I format the disk if I can't see it?

---

### Post by lsutiger on 2008-07-18
If you see something like this:
```
Disk/dev/sdb: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

Disk /dev/sdb doesn't contain a valid partition table
```


type:
```
mkfs -t <the filesytem you want> /dev/sdb (replace this for what your fdisk -l lists) 
```

---

