---
title: "Xubuntu configure my disk for UDMA33 but I have UDMA100"
date: 2008-02-02
forum: Hardware &amp; Laptops
---

### Post by gacolek on 2008-02-02
Hi everyone,

I have a problem with configure of my HD in Xubuntu. Xubuntu detected my disk as UDMA33 but it is capable of UDMA100. This is message form dmesg | grep ata:
```
[    0.000000]  BIOS-e820: 000000000eff0000 - 000000000effffc0 (ACPI data)
[   14.426348] Memory: 231820k/245696k available (2015k kernel code, 13348k reserved, 916k data, 364k init, 0k highmem)
[   14.426370]       .data : 0xc02f7de6 - 0xc03dce84   ( 916 kB)
[   18.363878] libata version 2.21 loaded.
[    4.144000] ata_piix 0000:00:1f.1: version 2.11
[    4.144000] scsi0 : ata_piix
[    4.144000] scsi1 : ata_piix
[    4.144000] ata1: PATA max UDMA/100 cmd 0x000101f0 ctl 0x000103f6 bmdma 0x00011100 irq 14
[    4.144000] ata2: PATA max UDMA/100 cmd 0x00010170 ctl 0x00010376 bmdma 0x00011108 irq 15
[    4.308000] ata1.00: ATA-6: HTS424040M9AT00, MA2OA71A, max UDMA/100
[    4.308000] ata1.00: 78140160 sectors, multi 16: LBA48 
[    4.308000] ata1.00: limited to UDMA/33 due to 40-wire cable
[    4.324000] ata1.00: configured for UDMA/33
[    4.644000] ata2.00: ATAPI: HL-DT-ST DVDRAM GSA-T10N, PP02, max UDMA/33
[    4.816000] ata2.00: configured for UDMA/33
[    5.636000] EXT3-fs: mounted filesystem with ordered data mode.

```


I try to set this option using hdparm, but i had that kind of error:
```
/dev/sda:
 setting xfermode to 69 (UltraDMA mode5)
SG_IO: bad/missing ATA_16 sense data::  70 00 05 00 00 00 00 0a 00 00 00 00 24 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
 HDIO_DRIVE_CMD(setxfermode) failed: Input/output error

```

My Xubuntu is very slow but I have Acer laptop with Celeron M 1,4GHz, 256MB ram and disk 40GB. On WinXP it works fine and disk work with UDMA100. How to fix this problem, anyone know?

---

### Post by froy02 on 2008-02-02
Change your ribbon cables to the hard drives with the 80-wire cables.  It is the motherboard's IDE controller that limits your transfer speed.  Also If you connect  a UDMA100 hard drive in same cable as a UDMA-33  peripheral like a CD/DVD drive or another old hard drive it would would follow the slower rate of transfer.

---

