---
title: "Usb ports wont work/ please help"
date: 2009-05-28
forum: Hardware
---

### Post by DJXRAY on 2009-05-28
hello, I have a problem with my usb ports on linux. the OS doesn't recognize anything i plug in (flash drive , cell phone "G1" or any other device). its weird because they worked fine when i had windows installed before. Also when i plug in my phone, i get power but it doesnt mount at all and when i plug in the flash drive (sandisk cruzer) i get a steady light but no icon on the desktop or places.. is there any solution?

heres my  dmesg:

[    0.004159] Initializing cgroup subsys cpuacct
[    0.004161] Initializing cgroup subsys memory
[    0.004165] Initializing cgroup subsys freezer
[    0.004174] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[    0.004176] CPU: L2 Cache: 1024K (64 bytes/line)
[    0.004185] Checking 'hlt' instruction... OK.
[    0.020468] SMP alternatives: switching to UP code
[    0.124014] ACPI: Core revision 20080926
[    0.125492] ACPI: Checking initramfs for custom DSDT
[    0.384442] ..TIMER: vector=0x30 apic1=0 pin1=0 apic2=-1 pin2=-1
[    0.427100] CPU0: AMD Athlon(tm) 64 Processor 3700+ stepping 02
[    0.428001] Brought up 1 CPUs
[    0.428001] Total of 1 processors activated (4377.55 BogoMIPS).
[    0.428001] CPU0 attaching NULL sched-domain.
[    0.428001] net_namespace: 776 bytes
[    0.428001] Booting paravirtualized kernel on bare hardware
[    0.428001] Time:  4:09:05  Date: 05/28/09
[    0.428001] regulator: core version 0.5
[    0.428001] NET: Registered protocol family 16
[    0.428001] EISA bus registered
[    0.428001] ACPI: bus type pci registered
[    0.428001] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 255
[    0.428001] PCI: MCFG area at e0000000 reserved in E820
[    0.428001] PCI: Using MMCONFIG for extended config space
[    0.428001] PCI: Using configuration type 1 for base access
[    0.428001] ACPI: EC: Look up EC in DSDT
[    0.429751] ACPI: Interpreter enabled
[    0.429754] ACPI: (supports S0 S1 S3 S4 S5)
[    0.429772] ACPI: Using IOAPIC for interrupt routing
[    0.432865] ACPI: No dock devices found.
[    0.432873] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.432904] pci 0000:00:00.0: reg 18 io port: [0x4100-0x411f]
[    0.432909] pci 0000:00:00.0: reg 1c 64bit mmio: [0xe0000000-0xffffffff]
[    0.432999] pci 0000:00:12.0: reg 10 io port: [0xfe00-0xfe07]
[    0.433006] pci 0000:00:12.0: reg 14 io port: [0xfd00-0xfd03]
[    0.433014] pci 0000:00:12.0: reg 18 io port: [0xfc00-0xfc07]
[    0.433022] pci 0000:00:12.0: reg 1c io port: [0xfb00-0xfb03]
[    0.433029] pci 0000:00:12.0: reg 20 io port: [0xfa00-0xfa0f]
[    0.433037] pci 0000:00:12.0: reg 24 32bit mmio: [0xfe02f000-0xfe02f1ff]
[    0.433045] pci 0000:00:12.0: reg 30 32bit mmio: [0x000000-0x07ffff]
[    0.433058] pci 0000:00:12.0: supports D1 D2
[    0.433101] pci 0000:00:13.0: reg 10 32bit mmio: [0xfe02e000-0xfe02efff]
[    0.433188] pci 0000:00:13.1: reg 10 32bit mmio: [0xfe02d000-0xfe02dfff]
[    0.433283] pci 0000:00:13.2: reg 10 32bit mmio: [0xfe02c000-0xfe02cfff]
[    0.433330] pci 0000:00:13.2: supports D1 D2
[    0.433332] pci 0000:00:13.2: PME# supported from D0 D1 D2 D3hot
[    0.433336] pci 0000:00:13.2: PME# disabled
[    0.433385] pci 0000:00:14.0: reg 10 io port: [0x500-0x50f]
[    0.433392] pci 0000:00:14.0: reg 14 32bit mmio: [0xfe02b000-0xfe02b3ff]
[    0.433426] HPET not enabled in BIOS. You might try hpet=force boot option
[    0.433473] pci 0000:00:14.1: reg 10 io port: [0x00-0x07]
[    0.433480] pci 0000:00:14.1: reg 14 io port: [0x00-0x03]
[    0.433488] pci 0000:00:14.1: reg 18 io port: [0x00-0x07]
[    0.433496] pci 0000:00:14.1: reg 1c io port: [0x00-0x03]
[    0.433503] pci 0000:00:14.1: reg 20 io port: [0xf800-0xf80f]
[    0.433658] pci 0000:00:14.5: reg 10 32bit mmio: [0xfe02a000-0xfe02a0ff]
[    0.433785] pci 0000:01:05.0: reg 10 32bit mmio: [0xd8000000-0xdfffffff]
[    0.433789] pci 0000:01:05.0: reg 14 io port: [0xef00-0xefff]
[    0.433793] pci 0000:01:05.0: reg 18 32bit mmio: [0xfddf0000-0xfddfffff]
[    0.433801] pci 0000:01:05.0: reg 30 32bit mmio: [0x000000-0x01ffff]
[    0.433805] pci 0000:01:05.0: supports D1 D2
[    0.433818] pci 0000:00:01.0: bridge io port: [0xe000-0xefff]
[    0.433821] pci 0000:00:01.0: bridge 32bit mmio: [0xfdd00000-0xfddfffff]
[    0.433825] pci 0000:00:01.0: bridge 64bit mmio pref: [0xd8000000-0xdfffffff]
[    0.433873] pci 0000:02:00.0: reg 10 io port: [0xdf00-0xdfff]
[    0.433933] pci 0000:02:00.0: PME# supported from D3hot D3cold
[    0.433938] pci 0000:02:00.0: PME# disabled
[    0.433991] pci 0000:02:03.0: reg 10 io port: [0xde00-0xdeff]
[    0.434001] pci 0000:02:03.0: reg 14 32bit mmio: [0xfdcff000-0xfdcff0ff]
[    0.434039] pci 0000:02:03.0: reg 30 32bit mmio: [0x000000-0x00ffff]
[    0.434053] pci 0000:02:03.0: supports D1 D2
[    0.434054] pci 0000:02:03.0: PME# supported from D1 D2 D3hot D3cold
[    0.434060] pci 0000:02:03.0: PME# disabled
[    0.434111] pci 0000:02:04.0: reg 10 32bit mmio: [0xfdcfe000-0xfdcfe7ff]
[    0.434121] pci 0000:02:04.0: reg 14 io port: [0xdd00-0xdd7f]
[    0.434174] pci 0000:02:04.0: supports D2
[    0.434175] pci 0000:02:04.0: PME# supported from D2 D3hot D3cold
[    0.434181] pci 0000:02:04.0: PME# disabled
[    0.434240] pci 0000:00:14.4: transparent bridge
[    0.434248] pci 0000:00:14.4: bridge io port: [0xd000-0xdfff]
[    0.434253] pci 0000:00:14.4: bridge 32bit mmio: [0xfdc00000-0xfdcfffff]
[    0.434258] pci 0000:00:14.4: bridge 32bit mmio pref: [0xfde00000-0xfdefffff]
[    0.434269] bus 00 -> node 0
[    0.434274] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.434485] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P2P_._PRT]
[    0.434693] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.AGP_._PRT]
[    0.447910] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 10 11) *0, disabled.
[    0.448012] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 10 11) *0, disabled.
[    0.448104] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 10 11) *0, disabled.
[    0.448195] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 10 11) *0, disabled.
[    0.448287] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 *10 11)
[    0.448377] ACPI: PCI Interrupt Link [LNKF] (IRQs *3 4 5 6 7 10 11)
[    0.448467] ACPI: PCI Interrupt Link [LNK0] (IRQs 3 4 5 6 7 10 *11)
[    0.448558] ACPI: PCI Interrupt Link [LNK1] (IRQs 3 4 5 6 7 10 11) *0, disabled.
[    0.448654] ACPI: WMI: Mapper loaded
[    0.448781] SCSI subsystem initialized
[    0.448817] libata version 3.00 loaded.
[    0.448851] usbcore: registered new interface driver usbfs
[    0.448864] usbcore: registered new interface driver hub
[    0.448885] usbcore: registered new device driver usb
[    0.448969] PCI: Using ACPI for IRQ routing
[    0.448976] pci 0000:00:00.0: BAR 3: can't allocate resource
[    0.449058] Bluetooth: Core ver 2.13
[    0.449058] NET: Registered protocol family 31
[    0.449058] Bluetooth: HCI device and connection manager initialized
[    0.449058] Bluetooth: HCI socket layer initialized
[    0.449058] NET: Registered protocol family 8
[    0.449058] NET: Registered protocol family 20
[    0.449058] NetLabel: Initializing
[    0.449058] NetLabel:  domain hash size = 128
[    0.449058] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.449058] NetLabel:  unlabeled traffic allowed by default
[    0.449058] AppArmor: AppArmor Filesystem Enabled
[    0.449058] pnp: PnP ACPI init
[    0.449058] ACPI: bus type pnp registered
[    0.450103] pnp 00:0b: mem resource (0xcd000-0xcffff) overlaps 0000:00:00.0 BAR 3 (0x0-0x1fffffff), disabling
[    0.450106] pnp 00:0b: mem resource (0xf0000-0xf7fff) overlaps 0000:00:00.0 BAR 3 (0x0-0x1fffffff), disabling
[    0.450109] pnp 00:0b: mem resource (0xf8000-0xfbfff) overlaps 0000:00:00.0 BAR 3 (0x0-0x1fffffff), disabling
[    0.450112] pnp 00:0b: mem resource (0xfc000-0xfffff) overlaps 0000:00:00.0 BAR 3 (0x0-0x1fffffff), disabling
[    0.450115] pnp 00:0b: mem resource (0x0-0x9ffff) overlaps 0000:00:00.0 BAR 3 (0x0-0x1fffffff), disabling
[    0.450118] pnp 00:0b: mem resource (0x100000-0x3beeffff) overlaps 0000:00:00.0 BAR 3 (0x0-0x1fffffff), disabling
[    0.450162] pnp: PnP ACPI: found 12 devices
[    0.450163] ACPI: ACPI bus type pnp unregistered
[    0.450166] PnPBIOS: Disabled by ACPI PNP
[    0.450172] system 00:01: ioport range 0x228-0x22f has been reserved
[    0.450174] system 00:01: ioport range 0x40b-0x40b has been reserved
[    0.450177] system 00:01: ioport range 0x4d6-0x4d6 has been reserved
[    0.450179] system 00:01: ioport range 0xc00-0xc01 has been reserved
[    0.450181] system 00:01: ioport range 0xc14-0xc14 has been reserved
[    0.450183] system 00:01: ioport range 0xc50-0xc52 has been reserved
[    0.450186] system 00:01: ioport range 0xc6c-0xc6d has been reserved
[    0.450188] system 00:01: ioport range 0xc6f-0xc6f has been reserved
[    0.450190] system 00:01: ioport range 0xcd4-0xcdf has been reserved
[    0.450193] system 00:01: ioport range 0x4000-0x40fe has been reserved
[    0.450195] system 00:01: ioport range 0x4210-0x4217 has been reserved
[    0.450201] system 00:06: ioport range 0x4d0-0x4d1 has been reserved
[    0.450203] system 00:06: ioport range 0x800-0x87f has been reserved
[    0.450208] system 00:0a: iomem range 0xe0000000-0xefffffff has been reserved
[    0.450213] system 00:0b: iomem range 0x3bf00000-0x3bffffff has been reserved
[    0.450216] system 00:0b: iomem range 0x3bef0000-0x3befffff could not be reserved
[    0.450219] system 00:0b: iomem range 0xffff0000-0xffffffff has been reserved
[    0.450221] system 00:0b: iomem range 0x3c000000-0x3fffffff has been reserved
[    0.450224] system 00:0b: iomem range 0xfec00000-0xfec00fff has been reserved
[    0.450226] system 00:0b: iomem range 0xfee00000-0xfee00fff has been reserved
[    0.450229] system 00:0b: iomem range 0xfff80000-0xfffeffff has been reserved
[    0.486097] pci 0000:00:01.0: PCI bridge, secondary bus 0000:01
[    0.486100] pci 0000:00:01.0:   IO window: 0xe000-0xefff
[    0.486103] pci 0000:00:01.0:   MEM window: 0xfdd00000-0xfddfffff
[    0.486106] pci 0000:00:01.0:   PREFETCH window: 0x000000d8000000-0x000000dfffffff
[    0.486110] pci 0000:00:14.4: PCI bridge, secondary bus 0000:02
[    0.486113] pci 0000:00:14.4:   IO window: 0xd000-0xdfff
[    0.486119] pci 0000:00:14.4:   MEM window: 0xfdc00000-0xfdcfffff
[    0.486124] pci 0000:00:14.4:   PREFETCH window: 0x000000fde00000-0x000000fdefffff
[    0.486141] bus: 00 index 0 io port: [0x00-0xffff]
[    0.486143] bus: 00 index 1 mmio: [0x000000-0xffffffff]
[    0.486145] bus: 01 index 0 io port: [0xe000-0xefff]
[    0.486147] bus: 01 index 1 mmio: [0xfdd00000-0xfddfffff]
[    0.486149] bus: 01 index 2 mmio: [0xd8000000-0xdfffffff]
[    0.486150] bus: 01 index 3 mmio: [0x0-0x0]
[    0.486152] bus: 02 index 0 io port: [0xd000-0xdfff]
[    0.486154] bus: 02 index 1 mmio: [0xfdc00000-0xfdcfffff]
[    0.486156] bus: 02 index 2 mmio: [0xfde00000-0xfdefffff]
[    0.486158] bus: 02 index 3 io port: [0x00-0xffff]
[    0.486160] bus: 02 index 4 mmio: [0x000000-0xffffffff]
[    0.486169] NET: Registered protocol family 2
[    0.486192] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.486192] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.486192] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.486192] TCP: Hash tables configured (established 131072 bind 65536)
[    0.486192] TCP reno registered
[    0.486192] NET: Registered protocol family 1
[    0.486192] checking if image is initramfs...<7>Switched to high resolution mode on CPU 0
[    0.739637]  it is
[    1.013150] Freeing initrd memory: 7377k freed
[    1.013241] cpufreq: No nForce2 chipset.
[    1.013357] audit: initializing netlink socket (disabled)
[    1.013373] type=2000 audit(1243483745.012:1): initialized
[    1.020472] highmem bounce pool size: 64 pages
[    1.020478] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    1.021483] VFS: Disk quotas dquot_6.5.1
[    1.021530] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    1.022024] fuse init (API version 7.10)
[    1.022093] msgmni has been set to 1725
[    1.022234] alg: No test for stdrng (krng)
[    1.022243] io scheduler noop registered
[    1.022245] io scheduler anticipatory registered
[    1.022246] io scheduler deadline registered
[    1.022259] io scheduler cfq registered (default)
[    1.022267] pci 0000:00:00.0: MSI quirk detected; MSI disabled
[    1.022323] pci 0000:01:05.0: Boot video device
[    1.022393] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    1.022400] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    1.022514] input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input0
[    1.022516] ACPI: Power Button (FF) [PWRF]
[    1.022553] input: Power Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1
[    1.022555] ACPI: Power Button (CM) [PWRB]
[    1.022734] processor ACPI_CPU:00: registered as cooling_device0
[    1.022737] ACPI: Processor [CPU0] (supports 8 throttling states)
[    1.024149] isapnp: Scanning for PnP cards...
[    1.378214] isapnp: No Plug & Play device found
[    1.379233] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
[    1.379989] brd: module loaded
[    1.380254] loop: module loaded
[    1.380311] Fixed MDIO Bus: probed
[    1.380316] PPP generic driver version 2.4.2
[    1.380362] input: Macintosh mouse button emulation as /devices/virtual/input/input2
[    1.380382] Driver 'sd' needs updating - please use bus_type methods
[    1.380389] Driver 'sr' needs updating - please use bus_type methods
[    1.380470] sata_sil 0000:00:12.0: version 2.3
[    1.380508] sata_sil 0000:00:12.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[    1.380584] scsi0 : sata_sil
[    1.380648] scsi1 : sata_sil
[    1.380715] ata1: SATA max UDMA/100 mmio m512@0xfe02f000 tf 0xfe02f080 irq 22
[    1.380719] ata2: SATA max UDMA/100 mmio m512@0xfe02f000 tf 0xfe02f0c0 irq 22
[    1.700056] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    1.708486] ata1.00: ATA-7: ST3250823AS, 3.03, max UDMA/100
[    1.708488] ata1.00: 488397168 sectors, multi 16: LBA48 
[    1.716494] ata1.00: configured for UDMA/100
[    2.036039] ata2: SATA link down (SStatus 0 SControl 300)
[    2.036125] scsi 0:0:0:0: Direct-Access     ATA      ST3250823AS      3.03 PQ: 0 ANSI: 5
[    2.036197] sd 0:0:0:0: [sda] 488397168 512-byte hardware sectors: (250 GB/232 GiB)
[    2.036210] sd 0:0:0:0: [sda] Write Protect is off
[    2.036212] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    2.036231] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.036275] sd 0:0:0:0: [sda] 488397168 512-byte hardware sectors: (250 GB/232 GiB)
[    2.036285] sd 0:0:0:0: [sda] Write Protect is off
[    2.036287] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    2.036305] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.036308]  sda: sda1 sda2 < sda5 >
[    2.081870] sd 0:0:0:0: [sda] Attached SCSI disk
[    2.081904] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    2.082041] pata_atiixp 0000:00:14.1: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    2.082129] scsi2 : pata_atiixp
[    2.082172] scsi3 : pata_atiixp
[    2.083077] ata3: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xf800 irq 14
[    2.083079] ata4: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xf808 irq 15
[    2.452530] ata4.00: ATAPI: TSSTcorpCD/DVDW TS-H552L, 0614, max UDMA/33
[    2.508513] ata4.00: configured for UDMA/33
[    2.510026] scsi 3:0:0:0: CD-ROM            TSSTcorp CD/DVDW TS-H552L 0614 PQ: 0 ANSI: 5
[    2.519360] sr0: scsi3-mmc drive: 40x/40x writer cd/rw xa/form2 cdda tray
[    2.519363] Uniform CD-ROM driver Revision: 3.20
[    2.519435] sr 3:0:0:0: Attached scsi CD-ROM sr0
[    2.519464] sr 3:0:0:0: Attached scsi generic sg1 type 5
[    2.519804] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    2.519821] ehci_hcd 0000:00:13.2: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    2.519835] ehci_hcd 0000:00:13.2: EHCI Host Controller
[    2.519888] ehci_hcd 0000:00:13.2: new USB bus registered, assigned bus number 1
[    2.519944] ehci_hcd 0000:00:13.2: irq 19, io mem 0xfe02c000
[    2.528023] ehci_hcd 0000:00:13.2: USB 2.0 started, EHCI 1.00
[    2.528095] usb usb1: configuration #1 chosen from 1 choice
[    2.528121] hub 1-0:1.0: USB hub found
[    2.528129] hub 1-0:1.0: 8 ports detected
[    2.528232] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    2.528245] ohci_hcd 0000:00:13.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    2.528254] ohci_hcd 0000:00:13.0: OHCI Host Controller
[    2.528287] ohci_hcd 0000:00:13.0: new USB bus registered, assigned bus number 2
[    2.528302] ohci_hcd 0000:00:13.0: irq 19, io mem 0xfe02e000
[    2.588054] usb usb2: configuration #1 chosen from 1 choice
[    2.588073] hub 2-0:1.0: USB hub found
[    2.588083] hub 2-0:1.0: 4 ports detected
[    2.588162] ohci_hcd 0000:00:13.1: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    2.588171] ohci_hcd 0000:00:13.1: OHCI Host Controller
[    2.588202] ohci_hcd 0000:00:13.1: new USB bus registered, assigned bus number 3
[    2.588216] ohci_hcd 0000:00:13.1: irq 19, io mem 0xfe02d000
[    2.648046] usb usb3: configuration #1 chosen from 1 choice
[    2.648065] hub 3-0:1.0: USB hub found
[    2.648075] hub 3-0:1.0: 4 ports detected
[    2.648155] uhci_hcd: USB Universal Host Controller Interface driver
[    2.648197] usbcore: registered new interface driver libusual
[    2.648224] usbcore: registered new interface driver usbserial
[    2.648232] USB Serial support registered for generic
[    2.648243] usbcore: registered new interface driver usbserial_generic
[    2.648245] usbserial: USB Serial Driver core
[    2.648285] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    2.651173] serio: i8042 KBD port at 0x60,0x64 irq 1
[    2.651177] serio: i8042 AUX port at 0x60,0x64 irq 12
[    2.651276] mice: PS/2 mouse device common for all mice
[    2.651421] rtc_cmos 00:03: RTC can wake from S4
[    2.651447] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0
[    2.651473] rtc0: alarms up to one month, 242 bytes nvram
[    2.651521] device-mapper: uevent: version 1.0.3
[    2.651609] device-mapper: ioctl: 4.14.0-ioctl (2008-04-23) initialised: [EMAIL="dm-devel@redhat.com"]dm-devel@redhat.com[/EMAIL]
[    2.651648] device-mapper: multipath: version 1.0.5 loaded
[    2.651651] device-mapper: multipath round-robin: version 1.0.0 loaded
[    2.651713] EISA: Probing bus 0 at eisa.0
[    2.651732] Cannot allocate resource for EISA slot 4
[    2.651750] EISA: Detected 0 cards.
[    2.651775] cpuidle: using governor ladder
[    2.651777] cpuidle: using governor menu
[    2.652202] TCP cubic registered
[    2.652284] NET: Registered protocol family 10
[    2.652623] lo: Disabled Privacy Extensions
[    2.652876] NET: Registered protocol family 17
[    2.652889] Bluetooth: L2CAP ver 2.11
[    2.652890] Bluetooth: L2CAP socket layer initialized
[    2.652893] Bluetooth: SCO (Voice Link) ver 0.6
[    2.652894] Bluetooth: SCO socket layer initialized
[    2.652914] Bluetooth: RFCOMM socket layer initialized
[    2.652918] Bluetooth: RFCOMM TTY layer initialized
[    2.652920] Bluetooth: RFCOMM ver 1.10
[    2.652938] powernow-k8: Found 1 AMD Athlon(tm) 64 Processor 3700+ processors (1 cpu cores) (version 2.20.00)
[    2.652971] powernow-k8:    0 : fid 0xe (2200 MHz), vid 0x8
[    2.652973] powernow-k8:    1 : fid 0xc (2000 MHz), vid 0x8
[    2.652975] powernow-k8:    2 : fid 0xa (1800 MHz), vid 0xa
[    2.652977] powernow-k8:    3 : fid 0x2 (1000 MHz), vid 0x12
[    2.653011] Using IPI No-Shortcut mode
[    2.653060] registered taskstats version 1
[    2.653153]   Magic number: 9:136:162
[    2.653232] rtc_cmos 00:03: setting system clock to 2009-05-28 04:09:07 UTC (1243483747)
[    2.653235] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    2.653236] EDD information not available.
[    2.653613] Freeing unused kernel memory: 532k freed
[    2.653722] Write protecting the kernel text: 4128k
[    2.653760] Write protecting the kernel read-only data: 1532k
[    2.700518] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3
[    2.840029] usb 1-8: new high speed USB device using ehci_hcd and address 2
[    3.041140] 8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)
[    3.041165] 8139cp 0000:02:03.0: This (id 10ec:8139 rev 10) is not an 8139C+ compatible chip, use 8139too
[    3.043234] 8139too Fast Ethernet driver 0.9.28
[    3.043267] 8139too 0000:02:03.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    3.044769] eth0: RealTek RTL8139 at 0xde00, 00:16:17:3f:6b:8c, IRQ 20
[    3.044771] eth0:  Identified 8139 chip type 'RTL-8100B/8139D'
[    3.058456] ohci1394 0000:02:04.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[    3.111229] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[21]  MMIO=[fdcfe000-fdcfe7ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[    3.432796] PM: Starting manual resume from disk
[    3.432799] PM: Resume from partition 8:5
[    3.432801] PM: Checking hibernation image.
[    3.432971] PM: Resume from disk failed.
[    3.477588] kjournald starting.  Commit interval 5 seconds
[    3.477596] EXT3-fs: mounted filesystem with ordered data mode.
[    4.400111] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[0010dc0000f66c8b]
[    7.897263] ehci_hcd 0000:00:13.2: port 8 reset error -110
[    7.897324] hub 1-0:1.0: hub_port_status failed (err = -32)
[    8.101242] ehci_hcd 0000:00:13.2: port 8 reset error -110
[    8.101244] hub 1-0:1.0: hub_port_status failed (err = -32)
[    8.305318] ehci_hcd 0000:00:13.2: port 8 reset error -110
[    8.305321] hub 1-0:1.0: hub_port_status failed (err = -32)
[    8.509340] ehci_hcd 0000:00:13.2: port 8 reset error -110
[    8.509454] hub 1-0:1.0: hub_port_status failed (err = -32)
[    8.629398] udev: starting version 141
[    8.713257] ehci_hcd 0000:00:13.2: port 8 reset error -110
[    8.713264] hub 1-0:1.0: hub_port_status failed (err = -32)
[    8.713267] hub 1-0:1.0: Cannot enable port 8.  Maybe the USB cable is bad?
[    8.731939] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[    8.769981] ehci_hcd 0000:00:13.2: port 8 reset error -110
[    8.769988] hub 1-0:1.0: hub_port_status failed (err = -32)
[    8.973254] ehci_hcd 0000:00:13.2: port 8 reset error -110
[    8.973261] hub 1-0:1.0: hub_port_status failed (err = -32)
[    9.177253] ehci_hcd 0000:00:13.2: port 8 reset error -110
[    9.177260] hub 1-0:1.0: hub_port_status failed (err = -32)
[    9.255788] parport_pc 00:07: reported by Plug and Play ACPI
[    9.255831] parport0: PC-style at 0x378, irq 7 [PCSPP,EPP]
[    9.276441] Linux agpgart interface v0.103
[    9.294434] piix4_smbus 0000:00:14.0: SMBus Host Controller at 0x500, revision 0
[    9.337092] input: PC Speaker as /devices/platform/pcspkr/input/input4
[    9.348740] ppdev: user-space parallel port driver
[    9.381539] ehci_hcd 0000:00:13.2: port 8 reset error -110
[    9.381546] hub 1-0:1.0: hub_port_status failed (err = -32)
[    9.469754] synaptics was reset on resume, see synaptics_resume_reset if you have trouble on resume
[    9.484777] ATI IXP AC97 controller 0000:00:14.5: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    9.585251] ehci_hcd 0000:00:13.2: port 8 reset error -110
[    9.585257] hub 1-0:1.0: hub_port_status failed (err = -32)
[    9.585260] hub 1-0:1.0: Cannot enable port 8.  Maybe the USB cable is bad?
[    9.601714] lp0: using parport0 (interrupt-driven).
[    9.641786] ehci_hcd 0000:00:13.2: port 8 reset error -110
[    9.641792] hub 1-0:1.0: hub_port_status failed (err = -32)
[    9.659366] Adding 2811332k swap on /dev/sda5.  Priority:-1 extents:1 across:2811332k
[    9.845240] ehci_hcd 0000:00:13.2: port 8 reset error -110
[    9.845245] hub 1-0:1.0: hub_port_status failed (err = -32)
[    9.956925] psmouse serio1: ID: 10 00 64<3>ehci_hcd 0000:00:13.2: port 8 reset error -110
[   10.049253] hub 1-0:1.0: hub_port_status failed (err = -32)
[   10.187090] EXT3 FS on sda1, internal journal
[   10.253387] ehci_hcd 0000:00:13.2: port 8 reset error -110
[   10.253394] hub 1-0:1.0: hub_port_status failed (err = -32)
[   10.457240] ehci_hcd 0000:00:13.2: port 8 reset error -110
[   10.457252] hub 1-0:1.0: hub_port_status failed (err = -32)
[   10.457255] hub 1-0:1.0: Cannot enable port 8.  Maybe the USB cable is bad?
[   10.513233] ehci_hcd 0000:00:13.2: port 8 reset error -110
[   10.513235] hub 1-0:1.0: hub_port_status failed (err = -32)
[   10.518735] input: ImPS/2 Generic Wheel Mouse as /devices/platform/i8042/serio1/input/input5
[   10.717245] ehci_hcd 0000:00:13.2: port 8 reset error -110
[   10.717252] hub 1-0:1.0: hub_port_status failed (err = -32)
[   10.921241] ehci_hcd 0000:00:13.2: port 8 reset error -110
[   10.921248] hub 1-0:1.0: hub_port_status failed (err = -32)
[   11.125249] ehci_hcd 0000:00:13.2: port 8 reset error -110
[   11.125255] hub 1-0:1.0: hub_port_status failed (err = -32)
[   11.174364] type=1505 audit(1243483756.018:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=1844
[   11.221981] type=1505 audit(1243483756.066:3): operation="profile_load" name="/sbin/dhclient-script" name2="default" pid=1848
[   11.222110] type=1505 audit(1243483756.066:4): operation="profile_load" name="/sbin/dhclient3" name2="default" pid=1848
[   11.222154] type=1505 audit(1243483756.066:5): operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" name2="default" pid=1848
[   11.222193] type=1505 audit(1243483756.066:6): operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" name2="default" pid=1848
[   11.329240] ehci_hcd 0000:00:13.2: port 8 reset error -110
[   11.329247] hub 1-0:1.0: hub_port_status failed (err = -32)
[   11.329250] hub 1-0:1.0: Cannot enable port 8.  Maybe the USB cable is bad?
[   11.329262] hub 1-0:1.0: unable to enumerate USB device on port 8
[   11.357165] type=1505 audit(1243483756.202:7): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=1853
[   11.357358] type=1505 audit(1243483756.202:8): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=1853
[   11.385307] type=1505 audit(1243483756.230:9): operation="profile_load" name="/usr/sbin/tcpdump" name2="default" pid=1857
[   13.140149] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   13.140153] Bluetooth: BNEP filters: protocol multicast
[   13.163702] Bridge firewalling registered
[   13.980804] pci 0000:01:05.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   14.663069] [drm] Initialized drm 1.1.0 20060810
[   14.684202] [drm] Initialized radeon 1.29.0 20080528 on minor 0
[   15.155662] [drm] Setting GART location based on new memory map
[   15.156312] [drm] Loading R300 Microcode
[   15.156330] [drm] Num pipes: 4
[   15.156335] [drm] writeback test succeeded in 1 usecs
[   18.154210] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[   29.000024] eth0: no IPv6 routers present
[   76.984126] Clocksource tsc unstable (delta = -122382193 ns)
[  200.368064] usb 1-6: new high speed USB device using ehci_hcd and address 6
[  200.425315] ehci_hcd 0000:00:13.2: port 6 reset error -110
[  200.425323] hub 1-0:1.0: hub_port_status failed (err = -32)
[  200.629417] ehci_hcd 0000:00:13.2: port 6 reset error -110
[  200.629423] hub 1-0:1.0: hub_port_status failed (err = -32)
[  200.833350] ehci_hcd 0000:00:13.2: port 6 reset error -110
[  200.833355] hub 1-0:1.0: hub_port_status failed (err = -32)
[  201.037408] ehci_hcd 0000:00:13.2: port 6 reset error -110
[  201.037413] hub 1-0:1.0: hub_port_status failed (err = -32)
[  201.241346] ehci_hcd 0000:00:13.2: port 6 reset error -110
[  201.241351] hub 1-0:1.0: hub_port_status failed (err = -32)
[  201.241355] hub 1-0:1.0: Cannot enable port 6.  Maybe the USB cable is bad?
[  201.297324] ehci_hcd 0000:00:13.2: port 6 reset error -110
[  201.297329] hub 1-0:1.0: hub_port_status failed (err = -32)
[  201.501403] ehci_hcd 0000:00:13.2: port 6 reset error -110
[  201.501408] hub 1-0:1.0: hub_port_status failed (err = -32)
[  201.705410] ehci_hcd 0000:00:13.2: port 6 reset error -110
[  201.705415] hub 1-0:1.0: hub_port_status failed (err = -32)
[  201.909378] ehci_hcd 0000:00:13.2: port 6 reset error -110
[  201.909383] hub 1-0:1.0: hub_port_status failed (err = -32)
[  202.113408] ehci_hcd 0000:00:13.2: port 6 reset error -110
[  202.113414] hub 1-0:1.0: hub_port_status failed (err = -32)
[  202.113418] hub 1-0:1.0: Cannot enable port 6.  Maybe the USB cable is bad?
[  202.169335] ehci_hcd 0000:00:13.2: port 6 reset error -110
[  202.169340] hub 1-0:1.0: hub_port_status failed (err = -32)
[  202.373376] ehci_hcd 0000:00:13.2: port 6 reset error -110
[  202.373381] hub 1-0:1.0: hub_port_status failed (err = -32)
[  202.577409] ehci_hcd 0000:00:13.2: port 6 reset error -110
[  202.577414] hub 1-0:1.0: hub_port_status failed (err = -32)
[  202.781316] ehci_hcd 0000:00:13.2: port 6 reset error -110
[  202.781322] hub 1-0:1.0: hub_port_status failed (err = -32)
[  202.985390] ehci_hcd 0000:00:13.2: port 6 reset error -110
[  202.985396] hub 1-0:1.0: hub_port_status failed (err = -32)
[  202.985400] hub 1-0:1.0: Cannot enable port 6.  Maybe the USB cable is bad?
[  203.041341] ehci_hcd 0000:00:13.2: port 6 reset error -110
[  203.041346] hub 1-0:1.0: hub_port_status failed (err = -32)
[  203.245347] ehci_hcd 0000:00:13.2: port 6 reset error -110
[  203.245352] hub 1-0:1.0: hub_port_status failed (err = -32)
[  203.449407] ehci_hcd 0000:00:13.2: port 6 reset error -110
[  203.449413] hub 1-0:1.0: hub_port_status failed (err = -32)
[  203.653407] ehci_hcd 0000:00:13.2: port 6 reset error -110
[  203.653413] hub 1-0:1.0: hub_port_status failed (err = -32)
[  203.857327] ehci_hcd 0000:00:13.2: port 6 reset error -110
[  203.857332] hub 1-0:1.0: hub_port_status failed (err = -32)
[  203.857337] hub 1-0:1.0: Cannot enable port 6.  Maybe the USB cable is bad?
[  203.857350] hub 1-0:1.0: unable to enumerate USB device on port 6
[  206.836048] hub 1-0:1.0: Cannot enable port 8.  Maybe the USB cable is bad?
[  209.804050] hub 1-0:1.0: Cannot enable port 8.  Maybe the USB cable is bad?
[  212.772966] hub 1-0:1.0: Cannot enable port 8.  Maybe the USB cable is bad?
[  215.740143] hub 1-0:1.0: Cannot enable port 8.  Maybe the USB cable is bad?

i have a amd 64 compaq sr1318nx model.. please help

---

### Post by johenkel on 2009-10-30
Hi there,

I got a Compaq SR1817EL with the same problem.
I found this by searching my dmesg log output through google.com/

Did you find a solution ?

johenkel

---

