---
title: "Dual boot, each with its own graphics card?"
date: 2010-01-16
forum: Hardware
---

### Post by rimshot4 on 2010-01-16
I'm new to Linux (and have been using the heck out of this forum--thank you all), and I have been cursed with a Radeon 9250 PCI on my dual-boot (XP) desktop. I've given up trying to get it to work to any reasonable degree in Ubuntu. 



I have a low-power onboard Intel graphics chipset that performs much better that my Radeon 9250 in Ubuntu, while the Radeon does very well in XP. Would it be possible to set up Ubuntu to use the Intel chipset while ignoring the Radeon PCI card? Without having to readjust my BIOS every time I switch OS?

(Note, physical connection is not a problem: the Intel onboard is connected via standard VGA cable, the Radeon PCI via the newer connection cable(DCI or whatever it's called), both into the same monitor, which itself switched from analog to digital seamlessly).

---

### Post by OmegaAI on 2010-01-17
Unless you have a Tesla card (2000-3000 USD card) that is not going to happen. It is a workstation environment and it is still being worked on.... :|

---

### Post by falconindy on 2010-01-17
> **rimshot4 said:**
> I'm new to Linux (and have been using the heck out of this forum--thank you all), and I have been cursed with a Radeon 9250 PCI on my dual-boot (XP) desktop. I've given up trying to get it to work to any reasonable degree in Ubuntu. 



I have a low-power onboard Intel graphics chipset that performs much better that my Radeon 9250 in Ubuntu, while the Radeon does very well in XP. Would it be possible to set up Ubuntu to use the Intel chipset while ignoring the Radeon PCI card? Without having to readjust my BIOS every time I switch OS?

(Note, physical connection is not a problem: the Intel onboard is connected via standard VGA cable, the Radeon PCI via the newer connection cable(DCI or whatever it's called), both into the same monitor, which itself switched from analog to digital seamlessly).
You might need to manually setup xorg.conf and/or xrandr to ignore the other video output, but this is certainly feasible.

No idea what the poster above is referencing.

---

