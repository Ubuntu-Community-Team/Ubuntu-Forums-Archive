---
title: "Seagate Freeagent 500GB drive will not mount on VIA USB PCI card in Ubuntu 7.10"
date: 2008-02-24
forum: Hardware &amp; Laptops
---

### Post by smiiiiiiiiiith on 2008-02-24
Hello all,

Having looked through all related posts, I have not found a solution to my problem.

I have an external USB Seagate Freeagent 500GB drive, formatted as one NTFS partition.  When I first bought the drive, I only had the use of my motherboard's USB 1.1 ports, so bought a VIA PCI card for USB 2.0 support.  I initially had no trouble mounting on USB 1.1 in Windows, but mounting on the USB 2.0 ports was intermittent, although my other USB devices (a Logitech webcam and a 1GB memory stick) have no problems.

Recently however the drive has stopped mounting at all in Windows, so I have tried mounting in Ubuntu to see if I can get the data off it and maybe try reformatting in ext3.  Initially I had no success, but after rewriting the partition using testdisk, it now automounts with no problems on the motherboard USB ports, but will still not mount on a USB 2.0 port (it did mount once, but at at 12 MBps).

Here is the response to an attempt to mount:

```

Error reading bootsector: Input/output error
Failed to mount '/dev/sdb1': Input/output error
NTFS is either inconsistent, or you have hardware faults, or you have a SoftRAID/FakeRAID hardware. 
In the first case run chkdsk /f on Windows then reboot into Windows TWICE. The usage of the /f parameter is very important!
 If you have SoftRAID/FakeRAID then first you must activate it and mount a different device under the /dev/mapper/ directory,
 (e.g. /dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation for the details.

```

Below is the dmesg output when connected to a USB 2.0 port:

```

[    0.000000] Linux version 2.6.22-14-generic (buildd@terranova) (gcc version 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)) #1 SMP Tue Feb 12 07:42:25 UTC 2008 (Ubuntu 2.6.22-14.52-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000002fff0000 (usable)
[    0.000000]  BIOS-e820: 000000002fff0000 - 000000002fff8000 (ACPI data)
[    0.000000]  BIOS-e820: 000000002fff8000 - 0000000030000000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000ffff0000 - 0000000100000000 (reserved)
[    0.000000] 0MB HIGHMEM available.
[    0.000000] 767MB LOWMEM available.
[    0.000000] Entering add_active_range(0, 0, 196592) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   196592
[    0.000000]   HighMem    196592 ->   196592
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   196592
[    0.000000] On node 0 totalpages: 196592
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 1503 pages used for memmap
[    0.000000]   Normal zone: 190993 pages, LIFO batch:31
[    0.000000]   HighMem zone: 0 pages used for memmap
[    0.000000] DMI 2.3 present.
[    0.000000] ACPI: RSDP signature @ 0xC00FABC0 checksum 0
[    0.000000] ACPI: RSDP 000FABC0, 0014 (r0 AMI   )
[    0.000000] ACPI: RSDT 2FFF0000, 0028 (r1 AMIINT                10 MSFT       97)
[    0.000000] ACPI: FACP 2FFF0030, 0074 (r1 AMIINT                10 MSFT       97)
[    0.000000] ACPI: DSDT 2FFF00B0, 1EE8 (r1 AMD75X IRONGATE     1000 MSFT  100000B)
[    0.000000] ACPI: FACS 2FFF8000, 0040
[    0.000000] ACPI: PM-Timer IO Port: 0x5008
[    0.000000] Allocating PCI resources starting at 40000000 (gap: 30000000:cfff0000)
[    0.000000] Built 1 zonelists.  Total pages: 195057
[    0.000000] Kernel command line: root=UUID=222d4aaa-23a8-40b3-aa40-ff732fefd9cd ro quiet splash
[    0.000000] Local APIC disabled by BIOS -- you can enable it with "lapic"
[    0.000000] mapped APIC to ffffd000 (0160e000)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] Detected 1212.005 MHz processor.
[   25.991430] Console: colour VGA+ 80x25
[   25.993221] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[   25.995975] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[   26.054429] Memory: 767884k/786368k available (2015k kernel code, 17880k reserved, 915k data, 364k init, 0k highmem)
[   26.054450] virtual kernel memory layout:
[   26.054452]     fixmap  : 0xfff4d000 - 0xfffff000   ( 712 kB)
[   26.054454]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   26.054456]     vmalloc : 0xf0800000 - 0xff7fe000   ( 239 MB)
[   26.054459]     lowmem  : 0xc0000000 - 0xefff0000   ( 767 MB)
[   26.054461]       .init : 0xc03e3000 - 0xc043e000   ( 364 kB)
[   26.054463]       .data : 0xc02f7e86 - 0xc03dce84   ( 915 kB)
[   26.054466]       .text : 0xc0100000 - 0xc02f7e86   (2015 kB)
[   26.054473] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   26.054568] SLUB: Genslabs=22, HWalign=32, Order=0-1, MinObjects=4, CPUs=1, Nodes=1
[   26.134515] Calibrating delay using timer specific routine.. 2426.14 BogoMIPS (lpj=4852297)
[   26.134580] Security Framework v1.0.0 initialized
[   26.134596] SELinux:  Disabled at boot.
[   26.134637] Mount-cache hash table entries: 512
[   26.134940] CPU: After generic identify, caps: 0183f9ff c1c7f9ff 00000000 00000000 00000000 00000000 00000000
[   26.134957] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[   26.134963] CPU: L2 Cache: 256K (64 bytes/line)
[   26.134968] CPU: After all inits, caps: 0183f9ff c1c7f9ff 00000000 00000420 00000000 00000000 00000000
[   26.134991] Compat vDSO mapped to ffffe000.
[   26.135019] Checking 'hlt' instruction... OK.
[   26.150582] SMP alternatives: switching to UP code
[   26.151118] Freeing SMP alternatives: 11k freed
[   26.151871] Early unpacking initramfs... done
[   26.715747] ACPI: Core revision 20070126
[   26.715931] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[   26.717491] ACPI: setting ELCR to 0800 (from 0c00)
[   26.717979] CPU0: AMD Athlon(tm) Processor stepping 02
[   26.717991] SMP motherboard not detected.
[   26.717996] Local APIC not detected. Using dummy APIC emulation.
[   26.718093] Brought up 1 CPUs
[   26.718405] Booting paravirtualized kernel on bare hardware
[   26.718518] Time: 14:38:11  Date: 01/24/108
[   26.718582] NET: Registered protocol family 16
[   26.718807] EISA bus registered
[   26.718828] ACPI: bus type pci registered
[   26.748209] PCI: PCI BIOS revision 2.10 entry at 0xfdb71, last bus=1
[   26.748215] PCI: Using configuration type 1
[   26.748218] Setting up standard PCI resources
[   26.762362] ACPI: EC: Look up EC in DSDT
[   26.765191] ACPI: Interpreter enabled
[   26.765196] ACPI: (supports S0 S1 S4 S5)
[   26.765222] ACPI: Using PIC for interrupt routing
[   26.770327] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   26.770351] PCI: Probing PCI hardware (bus 00)
[   26.771103] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   26.772762] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 9 *10 11 12 14 15)
[   26.772887] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
[   26.773007] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 9 *10 11 12 14 15)
[   26.773125] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 9 *10 11 12 14 15)
[   26.773278] ACPI: Power Resource [URP1] (off)
[   26.773320] ACPI: Power Resource [URP2] (off)
[   26.773359] ACPI: Power Resource [FDDP] (off)
[   26.773399] ACPI: Power Resource [LPTP] (off)
[   26.773413] Linux Plug and Play Support v0.97 (c) Adam Belay
[   26.773455] pnp: PnP ACPI init
[   26.773470] ACPI: bus type pnp registered
[   26.777437] pnp: PnP ACPI: found 12 devices
[   26.777442] ACPI: ACPI bus type pnp unregistered
[   26.777451] PnPBIOS: Disabled by ACPI PNP
[   26.777578] PCI: Using ACPI for IRQ routing
[   26.777584] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   26.780210] NET: Registered protocol family 8
[   26.780215] NET: Registered protocol family 20
[   26.780359] pnp: 00:01: ioport range 0xde00-0xde03 has been reserved
[   26.781840] Time: tsc clocksource has been installed.
[   26.810929] PCI: Bridge: 0000:00:01.0
[   26.810933]   IO window: b000-bfff
[   26.810941]   MEM window: e5a00000-e7afffff
[   26.810946]   PREFETCH window: d9800000-dd8fffff
[   26.810981] NET: Registered protocol family 2
[   26.849914] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[   26.850405] TCP established hash table entries: 131072 (order: 8, 1572864 bytes)
[   26.856899] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[   26.859733] TCP: Hash tables configured (established 131072 bind 65536)
[   26.859744] TCP reno registered
[   26.870107] checking if image is initramfs...<6>Switched to high resolution mode on CPU 0
[   27.338788]  it is
[   27.933279] Freeing initrd memory: 7058k freed
[   27.934158] audit: initializing netlink socket (disabled)
[   27.934190] audit(1203863891.732:1): initialized
[   27.938116] VFS: Disk quotas dquot_6.5.1
[   27.938226] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   27.938441] io scheduler noop registered
[   27.938446] io scheduler anticipatory registered
[   27.938450] io scheduler deadline registered
[   27.938473] io scheduler cfq registered (default)
[   27.938570] Boot video device is 0000:01:05.0
[   27.938914] isapnp: Scanning for PnP cards...
[   28.292518] isapnp: No Plug & Play device found
[   28.350496] Real Time Clock Driver v1.12ac
[   28.350679] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   28.350859] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   28.351295] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[   28.352717] 00:09: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   28.353393] 00:0a: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[   28.355021] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   28.355605] input: Macintosh mouse button emulation as /class/input/input0
[   28.355791] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f03:PS2M] at 0x60,0x64 irq 1,12
[   28.360396] serio: i8042 KBD port at 0x60,0x64 irq 1
[   28.360412] serio: i8042 AUX port at 0x60,0x64 irq 12
[   28.360877] mice: PS/2 mouse device common for all mice
[   28.361121] EISA: Probing bus 0 at eisa.0
[   28.361157] Cannot allocate resource for EISA slot 5
[   28.361174] EISA: Detected 0 cards.
[   28.361388] TCP cubic registered
[   28.361406] NET: Registered protocol family 1
[   28.361447] Using IPI No-Shortcut mode
[   28.361806]   Magic number: 12:842:637
[   28.363307] Freeing unused kernel memory: 364k freed
[   28.404230] input: AT Translated Set 2 keyboard as /class/input/input1
[   29.773662] AppArmor: AppArmor initialized<5>audit(1203863893.232:2):  type=1505 info="AppArmor initialized" pid=1165
[   29.786957] fuse init (API version 7.8)
[   29.796801] Failure registering capabilities with primary security module.
[   29.831605] ACPI: Thermal Zone [THRM] (30 C)
[   30.978507] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[   30.978523] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[   30.979998] AMD7409: IDE controller at PCI slot 0000:00:07.1
[   30.980036] AMD7409: chipset revision 7
[   30.980040] AMD7409: not 100% native mode: will probe irqs later
[   30.980055] AMD7409: 0000:00:07.1 (rev 07) UDMA66 controller
[   30.980077]     ide0: BM-DMA at 0xf000-0xf007, BIOS settings: hda:DMA, hdb:DMA
[   30.980096]     ide1: BM-DMA at 0xf008-0xf00f, BIOS settings: hdc:DMA, hdd:DMA
[   30.980110] Probing IDE interface ide0...
[   31.027043] usbcore: registered new interface driver usbfs
[   31.027106] usbcore: registered new interface driver hub
[   31.027164] usbcore: registered new device driver usb
[   31.028885] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
[   31.067824] USB Universal Host Controller Interface driver v3.0
[   31.141186] 8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)
[   31.265059] hda: ST380011A, ATA DISK drive
[   31.399251] FDC 0 is a post-1991 82077
[   31.544700] hdb: Maxtor 6L160P0, ATA DISK drive
[   31.604325] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[   31.604484] Probing IDE interface ide1...
[   32.339820] hdc: DVDRW IDE 16X, ATAPI CD/DVD-ROM drive
[   33.122951] hdd: CRD-8322B, ATAPI CD/DVD-ROM drive
[   33.181244] ide1 at 0x170-0x177,0x376 on irq 15
[   33.196546] SCSI subsystem initialized
[   33.207413] libata version 2.21 loaded.
[   33.212352] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 10
[   33.212365] PCI: setting IRQ 10 as level-triggered
[   33.212372] ACPI: PCI Interrupt 0000:00:07.4[D] -> Link [LNKD] -> GSI 10 (level, low) -> IRQ 10
[   33.212404] ohci_hcd 0000:00:07.4: OHCI Host Controller
[   33.213346] ohci_hcd 0000:00:07.4: new USB bus registered, assigned bus number 1
[   33.213389] ohci_hcd 0000:00:07.4: irq 10, io mem 0xefdfe000
[   33.230696] hda: max request size: 512KiB
[   33.266338] hda: 156301488 sectors (80026 MB) w/2048KiB Cache, CHS=16383/255/63, UDMA(66)
[   33.267082] usb usb1: configuration #1 chosen from 1 choice
[   33.267144] hub 1-0:1.0: USB hub found
[   33.267171] hub 1-0:1.0: 4 ports detected
[   33.267371] hda: cache flushes supported
[   33.267462]  hda: hda1 hda2
[   33.283879] hdb: max request size: 512KiB
[   33.305380] hdb: 320173056 sectors (163928 MB) w/8192KiB Cache, CHS=19929/255/63, UDMA(66)
[   33.306944] hdb: cache flushes supported
[   33.307017]  hdb: hdb1 hdb2
[   33.371590] ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 10
[   33.371602] ACPI: PCI Interrupt 0000:00:08.0[A] -> Link [LNKA] -> GSI 10 (level, low) -> IRQ 10
[   33.371627] uhci_hcd 0000:00:08.0: UHCI Host Controller
[   33.371688] uhci_hcd 0000:00:08.0: new USB bus registered, assigned bus number 2
[   33.371726] uhci_hcd 0000:00:08.0: irq 10, io base 0x0000d800
[   33.371981] usb usb2: configuration #1 chosen from 1 choice
[   33.372044] hub 2-0:1.0: USB hub found
[   33.372067] hub 2-0:1.0: 2 ports detected
[   33.384696] hdc: ATAPI 48X DVD-ROM DVD-R CD-R/RW drive, 2048kB Cache<4>hdc: drive side 80-wire cable detection failed, limiting max speed to UDMA33
[   33.384720] 
[   33.384726] Uniform CD-ROM driver Revision: 3.20
[   33.441568] hdd: ATAPI 32X CD-ROM drive, 128kB Cache, DMA
[   33.475247] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 11
[   33.475258] PCI: setting IRQ 11 as level-triggered
[   33.475264] ACPI: PCI Interrupt 0000:00:08.1[B] -> Link [LNKB] -> GSI 11 (level, low) -> IRQ 11
[   33.475287] uhci_hcd 0000:00:08.1: UHCI Host Controller
[   33.475348] uhci_hcd 0000:00:08.1: new USB bus registered, assigned bus number 3
[   33.475387] uhci_hcd 0000:00:08.1: irq 11, io base 0x0000da00
[   33.475651] usb usb3: configuration #1 chosen from 1 choice
[   33.475710] hub 3-0:1.0: USB hub found
[   33.475731] hub 3-0:1.0: 2 ports detected
[   33.579290] ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 10
[   33.579302] ACPI: PCI Interrupt 0000:00:08.2[C] -> Link [LNKC] -> GSI 10 (level, low) -> IRQ 10
[   33.579330] ehci_hcd 0000:00:08.2: EHCI Host Controller
[   33.579397] ehci_hcd 0000:00:08.2: new USB bus registered, assigned bus number 4
[   33.579488] ehci_hcd 0000:00:08.2: irq 10, io mem 0xefdffe00
[   33.579497] ehci_hcd 0000:00:08.2: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   33.579728] usb usb4: configuration #1 chosen from 1 choice
[   33.579786] hub 4-0:1.0: USB hub found
[   33.579809] hub 4-0:1.0: 4 ports detected
[   33.682774] 8139cp 0000:00:0b.0: This (id 10ec:8139 rev 10) is not an 8139C+ compatible chip
[   33.682788] 8139cp 0000:00:0b.0: Try the "8139too" driver instead.
[   33.686977] 8139too Fast Ethernet driver 0.9.28
[   33.687091] ACPI: PCI Interrupt 0000:00:0b.0[A] -> Link [LNKD] -> GSI 10 (level, low) -> IRQ 10
[   33.687488] eth0: RealTek RTL8139 at 0xf083af00, 00:06:4f:18:4d:09, IRQ 10
[   33.687493] eth0:  Identified 8139 chip type 'RTL-8100B/8139D'
[   33.915106] Attempting manual resume
[   33.915115] swsusp: Resume From Partition 3:66
[   33.915118] PM: Checking swsusp image.
[   33.932591] PM: Resume from disk failed.
[   33.998369] kjournald starting.  Commit interval 5 seconds
[   33.998399] EXT3-fs: mounted filesystem with ordered data mode.
[   34.353529] usb 4-1: new high speed USB device using ehci_hcd and address 2
[   34.502483] usb 4-1: configuration #1 chosen from 1 choice
[   34.745125] usb 4-4: new high speed USB device using ehci_hcd and address 3
[   34.881420] usb 4-4: configuration #1 chosen from 1 choice
[   45.697479] Linux agpgart interface v0.102 (c) Dave Jones
[   45.745908] agpgart: Detected AMD Irongate chipset
[   45.745928] agpgart: AMD 751 chipset with NVidia GeForce detected. Forcing to 1X due to errata.
[   45.757807] agpgart: AGP aperture is 64M @ 0xe0000000
[   45.802876] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   45.806699] shpchp: HPC vendor_id 1022 device_id 7007 ss_vid 0 ss_did 0
[   45.806713] shpchp: shpc_init: cannot reserve MMIO region
[   45.806753] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   47.237605] Linux video capture interface: v2.00
[   47.606118] input: PC Speaker as /class/input/input2
[   47.778331] saa7130/34: v4l2 driver version 0.2.14 loaded
[   47.778562] ACPI: PCI Interrupt 0000:00:09.0[A] -> Link [LNKB] -> GSI 11 (level, low) -> IRQ 11
[   47.778579] saa7133[0]: found at 0000:00:09.0, rev: 209, irq: 11, latency: 64, mmio: 0xefdff000
[   47.778592] saa7133[0]: subsystem: 1461:2c00, board: AVerMedia TV Hybrid A16AR [card=99,insmod option]
[   47.778610] saa7133[0]: board init: gpio is 2e600
[   47.778828] input: saa7134 IR (AVerMedia TV Hybrid as /class/input/input3
[   47.838705] input: ImPS/2 Logitech Wheel Mouse as /class/input/input4
[   47.843652] usbcore: registered new interface driver libusual
[   47.914585] saa7133[0]: i2c eeprom 00: 61 14 00 2c 00 00 00 00 00 00 00 00 00 00 00 00
[   47.914601] saa7133[0]: i2c eeprom 10: 00 ff 82 0e ff 20 ff ff ff ff ff ff ff ff ff ff
[   47.914613] saa7133[0]: i2c eeprom 20: 01 40 01 02 02 03 03 01 08 ff 00 a3 ff ff ff ff
[   47.914624] saa7133[0]: i2c eeprom 30: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   47.914635] saa7133[0]: i2c eeprom 40: ff 32 00 c0 86 1e ff ff ff ff ff ff ff ff ff ff
[   47.914646] saa7133[0]: i2c eeprom 50: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   47.914657] saa7133[0]: i2c eeprom 60: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   47.914668] saa7133[0]: i2c eeprom 70: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   47.995793] Initializing USB Mass Storage driver...
[   47.996181] scsi0 : SCSI emulation for USB Mass Storage devices
[   47.996309] usb-storage: device found at 2
[   47.996314] usb-storage: waiting for device to settle before scanning
[   47.996399] scsi1 : SCSI emulation for USB Mass Storage devices
[   47.996503] usb-storage: device found at 3
[   47.996506] usb-storage: waiting for device to settle before scanning
[   47.996527] usbcore: registered new interface driver usb-storage
[   47.996533] USB Mass Storage support registered.
[   48.074699] tuner 1-0043: chip found @ 0x86 (saa7133[0])
[   48.074791] tda9887 1-0043: tda988[5/6/7] found @ 0x43 (tuner)
[   48.090446] tuner 1-0060: TEA5767 detected.
[   48.090457] tuner 1-0060: chip found @ 0xc0 (saa7133[0])
[   48.090554] tuner 1-0060: type set to 62 (Philips TEA5767HN FM Radio)
[   48.198496] saa7133[0]: registered device video0 [v4l2]
[   48.198563] saa7133[0]: registered device vbi0
[   48.198620] saa7133[0]: registered device radio0
[   48.216642] parport_pc 00:0b: reported by Plug and Play ACPI
[   48.216791] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,EPP,ECP,DMA]
[   48.629893] DVB: registering new adapter (saa7133[0]).
[   48.629909] DVB: registering frontend 0 (Zarlink MT352 DVB-T)...
[   48.906262] saa7134 ALSA driver for DMA sound loaded
[   48.906339] saa7133[0]/alsa: saa7133[0] at 0xefdff000 irq 11 registered as card -2
[   49.561765] lp0: using parport0 (interrupt-driven).
[   49.660007] Adding 1469936k swap on /dev/hdb2.  Priority:-1 extents:1 across:1469936k
[   50.002327] EXT3 FS on hda2, internal journal
[   52.860038] No dock devices found.
[   52.989282] usb-storage: device scan complete
[   52.990699] scsi 1:0:0:0: Direct-Access              USB DISK 2.0     PMAP PQ: 0 ANSI: 0 CCS
[   52.990747] usb-storage: device scan complete
[   52.993028] scsi 0:0:0:0: Direct-Access     Seagate  FreeAgentDesktop 100D PQ: 0 ANSI: 4
[   53.063422] input: Power Button (FF) as /class/input/input5
[   53.073457] ACPI: Power Button (FF) [PWRF]
[   53.116362] input: Sleep Button (FF) as /class/input/input6
[   53.116763] ACPI: Sleep Button (FF) [SLPF]
[   53.152895] input: Power Button (CM) as /class/input/input7
[   53.153632] ACPI: Power Button (CM) [PWRB]
[   53.336665] sd 1:0:0:0: [sda] 2015232 512-byte hardware sectors (1032 MB)
[   53.340666] sd 1:0:0:0: [sda] Write Protect is off
[   53.340672] sd 1:0:0:0: [sda] Mode Sense: 23 00 00 00
[   53.340678] sd 1:0:0:0: [sda] Assuming drive cache: write through
[   53.346867] sd 1:0:0:0: [sda] 2015232 512-byte hardware sectors (1032 MB)
[   53.348646] sd 1:0:0:0: [sda] Write Protect is off
[   53.348652] sd 1:0:0:0: [sda] Mode Sense: 23 00 00 00
[   53.348657] sd 1:0:0:0: [sda] Assuming drive cache: write through
[   53.348671]  sda: sda1
[   53.353558] sd 1:0:0:0: [sda] Attached SCSI removable disk
[   53.361511] sd 0:0:0:0: [sdb] Spinning up disk...<6>powernow: No powernow capabilities detected
[   56.208091] eth0: link up, 100Mbps, full-duplex, lpa 0x41E1
[   56.574366] ppdev: user-space parallel port driver
[   57.091946] audit(1203863921.408:3):  type=1503 operation="inode_permission" requested_mask="a" denied_mask="a" name="/dev/tty" pid=4715 profile="/usr/sbin/cupsd"
[   60.399148] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[   60.399163] apm: overridden by ACPI.
[   61.551441] NET: Registered protocol family 10
[   61.552339] lo: Disabled Privacy Extensions
[   61.634803] Failure registering capabilities with primary security module.
[   63.062090] .ready
[   63.064419] sd 0:0:0:0: [sdb] 976773168 512-byte hardware sectors (500108 MB)
[   63.065922] sd 0:0:0:0: [sdb] Write Protect is off
[   63.065930] sd 0:0:0:0: [sdb] Mode Sense: 1c 00 00 00
[   63.065941] sd 0:0:0:0: [sdb] Assuming drive cache: write through
[   63.070119] sd 0:0:0:0: [sdb] 976773168 512-byte hardware sectors (500108 MB)
[   63.071654] sd 0:0:0:0: [sdb] Write Protect is off
[   63.071661] sd 0:0:0:0: [sdb] Mode Sense: 1c 00 00 00
[   63.071666] sd 0:0:0:0: [sdb] Assuming drive cache: write through
[   63.071676]  sdb: sdb1
[   63.100207] sd 0:0:0:0: [sdb] Attached SCSI disk
[   63.150001] sd 1:0:0:0: Attached scsi generic sg0 type 0
[   63.160842] sd 0:0:0:0: Attached scsi generic sg1 type 0
[   63.753433] usb 4-1: reset high speed USB device using ehci_hcd and address 2
[   63.997192] usb 4-4: reset high speed USB device using ehci_hcd and address 3
[   64.240887] usb 4-1: reset high speed USB device using ehci_hcd and address 2
[   64.484646] usb 4-4: reset high speed USB device using ehci_hcd and address 3
[   64.728438] usb 4-1: reset high speed USB device using ehci_hcd and address 2
[   64.973554] Bluetooth: Core ver 2.11
[   64.973829] NET: Registered protocol family 31
[   64.973834] Bluetooth: HCI device and connection manager initialized
[   64.973842] Bluetooth: HCI socket layer initialized
[   64.984223] usb 4-1: reset high speed USB device using ehci_hcd and address 2
[   65.020337] Bluetooth: L2CAP ver 2.8
[   65.020349] Bluetooth: L2CAP socket layer initialized
[   65.239893] usb 4-1: reset high speed USB device using ehci_hcd and address 2
[   65.325221] Bluetooth: RFCOMM socket layer initialized
[   65.325420] Bluetooth: RFCOMM TTY layer initialized
[   65.325424] Bluetooth: RFCOMM ver 1.8
[   65.495700] usb 4-1: reset high speed USB device using ehci_hcd and address 2
[   65.639528] sd 0:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
[   65.639552] end_request: I/O error, dev sdb, sector 48
[   65.639563] Buffer I/O error on device sdb, logical block 6
[   65.639577] Buffer I/O error on device sdb, logical block 7
[   65.639583] Buffer I/O error on device sdb, logical block 8
[   65.639589] Buffer I/O error on device sdb, logical block 9
[   65.639595] Buffer I/O error on device sdb, logical block 10
[   65.639601] Buffer I/O error on device sdb, logical block 11
[   65.639607] Buffer I/O error on device sdb, logical block 12
[   65.639613] Buffer I/O error on device sdb, logical block 13
[   65.639619] Buffer I/O error on device sdb, logical block 14
[   65.639624] Buffer I/O error on device sdb, logical block 15
[   65.915225] usb 4-1: reset high speed USB device using ehci_hcd and address 2
[   66.170949] usb 4-1: reset high speed USB device using ehci_hcd and address 2
[   66.430690] usb 4-1: reset high speed USB device using ehci_hcd and address 2
[   66.686452] usb 4-1: reset high speed USB device using ehci_hcd and address 2
[   66.946258] usb 4-1: reset high speed USB device using ehci_hcd and address 2
[   67.041619] NET: Registered protocol family 17
[   67.205952] usb 4-1: reset high speed USB device using ehci_hcd and address 2
[   67.349820] sd 0:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
[   67.349847] end_request: I/O error, dev sdb, sector 73
[   67.569573] usb 4-1: reset high speed USB device using ehci_hcd and address 2
[   67.909288] usb 4-1: reset high speed USB device using ehci_hcd and address 2
[   68.164971] usb 4-1: reset high speed USB device using ehci_hcd and address 2
[   68.420686] usb 4-1: reset high speed USB device using ehci_hcd and address 2
[   68.676432] usb 4-1: reset high speed USB device using ehci_hcd and address 2
[   68.932253] usb 4-1: reset high speed USB device using ehci_hcd and address 2
[   69.188770] usb 4-1: reset high speed USB device using ehci_hcd and address 2
[   69.335837] sd 0:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
[   69.335864] end_request: I/O error, dev sdb, sector 73
[   81.899209] eth0: no IPv6 routers present
[  115.902401] usb 4-1: reset high speed USB device using ehci_hcd and address 2
[  116.176741] usb 4-1: reset high speed USB device using ehci_hcd and address 2
[  116.440725] usb 4-1: reset high speed USB device using ehci_hcd and address 2
[  116.728487] usb 4-1: reset high speed USB device using ehci_hcd and address 2
[  116.992281] usb 4-1: reset high speed USB device using ehci_hcd and address 2
[  117.247986] usb 4-1: reset high speed USB device using ehci_hcd and address 2
[  117.507637] usb 4-1: reset high speed USB device using ehci_hcd and address 2
[  118.182985] usb 4-1: reset high speed USB device using ehci_hcd and address 2
[  118.466741] usb 4-1: reset high speed USB device using ehci_hcd and address 2
[  118.722444] usb 4-1: reset high speed USB device using ehci_hcd and address 2
[  118.974200] usb 4-1: reset high speed USB device using ehci_hcd and address 2
[  119.225988] usb 4-1: reset high speed USB device using ehci_hcd and address 2
[  119.481723] usb 4-1: reset high speed USB device using ehci_hcd and address 2
[  119.737459] usb 4-1: reset high speed USB device using ehci_hcd and address 2
[  119.878622] sd 0:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
[  119.878641] end_request: I/O error, dev sdb, sector 6291535
[  119.878648] printk: 29 messages suppressed.
[  119.878654] Buffer I/O error on device sdb1, logical block 6291472
[  119.878665] Buffer I/O error on device sdb1, logical block 6291473
[  119.878672] Buffer I/O error on device sdb1, logical block 6291474
[  119.878677] Buffer I/O error on device sdb1, logical block 6291475
[  119.878684] Buffer I/O error on device sdb1, logical block 6291476
[  119.878689] Buffer I/O error on device sdb1, logical block 6291477
[  119.878696] Buffer I/O error on device sdb1, logical block 6291478
[  119.878702] Buffer I/O error on device sdb1, logical block 6291479
[  119.878712] Buffer I/O error on device sdb1, logical block 6291480
[  119.878718] Buffer I/O error on device sdb1, logical block 6291481
[  119.989246] usb 4-1: reset high speed USB device using ehci_hcd and address 2
[  120.240933] usb 4-1: reset high speed USB device using ehci_hcd and address 2
[  120.496675] usb 4-1: reset high speed USB device using ehci_hcd and address 2
[  120.748416] usb 4-1: reset high speed USB device using ehci_hcd and address 2
[  121.004167] usb 4-1: reset high speed USB device using ehci_hcd and address 2
[  121.255919] usb 4-1: reset high speed USB device using ehci_hcd and address 2
[  121.399823] sd 0:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
[  121.399843] end_request: I/O error, dev sdb, sector 6291535
[  122.314918] usb 4-4: reset high speed USB device using ehci_hcd and address 3
[  122.586595] usb 4-4: reset high speed USB device using ehci_hcd and address 3
[  166.818358] usb 4-1: reset high speed USB device using ehci_hcd and address 2
[  167.074101] usb 4-1: reset high speed USB device using ehci_hcd and address 2
[  167.333844] usb 4-1: reset high speed USB device using ehci_hcd and address 2
[  167.589582] usb 4-1: reset high speed USB device using ehci_hcd and address 2
[  167.849326] usb 4-1: reset high speed USB device using ehci_hcd and address 2
[  168.109065] usb 4-1: reset high speed USB device using ehci_hcd and address 2
[  168.252991] sd 0:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
[  168.253016] end_request: I/O error, dev sdb, sector 63
[  168.253024] printk: 30 messages suppressed.
[  168.253030] Buffer I/O error on device sdb1, logical block 0
[  168.253044] Buffer I/O error on device sdb1, logical block 1
[  168.253077] Buffer I/O error on device sdb1, logical block 2
[  168.253083] Buffer I/O error on device sdb1, logical block 3
[  168.253092] Buffer I/O error on device sdb1, logical block 4
[  168.253098] Buffer I/O error on device sdb1, logical block 5
[  168.253104] Buffer I/O error on device sdb1, logical block 6
[  168.253110] Buffer I/O error on device sdb1, logical block 7
[  168.253116] Buffer I/O error on device sdb1, logical block 8
[  262.055966] usb 4-1: reset high speed USB device using ehci_hcd and address 2
[  262.318916] usb 4-1: reset high speed USB device using ehci_hcd and address 2
[  262.578651] usb 4-1: reset high speed USB device using ehci_hcd and address 2
[  262.846396] usb 4-1: reset high speed USB device using ehci_hcd and address 2
[  263.102126] usb 4-1: reset high speed USB device using ehci_hcd and address 2
[  263.361865] usb 4-1: reset high speed USB device using ehci_hcd and address 2
[  263.617612] usb 4-1: reset high speed USB device using ehci_hcd and address 2
[  263.877407] usb 4-1: reset high speed USB device using ehci_hcd and address 2
[  264.165062] usb 4-1: reset high speed USB device using ehci_hcd and address 2
[  264.420829] usb 4-1: reset high speed USB device using ehci_hcd and address 2
[  264.684562] usb 4-1: reset high speed USB device using ehci_hcd and address 2
[  264.940296] usb 4-1: reset high speed USB device using ehci_hcd and address 2
[  265.196038] usb 4-1: reset high speed USB device using ehci_hcd and address 2
[  265.451796] usb 4-1: reset high speed USB device using ehci_hcd and address 2
[  265.707559] usb 4-1: reset high speed USB device using ehci_hcd and address 2
[  265.967286] usb 4-1: reset high speed USB device using ehci_hcd and address 2
[  266.223027] usb 4-1: reset high speed USB device using ehci_hcd and address 2
[  266.482754] usb 4-1: reset high speed USB device using ehci_hcd and address 2
[  266.738562] usb 4-1: reset high speed USB device using ehci_hcd and address 2
[  266.882403] sd 0:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
[  266.882427] end_request: I/O error, dev sdb, sector 6291535
[  266.882436] printk: 7 messages suppressed.
[  266.882443] Buffer I/O error on device sdb1, logical block 6291472
[  266.882458] Buffer I/O error on device sdb1, logical block 6291473
[  266.882464] Buffer I/O error on device sdb1, logical block 6291474
[  266.882470] Buffer I/O error on device sdb1, logical block 6291475
[  266.882477] Buffer I/O error on device sdb1, logical block 6291476
[  266.882483] Buffer I/O error on device sdb1, logical block 6291477
[  266.882489] Buffer I/O error on device sdb1, logical block 6291478
[  266.882496] Buffer I/O error on device sdb1, logical block 6291479
[  266.882505] Buffer I/O error on device sdb1, logical block 6291480
[  266.882512] Buffer I/O error on device sdb1, logical block 6291481
[  267.002235] usb 4-1: reset high speed USB device using ehci_hcd and address 2
[  287.317925] usb 4-1: reset high speed USB device using ehci_hcd and address 2
[  287.573687] usb 4-1: reset high speed USB device using ehci_hcd and address 2
[  287.833407] usb 4-1: reset high speed USB device using ehci_hcd and address 2
[  288.093153] usb 4-1: reset high speed USB device using ehci_hcd and address 2
[  288.356887] usb 4-1: reset high speed USB device using ehci_hcd and address 2
[  288.616657] usb 4-1: reset high speed USB device using ehci_hcd and address 2
[  288.760543] sd 0:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
[  288.760566] end_request: I/O error, dev sdb, sector 73
[  288.760575] printk: 22 messages suppressed.
[  288.760581] Buffer I/O error on device sdb1, logical block 5
[  288.760594] Buffer I/O error on device sdb1, logical block 6
[  288.760599] Buffer I/O error on device sdb1, logical block 7
[  288.760607] Buffer I/O error on device sdb1, logical block 8
[  288.984267] usb 4-1: reset high speed USB device using ehci_hcd and address 2
[  289.240005] usb 4-1: reset high speed USB device using ehci_hcd and address 2
[  289.515761] usb 4-1: reset high speed USB device using ehci_hcd and address 2
[  289.771476] usb 4-1: reset high speed USB device using ehci_hcd and address 2
[  290.031216] usb 4-1: reset high speed USB device using ehci_hcd and address 2
[  290.286961] usb 4-1: reset high speed USB device using ehci_hcd and address 2
[  290.546723] usb 4-1: reset high speed USB device using ehci_hcd and address 2
[  290.802442] usb 4-1: reset high speed USB device using ehci_hcd and address 2
[  290.946363] sd 0:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
[  290.946385] end_request: I/O error, dev sdb, sector 63
[  511.801584] usb 4-1: reset high speed USB device using ehci_hcd and address 2
[  512.057322] usb 4-1: reset high speed USB device using ehci_hcd and address 2
[  512.317062] usb 4-1: reset high speed USB device using ehci_hcd and address 2
[  512.572804] usb 4-1: reset high speed USB device using ehci_hcd and address 2
[  512.832566] usb 4-1: reset high speed USB device using ehci_hcd and address 2
[  513.088290] usb 4-1: reset high speed USB device using ehci_hcd and address 2
[  513.232211] sd 0:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
[  513.232262] end_request: I/O error, dev sdb, sector 72
[  513.232271] printk: 27 messages suppressed.
[  513.232277] Buffer I/O error on device sdb, logical block 9
[  513.232290] Buffer I/O error on device sdb, logical block 10
[  513.232297] Buffer I/O error on device sdb, logical block 11
[  513.352046] usb 4-1: reset high speed USB device using ehci_hcd and address 2
[  513.611773] usb 4-1: reset high speed USB device using ehci_hcd and address 2
[  513.871506] usb 4-1: reset high speed USB device using ehci_hcd and address 2
[  514.131252] usb 4-1: reset high speed USB device using ehci_hcd and address 2
[  514.386993] usb 4-1: reset high speed USB device using ehci_hcd and address 2
[  514.646755] usb 4-1: reset high speed USB device using ehci_hcd and address 2
[  514.790649] sd 0:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
[  514.790675] end_request: I/O error, dev sdb, sector 65
[  514.790687] Buffer I/O error on device sdb1, logical block 1
[  514.790700] Buffer I/O error on device sdb1, logical block 2
[  514.790706] Buffer I/O error on device sdb1, logical block 3
[  514.790716] Buffer I/O error on device sdb1, logical block 4
[  514.790722] Buffer I/O error on device sdb1, logical block 5
[  514.790727] Buffer I/O error on device sdb1, logical block 6
[  514.790734] Buffer I/O error on device sdb1, logical block 7
[ 1117.204530] usb 4-1: reset high speed USB device using ehci_hcd and address 2
[ 1117.488243] usb 4-1: reset high speed USB device using ehci_hcd and address 2
[ 1117.743991] usb 4-1: reset high speed USB device using ehci_hcd and address 2
[ 1118.003750] usb 4-1: reset high speed USB device using ehci_hcd and address 2
[ 1118.259472] usb 4-1: reset high speed USB device using ehci_hcd and address 2
[ 1118.519213] usb 4-1: reset high speed USB device using ehci_hcd and address 2
[ 1118.662023] sd 0:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
[ 1118.662043] end_request: I/O error, dev sdb, sector 63
[ 1118.662052] printk: 8 messages suppressed.
[ 1118.662059] Buffer I/O error on device sdb1, logical block 0
[ 1118.662072] Buffer I/O error on device sdb1, logical block 1
[ 1118.662078] Buffer I/O error on device sdb1, logical block 2
[ 1118.662084] Buffer I/O error on device sdb1, logical block 3
[ 1118.662094] Buffer I/O error on device sdb1, logical block 4
[ 1118.662100] Buffer I/O error on device sdb1, logical block 5
[ 1118.662106] Buffer I/O error on device sdb1, logical block 6
[ 1118.662112] Buffer I/O error on device sdb1, logical block 7
[ 1118.662118] Buffer I/O error on device sdb1, logical block 8
[ 1118.662124] Buffer I/O error on device sdb1, logical block 9
[ 1123.370387] usb 4-1: reset high speed USB device using ehci_hcd and address 2
[ 1123.626134] usb 4-1: reset high speed USB device using ehci_hcd and address 2
[ 1123.933807] usb 4-1: reset high speed USB device using ehci_hcd and address 2
[ 1124.189568] usb 4-1: reset high speed USB device using ehci_hcd and address 2
[ 1124.449286] usb 4-1: reset high speed USB device using ehci_hcd and address 2
[ 1124.705034] usb 4-1: reset high speed USB device using ehci_hcd and address 2
[ 1124.964774] usb 4-1: reset high speed USB device using ehci_hcd and address 2
[ 1125.220566] usb 4-1: reset high speed USB device using ehci_hcd and address 2
[ 1125.364434] sd 0:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
[ 1125.364454] end_request: I/O error, dev sdb, sector 488384064
[ 1125.364462] printk: 6 messages suppressed.
[ 1125.364469] Buffer I/O error on device sdb1, logical block 488384001
[ 1125.488273] usb 4-1: reset high speed USB device using ehci_hcd and address 2
[ 2097.055780] FAT: bogus number of reserved sectors
[ 2097.055804] VFS: Can't find a valid FAT filesystem on dev sdb1.
[ 2107.926438] usb 4-1: reset high speed USB device using ehci_hcd and address 2
[ 2108.234269] usb 4-1: reset high speed USB device using ehci_hcd and address 2
[ 2108.601770] usb 4-1: reset high speed USB device using ehci_hcd and address 2
[ 2108.857503] usb 4-1: reset high speed USB device using ehci_hcd and address 2
[ 2109.113256] usb 4-1: reset high speed USB device using ehci_hcd and address 2
[ 2109.368992] usb 4-1: reset high speed USB device using ehci_hcd and address 2
[ 2109.624748] usb 4-1: reset high speed USB device using ehci_hcd and address 2
[ 2109.880484] usb 4-1: reset high speed USB device using ehci_hcd and address 2
[ 2110.024363] sd 0:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
[ 2110.024387] end_request: I/O error, dev sdb, sector 6291527
[ 2110.024422] printk: 6 messages suppressed.
[ 2110.024429] Buffer I/O error on device sdb1, logical block 6291464
[ 2110.024442] Buffer I/O error on device sdb1, logical block 6291465
[ 2110.024449] Buffer I/O error on device sdb1, logical block 6291466
[ 2110.024455] Buffer I/O error on device sdb1, logical block 6291467
[ 2110.024462] Buffer I/O error on device sdb1, logical block 6291468
[ 2110.024468] Buffer I/O error on device sdb1, logical block 6291469
[ 2110.024475] Buffer I/O error on device sdb1, logical block 6291470
[ 2110.024481] Buffer I/O error on device sdb1, logical block 6291471
[ 2110.180182] usb 4-1: reset high speed USB device using ehci_hcd and address 2
[ 2110.435947] usb 4-1: reset high speed USB device using ehci_hcd and address 2
[ 2110.691693] usb 4-1: reset high speed USB device using ehci_hcd and address 2


```

Any help much appreciated!  I would just attempt a reformat now if there wasn't data on, and I would like to avoid copying it at 12 MBps if possible.

---

### Post by konungursvia on 2008-02-24
I had something like this too, with a new 500 Gb external. I don't have the 1.1  / 2.0 problem but I can guess this: an unclean unmount in linux can leave ntfs files or folders flagged as "in use" or "open", so windows doesn't dare mount it. I am less knowledgeable in general than you are, but I'd suggest this: on your 1.1 usb, try and mount the drive again. Try getting a couple of clean unmounts. Did you try ntfs-config and enable external drives? this might help the 2.0 get on it. I did solve mine, but only after days of fiddling, to get a  clean unmount. I had to delete 3 files which were all sharing a single sector! Ntfs-3g works okay but sometimes the flags and pointers get screwed up. Once I eliminated the problem with 3 files referencing the same block and sector I got a clean unmount and could mount again in windows.

---

### Post by pettertorp on 2008-02-24
[http://ubuntuforums.org/showthread.php?t=701113&highlight=pettertorp](http://ubuntuforums.org/showthread.php?t=701113&highlight=pettertorp)
this thread was what I used and now my external 500gb from seagate works amazing :)

---

### Post by konungursvia on 2008-02-24
Warning: My wife is Chinese, so this is not a racist statement: beware hard drives manufactured in China! Some now have rootkits that call home and report on your data. I'd totally reformat it in ntfs on the windows side, eliminating the "help" software.

---

