---
title: "Ntfs"
date: 2006-04-11
forum: Hardware &amp; Laptops
---

### Post by brettr on 2006-04-11
1) 
[INDENT]Hey... i've been looking around at the posts on NTFS writing... from what i gather it is in a sort of alpha phase.. 

I am just curious as to what time frame people expect for it to be reliable?[/INDENT]

2)

[INDENT]Also.. i am kind of stuck right now.. i have a 200GB HD In an enclosure, and i would like to use it to dump some backups as well as other stuff that i dont want on this HD. The problem is right now it is in NTFS mode.. i can dump what is on it on another box and then reformat it to FAT32, but i read somewhere that the limitations on FAT32 drives was 137GB and a max partition size of i think 32GB... as well as a max file size of 4GB.

So i don't know what to do, because i would like this external HD to be accessible from windows.... so i can put some stuff on it from the other box which is running windows. I also would not want to have like 6 partitions.. I don't know what to do heh...[/INDENT]

If anyone has any suggestions would appreciate hearing them.

Thanks

---

### Post by badrinarayan on 2006-04-11
I create and format FAT partitions in Linux using fdisk and mkfs.vfat and I don't have a 32 GB restriction. See if that works for you.

---

### Post by aysiu on 2006-04-12
FAT32 partitions can hold only files smaller than 4 GB. The partition size isn't that limited, though. I don't know what the limit is exactly, but I used to have a 100 GB FAT32 partition.

You can always have a huge Ext3 partition and use [http://www.fs-driver.org/](http://www.fs-driver.org/) to read it from Windows.

---

### Post by brettr on 2006-04-12
Hey, Thanks for the heads up on the ext3 support for windows, i was looking into that.

And i found out what the deal with the 32GB was

> Windows 2000 and Windows XP can read and write to FAT32 filesystems of any size, but the format program on these platforms can only create FAT32 filesystems up to 32GB. Thompson and Thompson (2003) write[2] that "Bizarrely, Microsoft states that this behavior is by design". Microsoft's knowledge base article 184006[3] indeed confirms the limitation, but gives no rationale or explanation. Peter Norton's opinion[4] is that "Microsoft has intentionally crippled the FAT32 file system

As per wikipedia.

What i will most likely do is create 2 FAT32 partitions and one ext3 partition.

---

