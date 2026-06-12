---
title: "PCMCIA card only works with 'irqpoll'"
date: 2005-07-08
forum: Hardware &amp; Laptops
---

### Post by StupidHaiku on 2005-07-08
Hey all.  I've got a problem where my wifi card will only work when I enable the 'irqpoll' option at boot time.  The driver (madwifi, same problem with ndiswrapper) otherwise loads fine.  I get a message of 'irq #9: nobody cared' and 'diabling irq #9 in dmesg.  I'm not sure what other information would be relevant here, though I've tried pretty much everything (it's only recently I've realized I can get it to work w/ irqpoll).  The laptop is an older gateway solo and I've tried tinkering with the bios irq settings, but nothing seems to work.  Any help as to how I could get it working without irqpoll would be appreciated, but failing that, dmesg tells me irqpoll can impact system performance, does anyone know by how much?  I could live with it if it's only a small detriment.  
Thanks.

---

