---
title: "HUb erorr"
date: 2009-03-04
forum: Hardware
---

### Post by Michael12uk on 2009-03-04
i recently faced a problem after trying installing glent a 3D game. I managed to remove it easly using synaptic packet manager.

The Problem:
during the boot process it shows

[B][    4.361411] hub 1-2:1.0: hub_port_status failed (err = -71)
[    4.362401] hub 1-2:1.0: hub_port_status failed (err = -71)
[    4.363401] hub 1-2:1.0: hub_port_status failed (err = -71)
[    4.364400] hub 1-2:1.0: hub_port_status failed (err = -71)
[    4.365399] hub 1-2:1.0: hub_port_status failed (err = -71)
[    4.366399] hub 1-2:1.0: hub_port_status failed (err = -71)
[/B]

How can i fix this problem, now? It could be also that my new Ipod docking station what has a build in Hub causes the problem!?

The complete result of dmesg
[    0.444410] pci 0000:00:10.3: PME# supported from D0 D1 D2 D3hot D3cold
[    0.444413] pci 0000:00:10.3: PME# disabled
[    0.444434] PCI: 0000:00:10.4 reg 10 32bit mmio: [ee003000, ee0030ff]
[    0.444465] pci 0000:00:10.4: supports D1
[    0.444467] pci 0000:00:10.4: supports D2
[    0.444469] pci 0000:00:10.4: PME# supported from D0 D1 D2 D3hot D3cold
[    0.444473] pci 0000:00:10.4: PME# disabled
[    0.444523] HPET not enabled in BIOS. You might try hpet=force boot option
[    0.444555] PCI: 0000:00:11.5 reg 10 io port: [e000, e0ff]
[    0.444588] pci 0000:00:11.5: supports D1
[    0.444590] pci 0000:00:11.5: supports D2
[    0.444613] PCI: 0000:00:12.0 reg 10 io port: [e400, e4ff]
[    0.444619] PCI: 0000:00:12.0 reg 14 32bit mmio: [ee004000, ee0040ff]
[    0.444647] pci 0000:00:12.0: supports D1
[    0.444649] pci 0000:00:12.0: supports D2
[    0.444651] pci 0000:00:12.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.444655] pci 0000:00:12.0: PME# disabled
[    0.444729] PCI: 0000:01:00.0 reg 10 32bit mmio: [ec000000, ecffffff]
[    0.444734] PCI: 0000:01:00.0 reg 14 32bit mmio: [e0000000, e7ffffff]
[    0.444746] PCI: 0000:01:00.0 reg 30 32bit mmio: [0, 1ffff]
[    0.444778] PCI: bridge 0000:00:01.0 32bit mmio: [ec000000, edffffff]
[    0.444783] PCI: bridge 0000:00:01.0 32bit mmio pref: [e0000000, e7ffffff]
[    0.444789] bus 00 -> node 0
[    0.444796] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.509174] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 6 7 *10 11 12)
[    0.509362] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 6 7 10 *11 12)
[    0.509553] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 6 7 10 11 *12)
[    0.509721] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 6 7 10 11 12) *0, disabled.
[    0.509889] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 6 7 10 11 12) *0, disabled.
[    0.510050] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 6 7 10 11 12) *0, disabled.
[    0.510207] ACPI: PCI Interrupt Link [LNK0] (IRQs 3 4 6 7 10 11 12) *0, disabled.
[    0.510363] ACPI: PCI Interrupt Link [LNK1] (IRQs 3 4 6 7 10 11 12) *0, disabled.
[    0.510603] ACPI: PCI Interrupt Link [ALKA] (IRQs 20) *11
[    0.510797] ACPI: PCI Interrupt Link [ALKB] (IRQs *21)
[    0.510986] ACPI: PCI Interrupt Link [ALKC] (IRQs *22)
[    0.511212] ACPI: PCI Interrupt Link [ALKD] (IRQs *23)
[    0.511350] Linux Plug and Play Support v0.97 (c) Adam Belay
[    0.511380] pnp: PnP ACPI init
[    0.511387] ACPI: bus type pnp registered
[    0.515532] pnp: PnP ACPI: found 12 devices
[    0.515534] ACPI: ACPI bus type pnp unregistered
[    0.515538] PnPBIOS: Disabled by ACPI PNP
[    0.515856] PCI: Using ACPI for IRQ routing
[    0.516043] NET: Registered protocol family 8
[    0.516045] NET: Registered protocol family 20
[    0.516076] NetLabel: Initializing
[    0.516078] NetLabel:  domain hash size = 128
[    0.516080] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.516096] NetLabel:  unlabeled traffic allowed by default
[    0.516396] tracer: 772 pages allocated for 65536 entries of 48 bytes
[    0.516398]    actual entries 65620
[    0.516563] AppArmor: AppArmor Filesystem Enabled
[    0.516580] ACPI: RTC can wake from S4
[    0.516585] system 00:00: iomem range 0xcf800-0xcffff has been reserved
[    0.516585] system 00:00: iomem range 0xf0000-0xf7fff could not be reserved
[    0.516585] system 00:00: iomem range 0xf8000-0xfbfff could not be reserved
[    0.516585] system 00:00: iomem range 0xfc000-0xfffff could not be reserved
[    0.516585] system 00:00: iomem range 0x80000000-0x800fffff has been reserved
[    0.516585] system 00:00: iomem range 0x7fff0000-0x7fffffff could not be reserved
[    0.516585] system 00:00: iomem range 0xffff0000-0xffffffff could not be reserved
[    0.516585] system 00:00: iomem range 0x0-0x9ffff could not be reserved
[    0.516585] system 00:00: iomem range 0x100000-0x7ffeffff could not be reserved
[    0.516585] system 00:00: iomem range 0xfec00000-0xfec00fff could not be reserved
[    0.516585] system 00:00: iomem range 0xfee00000-0xfee00fff could not be reserved
[    0.516585] system 00:00: iomem range 0xfff80000-0xfffeffff has been reserved
[    0.516585] system 00:02: ioport range 0x4000-0x407f has been reserved
[    0.516585] system 00:02: ioport range 0x5000-0x500f has been reserved
[    0.516585] system 00:03: ioport range 0x4d0-0x4d1 has been reserved
[    0.516585] system 00:03: ioport range 0x800-0x805 has been reserved
[    0.516585] system 00:03: ioport range 0x290-0x297 has been reserved
[    0.551642] pci 0000:00:01.0: PCI bridge, secondary bus 0000:01
[    0.551645] pci 0000:00:01.0:   IO window: disabled
[    0.551650] pci 0000:00:01.0:   MEM window: 0xec000000-0xedffffff
[    0.551654] pci 0000:00:01.0:   PREFETCH window: 0x000000e0000000-0x000000e7ffffff
[    0.551667] pci 0000:00:01.0: setting latency timer to 64
[    0.551671] bus: 00 index 0 io port: [0, ffff]
[    0.551674] bus: 00 index 1 mmio: [0, ffffffff]
[    0.551676] bus: 01 index 0 mmio: [0, 0]
[    0.551678] bus: 01 index 1 mmio: [ec000000, edffffff]
[    0.551680] bus: 01 index 2 mmio: [e0000000, e7ffffff]
[    0.551682] bus: 01 index 3 mmio: [0, 0]
[    0.551695] NET: Registered protocol family 2
[    0.551810] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.552135] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.553016] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.553471] TCP: Hash tables configured (established 131072 bind 65536)
[    0.553474] TCP reno registered
[    0.553581] NET: Registered protocol family 1
[    0.553715] checking if image is initramfs... it is
[    1.052091] Switched to high resolution mode on CPU 0
[    1.257871] Freeing initrd memory: 8163k freed
[    1.258567] audit: initializing netlink socket (disabled)
[    1.258584] type=2000 audit(1236158048.256:1): initialized
[    1.264619] highmem bounce pool size: 64 pages
[    1.264625] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    1.266607] VFS: Disk quotas dquot_6.5.1
[    1.266685] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    1.266782] msgmni has been set to 1743
[    1.266895] io scheduler noop registered
[    1.266897] io scheduler anticipatory registered
[    1.266900] io scheduler deadline registered
[    1.266911] io scheduler cfq registered (default)
[    1.266927] PCI: VIA PCI bridge detected.Disabling DAC.
[    1.267016] pci 0000:01:00.0: Boot video device
[    1.267314] isapnp: Scanning for PnP cards...
[    1.621127] isapnp: No Plug & Play device found
[    1.653645] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
[    1.653770] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.654409] 00:09: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.655963] brd: module loaded
[    1.656045] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[    1.656150] PNP: PS/2 Controller [PNP0303:PS2K] at 0x60,0x64 irq 1
[    1.656153] PNP: PS/2 appears to have AUX port disabled, if this is incorrect please boot with i8042.nopnp
[    1.656288] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.656833] mice: PS/2 mouse device common for all mice
[    1.656959] rtc_cmos 00:05: rtc core: registered rtc_cmos as rtc0
[    1.656996] rtc0: alarms up to one year, y3k
[    1.657101] EISA: Probing bus 0 at eisa.0
[    1.657120] Cannot allocate resource for EISA slot 4
[    1.657122] Cannot allocate resource for EISA slot 5
[    1.657136] EISA: Detected 0 cards.
[    1.657139] cpuidle: using governor ladder
[    1.657142] cpuidle: using governor menu
[    1.657614] TCP cubic registered
[    1.657642] Using IPI No-Shortcut mode
[    1.657814] registered taskstats version 1
[    1.657932]   Magic number: 1:401:221
[    1.657973] tty ttyu5: hash matches
[    1.658102] rtc_cmos 00:05: setting system clock to 2009-03-04 09:14:09 UTC (1236158049)
[    1.658106] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.658108] EDD information not available.
[    1.658441] Freeing unused kernel memory: 424k freed
[    1.658500] Write protecting the kernel text: 2580k
[    1.658537] Write protecting the kernel read-only data: 940k
[    1.678542] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[    1.731100] vesafb: framebuffer at 0xe0000000, mapped to 0xf8880000, using 6144k, total 131072k
[    1.731105] vesafb: mode is 1024x768x32, linelength=4096, pages=1
[    1.731108] vesafb: protected mode interface info at c000:f510
[    1.731111] vesafb: pmi: set display start = c00cf546, set palette = c00cf5b0
[    1.731114] vesafb: pmi: ports = 3b4 3b5 3ba 3c0 3c1 3c4 3c5 3c6 3c7 3c8 3c9 3cc 3ce 3cf 3d0 3d1 3d2 3d3 3d4 3d5 3da 
[    1.731126] vesafb: scrolling: redraw
[    1.731129] vesafb: Truecolor: size=8:8:8:8, shift=24:16:8:0
[    1.731332] Console: switching to colour frame buffer device 128x48
[    1.802509] fb0: VESA VGA frame buffer device
[    2.104041] fuse init (API version 7.9)
[    2.199953] fan PNP0C0B:00: registered as cooling_device0
[    2.199964] ACPI: Fan [FAN] (on)
[    2.207380] processor ACPI0007:00: registered as cooling_device1
[    2.209857] thermal LNXTHERM:01: registered as thermal_zone0
[    2.210173] ACPI: Thermal Zone [THRM] (40 C)
[    2.796176] b43-pci-bridge 0000:00:0b.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    2.801532] ssb: Sonics Silicon Backplane found on PCI device 0000:00:0b.0
[    2.801714] No dock devices found.
[    2.862993] SCSI subsystem initialized
[    2.863088] ohci1394 0000:00:0a.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    2.915806] ohci1394: fw-host0: OHCI-1394 1.0 (PCI): IRQ=[17]  MMIO=[ee002000-ee0027ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[    2.968638] usbcore: registered new interface driver usbfs
[    2.968664] usbcore: registered new interface driver hub
[    2.994442] usbcore: registered new device driver usb
[    3.021582] libata version 3.00 loaded.
[    3.033011] USB Universal Host Controller Interface driver v3.0
[    3.037124] via-rhine.c:v1.10-LK1.4.3 2007-03-06 Written by Donald Becker
[    3.037128] via-rhine: Broken BIOS detected, avoid_D3 enabled.
[    3.068190] sata_via 0000:00:0f.0: version 2.3
[    3.068507] ACPI: PCI Interrupt Link [ALKA] BIOS reported IRQ 11, using IRQ 20
[    3.068510] ACPI: PCI Interrupt Link [ALKA] enabled at IRQ 20
[    3.068519] sata_via 0000:00:0f.0: PCI INT B -> Link[ALKA] -> GSI 20 (level, low) -> IRQ 20
[    3.068562] sata_via 0000:00:0f.0: routed to hard irq line 11
[    3.068644] scsi0 : sata_via
[    3.080041] scsi1 : sata_via
[    3.080118] ata1: SATA max UDMA/133 cmd 0xb400 ctl 0xb800 bmdma 0xc400 irq 20
[    3.080121] ata2: SATA max UDMA/133 cmd 0xbc00 ctl 0xc000 bmdma 0xc408 irq 20
[    3.284049] ata1: SATA link down 1.5 Gbps (SStatus 0 SControl 300)
[    3.488029] ata2: SATA link down 1.5 Gbps (SStatus 0 SControl 300)
[    3.488374] ACPI: PCI Interrupt Link [ALKB] enabled at IRQ 21
[    3.488383] uhci_hcd 0000:00:10.0: PCI INT A -> Link[ALKB] -> GSI 21 (level, low) -> IRQ 21
[    3.488393] uhci_hcd 0000:00:10.0: UHCI Host Controller
[    3.488450] uhci_hcd 0000:00:10.0: new USB bus registered, assigned bus number 1
[    3.488486] uhci_hcd 0000:00:10.0: irq 21, io base 0x0000d000
[    3.488656] usb usb1: configuration #1 chosen from 1 choice
[    3.488682] hub 1-0:1.0: USB hub found
[    3.488691] hub 1-0:1.0: 2 ports detected
[    3.696256] uhci_hcd 0000:00:10.1: PCI INT A -> Link[ALKB] -> GSI 21 (level, low) -> IRQ 21
[    3.696267] uhci_hcd 0000:00:10.1: UHCI Host Controller
[    3.696290] uhci_hcd 0000:00:10.1: new USB bus registered, assigned bus number 2
[    3.696313] uhci_hcd 0000:00:10.1: irq 21, io base 0x0000d400
[    3.696409] usb usb2: configuration #1 chosen from 1 choice
[    3.696435] hub 2-0:1.0: USB hub found
[    3.696444] hub 2-0:1.0: 2 ports detected
[    3.808010] usb 1-1: new low speed USB device using uhci_hcd and address 2
[    3.904227] uhci_hcd 0000:00:10.2: PCI INT B -> Link[ALKB] -> GSI 21 (level, low) -> IRQ 21
[    3.904238] uhci_hcd 0000:00:10.2: UHCI Host Controller
[    3.904260] uhci_hcd 0000:00:10.2: new USB bus registered, assigned bus number 3
[    3.904284] uhci_hcd 0000:00:10.2: irq 21, io base 0x0000d800
[    3.904376] usb usb3: configuration #1 chosen from 1 choice
[    3.904401] hub 3-0:1.0: USB hub found
[    3.904409] hub 3-0:1.0: 2 ports detected
[    3.984759] usb 1-1: configuration #1 chosen from 1 choice
[    4.100010] usb 1-2: new full speed USB device using uhci_hcd and address 3
[    4.112183] uhci_hcd 0000:00:10.3: PCI INT B -> Link[ALKB] -> GSI 21 (level, low) -> IRQ 21
[    4.112193] uhci_hcd 0000:00:10.3: UHCI Host Controller
[    4.112227] uhci_hcd 0000:00:10.3: new USB bus registered, assigned bus number 4
[    4.112250] uhci_hcd 0000:00:10.3: irq 21, io base 0x0000dc00
[    4.112350] usb usb4: configuration #1 chosen from 1 choice
[    4.112374] hub 4-0:1.0: USB hub found
[    4.112382] hub 4-0:1.0: 2 ports detected
[    4.243768] usb 1-2: configuration #1 chosen from 1 choice
[    4.246611] hub 1-2:1.0: USB hub found
[    4.248419] hub 1-2:1.0: 6 ports detected
[    4.320456] ehci_hcd 0000:00:10.4: PCI INT C -> Link[ALKB] -> GSI 21 (level, low) -> IRQ 21
[    4.320469] ehci_hcd 0000:00:10.4: EHCI Host Controller
[    4.320494] ehci_hcd 0000:00:10.4: new USB bus registered, assigned bus number 5
[    4.320534] ehci_hcd 0000:00:10.4: irq 21, io mem 0xee003000
[    4.332015] ehci_hcd 0000:00:10.4: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    4.332191] usb usb5: configuration #1 chosen from 1 choice
[    4.332218] hub 5-0:1.0: USB hub found
[    4.332227] hub 5-0:1.0: 8 ports detected
[    4.340098] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[00301bb50000d746]
[    4.361411] hub 1-2:1.0: hub_port_status failed (err = -71)
[    4.362401] hub 1-2:1.0: hub_port_status failed (err = -71)
[    4.363401] hub 1-2:1.0: hub_port_status failed (err = -71)
[    4.364400] hub 1-2:1.0: hub_port_status failed (err = -71)
[    4.365399] hub 1-2:1.0: hub_port_status failed (err = -71)
[    4.366399] hub 1-2:1.0: hub_port_status failed (err = -71)
[    4.492021] usb 1-1: USB disconnect, address 2
[    4.540473] ACPI: PCI Interrupt Link [ALKD] enabled at IRQ 23
[    4.540483] via-rhine 0000:00:12.0: PCI INT A -> Link[ALKD] -> GSI 23 (level, low) -> IRQ 23
[    4.544675] eth0: VIA Rhine II at 0xee004000, 00:30:1b:b5:d6:e2, IRQ 23.
[    4.545385] eth0: MII PHY found at address 1, status 0x786d advertising 05e1 Link 45e1.
[    4.553362] pata_via 0000:00:0f.1: version 0.3.3
[    4.553384] pata_via 0000:00:0f.1: PCI INT A -> Link[ALKA] -> GSI 20 (level, low) -> IRQ 20
[    4.560183] scsi2 : pata_via
[    4.560309] scsi3 : pata_via
[    4.562059] ata3: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xcc00 irq 14
[    4.562062] ata4: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xcc08 irq 15
[    4.620047] usb 1-2: USB disconnect, address 3
[    4.724371] ata3.00: ATAPI: PLEXTOR DVDR   PX-712A, 1.02, max UDMA/33
[    4.732266] ata3.00: configured for UDMA/33
[    4.905536] ata4.00: ATA-6: WDC WD1600JB-00EVA0, 15.05R15, max UDMA/100
[    4.905540] ata4.00: 312581808 sectors, multi 16: LBA48 
[    4.905721] ata4.01: ATA-7: Maxtor 2F040L0, VAM51JJ0, max UDMA/133
[    4.905723] ata4.01: 80293248 sectors, multi 16: LBA 
[    4.916008] usb 5-2: new high speed USB device using ehci_hcd and address 3
[    4.921412] ata4.00: configured for UDMA/100
[    4.936374] ata4.01: configured for UDMA/133
[    4.937044] scsi 2:0:0:0: CD-ROM            PLEXTOR  DVDR   PX-712A   1.02 PQ: 0 ANSI: 5
[    4.937217] scsi 2:0:0:0: Attached scsi generic sg0 type 5
[    4.937277] scsi 3:0:0:0: Direct-Access     ATA      WDC WD1600JB-00E 15.0 PQ: 0 ANSI: 5
[    4.937359] scsi 3:0:0:0: Attached scsi generic sg1 type 0
[    4.937411] scsi 3:0:1:0: Direct-Access     ATA      Maxtor 2F040L0   VAM5 PQ: 0 ANSI: 5
[    4.937488] scsi 3:0:1:0: Attached scsi generic sg2 type 0
[    4.980423] Driver 'sr' needs updating - please use bus_type methods
[    4.986115] Driver 'sd' needs updating - please use bus_type methods
[    4.986238] sr0: scsi3-mmc drive: 40x/40x writer cd/rw xa/form2 cdda tray
[    4.986243] Uniform CD-ROM driver Revision: 3.20
[    4.986333] sr 2:0:0:0: Attached scsi CD-ROM sr0
[    4.990076] sd 3:0:0:0: [sda] 312581808 512-byte hardware sectors (160042 MB)
[    4.990093] sd 3:0:0:0: [sda] Write Protect is off
[    4.990096] sd 3:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    4.990118] sd 3:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.990180] sd 3:0:0:0: [sda] 312581808 512-byte hardware sectors (160042 MB)
[    4.990192] sd 3:0:0:0: [sda] Write Protect is off
[    4.990195] sd 3:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    4.990215] sd 3:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.990220]  sda: sda1 sda2 < sda5 sda6 >
[    5.039683] sd 3:0:0:0: [sda] Attached SCSI disk
[    5.039756] sd 3:0:1:0: [sdb] 80293248 512-byte hardware sectors (41110 MB)
[    5.039772] sd 3:0:1:0: [sdb] Write Protect is off
[    5.039775] sd 3:0:1:0: [sdb] Mode Sense: 00 3a 00 00
[    5.039798] sd 3:0:1:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    5.039852] sd 3:0:1:0: [sdb] 80293248 512-byte hardware sectors (41110 MB)
[    5.039865] sd 3:0:1:0: [sdb] Write Protect is off
[    5.039867] sd 3:0:1:0: [sdb] Mode Sense: 00 3a 00 00
[    5.039889] sd 3:0:1:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    5.039893]  sdb:<6>usb 5-2: configuration #1 chosen from 1 choice
[    5.048700] hub 5-2:1.0: USB hub found
[    5.048796] hub 5-2:1.0: 6 ports detected
[    5.061964]  sdb1 sdb2 < sdb5 >
[    5.089721] sd 3:0:1:0: [sdb] Attached SCSI disk
[    5.272061] usbcore: registered new interface driver hiddev
[    5.512021] usb 1-1: new low speed USB device using uhci_hcd and address 4
[    5.688499] usb 1-1: configuration #1 chosen from 1 choice
[    5.704497] input: Logitech USB-PS/2 Optical Mouse as /devices/pci0000:00/0000:00:10.0/usb1/1-1/1-1:1.0/input/input2
[    5.704736] input,hidraw0: USB HID v1.10 Mouse [Logitech USB-PS/2 Optical Mouse] on usb-0000:00:10.0-1
[    5.704754] usbcore: registered new interface driver usbhid
[    5.704757] usbhid: v2.6:USB HID core driver
[    5.800212] PM: Starting manual resume from disk
[    5.800217] PM: Resume from partition 8:21
[    5.800219] PM: Checking hibernation image.
[    5.800365] PM: Resume from disk failed.
[    5.859862] kjournald starting.  Commit interval 5 seconds
[    5.859878] EXT3-fs: mounted filesystem with ordered data mode.
[    5.928015] usb 2-2: new full speed USB device using uhci_hcd and address 2
[    6.133180] usb 2-2: configuration #1 chosen from 1 choice
[   13.871966] udevd version 124 started
[   14.730342] Linux agpgart interface v0.103
[   14.808176] agpgart-amd64 0000:00:00.0: AGP bridge [1106/0204]
[   14.811429] agpgart-amd64 0000:00:00.0: AGP aperture is 64M @ 0xe8000000
[   14.868188] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   14.908683] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   15.460243] input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input3
[   15.472059] ACPI: Power Button (FF) [PWRF]
[   15.472195] input: Power Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input4
[   15.488018] ACPI: Power Button (CM) [PWRB]
[   15.979908] nvidia: module license 'NVIDIA' taints kernel.
[   16.872224] parport_pc 00:0a: reported by Plug and Play ACPI
[   16.872268] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
[   16.947916] b43-phy0: Broadcom 4306 WLAN found
[   17.028766] phy0: Selected rate control algorithm 'pid'
[   17.361289] ACPI: PCI Interrupt Link [ALKC] enabled at IRQ 22
[   17.361299] VIA 82xx Audio 0000:00:11.5: PCI INT C -> Link[ALKC] -> GSI 22 (level, low) -> IRQ 22
[   17.361443] VIA 82xx Audio 0000:00:11.5: setting latency timer to 64
[   17.361608] Broadcom 43xx driver loaded [ Features: PLR, Firmware-ID: FW13 ]
[   17.700168] Linux video capture interface: v2.00
[   17.765646] gspca: main v2.2.0 registered
[   17.792158] gspca: probing 093a:262a
[   17.801597] gspca: probe ok
[   17.801620] usbcore: registered new interface driver pac7311
[   17.801634] pac7311: registered
[   18.021826] nvidia 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   18.022106] NVRM: loading NVIDIA UNIX x86 Kernel Module  173.14.12  Thu Jul 17 18:11:36 PDT 2008
[   18.027107] input: PC Speaker as /devices/platform/pcspkr/input/input5
[   20.827370] lp0: using parport0 (interrupt-driven).
[   21.051098] Adding 1694816k swap on /dev/sdb5.  Priority:-1 extents:1 across:1694816k
[   21.543165] EXT3 FS on sdb1, internal journal
[   22.221755] type=1505 audit(1236158070.532:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=4151
[   22.469270] type=1505 audit(1236158070.780:3): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=4156
[   22.469540] type=1505 audit(1236158070.780:4): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=4156
[   22.638728] ip_tables: (C) 2000-2006 Netfilter Core Team
[   22.689642] nf_conntrack version 0.5.0 (16384 buckets, 65536 max)
[   22.689802] CONFIG_NF_CT_ACCT is deprecated and will be removed soon. Plase use
[   22.689805] nf_conntrack.acct=1 kernel paramater, acct=1 nf_conntrack module option or
[   22.689808] sysctl net.netfilter.nf_conntrack_acct=1 to enable it.
[   22.812884] NET: Registered protocol family 10
[   22.813447] lo: Disabled Privacy Extensions
[   22.825504] ip6_tables: (C) 2000-2006 Netfilter Core Team
[   24.203719] ACPI: WMI: Mapper loaded
[   24.512385] powernow-k8: Found 1 AMD Athlon(tm) 64 Processor 3000+ processors (1 cpu cores) (version 2.20.00)
[   24.512425] powernow-k8:    0 : fid 0xc (2000 MHz), vid 0x2
[   24.512427] powernow-k8:    1 : fid 0xa (1800 MHz), vid 0x6
[   24.512430] powernow-k8:    2 : fid 0x2 (1000 MHz), vid 0x12
[   25.489703] warning: `avahi-daemon' uses 32-bit capabilities (legacy support in use)
[   25.739677] apm: BIOS not found.
[   25.991675] ppdev: user-space parallel port driver
[   28.176120] Marking TSC unstable due to cpufreq changes
[   28.548025] Clocksource tsc unstable (delta = -188353308 ns)
[   32.555037] Bluetooth: Core ver 2.13
[   32.556768] NET: Registered protocol family 31
[   32.556773] Bluetooth: HCI device and connection manager initialized
[   32.556777] Bluetooth: HCI socket layer initialized
[   32.571941] Bluetooth: L2CAP ver 2.11
[   32.571946] Bluetooth: L2CAP socket layer initialized
[   32.583076] Bluetooth: SCO (Voice Link) ver 0.6
[   32.583082] Bluetooth: SCO socket layer initialized
[   32.594077] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   32.594083] Bluetooth: BNEP filters: protocol multicast
[   32.639597] Bridge firewalling registered
[   32.724541] Bluetooth: RFCOMM socket layer initialized
[   32.725240] Bluetooth: RFCOMM TTY layer initialized
[   32.725244] Bluetooth: RFCOMM ver 1.10
[   36.267495] agpgart-amd64 0000:00:00.0: AGP 3.0 bridge
[   36.267516] agpgart-amd64 0000:00:00.0: putting AGP V3 device into 8x mode
[   36.267607] nvidia 0000:01:00.0: putting AGP V3 device into 8x mode
[   36.972758] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[   37.021007] input: b43-phy0 as /devices/virtual/input/input6
[   37.173543] firmware: requesting b43/ucode5.fw
[   37.391575] firmware: requesting b43/pcm5.fw
[   37.462234] firmware: requesting b43/b0g0initvals5.fw
[   37.519290] firmware: requesting b43/b0g0bsinitvals5.fw
[   37.808030] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
[   37.961097] Registered led device: b43-phy0::tx
[   37.964432] Registered led device: b43-phy0::rx
[   37.965597] Registered led device: b43-phy0::radio
[   37.996440] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   38.152147] NET: Registered protocol family 17
[   40.288379] [UFW BLOCK INPUT]: IN=eth0 OUT= MAC=00:30:1b:b5:d6:e2:00:22:3f:37:b1:52:08:00 SRC=69.203.28.28 DST=192.168.1.2 LEN=91 TOS=0x00 PREC=0x00 TTL=47 ID=49367 PROTO=UDP SPT=44897 DPT=58647 LEN=71 
[   47.088023] eth0: no IPv6 routers present
[   74.714139] [UFW BLOCK INPUT]: IN=eth0 OUT= MAC=00:30:1b:b5:d6:e2:00:22:3f:37:b1:52:08:00 SRC=173.78.84.65 DST=192.168.1.2 LEN=111 TOS=0x00 PREC=0x00 TTL=106 ID=17111 PROTO=UDP SPT=41288 DPT=58647 LEN=91 
[   77.587546] [UFW BLOCK INPUT]: IN=eth0 OUT= MAC=00:30:1b:b5:d6:e2:00:22:3f:37:b1:52:08:00 SRC=83.81.103.61 DST=192.168.1.2 LEN=93 TOS=0x00 PREC=0x00 TTL=114 ID=27754 PROTO=UDP SPT=37938 DPT=58647 LEN=73 
[   92.226234] [UFW BLOCK INPUT]: IN=eth0 OUT= MAC=00:30:1b:b5:d6:e2:00:22:3f:37:b1:52:08:00 SRC=81.159.233.163 DST=192.168.1.2 LEN=111 TOS=0x00 PREC=0x00 TTL=112 ID=32501 PROTO=UDP SPT=6881 DPT=58647 LEN=91 
[   94.967710] [UFW BLOCK INPUT]: IN=eth0 OUT= MAC=00:30:1b:b5:d6:e2:00:22:3f:37:b1:52:08:00 SRC=173.78.84.65 DST=192.168.1.2 LEN=111 TOS=0x00 PREC=0x00 TTL=106 ID=18389 PROTO=UDP SPT=41288 DPT=58647 LEN=91 
[  102.189486] [UFW BLOCK INPUT]: IN=eth0 OUT= MAC=00:30:1b:b5:d6:e2:00:22:3f:37:b1:52:08:00 SRC=83.81.103.61 DST=192.168.1.2 LEN=93 TOS=0x00 PREC=0x00 TTL=114 ID=2561 PROTO=UDP SPT=37938 DPT=58647 LEN=73 
[  128.936999] [UFW BLOCK INPUT]: IN=eth0 OUT= MAC=00:30:1b:b5:d6:e2:00:22:3f:37:b1:52:08:00 SRC=90.213.132.111 DST=192.168.1.2 LEN=111 TOS=0x00 PREC=0x00 TTL=118 ID=8495 PROTO=UDP SPT=60963 DPT=58647 LEN=91 
[  136.683500] [UFW BLOCK INPUT]: IN=eth0 OUT= MAC=00:30:1b:b5:d6:e2:00:22:3f:37:b1:52:08:00 SRC=81.159.233.163 DST=192.168.1.2 LEN=111 TOS=0x00 PREC=0x00 TTL=112 ID=4920 PROTO=UDP SPT=6881 DPT=58647 LEN=91 
[  138.412037] [UFW BLOCK INPUT]: IN=eth0 OUT= MAC=00:30:1b:b5:d6:e2:00:22:3f:37:b1:52:08:00 SRC=86.29.87.242 DST=192.168.1.2 LEN=111 TOS=0x00 PREC=0x00 TTL=120 ID=6896 PROTO=UDP SPT=12242 DPT=58647 LEN=91 
[  167.342081] [UFW BLOCK INPUT]: IN=eth0 OUT= MAC=00:30:1b:b5:d6:e2:00:22:3f:37:b1:52:08:00 SRC=83.81.103.61 DST=192.168.1.2 LEN=93 TOS=0x00 PREC=0x00 TTL=114 ID=14825 PROTO=UDP SPT=37938 DPT=58647 LEN=73 
[  168.739388] ppdev0: registered pardevice
[  168.788039] ppdev0: unregistered pardevice
[  170.348470] ppdev0: registered pardevice
[  170.396365] ppdev0: unregistered pardevice
[  174.136481] ppdev0: registered pardevice
[  174.184167] ppdev0: unregistered pardevice
[  178.028477] [UFW BLOCK INPUT]: IN=eth0 OUT= MAC=00:30:1b:b5:d6:e2:00:22:3f:37:b1:52:08:00 SRC=83.81.103.61 DST=192.168.1.2 LEN=93 TOS=0x00 PREC=0x00 TTL=114 ID=17204 PROTO=UDP SPT=37938 DPT=58647 LEN=73 
[  182.660534] [UFW BLOCK INPUT]: IN=eth0 OUT= MAC=00:30:1b:b5:d6:e2:00:22:3f:37:b1:52:08:00 SRC=86.29.87.242 DST=192.168.1.2 LEN=111 TOS=0x00 PREC=0x00 TTL=120 ID=7981 PROTO=UDP SPT=12242 DPT=58647 LEN=91 
[  185.902277] [UFW BLOCK INPUT]: IN=eth0 OUT= MAC=00:30:1b:b5:d6:e2:00:22:3f:37:b1:52:08:00 SRC=87.206.174.164 DST=192.168.1.2 LEN=95 TOS=0x00 PREC=0x20 TTL=116 ID=30262 PROTO=UDP SPT=27777 DPT=58647 LEN=75 
[  190.367934] [UFW BLOCK INPUT]: IN=eth0 OUT= MAC=00:30:1b:b5:d6:e2:00:22:3f:37:b1:52:08:00 SRC=85.229.115.137 DST=192.168.1.2 LEN=105 TOS=0x00 PREC=0x00 TTL=115 ID=18479 PROTO=UDP SPT=52921 DPT=58647 LEN=85 
[  215.425308] [UFW BLOCK INPUT]: IN=eth0 OUT= MAC=00:30:1b:b5:d6:e2:00:22:3f:37:b1:52:08:00 SRC=67.8.85.231 DST=192.168.1.2 LEN=93 TOS=0x00 PREC=0x00 TTL=110 ID=16062 PROTO=UDP SPT=1858 DPT=58647 LEN=73 
[  215.537007] [UFW BLOCK INPUT]: IN=eth0 OUT= MAC=00:30:1b:b5:d6:e2:00:22:3f:37:b1:52:08:00 SRC=72.200.142.157 DST=192.168.1.2 LEN=91 TOS=0x00 PREC=0x00 TTL=119 ID=31021 PROTO=UDP SPT=17920 DPT=58647 LEN=71 
[  215.723605] [UFW BLOCK INPUT]: IN=eth0 OUT= MAC=00:30:1b:b5:d6:e2:00:22:3f:37:b1:52:08:00 SRC=190.49.39.35 DST=192.168.1.2 LEN=91 TOS=0x00 PREC=0x00 TTL=114 ID=8136 PROTO=UDP SPT=55691 DPT=58647 LEN=71 
[  215.889351] [UFW BLOCK INPUT]: IN=eth0 OUT= MAC=00:30:1b:b5:d6:e2:00:22:3f:37:b1:52:08:00 SRC=207.6.225.143 DST=192.168.1.2 LEN=91 TOS=0x00 PREC=0x00 TTL=54 ID=64187 PROTO=UDP SPT=41783 DPT=58647 LEN=71 
[  234.803974] [UFW BLOCK INPUT]: IN=eth0 OUT= MAC=00:30:1b:b5:d6:e2:00:22:3f:37:b1:52:08:00 SRC=84.125.89.102 DST=192.168.1.2 LEN=91 TOS=0x00 PREC=0x00 TTL=113 ID=28490 PROTO=UDP SPT=59414 DPT=58647 LEN=71 
[  257.422622] [UFW BLOCK INPUT]: IN=eth0 OUT= MAC=00:30:1b:b5:d6:e2:00:22:3f:37:b1:52:08:00 SRC=124.168.57.20 DST=192.168.1.2 LEN=108 TOS=0x00 PREC=0x00 TTL=115 ID=26624 PROTO=UDP SPT=34379 DPT=58647 LEN=88 
[  275.611202] [UFW BLOCK INPUT]: IN=eth0 OUT= MAC=00:30:1b:b5:d6:e2:00:22:3f:37:b1:52:08:00 SRC=98.204.214.215 DST=192.168.1.2 LEN=91 TOS=0x00 PREC=0x00 TTL=113 ID=30703 PROTO=UDP SPT=52837 DPT=58647 LEN=71 
[  308.169289] [UFW BLOCK INPUT]: IN=eth0 OUT= MAC=00:30:1b:b5:d6:e2:00:22:3f:37:b1:52:08:00 SRC=124.171.15.192 DST=192.168.1.2 LEN=302 TOS=0x00 PREC=0x20 TTL=116 ID=47023 PROTO=UDP SPT=19132 DPT=58647 LEN=282 
[  316.950239] [UFW BLOCK INPUT]: IN=eth0 OUT= MAC=00:30:1b:b5:d6:e2:00:22:3f:37:b1:52:08:00 SRC=80.219.158.181 DST=192.168.1.2 LEN=91 TOS=0x00 PREC=0x00 TTL=116 ID=30341 PROTO=UDP SPT=59006 DPT=58647 LEN=71 
[  337.531240] [UFW BLOCK INPUT]: IN=eth0 OUT= MAC=00:30:1b:b5:d6:e2:00:22:3f:37:b1:52:08:00 SRC=24.37.143.114 DST=192.168.1.2 LEN=302 TOS=0x00 PREC=0x00 TTL=108 ID=49008 PROTO=UDP SPT=61614 DPT=58647 LEN=282

---

### Post by albandy on 2009-03-04
I had a similar problem with my old computer, it has an integrated webcam connected internally to a usb port.
That webcam can be manually moved up and down, this broke an internal connector that cause this error.

So I think that one of your usb devices is not working well, try unplugin the usb devices and restart your computer

---

