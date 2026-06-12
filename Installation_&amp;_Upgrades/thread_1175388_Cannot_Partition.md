---
title: "Cannot Partition"
date: 2009-06-01
forum: Installation &amp; Upgrades
---

### Post by Taboo on 2009-06-01
I'm trying to install Jaunty Jackolope on my machine, but I'm having a few problems.

System Info:
I'm running a latest gen iMac, with a 500GB internal HD.  I'm dual booting OS10.5 with Vista.  I also have a 500GB external HD.  I have a 30-ishGB partition for Vista on the internal HD, and use the external HD for all my Window$ data.  The rest of the internal HD is devoted to OSX.

I want to put another partition into my internal HD, splitting my OSX partition in half, but the "New" button is greyed out, heres a pic:
[IMG]http://img194.imageshack.us/img194/263/gparted.png[/IMG]

My external HD is dev/sdb, and isn't in the pic

I can partition the 128.00MB unallocted partition (which I didn't even know I had) so I figure it must be something to do with having the maximum number of partitions.  When I tryed partitioning from the installer, it came up with a message that said something to do with some partitions being mounted, or active and do I want to try and unmount/deactiveate them as I will not be able to resize or format them, but I may be able to write to an already created partition.  I've also tried to partition MacintoshHD in OS10.5, but it never stops "modifying partition mapping/data/something else"  I haven't tried partitioning in Vista 'cos I really don't trust it not to format anything :-(

Does anybody know what the problem is? Do I need to do something strange because I'm using a Mac, or am I just trying to install too many OS's for my own good?

Please help :-(

Thanks
Taboo

---

### Post by lake54 on 2009-06-01
You can only have a maximum of 4 primary/logical partitions, but you can have more (unlimited?) extended partitions, providing you have the space.

I think from what I understand you need to resize a partition to create more free space, then create a new partition in the unallocated space which is much greater.

It's not the most intuitive piece of software for someone who's never used it before (like me) so it just takes a bit of getting used to.

Of course, saying all of that, I'm probably wrong :-)

Hope that helped, and if I was wrong, I apologise - a more experienced person will be along shortly :-)

James

---

### Post by Partyboi2 on 2009-06-01
> **Taboo said:**
> 

Does anybody know what the problem is? Do I need to do something strange because I'm using a Mac, or am I just trying to install too many OS's for my own good?

Please help :-(

Thanks
Taboo
Hi, you will need to resize your hfs partition to make room for another partition as already mentioned. Once you have resized your hfs partition, with the newly unallocated space create a extended partition, then you can have as many as you like logical partitions, you can only have 4 primary partitions and by creating a extended partition you are able to get around the 4 partition limit.

---

### Post by Taboo on 2009-06-01
Thanks for the help, has cleared it up :-)

---

