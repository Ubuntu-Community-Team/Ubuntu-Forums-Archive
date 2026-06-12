---
title: "problem shutting down acer 1310 aspire"
date: 2008-02-11
forum: Hardware &amp; Laptops
---

### Post by harys on 2008-02-11
Iget this message when i turn on my laptop. the problem is that it won't shutdown down automatically.
where should i look to fix it in the acpi?

Starting up...
[    0.000000] ACPI: BIOS age (208) fails cutoff (2000), acpi=force is required to enable ACPI
[    8.454556] PnPBIOS: dev_node_info: function not supported on this system
[    8.454618] PnPBIOS: Unable to get node info.  Aborting.
[    8.456391] PCI: Cannot allocate resource region 0 of device 0000:00:0a.0
Loading please wait...

**this is the result of the dmesg on my laptop**

harys@harys-laps-top:~$ dmesg
[    0.000000] Linux version 2.6.22-14-generic (buildd@terranova) (gcc version 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)) #1 SMP Fri Feb 1 04:59:50 UTC 2008 (Ubuntu 2.6.22-14.51-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000001dff0000 (usable)
[    0.000000]  BIOS-e820: 000000001dff0000 - 000000001dffffc0 (ACPI data)
[    0.000000]  BIOS-e820: 000000001dffffc0 - 000000001e000000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000fff80000 - 0000000100000000 (reserved)
[    0.000000] 0MB HIGHMEM available.
[    0.000000] 479MB LOWMEM available.
[    0.000000] Entering add_active_range(0, 0, 122864) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   122864
[    0.000000]   HighMem    122864 ->   122864
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   122864
[    0.000000] On node 0 totalpages: 122864
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 927 pages used for memmap
[    0.000000]   Normal zone: 117841 pages, LIFO batch:31
[    0.000000]   HighMem zone: 0 pages used for memmap
[    0.000000] DMI 2.3 present.
[    0.000000] ACPI: RSDP signature @ 0xC00E5010 checksum 0
[    0.000000] ACPI: RSDP 000E5010, 0014 (r0 OID_00)
[    0.000000] ACPI: RSDT 1DFFFBC0, 0030 (r1 INSYDE RSDT_000        1 _CSI    10101)
[    0.000000] ACPI: FACP 1DFFFAC0, 0074 (r1 INSYDE FACP_000      100 _CSI    10101)
[    0.000000] ACPI: DSDT 1DFFC6F0, 33C4 (r1 INSYDE    KN266     1000 MSFT  100000E)
[    0.000000] ACPI: FACS 1DFFFFC0, 0040
[    0.000000] ACPI: BOOT 1DFFFB50, 0028 (r1 INSYDE SYS_BOOT      100 _CSI    10101)
[    0.000000] ACPI: DBGP 1DFFFB80, 0034 (r1 INSYDE DBGP_000      100 _CSI    10101)
[    0.000000] ACPI: BIOS age (208) fails cutoff (2000), acpi=force is required to enable ACPI
[    0.000000] ACPI: Disabling ACPI support
[    0.000000] Allocating PCI resources starting at 20000000 (gap: 1e000000:e1f80000)
[    0.000000] Built 1 zonelists.  Total pages: 121905
[    0.000000] Kernel command line: root=UUID=242b21a9-4d15-4845-9531-ab0fc9619985 ro quiet splash
[    0.000000] Local APIC disabled by BIOS -- you can enable it with "lapic"
[    0.000000] mapped APIC to ffffd000 (013cd000)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 2048 (order: 11, 8192 bytes)
[    0.000000] Detected 1658.549 MHz processor.
[    7.927869] Console: colour VGA+ 80x25
[    7.928443] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
[    7.928888] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
[    7.951749] Memory: 475660k/491456k available (2015k kernel code, 15180k reserved, 916k data, 364k init, 0k highmem)
[    7.951763] virtual kernel memory layout:
[    7.951764]     fixmap  : 0xfff4d000 - 0xfffff000   ( 712 kB)
[    7.951766]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[    7.951767]     vmalloc : 0xde800000 - 0xff7fe000   ( 527 MB)
[    7.951769]     lowmem  : 0xc0000000 - 0xddff0000   ( 479 MB)
[    7.951770]       .init : 0xc03e3000 - 0xc043e000   ( 364 kB)
[    7.951772]       .data : 0xc02f7e66 - 0xc03dce84   ( 916 kB)
[    7.951773]       .text : 0xc0100000 - 0xc02f7e66   (2015 kB)
[    7.951778] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[    7.951844] SLUB: Genslabs=22, HWalign=32, Order=0-1, MinObjects=4, CPUs=1, Nodes=1
[    8.031832] Calibrating delay using timer specific routine.. 3321.72 BogoMIPS (lpj=6643442)
[    8.031884] Security Framework v1.0.0 initialized
[    8.031897] SELinux:  Disabled at boot.
[    8.031923] Mount-cache hash table entries: 512
[    8.032172] CPU: After generic identify, caps: 0183f9ff c1cbf9ff 00000000 00000000 00000000 00000000 00000000
[    8.032181] Enabling disabled K7/SSE Support.
[    8.032187] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[    8.032191] CPU: L2 Cache: 256K (64 bytes/line)
[    8.032195] CPU: After all inits, caps: 0383f9ff c1cbf9ff 00000000 00000420 00000000 00000000 00000000
[    8.032211] Compat vDSO mapped to ffffe000.
[    8.032233] Checking 'hlt' instruction... OK.
[    8.048021] SMP alternatives: switching to UP code
[    8.048406] Freeing SMP alternatives: 11k freed
[    8.049076] Early unpacking initramfs... done
[    8.451373] CPU0: AMD Athlon(tm) XP 2000+ stepping 01
[    8.451385] SMP motherboard not detected.
[    8.451390] Local APIC not detected. Using dummy APIC emulation.
[    8.451478] Brought up 1 CPUs
[    8.451783] Booting paravirtualized kernel on bare hardware
[    8.451923] Time: 19:32:29  Date: 01/09/108
[    8.451992] NET: Registered protocol family 16
[    8.452181] EISA bus registered
[    8.452304] PCI: PCI BIOS revision 2.10 entry at 0xe8a04, last bus=1
[    8.452308] PCI: Using configuration type 1
[    8.452310] Setting up standard PCI resources
[    8.454364] ACPI: Interpreter disabled.
[    8.454372] Linux Plug and Play Support v0.97 (c) Adam Belay
[    8.454389] pnp: PnP ACPI: disabled
[    8.454394] PnPBIOS: Scanning system for PnP BIOS support...
[    8.454541] PnPBIOS: Found PnP BIOS installation structure at 0xc00ff020
[    8.454546] PnPBIOS: PnP BIOS version 1.0, entry 0xea000:0x40a2, dseg 0xea000
[    8.454556] PnPBIOS: dev_node_info: function not supported on this system
[    8.454618] PnPBIOS: Unable to get node info.  Aborting.
[    8.454749] PCI: Probing PCI hardware
[    8.454757] PCI: Probing PCI hardware (bus 00)
[    8.455186] PCI quirk: region 1000-107f claimed by vt8235 PM
[    8.455190] PCI quirk: region 1400-140f claimed by vt8235 SMB
[    8.456333] PCI: Using IRQ router VIA [1106/3177] at 0000:00:11.0
[    8.456351] PCI: setting IRQ 10 as level-triggered
[    8.456356] PCI: Found IRQ 10 for device 0000:00:10.1
[    8.456391] PCI: Cannot allocate resource region 0 of device 0000:00:0a.0
[    8.457963] NET: Registered protocol family 8
[    8.457966] NET: Registered protocol family 20
[    8.458523] PCI: Bridge: 0000:00:01.0
[    8.458527]   IO window: c000-dfff
[    8.458532]   MEM window: e0000000-efffffff
[    8.458537]   PREFETCH window: a0000000-afffffff
[    8.458542] PCI: Bus 2, cardbus bridge: 0000:00:0a.0
[    8.458545]   IO window: 00001800-000018ff
[    8.458549]   IO window: 00001c00-00001cff
[    8.458554]   PREFETCH window: 20000000-23ffffff
[    8.458558]   MEM window: 24000000-27ffffff
[    8.458579] PCI: Setting latency timer of device 0000:00:01.0 to 64
[    8.458594] PCI: setting IRQ 11 as level-triggered
[    8.458598] PCI: Found IRQ 11 for device 0000:00:0a.0
[    8.458608] PCI: Sharing IRQ 11 with 0000:00:10.3
[    8.458633] NET: Registered protocol family 2
[    8.459575] Time: tsc clocksource has been installed.
[    8.487670] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
[    8.487772] TCP established hash table entries: 16384 (order: 5, 196608 bytes)
[    8.488351] TCP bind hash table entries: 16384 (order: 5, 131072 bytes)
[    8.488802] TCP: Hash tables configured (established 16384 bind 16384)
[    8.488806] TCP reno registered
[    8.499844] checking if image is initramfs... it is
[    9.299282] Freeing initrd memory: 7057k freed
[    9.299602] Simple Boot Flag at 0x37 set to 0x1
[    9.300121] audit: initializing netlink socket (disabled)
[    9.300160] audit(1202585550.012:1): initialized
[    9.302759] VFS: Disk quotas dquot_6.5.1
[    9.302859] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    9.303130] io scheduler noop registered
[    9.303133] io scheduler anticipatory registered
[    9.303136] io scheduler deadline registered
[    9.303153] io scheduler cfq registered (default)
[    9.303179] PCI: VIA PCI bridge detected. Disabling DAC.
[    9.303240] Boot video device is 0000:01:00.0
[    9.303508] isapnp: Scanning for PnP cards...
[    9.657187] isapnp: No Plug & Play device found
[    9.708385] Real Time Clock Driver v1.12ac
[    9.708498] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[    9.710706] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[    9.711210] input: Macintosh mouse button emulation as /class/input/input0
[    9.711361] PNP: No PS/2 controller found. Probing ports directly.
[    9.727151] i8042.c: Detected active multiplexing controller, rev 1.1.
[    9.737822] serio: i8042 KBD port at 0x60,0x64 irq 1
[    9.737833] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[    9.737837] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[    9.737840] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[    9.737843] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[    9.738239] mice: PS/2 mouse device common for all mice
[    9.739151] EISA: Probing bus 0 at eisa.0
[    9.739166] Cannot allocate resource for EISA slot 1
[    9.739198] EISA: Detected 0 cards.
[    9.739407] TCP cubic registered
[    9.739421] NET: Registered protocol family 1
[    9.739454] Using IPI No-Shortcut mode
[    9.739619]   Magic number: 12:144:546
[    9.739931]   hash matches device null
[    9.740808] Freeing unused kernel memory: 364k freed
[    9.908131] input: AT Translated Set 2 keyboard as /class/input/input1
[   11.047808] AppArmor: AppArmor initialized<5>audit(1202585552.012:2):  type=1505 info="AppArmor initialized" pid=1116
[   11.059869] fuse init (API version 7.8)
[   11.067026] Failure registering capabilities with primary security module.
[   11.118716] thermal: Unknown symbol acpi_processor_set_thermal_limit
[   11.944861] PCI: setting IRQ 5 as level-triggered
[   11.944870] PCI: Found IRQ 5 for device 0000:00:0c.0
[   11.944889] PCI: Sharing IRQ 5 with 0000:00:11.5
[   11.944893] PCI: Sharing IRQ 5 with 0000:00:11.6
[   11.994980] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[5]  MMIO=[f0000000-f00007ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[   12.023208] usbcore: registered new interface driver usbfs
[   12.023260] usbcore: registered new interface driver hub
[   12.023295] usbcore: registered new device driver usb
[   12.024640] USB Universal Host Controller Interface driver v3.0
[   12.024785] PCI: Found IRQ 11 for device 0000:00:10.0
[   12.024807] PCI: Sharing IRQ 11 with 0000:00:12.0
[   12.024811] PCI: Sharing IRQ 11 with 0000:01:00.0
[   12.024828] uhci_hcd 0000:00:10.0: UHCI Host Controller
[   12.025110] uhci_hcd 0000:00:10.0: new USB bus registered, assigned bus number 1
[   12.025146] uhci_hcd 0000:00:10.0: irq 11, io base 0x00001200
[   12.025477] usb usb1: configuration #1 chosen from 1 choice
[   12.025528] hub 1-0:1.0: USB hub found
[   12.025543] hub 1-0:1.0: 2 ports detected
[   12.076704] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[   12.076718] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[   12.107149] via-rhine.c:v1.10-LK1.4.3 2007-03-06 Written by Donald Becker
[   12.129649] PCI: Found IRQ 10 for device 0000:00:10.1
[   12.129680] PCI: VIA VLink IRQ fixup for 0000:00:10.1, from 255 to 10
[   12.129712] uhci_hcd 0000:00:10.1: UHCI Host Controller
[   12.129753] uhci_hcd 0000:00:10.1: new USB bus registered, assigned bus number 2
[   12.129786] uhci_hcd 0000:00:10.1: irq 10, io base 0x00001300
[   12.129929] usb usb2: configuration #1 chosen from 1 choice
[   12.129980] hub 2-0:1.0: USB hub found
[   12.129994] hub 2-0:1.0: 2 ports detected
[   12.235008] PCI: Found IRQ 11 for device 0000:00:10.3
[   12.235022] PCI: Sharing IRQ 11 with 0000:00:0a.0
[   12.235058] ehci_hcd 0000:00:10.3: EHCI Host Controller
[   12.235570] ehci_hcd 0000:00:10.3: new USB bus registered, assigned bus number 3
[   12.235648] ehci_hcd 0000:00:10.3: irq 11, io mem 0xf0008000
[   12.235656] ehci_hcd 0000:00:10.3: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   12.236168] usb usb3: configuration #1 chosen from 1 choice
[   12.236356] hub 3-0:1.0: USB hub found
[   12.236368] hub 3-0:1.0: 4 ports detected
[   12.338076] VP_IDE: IDE controller at PCI slot 0000:00:11.1
[   12.338112] VP_IDE: chipset revision 6
[   12.338116] VP_IDE: not 100% native mode: will probe irqs later
[   12.338130] VP_IDE: VIA vt8235 (rev 00) IDE UDMA133 controller on pci0000:00:11.1
[   12.338142]     ide0: BM-DMA at 0x1100-0x1107, BIOS settings: hda:DMA, hdb:pio
[   12.338157]     ide1: BM-DMA at 0x1108-0x110f, BIOS settings: hdc:DMA, hdd:pio
[   12.338168] Probing IDE interface ide0...
[   12.753020] hda: HITACHI_DK23EA-40, ATA DISK drive
[   13.264796] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[00c09f00000ac8db]
[   13.424717] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[   13.425196] Probing IDE interface ide1...
[   14.288073] hdc: QSI CD-RW/DVD-ROM SBW-242, ATAPI CD/DVD-ROM drive
[   14.959838] ide1 at 0x170-0x177,0x376 on irq 15
[   14.970286] SCSI subsystem initialized
[   14.978466] libata version 2.21 loaded.
[   14.981837] PCI: Found IRQ 11 for device 0000:00:12.0
[   14.981854] PCI: Sharing IRQ 11 with 0000:00:10.0
[   14.981868] PCI: Sharing IRQ 11 with 0000:01:00.0
[   14.986531] eth0: VIA Rhine II at 0x1e200, 00:c0:9f:25:45:1c, IRQ 11.
[   14.987253] eth0: MII PHY found at address 1, status 0x7809 advertising 01e1 Link 0000.
[   15.000698] hda: max request size: 128KiB
[   15.013803] hda: 78140160 sectors (40007 MB) w/2048KiB Cache, CHS=65535/16/63, UDMA(33)
[   15.014001] hda: cache flushes supported
[   15.014101]  hda: hda1 hda2 hda3 < hda5 >
[   15.094041] hdc: ATAPI 24X DVD-ROM CD-R/RW drive, 2048kB Cache, UDMA(33)
[   15.094057] Uniform CD-ROM driver Revision: 3.20
[   15.361536] Attempting manual resume
[   15.361543] swsusp: Resume From Partition 3:5
[   15.361546] PM: Checking swsusp image.
[   15.361989] PM: Resume from disk failed.
[   15.415329] kjournald starting.  Commit interval 5 seconds
[   15.415352] EXT3-fs: mounted filesystem with ordered data mode.
[   29.028037] Linux agpgart interface v0.102 (c) Dave Jones
[   29.035505] agpgart: Detected VIA Apollo Pro266 chipset
[   29.046430] agpgart: AGP aperture is 128M @ 0xb0000000
[   29.193227] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   29.212674] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   29.298009] Yenta: CardBus bridge found at 0000:00:0a.0 [10cf:10e7]
[   29.298035] Yenta O2: res at 0x94/0xD4: 00/ea
[   29.298038] Yenta O2: enabling read prefetch/write burst
[   29.423409] Yenta: ISA IRQ mask 0x0098, PCI irq 11
[   29.423417] Socket status: 30000007
[   29.586603] irda_init()
[   29.586646] NET: Registered protocol family 23
[   29.688216] input: PS/2 Mouse as /class/input/input2
[   29.714856] input: AlpsPS/2 ALPS GlidePoint as /class/input/input3
[   30.025288] PCI: Found IRQ 5 for device 0000:00:11.6
[   30.025303] PCI: Sharing IRQ 5 with 0000:00:0c.0
[   30.025314] PCI: Sharing IRQ 5 with 0000:00:11.5
[   30.312099] cs: IO port probe 0x100-0x3af: excluding 0x378-0x37f
[   30.313827] cs: IO port probe 0x3e0-0x4ff: excluding 0x4d0-0x4d7
[   30.314630] cs: IO port probe 0x820-0x8ff: clean.
[   30.315243] cs: IO port probe 0xc00-0xcf7: clean.
[   30.316028] cs: IO port probe 0xa00-0xaff: clean.
[   30.773782] PCI: Setting latency timer of device 0000:00:11.6 to 64
[   31.381447] MC'97 0 converters and GPIO not ready (0x1)
[   31.383913] PCI: Found IRQ 5 for device 0000:00:11.5
[   31.383926] PCI: Sharing IRQ 5 with 0000:00:0c.0
[   31.383939] PCI: Sharing IRQ 5 with 0000:00:11.6
[   31.384085] PCI: Setting latency timer of device 0000:00:11.5 to 64
[   32.700553] parport0: PC-style at 0x378 [PCSPP]
[   32.803363] lp0: using parport0 (polling).
[   32.921351] Adding 835340k swap on /dev/hda5.  Priority:-1 extents:1 across:835340k
[   33.275832] EXT3 FS on hda2, internal journal
[   35.633614] powernow_k7: Unknown symbol acpi_processor_notify_smm
[   35.633667] powernow_k7: Unknown symbol acpi_processor_unregister_performance
[   35.633766] powernow_k7: Unknown symbol acpi_processor_register_performance
[   35.670489] acpi_cpufreq: Unknown symbol acpi_processor_notify_smm
[   35.670543] acpi_cpufreq: Unknown symbol acpi_processor_unregister_performance
[   35.670656] acpi_cpufreq: Unknown symbol acpi_processor_preregister_performance
[   35.670715] acpi_cpufreq: Unknown symbol acpi_processor_register_performance
[   37.232561] eth0: link down
[   38.152296] ppdev: user-space parallel port driver
[   38.523259] audit(1202581979.974:3):  type=1503 operation="inode_permission" requested_mask="a" denied_mask="a" name="/dev/tty" pid=4202 profile="/usr/sbin/cupsd"
[   42.483410] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[   43.212987] Failure registering capabilities with primary security module.
[   43.658611] Bluetooth: Core ver 2.11
[   43.658808] NET: Registered protocol family 31
[   43.658811] Bluetooth: HCI device and connection manager initialized
[   43.658817] Bluetooth: HCI socket layer initialized
[   43.689580] Bluetooth: L2CAP ver 2.8
[   43.689589] Bluetooth: L2CAP socket layer initialized
[   43.896002] Bluetooth: RFCOMM socket layer initialized
[   43.896129] Bluetooth: RFCOMM TTY layer initialized
[   43.896132] Bluetooth: RFCOMM ver 1.8
[   47.598175] [drm] Initialized drm 1.1.0 20060810
[   47.618661] PCI: Found IRQ 11 for device 0000:01:00.0
[   47.618677] PCI: Sharing IRQ 11 with 0000:00:10.0
[   47.618689] PCI: Sharing IRQ 11 with 0000:00:12.0
[   47.623103] [drm] Initialized savage 2.4.1 20050313 on minor 0
[   47.623594] mtrr: base(0xaa000000) is not aligned on a size(0x5000000) boundary
[   47.624054] agpgart: Found an AGP 2.0 compliant device at 0000:00:00.0.
[   47.624079] agpgart: Putting AGP V2 device at 0000:00:00.0 into 0x mode
[   47.624135] agpgart: Putting AGP V2 device at 0000:01:00.0 into 0x mode
harys@harys-laps-top:~$ 

Thanks for your help.

harys

---

