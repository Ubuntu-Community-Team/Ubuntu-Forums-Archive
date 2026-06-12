---
title: "about hard drive noise"
date: 2007-03-10
forum: Hardware &amp; Laptops
---

### Post by lixx on 2007-03-10
im really concerned about the annoying clicks i hear when im using ubuntu. Btw, im using an HP nx6120 and a seagate-type hard drive. When i run windows, i don't hear any clicks. I tried tweaking hdparm, setting the acoustic management to quiet, and then re-enabling laptop-mode. Nothing works. So far, I don't use ubuntu anymore since it might do something really unexpected w/ my hard drive. Currently im using DSL booted from a flash drive, and won't return to ubuntu unless the annoying clicks are gone. Any help guys???

---

### Post by tgalati4 on 2007-03-10
Welcome to the community.

I am guessing that it is the file system doing its normal housekeeping.

Some things to reduce harddrive usage:

Maximize your ram:  256 MB is OK, 512 MB is better, 1 GB is sweet.  This reduces the swap file usage and allows you to have more applications run in ram before swapping.

Using DSL from a thumbdrive is also a good solution, especially if it contains the applications that you want to use.  It runs a little faster than Ubuntu because the kernel has been slimmed down and the applications have been trimmed as well.

What you lose is a decent package management system, so you can't experiment with the latest applications that are out there.  DSL applications tend to be older, stable applications that people have ported into the DSL universe.

Hard drives are cheap, don't worry about the noise.  Perhaps when you set up the Ubuntu partition, you didn't get a continguous block of disk space?

Get a cheap USB drive enclosure, get a cheap notebook drive, put Ubuntu on that.  When you get tired of Windows, or if the Windows drive gets balled up--as it usually does, you can swap drives and you will have a working, bootable system, with all of your preferences ready to go.

Another option is to get a CF card reader and an 8 or 16 GB CF card (prices are coming down on those as well, 4 GB are around $50 on sale) and put Ubuntu on it.  

That way you have a silent Ubuntu install, although the speed may not be great because cheap CF cards have slow memory controllers.  Expensive, high-speed cards that photographers use may be better, but then the PCMCIA bus limits the speed to 33 mbits/sec burst.

Good luck.

---

### Post by lhtown on 2007-03-10
It sounds like possibly your hard drive is going bad to me. Another possibility might be your CD rom or one of your fans.

This may seem like a dumb question, but do you have more than one hard drive (one of which Linux accesses that Windows doesn't?

I would suggest that you verify that the noise is from the hard drive. Perhaps there is a fan that runs with Linux that may not normally run under Windows due to different types of power management. Sometimes fans can make annoying clicking noises.

---

### Post by treesurf on 2007-03-10
If your hard drive is making that clicking noise every 5-10 seconds or so than the instructions in this thread may solve your problem.  It worked for me, at least.

[http://www.ubuntuforums.org/showthread.php?t=331418&page=3](http://www.ubuntuforums.org/showthread.php?t=331418&page=3)

---

