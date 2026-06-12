---
title: "Putting an IDE HDD in a computer with a SATA HDD with Ubuntu?"
date: 2012-03-03
forum: Hardware
---

### Post by Rytron on 2012-03-03
Hi.

Has anyone put an IDE HDD in a computer with a SATA HDD with Ubuntu and had no problems? Lets say we boot off the SATA and use the IDE HDD for extra storage.

Or is it best to use 2 SATAs on PC-A and 2 IDE HHD's on PC-B? Is it best not to mix them?

---

### Post by ddr3XD on 2012-03-03
mixing of IDE and SATA drives doesn't hurt at all. ;)

---

### Post by Bucky Ball on 2012-03-03
> **ddr3XD said:**
> mixing of IDE and SATA drives doesn't hurt at all. ;)

+1. I have it the other way around; IDE with XP and Ubuntu dual-booting and three SATA drives. All sweet. Just make sure you have the jumper set correctly on the IDE drive (you don't need to worry with SATA). Slave, not master. ;)

---

### Post by Rytron on 2012-03-03
Thanks guys.

Quick question. Since IDE HDD's have jumpers to control slave/master - what would happen if you had a PC with 3 HDD's (all SATA). How would you select the one to boot from and have the other 2 as extra storage. Let's say we have just the 1 OS (GNU/Linux of course).

---

### Post by ddr3XD on 2012-03-03
> **Rytron said:**
> Thanks guys.

Quick question. Since IDE HDD's have jumpers to control slave/master - what would happen if you had a PC with 3 HDD's (all SATA). How would you select the one to boot from and have the other 2 as extra storage. Let's say we have just the 1 OS (GNU/Linux of course).
your motherboard's BIOS should have the option to set the order of the drives in which to boot from. Also, even if it isn't set correctly it will still boot because after it fails to boot from one of your drives(your storage drives i guess) it will just move on to the other drive until it eventually gets to the bootable drive.

---

### Post by Rytron on 2012-03-03
> **ddr3XD said:**
> your motherboard's BIOS should have the option to set the order of the drives in which to boot from. Also, even if it isn't set correctly it will still boot because after it fails to boot from one of your drives(your storage drives i guess) it will just move on to the other drive until it eventually gets to the bootable drive.

Got it. :)

---

### Post by Bucky Ball on 2012-03-03
Whichever drive has the bootloader (MBR or Master Boot Record) on is the one, with one proviso: you need to set the first drive to boot in the BIOS, and this, naturally, you would set to the one with the MBR, presumably the one with Ubuntu on (although you can install the bootloader to any of the drives, don't: keep it simple).

Hope that helps further. ;)

---

### Post by grahammechanical on 2012-03-03
My motherboard has a bank of six SATA connectors. They are labelled from SATA1 through to SATA6. I only have one SATA hard disk, so which connector do you think that I plugged it into?

Regards.

---

### Post by ddr3XD on 2012-03-03
> **grahammechanical said:**
> My motherboard has a bank of six SATA connectors. They are labelled from SATA1 through to SATA6. I only have one SATA hard disk, so which connector do you think that I plugged it into?

Regards.
Is that a question or statement? i couldn't tell.

If it's a statement then let me also add that: the motherboard does not necessarily boot from the devices in the order that they are plugged into the SATA ports.

If its a question then the port in which you plug the HD into doesn't matter.

---

