---
title: "windows dual-booting: use the same files for the 2 OS (in a diff partition)"
date: 2009-08-12
forum: Installation &amp; Upgrades
---

### Post by bautig on 2009-08-12
I´m new and do not know if this goes here.
I am looking forward to swap to ubuntu but in the meantime i´d wished to dual boot and i was wondering if it was possible to use the same files between the two OS (windows xp and ubuntu 8.10) being one partition per each OS and one for the files. or if it is possible in any other way.

thanks

---

### Post by oldfred on 2009-08-13
I found this in tips that helps explain partitioning and discusses using NTFS for a data partition. 
[http://ubuntuforums.org/showthread.php?t=1110403&highlight=partitioning](http://ubuntuforums.org/showthread.php?t=1110403&highlight=partitioning)

I set up a separate share data partition using FAT32 about 3 years ago. Fat32 is not now recommended as only 4GB files can be used and it is not as sturdy. I am now converting my shared data to a NTFS partition.

You cannot share programs only data such as photos, music, data files etc. I share my firefox and thunderbird data between XP and Ubuntu so I see the same emails and bookmarks in both systems.

---

### Post by Mark Phelps on 2009-08-14
> **bautig said:**
>  ... i was wondering if it was possible to use the same files between the two OS ...
thanks

You can share partitions by mounting each OS's partition in the other OS -- but I would recommend strongly AGAINST that.  You run the risk of file system corruption and then, you end up with a broken OS partition.  

Also, as pointed out, there's no way you can get either OS to run the applications installed in the other, so you can't share "programs".

A better approach is to have a shared partition.  Both MS Windows and Ubuntu can read/write NTFS partitions without problems. That way, if the partition gets corrupted, since it's only data, it won't prevent booting and will be a lot easier to repair.

---

### Post by bautig on 2009-08-14
thanks to both of you i find the other thread as well as your answers very uselfuel. tanhks

---

