---
title: "ppc ubuntu"
date: 2005-03-31
forum: Hardware &amp; Laptops
---

### Post by brenden on 2005-03-31
I'm running PPC ubuntu on my laptop, which is a 15 inch G4 powerbook.  I regret buying this thing, but it's too late to return it.  So now, I'm trying to make the PCMCIA wireless card I bought work.  The card is an SMC2835W which will work using the prism54 driver.  However, when I try to connect to anything, it barfs after loading the firmware
```
PCI: Enabling device 0001:11:00.0 (0000 -> 0002)
divert: allocating divert_blk for eth0
eth0: resetting device...
eth0: uploading firmware...
eth0: firmware version: 1.0.4.3
eth0: firmware upload complete
eth0: no 'reset complete' IRQ seen - retrying
eth0: no 'reset complete' IRQ seen - retrying
eth0: interface reset failure
prism54: Your card/socket may be faulty, or IRQ line too busy :(
``` 

I would really like to get this working.  I've been roughly following the guide on the gentoo forums (I use gentoo on my amd64 desktop machine, but I don't feel like waiting for stuff to compile on my laptop) here: [http://forums.gentoo.org/viewtopic-t-162622.html](http://forums.gentoo.org/viewtopic-t-162622.html)

---

