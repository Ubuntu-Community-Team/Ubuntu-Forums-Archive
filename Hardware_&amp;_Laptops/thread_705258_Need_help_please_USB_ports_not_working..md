---
title: "Need help please USB ports not working."
date: 2008-02-23
forum: Hardware &amp; Laptops
---

### Post by pyrotechniccb on 2008-02-23
I did a search + was unable to find any info to fix my problem. But I can post the info you asked everyone else for. I can see that unlike most people my usb devices aren't showing up at all. Any help would be great.

lsusb :

Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  

dmesg :

```
[    0.000000] Linux version 2.6.22-14-generic (buildd@terranova) (gcc version 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)) #1 SMP Tue Feb 12 07:42:25 UTC 2008 (Ubuntu 2.6.22-14.52-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f000 (usable)
[    0.000000]  BIOS-e820: 000000000009f000 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000dc000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 0000000017f60000 (usable)
[    0.000000]  BIOS-e820: 0000000017f60000 - 0000000017f7a000 (ACPI data)
[    0.000000]  BIOS-e820: 0000000017f7a000 - 0000000017f7c000 (ACPI NVS)
[    0.000000]  BIOS-e820: 0000000017f7c000 - 0000000018000000 (reserved)
[    0.000000]  BIOS-e820: 00000000ff800000 - 0000000100000000 (reserved)
[    0.000000] 0MB HIGHMEM available.
[    0.000000] 383MB LOWMEM available.
[    0.000000] Entering add_active_range(0, 0, 98144) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->    98144
[    0.000000]   HighMem     98144 ->    98144
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->    98144
[    0.000000] On node 0 totalpages: 98144
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 734 pages used for memmap
[    0.000000]   Normal zone: 93314 pages, LIFO batch:31
[    0.000000]   HighMem zone: 0 pages used for memmap
[    0.000000] DMI present.
[    0.000000] ACPI: RSDP signature @ 0xC00F73D0 checksum 0
[    0.000000] ACPI: RSDP 000F73D0, 0024 (r2 IBM   )
[    0.000000] ACPI: XSDT 17F6F242, 0044 (r1 IBM    TP-1E        1033  LTP        0)
[    0.000000] ACPI: FACP 17F6F286, 0081 (r1 IBM    TP-1E        1033 IBM         1)
[    0.000000] ACPI: DSDT 17F6F36D, AC1A (r1 IBM    TP-1E        1033 MSFT  100000D)
[    0.000000] ACPI: FACS 17F7B000, 0040
[    0.000000] ACPI: SSDT 17F6F33A, 0033 (r1 IBM    TP-1E        1033 MSFT  100000D)
[    0.000000] ACPI: ECDT 17F79F87, 0051 (r1 IBM    TP-1E        1033 IBM         1)
[    0.000000] ACPI: BOOT 17F79FD8, 0028 (r1 IBM    TP-1E        1033  LTP        1)
[    0.000000] ACPI: PM-Timer IO Port: 0x1008
[    0.000000] Allocating PCI resources starting at 20000000 (gap: 18000000:e7800000)
[    0.000000] Built 1 zonelists.  Total pages: 97378
[    0.000000] Kernel command line: root=UUID=7d1c7b04-94ee-4d53-b2f8-538bac3fc555 ro quiet splash locale=en_US
[    0.000000] Local APIC disabled by BIOS -- you can enable it with "lapic"
[    0.000000] mapped APIC to ffffd000 (0130c000)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 2048 (order: 11, 8192 bytes)
[    0.000000] Detected 1199.021 MHz processor.
[    7.531874] Console: colour dummy device 80x25
[    7.532294] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
[    7.532903] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
[    7.555262] Memory: 377612k/392576k available (2015k kernel code, 14420k reserved, 915k data, 364k init, 0k highmem)
[    7.555280] virtual kernel memory layout:
[    7.555282]     fixmap  : 0xfff4d000 - 0xfffff000   ( 712 kB)
[    7.555284]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[    7.555287]     vmalloc : 0xd8800000 - 0xff7fe000   ( 623 MB)
[    7.555289]     lowmem  : 0xc0000000 - 0xd7f60000   ( 383 MB)
[    7.555292]       .init : 0xc03e3000 - 0xc043e000   ( 364 kB)
[    7.555294]       .data : 0xc02f7e86 - 0xc03dce84   ( 915 kB)
[    7.555296]       .text : 0xc0100000 - 0xc02f7e86   (2015 kB)
[    7.555302] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[    7.555371] SLUB: Genslabs=22, HWalign=32, Order=0-1, MinObjects=4, CPUs=1, Nodes=1
[    7.635395] Calibrating delay using timer specific routine.. 2399.82 BogoMIPS (lpj=4799650)
[    7.635442] Security Framework v1.0.0 initialized
[    7.635456] SELinux:  Disabled at boot.
[    7.635483] Mount-cache hash table entries: 512
[    7.635694] CPU: After generic identify, caps: 0383f9ff 00000000 00000000 00000000 00000000 00000000 00000000
[    7.635712] CPU: L1 I cache: 16K, L1 D cache: 16K
[    7.635717] CPU: L2 cache: 512K
[    7.635722] CPU: After all inits, caps: 0383f9ff 00000000 00000000 00000040 00000000 00000000 00000000
[    7.635738] Compat vDSO mapped to ffffe000.
[    7.635756] Checking 'hlt' instruction... OK.
[    7.651506] SMP alternatives: switching to UP code
[    7.651706] Freeing SMP alternatives: 11k freed
[    7.652092] Early unpacking initramfs... done
[    8.174086] ACPI: Core revision 20070126
[    8.174353] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[    8.181422] ACPI: setting ELCR to 0200 (from 0800)
[    8.194706] CPU0: Intel(R) Pentium(R) III Mobile CPU      1200MHz stepping 01
[    8.194716] SMP motherboard not detected.
[    8.194721] Local APIC not detected. Using dummy APIC emulation.
[    8.194795] Brought up 1 CPUs
[    8.195029] Booting paravirtualized kernel on bare hardware
[    8.195120] Time:  7:31:43  Date: 01/22/108
[    8.195172] NET: Registered protocol family 16
[    8.195365] EISA bus registered
[    8.195426] ACPI: bus type pci registered
[    8.195732] PCI: PCI BIOS revision 2.10 entry at 0xfd8fe, last bus=8
[    8.195737] PCI: Using configuration type 1
[    8.195740] Setting up standard PCI resources
[    8.201657] ACPI: EC: Found ECDT
[    8.212845] ACPI: Interpreter enabled
[    8.212852] ACPI: (supports S0 S3 S4 S5)
[    8.212879] ACPI: Using PIC for interrupt routing
[    8.224753] ACPI: EC: GPE=0x1c, ports=0x66, 0x62
[    8.224833] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    8.224844] PCI: Probing PCI hardware (bus 00)
[    8.225163] PCI quirk: region 1000-107f claimed by ICH4 ACPI/GPIO/TCO
[    8.225169] PCI quirk: region 1180-11bf claimed by ICH4 GPIO
[    8.225553] PCI: Firmware left 0000:02:08.0 e100 interrupts enabled, disabling
[    8.225610] PCI: Transparent bridge - 0000:00:1e.0
[    8.225755] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    8.225849] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.AGP_._PRT]
[    8.225885] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCI1._PRT]
[    8.230307] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 9 10 *11)
[    8.230621] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 9 10 *11)
[    8.230930] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 9 10 *11)
[    8.231238] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 9 10 *11)
[    8.231608] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 9 10 *11)
[    8.231891] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 9 10 11) *0, disabled.
[    8.232176] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 9 10 11) *0, disabled.
[    8.232459] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 9 10 11) *0, disabled.
[    8.232925] ACPI: Power Resource [PUBS] (off)
[    8.232944] Linux Plug and Play Support v0.97 (c) Adam Belay
[    8.232970] pnp: PnP ACPI init
[    8.232987] ACPI: bus type pnp registered
[    8.238790] pnp: PnP ACPI: found 13 devices
[    8.238795] ACPI: ACPI bus type pnp unregistered
[    8.238801] PnPBIOS: Disabled by ACPI PNP
[    8.238897] PCI: Using ACPI for IRQ routing
[    8.238903] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[    8.246109] NET: Registered protocol family 8
[    8.246113] NET: Registered protocol family 20
[    8.246230] pnp: 00:00: iomem range 0x0-0x9ffff could not be reserved
[    8.246236] pnp: 00:00: iomem range 0xc0000-0xc3fff could not be reserved
[    8.246241] pnp: 00:00: iomem range 0xc4000-0xc7fff could not be reserved
[    8.246246] pnp: 00:00: iomem range 0xc8000-0xcbfff could not be reserved
[    8.247390] Time: tsc clocksource has been installed.
[    8.276790] PCI: Bridge: 0000:00:01.0
[    8.276794]   IO window: 3000-3fff
[    8.276799]   MEM window: c0100000-c01fffff
[    8.276805]   PREFETCH window: e0000000-e7ffffff
[    8.276815] PCI: Bus 3, cardbus bridge: 0000:02:00.0
[    8.276819]   IO window: 00004000-000040ff
[    8.276824]   IO window: 00004400-000044ff
[    8.276830]   PREFETCH window: e8000000-ebffffff
[    8.276835]   MEM window: c4000000-c7ffffff
[    8.276840] PCI: Bus 7, cardbus bridge: 0000:02:00.1
[    8.276844]   IO window: 00004800-000048ff
[    8.276849]   IO window: 00004c00-00004cff
[    8.276855]   PREFETCH window: ec000000-efffffff
[    8.276860]   MEM window: c8000000-cbffffff
[    8.276865] PCI: Bridge: 0000:00:1e.0
[    8.276869]   IO window: 4000-8fff
[    8.276876]   MEM window: c0200000-cfffffff
[    8.276881]   PREFETCH window: e8000000-efffffff
[    8.276899] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[    8.277503] ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 11
[    8.277509] PCI: setting IRQ 11 as level-triggered
[    8.277514] ACPI: PCI Interrupt 0000:02:00.0[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
[    8.278047] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 11
[    8.278052] ACPI: PCI Interrupt 0000:02:00.1[B] -> Link [LNKB] -> GSI 11 (level, low) -> IRQ 11
[    8.278078] NET: Registered protocol family 2
[    8.315449] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
[    8.315533] TCP established hash table entries: 16384 (order: 5, 196608 bytes)
[    8.315961] TCP bind hash table entries: 16384 (order: 5, 131072 bytes)
[    8.316317] TCP: Hash tables configured (established 16384 bind 16384)
[    8.316323] TCP reno registered
[    8.327683] checking if image is initramfs... it is
[    8.779423] Switched to high resolution mode on CPU 0
[    9.316106] Freeing initrd memory: 7068k freed
[    9.316404] Simple Boot Flag at 0x35 set to 0x1
[    9.316813] audit: initializing netlink socket (disabled)
[    9.316841] audit(1203665503.688:1): initialized
[    9.320723] VFS: Disk quotas dquot_6.5.1
[    9.320835] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    9.321043] io scheduler noop registered
[    9.321048] io scheduler anticipatory registered
[    9.321052] io scheduler deadline registered
[    9.321088] io scheduler cfq registered (default)
[    9.321162] Boot video device is 0000:01:00.0
[    9.321453] isapnp: Scanning for PnP cards...
[    9.674363] isapnp: No Plug & Play device found
[    9.724394] Real Time Clock Driver v1.12ac
[    9.724561] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[    9.724665] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a NS16550A
[    9.725809] 00:0a: ttyS0 at I/O 0x3f8 (irq = 4) is a NS16550A
[    9.726124] PCI: Enabling device 0000:00:1f.6 (0000 -> 0001)
[    9.726141] ACPI: PCI Interrupt 0000:00:1f.6[B] -> Link [LNKB] -> GSI 11 (level, low) -> IRQ 11
[    9.726154] ACPI: PCI interrupt for device 0000:00:1f.6 disabled
[    9.727132] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[    9.727547] input: Macintosh mouse button emulation as /class/input/input0
[    9.727689] PNP: PS/2 Controller [PNP0303:KBD,PNP0f13:MOU] at 0x60,0x64 irq 1,12
[    9.735165] serio: i8042 KBD port at 0x60,0x64 irq 1
[    9.735176] serio: i8042 AUX port at 0x60,0x64 irq 12
[    9.735502] mice: PS/2 mouse device common for all mice
[    9.735693] EISA: Probing bus 0 at eisa.0
[    9.735705] Cannot allocate resource for EISA slot 1
[    9.735710] Cannot allocate resource for EISA slot 2
[    9.735714] Cannot allocate resource for EISA slot 3
[    9.735718] Cannot allocate resource for EISA slot 4
[    9.735722] Cannot allocate resource for EISA slot 5
[    9.735726] Cannot allocate resource for EISA slot 6
[    9.735730] Cannot allocate resource for EISA slot 7
[    9.735733] Cannot allocate resource for EISA slot 8
[    9.735737] EISA: Detected 0 cards.
[    9.735919] TCP cubic registered
[    9.735955] NET: Registered protocol family 1
[    9.736009] Using IPI No-Shortcut mode
[    9.736303]   Magic number: 12:844:521
[    9.736957] Freeing unused kernel memory: 364k freed
[    9.767376] input: AT Translated Set 2 keyboard as /class/input/input1
[   11.037893] AppArmor: AppArmor initialized<5>audit(1203665505.188:2):  type=1505 info="AppArmor initialized" pid=1191
[   11.053560] fuse init (API version 7.8)
[   11.061728] Failure registering capabilities with primary security module.
[   11.082629] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[   11.085671] ACPI: Thermal Zone [THM0] (70 C)
[   11.900204] usbcore: registered new interface driver usbfs
[   11.900247] usbcore: registered new interface driver hub
[   11.900285] usbcore: registered new device driver usb
[   11.902607] USB Universal Host Controller Interface driver v3.0
[   11.902735] ACPI: PCI Interrupt 0000:00:1d.0[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
[   11.902754] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[   11.902760] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[   11.903030] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[   11.903099] uhci_hcd 0000:00:1d.0: irq 11, io base 0x00001800
[   11.903303] usb usb1: configuration #1 chosen from 1 choice
[   11.903357] hub 1-0:1.0: USB hub found
[   11.903369] hub 1-0:1.0: 2 ports detected
[   12.015206] hub 1-0:1.0: over-current change on port 1
[   12.015929] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 11
[   12.015936] ACPI: PCI Interrupt 0000:00:1d.1[B] -> Link [LNKD] -> GSI 11 (level, low) -> IRQ 11
[   12.015954] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[   12.015960] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[   12.016008] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[   12.016041] uhci_hcd 0000:00:1d.1: irq 11, io base 0x00001820
[   12.016244] usb usb2: configuration #1 chosen from 1 choice
[   12.016294] hub 2-0:1.0: USB hub found
[   12.016307] hub 2-0:1.0: 2 ports detected
[   12.016913] SCSI subsystem initialized
[   12.032695] libata version 2.21 loaded.
[   12.119365] hub 2-0:1.0: over-current change on port 1
[   12.120075] ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 11
[   12.120082] ACPI: PCI Interrupt 0000:00:1d.2[C] -> Link [LNKC] -> GSI 11 (level, low) -> IRQ 11
[   12.120101] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[   12.120107] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[   12.120153] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
[   12.120185] uhci_hcd 0000:00:1d.2: irq 11, io base 0x00001840
[   12.120365] usb usb3: configuration #1 chosen from 1 choice
[   12.120428] hub 3-0:1.0: USB hub found
[   12.120441] hub 3-0:1.0: 2 ports detected
[   12.122523] e100: Intel(R) PRO/100 Network Driver, 3.5.17-k4-NAPI
[   12.122528] e100: Copyright(c) 1999-2006 Intel Corporation
[   12.223061] hub 2-0:1.0: over-current change on port 2
[   12.224254] ata_piix 0000:00:1f.1: version 2.11
[   12.224277] PCI: Enabling device 0000:00:1f.1 (0005 -> 0007)
[   12.224291] ACPI: PCI Interrupt 0000:00:1f.1[A] -> Link [LNKC] -> GSI 11 (level, low) -> IRQ 11
[   12.224351] PCI: Setting latency timer of device 0000:00:1f.1 to 64
[   12.224601] scsi0 : ata_piix
[   12.224673] scsi1 : ata_piix
[   12.225896] ata1: PATA max UDMA/100 cmd 0x000101f0 ctl 0x000103f6 bmdma 0x00011860 irq 14
[   12.225903] ata2: PATA max UDMA/100 cmd 0x00010170 ctl 0x00010376 bmdma 0x00011868 irq 15
[   12.392214] Floppy drive(s): fd0 is 1.44M
[   12.458852] FDC 0 is a National Semiconductor PC87306
[    4.948000] Marking TSC unstable due to: possible TSC halt in C2.
[    4.952000] Time: acpi_pm clocksource has been installed.
[    5.008000] ata1.00: ATA-6: IC25N060ATMR04-0, MO3OAD5A, max UDMA/100
[    5.008000] ata1.00: 117210240 sectors, multi 16: LBA48 
[    5.008000] ata1.01: ATAPI: TOSHIBA DVD-ROM SD-C2512, 1115, max UDMA/33
[    5.024000] ata1.00: configured for UDMA/100
[    5.212000] ata1.01: configured for UDMA/33
[    5.216000] Clocksource tsc unstable (delta = -436490118 ns)
[    5.532000] ata2.00: ATAPI: SONY    CD-RW  CRX700E, 1.6q, max UDMA/33
[    5.704000] ata2.00: configured for UDMA/33
[    5.704000] scsi 0:0:0:0: Direct-Access     ATA      IC25N060ATMR04-0 MO3O PQ: 0 ANSI: 5
[    5.732000] scsi 0:0:1:0: CD-ROM            TOSHIBA  DVD-ROM SD-C2512 1115 PQ: 0 ANSI: 5
[    5.736000] scsi 1:0:0:0: CD-ROM            SONY     CD-RW  CRX700E   1.6q PQ: 0 ANSI: 5
[    5.744000] ACPI: PCI Interrupt Link [LNKE] enabled at IRQ 11
[    5.744000] ACPI: PCI Interrupt 0000:02:08.0[A] -> Link [LNKE] -> GSI 11 (level, low) -> IRQ 11
[    5.768000] e100: eth0: e100_probe: addr 0xc0200000, irq 11, MAC addr 00:D0:59:BF:D1:EF
[    5.804000] sd 0:0:0:0: [sda] 117210240 512-byte hardware sectors (60012 MB)
[    5.804000] sd 0:0:0:0: [sda] Write Protect is off
[    5.804000] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    5.804000] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    5.804000] sd 0:0:0:0: [sda] 117210240 512-byte hardware sectors (60012 MB)
[    5.804000] sd 0:0:0:0: [sda] Write Protect is off
[    5.804000] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    5.804000] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    5.804000]  sda: sda1 sda2 sda3 < sda5 >
[    5.868000] sd 0:0:0:0: [sda] Attached SCSI disk
[    5.876000] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    5.876000] scsi 0:0:1:0: Attached scsi generic sg1 type 5
[    5.876000] scsi 1:0:0:0: Attached scsi generic sg2 type 5
[    5.908000] sr0: scsi3-mmc drive: 24x/24x cd/rw xa/form2 cdda tray
[    5.908000] Uniform CD-ROM driver Revision: 3.20
[    5.908000] sr 0:0:1:0: Attached scsi CD-ROM sr0
[    5.912000] sr1: scsi3-mmc drive: 24x/24x writer cd/rw xa/form2 cdda tray
[    5.912000] sr 1:0:0:0: Attached scsi CD-ROM sr1
[    6.272000] Attempting manual resume
[    6.272000] swsusp: Resume From Partition 8:5
[    6.272000] PM: Checking swsusp image.
[    6.272000] PM: Resume from disk failed.
[    6.332000] kjournald starting.  Commit interval 5 seconds
[    6.332000] EXT3-fs: mounted filesystem with ordered data mode.
[   17.644000] Linux agpgart interface v0.102 (c) Dave Jones
[   17.784000] agpgart: Detected an Intel 830M Chipset.
[   17.800000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   17.800000] agpgart: AGP aperture is 256M @ 0xd0000000
[   17.804000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   17.988000] iTCO_vendor_support: vendor-support=0
[   18.096000] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.01 (21-Jan-2007)
[   18.096000] iTCO_wdt: Found a ICH3-M TCO device (Version=1, TCOBASE=0x1060)
[   18.096000] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   18.820000] intel_rng: FWH not detected
[   19.172000] Yenta: CardBus bridge found at 0000:02:00.0 [1014:0185]
[   19.264000] input: PC Speaker as /class/input/input2
[   19.300000] spurious 8259A interrupt: IRQ7.
[   19.300000] Yenta: ISA IRQ mask 0x04b8, PCI irq 11
[   19.300000] Socket status: 30000820
[   19.300000] pcmcia: parent PCI bridge I/O window: 0x4000 - 0x8fff
[   19.300000] cs: IO port probe 0x4000-0x8fff: clean.
[   19.300000] pcmcia: parent PCI bridge Memory window: 0xc0200000 - 0xcfffffff
[   19.300000] pcmcia: parent PCI bridge Memory window: 0xe8000000 - 0xefffffff
[   19.300000] Yenta: CardBus bridge found at 0000:02:00.1 [1014:0185]
[   19.428000] Yenta: ISA IRQ mask 0x04b8, PCI irq 11
[   19.428000] Socket status: 30000006
[   19.428000] pcmcia: parent PCI bridge I/O window: 0x4000 - 0x8fff
[   19.428000] cs: IO port probe 0x4000-0x8fff: clean.
[   19.428000] pcmcia: parent PCI bridge Memory window: 0xc0200000 - 0xcfffffff
[   19.428000] pcmcia: parent PCI bridge Memory window: 0xe8000000 - 0xefffffff
[   19.936000] pccard: CardBus card inserted into slot 0
[   20.172000] irda_init()
[   20.172000] NET: Registered protocol family 23
[   20.504000] IBM TrackPoint firmware: 0x0e, buttons: 3/3
[   20.520000] input: TPPS/2 IBM TrackPoint as /class/input/input3
[   20.524000] pnp: Device 00:0b activated.
[   20.524000] parport_pc 00:0b: reported by Plug and Play ACPI
[   20.524000] parport0: PC-style at 0x3bc, irq 7 [PCSPP,TRISTATE]
[   20.540000] PCI: Enabling device 0000:00:1f.5 (0000 -> 0001)
[   20.540000] ACPI: PCI Interrupt 0000:00:1f.5[B] -> Link [LNKB] -> GSI 11 (level, low) -> IRQ 11
[   20.540000] PCI: Setting latency timer of device 0000:00:1f.5 to 64
[   20.620000] pnp: Device 00:0c activated.
[   20.620000] nsc_ircc_pnp_probe() : From PnP, found firbase 0x2F8 ; irq 3 ; dma 1.
[   20.620000] nsc-ircc, chip->init
[   20.620000] nsc-ircc, Found chip at base=0x02e
[   20.620000] nsc-ircc, driver loaded (Dag Brattli)
[   20.620000] IrDA: Registered device irda0
[   20.620000] nsc-ircc, Using dongle: IBM31T1100 or Temic TFDS6000/TFDS6500
[   20.788000] cs: IO port probe 0x100-0x3af: clean.
[   20.788000] cs: IO port probe 0x3e0-0x4ff: excluding 0x4d0-0x4d7
[   20.788000] cs: IO port probe 0x820-0x8ff: clean.
[   20.788000] cs: IO port probe 0xc00-0xcf7: clean.
[   20.788000] cs: IO port probe 0xa00-0xaff: clean.
[   20.792000] cs: IO port probe 0x100-0x3af: clean.
[   20.792000] cs: IO port probe 0x3e0-0x4ff: excluding 0x4d0-0x4d7
[   20.792000] cs: IO port probe 0x820-0x8ff: clean.
[   20.792000] cs: IO port probe 0xc00-0xcf7: clean.
[   20.792000] cs: IO port probe 0xa00-0xaff: clean.
[   21.788000] intel8x0_measure_ac97_clock: measured 55282 usecs
[   21.788000] intel8x0: clocking to 48000
[   22.248000] lp0: using parport0 (interrupt-driven).
[   22.380000] ndiswrapper version 1.45 loaded (smp=yes)
[   22.512000] ndiswrapper: driver bcmwl5 (Broadcom,02/11/2005, 3.100.64.0) loaded
[   22.512000] PCI: Enabling device 0000:03:00.0 (0000 -> 0002)
[   22.512000] ACPI: PCI Interrupt 0000:03:00.0[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
[   22.512000] PCI: Setting latency timer of device 0000:03:00.0 to 64
[   22.524000] ndiswrapper: using IRQ 11
[   22.872000] wlan0: ethernet device 00:11:50:9f:b8:25 using NDIS driver: bcmwl5, version: 0x3644000, NDIS version: 0x501, vendor: '', 14E4:4318.5.conf
[   22.872000] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK
[   22.872000] usbcore: registered new interface driver ndiswrapper
[   22.932000] ndiswrapper: changing interface name from 'wlan0' to 'eth1'
[   23.012000] Adding 1124508k swap on /dev/sda5.  Priority:-1 extents:1 across:1124508k
[   23.424000] EXT3 FS on sda2, internal journal
[   25.020000] ACPI: Video Device [VID] (multi-head: yes  rom: no  post: no)
[   25.116000] input: Power Button (FF) as /class/input/input4
[   25.120000] ACPI: Power Button (FF) [PWRF]
[   25.176000] input: Lid Switch as /class/input/input5
[   25.176000] ACPI: Lid Switch [LID]
[   25.204000] input: Sleep Button (CM) as /class/input/input6
[   25.204000] ACPI: Sleep Button (CM) [SLPB]
[   25.312000] ACPI: ACPI Dock Station Driver 
[   25.368000] ACPI: AC Adapter [AC] (on-line)
[   25.404000] ACPI: Battery Slot [BAT0] (battery present)
[   27.176000] ACPI: PCI Interrupt 0000:00:1f.6[B] -> Link [LNKB] -> GSI 11 (level, low) -> IRQ 11
[   27.176000] PCI: Setting latency timer of device 0000:00:1f.6 to 64
[   28.040000] ppdev: user-space parallel port driver
[   28.252000] audit(1203683530.872:3):  type=1503 operation="inode_permission" requested_mask="a" denied_mask="a" name="/dev/tty" pid=4808 profile="/usr/sbin/cupsd"
[   28.296000] IBM machine detected. Enabling interrupts during APM calls.
[   28.296000] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[   28.296000] apm: overridden by ACPI.
[   28.684000] thinkpad_acpi: ThinkPad ACPI Extras v0.14
[   28.684000] thinkpad_acpi: [http://ibm-acpi.sf.net/](http://ibm-acpi.sf.net/)
[   28.688000] thinkpad_acpi: another device driver is already handling bay events
[   28.688000] thinkpad_acpi: disabling subdriver bay
[   29.528000] Non-volatile memory driver v1.2
[   29.616000] input: /usr/sbin/thinkpad-keys as /class/input/input7
[   30.020000] Failure registering capabilities with primary security module.
[   30.252000] Bluetooth: Core ver 2.11
[   30.252000] NET: Registered protocol family 31
[   30.252000] Bluetooth: HCI device and connection manager initialized
[   30.252000] Bluetooth: HCI socket layer initialized
[   30.292000] Bluetooth: L2CAP ver 2.8
[   30.292000] Bluetooth: L2CAP socket layer initialized
[   30.420000] Bluetooth: RFCOMM socket layer initialized
[   30.420000] Bluetooth: RFCOMM TTY layer initialized
[   30.420000] Bluetooth: RFCOMM ver 1.8
[   57.420000] UDF-fs: No VRS found
[   57.448000] ISO 9660 Extensions: Microsoft Joliet Level 3
[   57.940000] ISOFS: changing to secondary root
[  137.236000] NET: Registered protocol family 17
[  158.044000] UDF-fs: Partition marked readonly; forcing readonly mount
[  158.068000] UDF-fs INFO UDF 0.9.8.1 (2004/29/09) Mounting volume 'TRANSFORMERS_VANILLA', timestamp 2007/08/23 22:34 (1ed4)
[  348.508000] UDF-fs: Partition marked readonly; forcing readonly mount
[  348.540000] UDF-fs INFO UDF 0.9.8.1 (2004/29/09) Mounting volume 'TRANSFORMERS_VANILLA', timestamp 2007/08/23 22:34 (1ed4)
[ 1018.712000] NET: Registered protocol family 10
[ 1018.712000] lo: Disabled Privacy Extensions
[ 1018.712000] ADDRCONF(NETDEV_UP): eth0: link is not ready
[ 1040.352000] ADDRCONF(NETDEV_UP): eth1: link is not ready
[ 1045.380000] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
[ 1055.824000] eth1: no IPv6 routers present
[ 1101.844000] ADDRCONF(NETDEV_UP): eth1: link is not ready
[ 1106.560000] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
[ 1116.716000] eth1: no IPv6 routers present
[ 1173.616000] ADDRCONF(NETDEV_UP): eth1: link is not ready
[ 1178.328000] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
[ 1194.988000] eth1: no IPv6 routers present
[ 1371.612000] UDF-fs: Partition marked readonly; forcing readonly mount
[ 1371.636000] UDF-fs INFO UDF 0.9.8.1 (2004/29/09) Mounting volume 'TRANSFORMERS_VANILLA', timestamp 2007/08/23 22:34 (1ed4)
[50845.156000] UDF-fs: Partition marked readonly; forcing readonly mount
[50845.216000] UDF-fs INFO UDF 0.9.8.1 (2004/29/09) Mounting volume 'JEFF_DUNHAM_ARGUING_WITH_MYSEL', timestamp 2006/02/03 14:36 (1ed4)
```

---

### Post by ajgreeny on 2008-02-23
Although it gives a lot more info about everything in your hardware try ```
sudo lshw
```There will be a lot of output but it does give details of the usb controller etc etc which ```
lsusb
``` doesn't.  Have you actually tried anything plugged in your usb sockets?  Output from **lsusb** or **sudo lsusb** on my system is exactly the same as yours, but all my usb sockets work perfectly.

---

### Post by Yellow Pasque on 2008-02-23
pyro, please edit your post so that it uses [ code ][ /code ] for the dmesg results. It is unreadable like that.

Try these commands:
```
sudo update-pciids; lspci | grep USB
sudo update-usbids; lsusb
lsmod | grep usb
```

---

### Post by pyrotechniccb on 2008-02-24
I just posted the usb part from sudo lshw. I tried all the stuff you told me to do Temujin. It still shows up the same when I do a lsusb. Even with something connected + something not connected. Thanks for the help so far.

```
 *-usb:0
             description: USB Controller
             product: 82801CA/CAM USB Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:1
             description: USB Controller
             product: 82801CA/CAM USB Controller #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:2
             description: USB Controller
             product: 82801CA/CAM USB Controller #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
```

---

### Post by pyrotechniccb on 2008-02-27
Still looking for help please.

---

