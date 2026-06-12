---
title: "[Need Help] Install Qosmio G20-106"
date: 2005-09-01
forum: Hardware &amp; Laptops
---

### Post by madmurphy on 2005-09-01
Hi,

I've like to install my Qosmio with ubuntu but there is no cdrom or Hard-Disk detected.
Are there any modules i could load to get the install to go on?
I think there are also no Hard Disks detected cause of SATA .....

sry for my bad english....
... im a german ....
... but please help me :roll:

---

### Post by Ju. on 2005-10-14
Same here, apparently the installer has issues with the Sata modules :


SCSI subsystem initialized
libata version 1.11 loaded.
ata_piix version 1.03
ACPI: PCI Interrupt 0000:00:1f.2[B] -> GSI 19 (level, low) -> IRQ19
PCI: Setting latency timer of device 000:00:1f.2 to 64
ata1: SATA max UDMA/133 cmd 0x9F98 bmdma 0x9F70 irq 19
ata2: SATA max UDMA/133 cmd 0x9F88 bmdma 0x9F78 irq 19
ATA: abnormal status 0xFF on port 0x9F9F
ata1: disabling port

---

### Post by FritzSolms on 2005-10-19
As far as I know the SATA drivers are not yet enabled in the UBUNTU kernel. I have my G20 going under Gentoo enabled the following two kernel driver options:

     <*>     Include IDE/ATA-2 DISK support                                                 
            [*]     Use multi-mode by default    

Don't know whether this is useful.

---

### Post by Ju. on 2005-10-19
I have to figure out how to boot on a custom kernel but thanks I'll give it a try.

Maybe if I make a module and try to give it at boot...

---

