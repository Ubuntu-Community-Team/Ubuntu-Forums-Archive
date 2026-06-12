---
title: "NOT AGAIN!! Resume failed!"
date: 2009-04-19
forum: Hardware
---

### Post by kakyoism on 2009-04-19
Suspend/Resume of my laptop has been working perfectly for quite a while.
Recently it can't resume, below is my dmesg result after the forced reboot and syslog (around 19:37 the reboot)

dmesg
```
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.24-23-server (buildd@palmer) (gcc version 4.2.4 (Ubuntu 4.2.4-1ubuntu3)) #1 SMP Wed Apr 1 22:22:14 UTC 2009 (Ubuntu 2.6.24-23.52-server)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
[    0.000000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000dc000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 00000000bf6d0000 (usable)
[    0.000000]  BIOS-e820: 00000000bf6d0000 - 00000000bf6e3000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000bf6e3000 - 00000000c0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed00000 - 00000000fed00400 (reserved)
[    0.000000]  BIOS-e820: 00000000fed14000 - 00000000fed1a000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed1c000 - 00000000fed90000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000ff000000 - 0000000100000000 (reserved)
[    0.000000]  BIOS-e820: 0000000100000000 - 0000000140000000 (usable)
[    0.000000] 4224MB HIGHMEM available.
[    0.000000] 896MB LOWMEM available.
[    0.000000] found SMP MP-table at 000f8520
[    0.000000] NX (Execute Disable) protection: active
[    0.000000] Entering add_active_range(0, 0, 1310720) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   229376
[    0.000000]   HighMem    229376 ->  1310720
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->  1310720
[    0.000000] On node 0 totalpages: 1310720
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 1760 pages used for memmap
[    0.000000]   Normal zone: 223520 pages, LIFO batch:31
[    0.000000]   HighMem zone: 8448 pages used for memmap
[    0.000000]   HighMem zone: 1072896 pages, LIFO batch:31
[    0.000000]   Movable zone: 0 pages used for memmap
[    0.000000] DMI present.
[    0.000000] ACPI: RSDP signature @ 0xC00F8480 checksum 0
[    0.000000] ACPI: RSDP 000F8480, 0024 (r2 HP    )
[    0.000000] ACPI: XSDT BF6D5AEB, 0084 (r1 HPQOEM SLIC-MPC  6040000  LTP        0)
[    0.000000] ACPI: FACP BF6DFC6C, 00F4 (r3 HP     30CC      6040000 ALAN        1)
[    0.000000] ACPI: DSDT BF6D703C, 8BBC (r1 HP     30CC      6040000 INTL 20061109)
[    0.000000] ACPI: FACS BF6E2FC0, 0040
[    0.000000] ACPI: HPET BF6DFD60, 0038 (r1 HP     30CC      6040000 LOHR       5A)
[    0.000000] ACPI: MCFG BF6DFD98, 003C (r1 HP     30CC      6040000 LOHR       5A)
[    0.000000] ACPI: TMOR BF6DFDD4, 0026 (r1 HP     30CC      6040000 PTL         3)
[    0.000000] ACPI: APIC BF6DFDFA, 0068 (r1 HP     30CC      6040000  LTP        0)
[    0.000000] ACPI: BOOT BF6DFE62, 0028 (r1 HP     30CC      6040000  LTP        1)
[    0.000000] ACPI: SLIC BF6DFE8A, 0176 (r1 HPQOEM SLIC-MPC  6040000  LTP        1)
[    0.000000] ACPI: SSDT BF6D6D5F, 02DD (r1 HP     30CC         1000 INTL 20061109)
[    0.000000] ACPI: SSDT BF6D6CB7, 00A8 (r1 HP     30CC         1000 INTL 20061109)
[    0.000000] ACPI: SSDT BF6D60FB, 025F (r1  HP    30CC         3000 INTL 20061109)
[    0.000000] ACPI: SSDT BF6D6055, 00A6 (r1  HP    30CC         3000 INTL 20061109)
[    0.000000] ACPI: SSDT BF6D5B6F, 04E6 (r1  HP     30CC        3000 INTL 20061109)
[    0.000000] ACPI: DMI detected: Hewlett-Packard
[    0.000000] ACPI: PM-Timer IO Port: 0x1008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] Processor #0 6:15 APIC version 20
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
[    0.000000] Processor #1 6:15 APIC version 20
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 high edge)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] Allocating PCI resources starting at c2000000 (gap: c0000000:20000000)
[    0.000000] swsusp: Registered nosave memory region: 000000000009f000 - 00000000000a0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000a0000 - 00000000000dc000
[    0.000000] swsusp: Registered nosave memory region: 00000000000dc000 - 0000000000100000
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 1300480
[    0.000000] Kernel command line: root=UUID=96bbbef5-3316-44cc-b0a2-7f489b657f17 ro quiet splash
[    0.000000] mapped APIC to ffffb000 (fee00000)
[    0.000000] mapped IOAPIC to ffffa000 (fec00000)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] Detected 1995.308 MHz processor.
[   14.669684] Console: colour VGA+ 80x25
[   14.669687] console [tty0] enabled
[   14.669975] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[   14.670255] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[   14.918828] Memory: 4129608k/5242880k available (2258k kernel code, 53908k reserved, 1037k data, 384k init, 3267392k highmem)
[   14.918835] virtual kernel memory layout:
[   14.918836]     fixmap  : 0xfff4c000 - 0xfffff000   ( 716 kB)
[   14.918837]     pkmap   : 0xffc00000 - 0xffe00000   (2048 kB)
[   14.918838]     vmalloc : 0xf8800000 - 0xffbfe000   ( 115 MB)
[   14.918839]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
[   14.918840]       .init : 0xc043e000 - 0xc049e000   ( 384 kB)
[   14.918840]       .data : 0xc0334a39 - 0xc0437fe4   (1037 kB)
[   14.918841]       .text : 0xc0100000 - 0xc0334a39   (2258 kB)
[   14.918844] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   14.918885] SLUB: Genslabs=11, HWalign=64, Order=0-1, MinObjects=4, CPUs=2, Nodes=1
[   14.919015] hpet clockevent registered
[   15.068954] Calibrating delay using timer specific routine.. 3993.81 BogoMIPS (lpj=19969087)
[   15.068975] Security Framework initialized
[   15.068981] SELinux:  Disabled at boot.
[   15.068993] AppArmor: AppArmor initialized
[   15.068997] Failure registering capabilities with primary security module.
[   15.069005] Mount-cache hash table entries: 512
[   15.069114] Initializing cgroup subsys ns
[   15.069119] Initializing cgroup subsys cpuacct
[   15.069128] CPU: After generic identify, caps: bfebfbff 20100000 00000000 00000000 0000e39d 00000000 00000001 00000000
[   15.069135] monitor/mwait feature present.
[   15.069136] using mwait in idle threads.
[   15.069140] CPU: L1 I cache: 32K, L1 D cache: 32K
[   15.069142] CPU: L2 cache: 2048K
[   15.069144] CPU: Physical Processor ID: 0
[   15.069145] CPU: Processor Core ID: 0
[   15.069147] CPU: After all inits, caps: bfebfbff 20100000 00000000 00043940 0000e39d 00000000 00000001 00000000
[   15.069155] Compat vDSO mapped to ffffe000.
[   15.069167] Checking 'hlt' instruction... OK.
[   15.109297] SMP alternatives: switching to UP code
[   15.110662] Early unpacking initramfs... done
[   15.414653] ACPI: Core revision 20070126
[   15.414701] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[   15.485430] CPU0: Intel(R) Core(TM)2 Duo CPU     T5750  @ 2.00GHz stepping 0d
[   15.485444] SMP alternatives: switching to SMP code
[   15.486074] Booting processor 1/1 eip 3000
[   15.496339] Initializing CPU#1
[   15.638696] Calibrating delay using timer specific routine.. 3990.28 BogoMIPS (lpj=19951418)
[   15.638702] CPU: After generic identify, caps: bfebfbff 20100000 00000000 00000000 0000e39d 00000000 00000001 00000000
[   15.638706] monitor/mwait feature present.
[   15.638708] CPU: L1 I cache: 32K, L1 D cache: 32K
[   15.638710] CPU: L2 cache: 2048K
[   15.638712] CPU: Physical Processor ID: 0
[   15.638713] CPU: Processor Core ID: 1
[   15.638714] CPU: After all inits, caps: bfebfbff 20100000 00000000 00043940 0000e39d 00000000 00000001 00000000
[   15.639172] CPU1: Intel(R) Core(TM)2 Duo CPU     T5750  @ 2.00GHz stepping 0d
[   15.639193] Total of 2 processors activated (7984.10 BogoMIPS).
[   15.639370] ENABLING IO-APIC IRQs
[   15.639558] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[   15.858696] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
[   15.878699] Brought up 2 CPUs
[   15.878717] CPU0 attaching sched-domain:
[   15.878719]  domain 0: span 03
[   15.878720]   groups: 01 02
[   15.878723] CPU1 attaching sched-domain:
[   15.878724]  domain 0: span 03
[   15.878726]   groups: 02 01
[   15.878910] net_namespace: 64 bytes
[   15.878920] Booting paravirtualized kernel on bare hardware
[   15.879330] Time: 23:37:17  Date: 04/19/09
[   15.879354] NET: Registered protocol family 16
[   15.879510] EISA bus registered
[   15.879514] ACPI: bus type pci registered
[   15.879900] PCI: PCI BIOS revision 3.00 entry at 0xfde31, last bus=9
[   15.879902] PCI: Using configuration type 1
[   15.879915] Setting up standard PCI resources
[   15.882069] ACPI: EC: Look up EC in DSDT
[   15.884076] ACPI: BIOS _OSI(Linux) query ignored via DMI
[   15.885091] ACPI: Interpreter enabled
[   15.885094] ACPI: (supports S0 S3 S4 S5)
[   15.885106] ACPI: Using IOAPIC for interrupt routing
[   15.886388] ACPI: EC: non-query interrupt received, switching to interrupt mode
[   15.894608] ACPI: EC: GPE = 0x17, I/O: command/status = 0x66, data = 0x62
[   15.894610] ACPI: EC: driver started in interrupt mode
[   15.894647] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   15.895658] PCI quirk: region 1000-107f claimed by ICH6 ACPI/GPIO/TCO
[   15.895663] PCI quirk: region 1180-11bf claimed by ICH6 GPIO
[   15.896897] PCI: Transparent bridge - 0000:00:1e.0
[   15.896943] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   15.897210] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP01._PRT]
[   15.897326] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP02._PRT]
[   15.897439] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP06._PRT]
[   15.897564] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIB._PRT]
[   15.906722] ACPI: PCI Interrupt Link [LNKA] (IRQs 1 3 4 *5 6 7 10 12 14 15)
[   15.906816] ACPI: PCI Interrupt Link [LNKB] (IRQs 1 3 4 5 6 7 11 12 14 15) *10
[   15.906908] ACPI: PCI Interrupt Link [LNKC] (IRQs 1 3 4 5 6 *7 10 12 14 15)
[   15.907000] ACPI: PCI Interrupt Link [LNKD] (IRQs 1 3 4 5 6 7 11 12 14 15) *10
[   15.907094] ACPI: PCI Interrupt Link [LNKE] (IRQs 1 3 4 5 6 7 10 12 14 15) *11
[   15.907185] ACPI: PCI Interrupt Link [LNKF] (IRQs 1 3 4 5 6 7 *11 12 14 15)
[   15.907276] ACPI: PCI Interrupt Link [LNKG] (IRQs 1 3 4 5 6 7 10 12 14 15) *11
[   15.907367] ACPI: PCI Interrupt Link [LNKH] (IRQs 1 3 4 5 6 7 11 12 14 15) *10
[   15.907493] Linux Plug and Play Support v0.97 (c) Adam Belay
[   15.907517] pnp: PnP ACPI init
[   15.907523] ACPI: bus type pnp registered
[   15.910981] pnp: PnP ACPI: found 11 devices
[   15.910983] ACPI: ACPI bus type pnp unregistered
[   15.910986] PnPBIOS: Disabled by ACPI PNP
[   15.911165] PCI: Using ACPI for IRQ routing
[   15.911167] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   16.048623] NET: Registered protocol family 8
[   16.048625] NET: Registered protocol family 20
[   16.048647] NetLabel: Initializing
[   16.048648] NetLabel:  domain hash size = 128
[   16.048649] NetLabel:  protocols = UNLABELED CIPSOv4
[   16.048659] NetLabel:  unlabeled traffic allowed by default
[   16.048665] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[   16.048669] hpet0: 3 64-bit timers, 14318180 Hz
[   16.049697] AppArmor: AppArmor Filesystem Enabled
[   16.058514] Time: tsc clocksource has been installed.
[   16.058526] Switched to high resolution mode on CPU 0
[   16.058613] Switched to high resolution mode on CPU 1
[   16.091024] system 00:01: iomem range 0xfed1c000-0xfed1ffff could not be reserved
[   16.091027] system 00:01: iomem range 0xfed14000-0xfed17fff could not be reserved
[   16.091030] system 00:01: iomem range 0xfed18000-0xfed18fff could not be reserved
[   16.091032] system 00:01: iomem range 0xfed19000-0xfed19fff could not be reserved
[   16.091034] system 00:01: iomem range 0xe0000000-0xefffffff could not be reserved
[   16.091037] system 00:01: iomem range 0xfed20000-0xfed3ffff could not be reserved
[   16.091039] system 00:01: iomem range 0xfed40000-0xfed44fff could not be reserved
[   16.091042] system 00:01: iomem range 0xfed45000-0xfed8ffff could not be reserved
[   16.091048] system 00:04: iomem range 0xfed00000-0xfed003ff could not be reserved
[   16.091054] system 00:06: ioport range 0x380-0x383 has been reserved
[   16.091056] system 00:06: ioport range 0x680-0x69f has been reserved
[   16.091058] system 00:06: ioport range 0x800-0x80f has been reserved
[   16.091060] system 00:06: ioport range 0x1000-0x107f has been reserved
[   16.091062] system 00:06: ioport range 0x1180-0x11bf has been reserved
[   16.091064] system 00:06: ioport range 0x1640-0x164f has been reserved
[   16.091067] system 00:06: ioport range 0xfe00-0xfe00 has been reserved
[   16.091071] system 00:07: ioport range 0x6a0-0x6af has been reserved
[   16.091074] system 00:07: ioport range 0x6b0-0x6ff has been reserved
[   16.121405] PCI: Bridge: 0000:00:1c.0
[   16.121409]   IO window: 4000-7fff
[   16.121414]   MEM window: f4000000-f5ffffff
[   16.121419]   PREFETCH window: f0000000-f1ffffff
[   16.121425] PCI: Bridge: 0000:00:1c.1
[   16.121428]   IO window: 8000-bfff
[   16.121434]   MEM window: f6000000-f7ffffff
[   16.121438]   PREFETCH window: f2000000-f3ffffff
[   16.121444] PCI: Bridge: 0000:00:1c.5
[   16.121447]   IO window: c000-cfff
[   16.121452]   MEM window: f8200000-f82fffff
[   16.121456]   PREFETCH window: c2000000-c20fffff
[   16.121463] PCI: Bridge: 0000:00:1e.0
[   16.121464]   IO window: disabled.
[   16.121470]   MEM window: f8300000-f83fffff
[   16.121474]   PREFETCH window: disabled.
[   16.121506] ACPI: PCI Interrupt 0000:00:1c.0[A] -> GSI 17 (level, low) -> IRQ 16
[   16.121512] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[   16.121537] ACPI: PCI Interrupt 0000:00:1c.1[B] -> GSI 16 (level, low) -> IRQ 17
[   16.121542] PCI: Setting latency timer of device 0000:00:1c.1 to 64
[   16.121567] ACPI: PCI Interrupt 0000:00:1c.5[B] -> GSI 16 (level, low) -> IRQ 17
[   16.121572] PCI: Setting latency timer of device 0000:00:1c.5 to 64
[   16.121587] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[   16.121596] NET: Registered protocol family 2
[   16.220993] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[   16.221190] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[   16.221576] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[   16.221777] TCP: Hash tables configured (established 131072 bind 65536)
[   16.221779] TCP reno registered
[   16.251042] checking if image is initramfs... it is
[   16.847251] Freeing initrd memory: 7759k freed
[   16.847391] Simple Boot Flag at 0x35 set to 0x1
[   16.847914] audit: initializing netlink socket (disabled)
[   16.847926] audit(1240184237.680:1): initialized
[   16.848319] highmem bounce pool size: 64 pages
[   16.848322] Total HugeTLB memory allocated, 0
[   16.849969] VFS: Disk quotas dquot_6.5.1
[   16.850034] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   16.850205] io scheduler noop registered
[   16.850207] io scheduler anticipatory registered
[   16.850209] io scheduler deadline registered (default)
[   16.850220] io scheduler cfq registered
[   16.850230] Boot video device is 0000:00:02.0
[   16.850447] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[   16.850509] assign_interrupt_mode Found MSI capability
[   16.850561] Allocate Port Service[0000:00:1c.0:pcie00]
[   16.850591] Allocate Port Service[0000:00:1c.0:pcie02]
[   16.850700] PCI: Setting latency timer of device 0000:00:1c.1 to 64
[   16.850761] assign_interrupt_mode Found MSI capability
[   16.850809] Allocate Port Service[0000:00:1c.1:pcie00]
[   16.850837] Allocate Port Service[0000:00:1c.1:pcie02]
[   16.850938] PCI: Setting latency timer of device 0000:00:1c.5 to 64
[   16.850999] assign_interrupt_mode Found MSI capability
[   16.851047] Allocate Port Service[0000:00:1c.5:pcie00]
[   16.851072] Allocate Port Service[0000:00:1c.5:pcie02]
[   16.851298] isapnp: Scanning for PnP cards...
[   17.208433] isapnp: No Plug & Play device found
[   17.228480] Real Time Clock Driver v1.12ac
[   17.228683] hpet_resources: 0xfed00000 is busy
[   17.228709] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   17.229727] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   17.229786] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[   17.229867] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[   17.271250] serio: i8042 KBD port at 0x60,0x64 irq 1
[   17.271254] serio: i8042 AUX port at 0x60,0x64 irq 12
[   17.308064] mice: PS/2 mouse device common for all mice
[   17.308161] EISA: Probing bus 0 at eisa.0
[   17.308168] Cannot allocate resource for EISA slot 1
[   17.308180] Cannot allocate resource for EISA slot 4
[   17.308182] Cannot allocate resource for EISA slot 5
[   17.308184] Cannot allocate resource for EISA slot 6
[   17.308185] Cannot allocate resource for EISA slot 7
[   17.308187] Cannot allocate resource for EISA slot 8
[   17.308189] EISA: Detected 0 cards.
[   17.308191] cpuidle: using governor ladder
[   17.308193] cpuidle: using governor menu
[   17.308269] NET: Registered protocol family 1
[   17.308294] Using IPI No-Shortcut mode
[   17.308324] registered taskstats version 1
[   17.308435]   Magic number: 5:437:656
[   17.308503] BIOS EDD facility v0.16 2004-Jun-25, 6 devices found
[   17.308845] Freeing unused kernel memory: 384k freed
[   17.308884] Write protecting the kernel read-only data: 828k
[   17.337691] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[   18.502380] fuse init (API version 7.9)
[   18.519533] ACPI: SSDT BF6D69B7, 0238 (r1  HP    30CC         3000 INTL 20061109)
[   18.519737] ACPI: SSDT BF6D635A, 05D8 (r1  HP    30CC         3001 INTL 20061109)
[   18.521380] Monitor-Mwait will be used to enter C-1 state
[   18.521383] Monitor-Mwait will be used to enter C-2 state
[   18.521385] Monitor-Mwait will be used to enter C-3 state
[   18.521486] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[   18.521490] ACPI: Processor [CPU0] (supports 8 throttling states)
[   18.521691] ACPI: SSDT BF6D6BEF, 00C8 (r1  HP    30CC         3000 INTL 20061109)
[   18.521880] ACPI: SSDT BF6D6932, 0085 (r1  HP    30CC         3000 INTL 20061109)
[   18.522709] Marking TSC unstable due to: TSC halts in idle.
[   18.522758] ACPI: CPU1 (power states: C1[C1] C2[C2] C3[C3])
[   18.522763] ACPI: Processor [CPU1] (supports 8 throttling states)
[   18.524486] ACPI Exception (thermal-0339): AE_BAD_DATA, No critical threshold [20070126]
[   18.527501] Time: hpet clocksource has been installed.
[   18.778300] usbcore: registered new interface driver usbfs
[   18.778322] usbcore: registered new interface driver hub
[   18.785322] usbcore: registered new device driver usb
[   18.787420] ACPI: PCI Interrupt 0000:00:1a.7[C] -> GSI 18 (level, low) -> IRQ 18
[   18.787433] PCI: Setting latency timer of device 0000:00:1a.7 to 64
[   18.787437] ehci_hcd 0000:00:1a.7: EHCI Host Controller
[   18.787653] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 1
[   18.791580] ehci_hcd 0000:00:1a.7: debug port 1
[   18.791588] PCI: cache line size of 32 is not supported by device 0000:00:1a.7
[   18.791597] ehci_hcd 0000:00:1a.7: irq 18, io mem 0xf8604800
[   18.797574] USB Universal Host Controller Interface driver v3.0
[   18.809907] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   18.810020] usb usb1: configuration #1 chosen from 1 choice
[   18.810045] hub 1-0:1.0: USB hub found
[   18.810051] hub 1-0:1.0: 4 ports detected
[   18.857773] SCSI subsystem initialized
[   18.878668] libata version 3.00 loaded.
[   18.919929] ACPI: PCI Interrupt 0000:00:1a.0[A] -> GSI 16 (level, low) -> IRQ 17
[   18.919942] PCI: Setting latency timer of device 0000:00:1a.0 to 64
[   18.919946] uhci_hcd 0000:00:1a.0: UHCI Host Controller
[   18.919973] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 2
[   18.920006] uhci_hcd 0000:00:1a.0: irq 17, io base 0x00001820
[   18.920105] usb usb2: configuration #1 chosen from 1 choice
[   18.920124] hub 2-0:1.0: USB hub found
[   18.920129] hub 2-0:1.0: 2 ports detected
[   19.027408] ACPI: PCI Interrupt 0000:00:1a.1[B] -> GSI 21 (level, low) -> IRQ 19
[   19.027420] PCI: Setting latency timer of device 0000:00:1a.1 to 64
[   19.027424] uhci_hcd 0000:00:1a.1: UHCI Host Controller
[   19.027444] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 3
[   19.027477] uhci_hcd 0000:00:1a.1: irq 19, io base 0x00001840
[   19.027581] usb usb3: configuration #1 chosen from 1 choice
[   19.027602] hub 3-0:1.0: USB hub found
[   19.027606] hub 3-0:1.0: 2 ports detected
[   19.137360] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 23 (level, low) -> IRQ 20
[   19.137372] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[   19.137376] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[   19.137397] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 4
[   19.137428] uhci_hcd 0000:00:1d.0: irq 20, io base 0x00001860
[   19.137536] usb usb4: configuration #1 chosen from 1 choice
[   19.137556] hub 4-0:1.0: USB hub found
[   19.137560] hub 4-0:1.0: 2 ports detected
[   19.247303] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 19 (level, low) -> IRQ 21
[   19.247315] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[   19.247319] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[   19.247339] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 5
[   19.247371] uhci_hcd 0000:00:1d.1: irq 21, io base 0x00001880
[   19.247485] usb usb5: configuration #1 chosen from 1 choice
[   19.247505] hub 5-0:1.0: USB hub found
[   19.247509] hub 5-0:1.0: 2 ports detected
[   19.290762] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 18
[   19.290778] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[   19.290785] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[   19.290822] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 6
[   19.290857] uhci_hcd 0000:00:1d.2: irq 18, io base 0x000018a0
[   19.290955] usb usb6: configuration #1 chosen from 1 choice
[   19.290974] hub 6-0:1.0: USB hub found
[   19.290978] hub 6-0:1.0: 2 ports detected
[   19.295920] usb 3-2: new low speed USB device using uhci_hcd and address 2
[   19.309825] r8169 Gigabit Ethernet driver 2.2LK loaded
[   19.309856] ACPI: PCI Interrupt 0000:08:00.0[A] -> GSI 17 (level, low) -> IRQ 16
[   19.309877] PCI: Setting latency timer of device 0000:08:00.0 to 64
[   19.310191] eth0: RTL8101e at 0xf8878000, 00:1e:68:99:1b:73, XID 34200000 IRQ 220
[   19.312729] ahci 0000:00:1f.2: version 3.0
[   19.312753] ACPI: PCI Interrupt 0000:00:1f.2[B] -> GSI 19 (level, low) -> IRQ 21
[   19.359650] usb 3-2: configuration #1 chosen from 1 choice
[   19.371374] usbcore: registered new interface driver hiddev
[   19.374590] input: Logitech USB Optical Mouse as /devices/pci0000:00/0000:00:1a.1/usb3/3-2/3-2:1.0/input/input2
[   19.377321] Clocksource tsc unstable (delta = -290109953 ns)
[   19.380792] input,hidraw0: USB HID v1.10 Mouse [Logitech USB Optical Mouse] on usb-0000:00:1a.1-2
[   19.380817] usbcore: registered new interface driver usbhid
[   19.380822] /build/buildd/linux-2.6.24/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
[   19.457413] ahci 0000:00:1f.2: AHCI 0001.0100 32 slots 3 ports 3 Gbps 0x7 impl SATA mode
[   19.457422] ahci 0000:00:1f.2: flags: 64bit ncq sntf pm led clo pio slum part 
[   19.457432] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[   19.457740] scsi0 : ahci
[   19.457962] scsi1 : ahci
[   19.458121] scsi2 : ahci
[   19.458201] ata1: SATA max UDMA/133 abar m2048@0xf8604000 port 0xf8604100 irq 219
[   19.458204] ata2: SATA max UDMA/133 abar m2048@0xf8604000 port 0xf8604180 irq 219
[   19.458207] ata3: SATA max UDMA/133 abar m2048@0xf8604000 port 0xf8604200 irq 219
[   19.498112] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[   19.498561] ata1.00: ATA-8: WDC WD2500BEVS-60UST0, 01.01A01, max UDMA/100
[   19.498566] ata1.00: 488397168 sectors, multi 16: LBA48 
[   19.499126] ata1.00: configured for UDMA/100
[   19.520819] ata2: SATA link down (SStatus 0 SControl 300)
[   19.542590] ata3: SATA link down (SStatus 0 SControl 300)
[   19.542830] scsi 0:0:0:0: Direct-Access     ATA      WDC WD2500BEVS-6 01.0 PQ: 0 ANSI: 5
[   19.543154] ACPI: PCI Interrupt 0000:09:09.0[A] -> GSI 20 (level, low) -> IRQ 22
[   19.596309] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[22]  MMIO=[f8300000-f83007ff]  Max Packet=[2048]  IR/IT contexts=[4/4]
[   19.600376] Driver 'sd' needs updating - please use bus_type methods
[   19.600826] ata_piix 0000:00:1f.1: version 2.12
[   19.600844] ACPI: PCI Interrupt 0000:00:1f.1[A] -> GSI 19 (level, low) -> IRQ 21
[   19.600879] PCI: Setting latency timer of device 0000:00:1f.1 to 64
[   19.600922] sd 0:0:0:0: [sda] 488397168 512-byte hardware sectors (250059 MB)
[   19.600934] sd 0:0:0:0: [sda] Write Protect is off
[   19.600936] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   19.600950] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   19.600993] sd 0:0:0:0: [sda] 488397168 512-byte hardware sectors (250059 MB)
[   19.601001] sd 0:0:0:0: [sda] Write Protect is off
[   19.601003] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   19.601017] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   19.601020]  sda:<6>scsi3 : ata_piix
[   19.601123] scsi4 : ata_piix
[   19.601615] ata4: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0x1810 irq 14
[   19.601618] ata5: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x1818 irq 15
[   19.652462]  sda1 sda2
[   19.676955] sd 0:0:0:0: [sda] Attached SCSI disk
[   19.680748] sd 0:0:0:0: Attached scsi generic sg0 type 0
[   19.906333] ata4.00: ATAPI: Optiarc DVD RW AD-7561A, GH09, max MWDMA2
[   19.919684] ata4.00: configured for MWDMA2
[   19.935560] scsi 3:0:0:0: CD-ROM            Optiarc  DVD RW AD-7561A  GH09 PQ: 0 ANSI: 5
[   19.935681] scsi 3:0:0:0: Attached scsi generic sg1 type 5
[   19.936015] ACPI: PCI Interrupt 0000:00:1d.7[A] -> GSI 23 (level, low) -> IRQ 20
[   19.936029] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[   19.936032] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[   19.936058] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 7
[   19.939956] ehci_hcd 0000:00:1d.7: debug port 1
[   19.939963] PCI: cache line size of 32 is not supported by device 0000:00:1d.7
[   19.939968] ehci_hcd 0000:00:1d.7: irq 20, io mem 0xf8604c00
[   19.946409] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   19.946599] usb usb7: configuration #1 chosen from 1 choice
[   19.946638] hub 7-0:1.0: USB hub found
[   19.946643] hub 7-0:1.0: 6 ports detected
[   19.966386] Driver 'sr' needs updating - please use bus_type methods
[   19.972796] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[   19.972802] Uniform CD-ROM driver Revision: 3.20
[   19.972870] sr 3:0:0:0: Attached scsi CD-ROM sr0
[   20.030048] Attempting manual resume
[   20.030051] swsusp: Resume From Partition 8:2
[   20.030053] PM: Checking swsusp image.
[   20.030203] PM: Resume from disk failed.
[   20.042358] EXT3-fs: INFO: recovery required on readonly filesystem.
[   20.042361] EXT3-fs: write access will be enabled during recovery.
[   20.288548] usb 7-4: new high speed USB device using ehci_hcd and address 2
[   20.408875] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[00241b00e96f1601]
[   20.447627] usb 7-4: configuration #1 chosen from 1 choice
[   21.296105] kjournald starting.  Commit interval 5 seconds
[   21.296147] EXT3-fs: sda1: orphan cleanup on readonly fs
[   21.296157] ext3_orphan_cleanup: deleting unreferenced inode 1843837
[   21.296193] ext3_orphan_cleanup: deleting unreferenced inode 1843836
[   21.296202] ext3_orphan_cleanup: deleting unreferenced inode 1843812
[   21.296211] ext3_orphan_cleanup: deleting unreferenced inode 2137508
[   21.296220] ext3_orphan_cleanup: deleting unreferenced inode 1843800
[   21.317998] ext3_orphan_cleanup: deleting unreferenced inode 475177
[   21.318011] EXT3-fs: sda1: 6 orphan inodes deleted
[   21.318013] EXT3-fs: recovery complete.
[   21.361658] EXT3-fs: mounted filesystem with ordered data mode.
[   30.258086] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   30.308551] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   30.351175] Linux agpgart interface v0.102
[   30.444176] iTCO_vendor_support: vendor-support=0
[   30.520267] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.02 (26-Jul-2007)
[   30.520358] iTCO_wdt: Found a ICH8M TCO device (Version=2, TCOBASE=0x1060)
[   30.520398] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   30.681350] ACPI: WMI-Acer: Mapper loaded
[   30.709451] input: PC Speaker as /devices/platform/pcspkr/input/input3
[   30.734522] input: Power Button (FF) as /devices/virtual/input/input4
[   30.888903] ricoh-mmc: Ricoh MMC Controller disabling driver
[   30.888907] ricoh-mmc: Copyright(c) Philip Langdale
[   30.888940] ricoh-mmc: Ricoh MMC controller found at 0000:09:09.2 [1180:0843] (rev 12)
[   30.888952] ricoh-mmc: Controller is now disabled.
[   30.905170] agpgart: Detected an Intel 965GM Chipset.
[   30.906054] agpgart: Detected 7676K stolen memory.
[   30.919527] agpgart: AGP aperture is 256M @ 0xd0000000
[   31.113696] ACPI: Power Button (FF) [PWRF]
[   31.113756] input: Power Button (CM) as /devices/virtual/input/input5
[   31.220721] sdhci: Secure Digital Host Controller Interface driver
[   31.220724] sdhci: Copyright(c) Pierre Ossman
[   31.220759] sdhci: SDHCI controller found at 0000:09:09.1 [1180:0822] (rev 22)
[   31.220779] ACPI: PCI Interrupt 0000:09:09.1[B] -> GSI 21 (level, low) -> IRQ 19
[   31.220794] sdhci:slot0: Will use DMA mode even though HW doesn't fully claim to support it.
[   31.220839] mmc0: SDHCI at 0xf8300800 irq 19 DMA
[   31.253553] ACPI: Power Button (CM) [PWRB]
[   31.253606] input: Sleep Button (CM) as /devices/virtual/input/input6
[   31.403492] ACPI: Sleep Button (CM) [SLPB]
[   31.403551] input: Lid Switch as /devices/virtual/input/input7
[   31.465071] ACPI: Lid Switch [LID]
[   31.469600] Linux video capture interface: v2.00
[   31.574093] ACPI: Battery Slot [BAT0] (battery present)
[   31.577371] ACPI: AC Adapter [ACAD] (on-line)
[   31.583619] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:02/LNXVIDEO:00/input/input8
[   31.641157] iwl4965: Intel(R) Wireless WiFi Link 4965AGN driver for Linux, 1.2.0
[   31.641160] iwl4965: Copyright(c) 2003-2007 Intel Corporation
[   31.641239] ACPI: PCI Interrupt 0000:02:00.0[A] -> GSI 16 (level, low) -> IRQ 17
[   31.641250] PCI: Setting latency timer of device 0000:02:00.0 to 64
[   31.641264] iwl4965: Detected Intel Wireless WiFi Link 4965AGN
[   31.713407] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[   31.723846] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/LNXVIDEO:01/input/input9
[   31.743539] uvcvideo: Found UVC 1.00 device HP Webcam (064e:a110)
[   31.747716] usbcore: registered new interface driver uvcvideo
[   31.747723] USB Video Class driver (v0.1.0)
[   31.888387] iwl4965: Radio disabled by HW RF Kill switch
[   31.895798] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)
[   31.957124] Synaptics Touchpad, model: 1, fw: 6.3, id: 0x1a0b1, caps: 0xa04711/0xa00000
[   32.065725] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input10
[   32.091347] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 22 (level, low) -> IRQ 23
[   32.091369] PCI: Setting latency timer of device 0000:00:1b.0 to 64
[   32.486671] lp: driver loaded but no devices found
[   32.595750] Adding 4883752k swap on /dev/sda2.  Priority:-1 extents:1 across:4883752k
[   33.238950] EXT3 FS on sda1, internal journal
[   33.430784] device-mapper: uevent: version 1.0.3
[   33.430812] device-mapper: ioctl: 4.12.0-ioctl (2007-10-02) initialised: dm-devel@redhat.com
[   34.910280] ip_tables: (C) 2000-2006 Netfilter Core Team
[   35.462378] No dock devices found.
[   37.301404] NET: Registered protocol family 10
[   37.301611] lo: Disabled Privacy Extensions
[   37.577022] apm: BIOS not found.
[   37.783338] ppdev: user-space parallel port driver
[   37.972485] audit(1240184261.650:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=5395 profile="/usr/sbin/cupsd" namespace="default"
[   42.505322] r8169: eth0: link up
[   42.505335] r8169: eth0: link up
[   42.608285] Bluetooth: Core ver 2.11
[   42.608409] NET: Registered protocol family 31
[   42.608412] Bluetooth: HCI device and connection manager initialized
[   42.608418] Bluetooth: HCI socket layer initialized
[   42.641374] Bluetooth: L2CAP ver 2.9
[   42.641382] Bluetooth: L2CAP socket layer initialized
[   42.722013] Bluetooth: RFCOMM socket layer initialized
[   42.722030] Bluetooth: RFCOMM TTY layer initialized
[   42.722033] Bluetooth: RFCOMM ver 1.8
[   44.167990] NET: Registered protocol family 17
[   44.714634] [drm] Initialized drm 1.1.0 20060810
[   44.716699] ACPI: PCI Interrupt 0000:00:02.0[A] -> GSI 16 (level, low) -> IRQ 17
[   44.716708] PCI: Setting latency timer of device 0000:00:02.0 to 64
[   44.716758] [drm] Initialized i915 1.6.0 20060119 on minor 0
[   44.732413] mtrr: type mismatch for d0000000,10000000 old: write-back new: write-combining
[   45.033726] /dev/vmmon[6173]: Module vmmon: registered with major=10 minor=165
[   45.033739] /dev/vmmon[6173]: Initial HV check: anyNotCapable=1 anyUnlocked=0 anyEnabled=0 anyDisabled=0
[   45.033741] /dev/vmmon[6173]: Module vmmon: initialized
[   45.084152] /dev/vmci[6184]: VMCI: Driver initialized.
[   45.084187] /dev/vmci[6184]: Module vmci: registered with major=10 minor=62
[   45.084190] /dev/vmci[6184]: Module vmci: initialized
[   45.119323] vsock: no version for "VMCIDatagram_Send" found: kernel tainted.
[   47.058286] /dev/vmnet: open called by PID 6331 (vmnet-bridge)
[   47.058295] /dev/vmnet: hub 0 does not exist, allocating memory.
[   47.058304] /dev/vmnet: port on hub 0 successfully opened
[   47.058317] bridge-eth0: up
[   47.058320] bridge-eth0: attached
[   47.136547] /dev/vmnet: open called by PID 6343 (vmnet-netifup)
[   47.136557] /dev/vmnet: hub 1 does not exist, allocating memory.
[   47.136567] /dev/vmnet: port on hub 1 successfully opened
[   47.230626] /dev/vmnet: open called by PID 6342 (vmnet-dhcpd)
[   47.230648] /dev/vmnet: port on hub 1 successfully opened
[   47.271476] /dev/vmnet: open called by PID 6377 (vmnet-dhcpd)
[   47.271494] /dev/vmnet: hub 8 does not exist, allocating memory.
[   47.271513] /dev/vmnet: port on hub 8 successfully opened
[   47.295748] /dev/vmnet: open called by PID 6382 (vmnet-natd)
[   47.295767] /dev/vmnet: port on hub 8 successfully opened
[   52.951381] /dev/vmnet: open called by PID 6862 (vmnet-netifup)
[   52.951401] /dev/vmnet: port on hub 8 successfully opened
[   53.377916] eth0: no IPv6 routers present
[   53.834663] vmnet1: no IPv6 routers present
[   59.819328] vmnet8: no IPv6 routers present
[   83.542137] CPU0 attaching NULL sched-domain.
[   83.542150] CPU1 attaching NULL sched-domain.
[   83.555887] CPU0 attaching sched-domain:
[   83.555896]  domain 0: span 03
[   83.555900]   groups: 01 02
[   83.555906] CPU1 attaching sched-domain:
[   83.555909]  domain 0: span 03
[   83.555911]   groups: 02 01
[   83.664130] CPU0 attaching NULL sched-domain.
[   83.664135] CPU1 attaching NULL sched-domain.
[   83.717969] CPU0 attaching sched-domain:
[   83.717978]  domain 0: span 03
[   83.717981]   groups: 01 02
[   83.717987] CPU1 attaching sched-domain:
[   83.717990]  domain 0: span 03
[   83.717993]   groups: 02 01
[  142.962597] nautilus[7084]: segfault at 00000084 eip b751c694 esp bfced0d0 error 4

```

============
syslog
============
```
Apr 19 05:08:13 kakyo-laptop syslogd 1.5.0#1ubuntu1: restart.
Apr 19 05:08:13 kakyo-laptop anacron[9458]: Job `cron.daily' terminated
Apr 19 05:08:13 kakyo-laptop anacron[9458]: Normal exit (1 job run)
Apr 19 05:17:01 kakyo-laptop /USR/SBIN/CRON[12157]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Apr 19 05:28:18 kakyo-laptop -- MARK --
Apr 19 05:48:18 kakyo-laptop -- MARK --
Apr 19 06:08:18 kakyo-laptop -- MARK --
Apr 19 06:17:01 kakyo-laptop /USR/SBIN/CRON[14719]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Apr 19 06:25:01 kakyo-laptop /USR/SBIN/CRON[15054]: (root) CMD (test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.daily ))
Apr 19 06:47:01 kakyo-laptop /USR/SBIN/CRON[15990]: (root) CMD (test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.weekly ))
Apr 19 07:08:18 kakyo-laptop -- MARK --
Apr 19 07:17:01 kakyo-laptop /USR/SBIN/CRON[17258]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Apr 19 07:28:18 kakyo-laptop -- MARK --
Apr 19 07:30:01 kakyo-laptop /USR/SBIN/CRON[17812]: (root) CMD (test -x /etc/init.d/anacron && /usr/sbin/invoke-rc.d anacron start >/dev/null)
Apr 19 07:30:01 kakyo-laptop anacron[17837]: Anacron 2.3 started on 2009-04-19
Apr 19 07:30:01 kakyo-laptop anacron[17837]: Normal exit (0 jobs run)
Apr 19 07:48:18 kakyo-laptop -- MARK --
Apr 19 08:08:18 kakyo-laptop -- MARK --
Apr 19 08:17:01 kakyo-laptop /USR/SBIN/CRON[19845]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Apr 19 08:28:18 kakyo-laptop -- MARK --
Apr 19 08:48:18 kakyo-laptop -- MARK --
Apr 19 09:08:18 kakyo-laptop -- MARK --
Apr 19 09:17:01 kakyo-laptop /USR/SBIN/CRON[22419]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Apr 19 09:28:18 kakyo-laptop -- MARK --
Apr 19 09:48:18 kakyo-laptop -- MARK --
Apr 19 10:08:18 kakyo-laptop -- MARK --
Apr 19 10:17:01 kakyo-laptop /USR/SBIN/CRON[24967]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Apr 19 10:28:18 kakyo-laptop -- MARK --
Apr 19 10:48:18 kakyo-laptop -- MARK --
Apr 19 11:04:00 kakyo-laptop gnome-power-manager: (kakyo) Suspending computer. Reason: The suspend button has been pressed.
Apr 19 11:04:04 kakyo-laptop NetworkManager: <info>  Going to sleep. 
Apr 19 11:04:04 kakyo-laptop vmnetBridge: RTM_NEWLINK: name:eth0 index:6 flags:0x00001002 
Apr 19 11:04:04 kakyo-laptop vmnetBridge: Can't remove interface eth0 6 (does not exist). 
Apr 19 11:04:04 kakyo-laptop vmnetBridge: RTM_DELLINK: name:eth0 index:6 flags:0x00001002 
Apr 19 11:04:04 kakyo-laptop vmnetBridge: Can't remove interface eth0 6 (does not exist). 
Apr 19 11:04:04 kakyo-laptop NetworkManager: <debug> [1240153444.240980] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/net_00_1e_68_99_1b_73'). 
Apr 19 11:04:04 kakyo-laptop NetworkManager: <info>  Deactivating device eth0. 
Apr 19 11:04:04 kakyo-laptop kernel: [21909.951004] ACPI: PCI interrupt for device 0000:08:00.0 disabled
Apr 19 11:04:04 kakyo-laptop kernel: [21910.020275] Syncing filesystems ... done.
Apr 19 11:04:04 kakyo-laptop kernel: [21910.020296] PM: Preparing system for mem sleep
Apr 19 13:00:53 kakyo-laptop kernel: [21910.030198] Freezing user space processes ... (elapsed 0.00 seconds) done.
Apr 19 13:00:53 kakyo-laptop kernel: [21910.031129] Freezing remaining freezable tasks ... (elapsed 0.00 seconds) done.
Apr 19 13:00:53 kakyo-laptop kernel: [21910.031171] PM: Entering mem sleep
Apr 19 13:00:53 kakyo-laptop kernel: [21910.031173] Suspending console(s)
Apr 19 13:00:53 kakyo-laptop kernel: [21910.051326] ACPI: PCI interrupt for device 0000:00:02.0 disabled
Apr 19 13:00:53 kakyo-laptop kernel: [21910.070936] sd 0:0:0:0: [sda] Synchronizing SCSI cache
Apr 19 13:00:53 kakyo-laptop kernel: [21910.384865] sd 0:0:0:0: [sda] Stopping disk
Apr 19 13:00:53 kakyo-laptop kernel: [21911.359495] ACPI handle has no context!
Apr 19 13:00:53 kakyo-laptop kernel: [21911.359687] ACPI handle has no context!
Apr 19 13:00:53 kakyo-laptop kernel: [21911.359706] ACPI: PCI interrupt for device 0000:09:09.1 disabled
Apr 19 13:00:53 kakyo-laptop kernel: [21911.359713] ACPI handle has no context!
Apr 19 13:00:53 kakyo-laptop pulseaudio[6942]: module-alsa-sink.c: Got POLLERR from ALSA
Apr 19 13:00:53 kakyo-laptop kernel: [21913.507424] ACPI: PCI interrupt for device 0000:00:1f.1 disabled
Apr 19 13:00:53 kakyo-laptop kernel: [21913.507577] ACPI: PCI interrupt for device 0000:00:1d.7 disabled
Apr 19 13:00:53 kakyo-laptop kernel: [21913.527280] ACPI: PCI interrupt for device 0000:00:1d.2 disabled
Apr 19 13:00:53 kakyo-laptop kernel: [21913.527328] ACPI: PCI interrupt for device 0000:00:1d.1 disabled
Apr 19 13:00:53 kakyo-laptop kernel: [21913.527375] ACPI: PCI interrupt for device 0000:00:1d.0 disabled
Apr 19 13:00:53 kakyo-laptop kernel: [21913.527935] ACPI: PCI interrupt for device 0000:00:1b.0 disabled
Apr 19 13:00:53 kakyo-laptop kernel: [21913.528287] ACPI: PCI interrupt for device 0000:00:1a.7 disabled
Apr 19 13:00:53 kakyo-laptop kernel: [21913.528588] ACPI: PCI interrupt for device 0000:00:1a.1 disabled
Apr 19 13:00:53 kakyo-laptop kernel: [21913.528636] ACPI: PCI interrupt for device 0000:00:1a.0 disabled
Apr 19 13:00:53 kakyo-laptop kernel: [21913.532110] Disabling non-boot CPUs ...
Apr 19 13:00:53 kakyo-laptop kernel: [21913.532128] CPU0 attaching NULL sched-domain.
Apr 19 13:00:53 kakyo-laptop kernel: [21913.532129] CPU1 attaching NULL sched-domain.
Apr 19 13:00:53 kakyo-laptop kernel: [21913.668011] CPU 1 is now offline
Apr 19 13:00:53 kakyo-laptop kernel: [21913.668014] SMP alternatives: switching to UP code
Apr 19 13:00:53 kakyo-laptop kernel: [21913.669421] CPU0 attaching sched-domain:
Apr 19 13:00:53 kakyo-laptop kernel: [21913.669424]  domain 0: span 01
Apr 19 13:00:53 kakyo-laptop kernel: [21913.669425]   groups: 01
Apr 19 13:00:53 kakyo-laptop kernel: [21913.669605] CPU1 is down
Apr 19 13:00:53 kakyo-laptop kernel: [    0.806206] Back to C!
Apr 19 13:00:53 kakyo-laptop kernel: [    0.806623] Enabling non-boot CPUs ...
Apr 19 13:00:53 kakyo-laptop kernel: [    0.806697] CPU0 attaching NULL sched-domain.
Apr 19 13:00:53 kakyo-laptop kernel: [    0.834853] SMP alternatives: switching to SMP code
Apr 19 13:00:53 kakyo-laptop kernel: [    0.835985] Booting processor 1/1 eip 3000
Apr 19 13:00:53 kakyo-laptop kernel: [    0.846228] Initializing CPU#1
Apr 19 13:00:53 kakyo-laptop kernel: [    0.994715] Calibrating delay using timer specific routine.. 3990.59 BogoMIPS (lpj=19952973)
Apr 19 13:00:53 kakyo-laptop kernel: [    0.994721] CPU: After generic identify, caps: bfebfbff 20100000 00000000 00000000 0000e39d 00000000 00000001 00000000
Apr 19 13:00:53 kakyo-laptop kernel: [    0.994726] monitor/mwait feature present.
Apr 19 13:00:53 kakyo-laptop kernel: [    0.994728] CPU: L1 I cache: 32K, L1 D cache: 32K
Apr 19 13:00:53 kakyo-laptop kernel: [    0.994730] CPU: L2 cache: 2048K
Apr 19 13:00:53 kakyo-laptop kernel: [    0.994732] CPU: Physical Processor ID: 0
Apr 19 13:00:53 kakyo-laptop kernel: [    0.994733] CPU: Processor Core ID: 1
Apr 19 13:00:53 kakyo-laptop kernel: [    0.994734] CPU: After all inits, caps: bfebfbff 20100000 00000000 00043940 0000e39d 00000000 00000001 00000000
Apr 19 13:00:53 kakyo-laptop kernel: [    0.995199] CPU1: Intel(R) Core(TM)2 Duo CPU     T5750  @ 2.00GHz stepping 0d
Apr 19 13:00:53 kakyo-laptop kernel: [    0.995241] CPU0 attaching sched-domain:
Apr 19 13:00:53 kakyo-laptop kernel: [    0.995243]  domain 0: span 03
Apr 19 13:00:53 kakyo-laptop kernel: [    0.995244]   groups: 01 02
Apr 19 13:00:53 kakyo-laptop kernel: [    0.995247] CPU1 attaching sched-domain:
Apr 19 13:00:53 kakyo-laptop kernel: [    0.995248]  domain 0: span 03
Apr 19 13:00:53 kakyo-laptop kernel: [    0.995249]   groups: 02 01
Apr 19 13:00:53 kakyo-laptop kernel: [    0.995557] CPU1 is up
Apr 19 13:00:53 kakyo-laptop kernel: [    1.000482] Switched to high resolution mode on CPU 1
Apr 19 13:00:53 kakyo-laptop kernel: [    1.041393] PM: Writing back config space on device 0000:00:02.0 at offset f (was 100, writing 105)
Apr 19 13:00:53 kakyo-laptop kernel: [    1.041414] PM: Writing back config space on device 0000:00:02.0 at offset 1 (was 900007, writing 900003)
Apr 19 13:00:53 kakyo-laptop kernel: [    1.054190] ACPI: PCI Interrupt 0000:00:1a.0[A] -> GSI 16 (level, low) -> IRQ 17
Apr 19 13:00:53 kakyo-laptop kernel: [    1.054198] PCI: Setting latency timer of device 0000:00:1a.0 to 64
Apr 19 13:00:53 kakyo-laptop kernel: [    1.054254] usb usb1: root hub lost power or was reset
Apr 19 13:00:53 kakyo-laptop kernel: [    1.054276] ACPI: PCI Interrupt 0000:00:1a.1[B] -> GSI 21 (level, low) -> IRQ 18
Apr 19 13:00:53 kakyo-laptop kernel: [    1.054281] PCI: Setting latency timer of device 0000:00:1a.1 to 64
Apr 19 13:00:53 kakyo-laptop kernel: [    1.054335] usb usb2: root hub lost power or was reset
Apr 19 13:00:53 kakyo-laptop kernel: [    1.055104] ACPI: PCI Interrupt 0000:00:1a.7[C] -> GSI 18 (level, low) -> IRQ 19
Apr 19 13:00:53 kakyo-laptop kernel: [    1.055113] PCI: Setting latency timer of device 0000:00:1a.7 to 64
Apr 19 13:00:53 kakyo-laptop kernel: [    1.055435] PM: Writing back config space on device 0000:00:1b.0 at offset 3 (was 0, writing 10)
Apr 19 13:00:53 kakyo-laptop kernel: [    1.055446] PM: Writing back config space on device 0000:00:1b.0 at offset 1 (was 100106, writing 100102)
Apr 19 13:00:53 kakyo-laptop kernel: [    1.055478] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 22 (level, low) -> IRQ 23
Apr 19 13:00:53 kakyo-laptop kernel: [    1.055488] PCI: Setting latency timer of device 0000:00:1b.0 to 64
Apr 19 13:00:53 kakyo-laptop kernel: [    1.059558] PM: Writing back config space on device 0000:00:1c.0 at offset f (was 40100, writing 4010a)
Apr 19 13:00:53 kakyo-laptop kernel: [    1.059584] PM: Writing back config space on device 0000:00:1c.0 at offset 3 (was 810000, writing 810010)
Apr 19 13:00:53 kakyo-laptop kernel: [    1.059590] PM: Writing back config space on device 0000:00:1c.0 at offset 1 (was 100007, writing 100407)
Apr 19 13:00:53 kakyo-laptop kernel: [    1.059644] PCI: Setting latency timer of device 0000:00:1c.0 to 64
Apr 19 13:00:53 kakyo-laptop kernel: [    1.059656] PM: Writing back config space on device 0000:00:1c.1 at offset f (was 40200, writing 40205)
Apr 19 13:00:53 kakyo-laptop kernel: [    1.059673] PM: Writing back config space on device 0000:00:1c.1 at offset 9 (was 10001, writing f3f1f201)
Apr 19 13:00:53 kakyo-laptop kernel: [    1.059682] PM: Writing back config space on device 0000:00:1c.1 at offset 8 (was 0, writing f7f0f600)
Apr 19 13:00:53 kakyo-laptop kernel: [    1.059687] PM: Writing back config space on device 0000:00:1c.1 at offset 7 (was 20000000, writing b080)
Apr 19 13:00:53 kakyo-laptop kernel: [    1.059697] PM: Writing back config space on device 0000:00:1c.1 at offset 3 (was 810000, writing 810010)
Apr 19 13:00:53 kakyo-laptop kernel: [    1.059707] PM: Writing back config space on device 0000:00:1c.1 at offset 1 (was 100000, writing 100507)
Apr 19 13:00:53 kakyo-laptop kernel: [    1.059756] PCI: Setting latency timer of device 0000:00:1c.1 to 64
Apr 19 13:00:53 kakyo-laptop kernel: [    1.059771] PM: Writing back config space on device 0000:00:1c.5 at offset f (was 40200, writing 40205)
Apr 19 13:00:53 kakyo-laptop kernel: [    1.059787] PM: Writing back config space on device 0000:00:1c.5 at offset 9 (was 10001, writing c201c201)
Apr 19 13:00:53 kakyo-laptop kernel: [    1.059792] PM: Writing back config space on device 0000:00:1c.5 at offset 8 (was 0, writing f820f820)
Apr 19 13:00:53 kakyo-laptop kernel: [    1.059797] PM: Writing back config space on device 0000:00:1c.5 at offset 7 (was 20000000, writing c0c0)
Apr 19 13:00:53 kakyo-laptop kernel: [    1.059811] PM: Writing back config space on device 0000:00:1c.5 at offset 3 (was 810000, writing 810010)
Apr 19 13:00:53 kakyo-laptop kernel: [    1.059817] PM: Writing back config space on device 0000:00:1c.5 at offset 1 (was 100000, writing 100507)
Apr 19 13:00:53 kakyo-laptop kernel: [    1.059870] PCI: Setting latency timer of device 0000:00:1c.5 to 64
Apr 19 13:00:53 kakyo-laptop kernel: [    1.059878] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 23 (level, low) -> IRQ 20
Apr 19 13:00:53 kakyo-laptop kernel: [    1.059884] PCI: Setting latency timer of device 0000:00:1d.0 to 64
Apr 19 13:00:53 kakyo-laptop kernel: [    1.059942] usb usb5: root hub lost power or was reset
Apr 19 13:00:53 kakyo-laptop kernel: [    1.059961] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 19 (level, low) -> IRQ 22
Apr 19 13:00:53 kakyo-laptop kernel: [    1.059967] PCI: Setting latency timer of device 0000:00:1d.1 to 64
Apr 19 13:00:53 kakyo-laptop kernel: [    1.060021] usb usb6: root hub lost power or was reset
Apr 19 13:00:53 kakyo-laptop kernel: [    1.060041] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 19
Apr 19 13:00:53 kakyo-laptop kernel: [    1.060046] PCI: Setting latency timer of device 0000:00:1d.2 to 64
Apr 19 13:00:53 kakyo-laptop kernel: [    1.060099] usb usb7: root hub lost power or was reset
Apr 19 13:00:53 kakyo-laptop kernel: [    1.060228] ACPI: PCI Interrupt 0000:00:1d.7[A] -> GSI 23 (level, low) -> IRQ 20
Apr 19 13:00:53 kakyo-laptop kernel: [    1.060236] PCI: Setting latency timer of device 0000:00:1d.7 to 64
Apr 19 13:00:53 kakyo-laptop kernel: [    1.060323] PM: Writing back config space on device 0000:00:1e.0 at offset 9 (was 10001, writing 1fff1)
Apr 19 13:00:53 kakyo-laptop kernel: [    1.060331] PM: Writing back config space on device 0000:00:1e.0 at offset 8 (was 0, writing f830f830)
Apr 19 13:00:53 kakyo-laptop kernel: [    1.060338] PM: Writing back config space on device 0000:00:1e.0 at offset 7 (was 62800000, writing 628000f0)
Apr 19 13:00:53 kakyo-laptop kernel: [    1.060356] PM: Writing back config space on device 0000:00:1e.0 at offset 1 (was 100004, writing 100107)
Apr 19 13:00:53 kakyo-laptop kernel: [    1.060386] PCI: Setting latency timer of device 0000:00:1e.0 to 64
Apr 19 13:00:53 kakyo-laptop kernel: [    1.060463] PM: Writing back config space on device 0000:00:1f.1 at offset f (was 100, writing 1ff)
Apr 19 13:00:53 kakyo-laptop kernel: [    1.060487] PM: Writing back config space on device 0000:00:1f.1 at offset 1 (was 2800005, writing 2880005)
Apr 19 13:00:53 kakyo-laptop kernel: [    1.060498] ACPI: PCI Interrupt 0000:00:1f.1[A] -> GSI 19 (level, low) -> IRQ 22
Apr 19 13:00:53 kakyo-laptop kernel: [    1.060503] PCI: Setting latency timer of device 0000:00:1f.1 to 64
Apr 19 13:00:53 kakyo-laptop kernel: [    1.061581] PM: Writing back config space on device 0000:00:1f.2 at offset f (was 200, writing 20a)
Apr 19 13:00:53 kakyo-laptop kernel: [    1.061615] PM: Writing back config space on device 0000:00:1f.2 at offset 1 (was 2b00007, writing 2b00407)
Apr 19 13:00:53 kakyo-laptop kernel: [    1.061677] PCI: Setting latency timer of device 0000:00:1f.2 to 64
Apr 19 13:00:53 kakyo-laptop kernel: [    1.061871] /dev/vmmon[0]: HostIF_ReadUptime: detected settimeofday: fixed uptimeBase old 18445503977606792171 new 18445503970604794480 attempts 1
Apr 19 13:00:53 kakyo-laptop kernel: [    1.075256] ata4.00: ACPI cmd ef/03:0c:00:00:00:a0 filtered out
Apr 19 13:00:53 kakyo-laptop kernel: [    1.075258] ata4.00: ACPI cmd ef/03:22:00:00:00:a0 filtered out
Apr 19 13:00:53 kakyo-laptop kernel: [    1.077102] ata4.00: configured for MWDMA2
Apr 19 13:00:53 kakyo-laptop kernel: [    1.077253] PM: Writing back config space on device 0000:00:1f.3 at offset 4 (was 0, writing c2100000)
Apr 19 13:00:53 kakyo-laptop kernel: [    1.077272] Coming out of suspend...
Apr 19 13:00:53 kakyo-laptop kernel: [    1.077803] PCI: Enabling device 0000:02:00.0 (0000 -> 0002)
Apr 19 13:00:53 kakyo-laptop kernel: [    1.077837] PM: Writing back config space on device 0000:02:00.0 at offset f (was 100, writing 105)
Apr 19 13:00:53 kakyo-laptop kernel: [    1.077881] PM: Writing back config space on device 0000:02:00.0 at offset 4 (was 4, writing f4000004)
Apr 19 13:00:53 kakyo-laptop kernel: [    1.077891] PM: Writing back config space on device 0000:02:00.0 at offset 3 (was 0, writing 10)
Apr 19 13:00:53 kakyo-laptop kernel: [    1.077905] PM: Writing back config space on device 0000:02:00.0 at offset 1 (was 100002, writing 100506)
Apr 19 13:00:53 kakyo-laptop kernel: [    1.135705] PM: Writing back config space on device 0000:08:00.0 at offset f (was 100, writing 10a)
Apr 19 13:00:53 kakyo-laptop kernel: [    1.135733] PM: Writing back config space on device 0000:08:00.0 at offset 6 (was 4, writing f8200004)
Apr 19 13:00:53 kakyo-laptop kernel: [    1.135743] PM: Writing back config space on device 0000:08:00.0 at offset 4 (was 1, writing c001)
Apr 19 13:00:53 kakyo-laptop kernel: [    1.135749] PM: Writing back config space on device 0000:08:00.0 at offset 3 (was 0, writing 10)
Apr 19 13:00:53 kakyo-laptop kernel: [    1.135758] PM: Writing back config space on device 0000:08:00.0 at offset 1 (was 100000, writing 100103)
Apr 19 13:00:53 kakyo-laptop kernel: [    1.173469] iwl4965: Radio disabled by HW RF Kill switch
Apr 19 13:00:53 kakyo-laptop kernel: [    1.199370] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[21]  MMIO=[f8300000-f83007ff]  Max Packet=[2048]  IR/IT contexts=[4/4]
Apr 19 13:00:53 kakyo-laptop kernel: [    1.217379] ACPI: PCI Interrupt 0000:09:09.1[B] -> GSI 21 (level, low) -> IRQ 18
Apr 19 13:00:53 kakyo-laptop kernel: [    1.217434] PM: Writing back config space on device 0000:09:09.2 at offset 4 (was f8300c00, writing f8301000)
Apr 19 13:00:53 kakyo-laptop kernel: [    1.217492] PM: Writing back config space on device 0000:09:09.3 at offset 4 (was f8301000, writing f8301400)
Apr 19 13:00:53 kakyo-laptop kernel: [    1.217531] PM: Writing back config space on device 0000:09:09.4 at offset f (was 200, writing 2ff)
Apr 19 13:00:53 kakyo-laptop kernel: [    1.217555] PM: Writing back config space on device 0000:09:09.4 at offset 4 (was 0, writing ffffff00)
Apr 19 13:00:53 kakyo-laptop kernel: [    1.217560] PM: Writing back config space on device 0000:09:09.4 at offset 3 (was 800000, writing 80f8ff)
Apr 19 13:00:53 kakyo-laptop kernel: [    1.217566] PM: Writing back config space on device 0000:09:09.4 at offset 1 (was 2100000, writing 2100546)
Apr 19 13:00:53 kakyo-laptop kernel: [    1.387262] ata3: SATA link down (SStatus 0 SControl 300)
Apr 19 13:00:53 kakyo-laptop kernel: [    1.389757] ata2: SATA link down (SStatus 0 SControl 300)
Apr 19 13:00:53 kakyo-laptop kernel: [    1.809625] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
Apr 19 13:00:53 kakyo-laptop kernel: [    1.839058] ata1.00: ACPI cmd ef/10:03:00:00:00:a0 succeeded
Apr 19 13:00:53 kakyo-laptop kernel: [    1.840536] ata1.00: configured for UDMA/100
Apr 19 13:00:53 kakyo-laptop kernel: [    1.859696] sd 0:0:0:0: [sda] 488397168 512-byte hardware sectors (250059 MB)
Apr 19 13:00:53 kakyo-laptop kernel: [    1.859748] sd 0:0:0:0: [sda] Write Protect is off
Apr 19 13:00:53 kakyo-laptop kernel: [    1.859752] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Apr 19 13:00:53 kakyo-laptop kernel: [    1.859840] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Apr 19 13:00:53 kakyo-laptop kernel: [    2.640437] sd 0:0:0:0: [sda] Starting disk
Apr 19 13:00:53 kakyo-laptop kernel: [    3.176724] ACPI: PCI Interrupt 0000:00:02.0[A] -> GSI 16 (level, low) -> IRQ 17
Apr 19 13:00:53 kakyo-laptop kernel: [    3.178052] PM: Finishing wakeup.
Apr 19 13:00:53 kakyo-laptop kernel: [    3.178054] Restarting tasks ... <6>usb 2-2: USB disconnect, address 4
Apr 19 13:00:53 kakyo-laptop kernel: [    3.178331] done.
Apr 19 13:00:53 kakyo-laptop gnome-power-manager: (kakyo) Resuming computer
Apr 19 13:00:53 kakyo-laptop pulseaudio[6942]: module-alsa-sink.c: Got POLLERR from ALSA
Apr 19 13:00:53 kakyo-laptop pulseaudio[6942]: module-alsa-sink.c: Got POLLERR from ALSA
Apr 19 13:00:53 kakyo-laptop anacron[27215]: Anacron 2.3 started on 2009-04-19
Apr 19 13:00:53 kakyo-laptop anacron[27215]: Normal exit (0 jobs run)
Apr 19 13:00:53 kakyo-laptop NetworkManager: <debug> [1240160453.944636] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_ffffffff_ffffffff_noserial_logicaldev_input'). 
Apr 19 13:00:53 kakyo-laptop pulseaudio[6942]: module-alsa-sink.c: Got POLLERR from ALSA
Apr 19 13:00:53 kakyo-laptop NetworkManager: <debug> [1240160453.968102] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_ffffffff_ffffffff_noserial'). 
Apr 19 13:00:53 kakyo-laptop NetworkManager: <debug> [1240160453.969609] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_ffffffff_ffffffff_noserial_0_logicaldev_input'). 
Apr 19 13:00:54 kakyo-laptop pulseaudio[6942]: module-alsa-sink.c: Got POLLERR from ALSA
Apr 19 13:00:54 kakyo-laptop NetworkManager: <debug> [1240160454.021493] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_ffffffff_ffffffff_noserial_0'). 
Apr 19 13:00:54 kakyo-laptop NetworkManager: <debug> [1240160454.026303] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_46d_c518_noserial'). 
Apr 19 13:00:54 kakyo-laptop kernel: [    3.493087] r8169 Gigabit Ethernet driver 2.2LK loaded
Apr 19 13:00:54 kakyo-laptop kernel: [    3.493129] ACPI: PCI Interrupt 0000:08:00.0[A] -> GSI 17 (level, low) -> IRQ 16
Apr 19 13:00:54 kakyo-laptop kernel: [    3.493153] PCI: Setting latency timer of device 0000:08:00.0 to 64
Apr 19 13:00:54 kakyo-laptop vmnetBridge: RTM_NEWLINK: name:eth0 index:7 flags:0x00001002 
Apr 19 13:00:54 kakyo-laptop vmnetBridge: Can't remove interface eth0 7 (does not exist). 
Apr 19 13:00:54 kakyo-laptop kernel: [    3.493797] eth0: RTL8101e at 0xf8c9c000, 00:1e:68:99:1b:73, XID 34200000 IRQ 220
Apr 19 13:00:54 kakyo-laptop pulseaudio[6942]: module-alsa-sink.c: Got POLLERR from ALSA
Apr 19 13:00:54 kakyo-laptop NetworkManager: <debug> [1240160454.097479] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/net_00_1e_68_99_1b_73'). 
Apr 19 13:00:54 kakyo-laptop vmnetBridge: RTM_NEWLINK: name:eth0 index:7 flags:0x00001043 
Apr 19 13:00:54 kakyo-laptop kernel: [    3.563423] r8169: eth0: link down
Apr 19 13:00:54 kakyo-laptop kernel: [    3.565284] ADDRCONF(NETDEV_UP): eth0: link is not ready
Apr 19 13:00:54 kakyo-laptop kernel: [    3.565636] /dev/vmnet: open called by PID 6238 (vmnet-bridge)
Apr 19 13:00:54 kakyo-laptop kernel: [    3.565645] /dev/vmnet: hub 0 does not exist, allocating memory.
Apr 19 13:00:54 kakyo-laptop kernel: [    3.565654] /dev/vmnet: port on hub 0 successfully opened
Apr 19 13:00:54 kakyo-laptop kernel: [    3.565661] bridge-eth0: up
Apr 19 13:00:54 kakyo-laptop pulseaudio[6942]: module-alsa-sink.c: Got POLLERR from ALSA
Apr 19 13:00:54 kakyo-laptop vmnetBridge: Started bridge eth0 to virtual network 0. 
Apr 19 13:00:54 kakyo-laptop vmnetBridge: RTM_NEWLINK: name:eth0 index:7 flags:0x00001003 
Apr 19 13:00:54 kakyo-laptop NetworkManager: <info>  eth0: Device is fully-supported using driver 'r8169'. 
Apr 19 13:00:54 kakyo-laptop kernel: [    3.608597] bridge-eth0: attached
Apr 19 13:00:54 kakyo-laptop kernel: [    3.608677] bridge-eth0: disabling the bridge
Apr 19 13:00:54 kakyo-laptop NetworkManager: <info>  nm_device_init(): waiting for device's worker thread to start 
Apr 19 13:00:54 kakyo-laptop NetworkManager: <info>  nm_device_init(): device's worker thread started, continuing. 
Apr 19 13:00:54 kakyo-laptop NetworkManager: <info>  Now managing wired Ethernet (802.3) device 'eth0'. 
Apr 19 13:00:54 kakyo-laptop NetworkManager: <info>  Deactivating device eth0. 
Apr 19 13:00:54 kakyo-laptop pulseaudio[6942]: module-alsa-sink.c: Got POLLERR from ALSA
Apr 19 13:00:54 kakyo-laptop NetworkManager: <info>  Will activate wired connection 'eth0' because it now has a link. 
Apr 19 13:00:54 kakyo-laptop vmnetBridge: Stopped bridge eth0 to virtual network 0. 
Apr 19 13:00:54 kakyo-laptop kernel: [    3.686691] bridge-eth0: down
Apr 19 13:00:54 kakyo-laptop kernel: [    3.686724] bridge-eth0: detached
Apr 19 13:00:54 kakyo-laptop pulseaudio[6942]: module-alsa-sink.c: Got POLLERR from ALSA
Apr 19 13:00:54 kakyo-laptop NetworkManager: <info>  Waking up from sleep. 
Apr 19 13:00:54 kakyo-laptop NetworkManager: <info>  Deactivating device eth0. 
Apr 19 13:00:54 kakyo-laptop pulseaudio[6942]: module-alsa-sink.c: Got POLLERR from ALSA
Apr 19 13:00:54 kakyo-laptop pulseaudio[6942]: module-alsa-sink.c: Got POLLERR from ALSA
Apr 19 13:00:54 kakyo-laptop vmnetBridge: RTM_NEWLINK: name:eth0 index:7 flags:0x00001002 
Apr 19 13:00:54 kakyo-laptop vmnetBridge: Can't remove interface eth0 7 (does not exist). 
Apr 19 13:00:54 kakyo-laptop kernel: [    3.860489] r8169: eth0: link down
Apr 19 13:00:54 kakyo-laptop vmnetBridge: RTM_NEWLINK: name:eth0 index:7 flags:0x00001003 
Apr 19 13:00:54 kakyo-laptop vmnetBridge: Can't remove interface eth0 7 (does not exist). 
Apr 19 13:00:54 kakyo-laptop kernel: [    3.862275] ADDRCONF(NETDEV_UP): eth0: link is not ready
Apr 19 13:00:54 kakyo-laptop NetworkManager: <info>  eth0: Device is fully-supported using driver 'r8169'. 
Apr 19 13:00:54 kakyo-laptop NetworkManager: <info>  nm_device_init(): waiting for device's worker thread to start 
Apr 19 13:00:54 kakyo-laptop NetworkManager: <info>  nm_device_init(): device's worker thread started, continuing. 
Apr 19 13:00:54 kakyo-laptop NetworkManager: <info>  Now managing wired Ethernet (802.3) device 'eth0'. 
Apr 19 13:00:54 kakyo-laptop NetworkManager: <info>  Deactivating device eth0. 
Apr 19 13:00:54 kakyo-laptop pulseaudio[6942]: module-alsa-sink.c: Got POLLERR from ALSA
Apr 19 13:00:54 kakyo-laptop last message repeated 2 times
Apr 19 13:00:57 kakyo-laptop kernel: [    6.322311] usb 2-2: new low speed USB device using uhci_hcd and address 5
Apr 19 13:00:57 kakyo-laptop kernel: [    6.461386] usb 2-2: configuration #1 chosen from 1 choice
Apr 19 13:00:57 kakyo-laptop NetworkManager: <debug> [1240160457.673970] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_46d_c518_noserial'). 
Apr 19 13:00:57 kakyo-laptop kernel: [    6.492603] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:1a.1/usb2/2-2/2-2:1.0/input/input15
Apr 19 13:00:57 kakyo-laptop NetworkManager: <debug> [1240160457.793380] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_ffffffff_ffffffff_noserial'). 
Apr 19 13:00:57 kakyo-laptop kernel: [    6.624323] input,hidraw0: USB HID v1.11 Mouse [Logitech USB Receiver] on usb-0000:00:1a.1-2
Apr 19 13:00:57 kakyo-laptop kernel: [    6.653225] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:1a.1/usb2/2-2/2-2:1.1/input/input16
Apr 19 13:00:57 kakyo-laptop NetworkManager: <debug> [1240160457.886129] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_ffffffff_ffffffff_noserial_0'). 
Apr 19 13:00:57 kakyo-laptop NetworkManager: <debug> [1240160457.910987] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_ffffffff_ffffffff_noserial_logicaldev_input'). 
Apr 19 13:00:57 kakyo-laptop anacron[27547]: Anacron 2.3 started on 2009-04-19
Apr 19 13:00:57 kakyo-laptop anacron[27547]: Normal exit (0 jobs run)
Apr 19 13:00:57 kakyo-laptop kernel: [    6.774488] input,hiddev96,hidraw1: USB HID v1.11 Device [Logitech USB Receiver] on usb-0000:00:1a.1-2
Apr 19 13:00:58 kakyo-laptop NetworkManager: <debug> [1240160458.068375] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_ffffffff_ffffffff_noserial_0_logicaldev_input'). 
Apr 19 13:13:23 kakyo-laptop kernel: [  493.603433] CPU0 attaching NULL sched-domain.
Apr 19 13:13:23 kakyo-laptop kernel: [  493.603439] CPU1 attaching NULL sched-domain.
Apr 19 13:13:23 kakyo-laptop kernel: [  493.646531] CPU0 attaching sched-domain:
Apr 19 13:13:23 kakyo-laptop kernel: [  493.646537]  domain 0: span 03
Apr 19 13:13:23 kakyo-laptop kernel: [  493.646538]   groups: 01 02
Apr 19 13:13:23 kakyo-laptop kernel: [  493.646541]   domain 1: span 03
Apr 19 13:13:23 kakyo-laptop kernel: [  493.646543]    groups: 03
Apr 19 13:13:23 kakyo-laptop kernel: [  493.646545] CPU1 attaching sched-domain:
Apr 19 13:13:23 kakyo-laptop kernel: [  493.646546]  domain 0: span 03
Apr 19 13:13:23 kakyo-laptop kernel: [  493.646548]   groups: 02 01
Apr 19 13:13:23 kakyo-laptop kernel: [  493.646550]   domain 1: span 03
Apr 19 13:13:23 kakyo-laptop kernel: [  493.646551]    groups: 03
Apr 19 13:17:01 kakyo-laptop /USR/SBIN/CRON[28480]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Apr 19 13:33:29 kakyo-laptop gnome-power-manager: (kakyo) Suspending computer. Reason: The suspend button has been pressed.
Apr 19 13:33:37 kakyo-laptop NetworkManager: <info>  Going to sleep. 
Apr 19 13:33:37 kakyo-laptop vmnetBridge: RTM_NEWLINK: name:eth0 index:7 flags:0x00001002 
Apr 19 13:33:37 kakyo-laptop vmnetBridge: Can't remove interface eth0 7 (does not exist). 
Apr 19 13:33:37 kakyo-laptop vmnetBridge: RTM_DELLINK: name:eth0 index:7 flags:0x00001002 
Apr 19 13:33:37 kakyo-laptop vmnetBridge: Can't remove interface eth0 7 (does not exist). 
Apr 19 13:33:37 kakyo-laptop NetworkManager: <debug> [1240162417.373681] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/net_00_1e_68_99_1b_73'). 
Apr 19 13:33:37 kakyo-laptop NetworkManager: <info>  Deactivating device eth0. 
Apr 19 13:33:37 kakyo-laptop kernel: [ 1237.105757] ACPI: PCI interrupt for device 0000:08:00.0 disabled
Apr 19 15:16:49 kakyo-laptop syslogd 1.5.0#1ubuntu1: restart.
Apr 19 15:16:49 kakyo-laptop kernel: Inspecting /boot/System.map-2.6.24-23-server
Apr 19 15:16:50 kakyo-laptop kernel: Loaded 28765 symbols from /boot/System.map-2.6.24-23-server.
Apr 19 15:16:50 kakyo-laptop kernel: Symbols match kernel version 2.6.24.
Apr 19 15:16:50 kakyo-laptop kernel: Loaded 19362 symbols from 95 modules.
Apr 19 15:16:50 kakyo-laptop kernel: [    0.000000] Initializing cgroup subsys cpuset
Apr 19 15:16:50 kakyo-laptop kernel: [    0.000000] Initializing cgroup subsys cpu
Apr 19 15:16:50 kakyo-laptop kernel: [    0.000000] Linux version 2.6.24-23-server (buildd@palmer) (gcc version 4.2.4 (Ubuntu 4.2.4-1ubuntu3)) #1 SMP Wed Apr 1 22:22:14 UTC 2009 (Ubuntu 2.6.24-23.52-server)
Apr 19 15:16:50 kakyo-laptop kernel: [    0.000000] BIOS-provided physical RAM map:
Apr 19 15:16:50 kakyo-laptop kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
Apr 19 15:16:50 kakyo-laptop kernel: [    0.000000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
Apr 19 15:16:50 kakyo-laptop kernel: [    0.000000]  BIOS-e820: 00000000000dc000 - 0000000000100000 (reserved)
Apr 19 15:16:50 kakyo-laptop kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 00000000bf6d0000 (usable)
Apr 19 15:16:50 kakyo-laptop kernel: [    0.000000]  BIOS-e820: 00000000bf6d0000 - 00000000bf6e3000 (ACPI NVS)
Apr 19 15:16:50 kakyo-laptop kernel: [    0.000000]  BIOS-e820: 00000000bf6e3000 - 00000000c0000000 (reserved)
Apr 19 15:16:50 kakyo-laptop kernel: [    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
Apr 19 15:16:50 kakyo-laptop kernel: [    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
Apr 19 15:16:50 kakyo-laptop kernel: [    0.000000]  BIOS-e820: 00000000fed00000 - 00000000fed00400 (reserved)
Apr 19 15:16:50 kakyo-laptop kernel: [    0.000000]  BIOS-e820: 00000000fed14000 - 00000000fed1a000 (reserved)
Apr 19 15:16:50 kakyo-laptop kernel: [    0.000000]  BIOS-e820: 00000000fed1c000 - 00000000fed90000 (reserved)
Apr 19 15:16:50 kakyo-laptop kernel: [    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
Apr 19 15:16:50 kakyo-laptop kernel: [    0.000000]  BIOS-e820: 00000000ff000000 - 0000000100000000 (reserved)
Apr 19 15:16:50 kakyo-laptop kernel: [    0.000000]  BIOS-e820: 0000000100000000 - 0000000140000000 (usable)
Apr 19 15:16:50 kakyo-laptop kernel: [    0.000000] 4224MB HIGHMEM available.
Apr 19 15:16:50 kakyo-laptop kernel: [    0.000000] 896MB LOWMEM available.
Apr 19 15:16:50 kakyo-laptop kernel: [    0.000000] found SMP MP-table at 000f8520
Apr 19 15:16:50 kakyo-laptop kernel: [    0.000000] NX (Execute Disable) protection: active
Apr 19 15:16:50 kakyo-laptop kernel: [    0.000000] Entering add_active_range(0, 0, 1310720) 0 entries of 256 used
Apr 19 15:16:50 kakyo-laptop kernel: [    0.000000] Zone PFN ranges:
Apr 19 15:16:50 kakyo-laptop kernel: [    0.000000]   DMA             0 ->     4096
Apr 19 15:16:50 kakyo-laptop kernel: [    0.000000]   Normal       4096 ->   229376
Apr 19 15:16:50 kakyo-laptop kernel: [    0.000000]   HighMem    229376 ->  1310720
Apr 19 15:16:50 kakyo-laptop kernel: [    0.000000] Movable zone start PFN for each node
Apr 19 15:16:50 kakyo-laptop kernel: [    0.000000] early_node_map[1] active PFN ranges
Apr 19 15:16:50 kakyo-laptop kernel: [    0.000000]     0:        0 ->  1310720
Apr 19 15:16:50 kakyo-laptop kernel: [    0.000000] On node 0 totalpages: 1310720
Apr 19 15:16:50 kakyo-laptop kernel: [    0.000000]   DMA zone: 32 pages used for memmap
Apr 19 15:16:50 kakyo-laptop kernel: [    0.000000]   DMA zone: 0 pages reserved
Apr 19 15:16:50 kakyo-laptop kernel: [    0.000000]   DMA zone: 4064 pages, LIFO batch:0
Apr 19 15:16:50 kakyo-laptop kernel: [    0.000000]   Normal zone: 1760 pages used for memmap
Apr 19 15:16:50 kakyo-laptop kernel: [    0.000000]   Normal zone: 223520 pages, LIFO batch:31
Apr 19 15:16:50 kakyo-laptop kernel: [    0.000000]   HighMem zone: 8448 pages used for memmap
Apr 19 15:16:50 kakyo-laptop kernel: [    0.000000]   HighMem zone: 1072896 pages, LIFO batch:31
Apr 19 15:16:50 kakyo-laptop kernel: [    0.000000]   Movable zone: 0 pages used for memmap
Apr 19 15:16:50 kakyo-laptop kernel: [    0.000000] DMI present.
Apr 19 15:16:50 kakyo-laptop kernel: [    0.000000] ACPI: RSDP signature @ 0xC00F8480 checksum 0
Apr 19 15:16:50 kakyo-laptop kernel: [    0.000000] ACPI: RSDP 000F8480, 0024 (r2 HP    )
Apr 19 15:16:50 kakyo-laptop kernel: [    0.000000] ACPI: XSDT BF6D5AEB, 0084 (r1 HPQOEM SLIC-MPC  6040000  LTP        0)
Apr 19 15:16:50 kakyo-laptop kernel: [    0.000000] ACPI: FACP BF6DFC6C, 00F4 (r3 HP     30CC      6040000 ALAN        1)
Apr 19 15:16:50 kakyo-laptop kernel: [    0.000000] ACPI: DSDT BF6D703C, 8BBC (r1 HP     30CC      6040000 INTL 20061109)
Apr 19 15:16:50 kakyo-laptop kernel: [    0.000000] ACPI: FACS BF6E2FC0, 0040
Apr 19 15:16:50 kakyo-laptop kernel: [    0.000000] ACPI: HPET BF6DFD60, 0038 (r1 HP     30CC      6040000 LOHR       5A)
Apr 19 15:16:50 kakyo-laptop kernel: [    0.000000] ACPI: MCFG BF6DFD98, 003C (r1 HP     30CC      6040000 LOHR       5A)
Apr 19 15:16:50 kakyo-laptop kernel: [    0.000000] ACPI: TMOR BF6DFDD4, 0026 (r1 HP     30CC      6040000 PTL         3)
Apr 19 15:16:50 kakyo-laptop kernel: [    0.000000] ACPI: APIC BF6DFDFA, 0068 (r1 HP     30CC      6040000  LTP        0)
Apr 19 15:16:50 kakyo-laptop kernel: [    0.000000] ACPI: BOOT BF6DFE62, 0028 (r1 HP     30CC      6040000  LTP        1)
Apr 19 15:16:50 kakyo-laptop kernel: [    0.000000] ACPI: SLIC BF6DFE8A, 0176 (r1 HPQOEM SLIC-MPC  6040000  LTP        1)
Apr 19 15:16:50 kakyo-laptop kernel: [    0.000000] ACPI: SSDT BF6D6D5F, 02DD (r1 HP     30CC         1000 INTL 20061109)
Apr 19 15:16:50 kakyo-laptop kernel: [    0.000000] ACPI: SSDT BF6D6CB7, 00A8 (r1 HP     30CC         1000 INTL 20061109)
Apr 19 15:16:50 kakyo-laptop kernel: [    0.000000] ACPI: SSDT BF6D60FB, 025F (r1  HP    30CC         3000 INTL 20061109)
Apr 19 15:16:50 kakyo-laptop kernel: [    0.000000] ACPI: SSDT BF6D6055, 00A6 (r1  HP    30CC         3000 INTL 20061109)
Apr 19 15:16:50 kakyo-laptop kernel: [    0.000000] ACPI: SSDT BF6D5B6F, 04E6 (r1  HP     30CC        3000 INTL 20061109)
Apr 19 15:16:50 kakyo-laptop kernel: [    0.000000] ACPI: DMI detected: Hewlett-Packard
Apr 19 15:16:50 kakyo-laptop kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x1008
Apr 19 15:16:50 kakyo-laptop kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Apr 19 15:16:50 kakyo-laptop kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
Apr 19 15:16:50 kakyo-laptop kernel: [    0.000000] Processor #0 6:15 APIC version 20
Apr 19 15:16:50 kakyo-laptop kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
Apr 19 15:16:50 kakyo-laptop kernel: [    0.000000] Processor #1 6:15 APIC version 20
Apr 19 15:16:50 kakyo-laptop kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
Apr 19 15:16:50 kakyo-laptop kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
Apr 19 15:16:50 kakyo-laptop kernel: [    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
Apr 19 15:16:50 kakyo-laptop kernel: [    0.000000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
Apr 19 15:16:50 kakyo-laptop kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 high edge)
Apr 19 15:16:50 kakyo-laptop kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
Apr 19 15:16:50 kakyo-laptop kernel: [    0.000000] ACPI: IRQ0 used by override.
Apr 19 15:16:50 kakyo-laptop kernel: [    0.000000] ACPI: IRQ2 used by override.
Apr 19 15:16:50 kakyo-laptop kernel: [    0.000000] ACPI: IRQ9 used by override.
Apr 19 15:16:50 kakyo-laptop kernel: [    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
Apr 19 15:16:50 kakyo-laptop kernel: [    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
Apr 19 15:16:50 kakyo-laptop kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
Apr 19 15:16:50 kakyo-laptop kernel: [    0.000000] Allocating PCI resources starting at c2000000 (gap: c0000000:20000000)
Apr 19 15:16:50 kakyo-laptop kernel: [    0.000000] swsusp: Registered nosave memory region: 000000000009f000 - 00000000000a0000
Apr 19 15:16:50 kakyo-laptop kernel: [    0.000000] swsusp: Registered nosave memory region: 00000000000a0000 - 00000000000dc000
Apr 19 15:16:50 kakyo-laptop kernel: [    0.000000] swsusp: Registered nosave memory region: 00000000000dc000 - 0000000000100000
Apr 19 15:16:50 kakyo-laptop kernel: [    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 1300480
Apr 19 15:16:50 kakyo-laptop kernel: [    0.000000] Kernel command line: root=UUID=96bbbef5-3316-44cc-b0a2-7f489b657f17 ro quiet splash
Apr 19 15:16:50 kakyo-laptop kernel: [    0.000000] mapped APIC to ffffb000 (fee00000)
Apr 19 15:16:50 kakyo-laptop kernel: [    0.000000] mapped IOAPIC to ffffa000 (fec00000)
Apr 19 15:16:50 kakyo-laptop kernel: [    0.000000] Enabling fast FPU save and restore... done.
Apr 19 15:16:50 kakyo-laptop kernel: [    0.000000] Enabling unmasked SIMD FPU exception support... done.
Apr 19 15:16:50 kakyo-laptop kernel: [    0.000000] Initializing CPU#0
Apr 19 15:16:50 kakyo-laptop kernel: [    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
Apr 19 15:16:50 kakyo-laptop kernel: [    0.000000] Detected 1995.343 MHz processor.
Apr 19 15:16:50 kakyo-laptop kernel: [   15.039414] Console: colour VGA+ 80x25
Apr 19 15:16:50 kakyo-laptop kernel: [   15.039416] console [tty0] enabled
Apr 19 15:16:50 kakyo-laptop kernel: [   15.039704] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
Apr 19 15:16:50 kakyo-laptop kernel: [   15.039982] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
Apr 19 15:16:50 kakyo-laptop kernel: [   15.288577] Memory: 4129608k/5242880k available (2258k kernel code, 53908k reserved, 1037k data, 384k init, 3267392k highmem)
Apr 19 15:16:50 kakyo-laptop kernel: [   15.288584] virtual kernel memory layout:
Apr 19 15:16:50 kakyo-laptop kernel: [   15.288585]     fixmap  : 0xfff4c000 - 0xfffff000   ( 716 kB)
Apr 19 15:16:50 kakyo-laptop kernel: [   15.288586]     pkmap   : 0xffc00000 - 0xffe00000   (2048 kB)
Apr 19 15:16:50 kakyo-laptop kernel: [   15.288587]     vmalloc : 0xf8800000 - 0xffbfe000   ( 115 MB)
Apr 19 15:16:50 kakyo-laptop kernel: [   15.288588]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
Apr 19 15:16:50 kakyo-laptop kernel: [   15.288589]       .init : 0xc043e000 - 0xc049e000   ( 384 kB)
Apr 19 15:16:50 kakyo-laptop kernel: [   15.288590]       .data : 0xc0334a39 - 0xc0437fe4   (1037 kB)
Apr 19 15:16:50 kakyo-laptop kernel: [   15.288591]       .text : 0xc0100000 - 0xc0334a39   (2258 kB)
Apr 19 15:16:50 kakyo-laptop kernel: [   15.288593] Checking if this processor honours the WP bit even in supervisor mode... Ok.
Apr 19 15:16:50 kakyo-laptop kernel: [   15.288633] SLUB: Genslabs=11, HWalign=64, Order=0-1, MinObjects=4, CPUs=2, Nodes=1
Apr 19 15:16:50 kakyo-laptop kernel: [   15.288766] hpet clockevent registered
Apr 19 15:16:50 kakyo-laptop kernel: [   15.438706] Calibrating delay using timer specific routine.. 3993.79 BogoMIPS (lpj=19968993)
Apr 19 15:16:50 kakyo-laptop kernel: [   15.438727] Security Framework initialized
Apr 19 15:16:50 kakyo-laptop kernel: [   15.438732] SELinux:  Disabled at boot.
Apr 19 15:16:50 kakyo-laptop kernel: [   15.438745] AppArmor: AppArmor initialized
Apr 19 15:16:50 kakyo-laptop kernel: [   15.438749] Failure registering capabilities with primary security module.
Apr 19 15:16:50 kakyo-laptop kernel: [   15.438757] Mount-cache hash table entries: 512
Apr 19 15:16:50 kakyo-laptop kernel: [   15.438869] Initializing cgroup subsys ns
Apr 19 15:16:50 kakyo-laptop kernel: [   15.438874] Initializing cgroup subsys cpuacct
Apr 19 15:16:50 kakyo-laptop kernel: [   15.438883] CPU: After generic identify, caps: bfebfbff 20100000 00000000 00000000 0000e39d 00000000 00000001 00000000
Apr 19 15:16:50 kakyo-laptop kernel: [   15.438890] monitor/mwait feature present.
Apr 19 15:16:50 kakyo-laptop kernel: [   15.438891] using mwait in idle threads.
Apr 19 15:16:50 kakyo-laptop kernel: [   15.438895] CPU: L1 I cache: 32K, L1 D cache: 32K
Apr 19 15:16:50 kakyo-laptop kernel: [   15.438897] CPU: L2 cache: 2048K
Apr 19 15:16:50 kakyo-laptop kernel: [   15.438899] CPU: Physical Processor ID: 0
Apr 19 15:16:50 kakyo-laptop kernel: [   15.438901] CPU: Processor Core ID: 0
Apr 19 15:16:50 kakyo-laptop kernel: [   15.438902] CPU: After all inits, caps: bfebfbff 20100000 00000000 00043940 0000e39d 00000000 00000001 00000000
Apr 19 15:16:50 kakyo-laptop kernel: [   15.438911] Compat vDSO mapped to ffffe000.
Apr 19 15:16:50 kakyo-laptop kernel: [   15.438922] Checking 'hlt' instruction... OK.
Apr 19 15:16:50 kakyo-laptop kernel: [   15.479046] SMP alternatives: switching to UP code
Apr 19 15:16:50 kakyo-laptop kernel: [   15.480414] Early unpacking initramfs... done
Apr 19 15:16:50 kakyo-laptop kernel: [   15.784373] ACPI: Core revision 20070126
Apr 19 15:16:50 kakyo-laptop kernel: [   15.784420] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
Apr 19 15:16:50 kakyo-laptop kernel: [   15.848299] CPU0: Intel(R) Core(TM)2 Duo CPU     T5750  @ 2.00GHz stepping 0d
Apr 19 15:16:50 kakyo-laptop kernel: [   15.848313] SMP alternatives: switching to SMP code
Apr 19 15:16:50 kakyo-laptop kernel: [   15.848955] Booting processor 1/1 eip 3000
Apr 19 15:16:50 kakyo-laptop kernel: [   15.859219] Initializing CPU#1
Apr 19 15:16:50 kakyo-laptop kernel: [   16.008448] Calibrating delay using timer specific routine.. 3990.32 BogoMIPS (lpj=19951634)
Apr 19 15:16:50 kakyo-laptop kernel: [   16.008454] CPU: After generic identify, caps: bfebfbff 20100000 00000000 00000000 0000e39d 00000000 00000001 00000000
Apr 19 15:16:50 kakyo-laptop kernel: [   16.008458] monitor/mwait feature present.
Apr 19 15:16:50 kakyo-laptop kernel: [   16.008460] CPU: L1 I cache: 32K, L1 D cache: 32K
Apr 19 15:16:50 kakyo-laptop kernel: [   16.008462] CPU: L2 cache: 2048K
Apr 19 15:16:50 kakyo-laptop kernel: [   16.008464] CPU: Physical Processor ID: 0
Apr 19 15:16:50 kakyo-laptop kernel: [   16.008465] CPU: Processor Core ID: 1
Apr 19 15:16:50 kakyo-laptop kernel: [   16.008466] CPU: After all inits, caps: bfebfbff 20100000 00000000 00043940 0000e39d 00000000 00000001 00000000
Apr 19 15:16:50 kakyo-laptop kernel: [   16.008959] CPU1: Intel(R) Core(TM)2 Duo CPU     T5750  @ 2.00GHz stepping 0d
Apr 19 15:16:50 kakyo-laptop kernel: [   16.008979] Total of 2 processors activated (7984.12 BogoMIPS).
Apr 19 15:16:50 kakyo-laptop kernel: [   16.009153] ENABLING IO-APIC IRQs
Apr 19 15:16:50 kakyo-laptop kernel: [   16.009341] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
Apr 19 15:16:50 kakyo-laptop kernel: [   16.228448] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
Apr 19 15:16:50 kakyo-laptop kernel: [   16.248452] Brought up 2 CPUs
Apr 19 15:16:50 kakyo-laptop kernel: [   16.248470] CPU0 attaching sched-domain:
Apr 19 15:16:50 kakyo-laptop kernel: [   16.248472]  domain 0: span 03
Apr 19 15:16:50 kakyo-laptop kernel: [   16.248473]   groups: 01 02
Apr 19 15:16:50 kakyo-laptop kernel: [   16.248476] CPU1 attaching sched-domain:
Apr 19 15:16:50 kakyo-laptop kernel: [   16.248478]  domain 0: span 03
Apr 19 15:16:50 kakyo-laptop kernel: [   16.248479]   groups: 02 01
Apr 19 15:16:50 kakyo-laptop kernel: [   16.248663] net_namespace: 64 bytes
Apr 19 15:16:50 kakyo-laptop kernel: [   16.248674] Booting paravirtualized kernel on bare hardware
Apr 19 15:16:50 kakyo-laptop kernel: [   16.249085] Time: 19:16:27  Date: 04/19/09
Apr 19 15:16:50 kakyo-laptop kernel: [   16.249109] NET: Registered protocol family 16
Apr 19 15:16:50 kakyo-laptop kernel: [   16.249265] EISA bus registered
Apr 19 15:16:50 kakyo-laptop kernel: [   16.249269] ACPI: bus type pci registered
Apr 19 15:16:50 kakyo-laptop kernel: [   16.249653] PCI: PCI BIOS revision 3.00 entry at 0xfde31, last bus=9
Apr 19 15:16:50 kakyo-laptop kernel: [   16.249655] PCI: Using configuration type 1
Apr 19 15:16:50 kakyo-laptop kernel: [   16.249669] Setting up standard PCI resources
Apr 19 15:16:50 kakyo-laptop kernel: [   16.251815] ACPI: EC: Look up EC in DSDT
Apr 19 15:16:50 kakyo-laptop kernel: [   16.253823] ACPI: BIOS _OSI(Linux) query ignored via DMI
Apr 19 15:16:50 kakyo-laptop kernel: [   16.254839] ACPI: Interpreter enabled
Apr 19 15:16:50 kakyo-laptop kernel: [   16.254842] ACPI: (supports S0 S3 S4 S5)
Apr 19 15:16:50 kakyo-laptop kernel: [   16.254854] ACPI: Using IOAPIC for interrupt routing
Apr 19 15:16:50 kakyo-laptop kernel: [   16.256138] ACPI: EC: non-query interrupt received, switching to interrupt mode
Apr 19 15:16:50 kakyo-laptop kernel: [   16.264646] ACPI: EC: GPE = 0x17, I/O: command/status = 0x66, data = 0x62
Apr 19 15:16:50 kakyo-laptop kernel: [   16.264649] ACPI: EC: driver started in interrupt mode
Apr 19 15:16:50 kakyo-laptop kernel: [   16.264685] ACPI: PCI Root Bridge [PCI0] (0000:00)
Apr 19 15:16:50 kakyo-laptop kernel: [   16.265696] PCI quirk: region 1000-107f claimed by ICH6 ACPI/GPIO/TCO
Apr 19 15:16:50 kakyo-laptop kernel: [   16.265700] PCI quirk: region 1180-11bf claimed by ICH6 GPIO
Apr 19 15:16:50 kakyo-laptop kernel: [   16.266932] PCI: Transparent bridge - 0000:00:1e.0
Apr 19 15:16:50 kakyo-laptop kernel: [   16.266978] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
Apr 19 15:16:50 kakyo-laptop kernel: [   16.267245] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP01._PRT]
Apr 19 15:16:50 kakyo-laptop kernel: [   16.267361] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP02._PRT]
Apr 19 15:16:50 kakyo-laptop kernel: [   16.267473] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP06._PRT]
Apr 19 15:16:50 kakyo-laptop kernel: [   16.267598] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIB._PRT]
Apr 19 15:16:50 kakyo-laptop kernel: [   16.276755] ACPI: PCI Interrupt Link [LNKA] (IRQs 1 3 4 *5 6 7 10 12 14 15)
Apr 19 15:16:50 kakyo-laptop kernel: [   16.276848] ACPI: PCI Interrupt Link [LNKB] (IRQs 1 3 4 5 6 7 11 12 14 15) *10
Apr 19 15:16:50 kakyo-laptop kernel: [   16.276940] ACPI: PCI Interrupt Link [LNKC] (IRQs 1 3 4 5 6 *7 10 12 14 15)
Apr 19 15:16:50 kakyo-laptop kernel: [   16.277032] ACPI: PCI Interrupt Link [LNKD] (IRQs 1 3 4 5 6 7 11 12 14 15) *10
Apr 19 15:16:50 kakyo-laptop kernel: [   16.277126] ACPI: PCI Interrupt Link [LNKE] (IRQs 1 3 4 5 6 7 10 12 14 15) *11
Apr 19 15:16:50 kakyo-laptop kernel: [   16.277217] ACPI: PCI Interrupt Link [LNKF] (IRQs 1 3 4 5 6 7 *11 12 14 15)
Apr 19 15:16:50 kakyo-laptop kernel: [   16.277307] ACPI: PCI Interrupt Link [LNKG] (IRQs 1 3 4 5 6 7 10 12 14 15) *11
Apr 19 15:16:50 kakyo-laptop kernel: [   16.277398] ACPI: PCI Interrupt Link [LNKH] (IRQs 1 3 4 5 6 7 11 12 14 15) *10
Apr 19 15:16:50 kakyo-laptop kernel: [   16.277524] Linux Plug and Play Support v0.97 (c) Adam Belay
Apr 19 15:16:50 kakyo-laptop kernel: [   16.277549] pnp: PnP ACPI init
Apr 19 15:16:50 kakyo-laptop kernel: [   16.277555] ACPI: bus type pnp registered
Apr 19 15:16:50 kakyo-laptop kernel: [   16.282606] pnp: PnP ACPI: found 11 devices
Apr 19 15:16:50 kakyo-laptop kernel: [   16.282608] ACPI: ACPI bus type pnp unregistered
Apr 19 15:16:50 kakyo-laptop kernel: [   16.282610] PnPBIOS: Disabled by ACPI PNP
Apr 19 15:16:50 kakyo-laptop kernel: [   16.282790] PCI: Using ACPI for IRQ routing
Apr 19 15:16:50 kakyo-laptop kernel: [   16.282792] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
Apr 19 15:16:50 kakyo-laptop kernel: [   16.418375] NET: Registered protocol family 8
Apr 19 15:16:50 kakyo-laptop kernel: [   16.418377] NET: Registered protocol family 20
Apr 19 15:16:50 kakyo-laptop kernel: [   16.418399] NetLabel: Initializing
Apr 19 15:16:50 kakyo-laptop kernel: [   16.418400] NetLabel:  domain hash size = 128
Apr 19 15:16:50 kakyo-laptop kernel: [   16.418402] NetLabel:  protocols = UNLABELED CIPSOv4
Apr 19 15:16:50 kakyo-laptop kernel: [   16.418411] NetLabel:  unlabeled traffic allowed by default
Apr 19 15:16:50 kakyo-laptop kernel: [   16.418417] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
Apr 19 15:16:50 kakyo-laptop kernel: [   16.418421] hpet0: 3 64-bit timers, 14318180 Hz
Apr 19 15:16:50 kakyo-laptop kernel: [   16.419450] AppArmor: AppArmor Filesystem Enabled
Apr 19 15:16:50 kakyo-laptop kernel: [   16.428266] Time: tsc clocksource has been installed.
Apr 19 15:16:50 kakyo-laptop kernel: [   16.428277] Switched to high resolution mode on CPU 0
Apr 19 15:16:50 kakyo-laptop kernel: [   16.428366] Switched to high resolution mode on CPU 1
Apr 19 15:16:50 kakyo-laptop kernel: [   16.460777] system 00:01: iomem range 0xfed1c000-0xfed1ffff could not be reserved
Apr 19 15:16:50 kakyo-laptop kernel: [   16.460780] system 00:01: iomem range 0xfed14000-0xfed17fff could not be reserved
Apr 19 15:16:50 kakyo-laptop kernel: [   16.460783] system 00:01: iomem range 0xfed18000-0xfed18fff could not be reserved
Apr 19 15:16:50 kakyo-laptop kernel: [   16.460785] system 00:01: iomem range 0xfed19000-0xfed19fff could not be reserved
Apr 19 15:16:50 kakyo-laptop kernel: [   16.460787] system 00:01: iomem range 0xe0000000-0xefffffff could not be reserved
Apr 19 15:16:50 kakyo-laptop kernel: [   16.460790] system 00:01: iomem range 0xfed20000-0xfed3ffff could not be reserved
Apr 19 15:16:50 kakyo-laptop kernel: [   16.460792] system 00:01: iomem range 0xfed40000-0xfed44fff could not be reserved
Apr 19 15:16:50 kakyo-laptop kernel: [   16.460795] system 00:01: iomem range 0xfed45000-0xfed8ffff could not be reserved
Apr 19 15:16:50 kakyo-laptop kernel: [   16.460801] system 00:04: iomem range 0xfed00000-0xfed003ff could not be reserved
Apr 19 15:16:50 kakyo-laptop kernel: [   16.460807] system 00:06: ioport range 0x380-0x383 has been reserved
Apr 19 15:16:50 kakyo-laptop kernel: [   16.460809] system 00:06: ioport range 0x680-0x69f has been reserved
Apr 19 15:16:50 kakyo-laptop kernel: [   16.460811] system 00:06: ioport range 0x800-0x80f has been reserved
Apr 19 15:16:50 kakyo-laptop kernel: [   16.460813] system 00:06: ioport range 0x1000-0x107f has been reserved
Apr 19 15:16:50 kakyo-laptop kernel: [   16.460816] system 00:06: ioport range 0x1180-0x11bf has been reserved
Apr 19 15:16:50 kakyo-laptop kernel: [   16.460818] system 00:06: ioport range 0x1640-0x164f has been reserved
Apr 19 15:16:50 kakyo-laptop kernel: [   16.460820] system 00:06: ioport range 0xfe00-0xfe00 has been reserved
Apr 19 15:16:50 kakyo-laptop kernel: [   16.460825] system 00:07: ioport range 0x6a0-0x6af has been reserved
Apr 19 15:16:50 kakyo-laptop kernel: [   16.460827] system 00:07: ioport range 0x6b0-0x6ff has been reserved
Apr 19 15:16:50 kakyo-laptop kernel: [   16.491157] PCI: Bridge: 0000:00:1c.0
Apr 19 15:16:50 kakyo-laptop kernel: [   16.491161]   IO window: 4000-7fff
Apr 19 15:16:50 kakyo-laptop kernel: [   16.491166]   MEM window: f4000000-f5ffffff
Apr 19 15:16:50 kakyo-laptop kernel: [   16.491171]   PREFETCH window: f0000000-f1ffffff
Apr 19 15:16:50 kakyo-laptop kernel: [   16.491177] PCI: Bridge: 0000:00:1c.1
Apr 19 15:16:50 kakyo-laptop kernel: [   16.491179]   IO window: 8000-bfff
Apr 19 15:16:50 kakyo-laptop kernel: [   16.491185]   MEM window: f6000000-f7ffffff
Apr 19 15:16:50 kakyo-laptop kernel: [   16.491189]   PREFETCH window: f2000000-f3ffffff
Apr 19 15:16:50 kakyo-laptop kernel: [   16.491195] PCI: Bridge: 0000:00:1c.5
Apr 19 15:16:50 kakyo-laptop kernel: [   16.491198]   IO window: c000-cfff
Apr 19 15:16:50 kakyo-laptop kernel: [   16.491204]   MEM window: f8200000-f82fffff
Apr 19 15:16:50 kakyo-laptop kernel: [   16.491208]   PREFETCH window: c2000000-c20fffff
Apr 19 15:16:50 kakyo-laptop kernel: [   16.491214] PCI: Bridge: 0000:00:1e.0
Apr 19 15:16:50 kakyo-laptop kernel: [   16.491215]   IO window: disabled.
Apr 19 15:16:50 kakyo-laptop kernel: [   16.491221]   MEM window: f8300000-f83fffff
Apr 19 15:16:50 kakyo-laptop kernel: [   16.491225]   PREFETCH window: disabled.
Apr 19 15:16:50 kakyo-laptop kernel: [   16.491257] ACPI: PCI Interrupt 0000:00:1c.0[A] -> GSI 17 (level, low) -> IRQ 16
Apr 19 15:16:50 kakyo-laptop kernel: [   16.491263] PCI: Setting latency timer of device 0000:00:1c.0 to 64
Apr 19 15:16:50 kakyo-laptop kernel: [   16.491288] ACPI: PCI Interrupt 0000:00:1c.1[B] -> GSI 16 (level, low) -> IRQ 17
Apr 19 15:16:50 kakyo-laptop kernel: [   16.491294] PCI: Setting latency timer of device 0000:00:1c.1 to 64
Apr 19 15:16:50 kakyo-laptop kernel: [   16.491318] ACPI: PCI Interrupt 0000:00:1c.5[B] -> GSI 16 (level, low) -> IRQ 17
Apr 19 15:16:50 kakyo-laptop kernel: [   16.491324] PCI: Setting latency timer of device 0000:00:1c.5 to 64
Apr 19 15:16:50 kakyo-laptop kernel: [   16.491338] PCI: Setting latency timer of device 0000:00:1e.0 to 64
Apr 19 15:16:50 kakyo-laptop kernel: [   16.491347] NET: Registered protocol family 2
Apr 19 15:16:50 kakyo-laptop kernel: [   16.590749] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
Apr 19 15:16:50 kakyo-laptop kernel: [   16.590945] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
Apr 19 15:16:50 kakyo-laptop kernel: [   16.591339] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
Apr 19 15:16:50 kakyo-laptop kernel: [   16.591540] TCP: Hash tables configured (established 131072 bind 65536)
Apr 19 15:16:50 kakyo-laptop kernel: [   16.591543] TCP reno registered
Apr 19 15:16:50 kakyo-laptop kernel: [   16.620796] checking if image is initramfs... it is
Apr 19 15:16:50 kakyo-laptop kernel: [   17.216996] Freeing initrd memory: 7759k freed
Apr 19 15:16:50 kakyo-laptop kernel: [   17.217137] Simple Boot Flag at 0x35 set to 0x1
Apr 19 15:16:50 kakyo-laptop kernel: [   17.217662] audit: initializing netlink socket (disabled)
Apr 19 15:16:50 kakyo-laptop kernel: [   17.217675] audit(1240168587.670:1): initialized
Apr 19 15:16:50 kakyo-laptop kernel: [   17.218070] highmem bounce pool size: 64 pages
Apr 19 15:16:50 kakyo-laptop kernel: [   17.218073] Total HugeTLB memory allocated, 0
Apr 19 15:16:50 kakyo-laptop kernel: [   17.219714] VFS: Disk quotas dquot_6.5.1
Apr 19 15:16:50 kakyo-laptop kernel: [   17.219779] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
Apr 19 15:16:50 kakyo-laptop kernel: [   17.219950] io scheduler noop registered
Apr 19 15:16:50 kakyo-laptop kernel: [   17.219951] io scheduler anticipatory registered
Apr 19 15:16:50 kakyo-laptop kernel: [   17.219953] io scheduler deadline registered (default)
Apr 19 15:16:50 kakyo-laptop kernel: [   17.219964] io scheduler cfq registered
Apr 19 15:16:50 kakyo-laptop kernel: [   17.219974] Boot video device is 0000:00:02.0
Apr 19 15:16:50 kakyo-laptop kernel: [   17.220191] PCI: Setting latency timer of device 0000:00:1c.0 to 64
Apr 19 15:16:50 kakyo-laptop kernel: [   17.220252] assign_interrupt_mode Found MSI capability
Apr 19 15:16:50 kakyo-laptop kernel: [   17.220303] Allocate Port Service[0000:00:1c.0:pcie00]
Apr 19 15:16:50 kakyo-laptop kernel: [   17.220333] Allocate Port Service[0000:00:1c.0:pcie02]
Apr 19 15:16:50 kakyo-laptop kernel: [   17.220440] PCI: Setting latency timer of device 0000:00:1c.1 to 64
Apr 19 15:16:50 kakyo-laptop kernel: [   17.220501] assign_interrupt_mode Found MSI capability
Apr 19 15:16:50 kakyo-laptop kernel: [   17.220549] Allocate Port Service[0000:00:1c.1:pcie00]
Apr 19 15:16:50 kakyo-laptop kernel: [   17.220576] Allocate Port Service[0000:00:1c.1:pcie02]
Apr 19 15:16:50 kakyo-laptop kernel: [   17.220675] PCI: Setting latency timer of device 0000:00:1c.5 to 64
Apr 19 15:16:50 kakyo-laptop kernel: [   17.220736] assign_interrupt_mode Found MSI capability
Apr 19 15:16:50 kakyo-laptop kernel: [   17.220784] Allocate Port Service[0000:00:1c.5:pcie00]
Apr 19 15:16:50 kakyo-laptop kernel: [   17.220808] Allocate Port Service[0000:00:1c.5:pcie02]
Apr 19 15:16:50 kakyo-laptop kernel: [   17.221032] isapnp: Scanning for PnP cards...
Apr 19 15:16:50 kakyo-laptop kernel: [   17.578164] isapnp: No Plug & Play device found
Apr 19 15:16:50 kakyo-laptop kernel: [   17.598201] Real Time Clock Driver v1.12ac
Apr 19 15:16:50 kakyo-laptop kernel: [   17.598403] hpet_resources: 0xfed00000 is busy
Apr 19 15:16:50 kakyo-laptop kernel: [   17.598429] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
Apr 19 15:16:50 kakyo-laptop kernel: [   17.599447] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
Apr 19 15:16:50 kakyo-laptop kernel: [   17.599506] input: Macintosh mouse button emulation as /devices/virtual/input/input0
Apr 19 15:16:50 kakyo-laptop kernel: [   17.599587] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
Apr 19 15:16:50 kakyo-laptop kernel: [   17.641101] serio: i8042 KBD port at 0x60,0x64 irq 1
Apr 19 15:16:50 kakyo-laptop kernel: [   17.641105] serio: i8042 AUX port at 0x60,0x64 irq 12
Apr 19 15:16:50 kakyo-laptop kernel: [   17.677838] mice: PS/2 mouse device common for all mice
Apr 19 15:16:50 kakyo-laptop kernel: [   17.677935] EISA: Probing bus 0 at eisa.0
Apr 19 15:16:50 kakyo-laptop kernel: [   17.677942] Cannot allocate resource for EISA slot 1
Apr 19 15:16:50 kakyo-laptop kernel: [   17.677954] Cannot allocate resource for EISA slot 4
Apr 19 15:16:50 kakyo-laptop kernel: [   17.677956] Cannot allocate resource for EISA slot 5
Apr 19 15:16:50 kakyo-laptop kernel: [   17.677957] Cannot allocate resource for EISA slot 6
Apr 19 15:16:50 kakyo-laptop kernel: [   17.677959] Cannot allocate resource for EISA slot 7
Apr 19 15:16:50 kakyo-laptop kernel: [   17.677961] Cannot allocate resource for EISA slot 8
Apr 19 15:16:50 kakyo-laptop kernel: [   17.677963] EISA: Detected 0 cards.
Apr 19 15:16:50 kakyo-laptop kernel: [   17.677965] cpuidle: using governor ladder
Apr 19 15:16:50 kakyo-laptop kernel: [   17.677967] cpuidle: using governor menu
Apr 19 15:16:50 kakyo-laptop kernel: [   17.678044] NET: Registered protocol family 1
Apr 19 15:16:50 kakyo-laptop kernel: [   17.678069] Using IPI No-Shortcut mode
Apr 19 15:16:50 kakyo-laptop kernel: [   17.678098] registered taskstats version 1
Apr 19 15:16:50 kakyo-laptop kernel: [   17.678209]   Magic number: 5:151:294
Apr 19 15:16:50 kakyo-laptop kernel: [   17.678212]   hash matches device hpet
Apr 19 15:16:50 kakyo-laptop kernel: [   17.678220]   hash matches device ttyz8
Apr 19 15:16:50 kakyo-laptop kernel: [   17.678224]   hash matches device ttywb
Apr 19 15:16:50 kakyo-laptop kernel: [   17.678264]   hash matches device tty27
Apr 19 15:16:50 kakyo-laptop kernel: [   17.678282] BIOS EDD facility v0.16 2004-Jun-25, 6 devices found
Apr 19 15:16:50 kakyo-laptop kernel: [   17.678620] Freeing unused kernel memory: 384k freed
Apr 19 15:16:50 kakyo-laptop kernel: [   17.678660] Write protecting the kernel read-only data: 828k
Apr 19 15:16:50 kakyo-laptop kernel: [   17.706290] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
Apr 19 15:16:50 kakyo-laptop kernel: [   18.869502] fuse init (API version 7.9)
Apr 19 15:16:50 kakyo-laptop kernel: [   18.886680] ACPI: SSDT BF6D69B7, 0238 (r1  HP    30CC         3000 INTL 20061109)
Apr 19 15:16:50 kakyo-laptop kernel: [   18.886888] ACPI: SSDT BF6D635A, 05D8 (r1  HP    30CC         3001 INTL 20061109)
Apr 19 15:16:50 kakyo-laptop kernel: [   18.888549] Monitor-Mwait will be used to enter C-1 state
Apr 19 15:16:50 kakyo-laptop kernel: [   18.888552] Monitor-Mwait will be used to enter C-2 state
Apr 19 15:16:50 kakyo-laptop kernel: [   18.888554] Monitor-Mwait will be used to enter C-3 state
Apr 19 15:16:50 kakyo-laptop kernel: [   18.888654] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
Apr 19 15:16:50 kakyo-laptop kernel: [   18.888658] ACPI: Processor [CPU0] (supports 8 throttling states)
Apr 19 15:16:50 kakyo-laptop kernel: [   18.888864] ACPI: SSDT BF6D6BEF, 00C8 (r1  HP    30CC         3000 INTL 20061109)
Apr 19 15:16:50 kakyo-laptop kernel: [   18.889057] ACPI: SSDT BF6D6932, 0085 (r1  HP    30CC         3000 INTL 20061109)
Apr 19 15:16:50 kakyo-laptop kernel: [   18.889885] Marking TSC unstable due to: TSC halts in idle.
Apr 19 15:16:50 kakyo-laptop kernel: [   18.889936] ACPI: CPU1 (power states: C1[C1] C2[C2] C3[C3])
Apr 19 15:16:50 kakyo-laptop kernel: [   18.889940] ACPI: Processor [CPU1] (supports 8 throttling states)
Apr 19 15:16:50 kakyo-laptop kernel: [   18.891657] ACPI Exception (thermal-0339): AE_BAD_DATA, No critical threshold [20070126]
Apr 19 15:16:50 kakyo-laptop kernel: [   18.897295] Time: hpet clocksource has been installed.
Apr 19 15:16:50 kakyo-laptop kernel: [   19.146966] usbcore: registered new interface driver usbfs
Apr 19 15:16:50 kakyo-laptop kernel: [   19.146988] usbcore: registered new interface driver hub
Apr 19 15:16:50 kakyo-laptop kernel: [   19.147546] usbcore: registered new device driver usb
Apr 19 15:16:50 kakyo-laptop kernel: [   19.149284] USB Universal Host Controller Interface driver v3.0
Apr 19 15:16:50 kakyo-laptop kernel: [   19.149334] ACPI: PCI Interrupt 0000:00:1a.0[A] -> GSI 16 (level, low) -> IRQ 17
Apr 19 15:16:50 kakyo-laptop kernel: [   19.149345] PCI: Setting latency timer of device 0000:00:1a.0 to 64
Apr 19 15:16:50 kakyo-laptop kernel: [   19.149349] uhci_hcd 0000:00:1a.0: UHCI Host Controller
Apr 19 15:16:50 kakyo-laptop kernel: [   19.149563] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 1
Apr 19 15:16:50 kakyo-laptop kernel: [   19.149597] uhci_hcd 0000:00:1a.0: irq 17, io base 0x00001820
Apr 19 15:16:50 kakyo-laptop kernel: [   19.149756] usb usb1: configuration #1 chosen from 1 choice
Apr 19 15:16:50 kakyo-laptop kernel: [   19.149776] hub 1-0:1.0: USB hub found
Apr 19 15:16:50 kakyo-laptop kernel: [   19.149781] hub 1-0:1.0: 2 ports detected
Apr 19 15:16:50 kakyo-laptop kernel: [   19.219582] SCSI subsystem initialized
Apr 19 15:16:50 kakyo-laptop kernel: [   19.234633] libata version 3.00 loaded.
Apr 19 15:16:50 kakyo-laptop kernel: [   19.259745] ACPI: PCI Interrupt 0000:00:1a.1[B] -> GSI 21 (level, low) -> IRQ 18
Apr 19 15:16:50 kakyo-laptop kernel: [   19.259758] PCI: Setting latency timer of device 0000:00:1a.1 to 64
Apr 19 15:16:50 kakyo-laptop kernel: [   19.259762] uhci_hcd 0000:00:1a.1: UHCI Host Controller
Apr 19 15:16:50 kakyo-laptop kernel: [   19.259783] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 2
Apr 19 15:16:50 kakyo-laptop kernel: [   19.259818] uhci_hcd 0000:00:1a.1: irq 18, io base 0x00001840
Apr 19 15:16:50 kakyo-laptop kernel: [   19.259919] usb usb2: configuration #1 chosen from 1 choice
Apr 19 15:16:50 kakyo-laptop kernel: [   19.259941] hub 2-0:1.0: USB hub found
Apr 19 15:16:50 kakyo-laptop kernel: [   19.259946] hub 2-0:1.0: 2 ports detected
Apr 19 15:16:50 kakyo-laptop kernel: [   19.369229] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 23 (level, low) -> IRQ 19
Apr 19 15:16:50 kakyo-laptop kernel: [   19.369242] PCI: Setting latency timer of device 0000:00:1d.0 to 64
Apr 19 15:16:50 kakyo-laptop kernel: [   19.369246] uhci_hcd 0000:00:1d.0: UHCI Host Controller
Apr 19 15:16:50 kakyo-laptop kernel: [   19.369266] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 3
Apr 19 15:16:50 kakyo-laptop kernel: [   19.369300] uhci_hcd 0000:00:1d.0: irq 19, io base 0x00001860
Apr 19 15:16:50 kakyo-laptop kernel: [   19.369406] usb usb3: configuration #1 chosen from 1 choice
Apr 19 15:16:50 kakyo-laptop kernel: [   19.369431] hub 3-0:1.0: USB hub found
Apr 19 15:16:50 kakyo-laptop kernel: [   19.369436] hub 3-0:1.0: 2 ports detected
Apr 19 15:16:50 kakyo-laptop kernel: [   19.479663] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 19 (level, low) -> IRQ 20
Apr 19 15:16:50 kakyo-laptop kernel: [   19.479674] PCI: Setting latency timer of device 0000:00:1d.1 to 64
Apr 19 15:16:50 kakyo-laptop kernel: [   19.479678] uhci_hcd 0000:00:1d.1: UHCI Host Controller
Apr 19 15:16:50 kakyo-laptop kernel: [   19.479698] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 4
Apr 19 15:16:50 kakyo-laptop kernel: [   19.479731] uhci_hcd 0000:00:1d.1: irq 20, io base 0x00001880
Apr 19 15:16:50 kakyo-laptop kernel: [   19.479835] usb usb4: configuration #1 chosen from 1 choice
Apr 19 15:16:50 kakyo-laptop kernel: [   19.479855] hub 4-0:1.0: USB hub found
Apr 19 15:16:50 kakyo-laptop kernel: [   19.479859] hub 4-0:1.0: 2 ports detected
Apr 19 15:16:50 kakyo-laptop kernel: [   19.589612] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 21
Apr 19 15:16:50 kakyo-laptop kernel: [   19.589625] PCI: Setting latency timer of device 0000:00:1d.2 to 64
Apr 19 15:16:50 kakyo-laptop kernel: [   19.589629] uhci_hcd 0000:00:1d.2: UHCI Host Controller
Apr 19 15:16:50 kakyo-laptop kernel: [   19.589652] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 5
Apr 19 15:16:50 kakyo-laptop kernel: [   19.589685] uhci_hcd 0000:00:1d.2: irq 21, io base 0x000018a0
Apr 19 15:16:50 kakyo-laptop kernel: [   19.589796] usb usb5: configuration #1 chosen from 1 choice
Apr 19 15:16:50 kakyo-laptop kernel: [   19.589816] hub 5-0:1.0: USB hub found
Apr 19 15:16:50 kakyo-laptop kernel: [   19.589820] hub 5-0:1.0: 2 ports detected
Apr 19 15:16:50 kakyo-laptop kernel: [   19.642538] ACPI: PCI Interrupt 0000:00:1a.7[C] -> GSI 18 (level, low) -> IRQ 21
Apr 19 15:16:50 kakyo-laptop kernel: [   19.642561] PCI: Setting latency timer of device 0000:00:1a.7 to 64
Apr 19 15:16:50 kakyo-laptop kernel: [   19.642568] ehci_hcd 0000:00:1a.7: EHCI Host Controller
Apr 19 15:16:50 kakyo-laptop kernel: [   19.642604] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 6
Apr 19 15:16:50 kakyo-laptop kernel: [   19.646505] ehci_hcd 0000:00:1a.7: debug port 1
Apr 19 15:16:50 kakyo-laptop kernel: [   19.646513] PCI: cache line size of 32 is not supported by device 0000:00:1a.7
Apr 19 15:16:50 kakyo-laptop kernel: [   19.646518] ehci_hcd 0000:00:1a.7: irq 21, io mem 0xf8604800
Apr 19 15:16:50 kakyo-laptop kernel: [   19.669836] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
Apr 19 15:16:50 kakyo-laptop kernel: [   19.669954] usb usb6: configuration #1 chosen from 1 choice
Apr 19 15:16:50 kakyo-laptop kernel: [   19.669975] hub 6-0:1.0: USB hub found
Apr 19 15:16:50 kakyo-laptop kernel: [   19.669980] hub 6-0:1.0: 4 ports detected
Apr 19 15:16:50 kakyo-laptop kernel: [   19.690056] ACPI: PCI Interrupt 0000:00:1d.7[A] -> GSI 23 (level, low) -> IRQ 19
Apr 19 15:16:50 kakyo-laptop kernel: [   19.690078] PCI: Setting latency timer of device 0000:00:1d.7 to 64
Apr 19 15:16:50 kakyo-laptop kernel: [   19.690084] ehci_hcd 0000:00:1d.7: EHCI Host Controller
Apr 19 15:16:50 kakyo-laptop kernel: [   19.690121] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 7
Apr 19 15:16:50 kakyo-laptop kernel: [   19.694041] ehci_hcd 0000:00:1d.7: debug port 1
Apr 19 15:16:50 kakyo-laptop kernel: [   19.694048] PCI: cache line size of 32 is not supported by device 0000:00:1d.7
Apr 19 15:16:50 kakyo-laptop kernel: [   19.694053] ehci_hcd 0000:00:1d.7: irq 19, io mem 0xf8604c00
Apr 19 15:16:50 kakyo-laptop kernel: [   19.699101] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
Apr 19 15:16:50 kakyo-laptop kernel: [   19.699268] usb usb7: configuration #1 chosen from 1 choice
Apr 19 15:16:50 kakyo-laptop kernel: [   19.699306] hub 7-0:1.0: USB hub found
Apr 19 15:16:50 kakyo-laptop kernel: [   19.699313] hub 7-0:1.0: 6 ports detected
Apr 19 15:16:50 kakyo-laptop kernel: [   19.706755] ahci 0000:00:1f.2: version 3.0
Apr 19 15:16:50 kakyo-laptop kernel: [   19.706779] ACPI: PCI Interrupt 0000:00:1f.2[B] -> GSI 19 (level, low) -> IRQ 20
Apr 19 15:16:50 kakyo-laptop kernel: [   19.722137] Clocksource tsc unstable (delta = -315127167 ns)
Apr 19 15:16:50 kakyo-laptop kernel: [   19.752741] usb 7-4: new high speed USB device using ehci_hcd and address 2
Apr 19 15:16:50 kakyo-laptop kernel: [   19.908931] usb 7-4: configuration #1 chosen from 1 choice
Apr 19 15:16:50 kakyo-laptop kernel: [   20.071235] ahci 0000:00:1f.2: AHCI 0001.0100 32 slots 3 ports 3 Gbps 0x7 impl SATA mode
Apr 19 15:16:50 kakyo-laptop kernel: [   20.071244] ahci 0000:00:1f.2: flags: 64bit ncq sntf pm led clo pio slum part 
Apr 19 15:16:50 kakyo-laptop kernel: [   20.071254] PCI: Setting latency timer of device 0000:00:1f.2 to 64
Apr 19 15:16:50 kakyo-laptop kernel: [   20.071565] scsi0 : ahci
Apr 19 15:16:50 kakyo-laptop kernel: [   20.071778] scsi1 : ahci
Apr 19 15:16:50 kakyo-laptop kernel: [   20.071892] scsi2 : ahci
Apr 19 15:16:50 kakyo-laptop kernel: [   20.071975] ata1: SATA max UDMA/133 abar m2048@0xf8604000 port 0xf8604100 irq 220
Apr 19 15:16:50 kakyo-laptop kernel: [   20.071979] ata2: SATA max UDMA/133 abar m2048@0xf8604000 port 0xf8604180 irq 220
Apr 19 15:16:50 kakyo-laptop kernel: [   20.071982] ata3: SATA max UDMA/133 abar m2048@0xf8604000 port 0xf8604200 irq 220
Apr 19 15:16:50 kakyo-laptop kernel: [   20.079782] usb 2-2: new low speed USB device using uhci_hcd and address 2
Apr 19 15:16:50 kakyo-laptop kernel: [   20.098811] usb 2-2: configuration #1 chosen from 1 choice
Apr 19 15:16:50 kakyo-laptop kernel: [   20.110352] usbcore: registered new interface driver hiddev
Apr 19 15:16:50 kakyo-laptop kernel: [   20.115166] input: Logitech USB Optical Mouse as /devices/pci0000:00/0000:00:1a.1/usb2/2-2/2-2:1.0/input/input2
Apr 19 15:16:50 kakyo-laptop kernel: [   20.126422] input,hidraw0: USB HID v1.10 Mouse [Logitech USB Optical Mouse] on usb-0000:00:1a.1-2
Apr 19 15:16:50 kakyo-laptop kernel: [   20.126447] usbcore: registered new interface driver usbhid
Apr 19 15:16:50 kakyo-laptop kernel: [   20.126452] /build/buildd/linux-2.6.24/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
Apr 19 15:16:50 kakyo-laptop kernel: [   20.143782] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
Apr 19 15:16:50 kakyo-laptop kernel: [   20.144234] ata1.00: ATA-8: WDC WD2500BEVS-60UST0, 01.01A01, max UDMA/100
Apr 19 15:16:50 kakyo-laptop kernel: [   20.144239] ata1.00: 488397168 sectors, multi 16: LBA48 
Apr 19 15:16:50 kakyo-laptop kernel: [   20.144801] ata1.00: configured for UDMA/100
Apr 19 15:16:50 kakyo-laptop kernel: [   20.170342] ata2: SATA link down (SStatus 0 SControl 300)
Apr 19 15:16:50 kakyo-laptop kernel: [   20.194608] ata3: SATA link down (SStatus 0 SControl 300)
Apr 19 15:16:50 kakyo-laptop kernel: [   20.194852] scsi 0:0:0:0: Direct-Access     ATA      WDC WD2500BEVS-6 01.0 PQ: 0 ANSI: 5
Apr 19 15:16:50 kakyo-laptop kernel: [   20.194934] r8169 Gigabit Ethernet driver 2.2LK loaded
Apr 19 15:16:50 kakyo-laptop kernel: [   20.194968] ACPI: PCI Interrupt 0000:08:00.0[A] -> GSI 17 (level, low) -> IRQ 16
Apr 19 15:16:50 kakyo-laptop kernel: [   20.194989] PCI: Setting latency timer of device 0000:08:00.0 to 64
Apr 19 15:16:50 kakyo-laptop kernel: [   20.195295] eth0: RTL8101e at 0xf8878000, 00:1e:68:99:1b:73, XID 34200000 IRQ 219
Apr 19 15:16:50 kakyo-laptop kernel: [   20.200351] ACPI: PCI Interrupt 0000:09:09.0[A] -> GSI 20 (level, low) -> IRQ 22
Apr 19 15:16:50 kakyo-laptop kernel: [   20.253459] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[22]  MMIO=[f8300000-f83007ff]  Max Packet=[2048]  IR/IT contexts=[4/4]
Apr 19 15:16:50 kakyo-laptop kernel: [   20.257562] ata_piix 0000:00:1f.1: version 2.12
Apr 19 15:16:50 kakyo-laptop kernel: [   20.257577] ACPI: PCI Interrupt 0000:00:1f.1[A] -> GSI 19 (level, low) -> IRQ 20
Apr 19 15:16:50 kakyo-laptop kernel: [   20.257611] PCI: Setting latency timer of device 0000:00:1f.1 to 64
Apr 19 15:16:50 kakyo-laptop kernel: [   20.259281] scsi3 : ata_piix
Apr 19 15:16:50 kakyo-laptop kernel: [   20.259751] Driver 'sd' needs updating - please use bus_type methods
Apr 19 15:16:50 kakyo-laptop kernel: [   20.259812] sd 0:0:0:0: [sda] 488397168 512-byte hardware sectors (250059 MB)
Apr 19 15:16:50 kakyo-laptop kernel: [   20.259822] sd 0:0:0:0: [sda] Write Protect is off
Apr 19 15:16:50 kakyo-laptop kernel: [   20.259824] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Apr 19 15:16:50 kakyo-laptop kernel: [   20.259838] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Apr 19 15:16:50 kakyo-laptop kernel: [   20.259877] sd 0:0:0:0: [sda] 488397168 512-byte hardware sectors (250059 MB)
Apr 19 15:16:50 kakyo-laptop kernel: [   20.259885] sd 0:0:0:0: [sda] Write Protect is off
Apr 19 15:16:50 kakyo-laptop kernel: [   20.259887] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Apr 19 15:16:50 kakyo-laptop kernel: [   20.259901] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Apr 19 15:16:50 kakyo-laptop kernel: [   20.259904]  sda:<6>scsi4 : ata_piix
Apr 19 15:16:50 kakyo-laptop kernel: [   20.260766] ata4: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0x1810 irq 14
Apr 19 15:16:50 kakyo-laptop kernel: [   20.260769] ata5: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x1818 irq 15
Apr 19 15:16:50 kakyo-laptop kernel: [   20.308426]  sda1 sda2
Apr 19 15:16:50 kakyo-laptop kernel: [   20.332906] sd 0:0:0:0: [sda] Attached SCSI disk
Apr 19 15:16:50 kakyo-laptop kernel: [   20.336695] sd 0:0:0:0: Attached scsi generic sg0 type 0
Apr 19 15:16:50 kakyo-laptop kernel: [   20.562075] ata4.00: ATAPI: Optiarc DVD RW AD-7561A, GH09, max MWDMA2
Apr 19 15:16:50 kakyo-laptop kernel: [   20.570245] ata4.00: configured for MWDMA2
Apr 19 15:16:50 kakyo-laptop kernel: [   20.586778] scsi 3:0:0:0: CD-ROM            Optiarc  DVD RW AD-7561A  GH09 PQ: 0 ANSI: 5
Apr 19 15:16:50 kakyo-laptop kernel: [   20.586907] scsi 3:0:0:0: Attached scsi generic sg1 type 5
Apr 19 15:16:50 kakyo-laptop kernel: [   20.595263] Driver 'sr' needs updating - please use bus_type methods
Apr 19 15:16:50 kakyo-laptop kernel: [   20.601738] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
Apr 19 15:16:50 kakyo-laptop kernel: [   20.601743] Uniform CD-ROM driver Revision: 3.20
Apr 19 15:16:50 kakyo-laptop kernel: [   20.601811] sr 3:0:0:0: Attached scsi CD-ROM sr0
Apr 19 15:16:50 kakyo-laptop kernel: [   20.657621] Attempting manual resume
Apr 19 15:16:50 kakyo-laptop kernel: [   20.657624] swsusp: Resume From Partition 8:2
Apr 19 15:16:50 kakyo-laptop kernel: [   20.657626] PM: Checking swsusp image.
Apr 19 15:16:50 kakyo-laptop kernel: [   20.657788] PM: Resume from disk failed.
Apr 19 15:16:50 kakyo-laptop kernel: [   20.671601] EXT3-fs: INFO: recovery required on readonly filesystem.
Apr 19 15:16:50 kakyo-laptop kernel: [   20.671607] EXT3-fs: write access will be enabled during recovery.
Apr 19 15:16:50 kakyo-laptop kernel: [   20.949172] kjournald starting.  Commit interval 5 seconds
Apr 19 15:16:50 kakyo-laptop kernel: [   20.949211] EXT3-fs: sda1: orphan cleanup on readonly fs
Apr 19 15:16:50 kakyo-laptop kernel: [   20.949220] ext3_orphan_cleanup: deleting unreferenced inode 1843800
Apr 19 15:16:50 kakyo-laptop kernel: [   20.963109] ext3_orphan_cleanup: deleting unreferenced inode 1847548
Apr 19 15:16:50 kakyo-laptop kernel: [   20.965099] ext3_orphan_cleanup: deleting unreferenced inode 1843837
Apr 19 15:16:50 kakyo-laptop kernel: [   20.965120] ext3_orphan_cleanup: deleting unreferenced inode 1843836
Apr 19 15:16:50 kakyo-laptop kernel: [   20.966284] ext3_orphan_cleanup: deleting unreferenced inode 1844408
Apr 19 15:16:50 kakyo-laptop kernel: [   20.966531] ext3_orphan_cleanup: deleting unreferenced inode 1844438
Apr 19 15:16:50 kakyo-laptop kernel: [   20.976516] ext3_orphan_cleanup: deleting unreferenced inode 1844431
Apr 19 15:16:50 kakyo-laptop kernel: [   20.976534] ext3_orphan_cleanup: deleting unreferenced inode 1844436
Apr 19 15:16:50 kakyo-laptop kernel: [   20.976756] ext3_orphan_cleanup: deleting unreferenced inode 1844452
Apr 19 15:16:50 kakyo-laptop kernel: [   20.976775] ext3_orphan_cleanup: deleting unreferenced inode 1844428
Apr 19 15:16:50 kakyo-laptop kernel: [   20.976795] ext3_orphan_cleanup: deleting unreferenced inode 1844427
Apr 19 15:16:50 kakyo-laptop kernel: [   20.976812] ext3_orphan_cleanup: deleting unreferenced inode 1844430
Apr 19 15:16:50 kakyo-laptop kernel: [   20.976830] ext3_orphan_cleanup: deleting unreferenced inode 1844429
Apr 19 15:16:50 kakyo-laptop kernel: [   20.976846] ext3_orphan_cleanup: deleting unreferenced inode 1844453
Apr 19 15:16:50 kakyo-laptop kernel: [   20.976864] ext3_orphan_cleanup: deleting unreferenced inode 1844444
Apr 19 15:16:50 kakyo-laptop kernel: [   20.976880] ext3_orphan_cleanup: deleting unreferenced inode 1844455
Apr 19 15:16:50 kakyo-laptop kernel: [   20.976896] ext3_orphan_cleanup: deleting unreferenced inode 1844457
Apr 19 15:16:50 kakyo-laptop kernel: [   20.976914] ext3_orphan_cleanup: deleting unreferenced inode 1844454
Apr 19 15:16:50 kakyo-laptop kernel: [   20.976930] ext3_orphan_cleanup: deleting unreferenced inode 1844445
Apr 19 15:16:50 kakyo-laptop kernel: [   20.976946] ext3_orphan_cleanup: deleting unreferenced inode 1844441
Apr 19 15:16:50 kakyo-laptop kernel: [   20.976965] ext3_orphan_cleanup: deleting unreferenced inode 1844447
Apr 19 15:16:50 kakyo-laptop kernel: [   20.976980] ext3_orphan_cleanup: deleting unreferenced inode 1844437
Apr 19 15:16:50 kakyo-laptop kernel: [   20.976996] ext3_orphan_cleanup: deleting unreferenced inode 1844440
Apr 19 15:16:50 kakyo-laptop kernel: [   20.977037] ext3_orphan_cleanup: deleting unreferenced inode 1844446
Apr 19 15:16:50 kakyo-laptop kernel: [   20.977053] ext3_orphan_cleanup: deleting unreferenced inode 1844434
Apr 19 15:16:50 kakyo-laptop kernel: [   20.992578] ext3_orphan_cleanup: deleting unreferenced inode 7742269
Apr 19 15:16:50 kakyo-laptop kernel: [   21.007440] ext3_orphan_cleanup: deleting unreferenced inode 7742268
Apr 19 15:16:50 kakyo-laptop kernel: [   21.016218] ext3_orphan_cleanup: deleting unreferenced inode 7742263
Apr 19 15:16:50 kakyo-laptop kernel: [   21.027182] ext3_orphan_cleanup: deleting unreferenced inode 7726014
Apr 19 15:16:50 kakyo-laptop kernel: [   21.041608] ext3_orphan_cleanup: deleting unreferenced inode 7725336
Apr 19 15:16:50 kakyo-laptop kernel: [   21.057105] ext3_orphan_cleanup: deleting unreferenced inode 7717350
Apr 19 15:16:50 kakyo-laptop kernel: [   21.072991] ext3_orphan_cleanup: deleting unreferenced inode 9560121
Apr 19 15:16:50 kakyo-laptop kernel: [   21.117742] ext3_orphan_cleanup: deleting unreferenced inode 1892509
Apr 19 15:16:50 kakyo-laptop kernel: [   21.157085] ext3_orphan_cleanup: deleting unreferenced inode 7957286
Apr 19 15:16:50 kakyo-laptop kernel: [   21.186948] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[00241b00e96f1601]
Apr 19 15:16:50 kakyo-laptop kernel: [   21.333689] ext3_orphan_cleanup: deleting unreferenced inode 475177
Apr 19 15:16:50 kakyo-laptop kernel: [   21.333708] EXT3-fs: sda1: 35 orphan inodes deleted
Apr 19 15:16:50 kakyo-laptop kernel: [   21.333711] EXT3-fs: recovery complete.
Apr 19 15:16:50 kakyo-laptop kernel: [   21.352940] EXT3-fs: mounted filesystem with ordered data mode.
Apr 19 15:16:50 kakyo-laptop kernel: [   29.516450] Linux agpgart interface v0.102
Apr 19 15:16:50 kakyo-laptop kernel: [   29.709693] agpgart: Detected an Intel 965GM Chipset.
Apr 19 15:16:50 kakyo-laptop kernel: [   29.710562] agpgart: Detected 7676K stolen memory.
Apr 19 15:16:50 kakyo-laptop kernel: [   29.723329] agpgart: AGP aperture is 256M @ 0xd0000000
Apr 19 15:16:50 kakyo-laptop kernel: [   29.749321] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Apr 19 15:16:50 kakyo-laptop kernel: [   29.793345] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
Apr 19 15:16:50 kakyo-laptop kernel: [   29.963556] input: PC Speaker as /devices/platform/pcspkr/input/input3
Apr 19 15:16:50 kakyo-laptop kernel: [   30.002540] iTCO_vendor_support: vendor-support=0
Apr 19 15:16:50 kakyo-laptop kernel: [   30.017846] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.02 (26-Jul-2007)
Apr 19 15:16:50 kakyo-laptop kernel: [   30.102516] ACPI: AC Adapter [ACAD] (on-line)
Apr 19 15:16:50 kakyo-laptop kernel: [   30.102772] input: Power Button (FF) as /devices/virtual/input/input4
Apr 19 15:16:50 kakyo-laptop kernel: [   30.272470] iTCO_wdt: Found a ICH8M TCO device (Version=2, TCOBASE=0x1060)
Apr 19 15:16:50 kakyo-laptop kernel: [   30.272509] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
Apr 19 15:16:50 kakyo-laptop kernel: [   30.412325] ACPI: Power Button (FF) [PWRF]
Apr 19 15:16:50 kakyo-laptop kernel: [   30.412384] input: Power Button (CM) as /devices/virtual/input/input5
Apr 19 15:16:50 kakyo-laptop kernel: [   30.543869] ricoh-mmc: Ricoh MMC Controller disabling driver
Apr 19 15:16:50 kakyo-laptop kernel: [   30.543872] ricoh-mmc: Copyright(c) Philip Langdale
Apr 19 15:16:50 kakyo-laptop kernel: [   30.543910] ricoh-mmc: Ricoh MMC controller found at 0000:09:09.2 [1180:0843] (rev 12)
Apr 19 15:16:50 kakyo-laptop kernel: [   30.543921] ricoh-mmc: Controller is now disabled.
Apr 19 15:16:50 kakyo-laptop kernel: [   30.562250] ACPI: Power Button (CM) [PWRB]
Apr 19 15:16:50 kakyo-laptop kernel: [   30.562306] input: Sleep Button (CM) as /devices/virtual/input/input6
Apr 19 15:16:50 kakyo-laptop kernel: [   30.722178] ACPI: Sleep Button (CM) [SLPB]
Apr 19 15:16:50 kakyo-laptop kernel: [   30.722240] input: Lid Switch as /devices/virtual/input/input7
Apr 19 15:16:50 kakyo-laptop kernel: [   30.751550] sdhci: Secure Digital Host Controller Interface driver
Apr 19 15:16:50 kakyo-laptop kernel: [   30.751553] sdhci: Copyright(c) Pierre Ossman
Apr 19 15:16:50 kakyo-laptop kernel: [   30.751592] sdhci: SDHCI controller found at 0000:09:09.1 [1180:0822] (rev 22)
Apr 19 15:16:50 kakyo-laptop kernel: [   30.751613] ACPI: PCI Interrupt 0000:09:09.1[B] -> GSI 21 (level, low) -> IRQ 18
Apr 19 15:16:50 kakyo-laptop kernel: [   30.751629] sdhci:slot0: Will use DMA mode even though HW doesn't fully claim to support it.
Apr 19 15:16:50 kakyo-laptop kernel: [   30.751672] mmc0: SDHCI at 0xf8300800 irq 18 DMA
Apr 19 15:16:50 kakyo-laptop kernel: [   30.803395] ACPI: Lid Switch [LID]
Apr 19 15:16:50 kakyo-laptop kernel: [   30.803463] ACPI: WMI-Acer: Mapper loaded
Apr 19 15:16:50 kakyo-laptop kernel: [   30.909569] ACPI: Battery Slot [BAT0] (battery present)
Apr 19 15:16:50 kakyo-laptop kernel: [   30.935607] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:02/LNXVIDEO:00/input/input8
Apr 19 15:16:50 kakyo-laptop kernel: [   31.054556] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
Apr 19 15:16:50 kakyo-laptop kernel: [   31.064483] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/LNXVIDEO:01/input/input9
Apr 19 15:16:50 kakyo-laptop kernel: [   31.204500] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)
Apr 19 15:16:50 kakyo-laptop kernel: [   31.320317] Linux video capture interface: v2.00
Apr 19 15:16:50 kakyo-laptop kernel: [   31.369893] Synaptics Touchpad, model: 1, fw: 6.3, id: 0x1a0b1, caps: 0xa04711/0xa00000
Apr 19 15:16:50 kakyo-laptop kernel: [   31.390546] iwl4965: Intel(R) Wireless WiFi Link 4965AGN driver for Linux, 1.2.0
Apr 19 15:16:50 kakyo-laptop kernel: [   31.390550] iwl4965: Copyright(c) 2003-2007 Intel Corporation
Apr 19 15:16:50 kakyo-laptop kernel: [   31.390631] ACPI: PCI Interrupt 0000:02:00.0[A] -> GSI 16 (level, low) -> IRQ 17
Apr 19 15:16:50 kakyo-laptop kernel: [   31.390641] PCI: Setting latency timer of device 0000:02:00.0 to 64
Apr 19 15:16:50 kakyo-laptop kernel: [   31.390656] iwl4965: Detected Intel Wireless WiFi Link 4965AGN
Apr 19 15:16:50 kakyo-laptop kernel: [   31.475380] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input10
Apr 19 15:16:50 kakyo-laptop kernel: [   31.602910] iwl4965: Radio disabled by HW RF Kill switch
Apr 19 15:16:50 kakyo-laptop kernel: [   31.603170] uvcvideo: Found UVC 1.00 device HP Webcam (064e:a110)
Apr 19 15:16:50 kakyo-laptop kernel: [   31.604765] usbcore: registered new interface driver uvcvideo
Apr 19 15:16:50 kakyo-laptop kernel: [   31.604769] USB Video Class driver (v0.1.0)
Apr 19 15:16:50 kakyo-laptop kernel: [   31.873488] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 22 (level, low) -> IRQ 23
Apr 19 15:16:50 kakyo-laptop kernel: [   31.873512] PCI: Setting latency timer of device 0000:00:1b.0 to 64
Apr 19 15:16:50 kakyo-laptop kernel: [   32.257686] lp: driver loaded but no devices found
Apr 19 15:16:50 kakyo-laptop kernel: [   32.366697] Adding 4883752k swap on /dev/sda2.  Priority:-1 extents:1 across:4883752k
Apr 19 15:16:50 kakyo-laptop kernel: [   32.915212] EXT3 FS on sda1, internal journal
Apr 19 15:16:50 kakyo-laptop kernel: [   33.135073] device-mapper: uevent: version 1.0.3
Apr 19 15:16:50 kakyo-laptop kernel: [   33.135102] device-mapper: ioctl: 4.12.0-ioctl (2007-10-02) initialised: dm-devel@redhat.com
Apr 19 15:16:50 kakyo-laptop kernel: [   34.825872] ip_tables: (C) 2000-2006 Netfilter Core Team
Apr 19 15:16:50 kakyo-laptop kernel: [   35.356503] No dock devices found.
Apr 19 15:16:50 kakyo-laptop NetworkManager: <info>  starting... 
Apr 19 15:16:50 kakyo-laptop NetworkManager: <info>  New VPN service 'vpnc' (org.freedesktop.NetworkManager.vpnc). 
Apr 19 15:16:51 kakyo-laptop kernel: [   37.205910] NET: Registered protocol family 10
Apr 19 15:16:51 kakyo-laptop kernel: [   37.206117] lo: Disabled Privacy Extensions
Apr 19 15:16:51 kakyo-laptop avahi-daemon[5362]: Found user 'avahi' (UID 109) and group 'avahi' (GID 120).
Apr 19 15:16:51 kakyo-laptop avahi-daemon[5362]: Successfully dropped root privileges.
Apr 19 15:16:51 kakyo-laptop avahi-daemon[5362]: avahi-daemon 0.6.22 starting up.
Apr 19 15:16:51 kakyo-laptop avahi-daemon[5362]: Successfully called chroot().
Apr 19 15:16:51 kakyo-laptop avahi-daemon[5362]: Successfully dropped remaining capabilities.
Apr 19 15:16:51 kakyo-laptop avahi-daemon[5362]: No service file found in /etc/avahi/services.
Apr 19 15:16:51 kakyo-laptop avahi-daemon[5362]: Network interface enumeration completed.
Apr 19 15:16:51 kakyo-laptop avahi-daemon[5362]: Registering HINFO record with values 'I686'/'LINUX'.
Apr 19 15:16:51 kakyo-laptop avahi-daemon[5362]: Server startup complete. Host name is kakyo-laptop.local. Local service cookie is 3152649118.
Apr 19 15:16:51 kakyo-laptop kernel: [   37.481402] apm: BIOS not found.
Apr 19 15:16:51 kakyo-laptop kernel: [   37.710109] ppdev: user-space parallel port driver
Apr 19 15:16:51 kakyo-laptop kernel: [   37.921431] audit(1240168611.812:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=5405 profile="/usr/sbin/cupsd" namespace="default"
Apr 19 15:16:55 kakyo-laptop dhcdbd: Started up.
Apr 19 15:16:57 kakyo-laptop NetworkManager: <info>  Found radio killswitch /org/freedesktop/Hal/devices/iwl_wlan_switch 
Apr 19 15:16:57 kakyo-laptop kernel: [   42.427962] r8169: eth0: link up
Apr 19 15:16:57 kakyo-laptop kernel: [   42.427972] r8169: eth0: link up
Apr 19 15:16:57 kakyo-laptop NetworkManager: <info>  eth0: Device is fully-supported using driver 'r8169'. 
Apr 19 15:16:57 kakyo-laptop NetworkManager: <info>  nm_device_init(): waiting for device's worker thread to start 
Apr 19 15:16:57 kakyo-laptop NetworkManager: <info>  nm_device_init(): device's worker thread started, continuing. 
Apr 19 15:16:57 kakyo-laptop NetworkManager: <info>  Now managing wired Ethernet (802.3) device 'eth0'. 
Apr 19 15:16:57 kakyo-laptop NetworkManager: <info>  Deactivating device eth0. 
Apr 19 15:16:57 kakyo-laptop NetworkManager: <info>  Will activate wired connection 'eth0' because it now has a link. 
Apr 19 15:16:57 kakyo-laptop NetworkManager: <debug> [1240168617.209314] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/storage_model_DVD_RW_AD_7561A'). 
Apr 19 15:16:57 kakyo-laptop NetworkManager: <info>  SWITCH: no current connection, found better connection 'eth0'. 
Apr 19 15:16:57 kakyo-laptop hcid[5937]: Bluetooth HCI daemon
Apr 19 15:16:57 kakyo-laptop kernel: [   42.538819] Bluetooth: Core ver 2.11
Apr 19 15:16:57 kakyo-laptop kernel: [   42.538947] NET: Registered protocol family 31
Apr 19 15:16:57 kakyo-laptop kernel: [   42.538950] Bluetooth: HCI device and connection manager initialized
Apr 19 15:16:57 kakyo-laptop kernel: [   42.538956] Bluetooth: HCI socket layer initialized
Apr 19 15:16:57 kakyo-laptop hcid[5937]: Starting SDP server
Apr 19 15:16:57 kakyo-laptop kernel: [   42.571098] Bluetooth: L2CAP ver 2.9
Apr 19 15:16:57 kakyo-laptop kernel: [   42.571106] Bluetooth: L2CAP socket layer initialized
Apr 19 15:16:57 kakyo-laptop hcid[5937]: Created local server at unix:abstract=/var/run/dbus-mcgy7lCL3x,guid=d54f3503c1cea2727b37f4b649eb78a9
Apr 19 15:16:57 kakyo-laptop audio[5956]: Bluetooth Audio daemon
Apr 19 15:16:57 kakyo-laptop input[5958]: Bluetooth Input daemon
Apr 19 15:16:57 kakyo-laptop audio[5956]: Unix socket created: 5
Apr 19 15:16:57 kakyo-laptop audio[5956]: audio.conf: Key file does not have key 'Enable'
Apr 19 15:16:57 kakyo-laptop audio[5956]: audio.conf: Key file does not have key 'Disable'
Apr 19 15:16:57 kakyo-laptop input[5958]: Registered input manager path:/org/bluez/input
Apr 19 15:16:57 kakyo-laptop kernel: [   42.639458] Bluetooth: RFCOMM socket layer initialized
Apr 19 15:16:57 kakyo-laptop kernel: [   42.639475] Bluetooth: RFCOMM TTY layer initialized
Apr 19 15:16:57 kakyo-laptop kernel: [   42.639478] Bluetooth: RFCOMM ver 1.8
Apr 19 15:16:57 kakyo-laptop audio[5956]: add_service_record: got record id 0x10000
Apr 19 15:16:57 kakyo-laptop audio[5956]: audio.conf: Key file does not have key 'Disable'
Apr 19 15:16:57 kakyo-laptop audio[5956]: audio.conf: Key file does not have group 'A2DP'
Apr 19 15:16:57 kakyo-laptop last message repeated 3 times
Apr 19 15:16:57 kakyo-laptop audio[5956]: SEP 0x806d308 registered: type:0 codec:0 seid:1
Apr 19 15:16:57 kakyo-laptop audio[5956]: add_service_record: got record id 0x10001
Apr 19 15:16:57 kakyo-laptop audio[5956]: add_service_record: got record id 0x10002
Apr 19 15:16:57 kakyo-laptop audio[5956]: add_service_record: got record id 0x10003
Apr 19 15:16:57 kakyo-laptop audio[5956]: Registered manager path:/org/bluez/audio
Apr 19 15:16:58 kakyo-laptop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.reason
Apr 19 15:16:58 kakyo-laptop NetworkManager: <info>  Will activate connection 'eth0'. 
Apr 19 15:16:58 kakyo-laptop NetworkManager: <info>  Device eth0 activation scheduled... 
Apr 19 15:16:58 kakyo-laptop NetworkManager: <info>  Error getting killswitch power: org.freedesktop.Hal.Device.KillSwitch.NotSupported - hal-ipw-killswitch-linux returned 255 
Apr 19 15:16:58 kakyo-laptop NetworkManager: <info>  Wireless now enabled by radio killswitch 
Apr 19 15:16:58 kakyo-laptop NetworkManager: <debug> [1240168618.212402] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_bluetooth'). 
Apr 19 15:16:58 kakyo-laptop NetworkManager: <info>  Activation (eth0) started... 
Apr 19 15:16:58 kakyo-laptop NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) scheduled... 
Apr 19 15:16:58 kakyo-laptop NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) started... 
Apr 19 15:16:58 kakyo-laptop NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) scheduled... 
Apr 19 15:16:58 kakyo-laptop NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) complete. 
Apr 19 15:16:58 kakyo-laptop NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) starting... 
Apr 19 15:16:58 kakyo-laptop NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) successful. 
Apr 19 15:16:58 kakyo-laptop NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) scheduled. 
Apr 19 15:16:58 kakyo-laptop NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) complete. 
Apr 19 15:16:58 kakyo-laptop NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) started... 
Apr 19 15:16:59 kakyo-laptop NetworkManager: <info>  Activation (eth0) Beginning DHCP transaction. 
Apr 19 15:16:59 kakyo-laptop NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) complete. 
Apr 19 15:16:59 kakyo-laptop NetworkManager: <info>  DHCP daemon state is now 12 (successfully started) for interface eth0 
Apr 19 15:16:59 kakyo-laptop ntpd[6062]: ntpd 4.2.4p4@1.1520-o Tue Jan  6 15:51:34 UTC 2009 (1)
Apr 19 15:16:59 kakyo-laptop ntpd[6063]: precision = 1.000 usec
Apr 19 15:16:59 kakyo-laptop ntpd[6063]: Listening on interface #0 wildcard, 0.0.0.0#123 Disabled
Apr 19 15:16:59 kakyo-laptop ntpd[6063]: Listening on interface #1 wildcard, ::#123 Disabled
Apr 19 15:16:59 kakyo-laptop ntpd[6063]: Listening on interface #2 lo, ::1#123 Enabled
Apr 19 15:16:59 kakyo-laptop ntpd[6063]: Listening on interface #3 lo, 127.0.0.1#123 Enabled
Apr 19 15:16:59 kakyo-laptop ntpd[6063]: kernel time sync status 0040
Apr 19 15:17:00 kakyo-laptop anacron[6083]: Anacron 2.3 started on 2009-04-19
Apr 19 15:17:00 kakyo-laptop ntpd[6063]: frequency initialized -138.289 PPM from /var/lib/ntp/ntp.drift
Apr 19 15:17:00 kakyo-laptop anacron[6083]: Normal exit (0 jobs run)
Apr 19 15:17:00 kakyo-laptop /usr/sbin/cron[6111]: (CRON) INFO (pidfile fd = 3)
Apr 19 15:17:00 kakyo-laptop /usr/sbin/cron[6112]: (CRON) STARTUP (fork ok)
Apr 19 15:17:00 kakyo-laptop /usr/sbin/cron[6112]: (CRON) INFO (Running @reboot jobs)
Apr 19 15:17:00 kakyo-laptop NetworkManager: <info>  DHCP daemon state is now 1 (starting) for interface eth0 
Apr 19 15:17:00 kakyo-laptop kernel: [   44.253555] NET: Registered protocol family 17
Apr 19 15:17:01 kakyo-laptop kernel: [   44.831366] [drm] Initialized drm 1.1.0 20060810
Apr 19 15:17:01 kakyo-laptop kernel: [   44.840784] ACPI: PCI Interrupt 0000:00:02.0[A] -> GSI 16 (level, low) -> IRQ 17
Apr 19 15:17:01 kakyo-laptop kernel: [   44.840792] PCI: Setting latency timer of device 0000:00:02.0 to 64
Apr 19 15:17:01 kakyo-laptop kernel: [   44.840855] [drm] Initialized i915 1.6.0 20060119 on minor 0
Apr 19 15:17:01 kakyo-laptop NetworkManager: <debug> [1240168621.134242] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_2a02_drm_i915_card0'). 
Apr 19 15:17:01 kakyo-laptop kernel: [   44.857194] mtrr: type mismatch for d0000000,10000000 old: write-back new: write-combining
Apr 19 15:17:01 kakyo-laptop kernel: [   45.203689] /dev/vmmon[6183]: Module vmmon: registered with major=10 minor=165
Apr 19 15:17:01 kakyo-laptop kernel: [   45.203702] /dev/vmmon[6183]: Initial HV check: anyNotCapable=1 anyUnlocked=0 anyEnabled=0 anyDisabled=0
Apr 19 15:17:01 kakyo-laptop kernel: [   45.203704] /dev/vmmon[6183]: Module vmmon: initialized
Apr 19 15:17:01 kakyo-laptop kernel: [   45.252889] /dev/vmci[6195]: VMCI: Driver initialized.
Apr 19 15:17:01 kakyo-laptop kernel: [   45.252935] /dev/vmci[6195]: Module vmci: registered with major=10 minor=62
Apr 19 15:17:01 kakyo-laptop kernel: [   45.252937] /dev/vmci[6195]: Module vmci: initialized
Apr 19 15:17:01 kakyo-laptop kernel: [   45.271233] vsock: no version for "VMCIDatagram_Send" found: kernel tainted.
Apr 19 15:17:02 kakyo-laptop ntpd_initres[6090]: host name not found: ntp.ubuntu.com
Apr 19 15:17:02 kakyo-laptop ntpd_initres[6090]: couldn't resolve `ntp.ubuntu.com', giving up on it
Apr 19 15:17:03 kakyo-laptop dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
Apr 19 15:17:03 kakyo-laptop dhclient: DHCPOFFER of 132.206.5.148 from 132.206.5.129
Apr 19 15:17:03 kakyo-laptop dhclient: DHCPREQUEST of 132.206.5.148 on eth0 to 255.255.255.255 port 67
Apr 19 15:17:03 kakyo-laptop dhclient: DHCPACK of 132.206.5.148 from 132.206.5.129
Apr 19 15:17:03 kakyo-laptop avahi-daemon[5362]: Joining mDNS multicast group on interface eth0.IPv4 with address 132.206.5.148.
Apr 19 15:17:03 kakyo-laptop avahi-daemon[5362]: New relevant interface eth0.IPv4 for mDNS.
Apr 19 15:17:03 kakyo-laptop avahi-daemon[5362]: Registering new address record for 132.206.5.148 on eth0.IPv4.
Apr 19 15:17:03 kakyo-laptop avahi-daemon[5362]: Withdrawing address record for 132.206.5.148 on eth0.
Apr 19 15:17:03 kakyo-laptop avahi-daemon[5362]: Leaving mDNS multicast group on interface eth0.IPv4 with address 132.206.5.148.
Apr 19 15:17:03 kakyo-laptop avahi-daemon[5362]: Interface eth0.IPv4 no longer relevant for mDNS.
Apr 19 15:17:03 kakyo-laptop avahi-daemon[5362]: Joining mDNS multicast group on interface eth0.IPv4 with address 132.206.5.148.
Apr 19 15:17:03 kakyo-laptop avahi-daemon[5362]: New relevant interface eth0.IPv4 for mDNS.
Apr 19 15:17:03 kakyo-laptop avahi-daemon[5362]: Registering new address record for 132.206.5.148 on eth0.IPv4.
Apr 19 15:17:03 kakyo-laptop NetworkManager: <info>  DHCP daemon state is now 2 (bound) for interface eth0 
Apr 19 15:17:03 kakyo-laptop NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP Configure Get) scheduled... 
Apr 19 15:17:03 kakyo-laptop NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP Configure Get) started... 
Apr 19 15:17:03 kakyo-laptop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.host_name
Apr 19 15:17:03 kakyo-laptop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.domain_name
Apr 19 15:17:03 kakyo-laptop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.nis_domain
Apr 19 15:17:03 kakyo-laptop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.nis_servers
Apr 19 15:17:03 kakyo-laptop NetworkManager: <info>  Retrieved the following IP4 configuration from the DHCP daemon: 
Apr 19 15:17:03 kakyo-laptop NetworkManager: <info>    address 132.206.5.148 
Apr 19 15:17:03 kakyo-laptop NetworkManager: <info>    netmask 255.255.255.128 
Apr 19 15:17:03 kakyo-laptop NetworkManager: <info>    broadcast 132.206.5.255 
Apr 19 15:17:03 kakyo-laptop NetworkManager: <info>    gateway 132.206.5.129 
Apr 19 15:17:03 kakyo-laptop NetworkManager: <info>    nameserver 132.206.85.18 
Apr 19 15:17:03 kakyo-laptop NetworkManager: <info>    nameserver 132.206.85.19 
Apr 19 15:17:03 kakyo-laptop NetworkManager: <info>    nameserver 132.206.85.36 
Apr 19 15:17:03 kakyo-laptop NetworkManager: <info>    nameserver 132.206.44.21 
Apr 19 15:17:03 kakyo-laptop NetworkManager: <info>    nameserver 132.206.25.21 
Apr 19 15:17:03 kakyo-laptop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.interface_mtu
Apr 19 15:17:03 kakyo-laptop NetworkManager: <info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) scheduled... 
Apr 19 15:17:03 kakyo-laptop NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP Configure Get) complete. 
Apr 19 15:17:03 kakyo-laptop NetworkManager: <info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) started... 
Apr 19 15:17:03 kakyo-laptop dhclient: bound to 132.206.5.148 -- renewal in 102594 seconds.
Apr 19 15:17:03 kakyo-laptop avahi-daemon[5362]: Withdrawing address record for 132.206.5.148 on eth0.
Apr 19 15:17:03 kakyo-laptop avahi-daemon[5362]: Leaving mDNS multicast group on interface eth0.IPv4 with address 132.206.5.148.
Apr 19 15:17:03 kakyo-laptop avahi-daemon[5362]: Interface eth0.IPv4 no longer relevant for mDNS.
Apr 19 15:17:03 kakyo-laptop avahi-daemon[5362]: Joining mDNS multicast group on interface eth0.IPv4 with address 132.206.5.148.
Apr 19 15:17:03 kakyo-laptop avahi-daemon[5362]: New relevant interface eth0.IPv4 for mDNS.
Apr 19 15:17:03 kakyo-laptop avahi-daemon[5362]: Registering new address record for 132.206.5.148 on eth0.IPv4.
Apr 19 15:17:03 kakyo-laptop vmnetBridge: Daemon created. 
Apr 19 15:17:03 kakyo-laptop vmnetBridge: RTM_NEWLINK: name:eth0 index:2 flags:0x00011043 
Apr 19 15:17:03 kakyo-laptop vmnetBridge: Started bridge eth0 to virtual network 0. 
Apr 19 15:17:03 kakyo-laptop kernel: [   46.983091] /dev/vmnet: open called by PID 6273 (vmnet-bridge)
Apr 19 15:17:03 kakyo-laptop kernel: [   46.983100] /dev/vmnet: hub 0 does not exist, allocating memory.
Apr 19 15:17:03 kakyo-laptop kernel: [   46.983109] /dev/vmnet: port on hub 0 successfully opened
Apr 19 15:17:03 kakyo-laptop kernel: [   46.983121] bridge-eth0: up
Apr 19 15:17:03 kakyo-laptop kernel: [   46.983125] bridge-eth0: attached
Apr 19 15:17:03 kakyo-laptop kernel: [   47.061365] /dev/vmnet: open called by PID 6285 (vmnet-netifup)
Apr 19 15:17:03 kakyo-laptop kernel: [   47.061376] /dev/vmnet: hub 1 does not exist, allocating memory.
Apr 19 15:17:03 kakyo-laptop kernel: [   47.061388] /dev/vmnet: port on hub 1 successfully opened
Apr 19 15:17:03 kakyo-laptop avahi-daemon[5362]: Joining mDNS multicast group on interface vmnet1.IPv4 with address 192.168.176.1.
Apr 19 15:17:03 kakyo-laptop avahi-daemon[5362]: New relevant interface vmnet1.IPv4 for mDNS.
Apr 19 15:17:03 kakyo-laptop avahi-daemon[5362]: Registering new address record for 192.168.176.1 on vmnet1.IPv4.
Apr 19 15:17:03 kakyo-laptop vmnet-dhcpd: Internet Software Consortium DHCP Server 2.0
Apr 19 15:17:03 kakyo-laptop vmnet-dhcpd: Copyright 1995, 1996, 1997, 1998, 1999 The Internet Software Consortium.
Apr 19 15:17:03 kakyo-laptop vmnet-dhcpd: All rights reserved.
Apr 19 15:17:03 kakyo-laptop vmnet-dhcpd: 
Apr 19 15:17:03 kakyo-laptop vmnet-dhcpd: Please contribute if you find this software useful.
Apr 19 15:17:03 kakyo-laptop vmnet-dhcpd: For info, please visit http://www.isc.org/dhcp-contrib.html
Apr 19 15:17:03 kakyo-laptop vmnet-dhcpd: 
Apr 19 15:17:03 kakyo-laptop vmnet-dhcpd: Configured subnet: 192.168.176.0
Apr 19 15:17:03 kakyo-laptop vmnet-dhcpd: Setting vmnet-dhcp IP address: 192.168.176.254
Apr 19 15:17:03 kakyo-laptop vmnet-dhcpd: Recving on     VNet/vmnet1/192.168.176.0
Apr 19 15:17:03 kakyo-laptop vmnet-dhcpd: Sending on     VNet/vmnet1/192.168.176.0
Apr 19 15:17:03 kakyo-laptop kernel: [   47.197428] /dev/vmnet: open called by PID 6284 (vmnet-dhcpd)
Apr 19 15:17:03 kakyo-laptop kernel: [   47.197441] /dev/vmnet: port on hub 1 successfully opened
Apr 19 15:17:03 kakyo-laptop vmnetBridge: Daemon created. 
Apr 19 15:17:03 kakyo-laptop kernel: [   47.212527] /dev/vmnet: open called by PID 6317 (vmnet-netifup)
Apr 19 15:17:03 kakyo-laptop kernel: [   47.212542] /dev/vmnet: hub 8 does not exist, allocating memory.
Apr 19 15:17:03 kakyo-laptop kernel: [   47.212561] /dev/vmnet: port on hub 8 successfully opened
Apr 19 15:17:03 kakyo-laptop vmnet-dhcpd: Internet Software Consortium DHCP Server 2.0
Apr 19 15:17:03 kakyo-laptop vmnet-dhcpd: Copyright 1995, 1996, 1997, 1998, 1999 The Internet Software Consortium.
Apr 19 15:17:03 kakyo-laptop vmnet-dhcpd: All rights reserved.
Apr 19 15:17:03 kakyo-laptop vmnet-dhcpd: 
Apr 19 15:17:03 kakyo-laptop vmnet-dhcpd: Please contribute if you find this software useful.
Apr 19 15:17:03 kakyo-laptop vmnet-dhcpd: For info, please visit http://www.isc.org/dhcp-contrib.html
Apr 19 15:17:03 kakyo-laptop vmnet-dhcpd: 
Apr 19 15:17:03 kakyo-laptop avahi-daemon[5362]: Joining mDNS multicast group on interface vmnet8.IPv4 with address 172.16.161.1.
Apr 19 15:17:03 kakyo-laptop avahi-daemon[5362]: New relevant interface vmnet8.IPv4 for mDNS.
Apr 19 15:17:03 kakyo-laptop avahi-daemon[5362]: Registering new address record for 172.16.161.1 on vmnet8.IPv4.
Apr 19 15:17:03 kakyo-laptop avahi-daemon[5362]: Withdrawing address record for 172.16.161.1 on vmnet8.
Apr 19 15:17:03 kakyo-laptop avahi-daemon[5362]: Leaving mDNS multicast group on interface vmnet8.IPv4 with address 172.16.161.1.
Apr 19 15:17:03 kakyo-laptop avahi-daemon[5362]: Interface vmnet8.IPv4 no longer relevant for mDNS.
Apr 19 15:17:03 kakyo-laptop avahi-daemon[5362]: Joining mDNS multicast group on interface vmnet8.IPv4 with address 172.16.161.1.
Apr 19 15:17:03 kakyo-laptop avahi-daemon[5362]: New relevant interface vmnet8.IPv4 for mDNS.
Apr 19 15:17:03 kakyo-laptop avahi-daemon[5362]: Registering new address record for 172.16.161.1 on vmnet8.IPv4.
Apr 19 15:17:04 kakyo-laptop vmnet-dhcpd: Configured subnet: 172.16.161.0
Apr 19 15:17:04 kakyo-laptop vmnet-dhcpd: Setting vmnet-dhcp IP address: 172.16.161.254
Apr 19 15:17:04 kakyo-laptop vmnet-dhcpd: Recving on     VNet/vmnet8/172.16.161.0
Apr 19 15:17:04 kakyo-laptop vmnet-dhcpd: Sending on     VNet/vmnet8/172.16.161.0
Apr 19 15:17:04 kakyo-laptop kernel: [   47.251932] /dev/vmnet: open called by PID 6320 (vmnet-dhcpd)
Apr 19 15:17:04 kakyo-laptop kernel: [   47.251955] /dev/vmnet: port on hub 8 successfully opened
Apr 19 15:17:04 kakyo-laptop kernel: [   47.287840] /dev/vmnet: open called by PID 6335 (vmnet-natd)
Apr 19 15:17:04 kakyo-laptop kernel: [   47.287861] /dev/vmnet: port on hub 8 successfully opened
Apr 19 15:17:04 kakyo-laptop NetworkManager: <info>  Clearing nscd hosts cache. 
Apr 19 15:17:04 kakyo-laptop NetworkManager: <WARN>  nm_spawn_process(): nm_spawn_process('/usr/sbin/nscd -i hosts'): could not spawn process. (Failed to execute child process "/usr/sbin/nscd" (No such file or directory))  
Apr 19 15:17:04 kakyo-laptop NetworkManager: <info>  Activation (eth0) successful, device activated. 
Apr 19 15:17:04 kakyo-laptop NetworkManager: <info>  Activation (eth0) Finish handler scheduled. 
Apr 19 15:17:04 kakyo-laptop NetworkManager: <info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) complete. 
Apr 19 15:17:04 kakyo-laptop ntpd[6063]: ntpd exiting on signal 15
Apr 19 15:17:04 kakyo-laptop watchdog-webAccess: [6672] Begin '/usr/lib/vmware/webAccess/java/jre1.5.0_15/bin/webAccess -client -Xmx64m -XX:MinHeapFreeRatio=30 -XX:MaxHeapFreeRatio=30 -Djava.util.logging.manager=org.apache.juli.ClassLoaderLogManager -Djava.endorsed.dirs=/usr/lib/vmware/webAccess/tomcat/apache-tomcat-6.0.16/common/endorsed -classpath /usr/lib/vmware/webAccess/tomcat/apache-tomcat-6.0.16/bin/bootstrap.jar:/usr/lib/vmware/webAccess/tomcat/apache-tomcat-6.0.16/bin/commons-logging-api.jar -Dcatalina.base=/usr/lib/vmware/webAccess/tomcat/apache-tomcat-6.0.16 -Dcatalina.home=/usr/lib/vmware/webAccess/tomcat/apache-tomcat-6.0.16 -Djava.io.tmpdir=/usr/lib/vmware/webAccess/tomcat/apache-tomcat-6.0.16/temp org.apache.catalina.startup.Bootstrap start', min-uptime = 30, max-quick-failures = 5, max-total-failures = 1000000
Apr 19 15:17:04 kakyo-laptop watchdog-webAccess: Executing '/usr/lib/vmware/webAccess/java/jre1.5.0_15/bin/webAccess -client -Xmx64m -XX:MinHeapFreeRatio=30 -XX:MaxHeapFreeRatio=30 -Djava.util.logging.manager=org.apache.juli.ClassLoaderLogManager -Djava.endorsed.dirs=/usr/lib/vmware/webAccess/tomcat/apache-tomcat-6.0.16/common/endorsed -classpath /usr/lib/vmware/webAccess/tomcat/apache-tomcat-6.0.16/bin/bootstrap.jar:/usr/lib/vmware/webAccess/tomcat/apache-tomcat-6.0.16/bin/commons-logging-api.jar -Dcatalina.base=/usr/lib/vmware/webAccess/tomcat/apache-tomcat-6.0.16 -Dcatalina.home=/usr/lib/vmware/webAccess/tomcat/apache-tomcat-6.0.16 -Djava.io.tmpdir=/usr/lib/vmware/webAccess/tomcat/apache-tomcat-6.0.16/temp org.apache.catalina.startup.Bootstrap start'
Apr 19 15:17:04 kakyo-laptop ntpdate[6656]: step time server 91.189.94.4 offset 2.951669 sec
Apr 19 15:17:08 kakyo-laptop avahi-daemon[5362]: Registering new address record for fe80::250:56ff:fec0:1 on vmnet1.*.
Apr 19 15:17:08 kakyo-laptop ntpd[6722]: ntpd 4.2.4p4@1.1520-o Tue Jan  6 15:51:34 UTC 2009 (1)
Apr 19 15:17:08 kakyo-laptop ntpd[6723]: precision = 1.000 usec
Apr 19 15:17:08 kakyo-laptop ntpd[6723]: Listening on interface #0 wildcard, 0.0.0.0#123 Disabled
Apr 19 15:17:08 kakyo-laptop ntpd[6723]: Listening on interface #1 wildcard, ::#123 Disabled
Apr 19 15:17:08 kakyo-laptop ntpd[6723]: bind() fd 18, family 10, port 123, scope 4, addr fe80::250:56ff:fec0:8, in6_is_addr_multicast=0 flags=0x11 fails: Cannot assign requested address
Apr 19 15:17:08 kakyo-laptop ntpd[6723]: unable to create socket on vmnet8 (2) for fe80::250:56ff:fec0:8#123
Apr 19 15:17:08 kakyo-laptop ntpd[6723]: failed to initialize interface for address fe80::250:56ff:fec0:8
Apr 19 15:17:08 kakyo-laptop ntpd[6723]: Listening on interface #3 lo, ::1#123 Enabled
Apr 19 15:17:08 kakyo-laptop ntpd[6723]: Listening on interface #4 vmnet1, fe80::250:56ff:fec0:1#123 Enabled
Apr 19 15:17:08 kakyo-laptop ntpd[6723]: bind() fd 20, family 10, port 123, scope 2, addr fe80::21e:68ff:fe99:1b73, in6_is_addr_multicast=0 flags=0x11 fails: Cannot assign requested address
Apr 19 15:17:08 kakyo-laptop ntpd[6723]: unable to create socket on eth0 (5) for fe80::21e:68ff:fe99:1b73#123
Apr 19 15:17:08 kakyo-laptop ntpd[6723]: failed to initialize interface for address fe80::21e:68ff:fe99:1b73
Apr 19 15:17:08 kakyo-laptop ntpd[6723]: Listening on interface #6 lo, 127.0.0.1#123 Enabled
Apr 19 15:17:08 kakyo-laptop ntpd[6723]: Listening on interface #7 eth0, 132.206.5.148#123 Enabled
Apr 19 15:17:08 kakyo-laptop ntpd[6723]: Listening on interface #8 vmnet1, 192.168.176.1#123 Enabled
Apr 19 15:17:08 kakyo-laptop ntpd[6723]: Listening on interface #9 vmnet8, 172.16.161.1#123 Enabled
Apr 19 15:17:08 kakyo-laptop ntpd[6723]: kernel time sync status 0040
Apr 19 15:17:08 kakyo-laptop ntpd[6723]: frequency initialized -138.289 PPM from /var/lib/ntp/ntp.drift
Apr 19 15:17:08 kakyo-laptop avahi-daemon[5362]: Registering new address record for fe80::250:56ff:fec0:8 on vmnet8.*.
Apr 19 15:17:08 kakyo-laptop kernel: [   48.648251] /dev/vmmon[0]: HostIF_ReadUptime: detected settimeofday: fixed uptimeBase old 18445503905088057342 new 18445503905085105656 attempts 1
Apr 19 15:17:08 kakyo-laptop avahi-daemon[5362]: Registering new address record for fe80::21e:68ff:fe99:1b73 on eth0.*.
Apr 19 15:17:09 kakyo-laptop ntpd[6723]: Listening on interface #10 vmnet8, fe80::250:56ff:fec0:8#123 Enabled
Apr 19 15:17:09 kakyo-laptop ntpd[6723]: Listening on interface #11 eth0, fe80::21e:68ff:fe99:1b73#123 Enabled
Apr 19 15:17:17 kakyo-laptop kernel: [   53.505622] vmnet1: no IPv6 routers present
Apr 19 15:17:17 kakyo-laptop kernel: [   53.651797] vmnet8: no IPv6 routers present
Apr 19 15:17:17 kakyo-laptop kernel: [   53.796233] eth0: no IPv6 routers present
Apr 19 15:17:18 kakyo-laptop anacron[6958]: Anacron 2.3 started on 2009-04-19
Apr 19 15:17:18 kakyo-laptop anacron[6958]: Normal exit (0 jobs run)
Apr 19 15:17:32 kakyo-laptop pulseaudio[7115]: main.c: setrlimit(RLIMIT_NICE, (31, 31)) failed: Operation not permitted
Apr 19 15:17:32 kakyo-laptop pulseaudio[7115]: main.c: setrlimit(RLIMIT_RTPRIO, (9, 9)) failed: Operation not permitted
Apr 19 15:17:42 kakyo-laptop hcid[5937]: Default passkey agent (:1.29, /org/bluez/passkey) registered
Apr 19 15:17:42 kakyo-laptop hcid[5937]: Default authorization agent (:1.29, /org/bluez/auth) registered
Apr 19 15:18:21 kakyo-laptop NetworkManager: <info>  Updating allowed wireless network lists. 
Apr 19 15:18:22 kakyo-laptop NetworkManager: <info>  Updating VPN Connections... 
Apr 19 15:18:23 kakyo-laptop anacron[7422]: Anacron 2.3 started on 2009-04-19
Apr 19 15:18:23 kakyo-laptop anacron[7422]: Normal exit (0 jobs run)
Apr 19 15:18:23 kakyo-laptop kernel: [   88.179590] CPU0 attaching NULL sched-domain.
Apr 19 15:18:23 kakyo-laptop kernel: [   88.179596] CPU1 attaching NULL sched-domain.
Apr 19 15:18:24 kakyo-laptop kernel: [   88.235194] CPU0 attaching sched-domain:
Apr 19 15:18:24 kakyo-laptop kernel: [   88.235199]  domain 0: span 03
Apr 19 15:18:24 kakyo-laptop kernel: [   88.235200]   groups: 01 02
Apr 19 15:18:24 kakyo-laptop kernel: [   88.235203] CPU1 attaching sched-domain:
Apr 19 15:18:24 kakyo-laptop kernel: [   88.235205]  domain 0: span 03
Apr 19 15:18:24 kakyo-laptop kernel: [   88.235206]   groups: 02 01
Apr 19 15:18:24 kakyo-laptop anacron[7472]: Anacron 2.3 started on 2009-04-19
Apr 19 15:18:24 kakyo-laptop anacron[7472]: Normal exit (0 jobs run)
Apr 19 15:18:24 kakyo-laptop kernel: [   88.388569] CPU0 attaching NULL sched-domain.
Apr 19 15:18:24 kakyo-laptop kernel: [   88.388578] CPU1 attaching NULL sched-domain.
Apr 19 15:18:24 kakyo-laptop kernel: [   88.431060] CPU0 attaching sched-domain:
Apr 19 15:18:24 kakyo-laptop kernel: [   88.431068]  domain 0: span 03
Apr 19 15:18:24 kakyo-laptop kernel: [   88.431071]   groups: 01 02
Apr 19 15:18:24 kakyo-laptop kernel: [   88.431077] CPU1 attaching sched-domain:
Apr 19 15:18:24 kakyo-laptop kernel: [   88.431080]  domain 0: span 03
Apr 19 15:18:24 kakyo-laptop kernel: [   88.431083]   groups: 02 01
Apr 19 15:18:29 kakyo-laptop gnome-power-manager: (kakyo) Power Manager is already running in this session.
Apr 19 15:18:48 kakyo-laptop scim-bridge: Failed to open the panel socket
Apr 19 15:18:50 kakyo-laptop last message repeated 2 times
Apr 19 15:19:21 kakyo-laptop kernel: [  139.870945] dropbox[7246]: segfault at 0004af9e eip 0004af9e esp bf86ac1c error 14
Apr 19 15:21:22 kakyo-laptop ntpd[6723]: synchronized to 91.189.94.4, stratum 2
Apr 19 15:21:22 kakyo-laptop ntpd[6723]: kernel time sync status change 0001
Apr 19 15:36:52 kakyo-laptop -- MARK --
Apr 19 15:56:52 kakyo-laptop -- MARK --
Apr 19 16:16:52 kakyo-laptop -- MARK --
Apr 19 16:17:01 kakyo-laptop /USR/SBIN/CRON[10771]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Apr 19 16:36:52 kakyo-laptop -- MARK --
Apr 19 16:56:52 kakyo-laptop -- MARK --
Apr 19 17:16:52 kakyo-laptop -- MARK --
Apr 19 17:17:01 kakyo-laptop /USR/SBIN/CRON[13447]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Apr 19 17:36:52 kakyo-laptop -- MARK --
Apr 19 17:56:52 kakyo-laptop -- MARK --
Apr 19 18:16:52 kakyo-laptop -- MARK --
Apr 19 18:17:01 kakyo-laptop /USR/SBIN/CRON[16536]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Apr 19 18:36:52 kakyo-laptop -- MARK --
Apr 19 18:56:52 kakyo-laptop -- MARK --
Apr 19 19:00:51 kakyo-laptop gnome-power-manager: (kakyo) Suspending computer. Reason: The suspend button has been pressed.
Apr 19 19:00:55 kakyo-laptop NetworkManager: <info>  Going to sleep. 
Apr 19 19:00:55 kakyo-laptop dhclient: There is already a pid file /var/run/dhclient.eth0.pid with pid 6039
Apr 19 19:00:55 kakyo-laptop dhclient: killed old client process, removed PID file
Apr 19 19:00:55 kakyo-laptop vmnetBridge: RTM_NEWLINK: name:eth0 index:2 flags:0x00001002 
Apr 19 19:00:55 kakyo-laptop kernel: [ 9201.547374] bridge-eth0: disabling the bridge
Apr 19 19:00:55 kakyo-laptop avahi-daemon[5362]: Interface eth0.IPv4 no longer relevant for mDNS.
Apr 19 19:00:55 kakyo-laptop avahi-daemon[5362]: Leaving mDNS multicast group on interface eth0.IPv4 with address 132.206.5.148.
Apr 19 19:00:55 kakyo-laptop kernel: [ 9201.613470] bridge-eth0: down
Apr 19 19:00:55 kakyo-laptop vmnetBridge: Stopped bridge eth0 to virtual network 0. 
Apr 19 19:00:55 kakyo-laptop kernel: [ 9201.614327] bridge-eth0: detached
Apr 19 19:00:55 kakyo-laptop avahi-daemon[5362]: Withdrawing address record for fe80::21e:68ff:fe99:1b73 on eth0.
Apr 19 19:00:55 kakyo-laptop avahi-daemon[5362]: Withdrawing address record for 132.206.5.148 on eth0.
Apr 19 19:00:56 kakyo-laptop dhclient: DHCPRELEASE on eth0 to 132.216.130.2 port 67
Apr 19 19:00:56 kakyo-laptop dhclient: send_packet: Network is unreachable
Apr 19 19:00:56 kakyo-laptop dhclient: send_packet: please consult README file regarding broadcast address.
Apr 19 19:00:56 kakyo-laptop vmnetBridge: RTM_DELLINK: name:eth0 index:2 flags:0x00001002 
Apr 19 19:00:56 kakyo-laptop vmnetBridge: Can't remove interface eth0 2 (does not exist). 
Apr 19 19:00:56 kakyo-laptop NetworkManager: <debug> [1240182056.533213] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/net_00_1e_68_99_1b_73'). 
Apr 19 19:00:56 kakyo-laptop NetworkManager: <info>  Deactivating device eth0. 
Apr 19 19:00:56 kakyo-laptop kernel: [ 9202.335772] ACPI: PCI interrupt for device 0000:08:00.0 disabled
Apr 19 19:37:39 kakyo-laptop syslogd 1.5.0#1ubuntu1: restart.
Apr 19 19:37:39 kakyo-laptop kernel: Inspecting /boot/System.map-2.6.24-23-server
Apr 19 19:37:40 kakyo-laptop kernel: Loaded 28765 symbols from /boot/System.map-2.6.24-23-server.
Apr 19 19:37:40 kakyo-laptop kernel: Symbols match kernel version 2.6.24.
Apr 19 19:37:40 kakyo-laptop kernel: Loaded 19362 symbols from 95 modules.
Apr 19 19:37:40 kakyo-laptop kernel: [    0.000000] Initializing cgroup subsys cpuset
Apr 19 19:37:40 kakyo-laptop kernel: [    0.000000] Initializing cgroup subsys cpu
Apr 19 19:37:40 kakyo-laptop kernel: [    0.000000] Linux version 2.6.24-23-server (buildd@palmer) (gcc version 4.2.4 (Ubuntu 4.2.4-1ubuntu3)) #1 SMP Wed Apr 1 22:22:14 UTC 2009 (Ubuntu 2.6.24-23.52-server)
Apr 19 19:37:40 kakyo-laptop kernel: [    0.000000] BIOS-provided physical RAM map:
Apr 19 19:37:40 kakyo-laptop kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
Apr 19 19:37:40 kakyo-laptop kernel: [    0.000000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
Apr 19 19:37:40 kakyo-laptop kernel: [    0.000000]  BIOS-e820: 00000000000dc000 - 0000000000100000 (reserved)
Apr 19 19:37:40 kakyo-laptop kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 00000000bf6d0000 (usable)
Apr 19 19:37:40 kakyo-laptop kernel: [    0.000000]  BIOS-e820: 00000000bf6d0000 - 00000000bf6e3000 (ACPI NVS)
Apr 19 19:37:40 kakyo-laptop kernel: [    0.000000]  BIOS-e820: 00000000bf6e3000 - 00000000c0000000 (reserved)
Apr 19 19:37:40 kakyo-laptop kernel: [    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
Apr 19 19:37:40 kakyo-laptop kernel: [    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
Apr 19 19:37:40 kakyo-laptop kernel: [    0.000000]  BIOS-e820: 00000000fed00000 - 00000000fed00400 (reserved)
Apr 19 19:37:40 kakyo-laptop kernel: [    0.000000]  BIOS-e820: 00000000fed14000 - 00000000fed1a000 (reserved)
Apr 19 19:37:40 kakyo-laptop kernel: [    0.000000]  BIOS-e820: 00000000fed1c000 - 00000000fed90000 (reserved)
Apr 19 19:37:40 kakyo-laptop kernel: [    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
Apr 19 19:37:40 kakyo-laptop kernel: [    0.000000]  BIOS-e820: 00000000ff000000 - 0000000100000000 (reserved)
Apr 19 19:37:40 kakyo-laptop kernel: [    0.000000]  BIOS-e820: 0000000100000000 - 0000000140000000 (usable)
Apr 19 19:37:40 kakyo-laptop kernel: [    0.000000] 4224MB HIGHMEM available.
Apr 19 19:37:40 kakyo-laptop kernel: [    0.000000] 896MB LOWMEM available.
Apr 19 19:37:40 kakyo-laptop kernel: [    0.000000] found SMP MP-table at 000f8520
Apr 19 19:37:40 kakyo-laptop kernel: [    0.000000] NX (Execute Disable) protection: active
Apr 19 19:37:40 kakyo-laptop kernel: [    0.000000] Entering add_active_range(0, 0, 1310720) 0 entries of 256 used
Apr 19 19:37:40 kakyo-laptop kernel: [    0.000000] Zone PFN ranges:
Apr 19 19:37:40 kakyo-laptop kernel: [    0.000000]   DMA             0 ->     4096
Apr 19 19:37:40 kakyo-laptop kernel: [    0.000000]   Normal       4096 ->   229376
Apr 19 19:37:40 kakyo-laptop kernel: [    0.000000]   HighMem    229376 ->  1310720
Apr 19 19:37:40 kakyo-laptop kernel: [    0.000000] Movable zone start PFN for each node
Apr 19 19:37:40 kakyo-laptop kernel: [    0.000000] early_node_map[1] active PFN ranges
Apr 19 19:37:40 kakyo-laptop kernel: [    0.000000]     0:        0 ->  1310720
Apr 19 19:37:40 kakyo-laptop kernel: [    0.000000] On node 0 totalpages: 1310720
Apr 19 19:37:40 kakyo-laptop kernel: [    0.000000]   DMA zone: 32 pages used for memmap
Apr 19 19:37:40 kakyo-laptop kernel: [    0.000000]   DMA zone: 0 pages reserved
Apr 19 19:37:40 kakyo-laptop kernel: [    0.000000]   DMA zone: 4064 pages, LIFO batch:0
Apr 19 19:37:40 kakyo-laptop kernel: [    0.000000]   Normal zone: 1760 pages used for memmap
Apr 19 19:37:40 kakyo-laptop kernel: [    0.000000]   Normal zone: 223520 pages, LIFO batch:31
Apr 19 19:37:40 kakyo-laptop kernel: [    0.000000]   HighMem zone: 8448 pages used for memmap
Apr 19 19:37:40 kakyo-laptop kernel: [    0.000000]   HighMem zone: 1072896 pages, LIFO batch:31
Apr 19 19:37:40 kakyo-laptop kernel: [    0.000000]   Movable zone: 0 pages used for memmap
Apr 19 19:37:40 kakyo-laptop kernel: [    0.000000] DMI present.
Apr 19 19:37:40 kakyo-laptop kernel: [    0.000000] ACPI: RSDP signature @ 0xC00F8480 checksum 0
Apr 19 19:37:40 kakyo-laptop kernel: [    0.000000] ACPI: RSDP 000F8480, 0024 (r2 HP    )
Apr 19 19:37:40 kakyo-laptop kernel: [    0.000000] ACPI: XSDT BF6D5AEB, 0084 (r1 HPQOEM SLIC-MPC  6040000  LTP        0)
Apr 19 19:37:40 kakyo-laptop kernel: [    0.000000] ACPI: FACP BF6DFC6C, 00F4 (r3 HP     30CC      6040000 ALAN        1)
Apr 19 19:37:40 kakyo-laptop kernel: [    0.000000] ACPI: DSDT BF6D703C, 8BBC (r1 HP     30CC      6040000 INTL 20061109)
Apr 19 19:37:40 kakyo-laptop kernel: [    0.000000] ACPI: FACS BF6E2FC0, 0040
Apr 19 19:37:40 kakyo-laptop kernel: [    0.000000] ACPI: HPET BF6DFD60, 0038 (r1 HP     30CC      6040000 LOHR       5A)
Apr 19 19:37:40 kakyo-laptop kernel: [    0.000000] ACPI: MCFG BF6DFD98, 003C (r1 HP     30CC      6040000 LOHR       5A)
Apr 19 19:37:40 kakyo-laptop kernel: [    0.000000] ACPI: TMOR BF6DFDD4, 0026 (r1 HP     30CC      6040000 PTL         3)
Apr 19 19:37:40 kakyo-laptop kernel: [    0.000000] ACPI: APIC BF6DFDFA, 0068 (r1 HP     30CC      6040000  LTP        0)
Apr 19 19:37:40 kakyo-laptop kernel: [    0.000000] ACPI: BOOT BF6DFE62, 0028 (r1 HP     30CC      6040000  LTP        1)
Apr 19 19:37:40 kakyo-laptop kernel: [    0.000000] ACPI: SLIC BF6DFE8A, 0176 (r1 HPQOEM SLIC-MPC  6040000  LTP        1)
Apr 19 19:37:40 kakyo-laptop kernel: [    0.000000] ACPI: SSDT BF6D6D5F, 02DD (r1 HP     30CC         1000 INTL 20061109)
Apr 19 19:37:40 kakyo-laptop kernel: [    0.000000] ACPI: SSDT BF6D6CB7, 00A8 (r1 HP     30CC         1000 INTL 20061109)
Apr 19 19:37:40 kakyo-laptop kernel: [    0.000000] ACPI: SSDT BF6D60FB, 025F (r1  HP    30CC         3000 INTL 20061109)
Apr 19 19:37:40 kakyo-laptop kernel: [    0.000000] ACPI: SSDT BF6D6055, 00A6 (r1  HP    30CC         3000 INTL 20061109)
Apr 19 19:37:40 kakyo-laptop kernel: [    0.000000] ACPI: SSDT BF6D5B6F, 04E6 (r1  HP     30CC        3000 INTL 20061109)
Apr 19 19:37:40 kakyo-laptop kernel: [    0.000000] ACPI: DMI detected: Hewlett-Packard
Apr 19 19:37:40 kakyo-laptop kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x1008
Apr 19 19:37:40 kakyo-laptop kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Apr 19 19:37:40 kakyo-laptop kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
Apr 19 19:37:40 kakyo-laptop kernel: [    0.000000] Processor #0 6:15 APIC version 20
Apr 19 19:37:40 kakyo-laptop kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
Apr 19 19:37:40 kakyo-laptop kernel: [    0.000000] Processor #1 6:15 APIC version 20
Apr 19 19:37:40 kakyo-laptop kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
Apr 19 19:37:40 kakyo-laptop kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
Apr 19 19:37:40 kakyo-laptop kernel: [    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
Apr 19 19:37:40 kakyo-laptop kernel: [    0.000000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
Apr 19 19:37:40 kakyo-laptop kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 high edge)
Apr 19 19:37:40 kakyo-laptop kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
Apr 19 19:37:40 kakyo-laptop kernel: [    0.000000] ACPI: IRQ0 used by override.
Apr 19 19:37:40 kakyo-laptop kernel: [    0.000000] ACPI: IRQ2 used by override.
Apr 19 19:37:40 kakyo-laptop kernel: [    0.000000] ACPI: IRQ9 used by override.
Apr 19 19:37:40 kakyo-laptop kernel: [    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
Apr 19 19:37:40 kakyo-laptop kernel: [    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
Apr 19 19:37:40 kakyo-laptop kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
Apr 19 19:37:40 kakyo-laptop kernel: [    0.000000] Allocating PCI resources starting at c2000000 (gap: c0000000:20000000)
Apr 19 19:37:40 kakyo-laptop kernel: [    0.000000] swsusp: Registered nosave memory region: 000000000009f000 - 00000000000a0000
Apr 19 19:37:40 kakyo-laptop kernel: [    0.000000] swsusp: Registered nosave memory region: 00000000000a0000 - 00000000000dc000
Apr 19 19:37:40 kakyo-laptop kernel: [    0.000000] swsusp: Registered nosave memory region: 00000000000dc000 - 0000000000100000
Apr 19 19:37:40 kakyo-laptop kernel: [    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 1300480
Apr 19 19:37:40 kakyo-laptop kernel: [    0.000000] Kernel command line: root=UUID=96bbbef5-3316-44cc-b0a2-7f489b657f17 ro quiet splash
Apr 19 19:37:40 kakyo-laptop kernel: [    0.000000] mapped APIC to ffffb000 (fee00000)
Apr 19 19:37:40 kakyo-laptop kernel: [    0.000000] mapped IOAPIC to ffffa000 (fec00000)
Apr 19 19:37:40 kakyo-laptop kernel: [    0.000000] Enabling fast FPU save and restore... done.
Apr 19 19:37:40 kakyo-laptop kernel: [    0.000000] Enabling unmasked SIMD FPU exception support... done.
Apr 19 19:37:40 kakyo-laptop kernel: [    0.000000] Initializing CPU#0
Apr 19 19:37:40 kakyo-laptop kernel: [    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
Apr 19 19:37:40 kakyo-laptop kernel: [    0.000000] Detected 1995.308 MHz processor.
Apr 19 19:37:40 kakyo-laptop kernel: [   14.669684] Console: colour VGA+ 80x25
Apr 19 19:37:40 kakyo-laptop kernel: [   14.669687] console [tty0] enabled
Apr 19 19:37:40 kakyo-laptop kernel: [   14.669975] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
Apr 19 19:37:40 kakyo-laptop kernel: [   14.670255] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
Apr 19 19:37:40 kakyo-laptop kernel: [   14.918828] Memory: 4129608k/5242880k available (2258k kernel code, 53908k reserved, 1037k data, 384k init, 3267392k highmem)
Apr 19 19:37:40 kakyo-laptop kernel: [   14.918835] virtual kernel memory layout:
Apr 19 19:37:40 kakyo-laptop kernel: [   14.918836]     fixmap  : 0xfff4c000 - 0xfffff000   ( 716 kB)
Apr 19 19:37:40 kakyo-laptop kernel: [   14.918837]     pkmap   : 0xffc00000 - 0xffe00000   (2048 kB)
Apr 19 19:37:40 kakyo-laptop kernel: [   14.918838]     vmalloc : 0xf8800000 - 0xffbfe000   ( 115 MB)
Apr 19 19:37:40 kakyo-laptop kernel: [   14.918839]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
Apr 19 19:37:40 kakyo-laptop kernel: [   14.918840]       .init : 0xc043e000 - 0xc049e000   ( 384 kB)
Apr 19 19:37:40 kakyo-laptop kernel: [   14.918840]       .data : 0xc0334a39 - 0xc0437fe4   (1037 kB)
Apr 19 19:37:40 kakyo-laptop kernel: [   14.918841]       .text : 0xc0100000 - 0xc0334a39   (2258 kB)
Apr 19 19:37:40 kakyo-laptop kernel: [   14.918844] Checking if this processor honours the WP bit even in supervisor mode... Ok.
Apr 19 19:37:40 kakyo-laptop kernel: [   14.918885] SLUB: Genslabs=11, HWalign=64, Order=0-1, MinObjects=4, CPUs=2, Nodes=1
Apr 19 19:37:40 kakyo-laptop kernel: [   14.919015] hpet clockevent registered
Apr 19 19:37:40 kakyo-laptop kernel: [   15.068954] Calibrating delay using timer specific routine.. 3993.81 BogoMIPS (lpj=19969087)
Apr 19 19:37:40 kakyo-laptop kernel: [   15.068975] Security Framework initialized
Apr 19 19:37:40 kakyo-laptop kernel: [   15.068981] SELinux:  Disabled at boot.
Apr 19 19:37:40 kakyo-laptop kernel: [   15.068993] AppArmor: AppArmor initialized
Apr 19 19:37:40 kakyo-laptop kernel: [   15.068997] Failure registering capabilities with primary security module.
Apr 19 19:37:40 kakyo-laptop kernel: [   15.069005] Mount-cache hash table entries: 512
Apr 19 19:37:40 kakyo-laptop kernel: [   15.069114] Initializing cgroup subsys ns
Apr 19 19:37:40 kakyo-laptop kernel: [   15.069119] Initializing cgroup subsys cpuacct
Apr 19 19:37:40 kakyo-laptop kernel: [   15.069128] CPU: After generic identify, caps: bfebfbff 20100000 00000000 00000000 0000e39d 00000000 00000001 00000000
Apr 19 19:37:40 kakyo-laptop kernel: [   15.069135] monitor/mwait feature present.
Apr 19 19:37:40 kakyo-laptop kernel: [   15.069136] using mwait in idle threads.
Apr 19 19:37:40 kakyo-laptop kernel: [   15.069140] CPU: L1 I cache: 32K, L1 D cache: 32K
Apr 19 19:37:40 kakyo-laptop kernel: [   15.069142] CPU: L2 cache: 2048K
Apr 19 19:37:40 kakyo-laptop kernel: [   15.069144] CPU: Physical Processor ID: 0
Apr 19 19:37:40 kakyo-laptop kernel: [   15.069145] CPU: Processor Core ID: 0
Apr 19 19:37:40 kakyo-laptop kernel: [   15.069147] CPU: After all inits, caps: bfebfbff 20100000 00000000 00043940 0000e39d 00000000 00000001 00000000
Apr 19 19:37:40 kakyo-laptop kernel: [   15.069155] Compat vDSO mapped to ffffe000.
Apr 19 19:37:40 kakyo-laptop kernel: [   15.069167] Checking 'hlt' instruction... OK.
Apr 19 19:37:40 kakyo-laptop kernel: [   15.109297] SMP alternatives: switching to UP code
Apr 19 19:37:40 kakyo-laptop kernel: [   15.110662] Early unpacking initramfs... done
Apr 19 19:37:40 kakyo-laptop kernel: [   15.414653] ACPI: Core revision 20070126
Apr 19 19:37:40 kakyo-laptop kernel: [   15.414701] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
Apr 19 19:37:40 kakyo-laptop kernel: [   15.485430] CPU0: Intel(R) Core(TM)2 Duo CPU     T5750  @ 2.00GHz stepping 0d
Apr 19 19:37:40 kakyo-laptop kernel: [   15.485444] SMP alternatives: switching to SMP code
Apr 19 19:37:40 kakyo-laptop kernel: [   15.486074] Booting processor 1/1 eip 3000
Apr 19 19:37:40 kakyo-laptop kernel: [   15.496339] Initializing CPU#1
Apr 19 19:37:40 kakyo-laptop kernel: [   15.638696] Calibrating delay using timer specific routine.. 3990.28 BogoMIPS (lpj=19951418)
Apr 19 19:37:40 kakyo-laptop kernel: [   15.638702] CPU: After generic identify, caps: bfebfbff 20100000 00000000 00000000 0000e39d 00000000 00000001 00000000
Apr 19 19:37:40 kakyo-laptop kernel: [   15.638706] monitor/mwait feature present.
Apr 19 19:37:40 kakyo-laptop kernel: [   15.638708] CPU: L1 I cache: 32K, L1 D cache: 32K
Apr 19 19:37:40 kakyo-laptop kernel: [   15.638710] CPU: L2 cache: 2048K
Apr 19 19:37:40 kakyo-laptop kernel: [   15.638712] CPU: Physical Processor ID: 0
Apr 19 19:37:40 kakyo-laptop kernel: [   15.638713] CPU: Processor Core ID: 1
Apr 19 19:37:40 kakyo-laptop kernel: [   15.638714] CPU: After all inits, caps: bfebfbff 20100000 00000000 00043940 0000e39d 00000000 00000001 00000000
Apr 19 19:37:40 kakyo-laptop kernel: [   15.639172] CPU1: Intel(R) Core(TM)2 Duo CPU     T5750  @ 2.00GHz stepping 0d
Apr 19 19:37:40 kakyo-laptop kernel: [   15.639193] Total of 2 processors activated (7984.10 BogoMIPS).
Apr 19 19:37:40 kakyo-laptop kernel: [   15.639370] ENABLING IO-APIC IRQs
Apr 19 19:37:40 kakyo-laptop kernel: [   15.639558] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
Apr 19 19:37:40 kakyo-laptop kernel: [   15.858696] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
Apr 19 19:37:40 kakyo-laptop kernel: [   15.878699] Brought up 2 CPUs
Apr 19 19:37:40 kakyo-laptop kernel: [   15.878717] CPU0 attaching sched-domain:
Apr 19 19:37:40 kakyo-laptop kernel: [   15.878719]  domain 0: span 03
Apr 19 19:37:40 kakyo-laptop kernel: [   15.878720]   groups: 01 02
Apr 19 19:37:40 kakyo-laptop kernel: [   15.878723] CPU1 attaching sched-domain:
Apr 19 19:37:40 kakyo-laptop kernel: [   15.878724]  domain 0: span 03
Apr 19 19:37:40 kakyo-laptop kernel: [   15.878726]   groups: 02 01
Apr 19 19:37:40 kakyo-laptop kernel: [   15.878910] net_namespace: 64 bytes
Apr 19 19:37:40 kakyo-laptop kernel: [   15.878920] Booting paravirtualized kernel on bare hardware
Apr 19 19:37:40 kakyo-laptop kernel: [   15.879330] Time: 23:37:17  Date: 04/19/09
Apr 19 19:37:40 kakyo-laptop kernel: [   15.879354] NET: Registered protocol family 16
Apr 19 19:37:40 kakyo-laptop kernel: [   15.879510] EISA bus registered
Apr 19 19:37:40 kakyo-laptop kernel: [   15.879514] ACPI: bus type pci registered
Apr 19 19:37:40 kakyo-laptop kernel: [   15.879900] PCI: PCI BIOS revision 3.00 entry at 0xfde31, last bus=9
Apr 19 19:37:40 kakyo-laptop kernel: [   15.879902] PCI: Using configuration type 1
Apr 19 19:37:40 kakyo-laptop kernel: [   15.879915] Setting up standard PCI resources
Apr 19 19:37:40 kakyo-laptop kernel: [   15.882069] ACPI: EC: Look up EC in DSDT
Apr 19 19:37:40 kakyo-laptop kernel: [   15.884076] ACPI: BIOS _OSI(Linux) query ignored via DMI
Apr 19 19:37:40 kakyo-laptop kernel: [   15.885091] ACPI: Interpreter enabled
Apr 19 19:37:40 kakyo-laptop kernel: [   15.885094] ACPI: (supports S0 S3 S4 S5)
Apr 19 19:37:40 kakyo-laptop kernel: [   15.885106] ACPI: Using IOAPIC for interrupt routing
Apr 19 19:37:40 kakyo-laptop kernel: [   15.886388] ACPI: EC: non-query interrupt received, switching to interrupt mode
Apr 19 19:37:40 kakyo-laptop kernel: [   15.894608] ACPI: EC: GPE = 0x17, I/O: command/status = 0x66, data = 0x62
Apr 19 19:37:40 kakyo-laptop kernel: [   15.894610] ACPI: EC: driver started in interrupt mode
Apr 19 19:37:40 kakyo-laptop kernel: [   15.894647] ACPI: PCI Root Bridge [PCI0] (0000:00)
Apr 19 19:37:40 kakyo-laptop kernel: [   15.895658] PCI quirk: region 1000-107f claimed by ICH6 ACPI/GPIO/TCO
Apr 19 19:37:40 kakyo-laptop kernel: [   15.895663] PCI quirk: region 1180-11bf claimed by ICH6 GPIO
Apr 19 19:37:40 kakyo-laptop kernel: [   15.896897] PCI: Transparent bridge - 0000:00:1e.0
Apr 19 19:37:40 kakyo-laptop kernel: [   15.896943] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
Apr 19 19:37:40 kakyo-laptop kernel: [   15.897210] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP01._PRT]
Apr 19 19:37:40 kakyo-laptop kernel: [   15.897326] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP02._PRT]
Apr 19 19:37:40 kakyo-laptop kernel: [   15.897439] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP06._PRT]
Apr 19 19:37:40 kakyo-laptop kernel: [   15.897564] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIB._PRT]
Apr 19 19:37:40 kakyo-laptop kernel: [   15.906722] ACPI: PCI Interrupt Link [LNKA] (IRQs 1 3 4 *5 6 7 10 12 14 15)
Apr 19 19:37:40 kakyo-laptop kernel: [   15.906816] ACPI: PCI Interrupt Link [LNKB] (IRQs 1 3 4 5 6 7 11 12 14 15) *10
Apr 19 19:37:40 kakyo-laptop kernel: [   15.906908] ACPI: PCI Interrupt Link [LNKC] (IRQs 1 3 4 5 6 *7 10 12 14 15)
Apr 19 19:37:40 kakyo-laptop kernel: [   15.907000] ACPI: PCI Interrupt Link [LNKD] (IRQs 1 3 4 5 6 7 11 12 14 15) *10
Apr 19 19:37:40 kakyo-laptop kernel: [   15.907094] ACPI: PCI Interrupt Link [LNKE] (IRQs 1 3 4 5 6 7 10 12 14 15) *11
Apr 19 19:37:40 kakyo-laptop kernel: [   15.907185] ACPI: PCI Interrupt Link [LNKF] (IRQs 1 3 4 5 6 7 *11 12 14 15)
Apr 19 19:37:40 kakyo-laptop kernel: [   15.907276] ACPI: PCI Interrupt Link [LNKG] (IRQs 1 3 4 5 6 7 10 12 14 15) *11
Apr 19 19:37:40 kakyo-laptop kernel: [   15.907367] ACPI: PCI Interrupt Link [LNKH] (IRQs 1 3 4 5 6 7 11 12 14 15) *10
Apr 19 19:37:40 kakyo-laptop kernel: [   15.907493] Linux Plug and Play Support v0.97 (c) Adam Belay
Apr 19 19:37:40 kakyo-laptop kernel: [   15.907517] pnp: PnP ACPI init
Apr 19 19:37:40 kakyo-laptop kernel: [   15.907523] ACPI: bus type pnp registered
Apr 19 19:37:40 kakyo-laptop kernel: [   15.910981] pnp: PnP ACPI: found 11 devices
Apr 19 19:37:40 kakyo-laptop kernel: [   15.910983] ACPI: ACPI bus type pnp unregistered
Apr 19 19:37:40 kakyo-laptop kernel: [   15.910986] PnPBIOS: Disabled by ACPI PNP
Apr 19 19:37:40 kakyo-laptop kernel: [   15.911165] PCI: Using ACPI for IRQ routing
Apr 19 19:37:40 kakyo-laptop kernel: [   15.911167] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
Apr 19 19:37:40 kakyo-laptop kernel: [   16.048623] NET: Registered protocol family 8
Apr 19 19:37:40 kakyo-laptop kernel: [   16.048625] NET: Registered protocol family 20
Apr 19 19:37:40 kakyo-laptop kernel: [   16.048647] NetLabel: Initializing
Apr 19 19:37:40 kakyo-laptop kernel: [   16.048648] NetLabel:  domain hash size = 128
Apr 19 19:37:40 kakyo-laptop kernel: [   16.048649] NetLabel:  protocols = UNLABELED CIPSOv4
Apr 19 19:37:40 kakyo-laptop kernel: [   16.048659] NetLabel:  unlabeled traffic allowed by default
Apr 19 19:37:40 kakyo-laptop kernel: [   16.048665] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
Apr 19 19:37:40 kakyo-laptop kernel: [   16.048669] hpet0: 3 64-bit timers, 14318180 Hz
Apr 19 19:37:40 kakyo-laptop kernel: [   16.049697] AppArmor: AppArmor Filesystem Enabled
Apr 19 19:37:40 kakyo-laptop kernel: [   16.058514] Time: tsc clocksource has been installed.
Apr 19 19:37:40 kakyo-laptop kernel: [   16.058526] Switched to high resolution mode on CPU 0
Apr 19 19:37:40 kakyo-laptop kernel: [   16.058613] Switched to high resolution mode on CPU 1
Apr 19 19:37:40 kakyo-laptop kernel: [   16.091024] system 00:01: iomem range 0xfed1c000-0xfed1ffff could not be reserved
Apr 19 19:37:40 kakyo-laptop kernel: [   16.091027] system 00:01: iomem range 0xfed14000-0xfed17fff could not be reserved
Apr 19 19:37:40 kakyo-laptop kernel: [   16.091030] system 00:01: iomem range 0xfed18000-0xfed18fff could not be reserved
Apr 19 19:37:40 kakyo-laptop kernel: [   16.091032] system 00:01: iomem range 0xfed19000-0xfed19fff could not be reserved
Apr 19 19:37:40 kakyo-laptop kernel: [   16.091034] system 00:01: iomem range 0xe0000000-0xefffffff could not be reserved
Apr 19 19:37:40 kakyo-laptop kernel: [   16.091037] system 00:01: iomem range 0xfed20000-0xfed3ffff could not be reserved
Apr 19 19:37:40 kakyo-laptop kernel: [   16.091039] system 00:01: iomem range 0xfed40000-0xfed44fff could not be reserved
Apr 19 19:37:40 kakyo-laptop kernel: [   16.091042] system 00:01: iomem range 0xfed45000-0xfed8ffff could not be reserved
Apr 19 19:37:40 kakyo-laptop kernel: [   16.091048] system 00:04: iomem range 0xfed00000-0xfed003ff could not be reserved
Apr 19 19:37:40 kakyo-laptop kernel: [   16.091054] system 00:06: ioport range 0x380-0x383 has been reserved
Apr 19 19:37:40 kakyo-laptop kernel: [   16.091056] system 00:06: ioport range 0x680-0x69f has been reserved
Apr 19 19:37:40 kakyo-laptop kernel: [   16.091058] system 00:06: ioport range 0x800-0x80f has been reserved
Apr 19 19:37:40 kakyo-laptop kernel: [   16.091060] system 00:06: ioport range 0x1000-0x107f has been reserved
Apr 19 19:37:40 kakyo-laptop kernel: [   16.091062] system 00:06: ioport range 0x1180-0x11bf has been reserved
Apr 19 19:37:40 kakyo-laptop kernel: [   16.091064] system 00:06: ioport range 0x1640-0x164f has been reserved
Apr 19 19:37:40 kakyo-laptop kernel: [   16.091067] system 00:06: ioport range 0xfe00-0xfe00 has been reserved
Apr 19 19:37:40 kakyo-laptop kernel: [   16.091071] system 00:07: ioport range 0x6a0-0x6af has been reserved
Apr 19 19:37:40 kakyo-laptop kernel: [   16.091074] system 00:07: ioport range 0x6b0-0x6ff has been reserved
Apr 19 19:37:40 kakyo-laptop kernel: [   16.121405] PCI: Bridge: 0000:00:1c.0
Apr 19 19:37:40 kakyo-laptop kernel: [   16.121409]   IO window: 4000-7fff
Apr 19 19:37:40 kakyo-laptop kernel: [   16.121414]   MEM window: f4000000-f5ffffff
Apr 19 19:37:40 kakyo-laptop kernel: [   16.121419]   PREFETCH window: f0000000-f1ffffff
Apr 19 19:37:40 kakyo-laptop kernel: [   16.121425] PCI: Bridge: 0000:00:1c.1
Apr 19 19:37:40 kakyo-laptop kernel: [   16.121428]   IO window: 8000-bfff
Apr 19 19:37:40 kakyo-laptop kernel: [   16.121434]   MEM window: f6000000-f7ffffff
Apr 19 19:37:40 kakyo-laptop kernel: [   16.121438]   PREFETCH window: f2000000-f3ffffff
Apr 19 19:37:40 kakyo-laptop kernel: [   16.121444] PCI: Bridge: 0000:00:1c.5
Apr 19 19:37:40 kakyo-laptop kernel: [   16.121447]   IO window: c000-cfff
Apr 19 19:37:40 kakyo-laptop kernel: [   16.121452]   MEM window: f8200000-f82fffff
Apr 19 19:37:40 kakyo-laptop kernel: [   16.121456]   PREFETCH window: c2000000-c20fffff
Apr 19 19:37:40 kakyo-laptop kernel: [   16.121463] PCI: Bridge: 0000:00:1e.0
Apr 19 19:37:40 kakyo-laptop kernel: [   16.121464]   IO window: disabled.
Apr 19 19:37:40 kakyo-laptop kernel: [   16.121470]   MEM window: f8300000-f83fffff
Apr 19 19:37:40 kakyo-laptop kernel: [   16.121474]   PREFETCH window: disabled.
Apr 19 19:37:40 kakyo-laptop kernel: [   16.121506] ACPI: PCI Interrupt 0000:00:1c.0[A] -> GSI 17 (level, low) -> IRQ 16
Apr 19 19:37:40 kakyo-laptop kernel: [   16.121512] PCI: Setting latency timer of device 0000:00:1c.0 to 64
Apr 19 19:37:40 kakyo-laptop kernel: [   16.121537] ACPI: PCI Interrupt 0000:00:1c.1[B] -> GSI 16 (level, low) -> IRQ 17
Apr 19 19:37:40 kakyo-laptop kernel: [   16.121542] PCI: Setting latency timer of device 0000:00:1c.1 to 64
Apr 19 19:37:40 kakyo-laptop kernel: [   16.121567] ACPI: PCI Interrupt 0000:00:1c.5[B] -> GSI 16 (level, low) -> IRQ 17
Apr 19 19:37:40 kakyo-laptop kernel: [   16.121572] PCI: Setting latency timer of device 0000:00:1c.5 to 64
Apr 19 19:37:40 kakyo-laptop kernel: [   16.121587] PCI: Setting latency timer of device 0000:00:1e.0 to 64
Apr 19 19:37:40 kakyo-laptop kernel: [   16.121596] NET: Registered protocol family 2
Apr 19 19:37:40 kakyo-laptop kernel: [   16.220993] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
Apr 19 19:37:40 kakyo-laptop kernel: [   16.221190] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
Apr 19 19:37:40 kakyo-laptop kernel: [   16.221576] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
Apr 19 19:37:40 kakyo-laptop kernel: [   16.221777] TCP: Hash tables configured (established 131072 bind 65536)
Apr 19 19:37:40 kakyo-laptop kernel: [   16.221779] TCP reno registered
Apr 19 19:37:40 kakyo-laptop kernel: [   16.251042] checking if image is initramfs... it is
Apr 19 19:37:40 kakyo-laptop kernel: [   16.847251] Freeing initrd memory: 7759k freed
Apr 19 19:37:40 kakyo-laptop kernel: [   16.847391] Simple Boot Flag at 0x35 set to 0x1
Apr 19 19:37:40 kakyo-laptop kernel: [   16.847914] audit: initializing netlink socket (disabled)
Apr 19 19:37:40 kakyo-laptop kernel: [   16.847926] audit(1240184237.680:1): initialized
Apr 19 19:37:40 kakyo-laptop kernel: [   16.848319] highmem bounce pool size: 64 pages
Apr 19 19:37:40 kakyo-laptop kernel: [   16.848322] Total HugeTLB memory allocated, 0
Apr 19 19:37:40 kakyo-laptop kernel: [   16.849969] VFS: Disk quotas dquot_6.5.1
Apr 19 19:37:40 kakyo-laptop kernel: [   16.850034] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
Apr 19 19:37:40 kakyo-laptop kernel: [   16.850205] io scheduler noop registered
Apr 19 19:37:40 kakyo-laptop kernel: [   16.850207] io scheduler anticipatory registered
Apr 19 19:37:40 kakyo-laptop kernel: [   16.850209] io scheduler deadline registered (default)
Apr 19 19:37:40 kakyo-laptop kernel: [   16.850220] io scheduler cfq registered
Apr 19 19:37:40 kakyo-laptop kernel: [   16.850230] Boot video device is 0000:00:02.0
Apr 19 19:37:40 kakyo-laptop kernel: [   16.850447] PCI: Setting latency timer of device 0000:00:1c.0 to 64
Apr 19 19:37:40 kakyo-laptop kernel: [   16.850509] assign_interrupt_mode Found MSI capability
Apr 19 19:37:40 kakyo-laptop kernel: [   16.850561] Allocate Port Service[0000:00:1c.0:pcie00]
Apr 19 19:37:40 kakyo-laptop kernel: [   16.850591] Allocate Port Service[0000:00:1c.0:pcie02]
Apr 19 19:37:40 kakyo-laptop kernel: [   16.850700] PCI: Setting latency timer of device 0000:00:1c.1 to 64
Apr 19 19:37:40 kakyo-laptop kernel: [   16.850761] assign_interrupt_mode Found MSI capability
Apr 19 19:37:40 kakyo-laptop kernel: [   16.850809] Allocate Port Service[0000:00:1c.1:pcie00]
Apr 19 19:37:40 kakyo-laptop kernel: [   16.850837] Allocate Port Service[0000:00:1c.1:pcie02]
Apr 19 19:37:40 kakyo-laptop kernel: [   16.850938] PCI: Setting latency timer of device 0000:00:1c.5 to 64
Apr 19 19:37:40 kakyo-laptop kernel: [   16.850999] assign_interrupt_mode Found MSI capability
Apr 19 19:37:40 kakyo-laptop kernel: [   16.851047] Allocate Port Service[0000:00:1c.5:pcie00]
Apr 19 19:37:40 kakyo-laptop kernel: [   16.851072] Allocate Port Service[0000:00:1c.5:pcie02]
Apr 19 19:37:40 kakyo-laptop kernel: [   16.851298] isapnp: Scanning for PnP cards...
Apr 19 19:37:40 kakyo-laptop kernel: [   17.208433] isapnp: No Plug & Play device found
Apr 19 19:37:40 kakyo-laptop kernel: [   17.228480] Real Time Clock Driver v1.12ac
Apr 19 19:37:40 kakyo-laptop kernel: [   17.228683] hpet_resources: 0xfed00000 is busy
Apr 19 19:37:40 kakyo-laptop kernel: [   17.228709] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
Apr 19 19:37:40 kakyo-laptop kernel: [   17.229727] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
Apr 19 19:37:40 kakyo-laptop kernel: [   17.229786] input: Macintosh mouse button emulation as /devices/virtual/input/input0
Apr 19 19:37:40 kakyo-laptop kernel: [   17.229867] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
Apr 19 19:37:40 kakyo-laptop kernel: [   17.271250] serio: i8042 KBD port at 0x60,0x64 irq 1
Apr 19 19:37:40 kakyo-laptop kernel: [   17.271254] serio: i8042 AUX port at 0x60,0x64 irq 12
Apr 19 19:37:40 kakyo-laptop kernel: [   17.308064] mice: PS/2 mouse device common for all mice
Apr 19 19:37:40 kakyo-laptop kernel: [   17.308161] EISA: Probing bus 0 at eisa.0
Apr 19 19:37:40 kakyo-laptop kernel: [   17.308168] Cannot allocate resource for EISA slot 1
Apr 19 19:37:40 kakyo-laptop kernel: [   17.308180] Cannot allocate resource for EISA slot 4
Apr 19 19:37:40 kakyo-laptop kernel: [   17.308182] Cannot allocate resource for EISA slot 5
Apr 19 19:37:40 kakyo-laptop kernel: [   17.308184] Cannot allocate resource for EISA slot 6
Apr 19 19:37:40 kakyo-laptop kernel: [   17.308185] Cannot allocate resource for EISA slot 7
Apr 19 19:37:40 kakyo-laptop kernel: [   17.308187] Cannot allocate resource for EISA slot 8
Apr 19 19:37:40 kakyo-laptop kernel: [   17.308189] EISA: Detected 0 cards.
Apr 19 19:37:40 kakyo-laptop kernel: [   17.308191] cpuidle: using governor ladder
Apr 19 19:37:40 kakyo-laptop kernel: [   17.308193] cpuidle: using governor menu
Apr 19 19:37:40 kakyo-laptop kernel: [   17.308269] NET: Registered protocol family 1
Apr 19 19:37:40 kakyo-laptop kernel: [   17.308294] Using IPI No-Shortcut mode
Apr 19 19:37:40 kakyo-laptop kernel: [   17.308324] registered taskstats version 1
Apr 19 19:37:40 kakyo-laptop kernel: [   17.308435]   Magic number: 5:437:656
Apr 19 19:37:40 kakyo-laptop kernel: [   17.308503] BIOS EDD facility v0.16 2004-Jun-25, 6 devices found
Apr 19 19:37:40 kakyo-laptop kernel: [   17.308845] Freeing unused kernel memory: 384k freed
Apr 19 19:37:40 kakyo-laptop kernel: [   17.308884] Write protecting the kernel read-only data: 828k
Apr 19 19:37:40 kakyo-laptop kernel: [   17.337691] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
Apr 19 19:37:40 kakyo-laptop kernel: [   18.502380] fuse init (API version 7.9)
Apr 19 19:37:40 kakyo-laptop kernel: [   18.519533] ACPI: SSDT BF6D69B7, 0238 (r1  HP    30CC         3000 INTL 20061109)
Apr 19 19:37:40 kakyo-laptop kernel: [   18.519737] ACPI: SSDT BF6D635A, 05D8 (r1  HP    30CC         3001 INTL 20061109)
Apr 19 19:37:40 kakyo-laptop kernel: [   18.521380] Monitor-Mwait will be used to enter C-1 state
Apr 19 19:37:40 kakyo-laptop kernel: [   18.521383] Monitor-Mwait will be used to enter C-2 state
Apr 19 19:37:40 kakyo-laptop kernel: [   18.521385] Monitor-Mwait will be used to enter C-3 state
Apr 19 19:37:40 kakyo-laptop kernel: [   18.521486] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
Apr 19 19:37:40 kakyo-laptop kernel: [   18.521490] ACPI: Processor [CPU0] (supports 8 throttling states)
Apr 19 19:37:40 kakyo-laptop kernel: [   18.521691] ACPI: SSDT BF6D6BEF, 00C8 (r1  HP    30CC         3000 INTL 20061109)
Apr 19 19:37:40 kakyo-laptop kernel: [   18.521880] ACPI: SSDT BF6D6932, 0085 (r1  HP    30CC         3000 INTL 20061109)
Apr 19 19:37:40 kakyo-laptop kernel: [   18.522709] Marking TSC unstable due to: TSC halts in idle.
Apr 19 19:37:40 kakyo-laptop kernel: [   18.522758] ACPI: CPU1 (power states: C1[C1] C2[C2] C3[C3])
Apr 19 19:37:40 kakyo-laptop kernel: [   18.522763] ACPI: Processor [CPU1] (supports 8 throttling states)
Apr 19 19:37:40 kakyo-laptop kernel: [   18.524486] ACPI Exception (thermal-0339): AE_BAD_DATA, No critical threshold [20070126]
Apr 19 19:37:40 kakyo-laptop kernel: [   18.527501] Time: hpet clocksource has been installed.
Apr 19 19:37:40 kakyo-laptop kernel: [   18.778300] usbcore: registered new interface driver usbfs
Apr 19 19:37:40 kakyo-laptop kernel: [   18.778322] usbcore: registered new interface driver hub
Apr 19 19:37:40 kakyo-laptop kernel: [   18.785322] usbcore: registered new device driver usb
Apr 19 19:37:40 kakyo-laptop kernel: [   18.787420] ACPI: PCI Interrupt 0000:00:1a.7[C] -> GSI 18 (level, low) -> IRQ 18
Apr 19 19:37:40 kakyo-laptop kernel: [   18.787433] PCI: Setting latency timer of device 0000:00:1a.7 to 64
Apr 19 19:37:40 kakyo-laptop kernel: [   18.787437] ehci_hcd 0000:00:1a.7: EHCI Host Controller
Apr 19 19:37:40 kakyo-laptop kernel: [   18.787653] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 1
Apr 19 19:37:40 kakyo-laptop kernel: [   18.791580] ehci_hcd 0000:00:1a.7: debug port 1
Apr 19 19:37:40 kakyo-laptop kernel: [   18.791588] PCI: cache line size of 32 is not supported by device 0000:00:1a.7
Apr 19 19:37:40 kakyo-laptop kernel: [   18.791597] ehci_hcd 0000:00:1a.7: irq 18, io mem 0xf8604800
Apr 19 19:37:40 kakyo-laptop kernel: [   18.797574] USB Universal Host Controller Interface driver v3.0
Apr 19 19:37:40 kakyo-laptop kernel: [   18.809907] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
Apr 19 19:37:40 kakyo-laptop kernel: [   18.810020] usb usb1: configuration #1 chosen from 1 choice
Apr 19 19:37:40 kakyo-laptop kernel: [   18.810045] hub 1-0:1.0: USB hub found
Apr 19 19:37:40 kakyo-laptop kernel: [   18.810051] hub 1-0:1.0: 4 ports detected
Apr 19 19:37:40 kakyo-laptop kernel: [   18.857773] SCSI subsystem initialized
Apr 19 19:37:40 kakyo-laptop kernel: [   18.878668] libata version 3.00 loaded.
Apr 19 19:37:40 kakyo-laptop kernel: [   18.919929] ACPI: PCI Interrupt 0000:00:1a.0[A] -> GSI 16 (level, low) -> IRQ 17
Apr 19 19:37:40 kakyo-laptop kernel: [   18.919942] PCI: Setting latency timer of device 0000:00:1a.0 to 64
Apr 19 19:37:40 kakyo-laptop kernel: [   18.919946] uhci_hcd 0000:00:1a.0: UHCI Host Controller
Apr 19 19:37:40 kakyo-laptop kernel: [   18.919973] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 2
Apr 19 19:37:40 kakyo-laptop kernel: [   18.920006] uhci_hcd 0000:00:1a.0: irq 17, io base 0x00001820
Apr 19 19:37:40 kakyo-laptop kernel: [   18.920105] usb usb2: configuration #1 chosen from 1 choice
Apr 19 19:37:40 kakyo-laptop kernel: [   18.920124] hub 2-0:1.0: USB hub found
Apr 19 19:37:40 kakyo-laptop kernel: [   18.920129] hub 2-0:1.0: 2 ports detected
Apr 19 19:37:40 kakyo-laptop kernel: [   19.027408] ACPI: PCI Interrupt 0000:00:1a.1[B] -> GSI 21 (level, low) -> IRQ 19
Apr 19 19:37:40 kakyo-laptop kernel: [   19.027420] PCI: Setting latency timer of device 0000:00:1a.1 to 64
Apr 19 19:37:40 kakyo-laptop kernel: [   19.027424] uhci_hcd 0000:00:1a.1: UHCI Host Controller
Apr 19 19:37:40 kakyo-laptop kernel: [   19.027444] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 3
Apr 19 19:37:40 kakyo-laptop kernel: [   19.027477] uhci_hcd 0000:00:1a.1: irq 19, io base 0x00001840
Apr 19 19:37:40 kakyo-laptop kernel: [   19.027581] usb usb3: configuration #1 chosen from 1 choice
Apr 19 19:37:40 kakyo-laptop kernel: [   19.027602] hub 3-0:1.0: USB hub found
Apr 19 19:37:40 kakyo-laptop kernel: [   19.027606] hub 3-0:1.0: 2 ports detected
Apr 19 19:37:40 kakyo-laptop kernel: [   19.137360] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 23 (level, low) -> IRQ 20
Apr 19 19:37:40 kakyo-laptop kernel: [   19.137372] PCI: Setting latency timer of device 0000:00:1d.0 to 64
Apr 19 19:37:40 kakyo-laptop kernel: [   19.137376] uhci_hcd 0000:00:1d.0: UHCI Host Controller
Apr 19 19:37:40 kakyo-laptop kernel: [   19.137397] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 4
Apr 19 19:37:40 kakyo-laptop kernel: [   19.137428] uhci_hcd 0000:00:1d.0: irq 20, io base 0x00001860
Apr 19 19:37:40 kakyo-laptop kernel: [   19.137536] usb usb4: configuration #1 chosen from 1 choice
Apr 19 19:37:40 kakyo-laptop kernel: [   19.137556] hub 4-0:1.0: USB hub found
Apr 19 19:37:40 kakyo-laptop kernel: [   19.137560] hub 4-0:1.0: 2 ports detected
Apr 19 19:37:40 kakyo-laptop kernel: [   19.247303] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 19 (level, low) -> IRQ 21
Apr 19 19:37:40 kakyo-laptop kernel: [   19.247315] PCI: Setting latency timer of device 0000:00:1d.1 to 64
Apr 19 19:37:40 kakyo-laptop kernel: [   19.247319] uhci_hcd 0000:00:1d.1: UHCI Host Controller
Apr 19 19:37:40 kakyo-laptop kernel: [   19.247339] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 5
Apr 19 19:37:40 kakyo-laptop kernel: [   19.247371] uhci_hcd 0000:00:1d.1: irq 21, io base 0x00001880
Apr 19 19:37:40 kakyo-laptop kernel: [   19.247485] usb usb5: configuration #1 chosen from 1 choice
Apr 19 19:37:40 kakyo-laptop kernel: [   19.247505] hub 5-0:1.0: USB hub found
Apr 19 19:37:40 kakyo-laptop kernel: [   19.247509] hub 5-0:1.0: 2 ports detected
Apr 19 19:37:40 kakyo-laptop kernel: [   19.290762] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 18
Apr 19 19:37:40 kakyo-laptop kernel: [   19.290778] PCI: Setting latency timer of device 0000:00:1d.2 to 64
Apr 19 19:37:40 kakyo-laptop kernel: [   19.290785] uhci_hcd 0000:00:1d.2: UHCI Host Controller
Apr 19 19:37:40 kakyo-laptop kernel: [   19.290822] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 6
Apr 19 19:37:40 kakyo-laptop kernel: [   19.290857] uhci_hcd 0000:00:1d.2: irq 18, io base 0x000018a0
Apr 19 19:37:40 kakyo-laptop kernel: [   19.290955] usb usb6: configuration #1 chosen from 1 choice
Apr 19 19:37:40 kakyo-laptop kernel: [   19.290974] hub 6-0:1.0: USB hub found
Apr 19 19:37:40 kakyo-laptop kernel: [   19.290978] hub 6-0:1.0: 2 ports detected
Apr 19 19:37:40 kakyo-laptop kernel: [   19.295920] usb 3-2: new low speed USB device using uhci_hcd and address 2
Apr 19 19:37:40 kakyo-laptop kernel: [   19.309825] r8169 Gigabit Ethernet driver 2.2LK loaded
Apr 19 19:37:40 kakyo-laptop kernel: [   19.309856] ACPI: PCI Interrupt 0000:08:00.0[A] -> GSI 17 (level, low) -> IRQ 16
Apr 19 19:37:40 kakyo-laptop kernel: [   19.309877] PCI: Setting latency timer of device 0000:08:00.0 to 64
Apr 19 19:37:40 kakyo-laptop kernel: [   19.310191] eth0: RTL8101e at 0xf8878000, 00:1e:68:99:1b:73, XID 34200000 IRQ 220
Apr 19 19:37:40 kakyo-laptop kernel: [   19.312729] ahci 0000:00:1f.2: version 3.0
Apr 19 19:37:40 kakyo-laptop kernel: [   19.312753] ACPI: PCI Interrupt 0000:00:1f.2[B] -> GSI 19 (level, low) -> IRQ 21
Apr 19 19:37:40 kakyo-laptop kernel: [   19.359650] usb 3-2: configuration #1 chosen from 1 choice
Apr 19 19:37:40 kakyo-laptop kernel: [   19.371374] usbcore: registered new interface driver hiddev
Apr 19 19:37:40 kakyo-laptop kernel: [   19.374590] input: Logitech USB Optical Mouse as /devices/pci0000:00/0000:00:1a.1/usb3/3-2/3-2:1.0/input/input2
Apr 19 19:37:40 kakyo-laptop kernel: [   19.377321] Clocksource tsc unstable (delta = -290109953 ns)
Apr 19 19:37:40 kakyo-laptop kernel: [   19.380792] input,hidraw0: USB HID v1.10 Mouse [Logitech USB Optical Mouse] on usb-0000:00:1a.1-2
Apr 19 19:37:40 kakyo-laptop kernel: [   19.380817] usbcore: registered new interface driver usbhid
Apr 19 19:37:40 kakyo-laptop kernel: [   19.380822] /build/buildd/linux-2.6.24/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
Apr 19 19:37:40 kakyo-laptop kernel: [   19.457413] ahci 0000:00:1f.2: AHCI 0001.0100 32 slots 3 ports 3 Gbps 0x7 impl SATA mode
Apr 19 19:37:40 kakyo-laptop kernel: [   19.457422] ahci 0000:00:1f.2: flags: 64bit ncq sntf pm led clo pio slum part 
Apr 19 19:37:40 kakyo-laptop kernel: [   19.457432] PCI: Setting latency timer of device 0000:00:1f.2 to 64
Apr 19 19:37:40 kakyo-laptop kernel: [   19.457740] scsi0 : ahci
Apr 19 19:37:40 kakyo-laptop kernel: [   19.457962] scsi1 : ahci
Apr 19 19:37:40 kakyo-laptop kernel: [   19.458121] scsi2 : ahci
Apr 19 19:37:40 kakyo-laptop kernel: [   19.458201] ata1: SATA max UDMA/133 abar m2048@0xf8604000 port 0xf8604100 irq 219
Apr 19 19:37:40 kakyo-laptop kernel: [   19.458204] ata2: SATA max UDMA/133 abar m2048@0xf8604000 port 0xf8604180 irq 219
Apr 19 19:37:40 kakyo-laptop kernel: [   19.458207] ata3: SATA max UDMA/133 abar m2048@0xf8604000 port 0xf8604200 irq 219
Apr 19 19:37:40 kakyo-laptop kernel: [   19.498112] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
Apr 19 19:37:40 kakyo-laptop kernel: [   19.498561] ata1.00: ATA-8: WDC WD2500BEVS-60UST0, 01.01A01, max UDMA/100
Apr 19 19:37:40 kakyo-laptop kernel: [   19.498566] ata1.00: 488397168 sectors, multi 16: LBA48 
Apr 19 19:37:40 kakyo-laptop kernel: [   19.499126] ata1.00: configured for UDMA/100
Apr 19 19:37:40 kakyo-laptop kernel: [   19.520819] ata2: SATA link down (SStatus 0 SControl 300)
Apr 19 19:37:40 kakyo-laptop kernel: [   19.542590] ata3: SATA link down (SStatus 0 SControl 300)
Apr 19 19:37:40 kakyo-laptop kernel: [   19.542830] scsi 0:0:0:0: Direct-Access     ATA      WDC WD2500BEVS-6 01.0 PQ: 0 ANSI: 5
Apr 19 19:37:40 kakyo-laptop kernel: [   19.543154] ACPI: PCI Interrupt 0000:09:09.0[A] -> GSI 20 (level, low) -> IRQ 22
Apr 19 19:37:40 kakyo-laptop kernel: [   19.596309] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[22]  MMIO=[f8300000-f83007ff]  Max Packet=[2048]  IR/IT contexts=[4/4]
Apr 19 19:37:40 kakyo-laptop kernel: [   19.600376] Driver 'sd' needs updating - please use bus_type methods
Apr 19 19:37:40 kakyo-laptop kernel: [   19.600826] ata_piix 0000:00:1f.1: version 2.12
Apr 19 19:37:40 kakyo-laptop kernel: [   19.600844] ACPI: PCI Interrupt 0000:00:1f.1[A] -> GSI 19 (level, low) -> IRQ 21
Apr 19 19:37:40 kakyo-laptop kernel: [   19.600879] PCI: Setting latency timer of device 0000:00:1f.1 to 64
Apr 19 19:37:40 kakyo-laptop kernel: [   19.600922] sd 0:0:0:0: [sda] 488397168 512-byte hardware sectors (250059 MB)
Apr 19 19:37:40 kakyo-laptop kernel: [   19.600934] sd 0:0:0:0: [sda] Write Protect is off
Apr 19 19:37:40 kakyo-laptop kernel: [   19.600936] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Apr 19 19:37:40 kakyo-laptop kernel: [   19.600950] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Apr 19 19:37:40 kakyo-laptop kernel: [   19.600993] sd 0:0:0:0: [sda] 488397168 512-byte hardware sectors (250059 MB)
Apr 19 19:37:40 kakyo-laptop kernel: [   19.601001] sd 0:0:0:0: [sda] Write Protect is off
Apr 19 19:37:40 kakyo-laptop kernel: [   19.601003] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Apr 19 19:37:40 kakyo-laptop kernel: [   19.601017] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Apr 19 19:37:40 kakyo-laptop kernel: [   19.601020]  sda:<6>scsi3 : ata_piix
Apr 19 19:37:40 kakyo-laptop kernel: [   19.601123] scsi4 : ata_piix
Apr 19 19:37:40 kakyo-laptop kernel: [   19.601615] ata4: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0x1810 irq 14
Apr 19 19:37:40 kakyo-laptop kernel: [   19.601618] ata5: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x1818 irq 15
Apr 19 19:37:40 kakyo-laptop kernel: [   19.652462]  sda1 sda2
Apr 19 19:37:40 kakyo-laptop kernel: [   19.676955] sd 0:0:0:0: [sda] Attached SCSI disk
Apr 19 19:37:40 kakyo-laptop kernel: [   19.680748] sd 0:0:0:0: Attached scsi generic sg0 type 0
Apr 19 19:37:40 kakyo-laptop kernel: [   19.906333] ata4.00: ATAPI: Optiarc DVD RW AD-7561A, GH09, max MWDMA2
Apr 19 19:37:40 kakyo-laptop kernel: [   19.919684] ata4.00: configured for MWDMA2
Apr 19 19:37:40 kakyo-laptop kernel: [   19.935560] scsi 3:0:0:0: CD-ROM            Optiarc  DVD RW AD-7561A  GH09 PQ: 0 ANSI: 5
Apr 19 19:37:40 kakyo-laptop kernel: [   19.935681] scsi 3:0:0:0: Attached scsi generic sg1 type 5
Apr 19 19:37:40 kakyo-laptop kernel: [   19.936015] ACPI: PCI Interrupt 0000:00:1d.7[A] -> GSI 23 (level, low) -> IRQ 20
Apr 19 19:37:40 kakyo-laptop kernel: [   19.936029] PCI: Setting latency timer of device 0000:00:1d.7 to 64
Apr 19 19:37:40 kakyo-laptop kernel: [   19.936032] ehci_hcd 0000:00:1d.7: EHCI Host Controller
Apr 19 19:37:40 kakyo-laptop kernel: [   19.936058] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 7
Apr 19 19:37:40 kakyo-laptop kernel: [   19.939956] ehci_hcd 0000:00:1d.7: debug port 1
Apr 19 19:37:40 kakyo-laptop kernel: [   19.939963] PCI: cache line size of 32 is not supported by device 0000:00:1d.7
Apr 19 19:37:40 kakyo-laptop kernel: [   19.939968] ehci_hcd 0000:00:1d.7: irq 20, io mem 0xf8604c00
Apr 19 19:37:40 kakyo-laptop kernel: [   19.946409] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
Apr 19 19:37:40 kakyo-laptop kernel: [   19.946599] usb usb7: configuration #1 chosen from 1 choice
Apr 19 19:37:40 kakyo-laptop kernel: [   19.946638] hub 7-0:1.0: USB hub found
Apr 19 19:37:40 kakyo-laptop kernel: [   19.946643] hub 7-0:1.0: 6 ports detected
Apr 19 19:37:40 kakyo-laptop kernel: [   19.966386] Driver 'sr' needs updating - please use bus_type methods
Apr 19 19:37:40 kakyo-laptop kernel: [   19.972796] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
Apr 19 19:37:40 kakyo-laptop kernel: [   19.972802] Uniform CD-ROM driver Revision: 3.20
Apr 19 19:37:40 kakyo-laptop kernel: [   19.972870] sr 3:0:0:0: Attached scsi CD-ROM sr0
Apr 19 19:37:40 kakyo-laptop kernel: [   20.030048] Attempting manual resume
Apr 19 19:37:40 kakyo-laptop kernel: [   20.030051] swsusp: Resume From Partition 8:2
Apr 19 19:37:40 kakyo-laptop kernel: [   20.030053] PM: Checking swsusp image.
Apr 19 19:37:40 kakyo-laptop kernel: [   20.030203] PM: Resume from disk failed.
Apr 19 19:37:40 kakyo-laptop kernel: [   20.042358] EXT3-fs: INFO: recovery required on readonly filesystem.
Apr 19 19:37:40 kakyo-laptop kernel: [   20.042361] EXT3-fs: write access will be enabled during recovery.
Apr 19 19:37:40 kakyo-laptop kernel: [   20.288548] usb 7-4: new high speed USB device using ehci_hcd and address 2
Apr 19 19:37:40 kakyo-laptop kernel: [   20.408875] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[00241b00e96f1601]
Apr 19 19:37:40 kakyo-laptop kernel: [   20.447627] usb 7-4: configuration #1 chosen from 1 choice
Apr 19 19:37:40 kakyo-laptop kernel: [   21.296105] kjournald starting.  Commit interval 5 seconds
Apr 19 19:37:40 kakyo-laptop kernel: [   21.296147] EXT3-fs: sda1: orphan cleanup on readonly fs
Apr 19 19:37:40 kakyo-laptop kernel: [   21.296157] ext3_orphan_cleanup: deleting unreferenced inode 1843837
Apr 19 19:37:40 kakyo-laptop kernel: [   21.296193] ext3_orphan_cleanup: deleting unreferenced inode 1843836
Apr 19 19:37:40 kakyo-laptop kernel: [   21.296202] ext3_orphan_cleanup: deleting unreferenced inode 1843812
Apr 19 19:37:40 kakyo-laptop kernel: [   21.296211] ext3_orphan_cleanup: deleting unreferenced inode 2137508
Apr 19 19:37:40 kakyo-laptop kernel: [   21.296220] ext3_orphan_cleanup: deleting unreferenced inode 1843800
Apr 19 19:37:40 kakyo-laptop kernel: [   21.317998] ext3_orphan_cleanup: deleting unreferenced inode 475177
Apr 19 19:37:40 kakyo-laptop kernel: [   21.318011] EXT3-fs: sda1: 6 orphan inodes deleted
Apr 19 19:37:40 kakyo-laptop kernel: [   21.318013] EXT3-fs: recovery complete.
Apr 19 19:37:40 kakyo-laptop kernel: [   21.361658] EXT3-fs: mounted filesystem with ordered data mode.
Apr 19 19:37:40 kakyo-laptop kernel: [   30.258086] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Apr 19 19:37:40 kakyo-laptop kernel: [   30.308551] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
Apr 19 19:37:40 kakyo-laptop kernel: [   30.351175] Linux agpgart interface v0.102
Apr 19 19:37:40 kakyo-laptop kernel: [   30.444176] iTCO_vendor_support: vendor-support=0
Apr 19 19:37:40 kakyo-laptop kernel: [   30.520267] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.02 (26-Jul-2007)
Apr 19 19:37:40 kakyo-laptop kernel: [   30.520358] iTCO_wdt: Found a ICH8M TCO device (Version=2, TCOBASE=0x1060)
Apr 19 19:37:40 kakyo-laptop kernel: [   30.520398] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
Apr 19 19:37:40 kakyo-laptop kernel: [   30.681350] ACPI: WMI-Acer: Mapper loaded
Apr 19 19:37:40 kakyo-laptop kernel: [   30.709451] input: PC Speaker as /devices/platform/pcspkr/input/input3
Apr 19 19:37:40 kakyo-laptop kernel: [   30.734522] input: Power Button (FF) as /devices/virtual/input/input4
Apr 19 19:37:40 kakyo-laptop kernel: [   30.888903] ricoh-mmc: Ricoh MMC Controller disabling driver
Apr 19 19:37:40 kakyo-laptop kernel: [   30.888907] ricoh-mmc: Copyright(c) Philip Langdale
Apr 19 19:37:40 kakyo-laptop kernel: [   30.888940] ricoh-mmc: Ricoh MMC controller found at 0000:09:09.2 [1180:0843] (rev 12)
Apr 19 19:37:40 kakyo-laptop kernel: [   30.888952] ricoh-mmc: Controller is now disabled.
Apr 19 19:37:40 kakyo-laptop kernel: [   30.905170] agpgart: Detected an Intel 965GM Chipset.
Apr 19 19:37:40 kakyo-laptop kernel: [   30.906054] agpgart: Detected 7676K stolen memory.
Apr 19 19:37:40 kakyo-laptop kernel: [   30.919527] agpgart: AGP aperture is 256M @ 0xd0000000
Apr 19 19:37:40 kakyo-laptop kernel: [   31.113696] ACPI: Power Button (FF) [PWRF]
Apr 19 19:37:40 kakyo-laptop kernel: [   31.113756] input: Power Button (CM) as /devices/virtual/input/input5
Apr 19 19:37:40 kakyo-laptop kernel: [   31.220721] sdhci: Secure Digital Host Controller Interface driver
Apr 19 19:37:40 kakyo-laptop kernel: [   31.220724] sdhci: Copyright(c) Pierre Ossman
Apr 19 19:37:40 kakyo-laptop kernel: [   31.220759] sdhci: SDHCI controller found at 0000:09:09.1 [1180:0822] (rev 22)
Apr 19 19:37:40 kakyo-laptop kernel: [   31.220779] ACPI: PCI Interrupt 0000:09:09.1[B] -> GSI 21 (level, low) -> IRQ 19
Apr 19 19:37:40 kakyo-laptop kernel: [   31.220794] sdhci:slot0: Will use DMA mode even though HW doesn't fully claim to support it.
Apr 19 19:37:40 kakyo-laptop kernel: [   31.220839] mmc0: SDHCI at 0xf8300800 irq 19 DMA
Apr 19 19:37:40 kakyo-laptop kernel: [   31.253553] ACPI: Power Button (CM) [PWRB]
Apr 19 19:37:40 kakyo-laptop kernel: [   31.253606] input: Sleep Button (CM) as /devices/virtual/input/input6
Apr 19 19:37:40 kakyo-laptop kernel: [   31.403492] ACPI: Sleep Button (CM) [SLPB]
Apr 19 19:37:40 kakyo-laptop kernel: [   31.403551] input: Lid Switch as /devices/virtual/input/input7
Apr 19 19:37:40 kakyo-laptop kernel: [   31.465071] ACPI: Lid Switch [LID]
Apr 19 19:37:40 kakyo-laptop kernel: [   31.469600] Linux video capture interface: v2.00
Apr 19 19:37:40 kakyo-laptop kernel: [   31.574093] ACPI: Battery Slot [BAT0] (battery present)
Apr 19 19:37:40 kakyo-laptop kernel: [   31.577371] ACPI: AC Adapter [ACAD] (on-line)
Apr 19 19:37:40 kakyo-laptop kernel: [   31.583619] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:02/LNXVIDEO:00/input/input8
Apr 19 19:37:40 kakyo-laptop kernel: [   31.641157] iwl4965: Intel(R) Wireless WiFi Link 4965AGN driver for Linux, 1.2.0
Apr 19 19:37:40 kakyo-laptop kernel: [   31.641160] iwl4965: Copyright(c) 2003-2007 Intel Corporation
Apr 19 19:37:40 kakyo-laptop kernel: [   31.641239] ACPI: PCI Interrupt 0000:02:00.0[A] -> GSI 16 (level, low) -> IRQ 17
Apr 19 19:37:40 kakyo-laptop kernel: [   31.641250] PCI: Setting latency timer of device 0000:02:00.0 to 64
Apr 19 19:37:40 kakyo-laptop kernel: [   31.641264] iwl4965: Detected Intel Wireless WiFi Link 4965AGN
Apr 19 19:37:40 kakyo-laptop kernel: [   31.713407] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
Apr 19 19:37:40 kakyo-laptop kernel: [   31.723846] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/LNXVIDEO:01/input/input9
Apr 19 19:37:40 kakyo-laptop kernel: [   31.743539] uvcvideo: Found UVC 1.00 device HP Webcam (064e:a110)
Apr 19 19:37:40 kakyo-laptop kernel: [   31.747716] usbcore: registered new interface driver uvcvideo
Apr 19 19:37:40 kakyo-laptop kernel: [   31.747723] USB Video Class driver (v0.1.0)
Apr 19 19:37:40 kakyo-laptop kernel: [   31.888387] iwl4965: Radio disabled by HW RF Kill switch
Apr 19 19:37:40 kakyo-laptop kernel: [   31.895798] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)
Apr 19 19:37:40 kakyo-laptop kernel: [   31.957124] Synaptics Touchpad, model: 1, fw: 6.3, id: 0x1a0b1, caps: 0xa04711/0xa00000
Apr 19 19:37:40 kakyo-laptop kernel: [   32.065725] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input10
Apr 19 19:37:40 kakyo-laptop kernel: [   32.091347] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 22 (level, low) -> IRQ 23
Apr 19 19:37:40 kakyo-laptop kernel: [   32.091369] PCI: Setting latency timer of device 0000:00:1b.0 to 64
Apr 19 19:37:40 kakyo-laptop kernel: [   32.486671] lp: driver loaded but no devices found
Apr 19 19:37:40 kakyo-laptop kernel: [   32.595750] Adding 4883752k swap on /dev/sda2.  Priority:-1 extents:1 across:4883752k
Apr 19 19:37:40 kakyo-laptop kernel: [   33.238950] EXT3 FS on sda1, internal journal
Apr 19 19:37:40 kakyo-laptop kernel: [   33.430784] device-mapper: uevent: version 1.0.3
Apr 19 19:37:40 kakyo-laptop kernel: [   33.430812] device-mapper: ioctl: 4.12.0-ioctl (2007-10-02) initialised: dm-devel@redhat.com
Apr 19 19:37:40 kakyo-laptop kernel: [   34.910280] ip_tables: (C) 2000-2006 Netfilter Core Team
Apr 19 19:37:40 kakyo-laptop kernel: [   35.462378] No dock devices found.
Apr 19 19:37:40 kakyo-laptop NetworkManager: <info>  starting... 
Apr 19 19:37:40 kakyo-laptop NetworkManager: <info>  New VPN service 'vpnc' (org.freedesktop.NetworkManager.vpnc). 
Apr 19 19:37:40 kakyo-laptop kernel: [   37.301404] NET: Registered protocol family 10
Apr 19 19:37:40 kakyo-laptop kernel: [   37.301611] lo: Disabled Privacy Extensions
Apr 19 19:37:41 kakyo-laptop avahi-daemon[5352]: Found user 'avahi' (UID 109) and group 'avahi' (GID 120).
Apr 19 19:37:41 kakyo-laptop avahi-daemon[5352]: Successfully dropped root privileges.
Apr 19 19:37:41 kakyo-laptop avahi-daemon[5352]: avahi-daemon 0.6.22 starting up.
Apr 19 19:37:41 kakyo-laptop avahi-daemon[5352]: Successfully called chroot().
Apr 19 19:37:41 kakyo-laptop avahi-daemon[5352]: Successfully dropped remaining capabilities.
Apr 19 19:37:41 kakyo-laptop avahi-daemon[5352]: No service file found in /etc/avahi/services.
Apr 19 19:37:41 kakyo-laptop avahi-daemon[5352]: Network interface enumeration completed.
Apr 19 19:37:41 kakyo-laptop avahi-daemon[5352]: Registering HINFO record with values 'I686'/'LINUX'.
Apr 19 19:37:41 kakyo-laptop avahi-daemon[5352]: Server startup complete. Host name is kakyo-laptop.local. Local service cookie is 1128868341.
Apr 19 19:37:41 kakyo-laptop kernel: [   37.577022] apm: BIOS not found.
Apr 19 19:37:41 kakyo-laptop kernel: [   37.783338] ppdev: user-space parallel port driver
Apr 19 19:37:41 kakyo-laptop kernel: [   37.972485] audit(1240184261.650:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=5395 profile="/usr/sbin/cupsd" namespace="default"
Apr 19 19:37:45 kakyo-laptop dhcdbd: Started up.
Apr 19 19:37:47 kakyo-laptop NetworkManager: <info>  Found radio killswitch /org/freedesktop/Hal/devices/iwl_wlan_switch 
Apr 19 19:37:47 kakyo-laptop kernel: [   42.505322] r8169: eth0: link up
Apr 19 19:37:47 kakyo-laptop kernel: [   42.505335] r8169: eth0: link up
Apr 19 19:37:47 kakyo-laptop NetworkManager: <info>  eth0: Device is fully-supported using driver 'r8169'. 
Apr 19 19:37:47 kakyo-laptop NetworkManager: <info>  nm_device_init(): waiting for device's worker thread to start 
Apr 19 19:37:47 kakyo-laptop NetworkManager: <info>  nm_device_init(): device's worker thread started, continuing. 
Apr 19 19:37:47 kakyo-laptop NetworkManager: <info>  Now managing wired Ethernet (802.3) device 'eth0'. 
Apr 19 19:37:47 kakyo-laptop NetworkManager: <info>  Deactivating device eth0. 
Apr 19 19:37:47 kakyo-laptop NetworkManager: <info>  Will activate wired connection 'eth0' because it now has a link. 
Apr 19 19:37:47 kakyo-laptop NetworkManager: <debug> [1240184267.071377] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/storage_model_DVD_RW_AD_7561A'). 
Apr 19 19:37:47 kakyo-laptop NetworkManager: <info>  SWITCH: no current connection, found better connection 'eth0'. 
Apr 19 19:37:47 kakyo-laptop hcid[5926]: Bluetooth HCI daemon
Apr 19 19:37:47 kakyo-laptop kernel: [   42.608285] Bluetooth: Core ver 2.11
Apr 19 19:37:47 kakyo-laptop kernel: [   42.608409] NET: Registered protocol family 31
Apr 19 19:37:47 kakyo-laptop kernel: [   42.608412] Bluetooth: HCI device and connection manager initialized
Apr 19 19:37:47 kakyo-laptop kernel: [   42.608418] Bluetooth: HCI socket layer initialized
Apr 19 19:37:47 kakyo-laptop hcid[5926]: Starting SDP server
Apr 19 19:37:47 kakyo-laptop kernel: [   42.641374] Bluetooth: L2CAP ver 2.9
Apr 19 19:37:47 kakyo-laptop hcid[5926]: Created local server at unix:abstract=/var/run/dbus-hOHrtSc7vy,guid=9f3d02c3011b63418252eba049ebb5cb
Apr 19 19:37:47 kakyo-laptop kernel: [   42.641382] Bluetooth: L2CAP socket layer initialized
Apr 19 19:37:47 kakyo-laptop audio[5946]: Bluetooth Audio daemon
Apr 19 19:37:47 kakyo-laptop input[5948]: Bluetooth Input daemon
Apr 19 19:37:47 kakyo-laptop input[5948]: Registered input manager path:/org/bluez/input
Apr 19 19:37:47 kakyo-laptop audio[5946]: Unix socket created: 5
Apr 19 19:37:47 kakyo-laptop audio[5946]: audio.conf: Key file does not have key 'Enable'
Apr 19 19:37:47 kakyo-laptop audio[5946]: audio.conf: Key file does not have key 'Disable'
Apr 19 19:37:47 kakyo-laptop kernel: [   42.722013] Bluetooth: RFCOMM socket layer initialized
Apr 19 19:37:47 kakyo-laptop kernel: [   42.722030] Bluetooth: RFCOMM TTY layer initialized
Apr 19 19:37:47 kakyo-laptop kernel: [   42.722033] Bluetooth: RFCOMM ver 1.8
Apr 19 19:37:47 kakyo-laptop audio[5946]: add_service_record: got record id 0x10000
Apr 19 19:37:47 kakyo-laptop audio[5946]: audio.conf: Key file does not have key 'Disable'
Apr 19 19:37:47 kakyo-laptop audio[5946]: audio.conf: Key file does not have group 'A2DP'
Apr 19 19:37:47 kakyo-laptop last message repeated 3 times
Apr 19 19:37:47 kakyo-laptop audio[5946]: SEP 0x806d308 registered: type:0 codec:0 seid:1
Apr 19 19:37:47 kakyo-laptop audio[5946]: add_service_record: got record id 0x10001
Apr 19 19:37:47 kakyo-laptop audio[5946]: add_service_record: got record id 0x10002
Apr 19 19:37:47 kakyo-laptop audio[5946]: add_service_record: got record id 0x10003
Apr 19 19:37:47 kakyo-laptop audio[5946]: Registered manager path:/org/bluez/audio
Apr 19 19:37:48 kakyo-laptop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.reason
Apr 19 19:37:48 kakyo-laptop NetworkManager: <info>  Will activate connection 'eth0'. 
Apr 19 19:37:48 kakyo-laptop NetworkManager: <info>  Device eth0 activation scheduled... 
Apr 19 19:37:48 kakyo-laptop NetworkManager: <info>  Error getting killswitch power: org.freedesktop.Hal.Device.KillSwitch.NotSupported - hal-ipw-killswitch-linux returned 255 
Apr 19 19:37:48 kakyo-laptop NetworkManager: <info>  Wireless now enabled by radio killswitch 
Apr 19 19:37:48 kakyo-laptop NetworkManager: <debug> [1240184268.071592] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_bluetooth'). 
Apr 19 19:37:48 kakyo-laptop NetworkManager: <info>  Activation (eth0) started... 
Apr 19 19:37:48 kakyo-laptop NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) scheduled... 
Apr 19 19:37:48 kakyo-laptop NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) started... 
Apr 19 19:37:48 kakyo-laptop NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) scheduled... 
Apr 19 19:37:48 kakyo-laptop NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) complete. 
Apr 19 19:37:48 kakyo-laptop NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) starting... 
Apr 19 19:37:48 kakyo-laptop NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) successful. 
Apr 19 19:37:48 kakyo-laptop NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) scheduled. 
Apr 19 19:37:48 kakyo-laptop NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) complete. 
Apr 19 19:37:48 kakyo-laptop NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) started... 
Apr 19 19:37:49 kakyo-laptop NetworkManager: <info>  Activation (eth0) Beginning DHCP transaction. 
Apr 19 19:37:49 kakyo-laptop NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) complete. 
Apr 19 19:37:49 kakyo-laptop NetworkManager: <info>  DHCP daemon state is now 12 (successfully started) for interface eth0 
Apr 19 19:37:49 kakyo-laptop ntpd[6052]: ntpd 4.2.4p4@1.1520-o Tue Jan  6 15:51:34 UTC 2009 (1)
Apr 19 19:37:49 kakyo-laptop ntpd[6053]: precision = 1.000 usec
Apr 19 19:37:49 kakyo-laptop ntpd[6053]: Listening on interface #0 wildcard, 0.0.0.0#123 Disabled
Apr 19 19:37:49 kakyo-laptop ntpd[6053]: Listening on interface #1 wildcard, ::#123 Disabled
Apr 19 19:37:49 kakyo-laptop ntpd[6053]: Listening on interface #2 lo, ::1#123 Enabled
Apr 19 19:37:49 kakyo-laptop ntpd[6053]: Listening on interface #3 lo, 127.0.0.1#123 Enabled
Apr 19 19:37:49 kakyo-laptop ntpd[6053]: kernel time sync status 0040
Apr 19 19:37:49 kakyo-laptop anacron[6073]: Anacron 2.3 started on 2009-04-19
Apr 19 19:37:49 kakyo-laptop ntpd[6053]: frequency initialized -80.772 PPM from /var/lib/ntp/ntp.drift
Apr 19 19:37:49 kakyo-laptop anacron[6073]: Normal exit (0 jobs run)
Apr 19 19:37:49 kakyo-laptop /usr/sbin/cron[6101]: (CRON) INFO (pidfile fd = 3)
Apr 19 19:37:49 kakyo-laptop /usr/sbin/cron[6102]: (CRON) STARTUP (fork ok)
Apr 19 19:37:50 kakyo-laptop /usr/sbin/cron[6102]: (CRON) INFO (Running @reboot jobs)
Apr 19 19:37:50 kakyo-laptop NetworkManager: <info>  DHCP daemon state is now 1 (starting) for interface eth0 
Apr 19 19:37:50 kakyo-laptop kernel: [   44.167990] NET: Registered protocol family 17
Apr 19 19:37:50 kakyo-laptop kernel: [   44.714634] [drm] Initialized drm 1.1.0 20060810
Apr 19 19:37:50 kakyo-laptop kernel: [   44.716699] ACPI: PCI Interrupt 0000:00:02.0[A] -> GSI 16 (level, low) -> IRQ 17
Apr 19 19:37:50 kakyo-laptop kernel: [   44.716708] PCI: Setting latency timer of device 0000:00:02.0 to 64
Apr 19 19:37:50 kakyo-laptop kernel: [   44.716758] [drm] Initialized i915 1.6.0 20060119 on minor 0
Apr 19 19:37:50 kakyo-laptop kernel: [   44.732413] mtrr: type mismatch for d0000000,10000000 old: write-back new: write-combining
Apr 19 19:37:50 kakyo-laptop NetworkManager: <debug> [1240184270.966123] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_2a02_drm_i915_card0'). 
Apr 19 19:37:51 kakyo-laptop kernel: [   45.033726] /dev/vmmon[6173]: Module vmmon: registered with major=10 minor=165
Apr 19 19:37:51 kakyo-laptop kernel: [   45.033739] /dev/vmmon[6173]: Initial HV check: anyNotCapable=1 anyUnlocked=0 anyEnabled=0 anyDisabled=0
Apr 19 19:37:51 kakyo-laptop kernel: [   45.033741] /dev/vmmon[6173]: Module vmmon: initialized
Apr 19 19:37:51 kakyo-laptop kernel: [   45.084152] /dev/vmci[6184]: VMCI: Driver initialized.
Apr 19 19:37:51 kakyo-laptop kernel: [   45.084187] /dev/vmci[6184]: Module vmci: registered with major=10 minor=62
Apr 19 19:37:51 kakyo-laptop kernel: [   45.084190] /dev/vmci[6184]: Module vmci: initialized
Apr 19 19:37:51 kakyo-laptop kernel: [   45.119323] vsock: no version for "VMCIDatagram_Send" found: kernel tainted.
Apr 19 19:37:51 kakyo-laptop ntpd_initres[6085]: host name not found: ntp.ubuntu.com
Apr 19 19:37:51 kakyo-laptop ntpd_initres[6085]: couldn't resolve `ntp.ubuntu.com', giving up on it
Apr 19 19:37:52 kakyo-laptop dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
Apr 19 19:37:52 kakyo-laptop dhclient: DHCPOFFER of 132.206.5.148 from 132.206.5.129
Apr 19 19:37:52 kakyo-laptop dhclient: DHCPREQUEST of 132.206.5.148 on eth0 to 255.255.255.255 port 67
Apr 19 19:37:52 kakyo-laptop dhclient: DHCPACK of 132.206.5.148 from 132.206.5.129
Apr 19 19:37:52 kakyo-laptop avahi-daemon[5352]: Joining mDNS multicast group on interface eth0.IPv4 with address 132.206.5.148.
Apr 19 19:37:52 kakyo-laptop avahi-daemon[5352]: New relevant interface eth0.IPv4 for mDNS.
Apr 19 19:37:52 kakyo-laptop avahi-daemon[5352]: Registering new address record for 132.206.5.148 on eth0.IPv4.
Apr 19 19:37:52 kakyo-laptop avahi-daemon[5352]: Withdrawing address record for 132.206.5.148 on eth0.
Apr 19 19:37:52 kakyo-laptop avahi-daemon[5352]: Leaving mDNS multicast group on interface eth0.IPv4 with address 132.206.5.148.
Apr 19 19:37:52 kakyo-laptop avahi-daemon[5352]: Interface eth0.IPv4 no longer relevant for mDNS.
Apr 19 19:37:52 kakyo-laptop avahi-daemon[5352]: Joining mDNS multicast group on interface eth0.IPv4 with address 132.206.5.148.
Apr 19 19:37:52 kakyo-laptop avahi-daemon[5352]: New relevant interface eth0.IPv4 for mDNS.
Apr 19 19:37:52 kakyo-laptop avahi-daemon[5352]: Registering new address record for 132.206.5.148 on eth0.IPv4.
Apr 19 19:37:52 kakyo-laptop dhclient: bound to 132.206.5.148 -- renewal in 104688 seconds.
Apr 19 19:37:52 kakyo-laptop NetworkManager: <info>  DHCP daemon state is now 2 (bound) for interface eth0 
Apr 19 19:37:52 kakyo-laptop NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP Configure Get) scheduled... 
Apr 19 19:37:52 kakyo-laptop NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP Configure Get) started... 
Apr 19 19:37:52 kakyo-laptop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.host_name
Apr 19 19:37:52 kakyo-laptop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.domain_name
Apr 19 19:37:52 kakyo-laptop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.nis_domain
Apr 19 19:37:52 kakyo-laptop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.nis_servers
Apr 19 19:37:52 kakyo-laptop NetworkManager: <info>  Retrieved the following IP4 configuration from the DHCP daemon: 
Apr 19 19:37:52 kakyo-laptop NetworkManager: <info>    address 132.206.5.148 
Apr 19 19:37:52 kakyo-laptop NetworkManager: <info>    netmask 255.255.255.128 
Apr 19 19:37:52 kakyo-laptop NetworkManager: <info>    broadcast 132.206.5.255 
Apr 19 19:37:52 kakyo-laptop NetworkManager: <info>    gateway 132.206.5.129 
Apr 19 19:37:52 kakyo-laptop NetworkManager: <info>    nameserver 132.206.85.18 
Apr 19 19:37:52 kakyo-laptop NetworkManager: <info>    nameserver 132.206.85.19 
Apr 19 19:37:52 kakyo-laptop NetworkManager: <info>    nameserver 132.206.85.36 
Apr 19 19:37:52 kakyo-laptop NetworkManager: <info>    nameserver 132.206.44.21 
Apr 19 19:37:52 kakyo-laptop NetworkManager: <info>    nameserver 132.206.25.21 
Apr 19 19:37:52 kakyo-laptop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.interface_mtu
Apr 19 19:37:52 kakyo-laptop NetworkManager: <info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) scheduled... 
Apr 19 19:37:52 kakyo-laptop NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP Configure Get) complete. 
Apr 19 19:37:52 kakyo-laptop NetworkManager: <info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) started... 
Apr 19 19:37:52 kakyo-laptop avahi-daemon[5352]: Withdrawing address record for 132.206.5.148 on eth0.
Apr 19 19:37:52 kakyo-laptop avahi-daemon[5352]: Leaving mDNS multicast group on interface eth0.IPv4 with address 132.206.5.148.
Apr 19 19:37:52 kakyo-laptop avahi-daemon[5352]: Interface eth0.IPv4 no longer relevant for mDNS.
Apr 19 19:37:52 kakyo-laptop avahi-daemon[5352]: Joining mDNS multicast group on interface eth0.IPv4 with address 132.206.5.148.
Apr 19 19:37:52 kakyo-laptop avahi-daemon[5352]: New relevant interface eth0.IPv4 for mDNS.
Apr 19 19:37:52 kakyo-laptop avahi-daemon[5352]: Registering new address record for 132.206.5.148 on eth0.IPv4.
Apr 19 19:37:53 kakyo-laptop NetworkManager: <info>  Clearing nscd hosts cache. 
Apr 19 19:37:53 kakyo-laptop NetworkManager: <WARN>  nm_spawn_process(): nm_spawn_process('/usr/sbin/nscd -i hosts'): could not spawn process. (Failed to execute child process "/usr/sbin/nscd" (No such file or directory))  
Apr 19 19:37:53 kakyo-laptop NetworkManager: <info>  Activation (eth0) successful, device activated. 
Apr 19 19:37:53 kakyo-laptop NetworkManager: <info>  Activation (eth0) Finish handler scheduled. 
Apr 19 19:37:53 kakyo-laptop NetworkManager: <info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) complete. 
Apr 19 19:37:53 kakyo-laptop ntpd[6053]: ntpd exiting on signal 15
Apr 19 19:37:53 kakyo-laptop vmnetBridge: Daemon created. 
Apr 19 19:37:53 kakyo-laptop vmnetBridge: RTM_NEWLINK: name:eth0 index:2 flags:0x00011043 
Apr 19 19:37:53 kakyo-laptop vmnetBridge: Started bridge eth0 to virtual network 0. 
Apr 19 19:37:53 kakyo-laptop kernel: [   47.058286] /dev/vmnet: open called by PID 6331 (vmnet-bridge)
Apr 19 19:37:53 kakyo-laptop kernel: [   47.058295] /dev/vmnet: hub 0 does not exist, allocating memory.
Apr 19 19:37:53 kakyo-laptop kernel: [   47.058304] /dev/vmnet: port on hub 0 successfully opened
Apr 19 19:37:53 kakyo-laptop kernel: [   47.058317] bridge-eth0: up
Apr 19 19:37:53 kakyo-laptop kernel: [   47.058320] bridge-eth0: attached
Apr 19 19:37:53 kakyo-laptop kernel: [   47.136547] /dev/vmnet: open called by PID 6343 (vmnet-netifup)
Apr 19 19:37:53 kakyo-laptop kernel: [   47.136557] /dev/vmnet: hub 1 does not exist, allocating memory.
Apr 19 19:37:53 kakyo-laptop kernel: [   47.136567] /dev/vmnet: port on hub 1 successfully opened
Apr 19 19:37:53 kakyo-laptop avahi-daemon[5352]: Joining mDNS multicast group on interface vmnet1.IPv4 with address 192.168.176.1.
Apr 19 19:37:53 kakyo-laptop avahi-daemon[5352]: New relevant interface vmnet1.IPv4 for mDNS.
Apr 19 19:37:53 kakyo-laptop avahi-daemon[5352]: Registering new address record for 192.168.176.1 on vmnet1.IPv4.
Apr 19 19:37:53 kakyo-laptop vmnet-dhcpd: Internet Software Consortium DHCP Server 2.0
Apr 19 19:37:53 kakyo-laptop vmnet-dhcpd: Copyright 1995, 1996, 1997, 1998, 1999 The Internet Software Consortium.
Apr 19 19:37:53 kakyo-laptop vmnet-dhcpd: All rights reserved.
Apr 19 19:37:53 kakyo-laptop vmnet-dhcpd: 
Apr 19 19:37:53 kakyo-laptop vmnet-dhcpd: Please contribute if you find this software useful.
Apr 19 19:37:53 kakyo-laptop vmnet-dhcpd: For info, please visit http://www.isc.org/dhcp-contrib.html
Apr 19 19:37:53 kakyo-laptop vmnet-dhcpd: 
Apr 19 19:37:53 kakyo-laptop vmnet-dhcpd: Configured subnet: 192.168.176.0
Apr 19 19:37:53 kakyo-laptop vmnet-dhcpd: Setting vmnet-dhcp IP address: 192.168.176.254
Apr 19 19:37:53 kakyo-laptop vmnet-dhcpd: Recving on     VNet/vmnet1/192.168.176.0
Apr 19 19:37:53 kakyo-laptop vmnet-dhcpd: Sending on     VNet/vmnet1/192.168.176.0
Apr 19 19:37:53 kakyo-laptop kernel: [   47.230626] /dev/vmnet: open called by PID 6342 (vmnet-dhcpd)
Apr 19 19:37:53 kakyo-laptop kernel: [   47.230648] /dev/vmnet: port on hub 1 successfully opened
Apr 19 19:37:53 kakyo-laptop vmnetBridge: Daemon created. 
Apr 19 19:37:53 kakyo-laptop vmnet-dhcpd: Internet Software Consortium DHCP Server 2.0
Apr 19 19:37:53 kakyo-laptop vmnet-dhcpd: Copyright 1995, 1996, 1997, 1998, 1999 The Internet Software Consortium.
Apr 19 19:37:53 kakyo-laptop vmnet-dhcpd: All rights reserved.
Apr 19 19:37:53 kakyo-laptop vmnet-dhcpd: 
Apr 19 19:37:53 kakyo-laptop vmnet-dhcpd: Please contribute if you find this software useful.
Apr 19 19:37:53 kakyo-laptop vmnet-dhcpd: For info, please visit http://www.isc.org/dhcp-contrib.html
Apr 19 19:37:53 kakyo-laptop vmnet-dhcpd: 
Apr 19 19:37:53 kakyo-laptop vmnet-dhcpd: Configured subnet: 172.16.161.0
Apr 19 19:37:53 kakyo-laptop vmnet-dhcpd: Setting vmnet-dhcp IP address: 172.16.161.254
Apr 19 19:37:53 kakyo-laptop kernel: [   47.271476] /dev/vmnet: open called by PID 6377 (vmnet-dhcpd)
Apr 19 19:37:53 kakyo-laptop kernel: [   47.271494] /dev/vmnet: hub 8 does not exist, allocating memory.
Apr 19 19:37:53 kakyo-laptop kernel: [   47.271513] /dev/vmnet: port on hub 8 successfully opened
Apr 19 19:37:53 kakyo-laptop vmnet-dhcpd: Recving on     VNet/vmnet8/172.16.161.0
Apr 19 19:37:53 kakyo-laptop vmnet-dhcpd: Sending on     VNet/vmnet8/172.16.161.0
Apr 19 19:37:53 kakyo-laptop ntpdate[6320]: step time server 91.189.94.4 offset 0.966561 sec
Apr 19 19:37:54 kakyo-laptop kernel: [   47.295748] /dev/vmnet: open called by PID 6382 (vmnet-natd)
Apr 19 19:37:54 kakyo-laptop kernel: [   47.295767] /dev/vmnet: port on hub 8 successfully opened
Apr 19 19:37:54 kakyo-laptop ntpd[6464]: ntpd 4.2.4p4@1.1520-o Tue Jan  6 15:51:34 UTC 2009 (1)
Apr 19 19:37:54 kakyo-laptop ntpd[6472]: precision = 1.000 usec
Apr 19 19:37:54 kakyo-laptop ntpd[6472]: Listening on interface #0 wildcard, 0.0.0.0#123 Disabled
Apr 19 19:37:54 kakyo-laptop ntpd[6472]: Listening on interface #1 wildcard, ::#123 Disabled
Apr 19 19:37:54 kakyo-laptop ntpd[6472]: Listening on interface #2 lo, ::1#123 Enabled
Apr 19 19:37:54 kakyo-laptop ntpd[6472]: bind() fd 19, family 10, port 123, scope 3, addr fe80::250:56ff:fec0:1, in6_is_addr_multicast=0 flags=0x11 fails: Cannot assign requested address
Apr 19 19:37:54 kakyo-laptop ntpd[6472]: unable to create socket on vmnet1 (3) for fe80::250:56ff:fec0:1#123
Apr 19 19:37:54 kakyo-laptop ntpd[6472]: failed to initialize interface for address fe80::250:56ff:fec0:1
Apr 19 19:37:54 kakyo-laptop ntpd[6472]: bind() fd 19, family 10, port 123, scope 2, addr fe80::21e:68ff:fe99:1b73, in6_is_addr_multicast=0 flags=0x11 fails: Cannot assign requested address
Apr 19 19:37:54 kakyo-laptop ntpd[6472]: unable to create socket on eth0 (4) for fe80::21e:68ff:fe99:1b73#123
Apr 19 19:37:54 kakyo-laptop ntpd[6472]: failed to initialize interface for address fe80::21e:68ff:fe99:1b73
Apr 19 19:37:54 kakyo-laptop ntpd[6472]: Listening on interface #5 lo, 127.0.0.1#123 Enabled
Apr 19 19:37:54 kakyo-laptop ntpd[6472]: Listening on interface #6 eth0, 132.206.5.148#123 Enabled
Apr 19 19:37:54 kakyo-laptop ntpd[6472]: Listening on interface #7 vmnet1, 192.168.176.1#123 Enabled
Apr 19 19:37:54 kakyo-laptop ntpd[6472]: kernel time sync status 0040
Apr 19 19:37:54 kakyo-laptop ntpd[6472]: frequency initialized -80.772 PPM from /var/lib/ntp/ntp.drift
Apr 19 19:37:55 kakyo-laptop watchdog-webAccess: [6682] Begin '/usr/lib/vmware/webAccess/java/jre1.5.0_15/bin/webAccess -client -Xmx64m -XX:MinHeapFreeRatio=30 -XX:MaxHeapFreeRatio=30 -Djava.util.logging.manager=org.apache.juli.ClassLoaderLogManager -Djava.endorsed.dirs=/usr/lib/vmware/webAccess/tomcat/apache-tomcat-6.0.16/common/endorsed -classpath /usr/lib/vmware/webAccess/tomcat/apache-tomcat-6.0.16/bin/bootstrap.jar:/usr/lib/vmware/webAccess/tomcat/apache-tomcat-6.0.16/bin/commons-logging-api.jar -Dcatalina.base=/usr/lib/vmware/webAccess/tomcat/apache-tomcat-6.0.16 -Dcatalina.home=/usr/lib/vmware/webAccess/tomcat/apache-tomcat-6.0.16 -Djava.io.tmpdir=/usr/lib/vmware/webAccess/tomcat/apache-tomcat-6.0.16/temp org.apache.catalina.startup.Bootstrap start', min-uptime = 30, max-quick-failures = 5, max-total-failures = 1000000
Apr 19 19:37:55 kakyo-laptop watchdog-webAccess: Executing '/usr/lib/vmware/webAccess/java/jre1.5.0_15/bin/webAccess -client -Xmx64m -XX:MinHeapFreeRatio=30 -XX:MaxHeapFreeRatio=30 -Djava.util.logging.manager=org.apache.juli.ClassLoaderLogManager -Djava.endorsed.dirs=/usr/lib/vmware/webAccess/tomcat/apache-tomcat-6.0.16/common/endorsed -classpath /usr/lib/vmware/webAccess/tomcat/apache-tomcat-6.0.16/bin/bootstrap.jar:/usr/lib/vmware/webAccess/tomcat/apache-tomcat-6.0.16/bin/commons-logging-api.jar -Dcatalina.base=/usr/lib/vmware/webAccess/tomcat/apache-tomcat-6.0.16 -Dcatalina.home=/usr/lib/vmware/webAccess/tomcat/apache-tomcat-6.0.16 -Djava.io.tmpdir=/usr/lib/vmware/webAccess/tomcat/apache-tomcat-6.0.16/temp org.apache.catalina.startup.Bootstrap start'
Apr 19 19:37:55 kakyo-laptop avahi-daemon[5352]: Registering new address record for fe80::21e:68ff:fe99:1b73 on eth0.*.
Apr 19 19:37:55 kakyo-laptop ntpd[6472]: bind() fd 22, family 10, port 123, scope 3, addr fe80::250:56ff:fec0:1, in6_is_addr_multicast=0 flags=0x11 fails: Cannot assign requested address
Apr 19 19:37:55 kakyo-laptop ntpd[6472]: unable to create socket on vmnet1 (8) for fe80::250:56ff:fec0:1#123
Apr 19 19:37:55 kakyo-laptop ntpd[6472]: failed to initialize interface for address fe80::250:56ff:fec0:1
Apr 19 19:37:55 kakyo-laptop ntpd[6472]: Listening on interface #9 eth0, fe80::21e:68ff:fe99:1b73#123 Enabled
Apr 19 19:37:56 kakyo-laptop avahi-daemon[5352]: Registering new address record for fe80::250:56ff:fec0:1 on vmnet1.*.
Apr 19 19:38:03 kakyo-laptop kernel: [   52.951381] /dev/vmnet: open called by PID 6862 (vmnet-netifup)
Apr 19 19:38:03 kakyo-laptop kernel: [   52.951401] /dev/vmnet: port on hub 8 successfully opened
Apr 19 19:38:03 kakyo-laptop avahi-daemon[5352]: Joining mDNS multicast group on interface vmnet8.IPv4 with address 172.16.161.1.
Apr 19 19:38:03 kakyo-laptop avahi-daemon[5352]: New relevant interface vmnet8.IPv4 for mDNS.
Apr 19 19:38:03 kakyo-laptop avahi-daemon[5352]: Registering new address record for 172.16.161.1 on vmnet8.IPv4.
Apr 19 19:38:03 kakyo-laptop avahi-daemon[5352]: Withdrawing address record for 172.16.161.1 on vmnet8.
Apr 19 19:38:03 kakyo-laptop avahi-daemon[5352]: Leaving mDNS multicast group on interface vmnet8.IPv4 with address 172.16.161.1.
Apr 19 19:38:03 kakyo-laptop avahi-daemon[5352]: Interface vmnet8.IPv4 no longer relevant for mDNS.
Apr 19 19:38:03 kakyo-laptop avahi-daemon[5352]: Joining mDNS multicast group on interface vmnet8.IPv4 with address 172.16.161.1.
Apr 19 19:38:03 kakyo-laptop avahi-daemon[5352]: New relevant interface vmnet8.IPv4 for mDNS.
Apr 19 19:38:03 kakyo-laptop avahi-daemon[5352]: Registering new address record for 172.16.161.1 on vmnet8.IPv4.
Apr 19 19:38:04 kakyo-laptop kernel: [   53.377916] eth0: no IPv6 routers present
Apr 19 19:38:05 kakyo-laptop avahi-daemon[5352]: Registering new address record for fe80::250:56ff:fec0:8 on vmnet8.*.
Apr 19 19:38:05 kakyo-laptop kernel: [   53.834663] vmnet1: no IPv6 routers present
Apr 19 19:38:14 kakyo-laptop kernel: [   59.819328] vmnet8: no IPv6 routers present
Apr 19 19:38:18 kakyo-laptop pulseaudio[7061]: main.c: setrlimit(RLIMIT_NICE, (31, 31)) failed: Operation not permitted
Apr 19 19:38:18 kakyo-laptop pulseaudio[7061]: main.c: setrlimit(RLIMIT_RTPRIO, (9, 9)) failed: Operation not permitted
Apr 19 19:38:31 kakyo-laptop hcid[5926]: Default passkey agent (:1.28, /org/bluez/passkey) registered
Apr 19 19:38:31 kakyo-laptop hcid[5926]: Default authorization agent (:1.28, /org/bluez/auth) registered
Apr 19 19:38:58 kakyo-laptop NetworkManager: <info>  Updating allowed wireless network lists. 
Apr 19 19:38:58 kakyo-laptop NetworkManager: <info>  Updating VPN Connections... 
Apr 19 19:38:59 kakyo-laptop anacron[7330]: Anacron 2.3 started on 2009-04-19
Apr 19 19:38:59 kakyo-laptop anacron[7330]: Normal exit (0 jobs run)
Apr 19 19:38:59 kakyo-laptop kernel: [   83.542137] CPU0 attaching NULL sched-domain.
Apr 19 19:38:59 kakyo-laptop kernel: [   83.542150] CPU1 attaching NULL sched-domain.
Apr 19 19:38:59 kakyo-laptop kernel: [   83.555887] CPU0 attaching sched-domain:
Apr 19 19:38:59 kakyo-laptop kernel: [   83.555896]  domain 0: span 03
Apr 19 19:38:59 kakyo-laptop kernel: [   83.555900]   groups: 01 02
Apr 19 19:38:59 kakyo-laptop kernel: [   83.555906] CPU1 attaching sched-domain:
Apr 19 19:38:59 kakyo-laptop kernel: [   83.555909]  domain 0: span 03
Apr 19 19:38:59 kakyo-laptop kernel: [   83.555911]   groups: 02 01
Apr 19 19:38:59 kakyo-laptop anacron[7381]: Anacron 2.3 started on 2009-04-19
Apr 19 19:38:59 kakyo-laptop anacron[7381]: Normal exit (0 jobs run)
Apr 19 19:38:59 kakyo-laptop kernel: [   83.664130] CPU0 attaching NULL sched-domain.
Apr 19 19:38:59 kakyo-laptop kernel: [   83.664135] CPU1 attaching NULL sched-domain.
Apr 19 19:38:59 kakyo-laptop kernel: [   83.717969] CPU0 attaching sched-domain:
Apr 19 19:38:59 kakyo-laptop kernel: [   83.717978]  domain 0: span 03
Apr 19 19:38:59 kakyo-laptop kernel: [   83.717981]   groups: 01 02
Apr 19 19:38:59 kakyo-laptop kernel: [   83.717987] CPU1 attaching sched-domain:
Apr 19 19:38:59 kakyo-laptop kernel: [   83.717990]  domain 0: span 03
Apr 19 19:38:59 kakyo-laptop kernel: [   83.717993]   groups: 02 01
Apr 19 19:39:03 kakyo-laptop gnome-power-manager: (kakyo) Power Manager is already running in this session.
Apr 19 19:39:22 kakyo-laptop scim-bridge: Failed to open the panel socket
Apr 19 19:39:22 kakyo-laptop scim-bridge: Failed to open the panel socket
Apr 19 19:40:05 kakyo-laptop kernel: [  142.962597] nautilus[7084]: segfault at 00000084 eip b751c694 esp bfced0d0 error 4

```

---

### Post by kakyoism on 2009-04-19
bump!

---

### Post by kakyoism on 2009-04-20
bump again!

---

### Post by kakyoism on 2009-04-20
bump * 3

---

### Post by Rzulf on 2009-04-21
Same problem here, it's strange because it used to work fine, just yesterday :/

---

### Post by jerich007 on 2009-04-21
I have the same problem on my T61 thinkpad.  Seems after one of the last updates (kernel maybe???) my resume failed.  Help!

---

### Post by Rzulf on 2009-04-21
bump!!!!!

---

### Post by kakyoism on 2009-04-21
ok, thx guys, more bumps please!!!

---

### Post by cubeist on 2009-04-21
I also cannot resume from suspend, but I know it is an ati/compiz conflict and I have had it since hardy heron...

If you are running compiz, try the command:
```
metacity --replace
```
before suspending.

---

### Post by kakyoism on 2009-04-21
thanks cubeist! seems to do the trick for me, but mine is an intel card, could you explain why it's an ati problem??

---

### Post by kakyoism on 2009-04-21
btw, what's the commandline to switch back to compiz??

---

### Post by kakyoism on 2009-04-21
UPDATES:

After successfully resume from suspend a minute ago under metacity, I just tried to switch back to compiz with "compiz --replace", and see an error message, to which a solution is given here:
[https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/209207]("https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/209207")

I followed the suggestion in the original bug report, i.e., run command:
```
gconftool-2 -s -t string /apps/compiz/plugins/scale/allscreens/options/initiate_edge Disabled
```

Now it seems that my suspend/resume cycle is back on under compiz.

Please try this and let everybody know what's happening!

---

### Post by cubeist on 2009-04-21
> **kakyoism said:**
> thanks cubeist! seems to do the trick for me, but mine is an intel card, could you explain why it's an ati problem??

well it is an ati problem for me! for you it is an intel driver problem...
Actually I think the problem lies in compiz not communicating with the driver on resume, thus nobody is there to draw the windows/desktop, and it freezes.  Metacity and/or nvidia don't have this problem.

---

### Post by ohiomoto on 2009-04-21
My Dell Vostro has a NVIDIA card and I am NOT running compiz (though it is on my computer) and I am having the same issue.  Seems to have started sometime around my last batch of updates.  Maybe around the time I started using the latest NVIDA restricted driver.

---

### Post by ohiomoto on 2009-04-21
Maybe my problem is a little different.  To be clear, my computer does resume, but I'm stuck on my blank screen (my screen saver) without the prompt to unlock the screen.  

I switched back to the previous NVIDIA driver and everything works fine again.  

I hope this helps someone with a similar problem.

---

### Post by cubeist on 2009-04-21
> **cubeist said:**
> well it is an ati problem for me! for you it is an intel driver problem...
Actually I think the problem lies in compiz not communicating with the driver on resume, thus nobody is there to draw the windows/desktop, and it freezes.  Metacity and/or nvidia don't have this problem.

my problem is this one:
[https://bugs.launchpad.net/fglrx/+bug/197209](https://bugs.launchpad.net/fglrx/+bug/197209)

---

### Post by Rzulf on 2009-04-22
> **kakyoism said:**
> UPDATES:

After successfully resume from suspend a minute ago under metacity, I just tried to switch back to compiz with "compiz --replace", and see an error message, to which a solution is given here:
[https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/209207]("https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/209207")

I followed the suggestion in the original bug report, i.e., run command:
```
gconftool-2 -s -t string /apps/compiz/plugins/scale/allscreens/options/initiate_edge Disabled
```

Now it seems that my suspend/resume cycle is back on under compiz.

Please try this and let everybody know what's happening!

It worked for me :) thanks :D

PS. I have NVidia card with the newest driver.

---

