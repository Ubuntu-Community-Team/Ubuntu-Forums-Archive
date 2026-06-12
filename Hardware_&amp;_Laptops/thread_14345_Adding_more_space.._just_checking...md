---
title: "Adding more space.. just checking.."
date: 2005-02-06
forum: Hardware &amp; Laptops
---

### Post by jak on 2005-02-06
Hi,

I have a 160GB drive in hda and an 8GB drive in hdb, now I've been using Ubuntu for  about just over a month and I'm starting to run out of space on my little 8GB drive I used for Linux.
The 160GB drive is in 3 partitions, hda1 is the boot, hda2 is ~110GB of NTFS for my (now rarely used) Windows installation, and ~50GB of FAT32 on hda3 so I can transfer files to and from the OSes.
I'm really running out of space so thought I could move /home onto hda3 to make the use of the space. I think I have it figured, but thought I best check with people who know their stuff.
I'm going to move all files from /home to /mnt/shared (where hda3 is currently mounted) and then edit fstab to contain an entry like,

FileSystem      MountPoint     Type     Options     Dump     Pass
....
/dev/hda3     /home     vfat     umask=000     0     0

I'm not to certain on what I should be putting so thought it best to check before I go messing things up.
Any comments or suggestions would be highly appreciated,
Thankyou.
Jak.

Update:
I went ahead, after a look I decided to put
/dev/hda3     /home     vfat     defaults,umask=000     1     2
instead of the line above in fstab, but when using
cp -ax * /mnt/shared/
in /home to copy files, the copied files all had the owner "root" which I couldnt change back afterwards.
So I'm tarring and gzipping all files now in /home.old (I made a backup just incase) and then going to extract them in /home

Update:
Didn't work. Thinking I doubt I would use Windows frequently anymore I used mkfs.ext3 to change the filesystem and it works fine. 47.3 GB free now instead of ~200mb.
Guide:
[http://www-106.ibm.com/developerworks/library/l-partplan.html](http://www-106.ibm.com/developerworks/library/l-partplan.html)

---

