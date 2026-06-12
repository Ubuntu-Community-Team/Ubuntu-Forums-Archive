---
title: "Check Ubuntu System"
date: 2010-07-15
forum: Hardware
---

### Post by kooia on 2010-07-15
Hi everyone,

I was wondering how you're supposed to find out the hardware... like your sound card, graphics card, video card, etc.  I'm trying to do some MIDI stuff, but I need to find out the sound card first.

Kooia

---

### Post by Fire_Chief on 2010-07-15
You could use the System Information utility from the System -> Administration menu (I think) or from a terminal run ```
lspci
```This will show you the PCI devices attached to the system. I think it will include onboard devices such as sound cards and NICs as well.

Cheers!

---

### Post by CharlesA on 2010-07-15
*lspci* and *lsusb* will tell you most of what you need to know.

There is also a *lshw* command.

---

