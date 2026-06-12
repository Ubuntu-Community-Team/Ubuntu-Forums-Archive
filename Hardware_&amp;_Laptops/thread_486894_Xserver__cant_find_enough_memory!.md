---
title: "Xserver  cant find enough memory?!?"
date: 2007-06-28
forum: Hardware &amp; Laptops
---

### Post by glenndavy on 2007-06-28
Hi 
I've got a pair of X1650 ati cards, on PCI-e busses.
One (main card) is on 1:0:0
the other is on 4:0:0

regardless of the driver i use, whether i use it alone or at same time, the second card gives me this error:

```
(II) Attempted to read BIOS 128KB from /sys/bus/pci/devices/0000:04:00.0/rom: got 0KB
Requesting insufficient memory window!: start: 0xff800000 end: 0xff8fffff size 0x10000000
(EE) Cannot find empty range to map base to
(EE) VESA(0): Cannot read V_BIOS (3)
(II) UnloadModule: "vesa"

```

The system is a core2duo, and with 4GB ram all in a asus p5bdeluxe.  Does anyone have any idea what might be behind this problem, or how i can address it?

thanks
Glenn

---

