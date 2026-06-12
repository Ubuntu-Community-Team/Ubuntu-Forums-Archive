---
title: "Resizing ntfs raid partition?"
date: 2007-08-22
forum: Hardware &amp; Laptops
---

### Post by khughitt on 2007-08-22
Hi all,

I Recently decided to try setting up a xp / ubuntu dual boot with raid 0. I used an onboard promise raid controller to setup a single array between two 300gb drives. I installed windows first (formatting the entire 600gb partition to ntfs). I then tried using Gparted Live! to shrink the partition so that I could make room for ubuntu. Unfortunately Gparted did not recognize the raid partition at first.

After a little more research online I decided to try loading the Gusty liveCD, then installed **dmraid** and used that to allow Ubuntu to see the raid partition. Afterwards I ran **ntfsresize** without a problem. The problems begin when I try and use **fdisk** or Gparted to re-create the partition.

Here is whats happening:

```
ubuntu@ubuntu**:/mnt$ sudo ntfsresize -s 100000000000 /dev/mapper/pdc_deibjeiej1**
ntfsresize v1.13.1 (libntfs 9:0:0)
Device name        : /dev/mapper/pdc_deibjeiej1
NTFS volume version: 3.1
Cluster size       : 4096 bytes
Current volume size: 600165745152 bytes (600166 MB)
Current device size: 600165748224 bytes (600166 MB)
New volume size    : 99999994368 bytes (100000 MB)
Checking filesystem consistency ...
100.00 percent completed
Accounting clusters ...
Space in use       : 30049 MB (5.0%)
Collecting resizing constraints ...
Needed relocations : 1369630 (5611 MB)
WARNING: Every sanity check passed and only the dangerous operations left.
Make sure that important data has been backed up! Power outage or computer
crash may result major data loss!
Are you sure you want to proceed (y/[n])? **y**
Schedule chkdsk for NTFS consistency check at Windows boot time ...
Resetting $LogFile ... (this might take a while)
Relocating needed data ...
100.00 percent completed
Updating $BadClust file ...
Updating $Bitmap file ...
Updating Boot record ...
Syncing device ...
Successfully resized NTFS on device '/dev/mapper/pdc_deibjeiej1'.
You can go on to shrink the device for example with Linux fdisk.
IMPORTANT: When recreating the partition, make sure that you
  1)  create it at the same disk sector (use sector as the unit!)
  2)  create it with the same partition type (usually 7, HPFS/NTFS)
  3)  do not make it smaller than the new NTFS filesystem size
  4)  set the bootable flag for the partition if it existed before
Otherwise you won't be able to access NTFS or can't boot from the disk!
If you make a mistake and don't have a partition table backup then you
can recover the partition table by TestDisk or Parted's rescue mode.

ubuntu@ubuntu:/mnt$ **sudo ntfsresize -i /dev/mapper/pdc_deibjeiej1**
ntfsresize v1.13.1 (libntfs 9:0:0)
ERROR: Volume is scheduled for check.
Run chkdsk /f and please try again, or see option -f.

ubuntu@ubuntu:/mnt$** fdisk /dev/mapper/pdc_deibjeiej1**
Unable to open /dev/mapper/pdc_deibjeiej1

ubuntu@ubuntu:/mnt$ **sudo fdisk /dev/mapper/pdc_deibjeiej1**

The number of cylinders for this disk is set to 72965.
There is nothing wrong with that, but this is larger than 1024,
and could in certain setups cause problems with:
1) software that runs at boot time (e.g., old versions of LILO)
2) booting and partitioning software from other OSs
   (e.g., DOS FDISK, OS/2 FDISK)

Command (m for help): p

Disk /dev/mapper/pdc_deibjeiej1: 600.1 GB, 600165748224 bytes
255 heads, 63 sectors/track, 72965 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

This doesn't look like a partition table
Probably you selected the wrong device.

                      Device Boot      Start         End      Blocks   Id  System
/dev/mapper/pdc_deibjeiej1p1   ?       13578      119522   850995205   72  Unknown
Partition 1 does not end on cylinder boundary.
/dev/mapper/pdc_deibjeiej1p2   ?       45382       79243   271987362   74  Unknown
Partition 2 does not end on cylinder boundary.
/dev/mapper/pdc_deibjeiej1p3   ?       10499       10499           0   65  Novell Netware 386
Partition 3 does not end on cylinder boundary.
/dev/mapper/pdc_deibjeiej1p4          167628      167631       25817+   0  Empty
Partition 4 does not end on cylinder boundary.

Partition table entries are not in disk order

```

I also tried using Gparted to setup the partitions, but it is giving an error message as well:
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=41418&stc=1&d=1187838766[/IMG]

I thought about trying to boot into windows and run **chkdisk**, but I don't know if that would help and am pretty sure the space used would change as soon as I boot into windows (because of swap file), so I would have to run ntfs-resize all over again.

Anyone have any ideas?

Any help would be greatly appreciated. This is my first time experimenting with RAID...
Thanks!

---

### Post by khughitt on 2007-08-23
Still no luck...

I tried using both the Ubuntu alternative install CD and Debian 4.0r1 today but still not luck. One the Debian wiki there is a guide on [installing on SATA FakeRAID partitions]("http://wiki.debian.org/DebianInstaller/SataRaid?highlight=%28raid%29"), but it says that there is no way to resize ntfs partitions at the time.

Any ideas?

---

### Post by generalj on 2007-11-23
I am about to attempt the same setup, I'll let you know how it goes.

I have a 2 drives in raid 0 with XP installed already. Going to attempt to dual boot it with ubuntu without uninstalling XP. I want ubuntu on the raid 0 as well.

---

### Post by psusi on 2007-11-26
You use fdisk on the DISK device, not the partition.  In other words, you need to drop the '1' at the end.

---

