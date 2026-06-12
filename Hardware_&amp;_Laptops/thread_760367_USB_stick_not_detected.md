---
title: "USB stick not detected"
date: 2008-04-20
forum: Hardware &amp; Laptops
---

### Post by thesergeant on 2008-04-20
Hi all,

Yes I am new to Ubuntu, I am just beginning to find my way around it.

I have installed Gutsy Gibbon and installed all the updates etc. Most things are working fine. 

However I have found that the system does not detect my 4gb USB memory stick.

It detects a powered MP3 drive absolutely fine. However I have a unpowered Memory card reader and that isn't detected either

I have read other similar threads without solving my problem - any suggestions ??

dmesg output 

Plugged in 

[    0.000000] Linux version 2.6.22-14-generic (buildd@terranova) (gcc version 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)) #1 SMP Tue Feb 12 07:42:25 UTC 2008 (Ubuntu 2.6.22-14.52-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000001fff0000 (usable)
[    0.000000]  BIOS-e820: 000000001fff0000 - 000000001fff8000 (ACPI data)
[    0.000000]  BIOS-e820: 000000001fff8000 - 0000000020000000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fff80000 - 0000000100000000 (reserved)
[    0.000000] 0MB HIGHMEM available.
[    0.000000] 511MB LOWMEM available.
[    0.000000] Entering add_active_range(0, 0, 131056) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   131056
[    0.000000]   HighMem    131056 ->   131056
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   131056
[    0.000000] On node 0 totalpages: 131056
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 991 pages used for memmap
[    0.000000]   Normal zone: 125969 pages, LIFO batch:31
[    0.000000]   HighMem zone: 0 pages used for memmap
[    0.000000] DMI 2.3 present.
[    0.000000] ACPI: RSDP signature @ 0xC00FA790 checksum 0
[    0.000000] ACPI: RSDP 000FA790, 0014 (r0 AMI   )
[    0.000000] ACPI: RSDT 1FFF0000, 002C (r1 AMIINT VIA_K7         10 MSFT       97)
[    0.000000] ACPI: FACP 1FFF0030, 0081 (r1 AMIINT VIA_K7         11 MSFT       97)
[    0.000000] ACPI: DSDT 1FFF0120, 30AF (r1    VIA    K7VT4     1000 MSFT  100000D)
[    0.000000] ACPI: FACS 1FFF8000, 0040
[    0.000000] ACPI: APIC 1FFF00C0, 0054 (r1 AMIINT VIA_K7          9 MSFT       97)
[    0.000000] ACPI: PM-Timer IO Port: 0x808
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] Processor #0 6:8 APIC version 16
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 3, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 low level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] Allocating PCI resources starting at 30000000 (gap: 20000000:dec00000)
[    0.000000] Built 1 zonelists.  Total pages: 130033
[    0.000000] Kernel command line: root=UUID=38d4cf67-37fc-4c67-a9c9-291307d26ed2 ro quiet splash
[    0.000000] mapped APIC to ffffd000 (fee00000)
[    0.000000] mapped IOAPIC to ffffc000 (fec00000)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 2048 (order: 11, 8192 bytes)
[    0.000000] Detected 1998.506 MHz processor.
[   18.149730] Console: colour VGA+ 80x25
[   18.150159] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
[   18.150491] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
[   18.167910] Memory: 508172k/524224k available (2015k kernel code, 15420k reserved, 915k data, 364k init, 0k highmem)
[   18.167921] virtual kernel memory layout:
[   18.167922]     fixmap  : 0xfff4d000 - 0xfffff000   ( 712 kB)
[   18.167923]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   18.167925]     vmalloc : 0xe0800000 - 0xff7fe000   ( 495 MB)
[   18.167926]     lowmem  : 0xc0000000 - 0xdfff0000   ( 511 MB)
[   18.167927]       .init : 0xc03e3000 - 0xc043e000   ( 364 kB)
[   18.167929]       .data : 0xc02f7e86 - 0xc03dce84   ( 915 kB)
[   18.167930]       .text : 0xc0100000 - 0xc02f7e86   (2015 kB)
[   18.167934] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   18.167985] SLUB: Genslabs=22, HWalign=32, Order=0-1, MinObjects=4, CPUs=1, Nodes=1
[   18.247952] Calibrating delay using timer specific routine.. 4001.34 BogoMIPS (lpj=8002684)
[   18.247990] Security Framework v1.0.0 initialized
[   18.247999] SELinux:  Disabled at boot.
[   18.248018] Mount-cache hash table entries: 512
[   18.248190] CPU: After generic identify, caps: 0383fbff c1c3fbff 00000000 00000000 00000000 00000000 00000000
[   18.248201] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[   18.248204] CPU: L2 Cache: 256K (64 bytes/line)
[   18.248207] CPU: After all inits, caps: 0383fbff c1c3fbff 00000000 00000420 00000000 00000000 00000000
[   18.248220] Compat vDSO mapped to ffffe000.
[   18.248235] Checking 'hlt' instruction... OK.
[   18.264106] SMP alternatives: switching to UP code
[   18.264413] Freeing SMP alternatives: 11k freed
[   18.264840] Early unpacking initramfs... done
[   18.585386] ACPI: Core revision 20070126
[   18.585495] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[   18.587162] CPU0: AMD Athlon(tm) XP 2400+ stepping 01
[   18.587190] Total of 1 processors activated (4001.34 BogoMIPS).
[   18.587960] ENABLING IO-APIC IRQs
[   18.588289] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[   18.735643] Brought up 1 CPUs
[   18.735841] Booting paravirtualized kernel on bare hardware
[   18.735945] Time:  7:09:46  Date: 03/20/108
[   18.735980] NET: Registered protocol family 16
[   18.736114] EISA bus registered
[   18.736133] ACPI: bus type pci registered
[   18.739080] PCI: PCI BIOS revision 2.10 entry at 0xfdae1, last bus=1
[   18.739083] PCI: Using configuration type 1
[   18.739085] Setting up standard PCI resources
[   18.743183] ACPI: EC: Look up EC in DSDT
[   18.746336] ACPI: Interpreter enabled
[   18.746340] ACPI: (supports S0 S1 S4 S5)
[   18.746355] ACPI: Using IOAPIC for interrupt routing
[   18.750412] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   18.750422] PCI: Probing PCI hardware (bus 00)
[   18.750800] PCI quirk: region 0800-087f claimed by vt8235 PM
[   18.750804] PCI quirk: region 0400-040f claimed by vt8235 SMB
[   18.751065] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   18.760323] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 10 *11 12 14 15)
[   18.760409] ACPI: PCI Interrupt Link [LNKB] (IRQs *3 4 5 6 7 10 11 12 14 15)
[   18.760492] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 *10 11 12 14 15)
[   18.760573] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 *5 6 7 10 11 12 14 15)
[   18.760670] ACPI: Power Resource [URP1] (off)
[   18.760697] ACPI: Power Resource [URP2] (off)
[   18.760723] ACPI: Power Resource [FDDP] (off)
[   18.760749] ACPI: Power Resource [LPTP] (off)
[   18.760762] Linux Plug and Play Support v0.97 (c) Adam Belay
[   18.760778] pnp: PnP ACPI init
[   18.760796] ACPI: bus type pnp registered
[   18.763113] pnp: PnP ACPI: found 12 devices
[   18.763116] ACPI: ACPI bus type pnp unregistered
[   18.763121] PnPBIOS: Disabled by ACPI PNP
[   18.763189] PCI: Using ACPI for IRQ routing
[   18.763193] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   18.763208] PCI: Cannot allocate resource region 0 of device 0000:00:0a.0
[   18.765239] NET: Registered protocol family 8
[   18.765242] NET: Registered protocol family 20
[   18.765334] pnp: 00:05: iomem range 0xfec00000-0xfec00fff could not be reserved
[   18.765337] pnp: 00:05: iomem range 0xfee00000-0xfee00fff could not be reserved
[   18.767563] Time: tsc clocksource has been installed.
[   18.795670] PCI: Bridge: 0000:00:01.0
[   18.795672]   IO window: disabled.
[   18.795676]   MEM window: dde00000-dfefffff
[   18.795681]   PREFETCH window: cdd00000-ddcfffff
[   18.795699] PCI: Setting latency timer of device 0000:00:01.0 to 64
[   18.795712] NET: Registered protocol family 2
[   18.835567] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
[   18.835644] TCP established hash table entries: 16384 (order: 5, 196608 bytes)
[   18.836017] TCP bind hash table entries: 16384 (order: 5, 131072 bytes)
[   18.836285] TCP: Hash tables configured (established 16384 bind 16384)
[   18.836289] TCP reno registered
[   18.847689] checking if image is initramfs... it is
[   19.299170] Switched to high resolution mode on CPU 0
[   19.450221] Freeing initrd memory: 7050k freed
[   19.450761] audit: initializing netlink socket (disabled)
[   19.450780] audit(1208675386.996:1): initialized
[   19.452873] VFS: Disk quotas dquot_6.5.1
[   19.452936] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   19.453053] io scheduler noop registered
[   19.453056] io scheduler anticipatory registered
[   19.453058] io scheduler deadline registered
[   19.453084] io scheduler cfq registered (default)
[   19.453099] PCI: VIA PCI bridge detected. Disabling DAC.
[   19.453158] Boot video device is 0000:01:00.0
[   19.453358] isapnp: Scanning for PnP cards...
[   19.806827] isapnp: No Plug & Play device found
[   19.841540] Real Time Clock Driver v1.12ac
[   19.841658] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   19.841761] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   19.842970] 00:02: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   19.844025] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   19.844303] input: Macintosh mouse button emulation as /class/input/input0
[   19.844401] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[   19.844806] serio: i8042 KBD port at 0x60,0x64 irq 1
[   19.844812] serio: i8042 AUX port at 0x60,0x64 irq 12
[   19.844993] mice: PS/2 mouse device common for all mice
[   19.845122] EISA: Probing bus 0 at eisa.0
[   19.845160] EISA: Detected 0 cards.
[   19.845384] TCP cubic registered
[   19.845396] NET: Registered protocol family 1
[   19.845422] Using IPI No-Shortcut mode
[   19.845627]   Magic number: 4:845:167
[   19.845718]   hash matches device ttyq7
[   19.845862]   hash matches device PNP0000:00
[   19.846415] Freeing unused kernel memory: 364k freed
[   19.886786] input: AT Translated Set 2 keyboard as /class/input/input1
[   21.077442] AppArmor: AppArmor initialized<5>audit(1208675388.496:2):  type=1505 info="AppArmor initialized" pid=1176
[   21.084816] fuse init (API version 7.8)
[   21.090431] Failure registering capabilities with primary security module.
[   21.757088] usbcore: registered new interface driver usbfs
[   21.757124] usbcore: registered new interface driver hub
[   21.757152] usbcore: registered new device driver usb
[   21.768994] USB Universal Host Controller Interface driver v3.0
[   21.769114] ACPI: PCI Interrupt 0000:00:10.0[A] -> GSI 21 (level, low) -> IRQ 16
[   21.769129] uhci_hcd 0000:00:10.0: UHCI Host Controller
[   21.769374] uhci_hcd 0000:00:10.0: new USB bus registered, assigned bus number 1
[   21.769410] uhci_hcd 0000:00:10.0: irq 16, io base 0x0000e000
[   21.769597] usb usb1: configuration #1 chosen from 1 choice
[   21.769637] hub 1-0:1.0: USB hub found
[   21.769649] hub 1-0:1.0: 2 ports detected
[   21.839038] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[   21.839046] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[   21.856630] via-rhine.c:v1.10-LK1.4.3 2007-03-06 Written by Donald Becker
[   21.873322] ACPI: PCI Interrupt 0000:00:10.1[B] -> GSI 21 (level, low) -> IRQ 16
[   21.873340] uhci_hcd 0000:00:10.1: UHCI Host Controller
[   21.873373] uhci_hcd 0000:00:10.1: new USB bus registered, assigned bus number 2
[   21.873399] uhci_hcd 0000:00:10.1: irq 16, io base 0x0000e400
[   21.873525] usb usb2: configuration #1 chosen from 1 choice
[   21.873568] hub 2-0:1.0: USB hub found
[   21.873580] hub 2-0:1.0: 2 ports detected
[   21.905549] Floppy drive(s): fd0 is 1.44M
[   21.961647] FDC 0 is a post-1991 82077
[   21.977177] ACPI: PCI Interrupt 0000:00:10.2[C] -> GSI 21 (level, low) -> IRQ 16
[   21.977195] uhci_hcd 0000:00:10.2: UHCI Host Controller
[   21.977228] uhci_hcd 0000:00:10.2: new USB bus registered, assigned bus number 3
[   21.977254] uhci_hcd 0000:00:10.2: irq 16, io base 0x0000e800
[   21.977395] usb usb3: configuration #1 chosen from 1 choice
[   21.977425] hub 3-0:1.0: USB hub found
[   21.977433] hub 3-0:1.0: 2 ports detected
[   22.083275] ACPI: PCI Interrupt 0000:00:10.3[D] -> GSI 21 (level, low) -> IRQ 16
[   22.083298] ehci_hcd 0000:00:10.3: EHCI Host Controller
[   22.083359] ehci_hcd 0000:00:10.3: new USB bus registered, assigned bus number 4
[   22.083414] ehci_hcd 0000:00:10.3: irq 16, io mem 0xdffeff00
[   22.112935] usb 1-1: new full speed USB device using uhci_hcd and address 2
[   22.112959] ehci_hcd 0000:00:10.3: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   22.113128] usb usb4: configuration #1 chosen from 1 choice
[   22.113162] hub 4-0:1.0: USB hub found
[   22.113176] hub 4-0:1.0: 6 ports detected
[   22.217300] VP_IDE: IDE controller at PCI slot 0000:00:11.1
[   22.217325] ACPI: Unable to derive IRQ for device 0000:00:11.1
[   22.217327] ACPI: PCI Interrupt 0000:00:11.1[A]: no GSI
[   22.217341] VP_IDE: chipset revision 6
[   22.217344] VP_IDE: not 100% native mode: will probe irqs later
[   22.217355] VP_IDE: VIA vt8235 (rev 00) IDE UDMA133 controller on pci0000:00:11.1
[   22.217365]     ide0: BM-DMA at 0xfc00-0xfc07, BIOS settings: hda:DMA, hdb:DMA
[   22.217377]     ide1: BM-DMA at 0xfc08-0xfc0f, BIOS settings: hdc:DMA, hdd:DMA
[   22.217387] Probing IDE interface ide0...
[   22.632543] hda: IC35L060AVV207-0, ATA DISK drive
[   22.912320] hdb: SAMSUNG SP1604N, ATA DISK drive
[   22.969130] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[   22.983678] Probing IDE interface ide1...
[   23.056131] usb 4-1: new high speed USB device using ehci_hcd and address 2
[   23.191170] usb 4-1: configuration #1 chosen from 1 choice
[   23.847616] hdc: DVD-RW IDE1008, ATAPI CD/DVD-ROM drive
[   24.630986] hdd: LITE-ON COMBO LTC-48161H, ATAPI CD/DVD-ROM drive
[   24.687574] ide1 at 0x170-0x177,0x376 on irq 15
[   24.696737] SCSI subsystem initialized
[   24.703010] libata version 2.21 loaded.
[   24.705613] ACPI: PCI Interrupt 0000:00:12.0[A] -> GSI 23 (level, low) -> IRQ 17
[   24.710030] eth0: VIA Rhine II at 0x1d800, 00:0c:6e:80:19:a2, IRQ 17.
[   24.710750] eth0: MII PHY found at address 1, status 0x7849 advertising 05e1 Link 0000.
[   24.720059] hda: max request size: 512KiB
[   24.738128] hda: 78165360 sectors (40020 MB) w/1821KiB Cache, CHS=16383/255/63, UDMA(100)
[   24.738599] hda: cache flushes supported
[   24.738680]  hda: hda1 hda2 < hda5 >
[   24.766369] hdb: max request size: 512KiB
[   24.767003] hdb: 312581808 sectors (160041 MB) w/2048KiB Cache, CHS=19457/255/63, UDMA(100)
[   24.767226] hdb: cache flushes supported
[   24.767270]  hdb: hdb1
[   24.799106] hdc: ATAPI 40X DVD-ROM DVD-R CD-R/RW drive, 2048kB Cache<4>hdc: drive side 80-wire cable detection failed, limiting max speed to UDMA33
[   24.799118] 
[   24.799122] Uniform CD-ROM driver Revision: 3.20
[   24.822470] hdd: ATAPI 48X DVD-ROM CD-R/RW drive, 2048kB Cache, UDMA(33)
[   25.057035] Attempting manual resume
[   25.057041] swsusp: Resume From Partition 3:5
[   25.057043] PM: Checking swsusp image.
[   25.057237] PM: Resume from disk failed.
[   25.086201] kjournald starting.  Commit interval 5 seconds
[   25.086218] EXT3-fs: mounted filesystem with ordered data mode.
[   32.407721] Linux agpgart interface v0.102 (c) Dave Jones
[   32.427477] agpgart: Detected VIA KM400/KM400A chipset
[   32.438084] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   32.438609] agpgart: AGP aperture is 128M @ 0xe0000000
[   32.447839] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   32.664278] irda_init()
[   32.664311] NET: Registered protocol family 23
[   33.614345] input: PC Speaker as /class/input/input2
[   33.874504] p54: LM86 firmware
[   34.106248] input: PS/2 Generic Mouse as /class/input/input3
[   34.111277] parport_pc 00:03: reported by Plug and Play ACPI
[   34.111403] parport0: PC-style at 0x378 (0x778), irq 7, dma 0 [PCSPP,TRISTATE,COMPAT,EPP,ECP,DMA]
[   34.196143] ACPI: PCI Interrupt 0000:00:11.5[C] -> GSI 22 (level, low) -> IRQ 18
[   34.196300] PCI: Setting latency timer of device 0000:00:11.5 to 64
[   34.386786] ieee80211_init: failed to initialize WME (err=-17)
[   34.396078] iwlwifi_rc80211_simple: Unknown symbol iwlwifi_ieee80211_rate_control_unregister
[   34.396123] iwlwifi_rc80211_simple: Unknown symbol iwlwifi_sta_info_put
[   34.396159] iwlwifi_rc80211_simple: Unknown symbol iwlwifi_sta_info_get
[   34.396214] iwlwifi_rc80211_simple: Unknown symbol iwlwifi_ieee80211_rate_control_register
[   34.406054] wmaster0: Selected rate control algorithm 'simple'
[   34.462767] phy0: hwaddr 00:0b:6b:6c:a8:75, isl3887
[   34.462793] usbcore: registered new interface driver prism54usb
[   35.084627] lp0: using parport0 (interrupt-driven).
[   35.141136] Adding 1502036k swap on /dev/hda5.  Priority:-1 extents:1 across:1502036k
[   35.491938] EXT3 FS on hda1, internal journal
[   36.667779] No dock devices found.
[   36.821797] input: Power Button (FF) as /class/input/input4
[   36.827636] ACPI: Power Button (FF) [PWRF]
[   36.867783] input: Power Button (CM) as /class/input/input5
[   36.873550] ACPI: Power Button (CM) [PWRB]
[   36.913582] input: Sleep Button (CM) as /class/input/input6
[   36.919369] ACPI: Sleep Button (CM) [SLPB]
[   38.299497] Failure registering capabilities with primary security module.
[   38.536122] eth0: link down
[   38.668623] ppdev: user-space parallel port driver
[   38.982466] audit(1208675406.796:3):  type=1503 operation="inode_permission" requested_mask="a" denied_mask="a" name="/dev/tty" pid=4732 profile="/usr/sbin/cupsd"
[   39.033755] apm: BIOS not found.
[   39.310403] Bluetooth: Core ver 2.11
[   39.310591] NET: Registered protocol family 31
[   39.310594] Bluetooth: HCI device and connection manager initialized
[   39.310599] Bluetooth: HCI socket layer initialized
[   39.324314] Bluetooth: L2CAP ver 2.8
[   39.324321] Bluetooth: L2CAP socket layer initialized
[   39.404747] Bluetooth: RFCOMM socket layer initialized
[   39.404866] Bluetooth: RFCOMM TTY layer initialized
[   39.404869] Bluetooth: RFCOMM ver 1.8
[  101.649674] NET: Registered protocol family 17
[  102.448733] wlan1: Initial auth_alg=0
[  102.448740] wlan1: authenticate with AP 00:0e:9b:a2:d3:1d
[  102.452653] wlan1: RX authentication from 00:0e:9b:a2:d3:1d (alg=0 transaction=2 status=0)
[  102.452662] wlan1: authenticated
[  102.452666] wlan1: associate with AP 00:0e:9b:a2:d3:1d
[  102.455580] wlan1: RX AssocResp from 00:0e:9b:a2:d3:1d (capab=0x411 status=0 aid=1)
[  102.455589] wlan1: associated
[  102.455694] wlan1: WMM queue=2 aci=0 acm=0 aifs=3 cWmin=15 cWmax=1023 burst=0
[  102.455704] wlan1: WMM queue=3 aci=1 acm=0 aifs=7 cWmin=15 cWmax=1023 burst=0
[  102.455709] wlan1: WMM queue=1 aci=2 acm=0 aifs=2 cWmin=7 cWmax=15 burst=30
[  102.455715] wlan1: WMM queue=0 aci=3 acm=0 aifs=2 cWmin=3 cWmax=7 burst=15
[  103.115211] wlan1: RX WEP frame with unknown keyidx 1 (A1=ff:ff:ff:ff:ff:ff A2=00:0e:9b:a2:d3:1d A3=00:11:5b:5b:6b:74)
[  109.589121] NET: Registered protocol family 10
[  109.589619] lo: Disabled Privacy Extensions
[  109.589894] ADDRCONF(NETDEV_UP): eth0: link is not ready
[  120.468613] wlan1: no IPv6 routers present
[  345.987207] usb 4-1: USB disconnect, address 2
[  346.311394] usb 4-1: new high speed USB device using ehci_hcd and address 3
[  346.447396] usb 4-1: configuration #1 chosen from 1 choice
[  346.481379] p54: LM86 firmware
[  348.477711] prism54usb: firmware upload failed!
[  348.477780] prism54usb: probe of 4-1:1.0 failed with error -110
[  441.927492] usb 4-1: USB disconnect, address 3
[  444.132646] usb 4-1: new high speed USB device using ehci_hcd and address 4
[  444.268624] usb 4-1: configuration #1 chosen from 1 choice
[  444.298331] p54: LM86 firmware
[  444.737556] wmaster0: Selected rate control algorithm 'simple'
[  444.737749] phy2: hwaddr 00:0b:6b:6c:a8:75, isl3887
[  444.793964] ADDRCONF(NETDEV_UP): wlan1: link is not ready
[  456.746915] wlan1: Initial auth_alg=0
[  456.746923] wlan1: authenticate with AP 00:0e:9b:a2:d3:1d
[  456.750834] wlan1: RX authentication from 00:0e:9b:a2:d3:1d (alg=0 transaction=2 status=0)
[  456.750842] wlan1: authenticated
[  456.750845] wlan1: associate with AP 00:0e:9b:a2:d3:1d
[  456.753692] wlan1: RX AssocResp from 00:0e:9b:a2:d3:1d (capab=0x411 status=0 aid=1)
[  456.753698] wlan1: associated
[  456.753782] wlan1: WMM queue=2 aci=0 acm=0 aifs=3 cWmin=15 cWmax=1023 burst=0
[  456.753789] wlan1: WMM queue=3 aci=1 acm=0 aifs=7 cWmin=15 cWmax=1023 burst=0
[  456.753794] wlan1: WMM queue=1 aci=2 acm=0 aifs=2 cWmin=7 cWmax=15 burst=30
[  456.753799] wlan1: WMM queue=0 aci=3 acm=0 aifs=2 cWmin=3 cWmax=7 burst=15
[  456.754000] ADDRCONF(NETDEV_CHANGE): wlan1: link becomes ready
[  474.027556] wlan1: no IPv6 routers present
[ 5903.690244] usb 4-2: new high speed USB device using ehci_hcd and address 5
[ 5904.393677] usb 4-2: new high speed USB device using ehci_hcd and address 6
[ 5904.689453] usb 4-2: new high speed USB device using ehci_hcd and address 7
[ 5905.800557] usb 4-2: new high speed USB device using ehci_hcd and address 8
[ 5906.096319] usb 4-2: new high speed USB device using ehci_hcd and address 9
[ 5906.392080] usb 4-2: new high speed USB device using ehci_hcd and address 10
[ 5907.263630] hub 4-0:1.0: Cannot enable port 2.  Maybe the USB cable is bad?
[ 5907.559142] usb 4-2: new high speed USB device using ehci_hcd and address 12
[ 5908.430708] hub 4-0:1.0: Cannot enable port 2.  Maybe the USB cable is bad?
[ 5909.093895] usb 4-2: new high speed USB device using ehci_hcd and address 16
[ 5909.965408] hub 4-0:1.0: Cannot enable port 2.  Maybe the USB cable is bad?
[ 5910.077130] usb 4-2: new high speed USB device using ehci_hcd and address 17
[ 5910.948735] hub 4-0:1.0: Cannot enable port 2.  Maybe the USB cable is bad?
[ 5911.060310] usb 4-2: new high speed USB device using ehci_hcd and address 18
[ 5911.467981] usb 4-2: device not accepting address 18, error -71
[ 5911.579895] usb 4-2: new high speed USB device using ehci_hcd and address 19
[ 5911.987560] usb 4-2: device not accepting address 19, error -71
[ 6150.203876] wlan1: No ProbeResp from current AP 00:0e:9b:a2:d3:1d - assume out of range
[ 6150.995321] wlan1: No STA entry for own AP 00:0e:9b:a2:d3:1d
[ 6156.682711] wlan1: No STA entry for own AP 00:0e:9b:a2:d3:1d
[ 6162.370191] wlan1: No STA entry for own AP 00:0e:9b:a2:d3:1d
[ 6168.057601] wlan1: No STA entry for own AP 00:0e:9b:a2:d3:1d
[ 6172.215859] ADDRCONF(NETDEV_CHANGE): wlan1: link becomes ready
[ 6172.406640] ADDRCONF(NETDEV_UP): wlan1: link is not ready
[ 6245.203435] usb 4-2: new high speed USB device using ehci_hcd and address 21
[ 6246.075029] hub 4-0:1.0: Cannot enable port 2.  Maybe the USB cable is bad?
[ 6246.186649] usb 4-2: new high speed USB device using ehci_hcd and address 22
[ 6247.058232] hub 4-0:1.0: Cannot enable port 2.  Maybe the USB cable is bad?
[ 6247.353707] usb 4-2: new high speed USB device using ehci_hcd and address 24
[ 6247.853307] usb 4-2: new high speed USB device using ehci_hcd and address 25
[ 6248.964397] usb 4-2: new high speed USB device using ehci_hcd and address 26
[ 6249.835959] hub 4-0:1.0: Cannot enable port 2.  Maybe the USB cable is bad?
[ 6249.947606] usb 4-2: new high speed USB device using ehci_hcd and address 27
[ 6250.651042] usb 4-2: new high speed USB device using ehci_hcd and address 28
[ 6251.130656] usb 4-2: new high speed USB device using ehci_hcd and address 30
[ 6252.002228] hub 4-0:1.0: Cannot enable port 2.  Maybe the USB cable is bad?
[ 6252.297745] usb 4-2: new high speed USB device using ehci_hcd and address 32
[ 6253.001157] usb 4-2: new high speed USB device using ehci_hcd and address 33
[ 6253.872699] hub 4-0:1.0: Cannot enable port 2.  Maybe the USB cable is bad?
[ 6253.984381] usb 4-2: new high speed USB device using ehci_hcd and address 34
[ 6254.280143] usb 4-2: new high speed USB device using ehci_hcd and address 35
[ 6255.151825] hub 4-0:1.0: Cannot enable port 2.  Maybe the USB cable is bad?
[ 6255.164087] ADDRCONF(NETDEV_UP): wlan1: link is not ready
[ 6255.263378] usb 4-2: new high speed USB device using ehci_hcd and address 36
[ 6255.559139] usb 4-2: new high speed USB device using ehci_hcd and address 37
[ 6256.430700] hub 4-0:1.0: Cannot enable port 2.  Maybe the USB cable is bad?
[ 6256.910016] usb 4-2: new high speed USB device using ehci_hcd and address 40
[ 6257.781526] hub 4-0:1.0: Cannot enable port 2.  Maybe the USB cable is bad?
[ 6257.893215] usb 4-2: new high speed USB device using ehci_hcd and address 41

---

### Post by daengbo on 2008-04-20
Your problem is obviously there at the end of dmesg. Have you tried the hardware on another system (other Linux or OS) to see if the hardware works?

Card readers and USB drives usually just work unless there's a hardware problem.

The only difference I can find in your dmesg output is that the working one is full speed while the ones that don't work are high speed. USB 2.0 has been pretty good on Linux since 2004, though, so that should really matter.

---

