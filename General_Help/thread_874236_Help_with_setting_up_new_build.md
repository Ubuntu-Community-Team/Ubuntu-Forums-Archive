---
title: "Help with setting up new build"
date: 2008-07-29
forum: General Help
---

### Post by Kobskid on 2008-07-29
I have been looking around here and I noticed there are a lot of really helpful people on here and I'm hoping you can all help me.
This is my first venture into Linux/ubuntu.  I'm looking to set up mainly a samba server but if I get interested I might look at other things to do with it.
But here is the problem I am having.  I cant write to one of my drives.  I have 2 hard drives and an external.  My second drive is filled with videos and other files as is my external.  I have Ubuntu installed on my first hard drive, which is a 500GB, with a home partition of 20 GB and a root of 10GB.  So I still have over 400GB free.  No matter how I format the partition of 400+GB I can not write to it.  Maybe I am not bright and I am missing something but I cant make new folders or anything on this first drive.

Also if anyone has a great guide on how Samba works I would appreciate that so I can see what I all want to do with that.

---

### Post by ibuclaw on 2008-07-29
[Here is a good Samba Share walkthrough.]("http://2tap.com/2007/04/22/sharing-files-between-a-windows-guest-and-ubuntu-host-using-vmware-and-samba/") If you follow it up until the "Bridge/NAT Networking" section.

As for your hard-drive, what filesystem is it?
```
sudo fdisk -l
```
```
cat /etc/fstab
```

Regards
Iain

---

### Post by Kobskid on 2008-07-29
It is ext3 right now, but its completely empty so I can reformat it to anything right now.

---

### Post by ibuclaw on 2008-07-29
What are you going to use the filesystem for?

If it's for backing up/storing music/etc. Then a simple line in your fstab file should fix it and get the permissions right.

Can you post the output of the two command I gave above?

Regards
Iain

---

### Post by Kobskid on 2008-07-29
> **tinivole said:**
> What are you going to use the filesystem for?

If it's for backing up/storing music/etc. Then a simple line in your fstab file should fix it and get the permissions right.

Can you post the output of the two command I gave above?

Regards
Iain
It will be for file sharing with my other drives.


```
Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000c83

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1245    10000431   83  Linux
/dev/sda2            1246        3735    20000925   83  Linux
/dev/sda3            3736        3984     2000092+  82  Linux swap / Solaris
/dev/sda4            3985       60801   456382552+  83  Linux

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0d33c523

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       60801   488384001    7  HPFS/NTFS

Disk /dev/sdc: 750.1 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe2811465

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1       91201   732572001    7  HPFS/NTFS

```

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=8f44218d-9f43-4e00-aa89-a07879970ae2 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda2
UUID=03f66df8-b5cf-4e4e-8fb0-8c4dbd81f009 /home           ext3    relatime        0       2
# /dev/sda3
UUID=ebd9a3b9-c2e0-46a1-8db2-8adc0273f1f6 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0


```

---

### Post by Kobskid on 2008-07-29
Well I was fiddling with it, dont really know what I did.  But I can write files to it now.

---

### Post by ibuclaw on 2008-07-29
Most probably chown and chmod on the top structure of the filesystem.

As for fstab line
```
/dev/sda4 /media/sda4           ext3    rw,relatime        0       2
```

Regards
Iain

---

