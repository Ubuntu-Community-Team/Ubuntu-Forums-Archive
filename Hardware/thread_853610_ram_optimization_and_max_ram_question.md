---
title: "ram optimization and max ram question"
date: 2008-07-08
forum: Hardware
---

### Post by rockstar on 2008-07-08
I have a question about how linux utilizes ram on a system.  To my understanding Windows XP only supports about 2gigs of Ram.  Also, programs are written to support certain amounts of Ram.  I know encoders and video editors are written to support the most.

How much ram has Ubuntu been written to accept? What about average programs, How much ram do they support?

I only have 512 mb of ram and I want to upgrade, I know the limit of my motherboard, but what would be a good suggestion for Linux? I wouldn't want to buy more than I need or more than the computer would utilize.

---

### Post by sdennie on 2008-07-08
For 64bit systems, Ubuntu should be able to support around 16 exabytes and I believe applications can use an arbitrary amount of RAM.  For 32bit systems, around 3.5G unless you use PAE, in which case it's around 64G.  Also, in 32bit I believe apps are limited to either 2G or 4G per application.

Depending on your needs, 1G is very good on Ubuntu and most users may not notice much of a difference between 1G and 2G.

---

### Post by stchman on 2008-07-08
> **rockstar said:**
> I have a question about how linux utilizes ram on a system.  To my understanding Windows XP only supports about 2gigs of Ram.  Also, programs are written to support certain amounts of Ram.  I know encoders and video editors are written to support the most.

How much ram has Ubuntu been written to accept? What about average programs, How much ram do they support?

I only have 512 mb of ram and I want to upgrade, I know the limit of my motherboard, but what would be a good suggestion for Linux? I wouldn't want to buy more than I need or more than the computer would utilize.

Windows XP 32 bit can support 4GB RAM maximum.  The OS has overhead so it turns out that about 3.5GB is seen by the OS.  Windows XP 64 and Ubuntu 64 can support 2^64 bytes of RAM.

For 32 bit Ubuntu 2GB will be way more then you ever need.  For 64 bit go with 4GB.

---

### Post by Alejandro Nova on 2008-12-24
I have 2.5 gigs of memory on this lappy (I bought them for Vista) and, although the Linux kernel does a good job caching all, the catch is: I'm always having 300-400 MB free (and the real memory usage is about 510 MB with all up). Do you know about a way of "bloating" Ubuntu a little (say, for instance, a RAM disk for my temporal files, or a way to load X and some programs directly from RAM)

---

### Post by ymo on 2008-12-24
> **stchman said:**
> Windows XP 64 and Ubuntu 64 can support 2^64 bytes of RAM.
Just yesterday I was reading a thread in the Linux-Kernel mailing list and came across [http://lkml.indiana.edu/hypermail/linux/kernel/0812.2/00292.html](http://lkml.indiana.edu/hypermail/linux/kernel/0812.2/00292.html) where it was explained that the x86-64 Linux kernel currently only supports up to 16TB (or 2^44 bytes).

According to Wikipedia ([http://en.wikipedia.org/wiki/Windows_XP_Professional#Advantages](http://en.wikipedia.org/wiki/Windows_XP_Professional#Advantages)), "Windows XP x64 is limited to 128 GB of physical memory and 8 terabytes of virtual memory per process."

---

