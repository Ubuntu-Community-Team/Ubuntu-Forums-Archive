---
title: "HSM violation"
date: 2009-10-14
forum: Hardware
---

### Post by redDEADresolve on 2009-10-14
I get this error from my new SSD on startup

```
[38.825065] ata1.00 exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6 frozen
[38.825227] BMDMA Stat 0x24
[38.825318] ata1.00:cmd c8/00:18:8f:89:20/00:00:00:00:/e0 tag 0 dma 1228in
[38.825321] res 58/00:18:8f:89:20/00:00:00:00:/e0 Emask 0x2 (HSM violation)
[38.825598] ata1.00: status {DRDY DRQ}
```

My computer stalls at bootup then after 25 seconds the error message pops up and I can login. I do not know if this is from a bad HD or from a bug. Can anyone out there tell me what a HSM violation is? I couldn't find much about it.

Hopefully this helps:

red@mini-9:~$ sudo hdparm -I /dev/sda
```
/dev/sda:

CompactFlash ATA device
	Model Number:       Flash Module                            
	Serial Number:      2519079A060101006403
	Firmware Revision:  Ver3.P0B
Standards:
	Supported: 5 4 
	Likely used: 6
Configuration:
	Logical		max	current
	cylinders	16383	16383
	heads		16	16
	sectors/track	63	63
	--
	CHS current addressable sectors:   61078752
	LBA    user addressable sectors:   61078752
	Logical/Physical Sector size:           512 bytes
	device size with M = 1024*1024:       29823 MBytes
	device size with M = 1000*1000:       31272 MBytes (31 GB)
	cache/buffer size  = 1 KBytes (type=DualPort)
	Nominal Media Rotation Rate: Solid State Device
Capabilities:
	LBA, IORDY(cannot be disabled)
	Standby timer values: spec'd by Standard, no device specific minimum
	R/W multiple sector transfer: Max = 1	Current = 1
	DMA: mdma0 mdma1 mdma2 udma0 udma1 udma2 udma3 udma4 *udma5 
	     Cycle time: min=120ns recommended=120ns
	PIO: pio0 pio1 pio2 pio3 pio4 
	     Cycle time: no flow control=120ns  IORDY flow control=120ns
Commands/features:
	Enabled	Supported:
	   *	SMART feature set
	    	Security Mode feature set
	   *	Power Management feature set
	    	Write cache
	   *	WRITE_BUFFER command
	   *	READ_BUFFER command
	   *	NOP cmd
	   *	CFA feature set
	   *	Mandatory FLUSH_CACHE
Security: 
	Master password revision code = 65534
		supported
	not	enabled
	not	locked
		frozen
	not	expired: security count
		supported: enhanced erase
	60min for SECURITY ERASE UNIT. 60min for ENHANCED SECURITY ERASE UNIT.
```


red@mini-9:~$ dmesg
```
red@mini-9:~$ dmesg
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.31-14-generic (buildd@rothera) (gcc version 4.4.1 (Ubuntu 4.4.1-4ubuntu7) ) #46-Ubuntu SMP Tue Oct 13 16:47:59 UTC 2009 (Ubuntu 2.6.31-14.46-generic)
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
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
[    0.000000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000007f6d0000 (usable)
[    0.000000]  BIOS-e820: 000000007f6d0000 - 000000007f6e2000 (ACPI data)
[    0.000000]  BIOS-e820: 000000007f6e2000 - 000000007f6e3000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000007f6e3000 - 0000000080000000 (reserved)
[    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed00000 - 00000000fed00400 (reserved)
[    0.000000]  BIOS-e820: 00000000fed14000 - 00000000fed1a000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed1c000 - 00000000fed90000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000ff000000 - 0000000100000000 (reserved)
[    0.000000] DMI present.
[    0.000000] last_pfn = 0x7f6d0 max_arch_pfn = 0x100000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-CFFFF write-protect
[    0.000000]   D0000-DFFFF uncachable
[    0.000000]   E0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000 mask 080000000 write-back
[    0.000000]   1 base 07F700000 mask 0FFF00000 uncachable
[    0.000000]   2 base 07F800000 mask 0FF800000 uncachable
[    0.000000]   3 disabled
[    0.000000]   4 disabled
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] e820 update range: 0000000000002000 - 0000000000006000 (usable) ==> (reserved)
[    0.000000] Scanning 1 areas for low memory corruption
[    0.000000] modified physical RAM map:
[    0.000000]  modified: 0000000000000000 - 0000000000002000 (usable)
[    0.000000]  modified: 0000000000002000 - 0000000000006000 (reserved)
[    0.000000]  modified: 0000000000006000 - 000000000009f800 (usable)
[    0.000000]  modified: 000000000009f800 - 00000000000a0000 (reserved)
[    0.000000]  modified: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  modified: 0000000000100000 - 000000007f6d0000 (usable)
[    0.000000]  modified: 000000007f6d0000 - 000000007f6e2000 (ACPI data)
[    0.000000]  modified: 000000007f6e2000 - 000000007f6e3000 (ACPI NVS)
[    0.000000]  modified: 000000007f6e3000 - 0000000080000000 (reserved)
[    0.000000]  modified: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  modified: 00000000fec00000 - 00000000fec10000 (reserved)
[    0.000000]  modified: 00000000fed00000 - 00000000fed00400 (reserved)
[    0.000000]  modified: 00000000fed14000 - 00000000fed1a000 (reserved)
[    0.000000]  modified: 00000000fed1c000 - 00000000fed90000 (reserved)
[    0.000000]  modified: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  modified: 00000000ff000000 - 0000000100000000 (reserved)
[    0.000000] initial memory mapped : 0 - 00c00000
[    0.000000] init_memory_mapping: 0000000000000000-00000000377fe000
[    0.000000] Using x86 segment limits to approximate NX protection
[    0.000000]  0000000000 - 0000400000 page 4k
[    0.000000]  0000400000 - 0037400000 page 2M
[    0.000000]  0037400000 - 00377fe000 page 4k
[    0.000000] kernel direct mapping tables up to 377fe000 @ 7000-c000
[    0.000000] RAMDISK: 37976000 - 37fef808
[    0.000000] Allocated new RAMDISK: 008ad000 - 00f26808
[    0.000000] Move RAMDISK from 0000000037976000 - 0000000037fef807 to 008ad000 - 00f26807
[    0.000000] ACPI: RSDP 000f7f70 00024 (v02 PTLTD )
[    0.000000] ACPI: XSDT 7f6dbed2 0006C (v01 PTLTD  	 XSDT   06040000  LTP 00000000)
[    0.000000] ACPI: FACP 7f6e1d48 000F4 (v03 INTEL  CALISTGA 06040000 ALAN 00000001)
[    0.000000] ACPI: DSDT 7f6dcdb7 04F1D (v01 INTEL  CALISTGA 06040000 INTL 20050624)
[    0.000000] ACPI: FACS 7f6e2fc0 00040
[    0.000000] ACPI: APIC 7f6e1e3c 00068 (v01 INTEL  CALISTGA 06040000 LOHR 0000005A)
[    0.000000] ACPI: HPET 7f6e1ea4 00038 (v01 INTEL  CALISTGA 06040000 LOHR 0000005A)
[    0.000000] ACPI: MCFG 7f6e1edc 0003C (v01 INTEL  CALISTGA 06040000 LOHR 0000005A)
[    0.000000] ACPI: TCPA 7f6e1f18 00032 (v01 PTLTD  CALISTGA 06040000  PTL 00000001)
[    0.000000] ACPI: TMOR 7f6e1f4a 00026 (v01 PTLTD           06040000 PTL  00000003)
[    0.000000] ACPI: APIC 7f6e1f70 00068 (v01 PTLTD  	 APIC   06040000  LTP 00000000)
[    0.000000] ACPI: BOOT 7f6e1fd8 00028 (v01 PTLTD  $SBFTBL$ 06040000  LTP 00000001)
[    0.000000] ACPI: SSDT 7f6dbf3e 004F6 (v02  PmRef    CpuPm 00003000 INTL 20050624)
[    0.000000] ACPI: BIOS bug: multiple APIC/MADT found, using 0
[    0.000000] ACPI: If "acpi_apic_instance=2" works better, notify linux-acpi@vger.kernel.org
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] 1150MB HIGHMEM available.
[    0.000000] 887MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 377fe000
[    0.000000]   low ram: 0 - 377fe000
[    0.000000]   node 0 low ram: 00000000 - 377fe000
[    0.000000]   node 0 bootmap 00008000 - 0000ef00
[    0.000000] (9 early reservations) ==> bootmem [0000000000 - 00377fe000]
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000]   #1 [0000001000 - 0000002000]    EX TRAMPOLINE ==> [0000001000 - 0000002000]
[    0.000000]   #2 [0000006000 - 0000007000]       TRAMPOLINE ==> [0000006000 - 0000007000]
[    0.000000]   #3 [0000100000 - 00008a80a0]    TEXT DATA BSS ==> [0000100000 - 00008a80a0]
[    0.000000]   #4 [000009f800 - 0000100000]    BIOS reserved ==> [000009f800 - 0000100000]
[    0.000000]   #5 [00008a9000 - 00008ac124]              BRK ==> [00008a9000 - 00008ac124]
[    0.000000]   #6 [0000007000 - 0000008000]          PGTABLE ==> [0000007000 - 0000008000]
[    0.000000]   #7 [00008ad000 - 0000f26808]      NEW RAMDISK ==> [00008ad000 - 0000f26808]
[    0.000000]   #8 [0000008000 - 000000f000]          BOOTMAP ==> [0000008000 - 000000f000]
[    0.000000] found SMP MP-table at [c00f7fa0] f7fa0
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000000 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x000377fe
[    0.000000]   HighMem  0x000377fe -> 0x0007f6d0
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[3] active PFN ranges
[    0.000000]     0: 0x00000000 -> 0x00000002
[    0.000000]     0: 0x00000006 -> 0x0000009f
[    0.000000]     0: 0x00000100 -> 0x0007f6d0
[    0.000000] On node 0 totalpages: 521835
[    0.000000] free_area_init_node: node 0, pgdat c0784900, node_mem_map c1000000
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3963 pages, LIFO batch:0
[    0.000000]   Normal zone: 1744 pages used for memmap
[    0.000000]   Normal zone: 221486 pages, LIFO batch:31
[    0.000000]   HighMem zone: 2302 pages used for memmap
[    0.000000]   HighMem zone: 292308 pages, LIFO batch:31
[    0.000000] Using APIC driver default
[    0.000000] ACPI: PM-Timer IO Port: 0x1008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
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
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
[    0.000000] SMP: Allowing 2 CPUs, 0 hotplug CPUs
[    0.000000] nr_irqs_gsi: 24
[    0.000000] PM: Registered nosave memory: 0000000000002000 - 0000000000006000
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
[    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 80000000 (gap: 80000000:60000000)
[    0.000000] NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:2 nr_node_ids:1
[    0.000000] PERCPU: Embedded 14 pages at c1ffa000, static data 35612 bytes
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 517757
[    0.000000] Kernel command line: root=UUID=0374c7f5-c6f9-4545-a0ac-2e15d4178704 ro quiet splash quiet 
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] allocated 10438720 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] Initializing HighMem for node 0 (000377fe:0007f6d0)
[    0.000000] Memory: 2044484k/2087744k available (4565k kernel code, 41980k reserved, 2143k data, 540k init, 1178440k highmem)
[    0.000000] virtual kernel memory layout:
[    0.000000]     fixmap  : 0xfff1d000 - 0xfffff000   ( 904 kB)
[    0.000000]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[    0.000000]     vmalloc : 0xf7ffe000 - 0xff7fe000   ( 120 MB)
[    0.000000]     lowmem  : 0xc0000000 - 0xf77fe000   ( 887 MB)
[    0.000000]       .init : 0xc078e000 - 0xc0815000   ( 540 kB)
[    0.000000]       .data : 0xc0575554 - 0xc078d308   (2143 kB)
[    0.000000]       .text : 0xc0100000 - 0xc0575554   (4565 kB)
[    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.000000] SLUB: Genslabs=13, HWalign=64, Order=0-3, MinObjects=0, CPUs=2, Nodes=1
[    0.000000] NR_IRQS:2304 nr_irqs:424
[    0.000000] Extended CMOS year: 2000
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 1596.149 MHz processor.
[    0.001878] Console: colour VGA+ 80x25
[    0.001885] console [tty0] enabled
[    0.002137] hpet clockevent registered
[    0.002145] HPET: 3 timers in total, 0 timers will be used for per-cpu timer
[    0.002156] Calibrating delay loop (skipped), value calculated using timer frequency.. 3192.29 BogoMIPS (lpj=6384596)
[    0.002195] Security Framework initialized
[    0.002234] AppArmor: AppArmor initialized
[    0.002248] Mount-cache hash table entries: 512
[    0.002474] Initializing cgroup subsys ns
[    0.002484] Initializing cgroup subsys cpuacct
[    0.002493] Initializing cgroup subsys memory
[    0.002505] Initializing cgroup subsys freezer
[    0.002510] Initializing cgroup subsys net_cls
[    0.002534] CPU: L1 I cache: 32K, L1 D cache: 24K
[    0.002540] CPU: L2 cache: 512K
[    0.002545] CPU: Physical Processor ID: 0
[    0.002549] CPU: Processor Core ID: 0
[    0.002556] mce: CPU supports 5 MCE banks
[    0.002569] CPU0: Thermal monitoring enabled (TM1)
[    0.002578] using mwait in idle threads.
[    0.002590] Performance Counters: Atom events, Intel PMU driver.
[    0.002604] ... version:                 3
[    0.002608] ... bit width:               40
[    0.002612] ... generic counters:        2
[    0.002617] ... value mask:              000000ffffffffff
[    0.002621] ... max period:              000000007fffffff
[    0.002626] ... fixed-purpose counters:  3
[    0.002630] ... counter mask:            0000000700000003
[    0.002639] Checking 'hlt' instruction... OK.
[    0.020013] ACPI: Core revision 20090521
[    0.036305] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.076010] CPU0: Intel(R) Atom(TM) CPU N270   @ 1.60GHz stepping 02
[    0.080001] Booting processor 1 APIC 0x1 ip 0x6000
[    0.004000] Initializing CPU#1
[    0.004000] Calibrating delay using timer specific routine.. 3191.93 BogoMIPS (lpj=6383860)
[    0.004000] CPU: L1 I cache: 32K, L1 D cache: 24K
[    0.004000] CPU: L2 cache: 512K
[    0.004000] CPU: Physical Processor ID: 0
[    0.004000] CPU: Processor Core ID: 0
[    0.004000] mce: CPU supports 5 MCE banks
[    0.004000] CPU1: Thermal monitoring enabled (TM1)
[    0.004000] x86 PAT enabled: cpu 1, old 0x7040600070406, new 0x7010600070106
[    0.165077] CPU1: Intel(R) Atom(TM) CPU N270   @ 1.60GHz stepping 02
[    0.165112] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
[    0.168048] Brought up 2 CPUs
[    0.168055] Total of 2 processors activated (6384.22 BogoMIPS).
[    0.168121] CPU0 attaching sched-domain:
[    0.168128]  domain 0: span 0-1 level SIBLING
[    0.168134]   groups: 0 1
[    0.168145] CPU1 attaching sched-domain:
[    0.168150]  domain 0: span 0-1 level SIBLING
[    0.168155]   groups: 1 0
[    0.168308] Booting paravirtualized kernel on bare hardware
[    0.168464] regulator: core version 0.5
[    0.168464] Time:  0:57:42  Date: 10/15/09
[    0.168464] NET: Registered protocol family 16
[    0.168464] EISA bus registered
[    0.168464] ACPI: bus type pci registered
[    0.168590] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 255
[    0.168598] PCI: MCFG area at e0000000 reserved in E820
[    0.168602] PCI: Using MMCONFIG for extended config space
[    0.168607] PCI: Using configuration type 1 for base access
[    0.173027] bio: create slab <bio-0> at 0
[    0.173386] ACPI: EC: Look up EC in DSDT
[    0.178952] ACPI: BIOS _OSI(Linux) query ignored
[    0.180494] ACPI: EC: non-query interrupt received, switching to interrupt mode
[    0.256168] ACPI: Interpreter enabled
[    0.256179] ACPI: (supports S0 S3 S4 S5)
[    0.256223] ACPI: Using IOAPIC for interrupt routing
[    0.305023] ACPI: EC: GPE = 0x19, I/O: command/status = 0x66, data = 0x62
[    0.305031] ACPI: EC: driver started in interrupt mode
[    0.305511] ACPI: No dock devices found.
[    0.306492] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.306642] pci 0000:00:02.0: reg 10 32bit mmio: [0xf0000000-0xf007ffff]
[    0.306653] pci 0000:00:02.0: reg 14 io port: [0x1800-0x1807]
[    0.306663] pci 0000:00:02.0: reg 18 32bit mmio: [0xd0000000-0xdfffffff]
[    0.306672] pci 0000:00:02.0: reg 1c 32bit mmio: [0xf0300000-0xf033ffff]
[    0.306728] pci 0000:00:02.1: reg 10 32bit mmio: [0xf0080000-0xf00fffff]
[    0.306881] pci 0000:00:1b.0: reg 10 64bit mmio: [0xf0540000-0xf0543fff]
[    0.306962] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    0.306971] pci 0000:00:1b.0: PME# disabled
[    0.307083] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.307092] pci 0000:00:1c.0: PME# disabled
[    0.307206] pci 0000:00:1c.1: PME# supported from D0 D3hot D3cold
[    0.307215] pci 0000:00:1c.1: PME# disabled
[    0.307331] pci 0000:00:1c.2: PME# supported from D0 D3hot D3cold
[    0.307340] pci 0000:00:1c.2: PME# disabled
[    0.307430] pci 0000:00:1d.0: reg 20 io port: [0x1820-0x183f]
[    0.307517] pci 0000:00:1d.1: reg 20 io port: [0x1840-0x185f]
[    0.307607] pci 0000:00:1d.2: reg 20 io port: [0x1860-0x187f]
[    0.307694] pci 0000:00:1d.3: reg 20 io port: [0x1880-0x189f]
[    0.307786] pci 0000:00:1d.7: reg 10 32bit mmio: [0xf0544000-0xf05443ff]
[    0.307868] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
[    0.307877] pci 0000:00:1d.7: PME# disabled
[    0.308096] pci 0000:00:1f.0: quirk: region 1000-107f claimed by ICH6 ACPI/GPIO/TCO
[    0.308105] pci 0000:00:1f.0: quirk: region 1180-11bf claimed by ICH6 GPIO
[    0.308114] pci 0000:00:1f.0: ICH7 LPC Generic IO decode 1 PIO at 0680 (mask 007f)
[    0.308123] pci 0000:00:1f.0: ICH7 LPC Generic IO decode 2 PIO at ff2c (mask 007f)
[    0.308134] pci 0000:00:1f.0: ICH7 LPC Generic IO decode 4 PIO at 0068 (mask 0007)
[    0.308199] pci 0000:00:1f.1: reg 10 io port: [0x00-0x07]
[    0.308213] pci 0000:00:1f.1: reg 14 io port: [0x00-0x03]
[    0.308225] pci 0000:00:1f.1: reg 18 io port: [0x00-0x07]
[    0.308238] pci 0000:00:1f.1: reg 1c io port: [0x00-0x03]
[    0.308251] pci 0000:00:1f.1: reg 20 io port: [0x1810-0x181f]
[    0.308347] pci 0000:00:1f.3: reg 20 io port: [0x18a0-0x18bf]
[    0.308477] pci 0000:02:00.0: reg 10 32bit mmio: [0xf0100000-0xf01000ff]
[    0.308565] pci 0000:02:00.0: reg 30 32bit mmio: [0x000000-0x00ffff]
[    0.308748] pci 0000:02:00.2: reg 10 32bit mmio: [0xf0100400-0xf01004ff]
[    0.309005] pci 0000:02:00.3: reg 10 32bit mmio: [0xf0100800-0xf01008ff]
[    0.309268] pci 0000:00:1c.0: bridge 32bit mmio: [0xf0100000-0xf01fffff]
[    0.309535] pci 0000:03:00.0: reg 10 32bit mmio: [0xf0200000-0xf0200fff]
[    0.309906] pci 0000:03:00.0: PME# supported from D0 D3hot D3cold
[    0.309930] pci 0000:03:00.0: PME# disabled
[    0.310099] pci 0000:00:1c.1: bridge 32bit mmio: [0xf0200000-0xf02fffff]
[    0.310315] pci 0000:04:00.0: reg 10 io port: [0x2000-0x20ff]
[    0.310428] pci 0000:04:00.0: reg 18 64bit mmio: [0xf0610000-0xf0610fff]
[    0.310488] pci 0000:04:00.0: reg 20 64bit mmio: [0xf0600000-0xf060ffff]
[    0.310534] pci 0000:04:00.0: reg 30 32bit mmio: [0x000000-0x01ffff]
[    0.310725] pci 0000:04:00.0: supports D1 D2
[    0.310730] pci 0000:04:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.310751] pci 0000:04:00.0: PME# disabled
[    0.310929] pci 0000:00:1c.2: bridge io port: [0x2000-0x2fff]
[    0.310946] pci 0000:00:1c.2: bridge 64bit mmio pref: [0xf0600000-0xf06fffff]
[    0.311022] pci 0000:00:1e.0: transparent bridge
[    0.311071] pci_bus 0000:00: on NUMA node 0
[    0.311082] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.311456] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP01._PRT]
[    0.311678] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP02._PRT]
[    0.311830] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP03._PRT]
[    0.312062] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIB._PRT]
[    0.323840] ACPI: PCI Interrupt Link [LNKA] (IRQs 1 3 4 5 6 *7 10 12 14 15)
[    0.324059] ACPI: PCI Interrupt Link [LNKB] (IRQs 1 3 4 5 6 7 *11 12 14 15)
[    0.324255] ACPI: PCI Interrupt Link [LNKC] (IRQs 1 3 4 5 6 7 10 12 14 15) *11
[    0.324452] ACPI: PCI Interrupt Link [LNKD] (IRQs 1 3 4 5 6 7 11 12 14 15) *10
[    0.324647] ACPI: PCI Interrupt Link [LNKE] (IRQs 1 3 4 5 6 7 10 12 14 15) *0, disabled.
[    0.324843] ACPI: PCI Interrupt Link [LNKF] (IRQs 1 3 4 5 6 7 11 12 14 15) *0, disabled.
[    0.325042] ACPI: PCI Interrupt Link [LNKG] (IRQs 1 3 4 5 6 7 *10 12 14 15)
[    0.325242] ACPI: PCI Interrupt Link [LNKH] (IRQs 1 3 4 *5 6 7 11 12 14 15)
[    0.325637] SCSI subsystem initialized
[    0.325719] libata version 3.00 loaded.
[    0.325719] usbcore: registered new interface driver usbfs
[    0.325719] usbcore: registered new interface driver hub
[    0.325719] usbcore: registered new device driver usb
[    0.325719] ACPI: WMI: Mapper loaded
[    0.325719] PCI: Using ACPI for IRQ routing
[    0.336021] Bluetooth: Core ver 2.15
[    0.336065] NET: Registered protocol family 31
[    0.336065] Bluetooth: HCI device and connection manager initialized
[    0.336065] Bluetooth: HCI socket layer initialized
[    0.336065] NetLabel: Initializing
[    0.336065] NetLabel:  domain hash size = 128
[    0.336065] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.336080] NetLabel:  unlabeled traffic allowed by default
[    0.336149] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[    0.336161] hpet0: 3 comparators, 64-bit 14.318180 MHz counter
[    0.356024] pnp: PnP ACPI init
[    0.356063] ACPI: bus type pnp registered
[    0.376249] pnp: PnP ACPI: found 11 devices
[    0.376255] ACPI: ACPI bus type pnp unregistered
[    0.376263] PnPBIOS: Disabled by ACPI PNP
[    0.376288] system 00:01: iomem range 0xe0000000-0xefffffff has been reserved
[    0.376297] system 00:01: iomem range 0xfed14000-0xfed17fff has been reserved
[    0.376304] system 00:01: iomem range 0xfed18000-0xfed18fff has been reserved
[    0.376312] system 00:01: iomem range 0xfed19000-0xfed19fff has been reserved
[    0.376319] system 00:01: iomem range 0xfed1c000-0xfed1ffff has been reserved
[    0.376326] system 00:01: iomem range 0xfed20000-0xfed3ffff has been reserved
[    0.376334] system 00:01: iomem range 0xfed40000-0xfed44fff has been reserved
[    0.376341] system 00:01: iomem range 0xfed45000-0xfed8ffff has been reserved
[    0.376357] system 00:04: iomem range 0xfed00000-0xfed003ff has been reserved
[    0.376372] system 00:06: ioport range 0x680-0x69f has been reserved
[    0.376380] system 00:06: ioport range 0x800-0x80f has been reserved
[    0.376387] system 00:06: ioport range 0x1000-0x107f has been reserved
[    0.376394] system 00:06: ioport range 0x1180-0x11bf has been reserved
[    0.376401] system 00:06: ioport range 0x1640-0x164f has been reserved
[    0.376409] system 00:06: ioport range 0xfe00-0xfe7f has been reserved
[    0.376416] system 00:06: ioport range 0xff00-0xff7f has been reserved
[    0.376429] system 00:07: ioport range 0x6a0-0x6af has been reserved
[    0.376436] system 00:07: ioport range 0x6b0-0x6ff has been reserved
[    0.411312] AppArmor: AppArmor Filesystem Enabled
[    0.411408] pci 0000:00:1c.0: PCI bridge, secondary bus 0000:02
[    0.411414] pci 0000:00:1c.0:   IO window: disabled
[    0.411425] pci 0000:00:1c.0:   MEM window: 0xf0100000-0xf01fffff
[    0.411434] pci 0000:00:1c.0:   PREFETCH window: 0x80000000-0x800fffff
[    0.411444] pci 0000:00:1c.1: PCI bridge, secondary bus 0000:03
[    0.411449] pci 0000:00:1c.1:   IO window: disabled
[    0.411459] pci 0000:00:1c.1:   MEM window: 0xf0200000-0xf02fffff
[    0.411468] pci 0000:00:1c.1:   PREFETCH window: disabled
[    0.411478] pci 0000:00:1c.2: PCI bridge, secondary bus 0000:04
[    0.411485] pci 0000:00:1c.2:   IO window: 0x2000-0x2fff
[    0.411496] pci 0000:00:1c.2:   MEM window: 0x80100000-0x801fffff
[    0.411505] pci 0000:00:1c.2:   PREFETCH window: 0x000000f0600000-0x000000f06fffff
[    0.411519] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:05
[    0.411523] pci 0000:00:1e.0:   IO window: disabled
[    0.411533] pci 0000:00:1e.0:   MEM window: disabled
[    0.411541] pci 0000:00:1e.0:   PREFETCH window: disabled
[    0.411565]   alloc irq_desc for 17 on node -1
[    0.411571]   alloc kstat_irqs on node -1
[    0.411583] pci 0000:00:1c.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    0.411593] pci 0000:00:1c.0: setting latency timer to 64
[    0.411608]   alloc irq_desc for 16 on node -1
[    0.411612]   alloc kstat_irqs on node -1
[    0.411621] pci 0000:00:1c.1: PCI INT B -> GSI 16 (level, low) -> IRQ 16
[    0.411630] pci 0000:00:1c.1: setting latency timer to 64
[    0.411644]   alloc irq_desc for 18 on node -1
[    0.411649]   alloc kstat_irqs on node -1
[    0.411657] pci 0000:00:1c.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.411666] pci 0000:00:1c.2: setting latency timer to 64
[    0.411680] pci 0000:00:1e.0: setting latency timer to 64
[    0.411689] pci_bus 0000:00: resource 0 io:  [0x00-0xffff]
[    0.411696] pci_bus 0000:00: resource 1 mem: [0x000000-0xffffffff]
[    0.411703] pci_bus 0000:02: resource 1 mem: [0xf0100000-0xf01fffff]
[    0.411709] pci_bus 0000:02: resource 2 pref mem [0x80000000-0x800fffff]
[    0.411716] pci_bus 0000:03: resource 1 mem: [0xf0200000-0xf02fffff]
[    0.411723] pci_bus 0000:04: resource 0 io:  [0x2000-0x2fff]
[    0.411729] pci_bus 0000:04: resource 1 mem: [0x80100000-0x801fffff]
[    0.411735] pci_bus 0000:04: resource 2 pref mem [0xf0600000-0xf06fffff]
[    0.411742] pci_bus 0000:05: resource 3 io:  [0x00-0xffff]
[    0.411748] pci_bus 0000:05: resource 4 mem: [0x000000-0xffffffff]
[    0.411823] NET: Registered protocol family 2
[    0.412045] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.412709] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.413698] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.414153] TCP: Hash tables configured (established 131072 bind 65536)
[    0.414160] TCP reno registered
[    0.414392] NET: Registered protocol family 1
[    0.414526] Trying to unpack rootfs image as initramfs...
[    0.501143] Switched to high resolution mode on CPU 1
[    0.503999] Switched to high resolution mode on CPU 0
[    0.732726] Freeing initrd memory: 6630k freed
[    0.739036] Simple Boot Flag at 0x36 set to 0x1
[    0.739426] cpufreq-nforce2: No nForce2 chipset.
[    0.739488] Scanning for low memory corruption every 60 seconds
[    0.739712] audit: initializing netlink socket (disabled)
[    0.739744] type=2000 audit(1255568261.736:1): initialized
[    0.757500] highmem bounce pool size: 64 pages
[    0.757513] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    0.760864] VFS: Disk quotas dquot_6.5.2
[    0.761007] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.762325] fuse init (API version 7.12)
[    0.762515] msgmni has been set to 1706
[    0.762978] alg: No test for stdrng (krng)
[    0.763010] io scheduler noop registered
[    0.763016] io scheduler anticipatory registered
[    0.763020] io scheduler deadline registered
[    0.763130] io scheduler cfq registered (default)
[    0.763155] pci 0000:00:02.0: Boot video device
[    0.763515]   alloc irq_desc for 24 on node -1
[    0.763521]   alloc kstat_irqs on node -1
[    0.763542] pcieport-driver 0000:00:1c.0: irq 24 for MSI/MSI-X
[    0.763559] pcieport-driver 0000:00:1c.0: setting latency timer to 64
[    0.763793]   alloc irq_desc for 25 on node -1
[    0.763798]   alloc kstat_irqs on node -1
[    0.763813] pcieport-driver 0000:00:1c.1: irq 25 for MSI/MSI-X
[    0.763829] pcieport-driver 0000:00:1c.1: setting latency timer to 64
[    0.764082]   alloc irq_desc for 26 on node -1
[    0.764087]   alloc kstat_irqs on node -1
[    0.764102] pcieport-driver 0000:00:1c.2: irq 26 for MSI/MSI-X
[    0.764118] pcieport-driver 0000:00:1c.2: setting latency timer to 64
[    0.764297] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.764503] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.769225] ACPI: AC Adapter [ACAD] (on-line)
[    0.769379] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input0
[    0.769387] ACPI: Power Button [PWRF]
[    0.769488] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input1
[    0.769560] ACPI: Lid Switch [LID0]
[    0.769660] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input2
[    0.769667] ACPI: Power Button [PWRB]
[    0.769768] input: Sleep Button as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input3
[    0.769775] ACPI: Sleep Button [SLPB]
[    0.771178] ACPI: SSDT 7f6dca9e 00245 (v02  PmRef  Cpu0Ist 00003000 INTL 20050624)
[    0.772112] ACPI: SSDT 7f6dc434 005E5 (v02  PmRef  Cpu0Cst 00003001 INTL 20050624)
[    0.773168] Monitor-Mwait will be used to enter C-1 state
[    0.773255] Monitor-Mwait will be used to enter C-2 state
[    0.773315] Monitor-Mwait will be used to enter C-3 state
[    0.773330] Marking TSC unstable due to TSC halts in idle
[    0.773406] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[    0.773477] processor LNXCPU:00: registered as cooling_device0
[    0.773487] ACPI: Processor [CPU0] (supports 8 throttling states)
[    0.774290] ACPI: SSDT 7f6dcce3 000D4 (v02  PmRef  Cpu1Ist 00003000 INTL 20050624)
[    0.774885] ACPI: SSDT 7f6dca19 00085 (v02  PmRef  Cpu1Cst 00003000 INTL 20050624)
[    0.776030] ACPI: CPU1 (power states: C1[C1] C2[C2] C3[C3])
[    0.776084] processor LNXCPU:01: registered as cooling_device1
[    0.776094] ACPI: Processor [CPU1] (supports 8 throttling states)
[    0.807707] thermal LNXTHERM:01: registered as thermal_zone0
[    0.807727] ACPI: Thermal Zone [TZ01] (52 C)
[    0.807873] isapnp: Scanning for PnP cards...
[    0.856449] ACPI: EC: GPE storm detected, transactions will use polling mode
[    1.161857] isapnp: No Plug & Play device found
[    1.356030] ACPI: EC: missing confirmations, switch off interrupt mode.
[    2.888278] ACPI: Battery Slot [BAT1] (battery present)
[    2.888543] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    2.891261] brd: module loaded
[    2.892298] loop: module loaded
[    2.892471] input: Macintosh mouse button emulation as /devices/virtual/input/input4
[    2.892709] ata_piix 0000:00:1f.1: version 2.13
[    2.892738]   alloc irq_desc for 19 on node -1
[    2.892743]   alloc kstat_irqs on node -1
[    2.892757] ata_piix 0000:00:1f.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    2.892825] ata_piix 0000:00:1f.1: setting latency timer to 64
[    2.892998] scsi0 : ata_piix
[    2.893217] scsi1 : ata_piix
[    2.894263] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0x1810 irq 14
[    2.894271] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x1818 irq 15
[    2.894588] ata2: port disabled. ignoring.
[    2.896339] Fixed MDIO Bus: probed
[    2.896419] PPP generic driver version 2.4.2
[    2.896641] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    2.896688]   alloc irq_desc for 23 on node -1
[    2.896695]   alloc kstat_irqs on node -1
[    2.896708] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    2.896740] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    2.896748] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    2.896858] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 1
[    2.900799] ehci_hcd 0000:00:1d.7: debug port 1
[    2.900811] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
[    2.900840] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xf0544000
[    2.916044] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    2.916214] usb usb1: configuration #1 chosen from 1 choice
[    2.916281] hub 1-0:1.0: USB hub found
[    2.916309] hub 1-0:1.0: 8 ports detected
[    2.916453] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    2.916495] uhci_hcd: USB Universal Host Controller Interface driver
[    2.916614] uhci_hcd 0000:00:1d.0: power state changed by ACPI to D0
[    2.916629] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    2.916643] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    2.916651] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    2.916732] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    2.916772] uhci_hcd 0000:00:1d.0: irq 23, io base 0x00001820
[    2.916950] usb usb2: configuration #1 chosen from 1 choice
[    2.917015] hub 2-0:1.0: USB hub found
[    2.917034] hub 2-0:1.0: 2 ports detected
[    2.917136] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    2.917153] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    2.917161] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    2.917227] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3
[    2.917282] uhci_hcd 0000:00:1d.1: irq 19, io base 0x00001840
[    2.917450] usb usb3: configuration #1 chosen from 1 choice
[    2.917515] hub 3-0:1.0: USB hub found
[    2.917530] hub 3-0:1.0: 2 ports detected
[    2.917622] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    2.917635] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    2.917642] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    2.917709] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4
[    2.917758] uhci_hcd 0000:00:1d.2: irq 18, io base 0x00001860
[    2.917925] usb usb4: configuration #1 chosen from 1 choice
[    2.917990] hub 4-0:1.0: USB hub found
[    2.918005] hub 4-0:1.0: 2 ports detected
[    2.918154] uhci_hcd 0000:00:1d.3: power state changed by ACPI to D0
[    2.918167] uhci_hcd 0000:00:1d.3: PCI INT D -> GSI 16 (level, low) -> IRQ 16
[    2.918179] uhci_hcd 0000:00:1d.3: setting latency timer to 64
[    2.918186] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[    2.918257] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 5
[    2.918309] uhci_hcd 0000:00:1d.3: irq 16, io base 0x00001880
[    2.918483] usb usb5: configuration #1 chosen from 1 choice
[    2.918544] hub 5-0:1.0: USB hub found
[    2.918559] hub 5-0:1.0: 2 ports detected
[    2.918749] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    2.953521] serio: i8042 KBD port at 0x60,0x64 irq 1
[    2.953536] serio: i8042 AUX port at 0x60,0x64 irq 12
[    2.953712] mice: PS/2 mouse device common for all mice
[    2.953997] rtc_cmos 00:08: RTC can wake from S4
[    2.954093] rtc_cmos 00:08: rtc core: registered rtc_cmos as rtc0
[    2.954142] rtc0: alarms up to one month, y3k, 242 bytes nvram, hpet irqs
[    2.954466] device-mapper: uevent: version 1.0.3
[    2.954726] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: dm-devel@redhat.com
[    2.954904] device-mapper: multipath: version 1.1.0 loaded
[    2.954912] device-mapper: multipath round-robin: version 1.0.0 loaded
[    2.955250] EISA: Probing bus 0 at eisa.0
[    2.955263] Cannot allocate resource for EISA slot 1
[    2.955271] Cannot allocate resource for EISA slot 2
[    2.955309] EISA: Detected 0 cards.
[    2.955723] cpuidle: using governor ladder
[    2.955980] cpuidle: using governor menu
[    2.957139] TCP cubic registered
[    2.957510] NET: Registered protocol family 10
[    2.958481] lo: Disabled Privacy Extensions
[    2.959196] NET: Registered protocol family 17
[    2.959239] Bluetooth: L2CAP ver 2.13
[    2.959243] Bluetooth: L2CAP socket layer initialized
[    2.959249] Bluetooth: SCO (Voice Link) ver 0.6
[    2.959253] Bluetooth: SCO socket layer initialized
[    2.959359] Bluetooth: RFCOMM TTY layer initialized
[    2.959368] Bluetooth: RFCOMM socket layer initialized
[    2.959374] Bluetooth: RFCOMM ver 1.11
[    2.960509] Using IPI No-Shortcut mode
[    2.960681] PM: Resume from disk failed.
[    2.960707] registered taskstats version 1
[    2.960954]   Magic number: 13:589:961
[    2.961107] rtc_cmos 00:08: setting system clock to 2009-10-15 00:57:44 UTC (1255568264)
[    2.961115] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    2.961120] EDD information not available.
[    2.981628] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input5
[    3.056606] ata1.00: CFA: Flash Module, Ver3.P0B, max UDMA/100
[    3.056614] ata1.00: 61078752 sectors, multi 1: LBA 
[    3.064553] ata1.00: configured for UDMA/100
[    3.064787] scsi 0:0:0:0: Direct-Access     ATA      Flash Module     Ver3 PQ: 0 ANSI: 5
[    3.065115] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    3.065230] sd 0:0:0:0: [sda] 61078752 512-byte logical blocks: (31.2 GB/29.1 GiB)
[    3.065364] sd 0:0:0:0: [sda] Write Protect is off
[    3.065372] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    3.065442] sd 0:0:0:0: [sda] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
[    3.065786]  sda: sda1 sda2 < sda5 sda6 >
[    3.069676] sd 0:0:0:0: [sda] Attached SCSI disk
[    3.228176] usb 1-2: new high speed USB device using ehci_hcd and address 2
[    3.401500] usb 1-2: configuration #1 chosen from 1 choice
[    3.500137] Clocksource tsc unstable (delta = -267499141 ns)
[    3.628757] Freeing unused kernel memory: 540k freed
[    3.629282] Write protecting the kernel text: 4568k
[    3.629363] Write protecting the kernel read-only data: 1836k
[    3.869103] usb 5-1: new full speed USB device using uhci_hcd and address 2
[    4.048623] usb 5-1: configuration #1 chosen from 1 choice
[    4.109580] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    4.109652] r8169 0000:04:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    4.109786] r8169 0000:04:00.0: setting latency timer to 64
[    4.109988]   alloc irq_desc for 27 on node -1
[    4.109997]   alloc kstat_irqs on node -1
[    4.110061] r8169 0000:04:00.0: irq 27 for MSI/MSI-X
[    4.111991] eth0: RTL8102e at 0xf8080000, 00:21:70:ba:fd:90, XID 24a00000 IRQ 27
[    4.756551] PM: Starting manual resume from disk
[    4.756560] PM: Resume from partition 8:6
[    4.756565] PM: Checking hibernation image.
[    4.757143] PM: Resume from disk failed.
[    4.764765] EXT4-fs (sda1): barriers enabled
[    4.767802] kjournald2 starting: pid 337, dev sda1:8, commit interval 5 seconds
[    4.767858] EXT4-fs (sda1): delayed allocation enabled
[    4.767866] EXT4-fs: file extents enabled
[    4.769242] EXT4-fs: mballoc enabled
[    4.769274] EXT4-fs (sda1): mounted filesystem with ordered data mode
[    4.978618] type=1505 audit(1255568266.514:2): operation="profile_load" pid=358 name=/sbin/dhclient3
[    4.979205] type=1505 audit(1255568266.514:3): operation="profile_load" pid=358 name=/usr/lib/NetworkManager/nm-dhcp-client.action
[    4.979535] type=1505 audit(1255568266.514:4): operation="profile_load" pid=358 name=/usr/lib/connman/scripts/dhclient-script
[    4.989591] type=1505 audit(1255568266.526:5): operation="profile_load" pid=360 name=/usr/sbin/tcpdump
[    5.233559] Adding 1100412k swap on /dev/sda6.  Priority:-1 extents:1 across:1100412k SS
[    5.337431] udev: starting version 147
[    5.380691] EXT4-fs (sda1): internal journal on sda1:8
[    5.549955] lp: driver loaded but no devices found
[    5.567552] EXT4-fs (sda5): barriers enabled
[    5.570503] kjournald2 starting: pid 457, dev sda5:8, commit interval 5 seconds
[    5.571610] EXT4-fs (sda5): internal journal on sda5:8
[    5.571629] EXT4-fs (sda5): delayed allocation enabled
[    5.571643] EXT4-fs: file extents enabled
[    5.576538] EXT4-fs: mballoc enabled
[    5.576572] EXT4-fs (sda5): mounted filesystem with ordered data mode
[    5.991617] type=1505 audit(1255568267.526:6): operation="profile_replace" pid=596 name=/sbin/dhclient3
[    5.992300] type=1505 audit(1255568267.530:7): operation="profile_replace" pid=596 name=/usr/lib/NetworkManager/nm-dhcp-client.action
[    5.992631] type=1505 audit(1255568267.530:8): operation="profile_replace" pid=596 name=/usr/lib/connman/scripts/dhclient-script
[    6.003096] type=1505 audit(1255568267.538:9): operation="profile_replace" pid=602 name=/usr/sbin/tcpdump
[    6.232355] acpi device:02: registered as cooling_device2
[    6.232761] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:01/input/input6
[    6.232891] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)
[    6.503916] Linux agpgart interface v0.103
[    6.530098] intel_rng: FWH not detected
[    6.551612] agpgart-intel 0000:00:00.0: Intel 945GME Chipset
[    6.551997] agpgart-intel 0000:00:00.0: detected 7932K stolen memory
[    6.555073] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xd0000000
[    6.737851] [drm] Initialized drm 1.1.0 20060810
[    6.801093] dcdbas dcdbas: Dell Systems Management Base Driver (version 5.6.0-3.2)
[    6.866139] i915 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    6.866155] i915 0000:00:02.0: setting latency timer to 64
[    6.908877] compal-laptop: Identified laptop model 'Dell Mini 9'.
[    6.909150] compal-laptop: driver 0.2.6 successfully loaded.
[    7.063526] dell-wmi: No known WMI GUID found
[    7.153450] [drm] fb0: inteldrmfb frame buffer device
[    7.153472] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
[    7.241650]   alloc irq_desc for 22 on node -1
[    7.241660]   alloc kstat_irqs on node -1
[    7.241677] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[    7.241828] HDA Intel 0000:00:1b.0: setting latency timer to 64
[    7.339130] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:1b.0/input/input7
[    8.267274] sdhci: Secure Digital Host Controller Interface driver
[    8.267283] sdhci: Copyright(c) Pierre Ossman
[    8.274388] sdhci-pci 0000:02:00.0: SDHCI controller found [197b:2382] (rev 0)
[    8.274438] sdhci-pci 0000:02:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    8.274601] sdhci-pci 0000:02:00.0: setting latency timer to 64
[    8.274723] Registered led device: mmc0::
[    8.274840] mmc0: SDHCI controller on PCI [0000:02:00.0] using ADMA
[    8.274876] sdhci-pci 0000:02:00.2: SDHCI controller found [197b:2381] (rev 0)
[    8.274919] sdhci-pci 0000:02:00.2: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    8.274938] sdhci-pci 0000:02:00.2: Refusing to bind to secondary interface.
[    8.274957] sdhci-pci 0000:02:00.2: PCI INT A disabled
[    8.298817] jmb38x_ms 0000:02:00.3: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    8.298838] jmb38x_ms 0000:02:00.3: setting latency timer to 64
[    8.307980] cfg80211: Calling CRDA to update world regulatory domain
[   38.804154] ata1: lost interrupt (Status 0x58)
[   38.808061] ata1: drained 32768 bytes to clear DRQ.
[   38.914158] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6 frozen
[   38.914214] ata1.00: BMDMA stat 0x24
[   38.914266] ata1.00: cmd c8/00:c0:3f:f3:13/00:00:00:00:00/e0 tag 0 dma 98304 in
[   38.914269]          res 58/00:c0:3f:f3:13/00:00:00:00:00/e0 Emask 0x2 (HSM violation)
[   38.914367] ata1.00: status: { DRDY DRQ }
[   38.914449] ata1: soft resetting link
[   39.084514] ata1.00: configured for UDMA/100
[   39.084537] ata1: EH complete
[   39.290666] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, 1.2.26ks
[   39.290678] iwl3945: Copyright(c) 2003-2009 Intel Corporation
[   39.290889] iwl3945 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   39.290919] iwl3945 0000:03:00.0: setting latency timer to 64
[   39.344465] iwl3945 0000:03:00.0: Tunable channels: 11 802.11bg, 13 802.11a channels
[   39.344477] iwl3945 0000:03:00.0: Detected Intel Wireless WiFi Link 3945ABG
[   39.344655]   alloc irq_desc for 28 on node -1
[   39.344663]   alloc kstat_irqs on node -1
[   39.344720] iwl3945 0000:03:00.0: irq 28 for MSI/MSI-X
[   39.401523] phy0: Selected rate control algorithm 'iwl-3945-rs'
[   39.574671] CPU0 attaching NULL sched-domain.
[   39.574684] CPU1 attaching NULL sched-domain.
[   39.588349] CPU0 attaching sched-domain:
[   39.588365]  domain 0: span 0-1 level SIBLING
[   39.588378]   groups: 0 1
[   39.588401] CPU1 attaching sched-domain:
[   39.588411]  domain 0: span 0-1 level SIBLING
[   39.588423]   groups: 1 0
[   40.117462] Bluetooth: Generic Bluetooth USB driver ver 0.5
[   40.117817] usbcore: registered new interface driver btusb
[   40.381281] Linux video capture interface: v2.00
[   40.486187] uvcvideo: Found UVC 1.00 device Integrated Webcam (064e:a118)
[   40.543570] input: Integrated Webcam as /devices/pci0000:00/0000:00:1d.7/usb1/1-2/1-2:1.0/input/input8
[   40.543694] usbcore: registered new interface driver uvcvideo
[   40.543703] USB Video Class driver (v0.1.0)
[   40.690908] CPU0 attaching NULL sched-domain.
[   40.690921] CPU1 attaching NULL sched-domain.
[   40.772287] cfg80211: World regulatory domain updated:
[   40.772295] 	(start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   40.772304] 	(2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   40.772311] 	(2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   40.772319] 	(2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   40.772326] 	(5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   40.772333] 	(5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   40.788485] [drm] LVDS-8: set mode 1024x600 c
[   41.149767] CPU0 attaching sched-domain:
[   41.149776]  domain 0: span 0-1 level SIBLING
[   41.149783]   groups: 0 1
[   41.149795] CPU1 attaching sched-domain:
[   41.149800]  domain 0: span 0-1 level SIBLING
[   41.149806]   groups: 1 0
[   41.172927] Console: switching to colour frame buffer device 128x37
[   41.184827] ip_tables: (C) 2000-2006 Netfilter Core Team
[   41.313261] r8169: eth0: link down
[   41.313900] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   41.993431] Synaptics Touchpad, model: 1, fw: 7.0, id: 0x1c0b1, caps: 0xd04711/0xa00000
[   42.079180] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input9
[   44.508866] iwl3945 0000:03:00.0: firmware: requesting iwlwifi-3945-2.ucode
[   44.529772] iwl3945 0000:03:00.0: loaded firmware version 15.32.2.9
[   44.616660] Registered led device: iwl-phy0::radio
[   44.616821] Registered led device: iwl-phy0::assoc
[   44.616880] Registered led device: iwl-phy0::RX
[   44.616937] Registered led device: iwl-phy0::TX
[   44.638604] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   46.430603] r8169: eth0: link down
[   46.431060] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   46.647730] Registered led device: iwl-phy0::radio
[   46.647868] Registered led device: iwl-phy0::assoc
[   46.647908] Registered led device: iwl-phy0::RX
[   46.647944] Registered led device: iwl-phy0::TX
[   46.669554] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   48.552133] wlan0: authenticate with AP 00:13:d4:d6:22:c6
[   48.554233] wlan0: authenticated
[   48.554246] wlan0: associate with AP 00:13:d4:d6:22:c6
[   48.556811] wlan0: RX AssocResp from 00:13:d4:d6:22:c6 (capab=0x411 status=0 aid=4)
[   48.556825] wlan0: associated
[   48.559424] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   59.520040] wlan0: no IPv6 routers present
[  737.777086] CE: hpet increasing min_delta_ns to 15000 nsec
[  810.213109] CE: hpet increasing min_delta_ns to 22500 nsec
```

---

### Post by danq989 on 2009-11-10
Many users of netbooks with SuperTalent SSDs are experiencing this issue under 9.10. Since the same HW is working fine for most in 9.l04, it appears to be a bug (possibly in the chipset ATA driver).

See [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/445852](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/445852)

---

### Post by rifferte on 2010-02-02
Any updates on this one? I saw a work around - but does that limit the system in any way? I have a ST 32GB in my mini now and I really would like to replace Windows with Ubuntu but this is scaring me off!

---

### Post by redDEADresolve on 2010-02-02
> **rifferte said:**
> Any updates on this one? I saw a work around - but does that limit the system in any way? I have a ST 32GB in my mini now and I really would like to replace Windows with Ubuntu but this is scaring me off!

There are other distro that run fine on the SuperTalent SSD.

Maybe try Debian.

---

### Post by Digikid on 2010-02-02
Ubuntu is BASED on Debian so why would using Debian be any different?

---

### Post by redDEADresolve on 2010-02-02
> **Digikid said:**
> Ubuntu is BASED on Debian so why would using Debian be any different?

Because it's a bug specifically in the Ubuntu Kernel being used in Karmic. 

It's not present in any of the Debian Testing Kernel or in Debian Unstable Kernel, which is the version Ubuntu is based off of.

I've switched to Debian Testing and I boot up within 12 seconds and I don't have any errors.

[http://www.reddeadresolve.com/2009/12/installing-debian-squeeze.html](http://www.reddeadresolve.com/2009/12/installing-debian-squeeze.html)

---

### Post by GenericAnimeBoy on 2010-02-24
The bug is not in the Ubuntu Karmic kernel, it is in libatasmart.  Switching to another distro will not necessarily fix the problem, as several other distros use libatasmart.  There is an active bug report in launchpad [here]("https://bugs.launchpad.net/bugs/445852") with more information.

It is VERY IMPORTANT if you have an affected SSD to either change to a distro that does not include libatasmart or to disable the problem utility via the workaround outlined in the bug report linked above.  Allowing the bug to continue unchecked may result in data loss or total hardware failure (your SSD hardware could be rendered unusable).

---

