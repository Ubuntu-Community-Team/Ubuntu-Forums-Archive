---
title: "[suspend] VAIO can't resume... was working before!!!"
date: 2008-08-08
forum: Hardware
---

### Post by kakyoism on 2008-08-08
I can't resume my laptop (see sig.) again. It worked perfectly before except that I had to press the spacebar a lot to get a response. 

Now it never worked. I tried to switch to another console log-in, but nothing happened; so I guess the keyboard wasn't working at all.

Help.......going crazy!

Here is the dmesg before suspend:
```
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Linux version 2.6.24-19-rt (buildd@terranova) (gcc version 4.2.3 (Ubuntu 4.2.3-2ubuntu7)) #1 SMP PREEMPT RT Sat Jul 12 02:53:01 UTC 2008 (Ubuntu 2.6.24-4.6-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
[    0.000000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000dc000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 00000000bf6d0000 (usable)
[    0.000000]  BIOS-e820: 00000000bf6d0000 - 00000000bf6e0000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000bf6e0000 - 00000000bf6e3000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000bf6e3000 - 00000000c0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed00000 - 00000000fed00400 (reserved)
[    0.000000]  BIOS-e820: 00000000fed14000 - 00000000fed1a000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed1c000 - 00000000fed90000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000ff000000 - 0000000100000000 (reserved)
[    0.000000]  BIOS-e820: 0000000100000000 - 0000000140000000 (usable)
[    0.000000] Warning only 4GB will be used.
[    0.000000] Use a HIGHMEM64G enabled kernel.
[    0.000000] 3200MB HIGHMEM available.
[    0.000000] 896MB LOWMEM available.
[    0.000000] found SMP MP-table at 000f8080
[    0.000000] Entering add_active_range(0, 0, 1048576) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   229376
[    0.000000]   HighMem    229376 ->  1048576
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->  1048576
[    0.000000] On node 0 totalpages: 1048576
[    0.000000]   DMA zone: 56 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4040 pages, LIFO batch:0
[    0.000000]   Normal zone: 3080 pages used for memmap
[    0.000000]   Normal zone: 222200 pages, LIFO batch:31
[    0.000000]   HighMem zone: 11200 pages used for memmap
[    0.000000]   HighMem zone: 808000 pages, LIFO batch:31
[    0.000000]   Movable zone: 0 pages used for memmap
[    0.000000] DMI present.
[    0.000000] ACPI: RSDP signature @ 0xC00F8050 checksum 0
[    0.000000] ACPI: RSDP 000F8050, 0024 (r2 PTLTD )
[    0.000000] ACPI: XSDT BF6D7E92, 008C (r1   Sony     VAIO 20071023 PTL         0)
[    0.000000] ACPI: FACP BF6DFC04, 00F4 (r3   Sony     VAIO 20071023 PTL         1)
[    0.000000] ACPI: DSDT BF6D9217, 6979 (r2   Sony     VAIO 20071023 PTL  20050624)
[    0.000000] ACPI: FACS BF6E2FC0, 0040
[    0.000000] ACPI: APIC BF6DFCF8, 0068 (r1   Sony     VAIO 20071023 PTL        5A)
[    0.000000] ACPI: HPET BF6DFD60, 0038 (r1   Sony     VAIO 20071023 PTL        5A)
[    0.000000] ACPI: MCFG BF6DFD98, 003C (r1   Sony     VAIO 20071023 PTL        5A)
[    0.000000] ACPI: SLIC BF6DFDD4, 0176 (r1   Sony     VAIO 20071023 PTL   1000000)
[    0.000000] ACPI: TMOR BF6DFF4A, 0026 (r1   Sony     VAIO 20071023 PTL         3)
[    0.000000] ACPI: APIC BF6DFF70, 0068 (r1   Sony     VAIO 20071023 PTL         0)
[    0.000000] ACPI: BOOT BF6DFFD8, 0028 (r1   Sony     VAIO 20071023 PTL         1)
[    0.000000] ACPI: SSDT BF6D90FA, 011D (r1   Sony     VAIO 20071023 PTL  20050624)
[    0.000000] ACPI: SSDT BF6D8FD7, 0123 (r1   Sony     VAIO 20071023 PTL  20050624)
[    0.000000] ACPI: SSDT BF6D8506, 0287 (r1   Sony     VAIO 20071023 PTL  20050624)
[    0.000000] ACPI: SSDT BF6D8452, 00B4 (r1   Sony     VAIO 20071023 PTL  20050624)
[    0.000000] ACPI: SSDT BF6D7F1E, 0534 (r1   Sony     VAIO 20071023 PTL  20050624)
[    0.000000] ACPI: BIOS bug: multiple APIC/MADT found, using 0
[    0.000000] ACPI: If "acpi_apic_instance=2" works better, notify linux-acpi@vger.kernel.org
[    0.000000] ACPI: DMI detected: Sony
[    0.000000] ACPI: PM-Timer IO Port: 0x1008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] Processor #0 6:15 APIC version 20
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
[    0.000000] Processor #1 6:15 APIC version 20
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 1, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
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
[    0.000000] Real-Time Preemption Support (C) 2004-2007 Ingo Molnar
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 1034240
[    0.000000] Kernel command line: root=UUID=1bebd1ca-6b65-462d-baf2-211248477bcb ro quiet splash
[    0.000000] mapped APIC to ffffb000 (fee00000)
[    0.000000] mapped IOAPIC to ffffa000 (fec00000)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] Detected 1828.828 MHz processor.
[   13.438472] Console: colour VGA+ 80x25
[   13.438475] console [tty0] enabled
[   13.438762] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[   13.439050] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[   13.667973] Memory: 3064700k/4194304k available (2225k kernel code, 70344k reserved, 1059k data, 368k init, 2218816k highmem)
[   13.667980] virtual kernel memory layout:
[   13.667981]     fixmap  : 0xfff4b000 - 0xfffff000   ( 720 kB)
[   13.667982]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   13.667983]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
[   13.667984]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
[   13.667985]       .init : 0xc043b000 - 0xc0497000   ( 368 kB)
[   13.667986]       .data : 0xc032c6a0 - 0xc0435324   (1059 kB)
[   13.667987]       .text : 0xc0100000 - 0xc032c6a0   (2225 kB)
[   13.667990] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   13.668254] hpet clockevent registered
[   13.728158] Calibrating delay using timer specific routine.. 3660.61 BogoMIPS (lpj=1830307)
[   13.728203] Security Framework initialized
[   13.728210] SELinux:  Disabled at boot.
[   13.728218] AppArmor: AppArmor initialized
[   13.728222] Failure registering capabilities with primary security module.
[   13.728238] Mount-cache hash table entries: 512
[   13.728383] Initializing cgroup subsys ns
[   13.728387] Initializing cgroup subsys cpuacct
[   13.728399] CPU: After generic identify, caps: bfebfbff 20100000 00000000 00000000 0000e39d 00000000 00000001 00000000
[   13.728407] monitor/mwait feature present.
[   13.728408] using mwait in idle threads.
[   13.728412] CPU: L1 I cache: 32K, L1 D cache: 32K
[   13.728414] CPU: L2 cache: 2048K
[   13.728417] CPU: Physical Processor ID: 0
[   13.728419] CPU: Processor Core ID: 0
[   13.728421] CPU: After all inits, caps: bfebfbff 20100000 00000000 00003940 0000e39d 00000000 00000001 00000000
[   13.728430] Compat vDSO mapped to ffffe000.
[   13.728442] Checking 'hlt' instruction... OK.
[   13.732518] SMP alternatives: switching to UP code
[   13.733720] Early unpacking initramfs... done
[   14.065086] ACPI: Core revision 20070126
[   14.065138] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[   14.077034] CPU0: Intel(R) Core(TM)2 Duo CPU     T5550  @ 1.83GHz stepping 0d
[   14.077052] SMP alternatives: switching to SMP code
[   14.077618] Booting processor 1/1 eip 3000
[   14.087850] Initializing CPU#1
[   14.148440] Calibrating delay using timer specific routine.. 3657.48 BogoMIPS (lpj=1828740)
[   14.148447] CPU: After generic identify, caps: bfebfbff 20100000 00000000 00000000 0000e39d 00000000 00000001 00000000
[   14.148452] monitor/mwait feature present.
[   14.148455] CPU: L1 I cache: 32K, L1 D cache: 32K
[   14.148457] CPU: L2 cache: 2048K
[   14.148459] CPU: Physical Processor ID: 0
[   14.148460] CPU: Processor Core ID: 1
[   14.148462] CPU: After all inits, caps: bfebfbff 20100000 00000000 00003940 0000e39d 00000000 00000001 00000000
[   14.148931] CPU1: Intel(R) Core(TM)2 Duo CPU     T5550  @ 1.83GHz stepping 0d
[   14.148953] Total of 2 processors activated (7318.09 BogoMIPS).
[   14.149146] ENABLING IO-APIC IRQs
[   14.149340] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[   14.260883] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
[   14.280881] Brought up 2 CPUs
[   14.280904] CPU0 attaching sched-domain:
[   14.280907]  domain 0: span 03
[   14.280909]   groups: 01 02
[   14.280913] CPU1 attaching sched-domain:
[   14.280914]  domain 0: span 03
[   14.280916]   groups: 02 01
[   14.281137] net_namespace: 76 bytes
[   14.281146] Booting paravirtualized kernel on bare hardware
[   14.281603] Time: 16:16:42  Date: 08/08/08
[   14.281643] NET: Registered protocol family 16
[   14.281848] EISA bus registered
[   14.281853] ACPI: bus type pci registered
[   14.282345] PCI: PCI BIOS revision 3.00 entry at 0xfddf1, last bus=9
[   14.282347] PCI: Using configuration type 1
[   14.282363] Setting up standard PCI resources
[   14.285365] ACPI: EC: Look up EC in DSDT
[   14.293011] ACPI: BIOS _OSI(Linux) query ignored via DMI
[   14.293014] ACPI: If "acpi_osi=Linux" works better, please notify linux-acpi@vger.kernel.org
[   14.294352] ACPI: Interpreter enabled
[   14.294355] ACPI: (supports S0 S3 S4 S5)
[   14.294373] ACPI: Using IOAPIC for interrupt routing
[   14.294758] ACPI: EC: non-query interrupt received, switching to interrupt mode
[   14.314626] ACPI: EC: GPE = 0x17, I/O: command/status = 0x66, data = 0x62
[   14.314629] ACPI: EC: driver started in interrupt mode
[   14.314676] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   14.315735] PCI quirk: region 1000-107f claimed by ICH6 ACPI/GPIO/TCO
[   14.315739] PCI quirk: region 1180-11bf claimed by ICH6 GPIO
[   14.316946] PCI: Transparent bridge - 0000:00:1e.0
[   14.317046] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   14.317439] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP01._PRT]
[   14.317587] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP02._PRT]
[   14.317734] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP03._PRT]
[   14.317907] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIB._PRT]
[   14.355788] ACPI: PCI Interrupt Link [LNKA] (IRQs 1 3 4 *5 6 7 10 12 14 15)
[   14.355899] ACPI: PCI Interrupt Link [LNKB] (IRQs 1 3 4 5 6 7 11 12 14 15) *10
[   14.356006] ACPI: PCI Interrupt Link [LNKC] (IRQs 1 3 4 5 6 *7 10 12 14 15)
[   14.356112] ACPI: PCI Interrupt Link [LNKD] (IRQs 1 3 4 5 6 7 11 12 14 15) *10
[   14.356219] ACPI: PCI Interrupt Link [LNKE] (IRQs 1 3 4 5 6 7 10 12 14 15) *0, disabled.
[   14.356326] ACPI: PCI Interrupt Link [LNKF] (IRQs 1 3 4 5 6 7 *11 12 14 15)
[   14.356432] ACPI: PCI Interrupt Link [LNKG] (IRQs 1 3 4 5 6 7 10 12 14 15) *11
[   14.356538] ACPI: PCI Interrupt Link [LNKH] (IRQs 1 3 4 5 6 7 11 12 14 15) *10
[   14.356703] Linux Plug and Play Support v0.97 (c) Adam Belay
[   14.356742] pnp: PnP ACPI init
[   14.356750] ACPI: bus type pnp registered
[   14.364267] pnp: PnP ACPI: found 10 devices
[   14.364269] ACPI: ACPI bus type pnp unregistered
[   14.364273] PnPBIOS: Disabled by ACPI PNP
[   14.364498] PCI: Using ACPI for IRQ routing
[   14.364501] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   14.472896] NET: Registered protocol family 8
[   14.472899] NET: Registered protocol family 20
[   14.472943] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[   14.472947] hpet0: 3 64-bit timers, 14318180 Hz
[   14.474005] AppArmor: AppArmor Filesystem Enabled
[   14.481266] system 00:01: iomem range 0xfed1c000-0xfed1ffff could not be reserved
[   14.481269] system 00:01: iomem range 0xfed14000-0xfed17fff could not be reserved
[   14.481272] system 00:01: iomem range 0xfed18000-0xfed18fff could not be reserved
[   14.481275] system 00:01: iomem range 0xfed19000-0xfed19fff could not be reserved
[   14.481278] system 00:01: iomem range 0xe0000000-0xefffffff could not be reserved
[   14.481281] system 00:01: iomem range 0xfed20000-0xfed3ffff could not be reserved
[   14.481284] system 00:01: iomem range 0xfed40000-0xfed44fff could not be reserved
[   14.481287] system 00:01: iomem range 0xfed45000-0xfed8ffff could not be reserved
[   14.481295] system 00:04: iomem range 0xfed00000-0xfed003ff could not be reserved
[   14.481301] system 00:06: ioport range 0x680-0x69f has been reserved
[   14.481304] system 00:06: ioport range 0x800-0x80f has been reserved
[   14.481307] system 00:06: ioport range 0x1000-0x107f has been reserved
[   14.481309] system 00:06: ioport range 0x1180-0x11bf has been reserved
[   14.481312] system 00:06: ioport range 0x1640-0x164f has been reserved
[   14.481315] system 00:06: ioport range 0xfe00-0xfe7f has been reserved
[   14.481317] system 00:06: ioport range 0xfe80-0xfeff has been reserved
[   14.511716] PCI: Bridge: 0000:00:1c.0
[   14.511720]   IO window: 2000-2fff
[   14.511726]   MEM window: f6000000-f7ffffff
[   14.511731]   PREFETCH window: f0000000-f1ffffff
[   14.511737] PCI: Bridge: 0000:00:1c.1
[   14.511741]   IO window: 3000-3fff
[   14.511747]   MEM window: f8000000-f9ffffff
[   14.511752]   PREFETCH window: f2000000-f3ffffff
[   14.511758] PCI: Bridge: 0000:00:1c.2
[   14.511761]   IO window: 4000-4fff
[   14.511767]   MEM window: fa000000-fbffffff
[   14.511772]   PREFETCH window: f4000000-f5ffffff
[   14.511784] PCI: Bus 9, cardbus bridge: 0000:08:03.0
[   14.511786]   IO window: 00001400-000014ff
[   14.511791]   IO window: 00005000-000050ff
[   14.511796]   PREFETCH window: c4000000-c7ffffff
[   14.511802]   MEM window: c8000000-cbffffff
[   14.511807] PCI: Bridge: 0000:00:1e.0
[   14.511808]   IO window: disabled.
[   14.511814]   MEM window: fc200000-fc2fffff
[   14.511819]   PREFETCH window: disabled.
[   14.511851] ACPI: PCI Interrupt 0000:00:1c.0[A] -> GSI 17 (level, low) -> IRQ 16
[   14.511858] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[   14.511884] ACPI: PCI Interrupt 0000:00:1c.1[B] -> GSI 16 (level, low) -> IRQ 17
[   14.511890] PCI: Setting latency timer of device 0000:00:1c.1 to 64
[   14.511916] ACPI: PCI Interrupt 0000:00:1c.2[C] -> GSI 18 (level, low) -> IRQ 18
[   14.511922] PCI: Setting latency timer of device 0000:00:1c.2 to 64
[   14.511943] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[   14.511962] ACPI: PCI Interrupt 0000:08:03.0[A] -> GSI 16 (level, low) -> IRQ 17
[   14.511993] NET: Registered protocol family 2
[   14.546942] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[   14.547186] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[   14.547712] TCP bind hash table entries: 65536 (order: 9, 2359296 bytes)
[   14.548968] TCP: Hash tables configured (established 131072 bind 65536)
[   14.548972] TCP reno registered
[   14.560277] checking if image is initramfs... it is
[   15.221570] Freeing initrd memory: 7696k freed
[   15.221727] Simple Boot Flag at 0x36 set to 0x1
[   15.222455] audit: initializing netlink socket (disabled)
[   15.222468] audit(1218212202.367:1): initialized
[   15.222530] krcupreemptd setsched 0
[   15.222532]   prio = 98
[   15.222707] highmem bounce pool size: 64 pages
[   15.222784] VFS: Disk quotas dquot_6.5.1
[   15.222809] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   15.222907] io scheduler noop registered
[   15.222909] io scheduler anticipatory registered
[   15.222911] io scheduler deadline registered
[   15.222921] io scheduler cfq registered (default)
[   15.222933] Boot video device is 0000:00:02.0
[   15.223181] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[   15.223245] assign_interrupt_mode Found MSI capability
[   15.223299] Allocate Port Service[0000:00:1c.0:pcie00]
[   15.223335] Allocate Port Service[0000:00:1c.0:pcie02]
[   15.223442] PCI: Setting latency timer of device 0000:00:1c.1 to 64
[   15.223506] assign_interrupt_mode Found MSI capability
[   15.223555] Allocate Port Service[0000:00:1c.1:pcie00]
[   15.223589] Allocate Port Service[0000:00:1c.1:pcie02]
[   15.223697] PCI: Setting latency timer of device 0000:00:1c.2 to 64
[   15.223760] assign_interrupt_mode Found MSI capability
[   15.223810] Allocate Port Service[0000:00:1c.2:pcie00]
[   15.223843] Allocate Port Service[0000:00:1c.2:pcie02]
[   15.224150] isapnp: Scanning for PnP cards...
[   15.581021] isapnp: No Plug & Play device found
[   15.607319] Real Time Clock Driver v1.12ac
[   15.607561] hpet_resources: 0xfed00000 is busy
[   15.607589] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   15.608964] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   15.609033] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[   15.609133] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[   15.612358] i8042.c: Detected active multiplexing controller, rev 1.1.
[   15.615899] serio: i8042 KBD port at 0x60,0x64 irq 1
[   15.615903] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[   15.615906] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[   15.615908] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[   15.615910] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[   15.624399] mice: PS/2 mouse device common for all mice
[   15.624520] EISA: Probing bus 0 at eisa.0
[   15.624528] Cannot allocate resource for EISA slot 1
[   15.624531] Cannot allocate resource for EISA slot 2
[   15.624533] Cannot allocate resource for EISA slot 3
[   15.624535] Cannot allocate resource for EISA slot 4
[   15.624537] Cannot allocate resource for EISA slot 5
[   15.624553] EISA: Detected 0 cards.
[   15.624556] cpuidle: using governor ladder
[   15.624630] NET: Registered protocol family 1
[   15.624657] Using IPI No-Shortcut mode
[   15.624691] registered taskstats version 1
[   15.624818]   Magic number: 4:30:287
[   15.624831]   hash matches device ttyz1
[   15.624889]   hash matches device tty20
[   15.624906] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[   15.624908] EDD information not available.
[   15.625099] Freeing unused kernel memory: 368k freed
[   15.827760] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[   16.867067] fuse init (API version 7.9)
[   16.880512] ACPI: SSDT BF6D8CD6, 021D (r1   Sony     VAIO 20071023 PTL  20050624)
[   16.880749] ACPI: SSDT BF6D878D, 04B7 (r1   Sony     VAIO 20071023 PTL  20050624)
[   16.883336] Monitor-Mwait will be used to enter C-1 state
[   16.883339] Monitor-Mwait will be used to enter C-2 state
[   16.883341] Monitor-Mwait will be used to enter C-3 state
[   16.883470] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[   16.883475] ACPI: Processor [CPU0] (supports 8 throttling states)
[   16.884280] ACPI: SSDT BF6D8EF3, 00E4 (r1   Sony     VAIO 20071023 PTL  20050624)
[   16.884519] ACPI: SSDT BF6D8C44, 0092 (r1   Sony     VAIO 20071023 PTL  20050624)
[   16.885808] ACPI: CPU1 (power states: C1[C1] C2[C2] C3[C3])
[   16.885814] ACPI: Processor [CPU1] (supports 8 throttling states)
[   16.888120] ACPI: Thermal Zone [TZ00] (58 C)
[   16.889072] ACPI Exception (thermal-0471): AE_NOT_FOUND, Invalid active threshold [0] [20070126]
[   16.889120] ACPI Exception (thermal-0471): AE_NOT_FOUND, Invalid active threshold [1] [20070126]
[   16.889692] ACPI: Thermal Zone [TZ01] (58 C)
[   17.077834] usbcore: registered new interface driver usbfs
[   17.077856] usbcore: registered new interface driver hub
[   17.078427] usbcore: registered new device driver usb
[   17.080282] USB Universal Host Controller Interface driver v3.0
[   17.080323] ACPI: PCI Interrupt 0000:00:1a.0[A] -> GSI 16 (level, low) -> IRQ 17
[   17.080334] PCI: Setting latency timer of device 0000:00:1a.0 to 64
[   17.080339] uhci_hcd 0000:00:1a.0: UHCI Host Controller
[   17.080647] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 1
[   17.080705] uhci_hcd 0000:00:1a.0: irq 17, io base 0x00001820
[   17.080842] usb usb1: configuration #1 chosen from 1 choice
[   17.080867] hub 1-0:1.0: USB hub found
[   17.080873] hub 1-0:1.0: 2 ports detected
[   17.181304] ACPI: PCI Interrupt 0000:00:1a.1[B] -> GSI 21 (level, low) -> IRQ 19
[   17.181316] PCI: Setting latency timer of device 0000:00:1a.1 to 64
[   17.181321] uhci_hcd 0000:00:1a.1: UHCI Host Controller
[   17.181349] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 2
[   17.181430] uhci_hcd 0000:00:1a.1: irq 19, io base 0x00001840
[   17.181549] usb usb2: configuration #1 chosen from 1 choice
[   17.181572] hub 2-0:1.0: USB hub found
[   17.181578] hub 2-0:1.0: 2 ports detected
[   17.282167] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 23 (level, low) -> IRQ 20
[   17.282179] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[   17.282184] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[   17.282209] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 3
[   17.282383] uhci_hcd 0000:00:1d.0: irq 20, io base 0x00001860
[   17.282501] usb usb3: configuration #1 chosen from 1 choice
[   17.282526] hub 3-0:1.0: USB hub found
[   17.282533] hub 3-0:1.0: 2 ports detected
[   17.383007] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 19 (level, low) -> IRQ 21
[   17.383020] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[   17.383024] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[   17.383049] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 4
[   17.383315] uhci_hcd 0000:00:1d.1: irq 21, io base 0x00001880
[   17.383449] usb usb4: configuration #1 chosen from 1 choice
[   17.383472] hub 4-0:1.0: USB hub found
[   17.383479] hub 4-0:1.0: 2 ports detected
[   17.483844] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 18
[   17.483857] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[   17.483861] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[   17.483886] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 5
[   17.483973] uhci_hcd 0000:00:1d.2: irq 18, io base 0x000018a0
[   17.484091] usb usb5: configuration #1 chosen from 1 choice
[   17.484115] hub 5-0:1.0: USB hub found
[   17.484121] hub 5-0:1.0: 2 ports detected
[   19.154180] SCSI subsystem initialized
[   19.510635] libata version 3.00 loaded.
[   19.536295] ata_piix 0000:00:1f.1: version 2.12
[   19.536313] ACPI: PCI Interrupt 0000:00:1f.1[A] -> GSI 19 (level, low) -> IRQ 21
[   19.536347] PCI: Setting latency timer of device 0000:00:1f.1 to 64
[   19.536446] scsi0 : ata_piix
[   19.536492] scsi1 : ata_piix
[   19.537328] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0x1810 irq 14
[   19.537331] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x1818 irq 15
[   19.842409] ata1.00: ATAPI: Optiarc DVD RW AD-7560A, DS02, max UDMA/33
[   19.999131] ata1.00: configured for UDMA/33
[   20.161609] scsi 0:0:0:0: CD-ROM            Optiarc  DVD RW AD-7560A  DS02 PQ: 0 ANSI: 5
[   20.162537] ACPI: PCI Interrupt 0000:00:1a.7[C] -> GSI 18 (level, low) -> IRQ 18
[   20.162550] PCI: Setting latency timer of device 0000:00:1a.7 to 64
[   20.162554] ehci_hcd 0000:00:1a.7: EHCI Host Controller
[   20.162584] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 6
[   20.166498] ehci_hcd 0000:00:1a.7: debug port 1
[   20.166506] PCI: cache line size of 32 is not supported by device 0000:00:1a.7
[   20.166513] ehci_hcd 0000:00:1a.7: irq 18, io mem 0xfc504800
[   20.175751] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   20.175861] usb usb6: configuration #1 chosen from 1 choice
[   20.175886] hub 6-0:1.0: USB hub found
[   20.175900] hub 6-0:1.0: 4 ports detected
[   20.276525] ACPI: PCI Interrupt 0000:00:1d.7[A] -> GSI 23 (level, low) -> IRQ 20
[   20.276538] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[   20.276542] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[   20.276588] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 7
[   20.280480] ehci_hcd 0000:00:1d.7: debug port 1
[   20.280487] PCI: cache line size of 32 is not supported by device 0000:00:1d.7
[   20.280492] ehci_hcd 0000:00:1d.7: irq 20, io mem 0xfc504c00
[   20.290329] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   20.290530] usb usb7: configuration #1 chosen from 1 choice
[   20.290568] hub 7-0:1.0: USB hub found
[   20.290575] hub 7-0:1.0: 6 ports detected
[   20.347224] Clocksource tsc unstable (delta = -871860172 ns)
[   20.358336] ahci 0000:00:1f.2: version 3.0
[   20.358359] ACPI: PCI Interrupt 0000:00:1f.2[B] -> GSI 19 (level, low) -> IRQ 21
[   20.358407] ahci 0000:00:1f.2: nr_ports (3) and implemented port map (0x1) don't match, using nr_ports
[   20.358410] ahci 0000:00:1f.2: forcing PORTS_IMPL to 0x7
[   20.414472] usb 7-2: new high speed USB device using ehci_hcd and address 2
[   20.529092] usb 7-2: configuration #1 chosen from 1 choice
[   20.529227] hub 7-2:1.0: USB hub found
[   20.529302] hub 7-2:1.0: 4 ports detected
[   20.877425] usb 7-2.1: new high speed USB device using ehci_hcd and address 4
[   20.966987] usb 7-2.1: configuration #1 chosen from 1 choice
[   20.999154] ahci 0000:00:1f.2: AHCI 0001.0100 32 slots 3 ports 3 Gbps 0x7 impl SATA mode
[   20.999158] ahci 0000:00:1f.2: flags: 64bit ncq sntf pm led clo pio slum part
[   20.999163] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[   20.999415] scsi2 : ahci
[   20.999598] scsi3 : ahci
[   20.999762] scsi4 : ahci
[   20.999823] ata3: SATA max UDMA/133 abar m2048@0xfc504000 port 0xfc504100 irq 220
[   20.999826] ata4: SATA max UDMA/133 abar m2048@0xfc504000 port 0xfc504180 irq 220
[   20.999830] ata5: SATA max UDMA/133 abar m2048@0xfc504000 port 0xfc504200 irq 220
[   21.143980] usb 7-2.2: new high speed USB device using ehci_hcd and address 5
[   21.231679] usb 7-2.2: configuration #1 chosen from 1 choice
[   21.432438] usb 4-2: new low speed USB device using uhci_hcd and address 2
[   21.436430] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[   21.437429] ata3.00: ATA-8: Hitachi HTS542525K9SA00, BBFOC3BP, max UDMA/133
[   21.437432] ata3.00: 488397168 sectors, multi 16: LBA48 NCQ (depth 31/32)
[   21.438650] ata3.00: configured for UDMA/133
[   21.467346] usb 4-2: configuration #1 chosen from 1 choice
[   21.488316] usbcore: registered new interface driver hiddev
[   21.495318] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:1d.1/usb4/4-2/4-2:1.0/input/input2
[   21.499206] input,hidraw0: USB HID v1.11 Mouse [Logitech USB Receiver] on usb-0000:00:1d.1-2
[   21.508353] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:1d.1/usb4/4-2/4-2:1.1/input/input3
[   21.509841] input,hiddev96,hidraw1: USB HID v1.11 Device [Logitech USB Receiver] on usb-0000:00:1d.1-2
[   21.509857] usbcore: registered new interface driver usbhid
[   21.509861] /build/buildd/linux-2.6.24/debian/build/custom-source-rt/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
[   21.537017] ata4: SATA link down (SStatus 0 SControl 0)
[   21.598051] ata5: SATA link down (SStatus 0 SControl 0)
[   21.598211] scsi 2:0:0:0: Direct-Access     ATA      Hitachi HTS54252 BBFO PQ: 0 ANSI: 5
[   21.598826] ACPI: PCI Interrupt 0000:08:03.1[B] -> GSI 17 (level, low) -> IRQ 16
[   21.649529] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[16]  MMIO=[fc206000-fc2067ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[   21.658533] Driver 'sd' needs updating - please use bus_type methods
[   21.658619] sd 2:0:0:0: [sda] 488397168 512-byte hardware sectors (250059 MB)
[   21.658632] sd 2:0:0:0: [sda] Write Protect is off
[   21.658635] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   21.658653] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   21.658703] sd 2:0:0:0: [sda] 488397168 512-byte hardware sectors (250059 MB)
[   21.658714] sd 2:0:0:0: [sda] Write Protect is off
[   21.658716] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   21.658734] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   21.658739]  sda:<6>usbcore: registered new interface driver libusual
[   21.673531] Driver 'sr' needs updating - please use bus_type methods
[   21.677080]  sda1 sda2 <<6>Initializing USB Mass Storage driver...
[   21.680648] scsi5 : SCSI emulation for USB Mass Storage devices
[   21.680713] usb-storage: device found at 4
[   21.680715] usb-storage: waiting for device to settle before scanning
[   21.680746] scsi6 : SCSI emulation for USB Mass Storage devices
[   21.680805] usbcore: registered new interface driver usb-storage
[   21.680808] USB Mass Storage support registered.
[   21.680929] usb-storage: device found at 5
[   21.680931] usb-storage: waiting for device to settle before scanning
[   21.683579] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[   21.683584] Uniform CD-ROM driver Revision: 3.20
[   21.683633] sr 0:0:0:0: Attached scsi CD-ROM sr0
[   21.701115]  sda5 >
[   21.701215] sd 2:0:0:0: [sda] Attached SCSI disk
[   21.707467] sr 0:0:0:0: Attached scsi generic sg0 type 5
[   21.707489] sd 2:0:0:0: Attached scsi generic sg1 type 0
[   21.983260] Attempting manual resume
[   21.983263] swsusp: Resume From Partition 8:5
[   21.983265] PM: Checking swsusp image.
[   21.983470] PM: Resume from disk failed.
[   21.998727] EXT3-fs: INFO: recovery required on readonly filesystem.
[   21.998734] EXT3-fs: write access will be enabled during recovery.
[   22.862138] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[0800460302a33869]
[   25.139052] kjournald starting.  Commit interval 5 seconds
[   25.139075] EXT3-fs: sda1: orphan cleanup on readonly fs
[   25.139081] ext3_orphan_cleanup: deleting unreferenced inode 2318475
[   25.205237] ext3_orphan_cleanup: deleting unreferenced inode 12845087
[   25.276759] ext3_orphan_cleanup: deleting unreferenced inode 12435458
[   25.276770] EXT3-fs: sda1: 3 orphan inodes deleted
[   25.276771] EXT3-fs: recovery complete.
[   25.293192] EXT3-fs: mounted filesystem with ordered data mode.
[   26.627084] usb-storage: device scan complete
[   26.627830] scsi 5:0:0:0: Direct-Access     WDC WD50 00AAKB-00UKA     07.0 PQ: 0 ANSI: 2
[   26.627916] usb-storage: device scan complete
[   26.629289] sd 5:0:0:0: [sdb] 976773168 512-byte hardware sectors (500108 MB)
[   26.629884] sd 5:0:0:0: [sdb] Write Protect is off
[   26.629889] sd 5:0:0:0: [sdb] Mode Sense: 00 00 00 00
[   26.629893] sd 5:0:0:0: [sdb] Assuming drive cache: write through
[   26.631071] sd 5:0:0:0: [sdb] 976773168 512-byte hardware sectors (500108 MB)
[   26.631449] scsi 6:0:0:0: Direct-Access     Maxtor 6 L250R0           0000 PQ: 0 ANSI: 0
[   26.631615] sd 5:0:0:0: [sdb] Write Protect is off
[   26.631618] sd 5:0:0:0: [sdb] Mode Sense: 00 00 00 00
[   26.631620] sd 5:0:0:0: [sdb] Assuming drive cache: write through
[   26.631623]  sdb: sdb1
[   26.645218] sd 5:0:0:0: [sdb] Attached SCSI disk
[   26.645257] sd 5:0:0:0: Attached scsi generic sg2 type 0
[   26.646249] sd 6:0:0:0: [sdc] 490234752 512-byte hardware sectors (251000 MB)
[   26.647159] sd 6:0:0:0: [sdc] Write Protect is off
[   26.647163] sd 6:0:0:0: [sdc] Mode Sense: 27 00 00 00
[   26.647167] sd 6:0:0:0: [sdc] Assuming drive cache: write through
[   26.648248] sd 6:0:0:0: [sdc] 490234752 512-byte hardware sectors (251000 MB)
[   26.649135] sd 6:0:0:0: [sdc] Write Protect is off
[   26.649137] sd 6:0:0:0: [sdc] Mode Sense: 27 00 00 00
[   26.649139] sd 6:0:0:0: [sdc] Assuming drive cache: write through
[   26.649141]  sdc: sdc1
[   26.668667] sd 6:0:0:0: [sdc] Attached SCSI disk
[   26.668703] sd 6:0:0:0: Attached scsi generic sg3 type 0
[   37.356404] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   37.427881] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   37.900578] Linux agpgart interface v0.102
[   38.047057] agpgart: Detected an Intel 965GM Chipset.
[   38.048108] agpgart: Detected 7676K stolen memory.
[   38.061597] agpgart: AGP aperture is 256M @ 0xd0000000
[   38.076174] iTCO_vendor_support: vendor-support=0
[   38.103756] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.02 (26-Jul-2007)
[   38.103833] iTCO_wdt: Found a ICH8M TCO device (Version=2, TCOBASE=0x1060)
[   38.103874] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   38.161728] input: PC Speaker as /devices/platform/pcspkr/input/input4
[   40.641473] input: Lid Switch as /devices/virtual/input/input5
[   40.650854] ACPI: Lid Switch [LID0]
[   40.650909] input: Power Button (CM) as /devices/virtual/input/input6
[   40.668052] ACPI: Power Button (CM) [PWRB]
[   40.671088] ACPI: AC Adapter [ADP1] (on-line)
[   40.867638] ACPI: PCI Interrupt 0000:02:00.0[A] -> GSI 16 (level, low) -> IRQ 17
[   40.867655] PCI: Setting latency timer of device 0000:02:00.0 to 64
[   40.867773] sky2 0000:02:00.0: v1.20 addr 0xf6000000 irq 17 Yukon-FE (0xb7) rev 3
[   40.868901] sky2 eth0: addr 00:1a:80:b5:8a:cb
[   41.075571] ACPI: PCI Interrupt 0000:08:03.2[C] -> GSI 18 (level, low) -> IRQ 18
[   41.238724] input: PS/2 Mouse as /devices/virtual/input/input7
[   41.269331] input: AlpsPS/2 ALPS GlidePoint as /devices/platform/i8042/serio4/input/input8
[   41.309275] ACPI: Battery Slot [BAT0] (battery present)
[   41.481828] iwl4965: Intel(R) Wireless WiFi Link 4965AGN driver for Linux, 1.2.0
[   41.481831] iwl4965: Copyright(c) 2003-2007 Intel Corporation
[   41.481953] ACPI: PCI Interrupt 0000:06:00.0[A] -> GSI 18 (level, low) -> IRQ 18
[   41.482353] PCI: Setting latency timer of device 0000:06:00.0 to 64
[   41.482376] iwl4965: Detected Intel Wireless WiFi Link 4965AGN
[   42.220380] Yenta: CardBus bridge found at 0000:08:03.0 [104d:902d]
[   42.220404] Yenta: Enabling burst memory read transactions
[   42.220409] Yenta: Using CSCINT to route CSC interrupts to PCI
[   42.220411] Yenta: Routing CardBus interrupts to PCI
[   42.220417] Yenta TI: socket 0000:08:03.0, mfunc 0x01121b22, devctl 0x64
[   42.443088] Yenta: ISA IRQ mask 0x0cf8, PCI irq 17
[   42.443092] Socket status: 30000006
[   42.443095] Yenta: Raising subordinate bus# of parent bus (#08) from #09 to #0c
[   42.443100] pcmcia: parent PCI bridge Memory window: 0xfc200000 - 0xfc2fffff
[   42.463848] iwl4965: Tunable channels: 11 802.11bg, 13 802.11a channels
[   42.464782] wmaster0: Selected rate control algorithm 'iwl-4965-rs'
[   43.274129] sony-laptop: Sony Notebook Control Driver v0.5.
[   43.278722] input: Sony Vaio Keys as /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:28/SNY5001:00/input/input9
[   43.296239] input: Sony Vaio Jogdial as /devices/virtual/input/input10
[   43.394852] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/LNXVIDEO:00/input/input11
[   43.410783] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)
[   43.936286] cs: IO port probe 0x100-0x3af: clean.
[   43.938372] cs: IO port probe 0x3e0-0x4ff: excluding 0x4d0-0x4d7
[   43.939254] cs: IO port probe 0x820-0x8ff: clean.
[   43.939978] cs: IO port probe 0xc00-0xcf7: clean.
[   43.940907] cs: IO port probe 0xa00-0xaff: clean.
[   44.369895] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 22 (level, low) -> IRQ 22
[   44.369936] PCI: Setting latency timer of device 0000:00:1b.0 to 64
[   44.374812] hda_codec: Unknown model for ALC262, trying auto-probe from BIOS...
[   44.632225] lp: driver loaded but no devices found
[   44.754493] Adding 9076684k swap on /dev/sda5.  Priority:-1 extents:1 across:9076684k
[   45.053806] EXT3 FS on sda1, internal journal
[   45.228835] device-mapper: uevent: version 1.0.3
[   45.228866] device-mapper: ioctl: 4.12.0-ioctl (2007-10-02) initialised: dm-devel@redhat.com
[   46.520936] ip_tables: (C) 2000-2006 Netfilter Core Team
[   47.054444] No dock devices found.
[   48.792761] apm: BIOS not found.
[   48.973220] ppdev: user-space parallel port driver
[   49.185455] audit(1218212239.314:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=5453 profile="/usr/sbin/cupsd" namespace="default"
[   49.314928] sonypi: Sony Programmable I/O Controller Driver v1.26.
[   49.315353] sonypi: please try the sony-laptop module instead and report failures, see also http://www.linux.it/~malattia/wiki/index.php/Sony_drivers
[   49.316759] sonypi: detected type2 model, verbose = 0, fnkeyinit = off, camera = off, compat = off, mask = 0xffffffff, useinput = on, acpi = on
[   49.317024] sonypi: enabled at irq=11, port1=0x1080, port2=0x1084
[   49.317093] sonypi: device allocated minor is 62
[   49.317419] input: Sony Vaio Jogdial as /devices/platform/sonypi/input/input12
[   49.332728] input: Sony Vaio Keys as /devices/platform/sonypi/input/input13
[   49.403089] sonypi command failed at /build/buildd/linux-2.6.24/debian/build/custom-source-rt/drivers/char/sonypi.c : sonypi_call1 (line 652)
[   49.448539] sonypi command failed at /build/buildd/linux-2.6.24/debian/build/custom-source-rt/drivers/char/sonypi.c : sonypi_call2 (line 663)
[   49.494563] sonypi command failed at /build/buildd/linux-2.6.24/debian/build/custom-source-rt/drivers/char/sonypi.c : sonypi_call2 (line 665)
[   49.536695] sonypi command failed at /build/buildd/linux-2.6.24/debian/build/custom-source-rt/drivers/char/sonypi.c : sonypi_call1 (line 652)
[   52.422692] vboxdrv: Trying to deactivate the NMI watchdog permanently...
[   52.423213] vboxdrv: Successfully done.
[   52.424485] vboxdrv: Found 2 processor cores.
[   52.424854] vboxdrv: fAsync=0 u64DiffCores=781.
[   52.425186] vboxdrv: TSC mode is 'synchronous', kernel timer mode is 'normal'.
[   52.425213] vboxdrv: Successfully loaded version 1.6.2 (interface 0x00070002).
[   52.556395] tun: Universal TUN/TAP device driver, 1.6
[   52.556805] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[   54.604413] sky2 eth0: enabling interface
[   54.727211] Bluetooth: Core ver 2.11
[   54.729135] NET: Registered protocol family 31
[   54.729143] Bluetooth: HCI device and connection manager initialized
[   54.729151] Bluetooth: HCI socket layer initialized
[   54.752508] Bluetooth: L2CAP ver 2.9
[   54.752513] Bluetooth: L2CAP socket layer initialized
[   54.847060] Bluetooth: RFCOMM socket layer initialized
[   54.847078] Bluetooth: RFCOMM TTY layer initialized
[   54.847081] Bluetooth: RFCOMM ver 1.8
[   55.662272] sky2 eth0: Link is up at 100 Mbps, full duplex, flow control both
[   57.540589] [drm] Initialized drm 1.1.0 20060810
[   57.543273] ACPI: PCI Interrupt 0000:00:02.0[A] -> GSI 16 (level, low) -> IRQ 17
[   57.543281] PCI: Setting latency timer of device 0000:00:02.0 to 64
[   57.543336] [drm] Initialized i915 1.6.0 20060119 on minor 0
[   57.561530] mtrr: type mismatch for d0000000,10000000 old: write-back new: write-combining
[   57.928668] NET: Registered protocol family 17
[   57.941758] vmmon: module license 'unspecified' taints kernel.
[   57.943984] /dev/vmmon[6132]: Module vmmon: registered with major=10 minor=165
[   57.944007] /dev/vmmon[6132]: Module vmmon: initialized
[   58.455245] /dev/vmnet: open called by PID 6162 (vmnet-bridge)
[   58.455254] /dev/vmnet: hub 0 does not exist, allocating memory.
[   58.455263] /dev/vmnet: port on hub 0 successfully opened
[   58.455277] bridge-eth0: enabling the bridge
[   58.455282] bridge-eth0: up
[   58.455284] bridge-eth0: already up
[   58.455286] bridge-eth0: attached
[   58.484142] /dev/vmnet: open called by PID 6178 (vmnet-netifup)
[   58.484153] /dev/vmnet: hub 8 does not exist, allocating memory.
[   58.484163] /dev/vmnet: port on hub 8 successfully opened
[   58.487779] /dev/vmnet: open called by PID 6169 (vmnet-netifup)
[   58.487789] /dev/vmnet: hub 1 does not exist, allocating memory.
[   58.487799] /dev/vmnet: port on hub 1 successfully opened
[   58.511628] /dev/vmnet: open called by PID 6177 (vmnet-natd)
[   58.511642] /dev/vmnet: port on hub 8 successfully opened
[   58.970588] /dev/vmnet: open called by PID 6204 (vmnet-dhcpd)
[   58.970609] /dev/vmnet: port on hub 8 successfully opened
[   58.981692] /dev/vmnet: open called by PID 6205 (vmnet-dhcpd)
[   58.981706] /dev/vmnet: port on hub 1 successfully opened
[   59.988292] usb 7-2.1: reset high speed USB device using ehci_hcd and address 4
[  116.835391] CPU0 attaching NULL sched-domain.
[  116.835808] CPU1 attaching NULL sched-domain.
[  116.836099] CPU0 attaching sched-domain:
[  116.836359]  domain 0: span 03
[  116.836600]   groups: 01 02
[  116.836888] CPU1 attaching sched-domain:
[  116.837141]  domain 0: span 03
[  116.837379]   groups: 02 01

```

Here is the clean dmesg after I had to hard-restart my machine:
```
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Linux version 2.6.24-19-rt (buildd@terranova) (gcc version 4.2.3 (Ubuntu 4.2.3-2ubuntu7)) #1 SMP PREEMPT RT Sat Jul 12 02:53:01 UTC 2008 (Ubuntu 2.6.24-4.6-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
[    0.000000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000dc000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 00000000bf6d0000 (usable)
[    0.000000]  BIOS-e820: 00000000bf6d0000 - 00000000bf6e0000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000bf6e0000 - 00000000bf6e3000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000bf6e3000 - 00000000c0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed00000 - 00000000fed00400 (reserved)
[    0.000000]  BIOS-e820: 00000000fed14000 - 00000000fed1a000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed1c000 - 00000000fed90000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000ff000000 - 0000000100000000 (reserved)
[    0.000000]  BIOS-e820: 0000000100000000 - 0000000140000000 (usable)
[    0.000000] Warning only 4GB will be used.
[    0.000000] Use a HIGHMEM64G enabled kernel.
[    0.000000] 3200MB HIGHMEM available.
[    0.000000] 896MB LOWMEM available.
[    0.000000] found SMP MP-table at 000f8080
[    0.000000] Entering add_active_range(0, 0, 1048576) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   229376
[    0.000000]   HighMem    229376 ->  1048576
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->  1048576
[    0.000000] On node 0 totalpages: 1048576
[    0.000000]   DMA zone: 56 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4040 pages, LIFO batch:0
[    0.000000]   Normal zone: 3080 pages used for memmap
[    0.000000]   Normal zone: 222200 pages, LIFO batch:31
[    0.000000]   HighMem zone: 11200 pages used for memmap
[    0.000000]   HighMem zone: 808000 pages, LIFO batch:31
[    0.000000]   Movable zone: 0 pages used for memmap
[    0.000000] DMI present.
[    0.000000] ACPI: RSDP signature @ 0xC00F8050 checksum 0
[    0.000000] ACPI: RSDP 000F8050, 0024 (r2 PTLTD )
[    0.000000] ACPI: XSDT BF6D7E92, 008C (r1   Sony     VAIO 20071023 PTL         0)
[    0.000000] ACPI: FACP BF6DFC04, 00F4 (r3   Sony     VAIO 20071023 PTL         1)
[    0.000000] ACPI: DSDT BF6D9217, 6979 (r2   Sony     VAIO 20071023 PTL  20050624)
[    0.000000] ACPI: FACS BF6E2FC0, 0040
[    0.000000] ACPI: APIC BF6DFCF8, 0068 (r1   Sony     VAIO 20071023 PTL        5A)
[    0.000000] ACPI: HPET BF6DFD60, 0038 (r1   Sony     VAIO 20071023 PTL        5A)
[    0.000000] ACPI: MCFG BF6DFD98, 003C (r1   Sony     VAIO 20071023 PTL        5A)
[    0.000000] ACPI: SLIC BF6DFDD4, 0176 (r1   Sony     VAIO 20071023 PTL   1000000)
[    0.000000] ACPI: TMOR BF6DFF4A, 0026 (r1   Sony     VAIO 20071023 PTL         3)
[    0.000000] ACPI: APIC BF6DFF70, 0068 (r1   Sony     VAIO 20071023 PTL         0)
[    0.000000] ACPI: BOOT BF6DFFD8, 0028 (r1   Sony     VAIO 20071023 PTL         1)
[    0.000000] ACPI: SSDT BF6D90FA, 011D (r1   Sony     VAIO 20071023 PTL  20050624)
[    0.000000] ACPI: SSDT BF6D8FD7, 0123 (r1   Sony     VAIO 20071023 PTL  20050624)
[    0.000000] ACPI: SSDT BF6D8506, 0287 (r1   Sony     VAIO 20071023 PTL  20050624)
[    0.000000] ACPI: SSDT BF6D8452, 00B4 (r1   Sony     VAIO 20071023 PTL  20050624)
[    0.000000] ACPI: SSDT BF6D7F1E, 0534 (r1   Sony     VAIO 20071023 PTL  20050624)
[    0.000000] ACPI: BIOS bug: multiple APIC/MADT found, using 0
[    0.000000] ACPI: If "acpi_apic_instance=2" works better, notify linux-acpi@vger.kernel.org
[    0.000000] ACPI: DMI detected: Sony
[    0.000000] ACPI: PM-Timer IO Port: 0x1008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] Processor #0 6:15 APIC version 20
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
[    0.000000] Processor #1 6:15 APIC version 20
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 1, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
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
[    0.000000] Real-Time Preemption Support (C) 2004-2007 Ingo Molnar
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 1034240
[    0.000000] Kernel command line: root=UUID=1bebd1ca-6b65-462d-baf2-211248477bcb ro quiet splash
[    0.000000] mapped APIC to ffffb000 (fee00000)
[    0.000000] mapped IOAPIC to ffffa000 (fec00000)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] Detected 1828.853 MHz processor.
[   11.260916] Console: colour VGA+ 80x25
[   11.260919] console [tty0] enabled
[   11.261207] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[   11.261494] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[   11.490530] Memory: 3064700k/4194304k available (2225k kernel code, 70344k reserved, 1059k data, 368k init, 2218816k highmem)
[   11.490537] virtual kernel memory layout:
[   11.490538]     fixmap  : 0xfff4b000 - 0xfffff000   ( 720 kB)
[   11.490539]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   11.490540]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
[   11.490541]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
[   11.490541]       .init : 0xc043b000 - 0xc0497000   ( 368 kB)
[   11.490542]       .data : 0xc032c6a0 - 0xc0435324   (1059 kB)
[   11.490543]       .text : 0xc0100000 - 0xc032c6a0   (2225 kB)
[   11.490546] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   11.490812] hpet clockevent registered
[   11.550716] Calibrating delay using timer specific routine.. 3660.73 BogoMIPS (lpj=1830367)
[   11.550763] Security Framework initialized
[   11.550769] SELinux:  Disabled at boot.
[   11.550777] AppArmor: AppArmor initialized
[   11.550781] Failure registering capabilities with primary security module.
[   11.550797] Mount-cache hash table entries: 512
[   11.550941] Initializing cgroup subsys ns
[   11.550945] Initializing cgroup subsys cpuacct
[   11.550957] CPU: After generic identify, caps: bfebfbff 20100000 00000000 00000000 0000e39d 00000000 00000001 00000000
[   11.550964] monitor/mwait feature present.
[   11.550966] using mwait in idle threads.
[   11.550969] CPU: L1 I cache: 32K, L1 D cache: 32K
[   11.550972] CPU: L2 cache: 2048K
[   11.550974] CPU: Physical Processor ID: 0
[   11.550976] CPU: Processor Core ID: 0
[   11.550978] CPU: After all inits, caps: bfebfbff 20100000 00000000 00003940 0000e39d 00000000 00000001 00000000
[   11.550988] Compat vDSO mapped to ffffe000.
[   11.550999] Checking 'hlt' instruction... OK.
[   11.555078] SMP alternatives: switching to UP code
[   11.556277] Early unpacking initramfs... done
[   11.888400] ACPI: Core revision 20070126
[   11.888452] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[   11.900348] CPU0: Intel(R) Core(TM)2 Duo CPU     T5550  @ 1.83GHz stepping 0d
[   11.900366] SMP alternatives: switching to SMP code
[   11.900921] Booting processor 1/1 eip 3000
[   11.911149] Initializing CPU#1
[   11.970998] Calibrating delay using timer specific routine.. 3657.50 BogoMIPS (lpj=1828750)
[   11.971005] CPU: After generic identify, caps: bfebfbff 20100000 00000000 00000000 0000e39d 00000000 00000001 00000000
[   11.971010] monitor/mwait feature present.
[   11.971013] CPU: L1 I cache: 32K, L1 D cache: 32K
[   11.971015] CPU: L2 cache: 2048K
[   11.971017] CPU: Physical Processor ID: 0
[   11.971018] CPU: Processor Core ID: 1
[   11.971020] CPU: After all inits, caps: bfebfbff 20100000 00000000 00003940 0000e39d 00000000 00000001 00000000
[   11.971538] CPU1: Intel(R) Core(TM)2 Duo CPU     T5550  @ 1.83GHz stepping 0d
[   11.971560] Total of 2 processors activated (7318.23 BogoMIPS).
[   11.971752] ENABLING IO-APIC IRQs
[   11.971946] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[   12.083441] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
[   12.103440] Brought up 2 CPUs
[   12.103464] CPU0 attaching sched-domain:
[   12.103466]  domain 0: span 03
[   12.103468]   groups: 01 02
[   12.103472] CPU1 attaching sched-domain:
[   12.103474]  domain 0: span 03
[   12.103476]   groups: 02 01
[   12.103696] net_namespace: 76 bytes
[   12.103705] Booting paravirtualized kernel on bare hardware
[   12.104162] Time: 16:23:54  Date: 08/08/08
[   12.104202] NET: Registered protocol family 16
[   12.104407] EISA bus registered
[   12.104411] ACPI: bus type pci registered
[   12.104905] PCI: PCI BIOS revision 3.00 entry at 0xfddf1, last bus=9
[   12.104907] PCI: Using configuration type 1
[   12.104922] Setting up standard PCI resources
[   12.107875] ACPI: EC: Look up EC in DSDT
[   12.115553] ACPI: BIOS _OSI(Linux) query ignored via DMI
[   12.115556] ACPI: If "acpi_osi=Linux" works better, please notify linux-acpi@vger.kernel.org
[   12.116872] ACPI: Interpreter enabled
[   12.116875] ACPI: (supports S0 S3 S4 S5)
[   12.116892] ACPI: Using IOAPIC for interrupt routing
[   12.117332] ACPI: EC: non-query interrupt received, switching to interrupt mode
[   12.137866] ACPI: EC: GPE = 0x17, I/O: command/status = 0x66, data = 0x62
[   12.137868] ACPI: EC: driver started in interrupt mode
[   12.137915] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   12.138974] PCI quirk: region 1000-107f claimed by ICH6 ACPI/GPIO/TCO
[   12.138979] PCI quirk: region 1180-11bf claimed by ICH6 GPIO
[   12.140187] PCI: Transparent bridge - 0000:00:1e.0
[   12.140286] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   12.140684] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP01._PRT]
[   12.140834] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP02._PRT]
[   12.140981] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP03._PRT]
[   12.141146] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIB._PRT]
[   12.179065] ACPI: PCI Interrupt Link [LNKA] (IRQs 1 3 4 *5 6 7 10 12 14 15)
[   12.179175] ACPI: PCI Interrupt Link [LNKB] (IRQs 1 3 4 5 6 7 11 12 14 15) *10
[   12.179283] ACPI: PCI Interrupt Link [LNKC] (IRQs 1 3 4 5 6 *7 10 12 14 15)
[   12.179389] ACPI: PCI Interrupt Link [LNKD] (IRQs 1 3 4 5 6 7 11 12 14 15) *10
[   12.179496] ACPI: PCI Interrupt Link [LNKE] (IRQs 1 3 4 5 6 7 10 12 14 15) *0, disabled.
[   12.179603] ACPI: PCI Interrupt Link [LNKF] (IRQs 1 3 4 5 6 7 *11 12 14 15)
[   12.179722] ACPI: PCI Interrupt Link [LNKG] (IRQs 1 3 4 5 6 7 10 12 14 15) *11
[   12.179829] ACPI: PCI Interrupt Link [LNKH] (IRQs 1 3 4 5 6 7 11 12 14 15) *10
[   12.179995] Linux Plug and Play Support v0.97 (c) Adam Belay
[   12.180029] pnp: PnP ACPI init
[   12.180036] ACPI: bus type pnp registered
[   12.187017] pnp: PnP ACPI: found 10 devices
[   12.187019] ACPI: ACPI bus type pnp unregistered
[   12.187023] PnPBIOS: Disabled by ACPI PNP
[   12.187242] PCI: Using ACPI for IRQ routing
[   12.187245] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   12.295091] NET: Registered protocol family 8
[   12.295093] NET: Registered protocol family 20
[   12.295136] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[   12.295140] hpet0: 3 64-bit timers, 14318180 Hz
[   12.296195] AppArmor: AppArmor Filesystem Enabled
[   12.304576] system 00:01: iomem range 0xfed1c000-0xfed1ffff could not be reserved
[   12.304579] system 00:01: iomem range 0xfed14000-0xfed17fff could not be reserved
[   12.304582] system 00:01: iomem range 0xfed18000-0xfed18fff could not be reserved
[   12.304585] system 00:01: iomem range 0xfed19000-0xfed19fff could not be reserved
[   12.304588] system 00:01: iomem range 0xe0000000-0xefffffff could not be reserved
[   12.304591] system 00:01: iomem range 0xfed20000-0xfed3ffff could not be reserved
[   12.304594] system 00:01: iomem range 0xfed40000-0xfed44fff could not be reserved
[   12.304597] system 00:01: iomem range 0xfed45000-0xfed8ffff could not be reserved
[   12.304605] system 00:04: iomem range 0xfed00000-0xfed003ff could not be reserved
[   12.304612] system 00:06: ioport range 0x680-0x69f has been reserved
[   12.304615] system 00:06: ioport range 0x800-0x80f has been reserved
[   12.304617] system 00:06: ioport range 0x1000-0x107f has been reserved
[   12.304620] system 00:06: ioport range 0x1180-0x11bf has been reserved
[   12.304622] system 00:06: ioport range 0x1640-0x164f has been reserved
[   12.304625] system 00:06: ioport range 0xfe00-0xfe7f has been reserved
[   12.304627] system 00:06: ioport range 0xfe80-0xfeff has been reserved
[   12.335033] PCI: Bridge: 0000:00:1c.0
[   12.335037]   IO window: 2000-2fff
[   12.335044]   MEM window: f6000000-f7ffffff
[   12.335049]   PREFETCH window: f0000000-f1ffffff
[   12.335055] PCI: Bridge: 0000:00:1c.1
[   12.335058]   IO window: 3000-3fff
[   12.335065]   MEM window: f8000000-f9ffffff
[   12.335069]   PREFETCH window: f2000000-f3ffffff
[   12.335076] PCI: Bridge: 0000:00:1c.2
[   12.335079]   IO window: 4000-4fff
[   12.335085]   MEM window: fa000000-fbffffff
[   12.335090]   PREFETCH window: f4000000-f5ffffff
[   12.335100] PCI: Bus 9, cardbus bridge: 0000:08:03.0
[   12.335102]   IO window: 00001400-000014ff
[   12.335107]   IO window: 00005000-000050ff
[   12.335112]   PREFETCH window: c4000000-c7ffffff
[   12.335118]   MEM window: c8000000-cbffffff
[   12.335123] PCI: Bridge: 0000:00:1e.0
[   12.335125]   IO window: disabled.
[   12.335131]   MEM window: fc200000-fc2fffff
[   12.335135]   PREFETCH window: disabled.
[   12.335168] ACPI: PCI Interrupt 0000:00:1c.0[A] -> GSI 17 (level, low) -> IRQ 16
[   12.335175] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[   12.335201] ACPI: PCI Interrupt 0000:00:1c.1[B] -> GSI 16 (level, low) -> IRQ 17
[   12.335207] PCI: Setting latency timer of device 0000:00:1c.1 to 64
[   12.335233] ACPI: PCI Interrupt 0000:00:1c.2[C] -> GSI 18 (level, low) -> IRQ 18
[   12.335239] PCI: Setting latency timer of device 0000:00:1c.2 to 64
[   12.335254] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[   12.335273] ACPI: PCI Interrupt 0000:08:03.0[A] -> GSI 16 (level, low) -> IRQ 17
[   12.335298] NET: Registered protocol family 2
[   12.369752] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[   12.369993] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[   12.370532] TCP bind hash table entries: 65536 (order: 9, 2359296 bytes)
[   12.371774] TCP: Hash tables configured (established 131072 bind 65536)
[   12.371778] TCP reno registered
[   12.383589] checking if image is initramfs... it is
[   13.044843] Freeing initrd memory: 7696k freed
[   13.045001] Simple Boot Flag at 0x36 set to 0x1
[   13.045704] audit: initializing netlink socket (disabled)
[   13.045723] audit(1218212634.361:1): initialized
[   13.045784] krcupreemptd setsched 0
[   13.045786]   prio = 98
[   13.045971] highmem bounce pool size: 64 pages
[   13.046045] VFS: Disk quotas dquot_6.5.1
[   13.046069] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   13.046156] io scheduler noop registered
[   13.046158] io scheduler anticipatory registered
[   13.046160] io scheduler deadline registered
[   13.046169] io scheduler cfq registered (default)
[   13.046181] Boot video device is 0000:00:02.0
[   13.046428] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[   13.046492] assign_interrupt_mode Found MSI capability
[   13.046545] Allocate Port Service[0000:00:1c.0:pcie00]
[   13.046584] Allocate Port Service[0000:00:1c.0:pcie02]
[   13.046704] PCI: Setting latency timer of device 0000:00:1c.1 to 64
[   13.046767] assign_interrupt_mode Found MSI capability
[   13.046817] Allocate Port Service[0000:00:1c.1:pcie00]
[   13.046854] Allocate Port Service[0000:00:1c.1:pcie02]
[   13.046963] PCI: Setting latency timer of device 0000:00:1c.2 to 64
[   13.047026] assign_interrupt_mode Found MSI capability
[   13.047076] Allocate Port Service[0000:00:1c.2:pcie00]
[   13.047110] Allocate Port Service[0000:00:1c.2:pcie02]
[   13.047394] isapnp: Scanning for PnP cards...
[   13.404304] isapnp: No Plug & Play device found
[   13.430629] Real Time Clock Driver v1.12ac
[   13.430862] hpet_resources: 0xfed00000 is busy
[   13.430888] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   13.432253] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   13.432320] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[   13.432416] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[   13.435590] i8042.c: Detected active multiplexing controller, rev 1.1.
[   13.439914] serio: i8042 KBD port at 0x60,0x64 irq 1
[   13.439971] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[   13.439974] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[   13.439976] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[   13.439978] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[   13.448157] mice: PS/2 mouse device common for all mice
[   13.448277] EISA: Probing bus 0 at eisa.0
[   13.448284] Cannot allocate resource for EISA slot 1
[   13.448288] Cannot allocate resource for EISA slot 2
[   13.448290] Cannot allocate resource for EISA slot 3
[   13.448292] Cannot allocate resource for EISA slot 4
[   13.448294] Cannot allocate resource for EISA slot 5
[   13.448310] EISA: Detected 0 cards.
[   13.448312] cpuidle: using governor ladder
[   13.448385] NET: Registered protocol family 1
[   13.448412] Using IPI No-Shortcut mode
[   13.448446] registered taskstats version 1
[   13.448571]   Magic number: 4:133:388
[   13.448659] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[   13.448661] EDD information not available.
[   13.448922] Freeing unused kernel memory: 368k freed
[   13.650467] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[   14.690531] fuse init (API version 7.9)
[   14.704365] ACPI: SSDT BF6D8CD6, 021D (r1   Sony     VAIO 20071023 PTL  20050624)
[   14.704608] ACPI: SSDT BF6D878D, 04B7 (r1   Sony     VAIO 20071023 PTL  20050624)
[   14.707221] Monitor-Mwait will be used to enter C-1 state
[   14.707224] Monitor-Mwait will be used to enter C-2 state
[   14.707226] Monitor-Mwait will be used to enter C-3 state
[   14.707357] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[   14.707363] ACPI: Processor [CPU0] (supports 8 throttling states)
[   14.707733] ACPI: SSDT BF6D8EF3, 00E4 (r1   Sony     VAIO 20071023 PTL  20050624)
[   14.707958] ACPI: SSDT BF6D8C44, 0092 (r1   Sony     VAIO 20071023 PTL  20050624)
[   14.709234] ACPI: CPU1 (power states: C1[C1] C2[C2] C3[C3])
[   14.709240] ACPI: Processor [CPU1] (supports 8 throttling states)
[   14.712329] ACPI: Thermal Zone [TZ00] (60 C)
[   14.713162] ACPI Exception (thermal-0471): AE_NOT_FOUND, Invalid active threshold [0] [20070126]
[   14.713209] ACPI Exception (thermal-0471): AE_NOT_FOUND, Invalid active threshold [1] [20070126]
[   14.713876] ACPI: Thermal Zone [TZ01] (60 C)
[   14.878757] usbcore: registered new interface driver usbfs
[   14.878780] usbcore: registered new interface driver hub
[   14.879223] usbcore: registered new device driver usb
[   14.880832] USB Universal Host Controller Interface driver v3.0
[   14.880875] ACPI: PCI Interrupt 0000:00:1a.0[A] -> GSI 16 (level, low) -> IRQ 17
[   14.880886] PCI: Setting latency timer of device 0000:00:1a.0 to 64
[   14.880890] uhci_hcd 0000:00:1a.0: UHCI Host Controller
[   14.881209] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 1
[   14.882869] uhci_hcd 0000:00:1a.0: irq 17, io base 0x00001820
[   14.883013] usb usb1: configuration #1 chosen from 1 choice
[   14.883039] hub 1-0:1.0: USB hub found
[   14.883045] hub 1-0:1.0: 2 ports detected
[   14.983952] ACPI: PCI Interrupt 0000:00:1a.1[B] -> GSI 21 (level, low) -> IRQ 19
[   14.983964] PCI: Setting latency timer of device 0000:00:1a.1 to 64
[   14.983969] uhci_hcd 0000:00:1a.1: UHCI Host Controller
[   14.983993] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 2
[   14.984055] uhci_hcd 0000:00:1a.1: irq 19, io base 0x00001840
[   14.984173] usb usb2: configuration #1 chosen from 1 choice
[   14.984197] hub 2-0:1.0: USB hub found
[   14.984203] hub 2-0:1.0: 2 ports detected
[   15.084833] ACPI: PCI Interrupt 0000:00:1a.7[C] -> GSI 18 (level, low) -> IRQ 18
[   15.084849] PCI: Setting latency timer of device 0000:00:1a.7 to 64
[   15.084853] ehci_hcd 0000:00:1a.7: EHCI Host Controller
[   15.084879] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 3
[   15.088794] ehci_hcd 0000:00:1a.7: debug port 1
[   15.088802] PCI: cache line size of 32 is not supported by device 0000:00:1a.7
[   15.088837] ehci_hcd 0000:00:1a.7: irq 18, io mem 0xfc504800
[   15.098657] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   15.098781] usb usb3: configuration #1 chosen from 1 choice
[   15.098807] hub 3-0:1.0: USB hub found
[   15.098814] hub 3-0:1.0: 4 ports detected
[   15.199683] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 23 (level, low) -> IRQ 20
[   15.199697] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[   15.199701] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[   15.199728] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 4
[   15.200379] uhci_hcd 0000:00:1d.0: irq 20, io base 0x00001860
[   15.200513] usb usb4: configuration #1 chosen from 1 choice
[   15.200538] hub 4-0:1.0: USB hub found
[   15.200544] hub 4-0:1.0: 2 ports detected
[   15.301252] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 19 (level, low) -> IRQ 21
[   15.301265] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[   15.301269] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[   15.301294] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 5
[   15.301382] uhci_hcd 0000:00:1d.1: irq 21, io base 0x00001880
[   15.301508] usb usb5: configuration #1 chosen from 1 choice
[   15.301532] hub 5-0:1.0: USB hub found
[   15.301538] hub 5-0:1.0: 2 ports detected
[   15.402352] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 18
[   15.402364] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[   15.402368] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[   15.402395] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 6
[   15.402425] uhci_hcd 0000:00:1d.2: irq 18, io base 0x000018a0
[   15.402540] usb usb6: configuration #1 chosen from 1 choice
[   15.402563] hub 6-0:1.0: USB hub found
[   15.402573] hub 6-0:1.0: 2 ports detected
[   15.503229] ACPI: PCI Interrupt 0000:00:1d.7[A] -> GSI 23 (level, low) -> IRQ 20
[   15.503245] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[   15.503249] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[   15.503275] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 7
[   15.507186] ehci_hcd 0000:00:1d.7: debug port 1
[   15.507193] PCI: cache line size of 32 is not supported by device 0000:00:1d.7
[   15.507201] ehci_hcd 0000:00:1d.7: irq 20, io mem 0xfc504c00
[   15.517037] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   15.517190] usb usb7: configuration #1 chosen from 1 choice
[   15.517217] hub 7-0:1.0: USB hub found
[   15.517225] hub 7-0:1.0: 6 ports detected
[   16.090209] usb 5-2: new low speed USB device using uhci_hcd and address 2
[   16.254925] usb 5-2: configuration #1 chosen from 1 choice
[   16.380907] SCSI subsystem initialized
[   16.593020] libata version 3.00 loaded.
[   16.665146] ahci 0000:00:1f.2: version 3.0
[   16.665177] ACPI: PCI Interrupt 0000:00:1f.2[B] -> GSI 19 (level, low) -> IRQ 21
[   16.665228] ahci 0000:00:1f.2: nr_ports (3) and implemented port map (0x1) don't match, using nr_ports
[   16.665230] ahci 0000:00:1f.2: forcing PORTS_IMPL to 0x7
[   17.664927] ahci 0000:00:1f.2: AHCI 0001.0100 32 slots 3 ports 3 Gbps 0x7 impl SATA mode
[   17.664932] ahci 0000:00:1f.2: flags: 64bit ncq sntf pm led clo pio slum part
[   17.664938] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[   17.665211] scsi0 : ahci
[   17.665296] scsi1 : ahci
[   17.665368] scsi2 : ahci
[   17.665429] ata1: SATA max UDMA/133 abar m2048@0xfc504000 port 0xfc504100 irq 220
[   17.665433] ata2: SATA max UDMA/133 abar m2048@0xfc504000 port 0xfc504180 irq 220
[   17.665436] ata3: SATA max UDMA/133 abar m2048@0xfc504000 port 0xfc504200 irq 220
[   17.853638] usbcore: registered new interface driver hiddev
[   17.868326] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:1d.1/usb5/5-2/5-2:1.0/input/input2
[   17.876343] input,hidraw0: USB HID v1.11 Mouse [Logitech USB Receiver] on usb-0000:00:1d.1-2
[   17.887690] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:1d.1/usb5/5-2/5-2:1.1/input/input3
[   17.895589] input,hiddev96,hidraw1: USB HID v1.11 Device [Logitech USB Receiver] on usb-0000:00:1d.1-2
[   17.895608] usbcore: registered new interface driver usbhid
[   17.895612] /build/buildd/linux-2.6.24/debian/build/custom-source-rt/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
[   18.119947] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[   18.120944] ata1.00: ATA-8: Hitachi HTS542525K9SA00, BBFOC3BP, max UDMA/133
[   18.120948] ata1.00: 488397168 sectors, multi 16: LBA48 NCQ (depth 31/32)
[   18.122177] ata1.00: configured for UDMA/133
[   18.176848] Clocksource tsc unstable (delta = -592264778 ns)
[   18.228856] ata2: SATA link down (SStatus 0 SControl 0)
[   18.287216] ata3: SATA link down (SStatus 0 SControl 0)
[   18.287399] scsi 0:0:0:0: Direct-Access     ATA      Hitachi HTS54252 BBFO PQ: 0 ANSI: 5
[   18.288229] ata_piix 0000:00:1f.1: version 2.12
[   18.288246] ACPI: PCI Interrupt 0000:00:1f.1[A] -> GSI 19 (level, low) -> IRQ 21
[   18.288282] PCI: Setting latency timer of device 0000:00:1f.1 to 64
[   18.288403] scsi3 : ata_piix
[   18.288455] scsi4 : ata_piix
[   18.289227] ata4: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0x1810 irq 14
[   18.289230] ata5: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x1818 irq 15
[   18.295735] Driver 'sd' needs updating - please use bus_type methods
[   18.297792] sd 0:0:0:0: [sda] 488397168 512-byte hardware sectors (250059 MB)
[   18.297829] sd 0:0:0:0: [sda] Write Protect is off
[   18.297832] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   18.297891] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   18.297962] sd 0:0:0:0: [sda] 488397168 512-byte hardware sectors (250059 MB)
[   18.297980] sd 0:0:0:0: [sda] Write Protect is off
[   18.297983] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   18.298013] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   18.298016]  sda: sda1 sda2 < sda5 >
[   18.344308] sd 0:0:0:0: [sda] Attached SCSI disk
[   18.348980] sd 0:0:0:0: Attached scsi generic sg0 type 0
[   18.593675] ata4.00: ATAPI: Optiarc DVD RW AD-7560A, DS02, max UDMA/33
[   18.603892] Attempting manual resume
[   18.603895] swsusp: Resume From Partition 8:5
[   18.603897] PM: Checking swsusp image.
[   18.604094] PM: Resume from disk failed.
[   18.619645] EXT3-fs: INFO: recovery required on readonly filesystem.
[   18.619657] EXT3-fs: write access will be enabled during recovery.
[   18.750404] ata4.00: configured for UDMA/33
[   18.913610] scsi 3:0:0:0: CD-ROM            Optiarc  DVD RW AD-7560A  DS02 PQ: 0 ANSI: 5
[   18.913767] scsi 3:0:0:0: Attached scsi generic sg1 type 5
[   18.914766] ACPI: PCI Interrupt 0000:08:03.1[B] -> GSI 17 (level, low) -> IRQ 16
[   18.965071] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[16]  MMIO=[fc206000-fc2067ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[   18.977246] Driver 'sr' needs updating - please use bus_type methods
[   18.984430] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[   18.984438] Uniform CD-ROM driver Revision: 3.20
[   18.984528] sr 3:0:0:0: Attached scsi CD-ROM sr0
[   20.213891] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[0800460302a33869]
[   21.788466] kjournald starting.  Commit interval 5 seconds
[   21.788484] EXT3-fs: sda1: orphan cleanup on readonly fs
[   21.788492] ext3_orphan_cleanup: deleting unreferenced inode 2318844
[   21.788538] ext3_orphan_cleanup: deleting unreferenced inode 13000766
[   21.788550] ext3_orphan_cleanup: deleting unreferenced inode 3899411
[   21.788559] EXT3-fs: sda1: 3 orphan inodes deleted
[   21.788560] EXT3-fs: recovery complete.
[   22.287472] EXT3-fs: mounted filesystem with ordered data mode.
[   33.696850] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   33.758826] Linux agpgart interface v0.102
[   33.846898] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   34.029139] agpgart: Detected an Intel 965GM Chipset.
[   34.030234] agpgart: Detected 7676K stolen memory.
[   34.043685] agpgart: AGP aperture is 256M @ 0xd0000000
[   34.769875] iTCO_vendor_support: vendor-support=0
[   34.814374] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.02 (26-Jul-2007)
[   34.814454] iTCO_wdt: Found a ICH8M TCO device (Version=2, TCOBASE=0x1060)
[   34.814545] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   34.878949] input: PC Speaker as /devices/platform/pcspkr/input/input4
[   35.996958] ACPI: AC Adapter [ADP1] (on-line)
[   36.662151] ACPI: Battery Slot [BAT0] (battery present)
[   36.848466] input: Lid Switch as /devices/virtual/input/input5
[   36.855545] ACPI: Lid Switch [LID0]
[   36.855613] input: Power Button (CM) as /devices/virtual/input/input6
[   36.870854] ACPI: Power Button (CM) [PWRB]
[   37.458843] Yenta: CardBus bridge found at 0000:08:03.0 [104d:902d]
[   37.458866] Yenta: Enabling burst memory read transactions
[   37.458872] Yenta: Using CSCINT to route CSC interrupts to PCI
[   37.458874] Yenta: Routing CardBus interrupts to PCI
[   37.458880] Yenta TI: socket 0000:08:03.0, mfunc 0x01121b22, devctl 0x64
[   37.682647] Yenta: ISA IRQ mask 0x0cf8, PCI irq 17
[   37.682652] Socket status: 30000006
[   37.682655] Yenta: Raising subordinate bus# of parent bus (#08) from #09 to #0c
[   37.682660] pcmcia: parent PCI bridge Memory window: 0xfc200000 - 0xfc2fffff
[   37.748609] iwl4965: Intel(R) Wireless WiFi Link 4965AGN driver for Linux, 1.2.0
[   37.748613] iwl4965: Copyright(c) 2003-2007 Intel Corporation
[   37.748813] ACPI: PCI Interrupt 0000:06:00.0[A] -> GSI 18 (level, low) -> IRQ 18
[   37.748844] PCI: Setting latency timer of device 0000:06:00.0 to 64
[   37.748867] iwl4965: Detected Intel Wireless WiFi Link 4965AGN
[   38.060415] input: PS/2 Mouse as /devices/virtual/input/input7
[   38.092226] input: AlpsPS/2 ALPS GlidePoint as /devices/platform/i8042/serio4/input/input8
[   38.588953] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/LNXVIDEO:00/input/input9
[   38.606399] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)
[   38.663395] ACPI: PCI Interrupt 0000:08:03.2[C] -> GSI 18 (level, low) -> IRQ 18
[   38.663484] ACPI: PCI Interrupt 0000:02:00.0[A] -> GSI 16 (level, low) -> IRQ 17
[   38.663496] PCI: Setting latency timer of device 0000:02:00.0 to 64
[   38.663528] sky2 0000:02:00.0: v1.20 addr 0xf6000000 irq 17 Yukon-FE (0xb7) rev 3
[   38.728363] sony-laptop: Sony Notebook Control Driver v0.5.
[   38.729433] sky2 eth0: addr 00:1a:80:b5:8a:cb
[   38.729545] input: Sony Vaio Keys as /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:28/SNY5001:00/input/input10
[   38.745218] input: Sony Vaio Jogdial as /devices/virtual/input/input11
[   38.909546] iwl4965: Tunable channels: 11 802.11bg, 13 802.11a channels
[   38.909932] wmaster0: Selected rate control algorithm 'iwl-4965-rs'
[   39.452603] cs: IO port probe 0x100-0x3af: clean.
[   39.454758] cs: IO port probe 0x3e0-0x4ff: excluding 0x4d0-0x4d7
[   39.455676] cs: IO port probe 0x820-0x8ff: clean.
[   39.456438] cs: IO port probe 0xc00-0xcf7: clean.
[   39.457381] cs: IO port probe 0xa00-0xaff: clean.
[   40.010596] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 22 (level, low) -> IRQ 22
[   40.010640] PCI: Setting latency timer of device 0000:00:1b.0 to 64
[   40.017773] hda_codec: Unknown model for ALC262, trying auto-probe from BIOS...
[   40.198101] lp: driver loaded but no devices found
[   40.320697] Adding 9076684k swap on /dev/sda5.  Priority:-1 extents:1 across:9076684k
[   40.687586] EXT3 FS on sda1, internal journal
[   40.841541] device-mapper: uevent: version 1.0.3
[   40.841573] device-mapper: ioctl: 4.12.0-ioctl (2007-10-02) initialised: dm-devel@redhat.com
[   41.743793] ip_tables: (C) 2000-2006 Netfilter Core Team
[   42.200624] No dock devices found.
[   43.819692] apm: BIOS not found.
[   43.933841] ppdev: user-space parallel port driver
[   44.123627] audit(1218212667.692:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=5297 profile="/usr/sbin/cupsd" namespace="default"
[   44.231006] sonypi: Sony Programmable I/O Controller Driver v1.26.
[   44.231366] sonypi: please try the sony-laptop module instead and report failures, see also http://www.linux.it/~malattia/wiki/index.php/Sony_drivers
[   44.232306] sonypi: detected type2 model, verbose = 0, fnkeyinit = off, camera = off, compat = off, mask = 0xffffffff, useinput = on, acpi = on
[   44.232311] sonypi: enabled at irq=11, port1=0x1080, port2=0x1084
[   44.232313] sonypi: device allocated minor is 62
[   44.232369] input: Sony Vaio Jogdial as /devices/platform/sonypi/input/input12
[   44.248720] input: Sony Vaio Keys as /devices/platform/sonypi/input/input13
[   44.317344] sonypi command failed at /build/buildd/linux-2.6.24/debian/build/custom-source-rt/drivers/char/sonypi.c : sonypi_call1 (line 652)
[   44.362569] sonypi command failed at /build/buildd/linux-2.6.24/debian/build/custom-source-rt/drivers/char/sonypi.c : sonypi_call2 (line 663)
[   44.411084] sonypi command failed at /build/buildd/linux-2.6.24/debian/build/custom-source-rt/drivers/char/sonypi.c : sonypi_call2 (line 665)
[   44.453245] sonypi command failed at /build/buildd/linux-2.6.24/debian/build/custom-source-rt/drivers/char/sonypi.c : sonypi_call1 (line 652)
[   47.094694] vboxdrv: Trying to deactivate the NMI watchdog permanently...
[   47.095407] vboxdrv: Successfully done.
[   47.095558] vboxdrv: Found 2 processor cores.
[   47.096718] vboxdrv: fAsync=0 u64DiffCores=2739.
[   47.096792] vboxdrv: TSC mode is 'synchronous', kernel timer mode is 'normal'.
[   47.096796] vboxdrv: Successfully loaded version 1.6.2 (interface 0x00070002).
[   47.265919] tun: Universal TUN/TAP device driver, 1.6
[   47.265996] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[   48.972945] sky2 eth0: enabling interface
[   49.021447] Bluetooth: Core ver 2.11
[   49.021755] NET: Registered protocol family 31
[   49.021759] Bluetooth: HCI device and connection manager initialized
[   49.021765] Bluetooth: HCI socket layer initialized
[   49.071823] Bluetooth: L2CAP ver 2.9
[   49.071838] Bluetooth: L2CAP socket layer initialized
[   49.217283] Bluetooth: RFCOMM socket layer initialized
[   49.217300] Bluetooth: RFCOMM TTY layer initialized
[   49.217304] Bluetooth: RFCOMM ver 1.8
[   50.061546] sky2 eth0: Link is up at 100 Mbps, full duplex, flow control both
[   51.587079] [drm] Initialized drm 1.1.0 20060810
[   51.590871] ACPI: PCI Interrupt 0000:00:02.0[A] -> GSI 16 (level, low) -> IRQ 17
[   51.590885] PCI: Setting latency timer of device 0000:00:02.0 to 64
[   51.590970] [drm] Initialized i915 1.6.0 20060119 on minor 0
[   51.617184] mtrr: type mismatch for d0000000,10000000 old: write-back new: write-combining
[   51.996695] vmmon: module license 'unspecified' taints kernel.
[   51.998763] /dev/vmmon[5965]: Module vmmon: registered with major=10 minor=165
[   51.998787] /dev/vmmon[5965]: Module vmmon: initialized
[   52.182489] NET: Registered protocol family 17
[   52.510189] /dev/vmnet: open called by PID 6002 (vmnet-bridge)
[   52.510198] /dev/vmnet: hub 0 does not exist, allocating memory.
[   52.510208] /dev/vmnet: port on hub 0 successfully opened
[   52.510221] bridge-eth0: enabling the bridge
[   52.510226] bridge-eth0: up
[   52.510228] bridge-eth0: already up
[   52.510230] bridge-eth0: attached
[   52.538966] /dev/vmnet: open called by PID 6017 (vmnet-netifup)
[   52.538977] /dev/vmnet: hub 8 does not exist, allocating memory.
[   52.538987] /dev/vmnet: port on hub 8 successfully opened
[   52.542623] /dev/vmnet: open called by PID 6009 (vmnet-netifup)
[   52.542633] /dev/vmnet: hub 1 does not exist, allocating memory.
[   52.542643] /dev/vmnet: port on hub 1 successfully opened
[   52.565764] /dev/vmnet: open called by PID 6018 (vmnet-natd)
[   52.565778] /dev/vmnet: port on hub 8 successfully opened
[   53.005678] /dev/vmnet: open called by PID 6045 (vmnet-dhcpd)
[   53.005692] /dev/vmnet: port on hub 1 successfully opened
[   53.005880] /dev/vmnet: open called by PID 6044 (vmnet-dhcpd)
[   53.005886] /dev/vmnet: port on hub 8 successfully opened
[  184.705311] CPU0 attaching NULL sched-domain.
[  184.705318] CPU1 attaching NULL sched-domain.
[  184.705326] CPU0 attaching sched-domain:
[  184.705328]  domain 0: span 03
[  184.705330]   groups: 01 02
[  184.705334] CPU1 attaching sched-domain:
[  184.705336]  domain 0: span 03
[  184.705338]   groups: 02 01

```

---

### Post by Daelyn on 2008-08-09
Search the forum a bit. There are many threads about suspend problems.

Also, this might help you a bit.

[https://wiki.ubuntu.com/DebuggingKernelSuspend](https://wiki.ubuntu.com/DebuggingKernelSuspend)

---

