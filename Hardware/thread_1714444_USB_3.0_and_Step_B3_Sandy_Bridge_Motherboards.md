---
title: "USB 3.0 and Step B3 Sandy Bridge Motherboards"
date: 2011-03-25
forum: Hardware
---

### Post by BBUCommander on 2011-03-25
I recently got my new AsRock Extreme 6 motherboard with B3 stepping for Intel Sandy Bridge processors.  The new stepping is meant to correct an issue with SATA3 & USB3 failure due to a faulty transistor in the previous stepping.  Windows 7 boots and runs without incident, but Ubuntu 10.10 (2.6.35-28-generic) gives me the following errors during boot and will not let me access by USB 3.0 ports:

"Cannot enable port #.  Maybe the USB cable is bad?"
"Cannot reset HCD device state."

It repeats the second quote numerous times per each device #.

I have tried setting USB 3.0 compatibility mode and any other I/O related motherboard BIOS settings I can think of to no avail.  The fact that I experience no problems in Windows 7 definitely implicates the current Linux kernel as the troublemaker.  Particularly strange is that my previous motherboard was the same AsRock Extreme 6 except without the B3 stepping and I experienced no such problems in Ubuntu.

Any suggestions for how I might get my USB 3.0 ports working?

Thanks!

---

### Post by fjgaude on 2011-03-25
I think the next kernel has this fixed, 2.6.38. You might try 11.04 LiveCD and see if the USB3.0 works.

---

### Post by jmandawg on 2011-05-08
I have the same mobo p67 extreme6 and the same problem on 11.04.  Looks like the USB 3.0 chipset (Etron EJ168A) this mobo uses isn't supported by linux.

I should have done more research before buying this one.  It does have a buttload of sata ports though.

---

