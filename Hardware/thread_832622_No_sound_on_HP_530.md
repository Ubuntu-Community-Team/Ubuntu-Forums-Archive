---
title: "No sound on HP 530"
date: 2008-06-17
forum: Hardware
---

### Post by Azmodanino on 2008-06-17
Hi;
I just installed kubuntu on a laptop HP 530, but i can't get sound on KDE, thought i get sound when i run speaker-test

here's the dmesg output:# dmesg
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.24-18-generic (buildd@terranova) (gcc version 4.2.3 (Ubuntu 4.2.3-2ubuntu7)) #1 SMP Wed May 28 20:27:26 UTC 2008 (Ubuntu 2.6.24-18.32-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000003f7d0000 (usable)
[    0.000000]  BIOS-e820: 000000003f7d0000 - 000000003f7e5600 (reserved)
[    0.000000]  BIOS-e820: 000000003f7e5600 - 000000003f7f8000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000003f7f8000 - 000000003f800000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed20000 - 00000000fed9b000 (reserved)
[    0.000000]  BIOS-e820: 00000000feda0000 - 00000000fedc0000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000ffb00000 - 00000000ffc00000 (reserved)
[    0.000000]  BIOS-e820: 00000000fff00000 - 0000000100000000 (reserved)
[    0.000000] 119MB HIGHMEM available.
[    0.000000] 896MB LOWMEM available.
[    0.000000] Entering add_active_range(0, 0, 260048) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   229376
[    0.000000]   HighMem    229376 ->   260048
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   260048
[    0.000000] On node 0 totalpages: 260048
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 1760 pages used for memmap
[    0.000000]   Normal zone: 223520 pages, LIFO batch:31
[    0.000000]   HighMem zone: 239 pages used for memmap
[    0.000000]   HighMem zone: 30433 pages, LIFO batch:7
[    0.000000]   Movable zone: 0 pages used for memmap
[    0.000000] DMI 2.4 present.
[    0.000000] ACPI: RSDP signature @ 0xC00F7830 checksum 0
[    0.000000] ACPI: RSDP 000F7830, 0024 (r2 HP    )
[    0.000000] ACPI: XSDT 3F7E57C8, 007C (r1 HPQOEM SLIC-MPC        1 HP          1)
[    0.000000] ACPI: FACP 3F7E5684, 00F4 (r4 HP     30D5            3 HP          1)
[    0.000000] ACPI: DSDT 3F7E5ACC, E974 (r1 HP       hp 520    10000 MSFT  100000E)
[    0.000000] ACPI: FACS 3F7F7E80, 0040
[    0.000000] ACPI: SLIC 3F7E5844, 0176 (r1 HPQOEM SLIC-MPC        1 HP          1)
[    0.000000] ACPI: HPET 3F7E59BC, 0038 (r1 HP     30D5            1 HP          1)
[    0.000000] ACPI: APIC 3F7E59F4, 0068 (r1 HP     30D5            1 HP          1)
[    0.000000] ACPI: MCFG 3F7E5A5C, 003C (r1 HP     30D5            1 HP          1)
[    0.000000] ACPI: TCPA 3F7E5A98, 0032 (r2 HP     30D5            1 HP          1)
[    0.000000] ACPI: SSDT 3F7F4440, 0024 (r1 HP       HPQNLP        1 MSFT  100000E)
[    0.000000] ACPI: SSDT 3F7F4464, 0326 (r1 HP       HPQSAT        1 MSFT  100000E)
[    0.000000] ACPI: SSDT 3F7F4F9D, 025F (r1 HP      Cpu0Tst     3000 INTL 20060317)
[    0.000000] ACPI: SSDT 3F7F51FC, 00A6 (r1 HP      Cpu1Tst     3000 INTL 20060317)
[    0.000000] ACPI: SSDT 3F7F52A2, 04D7 (r1 HP        CpuPm     3000 INTL 20060317)
[    0.000000] ACPI: DMI detected: Hewlett-Packard
[    0.000000] ACPI: PM-Timer IO Port: 0x1008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] Processor #0 6:14 APIC version 20
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
[    0.000000] Processor #1 6:14 APIC version 20
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x02] high edge lint[0x1])
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
[    0.000000] Allocating PCI resources starting at 40000000 (gap: 3f800000:bf400000)
[    0.000000] swsusp: Registered nosave memory region: 000000000009f000 - 00000000000a0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000a0000 - 00000000000e0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000e0000 - 0000000000100000
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 258017
[    0.000000] Kernel command line: root=UUID=24bdd6aa-a321-4fb3-869f-f9d59b8adfdf ro quiet splash modeprobe ps2
[    0.000000] mapped APIC to ffffb000 (fee00000)
[    0.000000] mapped IOAPIC to ffffa000 (fec00000)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] Detected 1828.824 MHz processor.
[    8.860819] Console: colour VGA+ 80x25
[    8.860822] console [tty0] enabled
[    8.861079] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    8.861424] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    8.887329] Memory: 1018660k/1040192k available (2176k kernel code, 20836k reserved, 1006k data, 368k init, 122688k highmem)
[    8.887337] virtual kernel memory layout:
[    8.887338]     fixmap  : 0xfff4b000 - 0xfffff000   ( 720 kB)
[    8.887339]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[    8.887341]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
[    8.887342]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
[    8.887343]       .init : 0xc0421000 - 0xc047d000   ( 368 kB)
[    8.887344]       .data : 0xc03201f4 - 0xc041bdc4   (1006 kB)
[    8.887345]       .text : 0xc0100000 - 0xc03201f4   (2176 kB)
[    8.887349] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[    8.887380] SLUB: Genslabs=11, HWalign=64, Order=0-1, MinObjects=4, CPUs=2, Nodes=1
[    8.887519] hpet clockevent registered
[    8.967390] Calibrating delay using timer specific routine.. 3661.66 BogoMIPS (lpj=7323337)
[    8.967407] Security Framework initialized
[    8.967414] SELinux:  Disabled at boot.
[    8.967427] AppArmor: AppArmor initialized
[    8.967431] Failure registering capabilities with primary security module.
[    8.967438] Mount-cache hash table entries: 512
[    8.967545] Initializing cgroup subsys ns
[    8.967549] Initializing cgroup subsys cpuacct
[    8.967559] CPU: After generic identify, caps: bfe9fbff 00100000 00000000 00000000 0000c1a9 00000000 00000000 00000000
[    8.967566] monitor/mwait feature present.
[    8.967568] using mwait in idle threads.
[    8.967571] CPU: L1 I cache: 32K, L1 D cache: 32K
[    8.967574] CPU: L2 cache: 2048K
[    8.967576] CPU: Physical Processor ID: 0
[    8.967578] CPU: Processor Core ID: 0
[    8.967580] CPU: After all inits, caps: bfe9fbff 00100000 00000000 00002940 0000c1a9 00000000 00000000 00000000
[    8.967588] Compat vDSO mapped to ffffe000.
[    8.967599] Checking 'hlt' instruction... OK.
[    8.983737] SMP alternatives: switching to UP code
[    8.985444] Early unpacking initramfs... done
[    9.332995] ACPI: Core revision 20070126
[    9.333099] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[    9.372140] CPU0: Intel(R) Core(TM) Duo CPU      T2400  @ 1.83GHz stepping 0c
[    9.372157] SMP alternatives: switching to SMP code
[    9.372807] Booting processor 1/1 eip 3000
[    9.383015] Initializing CPU#1
[    9.462544] Calibrating delay using timer specific routine.. 3657.54 BogoMIPS (lpj=7315093)
[    9.462550] CPU: After generic identify, caps: bfe9fbff 00100000 00000000 00000000 0000c1a9 00000000 00000000 00000000
[    9.462556] monitor/mwait feature present.
[    9.462559] CPU: L1 I cache: 32K, L1 D cache: 32K
[    9.462561] CPU: L2 cache: 2048K
[    9.462563] CPU: Physical Processor ID: 0
[    9.462564] CPU: Processor Core ID: 1
[    9.462566] CPU: After all inits, caps: bfe9fbff 00100000 00000000 00002940 0000c1a9 00000000 00000000 00000000
[    9.463125] CPU1: Intel(R) Core(TM) Duo CPU      T2400  @ 1.83GHz stepping 0c
[    9.463147] Total of 2 processors activated (7319.21 BogoMIPS).
[    9.463342] ENABLING IO-APIC IRQs
[    9.463533] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[    9.610408] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
[    9.630391] Brought up 2 CPUs
[    9.630417] CPU0 attaching sched-domain:
[    9.630420]  domain 0: span 03
[    9.630422]   groups: 01 02
[    9.630425] CPU1 attaching sched-domain:
[    9.630426]  domain 0: span 03
[    9.630428]   groups: 02 01
[    9.630672] net_namespace: 64 bytes
[    9.630682] Booting paravirtualized kernel on bare hardware
[    9.631127] Time:  4:45:40  Date: 06/18/08
[    9.631156] NET: Registered protocol family 16
[    9.631361] EISA bus registered
[    9.631366] ACPI: bus type pci registered
[    9.632642] PCI: PCI BIOS revision 2.10 entry at 0xf0322, last bus=16
[    9.632644] PCI: Using configuration type 1
[    9.632646] Setting up standard PCI resources
[    9.634519] ACPI: EC: Look up EC in DSDT
[    9.636042] ACPI: EC: non-query interrupt received, switching to interrupt mode
[    9.656989] ACPI: Interpreter enabled
[    9.656993] ACPI: (supports S0 S3 S4 S5)
[    9.657004] ACPI: Using IOAPIC for interrupt routing
[    9.663595] ACPI: EC: GPE = 0x16, I/O: command/status = 0x66, data = 0x62
[    9.663597] ACPI: EC: driver started in interrupt mode
[    9.663651] ACPI: PCI Root Bridge [C002] (0000:00)
[    9.664242] PCI quirk: region 1000-107f claimed by ICH6 ACPI/GPIO/TCO
[    9.664246] PCI quirk: region 1100-113f claimed by ICH6 GPIO
[    9.665023] PCI: Transparent bridge - 0000:00:1e.0
[    9.665106] ACPI: PCI Interrupt Routing Table [\_SB_.C002._PRT]
[    9.665372] ACPI: PCI Interrupt Routing Table [\_SB_.C002.C098._PRT]
[    9.665520] ACPI: PCI Interrupt Routing Table [\_SB_.C002.C100._PRT]
[    9.665643] ACPI: PCI Interrupt Routing Table [\_SB_.C002.C110._PRT]
[    9.681342] ACPI: PCI Interrupt Link [C10C] (IRQs *10 11)
[    9.681533] ACPI: PCI Interrupt Link [C10D] (IRQs *10 11)
[    9.681717] ACPI: PCI Interrupt Link [C10E] (IRQs 10 *11)
[    9.681894] ACPI: PCI Interrupt Link [C10F] (IRQs 10 11) *0, disabled.
[    9.682078] ACPI: PCI Interrupt Link [C11C] (IRQs 10 11) *5
[    9.682266] ACPI: PCI Interrupt Link [C11D] (IRQs *10 11)
[    9.682443] ACPI: PCI Interrupt Link [C11E] (IRQs 10 11) *0, disabled.
[    9.682532] ACPI Exception (pci_link-0184): AE_NOT_FOUND, Evaluating _PRS [20070126]
[    9.682701] ACPI: Power Resource [C1FE] (on)
[    9.682744] ACPI: Power Resource [C206] (on)
[    9.682838] ACPI: Power Resource [C2EE] (off)
[    9.682925] ACPI: Power Resource [C2EF] (off)
[    9.683018] ACPI: Power Resource [C2F0] (off)
[    9.683106] ACPI: Power Resource [C2F1] (off)
[    9.683159] Linux Plug and Play Support v0.97 (c) Adam Belay
[    9.683191] pnp: PnP ACPI init
[    9.683198] ACPI: bus type pnp registered
[    9.689223] pnp: PnP ACPI: found 12 devices
[    9.689225] ACPI: ACPI bus type pnp unregistered
[    9.689229] PnPBIOS: Disabled by ACPI PNP
[    9.689465] PCI: Using ACPI for IRQ routing
[    9.689467] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[    9.770153] NET: Registered protocol family 8
[    9.770155] NET: Registered protocol family 20
[    9.770189] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[    9.770194] hpet0: 3 64-bit timers, 14318180 Hz
[    9.771227] AppArmor: AppArmor Filesystem Enabled
[    9.774022] Time: tsc clocksource has been installed.
[    9.774037] Switched to high resolution mode on CPU 0
[    9.774143] Switched to high resolution mode on CPU 1
[    9.786994] system 00:00: iomem range 0x0-0x9ffff could not be reserved
[    9.786997] system 00:00: iomem range 0xe0000-0xfffff could not be reserved
[    9.787000] system 00:00: iomem range 0x100000-0x3f7fffff could not be reserved
[    9.787010] system 00:09: ioport range 0x500-0x57f has been reserved
[    9.787013] system 00:09: ioport range 0x800-0x80f has been reserved
[    9.787016] system 00:09: iomem range 0xffb00000-0xffbfffff could not be reserved
[    9.787020] system 00:09: iomem range 0xfff00000-0xffffffff could not be reserved
[    9.787025] system 00:0a: ioport range 0x4d0-0x4d1 has been reserved
[    9.787028] system 00:0a: ioport range 0x1000-0x107f has been reserved
[    9.787031] system 00:0a: ioport range 0x1100-0x113f has been reserved
[    9.787033] system 00:0a: ioport range 0x1200-0x121f has been reserved
[    9.787036] system 00:0a: iomem range 0xf8000000-0xfbffffff has been reserved
[    9.787039] system 00:0a: iomem range 0xfec00000-0xfec000ff could not be reserved
[    9.787042] system 00:0a: iomem range 0xfed20000-0xfed3ffff could not be reserved
[    9.787045] system 00:0a: iomem range 0xfed45000-0xfed8ffff could not be reserved
[    9.787048] system 00:0a: iomem range 0xfed90000-0xfed9afff could not be reserved
[    9.787054] system 00:0b: iomem range 0xfeda0000-0xfedbffff could not be reserved
[    9.787057] system 00:0b: iomem range 0xfee00000-0xfee00fff could not be reserved
[    9.817436] PCI: Bridge: 0000:00:1c.0
[    9.817438]   IO window: disabled.
[    9.817443]   MEM window: disabled.
[    9.817448]   PREFETCH window: disabled.
[    9.817453] PCI: Bridge: 0000:00:1c.1
[    9.817455]   IO window: disabled.
[    9.817460]   MEM window: f0000000-f00fffff
[    9.817465]   PREFETCH window: disabled.
[    9.817474] PCI: Bus 3, cardbus bridge: 0000:02:06.0
[    9.817476]   IO window: 00002400-000024ff
[    9.817481]   IO window: 00002800-000028ff
[    9.817486]   PREFETCH window: 40000000-43ffffff
[    9.817491]   MEM window: 44000000-47ffffff
[    9.817496] PCI: Bridge: 0000:00:1e.0
[    9.817499]   IO window: 2000-2fff
[    9.817505]   MEM window: f0100000-f03fffff
[    9.817509]   PREFETCH window: disabled.
[    9.817539] ACPI: PCI Interrupt 0000:00:1c.0[A] -> GSI 16 (level, low) -> IRQ 16
[    9.817546] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[    9.817569] ACPI: PCI Interrupt 0000:00:1c.1[B] -> GSI 17 (level, low) -> IRQ 17
[    9.817575] PCI: Setting latency timer of device 0000:00:1c.1 to 64
[    9.817588] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[    9.817606] ACPI: PCI Interrupt 0000:02:06.0[A] -> GSI 18 (level, low) -> IRQ 18
[    9.817619] NET: Registered protocol family 2
[    9.854902] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    9.855107] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    9.855795] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    9.856142] TCP: Hash tables configured (established 131072 bind 65536)
[    9.856145] TCP reno registered
[    9.866972] checking if image is initramfs... it is
[   10.556246] Freeing initrd memory: 7731k freed
[   10.557107] audit: initializing netlink socket (disabled)
[   10.557122] audit(1213764340.516:1): initialized
[   10.557311] highmem bounce pool size: 64 pages
[   10.559278] VFS: Disk quotas dquot_6.5.1
[   10.559353] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   10.559487] io scheduler noop registered
[   10.559489] io scheduler anticipatory registered
[   10.559491] io scheduler deadline registered
[   10.559502] io scheduler cfq registered (default)
[   10.559513] Boot video device is 0000:00:02.0
[   10.559562] PCI: Firmware left 0000:02:08.0 e100 interrupts enabled, disabling
[   10.559669] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[   10.559724] assign_interrupt_mode Found MSI capability
[   10.559774] Allocate Port Service[0000:00:1c.0:pcie00]
[   10.559809] Allocate Port Service[0000:00:1c.0:pcie02]
[   10.559906] PCI: Setting latency timer of device 0000:00:1c.1 to 64
[   10.559962] assign_interrupt_mode Found MSI capability
[   10.560006] Allocate Port Service[0000:00:1c.1:pcie00]
[   10.560040] Allocate Port Service[0000:00:1c.1:pcie02]
[   10.560304] isapnp: Scanning for PnP cards...
[   10.914031] isapnp: No Plug & Play device found
[   10.940381] Real Time Clock Driver v1.12ac
[   10.940626] hpet_resources: 0xfed00000 is busy
[   10.940678] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   10.942361] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   10.942428] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[   10.942530] PNP: PS/2 Controller [PNP0303:C1FB,PNP0f13:C1FC] at 0x60,0x64 irq 1,12
[   10.944384] i8042.c: Detected active multiplexing controller, rev 1.1.
[   10.945133] serio: i8042 KBD port at 0x60,0x64 irq 1
[   10.945138] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[   10.945141] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[   10.945144] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[   10.945146] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[   10.968046] mice: PS/2 mouse device common for all mice
[   10.968158] EISA: Probing bus 0 at eisa.0
[   10.968165] Cannot allocate resource for EISA slot 1
[   10.968167] Cannot allocate resource for EISA slot 2
[   10.968169] Cannot allocate resource for EISA slot 3
[   10.968191] EISA: Detected 0 cards.
[   10.968194] cpuidle: using governor ladder
[   10.968196] cpuidle: using governor menu
[   10.968288] NET: Registered protocol family 1
[   10.968315] Using IPI No-Shortcut mode
[   10.968344] registered taskstats version 1
[   10.968433]   Magic number: 12:10:768
[   10.968494]   hash matches device ptyp4
[   10.968521] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[   10.968523] EDD information not available.
[   10.968705] Freeing unused kernel memory: 368k freed
[   10.995930] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[   12.169682] fuse init (API version 7.9)
[   12.186316] ACPI: Transitioning device [C2F2] to D3
[   12.186319] ACPI: Transitioning device [C2F2] to D3
[   12.186322] ACPI: Fan [C2F2] (off)
[   12.186489] ACPI: Transitioning device [C2F3] to D3
[   12.186492] ACPI: Transitioning device [C2F3] to D3
[   12.186494] ACPI: Fan [C2F3] (off)
[   12.186659] ACPI: Transitioning device [C2F4] to D3
[   12.186661] ACPI: Transitioning device [C2F4] to D3
[   12.186664] ACPI: Fan [C2F4] (off)
[   12.186829] ACPI: Transitioning device [C2F5] to D3
[   12.186831] ACPI: Transitioning device [C2F5] to D3
[   12.186834] ACPI: Fan [C2F5] (off)
[   12.193240] ACPI: SSDT 3F7F4852, 01FB (r1 HP      Cpu0Ist     3000 INTL 20060317)
[   12.193451] ACPI: SSDT 3F7F4AD2, 04CB (r1 HP      Cpu0Cst     3001 INTL 20060317)
[   12.199465] ACPI: CPU0 (power states: C1[C1] C2[C2])
[   12.199470] ACPI: Processor [CPU0] (supports 8 throttling states)
[   12.199670] ACPI: SSDT 3F7F478A, 00C8 (r1 HP      Cpu1Ist     3000 INTL 20060317)
[   12.199864] ACPI: SSDT 3F7F4A4D, 0085 (r1 HP      Cpu1Cst     3000 INTL 20060317)
[   12.200751] ACPI: CPU1 (power states: C1[C1] C2[C2])
[   12.200756] ACPI: Processor [CPU1] (supports 8 throttling states)
[   12.223716] ACPI: Thermal Zone [TZ0] (35 C)
[   12.238065] ACPI: Thermal Zone [TZ1] (40 C)
[   12.251956] ACPI: Thermal Zone [TZ2] (31 C)
[   12.260692] ACPI: Thermal Zone [TZ3] (16 C)
[   12.264316] ACPI: Thermal Zone [TZ4] (65 C)
[   12.685400] usbcore: registered new interface driver usbfs
[   12.685423] usbcore: registered new interface driver hub
[   12.685483] usbcore: registered new device driver usb
[   12.686603] USB Universal Host Controller Interface driver v3.0
[   12.686657] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 20 (level, low) -> IRQ 19
[   12.686667] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[   12.686672] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[   12.686907] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[   12.686939] uhci_hcd 0000:00:1d.0: irq 19, io base 0x00003020
[   12.687065] usb usb1: configuration #1 chosen from 1 choice
[   12.687089] hub 1-0:1.0: USB hub found
[   12.687094] hub 1-0:1.0: 2 ports detected
[   12.827133] SCSI subsystem initialized
[   12.830045] ACPI: PCI Interrupt 0000:00:1d.7[A] -> GSI 20 (level, low) -> IRQ 19
[   12.830058] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[   12.830062] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[   12.830089] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 2
[   12.834005] ehci_hcd 0000:00:1d.7: debug port 1
[   12.834012] PCI: cache line size of 32 is not supported by device 0000:00:1d.7
[   12.834021] ehci_hcd 0000:00:1d.7: irq 19, io mem 0xf0584000
[   12.839662] e100: Intel(R) PRO/100 Network Driver, 3.5.23-k4-NAPI
[   12.839665] e100: Copyright(c) 1999-2006 Intel Corporation
[   12.848769] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   12.848879] usb usb2: configuration #1 chosen from 1 choice
[   12.848903] hub 2-0:1.0: USB hub found
[   12.848910] hub 2-0:1.0: 8 ports detected
[   12.859390] libata version 3.00 loaded.
[   12.952747] ACPI: PCI Interrupt 0000:02:08.0[A] -> GSI 20 (level, low) -> IRQ 19
[   12.979170] e100: eth0: e100_probe: addr 0xf0101000, irq 19, MAC addr 00:1b:38:e7:0b:43
[   12.979200] ata_piix 0000:00:1f.1: version 2.12
[   12.979218] ACPI: PCI Interrupt 0000:00:1f.1[A] -> GSI 16 (level, low) -> IRQ 16
[   12.979254] PCI: Setting latency timer of device 0000:00:1f.1 to 64
[   12.979425] scsi0 : ata_piix
[   12.979480] scsi1 : ata_piix
[   12.979934] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0x3040 irq 14
[   12.979937] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x3048 irq 15
[   13.296509] ata1.00: ATAPI: Optiarc DVD RW AD-7530B, NH02, max MWDMA2
[   13.468176] ata1.00: configured for MWDMA2
[   13.468237] ata2: port disabled. ignoring.
[   13.469650] scsi 0:0:0:0: CD-ROM            Optiarc  DVD RW AD-7530B  NH02 PQ: 0 ANSI: 5
[   13.470048] ahci 0000:00:1f.2: version 3.0
[   13.470079] ACPI: PCI Interrupt 0000:00:1f.2[B] -> GSI 21 (level, low) -> IRQ 20
[   13.470125] ahci 0000:00:1f.2: nr_ports (4) and implemented port map (0x1) don't match, using nr_ports
[   13.470127] ahci 0000:00:1f.2: forcing PORTS_IMPL to 0xf
[   14.470057] ahci 0000:00:1f.2: AHCI 0001.0100 32 slots 4 ports 1.5 Gbps 0xf impl SATA mode
[   14.470065] ahci 0000:00:1f.2: flags: 64bit ncq ilck stag pm led clo pmp pio slum part
[   14.470074] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[   14.470366] scsi2 : ahci
[   14.470550] scsi3 : ahci
[   14.470681] scsi4 : ahci
[   14.470816] scsi5 : ahci
[   14.470877] ata3: SATA max UDMA/133 abar m1024@0xf0585000 port 0xf0585100 irq 221
[   14.470881] ata4: SATA max UDMA/133 abar m1024@0xf0585000 port 0xf0585180 irq 221
[   14.470885] ata5: SATA max UDMA/133 abar m1024@0xf0585000 port 0xf0585200 irq 221
[   14.470888] ata6: SATA max UDMA/133 abar m1024@0xf0585000 port 0xf0585280 irq 221
[   15.108936] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[   15.111070] ata3.00: ACPI cmd f5/00:00:00:00:00:a0 filtered out
[   15.111073] ata3.00: ACPI cmd b1/c1:00:00:00:00:a0 filtered out
[   15.111190] ata3.00: ACPI cmd c6/00:10:00:00:00:a0 succeeded
[   15.111314] ata3.00: ACPI cmd ef/10:03:00:00:00:a0 succeeded
[   15.111704] ata3.00: ATA-8: FUJITSU MHY2120BH, 890B, max UDMA/100
[   15.111709] ata3.00: 234441648 sectors, multi 16: LBA48
[   15.113867] ata3.00: ACPI cmd f5/00:00:00:00:00:a0 filtered out
[   15.113870] ata3.00: ACPI cmd b1/c1:00:00:00:00:a0 filtered out
[   15.113980] ata3.00: ACPI cmd c6/00:10:00:00:00:a0 succeeded
[   15.114104] ata3.00: ACPI cmd ef/10:03:00:00:00:a0 succeeded
[   15.114511] ata3.00: configured for UDMA/100
[   15.115480] ata3.00: configured for UDMA/100
[   15.115485] ata3: EH complete
[   15.432382] ata4: SATA link down (SStatus 0 SControl 0)
[   15.751838] ata5: SATA link down (SStatus 0 SControl 0)
[   16.071293] ata6: SATA link down (SStatus 0 SControl 0)
[   16.071496] scsi 2:0:0:0: Direct-Access     ATA      FUJITSU MHY2120B 890B PQ: 0 ANSI: 5
[   16.083134] Driver 'sd' needs updating - please use bus_type methods
[   16.085615] Driver 'sr' needs updating - please use bus_type methods
[   16.091333] sd 2:0:0:0: [sda] 234441648 512-byte hardware sectors (120034 MB)
[   16.091370] sd 2:0:0:0: [sda] Write Protect is off
[   16.091376] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   16.091436] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   16.091524] sd 2:0:0:0: [sda] 234441648 512-byte hardware sectors (120034 MB)
[   16.091543] sd 2:0:0:0: [sda] Write Protect is off
[   16.091547] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   16.091588] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   16.091595]  sda:sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[   16.098238] Uniform CD-ROM driver Revision: 3.20
[   16.098309] sr 0:0:0:0: Attached scsi CD-ROM sr0
[   16.162667]  sda1 < sda5 sda6 sda7 sda8 > sda2 sda3
[   16.216829] sd 2:0:0:0: [sda] Attached SCSI disk
[   16.220882] sr 0:0:0:0: Attached scsi generic sg0 type 5
[   16.220902] sd 2:0:0:0: Attached scsi generic sg1 type 0
[   16.754912] Attempting manual resume
[   16.754915] swsusp: Resume From Partition 8:7
[   16.754917] PM: Checking swsusp image.
[   16.755121] PM: Resume from disk failed.
[   16.786480] kjournald starting.  Commit interval 5 seconds
[   16.786501] EXT3-fs: mounted filesystem with ordered data mode.
[   25.061887] input: PC Speaker as /devices/platform/pcspkr/input/input2
[   25.192718] intel_rng: FWH not detected
[   25.206473] Linux agpgart interface v0.102
[   25.244682] agpgart: Detected an Intel 945GME Chipset.
[   25.245675] agpgart: Detected 7932K stolen memory.
[   25.261270] agpgart: AGP aperture is 256M @ 0xe0000000
[   25.308549] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   25.348508] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   25.530338] iTCO_vendor_support: vendor-support=0
[   25.547188] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.02 (26-Jul-2007)
[   25.547281] iTCO_wdt: Found a ICH7-M TCO device (Version=2, TCOBASE=0x1060)
[   25.547317] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   25.592162] ACPI: AC Adapter [C1AB] (on-line)
[   25.608879] input: Power Button (FF) as /devices/virtual/input/input3
[   25.666902] ACPI: Power Button (FF) [PWRF]
[   25.666992] input: Sleep Button (CM) as /devices/virtual/input/input4
[   25.730808] ACPI: Sleep Button (CM) [C20B]
[   25.730868] input: Lid Switch as /devices/virtual/input/input5
[   25.762854] ACPI: Lid Switch [C20C]
[   25.762965] ACPI: WMI-Acer: Mapper loaded
[   25.966729] ACPI: Battery Slot [C1AC] (battery absent)
[   26.353833] Yenta: CardBus bridge found at 0000:02:06.0 [103c:30d5]
[   26.353861] Yenta: Using CSCINT to route CSC interrupts to PCI
[   26.353863] Yenta: Routing CardBus interrupts to PCI
[   26.353868] Yenta TI: socket 0000:02:06.0, mfunc 0x01be1b32, devctl 0x44
[   26.482901] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/LNXVIDEO:00/input/input6
[   26.549398] ACPI: Video Device [C085] (multi-head: yes  rom: no  post: no)
[   26.586132] Yenta: ISA IRQ mask 0x0cf8, PCI irq 18
[   26.586137] Socket status: 30000006
[   26.586140] Yenta: Raising subordinate bus# of parent bus (#02) from #03 to #06
[   26.586145] pcmcia: parent PCI bridge I/O window: 0x2000 - 0x2fff
[   26.586147] cs: IO port probe 0x2000-0x2fff: clean.
[   26.586378] pcmcia: parent PCI bridge Memory window: 0xf0100000 - 0xf03fffff
[   26.778111] Synaptics Touchpad, model: 1, fw: 6.3, id: 0x1a0b1, caps: 0xa04713/0x200000
[   26.822464] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio4/input/input7
[   27.033170] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 16 (level, low) -> IRQ 16
[   27.033198] PCI: Setting latency timer of device 0000:00:1b.0 to 64
[   27.038071] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, 1.2.0
[   27.038075] iwl3945: Copyright(c) 2003-2007 Intel Corporation
[   27.097681] ACPI: PCI Interrupt 0000:10:00.0[A] -> GSI 17 (level, low) -> IRQ 17
[   27.097698] PCI: Setting latency timer of device 0000:10:00.0 to 64
[   27.097719] iwl3945: Detected Intel PRO/Wireless 3945ABG Network Connection
[   27.574451] iwl3945: Radio Frequency Kill Switch is On:
[   27.574455] Kill switch must be turned off for wireless networking to work.
[   27.579630] iwl3945: WARNING: Requesting MAC access during RFKILL wakes up NIC
[   27.589638] iwl3945: WARNING: Requesting MAC access during RFKILL wakes up NIC
[   27.609564] iwl3945: WARNING: Requesting MAC access during RFKILL wakes up NIC
[   27.636962] iwl3945: WARNING: Requesting MAC access during RFKILL wakes up NIC
[   27.656941] iwl3945: Tunable channels: 11 802.11bg, 13 802.11a channels
[   27.858857] cs: IO port probe 0x100-0x3af: clean.
[   27.860889] cs: IO port probe 0x3e0-0x4ff: clean.
[   27.861718] cs: IO port probe 0x820-0x8ff: clean.
[   27.862400] cs: IO port probe 0xc00-0xcf7: clean.
[   27.863256] cs: IO port probe 0xa00-0xaff: clean.
[   27.987497] lp: driver loaded but no devices found
[   28.076533] Adding 975200k swap on /dev/sda7.  Priority:-1 extents:1 across:975200k
[   28.613532] EXT3 FS on sda6, internal journal
[   28.773989] device-mapper: uevent: version 1.0.3
[   28.774020] device-mapper: ioctl: 4.12.0-ioctl (2007-10-02) initialised: [email]dm-devel@redhat.com[/email]
[   30.003185] ip_tables: (C) 2000-2006 Netfilter Core Team
[   30.382388] No dock devices found.
[   31.463010] apm: BIOS not found.
[   31.617796] ppdev: user-space parallel port driver
[   31.739165] audit(1213753561.865:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=5078 profile="/usr/sbin/cupsd" namespace="default"
[   33.278989] e100: eth0: e100_watchdog: link up, 100Mbps, full-duplex
[   33.324138] Bluetooth: Core ver 2.11
[   33.324288] NET: Registered protocol family 31
[   33.324292] Bluetooth: HCI device and connection manager initialized
[   33.324299] Bluetooth: HCI socket layer initialized
[   33.390657] Bluetooth: L2CAP ver 2.9
[   33.390664] Bluetooth: L2CAP socket layer initialized
[   33.440618] Bluetooth: RFCOMM socket layer initialized
[   33.440630] Bluetooth: RFCOMM TTY layer initialized
[   33.440632] Bluetooth: RFCOMM ver 1.8
[   36.602033] NET: Registered protocol family 17
[   37.427156] [drm] Initialized drm 1.1.0 20060810
[   37.429949] ACPI: PCI Interrupt 0000:00:02.0[A] -> GSI 16 (level, low) -> IRQ 16
[   37.429959] PCI: Setting latency timer of device 0000:00:02.0 to 64
[   37.429992] DRM: Fill_in_dev failed.
[   37.429998] ACPI: PCI interrupt for device 0000:00:02.0 disabled
[   38.009993] NET: Registered protocol family 10
[   38.010362] lo: Disabled Privacy Extensions
[   48.072635] eth0: no IPv6 routers present


```

```


any help would be appreciated.

---

