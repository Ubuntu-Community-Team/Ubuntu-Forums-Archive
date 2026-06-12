---
title: "Issues with Harddrive and Gparted"
date: 2013-11-15
forum: Hardware
---

### Post by wewantutopia on 2013-11-15
Hi Everyone,

I dual boot Windows 7 and Ubuntu 12.04.

My wife was using the computer for work the other day, using Windows 7, and the computer crashed.  Upon rebooting into Windows 7 she was welcomed with the black screen of death.  Ubuntu still works fine of course.  I've been trying to get it up and running.  Booting either normally or in safe mode brings up a black screen with a low resolution cursor. I've booted with the repair disc and got into a command line.  I ran a chkdsk but after 24 hours it was finnished with not ever 1/10th of 1%.  No time for that.  Tried to restore the system but Windows repair disc doesn't even recognize there is a Windows install on the hard drive.

I've decided to nuke it and start over.

Upon booting into Ubuntu to use gpared to delete the partition and create a new one, gparted will not load the drives.  It opens and but it continues "searching" for drives with the hard drive light solid.  It never loads after 20 minutes.  

Looking for suggestions on what to do.

Thanks!

---

### Post by oldfred on 2013-11-15
When I had a corrupted XP, gparted would not show the drive until I ran chkdsk on the XP install. Since then I thought gparted showed partitions with issues but had the red or yellow icons warning that partition had issues. Are you using a current version of gparted?

I would not think Ubuntu would boot if there were partition table issues as that often causes issues.

Post this.
sudo fdisk -lu
sudo parted -l

---

### Post by wewantutopia on 2013-11-15
Thanks for responding!

Here is sudo fdisk -lu

```

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x312ad8c8

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      206847      102400    7  HPFS/NTFS/exFAT
/dev/sda2          206848  1710056457   854924805    7  HPFS/NTFS/exFAT
/dev/sda3      1905371136  1953523711    24076288   27  Hidden NTFS WinRE
/dev/sda4      1710057470  1905371135    97656833    5  Extended
Partition 4 does not start on physical sector boundary.
/dev/sda5      1710057472  1905371135    97656832   83  Linux

Partition table entries are not in disk order

Disk /dev/sdb: 8012 MB, 8012390400 bytes
246 heads, 40 sectors/track, 1590 cylinders, total 15649200 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x74f02dea

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1            2048    15646719     7822336   73  Unknown


```

Here is sudo parted -l

```

Model: ATA SAMSUNG HN-M101M (scsi)
Disk /dev/sda: 1000GB
Sector size (logical/physical): 512B/4096B
Partition Table: msdos

Number  Start   End     Size    Type      File system  Flags
 1      1049kB  106MB   105MB   primary   ntfs         boot
 2      106MB   876GB   875GB   primary   ntfs
 4      876GB   976GB   100GB   extended
 5      876GB   976GB   100GB   logical   ext4
 3      976GB   1000GB  24.7GB  primary   ntfs         diag


Model: ATA SanDisk iSSD P4 (scsi)
Disk /dev/sdb: 8012MB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      1049kB  8011MB  8010MB  primary


```

Thanks!

---

### Post by oldfred on 2013-11-15
Partition tables do look normal. 
I assume you ran chkdsk from recovery console as you have the separte 100MB boot & repair partition for Windows.
Normally issues like that have to have chkdsk to fix issues, and with a very large NTFS partition like you have it may take a very long time. 
Often I suggest for both Windows & Linux that system partitions be separate from data partitions. Just because we now have TB size drives does not mean we should have one very large system partition.

Since mostly a Windows issue I cannot suggest much more than what you have tried. Sometimes the third party Windows tools may work as they are more for Windows.

       [URL="http://www.sevenforums.com/"]http://www.sevenforums.com/
[/URL]
 [URL="http://neosmart.net/forums/"]http://neosmart.net/forums/
      [/URL]
 EASEUS Partition Master 
[http://www.partition-tool.com/personal.htm](http://www.partition-tool.com/personal.htm)
Partition Wizard
[http://www.partitionwizard.com/free-partition-manager.html](http://www.partitionwizard.com/free-partition-manager.html)
[http://www.partitionwizard.com/partitionmanager/partition-fix.html](http://www.partitionwizard.com/partitionmanager/partition-fix.html)

    [URL="http://neosmart.net/forums/"]
[/URL]

[URL="http://www.sevenforums.com/"]
[/URL]

---

