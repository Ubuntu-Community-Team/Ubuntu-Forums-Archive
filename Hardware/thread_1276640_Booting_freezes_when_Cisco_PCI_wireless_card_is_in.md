---
title: "Booting freezes when Cisco PCI wireless card is installed"
date: 2009-09-27
forum: Hardware
---

### Post by snikeris on 2009-09-27
The system freezes during boot when polling a Atheros based Cisco PCI wireless adapter.

If I remove the card, everything boots fine.  This issue is manifesting in BSD too, which leads me to believe it is some kind of conflict.  

There are no other PCI cards installed, other than a few on board things that are PCI.  I've tried disabling all devices (sound, ethernet, etc) in the BIOS that I was able to, but to no avail.

I've tried both PCI slots on the motherboard.

Any ideas?

---

### Post by snikeris on 2009-09-27
Is this the correct forum for this question?

---

### Post by snikeris on 2009-09-28
Interestingly enough, the adapter works fine in windows.  The adapter is a Cisco Aironet card.  How should I proceed?

---

### Post by P4man on 2009-09-28
try adding "acpi=noirq" to your kernel options.

---

### Post by snikeris on 2009-09-28
> **P4man said:**
> try adding "acpi=noirq" to your kernel options.

No success with trying this.

To note, it freezes (after a full-install or when booting the livecd) with this as the last output:

ath5k_pci 0000:04:00.0: registered as 'phy0'

The card works just fine in windows.

---

### Post by snikeris on 2009-09-29
Am I in the right forum for this issue?

Is any additional information required?

---

### Post by snikeris on 2009-09-30
Anyone have any suggestions, or where else I can go for help?

---

