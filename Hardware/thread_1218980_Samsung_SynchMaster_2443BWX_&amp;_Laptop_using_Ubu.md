---
title: "Samsung SynchMaster 2443BWX &amp; Laptop using Ubuntu"
date: 2009-07-21
forum: Hardware
---

### Post by Stoneface on 2009-07-21
I have a brand new 24" LCD Samsung SyncMaster 2433BWX that works under Windows XP out of the box. Under Windows the screen automatically recognizes the Windows system and takes the best resolution possible.
Under Ubuntu I added i810, but I get an error:
```

~$ i810switch lcd on
PCI id of i810 is not recognized.

```

So I need another way to get it to work. Is there anyone who has got this type of LCD to work under Ubuntu on a laptop, preferable and Acer Aspire?

---

### Post by Stoneface on 2009-07-21
No Solution yet. Here is my desmg log just after startup:

```

[    1.058073] pci 0000:00:0b.0: PCI bridge, secondary bus 0000:02
[    1.058075] pci 0000:00:0b.0:   IO window: 0x4000-0x4fff
[    1.058079] pci 0000:00:0b.0:   MEM window: 0xcc000000-0xceffffff
[    1.058082] pci 0000:00:0b.0:   PREFETCH window: 0x000000d0000000-0x000000dfffffff
[    1.058086] pci 0000:00:0c.0: PCI bridge, secondary bus 0000:03
[    1.058088] pci 0000:00:0c.0:   IO window: disabled
[    1.058091] pci 0000:00:0c.0:   MEM window: disabled
[    1.058093] pci 0000:00:0c.0:   PREFETCH window: disabled
[    1.058097] pci 0000:00:0e.0: PCI bridge, secondary bus 0000:07
[    1.058099] pci 0000:00:0e.0:   IO window: disabled
[    1.058102] pci 0000:00:0e.0:   MEM window: 0xf2000000-0xf20fffff
[    1.058105] pci 0000:00:0e.0:   PREFETCH window: disabled
[    1.058114] pci 0000:00:08.0: setting latency timer to 64
[    1.058119] pci 0000:00:0b.0: setting latency timer to 64
[    1.058124] pci 0000:00:0c.0: setting latency timer to 64
[    1.058129] pci 0000:00:0e.0: setting latency timer to 64
[    1.058132] bus: 00 index 0 io port: [0x00-0xffff]
[    1.058135] bus: 00 index 1 mmio: [0x000000-0xffffffff]
[    1.058137] bus: 01 index 0 mmio: [0x0-0x0]
[    1.058140] bus: 01 index 1 mmio: [0xf2100000-0xf21fffff]
[    1.058143] bus: 01 index 2 mmio: [0x0-0x0]
[    1.058144] bus: 01 index 3 io port: [0x00-0xffff]
[    1.058147] bus: 01 index 4 mmio: [0x000000-0xffffffff]
[    1.058149] bus: 02 index 0 io port: [0x4000-0x4fff]
[    1.058151] bus: 02 index 1 mmio: [0xcc000000-0xceffffff]
[    1.058154] bus: 02 index 2 mmio: [0xd0000000-0xdfffffff]
[    1.058156] bus: 02 index 3 mmio: [0x0-0x0]
[    1.058158] bus: 03 index 0 mmio: [0x0-0xfff]
[    1.058161] bus: 03 index 1 mmio: [0x0-0xfffff]
[    1.058163] bus: 03 index 2 mmio: [0x0-0xfffff]
[    1.058164] bus: 03 index 3 mmio: [0x0-0x0]
[    1.058167] bus: 07 index 0 mmio: [0x0-0x0]
[    1.058169] bus: 07 index 1 mmio: [0xf2000000-0xf20fffff]
[    1.058171] bus: 07 index 2 mmio: [0x0-0x0]
[    1.058173] bus: 07 index 3 mmio: [0x0-0x0]
[    1.058184] NET: Registered protocol family 2
[    1.072078] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    1.072394] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    1.073193] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    1.073625] TCP: Hash tables configured (established 131072 bind 65536)
[    1.073628] TCP reno registered
[    1.076120] NET: Registered protocol family 1
[    1.076255] checking if image is initramfs... it is
[    1.691740] Freeing initrd memory: 7371k freed
[    1.691776] Simple Boot Flag at 0x36 set to 0x1
[    1.691987] cpufreq: No nForce2 chipset.
[    1.692134] audit: initializing netlink socket (disabled)
[    1.692154] type=2000 audit(1248211621.692:1): initialized
[    1.700561] highmem bounce pool size: 64 pages
[    1.700567] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    1.701944] VFS: Disk quotas dquot_6.5.1
[    1.702004] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    1.702664] fuse init (API version 7.10)
[    1.702748] msgmni has been set to 1698
[    1.702958] alg: No test for stdrng (krng)
[    1.702971] io scheduler noop registered
[    1.702974] io scheduler anticipatory registered
[    1.702976] io scheduler deadline registered
[    1.702993] io scheduler cfq registered (default)
[    1.703026] pci 0000:00:00.0: Enabling HT MSI Mapping
[    1.703207] pci 0000:00:07.0: Enabling HT MSI Mapping
[    1.703222] pci 0000:00:08.0: Enabling HT MSI Mapping
[    1.703238] pci 0000:00:09.0: Enabling HT MSI Mapping
[    1.703255] pci 0000:00:0a.0: Enabling HT MSI Mapping
[    1.703271] pci 0000:00:0b.0: Enabling HT MSI Mapping
[    1.703286] pci 0000:00:0c.0: Enabling HT MSI Mapping
[    1.703302] pci 0000:00:0e.0: Enabling HT MSI Mapping
[    1.703331] pci 0000:02:00.0: Boot video device
[    1.706400] pcieport-driver 0000:00:0b.0: setting latency timer to 64
[    1.706426] pcieport-driver 0000:00:0b.0: found MSI capability
[    1.706443] pcieport-driver 0000:00:0b.0: irq 2303 for MSI/MSI-X
[    1.706450] pci_express 0000:00:0b.0:pcie00: allocate port service
[    1.706464] pci_express 0000:00:0b.0:pcie03: allocate port service
[    1.706503] pcieport-driver 0000:00:0c.0: setting latency timer to 64
[    1.706526] pcieport-driver 0000:00:0c.0: found MSI capability
[    1.706539] pcieport-driver 0000:00:0c.0: irq 2302 for MSI/MSI-X
[    1.706545] pci_express 0000:00:0c.0:pcie00: allocate port service
[    1.706559] pci_express 0000:00:0c.0:pcie03: allocate port service
[    1.706595] pcieport-driver 0000:00:0e.0: setting latency timer to 64
[    1.706618] pcieport-driver 0000:00:0e.0: found MSI capability
[    1.706631] pcieport-driver 0000:00:0e.0: irq 2301 for MSI/MSI-X
[    1.706638] pci_express 0000:00:0e.0:pcie00: allocate port service
[    1.706652] pci_express 0000:00:0e.0:pcie03: allocate port service
[    1.706705] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    1.706715] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    1.707621] ACPI: AC Adapter [ACAD] (on-line)
[    1.707695] ACPI: Battery Slot [BAT1] (battery absent)
[    1.707767] input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input0
[    1.707770] ACPI: Power Button (FF) [PWRF]
[    1.707822] input: Power Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1
[    1.707825] ACPI: Power Button (CM) [PWRB]
[    1.707883] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input2
[    1.708685] ACPI: Lid Switch [LID]
[    1.708734] input: Sleep Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input3
[    1.708737] ACPI: Sleep Button (CM) [SLPB]
[    1.709048] ACPI: processor limited to max C-state 1
[    1.709078] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[    1.709116] processor ACPI_CPU:00: registered as cooling_device0
[    1.709122] ACPI: Processor [CPU0] (supports 8 throttling states)
[    1.709176] processor ACPI_CPU:01: registered as cooling_device1
[    1.712430] thermal LNXTHERM:01: registered as thermal_zone0
[    1.714045] ACPI: Thermal Zone [THRM] (62 C)
[    1.714100] isapnp: Scanning for PnP cards...
[    2.066701] isapnp: No Plug & Play device found
[    2.080279] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
[    2.081331] brd: module loaded
[    2.081686] loop: module loaded
[    2.081771] Fixed MDIO Bus: probed
[    2.081777] PPP generic driver version 2.4.2
[    2.081844] input: Macintosh mouse button emulation as /devices/virtual/input/input4
[    2.081873] Driver 'sd' needs updating - please use bus_type methods
[    2.081883] Driver 'sr' needs updating - please use bus_type methods
[    2.081925] ahci 0000:00:09.0: version 3.0
[    2.082300] ACPI: PCI Interrupt Link [LSI0] enabled at IRQ 20
[    2.082312] ahci 0000:00:09.0: PCI INT A -> Link[LSI0] -> GSI 20 (level, low) -> IRQ 20
[    2.082354] ahci 0000:00:09.0: irq 2300 for MSI/MSI-X
[    2.082428] ahci 0000:00:09.0: AHCI 0001.0100 32 slots 4 ports 3 Gbps 0xf impl IDE mode
[    2.082432] ahci 0000:00:09.0: flags: 64bit sntf led clo pmp pio slum part 
[    2.082435] ahci 0000:00:09.0: setting latency timer to 64
[    2.082971] scsi0 : ahci
[    2.083123] scsi1 : ahci
[    2.083191] scsi2 : ahci
[    2.083257] scsi3 : ahci
[    2.083370] ata1: SATA max UDMA/133 abar m8192@0xf2484000 port 0xf2484100 irq 2300
[    2.083373] ata2: SATA max UDMA/133 abar m8192@0xf2484000 port 0xf2484180 irq 2300
[    2.083376] ata3: SATA max UDMA/133 abar m8192@0xf2484000 port 0xf2484200 irq 2300
[    2.083380] ata4: SATA max UDMA/133 abar m8192@0xf2484000 port 0xf2484280 irq 2300
[    2.676027] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    2.992765] ata1.00: ATA-7: TOSHIBA MK1637GSX, DL050J, max UDMA/100
[    2.992768] ata1.00: 312581808 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    2.993735] ata1.00: configured for UDMA/100
[    3.312027] ata2: SATA link down (SStatus 0 SControl 300)
[    3.632027] ata3: SATA link down (SStatus 0 SControl 300)
[    3.952027] ata4: SATA link down (SStatus 0 SControl 300)
[    3.952153] scsi 0:0:0:0: Direct-Access     ATA      TOSHIBA MK1637GS DL05 PQ: 0 ANSI: 5
[    3.952249] sd 0:0:0:0: [sda] 312581808 512-byte hardware sectors: (160 GB/149 GiB)
[    3.952266] sd 0:0:0:0: [sda] Write Protect is off
[    3.952268] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    3.952294] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    3.952371] sd 0:0:0:0: [sda] 312581808 512-byte hardware sectors: (160 GB/149 GiB)
[    3.952385] sd 0:0:0:0: [sda] Write Protect is off
[    3.952388] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    3.952410] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    3.952414]  sda: sda1 sda2 < sda5 sda6 sda7 >
[    4.068605] sd 0:0:0:0: [sda] Attached SCSI disk
[    4.068666] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    4.068927] pata_amd 0000:00:06.0: version 0.3.10
[    4.068973] pata_amd 0000:00:06.0: setting latency timer to 64
[    4.069087] scsi4 : pata_amd
[    4.069162] scsi5 : pata_amd
[    4.069577] ata5: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0x30c0 irq 14
[    4.069580] ata6: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0x30c8 irq 15
[    4.232345] ata5.00: ATAPI: MATSHITADVD-RAM UJ-850S, 1.61, max UDMA/33
[    4.232370] ata5: nv_mode_filter: 0x739f&0x701f->0x701f, BIOS=0x7000 (0xc000c600) ACPI=0x701f (60:600:0x13)
[    4.248294] ata5.00: configured for UDMA/33
[    4.248837] ata6: port disabled. ignoring.
[    4.250674] scsi 4:0:0:0: CD-ROM            MATSHITA DVD-RAM UJ-850S  1.61 PQ: 0 ANSI: 5
[    4.255044] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[    4.255047] Uniform CD-ROM driver Revision: 3.20
[    4.255151] sr 4:0:0:0: Attached scsi CD-ROM sr0
[    4.255195] sr 4:0:0:0: Attached scsi generic sg1 type 5
[    4.255736] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    4.256092] ACPI: PCI Interrupt Link [LUS2] enabled at IRQ 19
[    4.256103] ehci_hcd 0000:00:02.1: PCI INT B -> Link[LUS2] -> GSI 19 (level, low) -> IRQ 19
[    4.256124] ehci_hcd 0000:00:02.1: setting latency timer to 64
[    4.256127] ehci_hcd 0000:00:02.1: EHCI Host Controller
[    4.256189] ehci_hcd 0000:00:02.1: new USB bus registered, assigned bus number 1
[    4.256218] ehci_hcd 0000:00:02.1: debug port 1
[    4.256222] ehci_hcd 0000:00:02.1: cache line size of 64 is not supported
[    4.256241] ehci_hcd 0000:00:02.1: irq 19, io mem 0xf2489000
[    4.277223] ehci_hcd 0000:00:02.1: USB 2.0 started, EHCI 1.00
[    4.277292] usb usb1: configuration #1 chosen from 1 choice
[    4.277321] hub 1-0:1.0: USB hub found
[    4.277329] hub 1-0:1.0: 4 ports detected
[    4.277754] ACPI: PCI Interrupt Link [Z003] enabled at IRQ 18
[    4.277761] ehci_hcd 0000:00:04.1: PCI INT B -> Link[Z003] -> GSI 18 (level, low) -> IRQ 18
[    4.277773] ehci_hcd 0000:00:04.1: setting latency timer to 64
[    4.277776] ehci_hcd 0000:00:04.1: EHCI Host Controller
[    4.277828] ehci_hcd 0000:00:04.1: new USB bus registered, assigned bus number 2
[    4.277852] ehci_hcd 0000:00:04.1: debug port 1
[    4.277856] ehci_hcd 0000:00:04.1: cache line size of 64 is not supported
[    4.277874] ehci_hcd 0000:00:04.1: irq 18, io mem 0xf2489400
[    4.288028] ehci_hcd 0000:00:04.1: USB 2.0 started, EHCI 1.00
[    4.288087] usb usb2: configuration #1 chosen from 1 choice
[    4.288114] hub 2-0:1.0: USB hub found
[    4.288121] hub 2-0:1.0: 4 ports detected
[    4.288219] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    4.288556] ACPI: PCI Interrupt Link [LUS0] enabled at IRQ 17
[    4.288563] ohci_hcd 0000:00:02.0: PCI INT A -> Link[LUS0] -> GSI 17 (level, low) -> IRQ 17
[    4.288573] ohci_hcd 0000:00:02.0: setting latency timer to 64
[    4.288576] ohci_hcd 0000:00:02.0: OHCI Host Controller
[    4.288629] ohci_hcd 0000:00:02.0: new USB bus registered, assigned bus number 3
[    4.288651] ohci_hcd 0000:00:02.0: irq 17, io mem 0xf2486000
[    4.346067] usb usb3: configuration #1 chosen from 1 choice
[    4.346092] hub 3-0:1.0: USB hub found
[    4.346101] hub 3-0:1.0: 4 ports detected
[    4.346510] ACPI: PCI Interrupt Link [Z002] enabled at IRQ 16
[    4.346518] ohci_hcd 0000:00:04.0: PCI INT A -> Link[Z002] -> GSI 16 (level, low) -> IRQ 16
[    4.346528] ohci_hcd 0000:00:04.0: setting latency timer to 64
[    4.346531] ohci_hcd 0000:00:04.0: OHCI Host Controller
[    4.346576] ohci_hcd 0000:00:04.0: new USB bus registered, assigned bus number 4
[    4.346598] ohci_hcd 0000:00:04.0: irq 16, io mem 0xf2487000
[    4.402835] usb usb4: configuration #1 chosen from 1 choice
[    4.402858] hub 4-0:1.0: USB hub found
[    4.402866] hub 4-0:1.0: 4 ports detected
[    4.402958] uhci_hcd: USB Universal Host Controller Interface driver
[    4.403052] PNP: PS/2 Controller [PNP0303:KBC0,PNP0f13:MSE0] at 0x60,0x64 irq 1,12
[    4.405070] i8042.c: Detected active multiplexing controller, rev 1.1.
[    4.407174] serio: i8042 KBD port at 0x60,0x64 irq 1
[    4.407180] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[    4.407182] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[    4.407185] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[    4.407188] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[    4.409056] mice: PS/2 mouse device common for all mice
[    4.429085] rtc_cmos 00:07: RTC can wake from S4
[    4.429129] rtc_cmos 00:07: rtc core: registered rtc_cmos as rtc0
[    4.429169] rtc0: alarms up to one year, y3k, 114 bytes nvram, hpet irqs
[    4.429239] device-mapper: uevent: version 1.0.3
[    4.429339] device-mapper: ioctl: 4.14.0-ioctl (2008-04-23) initialised: dm-devel@redhat.com
[    4.429509] device-mapper: multipath: version 1.0.5 loaded
[    4.429512] device-mapper: multipath round-robin: version 1.0.0 loaded
[    4.429626] EISA: Probing bus 0 at eisa.0
[    4.429632] Cannot allocate resource for EISA slot 1
[    4.429638] Cannot allocate resource for EISA slot 3
[    4.429640] Cannot allocate resource for EISA slot 4
[    4.429652] EISA: Detected 0 cards.
[    4.429790] cpuidle: using governor ladder
[    4.429827] cpuidle: using governor menu
[    4.430358] TCP cubic registered
[    4.430465] NET: Registered protocol family 10
[    4.430878] lo: Disabled Privacy Extensions
[    4.431195] NET: Registered protocol family 17
[    4.431213] Bluetooth: L2CAP ver 2.11
[    4.431215] Bluetooth: L2CAP socket layer initialized
[    4.431218] Bluetooth: SCO (Voice Link) ver 0.6
[    4.431220] Bluetooth: SCO socket layer initialized
[    4.431275] Bluetooth: RFCOMM socket layer initialized
[    4.431282] Bluetooth: RFCOMM TTY layer initialized
[    4.431284] Bluetooth: RFCOMM ver 1.10
[    4.431343] powernow-k8: Found 1 AMD Turion(tm) 64 X2 Mobile Technology TL-58 processors (2 cpu cores) (version 2.20.00)
[    4.431388] powernow-k8:    0 : fid 0xb (1900 MHz), vid 0x11
[    4.431391] powernow-k8:    1 : fid 0xa (1800 MHz), vid 0x12
[    4.431394] powernow-k8:    2 : fid 0x8 (1600 MHz), vid 0x13
[    4.431397] powernow-k8:    3 : fid 0x0 (800 MHz), vid 0x1e
[    4.431452] Using IPI No-Shortcut mode
[    4.431546] registered taskstats version 1
[    4.431712]   Magic number: 1:738:500
[    4.431830] rtc_cmos 00:07: setting system clock to 2009-07-21 21:27:05 UTC (1248211625)
[    4.431833] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    4.431835] EDD information not available.
[    4.432217] Freeing unused kernel memory: 532k freed
[    4.432385] Write protecting the kernel text: 4112k
[    4.432442] Write protecting the kernel read-only data: 1524k
[    4.457586] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input5
[    4.608042] usb 1-1: new high speed USB device using ehci_hcd and address 2
[    4.708163] ACPI: PCI Interrupt Link [LNK1] enabled at IRQ 10
[    4.708178] ohci1394 0000:01:09.0: PCI INT A -> Link[LNK1] -> GSI 10 (level, low) -> IRQ 10
[    4.759957] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[10]  MMIO=[f2100000-f21007ff]  Max Packet=[2048]  IR/IT contexts=[4/4]
[    4.821352] usb 1-1: configuration #1 chosen from 1 choice
[    4.841439] forcedeth: Reverse Engineered nForce ethernet driver. Version 0.61.
[    4.841824] ACPI: PCI Interrupt Link [LMAC] enabled at IRQ 20
[    4.841829] forcedeth 0000:00:0a.0: PCI INT A -> Link[LMAC] -> GSI 20 (level, low) -> IRQ 20
[    4.841836] forcedeth 0000:00:0a.0: setting latency timer to 64
[    4.936104] usb 1-3: new high speed USB device using ehci_hcd and address 3
[    5.101092] Initializing USB Mass Storage driver...
[    5.104023] scsi6 : SCSI emulation for USB Mass Storage devices
[    5.104450] usb-storage: device found at 2
[    5.104454] usb-storage: waiting for device to settle before scanning
[    5.104465] usbcore: registered new interface driver usb-storage
[    5.104470] USB Mass Storage support registered.
[    5.361277] forcedeth 0000:00:0a.0: ifname eth0, PHY OUI 0x732 @ 1, addr 00:1b:24:d2:05:a2
[    5.361282] forcedeth 0000:00:0a.0: highdma pwrctl mgmt timirq gbit lnktim msi desc-v3
[    5.396680] usb 1-3: configuration #1 chosen from 1 choice
[    5.409091] scsi7 : SCSI emulation for USB Mass Storage devices
[    5.410077] usb-storage: device found at 3
[    5.410080] usb-storage: waiting for device to settle before scanning
[    5.427444] PM: Starting manual resume from disk
[    5.427448] PM: Resume from partition 8:7
[    5.427450] PM: Checking hibernation image.
[    5.427631] PM: Resume from disk failed.
[    5.430467] EXT3-fs: INFO: recovery required on readonly filesystem.
[    5.430471] EXT3-fs: write access will be enabled during recovery.
[    5.521025] usb 2-2: new high speed USB device using ehci_hcd and address 2
[    5.663381] usb 2-2: configuration #1 chosen from 1 choice
[    6.071718] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[00241b00d7cb8400]
[    6.081036] usb 4-4: new full speed USB device using ohci_hcd and address 2
[    6.303176] usb 4-4: configuration #1 chosen from 1 choice
[    6.496331] kjournald starting.  Commit interval 5 seconds
[    6.496346] EXT3-fs: sda6: orphan cleanup on readonly fs
[    6.496354] ext3_orphan_cleanup: deleting unreferenced inode 262169
[    6.496395] ext3_orphan_cleanup: deleting unreferenced inode 262163
[    6.496403] ext3_orphan_cleanup: deleting unreferenced inode 262162
[    6.496410] ext3_orphan_cleanup: deleting unreferenced inode 262149
[    6.496416] ext3_orphan_cleanup: deleting unreferenced inode 262147
[    6.496426] ext3_orphan_cleanup: deleting unreferenced inode 262146
[    6.496432] EXT3-fs: sda6: 6 orphan inodes deleted
[    6.496434] EXT3-fs: recovery complete.
[    6.513885] EXT3-fs: mounted filesystem with ordered data mode.
[   10.101615] usb-storage: device scan complete
[   10.103548] scsi 6:0:0:0: Direct-Access     WD       2500BEV External 1.05 PQ: 0 ANSI: 4
[   10.104538] sd 6:0:0:0: [sdb] 488397168 512-byte hardware sectors: (250 GB/232 GiB)
[   10.106410] sd 6:0:0:0: [sdb] Write Protect is off
[   10.106414] sd 6:0:0:0: [sdb] Mode Sense: 21 00 00 00
[   10.106416] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[   10.107047] sd 6:0:0:0: [sdb] 488397168 512-byte hardware sectors: (250 GB/232 GiB)
[   10.109413] sd 6:0:0:0: [sdb] Write Protect is off
[   10.109416] sd 6:0:0:0: [sdb] Mode Sense: 21 00 00 00
[   10.109418] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[   10.109422]  sdb: sdb1
[   10.110012] sd 6:0:0:0: [sdb] Attached SCSI disk
[   10.110075] sd 6:0:0:0: Attached scsi generic sg2 type 0
[   10.408203] usb-storage: device scan complete
[   10.426174] scsi 7:0:0:0: Direct-Access     JetFlash TS8GJFV35        8.07 PQ: 0 ANSI: 2
[   10.428548] sd 7:0:0:0: [sdc] 16023550 512-byte hardware sectors: (8.20 GB/7.63 GiB)
[   10.429411] sd 7:0:0:0: [sdc] Write Protect is off
[   10.429414] sd 7:0:0:0: [sdc] Mode Sense: 03 00 00 00
[   10.429416] sd 7:0:0:0: [sdc] Assuming drive cache: write through
[   10.430912] sd 7:0:0:0: [sdc] 16023550 512-byte hardware sectors: (8.20 GB/7.63 GiB)
[   10.432413] sd 7:0:0:0: [sdc] Write Protect is off
[   10.432416] sd 7:0:0:0: [sdc] Mode Sense: 03 00 00 00
[   10.432418] sd 7:0:0:0: [sdc] Assuming drive cache: write through
[   10.432421]  sdc: sdc1
[   10.433133] sd 7:0:0:0: [sdc] Attached SCSI removable disk
[   10.433175] sd 7:0:0:0: Attached scsi generic sg3 type 0
[   15.990805] udev: starting version 141
[   16.370166] acpi device:0f: registered as cooling_device2
[   16.370447] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A03:00/device:0c/device:0d/input/input6
[   16.401165] ACPI: Video Device [Z004] (multi-head: yes  rom: no  post: no)
[   16.451837] sdhci: Secure Digital Host Controller Interface driver
[   16.451841] sdhci: Copyright(c) Pierre Ossman
[   16.453499] sdhci-pci 0000:01:09.1: SDHCI controller found [1180:0822] (rev 22)
[   16.453921] ACPI: PCI Interrupt Link [LNK2] enabled at IRQ 11
[   16.453935] sdhci-pci 0000:01:09.1: PCI INT B -> Link[LNK2] -> GSI 11 (level, low) -> IRQ 11
[   16.454090] sdhci-pci 0000:01:09.1: Will use DMA mode even though HW doesn't fully claim to support it.
[   16.454160] mmc0: SDHCI controller on PCI [0000:01:09.1] using DMA
[   16.579562] Linux video capture interface: v2.00
[   16.617487] uvcvideo: Found UVC 1.00 device Acer CrystalEye webcam (064e:a101)
[   16.618455] input: Acer CrystalEye webcam as /devices/pci0000:00/0000:00:04.1/usb2/2-2/2-2:1.0/input/input7
[   16.621111] usbcore: registered new interface driver uvcvideo
[   16.621134] USB Video Class driver (v0.1.0)
[   16.686439] Linux agpgart interface v0.103
[   16.781943] cfg80211: Calling CRDA to update world regulatory domain
[   16.815900] ricoh-mmc: Ricoh MMC Controller disabling driver
[   16.815904] ricoh-mmc: Copyright(c) Philip Langdale
[   16.815944] ricoh-mmc: Ricoh MMC controller found at 0000:01:09.2 [1180:0843] (rev 12)
[   16.815959] ricoh-mmc: Controller is now disabled.
[   17.018406] Bluetooth: Generic Bluetooth USB driver ver 0.3
[   17.018544] usbcore: registered new interface driver btusb
[   17.089519] input: PC Speaker as /devices/platform/pcspkr/input/input8
[   17.215764] cfg80211: World regulatory domain updated:
[   17.215769] 	(start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   17.215772] 	(2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   17.215775] 	(2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   17.215778] 	(2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   17.215780] 	(5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   17.215783] 	(5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   18.018229] nvidia: module license 'NVIDIA' taints kernel.
[   18.273882] ACPI: PCI Interrupt Link [LK2E] enabled at IRQ 19
[   18.273889] nvidia 0000:02:00.0: PCI INT A -> Link[LK2E] -> GSI 19 (level, low) -> IRQ 19
[   18.273897] nvidia 0000:02:00.0: setting latency timer to 64
[   18.275363] NVRM: loading NVIDIA UNIX x86 Kernel Module  180.44  Mon Mar 23 14:59:10 PST 2009
[   18.494572] acer-wmi: Acer Laptop ACPI-WMI Extras
[   18.494919] acer-wmi: Brightness must be controlled by generic video driver
[   18.495032] acer-wmi: software RFKILL enabled
[   18.506449] synaptics was reset on resume, see synaptics_resume_reset if you have trouble on resume
[   18.651541] ACPI: PCI Interrupt Link [LK3E] enabled at IRQ 18
[   18.651548] ath5k_pci 0000:07:00.0: PCI INT A -> Link[LK3E] -> GSI 18 (level, low) -> IRQ 18
[   18.651557] ath5k_pci 0000:07:00.0: setting latency timer to 64
[   18.651645] ath5k_pci 0000:07:00.0: registered as 'phy0'
[   18.692223] phy0: Selected rate control algorithm 'pid'
[   18.892756] ath5k phy0: Atheros AR2425 chip found (MAC: 0xe2, PHY: 0x70)
[   19.091604] ACPI: PCI Interrupt Link [LAZA] enabled at IRQ 17
[   19.091612] HDA Intel 0000:00:07.0: PCI INT A -> Link[LAZA] -> GSI 17 (level, low) -> IRQ 17
[   19.091692] HDA Intel 0000:00:07.0: setting latency timer to 64
[   19.335290] Synaptics Touchpad, model: 1, fw: 6.5, id: 0x81a0b1, caps: 0xa04711/0xa04000
[   19.367805] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio4/input/input9
[   19.456025] hda_codec: Unknown model for ALC268, trying auto-probe from BIOS...
[   21.177383] lp: driver loaded but no devices found
[   21.344761] Adding 2120540k swap on /dev/sda7.  Priority:-1 extents:1 across:2120540k
[   21.887711] EXT3 FS on sda6, internal journal
[   22.961378] type=1505 audit(1248197244.028:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=2233
[   23.017918] type=1505 audit(1248197244.085:3): operation="profile_load" name="/sbin/dhclient-script" name2="default" pid=2237
[   23.018088] type=1505 audit(1248197244.085:4): operation="profile_load" name="/sbin/dhclient3" name2="default" pid=2237
[   23.018147] type=1505 audit(1248197244.085:5): operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" name2="default" pid=2237
[   23.018202] type=1505 audit(1248197244.085:6): operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" name2="default" pid=2237
[   23.183240] type=1505 audit(1248197244.249:7): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=2242
[   23.183488] type=1505 audit(1248197244.249:8): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=2242
[   23.216226] type=1505 audit(1248197244.281:9): operation="profile_load" name="/usr/sbin/mysqld" name2="default" pid=2246
[   23.248585] type=1505 audit(1248197244.313:10): operation="profile_load" name="/usr/sbin/tcpdump" name2="default" pid=2250
[   25.833366] usbcore: registered new interface driver usblp
[   37.481903] vboxdrv: Trying to deactivate the NMI watchdog permanently...
[   37.481908] vboxdrv: Successfully done.
[   37.481910] vboxdrv: Found 2 processor cores.
[   37.481993] vboxdrv: fAsync=1 offMin=0x12d3b offMax=0x12d3b
[   37.482054] vboxdrv: TSC mode is 'asynchronous', kernel timer mode is 'normal'.
[   37.482056] vboxdrv: Successfully loaded version 2.1.4_OSE (interface 0x000a0009).
[   40.563767] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   40.563771] Bluetooth: BNEP filters: protocol multicast
[   40.617439] Bridge firewalling registered
[   42.096334] ppdev: user-space parallel port driver
[   45.936035] forcedeth 0000:00:0a.0: irq 2299 for MSI/MSI-X
[   45.936259] eth0: no link during initialization.
[   45.936761] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   47.001522] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   48.981466] wlan0: direct probe to AP 00:19:e1:ff:e5:f0 try 1
[   49.181024] wlan0: direct probe to AP 00:19:e1:ff:e5:f0 try 2
[   49.380047] wlan0: direct probe to AP 00:19:e1:ff:e5:f0 try 3
[   49.580233] wlan0: direct probe to AP 00:19:e1:ff:e5:f0 timed out
[   80.382585] wlan0: authenticate with AP 00:1e:58:b8:00:25
[   80.384018] wlan0: authenticated
[   80.384023] wlan0: associate with AP 00:1e:58:b8:00:25
[   80.387447] wlan0: RX AssocResp from 00:1e:58:b8:00:25 (capab=0x431 status=0 aid=1)
[   80.387452] wlan0: associated
[   80.388087] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   90.900919] wlan0: no IPv6 routers present
[  108.000056] Clocksource tsc unstable (delta = -218154072 ns)
[  141.252675] wlan0 direct probe responded
[  141.252690] wlan0: authenticate with AP 00:1e:58:b8:00:25
[  141.254152] wlan0: authenticated
[  141.254159] wlan0: associate with AP 00:1e:58:b8:00:25
[  141.259453] wlan0: RX ReassocResp from 00:1e:58:b8:00:25 (capab=0x431 status=0 aid=1)
[  141.259460] wlan0: associated
[  144.283540] wlan0: deauthenticated
[  145.281062] wlan0: direct probe to AP 00:1e:58:b8:00:25 try 1
[  145.284502] wlan0 direct probe responded
[  145.284514] wlan0: authenticate with AP 00:1e:58:b8:00:25
[  145.286252] wlan0: authenticated
[  145.286262] wlan0: associate with AP 00:1e:58:b8:00:25
[  145.296057] wlan0: RX ReassocResp from 00:1e:58:b8:00:25 (capab=0x431 status=0 aid=1)
[  145.296068] wlan0: associated
[  266.205142] CE: hpet increasing min_delta_ns to 15000 nsec
[  266.205294] CE: hpet increasing min_delta_ns to 22500 nsec
[  266.205380] CE: hpet increasing min_delta_ns to 33750 nsec
[  689.673545] usb 1-1: USB disconnect, address 2

```

---

### Post by Stoneface on 2009-07-21
I think

```

[    4.405070] i8042.c: Detected active multiplexing controller, rev 1.1.
[    4.407174] serio: i8042 KBD port at 0x60,0x64 irq 1
[    4.407180] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[    4.407182] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[    4.407185] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[    4.407188] serio: i8042 AUX3 port at 0x60,0x64 irq 12


```

Is connected to my secondary attached screen issue

Or else

```

[    4.429626] EISA: Probing bus 0 at eisa.0
[    4.429632] Cannot allocate resource for EISA slot 1
[    4.429638] Cannot allocate resource for EISA slot 3
[    4.429640] Cannot allocate resource for EISA slot 4

```

But I just don't know yet..

---

### Post by Stoneface on 2009-07-22
The "i8042" chip (or any of its descendants) is the keyboard controller inside the computer and attached to the PS/2 port of newer computers as well as to the system bus (this excludes USB keyboards). This keyboard controller is handled by the drivers/input/serio/i8042.c code in the linux kernel. The input and output ports are defined in drivers/input/serio/i8042-io.h.

So I guess not related to my Samsung SynchMaster or the nVidia Graphics card..

Under NVIDIA X Server Settings I see not options for a second monitor or monitor switching.

---

### Post by Stoneface on 2009-07-22
I opened my xorg.conf @ /etc/X11/xorg.conf. I found this snippet on screens:

```
Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	DefaultDepth	24
EndSection

```

NB External Samsung SynchMaster only indicates I should "Check Signal Cable"

So am I supposed to add my second screen here? How? Or do I need to do something with NVIDIA X Server settings from the command line?

---

### Post by Stoneface on 2009-07-22
[s]Anybody knows a nice Ubuntu guide where attaching an external monitor and making it work is explained????[/S]

Reading this now: [https://help.ubuntu.com/community/NvidiaMultiMonitors](https://help.ubuntu.com/community/NvidiaMultiMonitors)

Some more data:
```

02:00.0 VGA compatible controller: nVidia Corporation GeForce 8400M G (rev a1)

```

```

$ uname -a
Linux me-laptop 2.6.28-13-generic #45-Ubuntu SMP Tue Jun 30 19:49:51 UTC 2009 i686 GNU/Linux

```

---

### Post by Stoneface on 2009-07-22
Well I used the shell command 
```
gksudo nvidia settings
```
entered NVIDIA X Server settings. This time I went to X Server Display Configuration and saw that the Samsung SynchMaster was detected, but that the seond screen was disabled. I enabled it by choosing separate x-screen. For it to become active I had to restart. I see something now. It's like the top left part of the Desktop with part of the menu. But it seems static. I am using the keyboard and mouse now, but my LCD screen registers nothing...? Then I suddenly entered the second screen and had to restart to get control back

---

### Post by Stoneface on 2009-07-22
I restarted - saw nine command prompts, then nine Ubuntu logos and then had to do a hard shut down as Ubuntu jammed (yes not only Windows gets stuck) and restarted manually. 
Well I am using NVIDIA twin view mode now. And I use my LCD screen to view what I am doing on this forum. Its is the primary X display.
The laptop screen does show the desktop as well, but not the active browser window as the lcd screen does . Furthermore the laptop screen only show 70% of the desktop. Really weird.
Can't I just have dual view as in get to see the same on both screens? Argggh
Wondering how I can switch back to my laptop screen using the correct resolution :-(

---

### Post by Stoneface on 2009-07-22
No luck yet getting both screens to display the same and at the right resolution. Anyone?

---

### Post by Stoneface on 2009-07-23
>Bump<

---

### Post by Stoneface on 2009-07-23
Just opened home folder and nautilus opened up on my laptop screen and not in my secondary LCD screen. As my mouse is only moving on my LCD screen I cannot do anything with my just opened home folder. This is driving me insane!
The question is, why did nautilus opened on my laptop screen? Second, how do I get my mouse there? Third, is twin view useful if you just want to work on you larger external screen?

Currrent xorg.conf:

```
# nvidia-settings: X configuration file generated by nvidia-settings
# nvidia-settings:  version 1.0  (buildd@palmer)  Sun Feb  1 20:21:04 UTC 2009

# xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg
# commented out by update-manager, HAL is now used
#Section "InputDevice"
#	Identifier	"Generic Keyboard"
#	Driver		"kbd"
#	Option		"XkbRules"	"xorg"
#	Option		"XkbModel"	"pc105"
#	Option		"XkbLayout"	"us"
#EndSection
# commented out by update-manager, HAL is now used
#Section "InputDevice"
#	Identifier	"Configured Mouse"
#	Driver		"mouse"
#	Option		"CorePointer"
#EndSection
# commented out by update-manager, HAL is now used
#Section "InputDevice"
#	Identifier	"Synaptics Touchpad"
#	Driver		"synaptics"
#	Option		"SendCoreEvents"	"true"
#	Option		"Device"		"/dev/psaux"
#	Option		"Protocol"		"auto-dev"
#	Option		"HorizEdgeScroll"	"0"
#EndSection

Section "ServerLayout"

	# commented out by update-manager, HAL is now used
	#	InputDevice	"Synaptics Touchpad"
    Identifier     "Default Layout"
    Screen      0  "Screen0" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Module"
    Load           "glx"
EndSection

Section "ServerFlags"
    Option         "Xinerama" "0"
EndSection

Section "InputDevice"

    # generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection

Section "InputDevice"

    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "Monitor"
    Identifier     "Configured Monitor"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Samsung SyncMaster"
    HorizSync       30.0 - 81.0
    VertRefresh     56.0 - 60.0
EndSection

Section "Monitor"
    Identifier     "Monitor1"
    VendorName     "Unknown"
    ModelName      "Samsung SyncMaster"
    HorizSync       30.0 - 81.0
    VertRefresh     56.0 - 60.0
EndSection

Section "Device"
    Identifier     "Configured Video Device"
    Driver         "nvidia"
    Option         "NoLogo" "True"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 8400M G"
EndSection

Section "Device"
    Identifier     "Device1"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 8400M G"
    BusID          "PCI:2:0:0"
    Screen          1
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "Configured Video Device"
    Monitor        "Configured Monitor"
    DefaultDepth    24
EndSection

Section "Screen"

# Removed Option "TwinView" "0"
# Removed Option "metamodes" "DFP: nvidia-auto-select +0+0"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "1"
    Option         "metamodes" "CRT: nvidia-auto-select +1280+0, DFP: nvidia-auto-select +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

Section "Screen"
    Identifier     "Screen1"
    Device         "Device1"
    Monitor        "Monitor1"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "metamodes" "CRT: nvidia-auto-select +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

```

---

### Post by Stoneface on 2009-07-28
Nobody here at the Ubuntu with twin view problems with a LCD screen attached like I have? Nautilus and some other programs still open in the second |wrong screen. It seems almost all programs (NVIDIA X Server setting open in the right window) I start from the menu open on my laptop screen which is supposed to be inactive. And that is true as the mouse pointer is on my external screen and all work is done there. So all programs should be opened there too.
Furthermore all desktop items are shown on the inactive screen and not on my external LCD screen. The only programs I can work with at the moment are Firefox - opened clicking on the separate icon- and Shell using a short cut key. And for some weird - and lucky - reason I can open Nvidia X Server settings so I can revert back to normal view or X Window view.
I found a similar error report at Launchpad filed by someone using Intrepid: [https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/282806](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/282806). The bug was solved. But I am using Jaunty Jackalope and I am having the same issue gain :-( I wanted to open a ticket and opened my password manager. But guess what. It opened in the wrong screen!

---

### Post by Stoneface on 2009-07-29
Well at [https://bugs.launchpad.net/ubuntu/+source/glib2.0/+bug/346964](https://bugs.launchpad.net/ubuntu/+source/glib2.0/+bug/346964) and [https://answers.launchpad.net/ubuntu/+source/glib2.0/+question/77380](https://answers.launchpad.net/ubuntu/+source/glib2.0/+question/77380)  there seem to be answers to this bug. The bug I filed was a duplicate.
I will log back into Ubuntu later and try to fix / replace the faulty library. Aparently Ubuntu won't update the library as it is not a security update for Jaunty :-( . The next version of Ubuntu should no longer have this issue..

---

### Post by Stoneface on 2009-08-08
To get Twin view to work on Ubuntu Jaunty Jackalope and for all programs to display on my secondary LCD screen I will follow [these instructions]("https://answers.launchpad.net/ubuntu/+source/glib2.0/+question/77380") and see if that works for me:

This is what I did to fix the dual monitor problem, thanks to the invaluable assistance of midnightflash!

Opened:
[https://launchpad.net/~intuitivenipple/+archive/ppa?field.name_filter=&field.status_filter=published&field.series_filter=jaunty](https://launchpad.net/~intuitivenipple/+archive/ppa?field.name_filter=&field.status_filter=published&field.series_filter=jaunty)

Opened:
[https://launchpad.net/+help/soyuz/ppa-sources-list.html](https://launchpad.net/+help/soyuz/ppa-sources-list.html)

Followed the instructions for PPA and authenication on ppa-sources-list.html

Opened update manager.

Selected only
 libglib2.0-0
 libglib2.0-0-dbg

Installed updates

Restarted

Verified installation using Sunaptic Package Manager File>History

Commit Log for Mon Jul 20 09:27:41 2009
 Upgraded the following packages:
  libglib2.0-0 (2.20.1-0ubuntu2) to 2.20.1-0ubuntu3~tj~ppa1j
  libglib2.0-0-dbg (2.20.1-0ubuntu2) to 2.20.1-0ubuntu3~tj~ppa1j

Tested menu items on screen 1 and they opened properly on screen 1 rather than screen 0. Note: some of the icon on the panel failed so I removed and replaced those.

Opened Software sources (see ppa-sources-list.html above) and unchecked
 [http://ppa.launchpad.net/intuitivenipple/ppa/ubuntu](http://ppa.launchpad.net/intuitivenipple/ppa/ubuntu)
 [http://ppa.launchpad.net/intuitivenipple/ppa/ubuntu](http://ppa.launchpad.net/intuitivenipple/ppa/ubuntu)
(I did this to avoid unintentional updates from this repository)

---

### Post by Stoneface on 2009-08-08
This did not work at all though. Now the terminal opens in my laptop screen as well and the Synaptic Package Manager as well. And as my mouse pointer still correctly opens in the large Samsung LCD screen I cannot use my mouse in the Synaptic Package manager nor in maaaany other programs. Because they only open in the laptop screen.
So until the next release Ubuntu is not an option for people who would like to add a secondary lcd screen to their laptop or desktop in twin view mode. I just does not work. The only programs that I have tried and open in the secondary screen where my mouse pointer is are:
[LIST]
[*]Firefox
[*]Terminal
[*]Gedit
[*]Nvidia Settings
[*]Evolution
[*]Brasero
[/LIST]

---

### Post by Stoneface on 2009-08-08
When I made my laptop screen the primary screen in the Nvidia X Server setting and restarted the mouse pointer opened in my laptop screen and the secondary LCD screen only showed my Desktop background. A desktop wallpaper without icons nor a menu mind you.
All programs except the terminal open on my laptop screen now. And when I move my mouse pointer all the way to the right edge of the laptop screen it goes from one screen to the other. Madness! So this primary screen switch does not solve the problem either..

---

### Post by Stoneface on 2009-08-08
Well no secondary screen in Ubuntu in twin view. It would be great if someone who is reading this thread steps in and tells me there is or there might be a solution out there for me. Anyone??? :confused:

```
# nvidia-settings: X configuration file generated by nvidia-settings
# nvidia-settings:  version 1.0  (buildd@palmer)  Sun Feb  1 20:21:04 UTC 2009

# xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg
# commented out by update-manager, HAL is now used
#Section "InputDevice"
#	Identifier	"Generic Keyboard"
#	Driver		"kbd"
#	Option		"XkbRules"	"xorg"
#	Option		"XkbModel"	"pc105"
#	Option		"XkbLayout"	"us"
#EndSection
# commented out by update-manager, HAL is now used
#Section "InputDevice"
#	Identifier	"Configured Mouse"
#	Driver		"mouse"
#	Option		"CorePointer"
#EndSection
# commented out by update-manager, HAL is now used
#Section "InputDevice"
#	Identifier	"Synaptics Touchpad"
#	Driver		"synaptics"
#	Option		"SendCoreEvents"	"true"
#	Option		"Device"		"/dev/psaux"
#	Option		"Protocol"		"auto-dev"
#	Option		"HorizEdgeScroll"	"0"
#EndSection

Section "ServerLayout"

	# commented out by update-manager, HAL is now used
	#	InputDevice	"Synaptics Touchpad"
    Identifier     "Default Layout"
    Screen      0  "Screen0" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Module"
    Load           "glx"
EndSection

Section "ServerFlags"
    Option         "Xinerama" "0"
EndSection

Section "InputDevice"

    # generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection

Section "InputDevice"

    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "Monitor"
    Identifier     "Configured Monitor"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Samsung SyncMaster"
    HorizSync       30.0 - 81.0
    VertRefresh     56.0 - 60.0
EndSection

Section "Monitor"
    Identifier     "Monitor1"
    VendorName     "Unknown"
    ModelName      "Samsung SyncMaster"
    HorizSync       30.0 - 81.0
    VertRefresh     56.0 - 60.0
EndSection

Section "Device"
    Identifier     "Configured Video Device"
    Driver         "nvidia"
    Option         "NoLogo" "True"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 8400M G"
EndSection

Section "Device"
    Identifier     "Device1"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 8400M G"
    BusID          "PCI:2:0:0"
    Screen          1
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "Configured Video Device"
    Monitor        "Configured Monitor"
    DefaultDepth    24
EndSection

Section "Screen"

# Removed Option "TwinView" "0"
# Removed Option "metamodes" "DFP: nvidia-auto-select +0+0"
# Removed Option "TwinView" "1"
# Removed Option "metamodes" "CRT: nvidia-auto-select +1280+0, DFP: nvidia-auto-select +0+0"
# Removed Option "TwinView" "0"
# Removed Option "metamodes" "DFP: nvidia-auto-select +0+0"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "1"
    Option         "TwinViewXineramaInfoOrder" "DFP-0"
    Option         "metamodes" "CRT: nvidia-auto-select +1280+0, DFP: nvidia-auto-select +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

Section "Screen"
    Identifier     "Screen1"
    Device         "Device1"
    Monitor        "Monitor1"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "metamodes" "CRT: nvidia-auto-select +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

```

---

### Post by Stoneface on 2009-08-08
I wonder if it is normal that my X Server setting mention my Samsung external LCD as monitor and screen twice:

```
Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Samsung SyncMaster"
    HorizSync       30.0 - 81.0
    VertRefresh     56.0 - 60.0
EndSection

Section "Monitor"
    Identifier     "Monitor1"
    VendorName     "Unknown"
    ModelName      "Samsung SyncMaster"
    HorizSync       30.0 - 81.0
    VertRefresh     56.0 - 60.0
EndSection
```

```
Section "Screen"
    Identifier     "Default Screen"
    Device         "Configured Video Device"
    Monitor        "Configured Monitor"
    DefaultDepth    24
EndSection

Section "Screen"

# Removed Option "TwinView" "0"
# Removed Option "metamodes" "DFP: nvidia-auto-select +0+0"
# Removed Option "TwinView" "1"
# Removed Option "metamodes" "CRT: nvidia-auto-select +1280+0, DFP: nvidia-auto-select +0+0"
# Removed Option "TwinView" "0"
# Removed Option "metamodes" "DFP: nvidia-auto-select +0+0"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "1"
    Option         "TwinViewXineramaInfoOrder" "DFP-0"
    Option         "metamodes" "CRT: nvidia-auto-select +1280+0, DFP: nvidia-auto-select +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

Section "Screen"
    Identifier     "Screen1"
    Device         "Device1"
    Monitor        "Monitor1"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "metamodes" "CRT: nvidia-auto-select +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection
```

---

### Post by Stoneface on 2009-08-08
I adjusted my Xorg.conf somewhat. No change to the current situation though. The external screen still onlt shows the desktop wallpaper and I can go there wth my mouse pointer from the right edge of the laptop screen. here is the Xorg.conf I have now:
```
# nvidia-settings: X configuration file generated by nvidia-settings
# nvidia-settings:  version 1.0  (buildd@palmer)  Sun Feb  1 20:21:04 UTC 2009

# xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg
# commented out by update-manager, HAL is now used
#Section "InputDevice"
#	Identifier	"Generic Keyboard"
#	Driver		"kbd"
#	Option		"XkbRules"	"xorg"
#	Option		"XkbModel"	"pc105"
#	Option		"XkbLayout"	"us"
#EndSection
# commented out by update-manager, HAL is now used
#Section "InputDevice"
#	Identifier	"Configured Mouse"
#	Driver		"mouse"
#	Option		"CorePointer"
#EndSection
# commented out by update-manager, HAL is now used
#Section "InputDevice"
#	Identifier	"Synaptics Touchpad"
#	Driver		"synaptics"
#	Option		"SendCoreEvents"	"true"
#	Option		"Device"		"/dev/psaux"
#	Option		"Protocol"		"auto-dev"
#	Option		"HorizEdgeScroll"	"0"
#EndSection

Section "ServerLayout"

	# commented out by update-manager, HAL is now used
	#	InputDevice	"Synaptics Touchpad"
    Identifier     "Default Layout"
    Screen      0  "Screen0" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Module"
    Load           "glx"
EndSection

Section "ServerFlags"
    Option         "Xinerama" "0"
EndSection

Section "InputDevice"

    # generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection

Section "InputDevice"

    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "Monitor"
    Identifier     "Configured Monitor"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Samsung SyncMaster"
    HorizSync       30.0 - 81.0
    VertRefresh     56.0 - 60.0
EndSection


Section "Device"
    Identifier     "Configured Video Device"
    Driver         "nvidia"
    Option         "NoLogo" "True"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 8400M G"
EndSection


Section "Screen"
    Identifier     "Default Screen"
    Device         "Configured Video Device"
    Monitor        "Configured Monitor"
    DefaultDepth    24
    Option "NoLogo" "True"
    Option "TwinView" "True"
    Option "MetaModes" "nvidia-auto-select, nvidia-auto-select"
    SubSection "Display"
    Depth 24
    Modes "nvidia-auto-select"
    EndSubSection
EndSection

Section "Screen"

# Removed Option "TwinView" "0"
# Removed Option "metamodes" "DFP: nvidia-auto-select +0+0"
# Removed Option "TwinView" "1"
# Removed Option "metamodes" "CRT: nvidia-auto-select +1280+0, DFP: nvidia-auto-select +0+0"
# Removed Option "TwinView" "0"
# Removed Option "metamodes" "DFP: nvidia-auto-select +0+0"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "1"
    Option         "TwinViewXineramaInfoOrder" "DFP-0"
    Option         "metamodes" "CRT: nvidia-auto-select +1280+0, DFP: nvidia-auto-select +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

```

---

### Post by Stoneface on 2009-08-08
With the earlier posted xorg.conf and adjusted library my twin view is just single view with the possibility to drag programs from the laptop screen to the Samsung LCD screen. I am typing in Firefox now on the external screen. I opened Firefox on the laptop screen as the menu is only there. Then I dragged it to the attached screen... This is just insane...
There must be something I need to fix in this part of the xorg configuration:
```
Section "Monitor"
    Identifier     "Configured Monitor"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Samsung SyncMaster"
    HorizSync       30.0 - 81.0
    VertRefresh     56.0 - 60.0
EndSection


Section "Device"
    Identifier     "Configured Video Device"
    Driver         "nvidia"
    Option         "NoLogo" "True"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 8400M G"
EndSection


Section "Screen"
    Identifier     "Default Screen"
    Device         "Configured Video Device"
    Monitor        "Configured Monitor"
    DefaultDepth    24
    Option "NoLogo" "True"
    Option "TwinView" "True"
    Option "MetaModes" "nvidia-auto-select, nvidia-auto-select"
    SubSection "Display"
    Depth 24
    Modes "nvidia-auto-select"
    EndSubSection
EndSection

Section "Screen"

# Removed Option "TwinView" "0"
# Removed Option "metamodes" "DFP: nvidia-auto-select +0+0"
# Removed Option "TwinView" "1"
# Removed Option "metamodes" "CRT: nvidia-auto-select +1280+0, DFP: nvidia-auto-select +0+0"
# Removed Option "TwinView" "0"
# Removed Option "metamodes" "DFP: nvidia-auto-select +0+0"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "1"
    Option         "TwinViewXineramaInfoOrder" "DFP-0"
    Option         "metamodes" "CRT: nvidia-auto-select +1280+0, DFP: nvidia-auto-select +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection
```

Or the latest downloaded glib2.0 library from the PPA is just not working properly either.

---

### Post by Stoneface on 2009-08-08
Well basically I guess Twin View just works like this unless I change the offset position??! With the current twin view settings I basically have a laptop as the main screen with the menu and right next to it my Samsung LCD screen as an extension of the desktop. I can go from one to the other with the mouse pointer. The right side of my laptop screen is the border so to speak...
I guess I will just have to live with these settings until something better comes along. I have been at this for a while now and I have had no hints from anybody else on this forum whatsoever. So I guess it's a mystery to everybody here.. 

--------------------------------------
New information
---------------------------------------
After using my two screens for a while like this I did get these messages in dmesg after not having actively used the laptop for several hours:
```
[37998.894404] NVRM: Xid (0002:00): 13, 0003 00000000 00008297 00001408 00000001 00000040
[41773.401904] NVRM: Xid (0002:00): 13, 0003 00000000 00008297 00001408 00000001 00000040
[44504.058060] NVRM: Xid (0002:00): 13, 0003 00000000 00008297 00001408 00000001 00000040
[44504.289694] NVRM: Xid (0002:00): 13, 0003 00000000 00008297 00001408 00000001 00000040
[44504.548620] NVRM: Xid (0002:00): 13, 0003 00000000 00008297 00001408 00000001 00000040
[44504.772582] NVRM: Xid (0002:00): 13, 0003 00000000 00008297 00001408 00000001 00000040
[44505.957595] NVRM: Xid (0002:00): 13, 0003 00000000 00008297 00001408 00000001 00000040
[44507.951901] NVRM: Xid (0002:00): 13, 0003 00000000 00008297 00001408 00000001 00000040

```

One terminal window behaved really off - I couldn't use it anymore -  and some program screens that were opened in the secondary Samsung Flat screen were moved to the laptop screen... .. According to someone here: [http://www.nvnews.net/vbulletin/showthread.php?t=123912&page=32](http://www.nvnews.net/vbulletin/showthread.php?t=123912&page=32) this a sign of screen corruption. After all the hassle I can believe that. So this is definitely not a perfect solution for a dual monitor system on Ubuntu yet..

---

### Post by Stoneface on 2009-08-11
By accident I changed X screen. Then I got these NVIDIA screen errors:
```

[104702.523165] NVRM: Xid (0002:00): 13, 0003 00000000 00008297 00001408 00000001 00000040
[104702.523744] NVRM: Xid (0002:00): 13, 0003 00000000 00008297 00001408 00000001 00000040

```

I might ask some help at the earlier mentioned forum [http://www.nvnews.net/vbulletin/](http://www.nvnews.net/vbulletin/). Maybe they can help. No-one here has so far been able to.

---

### Post by Stoneface on 2009-08-11
I opened an new thread @ NV News here: [http://www.nvnews.net/vbulletin/showthread.php?t=137218](http://www.nvnews.net/vbulletin/showthread.php?t=137218) . I will post back if I have more news.

---

### Post by urlwolf on 2009-08-11
> **Stoneface said:**
> I opened an new thread @ NV News here: [http://www.nvnews.net/vbulletin/showthread.php?t=137218](http://www.nvnews.net/vbulletin/showthread.php?t=137218) . I will post back if I have more news.

Thanks for keeping a log here.
It's a bit scary that (1) nobody answered and (2) you spent so much time on finding a solution -yet found nothing-

---

### Post by Stoneface on 2009-08-11
@ Urwolf. Thanks for the heads up :-) . Yeah it is really too bad nobody else here has had any insights so far. I switched to clone view now(offset 0+0). My computer is faster again, Rhythbox no longer hangs and I can type normally in Firefox again. 
I think the way twin view functioned with the secondary screen positioned left or right of the main screen (as an extension) causes the Xorg to eat up a lot of memory and causes screen error and display problems. Now I have my 24" flat screen as the main screen and my laptop clones is. Like this my laptop shows only a part of the main screen as it's resolution is smaller. But I like the resolution of the large screen so I keep it like this.
I will keep monitoring the error logs and general functioning of my box and will post back if I have any issues left. For now everyone should be warned of using twin view via NVIDIA X Server settings. It slows down your PC and causes screen display issues. Hopefully clone view will work so I can keep on using my brand new 24" samsung Synch Master

---

