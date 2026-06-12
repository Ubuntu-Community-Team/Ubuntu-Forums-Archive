---
title: "Intel DQ45CB, AHCI and SATA DVD Problems"
date: 2009-03-20
forum: Installation &amp; Upgrades
---

### Post by Krupski on 2009-03-20
Hi all,

The Intel DQ45CB motherboard has only SATA connectors for drive support. Therefore, a CD/DVD drive must be connected to one of the SATA ports.

Now, here's the problem: If the motherboard is set to "NATIVE, AHCI" mode, the DVD drive will not work.

This makes it impossible to install Ubuntu (or even Windows XP) by booting the CD.

Setting the motherboard to "IDE" mode allows the CD/DVD drive to work (and now it will boot Ubuntu or XP), but then the system will be slow due to AHCI not being used.

Note that the CD/DVD drive DOES work in AHCI mode AFTER AHCI drivers are installed (such as running WinXP after having *manually* installed IASTOR.SYS).

I've got older Intel motherboards with AHCI and they seem to have some sort of "AHCI BIOS" which (I'm guessing) provides INT-13 support while the motherboard is in AHCI mode so that a boot process can start (before the AHCI *drivers* get loaded).

For example, I can take a DQ35JO motherboard, set it to AHCI mode and then boot Ubuntu CD from a drive connected to a SATA port.

It seems as though the new DQ45CB board does not have an "INT-13 to AHCI" layer in the bios.

Has anyone run into this problem? If so, is there a solution?

BTW, I flashed the MOBO bios with the newest (version 0075) which is currently only a few days old... so it's not an "old bios" problem.

Any info will be greatly appreciated!

Thanks!

-- Roger

---

### Post by lemming465 on 2009-03-21
Can you do a USB boot/install instead of a CD install?

---

### Post by Krupski on 2009-03-21
> **lemming465 said:**
> Can you do a USB boot/install instead of a CD install?

I could... but that's not the point. 

I should be able to CD boot absolutely any bootable CD I wish. I'm trying to find out if the problem is the computer, just the BIOS or the DVD drive.

Thanks anyway for the suggestion.

-- Roger

---

### Post by Krupski on 2009-03-22
SOLVED!

My problem was that I was using an IDE/ATAPI DVD drive with a SATA to IDE adapter board.

Connecting a native SATA DVD drive to the motherboard made everything work.

---

### Post by ifkm on 2009-04-28
I want to add my experiences with the Intel DQ45CB:

Having the firmware 0059 on it, I could install 08.04.2 without problems (SATA DVD drive working) but not boot.
With IDE mode I couldn't install cause the DVD drive was not found, but I could start booting - but only to an initramfs prompt. 

Updating to new BIOS 0079, AHCI is working fine =)

THe only problematic point now is that the driver for the Ethernet chip has to be compiled by hand. At least with 08.04.2 which I needed for server purposes.

---

