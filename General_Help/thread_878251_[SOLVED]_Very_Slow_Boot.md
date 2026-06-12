---
title: "[SOLVED] Very Slow Boot"
date: 2008-08-02
forum: General Help
---

### Post by hundred1906 on 2008-08-02
Dapper Drake. On system start I get various messages ...[OK]
 then "Starting NFS Kernal Utilities [Fail].
 Then more messages .....[OK].
 Then I get the message "Starting NFS Kernal daemon" 
at which point the startup hangs for a long while (like 4 Minutes).

Eventually the boot completes. What is holding it back, this appeared to start happening after an update? I can't recall do anything that might have caused it.

Also, but this might be a separate problem, the system pretty much hangs  after I try to switch user.

Thanks

---

### Post by spiderbatdad on 2008-08-02
check ```
dmesg
```upgrade to 8.04 with a clean install?

---

### Post by hundred1906 on 2008-08-03
Currently running Ubuntu 8.04.1 - with the slow boot.

---

### Post by hundred1906 on 2008-08-06
Finally understood what DMSEG mean't

[   26.332046] ACPI: (supports S0 S1 S3 S4 S5)
[   26.332065] ACPI: Using IOAPIC for interrupt routing
[   26.339348] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   26.339976] PCI quirk: region 0800-087f claimed by ICH6 ACPI/GPIO/TCO
[   26.339980] PCI quirk: region 0480-04bf claimed by ICH6 GPIO
[   26.340961] PCI: Transparent bridge - 0000:00:1e.0
[   26.340999] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   26.341139] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P2._PRT]
[   26.341207] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P1._PRT]
[   26.341350] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P4._PRT]
[   26.341432] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P5._PRT]
[   26.341510] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P6._PRT]
[   26.344495] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 *10 11 12 14 15)
[   26.344609] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 *5 6 7 10 11 12 14 15)
[   26.344719] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 10 *11 12 14 15)
[   26.344829] ACPI: PCI Interrupt Link [LNKD] (IRQs *3 4 5 6 7 10 11 12 14 15)
[   26.344939] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 *5 6 7 10 11 12 14 15)
[   26.345049] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[   26.345160] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[   26.345272] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 *5 6 7 10 11 12 14 15)
[   26.345416] ACPI Warning (tbutils-0217): Incorrect checksum in table [OEMB] -  BB, should be AE [20070126]
[   26.345424] Linux Plug and Play Support v0.97 (c) Adam Belay
[   26.345466] pnp: PnP ACPI init
[   26.345476] ACPI: bus type pnp registered
[   26.350222] pnp: PnP ACPI: found 18 devices
[   26.350225] ACPI: ACPI bus type pnp unregistered
[   26.350229] PnPBIOS: Disabled by ACPI PNP
[   26.350524] PCI: Using ACPI for IRQ routing
[   26.350528] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   26.375901] NET: Registered protocol family 8
[   26.375903] NET: Registered protocol family 20
[   26.375978] AppArmor: AppArmor Filesystem Enabled
[   26.379897] Time: tsc clocksource has been installed.
[   26.391963] system 00:01: iomem range 0xfed13000-0xfed19fff has been reserved
[   26.391976] system 00:0a: ioport range 0x680-0x6ff has been reserved
[   26.391979] system 00:0a: ioport range 0x295-0x296 has been reserved
[   26.391985] system 00:0b: ioport range 0x4d0-0x4d1 has been reserved
[   26.391988] system 00:0b: ioport range 0x800-0x87f has been reserved
[   26.391990] system 00:0b: ioport range 0x480-0x4bf has been reserved
[   26.391993] system 00:0b: iomem range 0xfed1c000-0xfed1ffff has been reserved
[   26.391996] system 00:0b: iomem range 0xfed20000-0xfed8ffff has been reserved
[   26.392003] system 00:0d: iomem range 0xffc00000-0xfff7ffff could not be reserved
[   26.392009] system 00:0e: iomem range 0xfec00000-0xfec00fff has been reserved
[   26.392011] system 00:0e: iomem range 0xfee00000-0xfee00fff has been reserved
[   26.392018] system 00:0f: iomem range 0xe0000000-0xefffffff has been reserved
[   26.392024] system 00:10: iomem range 0xe0000000-0xefffffff has been reserved
[   26.392030] system 00:11: iomem range 0x0-0x9ffff could not be reserved
[   26.392033] system 00:11: iomem range 0x0-0x0 could not be reserved
[   26.392035] system 00:11: iomem range 0xe0000-0xfffff could not be reserved
[   26.392038] system 00:11: iomem range 0x100000-0x3fffffff could not be reserved
[   26.392041] system 00:11: iomem range 0x0-0x0 could not be reserved
[   26.422507] PCI: Bridge: 0000:00:01.0
[   26.422511]   IO window: d000-dfff
[   26.422515]   MEM window: f0000000-fbcfffff
[   26.422518]   PREFETCH window: d0000000-deffffff
[   26.422523] PCI: Bridge: 0000:00:1c.0
[   26.422524]   IO window: disabled.
[   26.422529]   MEM window: feb00000-febfffff
[   26.422533]   PREFETCH window: disabled.
[   26.422538] PCI: Bridge: 0000:00:1c.1
[   26.422539]   IO window: disabled.
[   26.422544]   MEM window: fbf00000-fbffffff
[   26.422548]   PREFETCH window: disabled.
[   26.422553] PCI: Bridge: 0000:00:1c.2
[   26.422554]   IO window: disabled.
[   26.422559]   MEM window: fbe00000-fbefffff
[   26.422563]   PREFETCH window: disabled.
[   26.422568] PCI: Bridge: 0000:00:1e.0
[   26.422571]   IO window: e000-efff
[   26.422576]   MEM window: fbd00000-fbdfffff
[   26.422579]   PREFETCH window: disabled.
[   26.422599] ACPI: PCI Interrupt 0000:00:01.0[A] -> GSI 16 (level, low) -> IRQ 16
[   26.422605] PCI: Setting latency timer of device 0000:00:01.0 to 64
[   26.422623] ACPI: PCI Interrupt 0000:00:1c.0[A] -> GSI 16 (level, low) -> IRQ 16
[   26.422629] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[   26.422647] ACPI: PCI Interrupt 0000:00:1c.1[B] -> GSI 17 (level, low) -> IRQ 17
[   26.422654] PCI: Setting latency timer of device 0000:00:1c.1 to 64
[   26.422673] ACPI: PCI Interrupt 0000:00:1c.2[C] -> GSI 18 (level, low) -> IRQ 18
[   26.422679] PCI: Setting latency timer of device 0000:00:1c.2 to 64
[   26.422689] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[   26.422701] NET: Registered protocol family 2
[   26.459976] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[   26.460270] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[   26.460843] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[   26.461125] TCP: Hash tables configured (established 131072 bind 65536)
[   26.461127] TCP reno registered
[   26.472095] checking if image is initramfs... it is
[   26.918988] Switched to high resolution mode on CPU 1
[   26.922841] Switched to high resolution mode on CPU 0
[   27.066548] Freeing initrd memory: 7678k freed
[   27.067440] audit: initializing netlink socket (disabled)
[   27.067456] audit(1217972614.300:1): initialized
[   27.067644] highmem bounce pool size: 64 pages
[   27.069980] VFS: Disk quotas dquot_6.5.1
[   27.070077] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   27.070226] io scheduler noop registered
[   27.070239] io scheduler anticipatory registered
[   27.070241] io scheduler deadline registered
[   27.070253] io scheduler cfq registered (default)
[   27.070344] Boot video device is 0000:01:00.0
[   27.070473] PCI: Setting latency timer of device 0000:00:01.0 to 64
[   27.070513] assign_interrupt_mode Found MSI capability
[   27.070546] Allocate Port Service[0000:00:01.0:pcie00]
[   27.070638] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[   27.070681] assign_interrupt_mode Found MSI capability
[   27.070717] Allocate Port Service[0000:00:1c.0:pcie00]
[   27.070760] Allocate Port Service[0000:00:1c.0:pcie02]
[   27.070856] PCI: Setting latency timer of device 0000:00:1c.1 to 64
[   27.070898] assign_interrupt_mode Found MSI capability
[   27.070933] Allocate Port Service[0000:00:1c.1:pcie00]
[   27.070975] Allocate Port Service[0000:00:1c.1:pcie02]
[   27.071069] PCI: Setting latency timer of device 0000:00:1c.2 to 64
[   27.071112] assign_interrupt_mode Found MSI capability
[   27.071147] Allocate Port Service[0000:00:1c.2:pcie00]
[   27.071189] Allocate Port Service[0000:00:1c.2:pcie02]
[   27.071510] isapnp: Scanning for PnP cards...
[   27.422654] isapnp: No Plug & Play device found
[   27.459319] Real Time Clock Driver v1.12ac
[   27.459432] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   27.459558] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   27.460334] 00:07: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   27.461351] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   27.461430] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[   27.461558] PNP: PS/2 Controller [PNP0f03:PS2M] at 0x60,0x64 irq 12
[   27.461561] PNP: PS/2 controller doesn't have KBD irq; using default 1
[   27.463658] serio: i8042 KBD port at 0x60,0x64 irq 1
[   27.463664] serio: i8042 AUX port at 0x60,0x64 irq 12
[   27.489332] mice: PS/2 mouse device common for all mice
[   27.489484] EISA: Probing bus 0 at eisa.0
[   27.489514] EISA: Detected 0 cards.
[   27.489517] cpuidle: using governor ladder
[   27.489519] cpuidle: using governor menu
[   27.489594] NET: Registered protocol family 1
[   27.489625] Using IPI No-Shortcut mode
[   27.489655] registered taskstats version 1
[   27.489766]   Magic number: 4:300:752
[   27.489770]   hash matches device ttyS3
[   27.489860] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[   27.489862] EDD information not available.
[   27.490036] Freeing unused kernel memory: 364k freed
[   28.730137] fuse init (API version 7.9)
[   28.752512] ACPI: Processor [CPU1] (supports 8 throttling states)
[   29.032823] usbcore: registered new interface driver usbfs
[   29.032855] usbcore: registered new interface driver hub
[   29.033920] usbcore: registered new device driver usb
[   29.051275] USB Universal Host Controller Interface driver v3.0
[   29.051349] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 23 (level, low) -> IRQ 19
[   29.051363] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[   29.051369] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[   29.051595] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[   29.051631] uhci_hcd 0000:00:1d.0: irq 19, io base 0x0000c480
[   29.051831] usb usb1: configuration #1 chosen from 1 choice
[   29.051872] hub 1-0:1.0: USB hub found
[   29.051882] hub 1-0:1.0: 2 ports detected
[   29.154358] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 19 (level, low) -> IRQ 20
[   29.154373] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[   29.154379] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[   29.154412] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[   29.154444] uhci_hcd 0000:00:1d.1: irq 20, io base 0x0000c800
[   29.154607] usb usb2: configuration #1 chosen from 1 choice
[   29.154648] hub 2-0:1.0: USB hub found
[   29.154657] hub 2-0:1.0: 2 ports detected
[   29.258132] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 18
[   29.258147] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[   29.258152] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[   29.258187] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
[   29.258220] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000c880
[   29.258390] usb usb3: configuration #1 chosen from 1 choice
[   29.258436] hub 3-0:1.0: USB hub found
[   29.258447] hub 3-0:1.0: 2 ports detected
[   29.361860] ACPI: PCI Interrupt 0000:00:1d.3[D] -> GSI 16 (level, low) -> IRQ 16
[   29.361876] PCI: Setting latency timer of device 0000:00:1d.3 to 64
[   29.361881] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[   29.361920] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 4
[   29.361954] uhci_hcd 0000:00:1d.3: irq 16, io base 0x0000cc00
[   29.362132] usb usb4: configuration #1 chosen from 1 choice
[   29.362171] hub 4-0:1.0: USB hub found
[   29.362180] hub 4-0:1.0: 2 ports detected
[   29.465629] tg3.c:v3.86 (November 9, 2007)
[   29.465653] ACPI: PCI Interrupt 0000:03:00.0[A] -> GSI 18 (level, low) -> IRQ 18
[   29.465666] PCI: Setting latency timer of device 0000:03:00.0 to 64
[   29.508104] usb 2-1: new full speed USB device using uhci_hcd and address 2
[   29.508491] eth0: Tigon3 [partno(BCM95751) rev 4001 PHY(5750)] (PCI Express) 10/100/1000Base-T Ethernet 00:11:09:2e:77:13
[   29.508504] eth0: RXcsums[1] LinkChgREG[0] MIirq[0] ASF[0] WireSpeed[1] TSOcap[1]
[   29.508509] eth0: dma_rwctrl[76180000] dma_mask[64-bit]
[   29.508558] ACPI: PCI Interrupt 0000:00:1d.7[A] -> GSI 23 (level, low) -> IRQ 19
[   29.508574] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[   29.508580] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[   29.508622] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 5
[   29.512517] ehci_hcd 0000:00:1d.7: debug port 1
[   29.512527] PCI: cache line size of 128 is not supported by device 0000:00:1d.7
[   29.512537] ehci_hcd 0000:00:1d.7: irq 19, io mem 0xdfffbc00
[   29.516697] SCSI subsystem initialized
[   29.525350] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   29.525508] usb usb5: configuration #1 chosen from 1 choice
[   29.525547] hub 5-0:1.0: USB hub found
[   29.525556] hub 5-0:1.0: 8 ports detected
[   29.533209] libata version 3.00 loaded.
[   29.629317] pata_via 0000:02:04.0: version 0.3.3
[   29.629354] ACPI: PCI Interrupt 0000:02:04.0[A] -> GSI 20 (level, low) -> IRQ 21
[   29.644081] scsi0 : pata_via
[   29.651632] Floppy drive(s): fd0 is 1.44M
[   29.654097] scsi1 : pata_via
[   29.654161] ata1: PATA max UDMA/133 cmd 0xe880 ctl 0xe800 bmdma 0xe080 irq 21
[   29.654166] ata2: PATA max UDMA/133 cmd 0xe480 ctl 0xe400 bmdma 0xe088 irq 21
[   29.671662] FDC 0 is a post-1991 82077
[   29.991163] ACPI: PCI Interrupt 0000:00:1f.1[A] -> GSI 18 (level, low) -> IRQ 18
[   29.991213] PCI: Setting latency timer of device 0000:00:1f.1 to 64
[   29.991231] ACPI: PCI interrupt for device 0000:00:1f.1 disabled
[   29.991396] ata_piix 0000:00:1f.1: version 2.12
[   29.991411] ACPI: PCI Interrupt 0000:00:1f.1[A] -> GSI 18 (level, low) -> IRQ 18
[   29.991446] PCI: Setting latency timer of device 0000:00:1f.1 to 64
[   29.991525] scsi2 : ata_piix
[   29.991598] scsi3 : ata_piix
[   29.991645] ata3: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xffa0 irq 14
[   29.991649] ata4: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xffa8 irq 15
[   30.076023] usb 5-3: new high speed USB device using ehci_hcd and address 2
[   30.461322] usb 5-3: configuration #1 chosen from 1 choice
[   30.583141] ata3.00: ATAPI: TSSTcorpCD-R/RW TS-H292A, TS02, max UDMA/33
[   30.583169] ata3.01: ATAPI: SONY    DVD RW DW-D23A, CYS1, max UDMA/66
[   30.697519] usb 5-4: new high speed USB device using ehci_hcd and address 3
[   30.753759] ata3.00: configured for UDMA/33
[   30.829696] usb 5-4: configuration #1 chosen from 1 choice
[   30.829845] hub 5-4:1.0: USB hub found
[   30.829934] hub 5-4:1.0: 4 ports detected
[   30.925244] ata3.01: configured for UDMA/66
[   31.092244] scsi 2:0:0:0: CD-ROM            TSSTcorp CD-R/RW TS-H292A TS02 PQ: 0 ANSI: 5
[   31.093097] scsi 2:0:1:0: CD-ROM            SONY     DVD RW DW-D23A   CYS1 PQ: 0 ANSI: 5
[   31.093180] ata_piix 0000:00:1f.2: MAP [ P0 P2 P1 P3 ]
[   31.093216] ACPI: PCI Interrupt 0000:00:1f.2[B] -> GSI 19 (level, low) -> IRQ 20
[   31.093255] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[   31.093339] scsi4 : ata_piix
[   31.093405] scsi5 : ata_piix
[   31.094959] ata5: SATA max UDMA/133 cmd 0xc400 ctl 0xc080 bmdma 0xb880 irq 20
[   31.094963] ata6: SATA max UDMA/133 cmd 0xc000 ctl 0xbc00 bmdma 0xb888 irq 20
[   31.172386] usb 5-8: new high speed USB device using ehci_hcd and address 4
[   31.265309] ata5.00: ATA-7: Maxtor 6B160M0, BANC1BY0, max UDMA/133
[   31.265314] ata5.00: 320173056 sectors, multi 16: LBA48 NCQ (not used)
[   31.266326] ata5.01: ATA-7: Maxtor 6L160M0, BACE1G10, max UDMA/133
[   31.266329] ata5.01: 320173056 sectors, multi 16: LBA48 NCQ (depth 0/32)
[   31.282284] ata5.00: configured for UDMA/133
[   31.298252] ata5.01: configured for UDMA/133
[   31.306555] usb 5-8: configuration #1 chosen from 1 choice
[   31.460828] ata6.00: ATA-7: Maxtor 6B160M0, BANC1BY0, max UDMA/133
[   31.460833] ata6.00: 320173056 sectors, multi 16: LBA48 NCQ (not used)
[   31.477788] ata6.00: configured for UDMA/133
[   31.477918] scsi 4:0:0:0: Direct-Access     ATA      Maxtor 6B160M0   BANC PQ: 0 ANSI: 5
[   31.478085] scsi 4:0:1:0: Direct-Access     ATA      Maxtor 6L160M0   BACE PQ: 0 ANSI: 5
[   31.478253] scsi 5:0:0:0: Direct-Access     ATA      Maxtor 6B160M0   BANC PQ: 0 ANSI: 5
[   31.479079] ACPI: PCI Interrupt 0000:02:03.0[A] -> GSI 19 (level, low) -> IRQ 20
[   31.531754] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[20]  MMIO=[fbdff800-fbdfffff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[   31.539804] usb 5-4.4: new low speed USB device using ehci_hcd and address 5
[   31.563893] Driver 'sd' needs updating - please use bus_type methods
[   31.564025] sd 4:0:0:0: [sda] 320173056 512-byte hardware sectors (163929 MB)
[   31.564047] sd 4:0:0:0: [sda] Write Protect is off
[   31.564052] sd 4:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   31.564082] sd 4:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   31.564151] sd 4:0:0:0: [sda] 320173056 512-byte hardware sectors (163929 MB)
[   31.564169] sd 4:0:0:0: [sda] Write Protect is off
[   31.564173] sd 4:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   31.564202] sd 4:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   31.564207]  sda:<4>Driver 'sr' needs updating - please use bus_type methods
[   31.567132]  sda1
[   31.567219] sd 4:0:0:0: [sda] Attached SCSI disk
[   31.567301] sd 4:0:1:0: [sdb] 320173056 512-byte hardware sectors (163929 MB)
[   31.567323] sd 4:0:1:0: [sdb] Write Protect is off
[   31.567328] sd 4:0:1:0: [sdb] Mode Sense: 00 3a 00 00
[   31.567361] sd 4:0:1:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   31.567440] sd 4:0:1:0: [sdb] 320173056 512-byte hardware sectors (163929 MB)
[   31.567459] sd 4:0:1:0: [sdb] Write Protect is off
[   31.567463] sd 4:0:1:0: [sdb] Mode Sense: 00 3a 00 00
[   31.567498] sd 4:0:1:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   31.567504]  sdb:sr0: scsi3-mmc drive: 52x/52x writer cd/rw xa/form2 cdda tray
[   31.572940] Uniform CD-ROM driver Revision: 3.20
[   31.573005] sr 2:0:0:0: Attached scsi CD-ROM sr0
[   31.575178]  sdb1 sdb2 sdb3 sdb4
[   31.578482] sr1: scsi3-mmc drive: 48x/48x writer cd/rw xa/form2 cdda tray
[   31.578534] sr 2:0:1:0: Attached scsi CD-ROM sr1
[   31.583257] sd 4:0:1:0: [sdb] Attached SCSI disk
[   31.583346] sd 5:0:0:0: [sdc] 320173056 512-byte hardware sectors (163929 MB)
[   31.583367] sd 5:0:0:0: [sdc] Write Protect is off
[   31.583372] sd 5:0:0:0: [sdc] Mode Sense: 00 3a 00 00
[   31.583419] sd 5:0:0:0: [sdc] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   31.583522] sd 5:0:0:0: [sdc] 320173056 512-byte hardware sectors (163929 MB)
[   31.583849] sd 5:0:0:0: [sdc] Write Protect is off
[   31.583854] sd 5:0:0:0: [sdc] Mode Sense: 00 3a 00 00
[   31.583899] sd 5:0:0:0: [sdc] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   31.583906]  sdc: unknown partition table
[   31.606718] sd 5:0:0:0: [sdc] Attached SCSI disk
[   31.614423] sr 2:0:0:0: Attached scsi generic sg0 type 5
[   31.614457] sr 2:0:1:0: Attached scsi generic sg1 type 5
[   31.614492] sd 4:0:0:0: Attached scsi generic sg2 type 0
[   31.614521] sd 4:0:1:0: Attached scsi generic sg3 type 0
[   31.614551] sd 5:0:0:0: Attached scsi generic sg4 type 0
[   31.641267] usb 5-4.4: configuration #1 chosen from 1 choice
[   31.655549] usbcore: registered new interface driver libusual
[   31.665208] Initializing USB Mass Storage driver...
[   31.666159] scsi6 : SCSI emulation for USB Mass Storage devices
[   31.666256] usbcore: registered new interface driver usb-storage
[   31.666262] USB Mass Storage support registered.
[   31.666388] usb-storage: device found at 4
[   31.666391] usb-storage: waiting for device to settle before scanning
[   31.714805] usbcore: registered new interface driver hiddev
[   31.718776] input:   USB Multimedia Keyboard  as /devices/pci0000:00/0000:00:1d.7/usb5/5-4/5-4.4/5-4.4:1.0/input/input1
[   31.735301] input,hidraw0: USB HID v1.00 Keyboard [  USB Multimedia Keyboard ] on usb-0000:00:1d.7-4.4
[   31.737512] input:   USB Multimedia Keyboard  as /devices/pci0000:00/0000:00:1d.7/usb5/5-4/5-4.4/5-4.4:1.1/input/input2
[   31.759333] input,hidraw1: USB HID v1.00 Device [  USB Multimedia Keyboard ] on usb-0000:00:1d.7-4.4
[   31.759361] usbcore: registered new interface driver usbhid
[   31.759368] /build/buildd/linux-2.6.24/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
[   32.088901] Attempting manual resume
[   32.088906] swsusp: Resume From Partition 8:19
[   32.088908] PM: Checking swsusp image.
[   32.089067] PM: Resume from disk failed.
[   32.104072] EXT3-fs: INFO: recovery required on readonly filesystem.
[   32.104078] EXT3-fs: write access will be enabled during recovery.
[   32.808626] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[0010dc00005d602d]
[   34.473532] kjournald starting.  Commit interval 5 seconds
[   34.473546] EXT3-fs: sdb1: orphan cleanup on readonly fs
[   34.473553] ext3_orphan_cleanup: deleting unreferenced inode 164710
[   34.473575] EXT3-fs: sdb1: 1 orphan inode deleted
[   34.473577] EXT3-fs: recovery complete.
[   34.474732] EXT3-fs: mounted filesystem with ordered data mode.
[   36.651352] usb-storage: device scan complete
[   36.651840] scsi 6:0:0:0: Direct-Access     Generic  USB SD Reader    1.00 PQ: 0 ANSI: 0
[   36.652342] scsi 6:0:0:1: Direct-Access     Generic  USB CF Reader    1.01 PQ: 0 ANSI: 0
[   36.652840] scsi 6:0:0:2: Direct-Access     Generic  USB SM Reader    1.02 PQ: 0 ANSI: 0
[   36.653338] scsi 6:0:0:3: Direct-Access     Generic  USB MS Reader    1.03 PQ: 0 ANSI: 0
[   36.654736] sd 6:0:0:0: [sdd] Attached SCSI removable disk
[   36.654776] sd 6:0:0:0: Attached scsi generic sg5 type 0
[   36.655854] sd 6:0:0:1: [sde] Attached SCSI removable disk
[   36.655887] sd 6:0:0:1: Attached scsi generic sg6 type 0
[   36.656975] sd 6:0:0:2: [sdf] Attached SCSI removable disk
[   36.657013] sd 6:0:0:2: Attached scsi generic sg7 type 0
[   36.658096] sd 6:0:0:3: [sdg] Attached SCSI removable disk
[   36.658130] sd 6:0:0:3: Attached scsi generic sg8 type 0
[   42.049798] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   42.099424] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   42.128583] Linux agpgart interface v0.102
[   42.780721] input: Power Button (FF) as /devices/virtual/input/input3
[   42.792424] ACPI: Power Button (FF) [PWRF]
[   42.792591] input: Power Button (CM) as /devices/virtual/input/input4
[   42.808382] ACPI: Power Button (CM) [PWRB]
[   43.662936] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
[   43.746233] [fglrx] Maximum main memory to use for locked dma buffers: 928 MBytes.
[   43.746288] [fglrx] ASYNCIO init succeed!
[   43.746948] [fglrx] PAT is enabled successfully!
[   43.747928] [fglrx] module loaded - fglrx 8.47.3 [Feb 25 2008] on minor 0
[   43.894924] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 16 (level, low) -> IRQ 16
[   43.894951] PCI: Setting latency timer of device 0000:00:1b.0 to 64
[   45.021583] phy0: Selected rate control algorithm 'simple'
[   45.062962] iTCO_vendor_support: vendor-support=0
[   45.161329] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.02 (26-Jul-2007)
[   45.161492] iTCO_wdt: Found a ICH6 or ICH6R TCO device (Version=2, TCOBASE=0x0860)
[   45.161552] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   45.367161] input: PC Speaker as /devices/platform/pcspkr/input/input5
[   45.496450] intel_rng: FWH not detected
[   45.942497] usbcore: registered new interface driver rt73usb
[   46.126523] input: PS2++ Logitech Wheel Mouse as /devices/platform/i8042/serio1/input/input6
[   46.495713] parport_pc 00:09: reported by Plug and Play ACPI
[   46.495756] parport0: PC-style at 0x3bc, irq 7 [PCSPP,TRISTATE]
[   49.025082] lp0: using parport0 (interrupt-driven).
[   49.112391] Adding 1461904k swap on /dev/sdb3.  Priority:-1 extents:1 across:1461904k
[   49.662581] EXT3 FS on sdb1, internal journal
[   52.627897] kjournald starting.  Commit interval 5 seconds
[   52.628025] EXT3 FS on sdb4, internal journal
[   52.628031] EXT3-fs: mounted filesystem with ordered data mode.
[   53.449253] ip_tables: (C) 2000-2006 Netfilter Core Team
[   55.288219] No dock devices found.
[   56.452921] ppdev: user-space parallel port driver
[   56.585175] audit(1217972644.661:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=5611 profile="/usr/sbin/cupsd" namespace="default"
[   56.660452] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[   56.660459] apm: disabled - APM is not SMP safe.
[   56.844486] RPC: Registered udp transport module.
[   56.844494] RPC: Registered tcp transport module.
[   56.886643] Installing knfsd (copyright (C) 1996 [email]okir@monad.swb.de[/email]).
[   86.870418] rpcbind: server localhost not responding, timed out
[   86.870447] RPC: failed to contact local rpcbind server (errno 5).
[  116.798402] rpcbind: server localhost not responding, timed out
[  116.798426] RPC: failed to contact local rpcbind server (errno 5).
[  146.726396] rpcbind: server localhost not responding, timed out
[  146.726416] RPC: failed to contact local rpcbind server (errno 5).
[  146.726559] NFSD: Using /var/lib/nfs/v4recovery as the NFSv4 state recovery directory
[  146.738843] NFSD: starting 90-second grace period
[  176.666352] rpcbind: server localhost not responding, timed out
[  176.666371] RPC: failed to contact local rpcbind server (errno 5).
[  206.594338] rpcbind: server localhost not responding, timed out
[  206.594357] RPC: failed to contact local rpcbind server (errno 5).
[  206.594365] lockd_up: makesock failed, error=-5
[  236.522338] rpcbind: server localhost not responding, timed out
[  236.522357] RPC: failed to contact local rpcbind server (errno 5).
[  236.532092] nfsd: last server has exited
[  236.532098] nfsd: unexporting all filesystems
[  266.458216] rpcbind: server localhost not responding, timed out
[  266.458235] RPC: failed to contact local rpcbind server (errno 5).
[  267.089549] NET: Registered protocol family 10
[  267.090023] lo: Disabled Privacy Extensions
[  268.183995] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  268.184034] Bluetooth: Core ver 2.11
[  268.184544] NET: Registered protocol family 31
[  268.184548] Bluetooth: HCI device and connection manager initialized
[  268.184554] Bluetooth: HCI socket layer initialized
[  268.230997] Bluetooth: L2CAP ver 2.9
[  268.231003] Bluetooth: L2CAP socket layer initialized
[  268.404067] ADDRCONF(NETDEV_UP): eth0: link is not ready
[  268.405528] Bluetooth: RFCOMM socket layer initialized
[  268.405544] Bluetooth: RFCOMM TTY layer initialized
[  268.405548] Bluetooth: RFCOMM ver 1.8
[  269.591818] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 16
[  272.575325] [fglrx] Reserve Block - 0 offset =  0X0 length = 0X40000
[  272.575332] [fglrx] Reserve Block - 1 offset =  0X7fff000 length = 0X1000
[  272.575337] [fglrx] Reserve Block - 2 offset =  0X7fbf000 length = 0X40000
[  272.722992] [fglrx] interrupt source 20008000 successfully enabled
[  272.723000] [fglrx] enable ID = 0x00000004
[  272.723013] [fglrx] Receive enable interrupt message with irqEnableMask: 20008000
[  272.723149] [fglrx] interrupt source 10000000 successfully enabled
[  272.723154] [fglrx] enable ID = 0x00000005
[  272.723160] [fglrx] Receive enable interrupt message with irqEnableMask: 10000000
[30380.428161] NET: Registered protocol family 17
[30381.591678] wlan0: Initial auth_alg=0
[30381.591687] wlan0: authenticate with AP 00:12:17:b7:ab:cb
[30381.593312] wlan0: RX authentication from 00:12:17:b7:ab:cb (alg=0 transaction=2 status=0)
[30381.593317] wlan0: authenticated
[30381.593323] wlan0: associate with AP 00:12:17:b7:ab:cb
[30381.595429] wlan0: RX AssocResp from 00:12:17:b7:ab:cb (capab=0x411 status=0 aid=3)
[30381.595434] wlan0: associated
[30381.595440] wlan0: switched to short barker preamble (BSSID=00:12:17:b7:ab:cb)
[30381.598934] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[30392.204120] wlan0: no IPv6 routers present
trevor@Linux-Antec:~$

---

### Post by hundred1906 on 2008-08-17
I fixed this myself by using SYSTEM SERVICES to disable Folder Sharing (I have no other computers to share with!).

---

### Post by Crafty Kisses on 2008-08-17
> **hundred1906 said:**
> I fixed this myself by using SYSTEM SERVICES to disable Folder Sharing (I have no other computers to share with!).

Alright then, mark the thread solved. :)

---

