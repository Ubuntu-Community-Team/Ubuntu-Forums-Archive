---
title: "Failing Harddisk SATA Issues"
date: 2016-06-10
forum: Hardware
---

### Post by M1GEO on 2016-06-10
Hello folks.

**_The Preamble_**

Bit of advice required. I have a failing HDD (probably failed in all honesty) that I'm trying to recover data from. If I connect the drive to a SATA port, I can see it, and mount it read only. I have tried to copy the drive to an image with ddrescue, but, it is taking an amazing amount of time (the drive is 2TB and it's doing about <1kByte/s).

I am currently using `rsync --ignore-errors -rtv /media/crappydrive /media/gooddrive` to copy the data back, but the Kernel is going mad with errors.  The filesystem is in good order aside from the bad blocks, but it appears the drive is timing out or something and the kernel keeps on hard resetting the SATA bus.  Something like:

```
[  +1.071966] ata6: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
[  +1.777824] ata6.00: configured for UDMA/133
[  +0.000015] ata6: EH complete
[  +7.034099] ata6.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6 frozen
[  +0.000008] ata6.00: failed command: SMART
[  +0.000008] ata6.00: cmd b0/da:00:00:4f:c2/00:00:00:00:00/00 tag 7
                       res 40/00:ff:00:00:00/00:00:00:00:00/40 Emask 0x4 (timeout)
[  +0.000004] ata6.00: status: { DRDY }
[  +0.000009] ata6: hard resetting link
[Jun11 02:49] ata6: softreset failed (1st FIS failed)
[  +0.000008] ata6: hard resetting link
[  +9.999770] ata6: softreset failed (1st FIS failed)
[  +0.000010] ata6: hard resetting link
[  +2.919850] ata6: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
[  +1.193028] ata6.00: configured for UDMA/133
[  +0.000015] ata6: EH complete
[Jun11 02:58] ata6.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6 frozen
[  +0.000010] ata6.00: failed command: SMART
[  +0.000010] ata6.00: cmd b0/d0:01:00:4f:c2/00:00:00:00:00/00 tag 29 pio 512 in
                       res 40/00:01:00:4f:c2/00:00:00:00:00/00 Emask 0x4 (timeout)
[  +0.000004] ata6.00: status: { DRDY }
[  +0.000005] ata6: hard resetting link
[  +9.999721] ata6: softreset failed (1st FIS failed)
[  +0.000009] ata6: hard resetting link
[  +9.999734] ata6: softreset failed (1st FIS failed)
[  +0.000008] ata6: hard resetting link

```

This will carry on, working for a while, slowly, copying the files, and resetting the bus - rsync will wait while the bus is reset, and carry on after it returns. However, after a while, it goes mad, and I get something like:

```
[  +0.000002] blk_update_request: I/O error, dev sdk, sector 3509806344
[  +0.000833] sd 5:0:0:0: [sdk] tag#8 FAILED Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
[  +0.000004] sd 5:0:0:0: [sdk] tag#8 CDB: Read(10) 28 00 d1 33 65 08 00 00 08 00
[  +0.000002] blk_update_request: I/O error, dev sdk, sector 3509806344
[  +0.000814] sd 5:0:0:0: [sdk] tag#9 FAILED Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
[  +0.000003] sd 5:0:0:0: [sdk] tag#9 CDB: Read(10) 28 00 d1 33 65 08 00 00 08 00
[  +0.000002] blk_update_request: I/O error, dev sdk, sector 3509806344
[  +6.360839] scsi_io_completion: 5452 callbacks suppressed
[  +0.000010] sd 5:0:0:0: [sdk] tag#6 FAILED Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
[  +0.000006] sd 5:0:0:0: [sdk] tag#6 CDB: Write(10) 2a 00 6e 84 0d 48 00 00 18 00
[  +0.000003] blk_update_request: 5452 callbacks suppressed
[  +0.000003] blk_update_request: I/O error, dev sdk, sector 1854147912
[  +0.000079] Aborting journal on device sdk2-8.

```

and rsync just reports I/O error.

I just want to salvage as much data as is possible. I have the data backed up in several places, so I won't loose it, but it's inconvenient and slow to restore, so I would like to salvage as much as I can. But I can't wait for the 30 days that ddrescue wants to take. I'm not that keen.

**_The Question_**

Is there anything I can tell the Kernel to speed this process up? I assume the OS knows the disc has had it, I'd rather it gave up on dead sectors quickly, and got to those that it can read, rather than hanging on for millions of hours trying to get an extra byte out of a dead sector.

Maximum fast recovery is required.

Suggestions greatly welcomed.

Thanks, all... I know nothing about HDD and that kind of thing...

---

