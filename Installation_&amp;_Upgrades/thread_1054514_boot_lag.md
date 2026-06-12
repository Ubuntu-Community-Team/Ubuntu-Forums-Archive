---
title: "boot lag"
date: 2009-01-29
forum: Installation &amp; Upgrades
---

### Post by evrkusd on 2009-01-29
during my boot i have to hit the return key at certain points in order to make it continue. it basically errors or hangs indefinitely at these points unless I hit return.
I took quiet out of the menu.lst entry and checked where exactly it is hanging. this has been happening since i updated to 8.10 from 8.04

here are the entries it hangs at:

3.13 hub 4-0:1.0: 2 ports detected
68.8 clocksource tsc unstable

ata1.00 configured for UDMA/100

147 ata2 SATA link down (ssstatus 0 scontrol 300)

173 '' ''

*using shell-style concurrent boot in runlevel S

*setting preliminary keymap...

*preparing restricted drivers


anyone with any ideas about what to do would be great.

---

### Post by taurus on 2009-01-29
> **evrkusd said:**
> during my boot i have to hit the return key at certain points in order to make it continue. it basically errors or hangs indefinitely at these points unless I hit return.
I took quiet out of the menu.lst entry and checked where exactly it is hanging. this has been happening since i updated to 8.10 from 8.04

here are the entries it hangs at:

3.13 hub 4-0:1.0: 2 ports detected
68.8 clocksource tsc unstable

ata1.00 configured for UDMA/100

147 ata2 SATA link down (ssstatus 0 scontrol 300)

173 '' ''

*using shell-style concurrent boot in runlevel S

*setting preliminary keymap...

***preparing restricted drivers**

anyone with any ideas about what to do would be great.

Maybe it has something to do with a driver for your graphic card?  What kind of graphic card do you have and have you installed any driver for it?

---

### Post by evrkusd on 2009-01-29
no, the video driver is fine. it's the one provided for my card via nvidia. i'll try to drop it back to a previous version to see if it helps but i'm pretty sure it's ok. any other ideas?

---

### Post by evrkusd on 2009-01-29
yeah, the video driver isn't the issue. during the upgrade there i was asked whether i wanted to replace or merge or keep the original file for a number of files. i think this may be where the issue came from but i'm not sure how to go back and fix it.

---

