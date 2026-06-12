---
title: "SATA Install without 'pci=nomsi'?"
date: 2009-03-12
forum: Installation &amp; Upgrades
---

### Post by Seventh Reign on 2009-03-12
I've noticed a severe lack of performance with my SATA Drives when installing any Debian based system.  Unfortunately the PCI=NoMSI boot option is the only way i've been able to even see my HDD's on that PC.  Are there any other options?

I'll post my Motherboard and Drive specs in a few hours.  

I do know that my motherboard doesnt support using SATA drives with IDE through the BIOS.

---

### Post by balcis on 2009-03-14
> **Seventh Reign said:**
> I've noticed a severe lack of performance with my SATA Drives when installing any Debian based system.  Unfortunately the PCI=NoMSI boot option is the only way i've been able to even see my HDD's on that PC.  Are there any other options?

I'll post my Motherboard and Drive specs in a few hours.  

I do know that my motherboard doesnt support using SATA drives with IDE through the BIOS.

even my motherboard supports to use my sata drives as ide (Asus a8v-mx), i couldn't be able to install any linux distros without pci=nomsi, becasue they couldn't detect any of my disks.

unfortunately i do not have an answer for your question but i want to ask: why do you want to boot without the parameter "pci=nomsi", is there any disadvantage when you boot this way?

---

