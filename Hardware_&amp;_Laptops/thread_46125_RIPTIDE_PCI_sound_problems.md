---
title: "RIPTIDE PCI sound problems"
date: 2005-07-03
forum: Hardware &amp; Laptops
---

### Post by mr.loco on 2005-07-03
hi, I'm new to the ubuntu community as well as the linux community as a whole. I have a problem with my on board soundcard. Windows says it's a riptide pci sound controller. Linux doesn't recognize it and i am unable to find any drivers for this soundcard. the card was included with my hp pavilion 8575C comp if that helps.

P.S.
whats the whole deal with kernel sources...i need to compile the berilios driver, but i dont know where to find the kernel...

---

### Post by MasterPatricko on 2005-07-04
Yeah I'm having the same problem. I have gone to Linuxant, downloaded the drivers. The riptide driver doesn't install at first because of a lack of a modversions.h in the kernel header files. After some research I came to the conclusion that this file was removed in the 2.6 kernel or something like that. So I hand-edited the install script to remove all reference to that file - but now it comes up with some other error. I have not gotten this card to work with ANY distro.

Probably better to just buy a new soundcard.

---

