---
title: "Missing drive locate after hard shutdown"
date: 2014-02-10
forum: Hardware
---

### Post by dheianevans on 2014-02-10
Woke up this morning to discover my newest drive (1 month) had gone missing. Doing a soft reboot did nothing except toss up a lot of DRDY ERR error messages followed by a failed to mount.

Looking at syslog I saw this earlier today:

Feb 10 06:46:50 buster kernel: [67675.710070] ata6.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
Feb 10 06:46:50 buster kernel: [67675.710079] ata6.00: BMDMA stat 0x25
Feb 10 06:46:50 buster kernel: [67675.710088] ata6.00: failed command: READ DMA EXT
Feb 10 06:46:50 buster kernel: [67675.710103] ata6.00: cmd 25/00:08:88:2d:41/00:00:67:00:00/e0 tag 0 dma 4096 in
Feb 10 06:46:50 buster kernel: [67675.710106]          res 51/04:08:88:2d:41/04:00:67:00:00/e0 Emask 0x1 (device error)
Feb 10 06:46:50 buster kernel: [67675.710114] ata6.00: status: { DRDY ERR }
Feb 10 06:46:50 buster kernel: [67675.710119] ata6.00: error: { ABRT }
Feb 10 06:46:50 buster kernel: [67675.740427] ata6.00: configured for UDMA/133
Feb 10 06:46:50 buster kernel: [67675.740457] ata6: EH complete

I finally wondered if a hard reboot would work. Powered off and started up. It found the drive no problem. The fast (2 min) smarttools test showed no issues. Should I do the full test? What could cause the drive to just "disappear" like that this morning?

Thanks.

---

