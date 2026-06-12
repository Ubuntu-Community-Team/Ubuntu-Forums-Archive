---
title: "Error 22 after uninstall"
date: 2006-01-10
forum: Installation &amp; Upgrades
---

### Post by Luke771 on 2006-01-10
I have a bad hard drive, good enough for windows (so far, anyway...) but not for linux; every time I tried to boot Breezy after some hours without using the computer, I got a lot of errors; after a few reinstalls I learned to always boot in recovery mode first, and then reeboot to regular mode after the errors had been fixed, and that worked for a while, but last time it was not possible to actually fix all the errors: I couldn't even automatically log in as root after recovery was done because (I suppose) some needed files had been lost. To make it short, I decided to do what I actually should have done earlier: uninstall Ubuntu and keep running windows until I get a new hard drive (I have a dual boot system with two primary partitions for Breezy and XP and one bigger FAT32 partition for file storage). So I rebooted from a Partition Magic CD, deleted the Ext3 and the Swap partitions, resized the extended partition and the logical FAT32 to make use of the free space created by the deletion, then I made the NTFS partition active and rebooted.
I had done that before and it always worked, this is the first time it fails, I am pretty sure that I did intall Grub in hd0,1 as I always do when installing on a dual boot - one hdd system, but I actually had a Grub problem with the previous Breezy install too (that was a stage2read error) and was told to reinstall Grub using the install CD in rescue mode, which actually got Grub to load, but the file system was still screwed up, so I had to reinstall Breezy from scratch. I installed Grub in hd0,1 as usual, so when setting the NTFS partition as active, the system should just load windows without trying to load Grub first, but that wasn't the case: I get Grub error 22, which I guess means that no Grub is found when tryng to load it(is it so?), but as far as I know, the system shouldn't even try to load Grub...
At this point the only thing I could do was booting from a live CD and come here crying for help again :-(  
OK, I hope I made it clear enough for someone to tell me how to fix this without having to rinstall windows too because I will have to do that anyway when I get my new hdd and now I just need to keep windows working some more days, then I'll buy a new hdd an reinstall everything.

---

### Post by Luke771 on 2006-01-10
the solution (of course) was to boot from the XP install CD in rescue mode and run FIXMBR.

---

### Post by scole on 2006-01-10
Well the easiest way to fix everything is to wipe out linux and start again :( You might say that thats impossible not to toot my own horn but i figured out a way that will allow you to unistall and boot right into windows on your first try. Just ready my thread the first post. That should set you right :) [http://ubuntuforums.org/showthread.php?p=634214#post634214](http://ubuntuforums.org/showthread.php?p=634214#post634214)

---

### Post by Dark Damo on 2006-01-10
Or you could do this.

Get webroot window washer for windows. Install it then make a bleach floppy. It distroy's and remerges all partitions then start everything from scratch? 

Might fix some problems you are having.


Or just format both the normal way?

---

