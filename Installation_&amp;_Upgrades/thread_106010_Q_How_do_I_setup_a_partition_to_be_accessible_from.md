---
title: "Q: How do I setup a partition to be accessible from both XP and Linux?"
date: 2005-12-19
forum: Installation &amp; Upgrades
---

### Post by Logic* on 2005-12-19
I'm setting up a dual boot of XP and Ubuntu ... have decided I need XP there as a backup while I am learning Linux.

I have a storage partition that I'd like to be able to have read and write access to from both XP and Ubuntu.  I know I could use FAT32 - but from what I gather it wouldn't be very efficient. How is the NTFS write support for Linux? Stable?

Basically, my question is, what would you do.. ? :) 

Thanks for listening.

---

### Post by Sutekh on 2005-12-19
Efficient or not, NTFS write capability in Linux isn't the way I'd go.  I'd go the FAT32.  In fact I *did* go the FAT32, and I'm quite happy with that.

You could always make a small NTFS partition and test using it.  There are programs that will do this, I think one's called Captive NTFS or similar.  There are a lot of threads dealing with writing to NTFS.

---

### Post by Logic* on 2005-12-24
What if I have about 120 GB of stuff that I want read and write access to from either OS? Can it be done? Whats the size limit on a FAT32 partition, anyway?

edit: I've just gone with a FAT32 drive. I thought the limit was **much** smaller :???: 

Thanks :-k

---

### Post by Sutekh on 2005-12-24
Yeah, I've hear people say its 32GB, but I doubt that since I have a 120GB partition working fine with FAT32.

Oh maximum *file* size is 4GB, but maximum partition size is 2TB.  That could be a problem if you want to store heavy duty video files.

---

### Post by The Warlock on 2005-12-24
[QUOTE=Sutekh]Yeah, I've hear people say its 32GB, but I doubt that since I have a 120GB partition working fine with FAT32.

Oh maximum *file* size is 4GB, but maximum partition size is 2TB.  That could be a problem if you want to store heavy duty video files.[/QUOTE]
The reason some people think that the FAT32 limit is 32 gigs is because Windows XP refuses to create a FAT32 partition larger than 32 gigs. It will *read* larger partitions just fine, but it won't create them because they think that they know what you want to do with your computer more than you do (which is why we're here, right?)

And yes, maximum file size is four gigabytes, so DVD isos are right out. Sorry.

---

### Post by brjoon1021 on 2007-02-21
Hey guys,

I am glad that I found this thread. Are those of you that are using FAT32 as a common Windows and Linux storage partition still happy that you went that route? I am looking the a good solution. I don't know whether to go FAT32, NTFS with the NTFS-3G driver for the Linuxes so that they can use NTFS or the opposite extreme by making the partitions ext2 or 3 and putting the driver in windows that allows it to read and write to Linux EXt2 partitions.

Thanks,

B.

---

