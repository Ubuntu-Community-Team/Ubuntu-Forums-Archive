---
title: "Gparted doesn't recognize partitions"
date: 2009-03-31
forum: Installation &amp; Upgrades
---

### Post by drimades on 2009-03-31
Hello!

I have the Ubuntu 8.10 CD and I tried it in live mode. I have 3 partitions on my laptop and I was able to mount them from Ubuntu. The problem is that when I use Gparted to edit partitions or when I try to install Ubuntu it doesn't recognize such partitions but only the entire hard disk (as free). Any idea?

---

### Post by ronparent on 2009-03-31
Have you tried a manual install option when the partioner first shows in the install process? If not, that option would allow you to pick whare ubuntu is installed (also show the existing partitions).

---

### Post by drimades on 2009-03-31
I resolved using **cfdisk** instead of **gparted**. Maybe because there were some pending operations from a previous cfdisk session. Thanks!

---

### Post by Tsarevich on 2009-04-18
I have a very similar problem. Yes, I am also going to try cfdisk. Hope it works.

---

