---
title: "partition order ok?"
date: 2009-07-24
forum: Installation &amp; Upgrades
---

### Post by linuca on 2009-07-24
Hi everybody! I just installed my ubuntu, with three partitions:

/dev/sda1 is swap
/dev/sda3 is /home
/dev/sda5 is /

A friend just told me that the performance is better if the / partition is in second place and the /home partition is third. I already installed the machine, does it worth it to install it all over again, just to change the order of the /home and / partitions? Or is it ok the way I did it?

Thanks.

---

### Post by philcamlin on 2009-07-24
the way you did it is ok :D

---

### Post by bacil on 2009-07-24
it used to make sense on older systems to put swap on firs set of blocks since when system was swaping heads on disks didn have to do much movemets. But these days are long gone. your setup is OK :-)

---

### Post by linuca on 2009-07-24
I knew it!

Thank you guys!

---

### Post by Bucky Ball on 2009-07-24
It is fastest if the OS (/) is in sda1. Why? It is the fastest part of the drive. The /swap should always go last as in modern machines it is barely touched (once you get to 2Gb+ RAM):

/
/home
/swap

Not quite sure what people are saying, here. Think about it. The way it is set up, the OS partition (which is probably about 10-20Gb) could be 100-750Gb away from the fastest part of the drive.

It does make a difference as all your programs are running from the slowest part of the drive (sda1 is on the outer edge, your current partition is closest to the middle).

There is a good reason A/V is recorded on to the first part of a different drive, not just partition. This is just a smaller version of that.

---

### Post by raymondh on 2009-07-24
> **linuca said:**
> I knew it!

Thank you guys!

And should you get interested in the WHY's of it (swap and where should you put it, etc)

[http://www.ranish.com/part/primer.htm](http://www.ranish.com/part/primer.htm)
[http://www.pcguide.com/ref/hdd/geom/tracksZBR-c.html](http://www.pcguide.com/ref/hdd/geom/tracksZBR-c.html)
[http://www.tldp.org/HOWTO/Multi-Disk-HOWTO.html#toc3](http://www.tldp.org/HOWTO/Multi-Disk-HOWTO.html#toc3)

---

### Post by linuca on 2009-07-24
Not sure what to believe anymore...

When this kind of issues comes up, I always get complete different answers...

I'm a web developer, I'll use php5, apache, mysql. Problably a VM with window$ XP and Vista. 

Regards.

---

### Post by merlinus on 2009-07-24
With the speed of modern processors, to say nothing of core duo and quad, and huge amounts of ram, IMFFHO this is an issue that is hardly relevant.

Better to spend your time on exploring and learning linux.  Look for the forest, and don't get lost in all the little trees.

YMMV, as always!

---

