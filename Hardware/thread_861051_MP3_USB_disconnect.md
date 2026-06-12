---
title: "MP3 USB disconnect"
date: 2008-07-16
forum: Hardware
---

### Post by morningwoodnews on 2008-07-16
Normally I find the answer in the forums. This time, I've had no luck.

I wanted to upload some new songs to my kid's mp3 player and the mp3 doesn't show up when I pop it into to USB.


Ubuntu Release 8.04 (hardy)
Kernel Linux 2.6.24-19 generic
Gnome 2.22.2

Device: Samsung YP-U2J

With the mp3 plugged in:

1. dmesg

[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   131008
[    0.000000]   HighMem    131008 ->   131008
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   131008
[    0.000000] On node 0 totalpages: 131008
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 991 pages used for memmap
[    0.000000]   Normal zone: 125921 pages, LIFO batch:31
[    0.000000]   HighMem zone: 0 pages used for memmap
[    0.000000]   Movable zone: 0 pages used for memmap
[    0.000000] DMI 2.3 present.
[    0.000000] ACPI: RSDP signature @ 0xC00FACA0 checksum 0
[    0.000000] ACPI: RSDP 000FACA0, 0014 (r0 ACPIAM)
[    0.000000] ACPI: RSDT 1FFC0000, 0030 (r1 A M I  OEMRSDT   4000414 MSFT       97)
[    0.000000] ACPI: FACP 1FFC0200, 0081 (r2 A M I  OEMFACP   4000414 MSFT       97)
[    0.000000] ACPI: DSDT 1FFC03F0, 3581 (r1  PSLA1 PSLA1119      119 INTL  2002026)
[    0.000000] ACPI: FACS 1FFCF000, 0040
[    0.000000] ACPI: APIC 1FFC0390, 005C (r1 A M I  OEMAPIC   4000414 MSFT       97)
[    0.000000] ACPI: OEMB 1FFCF040, 003F (r1 A M I  OEMBIOS   4000414 MSFT       97)
[    0.000000] ACPI: PM-Timer IO Port: 0x808
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] Processor #0 15:3 APIC version 20
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
[    0.000000] Processor #1 15:3 APIC version 20
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] Allocating PCI resources starting at 30000000 (gap: 20000000:dfb80000)
[    0.000000] swsusp: Registered nosave memory region: 000000000009f000 - 00000000000a0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000a0000 - 00000000000e8000
[    0.000000] swsusp: Registered nosave memory region: 00000000000e8000 - 0000000000100000
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 129985
[    0.000000] Kernel command line: root=UUID=c5db7a6f-1a55-4295-b341-ea20bc8ed8df ro quiet splash
[    0.000000] mapped APIC to ffffb000 (fee00000)
[    0.000000] mapped IOAPIC to ffffa000 (fec00000)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 2048 (order: 11, 8192 bytes)
[    0.000000] Detected 3000.199 MHz processor.
[   35.493690] Console: colour VGA+ 80x25
[   35.493694] console [tty0] enabled
[   35.493927] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
[   35.494143] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
[   35.502739] Memory: 507140k/524032k available (2177k kernel code, 16400k reserved, 1006k data, 368k init, 0k highmem)
[   35.502746] virtual kernel memory layout:
[   35.502747]     fixmap  : 0xfff4b000 - 0xfffff000   ( 720 kB)
[   35.502748]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   35.502749]     vmalloc : 0xe0800000 - 0xff7fe000   ( 495 MB)
[   35.502750]     lowmem  : 0xc0000000 - 0xdffc0000   ( 511 MB)
[   35.502751]       .init : 0xc0421000 - 0xc047d000   ( 368 kB)
[   35.502752]       .data : 0xc0320434 - 0xc041bdc4   (1006 kB)
[   35.502753]       .text : 0xc0100000 - 0xc0320434   (2177 kB)
[   35.502757] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   35.502793] SLUB: Genslabs=11, HWalign=64, Order=0-1, MinObjects=4, CPUs=2, Nodes=1
[   35.582744] Calibrating delay using timer specific routine.. 6005.45 BogoMIPS (lpj=12010919)
[   35.582768] Security Framework initialized
[   35.582773] SELinux:  Disabled at boot.
[   35.582785] AppArmor: AppArmor initialized
[   35.582791] Failure registering capabilities with primary security module.
[   35.582799] Mount-cache hash table entries: 512
[   35.582922] Initializing cgroup subsys ns
[   35.582926] Initializing cgroup subsys cpuacct
[   35.582939] CPU: After generic identify, caps: bfebfbff 00000000 00000000 00000000 0000041d 00000000 00000000 00000000
[   35.582948] monitor/mwait feature present.
[   35.582950] using mwait in idle threads.
[   35.582956] CPU: Trace cache: 12K uops, L1 D cache: 16K
[   35.582958] CPU: L2 cache: 1024K
[   35.582961] CPU: Physical Processor ID: 0
[   35.582963] CPU: After all inits, caps: bfebfbff 00000000 00000000 0000b180 0000041d 00000000 00000000 00000000
[   35.582974] Compat vDSO mapped to ffffe000.
[   35.582990] Checking 'hlt' instruction... OK.
[   35.599175] SMP alternatives: switching to UP code
[   35.601051] Early unpacking initramfs... done
[   35.908749] ACPI: Core revision 20070126
[   35.908799] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[   35.910556] CPU0: Intel(R) Pentium(R) 4 CPU 3.00GHz stepping 03
[   35.910576] SMP alternatives: switching to SMP code
[   35.911416] Booting processor 1/1 eip 3000
[   35.921656] Initializing CPU#1
[   36.002370] Calibrating delay using timer specific routine.. 6000.69 BogoMIPS (lpj=12001388)
[   36.002381] CPU: After generic identify, caps: bfebfbff 00000000 00000000 00000000 0000041d 00000000 00000000 00000000
[   36.002389] monitor/mwait feature present.
[   36.002396] CPU: Trace cache: 12K uops, L1 D cache: 16K
[   36.002399] CPU: L2 cache: 1024K
[   36.002401] CPU: Physical Processor ID: 0
[   36.002404] CPU: After all inits, caps: bfebfbff 00000000 00000000 0000b180 0000041d 00000000 00000000 00000000
[   36.002784] CPU1: Intel(R) Pentium(R) 4 CPU 3.00GHz stepping 03
[   36.002827] Total of 2 processors activated (12006.15 BogoMIPS).
[   36.002957] ENABLING IO-APIC IRQs
[   36.003133] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[   36.150393] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
[   36.170391] Brought up 2 CPUs
[   36.170418] CPU0 attaching sched-domain:
[   36.170421]  domain 0: span 03
[   36.170424]   groups: 01 02
[   36.170429]   domain 1: span 03
[   36.170431]    groups: 03
[   36.170434] CPU1 attaching sched-domain:
[   36.170436]  domain 0: span 03
[   36.170438]   groups: 02 01
[   36.170442]   domain 1: span 03
[   36.170444]    groups: 03
[   36.170726] net_namespace: 64 bytes
[   36.170736] Booting paravirtualized kernel on bare hardware
[   36.171299] Time:  5:35:21  Date: 07/16/08
[   36.171326] NET: Registered protocol family 16
[   36.171600] EISA bus registered
[   36.171607] ACPI: bus type pci registered
[   36.171784] PCI: PCI BIOS revision 2.10 entry at 0xf0031, last bus=2
[   36.171787] PCI: Using configuration type 1
[   36.171804] Setting up standard PCI resources
[   36.184994] ACPI: EC: Look up EC in DSDT
[   36.189051] ACPI: Interpreter enabled
[   36.189055] ACPI: (supports S0 S1 S3 S4 S5)
[   36.189074] ACPI: Using IOAPIC for interrupt routing
[   36.196561] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   36.197071] Force enabled HPET at base address 0xfed00000
[   36.197078] PCI quirk: region 0800-087f claimed by ICH4 ACPI/GPIO/TCO
[   36.197082] PCI quirk: region 0480-04bf claimed by ICH4 GPIO
[   36.197667] PCI: Transparent bridge - 0000:00:1e.0
[   36.197694] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   36.197808] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P4._PRT]
[   36.204501] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 *10 11 12 14 15)
[   36.204609] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 10 *11 12 14 15)
[   36.204714] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 *5 6 7 10 11 12 14 15)
[   36.204819] ACPI: PCI Interrupt Link [LNKD] (IRQs *3 4 5 6 7 10 11 12 14 15)
[   36.204926] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[   36.205035] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 *5 6 7 10 11 12 14 15)
[   36.205146] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[   36.205252] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 10 *11 12 14 15)
[   36.205406] ACPI Warning (tbutils-0217): Incorrect checksum in table [OEMB] -  2F, should be 22 [20070126]
[   36.205413] Linux Plug and Play Support v0.97 (c) Adam Belay
[   36.205457] pnp: PnP ACPI init
[   36.205466] ACPI: bus type pnp registered
[   36.209850] pnp: PnP ACPI: found 14 devices
[   36.209854] ACPI: ACPI bus type pnp unregistered
[   36.209858] PnPBIOS: Disabled by ACPI PNP
[   36.210188] PCI: Using ACPI for IRQ routing
[   36.210192] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   36.230194] NET: Registered protocol family 8
[   36.230197] NET: Registered protocol family 20
[   36.230313] hpet clockevent registered
[   36.230319] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[   36.230325] hpet0: 3 64-bit timers, 14318180 Hz
[   36.231371] AppArmor: AppArmor Filesystem Enabled
[   36.234180] Time: tsc clocksource has been installed.
[   36.246226] system 00:08: ioport range 0x680-0x6ff has been reserved
[   36.246234] system 00:09: ioport range 0x4d0-0x4d1 has been reserved
[   36.246237] system 00:09: ioport range 0x800-0x87f has been reserved
[   36.246240] system 00:09: ioport range 0x480-0x4bf has been reserved
[   36.246243] system 00:09: iomem range 0xfed20000-0xfed8ffff has been reserved
[   36.246246] system 00:09: iomem range 0xffb00000-0xffbfffff could not be reserved
[   36.246249] system 00:09: iomem range 0xfff80000-0xffffffff could not be reserved
[   36.246255] system 00:0a: iomem range 0xfec00000-0xfec00fff has been reserved
[   36.246258] system 00:0a: iomem range 0xfee00000-0xfee00fff has been reserved
[   36.246269] system 00:0d: iomem range 0x0-0x9ffff could not be reserved
[   36.246272] system 00:0d: iomem range 0xc0000-0xdffff could not be reserved
[   36.246275] system 00:0d: iomem range 0xe0000-0xfffff could not be reserved
[   36.246278] system 00:0d: iomem range 0x100000-0x1ffeffff could not be reserved
[   36.246280] system 00:0d: iomem range 0xfff00000-0xffffffff could not be reserved
[   36.276820] PCI: Bridge: 0000:00:01.0
[   36.276823]   IO window: disabled.
[   36.276828]   MEM window: fc900000-fe9fffff
[   36.276832]   PREFETCH window: e7f00000-f7efffff
[   36.276838] PCI: Bridge: 0000:00:1e.0
[   36.276841]   IO window: b000-bfff
[   36.276846]   MEM window: fea00000-feafffff
[   36.276850]   PREFETCH window: disabled.
[   36.276868] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[   36.276881] NET: Registered protocol family 2
[   36.314192] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
[   36.314476] TCP established hash table entries: 16384 (order: 5, 131072 bytes)
[   36.314552] TCP bind hash table entries: 16384 (order: 5, 131072 bytes)
[   36.314625] TCP: Hash tables configured (established 16384 bind 16384)
[   36.314628] TCP reno registered
[   36.326243] checking if image is initramfs... it is
[   36.729894] Switched to high resolution mode on CPU 1
[   36.733739] Switched to high resolution mode on CPU 0
[   36.936946] Freeing initrd memory: 7727k freed
[   36.937951] audit: initializing netlink socket (disabled)
[   36.937971] audit(1216186521.316:1): initialized
[   36.940676] VFS: Disk quotas dquot_6.5.1
[   36.940776] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   36.940937] io scheduler noop registered
[   36.940940] io scheduler anticipatory registered
[   36.940942] io scheduler deadline registered
[   36.940955] io scheduler cfq registered (default)
[   44.929758] 0000:00:1d.7 EHCI: BIOS handoff failed (BIOS bug ?) 01010001
[   44.929899] Boot video device is 0000:01:00.0
[   44.930277] isapnp: Scanning for PnP cards...
[   45.283628] isapnp: No Plug & Play device found
[   45.320526] Real Time Clock Driver v1.12ac
[   45.320650] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   45.320778] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   45.321679] 00:05: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   45.322902] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   45.322987] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[   45.323132] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f03:PS2M] at 0x60,0x64 irq 1,12
[   45.325989] serio: i8042 KBD port at 0x60,0x64 irq 1
[   45.325995] serio: i8042 AUX port at 0x60,0x64 irq 12
[   45.345463] mice: PS/2 mouse device common for all mice
[   45.345626] EISA: Probing bus 0 at eisa.0
[   45.345665] EISA: Detected 0 cards.
[   45.345669] cpuidle: using governor ladder
[   45.345671] cpuidle: using governor menu
[   45.345759] NET: Registered protocol family 1
[   45.345790] Using IPI No-Shortcut mode
[   45.345823] registered taskstats version 1
[   45.345933]   Magic number: 0:764:567
[   45.346051] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[   45.346053] EDD information not available.
[   45.346320] Freeing unused kernel memory: 368k freed
[   45.370780] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[   46.593354] fuse init (API version 7.9)
[   46.789912] usbcore: registered new interface driver usbfs
[   46.789948] usbcore: registered new interface driver hub
[   46.805013] usbcore: registered new device driver usb
[   46.825048] USB Universal Host Controller Interface driver v3.0
[   46.825129] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 16 (level, low) -> IRQ 16
[   46.825145] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[   46.825150] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[   46.825424] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[   46.825455] uhci_hcd 0000:00:1d.0: irq 16, io base 0x0000e000
[   46.825650] usb usb1: configuration #1 chosen from 1 choice
[   46.825691] hub 1-0:1.0: USB hub found
[   46.825701] hub 1-0:1.0: 2 ports detected
[   46.871992] SCSI subsystem initialized
[   46.904887] libata version 3.00 loaded.
[   46.928968] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 19 (level, low) -> IRQ 17
[   46.928986] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[   46.928992] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[   46.929031] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[   46.929060] uhci_hcd 0000:00:1d.1: irq 17, io base 0x0000e400
[   46.929239] usb usb2: configuration #1 chosen from 1 choice
[   46.929279] hub 2-0:1.0: USB hub found
[   46.929288] hub 2-0:1.0: 2 ports detected
[   47.032877] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 18
[   47.032894] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[   47.032899] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[   47.032936] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
[   47.032967] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000e800
[   47.033142] usb usb3: configuration #1 chosen from 1 choice
[   47.033183] hub 3-0:1.0: USB hub found
[   47.033192] hub 3-0:1.0: 2 ports detected
[   47.136768] ACPI: PCI Interrupt 0000:00:1d.3[A] -> GSI 16 (level, low) -> IRQ 16
[   47.136784] PCI: Setting latency timer of device 0000:00:1d.3 to 64
[   47.136790] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[   47.136826] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 4
[   47.136853] uhci_hcd 0000:00:1d.3: irq 16, io base 0x0000ec00
[   47.137043] usb usb4: configuration #1 chosen from 1 choice
[   47.137087] hub 4-0:1.0: USB hub found
[   47.137096] hub 4-0:1.0: 2 ports detected
[   47.212431] 8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)
[   47.240846] ACPI: PCI Interrupt 0000:00:1d.7[D] -> GSI 23 (level, low) -> IRQ 19
[   47.240872] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[   47.240879] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[   47.240918] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 5
[   47.244822] ehci_hcd 0000:00:1d.7: debug port 1
[   47.244832] PCI: cache line size of 128 is not supported by device 0000:00:1d.7
[   47.244845] ehci_hcd 0000:00:1d.7: irq 19, io mem 0xfebffc00
[   47.260510] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   47.260684] usb usb5: configuration #1 chosen from 1 choice
[   47.260725] hub 5-0:1.0: USB hub found
[   47.260736] hub 5-0:1.0: 8 ports detected
[   47.317687] Floppy drive(s): fd0 is 1.44M
[   47.336163] FDC 0 is a post-1991 82077
[   47.364682] ata_piix 0000:00:1f.1: version 2.12
[   47.364703] PCI: Enabling device 0000:00:1f.1 (0005 -> 0007)
[   47.364711] ACPI: PCI Interrupt 0000:00:1f.1[A] -> GSI 18 (level, low) -> IRQ 18
[   47.364766] PCI: Setting latency timer of device 0000:00:1f.1 to 64
[   47.378863] scsi0 : ata_piix
[   47.379912] scsi1 : ata_piix
[   47.382278] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xfc00 irq 14
[   47.382285] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xfc08 irq 15
[   47.544634] ata1.00: ATA-7: SAMSUNG SP1604N, TM100-24, max UDMA/133
[   47.544641] ata1.00: 312581808 sectors, multi 16: LBA48 
[   47.551656] ata1.00: configured for UDMA/100
[   47.902901] usb 3-1: new full speed USB device using uhci_hcd and address 2
[   48.035086] ata2.00: ATAPI: Hewlett-Packard DVD Writer 300, 3.11, max UDMA/33
[   48.035117] ata2.01: ATAPI: SAMSUNG CD-ROM  SC-148A, B401, max UDMA/33
[   48.075993] usb 3-1: configuration #1 chosen from 1 choice
[   48.091432] usbcore: registered new interface driver libusual
[   48.097783] Initializing USB Mass Storage driver...
[   48.097938] scsi2 : SCSI emulation for USB Mass Storage devices
[   48.098059] usbcore: registered new interface driver usb-storage
[   48.098066] USB Mass Storage support registered.
[   48.098222] usb-storage: device found at 2
[   48.098225] usb-storage: waiting for device to settle before scanning
[   48.206846] ata2.00: configured for UDMA/33
[   48.378640] ata2.01: configured for UDMA/33
[   48.378792] scsi 0:0:0:0: Direct-Access     ATA      SAMSUNG SP1604N  TM10 PQ: 0 ANSI: 5
[   48.381176] scsi 1:0:0:0: CD-ROM            HP       DVD Writer 300n  3.11 PQ: 0 ANSI: 5
[   48.381479] scsi 1:0:1:0: CD-ROM            SAMSUNG  CD-ROM SC-148A   B401 PQ: 0 ANSI: 5
[   48.381579] ata_piix 0000:00:1f.2: MAP [ P0 -- P1 -- ]
[   48.381604] ACPI: PCI Interrupt 0000:00:1f.2[A] -> GSI 18 (level, low) -> IRQ 18
[   48.381655] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[   48.381853] scsi3 : ata_piix
[   48.382020] scsi4 : ata_piix
[   48.382072] ata3: SATA max UDMA/133 cmd 0xd400 ctl 0xd000 bmdma 0xc400 irq 18
[   48.382077] ata4: SATA max UDMA/133 cmd 0xcc00 ctl 0xc800 bmdma 0xc408 irq 18
[   48.709946] ACPI: PCI Interrupt 0000:02:0e.0[A] -> GSI 21 (level, low) -> IRQ 20
[   48.759702] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[20]  MMIO=[feaff000-feaff7ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[   48.759799] 8139cp 0000:02:0f.0: This (id 10ec:8139 rev 10) is not an 8139C+ compatible chip
[   48.759805] 8139cp 0000:02:0f.0: Try the "8139too" driver instead.
[   48.768791] 8139too Fast Ethernet driver 0.9.28
[   48.768899] ACPI: PCI Interrupt 0000:02:0f.0[A] -> GSI 19 (level, low) -> IRQ 17
[   48.769796] eth0: RealTek RTL8139 at 0xb400, 00:0e:a6:a8:34:8a, IRQ 17
[   48.769800] eth0:  Identified 8139 chip type 'RTL-8101'
[   48.784467] Driver 'sd' needs updating - please use bus_type methods
[   48.784588] sd 0:0:0:0: [sda] 312581808 512-byte hardware sectors (160042 MB)
[   48.784610] sd 0:0:0:0: [sda] Write Protect is off
[   48.784615] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   48.784647] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   48.784737] sd 0:0:0:0: [sda] 312581808 512-byte hardware sectors (160042 MB)
[   48.784755] sd 0:0:0:0: [sda] Write Protect is off
[   48.784759] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   48.784790] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   48.784796]  sda:<4>Driver 'sr' needs updating - please use bus_type methods
[   48.808193]  sda1 sda2 sda3 sda4 < sda5 sda6 sda7 >
[   48.841943] sd 0:0:0:0: [sda] Attached SCSI disk
[   48.848712] sd 0:0:0:0: Attached scsi generic sg0 type 0
[   48.848744] sr 1:0:0:0: Attached scsi generic sg1 type 5
[   48.848775] scsi 1:0:1:0: Attached scsi generic sg2 type 5
[   48.851426] sr0: scsi3-mmc drive: 40x/40x writer cd/rw xa/form2 cdda tray
[   48.851434] Uniform CD-ROM driver Revision: 3.20
[   48.851514] sr 1:0:0:0: Attached scsi CD-ROM sr0
[   48.855627] sr1: scsi3-mmc drive: 1x/48x cd/rw xa/form2 cdda tray
[   48.855695] sr 1:0:1:0: Attached scsi CD-ROM sr1
[   49.465209] Attempting manual resume
[   49.465213] swsusp: Resume From Partition 8:7
[   49.465215] PM: Checking swsusp image.
[   49.465491] PM: Resume from disk failed.
[   49.506263] kjournald starting.  Commit interval 5 seconds
[   49.506278] EXT3-fs: mounted filesystem with ordered data mode.
[   50.029978] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[00e01800006e6f15]
[   53.091332] usb-storage: device scan complete
[   53.094311] scsi 2:0:0:0: Direct-Access     Generic  USB SD Reader    1.00 PQ: 0 ANSI: 0
[   53.097311] scsi 2:0:0:1: Direct-Access     Generic  USB CF Reader    1.01 PQ: 0 ANSI: 0
[   53.100307] scsi 2:0:0:2: Direct-Access     Generic  USB SM Reader    1.02 PQ: 0 ANSI: 0
[   53.103310] scsi 2:0:0:3: Direct-Access     Generic  USB MS Reader    1.03 PQ: 0 ANSI: 0
[   53.147287] sd 2:0:0:0: [sdb] Attached SCSI removable disk
[   53.147332] sd 2:0:0:0: Attached scsi generic sg3 type 0
[   53.190231] sd 2:0:0:1: [sdc] Attached SCSI removable disk
[   53.190266] sd 2:0:0:1: Attached scsi generic sg4 type 0
[   53.233182] sd 2:0:0:2: [sdd] Attached SCSI removable disk
[   53.233219] sd 2:0:0:2: Attached scsi generic sg5 type 0
[   53.276136] sd 2:0:0:3: [sde] Attached SCSI removable disk
[   53.276173] sd 2:0:0:3: Attached scsi generic sg6 type 0
[   59.053588] input: PC Speaker as /devices/platform/pcspkr/input/input2
[   59.288968] intel_rng: FWH not detected
[   59.336961] Linux agpgart interface v0.102
[   59.471784] parport_pc 00:07: reported by Plug and Play ACPI
[   59.471839] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
[   59.512775] agpgart: Detected an Intel 865 Chipset.
[   59.516676] agpgart: AGP aperture is 64M @ 0xf8000000
[   59.560657] iTCO_vendor_support: vendor-support=0
[   59.624605] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.02 (26-Jul-2007)
[   59.624732] iTCO_wdt: Found a ICH5 or ICH5R TCO device (Version=1, TCOBASE=0x0860)
[   59.624777] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   59.703494] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   59.776580] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   59.943494] input: Power Button (FF) as /devices/virtual/input/input3
[   60.027331] ACPI: Power Button (FF) [PWRF]
[   60.027495] input: Power Button (CM) as /devices/virtual/input/input4
[   60.075181] ACPI: Power Button (CM) [PWRB]
[   61.524691] nvidia: module license 'NVIDIA' taints kernel.
[   61.789111] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 16
[   61.789398] NVRM: loading NVIDIA UNIX x86 Kernel Module  169.12  Thu Feb 14 17:53:07 PST 2008
[   61.793501] eth0: link up, 10Mbps, half-duplex, lpa 0x4021
[   61.918358] ACPI: PCI Interrupt 0000:00:1f.5[B] -> GSI 17 (level, low) -> IRQ 21
[   61.918396] PCI: Setting latency timer of device 0000:00:1f.5 to 64
[   62.241002] intel8x0_measure_ac97_clock: measured 52730 usecs
[   62.241008] intel8x0: clocking to 48000
[   62.523451] input: ImPS/2 Generic Wheel Mouse as /devices/platform/i8042/serio1/input/input5
[   62.548099] NET: Registered protocol family 10
[   62.548588] lo: Disabled Privacy Extensions
[   63.682995] lp0: using parport0 (interrupt-driven).
[   63.774921] Adding 1141520k swap on /dev/sda7.  Priority:-1 extents:1 across:1141520k
[   64.330915] EXT3 FS on sda6, internal journal
[   64.467703] device-mapper: uevent: version 1.0.3
[   64.467750] device-mapper: ioctl: 4.12.0-ioctl (2007-10-02) initialised: [email]dm-devel@redhat.com[/email]
[   65.696625] ip_tables: (C) 2000-2006 Netfilter Core Team
[   66.285669] No dock devices found.
[   67.455404] ppdev: user-space parallel port driver
[   67.737160] audit(1216200952.183:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=5230 profile="/usr/sbin/cupsd" namespace="default"
[   67.975819] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[   67.975829] apm: disabled - APM is not SMP safe.
[   70.585818] Bluetooth: Core ver 2.11
[   70.586276] NET: Registered protocol family 31
[   70.586284] Bluetooth: HCI device and connection manager initialized
[   70.586292] Bluetooth: HCI socket layer initialized
[   70.665061] Bluetooth: L2CAP ver 2.9
[   70.665070] Bluetooth: L2CAP socket layer initialized
[   70.755670] Bluetooth: RFCOMM socket layer initialized
[   70.755694] Bluetooth: RFCOMM TTY layer initialized
[   70.755697] Bluetooth: RFCOMM ver 1.8
[   73.106469] eth0: no IPv6 routers present
[   73.163649] agpgart: Found an AGP 3.0 compliant device at 0000:00:00.0.
[   73.163666] agpgart: Putting AGP V3 device at 0000:00:00.0 into 8x mode
[   73.163703] agpgart: Putting AGP V3 device at 0000:01:00.0 into 8x mode
[ 1097.682226] usb 5-8: new high speed USB device using ehci_hcd and address 3
[ 1097.815288] usb 5-8: configuration #1 chosen from 1 choice
[ 1097.816184] scsi5 : SCSI emulation for USB Mass Storage devices
[ 1097.816690] usb-storage: device found at 3
[ 1097.816696] usb-storage: waiting for device to settle before scanning
[ 1102.809509] usb-storage: device scan complete
[ 1102.811628] usb 5-8: USB disconnect, address 3
[ 1715.579913] usb 5-7: new high speed USB device using ehci_hcd and address 4
[ 1715.713066] usb 5-7: configuration #1 chosen from 1 choice
[ 1715.759624] scsi6 : SCSI emulation for USB Mass Storage devices
[ 1715.764700] usb-storage: device found at 4
[ 1715.764707] usb-storage: waiting for device to settle before scanning
[ 1720.759729] usb-storage: device scan complete
[ 1720.761847] usb 5-7: USB disconnect, address 4




2. lsusb

Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 002: ID 058f:9360 Alcor Micro Corp. 8-in-1 Media Card Reader
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000



Can anyone help me?

---

### Post by Mark Phelps on 2008-07-16
You've got a lot of USB devices connected -- I'm guessing you have some kind of USB hub for them.  If so, have you tried plugging the device directly into a PC USB connector?

Also, have you confirmed that the USB device is the same USB version (i.e., 2.0) as the PC and/or hub support?  I've found that plugging in a USB 2.0 device to a USB 1.1 port or hub generally results in the device not being recognized.

---

### Post by morningwoodnews on 2008-07-16
Actually, the only usb's I have hooked up is a printer and wireless internet. 

The MP3 worked fine in Gutsy.

---

### Post by hansdown on 2008-07-16
Hi morningwoodnews. There is a thread dealing with this.[http://ubuntuforums.org/showthread.php?t=250046](http://ubuntuforums.org/showthread.php?t=250046) I hope it helps.

---

### Post by morningwoodnews on 2008-07-16
More info-


1. sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
240 heads, 63 sectors/track, 20673 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes
Disk identifier: 0xd3e3d3e3

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         765     5783368+   c  W95 FAT32 (LBA)
/dev/sda2   *         766       12723    90402480    7  HPFS/NTFS
/dev/sda3           12724       16967    32084640   83  Linux
/dev/sda4           16968       20673    28017360    5  Extended
/dev/sda5           20474       20673     1511968+  82  Linux swap / Solaris
/dev/sda6   *       16968       20322    25363737   83  Linux
/dev/sda7           20323       20473     1141528+  82  Linux swap / Solaris

Partition table entries are not in disk order


2. cat /etc/fstab


# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda6
UUID=c5db7a6f-1a55-4295-b341-ea20bc8ed8df /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda7
UUID=18ddbddf-6875-4711-9745-e0269807a062 none            swap    sw              0       0
/dev/scd1       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/scd0       /media/cdrom1   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0


3. df -h

Filesystem            Size  Used Avail Use% Mounted on
/dev/sda6              24G  7.4G   16G  33% /
varrun                252M   96K  252M   1% /var/run
varlock               252M     0  252M   0% /var/lock
udev                  252M   80K  252M   1% /dev
devshm                252M   12K  252M   1% /dev/shm
lrm                   252M   39M  213M  16% /lib/modules/2.6.24-19-generic/volatile


4. dmesg|grep scsi


[   30.904080] scsi0 : ata_piix
[   30.904587] scsi1 : ata_piix
[   31.558183] scsi2 : SCSI emulation for USB Mass Storage devices
[   31.902391] scsi 0:0:0:0: Direct-Access     ATA      SAMSUNG SP1604N  TM10 PQ: 0 ANSI: 5
[   31.904672] scsi 1:0:0:0: CD-ROM            HP       DVD Writer 300n  3.11 PQ: 0 ANSI: 5
[   31.905657] scsi 1:0:1:0: CD-ROM            SAMSUNG  CD-ROM SC-148A   B401 PQ: 0 ANSI: 5
[   31.905910] scsi3 : ata_piix
[   31.905984] scsi4 : ata_piix
[   32.312254] sd 0:0:0:0: Attached scsi generic sg0 type 0
[   32.312280] sr 1:0:0:0: Attached scsi generic sg1 type 5
[   32.312301] scsi 1:0:1:0: Attached scsi generic sg2 type 5
[   32.316262] sr0: scsi3-mmc drive: 40x/40x writer cd/rw xa/form2 cdda tray
[   32.316371] sr 1:0:0:0: Attached scsi CD-ROM sr0
[   32.320671] sr1: scsi3-mmc drive: 1x/48x cd/rw xa/form2 cdda tray
[   32.320773] sr 1:0:1:0: Attached scsi CD-ROM sr1
[   36.554045] scsi 2:0:0:0: Direct-Access     Generic  USB SD Reader    1.00 PQ: 0 ANSI: 0
[   36.557042] scsi 2:0:0:1: Direct-Access     Generic  USB CF Reader    1.01 PQ: 0 ANSI: 0
[   36.560038] scsi 2:0:0:2: Direct-Access     Generic  USB SM Reader    1.02 PQ: 0 ANSI: 0
[   36.563037] scsi 2:0:0:3: Direct-Access     Generic  USB MS Reader    1.03 PQ: 0 ANSI: 0
[   36.607063] sd 2:0:0:0: Attached scsi generic sg3 type 0
[   36.649999] sd 2:0:0:1: Attached scsi generic sg4 type 0
[   36.692950] sd 2:0:0:2: Attached scsi generic sg5 type 0
[   36.735900] sd 2:0:0:3: Attached scsi generic sg6 type 0

Thanks

---

