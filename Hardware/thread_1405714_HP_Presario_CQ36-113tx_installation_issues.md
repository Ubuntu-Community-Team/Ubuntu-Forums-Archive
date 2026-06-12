---
title: "HP Presario CQ36-113tx installation issues"
date: 2010-02-13
forum: Hardware
---

### Post by whatsup_will on 2010-02-13
i've been trying to install the latest stable release of ubuntu onto my brand new laptop (brought 2 days ago) and sadly it seems it has 2 graphics card sharing the same port, a intergrated graphics card and a discrete grpahics card, saldy it seems that ubuntu x-server gets confused and gives me no display after the select langage and what do you want to do screen (start live cd or install)

both options give me a black screen.

does anyone have a solution to get around the x-server issue and duel graphics card running the same display.

does ubuntu server edition ever enter x-server when installing? can i go via that path to get something installed on my laptop?

---

### Post by whatsup_will on 2010-02-14
well i got ubuntu server to install in cli mode, sadly when it boots up after the install it turns on both graphics cards and give me a black screen...

it also seams that when i reboot and go to windows my ATI discrete graphics had video output issues unless i reboot :'(

i've finally managed to access the ext4 partition under windows (had to install virtualbox and add the real disk as a raw disk and mounted the partition as there is no windows drivers that support the extend mode that is enabled by default)

which logs should i upload?

and what can i do to at least allow me to log into a cli server. xorg can come later

---

### Post by whatsup_will on 2010-02-14
here is the dmesg

```
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.31-14-server (buildd@crested) (gcc version 4.4.1 (Ubuntu 4.4.1-4ubuntu8) ) #48-Ubuntu SMP Fri Oct 16 15:07:34 UTC 2009 (Ubuntu 2.6.31-14.48-server)
[    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-2.6.31-14-server root=UUID=dce0c8b2-f26e-4e8b-b3ff-ac5bf0e0f34f ro quiet splash
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   Centaur CentaurHauls
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009d000 (usable)
[    0.000000]  BIOS-e820: 000000000009d000 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 00000000bb68d000 (usable)
[    0.000000]  BIOS-e820: 00000000bb68d000 - 00000000bb6bf000 (reserved)
[    0.000000]  BIOS-e820: 00000000bb6bf000 - 00000000bb74e000 (usable)
[    0.000000]  BIOS-e820: 00000000bb74e000 - 00000000bb7bf000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000bb7bf000 - 00000000bb7dd000 (usable)
[    0.000000]  BIOS-e820: 00000000bb7dd000 - 00000000bb7ff000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000bb7ff000 - 00000000bb800000 (usable)
[    0.000000]  BIOS-e820: 00000000bb800000 - 00000000c0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000f0000000 - 00000000f8000000 (reserved)
[    0.000000]  BIOS-e820: 00000000feb00000 - 00000000feb04000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed10000 - 00000000fed14000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed18000 - 00000000fed1a000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed1b000 - 00000000fed20000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000ffe00000 - 0000000100000000 (reserved)
[    0.000000]  BIOS-e820: 0000000100000000 - 0000000138000000 (usable)
[    0.000000] DMI 2.6 present.
[    0.000000] last_pfn = 0x138000 max_arch_pfn = 0x400000000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-EFFFF write-through
[    0.000000]   F0000-FFFFF write-combining
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000 mask F80000000 write-back
[    0.000000]   1 base 0FFE00000 mask FFFE00000 write-protect
[    0.000000]   2 base 080000000 mask FC0000000 write-back
[    0.000000]   3 base 0BC000000 mask FFC000000 uncachable
[    0.000000]   4 base 0BB800000 mask FFF800000 uncachable
[    0.000000]   5 base 100000000 mask FC0000000 write-back
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] last_pfn = 0xbb800 max_arch_pfn = 0x400000000
[    0.000000] e820 update range: 0000000000001000 - 0000000000006000 (usable) ==> (reserved)
[    0.000000] Scanning 1 areas for low memory corruption
[    0.000000] modified physical RAM map:
[    0.000000]  modified: 0000000000000000 - 0000000000001000 (usable)
[    0.000000]  modified: 0000000000001000 - 0000000000006000 (reserved)
[    0.000000]  modified: 0000000000006000 - 000000000009d000 (usable)
[    0.000000]  modified: 000000000009d000 - 00000000000a0000 (reserved)
[    0.000000]  modified: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  modified: 0000000000100000 - 00000000bb68d000 (usable)
[    0.000000]  modified: 00000000bb68d000 - 00000000bb6bf000 (reserved)
[    0.000000]  modified: 00000000bb6bf000 - 00000000bb74e000 (usable)
[    0.000000]  modified: 00000000bb74e000 - 00000000bb7bf000 (ACPI NVS)
[    0.000000]  modified: 00000000bb7bf000 - 00000000bb7dd000 (usable)
[    0.000000]  modified: 00000000bb7dd000 - 00000000bb7ff000 (ACPI data)
[    0.000000]  modified: 00000000bb7ff000 - 00000000bb800000 (usable)
[    0.000000]  modified: 00000000bb800000 - 00000000c0000000 (reserved)
[    0.000000]  modified: 00000000f0000000 - 00000000f8000000 (reserved)
[    0.000000]  modified: 00000000feb00000 - 00000000feb04000 (reserved)
[    0.000000]  modified: 00000000fec00000 - 00000000fec01000 (reserved)
[    0.000000]  modified: 00000000fed10000 - 00000000fed14000 (reserved)
[    0.000000]  modified: 00000000fed18000 - 00000000fed1a000 (reserved)
[    0.000000]  modified: 00000000fed1b000 - 00000000fed20000 (reserved)
[    0.000000]  modified: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  modified: 00000000ffe00000 - 0000000100000000 (reserved)
[    0.000000]  modified: 0000000100000000 - 0000000138000000 (usable)
[    0.000000] initial memory mapped : 0 - 20000000
[    0.000000] init_memory_mapping: 0000000000000000-00000000bb800000
[    0.000000] Using x86 segment limits to approximate NX protection
[    0.000000]  0000000000 - 00bb800000 page 2M
[    0.000000] kernel direct mapping tables up to bb800000 @ 8000-c000
[    0.000000] init_memory_mapping: 0000000100000000-0000000138000000
[    0.000000] Using x86 segment limits to approximate NX protection
[    0.000000]  0100000000 - 0138000000 page 2M
[    0.000000] kernel direct mapping tables up to 138000000 @ a000-10000
[    0.000000] RAMDISK: 37956000 - 37fefd3b
[    0.000000] ACPI: RSDP 00000000000fe020 00024 (v02 HP    )
[    0.000000] ACPI: XSDT 00000000bb7fe120 000A4 (v01 HPQOEM SLIC-MPC 00000001      01000013)
[    0.000000] ACPI: FACP 00000000bb7fc000 000F4 (v04 HP     SLIC-MPC 00000001 MSFT 01000013)
[    0.000000] ACPI: DSDT 00000000bb7e8000 10855 (v02 HP     SLIC-MPC 00000001 MSFT 01000013)
[    0.000000] ACPI: FACS 00000000bb75f000 00040
[    0.000000] ACPI: ASF! 00000000bb7fd000 000A5 (v32 HPQOEM SLIC-MPC 00000001 MSFT 01000013)
[    0.000000] ACPI: HPET 00000000bb7fb000 00038 (v01 HPQOEM SLIC-MPC 00000001 MSFT 01000013)
[    0.000000] ACPI: APIC 00000000bb7fa000 000BC (v02 HPQOEM SLIC-MPC 00000001 MSFT 01000013)
[    0.000000] ACPI: MCFG 00000000bb7f9000 0003C (v01 HPQOEM SLIC-MPC 00000001 MSFT 01000013)
[    0.000000] ACPI: SLIC 00000000bb7e7000 00176 (v01 HPQOEM SLIC-MPC 00000001 MSFT 01000013)
[    0.000000] ACPI: SSDT 00000000bb7e6000 00773 (v01 TrmRef PtidDevc 00001000 INTL 20051117)
[    0.000000] ACPI: SSDT 00000000bb7e5000 00172 (v01  VaRef  Va_Acpi 00003000 INTL 20051117)
[    0.000000] ACPI: BOOT 00000000bb7e4000 00028 (v01 HPQOEM SLIC-MPC 00000001 MSFT 01000013)
[    0.000000] ACPI: SSDT 00000000bb7e3000 00310 (v01 INTEL  SataAhci 00001000 INTL 20051117)
[    0.000000] ACPI: SSDT 00000000bb7e2000 00C39 (v01 INTEL   SataPri 00001000 INTL 20051117)
[    0.000000] ACPI: SSDT 00000000bb7e1000 006C5 (v01 INTEL   SataSec 00001000 INTL 20051117)
[    0.000000] ACPI: SPCR 00000000bb7e0000 00050 (v01 HPQOEM SLIC-MPC 00000000 MSFT 01000013)
[    0.000000] ACPI: ASPT 00000000bb7df000 00034 (v04 HPQOEM SLIC-MPC 00000001 MSFT 01000013)
[    0.000000] ACPI: WDRT 00000000bb7de000 00047 (v01 HPQOEM SLIC-MPC 00000000 MSFT 01000013)
[    0.000000] ACPI: SSDT 00000000bb7dd000 009F1 (v01  PmRef    CpuPm 00003000 INTL 20051117)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at 0000000000000000-0000000138000000
[    0.000000] Bootmem setup node 0 0000000000000000-0000000138000000
[    0.000000]   NODE_DATA [000000000000b000 - 000000000000ffff]
[    0.000000]   bootmap [0000000000010000 -  0000000000036fff] pages 27
[    0.000000] (8 early reservations) ==> bootmem [0000000000 - 0138000000]
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000]   #1 [0000006000 - 0000008000]       TRAMPOLINE ==> [0000006000 - 0000008000]
[    0.000000]   #2 [0001000000 - 00019e0ccc]    TEXT DATA BSS ==> [0001000000 - 00019e0ccc]
[    0.000000]   #3 [0037956000 - 0037fefd3b]          RAMDISK ==> [0037956000 - 0037fefd3b]
[    0.000000]   #4 [000009d000 - 0000100000]    BIOS reserved ==> [000009d000 - 0000100000]
[    0.000000]   #5 [00019e1000 - 00019e1354]              BRK ==> [00019e1000 - 00019e1354]
[    0.000000]   #6 [0000008000 - 000000a000]          PGTABLE ==> [0000008000 - 000000a000]
[    0.000000]   #7 [000000a000 - 000000b000]          PGTABLE ==> [000000a000 - 000000b000]
[    0.000000]  [ffffea0000000000-ffffea00045fffff] PMD -> [ffff880028600000-ffff88002bdfffff] on node 0
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000000 -> 0x00001000
[    0.000000]   DMA32    0x00001000 -> 0x00100000
[    0.000000]   Normal   0x00100000 -> 0x00138000
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[7] active PFN ranges
[    0.000000]     0: 0x00000000 -> 0x00000001
[    0.000000]     0: 0x00000006 -> 0x0000009d
[    0.000000]     0: 0x00000100 -> 0x000bb68d
[    0.000000]     0: 0x000bb6bf -> 0x000bb74e
[    0.000000]     0: 0x000bb7bf -> 0x000bb7dd
[    0.000000]     0: 0x000bb7ff -> 0x000bb800
[    0.000000]     0: 0x00100000 -> 0x00138000
[    0.000000] On node 0 totalpages: 997075
[    0.000000]   DMA zone: 56 pages used for memmap
[    0.000000]   DMA zone: 105 pages reserved
[    0.000000]   DMA zone: 3831 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 14280 pages used for memmap
[    0.000000]   DMA32 zone: 749427 pages, LIFO batch:31
[    0.000000]   Normal zone: 3136 pages used for memmap
[    0.000000]   Normal zone: 226240 pages, LIFO batch:31
[    0.000000] ACPI: PM-Timer IO Port: 0x408
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x04] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x05] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x05] lapic_id[0x00] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x06] lapic_id[0x00] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x07] lapic_id[0x00] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x08] lapic_id[0x00] disabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x02] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x03] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x04] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x05] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x06] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x07] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x08] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
[    0.000000] SMP: Allowing 8 CPUs, 4 hotplug CPUs
[    0.000000] nr_irqs_gsi: 24
[    0.000000] PM: Registered nosave memory: 0000000000001000 - 0000000000006000
[    0.000000] PM: Registered nosave memory: 000000000009d000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
[    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
[    0.000000] PM: Registered nosave memory: 00000000bb68d000 - 00000000bb6bf000
[    0.000000] PM: Registered nosave memory: 00000000bb74e000 - 00000000bb7bf000
[    0.000000] PM: Registered nosave memory: 00000000bb7dd000 - 00000000bb7ff000
[    0.000000] PM: Registered nosave memory: 00000000bb800000 - 00000000c0000000
[    0.000000] PM: Registered nosave memory: 00000000c0000000 - 00000000f0000000
[    0.000000] PM: Registered nosave memory: 00000000f0000000 - 00000000f8000000
[    0.000000] PM: Registered nosave memory: 00000000f8000000 - 00000000feb00000
[    0.000000] PM: Registered nosave memory: 00000000feb00000 - 00000000feb04000
[    0.000000] PM: Registered nosave memory: 00000000feb04000 - 00000000fec00000
[    0.000000] PM: Registered nosave memory: 00000000fec00000 - 00000000fec01000
[    0.000000] PM: Registered nosave memory: 00000000fec01000 - 00000000fed10000
[    0.000000] PM: Registered nosave memory: 00000000fed10000 - 00000000fed14000
[    0.000000] PM: Registered nosave memory: 00000000fed14000 - 00000000fed18000
[    0.000000] PM: Registered nosave memory: 00000000fed18000 - 00000000fed1a000
[    0.000000] PM: Registered nosave memory: 00000000fed1a000 - 00000000fed1b000
[    0.000000] PM: Registered nosave memory: 00000000fed1b000 - 00000000fed20000
[    0.000000] PM: Registered nosave memory: 00000000fed20000 - 00000000fee00000
[    0.000000] PM: Registered nosave memory: 00000000fee00000 - 00000000fee01000
[    0.000000] PM: Registered nosave memory: 00000000fee01000 - 00000000ffe00000
[    0.000000] PM: Registered nosave memory: 00000000ffe00000 - 0000000100000000
[    0.000000] Allocating PCI resources starting at c0000000 (gap: c0000000:30000000)
[    0.000000] NR_CPUS:64 nr_cpumask_bits:64 nr_cpu_ids:8 nr_node_ids:1
[    0.000000] PERCPU: Embedded 30 pages at ffff880028023000, static data 90720 bytes
[    0.000000] Built 1 zonelists in Node order, mobility grouping on.  Total pages: 979498
[    0.000000] Policy zone: Normal
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.31-14-server root=UUID=dce0c8b2-f26e-4e8b-b3ff-ac5bf0e0f34f ro quiet splash
[    0.000000] PID hash table entries: 4096 (order: 12, 32768 bytes)
[    0.000000] Initializing CPU#0
[    0.000000] Checking aperture...
[    0.000000] No AGP bridge found
[    0.000000] Calgary: detecting Calgary via BIOS EBDA area
[    0.000000] Calgary: Unable to locate Rio Grande table in EBDA - bailing!
[    0.000000] PCI-DMA: Using software bounce buffering for IO (SWIOTLB)
[    0.000000] Placing 64MB software IO TLB between ffff880020000000 - ffff880024000000
[    0.000000] software IO TLB at phys 0x20000000 - 0x24000000
[    0.000000] Memory: 3846916k/5111808k available (5303k kernel code, 1123508k absent, 141384k reserved, 3013k data, 660k init)
[    0.000000] SLUB: Genslabs=14, HWalign=64, Order=0-3, MinObjects=0, CPUs=8, Nodes=1
[    0.000000] NR_IRQS:4352 nr_irqs:472
[    0.000000] Extended CMOS year: 2000
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 2260.923 MHz processor.
[    0.001473] Console: colour VGA+ 80x25
[    0.001476] console [tty0] enabled
[    0.010310] allocated 40632320 bytes of page_cgroup
[    0.010312] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.010464] hpet clockevent registered
[    0.010472]   alloc irq_desc for 24 on node 0
[    0.010475]   alloc kstat_irqs on node 0
[    0.010483]   alloc irq_desc for 25 on node 0
[    0.010484]   alloc kstat_irqs on node 0
[    0.010487]   alloc irq_desc for 26 on node 0
[    0.010488]   alloc kstat_irqs on node 0
[    0.010491]   alloc irq_desc for 27 on node 0
[    0.010492]   alloc kstat_irqs on node 0
[    0.010496]   alloc irq_desc for 28 on node 0
[    0.010497]   alloc kstat_irqs on node 0
[    0.010499] HPET: 8 timers in total, 5 timers will be used for per-cpu timer
[    0.010504] Calibrating delay loop (skipped), value calculated using timer frequency.. 4521.84 BogoMIPS (lpj=22609230)
[    0.010521] Security Framework initialized
[    0.010538] AppArmor: AppArmor initialized
[    0.010801] Dentry cache hash table entries: 524288 (order: 10, 4194304 bytes)
[    0.011760] Inode-cache hash table entries: 262144 (order: 9, 2097152 bytes)
[    0.012164] Mount-cache hash table entries: 256
[    0.012267] Initializing cgroup subsys ns
[    0.012271] Initializing cgroup subsys cpuacct
[    0.012274] Initializing cgroup subsys memory
[    0.012279] Initializing cgroup subsys freezer
[    0.012280] Initializing cgroup subsys net_cls
[    0.012291] CPU: Physical Processor ID: 0
[    0.012292] CPU: Processor Core ID: 0
[    0.012296] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.012297] CPU: L2 cache: 256K
[    0.012298] CPU: L3 cache: 3072K
[    0.012301] CPU 0/0x0 -> Node 0
[    0.012304] mce: CPU supports 9 MCE banks
[    0.012312] CPU0: Thermal monitoring handled by SMI
[    0.012316] CPU 0 MCA banks CMCI:2 CMCI:3 CMCI:5 CMCI:6
[    0.012323] using mwait in idle threads.
[    0.012324] Performance Counters: Nehalem/Corei7 events, Intel PMU driver.
[    0.012329] ... version:                 3
[    0.012330] ... bit width:               48
[    0.012332] ... generic counters:        4
[    0.012333] ... value mask:              0000ffffffffffff
[    0.012334] ... max period:              000000007fffffff
[    0.012335] ... fixed-purpose counters:  3
[    0.012336] ... counter mask:            000000070000000f
[    0.014188] ACPI: Core revision 20090521
[    0.072623] Setting APIC routing to flat
[    0.073025] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.172831] CPU0: Intel(R) Core(TM) i5 CPU       M 430  @ 2.27GHz stepping 02
[    0.290065] Booting processor 1 APIC 0x1 ip 0x6000
[    0.300350] Initializing CPU#1
[    0.449652] Calibrating delay using timer specific routine.. 4522.50 BogoMIPS (lpj=22612544)
[    0.449661] CPU: Physical Processor ID: 0
[    0.449662] CPU: Processor Core ID: 0
[    0.449665] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.449667] CPU: L2 cache: 256K
[    0.449668] CPU: L3 cache: 3072K
[    0.449670] CPU 1/0x1 -> Node 0
[    0.449673] mce: CPU supports 9 MCE banks
[    0.449684] CPU1: Thermal monitoring enabled (TM1)
[    0.449688] CPU 1 MCA banks SHD:2 SHD:3 SHD:5 SHD:6
[    0.450718] x86 PAT enabled: cpu 1, old 0x7040600070406, new 0x7010600070106
[    0.452023] CPU1: Intel(R) Core(TM) i5 CPU       M 430  @ 2.27GHz stepping 02
[    0.452033] Skipping synchronization checks as TSC is reliable.
[    0.452132] Booting processor 2 APIC 0x4 ip 0x6000
[    0.462249] Initializing CPU#2
[    0.609352] Calibrating delay using timer specific routine.. 4522.51 BogoMIPS (lpj=22612578)
[    0.609361] CPU: Physical Processor ID: 0
[    0.609362] CPU: Processor Core ID: 2
[    0.609364] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.609365] CPU: L2 cache: 256K
[    0.609366] CPU: L3 cache: 3072K
[    0.609368] CPU 2/0x4 -> Node 0
[    0.609371] mce: CPU supports 9 MCE banks
[    0.609381] CPU2: Thermal monitoring enabled (TM1)
[    0.609384] CPU 2 MCA banks CMCI:2 CMCI:3 CMCI:5 SHD:6
[    0.610150] x86 PAT enabled: cpu 2, old 0x7040600070406, new 0x7010600070106
[    0.611111] CPU2: Intel(R) Core(TM) i5 CPU       M 430  @ 2.27GHz stepping 02
[    0.611122] Skipping synchronization checks as TSC is reliable.
[    0.611220] Booting processor 3 APIC 0x5 ip 0x6000
[    0.621337] Initializing CPU#3
[    0.769053] Calibrating delay using timer specific routine.. 4522.52 BogoMIPS (lpj=22612633)
[    0.769061] CPU: Physical Processor ID: 0
[    0.769062] CPU: Processor Core ID: 2
[    0.769064] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.769066] CPU: L2 cache: 256K
[    0.769067] CPU: L3 cache: 3072K
[    0.769069] CPU 3/0x5 -> Node 0
[    0.769071] mce: CPU supports 9 MCE banks
[    0.769081] CPU3: Thermal monitoring enabled (TM1)
[    0.769084] CPU 3 MCA banks SHD:2 SHD:3 SHD:5 SHD:6
[    0.770144] x86 PAT enabled: cpu 3, old 0x7040600070406, new 0x7010600070106
[    0.771461] CPU3: Intel(R) Core(TM) i5 CPU       M 430  @ 2.27GHz stepping 02
[    0.771471] Skipping synchronization checks as TSC is reliable.
[    0.771493] Brought up 4 CPUs
[    0.771495] Total of 4 processors activated (18089.39 BogoMIPS).
[    0.771557] CPU0 attaching sched-domain:
[    0.771559]  domain 0: span 0-1 level SIBLING
[    0.771561]   groups: 0 1
[    0.771564]   domain 1: span 0-3 level MC
[    0.771566]    groups: 0-1 2-3
[    0.771570] CPU1 attaching sched-domain:
[    0.771571]  domain 0: span 0-1 level SIBLING
[    0.771572]   groups: 1 0
[    0.771575]   domain 1: span 0-3 level MC
[    0.771576]    groups: 0-1 2-3
[    0.771579] CPU2 attaching sched-domain:
[    0.771581]  domain 0: span 2-3 level SIBLING
[    0.771582]   groups: 2 3
[    0.771584]   domain 1: span 0-3 level MC
[    0.771586]    groups: 2-3 0-1
[    0.771589] CPU3 attaching sched-domain:
[    0.771590]  domain 0: span 2-3 level SIBLING
[    0.771592]   groups: 3 2
[    0.771594]   domain 1: span 0-3 level MC
[    0.771596]    groups: 2-3 0-1
[    0.771880] Booting paravirtualized kernel on bare hardware
[    0.772026] regulator: core version 0.5
[    0.772053] Time:  1:45:12  Date: 02/14/10
[    0.772091] NET: Registered protocol family 16
[    0.772188] ACPI FADT declares the system doesn't support PCIe ASPM, so disable it
[    0.772190] ACPI: bus type pci registered
[    0.772262] PCI: MCFG configuration 0: base f0000000 segment 0 buses 0 - 127
[    0.772264] PCI: MCFG area at f0000000 reserved in E820
[    0.775542] PCI: Using MMCONFIG at f0000000 - f7ffffff
[    0.775543] PCI: Using configuration type 1 for base access
[    0.776150] bio: create slab <bio-0> at 0
[    0.777560] ACPI: EC: Enabling special treatment for EC from MSI.
[    0.777562] ACPI: EC: Look up EC in DSDT
[    0.826736] ACPI: BIOS _OSI(Linux) query ignored
[    0.835796] ACPI: EC: non-query interrupt received, switching to interrupt mode
[    0.992930] ACPI: Interpreter enabled
[    0.992933] ACPI: (supports S0 S3 S4 S5)
[    0.992964] ACPI: Using IOAPIC for interrupt routing
[    1.231930] [Firmware Bug]: ACPI: ACPI brightness control misses _BQC function
[    1.409128] ACPI: EC: GPE = 0x17, I/O: command/status = 0x66, data = 0x62
[    1.409130] ACPI: EC: driver started in interrupt mode
[    1.413599] ACPI: Power Resource [FN00] (off)
[    1.421940] ACPI: Power Resource [FN01] (on)
[    1.422854] ACPI: ACPI Dock Station Driver: 1 docks/bays found
[    1.423749] _OSC invalid UUID
[    1.423751] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    1.423839] pci 0000:00:01.0: PME# supported from D0 D3hot D3cold
[    1.423841] pci 0000:00:01.0: PME# disabled
[    1.423863] pci 0000:00:02.0: reg 10 64bit mmio: [0xe0000000-0xe03fffff]
[    1.423868] pci 0000:00:02.0: reg 18 64bit mmio: [0xd0000000-0xdfffffff]
[    1.423871] pci 0000:00:02.0: reg 20 io port: [0x8050-0x8057]
[    1.423956] pci 0000:00:16.0: reg 10 64bit mmio: [0xea506100-0xea50610f]
[    1.424013] pci 0000:00:16.0: PME# supported from D0 D3hot D3cold
[    1.424018] pci 0000:00:16.0: PME# disabled
[    1.424086] pci 0000:00:1a.0: reg 10 32bit mmio: [0xea505c00-0xea505fff]
[    1.424148] pci 0000:00:1a.0: PME# supported from D0 D3hot D3cold
[    1.424152] pci 0000:00:1a.0: PME# disabled
[    1.424205] pci 0000:00:1b.0: reg 10 64bit mmio: [0xea500000-0xea503fff]
[    1.424260] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    1.424265] pci 0000:00:1b.0: PME# disabled
[    1.424344] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    1.424348] pci 0000:00:1c.0: PME# disabled
[    1.424427] pci 0000:00:1c.1: PME# supported from D0 D3hot D3cold
[    1.424432] pci 0000:00:1c.1: PME# disabled
[    1.424511] pci 0000:00:1c.2: PME# supported from D0 D3hot D3cold
[    1.424516] pci 0000:00:1c.2: PME# disabled
[    1.424596] pci 0000:00:1c.3: PME# supported from D0 D3hot D3cold
[    1.424600] pci 0000:00:1c.3: PME# disabled
[    1.424680] pci 0000:00:1c.4: PME# supported from D0 D3hot D3cold
[    1.424684] pci 0000:00:1c.4: PME# disabled
[    1.424750] pci 0000:00:1d.0: reg 10 32bit mmio: [0xea505800-0xea505bff]
[    1.424813] pci 0000:00:1d.0: PME# supported from D0 D3hot D3cold
[    1.424818] pci 0000:00:1d.0: PME# disabled
[    1.425026] pci 0000:00:1f.2: reg 10 io port: [0x8048-0x804f]
[    1.425033] pci 0000:00:1f.2: reg 14 io port: [0x805c-0x805f]
[    1.425040] pci 0000:00:1f.2: reg 18 io port: [0x8040-0x8047]
[    1.425047] pci 0000:00:1f.2: reg 1c io port: [0x8058-0x805b]
[    1.425054] pci 0000:00:1f.2: reg 20 io port: [0x8020-0x803f]
[    1.425062] pci 0000:00:1f.2: reg 24 32bit mmio: [0xea505000-0xea5057ff]
[    1.425104] pci 0000:00:1f.2: PME# supported from D3hot
[    1.425109] pci 0000:00:1f.2: PME# disabled
[    1.425147] pci 0000:00:1f.3: reg 10 64bit mmio: [0xea506000-0xea5060ff]
[    1.425165] pci 0000:00:1f.3: reg 20 io port: [0x8000-0x801f]
[    1.425231] pci 0000:00:1f.6: reg 10 64bit mmio: [0xea504000-0xea504fff]
[    1.425321] pci 0000:01:00.0: reg 10 32bit mmio: [0xc0000000-0xcfffffff]
[    1.425327] pci 0000:01:00.0: reg 14 io port: [0x7000-0x70ff]
[    1.425333] pci 0000:01:00.0: reg 18 32bit mmio: [0xea400000-0xea40ffff]
[    1.425349] pci 0000:01:00.0: reg 30 32bit mmio: [0xfffe0000-0xffffffff]
[    1.425370] pci 0000:01:00.0: supports D1 D2
[    1.425401] pci 0000:01:00.1: reg 10 32bit mmio: [0xea410000-0xea413fff]
[    1.425446] pci 0000:01:00.1: supports D1 D2
[    1.425505] pci 0000:00:01.0: bridge io port: [0x7000-0x7fff]
[    1.425507] pci 0000:00:01.0: bridge 32bit mmio: [0xea400000-0xea4fffff]
[    1.425511] pci 0000:00:01.0: bridge 64bit mmio pref: [0xc0000000-0xcfffffff]
[    1.425564] pci 0000:00:1c.0: bridge io port: [0x6000-0x6fff]
[    1.425568] pci 0000:00:1c.0: bridge 32bit mmio: [0xe9400000-0xea3fffff]
[    1.425576] pci 0000:00:1c.0: bridge 64bit mmio pref: [0xe0400000-0xe13fffff]
[    1.425647] pci 0000:03:00.0: reg 10 64bit mmio: [0xe8400000-0xe840ffff]
[    1.425729] pci 0000:03:00.0: supports D1
[    1.425730] pci 0000:03:00.0: PME# supported from D0 D1 D3hot
[    1.425736] pci 0000:03:00.0: PME# disabled
[    1.425812] pci 0000:00:1c.1: bridge io port: [0x5000-0x5fff]
[    1.425817] pci 0000:00:1c.1: bridge 32bit mmio: [0xe8400000-0xe93fffff]
[    1.425824] pci 0000:00:1c.1: bridge 64bit mmio pref: [0xe1400000-0xe23fffff]
[    1.425985] pci 0000:04:00.0: reg 10 io port: [0x4000-0x40ff]
[    1.426061] pci 0000:04:00.0: reg 18 64bit mmio: [0xe2404000-0xe2404fff]
[    1.426112] pci 0000:04:00.0: reg 20 64bit mmio: [0xe2400000-0xe2403fff]
[    1.426139] pci 0000:04:00.0: reg 30 32bit mmio: [0xfffe0000-0xffffffff]
[    1.426286] pci 0000:04:00.0: supports D1 D2
[    1.426287] pci 0000:04:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    1.426301] pci 0000:04:00.0: PME# disabled
[    1.426452] pci 0000:00:1c.2: bridge io port: [0x4000-0x4fff]
[    1.426456] pci 0000:00:1c.2: bridge 32bit mmio: [0xe7400000-0xe83fffff]
[    1.426463] pci 0000:00:1c.2: bridge 64bit mmio pref: [0xe2400000-0xe33fffff]
[    1.426518] pci 0000:00:1c.3: bridge io port: [0x3000-0x3fff]
[    1.426522] pci 0000:00:1c.3: bridge 32bit mmio: [0xe6400000-0xe73fffff]
[    1.426529] pci 0000:00:1c.3: bridge 64bit mmio pref: [0xe3400000-0xe43fffff]
[    1.426583] pci 0000:00:1c.4: bridge io port: [0x2000-0x2fff]
[    1.426587] pci 0000:00:1c.4: bridge 32bit mmio: [0xe5400000-0xe63fffff]
[    1.426594] pci 0000:00:1c.4: bridge 64bit mmio pref: [0xe4400000-0xe53fffff]
[    1.426650] pci 0000:00:1e.0: transparent bridge
[    1.426702] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    1.426912] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P2._PRT]
[    1.427048] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P1._PRT]
[    1.427238] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP01._PRT]
[    1.427348] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP02._PRT]
[    1.427468] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP03._PRT]
[    1.427575] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP04._PRT]
[    1.427694] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP05._PRT]
[    1.427998] _OSC invalid UUID
[    1.455117] ACPI: PCI Root Bridge [CPBG] (0000:7f)
[    1.455503] ACPI: PCI Interrupt Link [LNKA] (IRQs 1 3 4 *5 6 7 10 12 14 15)
[    1.455661] ACPI: PCI Interrupt Link [LNKB] (IRQs 1 3 4 5 6 7 11 12 14 15) *10
[    1.455817] ACPI: PCI Interrupt Link [LNKC] (IRQs 1 3 4 5 6 7 10 12 14 15) *11
[    1.455974] ACPI: PCI Interrupt Link [LNKD] (IRQs 1 3 4 5 6 7 11 12 14 15) *0, disabled.
[    1.456130] ACPI: PCI Interrupt Link [LNKE] (IRQs 1 3 4 5 6 *7 10 12 14 15)
[    1.456285] ACPI: PCI Interrupt Link [LNKF] (IRQs 1 3 4 5 6 7 11 12 14 15) *10
[    1.456441] ACPI: PCI Interrupt Link [LNKG] (IRQs 1 3 4 5 6 *7 10 12 14 15)
[    1.456597] ACPI: PCI Interrupt Link [LNKH] (IRQs 1 3 4 5 6 7 11 12 14 15) *0, disabled.
[    1.456763] SCSI subsystem initialized
[    1.456832] libata version 3.00 loaded.
[    1.456881] usbcore: registered new interface driver usbfs
[    1.456891] usbcore: registered new interface driver hub
[    1.456909] usbcore: registered new device driver usb
[    1.457020] ACPI: WMI: Mapper loaded
[    1.457021] PCI: Using ACPI for IRQ routing
[    1.477739] Bluetooth: Core ver 2.15
[    1.477776] NET: Registered protocol family 31
[    1.477779] Bluetooth: HCI device and connection manager initialized
[    1.477783] Bluetooth: HCI socket layer initialized
[    1.477785] NetLabel: Initializing
[    1.477788] NetLabel:  domain hash size = 128
[    1.477790] NetLabel:  protocols = UNLABELED CIPSOv4
[    1.477811] NetLabel:  unlabeled traffic allowed by default
[    1.477870] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 24, 25, 26, 27, 28, 0
[    1.477875] hpet0: 8 comparators, 64-bit 14.318180 MHz counter
[    1.487728] hpet: hpet2 irq 24 for MSI
[    1.490069] hpet: hpet3 irq 25 for MSI
[    1.499458] hpet: hpet4 irq 26 for MSI
[    1.500117] hpet: hpet5 irq 27 for MSI
[    1.507689] Switched to high resolution mode on CPU 0
[    1.509427] Switched to high resolution mode on CPU 2
[    1.510018] Switched to high resolution mode on CPU 1
[    1.510085] Switched to high resolution mode on CPU 3
[    1.527650] pnp: PnP ACPI init
[    1.527666] ACPI: bus type pnp registered
[    1.650129]   alloc irq_desc for 23 on node 0
[    1.650131]   alloc kstat_irqs on node 0
[    1.650807] pnp: PnP ACPI: found 14 devices
[    1.650809] ACPI: ACPI bus type pnp unregistered
[    1.650818] system 00:04: iomem range 0xfed00000-0xfed003ff has been reserved
[    1.650823] system 00:06: ioport range 0x680-0x69f has been reserved
[    1.650825] system 00:06: ioport range 0x800-0x80f has been reserved
[    1.650827] system 00:06: ioport range 0x810-0x813 has been reserved
[    1.650829] system 00:06: ioport range 0xffff-0xffff has been reserved
[    1.650831] system 00:06: ioport range 0x400-0x47f has been reserved
[    1.650833] system 00:06: ioport range 0x500-0x57f has been reserved
[    1.650835] system 00:06: ioport range 0x164e-0x164f has been reserved
[    1.650838] system 00:07: ioport range 0x6a0-0x6af has been reserved
[    1.650840] system 00:07: ioport range 0x6b0-0x6ff has been reserved
[    1.650844] system 00:0b: iomem range 0xfed1c000-0xfed1ffff has been reserved
[    1.650846] system 00:0b: iomem range 0xfed10000-0xfed13fff has been reserved
[    1.650849] system 00:0b: iomem range 0xfed18000-0xfed18fff has been reserved
[    1.650851] system 00:0b: iomem range 0xfed19000-0xfed19fff has been reserved
[    1.650853] system 00:0b: iomem range 0xf0000000-0xf1ffffff has been reserved
[    1.650855] system 00:0b: iomem range 0xea600000-0xea600fff has been reserved
[    1.650857] system 00:0b: iomem range 0xfed20000-0xfed3ffff has been reserved
[    1.650859] system 00:0b: iomem range 0xfeb00000-0xfeb03fff has been reserved
[    1.650861] system 00:0b: iomem range 0xfed45000-0xfed8ffff has been reserved
[    1.650863] system 00:0b: iomem range 0xff000000-0xffffffff could not be reserved
[    1.650865] system 00:0b: iomem range 0xfee00000-0xfeefffff could not be reserved
[    1.650867] system 00:0b: iomem range 0xea600000-0xea600fff has been reserved
[    1.655504] AppArmor: AppArmor Filesystem Enabled
[    1.655514] pci 0000:01:00.0: BAR 6: no parent found for of device [0xfffe0000-0xffffffff]
[    1.655518] pci 0000:04:00.0: BAR 6: no parent found for of device [0xfffe0000-0xffffffff]
[    1.655580] pci 0000:00:01.0: PCI bridge, secondary bus 0000:01
[    1.655582] pci 0000:00:01.0:   IO window: 0x7000-0x7fff
[    1.655585] pci 0000:00:01.0:   MEM window: 0xea400000-0xea4fffff
[    1.655588] pci 0000:00:01.0:   PREFETCH window: 0x000000c0000000-0x000000cfffffff
[    1.655591] pci 0000:00:1c.0: PCI bridge, secondary bus 0000:02
[    1.655594] pci 0000:00:1c.0:   IO window: 0x6000-0x6fff
[    1.655600] pci 0000:00:1c.0:   MEM window: 0xe9400000-0xea3fffff
[    1.655605] pci 0000:00:1c.0:   PREFETCH window: 0x000000e0400000-0x000000e13fffff
[    1.655612] pci 0000:00:1c.1: PCI bridge, secondary bus 0000:03
[    1.655615] pci 0000:00:1c.1:   IO window: 0x5000-0x5fff
[    1.655621] pci 0000:00:1c.1:   MEM window: 0xe8400000-0xe93fffff
[    1.655626] pci 0000:00:1c.1:   PREFETCH window: 0x000000e1400000-0x000000e23fffff
[    1.655634] pci 0000:00:1c.2: PCI bridge, secondary bus 0000:04
[    1.655637] pci 0000:00:1c.2:   IO window: 0x4000-0x4fff
[    1.655642] pci 0000:00:1c.2:   MEM window: 0xe7400000-0xe83fffff
[    1.655647] pci 0000:00:1c.2:   PREFETCH window: 0x000000e2400000-0x000000e33fffff
[    1.655654] pci 0000:00:1c.3: PCI bridge, secondary bus 0000:05
[    1.655657] pci 0000:00:1c.3:   IO window: 0x3000-0x3fff
[    1.655663] pci 0000:00:1c.3:   MEM window: 0xe6400000-0xe73fffff
[    1.655667] pci 0000:00:1c.3:   PREFETCH window: 0x000000e3400000-0x000000e43fffff
[    1.655675] pci 0000:00:1c.4: PCI bridge, secondary bus 0000:08
[    1.655678] pci 0000:00:1c.4:   IO window: 0x2000-0x2fff
[    1.655684] pci 0000:00:1c.4:   MEM window: 0xe5400000-0xe63fffff
[    1.655688] pci 0000:00:1c.4:   PREFETCH window: 0x000000e4400000-0x000000e53fffff
[    1.655696] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:09
[    1.655697] pci 0000:00:1e.0:   IO window: disabled
[    1.655702] pci 0000:00:1e.0:   MEM window: disabled
[    1.655707] pci 0000:00:1e.0:   PREFETCH window: disabled
[    1.655715]   alloc irq_desc for 16 on node 0
[    1.655717]   alloc kstat_irqs on node 0
[    1.655721] pci 0000:00:01.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.655724] pci 0000:00:01.0: setting latency timer to 64
[    1.655731] pci 0000:00:1c.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.655736] pci 0000:00:1c.0: setting latency timer to 64
[    1.655743]   alloc irq_desc for 17 on node 0
[    1.655744]   alloc kstat_irqs on node 0
[    1.655747] pci 0000:00:1c.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    1.655752] pci 0000:00:1c.1: setting latency timer to 64
[    1.655759]   alloc irq_desc for 18 on node 0
[    1.655760]   alloc kstat_irqs on node 0
[    1.655763] pci 0000:00:1c.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    1.655768] pci 0000:00:1c.2: setting latency timer to 64
[    1.655775]   alloc irq_desc for 19 on node 0
[    1.655776]   alloc kstat_irqs on node 0
[    1.655779] pci 0000:00:1c.3: PCI INT D -> GSI 19 (level, low) -> IRQ 19
[    1.655783] pci 0000:00:1c.3: setting latency timer to 64
[    1.655791] pci 0000:00:1c.4: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.655795] pci 0000:00:1c.4: setting latency timer to 64
[    1.655802] pci 0000:00:1e.0: setting latency timer to 64
[    1.655806] pci_bus 0000:00: resource 0 io:  [0x00-0xffff]
[    1.655808] pci_bus 0000:00: resource 1 mem: [0x000000-0xffffffffffffffff]
[    1.655810] pci_bus 0000:01: resource 0 io:  [0x7000-0x7fff]
[    1.655812] pci_bus 0000:01: resource 1 mem: [0xea400000-0xea4fffff]
[    1.655813] pci_bus 0000:01: resource 2 pref mem [0xc0000000-0xcfffffff]
[    1.655815] pci_bus 0000:02: resource 0 io:  [0x6000-0x6fff]
[    1.655817] pci_bus 0000:02: resource 1 mem: [0xe9400000-0xea3fffff]
[    1.655819] pci_bus 0000:02: resource 2 pref mem [0xe0400000-0xe13fffff]
[    1.655820] pci_bus 0000:03: resource 0 io:  [0x5000-0x5fff]
[    1.655822] pci_bus 0000:03: resource 1 mem: [0xe8400000-0xe93fffff]
[    1.655824] pci_bus 0000:03: resource 2 pref mem [0xe1400000-0xe23fffff]
[    1.655826] pci_bus 0000:04: resource 0 io:  [0x4000-0x4fff]
[    1.655827] pci_bus 0000:04: resource 1 mem: [0xe7400000-0xe83fffff]
[    1.655829] pci_bus 0000:04: resource 2 pref mem [0xe2400000-0xe33fffff]
[    1.655831] pci_bus 0000:05: resource 0 io:  [0x3000-0x3fff]
[    1.655832] pci_bus 0000:05: resource 1 mem: [0xe6400000-0xe73fffff]
[    1.655834] pci_bus 0000:05: resource 2 pref mem [0xe3400000-0xe43fffff]
[    1.655836] pci_bus 0000:08: resource 0 io:  [0x2000-0x2fff]
[    1.655837] pci_bus 0000:08: resource 1 mem: [0xe5400000-0xe63fffff]
[    1.655839] pci_bus 0000:08: resource 2 pref mem [0xe4400000-0xe53fffff]
[    1.655841] pci_bus 0000:09: resource 3 io:  [0x00-0xffff]
[    1.655843] pci_bus 0000:09: resource 4 mem: [0x000000-0xffffffffffffffff]
[    1.655845] pci_bus 0000:7f: resource 0 io:  [0x00-0xffff]
[    1.655846] pci_bus 0000:7f: resource 1 mem: [0x000000-0xffffffffffffffff]
[    1.655873] NET: Registered protocol family 2
[    1.656012] IP route cache hash table entries: 131072 (order: 8, 1048576 bytes)
[    1.656856] TCP established hash table entries: 524288 (order: 11, 8388608 bytes)
[    1.659353] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    1.659656] TCP: Hash tables configured (established 524288 bind 65536)
[    1.659659] TCP reno registered
[    1.659759] NET: Registered protocol family 1
[    1.659808] Trying to unpack rootfs image as initramfs...
[    1.783464] Freeing initrd memory: 6759k freed
[    1.784927] Simple Boot Flag at 0x44 set to 0x1
[    1.785170] Scanning for low memory corruption every 60 seconds
[    1.785271] audit: initializing netlink socket (disabled)
[    1.785285] type=2000 audit(1266111912.631:1): initialized
[    1.793753] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    1.794802] VFS: Disk quotas dquot_6.5.2
[    1.794844] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    1.795278] fuse init (API version 7.12)
[    1.795336] msgmni has been set to 7526
[    1.795512] alg: No test for stdrng (krng)
[    1.795519] io scheduler noop registered
[    1.795521] io scheduler anticipatory registered
[    1.795522] io scheduler deadline registered (default)
[    1.795555] io scheduler cfq registered
[    1.795566] pci 0000:00:02.0: Boot video device
[    1.828525]   alloc irq_desc for 29 on node 0
[    1.828527]   alloc kstat_irqs on node 0
[    1.828535] pcieport-driver 0000:00:01.0: irq 29 for MSI/MSI-X
[    1.828540] pcieport-driver 0000:00:01.0: setting latency timer to 64
[    1.828663]   alloc irq_desc for 30 on node 0
[    1.828664]   alloc kstat_irqs on node 0
[    1.828673] pcieport-driver 0000:00:1c.0: irq 30 for MSI/MSI-X
[    1.828683] pcieport-driver 0000:00:1c.0: setting latency timer to 64
[    1.828827]   alloc irq_desc for 31 on node 0
[    1.828828]   alloc kstat_irqs on node 0
[    1.828836] pcieport-driver 0000:00:1c.1: irq 31 for MSI/MSI-X
[    1.828846] pcieport-driver 0000:00:1c.1: setting latency timer to 64
[    1.828988]   alloc irq_desc for 32 on node 0
[    1.828989]   alloc kstat_irqs on node 0
[    1.828997] pcieport-driver 0000:00:1c.2: irq 32 for MSI/MSI-X
[    1.829007] pcieport-driver 0000:00:1c.2: setting latency timer to 64
[    1.829149]   alloc irq_desc for 33 on node 0
[    1.829150]   alloc kstat_irqs on node 0
[    1.829158] pcieport-driver 0000:00:1c.3: irq 33 for MSI/MSI-X
[    1.829168] pcieport-driver 0000:00:1c.3: setting latency timer to 64
[    1.829311]   alloc irq_desc for 34 on node 0
[    1.829312]   alloc kstat_irqs on node 0
[    1.829320] pcieport-driver 0000:00:1c.4: irq 34 for MSI/MSI-X
[    1.829329] pcieport-driver 0000:00:1c.4: setting latency timer to 64
[    1.829420] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    1.829596] _OSC invalid UUID
[    1.829730] _OSC invalid UUID
[    1.829860] _OSC invalid UUID
[    1.829988] _OSC invalid UUID
[    1.830116] _OSC invalid UUID
[    1.830258] _OSC invalid UUID
[    1.830387] _OSC invalid UUID
[    1.830516] _OSC invalid UUID
[    1.830644] _OSC invalid UUID
[    1.830771] _OSC invalid UUID
[    1.830799] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    1.966900] ACPI: AC Adapter [AC] (on-line)
[    1.966968] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input0
[    1.966971] ACPI: Power Button [PWRF]
[    1.967008] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1
[    1.967010] ACPI: Power Button [PWRB]
[    1.967038] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input2
[    1.967127] ACPI: Lid Switch [LID0]
[    1.967157] input: Sleep Button as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input3
[    1.967163] ACPI: Sleep Button [SLPB]
[    1.979167] fan PNP0C0B:00: registered as cooling_device0
[    1.979172] ACPI: Fan [FAN0] (off)
[    2.007056] fan PNP0C0B:01: registered as cooling_device1
[    2.007060] ACPI: Fan [FAN1] (on)
[    2.008690] ACPI: SSDT 00000000bb691c18 003A0 (v01  PmRef  Cpu0Ist 00003000 INTL 20051117)
[    2.009315] ACPI: SSDT 00000000bb68fa18 004D1 (v01  PmRef  Cpu0Cst 00003001 INTL 20051117)
[    2.009924] Monitor-Mwait will be used to enter C-1 state
[    2.009944] Monitor-Mwait will be used to enter C-2 state
[    2.009959] Monitor-Mwait will be used to enter C-3 state
[    2.009978] ACPI: CPU0 (power states: C1[C1] C3[C3])
[    2.009991] processor LNXCPU:00: registered as cooling_device2
[    2.009994] ACPI: Processor [CPU0] (supports 8 throttling states)
[    2.010590] ACPI: SSDT 00000000bb690a98 00303 (v01  PmRef    ApIst 00003000 INTL 20051117)
[    2.011171] ACPI: SSDT 00000000bb68ed98 00119 (v01  PmRef    ApCst 00003000 INTL 20051117)
[    2.011929] ACPI: CPU1 (power states: C1[C1] C3[C3])
[    2.011945] processor LNXCPU:01: registered as cooling_device3
[    2.011947] ACPI: Processor [CPU1] (supports 8 throttling states)
[    2.012879] ACPI: CPU2 (power states: C1[C1] C3[C3])
[    2.012893] processor LNXCPU:02: registered as cooling_device4
[    2.012895] ACPI: Processor [CPU2] (supports 8 throttling states)
[    2.013837] ACPI: CPU3 (power states: C1[C1] C3[C3])
[    2.013852] processor LNXCPU:03: registered as cooling_device5
[    2.013855] ACPI: Processor [CPU3] (supports 8 throttling states)
[    2.169290] thermal LNXTHERM:01: registered as thermal_zone0
[    2.169323] ACPI: Thermal Zone [THRM] (67 C)
[    2.170214] Linux agpgart interface v0.103
[    2.170222] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    2.171077] brd: module loaded
[    2.171372] loop: module loaded
[    2.171417] input: Macintosh mouse button emulation as /devices/virtual/input/input4
[    2.171498] ahci 0000:00:1f.2: version 3.0
[    2.171513]   alloc irq_desc for 21 on node 0
[    2.171516]   alloc kstat_irqs on node 0
[    2.171522] ahci 0000:00:1f.2: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[    2.171560]   alloc irq_desc for 35 on node 0
[    2.171561]   alloc kstat_irqs on node 0
[    2.171569] ahci 0000:00:1f.2: irq 35 for MSI/MSI-X
[    2.171601] ahci: SSS flag set, parallel bus scan disabled
[    2.171642] ahci 0000:00:1f.2: AHCI 0001.0300 32 slots 4 ports 3 Gbps 0x13 impl SATA mode
[    2.171645] ahci 0000:00:1f.2: flags: 64bit ncq sntf ilck stag pm led clo pio slum part ems 
[    2.171650] ahci 0000:00:1f.2: setting latency timer to 64
[    2.206341] scsi0 : ahci
[    2.206426] scsi1 : ahci
[    2.206467] scsi2 : ahci
[    2.206506] scsi3 : ahci
[    2.206547] scsi4 : ahci
[    2.206671] ata1: SATA max UDMA/133 abar m2048@0xea505000 port 0xea505100 irq 35
[    2.206675] ata2: SATA max UDMA/133 abar m2048@0xea505000 port 0xea505180 irq 35
[    2.206676] ata3: DUMMY
[    2.206677] ata4: DUMMY
[    2.206680] ata5: SATA max UDMA/133 abar m2048@0xea505000 port 0xea505300 irq 35
[    2.207410] Fixed MDIO Bus: probed
[    2.207434] PPP generic driver version 2.4.2
[    2.207494] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    2.207530] ehci_hcd 0000:00:1a.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    2.207542] ehci_hcd 0000:00:1a.0: setting latency timer to 64
[    2.207546] ehci_hcd 0000:00:1a.0: EHCI Host Controller
[    2.207583] ehci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 1
[    2.211529] ehci_hcd 0000:00:1a.0: debug port 2
[    2.211540] ehci_hcd 0000:00:1a.0: cache line size of 32 is not supported
[    2.211557] ehci_hcd 0000:00:1a.0: irq 16, io mem 0xea505c00
[    2.226239] ehci_hcd 0000:00:1a.0: USB 2.0 started, EHCI 1.00
[    2.226342] usb usb1: configuration #1 chosen from 1 choice
[    2.226364] hub 1-0:1.0: USB hub found
[    2.226369] hub 1-0:1.0: 3 ports detected
[    2.226437]   alloc irq_desc for 20 on node 0
[    2.226438]   alloc kstat_irqs on node 0
[    2.226443] ehci_hcd 0000:00:1d.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    2.226453] ehci_hcd 0000:00:1d.0: setting latency timer to 64
[    2.226456] ehci_hcd 0000:00:1d.0: EHCI Host Controller
[    2.226481] ehci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    2.230429] ehci_hcd 0000:00:1d.0: debug port 2
[    2.230437] ehci_hcd 0000:00:1d.0: cache line size of 32 is not supported
[    2.230450] ehci_hcd 0000:00:1d.0: irq 20, io mem 0xea505800
[    2.246197] ehci_hcd 0000:00:1d.0: USB 2.0 started, EHCI 1.00
[    2.246281] usb usb2: configuration #1 chosen from 1 choice
[    2.246309] hub 2-0:1.0: USB hub found
[    2.246313] hub 2-0:1.0: 3 ports detected
[    2.246360] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    2.246370] uhci_hcd: USB Universal Host Controller Interface driver
[    2.246446] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    2.268801] serio: i8042 KBD port at 0x60,0x64 irq 1
[    2.268806] serio: i8042 AUX port at 0x60,0x64 irq 12
[    2.268864] mice: PS/2 mouse device common for all mice
[    2.268952] rtc_cmos 00:08: RTC can wake from S4
[    2.268980] rtc_cmos 00:08: rtc core: registered rtc_cmos as rtc0
[    2.269013] rtc0: alarms up to one year, y3k, 242 bytes nvram, hpet irqs
[    2.269107] device-mapper: uevent: version 1.0.3
[    2.269177] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: dm-devel@redhat.com
[    2.269248] device-mapper: multipath: version 1.1.0 loaded
[    2.269251] device-mapper: multipath round-robin: version 1.0.0 loaded
[    2.269513] cpuidle: using governor ladder
[    2.271888] cpuidle: using governor menu
[    2.272207] TCP cubic registered
[    2.272298] NET: Registered protocol family 10
[    2.272648] lo: Disabled Privacy Extensions
[    2.272863] NET: Registered protocol family 17
[    2.272876] Bluetooth: L2CAP ver 2.13
[    2.272878] Bluetooth: L2CAP socket layer initialized
[    2.272880] Bluetooth: SCO (Voice Link) ver 0.6
[    2.272881] Bluetooth: SCO socket layer initialized
[    2.272899] Bluetooth: RFCOMM TTY layer initialized
[    2.272901] Bluetooth: RFCOMM socket layer initialized
[    2.272903] Bluetooth: RFCOMM ver 1.11
[    2.274427] PM: Resume from disk failed.
[    2.274437] registered taskstats version 1
[    2.274555]   Magic number: 14:364:761
[    2.274670] rtc_cmos 00:08: setting system clock to 2010-02-14 01:45:14 UTC (1266111914)
[    2.274672] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    2.274674] EDD information not available.
[    2.291135] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input5
[    2.545663] usb 1-1: new high speed USB device using ehci_hcd and address 2
[    2.555654] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    2.557878] ata1.00: ATA-8: WDC WD3200BEKT-60V5T1, 12.01A12, max UDMA/100
[    2.557882] ata1.00: 625142448 sectors, multi 0: LBA48 NCQ (depth 31/32)
[    2.560275] ata1.00: configured for UDMA/100
[    2.647185] ACPI: Battery Slot [BAT0] (battery present)
[    2.647335] scsi 0:0:0:0: Direct-Access     ATA      WDC WD3200BEKT-6 12.0 PQ: 0 ANSI: 5
[    2.647469] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    2.647519] sd 0:0:0:0: [sda] 625142448 512-byte logical blocks: (320 GB/298 GiB)
[    2.647548] sd 0:0:0:0: [sda] Write Protect is off
[    2.647550] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    2.647564] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.647658]  sda: sda1 sda2 sda3 sda4 <
[    2.695823] usb 1-1: configuration #1 chosen from 1 choice
[    2.696106] hub 1-1:1.0: USB hub found
[    2.696296] hub 1-1:1.0: 6 ports detected
[    2.698979]  sda5 sda6 >
[    2.716107] sd 0:0:0:0: [sda] Attached SCSI disk
[    2.815105] usb 2-1: new high speed USB device using ehci_hcd and address 2
[    2.966470] usb 2-1: configuration #1 chosen from 1 choice
[    2.966701] hub 2-1:1.0: USB hub found
[    2.966914] hub 2-1:1.0: 8 ports detected
[    3.044780] usb 1-1.3: new high speed USB device using ehci_hcd and address 3
[    3.169098] usb 1-1.3: configuration #1 chosen from 1 choice
[    3.254381] usb 1-1.5: new full speed USB device using ehci_hcd and address 4
[    3.368360] usb 1-1.5: configuration #1 chosen from 1 choice
[    3.394593] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    3.397947] ata2.00: ATAPI: hp      DVDRAM GT30L, mP04, max UDMA/100, ATAPI AN
[    3.402942] ata2.00: configured for UDMA/100
[    3.426189] scsi 1:0:0:0: CD-ROM            hp       DVDRAM GT30L     mP04 PQ: 0 ANSI: 5
[    3.434243] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[    3.434248] Uniform CD-ROM driver Revision: 3.20
[    3.434335] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    3.434379] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    3.444666] usb 2-1.5: new high speed USB device using ehci_hcd and address 3
[    3.639360] usb 2-1.5: configuration #1 chosen from 1 choice
[    3.793778] ata5: SATA link down (SStatus 0 SControl 300)
[    3.803854] Freeing unused kernel memory: 660k freed
[    3.803982] Write protecting the kernel read-only data: 7572k
[    4.105381] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    4.105423] r8169 0000:04:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    4.105557] r8169 0000:04:00.0: setting latency timer to 64
[    4.105724]   alloc irq_desc for 36 on node 0
[    4.105726]   alloc kstat_irqs on node 0
[    4.105766] r8169 0000:04:00.0: irq 36 for MSI/MSI-X
[    4.106401] eth0: RTL8168d/8111d at 0xffffc90009194000, 00:26:22:bc:3b:c4, XID 283000c0 IRQ 36
[    4.136641] Initializing USB Mass Storage driver...
[    4.136765] scsi5 : SCSI emulation for USB Mass Storage devices
[    4.136843] usb-storage: device found at 3
[    4.136845] usb-storage: waiting for device to settle before scanning
[    4.136871] usbcore: registered new interface driver usb-storage
[    4.136874] USB Mass Storage support registered.
[    4.585181] PM: Starting manual resume from disk
[    4.585185] PM: Resume from partition 8:6
[    4.585186] PM: Checking hibernation image.
[    4.585387] PM: Resume from disk failed.
[    4.595092] EXT4-fs (sda5): barriers enabled
[    4.610114] kjournald2 starting: pid 409, dev sda5:8, commit interval 5 seconds
[    4.610140] EXT4-fs (sda5): delayed allocation enabled
[    4.610145] EXT4-fs: file extents enabled
[    4.617915] EXT4-fs: mballoc enabled
[    4.617928] EXT4-fs (sda5): mounted filesystem with ordered data mode
[    5.193487] type=1505 audit(1266111917.421:2): operation="profile_load" pid=430 name=/sbin/dhclient3
[    5.193526] type=1505 audit(1266111917.421:3): operation="profile_load" pid=430 name=/usr/lib/NetworkManager/nm-dhcp-client.action
[    5.193552] type=1505 audit(1266111917.421:4): operation="profile_load" pid=430 name=/usr/lib/connman/scripts/dhclient-script
[    5.256143] type=1505 audit(1266111917.481:5): operation="profile_load" pid=431 name=/usr/sbin/tcpdump
[    5.891866] Adding 6337600k swap on /dev/sda6.  Priority:-1 extents:1 across:6337600k 
[    6.036218] udev: starting version 147
[    6.201700] EXT4-fs (sda5): internal journal on sda5:8
[    6.672751] lp: driver loaded but no devices found
[    6.682288] Bluetooth: Generic Bluetooth USB driver ver 0.5
[    6.682411] usbcore: registered new interface driver btusb
[    6.710732] agpgart-intel 0000:00:00.0: Intel IGDNG/M Chipset
[    6.711474] agpgart-intel 0000:00:00.0: detected 32764K stolen memory
[    6.720114] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xd0000000
[    6.897368] Linux video capture interface: v2.00
[    6.944425] uvcvideo: Found UVC 1.00 device HP Webcam 101 (064e:c108)
[    6.957728] input: HP Webcam 101 as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.5/2-1.5:1.0/input/input6
[    6.957777] usbcore: registered new interface driver uvcvideo
[    6.957780] USB Video Class driver (v0.1.0)
[    7.026908] [drm] Initialized drm 1.1.0 20060810
[    7.027576] cfg80211: Calling CRDA to update world regulatory domain
[    7.028216] lirc_dev: IR Remote Control driver registered, major 61 
[    7.274070] lis3lv02d: laptop model unknown, using default axes configuration
[    7.274900] lis3lv02d: 1-byte sensor found
[    7.284563] input: ST LIS3LV02DL Accelerometer as /devices/platform/lis3lv02d/input/input7
[    7.284648] Registered led device: hp::hddprotect
[    7.284671] lis3lv02d driver loaded.
[    7.289274] i915 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    7.289278] i915 0000:00:02.0: setting latency timer to 64
[    7.301769]   alloc irq_desc for 37 on node 0
[    7.301772]   alloc kstat_irqs on node 0
[    7.301781] i915 0000:00:02.0: irq 37 for MSI/MSI-X
[    7.390006] [drm] radeon default to kernel modesetting DISABLED.
[    7.390584] pci 0000:01:00.0: power state changed by ACPI to D0
[    7.390592] pci 0000:01:00.0: enabling device (0006 -> 0007)
[    7.390601] pci 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    7.390606] pci 0000:01:00.0: setting latency timer to 64
[    7.390766] [drm] Initialized radeon 1.31.0 20080528 for 0000:01:00.0 on minor 1
[    7.394311] lirc_dev: lirc_register_driver: sample_rate: 0
[    7.394429] enecir: unknown ENE chip detected, assuming KB3926D
[    7.394430] enecir: driver support incomplete
[    7.394432] enecir: chip is 0x3926 - 0x00, 0xd2
[    7.394446] enecir: hardware features:
[    7.394447] enecir: learning and tx off, gpio40_learn off, fan_in off
[    7.394449] enecir: driver has been succesfully loaded
[    7.397300] ip_tables: (C) 2000-2006 Netfilter Core Team
[    7.535605] [drm] fb0: inteldrmfb frame buffer device
[    7.535612] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
[    7.535797]   alloc irq_desc for 22 on node 0
[    7.535799]   alloc kstat_irqs on node 0
[    7.535806] HDA Intel 0000:00:1b.0: PCI INT B -> GSI 22 (level, low) -> IRQ 22
[    7.535844] HDA Intel 0000:00:1b.0: setting latency timer to 64
[    7.547711] cfg80211: World regulatory domain updated:
[    7.547714]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[    7.547717]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[    7.547719]     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[    7.547721]     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[    7.547723]     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[    7.547725]     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[    7.567247] Synaptics Touchpad, model: 1, fw: 7.2, id: 0x1c0b1, caps: 0xd04731/0xa40000
[    7.628504] ath9k 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    7.628524] ath9k 0000:03:00.0: setting latency timer to 64
[    7.646979] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input8
[    7.681459] ath: EEPROM regdomain: 0x6a
[    7.681461] ath: EEPROM indicates we should expect a direct regpair map
[    7.681464] ath: Country alpha2 being used: 00
[    7.681465] ath: Regpair used: 0x6a
[    7.726329] phy0: Selected rate control algorithm 'ath9k_rate_control'
[    7.726813] Registered led device: ath9k-phy0::radio
[    7.726824] Registered led device: ath9k-phy0::assoc
[    7.726836] Registered led device: ath9k-phy0::tx
[    7.726846] Registered led device: ath9k-phy0::rx
[    7.726867] phy0: Atheros AR9285 MAC/BB Rev:2 AR5133 RF Rev:e0: mem=0xffffc90009720000, irq=17
[    7.744872] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:1b.0/input/input9
[    7.765556] input: HDA Intel Mic at Ext Front Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input10
[    7.765625] input: HDA Intel HP Out at Ext Front Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input11
[    7.766433] HDA Intel 0000:01:00.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    7.766495] HDA Intel 0000:01:00.1: setting latency timer to 64
[    7.855567] [drm] LVDS-8: set mode 1366x768 e
[    8.296447] Console: switching to colour frame buffer device 170x48
[    8.412483] type=1505 audit(1266075920.642:6): operation="profile_replace" pid=873 name=/sbin/dhclient3
[    8.412566] type=1505 audit(1266075920.642:7): operation="profile_replace" pid=873 name=/usr/lib/NetworkManager/nm-dhcp-client.action
[    8.412616] type=1505 audit(1266075920.642:8): operation="profile_replace" pid=873 name=/usr/lib/connman/scripts/dhclient-script
[    8.454705] type=1505 audit(1266075920.682:9): operation="profile_replace" pid=877 name=/usr/sbin/tcpdump
```

---

### Post by whatsup_will on 2010-02-14
[B]here is the [hardware spec]("http://h10025.www1.hp.com/ewfrf/wc/product?product=4114813&lc=en&dlc=en&cc=au&form_country=Australia&problem_area=hardware&os=other&troubleshooting=would%20like%20more%20control%20over%20the%20hardware%20in%20the%20bios%20to%20disble%20the%20intergrated%20graphics%20for%20a%20while.&emailsent_flag=yes&year=2010&setting_changes=&rcc=au&mediabt=&tech_skill=Advanced&form_url=https://h10025.www1.hp.com/ewfrf/wc/email?product=4114813&lc=en&cc=au&dlc=en&lang=en&cc=au&month=2&error_message=")


Hardware[/B]
**Product Name**CQ36-113TX**Product Number**WJ791PA**Microprocessor**2.26 GHz Intel Core i5-430M  processor**Microprocessor Cache**3 MB L2 Cache**Memory**2 GB**Memory  Max**Supports up  to 4 GB DDR3 memory**Video Graphics**ATI Mobility Radeon HD 4550  Graphics**Video Memory**512 MB dedicated memory**Display**13.3” Diagonal High-Definition HP  LED BrightView Widescreen Display (1366 x 768)**Hard  Drive**320 GB  (7200 rpm)**Multimedia Drive**LightScribe SuperMulti 8X DVD±RW with Double  Layer Support**Network Card**Integrated 10/100/1000 Gigabit  Ethernet LAN (RJ-45 connector)**Wireless Connectivity**Bluetooth wireless networking**Sound**Altec Lansing speakers**Keyboard**101 key compatible**Pointing  Device**Touch Pad  supporting Multi-Touch gestures. With On/Off button and dedicated  vertical Scroll Up/Down pad**PC Card Slots**1 ExpressCard/34 slot**External  Ports**
[LIST]
[*]5-in-1  integrated Digital Media Reader for Secure Digital cards, MultiMedia  cards, Memory Stick, Memory Stick Pro, or xD Picture cards
[*]3 USB  2.0 (3rd shared with eSATA port)
[*] 1 HDMI
[*] 1 eSATA Combo
[*]  1 VGA
[*] 1 RJ-45
[*] 1 Stereo Headphone out
[*] 1  Microphone in
[*] 1 Consumer IR
[*] AC Adapter
[/LIST]
**Dimensions**32.7 cm (L) x 22.2 cm (W) x 3.18  cm (min H) / 3.53 cm (max H)**Weight**2.11 kg**Power**
[LIST]
[*]90 W AC Power Adapter
[*]6-cell  Lithium-Ion (Li-Ion) battery
[/LIST]
**What's In The Box**Compaq Webcam with Integrated  Microphone

---

