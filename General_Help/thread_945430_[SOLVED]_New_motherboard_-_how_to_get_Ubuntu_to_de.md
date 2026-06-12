---
title: "[SOLVED] New motherboard - how to get Ubuntu to detect new PCI 'locations'?"
date: 2008-10-12
forum: General Help
---

### Post by Cup of Squirrels on 2008-10-12
Hello,

Due to a conked out PSU and various other messes, I had to get myself a new motherboard and cpu (moved from single core P4 to dual-core Intel).

However, I guess this means the locations of my PCI/AGP cards has changed, and Ubuntu hasn't picked up on this (Can't seem to find my PCI wireless card or graphics card. Not so sure about sound, it still works).

I know the hardware is fine, everything works great on my Windows partition.


Are there any commands that can help Ubuntu sniff out the new device locations?


Any help is appreciated, thanks =)

---

### Post by Yellow Pasque on 2008-10-12
Does Ubuntu recognize the hardware? (I would assume it at least recognizes your GPU since you aren't complaining about no display) Run these commands and make sure your cards are listed with lspci:
```
sudo update-pciids
lspci
```

Next, do you have the right drivers?
For wireless card, this should return info about your card with a driver=<module name> field. If your wirless card says "UNCLAIMED", then you have a driver issue:
```
sudo lshw -C network
```
For the graphics card, you may need to reinstall the graphics driver or reconfigure /etc/X11/xorg.conf  What kind of graphics card do you have?

---

### Post by Cup of Squirrels on 2008-10-12
> **Temüjin said:**
> Does Ubuntu recognize the hardware? (I would assume it at least recognizes your GPU since you aren't complaining about no display) Run these commands and make sure your cards are listed with lspci:
```
sudo update-pciids
lspci
```

Next, do you have the right drivers?
For wireless card, this should return info about your card with a driver=<module name> field. If your wirless card says "UNCLAIMED", then you have a driver issue:
```
sudo lshw -C network
```
For the graphics card, you may need to reinstall the graphics driver or reconfigure /etc/X11/xorg.conf  What kind of graphics card do you have?

Hello,

I did as you advised, and the system found all of my devices, allowing EnvyNG to reinstall my graphics drivers, and letting me reconfigure my network card.

Thankyou =)

---

### Post by Yellow Pasque on 2008-10-12
Awesome. Please mark the thread as SOLVED (under the thread tools menu).

---

