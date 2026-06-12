---
title: "Cannot mount my windows partition anymore?"
date: 2008-08-22
forum: General Help
---

### Post by JuBeZ on 2008-08-22
Hi, 

I've looked around and seen some suggestions, but none work for me. Recently Vista crashed (big surprised huh) and I got the blue screen of death. Ever since then I havn't been able to mount my Vista partition (OS). Earlier, I had preset it to automount at Ubuntu startup which was a breeze. Now whenever I click "OS" under Places, I get "You are not privileged to mount the volume OS". From what I've seen, maybe the partition has been corrupted? I'm not sure though, because I still use Vista without any problems. I'm too nervous to proceed because I'm worried to ruin my partitions or lose data, so I'm waiting for your suggestions before I mess anything up. 

Thanks

---

### Post by iaculallad on 2008-08-22
Try posting whatever displays when you issue the (3) terminal commands below:

```
sudo blkid
sudo fdisk -l
cat /etc/fstab
```

---

### Post by JuBeZ on 2008-08-22
**sudo blkid**
/dev/sda1: SEC_TYPE="msdos" LABEL="DellUtility" UUID="07D8-0302" TYPE="vfat" 
/dev/sda2: UUID="DE9023829023606F" LABEL="RECOVERY" TYPE="ntfs" 
/dev/sda3: UUID="884C26AA4C26934C" LABEL="OS" TYPE="ntfs" 
/dev/sda5: LABEL="MEDIADIRECT" UUID="9C2A-5046" TYPE="vfat" 
/dev/sda6: UUID="732f8764-84ea-4b1d-a227-b2ae468e271d" TYPE="ext3" 
/dev/sda7: TYPE="swap" UUID="43aab2a8-6e8c-4c8b-b444-2123ea7e586e" 

**sudo fdisk -l**
Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd0000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1          13      104391   de  Dell Utility
/dev/sda2              14        1319    10485760    7  HPFS/NTFS
/dev/sda3   *        1319       22364   169045898+   7  HPFS/NTFS
/dev/sda4           22365       24322    15720883+   f  W95 Ext'd (LBA)
/dev/sda5           23995       24322     2620416   dd  Unknown
/dev/sda6           22365       23920    12498538+  83  Linux
/dev/sda7           23921       23994      594373+  82  Linux swap / Solaris

Partition table entries are not in disk order

**cat /etc/fstab**
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda6
UUID=732f8764-84ea-4b1d-a227-b2ae468e271d /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda7
UUID=43aab2a8-6e8c-4c8b-b444-2123ea7e586e none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/sda3	/media/OS	ntfs-3g defaults,locale=en_US.utf8 0 0 



Wow, I like the speedy response iaculallad. :)

EDIT: Oh, one more thing. I'm able to mount my RECOVERY partition fine from Places>RECOVERY, so I'm pretty sure its just the OS partition being whacky, rather than me not being root or something like that. The partition I'm trying to mount is sda3

---

### Post by WRDN on 2008-08-22
The first thing I would do is try a clean shutdown of Vista- just boot into it, and shutdown normally. This allows it to unmount the disk properly, as it appears it did not do so before.

You may want to try and mount the disk forcefully after that. To do this, in the Terminal type:

```
sudo mkdir /media/vista
```

You can replace "vista" with another name if you wish.

Now, type:

```
sudo mount /dev/sda3 /media/vista -o force
```

---

### Post by JuBeZ on 2008-08-22
Haha HEY! That force mount thing worked. Thank you very much. :)

---

### Post by Terry19 on 2008-08-22
Its Vista, forget about it. :lolflag:

---

