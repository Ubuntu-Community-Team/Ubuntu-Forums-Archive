---
title: "Unable ro reclaim all space on drive"
date: 2014-09-14
forum: Hardware
---

### Post by cecilieaux on 2014-09-14
I have a 500GB data disk with a now-emptied Windows data (NTFS) partition, a /home partition, and between (100+ GB ) of unallocated space. I would like to have the whole drive for Linux (Ubuntu 14.04 LTS) /home. 

Of course, there is 308 GB of data for which I have no backup space (an external drive has a variety of backups, probably with dupes, as does /home (yes, I know, not a tidy disk housekeeper).

Problem: I used Gparted to move/resize the 300+ GB /home to grab the unallocated space, and it went up to about 200GB or so then reassessed and started all over. After it did it twice (immobilizing my computer for a day) I stopped and realized I'm doing this wrong or not thinking right or something.

Here are the specifics of my setup:

> NAME   MAJ:MIN RM   SIZE RO TYPE MOUNTPOINT
sda      8:0    0  74.5G  0 disk (WINDOWS ntfs)
&#9500;&#9472;sda1   8:1    0    47M  0 part (Dell utility)
&#9492;&#9472;sda2   8:2    0  74.5G  0 part (XP)
sdb      8:16   0 465.8G  0 disk 
&#9500;&#9472;sdb1   8:17   0    41G  0 part /media/<data> (WINDOWS ntfs)
&#9492;&#9472;sdb2   8:18   0 308.3G  0 part /home
sdc      8:32   0  74.5G  0 disk 
&#9500;&#9472;sdc1   8:33   0  65.2G  0 part /
&#9500;&#9472;sdc2   8:34   0     1K  0 part (dunno where this came from)
&#9492;&#9472;sdc5   8:37   0   9.3G  0 part [SWAP]

I am feeling very stupid. Would appreciate some pointers. What am I missing?

C

---

### Post by weatherman2 on 2014-09-14
Your map above shows 308.3GB for /home .  Are you saying you want to reclaim the remaining 41GB on /dev/sdb for /home?

The problem is that while growing a partition forward is usually quick and easy, growing it backward is not.  That 41GB in /dev/sdb1 can be reclaimed, but if you let Gparted do it, it will have to MOVE all of the data in sdb2 forward, which could be very time consuming, as I think you found out.

A better solution, if you have the space somewhere, is to copy off all of the data on /home (/dev/sdb2) somewhere else, then delete /dev/sdb1 and /dev/sdb2 and make a new /dev/sdb1 all for /home, then copy all of the data back to it.  It might be easier to use a live boot CD or USB to do the moves of /home 

(/dev/sdc2 is probably the extended partition FYI - not needed on that disk but Ubuntu often creates one anyway, to contain other partitions.  It will have 0 length because it doesn't have any data - only other logical partitions inside.  You could have lots of logical partitions inside an extended partition, but if you don't create one, you are limited to only four primary partitions on an MSDOS-style disk.  Making an extended partition gives you more options for future expansion.)

---

### Post by cecilieaux on 2014-10-09
> **weatherman2 said:**
> The problem is that while growing a partition forward is usually quick and easy, growing it backward is not.

Lesson learned, did a massive backup and reinstall wiping out everything on the larger HD. Now works fine.

Thanks!

---

