---
title: "External HDD needs filesystem/formatting"
date: 2011-08-14
forum: Hardware
---

### Post by Spock. on 2011-08-14
I have a 1TB External Maxtor Basics HDD (which is nearly full I might add) which I store everything on.  I removed it from my desktop (Win7) the other day to use on my netbook (ubuntu 11.04) to transfer some files, but when I put it back on my desktop It brought up a message box saying it needs to be formatted before I can use it.  I then plugged it back into my netbook to see if it was just the desktop being a nuisance  or whether it was the actual HDD.
fdisk -l says it's /dev/sdb with a bunch of text about cylinders, but when you try and mount it, it says that the device needs a filesystem.

Is there a way to restore this drive without losing data or am I going to have to format it?
There's nothing of importance on there, I'd just rather not have to build up again.

Thanks for reading.

---

### Post by dandnsmith on 2011-08-14
Sounds like the partition table has gone.
There are ways to recover this (if you don't happen to have recorded the original details) - try googling for testdisk, ubcd, Hirens Boot CD: I feel that Ive seen this stuff on at least one of those.

---

### Post by lewtds on 2011-08-14
> **Spock. said:**
> 
fdisk -l says it's /dev/sdb with a bunch of text about cylinders, but when you try and mount it, it says that the device needs a filesystem.
Thanks for reading.

Does it show a partition table?
In case it doesn't, it means you MBR is gone. If only the MBR (partition table) is damaged but nothing else is and you have only one partition on the disk then there is a pretty good chance of recovery using parted's rescue command.

---

### Post by gakon77 on 2011-08-14
> **lewtds said:**
> Does it show a partition table?
In case it doesn't, it means you MBR is gone. If only the MBR (partition table) is damaged but nothing else is and you have only one partition on the disk then there is a pretty good chance of recovery using parted's rescue command.

Hello there,

yesterday I have a similar issue with my external Hard Drive (1Tb, NTFS?)  - by mistake erased the file system of the HDD with the partitioning  GUI tool in Ubuntu, Palimpsest. 
It couldn't delete the whole lot in the HDD because it took the application just a flick to do it! 

TestDisk doesn't detect the only partition the HHD has (still I hope), so I wonder if it may be the same  issue about the MRB. 
I'm not sure if the original file system is NTFS and some test I performed with an spare flash drive weren't successful.

My question is, do you still think that the option in TestDisk about the MRB code is the solution? Or at least, is it safe?

Thanks.

---

### Post by Spock. on 2011-08-14
I did the MBR in TestDisk and it didn't make a difference for me.  Under the Advanced menu in TestDisk, I managed to list my files so I know they're still there.

---

### Post by Spock. on 2011-08-14
I've just been out for an hour taking my Son to the park, I got back and noticed that the drive has mounted and contains 2 folders $RECYCLE.BIN and TV Series, the rest of my stuff has vanished.  Have I lost 'em?

fsck /dev/sdb displayed the following:

```
dave@netbook:~$ fsck /dev/sdb
fsck from util-linux-ng 2.17.2
e2fsck 1.41.14 (22-Dec-2010)
fsck.ext2: Superblock invalid, trying backup blocks...
fsck.ext2: Bad magic number in super-block while trying to open /dev/sdb

The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device&gt;
```
does it help?

---

### Post by dandnsmith on 2011-08-14
I'm not sure about the detail of [i]e2fsck -b 8193 <device&gt[i] without checking it - the device&gt bit eludes me - but the principle is right, and could recover the filesystem.
If you have the resources, spacewise, I'd recommend making a backup of the whole space first using 
  dd if=/dev/sdb of= ...
(could use gzip to compress it somewhat)  
and then you can always get things back for another attempt.
HTH

---

### Post by coffeecat on 2011-08-14
@Spock, the presence of a $RECYCLE.BIN folder in your drive tells us that this is a Microsoft filesystem, probably NTFS. Indeed, you were using it with Windows 7, so it must be a Microsoft filesystem. But the terminal command fsck is for Linux filesystems. There is a fsck.msdos for FAT32, but there is no fsck for NTFS. You are in danger of further damaging that filesystem if you use fsck.

Two suggestions. Post the output of "sudo fdisk -lu" rather than just telling us it has a "bunch of text about cylinders". And see if you can repair it with chkdsk in Windows. If it is a NTFS filesystem, there is no Linux tool that can replace Windows' chkdsk.

---

