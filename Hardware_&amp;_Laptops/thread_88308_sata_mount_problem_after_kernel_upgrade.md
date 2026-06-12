---
title: "sata mount problem after kernel upgrade"
date: 2005-11-09
forum: Hardware &amp; Laptops
---

### Post by haltect on 2005-11-09
hello,

i have upgraded my ubuntu kernel from 2.6.12-9 to 2.6.14 and my sata drive stoped working. i used the same .config with just some changes, but the drive is not functional, i can't mount it:

> 
( halt - ~ )% mount /dev/sda1 /mnt/media/
mount: /dev/sda1 already mounted or /mnt/media/ busy
( halt - ~ )% cd /mnt/media/
( halt - /mnt/media )% ls
( halt - /mnt/media )% umount /dev/sda1
umount: /dev/sda1: not mounted
( halt - ~ )% fdisk -l /dev/sda

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       14593   117218241    c  W95 FAT32 (LBA)




from dmesg..

> 
[4294675.542000] SCSI subsystem initialized
[4294675.543000] libata version 1.12 loaded.
[4294675.544000] ACPI: PCI Interrupt 0000:00:05.0[A] -> GSI 17 (level, low) -> IRQ 22
[4294675.544000] sata_sis: Detected SiS 180/181 chipset in SATA mode
[4294675.544000] ata1: SATA max UDMA/133 cmd 0xEFE0 ctl 0xEFAE bmdma 0xEF90 irq 22
[4294675.544000] ata2: SATA max UDMA/133 cmd 0xEFA0 ctl 0xEFAA bmdma 0xEF98 irq 22
[4294675.749000] ata1: dev 0 cfg 49:2f00 82:346b 83:7d01 84:4003 85:3469 86:3c01 87:4003 88:007f
[4294675.749000] ata1: dev 0 ATA, max UDMA/133, 234441648 sectors: lba48
[4294675.750000] ata1: dev 0 configured for UDMA/133
[4294675.750000] scsi0 : sata_sis
[4294675.952000] ata2: no device found (phy stat 00000000)
[4294675.952000] scsi1 : sata_sis
[4294675.952000]   Vendor: ATA       Model: ST3120827AS       Rev: 3.42
[4294675.952000]   Type:   Direct-Access                      ANSI SCSI revision: 05
[4294678.018000] SCSI device sda: 234441648 512-byte hdwr sectors (120034 MB)
[4294678.018000] SCSI device sda: drive cache: write back
[4294678.018000] SCSI device sda: 234441648 512-byte hdwr sectors (120034 MB)
[4294678.018000] SCSI device sda: drive cache: write back
[4294678.018000]  sda: sda1
[4294678.036000] Attached scsi disk sda at scsi0, channel 0, id 0, lun 0


and this like 20 times

> 
[4294688.046000] device-mapper: error adding target to table
[4294688.053000] device-mapper: dm-linear: Device lookup failed



if i boot with the old kernel it works just fine, it's strange, someone knows what  this problem can be?

thanks in advance, 
h.

---

### Post by Teroedni on 2005-11-10
Your probably are missing the modules required to run s-ata
How have you configured the kernel?
Try again and make sure to check wheter or not you got all the modules you need.

---

### Post by haltect on 2005-11-10
the modules are the same :( 

this is the output with the old kernel

> 
[4294678.102000] SCSI subsystem initialized
[4294678.103000] ACPI: PCI Interrupt 0000:00:05.0[A] -> GSI 17 (level, low) -> IRQ 17
[4294678.103000] ata1: SATA max UDMA/133 cmd 0xEFE0 ctl 0xEFAE bmdma 0xEF90 irq 17
[4294678.103000] ata2: SATA max UDMA/133 cmd 0xEFA0 ctl 0xEFAA bmdma 0xEF98 irq 17
[4294678.308000] ata1: dev 0 ATA, max UDMA/133, 234441648 sectors: lba48
[4294678.308000] ata1: dev 0 configured for UDMA/133
[4294678.308000] scsi0 : sata_sis
[4294678.509000] ata2: no device found (phy stat 00000000)
[4294678.509000] scsi1 : sata_sis
[4294678.509000]   Vendor: ATA       Model: ST3120827AS       Rev: 3.42
[4294678.509000]   Type:   Direct-Access                      ANSI SCSI revision: 05
[4294680.580000] SCSI device sda: 234441648 512-byte hdwr sectors (120034 MB)
[4294680.580000] SCSI device sda: drive cache: write back
[4294680.580000] SCSI device sda: 234441648 512-byte hdwr sectors (120034 MB)
[4294680.580000] SCSI device sda: drive cache: write back
[4294680.580000]  /dev/scsi/host0/bus0/target0/lun0: p1
[4294680.603000] Attached scsi disk sda at scsi0, channel 0, id 0, lun 0


and now i found this errer in another log

> 
evms-engine.log:Nov 10 10:07:58 (none) _5_ Engine: is_object_change_pending: Change pending: Object sda1 needs to be activated.
evms-engine.log:Nov 10 10:07:58 (none) _5_ Engine: is_volume_change_pending: Change pending: Volume /dev/evms/sda1 needs to be activated.


anyone? :)

---

### Post by haltect on 2005-11-10
/dev/evms/sda1 on /mnt/media type vfat (rw)

this way it works :)

---

