---
title: "Installing a new harddrive and want to expand an old partition onto this one"
date: 2010-11-05
forum: Hardware
---

### Post by Dingbats on 2010-11-05
I'd search for this if I knew what to search for.

I'm on a Mac Pro, that has one 250 GB harddrive on it that I've split into two equal partitions, one for OS X and one for Ubuntu.  I'm going to install another drive, 500 GB, that I plan to split in two as well.  However, I want one of those partitions to act as if it's the same partition as the one I already have all my Ubuntu stuff on.  Is that possible?  How?

---

### Post by Dingbats on 2010-11-07
bumpity bomp...

---

### Post by sikander3786 on 2010-11-07
Simply copy/paste the whole partition from gparted will work. Use gparted from a Live CD.

Clonezilla is another choice.

[http://clonezilla.org](http://clonezilla.org)

You can also use dd. For more information,

```
man dd
```

---

### Post by Dingbats on 2010-11-08
> **sikander3786 said:**
> Simply copy/paste the whole partition from gparted will work. Use gparted from a Live CD.

Clonezilla is another choice.

[http://clonezilla.org](http://clonezilla.org)

You can also use dd. For more information,

```
man dd
```
I think you misunderstand me.  I don't want to copy any data.  The data that's on my current Ubuntu partition stays there.  I want to make it so that the new partition on the new harddrive "counts as" the same partition as the one I already have.  So it's just like I'm adding 250 empty gigabytes to the partition that's already there.

---

### Post by IcarusR on 2010-11-08
Format the 'new empty' drive, then mount it from within your ubuntu install.

---

### Post by sikander3786 on 2010-11-08
> So it's just like I'm adding 250 empty gigabytes to the partition that's already there.

So if I understand you correct this time :-) I think you want to make 2 physical hard drives act like a single partition?

You'll need to do some work on that. You can start here.

[http://en.wikipedia.org/wiki/Standard_RAID_levels#RAID_0](http://en.wikipedia.org/wiki/Standard_RAID_levels#RAID_0)

[http://en.wikipedia.org/wiki/Logical_Volume_Manager_%28Linux%29](http://en.wikipedia.org/wiki/Logical_Volume_Manager_%28Linux%29)

[https://help.ubuntu.com/community/Installation/RAID1%2BLVM](https://help.ubuntu.com/community/Installation/RAID1%2BLVM)

You can definitely setup a hardware or a software RAID. But I am not sure if you can expand your existing Ubuntu partition to take up that space. I think you'll need to re-install. Wait for some other informative replies.

If you just want to mount it, you can do it simply as **IcarusR **mentioned.

---

### Post by oldfred on 2010-11-08
I do not use this as I just mount and link folders into my root partition.

lvm info:
[http://ubuntuforums.org/showthread.php?t=141900](http://ubuntuforums.org/showthread.php?t=141900)
Advantages/Disadvantages
[http://ubuntuforums.org/showthread.php?t=1586328](http://ubuntuforums.org/showthread.php?t=1586328)

---

### Post by Dingbats on 2010-11-09
Thanks a lot guys.  It seems like a lot more of a hassle than what I'd be willing to do.  I think I'll just make a new partition out of it and organize it some other way.

This really should be simpler.

---

