---
title: "RAID Failure, is this a bad disk?"
date: 2010-03-26
forum: Hardware
---

### Post by Keithamus on 2010-03-26
Hi all. Woke up this morning to a broken RAID. One of the drives had failed. I rebuild the array, and it got to 44% just now, then I noticed it failed again. I've got a RAID 5 setup with 5x1.5tb disks btw.

This is the relevant part in my kern.log

```

Mar 26 17:38:13 cerberus kernel: [23272.040083] ata4.00: exception Emask 0x40 SAct 0x7 SErr 0x800 action 0x6 frozen
Mar 26 17:38:13 cerberus kernel: [23272.040114] ata4: SError: { HostInt }
Mar 26 17:38:13 cerberus kernel: [23272.040138] ata4.00: cmd 61/00:00:3f:19:aa/02:00:32:00:00/40 tag 0 ncq 262144 out
Mar 26 17:38:13 cerberus kernel: [23272.040141]          res 40/00:14:3f:2f:01/00:00:00:00:00/40 Emask 0x44 (timeout)
Mar 26 17:38:13 cerberus kernel: [23272.040177] ata4.00: status: { DRDY }
Mar 26 17:38:13 cerberus kernel: [23272.040197] ata4.00: cmd 61/00:08:3f:15:aa/04:00:32:00:00/40 tag 1 ncq 524288 out
Mar 26 17:38:13 cerberus kernel: [23272.040200]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x44 (timeout)
Mar 26 17:38:13 cerberus kernel: [23272.040235] ata4.00: status: { DRDY }
Mar 26 17:38:13 cerberus kernel: [23272.040255] ata4.00: cmd 61/00:10:3f:1b:aa/02:00:32:00:00/40 tag 2 ncq 262144 out
Mar 26 17:38:13 cerberus kernel: [23272.040257]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x44 (timeout)
Mar 26 17:38:13 cerberus kernel: [23272.040292] ata4.00: status: { DRDY }
Mar 26 17:38:13 cerberus kernel: [23272.040309] ata4: hard resetting link
Mar 26 17:38:23 cerberus kernel: [23282.050029] ata4: softreset failed (device not ready)
Mar 26 17:38:23 cerberus kernel: [23282.050053] ata4: hard resetting link
Mar 26 17:38:30 cerberus kernel: [23289.180044] ata4: softreset failed (device not ready)
Mar 26 17:38:30 cerberus kernel: [23289.180068] ata4: applying SB600 PMP SRST workaround and retrying
Mar 26 17:38:30 cerberus kernel: [23289.360066] ata4: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
Mar 26 17:38:30 cerberus kernel: [23289.373452] ata4.00: configured for UDMA/133
Mar 26 17:38:30 cerberus kernel: [23289.373464] ata4.00: device reported invalid CHS sector 0
Mar 26 17:38:30 cerberus kernel: [23289.373470] ata4.00: device reported invalid CHS sector 0
Mar 26 17:38:30 cerberus kernel: [23289.373486] ata4: EH complete
Mar 26 19:56:31 cerberus kernel: [31553.040078] ata4.00: exception Emask 0x40 SAct 0x0 SErr 0x800 action 0x6 frozen
Mar 26 19:56:31 cerberus kernel: [31553.040109] ata4: SError: { HostInt }
Mar 26 19:56:31 cerberus kernel: [31553.040131] ata4.00: cmd ea/00:00:00:00:00/00:00:00:00:00/a0 tag 0
Mar 26 19:56:31 cerberus kernel: [31553.040134]          res 40/00:14:3f:2f:01/00:00:00:00:00/40 Emask 0x44 (timeout)
Mar 26 19:56:31 cerberus kernel: [31553.040165] ata4.00: status: { DRDY }
Mar 26 19:56:31 cerberus kernel: [31553.040182] ata4: hard resetting link
Mar 26 19:56:41 cerberus kernel: [31563.050047] ata4: softreset failed (device not ready)
Mar 26 19:56:41 cerberus kernel: [31563.050070] ata4: hard resetting link
Mar 26 19:56:48 cerberus kernel: [31570.420040] ata4: softreset failed (device not ready)
Mar 26 19:56:48 cerberus kernel: [31570.420064] ata4: applying SB600 PMP SRST workaround and retrying
Mar 26 19:56:51 cerberus kernel: [31573.060129] ata4: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
Mar 26 19:56:51 cerberus kernel: [31573.073054] ata4.00: configured for UDMA/133
Mar 26 19:56:51 cerberus kernel: [31573.073085] ata4: EH complete
Mar 26 19:56:51 cerberus kernel: [31573.124775] end_request: I/O error, dev sdd, sector 2930271935
Mar 26 19:56:51 cerberus kernel: [31573.124803] md: super_written gets error=-5, uptodate=0
Mar 26 19:56:51 cerberus kernel: [31573.124811] raid5: Disk failure on sdd1, disabling device.
Mar 26 19:56:51 cerberus kernel: [31573.124813] raid5: Operation continuing on 4 devices.
Mar 26 19:56:51 cerberus kernel: [31573.160115] md: md0: recovery done.
Mar 26 19:56:51 cerberus kernel: [31573.300195] RAID5 conf printout:
Mar 26 19:56:51 cerberus kernel: [31573.300206]  --- rd:5 wd:4
Mar 26 19:56:51 cerberus kernel: [31573.300213]  disk 0, o:1, dev:sdb1
Mar 26 19:56:51 cerberus kernel: [31573.300217]  disk 1, o:1, dev:sdc1
Mar 26 19:56:51 cerberus kernel: [31573.300222]  disk 2, o:0, dev:sdd1
Mar 26 19:56:51 cerberus kernel: [31573.300226]  disk 3, o:1, dev:sde1
Mar 26 19:56:51 cerberus kernel: [31573.300230]  disk 4, o:1, dev:sdf1
Mar 26 19:56:51 cerberus kernel: [31573.300233] RAID5 conf printout:
Mar 26 19:56:51 cerberus kernel: [31573.300236]  --- rd:5 wd:4
Mar 26 19:56:51 cerberus kernel: [31573.300240]  disk 0, o:1, dev:sdb1
Mar 26 19:56:51 cerberus kernel: [31573.300244]  disk 1, o:1, dev:sdc1
Mar 26 19:56:51 cerberus kernel: [31573.300248]  disk 3, o:1, dev:sde1
Mar 26 19:56:51 cerberus kernel: [31573.300252]  disk 4, o:1, dev:sdf1
```

Just wanted to ask anyone with experience of failed disks if this is a failing harddrive, or controller, or if its something else I'm missing? Thanks

---

