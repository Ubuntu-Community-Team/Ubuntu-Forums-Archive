---
title: "Help Me,please. I can't Write&amp;Delete NTFS volumes on my USB hard drive"
date: 2007-05-20
forum: Hardware &amp; Laptops
---

### Post by killjanuary on 2007-05-20
I installed ntfs-3g. And I can success delete files on my local NTFS volumes harddisk .

But, I can't delete files on my USB hard drive. 

I am sure I clicked external driver support through ntfs-config.   :(

please help me......:(

My fstab is as follows:

```

proc /proc proc defaults 0 0
# Entry for /dev/hda3 :
UUID=8c6d54d3-a611-4dac-9809-6752417c8bf9 / ext3 defaults,errors=remount-ro 0 1
# Entry for /dev/hda1 :
UUID=1A18D54418D52015 /media/hda1 ntfs-3g defaults,locale=zh_CN.UTF-8 0 1
# Entry for /dev/hda4 :
UUID=3c145925-5005-4eab-a298-43ec0198c990 none swap sw 0 0
/dev/hdc /media/cdrom0 udf,iso9660 user,noauto 0 0

```

HDA3 is ext3 
hda1 is my local NTFS volumes. I can delete & write now.

```

sudo fdisk -l | grep NTFS

/dev/hda1   *           1       43905    22128088+   7  HPFS/NTFS
/dev/sda1               1       14024   112647748+   7  HPFS/NTFS
/dev/sda5           14025       30401   131548221    7  HPFS/NTFS


```
sda1 &sda 5 are my USB HARD DISKS.

---

### Post by killjanuary on 2007-05-20
Up

---

### Post by Milflyboy on 2007-05-20
I'm a *relative* noob myself and haven't tried to use ntfs-3g yet, but I've run into the permissions issue and set persistent mount options for my USB drive before.
Could it be a permissions issue? Try writing/deleting using sudo.

System Settings > Advanced tab > Disk and Filesystems. What are settings for the USB partitions? At some point you or the ntfs3g config thingy would have to override the default hotplug automount for those partitions, otherwise I'd think they'd be mounted as ntfs instead of ntfs-3g. Mount -l output would be helpful, as your fstab doesn't tell us about the USB partitions.

---

