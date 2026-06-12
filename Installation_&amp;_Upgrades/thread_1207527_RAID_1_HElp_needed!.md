---
title: "RAID 1 HElp needed!"
date: 2009-07-08
forum: Installation &amp; Upgrades
---

### Post by malarie on 2009-07-08
Good day,

I am new with raid configurations, and not so experienced with ubuntu administration..

I have installed Hardy from the Alternate CD because i needed to configure a raid 1 array.
sda and sdb are  SATA disks, but not the same size... sdb is 100GB bigger, but i still partitionned both disks taking into consideration that i would loose 100GB of space on sdb.


I went through the installation, but i'm sure i did someting wrong.. Or the partitions are not setup correctly.. (message displayed at the end of this post)

After the installation, everything seemed to be working just fine.. 
 /proc/mdstat  resynced  and all..   Once the sync was over, i decided to test my raid 1. I  disconnected sda's power while the pc was running..  I then lost write rights on a couple folders including /home/malarie

i have waited and after 5mins, i got a message saying that sda would be turned offline...

Now, everything works with sdb but i cannot see my sda anymore, and i dont know how to re-add it to the raid array..


[B]Here is some information on my setup:
[/B]
malarie@ubuntu:~$ cat /proc/mdstat
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10]
md1 : active raid1 sda2[0] sdb2[1]
      9767424 blocks [2/2] [UU]

md0 : active raid1 sdb1[1]
      146480512 blocks [2/1] [_U]

unused devices: <none>
**----------------------------------------------------**

malarie@ubuntu:~$ sudo mdadm --detail /dev/md0
/dev/md0:
        Version : 00.90.03
  Creation Time : Tue Jul  7 16:16:10 2009
     Raid Level : raid1
     Array Size : 146480512 (139.69 GiB 150.00 GB)
  Used Dev Size : 146480512 (139.69 GiB 150.00 GB)
   Raid Devices : 2
  Total Devices : 1
Preferred Minor : 0
    Persistence : Superblock is persistent

    Update Time : Wed Jul  8 09:33:49 2009
          State : active, degraded
 Active Devices : 1
Working Devices : 1
 Failed Devices : 0
  Spare Devices : 0

           UUID : f891b05d:5511c5e1:ab9f88d8:6e670a04
         Events : 0.223

    Number   Major   Minor   RaidDevice State
       0       0        0        0      removed
       1       8       17        1      active sync   /dev/sdb1

**------------------------------------------------------------**

malarie@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd42ad42a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       18236   146480638+  fd  Linux raid autodetect
/dev/sda2           18237       19457     9807682+  fd  Linux raid autodetect

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000dfe18

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       18236   146480638+  fd  Linux raid autodetect
/dev/sdb2           18237       19452     9767520   fd  Linux raid autodetect

Disk /dev/md0: 149.9 GB, 149996044288 bytes
2 heads, 4 sectors/track, 36620128 cylinders
Units = cylinders of 8 * 512 = 4096 bytes
Disk identifier: 0x00000000

Disk /dev/md0 doesn't contain a valid partition table

Disk /dev/md1: 10.0 GB, 10001842176 bytes
2 heads, 4 sectors/track, 2441856 cylinders
Units = cylinders of 8 * 512 = 4096 bytes
Disk identifier: 0x00000000

Disk /dev/md1 doesn't contain a valid partition table
**------------------------------------------------------------**

My FStab is:
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/md0
UUID=2cdc9d64-1aac-436f-bcbd-e40304199292 /               ext3    relatime,errors=remount-ro 0       1
# /dev/md1
UUID=958dd302-213c-4a92-af2b-af5cc23275be none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
**------------------------------------------------------------**

 How can i reattach sda1? and..is it possible to recreate the paritions on the disks without reinstalling the OS?

thanks.

---

### Post by running_rabbit07 on 2009-07-08
If you unplugged a power cable inside your PC with it running you are lucky anything works. ESD could have killed everything. 

You may have to reinstall but chances are that hard drive you unplugged may not work again.

---

### Post by malarie on 2009-07-08
I just followed this test procedure: [http://ltp.sourceforge.net/raid1.html](http://ltp.sourceforge.net/raid1.html)

---

### Post by running_rabbit07 on 2009-07-08
Though they may be hot swappable, messing with internals with the power on still scares me.

---

