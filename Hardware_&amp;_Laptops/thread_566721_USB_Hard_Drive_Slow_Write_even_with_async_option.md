---
title: "USB Hard Drive Slow Write even with async option"
date: 2007-10-03
forum: Hardware &amp; Laptops
---

### Post by ComradeVVA on 2007-10-03
I've been having a problem with copying files to my removable USB hard drive. I've read a lot about the problem and the #1 thing people recommend is mounting with the async option. That did not work for me and seems to not have worked for [[COLOR="RoyalBlue"]_others_[/COLOR]]("http://ubuntuforums.org/showthread.php?t=436622").

People also posted a couple of [_[COLOR="RoyalBlue"]other creative ways[/COLOR]_]("http://ubuntuforums.org/search.php?searchid=28209901") to speed up writing speed, but none of them have worked in my case either.

As a newbie, I'm not sure what command outputs to put for my system, but I can tell you that it's nothing special. Feel free to tell me to post other output to help you solve this. This seems to be a pretty common problem and I have not seen a clear solution to it.
[HTML]
root@VVAHOME:/# fdisk -l

Disk /dev/sda: 80.0 GB, 80054059008 bytes
255 heads, 63 sectors/track, 9732 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        9483    76172166   83  Linux
/dev/sda2            9484        9732     2000092+  82  Linux swap / Solaris

Disk /dev/sdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       14593   117218241   83  Linux

Disk /dev/sdc: 750.1 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       91201   732572001    c  W95 FAT32 (LBA)
[/HTML]

---

### Post by ComradeVVA on 2007-10-24
I've waited a little bit since posting, and now I'm not sure what to do. Just so I know there are people reading this and really not knowing the answer, could someone tell me the answers to the following questions:

How long does the average Ubuntu question take to be answered?
Is the above post an average question or is it something that will take time?
What should I do next if I want to solve the problem? Should I bug report? Where would I go for that? Or, should I wait some more for someone to answer the post?

Thanks again to all those who read the post. I will get this solved, sooner or later, because it's been a real pain. Imagine watching the transfer "time remaining" keep STEADILY increasing as the download progresses. I dunno why, but you just get the worst feeling :neutral:.

---

