---
title: "Hangs badly on start up"
date: 2009-09-02
forum: Installation &amp; Upgrades
---

### Post by warby1212 on 2009-09-02
Hi, I have installed Ubuntu 9.04 on a desktop with a Gigabyte ga-eg41m-s2h/s2 motherboard but it hangs badly when starting. Progress bar goes about 20% then stops for a minute or so. I'm tinking it must be a driver but don't know where to start. My boot log is below and you can see where it hangs but I can't make sense of it. Any help?:D

[    0.435984] pci 0000:00:1b.0: reg 10 64bit mmio: [0xf2500000-0xf2503fff]
[    0.436027] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    0.436030] pci 0000:00:1b.0: PME# disabled
[    0.436070] pci 0000:00:1d.0: reg 20 io port: [0xe000-0xe01f]
[    0.436113] pci 0000:00:1d.1: reg 20 io port: [0xe100-0xe11f]
[    0.436157] pci 0000:00:1d.2: reg 20 io port: [0xe200-0xe21f]
[    0.436200] pci 0000:00:1d.3: reg 20 io port: [0xe300-0xe31f]
[    0.436242] pci 0000:00:1d.7: reg 10 32bit mmio: [0xf2504000-0xf25043ff]
[    0.436381] pci 0000:00:1f.0: quirk: region 0400-047f claimed by ICH6 ACPI/GPIO/TCO
[    0.436385] pci 0000:00:1f.0: quirk: region 0480-04bf claimed by ICH6 GPIO
[    0.436418] pci 0000:00:1f.2: reg 10 io port: [0x00-0x07]
[    0.436424] pci 0000:00:1f.2: reg 14 io port: [0x00-0x03]
[    0.436429] pci 0000:00:1f.2: reg 18 io port: [0x00-0x07]
[    0.436434] pci 0000:00:1f.2: reg 1c io port: [0x00-0x03]
[    0.436440] pci 0000:00:1f.2: reg 20 io port: [0xf000-0xf00f]
[    0.436456] pci 0000:00:1f.2: PME# supported from D3hot
[    0.436459] pci 0000:00:1f.2: PME# disabled
[    0.436501] pci 0000:00:1f.3: reg 20 io port: [0x500-0x51f]
[    0.436555] pci 0000:01:02.0: reg 10 32bit mmio: [0xf1001000-0xf10017ff]
[    0.436592] pci 0000:01:02.0: supports D1 D2
[    0.436626] pci 0000:01:05.0: reg 10 io port: [0xd000-0xd0ff]
[    0.436632] pci 0000:01:05.0: reg 14 32bit mmio: [0xf1000000-0xf10000ff]
[    0.436657] pci 0000:01:05.0: reg 30 32bit mmio: [0x000000-0x01ffff]
[    0.436666] pci 0000:01:05.0: supports D1 D2
[    0.436668] pci 0000:01:05.0: PME# supported from D1 D2 D3hot D3cold
[    0.436672] pci 0000:01:05.0: PME# disabled
[    0.436709] pci 0000:00:1e.0: transparent bridge
[    0.436713] pci 0000:00:1e.0: bridge io port: [0xd000-0xdfff]
[    0.436717] pci 0000:00:1e.0: bridge 32bit mmio: [0xf0000000-0xf1ffffff]
[    0.436727] bus 00 -> node 0
[    0.436733] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.437013] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.HUB0._PRT]
[    0.445756] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 *5 6 7 9 10 11 12 14 15)
[    0.445857] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[    0.445958] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 *7 9 10 11 12 14 15)
[    0.446057] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
[    0.446156] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[    0.446255] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 9 *10 11 12 14 15)
[    0.446354] ACPI: PCI Interrupt Link [LNK0] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[    0.446453] ACPI: PCI Interrupt Link [LNK1] (IRQs *3 4 5 6 7 9 10 11 12 14 15)
[    0.446578] ACPI: WMI: Mapper loaded
[    0.446632] SCSI subsystem initialized
[    0.446632] libata version 3.00 loaded.
[    0.446632] usbcore: registered new interface driver usbfs
[    0.446632] usbcore: registered new interface driver hub
[    0.446632] usbcore: registered new device driver usb
[    0.446632] PCI: Using ACPI for IRQ routing
[    0.452010] Bluetooth: Core ver 2.13
[    0.452028] NET: Registered protocol family 31
[    0.452028] Bluetooth: HCI device and connection manager initialized
[    0.452028] Bluetooth: HCI socket layer initialized
[    0.452028] NET: Registered protocol family 8
[    0.452028] NET: Registered protocol family 20
[    0.452040] NetLabel: Initializing
[    0.452042] NetLabel:  domain hash size = 128
[    0.452044] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.452058] NetLabel:  unlabeled traffic allowed by default
[    0.452074] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[    0.452080] hpet0: 3 comparators, 64-bit 14.318180 MHz counter
[    0.456070] AppArmor: AppArmor Filesystem Enabled
[    0.464050] pnp: PnP ACPI init
[    0.464059] ACPI: bus type pnp registered
[    0.466269] pnp: PnP ACPI: found 15 devices
[    0.466270] ACPI: ACPI bus type pnp unregistered
[    0.466275] PnPBIOS: Disabled by ACPI PNP
[    0.466283] system 00:01: ioport range 0x4d0-0x4d1 has been reserved
[    0.466285] system 00:01: ioport range 0x290-0x29f has been reserved
[    0.466287] system 00:01: ioport range 0x800-0x87f has been reserved
[    0.466290] system 00:01: ioport range 0x290-0x294 has been reserved
[    0.466292] system 00:01: ioport range 0x880-0x88f has been reserved
[    0.466295] system 00:01: ioport range 0x4c0-0x4ff could not be reserved
[    0.466303] system 00:0b: ioport range 0x400-0x4bf could not be reserved
[    0.466309] system 00:0c: iomem range 0xd0000000-0xdfffffff has been reserved
[    0.466314] system 00:0d: iomem range 0xcc600-0xcffff has been reserved
[    0.466317] system 00:0d: iomem range 0xf0000-0xf7fff could not be reserved
[    0.466319] system 00:0d: iomem range 0xf8000-0xfbfff could not be reserved
[    0.466321] system 00:0d: iomem range 0xfc000-0xfffff could not be reserved
[    0.466324] system 00:0d: iomem range 0x3dce0000-0x3dcfffff could not be reserved
[    0.466326] system 00:0d: iomem range 0x0-0x9ffff could not be reserved
[    0.466329] system 00:0d: iomem range 0x100000-0x3dcdffff could not be reserved
[    0.466331] system 00:0d: iomem range 0xfec00000-0xfec00fff has been reserved
[    0.466333] system 00:0d: iomem range 0xfed13000-0xfed1dfff has been reserved
[    0.466336] system 00:0d: iomem range 0xfed20000-0xfed8ffff has been reserved
[    0.466338] system 00:0d: iomem range 0xfee00000-0xfee00fff has been reserved
[    0.466341] system 00:0d: iomem range 0xffb00000-0xffb7ffff has been reserved
[    0.466343] system 00:0d: iomem range 0xfff00000-0xffffffff has been reserved
[    0.466345] system 00:0d: iomem range 0xe0000-0xeffff has been reserved
[    0.500711] Switched to high resolution mode on CPU 1
[    0.501869] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:01
[    0.501873] pci 0000:00:1e.0:   IO window: 0xd000-0xdfff
[    0.501878] pci 0000:00:1e.0:   MEM window: 0xf0000000-0xf1ffffff
[    0.501882] pci 0000:00:1e.0:   PREFETCH window: 0x00000040000000-0x000000400fffff
[    0.501894] pci 0000:00:1e.0: setting latency timer to 64
[    0.501897] bus: 00 index 0 io port: [0x00-0xffff]
[    0.501899] bus: 00 index 1 mmio: [0x000000-0xffffffff]
[    0.501902] bus: 01 index 0 io port: [0xd000-0xdfff]
[    0.501903] bus: 01 index 1 mmio: [0xf0000000-0xf1ffffff]
[    0.501905] bus: 01 index 2 mmio: [0x40000000-0x400fffff]
[    0.501907] bus: 01 index 3 io port: [0x00-0xffff]
[    0.501909] bus: 01 index 4 mmio: [0x000000-0xffffffff]
[    0.501922] NET: Registered protocol family 2
[    0.504065] Switched to high resolution mode on CPU 0
[    0.516092] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.516345] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.516588] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.516709] TCP: Hash tables configured (established 131072 bind 65536)
[    0.516711] TCP reno registered
[    0.524124] NET: Registered protocol family 1
[    0.524252] checking if image is initramfs... it is
[    1.084123] Freeing initrd memory: 7368k freed
[    1.084308] cpufreq: No nForce2 chipset.
[    1.084434] audit: initializing netlink socket (disabled)
[    1.084455] type=2000 audit(1251955591.080:1): initialized
[    1.091020] highmem bounce pool size: 64 pages
[    1.091024] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    1.092231] VFS: Disk quotas dquot_6.5.1
[    1.092284] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    1.092827] fuse init (API version 7.10)
[    1.092902] msgmni has been set to 1724
[    1.093062] alg: No test for stdrng (krng)
[    1.093071] io scheduler noop registered
[    1.093073] io scheduler anticipatory registered
[    1.093075] io scheduler deadline registered
[    1.093087] io scheduler cfq registered (default)
[    1.093096] pci 0000:00:02.0: Boot video device
[    1.094868] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    1.094876] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    1.095002] input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input0
[    1.095004] ACPI: Power Button (FF) [PWRF]
[    1.095042] input: Power Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1
[    1.095045] ACPI: Power Button (CM) [PWRB]
[    1.095398] ACPI: SSDT 3DCE7280, 022A (r1  PmRef  Cpu0Ist     3000 INTL 20040311)
[    1.095600] ACPI: CPU0 (power states: C1[C1] C2[C2])
[    1.095622] processor ACPI_CPU:00: registered as cooling_device0
[    1.095625] ACPI: Processor [CPU0] (supports 8 throttling states)
[    1.095786] ACPI: SSDT 3DCE7740, 0152 (r1  PmRef  Cpu1Ist     3000 INTL 20040311)
[    1.095977] ACPI: CPU1 (power states: C1[C1] C2[C2])
[    1.095993] processor ACPI_CPU:01: registered as cooling_device1
[    1.095997] ACPI: Processor [CPU1] (supports 8 throttling states)
[    1.097313] isapnp: Scanning for PnP cards...
[    1.450213] isapnp: No Plug & Play device found
[    1.456750] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
[    1.456854] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.457207] 00:08: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.457943] brd: module loaded
[    1.458222] loop: module loaded
[    1.458281] Fixed MDIO Bus: probed
[    1.458287] PPP generic driver version 2.4.2
[    1.458334] input: Macintosh mouse button emulation as /devices/virtual/input/input2
[    1.458359] Driver 'sd' needs updating - please use bus_type methods
[    1.458368] Driver 'sr' needs updating - please use bus_type methods
[    1.458429] ata_piix 0000:00:1f.2: version 2.12
[    1.458442] ata_piix 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    1.458445] ata_piix 0000:00:1f.2: MAP [ P0 P2 IDE IDE ]
[    1.458477] ata_piix 0000:00:1f.2: setting latency timer to 64
[    1.458541] scsi0 : ata_piix
[    1.458609] scsi1 : ata_piix
[    1.459197] ata1: SATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xf000 irq 14
[    1.459200] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xf008 irq 15
[    1.648201] ata1.00: HPA unlocked: 488395055 -> 488397168, native 488397168
[    1.648207] ata1.00: ATA-8: ST3250318AS, CC35, max UDMA/133
[    1.648210] ata1.00: 488397168 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    1.664425] ata1.00: configured for UDMA/133
[    1.828358] ata2.01: ATAPI: HL-DT-ST DVDRAM GSA-H12N, UL02, max UDMA/66
[    1.844313] ata2.01: configured for UDMA/66
[    1.846714] scsi 0:0:0:0: Direct-Access     ATA      ST3250318AS      CC35 PQ: 0 ANSI: 5
[    1.846831] sd 0:0:0:0: [sda] 488397168 512-byte hardware sectors: (250 GB/232 GiB)
[    1.846846] sd 0:0:0:0: [sda] Write Protect is off
[    1.846848] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.846871] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.846926] sd 0:0:0:0: [sda] 488397168 512-byte hardware sectors: (250 GB/232 GiB)
[    1.846939] sd 0:0:0:0: [sda] Write Protect is off
[    1.846942] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.846964] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.846967]  sda: sda1 sda2 < sda5 sda6 sda7 sda8 >
[    1.909121] sd 0:0:0:0: [sda] Attached SCSI disk
[    1.909171] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.912926] scsi 1:0:1:0: CD-ROM            HL-DT-ST DVDRAM GSA-H12N  UL02 PQ: 0 ANSI: 5
[    1.925231] sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
[    1.925234] Uniform CD-ROM driver Revision: 3.20
[    1.925333] sr 1:0:1:0: Attached scsi CD-ROM sr0
[    1.925376] sr 1:0:1:0: Attached scsi generic sg1 type 5
[    1.925933] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    1.925950] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    1.925964] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    1.925967] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    1.926018] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 1
[    1.929922] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
[    1.929934] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xf2504000
[    1.944040] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    1.944110] usb usb1: configuration #1 chosen from 1 choice
[    1.944141] hub 1-0:1.0: USB hub found
[    1.944150] hub 1-0:1.0: 8 ports detected
[    1.944292] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    1.944305] uhci_hcd: USB Universal Host Controller Interface driver
[    1.944321] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    1.944326] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    1.944329] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    1.944368] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    1.944389] uhci_hcd 0000:00:1d.0: irq 23, io base 0x0000e000
[    1.944452] usb usb2: configuration #1 chosen from 1 choice
[    1.944474] hub 2-0:1.0: USB hub found
[    1.944480] hub 2-0:1.0: 2 ports detected
[    1.944548] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    1.944553] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    1.944556] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    1.944593] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3
[    1.944619] uhci_hcd 0000:00:1d.1: irq 19, io base 0x0000e100
[    1.944679] usb usb3: configuration #1 chosen from 1 choice
[    1.944701] hub 3-0:1.0: USB hub found
[    1.944707] hub 3-0:1.0: 2 ports detected
[    1.944780] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    1.944787] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    1.944789] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    1.944826] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4
[    1.944852] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000e200
[    1.944912] usb usb4: configuration #1 chosen from 1 choice
[    1.944935] hub 4-0:1.0: USB hub found
[    1.944940] hub 4-0:1.0: 2 ports detected
[    1.945010] uhci_hcd 0000:00:1d.3: PCI INT D -> GSI 16 (level, low) -> IRQ 16
[    1.945015] uhci_hcd 0000:00:1d.3: setting latency timer to 64
[    1.945018] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[    1.945054] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 5
[    1.945082] uhci_hcd 0000:00:1d.3: irq 16, io base 0x0000e300
[    1.945143] usb usb5: configuration #1 chosen from 1 choice
[    1.945165] hub 5-0:1.0: USB hub found
[    1.945171] hub 5-0:1.0: 2 ports detected
[    1.945295] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    1.945619] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.945625] serio: i8042 AUX port at 0x60,0x64 irq 12
[    1.948043] mice: PS/2 mouse device common for all mice
[    1.948205] rtc_cmos 00:04: RTC can wake from S4
[    1.948242] rtc_cmos 00:04: rtc core: registered rtc_cmos as rtc0
[    1.948275] rtc0: alarms up to one month, 242 bytes nvram, hpet irqs
[    1.948326] device-mapper: uevent: version 1.0.3
[    1.948400] device-mapper: ioctl: 4.14.0-ioctl (2008-04-23) initialised: [email]dm-devel@redhat.com[/email]
[    1.948465] device-mapper: multipath: version 1.0.5 loaded
[    1.948468] device-mapper: multipath round-robin: version 1.0.0 loaded
[    1.948535] EISA: Probing bus 0 at eisa.0
[    1.948561] EISA: Detected 0 cards.
[    1.948627] cpuidle: using governor ladder
[    1.948683] cpuidle: using governor menu
[    1.949135] TCP cubic registered
[    1.949221] NET: Registered protocol family 10
[    1.949605] lo: Disabled Privacy Extensions
[    1.949904] NET: Registered protocol family 17
[    1.949918] Bluetooth: L2CAP ver 2.11
[    1.949920] Bluetooth: L2CAP socket layer initialized
[    1.949923] Bluetooth: SCO (Voice Link) ver 0.6
[    1.949924] Bluetooth: SCO socket layer initialized
[    1.949943] Bluetooth: RFCOMM socket layer initialized
[    1.949948] Bluetooth: RFCOMM TTY layer initialized
[    1.949950] Bluetooth: RFCOMM ver 1.10
[    1.952065] Using IPI No-Shortcut mode
[    1.952158] registered taskstats version 1
[    1.952254]   Magic number: 9:145:415
[    1.952311] rtc_cmos 00:04: setting system clock to 2009-09-03 05:26:32 UTC (1251955592)
[    1.952314] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.952316] EDD information not available.
[    1.952496] Freeing unused kernel memory: 532k freed
[    1.952618] Write protecting the kernel text: 4116k
[    1.952659] Write protecting the kernel read-only data: 1524k
[    1.966716] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3
[    2.138720] Floppy drive(s): fd0 is 1.44M
[    2.159749] FDC 0 is a post-1991 82077
[    2.164516] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    2.164538] r8169 0000:01:05.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[    2.164592] r8169 0000:01:05.0: no PCI Express capability
[    2.165157] eth0: RTL8169sc/8110sc at 0xf7cc2000, 00:1f:d0:d2:f4:9b, XID 18000000 IRQ 21
[    2.256529] usb 1-8: new high speed USB device using ehci_hcd and address 2
[    2.390287] usb 1-8: configuration #1 chosen from 1 choice
[    2.394451] Initializing USB Mass Storage driver...
[    2.394897] scsi2 : SCSI emulation for USB Mass Storage devices
[    2.395016] usb-storage: device found at 2
[    2.395019] usb-storage: waiting for device to settle before scanning
[    2.395028] usbcore: registered new interface driver usb-storage
[    2.395031] USB Mass Storage support registered.
[    2.522739] PM: Starting manual resume from disk
[    2.522742] PM: Resume from partition 8:8
[    2.522743] PM: Checking hibernation image.
[    2.522913] PM: Resume from disk failed.
[    2.539925] kjournald starting.  Commit interval 5 seconds
[    2.539939] EXT3-fs: mounted filesystem with ordered data mode.
[    5.972662] udev: starting version 141
[    6.352965] intel_rng: FWH not detected
[    6.365071] Linux agpgart interface v0.103
[    6.392745] input: PC Speaker as /devices/platform/pcspkr/input/input4
[    6.399304] agpgart-intel 0000:00:00.0: Intel G41 Chipset
[    6.400269] agpgart-intel 0000:00:00.0: detected 32764K stolen memory
[    6.403031] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xe0000000
[    6.717092] iTCO_vendor_support: vendor-support=0
[    6.718430] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.05
[    6.718524] iTCO_wdt: Found a ICH7 or ICH7R TCO device (Version=2, TCOBASE=0x0460)
[    6.718571] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[    6.759306] synaptics was reset on resume, see synaptics_resume_reset if you have trouble on resume
[    6.780460] Linux video capture interface: v2.00
[    6.828906] saa7130/34: v4l2 driver version 0.2.14 loaded
[    6.828947] saa7134 0000:01:02.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    6.828953] saa7133[0]: found at 0000:01:02.0, rev: 209, irq: 18, latency: 32, mmio: 0xf1001000
[    6.828958] saa7133[0]: subsystem: 185b:c900, board: Compro VideoMate T750 [card=139,autodetected]
[    6.828983] saa7133[0]: board init: gpio is 84bf00
[    6.828988] saa7133[0]: Oops: IR config error [card=139]
[    6.933478] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    6.933522] HDA Intel 0000:00:1b.0: setting latency timer to 64
[    6.980041] saa7133[0]: i2c eeprom 00: 5b 18 00 c9 54 20 1c 00 43 43 a9 1c 55 d2 b2 92
[    6.980055] saa7133[0]: i2c eeprom 10: 00 ff 86 0f ff 20 ff ff ff ff ff ff ff ff ff ff
[    6.980069] saa7133[0]: i2c eeprom 20: 01 40 01 03 03 01 03 01 08 ff 00 89 ff ff ff ff
[    6.980082] saa7133[0]: i2c eeprom 30: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[    6.980095] saa7133[0]: i2c eeprom 40: ff d7 00 c4 86 1e 05 ff 02 c2 ff 01 ff ff ff ff
[    6.980108] saa7133[0]: i2c eeprom 50: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff cb
[    6.980121] saa7133[0]: i2c eeprom 60: 30 ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[    6.980134] saa7133[0]: i2c eeprom 70: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[    6.980147] saa7133[0]: i2c eeprom 80: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[    6.980160] saa7133[0]: i2c eeprom 90: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[    6.980173] saa7133[0]: i2c eeprom a0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[    6.980186] saa7133[0]: i2c eeprom b0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[    6.980199] saa7133[0]: i2c eeprom c0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[    6.980212] saa7133[0]: i2c eeprom d0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[    6.980224] saa7133[0]: i2c eeprom e0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[    6.980237] saa7133[0]: i2c eeprom f0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[    6.996697] tuner' 0-0061: chip found @ 0xc2 (saa7133[0])
[    7.004509] tuner' 0-0062: chip found @ 0xc4 (saa7133[0])
[    7.012033] tuner' 0-0063: chip found @ 0xc6 (saa7133[0])
[    7.020041] tuner' 0-0068: chip found @ 0xd0 (saa7133[0])
[    7.085980] xc2028 0-0061: creating new instance
[    7.085983] xc2028 0-0061: type set to XCeive xc2028/xc3028 tuner
[    7.085995] BUG: unable to handle kernel paging request at fffffff4
[    7.085999] IP: [<f80b62c0>] saa7134_board_init2+0x140/0x710 [saa7134]
[    7.086009] *pde = 007b7067 *pte = 00000000 
[    7.086013] Oops: 0000 [#1] SMP 
[    7.086016] last sysfs file: /sys/devices/pci0000:00/0000:00:1b.0/sound/card0/mixer/dev
[    7.086019] Dumping ftrace buffer:
[    7.086022]    (ftrace buffer empty)
[    7.086024] Modules linked in: tuner_xc2028 tuner snd_hda_intel snd_pcm_oss snd_mixer_oss snd_pcm snd_seq_dummy snd_seq_oss snd_seq_midi snd_rawmidi snd_seq_midi_event saa7134(+) snd_seq ir_common videodev snd_timer v4l1_compat compat_ioctl32 snd_seq_device v4l2_common iTCO_wdt iTCO_vendor_support snd psmouse videobuf_dma_sg soundcore intel_agp pcspkr serio_raw videobuf_core tveeprom snd_page_alloc agpgart usb_storage r8169 mii floppy fbcon tileblit font bitblit softcursor
[    7.086056] 
[    7.086059] Pid: 1458, comm: modprobe Not tainted (2.6.28-14-generic #47-Ubuntu) EG41M-S2H
[    7.086061] EIP: 0060:[<f80b62c0>] EFLAGS: 00010292 CPU: 0
[    7.086068] EIP is at saa7134_board_init2+0x140/0x710 [saa7134]
[    7.086070] EAX: 00000000 EBX: 00000000 ECX: f5d6dc38 EDX: 00000000
[    7.086072] ESI: 00000000 EDI: 00000000 EBP: 00000000 ESP: f5d6dc54
[    7.086074]  DS: 007b ES: 007b FS: 00d8 GS: 0033 SS: 0068
[    7.086076] Process modprobe (pid: 1458, ti=f5d6c000 task=f5d26480 task.ti=f5d6c000)
[    7.086078] Stack:
[    7.086080]  00000303 f5d6dc58 f5d6dc58 f6265000 f6679400 f6265000 f5d6dcd0 c014ae07
[    7.086086]  000000d0 f80b8889 656e7574 00000072 000000f0 f62654b0 00000000 f6265140
[    7.086092]  f80c2490 f62654b0 f5d6dcd0 f80b894d 65626f72 642d7000 006d6561 000005b2
[    7.086099] Call Trace:
[    7.086101]  [<c014ae07>] ? request_module+0x97/0xf0
[    7.086106]  [<f80b8889>] ? saa7134_i2c_eeprom+0xe9/0x110 [saa7134]
[    7.086116]  [<f80b894d>] ? saa7134_i2c_register+0x9d/0x120 [saa7134]
[    7.086124]  [<f80c1605>] ? saa7134_initdev+0x3d5/0x8dd [saa7134]
[    7.086134]  [<c02dcc6e>] ? pci_device_probe+0x5e/0x80
[    7.086139]  [<c034fa04>] ? really_probe+0x54/0x180
[    7.086143]  [<c02dc49e>] ? pci_match_device+0xbe/0xd0
[    7.086148]  [<c034fb6e>] ? driver_probe_device+0x3e/0x50
[    7.086151]  [<c034fc09>] ? __driver_attach+0x89/0x90
[    7.086154]  [<c034f323>] ? bus_for_each_dev+0x53/0x80
[    7.086157]  [<c02dcbb0>] ? pci_device_remove+0x0/0x40
[    7.086160]  [<c034f8c9>] ? driver_attach+0x19/0x20
[    7.086163]  [<c034fb80>] ? __driver_attach+0x0/0x90
[    7.086166]  [<c034ecf7>] ? bus_add_driver+0x1c7/0x240
[    7.086170]  [<c02dcbb0>] ? pci_device_remove+0x0/0x40
[    7.086173]  [<c034fda9>] ? driver_register+0x69/0x140
[    7.086177]  [<f80b8240>] ? saa7134_init+0x0/0x60 [saa7134]
[    7.086186]  [<c02dceca>] ? __pci_register_driver+0x4a/0x90
[    7.086189]  [<f80b8240>] ? saa7134_init+0x0/0x60 [saa7134]
[    7.086197]  [<f80b8292>] ? saa7134_init+0x52/0x60 [saa7134]
[    7.086206]  [<c010111e>] ? _stext+0x2e/0x170
[    7.086209]  [<c01a926c>] ? __vunmap+0x9c/0xe0
[    7.086213]  [<c0127cad>] ? update_curr+0x8d/0x1e0
[    7.086217]  [<c012c71c>] ? enqueue_entity+0x13c/0x360
[    7.086220]  [<c0128226>] ? wakeup_preempt_entity+0x76/0xb0
[    7.086223]  [<c0133b54>] ? try_to_wake_up+0x104/0x290
[    7.086228]  [<c01640e8>] ? sys_init_module+0x88/0x1b0
[    7.086231]  [<c0103f6b>] ? sysenter_do_call+0x12/0x2f
[    7.086235]  [<c0500000>] ? _read_lock_irq+0x10/0x20
[    7.086238] Code: 95 7b 44 c8 8b 55 90 8b 82 2c 01 00 00 89 5c 24 04 c7 04 24 b8 33 0c f8 89 44 24 08 e8 78 7b 44 c8 66 90 8b 45 90 e8 40 fd ff ff <8b> 5d f4 31 c0 8b 75 f8 8b 7d fc 89 ec 5d c3 90 8b 4d 90 8b 71 
[    7.086276] EIP: [<f80b62c0>] saa7134_board_init2+0x140/0x710 [saa7134] SS:ESP 0068:f5d6dc54
[    7.086286] ---[ end trace 6770c6879d5ff537 ]---
[    7.220934] psmouse serio1: ID: 10 00 64<7>usb-storage: device scan complete
[    7.427673] scsi 2:0:0:0: Direct-Access     ST310014 A                3.09 PQ: 0 ANSI: 0
[    7.429272] sd 2:0:0:0: [sdb] 20005649 512-byte hardware sectors: (10.2 GB/9.53 GiB)
[    7.430146] sd 2:0:0:0: [sdb] Write Protect is off
[    7.430150] sd 2:0:0:0: [sdb] Mode Sense: 03 00 00 00
[    7.430153] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[    7.431021] sd 2:0:0:0: [sdb] 20005649 512-byte hardware sectors: (10.2 GB/9.53 GiB)
[    7.431894] sd 2:0:0:0: [sdb] Write Protect is off
[    7.431897] sd 2:0:0:0: [sdb] Mode Sense: 03 00 00 00
[    7.431900] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[    7.431904]  sdb: sdb1
[    7.439467] sd 2:0:0:0: [sdb] Attached SCSI disk
[    7.439569] sd 2:0:0:0: Attached scsi generic sg2 type 0
[    7.739277] input: ImPS/2 Generic Wheel Mouse as /devices/platform/i8042/serio1/input/input5
[  186.237423] lp: driver loaded but no devices found
[  186.299023] Adding 3269188k swap on /dev/sda8.  Priority:-1 extents:1 across:3269188k
[  186.829471] EXT3 FS on sda7, internal journal
[  187.584934] kjournald starting.  Commit interval 5 seconds
[  187.585191] EXT3 FS on sda6, internal journal
[  187.585196] EXT3-fs: mounted filesystem with ordered data mode.
[  187.871333] type=1505 audit(1251919778.415:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=1950
[  187.912187] type=1505 audit(1251919778.459:3): operation="profile_load" name="/sbin/dhclient-script" name2="default" pid=1954
[  187.912257] type=1505 audit(1251919778.459:4): operation="profile_load" name="/sbin/dhclient3" name2="default" pid=1954
[  187.912292] type=1505 audit(1251919778.459:5): operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" name2="default" pid=1954
[  187.912325] type=1505 audit(1251919778.459:6): operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" name2="default" pid=1954
[  188.025366] type=1505 audit(1251919778.571:7): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=1959
[  188.025485] type=1505 audit(1251919778.571:8): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=1959
[  188.055147] type=1505 audit(1251919778.600:9): operation="profile_load" name="/usr/sbin/mysqld" name2="default" pid=1963
[  188.084835] type=1505 audit(1251919778.632:10): operation="profile_load" info="failed: profile already loaded" name="/usr/sbin/mysqld" name2="default" pid=1970
[  188.108883] type=1505 audit(1251919778.656:11): operation="profile_load" name="/usr/sbin/tcpdump" name2="default" pid=1976
[  191.865156] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[  191.865159] Bluetooth: BNEP filters: protocol multicast
[  191.879530] Bridge firewalling registered
[  192.719520] ppdev: user-space parallel port driver
[  193.605676] [drm] Initialized drm 1.1.0 20060810
[  193.617090] pci 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[  193.617095] pci 0000:00:02.0: setting latency timer to 64
[  193.617347] pci 0000:00:02.0: irq 2303 for MSI/MSI-X
[  193.617583] [drm] Initialized i915 1.6.0 20080730 on minor 0
[  193.618190] [drm:i915_setparam] *ERROR* unknown parameter 4
[  193.618209] [drm:i915_getparam] *ERROR* Unknown parameter 6
[  194.402618] [drm:i915_getparam] *ERROR* Unknown parameter 6
[  196.453477] r8169: eth0: link up
[  206.456024] eth0: no IPv6 routers present
[  224.435962] [drm:i915_getparam] *ERROR* Unknown parameter 6

---

### Post by warby1212 on 2009-09-03
I guess I'll just use windows...  :D

of course now I'll probably get some rant about how if I asked questions properly etc etc.......

no bites ?

---

### Post by pveurshout on 2009-09-20
> **warby1212 said:**
> 
[    7.086013] Oops: 0000 [#1] SMP 
[    7.086016] last sysfs file: /sys/devices/pci0000:00/0000:00:1b.0/sound/card0/mixer/dev
[    7.086019] Dumping ftrace buffer:
[    7.086022]    (ftrace buffer empty)
[    7.086024] Modules linked in: tuner_xc2028 tuner snd_hda_intel snd_pcm_oss snd_mixer_oss snd_pcm snd_seq_dummy snd_seq_oss snd_seq_midi snd_rawmidi snd_seq_midi_event saa7134(+) snd_seq ir_common videodev snd_timer v4l1_compat compat_ioctl32 snd_seq_device v4l2_common iTCO_wdt iTCO_vendor_support snd psmouse videobuf_dma_sg soundcore intel_agp pcspkr serio_raw videobuf_core tveeprom snd_page_alloc agpgart usb_storage r8169 mii floppy fbcon tileblit font bitblit softcursor
[    7.086056] 
[    7.086059] Pid: 1458, comm: modprobe Not tainted (2.6.28-14-generic #47-Ubuntu) EG41M-S2H
[    7.086061] EIP: 0060:[<f80b62c0>] EFLAGS: 00010292 CPU: 0
[    7.086068] EIP is at saa7134_board_init2+0x140/0x710 [saa7134]
[    7.086070] EAX: 00000000 EBX: 00000000 ECX: f5d6dc38 EDX: 00000000
[    7.086072] ESI: 00000000 EDI: 00000000 EBP: 00000000 ESP: f5d6dc54
[    7.086074]  DS: 007b ES: 007b FS: 00d8 GS: 0033 SS: 0068
[    7.086076] Process modprobe (pid: 1458, ti=f5d6c000 task=f5d26480 task.ti=f5d6c000)
[    7.086078] Stack:
[    7.086080]  00000303 f5d6dc58 f5d6dc58 f6265000 f6679400 f6265000 f5d6dcd0 c014ae07
[    7.086086]  000000d0 f80b8889 656e7574 00000072 000000f0 f62654b0 00000000 f6265140
[    7.086092]  f80c2490 f62654b0 f5d6dcd0 f80b894d 65626f72 642d7000 006d6561 000005b2
[    7.086099] Call Trace:
[    7.086101]  [<c014ae07>] ? request_module+0x97/0xf0
[    7.086106]  [<f80b8889>] ? saa7134_i2c_eeprom+0xe9/0x110 [saa7134]
[    7.086116]  [<f80b894d>] ? saa7134_i2c_register+0x9d/0x120 [saa7134]
[    7.086124]  [<f80c1605>] ? saa7134_initdev+0x3d5/0x8dd [saa7134]
[    7.086134]  [<c02dcc6e>] ? pci_device_probe+0x5e/0x80
[    7.086139]  [<c034fa04>] ? really_probe+0x54/0x180
[    7.086143]  [<c02dc49e>] ? pci_match_device+0xbe/0xd0
[    7.086148]  [<c034fb6e>] ? driver_probe_device+0x3e/0x50
[    7.086151]  [<c034fc09>] ? __driver_attach+0x89/0x90
[    7.086154]  [<c034f323>] ? bus_for_each_dev+0x53/0x80
[    7.086157]  [<c02dcbb0>] ? pci_device_remove+0x0/0x40
[    7.086160]  [<c034f8c9>] ? driver_attach+0x19/0x20
[    7.086163]  [<c034fb80>] ? __driver_attach+0x0/0x90
[    7.086166]  [<c034ecf7>] ? bus_add_driver+0x1c7/0x240
[    7.086170]  [<c02dcbb0>] ? pci_device_remove+0x0/0x40
[    7.086173]  [<c034fda9>] ? driver_register+0x69/0x140
[    7.086177]  [<f80b8240>] ? saa7134_init+0x0/0x60 [saa7134]
[    7.086186]  [<c02dceca>] ? __pci_register_driver+0x4a/0x90
[    7.086189]  [<f80b8240>] ? saa7134_init+0x0/0x60 [saa7134]
[    7.086197]  [<f80b8292>] ? saa7134_init+0x52/0x60 [saa7134]
[    7.086206]  [<c010111e>] ? _stext+0x2e/0x170
[    7.086209]  [<c01a926c>] ? __vunmap+0x9c/0xe0
[    7.086213]  [<c0127cad>] ? update_curr+0x8d/0x1e0
[    7.086217]  [<c012c71c>] ? enqueue_entity+0x13c/0x360
[    7.086220]  [<c0128226>] ? wakeup_preempt_entity+0x76/0xb0
[    7.086223]  [<c0133b54>] ? try_to_wake_up+0x104/0x290
[    7.086228]  [<c01640e8>] ? sys_init_module+0x88/0x1b0
[    7.086231]  [<c0103f6b>] ? sysenter_do_call+0x12/0x2f
[    7.086235]  [<c0500000>] ? _read_lock_irq+0x10/0x20
[    7.086238] Code: 95 7b 44 c8 8b 55 90 8b 82 2c 01 00 00 89 5c 24 04 c7 04 24 b8 33 0c f8 89 44 24 08 e8 78 7b 44 c8 66 90 8b 45 90 e8 40 fd ff ff <8b> 5d f4 31 c0 8b 75 f8 8b 7d fc 89 ec 5d c3 90 8b 4d 90 8b 71 
[    7.086276] EIP: [<f80b62c0>] saa7134_board_init2+0x140/0x710 [saa7134] SS:ESP 0068:f5d6dc54
[    7.086286] ---[ end trace 6770c6879d5ff537 ]---

Sorry to say, but these are *really* a pain in the ***. I've been getting them as well (though not at startup, but just randomly), and just can't manage to find out what they mean, let alone how to solve them. Have you tried reinstalling?

> **warby1212 said:**
> 
[    7.739277] input: ImPS/2 Generic Wheel Mouse as /devices/platform/i8042/serio1/input/input5
[  186.237423] lp: driver loaded but no devices found

Have you tried booting without your mouse (physically) connected?

---

### Post by MetroPietro on 2009-09-20
I have also had this problem; sometimes it hangs for as much as 10 minutes before it proceeds to boot with the step:
```
[  127.884676] udev: starting version 141
```
If this is due to a USB device, it may be the optical USB mouse I often plug in. As I scanned the web I also found commenter who suggested that a USB device which is **no longer plugged in** might be confusing the system, in which case fsck will no help, nor will rebuilding your initramfs. On that page they suggested resetting the BIOS, which sounds dreadful; but maybe that is the easiest or necessary path.

---

### Post by warby1212 on 2009-09-20
This is pretty amazing, I gave up on getting an answer to this question and after a year or two of using Ubuntu I just got sick of this particular problem which started with a new mother board and actually went back to the dark empire (XP) for a while. 

But suddenly it's fixed !!!

I'm sure it was the on board video which I couldn't get drivers for and I didn't want to shell out more money. Over the weekend though I started using an old CRT monitor for that PC and Ubuntu booted straight away. Fair enough I thought but I'm sure it won't work on the rectangular LCD (thinking it must be a screen res it can't handle but it did ! Now the thing is perfect and I can stay with Ubuntu.

Either: 
changing the monitor back and forth overwrote somethign bad or corrupt or
a recent bug fix in the auto download fixed it :P :) :popcorn: :guitar: 

Ps i did try swapping mouses. The error messages never made any sense to me.

---

