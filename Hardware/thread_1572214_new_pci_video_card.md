---
title: "new pci video card"
date: 2010-09-10
forum: Hardware
---

### Post by nixie21 on 2010-09-10
using linux mint, installed a PCI video card... bios screen comes on, i see the mint splash screen and then all goes black..computer is still on, but no pic...what should i do...?

Thanks!

---

### Post by ajgreeny on 2010-09-10
Depending on what the old card and the new one are, ie make and chipset etc etc, all you may need to do is uninstall whatever old driver you were using, rename or delete the old /etc/X11/xorg.conf, if there was one, and then restart.

The system should detect the new card and use an appropriate driver for it, then you can use the System->Administration->Hardware Drivers to see if there are any proprietary drivers available for the new card.

---

