---
title: "halt&#65306;unable to iterate IDE devices:no such files or directory"
date: 2008-02-17
forum: Hardware &amp; Laptops
---

### Post by kokerkov on 2008-02-17
i can't shutdown my pc properly,in x ,it only give some networkmanger libhal failed ,then nothing happen.
in recovery mode
```
halt
```
appears this 
```
halt&#65306;unable to iterate IDE devices:no such files or directory
```

---

### Post by kokerkov on 2008-02-17
```
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000001ffec000 (usable)
[    0.000000]  BIOS-e820: 000000001ffec000 - 000000001ffef000 (ACPI data)
[    0.000000]  BIOS-e820: 000000001ffef000 - 000000001ffff000 (reserved)
[    0.000000]  BIOS-e820: 000000001ffff000 - 0000000020000000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000ffff0000 - 0000000100000000 (reserved)
[    0.000000] 0MB HIGHMEM available.
[    0.000000] 511MB LOWMEM available.
[    0.000000] Entering add_active_range(0, 0, 131052) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   131052
[    0.000000]   HighMem    131052 ->   131052
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   131052
[    0.000000] On node 0 totalpages: 131052
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 991 pages used for memmap
[    0.000000]   Normal zone: 125965 pages, LIFO batch:31
[    0.000000]   HighMem zone: 0 pages used for memmap
[    0.000000] DMI 2.3 present.
[    0.000000] ASUS P4B266 detected: force use of acpi=ht
[    0.000000] ACPI: RSDP signature @ 0xC00F72A0 checksum 0
[    0.000000] ACPI: RSDP 000F72A0, 0014 (r0 ASUS  )
[    0.000000] ACPI: RSDT 1FFEC000, 0030 (r1 ASUS   P4B266-C 42302E31 MSFT 31313031)
[    0.000000] ACPI: FACP 1FFEC100, 0074 (r1 ASUS   P4B266-C 42302E31 MSFT 31313031)
[    0.000000] ACPI: DSDT 1FFEC180, 24AD (r1   ASUS P4B266-C     1000 MSFT  100000B)
[    0.000000] ACPI: FACS 1FFFF000, 0040
[    0.000000] ACPI: BOOT 1FFEC040, 0028 (r1 ASUS   P4B266-C 42302E31 MSFT 31313031)
[    0.000000] ACPI: APIC 1FFEC080, 005A (r1 ASUS   P4B266-C 42302E31 MSFT 31313031)
[    0.000000] ACPI: PM-Timer IO Port: 0xe408
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] Processor #0 15:2 APIC version 20
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] Allocating PCI resources starting at 30000000 (gap: 20000000:dec00000)
[    0.000000] Built 1 zonelists.  Total pages: 130029
[    0.000000] Kernel command line: root=UUID=ca11a4bc-50b5-4d49-ab28-142da2603032 ro quiet splash locale=zh_CN
[    0.000000] Found and enabled local APIC!
[    0.000000] mapped APIC to ffffd000 (fee00000)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 2048 (order: 11, 8192 bytes)
[    0.000000] Detected 2017.981 MHz processor.
[   30.614267] Console: colour VGA+ 80x25
[   30.614769] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
[   30.615249] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
[   30.630898] Memory: 508172k/524208k available (2015k kernel code, 15440k reserved, 915k data, 364k init, 0k highmem)
[   30.630911] virtual kernel memory layout:
[   30.630913]     fixmap  : 0xfff4d000 - 0xfffff000   ( 712 kB)
[   30.630914]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   30.630916]     vmalloc : 0xe0800000 - 0xff7fe000   ( 495 MB)
[   30.630917]     lowmem  : 0xc0000000 - 0xdffec000   ( 511 MB)
[   30.630918]       .init : 0xc03e3000 - 0xc043e000   ( 364 kB)
[   30.630920]       .data : 0xc02f7e86 - 0xc03dce84   ( 915 kB)
[   30.630921]       .text : 0xc0100000 - 0xc02f7e86   (2015 kB)
[   30.630925] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   30.630976] SLUB: Genslabs=22, HWalign=64, Order=0-1, MinObjects=4, CPUs=1, Nodes=1
[   30.710940] Calibrating delay using timer specific routine.. 4040.05 BogoMIPS (lpj=8080110)
[   30.710973] Security Framework v1.0.0 initialized
[   30.710982] SELinux:  Disabled at boot.
[   30.710999] Mount-cache hash table entries: 512
[   30.711184] CPU: After generic identify, caps: 3febfbff 00000000 00000000 00000000 00000000 00000000 00000000
[   30.711201] CPU: Trace cache: 12K uops, L1 D cache: 8K
[   30.711205] CPU: L2 cache: 512K
[   30.711208] CPU: Hyper-Threading is disabled
[   30.711212] CPU: After all inits, caps: 3febfbff 00000000 00000000 0000b080 00000000 00000000 00000000
[   30.711230] Compat vDSO mapped to ffffe000.
[   30.711247] Checking 'hlt' instruction... OK.
[   30.727121] SMP alternatives: switching to UP code
[   30.727398] Freeing SMP alternatives: 11k freed
[   30.727840] Early unpacking initramfs... done
[   31.151043] CPU0: Intel(R) Pentium(R) 4 CPU 2.00GHz stepping 04
[   31.151104] Total of 1 processors activated (4040.05 BogoMIPS).
[   31.258565] Brought up 1 CPUs
[   31.258744] Booting paravirtualized kernel on bare hardware
[   31.258828] Time: 16:10:56  Date: 01/17/108
[   31.258862] NET: Registered protocol family 16
[   31.258994] EISA bus registered
[   31.260801] PCI: PCI BIOS revision 2.10 entry at 0xf1070, last bus=2
[   31.260804] PCI: Using configuration type 1
[   31.260806] Setting up standard PCI resources
[   31.268339] ACPI: Interpreter disabled.
[   31.268345] Linux Plug and Play Support v0.97 (c) Adam Belay
[   31.268357] pnp: PnP ACPI: disabled
[   31.268363] PnPBIOS: Scanning system for PnP BIOS support...
[   31.268404] PnPBIOS: Found PnP BIOS installation structure at 0xc00fbf70
[   31.268408] PnPBIOS: PnP BIOS version 1.0, entry 0xf0000:0xbfa0, dseg 0xf0000
[   31.269282] PnPBIOS: 16 nodes reported by PnP BIOS; 16 recorded by driver
[   31.269356] PCI: Probing PCI hardware
[   31.269374] PCI: Probing PCI hardware (bus 00)
[   31.269630] PCI: Enabled i801 SMBus device
[   31.269638] PCI quirk: region e400-e47f claimed by ICH4 ACPI/GPIO/TCO
[   31.269642] PCI quirk: region ec00-ec3f claimed by ICH4 GPIO
[   31.270414] PCI: Transparent bridge - 0000:00:1e.0
[   31.271229] PCI: Using IRQ router PIIX/ICH [8086/2440] at 0000:00:1f.0
[   31.279179] NET: Registered protocol family 8
[   31.279182] NET: Registered protocol family 20
[   31.279277] pnp: 00:07: iomem range 0x0-0x9ffff could not be reserved
[   31.279282] pnp: 00:07: iomem range 0x100000-0x1fffffff could not be reserved
[   31.279285] pnp: 00:07: iomem range 0xe8000-0xeffff has been reserved
[   31.279289] pnp: 00:07: iomem range 0xf0000-0xf3fff could not be reserved
[   31.279304] pnp: 00:11: ioport range 0x290-0x297 has been reserved
[   31.279307] pnp: 00:11: ioport range 0x3f0-0x3f1 has been reserved
[   31.279311] pnp: 00:11: ioport range 0xe400-0xe47f has been reserved
[   31.279315] pnp: 00:11: ioport range 0xec00-0xec3f has been reserved
[   31.282500] Time: tsc clocksource has been installed.
[   31.309757] PCI: Bridge: 0000:00:01.0
[   31.309760]   IO window: disabled.
[   31.309766]   MEM window: ee000000-efdfffff
[   31.309771]   PREFETCH window: eff00000-f7ffffff
[   31.309780] PCI: Bridge: 0000:00:1e.0
[   31.309784]   IO window: d000-dfff
[   31.309791]   MEM window: ec000000-edffffff
[   31.309796]   PREFETCH window: efe00000-efefffff
[   31.309819] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[   31.309837] NET: Registered protocol family 2
[   31.346511] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
[   31.346577] TCP established hash table entries: 16384 (order: 5, 196608 bytes)
[   31.346758] TCP bind hash table entries: 16384 (order: 5, 131072 bytes)
[   31.346883] TCP: Hash tables configured (established 16384 bind 16384)
[   31.346888] TCP reno registered
[   31.358626] checking if image is initramfs... it is
[   31.810093] Switched to high resolution mode on CPU 0
[   32.196022] Freeing initrd memory: 7065k freed
[   32.196211] Simple Boot Flag at 0x3a set to 0x1
[   32.196512] audit: initializing netlink socket (disabled)
[   32.196533] audit(1203264657.048:1): initialized
[   32.199452] VFS: Disk quotas dquot_6.5.1
[   32.199534] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   32.199731] io scheduler noop registered
[   32.199734] io scheduler anticipatory registered
[   32.199737] io scheduler deadline registered
[   32.199758] io scheduler cfq registered (default)
[   32.199813] Boot video device is 0000:01:00.0
[   32.200039] isapnp: Scanning for PnP cards...
[   32.553962] isapnp: No Plug & Play device found
[   32.593650] Real Time Clock Driver v1.12ac
[   32.593748] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   32.593854] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   32.594116] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[   32.594915] 00:02: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   32.595328] 00:03: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[   32.596615] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   32.596940] input: Macintosh mouse button emulation as /class/input/input0
[   32.597068] PNP: PS/2 Controller [PNP0303,PNP0f13] at 0x60,0x64 irq 1,12
[   32.600536] serio: i8042 KBD port at 0x60,0x64 irq 1
[   32.600546] serio: i8042 AUX port at 0x60,0x64 irq 12
[   32.600825] mice: PS/2 mouse device common for all mice
[   32.600985] EISA: Probing bus 0 at eisa.0
[   32.601029] EISA: Detected 0 cards.
[   32.601167] TCP cubic registered
[   32.601184] NET: Registered protocol family 1
[   32.601263] Testing NMI watchdog ... OK.
[   32.680652] Using IPI No-Shortcut mode
[   32.680777]   Magic number: 12:564:186
[   32.681580] Freeing unused kernel memory: 364k freed
[   32.737258] input: AT Translated Set 2 keyboard as /class/input/input1
[   33.979175] AppArmor: AppArmor initialized<5>audit(1203264659.048:2):  type=1505 info="AppArmor initialized" pid=1125
[   33.991725] fuse init (API version 7.8)
[   33.998548] Failure registering capabilities with primary security module.
[   34.028933] thermal: Unknown symbol acpi_processor_set_thermal_limit
[   34.818825] SCSI subsystem initialized
[   34.827031] libata version 2.21 loaded.
[   34.832309] ata_piix 0000:00:1f.1: version 2.11
[   34.832398] PCI: Setting latency timer of device 0000:00:1f.1 to 64
[   34.832513] scsi0 : ata_piix
[   34.832572] scsi1 : ata_piix
[   34.832608] ata1: PATA max UDMA/100 cmd 0x000101f0 ctl 0x000103f6 bmdma 0x0001b800 irq 14
[   34.832613] ata2: PATA max UDMA/100 cmd 0x00010170 ctl 0x00010376 bmdma 0x0001b808 irq 15
[   34.851577] usbcore: registered new interface driver usbfs
[   34.851615] usbcore: registered new interface driver hub
[   34.851650] usbcore: registered new device driver usb
[   34.899553] USB Universal Host Controller Interface driver v3.0
[   34.956886] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
[   34.979176] 8139too Fast Ethernet driver 0.9.28
[   34.995597] ata1.00: ATA-5: ST360021A, 3.99, max UDMA/100
[   34.995603] ata1.00: 117231408 sectors, multi 16: LBA
[   35.003472] ata1.00: configured for UDMA/100
[   35.012220] Floppy drive(s): fd0 is 1.44M
[   35.079491] FDC 0 is a post-1991 82077
[   35.331012] ata2.01: ATAPI: ASUS    CD-S520/A, 2.0K, max UDMA/33
[   35.502850] ata2.01: configured for UDMA/33
[   35.503020] scsi 0:0:0:0: Direct-Access     ATA      ST360021A        3.99 PQ: 0 ANSI: 5
[   40.997594] ata2.01: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
[   40.997606] ata2.01: cmd a0/00:00:00:00:20/00:00:00:00:00/b0 tag 0 cdb 0x12 data 36 in
[   40.997610]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout)
[   41.948682] ata2: soft resetting port
[   42.432580] ata2.01: configured for UDMA/33
[   42.432602] ata2: EH complete
[   42.432831] scsi 1:0:1:0: CD-ROM            ASUS     CD-S520/A        2.0K PQ: 0 ANSI: 5
[   42.433515] PCI: setting IRQ 10 as level-triggered
[   42.433522] PCI: Found IRQ 10 for device 0000:00:1f.2
[   42.433557] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[   42.433562] uhci_hcd 0000:00:1f.2: UHCI Host Controller
[   42.433942] uhci_hcd 0000:00:1f.2: new USB bus registered, assigned bus number 1
[   42.433977] uhci_hcd 0000:00:1f.2: irq 10, io base 0x0000b400
[   42.434531] usb usb1: configuration #1 chosen from 1 choice
[   42.434737] hub 1-0:1.0: USB hub found
[   42.434748] hub 1-0:1.0: 2 ports detected
[   42.457583] sd 0:0:0:0: [sda] 117231408 512-byte hardware sectors (60022 MB)
[   42.458859] sd 0:0:0:0: [sda] Write Protect is off
[   42.458865] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   42.458906] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   42.458995] sd 0:0:0:0: [sda] 117231408 512-byte hardware sectors (60022 MB)
[   42.459010] sd 0:0:0:0: [sda] Write Protect is off
[   42.459013] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   42.459037] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   42.459044]  sda: sda1 sda2 < sda5 sda6 sda7 sda8 >
[   42.523704] sd 0:0:0:0: [sda] Attached SCSI disk
[   42.529218] sd 0:0:0:0: Attached scsi generic sg0 type 0
[   42.529247] scsi 1:0:1:0: Attached scsi generic sg1 type 5
[   42.536368] PCI: setting IRQ 9 as level-triggered
[   42.536375] PCI: Found IRQ 9 for device 0000:00:1f.4
[   42.536396] PCI: Sharing IRQ 9 with 0000:02:0b.0
[   42.536414] PCI: Setting latency timer of device 0000:00:1f.4 to 64
[   42.536419] uhci_hcd 0000:00:1f.4: UHCI Host Controller
[   42.536451] uhci_hcd 0000:00:1f.4: new USB bus registered, assigned bus number 2
[   42.536481] uhci_hcd 0000:00:1f.4: irq 9, io base 0x0000b000
[   42.536625] usb usb2: configuration #1 chosen from 1 choice
[   42.536667] hub 2-0:1.0: USB hub found
[   42.536680] hub 2-0:1.0: 2 ports detected
[   42.561781] sr0: scsi3-mmc drive: 52x/52x cd/rw xa/form2 cdda tray
[   42.561789] Uniform CD-ROM driver Revision: 3.20
[   42.562193] sr 1:0:1:0: Attached scsi CD-ROM sr0
[   42.640377] PCI: Found IRQ 9 for device 0000:02:0b.0
[   42.640394] PCI: Sharing IRQ 9 with 0000:00:1f.4
[   42.640418] ohci_hcd 0000:02:0b.0: OHCI Host Controller
[   42.640456] ohci_hcd 0000:02:0b.0: new USB bus registered, assigned bus number 3
[   42.640474] ohci_hcd 0000:02:0b.0: irq 9, io mem 0xed800000
[   42.725972] usb usb3: configuration #1 chosen from 1 choice
[   42.726015] hub 3-0:1.0: USB hub found
[   42.726029] hub 3-0:1.0: 3 ports detected
[   42.828080] PCI: setting IRQ 5 as level-triggered
[   42.828086] PCI: Found IRQ 5 for device 0000:02:0b.1
[   42.828126] ohci_hcd 0000:02:0b.1: OHCI Host Controller
[   42.828162] ohci_hcd 0000:02:0b.1: new USB bus registered, assigned bus number 4
[   42.828182] ohci_hcd 0000:02:0b.1: irq 5, io mem 0xed000000
[   42.913863] usb usb4: configuration #1 chosen from 1 choice
[   42.913905] hub 4-0:1.0: USB hub found
[   42.913919] hub 4-0:1.0: 2 ports detected
[   43.016056] PCI: Found IRQ 9 for device 0000:02:0b.2
[   43.016078] PCI: Sharing IRQ 9 with 0000:02:03.0
[   43.016087] PCI: Sharing IRQ 9 with 0000:02:0d.0
[   43.016100] ehci_hcd 0000:02:0b.2: EHCI Host Controller
[   43.016138] ehci_hcd 0000:02:0b.2: new USB bus registered, assigned bus number 5
[   43.039721] ehci_hcd 0000:02:0b.2: irq 9, io mem 0xec800000
[   43.039733] ehci_hcd 0000:02:0b.2: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   43.039902] usb usb5: configuration #1 chosen from 1 choice
[   43.039944] hub 5-0:1.0: USB hub found
[   43.039960] hub 5-0:1.0: 5 ports detected
[   43.112682] Attempting manual resume
[   43.112688] swsusp: Resume From Partition 8:7
[   43.112690] PM: Checking swsusp image.
[   43.131830] PM: Resume from disk failed.
[   43.143893] PCI: Found IRQ 9 for device 0000:02:0d.0
[   43.143915] PCI: Sharing IRQ 9 with 0000:02:03.0
[   43.143923] PCI: Sharing IRQ 9 with 0000:02:0b.2
[   43.144306] eth0: RealTek RTL8139 at 0xe08c2000, 00:0a:eb:13:64:b2, IRQ 9
[   43.144309] eth0:  Identified 8139 chip type 'RTL-8100B/8139D'
[   43.147690] 8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)
[   43.194301] kjournald starting.  Commit interval 5 seconds
[   43.194318] EXT3-fs: mounted filesystem with ordered data mode.
[   49.856174] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[   51.518120] NET: Registered protocol family 17
[   52.007651] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   52.011738] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   52.190255] intel_rng: FWH not detected
[   52.236718] parport_pc 00:01: reported by Plug and Play BIOS
[   52.236747] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE,EPP]
[   52.249735] iTCO_vendor_support: vendor-support=0
[   52.251363] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.01 (21-Jan-2007)
[   52.251455] iTCO_wdt: failed to reset NO_REBOOT flag, reboot disabled by hardware
[   52.251465] iTCO_wdt: No card detected
[   52.893117] Linux agpgart interface v0.102 (c) Dave Jones
[   52.989728] agpgart: Detected an Intel 845G Chipset.
[   52.995269] agpgart: AGP aperture is 64M @ 0xf8000000
[   53.137031] input: PC Speaker as /class/input/input2
[   53.295102] logips2pp: Detected unknown logitech mouse model 89
[   53.489064] nvidia: module license 'NVIDIA' taints kernel.
[   53.747065] PCI: setting IRQ 11 as level-triggered
[   53.747072] PCI: Found IRQ 11 for device 0000:01:00.0
[   53.747471] NVRM: loading NVIDIA UNIX x86 Kernel Module  100.14.19  Wed Sep 12 14:12:24 PDT 2007
[   53.833162] input: ImExPS/2 Logitech Explorer Mouse as /class/input/input3
[   54.525372] PCI: Found IRQ 9 for device 0000:02:03.0
[   54.525398] PCI: Sharing IRQ 9 with 0000:02:0b.2
[   54.525403] PCI: Sharing IRQ 9 with 0000:02:0d.0
[   55.574121] lp0: using parport0 (interrupt-driven).
[   55.630922] Adding 1020088k swap on /dev/sda7.  Priority:-1 extents:1 across:1020088k
[   58.923599] EXT3 FS on sda8, internal journal
[   68.378257] acpi_cpufreq: Unknown symbol acpi_processor_notify_smm
[   68.378320] acpi_cpufreq: Unknown symbol acpi_processor_unregister_performance
[   68.378488] acpi_cpufreq: Unknown symbol acpi_processor_preregister_performance
[   68.378568] acpi_cpufreq: Unknown symbol acpi_processor_register_performance
[   69.709358] ppdev: user-space parallel port driver
[   69.977268] audit(1203235895.307:3):  type=1503 operation="inode_permission" requested_mask="a" denied_mask="a" name="/dev/tty" pid=4492 profile="/usr/sbin/cupsd"
[   70.079333] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[   70.528171] Failure registering capabilities with primary security module.
[   70.843224] Bluetooth: Core ver 2.11
[   70.843405] NET: Registered protocol family 31
[   70.843409] Bluetooth: HCI device and connection manager initialized
[   70.843414] Bluetooth: HCI socket layer initialized
[   70.871979] Bluetooth: L2CAP ver 2.8
[   70.871985] Bluetooth: L2CAP socket layer initialized
[   71.104003] Bluetooth: RFCOMM socket layer initialized
[   71.104157] Bluetooth: RFCOMM TTY layer initialized
[   71.104161] Bluetooth: RFCOMM ver 1.8
[   73.660142] agpgart: Found an AGP 2.0 compliant device at 0000:00:00.0.
[   73.660166] agpgart: Putting AGP V2 device at 0000:00:00.0 into 4x mode
[   73.660187] agpgart: Putting AGP V2 device at 0000:01:00.0 into 4x mode
[   79.606725] NET: Registered protocol family 10
[   79.607181] lo: Disabled Privacy Extensions
[   90.499980] eth0: no IPv6 routers present
[  175.573223] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[  186.451602] eth0: no IPv6 routers present
[  190.185843] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[  200.681523] eth0: no IPv6 routers present 
```
it's what "dmesg"tells me,please help!

---

### Post by Yellow Pasque on 2008-02-17
It's been reported already. The developer is asking if the problem is still occurring with the latest software. If it is, you could do a great service to the community by filling in the information the developer is asking for.
> If so, please attach your /var/log/syslog and /var/log/daemon.log to this bug. Thanks, - Alexander
[https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/138691](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/138691)

---

