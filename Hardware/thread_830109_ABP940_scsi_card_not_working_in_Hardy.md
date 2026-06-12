---
title: "ABP940 scsi card not working in Hardy"
date: 2008-06-15
forum: Hardware
---

### Post by briggella on 2008-06-15
Tried new install onto Pc with MSI K8NGM-V motherboard using Nforce 4 C51G chipset, ABP940-UW scsi controller, Sil 3114 sata controler and Nvidia Geforce 4 MX440 8x graphics card.

All have worked in other machines with ubuntu.

This machine was built using alternative CD as I wanted raid1 with 2 750Gb drives with samsung HD753J drives. On top of this I created Logical volumes using LVM so quite a complex install but the system worked well.

However I now have problems with my scsi scanner (epson 1640) and a scsi II hard drive. The Iwill ABP940-UW card is recognised in the bios and in lspci but doesn´t work. I have loaded the sg module and the advansys module and recreated my initrd but nothing is seen on lsscsi or sg_utils or sane-find-scanner.

Any ideas as this has worked in every distro for the past 3 years

---

### Post by briggella on 2008-06-15
Correction - it does not appear in lspci. Only recognised on boot when the Bios loads but not in Linux. I have installed the advansys module and run update-initramfs -u to create a new initrd file. The modules are running on bootup but don't appear to work.

---

### Post by briggella on 2008-12-03
Bump

I don't suppose that anyone has any info regarding this card's demise in the Linux world?

---

