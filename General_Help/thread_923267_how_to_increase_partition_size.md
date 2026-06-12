---
title: "how to increase partition size"
date: 2008-09-18
forum: General Help
---

### Post by Cool Surfer on 2008-09-18
My ubuntu is installed thro within windows on second partition of 10gb. I want to increase the partition size. How can I do it please.

---

### Post by Elfy on 2008-09-18
You can use lpvm to resize your wubi virtual disk, [http://lubi.sourceforge.net/lvpm.html](http://lubi.sourceforge.net/lvpm.html)

The page goes through resizing towards the end.

---

### Post by jonian_g on 2008-09-18
Boot with LiveCD and use Partition Editor (gparted) to resize the partitions.
Before doing this boot into windows and defragment the windows partition.

---

### Post by drs305 on 2008-09-18
I don't quite understand your partition setup but in general partitioning in linux is done with an application called gparted. 

Since you will be working with partitions that cannot be 'unmounted' while linux is running, you will need to run gparted from the livecd or from the systemrescuecd or gparted cd. 

I'd recommend burning a systemrescue CD, it can come in handy. Here is a link:

[http://www.sysresccd.org/Main_Page]("http://www.sysresccd.org/Main_Page")

You can run gparted from linux - you just won't be able to make any changes to your / or /home partitions. You can, however, start gparted and take a snapshot and post the results here as an attachment so we can see how your partitions are set up.

If you have to adjust your windows partition you might be best served by doing it from a windows app.

---

### Post by Cool Surfer on 2008-09-18
Right now ubuntu is using the capacity of partition 2 
(10gb - shown during ubuntu install as 8gb)

do I need to use partition magic or similar software in windows to first increase size of partition2?

---

### Post by drs305 on 2008-09-18
Just to be sure we are all talking about the same thing, is this a wubi install of ubuntu INSIDE of windows or a normal install of ubuntu on it's own partition?

---

### Post by Elfy on 2008-09-18
If you are using wubi then the partition afaik is a virtual one and you will need to use lpvm.

You can also use lpvm to migrate yir wubi to a normal partition if you so wish, at which point it would be on a normal partition.

---

### Post by Cool Surfer on 2008-09-18
It is 
[I]
Ubuntu - Linux for Human Beings!

This section is an introduction to Ubuntu. It explains the Ubuntu philosophy and roots, gives information about how to contribute to Ubuntu, and shows how to get help with Ubuntu.

Thank you for your interest in Ubuntu 8.04
                - the Hardy Heron - released in April 2008.
				[/I]

installed withing windows. I booted into my windows xp, and inserted the ubuntu cd > then started the installation.,

---

### Post by Elfy on 2008-09-18
use lpvm then - [http://lubi.sourceforge.net/lvpm.html](http://lubi.sourceforge.net/lvpm.html)

---

### Post by Cool Surfer on 2008-09-18
> **forestpixie said:**
> use lpvm then - [http://lubi.sourceforge.net/lvpm.html](http://lubi.sourceforge.net/lvpm.html)


Thanks... downloading ...

---

