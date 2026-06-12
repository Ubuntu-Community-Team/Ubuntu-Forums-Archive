---
title: "Is there a use for a failing hardrive or a way to salvage part of the storage space?"
date: 2010-02-09
forum: Hardware
---

### Post by zarthon on 2010-02-09
I have a western digital 500GB HD that was part of an array. A SMART utility reported it was failing. Over 300 blocks have been marked bad and one block was not able to be relocated. Is there any use for it without any probing and tuning? With probing and tuning is their a way to just use the good parts of it? 
Since the drive was part of an array with lvm on top of it the file system approach described at [http://smartmontools.sourceforge.net/badblockhowto.html](http://smartmontools.sourceforge.net/badblockhowto.html) can't be used with existing files and it seems indirect to use a file system if i can just write logical blocks directly with dd.

In my imagination there Is a chance the problem is limited to a limited cylinder range and that the problem may not spread but prehaps this is shear fantasy!

If it's a cylinder range that is bad I was thinking I'd write a script to create several partitions and then using dd write some clever bits using into each while monitoring the SMART information with smartctl ( package smartmontools ) then perhaps I could narrow down where the problem is and also get the drive to mark many of the faulty blocks bad. The script could then create separate partitions around the bad areas. Once they were partitions off it could optionally free the reserved blocks from the firmware bad block reallocation for use in further failure of the used portions. (if this is possible.)
**Does a salvage utility like this that already exist?**  

**Is there a use for a drive that still works well but may have limited life?**
I was thinking would not matter much for stable system files as part of a firewall or utility pc I could mount paritions from it for /usr /bin and /sbin. That would also limit writes to the drive but it would not consume much space and it's a pretty big drive.
**Could it be used as an archive drive? Or will it continue to fail even if it's kept cold 99% of the time? **


Thanks ahead of time for your help insights and humor !

I use Ubuntu 9.10 Karmic Koala

---

### Post by tgalati4 on 2010-02-09
man badblocks

---

### Post by zarthon on 2010-02-11
> **tgalati4 said:**
> man badblocks

Thank you for your suggestion.

SMART tests reveal trouble before e2fsck or badblocks finds out about them. After the firmware of a drive runs out of free space to map logical blocks then the file system tools must handle the problem. 

Remapped blocks cause problems with arrays where the failing disk in the array is doing extra seeks on the hardware level. This slows reads and writes to the whole array. Other than this lag they are transparent to the file system and tools.

Specifically badblocks is not SMART aware. It analyzing file system level blocks which are mapped to logical blocks by the hard drive firmware. Logical blocks are composed of two kinds of blocks on the firmware level. Those that are in sequence on the disk and those that have been remapped to the free space reserved for use by the firmware to prevent file system level problems. 

So are you saying that one option would be to force the drive to consume the reserved space and then use badblocks to create a map of additional blocks?

In my opinion a better solution would be to identify and partition off the bad area of the disk and reserve the free reserved space for future issues BUT this may not be possible because it is possible that it's a sector and not a cylinder that is bad.

---

### Post by tgalati4 on 2010-02-11
A thoughtful explanation.  

First, is this drive in a USB enclosure, a desktop drive, a notebook drive?

SMART only covers 2/3's of failure modes.  The other 1/3 are spontaneous and unpredictable.

It's possible that your bad sectors are from a vibration mode.  Is your drive secured in it's drive bay?  Do you have rubber washers or other dampers installed?

I would first use the manufacturer's utility (try using Ultimate Boot CD) to reformat the disk, and perform a surface scan.  If that utility doesn't find any problems, then you can try to put the drive back in use, but I would only use it for non-critical use--say downloads of your favorite cartoons.

There are so many things that can go wrong with a drive.  Trying to guess what your exact problem is difficult.  Therefore trying to propose a work-around is even more difficult.

I have had SATA drives act strange, that were outside of a machine, not screwed down.  If your drive is secured and the cables have been reseated, then I would presume that you have a crashed head.  Was there an identifiable event--such as a power outage that triggered the SMART warnings?

---

### Post by markbuntu on 2010-02-12
Surface scan for sure. More than once. If the reports differ then the drive is going bad and will be nothing but a headache, even as a temp partition. You could use it for a permanent trash/email receptacle, it will be sure to lose anything you put in it. 

Or you could just put it in a trash receptacle.

---

### Post by sgosnell on 2010-02-12
The platters, when removed, make excellent mirrors, especially survival signalling mirrors.

---

