---
title: "Bad blocks on Hard disc"
date: 2014-05-26
forum: Hardware
---

### Post by john230 on 2014-05-26
I recently ran a disc check on my hard disc with ubuntu. the results were 312 bad blocks were found. 
And according to system monitor, my total disc space is 488gb, available space is 459gb, used space
3.5gb. And the bar next to it shows 0%. Seems like ubuntu diregards the bad blocks as there is approximately
40gb of the hard disc unaccounted for. Is there anyway to save the bad blocks? what should i do with them?
[http://imgur.com/49bujJ3](http://imgur.com/49bujJ3) shows a screenshot of the system monitor.

---

### Post by tgalati4 on 2014-05-26
You would have to do some research on your specific drive, but each disk drive can tolerate a certain number of badblocks.  You can remove them permanently by using *fsck -cc*, but the disk firmware will mark them bad.  Until you run out of space to reassign them, then you will have problems.  For a 500 GB drive, I would expect several thousand badblocks for a buffer, but I don't know the precise number.

Keep an eye on the SMART parameters for the drive:

```
sudo smartctl -a /dev/sda
```

I have a disk with 80 pending sectors on a freenas server and I get an email if it grows beyond that.  You could write a script to perform a similar function.

Bad sectors can be caused by a variety of things.  Bumping the disk during writes, a worn spot on the platter, mechanical/electrical wear on the swing arm, failing head, etc.  Sometimes they show up after a new disk drive's break-in period.  Other times, they show up near the end of a disk drive's life.  You just don't know, and you can't predict it.

If badblocks are growing and your disk is within a warranty period, I would remove files from it and try to get a warranty return.  Be aware that the disk you get may be a refurb in worse shape, so you are taking your chances either way.

---

### Post by WinEunuchs2Unix on 2014-05-26
All HDD's can have a certain number of bad sectors new from the factory but 10% sounds way to high.  I would return it just on principle IF that is really the reason.  I don't think it is because you said 312 Bad Blocks = 40 Gigabytes.

I think block size is usually 512 bytes or 4,096 bytes or something like that.  It's possible there is a hidden partition on your hard drive or something else occupying that 40GB or perhaps you need to double check your math???.

You are lucky that the system can see the bad blocks it will mark them as unusable and never put good information on them.  On my hdd I just replaced there were files on there that would drive the system crazy every time it tried to read that corrupted hdd space.  chkdsk /f would always bomb out trying to fix the sectors.  Luckily that damaged hdd area was a free trial of Microsoft Office 2007 so it just stayed in that garbage hole for 7 years LOL.

---

### Post by tgalati4 on 2014-05-26
The 40 GB of space is partly the 5% reserved for system use--buffers and overages to prevent Bad Things from Happening(tm).  The other 5% is the overhead of an ext4 format--inodes, file tables, directories, superblocks, backup superblocks, and any other formatting stuff that I didn't mention.  That sounds normal.  You can turn down the 5% system reserve and use Ext2 to save space, but because disk space is cheap and the overhead is used to keep things working.  It's a decent tradeoff.

---

### Post by WinEunuchs2Unix on 2014-05-27
Thanks for the info on the 40 GB I was suspecting something akin to your explanation. I remember when 150MB external HDD's cost 5 grand...

---

