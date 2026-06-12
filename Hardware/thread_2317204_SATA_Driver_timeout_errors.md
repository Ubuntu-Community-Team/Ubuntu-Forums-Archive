---
title: "SATA Driver timeout errors"
date: 2016-03-14
forum: Hardware
---

### Post by anath3ma on 2016-03-14
I am currently using Trusty on a banana-pi (sunxi arm) NAS.   Everything works well enough except when I put the drives to sleep.  Upon drive spinup I get errors like the following:

[Fri Feb 26 03:32:57 2016] ata1.00: failed to read SCR 1 (Emask=0x40)
[Fri Feb 26 03:32:57 2016] ata1.01: failed to read SCR 1 (Emask=0x40)
[Fri Feb 26 03:32:57 2016] ata1.15: exception Emask 0x10 SAct 0x0 SErr 0x480101 action 0x6 frozen
[Fri Feb 26 03:32:57 2016] ata1.15: irq_stat 0x08000000, interface fatal error
[Fri Feb 26 03:32:57 2016] ata1.15: SError: { RecovData UnrecovData 10B8B Handshk }
[Fri Feb 26 03:32:57 2016] ata1.00: exception Emask 0x100 SAct 0x4000000 SErr 0x0 action 0x6 frozen
[Fri Feb 26 03:32:57 2016] ata1.00: failed command: READ FPDMA QUEUED
[Fri Feb 26 03:32:57 2016] ata1.00: cmd 60/00:d0:00:8d:94/01:00:f3:00:00/40 tag 26 ncq 131072 in
[Fri Feb 26 03:32:57 2016]          res 40/00:d0:00:8d:94/00:00:f3:00:00/40 Emask 0x100 (unknown error)
[Fri Feb 26 03:32:57 2016] ata1.00: status: { DRDY }
[Fri Feb 26 03:32:57 2016] ata1.01: exception Emask 0x100 SAct 0x0 SErr 0x0 action 0x6 frozen
[Fri Feb 26 03:34:11 2016] ata1.00: failed to read SCR 1 (Emask=0x40)
[Fri Feb 26 03:34:11 2016] ata1.01: failed to read SCR 1 (Emask=0x40)
[Fri Feb 26 03:34:11 2016] ata1.15: exception Emask 0x10 SAct 0x0 SErr 0x680101 action 0x6 frozen
[Fri Feb 26 03:34:11 2016] ata1.15: irq_stat 0x08000000, interface fatal error
[Fri Feb 26 03:34:11 2016] ata1.15: SError: { RecovData UnrecovData 10B8B BadCRC Handshk }
[Fri Feb 26 03:34:11 2016] ata1.00: exception Emask 0x100 SAct 0x18 SErr 0x0 action 0x6 frozen
[Fri Feb 26 03:34:11 2016] ata1.00: failed command: READ FPDMA QUEUED
[Fri Feb 26 03:34:11 2016] ata1.00: cmd 60/00:18:00:d5:79/01:00:f2:00:00/40 tag 3 ncq 131072 in
[Fri Feb 26 03:34:11 2016]          res 40/00:18:00:d5:79/00:00:f2:00:00/40 Emask 0x100 (unknown error)
[Fri Feb 26 03:34:11 2016] ata1.00: status: { DRDY }


If the drives don't spin down, then I get no errors.  It sounds like i am just tripping over a timeout which could be a function of the driver, the SATA controller, or the firmware in my drive (4tb toshibas).  (or a combo of all of them)
Before using the backup drive I have tried to do a:
hdparm -S 0 /dev/disk/by-uuid/myBackupDriveUuid
sleep 1m

But no joy.  The drive spins up waits a minute then has the same errors.

It would be great to save power and spin the drives down as one of them is only used for backup once a week.   What are my options?

Thanks!

---

