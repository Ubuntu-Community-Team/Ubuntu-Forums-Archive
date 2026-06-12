---
title: "Hibernate on Toshiba A85"
date: 2007-08-15
forum: Hardware &amp; Laptops
---

### Post by Optimosis on 2007-08-15
So when I installed Feisty Fawn about a month ago, I got hibernate to work but not suspend.  (It was sorta cool having both Ubuntu and Windows hibernated simultaneously.)  While I have yet to figure out how to get the computer to actually suspend at all, I've noticed an annoying thing with hibernate.  Most people have reported not being able to recover from hibernate, but sometimes, my screen gets frozen at 

suspend: Snapshotting system

and I can tell that my processor's getting hung on some sort of infinite loop when I hear the fan suddenly go on high speed after about a minute.

Some people have told me that my swap partition might not have enough room to accommodate memory, but that seems awfully unlikely.  During the times hibernate works, I see something like

Memory: 125934589 KB
Free Swap: 895763496 KB
(these are made up numbers, but generally around the range, with Memory much less than Free Swap)

Plus, I have it configured so that the image is compressed when saved onto the disk.  Recently, I've been checking System Monitor before I hibernate, and each time there is at least 4 times as much free swap as memory, even when hibernate hangs.

However, I've noticed from System Monitor that my used swap rarely decreases.  In fact, there is a general upward trend in used swap vs. sessions between successive hibernates.  Even now, for example, when I just closed Evince, Tomboy notes, Gaim, and file browser, only leaving open Firefox and System Monitor, my used swap only decreased from 135.0 MB to 123.7MB.  I don't know if this is some sort of memory leak that's contributing to my hibernate problem.

Anyways, here are some of my specs:
Total Memory: 439.4 MB
Total Swap: 996.2 MB
Processor: Celeron M 1.4 GHz
Graphics: ATI Mobility Radeon 9200 IGP

Hope my problem can be diagnosed!

Thanks,
Optimosis

---

### Post by Optimosis on 2007-08-15
Oh, and I'm just wondering, what sorts of suspend/hibernate problems occur on the Thinkpad T61?  I'm getting one soon.

---

