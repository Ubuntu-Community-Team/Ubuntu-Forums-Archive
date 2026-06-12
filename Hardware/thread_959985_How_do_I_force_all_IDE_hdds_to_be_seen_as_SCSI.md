---
title: "How do I force all IDE hdds to be seen as SCSI?"
date: 2008-10-27
forum: Hardware
---

### Post by yongjunj on 2008-10-27
Hi,

I run Hardy on an old box with SOYO KT880 Dragon 2 board that has 2 SATA/PATA controllers: VIA 8237 and ALI M5281. The motherboard has 4 PATA connectors (supporting up to 8 PATA devices) and 4 SATA connectors (for 4 SATA devices).

I had all these connectors populated with PATA and SATA hard disks, but at the moment I only have some PATA drives attached (4 PATA drives on ALI - /dev/hd{a,b,c,d}, 1 PATA drive on VIA - /dev/sda).

I understand how SATA disks appear as SCSI (/dev/sd*), but I'm confused about how the naming works for PATA disks: The PATA drives connected to VIA controller appear as /dev/sd*, but those connected to ALI appear as /dev/hd*. I would like them all to appear as SCSI devices (/dev/sd*) because I want to be able to bring them all up as raw physical disks on my VMware virtual machine.

The following are what I thought were relevant lsmod outputs:

> 
yongjunj@junserver:~$ lsmod | grep ide
ide_disk               17536  0
ide_core              113996  2 ide_disk,alim15x3

yongjunj@junserver:~$ lsmod | grep sd
sd_mod                 30720  3
scsi_mod              151436  3 sg,sd_mod,libata


Presumably, alim15x3 is the ALI driver, and it seems that libata doesn't see it. dmesg shows that the four disks on ALI are assigned their names (hd*) before libata even loads up.

I've attached my dmesg and lshw output; I'd appreciate any help.. Thanks!

---

### Post by yongjunj on 2008-10-28
Building and installing pata_ali module solved the problem.
pata_ali module now replaces the alim15x3, and all drives appear as SCSI drives now :)

---

