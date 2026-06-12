---
title: "Silicon Image 3114 Adapter"
date: 2009-12-07
forum: Hardware
---

### Post by Deathcon_1 on 2009-12-07
I have 2x Silicon Image 3114 PCI adapters that are critical to my server.  I've been running my server for several months now and only recently gotten to the point of needing to start filling the drives on the cards.  I can read data off the drives (tested by switching drives from the motherboard's onboard controller to one of the SIL controllers.) but every time data is written to the drive the controller resets the ATA channel for about 6 hours.  

I converted the server from Gentoo to Ubuntu, I know these cards work in Gentoo and I also know from working with Gentoo that the kernel has SIL3114 drivers built in.  In fact, that Gentoo server was running explicitly off of the same cards.  

Is it possible to get the SIL3114 drivers put into the ubuntu kernel?

---

