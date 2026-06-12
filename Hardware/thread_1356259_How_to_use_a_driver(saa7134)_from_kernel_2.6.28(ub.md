---
title: "How to use a driver(saa7134) from kernel 2.6.28(ubuntu 9.04) in 2.6.31(ubuntu 9.10)"
date: 2009-12-15
forum: Hardware
---

### Post by bp0 on 2009-12-15
Some change in the 2.6.31 kernel driver for saa7134-based TV capture cards has made it impossible to change channels after upgrading to ubuntu 9.10. Of course this makes the card pretty useless unless I want to watch only channel 2. I want to use the old, working, driver with the new kernel. I've reported a bug, but past experiences have left me with very little confidence in that.

How can I compile and install the old saa7134 driver separately from the kernel package and inhibit the one in the package from being used? 
How can I do that without everything getting screwed up when Ubuntu decides to install a new kernel package?
Why aren't individual drivers maintained independently from the kernel in linux? (like the nvidia drivers are for example)

---

