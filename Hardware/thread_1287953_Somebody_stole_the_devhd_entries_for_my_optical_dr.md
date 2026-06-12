---
title: "Somebody stole the /dev/hd* entries for my optical drives"
date: 2009-10-10
forum: Hardware
---

### Post by Cracauer on 2009-10-10
Kind of a problem I would have thought I see, but hey it's the fun in computers, right? :)

I have a computer with a couple SATA harddrives and a couple P-ATA optical drives.

I don't exactly know when it started, but probably since I switched the SATA drives from PIIX to AHCI: my CD-ROM drives on P-ATA now don't get a /dev/hd* entry anymore. They only get a SCSI emulation device, /dev/sr*

The problem I have is that I cannot burn CDs anymore. I can burn DVDs with growisofs but cdrecord is not happy with the /dev/sr* devices and rejects good media (they work on a different computer). I know it worked on this hardware before, but that was when I had /dev/hd* entries.

```

scsi4 : ata_piix
scsi5 : ata_piix
ata5: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0x30b0 irq 14
ata6: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x30b8 irq 15
ata5.00: ATAPI: _NEC DVD_RW ND-3540A, 1.01, max UDMA/33
ata5.01: ATAPI: PIONEER DVD-RW  DVR-112D, 1.09, max UDMA/66
ata5.00: configured for UDMA/33
ata5.01: configured for UDMA/66
ata6: port disabled. ignoring.
scsi 4:0:0:0: CD-ROM            _NEC     DVD_RW ND-3540A  1.01 PQ: 0 ANSI: 5
scsi 4:0:0:0: Attached scsi generic sg4 type 5
scsi 4:0:1:0: CD-ROM            PIONEER  DVD-RW  DVR-112D 1.09 PQ: 0 ANSI: 5
scsi 4:0:1:0: Attached scsi generic sg5 type 5

```

That looks to me as if I should get both /dev entries. SCSI, AHCI and PIIX are all compiled into the kernel (no modules).

Is this a udev problem? Any ideas what could cause this?

This is Debian/stable.

Thanks

---

