---
title: "I want to manually decide what partitions to install to..."
date: 2009-01-12
forum: Installation &amp; Upgrades
---

### Post by MichaelSelf on 2009-01-12
I've partitioned my HD into three partitions for an install.  I have 70 gigs for Vista, 20 for Ubuntu and a 3rd formatted as FAT32 to use as a Swap between Vista and Ubuntu.  The drive for Ubuntu is currently formatted as FAT32 because EXT2 was not an option on the software I partitioned the drive with.  

Now, when I run the installation it automatically wants to install on the whole drive so I must do it manually.  When I go to install I don't know what to define as/home, etc.  

Help...what do I need to do?

---

### Post by mikewhatever on 2009-01-12
Choose manual partitioning and specify the partition you want. I am not sure, but I doubt fat32 is good for Ubuntu swap.

---

### Post by whoop on 2009-01-12
This is what I would do.
Launch liveCD (try ubuntu without installing)
Open terminal type:
```

sudo gparted

```
This starts a partitioning application. Completely remove the partition(s) you have reserved for ubuntu (apply the changes)
Reboot (to your livecd again)
Install Ubuntu (it will detect the free unpartitioned space)

Too make a long story short: You do not need to do pre-partitioning for ubuntu, it likes free unpartitioned space :-)

---

### Post by briandu on 2009-01-12
An Ubuntu/Linux swap is of swap format be carefull.

---

### Post by whoop on 2009-01-12
> **briandu said:**
> An Ubuntu/Linux swap is of swap format be carefull.

I think he made a misuse of the word swap. I think he means a partition that windows an linux can read and write to (could be wrong).
But linux swap is of type swap, and linux root and (optional) user should not be of type fat(32).

---

