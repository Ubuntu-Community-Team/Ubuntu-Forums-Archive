---
title: "Core 2 Duo / Quad - Maximized Performance"
date: 2007-09-28
forum: Hardware &amp; Laptops
---

### Post by verevi on 2007-09-28
I saw a few posts related, but none seemed to answer this question--Which install disk should I use for the Core 2 Duo (and is the answer the same for a Core 2 Quad)??

If I use the 32bit version, will I still get use of the multiple cores?  I'd prefer to use 64-bit, but from what I've read, not everything works with 64bit so its limiting.

Any other tips to maximize performance without getting my hands too dirty?

Would it be better to get a faster duo vs. a slower quad (because few things actually utilize more than 2 cores)?

Sorry if my questions seem dense, I'm learning this stuff.

Thanks for the help!

---

### Post by tgm4883 on 2007-09-28
Stick 64-bit on there.  You can use the alternate or Live Disk.  Most of the negativity toward 64-bit comes from people that don't run it, or haven't run it since early on.  I run it on all my capable systems (I have 1 old fileserver that has a P3 in it) and it runs awesome.  I use to run feisty that was pretty much a breeze with 64-bit but now I am running Gutsy on all my systems and it's even easier than feisty.  Most complaints come from flash, and it's seriously a breeze to install in feisty and installs the same way in gutsy (for both 32 and 64 bit systems)

Things aren't specifically written for 2 cores (well some probably are).  They are written for single core or multi core.  It really depends on what you want to use it for.  For instance, if you tend to use lots of VM's , I'd go quad core (actually, I'd go dual core but get a quad core capable motherboard as I think quad cores are a little expensive and I can always upgrade later)

---

### Post by PmDematagoda on 2007-09-28
Don't worry about the 32 bit compatibility with a 64 bit processor. Because 32 bit OSes are also well supported with 64 bit processors and mainboards, it's only 64 bit Oses that are not supported well on 32 bit processors and mainboards. I have an EM64T HT P4 processor and I use Ubuntu 32 bit and XP 32 bit on it with no problems.

But about Dual-Core or Quad-Core, I think tgm4883 has explained it very well and I would recommend the same thing.:)

A good way to increase performance is by increasing RAM, in your case the 32 bit OSes only support a maximum of about 3.2Gb of RAM, but if you were to get a 64 bit one, the the maximum supported is about 4Tb's of RAM.

Another way is by not using more than 85% of your disk space, because if you do then fragmentation can kick in, even in an ext3/2 file system which is popular for virtually no fragmentation if you have enough free disk space.

One good, but risky method is by cutting down your processes, remove the processes you don't need at startup and during your sessions and you can use those extra resources for your own work. But do this carefully because removing certain processes may render your OS inoperable.

---

