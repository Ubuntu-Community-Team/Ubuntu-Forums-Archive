---
title: "Esata strange errors"
date: 2012-08-27
forum: Hardware
---

### Post by klepto on 2012-08-27
I've hooked up my external drives to my laptop in Ubuntu via Esata cable. It doesn't automount like usb and I'm getting some strange errors in the log I wonder if someone can make sense out of it. I don't want anything to happen to my drives, so I'm pnoid. 

Monday, August 27, 2012 08:17:01 PM	LUNASYLUM	CRON[15533]	(root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Monday, August 27, 2012 08:46:23 PM	LUNASYLUM	kernel	[23216.157652] ata3: exception Emask 0x10 SAct 0x0 SErr 0x40c0000 action 0xe frozen
Monday, August 27, 2012 08:46:23 PM	LUNASYLUM	kernel	[23216.157663] ata3: irq_stat 0x00000040, connection status changed
Monday, August 27, 2012 08:46:23 PM	LUNASYLUM	kernel	[23216.157672] ata3: SError: { CommWake 10B8B DevExch }
Monday, August 27, 2012 08:46:23 PM	LUNASYLUM	kernel	[23216.157685] ata3: hard resetting link
Monday, August 27, 2012 08:46:33 PM	LUNASYLUM	kernel	[23226.180307] ata3: softreset failed (device not ready)
Monday, August 27, 2012 08:46:33 PM	LUNASYLUM	kernel	[23226.180319] ata3: hard resetting link
Monday, August 27, 2012 08:46:38 PM	LUNASYLUM	kernel	[23230.828337] ata3: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
Monday, August 27, 2012 08:46:38 PM	LUNASYLUM	kernel	[23230.836761] ata3.00: ATA-8: WDC WD1502FAEX-007BA0, 05.01D05, max UDMA/133
Monday, August 27, 2012 08:46:38 PM	LUNASYLUM	kernel	[23230.836772] ata3.00: 2930277168 sectors, multi 0: LBA48 
Monday, August 27, 2012 08:46:38 PM	LUNASYLUM	kernel	[23230.839881] ata3.00: configured for UDMA/133
Monday, August 27, 2012 08:46:38 PM	LUNASYLUM	kernel	[23230.852341] ata3: EH complete
Monday, August 27, 2012 08:46:38 PM	LUNASYLUM	kernel	[23230.852542] scsi 2:0:0:0: Direct-Access     ATA      WDC WD1502FAEX-0 05.0 PQ: 0 ANSI: 5
Monday, August 27, 2012 08:46:38 PM	LUNASYLUM	kernel	[23230.853082] sd 2:0:0:0: [sdc] 2930277168 512-byte logical blocks: (1.50 TB/1.36 TiB)
Monday, August 27, 2012 08:46:38 PM	LUNASYLUM	kernel	[23230.853488] sd 2:0:0:0: [sdc] Write Protect is off
Monday, August 27, 2012 08:46:38 PM	LUNASYLUM	kernel	[23230.853500] sd 2:0:0:0: [sdc] Mode Sense: 00 3a 00 00
Monday, August 27, 2012 08:46:38 PM	LUNASYLUM	kernel	[23230.853846] sd 2:0:0:0: [sdc] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Monday, August 27, 2012 08:46:38 PM	LUNASYLUM	kernel	[23230.853857] sd 2:0:0:0: Attached scsi generic sg3 type 0
Monday, August 27, 2012 08:46:38 PM	LUNASYLUM	kernel	[23230.860644]  sdc: sdc1
Monday, August 27, 2012 08:46:38 PM	LUNASYLUM	kernel	[23230.862377] sd 2:0:0:0: [sdc] Attached SCSI disk
Monday, August 27, 2012 08:47:15 PM	LUNASYLUM	kernel	[23268.243407] EXT4-fs (sdc1): mounted filesystem with ordered data mode. Opts: (null)
Monday, August 27, 2012 08:54:36 PM	LUNASYLUM	kernel	[23708.870453] ata3: exception Emask 0x10 SAct 0x0 SErr 0x90200 action 0xe frozen
Monday, August 27, 2012 08:54:36 PM	LUNASYLUM	kernel	[23708.870464] ata3: irq_stat 0x00400000, PHY RDY changed
Monday, August 27, 2012 08:54:36 PM	LUNASYLUM	kernel	[23708.870473] ata3: SError: { Persist PHYRdyChg 10B8B }
Monday, August 27, 2012 08:54:36 PM	LUNASYLUM	kernel	[23708.870484] ata3: hard resetting link
Monday, August 27, 2012 08:54:37 PM	LUNASYLUM	kernel	[23709.592087] ata3: SATA link down (SStatus 0 SControl 300)
Monday, August 27, 2012 08:54:42 PM	LUNASYLUM	kernel	[23714.592232] ata3: hard resetting link
Monday, August 27, 2012 08:54:42 PM	LUNASYLUM	kernel	[23714.912186] ata3: SATA link down (SStatus 0 SControl 300)
Monday, August 27, 2012 08:54:42 PM	LUNASYLUM	kernel	[23714.912206] ata3: limiting SATA link speed to 1.5 Gbps
Monday, August 27, 2012 08:54:47 PM	LUNASYLUM	kernel	[23719.912121] ata3: hard resetting link
Monday, August 27, 2012 08:54:47 PM	LUNASYLUM	kernel	[23720.232287] ata3: SATA link down (SStatus 0 SControl 310)
Monday, August 27, 2012 08:54:47 PM	LUNASYLUM	kernel	[23720.232305] ata3.00: disabled
Monday, August 27, 2012 08:54:47 PM	LUNASYLUM	kernel	[23720.248338] ata3: EH complete
Monday, August 27, 2012 08:54:47 PM	LUNASYLUM	kernel	[23720.248363] ata3.00: detaching (SCSI 2:0:0:0)
Monday, August 27, 2012 08:54:47 PM	LUNASYLUM	kernel	[23720.251178] sd 2:0:0:0: [sdc] Synchronizing SCSI cache
Monday, August 27, 2012 08:54:47 PM	LUNASYLUM	kernel	[23720.251263] sd 2:0:0:0: [sdc]  Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
Monday, August 27, 2012 08:54:47 PM	LUNASYLUM	kernel	[23720.251274] sd 2:0:0:0: [sdc] Stopping disk
Monday, August 27, 2012 08:54:47 PM	LUNASYLUM	kernel	[23720.251292] sd 2:0:0:0: [sdc] START_STOP FAILED
Monday, August 27, 2012 08:54:47 PM	LUNASYLUM	kernel	[23720.251296] sd 2:0:0:0: [sdc]  Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK

---

