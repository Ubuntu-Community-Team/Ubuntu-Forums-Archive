---
title: "Dual boot question"
date: 2009-03-07
forum: Installation &amp; Upgrades
---

### Post by joshman1204 on 2009-03-07
I am in the process of converting from xp to linux and have several questions. I am not new to linux I used debian about 5 years ago but have since become an MCSE certified microsoft fan boy. Lately I gotten tired of the never ending spyware/malware battle and decided to format and start over!

Anyway I am trying to accomplish the following and need some help. I want to have a 50-100gig linux system partition, a 50-100gig microsoft xp partition and then a 600-700gig partition for all of my personal files(music, movies, pictures) that can be accessed by both systems.

Please let me know if this is possible and what the best way to accomplish it(i.e. one big drive, three smaller drives)

Thanks!

---

### Post by Agg23 on 2009-03-07
I suggest you should should use [Wubi]("http://wubi-installer.org/").  That is what I use for my computer.  It allows you to run ubuntu without creating a new partition.  I must say though you should use at least a 15GB disk image size because I've almost run out.

---

### Post by lykwydchykyn on 2009-03-07
You don't need even 50 gigs for a linux system partition.  20 gig will be adequate.  A few years ago I'd have said 10 gig was fine, but if you start installing a lot of these games that have 200mb+ of data, then you need more.

You probably don't want your actual home partition to be the big data partition, because you need this readable by both Windows and Linux.  I'd recommend NOT having your actual home directory readable on Windows, either by using a Windows file system or by installing the ext2/3 driver on Windows.  So you can use that extra 30-80 gig you didn't use on the system partition for your home directory, then make a link from your home directory to the big data partition.

As far as the physical layout of these partitions, I don't think it matters much, though windows xp seems to like being the first partition on the first drive.

---

### Post by joshman1204 on 2009-03-07
I know 50gigs may not be necessary but I would rather have way too much than not enough especially with the cheap price of storage these days. So if I understand right I could get a 150gig drive and install XP and ubuntu on it and then get a 1terabyte drive and use that as a huge media drive. How would I need to format the media drive to be accessible for read and write by both systems?

---

### Post by lykwydchykyn on 2009-03-08
> **joshman1204 said:**
> I know 50gigs may not be necessary but I would rather have way too much than not enough especially with the cheap price of storage these days. 

Ok.  As long as you promise to post a thread here telling everyone I was dead wrong when you break 20 gig (not counting /home). :mrgreen: 
> 
So if I understand right I could get a 150gig drive and install XP and ubuntu on it and then get a 1terabyte drive and use that as a huge media drive. 

Sounds like a good plan.

> 
How would I need to format the media drive to be accessible for read and write by both systems?

Windows reads FAT32 and NTFS natively.  I wouldn't want to deal with a 1 terabyte FAT32 partition if it's even possible to create one.    Linux's NTFS drivers so far have served me without any issues, though there are occasional complications mounting NTFS if the drive gets shut down uncleanly (e.g., losing power while booted to Windows).  

On the other hand, there is an ext2/3 driver for Windows that would enable it to read Linux's ext3 filesystem ([www.fs-driver.org](www.fs-driver.org)).  I've heard mixed reports about this one, but the few times I've used it I didn't have problems.

So it comes down to whether you trust Linux's NTFS drivers more, or this Windows ext3 driver more.  I'd go with the native filesystem for whichever OS you plan to use more often.

---

