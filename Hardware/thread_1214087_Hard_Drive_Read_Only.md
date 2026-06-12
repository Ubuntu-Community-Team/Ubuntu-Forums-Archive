---
title: "Hard Drive Read Only"
date: 2009-07-15
forum: Hardware
---

### Post by samuel.stidham314 on 2009-07-15
I think I posted this topic in the wrong forum (Installation & Upgrades), so I thought I needed to repost it here.  Here's a quick synopsis of my problem:
 
I already know how many hard drives are connected to my computer (a single hard drive) and how many partitions and what format each partition is on my hard drive (a single ntfs partition with XP SP3).  Here's my problem.  Not too long ago I had a problem with XP.  It crashed.  The wonderful "Non system disk" message came on my screen.
 
So, I decided to put ubuntu on my computer ... redo all the partitions and whatever. All those of you who have ever used a floppy disk knows that the floppy can be put in a read only condition where nothing in any form or fashion can be written to this floppy disk.
 
Well, my hard drive (somehow) has had its permissions changed to read only.  I have tried various partition managers including those on Kubuntu live sessions, Ubuntu live sessions, Partition Magic, and have even booted using another hard drive and using this hard drive as a slave and nothing is working to change the hard drive from a read only position to a read and write position.
 
I don't need to check to see what partitions are on there.  As I have already stated, I know what partition is on the hard drive.  I have went into the hard drive and tried to change it, as I have said, with various partition programs and none are working.
 
In most versions of linux that I have tried, the hard drive doesn't even show up .... in FDISK it shows up, but it states "hidden" as the status and none of the partitions can be changed.
 
What do I do so I can run linux on my computer?
 
Thanks in advance

---

### Post by munky99999 on 2009-07-15
Sounds like a bad hard drive.

It will take several hours.

Do this off a livecd. Also be sure to get this code exactly right because one of the options missing or wrong could mean an erased disc.

```

badblocks -snv /dev/sdb
```

Or whatever position the hard drive is at. It will non-destructively discover bad sectors.

If you get Fedora11 livecd. There are hard drive diagnostic tools that wouldnt likely pop up right away. It uses the SMART diagnostics; much faster but doesnt tell you much.


Also if it's a bad hard drive. The drive is pretty much done at this point.

---

### Post by samuel.stidham314 on 2009-07-16
Okay, I've done what you said, but the terminal says 

"Permission denied while trying to determine device size"

I have used various techniques presented by various websites concerning this problem ... there's nothing wrong with the Hard Drive ... it's just denying permission to the partitions.  I thought that perhaps it had to do with NTFS ..... so I looked into NTFS 3G ... still not much luck ... hopefully I will overcome this problem.

I'm trying to install the operating system again.  Lets hope it works.

---

### Post by munky99999 on 2009-07-16
sorry for lateneess. I tried to get on earlier today but forums were broked.

> "Permission denied while trying to determine device size"

ya. sudo i guess is necessary infront of the command. then it should run.

---

