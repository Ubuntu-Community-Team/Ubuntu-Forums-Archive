---
title: "Se me queda congelado el puntero ayuda!!"
date: 2009-03-22
forum: Hardware
---

### Post by santi698 on 2009-03-22
Hola, tengo ubuntu 8.10 y al arrancar el mouse funciona bien por un ratito hasta q se queda congelado en un lugar, tengo un mouse inalambrico genius slimstar 600, necesito ayuda!!

---

### Post by Hei Ku on 2009-03-22
Poné que te aparece si pones en la terminal "dmesg" despues que se te congela el mouse.

---

### Post by santi698 on 2009-03-24
Me aparece esto:

[    0.639118] pci 0000:00:06.0: reg 20 io port: [0xffa0-0xffaf]
[    0.639152] pci 0000:00:07.0: reg 10 32bit mmio: [0xfcf78000-0xfcf7bfff]
[    0.639172] pci 0000:00:07.0: PME# supported from D3hot D3cold
[    0.639175] pci 0000:00:07.0: PME# disabled
[    0.639224] pci 0000:00:09.0: reg 10 io port: [0xd480-0xd487]
[    0.639228] pci 0000:00:09.0: reg 14 io port: [0xd400-0xd403]
[    0.639232] pci 0000:00:09.0: reg 18 io port: [0xd080-0xd087]
[    0.639235] pci 0000:00:09.0: reg 1c io port: [0xd000-0xd003]
[    0.639239] pci 0000:00:09.0: reg 20 io port: [0xcc00-0xcc0f]
[    0.639242] pci 0000:00:09.0: reg 24 32bit mmio: [0xfcf76000-0xfcf77fff]
[    0.639274] pci 0000:00:0a.0: reg 10 32bit mmio: [0xfcf7c000-0xfcf7cfff]
[    0.639277] pci 0000:00:0a.0: reg 14 io port: [0xc880-0xc887]
[    0.639281] pci 0000:00:0a.0: reg 18 32bit mmio: [0xfcf7f400-0xfcf7f4ff]
[    0.639285] pci 0000:00:0a.0: reg 1c 32bit mmio: [0xfcf7f000-0xfcf7f00f]
[    0.639296] pci 0000:00:0a.0: supports D1 D2
[    0.639298] pci 0000:00:0a.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.639302] pci 0000:00:0a.0: PME# disabled
[    0.639328] pci 0000:00:0b.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.639330] pci 0000:00:0b.0: PME# disabled
[    0.639475] pci 0000:00:10.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.639483] pci 0000:00:10.0: PME# disabled
[    0.639655] pci 0000:00:12.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.639662] pci 0000:00:12.0: PME# disabled
[    0.639807] pci 0000:00:08.0: transparent bridge
[    0.639827] pci 0000:02:00.0: reg 10 32bit mmio: [0xfd000000-0xfdffffff]
[    0.639833] pci 0000:02:00.0: reg 14 64bit mmio: [0xf0000000-0xf7ffffff]
[    0.639839] pci 0000:02:00.0: reg 1c 64bit mmio: [0xfa000000-0xfbffffff]
[    0.639842] pci 0000:02:00.0: reg 24 io port: [0xec00-0xec7f]
[    0.639846] pci 0000:02:00.0: reg 30 32bit mmio: [0xfebe0000-0xfebfffff]
[    0.639869] pci 0000:00:0b.0: bridge io port: [0xe000-0xefff]
[    0.639872] pci 0000:00:0b.0: bridge 32bit mmio: [0xfd000000-0xfebfffff]
[    0.639875] pci 0000:00:0b.0: bridge 64bit mmio pref: [0xf0000000-0xfbffffff]
[    0.640050] bus 00 -> node 0
[    0.640055] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.640504] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P1._PRT]
[    0.640677] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.IXVE._PRT]
[    0.640808] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.MXR0._PRT]
[    0.640952] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.BR12._PRT]
[    0.661324] ACPI: PCI Interrupt Link [LNKA] (IRQs 16 17 18 19) *0, disabled.
[    0.661645] ACPI: PCI Interrupt Link [LNKB] (IRQs 16 17 18 19) *0, disabled.
[    0.661967] ACPI: PCI Interrupt Link [LNKC] (IRQs 16 17 18 19) *0, disabled.
[    0.662289] ACPI: PCI Interrupt Link [LNKD] (IRQs 16 17 18 19) *0, disabled.
[    0.662609] ACPI: PCI Interrupt Link [LN0A] (IRQs 16 17 18 19) *10
[    0.662930] ACPI: PCI Interrupt Link [LN0B] (IRQs 16 17 18 19) *0, disabled.
[    0.663251] ACPI: PCI Interrupt Link [LN0C] (IRQs 16 17 18 19) *0, disabled.
[    0.663571] ACPI: PCI Interrupt Link [LN0D] (IRQs 16 17 18 19) *0, disabled.
[    0.663892] ACPI: PCI Interrupt Link [LN1A] (IRQs 16 17 18 19) *0, disabled.
[    0.664211] ACPI: PCI Interrupt Link [LN1B] (IRQs 16 17 18 19) *0, disabled.
[    0.664532] ACPI: PCI Interrupt Link [LN1C] (IRQs 16 17 18 19) *0, disabled.
[    0.664849] ACPI: PCI Interrupt Link [LN1D] (IRQs 16 17 18 19) *0, disabled.
[    0.665175] ACPI: PCI Interrupt Link [LN2A] (IRQs 16 17 18 19) *11
[    0.665496] ACPI: PCI Interrupt Link [LN2B] (IRQs 16 17 18 19) *0, disabled.
[    0.665819] ACPI: PCI Interrupt Link [LN2C] (IRQs 16 17 18 19) *0, disabled.
[    0.666141] ACPI: PCI Interrupt Link [LN2D] (IRQs 16 17 18 19) *0, disabled.
[    0.666463] ACPI: PCI Interrupt Link [LN3A] (IRQs 16 17 18 19) *0, disabled.
[    0.666785] ACPI: PCI Interrupt Link [LN3B] (IRQs 16 17 18 19) *0, disabled.
[    0.667108] ACPI: PCI Interrupt Link [LN3C] (IRQs 16 17 18 19) *0, disabled.
[    0.667431] ACPI: PCI Interrupt Link [LN3D] (IRQs 16 17 18 19) *0, disabled.
[    0.667754] ACPI: PCI Interrupt Link [LN4A] (IRQs 16 17 18 19) *0, disabled.
[    0.668091] ACPI: PCI Interrupt Link [LN4B] (IRQs 16 17 18 19) *0, disabled.
[    0.668413] ACPI: PCI Interrupt Link [LN4C] (IRQs 16 17 18 19) *0, disabled.
[    0.668735] ACPI: PCI Interrupt Link [LN4D] (IRQs 16 17 18 19) *0, disabled.
[    0.669057] ACPI: PCI Interrupt Link [LN5A] (IRQs 16 17 18 19) *0, disabled.
[    0.669379] ACPI: PCI Interrupt Link [LN5B] (IRQs 16 17 18 19) *0, disabled.
[    0.669702] ACPI: PCI Interrupt Link [LN5C] (IRQs 16 17 18 19) *0, disabled.
[    0.670021] ACPI: PCI Interrupt Link [LN5D] (IRQs 16 17 18 19) *0, disabled.
[    0.670343] ACPI: PCI Interrupt Link [LN6A] (IRQs 16 17 18 19) *0, disabled.
[    0.670666] ACPI: PCI Interrupt Link [LN6B] (IRQs 16 17 18 19) *0, disabled.
[    0.670993] ACPI: PCI Interrupt Link [LN6C] (IRQs 16 17 18 19) *0, disabled.
[    0.671311] ACPI: PCI Interrupt Link [LN6D] (IRQs 16 17 18 19) *0, disabled.
[    0.671632] ACPI: PCI Interrupt Link [LN7A] (IRQs 16 17 18 19) *0, disabled.
[    0.671953] ACPI: PCI Interrupt Link [LN7B] (IRQs 16 17 18 19) *0, disabled.
[    0.672272] ACPI: PCI Interrupt Link [LN7C] (IRQs 16 17 18 19) *0, disabled.
[    0.672591] ACPI: PCI Interrupt Link [LN7D] (IRQs 16 17 18 19) *0, disabled.
[    0.672918] ACPI: PCI Interrupt Link [LUB0] (IRQs 20 21 22 23) *10
[    0.673245] ACPI: PCI Interrupt Link [LUB2] (IRQs 20 21 22 23) *15
[    0.673571] ACPI: PCI Interrupt Link [LMAC] (IRQs 20 21 22 23) *10
[    0.673898] ACPI: PCI Interrupt Link [LAZA] (IRQs 20 21 22 23) *15
[    0.674225] ACPI: PCI Interrupt Link [SGRU] (IRQs 20 21 22 23) *15
[    0.674550] ACPI: PCI Interrupt Link [LSMB] (IRQs 20 21 22 23) *11
[    0.674876] ACPI: PCI Interrupt Link [LPMU] (IRQs 20 21 22 23) *10
[    0.675205] ACPI: PCI Interrupt Link [LSA0] (IRQs 20 21 22 23) *5
[    0.675587] ACPI: PCI Interrupt Link [LATA] (IRQs 20 21 22 23) *0, disabled.
[    0.675914] ACPI: PCI Interrupt Link [UB11] (IRQs 20 21 22 23) *11
[    0.676256] ACPI: PCI Interrupt Link [UB12] (IRQs 20 21 22 23) *10
[    0.676401] ACPI Warning (tbutils-0217): Incorrect checksum in table [OEMB] - 1B, should be 0E [20080926]
[    0.676554] ACPI: WMI: Mapper loaded
[    0.676590] SCSI subsystem initialized
[    0.676590] libata version 3.00 loaded.
[    0.676590] usbcore: registered new interface driver usbfs
[    0.676590] usbcore: registered new interface driver hub
[    0.676590] usbcore: registered new device driver usb
[    0.676590] PCI: Using ACPI for IRQ routing
[    0.680008] Bluetooth: Core ver 2.13
[    0.680018] NET: Registered protocol family 31
[    0.680018] Bluetooth: HCI device and connection manager initialized
[    0.680018] Bluetooth: HCI socket layer initialized
[    0.680018] NET: Registered protocol family 8
[    0.680020] NET: Registered protocol family 20
[    0.680028] NetLabel: Initializing
[    0.680029] NetLabel:  domain hash size = 128
[    0.680030] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.680040] NetLabel:  unlabeled traffic allowed by default
[    0.680056] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 31
[    0.680060] hpet0: 3 comparators, 32-bit 25.000000 MHz counter
[    0.696046] AppArmor: AppArmor Filesystem Enabled
[    0.700016] Switched to high resolution mode on CPU 1
[    0.700019] Switched to high resolution mode on CPU 0
[    0.700023] Switched to high resolution mode on CPU 2
[    0.700028] Switched to high resolution mode on CPU 3
[    0.700403] pnp: PnP ACPI init
[    0.700412] ACPI: bus type pnp registered
[    0.704490] pnp 00:06: io resource (0x900-0x97f) overlaps 0000:00:01.0 BAR 0 (0x900-0x9ff), disabling
[    0.704493] pnp 00:06: io resource (0x980-0x9ff) overlaps 0000:00:01.0 BAR 0 (0x900-0x9ff), disabling
[    0.711961] pnp: PnP ACPI: found 15 devices
[    0.711962] ACPI: ACPI bus type pnp unregistered
[    0.711965] PnPBIOS: Disabled by ACPI PNP
[    0.711974] system 00:06: ioport range 0x4d0-0x4d1 has been reserved
[    0.711977] system 00:06: ioport range 0x800-0x80f has been reserved
[    0.711979] system 00:06: ioport range 0x500-0x57f has been reserved
[    0.711981] system 00:06: ioport range 0x580-0x5ff has been reserved
[    0.711986] system 00:06: ioport range 0x800-0x87f could not be reserved
[    0.711988] system 00:06: ioport range 0x880-0x8ff has been reserved
[    0.711990] system 00:06: ioport range 0xd00-0xd7f has been reserved
[    0.711992] system 00:06: ioport range 0xd80-0xdff has been reserved
[    0.711995] system 00:06: iomem range 0xfed04000-0xfed04fff has been reserved
[    0.711997] system 00:06: iomem range 0xfee01000-0xfeefffff has been reserved
[    0.712006] system 00:09: iomem range 0xfec00000-0xfec00fff has been reserved
[    0.712008] system 00:09: iomem range 0xfee00000-0xfee00fff has been reserved
[    0.712010] system 00:09: iomem range 0x78000000-0x7fffffff has been reserved
[    0.712015] system 00:0b: ioport range 0x230-0x23f has been reserved
[    0.712017] system 00:0b: ioport range 0x290-0x29f has been reserved
[    0.712019] system 00:0b: ioport range 0xa00-0xa0f has been reserved
[    0.712021] system 00:0b: ioport range 0xa10-0xa1f has been reserved
[    0.712025] system 00:0d: iomem range 0xe0000000-0xefffffff has been reserved
[    0.712030] system 00:0e: iomem range 0x0-0x9ffff could not be reserved
[    0.712032] system 00:0e: iomem range 0xc0000-0xcffff could not be reserved
[    0.712034] system 00:0e: iomem range 0xe0000-0xfffff could not be reserved
[    0.712036] system 00:0e: iomem range 0x100000-0x7fffffff could not be reserved
[    0.712039] system 00:0e: iomem range 0xfed45000-0xffffffff could not be reserved
[    0.746715] pci 0000:00:08.0: PCI bridge, secondary bus 0000:01
[    0.746717] pci 0000:00:08.0:   IO window: disabled
[    0.746720] pci 0000:00:08.0:   MEM window: disabled
[    0.746723] pci 0000:00:08.0:   PREFETCH window: disabled
[    0.746727] pci 0000:00:0b.0: PCI bridge, secondary bus 0000:02
[    0.746729] pci 0000:00:0b.0:   IO window: 0xe000-0xefff
[    0.746732] pci 0000:00:0b.0:   MEM window: 0xfd000000-0xfebfffff
[    0.746735] pci 0000:00:0b.0:   PREFETCH window: 0x000000f0000000-0x000000fbffffff
[    0.746739] pci 0000:00:10.0: PCI bridge, secondary bus 0000:03
[    0.746740] pci 0000:00:10.0:   IO window: disabled
[    0.746749] pci 0000:00:10.0:   MEM window: disabled
[    0.746756] pci 0000:00:10.0:   PREFETCH window: disabled
[    0.746768] pci 0000:00:12.0: PCI bridge, secondary bus 0000:04
[    0.746770] pci 0000:00:12.0:   IO window: disabled
[    0.746779] pci 0000:00:12.0:   MEM window: disabled
[    0.746786] pci 0000:00:12.0:   PREFETCH window: disabled
[    0.746802] pci 0000:00:08.0: setting latency timer to 64
[    0.746807] pci 0000:00:0b.0: setting latency timer to 64
[    0.747246] ACPI: PCI Interrupt Link [LN0A] enabled at IRQ 19
[    0.747259] pci 0000:00:10.0: PCI INT A -> Link[LN0A] -> GSI 19 (level, low) -> IRQ 19
[    0.747267] pci 0000:00:10.0: setting latency timer to 64
[    0.747705] ACPI: PCI Interrupt Link [LN2A] enabled at IRQ 18
[    0.747716] pci 0000:00:12.0: PCI INT A -> Link[LN2A] -> GSI 18 (level, low) -> IRQ 18
[    0.747724] pci 0000:00:12.0: setting latency timer to 64
[    0.747729] bus: 00 index 0 io port: [0x00-0xffff]
[    0.747731] bus: 00 index 1 mmio: [0x000000-0xffffffff]
[    0.747733] bus: 01 index 0 mmio: [0x0-0x0]
[    0.747734] bus: 01 index 1 mmio: [0x0-0x0]
[    0.747736] bus: 01 index 2 mmio: [0x0-0x0]
[    0.747738] bus: 01 index 3 io port: [0x00-0xffff]
[    0.747739] bus: 01 index 4 mmio: [0x000000-0xffffffff]
[    0.747741] bus: 02 index 0 io port: [0xe000-0xefff]
[    0.747743] bus: 02 index 1 mmio: [0xfd000000-0xfebfffff]
[    0.747745] bus: 02 index 2 mmio: [0xf0000000-0xfbffffff]
[    0.747746] bus: 02 index 3 mmio: [0x0-0x0]
[    0.747748] bus: 03 index 0 mmio: [0x0-0x0]
[    0.747749] bus: 03 index 1 mmio: [0x0-0x0]
[    0.747751] bus: 03 index 2 mmio: [0x0-0x0]
[    0.747752] bus: 03 index 3 mmio: [0x0-0x0]
[    0.747754] bus: 04 index 0 mmio: [0x0-0x0]
[    0.747755] bus: 04 index 1 mmio: [0x0-0x0]
[    0.747756] bus: 04 index 2 mmio: [0x0-0x0]
[    0.747758] bus: 04 index 3 mmio: [0x0-0x0]
[    0.747766] NET: Registered protocol family 2
[    0.757616] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.757837] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.758233] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.758454] TCP: Hash tables configured (established 131072 bind 65536)
[    0.758456] TCP reno registered
[    0.761448] NET: Registered protocol family 1
[    0.761556] checking if image is initramfs... it is
[    1.249026] Freeing initrd memory: 7369k freed
[    1.249411] cpufreq: No nForce2 chipset.
[    1.249518] audit: initializing netlink socket (disabled)
[    1.249533] type=2000 audit(1237890965.249:1): initialized
[    1.256014] highmem bounce pool size: 64 pages
[    1.256018] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    1.257266] VFS: Disk quotas dquot_6.5.1
[    1.257316] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    1.257854] fuse init (API version 7.10)
[    1.257927] msgmni has been set to 1701
[    1.258106] alg: No test for stdrng (krng)
[    1.258118] io scheduler noop registered
[    1.258120] io scheduler anticipatory registered
[    1.258121] io scheduler deadline registered
[    1.258136] io scheduler cfq registered (default)
[    1.305325] pci 0000:00:07.0: Enabling HT MSI Mapping
[    1.305354] pci 0000:00:08.0: Enabling HT MSI Mapping
[    1.305384] pci 0000:00:09.0: Enabling HT MSI Mapping
[    1.305415] pci 0000:00:0a.0: Enabling HT MSI Mapping
[    1.305443] pci 0000:00:0b.0: Enabling HT MSI Mapping
[    1.305508] pci 0000:00:10.0: Enabling HT MSI Mapping
[    1.305575] pci 0000:00:12.0: Enabling HT MSI Mapping
[    1.305619] pci 0000:02:00.0: Boot video device
[    1.320216] pcieport-driver 0000:00:10.0: setting latency timer to 64
[    1.320389] pcieport-driver 0000:00:10.0: found MSI capability
[    1.320474] pcieport-driver 0000:00:10.0: irq 2303 for MSI/MSI-X
[    1.320513] pci_express 0000:00:10.0:pcie00: allocate port service
[    1.320692] pcieport-driver 0000:00:12.0: setting latency timer to 64
[    1.320863] pcieport-driver 0000:00:12.0: found MSI capability
[    1.320949] pcieport-driver 0000:00:12.0: irq 2302 for MSI/MSI-X
[    1.320982] pci_express 0000:00:12.0:pcie00: allocate port service
[    1.321135] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    1.321142] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    1.321277] input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input0
[    1.321279] ACPI: Power Button (FF) [PWRF]
[    1.321318] input: Power Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1
[    1.321320] ACPI: Power Button (CM) [PWRB]
[    1.321633] processor ACPI_CPU:00: registered as cooling_device0
[    1.321660] processor ACPI_CPU:01: registered as cooling_device1
[    1.321689] processor ACPI_CPU:02: registered as cooling_device2
[    1.321718] processor ACPI_CPU:03: registered as cooling_device3
[    1.330149] isapnp: Scanning for PnP cards...
[    1.683795] isapnp: No Plug & Play device found
[    1.689791] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
[    1.689879] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.690219] 00:0c: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.690814] brd: module loaded
[    1.691073] loop: module loaded
[    1.691124] Fixed MDIO Bus: probed
[    1.691129] PPP generic driver version 2.4.2
[    1.691174] input: Macintosh mouse button emulation as /devices/virtual/input/input2
[    1.691195] Driver 'sd' needs updating - please use bus_type methods
[    1.691202] Driver 'sr' needs updating - please use bus_type methods
[    1.691237] ahci 0000:00:09.0: version 3.0
[    1.691692] ACPI: PCI Interrupt Link [LSA0] enabled at IRQ 23
[    1.691702] ahci 0000:00:09.0: PCI INT A -> Link[LSA0] -> GSI 23 (level, low) -> IRQ 23
[    1.691736] ahci 0000:00:09.0: irq 2301 for MSI/MSI-X
[    1.691807] ahci 0000:00:09.0: AHCI 0001.0200 32 slots 6 ports 3 Gbps 0x3f impl IDE mode
[    1.691809] ahci 0000:00:09.0: flags: 64bit ncq sntf led clo pmp pio 
[    1.691812] ahci 0000:00:09.0: setting latency timer to 64
[    1.692254] scsi0 : ahci
[    1.692334] scsi1 : ahci
[    1.692388] scsi2 : ahci
[    1.692439] scsi3 : ahci
[    1.692498] scsi4 : ahci
[    1.692554] scsi5 : ahci
[    1.692637] ata1: SATA max UDMA/133 abar m8192@0xfcf76000 port 0xfcf76100 irq 2301
[    1.692640] ata2: SATA max UDMA/133 abar m8192@0xfcf76000 port 0xfcf76180 irq 2301
[    1.692642] ata3: SATA max UDMA/133 abar m8192@0xfcf76000 port 0xfcf76200 irq 2301
[    1.692644] ata4: SATA max UDMA/133 abar m8192@0xfcf76000 port 0xfcf76280 irq 2301
[    1.692646] ata5: SATA max UDMA/133 abar m8192@0xfcf76000 port 0xfcf76300 irq 2301
[    1.692648] ata6: SATA max UDMA/133 abar m8192@0xfcf76000 port 0xfcf76380 irq 2301
[    2.176013] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    2.177838] ata1.00: ATA-8: ST3500320AS, SD1A, max UDMA/133
[    2.177840] ata1.00: 976773168 sectors, multi 16: LBA48 NCQ (depth 31/32)
[    2.180064] ata1.00: configured for UDMA/133
[    2.500376] ata2: SATA link down (SStatus 0 SControl 300)
[    2.820248] ata3: SATA link down (SStatus 0 SControl 300)
[    3.140120] ata4: SATA link down (SStatus 0 SControl 300)
[    3.460017] ata5: SATA link down (SStatus 0 SControl 300)
[    3.780237] ata6: SATA link down (SStatus 0 SControl 300)
[    3.780323] scsi 0:0:0:0: Direct-Access     ATA      ST3500320AS      SD1A PQ: 0 ANSI: 5
[    3.780391] sd 0:0:0:0: [sda] 976773168 512-byte hardware sectors: (500 GB/465 GiB)
[    3.780403] sd 0:0:0:0: [sda] Write Protect is off
[    3.780405] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    3.780423] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    3.780467] sd 0:0:0:0: [sda] 976773168 512-byte hardware sectors: (500 GB/465 GiB)
[    3.780480] sd 0:0:0:0: [sda] Write Protect is off
[    3.780482] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    3.780502] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    3.780516]  sda: sda1 sda2 < sda5 sda6 sda7 >
[    3.839573] sd 0:0:0:0: [sda] Attached SCSI disk
[    3.839604] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    3.839773] pata_amd 0000:00:06.0: version 0.3.10
[    3.839800] pata_amd 0000:00:06.0: setting latency timer to 64
[    3.839875] scsi6 : pata_amd
[    3.839936] scsi7 : pata_amd
[    3.841119] ata7: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xffa0 irq 14
[    3.841125] ata8: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xffa8 irq 15
[    4.004668] ata7.00: ATAPI: TSSTcorp CDDVDW SH-S202J, SB01, max UDMA/66
[    4.004689] ata7: nv_mode_filter: 0x1f39f&0x1f01f->0x1f01f, BIOS=0x1f000 (0xc5000000) ACPI=0x1f01f (30:900:0x11)
[    4.020998] ata7.00: configured for UDMA/66
[    4.021470] ata8: port disabled. ignoring.
[    4.022452] scsi 6:0:0:0: CD-ROM            TSSTcorp CDDVDW SH-S202J  SB01 PQ: 0 ANSI: 5
[    4.024337] CE: hpet increasing min_delta_ns to 15000 nsec
[    4.027223] sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
[    4.027226] Uniform CD-ROM driver Revision: 3.20
[    4.027299] sr 6:0:0:0: Attached scsi CD-ROM sr0
[    4.027331] sr 6:0:0:0: Attached scsi generic sg1 type 5
[    4.027689] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    4.028154] ACPI: PCI Interrupt Link [LUB2] enabled at IRQ 22
[    4.028162] ehci_hcd 0000:00:02.1: PCI INT B -> Link[LUB2] -> GSI 22 (level, low) -> IRQ 22
[    4.028173] ehci_hcd 0000:00:02.1: setting latency timer to 64
[    4.028175] ehci_hcd 0000:00:02.1: EHCI Host Controller
[    4.028216] ehci_hcd 0000:00:02.1: new USB bus registered, assigned bus number 1
[    4.028238] ehci_hcd 0000:00:02.1: debug port 1
[    4.028241] ehci_hcd 0000:00:02.1: cache line size of 64 is not supported
[    4.028257] ehci_hcd 0000:00:02.1: irq 22, io mem 0xfcf7fc00
[    4.036156] ehci_hcd 0000:00:02.1: USB 2.0 started, EHCI 1.00
[    4.036211] usb usb1: configuration #1 chosen from 1 choice
[    4.036231] hub 1-0:1.0: USB hub found
[    4.036238] hub 1-0:1.0: 6 ports detected
[    4.036752] ACPI: PCI Interrupt Link [UB12] enabled at IRQ 21
[    4.036759] ehci_hcd 0000:00:04.1: PCI INT B -> Link[UB12] -> GSI 21 (level, low) -> IRQ 21
[    4.036767] ehci_hcd 0000:00:04.1: setting latency timer to 64
[    4.036769] ehci_hcd 0000:00:04.1: EHCI Host Controller
[    4.036797] ehci_hcd 0000:00:04.1: new USB bus registered, assigned bus number 2
[    4.036816] ehci_hcd 0000:00:04.1: debug port 1
[    4.036819] ehci_hcd 0000:00:04.1: cache line size of 64 is not supported
[    4.036834] ehci_hcd 0000:00:04.1: irq 21, io mem 0xfcf7f800
[    4.048283] ehci_hcd 0000:00:04.1: USB 2.0 started, EHCI 1.00
[    4.048340] usb usb2: configuration #1 chosen from 1 choice
[    4.048360] hub 2-0:1.0: USB hub found
[    4.048369] hub 2-0:1.0: 6 ports detected
[    4.048453] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    4.048899] ACPI: PCI Interrupt Link [LUB0] enabled at IRQ 20
[    4.048906] ohci_hcd 0000:00:02.0: PCI INT A -> Link[LUB0] -> GSI 20 (level, low) -> IRQ 20
[    4.048914] ohci_hcd 0000:00:02.0: setting latency timer to 64
[    4.048916] ohci_hcd 0000:00:02.0: OHCI Host Controller
[    4.048945] ohci_hcd 0000:00:02.0: new USB bus registered, assigned bus number 3
[    4.048964] ohci_hcd 0000:00:02.0: irq 20, io mem 0xfcf7e000
[    4.106290] usb usb3: configuration #1 chosen from 1 choice
[    4.106308] hub 3-0:1.0: USB hub found
[    4.106320] hub 3-0:1.0: 6 ports detected
[    4.106826] ACPI: PCI Interrupt Link [UB11] enabled at IRQ 23
[    4.106828] ohci_hcd 0000:00:04.0: PCI INT A -> Link[UB11] -> GSI 23 (level, low) -> IRQ 23
[    4.106836] ohci_hcd 0000:00:04.0: setting latency timer to 64
[    4.106838] ohci_hcd 0000:00:04.0: OHCI Host Controller
[    4.106871] ohci_hcd 0000:00:04.0: new USB bus registered, assigned bus number 4
[    4.106890] ohci_hcd 0000:00:04.0: irq 23, io mem 0xfcf7d000
[    4.162180] usb usb4: configuration #1 chosen from 1 choice
[    4.162202] hub 4-0:1.0: USB hub found
[    4.162208] hub 4-0:1.0: 6 ports detected
[    4.162281] uhci_hcd: USB Universal Host Controller Interface driver
[    4.162333] usbcore: registered new interface driver libusual
[    4.162357] usbcore: registered new interface driver usbserial
[    4.162364] USB Serial support registered for generic
[    4.162374] usbcore: registered new interface driver usbserial_generic
[    4.162378] usbserial: USB Serial Driver core
[    4.162415] PNP: PS/2 Controller [PNP0303:PS2K] at 0x60,0x64 irq 1
[    4.162417] PNP: PS/2 appears to have AUX port disabled, if this is incorrect please boot with i8042.nopnp
[    4.162495] serio: i8042 KBD port at 0x60,0x64 irq 1
[    4.164371] mice: PS/2 mouse device common for all mice
[    4.169867] rtc_cmos 00:08: RTC can wake from S4
[    4.169892] rtc_cmos 00:08: rtc core: registered rtc_cmos as rtc0
[    4.169949] rtc0: alarms up to one year, y3k, 114 bytes nvram, hpet irqs
[    4.169999] device-mapper: uevent: version 1.0.3
[    4.170079] device-mapper: ioctl: 4.14.0-ioctl (2008-04-23) initialised: [email]dm-devel@redhat.com[/email]
[    4.170223] device-mapper: multipath: version 1.0.5 loaded
[    4.170225] device-mapper: multipath round-robin: version 1.0.0 loaded
[    4.170297] EISA: Probing bus 0 at eisa.0
[    4.170320] EISA: Detected 0 cards.
[    4.170430] cpuidle: using governor ladder
[    4.170432] cpuidle: using governor menu
[    4.170861] TCP cubic registered
[    4.170952] NET: Registered protocol family 10
[    4.171321] lo: Disabled Privacy Extensions
[    4.171595] NET: Registered protocol family 17
[    4.171609] Bluetooth: L2CAP ver 2.11
[    4.171610] Bluetooth: L2CAP socket layer initialized
[    4.171612] Bluetooth: SCO (Voice Link) ver 0.6
[    4.171614] Bluetooth: SCO socket layer initialized
[    4.171644] Bluetooth: RFCOMM socket layer initialized
[    4.171648] Bluetooth: RFCOMM TTY layer initialized
[    4.171650] Bluetooth: RFCOMM ver 1.10
[    4.171707] powernow-k8: Found 1 AMD Phenom(tm) 9650 Quad-Core Processor processors (4 cpu cores) (version 2.20.00)
[    4.171744] powernow-k8:    0 : pstate 0 (2300 MHz)
[    4.171747] powernow-k8:    1 : pstate 1 (1200 MHz)
[    4.171952] Using IPI No-Shortcut mode
[    4.172017] registered taskstats version 1
[    4.172132]   Magic number: 1:425:629
[    4.172167] pci_link PNP0C0F:2d: hash matches
[    4.172258] rtc_cmos 00:08: setting system clock to 2009-03-24 10:36:08 UTC (1237890968)
[    4.172260] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    4.172262] EDD information not available.
[    4.172526] Freeing unused kernel memory: 532k freed
[    4.172651] Write protecting the kernel text: 4128k
[    4.172699] Write protecting the kernel read-only data: 1532k
[    4.192655] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3
[    4.331682] Floppy drive(s): fd0 is 1.44M
[    4.348927] FDC 0 is a post-1991 82077
[    4.357628] forcedeth: Reverse Engineered nForce ethernet driver. Version 0.61.
[    4.358127] ACPI: PCI Interrupt Link [LMAC] enabled at IRQ 22
[    4.358132] forcedeth 0000:00:0a.0: PCI INT A -> Link[LMAC] -> GSI 22 (level, low) -> IRQ 22
[    4.358136] forcedeth 0000:00:0a.0: setting latency timer to 64
[    4.421919] forcedeth 0000:00:0a.0: ifname eth0, PHY OUI 0x732 @ 3, addr 00:22:15:b6:7e:99
[    4.421924] forcedeth 0000:00:0a.0: highdma csum pwrctl mgmt timirq gbit lnktim msi desc-v3
[    4.600522] usb 3-4: new low speed USB device using ohci_hcd and address 2
[    4.709185] PM: Starting manual resume from disk
[    4.709188] PM: Resume from partition 8:7
[    4.709189] PM: Checking hibernation image.
[    4.709598] PM: Resume from disk failed.
[    4.741264] kjournald starting.  Commit interval 5 seconds
[    4.741273] EXT3-fs: mounted filesystem with ordered data mode.
[    4.810167] usb 3-4: configuration #1 chosen from 1 choice
[    5.284366] usb 4-2: new full speed USB device using ohci_hcd and address 2
[    5.490743] usb 4-2: configuration #1 chosen from 1 choice
[    5.796875] usb 4-4: new low speed USB device using ohci_hcd and address 3
[    6.015554] usb 4-4: configuration #1 chosen from 1 choice
[    9.048352] udev: starting version 140
[    9.307805] parport_pc 00:05: reported by Plug and Play ACPI
[    9.307853] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
[    9.363499] usbcore: registered new interface driver hiddev
[    9.372637] input: USB Gamepad  as /devices/pci0000:00/0000:00:02.0/usb3/3-4/3-4:1.0/input/input4
[    9.377835] generic-usb 0003:0810:0007.0001: input,hidraw0: USB HID v1.10 Joystick [USB Gamepad ] on usb-0000:00:02.0-4/input0
[    9.384520] input: Genius SS 600 Laser PC as /devices/pci0000:00/0000:00:04.0/usb4/4-4/4-4:1.0/input/input5
[    9.389818] generic-usb 0003:0458:007E.0002: input,hidraw1: USB HID v1.00 Keyboard [Genius SS 600 Laser PC] on usb-0000:00:04.0-4/input0
[    9.399491] input: Genius SS 600 Laser PC as /devices/pci0000:00/0000:00:04.0/usb4/4-4/4-4:1.1/input/input6
[    9.406134] generic-usb 0003:0458:007E.0003: input,hidraw2: USB HID v1.00 Mouse [Genius SS 600 Laser PC] on usb-0000:00:04.0-4/input1
[    9.406150] usbcore: registered new interface driver usbhid
[    9.406167] usbhid: v2.6:USB HID core driver
[    9.478172] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[    9.553015] ppdev: user-space parallel port driver
[    9.558180] input: PC Speaker as /devices/platform/pcspkr/input/input7
[    9.744844] HDA Intel 0000:00:07.0: power state changed by ACPI to D0
[    9.745356] ACPI: PCI Interrupt Link [LAZA] enabled at IRQ 21
[    9.745361] HDA Intel 0000:00:07.0: PCI INT A -> Link[LAZA] -> GSI 21 (level, low) -> IRQ 21
[    9.745515] HDA Intel 0000:00:07.0: setting latency timer to 64
[    9.790485] usbcore: registered new interface driver snd-usb-audio
[   10.628353] lp0: using parport0 (interrupt-driven).
[   10.700045] Adding 2923788k swap on /dev/sda7.  Priority:-1 extents:1 across:2923788k
[   11.236879] EXT3 FS on sda5, internal journal
[   12.292470] type=1505 audit(1237901776.616:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=2062
[   12.339281] type=1505 audit(1237901776.665:3): operation="profile_load" name="/sbin/dhclient-script" name2="default" pid=2066
[   12.339366] type=1505 audit(1237901776.665:4): operation="profile_load" name="/sbin/dhclient3" name2="default" pid=2066
[   12.339402] type=1505 audit(1237901776.665:5): operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" name2="default" pid=2066
[   12.339474] type=1505 audit(1237901776.665:6): operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" name2="default" pid=2066
[   12.460191] type=1505 audit(1237901776.787:7): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=2071
[   12.460345] type=1505 audit(1237901776.787:8): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=2071
[   12.487111] type=1505 audit(1237901776.811:9): operation="profile_load" name="/usr/sbin/tcpdump" name2="default" pid=2075
[   14.899941] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   14.899944] Bluetooth: BNEP filters: protocol multicast
[   14.907837] Bridge firewalling registered
[   20.672533] forcedeth 0000:00:0a.0: irq 2300 for MSI/MSI-X
[   31.060235] eth0: no IPv6 routers present
[   39.104015] timeout: still 8 active urbs..
[ 1264.064351] hda-intel: IRQ timing workaround is activated for card #0. Suggest a bigger bdl_pos_adj.
santi698@santi698-desktop:~$ 
santi698@santi698-desktop:~$

---

### Post by Hei Ku on 2009-03-24
tenes algun problema de sonido? El ultimo error parece estar mas relacionado a sonido que al trackpad.

Despues de reiniciar, hace un "cat /proc/interrupts" y postea el resultado.
Puede ser que haya dispositivos que estan usando la misma IRQ.

---

### Post by santi698 on 2009-03-24
no, no tengo ningun problema con el sonido, q raro

---

### Post by santi698 on 2009-03-24
el resultado del comando es este: 

santi698@santi698-desktop:~$ cat /proc/interrupts
           CPU0       CPU1       CPU2       CPU3       
  0:        151         98       1140      15080   IO-APIC-edge      timer
  1:          1          7        174        796   IO-APIC-edge      i8042
  4:          0          0          0          4   IO-APIC-edge    
  6:          0          0          0          5   IO-APIC-edge      floppy
  7:          1          0          0          0   IO-APIC-edge      parport0
  8:          0          0          0          1   IO-APIC-edge      rtc0
  9:          0          0          0          0   IO-APIC-fasteoi   acpi
 14:          0          7        104        692   IO-APIC-edge      pata_amd
 15:          0          0          0          0   IO-APIC-edge      pata_amd
 20:          0          0          2         22   IO-APIC-fasteoi   ohci_hcd:usb3
 21:          5         39        409       1952   IO-APIC-fasteoi   ehci_hcd:usb2, HDA Intel
 22:          0          0          0          3   IO-APIC-fasteoi   ehci_hcd:usb1
 23:          1        177       3233      69827   IO-APIC-fasteoi   ohci_hcd:usb4
2300:          1         67       1174       6421   PCI-MSI-edge      eth0
2301:          3         98       1255       8347   PCI-MSI-edge      ahci
NMI:          0          0          0          0   Non-maskable interrupts
LOC:       7603       4526       6679       4109   Local timer interrupts
RES:       4507       3519       5352       4641   Rescheduling interrupts
CAL:        102        112         95         43   Function call interrupts
TLB:        687        665        780        536   TLB shootdowns
SPU:          0          0          0          0   Spurious interrupts
ERR:          1
MIS:          0

---

