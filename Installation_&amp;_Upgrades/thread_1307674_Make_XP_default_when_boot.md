---
title: "Make XP default when boot"
date: 2009-10-31
forum: Installation &amp; Upgrades
---

### Post by bangrobe on 2009-10-31
I installed Win XP, after that I installed Ubuntu 9.10 . Boot is OK and Ubuntu is default. But I'd like Win XP is boot default. Grub2 is very hard to control. So anyone can help me??:(

---

### Post by miro3 on 2009-10-31
try edit /etc/default/grub

GRUB_DEFAULT=0
*Sets the default and pre-selected menu entry. Entries may be numeric or saved
*GRUB_DEFAULT=0
*Sets the default menu entry by menu position. As with Grub Legacy, the first "menuentry" in grub.cfg is 0, the second is 1, etc.

[http://wiki.ubuntu.com/Grub2#grub (/etc/default/grub)]("http://wiki.ubuntu.com/Grub2#grub (/etc/default/grub)")

---

