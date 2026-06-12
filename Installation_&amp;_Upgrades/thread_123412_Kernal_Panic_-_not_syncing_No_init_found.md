---
title: "Kernal Panic - not syncing: No init found"
date: 2006-01-30
forum: Installation &amp; Upgrades
---

### Post by Blindbatts on 2006-01-30
Trying to install Ubuntu on a spare computer, I got the disc from a free package at school.

Athlon 1.1ghz
768mb
2 x HD's, 10.2 and 13.5gb (IDE)
CD-rom
LS-120 drive
ATI All-in-wonder 128 PCI video
3com 3c905b PCI NIC

I forget the exact mobo but its a Via based one.

ubuntu cd shows as "version 5.10 for your pc"

I havent tried the "live" cd yet, just the install one.

I can use the boot menu, but I'm not sure what all to do...

---

### Post by Blindbatts on 2006-01-30
ahh, I figured it out.

I installed with this switch:

linux pci=noacpi

and it seems to be working so far

---

