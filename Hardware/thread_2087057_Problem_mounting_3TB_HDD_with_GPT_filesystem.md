---
title: "Problem mounting 3TB HDD with GPT filesystem"
date: 2012-11-22
forum: Hardware
---

### Post by miragemonger on 2012-11-22
Hello, everyone. I just setup a brad new 12.04 server and am having a problem mounting my Seagate 3TB hard drive that has all my data on it. The drive was formatted on Windows 7 and if I do a fdisk -l I get the following output (/dev/sda1) is the disk in question: 



> 
WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.
Disk /dev/sda: 3000.6 GB, 3000591900160 bytes
256 heads, 63 sectors/track, 363376 cylinders, total 5860531055 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1  4294967295  2147483647+  ee  GPT
Partition 1 does not start on physical sector boundary.


I have tried to mount this disk using the following command: 
mount -t ntfs-3g /dev/sda /fileserver

and get this error: 

> NTFS signature is missing.
Failed to mount '/dev/sda': Invalid argument
The device '/dev/sda' doesn't seem to have a valid NTFS.
Maybe the wrong device is used? Or the whole disk instead of a
partition (e.g. /dev/sda, not /dev/sda1)? Or the other way around?
Also tried using /dev/sda1 instead of /dev/sda and got the same error. 

Any ideas? Thanks in advance!

---

### Post by oldfred on 2012-11-23
You still have to have partition(s)

You cannot use fdisk with gpt partitions, it will just show the protective MBR as that is all it can see.

You have to use gdisk, parted or gparted.

It also looks like protective MBR does not include the full drive. Did Windows partition it correctly? 

       three Linux partitioning tools: the fdisk family [fdisk, sfdisk, and cfdisk], the libparted family [GNU Parted, GParted, Palimpsest Disk Utility, and several others], and the GPT fdisk family [gdisk and sgdisk]. 

            GPT fdisk Tutorial -srs5694 in forums
[http://ubuntuforums.org/showthread.php?t=1439794](http://ubuntuforums.org/showthread.php?t=1439794)
[http://www.rodsbooks.com/gdisk/](http://www.rodsbooks.com/gdisk/)

    
       repair gpt:
[http://www.rodsbooks.com/gdisk/repairing.html](http://www.rodsbooks.com/gdisk/repairing.html)

    
Post these, change sda to whichever drive it is, if not sda:
       sudo parted /dev/sda unit s print
or
sudo gdisk -l /dev/sda

---

### Post by miragemonger on 2012-11-28
Thanks for the reply oldfred. I was away for a couple of days and just go to this. Here is the output of the command requested: 
$sudo gdisk -l /dev/sda
GPT fdisk (gdisk) version 0.8.1

Partition table scan:
  MBR: protective
  BSD: not present
  APM: not present
  GPT: present

Found valid GPT with protective MBR; using GPT.

Warning! Secondary partition table overlaps the last partition by
1202 blocks!
You will need to delete this partition or resize it in another utility.
Disk /dev/sda: 5860531055 sectors, 2.7 TiB
Logical sector size: 512 bytes
Disk identifier (GUID): AEE558CD-5583-4AA8-80D7-6748DEB7B00C
Partition table holds up to 128 entries
First usable sector is 34, last usable sector is 5860531021
Partitions will be aligned on 8-sector boundaries
Total free space is 2014 sectors (1007.0 KiB)

Number  Start (sector)    End (sector)  Size       Code  Name
   1              34          262177   128.0 MiB   0C01  Microsoft reserved part
   2          264192      5860532223   2.7 TiB     0700  Basic data partition

---

### Post by oldfred on 2012-11-28
You  are the second user with an overlapping partition table issue.

[http://ubuntuforums.org/showthread.php?p=12377816](http://ubuntuforums.org/showthread.php?p=12377816)

In that thread I had hoped gdisk would automatically fix it. 

Not sure how to resize. Perhaps gdisk's advance mode.

The one procedure I did see in gdisk was delete partition and recreate with the new slightly smaller size. Best to have good backups of both old partition table and all data.

Not sure if gparted or any of the Windows tools will let you shrink the partition slightly. What partitioning tool did you use to create partitions?

---

### Post by miragemonger on 2012-11-28
Hmm, interesting. Well that definitely helps a lot and thanks for your quick responses! I used Win7's built-in disk format utility to create the partition. I should have used something better ... 

I guess the best thing to do at this point is to back it up and recreate the partition. 

Thanks again for your help.

---

