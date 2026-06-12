---
title: "[SOLVED] Which file system?"
date: 2008-08-05
forum: General Help
---

### Post by nobody13 on 2008-08-05
I have 2 sata drives set up as raid 1 and would like to acess them from windows or linux. Wich file system is best for this?

---

### Post by tamoneya on 2008-08-05
First of all you should have at least 3 partitions.  One for each OS to be installed in and the on for storage.  For the storage partition format it depends which OS you use more often.  I tend to stay away from FAT32 because of the 4GB file limit.  It tends to get in my way.  If you primarily use linux I would recommend ext3 and then use fs-driver.  If you primarily use windows I would recommend that you use NTFS and then use the linux NTFS drivers that are preinstalled in linux.

[http://www.fs-driver.org/](http://www.fs-driver.org/)

---

### Post by Ender305 on 2008-08-05
just use ext3 and install ext2ifs in windows, it fully integrates the filesystems into windows

---

### Post by nobody13 on 2008-08-06
Ext3 it is. Thanks for the replies.

---

### Post by dcstar on 2008-08-06
> **nobody13 said:**
> I have 2 sata drives set up as raid 1 and would like to acess them from windows or linux. Wich file system is best for this?

Software or "real" Hardware RAID?, I have systems that have SATA "RAID" on the motherboard, but it is the "FakeRAID" variety that requires special Windows drivers and is still seen as two separate drives by Ubuntu.

I believe in that case you have to set up a Linux RAID system, and I'm not 100% sure that will work correctly with both OSs (not matter what filesystem is used).

---

### Post by tamoneya on 2008-08-06
> **dcstar said:**
> Software or "real" Hardware RAID?, I have systems that have SATA "RAID" on the motherboard, but it is the "FakeRAID" variety that requires special Windows drivers and is still seen as two separate drives by Ubuntu.

I believe in that case you have to set up a Linux RAID system, and I'm not 100% sure that will work correctly with both OSs (not matter what filesystem is used).

I believe that for most of the fakeRAID chipsets RAIDS 0 and 1 are both supported.  It is the more complicated stuff like 5 that doesnt work.

---

### Post by nobody13 on 2008-08-07
I'm not sure if it's software or hardware raid. Until now I never heard of fake raid but it is an onboard controller and does show up as 2 drives under Linux. I did install ext2ifs and it works under Windows XP but doesn't automount under Linux like my 2 ATA drives did before I replaced my motherboard. I was thinking that I just needed to figure out what line needed to be added to fstab but now you've got me a little worried. They're currently connected to my Silicon Image controller and I also have a VIA controller onboard if it makes a difference. What do I need to do to get it to work?

Hopefully relevant data below:

Motherboard is a Soyo kt600 Dragon Ultra Platnum
sda and sdb are the 2 drives

lspci:
```

00:0f.0 RAID bus controller: VIA Technologies, Inc. VIA VT6420 SATA RAID Controller (rev 80)
00:13.0 RAID bus controller: Silicon Image, Inc. SiI 3112 [SATALink/SATARaid] Serial ATA Controller (rev 02)

``` 

 fdisk -l:
```

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xf768e6b6

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       60801   488384001   83  Linux

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xf768e6b6

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       60801   488384001   83  Linux

Disk /dev/sdc: 60.0 GB, 60022480896 bytes
255 heads, 63 sectors/track, 7297 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00015235

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1          17      136521   83  Linux
/dev/sdc2              18         383     2939895   82  Linux swap / Solaris
/dev/sdc3             384        7297    55536705   83  Linux

Disk /dev/sdd: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xaf63af63

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1   *           1        3824    30716248+   7  HPFS/NTFS
/dev/sdd2            3825        9728    47423880    f  W95 Ext'd (LBA)
/dev/sdd5            3825        9728    47423848+   7  HPFS/NTFS

Disk /dev/md0: 500.1 GB, 500107771904 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xf768e6b6

    Device Boot      Start         End      Blocks   Id  System
/dev/md0p1               1       60801   488384001   83  Linux

```

fstab:
```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda3
UUID=0d06c78e-49e3-4eee-8300-d72c5d285ad3 /               reiserfs defaults        0       1
# /dev/hda1
UUID=67b3286b-a738-4b49-b19a-fc81686591e4 /boot           ext2    defaults        0       2
# /dev/hdb1
UUID=94249FD2249FB628 /media/hdb1     ntfs    defaults,umask=007,gid=46 0       1
# /dev/hdb5
UUID=FA74775B74771A19 /media/hdb5     ntfs    defaults,umask=007,gid=46 0       1
# /dev/hda2
UUID=a9c5eb81-5637-4fc4-a9b7-ecc44ed6e00f none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0

```

---

### Post by tamoneya on 2008-08-07
that definitely sounds like fake raid.  Read this article: [https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)

---

### Post by nobody13 on 2008-08-07
That got it working. Thanks

---

