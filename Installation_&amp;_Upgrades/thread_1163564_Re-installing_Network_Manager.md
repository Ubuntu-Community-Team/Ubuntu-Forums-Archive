---
title: "Re-installing Network Manager"
date: 2009-05-18
forum: Installation &amp; Upgrades
---

### Post by Macr237 on 2009-05-18
Is it possible to reinstall only one package of Ubuntu 9.04? It appears I have a problem with my Network manager, which will not identify my USB wireless dongle. I can get it to recognise it on my desktop, but with the exact same settings on my laptop, it is not recognised.

Does it have be done from disk or can it bee done from synaptic? And if it can be done from either, what file am I actually looking for.

I do not want to have to reload the whole installation disk again.

TIA

---

### Post by mikewhatever on 2009-05-18
Try the following two packages:
network-manager-gnome
network-manager

---

### Post by Macr237 on 2009-05-18
I'll give that a crack and report back.
TIA

---

### Post by Macr237 on 2009-05-18
Well, unfortunately that is not working. Could there be something else which maybe be affecting it that would prevent it recognising the dongle?

---

### Post by mikewhatever on 2009-05-23
You should post the output of **sudo lshw -C network**. I suspect the network manager has nothing to do with recognizing the dongle, if anything, it's probably the kernel module.

---

### Post by Macr237 on 2009-05-23
Thanx Mike. I have worked out my problem. It appears that Ubuntu either:
1. Had a M$ moment and didn't load properly; or
ii. I tried so many different work arounds, that I altered it to a point it was irrepairable. 

I reloaded Ubuntu and tried again from the beginning and got it to work. Oh and Ubuntu gurus need to modify the Optus 3G setup as it is wrong for APPN.
Comes up as CONNECT, when it is actually PRECONNECT. But I am using prepaid, so maybe they need a third category.

---

