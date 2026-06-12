---
title: "Egdy with cardbus TV Tuner"
date: 2007-03-02
forum: Hardware &amp; Laptops
---

### Post by Brooklyn on 2007-03-02
Hello, I have a cardbus tv tuner, model dvb-T2100(if that means anything).  It says it has an Xcieve XC 3028 tuner and a Conexant CX2388 chipset.  

Ok, so I installed the v4l drivers as the wiki stated, however, whenever I plug in the card, it is recognized as a saa7134 type, and grep gives me a fronted failure.  

Now I try to unload all the drivers, and modprobe the cx driver, but it says no such device found.  So does this mean I really have a SAA7134 card or ?

---

### Post by Brooklyn on 2007-03-03
OK, so the driver in windows says its a Saa7134 card, so it must be.  The box was poorly made, I think its for 2 different cards, and I was looking at the wrong section.  Anyway, the box says smart tv 2200 as the type of card, and card type 32 is a "smart tv" card, so I thought I would try to set the driver to that card.  Well, now I get a partity error, instead of a frontend failure.... Can anyone give me advice?

---

