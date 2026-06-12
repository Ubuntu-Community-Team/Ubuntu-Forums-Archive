---
title: "HDD/SSD Dual/Triple Boot Combo"
date: 2012-08-01
forum: Hardware
---

### Post by Gargintua on 2012-08-01
hey, i really want the perfect hdd/ssd combo for my computer setup

at the moment
-60GB SSD: 1 ubuntu partition
-2x320gbs HDD Raid 0: Windows 7
-1TB External HDD: Storage

there are a few problems with this setup such as windows 7 speed. and the fact that my storage is on an external portable HDD. Another issue is that Windows 7 Quickly Fills up a 60 GB SSD like its nothing.

possible scenarios
-buy another 60GB SSD (120GB Raid 0): DUALBOOT W7/Ubuntu
-give small 60gb SSD to sister and buy larger SSD
-(What about TRIM? Last time grub didnt work on my dualboot SSD)

-3TB internal storage: (What about BACKUPS??)
-Multiple 1TBs internal storage in some RAID like arrangement
(Maybe 2 hard drive and hot spare or raid5) 
(pls note. I have No dedicated RAID Controller Hardware, Only Bios)

-Get rid of small 2x320gbs Raid 0

-possible hackintosh tripleboot

what would be your ideal/dream layout? (most effective or effecient)
Thanks for any thoughts or opinions
will be purchasing on friday afternoon

---

### Post by oldfred on 2012-08-01
We do not support circumventing TOS, EULA, etc here. Such threads will be closed and offending users will be penalized with infractions and warnings.
[http://ubuntuforums.org/index.php?page=policy](http://ubuntuforums.org/index.php?page=policy)

I do not believe in RAID for most desktops, see link below. It was used for speed, but now with SSD it does not really add much if anything. And RAID is not a backup.

Don't bother with RAID 0 unless you have a specific need for speed without data redundancy, since if one drive goes out, you lose the whole array.
[http://en.wikipedia.org/wiki/RAID](http://en.wikipedia.org/wiki/RAID)

I try to just backup my important data, but as a home user is is not as critical as a business might be. So most important files go to DVD as archive periodically and data is rsynced to different drives for short term backup.

I always find my own most optimal grand plan is obsolete a year or two later. After a couple of years, I lose some confidence on my drive(s) and get a new larger on and end up with lots of new space.

My latest new plan was  a new 60GB SSD which gives me room for two / (root) partitions, one current or long term and the other testing or maybe the next permanent version. But I also have an install of Ubuntu on every other drive except my XP which is now obsolete. I really like not booting XP anymore. :)

You should not have any issues with trim, but I prefer to keep Windows on one drive and Linux on other drives.

If you go with a new 3TB drive you will have to use gpt. Windows 7 will read gpt drives, but only boot from them if UEFI not BIOS.

[https://wiki.archlinux.org/index.php/GPT](https://wiki.archlinux.org/index.php/GPT)
[https://wiki.archlinux.org/index.php/Grub2](https://wiki.archlinux.org/index.php/Grub2)

[https://wiki.archlinux.org/index.php/Solid_State_Drives](https://wiki.archlinux.org/index.php/Solid_State_Drives) - SSD
[http://www.ocztechnologyforum.com/forum/showthread.php?54379-Linux-Tips-tweaks-and-alignment](http://www.ocztechnologyforum.com/forum/showthread.php?54379-Linux-Tips-tweaks-and-alignment)

trim does need ahci  which requires extra drivers in Windows 7. I would think you have done that already.

---

### Post by Gargintua on 2012-08-02
Thank you oldfred, you gave a brilliant idea for my new layout

-60gb SSD: Ubuntu
-80gb SSD: W7

-3TB HDD: Storage (Raid 1)
-2nd 3TB HDD: Backup (Raid 1)

-In this configuration both OS's are fast and have enough room to breathe. 

-Data on the Massive Storage HDD is safe because of RAID 1 (with identical HDD)

-Additional thoughts
-Still thinking about the SSD. If i had 1 larger SSD or 2 SSDs in Raid 0, i could effectively partion the the two operating systems. EG: 120 GB SSD, (30GB Ubuntu, 90GB Windows 7)

---

### Post by oldfred on 2012-08-02
Either should work, everyone has different ideas and there is not one best way. 

Some food for thought and why I have Ubuntu on every drive:
Creating a Dedicated Knoppix Partition for large drives
[http://www.troubleshooters.com/linux/knoppix/knoppix_partition.htm](http://www.troubleshooters.com/linux/knoppix/knoppix_partition.htm)
Except I have multiple Ubuntu installs and rotate newest install from drive to drive.

---

