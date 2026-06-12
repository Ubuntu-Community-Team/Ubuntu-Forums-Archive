---
title: "Installation Question Re: HP Recovery Partition"
date: 2009-09-09
forum: Installation &amp; Upgrades
---

### Post by *Torpedo* on 2009-09-09
I've used Ubuntu since Dapper Drake and really love it. :)

Before the question, here's some background info: I'm working on a friend's Windows XP machine that recently crashed and have been able to successfully back up all his files for him with a Linux LiveCD. Since he doesn't have the XP CD and is willing to give Ubuntu a try, I am now planning on installing Ubuntu on this computer.

Now for the question: It's an HP that has a 80 GB hard drive split into 2 partitions: the main 70 GB (NTFS) used for the OS and all it's files, and a 10 GB HP Recovery Partition (FAT or FAT32) that right now doesn't even do any good. I'm just wondering if he later decides he wants to go back to XP and buys a XP CD, would he need that 10 GB HP Recovery Partition to be there, or can I just format the entire 80 GB to one ext3 partition?

---

### Post by Earl_Maroon on 2009-09-09
I believe these recovery partitions are for resetting the machine to the factory defaults.
If/when your friend is installing a new copy of XP it shouldn't be of any consequence whether that partition is there or not.
As you've backed up his files there shouldn't be a problem as far as I can see.

---

### Post by stlsaint on 2009-09-09
the best thing to do would be to make a image backup of that hp revoery partition. that way he wont need to go buy a cd. but should that partition be bad and you cant back it up ad your friend does get the cd than...NO you will not need that recover drive to install xp..granted he will have to go thru and install the individual drivers that xp wont grab automatically which can be a pain. so in summary.
1) Try to make backup image of recovery partition than format entire drive to fully 80gb
2) NO he will not need the recovery drive should you choose to install...but i will cause alot more work.


Happy Ubuntuing

---

### Post by *Torpedo* on 2009-09-09
Alright, thanks for the info guys. :)

---

### Post by Zimmer on 2009-09-09
Also, did your friend make recovery CD's from the HP partition?
If those ar OK then (in theory) he should not need the partition.....

ps.
I have kept the partition with  my dual boot AND the disks.... just in case ;)

---

### Post by *Torpedo* on 2009-09-09
> **stlsaint said:**
> the best thing to do would be to make a image backup of that hp revoery partition. that way he wont need to go buy a cd.

> **Zimmer said:**
> Also, did your friend make recovery CD's from the HP partition?

There aren't any CD's made from the recovery partition, so what would be the best way to go about making an image of it?

---

### Post by Zimmer on 2009-09-09
Have a good read over here
[http://www.partimage.org/Partimage-manual_Usage](http://www.partimage.org/Partimage-manual_Usage)

This may be what you are lookng for..

---

### Post by *Torpedo* on 2009-09-10
> **Zimmer said:**
> Have a good read over here
[http://www.partimage.org/Partimage-manual_Usage](http://www.partimage.org/Partimage-manual_Usage)

This may be what you are lookng for..

Thanks again for the info, and I'll go mark this thread as solved. :cool:

---

