---
title: "Support for intel x5300-N wireless card"
date: 2010-03-23
forum: Hardware
---

### Post by debianmike on 2010-03-23
While a lspci lists the x5300-N wireless card, it doesn't really work and I've heard from others "N" drivers are still pretty iffy in Linux.

How do I know if/when this card will be supported in Ubuntu?

I can't find the Hardware Compatibilty List if one exists.

thanks much!

---

### Post by Muzer on 2010-03-23
Please post the output of:

lspci -nn

(if it's a non-USB card)

or:

lsusb

(if it's USB)


...so we can see the exact device number.

---

### Post by debianmike on 2010-03-23
05:00.0 Network controller [0280]: Intel Corporation PRO/Wireless 5300 AGN [Shiloh] Network Connection [8086:4235]

Linux piccolo 2.6.31-20-generic #58-Ubuntu SMP Fri Mar 12 05:23:09 UTC 2010 i686 GNU/Linux

---

### Post by Muzer on 2010-03-24
Hmm, all I've been able to find out from searches is that the driver used is iwlagn - which is probably already installed...

---

