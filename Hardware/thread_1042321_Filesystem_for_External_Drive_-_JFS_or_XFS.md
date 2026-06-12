---
title: "Filesystem for External Drive - JFS or XFS?"
date: 2009-01-17
forum: Hardware
---

### Post by rvbhute on 2009-01-17
I have put a 500GB SATA drive inside a USB enclosure. I plan to use it as a media store to hold movies, music, etc. and maybe, backups too.

A point to note is that while it will not hurt if I lose the media files due to file system corruption (the home folder is more valuable), hey, no one wants to lose their collection (backup is simply not feasible, given the size). So I would still like filesystem damages to be minimal, in case of accidents like power failures and hard restarts.

I have searched around on Google and these forums and here are my thoughts/questions:

1. JFS - My first preference. Should I be worried by IBM's end of support and fading user community? - [http://ubuntuforums.org/archive/index.php/t-253483.html](http://ubuntuforums.org/archive/index.php/t-253483.html) Is this the only minus point for this excellent filesystem?

2. XFS - Yes, the power situation is not the best there is at my place, and I have to worry about hard restarts, sometimes caused by faulty hardware and peripherals. 

3. ext4 - The best of JFS/XFS with the best of ext3 - its coming with Jaunty Jackalope, but right now, I have to wait :)

4. Can I set a regular filesystem check for JFS partitions using tune2fs (or its JFS version)? Does this work for USB drives?

5. I have a 100GB partition on the internal drive, meant for the same purpose - it hold media during download, editing, etc before they will be moved to he external drive. It is mounted as a separate folder (/data). Can I make it JFS while keeping / and /home as ext3? What about the periodic checks as in case of ext3?

Thanks.

---

### Post by Trueno22 on 2009-01-18
I am alpha testing jaunty with ext4 and running intrepid with JFS on my root and home partitions.  

Honestly in my setup the Intrepid setup with JFS runs snappier than EXT4.  Programs start faster, transferring of files is 10mb/s faster.   

This could be due to Jaunty being in Alpha, but who knows.

I also use XFS on my external.

---

### Post by rvbhute on 2009-01-18
I have spent the day reading articles about JFS and I am convinced!

Just two more doubts:
1. If I convert /home and another extra partition (which I mount to /data) to JFS, can I set them to fsck every N mounts, just like ext2/3 filesystems? Not that it may be needed, but why to take chances, right? The /data partition could be unmounted while logged in and I could run the fsck manually, but I'm curious about /home.

2. Quite a few negative posts mentioned that JFS (and XFS) are sensitive to power failures and hard reboots. The procedure to power down the external drive is to unmount it and switch it off from the back panel - this sounds almost like we are cutting off power to the drive AKA power failure. Will this damage the JFS partition or am I being too paranoid?

---

### Post by Trueno22 on 2009-01-18
My external has XFS I do hard shut downs on it by just holding the power button and not un mounting it first.  Never had any problems.  My guess is that UBuntu senses I pushed the button and unmounts it.

---

