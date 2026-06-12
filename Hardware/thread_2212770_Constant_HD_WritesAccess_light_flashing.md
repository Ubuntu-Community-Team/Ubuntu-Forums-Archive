---
title: "Constant HD Writes/Access light flashing"
date: 2014-03-23
forum: Hardware
---

### Post by jeremy21 on 2014-03-23
Hi,
  Setting up a home server on a HP MicroServer N54.  Loaded up Ubuntu Server with a GUI ([COLOR=#000000][FONT=Tahoma]--no-install-recommends ubuntu-desktop) set up a RAID 5 array with 2TB drives for data, with a separate SSD for OS.  Everything seems to be working fine, but I'm showing constant writes to the array.  I can tell because I can feel the drive vibrate.  Its the third one (/dev/sdc).

Current fstab:
[/FONT][/COLOR]```

# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sde1 during installation
UUID=2c457dc7-c586-428e-af96-2f20f5f9f490 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sde5 during installation
UUID=917e0515-6b22-4c09-ae67-b99622268b50 none            swap    sw              0       0
/dev/md0    /srv        ext4    defaults    1    2
#Raid 5 array on main sata controller

```
[COLOR=#000000][FONT=Tahoma]
Status of Array:
[/FONT][/COLOR]```
/dev/md0:        Version : 1.2
  Creation Time : Sat Mar 22 00:25:58 2014
     Raid Level : raid5
     Array Size : 5860145664 (5588.67 GiB 6000.79 GB)
  Used Dev Size : 1953381888 (1862.89 GiB 2000.26 GB)
   Raid Devices : 4
  Total Devices : 4
    Persistence : Superblock is persistent


    Update Time : Sat Mar 22 23:50:59 2014
          State : clean 
 Active Devices : 4
Working Devices : 4
 Failed Devices : 0
  Spare Devices : 0


         Layout : left-symmetric
     Chunk Size : 512K


           Name : Server:0  (local to host Server)
           UUID : eefdf9d1:10e0bcb6:f7a5f726:4deb195d
         Events : 85


    Number   Major   Minor   RaidDevice State
       0       8        5        0      active sync   /dev/sda5
       1       8       21        1      active sync   /dev/sdb5
       2       8       37        2      active sync   /dev/sdc5
       3       8       53        3      active sync   /dev/sdd5

```

I've run iotop and get the following:
[IMG]http://i.imgur.com/WEirOGY.png[/IMG]
[IMG]http://i.imgur.com/RJzzJOs.png[/IMG]

I installed GkrellM Sys Mon to see traffic, and disk access look like a heartbeat - 
[IMG]http://i.imgur.com/fBeEsIr.png[/IMG]

if pics aren't coming up here's the album - [http://imgur.com/a/iCNzd/all](http://imgur.com/a/iCNzd/all)

I've run short tests with GSmart Control and no errors on any disk.

Any advice is appreciated.

JT

---

