---
title: "ata3 a duplicate attempt to connect to hard drive"
date: 2014-01-01
forum: Hardware
---

### Post by WanderingAlbatross on 2014-01-01
Dear friends,

I have just installed on a Satellite P775-S7320.  The boot up time is unbelievably slow.  I spent a lot of time researching the following from dmesg:

[PHP][   10.976109] ata3: link is slow to respond, please be patient (ready=0)
[   15.400111] ata3: COMRESET failed (errno=-16)
[/PHP]

This lead to many complaints about hard drive connectors or failed hard drives.  I even upgraded to 3.11 kernel to make sure it wasn't the problem.  None of that worked.  Then I realized these lines in dmesg are showing the computer is looking for two hard drives, and there is only one.:

[PHP][    5.005223] ata1: SATA max UDMA/133 abar m2048@0xf7f06000 port 0xf7f06100 irq 40
[    5.005225] ata2: DUMMY
[    5.005228] ata3: SATA max UDMA/133 abar m2048@0xf7f06000 port 0xf7f06200 irq 40
[    5.005230] ata4: DUMMY
[    5.005231] ata5: DUMMY
[    5.005233] ata6: DUMMY
[/PHP]

It seems to be trying to reconnect to the same hard drive twice.  There is no way in Bios to disable this.  The computer will stall on boot up for anywhere between 250 seconds and 850 seconds, until it decides to give up and continue booting.  Here is the dmesg on that:
[PHP][  230.680164] ata3: link is slow to respond, please be patient (ready=0)
[  260.360162] ata3: COMRESET failed (errno=-16)
[  260.360176] ata3: hard resetting link
[  265.384159] ata3: COMRESET failed (errno=-16)
[  265.384174] ata3: reset failed, giving up
[  265.384186] ata3: EH complete[/PHP]

I wonder if anyone knows how to blacklist this ata3 in the kernel modules.  That would correct the whole thing because it runs fine once the machine boots.  Or another possibility would be to reduce the time it looks for additional hard drives.  Does anyone have an idea?  I will post the whole dmesg below if you really want to see all it:
[PHP][    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 3.2.0-57-generic (buildd@lamiak) (gcc version 4.6.3 (Ubuntu/Linaro 4.6.3-1ubuntu5) ) #87-Ubuntu SMP Tue Nov 12 21:38:12 UTC 2013 (Ubuntu 3.2.0-57.87-generic 3.2.52)
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
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009d800 (usable)
[    0.000000]  BIOS-e820: 000000000009d800 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 0000000020000000 (usable)
[    0.000000]  BIOS-e820: 0000000020000000 - 0000000020200000 (reserved)
[    0.000000]  BIOS-e820: 0000000020200000 - 0000000040000000 (usable)
[    0.000000]  BIOS-e820: 0000000040000000 - 0000000040200000 (reserved)
[    0.000000]  BIOS-e820: 0000000040200000 - 00000000ca53d000 (usable)
[    0.000000]  BIOS-e820: 00000000ca53d000 - 00000000ca580000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000ca580000 - 00000000ca6e7000 (usable)
[    0.000000]  BIOS-e820: 00000000ca6e7000 - 00000000ca967000 (reserved)
[    0.000000]  BIOS-e820: 00000000ca967000 - 00000000cabd7000 (usable)
[    0.000000]  BIOS-e820: 00000000cabd7000 - 00000000cad68000 (reserved)
[    0.000000]  BIOS-e820: 00000000cad68000 - 00000000cafe8000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000cafe8000 - 00000000cb000000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000cb800000 - 00000000cfa00000 (reserved)
[    0.000000]  BIOS-e820: 00000000f8000000 - 00000000fc000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed00000 - 00000000fed04000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed1c000 - 00000000fed20000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000ff000000 - 0000000100000000 (reserved)
[    0.000000]  BIOS-e820: 0000000100000000 - 00000001afe00000 (usable)
[    0.000000] Notice: NX (Execute Disable) protection cannot be enabled in hardware: non-PAE kernel!
[    0.000000] NX (Execute Disable) protection: approximated by x86 segment limits
[    0.000000] SMBIOS 2.6 present.
[    0.000000] DMI: TOSHIBA Satellite P775/PHRAA, BIOS 1.50 07/21/2011                                                                                                                                                           
[    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)                                                                                                                                    
[    0.000000] e820 remove range: 00000000000a0000 - 0000000000100000 (usable)                                                                                                                                                   
[    0.000000] last_pfn = 0xcabd7 max_arch_pfn = 0x100000                                                                                                                                                                        
[    0.000000] MTRR default type: uncachable                                                                                                                                                                                     
[    0.000000] MTRR fixed ranges enabled:                                                                                                                                                                                        
[    0.000000]   00000-9FFFF write-back                                                                                                                                                                                          
[    0.000000]   A0000-BFFFF uncachable                                                                                                                                                                                          
[    0.000000]   C0000-CFFFF write-protect                                                                                                                                                                                       
[    0.000000]   D0000-E7FFF uncachable                                                                                                                                                                                          
[    0.000000]   E8000-FFFFF write-protect                                                                                                                                                                                       
[    0.000000] MTRR variable ranges enabled:                                                                                                                                                                                     
[    0.000000]   0 base 000000000 mask E00000000 write-back
[    0.000000]   1 base 0CB800000 mask FFF800000 uncachable
[    0.000000]   2 base 0CC000000 mask FFC000000 uncachable
[    0.000000]   3 base 0D0000000 mask FF0000000 uncachable
[    0.000000]   4 base 0E0000000 mask FE0000000 uncachable
[    0.000000]   5 base 1AFE00000 mask FFFE00000 uncachable
[    0.000000]   6 base 1B0000000 mask FF0000000 uncachable
[    0.000000]   7 base 1C0000000 mask FC0000000 uncachable
[    0.000000]   8 disabled
[    0.000000]   9 disabled
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] original variable MTRRs
[    0.000000] reg 0, base: 0GB, range: 8GB, type WB
[    0.000000] reg 1, base: 3256MB, range: 8MB, type UC
[    0.000000] reg 2, base: 3264MB, range: 64MB, type UC
[    0.000000] reg 3, base: 3328MB, range: 256MB, type UC
[    0.000000] reg 4, base: 3584MB, range: 512MB, type UC
[    0.000000] reg 5, base: 6910MB, range: 2MB, type UC
[    0.000000] reg 6, base: 6912MB, range: 256MB, type UC
[    0.000000] reg 7, base: 7GB, range: 1GB, type UC
[    0.000000] total RAM covered: 6070M
[    0.000000] Found optimal setting for mtrr clean up
[    0.000000]  gran_size: 64K  chunk_size: 16M         num_reg: 9      lose cover RAM: 0G
[    0.000000] New variable MTRRs
[    0.000000] reg 0, base: 0GB, range: 2GB, type WB
[    0.000000] reg 1, base: 2GB, range: 1GB, type WB
[    0.000000] reg 2, base: 3GB, range: 128MB, type WB
[    0.000000] reg 3, base: 3200MB, range: 64MB, type WB
[    0.000000] reg 4, base: 3256MB, range: 8MB, type UC
[    0.000000] reg 5, base: 4GB, range: 2GB, type WB
[    0.000000] reg 6, base: 6GB, range: 512MB, type WB
[    0.000000] reg 7, base: 6656MB, range: 256MB, type WB
[    0.000000] reg 8, base: 6910MB, range: 2MB, type UC
[    0.000000] e820 update range: 00000000cb800000 - 0000000100000000 (usable) ==> (reserved)
[    0.000000] found SMP MP-table at [c00fcd70] fcd70
[    0.000000] initial memory mapped : 0 - 01c00000
[    0.000000] Base memory trampoline at [c0099000] 99000 size 16384
[    0.000000] reserving inaccessible SNB gfx pages
[    0.000000] init_memory_mapping: 0000000000000000-00000000377fe000
[    0.000000]  0000000000 - 0000400000 page 4k
[    0.000000]  0000400000 - 0037400000 page 2M
[    0.000000]  0037400000 - 00377fe000 page 4k
[    0.000000] kernel direct mapping tables up to 377fe000 @ 1bf8000-1c00000
[    0.000000] RAMDISK: 35a3e000 - 36d17000
[    0.000000] ACPI: RSDP 000f0430 00024 (v02 TOSCPL)
[    0.000000] ACPI: XSDT cafed070 0005C (v01 TOSCPL TOSCPL00 01072009 AMI  00010013)
[    0.000000] ACPI: FACP caffcbe0 000F4 (v04 TOSCPL TOSCPL00 01072009 AMI  00010013)
[    0.000000] ACPI: DSDT cafed158 0FA88 (v02 TOSCPL TOSCPL00 0000003A INTL 20051117)
[    0.000000] ACPI: FACS cafdff80 00040
[    0.000000] ACPI: APIC caffccd8 00092 (v03 TOSCPL TOSCPL00 01072009 AMI  00010013)
[    0.000000] ACPI: MCFG caffcd70 0003C (v01 TOSCPL TOSCPL00 01072009 MSFT 00000097)
[    0.000000] ACPI: SLIC caffcdb0 00176 (v01 TOSCPL TOSCPL00 01072009 AMI  00010013)
[    0.000000] ACPI: HPET caffcf28 00038 (v01 TOSCPL TOSCPL00 01072009 AMI. 00000004)
[    0.000000] ACPI: SSDT caffcf60 0094E (v01  PmRef  Cpu0Ist 00003000 INTL 20051117)
[    0.000000] ACPI: SSDT caffd8b0 00996 (v01  PmRef    CpuPm 00003000 INTL 20051117)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] 2355MB HIGHMEM available.
[    0.000000] 887MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 377fe000
[    0.000000]   low ram: 0 - 377fe000
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x000377fe
[    0.000000]   HighMem  0x000377fe -> 0x000cabd7
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[6] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x0000009d
[    0.000000]     0: 0x00000100 -> 0x00020000
[    0.000000]     0: 0x00020200 -> 0x00040000
[    0.000000]     0: 0x00040200 -> 0x000ca53d
[    0.000000]     0: 0x000ca580 -> 0x000ca6e7
[    0.000000]     0: 0x000ca967 -> 0x000cabd7
[    0.000000] On node 0 totalpages: 828577
[    0.000000] free_area_init_node: node 0, pgdat c182bd80, node_mem_map f40e6200
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3949 pages, LIFO batch:0
[    0.000000]   Normal zone: 1744 pages used for memmap
[    0.000000]   Normal zone: 220974 pages, LIFO batch:31
[    0.000000]   HighMem zone: 4712 pages used for memmap
[    0.000000]   HighMem zone: 597166 pages, LIFO batch:31
[    0.000000] Using APIC driver default
[    0.000000] ACPI: PM-Timer IO Port: 0x408
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x02] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x04] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x06] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x05] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x06] lapic_id[0x03] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x07] lapic_id[0x05] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x08] lapic_id[0x07] enabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0xff] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x8086a701 base: 0xfed00000
[    0.000000] SMP: Allowing 8 CPUs, 0 hotplug CPUs
[    0.000000] nr_irqs_gsi: 40
[    0.000000] PM: Registered nosave memory: 000000000009d000 - 000000000009e000
[    0.000000] PM: Registered nosave memory: 000000000009e000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
[    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
[    0.000000] PM: Registered nosave memory: 0000000020000000 - 0000000020200000
[    0.000000] Allocating PCI resources starting at cfa00000 (gap: cfa00000:28600000)
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] setup_percpu: NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:8 nr_node_ids:1
[    0.000000] PERCPU: Embedded 13 pages/cpu @f7783000 s31616 r0 d21632 u53248
[    0.000000] pcpu-alloc: s31616 r0 d21632 u53248 alloc=13*4096
[    0.000000] pcpu-alloc: [0] 0 [0] 1 [0] 2 [0] 3 [0] 4 [0] 5 [0] 6 [0] 7 
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 822089
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.2.0-57-generic root=UUID=159c5b59-aea9-40db-ac4d-2fe852ff9803 ro quiet splash vt.handoff=7
[    0.000000] PID hash table entries: 4096 (order: 2, 16384 bytes)
[    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.000000] Initializing CPU#0
[    0.000000] xsave/xrstor: enabled xstate_bv 0x7, cntxt size 0x340
[    0.000000] allocated 13286512 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] Initializing HighMem for node 0 (000377fe:000cabd7)
[    0.000000] Memory: 3244184k/3321692k available (5639k kernel code, 70124k reserved, 2778k data, 716k init, 2407512k highmem)
[    0.000000] virtual kernel memory layout:
[    0.000000]     fixmap  : 0xfff16000 - 0xfffff000   ( 932 kB)
[    0.000000]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[    0.000000]     vmalloc : 0xf7ffe000 - 0xff7fe000   ( 120 MB)
[    0.000000]     lowmem  : 0xc0000000 - 0xf77fe000   ( 887 MB)
[    0.000000]       .init : 0xc1839000 - 0xc18ec000   ( 716 kB)
[    0.000000]       .data : 0xc1581c84 - 0xc18384c0   (2778 kB)
[    0.000000]       .text : 0xc1000000 - 0xc1581c84   (5639 kB)
[    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.000000] SLUB: Genslabs=15, HWalign=64, Order=0-3, MinObjects=0, CPUs=8, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000]  RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000] NR_IRQS:2304 nr_irqs:744 16
[    0.000000] CPU 0 irqstacks, hard=f700a000 soft=f700c000
[    0.000000] Extended CMOS year: 2000
[    0.000000] vt handoff: transparent VT on vt#7
[    0.000000] Console: colour dummy device 80x25
[    0.000000] console [tty0] enabled
[    0.000000] hpet clockevent registered
[    0.000000] Fast TSC calibration using PIT
[    0.004000] Detected 2195.182 MHz processor.
[    0.000001] Calibrating delay loop (skipped), value calculated using timer frequency.. 4390.36 BogoMIPS (lpj=8780728)
[    0.000005] pid_max: default: 32768 minimum: 301
[    0.000026] Security Framework initialized
[    0.000039] AppArmor: AppArmor initialized
[    0.000041] Yama: becoming mindful.
[    0.000085] Mount-cache hash table entries: 512
[    0.000195] Initializing cgroup subsys cpuacct
[    0.000200] Initializing cgroup subsys memory
[    0.000207] Initializing cgroup subsys devices
[    0.000209] Initializing cgroup subsys freezer
[    0.000211] Initializing cgroup subsys blkio
[    0.000216] Initializing cgroup subsys perf_event
[    0.000240] CPU: Physical Processor ID: 0
[    0.000241] CPU: Processor Core ID: 0
[    0.000246] ENERGY_PERF_BIAS: Set to 'normal', was 'performance'
[    0.000247] ENERGY_PERF_BIAS: View and update with x86_energy_perf_policy(8)
[    0.000250] mce: CPU supports 9 MCE banks
[    0.000264] CPU0: Thermal monitoring enabled (TM1)
[    0.000271] using mwait in idle threads.
[    0.002513] ACPI: Core revision 20110623
[    0.002516] TOSHIBA Satellite detected - force copy of DSDT to local memory
[    0.002607] ACPI: Forced DSDT copy: length 0x0FA88 copied locally, original unmapped
[    0.013917] ftrace: allocating 25522 entries in 50 pages
[    0.023677] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.024098] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.063742] CPU0: Intel(R) Core(TM) i7-2670QM CPU @ 2.20GHz stepping 07
[    0.168181] Performance Events: PEBS fmt1+, SandyBridge events, Intel PMU driver.
[    0.168186] PEBS disabled due to CPU errata.
[    0.168188] ... version:                3
[    0.168190] ... bit width:              48
[    0.168191] ... generic registers:      4
[    0.168192] ... value mask:             0000ffffffffffff
[    0.168194] ... max period:             000000007fffffff
[    0.168196] ... fixed-purpose events:   3
[    0.168197] ... event mask:             000000070000000f
[    0.168346] NMI watchdog enabled, takes one hw-pmu counter.
[    0.168417] CPU 1 irqstacks, hard=f7168000 soft=f716a000
[    0.168419] Booting Node   0, Processors  #1
[    0.168421] smpboot cpu 1: start_ip = 99000
[    0.180816] Initializing CPU#1
[    0.276128] TSC synchronization [CPU#0 -> CPU#1]:
[    0.276130] Measured 4402542 cycles TSC warp between CPUs, turning off TSC clock.
[    0.008000] Marking TSC unstable due to check_tsc_sync_source failed
[    0.156029] NMI watchdog enabled, takes one hw-pmu counter.
[    0.156101] CPU 2 irqstacks, hard=f7176000 soft=f7178000
[    0.156103]  #2
[    0.156105] smpboot cpu 2: start_ip = 99000
[    0.008000] Initializing CPU#2
[    0.244153] NMI watchdog enabled, takes one hw-pmu counter.
[    0.244231] CPU 3 irqstacks, hard=f71ac000 soft=f71ae000
[    0.244232]  #3
[    0.244234] smpboot cpu 3: start_ip = 99000
[    0.008000] Initializing CPU#3
[    0.332102] NMI watchdog enabled, takes one hw-pmu counter.
[    0.332178] CPU 4 irqstacks, hard=f71c6000 soft=f71c8000
[    0.332180]  #4
[    0.332181] smpboot cpu 4: start_ip = 99000
[    0.008000] Initializing CPU#4
[    0.420165] NMI watchdog enabled, takes one hw-pmu counter.
[    0.420247] CPU 5 irqstacks, hard=f71e4000 soft=f71e6000
[    0.420249]  #5
[    0.420250] smpboot cpu 5: start_ip = 99000
[    0.008000] Initializing CPU#5
[    0.508119] NMI watchdog enabled, takes one hw-pmu counter.
[    0.508194] CPU 6 irqstacks, hard=f71f2000 soft=f71f4000
[    0.508196]  #6
[    0.508197] smpboot cpu 6: start_ip = 99000
[    0.008000] Initializing CPU#6
[    0.596165] NMI watchdog enabled, takes one hw-pmu counter.
[    0.596240] CPU 7 irqstacks, hard=f7208000 soft=f720a000
[    0.596242]  #7 Ok.
[    0.596243] smpboot cpu 7: start_ip = 99000
[    0.008000] Initializing CPU#7
[    0.684111] NMI watchdog enabled, takes one hw-pmu counter.
[    0.684138] Brought up 8 CPUs
[    0.684140] Total of 8 processors activated (35119.21 BogoMIPS).
[    0.688211] devtmpfs: initialized
[    0.688211] EVM: security.selinux
[    0.688211] EVM: security.SMACK64
[    0.688211] EVM: security.capability
[    0.688241] PM: Registering ACPI NVS region at ca53d000 (274432 bytes)
[    0.688241] PM: Registering ACPI NVS region at cad68000 (2621440 bytes)
[    0.689011] print_constraints: dummy: 
[    0.689042] RTC time:  8:27:31, date: 01/01/14
[    0.689078] NET: Registered protocol family 16
[    0.689521] Trying to unpack rootfs image as initramfs...
[    0.689174] EISA bus registered
[    0.689195] ACPI FADT declares the system doesn't support PCIe ASPM, so disable it
[    0.689197] ACPI: bus type pci registered
[    0.689255] PCI: MMCONFIG for domain 0000 [bus 00-3f] at [mem 0xf8000000-0xfbffffff] (base 0xf8000000)
[    0.689259] PCI: MMCONFIG at [mem 0xf8000000-0xfbffffff] reserved in E820
[    0.689261] PCI: Using MMCONFIG for extended config space
[    0.689262] PCI: Using configuration type 1 for base access
[    0.690137] bio: create slab <bio-0> at 0
[    0.690137] ACPI: Added _OSI(Module Device)
[    0.690137] ACPI: Added _OSI(Processor Device)
[    0.690137] ACPI: Added _OSI(3.0 _SCP Extensions)
[    0.690137] ACPI: Added _OSI(Processor Aggregator Device)
[    0.693467] ACPI: EC: Look up EC in DSDT
[    0.705584] ACPI: Executed 1 blocks of module-level executable AML code
[    0.744087] [Firmware Bug]: ACPI: BIOS _OSI(Linux) query ignored
[    0.744493] ACPI: SSDT cad51718 0067C (v01  PmRef  Cpu0Cst 00003001 INTL 20051117)
[    0.745053] ACPI: Dynamic OEM Table Load:
[    0.745056] ACPI: SSDT   (null) 0067C (v01  PmRef  Cpu0Cst 00003001 INTL 20051117)
[    0.776305] ACPI: SSDT cad52a98 00303 (v01  PmRef    ApIst 00003000 INTL 20051117)
[    0.776904] ACPI: Dynamic OEM Table Load:
[    0.776907] ACPI: SSDT   (null) 00303 (v01  PmRef    ApIst 00003000 INTL 20051117)
[    0.800147] ACPI: SSDT cad50d98 00119 (v01  PmRef    ApCst 00003000 INTL 20051117)
[    0.800700] ACPI: Dynamic OEM Table Load:
[    0.800703] ACPI: SSDT   (null) 00119 (v01  PmRef    ApCst 00003000 INTL 20051117)
[    1.083830] Freeing initrd memory: 19300k freed
[    4.080300] ACPI: Interpreter enabled
[    4.080322] ACPI: (supports S0 S3 S4 S5)
[    4.080390] ACPI: Using IOAPIC for interrupt routing
[    4.141954] ACPI: EC: GPE = 0x17, I/O: command/status = 0x66, data = 0x62
[    4.142737] ACPI: ACPI Dock Station Driver: 1 docks/bays found
[    4.142739] HEST: Table not found.
[    4.142744] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[    4.143023] \_SB_.PCI0:_OSC invalid UUID
[    4.143024] _OSC request data:1 8 0 
[    4.143029] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-3e])
[    4.143493] pci_root PNP0A08:00: host bridge window [io  0x0000-0x0cf7]
[    4.143496] pci_root PNP0A08:00: host bridge window [io  0x0d00-0xffff]
[    4.143498] pci_root PNP0A08:00: host bridge window [mem 0x000a0000-0x000bffff]
[    4.143501] pci_root PNP0A08:00: host bridge window [mem 0x000d0000-0x000d3fff]
[    4.143503] pci_root PNP0A08:00: host bridge window [mem 0x000d4000-0x000d7fff]
[    4.143505] pci_root PNP0A08:00: host bridge window [mem 0x000d8000-0x000dbfff]
[    4.143508] pci_root PNP0A08:00: host bridge window [mem 0x000dc000-0x000dffff]
[    4.143510] pci_root PNP0A08:00: host bridge window [mem 0x000e0000-0x000e3fff]
[    4.143512] pci_root PNP0A08:00: host bridge window [mem 0x000e4000-0x000e7fff]
[    4.143515] pci_root PNP0A08:00: host bridge window [mem 0xcfa00000-0xfeafffff]
[    4.143517] pci_root PNP0A08:00: host bridge window [mem 0xfed40000-0xfed44fff]
[    4.143531] pci 0000:00:00.0: [8086:0104] type 0 class 0x000600
[    4.143573] pci 0000:00:02.0: [8086:0116] type 0 class 0x000300
[    4.143585] pci 0000:00:02.0: reg 10: [mem 0xf7800000-0xf7bfffff 64bit]
[    4.143593] pci 0000:00:02.0: reg 18: [mem 0xe0000000-0xefffffff 64bit pref]
[    4.143598] pci 0000:00:02.0: reg 20: [io  0xf000-0xf03f]
[    4.143659] pci 0000:00:16.0: [8086:1c3a] type 0 class 0x000780
[    4.143685] pci 0000:00:16.0: reg 10: [mem 0xf7f0a000-0xf7f0a00f 64bit]
[    4.143767] pci 0000:00:16.0: PME# supported from D0 D3hot D3cold
[    4.143773] pci 0000:00:16.0: PME# disabled
[    4.143810] pci 0000:00:1a.0: [8086:1c2d] type 0 class 0x000c03
[    4.143833] pci 0000:00:1a.0: reg 10: [mem 0xf7f08000-0xf7f083ff]
[    4.143931] pci 0000:00:1a.0: PME# supported from D0 D3hot D3cold
[    4.143936] pci 0000:00:1a.0: PME# disabled
[    4.143964] pci 0000:00:1b.0: [8086:1c20] type 0 class 0x000403
[    4.143982] pci 0000:00:1b.0: reg 10: [mem 0xf7f00000-0xf7f03fff 64bit]
[    4.144058] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    4.144062] pci 0000:00:1b.0: PME# disabled
[    4.144087] pci 0000:00:1c.0: [8086:1c10] type 1 class 0x000604
[    4.144175] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    4.144180] pci 0000:00:1c.0: PME# disabled
[    4.144206] pci 0000:00:1c.1: [8086:1c12] type 1 class 0x000604
[    4.144301] pci 0000:00:1c.1: PME# supported from D0 D3hot D3cold
[    4.144306] pci 0000:00:1c.1: PME# disabled
[    4.144334] pci 0000:00:1c.3: [8086:1c16] type 1 class 0x000604
[    4.144423] pci 0000:00:1c.3: PME# supported from D0 D3hot D3cold
[    4.144428] pci 0000:00:1c.3: PME# disabled
[    4.144456] pci 0000:00:1c.5: [8086:1c1a] type 1 class 0x000604
[    4.144544] pci 0000:00:1c.5: PME# supported from D0 D3hot D3cold
[    4.144549] pci 0000:00:1c.5: PME# disabled
[    4.144582] pci 0000:00:1d.0: [8086:1c26] type 0 class 0x000c03
[    4.144606] pci 0000:00:1d.0: reg 10: [mem 0xf7f07000-0xf7f073ff]
[    4.144703] pci 0000:00:1d.0: PME# supported from D0 D3hot D3cold
[    4.144708] pci 0000:00:1d.0: PME# disabled
[    4.144734] pci 0000:00:1f.0: [8086:1c49] type 0 class 0x000601
[    4.144867] pci 0000:00:1f.2: [8086:1c03] type 0 class 0x000106
[    4.144889] pci 0000:00:1f.2: reg 10: [io  0xf0b0-0xf0b7]
[    4.144898] pci 0000:00:1f.2: reg 14: [io  0xf0a0-0xf0a3]
[    4.144907] pci 0000:00:1f.2: reg 18: [io  0xf090-0xf097]
[    4.144916] pci 0000:00:1f.2: reg 1c: [io  0xf080-0xf083]
[    4.144926] pci 0000:00:1f.2: reg 20: [io  0xf060-0xf07f]
[    4.144935] pci 0000:00:1f.2: reg 24: [mem 0xf7f06000-0xf7f067ff]
[    4.144985] pci 0000:00:1f.2: PME# supported from D3hot
[    4.144990] pci 0000:00:1f.2: PME# disabled
[    4.145011] pci 0000:00:1f.3: [8086:1c22] type 0 class 0x000c05
[    4.145028] pci 0000:00:1f.3: reg 10: [mem 0xf7f05000-0xf7f050ff 64bit]
[    4.145052] pci 0000:00:1f.3: reg 20: [io  0xf040-0xf05f]
[    4.145208] pci 0000:02:00.0: [10ec:8168] type 0 class 0x000200
[    4.145277] pci 0000:02:00.0: reg 10: [io  0xe000-0xe0ff]
[    4.145398] pci 0000:02:00.0: reg 18: [mem 0xf0004000-0xf0004fff 64bit pref]
[    4.145474] pci 0000:02:00.0: reg 20: [mem 0xf0000000-0xf0003fff 64bit pref]
[    4.145804] pci 0000:02:00.0: supports D1 D2
[    4.145806] pci 0000:02:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    4.145822] pci 0000:02:00.0: PME# disabled
[    4.152334] pci 0000:00:1c.0: PCI bridge to [bus 02-02]
[    4.152345] pci 0000:00:1c.0:   bridge window [io  0xe000-0xefff]
[    4.152367] pci 0000:00:1c.0:   bridge window [mem 0xf0000000-0xf00fffff 64bit pref]
[    4.152582] pci 0000:03:00.0: [8086:0885] type 0 class 0x000280
[    4.152747] pci 0000:03:00.0: reg 10: [mem 0xf7e00000-0xf7e01fff 64bit]
[    4.153421] pci 0000:03:00.0: PME# supported from D0 D3hot D3cold
[    4.153456] pci 0000:03:00.0: PME# disabled
[    4.160411] pci 0000:00:1c.1: PCI bridge to [bus 03-03]
[    4.160419] pci 0000:00:1c.1:   bridge window [mem 0xf7e00000-0xf7efffff]
[    4.160498] pci 0000:05:00.0: [197b:2392] type 0 class 0x000880
[    4.160525] pci 0000:05:00.0: reg 10: [mem 0xf7d03000-0xf7d030ff]
[    4.160783] pci 0000:05:00.2: [197b:2391] type 0 class 0x000805
[    4.160811] pci 0000:05:00.2: reg 10: [mem 0xf7d02000-0xf7d020ff]
[    4.161064] pci 0000:05:00.3: [197b:2393] type 0 class 0x000880
[    4.161092] pci 0000:05:00.3: reg 10: [mem 0xf7d01000-0xf7d010ff]
[    4.161342] pci 0000:05:00.4: [197b:2394] type 0 class 0x000880
[    4.161369] pci 0000:05:00.4: reg 10: [mem 0xf7d00000-0xf7d000ff]
[    4.168332] pci 0000:00:1c.3: PCI bridge to [bus 05-05]
[    4.168347] pci 0000:00:1c.3:   bridge window [mem 0xf7d00000-0xf7dfffff]
[    4.168457] pci 0000:06:00.0: [1033:0194] type 0 class 0x000c03
[    4.168486] pci 0000:06:00.0: reg 10: [mem 0xf7c00000-0xf7c01fff 64bit]
[    4.168627] pci 0000:06:00.0: PME# supported from D0 D3hot D3cold
[    4.168633] pci 0000:06:00.0: PME# disabled
[    4.176292] pci 0000:00:1c.5: PCI bridge to [bus 06-06]
[    4.176307] pci 0000:00:1c.5:   bridge window [mem 0xf7c00000-0xf7cfffff]
[    4.176365] pci_bus 0000:00: on NUMA node 0
[    4.176373] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    4.176567] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP01._PRT]
[    4.176605] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP02._PRT]
[    4.176644] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP04._PRT]
[    4.176703] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP06._PRT]
[    4.176797] \_SB_.PCI0:_OSC invalid UUID
[    4.176798] _OSC request data:1 1f 0 
[    4.176803]  pci0000:00: Requesting ACPI _OSC control (0x1d)
[    4.176835] \_SB_.PCI0:_OSC invalid UUID
[    4.176837] _OSC request data:1 0 1d 
[    4.176841]  pci0000:00: ACPI _OSC request failed (AE_ERROR), returned control mask: 0x1d
[    4.176843] ACPI _OSC control for PCIe not granted, disabling ASPM
[    4.181113] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 10 *11 12 14 15)
[    4.181166] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 *5 6 10 11 12 14 15)
[    4.181216] ACPI: PCI Interrupt Link [LNKC] (IRQs *3 4 5 6 10 11 12 14 15)
[    4.181266] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 *10 11 12 14 15)
[    4.181317] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 10 11 12 14 15) *0, disabled.
[    4.181369] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 10 11 12 14 15) *0, disabled.
[    4.181421] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 *5 6 10 11 12 14 15)
[    4.181468] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 *5 6 10 11 12 14 15)
[    4.181543] vgaarb: device added: PCI:0000:00:02.0,decodes=io+mem,owns=io+mem,locks=none
[    4.181543] vgaarb: loaded
[    4.181543] vgaarb: bridge control possible 0000:00:02.0
[    4.181543] i2c-core: driver [aat2870] using legacy suspend method
[    4.181543] i2c-core: driver [aat2870] using legacy resume method
[    4.181543] SCSI subsystem initialized
[    4.181611] libata version 3.00 loaded.
[    4.181611] usbcore: registered new interface driver usbfs
[    4.181611] usbcore: registered new interface driver hub
[    4.181611] usbcore: registered new device driver usb
[    4.181611] PCI: Using ACPI for IRQ routing
[    4.181928] PCI: pci_cache_line_size set to 64 bytes
[    4.182079] reserve RAM buffer: 000000000009d800 - 000000000009ffff 
[    4.182082] reserve RAM buffer: 00000000ca53d000 - 00000000cbffffff 
[    4.182085] reserve RAM buffer: 00000000ca6e7000 - 00000000cbffffff 
[    4.182087] reserve RAM buffer: 00000000cabd7000 - 00000000cbffffff 
[    4.182174] NetLabel: Initializing
[    4.182175] NetLabel:  domain hash size = 128
[    4.182177] NetLabel:  protocols = UNLABELED CIPSOv4
[    4.182186] NetLabel:  unlabeled traffic allowed by default
[    4.182551] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0, 0, 0, 0, 0
[    4.182551] hpet0: 8 comparators, 64-bit 14.318180 MHz counter
[    4.185274] Switching to clocksource hpet
[    4.190641] AppArmor: AppArmor Filesystem Enabled
[    4.190655] pnp: PnP ACPI init
[    4.190668] ACPI: bus type pnp registered
[    4.190914] pnp 00:00: [bus 00-3e]
[    4.190917] pnp 00:00: [io  0x0000-0x0cf7 window]
[    4.190920] pnp 00:00: [io  0x0cf8-0x0cff]
[    4.190922] pnp 00:00: [io  0x0d00-0xffff window]
[    4.190924] pnp 00:00: [mem 0x000a0000-0x000bffff window]
[    4.190926] pnp 00:00: [mem 0x000c0000-0x000c3fff window]
[    4.190929] pnp 00:00: [mem 0x000c4000-0x000c7fff window]
[    4.190931] pnp 00:00: [mem 0x000c8000-0x000cbfff window]
[    4.190933] pnp 00:00: [mem 0x000cc000-0x000cffff window]
[    4.190935] pnp 00:00: [mem 0x000d0000-0x000d3fff window]
[    4.190937] pnp 00:00: [mem 0x000d4000-0x000d7fff window]
[    4.190939] pnp 00:00: [mem 0x000d8000-0x000dbfff window]
[    4.190941] pnp 00:00: [mem 0x000dc000-0x000dffff window]
[    4.190944] pnp 00:00: [mem 0x000e0000-0x000e3fff window]
[    4.190946] pnp 00:00: [mem 0x000e4000-0x000e7fff window]
[    4.190948] pnp 00:00: [mem 0x000e8000-0x000ebfff window]
[    4.190950] pnp 00:00: [mem 0x000ec000-0x000effff window]
[    4.190952] pnp 00:00: [mem 0x000f0000-0x000fffff window]
[    4.190954] pnp 00:00: [mem 0xcfa00000-0xfeafffff window]
[    4.190956] pnp 00:00: [mem 0xfed40000-0xfed44fff window]
[    4.191017] pnp 00:00: Plug and Play ACPI device, IDs PNP0a08 PNP0a03 (active)
[    4.191030] pnp 00:01: [io  0x0000-0x001f]
[    4.191032] pnp 00:01: [io  0x0081-0x0091]
[    4.191034] pnp 00:01: [io  0x0093-0x009f]
[    4.191036] pnp 00:01: [io  0x00c0-0x00df]
[    4.191038] pnp 00:01: [dma 4]
[    4.191059] pnp 00:01: Plug and Play ACPI device, IDs PNP0200 (active)
[    4.191068] pnp 00:02: [mem 0xff000000-0xffffffff]
[    4.191090] pnp 00:02: Plug and Play ACPI device, IDs INT0800 (active)
[    4.191159] pnp 00:03: [mem 0xfed00000-0xfed003ff]
[    4.191181] pnp 00:03: Plug and Play ACPI device, IDs PNP0103 (active)
[    4.191193] pnp 00:04: [io  0x002e-0x002f]
[    4.191195] pnp 00:04: [io  0x004e-0x004f]
[    4.191197] pnp 00:04: [io  0x0061]
[    4.191198] pnp 00:04: [io  0x0063]
[    4.191200] pnp 00:04: [io  0x0065]
[    4.191205] pnp 00:04: [io  0x0067]
[    4.191207] pnp 00:04: [io  0x0070]
[    4.191209] pnp 00:04: [io  0x0080]
[    4.191210] pnp 00:04: [io  0x0092]
[    4.191212] pnp 00:04: [io  0x00b2-0x00b3]
[    4.191214] pnp 00:04: [io  0x0680-0x069f]
[    4.191216] pnp 00:04: [io  0x1000-0x100f]
[    4.191218] pnp 00:04: [io  0xffff]
[    4.191219] pnp 00:04: [io  0xffff]
[    4.191221] pnp 00:04: [io  0x0400-0x0453]
[    4.191223] pnp 00:04: [io  0x0458-0x047f]
[    4.191225] pnp 00:04: [io  0x0500-0x057f]
[    4.191227] pnp 00:04: [io  0x164e-0x164f]
[    4.191268] system 00:04: [io  0x0680-0x069f] has been reserved
[    4.191270] system 00:04: [io  0x1000-0x100f] has been reserved
[    4.191273] system 00:04: [io  0xffff] has been reserved
[    4.191275] system 00:04: [io  0xffff] has been reserved
[    4.191277] system 00:04: [io  0x0400-0x0453] has been reserved
[    4.191279] system 00:04: [io  0x0458-0x047f] has been reserved
[    4.191282] system 00:04: [io  0x0500-0x057f] has been reserved
[    4.191284] system 00:04: [io  0x164e-0x164f] has been reserved
[    4.191287] system 00:04: Plug and Play ACPI device, IDs PNP0c02 (active)
[    4.191295] pnp 00:05: [io  0x0070-0x0077]
[    4.191304] pnp 00:05: [irq 8]
[    4.191325] pnp 00:05: Plug and Play ACPI device, IDs PNP0b00 (active)
[    4.191351] pnp 00:06: [io  0x0454-0x0457]
[    4.191386] system 00:06: [io  0x0454-0x0457] has been reserved
[    4.191389] system 00:06: Plug and Play ACPI device, IDs INT3f0d PNP0c02 (active)
[    4.191411] pnp 00:07: [io  0x0010-0x001f]
[    4.191413] pnp 00:07: [io  0x0022-0x003f]
[    4.191415] pnp 00:07: [io  0x0044-0x005f]
[    4.191416] pnp 00:07: [io  0x0072-0x007f]
[    4.191418] pnp 00:07: [io  0x0080]
[    4.191420] pnp 00:07: [io  0x0084-0x0086]
[    4.191422] pnp 00:07: [io  0x0088]
[    4.191423] pnp 00:07: [io  0x008c-0x008e]
[    4.191425] pnp 00:07: [io  0x0090-0x009f]
[    4.191427] pnp 00:07: [io  0x00a2-0x00bf]
[    4.191429] pnp 00:07: [io  0x00e0-0x00ef]
[    4.191431] pnp 00:07: [io  0x04d0-0x04d1]
[    4.191433] pnp 00:07: [io  0xff2c-0xff2f]
[    4.191472] system 00:07: [io  0x04d0-0x04d1] has been reserved
[    4.191474] system 00:07: [io  0xff2c-0xff2f] has been reserved
[    4.191477] system 00:07: Plug and Play ACPI device, IDs PNP0c02 (active)
[    4.191485] pnp 00:08: [io  0x00f0-0x00ff]
[    4.191491] pnp 00:08: [irq 13]
[    4.191514] pnp 00:08: Plug and Play ACPI device, IDs PNP0c04 (active)
[    4.208119] pnp 00:09: [irq 12]
[    4.208160] pnp 00:09: Plug and Play ACPI device, IDs TOS0300 SYN0700 SYN0002 PNP0f13 (active)
[    4.208174] pnp 00:0a: [io  0x0060]
[    4.208176] pnp 00:0a: [io  0x0064]
[    4.208181] pnp 00:0a: [irq 1]
[    4.208208] pnp 00:0a: Plug and Play ACPI device, IDs PNP0303 PNP030b (active)
[    4.208449] pnp 00:0b: [mem 0xfed1c000-0xfed1ffff]
[    4.208451] pnp 00:0b: [mem 0xfed10000-0xfed17fff]
[    4.208453] pnp 00:0b: [mem 0xfed18000-0xfed18fff]
[    4.208455] pnp 00:0b: [mem 0xfed19000-0xfed19fff]
[    4.208457] pnp 00:0b: [mem 0xf8000000-0xfbffffff]
[    4.208459] pnp 00:0b: [mem 0xfed20000-0xfed3ffff]
[    4.208461] pnp 00:0b: [mem 0xfed90000-0xfed93fff]
[    4.208463] pnp 00:0b: [mem 0xfed45000-0xfed8ffff]
[    4.208465] pnp 00:0b: [mem 0xff000000-0xffffffff]
[    4.208467] pnp 00:0b: [mem 0xfee00000-0xfeefffff]
[    4.208469] pnp 00:0b: [mem 0xcfa00000-0xcfa00fff]
[    4.208534] system 00:0b: [mem 0xfed1c000-0xfed1ffff] has been reserved
[    4.208537] system 00:0b: [mem 0xfed10000-0xfed17fff] has been reserved
[    4.208540] system 00:0b: [mem 0xfed18000-0xfed18fff] has been reserved
[    4.208542] system 00:0b: [mem 0xfed19000-0xfed19fff] has been reserved
[    4.208545] system 00:0b: [mem 0xf8000000-0xfbffffff] has been reserved
[    4.208547] system 00:0b: [mem 0xfed20000-0xfed3ffff] has been reserved
[    4.208550] system 00:0b: [mem 0xfed90000-0xfed93fff] has been reserved
[    4.208552] system 00:0b: [mem 0xfed45000-0xfed8ffff] has been reserved
[    4.208555] system 00:0b: [mem 0xff000000-0xffffffff] has been reserved
[    4.208557] system 00:0b: [mem 0xfee00000-0xfeefffff] could not be reserved
[    4.208560] system 00:0b: [mem 0xcfa00000-0xcfa00fff] has been reserved
[    4.208563] system 00:0b: Plug and Play ACPI device, IDs PNP0c02 (active)
[    4.209359] pnp 00:0c: [mem 0x20000000-0x201fffff]
[    4.209362] pnp 00:0c: [mem 0x40000000-0x401fffff]
[    4.209433] system 00:0c: [mem 0x20000000-0x201fffff] has been reserved
[    4.209436] system 00:0c: [mem 0x40000000-0x401fffff] has been reserved
[    4.209439] system 00:0c: Plug and Play ACPI device, IDs PNP0c01 (active)
[    4.209567] pnp: PnP ACPI: found 13 devices
[    4.209568] ACPI: ACPI bus type pnp unregistered
[    4.209571] PnPBIOS: Disabled by ACPI PNP
[    4.246347] PCI: max bus depth: 1 pci_try_num: 2
[    4.246386] pci 0000:00:1c.0: PCI bridge to [bus 02-02]
[    4.246390] pci 0000:00:1c.0:   bridge window [io  0xe000-0xefff]
[    4.246399] pci 0000:00:1c.0:   bridge window [mem 0xf0000000-0xf00fffff 64bit pref]
[    4.246406] pci 0000:00:1c.1: PCI bridge to [bus 03-03]
[    4.246412] pci 0000:00:1c.1:   bridge window [mem 0xf7e00000-0xf7efffff]
[    4.246422] pci 0000:00:1c.3: PCI bridge to [bus 05-05]
[    4.246428] pci 0000:00:1c.3:   bridge window [mem 0xf7d00000-0xf7dfffff]
[    4.246437] pci 0000:00:1c.5: PCI bridge to [bus 06-06]
[    4.246443] pci 0000:00:1c.5:   bridge window [mem 0xf7c00000-0xf7cfffff]
[    4.246465] pci 0000:00:1c.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    4.246471] pci 0000:00:1c.0: setting latency timer to 64
[    4.246485] pci 0000:00:1c.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    4.246490] pci 0000:00:1c.1: setting latency timer to 64
[    4.246501] pci 0000:00:1c.3: PCI INT D -> GSI 19 (level, low) -> IRQ 19
[    4.246506] pci 0000:00:1c.3: setting latency timer to 64
[    4.246515] pci 0000:00:1c.5: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    4.246519] pci 0000:00:1c.5: setting latency timer to 64
[    4.246523] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
[    4.246526] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
[    4.246528] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
[    4.246530] pci_bus 0000:00: resource 7 [mem 0x000d0000-0x000d3fff]
[    4.246533] pci_bus 0000:00: resource 8 [mem 0x000d4000-0x000d7fff]
[    4.246535] pci_bus 0000:00: resource 9 [mem 0x000d8000-0x000dbfff]
[    4.246537] pci_bus 0000:00: resource 10 [mem 0x000dc000-0x000dffff]
[    4.246539] pci_bus 0000:00: resource 11 [mem 0x000e0000-0x000e3fff]
[    4.246541] pci_bus 0000:00: resource 12 [mem 0x000e4000-0x000e7fff]
[    4.246544] pci_bus 0000:00: resource 13 [mem 0xcfa00000-0xfeafffff]
[    4.246546] pci_bus 0000:00: resource 14 [mem 0xfed40000-0xfed44fff]
[    4.246548] pci_bus 0000:02: resource 0 [io  0xe000-0xefff]
[    4.246551] pci_bus 0000:02: resource 2 [mem 0xf0000000-0xf00fffff 64bit pref]
[    4.246553] pci_bus 0000:03: resource 1 [mem 0xf7e00000-0xf7efffff]
[    4.246555] pci_bus 0000:05: resource 1 [mem 0xf7d00000-0xf7dfffff]
[    4.246558] pci_bus 0000:06: resource 1 [mem 0xf7c00000-0xf7cfffff]
[    4.246584] NET: Registered protocol family 2
[    4.246628] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    4.246760] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    4.246981] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    4.247077] TCP: Hash tables configured (established 131072 bind 65536)
[    4.247079] TCP reno registered
[    4.247081] UDP hash table entries: 512 (order: 2, 16384 bytes)
[    4.247086] UDP-Lite hash table entries: 512 (order: 2, 16384 bytes)
[    4.247142] NET: Registered protocol family 1
[    4.247152] pci 0000:00:02.0: Boot video device
[    4.247163] pci 0000:00:1a.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    4.372051] pci 0000:00:1a.0: PCI INT A disabled
[    4.372111] pci 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    4.500045] pci 0000:00:1d.0: PCI INT A disabled
[    4.500138] pci 0000:06:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    4.500164] pci 0000:06:00.0: PCI INT A disabled
[    4.500168] PCI: CLS 64 bytes, default 64
[    4.500828] audit: initializing netlink socket (disabled)
[    4.500835] type=2000 audit(1388564855.496:1): initialized
[    4.523771] highmem bounce pool size: 64 pages
[    4.523775] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    4.525483] VFS: Disk quotas dquot_6.5.2
[    4.525535] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    4.525998] fuse init (API version 7.17)
[    4.526083] msgmni has been set to 1671
[    4.526447] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    4.526476] io scheduler noop registered
[    4.526478] io scheduler deadline registered
[    4.526483] io scheduler cfq registered (default)
[    4.526770] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    4.526787] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    4.526840] intel_idle: MWAIT substates: 0x21120
[    4.526842] intel_idle: v0.4 model 0x2A
[    4.526843] intel_idle: lapic_timer_reliable_states 0xffffffff
[    4.536094] ACPI: Deprecated procfs I/F for AC is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
[    4.548100] ACPI: AC Adapter [ACAD] (on-line)
[    4.548219] input: Lid Switch as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0D:00/input/input0
[    4.548241] ACPI: Lid Switch [LID0]
[    4.548280] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input1
[    4.548284] ACPI: Power Button [PWRB]
[    4.548321] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input2
[    4.548324] ACPI: Power Button [PWRF]
[    4.570251] ACPI: Deprecated procfs I/F for battery is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
[    4.570259] ACPI: Battery Slot [BAT1] (battery present)
[    4.570293] ERST: Table is not found!
[    4.570294] GHES: HEST is not enabled!
[    4.570371] isapnp: Scanning for PnP cards...
[    4.570451] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    4.728251] [Firmware Bug]: battery: (dis)charge rate invalid.
[    4.728289] ACPI: Battery Slot [BAT1] (battery present)
[    4.924352] isapnp: No Plug & Play device found
[    4.976434] Linux agpgart interface v0.103
[    4.976538] agpgart-intel 0000:00:00.0: Intel Sandybridge Chipset
[    4.976605] agpgart-intel 0000:00:00.0: detected gtt size: 2097152K total, 262144K mappable
[    4.977853] agpgart-intel 0000:00:00.0: detected 65536K stolen memory
[    4.977985] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xe0000000
[    4.979369] brd: module loaded
[    4.980088] loop: module loaded
[    4.980190] ahci 0000:00:1f.2: version 3.0
[    4.980202] ahci 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    4.980249] ahci 0000:00:1f.2: irq 40 for MSI/MSI-X
[    4.980277] ahci: SSS flag set, parallel bus scan disabled
[    4.996067] ahci 0000:00:1f.2: AHCI 0001.0300 32 slots 6 ports 6 Gbps 0x5 impl SATA mode
[    4.996077] ahci 0000:00:1f.2: flags: 64bit ncq sntf stag pm led clo pio slum part ems apst 
[    4.996089] ahci 0000:00:1f.2: setting latency timer to 64
[    5.004547] scsi0 : ahci
[    5.004626] scsi1 : ahci
[    5.004695] scsi2 : ahci
[    5.004761] scsi3 : ahci
[    5.004830] scsi4 : ahci
[    5.004899] scsi5 : ahci
[    5.005223] ata1: SATA max UDMA/133 abar m2048@0xf7f06000 port 0xf7f06100 irq 40
[    5.005225] ata2: DUMMY
[    5.005228] ata3: SATA max UDMA/133 abar m2048@0xf7f06000 port 0xf7f06200 irq 40
[    5.005230] ata4: DUMMY
[    5.005231] ata5: DUMMY
[    5.005233] ata6: DUMMY
[    5.005586] Fixed MDIO Bus: probed
[    5.005605] tun: Universal TUN/TAP device driver, 1.6
[    5.005606] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    5.005651] PPP generic driver version 2.4.2
[    5.005748] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    5.005763] ehci_hcd 0000:00:1a.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    5.005776] ehci_hcd 0000:00:1a.0: setting latency timer to 64
[    5.005780] ehci_hcd 0000:00:1a.0: EHCI Host Controller
[    5.005819] ehci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 1
[    5.005843] ehci_hcd 0000:00:1a.0: debug port 2
[    5.009718] ehci_hcd 0000:00:1a.0: cache line size of 64 is not supported
[    5.009733] ehci_hcd 0000:00:1a.0: irq 16, io mem 0xf7f08000
[    5.024033] ehci_hcd 0000:00:1a.0: USB 2.0 started, EHCI 1.00
[    5.024219] hub 1-0:1.0: USB hub found
[    5.024223] hub 1-0:1.0: 2 ports detected
[    5.024281] ehci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    5.024293] ehci_hcd 0000:00:1d.0: setting latency timer to 64
[    5.024297] ehci_hcd 0000:00:1d.0: EHCI Host Controller
[    5.024338] ehci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    5.024358] ehci_hcd 0000:00:1d.0: debug port 2
[    5.028243] ehci_hcd 0000:00:1d.0: cache line size of 64 is not supported
[    5.028258] ehci_hcd 0000:00:1d.0: irq 23, io mem 0xf7f07000
[    5.044032] ehci_hcd 0000:00:1d.0: USB 2.0 started, EHCI 1.00
[    5.044196] hub 2-0:1.0: USB hub found
[    5.044200] hub 2-0:1.0: 2 ports detected
[    5.044254] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    5.044266] uhci_hcd: USB Universal Host Controller Interface driver
[    5.044297] xhci_hcd 0000:06:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    5.044312] xhci_hcd 0000:06:00.0: setting latency timer to 64
[    5.044316] xhci_hcd 0000:06:00.0: xHCI Host Controller
[    5.044357] xhci_hcd 0000:06:00.0: new USB bus registered, assigned bus number 3
[    5.044571] xhci_hcd 0000:06:00.0: irq 41 for MSI/MSI-X
[    5.044577] xhci_hcd 0000:06:00.0: irq 42 for MSI/MSI-X
[    5.044583] xhci_hcd 0000:06:00.0: irq 43 for MSI/MSI-X
[    5.044589] xhci_hcd 0000:06:00.0: irq 44 for MSI/MSI-X
[    5.044595] xhci_hcd 0000:06:00.0: irq 45 for MSI/MSI-X
[    5.044601] xhci_hcd 0000:06:00.0: irq 46 for MSI/MSI-X
[    5.044606] xhci_hcd 0000:06:00.0: irq 47 for MSI/MSI-X
[    5.044612] xhci_hcd 0000:06:00.0: irq 48 for MSI/MSI-X
[    5.044810] xHCI xhci_add_endpoint called for root hub
[    5.044812] xHCI xhci_check_bandwidth called for root hub
[    5.044836] hub 3-0:1.0: USB hub found
[    5.044843] hub 3-0:1.0: 2 ports detected
[    5.044895] xhci_hcd 0000:06:00.0: xHCI Host Controller
[    5.044932] xhci_hcd 0000:06:00.0: new USB bus registered, assigned bus number 4
[    5.048015] xHCI xhci_add_endpoint called for root hub
[    5.048016] xHCI xhci_check_bandwidth called for root hub
[    5.048038] hub 4-0:1.0: USB hub found
[    5.048045] hub 4-0:1.0: 2 ports detected
[    5.092112] usbcore: registered new interface driver libusual
[    5.092177] i8042: PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    5.142681] serio: i8042 KBD port at 0x60,0x64 irq 1
[    5.142686] serio: i8042 AUX port at 0x60,0x64 irq 12
[    5.142794] mousedev: PS/2 mouse device common for all mice
[    5.145138] rtc_cmos 00:05: RTC can wake from S4
[    5.145248] rtc_cmos 00:05: rtc core: registered rtc_cmos as rtc0
[    5.145277] rtc0: alarms up to one month, y3k, 242 bytes nvram, hpet irqs
[    5.145339] device-mapper: uevent: version 1.0.3
[    5.145403] device-mapper: ioctl: 4.22.0-ioctl (2011-10-19) initialised: dm-devel@redhat.com
[    5.145420] EISA: Probing bus 0 at eisa.0
[    5.145422] EISA: Cannot allocate resource for mainboard
[    5.145423] Cannot allocate resource for EISA slot 1
[    5.145425] Cannot allocate resource for EISA slot 2
[    5.145427] Cannot allocate resource for EISA slot 3
[    5.145428] Cannot allocate resource for EISA slot 4
[    5.145430] Cannot allocate resource for EISA slot 5
[    5.145432] Cannot allocate resource for EISA slot 6
[    5.145433] Cannot allocate resource for EISA slot 7
[    5.145435] Cannot allocate resource for EISA slot 8
[    5.145437] EISA: Detected 0 cards.
[    5.145445] cpufreq-nforce2: No nForce2 chipset.
[    5.145680] cpuidle: using governor ladder
[    5.146060] cpuidle: using governor menu
[    5.146062] EFI Variables Facility v0.08 2004-May-17
[    5.146236] TCP cubic registered
[    5.146340] NET: Registered protocol family 10
[    5.146752] NET: Registered protocol family 17
[    5.146757] Registering the dns_resolver key type
[    5.146772] Using IPI No-Shortcut mode
[    5.146876] PM: Hibernation image not present or could not be loaded.
[    5.146885] registered taskstats version 1
[    5.154056]   Magic number: 14:813:471
[    5.154166] rtc_cmos 00:05: setting system clock to 2014-01-01 08:27:36 UTC (1388564856)
[    5.155712] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    5.155714] EDD information not available.
[    5.193587] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3
[    5.324114] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    5.348123] usb 1-1: new high-speed USB device number 2 using ehci_hcd
[    5.375038] ata1.00: ATA-8: TOSHIBA MK7575GSX, GT001M, max UDMA/100
[    5.375050] ata1.00: 1465149168 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
[    5.376147] ata1.00: configured for UDMA/100
[    5.376294] scsi 0:0:0:0: Direct-Access     ATA      TOSHIBA MK7575GS GT00 PQ: 0 ANSI: 5
[    5.376485] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    5.376538] sd 0:0:0:0: [sda] 1465149168 512-byte logical blocks: (750 GB/698 GiB)
[    5.376876] sd 0:0:0:0: [sda] Write Protect is off
[    5.376879] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    5.377030] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    5.442389]  sda: sda1 sda2 sda3 sda4 < sda5 sda6 >
[    5.443865] sd 0:0:0:0: [sda] Attached SCSI disk
[    5.481034] hub 1-1:1.0: USB hub found
[    5.481225] hub 1-1:1.0: 6 ports detected
[    5.592120] usb 2-1: new high-speed USB device number 2 using ehci_hcd
[    5.725032] hub 2-1:1.0: USB hub found
[    5.725224] hub 2-1:1.0: 6 ports detected
[    5.796354] usb 1-1.2: new high-speed USB device number 3 using ehci_hcd
[    6.068353] usb 1-1.4: new high-speed USB device number 4 using ehci_hcd
[   10.976109] ata3: link is slow to respond, please be patient (ready=0)
[   15.400111] ata3: COMRESET failed (errno=-16)
[   21.000239] ata3: link is slow to respond, please be patient (ready=0)
[   25.424112] ata3: COMRESET failed (errno=-16)
[   30.964209] ata3: link is slow to respond, please be patient (ready=0)
[   60.476106] ata3: COMRESET failed (errno=-16)
[   60.476118] ata3: limiting SATA link speed to 1.5 Gbps
[   65.500114] ata3: COMRESET failed (errno=-16)
[   65.500149] ata3: reset failed, giving up
[   65.500168] ata3: exception Emask 0x52 SAct 0x0 SErr 0x5ad0c02 action 0xe frozen t4
[   65.500175] ata3: irq_stat 0x00400040, connection status changed
[   65.500191] ata3: SError: { RecovComm Proto HostInt PHYRdyChg CommWake 10B8B BadCRC LinkSeq TrStaTrns DevExch }
[   65.500196] ata3: hard resetting link
[   67.728114] ata3: COMRESET failed (errno=-32)
[   67.728126] ata3: reset failed (errno=-32), retrying in 8 secs
[   75.500231] ata3: limiting SATA link speed to 1.5 Gbps
[   75.500234] ata3: hard resetting link
[   81.264111] ata3: link is slow to respond, please be patient (ready=0)
[   85.520111] ata3: COMRESET failed (errno=-16)
[   85.520122] ata3: hard resetting link
[   91.284113] ata3: link is slow to respond, please be patient (ready=0)
[  120.572113] ata3: COMRESET failed (errno=-16)
[  120.572126] ata3: hard resetting link
[  125.608114] ata3: COMRESET failed (errno=-16)
[  125.608129] ata3: reset failed, giving up
[  125.608145] ata3: EH complete
[  125.608553] Freeing unused kernel memory: 716k freed
[  125.608765] Write protecting the kernel text: 5640k
[  125.608853] Write protecting the kernel read-only data: 2332k
[  125.627813] udevd[131]: starting version 175
[  125.740655] sdhci: Secure Digital Host Controller Interface driver
[  125.740659] sdhci: Copyright(c) Pierre Ossman
[  125.740940] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[  125.740963] r8169 0000:02:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[  125.741010] r8169 0000:02:00.0: setting latency timer to 64
[  125.741024] sdhci-pci 0000:05:00.0: SDHCI controller found [197b:2392] (rev 30)
[  125.741062] sdhci-pci 0000:05:00.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[  125.741113] sdhci-pci 0000:05:00.0: setting latency timer to 64
[  125.741138] r8169 0000:02:00.0: irq 49 for MSI/MSI-X
[  125.741142] mmc0: no vmmc regulator found
[  125.741192] Registered led device: mmc0::
[  125.741687] r8169 0000:02:00.0: eth0: RTL8168evl/8111evl at 0xf8024000, b8:70:f4:d3:be:6a, XID 0c900800 IRQ 49
[  125.741692] r8169 0000:02:00.0: eth0: jumbo features [frames: 9200 bytes, tx checksumming: ko]
[  125.742259] mmc0: SDHCI controller on PCI [0000:05:00.0] using DMA
[  125.742275] sdhci-pci 0000:05:00.2: SDHCI controller found [197b:2391] (rev 30)
[  125.742295] sdhci-pci 0000:05:00.2: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[  125.742302] sdhci-pci 0000:05:00.2: Refusing to bind to secondary interface.
[  125.742312] sdhci-pci 0000:05:00.2: PCI INT A disabled
[  125.743171] [drm] Initialized drm 1.1.0 20060810
[  125.748736] i915 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[  125.748743] i915 0000:00:02.0: setting latency timer to 64
[  125.774757] i915 0000:00:02.0: irq 50 for MSI/MSI-X
[  125.774762] [drm] Supports vblank timestamp caching Rev 1 (10.10.2010).
[  125.774764] [drm] Driver supports precise vblank timestamp query.
[  125.774795] vgaarb: device changed decodes: PCI:0000:00:02.0,olddecodes=io+mem,decodes=io+mem:owns=io+mem
[  126.343061] fbcon: inteldrmfb (fb0) is primary device
[  126.343106] Console: switching to colour frame buffer device 200x56
[  126.343146] fb0: inteldrmfb frame buffer device
[  126.343148] drm: registered panic notifier
[  126.427719] acpi device:5f: registered as cooling_device8
[  126.427922] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/LNXVIDEO:00/input/input4
[  126.428044] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)
[  126.428068] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
[  127.100156] EXT4-fs (sda6): mounted filesystem with ordered data mode. Opts: (null)
[  138.908062] ADDRCONF(NETDEV_UP): eth0: link is not ready
[  139.039989] udevd[419]: starting version 175
[  139.070424] Adding 11718652k swap on /dev/sda5.  Priority:-1 extents:1 across:11718652k 
[  139.913445] cfg80211: Calling CRDA to update world regulatory domain
[  139.960271] mei: module is from the staging directory, the quality is unknown, you have been warned.
[  139.960594] mei 0000:00:16.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[  139.960601] mei 0000:00:16.0: setting latency timer to 64
[  139.960660] mei 0000:00:16.0: irq 51 for MSI/MSI-X
[  140.203117] jmb38x_ms 0000:05:00.3: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[  140.203127] jmb38x_ms 0000:05:00.3: setting latency timer to 64
[  140.204351] wmi: Mapper loaded
[  140.217070] lp: driver loaded but no devices found
[  140.240678] Linux video capture interface: v2.00
[  140.258348] cfg80211: World regulatory domain updated:
[  140.258351] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[  140.258354] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  140.258356] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[  140.258359] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[  140.258361] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  140.258363] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  140.409283] toshiba_acpi: Toshiba Laptop ACPI Extras version 0.19
[  140.409348] input: Toshiba input device as /devices/virtual/input/input5
[  140.417456] Registered led device: toshiba::illumination
[  140.600734] uvcvideo: Found UVC 1.00 device USB 2.0 Camera (058f:b003)
[  140.604872] input: USB 2.0 Camera as /devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.4/1-1.4:1.0/input/input6
[  140.604969] usbcore: registered new interface driver uvcvideo
[  140.604972] USB Video Class driver (1.1.1)
[  140.932262] i2400m_usb 1-1.2:1.0: WiMAX interface wmx0 (64:d4:da:5f:d0:f5) ready
[  141.107178] Intel(R) Wireless WiFi Link AGN driver for Linux, in-tree:
[  141.107182] Copyright(c) 2003-2011 Intel Corporation
[  141.107265] iwlwifi 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[  141.107318] iwlwifi 0000:03:00.0: setting latency timer to 64
[  141.107358] iwlwifi 0000:03:00.0: pci_resource_len = 0x00002000
[  141.107360] iwlwifi 0000:03:00.0: pci_resource_base = f8134000
[  141.107362] iwlwifi 0000:03:00.0: HW Revision ID = 0x67
[  141.107667] iwlwifi 0000:03:00.0: irq 52 for MSI/MSI-X
[  141.107776] iwlwifi 0000:03:00.0: Detected Intel(R) Centrino(R) Wireless-N + WiMAX 6150 BGN, REV=0x84
[  141.107925] iwlwifi 0000:03:00.0: L1 Enabled; Disabling L0S
[  141.118620] iwlwifi 0000:03:00.0: device EEPROM VER=0x557, CALIB=0x6
[  141.118623] iwlwifi 0000:03:00.0: Device SKU: 0X150
[  141.118625] iwlwifi 0000:03:00.0: Valid Tx ant: 0X1, Valid Rx ant: 0X3
[  141.118649] iwlwifi 0000:03:00.0: Tunable channels: 13 802.11bg, 0 802.11a channels
[  141.118812] iwlwifi 0000:03:00.0: RF_KILL bit toggled to disable radio.
[  141.352285] EXT4-fs (sda6): re-mounted. Opts: errors=remount-ro
[  141.406738] iwlwifi 0000:03:00.0: loaded firmware version 41.28.5.1 build 33926
[  141.406913] Registered led device: phy0-led
[  141.406950] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain
[  141.477720] snd_hda_intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[  141.477774] snd_hda_intel 0000:00:1b.0: irq 53 for MSI/MSI-X
[  141.477803] snd_hda_intel 0000:00:1b.0: setting latency timer to 64
[  141.576165] ieee80211 phy0: Selected rate control algorithm 'iwl-agn-rs'
[  141.724274] init: failsafe main process (780) killed by TERM signal
[  142.259629] psmouse serio1: synaptics: Touchpad model: 1, fw: 7.4, id: 0x1e0b1, caps: 0xd04773/0xa40000/0xa0400
[  142.259644] psmouse serio1: synaptics: Toshiba Satellite P775 detected, limiting rate to 40pps.
[  142.412516] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input7
[  142.500910] ppdev: user-space parallel port driver
[  142.586879] Bluetooth: Core ver 2.16
[  142.586895] NET: Registered protocol family 31
[  142.586897] Bluetooth: HCI device and connection manager initialized
[  142.586899] Bluetooth: HCI socket layer initialized
[  142.586901] Bluetooth: L2CAP socket layer initialized
[  142.586906] Bluetooth: SCO socket layer initialized
[  142.602127] HDMI status: Codec=3 Pin=5 Presence_Detect=0 ELD_Valid=0
[  142.602214] input: HDA Intel PCH HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:1b.0/sound/card0/input8
[  142.602394] input: HDA Intel PCH Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input9
[  142.602519] input: HDA Intel PCH Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card0/input10
[  142.626191] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[  142.626194] Bluetooth: BNEP filters: protocol multicast
[  142.661903] Bluetooth: RFCOMM TTY layer initialized
[  142.661907] Bluetooth: RFCOMM socket layer initialized
[  142.661909] Bluetooth: RFCOMM ver 1.11
[  144.670092] i2400m_usb 1-1.2:1.0: firmware interface version 9.3.2
[  144.680164] usbcore: registered new interface driver i2400m_usb
[  144.680278] ADDRCONF(NETDEV_UP): wmx0: link is not ready
[  144.680779] ADDRCONF(NETDEV_UP): wmx0: link is not ready
[  144.912971] r8169 0000:02:00.0: eth0: link down
[  144.913123] ADDRCONF(NETDEV_UP): eth0: link is not ready
[  144.913584] ADDRCONF(NETDEV_UP): eth0: link is not ready
[  144.915172] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  145.206681] ata3: exception Emask 0x40 SAct 0x0 SErr 0x80800 action 0x7
[  145.206686] ata3: SError: { HostInt 10B8B }
[  145.206691] ata3: hard resetting link
[  145.834871] [drm:gen6_sanitize_pm] *ERROR* Power management discrepancy: GEN6_RP_INTERRUPT_LIMITS expected 16000000, was 12060000
[  150.576047] ata3: link is slow to respond, please be patient (ready=0)
[  155.224026] ata3: COMRESET failed (errno=-16)
[  155.224033] ata3: hard resetting link
[  160.592107] ata3: link is slow to respond, please be patient (ready=0)
[  165.240108] ata3: COMRESET failed (errno=-16)
[  165.240131] ata3: hard resetting link
[  170.600115] ata3: link is slow to respond, please be patient (ready=0)
[  200.280121] ata3: COMRESET failed (errno=-16)
[  200.280144] ata3: hard resetting link
[  205.304123] ata3: COMRESET failed (errno=-16)
[  205.304145] ata3: reset failed, giving up
[  205.304157] ata3: exception Emask 0x40 SAct 0x0 SErr 0x80800 action 0x7 t4
[  205.304160] ata3: SError: { HostInt 10B8B }
[  205.304164] ata3: hard resetting link
[  210.664161] ata3: link is slow to respond, please be patient (ready=0)
[  215.312157] ata3: COMRESET failed (errno=-16)
[  215.312170] ata3: hard resetting link
[  220.672164] ata3: link is slow to respond, please be patient (ready=0)
[  225.320167] ata3: COMRESET failed (errno=-16)
[  225.320180] ata3: hard resetting link
[  230.680164] ata3: link is slow to respond, please be patient (ready=0)
[  260.360162] ata3: COMRESET failed (errno=-16)
[  260.360176] ata3: hard resetting link
[  265.384159] ata3: COMRESET failed (errno=-16)
[  265.384174] ata3: reset failed, giving up
[  265.384186] ata3: EH complete[/PHP]

---

### Post by WanderingAlbatross on 2014-01-25
Still no progress.  It is actually not looking for another hard drive, but uses more than one disk controller for the same hard drive.
Some suggest adding the following boot parameter:libahci.skip_host_reset=1.  I tried, but to no avail.  Also, the kernels up to 3.11 still have the same problem.
Looks like this is a big glitch.

---

