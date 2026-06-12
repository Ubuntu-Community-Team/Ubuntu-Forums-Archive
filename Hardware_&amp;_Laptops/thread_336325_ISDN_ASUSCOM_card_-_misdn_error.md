---
title: "ISDN ASUSCOM card - misdn error"
date: 2007-01-11
forum: Hardware &amp; Laptops
---

### Post by juraj on 2007-01-11
I have an internal PCI ASUSCOM ISDN card. I get this when I do "dmesg | grep isdn" on every boot:

[timestamp] mISDN: INTERNAL ERROR in drivers/isdn/misdn/stack.c:596

misdn is also holding my system back from hibernation. I've submitted a [bug report]("https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.17/+bug/76039") about that, but nobody cared. I've installed isdntools but nothing. There is no corresponding pseudo-file in /dev and I can't use the device.

Is there any solution? Can I access internet using this device?

---

