---
title: "SATA 3 SSD errors at boot"
date: 2014-01-19
forum: Hardware
---

### Post by pastim on 2014-01-19
I have acquired a new PC with two SATA 3 6Gb/s SSDs.  The one giving problems is a full SATA drive, the second is mSATA.  When I boot 13.10 I get errors like the ones in amongst the syslog extracts below for ata2, which is the one with 13.10 installed on it and also the EFI boot partition.

If I set the BIOS to use SATA 2 (ie 3Gb/s) I generally get no such messages.

I've had no problems (yet) in normal running.

My question is whether this is likely to be a PC SATA interface issue (there are no SATA cables, the drives plug straight in and have been reseated several times), an SSD hardware or firmware issue, an ubuntu issue, or nothing to worry about!

I have tried various suggested changes, including adding [COLOR=#000000][FONT=Liberation Serif]libata.force=noncq [/FONT][/COLOR]to grub, but this made it worse, and the other SSD got errors as well.[COLOR=#000000][FONT=Liberation Serif]
[/FONT][/COLOR]
```

kernel: [    1.581716] ata2: SATA link up 6.0 Gbps (SStatus 133 SControl 300)
 kernel: [    1.582301] ata2.00: configured for UDMA/133
 kernel: [    1.582311] ata2: EH complete
 kernel: [    1.587246] usb 3-2: New USB device found, idVendor=2109, idProduct=2812
 kernel: [    1.587250] usb 3-2: New USB device strings: Mfr=1, Product=2, SerialNumber=0
 kernel: [    1.587252] usb 3-2: Product: USB2.0 Hub             
 kernel: [    1.587255] usb 3-2: Manufacturer: VIA Labs, Inc.         
 kernel: [    1.587735] hub 3-2:1.0: USB hub found
 kernel: [    1.587850] hub 3-2:1.0: 4 ports detected
 kernel: [    1.594022] EXT4-fs (sda2): mounted filesystem with ordered data mode. Opts: (null)
 kernel: [    1.608752] ata2.00: exception Emask 0x10 SAct 0x7fff8003 SErr 0x280100 action 0x6 frozen
 kernel: [    1.608755] ata2.00: irq_stat 0x08000000, interface fatal error
 kernel: [    1.608757] ata2: SError: { UnrecovData 10B8B BadCRC }
 kernel: [    1.608759] ata2.00: failed command: READ FPDMA QUEUED
 kernel: [    1.608763] ata2.00: cmd 60/08:00:00:8a:de/00:00:02:00:00/40 tag 0 ncq 4096 in
 kernel: [    1.608763]          res 40/00:08:00:89:de/00:00:02:00:00/40 Emask 0x10 (ATA bus error)
 kernel: [    1.608764] ata2.00: status: { DRDY }
 kernel: [    1.608766] ata2.00: failed command: READ FPDMA QUEUED
 kernel: [    1.608768] ata2.00: cmd 60/08:08:00:89:de/00:00:02:00:00/40 tag 1 ncq 4096 in
 kernel: [    1.608768]          res 40/00:08:00:89:de/00:00:02:00:00/40 Emask 0x10 (ATA bus error)
 kernel: [    1.608770] ata2.00: status: { DRDY }
 kernel: [    1.608771] ata2.00: failed command: READ FPDMA QUEUED
 kernel: [    1.608774] ata2.00: cmd 60/08:78:80:89:de/00:00:02:00:00/40 tag 15 ncq 4096 in
 kernel: [    1.608774]          res 40/00:08:00:89:de/00:00:02:00:00/40 Emask 0x10 (ATA bus error)
 kernel: [    1.608775] ata2.00: status: { DRDY }
 kernel: [    1.608776] ata2.00: failed command: READ FPDMA QUEUED
 kernel: [    1.608779] ata2.00: cmd 60/08:80:88:89:de/00:00:02:00:00/40 tag 16 ncq 4096 in
 kernel: [    1.608779]          res 40/00:08:00:89:de/00:00:02:00:00/40 Emask 0x10 (ATA bus error)
 kernel: [    1.608780] ata2.00: status: { DRDY }
 kernel: [    1.608781] ata2.00: failed command: READ FPDMA QUEUED
 kernel: [    1.608783] ata2.00: cmd 60/08:88:90:89:de/00:00:02:00:00/40 tag 17 ncq 4096 in
 kernel: [    1.608783]          res 40/00:08:00:89:de/00:00:02:00:00/40 Emask 0x10 (ATA bus error)
 kernel: [    1.608785] ata2.00: status: { DRDY }
 kernel: [    1.608786] ata2.00: failed command: READ FPDMA QUEUED
 kernel: [    1.608788] ata2.00: cmd 60/08:90:98:89:de/00:00:02:00:00/40 tag 18 ncq 4096 in
 kernel: [    1.608788]          res 40/00:08:00:89:de/00:00:02:00:00/40 Emask 0x10 (ATA bus error)
 kernel: [    1.608790] ata2.00: status: { DRDY }
 kernel: [    1.608791] ata2.00: failed command: READ FPDMA QUEUED
 kernel: [    1.608793] ata2.00: cmd 60/08:98:a0:89:de/00:00:02:00:00/40 tag 19 ncq 4096 in
 kernel: [    1.608793]          res 40/00:08:00:89:de/00:00:02:00:00/40 Emask 0x10 (ATA bus error)
 kernel: [    1.608794] ata2.00: status: { DRDY }
 kernel: [    1.608796] ata2.00: failed command: READ FPDMA QUEUED
 kernel: [    1.608798] ata2.00: cmd 60/08:a0:a8:89:de/00:00:02:00:00/40 tag 20 ncq 4096 in
 kernel: [    1.608798]          res 40/00:08:00:89:de/00:00:02:00:00/40 Emask 0x10 (ATA bus error)
 kernel: [    1.608799] ata2.00: status: { DRDY }
 kernel: [    1.608800] ata2.00: failed command: READ FPDMA QUEUED
 kernel: [    1.608803] ata2.00: cmd 60/08:a8:b0:89:de/00:00:02:00:00/40 tag 21 ncq 4096 in
 kernel: [    1.608803]          res 40/00:08:00:89:de/00:00:02:00:00/40 Emask 0x10 (ATA bus error)
 kernel: [    1.608804] ata2.00: status: { DRDY }
 kernel: [    1.608805] ata2.00: failed command: READ FPDMA QUEUED
 kernel: [    1.608808] ata2.00: cmd 60/08:b0:b8:89:de/00:00:02:00:00/40 tag 22 ncq 4096 in
 kernel: [    1.608808]          res 40/00:08:00:89:de/00:00:02:00:00/40 Emask 0x10 (ATA bus error)
 kernel: [    1.608809] ata2.00: status: { DRDY }
 kernel: [    1.608810] ata2.00: failed command: READ FPDMA QUEUED
 kernel: [    1.608813] ata2.00: cmd 60/08:b8:c0:89:de/00:00:02:00:00/40 tag 23 ncq 4096 in
 kernel: [    1.608813]          res 40/00:08:00:89:de/00:00:02:00:00/40 Emask 0x10 (ATA bus error)
 kernel: [    1.608814] ata2.00: status: { DRDY }
 kernel: [    1.608815] ata2.00: failed command: READ FPDMA QUEUED
 kernel: [    1.608817] ata2.00: cmd 60/08:c0:c8:89:de/00:00:02:00:00/40 tag 24 ncq 4096 in
 kernel: [    1.608817]          res 40/00:08:00:89:de/00:00:02:00:00/40 Emask 0x10 (ATA bus error)
 kernel: [    1.608819] ata2.00: status: { DRDY }
 kernel: [    1.608820] ata2.00: failed command: READ FPDMA QUEUED
 kernel: [    1.608822] ata2.00: cmd 60/08:c8:d0:89:de/00:00:02:00:00/40 tag 25 ncq 4096 in
 kernel: [    1.608822]          res 40/00:08:00:89:de/00:00:02:00:00/40 Emask 0x10 (ATA bus error)
 kernel: [    1.608823] ata2.00: status: { DRDY }
 kernel: [    1.608825] ata2.00: failed command: READ FPDMA QUEUED
 kernel: [    1.608827] ata2.00: cmd 60/08:d0:d8:89:de/00:00:02:00:00/40 tag 26 ncq 4096 in
 kernel: [    1.608827]          res 40/00:08:00:89:de/00:00:02:00:00/40 Emask 0x10 (ATA bus error)
 kernel: [    1.608828] ata2.00: status: { DRDY }
 kernel: [    1.608829] ata2.00: failed command: READ FPDMA QUEUED
 kernel: [    1.608832] ata2.00: cmd 60/08:d8:e0:89:de/00:00:02:00:00/40 tag 27 ncq 4096 in
 kernel: [    1.608832]          res 40/00:08:00:89:de/00:00:02:00:00/40 Emask 0x10 (ATA bus error)
 kernel: [    1.608833] ata2.00: status: { DRDY }
 kernel: [    1.608834] ata2.00: failed command: READ FPDMA QUEUED
 kernel: [    1.608837] ata2.00: cmd 60/08:e0:e8:89:de/00:00:02:00:00/40 tag 28 ncq 4096 in
 kernel: [    1.608837]          res 40/00:08:00:89:de/00:00:02:00:00/40 Emask 0x10 (ATA bus error)
 kernel: [    1.608838] ata2.00: status: { DRDY }
 kernel: [    1.608839] ata2.00: failed command: READ FPDMA QUEUED
 kernel: [    1.608842] ata2.00: cmd 60/08:e8:f0:89:de/00:00:02:00:00/40 tag 29 ncq 4096 in
 kernel: [    1.608842]          res 40/00:08:00:89:de/00:00:02:00:00/40 Emask 0x10 (ATA bus error)
 kernel: [    1.608843] ata2.00: status: { DRDY }
 kernel: [    1.608844] ata2.00: failed command: READ FPDMA QUEUED
 kernel: [    1.608846] ata2.00: cmd 60/08:f0:f8:89:de/00:00:02:00:00/40 tag 30 ncq 4096 in
 kernel: [    1.608846]          res 40/00:08:00:89:de/00:00:02:00:00/40 Emask 0x10 (ATA bus error)
 kernel: [    1.608848] ata2.00: status: { DRDY }
 kernel: [    1.608850] ata2: hard resetting link
 kernel: [    1.761927] usb 3-6: new high-speed USB device number 4 using xhci_hcd
 kernel: [    1.778341] usb 3-6: New USB device found, idVendor=0bda, idProduct=0129
 kernel: [    1.778344] usb 3-6: New USB device strings: Mfr=1, Product=2, SerialNumber=3
 kernel: [    1.778346] usb 3-6: Product: USB2.0-CRW
 kernel: [    1.778347] usb 3-6: Manufacturer: Generic
 kernel: [    1.778348] usb 3-6: SerialNumber: 20100201396000000
 kernel: [    1.930098] ata2: SATA link up 6.0 Gbps (SStatus 133 SControl 300)
 kernel: [    1.930720] ata2.00: configured for UDMA/133
 kernel: [    1.930733] sd 1:0:0:0: [sda]  
 kernel: [    1.930735] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
 kernel: [    1.930736] sd 1:0:0:0: [sda]  
 kernel: [    1.930737] Sense Key : Aborted Command [current] [descriptor]
 kernel: [    1.930739] Descriptor sense data with sense descriptors (in hex):
 kernel: [    1.930740]         72 0b 00 00 00 00 00 0c 00 0a 80 00 00 00 00 00 
 kernel: [    1.930745]         02 de 89 00 
 kernel: [    1.930748] sd 1:0:0:0: [sda]  
 kernel: [    1.930749] Add. Sense: No additional sense information
 kernel: [    1.930750] sd 1:0:0:0: [sda] CDB: 
 kernel: [    1.930751] Read(10): 28 00 02 de 8a 00 00 00 08 00
 kernel: [    1.930756] end_request: I/O error, dev sda, sector 48138752
 kernel: [    1.930765] sd 1:0:0:0: [sda]  
 kernel: [    1.930766] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
 kernel: [    1.930767] sd 1:0:0:0: [sda]  
 kernel: [    1.930768] Sense Key : Aborted Command [current] [descriptor]
 kernel: [    1.930769] Descriptor sense data with sense descriptors (in hex):
 kernel: [    1.930770]         72 0b 00 00 00 00 00 0c 00 0a 80 00 00 00 00 00 
 kernel: [    1.930775]         02 de 89 00 
 kernel: [    1.930777] sd 1:0:0:0: [sda]  
 kernel: [    1.930778] Add. Sense: No additional sense information
 kernel: [    1.930779] sd 1:0:0:0: [sda] CDB: 
 kernel: [    1.930780] Read(10): 28 00 02 de 89 80 00 00 08 00
 kernel: [    1.930784] end_request: I/O error, dev sda, sector 48138624
 kernel: [    1.930787] sd 1:0:0:0: [sda]  
 kernel: [    1.930788] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
 kernel: [    1.930789] sd 1:0:0:0: [sda]  
 kernel: [    1.930790] Sense Key : Aborted Command [current] [descriptor]
 kernel: [    1.930791] Descriptor sense data with sense descriptors (in hex):
 kernel: [    1.930792]         72 0b 00 00 00 00 00 0c 00 0a 80 00 00 00 00 00 
 kernel: [    1.930797]         02 de 89 00 
 kernel: [    1.930799] sd 1:0:0:0: [sda]  
 kernel: [    1.930800] Add. Sense: No additional sense information
 kernel: [    1.930801] sd 1:0:0:0: [sda] CDB: 
 kernel: [    1.930802] Read(10): 28 00 02 de 89 88 00 00 08 00
 kernel: [    1.930806] end_request: I/O error, dev sda, sector 48138632
 kernel: [    1.930808] sd 1:0:0:0: [sda]  
 kernel: [    1.930809] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
 kernel: [    1.930810] sd 1:0:0:0: [sda]  
 kernel: [    1.930810] Sense Key : Aborted Command [current] [descriptor]
 kernel: [    1.930811] Descriptor sense data with sense descriptors (in hex):
 kernel: [    1.930812]         72 0b 00 00 00 00 00 0c 00 0a 80 00 00 00 00 00 
 kernel: [    1.930817]         02 de 89 00 
 kernel: [    1.930819] sd 1:0:0:0: [sda]  
 kernel: [    1.930820] Add. Sense: No additional sense information
 kernel: [    1.930821] sd 1:0:0:0: [sda] CDB: 
 kernel: [    1.930822] Read(10): 28 00 02 de 89 90 00 00 08 00
 kernel: [    1.930826] end_request: I/O error, dev sda, sector 48138640
 kernel: [    1.930828] sd 1:0:0:0: [sda]  
 kernel: [    1.930829] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
 kernel: [    1.930830] sd 1:0:0:0: [sda]  
 kernel: [    1.930831] Sense Key : Aborted Command [current] [descriptor]
 kernel: [    1.930832] Descriptor sense data with sense descriptors (in hex):
 kernel: [    1.930833]         72 0b 00 00 00 00 00 0c 00 0a 80 00 00 00 00 00 
 kernel: [    1.930838]         02 de 89 00 
 kernel: [    1.930840] sd 1:0:0:0: [sda]  
 kernel: [    1.930841] Add. Sense: No additional sense information
 kernel: [    1.930842] sd 1:0:0:0: [sda] CDB: 
 kernel: [    1.930842] Read(10): 28 00 02 de 89 98 00 00 08 00
 kernel: [    1.930846] end_request: I/O error, dev sda, sector 48138648
 kernel: [    1.930848] sd 1:0:0:0: [sda]  
 kernel: [    1.930849] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
 kernel: [    1.930850] sd 1:0:0:0: [sda]  
 kernel: [    1.930851] Sense Key : Aborted Command [current] [descriptor]
 kernel: [    1.930852] Descriptor sense data with sense descriptors (in hex):
 kernel: [    1.930853]         72 0b 00 00 00 00 00 0c 00 0a 80 00 00 00 00 00 
 kernel: [    1.930858]         02 de 89 00 
 kernel: [    1.930860] sd 1:0:0:0: [sda]  
 kernel: [    1.930861] Add. Sense: No additional sense information
 kernel: [    1.930862] sd 1:0:0:0: [sda] CDB: 
 kernel: [    1.930862] Read(10): 28 00 02 de 89 a0 00 00 08 00
 kernel: [    1.930866] end_request: I/O error, dev sda, sector 48138656
 kernel: [    1.930869] sd 1:0:0:0: [sda]  
 kernel: [    1.930870] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
 kernel: [    1.930871] sd 1:0:0:0: [sda]  
 kernel: [    1.930871] Sense Key : Aborted Command [current] [descriptor]
 kernel: [    1.930872] Descriptor sense data with sense descriptors (in hex):
 kernel: [    1.930873]         72 0b 00 00 00 00 00 0c 00 0a 80 00 00 00 00 00 
 kernel: [    1.930878]         02 de 89 00 
 kernel: [    1.930880] sd 1:0:0:0: [sda]  
 kernel: [    1.930881] Add. Sense: No additional sense information
 kernel: [    1.930882] sd 1:0:0:0: [sda] CDB: 
 kernel: [    1.930883] Read(10): 28 00 02 de 89 a8 00 00 08 00
 kernel: [    1.930887] end_request: I/O error, dev sda, sector 48138664
 kernel: [    1.930889] sd 1:0:0:0: [sda]  
 kernel: [    1.930890] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
 kernel: [    1.930891] sd 1:0:0:0: [sda]  

```


```

kernel: [    6.266170] ata2: SATA link up 6.0 Gbps (SStatus 133 SControl 300)
 kernel: [    6.266360] ata2.00: FORCE: horkage modified (noncq)
 kernel: [    6.266475] ata2.00: ATA-9: Samsung SSD 840 EVO 250GB, EXT0BB0Q, max UDMA/133
 kernel: [    6.266477] ata2.00: 488397168 sectors, multi 16: LBA48 NCQ (not used)
 kernel: [    6.266826] ata2.00: configured for UDMA/133
 kernel: [    6.267012] scsi 1:0:0:0: Direct-Access     ATA      Samsung SSD 840  EXT0 PQ: 0 ANSI: 5
 kernel: [    6.267146] sd 1:0:0:0: [sdb] 488397168 512-byte logical blocks: (250 GB/232 GiB)
 kernel: [    6.267150] sd 1:0:0:0: Attached scsi generic sg1 type 0
 kernel: [    6.267298] sd 1:0:0:0: [sdb] Write Protect is off
 kernel: [    6.267301] sd 1:0:0:0: [sdb] Mode Sense: 00 3a 00 00
 kernel: [    6.267341] sd 1:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
 kernel: [    6.268628]  sdb: sdb1 sdb2 sdb6 sdb7
 kernel: [    6.268983] sd 1:0:0:0: [sdb] Attached SCSI disk
 kernel: [    6.586496] ata5: SATA link up 6.0 Gbps (SStatus 133 SControl 300)
 kernel: [    6.586718] ata5.00: FORCE: horkage modified (noncq)
 kernel: [    6.586771] ACPI Error: [DSSP] Namespace lookup failure, AE_NOT_FOUND (20130517/psargs-359)
 kernel: [    6.586775] ACPI Error: Method parse/execution failed [\_SB_.PCI0.SAT0.SPT4._GTF] (Node ffff880214bd9a78), AE_NOT_FOUND (20130517/psparse-536)
 kernel: [    6.586842] ata5.00: supports DRM functions and may not be fully accessible
 kernel: [    6.586844] ata5.00: ATA-9: Crucial_CT240M500SSD3, MU03, max UDMA/133
 kernel: [    6.586846] ata5.00: 468862128 sectors, multi 16: LBA48 NCQ (not used)
 kernel: [    6.590487] ACPI Error: [DSSP] Namespace lookup failure, AE_NOT_FOUND (20130517/psargs-359)
 kernel: [    6.590493] ACPI Error: Method parse/execution failed [\_SB_.PCI0.SAT0.SPT4._GTF] (Node ffff880214bd9a78), AE_NOT_FOUND (20130517/psparse-536)
 kernel: [    6.590555] ata5.00: supports DRM functions and may not be fully accessible
 kernel: [    6.593795] ata5.00: configured for UDMA/133
 kernel: [    6.593958] scsi 4:0:0:0: Direct-Access     ATA      Crucial_CT240M50 MU03 PQ: 0 ANSI: 5
 kernel: [    6.594109] sd 4:0:0:0: Attached scsi generic sg2 type 0
 kernel: [    6.594130] sd 4:0:0:0: [sdc] 468862128 512-byte logical blocks: (240 GB/223 GiB)
 kernel: [    6.594132] sd 4:0:0:0: [sdc] 4096-byte physical blocks
 kernel: [    6.594402] sd 4:0:0:0: [sdc] Write Protect is off
 kernel: [    6.594405] sd 4:0:0:0: [sdc] Mode Sense: 00 3a 00 00
 kernel: [    6.594445] sd 4:0:0:0: [sdc] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
 kernel: [    6.595042]  sdc: sdc1
 kernel: [    6.595352] sd 4:0:0:0: [sdc] Attached SCSI disk
 kernel: [    6.616577] ata2.00: exception Emask 0x10 SAct 0x0 SErr 0x280100 action 0x6 frozen
 kernel: [    6.616579] ata2.00: irq_stat 0x08000000, interface fatal error
 kernel: [    6.616581] ata2: SError: { UnrecovData 10B8B BadCRC }
 kernel: [    6.616583] ata2.00: failed command: READ DMA
 kernel: [    6.616586] ata2.00: cmd c8/00:08:b8:09:00/00:00:00:00:00/e0 tag 0 dma 4096 in
 kernel: [    6.616586]          res 50/00:00:bf:19:ae/00:00:00:00:00/e4 Emask 0x10 (ATA bus error)
 kernel: [    6.616588] ata2.00: status: { DRDY }
 kernel: [    6.616591] ata2: hard resetting link
 kernel: [    6.934904] ata2: SATA link up 6.0 Gbps (SStatus 133 SControl 300)
 kernel: [    6.935526] ata2.00: configured for UDMA/133
 kernel: [    6.935536] ata2: EH complete
 kernel: [    6.951193] EXT4-fs (sdb2): mounted filesystem with ordered data mode. Opts: (null)
 kernel: [    6.967707] ata2.00: exception Emask 0x10 SAct 0x0 SErr 0x280100 action 0x6 frozen
 kernel: [    6.967710] ata2.00: irq_stat 0x08000000, interface fatal error
 kernel: [    6.967712] ata2: SError: { UnrecovData 10B8B BadCRC }
 kernel: [    6.967715] ata2.00: failed command: READ DMA
 kernel: [    6.967718] ata2.00: cmd c8/00:f0:18:89:de/00:00:00:00:00/e2 tag 0 dma 122880 in
 kernel: [    6.967718]          res 50/00:00:17:89:de/00:00:00:00:00/e2 Emask 0x10 (ATA bus error)
 kernel: [    6.967720] ata2.00: status: { DRDY }
 kernel: [    6.967723] ata2: hard resetting link
 kernel: [    7.287292] ata2: SATA link up 6.0 Gbps (SStatus 133 SControl 300)
 kernel: [    7.287804] ata2.00: configured for UDMA/133
 kernel: [    7.287816] sd 1:0:0:0: [sdb]  
 kernel: [    7.287817] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
 kernel: [    7.287819] sd 1:0:0:0: [sdb]  
 kernel: [    7.287820] Sense Key : Aborted Command [current] [descriptor]
 kernel: [    7.287822] Descriptor sense data with sense descriptors (in hex):
 kernel: [    7.287823]         72 0b 00 00 00 00 00 0c 00 0a 80 00 00 00 00 00 
 kernel: [    7.287828]         02 de 89 17 
 kernel: [    7.287831] sd 1:0:0:0: [sdb]  
 kernel: [    7.287832] Add. Sense: No additional sense information
 kernel: [    7.287833] sd 1:0:0:0: [sdb] CDB: 
 kernel: [    7.287834] Read(10): 28 00 02 de 89 18 00 00 f0 00
 kernel: [    7.287839] end_request: I/O error, dev sdb, sector 48138520
 kernel: [    7.287847] ata2: EH complete
 kernel: [    7.288060] ata2.00: exception Emask 0x10 SAct 0x0 SErr 0x280100 action 0x6 frozen
 kernel: [    7.288063] ata2.00: irq_stat 0x08000000, interface fatal error
 kernel: [    7.288066] ata2: SError: { UnrecovData 10B8B BadCRC }
 kernel: [    7.288068] ata2.00: failed command: READ DMA
 kernel: [    7.288071] ata2.00: cmd c8/00:e8:20:89:de/00:00:00:00:00/e2 tag 0 dma 118784 in
 kernel: [    7.288071]          res 50/00:00:6f:59:1c/00:00:1d:00:00/ed Emask 0x10 (ATA bus error)
 kernel: [    7.288073] ata2.00: status: { DRDY }
 kernel: [    7.288076] ata2: hard resetting link
 kernel: [    7.607644] ata2: SATA link up 6.0 Gbps (SStatus 133 SControl 300)
 kernel: [    7.608261] ata2.00: configured for UDMA/133
 kernel: [    7.608271] ata2: EH complete
 kernel: [    7.608500] ata2: limiting SATA link speed to 3.0 Gbps
 kernel: [    7.608504] ata2.00: exception Emask 0x10 SAct 0x0 SErr 0x280100 action 0x6 frozen
 kernel: [    7.608506] ata2.00: irq_stat 0x08000000, interface fatal error
 kernel: [    7.608508] ata2: SError: { UnrecovData 10B8B BadCRC }
 kernel: [    7.608510] ata2.00: failed command: READ DMA
 kernel: [    7.608513] ata2.00: cmd c8/00:e8:20:89:de/00:00:00:00:00/e2 tag 0 dma 118784 in
 kernel: [    7.608513]          res 50/00:00:6f:59:1c/00:00:1d:00:00/ed Emask 0x10 (ATA bus error)
 kernel: [    7.608515] ata2.00: status: { DRDY }
 kernel: [    7.608518] ata2: hard resetting link
 kernel: [    7.927994] ata2: SATA link up 3.0 Gbps (SStatus 123 SControl 320)
 kernel: [    7.928645] ata2.00: configured for UDMA/133
 kernel: [    7.928656] ata2: EH comple


```

---

### Post by pastim on 2014-01-23
I was asked by the PC manufacturer to install Windows and try that.  I did so. 

Since I had already set the disk up with GPT partitions, and UEFI boot, this was actually not too hard (even though some comments on the web indicate it is impossible to add Wwindows after ubuntu).  I just created a new partition, used my Windows 7 disk to boot and set up, and it all worked without destroying ubuntu.  I didn't even really need boot-repair, although I did use it once.

The answer to the question about my SSD is that windows doesn't like the 6G/b/s setting either.

So I have some sort of disk/PC hardware incompatibility problem.

---

