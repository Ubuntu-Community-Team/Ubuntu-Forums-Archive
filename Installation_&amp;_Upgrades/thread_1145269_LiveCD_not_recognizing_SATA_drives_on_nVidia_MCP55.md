---
title: "LiveCD not recognizing SATA drives on nVidia MCP55 SATA controller"
date: 2009-05-01
forum: Installation &amp; Upgrades
---

### Post by spl757 on 2009-05-01
I have a XFX nForce 680i LT motherboard with the MCP55 SATA controller and the newest 2.6.28 kernel that comes with Jaunty does not see my drives.   Has anyone else had this problem with nVidia chipsets?  If I use kernel 2.6.27-11 it sees my drives and I can boot.

00:0e.0 IDE interface: nVidia Corporation MCP55 SATA Controller (rev a2)
Barracuda 7200.10 SATA 3.0Gb/s 500-GB Hard Drive

Thanks for any help.

---

### Post by spl757 on 2009-05-01
Oh yeah, the error I am getting is this:

"SRST failed (errno=-16)"

I've tried edd=on, noacpi, noapic, apm=on, irqpoll, all_generic_ide, and pci=nomsi kernel parameters

---

### Post by StrikerMan780 on 2010-11-25
Sorry for the bump, but I am having this issue as well.

---

