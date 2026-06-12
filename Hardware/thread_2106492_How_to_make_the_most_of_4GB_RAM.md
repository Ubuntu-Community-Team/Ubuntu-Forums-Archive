---
title: "How to make the most of 4GB RAM?"
date: 2013-01-19
forum: Hardware
---

### Post by blackbird34 on 2013-01-19
Hi
I've just upgraded my RAM from 2 to 4 GB and I'd like to make the most of it to take some of the load off the not-so-good CPU in my laptop (Intel Celeron 900, single-core 2GHz). What are the best things to load into RAM for fast access? Or does Ubuntu do all this very well by default?

---

### Post by sanderj on 2013-01-19
First check that your 4GB is seen by Linux:

```
free -m

```
It should be above 3400 ...

Here's my 4GB system:

```
sander@R540:~$ free -m
             total       used       free     shared    buffers     cached
Mem:          3753       3278        475          0         99        966
-/+ buffers/cache:       2211       1541
Swap:         4766        308       4458
sander@R540:~$

```

---

### Post by blackbird34 on 2013-01-19
Yeah it shows up, I did a memtest on boot, and the free command says I have 3858 MB of RAM. Besides, the laptop is way faster, there's no doubt it works.

---

### Post by sanderj on 2013-01-19
> **blackbird34 said:**
> Yeah it shows up, I did a memtest on boot, and the free command says I have 3858 MB of RAM. Besides, the laptop is way faster, there's no doubt it works.

So that's good. That's all you can do, I would say. Linux will take care of the rest.

---

### Post by jerome1232 on 2013-01-19
Yeah, ram can't take any load off of a cpu since it has no processing power. It's just ram, it stores the instructions and data for the processor to work on.

---

### Post by KdotJ on 2013-01-19
I'd say that's pretty much it too (unless someone else knows anything). The RAM is not particularly going to take load off of the CPU per se as they do different jobs.

---

### Post by ahallubuntu on 2013-01-19
Exactly - RAM doesn't help at all if you aren't running out of it.  It lets you open more windows without "swapping" to disk.  The first few minutes after booting shouldn't be any different, at least in Ubuntu, until you open a lot of windows.  Upgrading from 2GB to 4GB would help a Windows machine a lot more than a Linux machine, typically.

It's not always that hard to upgrade a laptop CPU.  Depends on the make/model. Some laptop CPUs are very difficult to get to and others are very easy to get to.  My Dell Inspiron 1545 CPU is extremely easy to upgrade - easier than upgrading a desktop.  You can get to it from the bottom of the laptop.  Only about ten screws (total including the bottom panel) to remove it.

---

### Post by KdotJ on 2013-01-19
I'd say that upgrading the RAM is enough for your average person to feel like they have a new machine - at least for the most part.

---

### Post by jerome1232 on 2013-01-19
+1, "unused" ram get's used as a file cache, speeding things up. It just doesn't directly take any load off the cpu, (indirectly maybe, since you would be swapping less, and swapping is an additional load on the cpu) for example a 1ghz single core with 12 GB's of ram will still chug doing cpu intensive tasks, just as the most modern i7 on 1GB of ram will chug doing something memory intensive, like photo editing.

It also allows applications to allocate more space for cache etc... Generally more ram is the cheapest, most effective upgrade you can do.

---

### Post by hydn79 on 2013-01-19
There's one fast way to have a MAJOR impact on RAM usage:
1) Choose a lighter distro. (Eg. [lubuntu.net]("http://lubuntu.net") or [http://xubuntu.org/](http://xubuntu.org/)) Of course, there's Arch, Gentoo & Slackware but those are not the types of distros in question. :)

---

### Post by tgalati4 on 2013-01-19
There used to be some speedup running Firefox cache in a temporary RAM disk, but I don't think that applies anymore with the latest improvements in Firefox.  These improvements were motivated by Google's Chrome performance.  

If your BIOS allows manual tweaking of the RAM timing, you can probably get another 10% in RAM read/write speed.  Use memtest to compare timing.

---

### Post by tartalo on 2013-01-19
Linux already caches things to RAM, but maybe you can use a ramdisk for something that uses the hard drive heavily, here's one example:

[http://www.cyberciti.biz/faq/howto-create-linux-ram-disk-filesystem/](http://www.cyberciti.biz/faq/howto-create-linux-ram-disk-filesystem/)

---

### Post by blackbird34 on 2013-01-20
Thanks everyone.

---

