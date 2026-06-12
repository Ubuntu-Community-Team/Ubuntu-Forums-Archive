---
title: "Breezy unable to mount cdrom at installation"
date: 2005-10-13
forum: Hardware &amp; Laptops
---

### Post by fif on 2005-10-13
At install, the mount command is unable to mount the cdrom. Trying via a shell, mount reports that there is no cdrom.
I wonder if this comes from my hardware config: I have 3 disks mixing p- and s-ata, and I use the p-ata disk as a boot disk. But I cannot figure out why the error I get is that no cd is present in the drive...

Does anyone have a clue?

TIA

Fif

---

### Post by fif on 2005-10-13
Sorry everyone. I was too quick in addressing a request to the forum. I mixed up in the configuration of my motherboard (Asus P4P800). Having a look at the manual helped - select SATA for IDE config i.s.o. PATA+SATA
Cdrom is now correctly recognised as installation media...

---

