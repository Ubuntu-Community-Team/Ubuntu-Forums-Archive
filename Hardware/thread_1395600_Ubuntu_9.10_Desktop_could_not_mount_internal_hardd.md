---
title: "Ubuntu 9.10 Desktop could not mount internal harddisks attached to a RAID motherboard"
date: 2010-02-01
forum: Hardware
---

### Post by tkwinfo on 2010-02-01
Hi All,

     I have posted this question to the "ubuntu-user" mailing list. I re-post it here as I think the question is more hardware-related.

     Thanks for any comment.

Regards 
Lawrence

---------- Forwarded message ----------
From: **Lawrence Tsang** <tkwinfo@gmail.com>
Date: Mon, Feb 1, 2010 at 6:39 AM
Subject: Fwd: Ubuntu 9.10 Desktop CD booted system could not mount internal harddisks attached to a RAID motherboard
To: [email]ubuntu-users@lists.ubuntu.com[/email]


Hi All,

     I want to add some points.

     When my system is booted from the Ubuntu 8.04.4 Desktop CD, the OS recognizes ALL my internal and removable partitions. The outputs of some commands that I have run in a root terminal are listed as below :

---------------------------------------------------------------------
root@ubuntu:~# fdisk -l

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa3dea3de

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       15201   122102001    7  HPFS/NTFS
/dev/sda2           15202       30401   122094000    7  HPFS/NTFS


Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x43d850f0

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       30401   244196001    7  HPFS/NTFS


Disk /dev/sdg: 8029 MB, 8029470208 bytes
255 heads, 63 sectors/track, 976 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System

/dev/sdg1               1         976     7839698    b  W95 FAT32

Disk /dev/sdh: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x67df8048

   Device Boot      Start         End      Blocks   Id  System
/dev/sdh1               2       60801   488376000    f  W95 Ext'd (LBA)
/dev/sdh5               2       60801   488375968+   7  HPFS/NTFS

root@ubuntu:~# 


root@ubuntu:~# blkid
/dev/sda1: UUID="D2EC0953EC0932F1" LABEL="SYSTEM" TYPE="ntfs" 
/dev/sda2: UUID="30184A93184A584C" LABEL="DATA" TYPE="ntfs" 
/dev/sdb1: UUID="0ADC9EC9DC9EAF07" LABEL="DATA_2" TYPE="ntfs" 
/dev/loop0: TYPE="squashfs" 
/dev/sdg1: UUID="355E-514C" TYPE="vfat" 
/dev/sdh5: UUID="A868C79E68C769A0" LABEL="500G_DISK" TYPE="ntfs" 

 root@ubuntu:~# 


root@ubuntu:~# ls -l /dev/sd*
brw-rw---- 1 root disk 8,   0 2010-02-01 13:53 /dev/sda
brw-rw---- 1 root disk 8,   1 2010-02-01 06:21 /dev/sda1
brw-rw---- 1 root disk 8,   2 2010-02-01 06:22 /dev/sda2
brw-rw---- 1 root disk 8,  16 2010-02-01 13:53 /dev/sdb
brw-rw---- 1 root disk 8,  17 2010-02-01 13:53 /dev/sdb1
brw-rw---- 1 root disk 8,  32 2010-02-01 13:53 /dev/sdc
brw-rw---- 1 root disk 8,  48 2010-02-01 13:53 /dev/sdd
brw-rw---- 1 root disk 8,  64 2010-02-01 13:53 /dev/sde
brw-rw---- 1 root disk 8,  80 2010-02-01 13:53 /dev/sdf
brw-rw---- 1 root disk 8,  96 2010-02-01 13:53 /dev/sdg
brw-rw---- 1 root disk 8,  97 2010-02-01 13:53 /dev/sdg1
brw-rw---- 1 root disk 8, 112 2010-02-01 13:53 /dev/sdh
brw-rw---- 1 root disk 8, 113 2010-02-01 13:53 /dev/sdh1
brw-rw---- 1 root disk 8, 117 2010-02-01 13:53 /dev/sdh5
root@ubuntu:~# 

---------------------------------------------------------------------

     I don't know why the Ubuntu 8.04.4 Desktop "blkid" command treats my 2 internal harddisk (/dev/sda, /dev/sdb) normally while the Ubuntu 9.10 Desktop "blkid" command treats my 2 disks as "isw_raid_member" and could not see its partitions.

     Any idea ?

Regards
[COLOR=#888888]Lawrence[/COLOR]


---------- Forwarded message ----------
From: **Lawrence Tsang** <[EMAIL="tkwinfo@gmail.com"]tkwinfo@gmail.com[/EMAIL]>
Date: Mon, Feb 1, 2010 at 4:18 AM
Subject: Ubuntu 9.10 Desktop CD booted system could not mount internal harddisks attached to a RAID motherboard
To: [EMAIL="ubuntu-users@lists.ubuntu.com"]ubuntu-users@lists.ubuntu.com[/EMAIL]


Hi All,

     I have a computer system having 2 internal 250GB harddisks attached to a RAID motherboard. I have not used the RAID feature and have just set the two internal harddisks as independent IDE disks. This system works OK in a Windows XP environment. I could see and use these 2 internal disks in such a XP environment for at least 1 year.
 
     However, recently, when I boot my system using the Ubuntu 9.10 Desktop CD in a cdrom, the CD boots normally into a workable Ubuntu 9.10 Desktop. But I just could not use the above mentioned 2 internal harddisks.
 
     The following are some commands that I have run inside a root terminal and the corresponding outputs :

--------------------------------------------------------------------------------------------------
 [I]root@ubuntu:/home/ubuntu# fdisk -l

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa3dea3de
 
   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       15201   122102001    7  HPFS/NTFS
/dev/sda2           15202       30401   122094000    7  HPFS/NTFS

Disk /dev/sdb: 250.1 GB, 250059350016 bytes
 255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x43d850f0

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       30401   244196001    7  HPFS/NTFS
 
Disk /dev/sdc: 8029 MB, 8029470208 bytes
255 heads, 63 sectors/track, 976 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
 /dev/sdc1               1         976     7839698    b  W95 FAT32

Disk /dev/sdh: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x67df8048

   Device Boot      Start         End      Blocks   Id  System
/dev/sdh1               2       60801   488376000    f  W95 Ext'd (LBA)
/dev/sdh5               2       60801   488375968+   7  HPFS/NTFS
root@ubuntu:/home/ubuntu#[/I]
 --------------------------------------------------------------------------------------------------

[I]root@ubuntu:/home/ubuntu# blkid
/dev/loop0: TYPE="squashfs"
/dev/sda: TYPE="isw_raid_member"
 /dev/sdb: TYPE="isw_raid_member"
/dev/sdc1: UUID="355E-514C" TYPE="vfat"
/dev/sdh5: UUID="A868C79E68C769A0" LABEL="500G_DISK" TYPE="ntfs"
root@ubuntu:/home/ubuntu#[/I]
 --------------------------------------------------------------------------------------------------

     Ubuntu 9.10 could list the 2 internal harddisks as /dev/sda, /dev/sdb. But it could not list the partitions in these 2 disks as devices as follows : 
 
--------------------------------------------------------------------------------------------------

[I]root@ubuntu:/home/ubuntu# ls -l /dev/sd*
brw-rw---- 1 root disk 8,   0 2010-02-01 03:30 /dev/sda
brw-rw---- 1 root disk 8,  16 2010-02-01 03:30 /dev/sdb
 brw-rw---- 1 root disk 8,  32 2010-02-01 03:30 /dev/sdc
brw-rw---- 1 root disk 8,  48 2010-02-01 03:30 /dev/sdd
brw-rw---- 1 root disk 8,  64 2010-02-01 03:30 /dev/sde
brw-rw---- 1 root disk 8,  80 2010-02-01 03:30 /dev/sdf
 brw-rw---- 1 root disk 8,  96 2010-02-01 03:30 /dev/sdg
brw-rw---- 1 root disk 8,  97 2010-02-01 03:30 /dev/sdg1
brw-rw---- 1 root disk 8, 112 2010-02-01 03:30 /dev/sdh
brw-rw---- 1 root disk 8, 113 2010-02-01 03:30 /dev/sdh1
 brw-rw---- 1 root disk 8, 117 2010-02-01 03:30 /dev/sdh5
root@ubuntu:/home/ubuntu# [/I]
--------------------------------------------------------------------------------------------------

     The 2 internal disks, /dev/sda and /dev/sdb, are of type "isw_raid_member" as listed by the "blkid" command. I think this is because these disks are attached to the RAID motherboard and may have been treated by Ubuntu 9.10 as RAID devices.
 
     I could use the other USB disks, sdg1 and sdh5, in a normal way. (/dev/sdc is a 8G USB flash drive. I don't know why sdg1 is seen by "fdisk" and "blkid" as sdc1) 

     This picture happens for Ubuntu 9.10 Desktop. If I use Ubuntu 8.04.4 Desktop CD in a cdrom to boot my computer, I could use ALL my harddisk normally. 
 
     What should I do in order to use the 2 RAID attached disks in Ubuntu 9.10 Desktop ? Thanks for any suggestion.

Regards
[COLOR=#888888]Lawrence

[/COLOR]

---

