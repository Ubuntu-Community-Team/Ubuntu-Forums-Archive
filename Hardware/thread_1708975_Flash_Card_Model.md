---
title: "Flash Card Model"
date: 2011-03-17
forum: Hardware
---

### Post by frayedknot on 2011-03-17
Hello,

I'm in the process of converting a script that erases a particular model of flash cards.  This script was meant for use in a system that has an ide flash card reader.  I now have a Dell T3500 running Ubuntu 10.10 32bit with a X-in-1 flash card reader which is scsi.  The card is properly automounted by Unbutu from /dev/sdd.

In the old script used to following to get the compact flash card model:
```
cat /proc/ide/hdc/model
```

The particular models that it was looking for was STEC M2+ CF 9.0.2 or SILICONSYSTEMS INC 1GB (not that this is relevant here, but you can see the detail that is needed from the model number).

I'm looking for a way to achieve this using a flash card reader on the scsi bus.  I've tried cat proc, sdparm, and sg_scan.  You can see that it gives the Generic Vendor and Model for the card reader even when a card is inserted and mounted.

```
cat /proc/scsi/scsi
Attached devices:
Host: scsi0 Channel: 00 Id: 00 Lun: 00
  Vendor: ATA      Model: WDC WD1001FAES-7 Rev: 05.0
  Type:   Direct-Access                    ANSI  SCSI revision: 05
Host: scsi0 Channel: 00 Id: 01 Lun: 00
  Vendor: HL-DT-ST Model: DVD-ROM DH30N    Rev: A101
  Type:   CD-ROM                           ANSI  SCSI revision: 05
Host: scsi1 Channel: 00 Id: 00 Lun: 00
  Vendor: ATA      Model: WDC WD1001FAES-7 Rev: 05.0
  Type:   Direct-Access                    ANSI  SCSI revision: 05
Host: scsi4 Channel: 00 Id: 00 Lun: 00
  Vendor: Generic- Model: SD/MMC           Rev: 1.00
  Type:   Direct-Access                    ANSI  SCSI revision: 00
Host: scsi4 Channel: 00 Id: 00 Lun: 01
  Vendor: Generic- Model: Compact Flash    Rev: 1.01
  Type:   Direct-Access                    ANSI  SCSI revision: 00
Host: scsi4 Channel: 00 Id: 00 Lun: 02
  Vendor: Generic- Model: SM/xD Picture    Rev: 1.02
  Type:   Direct-Access                    ANSI  SCSI revision: 00
Host: scsi4 Channel: 00 Id: 00 Lun: 03
  Vendor: Generic- Model: MS/MS-Pro        Rev: 1.03
  Type:   Direct-Access                    ANSI  SCSI revision: 00
Host: scsi5 Channel: 00 Id: 00 Lun: 00
  Vendor: A-DATA   Model: USB Flash Drive  Rev: 0.00
  Type:   Direct-Access                    ANSI  SCSI revision: 02
```

sg_scan shows that the compact flash card port is on /dev/sg4:
```
sg_scan -i
/dev/sg0: scsi0 channel=0 id=0 lun=0 [em]
    ATA       WDC WD1001FAES-7  05.0 [rmb=0 cmdq=0 pqual=0 pdev=0x0] 
/dev/sg1: scsi0 channel=0 id=1 lun=0 [em]
    HL-DT-ST  DVD-ROM DH30N     A101 [rmb=1 cmdq=0 pqual=0 pdev=0x5] 
/dev/sg2: scsi1 channel=0 id=0 lun=0 [em]
    ATA       WDC WD1001FAES-7  05.0 [rmb=0 cmdq=0 pqual=0 pdev=0x0] 
/dev/sg3: scsi4 channel=0 id=0 lun=0 [em]
    Generic-  SD/MMC            1.00 [rmb=1 cmdq=0 pqual=0 pdev=0x0] 
/dev/sg4: scsi4 channel=0 id=0 lun=1 [em]
    Generic-  Compact Flash     1.01 [rmb=1 cmdq=0 pqual=0 pdev=0x0] 
/dev/sg5: scsi4 channel=0 id=0 lun=2 [em]
    Generic-  SM/xD Picture     1.02 [rmb=1 cmdq=0 pqual=0 pdev=0x0] 
/dev/sg6: scsi4 channel=0 id=0 lun=3 [em]
    Generic-  MS/MS-Pro         1.03 [rmb=1 cmdq=0 pqual=0 pdev=0x0] 
/dev/sg7: scsi5 channel=0 id=0 lun=0 [em]
    A-DATA    USB Flash Drive   0.00 [rmb=1 cmdq=0 pqual=0 pdev=0x0] 
```

sg_map shows that /dev/sg4 is mapped to /dev/sdd:
```
sg_map
/dev/sg0  /dev/sda
/dev/sg1  /dev/scd0
/dev/sg2  /dev/sdb
/dev/sg3  /dev/sdc
/dev/sg4  /dev/sdd
/dev/sg5  /dev/sde
/dev/sg6  /dev/sdf
/dev/sg7  /dev/sdg
```

sdparm:
```
root@msp0vlx2-1:~# sdparm /dev/sdd
    /dev/sdd: Generic-  Compact Flash     1.01
```

The system that uses the cards is only compatible with certain models, so that is why I'd like to be able to confirm that the correct flash card is inserted.  Any ideas?

Thanks in advance!

---

### Post by frayedknot on 2011-04-25
I still haven't been able to solve this, although I must admit I have not been able to allocate much time.

Has anyone encountered this?

---

