---
title: "Need fix with my hdd drives"
date: 2009-04-14
forum: Hardware
---

### Post by Daivana on 2009-04-14
Hello all!

I'm new to this OS, my XP broke because of viruses so I installed Ubuntu, now there are some issues with my hard drives I need to fix.

First when I execute  sudo fdisk -l I get:
 > Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa725a725

   Device Boot      Start         End      Blocks   Id  System

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe3f8e3f8

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        9353    75127941   83  Linux
/dev/sdb2            9354        9729     3020220    5  Extended
/dev/sdb5            9354        9729     3020188+  82  Linux swap / Solaris



I need to mount the /dev/sda: 200.0 GB drive and see it in Computer, but I can't.

Before I continue I will mention one thing, at first I could see the drive but I couldn't open it, somehow I managed to mount it, later I experimented with KwikDisk app and I did something to the /dev/sda: 200.0 GB drive, after reboot I dont see the drive in Computer.


Another thing is I don't understand the meaning about the system drive, why is it unknown type?
[IMG]http://img245.imageshack.us/my.php?image=screenshoth.jpg[/IMG]

---

### Post by cariboo on 2009-04-14
According to your listing /dev/sda isn't partitioned or formatted. I would suggest you install gparted, it is in the repositories. You can install it using Add/Remove Programs, or Synaptic Package Manager. Once it is installed, go to System-->Administration-->Partition Editor, and see if the drive shows up there. If you can still see the drive, you might want to try [Testdisk]("http://www.cgsecurity.org/wiki/TestDisk") to try and restore the partitions. Testdisk is also in the repositories.

Jim

---

### Post by Daivana on 2009-04-14
Thanks for the reply, in the partition editor I see the disk, I can't get to work the testdisk app, there are 4 options to choose for download, I don't know which one I have to download, I have Ubuntu 8.10 (intrepid).


Edit. I tried all of them, I don't know how to setup it :/


Ok I got it, working now on recovery.



It seams I can't recover it.
> Disk /dev/sda - 200 GB / 186 GiB - CHS 24321 255 63

The harddisk (200 GB / 186 GiB) seems too small! (< 383 GB / 357 GiB)
Check the harddisk size: HD jumpers settings, BIOS detection...

The following partition can't be recovered:
     Partition               Start        End    Size in sectors
  HPFS - NTFS          24320 254 63 46682 254 61  359245529










[ Continue ]

NTFS, 183 GB / 171 GiB





Alright, I understand now how to work with the app, I am coping the files on another volume, after that I will format it.


This is solved, thanks showing me the way cariboo907

---

