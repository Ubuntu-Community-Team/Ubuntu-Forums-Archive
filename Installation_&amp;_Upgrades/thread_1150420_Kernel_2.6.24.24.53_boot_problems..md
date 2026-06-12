---
title: "Kernel 2.6.24.24.53 boot problems."
date: 2009-05-06
forum: Installation &amp; Upgrades
---

### Post by knowone123 on 2009-05-06
Hi. Has anyone had problems with kernel 2.6.24.24.53. My update last night included this and succeeded in preventing me from accessing the net via wireless. Removing the usb dongle, restarting the machine worked to get me to the desktop, then attaching the dongle an re-enabling the network, worked ok. I cant have this as the machine is used by someone who just wants something as easy as windows, and no hassles.
Looking at the  messages from my machine, apparently my dongle does not respond to system network requests quickly enough on bootup and times out, freezing the system, requiring a restart. After some sweating I have reverted to kernel 2.6.24.23, which works fine. Possibly a change of process sequence in the kernel has caused this. 
Now I think about it, my recent foray into upgrading from 8.04 to 9.04 did not go well, possibly for the same reason, as the network dongle was not seen. At all. I may try this out again later.
Anyone else have the same types of problem?

Regards all.
K.
Ubuntu 8.04.

---

### Post by gomphus on 2009-05-06
Hi there, 

I have also problems with my wireless lan after upgrading the kernel from 2.6.24.23 to 2.6.24.24 in Ubuntu 8.04-2. Everything worked fine with the old one (which I am currently using). I am using a TP-Link TL-WN321G USB dongle. The Network manager I use is WICD. After the kernel upgrade the USB dongle is not working anymore :( Any ideas?

       ... thanks in advance 

          gomphus

---

