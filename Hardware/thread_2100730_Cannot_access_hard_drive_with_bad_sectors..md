---
title: "Cannot access hard drive with bad sectors."
date: 2013-01-02
forum: Hardware
---

### Post by styk3 on 2013-01-02
Some background info: 

A friend of mine had to force shutdown his Windows laptop after it had become unresponsive. After reboot, it refuses to boot and asks  to insert installation CD. 

After a very tedious few hours of trying different approaches with the Repair tools with windows, there is no result.

I decided to rescue the files and format, so I boot up Ubuntu. It takes a LOT longer than usual, nearly 45 mins to fully boot up. 
It also happens that I can't access the files on that hard drive (although it does recognize the drive).

Disk management shows that the HDD (Samsung HN-M250MBB, 250GB) is okay but has 8 bad sectors. I'm assuming this has something to do with all the problems.

Could anyone suggest a course of action from here on? There is some very valuable data there, and formatting it is a last resort (although not out of the question). 

Thank you in advance.

---

### Post by ahallubuntu on 2013-01-02
How did you establish it has "bad sectors?"  Did you check the S.M.A.R.T. status?  In Ubuntu, try GSmartControl or try the Parted Magic Linux distro (great CD for troubleshooting).  How many Pending Sectors does it have?  (Reallocated Sectors aren't a big deal if you only have a few - they represent sectors that have failed and ALREADY BEEN REPLACED with spares, though the drive will eventually run out of spares.)  Check the Attributes in GSmartControl (or "Disk Health", same thing, in Parted Magic).  Any other attributes in red?

The disk may well be failing, and after you recover any files (if you can), you may need to junk it and get a new drive.  If it has only eight bad sectors, it should be possible to get most of the files off - IF you have only eight.

First things first: after you check S.M.A.R.T. you could probably boot a Windows CD and run chkdsk /f on the drive.  That may take a very long time especially with bad sectors, but it might fix the filesystem enough to be able to access most of the files.

You can also look into ddrescue and testdisk.

---

### Post by nainsurvolte on 2013-01-02
+1 for everything mentioned to check if drive is faulty.

 If it is indeed faulty, I have no clue as to what is good or not to do.  Could it damage more the disk to make it work or even affect the data  ???

If it is not that faulty, and since it is a 250GB, I would create a complete disc image that could be done within testdisk or using dd. 

I passed the last 2 weeks at trying to recover information from corrupted partition disk myself but had enormous amount of data that kind of prevented me from imaging all the data. Now, I may have done a mistake or even a software I used may have done something wrong, and now the disk have been altered even more. I also read that you can block the disk from being written on, but have not searched for how to do, but should have.

Good luck

---

