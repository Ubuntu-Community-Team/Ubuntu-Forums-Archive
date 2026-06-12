---
title: "KWorld ATSC 120 PCI TV Card and Post Lucid (10.04) Kernels"
date: 2013-07-17
forum: Hardware
---

### Post by johnappleseed on 2013-07-17
First time poster and long time reader and Ubuntu fanatic.  I have noticed that since the 10.04 release, support for the KWorld ATSC 120 PCI TV Card is no longer working correctly.  This card works flawlessly in DVB in 10.04.  I have followed the directions posted here: [http://www.linuxtv.org/wiki/index.php/KWorld_ATSC_120](http://www.linuxtv.org/wiki/index.php/KWorld_ATSC_120) and with any Ubuntu version after 10.04 the card doesn't work.  Doing a channel scan in MythTV isn't able to get Signal Lock on any digital channels.  Not sure what changed in the kernel since Lucid, but could the source for those cx88 kernel modules be compiled to work with the 13.04  kernel headers?  I hate to sound like a total noob here, but how would I go about all of this if it's doable?  I've been using Ubuntu for years, compiled Kernels from source and that sort of thing, but never modules from a previous kernel version.  I'd get a different card, but it works perfectly in 10.04 and I'd rather not do that unless the card was bad.  My main concern is the end of support for Lucid and I'd like to bump up to a newer release and kernel.

---

### Post by dino99 on 2013-07-18
on that updated page, your card is shown as "work"  [http://www.mythtv.org/wiki/Digital_Tuner_Cards](http://www.mythtv.org/wiki/Digital_Tuner_Cards)

but kworld seems having droped the pci120, replaced by pci150; maybe you can compile it to see if it works.
[http://global.kworld-global.com/main/support_down.aspx?mnuid=1255&modid=14](http://global.kworld-global.com/main/support_down.aspx?mnuid=1255&modid=14)

or report an ubuntu-bug against linux

---

