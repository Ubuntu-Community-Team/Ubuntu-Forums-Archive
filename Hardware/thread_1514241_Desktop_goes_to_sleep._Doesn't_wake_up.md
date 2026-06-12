---
title: "Desktop goes to sleep. Doesn't wake up"
date: 2010-06-20
forum: Hardware
---

### Post by OSX@Linux on 2010-06-20
So, I've been using Ubuntu since 6.10 and I love it. Until now, I haven't been putting my computer to sleep, just leaving it running all the time. In an effort to be more power conscious, I got an 80+ energy efficient power supply from Antec. Realizing it would save even more power if I put my computer to sleep when I'm not using it, I tried to.

Every time the computer goes to sleep, it won't wake back up. The CPU fan and hard disks start to spin up, but I see nothing on my monitor. I have VNC set up, but it won't connect after waking up. I'm forced to restart my computer if it goes to sleep, so I disabled it. 

I would really like to have sleep on my computer. Using 10.04.

Hardware

MSI P6NGM-FD Motherboard
Antec Earthwatts 380w Power Supply
Zotec Nvidia GT 220 Graphics Card
Pentium 4 Dual Core 1.6 Ghz

---

### Post by OSX@Linux on 2010-06-20
I just tried downgrading GRUB, as some posts on other threads suggested. Still, no sleep and wake up.

---

### Post by lanzcc on 2010-10-04
Yes, 

My IBM-made Pentium 4 cluster machines go to sleep, and every time they do, they disable the clustering software, requiring hard reboots of every node.

Any suggestions? Please, I've tried everything. The manufacturers don't even have billable support any more for pentium 4 machines

Lanzcc

---

### Post by kristianheath on 2011-04-18
Hi

I have a similar issue, although not with Ubuntu. I have 2 separate PCs both powered by Antec Earthwatts 380s. Despite being configured to do so, neither of these will wake on lan. I've configured several other PCs to allow W.O.L. so I have reasonable confidence that I'm doing the right thing.

I guess the power supply must be turning off significant parts of the underlying system which prevents WOL working. I notice that when the machines are sleeping that the link light on the network cards turns off - so I suppose this is a good sign that the network cards are being powered whilst in this low power state.

I didn't mention above but I'm using Windows, rather than Ubuntu - however, I've been suffering serious frustration on trying to get this to work and only recently concluded that it is something to do with the power supply.

Cheers,
Kris.

---

