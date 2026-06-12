---
title: "Broken Raid5 using MDADM after intrepid update"
date: 2008-11-08
forum: General Help
---

### Post by Ghetek on 2008-11-08
Hey guys i am having trouble putting my raid5 back together. Here is the info of my system.

md0 is my /
md1 is my swap
md2 SHOULD be 3 750gb hds plus one more that i need to format, add as spare and grow.

```

**root@LNXII:/# fdisk -l**

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xf650265a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9240    74220268+  fd  Linux raid autodetect
/dev/sda2            9241        9729     3927892+  fd  Linux raid autodetect

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe7dc730a

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        9240    74220268+  fd  Linux raid autodetect
/dev/sdb2            9241        9729     3927892+  fd  Linux raid autodetect

Disk /dev/sdc: 750.1 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xfe875a22

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       91201   732572001   fd  Linux raid autodetect

Disk /dev/sdd: 750.1 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xfdce3eff

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1       91201   732572001    7  HPFS/NTFS

Disk /dev/sde: 750.1 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000b0c2e

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1               1       91201   732572001   fd  Linux raid autodetect

Disk /dev/sdf: 750.1 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x2052474d

   Device Boot      Start         End      Blocks   Id  System
/dev/sdf1               1       91201   732572001   fd  Linux raid autodetect
**root@LNXII:/# cat /proc/mdstat**
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10]
md1 : active raid1 sda2[0] sdb2[1]
      3927808 blocks [2/2] [UU]

md0 : active raid1 sda1[0] sdb1[1]
      74220160 blocks [2/2] [UU]

unused devices: <none>
**root@LNXII:/# mdadm --examine /dev/sdc1**
mdadm: No md superblock detected on /dev/sdc1.
**root@LNXII:/# mdadm --examine /dev/sde1**
/dev/sde1:
          Magic : a92b4efc
        Version : 00.90.00
           UUID : d81d2e17:90f3ae8f:0c4c7919:6415c35c (local to host LNXII)
  Creation Time : Mon Oct 27 00:48:07 2008
     Raid Level : raid5
  Used Dev Size : 732571904 (698.64 GiB 750.15 GB)
     Array Size : 1465143808 (1397.27 GiB 1500.31 GB)
   Raid Devices : 3
  Total Devices : 3
Preferred Minor : 2

    Update Time : Wed Nov  5 10:13:41 2008
          State : clean
 Active Devices : 2
Working Devices : 2
 Failed Devices : 1
  Spare Devices : 0
       Checksum : 40634a07 - correct
         Events : 78218

         Layout : left-symmetric
     Chunk Size : 64K

      Number   Major   Minor   RaidDevice State
this     1       8       49        1      active sync   /dev/sdd1

   0     0       8       33        0      active sync
   1     1       8       49        1      active sync   /dev/sdd1
   2     2       0        0        2      faulty removed
**root@LNXII:/# mdadm --examine /dev/sdf1**
/dev/sdf1:
          Magic : a92b4efc
        Version : 00.90.00
           UUID : d81d2e17:90f3ae8f:0c4c7919:6415c35c (local to host LNXII)
  Creation Time : Mon Oct 27 00:48:07 2008
     Raid Level : raid5
  Used Dev Size : 732571904 (698.64 GiB 750.15 GB)
     Array Size : 1465143808 (1397.27 GiB 1500.31 GB)
   Raid Devices : 3
  Total Devices : 3
Preferred Minor : 2

    Update Time : Wed Nov  5 10:13:41 2008
          State : clean
 Active Devices : 2
Working Devices : 2
 Failed Devices : 1
  Spare Devices : 0
       Checksum : 406349f5 - correct
         Events : 78218

         Layout : left-symmetric
     Chunk Size : 64K

      Number   Major   Minor   RaidDevice State
this     0       8       33        0      active sync

   0     0       8       33        0      active sync
   1     1       8       49        1      active sync   /dev/sdd1
   2     2       0        0        2      faulty removed
**root@LNXII:/# mdadm --examine /dev/md2**
mdadm: No md superblock detected on /dev/md2.
root@LNXII:/#




```

any ideas?

---

### Post by fjgaude on 2008-11-08
Here's what I would try: delete the **/etc/mdadm/mdadm.conf** file, remove **mdadam**, re-boot. The re-install mdadm and then run this:

```
sudo mdadm --assemble --scan
```

This should auto create a new mdadm.conf file and you should be ready to mount the arrays, assuming you don't have lines in your **/etc/fstab** that have already done this.

If the arrays assemble, your might wish to use the mdamd -D command on each of them to see that all are okay.

Let us know how you are doing.

---

### Post by Ghetek on 2008-11-08
Thanks for the response! Ok so i should delete the mdadm.conf, "apt-get remove mdadm". How do i get back into ubuntu if my root "/" is mounted on md0 and my swap is mounted to md1? just wanna make sure that i can boot back up.

if it helps...
The 750gb hard drives are outside the system and they are on esata. they connect to a software raid card that doesnt have any settings in place.

swap(md1) and /(md0) are at two independent raid1 partition setups on 2 80gb eide hard drives.

---

### Post by fjgaude on 2008-11-08
Gosh, I don't know what to suggest... try reading, studying some of these and see if you can find an answer:

[http://shsc.info/LinuxSoftwareRAID](http://shsc.info/LinuxSoftwareRAID)
/usr/share/doc/mdadm/FAQ.gz  and md.txt.gz
[http://blog.tcg.com/tcg/2006/04/recovering_raid.html](http://blog.tcg.com/tcg/2006/04/recovering_raid.html)
[http://tldp.org/HOWTO/Software-RAID-HOWTO.html](http://tldp.org/HOWTO/Software-RAID-HOWTO.html)

I would never do what you have implemented for reliability reasons, always have triple backups. I have one online, one near-line, and one offline, for all important stuff.

Let us know what you come up with.

---

### Post by Ghetek on 2008-11-08
Thanks anyway.

---

### Post by Ghetek on 2008-11-13
sry for the BUMP

---

