---
title: "mount: wrong fs type, bad option, bad superblock on /dev/sdb1"
date: 2008-06-24
forum: Hardware
---

### Post by volmark on 2008-06-24
I have installed second SATA HD drive (the boot one is SCSI) but couldn’t mount it properly. I’ve formatted it with fsck.ext3 and partitioned with TestDisk (external CD).
Here are some listings of /etc/fstab and screen dumps of fdisk.

~$ sudo fdisk -l

Disk /dev/sda: 36.4 GB, 36419584000 bytes
255 heads, 63 sectors/track, 4427 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xc3cd54c8

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4240    34057768+  83  Linux
/dev/sda2            4241        4427     1502077+   5  Extended
/dev/sda5            4241        4427     1502046   82  Linux swap / Solaris

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xc3b64465

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        9729    78148161   83  Linux

--------------------------------------------------------------------

~$ sudo nano /etc/fstab
  GNU nano 2.0.7                                      

File: /etc/fstab

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=1010ffdb-c0fb-4f1d-9e65-589160c3bcd8 /               ext3 relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=dd32c617-6437-42ce-b3dc-17a9977fa74c none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

# 2. HD
/dev/sdb1       /media/hd2      ext3    defaults        0       0


--------------------------------------------------------------------

~$ sudo mount -a

--------------------------------------------------------------------


~$ sudo mount -a
mount: wrong fs type, bad option, bad superblock on /dev/sdb1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

---

### Post by asuastrophysics on 2010-05-12
I'm having the exact same issue. Glad to see that the community cares to leave a response. I've reformatted my entire hard disk and reinstalled ubuntu, and I still can't boot up. Now, I can't even chroot into it. 

What does this stupid error mean? I know it's an ext4 filesystem, so why shouldnt I be able to mount it like this:
```
sudo mount -t ext4 /dev/sda2 /mnt
```

:confused:

---

### Post by ZootHornRollo on 2010-05-15
i followed this :

[http://ubuntuforums.org/showpost.php?p=7822694&postcount=2](http://ubuntuforums.org/showpost.php?p=7822694&postcount=2)

worked for me!  ;)

---

### Post by alienprdkt on 2010-08-15
> **ZootHornRollo said:**
> i followed this :

[http://ubuntuforums.org/showpost.php?p=7822694&postcount=2](http://ubuntuforums.org/showpost.php?p=7822694&postcount=2)

worked for me!  ;)
 

worked for me as well

---

### Post by Harika_p on 2011-07-04
I was going to move to Fedora 15 since I have been facing "initramfs" with my Ubuntu 10.04 LTS. But some how I managed to fix it using some posts along with this one (The link introduced here!)
Maybe I should be thinking of sth more smooth and stable like Fedora!!!

---

