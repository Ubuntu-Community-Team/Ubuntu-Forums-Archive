---
title: "cannot see wirless connection after 9.04 upgrade"
date: 2009-05-27
forum: Installation &amp; Upgrades
---

### Post by unix1adm on 2009-05-27
I upgraded to the 9.04 today. I can see  and use my cell modem card but i cannot see my wireless networks. 

What happened?
When I go into the Network Connections under  system preferences I see the entry there but not in the upper right side where I use to see it. 

How do I get my wireless working agian. This si URGENT as  I need this laptop.

I am using another one to post this message but need my Linux one back online ASAP. Thanx for the help 

CJ

---

### Post by unix1adm on 2009-05-27
I also notice my wirless icon i snot light up. for somereason it looks like 9.0.4 dropped my driver??? 

can i go back to the 8.x OS...

---

### Post by regala on 2009-05-27
> **unix1adm said:**
> I also notice my wirless icon i snot light up. for somereason it looks like 9.0.4 dropped my driver??? 

can i go back to the 8.x OS...

what is your card ? (this is the least we have to know if we don't want to use a crystal ball)

:)

br, mathieu

---

### Post by unix1adm on 2009-05-27
how do i tell i know i wne through this on 8.10 but it worked. now after the 9.0.4 upgrade it does not. 

Give me the command you need me to run and I will.

---

### Post by unix1adm on 2009-05-27
here is th eout put of my dmesg

    0.513774] pci 0000:00:1f.0: quirk: region 1180-11bf claimed by ICH4 GPIO
[    0.513795] PCI: 0000:00:1f.1 reg 10 io port: [0, 7]
[    0.513802] PCI: 0000:00:1f.1 reg 14 io port: [0, 3]
[    0.513809] PCI: 0000:00:1f.1 reg 18 io port: [0, 7]
[    0.513817] PCI: 0000:00:1f.1 reg 1c io port: [0, 3]
[    0.513824] PCI: 0000:00:1f.1 reg 20 io port: [1860, 186f]
[    0.513831] PCI: 0000:00:1f.1 reg 24 32bit mmio: [0, 3ff]
[    0.513880] PCI: 0000:00:1f.3 reg 20 io port: [1880, 189f]
[    0.513922] PCI: 0000:00:1f.5 reg 10 io port: [1c00, 1cff]
[    0.513929] PCI: 0000:00:1f.5 reg 14 io port: [18c0, 18ff]
[    0.513936] PCI: 0000:00:1f.5 reg 18 32bit mmio: [c0000c00, c0000dff]
[    0.513943] PCI: 0000:00:1f.5 reg 1c 32bit mmio: [c0000800, c00008ff]
[    0.513969] pci 0000:00:1f.5: PME# supported from D0 D3hot D3cold
[    0.513974] pci 0000:00:1f.5: PME# disabled
[    0.513999] PCI: 0000:00:1f.6 reg 10 io port: [2400, 24ff]
[    0.514006] PCI: 0000:00:1f.6 reg 14 io port: [2000, 207f]
[    0.514041] pci 0000:00:1f.6: PME# supported from D0 D3hot D3cold
[    0.514046] pci 0000:00:1f.6: PME# disabled
[    0.514077] PCI: 0000:01:00.0 reg 10 32bit mmio: [e0000000, e7ffffff]
[    0.514084] PCI: 0000:01:00.0 reg 14 io port: [3000, 30ff]
[    0.514090] PCI: 0000:01:00.0 reg 18 32bit mmio: [c0100000, c010ffff]
[    0.514105] PCI: 0000:01:00.0 reg 30 32bit mmio: [0, 1ffff]
[    0.514120] pci 0000:01:00.0: supports D1
[    0.514123] pci 0000:01:00.0: supports D2
[    0.514153] PCI: bridge 0000:00:01.0 io port: [3000, 3fff]
[    0.514157] PCI: bridge 0000:00:01.0 32bit mmio: [c0100000, c01fffff]
[    0.514161] PCI: bridge 0000:00:01.0 32bit mmio pref: [e0000000, e7ffffff]
[    0.514196] PCI: 0000:02:00.0 reg 10 32bit mmio: [b0000000, b0000fff]
[    0.514211] pci 0000:02:00.0: supports D1
[    0.514213] pci 0000:02:00.0: supports D2
[    0.514215] pci 0000:02:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.514220] pci 0000:02:00.0: PME# disabled
[    0.514257] PCI: 0000:02:02.0 reg 10 32bit mmio: [c0200000, c020ffff]
[    0.516075] PCI: 0000:02:08.0 reg 10 32bit mmio: [c0210000, c0210fff]
[    0.516082] PCI: 0000:02:08.0 reg 14 io port: [8000, 803f]
[    0.516116] pci 0000:02:08.0: supports D1
[    0.516118] pci 0000:02:08.0: supports D2
[    0.516121] pci 0000:02:08.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.516126] pci 0000:02:08.0: PME# disabled
[    0.516154] pci 0000:00:1e.0: transparent bridge
[    0.516159] PCI: bridge 0000:00:1e.0 io port: [4000, 8fff]
[    0.516164] PCI: bridge 0000:00:1e.0 32bit mmio: [c0200000, cfffffff]
[    0.516170] PCI: bridge 0000:00:1e.0 32bit mmio pref: [e8000000, efffffff]
[    0.516196] bus 00 -> node 0
[    0.516204] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.516280] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.AGP_._PRT]
[    0.516312] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCI1._PRT]
[    0.520847] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 9 10 *11)
[    0.521132] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 9 10 *11)
[    0.521414] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 9 10 *11)
[    0.521694] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 9 10 *11)
[    0.521975] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 9 10 *11)
[    0.522234] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 9 10 11) *0, disabled.
[    0.522492] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 9 10 11) *0, disabled.
[    0.522779] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 9 10 *11)
[    0.522973] ACPI: Power Resource [PUBS] (on)
[    0.522973] Linux Plug and Play Support v0.97 (c) Adam Belay
[    0.522973] pnp: PnP ACPI init
[    0.522973] ACPI: bus type pnp registered
[    0.528850] pnp: PnP ACPI: found 13 devices
[    0.528853] ACPI: ACPI bus type pnp unregistered
[    0.528857] PnPBIOS: Disabled by ACPI PNP
[    0.529262] PCI: Using ACPI for IRQ routing
[    0.529383] NET: Registered protocol family 8
[    0.529383] NET: Registered protocol family 20
[    0.529383] NetLabel: Initializing
[    0.529383] NetLabel:  domain hash size = 128
[    0.529383] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.529383] NetLabel:  unlabeled traffic allowed by default
[    0.529383] tracer: 772 pages allocated for 65536 entries of 48 bytes
[    0.529383]    actual entries 65620
[    0.529383] AppArmor: AppArmor Filesystem Enabled
[    0.529383] ACPI: RTC can wake from S4
[    0.529383] system 00:00: iomem range 0x0-0x9ffff could not be reserved
[    0.529383] system 00:00: iomem range 0xc0000-0xc3fff could not be reserved
[    0.529383] system 00:00: iomem range 0xc4000-0xc7fff could not be reserved
[    0.529383] system 00:00: iomem range 0xc8000-0xcbfff could not be reserved
[    0.529383] system 00:00: iomem range 0xcc000-0xcffff could not be reserved
[    0.529383] system 00:00: iomem range 0xd0000-0xd3fff could not be reserved
[    0.529383] system 00:00: iomem range 0xdc000-0xdffff could not be reserved
[    0.529383] system 00:00: iomem range 0xe0000-0xe3fff could not be reserved
[    0.529383] system 00:00: iomem range 0xe4000-0xe7fff could not be reserved
[    0.529383] system 00:00: iomem range 0xe8000-0xebfff could not be reserved
[    0.529383] system 00:00: iomem range 0xec000-0xeffff could not be reserved
[    0.529383] system 00:00: iomem range 0xf0000-0xfffff could not be reserved
[    0.529383] system 00:00: iomem range 0x100000-0x5fffffff could not be reserved
[    0.529383] system 00:00: iomem range 0xfec00000-0xffffffff could not be reserved
[    0.529383] system 00:02: ioport range 0x1000-0x107f has been reserved
[    0.529383] system 00:02: ioport range 0x1180-0x11bf has been reserved
[    0.529383] system 00:02: ioport range 0x15e0-0x15ef has been reserved
[    0.529383] system 00:02: ioport range 0x1600-0x162f has been reserved
[    0.529383] system 00:02: ioport range 0x1632-0x167f has been reserved
[    0.529383] system 00:02: ioport range 0x1630-0x1631 has been reserved
[    0.565195] pci 0000:00:01.0: PCI bridge, secondary bus 0000:01
[    0.565199] pci 0000:00:01.0:   IO window: 0x3000-0x3fff
[    0.565204] pci 0000:00:01.0:   MEM window: 0xc0100000-0xc01fffff
[    0.565208] pci 0000:00:01.0:   PREFETCH window: 0x000000e0000000-0x000000e7ffffff
[    0.565216] pci 0000:02:00.0: CardBus bridge, secondary bus 0000:03
[    0.565219] pci 0000:02:00.0:   IO window: 0x004000-0x0040ff
[    0.565224] pci 0000:02:00.0:   IO window: 0x004400-0x0044ff
[    0.565229] pci 0000:02:00.0:   PREFETCH window: 0xe8000000-0xebffffff
[    0.565234] pci 0000:02:00.0:   MEM window: 0xc4000000-0xc7ffffff
[    0.565239] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:02
[    0.565243] pci 0000:00:1e.0:   IO window: 0x4000-0x8fff
[    0.565250] pci 0000:00:1e.0:   MEM window: 0xc0200000-0xcfffffff
[    0.565255] pci 0000:00:1e.0:   PREFETCH window: 0x000000e8000000-0x000000efffffff
[    0.565273] pci 0000:00:1e.0: setting latency timer to 64
[    0.565794] ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 11
[    0.565798] PCI: setting IRQ 11 as level-triggered
[    0.565803] pci 0000:02:00.0: PCI INT A -> Link[LNKA] -> GSI 11 (level, low) -> IRQ 11
[    0.565810] bus: 00 index 0 io port: [0, ffff]
[    0.565813] bus: 00 index 1 mmio: [0, ffffffff]
[    0.565816] bus: 01 index 0 io port: [3000, 3fff]
[    0.565818] bus: 01 index 1 mmio: [c0100000, c01fffff]
[    0.565821] bus: 01 index 2 mmio: [e0000000, e7ffffff]
[    0.565824] bus: 01 index 3 mmio: [0, 0]
[    0.565826] bus: 02 index 0 io port: [4000, 8fff]
[    0.565829] bus: 02 index 1 mmio: [c0200000, cfffffff]
[    0.565832] bus: 02 index 2 mmio: [e8000000, efffffff]
[    0.565835] bus: 02 index 3 io port: [0, ffff]
[    0.565837] bus: 02 index 4 mmio: [0, ffffffff]
[    0.565840] bus: 03 index 0 io port: [4000, 40ff]
[    0.565842] bus: 03 index 1 io port: [4400, 44ff]
[    0.565845] bus: 03 index 2 mmio: [e8000000, ebffffff]
[    0.565848] bus: 03 index 3 mmio: [c4000000, c7ffffff]
[    0.565859] NET: Registered protocol family 2
[    0.566006] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.566298] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.567227] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.567872] TCP: Hash tables configured (established 131072 bind 65536)
[    0.567877] TCP reno registered
[    0.568072] NET: Registered protocol family 1
[    0.568230] checking if image is initramfs... it is
[    1.068084] Switched to high resolution mode on CPU 0
[    1.434688] Freeing initrd memory: 8006k freed
[    1.434988] Simple Boot Flag at 0x35 set to 0x1
[    1.435508] audit: initializing netlink socket (disabled)
[    1.435532] type=2000 audit(1243436751.432:1): initialized
[    1.443340] highmem bounce pool size: 64 pages
[    1.443348] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    1.446238] VFS: Disk quotas dquot_6.5.1
[    1.446347] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    1.446485] msgmni has been set to 1752
[    1.446643] io scheduler noop registered
[    1.446647] io scheduler anticipatory registered
[    1.446650] io scheduler deadline registered
[    1.446665] io scheduler cfq registered (default)
[    1.446755] pci 0000:01:00.0: Boot video device
[    1.446770] pci 0000:02:08.0: Firmware left e100 interrupts enabled; disabling
[    1.447174] isapnp: Scanning for PnP cards...
[    1.800181] isapnp: No Plug & Play device found
[    1.842474] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
[    1.843807] serial 00:0a: activated
[    1.844096] 00:0a: ttyS0 at I/O 0x3f8 (irq = 4) is a NS16550A
[    1.844807] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 11
[    1.844813] serial 0000:00:1f.6: PCI INT B -> Link[LNKB] -> GSI 11 (level, low) -> IRQ 11
[    1.844822] serial 0000:00:1f.6: PCI INT B disabled
[    1.846737] brd: module loaded
[    1.846827] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[    1.846977] PNP: PS/2 Controller [PNP0303:KBD,PNP0f13:MOU] at 0x60,0x64 irq 1,12
[    1.852183] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.852195] serio: i8042 AUX port at 0x60,0x64 irq 12
[    1.852559] mice: PS/2 mouse device common for all mice
[    1.852735] rtc_cmos 00:06: rtc core: registered rtc_cmos as rtc0
[    1.852753] rtc0: alarms up to one month, y3k
[    1.852889] EISA: Probing bus 0 at eisa.0
[    1.852896] Cannot allocate resource for EISA slot 1
[    1.852899] Cannot allocate resource for EISA slot 2
[    1.852902] Cannot allocate resource for EISA slot 3
[    1.852905] Cannot allocate resource for EISA slot 4
[    1.852908] Cannot allocate resource for EISA slot 5
[    1.852910] Cannot allocate resource for EISA slot 6
[    1.852913] Cannot allocate resource for EISA slot 7
[    1.852916] Cannot allocate resource for EISA slot 8
[    1.852918] EISA: Detected 0 cards.
[    1.852923] cpuidle: using governor ladder
[    1.852926] cpuidle: using governor menu
[    1.853523] TCP cubic registered
[    1.853555] Using IPI No-Shortcut mode
[    1.853797] registered taskstats version 1
[    1.853932]   Magic number: 9:127:84
[    1.854081] rtc_cmos 00:06: setting system clock to 2009-05-27 15:05:52 UTC (1243436752)
[    1.854085] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.854088] EDD information not available.
[    1.854416] Freeing unused kernel memory: 424k freed
[    1.854473] Write protecting the kernel text: 2576k
[    1.854507] Write protecting the kernel read-only data: 936k
[    1.857487] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[    2.095332] fuse init (API version 7.9)
[    2.330974] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[    2.335998] processor ACPI0007:00: registered as cooling_device0
[    2.336018] ACPI: Processor [CPU] (supports 8 throttling states)
[    2.364797] thermal LNXTHERM:01: registered as thermal_zone0
[    2.366300] ACPI: Thermal Zone [THM0] (70 C)
[    3.253731] ACPI: ACPI Dock Station Driver
[    3.392106] usbcore: registered new interface driver usbfs
[    3.392142] usbcore: registered new interface driver hub
[    3.402678] usbcore: registered new device driver usb
[    3.405459] USB Universal Host Controller Interface driver v3.0
[    3.409053] uhci_hcd 0000:00:1d.0: power state changed by ACPI to D0
[    3.409066] uhci_hcd 0000:00:1d.0: PCI INT A -> Link[LNKA] -> GSI 11 (level, low) -> IRQ 11
[    3.409078] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    3.409082] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    3.409138] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[    3.409167] uhci_hcd 0000:00:1d.0: irq 11, io base 0x00001800
[    3.409390] usb usb1: configuration #1 chosen from 1 choice
[    3.409423] hub 1-0:1.0: USB hub found
[    3.409433] hub 1-0:1.0: 2 ports detected
[    3.511609] SCSI subsystem initialized
[    3.512801] uhci_hcd 0000:00:1d.1: power state changed by ACPI to D0
[    3.513307] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 11
[    3.513313] uhci_hcd 0000:00:1d.1: PCI INT B -> Link[LNKD] -> GSI 11 (level, low) -> IRQ 11
[    3.513324] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    3.513328] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    3.513359] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[    3.513384] uhci_hcd 0000:00:1d.1: irq 11, io base 0x00001820
[    3.513501] usb usb2: configuration #1 chosen from 1 choice
[    3.513539] hub 2-0:1.0: USB hub found
[    3.513547] hub 2-0:1.0: 2 ports detected
[    3.616932] ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 11
[    3.616939] uhci_hcd 0000:00:1d.2: PCI INT C -> Link[LNKC] -> GSI 11 (level, low) -> IRQ 11
[    3.616951] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    3.616955] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    3.616995] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
[    3.617022] uhci_hcd 0000:00:1d.2: irq 11, io base 0x00001840
[    3.617142] usb usb3: configuration #1 chosen from 1 choice
[    3.617178] hub 3-0:1.0: USB hub found
[    3.617187] hub 3-0:1.0: 2 ports detected
[    3.622558] e100: Intel(R) PRO/100 Network Driver, 3.5.23-k4-NAPI
[    3.622562] e100: Copyright(c) 1999-2006 Intel Corporation
[    3.626742] libata version 3.00 loaded.
[    3.721120] ehci_hcd 0000:00:1d.7: power state changed by ACPI to D0
[    3.721626] ACPI: PCI Interrupt Link [LNKH] enabled at IRQ 11
[    3.721632] ehci_hcd 0000:00:1d.7: PCI INT D -> Link[LNKH] -> GSI 11 (level, low) -> IRQ 11
[    3.721652] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    3.721657] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    3.721690] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 4
[    3.725608] ehci_hcd 0000:00:1d.7: debug port 1
[    3.725615] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
[    3.725626] ehci_hcd 0000:00:1d.7: irq 11, io mem 0xc0000000
[    3.740027] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    3.740166] usb usb4: configuration #1 chosen from 1 choice
[    3.740201] hub 4-0:1.0: USB hub found
[    3.740209] hub 4-0:1.0: 6 ports detected
[    3.846226] ACPI: PCI Interrupt Link [LNKE] enabled at IRQ 11
[    3.846233] e100 0000:02:08.0: PCI INT A -> Link[LNKE] -> GSI 11 (level, low) -> IRQ 11
[    3.870502] e100 0000:02:08.0: PME# disabled
[    3.873709] e100: eth0: e100_probe: addr 0xc0210000, irq 11, MAC addr 00:11:25:86:3d:04
[    3.876871] pata_acpi 0000:00:1f.1: enabling device (0005 -> 0007)
[    3.876880] pata_acpi 0000:00:1f.1: PCI INT A -> Link[LNKC] -> GSI 11 (level, low) -> IRQ 11
[    3.876918] pata_acpi 0000:00:1f.1: setting latency timer to 64
[    3.876935] pata_acpi 0000:00:1f.1: PCI INT A disabled
[    3.881259] ata_piix 0000:00:1f.1: version 2.12
[    3.881268] ata_piix 0000:00:1f.1: PCI INT A -> Link[LNKC] -> GSI 11 (level, low) -> IRQ 11
[    3.881298] ata_piix 0000:00:1f.1: setting latency timer to 64
[    3.882278] scsi0 : ata_piix
[    3.882404] scsi1 : ata_piix
[    3.883762] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0x1860 irq 14
[    3.883766] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x1868 irq 15
[    4.100302] ata1.00: ATA-8: WDC WD2500BEVE-00WZT0, 01.01A01, max UDMA/100
[    4.100307] ata1.00: 488397168 sectors, multi 16: LBA48 
[    4.108899] ata1.00: configured for UDMA/100
[    4.268010] Marking TSC unstable due to TSC halts in idle
[    4.272338] ata2.00: ATAPI: HL-DT-STCD-RW/DVD DRIVE GCC-4241N, 0202, max UDMA/33
[    4.288270] ata2.00: configured for UDMA/33
[    4.288420] scsi 0:0:0:0: Direct-Access     ATA      WDC WD2500BEVE-0 01.0 PQ: 0 ANSI: 5
[    4.293622] scsi 1:0:0:0: CD-ROM            HL-DT-ST RW/DVD GCC-4241N 0202 PQ: 0 ANSI: 5
[    4.305960] scsi 0:0:0:0: Attached scsi generic sg0 type 0
[    4.306004] scsi 1:0:0:0: Attached scsi generic sg1 type 5
[    4.331390] Driver 'sd' needs updating - please use bus_type methods
[    4.331527] sd 0:0:0:0: [sda] 488397168 512-byte hardware sectors (250059 MB)
[    4.331557] sd 0:0:0:0: [sda] Write Protect is off
[    4.331560] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    4.331608] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.331705] sd 0:0:0:0: [sda] 488397168 512-byte hardware sectors (250059 MB)
[    4.331731] sd 0:0:0:0: [sda] Write Protect is off
[    4.331735] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    4.331782] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.331788]  sda:<4>Driver 'sr' needs updating - please use bus_type methods
[    4.342441]  sda1 sda2 sda3 sda4
[    4.360421] sd 0:0:0:0: [sda] Attached SCSI disk
[    4.375928] sr0: scsi3-mmc drive: 24x/24x writer cd/rw xa/form2 cdda tray
[    4.375933] Uniform CD-ROM driver Revision: 3.20
[    4.376096] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    5.064113] Clocksource tsc unstable (delta = -78240442 ns)
[    9.885760] kjournald starting.  Commit interval 5 seconds
[    9.885777] EXT3-fs: mounted filesystem with ordered data mode.
[   16.120444] udev: starting version 141
[   16.297340] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   16.321432] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   16.386034] irda_init()
[   16.386047] NET: Registered protocol family 23
[   16.646276] input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input2
[   16.652118] ACPI: Power Button (FF) [PWRF]
[   16.652210] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input3
[   16.652760] ACPI: Lid Switch [LID]
[   16.654102] input: Sleep Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input4
[   16.661754] ACPI: Battery Slot [BAT0] (battery present)
[   16.666446] ACPI: \_SB_.PCI0.IDE0.SCND.MSTR: found ejectable bay
[   16.666453] ACPI: \_SB_.PCI0.IDE0.SCND.MSTR: Adding notify handler
[   16.666564] ACPI: Error installing bay notify handler
[   16.668055] ACPI: Sleep Button (CM) [SLPB]
[   16.669030] ACPI: AC Adapter [AC] (on-line)
[   16.669482] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A03:00/device:03/device:04/input/input5
[   16.684129] ACPI: Video Device [VID] (multi-head: yes  rom: no  post: no)
[   16.692207] Linux agpgart interface v0.103
[   16.720364] nsc-ircc 00:0c: activated
[   16.720370] nsc_ircc_pnp_probe() : From PnP, found firbase 0x2F8 ; irq 3 ; dma 1.
[   16.720549] nsc-ircc, chip->init
[   16.720558] nsc-ircc, Found chip at base=0x02e
[   16.720582] nsc-ircc, driver loaded (Dag Brattli)
[   16.721041] IrDA: Registered device irda0
[   16.721044] nsc-ircc, Using dongle: IBM31T1100 or Temic TFDS6000/TFDS6500
[   16.731336] Non-volatile memory driver v1.2
[   16.799926] input: PC Speaker as /devices/platform/pcspkr/input/input6
[   16.965967] intel_rng: FWH not detected
[   17.020992] parport_pc 00:0b: reported by Plug and Play ACPI
[   17.021035] parport0: PC-style at 0x3bc, irq 7 [PCSPP,TRISTATE]
[   17.048734] agpgart-intel 0000:00:00.0: Intel 855PM Chipset
[   17.063774] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xd0000000
[   17.379199] iTCO_vendor_support: vendor-support=0
[   17.392097] Yenta: CardBus bridge found at 0000:02:00.0 [1014:0552]
[   17.392117] Yenta: Using INTVAL to route CSC interrupts to PCI
[   17.392119] Yenta: Routing CardBus interrupts to PCI
[   17.392125] Yenta TI: socket 0000:02:00.0, mfunc 0x01d21b22, devctl 0x64
[   17.419107] ppdev: user-space parallel port driver
[   17.419376] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.03 (30-Apr-2008)
[   17.625916] Yenta: ISA IRQ mask 0x0430, PCI irq 11
[   17.625921] Socket status: 30000020
[   17.625926] pcmcia: parent PCI bridge I/O window: 0x4000 - 0x8fff
[   17.625929] cs: IO port probe 0x4000-0x8fff: clean.
[   17.627330] pcmcia: parent PCI bridge Memory window: 0xc0200000 - 0xcfffffff
[   17.627333] pcmcia: parent PCI bridge Memory window: 0xe8000000 - 0xefffffff
[   17.705810] Intel ICH 0000:00:1f.5: PCI INT B -> Link[LNKB] -> GSI 11 (level, low) -> IRQ 11
[   17.705833] Intel ICH 0000:00:1f.5: setting latency timer to 64
[   18.029786] Synaptics Touchpad, model: 1, fw: 5.9, id: 0x2c6ab1, caps: 0x884793/0x0
[   18.029792] serio: Synaptics pass-through port at isa0060/serio1/input0
[   18.081625] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input7
[   18.085161] thinkpad_acpi: ThinkPad ACPI Extras v0.21
[   18.085165] thinkpad_acpi: [http://ibm-acpi.sf.net/](http://ibm-acpi.sf.net/)
[   18.085168] thinkpad_acpi: ThinkPad BIOS 1RETDJWW (3.15 ), EC 1RHT71WW-3.04
[   18.085171] thinkpad_acpi: IBM ThinkPad R51, model 1830WCW
[   18.089415] iTCO_wdt: Found a ICH4-M TCO device (Version=1, TCOBASE=0x1060)
[   18.089479] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   18.090451] Registered led device: tpacpi::thinklight
[   18.090716] thinkpad_acpi: another device driver is already handling bay events
[   18.090720] thinkpad_acpi: disabling subdriver bay
[   18.090753] Registered led device: tpacpi::power
[   18.090771] Registered led device: tpacpi:orange:batt
[   18.090789] Registered led device: tpacpi:green:batt
[   18.090807] Registered led device: tpacpi::dock_active
[   18.090825] Registered led device: tpacpi::bay_active
[   18.090843] Registered led device: tpacpi::dock_batt
[   18.090861] Registered led device: tpacpi::unknown_led
[   18.090879] Registered led device: tpacpi::standby
[   18.093837] input: ThinkPad Extra Buttons as /devices/virtual/input/input8
[   18.264125] pccard: CardBus card inserted into slot 0
[   18.264165] PCI: 0000:03:00.0 reg 10 32bit mmio: [0, fff]
[   18.264217] pci 0000:03:00.0: supports D1
[   18.264219] pci 0000:03:00.0: supports D2
[   18.264222] pci 0000:03:00.0: PME# supported from D0 D1 D2 D3hot
[   18.264228] pci 0000:03:00.0: PME# disabled
[   18.264262] PCI: 0000:03:00.1 reg 10 32bit mmio: [0, fff]
[   18.264311] pci 0000:03:00.1: supports D1
[   18.264313] pci 0000:03:00.1: supports D2
[   18.264316] pci 0000:03:00.1: PME# supported from D0 D1 D2 D3hot
[   18.264321] pci 0000:03:00.1: PME# disabled
[   18.408884] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
[   18.442999] cs: IO port probe 0x100-0x3af: clean.
[   18.444036] cs: IO port probe 0x3e0-0x4ff: excluding 0x4d0-0x4d7
[   18.444469] cs: IO port probe 0x820-0x8ff: clean.
[   18.444836] cs: IO port probe 0xc00-0xcf7: clean.
[   18.445350] cs: IO port probe 0xa00-0xaff: clean.
[   18.632042] intel8x0_measure_ac97_clock: measured 55357 usecs
[   18.632046] intel8x0: clocking to 48000
[   18.634248] ohci_hcd 0000:03:00.0: enabling device (0000 -> 0002)
[   18.634262] ohci_hcd 0000:03:00.0: PCI INT A -> Link[LNKA] -> GSI 11 (level, low) -> IRQ 11
[   18.634281] ohci_hcd 0000:03:00.0: setting latency timer to 64
[   18.634285] ohci_hcd 0000:03:00.0: OHCI Host Controller
[   18.634415] ohci_hcd 0000:03:00.0: new USB bus registered, assigned bus number 5
[   18.634435] ohci_hcd 0000:03:00.0: irq 11, io mem 0xc4000000
[   18.720727] usb usb5: configuration #1 chosen from 1 choice
[   18.721000] hub 5-0:1.0: USB hub found
[   18.721015] hub 5-0:1.0: 1 port detected
[   18.824400] ohci_hcd 0000:03:00.1: enabling device (0000 -> 0002)
[   18.824413] ohci_hcd 0000:03:00.1: PCI INT B -> Link[LNKA] -> GSI 11 (level, low) -> IRQ 11
[   18.824440] ohci_hcd 0000:03:00.1: setting latency timer to 64
[   18.824444] ohci_hcd 0000:03:00.1: OHCI Host Controller
[   18.825284] ohci_hcd 0000:03:00.1: new USB bus registered, assigned bus number 6
[   18.825310] ohci_hcd 0000:03:00.1: irq 11, io mem 0xc4001000
[   18.911238] usb usb6: configuration #1 chosen from 1 choice
[   18.913553] hub 6-0:1.0: USB hub found
[   18.913726] hub 6-0:1.0: 1 port detected
[   19.161414] lp0: using parport0 (interrupt-driven).
[   19.822024] EXT3 FS on sda1, internal journal
[   20.433678] type=1505 audit(1243436771.077:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=3977
[   20.496600] type=1505 audit(1243436771.141:3): operation="profile_load" name="/sbin/dhclient-script" name2="default" pid=3981
[   20.496756] type=1505 audit(1243436771.141:4): operation="profile_load" name="/sbin/dhclient3" name2="default" pid=3981
[   20.496813] type=1505 audit(1243436771.141:5): operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" name2="default" pid=3981
[   20.496862] type=1505 audit(1243436771.141:6): operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" name2="default" pid=3981
[   20.682371] type=1505 audit(1243436771.325:7): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=3986
[   20.682689] type=1505 audit(1243436771.325:8): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=3986
[   20.718582] type=1505 audit(1243436771.361:9): operation="profile_load" name="/usr/sbin/tcpdump" name2="default" pid=3990
[   21.099674] ACPI: WMI: Mapper loaded
[   21.153875] ACPI: \_SB_.PCI0.IDE0.SCND.MSTR: found ejectable bay
[   21.153883] ACPI: \_SB_.PCI0.IDE0.SCND.MSTR: Adding notify handler
[   21.153919] ACPI: Error installing bay notify handler
[   21.536048] usb 5-1: new full speed USB device using ohci_hcd and address 2
[   21.750731] usb 5-1: configuration #1 chosen from 1 choice
[   21.785612] cdc_acm 5-1:1.0: ttyACM0: USB ACM device
[   21.790269] usbcore: registered new interface driver cdc_acm
[   21.790393] cdc_acm: v0.26:USB Abstract Control Model driver for USB modems and ISDN adapters
[   23.410344] IBM TrackPoint firmware: 0x0e, buttons: 3/3
[   23.633145] input: TPPS/2 IBM TrackPoint as /devices/platform/i8042/serio1/serio2/input/input9
[   24.797225] vboxdrv: Trying to deactivate the NMI watchdog permanently...
[   24.797234] vboxdrv: Successfully done.
[   24.797237] vboxdrv: Found 1 processor cores.
[   24.798000] vboxdrv: TSC mode is 'synchronous', kernel timer mode is 'normal'.
[   24.798007] vboxdrv: Successfully loaded version 2.1.4_OSE (interface 0x000a0009).
[   26.210881] Bluetooth: Core ver 2.13
[   26.212672] NET: Registered protocol family 31
[   26.212687] Bluetooth: HCI device and connection manager initialized
[   26.212691] Bluetooth: HCI socket layer initialized
[   26.236142] Bluetooth: L2CAP ver 2.11
[   26.236151] Bluetooth: L2CAP socket layer initialized
[   26.244949] Bluetooth: SCO (Voice Link) ver 0.6
[   26.244957] Bluetooth: SCO socket layer initialized
[   26.253604] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   26.253612] Bluetooth: BNEP filters: protocol multicast
[   26.296884] Bridge firewalling registered
[   26.297724] pan0: Dropping NETIF_F_UFO since no NETIF_F_HW_CSUM feature.
[   26.431180] Bluetooth: RFCOMM socket layer initialized
[   26.431445] Bluetooth: RFCOMM TTY layer initialized
[   26.431452] Bluetooth: RFCOMM ver 1.10
[   27.805005] pci 0000:01:00.0: power state changed by ACPI to D0
[   27.805412] pci 0000:01:00.0: PCI INT A -> Link[LNKA] -> GSI 11 (level, low) -> IRQ 11
[   27.860359] [drm] Initialized drm 1.1.0 20060810
[   27.882700] [drm] Initialized radeon 1.29.0 20080528 on minor 0
[   28.152098] agpgart-intel 0000:00:00.0: AGP 2.0 bridge
[   28.152130] agpgart-intel 0000:00:00.0: putting AGP V2 device into 4x mode
[   28.152168] pci 0000:01:00.0: putting AGP V2 device into 4x mode
[   28.386195] [drm] Setting GART location based on new memory map
[   28.386210] [drm] Loading R100 Microcode
[   28.386265] [drm] writeback test succeeded in 2 usecs
[   33.222373] NET: Registered protocol family 10
[   33.224251] lo: Disabled Privacy Extensions
[   33.225596] ADDRCONF(NETDEV_UP): eth0: link is not ready
[  792.000142] e100: eth0: e100_watchdog: link up, 100Mbps, full-duplex
[  792.000487] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[  792.480064] NET: Registered protocol family 17
[  802.792035] eth0: no IPv6 routers present
[  996.000325] e100: eth0: e100_watchdog: link down

---

### Post by unix1adm on 2009-05-27
this is an ibm r51 laptop if that helps

---

### Post by unix1adm on 2009-05-27
root@cj454-lt:~# lspci
00:00.0 Host bridge: Intel Corporation 82855PM Processor to I/O Controller (rev 03)
00:01.0 PCI bridge: Intel Corporation 82855PM Processor to AGP Controller (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 81)
00:1f.0 ISA bridge: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801DBM (ICH4-M) IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 01)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 01)
00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 01)
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility M7 LW [Radeon Mobility 7500]
02:00.0 CardBus bridge: Texas Instruments PCI4520 PC card Cardbus Controller (rev 01)
02:02.0 Ethernet controller: Atheros Communications Inc. AR5212 802.11abg NIC (rev 01)
02:08.0 Ethernet controller: Intel Corporation 82801DB PRO/100 VE (MOB) Ethernet Controller (rev 81)
03:00.0 USB Controller: NEC Corporation USB (rev 43)
03:00.1 USB Controller: NEC Corporation USB (rev 43)

---

### Post by unix1adm on 2009-05-27
root@cj454-lt:~# lshw -C network
  *-network:0 UNCLAIMED   
       description: Ethernet controller
       product: AR5212 802.11abg NIC
       vendor: Atheros Communications Inc.
       physical id: 2
       bus info: pci@0000:02:02.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: latency=80 maxlatency=28 mingnt=10
  *-network:1
       description: Ethernet interface
       product: 82801DB PRO/100 VE (MOB) Ethernet Controller
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0000:02:08.0
       logical name: eth0
       version: 81
       serial: 00:11:25:86:3d:04
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.23-k4-NAPI duplex=half firmware=N/A latency=66 link=no maxlatency=56 mingnt=8 module=e100 multicast=yes port=MII speed=10MB/s
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: ea:df:7b:09:4b:8f
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

---

### Post by unix1adm on 2009-05-27
i think i found it... adminstration hardware drivers. 

the drive was not activated.

---

