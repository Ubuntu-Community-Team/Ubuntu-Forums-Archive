---
title: "Aspire One 521 Athlon II Neo Procesor K125 installation problem"
date: 2010-08-09
forum: Hardware
---

### Post by utileria on 2010-08-09
Trying to install 10.04 and remix 10.04  in model AO521-3165 Aspire One 521 Athlon II Neo Procesor K125  gives an installation failure. (Tested in several AO521 giving the same result)

a) The first message: Disabling IRQ # 18

b) 10.04 in mode installing without modification gets into a 3 sound loop and then halts completely.

c) remix in mode installing without modification gets into the gnome screen but the keyboard is completely dead.

d) Installing both of them in the hard disk can partition hard disk but then the system asks the name and password and again the keyboard is dead.

Here is another message trying to install BackTrack4R1 giving maybe more clues:

[Firmware bug] PCI MMConfig at (mem 0xe0000000 - 0xe03fffff not reserved in ACPI motherboard resources
i8042.C: Can´t read CTR while initializing i8042
irq18 nobody cared (try booting with the "irqpool" option)
Disabling IRQ #18

e) The same result with Open Suse.

Help me with this technical issue.

Thank you very much!

---

### Post by clrg on 2010-08-09
Try the alternate installation CD. Also, try booting with the option suggested:

> irq18 nobody cared (try booting with the "irqpool" option)

---

### Post by utileria on 2010-08-09
> **clrg said:**
> Try the alternate installation CD. Also, try booting with the option suggested:

Adding irqpoll gives the same result and the message:

[31.000154] shpchp 0000:00:01.0: Cannot reserve MMIO region

---

### Post by jbluzb86 on 2010-10-21
Is this fixed in version 10.10

---

