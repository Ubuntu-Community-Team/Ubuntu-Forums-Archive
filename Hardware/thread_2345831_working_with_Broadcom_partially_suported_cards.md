---
title: "working with Broadcom partially suported cards"
date: 2016-12-08
forum: Hardware
---

### Post by yldouright on 2016-12-08
I recently had the need to do a wireless pentest. The laptop I had  for this purpose included a Broadcom card that was only partially supported by the Linux kernel driver. Briefly, the card has internet access with the "wl" driver but I can't use the card's advanced features with it. An internet search reveals my particular card, a Broadcom 4322 has several variants. I determined mine with:
*lspci -vnn | grep 14e4*
It appears as though my card is included in the b43.ko module. I downloaded this module but before I install it and kill my distro I would like some questions:

1. How do I try the b43.ko module without it conflicting with the installed wl driver?
2. The b43.ko module has the individual "n0initvals.fw" for my card, how do I extract it and install it. 
3. If any of the above succeed, how do I remove and blacklist my current "wl" driver so it doesn't mess me up with an update?

---

### Post by ajgreeny on 2016-12-08
We do not support any threads relating to penetration testing in this forum as shown in the forum CoC .
[http://ubuntuforums.org/misc.php?do=showrules](http://ubuntuforums.org/misc.php?do=showrules)

Thread closed.

---

