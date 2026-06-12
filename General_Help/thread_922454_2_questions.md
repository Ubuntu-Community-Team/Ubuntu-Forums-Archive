---
title: "2 questions"
date: 2008-09-17
forum: General Help
---

### Post by hjaeger on 2008-09-17
1. My "folder links" always get broken. (links located in filesystem home --> location another driver)


2. Error with the sudo kommamd.  Example: sudo cd/bin   command not found

---

### Post by bingoUV on 2008-09-17
> **hjaeger said:**
> 
2. Error with the sudo kommamd.  Example: sudo cd/bin   command not found

There needs to be a space between cd and /bin.
```

sudo cd /bin

```

BTW you do not need sudo to cd into /bin.

---

### Post by jken146 on 2008-09-17
> **hjaeger said:**
> 1. My "folder links" always get broken. (links located in filesystem home --> location another driver)
Please post the outputs of ```
sudo fdisk -l
``` and ```
cat /etc/fstab
```


> 2. Error with the sudo kommamd.  Example: sudo cd/bin   command not found
That should be ```
cd /bin
```  You're missing a space.

---

### Post by hjaeger on 2008-09-17
[sudo] password for hjaeger:

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd25cd25c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       14027   112671846   83  Linux
/dev/sda2           14028       14593     4546395    5  Extended
/dev/sda5           14028       14593     4546363+  82  Linux swap / Solaris

Disk /dev/sdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x05620561

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       14593   117218241    7  HPFS/NTFS

Disk /dev/sdc: 400.0 GB, 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x34e2d247

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       48641   390708801    7  HPFS/NTFS
hjaeger@p28:~$




  Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       48641   390708801    7  HPFS/NTFS
hjaeger@p28:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=edcf6826-f0a4-4fda-bd9b-6948e831a53c /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=476a2c23-b971-4aac-b60a-d4c57bf011a2 none            swap    sw              0       0
/dev/sdd1       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
hjaeger@p28:~$

---

### Post by jken146 on 2008-09-17
OK, the problem probably is that sdb1 and sdc1 do not have entries in /etc/fstab, so Ubuntu is auto-mounting them each time, which could result in links not pointing to the same place they originally did.  All you have to do is add a couple of lines to the bottom of /etc/fstab.  

First, make some mount points.  You can choose the names yourself if you like, but I'll suggest data and data1.  ```
sudo mkdir /media/data
sudo mkdir /media/data1
```
Now for fstab:```
gksudo gedit /etc/fstab
``` Then add ```
/dev/sdb1 /media/data ntfs defaults 0 0
/dev/sdc1 /media/data1 ntfs defaults 0 0
```
Save fstab and quit gedit.  Then type ```
sudo umount /dev/sdb1 && sudo umount /dev/sdc1 && sudo mount -a
```

---

### Post by hjaeger on 2008-09-17
Last msg i got;;

Not sure if it worked yet. In the middle of a poker turny, but thanks =)


hjaeger@p28:~$ sudo umount /dev/sdb1 && sudo umount /dev/sdc1 && sudo mount -a
umount: /dev/sdb1: not mounted
hjaeger@p28:~$

---

### Post by jken146 on 2008-09-17
Alright, that doesn't matter.  Just do ```
sudo umount /dev/sdc1
sudo mount -a
```separately.  Ignore messages about things not already being mounted.

---

