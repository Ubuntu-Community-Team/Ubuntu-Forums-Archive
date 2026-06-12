---
title: "SIIG SC-SA0R11-S1 (Marvell 9230) PCIe SATA drives not showing."
date: 2015-05-09
forum: Hardware
---

### Post by herrdoktor330 on 2015-05-09
Hello everyone.

I'm having an issue where two drives, two 750gb Green WD drives, are being undetected on a Marvell 9230 card in Ubuntu 14.04.1. I tried googling the issue and have been coming up bumpkis. Here's some of the commands I know to troubleshoot this.

sudo lspci -v
```

04:00.0 SATA controller: Marvell Technology Group Ltd. 88SE9230 PCIe SATA 6Gb/s Controller (rev 11) (prog-if 01 [AHCI 1.0])
	Subsystem: Marvell Technology Group Ltd. 88SE9230 PCIe SATA 6Gb/s Controller
	Flags: bus master, fast devsel, latency 0, IRQ 64
	I/O ports at c050 [size=8]
	I/O ports at c040 [size=4]
	I/O ports at c030 [size=8]
	I/O ports at c020 [size=4]
	I/O ports at c000 [size=32]
	Memory at fe810000 (32-bit, non-prefetchable) [size=2K]
	Expansion ROM at fe800000 [disabled] [size=64K]
	Capabilities: [40] Power Management version 3
	Capabilities: [50] MSI: Enable+ Count=1/1 Maskable- 64bit-
	Capabilities: [70] Express Legacy Endpoint, MSI 00
	Capabilities: [e0] SATA HBA v0.0
	Capabilities: [100] Advanced Error Reporting
	Kernel driver in use: ahci


```

sudo lshw -class disk
```

  *-disk                  
       description: ATA Disk
       product: ST2000DL004 HD20
       vendor: Seagate
       physical id: 0.0.0
       bus info: scsi@0:0.0.0
       logical name: /dev/sda
       version: 1AQ1
       serial: S2H7J90C623017
       size: 1863GiB (2TB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 sectorsize=512 signature=0000adfe
  *-disk
       description: ATA Disk
       product: WDC WD40EFRX-68W
       vendor: Western Digital
       physical id: 0.0.0
       bus info: scsi@1:0.0.0
       logical name: /dev/sdb
       version: 80.0
       serial: WD-WCC4E0404915
       size: 3726GiB (4TB)
       capabilities: gpt-1.00 partitioned partitioned:gpt
       configuration: ansiversion=5 guid=a3c8dc32-26aa-4c34-addb-5dd118dc674c sectorsize=4096
  *-disk
       description: ATA Disk
       product: SAMSUNG HD204UI
       physical id: 0.0.0
       bus info: scsi@2:0.0.0
       logical name: /dev/sdc
       version: 1AQ1
       serial: S2H7J9EB300851
       size: 1863GiB (2TB)
       capabilities: gpt-1.00 partitioned partitioned:gpt
       configuration: ansiversion=5 guid=4a209ec8-9110-43e9-b0b6-e1f7e17ecddd sectorsize=512
  *-disk
       description: ATA Disk
       product: ST4000VN000-1H41
       vendor: Seagate
       physical id: 0.0.0
       bus info: scsi@3:0.0.0
       logical name: /dev/sdd
       version: SC43
       serial: Z300SVXG
       size: 3726GiB (4TB)
       capabilities: gpt-1.00 partitioned partitioned:gpt
       configuration: ansiversion=5 guid=79604732-72d2-479b-a1f4-7b1d107235a5 sectorsize=4096
  *-disk
       description: ATA Disk
       product: ST4000VN000-1H41
       vendor: Seagate
       physical id: 0.0.0
       bus info: scsi@4:0.0.0
       logical name: /dev/sde
       version: SC43
       serial: Z3012CF7
       size: 3726GiB (4TB)
       capabilities: gpt-1.00 partitioned partitioned:gpt
       configuration: ansiversion=5 guid=d9aeaff8-b119-47f0-a651-e43928ad710e sectorsize=4096
  *-disk
       description: ATA Disk
       product: CT250BX100SSD1
       physical id: 0.0.0
       bus info: scsi@5:0.0.0
       logical name: /dev/sdf
       version: MU01
       serial: 1451F000DC5F
       size: 232GiB (250GB)
       capabilities: gpt-1.00 partitioned partitioned:gpt
       configuration: ansiversion=5 guid=58c87e02-e5bf-4e9a-9bf2-595be41e9b29 sectorsize=512
  *-disk
       description: ATA Disk
       product: ST2000DL004 HD20
       vendor: Seagate
       physical id: 0.0.0
       bus info: scsi@6:0.0.0
       logical name: /dev/sdg
       version: 1AQ1
       serial: S2H7J90C623026
       size: 1863GiB (2TB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 sectorsize=512 signature=0000a729


```

What am I missing to get these drives detected and working on this PCIe card?

---

