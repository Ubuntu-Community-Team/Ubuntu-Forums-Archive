---
title: "TImedelay after splash screen"
date: 2009-10-30
forum: Installation &amp; Upgrades
---

### Post by apparle on 2009-10-30
The computer just displays a total black screen with a blinking cursor for 30 seconds after the Splash screen(boot screen) is over.
After that I get some 5-6 messages just for a split second and then the login screen is displayed.

I have Kubuntu karmic 9.10 fresh install (but tried on ubuntu also)

I have attached the kernel log(output of dmseg)
The time between these two lines(from the log) in 31sec. So I suspect that this is the problem.
```
[   10.129879] ATI IXP AC97 controller 0000:00:14.5: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[   42.816029] ata5: lost interrupt (Status 0x58)

```
What does this mean and why do I get it? Can this be fixed, if yes how?
I have freshly installed 9.10 karmic, though I suspect I used to get the same problem in jaunty but just before the splash screen.
Sorry I can't attach the file due to some problems, so here is the file

```
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.31-14-generic (buildd@rothera) (gcc version 4.4.1 (Ubuntu 4.4.1-4ubuntu8) ) #48-Ubuntu SMP Fri Oct 16 14:04:26 UTC 2009 (Ubuntu 2.6.31-14.48-generic)
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   NSC Geode by NSC
[    0.000000]   Cyrix CyrixInstead
[    0.000000]   Centaur CentaurHauls
[    0.000000]   Transmeta GenuineTMx86
[    0.000000]   Transmeta TransmetaCPU
[    0.000000]   UMC UMC UMC UMC
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f000 (usable)
[    0.000000]  BIOS-e820: 000000000009f000 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000004fef0000 (usable)
[    0.000000]  BIOS-e820: 000000004fef0000 - 000000004fef3000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000004fef3000 - 000000004ff00000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 0000000100000000 (reserved)
[    0.000000] DMI 2.2 present.
[    0.000000] Phoenix BIOS detected: BIOS may corrupt low RAM, working around it.
[    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
[    0.000000] last_pfn = 0x4fef0 max_arch_pfn = 0x100000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-CEFFF write-protect
[    0.000000]   CF000-EFFFF uncachable
[    0.000000]   F0000-FFFFF write-through
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000 mask FC0000000 write-back
[    0.000000]   1 base 040000000 mask FF0000000 write-back
[    0.000000]   2 base 04FF00000 mask FFFF00000 uncachable
[    0.000000]   3 disabled
[    0.000000]   4 disabled
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] Scanning 0 areas for low memory corruption
[    0.000000] modified physical RAM map:
[    0.000000]  modified: 0000000000000000 - 0000000000010000 (reserved)
[    0.000000]  modified: 0000000000010000 - 000000000009f000 (usable)
[    0.000000]  modified: 000000000009f000 - 00000000000a0000 (reserved)
[    0.000000]  modified: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  modified: 0000000000100000 - 000000004fef0000 (usable)
[    0.000000]  modified: 000000004fef0000 - 000000004fef3000 (ACPI NVS)
[    0.000000]  modified: 000000004fef3000 - 000000004ff00000 (ACPI data)
[    0.000000]  modified: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  modified: 00000000fec00000 - 0000000100000000 (reserved)
[    0.000000] initial memory mapped : 0 - 00c00000
[    0.000000] init_memory_mapping: 0000000000000000-00000000377fe000
[    0.000000] Using x86 segment limits to approximate NX protection
[    0.000000]  0000000000 - 0000400000 page 4k
[    0.000000]  0000400000 - 0037400000 page 2M
[    0.000000]  0037400000 - 00377fe000 page 4k
[    0.000000] kernel direct mapping tables up to 377fe000 @ 10000-15000
[    0.000000] RAMDISK: 378a2000 - 37feffc4
[    0.000000] Allocated new RAMDISK: 008ad000 - 00ffafc4
[    0.000000] Move RAMDISK from 00000000378a2000 - 0000000037feffc3 to 008ad000 - 00ffafc3
[    0.000000] ACPI: RSDP 000f87c0 00014 (v00 RS400 )
[    0.000000] ACPI: RSDT 4fef3040 00030 (v01 RS400  AWRDACPI 42302E31 AWRD 00000000)
[    0.000000] ACPI: FACP 4fef30c0 00074 (v01 RS400  AWRDACPI 42302E31 AWRD 00000000)
[    0.000000] ACPI: DSDT 4fef3180 0416F (v01 RS400  AWRDACPI 00001000 MSFT 0100000E)
[    0.000000] ACPI: FACS 4fef0000 00040
[    0.000000] ACPI: MCFG 4fef7440 0003C (v01 RS400  AWRDACPI 42302E31 AWRD 00000000)
[    0.000000] ACPI: APIC 4fef7340 00084 (v01 RS400  AWRDACPI 42302E31 AWRD 00000000)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] 390MB HIGHMEM available.
[    0.000000] 887MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 377fe000
[    0.000000]   low ram: 0 - 377fe000
[    0.000000]   node 0 low ram: 00000000 - 377fe000
[    0.000000]   node 0 bootmap 00011000 - 00017f00
[    0.000000] (9 early reservations) ==> bootmem [0000000000 - 00377fe000]
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000]   #1 [0000001000 - 0000002000]    EX TRAMPOLINE ==> [0000001000 - 0000002000]
[    0.000000]   #2 [0000006000 - 0000007000]       TRAMPOLINE ==> [0000006000 - 0000007000]
[    0.000000]   #3 [0000100000 - 00008a80a0]    TEXT DATA BSS ==> [0000100000 - 00008a80a0]
[    0.000000]   #4 [000009f000 - 0000100000]    BIOS reserved ==> [000009f000 - 0000100000]
[    0.000000]   #5 [00008a9000 - 00008ac072]              BRK ==> [00008a9000 - 00008ac072]
[    0.000000]   #6 [0000010000 - 0000011000]          PGTABLE ==> [0000010000 - 0000011000]
[    0.000000]   #7 [00008ad000 - 0000ffafc4]      NEW RAMDISK ==> [00008ad000 - 0000ffafc4]
[    0.000000]   #8 [0000011000 - 0000018000]          BOOTMAP ==> [0000011000 - 0000018000]
[    0.000000] found SMP MP-table at [c00f4070] f4070
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x000377fe
[    0.000000]   HighMem  0x000377fe -> 0x0004fef0
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[2] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x0000009f
[    0.000000]     0: 0x00000100 -> 0x0004fef0
[    0.000000] On node 0 totalpages: 327295
[    0.000000] free_area_init_node: node 0, pgdat c0784900, node_mem_map c1000200
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3951 pages, LIFO batch:0
[    0.000000]   Normal zone: 1744 pages used for memmap
[    0.000000]   Normal zone: 221486 pages, LIFO batch:31
[    0.000000]   HighMem zone: 782 pages used for memmap
[    0.000000]   HighMem zone: 99300 pages, LIFO batch:31
[    0.000000] Using APIC driver default
[    0.000000] ACPI: PM-Timer IO Port: 0x4008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x02] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x03] disabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x02] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x03] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x04] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 4, version 33, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 low level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] SMP: Allowing 4 CPUs, 2 hotplug CPUs
[    0.000000] nr_irqs_gsi: 24
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000f0000
[    0.000000] PM: Registered nosave memory: 00000000000f0000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 4ff00000 (gap: 4ff00000:90100000)
[    0.000000] NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:4 nr_node_ids:1
[    0.000000] PERCPU: Embedded 14 pages at c1a05000, static data 35612 bytes
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 324737
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.31-14-generic root=UUID=44fe68f7-66af-4e76-b9ad-37ad86b129a3 ro quiet splash
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] allocated 6547840 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] Initializing HighMem for node 0 (000377fe:0004fef0)
[    0.000000] Memory: 1275228k/1309632k available (4565k kernel code, 33032k reserved, 2143k data, 540k init, 400328k highmem)
[    0.000000] virtual kernel memory layout:
[    0.000000]     fixmap  : 0xfff1d000 - 0xfffff000   ( 904 kB)
[    0.000000]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[    0.000000]     vmalloc : 0xf7ffe000 - 0xff7fe000   ( 120 MB)
[    0.000000]     lowmem  : 0xc0000000 - 0xf77fe000   ( 887 MB)
[    0.000000]       .init : 0xc078e000 - 0xc0815000   ( 540 kB)
[    0.000000]       .data : 0xc0575554 - 0xc078d308   (2143 kB)
[    0.000000]       .text : 0xc0100000 - 0xc0575554   (4565 kB)
[    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.000000] SLUB: Genslabs=13, HWalign=128, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
[    0.000000] NR_IRQS:2304 nr_irqs:440
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 2799.890 MHz processor.
[    0.000913] Console: colour VGA+ 80x25
[    0.000918] console [tty0] enabled
[    0.004014] Calibrating delay loop (skipped), value calculated using timer frequency.. 5599.78 BogoMIPS (lpj=11199560)
[    0.004043] Security Framework initialized
[    0.004079] AppArmor: AppArmor initialized
[    0.004090] Mount-cache hash table entries: 512
[    0.004294] Initializing cgroup subsys ns
[    0.004303] Initializing cgroup subsys cpuacct
[    0.004309] Initializing cgroup subsys memory
[    0.004318] Initializing cgroup subsys freezer
[    0.004322] Initializing cgroup subsys net_cls
[    0.004348] CPU: Trace cache: 12K uops, L1 D cache: 16K
[    0.004352] CPU: L2 cache: 1024K
[    0.004356] CPU: Physical Processor ID: 0
[    0.004359] CPU: Processor Core ID: 0
[    0.004364] mce: CPU supports 4 MCE banks
[    0.004380] CPU0: Thermal monitoring enabled (TM1)
[    0.004387] using mwait in idle threads.
[    0.004398] Performance Counters: no PMU driver, software counters only.
[    0.004406] Checking 'hlt' instruction... OK.
[    0.023837] ACPI: Core revision 20090521
[    0.036456] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.076368] CPU0: Intel(R) Pentium(R) D CPU 2.80GHz stepping 07
[    0.080001] Booting processor 1 APIC 0x1 ip 0x6000
[    0.004000] Initializing CPU#1
[    0.004000] Calibrating delay using timer specific routine.. 5599.85 BogoMIPS (lpj=11199714)
[    0.004000] CPU: Trace cache: 12K uops, L1 D cache: 16K
[    0.004000] CPU: L2 cache: 1024K
[    0.004000] CPU: Physical Processor ID: 0
[    0.004000] CPU: Processor Core ID: 1
[    0.004000] mce: CPU supports 4 MCE banks
[    0.004000] CPU1: Thermal monitoring enabled (TM1)
[    0.004000] x86 PAT enabled: cpu 1, old 0x7040600070406, new 0x7010600070106
[    0.165020] CPU1: Intel(R) Pentium(R) D CPU 2.80GHz stepping 07
[    0.165040] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
[    0.168025] Brought up 2 CPUs
[    0.168030] Total of 2 processors activated (11199.63 BogoMIPS).
[    0.168089] CPU0 attaching sched-domain:
[    0.168094]  domain 0: span 0-1 level CPU
[    0.168098]   groups: 0 1
[    0.168107] CPU1 attaching sched-domain:
[    0.168111]  domain 0: span 0-1 level CPU
[    0.168115]   groups: 1 0
[    0.168213] Booting paravirtualized kernel on bare hardware
[    0.168303] regulator: core version 0.5
[    0.168303] Time:  2:24:49  Date: 10/31/09
[    0.168303] NET: Registered protocol family 16
[    0.168325] EISA bus registered
[    0.168341] ACPI: bus type pci registered
[    0.168442] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 255
[    0.168447] PCI: MCFG area at e0000000 reserved in E820
[    0.168450] PCI: Using MMCONFIG for extended config space
[    0.168453] PCI: Using configuration type 1 for base access
[    0.169926] bio: create slab <bio-0> at 0
[    0.172742] ACPI: EC: Look up EC in DSDT
[    0.181705] ACPI: Interpreter enabled
[    0.181712] ACPI: (supports S0 S1 S4 S5)
[    0.181742] ACPI: Using IOAPIC for interrupt routing
[    0.188111] ACPI: No dock devices found.
[    0.188258] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.188332] pci 0000:00:00.0: reg 10 32bit mmio: [0xf4000000-0xf7ffffff]
[    0.188340] pci 0000:00:00.0: reg 14 32bit mmio: [0xfdfff000-0xfdffffff]
[    0.188354] pci 0000:00:00.0: reg 1c 64bit mmio: [0xe0000000-0xffffffff]
[    0.188414] pci 0000:00:01.0: reg 10 32bit mmio: [0xf4000000-0xf7ffffff]
[    0.188538] pci 0000:00:11.0: reg 10 io port: [0xff00-0xff07]
[    0.188550] pci 0000:00:11.0: reg 14 io port: [0xfe00-0xfe03]
[    0.188561] pci 0000:00:11.0: reg 18 io port: [0xfd00-0xfd07]
[    0.188573] pci 0000:00:11.0: reg 1c io port: [0xfc00-0xfc03]
[    0.188584] pci 0000:00:11.0: reg 20 io port: [0xfb00-0xfb0f]
[    0.188596] pci 0000:00:11.0: reg 24 32bit mmio: [0xfdffe000-0xfdffe1ff]
[    0.188608] pci 0000:00:11.0: reg 30 32bit mmio: [0x000000-0x07ffff]
[    0.188651] pci 0000:00:11.0: supports D1 D2
[    0.188730] pci 0000:00:12.0: reg 10 io port: [0xfa00-0xfa07]
[    0.188742] pci 0000:00:12.0: reg 14 io port: [0xf900-0xf903]
[    0.188753] pci 0000:00:12.0: reg 18 io port: [0xf800-0xf807]
[    0.188765] pci 0000:00:12.0: reg 1c io port: [0xf700-0xf703]
[    0.188776] pci 0000:00:12.0: reg 20 io port: [0xf600-0xf60f]
[    0.188788] pci 0000:00:12.0: reg 24 32bit mmio: [0xfdffd000-0xfdffd1ff]
[    0.188800] pci 0000:00:12.0: reg 30 32bit mmio: [0x000000-0x07ffff]
[    0.188843] pci 0000:00:12.0: supports D1 D2
[    0.188906] pci 0000:00:13.0: reg 10 32bit mmio: [0xfdffc000-0xfdffcfff]
[    0.189045] pci 0000:00:13.1: reg 10 32bit mmio: [0xfdffb000-0xfdffbfff]
[    0.189195] pci 0000:00:13.2: reg 10 32bit mmio: [0xfdffa000-0xfdffafff]
[    0.189285] pci 0000:00:13.2: supports D1 D2
[    0.189288] pci 0000:00:13.2: PME# supported from D0 D1 D2 D3hot
[    0.189296] pci 0000:00:13.2: PME# disabled
[    0.189349] pci 0000:00:14.0: reg 10 io port: [0x500-0x50f]
[    0.189361] pci 0000:00:14.0: reg 14 32bit mmio: [0xfdff9000-0xfdff93ff]
[    0.189408] HPET not enabled in BIOS. You might try hpet=force boot option
[    0.189468] pci 0000:00:14.1: reg 10 io port: [0x00-0x07]
[    0.189479] pci 0000:00:14.1: reg 14 io port: [0x00-0x03]
[    0.189491] pci 0000:00:14.1: reg 18 io port: [0x00-0x07]
[    0.189502] pci 0000:00:14.1: reg 1c io port: [0x00-0x03]
[    0.189513] pci 0000:00:14.1: reg 20 io port: [0xf400-0xf40f]
[    0.189761] pci 0000:00:14.5: reg 10 32bit mmio: [0xfdff8000-0xfdff80ff]
[    0.189919] pci 0000:01:05.0: reg 10 32bit mmio: [0xd0000000-0xdfffffff]
[    0.189926] pci 0000:01:05.0: reg 14 io port: [0xee00-0xeeff]
[    0.189933] pci 0000:01:05.0: reg 18 32bit mmio: [0xfdef0000-0xfdefffff]
[    0.189951] pci 0000:01:05.0: reg 30 32bit mmio: [0x000000-0x01ffff]
[    0.189972] pci 0000:01:05.0: supports D1 D2
[    0.190006] pci 0000:01:05.1: reg 10 32bit mmio: [0x000000-0xfffffff]
[    0.190014] pci 0000:01:05.1: reg 14 32bit mmio: [0x000000-0x00ffff]
[    0.190048] pci 0000:01:05.1: supports D1 D2
[    0.190090] pci 0000:00:01.0: bridge io port: [0xe000-0xefff]
[    0.190095] pci 0000:00:01.0: bridge 32bit mmio: [0xfde00000-0xfdefffff]
[    0.190100] pci 0000:00:01.0: bridge 32bit mmio pref: [0xd0000000-0xdfffffff]
[    0.190186] pci 0000:02:07.0: reg 10 io port: [0xde00-0xdeff]
[    0.190200] pci 0000:02:07.0: reg 14 32bit mmio: [0xfddff000-0xfddff0ff]
[    0.190287] pci 0000:02:07.0: supports D1 D2
[    0.190290] pci 0000:02:07.0: PME# supported from D1 D2 D3hot D3cold
[    0.190297] pci 0000:02:07.0: PME# disabled
[    0.190370] pci 0000:00:14.4: transparent bridge
[    0.190382] pci 0000:00:14.4: bridge io port: [0xd000-0xdfff]
[    0.190389] pci 0000:00:14.4: bridge 32bit mmio: [0xfdd00000-0xfddfffff]
[    0.190397] pci 0000:00:14.4: bridge 32bit mmio pref: [0xfdc00000-0xfdcfffff]
[    0.190414] pci_bus 0000:00: on NUMA node 0
[    0.190421] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.190716] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P2P_._PRT]
[    0.190895] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.AGP_._PRT]
[    0.212488] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 10 11) *0, disabled.
[    0.212633] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 10 11) *0, disabled.
[    0.212775] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 10 11) *0, disabled.
[    0.212916] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 10 11) *0, disabled.
[    0.213057] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 10 11) *0, disabled.
[    0.213198] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 *10 11)
[    0.213337] ACPI: PCI Interrupt Link [LNK0] (IRQs 3 4 *5 6 7 10 11)
[    0.213477] ACPI: PCI Interrupt Link [LNK1] (IRQs 3 4 5 6 7 10 *11)
[    0.213748] SCSI subsystem initialized
[    0.213795] libata version 3.00 loaded.
[    0.213795] usbcore: registered new interface driver usbfs
[    0.213795] usbcore: registered new interface driver hub
[    0.213795] usbcore: registered new device driver usb
[    0.213795] ACPI: WMI: Mapper loaded
[    0.213795] PCI: Using ACPI for IRQ routing
[    0.213795] pci 0000:00:00.0: BAR 3: address space collision on of device [0xe0000000-0xffffffff]
[    0.213795] pci 0000:00:00.0: BAR 3: can't allocate resource
[    0.213795] pci 0000:00:01.0: BAR 0: address space collision on of device [0xf4000000-0xf7ffffff]
[    0.213795] pci 0000:00:01.0: BAR 0: can't allocate resource
[    0.224013] Bluetooth: Core ver 2.15
[    0.224036] NET: Registered protocol family 31
[    0.224036] Bluetooth: HCI device and connection manager initialized
[    0.224036] Bluetooth: HCI socket layer initialized
[    0.224036] NetLabel: Initializing
[    0.224036] NetLabel:  domain hash size = 128
[    0.224036] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.224055] NetLabel:  unlabeled traffic allowed by default
[    0.236018] pnp: PnP ACPI init
[    0.236047] ACPI: bus type pnp registered
[    0.240505] pnp 00:0d: mem resource (0xf0000-0xf3fff) overlaps 0000:00:00.0 BAR 3 (0x0-0x1fffffff), disabling
[    0.240510] pnp 00:0d: mem resource (0xf4000-0xf7fff) overlaps 0000:00:00.0 BAR 3 (0x0-0x1fffffff), disabling
[    0.240515] pnp 00:0d: mem resource (0xf8000-0xfbfff) overlaps 0000:00:00.0 BAR 3 (0x0-0x1fffffff), disabling
[    0.240520] pnp 00:0d: mem resource (0xfc000-0xfffff) overlaps 0000:00:00.0 BAR 3 (0x0-0x1fffffff), disabling
[    0.240524] pnp 00:0d: mem resource (0x0-0x9ffff) overlaps 0000:00:00.0 BAR 3 (0x0-0x1fffffff), disabling
[    0.240529] pnp 00:0d: mem resource (0x100000-0x4feeffff) overlaps 0000:00:00.0 BAR 3 (0x0-0x1fffffff), disabling
[    0.240535] pnp 00:0d: mem resource (0xf0000-0xf3fff) overlaps 0000:00:01.0 BAR 0 (0x0-0x3ffffff), disabling
[    0.240540] pnp 00:0d: mem resource (0xf4000-0xf7fff) overlaps 0000:00:01.0 BAR 0 (0x0-0x3ffffff), disabling
[    0.240544] pnp 00:0d: mem resource (0xf8000-0xfbfff) overlaps 0000:00:01.0 BAR 0 (0x0-0x3ffffff), disabling
[    0.240549] pnp 00:0d: mem resource (0xfc000-0xfffff) overlaps 0000:00:01.0 BAR 0 (0x0-0x3ffffff), disabling
[    0.240553] pnp 00:0d: mem resource (0x0-0x9ffff) overlaps 0000:00:01.0 BAR 0 (0x0-0x3ffffff), disabling
[    0.240558] pnp 00:0d: mem resource (0x100000-0x4feeffff) overlaps 0000:00:01.0 BAR 0 (0x0-0x3ffffff), disabling
[    0.240584] pnp 00:0d: mem resource (0xf0000-0xf3fff) overlaps 0000:01:05.1 BAR 0 (0x0-0xfffffff), disabling
[    0.240589] pnp 00:0d: mem resource (0xf4000-0xf7fff) overlaps 0000:01:05.1 BAR 0 (0x0-0xfffffff), disabling
[    0.240594] pnp 00:0d: mem resource (0xf8000-0xfbfff) overlaps 0000:01:05.1 BAR 0 (0x0-0xfffffff), disabling
[    0.240598] pnp 00:0d: mem resource (0xfc000-0xfffff) overlaps 0000:01:05.1 BAR 0 (0x0-0xfffffff), disabling
[    0.240603] pnp 00:0d: mem resource (0x0-0x9ffff) overlaps 0000:01:05.1 BAR 0 (0x0-0xfffffff), disabling
[    0.240607] pnp 00:0d: mem resource (0x100000-0x4feeffff) overlaps 0000:01:05.1 BAR 0 (0x0-0xfffffff), disabling
[    0.240665] pnp: PnP ACPI: found 14 devices
[    0.240669] ACPI: ACPI bus type pnp unregistered
[    0.240675] PnPBIOS: Disabled by ACPI PNP
[    0.240690] system 00:01: ioport range 0x140-0x15f has been reserved
[    0.240695] system 00:01: ioport range 0x228-0x22f has been reserved
[    0.240699] system 00:01: ioport range 0x4d6-0x4d6 has been reserved
[    0.240703] system 00:01: ioport range 0xc00-0xc01 has been reserved
[    0.240707] system 00:01: ioport range 0xc14-0xc14 has been reserved
[    0.240710] system 00:01: ioport range 0xc50-0xc52 has been reserved
[    0.240714] system 00:01: ioport range 0xc6c-0xc6d has been reserved
[    0.240718] system 00:01: ioport range 0xc6f-0xc6f has been reserved
[    0.240722] system 00:01: ioport range 0xcd4-0xcdf has been reserved
[    0.240726] system 00:01: ioport range 0x4000-0x40fe has been reserved
[    0.240729] system 00:01: ioport range 0x4210-0x4217 has been reserved
[    0.240741] system 00:06: ioport range 0x4d0-0x4d1 has been reserved
[    0.240745] system 00:06: ioport range 0x220-0x225 has been reserved
[    0.240748] system 00:06: ioport range 0x40b-0x41a has been reserved
[    0.240752] system 00:06: ioport range 0x880-0x88f has been reserved
[    0.240764] system 00:0c: iomem range 0xe0000000-0xefffffff has been reserved
[    0.240774] system 00:0d: iomem range 0x4ff00000-0x4fffffff could not be reserved
[    0.240778] system 00:0d: iomem range 0x4fef0000-0x4fefffff could not be reserved
[    0.240782] system 00:0d: iomem range 0xffff0000-0xffffffff has been reserved
[    0.240787] system 00:0d: iomem range 0xfec00000-0xfec00fff could not be reserved
[    0.240791] system 00:0d: iomem range 0xfee00000-0xfee00fff has been reserved
[    0.240795] system 00:0d: iomem range 0xfff80000-0xfffeffff has been reserved
[    0.275552] AppArmor: AppArmor Filesystem Enabled
[    0.275597] pci 0000:01:05.1: BAR 0: can't allocate mem resource [0xe0000000-0xdfffffff]
[    0.275605] pci 0000:00:01.0: PCI bridge, secondary bus 0000:01
[    0.275609] pci 0000:00:01.0:   IO window: 0xe000-0xefff
[    0.275615] pci 0000:00:01.0:   MEM window: 0xfde00000-0xfdefffff
[    0.275620] pci 0000:00:01.0:   PREFETCH window: 0xd0000000-0xdfffffff
[    0.275626] pci 0000:00:14.4: PCI bridge, secondary bus 0000:02
[    0.275631] pci 0000:00:14.4:   IO window: 0xd000-0xdfff
[    0.275639] pci 0000:00:14.4:   MEM window: 0xfdd00000-0xfddfffff
[    0.275646] pci 0000:00:14.4:   PREFETCH window: 0xfdc00000-0xfdcfffff
[    0.275671] pci_bus 0000:00: resource 0 io:  [0x00-0xffff]
[    0.275675] pci_bus 0000:00: resource 1 mem: [0x000000-0xffffffff]
[    0.275679] pci_bus 0000:01: resource 0 io:  [0xe000-0xefff]
[    0.275682] pci_bus 0000:01: resource 1 mem: [0xfde00000-0xfdefffff]
[    0.275686] pci_bus 0000:01: resource 2 pref mem [0xd0000000-0xdfffffff]
[    0.275689] pci_bus 0000:02: resource 0 io:  [0xd000-0xdfff]
[    0.275693] pci_bus 0000:02: resource 1 mem: [0xfdd00000-0xfddfffff]
[    0.275696] pci_bus 0000:02: resource 2 pref mem [0xfdc00000-0xfdcfffff]
[    0.275700] pci_bus 0000:02: resource 3 io:  [0x00-0xffff]
[    0.275703] pci_bus 0000:02: resource 4 mem: [0x000000-0xffffffff]
[    0.275762] NET: Registered protocol family 2
[    0.275914] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.276449] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.277226] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.277887] TCP: Hash tables configured (established 131072 bind 65536)
[    0.277892] TCP reno registered
[    0.278091] NET: Registered protocol family 1
[    0.278203] Trying to unpack rootfs image as initramfs...
[    0.536843] Freeing initrd memory: 7479k freed
[    0.545771] cpufreq-nforce2: No nForce2 chipset.
[    0.545818] Scanning for low memory corruption every 60 seconds
[    0.545972] audit: initializing netlink socket (disabled)
[    0.546000] type=2000 audit(1256955889.543:1): initialized
[    0.555740] highmem bounce pool size: 64 pages
[    0.555750] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    0.557762] VFS: Disk quotas dquot_6.5.2
[    0.557847] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.558647] fuse init (API version 7.12)
[    0.558772] msgmni has been set to 1725
[    0.559121] alg: No test for stdrng (krng)
[    0.559156] io scheduler noop registered
[    0.559159] io scheduler anticipatory registered
[    0.559162] io scheduler deadline registered
[    0.559224] io scheduler cfq registered (default)
[    0.559237] pci 0000:00:00.0: MSI quirk detected; MSI disabled
[    0.789078] Switched to high resolution mode on CPU 1
[    0.791993] Switched to high resolution mode on CPU 0
[    2.200011] pci 0000:00:13.2: EHCI: BIOS handoff failed (BIOS bug?) 01010001
[    2.200036] pci 0000:01:05.0: Boot video device
[    2.200164] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    2.200206] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    2.200396] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input0
[    2.200401] ACPI: Power Button [PWRF]
[    2.200482] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1
[    2.200486] ACPI: Power Button [PWRB]
[    2.200570] fan PNP0C0B:00: registered as cooling_device0
[    2.200578] ACPI: Fan [FAN] (on)
[    2.200959] processor LNXCPU:00: registered as cooling_device1
[    2.201024] processor LNXCPU:01: registered as cooling_device2
[    2.204269] thermal LNXTHERM:01: registered as thermal_zone0
[    2.204282] ACPI: Thermal Zone [THRM] (42 C)
[    2.204360] isapnp: Scanning for PnP cards...
[    2.558930] isapnp: No Plug & Play device found
[    2.560543] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    2.560699] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    2.560844] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[    2.561280] 00:07: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    2.561477] 00:08: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[    2.562978] brd: module loaded
[    2.563623] loop: module loaded
[    2.563721] input: Macintosh mouse button emulation as /devices/virtual/input/input2
[    2.563921] sata_sil 0000:00:11.0: version 2.4
[    2.563974]   alloc irq_desc for 23 on node -1
[    2.563977]   alloc kstat_irqs on node -1
[    2.563987] sata_sil 0000:00:11.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    2.564132] scsi0 : sata_sil
[    2.564265] scsi1 : sata_sil
[    2.564466] ata1: SATA max UDMA/100 mmio m512@0xfdffe000 tf 0xfdffe080 irq 23
[    2.564472] ata2: SATA max UDMA/100 mmio m512@0xfdffe000 tf 0xfdffe0c0 irq 23
[    2.564559]   alloc irq_desc for 21 on node -1
[    2.564563]   alloc kstat_irqs on node -1
[    2.564569] sata_sil 0000:00:12.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[    2.564659] scsi2 : sata_sil
[    2.564747] scsi3 : sata_sil
[    2.564925] ata3: SATA max UDMA/100 mmio m512@0xfdffd000 tf 0xfdffd080 irq 21
[    2.564931] ata4: SATA max UDMA/100 mmio m512@0xfdffd000 tf 0xfdffd0c0 irq 21
[    2.565199]   alloc irq_desc for 16 on node -1
[    2.565203]   alloc kstat_irqs on node -1
[    2.565210] pata_atiixp 0000:00:14.1: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    2.565358] scsi4 : pata_atiixp
[    2.565475] scsi5 : pata_atiixp
[    2.567029] ata5: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xf400 irq 14
[    2.567034] ata6: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xf408 irq 15
[    2.568056] Fixed MDIO Bus: probed
[    2.568109] PPP generic driver version 2.4.2
[    2.568253] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    2.568281]   alloc irq_desc for 19 on node -1
[    2.568285]   alloc kstat_irqs on node -1
[    2.568292] ehci_hcd 0000:00:13.2: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    2.568308] ehci_hcd 0000:00:13.2: EHCI Host Controller
[    2.568385] ehci_hcd 0000:00:13.2: new USB bus registered, assigned bus number 1
[    2.568470] ehci_hcd 0000:00:13.2: irq 19, io mem 0xfdffa000
[    2.580011] ehci_hcd 0000:00:13.2: USB 2.0 started, EHCI 1.00
[    2.580137] usb usb1: configuration #1 chosen from 1 choice
[    2.580181] hub 1-0:1.0: USB hub found
[    2.580193] hub 1-0:1.0: 8 ports detected
[    2.580300] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    2.580324] ohci_hcd 0000:00:13.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    2.580338] ohci_hcd 0000:00:13.0: OHCI Host Controller
[    2.580385] ohci_hcd 0000:00:13.0: new USB bus registered, assigned bus number 2
[    2.580406] ohci_hcd 0000:00:13.0: irq 19, io mem 0xfdffc000
[    2.640082] usb usb2: configuration #1 chosen from 1 choice
[    2.640121] hub 2-0:1.0: USB hub found
[    2.640136] hub 2-0:1.0: 4 ports detected
[    2.640214] ohci_hcd 0000:00:13.1: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    2.640228] ohci_hcd 0000:00:13.1: OHCI Host Controller
[    2.640278] ohci_hcd 0000:00:13.1: new USB bus registered, assigned bus number 3
[    2.640299] ohci_hcd 0000:00:13.1: irq 19, io mem 0xfdffb000
[    2.700080] usb usb3: configuration #1 chosen from 1 choice
[    2.700118] hub 3-0:1.0: USB hub found
[    2.700133] hub 3-0:1.0: 4 ports detected
[    2.700225] uhci_hcd: USB Universal Host Controller Interface driver
[    2.700353] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    2.700721] serio: i8042 KBD port at 0x60,0x64 irq 1
[    2.700732] serio: i8042 AUX port at 0x60,0x64 irq 12
[    2.700845] mice: PS/2 mouse device common for all mice
[    2.700984] rtc_cmos 00:03: RTC can wake from S4
[    2.701035] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0
[    2.701067] rtc0: alarms up to one month, 242 bytes nvram
[    2.701209] device-mapper: uevent: version 1.0.3
[    2.701334] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: dm-devel@redhat.com
[    2.701460] device-mapper: multipath: version 1.1.0 loaded
[    2.701465] device-mapper: multipath round-robin: version 1.0.0 loaded
[    2.701630] EISA: Probing bus 0 at eisa.0
[    2.701655] Cannot allocate resource for EISA slot 4
[    2.701678] EISA: Detected 0 cards.
[    2.701835] cpuidle: using governor ladder
[    2.701839] cpuidle: using governor menu
[    2.702604] TCP cubic registered
[    2.702782] NET: Registered protocol family 10
[    2.703498] lo: Disabled Privacy Extensions
[    2.704022] NET: Registered protocol family 17
[    2.704048] Bluetooth: L2CAP ver 2.13
[    2.704051] Bluetooth: L2CAP socket layer initialized
[    2.704055] Bluetooth: SCO (Voice Link) ver 0.6
[    2.704057] Bluetooth: SCO socket layer initialized
[    2.704107] Bluetooth: RFCOMM TTY layer initialized
[    2.704112] Bluetooth: RFCOMM socket layer initialized
[    2.704114] Bluetooth: RFCOMM ver 1.11
[    2.704169] Using IPI No-Shortcut mode
[    2.704278] PM: Resume from disk failed.
[    2.704304] registered taskstats version 1
[    2.704454]   Magic number: 13:936:410
[    2.704487] misc ecryptfs: hash matches
[    2.704552] rtc_cmos 00:03: setting system clock to 2009-10-31 02:24:51 UTC (1256955891)
[    2.704557] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    2.704560] EDD information not available.
[    2.718423] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3
[    2.732753] ata5.00: ATA-6: WDC WD800JB-00JJC0, 05.01C05, max UDMA/100
[    2.732758] ata5.00: 156301488 sectors, multi 16: LBA 
[    2.732798] ata5.00: limited to UDMA/33 due to 40-wire cable
[    2.740722] ata5.00: configured for UDMA/33
[    2.884033] ata1: SATA link down (SStatus 0 SControl 310)
[    2.884140] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
[    2.892020] usb 1-6: new high speed USB device using ehci_hcd and address 2
[    2.892617] ata3.00: ATA-8: WDC WD10EADS-00M2B0, 01.00A01, max UDMA/133
[    2.892622] ata3.00: 1953525168 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    2.900658] ata3.00: configured for UDMA/100
[    3.026615] usb 1-6: configuration #1 chosen from 1 choice
[    3.204029] ata2: SATA link down (SStatus 0 SControl 310)
[    3.204213] scsi 2:0:0:0: Direct-Access     ATA      WDC WD10EADS-00M 01.0 PQ: 0 ANSI: 5
[    3.204429] sd 2:0:0:0: Attached scsi generic sg0 type 0
[    3.204542] sd 2:0:0:0: [sda] 1953525168 512-byte logical blocks: (1.00 TB/931 GiB)
[    3.204614] sd 2:0:0:0: [sda] Write Protect is off
[    3.204619] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    3.204655] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    3.204852]  sda: sda1 sda2 < sda5 sda6 sda7 sda8 >
[    3.266318] sd 2:0:0:0: [sda] Attached SCSI disk
[    3.524030] ata4: SATA link down (SStatus 0 SControl 310)
[    3.524164] scsi 4:0:0:0: Direct-Access     ATA      WDC WD800JB-00JJ 05.0 PQ: 0 ANSI: 5
[    3.524332] sd 4:0:0:0: [sdb] 156301488 512-byte logical blocks: (80.0 GB/74.5 GiB)
[    3.524345] sd 4:0:0:0: Attached scsi generic sg1 type 0
[    3.524570] sd 4:0:0:0: [sdb] Write Protect is off
[    3.524575] sd 4:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[    3.524610] sd 4:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    3.524797]  sdb: sdb1 sdb2 < sdb5 sdb6 sdb7 sdb8 >
[    3.594460] sd 4:0:0:0: [sdb] Attached SCSI disk
[    3.704581] ata6.00: ATAPI: ATAPI   DVD A  DH20A4P, 9P59, max UDMA/66
[    3.704617] ata6.00: limited to UDMA/33 due to 40-wire cable
[    3.736548] ata6.00: configured for UDMA/33
[    3.738343] scsi 5:0:0:0: CD-ROM            ATAPI    DVD A  DH20A4P   9P59 PQ: 0 ANSI: 5
[    3.743576] sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
[    3.743581] Uniform CD-ROM driver Revision: 3.20
[    3.743684] sr 5:0:0:0: Attached scsi CD-ROM sr0
[    3.743761] sr 5:0:0:0: Attached scsi generic sg2 type 5
[    3.743797] Freeing unused kernel memory: 540k freed
[    3.744428] Write protecting the kernel text: 4568k
[    3.744490] Write protecting the kernel read-only data: 1836k
[    3.910364] Linux agpgart interface v0.103
[    3.912743] agpgart-ati 0000:00:00.0: unsupported Ati chipset [1002/5a33])
[    4.041711] [drm] Initialized drm 1.1.0 20060810
[    4.078618] [drm] radeon default to kernel modesetting DISABLED.
[    4.079000]   alloc irq_desc for 17 on node -1
[    4.079004]   alloc kstat_irqs on node -1
[    4.079016] pci 0000:01:05.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    4.079211] [drm] Initialized radeon 1.31.0 20080528 for 0000:01:05.0 on minor 0
[    4.085960] <6>8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)
[    4.086007] 8139cp 0000:02:07.0: This (id 10ec:8139 rev 10) is not an 8139C+ compatible chip, use 8139too
[    4.090134] 8139too Fast Ethernet driver 0.9.28
[    4.090209]   alloc irq_desc for 22 on node -1
[    4.090213]   alloc kstat_irqs on node -1
[    4.090225] 8139too 0000:02:07.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[    4.092242] eth0: RealTek RTL8139 at 0xde00, 00:15:58:21:34:e7, IRQ 22
[    4.098536] Initializing USB Mass Storage driver...
[    4.098762] scsi6 : SCSI emulation for USB Mass Storage devices
[    4.098934] usbcore: registered new interface driver usb-storage
[    4.098940] USB Mass Storage support registered.
[    4.099271] usb-storage: device found at 2
[    4.099274] usb-storage: waiting for device to settle before scanning
[    5.611540] PM: Starting manual resume from disk
[    5.611546] PM: Resume from partition 8:24
[    5.611549] PM: Checking hibernation image.
[    5.611873] PM: Resume from disk failed.
[    5.630903] EXT4-fs (sdb7): barriers enabled
[    5.647179] kjournald2 starting: pid 378, dev sdb7:8, commit interval 5 seconds
[    5.647194] EXT4-fs (sdb7): delayed allocation enabled
[    5.647200] EXT4-fs: file extents enabled
[    5.648971] EXT4-fs: mballoc enabled
[    5.648992] EXT4-fs (sdb7): mounted filesystem with ordered data mode
[    6.251891] type=1505 audit(1256955895.044:2): operation="profile_load" pid=401 name=/sbin/dhclient3
[    6.252694] type=1505 audit(1256955895.047:3): operation="profile_load" pid=401 name=/usr/lib/NetworkManager/nm-dhcp-client.action
[    6.253128] type=1505 audit(1256955895.047:4): operation="profile_load" pid=401 name=/usr/lib/connman/scripts/dhclient-script
[    6.264503] type=1505 audit(1256955895.059:5): operation="profile_load" pid=402 name=/usr/lib/cups/backend/cups-pdf
[    6.265419] type=1505 audit(1256955895.059:6): operation="profile_load" pid=402 name=/usr/sbin/cupsd
[    6.275499] type=1505 audit(1256955895.067:7): operation="profile_load" pid=403 name=/usr/sbin/mysqld-akonadi
[    6.278843] type=1505 audit(1256955895.071:8): operation="profile_load" pid=404 name=/usr/sbin/tcpdump
[    6.900881] Adding 2931820k swap on /dev/sdb8.  Priority:-1 extents:1 across:2931820k 
[    7.132161] udev: starting version 147
[    8.049582] piix4_smbus 0000:00:14.0: SMBus Host Controller at 0x500, revision 0
[    8.215947] psmouse serio1: ID: 10 00 64
[    8.288851] lp: driver loaded but no devices found
[    8.293283] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[    8.525003] parport_pc 00:09: reported by Plug and Play ACPI
[    8.525078] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
[    8.600861] ppdev: user-space parallel port driver
[    8.620307] lp0: using parport0 (interrupt-driven).
[    8.736342] input: ImPS/2 Generic Wheel Mouse as /devices/platform/i8042/serio1/input/input4
[    9.096224] usb-storage: device scan complete
[    9.096944] scsi 6:0:0:0: Direct-Access     JetFlash TS2GJFV30        8.07 PQ: 0 ANSI: 2
[    9.097688] sd 6:0:0:0: Attached scsi generic sg3 type 0
[    9.100672] sd 6:0:0:0: [sdc] 3969022 512-byte logical blocks: (2.03 GB/1.89 GiB)
[    9.101156] sd 6:0:0:0: [sdc] Write Protect is off
[    9.101161] sd 6:0:0:0: [sdc] Mode Sense: 03 00 00 00
[    9.101164] sd 6:0:0:0: [sdc] Assuming drive cache: write through
[    9.104580] sd 6:0:0:0: [sdc] Assuming drive cache: write through
[    9.104594]  sdc: sdc1
[    9.247677] sd 6:0:0:0: [sdc] Assuming drive cache: write through
[    9.247689] sd 6:0:0:0: [sdc] Attached SCSI removable disk
[    9.455483] ip_tables: (C) 2000-2006 Netfilter Core Team
[    9.468567] EXT4-fs (sdb7): internal journal on sdb7:8
[   10.129879] ATI IXP AC97 controller 0000:00:14.5: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[   42.816029] ata5: lost interrupt (Status 0x58)
[   42.820004] ata5: drained 6144 bytes to clear DRQ.
[   42.838422] ata5.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6 frozen
[   42.838482] ata5.00: cmd c8/00:18:10:64:6b/00:00:00:00:00/e7 tag 0 dma 12288 in
[   42.838483]          res 40/00:00:00:4f:c2/00:00:00:00:00/00 Emask 0x4 (timeout)
[   42.838573] ata5.00: status: { DRDY }
[   47.876013] ata5: link is slow to respond, please be patient (ready=0)
[   52.860017] ata5: device not ready (errno=-16), forcing hardreset
[   52.860029] ata5: soft resetting link
[   53.032692] ata5.00: configured for UDMA/33
[   53.032699] ata5.00: device reported invalid CHS sector 0
[   53.032715] ata5: EH complete
[   53.353346] type=1505 audit(1256936142.147:9): operation="profile_replace" pid=951 name=/sbin/dhclient3
[   53.354143] type=1505 audit(1256936142.147:10): operation="profile_replace" pid=951 name=/usr/lib/NetworkManager/nm-dhcp-client.action
[   53.354579] type=1505 audit(1256936142.147:11): operation="profile_replace" pid=951 name=/usr/lib/connman/scripts/dhclient-script
[   53.357863] type=1505 audit(1256936142.151:12): operation="profile_replace" pid=953 name=/usr/lib/cups/backend/cups-pdf
[   53.358785] type=1505 audit(1256936142.151:13): operation="profile_replace" pid=953 name=/usr/sbin/cupsd
[   53.362252] type=1505 audit(1256936142.155:14): operation="profile_replace" pid=955 name=/usr/sbin/mysqld-akonadi
[   53.364977] type=1505 audit(1256936142.159:15): operation="profile_replace" pid=956 name=/usr/sbin/tcpdump
[   53.952249] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[   57.362478] [drm] Setting GART location based on new memory map
[   57.363162] [drm] Loading R300 Microcode
[   57.363197] [drm] Num pipes: 4
[   57.363205] [drm] writeback test succeeded in 1 usecs
[   58.588679] CPU0 attaching NULL sched-domain.
[   58.588688] CPU1 attaching NULL sched-domain.
[   58.604077] CPU0 attaching sched-domain:
[   58.604084]  domain 0: span 0-1 level MC
[   58.604088]   groups: 0 1
[   58.604095]   domain 1: span 0-1 level CPU
[   58.604099]    groups: 0-1 (__cpu_power = 2048)
[   58.604107] CPU1 attaching sched-domain:
[   58.604110]  domain 0: span 0-1 level MC
[   58.604114]   groups: 1 0
[   58.604119]   domain 1: span 0-1 level CPU
[   58.604123]    groups: 0-1 (__cpu_power = 2048)
[   71.673916] CPU0 attaching NULL sched-domain.
[   71.673926] CPU1 attaching NULL sched-domain.
[   71.692585] CPU0 attaching sched-domain:
[   71.692591]  domain 0: span 0-1 level CPU
[   71.692595]   groups: 0 1
[   71.692604] CPU1 attaching sched-domain:
[   71.692607]  domain 0: span 0-1 level CPU
[   71.692611]   groups: 1 0

```

---

