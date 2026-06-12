---
title: "Using GPRS-modem on PL2303 - driver problems"
date: 2008-05-17
forum: Hardware
---

### Post by romx on 2008-05-17
I have a GPRS/EDGE modem on USB. 
From interface side it’s a simple and good known Prolific PL2303 (I saw an IC inside), which, as I know, bundled in current kernel.
Unfortunately it’s tweaked by firmware (as I think).
USB data is: VID_067B&PID_0611 (modem name is DT-611U, so PID is just from modem’s name).
It working fine with Windows, but I like to use it in Linux too.
Changing in VID/PID make it unknown for my Linux (eeeXubuntu 7.10, tweaked Gutsy Gibbon for ASUS eeePC), and, unfortunately, I can’t got a ttyUSB.
It’s discovered by system like “unknown full-speed USB device”

How can I make my modem usable in my Linux system? 
Can I add support for this PID without recompiling of pl2303 driver?

---

