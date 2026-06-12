---
title: "Re-Partitioning Existing Installation(s)?"
date: 2008-04-01
forum: Hardware &amp; Laptops
---

### Post by dbsoundman on 2008-04-01
I initially partitioned my laptop when I wanted an Ubuntu dual boot in such a way that I have too much swap space, too much windows partition space, and not enough actual file saving space (i.e. /home). I would like to, ideally, re-partition existing partitions basically so that they make more sense. Can I do this safely or do I have to back everything up and start over? Actually, I SHOULD turn the existing XP installation to a virtual machine, but even then I think I would leave it on it's own drive, as I'm sure it's pretty large. Anyway, any suggestions?

Thanks,
Dan

---

### Post by chewearn on 2008-04-02
First thing, you should back-up everything anyway.

Then, use whatever Windows partition resize tool you know or like, to take care of Windows side.  I personally prefer Partition Magic.

Then, to resize linux partitions, I suggest GParted LiveCD.
[http://gparted-livecd.tuxfamily.org/](http://gparted-livecd.tuxfamily.org/)

You might need to edit fstab later on, if any of the partition UUID changes.

---

### Post by dbsoundman on 2008-04-02
So I should use a different partition utility for each OS's drive space? I had never heard of that before, but I suppose it makes sense. Doing the backup will be interesting too as I am running out of backup space and I hate writing CDs or DVDs for backup purposes, but I will probably do it, maybe after I install 7.10 on the desktop...

-Dan

---

### Post by chewearn on 2008-04-02
It is possible to use GParted LiveCD to resize Windows NTFS as well, so that you don't need a Windows based partition tool.

But I experienced ntfs-3g write problem before, causing file corruption.  Since then, I am hesitant to recommend Linux NTFS tools.  With MS closed proprietary system, you never know what is hidden.

---

