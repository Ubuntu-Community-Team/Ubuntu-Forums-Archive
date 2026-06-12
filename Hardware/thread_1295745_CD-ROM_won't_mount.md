---
title: "CD-ROM won't mount"
date: 2009-10-19
forum: Hardware
---

### Post by manji_kun on 2009-10-19
My previous CD rom drive went out recently, so i got myself a new one, after the installation i realized that the drive wont mount, Ubuntu reads the drive and sees it, but won't load any CD's of any kind, saying 

"Unable to mount location."

any idea's what i can do to make the computer read CD's?

---

### Post by superdav42 on 2009-10-19
what is the output of ```
dmesg
```?
What happens when you try to manually mount it using the mount command.

---

### Post by manji_kun on 2009-10-19
> 
[    0.583822] pci 0000:00:10.0: bridge 32bit mmio: [0xfaa00000-0xfaafffff]
[    0.583834] bus 00 -> node 0
[    0.583846] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.584215] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCE0._PRT]
[    0.584349] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCE1._PRT]
[    0.584483] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCE2._PRT]
[    0.584646] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P1._PRT]
[    0.597494] ACPI: PCI Interrupt Link [LNKA] (IRQs 16 17 18 19) *0, disabled.
[    0.597765] ACPI: PCI Interrupt Link [LNKB] (IRQs 16 17 18 19) *0, disabled.
[    0.598035] ACPI: PCI Interrupt Link [LNKC] (IRQs 16 17 18 19) *9
[    0.598304] ACPI: PCI Interrupt Link [LNKD] (IRQs 16 17 18 19) *9
[    0.598574] ACPI: PCI Interrupt Link [LNEA] (IRQs 16 17 18 19) *0, disabled.
[    0.598843] ACPI: PCI Interrupt Link [LNEB] (IRQs 16 17 18 19) *0, disabled.
[    0.599114] ACPI: PCI Interrupt Link [LNEC] (IRQs 16 17 18 19) *11
[    0.599390] ACPI: PCI Interrupt Link [LNED] (IRQs 16 17 18 19) *0, disabled.
[    0.599665] ACPI: PCI Interrupt Link [LUB0] (IRQs 20 21 22 23) *9
[    0.599935] ACPI: PCI Interrupt Link [LUB2] (IRQs 20 21 22 23) *5
[    0.600215] ACPI: PCI Interrupt Link [LMAC] (IRQs 20 21 22 23) *9
[    0.600489] ACPI: PCI Interrupt Link [LAZA] (IRQs 20 21 22 23) *9
[    0.600760] ACPI: PCI Interrupt Link [LACI] (IRQs 20 21 22 23) *0, disabled.
[    0.601034] ACPI: PCI Interrupt Link [LMC9] (IRQs 20 21 22 23) *0, disabled.
[    0.601306] ACPI: PCI Interrupt Link [LSMB] (IRQs 20 21 22 23) *9
[    0.601577] ACPI: PCI Interrupt Link [LPMU] (IRQs 20 21 22 23) *10
[    0.601853] ACPI: PCI Interrupt Link [LSA0] (IRQs 20 21 22 23) *9
[    0.602125] ACPI: PCI Interrupt Link [LSA1] (IRQs 20 21 22 23) *0, disabled.
[    0.602445] ACPI: PCI Interrupt Link [LATA] (IRQs 20 21 22 23) *0, disabled.
[    0.602594] ACPI Warning (tbutils-0217): Incorrect checksum in table [OEMB] - 65, should be 58 [20080926]
[    0.602618] ACPI: WMI: Mapper loaded
[    0.602832] SCSI subsystem initialized
[    0.602874] libata version 3.00 loaded.
[    0.602923] usbcore: registered new interface driver usbfs
[    0.602941] usbcore: registered new interface driver hub
[    0.602969] usbcore: registered new device driver usb
[    0.603081] PCI: Using ACPI for IRQ routing
[    0.603199] Bluetooth: Core ver 2.13
[    0.603199] NET: Registered protocol family 31
[    0.603199] Bluetooth: HCI device and connection manager initialized
[    0.603199] Bluetooth: HCI socket layer initialized
[    0.603199] NET: Registered protocol family 8
[    0.603199] NET: Registered protocol family 20
[    0.603199] NetLabel: Initializing
[    0.603199] NetLabel:  domain hash size = 128
[    0.603199] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.603199] NetLabel:  unlabeled traffic allowed by default
[    0.603199] AppArmor: AppArmor Filesystem Enabled
[    0.603199] pnp: PnP ACPI init
[    0.603199] ACPI: bus type pnp registered
[    0.610708] pnp: PnP ACPI: found 14 devices
[    0.610711] ACPI: ACPI bus type pnp unregistered
[    0.610715] PnPBIOS: Disabled by ACPI PNP
[    0.610728] system 00:07: ioport range 0x4d0-0x4d1 has been reserved
[    0.610732] system 00:07: ioport range 0x800-0x80f has been reserved
[    0.610735] system 00:07: ioport range 0x500-0x57f has been reserved
[    0.610738] system 00:07: ioport range 0x580-0x5ff has been reserved
[    0.610741] system 00:07: ioport range 0x800-0x87f could not be reserved
[    0.610745] system 00:07: ioport range 0x880-0x8ff has been reserved
[    0.610748] system 00:07: ioport range 0x900-0x97f has been reserved
[    0.610751] system 00:07: ioport range 0x980-0x9ff has been reserved
[    0.610754] system 00:07: ioport range 0x2000-0x207f has been reserved
[    0.610758] system 00:07: ioport range 0x2080-0x20ff has been reserved
[    0.610762] system 00:07: iomem range 0xfefe0000-0xfefe01ff has been reserved
[    0.610765] system 00:07: iomem range 0xfeb80000-0xfebbffff has been reserved
[    0.610769] system 00:07: iomem range 0xfee01000-0xfeefffff has been reserved
[    0.610775] system 00:08: iomem range 0xfec00000-0xfec00fff has been reserved
[    0.610779] system 00:08: iomem range 0xfee00000-0xfee00fff has been reserved
[    0.610785] system 00:0b: ioport range 0x290-0x297 has been reserved
[    0.610791] system 00:0c: iomem range 0xe0000000-0xefffffff has been reserved
[    0.610798] system 00:0d: iomem range 0x0-0x9ffff could not be reserved
[    0.610801] system 00:0d: iomem range 0xc0000-0xcffff could not be reserved
[    0.610804] system 00:0d: iomem range 0xe0000-0xfffff could not be reserved
[    0.610808] system 00:0d: iomem range 0x100000-0x5fffffff could not be reserved
[    0.610811] system 00:0d: iomem range 0xff780000-0xffffffff could not be reserved
[    0.645546] pci 0000:00:02.0: PCI bridge, secondary bus 0000:01
[    0.645549] pci 0000:00:02.0:   IO window: disabled
[    0.645553] pci 0000:00:02.0:   MEM window: disabled
[    0.645556] pci 0000:00:02.0:   PREFETCH window: disabled
[    0.645560] pci 0000:00:03.0: PCI bridge, secondary bus 0000:02
[    0.645562] pci 0000:00:03.0:   IO window: disabled
[    0.645565] pci 0000:00:03.0:   MEM window: disabled
[    0.645568] pci 0000:00:03.0:   PREFETCH window: disabled
[    0.645572] pci 0000:00:04.0: PCI bridge, secondary bus 0000:03
[    0.645575] pci 0000:00:04.0:   IO window: disabled
[    0.645578] pci 0000:00:04.0:   MEM window: disabled
[    0.645581] pci 0000:00:04.0:   PREFETCH window: disabled
[    0.645585] pci 0000:00:10.0: PCI bridge, secondary bus 0000:04
[    0.645588] pci 0000:00:10.0:   IO window: 0xc000-0xcfff
[    0.645593] pci 0000:00:10.0:   MEM window: 0xfaa00000-0xfaafffff
[    0.645596] pci 0000:00:10.0:   PREFETCH window: disabled
[    0.645607] pci 0000:00:02.0: setting latency timer to 64
[    0.645612] pci 0000:00:03.0: setting latency timer to 64
[    0.645618] pci 0000:00:04.0: setting latency timer to 64
[    0.645623] pci 0000:00:10.0: setting latency timer to 64
[    0.645627] bus: 00 index 0 io port: [0x00-0xffff]
[    0.645629] bus: 00 index 1 mmio: [0x000000-0xffffffff]
[    0.645632] bus: 01 index 0 mmio: [0x0-0x0]
[    0.645634] bus: 01 index 1 mmio: [0x0-0x0]
[    0.645636] bus: 01 index 2 mmio: [0x0-0x0]
[    0.645638] bus: 01 index 3 mmio: [0x0-0x0]
[    0.645641] bus: 02 index 0 mmio: [0x0-0x0]
[    0.645643] bus: 02 index 1 mmio: [0x0-0x0]
[    0.645645] bus: 02 index 2 mmio: [0x0-0x0]
[    0.645647] bus: 02 index 3 mmio: [0x0-0x0]
[    0.645649] bus: 03 index 0 mmio: [0x0-0x0]
[    0.645651] bus: 03 index 1 mmio: [0x0-0x0]
[    0.645653] bus: 03 index 2 mmio: [0x0-0x0]
[    0.645655] bus: 03 index 3 mmio: [0x0-0x0]
[    0.645658] bus: 04 index 0 io port: [0xc000-0xcfff]
[    0.645660] bus: 04 index 1 mmio: [0xfaa00000-0xfaafffff]
[    0.645663] bus: 04 index 2 mmio: [0x0-0x0]
[    0.645665] bus: 04 index 3 io port: [0x00-0xffff]
[    0.645667] bus: 04 index 4 mmio: [0x000000-0xffffffff]
[    0.645681] NET: Registered protocol family 2
[    0.645811] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.646135] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.647043] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.647527] TCP: Hash tables configured (established 131072 bind 65536)
[    0.647530] TCP reno registered
[    0.647634] NET: Registered protocol family 1
[    0.647779] checking if image is initramfs... it is
[    1.148090] Switched to high resolution mode on CPU 0
[    1.366121] Freeing initrd memory: 7384k freed
[    1.366224] cpufreq: No nForce2 chipset.
[    1.366359] audit: initializing netlink socket (disabled)
[    1.366376] type=2000 audit(1255994435.364:1): initialized
[    1.376214] highmem bounce pool size: 64 pages
[    1.376220] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    1.377619] VFS: Disk quotas dquot_6.5.1
[    1.377680] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    1.378340] fuse init (API version 7.10)
[    1.378429] msgmni has been set to 1713
[    1.378612] alg: No test for stdrng (krng)
[    1.378624] io scheduler noop registered
[    1.378626] io scheduler anticipatory registered
[    1.378628] io scheduler deadline registered
[    1.378645] io scheduler cfq registered (default)
[    1.378663] pci 0000:00:00.0: Enabling HT MSI Mapping
[    1.378704] pci 0000:00:02.0: Enabling HT MSI Mapping
[    1.378715] pci 0000:00:03.0: Enabling HT MSI Mapping
[    1.378726] pci 0000:00:04.0: Enabling HT MSI Mapping
[    1.378737] pci 0000:00:05.0: Boot video device
[    1.378759] pci 0000:00:09.0: Enabling HT MSI Mapping
[    1.816050] pci 0000:00:0e.0: Enabling HT MSI Mapping
[    1.816062] pci 0000:00:10.0: Enabling HT MSI Mapping
[    1.816075] pci 0000:00:10.1: Enabling HT MSI Mapping
[    1.823155] pcieport-driver 0000:00:02.0: setting latency timer to 64
[    1.823183] pcieport-driver 0000:00:02.0: found MSI capability
[    1.823202] pcieport-driver 0000:00:02.0: irq 2303 for MSI/MSI-X
[    1.823210] pci_express 0000:00:02.0:pcie00: allocate port service
[    1.823231] pci_express 0000:00:02.0:pcie03: allocate port service
[    1.823270] pcieport-driver 0000:00:03.0: setting latency timer to 64
[    1.823296] pcieport-driver 0000:00:03.0: found MSI capability
[    1.823310] pcieport-driver 0000:00:03.0: irq 2302 for MSI/MSI-X
[    1.823317] pci_express 0000:00:03.0:pcie00: allocate port service
[    1.823330] pci_express 0000:00:03.0:pcie03: allocate port service
[    1.823368] pcieport-driver 0000:00:04.0: setting latency timer to 64
[    1.823394] pcieport-driver 0000:00:04.0: found MSI capability
[    1.823408] pcieport-driver 0000:00:04.0: irq 2301 for MSI/MSI-X
[    1.823415] pci_express 0000:00:04.0:pcie00: allocate port service
[    1.823431] pci_express 0000:00:04.0:pcie03: allocate port service
[    1.823482] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    1.823491] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    1.823625] input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input0
[    1.823628] ACPI: Power Button (FF) [PWRF]
[    1.823678] input: Power Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1
[    1.823681] ACPI: Power Button (CM) [PWRB]
[    1.824156] processor ACPI_CPU:00: registered as cooling_device0
[    1.828534] isapnp: Scanning for PnP cards...
[    2.181975] isapnp: No Plug & Play device found
[    2.183146] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
[    2.183250] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    2.183603] 00:0a: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    2.184395] brd: module loaded
[    2.184739] loop: module loaded
[    2.184823] Fixed MDIO Bus: probed
[    2.184829] PPP generic driver version 2.4.2
[    2.184894] input: Macintosh mouse button emulation as /devices/virtual/input/input2
[    2.184928] Driver 'sd' needs updating - please use bus_type methods
[    2.184937] Driver 'sr' needs updating - please use bus_type methods
[    2.185141] sata_nv 0000:00:0e.0: version 3.5
[    2.185547] ACPI: PCI Interrupt Link [LSA0] enabled at IRQ 23
[    2.185560] sata_nv 0000:00:0e.0: PCI INT A -> Link[LSA0] -> GSI 23 (level, low) -> IRQ 23
[    2.185564] sata_nv 0000:00:0e.0: Using SWNCQ mode
[    2.185632] sata_nv 0000:00:0e.0: setting latency timer to 64
[    2.185833] scsi0 : sata_nv
[    2.185947] scsi1 : sata_nv
[    2.186126] ata1: SATA max UDMA/133 cmd 0xe800 ctl 0xe480 bmdma 0xe000 irq 23
[    2.186130] ata2: SATA max UDMA/133 cmd 0xe400 ctl 0xe080 bmdma 0xe008 irq 23
[    2.918493] ata1: SATA link down (SStatus 0 SControl 300)
[    3.650493] ata2: SATA link down (SStatus 0 SControl 300)
[    3.650593] pata_amd 0000:00:0d.0: version 0.3.10
[    3.650640] pata_amd 0000:00:0d.0: setting latency timer to 64
[    3.650723] scsi2 : pata_amd
[    3.650783] scsi3 : pata_amd
[    3.652451] ata3: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xffa0 irq 14
[    3.652454] ata4: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xffa8 irq 15
[    3.825085] ata3.00: ATA-4: WDC WD205BA, 16.13M16, max UDMA/66
[    3.825089] ata3.00: 40088160 sectors, multi 16: LBA 


nothing happens other than that.

or did i get the wrong idea? >.<

---

