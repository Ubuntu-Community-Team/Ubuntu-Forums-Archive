---
title: "scsi tape drive not listed in disk utility"
date: 2011-11-13
forum: Hardware
---

### Post by Fenderian_Mayhew on 2011-11-13
Solved: loaded and ran lsscsi, was shown the device path, and used it to activate the scsi tape drive.

i have an C1537A tape drive atached via an HBA to a 64bit system(maybe an 32 bit OS). the controller is seen by the system but the drive is not listed except in the /Proc/scsi/scsi [COLOR=Blue](In blue)[/COLOR]
mayhew@UMB-1:~$ cat /proc/scsi/scsi 
Attached devices:
[COLOR=Blue]Host: scsi0 Channel: 00 Id: 00 Lun: 00
  Vendor: HP       Model: C1537A           Rev: L411
  Type:   Sequential-Access                ANSI  SCSI revision: 02[/COLOR]
Host: scsi1 Channel: 00 Id: 00 Lun: 00
  Vendor: TSSTcorp Model: CDDVDW SH-S203N  Rev: SB01
  Type:   CD-ROM                           ANSI  SCSI revision: 05
Host: scsi3 Channel: 00 Id: 00 Lun: 00
  Vendor: ATA      Model: WDC WD5000AAKS-0 Rev: 05.0
  Type:   Direct-Access                    ANSI  SCSI revision: 05
Host: scsi5 Channel: 00 Id: 00 Lun: 00
  Vendor: ATA      Model: QUANTUM FIREBALL Rev: APL.
  Type:   Direct-Access                    ANSI  SCSI revision: 05
Host: scsi6 Channel: 00 Id: 00 Lun: 00
  Vendor: ATA      Model: MAXTOR 6L020J1   Rev: A93.
  Type:   Direct-Access                    ANSI  SCSI revision: 05
Host: scsi7 Channel: 00 Id: 00 Lun: 00
  Vendor: Generic  Model: USB SD Reader    Rev: 1.00
  Type:   Direct-Access                    ANSI  SCSI revision: 00
Host: scsi7 Channel: 00 Id: 00 Lun: 01
  Vendor: Generic  Model: USB CF Reader    Rev: 1.01
  Type:   Direct-Access                    ANSI  SCSI revision: 00
Host: scsi7 Channel: 00 Id: 00 Lun: 02
  Vendor: Generic  Model: USB SM Reader    Rev: 1.02
  Type:   Direct-Access                    ANSI  SCSI revision: 00
Host: scsi7 Channel: 00 Id: 00 Lun: 03
  Vendor: Generic  Model: USB MS Reader    Rev: 1.03
  Type:   Direct-Access                    ANSI  SCSI revision: 00
mayhew@UMB-1:~$ 

how do i make the drive useable?
any advice and or sugestions are welecomed and appriciated. 

Thanks
F. mayhew

---

### Post by Fenderian_Mayhew on 2011-11-13
Works perfectly in windows.

---

