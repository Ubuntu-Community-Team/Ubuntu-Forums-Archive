---
title: "irq poll usb issue with koala"
date: 2009-10-29
forum: Installation &amp; Upgrades
---

### Post by umabatata on 2009-10-29
Hi there
I installed 9.1 just now and it is all looking good.
Previously I had to add irqpoll to menu.lst to get usb ports working. (this seems to be a problem specific to this midel of machine (fujitsu seimens amilo L7310gw) I have done this on a few versions. Karmic does not have menu.lst but has grub.cfg instead - but it cannot be edited. Any ideas...?
Thanks.

---

### Post by umabatata on 2009-10-29
sorted. 
Found out about the new grub system, edited the grub file and then did a grub update. sweet as now.

---

