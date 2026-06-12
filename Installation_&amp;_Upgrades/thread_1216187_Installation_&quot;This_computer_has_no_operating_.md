---
title: "Installation: &quot;This computer has no operating systems on it.&quot;"
date: 2009-07-18
forum: Installation &amp; Upgrades
---

### Post by jamesclish on 2009-07-18
Hi there

A few months ago, I posted this problem ([http://ubuntuforums.org/showthread.php?p=7138024](http://ubuntuforums.org/showthread.php?p=7138024)) regarding the Jaunty LiveCD's refusal to see my partitions.

I tried a few suggestions, but none worked...

I'm not exactly a linux buff so...you know...

Here's the output of sudo fdisk -l (I understand that's what you linux folk look at).

```
Usage: fdisk [-l] [-b SSZ] [-u] device
E.g.: fdisk /dev/hda  (for the first IDE disk)
  or: fdisk /dev/sdc  (for the third SCSI disk)
  or: fdisk /dev/eda  (for the first PS/2 ESDI drive)
  or: fdisk /dev/rd/c0d0  or: fdisk /dev/ida/c0d0  (for RAID devices)
  ...
jamesclish@james-laptop:~$ sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x08000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *       19131       19458     2620416    c  W95 FAT32 (LBA)
/dev/sda2              11        1316    10485760    7  HPFS/NTFS
/dev/sda3   *        1316       17856   132860920    7  HPFS/NTFS
/dev/sda4           17857       19458    12860673+   f  W95 Ext'd (LBA)
/dev/sda5           19131       19458     2620416   dd  Unknown
/dev/sda6           17857       19070     9751423+  83  Linux
/dev/sda7           19071       19130      481918+  82  Linux swap / Solaris

Partition table entries are not in disk order

```

Essentially, my problem is that the Jaunty LiveCD's partition manager won't recognise any partitions, and says "This computer has no operating systems on it." All it sees is one big, unpartitioned volume.

So, if anyone can make sense of my naive terminology, any suggestions would be great!

-James

---

### Post by merlinus on 2009-07-18
To be honest, I am not surprised.  If you look at your partition table, not only are they not in numerical order, but there are other strange things as well.

For example:

/dev/sda1   *       19131       19458     2620416    c  W95 FAT32 (LBA)
/dev/sda5           19131       19458     2620416   dd  Unknown

These two partitions are occupying the same space.  One is listed as fat32, the other as unknown.

Also, blocks 1-10 seem to be missing.  Perhaps there is some sort of hidden partition?

At best this would confuse gparted.\

Did you try the live gparted disk?

---

### Post by jamesclish on 2009-07-18
The only thing that might perhaps be interfering with the partitions is the small partition set aside by Dell for its "Media Direct" feature. (You hit a button on the laptop and it boots into a separate Dell Media Direct 'operating system' where you can view your media.)

Is gparted the partitioning tool on the Jaunty LiveCD? If so, that's the one I used.

I think I may have to just reformat completely, unless someone could suggest another idea.

-James

---

### Post by merlinus on 2009-07-18
gparted live cd is a later version than the one on the ubuntu disk.  It may show something different.

[http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)

---

### Post by jamesclish on 2009-07-18
Just for the record, I can access the partitions from Vista's built in partitioning tool. It says all the partitions are there and intact.

---

### Post by presence1960 on 2009-07-18
I agree with merlin that your partition table looks troubling. If you want to try without formatting give the alternate text based installer a try. Get it here: [alternate]("http://www.ubuntu.com/getubuntu/downloadmirrors#alternate")

---

### Post by merlinus on 2009-07-18
Another possibility is to use testdisk to fix the partition table.

[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

---

### Post by g_tenny on 2009-07-18
I have the same problem here too...
And TestDisk shows a "Space conflict" between two partitions and the LBA Extended partition overlaps 3 other partitions(i never formatted any partition as Ext'd LBA!)
This is the result of a "sudo fdisk -l" on my PC...
```
omitting empty partition (5)

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x3ee33ee2

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2475    19880406    7  HPFS/NTFS
/dev/sda5            2477        4797    18643401    b  W95 FAT32
/dev/sda6            4798        4866      554211    b  W95 FAT32
/dev/sda3            4867        7299    19543041    7  HPFS/NTFS
/dev/sda7            7300        9729    19518943+   b  W95 FAT32

/dev/sda2            2476        9729    58267755    f  W95 Ext'd(LBA)
```

And I get the same "This computer has no operating systems on it" with just one big, unpartitioned volume... the same problem James faces...:(
 -GTNy

---

### Post by RJARRRPCGP on 2009-07-18
> **jamesclish said:**
> Hi there

A few months ago, I posted this problem ([http://ubuntuforums.org/showthread.php?p=7138024](http://ubuntuforums.org/showthread.php?p=7138024)) regarding the Jaunty LiveCD's refusal to see my partitions.

I tried a few suggestions, but none worked...

I'm not exactly a linux buff so...you know...

Here's the output of sudo fdisk -l (I understand that's what you linux folk look at).

```
Usage: fdisk [-l] [-b SSZ] [-u] device
E.g.: fdisk /dev/hda  (for the first IDE disk)
  or: fdisk /dev/sdc  (for the third SCSI disk)
  or: fdisk /dev/eda  (for the first PS/2 ESDI drive)
  or: fdisk /dev/rd/c0d0  or: fdisk /dev/ida/c0d0  (for RAID devices)
  ...
jamesclish@james-laptop:~$ sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x08000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *       19131       19458     2620416    c  W95 FAT32 (LBA)
/dev/sda2              11        1316    10485760    7  HPFS/NTFS
/dev/sda3   *        1316       17856   132860920    7  HPFS/NTFS
/dev/sda4           17857       19458    12860673+   f  W95 Ext'd (LBA)
/dev/sda5           19131       19458     2620416   dd  Unknown
/dev/sda6           17857       19070     9751423+  83  Linux
/dev/sda7           19071       19130      481918+  82  Linux swap / Solaris

Partition table entries are not in disk order

```

Essentially, my problem is that the Jaunty LiveCD's partition manager won't recognise any partitions, and says "This computer has no operating systems on it." All it sees is one big, unpartitioned volume.

So, if anyone can make sense of my naive terminology, any suggestions would be great!

-James

The partitions probably are corrupted. Sorry. :(

---

### Post by shicy on 2009-07-18
i've heard that someone had similar problem as you and saved his partitions with Testdisk. I didn't try that program so i don't know how he did it, but you can try ;)

---

### Post by g_tenny on 2009-08-04
> **jamesclish said:**
> Hi there

A few months ago, I posted this problem ([http://ubuntuforums.org/showthread.php?p=7138024](http://ubuntuforums.org/showthread.php?p=7138024)) regarding the Jaunty LiveCD's refusal to see my partitions.

I tried a few suggestions, but none worked...

I'm not exactly a linux buff so...you know...

Here's the output of sudo fdisk -l (I understand that's what you linux folk look at).

```
Usage: fdisk [-l] [-b SSZ] [-u] device
E.g.: fdisk /dev/hda  (for the first IDE disk)
  or: fdisk /dev/sdc  (for the third SCSI disk)
  or: fdisk /dev/eda  (for the first PS/2 ESDI drive)
  or: fdisk /dev/rd/c0d0  or: fdisk /dev/ida/c0d0  (for RAID devices)
  ...
jamesclish@james-laptop:~$ sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x08000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *       19131       19458     2620416    c  W95 FAT32 (LBA)
/dev/sda2              11        1316    10485760    7  HPFS/NTFS
/dev/sda3   *        1316       17856   132860920    7  HPFS/NTFS
/dev/sda4           17857       19458    12860673+   f  W95 Ext'd (LBA)
/dev/sda5           19131       19458     2620416   dd  Unknown
/dev/sda6           17857       19070     9751423+  83  Linux
/dev/sda7           19071       19130      481918+  82  Linux swap / Solaris

Partition table entries are not in disk order

```

Essentially, my problem is that the Jaunty LiveCD's partition manager won't recognise any partitions, and says "This computer has no operating systems on it." All it sees is one big, unpartitioned volume.

So, if anyone can make sense of my naive terminology, any suggestions would be great!

-James

Hey James,
I had the same problem with my PC with 'mysterious' Ext'd LBA partitions and i was able to fix it.I just downloaded TestDisk([http://www.cgsecurity.org/wiki/TestDisk_Download](http://www.cgsecurity.org/wiki/TestDisk_Download)) and told it to "Delete" my partition table and then "Analyse" my disk to get the correct partition table and then saved it.
But "DO NOT REBOOT" during the process even if it asks you to do so. 
And, make yourself familiar with TestDisk before you try this out.
Hope this helps...

---

