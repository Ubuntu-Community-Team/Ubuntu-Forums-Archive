---
title: "I need to boot from SCSI (sda) but have OS on IDE (sdb)"
date: 2009-04-10
forum: Installation &amp; Upgrades
---

### Post by OWize1 on 2009-04-10
My old computer has a SCSI 'feature board' that only allows the computer to boot from the 4GB SCSI hard drive and not the 40GB IDE ATA 2nd hard drive. I want to configure the startup (GRUB?) to only boot from SCSI1(0,0,0)sda, but everything else to be installed and operate on the 2nd ATA drive (SCSI2(0,0,0)sdb). And NO, it is not possible to change the BIOS or jumpers on the motherboard or feature board to change the boot drive. Am I making myself clear?

I ran the LiveCD and installed everything on sdb, but now the computer won't boot - "Non-System disk or disk error". I started the installation again and stopped at the partition question as I'm not sure what to do to achieve what I'm looking for.

**How do I configure the partitions and 2 drives to boot from the SCSI drive, but do EVERYTHING else on the 2nd 40GB hard drive?**

Please help me with this remedial question.

---

### Post by Zack McCool on 2009-04-10
> **OWize1 said:**
> My old computer has a SCSI 'feature board' that only allows the computer to boot from the 4GB SCSI hard drive and not the 40GB IDE ATA 2nd hard drive. I want to configure the startup (GRUB?) to only boot from SCSI1(0,0,0)sda, but everything else to be installed and operate on the 2nd ATA drive (SCSI2(0,0,0)sdb). And NO, it is not possible to change the BIOS or jumpers on the motherboard or feature board to change the boot drive. Am I making myself clear?

I ran the LiveCD and installed everything on sdb, but now the computer won't boot - "Non-System disk or disk error". I started the installation again and stopped at the partition question as I'm not sure what to do to achieve what I'm looking for.

Please help me with this remedial question.

You can install it wherever you want, but at the end of the install there is a final dialog with an "Advanced" button.  Click on that and make sure that grub gets installed in the MBR of sda.

---

