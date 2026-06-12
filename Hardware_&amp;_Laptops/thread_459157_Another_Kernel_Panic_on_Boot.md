---
title: "Another Kernel Panic on Boot"
date: 2007-05-30
forum: Hardware &amp; Laptops
---

### Post by bjordonthaden on 2007-05-30
Hello

Long time, first time

Never had a problem that the forums or google couldn't help with until now:

System:
Dell Inspiron 8000 1 GHz PIII, 512 RAM, Microsoft MN-520 PCMCIA wireless
New install of Feisty
Kernel 2.6.20-16-generic

Problem:
Kernel panic at boot if the wireless card is inserted. Boots normally if the wireless card is absent. If I insert the wireless card later, everything is fine. (I can't find a log of the boot in the dmesg log or the system log.)

From the  boot screen it says something like 
> Code: Bad EIP value
Kernel panic - not syncing: Fatal exception on interrupt.

The failure was present in the previous installed kernel of Feisty. I was hoping that a new kernel would fix the problem. No problems with previous ubuntu releases.

Thanks

---

### Post by bjordonthaden on 2007-08-14
For those of you interested, I figured out the problem has something to do with pcmciautils functions to interface with pcmcia cards. The #$%@# thing was loading two drivers, hostap_cs and orinico_cs conflicting with each other. Furthermore, hostap_cs doesn't work well with the card, leaving the best choice as orinico_cs. The inelegant solution is to blacklist the hostap_cs driver in /etc/modprobe.d/blacklist

Now the laptop boots and wireless run's fine.

Brandon

---

### Post by Timothy S on 2007-12-21
Thanks! I was having this problem with my inspiron 8100, now it works!

---

