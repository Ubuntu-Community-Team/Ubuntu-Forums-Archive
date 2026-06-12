---
title: "Ethernet broken after 8.10 install"
date: 2009-02-22
forum: Installation &amp; Upgrades
---

### Post by too_many_people on 2009-02-22
So this is an issue I've been having for some time now...
Whenever I install Ubuntu 8.10 on my machine, the Ethernet port (which has a functional jack plugged in right now - I'm writing from the computer) doesn't get properly recognized by the OS.  Network Manager appears to recognize it, but it seems to get the wrong driver for the chipset because an ifconfig shows the card but no connection.  The same problem occurs with OpenSuse 11.1 but not with Fedora 10.
The board is a Foxconn A7GM-S with a RTL8111B chip on-board.
I seem to remember reading something about this before, but I cannot, for the life of me, remember the resolution.
Any help would be appreciated,

John

---

### Post by too_many_people on 2009-02-24
So...is there any resolution to this?  Is it in the wrong sub-forum?  Am I not asking the right question?


Um...bump?:p

---

### Post by pgmer6809 on 2009-02-24
> **too_many_people said:**
> So...is there any resolution to this?  Is it in the wrong sub-forum?  Am I not asking the right question?


Um...bump?:p

You might try asking on the networking forum.
I had/have similar problems. I posted some months ago under the name pgmer6809 in the networking forum.
Never got a resolution.
Lots of the usual wild goose chases about configuring network manager etc.
But this is all smoke.
When you try an ifup or an ifconfig, the network comes up but an IP address is never assigned. If you assign a static IP address you get some sort of overflow error. At least that is what happened to me.
Same error on both Hardy and Ibex. But the wireless works fine. 
Also Hardy and Ibex work fine on an older computer with an old 3COM PCI ethernet card.
But the skge driver (for Marvell chips) and the driver for my LAN on my HP laptop have the same problem. An IP address is never assigned, or a static assignment gets a buffer overflow error.

---

### Post by too_many_people on 2009-02-25
That's exactly it.  It seems like Network Manager's detection of cards/chipsets is ahead of the kernel's detection in some cases.  ifup and ifconfig eth0 (pretending that's the name of my adapter) fail, while Network Manager successfully assigns an IP right out of the gate.  Weird.
Does anyone know any resolution to this?
I consider it an install/upgrade issue because it's broken the minute I install/upgrade to 8.10.

Thinking back on old readings, I remember seeing somewhere that the RTL8111B driver gets improperly detected in some kernels as an 8140 driver or something.  Does this sound familiar?

---

