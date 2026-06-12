---
title: "memtest86+ but with running system"
date: 2013-10-30
forum: Hardware
---

### Post by geohei on 2013-10-30
Hi.

I got some new DDR2 RAM installed on my hardware running Ubuntu server 12.04.

Since I can hardly afford to start memtest86+ from Grub (which requires Ubuntu system to be down), I'm presently looking how I can check my memory while the system is up and running (same tests more or less than memtest86+).

Can I do that, or is there no way around to shut down the system for RAM tests?

Thanks,

---

### Post by tgalati4 on 2013-10-31
Well, by its very nature, RAM tests are destructive.  Memtest writes different patterns to blocks of RAM, so that RAM is not available to the system.  I don't know of any RAM test that runs with *init* operating.  

If you can afford to run a server for critical services with RAM that you installed (but did not burn in for 24 hours with memtest) what is the issue with bringing the server down?

If your system runs for several weeks (uptime of several months) then you can assume that the RAM is good.  If it crashes, then it could be the RAM or it could be something else.

Generally you should test the RAM right after installing it for at least 24 hours.  I like to run 30 complete cycles of memtest, which represents a large data population.  This is a better predictor for long-term use of the RAM.  If you don't have the time, run it for a couple of memtest cycles and hope that it is OK.

If this is for Obamacare servers, then there are larger problems that need solving first.

---

### Post by geohei on 2013-10-31
I could imagine that memory tests could theoretically be possible by testing the free memory, then mapping the operating system reserved memory to this already tested memory, then testing the remaining part of the memory. But anyway ... let's skip this part due apparent lack of software.

After reading your reply, I'll get the server down and run memtest86+ a couple of passes.

I don't like to test it by trial-and-error in actual operation just by saying that the RAM must be ok if it ran during weeks flawlessly. First, you can't really say if an error occurred because this one might not be obvious and second, bad luck in respect of error occurrence could damage data on HDDs!

I'll get the system down and use memtest86+!

Thanks!

---

