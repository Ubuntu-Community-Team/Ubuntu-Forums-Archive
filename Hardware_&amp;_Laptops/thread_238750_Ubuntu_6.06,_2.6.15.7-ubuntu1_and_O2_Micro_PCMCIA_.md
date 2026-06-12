---
title: "Ubuntu 6.06, 2.6.15.7-ubuntu1 and O2 Micro PCMCIA Controller problems"
date: 2006-08-18
forum: Hardware &amp; Laptops
---

### Post by dprime on 2006-08-18
Hi,

I've been trying to get various pcmcia devices (usb/firewire bridge cards etc) to work on a couple of laptops I have and have been experiencing some problems with detection and hotplugging.

Sometimes when plugging the card in, it will not power up. If I eject the card (manually) and plug it in again, it will power up and enumerate and generally function properly. The real prbolem occurs when I unplug it again. After I unplug the card the system will lock up (not a 100% occurance, but it will lock up after the 2nd or 3rd hotplug every time).

The laptops were all running ubuntu 6.06 and have an O2Micro PCMCIA controller.

Has anyone experienced similar?

cheers,

dprime

---

### Post by BungaMan on 2006-08-30
can you do 
lspci | grep O2
I'm searching to get my card reader to work with O2 Micro but no luck so far.  What did you do to get it to work?

---

