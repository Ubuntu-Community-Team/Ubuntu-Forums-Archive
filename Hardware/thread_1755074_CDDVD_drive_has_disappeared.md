---
title: "CD/DVD drive has disappeared"
date: 2011-05-10
forum: Hardware
---

### Post by Jason Spaceman on 2011-05-10
I installed Ubuntu 11.04 and after the install I notice that my CD/DVD drive has disappeared, both in Ubuntu and in Windows XP.  

I had this happen before, a few years ago, and I can't remember the solution.  I think it has something to do with getting Grub to pass on some commands during the boot so that the computer recognizes the drive.  Does anyone know what the command is, and how to set it up so that is is passed on every time I boot?

Thanks.

---

### Post by TheNerdAL on 2011-05-10
Type: 
```
dmesg
``` 
And post the results.

And can you see the drive when selecting a boot option in the Bios?

---

### Post by trozamon on 2011-05-10
Does it show up when you put in a CD or DVD?

---

### Post by Jason Spaceman on 2011-05-10
OK, I put a CD into the drive and Ubuntu mounted it and I can see it.  That's strange.  But I still get no CD drive in WinXP.

Here is my dmesg:

```
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.38-8-generic (buildd@vernadsky) (gcc version 4.5.2 (Ubuntu/Linaro 4.5.2-8ubuntu3) ) #42-Ubuntu SMP Mon Apr 11 03:31:50 UTC 2011 (Ubuntu 2.6.38-8.42-generic 2.6.38.2)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
[    0.000000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000007fe80000 (usable)
[    0.000000]  BIOS-e820: 000000007fe80000 - 000000007fe8b000 (ACPI data)
[    0.000000]  BIOS-e820: 000000007fe8b000 - 000000007ff00000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000007ff00000 - 0000000080000000 (reserved)
[    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed00000 - 00000000fed00400 (reserved)
[    0.000000]  BIOS-e820: 00000000fed14000 - 00000000fed1a000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed1c000 - 00000000fed90000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000ff000000 - 0000000100000000 (reserved)
[    0.000000] Notice: NX (Execute Disable) protection cannot be enabled in hardware: non-PAE kernel!
[    0.000000] NX (Execute Disable) protection: approximated by x86 segment limits
[    0.000000] DMI present.
[    0.000000] DMI: Clevo Co. M570U/CAPELL VALLEY(NAPA) CRB, BIOS NAPA0001.86C.00                11/30/06
[    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
[    0.000000] e820 remove range: 00000000000a0000 - 0000000000100000 (usable)
[    0.000000] last_pfn = 0x7fe80 max_arch_pfn = 0x100000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-CFFFF write-protect
[    0.000000]   D0000-DFFFF uncachable
[    0.000000]   E0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000 mask F80000000 write-back
[    0.000000]   1 base 07FF00000 mask FFFF00000 uncachable
[    0.000000]   2 disabled
[    0.000000]   3 disabled
[    0.000000]   4 disabled
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] PAT not supported by CPU.
[    0.000000] found SMP MP-table at [c00f7760] f7760
[    0.000000] initial memory mapped : 0 - 01c00000
[    0.000000] init_memory_mapping: 0000000000000000-00000000377fe000
[    0.000000]  0000000000 - 0000400000 page 4k
[    0.000000]  0000400000 - 0037400000 page 2M
[    0.000000]  0037400000 - 00377fe000 page 4k
[    0.000000] kernel direct mapping tables up to 377fe000 @ 1bfb000-1c00000
[    0.000000] RAMDISK: 36782000 - 373b9000
[    0.000000] ACPI: RSDP 000f76b0 00014 (v00 PTLTD )
[    0.000000] ACPI: RSDT 7fe85518 0004C (v01 MSTEST TESTONLY 06040000  LTP 00000000)
[    0.000000] ACPI: FACP 7fe8acaa 00074 (v01 INTEL  CALISTGA 06040000 LOHR 0000005A)
[    0.000000] ACPI: DSDT 7fe86c19 04091 (v01 INTEL  CALISTGA 06040000 INTL 20050624)
[    0.000000] ACPI: FACS 7fe8bfc0 00040
[    0.000000] ACPI: APIC 7fe8ad1e 00068 (v01 INTEL  CALISTGA 06040000 LOHR 0000005A)
[    0.000000] ACPI: HPET 7fe8ad86 00038 (v01 INTEL  CALISTGA 06040000 LOHR 0000005A)
[    0.000000] ACPI: MCFG 7fe8adbe 0003C (v01 INTEL  CALISTGA 06040000 LOHR 0000005A)
[    0.000000] ACPI: APIC 7fe8adfa 00068 (v01 PTLTD  ? APIC   06040000  LTP 00000000)
[    0.000000] ACPI: SLIC 7fe8ae62 00176 (v01 MSTEST TESTONLY 06040000  LTP 00000000)
[    0.000000] ACPI: BOOT 7fe8afd8 00028 (v01 PTLTD  $SBFTBL$ 06040000  LTP 00000001)
[    0.000000] ACPI: SSDT 7fe865ca 0064F (v01 SataRe  SataPri 00001000 INTL 20050624)
[    0.000000] ACPI: SSDT 7fe85f2e 0069C (v01 SataRe  SataSec 00001000 INTL 20050624)
[    0.000000] ACPI: SSDT 7fe85564 004F6 (v01  PmRef    CpuPm 00003000 INTL 20050624)
[    0.000000] ACPI: BIOS bug: multiple APIC/MADT found, using 0
[    0.000000] ACPI: If "acpi_apic_instance=2" works better, notify linux-acpi@vger.kernel.org
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] 1158MB HIGHMEM available.
[    0.000000] 887MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 377fe000
[    0.000000]   low ram: 0 - 377fe000
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x000377fe
[    0.000000]   HighMem  0x000377fe -> 0x0007fe80
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[2] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x0000009f
[    0.000000]     0: 0x00000100 -> 0x0007fe80
[    0.000000] On node 0 totalpages: 523791
[    0.000000] free_area_init_node: node 0, pgdat c1784100, node_mem_map f5782200
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3951 pages, LIFO batch:0
[    0.000000]   Normal zone: 1744 pages used for memmap
[    0.000000]   Normal zone: 221486 pages, LIFO batch:31
[    0.000000]   HighMem zone: 2318 pages used for memmap
[    0.000000]   HighMem zone: 294260 pages, LIFO batch:31
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
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
[    0.000000] SMP: Allowing 2 CPUs, 0 hotplug CPUs
[    0.000000] nr_irqs_gsi: 40
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
[    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 80000000 (gap: 80000000:60000000)
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] setup_percpu: NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:2 nr_node_ids:1
[    0.000000] PERCPU: Embedded 13 pages/cpu @f5000000 s28800 r0 d24448 u2097152
[    0.000000] pcpu-alloc: s28800 r0 d24448 u2097152 alloc=1*4194304
[    0.000000] pcpu-alloc: [0] 0 1 
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 519697
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.38-8-generic root=UUID=778011d0-ede6-4d77-9d30-ae442c5dfc10 ro quiet splash vt.handoff=7
[    0.000000] PID hash table entries: 4096 (order: 2, 16384 bytes)
[    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.000000] Initializing CPU#0
[    0.000000] allocated 10477760 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] Initializing HighMem for node 0 (000377fe:0007fe80)
[    0.000000] Memory: 2045720k/2095616k available (5188k kernel code, 49444k reserved, 2540k data, 700k init, 1186312k highmem)
[    0.000000] virtual kernel memory layout:
[    0.000000]     fixmap  : 0xfff16000 - 0xfffff000   ( 932 kB)
[    0.000000]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[    0.000000]     vmalloc : 0xf7ffe000 - 0xff7fe000   ( 120 MB)
[    0.000000]     lowmem  : 0xc0000000 - 0xf77fe000   ( 887 MB)
[    0.000000]       .init : 0xc178d000 - 0xc183c000   ( 700 kB)
[    0.000000]       .data : 0xc15112a1 - 0xc178c480   (2540 kB)
[    0.000000]       .text : 0xc1000000 - 0xc15112a1   (5188 kB)
[    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.000000] SLUB: Genslabs=15, HWalign=64, Order=0-3, MinObjects=0, CPUs=2, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000] 	RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000] 	RCU-based detection of stalled CPUs is disabled.
[    0.000000] NR_IRQS:2304 nr_irqs:512 16
[    0.000000] CPU 0 irqstacks, hard=f4008000 soft=f400a000
[    0.000000] vt handoff: transparent VT on vt#7
[    0.000000] Console: colour dummy device 80x25
[    0.000000] console [tty0] enabled
[    0.000000] hpet clockevent registered
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 2161.054 MHz processor.
[    0.004005] Calibrating delay loop (skipped), value calculated using timer frequency.. 4322.10 BogoMIPS (lpj=8644216)
[    0.004015] pid_max: default: 32768 minimum: 301
[    0.004061] Security Framework initialized
[    0.004092] AppArmor: AppArmor initialized
[    0.004096] Yama: becoming mindful.
[    0.004209] Mount-cache hash table entries: 512
[    0.004464] Initializing cgroup subsys ns
[    0.004471] ns_cgroup deprecated: consider using the 'clone_children' flag without the ns_cgroup.
[    0.004478] Initializing cgroup subsys cpuacct
[    0.004488] Initializing cgroup subsys memory
[    0.004506] Initializing cgroup subsys devices
[    0.004512] Initializing cgroup subsys freezer
[    0.004516] Initializing cgroup subsys net_cls
[    0.004521] Initializing cgroup subsys blkio
[    0.004590] CPU: Physical Processor ID: 0
[    0.004594] CPU: Processor Core ID: 0
[    0.004600] mce: CPU supports 6 MCE banks
[    0.004616] CPU0: Thermal monitoring handled by SMI
[    0.004623] using mwait in idle threads.
[    0.010588] ACPI: Core revision 20110112
[    0.019507] ftrace: allocating 23640 entries in 47 pages
[    0.024089] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.024499] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.066093] CPU0: Genuine Intel(R) CPU           T2600  @ 2.16GHz stepping 08
[    0.068003] Performance Events: Core events, core PMU driver.
[    0.068003] ... version:                1
[    0.068003] ... bit width:              40
[    0.068003] ... generic registers:      2
[    0.068003] ... value mask:             000000ffffffffff
[    0.068003] ... max period:             000000007fffffff
[    0.068003] ... fixed-purpose events:   0
[    0.068003] ... event mask:             0000000000000003
[    0.068003] CPU 1 irqstacks, hard=f40aa000 soft=f40ac000
[    0.068003] Booting Node   0, Processors  #1 Ok.
[    0.008000] Initializing CPU#1
[    0.008000] CPU1: Thermal monitoring handled by SMI
[    0.156038] Brought up 2 CPUs
[    0.156044] Total of 2 processors activated (8644.74 BogoMIPS).
[    0.156943] devtmpfs: initialized
[    0.160379] print_constraints: dummy: 
[    0.160424] Time: 21:44:42  Date: 05/10/11
[    0.160515] NET: Registered protocol family 16
[    0.160574] Trying to unpack rootfs image as initramfs...
[    0.160776] EISA bus registered
[    0.160793] ACPI: bus type pci registered
[    0.160938] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xe0000000-0xefffffff] (base 0xe0000000)
[    0.160947] PCI: MMCONFIG at [mem 0xe0000000-0xefffffff] reserved in E820
[    0.160951] PCI: Using MMCONFIG for extended config space
[    0.160956] PCI: Using configuration type 1 for base access
[    0.163238] bio: create slab <bio-0> at 0
[    0.165939] ACPI: EC: Look up EC in DSDT
[    0.170667] [Firmware Bug]: ACPI: BIOS _OSI(Linux) query ignored
[    0.171804] ACPI: SSDT 7fe85cbb 001EA (v01  PmRef  Cpu0Ist 00003000 INTL 20050624)
[    0.172620] ACPI: Dynamic OEM Table Load:
[    0.172628] ACPI: SSDT   (null) 001EA (v01  PmRef  Cpu0Ist 00003000 INTL 20050624)
[    0.172886] ACPI: SSDT 7fe85a5a 001DC (v01  PmRef  Cpu0Cst 00003001 INTL 20050624)
[    0.173471] ACPI: Dynamic OEM Table Load:
[    0.173478] ACPI: SSDT   (null) 001DC (v01  PmRef  Cpu0Cst 00003001 INTL 20050624)
[    0.174027] ACPI: SSDT 7fe85ea5 00089 (v01  PmRef  Cpu1Ist 00003000 INTL 20050624)
[    0.174626] ACPI: Dynamic OEM Table Load:
[    0.174633] ACPI: SSDT   (null) 00089 (v01  PmRef  Cpu1Ist 00003000 INTL 20050624)
[    0.174859] ACPI: SSDT 7fe85c36 00085 (v01  PmRef  Cpu1Cst 00003000 INTL 20050624)
[    0.175445] ACPI: Dynamic OEM Table Load:
[    0.175452] ACPI: SSDT   (null) 00085 (v01  PmRef  Cpu1Cst 00003000 INTL 20050624)
[    0.175988] ACPI: Interpreter enabled
[    0.176017] ACPI: (supports S0 S3 S4 S5)
[    0.176059] ACPI: Using IOAPIC for interrupt routing
[    0.186524] ACPI: EC: GPE = 0x17, I/O: command/status = 0x66, data = 0x62
[    0.264307] ACPI: No dock devices found.
[    0.264316] HEST: Table not found.
[    0.264325] PCI: Ignoring host bridge windows from ACPI; if necessary, use "pci=use_crs" and report a bug
[    0.265007] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
[    0.266289] pci_root PNP0A08:00: host bridge window [io  0x0000-0x0cf7] (ignored)
[    0.266297] pci_root PNP0A08:00: host bridge window [io  0x0d00-0xffff] (ignored)
[    0.266304] pci_root PNP0A08:00: host bridge window [mem 0x000a0000-0x000bffff] (ignored)
[    0.266311] pci_root PNP0A08:00: host bridge window [mem 0x000d0000-0x000d3fff] (ignored)
[    0.266318] pci_root PNP0A08:00: host bridge window [mem 0x000d4000-0x000d7fff] (ignored)
[    0.266325] pci_root PNP0A08:00: host bridge window [mem 0x000d8000-0x000dbfff] (ignored)
[    0.266331] pci_root PNP0A08:00: host bridge window [mem 0x000dc000-0x000dffff] (ignored)
[    0.266338] pci_root PNP0A08:00: host bridge window [mem 0x80000000-0xfebfffff] (ignored)
[    0.266361] pci 0000:00:00.0: [8086:27a0] type 0 class 0x000600
[    0.266442] pci 0000:00:01.0: [8086:27a1] type 1 class 0x000604
[    0.266505] pci 0000:00:01.0: PME# supported from D0 D3hot D3cold
[    0.266512] pci 0000:00:01.0: PME# disabled
[    0.266602] pci 0000:00:1b.0: [8086:27d8] type 0 class 0x000403
[    0.266634] pci 0000:00:1b.0: reg 10: [mem 0xda300000-0xda303fff 64bit]
[    0.266741] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    0.266750] pci 0000:00:1b.0: PME# disabled
[    0.266789] pci 0000:00:1c.0: [8086:27d0] type 1 class 0x000604
[    0.266901] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.266909] pci 0000:00:1c.0: PME# disabled
[    0.266953] pci 0000:00:1c.1: [8086:27d2] type 1 class 0x000604
[    0.267064] pci 0000:00:1c.1: PME# supported from D0 D3hot D3cold
[    0.267073] pci 0000:00:1c.1: PME# disabled
[    0.267118] pci 0000:00:1c.2: [8086:27d4] type 1 class 0x000604
[    0.267229] pci 0000:00:1c.2: PME# supported from D0 D3hot D3cold
[    0.267238] pci 0000:00:1c.2: PME# disabled
[    0.267285] pci 0000:00:1d.0: [8086:27c8] type 0 class 0x000c03
[    0.267359] pci 0000:00:1d.0: reg 20: [io  0x1800-0x181f]
[    0.267413] pci 0000:00:1d.1: [8086:27c9] type 0 class 0x000c03
[    0.267485] pci 0000:00:1d.1: reg 20: [io  0x1820-0x183f]
[    0.267540] pci 0000:00:1d.2: [8086:27ca] type 0 class 0x000c03
[    0.267613] pci 0000:00:1d.2: reg 20: [io  0x1840-0x185f]
[    0.267667] pci 0000:00:1d.3: [8086:27cb] type 0 class 0x000c03
[    0.267741] pci 0000:00:1d.3: reg 20: [io  0x1860-0x187f]
[    0.267810] pci 0000:00:1d.7: [8086:27cc] type 0 class 0x000c03
[    0.267843] pci 0000:00:1d.7: reg 10: [mem 0xda304000-0xda3043ff]
[    0.267957] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
[    0.267967] pci 0000:00:1d.7: PME# disabled
[    0.268000] pci 0000:00:1e.0: [8086:2448] type 1 class 0x000604
[    0.268129] pci 0000:00:1f.0: [8086:27bd] type 0 class 0x000601
[    0.268269] pci 0000:00:1f.0: quirk: [io  0x1000-0x107f] claimed by ICH6 ACPI/GPIO/TCO
[    0.268280] pci 0000:00:1f.0: quirk: [io  0x1180-0x11bf] claimed by ICH6 GPIO
[    0.268356] pci 0000:00:1f.2: [8086:27c4] type 0 class 0x000101
[    0.268385] pci 0000:00:1f.2: reg 10: [io  0x0000-0x0007]
[    0.268403] pci 0000:00:1f.2: reg 14: [io  0x0000-0x0003]
[    0.268420] pci 0000:00:1f.2: reg 18: [io  0x0000-0x0007]
[    0.268438] pci 0000:00:1f.2: reg 1c: [io  0x0000-0x0003]
[    0.268456] pci 0000:00:1f.2: reg 20: [io  0x18b0-0x18bf]
[    0.268515] pci 0000:00:1f.2: PME# supported from D3hot
[    0.268523] pci 0000:00:1f.2: PME# disabled
[    0.268549] pci 0000:00:1f.3: [8086:27da] type 0 class 0x000c05
[    0.268640] pci 0000:00:1f.3: reg 20: [io  0x18c0-0x18df]
[    0.268766] pci 0000:01:00.0: [10de:0299] type 0 class 0x000300
[    0.268785] pci 0000:01:00.0: reg 10: [mem 0xd9000000-0xd9ffffff]
[    0.268804] pci 0000:01:00.0: reg 14: [mem 0xc0000000-0xcfffffff 64bit pref]
[    0.268824] pci 0000:01:00.0: reg 1c: [mem 0xd8000000-0xd8ffffff 64bit]
[    0.268838] pci 0000:01:00.0: reg 24: [io  0x2000-0x207f]
[    0.268852] pci 0000:01:00.0: reg 30: [mem 0x00000000-0x0001ffff pref]
[    0.268900] pci 0000:01:00.0: disabling ASPM on pre-1.1 PCIe device.  You can enable it with 'pcie_aspm=force'
[    0.268915] pci 0000:00:01.0: PCI bridge to [bus 01-01]
[    0.268923] pci 0000:00:01.0:   bridge window [io  0x2000-0x2fff]
[    0.268931] pci 0000:00:01.0:   bridge window [mem 0xd8000000-0xd9ffffff]
[    0.268942] pci 0000:00:01.0:   bridge window [mem 0xc0000000-0xcfffffff 64bit pref]
[    0.269128] pci 0000:02:00.0: [8086:4222] type 0 class 0x000280
[    0.269192] pci 0000:02:00.0: reg 10: [mem 0xd4000000-0xd4000fff]
[    0.269559] pci 0000:02:00.0: PME# supported from D0 D3hot D3cold
[    0.269576] pci 0000:02:00.0: PME# disabled
[    0.269653] pci 0000:02:00.0: disabling ASPM on pre-1.1 PCIe device.  You can enable it with 'pcie_aspm=force'
[    0.269699] pci 0000:00:1c.0: PCI bridge to [bus 02-02]
[    0.269708] pci 0000:00:1c.0:   bridge window [io  0x3000-0x3fff]
[    0.269718] pci 0000:00:1c.0:   bridge window [mem 0xd4000000-0xd5ffffff]
[    0.269731] pci 0000:00:1c.0:   bridge window [mem 0xd0000000-0xd1ffffff 64bit pref]
[    0.269814] pci 0000:00:1c.1: PCI bridge to [bus 03-04]
[    0.269823] pci 0000:00:1c.1:   bridge window [io  0x4000-0x4fff]
[    0.269832] pci 0000:00:1c.1:   bridge window [mem 0xd6000000-0xd7ffffff]
[    0.269846] pci 0000:00:1c.1:   bridge window [mem 0xd2000000-0xd3ffffff 64bit pref]
[    0.269928] pci 0000:00:1c.2: PCI bridge to [bus 05-05]
[    0.269937] pci 0000:00:1c.2:   bridge window [io  0xf000-0x0000] (disabled)
[    0.269947] pci 0000:00:1c.2:   bridge window [mem 0xfff00000-0x000fffff] (disabled)
[    0.269960] pci 0000:00:1c.2:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    0.270037] pci 0000:06:04.0: [1131:7133] type 0 class 0x000480
[    0.270071] pci 0000:06:04.0: reg 10: [mem 0xda006000-0xda0067ff]
[    0.270192] pci 0000:06:04.0: supports D1 D2
[    0.270231] pci 0000:06:07.0: [104c:8039] type 2 class 0x000607
[    0.270265] pci 0000:06:07.0: reg 10: [mem 0xda004000-0xda004fff]
[    0.270303] pci 0000:06:07.0: supports D1 D2
[    0.270308] pci 0000:06:07.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.270318] pci 0000:06:07.0: PME# disabled
[    0.270351] pci 0000:06:07.1: [104c:803a] type 0 class 0x000c00
[    0.270386] pci 0000:06:07.1: reg 10: [mem 0xda006800-0xda006fff]
[    0.270407] pci 0000:06:07.1: reg 14: [mem 0xda000000-0xda003fff]
[    0.270519] pci 0000:06:07.1: supports D1 D2
[    0.270524] pci 0000:06:07.1: PME# supported from D0 D1 D2 D3hot
[    0.270534] pci 0000:06:07.1: PME# disabled
[    0.270566] pci 0000:06:07.2: [104c:803b] type 0 class 0x000180
[    0.270600] pci 0000:06:07.2: reg 10: [mem 0xda005000-0xda005fff]
[    0.270724] pci 0000:06:07.2: supports D1 D2
[    0.270729] pci 0000:06:07.2: PME# supported from D0 D1 D2 D3hot
[    0.270739] pci 0000:06:07.2: PME# disabled
[    0.270772] pci 0000:06:07.3: [104c:803c] type 0 class 0x000805
[    0.270805] pci 0000:06:07.3: reg 10: [mem 0xda007000-0xda0070ff]
[    0.270928] pci 0000:06:07.3: supports D1 D2
[    0.270933] pci 0000:06:07.3: PME# supported from D0 D1 D2 D3hot D3cold
[    0.270943] pci 0000:06:07.3: PME# disabled
[    0.270992] pci 0000:06:0b.0: [10ec:8169] type 0 class 0x000200
[    0.271026] pci 0000:06:0b.0: reg 10: [io  0x5000-0x50ff]
[    0.271046] pci 0000:06:0b.0: reg 14: [mem 0xda007400-0xda0074ff]
[    0.271126] pci 0000:06:0b.0: reg 30: [mem 0x00000000-0x0001ffff pref]
[    0.271162] pci 0000:06:0b.0: supports D1 D2
[    0.271167] pci 0000:06:0b.0: PME# supported from D1 D2 D3hot D3cold
[    0.271177] pci 0000:06:0b.0: PME# disabled
[    0.271237] pci 0000:00:1e.0: PCI bridge to [bus 06-07] (subtractive decode)
[    0.271247] pci 0000:00:1e.0:   bridge window [io  0x5000-0x5fff]
[    0.271256] pci 0000:00:1e.0:   bridge window [mem 0xda000000-0xda0fffff]
[    0.271269] pci 0000:00:1e.0:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    0.271276] pci 0000:00:1e.0:   bridge window [io  0x0000-0xffff] (subtractive decode)
[    0.271283] pci 0000:00:1e.0:   bridge window [mem 0x00000000-0xffffffff] (subtractive decode)
[    0.271353] pci_bus 0000:07: [bus 07-0a] partially hidden behind transparent bridge 0000:06 [bus 06-07]
[    0.271396] pci_bus 0000:00: on NUMA node 0
[    0.271405] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.271761] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEGP._PRT]
[    0.271900] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP01._PRT]
[    0.272042] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP02._PRT]
[    0.272162] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP03._PRT]
[    0.272285] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIB._PRT]
[    0.272498]  pci0000:00: Requesting ACPI _OSC control (0x1d)
[    0.278783] ACPI: PCI Interrupt Link [LNKA] (IRQs 1 3 4 5 6 *7 10 12 14 15)
[    0.278904] ACPI: PCI Interrupt Link [LNKB] (IRQs 1 3 4 5 6 7 *11 12 14 15)
[    0.279019] ACPI: PCI Interrupt Link [LNKC] (IRQs 1 3 4 5 6 7 10 12 14 15) *11
[    0.279135] ACPI: PCI Interrupt Link [LNKD] (IRQs 1 3 4 5 6 7 11 12 14 15) *10
[    0.279252] ACPI: PCI Interrupt Link [LNKE] (IRQs 1 3 4 5 6 7 10 12 14 15) *0, disabled.
[    0.279369] ACPI: PCI Interrupt Link [LNKF] (IRQs 1 3 4 5 6 7 11 12 14 15) *0, disabled.
[    0.279486] ACPI: PCI Interrupt Link [LNKG] (IRQs 1 3 4 5 6 7 *10 12 14 15)
[    0.279600] ACPI: PCI Interrupt Link [LNKH] (IRQs 1 3 4 *5 6 7 11 12 14 15)
[    0.279857] vgaarb: device added: PCI:0000:01:00.0,decodes=io+mem,owns=io+mem,locks=none
[    0.279872] vgaarb: loaded
[    0.280362] SCSI subsystem initialized
[    0.280479] libata version 3.00 loaded.
[    0.280584] usbcore: registered new interface driver usbfs
[    0.280611] usbcore: registered new interface driver hub
[    0.280676] usbcore: registered new device driver usb
[    0.280927] wmi: Mapper loaded
[    0.280932] PCI: Using ACPI for IRQ routing
[    0.280938] PCI: pci_cache_line_size set to 64 bytes
[    0.281122] reserve RAM buffer: 000000000009f800 - 000000000009ffff 
[    0.281128] reserve RAM buffer: 000000007fe80000 - 000000007fffffff 
[    0.281339] NetLabel: Initializing
[    0.281344] NetLabel:  domain hash size = 128
[    0.281347] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.281372] NetLabel:  unlabeled traffic allowed by default
[    0.281454] HPET: 3 timers in total, 0 timers will be used for per-cpu timer
[    0.281465] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[    0.281476] hpet0: 3 comparators, 64-bit 14.318180 MHz counter
[    0.284645] Switching to clocksource hpet
[    0.286437] Switched to NOHz mode on CPU #0
[    0.286583] Switched to NOHz mode on CPU #1
[    0.301289] AppArmor: AppArmor Filesystem Enabled
[    0.301344] pnp: PnP ACPI init
[    0.301383] ACPI: bus type pnp registered
[    0.302573] pnp 00:00: [bus 00-ff]
[    0.302581] pnp 00:00: [io  0x0000-0x0cf7 window]
[    0.302586] pnp 00:00: [io  0x0cf8-0x0cff]
[    0.302592] pnp 00:00: [io  0x0d00-0xffff window]
[    0.302598] pnp 00:00: [mem 0x000a0000-0x000bffff window]
[    0.302604] pnp 00:00: [mem 0x000c0000-0x000c3fff window]
[    0.302610] pnp 00:00: [mem 0x000c4000-0x000c7fff window]
[    0.302616] pnp 00:00: [mem 0x000c8000-0x000cbfff window]
[    0.302621] pnp 00:00: [mem 0x000cc000-0x000cffff window]
[    0.302627] pnp 00:00: [mem 0x000d0000-0x000d3fff window]
[    0.302633] pnp 00:00: [mem 0x000d4000-0x000d7fff window]
[    0.302639] pnp 00:00: [mem 0x000d8000-0x000dbfff window]
[    0.302645] pnp 00:00: [mem 0x000dc000-0x000dffff window]
[    0.302651] pnp 00:00: [mem 0x000e0000-0x000e3fff window]
[    0.302656] pnp 00:00: [mem 0x000e4000-0x000e7fff window]
[    0.302662] pnp 00:00: [mem 0x000e8000-0x000ebfff window]
[    0.302668] pnp 00:00: [mem 0x000ec000-0x000effff window]
[    0.302674] pnp 00:00: [mem 0x000f0000-0x000fffff window]
[    0.302680] pnp 00:00: [mem 0x80000000-0xfebfffff window]
[    0.302686] pnp 00:00: [mem 0xfed40000-0xfed44fff window]
[    0.302825] pnp 00:00: Plug and Play ACPI device, IDs PNP0a08 PNP0a03 (active)
[    0.302868] pnp 00:01: [mem 0xe0000000-0xefffffff]
[    0.302874] pnp 00:01: [mem 0xfed14000-0xfed17fff]
[    0.302879] pnp 00:01: [mem 0xfed18000-0xfed18fff]
[    0.302884] pnp 00:01: [mem 0xfed19000-0xfed19fff]
[    0.302890] pnp 00:01: [mem 0xfed1c000-0xfed1ffff]
[    0.302895] pnp 00:01: [mem 0xfed20000-0xfed3ffff]
[    0.302901] pnp 00:01: [mem 0xfed45000-0xfed8ffff]
[    0.303033] system 00:01: [mem 0xe0000000-0xefffffff] has been reserved
[    0.303041] system 00:01: [mem 0xfed14000-0xfed17fff] has been reserved
[    0.303048] system 00:01: [mem 0xfed18000-0xfed18fff] has been reserved
[    0.303055] system 00:01: [mem 0xfed19000-0xfed19fff] has been reserved
[    0.303062] system 00:01: [mem 0xfed1c000-0xfed1ffff] has been reserved
[    0.303069] system 00:01: [mem 0xfed20000-0xfed3ffff] has been reserved
[    0.303076] system 00:01: [mem 0xfed45000-0xfed8ffff] has been reserved
[    0.303084] system 00:01: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.303457] pnp 00:02: [io  0x0000-0x001f]
[    0.303463] pnp 00:02: [io  0x0081-0x0091]
[    0.303468] pnp 00:02: [io  0x0093-0x009f]
[    0.303474] pnp 00:02: [io  0x00c0-0x00df]
[    0.303480] pnp 00:02: [dma 4]
[    0.303567] pnp 00:02: Plug and Play ACPI device, IDs PNP0200 (active)
[    0.303589] pnp 00:03: [mem 0xff000000-0xffffffff]
[    0.303674] pnp 00:03: Plug and Play ACPI device, IDs INT0800 (active)
[    0.303820] pnp 00:04: [mem 0xfed00000-0xfed003ff]
[    0.303960] system 00:04: [mem 0xfed00000-0xfed003ff] has been reserved
[    0.303969] system 00:04: Plug and Play ACPI device, IDs PNP0103 PNP0c01 (active)
[    0.303996] pnp 00:05: [io  0x00f0]
[    0.304037] pnp 00:05: [irq 13]
[    0.304133] pnp 00:05: Plug and Play ACPI device, IDs PNP0c04 (active)
[    0.304161] pnp 00:06: [io  0x002e-0x002f]
[    0.304166] pnp 00:06: [io  0x0061]
[    0.304171] pnp 00:06: [io  0x0063]
[    0.304176] pnp 00:06: [io  0x0065]
[    0.304181] pnp 00:06: [io  0x0067]
[    0.304186] pnp 00:06: [io  0x0070]
[    0.304190] pnp 00:06: [io  0x0080]
[    0.304195] pnp 00:06: [io  0x0092]
[    0.304200] pnp 00:06: [io  0x00b2-0x00b3]
[    0.304205] pnp 00:06: [io  0x0680-0x069f]
[    0.304210] pnp 00:06: [io  0x0800-0x080f]
[    0.304215] pnp 00:06: [io  0x1000-0x107f]
[    0.304220] pnp 00:06: [io  0x1180-0x11bf]
[    0.304225] pnp 00:06: [io  0x1640-0x164f]
[    0.304383] system 00:06: [io  0x0680-0x069f] has been reserved
[    0.304390] system 00:06: [io  0x0800-0x080f] has been reserved
[    0.304397] system 00:06: [io  0x1000-0x107f] has been reserved
[    0.304403] system 00:06: [io  0x1180-0x11bf] has been reserved
[    0.304410] system 00:06: [io  0x1640-0x164f] has been reserved
[    0.304418] system 00:06: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.304475] pnp 00:07: [io  0x06a0-0x06af]
[    0.304481] pnp 00:07: [io  0x06b0-0x06ff]
[    0.304615] system 00:07: [io  0x06a0-0x06af] has been reserved
[    0.304622] system 00:07: [io  0x06b0-0x06ff] has been reserved
[    0.304629] system 00:07: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.304652] pnp 00:08: [io  0x0070-0x0077]
[    0.304663] pnp 00:08: [irq 8]
[    0.304755] pnp 00:08: Plug and Play ACPI device, IDs PNP0b00 (active)
[    0.305078] pnp 00:09: [io  0x03f8-0x03ff]
[    0.305090] pnp 00:09: [irq 4]
[    0.305291] pnp 00:09: Plug and Play ACPI device, IDs PNP0501 (active)
[    0.305391] pnp 00:0a: [io  0x02f8-0x02ff]
[    0.305403] pnp 00:0a: [irq 3]
[    0.305407] pnp 00:0a: [dma 3]
[    0.305548] pnp 00:0a: Plug and Play ACPI device, IDs NSC6001 PNP0510 (active)
[    0.305572] pnp 00:0b: [io  0x0060]
[    0.305577] pnp 00:0b: [io  0x0064]
[    0.305588] pnp 00:0b: [irq 1]
[    0.305685] pnp 00:0b: Plug and Play ACPI device, IDs PNP0303 (active)
[    0.305712] pnp 00:0c: [irq 12]
[    0.305814] pnp 00:0c: Plug and Play ACPI device, IDs PNP0f13 (active)
[    0.305879] pnp: PnP ACPI: found 13 devices
[    0.305883] ACPI: ACPI bus type pnp unregistered
[    0.305892] PnPBIOS: Disabled by ACPI PNP
[    0.344838] pci 0000:00:1e.0: BAR 15: assigned [mem 0x80000000-0x85ffffff pref]
[    0.344849] pci 0000:00:1c.2: BAR 14: assigned [mem 0x86000000-0x861fffff]
[    0.344859] pci 0000:00:1c.2: BAR 15: assigned [mem 0x86200000-0x863fffff 64bit pref]
[    0.344868] pci 0000:00:1c.2: BAR 13: assigned [io  0x6000-0x6fff]
[    0.344878] pci 0000:01:00.0: BAR 6: can't assign mem pref (size 0x20000)
[    0.344885] pci 0000:00:01.0: PCI bridge to [bus 01-01]
[    0.344892] pci 0000:00:01.0:   bridge window [io  0x2000-0x2fff]
[    0.344900] pci 0000:00:01.0:   bridge window [mem 0xd8000000-0xd9ffffff]
[    0.344909] pci 0000:00:01.0:   bridge window [mem 0xc0000000-0xcfffffff 64bit pref]
[    0.344919] pci 0000:00:1c.0: PCI bridge to [bus 02-02]
[    0.344926] pci 0000:00:1c.0:   bridge window [io  0x3000-0x3fff]
[    0.344937] pci 0000:00:1c.0:   bridge window [mem 0xd4000000-0xd5ffffff]
[    0.344947] pci 0000:00:1c.0:   bridge window [mem 0xd0000000-0xd1ffffff 64bit pref]
[    0.344960] pci 0000:00:1c.1: PCI bridge to [bus 03-04]
[    0.344967] pci 0000:00:1c.1:   bridge window [io  0x4000-0x4fff]
[    0.344978] pci 0000:00:1c.1:   bridge window [mem 0xd6000000-0xd7ffffff]
[    0.344987] pci 0000:00:1c.1:   bridge window [mem 0xd2000000-0xd3ffffff 64bit pref]
[    0.345001] pci 0000:00:1c.2: PCI bridge to [bus 05-05]
[    0.345007] pci 0000:00:1c.2:   bridge window [io  0x6000-0x6fff]
[    0.345018] pci 0000:00:1c.2:   bridge window [mem 0x86000000-0x861fffff]
[    0.345028] pci 0000:00:1c.2:   bridge window [mem 0x86200000-0x863fffff 64bit pref]
[    0.345045] pci 0000:06:07.0: BAR 15: assigned [mem 0x80000000-0x83ffffff pref]
[    0.345056] pci 0000:06:07.0: BAR 16: assigned [mem 0x88000000-0x8bffffff]
[    0.345063] pci 0000:06:0b.0: BAR 6: assigned [mem 0x84000000-0x8401ffff pref]
[    0.345070] pci 0000:06:07.0: BAR 13: assigned [io  0x5400-0x54ff]
[    0.345077] pci 0000:06:07.0: BAR 14: assigned [io  0x5800-0x58ff]
[    0.345083] pci 0000:06:07.0: CardBus bridge to [bus 07-0a]
[    0.345088] pci 0000:06:07.0:   bridge window [io  0x5400-0x54ff]
[    0.345098] pci 0000:06:07.0:   bridge window [io  0x5800-0x58ff]
[    0.345108] pci 0000:06:07.0:   bridge window [mem 0x80000000-0x83ffffff pref]
[    0.345118] pci 0000:06:07.0:   bridge window [mem 0x88000000-0x8bffffff]
[    0.345128] pci 0000:00:1e.0: PCI bridge to [bus 06-07]
[    0.345135] pci 0000:00:1e.0:   bridge window [io  0x5000-0x5fff]
[    0.345146] pci 0000:00:1e.0:   bridge window [mem 0xda000000-0xda0fffff]
[    0.345156] pci 0000:00:1e.0:   bridge window [mem 0x80000000-0x85ffffff pref]
[    0.345196] pci 0000:00:01.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.345205] pci 0000:00:01.0: setting latency timer to 64
[    0.345225] pci 0000:00:1c.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    0.345234] pci 0000:00:1c.0: setting latency timer to 64
[    0.345248] pci 0000:00:1c.1: PCI INT B -> GSI 16 (level, low) -> IRQ 16
[    0.345257] pci 0000:00:1c.1: setting latency timer to 64
[    0.345276] pci 0000:00:1c.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.345285] pci 0000:00:1c.2: setting latency timer to 64
[    0.345300] pci 0000:00:1e.0: setting latency timer to 64
[    0.345314] pci 0000:06:07.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.345326] pci_bus 0000:00: resource 0 [io  0x0000-0xffff]
[    0.345332] pci_bus 0000:00: resource 1 [mem 0x00000000-0xffffffff]
[    0.345338] pci_bus 0000:01: resource 0 [io  0x2000-0x2fff]
[    0.345344] pci_bus 0000:01: resource 1 [mem 0xd8000000-0xd9ffffff]
[    0.345351] pci_bus 0000:01: resource 2 [mem 0xc0000000-0xcfffffff 64bit pref]
[    0.345357] pci_bus 0000:02: resource 0 [io  0x3000-0x3fff]
[    0.345363] pci_bus 0000:02: resource 1 [mem 0xd4000000-0xd5ffffff]
[    0.345370] pci_bus 0000:02: resource 2 [mem 0xd0000000-0xd1ffffff 64bit pref]
[    0.345376] pci_bus 0000:03: resource 0 [io  0x4000-0x4fff]
[    0.345382] pci_bus 0000:03: resource 1 [mem 0xd6000000-0xd7ffffff]
[    0.345388] pci_bus 0000:03: resource 2 [mem 0xd2000000-0xd3ffffff 64bit pref]
[    0.345394] pci_bus 0000:05: resource 0 [io  0x6000-0x6fff]
[    0.345400] pci_bus 0000:05: resource 1 [mem 0x86000000-0x861fffff]
[    0.345407] pci_bus 0000:05: resource 2 [mem 0x86200000-0x863fffff 64bit pref]
[    0.345413] pci_bus 0000:06: resource 0 [io  0x5000-0x5fff]
[    0.345419] pci_bus 0000:06: resource 1 [mem 0xda000000-0xda0fffff]
[    0.345425] pci_bus 0000:06: resource 2 [mem 0x80000000-0x85ffffff pref]
[    0.345431] pci_bus 0000:06: resource 4 [io  0x0000-0xffff]
[    0.345437] pci_bus 0000:06: resource 5 [mem 0x00000000-0xffffffff]
[    0.345443] pci_bus 0000:07: resource 0 [io  0x5400-0x54ff]
[    0.345449] pci_bus 0000:07: resource 1 [io  0x5800-0x58ff]
[    0.345455] pci_bus 0000:07: resource 2 [mem 0x80000000-0x83ffffff pref]
[    0.345461] pci_bus 0000:07: resource 3 [mem 0x88000000-0x8bffffff]
[    0.345554] NET: Registered protocol family 2
[    0.345709] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.346192] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.347415] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.348057] TCP: Hash tables configured (established 131072 bind 65536)
[    0.348063] TCP reno registered
[    0.348072] UDP hash table entries: 512 (order: 2, 16384 bytes)
[    0.348092] UDP-Lite hash table entries: 512 (order: 2, 16384 bytes)
[    0.348277] NET: Registered protocol family 1
[    0.348485] pci 0000:01:00.0: Boot video device
[    0.348531] PCI: CLS 64 bytes, default 64
[    0.348575] Simple Boot Flag at 0x36 set to 0x1
[    0.348960] cpufreq-nforce2: No nForce2 chipset.
[    0.349248] audit: initializing netlink socket (disabled)
[    0.349268] type=2000 audit(1305063881.344:1): initialized
[    0.370362] highmem bounce pool size: 64 pages
[    0.370375] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    0.374629] VFS: Disk quotas dquot_6.5.2
[    0.374773] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.376369] fuse init (API version 7.16)
[    0.376582] msgmni has been set to 1678
[    0.377090] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.377151] io scheduler noop registered
[    0.377156] io scheduler deadline registered
[    0.377191] io scheduler cfq registered (default)
[    0.377444] pcieport 0000:00:01.0: setting latency timer to 64
[    0.377507] pcieport 0000:00:01.0: irq 40 for MSI/MSI-X
[    0.377610] pcieport 0000:00:1c.0: setting latency timer to 64
[    0.377685] pcieport 0000:00:1c.0: irq 41 for MSI/MSI-X
[    0.377808] pcieport 0000:00:1c.1: setting latency timer to 64
[    0.377882] pcieport 0000:00:1c.1: irq 42 for MSI/MSI-X
[    0.378005] pcieport 0000:00:1c.2: setting latency timer to 64
[    0.378080] pcieport 0000:00:1c.2: irq 43 for MSI/MSI-X
[    0.378261] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.378320] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.378477] intel_idle: MWAIT substates: 0x22220
[    0.378481] intel_idle: does not run on family 6 model 14
[    0.588103] ACPI: Deprecated procfs I/F for AC is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
[    0.800137] ACPI: AC Adapter [ADP0] (on-line)
[    0.800557] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input0
[    0.825288] Freeing initrd memory: 12508k freed
[    0.844034] ACPI: Lid Switch [LID0]
[    0.844206] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1
[    0.852080] ACPI: Power Button [PWRB]
[    0.852194] input: Sleep Button as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input2
[    0.852260] ACPI: Sleep Button [SLPB]
[    0.852603] ACPI: acpi_idle registered with cpuidle
[    0.852882] Marking TSC unstable due to TSC halts in idle
[    1.213809] ACPI: Invalid passive threshold
[    1.612596] thermal LNXTHERM:00: registered as thermal_zone0
[    1.612605] ACPI: Thermal Zone [THM0] (39 C)
[    1.612647] ACPI: Deprecated procfs I/F for battery is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
[    1.612689] ACPI: Deprecated procfs I/F for battery is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
[    1.612809] ERST: Table is not found!
[    1.612971] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    1.613201] ACPI: Battery Slot [BAT1] (battery absent)
[    1.613240] isapnp: Scanning for PnP cards...
[    1.633690] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.665345] ACPI: Battery Slot [BAT0] (battery present)
[    1.708081] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 8250
[    1.967669] isapnp: No Plug & Play device found
[    2.012242] 00:09: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    2.012901] Linux agpgart interface v0.103
[    2.016240] brd: module loaded
[    2.017659] loop: module loaded
[    2.017850] i2c-core: driver [adp5520] using legacy suspend method
[    2.017855] i2c-core: driver [adp5520] using legacy resume method
[    2.018064] ata_piix 0000:00:1f.2: version 2.13
[    2.018103] ata_piix 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    2.018114] ata_piix 0000:00:1f.2: MAP [ P0 P2 IDE IDE ]
[    2.172026] ata_piix 0000:00:1f.2: applying IOCFG bit18 quirk
[    2.172047] ata_piix 0000:00:1f.2: setting latency timer to 64
[    2.172779] scsi0 : ata_piix
[    2.172990] scsi1 : ata_piix
[    2.174392] ata1: SATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0x18b0 irq 14
[    2.174400] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x18b8 irq 15
[    2.175247] Fixed MDIO Bus: probed
[    2.175339] PPP generic driver version 2.4.2
[    2.175430] tun: Universal TUN/TAP device driver, 1.6
[    2.175435] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    2.175640] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    2.175682] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    2.175702] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    2.175710] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    2.175797] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 1
[    2.175885] ehci_hcd 0000:00:1d.7: using broken periodic workaround
[    2.175905] ehci_hcd 0000:00:1d.7: debug port 1
[    2.179789] ehci_hcd 0000:00:1d.7: cache line size of 64 is not supported
[    2.179821] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xda304000
[    2.192027] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    2.192301] hub 1-0:1.0: USB hub found
[    2.192311] hub 1-0:1.0: 8 ports detected
[    2.192501] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    2.192533] uhci_hcd: USB Universal Host Controller Interface driver
[    2.192579] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    2.192592] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    2.192599] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    2.192683] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    2.192758] uhci_hcd 0000:00:1d.0: irq 23, io base 0x00001800
[    2.193030] hub 2-0:1.0: USB hub found
[    2.193040] hub 2-0:1.0: 2 ports detected
[    2.193192] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    2.193204] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    2.193211] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    2.193298] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3
[    2.193391] uhci_hcd 0000:00:1d.1: irq 19, io base 0x00001820
[    2.193669] hub 3-0:1.0: USB hub found
[    2.193679] hub 3-0:1.0: 2 ports detected
[    2.193830] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    2.193842] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    2.193849] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    2.193937] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4
[    2.196095] uhci_hcd 0000:00:1d.2: irq 18, io base 0x00001840
[    2.196373] hub 4-0:1.0: USB hub found
[    2.196382] hub 4-0:1.0: 2 ports detected
[    2.196534] uhci_hcd 0000:00:1d.3: PCI INT D -> GSI 16 (level, low) -> IRQ 16
[    2.196546] uhci_hcd 0000:00:1d.3: setting latency timer to 64
[    2.196553] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[    2.196651] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 5
[    2.196740] uhci_hcd 0000:00:1d.3: irq 16, io base 0x00001860
[    2.197009] hub 5-0:1.0: USB hub found
[    2.197018] hub 5-0:1.0: 2 ports detected
[    2.197306] i8042: PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    2.199557] i8042: Detected active multiplexing controller, rev 1.1
[    2.200658] serio: i8042 KBD port at 0x60,0x64 irq 1
[    2.200671] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[    2.200743] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[    2.200804] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[    2.200865] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[    2.201133] mousedev: PS/2 mouse device common for all mice
[    2.201601] rtc_cmos 00:08: rtc core: registered rtc_cmos as rtc0
[    2.201644] rtc0: alarms up to one month, y3k, 242 bytes nvram, hpet irqs
[    2.201825] device-mapper: uevent: version 1.0.3
[    2.202019] device-mapper: ioctl: 4.19.1-ioctl (2011-01-07) initialised: dm-devel@redhat.com
[    2.202156] device-mapper: multipath: version 1.2.0 loaded
[    2.202162] device-mapper: multipath round-robin: version 1.0.0 loaded
[    2.202320] EISA: Probing bus 0 at eisa.0
[    2.202331] Cannot allocate resource for EISA slot 1
[    2.202336] Cannot allocate resource for EISA slot 2
[    2.202341] Cannot allocate resource for EISA slot 3
[    2.202346] Cannot allocate resource for EISA slot 4
[    2.202351] Cannot allocate resource for EISA slot 5
[    2.202356] Cannot allocate resource for EISA slot 6
[    2.202371] EISA: Detected 0 cards.
[    2.202597] cpuidle: using governor ladder
[    2.202775] cpuidle: using governor menu
[    2.203421] TCP cubic registered
[    2.203724] NET: Registered protocol family 10
[    2.205100] NET: Registered protocol family 17
[    2.205133] Registering the dns_resolver key type
[    2.205694] Using IPI No-Shortcut mode
[    2.205897] PM: Hibernation image not present or could not be loaded.
[    2.205911] registered taskstats version 1
[    2.206273]   Magic number: 11:656:752
[    2.206293] tty ttyS3: hash matches
[    2.206375] rtc_cmos 00:08: setting system clock to 2011-05-10 21:44:44 UTC (1305063884)
[    2.206379] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    2.206381] EDD information not available.
[    2.223139] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3
[    2.336664] ata1.00: ATA-7: HTS721010G9SA00, MCZOC10H, max UDMA/100
[    2.336671] ata1.00: 195371568 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    2.352823] ata2.01: ATAPI: PIONEER DVD-RW  DVR-K16, 1.44, max UDMA/33
[    2.353617] ata1.00: configured for UDMA/100
[    2.353890] scsi 0:0:0:0: Direct-Access     ATA      HTS721010G9SA00  MCZO PQ: 0 ANSI: 5
[    2.354079] sd 0:0:0:0: [sda] 195371568 512-byte logical blocks: (100 GB/93.1 GiB)
[    2.354098] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    2.354141] sd 0:0:0:0: [sda] Write Protect is off
[    2.354145] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    2.354209] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.384848] ata2.01: configured for UDMA/33
[    2.403582]  sda: sda1 sda2 < sda5 > sda3 sda4
[    2.404293] sd 0:0:0:0: [sda] Attached SCSI disk
[    2.406883] scsi 1:0:1:0: CD-ROM            PIONEER  DVD-RW  DVR-K16  1.44 PQ: 0 ANSI: 5
[    2.419026] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[    2.419032] cdrom: Uniform CD-ROM driver Revision: 3.20
[    2.419241] sr 1:0:1:0: Attached scsi CD-ROM sr0
[    2.419379] sr 1:0:1:0: Attached scsi generic sg1 type 5
[    2.419514] Freeing unused kernel memory: 700k freed
[    2.419825] Write protecting the kernel text: 5192k
[    2.419883] Write protecting the kernel read-only data: 2148k
[    2.443004] <30>udev[70]: starting version 167
[    2.872066] usb 5-2: new full speed USB device using uhci_hcd and address 2
[    2.965374] sdhci: Secure Digital Host Controller Interface driver
[    2.965378] sdhci: Copyright(c) Pierre Ossman
[    2.970990] firewire_ohci 0000:06:07.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    3.024141] firewire_ohci: Added fw-ohci device 0000:06:07.1, OHCI v1.10, 4 IR + 8 IT contexts, quirks 0x2
[    3.024222] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    3.024259] r8169 0000:06:0b.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    3.024303] r8169 0000:06:0b.0: (unregistered net_device): no PCI Express capability
[    3.024918] r8169 0000:06:0b.0: eth0: RTL8169sb/8110sb at 0xf8022400, 00:90:f5:4f:f8:1a, XID 10000000 IRQ 17
[    3.040104] sdhci-pci 0000:06:07.3: SDHCI controller found [104c:803c] (rev 0)
[    3.040128] sdhci-pci 0000:06:07.3: PCI INT D -> GSI 19 (level, low) -> IRQ 19
[    3.040173] mmc0: no vmmc regulator found
[    3.040252] Registered led device: mmc0::
[    3.040348] mmc0: SDHCI controller on PCI [0000:06:07.3] using PIO
[    3.083812] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:1d.3/usb5/5-2/5-2:1.0/input/input4
[    3.083950] generic-usb 0003:046D:C51A.0001: input,hidraw0: USB HID v1.11 Mouse [Logitech USB Receiver] on usb-0000:00:1d.3-2/input0
[    3.091049] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:1d.3/usb5/5-2/5-2:1.1/input/input5
[    3.091261] generic-usb 0003:046D:C51A.0002: input,hiddev0,hidraw1: USB HID v1.11 Device [Logitech USB Receiver] on usb-0000:00:1d.3-2/input1
[    3.091277] usbcore: registered new interface driver usbhid
[    3.091279] usbhid: USB HID core driver
[    3.524231] firewire_core: created device fw0: GUID 08003856004ff81a, S400
[    3.548326] EXT4-fs (sda4): mounted filesystem with ordered data mode. Opts: (null)
[   27.433006] <30>udev[299]: starting version 167
[   27.452384] Adding 489976k swap on /dev/sda3.  Priority:-1 extents:1 across:489976k 
[   27.466729] lp: driver loaded but no devices found
[   27.882205] EXT4-fs (sda4): re-mounted. Opts: errors=remount-ro
[   28.086835] type=1400 audit(1305078310.375:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=415 comm="apparmor_parser"
[   28.087651] type=1400 audit(1305078310.375:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=415 comm="apparmor_parser"
[   28.088197] type=1400 audit(1305078310.379:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=415 comm="apparmor_parser"
[   28.193923] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:01/LNXVIDEO:00/input/input6
[   28.194024] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[   28.217674] r8169 0000:06:0b.0: eth0: link down
[   28.218090] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   28.340292] intel_rng: FWH not detected
[   28.424170] tifm_7xx1 0000:06:07.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[   28.442428] Linux video capture interface: v2.00
[   28.444916] yenta_cardbus 0000:06:07.0: CardBus bridge found [1558:0571]
[   28.444939] yenta_cardbus 0000:06:07.0: Enabling burst memory read transactions
[   28.444945] yenta_cardbus 0000:06:07.0: Using CSCINT to route CSC interrupts to PCI
[   28.444948] yenta_cardbus 0000:06:07.0: Routing CardBus interrupts to PCI
[   28.444955] yenta_cardbus 0000:06:07.0: TI: mfunc 0x01aa1b22, devctl 0x64
[   28.542460] type=1400 audit(1305078310.831:5): apparmor="STATUS" operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" pid=664 comm="apparmor_parser"
[   28.549696] type=1400 audit(1305078310.839:6): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=665 comm="apparmor_parser"
[   28.550864] type=1400 audit(1305078310.839:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=665 comm="apparmor_parser"
[   28.554224] type=1400 audit(1305078310.843:8): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=665 comm="apparmor_parser"
[   28.559161] cfg80211: Calling CRDA to update world regulatory domain
[   28.562784] type=1400 audit(1305078310.851:9): apparmor="STATUS" operation="profile_load" name="/usr/bin/freshclam" pid=669 comm="apparmor_parser"
[   28.570475] type=1400 audit(1305078310.859:10): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=674 comm="apparmor_parser"
[   28.571447] type=1400 audit(1305078310.859:11): apparmor="STATUS" operation="profile_load" name="/usr/sbin/cupsd" pid=674 comm="apparmor_parser"
[   28.609905] nvidia: module license 'NVIDIA' taints kernel.
[   28.609910] Disabling lock debugging due to kernel taint
[   28.633432] IR NEC protocol handler initialized
[   28.640552] psmouse serio4: ID: 10 00 64
[   28.654849] IR RC5(x) protocol handler initialized
[   28.665896] IR RC6 protocol handler initialized
[   28.672909] IR JVC protocol handler initialized
[   28.782289] yenta_cardbus 0000:06:07.0: ISA IRQ mask 0x0cf0, PCI irq 16
[   28.782293] yenta_cardbus 0000:06:07.0: Socket status: 30000006
[   28.782298] pci_bus 0000:06: Raising subordinate bus# of parent bus (#06) from #07 to #0a
[   28.782307] yenta_cardbus 0000:06:07.0: pcmcia: parent PCI bridge window: [io  0x5000-0x5fff]
[   28.782310] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x5000-0x5fff: excluding 0x5000-0x50ff 0x5400-0x54ff 0x5800-0x58ff
[   28.796919] yenta_cardbus 0000:06:07.0: pcmcia: parent PCI bridge window: [mem 0xda000000-0xda0fffff]
[   28.796924] pcmcia_socket pcmcia_socket0: cs: memory probe 0xda000000-0xda0fffff: excluding 0xda000000-0xda00ffff
[   28.796939] yenta_cardbus 0000:06:07.0: pcmcia: parent PCI bridge window: [mem 0x80000000-0x85ffffff pref]
[   28.796942] pcmcia_socket pcmcia_socket0: cs: memory probe 0x80000000-0x85ffffff: excluding 0x80000000-0x85ffffff
[   28.811567] IR Sony protocol handler initialized
[   28.811921] cfg80211: World regulatory domain updated:
[   28.811923] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   28.811926] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   28.811929] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   28.811931] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   28.811934] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   28.811937] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   28.812620] irda_init()
[   28.812634] NET: Registered protocol family 23
[   28.817976] saa7130/34: v4l2 driver version 0.2.16 loaded
[   28.822743] nsc_ircc_pnp_probe() : From PnP, found firbase 0x2F8 ; irq 3 ; dma 3.
[   28.822805] nsc-ircc, chip->init
[   28.822819] nsc-ircc, Found chip at base=0x02e
[   28.822857] nsc-ircc, driver loaded (Dag Brattli)
[   28.823387] nsc_ircc_open(), can't get iobase of 0x2f8
[   28.823433] nsc-ircc, Found chip at base=0x02e
[   28.823471] nsc-ircc, driver loaded (Dag Brattli)
[   28.823475] nsc_ircc_open(), can't get iobase of 0x2f8
[   28.823491] nsc-ircc, chip->init
[   28.823504] nsc-ircc, Found chip at base=0x02e
[   28.823542] nsc-ircc, driver loaded (Dag Brattli)
[   28.824369] saa7134 0000:06:04.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[   28.824378] saa7133[0]: found at 0000:06:04.0, rev: 209, irq: 18, latency: 181, mmio: 0xda006000
[   28.824387] saa7133[0]: subsystem: 5168:3307, board: LifeView FlyDVB-T Hybrid Cardbus/MSI TV @nywhere A/D NB [card=94,autodetected]
[   28.824405] saa7133[0]: board init: gpio is 10000
[   28.828864] nsc-ircc 00:0a: disabled
[   28.896606] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, in-tree:s
[   28.896610] iwl3945: Copyright(c) 2003-2010 Intel Corporation
[   28.896682] iwl3945 0000:02:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   28.896697] iwl3945 0000:02:00.0: setting latency timer to 64
[   28.950705] iwl3945 0000:02:00.0: Tunable channels: 11 802.11bg, 13 802.11a channels
[   28.950709] iwl3945 0000:02:00.0: Detected Intel Wireless WiFi Link 3945ABG
[   28.950858] iwl3945 0000:02:00.0: irq 44 for MSI/MSI-X
[   28.992448] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain 
[   29.032330] ieee80211 phy0: Selected rate control algorithm 'iwl-3945-rs'
[   29.054576] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   29.054637] HDA Intel 0000:00:1b.0: irq 45 for MSI/MSI-X
[   29.054669] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   29.084845] saa7133[0]: i2c eeprom 00: 68 51 07 33 54 20 1c 00 43 43 a9 1c 55 d2 b2 92
[   29.084858] saa7133[0]: i2c eeprom 10: 00 00 62 08 ff 20 ff ff ff ff ff ff ff ff ff ff
[   29.084869] saa7133[0]: i2c eeprom 20: 01 40 01 03 03 01 01 03 08 ff 01 17 ff ff ff ff
[   29.084880] saa7133[0]: i2c eeprom 30: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   29.084891] saa7133[0]: i2c eeprom 40: ff 21 00 c2 96 10 05 01 01 16 22 15 ff ff ff ff
[   29.084902] saa7133[0]: i2c eeprom 50: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   29.084913] saa7133[0]: i2c eeprom 60: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   29.084924] saa7133[0]: i2c eeprom 70: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   29.084935] saa7133[0]: i2c eeprom 80: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   29.084946] saa7133[0]: i2c eeprom 90: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   29.084957] saa7133[0]: i2c eeprom a0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   29.084968] saa7133[0]: i2c eeprom b0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   29.084978] saa7133[0]: i2c eeprom c0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   29.084989] saa7133[0]: i2c eeprom d0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   29.085000] saa7133[0]: i2c eeprom e0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   29.085011] saa7133[0]: i2c eeprom f0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   29.107085] i2c-core: driver [tuner] using legacy suspend method
[   29.107088] i2c-core: driver [tuner] using legacy resume method
[   29.166030] tuner 0-004b: chip found @ 0x96 (saa7133[0])
[   29.177325] hda_codec: ALC880: BIOS auto-probing.
[   29.256033] tda829x 0-004b: setting tuner address to 61
[   29.320026] tda829x 0-004b: type set to tda8290+75a
[   29.806407] lirc_dev: IR Remote Control driver registered, major 249 
[   29.809025] IR LIRC bridge handler initialized
[   29.835691] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x100-0x3af: excluding 0x170-0x177 0x1f0-0x1f7 0x2f8-0x2ff 0x370-0x377
[   29.837700] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x3e0-0x4ff: excluding 0x3f0-0x3ff 0x4d0-0x4d7
[   29.838523] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x820-0x8ff: clean.
[   29.839223] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xc00-0xcf7: clean.
[   29.839989] pcmcia_socket pcmcia_socket0: cs: memory probe 0x0c0000-0x0fffff: excluding 0xc0000-0xcffff 0xe0000-0xfffff
[   29.840336] pcmcia_socket pcmcia_socket0: cs: memory probe 0xa0000000-0xa0ffffff: clean.
[   29.840401] pcmcia_socket pcmcia_socket0: cs: memory probe 0x60000000-0x60ffffff: excluding 0x60000000-0x60ffffff
[   29.840465] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xa00-0xaff: clean.
[   30.051791] nvidia 0000:01:00.0: power state changed by ACPI to D0
[   30.051796] nvidia 0000:01:00.0: power state changed by ACPI to D0
[   30.051806] nvidia 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   30.051815] nvidia 0000:01:00.0: setting latency timer to 64
[   30.051822] vgaarb: device changed decodes: PCI:0000:01:00.0,olddecodes=io+mem,decodes=none:owns=io+mem
[   30.052444] NVRM: loading NVIDIA UNIX x86 Kernel Module  270.41.06  Mon Apr 18 14:54:25 PDT 2011
[   30.083127] iwl3945 0000:02:00.0: loaded firmware version 15.32.2.9
[   30.100991] elantech: assuming hardware version 1, firmware version 2.0.0
[   30.132061] elantech: Synaptics capabilities query result 0x06, 0x02, 0x64.
[   30.160546] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   30.336472] cfg80211: Found new beacon on frequency: 5180 MHz (Ch 36) on phy0
[   30.350907] elantech: touchpad refuses to switch to absolute mode.
[   30.350913] elantech: failed to initialise registers.
[   30.350915] elantech: failed to put touchpad into absolute mode.
[   30.811029] input: ImPS/2 Elantech Touchpad as /devices/platform/i8042/serio4/input/input7
[   32.340579] EXT4-fs (sda4): re-mounted. Opts: errors=remount-ro,commit=0
[   33.096244] saa7133[0]: registered device video0 [v4l2]
[   33.096318] saa7133[0]: registered device vbi0
[   33.096390] saa7133[0]: registered device radio0
[   33.108243] saa7134 ALSA driver for DMA sound loaded
[   33.108286] saa7133[0]/alsa: saa7133[0] at 0xda006000 irq 18 registered as card -2
[   33.133052] dvb_init() allocating 1 frontend
[   33.516158] DVB: registering new adapter (saa7133[0])
[   33.516167] DVB: registering adapter 0 frontend 0 (Philips TDA10046H DVB-T)...
[   33.636039] tda1004x: setting up plls for 48MHz sampling clock
[   33.810334] tda1004x: found firmware revision ea -- invalid
[   33.810338] tda1004x: trying to boot from eeprom
[   34.121129] tda1004x: found firmware revision ea -- invalid
[   34.121133] tda1004x: waiting for firmware upload...
[   34.142432] tda1004x: no firmware upload (timeout or file not found?)
[   34.142440] tda1004x: firmware upload failed
[   34.164347] tda827x_probe_version: could not read from tuner at addr: 0xc2
[   34.469040] vesafb: framebuffer at 0xc0000000, mapped to 0xf8480000, using 5120k, total 5120k
[   34.469045] vesafb: mode is 1280x1024x32, linelength=5120, pages=0
[   34.469047] vesafb: scrolling: redraw
[   34.469050] vesafb: Truecolor: size=8:8:8:8, shift=24:16:8:0
[   34.469274] Console: switching to colour frame buffer device 160x64
[   34.469318] fb0: VESA VGA frame buffer device
[   34.497455] ppdev: user-space parallel port driver
[   34.521358] audit_printk_skb: 18 callbacks suppressed
[   34.521362] type=1400 audit(1305078316.811:18): apparmor="STATUS" operation="profile_replace" name="/usr/lib/cups/backend/cups-pdf" pid=1258 comm="apparmor_parser"
[   34.522339] type=1400 audit(1305078316.811:19): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/cupsd" pid=1258 comm="apparmor_parser"
[   42.682701] EXT4-fs (sda4): re-mounted. Opts: errors=remount-ro,commit=0
[  185.521692] wlan0: authenticate with 00:0f:b5:92:d3:ad (try 1)
[  185.524837] wlan0: authenticated
[  185.525901] wlan0: associate with 00:0f:b5:92:d3:ad (try 1)
[  185.529132] wlan0: RX AssocResp from 00:0f:b5:92:d3:ad (capab=0x431 status=0 aid=1)
[  185.529140] wlan0: associated
[  185.532515] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  185.532596] cfg80211: Calling CRDA for country: US
[  185.538419] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[  185.538425] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2700 mBm)
[  185.538428] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
[  185.538433] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2700 mBm)
[  185.538436] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
[  185.538440] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2700 mBm)
[  185.538444] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
[  185.538448] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2700 mBm)
[  185.538451] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
[  185.538455] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2700 mBm)
[  185.538459] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
[  185.538463] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2700 mBm)
[  185.538466] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
[  185.538470] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2700 mBm)
[  185.538474] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
[  185.538478] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2700 mBm)
[  185.538481] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
[  185.538485] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2700 mBm)
[  185.538489] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
[  185.538493] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2700 mBm)
[  185.538496] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[  185.538500] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2700 mBm)
[  185.538504] cfg80211: Updating information on frequency 5180 MHz for a 20 MHz width channel with regulatory rule:
[  185.538508] cfg80211: 5170000 KHz - 5250000 KHz @  KHz), (300 mBi, 1700 mBm)
[  185.538511] cfg80211: Updating information on frequency 5200 MHz for a 20 MHz width channel with regulatory rule:
[  185.538515] cfg80211: 5170000 KHz - 5250000 KHz @  KHz), (300 mBi, 1700 mBm)
[  185.538519] cfg80211: Updating information on frequency 5220 MHz for a 20 MHz width channel with regulatory rule:
[  185.538523] cfg80211: 5170000 KHz - 5250000 KHz @  KHz), (300 mBi, 1700 mBm)
[  185.538526] cfg80211: Updating information on frequency 5240 MHz for a 20 MHz width channel with regulatory rule:
[  185.538530] cfg80211: 5170000 KHz - 5250000 KHz @  KHz), (300 mBi, 1700 mBm)
[  185.538534] cfg80211: Updating information on frequency 5260 MHz for a 20 MHz width channel with regulatory rule:
[  185.538538] cfg80211: 5250000 KHz - 5330000 KHz @  KHz), (300 mBi, 2000 mBm)
[  185.538541] cfg80211: Updating information on frequency 5280 MHz for a 20 MHz width channel with regulatory rule:
[  185.538545] cfg80211: 5250000 KHz - 5330000 KHz @  KHz), (300 mBi, 2000 mBm)
[  185.538549] cfg80211: Updating information on frequency 5300 MHz for a 20 MHz width channel with regulatory rule:
[  185.538553] cfg80211: 5250000 KHz - 5330000 KHz @  KHz), (300 mBi, 2000 mBm)
[  185.538556] cfg80211: Updating information on frequency 5320 MHz for a 20 MHz width channel with regulatory rule:
[  185.538560] cfg80211: 5250000 KHz - 5330000 KHz @  KHz), (300 mBi, 2000 mBm)
[  185.538564] cfg80211: Updating information on frequency 5745 MHz for a 20 MHz width channel with regulatory rule:
[  185.538568] cfg80211: 5735000 KHz - 5835000 KHz @  KHz), (300 mBi, 3000 mBm)
[  185.538571] cfg80211: Updating information on frequency 5765 MHz for a 20 MHz width channel with regulatory rule:
[  185.538575] cfg80211: 5735000 KHz - 5835000 KHz @  KHz), (300 mBi, 3000 mBm)
[  185.538579] cfg80211: Updating information on frequency 5785 MHz for a 20 MHz width channel with regulatory rule:
[  185.538583] cfg80211: 5735000 KHz - 5835000 KHz @  KHz), (300 mBi, 3000 mBm)
[  185.538586] cfg80211: Updating information on frequency 5805 MHz for a 20 MHz width channel with regulatory rule:
[  185.538590] cfg80211: 5735000 KHz - 5835000 KHz @  KHz), (300 mBi, 3000 mBm)
[  185.538594] cfg80211: Updating information on frequency 5825 MHz for a 20 MHz width channel with regulatory rule:
[  185.538598] cfg80211: 5735000 KHz - 5835000 KHz @  KHz), (300 mBi, 3000 mBm)
[  185.538602] cfg80211: Regulatory domain changed to country: US
[  185.538604] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[  185.538609] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[  185.538613] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 1700 mBm)
[  185.538617] cfg80211:     (5250000 KHz - 5330000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  185.538621] cfg80211:     (5490000 KHz - 5600000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  185.538624] cfg80211:     (5650000 KHz - 5710000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  185.538628] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 3000 mBm)
[  185.905514] Intel AES-NI instructions are not detected.
[  186.048095] padlock_aes: VIA PadLock not detected.
[  196.184029] wlan0: no IPv6 routers present
```

---

