---
title: "Partitioning with fdisk"
date: 2009-09-12
forum: Hardware
---

### Post by Spiffworks on 2009-09-12
Hi all,

My first post. I have a 160GB sata hard disk that I'm having trouble formatting. This is the fdisk output.

[B]karthik@karthik-desktop:~$ sudo fdisk /dev/sda
[sudo] password for karthik: 

The number of cylinders for this disk is set to 19457.
There is nothing wrong with that, but this is larger than 1024,
and could in certain setups cause problems with:
1) software that runs at boot time (e.g., old versions of LILO)
2) booting and partitioning software from other OSs
   (e.g., DOS FDISK, OS/2 FDISK)

Command (m for help): p

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x8350c562

   Device Boot      Start         End      Blocks   Id  System
/dev/sda2            3825       19456   125564040    f  W95 Ext'd (LBA)
/dev/sda3            5355       19456   113274283+   7  HPFS/NTFS[/B]

The only partition should be sda3, which is 108GB in size and has my data. Is sda2 some sort of requirement or can it be deleted, leaving sda3 intact? I want to erase everything but sda3 and install Ubuntu in the free space. Meanwhile, GParted doesn't recognise any of the disk's partitions, saying that there is 149 GB of unallocated space. Ubuntu, however, mounts sda3.

Can anybody explain this?

Thanks,

K. K

---

### Post by relay_man on 2009-09-12
The dev/sda2 is an extended partition.  This was just explained to me a short time ago by others here.
It's purpose is to allow other "virtual" partitions if they become necessary.
A typical installation will only allow 4 partitions(linux system).
I guess some people find it necessary to have more than 4 partitions.
(when dual booting possibly?)

I'm not familiar enough with MS windows to say  that the dev/sda3 partition can be safely deleted.
In a linux system, it can be safely deleted if no virtual partitions will be needed.

It appears that the dev/sda3 is your windows partition.(103GB)

I've not used Gparted to resize partitions, but I found this thread:
[http://ubuntuforums.org/showthread.php?t=96617](http://ubuntuforums.org/showthread.php?t=96617)
which appears to have some useful info.

---

### Post by Spiffworks on 2009-09-12
I want  to install only Linux on this hard disk, so I can delete sda2, right? The main aim is to get Ubuntu to recognise the partitions in the live session, which it doesn't(It does the same as GParted). Anyway, will try deleting sda2 later in the day, on a Windows machine now.

Edit: Problem solved, deleted sda2, and GParted is detecting it fine. I guess the Windows extended onsense was messing it up. Now on to installng Ubuntu.

Thanks a lot,

K. K

---

