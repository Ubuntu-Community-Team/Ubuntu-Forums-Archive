---
title: "Are SATA drives supposed to run at 15MB/s?"
date: 2009-09-14
forum: Hardware
---

### Post by stasiana on 2009-09-14
**AN UPDATE**: After some hdparm work, I see that the OS can actually read at about 70MB/s, but the the question becomes:

*Why does copying a 1GB file from one SATA drive to another average about 15MB/s while the raw speed is 70MB/s? Is this normal?*

My hdparm output below:

$ sudo hdparm -i /dev/sda

/dev/sda:

 Model=WDC WD10EACS-00ZJB0                     , FwRev=01.01B01, SerialNo=     WD-WCASJ0417567
 Config={ HardSect NotMFM HdSw>15uSec SpinMotCtl Fixed DTR>5Mbs FmtGapReq }
 RawCHS=16383/16/63, TrkSize=0, SectSize=0, ECCbytes=50
 BuffType=unknown, BuffSize=16384kB, MaxMultSect=16, MultSect=?1?
 CurCHS=16383/16/63, CurSects=16514064, LBA=yes, LBAsects=1953525168
 IORDY=on/off, tPIO={min:120,w/IORDY:120}, tDMA={min:120,rec:120}
 PIO modes:  pio0 pio3 pio4 
 DMA modes:  mdma0 mdma1 mdma2 
 UDMA modes: udma0 udma1 udma2 udma3 udma4 udma5 *udma6 
 AdvancedPM=no WriteCache=enabled
 Drive conforms to: Unspecified:  ATA/ATAPI-1,2,3,4,5,6,7

 * signifies the current active mode

$ sudo hdparm -t --direct /dev/sda

/dev/sda:
 Timing O_DIRECT disk reads:  206 MB in  3.01 seconds =  68.44 MB/sec



Hello folks,

I have Ubuntu 9.04 installed on a computer with a boot PATA drive and 4 ext4 SATA drives for file storage. It's runs on an ASUS M2NPV-VM motherboard.

Does 15MB/s sound right for the transfer speed of SATA drives (e.g. copying a file from one to another)? I read from other postings here that typical speeds are more like 70MB/s. Don't understand why there is such a big difference.

Below is part of the dmesg output describing the drives. Can someone have a look to see if things are set up right? If not, would appreciate suggestions in improving performance.

Thanks.

[    1.394757] sata_nv 0000:00:0e.0: version 3.5
[    1.395055] ACPI: PCI Interrupt Link [APSI] enabled at IRQ 23
[    1.395066] sata_nv 0000:00:0e.0: PCI INT A -> Link[APSI] -> GSI 23 (level, low) -> IRQ 23
[    1.395069] sata_nv 0000:00:0e.0: Using SWNCQ mode
[    1.395117] sata_nv 0000:00:0e.0: setting latency timer to 64
[    1.395250] scsi0 : sata_nv
[    1.395338] scsi1 : sata_nv
[    1.395467] ata1: SATA max UDMA/133 cmd 0x9f0 ctl 0xbf0 bmdma 0xe000 irq 23
[    1.395469] ata2: SATA max UDMA/133 cmd 0x970 ctl 0xb70 bmdma 0xe008 irq 23
[    2.272043] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    2.295012] ata1.00: ATA-8: WDC WD10EACS-00ZJB0, 01.01B01, max UDMA/133
[    2.295015] ata1.00: 1953525168 sectors, multi 1: LBA48 NCQ (depth 31/32)
[    2.308738] ata1.00: configured for UDMA/133
[    3.188041] ata2: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    3.211145] ata2.00: ATA-8: WDC WD10EACS-00ZJB0, 01.01B01, max UDMA/133
[    3.211147] ata2.00: 1953525168 sectors, multi 1: LBA48 NCQ (depth 31/32)
[    3.224436] ata2.00: configured for UDMA/133
[    3.224524] scsi 0:0:0:0: Direct-Access     ATA      WDC WD10EACS-00Z 01.0 PQ: 0 ANSI: 5
[    3.224598] sd 0:0:0:0: [sda] 1953525168 512-byte hardware sectors: (1.00 TB/931 GiB)
[    3.224611] sd 0:0:0:0: [sda] Write Protect is off
[    3.224613] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    3.224631] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    3.224684] sd 0:0:0:0: [sda] 1953525168 512-byte hardware sectors: (1.00 TB/931 GiB)
[    3.224694] sd 0:0:0:0: [sda] Write Protect is off
[    3.224696] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    3.224714] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    3.224717]  sda: sda1
[    3.227710] sd 0:0:0:0: [sda] Attached SCSI disk
[    3.227749] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    3.227795] scsi 1:0:0:0: Direct-Access     ATA      WDC WD10EACS-00Z 01.0 PQ: 0 ANSI: 5
[    3.227853] sd 1:0:0:0: [sdb] 1953525168 512-byte hardware sectors: (1.00 TB/931 GiB)
[    3.227863] sd 1:0:0:0: [sdb] Write Protect is off
[    3.227865] sd 1:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[    3.227882] sd 1:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    3.227920] sd 1:0:0:0: [sdb] 1953525168 512-byte hardware sectors: (1.00 TB/931 GiB)
[    3.227930] sd 1:0:0:0: [sdb] Write Protect is off
[    3.227932] sd 1:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[    3.227948] sd 1:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    3.227951]  sdb: sdb1
[    3.234042] sd 1:0:0:0: [sdb] Attached SCSI disk
[    3.234068] sd 1:0:0:0: Attached scsi generic sg1 type 0

---

