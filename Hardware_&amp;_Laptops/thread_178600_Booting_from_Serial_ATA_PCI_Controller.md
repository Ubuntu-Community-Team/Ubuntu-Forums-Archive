---
title: "Booting from Serial ATA PCI Controller"
date: 2006-05-18
forum: Hardware &amp; Laptops
---

### Post by shadypalm88 on 2006-05-18
I just installed a SATA controller card and large SATA disk, and would like to boot Ubuntu from it, but when I turn the machine on it simply says "Boot failure: System halted."

Any thoughts?

---

### Post by mips on 2006-05-18
[QUOTE=shadypalm88]I just installed a SATA controller card and large SATA disk, and would like to boot Ubuntu from it, but when I turn the machine on it simply says "Boot failure: System halted."

Any thoughts?[/QUOTE]

What card ?
Is this the only card drive in the pc ?
I assume it gets past the bios screen, sees the controller card and then tries to boot the drive followed by the failure ?
Is everything setup correctly in the 'sata controller' cards bios ?
Is the drive formatted or what ?

---

### Post by shadypalm88 on 2006-05-18
[QUOTE=mips]What card ?
Is this the only card drive in the pc ?
I assume it gets past the bios screen, sees the controller card and then tries to boot the drive followed by the failure ?
Is everything setup correctly in the 'sata controller' cards bios ?
Is the drive formatted or what ?[/QUOTE]

I don't think the BIOS is seeing it as a boot device.  The card is a Vantec UGT-ST200 and its controller is a Silicon Image SATALink Sil3112.

There must be some way for this to work; the BIOS sees the network boot agent on my network card, after all.

---

