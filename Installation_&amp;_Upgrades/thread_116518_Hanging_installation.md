---
title: "Hanging installation"
date: 2006-01-12
forum: Installation &amp; Upgrades
---

### Post by badun on 2006-01-12
Tried installing 5.10 from CD and also a Live CD.  If I use default boot parms it freezes when it starts the logs.  Searching this forum and others I attempted the boot using the usb=false and acpi=off parms.  I was able to select a language and country, but the next screen was just blue and the installation progresses no further (BSOD? ha ha).  I also disabled legacy USB, same problem with the BSOD.

specs:
Biostar M7NCD Pro (nForce2) @ 200mhz
XP 3200+ (@ 200mhz)
GeForce 6600GT
2 IDE PATA HD's
1 IDE PATA CD
1 IDE PATA DVD

That's about it for peripherals, other than a few small UDB devices, such as a media reader, Webcam, hub, etc.

TIA for the help!

---

### Post by Kipper on 2006-01-13
If you cannot get the LiveCD to run on your Nforce2 m/board try these boot params:

nolapic noapic acpi=ht

They are mentioned in the LiveCD help pages.

Hope that helps.

---

### Post by badun on 2006-01-13
Still no workies.  I guess I'll wait for the next release.  Or just use a different distro.

---

