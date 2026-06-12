---
title: "Not able to log into ubuntu...."
date: 2008-10-01
forum: General Help
---

### Post by Julius1988 on 2008-10-01
I recently ran an update in ubuntu, now i am not able to log into ubuntu(the screen stays black after the load screen)what to do?

---

### Post by jamieh on 2008-10-01
I'm a noob myself, but can Ubuntu boot in verbose mode? If so, tell us where the scrolling lines of text stop.

---

### Post by Julius1988 on 2008-10-01
> [5.788000]sd 0:0:0:0: attachedscsi generic sd0 type 0
but this happens only after i ran the update.........

---

### Post by Julius1988 on 2008-10-01
any clue of what is happening?

---

### Post by Julius1988 on 2008-10-01
here is my dmesg output
> 
[    0.000000] Linux version 2.6.22-14-generic (buildd@terranova) (gcc version 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)) #1 SMP Tue Feb 12 07:42:25 UTC 2008 (Ubuntu 2.6.22-14.52-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e4000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000007ffc0000 (usable)
[    0.000000]  BIOS-e820: 000000007ffc0000 - 000000007ffce000 (ACPI data)
[    0.000000]  BIOS-e820: 000000007ffce000 - 000000007fff0000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000007fff0000 - 0000000080000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fef00000 (reserved)
[    0.000000]  BIOS-e820: 00000000ffb80000 - 0000000100000000 (reserved)
[    0.000000] 1151MB HIGHMEM available.
[    0.000000] 896MB LOWMEM available.
[    0.000000] found SMP MP-table at 000ff780
[    0.000000] Entering add_active_range(0, 0, 524224) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   229376
[    0.000000]   HighMem    229376 ->   524224
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   524224
[    0.000000] On node 0 totalpages: 524224
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 1760 pages used for memmap
[    0.000000]   Normal zone: 223520 pages, LIFO batch:31
[    0.000000]   HighMem zone: 2303 pages used for memmap
[    0.000000]   HighMem zone: 292545 pages, LIFO batch:31
[    0.000000] DMI present.
[    0.000000] ACPI: RSDP signature @ 0xC00FB810 checksum 0
[    0.000000] ACPI: RSDP 000FB810, 0014 (r0 ACPIAM)
[    0.000000] ACPI: RSDT 7FFC0000, 0034 (r1 A_M_I_ OEMRSDT   5000701 MSFT       97)
[    0.000000] ACPI: FACP 7FFC0200, 0084 (r2 A_M_I_ OEMFACP   5000701 MSFT       97)
[    0.000000] ACPI: DSDT 7FFC0440, 6768 (r1  A0785 A0785000        0 INTL  2002026)
[    0.000000] ACPI: FACS 7FFCE000, 0040
[    0.000000] ACPI: MCFG 7FFC0400, 003C (r1 A_M_I_ OEMMCFG   5000701 MSFT       97)
[    0.000000] ACPI: OEMB 7FFCE040, 0060 (r1 A_M_I_ AMI_OEM   5000701 MSFT       97)
[    0.000000] ACPI: HPET 7FFC6BB0, 0038 (r1 A_M_I_ OEMHPET0  5000701 MSFT       97)
[    0.000000] ACPI: PM-Timer IO Port: 0x508
[    0.000000] ACPI: HPET id: 0x10de8201 base: 0xfed00000
[    0.000000] Intel MultiProcessor Specification v1.4
[    0.000000]     Virtual Wire compatibility mode.
[    0.000000] OEM ID: TEMPLATE Product ID: SE           APIC at: 0xFEE00000
[    0.000000] Processor #0 15:3 APIC version 16
[    0.000000] Processor #1 15:3 APIC version 16
[    0.000000] I/O APIC #2 Version 17 at 0xFEC00000.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] Processors: 2
[    0.000000] Allocating PCI resources starting at 88000000 (gap: 80000000:7ec00000)
[    0.000000] Built 1 zonelists.  Total pages: 520129
[    0.000000] Kernel command line: root=UUID=0e731726-79eb-4073-8e49-3b3d6b4883bb ro single
[    0.000000] mapped APIC to ffffd000 (fee00000)
[    0.000000] mapped IOAPIC to ffffc000 (fec00000)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] Detected 3013.729 MHz processor.
[    0.000000] spurious 8259A interrupt: IRQ7.
[    0.000000] Console: colour VGA+ 80x25
[    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.000000] Memory: 2066820k/2096896k available (2015k kernel code, 28844k reserved, 915k data, 364k init, 1179392k highmem)
[    0.000000] virtual kernel memory layout:
[    0.000000]     fixmap  : 0xfff4d000 - 0xfffff000   ( 712 kB)
[    0.000000]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[    0.000000]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
[    0.000000]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
[    0.000000]       .init : 0xc03e3000 - 0xc043e000   ( 364 kB)
[    0.000000]       .data : 0xc02f7e86 - 0xc03dce84   ( 915 kB)
[    0.000000]       .text : 0xc0100000 - 0xc02f7e86   (2015 kB)
[    0.000000] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[    0.000000] SLUB: Genslabs=22, HWalign=64, Order=0-1, MinObjects=4, CPUs=2, Nodes=1
[    0.000000] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 31
[    0.000000] hpet0: 3 32-bit timers, 25000000 Hz
[    0.080000] Calibrating delay using timer specific routine.. 6033.02 BogoMIPS (lpj=12066044)
[    0.080000] Security Framework v1.0.0 initialized
[    0.080000] SELinux:  Disabled at boot.
[    0.080000] Mount-cache hash table entries: 512
[    0.080000] CPU: After generic identify, caps: 178bfbff ebd3fbff 00000000 00000000 00002001 00000000 0000001f
[    0.080000] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[    0.080000] CPU: L2 Cache: 1024K (64 bytes/line)
[    0.080000] CPU 0(2) -> Core 0
[    0.080000] CPU: After all inits, caps: 178bfbff ebd3fbff 00000000 00000410 00002001 00000000 0000001f
[    0.080000] Compat vDSO mapped to ffffe000.
[    0.080000] Checking 'hlt' instruction... OK.
[    0.096000] SMP alternatives: switching to UP code
[    0.096000] Early unpacking initramfs... done
[    0.316000] ACPI: Core revision 20070126
[    0.316000] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[    0.320000] ACPI: setting ELCR to 0200 (from 8c00)
[    0.320000] CPU0: AMD Athlon(tm) 64 X2 Dual Core Processor 6000+ stepping 03
[    0.320000] SMP alternatives: switching to SMP code
[    0.320000] Booting processor 1/1 eip 3000
[    0.328000] Initializing CPU#1
[    0.408000] Calibrating delay using timer specific routine.. 6027.33 BogoMIPS (lpj=12054666)
[    0.408000] CPU: After generic identify, caps: 178bfbff ebd3fbff 00000000 00000000 00002001 00000000 0000001f
[    0.408000] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[    0.408000] CPU: L2 Cache: 1024K (64 bytes/line)
[    0.408000] CPU 1(2) -> Core 1
[    0.408000] CPU: After all inits, caps: 178bfbff ebd3fbff 00000000 00000410 00002001 00000000 0000001f
[    0.408000] CPU1: AMD Athlon(tm) 64 X2 Dual Core Processor 6000+ stepping 03
[    0.408000] Total of 2 processors activated (12060.35 BogoMIPS).
[    0.408000] ExtINT not setup in hardware but reported by MP table
[    0.408000] ENABLING IO-APIC IRQs
[    0.408000] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=0 pin2=0
[    0.448000] Brought up 2 CPUs
[    0.488000] migration_cost=4000
[    0.488000] Booting paravirtualized kernel on bare hardware
[    0.492000] Time: 11:20:25  Date: 09/01/108
[    0.492000] NET: Registered protocol family 16
[    0.492000] EISA bus registered
[    0.492000] ACPI: bus type pci registered
[    0.492000] PCI: PCI BIOS revision 3.00 entry at 0xf0031, last bus=4
[    0.492000] PCI: Using configuration type 1
[    0.492000] Setting up standard PCI resources
[    0.496000] ACPI: EC: Look up EC in DSDT
[    0.500000] ACPI: Interpreter enabled
[    0.500000] ACPI: (supports S0 S1 S3 S4 S5)
[    0.500000] ACPI: Using PIC for interrupt routing
[    0.508000] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.508000] PCI: Probing PCI hardware (bus 00)
[    0.508000] PCI: Transparent bridge - 0000:00:04.0
[    0.508000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.508000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P1._PRT]
[    0.508000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P2._PRT]
[    0.508000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.BR11._PRT]
[    0.508000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.BR12._PRT]
[    0.512000] ACPI: PCI Interrupt Link [LNKA] (IRQs 7 10 *11 14)
[    0.512000] ACPI: PCI Interrupt Link [LNKB] (IRQs 7 10 11 14) *0, disabled.
[    0.512000] ACPI: PCI Interrupt Link [LNKC] (IRQs 7 10 11 14) *0, disabled.
[    0.516000] ACPI: PCI Interrupt Link [LNKD] (IRQs 7 10 11 14) *0, disabled.
[    0.516000] ACPI: PCI Interrupt Link [LNEA] (IRQs 7 10 11 14) *0, disabled.
[    0.516000] ACPI: PCI Interrupt Link [LNEB] (IRQs 7 10 11 14) *0, disabled.
[    0.516000] ACPI: PCI Interrupt Link [LNEC] (IRQs 7 10 11 14) *0, disabled.
[    0.516000] ACPI: PCI Interrupt Link [LNED] (IRQs 7 10 *11 14)
[    0.516000] ACPI: PCI Interrupt Link [LUB0] (IRQs 7 10 *11 14)
[    0.516000] ACPI: PCI Interrupt Link [LUB2] (IRQs 7 *10 11 14)
[    0.516000] ACPI: PCI Interrupt Link [LMAC] (IRQs 7 10 *11 14)
[    0.516000] ACPI: PCI Interrupt Link [LAZA] (IRQs 7 10 *11 14)
[    0.516000] ACPI: PCI Interrupt Link [LACI] (IRQs 7 10 11 14) *0, disabled.
[    0.516000] ACPI: PCI Interrupt Link [LMC9] (IRQs 7 10 11 14) *0, disabled.
[    0.516000] ACPI: PCI Interrupt Link [LSMB] (IRQs 7 *10 11 14)
[    0.516000] ACPI: PCI Interrupt Link [LPMU] (IRQs 7 10 11 14) *0, disabled.
[    0.520000] ACPI: PCI Interrupt Link [LSA0] (IRQs *15)
[    0.520000] ACPI: PCI Interrupt Link [LSA1] (IRQs 5) *0, disabled.
[    0.520000] ACPI: PCI Interrupt Link [LATA] (IRQs 7 10 11 14) *0, disabled.
[    0.520000] Linux Plug and Play Support v0.97 (c) Adam Belay
[    0.520000] pnp: PnP ACPI init
[    0.520000] ACPI: bus type pnp registered
[    0.524000] pnp: PnP ACPI: found 16 devices
[    0.524000] ACPI: ACPI bus type pnp unregistered
[    0.524000] PnPBIOS: Disabled by ACPI PNP
[    0.524000] PCI: Using ACPI for IRQ routing
[    0.524000] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[    0.532000] NET: Registered protocol family 8
[    0.532000] NET: Registered protocol family 20
[    0.532000] pnp: 00:07: iomem range 0xfefe0000-0xfefe01ff has been reserved
[    0.532000] pnp: 00:07: iomem range 0xfefe1000-0xfefe1fff has been reserved
[    0.532000] pnp: 00:07: iomem range 0xfee01000-0xfeefffff could not be reserved
[    0.532000] pnp: 00:07: iomem range 0xffb80000-0xffffffff could not be reserved
[    0.532000] pnp: 00:09: iomem range 0xfec00000-0xfec00fff could not be reserved
[    0.532000] pnp: 00:09: iomem range 0xfee00000-0xfee00fff could not be reserved
[    0.532000] pnp: 00:09: iomem range 0x0-0x0 could not be reserved
[    0.532000] pnp: 00:0c: ioport range 0x230-0x23f has been reserved
[    0.532000] pnp: 00:0c: ioport range 0x290-0x29f has been reserved
[    0.532000] pnp: 00:0c: ioport range 0xa00-0xa0f has been reserved
[    0.532000] pnp: 00:0c: ioport range 0xa10-0xa1f has been reserved
[    0.532000] pnp: 00:0e: iomem range 0xe0000000-0xefffffff has been reserved
[    0.532000] pnp: 00:0f: iomem range 0x0-0x9ffff could not be reserved
[    0.532000] pnp: 00:0f: iomem range 0xc0000-0xcffff could not be reserved
[    0.532000] pnp: 00:0f: iomem range 0xe0000-0xfffff could not be reserved
[    0.532000] pnp: 00:0f: iomem range 0x100000-0x7fffffff could not be reserved
[    0.536000] Time: hpet clocksource has been installed.
[    0.536000] Switched to high resolution mode on CPU 0
[    0.536000] Switched to high resolution mode on CPU 1
[    0.560000] PCI: Bridge: 0000:00:04.0
[    0.560000]   IO window: disabled.
[    0.560000]   MEM window: dde00000-ddefffff
[    0.560000]   PREFETCH window: disabled.
[    0.560000] PCI: Bridge: 0000:00:09.0
[    0.560000]   IO window: e000-efff
[    0.560000]   MEM window: ddf00000-dfffffff
[    0.560000]   PREFETCH window: c0000000-cfffffff
[    0.560000] PCI: Bridge: 0000:00:0b.0
[    0.560000]   IO window: disabled.
[    0.560000]   MEM window: disabled.
[    0.560000]   PREFETCH window: disabled.
[    0.560000] PCI: Bridge: 0000:00:0c.0
[    0.560000]   IO window: disabled.
[    0.560000]   MEM window: disabled.
[    0.560000]   PREFETCH window: disabled.
[    0.560000] PCI: Setting latency timer of device 0000:00:04.0 to 64
[    0.560000] PCI: Setting latency timer of device 0000:00:09.0 to 64
[    0.560000] PCI: Setting latency timer of device 0000:00:0b.0 to 64
[    0.560000] PCI: Setting latency timer of device 0000:00:0c.0 to 64
[    0.560000] NET: Registered protocol family 2
[    0.604000] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.604000] TCP established hash table entries: 131072 (order: 8, 1572864 bytes)
[    0.604000] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.604000] TCP: Hash tables configured (established 131072 bind 65536)
[    0.604000] TCP reno registered
[    0.620000] checking if image is initramfs... it is
[    1.056000] Freeing initrd memory: 7720k freed
[    1.056000] audit: initializing netlink socket (disabled)
[    1.056000] audit(1222860026.036:1): initialized
[    1.056000] highmem bounce pool size: 64 pages
[    1.056000] VFS: Disk quotas dquot_6.5.1
[    1.056000] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    1.056000] io scheduler noop registered
[    1.056000] io scheduler anticipatory registered
[    1.056000] io scheduler deadline registered
[    1.056000] io scheduler cfq registered (default)
[    1.480000] Boot video device is 0000:02:00.0
[    1.480000] PCI: Setting latency timer of device 0000:00:09.0 to 64
[    1.480000] assign_interrupt_mode Found MSI capability
[    1.480000] Allocate Port Service[0000:00:09.0:pcie00]
[    1.480000] PCI: Setting latency timer of device 0000:00:0b.0 to 64
[    1.480000] assign_interrupt_mode Found MSI capability
[    1.480000] Allocate Port Service[0000:00:0b.0:pcie00]
[    1.480000] PCI: Setting latency timer of device 0000:00:0c.0 to 64
[    1.480000] assign_interrupt_mode Found MSI capability
[    1.480000] Allocate Port Service[0000:00:0c.0:pcie00]
[    1.480000] isapnp: Scanning for PnP cards...
[    1.836000] isapnp: No Plug & Play device found
[    1.848000] Real Time Clock Driver v1.12ac
[    1.848000] hpet_resources: 0xfed00000 is busy
[    1.848000] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[    1.848000] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.848000] 00:0d: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.848000] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[    1.848000] input: Macintosh mouse button emulation as /class/input/input0
[    1.848000] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f03:PS2M] at 0x60,0x64 irq 1,12
[    1.848000] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.848000] serio: i8042 AUX port at 0x60,0x64 irq 12
[    1.848000] mice: PS/2 mouse device common for all mice
[    1.848000] EISA: Probing bus 0 at eisa.0
[    1.848000] EISA: Detected 0 cards.
[    1.848000] TCP cubic registered
[    1.848000] NET: Registered protocol family 1
[    1.848000] Using IPI No-Shortcut mode
[    1.848000]   Magic number: 12:534:326
[    1.848000]   hash matches device ttyyf
[    1.848000] Freeing unused kernel memory: 364k freed
[    1.980000] AppArmor: AppArmor initialized<5>audit(1222860026.536:2):  type=1505 info="AppArmor initialized" pid=1204
[    1.984000] fuse init (API version 7.8)
[    1.988000] Failure registering capabilities with primary security module.
[    2.020000] ACPI Exception (processor_core-0783): AE_NOT_FOUND, Processor Device is not present [20070126]
[    2.020000] ACPI Exception (processor_core-0783): AE_NOT_FOUND, Processor Device is not present [20070126]
[    2.356000] usbcore: registered new interface driver usbfs
[    2.356000] usbcore: registered new interface driver hub
[    2.356000] usbcore: registered new device driver usb
[    2.356000] ACPI: PCI Interrupt Link [LUB2] enabled at IRQ 10
[    2.356000] PCI: setting IRQ 10 as level-triggered
[    2.356000] ACPI: PCI Interrupt 0000:00:02.1[B] -> Link [LUB2] -> GSI 10 (level, low) -> IRQ 10
[    2.356000] PCI: Setting latency timer of device 0000:00:02.1 to 64
[    2.356000] ehci_hcd 0000:00:02.1: EHCI Host Controller
[    2.356000] ehci_hcd 0000:00:02.1: new USB bus registered, assigned bus number 1
[    2.356000] ehci_hcd 0000:00:02.1: debug port 1
[    2.356000] PCI: cache line size of 64 is not supported by device 0000:00:02.1
[    2.356000] ehci_hcd 0000:00:02.1: irq 10, io mem 0xdddfec00
[    2.356000] ehci_hcd 0000:00:02.1: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    2.356000] usb usb1: configuration #1 chosen from 1 choice
[    2.356000] hub 1-0:1.0: USB hub found
[    2.356000] hub 1-0:1.0: 8 ports detected
[    2.388000] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
[    2.420000] SCSI subsystem initialized
[    2.440000] Floppy drive(s): fd0 is 1.44M
[    2.448000] libata version 2.21 loaded.
[    2.452000] forcedeth.c: Reverse Engineered nForce ethernet driver. Version 0.60.
[    2.456000] FDC 0 is a post-1991 82077
[    2.460000] ACPI: PCI Interrupt Link [LUB0] enabled at IRQ 11
[    2.460000] PCI: setting IRQ 11 as level-triggered
[    2.460000] ACPI: PCI Interrupt 0000:00:02.0[A] -> Link [LUB0] -> GSI 11 (level, low) -> IRQ 11
[    2.460000] PCI: Setting latency timer of device 0000:00:02.0 to 64
[    2.460000] ohci_hcd 0000:00:02.0: OHCI Host Controller
[    2.460000] ohci_hcd 0000:00:02.0: new USB bus registered, assigned bus number 2
[    2.460000] ohci_hcd 0000:00:02.0: irq 11, io mem 0xdddff000
[    2.516000] usb usb2: configuration #1 chosen from 1 choice
[    2.516000] hub 2-0:1.0: USB hub found
[    2.516000] hub 2-0:1.0: 8 ports detected
[    2.620000] sata_nv 0000:00:08.0: version 3.4
[    2.620000] ACPI: PCI Interrupt Link [LSA0] enabled at IRQ 15
[    2.620000] PCI: setting IRQ 15 as level-triggered
[    2.620000] ACPI: PCI Interrupt 0000:00:08.0[A] -> Link [LSA0] -> GSI 15 (level, low) -> IRQ 15
[    2.620000] PCI: Setting latency timer of device 0000:00:08.0 to 64
[    2.620000] scsi0 : sata_nv
[    2.620000] scsi1 : sata_nv
[    2.620000] ata1: SATA max UDMA/133 cmd 0x0001d400 ctl 0x0001d082 bmdma 0x0001c880 irq 15
[    2.620000] ata2: SATA max UDMA/133 cmd 0x0001d000 ctl 0x0001cc02 bmdma 0x0001c888 irq 15
[    2.624000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[    2.624000] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[    2.948000] usb 2-2: new low speed USB device using ohci_hcd and address 2
[    3.088000] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    3.128000] ata1.00: ATA-7: ST3320620AS, 3.AAK, max UDMA/133
[    3.128000] ata1.00: 625142448 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    3.156000] usb 2-2: configuration #1 chosen from 1 choice
[    3.168000] usbcore: registered new interface driver hiddev
[    3.176000] input: USB-compliant keyboard as /class/input/input1
[    3.176000] input: USB HID v1.10 Keyboard [USB-compliant keyboard] on usb-0000:00:02.0-2
[    3.180000] input: USB-compliant keyboard as /class/input/input2
[    3.180000] input: USB HID v1.10 Device [USB-compliant keyboard] on usb-0000:00:02.0-2
[    3.180000] usbcore: registered new interface driver usbhid
[    3.180000] /build/buildd/linux-source-2.6.22-2.6.22/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
[    3.196000] ata1.00: configured for UDMA/133
[    3.508000] ata2: SATA link down (SStatus 0 SControl 300)
[    3.516000] scsi 0:0:0:0: Direct-Access     ATA      ST3320620AS      3.AA PQ: 0 ANSI: 5
[    3.516000] ACPI: PCI Interrupt Link [LMAC] enabled at IRQ 11
[    3.516000] ACPI: PCI Interrupt 0000:00:07.0[A] -> Link [LMAC] -> GSI 11 (level, low) -> IRQ 11
[    3.516000] PCI: Setting latency timer of device 0000:00:07.0 to 64
[    3.516000] forcedeth: using HIGHDMA
[    3.520000] sd 0:0:0:0: [sda] 625142448 512-byte hardware sectors (320073 MB)
[    3.520000] sd 0:0:0:0: [sda] Write Protect is off
[    3.520000] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    3.520000] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    3.520000] sd 0:0:0:0: [sda] 625142448 512-byte hardware sectors (320073 MB)
[    3.520000] sd 0:0:0:0: [sda] Write Protect is off
[    3.520000] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    3.520000] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    3.520000]  sda: sda1 sda2 < sda5 sda6 sda7 sda8 sda9 sda10 >
[    3.620000] sd 0:0:0:0: [sda] Attached SCSI disk
[    3.624000] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    3.912000] Attempting manual resume
[    3.912000] swsusp: Resume From Partition 8:10
[    3.912000] PM: Checking swsusp image.
[    3.912000] PM: Resume from disk failed.
[    3.936000] kjournald starting.  Commit interval 5 seconds
[    3.936000] EXT3-fs: mounted filesystem with ordered data mode.
[    4.036000] eth0: forcedeth.c: subsystem: 01043:8234 bound to 0000:00:07.0
[    4.036000] NFORCE-MCP61: IDE controller at PCI slot 0000:00:06.0
[    4.036000] NFORCE-MCP61: chipset revision 162
[    4.036000] NFORCE-MCP61: not 100% native mode: will probe irqs later
[    4.036000] NFORCE-MCP61: BIOS didn't set cable bits correctly. Enabling workaround.
[    4.036000] NFORCE-MCP61: 0000:00:06.0 (rev a2) UDMA133 controller
[    4.036000]     ide0: BM-DMA at 0xffa0-0xffa7, BIOS settings: hda:DMA, hdb:DMA
[    4.036000] Probing IDE interface ide0...
[    4.772000] hda: SONY DVD RW DRU-190A, ATAPI CD/DVD-ROM drive
[    5.556000] hdb: SONY DVD RW AW-G170A, ATAPI CD/DVD-ROM drive
[    5.612000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[   10.040000] i2c-adapter i2c-0: nForce2 SMBus adapter at 0x600
[   10.040000] i2c-adapter i2c-1: nForce2 SMBus adapter at 0x700
[   10.088000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   10.092000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   10.140000] Linux video capture interface: v2.00
[   10.172000] hda: ATAPI 12X DVD-ROM DVD-R-RAM CD-R/RW drive, 2048kB Cache, UDMA(66)
[   10.172000] Uniform CD-ROM driver Revision: 3.20
[   10.176000] hdb: ATAPI 48X DVD-ROM DVD-R-RAM CD-R/RW drive, 2048kB Cache, UDMA(66)
[   10.252000] logips2pp: Detected unknown logitech mouse model 106
[   10.268000] Linux agpgart interface v0.102 (c) Dave Jones
[   10.312000] saa7130/34: v4l2 driver version 0.2.14 loaded
[   10.312000] ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 11
[   10.312000] ACPI: PCI Interrupt 0000:01:06.0[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
[   10.312000] saa7130[0]: found at 0000:01:06.0, rev: 1, irq: 11, latency: 64, mmio: 0xddeffc00
[   10.312000] saa7134: <rant>
[   10.312000] saa7134:  Congratulations!  Your TV card vendor saved a few
[   10.312000] saa7134:  cents for a eeprom, thus your pci board has no
[   10.312000] saa7134:  subsystem ID and I can't identify it automatically
[   10.312000] saa7134: </rant>
[   10.312000] saa7134: I feel better now.  Ok, here are the good news:
[   10.312000] saa7134: You can use the card=<nr> insmod option to specify
[   10.312000] saa7134: which board do you have.  The list:
[   10.312000] saa7134:   card=0 -> UNKNOWN/GENERIC                         
[   10.312000] saa7134:   card=1 -> Proteus Pro [philips reference design]   1131:2001 1131:2001
[   10.312000] saa7134:   card=2 -> LifeView FlyVIDEO3000                    5168:0138 4e42:0138
[   10.312000] saa7134:   card=3 -> LifeView/Typhoon FlyVIDEO2000            5168:0138 4e42:0138
[   10.312000] saa7134:   card=4 -> EMPRESS                                  1131:6752
[   10.312000] saa7134:   card=5 -> SKNet Monster TV                         1131:4e85
[   10.312000] saa7134:   card=6 -> Tevion MD 9717                          
[   10.312000] saa7134:   card=7 -> KNC One TV-Station RDS / Typhoon TV Tune 1131:fe01 1894:fe01
[   10.312000] saa7134:   card=8 -> Terratec Cinergy 400 TV                  153b:1142
[   10.312000] saa7134:   card=9 -> Medion 5044                             
[   10.312000] saa7134:   card=10 -> Kworld/KuroutoShikou SAA7130-TVPCI      
[   10.312000] saa7134:   card=11 -> Terratec Cinergy 600 TV                  153b:1143
[   10.312000] saa7134:   card=12 -> Medion 7134                              16be:0003
[   10.312000] saa7134:   card=13 -> Typhoon TV+Radio 90031                  
[   10.312000] saa7134:   card=14 -> ELSA EX-VISION 300TV                     1048:226b
[   10.312000] saa7134:   card=15 -> ELSA EX-VISION 500TV                     1048:226a
[   10.316000] saa7134:   card=16 -> ASUS TV-FM 7134                          1043:4842 1043:4830 1043:4840
[   10.316000] saa7134:   card=17 -> AOPEN VA1000 POWER                       1131:7133
[   10.316000] saa7134:   card=18 -> BMK MPEX No Tuner                       
[   10.316000] saa7134:   card=19 -> Compro VideoMate TV                      185b:c100
[   10.316000] saa7134:   card=20 -> Matrox CronosPlus                        102b:48d0
[   10.316000] saa7134:   card=21 -> 10MOONS PCI TV CAPTURE CARD              1131:2001
[   10.316000] saa7134:   card=22 -> AverMedia M156 / Medion 2819             1461:a70b
[   10.316000] saa7134:   card=23 -> BMK MPEX Tuner                          
[   10.316000] saa7134:   card=24 -> KNC One TV-Station DVR                   1894:a006
[   10.316000] saa7134:   card=25 -> ASUS TV-FM 7133                          1043:4843
[   10.316000] saa7134:   card=26 -> Pinnacle PCTV Stereo (saa7134)           11bd:002b
[   10.316000] saa7134:   card=27 -> Manli MuchTV M-TV002/Behold TV 403 FM   
[   10.316000] saa7134:   card=28 -> Manli MuchTV M-TV001/Behold TV 401      
[   10.316000] saa7134:   card=29 -> Nagase Sangyo TransGear 3000TV           1461:050c
[   10.316000] saa7134:   card=30 -> Elitegroup ECS TVP3XP FM1216 Tuner Card( 1019:4cb4
[   10.316000] saa7134:   card=31 -> Elitegroup ECS TVP3XP FM1236 Tuner Card  1019:4cb5
[   10.316000] saa7134:   card=32 -> AVACS SmartTV                           
[   10.316000] saa7134:   card=33 -> AVerMedia DVD EZMaker                    1461:10ff
[   10.316000] saa7134:   card=34 -> Noval Prime TV 7133                     
[   10.316000] saa7134:   card=35 -> AverMedia AverTV Studio 305              1461:2115
[   10.316000] saa7134:   card=36 -> UPMOST PURPLE TV                         12ab:0800
[   10.316000] saa7134:   card=37 -> Items MuchTV Plus / IT-005              
[   10.316000] saa7134:   card=38 -> Terratec Cinergy 200 TV                  153b:1152
[   10.316000] saa7134:   card=39 -> LifeView FlyTV Platinum Mini             5168:0212 4e42:0212
[   10.316000] saa7134:   card=40 -> Compro VideoMate TV PVR/FM               185b:c100
[   10.316000] saa7134:   card=41 -> Compro VideoMate TV Gold+                185b:c100
[   10.316000] saa7134:   card=42 -> Sabrent SBT-TVFM (saa7130)              
[   10.316000] saa7134:   card=43 -> :Zolid Xpert TV7134                     
[   10.316000] saa7134:   card=44 -> Empire PCI TV-Radio LE                  
[   10.316000] saa7134:   card=45 -> Avermedia AVerTV Studio 307              1461:9715
[   10.316000] saa7134:   card=46 -> AVerMedia Cardbus TV/Radio (E500)        1461:d6ee
[   10.316000] saa7134:   card=47 -> Terratec Cinergy 400 mobile              153b:1162
[   10.316000] saa7134:   card=48 -> Terratec Cinergy 600 TV MK3              153b:1158
[   10.316000] saa7134:   card=49 -> Compro VideoMate Gold+ Pal               185b:c200
[   10.316000] saa7134:   card=50 -> Pinnacle PCTV 300i DVB-T + PAL           11bd:002d
[   10.316000] saa7134:   card=51 -> ProVideo PV952                           1540:9524
[   10.316000] saa7134:   card=52 -> AverMedia AverTV/305                     1461:2108
[   10.316000] saa7134:   card=53 -> ASUS TV-FM 7135                          1043:4845
[   10.316000] saa7134:   card=54 -> LifeView FlyTV Platinum FM / Gold        5168:0214 5168:5214 1489:0214 5168:0304
[   10.316000] saa7134:   card=55 -> LifeView FlyDVB-T DUO / MSI TV@nywhere D 5168:0306 4e42:0306
[   10.316000] saa7134:   card=56 -> Avermedia AVerTV 307                     1461:a70a
[   10.316000] saa7134:   card=57 -> Avermedia AVerTV GO 007 FM               1461:f31f
[   10.316000] saa7134:   card=58 -> ADS Tech Instant TV (saa7135)            1421:0350 1421:0351 1421:0370 1421:1370
[   10.316000] saa7134:   card=59 -> Kworld/Tevion V-Stream Xpert TV PVR7134 
[   10.316000] saa7134:   card=60 -> LifeView/Typhoon/Genius FlyDVB-T Duo Car 5168:0502 4e42:0502 1489:0502
[   10.316000] saa7134:   card=61 -> Philips TOUGH DVB-T reference design     1131:2004
[   10.316000] saa7134:   card=62 -> Compro VideoMate TV Gold+II             
[   10.320000] saa7134:   card=63 -> Kworld Xpert TV PVR7134                 
[   10.320000] saa7134:   card=64 -> FlyTV mini Asus Digimatrix               1043:0210
[   10.320000] saa7134:   card=65 -> V-Stream Studio TV Terminator           
[   10.320000] saa7134:   card=66 -> Yuan TUN-900 (saa7135)                  
[   10.320000] saa7134:   card=67 -> Beholder BeholdTV 409 FM                 0000:4091
[   10.320000] saa7134:   card=68 -> GoTView 7135 PCI                         5456:7135
[   10.320000] saa7134:   card=69 -> Philips EUROPA V3 reference design       1131:2004
[   10.320000] saa7134:   card=70 -> Compro Videomate DVB-T300                185b:c900
[   10.320000] saa7134:   card=71 -> Compro Videomate DVB-T200                185b:c901
[   10.320000] saa7134:   card=72 -> RTD Embedded Technologies VFG7350        1435:7350
[   10.320000] saa7134:   card=73 -> RTD Embedded Technologies VFG7330        1435:7330
[   10.320000] saa7134:   card=74 -> LifeView FlyTV Platinum Mini2            14c0:1212
[   10.320000] saa7134:   card=75 -> AVerMedia AVerTVHD MCE A180              1461:1044
[   10.320000] saa7134:   card=76 -> SKNet MonsterTV Mobile                   1131:4ee9
[   10.320000] saa7134:   card=77 -> Pinnacle PCTV 40i/50i/110i (saa7133)     11bd:002e
[   10.320000] saa7134:   card=78 -> ASUSTeK P7131 Dual                       1043:4862 1043:4857
[   10.320000] saa7134:   card=79 -> Sedna/MuchTV PC TV Cardbus TV/Radio (ITO
[   10.320000] saa7134:   card=80 -> ASUS Digimatrix TV                       1043:0210
[   10.320000] saa7134:   card=81 -> Philips Tiger reference design           1131:2018
[   10.320000] saa7134:   card=82 -> MSI TV@Anywhere plus                     1462:6231
[   10.320000] saa7134:   card=83 -> Terratec Cinergy 250 PCI TV              153b:1160
[   10.320000] saa7134:   card=84 -> LifeView FlyDVB Trio                     5168:0319
[   10.320000] saa7134:   card=85 -> AverTV DVB-T 777                         1461:2c05 1461:2c05
[   10.320000] saa7134:   card=86 -> LifeView FlyDVB-T / Genius VideoWonder D 5168:0301 1489:0301
[   10.320000] saa7134:   card=87 -> ADS Instant TV Duo Cardbus PTV331        0331:1421
[   10.320000] saa7134:   card=88 -> Tevion/KWorld DVB-T 220RF                17de:7201
[   10.320000] saa7134:   card=89 -> ELSA EX-VISION 700TV                     1048:226c
[   10.320000] saa7134:   card=90 -> Kworld ATSC110                           17de:7350
[   10.320000] saa7134:   card=91 -> AVerMedia A169 B                         1461:7360
[   10.320000] saa7134:   card=92 -> AVerMedia A169 B1                        1461:6360
[   10.320000] saa7134:   card=93 -> Medion 7134 Bridge #2                    16be:0005
[   10.320000] saa7134:   card=94 -> LifeView FlyDVB-T Hybrid Cardbus         5168:3306 5168:3502
[   10.320000] saa7134:   card=95 -> LifeView FlyVIDEO3000 (NTSC)             5169:0138
[   10.320000] saa7134:   card=96 -> Medion Md8800 Quadro                     16be:0007 16be:0008
[   10.320000] saa7134:   card=97 -> LifeView FlyDVB-S /Acorp TV134DS         5168:0300 4e42:0300
[   10.320000] saa7134:   card=98 -> Proteus Pro 2309                         0919:2003
[   10.320000] saa7134:   card=99 -> AVerMedia TV Hybrid A16AR                1461:2c00
[   10.324000] saa7134:   card=100 -> Asus Europa2 OEM                         1043:4860
[   10.324000] saa7134:   card=101 -> Pinnacle PCTV 310i                       11bd:002f
[   10.324000] saa7134:   card=102 -> Avermedia AVerTV Studio 507              1461:9715
[   10.324000] saa7134:   card=103 -> Compro Videomate DVB-T200A              
[   10.324000] saa7134:   card=104 -> Hauppauge WinTV-HVR1110 DVB-T/Hybrid     0070:6701
[   10.324000] saa7134:   card=105 -> Terratec Cinergy HT PCMCIA               153b:1172
[   10.324000] saa7134:   card=106 -> Encore ENLTV                             1131:2342 1131:2341 3016:2344
[   10.324000] saa7134:   card=107 -> Encore ENLTV-FM                          1131:230f
[   10.324000] saa7134:   card=108 -> Terratec Cinergy HT PCI                  153b:1175
[   10.324000] saa7134:   card=109 -> Philips Tiger - S Reference design      
[   10.324000] saa7134:   card=110 -> Avermedia M102                           1461:f31e
[   10.324000] saa7134:   card=111 -> ASUS P7131 4871                          1043:4871
[   10.324000] saa7134:   card=112 -> ASUSTeK P7131 Hybrid                     1043:4876
[   10.324000] saa7134:   card=113 -> Elitegroup ECS TVP3XP FM1246 Tuner Card  1019:4cb6
[   10.324000] saa7134:   card=114 -> KWorld DVB-T 210                         17de:7250
[   10.324000] saa7134:   card=115 -> Sabrent PCMCIA TV-PCB05                  0919:2003
[   10.324000] saa7130[0]: subsystem: 1131:0000, board: UNKNOWN/GENERIC [card=0,autodetected]
[   10.324000] saa7130[0]: board init: gpio is 60c000
[   10.376000] nvidia: module license 'NVIDIA' taints kernel.
[   10.628000] saa7130[0]: Huh, no eeprom present (err=-5)?
[   10.628000] saa7130[0]: registered device video0 [v4l2]
[   10.628000] saa7130[0]: registered device vbi0
[   10.636000] ACPI: PCI Interrupt Link [LNED] enabled at IRQ 11
[   10.636000] ACPI: PCI Interrupt 0000:02:00.0[A] -> Link [LNED] -> GSI 11 (level, low) -> IRQ 11
[   10.636000] PCI: Setting latency timer of device 0000:02:00.0 to 64
[   10.636000] NVRM: loading NVIDIA UNIX x86 Kernel Module  100.14.19  Wed Sep 12 14:12:24 PDT 2007
[   10.716000] input: ImExPS/2 Logitech Explorer Mouse as /class/input/input3
[   10.716000] parport_pc 00:06: reported by Plug and Play ACPI
[   10.716000] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
[   10.720000] input: PC Speaker as /class/input/input4
[   10.752000] saa7134 ALSA driver for DMA sound loaded
[   10.752000] saa7130[0]/alsa: saa7130[0] at 0xddeffc00 irq 11 registered as card -2
[   10.836000] ACPI: PCI Interrupt Link [LAZA] enabled at IRQ 11
[   10.836000] ACPI: PCI Interrupt 0000:00:05.0[B] -> Link [LAZA] -> GSI 11 (level, low) -> IRQ 11
[   10.836000] PCI: Setting latency timer of device 0000:00:05.0 to 64
[   11.044000] hda_codec: Unknown model for ALC662, trying auto-probe from BIOS...
[   11.280000] lp0: using parport0 (interrupt-driven).
[   11.356000] Adding 7743288k swap on /dev/sda10.  Priority:-1 extents:1 across:7743288k
[   12.936000] EXT3 FS on sda9, internal journal
[   20.100000] kjournald starting.  Commit interval 5 seconds
[   20.100000] EXT3 FS on sda6, internal journal
[   20.100000] EXT3-fs: mounted filesystem with ordered data mode.



---

