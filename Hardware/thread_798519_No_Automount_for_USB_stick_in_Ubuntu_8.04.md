---
title: "No Automount for USB stick in Ubuntu 8.04"
date: 2008-05-18
forum: Hardware
---

### Post by ekp on 2008-05-18
I have not been able to automount USB stick in Ubuntu 8.04

```
 dmesg
[    0.000000] Linux version 2.6.24-16-generic (buildd@palmer) (gcc version 4.2.3 (Ubuntu 4.2.3-2ubuntu7)) #1 SMP Thu Apr 10 13:23:42 UTC 2008 (Ubuntu 2.6.24-16.30-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000002fff0000 (usable)
[    0.000000]  BIOS-e820: 000000002fff0000 - 000000002fff8000 (ACPI data)
[    0.000000]  BIOS-e820: 000000002fff8000 - 0000000030000000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000ffee0000 - 00000000fff00000 (reserved)
[    0.000000]  BIOS-e820: 00000000fffc0000 - 0000000100000000 (reserved)
[    0.000000] 0MB HIGHMEM available.
[    0.000000] 767MB LOWMEM available.
[    0.000000] Entering add_active_range(0, 0, 196592) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   196592
[    0.000000]   HighMem    196592 ->   196592
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   196592
[    0.000000] On node 0 totalpages: 196592
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 1503 pages used for memmap
[    0.000000]   Normal zone: 190993 pages, LIFO batch:31
[    0.000000]   HighMem zone: 0 pages used for memmap
[    0.000000]   Movable zone: 0 pages used for memmap
[    0.000000] DMI 2.3 present.
[    0.000000] ACPI: RSDP signature @ 0xC00FA2C0 checksum 0
[    0.000000] ACPI: RSDP 000FA2C0, 0014 (r0 AMI   )
[    0.000000] ACPI: RSDT 2FFF0000, 0028 (r1 AMIINT SiS735XX     1000 MSFT  100000B)
[    0.000000] ACPI: FACP 2FFF0030, 0074 (r1 AMIINT SiS735XX     1000 MSFT  100000B)
[    0.000000] ACPI: DSDT 2FFF0100, 33D3 (r1    SiS      735      100 MSFT  100000D)
[    0.000000] ACPI: FACS 2FFF8000, 0040
[    0.000000] ACPI: PM-Timer IO Port: 0x808
[    0.000000] Allocating PCI resources starting at 40000000 (gap: 30000000:cec00000)
[    0.000000] swsusp: Registered nosave memory region: 000000000009f000 - 00000000000a0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000a0000 - 00000000000f0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000f0000 - 0000000000100000
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 195057
[    0.000000] Kernel command line: root=UUID=5770ba01-f9d0-4b2a-af5e-b401ce4242df ro quiet splash
[    0.000000] Local APIC disabled by BIOS -- you can enable it with "lapic"
[    0.000000] mapped APIC to ffffb000 (0160e000)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] Detected 1526.894 MHz processor.
[   36.171637] Console: colour VGA+ 80x25
[   36.171643] console [tty0] enabled
[   36.172803] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[   36.175002] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[   36.206034] Memory: 767012k/786368k available (2157k kernel code, 18748k reserved, 998k data, 364k init, 0k highmem)
[   36.206046] virtual kernel memory layout:
[   36.206047]     fixmap  : 0xfff4b000 - 0xfffff000   ( 720 kB)
[   36.206049]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   36.206050]     vmalloc : 0xf0800000 - 0xff7fe000   ( 239 MB)
[   36.206052]     lowmem  : 0xc0000000 - 0xefff0000   ( 767 MB)
[   36.206053]       .init : 0xc041b000 - 0xc0476000   ( 364 kB)
[   36.206055]       .data : 0xc031b5a4 - 0xc0414dc4   ( 998 kB)
[   36.206057]       .text : 0xc0100000 - 0xc031b5a4   (2157 kB)
[   36.206061] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   36.206119] SLUB: Genslabs=11, HWalign=32, Order=0-1, MinObjects=4, CPUs=1, Nodes=1
[   36.286065] Calibrating delay using timer specific routine.. 3055.42 BogoMIPS (lpj=6110848)
[   36.286111] Security Framework initialized
[   36.286121] SELinux:  Disabled at boot.
[   36.286148] AppArmor: AppArmor initialized
[   36.286154] Failure registering capabilities with primary security module.
[   36.286167] Mount-cache hash table entries: 512
[   36.286353] CPU: After generic identify, caps: 0383f9ff c1c3f9ff 00000000 00000000 00000000 00000000 00000000 00000000
[   36.286365] CPU: CLK_CTL MSR was 6003d22f. Reprogramming to 2003d22f
[   36.286370] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[   36.286373] CPU: L2 Cache: 256K (64 bytes/line)
[   36.286377] CPU: After all inits, caps: 0383f9ff c1c3f9ff 00000000 00000420 00000000 00000000 00000000 00000000
[   36.286392] Compat vDSO mapped to ffffe000.
[   36.286409] Checking 'hlt' instruction... OK.
[   36.302351] SMP alternatives: switching to UP code
[   36.303814] Freeing SMP alternatives: 11k freed
[   36.304008] Early unpacking initramfs... done
[   36.759874] ACPI: Core revision 20070126
[   36.759993] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[   36.761665] ACPI: setting ELCR to 0200 (from 0c20)
[   36.925967] CPU0: AMD Athlon(tm) XP 1800+ stepping 01
[   36.925976] SMP motherboard not detected.
[   36.925980] Local APIC not detected. Using dummy APIC emulation.
[   36.926057] Brought up 1 CPUs
[   36.926093] CPU0 attaching sched-domain:
[   36.926096]  domain 0: span 01
[   36.926098]   groups: 01
[   36.926412] net_namespace: 64 bytes
[   36.926426] Booting paravirtualized kernel on bare hardware
[   36.927060] Time: 10:55:13  Date: 05/18/08
[   36.927109] NET: Registered protocol family 16
[   36.927423] EISA bus registered
[   36.927439] ACPI: bus type pci registered
[   36.928866] PCI: PCI BIOS revision 2.10 entry at 0xfdb01, last bus=1
[   36.928869] PCI: Using configuration type 1
[   36.928872] Setting up standard PCI resources
[   36.931092] ACPI: EC: Look up EC in DSDT
[   36.935238] ACPI: Interpreter enabled
[   36.935243] ACPI: (supports S0 S1 S4 S5)
[   36.935259] ACPI: Using PIC for interrupt routing
[   36.940716] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   36.940914] Enabling SiS 96x SMBus.
[   36.941575] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   36.943426] ACPI: PCI Interrupt Link [LNKA] (IRQs *11)
[   36.943539] ACPI: PCI Interrupt Link [LNKB] (IRQs *11)
[   36.943647] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 7 *10 12 14 15)
[   36.943756] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 7 *10 12 14 15)
[   36.943865] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 7 10 12 14 15) *0, disabled.
[   36.943973] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 7 10 12 14 15) *0, disabled.
[   36.944082] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 7 10 12 14 15) *0, disabled.
[   36.944190] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 *5 7 10 12 14 15)
[   36.944316] ACPI: Power Resource [URP1] (off)
[   36.944350] ACPI: Power Resource [URP2] (off)
[   36.944383] ACPI: Power Resource [FDDP] (off)
[   36.944414] ACPI: Power Resource [LPTP] (off)
[   36.944478] Linux Plug and Play Support v0.97 (c) Adam Belay
[   36.944527] pnp: PnP ACPI init
[   36.944538] ACPI: bus type pnp registered
[   36.948336] pnp: PnP ACPI: found 11 devices
[   36.948341] ACPI: ACPI bus type pnp unregistered
[   36.948348] PnPBIOS: Disabled by ACPI PNP
[   36.948699] PCI: Using ACPI for IRQ routing
[   36.948704] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   36.961465] NET: Registered protocol family 8
[   36.961468] NET: Registered protocol family 20
[   36.961584] AppArmor: AppArmor Filesystem Enabled
[   36.965430] Time: tsc clocksource has been installed.
[   37.004034] PCI: Bridge: 0000:00:01.0
[   37.004037]   IO window: disabled.
[   37.004044]   MEM window: cde00000-cfefffff
[   37.004049]   PREFETCH window: bdc00000-cdcfffff
[   37.004078] NET: Registered protocol family 2
[   37.041487] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[   37.042006] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[   37.044897] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[   37.046279] TCP: Hash tables configured (established 131072 bind 65536)
[   37.046285] TCP reno registered
[   37.057581] checking if image is initramfs... it is
[   37.504960] Switched to high resolution mode on CPU 0
[   37.916755] Freeing initrd memory: 7695k freed
[   37.917693] audit: initializing netlink socket (disabled)
[   37.917719] audit(1211108113.556:1): initialized
[   37.920605] VFS: Disk quotas dquot_6.5.1
[   37.920713] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   37.920944] io scheduler noop registered
[   37.920948] io scheduler anticipatory registered
[   37.920950] io scheduler deadline registered
[   37.920964] io scheduler cfq registered (default)
[   37.921043] Boot video device is 0000:01:00.0
[   37.921445] isapnp: Scanning for PnP cards...
[   38.274561] isapnp: No Plug & Play device found
[   38.316253] Real Time Clock Driver v1.12ac
[   38.316401] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   38.316574] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   38.316761] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[   38.317617] 00:08: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   38.318094] 00:09: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[   38.318568] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 11
[   38.318573] PCI: setting IRQ 11 as level-triggered
[   38.318577] ACPI: PCI Interrupt 0000:00:0b.0[A] -> Link [LNKB] -> GSI 11 (level, low) -> IRQ 11
[   38.318922] 0000:00:0b.0: ttyS2 at I/O 0xd400 (irq = 11) is a 16550A
[   38.319977] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   38.320387] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[   38.320542] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f03:PS2M] at 0x60,0x64 irq 1,12
[   38.320862] serio: i8042 KBD port at 0x60,0x64 irq 1
[   38.320869] serio: i8042 AUX port at 0x60,0x64 irq 12
[   38.332142] mice: PS/2 mouse device common for all mice
[   38.332312] EISA: Probing bus 0 at eisa.0
[   38.332353] EISA: Detected 0 cards.
[   38.332359] cpuidle: using governor ladder
[   38.332362] cpuidle: using governor menu
[   38.332586] NET: Registered protocol family 1
[   38.332627] Using IPI No-Shortcut mode
[   38.332681] registered taskstats version 1
[   38.332810]   Magic number: 8:296:932
[   38.333087] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[   38.333090] EDD information not available.
[   38.333734] Freeing unused kernel memory: 364k freed
[   38.360080] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[   39.665576] fuse init (API version 7.9)
[   40.529978] usbcore: registered new interface driver usbfs
[   40.530016] usbcore: registered new interface driver hub
[   40.542009] usbcore: registered new device driver usb
[   40.554871] SCSI subsystem initialized
[   40.617837] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
[   40.618155] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 10
[   40.618160] PCI: setting IRQ 10 as level-triggered
[   40.618164] ACPI: PCI Interrupt 0000:00:02.2[D] -> Link [LNKD] -> GSI 10 (level, low) -> IRQ 10
[   40.618187] ohci_hcd 0000:00:02.2: OHCI Host Controller
[   40.618624] ohci_hcd 0000:00:02.2: new USB bus registered, assigned bus number 1
[   40.618653] ohci_hcd 0000:00:02.2: irq 10, io mem 0xcfffe000
[   40.649774] Linux Tulip driver version 1.1.15 (Feb 27, 2007)
[   40.665755] libata version 3.00 loaded.
[   40.673476] USB Universal Host Controller Interface driver v3.0
[   40.675884] usb usb1: configuration #1 chosen from 1 choice
[   40.675920] hub 1-0:1.0: USB hub found
[   40.675934] hub 1-0:1.0: 3 ports detected
[   40.778007] ACPI: PCI Interrupt Link [LNKH] enabled at IRQ 5
[   40.778016] PCI: setting IRQ 5 as level-triggered
[   40.778020] ACPI: PCI Interrupt 0000:00:02.3[A] -> Link [LNKH] -> GSI 5 (level, low) -> IRQ 5
[   40.778044] ohci_hcd 0000:00:02.3: OHCI Host Controller
[   40.778088] ohci_hcd 0000:00:02.3: new USB bus registered, assigned bus number 2
[   40.778111] ohci_hcd 0000:00:02.3: irq 5, io mem 0xcffff000
[   40.826825] Floppy drive(s): fd0 is 1.44M
[   40.835731] usb usb2: configuration #1 chosen from 1 choice
[   40.835781] hub 2-0:1.0: USB hub found
[   40.835795] hub 2-0:1.0: 3 ports detected
[   40.849230] FDC 0 is a post-1991 82077
[   40.938075] ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 10
[   40.938083] ACPI: PCI Interrupt 0000:00:0d.0[A] -> Link [LNKC] -> GSI 10 (level, low) -> IRQ 10
[   40.938475] tulip0:  MII transceiver #1 config 1000 status 786d advertising 01e1.
[   40.942612] eth0: ADMtek Comet rev 17 at Port 0xd000, 00:50:bf:50:84:8c, IRQ 10.
[   40.942943] ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 11
[   40.942947] ACPI: PCI Interrupt 0000:00:13.0[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
[   40.942961] uhci_hcd 0000:00:13.0: UHCI Host Controller
[   40.943012] uhci_hcd 0000:00:13.0: new USB bus registered, assigned bus number 3
[   40.943044] uhci_hcd 0000:00:13.0: irq 11, io base 0x0000c800
[   40.943219] usb usb3: configuration #1 chosen from 1 choice
[   40.943260] hub 3-0:1.0: USB hub found
[   40.943271] hub 3-0:1.0: 2 ports detected
[   41.045577] ACPI: PCI Interrupt 0000:00:13.1[B] -> Link [LNKB] -> GSI 11 (level, low) -> IRQ 11
[   41.045598] uhci_hcd 0000:00:13.1: UHCI Host Controller
[   41.045635] uhci_hcd 0000:00:13.1: new USB bus registered, assigned bus number 4
[   41.045665] uhci_hcd 0000:00:13.1: irq 11, io base 0x0000cc00
[   41.045833] usb usb4: configuration #1 chosen from 1 choice
[   41.045872] hub 4-0:1.0: USB hub found
[   41.045882] hub 4-0:1.0: 2 ports detected
[   41.152283] ACPI: PCI Interrupt 0000:00:13.2[C] -> Link [LNKC] -> GSI 10 (level, low) -> IRQ 10
[   41.152306] ehci_hcd 0000:00:13.2: EHCI Host Controller
[   41.152365] ehci_hcd 0000:00:13.2: new USB bus registered, assigned bus number 5
[   41.152415] ehci_hcd 0000:00:13.2: irq 10, io mem 0xcfffdf00
[   41.161209] ehci_hcd 0000:00:13.2: USB 2.0 started, EHCI 0.95, driver 10 Dec 2004
[   41.161414] usb usb5: configuration #1 chosen from 1 choice
[   41.161457] hub 5-0:1.0: USB hub found
[   41.161471] hub 5-0:1.0: 4 ports detected
[   41.270452] pata_sis 0000:00:02.5: version 0.5.2
[   41.272114] scsi0 : pata_sis
[   41.273594] scsi1 : pata_sis
[   41.274463] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xff00 irq 14
[   41.274468] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xff08 irq 15
[   41.437489] ata1.00: ATA-4: Maxtor 90843D4, GAS54112, max UDMA/33
[   41.437497] ata1.00: 16481808 sectors, multi 16: LBA 
[   41.453293] ata1.00: configured for UDMA/33
[   41.924431] usb 5-1: new high speed USB device using ehci_hcd and address 2
[   41.936800] ata2.00: ATAPI: PLEXTOR CD-R   PX-W4824A, 1.01, max UDMA/33
[   41.936826] ata2.01: ATAPI: FX4010M, AM2A, max UDMA/33
[   42.068372] usb 5-1: configuration #1 chosen from 1 choice
[   42.108471] ata2.00: configured for UDMA/33
[   42.280326] ata2.01: configured for UDMA/33
[   42.280525] scsi 0:0:0:0: Direct-Access     ATA      Maxtor 90843D4   GAS5 PQ: 0 ANSI: 5
[   42.282065] scsi 1:0:0:0: CD-ROM            PLEXTOR  CD-R   PX-W4824A 1.01 PQ: 0 ANSI: 5
[   42.286854] scsi 1:0:1:0: CD-ROM            MITSUMI  CD-ROM FX4010M!B AM2A PQ: 0 ANSI: 5
[   42.301323] Driver 'sd' needs updating - please use bus_type methods
[   42.301476] sd 0:0:0:0: [sda] 16481808 512-byte hardware sectors (8439 MB)
[   42.301498] sd 0:0:0:0: [sda] Write Protect is off
[   42.301502] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   42.301531] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   42.301610] sd 0:0:0:0: [sda] 16481808 512-byte hardware sectors (8439 MB)
[   42.301626] sd 0:0:0:0: [sda] Write Protect is off
[   42.301629] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   42.301654] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   42.301659]  sda:<6>usb 5-2: new high speed USB device using ehci_hcd and address 3
[   42.312823] Driver 'sr' needs updating - please use bus_type methods
[   42.441185] usb 5-2: configuration #1 chosen from 1 choice
[   42.444844] usbcore: registered new interface driver libusual
[   42.454097] Initializing USB Mass Storage driver...
[   42.456284] scsi2 : SCSI emulation for USB Mass Storage devices
[   42.463948] usb-storage: device found at 2
[   42.463956] usb-storage: waiting for device to settle before scanning
[   42.476496] scsi3 : SCSI emulation for USB Mass Storage devices
[   42.488632] usbcore: registered new interface driver usb-storage
[   42.488643] USB Mass Storage support registered.
[   42.488816] usb-storage: device found at 3
[   42.488819] usb-storage: waiting for device to settle before scanning
[   43.412545]  sda1 sda2 < sda5 >
[   43.434967] sd 0:0:0:0: [sda] Attached SCSI disk
[   43.443647] sr0: scsi3-mmc drive: 40x/40x writer cd/rw xa/form2 cdda tray
[   43.443657] Uniform CD-ROM driver Revision: 3.20
[   43.443740] sr 1:0:0:0: Attached scsi CD-ROM sr0
[   43.446484] sd 0:0:0:0: Attached scsi generic sg0 type 0
[   43.446519] sr 1:0:0:0: Attached scsi generic sg1 type 5
[   43.446544] sr 1:0:1:0: Attached scsi generic sg2 type 5
[   43.448315] sr1: scsi3-mmc drive: 40x/40x cd/rw xa/form2 cdda tray
[   43.448429] sr 1:0:1:0: Attached scsi CD-ROM sr1
[   44.390074] Attempting manual resume
[   44.390082] swsusp: Resume From Partition 8:5
[   44.390084] PM: Checking swsusp image.
[   44.403167] PM: Resume from disk failed.
[   44.474620] kjournald starting.  Commit interval 5 seconds
[   44.474640] EXT3-fs: mounted filesystem with ordered data mode.
[   47.458931] usb-storage: device scan complete
[   47.459527] scsi 2:0:0:0: Direct-Access              USB Flash Memory 1.04 PQ: 0 ANSI: 0 CCS
[   47.460993] sd 2:0:0:0: [sdb] 2004992 512-byte hardware sectors (1027 MB)
[   47.461648] sd 2:0:0:0: [sdb] Write Protect is off
[   47.461653] sd 2:0:0:0: [sdb] Mode Sense: 23 00 00 00
[   47.461656] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[   47.464238] sd 2:0:0:0: [sdb] 2004992 512-byte hardware sectors (1027 MB)
[   47.464863] sd 2:0:0:0: [sdb] Write Protect is off
[   47.464867] sd 2:0:0:0: [sdb] Mode Sense: 23 00 00 00
[   47.464870] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[   47.464874]  sdb: sdb1
[   47.465828] sd 2:0:0:0: [sdb] Attached SCSI removable disk
[   47.465888] sd 2:0:0:0: Attached scsi generic sg3 type 0
[   47.483012] usb-storage: device scan complete
[   47.483873] scsi 3:0:0:0: Direct-Access     EPSON    Stylus Storage   1.00 PQ: 0 ANSI: 2
[   47.485522] sd 3:0:0:0: [sdc] Attached SCSI removable disk
[   47.485569] sd 3:0:0:0: Attached scsi generic sg4 type 0
[   58.151971] Linux agpgart interface v0.102
[   58.220084] agpgart: Detected SiS chipset - id:1845
[   58.225391] agpgart: AGP aperture is 64M @ 0xd0000000
[   58.292015] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   58.379850] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   58.462406] sis630_smbus 0000:00:02.0: SIS630 comp. bus not detected, module not inserted.
[   58.527671] sis96x_smbus 0000:00:02.1: SiS96x SMBus base address: 0x0c00
[   58.879499] input: Power Button (FF) as /devices/virtual/input/input2
[   58.891213] ACPI: Power Button (FF) [PWRF]
[   58.891411] input: Sleep Button (CM) as /devices/virtual/input/input3
[   58.907164] ACPI: Sleep Button (CM) [SLPB]
[   60.579393] nvidia: module license 'NVIDIA' taints kernel.
[   62.074795] input: PC Speaker as /devices/platform/pcspkr/input/input4
[   62.296375] usblp0: USB Bidirectional printer dev 3 if 1 alt 0 proto 2 vid 0x04B8 pid 0x0811
[   62.296407] usbcore: registered new interface driver usblp
[   62.578231] ACPI: PCI Interrupt 0000:00:02.7[C] -> Link [LNKC] -> GSI 10 (level, low) -> IRQ 10
[   62.899137] intel8x0_measure_ac97_clock: measured 55879 usecs
[   62.899146] intel8x0: clocking to 48000
[   63.024010] parport_pc 00:0a: reported by Plug and Play ACPI
[   63.024069] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
[   63.431278] ACPI: PCI Interrupt 0000:01:00.0[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
[   63.431926] NVRM: loading NVIDIA UNIX x86 Kernel Module  169.12  Thu Feb 14 17:53:07 PST 2008
[   63.790013] input: PS2++ Logitech MX Mouse as /devices/platform/i8042/serio1/input/input5
[   66.685387] lp0: using parport0 (interrupt-driven).
[   66.776972] Adding 393552k swap on /dev/sda5.  Priority:-1 extents:1 across:393552k
[   67.473958] EXT3 FS on sda1, internal journal
[   69.157899] ip_tables: (C) 2000-2006 Netfilter Core Team
[   69.902834] No dock devices found.
[   71.631552] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[   71.631561] apm: overridden by ACPI.
[   71.831196] ppdev: user-space parallel port driver
[   72.130688] audit(1211108148.571:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=4911 profile="/usr/sbin/cupsd" namespace="default"
[   74.890473] Bluetooth: Core ver 2.11
[   74.892004] NET: Registered protocol family 31
[   74.892013] Bluetooth: HCI device and connection manager initialized
[   74.892019] Bluetooth: HCI socket layer initialized
[   74.989895] Bluetooth: L2CAP ver 2.9
[   74.989904] Bluetooth: L2CAP socket layer initialized
[   75.223575] Bluetooth: RFCOMM socket layer initialized
[   75.223609] Bluetooth: RFCOMM TTY layer initialized
[   75.223612] Bluetooth: RFCOMM ver 1.8
[   77.435519] NET: Registered protocol family 17
[   77.605748] 0000:00:0d.0: tulip_stop_rxtx() failed (CSR5 0xfc664010 CSR6 0xff972117)
[   77.605766] eth0: Setting full-duplex based on MII#1 link partner capability of 45e1.
[   79.958098] agpgart: Found an AGP 2.0 compliant device at 0000:00:00.0.
[   79.958122] agpgart: Putting AGP V2 device at 0000:00:00.0 into 4x mode
[   79.958164] agpgart: Putting AGP V2 device at 0000:01:00.0 into 4x mode
[   84.046287] NET: Registered protocol family 10
[   84.047407] lo: Disabled Privacy Extensions
[   94.771632] eth0: no IPv6 routers present
[  116.469539] cdrom: sr0: mrw address space DMA selected
[  116.700152] cdrom: sr0: mrw address space DMA selected
[  117.057301] UDF-fs: No VRS found
[  117.061827] ISO 9660 Extensions: Microsoft Joliet Level 3
[  117.062652] ISOFS: changing to secondary root
[  406.467518] sr 1:0:1:0: [sr1] Device not ready: Sense Key : Not Ready [current] 
[  406.467531] sr 1:0:1:0: [sr1] Device not ready: Add. Sense: Medium not present
[  406.467541] end_request: I/O error, dev sr1, sector 0
[  406.467546] Buffer I/O error on device sr1, logical block 0
[  406.467553] Buffer I/O error on device sr1, logical block 1
[  406.467557] Buffer I/O error on device sr1, logical block 2
[  406.467561] Buffer I/O error on device sr1, logical block 3
[  406.467564] Buffer I/O error on device sr1, logical block 4
[  406.467567] Buffer I/O error on device sr1, logical block 5
[  406.467571] Buffer I/O error on device sr1, logical block 6
[  406.467574] Buffer I/O error on device sr1, logical block 7
[  406.469861] sr 1:0:1:0: [sr1] Device not ready: Sense Key : Not Ready [current] 
[  406.469868] sr 1:0:1:0: [sr1] Device not ready: Add. Sense: Medium not present
[  406.469875] end_request: I/O error, dev sr1, sector 0
[  406.469878] Buffer I/O error on device sr1, logical block 0
[  406.471140] sr 1:0:1:0: [sr1] Device not ready: Sense Key : Not Ready [current] 
[  406.471150] sr 1:0:1:0: [sr1] Device not ready: Add. Sense: Medium not present
[  406.471157] end_request: I/O error, dev sr1, sector 4
[  406.471162] Buffer I/O error on device sr1, logical block 1
[ 1113.866296] usb 5-1: USB disconnect, address 2
[ 1123.267511] usb 5-1: new high speed USB device using ehci_hcd and address 4
[ 1123.411524] usb 5-1: configuration #1 chosen from 1 choice
[ 1123.425445] scsi4 : SCSI emulation for USB Mass Storage devices
[ 1123.433084] usb-storage: device found at 4
[ 1123.433093] usb-storage: waiting for device to settle before scanning
[ 1128.426499] usb-storage: device scan complete
[ 1128.427530] scsi 4:0:0:0: Direct-Access              USB Flash Memory 1.04 PQ: 0 ANSI: 0 CCS
[ 1128.714971] sd 4:0:0:0: [sdb] 2004992 512-byte hardware sectors (1027 MB)
[ 1128.715920] sd 4:0:0:0: [sdb] Write Protect is off
[ 1128.715925] sd 4:0:0:0: [sdb] Mode Sense: 23 00 00 00
[ 1128.715928] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[ 1128.718459] sd 4:0:0:0: [sdb] 2004992 512-byte hardware sectors (1027 MB)
[ 1128.719251] sd 4:0:0:0: [sdb] Write Protect is off
[ 1128.719255] sd 4:0:0:0: [sdb] Mode Sense: 23 00 00 00
[ 1128.719258] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[ 1128.719264]  sdb: sdb1
[ 1128.720206] sd 4:0:0:0: [sdb] Attached SCSI removable disk
[ 1128.720275] sd 4:0:0:0: Attached scsi generic sg3 type 0




```

Also have not been able to mount from sudo mount

---

### Post by EXCiD3 on 2008-05-18
Is your drive in FAT32 format and when it is plugged in does it show up in /dev?

---

