---
title: "major issue with hard drive crashes"
date: 2007-09-20
forum: Hardware &amp; Laptops
---

### Post by calypso612 on 2007-09-20
There are random times (I could be sorting through music in amarok) or surfing the web on either firefox or opera. But after a certain random moment in time, the computer stops accepting input (like if I try to add an album cover in amarok or try to download a file of the web or even opening a terminal, everything stops working, however I can still move the mouse around. I can't shutdown though. So I restart and in normal mode I am unable to get into ubuntu, however in recovery mode I can. then I restart into normal mode and everything seems to work again.

Specs on System:
Compal Hel-80
200gig Hitachi SATA hard drive

This is the dmesg output generated from booting through recovery mode:

(Note: [    3.940000] is when things start looking weird sorry about all the output just want to make sure I don't overlook anything)

[    0.383348] checking if image is initramfs... it is
[    0.868910] Freeing initrd memory: 6780k freed
[    0.869179] Simple Boot Flag at 0x36 set to 0x1
[    0.869637] audit: initializing netlink socket (disabled)
[    0.869741] audit(1190221403.528:1): initialized
[    0.869912] highmem bounce pool size: 64 pages
[    0.870068] VFS: Disk quotas dquot_6.5.1
[    0.870170] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.870299] io scheduler noop registered
[    0.870474] io scheduler anticipatory registered
[    0.870637] io scheduler deadline registered
[    0.870808] io scheduler cfq registered (default)
[    0.871262] PCI: Setting latency timer of device 0000:00:01.0 to 64
[    0.871295] assign_interrupt_mode Found MSI capability
[    0.871387] Allocate Port Service[0000:00:01.0:pcie00]
[    0.871464] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[    0.871519] assign_interrupt_mode Found MSI capability
[    0.871609] Allocate Port Service[0000:00:1c.0:pcie00]
[    0.871633] Allocate Port Service[0000:00:1c.0:pcie02]
[    0.871743] PCI: Setting latency timer of device 0000:00:1c.2 to 64
[    0.871798] assign_interrupt_mode Found MSI capability
[    0.871889] Allocate Port Service[0000:00:1c.2:pcie00]
[    0.871913] Allocate Port Service[0000:00:1c.2:pcie02]
[    0.872024] PCI: Setting latency timer of device 0000:00:1c.3 to 64
[    0.872080] assign_interrupt_mode Found MSI capability
[    0.872171] Allocate Port Service[0000:00:1c.3:pcie00]
[    0.872196] Allocate Port Service[0000:00:1c.3:pcie02]
[    0.872350] isapnp: Scanning for PnP cards...
[    1.228502] isapnp: No Plug & Play device found
[    1.244537] Real Time Clock Driver v1.12ac
[    1.244678] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[    1.245282] mice: PS/2 mouse device common for all mice
[    1.245819] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[    1.246034] input: Macintosh mouse button emulation as /class/input/input0
[    1.246153] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[    1.246245] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[    1.246604] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    1.267392] i8042.c: Detected active multiplexing controller, rev 1.1.
[    1.285010] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.285103] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[    1.285196] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[    1.285285] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[    1.285372] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[    1.285524] EISA: Probing bus 0 at eisa.0
[    1.285620] Cannot allocate resource for EISA slot 1
[    1.285712] Cannot allocate resource for EISA slot 2
[    1.285802] Cannot allocate resource for EISA slot 3
[    1.285893] Cannot allocate resource for EISA slot 4
[    1.285999] EISA: Detected 0 cards.
[    1.316117] TCP cubic registered
[    1.316210] NET: Registered protocol family 1
[    1.316315] Starting balanced_irq
[    1.316405] Using IPI No-Shortcut mode
[    1.316571] ACPI: (supports S0 S3 S4 S5)
[    1.317065]   Magic number: 7:761:87
[    1.317195]   hash matches device 0000:00:1c.2:pcie00
[    1.317445] Freeing unused kernel memory: 328k freed
[    1.317691] Time: tsc clocksource has been installed.
[    1.328118] input: AT Translated Set 2 keyboard as /class/input/input1
[    1.463541] Capability LSM initialized
[    1.494150] ACPI (exconfig-0455): Dynamic SSDT Load - OemId [ PmRef] OemTableId [ Cpu0Ist] [20060707]
[    1.494590] ACPI (exconfig-0455): Dynamic SSDT Load - OemId [ PmRef] OemTableId [ Cpu0Cst] [20060707]
[    1.495104] Monitor-Mwait will be used to enter C-1 state
[    1.495106] Monitor-Mwait will be used to enter C-2 state
[    1.495107] Monitor-Mwait will be used to enter C-3 state
[    1.495112] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[    1.495903] ACPI (exconfig-0455): Dynamic SSDT Load - OemId [ PmRef] OemTableId [ Cpu1Ist] [20060707]
[    1.496303] ACPI (exconfig-0455): Dynamic SSDT Load - OemId [ PmRef] OemTableId [ Cpu1Cst] [20060707]
[    1.496864] ACPI: CPU1 (power states: C1[C1] C2[C2] C3[C3])
[    2.032000] Time: hpet clocksource has been installed.
[    2.240000] usbcore: registered new interface driver usbfs
[    2.240000] usbcore: registered new interface driver hub
[    2.240000] usbcore: registered new device driver usb
[    2.244000] USB Universal Host Controller Interface driver v3.0
[    2.244000] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 23 (level, low) -> IRQ 20
[    2.244000] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[    2.244000] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    2.244000] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[    2.244000] uhci_hcd 0000:00:1d.0: irq 20, io base 0x00001800
[    2.244000] usb usb1: configuration #1 chosen from 1 choice
[    2.244000] hub 1-0:1.0: USB hub found
[    2.244000] hub 1-0:1.0: 2 ports detected
[    2.328000] ieee1394: Initialized config rom entry `ip1394'
[    2.348000] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 19 (level, low) -> IRQ 19
[    2.348000] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[    2.348000] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    2.348000] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[    2.348000] uhci_hcd 0000:00:1d.1: irq 19, io base 0x00001820
[    2.348000] usb usb2: configuration #1 chosen from 1 choice
[    2.348000] hub 2-0:1.0: USB hub found
[    2.348000] hub 2-0:1.0: 2 ports detected
[    2.452000] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 18
[    2.452000] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[    2.452000] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    2.452000] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
[    2.452000] uhci_hcd 0000:00:1d.2: irq 18, io base 0x00001840
[    2.452000] usb usb3: configuration #1 chosen from 1 choice
[    2.452000] hub 3-0:1.0: USB hub found
[    2.452000] hub 3-0:1.0: 2 ports detected
[    2.456000] SCSI subsystem initialized
[    2.460000] libata version 2.20 loaded.
[    2.556000] ACPI: PCI Interrupt 0000:00:1d.3[D] -> GSI 16 (level, low) -> IRQ 16
[    2.556000] PCI: Setting latency timer of device 0000:00:1d.3 to 64
[    2.556000] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[    2.556000] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 4
[    2.556000] uhci_hcd 0000:00:1d.3: irq 16, io base 0x00001860
[    2.556000] usb usb4: configuration #1 chosen from 1 choice
[    2.556000] hub 4-0:1.0: USB hub found
[    2.556000] hub 4-0:1.0: 2 ports detected
[    2.660000] ACPI: PCI Interrupt 0000:00:1d.7[A] -> GSI 23 (level, low) -> IRQ 20
[    2.660000] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[    2.660000] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    2.660000] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 5
[    2.660000] ehci_hcd 0000:00:1d.7: debug port 1
[    2.660000] PCI: cache line size of 32 is not supported by device 0000:00:1d.7
[    2.660000] ehci_hcd 0000:00:1d.7: irq 20, io mem 0xd2504000
[    2.664000] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    2.664000] usb usb5: configuration #1 chosen from 1 choice
[    2.664000] hub 5-0:1.0: USB hub found
[    2.664000] hub 5-0:1.0: 8 ports detected
[    2.692000] usb 2-2: new full speed USB device using uhci_hcd and address 2
[    2.768000] r8169 Gigabit Ethernet driver 2.2LK loaded
[    2.768000] ACPI: PCI Interrupt 0000:04:00.0[A] -> GSI 18 (level, low) -> IRQ 18
[    2.768000] PCI: Setting latency timer of device 0000:04:00.0 to 64
[    2.768000] eth0: RTL8168b/8111b at 0xf885c000, 00:16:d4:16:df:5c, IRQ 18
[    2.772000] ACPI: PCI Interrupt 0000:06:00.0[A] -> GSI 20 (level, low) -> IRQ 21
[    2.776000] PCI: Setting latency timer of device 0000:06:00.0 to 64
[    2.828000] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[21]  MMIO=[fabff800-fabfffff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[    2.832000] ata_piix 0000:00:1f.2: version 2.10ac1
[    2.832000] ata_piix 0000:00:1f.2: MAP [ P0 P2 IDE IDE ]
[    2.988000] ACPI: PCI Interrupt 0000:00:1f.2[B] -> GSI 19 (level, low) -> IRQ 19
[    2.988000] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[    2.988000] ata1: SATA max UDMA/133 cmd 0x000101f0 ctl 0x000103f6 bmdma 0x000118b0 irq 14
[    2.988000] ata2: PATA max UDMA/100 cmd 0x00010170 ctl 0x00010376 bmdma 0x000118b8 irq 15
[    2.988000] scsi0 : ata_piix
[    3.124000] usb 5-4: new high speed USB device using ehci_hcd and address 2
[    3.152000] ata1.00: ata_hpa_resize 1: sectors = 390721968, hpa_sectors = 390721968
[    3.152000] ata1.00: ATA-8: Hitachi HTS722020K9SA00, DC4OC50P, max UDMA/133
[    3.152000] ata1.00: 390721968 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    3.160000] ata1.00: ata_hpa_resize 1: sectors = 390721968, hpa_sectors = 390721968
[    3.160000] ata1.00: configured for UDMA/133
[    3.160000] scsi1 : ata_piix
[    3.256000] usb 5-4: configuration #1 chosen from 1 choice
[    3.480000] ata2.00: ATAPI, max UDMA/33
[    3.644000] ata2.00: configured for UDMA/33
[    3.644000] scsi 0:0:0:0: Direct-Access     ATA      Hitachi HTS72202 DC4O PQ: 0 ANSI: 5
[    3.648000] scsi 1:0:0:0: CD-ROM            MATSHITA DVD-RAM UJ-850S  1.50 PQ: 0 ANSI: 5
[    3.656000] SCSI device sda: 390721968 512-byte hdwr sectors (200050 MB)
[    3.656000] sda: Write Protect is off
[    3.656000] sda: Mode Sense: 00 3a 00 00
[    3.656000] SCSI device sda: write cache: disabled, read cache: enabled, doesn't support DPO or FUA
[    3.656000] SCSI device sda: 390721968 512-byte hdwr sectors (200050 MB)
[    3.656000] sda: Write Protect is off
[    3.656000] sda: Mode Sense: 00 3a 00 00
[    3.656000] SCSI device sda: write cache: disabled, read cache: enabled, doesn't support DPO or FUA
[    3.656000]  sda: sda1 sda2 sda3
[    3.692000] sd 0:0:0:0: Attached scsi disk sda
[    3.696000] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    3.696000] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    3.700000] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[    3.700000] Uniform CD-ROM driver Revision: 3.20
[    3.700000] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    3.804000] usb 3-2: new full speed USB device using uhci_hcd and address 2
[    3.940000] Attempting manual resume
[    3.940000] swsusp: Resume From Partition 8:2
[    3.940000] PM: Checking swsusp image.
[    3.940000] PM: Resume from disk failed.
[    3.952000] EXT3-fs: INFO: recovery required on readonly filesystem.
[    3.952000] EXT3-fs: write access will be enabled during recovery.
[    3.968000] usb 3-2: configuration #1 chosen from 1 choice
[    4.104000] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[00023f6793401f28]
[    7.216000] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[    7.220000] ata1.00: (BMDMA stat 0x25)
[    7.220000] ata1.00: cmd c8/00:f8:91:b0:ad/00:00:00:00:00/eb tag 0 cdb 0x0 data 126976 in
[    7.220000]          res 51/40:4d:3c:b1:ad/00:00:00:00:00/eb Emask 0x9 (media error)
[    7.228000] ata1.00: ata_hpa_resize 1: sectors = 390721968, hpa_sectors = 390721968
[    7.236000] ata1.00: ata_hpa_resize 1: sectors = 390721968, hpa_sectors = 390721968
[    7.236000] ata1.00: configured for UDMA/133
[    7.236000] ata1: EH complete
[   10.152000] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[   10.152000] ata1.00: (BMDMA stat 0x25)
[   10.152000] ata1.00: cmd c8/00:f8:91:b0:ad/00:00:00:00:00/eb tag 0 cdb 0x0 data 126976 in
[   10.152000]          res 51/40:4d:3c:b1:ad/00:00:00:00:00/eb Emask 0x9 (media error)
[   10.160000] ata1.00: ata_hpa_resize 1: sectors = 390721968, hpa_sectors = 390721968
[   10.168000] ata1.00: ata_hpa_resize 1: sectors = 390721968, hpa_sectors = 390721968
[   10.168000] ata1.00: configured for UDMA/133
[   10.168000] ata1: EH complete
[   13.068000] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[   13.068000] ata1.00: (BMDMA stat 0x25)
[   13.068000] ata1.00: cmd c8/00:f8:91:b0:ad/00:00:00:00:00/eb tag 0 cdb 0x0 data 126976 in
[   13.068000]          res 51/40:4d:3c:b1:ad/00:00:00:00:00/eb Emask 0x9 (media error)
[   13.076000] ata1.00: ata_hpa_resize 1: sectors = 390721968, hpa_sectors = 390721968
[   13.084000] ata1.00: ata_hpa_resize 1: sectors = 390721968, hpa_sectors = 390721968
[   13.084000] ata1.00: configured for UDMA/133
[   13.084000] ata1: EH complete
[   15.984000] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[   15.984000] ata1.00: (BMDMA stat 0x25)
[   15.984000] ata1.00: cmd c8/00:f8:91:b0:ad/00:00:00:00:00/eb tag 0 cdb 0x0 data 126976 in
[   15.984000]          res 51/40:4d:3c:b1:ad/00:00:00:00:00/eb Emask 0x9 (media error)
[   15.992000] ata1.00: ata_hpa_resize 1: sectors = 390721968, hpa_sectors = 390721968
[   16.000000] ata1.00: ata_hpa_resize 1: sectors = 390721968, hpa_sectors = 390721968
[   16.000000] ata1.00: configured for UDMA/133
[   16.000000] ata1: EH complete
[   18.904000] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[   18.904000] ata1.00: (BMDMA stat 0x25)
[   18.904000] ata1.00: cmd c8/00:f8:91:b0:ad/00:00:00:00:00/eb tag 0 cdb 0x0 data 126976 in
[   18.904000]          res 51/40:4d:3c:b1:ad/00:00:00:00:00/eb Emask 0x9 (media error)
[   18.912000] ata1.00: ata_hpa_resize 1: sectors = 390721968, hpa_sectors = 390721968
[   18.920000] ata1.00: ata_hpa_resize 1: sectors = 390721968, hpa_sectors = 390721968
[   18.920000] ata1.00: configured for UDMA/133
[   18.920000] ata1: EH complete
[   21.828000] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[   21.828000] ata1.00: (BMDMA stat 0x25)
[   21.828000] ata1.00: cmd c8/00:f8:91:b0:ad/00:00:00:00:00/eb tag 0 cdb 0x0 data 126976 in
[   21.828000]          res 51/40:4d:3c:b1:ad/00:00:00:00:00/eb Emask 0x9 (media error)
[   21.836000] ata1.00: ata_hpa_resize 1: sectors = 390721968, hpa_sectors = 390721968
[   21.844000] ata1.00: ata_hpa_resize 1: sectors = 390721968, hpa_sectors = 390721968
[   21.844000] ata1.00: configured for UDMA/133
[   21.844000] sd 0:0:0:0: SCSI error: return code = 0x08000002
[   21.844000] sda: Current [descriptor]: sense key: Medium Error
[   21.844000]     Additional sense: Unrecovered read error - auto reallocate failed
[   21.844000] Descriptor sense data with sense descriptors (in hex):
[   21.844000]         72 03 11 04 00 00 00 0c 00 0a 80 00 00 00 00 00 
[   21.844000]         0b ad b1 3c 
[   21.844000] end_request: I/O error, dev sda, sector 195932476
[   21.844000] ata1: EH complete
[   21.848000] SCSI device sda: 390721968 512-byte hdwr sectors (200050 MB)
[   21.848000] sda: Write Protect is off
[   21.848000] sda: Mode Sense: 00 3a 00 00
[   21.848000] SCSI device sda: write cache: disabled, read cache: enabled, doesn't support DPO or FUA
[   21.856000] SCSI device sda: 390721968 512-byte hdwr sectors (200050 MB)
[   21.860000] sda: Write Protect is off
[   21.860000] sda: Mode Sense: 00 3a 00 00
[   21.860000] SCSI device sda: write cache: disabled, read cache: enabled, doesn't support DPO or FUA
[   25.136000] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[   25.136000] ata1.00: (BMDMA stat 0x25)
[   25.136000] ata1.00: cmd c8/00:20:39:b1:ad/00:00:00:00:00/eb tag 0 cdb 0x0 data 16384 in
[   25.136000]          res 51/40:1d:3c:b1:ad/00:00:00:00:00/eb Emask 0x9 (media error)
[   25.144000] ata1.00: ata_hpa_resize 1: sectors = 390721968, hpa_sectors = 390721968
[   25.152000] ata1.00: ata_hpa_resize 1: sectors = 390721968, hpa_sectors = 390721968
[   25.152000] ata1.00: configured for UDMA/133
[   25.152000] ata1: EH complete
[   28.060000] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[   28.060000] ata1.00: (BMDMA stat 0x25)
[   28.060000] ata1.00: cmd c8/00:20:39:b1:ad/00:00:00:00:00/eb tag 0 cdb 0x0 data 16384 in
[   28.060000]          res 51/40:1d:3c:b1:ad/00:00:00:00:00/eb Emask 0x9 (media error)
[   28.068000] ata1.00: ata_hpa_resize 1: sectors = 390721968, hpa_sectors = 390721968
[   28.076000] ata1.00: ata_hpa_resize 1: sectors = 390721968, hpa_sectors = 390721968
[   28.076000] ata1.00: configured for UDMA/133
[   28.076000] ata1: EH complete
[   30.996000] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[   30.996000] ata1.00: (BMDMA stat 0x25)
[   30.996000] ata1.00: cmd c8/00:20:39:b1:ad/00:00:00:00:00/eb tag 0 cdb 0x0 data 16384 in
[   30.996000]          res 51/40:1d:3c:b1:ad/00:00:00:00:00/eb Emask 0x9 (media error)
[   31.004000] ata1.00: ata_hpa_resize 1: sectors = 390721968, hpa_sectors = 390721968
[   31.012000] ata1.00: ata_hpa_resize 1: sectors = 390721968, hpa_sectors = 390721968
[   31.012000] ata1.00: configured for UDMA/133
[   31.012000] ata1: EH complete
[   33.936000] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[   33.936000] ata1.00: (BMDMA stat 0x25)
[   33.936000] ata1.00: cmd c8/00:20:39:b1:ad/00:00:00:00:00/eb tag 0 cdb 0x0 data 16384 in
[   33.936000]          res 51/40:1d:3c:b1:ad/00:00:00:00:00/eb Emask 0x9 (media error)
[   33.944000] ata1.00: ata_hpa_resize 1: sectors = 390721968, hpa_sectors = 390721968
[   33.952000] ata1.00: ata_hpa_resize 1: sectors = 390721968, hpa_sectors = 390721968
[   33.952000] ata1.00: configured for UDMA/133
[   33.952000] ata1: EH complete
[   36.860000] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[   36.860000] ata1.00: (BMDMA stat 0x25)
[   36.864000] ata1.00: cmd c8/00:20:39:b1:ad/00:00:00:00:00/eb tag 0 cdb 0x0 data 16384 in
[   36.864000]          res 51/40:1d:3c:b1:ad/00:00:00:00:00/eb Emask 0x9 (media error)
[   36.872000] ata1.00: ata_hpa_resize 1: sectors = 390721968, hpa_sectors = 390721968
[   36.880000] ata1.00: ata_hpa_resize 1: sectors = 390721968, hpa_sectors = 390721968
[   36.880000] ata1.00: configured for UDMA/133
[   36.880000] ata1: EH complete
[   39.796000] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[   39.800000] ata1.00: (BMDMA stat 0x25)
[   39.800000] ata1.00: cmd c8/00:20:39:b1:ad/00:00:00:00:00/eb tag 0 cdb 0x0 data 16384 in
[   39.800000]          res 51/40:1d:3c:b1:ad/00:00:00:00:00/eb Emask 0x9 (media error)
[   39.808000] ata1.00: ata_hpa_resize 1: sectors = 390721968, hpa_sectors = 390721968
[   39.816000] ata1.00: ata_hpa_resize 1: sectors = 390721968, hpa_sectors = 390721968
[   39.816000] ata1.00: configured for UDMA/133
[   39.816000] sd 0:0:0:0: SCSI error: return code = 0x08000002
[   39.816000] sda: Current [descriptor]: sense key: Medium Error
[   39.816000]     Additional sense: Unrecovered read error - auto reallocate failed
[   39.816000] Descriptor sense data with sense descriptors (in hex):
[   39.816000]         72 03 11 04 00 00 00 0c 00 0a 80 00 00 00 00 00 
[   39.816000]         0b ad b1 3c 
[   39.816000] end_request: I/O error, dev sda, sector 195932476
[   39.816000] ata1: EH complete
[   39.832000] SCSI device sda: 390721968 512-byte hdwr sectors (200050 MB)
[   39.840000] sda: Write Protect is off
[   39.840000] sda: Mode Sense: 00 3a 00 00
[   39.856000] SCSI device sda: write cache: disabled, read cache: enabled, doesn't support DPO or FUA
[   39.872000] SCSI device sda: 390721968 512-byte hdwr sectors (200050 MB)
[   39.876000] sda: Write Protect is off
[   39.876000] sda: Mode Sense: 00 3a 00 00
[   39.896000] SCSI device sda: write cache: disabled, read cache: enabled, doesn't support DPO or FUA
[   42.732000] kjournald starting.  Commit interval 5 seconds
[   42.732000] EXT3-fs: sda3: orphan cleanup on readonly fs
[   42.732000] ext3_orphan_cleanup: deleting unreferenced inode 2916494
[   42.732000] ext3_orphan_cleanup: deleting unreferenced inode 2916493
[   42.732000] ext3_orphan_cleanup: deleting unreferenced inode 2916492
[   42.732000] ext3_orphan_cleanup: deleting unreferenced inode 2916607
[   42.732000] ext3_orphan_cleanup: deleting unreferenced inode 2916606
[   42.732000] EXT3-fs: sda3: 5 orphan inodes deleted
[   42.732000] EXT3-fs: recovery complete.
[   42.832000] EXT3-fs: mounted filesystem with ordered data mode.
[   50.756000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   50.760000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   50.808000] iTCO_vendor_support: vendor-support=0
[   50.808000] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.01 (11-Nov-2006)
[   50.808000] iTCO_wdt: Found a ICH7-M TCO device (Version=2, TCOBASE=0x1060)
[   50.808000] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   50.944000] intel_rng: FWH not detected
[   50.964000] Yenta: CardBus bridge found at 0000:06:04.0 [14c0:0020]
[   50.964000] Yenta: Using CSCINT to route CSC interrupts to PCI
[   50.964000] Yenta: Routing CardBus interrupts to PCI
[   50.964000] Yenta TI: socket 0000:06:04.0, mfunc 0x88501212, devctl 0x44
[   51.032000] Linux agpgart interface v0.102 (c) Dave Jones
[   51.056000] agpgart: Detected an Intel 945GM Chipset.
[   51.072000] agpgart: AGP aperture is 256M @ 0x0
[   51.104000] tpm_inf_pnp 00:02: Found TPM with ID IFX0102
[   51.104000] tpm_inf_pnp 00:02: TPM found: config base 0x4e, io base 0x1670, chip version 0x000b, vendor id 0x15d1 (Infineon), product id 0x000b (SLB 9635 TT 

I can't tell if this is a Hard drive issue or a hard drive controller issue, or if it's software related. I've run fsck on this drive several times and found no errors. So if anyone has any idea's it would be much appreciated.

---

### Post by dabl on 2007-09-20
I far from an expert -- so don't believe anything I write ...

Here's the first info about your hard drive:

> [ 3.644000] scsi 0:0:0:0: Direct-Access ATA Hitachi HTS72202 DC4O PQ: 0 ANSI: 5
[ 3.648000] scsi 1:0:0:0: CD-ROM MATSHITA DVD-RAM UJ-850S 1.50 PQ: 0 ANSI: 5
[ 3.656000] SCSI device sda: 390721968 512-byte hdwr sectors (200050 MB)
[ 3.656000] sda: Write Protect is off
[ 3.656000] sda: Mode Sense: 00 3a 00 00
[ 3.656000] SCSI device sda: write cache: disabled, read cache: enabled, doesn't support DPO or FUA
[ 3.656000] SCSI device sda: 390721968 512-byte hdwr sectors (200050 MB)
[ 3.656000] sda: Write Protect is off
[ 3.656000] sda: Mode Sense: 00 3a 00 00
[ 3.656000] SCSI device sda: write cache: disabled, read cache: enabled, doesn't support DPO or FUA
[ 3.656000] sda: sda1 sda2 sda3
[ 3.692000] sd 0:0:0:0: Attached scsi disk sda
[ 3.696000] sd 0:0:0:0: Attached scsi generic sg0 type 0

Then later on, I find this, which is not exactly confidence-inspiring:

> [ 7.216000] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[ 7.220000] ata1.00: (BMDMA stat 0x25)
[ 7.220000] ata1.00: cmd c8/00:f8:91:b0:ad/00:00:00:00:00/eb tag 0 cdb 0x0 data 126976 in
[ 7.220000] res 51/40:4d:3c:b1:ad/00:00:00:00:00/eb Emask 0x9 (media error)

Then the entire rest of your output, all the way down to here:

> [ 39.896000] SCSI device sda: write cache: disabled, read cache: enabled, doesn't support DPO or FUA

is just about that hard drive.

I don't have that much dmesg output from FIVE hard drives!  I'm thinking there's a problem with it -- not necessarily that it's broken, but Linux isn't liking it much ... sorry I can't be more specific.  :-({|=

---

### Post by ubuntu_demon on 2007-10-12
calypso612 what version of Ubuntu are you running ?
calypso612 did you figure our whether your harddrive is dying or whether it is some other problem ?

I'm dual-booting Feisty and Gutsy and I might be experiencing a similar problem :
[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/151938](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/151938)
[http://ubuntudemon.wordpress.com/2007/10/12/bug-151938-in-linux-source-2622/](http://ubuntudemon.wordpress.com/2007/10/12/bug-151938-in-linux-source-2622/)

thanks

---

### Post by harjinder1988 on 2008-05-13
I think i have the same problem
have two Ubuntu installations running on my Hard Disk
upgraded gutsy to hardy heron and cant get either of two installations working now.. i fear if its hardware problem


hers d dmesg log


0+ processors (version 2.00.00)
[  627.807833] powernow-k8: MP systems not supported by PSB BIOS structure
[  627.808030] powernow-k8: MP systems not supported by PSB BIOS structure
[  632.805760] lp0: using parport0 (interrupt-driven).
[  633.958279] ppdev: user-space parallel port driver
[  635.268101] eth0: no link during initialization.
[  638.389465] Failure registering capabilities with primary security module.
[  639.292524] Bluetooth: Core ver 2.11
[  639.292683] NET: Registered protocol family 31
[  639.292686] Bluetooth: HCI device and connection manager initialized
[  639.292690] Bluetooth: HCI socket layer initialized
[  639.376389] Bluetooth: L2CAP ver 2.8
[  639.376393] Bluetooth: L2CAP socket layer initialized
[  639.921649] Bluetooth: RFCOMM socket layer initialized
[  639.921669] Bluetooth: RFCOMM TTY layer initialized
[  639.921671] Bluetooth: RFCOMM ver 1.8
[  788.594559] end_request: I/O error, dev fd0, sector 0
[  800.775717] end_request: I/O error, dev fd0, sector 0
[  812.957550] end_request: I/O error, dev fd0, sector 0
[  825.132448] end_request: I/O error, dev fd0, sector 0
[  837.306252] end_request: I/O error, dev fd0, sector 0
[  837.306258] Buffer I/O error on device fd0, logical block 0
[  849.479961] end_request: I/O error, dev fd0, sector 0
[  849.479968] Buffer I/O error on device fd0, logical block 0
[  861.641668] end_request: I/O error, dev fd0, sector 0
[  861.641674] Buffer I/O error on device fd0, logical block 0
[  873.887443] end_request: I/O error, dev fd0, sector 0
[  873.887449] Buffer I/O error on device fd0, logical block 0
[  886.133416] end_request: I/O error, dev fd0, sector 0
[  886.133423] Buffer I/O error on device fd0, logical block 0
[  898.367440] end_request: I/O error, dev fd0, sector 0
[  898.367445] Buffer I/O error on device fd0, logical block 0
[  910.590083] end_request: I/O error, dev fd0, sector 0
[  910.590090] Buffer I/O error on device fd0, logical block 0
[  922.811951] end_request: I/O error, dev fd0, sector 0
[  922.811957] Buffer I/O error on device fd0, logical block 0
[  935.025584] end_request: I/O error, dev fd0, sector 0
[  935.025590] Buffer I/O error on device fd0, logical block 0
[  947.231221] end_request: I/O error, dev fd0, sector 0
[  947.231227] Buffer I/O error on device fd0, logical block 0
[  959.429869] end_request: I/O error, dev fd0, sector 0
[  959.429875] Buffer I/O error on device fd0, logical block 0
[  971.611047] end_request: I/O error, dev fd0, sector 0
[  971.611054] Buffer I/O error on device fd0, logical block 0
[  983.797448] end_request: I/O error, dev fd0, sector 0
[  983.797454] Buffer I/O error on device fd0, logical block 0
[  995.983449] end_request: I/O error, dev fd0, sector 0
[  995.983455] Buffer I/O error on device fd0, logical block 0
[ 1008.173065] end_request: I/O error, dev fd0, sector 0
[ 1008.173071] Buffer I/O error on device fd0, logical block 0
[ 1020.363258] end_request: I/O error, dev fd0, sector 0
[ 1020.363265] Buffer I/O error on device fd0, logical block 0
[ 1032.548839] end_request: I/O error, dev fd0, sector 0
[ 1044.731635] end_request: I/O error, dev fd0, sector 0
[ 1056.917578] end_request: I/O error, dev fd0, sector 0
[ 1069.098891] end_request: I/O error, dev fd0, sector 0
[ 1069.098897] Buffer I/O error on device fd0, logical block 0
[ 1081.272733] end_request: I/O error, dev fd0, sector 0
[ 1081.272740] Buffer I/O error on device fd0, logical block 0
[ 1088.524061] ata2.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[ 1088.524067] ata2.00: (BMDMA stat 0x25)
[ 1088.524072] ata2.00: cmd c8/00:2c:61:00:00/00:00:00:00:00/e0 tag 0
cdb 0x0 data 22528 in
[ 1088.524073]          res 51/40:09:84:00:00/00:00:00:00:00/e0 Emask
0x9 (media error)
[ 1088.547365] ata2.00: configured for UDMA/133
[ 1088.547373] ata2: EH complete
[ 1093.189533] ata2.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[ 1093.189537] ata2.00: (BMDMA stat 0x25)
[ 1093.189541] ata2.00: cmd c8/00:2c:61:00:00/00:00:00:00:00/e0 tag 0
cdb 0x0 data 22528 in
[ 1093.189543]          res 51/40:09:84:00:00/00:00:00:00:00/e0 Emask
0x9 (media error)
[ 1093.214582] ata2.00: configured for UDMA/133
[ 1093.214589] ata2: EH complete
[ 1097.871671] ata2.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[ 1097.871676] ata2.00: (BMDMA stat 0x25)
[ 1097.871681] ata2.00: cmd c8/00:2c:61:00:00/00:00:00:00:00/e0 tag 0
cdb 0x0 data 22528 in
[ 1097.871682]          res 51/40:09:84:00:00/00:00:00:00:00/e0 Emask
0x9 (media error)
[ 1097.893798] ata2.00: configured for UDMA/133
[ 1097.893806] ata2: EH complete
[ 1102.578803] ata2.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[ 1102.578808] ata2.00: (BMDMA stat 0x25)
[ 1102.578812] ata2.00: cmd c8/00:2c:61:00:00/00:00:00:00:00/e0 tag 0
cdb 0x0 data 22528 in
[ 1102.578813]          res 51/40:09:84:00:00/00:00:00:00:00/e0 Emask
0x9 (media error)
[ 1102.601008] ata2.00: configured for UDMA/133
[ 1102.601015] ata2: EH complete
[ 1107.319261] ata2.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[ 1107.319265] ata2.00: (BMDMA stat 0x25)
[ 1107.319269] ata2.00: cmd c8/00:2c:61:00:00/00:00:00:00:00/e0 tag 0
cdb 0x0 data 22528 in
[ 1107.319270]          res 51/40:09:84:00:00/00:00:00:00:00/e0 Emask
0x9 (media error)
[ 1107.340216] ata2.00: configured for UDMA/133
[ 1107.340223] ata2: EH complete
[ 1112.051388] ata2.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[ 1112.051392] ata2.00: (BMDMA stat 0x25)
[ 1112.051397] ata2.00: cmd c8/00:2c:61:00:00/00:00:00:00:00/e0 tag 0
cdb 0x0 data 22528 in
[ 1112.051398]          res 51/40:09:84:00:00/00:00:00:00:00/e0 Emask
0x9 (media error)
[ 1112.075422] ata2.00: configured for UDMA/133
[ 1112.075449] sd 1:0:0:0: [sda] Result: hostbyte=DID_OK
driverbyte=DRIVER_SENSE,SUGGEST_OK
[ 1112.075452] sd 1:0:0:0: [sda] Sense Key : Medium Error [current] [descriptor]
[ 1112.075455] Descriptor sense data with sense descriptors (in hex):
[ 1112.075457]         72 03 11 04 00 00 00 0c 00 0a 80 00 00 00 00 00
[ 1112.075462]         00 00 00 84
[ 1112.075464] sd 1:0:0:0: [sda] Add. Sense: Unrecovered read error -
auto reallocate failed
[ 1112.075468] end_request: I/O error, dev sda, sector 132
[ 1112.075471] Buffer I/O error on device sda1, logical block 34
[ 1112.075474] Buffer I/O error on device sda1, logical block 35
[ 1112.075477] Buffer I/O error on device sda1, logical block 36
[ 1112.075479] Buffer I/O error on device sda1, logical block 37
[ 1112.075481] Buffer I/O error on device sda1, logical block 38
[ 1112.075490] ata2: EH complete
[ 1112.102066] sd 1:0:0:0: [sda] 312581808 512-byte hardware sectors (160042 MB)
[ 1116.758524] ata2.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[ 1116.758529] ata2.00: (BMDMA stat 0x25)
[ 1116.758534] ata2.00: cmd c8/00:04:83:00:00/00:00:00:00:00/e0 tag 0
cdb 0x0 data 2048 in
[ 1116.758535]          res 51/40:03:84:00:00/00:00:00:00:00/e0 Emask
0x9 (media error)
[ 1116.782633] ata2.00: configured for UDMA/133
[ 1116.782642] ata2: EH complete
[ 1121.440661] ata2.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[ 1121.440666] ata2.00: (BMDMA stat 0x25)
[ 1121.440670] ata2.00: cmd c8/00:04:83:00:00/00:00:00:00:00/e0 tag 0
cdb 0x0 data 2048 in
[ 1121.440671]          res 51/40:03:84:00:00/00:00:00:00:00/e0 Emask
0x9 (media error)
[ 1121.461849] ata2.00: configured for UDMA/133
[ 1121.461857] ata2: EH complete
[ 1126.172786] ata2.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[ 1126.172790] ata2.00: (BMDMA stat 0x25)
[ 1126.172795] ata2.00: cmd c8/00:04:83:00:00/00:00:00:00:00/e0 tag 0
cdb 0x0 data 2048 in
[ 1126.172796]          res 51/40:03:84:00:00/00:00:00:00:00/e0 Emask
0x9 (media error)
[ 1126.197056] ata2.00: configured for UDMA/133
[ 1126.197063] ata2: EH complete
[ 1130.921573] ata2.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[ 1130.921576] ata2.00: (BMDMA stat 0x25)
[ 1130.921581] ata2.00: cmd c8/00:04:83:00:00/00:00:00:00:00/e0 tag 0
cdb 0x0 data 2048 in
[ 1130.921582]          res 51/40:03:84:00:00/00:00:00:00:00/e0 Emask
0x9 (media error)
[ 1130.944260] ata2.00: configured for UDMA/133
[ 1130.944266] ata2: EH complete
[ 1135.670363] ata2.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[ 1135.670367] ata2.00: (BMDMA stat 0x25)
[ 1135.670371] ata2.00: cmd c8/00:04:83:00:00/00:00:00:00:00/e0 tag 0
cdb 0x0 data 2048 in
[ 1135.670372]          res 51/40:03:84:00:00/00:00:00:00:00/e0 Emask
0x9 (media error)
[ 1135.691466] ata2.00: configured for UDMA/133
[ 1135.691472] ata2: EH complete
[ 1140.360841] ata2.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[ 1140.360846] ata2.00: (BMDMA stat 0x25)
[ 1140.360851] ata2.00: cmd c8/00:04:83:00:00/00:00:00:00:00/e0 tag 0
cdb 0x0 data 2048 in
[ 1140.360852]          res 51/40:03:84:00:00/00:00:00:00:00/e0 Emask
0x9 (media error)
[ 1140.382678] ata2.00: configured for UDMA/133
[ 1140.382692] sd 1:0:0:0: [sda] Result: hostbyte=DID_OK
driverbyte=DRIVER_SENSE,SUGGEST_OK
[ 1140.382695] sd 1:0:0:0: [sda] Sense Key : Medium Error [current] [descriptor]
[ 1140.382698] Descriptor sense data with sense descriptors (in hex):
[ 1140.382700]         72 03 11 04 00 00 00 0c 00 0a 80 00 00 00 00 00
[ 1140.382704]         00 00 00 84
[ 1140.382707] sd 1:0:0:0: [sda] Add. Sense: Unrecovered read error -
auto reallocate failed
[ 1140.382711] end_request: I/O error, dev sda, sector 132
[ 1140.382714] Buffer I/O error on device sda1, logical block 34
[ 1140.382718] Buffer I/O error on device sda1, logical block 35
[ 1140.382731] ata2: EH complete
[ 1140.385398] sd 1:0:0:0: [sda] Write Protect is off
[ 1140.385401] sd 1:0:0:0: [sda] Mode Sense: 00 3a 00 00
[ 1140.386455] sd 1:0:0:0: [sda] Write cache: enabled, read cache:
enabled, doesn't support DPO or FUA
[ 1140.388260] sd 1:0:0:0: [sda] 312581808 512-byte hardware sectors (160042 MB)
[ 1140.388340] sd 1:0:0:0: [sda] Write Protect is off
[ 1140.388343] sd 1:0:0:0: [sda] Mode Sense: 00 3a 00 00
[ 1140.388755] sd 1:0:0:0: [sda] Write cache: enabled, read cache:
enabled, doesn't support DPO or FUA
[ 1145.134623] ata2.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[ 1145.134628] ata2.00: (BMDMA stat 0x25)
[ 1145.134633] ata2.00: cmd c8/00:3e:61:00:00/00:00:00:00:00/e0 tag 0
cdb 0x0 data 31744 in
[ 1145.134635]          res 51/40:1b:84:00:00/00:00:00:00:00/e0 Emask
0x9 (media error)
[ 1145.169878] ata2.00: configured for UDMA/133
[ 1145.169886] ata2: EH complete
[ 1149.833420] ata2.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[ 1149.833424] ata2.00: (BMDMA stat 0x25)
[ 1149.833429] ata2.00: cmd c8/00:3e:61:00:00/00:00:00:00:00/e0 tag 0
cdb 0x0 data 31744 in
[ 1149.833430]          res 51/40:1b:84:00:00/00:00:00:00:00/e0 Emask
0x9 (media error)
[ 1149.869088] ata2.00: configured for UDMA/133
[ 1149.869097] ata2: EH complete
[ 1154.523890] ata2.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[ 1154.523894] ata2.00: (BMDMA stat 0x25)
[ 1154.523898] ata2.00: cmd c8/00:3e:61:00:00/00:00:00:00:00/e0 tag 0
cdb 0x0 data 31744 in
[ 1154.523899]          res 51/40:1b:84:00:00/00:00:00:00:00/e0 Emask
0x9 (media error)
[ 1154.552302] ata2.00: configured for UDMA/133
[ 1154.552308] ata2: EH complete
[ 1159.239353] ata2.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[ 1159.239357] ata2.00: (BMDMA stat 0x25)
[ 1159.239362] ata2.00: cmd c8/00:3e:61:00:00/00:00:00:00:00/e0 tag 0
cdb 0x0 data 31744 in
[ 1159.239363]          res 51/40:1b:84:00:00/00:00:00:00:00/e0 Emask
0x9 (media error)
[ 1159.267513] ata2.00: configured for UDMA/133
[ 1159.267520] ata2: EH complete
[ 1163.921493] ata2.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[ 1163.921496] ata2.00: (BMDMA stat 0x25)
[ 1163.921501] ata2.00: cmd c8/00:3e:61:00:00/00:00:00:00:00/e0 tag 0
cdb 0x0 data 31744 in
[ 1163.921502]          res 51/40:1b:84:00:00/00:00:00:00:00/e0 Emask
0x9 (media error)
[ 1163.950730] ata2.00: configured for UDMA/133
[ 1163.950737] ata2: EH complete
[ 1168.636957] ata2.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[ 1168.636961] ata2.00: (BMDMA stat 0x25)
[ 1168.636966] ata2.00: cmd c8/00:3e:61:00:00/00:00:00:00:00/e0 tag 0
cdb 0x0 data 31744 in
[ 1168.636967]          res 51/40:1b:84:00:00/00:00:00:00:00/e0 Emask
0x9 (media error)
[ 1168.661940] ata2.00: configured for UDMA/133
[ 1168.661968] sd 1:0:0:0: [sda] Result: hostbyte=DID_OK
driverbyte=DRIVER_SENSE,SUGGEST_OK
[ 1168.661971] sd 1:0:0:0: [sda] Sense Key : Medium Error [current] [descriptor]
[ 1168.661975] Descriptor sense data with sense descriptors (in hex):
[ 1168.661976]         72 03 11 04 00 00 00 0c 00 0a 80 00 00 00 00 00
[ 1168.661981]         00 00 00 84
[ 1168.661983] sd 1:0:0:0: [sda] Add. Sense: Unrecovered read error -
auto reallocate failed
[ 1168.661987] end_request: I/O error, dev sda, sector 132
[ 1168.661990] Buffer I/O error on device sda1, logical block 34
[ 1168.661993] Buffer I/O error on device sda1, logical block 35
[ 1168.661996] Buffer I/O error on device sda1, logical block 36
[ 1168.661999] Buffer I/O error on device sda1, logical block 37
[ 1168.662001] Buffer I/O error on device sda1, logical block 38
[ 1168.662004] Buffer I/O error on device sda1, logical block 39
[ 1168.662006] Buffer I/O error on device sda1, logical block 40
[ 1168.662009] Buffer I/O error on device sda1, logical block 41
[ 1168.662011] Buffer I/O error on device sda1, logical block 42
[ 1168.662013] Buffer I/O error on device sda1, logical block 43
[ 1168.662024] ata2: EH complete
[ 1168.687636] sd 1:0:0:0: [sda] 312581808 512-byte hardware sectors (160042 MB)
[ 1173.352424] ata2.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[ 1173.352429] ata2.00: (BMDMA stat 0x25)
[ 1173.352433] ata2.00: cmd c8/00:04:83:00:00/00:00:00:00:00/e0 tag 0
cdb 0x0 data 2048 in
[ 1173.352435]          res 51/40:03:84:00:00/00:00:00:00:00/e0 Emask
0x9 (media error)
[ 1173.377150] ata2.00: configured for UDMA/133
[ 1173.377158] ata2: EH complete
[ 1178.042893] ata2.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[ 1178.042897] ata2.00: (BMDMA stat 0x25)
[ 1178.042901] ata2.00: cmd c8/00:04:83:00:00/00:00:00:00:00/e0 tag 0
cdb 0x0 data 2048 in
[ 1178.042903]          res 51/40:03:84:00:00/00:00:00:00:00/e0 Emask
0x9 (media error)
[ 1178.068363] ata2.00: configured for UDMA/133
[ 1178.068370] ata2: EH complete
[ 1182.691705] ata2.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[ 1182.691709] ata2.00: (BMDMA stat 0x25)
[ 1182.691713] ata2.00: cmd c8/00:04:83:00:00/00:00:00:00:00/e0 tag 0
cdb 0x0 data 2048 in
[ 1182.691714]          res 51/40:03:84:00:00/00:00:00:00:00/e0 Emask
0x9 (media error)
[ 1182.715584] ata2.00: configured for UDMA/133
[ 1182.715591] ata2: EH complete
[ 1187.348852] ata2.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[ 1187.348856] ata2.00: (BMDMA stat 0x25)
[ 1187.348860] ata2.00: cmd c8/00:04:83:00:00/00:00:00:00:00/e0 tag 0
cdb 0x0 data 2048 in
[ 1187.348861]          res 51/40:03:84:00:00/00:00:00:00:00/e0 Emask
0x9 (media error)
[ 1187.374803] ata2.00: configured for UDMA/133
[ 1187.374810] ata2: EH complete
[ 1192.022660] ata2.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[ 1192.022664] ata2.00: (BMDMA stat 0x25)
[ 1192.022668] ata2.00: cmd c8/00:04:83:00:00/00:00:00:00:00/e0 tag 0
cdb 0x0 data 2048 in
[ 1192.022669]          res 51/40:03:84:00:00/00:00:00:00:00/e0 Emask
0x9 (media error)
[ 1192.050021] ata2.00: configured for UDMA/133
[ 1192.050029] ata2: EH complete
[ 1196.788111] ata2.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[ 1196.788115] ata2.00: (BMDMA stat 0x25)
[ 1196.788119] ata2.00: cmd c8/00:04:83:00:00/00:00:00:00:00/e0 tag 0
cdb 0x0 data 2048 in
[ 1196.788120]          res 51/40:03:84:00:00/00:00:00:00:00/e0 Emask
0x9 (media error)
[ 1196.813223] ata2.00: configured for UDMA/133
[ 1196.813233] sd 1:0:0:0: [sda] Result: hostbyte=DID_OK
driverbyte=DRIVER_SENSE,SUGGEST_OK
[ 1196.813236] sd 1:0:0:0: [sda] Sense Key : Medium Error [current] [descriptor]
[ 1196.813239] Descriptor sense data with sense descriptors (in hex):
[ 1196.813241]         72 03 11 04 00 00 00 0c 00 0a 80 00 00 00 00 00
[ 1196.813246]         00 00 00 84
[ 1196.813248] sd 1:0:0:0: [sda] Add. Sense: Unrecovered read error -
auto reallocate failed
[ 1196.813252] end_request: I/O error, dev sda, sector 132
[ 1196.813254] printk: 4 messages suppressed.
[ 1196.813256] Buffer I/O error on device sda1, logical block 34
[ 1196.813260] Buffer I/O error on device sda1, logical block 35
[ 1196.813270] ata2: EH complete
[ 1196.813441] sd 1:0:0:0: [sda] Write Protect is off
[ 1196.813443] sd 1:0:0:0: [sda] Mode Sense: 00 3a 00 00
[ 1196.815597] sd 1:0:0:0: [sda] Write cache: enabled, read cache:
enabled, doesn't support DPO or FUA
[ 1196.815671] sd 1:0:0:0: [sda] 312581808 512-byte hardware sectors (160042 MB)
[ 1196.815700] sd 1:0:0:0: [sda] Write Protect is off
[ 1196.815702] sd 1:0:0:0: [sda] Mode Sense: 00 3a 00 00
[ 1196.817274] sd 1:0:0:0: [sda] Write cache: enabled, read cache:
enabled, doesn't support DPO or FUA
[ 1262.059457] NET: Registered protocol family 10
[ 1262.059720] lo: Disabled Privacy Extensions
[ 1262.060028] ADDRCONF(NETDEV_UP): eth0: link is not ready
[ 1347.099108] eth0: link up.
[ 1347.099925] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[ 1349.527667] NET: Registered protocol family 17
[ 1352.476281] eth0: link down.
[ 1354.127828] eth0: link up.
[ 1354.128647] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[ 1354.898346] usb 1-5: new full speed USB device using ohci_hcd and address 2
[ 1355.119580] usb 1-5: configuration #2 chosen from 2 choices
[ 1355.302435] eth1: register 'cdc_ether' at usb-0000:00:02.0-5, CDC
Ethernet Device, 00:08:5c:57:53:b7
[ 1355.302452] usbcore: registered new interface driver cdc_ether
[ 1364.596902] eth0: no IPv6 routers present
[ 1386.273159] eth0: no IPv6 routers present
[ 1390.872042] ata2.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[ 1390.872048] ata2.00: (BMDMA stat 0x25)
[ 1390.872054] ata2.00: cmd c8/00:08:7f:00:00/00:00:00:00:00/e0 tag 0
cdb 0x0 data 4096 in
[ 1390.872055]          res 51/40:03:84:00:00/00:00:00:00:00/e0 Emask
0x9 (media error)
[ 1390.896787] ata2.00: configured for UDMA/133
[ 1390.896797] ata2: EH complete
[ 1395.562523] ata2.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[ 1395.562529] ata2.00: (BMDMA stat 0x25)
[ 1395.562535] ata2.00: cmd c8/00:08:7f:00:00/00:00:00:00:00/e0 tag 0
cdb 0x0 data 4096 in
[ 1395.562537]          res 51/40:03:84:00:00/00:00:00:00:00/e0 Emask
0x9 (media error)
[ 1395.584012] ata2.00: configured for UDMA/133
[ 1395.584023] ata2: EH complete
[ 1400.228010] ata2.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[ 1400.228016] ata2.00: (BMDMA stat 0x25)
[ 1400.228022] ata2.00: cmd c8/00:08:7f:00:00/00:00:00:00:00/e0 tag 0
cdb 0x0 data 4096 in
[ 1400.228024]          res 51/40:03:84:00:00/00:00:00:00:00/e0 Emask
0x9 (media error)
[ 1400.251242] ata2.00: configured for UDMA/133
[ 1400.251254] ata2: EH complete
[ 1404.926823] ata2.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[ 1404.926829] ata2.00: (BMDMA stat 0x25)
[ 1404.926834] ata2.00: cmd c8/00:08:7f:00:00/00:00:00:00:00/e0 tag 0
cdb 0x0 data 4096 in
[ 1404.926835]          res 51/40:03:84:00:00/00:00:00:00:00/e0 Emask
0x9 (media error)
[ 1404.950463] ata2.00: configured for UDMA/133
[ 1404.950475] ata2: EH complete
[ 1409.667289] ata2.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[ 1409.667294] ata2.00: (BMDMA stat 0x25)
[ 1409.667300] ata2.00: cmd c8/00:08:7f:00:00/00:00:00:00:00/e0 tag 0
cdb 0x0 data 4096 in
[ 1409.667302]          res 51/40:03:84:00:00/00:00:00:00:00/e0 Emask
0x9 (media error)
[ 1409.689681] ata2.00: configured for UDMA/133
[ 1409.689692] ata2: EH complete
[ 1414.399428] ata2.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[ 1414.399434] ata2.00: (BMDMA stat 0x25)
[ 1414.399439] ata2.00: cmd c8/00:08:7f:00:00/00:00:00:00:00/e0 tag 0
cdb 0x0 data 4096 in
[ 1414.399441]          res 51/40:03:84:00:00/00:00:00:00:00/e0 Emask
0x9 (media error)
[ 1414.420896] ata2.00: configured for UDMA/133
[ 1414.420910] sd 1:0:0:0: [sda] Result: hostbyte=DID_OK
driverbyte=DRIVER_SENSE,SUGGEST_OK
[ 1414.420915] sd 1:0:0:0: [sda] Sense Key : Medium Error [current] [descriptor]
[ 1414.420921] Descriptor sense data with sense descriptors (in hex):
[ 1414.420923]         72 03 11 04 00 00 00 0c 00 0a 80 00 00 00 00 00
[ 1414.420933]         00 00 00 84
[ 1414.420937] sd 1:0:0:0: [sda] Add. Sense: Unrecovered read error -
auto reallocate failed
[ 1414.420943] end_request: I/O error, dev sda, sector 132
[ 1414.420958] ata2: EH complete
[ 1414.421027] EXT3-fs: can't read group descriptor 7
[ 1414.422418] sd 1:0:0:0: [sda] 312581808 512-byte hardware sectors (160042 MB)
[ 1414.423445] sd 1:0:0:0: [sda] Write Protect is off
[ 1414.423449] sd 1:0:0:0: [sda] Mode Sense: 00 3a 00 00
[ 1414.424675] sd 1:0:0:0: [sda] Write cache: enabled, read cache:
enabled, doesn't support DPO or FUA
[ 1414.425388] sd 1:0:0:0: [sda] 312581808 512-byte hardware sectors (160042 MB)
[ 1414.425444] sd 1:0:0:0: [sda] Write Protect is off
[ 1414.425447] sd 1:0:0:0: [sda] Mode Sense: 00 3a 00 00
[ 1414.426160] sd 1:0:0:0: [sda] Write cache: enabled, read cache:
enabled, doesn't support DPO or FUA
[ 1414.584033] kjournald starting.  Commit interval 5 seconds
[ 1414.584173] EXT3 FS on sda3, internal journal
[ 1414.584179] EXT3-fs: mounted filesystem with ordered data mode.
[ 2145.771299] hdb: media error (bad sector): status=0x51 { DriveReady
SeekComplete Error }
[ 2145.771306] hdb: media error (bad sector): error=0x30 {
LastFailedSense=0x03 }
[ 2145.771309] ide: failed opcode was: unknown
[ 2145.771737] hdb: error code: 0x70  sense_key: 0x03  asc: 0x10  ascq: 0x00
[ 2145.771741] end_request: I/O error, dev hdb, sector 1086708
[ 2145.771746] Buffer I/O error on device hdb, logical block 271677
[ 2145.771750] Buffer I/O error on device hdb, logical block 271678
[ 2145.771753] Buffer I/O error on device hdb, logical block 271679
[ 2145.771756] Buffer I/O error on device hdb, logical block 271680
[ 2145.771758] Buffer I/O error on device hdb, logical block 271681
[ 2145.771761] Buffer I/O error on device hdb, logical block 271682
[ 2145.771764] Buffer I/O error on device hdb, logical block 271683
[ 2145.771767] Buffer I/O error on device hdb, logical block 271684
[ 2145.771769] Buffer I/O error on device hdb, logical block 271685
[ 2145.771772] Buffer I/O error on device hdb, logical block 271686
[ 2167.051038] ata2.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[ 2167.051043] ata2.00: (BMDMA stat 0x25)
[ 2167.051048] ata2.00: cmd c8/00:08:7f:00:00/00:00:00:00:00/e0 tag 0
cdb 0x0 data 4096 in
[ 2167.051050]          res 51/40:03:84:00:00/00:00:00:00:00/e0 Emask
0x9 (media error)
[ 2167.076625] ata2.00: configured for UDMA/133
[ 2167.076633] ata2: EH complete
[ 2171.816500] ata2.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[ 2171.816505] ata2.00: (BMDMA stat 0x25)
[ 2171.816511] ata2.00: cmd c8/00:08:7f:00:00/00:00:00:00:00/e0 tag 0
cdb 0x0 data 4096 in
[ 2171.816512]          res 51/40:03:84:00:00/00:00:00:00:00/e0 Emask
0x9 (media error)
[ 2171.839842] ata2.00: configured for UDMA/133
[ 2171.839851] ata2: EH complete
[ 2176.506970] ata2.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[ 2176.506974] ata2.00: (BMDMA stat 0x25)
[ 2176.506978] ata2.00: cmd c8/00:08:7f:00:00/00:00:00:00:00/e0 tag 0
cdb 0x0 data 4096 in
[ 2176.506979]          res 51/40:03:84:00:00/00:00:00:00:00/e0 Emask
0x9 (media error)
[ 2176.531061] ata2.00: configured for UDMA/133
[ 2176.531066] ata2: EH complete
[ 2181.214113] ata2.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[ 2181.214116] ata2.00: (BMDMA stat 0x25)
[ 2181.214120] ata2.00: cmd c8/00:08:7f:00:00/00:00:00:00:00/e0 tag 0
cdb 0x0 data 4096 in
[ 2181.214122]          res 51/40:03:84:00:00/00:00:00:00:00/e0 Emask
0x9 (media error)
[ 2181.238283] ata2.00: configured for UDMA/133
[ 2181.238288] ata2: EH complete
[ 2185.937918] ata2.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[ 2185.937921] ata2.00: (BMDMA stat 0x25)
[ 2185.937925] ata2.00: cmd c8/00:08:7f:00:00/00:00:00:00:00/e0 tag 0
cdb 0x0 data 4096 in
[ 2185.937926]          res 51/40:03:84:00:00/00:00:00:00:00/e0 Emask
0x9 (media error)
[ 2185.961502] ata2.00: configured for UDMA/133
[ 2185.961507] ata2: EH complete
[ 2190.661734] ata2.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[ 2190.661738] ata2.00: (BMDMA stat 0x25)
[ 2190.661743] ata2.00: cmd c8/00:08:7f:00:00/00:00:00:00:00/e0 tag 0
cdb 0x0 data 4096 in
[ 2190.661744]          res 51/40:03:84:00:00/00:00:00:00:00/e0 Emask
0x9 (media error)
[ 2190.684722] ata2.00: configured for UDMA/133
[ 2190.684733] sd 1:0:0:0: [sda] Result: hostbyte=DID_OK
driverbyte=DRIVER_SENSE,SUGGEST_OK
[ 2190.684736] sd 1:0:0:0: [sda] Sense Key : Medium Error [current] [descriptor]
[ 2190.684739] Descriptor sense data with sense descriptors (in hex):
[ 2190.684741]         72 03 11 04 00 00 00 0c 00 0a 80 00 00 00 00 00
[ 2190.684746]         00 00 00 84
[ 2190.684749] sd 1:0:0:0: [sda] Add. Sense: Unrecovered read error -
auto reallocate failed
[ 2190.684753] end_request: I/O error, dev sda, sector 132
[ 2190.684765] ata2: EH complete
[ 2190.684791] EXT3-fs: can't read group descriptor 7
[ 2190.686777] sd 1:0:0:0: [sda] 312581808 512-byte hardware sectors (160042 MB)
[ 2190.686896] sd 1:0:0:0: [sda] Write Protect is off
[ 2190.686898] sd 1:0:0:0: [sda] Mode Sense: 00 3a 00 00
[ 2190.687764] sd 1:0:0:0: [sda] Write cache: enabled, read cache:
enabled, doesn't support DPO or FUA
[ 2190.688180] sd 1:0:0:0: [sda] 312581808 512-byte hardware sectors (160042 MB)
[ 2190.688390] sd 1:0:0:0: [sda] Write Protect is off
[ 2190.688392] sd 1:0:0:0: [sda] Mode Sense: 00 3a 00 00
[ 2190.688815] sd 1:0:0:0: [sda] Write cache: enabled, read cache:
enabled, doesn't support DPO or FUA









plz if neone can help :(

---

