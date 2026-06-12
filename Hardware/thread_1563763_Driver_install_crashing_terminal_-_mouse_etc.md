---
title: "Driver install crashing terminal - mouse etc"
date: 2010-08-29
forum: Hardware
---

### Post by dede468 on 2010-08-29
Two different laptops - same problem.

First, checked lsusb in terminal which told me there was a usb SGS Thomson modem plugged in.

Downloaded source and daemon sl-modem from Ubuntu 10.04 repo.

Rechecked lsusb WITHOUT modem plugged in - all OK

Plugged in modem, rechecked lsusb.or tried to. Mouse stopped working and terminal cursor froze. Unplugged mouse still same. Unplugged modem - still same. Then had to restart computer to unfreeze things. 

Then tried same thing on a different make of laptop with exactly the same results. Driver details on Synaptic say this modem works with internal OR usb modems.  Is this a case of two devices trying to use same IRQ?  Any ideas how to check/find problem? Anyone please?

---

