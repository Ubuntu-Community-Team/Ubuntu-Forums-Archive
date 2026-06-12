---
title: "1201ha: Wireless causes lock-ups"
date: 2010-01-03
forum: Hardware
---

### Post by linewire on 2010-01-03
I have a 1201ha which is essentially the 1101ha netbook.  But it seems whenever wireless is active and I download something or click on a link, then I'd say 1/15 times the whole screen goes crazy and flips out and I am forced to do a hard restart. 
Are there some set of alternate drivers I might be able to use?  It has done this with 9.04,9.10 & 9.10 UNR...currently using 9.10

---

### Post by rantingkitten on 2010-01-03
Do you know what kind of wireless chip you have?  You can run the command 'lspci' to find out -- that'll list all your hardware, and your wireless will be somewhere in there.  For example mine says:

10:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)

Also, when this happens, it's a good idea to check system messages to find out what went wrong.  The command 'dmesg' can be helpful, as well as 'cat /var/log/syslog' or 'tail /var/log/syslog'.  Look for information in either of those that pertain to the wireless during or after the crash.  With that information maybe we can find out what's going on.

---

### Post by linewire on 2010-01-19
Delayed reply! but issue is still a problem. "lspci" shows:
```
00:00.0 Host bridge: Intel Corporation System Controller Hub (SCH Poulsbo) (rev 07)
00:02.0 VGA compatible controller: Intel Corporation System Controller Hub (SCH Poulsbo) Graphics Controller (rev 07)
00:1b.0 Audio device: Intel Corporation System Controller Hub (SCH Poulsbo) HD Audio Controller (rev 07)
00:1c.0 PCI bridge: Intel Corporation System Controller Hub (SCH Poulsbo) PCI Express Port 1 (rev 07)
00:1c.1 PCI bridge: Intel Corporation System Controller Hub (SCH Poulsbo) PCI Express Port 2 (rev 07)
00:1d.0 USB Controller: Intel Corporation System Controller Hub (SCH Poulsbo) USB UHCI #1 (rev 07)
00:1d.1 USB Controller: Intel Corporation System Controller Hub (SCH Poulsbo) USB UHCI #2 (rev 07)
00:1d.2 USB Controller: Intel Corporation System Controller Hub (SCH Poulsbo) USB UHCI #3 (rev 07)
00:1d.7 USB Controller: Intel Corporation System Controller Hub (SCH Poulsbo) USB EHCI #1 (rev 07)
00:1f.0 ISA bridge: Intel Corporation System Controller Hub (SCH Poulsbo) LPC Bridge (rev 07)
00:1f.1 IDE interface: Intel Corporation System Controller Hub (SCH Poulsbo) IDE Controller (rev 07)
01:00.0 Network controller: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) (rev 01)
03:00.0 Ethernet controller: Attansic Technology Corp. Atheros AR8132 / L1c Gigabit Ethernet Adapter (rev c0)
```and dmesg shows:
[HTML][    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.31-18-generic (buildd@rothera) (gcc version 4.4.1 (Ubuntu 4.4.1-4ubuntu8) ) #55-Ubuntu SMP Fri Jan 8 14:55:26 UTC 2010 (Ubuntu 2.6.31-18.55-generic)
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
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e2000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000003f650000 (usable)
[    0.000000]  BIOS-e820: 000000003f650000 - 000000003f660000 (reserved)
[    0.000000]  BIOS-e820: 000000003f660000 - 000000003f66e000 (ACPI data)
[    0.000000]  BIOS-e820: 000000003f66e000 - 000000003f6b0000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000003f6b0000 - 000000003f6c0000 (reserved)
[    0.000000]  BIOS-e820: 000000003f6c8000 - 000000003f800000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fff00000 - 0000000100000000 (reserved)
[    0.000000] DMI 2.5 present.
[    0.000000] AMI BIOS detected: BIOS may corrupt low RAM, working around it.
[    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
[    0.000000] last_pfn = 0x3f650 max_arch_pfn = 0x100000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-DFFFF uncachable
[    0.000000]   E0000-EFFFF write-through
[    0.000000]   F0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000 mask 0C0000000 write-back
[    0.000000]   1 base 03F700000 mask 0FFF00000 uncachable
[    0.000000]   2 base 03F800000 mask 0FF800000 uncachable
[    0.000000]   3 disabled
[    0.000000]   4 disabled
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] Scanning 0 areas for low memory corruption
[    0.000000] modified physical RAM map:
[    0.000000]  modified: 0000000000000000 - 0000000000010000 (reserved)
[    0.000000]  modified: 0000000000010000 - 000000000009fc00 (usable)
[    0.000000]  modified: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  modified: 00000000000e2000 - 0000000000100000 (reserved)
[    0.000000]  modified: 0000000000100000 - 000000003f650000 (usable)
[    0.000000]  modified: 000000003f650000 - 000000003f660000 (reserved)
[    0.000000]  modified: 000000003f660000 - 000000003f66e000 (ACPI data)
[    0.000000]  modified: 000000003f66e000 - 000000003f6b0000 (ACPI NVS)
[    0.000000]  modified: 000000003f6b0000 - 000000003f6c0000 (reserved)
[    0.000000]  modified: 000000003f6c8000 - 000000003f800000 (reserved)
[    0.000000]  modified: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  modified: 00000000fff00000 - 0000000100000000 (reserved)
[    0.000000] initial memory mapped : 0 - 00c00000
[    0.000000] init_memory_mapping: 0000000000000000-00000000377fe000
[    0.000000] Using x86 segment limits to approximate NX protection
[    0.000000]  0000000000 - 0000400000 page 4k
[    0.000000]  0000400000 - 0037400000 page 2M
[    0.000000]  0037400000 - 00377fe000 page 4k
[    0.000000] kernel direct mapping tables up to 377fe000 @ 10000-15000
[    0.000000] RAMDISK: 2f1af000 - 2f8fb39b
[    0.000000] ACPI: RSDP 000fbfd0 00024 (v02 ACPIAM)
[    0.000000] ACPI: XSDT 3f660100 0005C (v01 110409 XSDT1605 20091104 MSFT 00000097)
[    0.000000] ACPI: FACP 3f660290 000F4 (v04 110409 FACP1605 20091104 MSFT 00000097)
[    0.000000] ACPI: DSDT 3f660430 095E0 (v02  A1451 A1451000 00000000 INTL 20060113)
[    0.000000] ACPI: FACS 3f66e000 00040
[    0.000000] ACPI: APIC 3f660390 0005C (v02 110409 APIC1605 20091104 MSFT 00000097)
[    0.000000] ACPI: MCFG 3f6603f0 0003C (v01 110409 OEMMCFG  20091104 MSFT 00000097)
[    0.000000] ACPI: OEMB 3f66e040 0012C (v01 110409 OEMB1605 20091104 MSFT 00000097)
[    0.000000] ACPI: HPET 3f669a10 00038 (v01 110409 OEMHPET  20091104 MSFT 00000097)
[    0.000000] ACPI: GSCI 3f66e170 02024 (v01 110409 GMCHSCI  20091104 MSFT 00000097)
[    0.000000] ACPI: SSDT 3f670b60 004F0 (v01  PmRef    CpuPm 00003000 INTL 20060113)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] 126MB HIGHMEM available.
[    0.000000] 887MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 377fe000
[    0.000000]   low ram: 0 - 377fe000
[    0.000000]   node 0 low ram: 00000000 - 377fe000
[    0.000000]   node 0 bootmap 00011000 - 00017f00
[    0.000000] (9 early reservations) ==> bootmem [0000000000 - 00377fe000]
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000]   #1 [0000001000 - 0000002000]    EX TRAMPOLINE ==> [0000001000 - 0000002000]
[    0.000000]   #2 [0000006000 - 0000007000]       TRAMPOLINE ==> [0000006000 - 0000007000]
[    0.000000]   #3 [0000100000 - 00008ad060]    TEXT DATA BSS ==> [0000100000 - 00008ad060]
[    0.000000]   #4 [002f1af000 - 002f8fb39b]          RAMDISK ==> [002f1af000 - 002f8fb39b]
[    0.000000]   #5 [000009fc00 - 0000100000]    BIOS reserved ==> [000009fc00 - 0000100000]
[    0.000000]   #6 [00008ae000 - 00008b11a8]              BRK ==> [00008ae000 - 00008b11a8]
[    0.000000]   #7 [0000010000 - 0000011000]          PGTABLE ==> [0000010000 - 0000011000]
[    0.000000]   #8 [0000011000 - 0000018000]          BOOTMAP ==> [0000011000 - 0000018000]
[    0.000000] found SMP MP-table at [c00ff780] ff780
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x000377fe
[    0.000000]   HighMem  0x000377fe -> 0x0003f650
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[2] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x0000009f
[    0.000000]     0: 0x00000100 -> 0x0003f650
[    0.000000] On node 0 totalpages: 259551
[    0.000000] free_area_init_node: node 0, pgdat c0788920, node_mem_map c1000200
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3951 pages, LIFO batch:0
[    0.000000]   Normal zone: 1744 pages used for memmap
[    0.000000]   Normal zone: 221486 pages, LIFO batch:31
[    0.000000]   HighMem zone: 253 pages used for memmap
[    0.000000]   HighMem zone: 32085 pages, LIFO batch:7
[    0.000000] Using APIC driver default
[    0.000000] ACPI: PM-Timer IO Port: 0x908
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
[    0.000000] SMP: Allowing 2 CPUs, 0 hotplug CPUs
[    0.000000] nr_irqs_gsi: 24
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e2000
[    0.000000] PM: Registered nosave memory: 00000000000e2000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 3f800000 (gap: 3f800000:bf600000)
[    0.000000] NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:2 nr_node_ids:1
[    0.000000] PERCPU: Embedded 14 pages at c17f4000, static data 35612 bytes
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 257522
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.31-18-generic root=UUID=bc7a1ac9-1d9a-43ab-9e87-6e2e1fd241bb ro quiet splash
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] allocated 5192960 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] Initializing HighMem for node 0 (000377fe:0003f650)
[    0.000000] Memory: 1008260k/1038656k available (4578k kernel code, 29496k reserved, 2146k data, 540k init, 129352k highmem)
[    0.000000] virtual kernel memory layout:
[    0.000000]     fixmap  : 0xfff1d000 - 0xfffff000   ( 904 kB)
[    0.000000]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[    0.000000]     vmalloc : 0xf7ffe000 - 0xff7fe000   ( 120 MB)
[    0.000000]     lowmem  : 0xc0000000 - 0xf77fe000   ( 887 MB)
[    0.000000]       .init : 0xc0792000 - 0xc0819000   ( 540 kB)
[    0.000000]       .data : 0xc0578a34 - 0xc0791448   (2146 kB)
[    0.000000]       .text : 0xc0100000 - 0xc0578a34   (4578 kB)
[    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.000000] SLUB: Genslabs=13, HWalign=64, Order=0-3, MinObjects=0, CPUs=2, Nodes=1
[    0.000000] NR_IRQS:2304 nr_irqs:424
[    0.000000] Extended CMOS year: 2000
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 1331.292 MHz processor.
[    0.002110] Console: colour VGA+ 80x25
[    0.002119] console [tty0] enabled
[    0.002413] hpet clockevent registered
[    0.002422] HPET: 3 timers in total, 0 timers will be used for per-cpu timer
[    0.002436] Calibrating delay loop (skipped), value calculated using timer frequency.. 2662.58 BogoMIPS (lpj=5325168)
[    0.002482] Security Framework initialized
[    0.002529] AppArmor: AppArmor initialized
[    0.002546] Mount-cache hash table entries: 512
[    0.002825] Initializing cgroup subsys ns
[    0.002839] Initializing cgroup subsys cpuacct
[    0.002849] Initializing cgroup subsys memory
[    0.002864] Initializing cgroup subsys freezer
[    0.002870] Initializing cgroup subsys net_cls
[    0.002900] CPU: L1 I cache: 32K, L1 D cache: 24K
[    0.002908] CPU: L2 cache: 512K
[    0.002914] CPU: Physical Processor ID: 0
[    0.002919] CPU: Processor Core ID: 0
[    0.002928] mce: CPU supports 5 MCE banks
[    0.002945] CPU0: Thermal monitoring enabled (TM2)
[    0.002954] using mwait in idle threads.
[    0.002969] Performance Counters: Atom events, Intel PMU driver.
[    0.002987] ... version:                 3
[    0.002992] ... bit width:               40
[    0.002998] ... generic counters:        2
[    0.003003] ... value mask:              000000ffffffffff
[    0.003008] ... max period:              000000007fffffff
[    0.003014] ... fixed-purpose counters:  3
[    0.003019] ... counter mask:            0000000700000003
[    0.003030] Checking 'hlt' instruction... OK.
[    0.020016] ACPI: Core revision 20090521
[    0.044476] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.087621] CPU0: Intel(R) Atom(TM) CPU Z520   @ 1.33GHz stepping 02
[    0.088001] Booting processor 1 APIC 0x1 ip 0x6000
[    0.004000] Initializing CPU#1
[    0.004000] Calibrating delay using timer specific routine.. 2662.50 BogoMIPS (lpj=5325016)
[    0.004000] CPU: L1 I cache: 32K, L1 D cache: 24K
[    0.004000] CPU: L2 cache: 512K
[    0.004000] CPU: Physical Processor ID: 0
[    0.004000] CPU: Processor Core ID: 0
[    0.004000] mce: CPU supports 5 MCE banks
[    0.004000] CPU1: Thermal monitoring enabled (TM2)
[    0.004000] x86 PAT enabled: cpu 1, old 0x7040600070406, new 0x7010600070106
[    0.173112] CPU1: Intel(R) Atom(TM) CPU Z520   @ 1.33GHz stepping 02
[    0.173152] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
[    0.176047] Brought up 2 CPUs
[    0.176055] Total of 2 processors activated (5325.09 BogoMIPS).
[    0.176132] CPU0 attaching sched-domain:
[    0.176141]  domain 0: span 0-1 level SIBLING
[    0.176148]   groups: 0 1
[    0.176162] CPU1 attaching sched-domain:
[    0.176167]  domain 0: span 0-1 level SIBLING
[    0.176174]   groups: 1 0
[    0.176416] Booting paravirtualized kernel on bare hardware
[    0.176570] regulator: core version 0.5
[    0.176570] Time: 10:12:42  Date: 01/19/10
[    0.176570] NET: Registered protocol family 16
[    0.176570] EISA bus registered
[    0.176570] ACPI: bus type pci registered
[    0.176691] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 255
[    0.176700] PCI: Not using MMCONFIG.
[    0.176984] PCI: PCI BIOS revision 3.00 entry at 0xf0031, last bus=3
[    0.176990] PCI: Using configuration type 1 for base access
[    0.182183] bio: create slab <bio-0> at 0
[    0.184955] ACPI: EC: Look up EC in DSDT
[    0.204256] ACPI: Interpreter enabled
[    0.204276] ACPI: (supports S0 S1 S3 S4 S5)
[    0.204351] ACPI: Using IOAPIC for interrupt routing
[    0.204486] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 255
[    0.207206] ACPI: BIOS _OSI(Linux) query ignored
[    0.211836] PCI: MCFG area at e0000000 reserved in ACPI motherboard resources
[    0.211844] PCI: Using MMCONFIG for extended config space
[    0.226081] ACPI: EC: GPE = 0xd, I/O: command/status = 0x66, data = 0x62
[    0.226089] ACPI: EC: driver started in poll mode
[    0.226297] ACPI Warning: Incorrect checksum in table [OEMB] - 24, should be 74 20090521 tbutils-246
[    0.227606] ACPI: No dock devices found.
[    0.228031] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.228232] pci 0000:00:02.0: reg 10 32bit mmio: [0xf3f80000-0xf3ffffff]
[    0.228246] pci 0000:00:02.0: reg 14 io port: [0xc880-0xc887]
[    0.228258] pci 0000:00:02.0: reg 18 32bit mmio: [0xd0000000-0xdfffffff]
[    0.228271] pci 0000:00:02.0: reg 1c 32bit mmio: [0xf3f40000-0xf3f7ffff]
[    0.228401] pci 0000:00:1b.0: reg 10 64bit mmio: [0xf3f38000-0xf3f3bfff]
[    0.228456] pci 0000:00:1b.0: PME# supported from D0 D3hot
[    0.228465] pci 0000:00:1b.0: PME# disabled
[    0.228541] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.228550] pci 0000:00:1c.0: PME# disabled
[    0.228626] pci 0000:00:1c.1: PME# supported from D0 D3hot D3cold
[    0.228635] pci 0000:00:1c.1: PME# disabled
[    0.228699] pci 0000:00:1d.0: reg 20 io port: [0xb880-0xb89f]
[    0.228764] pci 0000:00:1d.1: reg 20 io port: [0xc080-0xc09f]
[    0.228829] pci 0000:00:1d.2: reg 20 io port: [0xc480-0xc49f]
[    0.228915] pci 0000:00:1d.7: reg 10 32bit mmio: [0xf3f37c00-0xf3f37fff]
[    0.229000] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
[    0.229010] pci 0000:00:1d.7: PME# disabled
[    0.229126] pci 0000:00:1f.1: reg 20 io port: [0xffa0-0xffaf]
[    0.229233] pci 0000:03:00.0: reg 10 64bit mmio: [0xfbfc0000-0xfbffffff]
[    0.229249] pci 0000:03:00.0: reg 18 io port: [0xe880-0xe8ff]
[    0.229329] pci 0000:03:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.229339] pci 0000:03:00.0: PME# disabled
[    0.229415] pci 0000:00:1c.0: bridge io port: [0xe000-0xefff]
[    0.229425] pci 0000:00:1c.0: bridge 32bit mmio: [0xfbf00000-0xfbffffff]
[    0.229502] pci 0000:01:00.0: reg 10 64bit mmio: [0xfbef0000-0xfbefffff]
[    0.229585] pci 0000:01:00.0: supports D1
[    0.229591] pci 0000:01:00.0: PME# supported from D0 D1 D3hot D3cold
[    0.229601] pci 0000:01:00.0: PME# disabled
[    0.229679] pci 0000:00:1c.1: bridge io port: [0xd000-0xdfff]
[    0.229689] pci 0000:00:1c.1: bridge 32bit mmio: [0xf4000000-0xfbefffff]
[    0.229699] pci 0000:00:1c.1: bridge 32bit mmio pref: [0xcc000000-0xcfffffff]
[    0.229718] pci_bus 0000:00: on NUMA node 0
[    0.229734] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.230037] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.POP4._PRT]
[    0.230166] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.POP5._PRT]
[    0.245970] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 10 *11 12 14 15)
[    0.246291] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 *10 11 12 14 15)
[    0.246606] ACPI: PCI Interrupt Link [LNKC] (IRQs *3 4 5 6 7 10 11 12 14 15)
[    0.246931] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 10 11 12 14 *15)
[    0.247247] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 *4 5 6 7 10 11 12 14 15)
[    0.247562] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 *7 10 11 12 14 15)
[    0.247878] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 *5 6 7 10 11 12 14 15)
[    0.248205] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 *6 7 10 11 12 14 15)
[    0.248711] SCSI subsystem initialized
[    0.248755] libata version 3.00 loaded.
[    0.248755] usbcore: registered new interface driver usbfs
[    0.248755] usbcore: registered new interface driver hub
[    0.248755] usbcore: registered new device driver usb
[    0.248755] ACPI: WMI: Mapper loaded
[    0.248755] PCI: Using ACPI for IRQ routing
[    0.260026] Bluetooth: Core ver 2.15
[    0.260089] NET: Registered protocol family 31
[    0.260089] Bluetooth: HCI device and connection manager initialized
[    0.260089] Bluetooth: HCI socket layer initialized
[    0.260089] NetLabel: Initializing
[    0.260089] NetLabel:  domain hash size = 128
[    0.260089] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.260095] NetLabel:  unlabeled traffic allowed by default
[    0.260183] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[    0.260198] hpet0: 3 comparators, 64-bit 14.318180 MHz counter
[    0.277216] pnp: PnP ACPI init
[    0.277266] ACPI: bus type pnp registered
[    0.283186] pnp: PnP ACPI: found 14 devices
[    0.283194] ACPI: ACPI bus type pnp unregistered
[    0.283205] PnPBIOS: Disabled by ACPI PNP
[    0.283234] system 00:01: iomem range 0x40000000-0x7fffffff has been reserved
[    0.283244] system 00:01: iomem range 0x3f800000-0x3fffffff could not be reserved
[    0.283266] system 00:06: ioport range 0x374-0x375 has been reserved
[    0.283275] system 00:06: ioport range 0x3f4-0x3f5 has been reserved
[    0.283283] system 00:06: ioport range 0x380-0x387 has been reserved
[    0.283292] system 00:06: ioport range 0x9f4-0x9ff has been reserved
[    0.283301] system 00:06: ioport range 0x4d0-0x4d1 has been reserved
[    0.283309] system 00:06: ioport range 0x900-0x9f3 has been reserved
[    0.283318] system 00:06: ioport range 0x400-0x43f has been reserved
[    0.283326] system 00:06: ioport range 0x480-0x4bf has been reserved
[    0.283335] system 00:06: iomem range 0xf0000000-0xf0003fff has been reserved
[    0.283344] system 00:06: iomem range 0x384-0x387 could not be reserved
[    0.283367] system 00:0a: iomem range 0xfec00000-0xfec00fff could not be reserved
[    0.283377] system 00:0a: iomem range 0xfee00000-0xfee00fff has been reserved
[    0.283393] system 00:0c: iomem range 0xe0000000-0xefffffff has been reserved
[    0.283409] system 00:0d: iomem range 0x0-0x9ffff could not be reserved
[    0.283418] system 00:0d: iomem range 0xc0000-0xcffff could not be reserved
[    0.283426] system 00:0d: iomem range 0xe0000-0xfffff could not be reserved
[    0.283435] system 00:0d: iomem range 0x100000-0x3f7fffff could not be reserved
[    0.318355] AppArmor: AppArmor Filesystem Enabled
[    0.318400] pci 0000:00:1c.0: PCI bridge, secondary bus 0000:03
[    0.318409] pci 0000:00:1c.0:   IO window: 0xe000-0xefff
[    0.318421] pci 0000:00:1c.0:   MEM window: 0xfbf00000-0xfbffffff
[    0.318430] pci 0000:00:1c.0:   PREFETCH window: disabled
[    0.318439] pci 0000:00:1c.1: PCI bridge, secondary bus 0000:01
[    0.318447] pci 0000:00:1c.1:   IO window: 0xd000-0xdfff
[    0.318458] pci 0000:00:1c.1:   MEM window: 0xf4000000-0xfbefffff
[    0.318468] pci 0000:00:1c.1:   PREFETCH window: 0xcc000000-0xcfffffff
[    0.318493]   alloc irq_desc for 16 on node -1
[    0.318500]   alloc kstat_irqs on node -1
[    0.318514] pci 0000:00:1c.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.318526] pci 0000:00:1c.0: setting latency timer to 64
[    0.318540]   alloc irq_desc for 17 on node -1
[    0.318545]   alloc kstat_irqs on node -1
[    0.318555] pci 0000:00:1c.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    0.318565] pci 0000:00:1c.1: setting latency timer to 64
[    0.318575] pci_bus 0000:00: resource 0 io:  [0x00-0xffff]
[    0.318583] pci_bus 0000:00: resource 1 mem: [0x000000-0xffffffff]
[    0.318591] pci_bus 0000:03: resource 0 io:  [0xe000-0xefff]
[    0.318598] pci_bus 0000:03: resource 1 mem: [0xfbf00000-0xfbffffff]
[    0.318606] pci_bus 0000:01: resource 0 io:  [0xd000-0xdfff]
[    0.318613] pci_bus 0000:01: resource 1 mem: [0xf4000000-0xfbefffff]
[    0.318621] pci_bus 0000:01: resource 2 pref mem [0xcc000000-0xcfffffff]
[    0.318710] NET: Registered protocol family 2
[    0.318961] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.319745] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.321041] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.321758] TCP: Hash tables configured (established 131072 bind 65536)
[    0.321767] TCP reno registered
[    0.322058] NET: Registered protocol family 1
[    0.322224] Trying to unpack rootfs image as initramfs...
[    0.501195] Switched to high resolution mode on CPU 1
[    0.504003] Switched to high resolution mode on CPU 0
[    0.755286] Freeing initrd memory: 7472k freed
[    0.766662] cpufreq-nforce2: No nForce2 chipset.
[    0.766737] Scanning for low memory corruption every 60 seconds
[    0.767011] audit: initializing netlink socket (disabled)
[    0.767057] type=2000 audit(1263895961.765:1): initialized
[    0.788114] highmem bounce pool size: 64 pages
[    0.788130] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    0.791987] VFS: Disk quotas dquot_6.5.2
[    0.792152] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.793673] fuse init (API version 7.12)
[    0.793932] msgmni has been set to 1732
[    0.794486] alg: No test for stdrng (krng)
[    0.794525] io scheduler noop registered
[    0.794531] io scheduler anticipatory registered
[    0.794537] io scheduler deadline registered
[    0.794672] io scheduler cfq registered (default)
[    0.794703] pci 0000:00:02.0: Boot video device
[    0.794983] pcieport-driver 0000:00:1c.0: setting latency timer to 64
[    0.795142] pcieport-driver 0000:00:1c.1: setting latency timer to 64
[    0.795291] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.795521] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.795852] ACPI: AC Adapter [AC0] (on-line)
[    0.796057] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input0
[    0.797531] ACPI: EC: non-query interrupt received, switching to interrupt mode
[    0.807804] ACPI: Lid Switch [LID]
[    0.807953] input: Sleep Button as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input1
[    0.807963] ACPI: Sleep Button [SLPB]
[    0.808103] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input2
[    0.808111] ACPI: Power Button [PWRB]
[    0.809643] ACPI: SSDT 3f670270 001FA (v01  PmRef  Cpu0Ist 00003000 INTL 20060113)
[    0.810917] ACPI: SSDT 3f670500 0065D (v01  PmRef  Cpu0Cst 00003001 INTL 20060113)
[    0.812409] Monitor-Mwait will be used to enter C-1 state
[    0.812502] Monitor-Mwait will be used to enter C-2 state
[    0.812575] Monitor-Mwait will be used to enter C-3 state
[    0.812646] Monitor-Mwait will be used to enter C-3 state
[    0.812672] Marking TSC unstable due to TSC halts in idle
[    0.812734] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3] C4[C3])
[    0.812812] processor LNXCPU:00: registered as cooling_device0
[    0.813749] ACPI: SSDT 3f6701a0 000CC (v01  PmRef  Cpu1Ist 00003000 INTL 20060113)
[    0.814675] ACPI: SSDT 3f670470 00085 (v01  PmRef  Cpu1Cst 00003000 INTL 20060113)
[    0.816530] ACPI: CPU1 (power states: C1[C1] C2[C2] C3[C3] C4[C3])
[    0.816601] processor LNXCPU:01: registered as cooling_device1
[    0.839279] thermal LNXTHERM:01: registered as thermal_zone0
[    0.839302] ACPI: Thermal Zone [TZ00] (53 C)
[    0.839449] isapnp: Scanning for PnP cards...
[    1.095464] ACPI: Battery Slot [BAT0] (battery present)
[    1.194600] isapnp: No Plug & Play device found
[    1.197875] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    1.201102] brd: module loaded
[    1.202333] loop: module loaded
[    1.202549] input: Macintosh mouse button emulation as /devices/virtual/input/input3
[    1.204140] pata_sch 0000:00:1f.1: version 0.2
[    1.204220] pata_sch 0000:00:1f.1: setting latency timer to 64
[    1.204415] scsi0 : pata_sch
[    1.204653] scsi1 : pata_sch
[    1.205600] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xffa0 irq 14
[    1.205609] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xffa8 irq 15
[    1.206511] Fixed MDIO Bus: probed
[    1.206616] PPP generic driver version 2.4.2
[    1.206871] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    1.206932]   alloc irq_desc for 19 on node -1
[    1.206939]   alloc kstat_irqs on node -1
[    1.206955] ehci_hcd 0000:00:1d.7: PCI INT D -> GSI 19 (level, low) -> IRQ 19
[    1.206990] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    1.206999] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    1.207082] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 1
[    1.211012] ehci_hcd 0000:00:1d.7: debug port 1
[    1.211026] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
[    1.211060] ehci_hcd 0000:00:1d.7: irq 19, io mem 0xf3f37c00
[    1.224033] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    1.224236] usb usb1: configuration #1 chosen from 1 choice
[    1.224323] hub 1-0:1.0: USB hub found
[    1.224344] hub 1-0:1.0: 8 ports detected
[    1.224491] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    1.224544] uhci_hcd: USB Universal Host Controller Interface driver
[    1.224631]   alloc irq_desc for 20 on node -1
[    1.224637]   alloc kstat_irqs on node -1
[    1.224651] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    1.224665] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    1.224674] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    1.224763] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    1.224813] uhci_hcd 0000:00:1d.0: irq 20, io base 0x0000b880
[    1.225029] usb usb2: configuration #1 chosen from 1 choice
[    1.225103] hub 2-0:1.0: USB hub found
[    1.225121] hub 2-0:1.0: 2 ports detected
[    1.225234]   alloc irq_desc for 21 on node -1
[    1.225240]   alloc kstat_irqs on node -1
[    1.225253] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[    1.225265] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    1.225273] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    1.225361] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3
[    1.225408] uhci_hcd 0000:00:1d.1: irq 21, io base 0x0000c080
[    1.225605] usb usb3: configuration #1 chosen from 1 choice
[    1.225675] hub 3-0:1.0: USB hub found
[    1.225692] hub 3-0:1.0: 2 ports detected
[    1.225790]   alloc irq_desc for 18 on node -1
[    1.225796]   alloc kstat_irqs on node -1
[    1.225809] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    1.225821] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    1.225828] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    1.225908] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4
[    1.225955] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000c480
[    1.226151] usb usb4: configuration #1 chosen from 1 choice
[    1.226222] hub 4-0:1.0: USB hub found
[    1.226239] hub 4-0:1.0: 2 ports detected
[    1.226482] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    1.255399] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.255416] serio: i8042 AUX port at 0x60,0x64 irq 12
[    1.255567] mice: PS/2 mouse device common for all mice
[    1.255830] rtc_cmos 00:02: RTC can wake from S4
[    1.255918] rtc_cmos 00:02: rtc core: registered rtc_cmos as rtc0
[    1.255954] rtc0: alarms up to one month, y3k, 114 bytes nvram, hpet irqs
[    1.257292] device-mapper: uevent: version 1.0.3
[    1.257563] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: dm-devel@redhat.com
[    1.257785] device-mapper: multipath: version 1.1.0 loaded
[    1.257795] device-mapper: multipath round-robin: version 1.0.0 loaded
[    1.258142] EISA: Probing bus 0 at eisa.0
[    1.258197] EISA: Detected 0 cards.
[    1.258682] cpuidle: using governor ladder
[    1.259055] cpuidle: using governor menu
[    1.260384] TCP cubic registered
[    1.260819] NET: Registered protocol family 10
[    1.262016] lo: Disabled Privacy Extensions
[    1.262863] NET: Registered protocol family 17
[    1.262921] Bluetooth: L2CAP ver 2.13
[    1.262926] Bluetooth: L2CAP socket layer initialized
[    1.262934] Bluetooth: SCO (Voice Link) ver 0.6
[    1.262938] Bluetooth: SCO socket layer initialized
[    1.263044] Bluetooth: RFCOMM TTY layer initialized
[    1.263056] Bluetooth: RFCOMM socket layer initialized
[    1.263064] Bluetooth: RFCOMM ver 1.11
[    1.264642] Using IPI No-Shortcut mode
[    1.264860] PM: Resume from disk failed.
[    1.264891] registered taskstats version 1
[    1.265150]   Magic number: 10:622:224
[    1.265274] rtc_cmos 00:02: setting system clock to 2010-01-19 10:12:43 UTC (1263895963)
[    1.265285] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.265290] EDD information not available.
[    1.279402] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input4
[    1.417532] ata1.00: ATA-8: ST9160301AS, 0001SDM2, max UDMA/133
[    1.417551] ata1.00: 312581808 sectors, multi 16: LBA48 
[    1.433019] ata1.00: configured for UDMA/100
[    1.433350] scsi 0:0:0:0: Direct-Access     ATA      ST9160301AS      0001 PQ: 0 ANSI: 5
[    1.433716] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.433855] sd 0:0:0:0: [sda] 312581808 512-byte logical blocks: (160 GB/149 GiB)
[    1.434033] sd 0:0:0:0: [sda] Write Protect is off
[    1.434042] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.434126] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.434529]  sda: sda1 sda2 < sda5 >
[    1.489295] sd 0:0:0:0: [sda] Attached SCSI disk
[    1.500212] Clocksource tsc unstable (delta = -213526294 ns)
[    1.599065] Freeing unused kernel memory: 540k freed
[    1.599655] Write protecting the kernel text: 4580k
[    1.599748] Write protecting the kernel read-only data: 1840k
[    1.599987] usb 1-5: new high speed USB device using ehci_hcd and address 3
[    1.815517] usb 1-5: configuration #1 chosen from 1 choice
[    2.091670] usb 3-1: new low speed USB device using uhci_hcd and address 2
[    2.276331] usb 3-1: configuration #1 chosen from 1 choice
[    2.310151] usbcore: registered new interface driver hiddev
[    2.326000] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:1d.1/usb3/3-1/3-1:1.0/input/input5
[    2.326224] generic-usb 0003:046D:C521.0001: input,hidraw0: USB HID v1.11 Mouse [Logitech USB Receiver] on usb-0000:00:1d.1-1/input0
[    2.355375] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:1d.1/usb3/3-1/3-1:1.1/input/input6
[    2.355719] generic-usb 0003:046D:C521.0002: input,hiddev96,hidraw1: USB HID v1.11 Device [Logitech USB Receiver] on usb-0000:00:1d.1-1/input1
[    2.355797] usbcore: registered new interface driver usbhid
[    2.355806] usbhid: v2.6:USB HID core driver
[    4.391056] PM: Starting manual resume from disk
[    4.391069] PM: Resume from partition 8:5
[    4.391074] PM: Checking hibernation image.
[    4.391700] PM: Resume from disk failed.
[    4.407478] EXT4-fs (sda1): INFO: recovery required on readonly filesystem
[    4.407495] EXT4-fs (sda1): write access will be enabled during recovery
[    4.452264] EXT4-fs (sda1): barriers enabled
[    4.882124] kjournald2 starting: pid 338, dev sda1:8, commit interval 5 seconds
[    4.882446] EXT4-fs (sda1): delayed allocation enabled
[    4.882458] EXT4-fs: file extents enabled
[    4.934756] EXT4-fs: mballoc enabled
[    4.934801] EXT4-fs (sda1): recovery complete
[    4.936325] EXT4-fs (sda1): mounted filesystem with ordered data mode
[    6.036605] type=1505 audit(1263895968.270:2): operation="profile_load" pid=363 name=/sbin/dhclient3
[    6.037351] type=1505 audit(1263895968.270:3): operation="profile_load" pid=363 name=/usr/lib/NetworkManager/nm-dhcp-client.action
[    6.037774] type=1505 audit(1263895968.270:4): operation="profile_load" pid=363 name=/usr/lib/connman/scripts/dhclient-script
[    6.084513] type=1505 audit(1263895968.318:5): operation="profile_load" pid=364 name=/usr/bin/evince
[    6.095654] type=1505 audit(1263895968.326:6): operation="profile_load" pid=364 name=/usr/bin/evince-previewer
[    6.102583] type=1505 audit(1263895968.334:7): operation="profile_load" pid=364 name=/usr/bin/evince-thumbnailer
[    6.127783] type=1505 audit(1263895968.358:8): operation="profile_load" pid=366 name=/usr/lib/cups/backend/cups-pdf
[    6.128768] type=1505 audit(1263895968.362:9): operation="profile_load" pid=366 name=/usr/sbin/cupsd
[    6.150575] type=1505 audit(1263895968.382:10): operation="profile_load" pid=367 name=/usr/sbin/tcpdump
[   15.081688] udev: starting version 147
[   15.123152] Adding 2980016k swap on /dev/sda5.  Priority:-1 extents:1 across:2980016k 
[   15.405091] lp: driver loaded but no devices found
[   15.581778] eeepc_laptop: Eee PC Hotkey Driver
[   15.582598] eeepc_laptop: Hotkey init flags 0x41
[   15.584265] eeepc_laptop: TYPE (2000000) not reported by BIOS, enabling anyway
[   15.681889] eeepc_laptop: PANELPOWER (4000000) not reported by BIOS, enabling anyway
[   15.690800] ACPI: I/O resource isch_smbus [0x400-0x43f] conflicts with ACPI region SMRG [0x400-0x43f]
[   15.690815] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   15.692007] eeepc_laptop: TPD (8000000) not reported by BIOS, enabling anyway
[   15.692020] eeepc_laptop: Get control methods supported: 0xe901701
[   15.692229] input: Asus EeePC extra buttons as /devices/virtual/input/input7
[   15.692764] eeepc_laptop: Backlight controlled by ACPI video driver
[   15.707754] atl1c 0000:03:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   15.707785] atl1c 0000:03:00.0: setting latency timer to 64
[   15.707867] atl1c 0000:03:00.0: PME# disabled
[   15.707881] atl1c 0000:03:00.0: PME# disabled
[   15.752588] Linux video capture interface: v2.00
[   15.767733] uvcvideo: Found UVC 1.00 device USB2.0 UVC 1.3M WebCam (13d3:5071)
[   15.795389] cfg80211: Calling CRDA to update world regulatory domain
[   15.825474] input: USB2.0 UVC 1.3M WebCam as /devices/pci0000:00/0000:00:1d.7/usb1/1-5/1-5:1.0/input/input8
[   15.825644] usbcore: registered new interface driver uvcvideo
[   15.825656] USB Video Class driver (v0.1.0)
[   15.849098] EXT4-fs (sda1): internal journal on sda1:8
[   15.858996] atl1c 0000:03:00.0: version 1.0.0.1-NAPI
[   15.913442] cfg80211: World regulatory domain updated:
[   15.913453]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   15.913466]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   15.913478]     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   15.913489]     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   15.913500]     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   15.913511]     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   15.921731] ath9k 0000:01:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   15.921758] ath9k 0000:01:00.0: setting latency timer to 64
[   15.971257] ath: EEPROM regdomain: 0x60
[   15.971268] ath: EEPROM indicates we should expect a direct regpair map
[   15.971281] ath: Country alpha2 being used: 00
[   15.971288] ath: Regpair used: 0x60
[   15.998350] ip_tables: (C) 2000-2006 Netfilter Core Team
[   16.215124] phy0: Selected rate control algorithm 'ath9k_rate_control'
[   16.217931] Registered led device: ath9k-phy0::radio
[   16.218009] Registered led device: ath9k-phy0::assoc
[   16.218085] Registered led device: ath9k-phy0::tx
[   16.218151] Registered led device: ath9k-phy0::rx
[   16.218210] phy0: Atheros AR9285 MAC/BB Rev:2 AR5133 RF Rev:e0: mem=0xf8680000, irq=17
[   16.420438]   alloc irq_desc for 23 on node -1
[   16.420450]   alloc kstat_irqs on node -1
[   16.420472] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[   16.420555] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   16.597102] hda_codec: Unknown model for ALC269, trying auto-probe from BIOS...
[   16.597368] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:1b.0/input/input9
[   16.769983]   alloc irq_desc for 24 on node -1
[   16.769996]   alloc kstat_irqs on node -1
[   16.770031] atl1c 0000:03:00.0: irq 24 for MSI/MSI-X
[   16.770973] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   16.939182] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   17.000093] Synaptics Touchpad, model: 1, fw: 7.2, id: 0x1c0b1, caps: 0xd04731/0xa40000
[   17.107515] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input10
[   17.229998] type=1505 audit(1263895979.462:11): operation="profile_replace" pid=877 name=/sbin/dhclient3
[   17.230718] type=1505 audit(1263895979.462:12): operation="profile_replace" pid=877 name=/usr/lib/NetworkManager/nm-dhcp-client.action
[   17.231124] type=1505 audit(1263895979.462:13): operation="profile_replace" pid=877 name=/usr/lib/connman/scripts/dhclient-script
[   17.244338] type=1505 audit(1263895979.478:14): operation="profile_replace" pid=885 name=/usr/bin/evince
[   17.260108] type=1505 audit(1263895979.494:15): operation="profile_replace" pid=885 name=/usr/bin/evince-previewer
[   17.269194] type=1505 audit(1263895979.502:16): operation="profile_replace" pid=885 name=/usr/bin/evince-thumbnailer
[   17.297265] type=1505 audit(1263895979.530:17): operation="profile_replace" pid=896 name=/usr/lib/cups/backend/cups-pdf
[   17.298562] type=1505 audit(1263895979.530:18): operation="profile_replace" pid=896 name=/usr/sbin/cupsd
[   17.305183] type=1505 audit(1263895979.538:19): operation="profile_replace" pid=899 name=/usr/sbin/tcpdump
[   19.199819] ppdev: user-space parallel port driver
[   19.434962] Linux agpgart interface v0.103
[   19.528418] [drm] Initialized drm 1.1.0 20060810
[   19.583141]   alloc irq_desc for 22 on node -1
[   19.583154]   alloc kstat_irqs on node -1
[   19.583177] psb 0000:00:02.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   19.583194] psb 0000:00:02.0: setting latency timer to 64
[   19.583279] [drm] psb - 5.0.1.0046
[   19.602633] [drm:psb_do_init] *ERROR* Debug is 0x00000000
[   19.625322] psb 0000:00:02.0: firmware: requesting msvdx_fw.bin
[   19.705779] [drm] SGX core id = 0x01130000
[   19.705791] [drm] SGX core rev major = 0x01, minor = 0x02
[   19.705801] [drm] SGX core rev maintenance = 0x01, designer = 0x00
[   19.706284] [drm] intel_lvds_init: OpRegion has the VBT address
[   19.706302] [drm] intel_lvds_init: The bdb->signature is BIOS_DATA_BLOCK &#65533;, the bdb_off is 48
[   19.706340] [drm] intel_lvds_init: BLC Data in BIOS VBT tables: datasize=0 paneltype=15                                 type=0x02 pol=0x00 freq=0x00c8 minlevel=0x00                        i2caddr=0x58 cmd=0xaa 
[   19.706367] [drm] intel_lvds_init: the CoreClock is 200
[   19.706379] [drm] intel_lvds_init: sku_value is 0x00800000
[   19.706387] [drm] intel_lvds_init: sku_bMaxResEnableInt is 0
[   19.706475] [drm] intel_lvds_set_backlight: the level is 100
[   19.706485] [drm] LVDSGetPWMMaxBacklight: the max_pwm_blc is 31250.
[   19.960262] [drm] intel_sdvo_init: sku_value is 0x00800000
[   19.960274] [drm] intel_sdvo_init: sku_bSDVOEnable is 1
[   20.008733] CPU0 attaching NULL sched-domain.
[   20.008751] CPU1 attaching NULL sched-domain.
[   20.408056] [drm] intel_sdvo_init: sku_value is 0x00800000
[   20.408065] [drm] intel_sdvo_init: sku_bSDVOEnable is 1
[   20.413339] CPU0 attaching sched-domain:
[   20.413352]  domain 0: span 0-1 level SIBLING
[   20.413362]   groups: 0 1
[   20.413379] CPU1 attaching sched-domain:
[   20.413387]  domain 0: span 0-1 level SIBLING
[   20.413395]   groups: 1 0
[   21.184642] detear is disabled
[   21.217629] [drm] Initialized psb 4.41.1 20090416 on minor 0
[   23.425411] buffer underrun 0x0
[   62.068160] wlan0: authenticate with AP 00:22:b0:b9:cd:95
[   62.073784] wlan0: authenticated
[   62.073797] wlan0: associate with AP 00:22:b0:b9:cd:95
[   62.077751] wlan0: RX AssocResp from 00:22:b0:b9:cd:95 (capab=0x421 status=0 aid=4)
[   62.077765] wlan0: associated
[   62.079066] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   72.156051] wlan0: no IPv6 routers present
[/HTML]and 'cat  /var/log/syslog' shows:
```
f800000-0x3fffffff could not be reserved
Jan 19 02:12:58 r15x-laptop kernel: [    0.283266] system 00:06: ioport range 0x374-0x375 has been reserved
Jan 19 02:12:58 r15x-laptop kernel: [    0.283275] system 00:06: ioport range 0x3f4-0x3f5 has been reserved
Jan 19 02:12:58 r15x-laptop kernel: [    0.283283] system 00:06: ioport range 0x380-0x387 has been reserved
Jan 19 02:12:58 r15x-laptop kernel: [    0.283292] system 00:06: ioport range 0x9f4-0x9ff has been reserved
Jan 19 02:12:58 r15x-laptop kernel: [    0.283301] system 00:06: ioport range 0x4d0-0x4d1 has been reserved
Jan 19 02:12:58 r15x-laptop kernel: [    0.283309] system 00:06: ioport range 0x900-0x9f3 has been reserved
Jan 19 02:12:58 r15x-laptop kernel: [    0.283318] system 00:06: ioport range 0x400-0x43f has been reserved
Jan 19 02:12:58 r15x-laptop kernel: [    0.283326] system 00:06: ioport range 0x480-0x4bf has been reserved
Jan 19 02:12:58 r15x-laptop kernel: [    0.283335] system 00:06: iomem range 0xf0000000-0xf0003fff has been reserved
Jan 19 02:12:58 r15x-laptop kernel: [    0.283344] system 00:06: iomem range 0x384-0x387 could not be reserved
Jan 19 02:12:58 r15x-laptop kernel: [    0.283367] system 00:0a: iomem range 0xfec00000-0xfec00fff could not be reserved
Jan 19 02:12:58 r15x-laptop kernel: [    0.283377] system 00:0a: iomem range 0xfee00000-0xfee00fff has been reserved
Jan 19 02:12:58 r15x-laptop kernel: [    0.283393] system 00:0c: iomem range 0xe0000000-0xefffffff has been reserved
Jan 19 02:12:58 r15x-laptop kernel: [    0.283409] system 00:0d: iomem range 0x0-0x9ffff could not be reserved
Jan 19 02:12:58 r15x-laptop kernel: [    0.283418] system 00:0d: iomem range 0xc0000-0xcffff could not be reserved
Jan 19 02:12:58 r15x-laptop kernel: [    0.283426] system 00:0d: iomem range 0xe0000-0xfffff could not be reserved
Jan 19 02:12:58 r15x-laptop kernel: [    0.283435] system 00:0d: iomem range 0x100000-0x3f7fffff could not be reserved
Jan 19 02:12:58 r15x-laptop kernel: [    0.318355] AppArmor: AppArmor Filesystem Enabled
Jan 19 02:12:58 r15x-laptop kernel: [    0.318400] pci 0000:00:1c.0: PCI bridge, secondary bus 0000:03
Jan 19 02:12:58 r15x-laptop kernel: [    0.318409] pci 0000:00:1c.0:   IO window: 0xe000-0xefff
Jan 19 02:12:58 r15x-laptop kernel: [    0.318421] pci 0000:00:1c.0:   MEM window: 0xfbf00000-0xfbffffff
Jan 19 02:12:58 r15x-laptop kernel: [    0.318430] pci 0000:00:1c.0:   PREFETCH window: disabled
Jan 19 02:12:58 r15x-laptop kernel: [    0.318439] pci 0000:00:1c.1: PCI bridge, secondary bus 0000:01
Jan 19 02:12:58 r15x-laptop kernel: [    0.318447] pci 0000:00:1c.1:   IO window: 0xd000-0xdfff
Jan 19 02:12:58 r15x-laptop kernel: [    0.318458] pci 0000:00:1c.1:   MEM window: 0xf4000000-0xfbefffff
Jan 19 02:12:58 r15x-laptop modem-manager: Loaded plugin ZTE
Jan 19 02:12:58 r15x-laptop modem-manager: Loaded plugin Huawei
Jan 19 02:12:58 r15x-laptop modem-manager: Loaded plugin Option
Jan 19 02:12:58 r15x-laptop modem-manager: Loaded plugin Novatel
Jan 19 02:12:58 r15x-laptop kernel: [    0.318468] pci 0000:00:1c.1:   PREFETCH window: 0xcc000000-0xcfffffff
Jan 19 02:12:58 r15x-laptop NetworkManager: <info>  Wireless now enabled by radio killswitch
Jan 19 02:12:58 r15x-laptop NetworkManager:    SCPlugin-Ifupdown: (155663088) ... get_connections.
Jan 19 02:12:58 r15x-laptop NetworkManager:    SCPlugin-Ifupdown: (155663088) ... get_connections (managed=false): return empty list.
Jan 19 02:12:58 r15x-laptop kernel: [    0.318493]   alloc irq_desc for 16 on node -1
Jan 19 02:12:58 r15x-laptop kernel: [    0.318500]   alloc kstat_irqs on node -1
Jan 19 02:12:58 r15x-laptop kernel: [    0.318514] pci 0000:00:1c.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Jan 19 02:12:58 r15x-laptop kernel: [    0.318526] pci 0000:00:1c.0: setting latency timer to 64
Jan 19 02:12:58 r15x-laptop kernel: [    0.318540]   alloc irq_desc for 17 on node -1
Jan 19 02:12:58 r15x-laptop kernel: [    0.318545]   alloc kstat_irqs on node -1
Jan 19 02:12:58 r15x-laptop kernel: [    0.318555] pci 0000:00:1c.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
Jan 19 02:12:58 r15x-laptop kernel: [    0.318565] pci 0000:00:1c.1: setting latency timer to 64
Jan 19 02:12:58 r15x-laptop kernel: [    0.318575] pci_bus 0000:00: resource 0 io:  [0x00-0xffff]
Jan 19 02:12:58 r15x-laptop kernel: [    0.318583] pci_bus 0000:00: resource 1 mem: [0x000000-0xffffffff]
Jan 19 02:12:58 r15x-laptop kernel: [    0.318591] pci_bus 0000:03: resource 0 io:  [0xe000-0xefff]
Jan 19 02:12:58 r15x-laptop kernel: [    0.318598] pci_bus 0000:03: resource 1 mem: [0xfbf00000-0xfbffffff]
Jan 19 02:12:58 r15x-laptop kernel: [    0.318606] pci_bus 0000:01: resource 0 io:  [0xd000-0xdfff]
Jan 19 02:12:58 r15x-laptop kernel: [    0.318613] pci_bus 0000:01: resource 1 mem: [0xf4000000-0xfbefffff]
Jan 19 02:12:58 r15x-laptop kernel: [    0.318621] pci_bus 0000:01: resource 2 pref mem [0xcc000000-0xcfffffff]
Jan 19 02:12:58 r15x-laptop kernel: [    0.318710] NET: Registered protocol family 2
Jan 19 02:12:58 r15x-laptop kernel: [    0.318961] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
Jan 19 02:12:58 r15x-laptop kernel: [    0.319745] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
Jan 19 02:12:58 r15x-laptop kernel: [    0.321041] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
Jan 19 02:12:58 r15x-laptop kernel: [    0.321758] TCP: Hash tables configured (established 131072 bind 65536)
Jan 19 02:12:58 r15x-laptop kernel: [    0.321767] TCP reno registered
Jan 19 02:12:58 r15x-laptop kernel: [    0.322058] NET: Registered protocol family 1
Jan 19 02:12:58 r15x-laptop kernel: [    0.322224] Trying to unpack rootfs image as initramfs...
Jan 19 02:12:58 r15x-laptop kernel: [    0.501195] Switched to high resolution mode on CPU 1
Jan 19 02:12:58 r15x-laptop kernel: [    0.504003] Switched to high resolution mode on CPU 0
Jan 19 02:12:58 r15x-laptop kernel: [    0.755286] Freeing initrd memory: 7472k freed
Jan 19 02:12:58 r15x-laptop kernel: [    0.766662] cpufreq-nforce2: No nForce2 chipset.
Jan 19 02:12:58 r15x-laptop kernel: [    0.766737] Scanning for low memory corruption every 60 seconds
Jan 19 02:12:58 r15x-laptop kernel: [    0.767011] audit: initializing netlink socket (disabled)
Jan 19 02:12:58 r15x-laptop kernel: [    0.767057] type=2000 audit(1263895961.765:1): initialized
Jan 19 02:12:58 r15x-laptop kernel: [    0.788114] highmem bounce pool size: 64 pages
Jan 19 02:12:58 r15x-laptop kernel: [    0.788130] HugeTLB registered 4 MB page size, pre-allocated 0 pages
Jan 19 02:12:58 r15x-laptop kernel: [    0.791987] VFS: Disk quotas dquot_6.5.2
Jan 19 02:12:58 r15x-laptop kernel: [    0.792152] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
Jan 19 02:12:58 r15x-laptop kernel: [    0.793673] fuse init (API version 7.12)
Jan 19 02:12:58 r15x-laptop kernel: [    0.793932] msgmni has been set to 1732
Jan 19 02:12:58 r15x-laptop kernel: [    0.794486] alg: No test for stdrng (krng)
Jan 19 02:12:58 r15x-laptop kernel: [    0.794525] io scheduler noop registered
Jan 19 02:12:58 r15x-laptop avahi-daemon[740]: No service file found in /etc/avahi/services.
Jan 19 02:12:58 r15x-laptop kernel: [    0.794531] io scheduler anticipatory registered
Jan 19 02:12:58 r15x-laptop kernel: [    0.794537] io scheduler deadline registered
Jan 19 02:12:58 r15x-laptop kernel: [    0.794672] io scheduler cfq registered (default)
Jan 19 02:12:58 r15x-laptop kernel: [    0.794703] pci 0000:00:02.0: Boot video device
Jan 19 02:12:58 r15x-laptop kernel: [    0.794983] pcieport-driver 0000:00:1c.0: setting latency timer to 64
Jan 19 02:12:58 r15x-laptop kernel: [    0.795142] pcieport-driver 0000:00:1c.1: setting latency timer to 64
Jan 19 02:12:58 r15x-laptop kernel: [    0.795291] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Jan 19 02:12:58 r15x-laptop kernel: [    0.795521] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
Jan 19 02:12:58 r15x-laptop kernel: [    0.795852] ACPI: AC Adapter [AC0] (on-line)
Jan 19 02:12:58 r15x-laptop kernel: [    0.796057] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input0
Jan 19 02:12:58 r15x-laptop kernel: [    0.797531] ACPI: EC: non-query interrupt received, switching to interrupt mode
Jan 19 02:12:58 r15x-laptop kernel: [    0.807804] ACPI: Lid Switch [LID]
Jan 19 02:12:58 r15x-laptop kernel: [    0.807953] input: Sleep Button as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input1
Jan 19 02:12:58 r15x-laptop kernel: [    0.807963] ACPI: Sleep Button [SLPB]
Jan 19 02:12:58 r15x-laptop kernel: [    0.808103] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input2
Jan 19 02:12:58 r15x-laptop kernel: [    0.808111] ACPI: Power Button [PWRB]
Jan 19 02:12:59 r15x-laptop NetworkManager:    Ifupdown: get unmanaged devices count: 0
Jan 19 02:12:59 r15x-laptop NetworkManager: <info>  (eth0): carrier is OFF
Jan 19 02:12:59 r15x-laptop NetworkManager: <info>  (eth0): new Ethernet device (driver: 'atl1c')
Jan 19 02:12:59 r15x-laptop NetworkManager: <info>  (eth0): exported as /org/freedesktop/NetworkManager/Devices/0
Jan 19 02:12:59 r15x-laptop NetworkManager: <info>  (eth0): now managed
Jan 19 02:12:59 r15x-laptop NetworkManager: <info>  (eth0): device state change: 1 -> 2 (reason 2)
Jan 19 02:12:59 r15x-laptop kernel: [    0.809643] ACPI: SSDT 3f670270 001FA (v01  PmRef  Cpu0Ist 00003000 INTL 20060113)
Jan 19 02:12:59 r15x-laptop NetworkManager: <info>  (eth0): bringing up device.
Jan 19 02:12:59 r15x-laptop kernel: [    0.810917] ACPI: SSDT 3f670500 0065D (v01  PmRef  Cpu0Cst 00003001 INTL 20060113)
Jan 19 02:12:59 r15x-laptop NetworkManager: <info>  (eth0): preparing device.
Jan 19 02:12:59 r15x-laptop kernel: [    0.812409] Monitor-Mwait will be used to enter C-1 state
Jan 19 02:12:59 r15x-laptop kernel: [    0.812502] Monitor-Mwait will be used to enter C-2 state
Jan 19 02:12:59 r15x-laptop NetworkManager: <info>  (eth0): deactivating device (reason: 2).
Jan 19 02:12:59 r15x-laptop kernel: [    0.812575] Monitor-Mwait will be used to enter C-3 state
Jan 19 02:12:59 r15x-laptop kernel: [    0.812646] Monitor-Mwait will be used to enter C-3 state
Jan 19 02:12:59 r15x-laptop NetworkManager: Added default wired connection 'Auto eth0' for /sys/devices/pci0000:00/0000:00:1c.0/0000:03:00.0/net/eth0
Jan 19 02:12:59 r15x-laptop kernel: [    0.812672] Marking TSC unstable due to TSC halts in idle
Jan 19 02:12:59 r15x-laptop kernel: [    0.812734] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3] C4[C3])
Jan 19 02:12:59 r15x-laptop NetworkManager: <info>  (wlan0): driver supports SSID scans (scan_capa 0x01).
Jan 19 02:12:59 r15x-laptop kernel: [    0.812812] processor LNXCPU:00: registered as cooling_device0
Jan 19 02:12:59 r15x-laptop kernel: [    0.813749] ACPI: SSDT 3f6701a0 000CC (v01  PmRef  Cpu1Ist 00003000 INTL 20060113)
Jan 19 02:12:59 r15x-laptop NetworkManager: <info>  (wlan0): new 802.11 WiFi device (driver: 'ath9k')
Jan 19 02:12:59 r15x-laptop kernel: [    0.814675] ACPI: SSDT 3f670470 00085 (v01  PmRef  Cpu1Cst 00003000 INTL 20060113)
Jan 19 02:12:59 r15x-laptop NetworkManager: <info>  (wlan0): exported as /org/freedesktop/NetworkManager/Devices/1
Jan 19 02:12:59 r15x-laptop kernel: [    0.816530] ACPI: CPU1 (power states: C1[C1] C2[C2] C3[C3] C4[C3])
Jan 19 02:12:59 r15x-laptop kernel: [    0.816601] processor LNXCPU:01: registered as cooling_device1
Jan 19 02:12:59 r15x-laptop NetworkManager: <info>  (wlan0): now managed
Jan 19 02:12:59 r15x-laptop kernel: [    0.839279] thermal LNXTHERM:01: registered as thermal_zone0
Jan 19 02:12:59 r15x-laptop kernel: [    0.839302] ACPI: Thermal Zone [TZ00] (53 C)
Jan 19 02:12:59 r15x-laptop NetworkManager: <info>  (wlan0): device state change: 1 -> 2 (reason 2)
Jan 19 02:12:59 r15x-laptop kernel: [    0.839449] isapnp: Scanning for PnP cards...
Jan 19 02:12:59 r15x-laptop kernel: [    1.095464] ACPI: Battery Slot [BAT0] (battery present)
Jan 19 02:12:59 r15x-laptop avahi-daemon[740]: Network interface enumeration completed.
Jan 19 02:12:59 r15x-laptop kernel: [    1.194600] isapnp: No Plug & Play device found
Jan 19 02:12:59 r15x-laptop kernel: [    1.197875] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
Jan 19 02:12:59 r15x-laptop avahi-daemon[740]: Registering HINFO record with values 'I686'/'LINUX'.
Jan 19 02:12:59 r15x-laptop avahi-daemon[740]: Server startup complete. Host name is r15x-laptop.local. Local service cookie is 760532834.
Jan 19 02:12:59 r15x-laptop kernel: [    1.201102] brd: module loaded
Jan 19 02:12:59 r15x-laptop kernel: [    1.202333] loop: module loaded
Jan 19 02:12:59 r15x-laptop kernel: [    1.202549] input: Macintosh mouse button emulation as /devices/virtual/input/input3
Jan 19 02:12:59 r15x-laptop kernel: [    1.204140] pata_sch 0000:00:1f.1: version 0.2
Jan 19 02:12:59 r15x-laptop kernel: [    1.204220] pata_sch 0000:00:1f.1: setting latency timer to 64
Jan 19 02:12:59 r15x-laptop kernel: [    1.204415] scsi0 : pata_sch
Jan 19 02:12:59 r15x-laptop kernel: [    1.204653] scsi1 : pata_sch
Jan 19 02:12:59 r15x-laptop kernel: [    1.205600] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xffa0 irq 14
Jan 19 02:12:59 r15x-laptop kernel: [    1.205609] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xffa8 irq 15
Jan 19 02:12:59 r15x-laptop kernel: [    1.206511] Fixed MDIO Bus: probed
Jan 19 02:12:59 r15x-laptop kernel: [    1.206616] PPP generic driver version 2.4.2
Jan 19 02:12:59 r15x-laptop kernel: [    1.206871] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
Jan 19 02:12:59 r15x-laptop kernel: [    1.206932]   alloc irq_desc for 19 on node -1
Jan 19 02:12:59 r15x-laptop kernel: [    1.206939]   alloc kstat_irqs on node -1
Jan 19 02:12:59 r15x-laptop kernel: [    1.206955] ehci_hcd 0000:00:1d.7: PCI INT D -> GSI 19 (level, low) -> IRQ 19
Jan 19 02:12:59 r15x-laptop kernel: [    1.206990] ehci_hcd 0000:00:1d.7: setting latency timer to 64
Jan 19 02:12:59 r15x-laptop kernel: [    1.206999] ehci_hcd 0000:00:1d.7: EHCI Host Controller
Jan 19 02:12:59 r15x-laptop kernel: [    1.207082] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 1
Jan 19 02:12:59 r15x-laptop kernel: [    1.211012] ehci_hcd 0000:00:1d.7: debug port 1
Jan 19 02:12:59 r15x-laptop kernel: [    1.211026] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
Jan 19 02:12:59 r15x-laptop kernel: [    1.211060] ehci_hcd 0000:00:1d.7: irq 19, io mem 0xf3f37c00
Jan 19 02:12:59 r15x-laptop kernel: [    1.224033] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
Jan 19 02:12:59 r15x-laptop kernel: [    1.224236] usb usb1: configuration #1 chosen from 1 choice
Jan 19 02:12:59 r15x-laptop kernel: [    1.224323] hub 1-0:1.0: USB hub found
Jan 19 02:12:59 r15x-laptop kernel: [    1.224344] hub 1-0:1.0: 8 ports detected
Jan 19 02:12:59 r15x-laptop kernel: [    1.224491] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
Jan 19 02:12:59 r15x-laptop kernel: [    1.224544] uhci_hcd: USB Universal Host Controller Interface driver
Jan 19 02:12:59 r15x-laptop NetworkManager: <info>  (wlan0): bringing up device.
Jan 19 02:12:59 r15x-laptop kernel: [    1.224631]   alloc irq_desc for 20 on node -1
Jan 19 02:12:59 r15x-laptop kernel: [    1.224637]   alloc kstat_irqs on node -1
Jan 19 02:12:59 r15x-laptop kernel: [    1.224651] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
Jan 19 02:12:59 r15x-laptop kernel: [    1.224665] uhci_hcd 0000:00:1d.0: setting latency timer to 64
Jan 19 02:12:59 r15x-laptop kernel: [    1.224674] uhci_hcd 0000:00:1d.0: UHCI Host Controller
Jan 19 02:12:59 r15x-laptop kernel: [    1.224763] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
Jan 19 02:12:59 r15x-laptop kernel: [    1.224813] uhci_hcd 0000:00:1d.0: irq 20, io base 0x0000b880
Jan 19 02:12:59 r15x-laptop kernel: [    1.225029] usb usb2: configuration #1 chosen from 1 choice
Jan 19 02:12:59 r15x-laptop kernel: [    1.225103] hub 2-0:1.0: USB hub found
Jan 19 02:12:59 r15x-laptop kernel: [    1.225121] hub 2-0:1.0: 2 ports detected
Jan 19 02:12:59 r15x-laptop kernel: [    1.225234]   alloc irq_desc for 21 on node -1
Jan 19 02:12:59 r15x-laptop kernel: [    1.225240]   alloc kstat_irqs on node -1
Jan 19 02:12:59 r15x-laptop kernel: [    1.225253] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
Jan 19 02:12:59 r15x-laptop kernel: [    1.225265] uhci_hcd 0000:00:1d.1: setting latency timer to 64
Jan 19 02:12:59 r15x-laptop kernel: [    1.225273] uhci_hcd 0000:00:1d.1: UHCI Host Controller
Jan 19 02:12:59 r15x-laptop kernel: [    1.225361] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3
Jan 19 02:12:59 r15x-laptop kernel: [    1.225408] uhci_hcd 0000:00:1d.1: irq 21, io base 0x0000c080
Jan 19 02:12:59 r15x-laptop kernel: [    1.225605] usb usb3: configuration #1 chosen from 1 choice
Jan 19 02:12:59 r15x-laptop kernel: [    1.225675] hub 3-0:1.0: USB hub found
Jan 19 02:12:59 r15x-laptop kernel: [    1.225692] hub 3-0:1.0: 2 ports detected
Jan 19 02:12:59 r15x-laptop kernel: [    1.225790]   alloc irq_desc for 18 on node -1
Jan 19 02:12:59 r15x-laptop kernel: [    1.225796]   alloc kstat_irqs on node -1
Jan 19 02:12:59 r15x-laptop kernel: [    1.225809] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
Jan 19 02:12:59 r15x-laptop kernel: [    1.225821] uhci_hcd 0000:00:1d.2: setting latency timer to 64
Jan 19 02:12:59 r15x-laptop kernel: [    1.225828] uhci_hcd 0000:00:1d.2: UHCI Host Controller
Jan 19 02:12:59 r15x-laptop kernel: [    1.225908] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4
Jan 19 02:12:59 r15x-laptop kernel: [    1.225955] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000c480
Jan 19 02:12:59 r15x-laptop kernel: [    1.226151] usb usb4: configuration #1 chosen from 1 choice
Jan 19 02:12:59 r15x-laptop kernel: [    1.226222] hub 4-0:1.0: USB hub found
Jan 19 02:12:59 r15x-laptop kernel: [    1.226239] hub 4-0:1.0: 2 ports detected
Jan 19 02:12:59 r15x-laptop kernel: [    1.226482] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
Jan 19 02:12:59 r15x-laptop kernel: [    1.255399] serio: i8042 KBD port at 0x60,0x64 irq 1
Jan 19 02:12:59 r15x-laptop kernel: [    1.255416] serio: i8042 AUX port at 0x60,0x64 irq 12
Jan 19 02:12:59 r15x-laptop kernel: [    1.255567] mice: PS/2 mouse device common for all mice
Jan 19 02:12:59 r15x-laptop kernel: [    1.255830] rtc_cmos 00:02: RTC can wake from S4
Jan 19 02:12:59 r15x-laptop kernel: [    1.255918] rtc_cmos 00:02: rtc core: registered rtc_cmos as rtc0
Jan 19 02:12:59 r15x-laptop kernel: [    1.255954] rtc0: alarms up to one month, y3k, 114 bytes nvram, hpet irqs
Jan 19 02:12:59 r15x-laptop kernel: [    1.257292] device-mapper: uevent: version 1.0.3
Jan 19 02:12:59 r15x-laptop kernel: [    1.257563] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: dm-devel@redhat.com
Jan 19 02:12:59 r15x-laptop kernel: [    1.257785] device-mapper: multipath: version 1.1.0 loaded
Jan 19 02:12:59 r15x-laptop kernel: [    1.257795] device-mapper: multipath round-robin: version 1.0.0 loaded
Jan 19 02:12:59 r15x-laptop kernel: [    1.258142] EISA: Probing bus 0 at eisa.0
Jan 19 02:12:59 r15x-laptop kernel: [    1.258197] EISA: Detected 0 cards.
Jan 19 02:12:59 r15x-laptop kernel: [    1.258682] cpuidle: using governor ladder
Jan 19 02:12:59 r15x-laptop kernel: [    1.259055] cpuidle: using governor menu
Jan 19 02:12:59 r15x-laptop kernel: [    1.260384] TCP cubic registered
Jan 19 02:12:59 r15x-laptop kernel: [    1.260819] NET: Registered protocol family 10
Jan 19 02:12:59 r15x-laptop kernel: [    1.262016] lo: Disabled Privacy Extensions
Jan 19 02:12:59 r15x-laptop kernel: [    1.262863] NET: Registered protocol family 17
Jan 19 02:12:59 r15x-laptop kernel: [    1.262921] Bluetooth: L2CAP ver 2.13
Jan 19 02:12:59 r15x-laptop kernel: [    1.262926] Bluetooth: L2CAP socket layer initialized
Jan 19 02:12:59 r15x-laptop kernel: [    1.262934] Bluetooth: SCO (Voice Link) ver 0.6
Jan 19 02:12:59 r15x-laptop NetworkManager: <info>  (wlan0): preparing device.
Jan 19 02:12:59 r15x-laptop kernel: [    1.262938] Bluetooth: SCO socket layer initialized
Jan 19 02:12:59 r15x-laptop kernel: [    1.263044] Bluetooth: RFCOMM TTY layer initialized
Jan 19 02:12:59 r15x-laptop kernel: [    1.263056] Bluetooth: RFCOMM socket layer initialized
Jan 19 02:12:59 r15x-laptop kernel: [    1.263064] Bluetooth: RFCOMM ver 1.11
Jan 19 02:12:59 r15x-laptop kernel: [    1.264642] Using IPI No-Shortcut mode
Jan 19 02:12:59 r15x-laptop kernel: [    1.264860] PM: Resume from disk failed.
Jan 19 02:12:59 r15x-laptop kernel: [    1.264891] registered taskstats version 1
Jan 19 02:12:59 r15x-laptop kernel: [    1.265150]   Magic number: 10:622:224
Jan 19 02:12:59 r15x-laptop kernel: [    1.265274] rtc_cmos 00:02: setting system clock to 2010-01-19 10:12:43 UTC (1263895963)
Jan 19 02:12:59 r15x-laptop kernel: [    1.265285] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
Jan 19 02:12:59 r15x-laptop kernel: [    1.265290] EDD information not available.
Jan 19 02:12:59 r15x-laptop kernel: [    1.279402] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input4
Jan 19 02:12:59 r15x-laptop kernel: [    1.417532] ata1.00: ATA-8: ST9160301AS, 0001SDM2, max UDMA/133
Jan 19 02:12:59 r15x-laptop kernel: [    1.417551] ata1.00: 312581808 sectors, multi 16: LBA48 
Jan 19 02:12:59 r15x-laptop kernel: [    1.433019] ata1.00: configured for UDMA/100
Jan 19 02:12:59 r15x-laptop kernel: [    1.433350] scsi 0:0:0:0: Direct-Access     ATA      ST9160301AS      0001 PQ: 0 ANSI: 5
Jan 19 02:12:59 r15x-laptop kernel: [    1.433716] sd 0:0:0:0: Attached scsi generic sg0 type 0
Jan 19 02:12:59 r15x-laptop kernel: [    1.433855] sd 0:0:0:0: [sda] 312581808 512-byte logical blocks: (160 GB/149 GiB)
Jan 19 02:12:59 r15x-laptop kernel: [    1.434033] sd 0:0:0:0: [sda] Write Protect is off
Jan 19 02:12:59 r15x-laptop kernel: [    1.434042] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Jan 19 02:12:59 r15x-laptop kernel: [    1.434126] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Jan 19 02:12:59 r15x-laptop kernel: [    1.434529]  sda: sda1 sda2 < sda5 >
Jan 19 02:12:59 r15x-laptop kernel: [    1.489295] sd 0:0:0:0: [sda] Attached SCSI disk
Jan 19 02:12:59 r15x-laptop kernel: [    1.500212] Clocksource tsc unstable (delta = -213526294 ns)
Jan 19 02:12:59 r15x-laptop kernel: [    1.599065] Freeing unused kernel memory: 540k freed
Jan 19 02:12:59 r15x-laptop kernel: [    1.599655] Write protecting the kernel text: 4580k
Jan 19 02:12:59 r15x-laptop kernel: [    1.599748] Write protecting the kernel read-only data: 1840k
Jan 19 02:12:59 r15x-laptop kernel: [    1.599987] usb 1-5: new high speed USB device using ehci_hcd and address 3
Jan 19 02:12:59 r15x-laptop kernel: [    1.815517] usb 1-5: configuration #1 chosen from 1 choice
Jan 19 02:12:59 r15x-laptop kernel: [    2.091670] usb 3-1: new low speed USB device using uhci_hcd and address 2
Jan 19 02:12:59 r15x-laptop kernel: [    2.276331] usb 3-1: configuration #1 chosen from 1 choice
Jan 19 02:12:59 r15x-laptop kernel: [    2.310151] usbcore: registered new interface driver hiddev
Jan 19 02:12:59 r15x-laptop kernel: [    2.326000] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:1d.1/usb3/3-1/3-1:1.0/input/input5
Jan 19 02:12:59 r15x-laptop kernel: [    2.326224] generic-usb 0003:046D:C521.0001: input,hidraw0: USB HID v1.11 Mouse [Logitech USB Receiver] on usb-0000:00:1d.1-1/input0
Jan 19 02:12:59 r15x-laptop kernel: [    2.355375] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:1d.1/usb3/3-1/3-1:1.1/input/input6
Jan 19 02:12:59 r15x-laptop kernel: [    2.355719] generic-usb 0003:046D:C521.0002: input,hiddev96,hidraw1: USB HID v1.11 Device [Logitech USB Receiver] on usb-0000:00:1d.1-1/input1
Jan 19 02:12:59 r15x-laptop kernel: [    2.355797] usbcore: registered new interface driver usbhid
Jan 19 02:12:59 r15x-laptop kernel: [    2.355806] usbhid: v2.6:USB HID core driver
Jan 19 02:12:59 r15x-laptop kernel: [    4.391056] PM: Starting manual resume from disk
Jan 19 02:12:59 r15x-laptop kernel: [    4.391069] PM: Resume from partition 8:5
Jan 19 02:12:59 r15x-laptop kernel: [    4.391074] PM: Checking hibernation image.
Jan 19 02:12:59 r15x-laptop kernel: [    4.391700] PM: Resume from disk failed.
Jan 19 02:12:59 r15x-laptop kernel: [    4.407478] EXT4-fs (sda1): INFO: recovery required on readonly filesystem
Jan 19 02:12:59 r15x-laptop kernel: [    4.407495] EXT4-fs (sda1): write access will be enabled during recovery
Jan 19 02:12:59 r15x-laptop NetworkManager: <info>  (wlan0): deactivating device (reason: 2).
Jan 19 02:12:59 r15x-laptop NetworkManager: supplicant_interface_acquire: assertion `mgr_state == NM_SUPPLICANT_MANAGER_STATE_IDLE' failed
Jan 19 02:12:59 r15x-laptop NetworkManager: <WARN>  default_adapter_cb(): bluez error getting default adapter: The name org.bluez was not provided by any .service files
Jan 19 02:12:59 r15x-laptop NetworkManager: <info>  modem-manager is now available
Jan 19 02:12:59 r15x-laptop NetworkManager: <info>  Trying to start the supplicant...
Jan 19 02:12:59 r15x-laptop kernel: [    4.452264] EXT4-fs (sda1): barriers enabled
Jan 19 02:12:59 r15x-laptop kernel: [    4.882124] kjournald2 starting: pid 338, dev sda1:8, commit interval 5 seconds
Jan 19 02:12:59 r15x-laptop kernel: [    4.882446] EXT4-fs (sda1): delayed allocation enabled
Jan 19 02:12:59 r15x-laptop kernel: [    4.882458] EXT4-fs: file extents enabled
Jan 19 02:12:59 r15x-laptop kernel: [    4.934756] EXT4-fs: mballoc enabled
Jan 19 02:12:59 r15x-laptop kernel: [    4.934801] EXT4-fs (sda1): recovery complete
Jan 19 02:12:59 r15x-laptop kernel: [    4.936325] EXT4-fs (sda1): mounted filesystem with ordered data mode
Jan 19 02:12:59 r15x-laptop kernel: [    6.036605] type=1505 audit(1263895968.270:2): operation="profile_load" pid=363 name=/sbin/dhclient3
Jan 19 02:12:59 r15x-laptop kernel: [    6.037351] type=1505 audit(1263895968.270:3): operation="profile_load" pid=363 name=/usr/lib/NetworkManager/nm-dhcp-client.action
Jan 19 02:12:59 r15x-laptop kernel: [    6.037774] type=1505 audit(1263895968.270:4): operation="profile_load" pid=363 name=/usr/lib/connman/scripts/dhclient-script
Jan 19 02:12:59 r15x-laptop kernel: [    6.084513] type=1505 audit(1263895968.318:5): operation="profile_load" pid=364 name=/usr/bin/evince
Jan 19 02:12:59 r15x-laptop kernel: [    6.095654] type=1505 audit(1263895968.326:6): operation="profile_load" pid=364 name=/usr/bin/evince-previewer
Jan 19 02:12:59 r15x-laptop kernel: [    6.102583] type=1505 audit(1263895968.334:7): operation="profile_load" pid=364 name=/usr/bin/evince-thumbnailer
Jan 19 02:12:59 r15x-laptop kernel: [    6.127783] type=1505 audit(1263895968.358:8): operation="profile_load" pid=366 name=/usr/lib/cups/backend/cups-pdf
Jan 19 02:12:59 r15x-laptop kernel: [    6.128768] type=1505 audit(1263895968.362:9): operation="profile_load" pid=366 name=/usr/sbin/cupsd
Jan 19 02:12:59 r15x-laptop kernel: [    6.150575] type=1505 audit(1263895968.382:10): operation="profile_load" pid=367 name=/usr/sbin/tcpdump
Jan 19 02:12:59 r15x-laptop kernel: [   15.081688] udev: starting version 147
Jan 19 02:12:59 r15x-laptop kernel: [   15.123152] Adding 2980016k swap on /dev/sda5.  Priority:-1 extents:1 across:2980016k 
Jan 19 02:12:59 r15x-laptop kernel: [   15.405091] lp: driver loaded but no devices found
Jan 19 02:12:59 r15x-laptop kernel: [   15.581778] eeepc_laptop: Eee PC Hotkey Driver
Jan 19 02:12:59 r15x-laptop kernel: [   15.582598] eeepc_laptop: Hotkey init flags 0x41
Jan 19 02:12:59 r15x-laptop kernel: [   15.584265] eeepc_laptop: TYPE (2000000) not reported by BIOS, enabling anyway
Jan 19 02:12:59 r15x-laptop kernel: [   15.681889] eeepc_laptop: PANELPOWER (4000000) not reported by BIOS, enabling anyway
Jan 19 02:12:59 r15x-laptop kernel: [   15.690800] ACPI: I/O resource isch_smbus [0x400-0x43f] conflicts with ACPI region SMRG [0x400-0x43f]
Jan 19 02:12:59 r15x-laptop kernel: [   15.690815] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
Jan 19 02:12:59 r15x-laptop kernel: [   15.692007] eeepc_laptop: TPD (8000000) not reported by BIOS, enabling anyway
Jan 19 02:12:59 r15x-laptop kernel: [   15.692020] eeepc_laptop: Get control methods supported: 0xe901701
Jan 19 02:12:59 r15x-laptop kernel: [   15.692229] input: Asus EeePC extra buttons as /devices/virtual/input/input7
Jan 19 02:12:59 r15x-laptop kernel: [   15.692764] eeepc_laptop: Backlight controlled by ACPI video driver
Jan 19 02:12:59 r15x-laptop kernel: [   15.707754] atl1c 0000:03:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Jan 19 02:12:59 r15x-laptop kernel: [   15.707785] atl1c 0000:03:00.0: setting latency timer to 64
Jan 19 02:12:59 r15x-laptop kernel: [   15.707867] atl1c 0000:03:00.0: PME# disabled
Jan 19 02:12:59 r15x-laptop kernel: [   15.707881] atl1c 0000:03:00.0: PME# disabled
Jan 19 02:12:59 r15x-laptop kernel: [   15.752588] Linux video capture interface: v2.00
Jan 19 02:12:59 r15x-laptop kernel: [   15.767733] uvcvideo: Found UVC 1.00 device USB2.0 UVC 1.3M WebCam (13d3:5071)
Jan 19 02:12:59 r15x-laptop kernel: [   15.795389] cfg80211: Calling CRDA to update world regulatory domain
Jan 19 02:12:59 r15x-laptop kernel: [   15.825474] input: USB2.0 UVC 1.3M WebCam as /devices/pci0000:00/0000:00:1d.7/usb1/1-5/1-5:1.0/input/input8
Jan 19 02:12:59 r15x-laptop kernel: [   15.825644] usbcore: registered new interface driver uvcvideo
Jan 19 02:12:59 r15x-laptop kernel: [   15.825656] USB Video Class driver (v0.1.0)
Jan 19 02:12:59 r15x-laptop kernel: [   15.849098] EXT4-fs (sda1): internal journal on sda1:8
Jan 19 02:12:59 r15x-laptop kernel: [   15.858996] atl1c 0000:03:00.0: version 1.0.0.1-NAPI
Jan 19 02:12:59 r15x-laptop kernel: [   15.913442] cfg80211: World regulatory domain updated:
Jan 19 02:12:59 r15x-laptop kernel: [   15.913453]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
Jan 19 02:12:59 r15x-laptop NetworkManager: <info>  (wlan0): supplicant manager state:  down -> idle
Jan 19 02:12:59 r15x-laptop NetworkManager: <info>  (wlan0): device state change: 2 -> 3 (reason 0)
Jan 19 02:12:59 r15x-laptop kernel: [   15.913466]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Jan 19 02:12:59 r15x-laptop kernel: [   15.913478]     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Jan 19 02:12:59 r15x-laptop kernel: [   15.913489]     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Jan 19 02:12:59 r15x-laptop kernel: [   15.913500]     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Jan 19 02:12:59 r15x-laptop kernel: [   15.913511]     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Jan 19 02:12:59 r15x-laptop kernel: [   15.921731] ath9k 0000:01:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
Jan 19 02:12:59 r15x-laptop kernel: [   15.921758] ath9k 0000:01:00.0: setting latency timer to 64
Jan 19 02:12:59 r15x-laptop kernel: [   15.971257] ath: EEPROM regdomain: 0x60
Jan 19 02:12:59 r15x-laptop kernel: [   15.971268] ath: EEPROM indicates we should expect a direct regpair map
Jan 19 02:12:59 r15x-laptop kernel: [   15.971281] ath: Country alpha2 being used: 00
Jan 19 02:12:59 r15x-laptop kernel: [   15.971288] ath: Regpair used: 0x60
Jan 19 02:12:59 r15x-laptop kernel: [   15.998350] ip_tables: (C) 2000-2006 Netfilter Core Team
Jan 19 02:12:59 r15x-laptop kernel: [   16.215124] phy0: Selected rate control algorithm 'ath9k_rate_control'
Jan 19 02:12:59 r15x-laptop kernel: [   16.217931] Registered led device: ath9k-phy0::radio
Jan 19 02:12:59 r15x-laptop kernel: [   16.218009] Registered led device: ath9k-phy0::assoc
Jan 19 02:12:59 r15x-laptop kernel: [   16.218085] Registered led device: ath9k-phy0::tx
Jan 19 02:12:59 r15x-laptop kernel: [   16.218151] Registered led device: ath9k-phy0::rx
Jan 19 02:12:59 r15x-laptop kernel: [   16.218210] phy0: Atheros AR9285 MAC/BB Rev:2 AR5133 RF Rev:e0: mem=0xf8680000, irq=17
Jan 19 02:12:59 r15x-laptop kernel: [   16.420438]   alloc irq_desc for 23 on node -1
Jan 19 02:12:59 r15x-laptop kernel: [   16.420450]   alloc kstat_irqs on node -1
Jan 19 02:12:59 r15x-laptop kernel: [   16.420472] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
Jan 19 02:12:59 r15x-laptop kernel: [   16.420555] HDA Intel 0000:00:1b.0: setting latency timer to 64
Jan 19 02:12:59 r15x-laptop kernel: [   16.597102] hda_codec: Unknown model for ALC269, trying auto-probe from BIOS...
Jan 19 02:12:59 r15x-laptop kernel: [   16.597368] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:1b.0/input/input9
Jan 19 02:12:59 r15x-laptop kernel: [   16.769983]   alloc irq_desc for 24 on node -1
Jan 19 02:12:59 r15x-laptop kernel: [   16.769996]   alloc kstat_irqs on node -1
Jan 19 02:12:59 r15x-laptop kernel: [   16.770031] atl1c 0000:03:00.0: irq 24 for MSI/MSI-X
Jan 19 02:12:59 r15x-laptop kernel: [   16.770973] ADDRCONF(NETDEV_UP): eth0: link is not ready
Jan 19 02:12:59 r15x-laptop kernel: [   16.939182] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Jan 19 02:12:59 r15x-laptop kernel: [   17.000093] Synaptics Touchpad, model: 1, fw: 7.2, id: 0x1c0b1, caps: 0xd04731/0xa40000
Jan 19 02:12:59 r15x-laptop kernel: [   17.107515] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input10
Jan 19 02:12:59 r15x-laptop NetworkManager: <info>  (wlan0): supplicant interface state:  starting -> ready
Jan 19 02:12:59 r15x-laptop kernel: [   17.229998] type=1505 audit(1263895979.462:11): operation="profile_replace" pid=877 name=/sbin/dhclient3
Jan 19 02:12:59 r15x-laptop kernel: [   17.230718] type=1505 audit(1263895979.462:12): operation="profile_replace" pid=877 name=/usr/lib/NetworkManager/nm-dhcp-client.action
Jan 19 02:12:59 r15x-laptop kernel: [   17.231124] type=1505 audit(1263895979.462:13): operation="profile_replace" pid=877 name=/usr/lib/connman/scripts/dhclient-script
Jan 19 02:12:59 r15x-laptop kernel: [   17.244338] type=1505 audit(1263895979.478:14): operation="profile_replace" pid=885 name=/usr/bin/evince
Jan 19 02:12:59 r15x-laptop kernel: [   17.260108] type=1505 audit(1263895979.494:15): operation="profile_replace" pid=885 name=/usr/bin/evince-previewer
Jan 19 02:12:59 r15x-laptop kernel: [   17.269194] type=1505 audit(1263895979.502:16): operation="profile_replace" pid=885 name=/usr/bin/evince-thumbnailer
Jan 19 02:12:59 r15x-laptop kernel: [   17.297265] type=1505 audit(1263895979.530:17): operation="profile_replace" pid=896 name=/usr/lib/cups/backend/cups-pdf
Jan 19 02:12:59 r15x-laptop kernel: [   17.298562] type=1505 audit(1263895979.530:18): operation="profile_replace" pid=896 name=/usr/sbin/cupsd
Jan 19 02:12:59 r15x-laptop kernel: [   17.305183] type=1505 audit(1263895979.538:19): operation="profile_replace" pid=899 name=/usr/sbin/tcpdump
Jan 19 02:12:59 r15x-laptop gdm-binary[831]: WARNING: Unable to load file '/etc/gdm/custom.conf': No such file or directory
Jan 19 02:12:59 r15x-laptop gdm-simple-slave[948]: WARNING: Unable to load file '/etc/gdm/custom.conf': No such file or directory
Jan 19 02:12:59 r15x-laptop gdm-binary[831]: WARNING: Unable to find users: no seat-id found
Jan 19 02:12:59 r15x-laptop cron[959]: (CRON) INFO (pidfile fd = 3)
Jan 19 02:12:59 r15x-laptop init: apport pre-start process (956) terminated with status 1
Jan 19 02:12:59 r15x-laptop init: apport post-stop process (973) terminated with status 1
Jan 19 02:12:59 r15x-laptop cron[980]: (CRON) STARTUP (fork ok)
Jan 19 02:13:00 r15x-laptop cron[980]: (CRON) INFO (Running @reboot jobs)
Jan 19 02:13:00 r15x-laptop anacron[974]: Anacron 2.3 started on 2010-01-19
Jan 19 02:13:00 r15x-laptop anacron[974]: Normal exit (0 jobs run)
Jan 19 02:13:00 r15x-laptop acpid: client connected from 962[0:0]
Jan 19 02:13:00 r15x-laptop wpa_supplicant[843]: CTRL-EVENT-SCAN-RESULTS 
Jan 19 02:13:00 r15x-laptop wpa_supplicant[843]: WPS-AP-AVAILABLE 
Jan 19 02:13:00 r15x-laptop acpid: client connected from 1072[106:113]
Jan 19 02:13:01 r15x-laptop kernel: [   19.199819] ppdev: user-space parallel port driver
Jan 19 02:13:01 r15x-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1d.0/usb2
Jan 19 02:13:01 r15x-laptop udev-configure-printer: Failed to get parent
Jan 19 02:13:01 r15x-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1d.0/usb2/2-0:1.0
Jan 19 02:13:01 r15x-laptop udev-configure-printer: parent devpath is /devices/pci0000:00/0000:00:1d.0/usb2
Jan 19 02:13:01 r15x-laptop udev-configure-printer: Device vendor/product is 1D6B:0001
Jan 19 02:13:01 r15x-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1d.1/usb3
Jan 19 02:13:01 r15x-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1d.1/usb3/3-0:1.0
Jan 19 02:13:01 r15x-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1d.1/usb3/3-1
Jan 19 02:13:01 r15x-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1d.1/usb3/3-1/3-1:1.0
Jan 19 02:13:01 r15x-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1d.1/usb3/3-1/3-1:1.1
Jan 19 02:13:01 r15x-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1d.1/usb3/3-1/3-1:1.1/usb/hiddev0
Jan 19 02:13:01 r15x-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1d.2/usb4
Jan 19 02:13:01 r15x-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1d.2/usb4/4-0:1.0
Jan 19 02:13:01 r15x-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1d.7/usb1
Jan 19 02:13:01 r15x-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1d.7/usb1/1-0:1.0
Jan 19 02:13:01 r15x-laptop kernel: [   19.434962] Linux agpgart interface v0.103
Jan 19 02:13:01 r15x-laptop udev-configure-printer: invalid or missing IEEE 1284 Device ID
Jan 19 02:13:01 r15x-laptop udev-configure-printer: Failed to get parent
Jan 19 02:13:01 r15x-laptop udev-configure-printer: parent devpath is /devices/pci0000:00/0000:00:1d.1/usb3
Jan 19 02:13:01 r15x-laptop udev-configure-printer: Device vendor/product is 1D6B:0001
Jan 19 02:13:01 r15x-laptop udev-configure-printer: invalid or missing IEEE 1284 Device ID
Jan 19 02:13:01 r15x-laptop udev-configure-printer: parent devpath is /devices/pci0000:00/0000:00:1d.1/usb3
Jan 19 02:13:01 r15x-laptop udev-configure-printer: Device vendor/product is 1D6B:0001
Jan 19 02:13:01 r15x-laptop udev-configure-printer: invalid or missing IEEE 1284 Device ID
Jan 19 02:13:01 r15x-laptop udev-configure-printer: parent devpath is /devices/pci0000:00/0000:00:1d.1/usb3/3-1
Jan 19 02:13:01 r15x-laptop kernel: [   19.528418] [drm] Initialized drm 1.1.0 20060810
Jan 19 02:13:01 r15x-laptop udev-configure-printer: Device vendor/product is 046D:C521
Jan 19 02:13:01 r15x-laptop udev-configure-printer: invalid or missing IEEE 1284 Device ID
Jan 19 02:13:01 r15x-laptop udev-configure-printer: parent devpath is /devices/pci0000:00/0000:00:1d.1/usb3/3-1
Jan 19 02:13:01 r15x-laptop udev-configure-printer: Device vendor/product is 046D:C521
Jan 19 02:13:01 r15x-laptop udev-configure-printer: invalid or missing IEEE 1284 Device ID
Jan 19 02:13:01 r15x-laptop udev-configure-printer: Failed to get parent
Jan 19 02:13:01 r15x-laptop udev-configure-printer: parent devpath is /devices/pci0000:00/0000:00:1d.1/usb3/3-1
Jan 19 02:13:01 r15x-laptop udev-configure-printer: Device vendor/product is 046D:C521
Jan 19 02:13:01 r15x-laptop udev-configure-printer: invalid or missing IEEE 1284 Device ID
Jan 19 02:13:01 r15x-laptop udev-configure-printer: parent devpath is /devices/pci0000:00/0000:00:1d.2/usb4
Jan 19 02:13:01 r15x-laptop udev-configure-printer: Device vendor/product is 1D6B:0001
Jan 19 02:13:01 r15x-laptop udev-configure-printer: invalid or missing IEEE 1284 Device ID
Jan 19 02:13:01 r15x-laptop udev-configure-printer: Failed to get parent
Jan 19 02:13:01 r15x-laptop udev-configure-printer: parent devpath is /devices/pci0000:00/0000:00:1d.7/usb1
Jan 19 02:13:01 r15x-laptop udev-configure-printer: Device vendor/product is 1D6B:0002
Jan 19 02:13:01 r15x-laptop udev-configure-printer: invalid or missing IEEE 1284 Device ID
Jan 19 02:13:01 r15x-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1d.7/usb1/1-5
Jan 19 02:13:01 r15x-laptop udev-configure-printer: parent devpath is /devices/pci0000:00/0000:00:1d.7/usb1
Jan 19 02:13:01 r15x-laptop udev-configure-printer: Device vendor/product is 1D6B:0002
Jan 19 02:13:01 r15x-laptop udev-configure-printer: invalid or missing IEEE 1284 Device ID
Jan 19 02:13:01 r15x-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1d.7/usb1/1-5/1-5:1.0
Jan 19 02:13:01 r15x-laptop udev-configure-printer: parent devpath is /devices/pci0000:00/0000:00:1d.7/usb1/1-5
Jan 19 02:13:01 r15x-laptop udev-configure-printer: Device vendor/product is 13D3:5071
Jan 19 02:13:01 r15x-laptop udev-configure-printer: invalid or missing IEEE 1284 Device ID
Jan 19 02:13:01 r15x-laptop udev-configure-printer: add /devices/pci0000:00/0000:00:1d.7/usb1/1-5/1-5:1.1
Jan 19 02:13:01 r15x-laptop udev-configure-printer: parent devpath is /devices/pci0000:00/0000:00:1d.7/usb1/1-5
Jan 19 02:13:01 r15x-laptop udev-configure-printer: Device vendor/product is 13D3:5071
Jan 19 02:13:01 r15x-laptop udev-configure-printer: invalid or missing IEEE 1284 Device ID
Jan 19 02:13:01 r15x-laptop kernel: [   19.583141]   alloc irq_desc for 22 on node -1
Jan 19 02:13:01 r15x-laptop kernel: [   19.583154]   alloc kstat_irqs on node -1
Jan 19 02:13:01 r15x-laptop kernel: [   19.583177] psb 0000:00:02.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
Jan 19 02:13:01 r15x-laptop kernel: [   19.583194] psb 0000:00:02.0: setting latency timer to 64
Jan 19 02:13:01 r15x-laptop kernel: [   19.583279] [drm] psb - 5.0.1.0046
Jan 19 02:13:01 r15x-laptop kernel: [   19.602633] [drm:psb_do_init] *ERROR* Debug is 0x00000000
Jan 19 02:13:01 r15x-laptop kernel: [   19.625322] psb 0000:00:02.0: firmware: requesting msvdx_fw.bin
Jan 19 02:13:01 r15x-laptop kernel: [   19.705779] [drm] SGX core id = 0x01130000
Jan 19 02:13:01 r15x-laptop kernel: [   19.705791] [drm] SGX core rev major = 0x01, minor = 0x02
Jan 19 02:13:01 r15x-laptop kernel: [   19.705801] [drm] SGX core rev maintenance = 0x01, designer = 0x00
Jan 19 02:13:01 r15x-laptop kernel: [   19.706284] [drm] intel_lvds_init: OpRegion has the VBT address
Jan 19 02:13:01 r15x-laptop kernel: [   19.706302] [drm] intel_lvds_init: The bdb->signature is BIOS_DATA_BLOCK &#65533;, the bdb_off is 48
Jan 19 02:13:01 r15x-laptop kernel: [   19.706340] [drm] intel_lvds_init: BLC Data in BIOS VBT tables: datasize=0 paneltype=15                     type=0x02 pol=0x00 freq=0x00c8 minlevel=0x00                        i2caddr=0x58 cmd=0xaa 
Jan 19 02:13:01 r15x-laptop kernel: [   19.706367] [drm] intel_lvds_init: the CoreClock is 200
Jan 19 02:13:01 r15x-laptop kernel: [   19.706379] [drm] intel_lvds_init: sku_value is 0x00800000
Jan 19 02:13:01 r15x-laptop kernel: [   19.706387] [drm] intel_lvds_init: sku_bMaxResEnableInt is 0
Jan 19 02:13:01 r15x-laptop kernel: [   19.706475] [drm] intel_lvds_set_backlight: the level is 100
Jan 19 02:13:01 r15x-laptop kernel: [   19.706485] [drm] LVDSGetPWMMaxBacklight: the max_pwm_blc is 31250.
Jan 19 02:13:02 r15x-laptop kernel: [   19.960262] [drm] intel_sdvo_init: sku_value is 0x00800000
Jan 19 02:13:02 r15x-laptop kernel: [   19.960274] [drm] intel_sdvo_init: sku_bSDVOEnable is 1
Jan 19 02:13:02 r15x-laptop anacron[1294]: Anacron 2.3 started on 2010-01-19
Jan 19 02:13:02 r15x-laptop anacron[1294]: Normal exit (0 jobs run)
Jan 19 02:13:02 r15x-laptop kernel: [   20.008733] CPU0 attaching NULL sched-domain.
Jan 19 02:13:02 r15x-laptop kernel: [   20.008751] CPU1 attaching NULL sched-domain.
Jan 19 02:13:02 r15x-laptop kernel: [   20.408056] [drm] intel_sdvo_init: sku_value is 0x00800000
Jan 19 02:13:02 r15x-laptop kernel: [   20.408065] [drm] intel_sdvo_init: sku_bSDVOEnable is 1
Jan 19 02:13:02 r15x-laptop kernel: [   20.413339] CPU0 attaching sched-domain:
Jan 19 02:13:02 r15x-laptop kernel: [   20.413352]  domain 0: span 0-1 level SIBLING
Jan 19 02:13:02 r15x-laptop kernel: [   20.413362]   groups: 0 1
Jan 19 02:13:02 r15x-laptop kernel: [   20.413379] CPU1 attaching sched-domain:
Jan 19 02:13:02 r15x-laptop kernel: [   20.413387]  domain 0: span 0-1 level SIBLING
Jan 19 02:13:02 r15x-laptop kernel: [   20.413395]   groups: 1 0
Jan 19 02:13:03 r15x-laptop kernel: [   21.184642] detear is disabled
Jan 19 02:13:03 r15x-laptop kernel: [   21.217629] [drm] Initialized psb 4.41.1 20090416 on minor 0
Jan 19 02:13:05 r15x-laptop kernel: [   23.425411] buffer underrun 0x0
Jan 19 02:13:08 r15x-laptop console-kit-daemon[749]: WARNING: Couldn't read /proc/739/environ: Failed to open file '/proc/739/environ': No such file or directory
Jan 19 02:13:08 r15x-laptop gnome-session[1380]: devkit-power-gobject-WARNING: Couldn't enumerate devices: The name org.freedesktop.DeviceKit.Power was not provided by any .service files
Jan 19 02:13:08 r15x-laptop gnome-session[1380]: WARNING: Could not launch application 'metacity.desktop': Unable to start application: Failed to execute child process "metacity" (No such file or directory)
Jan 19 02:13:08 r15x-laptop gnome-session[1380]: WARNING: Could not launch application 'gnome-power-manager.desktop': Unable to start application: Failed to execute child process "gnome-power-manager" (No such file or directory)
Jan 19 02:13:09 r15x-laptop gdm-simple-greeter[1390]: devkit-power-gobject-WARNING: Couldn't enumerate devices: The name org.freedesktop.DeviceKit.Power was not provided by any .service files
Jan 19 02:13:09 r15x-laptop gdm-simple-greeter[1390]: devkit-power-gobject-WARNING: Error invoking GetAll() to get properties: The name org.freedesktop.DeviceKit.Power was not provided by any .service files
Jan 19 02:13:09 r15x-laptop gdm-simple-greeter[1390]: devkit-power-gobject-WARNING: Error invoking GetAll() to get properties: The name org.freedesktop.DeviceKit.Power was not provided by any .service files
Jan 19 02:13:11 r15x-laptop gdm-simple-greeter[1390]: devkit-power-gobject-WARNING: Couldn't enumerate devices: The name org.freedesktop.DeviceKit.Power was not provided by any .service files
Jan 19 02:13:11 r15x-laptop gdm-simple-greeter[1390]: devkit-power-gobject-WARNING: Error invoking GetAll() to get properties: The name org.freedesktop.DeviceKit.Power was not provided by any .service files
Jan 19 02:13:11 r15x-laptop gdm-simple-greeter[1390]: devkit-power-gobject-WARNING: Couldn't enumerate devices: The name org.freedesktop.DeviceKit.Power was not provided by any .service files
Jan 19 02:13:11 r15x-laptop gdm-simple-greeter[1390]: devkit-power-gobject-WARNING: Error invoking GetAll() to get properties: The name org.freedesktop.DeviceKit.Power was not provided by any .service files
Jan 19 02:13:21 r15x-laptop wpa_supplicant[843]: CTRL-EVENT-SCAN-RESULTS 
Jan 19 02:13:21 r15x-laptop wpa_supplicant[843]: WPS-AP-AVAILABLE 
Jan 19 02:13:22 r15x-laptop gdm-simple-greeter[1390]: devkit-power-gobject-WARNING: Couldn't enumerate devices: The name org.freedesktop.DeviceKit.Power was not provided by any .service files
Jan 19 02:13:22 r15x-laptop gdm-simple-greeter[1390]: devkit-power-gobject-WARNING: Error invoking GetAll() to get properties: The name org.freedesktop.DeviceKit.Power was not provided by any .service files
Jan 19 02:13:42 r15x-laptop NetworkManager: <info>  Activation (wlan0) starting connection 'Auto dlink'
Jan 19 02:13:42 r15x-laptop NetworkManager: <info>  (wlan0): device state change: 3 -> 4 (reason 0)
Jan 19 02:13:42 r15x-laptop NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Jan 19 02:13:42 r15x-laptop NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Jan 19 02:13:42 r15x-laptop NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Jan 19 02:13:42 r15x-laptop NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Jan 19 02:13:42 r15x-laptop NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Jan 19 02:13:42 r15x-laptop NetworkManager: <info>  (wlan0): device state change: 4 -> 5 (reason 0)
Jan 19 02:13:42 r15x-laptop NetworkManager: <info>  Activation (wlan0/wireless): connection 'Auto dlink' requires no security.  No secrets needed.
Jan 19 02:13:42 r15x-laptop NetworkManager: <info>  Config: added 'ssid' value 'dlink'
Jan 19 02:13:42 r15x-laptop NetworkManager: <info>  Config: added 'scan_ssid' value '1'
Jan 19 02:13:42 r15x-laptop NetworkManager: <info>  Config: added 'key_mgmt' value 'NONE'
Jan 19 02:13:42 r15x-laptop NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Jan 19 02:13:42 r15x-laptop NetworkManager: <info>  Config: set interface ap_scan to 1
Jan 19 02:13:42 r15x-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  inactive -> scanning
Jan 19 02:13:44 r15x-laptop wpa_supplicant[843]: CTRL-EVENT-SCAN-RESULTS 
Jan 19 02:13:44 r15x-laptop wpa_supplicant[843]: WPS-AP-AVAILABLE 
Jan 19 02:13:44 r15x-laptop wpa_supplicant[843]: Trying to associate with 00:22:b0:b9:cd:95 (SSID='dlink' freq=2462 MHz)
Jan 19 02:13:44 r15x-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  scanning -> associating
Jan 19 02:13:44 r15x-laptop kernel: [   62.068160] wlan0: authenticate with AP 00:22:b0:b9:cd:95
Jan 19 02:13:44 r15x-laptop kernel: [   62.073784] wlan0: authenticated
Jan 19 02:13:44 r15x-laptop kernel: [   62.073797] wlan0: associate with AP 00:22:b0:b9:cd:95
Jan 19 02:13:44 r15x-laptop wpa_supplicant[843]: Associated with 00:22:b0:b9:cd:95
Jan 19 02:13:44 r15x-laptop kernel: [   62.077751] wlan0: RX AssocResp from 00:22:b0:b9:cd:95 (capab=0x421 status=0 aid=4)
Jan 19 02:13:44 r15x-laptop kernel: [   62.077765] wlan0: associated
Jan 19 02:13:44 r15x-laptop kernel: [   62.079066] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
Jan 19 02:13:44 r15x-laptop wpa_supplicant[843]: CTRL-EVENT-CONNECTED - Connection to 00:22:b0:b9:cd:95 completed (auth) [id=0 id_str=]
Jan 19 02:13:44 r15x-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  associating -> associated
Jan 19 02:13:44 r15x-laptop NetworkManager: <info>  (wlan0): supplicant connection state:  associated -> completed
Jan 19 02:13:44 r15x-laptop NetworkManager: <info>  Activation (wlan0/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to wireless network 'dlink'.
Jan 19 02:13:44 r15x-laptop NetworkManager: <info>  Activation (wlan0) Stage 3 of 5 (IP Configure Start) scheduled.
Jan 19 02:13:44 r15x-laptop NetworkManager: <info>  Activation (wlan0) Stage 3 of 5 (IP Configure Start) started...
Jan 19 02:13:44 r15x-laptop NetworkManager: <info>  (wlan0): device state change: 5 -> 7 (reason 0)
Jan 19 02:13:44 r15x-laptop NetworkManager: <info>  Activation (wlan0) Beginning DHCP transaction (timeout in 45 seconds)
Jan 19 02:13:44 r15x-laptop NetworkManager: <info>  dhclient started with pid 1547
Jan 19 02:13:44 r15x-laptop NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP6 Configure Get) scheduled...
Jan 19 02:13:44 r15x-laptop NetworkManager: <info>  Activation (wlan0) Stage 3 of 5 (IP Configure Start) complete.
Jan 19 02:13:44 r15x-laptop NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP6 Configure Get) started...
Jan 19 02:13:44 r15x-laptop NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP6 Configure Get) complete.
Jan 19 02:13:44 r15x-laptop dhclient: Internet Systems Consortium DHCP Client V3.1.2
Jan 19 02:13:44 r15x-laptop dhclient: Copyright 2004-2008 Internet Systems Consortium.
Jan 19 02:13:44 r15x-laptop dhclient: All rights reserved.
Jan 19 02:13:44 r15x-laptop dhclient: For info, please visit http://www.isc.org/sw/dhcp/
Jan 19 02:13:44 r15x-laptop dhclient: 
Jan 19 02:13:44 r15x-laptop NetworkManager: <info>  DHCP: device wlan0 state changed (null) -> preinit
Jan 19 02:13:44 r15x-laptop dhclient: Listening on LPF/wlan0/00:25:d3:d6:c0:39
Jan 19 02:13:44 r15x-laptop dhclient: Sending on   LPF/wlan0/00:25:d3:d6:c0:39
Jan 19 02:13:44 r15x-laptop dhclient: Sending on   Socket/fallback
Jan 19 02:13:45 r15x-laptop avahi-daemon[740]: Registering new address record for fe80::225:d3ff:fed6:c039 on wlan0.*.
Jan 19 02:13:46 r15x-laptop dhclient: DHCPREQUEST of 192.168.0.105 on wlan0 to 255.255.255.255 port 67
Jan 19 02:13:46 r15x-laptop dhclient: DHCPACK of 192.168.0.105 from 192.168.0.1
Jan 19 02:13:46 r15x-laptop dhclient: bound to 192.168.0.105 -- renewal in 4799 seconds.
Jan 19 02:13:46 r15x-laptop NetworkManager: <info>  DHCP: device wlan0 state changed preinit -> reboot
Jan 19 02:13:46 r15x-laptop NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP4 Configure Get) scheduled...
Jan 19 02:13:46 r15x-laptop NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP4 Configure Get) started...
Jan 19 02:13:46 r15x-laptop NetworkManager: <info>    address 192.168.0.105
Jan 19 02:13:46 r15x-laptop NetworkManager: <info>    prefix 24 (255.255.255.0)
Jan 19 02:13:46 r15x-laptop NetworkManager: <info>    gateway 192.168.0.1
Jan 19 02:13:46 r15x-laptop NetworkManager: <info>    nameserver '192.168.0.1'
Jan 19 02:13:46 r15x-laptop NetworkManager: <info>    domain name 'hsd1.wa.comcast.net.'
Jan 19 02:13:46 r15x-laptop NetworkManager: <info>  Activation (wlan0) Stage 5 of 5 (IP Configure Commit) scheduled...
Jan 19 02:13:46 r15x-laptop NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP4 Configure Get) complete.
Jan 19 02:13:46 r15x-laptop NetworkManager: <info>  Activation (wlan0) Stage 5 of 5 (IP Configure Commit) started...
Jan 19 02:13:46 r15x-laptop avahi-daemon[740]: Joining mDNS multicast group on interface wlan0.IPv4 with address 192.168.0.105.
Jan 19 02:13:46 r15x-laptop avahi-daemon[740]: New relevant interface wlan0.IPv4 for mDNS.
Jan 19 02:13:46 r15x-laptop avahi-daemon[740]: Registering new address record for 192.168.0.105 on wlan0.IPv4.
Jan 19 02:13:47 r15x-laptop NetworkManager: <info>  (wlan0): device state change: 7 -> 8 (reason 0)
Jan 19 02:13:47 r15x-laptop NetworkManager: <info>  Policy set 'Auto dlink' (wlan0) as default for routing and DNS.
Jan 19 02:13:47 r15x-laptop NetworkManager: <info>  Activation (wlan0) successful, device activated.
Jan 19 02:13:47 r15x-laptop NetworkManager: <info>  Activation (wlan0) Stage 5 of 5 (IP Configure Commit) complete.
Jan 19 02:13:48 r15x-laptop ntpdate[1601]: adjust time server 91.189.94.4 offset -0.369443 sec
Jan 19 02:13:51 r15x-laptop wpa_supplicant[843]: CTRL-EVENT-SCAN-RESULTS 
Jan 19 02:13:54 r15x-laptop kernel: [   72.156051] wlan0: no IPv6 routers present
Jan 19 02:14:31 r15x-laptop wpa_supplicant[843]: CTRL-EVENT-SCAN-RESULTS 
Jan 19 02:15:31 r15x-laptop wpa_supplicant[843]: CTRL-EVENT-SCAN-RESULTS 
Jan 19 02:16:51 r15x-laptop wpa_supplicant[843]: CTRL-EVENT-SCAN-RESULTS 
Jan 19 02:17:01 r15x-laptop CRON[1674]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Jan 19 02:18:31 r15x-laptop wpa_supplicant[843]: CTRL-EVENT-SCAN-RESULTS 

```

---

