---
title: "NForce 3 250Gb : no sound"
date: 2004-12-29
forum: Hardware &amp; Laptops
---

### Post by albator2000 on 2004-12-29
Hi there

I've a Soltek Qbic with a NForce 3 250Gb motherboard in it and a A64 3000+
I've installed Ubuntu 4.10 (Warty) and everything is OK : my SATA harddrive is working perfectly, my network adapter (NForce onboard adapter) too but there's no sound at all  :-( 

I've downloaded NFORCE-Linux-x86-1.0-0292-pkg1.run and installed it, it says it's correctly installed but there's still no sound

lsmod show me that Ubuntu load pcicmi module and many other, since i've a nvidia sound card it can't work so I've forced loading nvsound instead of all this stuff and now lsmod looks like correct :

nvsound & soundcore loaded

...still no sound, VLC want /dev/dsp, XMMS is crashing telling me that my sound card is not installed, ect...

Help me please

---

### Post by albator2000 on 2005-01-17
no help here ?
ok... i'll buy an Audigy sound card :(

---

