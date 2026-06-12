---
title: "device IRQ and drivers"
date: 2010-01-11
forum: Hardware
---

### Post by brickhead248 on 2010-01-11
Hello Ubuntu forum members!

I've been converted to Ubuntu, and i'm loving it. I like it so much that im trying to become completely independant from MS Window$.

Unfortunately, this is not easy when developers write software that doesnt work in windows XP without the user having to screw around with IRQ assignments.

I have this program called DVR2000 (it refers to itself by many names such as PEAQUE, DSR digital survalence), which i use to display the input of security cameras via a PCI card.

when it runs, it gives the error "the register security key is not found" when you try and run it. - this is completely meaningless, because it is trying to say that it cannot detect the PCI card.

when i had it running in XP, i would make sure that the drivers which it came with were installed correctly via device manager, and then, because the pci card wasn't acquiring the correct IRQ, i would have to disable some devices individually until the software worked.

Unfortunately there is no device manager in ubuntu, and when i installed it through WINE, i got the error. so [B]TL;DR: How do i manually install drivers for this PCI card, and how do i find out which devices are using which IRQ lines?
[/B]
i've had a look at Device Manager but thats not what im looking for

i have tried booting under the options PCI=ROUTEIRQ and ACPI=OFF, these havent worked.

i also went into the BIOS and diabled all the redundant serial ports, and assigned the PCI device that i thought was the card to an IRQ of 11 and then 10 (the open ones).

still have the problem.

any ideas?

---

### Post by brickhead248 on 2010-01-11
hmmm.... just realised that the drivers on the disk are XP only.

that is probably causing the problem.

what do i do?

---

### Post by Cool Javelin on 2010-06-08
Brickhead:

Have you found a solution to this issue yet as I have that same video capture card in a windoz machine and would like to move to Linux too.

To be honest, I have no real desire to stay with that DSR software that came with the card. It does the job I need, but I would prefer more flexibility.

Thanks, Mark.

---

