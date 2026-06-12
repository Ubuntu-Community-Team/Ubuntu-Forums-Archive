---
title: "Supported IDE controller for Meerkat?"
date: 2010-11-04
forum: Hardware
---

### Post by andrusoid on 2010-11-04
Looking for a PCI IDE 133 controller for Meerkat. (Ubuntu 10.10, *not* Lubuntu)

Anyone have a known good controller working?

I tried a VIA VT6410, supported by the kernel, controller shows up in the system but does not detect attached drives. Drives do show in XP, can be formatted and striped, set up as mirror, span, etc. Just aren't recognized by Meerkat. (I've read all I can find, used dmraid, mdadm, all expect to have something in /dev.)

I found this link that may point to an possible improvement to the via_pata driver.

[http://www.spinics.net/lists/linux-ide/msg37206.html](http://www.spinics.net/lists/linux-ide/msg37206.html)

I've looked for an HCL to search for the answer here. Just looking for a controller that's known to work.

Thanks.

---

