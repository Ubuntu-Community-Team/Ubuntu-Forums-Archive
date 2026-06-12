---
title: "How to manually map bad sectors on a HD?"
date: 2016-06-10
forum: Hardware
---

### Post by mma8x on 2016-06-10
I have a media server that flaked out after upgrading ubuntu. Started throwing weird errors, looks like I have bad sectors. SMART testing came back ok. I'm running badblocks now, and it's taking FOREVER once it started encountering the bad blocks. Several days so far. It appears that I have a bunch of bad sectors at the end of the drive. So far I have every sector from 1459946496 through 1463934378 marked bad. My HDD has blocks ranging to 1465138583. This is about 3gb on a 1.5 TB drive. I realize that my drive is likely failing. I have all the important data off of there. I'd like to just manually mark sectors 1459946496 through 1465138583 as bad. The file format just seems to be sector/new line/sector +1/new line. How do I either a) write a script that will give me the appropriately formatted text file or b) pass a range of values on to e2fsck?

---

### Post by yoshii on 2016-06-11
A very long time ago, when I was using Windows, I used ScanDisk in DOS mode to get a visual idea of where the bad blocks were on my failing used hard drive.  

Then, what I did was to split the hard drive into two partitions around the bad blocks so that the bad blocks were never even used at all.  They were in an unused drive area.  
You could try that.  

One thing to bear in mind... on Windows systems, the last 8 GB of drive space is supposed to be left unused.  This is so that some of it can be reclaimed to replace bad blocks as they occur.  So when you do your drive formatting, it's best to leave some of the space at the end unused.  I'm not sure if this applies to Linux systems also, but it might.  These days hard drives are so huge, even leaving out 24 GB from 320 GB or 2 TB is nothing.  

Also, because of an old lingering bug in older versions of gParted and because of MBR/Partition map stadard issues, it's best to leave the first 2 MB of drive space unused also.  
gParted will default to leaving the first MB of drive space unused, but it's actually safer to avoid the first 2 MB so that your partition table won't accidentally get overwritten by some softwares or firmwares.  

If you do partition the drive to work around the bad blocks, you might be able to use LVM to use the two partitions as if they were one.  But unfortunately I don't know how to accomplish that.  

Good luck.

---

