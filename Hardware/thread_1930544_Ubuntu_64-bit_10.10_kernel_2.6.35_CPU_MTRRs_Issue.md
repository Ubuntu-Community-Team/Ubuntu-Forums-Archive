---
title: "Ubuntu 64-bit 10.10 kernel 2.6.35 CPU MTRRs Issue"
date: 2012-02-23
forum: Hardware
---

### Post by LinuxSailor on 2012-02-23
All,

First post here on the forum.  I would like to report an issue with Ubuntu 10.10 on 64-bit kernel 2.6.35 that is not present in 10.04 LTS 64-bit on kernel 2.6.32.

I have a Gigabyte GA-970A-UD3, AMD FX-8120 CPU, 16GB DDR3-1333 RAM, nVidia GTX550Ti and an OCZ Agility 3 120GB SSD.  The BIOS reports 16GB RAM installed.  

When I installed Ubuntu 10.10 to get the later kernel with TRIM support for the SSD, the OS is only reporting 3.2GiB available instead of the 15.7GiB I am expecting.  

Research has revealed the following from dmesg (relevant section bolded):

```

[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.35-22-generic (buildd@allspice) (gcc version 4.4.5 (Ubuntu/Linaro 4.4.4-14ubuntu4) ) #33-Ubuntu SMP Sun Sep 19 20:32:27 UTC 2010 (Ubuntu 2.6.35-22.33-generic 2.6.35.4)
[    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-2.6.35-22-generic root=UUID=9129347f-e2a2-4b97-965c-800823aaf090 ro quiet splash
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009a000 (usable)
[    0.000000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 00000000cfda0000 (usable)
[    0.000000]  BIOS-e820: 00000000cfda0000 - 00000000cfdd1000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000cfdd1000 - 00000000cfe00000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000cfe00000 - 00000000cff00000 (reserved)
[    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 0000000100000000 (reserved)
[    0.000000]  BIOS-e820: 0000000100000000 - 000000042f000000 (usable)
[    0.000000] NX (Execute Disable) protection: active
[    0.000000] DMI 2.4 present.
[    0.000000] e820 update range: 0000000000000000 - 0000000000001000 (usable) ==> (reserved)
[    0.000000] e820 remove range: 00000000000a0000 - 0000000000100000 (usable)
[    0.000000] No AGP bridge found
[    0.000000] last_pfn = 0x42f000 max_arch_pfn = 0x400000000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-C7FFF write-protect
[    0.000000]   C8000-FFFFF uncachable
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000000 mask FFFF80000000 write-back
[    0.000000]   1 base 000080000000 mask FFFFC0000000 write-back
[    0.000000]   2 base 0000C0000000 mask FFFFF0000000 write-back
[    0.000000]   3 base 0000CFE00000 mask FFFFFFE00000 uncachable
[    0.000000]   4 disabled
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] e820 update range: 00000000cfe00000 - 000000042f000000 (usable) ==> (reserved)
[B][    0.000000] WARNING: BIOS bug: CPU MTRRs don't cover all of memory, losing 13040MB of RAM.
[    0.000000] ------------[ cut here ]------------
[    0.000000] WARNING: at /build/buildd/linux-2.6.35/arch/x86/kernel/cpu/mtrr/cleanup.c:971 mtrr_trim_uncached_memory+0x2d8/0x303()
[    0.000000] Hardware name: GA-970A-UD3
[    0.000000] Modules linked in:
[    0.000000] Pid: 0, comm: swapper Not tainted 2.6.35-22-generic #33-Ubuntu
[    0.000000] Call Trace:
[    0.000000]  [<ffffffff8106077f>] warn_slowpath_common+0x7f/0xc0
[    0.000000]  [<ffffffff810607da>] warn_slowpath_null+0x1a/0x20
[    0.000000]  [<ffffffff81af7970>] mtrr_trim_uncached_memory+0x2d8/0x303
[    0.000000]  [<ffffffff81af2910>] setup_arch+0x422/0x79e
[    0.000000]  [<ffffffff815864c9>] ? printk+0x68/0x6f
[    0.000000]  [<ffffffff81aed9f3>] start_kernel+0xdd/0x390
[    0.000000]  [<ffffffff81aed341>] x86_64_start_reservations+0x12c/0x130
[    0.000000]  [<ffffffff81aed43f>] x86_64_start_kernel+0xfa/0x109
[    0.000000] ---[ end trace a7919e7f17c0a725 ]---[/B]
[    0.000000] update e820 for mtrr
[    0.000000] modified physical RAM map:
[    0.000000]  modified: 0000000000000000 - 0000000000001000 (reserved)
[    0.000000]  modified: 0000000000001000 - 000000000009a000 (usable)
[    0.000000]  modified: 000000000009f800 - 00000000000a0000 (reserved)
[    0.000000]  modified: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  modified: 0000000000100000 - 00000000cfda0000 (usable)
[    0.000000]  modified: 00000000cfda0000 - 00000000cfdd1000 (ACPI NVS)
[    0.000000]  modified: 00000000cfdd1000 - 00000000cfe00000 (ACPI data)
[    0.000000]  modified: 00000000cfe00000 - 00000000cff00000 (reserved)
[    0.000000]  modified: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  modified: 00000000fec00000 - 000000042f000000 (reserved)
[    0.000000] last_pfn = 0xcfda0 max_arch_pfn = 0x400000000
[    0.000000] e820 update range: 0000000000001000 - 0000000000010000 (usable) ==> (reserved)
[    0.000000] Scanning 1 areas for low memory corruption
[    0.000000] modified physical RAM map:
[    0.000000]  modified: 0000000000000000 - 0000000000010000 (reserved)
[    0.000000]  modified: 0000000000010000 - 000000000009a000 (usable)
[    0.000000]  modified: 000000000009f800 - 00000000000a0000 (reserved)
[    0.000000]  modified: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  modified: 0000000000100000 - 00000000cfda0000 (usable)
[    0.000000]  modified: 00000000cfda0000 - 00000000cfdd1000 (ACPI NVS)
[    0.000000]  modified: 00000000cfdd1000 - 00000000cfe00000 (ACPI data)
[    0.000000]  modified: 00000000cfe00000 - 00000000cff00000 (reserved)
[    0.000000]  modified: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  modified: 00000000fec00000 - 000000042f000000 (reserved)
[    0.000000] initial memory mapped : 0 - 20000000
[    0.000000] found SMP MP-table at [ffff8800000f4b30] f4b30
[    0.000000] Using GB pages for direct mapping
[    0.000000] init_memory_mapping: 0000000000000000-00000000cfda0000
[    0.000000]  0000000000 - 00c0000000 page 1G
[    0.000000]  00c0000000 - 00cfc00000 page 2M
[    0.000000]  00cfc00000 - 00cfda0000 page 4k
[    0.000000] kernel direct mapping tables up to cfda0000 @ 16000-19000
[    0.000000] RAMDISK: 37571000 - 37ff0000
[    0.000000] ACPI: RSDP 00000000000f6a50 00014 (v00 GBT   )
[    0.000000] ACPI: RSDT 00000000cfdd1000 00048 (v01 GBT    GBTUACPI 42302E31 GBTU 01010101)
[    0.000000] ACPI: FACP 00000000cfdd1080 00074 (v01 GBT    GBTUACPI 42302E31 GBTU 01010101)
[    0.000000] ACPI: DSDT 00000000cfdd1100 0792A (v01 GBT    GBTUACPI 00001000 MSFT 03000000)
[    0.000000] ACPI: FACS 00000000cfda0000 00040
[    0.000000] ACPI: MSDM 00000000cfdd8b00 00055 (v03 GBT    GBTUACPI 42302E31 GBTU 01010101)
[    0.000000] ACPI: HPET 00000000cfdd8b80 00038 (v01 GBT    GBTUACPI 42302E31 GBTU 00000098)
[    0.000000] ACPI: MCFG 00000000cfdd8bc0 0003C (v01 GBT    GBTUACPI 42302E31 GBTU 01010101)
[    0.000000] ACPI: MATS 00000000cfdd8c40 00034 (v01 GBT             00000000      00000000)
[    0.000000] ACPI: TAMG 00000000cfdd8cb0 00202 (v01 GBT    GBT   B0 5455312E BG?? 53450101)
[    0.000000] ACPI: APIC 00000000cfdd8a40 000BC (v01 GBT    GBTUACPI 42302E31 GBTU 01010101)
[    0.000000] ACPI: MATS 00000000cfdd8ec0 061FD (v01        MATS RCM 80000001 INTL 20061109)
[    0.000000] ACPI: SSDT 00000000cfddf130 01714 (v01 AMD    POWERNOW 00000001 AMD  00000001)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at 0000000000000000-00000000cfda0000
[    0.000000] Initmem setup node 0 0000000000000000-00000000cfda0000
[    0.000000]   NODE_DATA [0000000001d18100 - 0000000001d1d0ff]
[    0.000000]  [ffffea0000000000-ffffea0002dfffff] PMD -> [ffff880002600000-ffff8800053fffff] on node 0
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   DMA32    0x00001000 -> 0x00100000
[    0.000000]   Normal   empty
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[2] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x0000009a
[    0.000000]     0: 0x00000100 -> 0x000cfda0
[    0.000000] On node 0 totalpages: 851242
[    0.000000]   DMA zone: 56 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3922 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 11584 pages used for memmap
[    0.000000]   DMA32 zone: 835680 pages, LIFO batch:31
[    0.000000] ACPI: PM-Timer IO Port: 0x808
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x02] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x03] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x04] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x05] lapic_id[0x05] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x06] lapic_id[0x06] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x07] lapic_id[0x07] enabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] dfl dfl lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] dfl dfl lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x02] dfl dfl lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x03] dfl dfl lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x04] dfl dfl lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x05] dfl dfl lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x06] dfl dfl lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x07] dfl dfl lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x08] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 8, version 33, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 low level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x10b9a201 base: 0xfed00000
[    0.000000] SMP: Allowing 8 CPUs, 0 hotplug CPUs
[    0.000000] nr_irqs_gsi: 40
[    0.000000] early_res array is doubled to 64 at [18000 - 187ff]
[    0.000000] PM: Registered nosave memory: 000000000009a000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000f0000
[    0.000000] PM: Registered nosave memory: 00000000000f0000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at cff00000 (gap: cff00000:10100000)
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] setup_percpu: NR_CPUS:64 nr_cpumask_bits:64 nr_cpu_ids:8 nr_node_ids:1
[    0.000000] PERCPU: Embedded 30 pages/cpu @ffff880001e00000 s91520 r8192 d23168 u262144
[    0.000000] pcpu-alloc: s91520 r8192 d23168 u262144 alloc=1*2097152
[    0.000000] pcpu-alloc: [0] 0 1 2 3 4 5 6 7 
[    0.000000] Built 1 zonelists in Node order, mobility grouping on.  Total pages: 839602
[    0.000000] Policy zone: DMA32
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.35-22-generic root=UUID=9129347f-e2a2-4b97-965c-800823aaf090 ro quiet splash
[    0.000000] PID hash table entries: 4096 (order: 3, 32768 bytes)
[    0.000000] xsave/xrstor: enabled xstate_bv 0x7, cntxt size 0x340
[    0.000000] Checking aperture...
[    0.000000] No AGP bridge found
[    0.000000] Calgary: detecting Calgary via BIOS EBDA area
[    0.000000] Calgary: Unable to locate Rio Grande table in EBDA - bailing!
[    0.000000] Subtract (54 early reservations)
[    0.000000]   #1 [0001000000 - 0001d17114]   TEXT DATA BSS
[    0.000000]   #2 [0037571000 - 0037ff0000]         RAMDISK
[    0.000000]   #3 [0001d18000 - 0001d180f6]             BRK
[    0.000000]   #4 [00000f4b40 - 0000100000]   BIOS reserved
[    0.000000]   #5 [00000f4b30 - 00000f4b40]    MP-table mpf
[    0.000000]   #6 [000009a000 - 00000f1a54]   BIOS reserved
[    0.000000]   #7 [00000f1c68 - 00000f4b30]   BIOS reserved
[    0.000000]   #8 [00000f1a54 - 00000f1c68]    MP-table mpc
[    0.000000]   #9 [0000010000 - 0000012000]      TRAMPOLINE
[    0.000000]   #10 [0000012000 - 0000016000]     ACPI WAKEUP
[    0.000000]   #11 [0000016000 - 0000018000]         PGTABLE
[    0.000000]   #12 [0001d18100 - 0001d1d100]       NODE_DATA
[    0.000000]   #13 [0001d1d100 - 0001d1e100]         BOOTMEM
[    0.000000]   #14 [0001d17140 - 0001d173b0]         BOOTMEM
[    0.000000]   #15 [000251f000 - 0002520000]         BOOTMEM
[    0.000000]   #16 [0002520000 - 0002521000]         BOOTMEM
[    0.000000]   #17 [0002600000 - 0005400000]        MEMMAP 0
[    0.000000]   #18 [0001d173c0 - 0001d17540]         BOOTMEM
[    0.000000]   #19 [0001d1e100 - 0001d36100]         BOOTMEM
[    0.000000]   #20 [0001d37000 - 0001d38000]         BOOTMEM
[    0.000000]   #21 [0001d17540 - 0001d17581]         BOOTMEM
[    0.000000]   #22 [0001d175c0 - 0001d17603]         BOOTMEM
[    0.000000]   #23 [0001d17640 - 0001d17870]         BOOTMEM
[    0.000000]   #24 [0001d17880 - 0001d178e8]         BOOTMEM
[    0.000000]   #25 [0001d17900 - 0001d17968]         BOOTMEM
[    0.000000]   #26 [0001d17980 - 0001d179e8]         BOOTMEM
[    0.000000]   #27 [0001d17a00 - 0001d17a68]         BOOTMEM
[    0.000000]   #28 [0001d17a80 - 0001d17ae8]         BOOTMEM
[    0.000000]   #29 [0001d17b00 - 0001d17b68]         BOOTMEM
[    0.000000]   #30 [0001d17b80 - 0001d17be8]         BOOTMEM
[    0.000000]   #31 [0001d17c00 - 0001d17c68]         BOOTMEM
[    0.000000]   #32 [0001d17c80 - 0001d17ce8]         BOOTMEM
[    0.000000]   #33 [0001d17d00 - 0001d17d68]         BOOTMEM
[    0.000000]   #34 [0001d17d80 - 0001d17da0]         BOOTMEM
[    0.000000]   #35 [0001d17dc0 - 0001d17e2a]         BOOTMEM
[    0.000000]   #36 [0001d17e40 - 0001d17eaa]         BOOTMEM
[    0.000000]   #37 [0001e00000 - 0001e1e000]         BOOTMEM
[    0.000000]   #38 [0001e40000 - 0001e5e000]         BOOTMEM
[    0.000000]   #39 [0001e80000 - 0001e9e000]         BOOTMEM
[    0.000000]   #40 [0001ec0000 - 0001ede000]         BOOTMEM
[    0.000000]   #41 [0001f00000 - 0001f1e000]         BOOTMEM
[    0.000000]   #42 [0001f40000 - 0001f5e000]         BOOTMEM
[    0.000000]   #43 [0001f80000 - 0001f9e000]         BOOTMEM
[    0.000000]   #44 [0001fc0000 - 0001fde000]         BOOTMEM
[    0.000000]   #45 [0001d17ec0 - 0001d17ec8]         BOOTMEM
[    0.000000]   #46 [0001d17f00 - 0001d17f08]         BOOTMEM
[    0.000000]   #47 [0001d17f40 - 0001d17f60]         BOOTMEM
[    0.000000]   #48 [0001d17f80 - 0001d17fc0]         BOOTMEM
[    0.000000]   #49 [0001d36100 - 0001d36220]         BOOTMEM
[    0.000000]   #50 [0001d36240 - 0001d36288]         BOOTMEM
[    0.000000]   #51 [0001d362c0 - 0001d36308]         BOOTMEM
[    0.000000]   #52 [0001d38000 - 0001d40000]         BOOTMEM
[    0.000000]   #53 [0001d36340 - 0001d36680]         BOOTMEM
[    0.000000] Memory: 3332548k/3405440k available (5708k kernel code, 472k absent, 72420k reserved, 5382k data, 908k init)
[    0.000000] SLUB: Genslabs=14, HWalign=64, Order=0-3, MinObjects=0, CPUs=8, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000]     RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000]     RCU-based detection of stalled CPUs is disabled.
[    0.000000]     Verbose stalled-CPUs detection is disabled.
[    0.000000] NR_IRQS:4352 nr_irqs:744
[    0.000000] spurious 8259A interrupt: IRQ7.
[    0.000000] Console: colour VGA+ 80x25
[    0.000000] console [tty0] enabled
[    0.000000] allocated 34078720 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] hpet clockevent registered
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 3422.901 MHz processor.
[    0.010005] Calibrating delay loop (skipped), value calculated using timer frequency.. 6241.74 BogoMIPS (lpj=31208700)
[    0.010009] pid_max: default: 32768 minimum: 301
[    0.010023] Security Framework initialized
[    0.010035] AppArmor: AppArmor initialized
[    0.010036] Yama: becoming mindful.
[    0.010421] Dentry cache hash table entries: 524288 (order: 10, 4194304 bytes)
[    0.011417] Inode-cache hash table entries: 262144 (order: 9, 2097152 bytes)
[    0.011823] Mount-cache hash table entries: 256
[    0.011906] Initializing cgroup subsys ns
[    0.011908] Initializing cgroup subsys cpuacct
[    0.011911] Initializing cgroup subsys memory
[    0.011917] Initializing cgroup subsys devices
[    0.011918] Initializing cgroup subsys freezer
[    0.011920] Initializing cgroup subsys net_cls
[    0.011936] CPU: Physical Processor ID: 0
[    0.011937] CPU: Processor Core ID: 0
[    0.011939] mce: CPU supports 7 MCE banks
[    0.011947] Performance Events: AMD PMU driver.
[    0.011950] ... version:                0
[    0.011951] ... bit width:              48
[    0.011951] ... generic registers:      4
[    0.011952] ... value mask:             0000ffffffffffff
[    0.011954] ... max period:             00007fffffffffff
[    0.011955] ... fixed-purpose events:   0
[    0.011956] ... event mask:             000000000000000f
[    0.013194] ACPI: Core revision 20100428
[    0.030011] ftrace: converting mcount calls to 0f 1f 44 00 00
[    0.030016] ftrace: allocating 22680 entries in 89 pages
[    0.040043] Setting APIC routing to flat
[    0.040277] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.143901] CPU0: AMD FX(tm)-8120 Eight-Core Processor            stepping 02
[    0.150000] Booting Node   0, Processors  #1 #2 #3 #4 #5 #6 #7 Ok.
[    1.330004] Brought up 8 CPUs
[    1.330006] Total of 8 processors activated (49933.89 BogoMIPS).
[    1.336095] devtmpfs: initialized
[    1.336095] regulator: core version 0.5
[    1.336095] Time:  1:11:51  Date: 02/24/12
[    1.336095] NET: Registered protocol family 16
[    1.336095] Trying to unpack rootfs image as initramfs...
[    1.336095] ACPI: bus type pci registered
[    1.336095] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xe0000000-0xefffffff] (base 0xe0000000)
[    1.336095] PCI: MMCONFIG at [mem 0xe0000000-0xefffffff] reserved in E820
[    1.356029] PCI: Using configuration type 1 for base access
[    1.356475] bio: create slab <bio-0> at 0
[    1.356599] ACPI: EC: Look up EC in DSDT
[    1.367096] ACPI: Interpreter enabled
[    1.367099] ACPI: (supports S0 S3 S4 S5)
[    1.367116] ACPI: Using IOAPIC for interrupt routing
[    1.373684] ACPI Warning: Incorrect checksum in table [TAMG] - 0x45, should be 0x44 (20100428/tbutils-314)
[    1.373768] ACPI: No dock devices found.
[    1.373770] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[    1.373855] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
[    1.374020] pci_root PNP0A03:00: host bridge window [io  0x0000-0x0cf7]
[    1.374022] pci_root PNP0A03:00: host bridge window [io  0x0d00-0xffff]
[    1.374024] pci_root PNP0A03:00: host bridge window [mem 0x000a0000-0x000bffff]
[    1.374025] pci_root PNP0A03:00: host bridge window [mem 0x000c0000-0x000dffff]
[    1.374027] pci_root PNP0A03:00: host bridge window [mem 0xfed40000-0xfed44fff]
[    1.374028] pci_root PNP0A03:00: host bridge window [mem 0xd0000000-0xfebfffff]
[    1.374046] pci 0000:00:00.0: reg 1c: [mem 0xe0000000-0xffffffff 64bit]
[    1.374100] pci 0000:00:02.0: PME# supported from D0 D3hot D3cold
[    1.374102] pci 0000:00:02.0: PME# disabled
[    1.374130] pci 0000:00:04.0: PME# supported from D0 D3hot D3cold
[    1.374132] pci 0000:00:04.0: PME# disabled
[    1.374162] pci 0000:00:09.0: PME# supported from D0 D3hot D3cold
[    1.374164] pci 0000:00:09.0: PME# disabled
[    1.374194] pci 0000:00:0a.0: PME# supported from D0 D3hot D3cold
[    1.374196] pci 0000:00:0a.0: PME# disabled
[    1.374224] pci 0000:00:11.0: reg 10: [io  0xff00-0xff07]
[    1.374229] pci 0000:00:11.0: reg 14: [io  0xfe00-0xfe03]
[    1.374233] pci 0000:00:11.0: reg 18: [io  0xfd00-0xfd07]
[    1.374237] pci 0000:00:11.0: reg 1c: [io  0xfc00-0xfc03]
[    1.374242] pci 0000:00:11.0: reg 20: [io  0xfb00-0xfb0f]
[    1.374246] pci 0000:00:11.0: reg 24: [mem 0xfdfff000-0xfdfff3ff]
[    1.374281] pci 0000:00:12.0: reg 10: [mem 0xfdffe000-0xfdffefff]
[    1.374326] pci 0000:00:12.2: reg 10: [mem 0xfdffd000-0xfdffd0ff]
[    1.374359] pci 0000:00:12.2: supports D1 D2
[    1.374361] pci 0000:00:12.2: PME# supported from D0 D1 D2 D3hot
[    1.374364] pci 0000:00:12.2: PME# disabled
[    1.374384] pci 0000:00:13.0: reg 10: [mem 0xfdffc000-0xfdffcfff]
[    1.374427] pci 0000:00:13.2: reg 10: [mem 0xfdffb000-0xfdffb0ff]
[    1.374460] pci 0000:00:13.2: supports D1 D2
[    1.374462] pci 0000:00:13.2: PME# supported from D0 D1 D2 D3hot
[    1.374464] pci 0000:00:13.2: PME# disabled
[    1.374525] pci 0000:00:14.2: reg 10: [mem 0xfdff4000-0xfdff7fff 64bit]
[    1.374553] pci 0000:00:14.2: PME# supported from D0 D3hot D3cold
[    1.374555] pci 0000:00:14.2: PME# disabled
[    1.374622] pci 0000:00:14.5: reg 10: [mem 0xfdffa000-0xfdffafff]
[    1.374690] pci 0000:00:15.0: supports D1 D2
[    1.374709] pci 0000:00:16.0: reg 10: [mem 0xfdff9000-0xfdff9fff]
[    1.374753] pci 0000:00:16.2: reg 10: [mem 0xfdff8000-0xfdff80ff]
[    1.374786] pci 0000:00:16.2: supports D1 D2
[    1.374787] pci 0000:00:16.2: PME# supported from D0 D1 D2 D3hot
[    1.374790] pci 0000:00:16.2: PME# disabled
[    1.374908] pci 0000:01:00.0: reg 10: [mem 0xf8000000-0xf9ffffff]
[    1.374914] pci 0000:01:00.0: reg 14: [mem 0xd0000000-0xd7ffffff 64bit pref]
[    1.374920] pci 0000:01:00.0: reg 1c: [mem 0xdc000000-0xdfffffff 64bit pref]
[    1.374924] pci 0000:01:00.0: reg 24: [io  0xbf00-0xbf7f]
[    1.374928] pci 0000:01:00.0: reg 30: [mem 0x00000000-0x0007ffff pref]
[    1.374967] pci 0000:01:00.1: reg 10: [mem 0xfbffc000-0xfbffffff]
[    1.390013] pci 0000:00:02.0: PCI bridge to [bus 01-01]
[    1.390016] pci 0000:00:02.0:   bridge window [io  0xb000-0xbfff]
[    1.390018] pci 0000:00:02.0:   bridge window [mem 0xf8000000-0xfbffffff]
[    1.390021] pci 0000:00:02.0:   bridge window [mem 0xd0000000-0xdfffffff 64bit pref]
[    1.390060] pci 0000:02:00.0: reg 10: [mem 0xfd9f8000-0xfd9fffff 64bit]
[    1.390100] pci 0000:02:00.0: supports D1 D2
[    1.390102] pci 0000:02:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    1.390104] pci 0000:02:00.0: PME# disabled
[    1.410011] pci 0000:00:04.0: PCI bridge to [bus 02-02]
[    1.410014] pci 0000:00:04.0:   bridge window [io  0xe000-0xefff]
[    1.410016] pci 0000:00:04.0:   bridge window [mem 0xfd900000-0xfd9fffff]
[    1.410019] pci 0000:00:04.0:   bridge window [mem 0xfd600000-0xfd6fffff 64bit pref]
[    1.410056] pci 0000:03:00.0: reg 10: [io  0xde00-0xdeff]
[    1.410068] pci 0000:03:00.0: reg 18: [mem 0xfdeff000-0xfdefffff 64bit pref]
[    1.410078] pci 0000:03:00.0: reg 20: [mem 0xfdef8000-0xfdefbfff 64bit pref]
[    1.410107] pci 0000:03:00.0: supports D1 D2
[    1.410108] pci 0000:03:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    1.410111] pci 0000:03:00.0: PME# disabled
[    1.430010] pci 0000:00:09.0: PCI bridge to [bus 03-03]
[    1.430013] pci 0000:00:09.0:   bridge window [io  0xd000-0xdfff]
[    1.430015] pci 0000:00:09.0:   bridge window [mem 0xfd500000-0xfd5fffff]
[    1.430018] pci 0000:00:09.0:   bridge window [mem 0xfde00000-0xfdefffff 64bit pref]
[    1.430057] pci 0000:04:00.0: reg 10: [mem 0xfddf8000-0xfddfffff 64bit]
[    1.430095] pci 0000:04:00.0: supports D1 D2
[    1.430096] pci 0000:04:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    1.430099] pci 0000:04:00.0: PME# disabled
[    1.450010] pci 0000:00:0a.0: PCI bridge to [bus 04-04]
[    1.450013] pci 0000:00:0a.0:   bridge window [io  0xc000-0xcfff]
[    1.450015] pci 0000:00:0a.0:   bridge window [mem 0xfdd00000-0xfddfffff]
[    1.450019] pci 0000:00:0a.0:   bridge window [mem 0xfdc00000-0xfdcfffff 64bit pref]
[    1.450065] pci 0000:00:14.4: PCI bridge to [bus 05-05] (subtractive decode)
[    1.450068] pci 0000:00:14.4:   bridge window [io  0xa000-0xafff]
[    1.450071] pci 0000:00:14.4:   bridge window [mem 0xfdb00000-0xfdbfffff]
[    1.450075] pci 0000:00:14.4:   bridge window [mem 0xfda00000-0xfdafffff pref]
[    1.450077] pci 0000:00:14.4:   bridge window [io  0x0000-0x0cf7] (subtractive decode)
[    1.450079] pci 0000:00:14.4:   bridge window [io  0x0d00-0xffff] (subtractive decode)
[    1.450081] pci 0000:00:14.4:   bridge window [mem 0x000a0000-0x000bffff] (subtractive decode)
[    1.450082] pci 0000:00:14.4:   bridge window [mem 0x000c0000-0x000dffff] (subtractive decode)
[    1.450084] pci 0000:00:14.4:   bridge window [mem 0xfed40000-0xfed44fff] (subtractive decode)
[    1.450086] pci 0000:00:14.4:   bridge window [mem 0xd0000000-0xfebfffff] (subtractive decode)
[    1.450119] pci 0000:00:15.0: PCI bridge to [bus 06-06]
[    1.450123] pci 0000:00:15.0:   bridge window [io  0x9000-0x9fff]
[    1.450125] pci 0000:00:15.0:   bridge window [mem 0xfd800000-0xfd8fffff]
[    1.450129] pci 0000:00:15.0:   bridge window [mem 0xfd700000-0xfd7fffff 64bit pref]
[    1.450148] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    1.450368] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX0._PRT]
[    1.450420] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P2P_._PRT]
[    1.450479] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCE2._PRT]
[    1.450520] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCE4._PRT]
[    1.450564] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCE9._PRT]
[    1.450601] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCEA._PRT]
[    1.468719] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 10 11) *0
[    1.468795] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 10 11) *0
[    1.468870] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 10 11) *0
[    1.468943] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 10 11) *0
[    1.469016] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 10 11) *0
[    1.469088] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 10 11) *0
[    1.470052] ACPI: PCI Interrupt Link [LNK0] (IRQs 3 4 5 6 7 10 11) *0
[    1.470126] ACPI: PCI Interrupt Link [LNK1] (IRQs 3 4 5 6 7 10 11) *0
[    1.470155] HEST: Table is not found!
[    1.470205] vgaarb: device added: PCI:0000:01:00.0,decodes=io+mem,owns=io+mem,locks=none
[    1.470208] vgaarb: loaded
[    1.470293] SCSI subsystem initialized
[    1.470304] libata version 3.00 loaded.
[    1.470304] usbcore: registered new interface driver usbfs
[    1.470304] usbcore: registered new interface driver hub
[    1.470304] usbcore: registered new device driver usb
[    1.470304] ACPI: WMI: Mapper loaded
[    1.470304] PCI: Using ACPI for IRQ routing
[    1.470304] PCI: pci_cache_line_size set to 64 bytes
[    1.470304] pci 0000:00:00.0: no compatible bridge window for [mem 0xe0000000-0xffffffff 64bit]
[    1.470304] reserve RAM buffer: 000000000009a000 - 000000000009ffff 
[    1.470304] reserve RAM buffer: 00000000cfda0000 - 00000000cfffffff 
[    1.470304] NetLabel: Initializing
[    1.470304] NetLabel:  domain hash size = 128
[    1.470304] NetLabel:  protocols = UNLABELED CIPSOv4
[    1.470304] NetLabel:  unlabeled traffic allowed by default
[    1.470304] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[    1.470304] hpet0: 3 comparators, 32-bit 14.318180 MHz counter
[    1.472084] Switching to clocksource tsc
[    1.477450] AppArmor: AppArmor Filesystem Enabled
[    1.477456] pnp: PnP ACPI init
[    1.477462] ACPI: bus type pnp registered
[    1.477998] pnp 00:02: disabling [mem 0x00000000-0x00000fff window] because it overlaps 0000:00:00.0 BAR 3 [mem 0x00000000-0x1fffffff 64bit]
[    1.478021] pnp 00:02: disabling [mem 0x00000000-0x00000fff window disabled] because it overlaps 0000:01:00.0 BAR 6 [mem 0x00000000-0x0007ffff pref]
[    1.478551] pnp 00:0b: disabling [mem 0x000d4200-0x000d7fff] because it overlaps 0000:00:00.0 BAR 3 [mem 0x00000000-0x1fffffff 64bit]
[    1.478551] pnp 00:0b: disabling [mem 0x000f0000-0x000f7fff] because it overlaps 0000:00:00.0 BAR 3 [mem 0x00000000-0x1fffffff 64bit]
[    1.478551] pnp 00:0b: disabling [mem 0x000f8000-0x000fbfff] because it overlaps 0000:00:00.0 BAR 3 [mem 0x00000000-0x1fffffff 64bit]
[    1.478551] pnp 00:0b: disabling [mem 0x000fc000-0x000fffff] because it overlaps 0000:00:00.0 BAR 3 [mem 0x00000000-0x1fffffff 64bit]
[    1.478551] pnp 00:0b: disabling [mem 0x00000000-0x0009ffff] because it overlaps 0000:00:00.0 BAR 3 [mem 0x00000000-0x1fffffff 64bit]
[    1.478551] pnp 00:0b: disabling [mem 0x00100000-0xcfd9ffff] because it overlaps 0000:00:00.0 BAR 3 [mem 0x00000000-0x1fffffff 64bit]
[    1.478551] pnp: PnP ACPI: found 12 devices
[    1.478551] ACPI: ACPI bus type pnp unregistered
[    1.478551] system 00:01: [io  0x04d0-0x04d1] has been reserved
[    1.478551] system 00:01: [io  0x0220-0x0225] has been reserved
[    1.478551] system 00:01: [io  0x0290-0x0294] has been reserved
[    1.478551] system 00:02: [io  0x0900-0x091f] has been reserved
[    1.478551] system 00:02: [io  0x0228-0x022f] has been reserved
[    1.478551] system 00:02: [io  0x040b] has been reserved
[    1.478551] system 00:02: [io  0x04d6] has been reserved
[    1.478551] system 00:02: [io  0x0c00-0x0c01] has been reserved
[    1.478551] system 00:02: [io  0x0c14] has been reserved
[    1.478551] system 00:02: [io  0x0c50-0x0c52] has been reserved
[    1.478551] system 00:02: [io  0x0c6c-0x0c6d] has been reserved
[    1.478551] system 00:02: [io  0x0c6f] has been reserved
[    1.478551] system 00:02: [io  0x0cd0-0x0cd1] has been reserved
[    1.478551] system 00:02: [io  0x0cd2-0x0cd3] has been reserved
[    1.478551] system 00:02: [io  0x0cd4-0x0cdf] has been reserved
[    1.478551] system 00:02: [io  0x0800-0x08fe] has been reserved
[    1.478551] system 00:02: [io  0x0a10-0x0a17] has been reserved
[    1.478551] system 00:02: [io  0x0b00-0x0b0f] has been reserved
[    1.478551] system 00:02: [io  0x0b10-0x0b1f] has been reserved
[    1.478551] system 00:02: [io  0x0b20-0x0b3f] has been reserved
[    1.478551] system 00:02: [mem 0xfee00400-0xfee00fff window] has been reserved
[    1.478551] system 00:0a: [mem 0xe0000000-0xefffffff] has been reserved
[    1.478551] system 00:0b: [mem 0xcfda0000-0xcfdfffff] could not be reserved
[    1.478551] system 00:0b: [mem 0xffff0000-0xffffffff] has been reserved
[    1.478551] system 00:0b: [mem 0xcfe00000-0xcfefffff] has been reserved
[    1.478551] system 00:0b: [mem 0xcff00000-0xcfffffff] could not be reserved
[    1.478551] system 00:0b: [mem 0xfec00000-0xfec00fff] could not be reserved
[    1.478551] system 00:0b: [mem 0xfee00000-0xfee00fff] could not be reserved
[    1.478551] system 00:0b: [mem 0xfff80000-0xfffeffff] has been reserved
[    1.483141] pci 0000:01:00.0: BAR 6: assigned [mem 0xd8000000-0xd807ffff pref]
[    1.483144] pci 0000:00:02.0: PCI bridge to [bus 01-01]
[    1.483145] pci 0000:00:02.0:   bridge window [io  0xb000-0xbfff]
[    1.483148] pci 0000:00:02.0:   bridge window [mem 0xf8000000-0xfbffffff]
[    1.483150] pci 0000:00:02.0:   bridge window [mem 0xd0000000-0xdfffffff 64bit pref]
[    1.483153] pci 0000:00:04.0: PCI bridge to [bus 02-02]
[    1.483154] pci 0000:00:04.0:   bridge window [io  0xe000-0xefff]
[    1.483156] pci 0000:00:04.0:   bridge window [mem 0xfd900000-0xfd9fffff]
[    1.483158] pci 0000:00:04.0:   bridge window [mem 0xfd600000-0xfd6fffff 64bit pref]
[    1.483161] pci 0000:00:09.0: PCI bridge to [bus 03-03]
[    1.483163] pci 0000:00:09.0:   bridge window [io  0xd000-0xdfff]
[    1.483165] pci 0000:00:09.0:   bridge window [mem 0xfd500000-0xfd5fffff]
[    1.483167] pci 0000:00:09.0:   bridge window [mem 0xfde00000-0xfdefffff 64bit pref]
[    1.483170] pci 0000:00:0a.0: PCI bridge to [bus 04-04]
[    1.483171] pci 0000:00:0a.0:   bridge window [io  0xc000-0xcfff]
[    1.483173] pci 0000:00:0a.0:   bridge window [mem 0xfdd00000-0xfddfffff]
[    1.483176] pci 0000:00:0a.0:   bridge window [mem 0xfdc00000-0xfdcfffff 64bit pref]
[    1.483178] pci 0000:00:14.4: PCI bridge to [bus 05-05]
[    1.483180] pci 0000:00:14.4:   bridge window [io  0xa000-0xafff]
[    1.483184] pci 0000:00:14.4:   bridge window [mem 0xfdb00000-0xfdbfffff]
[    1.483187] pci 0000:00:14.4:   bridge window [mem 0xfda00000-0xfdafffff pref]
[    1.483191] pci 0000:00:15.0: PCI bridge to [bus 06-06]
[    1.483193] pci 0000:00:15.0:   bridge window [io  0x9000-0x9fff]
[    1.483196] pci 0000:00:15.0:   bridge window [mem 0xfd800000-0xfd8fffff]
[    1.483199] pci 0000:00:15.0:   bridge window [mem 0xfd700000-0xfd7fffff 64bit pref]
[    1.483206]   alloc irq_desc for 18 on node -1
[    1.483208]   alloc kstat_irqs on node -1
[    1.483211] pci 0000:00:02.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    1.483214] pci 0000:00:02.0: setting latency timer to 64
[    1.483218]   alloc irq_desc for 16 on node -1
[    1.483219]   alloc kstat_irqs on node -1
[    1.483221] pci 0000:00:04.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.483223] pci 0000:00:04.0: setting latency timer to 64
[    1.483227]   alloc irq_desc for 17 on node -1
[    1.483228]   alloc kstat_irqs on node -1
[    1.483230] pci 0000:00:09.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    1.483232] pci 0000:00:09.0: setting latency timer to 64
[    1.483235] pci 0000:00:0a.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    1.483237] pci 0000:00:0a.0: setting latency timer to 64
[    1.483245] pci 0000:00:15.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    1.483247] pci 0000:00:15.0: setting latency timer to 64
[    1.483250] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
[    1.483251] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
[    1.483253] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
[    1.483254] pci_bus 0000:00: resource 7 [mem 0x000c0000-0x000dffff]
[    1.483255] pci_bus 0000:00: resource 8 [mem 0xfed40000-0xfed44fff]
[    1.483257] pci_bus 0000:00: resource 9 [mem 0xd0000000-0xfebfffff]
[    1.483258] pci_bus 0000:01: resource 0 [io  0xb000-0xbfff]
[    1.483259] pci_bus 0000:01: resource 1 [mem 0xf8000000-0xfbffffff]
[    1.483261] pci_bus 0000:01: resource 2 [mem 0xd0000000-0xdfffffff 64bit pref]
[    1.483262] pci_bus 0000:02: resource 0 [io  0xe000-0xefff]
[    1.483263] pci_bus 0000:02: resource 1 [mem 0xfd900000-0xfd9fffff]
[    1.483265] pci_bus 0000:02: resource 2 [mem 0xfd600000-0xfd6fffff 64bit pref]
[    1.483266] pci_bus 0000:03: resource 0 [io  0xd000-0xdfff]
[    1.483268] pci_bus 0000:03: resource 1 [mem 0xfd500000-0xfd5fffff]
[    1.483269] pci_bus 0000:03: resource 2 [mem 0xfde00000-0xfdefffff 64bit pref]
[    1.483270] pci_bus 0000:04: resource 0 [io  0xc000-0xcfff]
[    1.483272] pci_bus 0000:04: resource 1 [mem 0xfdd00000-0xfddfffff]
[    1.483273] pci_bus 0000:04: resource 2 [mem 0xfdc00000-0xfdcfffff 64bit pref]
[    1.483275] pci_bus 0000:05: resource 0 [io  0xa000-0xafff]
[    1.483276] pci_bus 0000:05: resource 1 [mem 0xfdb00000-0xfdbfffff]
[    1.483277] pci_bus 0000:05: resource 2 [mem 0xfda00000-0xfdafffff pref]
[    1.483279] pci_bus 0000:05: resource 4 [io  0x0000-0x0cf7]
[    1.483280] pci_bus 0000:05: resource 5 [io  0x0d00-0xffff]
[    1.483281] pci_bus 0000:05: resource 6 [mem 0x000a0000-0x000bffff]
[    1.483282] pci_bus 0000:05: resource 7 [mem 0x000c0000-0x000dffff]
[    1.483284] pci_bus 0000:05: resource 8 [mem 0xfed40000-0xfed44fff]
[    1.483285] pci_bus 0000:05: resource 9 [mem 0xd0000000-0xfebfffff]
[    1.483286] pci_bus 0000:06: resource 0 [io  0x9000-0x9fff]
[    1.483288] pci_bus 0000:06: resource 1 [mem 0xfd800000-0xfd8fffff]
[    1.483289] pci_bus 0000:06: resource 2 [mem 0xfd700000-0xfd7fffff 64bit pref]
[    1.483308] NET: Registered protocol family 2
[    1.483437] IP route cache hash table entries: 131072 (order: 8, 1048576 bytes)
[    1.484434] TCP established hash table entries: 524288 (order: 11, 8388608 bytes)
[    1.486098] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    1.486285] TCP: Hash tables configured (established 524288 bind 65536)
[    1.486287] TCP reno registered
[    1.486296] UDP hash table entries: 2048 (order: 4, 65536 bytes)
[    1.486316] UDP-Lite hash table entries: 2048 (order: 4, 65536 bytes)
[    1.486390] NET: Registered protocol family 1
[    1.525194] Freeing initrd memory: 10748k freed
[    1.570078] pci 0000:01:00.0: Boot video device
[    1.570115] PCI: CLS 64 bytes, default 64
[    1.570498] Scanning for low memory corruption every 60 seconds
[    1.570579] audit: initializing netlink socket (disabled)
[    1.570585] type=2000 audit(1330045911.570:1): initialized
[    1.579655] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    1.580787] VFS: Disk quotas dquot_6.5.2
[    1.580822] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    1.581263] fuse init (API version 7.14)
[    1.581317] msgmni has been set to 6529
[    1.583139] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    1.583142] io scheduler noop registered
[    1.583143] io scheduler deadline registered
[    1.583170] io scheduler cfq registered (default)
[    1.583239] pcieport 0000:00:02.0: setting latency timer to 64
[    1.583255]   alloc irq_desc for 40 on node -1
[    1.583257]   alloc kstat_irqs on node -1
[    1.583263] pcieport 0000:00:02.0: irq 40 for MSI/MSI-X
[    1.583292] pcieport 0000:00:04.0: setting latency timer to 64
[    1.583306]   alloc irq_desc for 41 on node -1
[    1.583307]   alloc kstat_irqs on node -1
[    1.583311] pcieport 0000:00:04.0: irq 41 for MSI/MSI-X
[    1.583338] pcieport 0000:00:09.0: setting latency timer to 64
[    1.583352]   alloc irq_desc for 42 on node -1
[    1.583354]   alloc kstat_irqs on node -1
[    1.583357] pcieport 0000:00:09.0: irq 42 for MSI/MSI-X
[    1.583382] pcieport 0000:00:0a.0: setting latency timer to 64
[    1.583396]   alloc irq_desc for 43 on node -1
[    1.583397]   alloc kstat_irqs on node -1
[    1.583401] pcieport 0000:00:0a.0: irq 43 for MSI/MSI-X
[    1.583429] pcieport 0000:00:15.0: setting latency timer to 64
[    1.583453]   alloc irq_desc for 44 on node -1
[    1.583454]   alloc kstat_irqs on node -1
[    1.583459] pcieport 0000:00:15.0: irq 44 for MSI/MSI-X
[    1.583516] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    1.583552] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    1.583652] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0
[    1.583656] ACPI: Power Button [PWRB]
[    1.583686] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
[    1.583688] ACPI: Power Button [PWRF]
[    1.583906] ACPI: acpi_idle registered with cpuidle
[    1.585633] ERST: Table is not found!
[    1.585740] Linux agpgart interface v0.103
[    1.585754] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    1.585832] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.586034] 00:08: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.586670] brd: module loaded
[    1.586960] loop: module loaded
[    1.587224] Fixed MDIO Bus: probed
[    1.587244] PPP generic driver version 2.4.2
[    1.587263] tun: Universal TUN/TAP device driver, 1.6
[    1.587264] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    1.587304] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    1.587316] ehci_hcd 0000:00:12.2: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    1.587323] ehci_hcd 0000:00:12.2: EHCI Host Controller
[    1.587346] ehci_hcd 0000:00:12.2: new USB bus registered, assigned bus number 1
[    1.587365] ehci_hcd 0000:00:12.2: debug port 1
[    1.587379] ehci_hcd 0000:00:12.2: irq 17, io mem 0xfdffd000
[    1.610658] ehci_hcd 0000:00:12.2: USB 2.0 started, EHCI 1.00
[    1.610735] hub 1-0:1.0: USB hub found
[    1.610738] hub 1-0:1.0: 5 ports detected
[    1.610784] ehci_hcd 0000:00:13.2: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    1.610792] ehci_hcd 0000:00:13.2: EHCI Host Controller
[    1.610811] ehci_hcd 0000:00:13.2: new USB bus registered, assigned bus number 2
[    1.610828] ehci_hcd 0000:00:13.2: debug port 1
[    1.610836] ehci_hcd 0000:00:13.2: irq 17, io mem 0xfdffb000
[    1.630653] ehci_hcd 0000:00:13.2: USB 2.0 started, EHCI 1.00
[    1.630722] hub 2-0:1.0: USB hub found
[    1.630725] hub 2-0:1.0: 5 ports detected
[    1.630770] ehci_hcd 0000:00:16.2: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    1.630779] ehci_hcd 0000:00:16.2: EHCI Host Controller
[    1.630798] ehci_hcd 0000:00:16.2: new USB bus registered, assigned bus number 3
[    1.630815] ehci_hcd 0000:00:16.2: debug port 1
[    1.630823] ehci_hcd 0000:00:16.2: irq 17, io mem 0xfdff8000
[    1.650653] ehci_hcd 0000:00:16.2: USB 2.0 started, EHCI 1.00
[    1.650720] hub 3-0:1.0: USB hub found
[    1.650723] hub 3-0:1.0: 4 ports detected
[    1.650766] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    1.650774] ohci_hcd 0000:00:12.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    1.650782] ohci_hcd 0000:00:12.0: OHCI Host Controller
[    1.650802] ohci_hcd 0000:00:12.0: new USB bus registered, assigned bus number 4
[    1.650818] ohci_hcd 0000:00:12.0: irq 18, io mem 0xfdffe000
[    1.714394] hub 4-0:1.0: USB hub found
[    1.714399] hub 4-0:1.0: 5 ports detected
[    1.714443] ohci_hcd 0000:00:13.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    1.714451] ohci_hcd 0000:00:13.0: OHCI Host Controller
[    1.714470] ohci_hcd 0000:00:13.0: new USB bus registered, assigned bus number 5
[    1.714480] ohci_hcd 0000:00:13.0: irq 18, io mem 0xfdffc000
[    1.774370] hub 5-0:1.0: USB hub found
[    1.774375] hub 5-0:1.0: 5 ports detected
[    1.774422] ohci_hcd 0000:00:14.5: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    1.774432] ohci_hcd 0000:00:14.5: OHCI Host Controller
[    1.774451] ohci_hcd 0000:00:14.5: new USB bus registered, assigned bus number 6
[    1.774462] ohci_hcd 0000:00:14.5: irq 18, io mem 0xfdffa000
[    1.834371] hub 6-0:1.0: USB hub found
[    1.834375] hub 6-0:1.0: 2 ports detected
[    1.834415] ohci_hcd 0000:00:16.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    1.834424] ohci_hcd 0000:00:16.0: OHCI Host Controller
[    1.834442] ohci_hcd 0000:00:16.0: new USB bus registered, assigned bus number 7
[    1.834452] ohci_hcd 0000:00:16.0: irq 18, io mem 0xfdff9000
[    1.894372] hub 7-0:1.0: USB hub found
[    1.894376] hub 7-0:1.0: 4 ports detected
[    1.894418] uhci_hcd: USB Universal Host Controller Interface driver
[    1.894475] PNP: PS/2 Controller [PNP0303:PS2K] at 0x60,0x64 irq 1
[    1.894476] PNP: PS/2 appears to have AUX port disabled, if this is incorrect please boot with i8042.nopnp
[    1.894572] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.894611] mice: PS/2 mouse device common for all mice
[    1.894993] rtc_cmos 00:05: RTC can wake from S4
[    1.894993] rtc_cmos 00:05: rtc core: registered rtc_cmos as rtc0
[    1.894993] rtc0: alarms up to one month, 242 bytes nvram, hpet irqs
[    1.894993] device-mapper: uevent: version 1.0.3
[    1.895253] device-mapper: ioctl: 4.17.0-ioctl (2010-03-05) initialised: dm-devel@redhat.com
[    1.895426] device-mapper: multipath: version 1.1.1 loaded
[    1.895428] device-mapper: multipath round-robin: version 1.0.0 loaded
[    1.895853] cpuidle: using governor ladder
[    1.896022] cpuidle: using governor menu
[    1.896203] TCP cubic registered
[    1.896285] NET: Registered protocol family 10
[    1.896532] lo: Disabled Privacy Extensions
[    1.896666] NET: Registered protocol family 17
[    1.896710] powernow-k8: Found 1 AMD FX(tm)-8120 Eight-Core Processor            (8 cpu cores) (version 2.20.00)
[    1.896724] powernow-k8: Core Performance Boosting: on.
[    1.896776] powernow-k8:    0 : pstate 0 (3100 MHz)
[    1.896777] powernow-k8:    1 : pstate 1 (2800 MHz)
[    1.896779] powernow-k8:    2 : pstate 2 (2300 MHz)
[    1.896780] powernow-k8:    3 : pstate 3 (1900 MHz)
[    1.896781] powernow-k8:    4 : pstate 4 (1400 MHz)
[    1.897631] PM: Resume from disk failed.
[    1.897638] registered taskstats version 1
[    1.897824]   Magic number: 0:497:155
[    1.897830] bdi 1:7: hash matches
[    1.897841] acpi device:22: hash matches
[    1.897870] rtc_cmos 00:05: setting system clock to 2012-02-24 01:11:52 UTC (1330045912)
[    1.897872] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.897873] EDD information not available.
[    1.897928] Freeing unused kernel memory: 908k freed
[    1.898081] Write protecting the kernel read-only data: 10240k
[    1.898230] Freeing unused kernel memory: 416k freed
[    1.898401] Freeing unused kernel memory: 1644k freed
[    1.909996] udev[146]: starting version 163
[    1.917641] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input2
[    1.938243] ahci 0000:00:11.0: version 3.0
[    1.938243]   alloc irq_desc for 19 on node -1
[    1.938243]   alloc kstat_irqs on node -1
[    1.938243] ahci 0000:00:11.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    1.938278] ahci 0000:00:11.0: AHCI 0001.0200 32 slots 6 ports 6 Gbps 0x3f impl SATA mode
[    1.938281] ahci 0000:00:11.0: flags: 64bit ncq sntf ilck pm led clo pmp pio slum part 
[    1.939217] scsi0 : ahci
[    1.939377] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    1.939393] r8169 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    1.939420] r8169 0000:03:00.0: setting latency timer to 64
[    1.939425] r8169 0000:03:00.0: (unregistered net_device): unknown MAC, using family default
[    1.939551] scsi1 : ahci
[    1.939471]   alloc irq_desc for 45 on node -1
[    1.939472]   alloc kstat_irqs on node -1
[    1.939481] r8169 0000:03:00.0: irq 45 for MSI/MSI-X
[    1.939674] scsi2 : ahci
[    1.939995] scsi3 : ahci
[    1.940044] scsi4 : ahci
[    1.940096] scsi5 : ahci
[    1.940175] r8169 0000:03:00.0: eth0: RTL8168b/8111b at 0xffffc90000632000, 50:e5:49:c8:12:88, XID 0c900800 IRQ 45
[    1.940243] ata1: SATA max UDMA/133 abar m1024@0xfdfff000 port 0xfdfff100 irq 19
[    1.940246] ata2: SATA max UDMA/133 abar m1024@0xfdfff000 port 0xfdfff180 irq 19
[    1.940248] ata3: SATA max UDMA/133 abar m1024@0xfdfff000 port 0xfdfff200 irq 19
[    1.940251] ata4: SATA max UDMA/133 abar m1024@0xfdfff000 port 0xfdfff280 irq 19
[    1.940254] ata5: SATA max UDMA/133 abar m1024@0xfdfff000 port 0xfdfff300 irq 19
[    1.940256] ata6: SATA max UDMA/133 abar m1024@0xfdfff000 port 0xfdfff380 irq 19
[    2.150185] usb 5-5: new low speed USB device using ohci_hcd and address 2
[    2.270198] ata6: SATA link down (SStatus 0 SControl 300)
[    2.270215] ata4: SATA link down (SStatus 0 SControl 300)
[    2.270234] ata3: SATA link down (SStatus 0 SControl 300)
[    2.270243] ata5: SATA link down (SStatus 0 SControl 300)
[    2.450720] ata2: SATA link up 6.0 Gbps (SStatus 133 SControl 300)
[    2.460173] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    2.462715] ata2.00: ATA-8: OCZ-AGILITY3, 2.15, max UDMA/133
[    2.462717] ata2.00: 234441648 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
[    2.463387] ata1.00: ATAPI: HL-DT-ST DVDRAM GH24LS70, GL01, max UDMA/100
[    2.467777] ata1.00: configured for UDMA/100
[    2.472687] ata2.00: configured for UDMA/133
[    2.493267] scsi 0:0:0:0: CD-ROM            HL-DT-ST DVDRAM GH24LS70  GL01 PQ: 0 ANSI: 5
[    2.514143] sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
[    2.514149] Uniform CD-ROM driver Revision: 3.20
[    2.514308] sr 0:0:0:0: Attached scsi CD-ROM sr0
[    2.514372] sr 0:0:0:0: Attached scsi generic sg0 type 5
[    2.514510] scsi 1:0:0:0: Direct-Access     ATA      OCZ-AGILITY3     2.15 PQ: 0 ANSI: 5
[    2.514587] sd 1:0:0:0: Attached scsi generic sg1 type 0
[    2.514616] sd 1:0:0:0: [sda] 234441648 512-byte logical blocks: (120 GB/111 GiB)
[    2.514787] sd 1:0:0:0: [sda] Write Protect is off
[    2.514789] sd 1:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    2.514814] sd 1:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.514942]  sda: sda1
[    2.515382] sd 1:0:0:0: [sda] Attached SCSI disk
[    2.518755] usbcore: registered new interface driver hiddev
[    2.522879] input: Cypress Sem PS2/USB Browser Combo Mouse as /devices/pci0000:00/0000:00:13.0/usb5/5-5/5-5:1.0/input/input3
[    2.522933] generic-usb 0003:05FE:0011.0001: input,hidraw0: USB HID v1.00 Mouse [Cypress Sem PS2/USB Browser Combo Mouse] on usb-0000:00:13.0-5/input0
[    2.522943] usbcore: registered new interface driver usbhid
[    2.522944] usbhid: USB HID core driver
[    2.537278] EXT4-fs (sda1): INFO: recovery required on readonly filesystem
[    2.537280] EXT4-fs (sda1): write access will be enabled during recovery
[    2.595286] EXT4-fs (sda1): recovery complete
[    2.595656] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)
[    2.742165] EXT4-fs (sda1): re-mounted. Opts: discard,errors=remount-ro
[    2.745293] udev[408]: starting version 163
[    2.753585] lp: driver loaded but no devices found
[    2.778785] xhci_hcd 0000:02:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    2.778805] xhci_hcd 0000:02:00.0: setting latency timer to 64
[    2.778808] xhci_hcd 0000:02:00.0: xHCI Host Controller
[    2.778891] xhci_hcd 0000:02:00.0: new USB bus registered, assigned bus number 8
[    2.778961] xhci_hcd 0000:02:00.0: irq 16, io mem 0xfd9f8000
[    2.778984] usb usb8: No SuperSpeed endpoint companion for config 1  interface 0 altsetting 0 ep 129: using minimum values
[    2.779079] xHCI xhci_add_endpoint called for root hub
[    2.779082] xHCI xhci_check_bandwidth called for root hub
[    2.779108] hub 8-0:1.0: USB hub found
[    2.779112] hub 8-0:1.0: 4 ports detected
[    2.779182] xhci_hcd 0000:04:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    2.779408] xhci_hcd 0000:04:00.0: setting latency timer to 64
[    2.779411] xhci_hcd 0000:04:00.0: xHCI Host Controller
[    2.779450] xhci_hcd 0000:04:00.0: new USB bus registered, assigned bus number 9
[    2.779510] xhci_hcd 0000:04:00.0: irq 18, io mem 0xfddf8000
[    2.779532] usb usb9: No SuperSpeed endpoint companion for config 1  interface 0 altsetting 0 ep 129: using minimum values
[    2.780084] xHCI xhci_add_endpoint called for root hub
[    2.780084] xHCI xhci_check_bandwidth called for root hub
[    2.780222] hub 9-0:1.0: USB hub found
[    2.780222] hub 9-0:1.0: 4 ports detected
[    2.783987] ACPI: resource piix4_smbus [io  0x0b00-0x0b07] conflicts with ACPI region SOR1 [io  0x0b00-0x0b0f 64bit]
[    2.783987] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[    2.794485] [drm] Initialized drm 1.1.0 20060810
[    2.823068] type=1400 audit(1330045913.419:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient3" pid=609 comm="apparmor_parser"
[    2.823389] type=1400 audit(1330045913.419:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=609 comm="apparmor_parser"
[    2.823560] type=1400 audit(1330045913.419:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=609 comm="apparmor_parser"
[    2.855013] nouveau 0000:01:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    2.855017] nouveau 0000:01:00.0: setting latency timer to 64
[    2.860861] [drm] nouveau 0000:01:00.0: Unsupported chipset 0x0cf200a1
[    2.861361] nouveau 0000:01:00.0: PCI INT A disabled
[    2.861367] nouveau: probe of 0000:01:00.0 failed with error -22
[    2.867310] type=1400 audit(1330045913.459:5): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=814 comm="apparmor_parser"
[    2.867367] type=1400 audit(1330045913.459:6): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient3" pid=811 comm="apparmor_parser"
[    2.867705] type=1400 audit(1330045913.459:7): apparmor="STATUS" operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" pid=810 comm="apparmor_parser"
[    2.867852] type=1400 audit(1330045913.459:8): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=811 comm="apparmor_parser"
[    2.867874] type=1400 audit(1330045913.459:9): apparmor="STATUS" operation="profile_load" name="/usr/sbin/cupsd" pid=814 comm="apparmor_parser"
[    2.868114] type=1400 audit(1330045913.459:10): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=811 comm="apparmor_parser"
[    2.890706] HDA Intel 0000:00:14.2: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    2.912262] r8169 0000:03:00.0: eth0: link down
[    2.912370] r8169 0000:03:00.0: eth0: link down
[    2.912596] ADDRCONF(NETDEV_UP): eth0: link is not ready
[    3.014628] HDA Intel 0000:01:00.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    3.014628] hda_intel: Disable MSI for Nvidia chipset
[    3.014628] HDA Intel 0000:01:00.1: setting latency timer to 64
[    3.313994] EXT4-fs (sda1): re-mounted. Opts: discard,errors=remount-ro,commit=0
[    4.827794] ppdev: user-space parallel port driver
[    5.673670] r8169 0000:03:00.0: eth0: link up
[    5.673933] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[    6.033507] EXT4-fs (sda1): re-mounted. Opts: discard,errors=remount-ro,commit=0
[   15.800705] eth0: no IPv6 routers present

```

This issue only appears on the later kernel.  If I boot the 10.04 LTS LiveCD, it reports the full 16GB.  

Can someone provide a guidance on a patch or something I can do to fix this?  I can revert back to 10.04 LTS but I will lose the SSD TRIM support since it doesn't support it.  I effectively need 10.04 LTS on a 2.6.33 kernel with the CPU MTRR issue not present.

My motherboard is on the latest stable BIOS release from Gigabyte (F4).  There is a beta F5 BIOS available but I'm not going to risk it just yet if I can get a patch, kernel parameters or a different kernel that supports my RAM and SSD TRIM at once.

I can provide additional trace outputs as desired.  uname -a reports x86_64 and dmidecode does see all four DIMM slots populated correctly.

Thanks for any help.

Matt

---

### Post by LinuxSailor on 2012-02-23
For reference, here is the dmesg output from the 10.04 LTS LiveCD with 16GB working:

```

[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.32-38-generic (buildd@allspice) (gcc version 4.4.3 (Ubuntu 4.4.3-4ubuntu5) ) #83-Ubuntu SMP Wed Jan 4 11:12:07 UTC 2012 (Ubuntu 2.6.32-38.83-generic 2.6.32.52+drm33.21)
[    0.000000] Command line: BOOT_IMAGE=/casper/vmlinuz file=/cdrom/preseed/ubuntu.seed boot=casper initrd=/casper/initrd.lz quiet splash -- maybe-ubiquity
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   Centaur CentaurHauls
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
[    0.000000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 00000000cfda0000 (usable)
[    0.000000]  BIOS-e820: 00000000cfda0000 - 00000000cfdd1000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000cfdd1000 - 00000000cfe00000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000cfe00000 - 00000000cff00000 (reserved)
[    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 0000000100000000 (reserved)
[    0.000000]  BIOS-e820: 0000000100000000 - 000000042f000000 (usable)
[    0.000000] DMI 2.4 present.
[    0.000000] last_pfn = 0x42f000 max_arch_pfn = 0x400000000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-C7FFF write-protect
[    0.000000]   C8000-FFFFF uncachable
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000000 mask FFFF80000000 write-back
[    0.000000]   1 base 000080000000 mask FFFFC0000000 write-back
[    0.000000]   2 base 0000C0000000 mask FFFFF0000000 write-back
[    0.000000]   3 base 0000CFE00000 mask FFFFFFE00000 uncachable
[    0.000000]   4 disabled
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] TOM2: 000000042f000000 aka 17136M
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] e820 update range: 00000000cfe00000 - 0000000100000000 (usable) ==> (reserved)
[    0.000000] last_pfn = 0xcfda0 max_arch_pfn = 0x400000000
[    0.000000] e820 update range: 0000000000001000 - 0000000000006000 (usable) ==> (reserved)
[    0.000000] Scanning 1 areas for low memory corruption
[    0.000000] modified physical RAM map:
[    0.000000]  modified: 0000000000000000 - 0000000000001000 (usable)
[    0.000000]  modified: 0000000000001000 - 0000000000006000 (reserved)
[    0.000000]  modified: 0000000000006000 - 000000000009f800 (usable)
[    0.000000]  modified: 000000000009f800 - 00000000000a0000 (reserved)
[    0.000000]  modified: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  modified: 0000000000100000 - 00000000cfda0000 (usable)
[    0.000000]  modified: 00000000cfda0000 - 00000000cfdd1000 (ACPI NVS)
[    0.000000]  modified: 00000000cfdd1000 - 00000000cfe00000 (ACPI data)
[    0.000000]  modified: 00000000cfe00000 - 00000000cff00000 (reserved)
[    0.000000]  modified: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  modified: 00000000fec00000 - 0000000100000000 (reserved)
[    0.000000]  modified: 0000000100000000 - 000000042f000000 (usable)
[    0.000000] initial memory mapped : 0 - 20000000
[    0.000000] Using GB pages for direct mapping
[    0.000000] init_memory_mapping: 0000000000000000-00000000cfda0000
[    0.000000] NX (Execute Disable) protection: active
[    0.000000]  0000000000 - 00c0000000 page 1G
[    0.000000]  00c0000000 - 00cfc00000 page 2M
[    0.000000]  00cfc00000 - 00cfda0000 page 4k
[    0.000000] kernel direct mapping tables up to cfda0000 @ 8000-b000
[    0.000000] init_memory_mapping: 0000000100000000-000000042f000000
[    0.000000] NX (Execute Disable) protection: active
[    0.000000]  0100000000 - 0400000000 page 1G
[    0.000000]  0400000000 - 042f000000 page 2M
[    0.000000] kernel direct mapping tables up to 42f000000 @ a000-c000
[    0.000000] RAMDISK: 7f691000 - 7ffff884
[    0.000000] ACPI: RSDP 00000000000f6a50 00014 (v00 GBT   )
[    0.000000] ACPI: RSDT 00000000cfdd1000 0004C (v01 GBT    GBTUACPI 42302E31 GBTU 01010101)
[    0.000000] ACPI: FACP 00000000cfdd1080 00074 (v01 GBT    GBTUACPI 42302E31 GBTU 01010101)
[    0.000000] ACPI: DSDT 00000000cfdd1100 0792A (v01 GBT    GBTUACPI 00001000 MSFT 03000000)
[    0.000000] ACPI: FACS 00000000cfda0000 00040
[    0.000000] ACPI: MSDM 00000000cfdd8b00 00055 (v03 GBT    GBTUACPI 42302E31 GBTU 01010101)
[    0.000000] ACPI: HPET 00000000cfdd8b80 00038 (v01 GBT    GBTUACPI 42302E31 GBTU 00000098)
[    0.000000] ACPI: MCFG 00000000cfdd8bc0 0003C (v01 GBT    GBTUACPI 42302E31 GBTU 01010101)
[    0.000000] ACPI: MATS 00000000cfdd8c40 00034 (v01 GBT             00000000      00000000)
[    0.000000] ACPI: TAMG 00000000cfdd8cb0 00202 (v01 GBT    GBT   B0 5455312E BG?? 53450101)
[    0.000000] ACPI: APIC 00000000cfdd8a40 000BC (v01 GBT    GBTUACPI 42302E31 GBTU 01010101)
[    0.000000] ACPI: MATS 00000000cfdd8ec0 061FD (v01        MATS RCM 80000001 INTL 20061109)
[    0.000000] ACPI: SSDT 00000000cfddf130 01714 (v01 AMD    POWERNOW 00000001 AMD  00000001)
[    0.000000] ACPI: IVRS 00000000cfde08c0 000E0 (v01  AMD     RD890S 00202031 AMD  00000000)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at 0000000000000000-000000042f000000
[    0.000000] Bootmem setup node 0 0000000000000000-000000042f000000
[    0.000000]   NODE_DATA [000000000000b000 - 000000000000ffff]
[    0.000000]   bootmap [0000000000010000 -  0000000000095dff] pages 86
[    0.000000] (8 early reservations) ==> bootmem [0000000000 - 042f000000]
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000]   #1 [0000006000 - 0000008000]       TRAMPOLINE ==> [0000006000 - 0000008000]
[    0.000000]   #2 [0001000000 - 0001a35ac4]    TEXT DATA BSS ==> [0001000000 - 0001a35ac4]
[    0.000000]   #3 [007f691000 - 007ffff884]          RAMDISK ==> [007f691000 - 007ffff884]
[    0.000000]   #4 [000009f800 - 0000100000]    BIOS reserved ==> [000009f800 - 0000100000]
[    0.000000]   #5 [0001a36000 - 0001a360f6]              BRK ==> [0001a36000 - 0001a360f6]
[    0.000000]   #6 [0000008000 - 000000a000]          PGTABLE ==> [0000008000 - 000000a000]
[    0.000000]   #7 [000000a000 - 000000b000]          PGTABLE ==> [000000a000 - 000000b000]
[    0.000000] found SMP MP-table at [ffff8800000f4b30] f4b30
[    0.000000]  [ffffea0000000000-ffffea000ebfffff] PMD -> [ffff880028600000-ffff8800367fffff] on node 0
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000000 -> 0x00001000
[    0.000000]   DMA32    0x00001000 -> 0x00100000
[    0.000000]   Normal   0x00100000 -> 0x0042f000
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[4] active PFN ranges
[    0.000000]     0: 0x00000000 -> 0x00000001
[    0.000000]     0: 0x00000006 -> 0x0000009f
[    0.000000]     0: 0x00000100 -> 0x000cfda0
[    0.000000]     0: 0x00100000 -> 0x0042f000
[    0.000000] On node 0 totalpages: 4189498
[    0.000000]   DMA zone: 56 pages used for memmap
[    0.000000]   DMA zone: 102 pages reserved
[    0.000000]   DMA zone: 3836 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 14280 pages used for memmap
[    0.000000]   DMA32 zone: 832984 pages, LIFO batch:31
[    0.000000]   Normal zone: 45640 pages used for memmap
[    0.000000]   Normal zone: 3292600 pages, LIFO batch:31
[    0.000000] ACPI: PM-Timer IO Port: 0x808
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x02] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x03] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x04] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x05] lapic_id[0x05] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x06] lapic_id[0x06] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x07] lapic_id[0x07] enabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] dfl dfl lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] dfl dfl lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x02] dfl dfl lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x03] dfl dfl lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x04] dfl dfl lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x05] dfl dfl lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x06] dfl dfl lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x07] dfl dfl lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x08] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 8, version 33, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 low level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x10b9a201 base: 0xfed00000
[    0.000000] SMP: Allowing 8 CPUs, 0 hotplug CPUs
[    0.000000] nr_irqs_gsi: 24
[    0.000000] PM: Registered nosave memory: 0000000000001000 - 0000000000006000
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000f0000
[    0.000000] PM: Registered nosave memory: 00000000000f0000 - 0000000000100000
[    0.000000] PM: Registered nosave memory: 00000000cfda0000 - 00000000cfdd1000
[    0.000000] PM: Registered nosave memory: 00000000cfdd1000 - 00000000cfe00000
[    0.000000] PM: Registered nosave memory: 00000000cfe00000 - 00000000cff00000
[    0.000000] PM: Registered nosave memory: 00000000cff00000 - 00000000e0000000
[    0.000000] PM: Registered nosave memory: 00000000e0000000 - 00000000f0000000
[    0.000000] PM: Registered nosave memory: 00000000f0000000 - 00000000fec00000
[    0.000000] PM: Registered nosave memory: 00000000fec00000 - 0000000100000000
[    0.000000] Allocating PCI resources starting at cff00000 (gap: cff00000:10100000)
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] NR_CPUS:64 nr_cpumask_bits:64 nr_cpu_ids:8 nr_node_ids:1
[    0.000000] PERCPU: Embedded 30 pages/cpu @ffff880028200000 s91608 r8192 d23080 u262144
[    0.000000] pcpu-alloc: s91608 r8192 d23080 u262144 alloc=1*2097152
[    0.000000] pcpu-alloc: [0] 0 1 2 3 4 5 6 7 
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 4129420
[    0.000000] Policy zone: Normal
[    0.000000] Kernel command line: BOOT_IMAGE=/casper/vmlinuz file=/cdrom/preseed/ubuntu.seed boot=casper initrd=/casper/initrd.lz quiet splash -- maybe-ubiquity
[    0.000000] PID hash table entries: 4096 (order: 3, 32768 bytes)
[    0.000000] Initializing CPU#0
[    0.000000] xsave/xrstor: enabled xstate_bv 0x7, cntxt size 0x340
[    0.000000] Checking aperture...
[    0.000000] No AGP bridge found
[    0.000000] Calgary: detecting Calgary via BIOS EBDA area
[    0.000000] Calgary: Unable to locate Rio Grande table in EBDA - bailing!
[    0.000000] Memory: 16505152k/17547264k available (5436k kernel code, 789272k absent, 252840k reserved, 2982k data, 884k init)
[    0.000000] SLUB: Genslabs=14, HWalign=64, Order=0-3, MinObjects=0, CPUs=8, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000] NR_IRQS:4352 nr_irqs:472
[    0.000000] Console: colour VGA+ 80x25
[    0.000000] console [tty0] enabled
[    0.000000] allocated 167772160 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] hpet clockevent registered
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 3422.841 MHz processor.
[    0.010004] Calibrating delay loop (skipped), value calculated using timer frequency.. 6241.63 BogoMIPS (lpj=31208150)
[    0.010017] Security Framework initialized
[    0.010028] AppArmor: AppArmor initialized
[    0.011023] Dentry cache hash table entries: 2097152 (order: 12, 16777216 bytes)
[    0.014638] Inode-cache hash table entries: 1048576 (order: 11, 8388608 bytes)
[    0.016161] Mount-cache hash table entries: 256
[    0.016242] Initializing cgroup subsys ns
[    0.016245] Initializing cgroup subsys cpuacct
[    0.016247] Initializing cgroup subsys memory
[    0.016252] Initializing cgroup subsys devices
[    0.016253] Initializing cgroup subsys freezer
[    0.016255] Initializing cgroup subsys net_cls
[    0.016267] CPU: L1 I Cache: 64K (64 bytes/line), D cache 16K (64 bytes/line)
[    0.016269] CPU: L2 Cache: 2048K (64 bytes/line)
[    0.016270] CPU 0/0x0 -> Node 0
[    0.016272] CPU: Physical Processor ID: 0
[    0.016273] CPU: Processor Core ID: 0
[    0.016275] mce: CPU supports 7 MCE banks
[    0.016283] Performance Events: AMD PMU driver.
[    0.016286] ... version:                0
[    0.016287] ... bit width:              48
[    0.016288] ... generic registers:      4
[    0.016289] ... value mask:             0000ffffffffffff
[    0.016290] ... max period:             00007fffffffffff
[    0.016291] ... fixed-purpose events:   0
[    0.016292] ... event mask:             000000000000000f
[    0.017474] ACPI: Core revision 20090903
[    0.030013] ftrace: converting mcount calls to 0f 1f 44 00 00
[    0.030019] ftrace: allocating 22567 entries in 89 pages
[    0.040046] Setting APIC routing to flat
[    0.040278] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.143902] CPU0: AMD FX(tm)-8120 Eight-Core Processor            stepping 02
[    0.150000] Booting processor 1 APIC 0x1 ip 0x6000
[    0.020000] Initializing CPU#1
[    0.020000] CPU: L1 I Cache: 64K (64 bytes/line), D cache 16K (64 bytes/line)
[    0.020000] CPU: L2 Cache: 2048K (64 bytes/line)
[    0.020000] CPU 1/0x1 -> Node 0
[    0.020000] CPU: Physical Processor ID: 0
[    0.020000] CPU: Processor Core ID: 1
[    0.300098] CPU1: AMD FX(tm)-8120 Eight-Core Processor            stepping 02
[    0.300104] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
[    0.310070] Booting processor 2 APIC 0x2 ip 0x6000
[    0.020000] Initializing CPU#2
[    0.020000] CPU: L1 I Cache: 64K (64 bytes/line), D cache 16K (64 bytes/line)
[    0.020000] CPU: L2 Cache: 2048K (64 bytes/line)
[    0.020000] CPU 2/0x2 -> Node 0
[    0.020000] CPU: Physical Processor ID: 0
[    0.020000] CPU: Processor Core ID: 5
[    0.470106] CPU2: AMD FX(tm)-8120 Eight-Core Processor            stepping 02
[    0.470111] checking TSC synchronization [CPU#0 -> CPU#2]: passed.
[    0.480044] Booting processor 3 APIC 0x3 ip 0x6000
[    0.020000] Initializing CPU#3
[    0.020000] CPU: L1 I Cache: 64K (64 bytes/line), D cache 16K (64 bytes/line)
[    0.020000] CPU: L2 Cache: 2048K (64 bytes/line)
[    0.020000] CPU 3/0x3 -> Node 0
[    0.020000] CPU: Physical Processor ID: 0
[    0.020000] CPU: Processor Core ID: 3
[    0.640088] CPU3: AMD FX(tm)-8120 Eight-Core Processor            stepping 02
[    0.640093] checking TSC synchronization [CPU#0 -> CPU#3]: passed.
[    0.650049] Booting processor 4 APIC 0x4 ip 0x6000
[    0.020000] Initializing CPU#4
[    0.020000] CPU: L1 I Cache: 64K (64 bytes/line), D cache 16K (64 bytes/line)
[    0.020000] CPU: L2 Cache: 2048K (64 bytes/line)
[    0.020000] CPU 4/0x4 -> Node 0
[    0.020000] CPU: Physical Processor ID: 0
[    0.020000] CPU: Processor Core ID: 2
[    0.810076] CPU4: AMD FX(tm)-8120 Eight-Core Processor            stepping 02
[    0.810080] checking TSC synchronization [CPU#0 -> CPU#4]: passed.
[    0.820049] Booting processor 5 APIC 0x5 ip 0x6000
[    0.020000] Initializing CPU#5
[    0.020000] CPU: L1 I Cache: 64K (64 bytes/line), D cache 16K (64 bytes/line)
[    0.020000] CPU: L2 Cache: 2048K (64 bytes/line)
[    0.020000] CPU 5/0x5 -> Node 0
[    0.020000] CPU: Physical Processor ID: 0
[    0.020000] CPU: Processor Core ID: 4
[    0.980062] CPU5: AMD FX(tm)-8120 Eight-Core Processor            stepping 02
[    0.980066] checking TSC synchronization [CPU#0 -> CPU#5]: passed.
[    0.990048] Booting processor 6 APIC 0x6 ip 0x6000
[    0.020000] Initializing CPU#6
[    0.020000] CPU: L1 I Cache: 64K (64 bytes/line), D cache 16K (64 bytes/line)
[    0.020000] CPU: L2 Cache: 2048K (64 bytes/line)
[    0.020000] CPU 6/0x6 -> Node 0
[    0.020000] CPU: Physical Processor ID: 0
[    0.020000] CPU: Processor Core ID: 7
[    1.150049] CPU6: AMD FX(tm)-8120 Eight-Core Processor            stepping 02
[    1.150053] checking TSC synchronization [CPU#0 -> CPU#6]: passed.
[    1.160053] Booting processor 7 APIC 0x7 ip 0x6000
[    0.020000] Initializing CPU#7
[    0.020000] CPU: L1 I Cache: 64K (64 bytes/line), D cache 16K (64 bytes/line)
[    0.020000] CPU: L2 Cache: 2048K (64 bytes/line)
[    0.020000] CPU 7/0x7 -> Node 0
[    0.020000] CPU: Physical Processor ID: 0
[    0.020000] CPU: Processor Core ID: 6
[    1.320040] CPU7: AMD FX(tm)-8120 Eight-Core Processor            stepping 02
[    1.320044] checking TSC synchronization [CPU#0 -> CPU#7]: passed.
[    1.330007] Brought up 8 CPUs
[    1.330009] Total of 8 processors activated (49934.12 BogoMIPS).
[    1.336935] CPU0 attaching sched-domain:
[    1.336938]  domain 0: span 0-7 level MC
[    1.336939]   groups: 0 1 2 3 4 5 6 7
[    1.336945] CPU1 attaching sched-domain:
[    1.336947]  domain 0: span 0-7 level MC
[    1.336948]   groups: 1 2 3 4 5 6 7 0
[    1.336952] CPU2 attaching sched-domain:
[    1.336953]  domain 0: span 0-7 level MC
[    1.336954]   groups: 2 3 4 5 6 7 0 1
[    1.336958] CPU3 attaching sched-domain:
[    1.336959]  domain 0: span 0-7 level MC
[    1.336961]   groups: 3 4 5 6 7 0 1 2
[    1.336965] CPU4 attaching sched-domain:
[    1.336966]  domain 0: span 0-7 level MC
[    1.336967]   groups: 4 5 6 7 0 1 2 3
[    1.336971] CPU5 attaching sched-domain:
[    1.336972]  domain 0: span 0-7 level MC
[    1.336973]   groups: 5 6 7 0 1 2 3 4
[    1.336977] CPU6 attaching sched-domain:
[    1.336978]  domain 0: span 0-7 level MC
[    1.336979]   groups: 6 7 0 1 2 3 4 5
[    1.336983] CPU7 attaching sched-domain:
[    1.336984]  domain 0: span 0-7 level MC
[    1.336985]   groups: 7 0 1 2 3 4 5 6
[    1.337075] devtmpfs: initialized
[    1.337075] regulator: core version 0.5
[    1.337075] Time:  3:51:54  Date: 02/24/12
[    1.337075] NET: Registered protocol family 16
[    1.337075] Trying to unpack rootfs image as initramfs...
[    1.337075] ACPI: bus type pci registered
[    1.337075] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 255
[    1.337075] PCI: MCFG area at e0000000 reserved in E820
[    1.345186] PCI: Using MMCONFIG at e0000000 - efffffff
[    1.345187] PCI: Using configuration type 1 for base access
[    1.345688] bio: create slab <bio-0> at 0
[    1.345688] ACPI: EC: Look up EC in DSDT
[    1.356721] ACPI: Interpreter enabled
[    1.356724] ACPI: (supports S0 S3 S4 S5)
[    1.356740] ACPI: Using IOAPIC for interrupt routing
[    1.362969] ACPI Warning: Incorrect checksum in table [TAMG] - 45, should be 44 (20090903/tbutils-314)
[    1.363073] ACPI: No dock devices found.
[    1.363155] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    1.363189] pci 0000:00:00.0: reg 1c 64bit mmio: [0xe0000000-0xffffffff]
[    1.363273] pci 0000:00:02.0: PME# supported from D0 D3hot D3cold
[    1.363275] pci 0000:00:02.0: PME# disabled
[    1.363303] pci 0000:00:04.0: PME# supported from D0 D3hot D3cold
[    1.363305] pci 0000:00:04.0: PME# disabled
[    1.363335] pci 0000:00:09.0: PME# supported from D0 D3hot D3cold
[    1.363336] pci 0000:00:09.0: PME# disabled
[    1.363363] pci 0000:00:0a.0: PME# supported from D0 D3hot D3cold
[    1.363364] pci 0000:00:0a.0: PME# disabled
[    1.363397] pci 0000:00:11.0: reg 10 io port: [0xff00-0xff07]
[    1.363402] pci 0000:00:11.0: reg 14 io port: [0xfe00-0xfe03]
[    1.363406] pci 0000:00:11.0: reg 18 io port: [0xfd00-0xfd07]
[    1.363410] pci 0000:00:11.0: reg 1c io port: [0xfc00-0xfc03]
[    1.363415] pci 0000:00:11.0: reg 20 io port: [0xfb00-0xfb0f]
[    1.363419] pci 0000:00:11.0: reg 24 32bit mmio: [0xfdfff000-0xfdfff3ff]
[    1.363431] pci 0000:00:11.0: set SATA to AHCI mode
[    1.363461] pci 0000:00:12.0: reg 10 32bit mmio: [0xfdffe000-0xfdffefff]
[    1.363509] pci 0000:00:12.2: reg 10 32bit mmio: [0xfdffd000-0xfdffd0ff]
[    1.363542] pci 0000:00:12.2: supports D1 D2
[    1.363543] pci 0000:00:12.2: PME# supported from D0 D1 D2 D3hot
[    1.363546] pci 0000:00:12.2: PME# disabled
[    1.363567] pci 0000:00:13.0: reg 10 32bit mmio: [0xfdffc000-0xfdffcfff]
[    1.363615] pci 0000:00:13.2: reg 10 32bit mmio: [0xfdffb000-0xfdffb0ff]
[    1.363648] pci 0000:00:13.2: supports D1 D2
[    1.363649] pci 0000:00:13.2: PME# supported from D0 D1 D2 D3hot
[    1.363651] pci 0000:00:13.2: PME# disabled
[    1.363704] pci 0000:00:14.1: reg 10 io port: [0x00-0x07]
[    1.363708] pci 0000:00:14.1: reg 14 io port: [0x00-0x03]
[    1.363713] pci 0000:00:14.1: reg 18 io port: [0x00-0x07]
[    1.363717] pci 0000:00:14.1: reg 1c io port: [0x00-0x03]
[    1.363721] pci 0000:00:14.1: reg 20 io port: [0xfa00-0xfa0f]
[    1.363755] pci 0000:00:14.2: reg 10 64bit mmio: [0xfdff4000-0xfdff7fff]
[    1.363782] pci 0000:00:14.2: PME# supported from D0 D3hot D3cold
[    1.363785] pci 0000:00:14.2: PME# disabled
[    1.363853] pci 0000:00:14.5: reg 10 32bit mmio: [0xfdffa000-0xfdffafff]
[    1.363916] pci 0000:00:15.0: supports D1 D2
[    1.363936] pci 0000:00:16.0: reg 10 32bit mmio: [0xfdff9000-0xfdff9fff]
[    1.363983] pci 0000:00:16.2: reg 10 32bit mmio: [0xfdff8000-0xfdff80ff]
[    1.364016] pci 0000:00:16.2: supports D1 D2
[    1.364017] pci 0000:00:16.2: PME# supported from D0 D1 D2 D3hot
[    1.364020] pci 0000:00:16.2: PME# disabled
[    1.364124] pci 0000:01:00.0: reg 10 32bit mmio: [0xf8000000-0xf9ffffff]
[    1.364131] pci 0000:01:00.0: reg 14 64bit mmio pref: [0xd0000000-0xd7ffffff]
[    1.364137] pci 0000:01:00.0: reg 1c 64bit mmio pref: [0xdc000000-0xdfffffff]
[    1.364141] pci 0000:01:00.0: reg 24 io port: [0xcf00-0xcf7f]
[    1.364145] pci 0000:01:00.0: reg 30 32bit mmio pref: [0x000000-0x07ffff]
[    1.364188] pci 0000:01:00.1: reg 10 32bit mmio: [0xfbffc000-0xfbffffff]
[    1.364253] pci 0000:00:02.0: bridge io port: [0xc000-0xcfff]
[    1.364255] pci 0000:00:02.0: bridge 32bit mmio: [0xf8000000-0xfbffffff]
[    1.364258] pci 0000:00:02.0: bridge 64bit mmio pref: [0xd0000000-0xdfffffff]
[    1.364287] pci 0000:02:00.0: reg 10 64bit mmio: [0xfd9f8000-0xfd9fffff]
[    1.364322] pci 0000:02:00.0: supports D1 D2
[    1.364323] pci 0000:02:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    1.364326] pci 0000:02:00.0: PME# disabled
[    1.364362] pci 0000:00:04.0: bridge io port: [0xb000-0xbfff]
[    1.364364] pci 0000:00:04.0: bridge 32bit mmio: [0xfd900000-0xfd9fffff]
[    1.364367] pci 0000:00:04.0: bridge 64bit mmio pref: [0xfd600000-0xfd6fffff]
[    1.364394] pci 0000:03:00.0: reg 10 io port: [0xee00-0xeeff]
[    1.364406] pci 0000:03:00.0: reg 18 64bit mmio pref: [0xfdeff000-0xfdefffff]
[    1.364415] pci 0000:03:00.0: reg 20 64bit mmio pref: [0xfdef8000-0xfdefbfff]
[    1.364442] pci 0000:03:00.0: supports D1 D2
[    1.364443] pci 0000:03:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    1.364446] pci 0000:03:00.0: PME# disabled
[    1.364488] pci 0000:00:09.0: bridge io port: [0xe000-0xefff]
[    1.364490] pci 0000:00:09.0: bridge 32bit mmio: [0xfd500000-0xfd5fffff]
[    1.364493] pci 0000:00:09.0: bridge 64bit mmio pref: [0xfde00000-0xfdefffff]
[    1.364521] pci 0000:04:00.0: reg 10 64bit mmio: [0xfddf8000-0xfddfffff]
[    1.364556] pci 0000:04:00.0: supports D1 D2
[    1.364558] pci 0000:04:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    1.364560] pci 0000:04:00.0: PME# disabled
[    1.364597] pci 0000:00:0a.0: bridge io port: [0xd000-0xdfff]
[    1.364599] pci 0000:00:0a.0: bridge 32bit mmio: [0xfdd00000-0xfddfffff]
[    1.364601] pci 0000:00:0a.0: bridge 64bit mmio pref: [0xfdc00000-0xfdcfffff]
[    1.364641] pci 0000:00:14.4: transparent bridge
[    1.364644] pci 0000:00:14.4: bridge io port: [0xa000-0xafff]
[    1.364647] pci 0000:00:14.4: bridge 32bit mmio: [0xfdb00000-0xfdbfffff]
[    1.364650] pci 0000:00:14.4: bridge 32bit mmio pref: [0xfda00000-0xfdafffff]
[    1.364682] pci 0000:00:15.0: bridge io port: [0x9000-0x9fff]
[    1.364684] pci 0000:00:15.0: bridge 32bit mmio: [0xfd800000-0xfd8fffff]
[    1.364688] pci 0000:00:15.0: bridge 64bit mmio pref: [0xfd700000-0xfd7fffff]
[    1.364703] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    1.364903] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX0._PRT]
[    1.364950] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P2P_._PRT]
[    1.365006] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCE2._PRT]
[    1.365044] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCE4._PRT]
[    1.365088] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCE9._PRT]
[    1.365123] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCEA._PRT]
[    1.385097] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 10 11) *0
[    1.385170] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 10 11) *0
[    1.385241] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 10 11) *0
[    1.385310] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 10 11) *0
[    1.385380] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 10 11) *0
[    1.385449] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 10 11) *0
[    1.385518] ACPI: PCI Interrupt Link [LNK0] (IRQs 3 4 5 6 7 10 11) *0
[    1.385587] ACPI: PCI Interrupt Link [LNK1] (IRQs 3 4 5 6 7 10 11) *0
[    1.385660] vgaarb: device added: PCI:0000:01:00.0,decodes=io+mem,owns=io+mem,locks=none
[    1.385663] vgaarb: loaded
[    1.385729] SCSI subsystem initialized
[    1.385738] libata version 3.00 loaded.
[    1.385738] usbcore: registered new interface driver usbfs
[    1.385738] usbcore: registered new interface driver hub
[    1.385738] usbcore: registered new device driver usb
[    1.385738] ACPI: WMI: Mapper loaded
[    1.385738] PCI: Using ACPI for IRQ routing
[    1.385738] pci 0000:00:00.0: BAR 3: address space collision on of device [0xe0000000-0xffffffff]
[    1.385738] pci 0000:00:00.0: BAR 3: can't allocate resource
[    1.385738] NetLabel: Initializing
[    1.385738] NetLabel:  domain hash size = 128
[    1.385738] NetLabel:  protocols = UNLABELED CIPSOv4
[    1.385738] NetLabel:  unlabeled traffic allowed by default
[    1.385738] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[    1.385738] hpet0: 3 comparators, 32-bit 14.318180 MHz counter
[    1.385738] Switching to clocksource tsc
[    3.015508] AppArmor: AppArmor Filesystem Enabled
[    3.015508] pnp: PnP ACPI init
[    3.015508] ACPI: bus type pnp registered
[    3.015508] pnp 00:0b: mem resource (0xcd800-0xcffff) overlaps 0000:00:00.0 BAR 3 (0x0-0x1fffffff), disabling
[    3.015508] pnp 00:0b: mem resource (0xf0000-0xf7fff) overlaps 0000:00:00.0 BAR 3 (0x0-0x1fffffff), disabling
[    3.015508] pnp 00:0b: mem resource (0xf8000-0xfbfff) overlaps 0000:00:00.0 BAR 3 (0x0-0x1fffffff), disabling
[    3.015508] pnp 00:0b: mem resource (0xfc000-0xfffff) overlaps 0000:00:00.0 BAR 3 (0x0-0x1fffffff), disabling
[    3.015508] pnp 00:0b: mem resource (0x0-0x9ffff) overlaps 0000:00:00.0 BAR 3 (0x0-0x1fffffff), disabling
[    3.015508] pnp 00:0b: mem resource (0x100000-0xcfd9ffff) overlaps 0000:00:00.0 BAR 3 (0x0-0x1fffffff), disabling
[    3.015508] pnp: PnP ACPI: found 12 devices
[    3.015508] ACPI: ACPI bus type pnp unregistered
[    3.015508] system 00:01: ioport range 0x4d0-0x4d1 has been reserved
[    3.015508] system 00:01: ioport range 0x220-0x225 has been reserved
[    3.015508] system 00:01: ioport range 0x290-0x294 has been reserved
[    3.015508] system 00:02: ioport range 0x900-0x91f has been reserved
[    3.015508] system 00:02: ioport range 0x228-0x22f has been reserved
[    3.015508] system 00:02: ioport range 0x40b-0x40b has been reserved
[    3.015508] system 00:02: ioport range 0x4d6-0x4d6 has been reserved
[    3.015508] system 00:02: ioport range 0xc00-0xc01 has been reserved
[    3.015508] system 00:02: ioport range 0xc14-0xc14 has been reserved
[    3.015508] system 00:02: ioport range 0xc50-0xc52 has been reserved
[    3.015508] system 00:02: ioport range 0xc6c-0xc6d has been reserved
[    3.015508] system 00:02: ioport range 0xc6f-0xc6f has been reserved
[    3.015508] system 00:02: ioport range 0xcd0-0xcd1 has been reserved
[    3.015508] system 00:02: ioport range 0xcd2-0xcd3 has been reserved
[    3.015508] system 00:02: ioport range 0xcd4-0xcdf has been reserved
[    3.015508] system 00:02: ioport range 0x800-0x8fe has been reserved
[    3.015508] system 00:02: ioport range 0xa10-0xa17 has been reserved
[    3.015508] system 00:02: ioport range 0xb00-0xb0f has been reserved
[    3.015508] system 00:02: ioport range 0xb10-0xb1f has been reserved
[    3.015508] system 00:02: ioport range 0xb20-0xb3f has been reserved
[    3.015508] system 00:0a: iomem range 0xe0000000-0xefffffff has been reserved
[    3.015508] system 00:0b: iomem range 0xcfda0000-0xcfdfffff could not be reserved
[    3.015508] system 00:0b: iomem range 0xffff0000-0xffffffff has been reserved
[    3.015508] system 00:0b: iomem range 0xcfe00000-0xcfefffff has been reserved
[    3.015508] system 00:0b: iomem range 0xcff00000-0xcfffffff could not be reserved
[    3.015508] system 00:0b: iomem range 0xfec00000-0xfec00fff could not be reserved
[    3.015508] system 00:0b: iomem range 0xfee00000-0xfee00fff has been reserved
[    3.015508] system 00:0b: iomem range 0xfff80000-0xfffeffff has been reserved
[    3.017719] pci 0000:00:02.0: PCI bridge, secondary bus 0000:01
[    3.017721] pci 0000:00:02.0:   IO window: 0xc000-0xcfff
[    3.017723] pci 0000:00:02.0:   MEM window: 0xf8000000-0xfbffffff
[    3.017725] pci 0000:00:02.0:   PREFETCH window: 0x000000d0000000-0x000000dfffffff
[    3.017728] pci 0000:00:04.0: PCI bridge, secondary bus 0000:02
[    3.017730] pci 0000:00:04.0:   IO window: 0xb000-0xbfff
[    3.017732] pci 0000:00:04.0:   MEM window: 0xfd900000-0xfd9fffff
[    3.017734] pci 0000:00:04.0:   PREFETCH window: 0x000000fd600000-0x000000fd6fffff
[    3.017737] pci 0000:00:09.0: PCI bridge, secondary bus 0000:03
[    3.017738] pci 0000:00:09.0:   IO window: 0xe000-0xefff
[    3.017740] pci 0000:00:09.0:   MEM window: 0xfd500000-0xfd5fffff
[    3.017742] pci 0000:00:09.0:   PREFETCH window: 0x000000fde00000-0x000000fdefffff
[    3.017745] pci 0000:00:0a.0: PCI bridge, secondary bus 0000:04
[    3.017746] pci 0000:00:0a.0:   IO window: 0xd000-0xdfff
[    3.017748] pci 0000:00:0a.0:   MEM window: 0xfdd00000-0xfddfffff
[    3.017750] pci 0000:00:0a.0:   PREFETCH window: 0x000000fdc00000-0x000000fdcfffff
[    3.017753] pci 0000:00:14.4: PCI bridge, secondary bus 0000:05
[    3.017755] pci 0000:00:14.4:   IO window: 0xa000-0xafff
[    3.017758] pci 0000:00:14.4:   MEM window: 0xfdb00000-0xfdbfffff
[    3.017761] pci 0000:00:14.4:   PREFETCH window: 0xfda00000-0xfdafffff
[    3.017765] pci 0000:00:15.0: PCI bridge, secondary bus 0000:06
[    3.017767] pci 0000:00:15.0:   IO window: 0x9000-0x9fff
[    3.017770] pci 0000:00:15.0:   MEM window: 0xfd800000-0xfd8fffff
[    3.017773] pci 0000:00:15.0:   PREFETCH window: 0x000000fd700000-0x000000fd7fffff
[    3.017780]   alloc irq_desc for 18 on node -1
[    3.017782]   alloc kstat_irqs on node -1
[    3.017785] pci 0000:00:02.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    3.017788] pci 0000:00:02.0: setting latency timer to 64
[    3.017791]   alloc irq_desc for 16 on node -1
[    3.017792]   alloc kstat_irqs on node -1
[    3.017794] pci 0000:00:04.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    3.017796] pci 0000:00:04.0: setting latency timer to 64
[    3.017799]   alloc irq_desc for 17 on node -1
[    3.017800]   alloc kstat_irqs on node -1
[    3.017803] pci 0000:00:09.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    3.017804] pci 0000:00:09.0: setting latency timer to 64
[    3.017808] pci 0000:00:0a.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    3.017810] pci 0000:00:0a.0: setting latency timer to 64
[    3.017818] pci 0000:00:15.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    3.017820] pci 0000:00:15.0: setting latency timer to 64
[    3.017823] pci_bus 0000:00: resource 0 io:  [0x00-0xffff]
[    3.017824] pci_bus 0000:00: resource 1 mem: [0x000000-0xffffffffffffffff]
[    3.017826] pci_bus 0000:01: resource 0 io:  [0xc000-0xcfff]
[    3.017828] pci_bus 0000:01: resource 1 mem: [0xf8000000-0xfbffffff]
[    3.017829] pci_bus 0000:01: resource 2 pref mem [0xd0000000-0xdfffffff]
[    3.017831] pci_bus 0000:02: resource 0 io:  [0xb000-0xbfff]
[    3.017832] pci_bus 0000:02: resource 1 mem: [0xfd900000-0xfd9fffff]
[    3.017833] pci_bus 0000:02: resource 2 pref mem [0xfd600000-0xfd6fffff]
[    3.017835] pci_bus 0000:03: resource 0 io:  [0xe000-0xefff]
[    3.017836] pci_bus 0000:03: resource 1 mem: [0xfd500000-0xfd5fffff]
[    3.017837] pci_bus 0000:03: resource 2 pref mem [0xfde00000-0xfdefffff]
[    3.017839] pci_bus 0000:04: resource 0 io:  [0xd000-0xdfff]
[    3.017840] pci_bus 0000:04: resource 1 mem: [0xfdd00000-0xfddfffff]
[    3.017842] pci_bus 0000:04: resource 2 pref mem [0xfdc00000-0xfdcfffff]
[    3.017843] pci_bus 0000:05: resource 0 io:  [0xa000-0xafff]
[    3.017845] pci_bus 0000:05: resource 1 mem: [0xfdb00000-0xfdbfffff]
[    3.017846] pci_bus 0000:05: resource 2 pref mem [0xfda00000-0xfdafffff]
[    3.017847] pci_bus 0000:05: resource 3 io:  [0x00-0xffff]
[    3.017849] pci_bus 0000:05: resource 4 mem: [0x000000-0xffffffffffffffff]
[    3.017850] pci_bus 0000:06: resource 0 io:  [0x9000-0x9fff]
[    3.017851] pci_bus 0000:06: resource 1 mem: [0xfd800000-0xfd8fffff]
[    3.017853] pci_bus 0000:06: resource 2 pref mem [0xfd700000-0xfd7fffff]
[    3.017878] NET: Registered protocol family 2
[    3.018211] IP route cache hash table entries: 524288 (order: 10, 4194304 bytes)
[    3.020141] TCP established hash table entries: 524288 (order: 11, 8388608 bytes)
[    3.022072] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    3.022316] TCP: Hash tables configured (established 524288 bind 65536)
[    3.022317] TCP reno registered
[    3.022403] NET: Registered protocol family 1
[    3.100064] pci 0000:01:00.0: Boot video device
[    3.100231] pci 0000:00:00.2: can't derive routing for PCI INT A
[    3.100233] pci 0000:00:00.2: PCI INT A: no GSI
[    3.100278]   alloc irq_desc for 24 on node -1
[    3.100279]   alloc kstat_irqs on node -1
[    3.100285] pci 0000:00:00.2: irq 24 for MSI/MSI-X
[    3.100295] AMD-Vi: Enabling IOMMU at 0000:00:00.2 cap 0x40
[    3.107074] AMD-Vi: device isolation enabled
[    3.107076] AMD-Vi: Lazy IO/TLB flushing enabled
[    3.107492] Scanning for low memory corruption every 60 seconds
[    3.107577] audit: initializing netlink socket (disabled)
[    3.107584] type=2000 audit(1330055516.100:1): initialized
[    3.114836] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    3.115920] VFS: Disk quotas dquot_6.5.2
[    3.115954] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    3.116403] fuse init (API version 7.13)
[    3.116456] msgmni has been set to 32236
[    3.116728] alg: No test for stdrng (krng)
[    3.116762] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    3.116764] io scheduler noop registered
[    3.116765] io scheduler anticipatory registered
[    3.116766] io scheduler deadline registered
[    3.116807] io scheduler cfq registered (default)
[    3.116893]   alloc irq_desc for 25 on node -1
[    3.116894]   alloc kstat_irqs on node -1
[    3.116899] pcieport 0000:00:02.0: irq 25 for MSI/MSI-X
[    3.116903] pcieport 0000:00:02.0: setting latency timer to 64
[    3.116950]   alloc irq_desc for 26 on node -1
[    3.116951]   alloc kstat_irqs on node -1
[    3.116954] pcieport 0000:00:04.0: irq 26 for MSI/MSI-X
[    3.116958] pcieport 0000:00:04.0: setting latency timer to 64
[    3.117003]   alloc irq_desc for 27 on node -1
[    3.117004]   alloc kstat_irqs on node -1
[    3.117007] pcieport 0000:00:09.0: irq 27 for MSI/MSI-X
[    3.117010] pcieport 0000:00:09.0: setting latency timer to 64
[    3.117055]   alloc irq_desc for 28 on node -1
[    3.117056]   alloc kstat_irqs on node -1
[    3.117059] pcieport 0000:00:0a.0: irq 28 for MSI/MSI-X
[    3.117062] pcieport 0000:00:0a.0: setting latency timer to 64
[    3.117123]   alloc irq_desc for 29 on node -1
[    3.117124]   alloc kstat_irqs on node -1
[    3.117130] pcieport 0000:00:15.0: irq 29 for MSI/MSI-X
[    3.117135] pcieport 0000:00:15.0: setting latency timer to 64
[    3.117185] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    3.117224] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    3.117275] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0
[    3.117277] ACPI: Power Button [PWRB]
[    3.117307] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
[    3.117309] ACPI: Power Button [PWRF]
[    3.117599] processor LNXCPU:00: registered as cooling_device0
[    3.117633] processor LNXCPU:01: registered as cooling_device1
[    3.117674] processor LNXCPU:02: registered as cooling_device2
[    3.117713] processor LNXCPU:03: registered as cooling_device3
[    3.117748] processor LNXCPU:04: registered as cooling_device4
[    3.117782] processor LNXCPU:05: registered as cooling_device5
[    3.117818] processor LNXCPU:06: registered as cooling_device6
[    3.117853] processor LNXCPU:07: registered as cooling_device7
[    3.120536] Linux agpgart interface v0.103
[    3.120560] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    3.120640] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    3.120851] 00:08: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    3.121502] brd: module loaded
[    3.121772] loop: module loaded
[    3.121822] input: Macintosh mouse button emulation as /devices/virtual/input/input2
[    3.121894] pata_acpi 0000:00:14.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    3.122089] Fixed MDIO Bus: probed
[    3.122110] PPP generic driver version 2.4.2
[    3.122128] tun: Universal TUN/TAP device driver, 1.6
[    3.122129] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    3.122171] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    3.122181] ehci_hcd 0000:00:12.2: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    3.122202] ehci_hcd 0000:00:12.2: EHCI Host Controller
[    3.122220] ehci_hcd 0000:00:12.2: new USB bus registered, assigned bus number 1
[    3.122228] ehci_hcd 0000:00:12.2: QUIRK: Enable exception for AMD Hudson ASPM
[    3.122248] ehci_hcd 0000:00:12.2: debug port 1
[    3.122261] ehci_hcd 0000:00:12.2: irq 17, io mem 0xfdffd000
[    3.140016] ehci_hcd 0000:00:12.2: USB 2.0 started, EHCI 1.00
[    3.140075] usb usb1: configuration #1 chosen from 1 choice
[    3.140092] hub 1-0:1.0: USB hub found
[    3.140097] hub 1-0:1.0: 5 ports detected
[    3.140131] ehci_hcd 0000:00:13.2: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    3.140139] ehci_hcd 0000:00:13.2: EHCI Host Controller
[    3.140157] ehci_hcd 0000:00:13.2: new USB bus registered, assigned bus number 2
[    3.140165] ehci_hcd 0000:00:13.2: QUIRK: Enable exception for AMD Hudson ASPM
[    3.140180] ehci_hcd 0000:00:13.2: debug port 1
[    3.140188] ehci_hcd 0000:00:13.2: irq 17, io mem 0xfdffb000
[    3.160015] ehci_hcd 0000:00:13.2: USB 2.0 started, EHCI 1.00
[    3.160058] usb usb2: configuration #1 chosen from 1 choice
[    3.160074] hub 2-0:1.0: USB hub found
[    3.160079] hub 2-0:1.0: 5 ports detected
[    3.160113] ehci_hcd 0000:00:16.2: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    3.160122] ehci_hcd 0000:00:16.2: EHCI Host Controller
[    3.160140] ehci_hcd 0000:00:16.2: new USB bus registered, assigned bus number 3
[    3.160148] ehci_hcd 0000:00:16.2: QUIRK: Enable exception for AMD Hudson ASPM
[    3.160162] ehci_hcd 0000:00:16.2: debug port 1
[    3.160171] ehci_hcd 0000:00:16.2: irq 17, io mem 0xfdff8000
[    3.180016] ehci_hcd 0000:00:16.2: USB 2.0 started, EHCI 1.00
[    3.180060] usb usb3: configuration #1 chosen from 1 choice
[    3.180076] hub 3-0:1.0: USB hub found
[    3.180080] hub 3-0:1.0: 4 ports detected
[    3.180112] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    3.180120] ohci_hcd 0000:00:12.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    3.180129] ohci_hcd 0000:00:12.0: OHCI Host Controller
[    3.180151] ohci_hcd 0000:00:12.0: new USB bus registered, assigned bus number 4
[    3.180168] ohci_hcd 0000:00:12.0: irq 18, io mem 0xfdffe000
[    3.243738] usb usb4: configuration #1 chosen from 1 choice
[    3.243756] hub 4-0:1.0: USB hub found
[    3.243763] hub 4-0:1.0: 5 ports detected
[    3.243801] ohci_hcd 0000:00:13.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    3.243810] ohci_hcd 0000:00:13.0: OHCI Host Controller
[    3.243831] ohci_hcd 0000:00:13.0: new USB bus registered, assigned bus number 5
[    3.243843] ohci_hcd 0000:00:13.0: irq 18, io mem 0xfdffc000
[    3.303742] usb usb5: configuration #1 chosen from 1 choice
[    3.303765] hub 5-0:1.0: USB hub found
[    3.303774] hub 5-0:1.0: 5 ports detected
[    3.303820] ohci_hcd 0000:00:14.5: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    3.303835] ohci_hcd 0000:00:14.5: OHCI Host Controller
[    3.303861] ohci_hcd 0000:00:14.5: new USB bus registered, assigned bus number 6
[    3.303880] ohci_hcd 0000:00:14.5: irq 18, io mem 0xfdffa000
[    3.306618] Freeing initrd memory: 9658k freed
[    3.363770] usb usb6: configuration #1 chosen from 1 choice
[    3.363787] hub 6-0:1.0: USB hub found
[    3.363796] hub 6-0:1.0: 2 ports detected
[    3.363832] ohci_hcd 0000:00:16.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    3.363845] ohci_hcd 0000:00:16.0: OHCI Host Controller
[    3.363866] ohci_hcd 0000:00:16.0: new USB bus registered, assigned bus number 7
[    3.363880] ohci_hcd 0000:00:16.0: irq 18, io mem 0xfdff9000
[    3.423731] usb usb7: configuration #1 chosen from 1 choice
[    3.423746] hub 7-0:1.0: USB hub found
[    3.423752] hub 7-0:1.0: 4 ports detected
[    3.423786] uhci_hcd: USB Universal Host Controller Interface driver
[    3.423833] PNP: PS/2 Controller [PNP0303:PS2K] at 0x60,0x64 irq 1
[    3.423834] PNP: PS/2 appears to have AUX port disabled, if this is incorrect please boot with i8042.nopnp
[    3.423932] serio: i8042 KBD port at 0x60,0x64 irq 1
[    3.423989] mice: PS/2 mouse device common for all mice
[    3.424355] rtc_cmos 00:05: RTC can wake from S4
[    3.424355] rtc_cmos 00:05: rtc core: registered rtc_cmos as rtc0
[    3.424355] rtc0: alarms up to one month, 242 bytes nvram, hpet irqs
[    3.424355] device-mapper: uevent: version 1.0.3
[    3.424650] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: dm-devel@redhat.com
[    3.424822] device-mapper: multipath: version 1.1.0 loaded
[    3.424824] device-mapper: multipath round-robin: version 1.0.0 loaded
[    3.425266] cpuidle: using governor ladder
[    3.425462] cpuidle: using governor menu
[    3.425692] TCP cubic registered
[    3.425788] NET: Registered protocol family 10
[    3.426271] NET: Registered protocol family 17
[    3.426315] powernow-k8: Found 1 AMD FX(tm)-8120 Eight-Core Processor            processors (8 cpu cores) (version 2.20.00)
[    3.426368] powernow-k8:    0 : pstate 0 (3100 MHz)
[    3.426369] powernow-k8:    1 : pstate 1 (2800 MHz)
[    3.426371] powernow-k8:    2 : pstate 2 (2300 MHz)
[    3.426372] powernow-k8:    3 : pstate 3 (1900 MHz)
[    3.426373] powernow-k8:    4 : pstate 4 (1400 MHz)
[    3.427294] PM: Resume from disk failed.
[    3.427305] registered taskstats version 1
[    3.427581]   Magic number: 0:433:867
[    3.427655] rtc_cmos 00:05: setting system clock to 2012-02-24 03:51:57 UTC (1330055517)
[    3.427657] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    3.427658] EDD information not available.
[    3.427701] Freeing unused kernel memory: 884k freed
[    3.427847] Write protecting the kernel read-only data: 7716k
[    3.442488] udev: starting version 151
[    3.446424] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3
[    3.469648] [drm] Initialized drm 1.1.0 20060810
[    3.472358] ahci 0000:00:11.0: version 3.0
[    3.472529]   alloc irq_desc for 19 on node -1
[    3.472531]   alloc kstat_irqs on node -1
[    3.472536] ahci 0000:00:11.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    3.472639] ahci 0000:00:11.0: AHCI 0001.0200 32 slots 4 ports 6 Gbps 0xf impl SATA mode
[    3.472641] ahci 0000:00:11.0: flags: 64bit ncq sntf ilck pm led clo pmp pio slum part 
[    3.472863] scsi0 : ahci
[    3.472953] scsi1 : ahci
[    3.473009] scsi2 : ahci
[    3.473060] scsi3 : ahci
[    3.473164] ata1: SATA max UDMA/133 abar m1024@0xfdfff000 port 0xfdfff100 irq 19
[    3.473166] ata2: SATA max UDMA/133 abar m1024@0xfdfff000 port 0xfdfff180 irq 19
[    3.473169] ata3: SATA max UDMA/133 abar m1024@0xfdfff000 port 0xfdfff200 irq 19
[    3.473171] ata4: SATA max UDMA/133 abar m1024@0xfdfff000 port 0xfdfff280 irq 19
[    3.474600] scsi4 : pata_atiixp
[    3.474683] scsi5 : pata_atiixp
[    3.475616] ata5: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xfa00 irq 14
[    3.475618] ata6: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xfa08 irq 15
[    3.476153] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    3.476153] r8169 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    3.476153] r8169 0000:03:00.0: setting latency timer to 64
[    3.476153] r8169 0000:03:00.0: unknown MAC, using family default
[    3.476153]   alloc irq_desc for 30 on node -1
[    3.476153]   alloc kstat_irqs on node -1
[    3.476153] r8169 0000:03:00.0: irq 30 for MSI/MSI-X
[    3.476419] eth0: RTL8168b/8111b at 0xffffc90001858000, 50:e5:49:c8:12:88, XID 0c900800 IRQ 30
[    3.670117] usb 5-5: new low speed USB device using ohci_hcd and address 2
[    3.820149] ata4: SATA link down (SStatus 0 SControl 300)
[    3.820155] ata3: SATA link down (SStatus 0 SControl 300)
[    3.883276] usb 5-5: configuration #1 chosen from 1 choice
[    4.000024] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    4.000027] ata2: SATA link up 6.0 Gbps (SStatus 133 SControl 300)
[    4.003614] ata1.00: ATAPI: HL-DT-ST DVDRAM GH24LS70, GL01, max UDMA/100
[    4.008155] ata1.00: configured for UDMA/100
[    4.011739] ata2.00: ATA-8: OCZ-AGILITY3, 2.15, max UDMA/133
[    4.011741] ata2.00: 234441648 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
[    4.023450] ata2.00: configured for UDMA/133
[    4.033456] scsi 0:0:0:0: CD-ROM            HL-DT-ST DVDRAM GH24LS70  GL01 PQ: 0 ANSI: 5
[    4.038195] sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
[    4.038200] Uniform CD-ROM driver Revision: 3.20
[    4.038352] sr 0:0:0:0: Attached scsi CD-ROM sr0
[    4.038407] sr 0:0:0:0: Attached scsi generic sg0 type 5
[    4.041548] scsi 1:0:0:0: Direct-Access     ATA      OCZ-AGILITY3     2.15 PQ: 0 ANSI: 5
[    4.041667] sd 1:0:0:0: Attached scsi generic sg1 type 0
[    4.041714] sd 1:0:0:0: [sda] 234441648 512-byte logical blocks: (120 GB/111 GiB)
[    4.041751] sd 1:0:0:0: [sda] Write Protect is off
[    4.041751] sd 1:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    4.041763] sd 1:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.041830]  sda: sda1
[    4.042163] sd 1:0:0:0: [sda] Attached SCSI disk
[    4.220886] usbcore: registered new interface driver hiddev
[    4.225178] input: Cypress Sem PS2/USB Browser Combo Mouse as /devices/pci0000:00/0000:00:13.0/usb5/5-5/5-5:1.0/input/input4
[    4.225250] generic-usb 0003:05FE:0011.0001: input,hidraw0: USB HID v1.00 Mouse [Cypress Sem PS2/USB Browser Combo Mouse] on usb-0000:00:13.0-5/input0
[    4.225267] usbcore: registered new interface driver usbhid
[    4.225267] usbhid: v2.6:USB HID core driver
[    4.231579] nouveau 0000:01:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    4.231579] nouveau 0000:01:00.0: setting latency timer to 64
[    4.233597] [drm] nouveau 0000:01:00.0: Unsupported chipset 0x0cf200a1
[    4.233697] nouveau 0000:01:00.0: PCI INT A disabled
[    4.233697] nouveau: probe of 0000:01:00.0 failed with error -22
[    4.234848] vga16fb: initializing
[    4.234848] vga16fb: mapped to 0xffff8800000a0000
[    4.234906] fb0: VGA16 VGA frame buffer device
[    4.411263] Console: switching to colour frame buffer device 80x30
[    5.795197] xor: automatically using best checksumming function: generic_sse
[    5.839225]    generic_sse: 12858.800 MB/sec
[    5.839227] xor: using function: generic_sse (12858.800 MB/sec)
[    5.841387] device-mapper: dm-raid45: initialized v0.2594b
[    5.937163] EXT4-fs (sda1): mounted filesystem with ordered data mode
[    6.911938] sr 0:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[    6.911941] sr 0:0:0:0: [sr0] Sense Key : Illegal Request [current] 
[    6.911943] Info fld=0x56f60, ILI
[    6.911944] sr 0:0:0:0: [sr0] Add. Sense: Illegal mode for this track
[    6.911947] sr 0:0:0:0: [sr0] CDB: Read(10): 28 00 00 05 6f 60 00 00 02 00
[    6.911952] end_request: I/O error, dev sr0, sector 1424768
[    6.911953] Buffer I/O error on device sr0, logical block 178096
[    6.936449] sr 0:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[    6.936451] sr 0:0:0:0: [sr0] Sense Key : Illegal Request [current] 
[    6.936453] Info fld=0x56f60, ILI
[    6.936454] sr 0:0:0:0: [sr0] Add. Sense: Illegal mode for this track
[    6.936457] sr 0:0:0:0: [sr0] CDB: Read(10): 28 00 00 05 6f 60 00 00 02 00
[    6.936461] end_request: I/O error, dev sr0, sector 1424768
[    6.936463] Buffer I/O error on device sr0, logical block 178096
[    6.961064] sr 0:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[    6.961103] sr 0:0:0:0: [sr0] Sense Key : Illegal Request [current] 
[    6.961156] Info fld=0x56f60, ILI
[    6.961157] sr 0:0:0:0: [sr0] Add. Sense: Illegal mode for this track
[    6.961160] sr 0:0:0:0: [sr0] CDB: Read(10): 28 00 00 05 6f 60 00 00 02 00
[    6.961183] end_request: I/O error, dev sr0, sector 1424768
[    6.961209] Buffer I/O error on device sr0, logical block 178096
[    6.985553] sr 0:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[    6.985556] sr 0:0:0:0: [sr0] Sense Key : Illegal Request [current] 
[    6.985558] Info fld=0x56f60, ILI
[    6.985559] sr 0:0:0:0: [sr0] Add. Sense: Illegal mode for this track
[    6.985562] sr 0:0:0:0: [sr0] CDB: Read(10): 28 00 00 05 6f 60 00 00 02 00
[    6.985566] end_request: I/O error, dev sr0, sector 1424768
[    6.985568] Buffer I/O error on device sr0, logical block 178096
[    7.010150] sr 0:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[    7.010157] sr 0:0:0:0: [sr0] Sense Key : Illegal Request [current] 
[    7.010163] Info fld=0x56f60, ILI
[    7.010166] sr 0:0:0:0: [sr0] Add. Sense: Illegal mode for this track
[    7.010172] sr 0:0:0:0: [sr0] CDB: Read(10): 28 00 00 05 6f 60 00 00 02 00
[    7.010183] end_request: I/O error, dev sr0, sector 1424768
[    7.010188] Buffer I/O error on device sr0, logical block 178096
[    7.034701] sr 0:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[    7.034707] sr 0:0:0:0: [sr0] Sense Key : Illegal Request [current] 
[    7.034714] Info fld=0x56f60, ILI
[    7.034716] sr 0:0:0:0: [sr0] Add. Sense: Illegal mode for this track
[    7.034723] sr 0:0:0:0: [sr0] CDB: Read(10): 28 00 00 05 6f 60 00 00 02 00
[    7.034734] end_request: I/O error, dev sr0, sector 1424768
[    7.034739] Buffer I/O error on device sr0, logical block 178096
[    7.059256] sr 0:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[    7.059263] sr 0:0:0:0: [sr0] Sense Key : Illegal Request [current] 
[    7.059269] Info fld=0x56f60, ILI
[    7.059272] sr 0:0:0:0: [sr0] Add. Sense: Illegal mode for this track
[    7.059278] sr 0:0:0:0: [sr0] CDB: Read(10): 28 00 00 05 6f 60 00 00 02 00
[    7.059289] end_request: I/O error, dev sr0, sector 1424768
[    7.059294] Buffer I/O error on device sr0, logical block 178096
[    7.182081] sr 0:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[    7.182088] sr 0:0:0:0: [sr0] Sense Key : Illegal Request [current] 
[    7.182094] Info fld=0x56f60, ILI
[    7.182097] sr 0:0:0:0: [sr0] Add. Sense: Illegal mode for this track
[    7.182103] sr 0:0:0:0: [sr0] CDB: Read(10): 28 00 00 05 6f 60 00 00 02 00
[    7.182114] end_request: I/O error, dev sr0, sector 1424768
[    7.182120] Buffer I/O error on device sr0, logical block 178096
[    7.206609] sr 0:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[    7.206616] sr 0:0:0:0: [sr0] Sense Key : Illegal Request [current] 
[    7.206622] Info fld=0x56f60, ILI
[    7.206625] sr 0:0:0:0: [sr0] Add. Sense: Illegal mode for this track
[    7.206631] sr 0:0:0:0: [sr0] CDB: Read(10): 28 00 00 05 6f 60 00 00 02 00
[    7.206643] end_request: I/O error, dev sr0, sector 1424768
[    7.206648] Buffer I/O error on device sr0, logical block 178096
[    7.231208] sr 0:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[    7.231215] sr 0:0:0:0: [sr0] Sense Key : Illegal Request [current] 
[    7.231221] Info fld=0x56f60, ILI
[    7.231224] sr 0:0:0:0: [sr0] Add. Sense: Illegal mode for this track
[    7.231231] sr 0:0:0:0: [sr0] CDB: Read(10): 28 00 00 05 6f 60 00 00 02 00
[    7.231242] end_request: I/O error, dev sr0, sector 1424768
[    8.076887] ISO 9660 Extensions: Microsoft Joliet Level 3
[    8.154317] ISO 9660 Extensions: RRIP_1991A
[    8.292248] aufs 2-standalone.tree-20091207
[    8.398819] squashfs: version 4.0 (2009/01/31) Phillip Lougher
[   60.144548] udev: starting version 151
[   64.639031] xhci_hcd 0000:02:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   64.639121] xhci_hcd 0000:02:00.0: setting latency timer to 64
[   64.639124] xhci_hcd 0000:02:00.0: xHCI Host Controller
[   64.639283] xhci_hcd 0000:02:00.0: new USB bus registered, assigned bus number 8
[   64.639283] xhci_hcd 0000:02:00.0: irq 16, io mem 0xfd9f8000
[   64.639283] usb usb8: config 1 interface 0 altsetting 0 endpoint 0x81 has no SuperSpeed companion descriptor
[   64.639435] usb usb8: configuration #1 chosen from 1 choice
[   64.639435] xHCI xhci_add_endpoint called for root hub
[   64.639435] xHCI xhci_check_bandwidth called for root hub
[   64.639490] hub 8-0:1.0: USB hub found
[   64.639490] hub 8-0:1.0: 4 ports detected
[   64.639490] xhci_hcd 0000:04:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[   64.639490] xhci_hcd 0000:04:00.0: setting latency timer to 64
[   64.639490] xhci_hcd 0000:04:00.0: xHCI Host Controller
[   64.639514] xhci_hcd 0000:04:00.0: new USB bus registered, assigned bus number 9
[   64.639514] xhci_hcd 0000:04:00.0: irq 18, io mem 0xfddf8000
[   64.639522] usb usb9: config 1 interface 0 altsetting 0 endpoint 0x81 has no SuperSpeed companion descriptor
[   64.639614] usb usb9: configuration #1 chosen from 1 choice
[   64.639614] xHCI xhci_add_endpoint called for root hub
[   64.639614] xHCI xhci_check_bandwidth called for root hub
[   64.639757] hub 9-0:1.0: USB hub found
[   64.639757] hub 9-0:1.0: 4 ports detected
[   64.920628] ACPI: resource piix4_smbus [0xb00-0xb07] conflicts with ACPI region SOR1 [0xb00-0xb0f]
[   64.920630] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   65.795665] r8169: eth0: link up
[   65.795757] r8169: eth0: link up
[   67.649117] HDA Intel 0000:00:14.2: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   67.971355] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:14.2/input/input5
[   72.126764] lp: driver loaded but no devices found
[   72.469074] ppdev: user-space parallel port driver
[   76.781326] eth0: no IPv6 routers present
[  157.031689] sr 0:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  157.031696] sr 0:0:0:0: [sr0] Sense Key : Illegal Request [current] 
[  157.031703] Info fld=0x56f60, ILI
[  157.031706] sr 0:0:0:0: [sr0] Add. Sense: Illegal mode for this track
[  157.031713] sr 0:0:0:0: [sr0] CDB: Read(10): 28 00 00 05 6f 60 00 00 02 00
[  157.031725] end_request: I/O error, dev sr0, sector 1424768
[  157.031730] __ratelimit: 1 callbacks suppressed
[  157.031734] Buffer I/O error on device sr0, logical block 356192
[  157.031739] Buffer I/O error on device sr0, logical block 356193
[  157.056220] sr 0:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  157.056227] sr 0:0:0:0: [sr0] Sense Key : Illegal Request [current] 
[  157.056233] Info fld=0x56f60, ILI
[  157.056236] sr 0:0:0:0: [sr0] Add. Sense: Illegal mode for this track
[  157.056243] sr 0:0:0:0: [sr0] CDB: Read(10): 28 00 00 05 6f 60 00 00 01 00
[  157.056254] end_request: I/O error, dev sr0, sector 1424768
[  157.056259] Buffer I/O error on device sr0, logical block 356192
[  157.080226] sr 0:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  157.080233] sr 0:0:0:0: [sr0] Sense Key : Illegal Request [current] 
[  157.080239] Info fld=0x56f61, ILI
[  157.080242] sr 0:0:0:0: [sr0] Add. Sense: Illegal mode for this track
[  157.080248] sr 0:0:0:0: [sr0] CDB: Read(10): 28 00 00 05 6f 61 00 00 01 00
[  157.080259] end_request: I/O error, dev sr0, sector 1424772
[  157.080265] Buffer I/O error on device sr0, logical block 356193
[  157.105334] sr 0:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  157.105340] sr 0:0:0:0: [sr0] Sense Key : Illegal Request [current] 
[  157.105347] Info fld=0x56f60, ILI
[  157.105349] sr 0:0:0:0: [sr0] Add. Sense: Illegal mode for this track
[  157.105356] sr 0:0:0:0: [sr0] CDB: Read(10): 28 00 00 05 6f 60 00 00 01 00
[  157.105367] end_request: I/O error, dev sr0, sector 1424768
[  157.105372] Buffer I/O error on device sr0, logical block 356192
[  157.129302] sr 0:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  157.129309] sr 0:0:0:0: [sr0] Sense Key : Illegal Request [current] 
[  157.129315] Info fld=0x56f61, ILI
[  157.129318] sr 0:0:0:0: [sr0] Add. Sense: Illegal mode for this track
[  157.129324] sr 0:0:0:0: [sr0] CDB: Read(10): 28 00 00 05 6f 61 00 00 01 00
[  157.129336] end_request: I/O error, dev sr0, sector 1424772
[  157.129341] Buffer I/O error on device sr0, logical block 356193
[  157.154396] sr 0:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  157.154403] sr 0:0:0:0: [sr0] Sense Key : Illegal Request [current] 
[  157.154409] Info fld=0x56f60, ILI
[  157.154412] sr 0:0:0:0: [sr0] Add. Sense: Illegal mode for this track
[  157.154418] sr 0:0:0:0: [sr0] CDB: Read(10): 28 00 00 05 6f 60 00 00 01 00
[  157.154429] end_request: I/O error, dev sr0, sector 1424768
[  157.154435] Buffer I/O error on device sr0, logical block 356192
[  157.178408] sr 0:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  157.178415] sr 0:0:0:0: [sr0] Sense Key : Illegal Request [current] 
[  157.178421] Info fld=0x56f61, ILI
[  157.178424] sr 0:0:0:0: [sr0] Add. Sense: Illegal mode for this track
[  157.178431] sr 0:0:0:0: [sr0] CDB: Read(10): 28 00 00 05 6f 61 00 00 01 00
[  157.178442] end_request: I/O error, dev sr0, sector 1424772
[  157.178447] Buffer I/O error on device sr0, logical block 356193
[  157.583803] sr 0:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  157.583810] sr 0:0:0:0: [sr0] Sense Key : Illegal Request [current] 
[  157.583816] Info fld=0x56f60, ILI
[  157.583819] sr 0:0:0:0: [sr0] Add. Sense: Illegal mode for this track
[  157.583826] sr 0:0:0:0: [sr0] CDB: Read(10): 28 00 00 05 6f 60 00 00 02 00
[  157.583837] end_request: I/O error, dev sr0, sector 1424768
[  157.583842] Buffer I/O error on device sr0, logical block 356192
[  157.583847] Buffer I/O error on device sr0, logical block 356193
[  157.608351] sr 0:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  157.608358] sr 0:0:0:0: [sr0] Sense Key : Illegal Request [current] 
[  157.608365] Info fld=0x56f60, ILI
[  157.608367] sr 0:0:0:0: [sr0] Add. Sense: Illegal mode for this track
[  157.608374] sr 0:0:0:0: [sr0] CDB: Read(10): 28 00 00 05 6f 60 00 00 01 00
[  157.608385] end_request: I/O error, dev sr0, sector 1424768
[  157.632356] sr 0:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  157.632362] sr 0:0:0:0: [sr0] Sense Key : Illegal Request [current] 
[  157.632369] Info fld=0x56f61, ILI
[  157.632371] sr 0:0:0:0: [sr0] Add. Sense: Illegal mode for this track
[  157.632378] sr 0:0:0:0: [sr0] CDB: Read(10): 28 00 00 05 6f 61 00 00 01 00
[  157.632389] end_request: I/O error, dev sr0, sector 1424772
[  157.657425] sr 0:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  157.657432] sr 0:0:0:0: [sr0] Sense Key : Illegal Request [current] 
[  157.657438] Info fld=0x56f60, ILI
[  157.657441] sr 0:0:0:0: [sr0] Add. Sense: Illegal mode for this track
[  157.657447] sr 0:0:0:0: [sr0] CDB: Read(10): 28 00 00 05 6f 60 00 00 01 00
[  157.657458] end_request: I/O error, dev sr0, sector 1424768
[  157.681441] sr 0:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  157.681447] sr 0:0:0:0: [sr0] Sense Key : Illegal Request [current] 
[  157.681454] Info fld=0x56f61, ILI
[  157.681456] sr 0:0:0:0: [sr0] Add. Sense: Illegal mode for this track
[  157.681463] sr 0:0:0:0: [sr0] CDB: Read(10): 28 00 00 05 6f 61 00 00 01 00
[  157.681474] end_request: I/O error, dev sr0, sector 1424772
[  158.626648] sr 0:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  158.626655] sr 0:0:0:0: [sr0] Sense Key : Illegal Request [current] 
[  158.626662] Info fld=0x56f60, ILI
[  158.626665] sr 0:0:0:0: [sr0] Add. Sense: Illegal mode for this track
[  158.626672] sr 0:0:0:0: [sr0] CDB: Read(10): 28 00 00 05 6f 60 00 00 02 00
[  158.626683] end_request: I/O error, dev sr0, sector 1424768
[  158.822930] sr 0:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  158.822937] sr 0:0:0:0: [sr0] Sense Key : Illegal Request [current] 
[  158.822943] Info fld=0x56f60, ILI
[  158.822946] sr 0:0:0:0: [sr0] Add. Sense: Illegal mode for this track
[  158.822953] sr 0:0:0:0: [sr0] CDB: Read(10): 28 00 00 05 6f 60 00 00 02 00
[  158.822964] end_request: I/O error, dev sr0, sector 1424768
[  158.847473] sr 0:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  158.847480] sr 0:0:0:0: [sr0] Sense Key : Illegal Request [current] 
[  158.847486] Info fld=0x56f60, ILI
[  158.847489] sr 0:0:0:0: [sr0] Add. Sense: Illegal mode for this track
[  158.847496] sr 0:0:0:0: [sr0] CDB: Read(10): 28 00 00 05 6f 60 00 00 01 00
[  158.847507] end_request: I/O error, dev sr0, sector 1424768
[  158.871482] sr 0:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  158.871489] sr 0:0:0:0: [sr0] Sense Key : Illegal Request [current] 
[  158.871495] Info fld=0x56f61, ILI
[  158.871498] sr 0:0:0:0: [sr0] Add. Sense: Illegal mode for this track
[  158.871504] sr 0:0:0:0: [sr0] CDB: Read(10): 28 00 00 05 6f 61 00 00 01 00
[  158.871516] end_request: I/O error, dev sr0, sector 1424772
[  159.779797] sr 0:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  159.779804] sr 0:0:0:0: [sr0] Sense Key : Illegal Request [current] 
[  159.779811] Info fld=0x56f60, ILI
[  159.779814] sr 0:0:0:0: [sr0] Add. Sense: Illegal mode for this track
[  159.779821] sr 0:0:0:0: [sr0] CDB: Read(10): 28 00 00 05 6f 60 00 00 02 00
[  159.779833] end_request: I/O error, dev sr0, sector 1424768
[  159.804422] sr 0:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  159.804429] sr 0:0:0:0: [sr0] Sense Key : Illegal Request [current] 
[  159.804435] Info fld=0x56f60, ILI
[  159.804438] sr 0:0:0:0: [sr0] Add. Sense: Illegal mode for this track
[  159.804445] sr 0:0:0:0: [sr0] CDB: Read(10): 28 00 00 05 6f 60 00 00 01 00
[  159.804456] end_request: I/O error, dev sr0, sector 1424768
[  159.828402] sr 0:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  159.828409] sr 0:0:0:0: [sr0] Sense Key : Illegal Request [current] 
[  159.828415] Info fld=0x56f61, ILI
[  159.828418] sr 0:0:0:0: [sr0] Add. Sense: Illegal mode for this track
[  159.828425] sr 0:0:0:0: [sr0] CDB: Read(10): 28 00 00 05 6f 61 00 00 01 00
[  159.828436] end_request: I/O error, dev sr0, sector 1424772
[  160.233870] sr 0:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  160.233876] sr 0:0:0:0: [sr0] Sense Key : Illegal Request [current] 
[  160.233883] Info fld=0x56f60, ILI
[  160.233885] sr 0:0:0:0: [sr0] Add. Sense: Illegal mode for this track
[  160.233892] sr 0:0:0:0: [sr0] CDB: Read(10): 28 00 00 05 6f 60 00 00 02 00
[  160.233903] end_request: I/O error, dev sr0, sector 1424768
[  160.258338] sr 0:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  160.258345] sr 0:0:0:0: [sr0] Sense Key : Illegal Request [current] 
[  160.258351] Info fld=0x56f60, ILI
[  160.258354] sr 0:0:0:0: [sr0] Add. Sense: Illegal mode for this track
[  160.258360] sr 0:0:0:0: [sr0] CDB: Read(10): 28 00 00 05 6f 60 00 00 01 00
[  160.258371] end_request: I/O error, dev sr0, sector 1424768
[  160.282355] sr 0:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  160.282361] sr 0:0:0:0: [sr0] Sense Key : Illegal Request [current] 
[  160.282368] Info fld=0x56f61, ILI
[  160.282370] sr 0:0:0:0: [sr0] Add. Sense: Illegal mode for this track
[  160.282377] sr 0:0:0:0: [sr0] CDB: Read(10): 28 00 00 05 6f 61 00 00 01 00
[  160.282388] end_request: I/O error, dev sr0, sector 1424772
[  160.466921] sr 0:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  160.466927] sr 0:0:0:0: [sr0] Sense Key : Illegal Request [current] 
[  160.466934] Info fld=0x56f60, ILI
[  160.466936] sr 0:0:0:0: [sr0] Add. Sense: Illegal mode for this track
[  160.466943] sr 0:0:0:0: [sr0] CDB: Read(10): 28 00 00 05 6f 60 00 00 02 00
[  160.466954] end_request: I/O error, dev sr0, sector 1424768
[  160.491447] sr 0:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  160.491453] sr 0:0:0:0: [sr0] Sense Key : Illegal Request [current] 
[  160.491460] Info fld=0x56f60, ILI
[  160.491463] sr 0:0:0:0: [sr0] Add. Sense: Illegal mode for this track
[  160.491470] sr 0:0:0:0: [sr0] CDB: Read(10): 28 00 00 05 6f 60 00 00 01 00
[  160.491481] end_request: I/O error, dev sr0, sector 1424768
[  160.515456] sr 0:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  160.515462] sr 0:0:0:0: [sr0] Sense Key : Illegal Request [current] 
[  160.515469] Info fld=0x56f61, ILI
[  160.515471] sr 0:0:0:0: [sr0] Add. Sense: Illegal mode for this track
[  160.515478] sr 0:0:0:0: [sr0] CDB: Read(10): 28 00 00 05 6f 61 00 00 01 00
[  160.515489] end_request: I/O error, dev sr0, sector 1424772
[  160.540527] sr 0:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  160.540534] sr 0:0:0:0: [sr0] Sense Key : Illegal Request [current] 
[  160.540540] Info fld=0x56f60, ILI
[  160.540543] sr 0:0:0:0: [sr0] Add. Sense: Illegal mode for this track
[  160.540549] sr 0:0:0:0: [sr0] CDB: Read(10): 28 00 00 05 6f 60 00 00 01 00
[  160.540560] end_request: I/O error, dev sr0, sector 1424768
[  160.564532] sr 0:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  160.564539] sr 0:0:0:0: [sr0] Sense Key : Illegal Request [current] 
[  160.564545] Info fld=0x56f61, ILI
[  160.564548] sr 0:0:0:0: [sr0] Add. Sense: Illegal mode for this track
[  160.564554] sr 0:0:0:0: [sr0] CDB: Read(10): 28 00 00 05 6f 61 00 00 01 00
[  160.564565] end_request: I/O error, dev sr0, sector 1424772
[  160.969945] sr 0:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  160.969952] sr 0:0:0:0: [sr0] Sense Key : Illegal Request [current] 
[  160.969958] Info fld=0x56f60, ILI
[  160.969960] sr 0:0:0:0: [sr0] Add. Sense: Illegal mode for this track
[  160.969967] sr 0:0:0:0: [sr0] CDB: Read(10): 28 00 00 05 6f 60 00 00 02 00
[  160.969978] end_request: I/O error, dev sr0, sector 1424768
[  160.994489] sr 0:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  160.994496] sr 0:0:0:0: [sr0] Sense Key : Illegal Request [current] 
[  160.994502] Info fld=0x56f60, ILI
[  160.994505] sr 0:0:0:0: [sr0] Add. Sense: Illegal mode for this track
[  160.994512] sr 0:0:0:0: [sr0] CDB: Read(10): 28 00 00 05 6f 60 00 00 01 00
[  160.994523] end_request: I/O error, dev sr0, sector 1424768
[  161.018484] sr 0:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  161.018491] sr 0:0:0:0: [sr0] Sense Key : Illegal Request [current] 
[  161.018497] Info fld=0x56f61, ILI
[  161.018500] sr 0:0:0:0: [sr0] Add. Sense: Illegal mode for this track
[  161.018507] sr 0:0:0:0: [sr0] CDB: Read(10): 28 00 00 05 6f 61 00 00 01 00
[  161.018518] end_request: I/O error, dev sr0, sector 1424772

```

Matt

---

