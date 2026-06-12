---
title: "[solved] Floppy kernel module not automatic loaded"
date: 2013-04-18
forum: Hardware
---

### Post by kuifje09 on 2013-04-18
Running ubuntu 12.04 I tried to use the floppy drive and found it not usable.
No devicefiles , no kernel module loaded.
Luckily it is available so I could modprobe floppy  and be able to use it again.
Why is it not loaded by default when the floppy drive is available in the hardware?

---

### Post by cortman on 2013-04-18
Probably because so few people use floppies nowadays. You could probably find out what logic the system used by grepping dmesg for "floppy".
You can make also make the system load the floppy module at boot (make the change permanent) by opening /etc/modules in a text editor, and simply adding a line containing the module name.

---

