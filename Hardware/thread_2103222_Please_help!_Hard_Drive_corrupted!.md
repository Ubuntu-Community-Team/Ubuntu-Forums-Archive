---
title: "Please help! Hard Drive corrupted!"
date: 2013-01-09
forum: Hardware
---

### Post by A6Tech on 2013-01-09
Guys, I'm pretty new to Ubuntu and this forum, so I'm not sure if this question is in appropriate section. But, I need big help. Anyway, I was playing with Ubuntu Disk Utility, and I saw that one of my partitions have boot label, and I wanted to remove that label as that partition doesn't contain any OS. But, Ubuntu froze in a middle of process, and I had to restart the computer. When I booted Windows, I couldn't access the partition and It was shown as RAW file system in Disk Management. Can you please help me, that partition contains essential data which I mustn't lose If I want to continue with life :(

---

### Post by ahallubuntu on 2013-01-09
Sounds like the partition table got corrupted.  That means your file structure is probably gone.  The files that you care about can probably be recovered with testdisk.  You'll have to boot up a live CD or connect the drive to another computer or something like that plus connect another drive to copy the files to (or copy over a network).

[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

After you're done this process, I presume you will start making regular backups?  Hard drives can fail without warning, even if you don't do anything dumb, and you could lose everything and have NO option to get the files back.  Some of us have had to learn this lesson the hard way.

---

### Post by A6Tech on 2013-01-09
I've checked the drive with Advanced NTFS Recovery, and I could see the folders and files, but I can't recover them as I haven't bought the software. Is there any free alternative? TestDisk says it can not recognize the file system.

---

### Post by A6Tech on 2013-01-09
Oh my God, Remo Recover is the solution. It found all the files with the folder structure as it was before, now I just need another hard drive to copy those files. Thanks to all the programmers who made that program :D

---

### Post by Hendry on 2013-01-09
There was no way to recover your partition with a live cd?

---

### Post by A6Tech on 2013-01-09
I haven't tried that, but It would be nice if I didn't even have to recover files. Maybe there is just a solution to repair that partition.

---

### Post by A6Tech on 2013-01-09
I'll try with Gparted and reply how it went.

---

### Post by ahallubuntu on 2013-01-09
> **Hendry said:**
> There was no way to recover your partition with a live cd?

Not if the partition table on the hard drive has been corrupted, no.

---

### Post by oldfred on 2013-01-09
RAW in Windows means unformatted, but it also means that the PBR or partition boot table is not correctly seen as NTFS. NTFS partitions do keep a backup PBR that testdisk can restore or testdisk can build a XP type NTFS PBR. Windows 7 PBR is different.

Does partition table see partition as NTFS?

sudo fdisk -lu

If not use Disk Utility to change to 07, do not reformat, just change type.

Then see if testdisk sees partition and look to see if it has a backup PBR.

       Instructions
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)
[http://www.cgsecurity.org/wiki/Menu_Analyse](http://www.cgsecurity.org/wiki/Menu_Analyse)
[http://www.cgsecurity.org/wiki/TestDisk:_undelete_file_for_NTFS](http://www.cgsecurity.org/wiki/TestDisk:_undelete_file_for_NTFS)

    
This was for those who installed grub to the Windows PBR, but the fix is the same, if a damaged partition boot sector.
Fix for most, a few have other issues, better than windows fix in many cases as it also fixes other parameters:
If win7 use small 'system reserved' NTFS partition instead of the partition where windows was installed for win7
This has instructions on using testdisk to repair the install of grub to the boot sector for windows from Ubuntu or Linux LiveCD.
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)
You want to get to this screen:
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step#NTFS_Boot_sector_recovery](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step#NTFS_Boot_sector_recovery)

OR:
[HowTo] Repair the bootsector of a Windows partition  - YannBuntu
[https://help.ubuntu.com/community/BootSectorFix](https://help.ubuntu.com/community/BootSectorFix)
[http://ubuntuforums.org/showthread.php?t=1926510](http://ubuntuforums.org/showthread.php?t=1926510)

---

