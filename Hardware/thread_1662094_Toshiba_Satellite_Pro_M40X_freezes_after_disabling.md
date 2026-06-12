---
title: "Toshiba Satellite Pro M40X freezes after disabling IRQ #18"
date: 2011-01-07
forum: Hardware
---

### Post by zensys on 2011-01-07
I have a Toshiba Satellite Pro M40X with Ubuntu 10.10 and the latest (1.60) BIOS. Since 10.04 I get a message "disabling IRQ #18" where booting stops for a few seconds but afterwards booted correctly. Now (some time had passed already after upgrading to 10.010) it boots into the desktop but then freezes totally (no mouse, no keyboard, no touch pad) at some keyring password dialog.

Previous kernels, recovery modes and the memtest work neither but I can boot with a 9.10 live CD (to get the log files).

Any help to prevent me throwing away this 5 year old laptop is greatly appreciated.

Here is my dmesg (apologies if it is too long):

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
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
[    0.000000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000dc000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000005f6e0000 (usable)
[    0.000000]  BIOS-e820: 000000005f6e0000 - 000000005f6ea000 (ACPI data)
[    0.000000]  BIOS-e820: 000000005f6ea000 - 000000005f700000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000005f700000 - 0000000060000000 (reserved)
[    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0006000 (reserved)
[    0.000000]  BIOS-e820: 00000000f0008000 - 00000000f000c000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed20000 - 00000000fed90000 (reserved)
[    0.000000]  BIOS-e820: 00000000ff000000 - 0000000100000000 (reserved)
[    0.000000] DMI present.
[    0.000000] last_pfn = 0x5f6e0 max_arch_pfn = 0x100000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-CFFFF write-protect
[    0.000000]   D0000-E3FFF uncachable
[    0.000000]   E4000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000 mask FC0000000 write-back
[    0.000000]   1 base 040000000 mask FE0000000 write-back
[    0.000000]   2 base 05F700000 mask FFFF00000 uncachable
[    0.000000]   3 base 05F800000 mask FFF800000 uncachable
[    0.000000]   4 disabled
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] PAT not supported by CPU.
[    0.000000] e820 update range: 0000000000002000 - 0000000000006000 (usable) ==> (reserved)
[    0.000000] Scanning 1 areas for low memory corruption
[    0.000000] modified physical RAM map:
[    0.000000]  modified: 0000000000000000 - 0000000000002000 (usable)
[    0.000000]  modified: 0000000000002000 - 0000000000006000 (reserved)
[    0.000000]  modified: 0000000000006000 - 000000000009f800 (usable)
[    0.000000]  modified: 000000000009f800 - 00000000000a0000 (reserved)
[    0.000000]  modified: 00000000000dc000 - 0000000000100000 (reserved)
[    0.000000]  modified: 0000000000100000 - 000000005f6e0000 (usable)
[    0.000000]  modified: 000000005f6e0000 - 000000005f6ea000 (ACPI data)
[    0.000000]  modified: 000000005f6ea000 - 000000005f700000 (ACPI NVS)
[    0.000000]  modified: 000000005f700000 - 0000000060000000 (reserved)
[    0.000000]  modified: 00000000e0000000 - 00000000f0006000 (reserved)
[    0.000000]  modified: 00000000f0008000 - 00000000f000c000 (reserved)
[    0.000000]  modified: 00000000fed20000 - 00000000fed90000 (reserved)
[    0.000000]  modified: 00000000ff000000 - 0000000100000000 (reserved)
[    0.000000] initial memory mapped : 0 - 00c00000
[    0.000000] init_memory_mapping: 0000000000000000-00000000377fe000
[    0.000000] Using x86 segment limits to approximate NX protection
[    0.000000]  0000000000 - 0000400000 page 4k
[    0.000000]  0000400000 - 0037400000 page 2M
[    0.000000]  0037400000 - 00377fe000 page 4k
[    0.000000] kernel direct mapping tables up to 377fe000 @ 7000-c000
[    0.000000] RAMDISK: 5f132000 - 5f6af098
[    0.000000] Allocated new RAMDISK: 008ad000 - 00e2a098
[    0.000000] Move RAMDISK from 000000005f132000 - 000000005f6af097 to 008ad000 - 00e2a097
[    0.000000] ACPI: RSDP 000f6b70 00014 (v00 TOSCPL)
[    0.000000] ACPI: RSDT 5f6e383f 00044 (v01 TOSCPL   RSDT   06040000  LTP 00000000)
[    0.000000] ACPI: APIC 5f6e9e88 00068 (v01 INTEL  ALVISO   06040000 LOHR 0000005F)
[    0.000000] ACPI: FACP 5f6e9ef0 00074 (v01 TOSCPL ALVISO   06040000 LOHR 00000032)
[    0.000000] ACPI: DSDT 5f6e495f 05529 (v01 TOSCPL ALVISO   06040000 MSFT 0100000E)
[    0.000000] ACPI: FACS 5f6fafc0 00040
[    0.000000] ACPI: BOOT 5f6e9fd8 00028 (v01 PTLTD  $SBFTBL$ 06040000  LTP 00000001)
[    0.000000] ACPI: MCFG 5f6e9f9c 0003C (v01 INTEL  ALVISO   06040000 LOHR 0000005F)
[    0.000000] ACPI: SSDT 5f6e430c 0064F (v01 SataRe  SataPri 00001000 INTL 20030224)
[    0.000000] ACPI: SSDT 5f6e3c7a 00692 (v01 SataRe  SataSec 00001000 INTL 20030224)
[    0.000000] ACPI: SSDT 5f6e3a9c 001DE (v01  PmRef  Cpu0Cst 00003001 INTL 20030224)
[    0.000000] ACPI: SSDT 5f6e3883 00219 (v01  PmRef    CpuPm 00003000 INTL 20030224)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] 638MB HIGHMEM available.
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
[    0.000000]   #5 [00008a9000 - 00008ac0f8]              BRK ==> [00008a9000 - 00008ac0f8]
[    0.000000]   #6 [0000007000 - 0000008000]          PGTABLE ==> [0000007000 - 0000008000]
[    0.000000]   #7 [00008ad000 - 0000e2a098]      NEW RAMDISK ==> [00008ad000 - 0000e2a098]
[    0.000000]   #8 [0000008000 - 000000f000]          BOOTMAP ==> [0000008000 - 000000f000]
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000000 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x000377fe
[    0.000000]   HighMem  0x000377fe -> 0x0005f6e0
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[3] active PFN ranges
[    0.000000]     0: 0x00000000 -> 0x00000002
[    0.000000]     0: 0x00000006 -> 0x0000009f
[    0.000000]     0: 0x00000100 -> 0x0005f6e0
[    0.000000] On node 0 totalpages: 390779
[    0.000000] free_area_init_node: node 0, pgdat c0784900, node_mem_map c1000000
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3963 pages, LIFO batch:0
[    0.000000]   Normal zone: 1744 pages used for memmap
[    0.000000]   Normal zone: 221486 pages, LIFO batch:31
[    0.000000]   HighMem zone: 1278 pages used for memmap
[    0.000000]   HighMem zone: 162276 pages, LIFO batch:31
[    0.000000] Using APIC driver default
[    0.000000] ACPI: PM-Timer IO Port: 0x1008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] disabled)
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
[    0.000000] SMP: Allowing 2 CPUs, 1 hotplug CPUs
[    0.000000] nr_irqs_gsi: 24
[    0.000000] PM: Registered nosave memory: 0000000000002000 - 0000000000006000
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000dc000
[    0.000000] PM: Registered nosave memory: 00000000000dc000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 60000000 (gap: 60000000:80000000)
[    0.000000] NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:2 nr_node_ids:1
[    0.000000] PERCPU: Embedded 14 pages at c1bf7000, static data 35612 bytes
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 387725
[    0.000000] Kernel command line: BOOT_IMAGE=/casper/vmlinuz file=/cdrom/preseed/ubuntu.seed boot=casper initrd=/casper/initrd.lz quiet splash --
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] allocated 7817600 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] Initializing HighMem for node 0 (000377fe:0005f6e0)
[    0.000000] Memory: 1527876k/1563520k available (4565k kernel code, 34304k reserved, 2143k data, 540k init, 654216k highmem)
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
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 1496.266 MHz processor.
[    0.002074] Console: colour VGA+ 80x25
[    0.002080] console [tty0] enabled
[    0.004014] Calibrating delay loop (skipped), value calculated using timer frequency.. 2992.53 BogoMIPS (lpj=5985064)
[    0.004055] Security Framework initialized
[    0.004090] AppArmor: AppArmor initialized
[    0.004103] Mount-cache hash table entries: 512
[    0.004329] Initializing cgroup subsys ns
[    0.004337] Initializing cgroup subsys cpuacct
[    0.004343] Initializing cgroup subsys memory
[    0.004353] Initializing cgroup subsys freezer
[    0.004356] Initializing cgroup subsys net_cls
[    0.004380] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.004384] CPU: L2 cache: 1024K
[    0.004390] mce: CPU supports 5 MCE banks
[    0.004402] CPU0: Thermal monitoring enabled (TM1)
[    0.004417] Performance Counters: p6 PMU driver.
[    0.004427] ... version:                 0
[    0.004429] ... bit width:               32
[    0.004432] ... generic counters:        2
[    0.004434] ... value mask:              00000000ffffffff
[    0.004437] ... max period:              000000007fffffff
[    0.004440] ... fixed-purpose counters:  0
[    0.004442] ... counter mask:            0000000000000003
[    0.004449] Checking 'hlt' instruction... OK.
[    0.021073] SMP alternatives: switching to UP code
[    0.028007] ACPI: Core revision 20090521
[    0.044483] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.085102] CPU0: Intel(R) Celeron(R) M processor         1.50GHz stepping 08
[    0.088001] Brought up 1 CPUs
[    0.088001] Total of 1 processors activated (2992.53 BogoMIPS).
[    0.088001] CPU0 attaching NULL sched-domain.
[    0.088001] Booting paravirtualized kernel on bare hardware
[    0.088001] regulator: core version 0.5
[    0.088001] Time: 20:26:16  Date: 01/07/11
[    0.088001] NET: Registered protocol family 16
[    0.088001] EISA bus registered
[    0.088001] ACPI: bus type pci registered
[    0.088001] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 255
[    0.088001] PCI: MCFG area at e0000000 reserved in E820
[    0.088001] PCI: Using MMCONFIG for extended config space
[    0.088001] PCI: Using configuration type 1 for base access
[    0.088001] bio: create slab <bio-0> at 0
[    0.088001] ACPI: EC: Look up EC in DSDT
[    0.090537] ACPI: Interpreter enabled
[    0.090545] ACPI: (supports S0 S3 S4 S5)
[    0.090574] ACPI: Using IOAPIC for interrupt routing
[    0.091412] [Firmware Bug]: ACPI: ACPI brightness control misses _BQC function
[    0.132699] ACPI: EC: GPE = 0x1d, I/O: command/status = 0x66, data = 0x62
[    0.132703] ACPI: EC: driver started in poll mode
[    0.133153] ACPI: No dock devices found.
[    0.133861] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.133973] pci 0000:00:02.0: reg 10 32bit mmio: [0xb0080000-0xb00fffff]
[    0.133980] pci 0000:00:02.0: reg 14 io port: [0x1800-0x1807]
[    0.133986] pci 0000:00:02.0: reg 18 32bit mmio: [0xc0000000-0xcfffffff]
[    0.133993] pci 0000:00:02.0: reg 1c 32bit mmio: [0xb0000000-0xb003ffff]
[    0.134033] pci 0000:00:02.1: reg 10 32bit mmio: [0x000000-0x07ffff]
[    0.134156] pci 0000:00:1d.0: reg 20 io port: [0x1820-0x183f]
[    0.134224] pci 0000:00:1d.1: reg 20 io port: [0x1840-0x185f]
[    0.134292] pci 0000:00:1d.2: reg 20 io port: [0x1860-0x187f]
[    0.134360] pci 0000:00:1d.3: reg 20 io port: [0x1880-0x189f]
[    0.134438] pci 0000:00:1d.7: reg 10 32bit mmio: [0xb0040000-0xb00403ff]
[    0.134505] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
[    0.134512] pci 0000:00:1d.7: PME# disabled
[    0.134626] pci 0000:00:1e.2: reg 10 io port: [0x1c00-0x1cff]
[    0.134636] pci 0000:00:1e.2: reg 14 io port: [0x18c0-0x18ff]
[    0.134645] pci 0000:00:1e.2: reg 18 32bit mmio: [0xb0040800-0xb00409ff]
[    0.134655] pci 0000:00:1e.2: reg 1c 32bit mmio: [0xb0040400-0xb00404ff]
[    0.134696] pci 0000:00:1e.2: PME# supported from D0 D3hot D3cold
[    0.134702] pci 0000:00:1e.2: PME# disabled
[    0.134745] pci 0000:00:1e.3: reg 10 io port: [0x2400-0x24ff]
[    0.134755] pci 0000:00:1e.3: reg 14 io port: [0x2000-0x207f]
[    0.134808] pci 0000:00:1e.3: PME# supported from D0 D3hot D3cold
[    0.134813] pci 0000:00:1e.3: PME# disabled
[    0.134911] pci 0000:00:1f.0: Force enabled HPET at 0xfed00000
[    0.134921] pci 0000:00:1f.0: quirk: region 1000-107f claimed by ICH6 ACPI/GPIO/TCO
[    0.134926] pci 0000:00:1f.0: quirk: region 1180-11bf claimed by ICH6 GPIO
[    0.134977] pci 0000:00:1f.2: reg 10 io port: [0x00-0x07]
[    0.134987] pci 0000:00:1f.2: reg 14 io port: [0x00-0x03]
[    0.134996] pci 0000:00:1f.2: reg 18 io port: [0x00-0x07]
[    0.135005] pci 0000:00:1f.2: reg 1c io port: [0x00-0x03]
[    0.135015] pci 0000:00:1f.2: reg 20 io port: [0x18b0-0x18bf]
[    0.135052] pci 0000:00:1f.2: PME# supported from D3hot
[    0.135058] pci 0000:00:1f.2: PME# disabled
[    0.135126] pci 0000:00:1f.3: reg 20 io port: [0x20a0-0x20bf]
[    0.135214] pci 0000:06:01.0: reg 10 io port: [0x3000-0x30ff]
[    0.135225] pci 0000:06:01.0: reg 14 32bit mmio: [0xb0116000-0xb01160ff]
[    0.135291] pci 0000:06:01.0: supports D1 D2
[    0.135294] pci 0000:06:01.0: PME# supported from D1 D2 D3hot D3cold
[    0.135300] pci 0000:06:01.0: PME# disabled
[    0.135353] pci 0000:06:02.0: reg 10 32bit mmio: [0xb0100000-0xb010ffff]
[    0.135478] pci 0000:06:04.0: reg 10 32bit mmio: [0xb0117000-0xb0117fff]
[    0.135508] pci 0000:06:04.0: supports D1 D2
[    0.135511] pci 0000:06:04.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.135518] pci 0000:06:04.0: PME# disabled
[    0.135572] pci 0000:06:04.2: reg 10 32bit mmio: [0xb0116800-0xb0116fff]
[    0.135584] pci 0000:06:04.2: reg 14 32bit mmio: [0xb0110000-0xb0113fff]
[    0.135655] pci 0000:06:04.2: supports D1 D2
[    0.135657] pci 0000:06:04.2: PME# supported from D0 D1 D2 D3hot
[    0.135664] pci 0000:06:04.2: PME# disabled
[    0.135717] pci 0000:06:04.3: reg 10 32bit mmio: [0xb0114000-0xb0115fff]
[    0.135790] pci 0000:06:04.3: supports D1 D2
[    0.135793] pci 0000:06:04.3: PME# supported from D0 D1 D2 D3hot
[    0.135800] pci 0000:06:04.3: PME# disabled
[    0.135851] pci 0000:06:04.4: reg 10 32bit mmio: [0xb0118400-0xb01184ff]
[    0.135862] pci 0000:06:04.4: reg 14 32bit mmio: [0xb0118000-0xb01180ff]
[    0.135873] pci 0000:06:04.4: reg 18 32bit mmio: [0xb0116400-0xb01164ff]
[    0.135932] pci 0000:06:04.4: supports D1 D2
[    0.135935] pci 0000:06:04.4: PME# supported from D0 D1 D2 D3hot
[    0.135941] pci 0000:06:04.4: PME# disabled
[    0.136012] pci 0000:00:1e.0: transparent bridge
[    0.136018] pci 0000:00:1e.0: bridge io port: [0x3000-0x3fff]
[    0.136024] pci 0000:00:1e.0: bridge 32bit mmio: [0xb0100000-0xb01fffff]
[    0.136067] pci_bus 0000:00: on NUMA node 0
[    0.136075] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.136310] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIB._PRT]
[    0.142104] ACPI: PCI Interrupt Link [LNKA] (IRQs 1 3 4 5 6 7 *10 12 14 15)
[    0.142236] ACPI: PCI Interrupt Link [LNKB] (IRQs 1 3 4 5 6 7 11 12 14 15) *10
[    0.142363] ACPI: PCI Interrupt Link [LNKC] (IRQs 1 3 4 5 6 7 10 12 14 15) *11
[    0.142488] ACPI: PCI Interrupt Link [LNKD] (IRQs 1 3 4 5 6 7 *11 12 14 15)
[    0.142614] ACPI: PCI Interrupt Link [LNKE] (IRQs 1 3 4 5 6 7 10 12 14 15) *11
[    0.142739] ACPI: PCI Interrupt Link [LNKF] (IRQs 1 3 4 5 6 7 *11 12 14 15)
[    0.142864] ACPI: PCI Interrupt Link [LNKG] (IRQs 1 3 4 5 6 7 10 12 14 15) *11
[    0.142995] ACPI: PCI Interrupt Link [LNKH] (IRQs 1 3 4 5 6 7 *11 12 14 15)
[    0.143240] SCSI subsystem initialized
[    0.143314] libata version 3.00 loaded.
[    0.143420] usbcore: registered new interface driver usbfs
[    0.143447] usbcore: registered new interface driver hub
[    0.143485] usbcore: registered new device driver usb
[    0.143653] ACPI: WMI: Mapper loaded
[    0.143656] PCI: Using ACPI for IRQ routing
[    0.143869] Bluetooth: Core ver 2.15
[    0.143905] NET: Registered protocol family 31
[    0.143908] Bluetooth: HCI device and connection manager initialized
[    0.143912] Bluetooth: HCI socket layer initialized
[    0.143915] NetLabel: Initializing
[    0.143917] NetLabel:  domain hash size = 128
[    0.143919] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.143938] NetLabel:  unlabeled traffic allowed by default
[    0.144125] hpet clockevent registered
[    0.144130] HPET: 3 timers in total, 0 timers will be used for per-cpu timer
[    0.144139] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[    0.144145] hpet0: 3 comparators, 64-bit 14.318180 MHz counter
[    0.150440] pnp: PnP ACPI init
[    0.150485] ACPI: bus type pnp registered
[    0.172163] pnp: PnP ACPI: found 9 devices
[    0.172169] ACPI: ACPI bus type pnp unregistered
[    0.172175] PnPBIOS: Disabled by ACPI PNP
[    0.172192] system 00:01: ioport range 0xfe00-0xfe7f has been reserved
[    0.172196] system 00:01: ioport range 0xfe80-0xfeff has been reserved
[    0.172200] system 00:01: ioport range 0xff00-0xff7f has been reserved
[    0.172205] system 00:01: iomem range 0xe0000000-0xefffffff has been reserved
[    0.172209] system 00:01: iomem range 0xf0000000-0xf0003fff has been reserved
[    0.172214] system 00:01: iomem range 0xf0004000-0xf0004fff has been reserved
[    0.172218] system 00:01: iomem range 0xf0005000-0xf0005fff has been reserved
[    0.172222] system 00:01: iomem range 0xf0008000-0xf000bfff has been reserved
[    0.172226] system 00:01: iomem range 0xfed20000-0xfed8ffff has been reserved
[    0.172235] system 00:05: ioport range 0x800-0x80f has been reserved
[    0.172239] system 00:05: ioport range 0x1000-0x107f has been reserved
[    0.172243] system 00:05: ioport range 0x1180-0x11bf has been reserved
[    0.172248] system 00:05: ioport range 0x1640-0x164f has been reserved
[    0.207002] AppArmor: AppArmor Filesystem Enabled
[    0.207049] pci 0000:06:04.0: CardBus bridge, secondary bus 0000:07
[    0.207053] pci 0000:06:04.0:   IO window: 0x003400-0x0034ff
[    0.207063] pci 0000:06:04.0:   IO window: 0x003800-0x0038ff
[    0.207070] pci 0000:06:04.0:   PREFETCH window: 0x60000000-0x63ffffff
[    0.207077] pci 0000:06:04.0:   MEM window: 0x68000000-0x6bffffff
[    0.207085] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:06
[    0.207090] pci 0000:00:1e.0:   IO window: 0x3000-0x3fff
[    0.207097] pci 0000:00:1e.0:   MEM window: 0xb0100000-0xb01fffff
[    0.207104] pci 0000:00:1e.0:   PREFETCH window: 0x60000000-0x63ffffff
[    0.207121] pci 0000:00:1e.0: setting latency timer to 64
[    0.207136]   alloc irq_desc for 16 on node -1
[    0.207140]   alloc kstat_irqs on node -1
[    0.207148] pci 0000:06:04.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.207157] pci_bus 0000:00: resource 0 io:  [0x00-0xffff]
[    0.207161] pci_bus 0000:00: resource 1 mem: [0x000000-0xffffffff]
[    0.207165] pci_bus 0000:06: resource 0 io:  [0x3000-0x3fff]
[    0.207169] pci_bus 0000:06: resource 1 mem: [0xb0100000-0xb01fffff]
[    0.207173] pci_bus 0000:06: resource 2 pref mem [0x60000000-0x63ffffff]
[    0.207176] pci_bus 0000:06: resource 3 io:  [0x00-0xffff]
[    0.207180] pci_bus 0000:06: resource 4 mem: [0x000000-0xffffffff]
[    0.207184] pci_bus 0000:07: resource 0 io:  [0x3400-0x34ff]
[    0.207188] pci_bus 0000:07: resource 1 io:  [0x3800-0x38ff]
[    0.207191] pci_bus 0000:07: resource 2 pref mem [0x60000000-0x63ffffff]
[    0.207195] pci_bus 0000:07: resource 3 mem: [0x68000000-0x6bffffff]
[    0.207246] NET: Registered protocol family 2
[    0.207376] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.207795] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.209207] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.210082] TCP: Hash tables configured (established 131072 bind 65536)
[    0.210090] TCP reno registered
[    0.210298] NET: Registered protocol family 1
[    0.210405] Trying to unpack rootfs image as initramfs...
[    0.648012] Switched to high resolution mode on CPU 0
[    2.274249] Freeing initrd memory: 5620k freed
[    2.280495] Simple Boot Flag at 0x36 set to 0x1
[    2.280623] cpufreq-nforce2: No nForce2 chipset.
[    2.280667] Scanning for low memory corruption every 60 seconds
[    2.280842] audit: initializing netlink socket (disabled)
[    2.280871] type=2000 audit(1294431978.280:1): initialized
[    2.292732] highmem bounce pool size: 64 pages
[    2.292742] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    2.294666] VFS: Disk quotas dquot_6.5.2
[    2.294743] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    2.295469] fuse init (API version 7.12)
[    2.295583] msgmni has been set to 1719
[    2.295840] alg: No test for stdrng (krng)
[    2.295856] io scheduler noop registered
[    2.295859] io scheduler anticipatory registered
[    2.295862] io scheduler deadline registered
[    2.295920] io scheduler cfq registered (default)
[    2.295941] pci 0000:00:02.0: Boot video device
[    2.296175] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    2.296208] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    2.296446] ACPI: AC Adapter [ACAD] (on-line)
[    2.296564] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input0
[    2.296569] ACPI: Power Button [PWRF]
[    2.296639] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input1
[    2.296685] ACPI: Lid Switch [LID0]
[    2.296740] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input2
[    2.296744] ACPI: Power Button [PWRB]
[    2.297221] Marking TSC unstable due to TSC halts in idle
[    2.297247] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[    2.297280] processor LNXCPU:00: registered as cooling_device0
[    2.316270] isapnp: Scanning for PnP cards...
[    2.409704] ACPI: Battery Slot [BAT1] (battery present)
[    2.671062] isapnp: No Plug & Play device found
[    2.672464] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    2.672900]   alloc irq_desc for 20 on node -1
[    2.672904]   alloc kstat_irqs on node -1
[    2.672914] serial 0000:00:1e.3: PCI INT B -> GSI 20 (level, low) -> IRQ 20
[    2.672923] serial 0000:00:1e.3: PCI INT B disabled
[    2.674132] brd: module loaded
[    2.674725] loop: module loaded
[    2.674822] input: Macintosh mouse button emulation as /devices/virtual/input/input3
[    2.674922] ahci 0000:00:1f.2: version 3.0
[    2.674936]   alloc irq_desc for 19 on node -1
[    2.674938]   alloc kstat_irqs on node -1
[    2.674945] ahci 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    2.674959] ahci 0000:00:1f.2: PCI INT B disabled
[    2.674965] ahci: probe of 0000:00:1f.2 failed with error -22
[    2.675021] ata_piix 0000:00:1f.2: version 2.13
[    2.675030] ata_piix 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    2.675039] ata_piix 0000:00:1f.2: MAP [ P0 P2 IDE IDE ]
[    2.675091] ata_piix 0000:00:1f.2: setting latency timer to 64
[    2.675208] scsi0 : ata_piix
[    2.675323] scsi1 : ata_piix
[    2.676658] ata1: SATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0x18b0 irq 14
[    2.676663] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x18b8 irq 15
[    2.677765] Fixed MDIO Bus: probed
[    2.677810] PPP generic driver version 2.4.2
[    2.677940] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    2.677965]   alloc irq_desc for 23 on node -1
[    2.677968]   alloc kstat_irqs on node -1
[    2.677977] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    2.677999] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    2.678004] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    2.678070] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 1
[    2.681983] ehci_hcd 0000:00:1d.7: debug port 1
[    2.681992] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
[    2.682281] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xb0040000
[    2.696022] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    2.696136] usb usb1: configuration #1 chosen from 1 choice
[    2.696183] hub 1-0:1.0: USB hub found
[    2.696194] hub 1-0:1.0: 8 ports detected
[    2.696284] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    2.696306] uhci_hcd: USB Universal Host Controller Interface driver
[    2.696347] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    2.696356] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    2.696360] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    2.696400] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    2.696430] uhci_hcd 0000:00:1d.0: irq 23, io base 0x00001820
[    2.696537] usb usb2: configuration #1 chosen from 1 choice
[    2.696571] hub 2-0:1.0: USB hub found
[    2.696595] hub 2-0:1.0: 2 ports detected
[    2.696651] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    2.696659] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    2.696664] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    2.696703] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3
[    2.696745] uhci_hcd 0000:00:1d.1: irq 19, io base 0x00001840
[    2.696846] usb usb3: configuration #1 chosen from 1 choice
[    2.696879] hub 3-0:1.0: USB hub found
[    2.696888] hub 3-0:1.0: 2 ports detected
[    2.696943]   alloc irq_desc for 18 on node -1
[    2.696946]   alloc kstat_irqs on node -1
[    2.696953] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    2.696961] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    2.696965] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    2.697013] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4
[    2.697050] uhci_hcd 0000:00:1d.2: irq 18, io base 0x00001860
[    2.697150] usb usb4: configuration #1 chosen from 1 choice
[    2.697184] hub 4-0:1.0: USB hub found
[    2.697192] hub 4-0:1.0: 2 ports detected
[    2.697252] uhci_hcd 0000:00:1d.3: PCI INT D -> GSI 16 (level, low) -> IRQ 16
[    2.697260] uhci_hcd 0000:00:1d.3: setting latency timer to 64
[    2.697264] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[    2.697300] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 5
[    2.697337] uhci_hcd 0000:00:1d.3: irq 16, io base 0x00001880
[    2.697432] usb usb5: configuration #1 chosen from 1 choice
[    2.697465] hub 5-0:1.0: USB hub found
[    2.697473] hub 5-0:1.0: 2 ports detected
[    2.697592] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    2.697912] i8042.c: Detected active multiplexing controller, rev 1.1.
[    2.697990] serio: i8042 KBD port at 0x60,0x64 irq 1
[    2.698000] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[    2.698004] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[    2.698008] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[    2.698012] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[    2.698082] mice: PS/2 mouse device common for all mice
[    2.698228] rtc_cmos 00:06: RTC can wake from S4
[    2.698273] rtc_cmos 00:06: rtc core: registered rtc_cmos as rtc0
[    2.698308] rtc0: alarms up to one month, y3k, 242 bytes nvram, hpet irqs
[    2.698449] device-mapper: uevent: version 1.0.3
[    2.698574] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: [email]dm-devel@redhat.com[/email]
[    2.698674] device-mapper: multipath: version 1.1.0 loaded
[    2.698678] device-mapper: multipath round-robin: version 1.0.0 loaded
[    2.698840] EISA: Probing bus 0 at eisa.0
[    2.698850] Cannot allocate resource for EISA slot 1
[    2.698853] Cannot allocate resource for EISA slot 2
[    2.698856] Cannot allocate resource for EISA slot 3
[    2.698879] EISA: Detected 0 cards.
[    2.698993] cpuidle: using governor ladder
[    2.699085] cpuidle: using governor menu
[    2.699718] TCP cubic registered
[    2.699920] NET: Registered protocol family 10
[    2.700490] lo: Disabled Privacy Extensions
[    2.700874] NET: Registered protocol family 17
[    2.700898] Bluetooth: L2CAP ver 2.13
[    2.700900] Bluetooth: L2CAP socket layer initialized
[    2.700904] Bluetooth: SCO (Voice Link) ver 0.6
[    2.700906] Bluetooth: SCO socket layer initialized
[    2.700962] Bluetooth: RFCOMM TTY layer initialized
[    2.700966] Bluetooth: RFCOMM socket layer initialized
[    2.700968] Bluetooth: RFCOMM ver 1.11
[    2.701009] Using IPI No-Shortcut mode
[    2.701106] PM: Resume from disk failed.
[    2.701124] registered taskstats version 1
[    2.701272]   Magic number: 11:988:446
[    2.701396] rtc_cmos 00:06: setting system clock to 2011-01-07 20:26:19 UTC (1294431979)
[    2.701400] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    2.701403] EDD information not available.
[    2.703053] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input4
[    2.844651] ata2.00: ATAPI: HL-DT-ST DVDRAM GMA-4080N, 0V35, max UDMA/33
[    2.846678] ata1.00: ATA-8: SAMSUNG HM160HC, LQ100-10, max UDMA/100
[    2.846682] ata1.00: 312581808 sectors, multi 16: LBA48 
[    2.846699] ata1.00: applying bridge limits
[    2.860560] ata2.00: configured for UDMA/33
[    2.862498] ata1.00: configured for UDMA/100
[    2.862675] scsi 0:0:0:0: Direct-Access     ATA      SAMSUNG HM160HC  LQ10 PQ: 0 ANSI: 5
[    2.862843] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    2.862896] sd 0:0:0:0: [sda] 312581808 512-byte logical blocks: (160 GB/149 GiB)
[    2.862957] sd 0:0:0:0: [sda] Write Protect is off
[    2.862961] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    2.862992] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.863178]  sda:
[    2.867538] scsi 1:0:0:0: CD-ROM            HL-DT-ST DVDRAM GMA-4080N 0V35 PQ: 0 ANSI: 5
[    2.871716] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[    2.871721] Uniform CD-ROM driver Revision: 3.20
[    2.871835] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    2.871887] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    2.890088]  sda1 sda2 sda3 sda4
[    2.919705] sd 0:0:0:0: [sda] Attached SCSI disk
[    2.919726] Freeing unused kernel memory: 540k freed
[    2.920167] Write protecting the kernel text: 4568k
[    2.920215] Write protecting the kernel read-only data: 1836k
[    3.166827] Linux agpgart interface v0.103
[    3.171492] agpgart-intel 0000:00:00.0: Intel 915GM Chipset
[    3.171855] agpgart-intel 0000:00:00.0: detected 7932K stolen memory
[    3.196127] usb 3-1: new low speed USB device using uhci_hcd and address 2
[    3.209502] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xc0000000
[    3.301838] ohci1394 0000:06:04.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    3.307347] <6>8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)
[    3.351962] [drm] Initialized drm 1.1.0 20060810
[    3.357826] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[11]  MMIO=[b0116800-b0116fff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[    3.357993] 8139cp 0000:06:01.0: This (id 10ec:8139 rev 10) is not an 8139C+ compatible chip, use 8139too
[    3.372196] i915 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    3.372208] i915 0000:00:02.0: setting latency timer to 64
[    3.382126] 8139too Fast Ethernet driver 0.9.28
[    3.382225]   alloc irq_desc for 21 on node -1
[    3.382229]   alloc kstat_irqs on node -1
[    3.382238] 8139too 0000:06:01.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[    3.383683] eth0: RealTek RTL8139 at 0x3000, 00:0f:b0:8e:df:46, IRQ 21
[    3.776261] [drm] DAC-6: set mode 640x480 0
[    3.778489] usb 3-1: configuration #1 chosen from 1 choice
[    3.792178] usbcore: registered new interface driver hiddev
[    3.976351] input: USB Optical Wheel Mouse as /devices/pci0000:00/0000:00:1d.1/usb3/3-1/3-1:1.0/input/input5
[    3.976465] generic-usb 0003:04FC:0005.0001: input,hidraw0: USB HID v1.10 Mouse [USB Optical Wheel Mouse] on usb-0000:00:1d.1-1/input0
[    3.976492] usbcore: registered new interface driver usbhid
[    3.976496] usbhid: v2.6:USB HID core driver
[    4.020267] [drm] TV-14: set mode NTSC 480i 0
[    4.150531] [drm] fb0: inteldrmfb frame buffer device
[    4.150553] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
[    4.218043] render error detected, EIR: 0x00000010
[    4.218048] page table error
[    4.218049]   PGTBL_ER: 0x00000100
[    4.218054] [drm:i915_handle_error] *ERROR* EIR stuck: 0x00000010, masking
[    4.218064] render error detected, EIR: 0x00000010
[    4.218066] page table error
[    4.218068]   PGTBL_ER: 0x00000100
[    4.226351] [drm] LVDS-8: set mode 1280x800 17
[    4.253082] Console: switching to colour frame buffer device 160x50
[    4.551669] xor: automatically using best checksumming function: pIII_sse
[    4.568011]    pIII_sse  :  2230.000 MB/sec
[    4.568016] xor: using function: pIII_sse (2230.000 MB/sec)
[    4.575747] device-mapper: dm-raid45: initialized v0.2594b
[    4.834904] irq 18: nobody cared (try booting with the "irqpoll" option)
[    4.834913] Pid: 393, comm: mount.ntfs Not tainted 2.6.31-14-generic #48-Ubuntu
[    4.834918] Call Trace:
[    4.834933]  [<c056e41c>] ? printk+0x18/0x1c
[    4.834942]  [<c0190ee7>] __report_bad_irq+0x27/0x90
[    4.834948]  [<c018f8fc>] ? handle_IRQ_event+0x4c/0x140
[    4.834952]  [<c01910a0>] note_interrupt+0x150/0x190
[    4.834958]  [<c01915fc>] handle_fasteoi_irq+0xac/0xd0
[    4.834964]  [<c0105a38>] handle_irq+0x18/0x30
[    4.834968]  [<c0104f07>] do_IRQ+0x47/0xc0
[    4.834975]  [<c01e7fd3>] ? sys_pread64+0x63/0x80
[    4.834979]  [<c01039b0>] common_interrupt+0x30/0x40
[    4.834982] handlers:
[    4.834984] [<c040f1c0>] (usb_hcd_irq+0x0/0x70)
[    4.834992] Disabling IRQ #18
[    5.035924] EXT4-fs (sda3): INFO: recovery required on readonly filesystem
[    5.035931] EXT4-fs (sda3): write access will be enabled during recovery
[    5.041806] EXT4-fs (sda3): barriers enabled
[    5.321694] kjournald2 starting: pid 411, dev sda3:8, commit interval 5 seconds
[    5.321722] EXT4-fs (sda3): delayed allocation enabled
[    5.321727] EXT4-fs: file extents enabled
[    5.321820] EXT4-fs: mballoc enabled
[    5.321840] EXT4-fs (sda3): recovery complete
[    5.325483] EXT4-fs (sda3): mounted filesystem with ordered data mode
[    5.339444] EXT4-fs: mballoc: 0 blocks 0 reqs (0 success)
[    5.339449] EXT4-fs: mballoc: 0 extents scanned, 0 goal hits, 0 2^N hits, 0 breaks, 0 lost
[    5.339453] EXT4-fs: mballoc: 0 generated and it took 0
[    5.339456] EXT4-fs: mballoc: 0 preallocated, 0 discarded
[    5.457424] EXT4-fs (sda4): INFO: recovery required on readonly filesystem
[    5.457432] EXT4-fs (sda4): write access will be enabled during recovery
[    5.468587] EXT4-fs (sda4): barriers enabled
[    6.385034] kjournald2 starting: pid 421, dev sda4:8, commit interval 5 seconds
[    6.385064] EXT4-fs (sda4): delayed allocation enabled
[    6.385069] EXT4-fs: file extents enabled
[    6.399462] EXT4-fs: mballoc enabled
[    6.399483] EXT4-fs (sda4): recovery complete
[    6.399832] EXT4-fs (sda4): mounted filesystem with ordered data mode
[    6.425568] EXT4-fs: mballoc: 0 blocks 0 reqs (0 success)
[    6.425574] EXT4-fs: mballoc: 0 extents scanned, 0 goal hits, 0 2^N hits, 0 breaks, 0 lost
[    6.425577] EXT4-fs: mballoc: 0 generated and it took 0
[    6.425580] EXT4-fs: mballoc: 0 preallocated, 0 discarded
[    9.149386] sr 1:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[    9.149395] sr 1:0:0:0: [sr0] Sense Key : Illegal Request [current] 
[    9.149402] Info fld=0x563f2, ILI
[    9.149405] sr 1:0:0:0: [sr0] Add. Sense: Illegal mode for this track
[    9.149415] end_request: I/O error, dev sr0, sector 1413064
[    9.149420] Buffer I/O error on device sr0, logical block 176633
[    9.153892] sr 1:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[    9.153897] sr 1:0:0:0: [sr0] Sense Key : Illegal Request [current] 
[    9.153902] Info fld=0x563f2, ILI
[    9.153905] sr 1:0:0:0: [sr0] Add. Sense: Illegal mode for this track
[    9.153911] end_request: I/O error, dev sr0, sector 1413064
[    9.153915] Buffer I/O error on device sr0, logical block 176633
[    9.159931] sr 1:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[    9.159936] sr 1:0:0:0: [sr0] Sense Key : Illegal Request [current] 
[    9.159941] Info fld=0x563f2, ILI
[    9.159944] sr 1:0:0:0: [sr0] Add. Sense: Illegal mode for this track
[    9.159951] end_request: I/O error, dev sr0, sector 1413064
[    9.159954] Buffer I/O error on device sr0, logical block 176633
[    9.164369] sr 1:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[    9.164374] sr 1:0:0:0: [sr0] Sense Key : Illegal Request [current] 
[    9.164379] Info fld=0x563f2, ILI
[    9.164382] sr 1:0:0:0: [sr0] Add. Sense: Illegal mode for this track
[    9.164388] end_request: I/O error, dev sr0, sector 1413064
[    9.164392] Buffer I/O error on device sr0, logical block 176633
[    9.170514] sr 1:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[    9.170519] sr 1:0:0:0: [sr0] Sense Key : Illegal Request [current] 
[    9.170524] Info fld=0x563f2, ILI
[    9.170526] sr 1:0:0:0: [sr0] Add. Sense: Illegal mode for this track
[    9.170533] end_request: I/O error, dev sr0, sector 1413064
[    9.170537] Buffer I/O error on device sr0, logical block 176633
[    9.175025] sr 1:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[    9.175030] sr 1:0:0:0: [sr0] Sense Key : Illegal Request [current] 
[    9.175035] Info fld=0x563f2, ILI
[    9.175038] sr 1:0:0:0: [sr0] Add. Sense: Illegal mode for this track
[    9.175044] end_request: I/O error, dev sr0, sector 1413064
[    9.175048] Buffer I/O error on device sr0, logical block 176633
[    9.179708] sr 1:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[    9.179713] sr 1:0:0:0: [sr0] Sense Key : Illegal Request [current] 
[    9.179718] Info fld=0x563f2, ILI
[    9.179721] sr 1:0:0:0: [sr0] Add. Sense: Illegal mode for this track
[    9.179728] end_request: I/O error, dev sr0, sector 1413064
[    9.179732] Buffer I/O error on device sr0, logical block 176633
[    9.281842] sr 1:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[    9.281847] sr 1:0:0:0: [sr0] Sense Key : Illegal Request [current] 
[    9.281853] Info fld=0x563f2, ILI
[    9.281855] sr 1:0:0:0: [sr0] Add. Sense: Illegal mode for this track
[    9.281862] end_request: I/O error, dev sr0, sector 1413064
[    9.281866] Buffer I/O error on device sr0, logical block 176633
[    9.286282] sr 1:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[    9.286286] sr 1:0:0:0: [sr0] Sense Key : Illegal Request [current] 
[    9.286292] Info fld=0x563f2, ILI
[    9.286294] sr 1:0:0:0: [sr0] Add. Sense: Illegal mode for this track
[    9.286301] end_request: I/O error, dev sr0, sector 1413064
[    9.286304] Buffer I/O error on device sr0, logical block 176633
[    9.651979] ISO 9660 Extensions: Microsoft Joliet Level 3
[    9.720253] ISO 9660 Extensions: RRIP_1991A
[   10.065574] aufs 2-standalone.tree-30-20090727
[   10.351824] squashfs: version 4.0 (2009/01/31) Phillip Lougher
[  136.292589] Adding 1028152k swap on /dev/sda2.  Priority:-1 extents:1 across:1028152k 
[  138.413791] udev: starting version 147
[  142.903060] intel_rng: FWH not detected
[  143.197005] cfg80211: Calling CRDA to update world regulatory domain
[  143.202462]   alloc irq_desc for 17 on node -1
[  143.202466]   alloc kstat_irqs on node -1
[  143.202477] tifm_7xx1 0000:06:04.3: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[  144.262395] yenta_cardbus 0000:06:04.0: CardBus bridge found [1179:ff00]
[  144.262424] yenta_cardbus 0000:06:04.0: Enabling burst memory read transactions
[  144.262431] yenta_cardbus 0000:06:04.0: Using CSCINT to route CSC interrupts to PCI
[  144.262434] yenta_cardbus 0000:06:04.0: Routing CardBus interrupts to PCI
[  144.262442] yenta_cardbus 0000:06:04.0: TI: mfunc 0x10aa1b22, devctl 0x66
[  144.329729] sdhci: Secure Digital Host Controller Interface driver
[  144.329735] sdhci: Copyright(c) Pierre Ossman
[  144.492688] yenta_cardbus 0000:06:04.0: ISA IRQ mask 0x04f8, PCI irq 16
[  144.492695] yenta_cardbus 0000:06:04.0: Socket status: 30000006
[  144.492701] pci_bus 0000:06: Raising subordinate bus# of parent bus (#06) from #07 to #0a
[  144.492713] yenta_cardbus 0000:06:04.0: pcmcia: parent PCI bridge I/O window: 0x3000 - 0x3fff
[  144.492718] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x3000-0x3fff: clean.
[  144.492997] yenta_cardbus 0000:06:04.0: pcmcia: parent PCI bridge Memory window: 0xb0100000 - 0xb01fffff
[  144.493001] yenta_cardbus 0000:06:04.0: pcmcia: parent PCI bridge Memory window: 0x60000000 - 0x63ffffff
[  144.493783] sdhci-pci 0000:06:04.4: SDHCI controller found [104c:8034] (rev 0)
[  144.493808] sdhci-pci 0000:06:04.4: PCI INT D -> GSI 19 (level, low) -> IRQ 19
[  144.493903] Registered led device: mmc0::
[  144.493958] mmc0: SDHCI controller on PCI [0000:06:04.4] using PIO
[  144.494002] Registered led device: mmc1::
[  144.494030] mmc1: SDHCI controller on PCI [0000:06:04.4] using PIO
[  144.494079] Registered led device: mmc2::
[  144.494107] mmc2: SDHCI controller on PCI [0000:06:04.4] using PIO
[  144.574253] input: PS/2 Mouse as /devices/platform/i8042/serio4/input/input6
[  144.626666] input: AlpsPS/2 ALPS GlidePoint as /devices/platform/i8042/serio4/input/input7
[  145.310324]   alloc irq_desc for 22 on node -1
[  145.310330]   alloc kstat_irqs on node -1
[  145.310341] ath5k 0000:06:02.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[  145.310413] ath5k 0000:06:02.0: registered as 'phy0'
[  145.422008] ath: EEPROM regdomain: 0x64
[  145.422012] ath: EEPROM indicates we should expect a direct regpair map
[  145.422018] ath: Country alpha2 being used: 00
[  145.422020] ath: Regpair used: 0x64
[  146.493424] ip_tables: (C) 2000-2006 Netfilter Core Team
[  146.775220] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x100-0x3af: clean.
[  146.777006] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x3e0-0x4ff: excluding 0x4d0-0x4d7
[  146.777752] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x820-0x8ff: clean.
[  146.778369] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xc00-0xcf7: clean.
[  146.779182] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xa00-0xaff: clean.
[  147.179612] phy0: Selected rate control algorithm 'minstrel'
[  147.180469] ath5k phy0: Atheros AR2414 chip found (MAC: 0x79, PHY: 0x45)
[  147.643302] usplash[316]: segfault at b764314c ip 00717de6 sp bfc7c680 error 6 in libusplash.so.0 (deleted)[6f3000+29000]
[  147.777295] cfg80211: World regulatory domain updated:
[  147.777304] 	(start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[  147.777308] 	(2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  147.777312] 	(2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[  147.777316] 	(2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[  147.777320] 	(5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  147.777323] 	(5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  151.091186] Intel ICH 0000:00:1e.2: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[  151.091248] Intel ICH 0000:00:1e.2: setting latency timer to 64
[  151.924035] intel8x0_measure_ac97_clock: measured 55381 usecs (2668 samples)
[  151.924041] intel8x0: clocking to 48000
[  152.436472] eth0: link down
[  152.457694] ADDRCONF(NETDEV_UP): eth0: link is not ready
[  152.588547] ADDRCONF(NETDEV_UP): wlan0: link is not ready

---

### Post by davidmohammed on 2011-01-07
have you tried grub boot options such as

noapic
nolapic
noacpi

?

---

### Post by IcarusR on 2011-01-07
> irq 18: nobody cared (try booting with the "irqpoll" option)

Have you tried this, as suggested in dmesg ?

---

### Post by zensys on 2011-01-07
Thanks, will try both suggestions and come back here.

But as before I booted perfectly without these options, what would typically be the root cause of this problems: hardware failure, newer kernels too advanced for old BIOS, BIOS corrupted, etc.?

Would reflashing the BIOS stand a chance of solving the problem?

---

### Post by zensys on 2011-01-08
tried both suggestions without success however:

- noapic nolapic noacpi substitutes disabling irq18 for irq10 and freezes before getting to the desktop
- irqpoll supresses disabling irq18 but freezes into the unlock keyring dialog all the same

what about reflashing the BIOS?

---

### Post by zensys on 2011-01-08
forgot to mention that I do succeed booting into windows, so if it is hardware failure apparently it does not affect windows.

---

### Post by davidmohammed on 2011-01-08
having googled around, similar issues about IRQ freezes do point to hardware conflicts of some sort.  Windows may be more tolerant.

I would recommend experimenting with your hardware setup - simplify the hardware to the basics 

e.g. onboard graphics to a monitor - use only opensource graphics drivers instead of the proprietary drivers, fixed keyboard & mouse instead of wireless, remove all usb devices,....  Remove all pmcia cards etc.

Once you can boot without any freezing, start slotting in various hardware until you get your freezes again.

---

