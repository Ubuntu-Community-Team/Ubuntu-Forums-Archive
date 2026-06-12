---
title: "Graphics Card Drivers?"
date: 2009-06-11
forum: Installation &amp; Upgrades
---

### Post by RocketDarkness on 2009-06-11
Hello all. I've recently downloaded ubuntu-desktop onto a server, but it's having some strange graphical issues. The screen is greatly washed out. I can provide a pseudo-fix by dropping the gamma significantly, but that messes with the appearance of other things. I suspect it has to do with the drivers, but I'm not positive.  I'm looking at xorg.conf, and all it says is Identifier "Configured Video Device", in regards to graphics card.

The following is from hwinfo, in relation to the graphics card (I think it's onboard). In any case, can anyone help nudge me in the right direction? I'd be glad to supply any information necessary, just let me know what  you need and how to get it.


Hardware Class: graphics card
  Model: "Hewlett-Packard Company ES1000 515E"
  Vendor: pci 0x1002 "ATI Technologies Inc"
  Device: pci 0x515e "ES1000 515E"
  SubVendor: pci 0x103c "Hewlett-Packard Company"
  SubDevice: pci 0x31fb 
  Revision: 0x02
  Memory Range: 0xd8000000-0xdfffffff (rw,prefetchable)
  I/O Ports: 0x3000-0x30ff (rw)
  Memory Range: 0xf7ff0000-0xf7ffffff (rw,non-prefetchable)
  Memory Range: 0xf7e00000-0xf7e1ffff (ro,prefetchable,disabled)
  IRQ: 7 (no events)
  I/O Ports: 0x3c0-0x3df (rw)
  Module Alias: "pci:v00001002d0000515Esv0000103Csd000031FBbc03sc00i00"
  Driver Info #0:
    XFree86 v4 Server Module: radeon
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #32 (PCI bridge)

---

### Post by Steelmourne on 2009-06-11
That looks like ATI radeon problems. Try looking here: [http://wiki.cchtml.com/index.php/Main_Page](http://wiki.cchtml.com/index.php/Main_Page)

---

### Post by RocketDarkness on 2009-06-12
Hey, thanks! That seems to have cleared up the major issues. Says it's running in low-graphics mode, but that's not a problem. Just nice to be able to see things again. =)

---

