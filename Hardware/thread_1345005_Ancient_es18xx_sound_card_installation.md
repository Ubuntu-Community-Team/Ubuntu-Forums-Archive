---
title: "Ancient es18xx sound card installation"
date: 2009-12-03
forum: Hardware
---

### Post by afrodeity on 2009-12-03
I need some help getting this card working for a friend who is migrating to ubuntu on old hardware. This is what we have to deal with in the "developing world".

here is the dmesg
```

[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.24-19-generic (buildd@palmer) (gcc version 4.2.3 (Ubuntu 4.2.3-2ubuntu7)) #1 SMP Wed Jun 18 14:43:41 UTC 2008 (Ubuntu 2.6.24-19.34-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 0000000000f00000 (usable)
[    0.000000]  BIOS-e820: 0000000000f00000 - 0000000001000000 (reserved)
[    0.000000]  BIOS-e820: 0000000001000000 - 0000000010000000 (usable)
[    0.000000]  BIOS-e820: 00000000ffff0000 - 0000000100000000 (reserved)
[    0.000000] 0MB HIGHMEM available.
[    0.000000] 256MB LOWMEM available.
[    0.000000] Entering add_active_range(0, 0, 65536) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->    65536
[    0.000000]   HighMem     65536 ->    65536
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->    65536
[    0.000000] On node 0 totalpages: 65536
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 480 pages used for memmap
[    0.000000]   Normal zone: 60960 pages, LIFO batch:15
[    0.000000]   HighMem zone: 0 pages used for memmap
[    0.000000]   Movable zone: 0 pages used for memmap
[    0.000000] DMI 2.2 present.
[    0.000000] Allocating PCI resources starting at 20000000 (gap: 10000000:efff0000)
[    0.000000] swsusp: Registered nosave memory region: 000000000009f000 - 00000000000a0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000a0000 - 00000000000f0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000f0000 - 0000000000100000
[    0.000000] swsusp: Registered nosave memory region: 0000000000f00000 - 0000000001000000
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 65024
[    0.000000] Kernel command line: root=UUID=79c7bd94-ad2c-4e36-b492-3479b1ecefcf ro quiet splash acpi=off
[    0.000000] Local APIC disabled by BIOS -- you can enable it with "lapic"
[    0.000000] mapped APIC to ffffb000 (0120c000)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 1024 (order: 10, 4096 bytes)
[    0.000000] Detected 467.776 MHz processor.
[   24.351974] Console: colour VGA+ 80x25
[   24.352001] console [tty0] enabled
[   24.353106] Dentry cache hash table entries: 32768 (order: 5, 131072 bytes)
[   24.354454] Inode-cache hash table entries: 16384 (order: 4, 65536 bytes)
[   24.407823] Memory: 247024k/262144k available (2177k kernel code, 13708k reserved, 1006k data, 368k init, 0k highmem)
[   24.407862] virtual kernel memory layout:
[   24.407867]     fixmap  : 0xfff4b000 - 0xfffff000   ( 720 kB)
[   24.407874]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   24.407880]     vmalloc : 0xd0800000 - 0xff7fe000   ( 751 MB)
[   24.407886]     lowmem  : 0xc0000000 - 0xd0000000   ( 256 MB)
[   24.407892]       .init : 0xc0421000 - 0xc047d000   ( 368 kB)
[   24.407898]       .data : 0xc0320434 - 0xc041bdc4   (1006 kB)
[   24.407904]       .text : 0xc0100000 - 0xc0320434   (2177 kB)
[   24.407919] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   24.408112] SLUB: Genslabs=11, HWalign=32, Order=0-1, MinObjects=4, CPUs=1, Nodes=1
[   24.488177] Calibrating delay using timer specific routine.. 937.20 BogoMIPS (lpj=1874406)
[   24.488337] Security Framework initialized
[   24.488397] SELinux:  Disabled at boot.
[   24.488473] AppArmor: AppArmor initialized
[   24.488495] Failure registering capabilities with primary security module.
[   24.488539] Mount-cache hash table entries: 512
[   24.489296] Initializing cgroup subsys ns
[   24.489332] Initializing cgroup subsys cpuacct
[   24.489388] CPU: After generic identify, caps: 0183f9ff 00000000 00000000 00000000 00000000 00000000 00000000 00000000
[   24.489441] CPU: L1 I cache: 16K, L1 D cache: 16K
[   24.489452] CPU: L2 cache: 128K
[   24.489472] CPU: After all inits, caps: 0183f9ff 00000000 00000000 00000040 00000000 00000000 00000000 00000000
[   24.489534] Compat vDSO mapped to ffffe000.
[   24.489618] Checking 'hlt' instruction... OK.
[   24.504389] SMP alternatives: switching to UP code
[   24.510152] Freeing SMP alternatives: 11k freed
[   24.510962] Early unpacking initramfs... done
[   26.288735] CPU0: Intel Celeron (Mendocino) stepping 05
[   26.288787] SMP motherboard not detected.
[   26.288800] Local APIC not detected. Using dummy APIC emulation.
[   26.289135] Brought up 1 CPUs
[   26.289277] CPU0 attaching sched-domain:
[   26.289295]  domain 0: span 01
[   26.289304]   groups: 01
[   26.290841] net_namespace: 64 bytes
[   26.290899] Booting paravirtualized kernel on bare hardware
[   26.293949] Time:  0:11:12  Date: 11/20/09
[   26.294200] NET: Registered protocol family 16
[   26.296403] EISA bus registered
[   26.331579] PCI: PCI BIOS revision 2.10 entry at 0xfb020, last bus=1
[   26.331598] PCI: Using configuration type 1
[   26.331668] Setting up standard PCI resources
[   26.348320] ACPI: Interpreter disabled.
[   26.348354] Linux Plug and Play Support v0.97 (c) Adam Belay
[   26.348690] pnp: PnP ACPI: disabled
[   26.348713] PnPBIOS: Scanning system for PnP BIOS support...
[   26.349275] PnPBIOS: Found PnP BIOS installation structure at 0xc00fbc90
[   26.349296] PnPBIOS: PnP BIOS version 1.0, entry 0xf0000:0xbcb8, dseg 0xf0000
[   26.359587] PnPBIOS: 16 nodes reported by PnP BIOS; 16 recorded by driver
[   26.362108] PCI: Probing PCI hardware
[   26.362132] PCI: Probing PCI hardware (bus 00)
[   26.363160] PCI quirk: region 6000-607f claimed by vt82c686 HW-mon
[   26.363177] PCI quirk: region 5000-500f claimed by vt82c686 SMB
[   26.368757] PCI: Using IRQ router VIA [1106/0686] at 0000:00:07.0
[   26.400099] NET: Registered protocol family 8
[   26.400118] NET: Registered protocol family 20
[   26.400841] AppArmor: AppArmor Filesystem Enabled
[   26.401335] system 00:07: iomem range 0x0-0x9ffff could not be reserved
[   26.401357] system 00:07: iomem range 0xfffe0000-0xffffffff could not be reserved
[   26.401372] system 00:07: iomem range 0x100000-0xfffffff could not be reserved
[   26.401417] system 00:08: iomem range 0xf0000-0xf3fff could not be reserved
[   26.401431] system 00:08: iomem range 0xf4000-0xf7fff could not be reserved
[   26.401444] system 00:08: iomem range 0xf8000-0xfffff could not be reserved
[   26.401457] system 00:08: iomem range 0xcc000-0xcffff has been reserved
[   26.401498] system 00:0b: ioport range 0x208-0x20f has been reserved
[   26.404050] Time: tsc clocksource has been installed.
[   26.405701] PCI: Bridge: 0000:00:01.0
[   26.405716]   IO window: disabled.
[   26.405737]   MEM window: d4000000-d5ffffff
[   26.405750]   PREFETCH window: 20000000-200fffff
[   26.405804] PCI: Setting latency timer of device 0000:00:01.0 to 64
[   26.405899] NET: Registered protocol family 2
[   26.444595] IP route cache hash table entries: 2048 (order: 1, 8192 bytes)
[   26.445871] TCP established hash table entries: 8192 (order: 4, 65536 bytes)
[   26.446606] TCP bind hash table entries: 8192 (order: 4, 65536 bytes)
[   26.447301] TCP: Hash tables configured (established 8192 bind 8192)
[   26.447317] TCP reno registered
[   26.457176] checking if image is initramfs... it is
[   29.592634] Freeing initrd memory: 7313k freed
[   29.597288] audit: initializing netlink socket (disabled)
[   29.597395] audit(1258675875.192:1): initialized
[   29.616336] VFS: Disk quotas dquot_6.5.1
[   29.617114] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   29.618894] io scheduler noop registered
[   29.618918] io scheduler anticipatory registered
[   29.618927] io scheduler deadline registered
[   29.619062] io scheduler cfq registered (default)
[   29.619142] PCI: VIA PCI bridge detected. Disabling DAC.
[   29.619156] PCI: Disabling Via external APIC routing
[   29.619232] Boot video device is 0000:01:00.0
[   29.621496] isapnp: Scanning for PnP cards...
[   29.720707] isapnp: Card 'ESS ES1869 Plug and Play AudioDrive'
[   29.720727] isapnp: 1 Plug & Play card detected total
[   30.174896] Real Time Clock Driver v1.12ac
[   30.175615] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   30.176460] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   30.177678] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[   30.183187] 00:0d: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   30.185836] 00:0e: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[   30.193616] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   30.194212] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[   30.195183] PNP: PS/2 Controller [PNP0303,PNP0f13] at 0x60,0x64 irq 1,12
[   30.196515] serio: i8042 KBD port at 0x60,0x64 irq 1
[   30.196553] serio: i8042 AUX port at 0x60,0x64 irq 12
[   30.208535] mice: PS/2 mouse device common for all mice
[   30.209721] EISA: Probing bus 0 at eisa.0
[   30.209792] Cannot allocate resource for EISA slot 5
[   30.209802] Cannot allocate resource for EISA slot 6
[   30.209827] EISA: Detected 0 cards.
[   30.209844] cpuidle: using governor ladder
[   30.209854] cpuidle: using governor menu
[   30.211026] NET: Registered protocol family 1
[   30.211253] Using IPI No-Shortcut mode
[   30.211470] registered taskstats version 1
[   30.211999]   Magic number: 1:147:153
[   30.212159]   hash matches device ttyp7
[   30.212359] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[   30.212369] EDD information not available.
[   30.215695] Freeing unused kernel memory: 368k freed
[   30.236613] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[   32.948663] fuse init (API version 7.9)
[   33.158166] thermal: Unknown symbol acpi_processor_set_thermal_limit
[   35.741123] SCSI subsystem initialized
[   36.096540] usbcore: registered new interface driver usbfs
[   36.096673] usbcore: registered new interface driver hub
[   36.215653] usbcore: registered new device driver usb
[   36.281450] 8139too Fast Ethernet driver 0.9.28
[   36.281829] PCI: setting IRQ 11 as level-triggered
[   36.281844] PCI: Found IRQ 11 for device 0000:00:0f.0
[   36.283573] eth0: RealTek RTL8139 at 0xe800, 00:1d:0f:c2:85:c0, IRQ 11
[   36.283587] eth0:  Identified 8139 chip type 'RTL-8100B/8139D'
[   36.803271] Floppy drive(s): fd0 is 1.44M
[   36.823259] FDC 0 is a post-1991 82077
[   36.870373] USB Universal Host Controller Interface driver v3.0
[   36.870931] PCI: setting IRQ 10 as level-triggered
[   36.870948] PCI: Found IRQ 10 for device 0000:00:07.2
[   36.870985] PCI: Sharing IRQ 10 with 0000:00:07.3
[   36.871054] uhci_hcd 0000:00:07.2: UHCI Host Controller
[   36.872715] uhci_hcd 0000:00:07.2: new USB bus registered, assigned bus number 1
[   36.872823] uhci_hcd 0000:00:07.2: irq 10, io base 0x0000d400
[   36.873660] usb usb1: configuration #1 chosen from 1 choice
[   36.873815] hub 1-0:1.0: USB hub found
[   36.873857] hub 1-0:1.0: 2 ports detected
[   36.917903] libata version 3.00 loaded.
[   36.932671] 8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)
[   36.975949] PCI: Found IRQ 10 for device 0000:00:07.3
[   36.975999] PCI: Sharing IRQ 10 with 0000:00:07.2
[   36.976070] uhci_hcd 0000:00:07.3: UHCI Host Controller
[   36.976267] uhci_hcd 0000:00:07.3: new USB bus registered, assigned bus number 2
[   36.976351] uhci_hcd 0000:00:07.3: irq 10, io base 0x0000d800
[   36.977050] usb usb2: configuration #1 chosen from 1 choice
[   36.977185] hub 2-0:1.0: USB hub found
[   36.977227] hub 2-0:1.0: 2 ports detected
[   37.160799] pata_via 0000:00:07.1: version 0.3.3
[   37.168508] scsi0 : pata_via
[   37.172336] scsi1 : pata_via
[   37.172749] ata1: PATA max UDMA/66 cmd 0x1f0 ctl 0x3f6 bmdma 0xd000 irq 14
[   37.172765] ata2: PATA max UDMA/66 cmd 0x170 ctl 0x376 bmdma 0xd008 irq 15
[   37.492966] ata1.00: ATA-6: WDC WD800JB-00ETA0, 77.07W77, max UDMA/100
[   37.492996] ata1.00: 156301488 sectors, multi 0: LBA48 
[   37.493110] ata1.01: ATAPI: ATAPI CDROM, V140M, max UDMA/33
[   37.493168] ata1.00: limited to UDMA/33 due to 40-wire cable
[   37.508867] ata1.00: configured for UDMA/33
[   37.671821] ata1.01: configured for UDMA/33
[   37.839459] scsi 0:0:0:0: Direct-Access     ATA      WDC WD800JB-00ET 77.0 PQ: 0 ANSI: 5
[   37.840451] scsi 0:0:1:0: CD-ROM                     ATAPI CDROM      140M PQ: 0 ANSI: 5
[   41.494063] Driver 'sd' needs updating - please use bus_type methods
[   41.505415] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors (80026 MB)
[   41.505517] sd 0:0:0:0: [sda] Write Protect is off
[   41.505532] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   41.505644] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   41.506000] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors (80026 MB)
[   41.506067] sd 0:0:0:0: [sda] Write Protect is off
[   41.506080] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   41.506181] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   41.506218]  sda: sda1 sda2 <<4>Driver 'sr' needs updating - please use bus_type methods
[   41.562891]  sda5 >
[   41.563486] sd 0:0:0:0: [sda] Attached SCSI disk
[   41.603252] sr0: scsi3-mmc drive: 0x/0x cd/rw xa/form2 cdda tray
[   41.603293] Uniform CD-ROM driver Revision: 3.20
[   41.603639] sr 0:0:1:0: Attached scsi CD-ROM sr0
[   41.632535] sd 0:0:0:0: Attached scsi generic sg0 type 0
[   41.632640] sr 0:0:1:0: Attached scsi generic sg1 type 5
[   42.403417] Attempting manual resume
[   42.403445] swsusp: Resume From Partition 8:5
[   42.403453] PM: Checking swsusp image.
[   42.404253] PM: Resume from disk failed.
[   42.570884] kjournald starting.  Commit interval 5 seconds
[   42.570997] EXT3-fs: mounted filesystem with ordered data mode.
[   60.158003] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   60.397690] Linux agpgart interface v0.102
[   60.519793] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   60.685730] parport_pc: VIA 686A/8231 detected
[   60.685760] parport_pc: probing current configuration
[   60.685798] parport_pc: Current parallel port base: 0x378
[   60.685897] parport0: PC-style at 0x378, irq 7 [PCSPP,EPP]
[   60.798200] input: PC Speaker as /devices/platform/pcspkr/input/input2
[   60.821638] parport_pc: VIA parallel port: io=0x378, irq=7
[   60.891399] agpgart: Detected VIA Apollo Pro 133 chipset
[   60.902357] agpgart: AGP aperture is 64M @ 0xd0000000
[   62.269814] input: ImPS/2 Generic Wheel Mouse as /devices/platform/i8042/serio1/input/input3
[   65.345858] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[   68.429516] NET: Registered protocol family 10
[   68.430810] lo: Disabled Privacy Extensions
[   68.711642] ns558 01:01.02: activated
[   68.782808] gameport: NS558 PnP Gameport is pnp01:01.02/gameport0, io 0x201, speed 497kHz
[   70.915415] ALSA /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-generic/sound/alsa-driver/isa/../alsa-kernel/isa/es18xx.c:208: dsp_get_byte failed: 0x22a = 0xaa!!!
[   70.915460] ALSA /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-generic/sound/alsa-driver/isa/../alsa-kernel/isa/es18xx.c:1635: es18xx: [0x220] ESS chip not found
[   70.921004] es18xx-pnpbios 01:01.01: activated
[   70.923407] es18xx-pnpbios 01:01.01: disabled
[   70.923442] es18xx-pnpbios: probe of 01:01.01 failed with error -2
[   70.926208] es18xx 01:01.00: activated
[   70.928779] es18xx 01:01.01: activated
[   70.932804] ALSA /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-generic/sound/alsa-driver/isa/../alsa-kernel/isa/es18xx.c:208: dsp_get_byte failed: 0x22a = 0xaa!!!
[   70.932837] ALSA /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-generic/sound/alsa-driver/isa/../alsa-kernel/isa/es18xx.c:1635: es18xx: [0x220] ESS chip not found
[   70.935307] es18xx 01:01.00: disabled
[   70.937711] es18xx 01:01.01: disabled
[   73.002145] PCI: Found IRQ 10 for device 0000:00:07.5
[   73.002409] PCI: Setting latency timer of device 0000:00:07.5 to 64
[   78.483750] eth0: no IPv6 routers present
[   80.405066] lp0: using parport0 (interrupt-driven).
[   80.961930] Adding 738948k swap on /dev/sda5.  Priority:-1 extents:1 across:738948k
[   81.720175] EXT3 FS on sda1, internal journal
[   85.411431] ip_tables: (C) 2000-2006 Netfilter Core Team
[   86.405364] PPP generic driver version 2.4.2
[   86.466346] NET: Registered protocol family 17
[   89.758223] acpi_cpufreq: Unknown symbol acpi_processor_notify_smm
[   89.759120] acpi_cpufreq: Unknown symbol acpi_processor_unregister_performance
[   89.760772] acpi_cpufreq: Unknown symbol acpi_processor_preregister_performance
[   89.761587] acpi_cpufreq: Unknown symbol acpi_processor_register_performance
[   91.838117] NET: Registered protocol family 24
[   93.135799] apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac)
[   93.673512] ppdev: user-space parallel port driver
[   93.889810] audit(1258675939.950:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=4624 profile="/usr/sbin/cupsd" namespace="default"
[   97.451824] Bluetooth: Core ver 2.11
[   97.456086] NET: Registered protocol family 31
[   97.456119] Bluetooth: HCI device and connection manager initialized
[   97.456141] Bluetooth: HCI socket layer initialized
[   97.626289] Bluetooth: L2CAP ver 2.9
[   97.626324] Bluetooth: L2CAP socket layer initialized
[   97.818375] Bluetooth: RFCOMM socket layer initialized
[   97.819906] Bluetooth: RFCOMM TTY layer initialized
[   97.819950] Bluetooth: RFCOMM ver 1.8

```

Here is lshw
```

[   24.489452] CPU: L2 cache: 128K
[   24.489472] CPU: After all inits, caps: 0183f9ff 00000000 00000000 00000040 00000000 00000000 00000000 00000000
[   24.489534] Compat vDSO mapped to ffffe000.
[   24.489618] Checking 'hlt' instruction... OK.
[   24.504389] SMP alternatives: switching to UP code
[   24.510152] Freeing SMP alternatives: 11k freed
[   24.510962] Early unpacking initramfs... done
[   26.288735] CPU0: Intel Celeron (Mendocino) stepping 05
[   26.288787] SMP motherboard not detected.
[   26.288800] Local APIC not detected. Using dummy APIC emulation.
[   26.289135] Brought up 1 CPUs
[   26.289277] CPU0 attaching sched-domain:
[   26.289295]  domain 0: span 01
[   26.289304]   groups: 01
[   26.290841] net_namespace: 64 bytes
[   26.290899] Booting paravirtualized kernel on bare hardware
[   26.293949] Time:  0:11:12  Date: 11/20/09
[   26.294200] NET: Registered protocol family 16
[   26.296403] EISA bus registered
[   26.331579] PCI: PCI BIOS revision 2.10 entry at 0xfb020, last bus=1
[   26.331598] PCI: Using configuration type 1
[   26.331668] Setting up standard PCI resources
[   26.348320] ACPI: Interpreter disabled.
[   26.348354] Linux Plug and Play Support v0.97 (c) Adam Belay
[   26.348690] pnp: PnP ACPI: disabled
[   26.348713] PnPBIOS: Scanning system for PnP BIOS support...
[   26.349275] PnPBIOS: Found PnP BIOS installation structure at 0xc00fbc90
[   26.349296] PnPBIOS: PnP BIOS version 1.0, entry 0xf0000:0xbcb8, dseg 0xf0000
[   26.359587] PnPBIOS: 16 nodes reported by PnP BIOS; 16 recorded by driver
[   26.362108] PCI: Probing PCI hardware
[   26.362132] PCI: Probing PCI hardware (bus 00)
[   26.363160] PCI quirk: region 6000-607f claimed by vt82c686 HW-mon
[   26.363177] PCI quirk: region 5000-500f claimed by vt82c686 SMB
[   26.368757] PCI: Using IRQ router VIA [1106/0686] at 0000:00:07.0
[   26.400099] NET: Registered protocol family 8
[   26.400118] NET: Registered protocol family 20
[   26.400841] AppArmor: AppArmor Filesystem Enabled
[   26.401335] system 00:07: iomem range 0x0-0x9ffff could not be reserved
[   26.401357] system 00:07: iomem range 0xfffe0000-0xffffffff could not be reserved
[   26.401372] system 00:07: iomem range 0x100000-0xfffffff could not be reserved
[   26.401417] system 00:08: iomem range 0xf0000-0xf3fff could not be reserved
[   26.401431] system 00:08: iomem range 0xf4000-0xf7fff could not be reserved
[   26.401444] system 00:08: iomem range 0xf8000-0xfffff could not be reserved
[   26.401457] system 00:08: iomem range 0xcc000-0xcffff has been reserved
[   26.401498] system 00:0b: ioport range 0x208-0x20f has been reserved
[   26.404050] Time: tsc clocksource has been installed.
[   26.405701] PCI: Bridge: 0000:00:01.0
[   26.405716]   IO window: disabled.
[   26.405737]   MEM window: d4000000-d5ffffff
[   26.405750]   PREFETCH window: 20000000-200fffff
[   26.405804] PCI: Setting latency timer of device 0000:00:01.0 to 64
[   26.405899] NET: Registered protocol family 2
[   26.444595] IP route cache hash table entries: 2048 (order: 1, 8192 bytes)
[   26.445871] TCP established hash table entries: 8192 (order: 4, 65536 bytes)
[   26.446606] TCP bind hash table entries: 8192 (order: 4, 65536 bytes)
[   26.447301] TCP: Hash tables configured (established 8192 bind 8192)
[   26.447317] TCP reno registered
[   26.457176] checking if image is initramfs... it is
[   29.592634] Freeing initrd memory: 7313k freed
[   29.597288] audit: initializing netlink socket (disabled)
[   29.597395] audit(1258675875.192:1): initialized
[   29.616336] VFS: Disk quotas dquot_6.5.1
[   29.617114] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   29.618894] io scheduler noop registered
[   29.618918] io scheduler anticipatory registered
[   29.618927] io scheduler deadline registered
[   29.619062] io scheduler cfq registered (default)
[   29.619142] PCI: VIA PCI bridge detected. Disabling DAC.
[   29.619156] PCI: Disabling Via external APIC routing
[   29.619232] Boot video device is 0000:01:00.0
[   29.621496] isapnp: Scanning for PnP cards...
[   29.720707] isapnp: Card 'ESS ES1869 Plug and Play AudioDrive'
[   29.720727] isapnp: 1 Plug & Play card detected total
[   30.174896] Real Time Clock Driver v1.12ac
[   30.175615] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   30.176460] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   30.177678] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[   30.183187] 00:0d: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   30.185836] 00:0e: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[   30.193616] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   30.194212] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[   30.195183] PNP: PS/2 Controller [PNP0303,PNP0f13] at 0x60,0x64 irq 1,12
[   30.196515] serio: i8042 KBD port at 0x60,0x64 irq 1
[   30.196553] serio: i8042 AUX port at 0x60,0x64 irq 12
[   30.208535] mice: PS/2 mouse device common for all mice
[   30.209721] EISA: Probing bus 0 at eisa.0
[   30.209792] Cannot allocate resource for EISA slot 5
[   30.209802] Cannot allocate resource for EISA slot 6
[   30.209827] EISA: Detected 0 cards.
[   30.209844] cpuidle: using governor ladder
[   30.209854] cpuidle: using governor menu
[   30.211026] NET: Registered protocol family 1
[   30.211253] Using IPI No-Shortcut mode
[   30.211470] registered taskstats version 1
[   30.211999]   Magic number: 1:147:153
[   30.212159]   hash matches device ttyp7
[   30.212359] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[   30.212369] EDD information not available.
[   30.215695] Freeing unused kernel memory: 368k freed
[   30.236613] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[   32.948663] fuse init (API version 7.9)
[   33.158166] thermal: Unknown symbol acpi_processor_set_thermal_limit
[   35.741123] SCSI subsystem initialized
[   36.096540] usbcore: registered new interface driver usbfs
[   36.096673] usbcore: registered new interface driver hub
[   36.215653] usbcore: registered new device driver usb
[   36.281450] 8139too Fast Ethernet driver 0.9.28
[   36.281829] PCI: setting IRQ 11 as level-triggered
[   36.281844] PCI: Found IRQ 11 for device 0000:00:0f.0
[   36.283573] eth0: RealTek RTL8139 at 0xe800, 00:1d:0f:c2:85:c0, IRQ 11
[   36.283587] eth0:  Identified 8139 chip type 'RTL-8100B/8139D'
[   36.803271] Floppy drive(s): fd0 is 1.44M
[   36.823259] FDC 0 is a post-1991 82077
[   36.870373] USB Universal Host Controller Interface driver v3.0
[   36.870931] PCI: setting IRQ 10 as level-triggered
[   36.870948] PCI: Found IRQ 10 for device 0000:00:07.2
[   36.870985] PCI: Sharing IRQ 10 with 0000:00:07.3
[   36.871054] uhci_hcd 0000:00:07.2: UHCI Host Controller
[   36.872715] uhci_hcd 0000:00:07.2: new USB bus registered, assigned bus number 1
[   36.872823] uhci_hcd 0000:00:07.2: irq 10, io base 0x0000d400
[   36.873660] usb usb1: configuration #1 chosen from 1 choice
[   36.873815] hub 1-0:1.0: USB hub found
[   36.873857] hub 1-0:1.0: 2 ports detected
[   36.917903] libata version 3.00 loaded.
[   36.932671] 8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)
[   36.975949] PCI: Found IRQ 10 for device 0000:00:07.3
[   36.975999] PCI: Sharing IRQ 10 with 0000:00:07.2
[   36.976070] uhci_hcd 0000:00:07.3: UHCI Host Controller
[   36.976267] uhci_hcd 0000:00:07.3: new USB bus registered, assigned bus number 2
[   36.976351] uhci_hcd 0000:00:07.3: irq 10, io base 0x0000d800
[   36.977050] usb usb2: configuration #1 chosen from 1 choice
[   36.977185] hub 2-0:1.0: USB hub found
[   36.977227] hub 2-0:1.0: 2 ports detected
[   37.160799] pata_via 0000:00:07.1: version 0.3.3
[   37.168508] scsi0 : pata_via
[   37.172336] scsi1 : pata_via
[   37.172749] ata1: PATA max UDMA/66 cmd 0x1f0 ctl 0x3f6 bmdma 0xd000 irq 14
[   37.172765] ata2: PATA max UDMA/66 cmd 0x170 ctl 0x376 bmdma 0xd008 irq 15
[   37.492966] ata1.00: ATA-6: WDC WD800JB-00ETA0, 77.07W77, max UDMA/100
[   37.492996] ata1.00: 156301488 sectors, multi 0: LBA48 
[   37.493110] ata1.01: ATAPI: ATAPI CDROM, V140M, max UDMA/33
[   37.493168] ata1.00: limited to UDMA/33 due to 40-wire cable
[   37.508867] ata1.00: configured for UDMA/33
[   37.671821] ata1.01: configured for UDMA/33
[   37.839459] scsi 0:0:0:0: Direct-Access     ATA      WDC WD800JB-00ET 77.0 PQ: 0 ANSI: 5
[   37.840451] scsi 0:0:1:0: CD-ROM                     ATAPI CDROM      140M PQ: 0 ANSI: 5
[   41.494063] Driver 'sd' needs updating - please use bus_type methods
[   41.505415] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors (80026 MB)
[   41.505517] sd 0:0:0:0: [sda] Write Protect is off
[   41.505532] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   41.505644] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   41.506000] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors (80026 MB)
[   41.506067] sd 0:0:0:0: [sda] Write Protect is off
[   41.506080] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   41.506181] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   41.506218]  sda: sda1 sda2 <<4>Driver 'sr' needs updating - please use bus_type methods
[   41.562891]  sda5 >
[   41.563486] sd 0:0:0:0: [sda] Attached SCSI disk
[   41.603252] sr0: scsi3-mmc drive: 0x/0x cd/rw xa/form2 cdda tray
[   41.603293] Uniform CD-ROM driver Revision: 3.20
[   41.603639] sr 0:0:1:0: Attached scsi CD-ROM sr0
[   41.632535] sd 0:0:0:0: Attached scsi generic sg0 type 0
[   41.632640] sr 0:0:1:0: Attached scsi generic sg1 type 5
[   42.403417] Attempting manual resume
[   42.403445] swsusp: Resume From Partition 8:5
[   42.403453] PM: Checking swsusp image.
[   42.404253] PM: Resume from disk failed.
[   42.570884] kjournald starting.  Commit interval 5 seconds
[   42.570997] EXT3-fs: mounted filesystem with ordered data mode.
[   60.158003] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   60.397690] Linux agpgart interface v0.102
[   60.519793] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   60.685730] parport_pc: VIA 686A/8231 detected
[   60.685760] parport_pc: probing current configuration
[   60.685798] parport_pc: Current parallel port base: 0x378
[   60.685897] parport0: PC-style at 0x378, irq 7 [PCSPP,EPP]
[   60.798200] input: PC Speaker as /devices/platform/pcspkr/input/input2
[   60.821638] parport_pc: VIA parallel port: io=0x378, irq=7
[   60.891399] agpgart: Detected VIA Apollo Pro 133 chipset
[   60.902357] agpgart: AGP aperture is 64M @ 0xd0000000
[   62.269814] input: ImPS/2 Generic Wheel Mouse as /devices/platform/i8042/serio1/input/input3
[   65.345858] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[   68.429516] NET: Registered protocol family 10
[   68.430810] lo: Disabled Privacy Extensions
[   68.711642] ns558 01:01.02: activated
[   68.782808] gameport: NS558 PnP Gameport is pnp01:01.02/gameport0, io 0x201, speed 497kHz
[   70.915415] ALSA /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-generic/sound/alsa-driver/isa/../alsa-kernel/isa/es18xx.c:208: dsp_get_byte failed: 0x22a = 0xaa!!!
[   70.915460] ALSA /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-generic/sound/alsa-driver/isa/../alsa-kernel/isa/es18xx.c:1635: es18xx: [0x220] ESS chip not found
[   70.921004] es18xx-pnpbios 01:01.01: activated
[   70.923407] es18xx-pnpbios 01:01.01: disabled
[   70.923442] es18xx-pnpbios: probe of 01:01.01 failed with error -2
[   70.926208] es18xx 01:01.00: activated
[   70.928779] es18xx 01:01.01: activated
[   70.932804] ALSA /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-generic/sound/alsa-driver/isa/../alsa-kernel/isa/es18xx.c:208: dsp_get_byte failed: 0x22a = 0xaa!!!
[   70.932837] ALSA /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-generic/sound/alsa-driver/isa/../alsa-kernel/isa/es18xx.c:1635: es18xx: [0x220] ESS chip not found
[   70.935307] es18xx 01:01.00: disabled
[   70.937711] es18xx 01:01.01: disabled
[   73.002145] PCI: Found IRQ 10 for device 0000:00:07.5
[   73.002409] PCI: Setting latency timer of device 0000:00:07.5 to 64
[   78.483750] eth0: no IPv6 routers present
[   80.405066] lp0: using parport0 (interrupt-driven).
[   80.961930] Adding 738948k swap on /dev/sda5.  Priority:-1 extents:1 across:738948k
[   81.720175] EXT3 FS on sda1, internal journal
[   85.411431] ip_tables: (C) 2000-2006 Netfilter Core Team
[   86.405364] PPP generic driver version 2.4.2
[   86.466346] NET: Registered protocol family 17
[   89.758223] acpi_cpufreq: Unknown symbol acpi_processor_notify_smm
[   89.759120] acpi_cpufreq: Unknown symbol acpi_processor_unregister_performance
[   89.760772] acpi_cpufreq: Unknown symbol acpi_processor_preregister_performance
[   89.761587] acpi_cpufreq: Unknown symbol acpi_processor_register_performance
[   91.838117] NET: Registered protocol family 24
[   93.135799] apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac)
[   93.673512] ppdev: user-space parallel port driver
[   93.889810] audit(1258675939.950:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=4624 profile="/usr/sbin/cupsd" namespace="default"
[   97.451824] Bluetooth: Core ver 2.11
[   97.456086] NET: Registered protocol family 31
[   97.456119] Bluetooth: HCI device and connection manager initialized
[   97.456141] Bluetooth: HCI socket layer initialized
[   97.626289] Bluetooth: L2CAP ver 2.9
[   97.626324] Bluetooth: L2CAP socket layer initialized
[   97.818375] Bluetooth: RFCOMM socket layer initialized
[   97.819906] Bluetooth: RFCOMM TTY layer initialized
[   97.819950] Bluetooth: RFCOMM ver 1.8
shiva@woodstock-desktop:~$ 
shiva@woodstock-desktop:~$ lshw
WARNING: you should run this program as super-user.
qCI (sysfs)  
shiva@woodstock-desktop:~$ sudo lshw
woodstock-desktop         
    description: Desktop Computer
    product: VT82C692BX
    vendor: VIA Technologies, Inc.
    width: 32 bits
    capabilities: smbios-2.2 dmi-2.2
    configuration: boot=normal chassis=desktop
  *-core
       description: Motherboard
       product: 693-686A
       physical id: 0
     *-firmware
          description: BIOS
          vendor: Award Software International, Inc.
          physical id: 0
          version: 6.00 PG (02/18/2000)
          size: 128KiB
          capacity: 192KiB
          capabilities: isa pci pnp apm upgrade shadowing escd cdboot bootselect socketedrom edd int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb agp ls120boot zipboot biosbootspecification
     *-cpu
          description: CPU
          product: Celeron (Mendocino)
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: 6.6.5
          slot: SLOT 1
          size: 466MHz
          capacity: 500MHz
          width: 32 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 sep mtrr pge mca cmov pat pse36 mmx fxsr up
        *-cache:0
             description: L1 cache
             physical id: a
             slot: Internal Cache
             size: 32KiB
             capacity: 32KiB
             capabilities: synchronous internal write-back
        *-cache:1
             description: L2 cache
             physical id: b
             slot: External Cache
             size: 128KiB
             capacity: 2MiB
             capabilities: synchronous external write-back
     *-memory
          description: System Memory
          physical id: 1f
          slot: System board or motherboard
          size: 256MiB
          capacity: 512MiB
        *-bank:0
             description: DIMM EDRAM
             physical id: 0
             slot: BANK_0
             size: 128MiB
        *-bank:1
             description: DIMM EDRAM
             physical id: 1
             slot: BANK_1
             size: 128MiB
        *-bank:2
             description: DIMM EDRAM [empty]
             physical id: 2
             slot: BANK_2
        *-bank:3
             description: DIMM EDRAM [empty]
             physical id: 3
             slot: BANK_3
     *-pci:0
          description: Host bridge
          product: VT82C693A/694x [Apollo PRO133x]
          vendor: VIA Technologies, Inc.
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 44
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-via module=via_agp
        *-pci
             description: PCI bridge
             product: VT82C598/694x [Apollo MVP3/Pro133x AGP]
             vendor: VIA Technologies, Inc.
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pci pm normal_decode bus_master cap_list
           *-display UNCLAIMED
                description: VGA compatible controller
                product: 3DImage 9750
                vendor: Trident Microsystems
                physical id: 0
                bus info: pci@0000:01:00.0
                version: f3
                width: 32 bits
                clock: 66MHz
                capabilities: vga_controller bus_master
                configuration: latency=32
        *-isa
             description: ISA bridge
             product: VT82C686 [Apollo Super South]
             vendor: VIA Technologies, Inc.
             physical id: 7
             bus info: pci@0000:00:07.0
             version: 1b
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master
             configuration: driver=parport_pc latency=0 module=parport_pc
        *-ide
             description: IDE interface
             product: VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE
             vendor: VIA Technologies, Inc.
             physical id: 7.1
             bus info: pci@0000:00:07.1
             logical name: scsi0
             version: 06
             width: 32 bits
             clock: 33MHz
             capabilities: ide pm bus_master cap_list emulated
             configuration: driver=pata_via latency=32 module=pata_via
           *-disk
                description: ATA Disk
                product: WDC WD800JB-00ET
                vendor: Western Digital
                physical id: 0.0.0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: 77.0
                serial: WD-WMAHL1328654
                size: 74GiB (80GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=80cb80cb
              *-volume:0
                   description: EXT3 volume
                   vendor: Linux
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   logical name: /
                   logical name: /dev/.static/dev
                   version: 1.0
                   serial: 79c7bd94-ad2c-4e36-b492-3479b1ecefcf
                   size: 73GiB
                   capacity: 73GiB
                   capabilities: primary bootable journaled extended_attributes large_files huge_files recover ext3 ext2 initialized
                   configuration: created=2009-07-23 20:08:10 filesystem=ext3 modified=2009-11-20 02:12:07 mount.fstype=ext3 mount.options=rw,relatime,errors=remount-ro,data=ordered mounted=2009-11-20 02:12:07 state=mounted
              *-volume:1
                   description: Extended partition
                   physical id: 2
                   bus info: scsi@0:0.0.0,2
                   logical name: /dev/sda2
                   size: 721MiB
                   capacity: 721MiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume
                      description: Linux swap / Solaris partition
                      physical id: 5
                      logical name: /dev/sda5
                      capacity: 721MiB
                      capabilities: nofs
           *-cdrom
                description: SCSI CD-ROM
                product: ATAPI CDROM
                physical id: 0.1.0
                bus info: scsi@0:0.1.0
                logical name: /dev/cdrom
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: 140M
                capabilities: removable audio
                configuration: ansiversion=5 status=open
        *-usb:0
             description: USB Controller
             product: VT82xxxxx UHCI USB 1.1 Controller
             vendor: VIA Technologies, Inc.
             physical id: 7.2
             bus info: pci@0000:00:07.2
             version: 0e
             width: 32 bits
             clock: 33MHz
             capabilities: pm uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=32 module=uhci_hcd
        *-usb:1
             description: USB Controller
             product: VT82xxxxx UHCI USB 1.1 Controller
             vendor: VIA Technologies, Inc.
             physical id: 7.3
             bus info: pci@0000:00:07.3
             version: 0e
             width: 32 bits
             clock: 33MHz
             capabilities: pm uhci bus_master cap_list
             configuration: driver=uhci_hcd latency=32 module=uhci_hcd
        *-multimedia
             description: Multimedia audio controller
             product: VT82C686 AC97 Audio Controller
             vendor: VIA Technologies, Inc.
             physical id: 7.5
             bus info: pci@0000:00:07.5
             version: 21
             width: 32 bits
             clock: 33MHz
             capabilities: pm cap_list
             configuration: driver=VIA 82xx Audio latency=0 module=snd_via82xx
        *-network
             description: Ethernet interface
             product: RTL-8139/8139C/8139C+
             vendor: Realtek Semiconductor Co., Ltd.
             physical id: f
             bus info: pci@0000:00:0f.0
             logical name: eth0
             version: 10
             serial: 00:1d:0f:c2:85:c0
             size: 100MB/s
             capacity: 100MB/s
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
             configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full latency=32 link=yes maxlatency=64 mingnt=32 module=8139too multicast=yes port=MII speed=100MB/s
     *-pci:1
          description: Host bridge
          product: VT82C686 [Apollo Super ACPI]
          vendor: VIA Technologies, Inc.
          physical id: 101
          bus info: pci@0000:00:07.4
          version: 20
          width: 32 bits
          clock: 33MHz

```

/etc/modprobe.d/alsa-base

```

alias char-major-116 snd
alias snd-card-1 snd-es18xx
options snd-es18xx index=0 enable=1 isapnp=0 port=0x220 mpu_port=0x388 fm_port=$

alias char-major-14 soundcore
alias sound-slot-0 snd-card-0

alias sound-service-0-0 snd-mixer-oss
alias sound-service-0-1 snd-seq-oss
alias sound-service-0-3 snd-pcm-oss
alias sound-service-0-8 snd-seq-oss
alias sound-service-0-12 snd-pcm-oss

# autoloader aliases
install sound-slot-0 /sbin/modprobe snd-card-0
install sound-slot-1 /sbin/modprobe snd-card-1
install sound-slot-2 /sbin/modprobe snd-card-2
install sound-slot-3 /sbin/modprobe snd-card-3
install sound-slot-4 /sbin/modprobe snd-card-4

```

I have tried to troubleshoot it myself using these postings

[http://ubuntuforums.org/showthread.php?t=148077&highlight=es1869+no+sound](http://ubuntuforums.org/showthread.php?t=148077&highlight=es1869+no+sound)

[http://ubuntuforums.org/showthread.php?p=7964770](http://ubuntuforums.org/showthread.php?p=7964770)

but bios really old, and I'm not good at old agp ports. Anybody have any idea what the options/ports should be in /etc/modprobe.d/alsa-base? Clearly they the wrong ones. When I boot up I see the card at 1 1 1,3 what does this mean?

---

### Post by crusty420 on 2009-12-04
I have an old soundblaster ISA card with that similiar chipset, It was a huge pain to get it recognized under kubuntu 7.10, I haven't tried it with the new distro, but I had to manually configure every single port and DMA the card used. However in winblows they had drivers and everything was configured itself. I can't remember how I done it because it's been so long ago, I do remember having like 10-12 different tech pages open trying to figure out it. I do remember that I had to use OSS instead of ALSA for some reason. However I have a PCI soundblaster in this one and it get auto-configured in 9.10 which is a nice relief.

---

### Post by afrodeity on 2009-12-06
That't the thing, configuring the ports. Don't know how to go about this. It's a real pain in the @#$%.

---

### Post by FactTech on 2010-01-05
You might take a look at:

[http://ubuntuforums.org/showthread.php?t=1370672&highlight=es1869](http://ubuntuforums.org/showthread.php?t=1370672&highlight=es1869)

I just got an ES1869 working fine on CrunchBang Lite 8.10 -- the same information may apply.

---

### Post by afrodeity on 2010-01-09
Thanks facttech, at least now I can see what's going on with pnputils.

 lspnp -v doesn't show me the card, so there must be something wrong. I'll have to try cleaning the contacts or something.

---

