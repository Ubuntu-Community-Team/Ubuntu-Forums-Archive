---
title: "SATA drives listed as scsi in /proc/scsi/scsi"
date: 2008-11-29
forum: Hardware
---

### Post by joeboentoe on 2008-11-29
Hello, can someone explain me why my SATA drives and IDE CD/DVD writers are listed as SCSI devices if I do cat /proc/scsi/scsi

cat /proc/scsi/scsi
Attached devices:
Host: scsi0 Channel: 00 Id: 00 Lun: 00
  Vendor: ATA      Model: SAMSUNG SP2004C  Rev: VM10
  Type:   Direct-Access                    ANSI  SCSI revision: 05
Host: scsi1 Channel: 00 Id: 00 Lun: 00
  Vendor: ATA      Model: WDC WD3200AAKS-0 Rev: 12.0
  Type:   Direct-Access                    ANSI  SCSI revision: 05
Host: scsi4 Channel: 00 Id: 00 Lun: 00
  Vendor: AOPEN    Model: CD-RW CRW5224    Rev: 1.06
  Type:   CD-ROM                           ANSI  SCSI revision: 05
Host: scsi4 Channel: 00 Id: 01 Lun: 00
  Vendor: _NEC     Model: DVD_RW ND-2510A  Rev: 2.15
  Type:   CD-ROM                           ANSI  SCSI revision: 05


thanks in advance!

---

### Post by cariboo on 2008-11-29
There is nothing wrong with yor setup here is waht I get when I run  cat /proc/scsi/scsi:

```
 cat /proc/scsi/scsi
Attached devices:
Host: scsi0 Channel: 00 Id: 00 Lun: 00
  Vendor: ATA      Model: HDT722516DLA380  Rev: V43O
  Type:   Direct-Access                    ANSI  SCSI revision: 05
Host: scsi4 Channel: 00 Id: 00 Lun: 00
  Vendor: ATA      Model: ST3250620A       Rev: 3.AA
  Type:   Direct-Access                    ANSI  SCSI revision: 05
Host: scsi5 Channel: 00 Id: 00 Lun: 00
  Vendor: HL-DT-ST Model: DVDRAM GSA-4167B Rev: DL10
  Type:   CD-ROM                           ANSI  SCSI revision: 05
```

Have a look here:

[http://linuxmafia.com/faq/Hardware/sata.html](http://linuxmafia.com/faq/Hardware/sata.html)

for an explanation.

Jim

---

### Post by jmoondoggie on 2010-06-19
That's all well and good, but to get useful info, you need to be able to map the SCSI ID info to the SATA drive location.  If you have multiple sata drives with the same architecture, you can't tell which is which.  There is no serial number info.

Jeff

---

