---
title: "SSHD performance gain?"
date: 2015-04-17
forum: Hardware
---

### Post by snatchell on 2015-04-17
Dell 11-i3147
Intel Pentium N3530
8GB DDR3 RAM
Ubuntu 14.04.2
Kernel 4.0

Just recently purchased and installed a Western Digital WD10S12X Hybrid Drive. It has 1TB platter storage and 16GB NAND for caching handled by the disk firmware.
I have learned that these disks are supposed to give similar performance to an SSD. I wanted to ask others with SSHD experience: how quick does the boost come? Does it take awhile for the firmware to learn my file habits? And also, how long does the read/write limit last on a SSHD?

---

### Post by weatherman2 on 2015-04-17
It appears that this WD "hybrid" drive is different from others like Seagate's version of the same idea.  The Seagate version has a controller that performs the cache function in firmware, but the WD version appears to require a software driver to do so. There's a good chance there is no driver like this available for Linux.  There doesn't seem to be a driver for Mac OS X, either

So, it may be that you never see any performance boost from the 16GB SSD.  You're probably going to be stuck with the regular hard drive portion of the device.

[http://techreport.com/news/24783/wd-explains-hybrid-tech-behind-black-sshds](http://techreport.com/news/24783/wd-explains-hybrid-tech-behind-black-sshds)

---

### Post by snatchell on 2015-04-17
So seagate is linux-friendly when it comes to hybrid drives with ssd cache? or should i just get a dual drive that allows me to allocate the whole OS to SSD storage?

---

### Post by weatherman2 on 2015-04-17
In theory, the Seagate (and Toshiba) versions of a hybrid drive should be more Linux-friendly, with the controller doing the caching, but I haven't used any of them personally.  (I installed one of the Seagates in a laptop but it was used for Windows.)  I'd do some digging from people who have actually used them to see what experiences they have had.

I myself prefer the idea of a separate small SSD for just the OS.  16GB is enough for me for a decent Ubuntu installation.  I don't think you can do it with that WD drive you have, though - maybe but I doubt it.

---

### Post by snatchell on 2015-04-18
WD just made my blacklist.

I'll just go with a spare 240GB SSD I had as a fallback. I'll use the 1tb as an external until WD decides to play ball where compatibility is considered.

---

