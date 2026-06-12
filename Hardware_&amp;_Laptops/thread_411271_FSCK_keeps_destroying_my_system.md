---
title: "FSCK keeps destroying my system"
date: 2007-04-16
forum: Hardware &amp; Laptops
---

### Post by dibrom on 2007-04-16
I've never been so angry at software before.  I'm trying my best to refrain from saying things like "I'm going back to MS and use a REAL OS again", and worse yet, actually doing it.  I'm at the end of my tether and here are my woes:

I have a system with four HDD's in and am using MD and LVM2 to have a lot of fun.  This system has been working fine for two years, but recently I decided to perform a clean install, resize my Partitions and finally delete that windows partition i had kept for legacy purposes.

That problem is FSCK & Software RAID 0.  Unfortunately, FSCK also destroyed the evidence, but this is roughly what I saw going on:

My Raid Setup:
MD0 - RAID 0 - SDA6, SDB6
MD1 - RAID 0 - SDA7, SDB7
MD2 - RAID 0 - SDA8, SDB8
MD3 - RAID 0 - SDA9, SDB9

FSCK, instead of scanning MD0 on reboot, scanned SDA6.  Considering that it's a RAID0, FSCK found some "File System Errors" and decided to fix it.  This included clearing some superblocks, fixing journals and other bits which it did without asking me.  How did FSCK get to SDA6?  I don't know why or how (there's nothing in my fstab to suggest doing this), but it navigated to 
/dev/evms/.nodes/sda6.  It also did this for SDA7 and SDA8.

My only guess is that I use UUID's in my fstab file.  So I looked under /dev/disks/by-uuid to see where the udev links were pointing, nope... pointing to the correct spot (/dev/md0, md1....).

How could this be? How can I prevent FSCK from going freelance on my PC hardware? If I had been asked "Do you want me to fix this?" I would have answered no, BEFORE it cleared journals and so forth.

What's worse, this is the third time in three days.  I have spent stupid amount of hours trying to set this all up.  I'm not touching Ubuntu 7.04, because I tried that twice (I know it's beta, but four days before beta release and, well, I downloaded 6.10 and installed that instead).  What disappoints me is that 6.10, well, disappointed me.  Do I need to roll back to 6.04?

I haven't lost important files, those are backed up regularly and exist on plain ext3 partitions.  I'm too scared to reset my PC right now and, well, I'm considering the amount of work it might take me to return to Windows XP and whether it is worth it.

If you've read this far, I guess the only question I have is how can I limit FSCK from making decisions for me?  I can tell the difference between MD0 and SDA6, I don't trust it to.

---

