---
title: "Where is my SCSI CD Changer?"
date: 2008-03-09
forum: Hardware &amp; Laptops
---

### Post by mjbraun on 2008-03-09
I have a 200-disc, 4 drive JVC CD changer that I can no longer see on my system. Strangely, when I boot up, the changer initializes (which means it has to check every disc slot) I can  see the actual drives in /dev/ but not the changer robot. I need to be able to see the changer device in order to use such tools at MTX. 

mjbraun@ripper:/$ cat /proc/scsi/scsi 
Attached devices:
Host: scsi2 Channel: 00 Id: 02 Lun: 00
  Vendor: PLEXTOR  Model: CD-ROM PX-32CS   Rev: 1.01
  Type:   CD-ROM                           ANSI  SCSI revision: 02
Host: scsi2 Channel: 00 Id: 03 Lun: 00
  Vendor: PLEXTOR  Model: CD-ROM PX-32CS   Rev: 1.01
  Type:   CD-ROM                           ANSI  SCSI revision: 02
Host: scsi2 Channel: 00 Id: 04 Lun: 00
  Vendor: PLEXTOR  Model: CD-ROM PX-32CS   Rev: 1.01
  Type:   CD-ROM                           ANSI  SCSI revision: 02
Host: scsi2 Channel: 00 Id: 05 Lun: 00
  Vendor: PLEXTOR  Model: CD-ROM PX-32CS   Rev: 1.01
  Type:   CD-ROM                           ANSI  SCSI revision: 02
Host: scsi2 Channel: 00 Id: 06 Lun: 00
  Vendor: JVC      Model: CD-CHG MC-1200   Rev: 1.02
  Type:   Medium Changer                   ANSI  SCSI revision: 02


mjbraun@ripper:/$ ls /dev/sg*
/dev/sg0  /dev/sg1  /dev/sg2  /dev/sg3

(There should be a sg4 which would be the changer robot)

dmesg gives:

[   63.365211] sr0: scsi-1 drive
[   63.365294] sr 2:0:2:0: Attached scsi CD-ROM sr0
[   63.373597] sr1: scsi-1 drive
[   63.373700] sr 2:0:3:0: Attached scsi CD-ROM sr1
[   63.382223] sr2: scsi-1 drive
[   63.382315] sr 2:0:4:0: Attached scsi CD-ROM sr2
[   63.390235] sr3: scsi-1 drive
[   63.390323] sr 2:0:5:0: Attached scsi CD-ROM sr3
[   63.405916] sr 2:0:2:0: Attached scsi generic sg0 type 5
[   63.406290] sr 2:0:3:0: Attached scsi generic sg1 type 5
[   63.406657] sr 2:0:4:0: Attached scsi generic sg2 type 5
[   63.407061] sr 2:0:5:0: Attached scsi generic sg3 type 5
[   63.407443] scsi 2:0:6:0: Attached scsi generic sg4 type 8     <------ yet sg4 isn't under /dev
[   63.491941] SCSI Media Changer driver v0.25 
[   63.499124] ch0: type #1 (mt): 0x2000+1 [medium transport]
[   63.499129] ch0: type #2 (st): 0x1+200 [storage]
[   63.499131] ch0: type #3 (ie): 0x4000+1 [import/export]
[   63.499133] ch0: type #4 (dt): 0x3001+4 [data transfer]
[   63.529703] ch0: dt 0x3001: ID 5, LUN 0, name: PLEXTOR  CD-ROM PX-32CS   1.01
[   63.576858] ch0: dt 0x3002: ID 4, LUN 0, name: PLEXTOR  CD-ROM PX-32CS   1.01
[   63.585243] ch0: dt 0x3003: ID 3, LUN 0, name: PLEXTOR  CD-ROM PX-32CS   1.01
[   63.595194] ch0: dt 0x3004: ID 2, LUN 0, name: PLEXTOR  CD-ROM PX-32CS   1.01
[   63.595204] ch0: INITIALIZE ELEMENT STATUS, may take some time ...

Also, what is causing it to initialize? I'd like to stop it from doing that. Any and all help would be greatly appreciated!

This is a stock install of Gutsy.

---

### Post by mjbraun on 2008-03-10
Stranger still, if I rmmod/insmod the sg module, sg4 shows up and works just fine. But why doesn't it behave properly at system boot?

---

