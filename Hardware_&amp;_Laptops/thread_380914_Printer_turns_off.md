---
title: "Printer turns off"
date: 2007-03-10
forum: Hardware &amp; Laptops
---

### Post by geovino on 2007-03-10
I have a HP 5440 deskjet that is connected directly to PC and I've noticed that after turning off computer it will also turn off the printer, which I always leave on. Are there printer settings to correct this problem?

---

### Post by thingy on 2007-03-10
Pagew 58 in your printer's manual talks about an auto off feature:

[http://h10032.www1.hp.com/ctg/Manual/c00452908.pdf](http://h10032.www1.hp.com/ctg/Manual/c00452908.pdf)

> Select the auto-off feature to automatically place the printer into idle mode after 30 minutes and to turn back on automatically when print jobs are sent to the printer. Selecting auto-off cancels the FEMP energy savings mode.

Problem is, this sounds like a feature of the printer which a HP made windows driver can probably control. However, the linux HP drivers most probably won't have the feature.


Post a message on the HP linux drivers forum and see what they say:

[http://hplip.sourceforge.net/](http://hplip.sourceforge.net/)

---

### Post by geovino on 2007-03-11
Found it and turned off the setting. Thanks.

---

