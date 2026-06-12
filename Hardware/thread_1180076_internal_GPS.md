---
title: "internal GPS?"
date: 2009-06-06
forum: Hardware
---

### Post by Anfanglir on 2009-06-06
EDIT: Problem solved. END EDIT

Hi
is it possible to get Ubuntu Jaunty to recognise an internal GPS? I have a Fujitsu u820 with an internal gps chip made by Kyocera. Kyocera seem to use Sirf Star III chipsets on recent products, and i suspect thats whath the u820 have. I have tried different gps applications available in Ubuntu but they cant find the gps. I guess they look for external devices by default.

The gps is recognised in Windows as com 3, the location path as reported by Windows device manager is: 
PCIROOT(0)#PCI(1D01)#USBROOT(0)#USB(1)

The output for dmesg is:
[    0.676109] Bluetooth: HCI socket layer initialized
[    0.676109] NET: Registered protocol family 8
[    0.676109] NET: Registered protocol family 20
[    0.676145] NetLabel: Initializing
[    0.676155] NetLabel:  domain hash size = 128
[    0.676176] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.676204] NetLabel:  unlabeled traffic allowed by default
[    0.676235] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[    0.676245] hpet0: 3 comparators, 64-bit 14.318180 MHz counter
[    0.680118] AppArmor: AppArmor Filesystem Enabled
[    0.684028] Switched to high resolution mode on CPU 0
[    0.684369] Switched to high resolution mode on CPU 1
[    0.688091] pnp: PnP ACPI init
[    0.688131] ACPI: bus type pnp registered
[    0.691881] pnp: PnP ACPI: found 10 devices
[    0.691886] ACPI: ACPI bus type pnp unregistered
[    0.691894] PnPBIOS: Disabled by ACPI PNP
[    0.691919] system 00:01: ioport range 0x374-0x375 has been reserved
[    0.691925] system 00:01: ioport range 0x3f4-0x3f5 has been reserved
[    0.691931] system 00:01: ioport range 0x4d0-0x4d1 has been reserved
[    0.691937] system 00:01: ioport range 0x680-0x69f has been reserved
[    0.691943] system 00:01: ioport range 0x800-0x80f has been reserved
[    0.691949] system 00:01: ioport range 0x1000-0x107f has been reserved
[    0.691955] system 00:01: ioport range 0x1080-0x10ff has been reserved
[    0.691961] system 00:01: ioport range 0x1100-0x111f has been reserved
[    0.691967] system 00:01: ioport range 0x1180-0x11bf has been reserved
[    0.691973] system 00:01: ioport range 0x1640-0x164f has been reserved
[    0.691980] system 00:01: ioport range 0xf800-0xf87f has been reserved
[    0.691986] system 00:01: ioport range 0xf880-0xf8ff has been reserved
[    0.691992] system 00:01: ioport range 0xfc00-0xfc7f has been reserved
[    0.691998] system 00:01: ioport range 0xfc80-0xfcff has been reserved
[    0.692004] system 00:01: ioport range 0xfd00-0xfd6f has been reserved
[    0.692029] system 00:01: ioport range 0xfe00-0xfe03 has been reserved
[    0.692037] system 00:01: iomem range 0xc0000-0xdffff could not be reserved
[    0.692044] system 00:01: iomem range 0xe0000-0xeffff could not be reserved
[    0.692050] system 00:01: iomem range 0xf0000-0xfffff could not be reserved
[    0.692057] system 00:01: iomem range 0x3f800000-0x3fffffff has been reserved
[    0.692063] system 00:01: iomem range 0x40000000-0x7fffffff has been reserved
[    0.692077] system 00:02: iomem range 0xfd000000-0xfd003fff has been reserved
[    0.692083] system 00:02: iomem range 0xe0000000-0xefffffff could not be reserved
[    0.692090] system 00:02: iomem range 0xfed00000-0xfed3ffff has been reserved
[    0.692096] system 00:02: iomem range 0xfed40000-0xfed44fff has been reserved
[    0.692102] system 00:02: iomem range 0xfed45000-0xfed4bfff has been reserved
[    0.692109] system 00:02: iomem range 0xfef00000-0xfeffffff has been reserved
[    0.727048] pci 0000:05:03.0: BAR 10: can't allocate mem resource [0x000000-0x3ffffff]
[    0.727063] pci 0000:05:03.0: CardBus bridge, secondary bus 0000:06
[    0.727068] pci 0000:05:03.0:   IO window: 0x002400-0x0024ff
[    0.727079] pci 0000:05:03.0:   IO window: 0x002800-0x0028ff
[    0.727089] pci 0000:05:03.0:   PREFETCH window: 0x80000000-0x83ffffff
[    0.727100] pci 0000:04:00.0: PCI bridge, secondary bus 0000:05
[    0.727107] pci 0000:04:00.0:   IO window: 0x2000-0x2fff
[    0.727119] pci 0000:04:00.0:   MEM window: 0xfd200000-0xfd4fffff
[    0.727129] pci 0000:04:00.0:   PREFETCH window: 0x00000080000000-0x00000083ffffff
[    0.727145] pci 0000:00:1c.0: PCI bridge, secondary bus 0000:04
[    0.727151] pci 0000:00:1c.0:   IO window: 0x2000-0x2fff
[    0.727159] pci 0000:00:1c.0:   MEM window: 0xfd200000-0xfd4fffff
[    0.727166] pci 0000:00:1c.0:   PREFETCH window: 0x00000080000000-0x00000083ffffff
[    0.727177] pci 0000:00:1c.1: PCI bridge, secondary bus 0000:08
[    0.727181] pci 0000:00:1c.1:   IO window: disabled
[    0.727189] pci 0000:00:1c.1:   MEM window: 0xfd500000-0xfd5fffff
[    0.727196] pci 0000:00:1c.1:   PREFETCH window: disabled
[    0.727223] pci 0000:00:1c.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    0.727232] pci 0000:00:1c.0: setting latency timer to 64
[    0.727250] pci 0000:04:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.727260] pci 0000:04:00.0: setting latency timer to 64
[    0.727278] pci 0000:05:03.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    0.727295] pci 0000:00:1c.1: PCI INT B -> GSI 16 (level, low) -> IRQ 16
[    0.727302] pci 0000:00:1c.1: setting latency timer to 64
[    0.727309] bus: 00 index 0 io port: [0x00-0xffff]
[    0.727314] bus: 00 index 1 mmio: [0x000000-0xffffffff]
[    0.727319] bus: 04 index 0 io port: [0x2000-0x2fff]
[    0.727324] bus: 04 index 1 mmio: [0xfd200000-0xfd4fffff]
[    0.727329] bus: 04 index 2 mmio: [0x80000000-0x83ffffff]
[    0.727333] bus: 04 index 3 mmio: [0x0-0x0]
[    0.727337] bus: 05 index 0 io port: [0x2000-0x2fff]
[    0.727342] bus: 05 index 1 mmio: [0xfd200000-0xfd4fffff]
[    0.727347] bus: 05 index 2 mmio: [0x80000000-0x83ffffff]
[    0.727351] bus: 05 index 3 mmio: [0x0-0x0]
[    0.727356] bus: 06 index 0 io port: [0x2400-0x24ff]
[    0.727360] bus: 06 index 1 io port: [0x2800-0x28ff]
[    0.727365] bus: 06 index 2 mmio: [0x80000000-0x83ffffff]
[    0.727369] bus: 06 index 3 mmio: [0x0-0x0]
[    0.727374] bus: 08 index 0 mmio: [0x0-0x0]
[    0.727378] bus: 08 index 1 mmio: [0xfd500000-0xfd5fffff]
[    0.727382] bus: 08 index 2 mmio: [0x0-0x0]
[    0.727386] bus: 08 index 3 mmio: [0x0-0x0]
[    0.727408] NET: Registered protocol family 2
[    0.740282] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.740884] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.741977] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.742617] TCP: Hash tables configured (established 131072 bind 65536)
[    0.742624] TCP reno registered
[    0.748354] NET: Registered protocol family 1
[    0.748620] checking if image is initramfs... it is
[    1.732493] Freeing initrd memory: 7369k freed
[    1.732573] Simple Boot Flag at 0x7b set to 0x1
[    1.732952] cpufreq: No nForce2 chipset.
[    1.733257] audit: initializing netlink socket (disabled)
[    1.733301] type=2000 audit(1244298014.732:1): initialized
[    1.747832] highmem bounce pool size: 64 pages
[    1.747844] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    1.750689] VFS: Disk quotas dquot_6.5.1
[    1.750813] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    1.752140] fuse init (API version 7.10)
[    1.752325] msgmni has been set to 1724
[    1.752696] alg: No test for stdrng (krng)
[    1.752729] io scheduler noop registered
[    1.752734] io scheduler anticipatory registered
[    1.752738] io scheduler deadline registered
[    1.752776] io scheduler cfq registered (default)
[    1.752803] pci 0000:00:02.0: Boot video device
[    1.757567] pcieport-driver 0000:00:1c.0: setting latency timer to 64
[    1.757611] pci_express 0000:00:1c.0:pcie00: allocate port service
[    1.757646] pci_express 0000:00:1c.0:pcie02: allocate port service
[    1.757721] pcieport-driver 0000:00:1c.1: setting latency timer to 64
[    1.757761] pci_express 0000:00:1c.1:pcie00: allocate port service
[    1.757788] pci_express 0000:00:1c.1:pcie02: allocate port service
[    1.757919] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    1.758303] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    1.758650] ACPI: AC Adapter [AC] (on-line)
[    1.760233] ACPI: EC: non-query interrupt received, switching to interrupt mode
[    1.773640] ACPI: Battery Slot [CMB1] (battery present)
[    1.773786] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input0
[    1.773892] ACPI: Lid Switch [LID]
[    1.773993] input: Power Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1
[    1.773999] ACPI: Power Button (CM) [PWRB]
[    1.775517] ACPI: SSDT 3F5BFDA3, 0245 (r1 FUJ    FJNB1EE   1180000 FUJ       100)
[    1.776293] ACPI: SSDT 3F5C02BC, 05CD (r1 FUJ    FJNB1EE   1180000 FUJ       100)
[    1.777087] Monitor-Mwait will be used to enter C-1 state
[    1.777094] Monitor-Mwait will be used to enter C-2 state
[    1.777124] ACPI: CPU0 (power states: C1[C1] C2[C2])
[    1.777178] processor ACPI_CPU:00: registered as cooling_device0
[    1.777187] ACPI: Processor [CPU0] (supports 8 throttling states)
[    1.777881] ACPI: SSDT 3F5C01F8, 00C4 (r1 FUJ    FJNB1EE   1180000 FUJ       100)
[    1.778535] ACPI: SSDT 3F5C0889, 0047 (r1 FUJ    FJNB1EE   1180000 FUJ       100)
[    1.779470] ACPI: CPU1 (power states: C1[C1] C2[C2])
[    1.779513] processor ACPI_CPU:01: registered as cooling_device1
[    1.779522] ACPI: Processor [CPU1] (supports 8 throttling states)
[    1.783862] thermal LNXTHERM:01: registered as thermal_zone0
[    1.784051] ACPI: Thermal Zone [TZ00] (27 C)
[    1.784744] thermal LNXTHERM:02: registered as thermal_zone1
[    1.784948] ACPI: Thermal Zone [TZ01] (27 C)
[    1.785053] isapnp: Scanning for PnP cards...
[    2.139172] isapnp: No Plug & Play device found
[    2.145486] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
[    2.147385] brd: module loaded
[    2.148046] loop: module loaded
[    2.148217] Fixed MDIO Bus: probed
[    2.148230] PPP generic driver version 2.4.2
[    2.148355] input: Macintosh mouse button emulation as /devices/virtual/input/input2
[    2.148417] Driver 'sd' needs updating - please use bus_type methods
[    2.148437] Driver 'sr' needs updating - please use bus_type methods
[    2.149749] pata_sch 0000:00:1f.1: version 0.2
[    2.149818] pata_sch 0000:00:1f.1: setting latency timer to 64
[    2.149981] scsi0 : pata_sch
[    2.150191] scsi1 : pata_sch
[    2.151207] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0x1810 irq 14
[    2.151214] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x1818 irq 15
[    2.312590] ata1.00: ATA-7: TOSHIBA MK6028GAL, BN101F, max UDMA/100
[    2.312603] ata1.00: 117210240 sectors, multi 16: LBA48 
[    2.320614] ata1.00: configured for UDMA/100
[    2.486945] scsi 0:0:0:0: Direct-Access     ATA      TOSHIBA MK6028GA BN10 PQ: 0 ANSI: 5
[    2.487176] sd 0:0:0:0: [sda] 117210240 512-byte hardware sectors: (60.0 GB/55.8 GiB)
[    2.487219] sd 0:0:0:0: [sda] Write Protect is off
[    2.487225] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    2.487296] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.487450] sd 0:0:0:0: [sda] 117210240 512-byte hardware sectors: (60.0 GB/55.8 GiB)
[    2.487490] sd 0:0:0:0: [sda] Write Protect is off
[    2.487496] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    2.487565] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.487574]  sda: sda1 sda2 sda3 sda4 < sda5 sda6 >
[    2.552358] sd 0:0:0:0: [sda] Attached SCSI disk
[    2.552464] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    2.552718] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    2.552779] ehci_hcd 0000:00:1d.7: PCI INT D -> GSI 21 (level, low) -> IRQ 21
[    2.552816] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    2.552823] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    2.552939] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 1
[    2.556874] ehci_hcd 0000:00:1d.7: debug port 1
[    2.556885] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
[    2.556913] ehci_hcd 0000:00:1d.7: irq 21, io mem 0xfd8a5000
[    2.572081] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    2.572343] usb usb1: configuration #1 chosen from 1 choice
[    2.572444] hub 1-0:1.0: USB hub found
[    2.572460] hub 1-0:1.0: 8 ports detected
[    2.572690] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    2.572735] uhci_hcd: USB Universal Host Controller Interface driver
[    2.572815] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    2.572827] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    2.572833] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    2.572931] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    2.572972] uhci_hcd 0000:00:1d.0: irq 23, io base 0x00001820
[    2.573147] usb usb2: configuration #1 chosen from 1 choice
[    2.573200] hub 2-0:1.0: USB hub found
[    2.573215] hub 2-0:1.0: 2 ports detected
[    2.573374] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    2.573385] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    2.573391] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    2.573484] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3
[    2.573523] uhci_hcd 0000:00:1d.1: irq 19, io base 0x00001840
[    2.573678] usb usb3: configuration #1 chosen from 1 choice
[    2.573731] hub 3-0:1.0: USB hub found
[    2.573746] hub 3-0:1.0: 2 ports detected
[    2.573908] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    2.573919] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    2.573925] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    2.574008] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4
[    2.574047] uhci_hcd 0000:00:1d.2: irq 18, io base 0x00001860
[    2.574199] usb usb4: configuration #1 chosen from 1 choice
[    2.574257] hub 4-0:1.0: USB hub found
[    2.574271] hub 4-0:1.0: 2 ports detected
[    2.574507] usbcore: registered new interface driver libusual
[    2.574581] usbcore: registered new interface driver usbserial
[    2.574604] USB Serial support registered for generic
[    2.574642] usbcore: registered new interface driver usbserial_generic
[    2.574646] usbserial: USB Serial Driver core
[    2.574729] PNP: PS/2 Controller [PNP0303:KBC,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    2.577505] i8042.c: Detected active multiplexing controller, rev 1.1.
[    2.578913] serio: i8042 KBD port at 0x60,0x64 irq 1
[    2.578927] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[    2.578934] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[    2.578940] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[    2.578948] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[    2.580187] mice: PS/2 mouse device common for all mice
[    2.592391] rtc_cmos 00:08: rtc core: registered rtc_cmos as rtc0
[    2.592443] rtc0: alarms up to one month, y3k, 114 bytes nvram, hpet irqs
[    2.592590] device-mapper: uevent: version 1.0.3
[    2.592801] device-mapper: ioctl: 4.14.0-ioctl (2008-04-23) initialised: dm-devel@redhat.com
[    2.592985] device-mapper: multipath: version 1.0.5 loaded
[    2.592991] device-mapper: multipath round-robin: version 1.0.0 loaded
[    2.593198] EISA: Probing bus 0 at eisa.0
[    2.593212] Cannot allocate resource for EISA slot 1
[    2.593217] Cannot allocate resource for EISA slot 2
[    2.593254] EISA: Detected 0 cards.
[    2.593480] cpuidle: using governor ladder
[    2.593659] cpuidle: using governor menu
[    2.594757] TCP cubic registered
[    2.595005] NET: Registered protocol family 10
[    2.595870] lo: Disabled Privacy Extensions
[    2.596569] NET: Registered protocol family 17
[    2.596610] Bluetooth: L2CAP ver 2.11
[    2.596614] Bluetooth: L2CAP socket layer initialized
[    2.596619] Bluetooth: SCO (Voice Link) ver 0.6
[    2.596623] Bluetooth: SCO socket layer initialized
[    2.596715] Bluetooth: RFCOMM socket layer initialized
[    2.596730] Bluetooth: RFCOMM TTY layer initialized
[    2.596735] Bluetooth: RFCOMM ver 1.10
[    2.596808] Marking TSC unstable due to TSC halts in idle
[    2.598254] Using IPI No-Shortcut mode
[    2.598430] registered taskstats version 1
[    2.598629]   Magic number: 13:205:333
[    2.598665] tty tty54: hash matches
[    2.598749] rtc_cmos 00:08: setting system clock to 2009-06-06 14:20:16 UTC (1244298016)
[    2.598757] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    2.598761] EDD information not available.
[    2.599197] Freeing unused kernel memory: 532k freed
[    2.599493] Write protecting the kernel text: 4128k
[    2.599594] Write protecting the kernel read-only data: 1532k
[    2.622046] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3
[    3.045470] 8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)
[    3.045545] 8139cp 0000:05:04.0: This (id 10ec:8139 rev 10) is not an 8139C+ compatible chip, use 8139too
[    3.052915] 8139too Fast Ethernet driver 0.9.28
[    3.053011] 8139too 0000:05:04.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    3.057314] eth0: RealTek RTL8139 at 0x2000, 00:23:26:41:26:10, IRQ 16
[    3.057320] eth0:  Identified 8139 chip type 'RTL-8101'
[    3.277067] usb 1-8: new high speed USB device using ehci_hcd and address 6
[    3.583325] usb 1-8: configuration #1 chosen from 1 choice
[    3.825304] usb 2-2: new low speed USB device using uhci_hcd and address 2
[    4.006946] usb 2-2: configuration #1 chosen from 1 choice
[    4.035275] usbcore: registered new interface driver hiddev
[    4.051835] generic-usb 0003:0430:0530.0001: hiddev96,hidraw0: USB HID v1.00 Device [Fujitsu Component USB Touch Panel] on usb-0000:00:1d.0-2/input0
[    4.051879] usbcore: registered new interface driver usbhid
[    4.051888] usbhid: v2.6:USB HID core driver
[    4.248118] usb 3-1: new full speed USB device using uhci_hcd and address 2
[    4.431829] usb 3-1: configuration #1 chosen from 1 choice
[    4.537556] PM: Starting manual resume from disk
[    4.537566] PM: Resume from partition 8:5
[    4.537570] PM: Checking hibernation image.
[    4.537950] PM: Resume from disk failed.
[    4.587929] kjournald starting.  Commit interval 5 seconds
[    4.587968] EXT3-fs: mounted filesystem with ordered data mode.
[    4.676106] usb 3-2: new full speed USB device using uhci_hcd and address 3
[    4.894350] usb 3-2: configuration #1 chosen from 1 choice
[    5.136106] usb 4-1: new full speed USB device using uhci_hcd and address 2
[    5.308340] usb 4-1: configuration #1 chosen from 1 choice
[   14.010665] udev: starting version 141
[   14.271437] Bluetooth: Generic Bluetooth USB driver ver 0.3
[   14.271784] usbcore: registered new interface driver btusb
[   15.372725] input: Fujitsu FUJ02B1 as /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:15/FUJ02B1:00/input/input4
[   15.376443] ACPI: Fujitsu FUJ02B1 [FJEX] (on)
[   15.378363] input: Fujitsu FUJ02E3 as /devices/LNXSYSTM:00/device:00/FUJ02E3:00/input/input5
[   15.388319] ACPI: Fujitsu FUJ02E3 [FEXT] (on)
[   15.388853] fujitsu-laptop: driver 0.4.3 successfully loaded.
[   15.674484] fsc_btns: found: Unknown (using defaults)
[   15.675015] input: fsc tablet buttons as /devices/platform/fsc_btns/input/input6
[   15.681956] input: fsc tablet switch as /devices/platform/fsc_btns/input/input7
[   15.700313] isch_smbus 0000:00:1f.0: SMBus region 0x1100 already in use!
[   15.700336] isch_smbus: probe of 0000:00:1f.0 failed with error -16
[   15.708112] input: PC Speaker as /devices/platform/pcspkr/input/input8
[   15.742668] sdhci: Secure Digital Host Controller Interface driver
[   15.742677] sdhci: Copyright(c) Pierre Ossman
[   15.746959] sdhci-pci 0000:00:1e.0: SDHCI controller found [8086:811c] (rev 6)
[   15.747000] sdhci-pci 0000:00:1e.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   15.747106] sdhci-pci 0000:00:1e.0: setting latency timer to 64
[   15.747381] mmc0: SDHCI controller on PCI [0000:00:1e.0] using DMA
[   15.789639] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   15.815815] ACPI Error (exresop-0590): Needed [Buffer/String/Package], found [Integer] f6ff74d8 [20080926]
[   15.815835] ACPI Exception (dswexec-0445): AE_AML_OPERAND_TYPE, While resolving operands for [OpcodeName unavailable] [20080926]
[   15.815855] ACPI Error (psparse-0524): Method parse/execution failed [\_SB_.PCI0.GFX0.LCD_._BQC] (Node f6c194c8), AE_AML_OPERAND_TYPE
[   15.872342] acpi device:04: registered as cooling_device2
[   15.873520] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:02/input/input9
[   15.878524] Linux video capture interface: v2.00
[   15.892213] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)
[   16.035901] cfg80211: Calling CRDA to update world regulatory domain
[   16.089816] synaptics was reset on resume, see synaptics_resume_reset if you have trouble on resume
[   16.129574] cfg80211: World regulatory domain updated:
[   16.129582] 	(start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   16.129589] 	(2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   16.129595] 	(2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   16.129601] 	(2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   16.129606] 	(5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   16.129611] 	(5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   16.150209] yenta_cardbus 0000:05:03.0: CardBus bridge found [10cf:14c0]
[   16.150261] yenta_cardbus 0000:05:03.0: CardBus bridge, secondary bus 0000:06
[   16.150270] yenta_cardbus 0000:05:03.0:   IO window: 0x002400-0x0024ff
[   16.150283] yenta_cardbus 0000:05:03.0:   IO window: 0x002800-0x0028ff
[   16.150297] yenta_cardbus 0000:05:03.0:   PREFETCH window: 0x80000000-0x83ffffff
[   16.150311] yenta_cardbus 0000:05:03.0:   MEM window: 0xfd240000-0xfd27ffff
[   16.150330] yenta_cardbus 0000:05:03.0: O2: res at 0x94/0xD4: 00/ea
[   16.150336] yenta_cardbus 0000:05:03.0: O2: enabling read prefetch/write burst
[   16.176233] uvcvideo: Found UVC 1.00 device USB Camera (03ee:7320)
[   16.178211] input: USB Camera as /devices/pci0000:00/0000:00:1d.7/usb1/1-8/1-8:1.0/input/input10
[   16.184575] usbcore: registered new interface driver uvcvideo
[   16.184661] USB Video Class driver (v0.1.0)
[   16.281594] yenta_cardbus 0000:05:03.0: ISA IRQ mask 0x0000, PCI irq 19
[   16.281605] yenta_cardbus 0000:05:03.0: Socket status: 30000006
[   16.281616] yenta_cardbus 0000:05:03.0: pcmcia: parent PCI bridge I/O window: 0x2000 - 0x2fff
[   16.281624] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x2000-0x2fff: clean.
[   16.282054] yenta_cardbus 0000:05:03.0: pcmcia: parent PCI bridge Memory window: 0xfd200000 - 0xfd4fffff
[   16.282061] yenta_cardbus 0000:05:03.0: pcmcia: parent PCI bridge Memory window: 0x80000000 - 0x83ffffff
[   16.402345] ath9k: 0.1
[   16.402657] ath9k 0000:08:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   16.402677] ath9k 0000:08:00.0: setting latency timer to 64
[   16.658784] psmouse serio4: ID: 42 01 0a<7>phy0: Selected rate control algorithm 'ath9k_rate_control'
[   16.950012] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x100-0x3af: clean.
[   16.952238] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x3e0-0x4ff: clean.
[   16.953216] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x820-0x8ff: clean.
[   16.954016] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xc00-0xcf7: clean.
[   16.955154] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xa00-0xaff: clean.
[   17.170636] HDA Intel 0000:00:1b.0: power state changed by ACPI to D0
[   17.170659] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   17.170824] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   17.173954] Registered led device: ath9k-phy0:radio
[   17.174010] Registered led device: ath9k-phy0:assoc
[   17.174063] Registered led device: ath9k-phy0:tx
[   17.174128] Registered led device: ath9k-phy0:rx
[   17.175336] phy0: Atheros 9280: mem=0xf7f40000, irq=17
[   17.202962] hda_codec: Unknown model for ALC269, trying auto-probe from BIOS...
[   17.253075] input: PS/2 Generic Mouse as /devices/platform/i8042/serio4/input/input11
[   17.557100] lp: driver loaded but no devices found
[   17.769718] Adding 570268k swap on /dev/sda5.  Priority:-1 extents:1 across:570268k
[   18.352244] EXT3 FS on sda6, internal journal
[   19.884208] type=1505 audit(1244290833.785:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=2066
[   19.997973] type=1505 audit(1244290833.897:3): operation="profile_load" name="/sbin/dhclient-script" name2="default" pid=2070
[   19.998286] type=1505 audit(1244290833.897:4): operation="profile_load" name="/sbin/dhclient3" name2="default" pid=2070
[   19.998405] type=1505 audit(1244290833.897:5): operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" name2="default" pid=2070
[   19.998509] type=1505 audit(1244290833.897:6): operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" name2="default" pid=2070
[   20.321120] type=1505 audit(1244290834.221:7): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=2075
[   20.321598] type=1505 audit(1244290834.221:8): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=2075
[   20.387375] type=1505 audit(1244290834.285:9): operation="profile_load" name="/usr/sbin/tcpdump" name2="default" pid=2079
[   26.099069] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   26.099076] Bluetooth: BNEP filters: protocol multicast
[   26.132745] Bridge firewalling registered
[   27.960424] ppdev: user-space parallel port driver
[   29.483761] Linux agpgart interface v0.103
[   29.600422] [drm] Initialized drm 1.1.0 20060810
[   29.656548] psb 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   29.656562] psb 0000:00:02.0: setting latency timer to 64
[   29.656652] [drm] psb - 5.0.0.0045
[   29.672065] [drm:psb_do_init] *ERROR* Debug is 0x00000000
[   29.701939] psb 0000:00:02.0: firmware: requesting msvdx_fw.bin
[   29.751454] [drm:msvdx_get_fw] *ERROR* MSVDX: msvdx_fw.bin request_firmware failed: Reason -2
[   29.751468] [drm:psb_setup_fw] *ERROR* psb: No valid msvdx_fw.bin firmware found.
[   29.767897] [drm] SGX core id = 0x01130000
[   29.767907] [drm] SGX core rev major = 0x01, minor = 0x02
[   29.767913] [drm] SGX core rev maintenance = 0x01, designer = 0x00
[   29.768923] [drm] intel_lvds_init: OpRegion has the VBT address
[   29.768939] [drm] intel_lvds_init: The bdb->signature is BIOS_DATA_BLOCK &#65533;, the bdb_off is 48
[   29.768968] [drm] intel_lvds_init: BLC Data in BIOS VBT tables: datasize=0 paneltype=0 				type=0x02 pol=0x00 freq=0x00c8 minlevel=0x05    								i2caddr=0x58 cmd=0xaa 
[   29.768991] [drm] intel_lvds_init: the CoreClock is 200
[   29.769050] [drm] intel_lvds_init: sku_value is 0x00800000
[   29.769056] [drm] intel_lvds_init: sku_bMaxResEnableInt is 0
[   29.771681] [drm] intel_lvds_set_backlight: the level is 100
[   29.771692] [drm] LVDSGetPWMMaxBacklight: the max_pwm_blc is 31250.
[   29.873633] [drm] unable to read EDID block.
[   29.993379] usbcore: deregistering interface driver usbhid
[   29.999033] usbcore: deregistering interface driver hiddev
[   30.028602] [drm] unable to read EDID block.
[   30.038106] fujitsu_usb_touchscreen: fujitsu_touchscreen::probing::device found::[Fujitsu Component USB Touch Panel][usb-0000:00:1d.0-2/input0]
[   30.038221] input: Fujitsu Component USB Touch Panel as /devices/pci0000:00/0000:00:1d.0/usb2/2-2/2-2:1.0/input/input12
[   30.054816] fujitsu_usb_touchscreen: fujitsu_touchscreen::loaded::min-max values::x[64,3870] y[304,3960]
[   30.054884] usbcore: registered new interface driver usb_u810_tablet
[   30.054893] fujitsu_usb_touchscreen: v0.3.4:Fujitsu usb touchscreen driver for u810, p1620
[   30.105544] usbcore: registered new interface driver hiddev
[   30.105602] usbcore: registered new interface driver usbhid
[   30.105612] usbhid: v2.6:USB HID core driver
[   30.181555] [drm] unable to read EDID block.
[   30.236168] [drm] LVDS: no EDID data from device, reading ACPI _DDC data.
[   30.236219] psb 0000:00:02.0: LVDS: EDID invalid.
[   30.236265] [drm] intel_sdvo_init: sku_value is 0x00800000
[   30.236274] [drm] intel_sdvo_init: sku_bSDVOEnable is 1
[   30.681047] [drm] intel_sdvo_init: sku_value is 0x00800000
[   30.681054] [drm] intel_sdvo_init: sku_bSDVOEnable is 1
[   30.784602] [drm] unable to read EDID block.
[   30.936604] [drm] unable to read EDID block.
[   31.088604] [drm] unable to read EDID block.
[   31.140163] [drm] LVDS: no EDID data from device, reading ACPI _DDC data.
[   31.140204] psb 0000:00:02.0: LVDS: EDID invalid.
[   31.635863] detear is disabled
[   31.678742] Console: switching to colour frame buffer device 160x50
[   31.678792] [drm] intel_lvds_prepare
[   31.678799] [drm] intel_lvds_set_power: 0
[   31.678805] [drm] intel_lvds_set_backlight: the level is 0
[   31.678813] [drm] LVDSGetPWMMaxBacklight: the max_pwm_blc is 31250.
[   32.010112] [drm] LVDS: set mode 1280x800 7
[   32.010177] [drm] intel_lvds_commit
[   32.010181] [drm] intel_lvds_set_power: 1
[   32.101625] eth0: link down
[   32.102180] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   34.931470] [drm] intel_lvds_set_backlight: the level is 100
[   34.931478] [drm] LVDSGetPWMMaxBacklight: the max_pwm_blc is 31250.
[   34.931493] [drm] fb0: psbfb frame buffer device
[   34.931505] [drm] intel_lvds_prepare
[   34.931509] [drm] intel_lvds_set_power: 0
[   34.931512] [drm] intel_lvds_set_backlight: the level is 0
[   34.931517] [drm] LVDSGetPWMMaxBacklight: the max_pwm_blc is 31250.
[   34.992183] [drm] LVDS: set mode 1280x800 5
[   34.992247] [drm] intel_lvds_commit
[   34.992251] [drm] intel_lvds_set_power: 1
[   37.938988] [drm] intel_lvds_set_backlight: the level is 100
[   37.938996] [drm] LVDSGetPWMMaxBacklight: the max_pwm_blc is 31250.
[   37.972375] [drm] Initialized psb 4.40.0 20090319 on minor 0
[   37.984849] buffer underrun 0x0
[   37.997669] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   46.441000] [drm] intel_lvds_prepare
[   46.441014] [drm] intel_lvds_set_power: 0
[   46.441018] [drm] intel_lvds_set_backlight: the level is 0
[   46.441024] [drm] LVDSGetPWMMaxBacklight: the max_pwm_blc is 31250.
[   46.521786] [drm] LVDS: set mode 1280x800 7
[   46.521846] [drm] intel_lvds_commit
[   46.521849] [drm] intel_lvds_set_power: 1
[   49.467811] [drm] intel_lvds_set_backlight: the level is 100
[   49.467817] [drm] LVDSGetPWMMaxBacklight: the max_pwm_blc is 31250.
[   49.467827] [drm] intel_lvds_dpms: the mode is 0
[   49.467831] [drm] intel_lvds_set_power: 1
[   49.467835] [drm] intel_lvds_set_backlight: the level is 100
[   49.467839] [drm] LVDSGetPWMMaxBacklight: the max_pwm_blc is 31250.
[   49.662692] [drm] intel_lvds_prepare
[   49.662700] [drm] intel_lvds_set_power: 0
[   49.662704] [drm] intel_lvds_set_backlight: the level is 0
[   49.662709] [drm] LVDSGetPWMMaxBacklight: the max_pwm_blc is 31250.
[   49.743441] [drm] LVDS: set mode 1280x800 7
[   49.743501] [drm] intel_lvds_commit
[   49.743504] [drm] intel_lvds_set_power: 1
[   52.675833] [drm] intel_lvds_set_backlight: the level is 100
[   52.675839] [drm] LVDSGetPWMMaxBacklight: the max_pwm_blc is 31250.
[   66.910426] hda-intel: Invalid position buffer, using LPIB read method instead.
[  104.447713] hda-intel: IRQ timing workaround is activated for card #0. Suggest a bigger bdl_pos_adj.
[  125.390427] wlan0: authenticate with AP 00:17:9a:65:fb:e5
[  125.588068] wlan0: authenticate with AP 00:17:9a:65:fb:e5
[  125.789098] wlan0: authenticate with AP 00:17:9a:65:fb:e5
[  125.989086] wlan0: authentication with AP 00:17:9a:65:fb:e5 timed out
[  138.272548] wlan0: authenticate with AP 00:17:9a:65:fb:e5
[  138.282911] wlan0: authenticate with AP 00:17:9a:65:fb:e5
[  138.480049] wlan0: authenticate with AP 00:17:9a:65:fb:e5
[  138.680668] wlan0: authenticate with AP 00:17:9a:65:fb:e5
[  138.888064] wlan0: authentication with AP 00:17:9a:65:fb:e5 timed out
[  151.433446] wlan0: authenticate with AP 00:17:9a:65:fb:e5
[  151.443253] wlan0: authenticate with AP 00:17:9a:65:fb:e5
[  151.641025] wlan0: authenticate with AP 00:17:9a:65:fb:e5
[  151.841025] wlan0: authenticate with AP 00:17:9a:65:fb:e5
[  152.041024] wlan0: authentication with AP 00:17:9a:65:fb:e5 timed out
[  164.505642] wlan0: authenticate with AP 00:17:9a:65:fb:e5
[  164.515402] wlan0: authenticate with AP 00:17:9a:65:fb:e5
[  164.712100] wlan0: authenticate with AP 00:17:9a:65:fb:e5
[  164.912121] wlan0: authenticate with AP 00:17:9a:65:fb:e5
[  165.112104] wlan0: authentication with AP 00:17:9a:65:fb:e5 timed out
[  177.589868] wlan0: authenticate with AP 00:17:9a:65:fb:e5
[  177.596916] wlan0: authenticated
[  177.596935] wlan0: associate with AP 00:17:9a:65:fb:e5
[  177.599068] wlan0: RX AssocResp from 00:17:9a:65:fb:e5 (capab=0x431 status=0 aid=3)
[  177.599077] wlan0: associated
[  177.611352] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  187.920042] wlan0: no IPv6 routers present
[  223.333814] wlan0: disassociating by local choice (reason=3)


Help appreciated.

---

### Post by Anfanglir on 2009-06-24
bump for visibility

/ Anfanglir

---

### Post by Anfanglir on 2009-07-13
matrix at the umpc portal forum has solved the gps issue on the u820, see this thread:

[http://www.umpcportal.com/modules/newbb/viewtopic.php?topic_id=5545&forum=16](http://www.umpcportal.com/modules/newbb/viewtopic.php?topic_id=5545&forum=16)

/ Anfanglir

---

