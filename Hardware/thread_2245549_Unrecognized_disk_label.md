---
title: "Unrecognized disk label"
date: 2014-09-24
forum: Hardware
---

### Post by The musmula on 2014-09-24
I have a SanDisk 16GB USB flash drive and it has stopped working. The first problems looked like this:
[LIST=1]
[*]Plug it in 
[*]put data on it 
[*]unplug it 
[*]plug it in 
[*]realize that all of your data is gone 
[/LIST]
Then i fired up GParted wich was like: "Unallocated space", "Unrecognized disk label", "Please create a partition table", so I did. I created an msdos partition table and after that I tryed to add a fat32 partition, think it worked? nope. "Unallocated space", "Unrecognized disk label", "Please create a partition table"...

So I did this:
```

sudo dd if=/dev/zero of=/dev/sdc bs=8M count= <I have forgoten how much but it was enough for 5gb or so>

```
The result? GParted is happy :) I create a partition table, add a partition add some data, plug it out and back in and everything works fine, yaaay, right? nope

now... a month later I get the same problem, but dd wont work, even when I fill all 16gb of space with zeros, nothing... Help?

---

### Post by tgalati4 on 2014-09-24
First, did you pull the USB drive out too quickly?  It's possible that the computer was not finished writing data to it, even though the Nautilus dialog box went away--indicating (falsely) that the copy operation was finished.

It's also possible that your drive is worn out.  Try formatting in a camera (if SD card or similar) or take another identical flash drive and note the CHS values--cylinders, heads, sectors.  See if they match with the one you formatted in gparted.  I've had problems with gparted screwing up flash drives because it chooses CHS values that are fine for real hard disks but do not work with flash drives.

You can use *fdisk* to discover the CHS count: (from [http://ubuntuforums.org/showthread.php?t=934259&highlight=CHS](http://ubuntuforums.org/showthread.php?t=934259&highlight=CHS))

> galati4@Mint14-Extensa ~ $ sudo fdisk -l
[sudo] password for tgalati4: 

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x66d07300

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2048    20482047    10240000   27  Hidden NTFS WinRE
/dev/sda2   *    20482048   166539263    73028608    7  HPFS/NTFS/exFAT
/dev/sda3       166539264   304390143    68925440   83  Linux
/dev/sda4       304390144   312580095     4094976   82  Linux swap / Solaris

Disk /dev/mmcblk0: 15.9 GB, 15931539456 bytes
255 heads, 63 sectors/track, 1936 cylinders, total 31116288 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

        Device Boot      Start         End      Blocks   Id  System
/dev/mmcblk0p1            8192    31116287    15554048    c  W95 FAT32 (LBA)



So I have a 16 GB SD card in my laptop's card reader with the following CHS:  1936 cylinders, 255 heads, 63 sectors/track.  Now if I take that drive and wipe it with *dd* and try to reformat it in *gparted*, it will have different CHS values, and it may or may not work!

---

### Post by The musmula on 2014-09-25
well... it is something. Thank you, I will try to find one of those flash drives to compare, if you are right I can tell my client she can feed the flash drive to the trash can (what she knew all along... lol).
Anyways, last time she used the flash drive she was copying data onto it from her Vista, the PC froze for more than half an hour so she had to crash it... I am pretty sure that could cause a simmilar (probably worse) situation you described earlier :)

thanks for your time

This is great.
It seems you are right about Gparted and flash drives. I did the exact same thing in fdisk (I love console apps) and it worked right away. I didnt even have to clear the drive with dd, now data stays on the disk even after being unpluged. Thank you

---

