---
title: "Dead drives"
date: 2013-08-18
forum: Hardware
---

### Post by jason13 on 2013-08-18
After switching out my old dying HDD for new drives I tried to recover some of the data off of them. First, the drive I operated off of (a Seagate) will try to boot, and the various partitions are recognized and available, except for the very large partition that served as /home, which is where my beloved data is. Second, my backup drive (a WD), which I haven't had plugged in, but worked fine the last time I did, is completely unrecognised by multiple Linux installations. I tried different SATA cables in different ports on my MB as well as different power connections. I know data can be recovered even after major problems, are there third party services for data recovery? Are there options I could use on my own that I haven't tried? I would rather have the data from the drives and I don't need the drives themselves (both 1TB drives)

---

### Post by TheFu on 2013-08-18
Data recovery is hard. Most businesses that do that work charge $3000+.  Sometimes it is a bad controller board, so they swap that out. The data on the original media inside is fine. Other times it takes much more work and they have specialized software and only use eSATA connected docks.

If the drives are making unusual noises - stop. Spend the money or live without the data. If you like and are willing to risk it, people have frozen their HDDs to shrink metals and read the last bits of data off a dying HDD. Read up on the techniques, since putting a HDD directly in a freezer is bad.

If the drives spin up fine, you can use **ddrescue** to mirror them at the device or partition level, THEN try to restore data off that mirror using other tools from the **testdisk** package.  It isn't easy and will take a long time with lots of manual effort.  The more of these tools that you use, the more likely you are to damage the drive and prevent the commercial places from being able to recover.  Always work off a cloned drive, never the original.

If the data is not that important and you are willing to risk destruction, there are tools like **Spinrite** ($90) which can force a refresh of the bits on the disk and that will restore the data.  Data recovery experts cringe at any tool which modifies the source in anyway like spinrite does.  For lazy bits, spinrite is a viable option.  It could be said that running **ddrescue** or **testdisk** will accomplish the same thing.

There you have it.  Personally, I find it easier to have nightly backups. Old data that hasn't been accessed in months can suffer from "bit rot" on any media.  With some care, it is possible to use HDDs and cheap optical discs for backing up some data, but we must try to recover it from time to time to ensure the media hasn't broken down.  I believe the process of accessing the data nightly during my backup processes helps to prevent failures and data loss on the source.

I've seen problems recovering data from DVDs burned in 2002 and I use 10% extra par2 files to help restore that data to be identical with the original.  A few 2008 discs have failed too, so it is impossible to know strictly by age when something will fail.  Spinning HDDs have strange failure and bitrot dates. It is impossible to guess even if they've sat on a shelf the entire time.

---

### Post by Sef on 2013-08-18
[Test Disk]("http://www.cgsecurity.org/wiki/TestDisk") like the first poster mentioned can recover data, though no results  are 100% guaranteed.

---

