---
title: "[SOLVED] NTFS HD/partitions suddenly not mounting?"
date: 2008-11-06
forum: Hardware
---

### Post by Senuf on 2008-11-06
Hello. As always, let me start asking for an extra dose of patience, since english is not my native tongue.

I've seen that others posted some similar threads, but. although similar, I couldn't guess from them how to solve MY problem. Hence, this new thread.

Now, to the point.

My PC has two Hard Disks. One is NTFS; it has the main XP startup partition, and another partition, which is shared and where I put my work files.
The other disk has Ubuntu, including some shared space too.

A short while ago I resized partitions with gparted (booted from a Hardy Heron live CD), and then I upgraded to Intrepid Ibex. It all went well, until today, where I find that I can't see the NTFS disk.

I guess (from what I've seen) that I need to post etc/fstab file content in here, and that's what I'm doing, but first let me tell you that I guess that I found a few inconsistencies in it (I'm not sure, but it seems so to me), and probably related to the partitions' resizing I mentiones earlier.

**_Well, here goes first a [COLOR="Blue"]sudo fdisk -l[/COLOR]_ (I have it in spanish, but based on other posts I guessed I could translate it, like [COLOR="Red"]cilindros-->cylinders)[/COLOR]:**

```
leo@leo-desktop-ub:~$ sudo fdisk -l
[sudo] password for leo: 

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xde42de42

Device Boot    Start      End      Blocks  Id  System
/dev/sda1   *           1        6527    52428096    7  HPFS/NTFS
/dev/sda2            6528        9728    25712032+   f  W95 Ext'd (LBA)
/dev/sda5            6528        9728    25712001    7  HPFS/NTFS

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x139b139b

Device Boot    Start      End      Blocks  Id  System
/dev/sdb1               1        1919    15414336   83  Linux
/dev/sdb2            1920        9729    62733825    5  Extended
/dev/sdb5            1920        2116     1582371   82  Linux swap / Solaris
/dev/sdb6            2117        3776    13333918+  83  Linux
/dev/sdb7            3777        9729    47817441    b  W95 FAT32

```


**_Now, the etc/fstab file content_:**

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hdb1
UUID=96099255-b4ea-4655-ae93-f7787a6735cc /               ext3    defaults,errors=remount-ro 0       1
# /dev/hdb7
UUID=AD6B-6954  /comun          vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/hdb6
UUID=8b30d582-bf3c-40a4-9c20-f2de1e149f02 /home           ext3    defaults        0       2
# /dev/hda1
UUID=2A8048088047D8C9 /media/hda1     ntfs    defaults,umask=007,gid=46 0       1
# /dev/hda5
UUID=FA20698B20695025 /media/hda5     ntfs    defaults,umask=007,gid=46 0       1
# /dev/hdb5
UUID=91f55437-7b61-4840-b20a-bdcc4e862279 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0

```

I'd like to understand any of this all, and slowly but steadily I'm learning (after I was brainwashed by window$ for a long time, heheh), but this still is out of my reach.

Would you please help me?

Thanks in advance.

Leo (Buenos Aires, Argentina)

---

### Post by dolman25 on 2008-11-06
If you shut down windows improperly such as presing the restart button or blue screen of death. you will have problems mounting with linux. I dont know why this happens maybe someone else can answer. I have had this problem before, i just booted back into windows and then made sure i shut down windows properly, anyway thats the first thing i would try.

---

### Post by sisco311 on 2008-11-06
you can also try to mount the partition manualy from a 

terminal and post the error message:

```
sudo mount /dev/sda1 /media/hda1 -t ntfs -o defaults,umask=007,gid=46
```

---

### Post by Senuf on 2008-11-06
> **dolman25 said:**
> If you shut down windows improperly such as presing the restart button or blue screen of death. you will have problems mounting with linux. I dont know why this happens maybe someone else can answer. I have had this problem before, i just booted back into windows and then made sure i shut down windows properly, anyway thats the first thing i would try.

Dolman25, you were right!!!
I was afraid to reboot (especially starting up in Windows), but... it worked!!!

You were right in one thing...
I was doing some complex batch processing of certain files, which REQUIRED ME to work in Windows (details not important), and since it was going to be a looooong task, I left the PC working while I went to sleep. When I woke up today I found the PC rebooted and with the Ubuntu Login screen, so it seems that windows somehow crashed (typically Windows...), meaning it wasn't shut down properly, as you very well deduced.

Thanks a lot, and thanks to you too, sisco311 (I've already written down your suggestion, just in case I have a similar problem which can't be corrected the way I did right minutes ago).

Leo (happy!)

---

