---
title: "Multiple problems with Sandisk SSD &amp; Samsung SSD on Asus M5A97 EVO R2.0 motherboard"
date: 2014-10-19
forum: Hardware
---

### Post by runesvend on 2014-10-19
I have an odd problem that I don't know how to fix.

My PC consists of an Asus M5A97 EVO R2.0 motherboard, to which three HDDs are attached:

Port 1: WDC 2TB HDD
Port 2: Samsung SSD 840 EVO 1TB
Port 4: SanDisk SDSSDH2256G

(picture: [ATTACH=CONFIG]257350[/ATTACH])

When I turn on my PC for the first time of the day, and it tries to boot from the SanDisk SSD, the message I'm usually greeted with is this:

[ATTACH=CONFIG]257351[/ATTACH]

or this:

[ATTACH=CONFIG]257352[/ATTACH]

Sometimes it successfully boots the kernel, but it ends in kernel panic (presumably because the kernel can't read from the SSD in question).

If I let my computer run, with this screen on, for about a minute or two, reboot, and try to boot from the SanDisk SSD *again*, everything works fine. It boots up Ubuntu and there are no problems.

If I try to boot from the Samsung SSD right after turning my computer on, I get the same error as above.

If, however, I:

1. Turn on my computer, wait 1-2 minutes or so
2. Boot up Ubuntu from the SanDisk SSD
3. Wait 15 minutes or so, doing stuff in Ubuntu, running from the SanDisk SSD
4. Reboot PC
5. Boot from Samsung SSD

It works!

It's like my two SSDs need a couple of minutes to wake up. One minute or two for the SanDisk SSD and substantially longer for the Samsung SSD.

I'd like to note that through the entire time that my PC is unable to boot from the Samsung SSD, and I'm in Ubuntu, booted from the SanDisk SSD, I can access the Samsung SSD just fine: mount it, read files, etc. It's just the booting process that doesn't work.

I'm running Ubuntu from the Samsung SSD right now. I just had to wait around 15 minutes after turning my computer on for it to be able to boot from it.

Here's the dmesg from booting from the Samsung SSD:

```
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Initializing cgroup subsys cpuacct
[    0.000000] Linux version 3.13.0-36-generic (buildd@toyol) (gcc version 4.8.2 (Ubuntu 4.8.2-19ubuntu1) ) #63-Ubuntu SMP Wed Sep 3 21:30:07 UTC 2014 (Ubuntu 3.13.0-36.63-generic 3.13.11.6)
[    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-3.13.0-36-generic root=UUID=675f4bd2-1144-410d-9a88-bcb20b920581 ro quiet splash nomdmonddf nomdmonisw nomdmonddf nomdmonisw nomdmonddf nomdmonisw
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   Centaur CentaurHauls
[    0.000000] e820: BIOS-provided physical RAM map:
[    0.000000] BIOS-e820: [mem 0x0000000000000000-0x000000000009e7ff] usable
[    0.000000] BIOS-e820: [mem 0x000000000009e800-0x000000000009ffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000000e0000-0x00000000000fffff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000000100000-0x00000000ba867fff] usable
[    0.000000] BIOS-e820: [mem 0x00000000ba868000-0x00000000bab43fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000bab44000-0x00000000bab53fff] ACPI data
[    0.000000] BIOS-e820: [mem 0x00000000bab54000-0x00000000bb959fff] ACPI NVS
[    0.000000] BIOS-e820: [mem 0x00000000bb95a000-0x00000000bca36fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000bca37000-0x00000000bca37fff] usable
[    0.000000] BIOS-e820: [mem 0x00000000bca38000-0x00000000bcc3dfff] ACPI NVS
[    0.000000] BIOS-e820: [mem 0x00000000bcc3e000-0x00000000bd082fff] usable
[    0.000000] BIOS-e820: [mem 0x00000000bd083000-0x00000000bd7f3fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000bd7f4000-0x00000000bd7fffff] usable
[    0.000000] BIOS-e820: [mem 0x00000000fec00000-0x00000000fec00fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fec10000-0x00000000fec10fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fec20000-0x00000000fec20fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fed00000-0x00000000fed00fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fed61000-0x00000000fed70fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fed80000-0x00000000fed8ffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fef00000-0x00000000ffffffff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000100001000-0x000000043effffff] usable
[    0.000000] NX (Execute Disable) protection: active
[    0.000000] SMBIOS 2.7 present.
[    0.000000] DMI: To be filled by O.E.M. To be filled by O.E.M./M5A97 EVO R2.0, BIOS 2201 11/25/2013
[    0.000000] e820: update [mem 0x00000000-0x00000fff] usable ==> reserved
[    0.000000] e820: remove [mem 0x000a0000-0x000fffff] usable
[    0.000000] No AGP bridge found
[    0.000000] e820: last_pfn = 0x43f000 max_arch_pfn = 0x400000000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF write-through
[    0.000000]   C0000-CFFFF write-protect
[    0.000000]   D0000-EBFFF uncachable
[    0.000000]   EC000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000000 mask FFFF80000000 write-back
[    0.000000]   1 base 000080000000 mask FFFFC0000000 write-back
[    0.000000]   2 base 0000BD800000 mask FFFFFF800000 uncachable
[    0.000000]   3 base 0000BE000000 mask FFFFFE000000 uncachable
[    0.000000]   4 disabled
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] TOM2: 000000043f000000 aka 17392M
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] original variable MTRRs
[    0.000000] reg 0, base: 0GB, range: 2GB, type WB
[    0.000000] reg 1, base: 2GB, range: 1GB, type WB
[    0.000000] reg 2, base: 3032MB, range: 8MB, type UC
[    0.000000] reg 3, base: 3040MB, range: 32MB, type UC
[    0.000000] total RAM covered: 3032M
[    0.000000] Found optimal setting for mtrr clean up
[    0.000000]  gran_size: 64K 	chunk_size: 64M 	num_reg: 4  	lose cover RAM: 0G
[    0.000000] New variable MTRRs
[    0.000000] reg 0, base: 0GB, range: 2GB, type WB
[    0.000000] reg 1, base: 2GB, range: 1GB, type WB
[    0.000000] reg 2, base: 3032MB, range: 8MB, type UC
[    0.000000] reg 3, base: 3040MB, range: 32MB, type UC
[    0.000000] e820: update [mem 0xbd800000-0xffffffff] usable ==> reserved
[    0.000000] e820: last_pfn = 0xbd800 max_arch_pfn = 0x400000000
[    0.000000] Scanning 1 areas for low memory corruption
[    0.000000] Base memory trampoline at [ffff880000098000] 98000 size 24576
[    0.000000] Using GB pages for direct mapping
[    0.000000] init_memory_mapping: [mem 0x00000000-0x000fffff]
[    0.000000]  [mem 0x00000000-0x000fffff] page 4k
[    0.000000] BRK [0x01fdf000, 0x01fdffff] PGTABLE
[    0.000000] BRK [0x01fe0000, 0x01fe0fff] PGTABLE
[    0.000000] BRK [0x01fe1000, 0x01fe1fff] PGTABLE
[    0.000000] init_memory_mapping: [mem 0x43ee00000-0x43effffff]
[    0.000000]  [mem 0x43ee00000-0x43effffff] page 2M
[    0.000000] BRK [0x01fe2000, 0x01fe2fff] PGTABLE
[    0.000000] init_memory_mapping: [mem 0x43c000000-0x43edfffff]
[    0.000000]  [mem 0x43c000000-0x43edfffff] page 2M
[    0.000000] init_memory_mapping: [mem 0x400000000-0x43bffffff]
[    0.000000]  [mem 0x400000000-0x43bffffff] page 2M
[    0.000000] init_memory_mapping: [mem 0x00100000-0xba867fff]
[    0.000000]  [mem 0x00100000-0x001fffff] page 4k
[    0.000000]  [mem 0x00200000-0x3fffffff] page 2M
[    0.000000]  [mem 0x40000000-0x7fffffff] page 1G
[    0.000000]  [mem 0x80000000-0xba7fffff] page 2M
[    0.000000]  [mem 0xba800000-0xba867fff] page 4k
[    0.000000] init_memory_mapping: [mem 0xbca37000-0xbca37fff]
[    0.000000]  [mem 0xbca37000-0xbca37fff] page 4k
[    0.000000] BRK [0x01fe3000, 0x01fe3fff] PGTABLE
[    0.000000] init_memory_mapping: [mem 0xbcc3e000-0xbd082fff]
[    0.000000]  [mem 0xbcc3e000-0xbcdfffff] page 4k
[    0.000000]  [mem 0xbce00000-0xbcffffff] page 2M
[    0.000000]  [mem 0xbd000000-0xbd082fff] page 4k
[    0.000000] BRK [0x01fe4000, 0x01fe4fff] PGTABLE
[    0.000000] init_memory_mapping: [mem 0xbd7f4000-0xbd7fffff]
[    0.000000]  [mem 0xbd7f4000-0xbd7fffff] page 4k
[    0.000000] init_memory_mapping: [mem 0x100001000-0x3ffffffff]
[    0.000000]  [mem 0x100001000-0x1001fffff] page 4k
[    0.000000]  [mem 0x100200000-0x13fffffff] page 2M
[    0.000000]  [mem 0x140000000-0x3ffffffff] page 1G
[    0.000000] RAMDISK: [mem 0x34a70000-0x3652ffff]
[    0.000000] ACPI: RSDP 00000000000f0490 000024 (v02 ALASKA)
[    0.000000] ACPI: XSDT 00000000bab4b070 000054 (v01 ALASKA    A M I 01072009 AMI  00010013)
[    0.000000] ACPI: FACP 00000000bab52260 00010C (v05 ALASKA    A M I 01072009 AMI  00010013)
[    0.000000] ACPI BIOS Warning (bug): Optional FADT field Pm2ControlBlock has zero address or length: 0x0000000000000000/0x1 (20131115/tbfadt-603)
[    0.000000] ACPI: DSDT 00000000bab4b158 007101 (v02 ALASKA    A M I 00000000 INTL 20051117)
[    0.000000] ACPI: FACS 00000000bb954f80 000040
[    0.000000] ACPI: APIC 00000000bab52370 00009E (v03 ALASKA    A M I 01072009 AMI  00010013)
[    0.000000] ACPI: FPDT 00000000bab52410 000044 (v01 ALASKA    A M I 01072009 AMI  00010013)
[    0.000000] ACPI: MCFG 00000000bab52458 00003C (v01 ALASKA    A M I 01072009 MSFT 00010013)
[    0.000000] ACPI: HPET 00000000bab52498 000038 (v01 ALASKA    A M I 01072009 AMI  00000005)
[    0.000000] ACPI: SSDT 00000000bab52528 001714 (v01 AMD    POWERNOW 00000001 AMD  00000001)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at [mem 0x0000000000000000-0x000000043effffff]
[    0.000000] Initmem setup node 0 [mem 0x00000000-0x43effffff]
[    0.000000]   NODE_DATA [mem 0x43eff5000-0x43eff9fff]
[    0.000000]  [ffffea0000000000-ffffea0010ffffff] PMD -> [ffff88042e600000-ffff88043e5fffff] on node 0
[    0.000000] Zone ranges:
[    0.000000]   DMA      [mem 0x00001000-0x00ffffff]
[    0.000000]   DMA32    [mem 0x01000000-0xffffffff]
[    0.000000]   Normal   [mem 0x100000000-0x43effffff]
[    0.000000] Movable zone start for each node
[    0.000000] Early memory node ranges
[    0.000000]   node   0: [mem 0x00001000-0x0009dfff]
[    0.000000]   node   0: [mem 0x00100000-0xba867fff]
[    0.000000]   node   0: [mem 0xbca37000-0xbca37fff]
[    0.000000]   node   0: [mem 0xbcc3e000-0xbd082fff]
[    0.000000]   node   0: [mem 0xbd7f4000-0xbd7fffff]
[    0.000000]   node   0: [mem 0x100001000-0x43effffff]
[    0.000000] On node 0 totalpages: 4168790
[    0.000000]   DMA zone: 64 pages used for memmap
[    0.000000]   DMA zone: 21 pages reserved
[    0.000000]   DMA zone: 3997 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 11891 pages used for memmap
[    0.000000]   DMA32 zone: 761018 pages, LIFO batch:31
[    0.000000]   Normal zone: 53184 pages used for memmap
[    0.000000]   Normal zone: 3403775 pages, LIFO batch:31
[    0.000000] ACPI: PM-Timer IO Port: 0x808
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x10] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x11] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x12] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x13] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x05] lapic_id[0x14] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x06] lapic_id[0x15] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x07] lapic_id[0x16] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x08] lapic_id[0x17] enabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0xff] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x09] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 9, version 33, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: IOAPIC (id[0x0a] address[0xfec20000] gsi_base[24])
[    0.000000] IOAPIC[1]: apic_id 10, version 33, address 0xfec20000, GSI 24-55
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 low level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x43538210 base: 0xfed00000
[    0.000000] smpboot: Allowing 8 CPUs, 0 hotplug CPUs
[    0.000000] nr_irqs_gsi: 72
[    0.000000] PM: Registered nosave memory: [mem 0x0009e000-0x0009efff]
[    0.000000] PM: Registered nosave memory: [mem 0x0009f000-0x0009ffff]
[    0.000000] PM: Registered nosave memory: [mem 0x000a0000-0x000dffff]
[    0.000000] PM: Registered nosave memory: [mem 0x000e0000-0x000fffff]
[    0.000000] PM: Registered nosave memory: [mem 0xba868000-0xbab43fff]
[    0.000000] PM: Registered nosave memory: [mem 0xbab44000-0xbab53fff]
[    0.000000] PM: Registered nosave memory: [mem 0xbab54000-0xbb959fff]
[    0.000000] PM: Registered nosave memory: [mem 0xbb95a000-0xbca36fff]
[    0.000000] PM: Registered nosave memory: [mem 0xbca38000-0xbcc3dfff]
[    0.000000] PM: Registered nosave memory: [mem 0xbd083000-0xbd7f3fff]
[    0.000000] PM: Registered nosave memory: [mem 0xbd800000-0xfebfffff]
[    0.000000] PM: Registered nosave memory: [mem 0xfec00000-0xfec00fff]
[    0.000000] PM: Registered nosave memory: [mem 0xfec01000-0xfec0ffff]
[    0.000000] PM: Registered nosave memory: [mem 0xfec10000-0xfec10fff]
[    0.000000] PM: Registered nosave memory: [mem 0xfec11000-0xfec1ffff]
[    0.000000] PM: Registered nosave memory: [mem 0xfec20000-0xfec20fff]
[    0.000000] PM: Registered nosave memory: [mem 0xfec21000-0xfecfffff]
[    0.000000] PM: Registered nosave memory: [mem 0xfed00000-0xfed00fff]
[    0.000000] PM: Registered nosave memory: [mem 0xfed01000-0xfed60fff]
[    0.000000] PM: Registered nosave memory: [mem 0xfed61000-0xfed70fff]
[    0.000000] PM: Registered nosave memory: [mem 0xfed71000-0xfed7ffff]
[    0.000000] PM: Registered nosave memory: [mem 0xfed80000-0xfed8ffff]
[    0.000000] PM: Registered nosave memory: [mem 0xfed90000-0xfeefffff]
[    0.000000] PM: Registered nosave memory: [mem 0xfef00000-0xffffffff]
[    0.000000] PM: Registered nosave memory: [mem 0x100000000-0x100000fff]
[    0.000000] e820: [mem 0xbd800000-0xfebfffff] available for PCI devices
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] setup_percpu: NR_CPUS:256 nr_cpumask_bits:256 nr_cpu_ids:8 nr_node_ids:1
[    0.000000] PERCPU: Embedded 29 pages/cpu @ffff88043ec00000 s86336 r8192 d24256 u262144
[    0.000000] pcpu-alloc: s86336 r8192 d24256 u262144 alloc=1*2097152
[    0.000000] pcpu-alloc: [0] 0 1 2 3 4 5 6 7 
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 4103630
[    0.000000] Policy zone: Normal
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.13.0-36-generic root=UUID=675f4bd2-1144-410d-9a88-bcb20b920581 ro quiet splash nomdmonddf nomdmonisw nomdmonddf nomdmonisw nomdmonddf nomdmonisw
[    0.000000] PID hash table entries: 4096 (order: 3, 32768 bytes)
[    0.000000] xsave: enabled xstate_bv 0x7, cntxt size 0x340
[    0.000000] Checking aperture...
[    0.000000] No AGP bridge found
[    0.000000] Node 0: aperture @ 0 size 32 MB
[    0.000000] Your BIOS doesn't leave a aperture memory hole
[    0.000000] Please enable the IOMMU option in the BIOS setup
[    0.000000] This costs you 64 MB of RAM
[    0.000000] Mapping aperture over 65536 KB of RAM @ b0000000
[    0.000000] PM: Registered nosave memory: [mem 0xb0000000-0xb3ffffff]
[    0.000000] Memory: 16236448K/16675160K available (7373K kernel code, 1144K rwdata, 3404K rodata, 1336K init, 1440K bss, 438712K reserved)
[    0.000000] SLUB: HWalign=64, Order=0-3, MinObjects=0, CPUs=8, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000] 	RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000] 	RCU restricting CPUs from NR_CPUS=256 to nr_cpu_ids=8.
[    0.000000] 	Offload RCU callbacks from all CPUs
[    0.000000] 	Offload RCU callbacks from CPUs: 0-7.
[    0.000000] NR_IRQS:16640 nr_irqs:1288 16
[    0.000000] spurious 8259A interrupt: IRQ7.
[    0.000000] Console: colour VGA+ 80x25
[    0.000000] console [tty0] enabled
[    0.000000] allocated 67108864 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] hpet clockevent registered
[    0.000000] tsc: Fast TSC calibration using PIT
[    0.004000] tsc: Detected 3511.476 MHz processor
[    0.000003] Calibrating delay loop (skipped), value calculated using timer frequency.. 7022.95 BogoMIPS (lpj=14045904)
[    0.000006] pid_max: default: 32768 minimum: 301
[    0.000027] Security Framework initialized
[    0.000045] AppArmor: AppArmor initialized
[    0.000046] Yama: becoming mindful.
[    0.001179] Dentry cache hash table entries: 2097152 (order: 12, 16777216 bytes)
[    0.005149] Inode-cache hash table entries: 1048576 (order: 11, 8388608 bytes)
[    0.006917] Mount-cache hash table entries: 32768 (order: 6, 262144 bytes)
[    0.006937] Mountpoint-cache hash table entries: 32768 (order: 6, 262144 bytes)
[    0.007194] Initializing cgroup subsys memory
[    0.007199] Initializing cgroup subsys devices
[    0.007201] Initializing cgroup subsys freezer
[    0.007203] Initializing cgroup subsys blkio
[    0.007204] Initializing cgroup subsys perf_event
[    0.007206] Initializing cgroup subsys hugetlb
[    0.007223] tseg: 00bd800000
[    0.007225] CPU: Physical Processor ID: 0
[    0.007226] CPU: Processor Core ID: 0
[    0.007227] mce: CPU supports 7 MCE banks
[    0.007233] LVT offset 1 assigned for vector 0xf9
[    0.007238] Last level iTLB entries: 4KB 512, 2MB 1024, 4MB 512
[    0.007238] Last level dTLB entries: 4KB 1024, 2MB 1024, 4MB 512
[    0.007238] tlb_flushall_shift: 5
[    0.007322] Freeing SMP alternatives memory: 32K (ffffffff81e6d000 - ffffffff81e75000)
[    0.008071] ACPI: Core revision 20131115
[    0.010380] ACPI: All ACPI Tables successfully acquired
[    0.216165] ftrace: allocating 28537 entries in 112 pages
[    0.225361] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.265099] smpboot: CPU0: AMD FX(tm)-8320 Eight-Core Processor (fam: 15, model: 02, stepping: 00)
[    0.370261] Performance Events: Fam15h core perfctr, AMD PMU driver.
[    0.370265] ... version:                0
[    0.370267] ... bit width:              48
[    0.370267] ... generic registers:      6
[    0.370268] ... value mask:             0000ffffffffffff
[    0.370270] ... max period:             00007fffffffffff
[    0.370270] ... fixed-purpose events:   0
[    0.370271] ... event mask:             000000000000003f
[    0.371795] NMI watchdog: enabled on all CPUs, permanently consumes one hw-PMU counter.
[    0.371863] x86: Booting SMP configuration:
[    0.371865] .... node  #0, CPUs:      #1 #2 #3 #4 #5 #6 #7
[    0.464111] x86: Booted up 1 node, 8 CPUs
[    0.464114] smpboot: Total of 8 processors activated (56183.61 BogoMIPS)
[    0.474428] devtmpfs: initialized
[    0.477903] EVM: security.selinux
[    0.477905] EVM: security.SMACK64
[    0.477906] EVM: security.ima
[    0.477907] EVM: security.capability
[    0.477992] PM: Registering ACPI NVS region [mem 0xbab54000-0xbb959fff] (14704640 bytes)
[    0.478219] PM: Registering ACPI NVS region [mem 0xbca38000-0xbcc3dfff] (2121728 bytes)
[    0.479068] pinctrl core: initialized pinctrl subsystem
[    0.479124] regulator-dummy: no parameters
[    0.479148] RTC time: 10:53:12, date: 10/19/14
[    0.479180] NET: Registered protocol family 16
[    0.479305] cpuidle: using governor ladder
[    0.479307] cpuidle: using governor menu
[    0.479392] ACPI: bus type PCI registered
[    0.479393] acpiphp: ACPI Hot Plug PCI Controller Driver version: 0.5
[    0.479446] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xe0000000-0xefffffff] (base 0xe0000000)
[    0.479448] PCI: not using MMCONFIG
[    0.479449] PCI: Using configuration type 1 for base access
[    0.479450] PCI: Using configuration type 1 for extended access
[    0.480662] bio: create slab <bio-0> at 0
[    0.480848] ACPI: Added _OSI(Module Device)
[    0.480849] ACPI: Added _OSI(Processor Device)
[    0.480850] ACPI: Added _OSI(3.0 _SCP Extensions)
[    0.480852] ACPI: Added _OSI(Processor Aggregator Device)
[    0.482846] ACPI: Executed 2 blocks of module-level executable AML code
[    0.486953] ACPI: Interpreter enabled
[    0.486958] ACPI Exception: AE_NOT_FOUND, While evaluating Sleep State [\_S1_] (20131115/hwxface-580)
[    0.486962] ACPI Exception: AE_NOT_FOUND, While evaluating Sleep State [\_S2_] (20131115/hwxface-580)
[    0.486976] ACPI: (supports S0 S3 S4 S5)
[    0.486978] ACPI: Using IOAPIC for interrupt routing
[    0.487119] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xe0000000-0xefffffff] (base 0xe0000000)
[    0.487158] PCI: MMCONFIG at [mem 0xe0000000-0xefffffff] reserved in ACPI motherboard resources
[    0.502127] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[    0.502254] ACPI: No dock devices found.
[    0.510154] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
[    0.510159] acpi PNP0A03:00: _OSC: OS supports [ExtendedConfig ASPM ClockPM Segments MSI]
[    0.510164] acpi PNP0A03:00: _OSC failed (AE_NOT_FOUND); disabling ASPM
[    0.510668] PCI host bridge to bus 0000:00
[    0.510670] pci_bus 0000:00: root bus resource [bus 00-ff]
[    0.510672] pci_bus 0000:00: root bus resource [io  0x0000-0x03af]
[    0.510674] pci_bus 0000:00: root bus resource [io  0x03e0-0x0cf7]
[    0.510676] pci_bus 0000:00: root bus resource [io  0x03b0-0x03df]
[    0.510680] pci_bus 0000:00: root bus resource [io  0x0d00-0xffff]
[    0.510682] pci_bus 0000:00: root bus resource [mem 0x000a0000-0x000bffff]
[    0.510684] pci_bus 0000:00: root bus resource [mem 0x000c0000-0x000dffff]
[    0.510685] pci_bus 0000:00: root bus resource [mem 0xc0000000-0xffffffff]
[    0.510700] pci 0000:00:00.0: [1002:5a14] type 00 class 0x060000
[    0.510855] pci 0000:00:02.0: [1002:5a16] type 01 class 0x060400
[    0.510906] pci 0000:00:02.0: PME# supported from D0 D3hot D3cold
[    0.510968] pci 0000:00:02.0: System wakeup disabled by ACPI
[    0.510997] pci 0000:00:04.0: [1002:5a18] type 01 class 0x060400
[    0.511046] pci 0000:00:04.0: PME# supported from D0 D3hot D3cold
[    0.511106] pci 0000:00:04.0: System wakeup disabled by ACPI
[    0.511134] pci 0000:00:05.0: [1002:5a19] type 01 class 0x060400
[    0.511183] pci 0000:00:05.0: PME# supported from D0 D3hot D3cold
[    0.511243] pci 0000:00:05.0: System wakeup disabled by ACPI
[    0.511271] pci 0000:00:06.0: [1002:5a1a] type 01 class 0x060400
[    0.511348] pci 0000:00:06.0: PME# supported from D0 D3hot D3cold
[    0.511410] pci 0000:00:06.0: System wakeup disabled by ACPI
[    0.511438] pci 0000:00:07.0: [1002:5a1b] type 01 class 0x060400
[    0.511487] pci 0000:00:07.0: PME# supported from D0 D3hot D3cold
[    0.511549] pci 0000:00:07.0: System wakeup disabled by ACPI
[    0.511590] pci 0000:00:11.0: [1002:4391] type 00 class 0x010601
[    0.511608] pci 0000:00:11.0: reg 0x10: [io  0xf040-0xf047]
[    0.511617] pci 0000:00:11.0: reg 0x14: [io  0xf030-0xf033]
[    0.511626] pci 0000:00:11.0: reg 0x18: [io  0xf020-0xf027]
[    0.511635] pci 0000:00:11.0: reg 0x1c: [io  0xf010-0xf013]
[    0.511644] pci 0000:00:11.0: reg 0x20: [io  0xf000-0xf00f]
[    0.511654] pci 0000:00:11.0: reg 0x24: [mem 0xfeb0b000-0xfeb0b3ff]
[    0.511772] pci 0000:00:12.0: [1002:4397] type 00 class 0x0c0310
[    0.511785] pci 0000:00:12.0: reg 0x10: [mem 0xfeb0a000-0xfeb0afff]
[    0.511891] pci 0000:00:12.0: System wakeup disabled by ACPI
[    0.511923] pci 0000:00:12.2: [1002:4396] type 00 class 0x0c0320
[    0.511941] pci 0000:00:12.2: reg 0x10: [mem 0xfeb09000-0xfeb090ff]
[    0.512020] pci 0000:00:12.2: supports D1 D2
[    0.512022] pci 0000:00:12.2: PME# supported from D0 D1 D2 D3hot
[    0.512082] pci 0000:00:12.2: System wakeup disabled by ACPI
[    0.512113] pci 0000:00:13.0: [1002:4397] type 00 class 0x0c0310
[    0.512126] pci 0000:00:13.0: reg 0x10: [mem 0xfeb08000-0xfeb08fff]
[    0.512232] pci 0000:00:13.0: System wakeup disabled by ACPI
[    0.512265] pci 0000:00:13.2: [1002:4396] type 00 class 0x0c0320
[    0.512283] pci 0000:00:13.2: reg 0x10: [mem 0xfeb07000-0xfeb070ff]
[    0.512362] pci 0000:00:13.2: supports D1 D2
[    0.512363] pci 0000:00:13.2: PME# supported from D0 D1 D2 D3hot
[    0.512423] pci 0000:00:13.2: System wakeup disabled by ACPI
[    0.512455] pci 0000:00:14.0: [1002:4385] type 00 class 0x0c0500
[    0.512626] pci 0000:00:14.2: [1002:4383] type 00 class 0x040300
[    0.512646] pci 0000:00:14.2: reg 0x10: [mem 0xfeb00000-0xfeb03fff 64bit]
[    0.512710] pci 0000:00:14.2: PME# supported from D0 D3hot D3cold
[    0.512767] pci 0000:00:14.2: System wakeup disabled by ACPI
[    0.512793] pci 0000:00:14.3: [1002:439d] type 00 class 0x060100
[    0.512928] pci 0000:00:14.4: [1002:4384] type 01 class 0x060401
[    0.513012] pci 0000:00:14.4: System wakeup disabled by ACPI
[    0.513037] pci 0000:00:14.5: [1002:4399] type 00 class 0x0c0310
[    0.513050] pci 0000:00:14.5: reg 0x10: [mem 0xfeb06000-0xfeb06fff]
[    0.513157] pci 0000:00:14.5: System wakeup disabled by ACPI
[    0.513185] pci 0000:00:16.0: [1002:4397] type 00 class 0x0c0310
[    0.513198] pci 0000:00:16.0: reg 0x10: [mem 0xfeb05000-0xfeb05fff]
[    0.513303] pci 0000:00:16.0: System wakeup disabled by ACPI
[    0.513336] pci 0000:00:16.2: [1002:4396] type 00 class 0x0c0320
[    0.513354] pci 0000:00:16.2: reg 0x10: [mem 0xfeb04000-0xfeb040ff]
[    0.513433] pci 0000:00:16.2: supports D1 D2
[    0.513434] pci 0000:00:16.2: PME# supported from D0 D1 D2 D3hot
[    0.513494] pci 0000:00:16.2: System wakeup disabled by ACPI
[    0.513525] pci 0000:00:18.0: [1022:1600] type 00 class 0x060000
[    0.513622] pci 0000:00:18.1: [1022:1601] type 00 class 0x060000
[    0.513707] pci 0000:00:18.2: [1022:1602] type 00 class 0x060000
[    0.513793] pci 0000:00:18.3: [1022:1603] type 00 class 0x060000
[    0.513884] pci 0000:00:18.4: [1022:1604] type 00 class 0x060000
[    0.513968] pci 0000:00:18.5: [1022:1605] type 00 class 0x060000
[    0.514270] pci 0000:01:00.0: [1002:68b8] type 00 class 0x030000
[    0.514286] pci 0000:01:00.0: reg 0x10: [mem 0xc0000000-0xcfffffff 64bit pref]
[    0.514297] pci 0000:01:00.0: reg 0x18: [mem 0xfea20000-0xfea3ffff 64bit]
[    0.514306] pci 0000:01:00.0: reg 0x20: [io  0xe000-0xe0ff]
[    0.514320] pci 0000:01:00.0: reg 0x30: [mem 0xfea00000-0xfea1ffff pref]
[    0.514356] pci 0000:01:00.0: supports D1 D2
[    0.514399] pci 0000:01:00.1: [1002:aa58] type 00 class 0x040300
[    0.514414] pci 0000:01:00.1: reg 0x10: [mem 0xfea40000-0xfea43fff 64bit]
[    0.514483] pci 0000:01:00.1: supports D1 D2
[    0.522510] pci 0000:00:02.0: PCI bridge to [bus 01]
[    0.522515] pci 0000:00:02.0:   bridge window [io  0xe000-0xefff]
[    0.522518] pci 0000:00:02.0:   bridge window [mem 0xfea00000-0xfeafffff]
[    0.522522] pci 0000:00:02.0:   bridge window [mem 0xc0000000-0xcfffffff 64bit pref]
[    0.522745] pci 0000:02:00.0: [10ec:8168] type 00 class 0x020000
[    0.522760] pci 0000:02:00.0: reg 0x10: [io  0xd000-0xd0ff]
[    0.522783] pci 0000:02:00.0: reg 0x18: [mem 0xd0004000-0xd0004fff 64bit pref]
[    0.522798] pci 0000:02:00.0: reg 0x20: [mem 0xd0000000-0xd0003fff 64bit pref]
[    0.522862] pci 0000:02:00.0: supports D1 D2
[    0.522864] pci 0000:02:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.530513] pci 0000:00:04.0: PCI bridge to [bus 02]
[    0.530518] pci 0000:00:04.0:   bridge window [io  0xd000-0xdfff]
[    0.530523] pci 0000:00:04.0:   bridge window [mem 0xd0000000-0xd00fffff 64bit pref]
[    0.530586] pci 0000:03:00.0: [1b21:1042] type 00 class 0x0c0330
[    0.530607] pci 0000:03:00.0: reg 0x10: [mem 0xfe900000-0xfe907fff 64bit]
[    0.530709] pci 0000:03:00.0: PME# supported from D3hot D3cold
[    0.538523] pci 0000:00:05.0: PCI bridge to [bus 03]
[    0.538529] pci 0000:00:05.0:   bridge window [mem 0xfe900000-0xfe9fffff]
[    0.538589] pci 0000:04:00.0: [1b21:0612] type 00 class 0x010601
[    0.538602] pci 0000:04:00.0: reg 0x10: [io  0xc050-0xc057]
[    0.538611] pci 0000:04:00.0: reg 0x14: [io  0xc040-0xc043]
[    0.538620] pci 0000:04:00.0: reg 0x18: [io  0xc030-0xc037]
[    0.538629] pci 0000:04:00.0: reg 0x1c: [io  0xc020-0xc023]
[    0.538638] pci 0000:04:00.0: reg 0x20: [io  0xc000-0xc01f]
[    0.538648] pci 0000:04:00.0: reg 0x24: [mem 0xfe800000-0xfe8001ff]
[    0.546533] pci 0000:00:06.0: PCI bridge to [bus 04]
[    0.546538] pci 0000:00:06.0:   bridge window [io  0xc000-0xcfff]
[    0.546541] pci 0000:00:06.0:   bridge window [mem 0xfe800000-0xfe8fffff]
[    0.546635] pci 0000:05:00.0: [1b21:1042] type 00 class 0x0c0330
[    0.546655] pci 0000:05:00.0: reg 0x10: [mem 0xfe700000-0xfe707fff 64bit]
[    0.546757] pci 0000:05:00.0: PME# supported from D3hot D3cold
[    0.554549] pci 0000:00:07.0: PCI bridge to [bus 05]
[    0.554554] pci 0000:00:07.0:   bridge window [mem 0xfe700000-0xfe7fffff]
[    0.554605] pci 0000:06:07.0: [1106:3044] type 00 class 0x0c0010
[    0.554627] pci 0000:06:07.0: reg 0x10: [mem 0xfe600000-0xfe6007ff]
[    0.554639] pci 0000:06:07.0: reg 0x14: [io  0xb000-0xb07f]
[    0.554729] pci 0000:06:07.0: supports D2
[    0.554730] pci 0000:06:07.0: PME# supported from D2 D3hot D3cold
[    0.554797] pci 0000:00:14.4: PCI bridge to [bus 06] (subtractive decode)
[    0.554801] pci 0000:00:14.4:   bridge window [io  0xb000-0xbfff]
[    0.554804] pci 0000:00:14.4:   bridge window [mem 0xfe600000-0xfe6fffff]
[    0.554808] pci 0000:00:14.4:   bridge window [io  0x0000-0x03af] (subtractive decode)
[    0.554810] pci 0000:00:14.4:   bridge window [io  0x03e0-0x0cf7] (subtractive decode)
[    0.554811] pci 0000:00:14.4:   bridge window [io  0x03b0-0x03df] (subtractive decode)
[    0.554813] pci 0000:00:14.4:   bridge window [io  0x0d00-0xffff] (subtractive decode)
[    0.554815] pci 0000:00:14.4:   bridge window [mem 0x000a0000-0x000bffff] (subtractive decode)
[    0.554816] pci 0000:00:14.4:   bridge window [mem 0x000c0000-0x000dffff] (subtractive decode)
[    0.554818] pci 0000:00:14.4:   bridge window [mem 0xc0000000-0xffffffff] (subtractive decode)
[    0.555225] ACPI: PCI Interrupt Link [LNKA] (IRQs 4 7 10 11 14 15) *0
[    0.555298] ACPI: PCI Interrupt Link [LNKB] (IRQs 4 7 10 11 14 15) *0
[    0.555373] ACPI: PCI Interrupt Link [LNKC] (IRQs 4 7 10 11 14 15) *0
[    0.555447] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 10 11 14 15) *0
[    0.555508] ACPI: PCI Interrupt Link [LNKE] (IRQs 4 7 10 11 14 15) *0
[    0.555557] ACPI: PCI Interrupt Link [LNKF] (IRQs 4 7 10 11 14 15) *0
[    0.555606] ACPI: PCI Interrupt Link [LNKG] (IRQs 4 7 10 11 14 15) *0
[    0.555655] ACPI: PCI Interrupt Link [LNKH] (IRQs 4 7 10 11 14 15) *0
[    0.555789] ACPI: Enabled 1 GPEs in block 00 to 1F
[    0.555795] ACPI: \_SB_.PCI0: notify handler is installed
[    0.555834] Found 1 acpi root devices
[    0.555856] ACPI : EC: GPE = 0xa, I/O: command/status = 0x66, data = 0x62
[    0.555950] vgaarb: device added: PCI:0000:01:00.0,decodes=io+mem,owns=io+mem,locks=none
[    0.555952] vgaarb: loaded
[    0.555953] vgaarb: bridge control possible 0000:01:00.0
[    0.556108] SCSI subsystem initialized
[    0.556160] libata version 3.00 loaded.
[    0.556176] ACPI: bus type USB registered
[    0.556191] usbcore: registered new interface driver usbfs
[    0.556197] usbcore: registered new interface driver hub
[    0.556220] usbcore: registered new device driver usb
[    0.556338] PCI: Using ACPI for IRQ routing
[    0.564611] PCI: pci_cache_line_size set to 64 bytes
[    0.564682] e820: reserve RAM buffer [mem 0x0009e800-0x0009ffff]
[    0.564683] e820: reserve RAM buffer [mem 0xba868000-0xbbffffff]
[    0.564684] e820: reserve RAM buffer [mem 0xbca38000-0xbfffffff]
[    0.564686] e820: reserve RAM buffer [mem 0xbd083000-0xbfffffff]
[    0.564687] e820: reserve RAM buffer [mem 0xbd800000-0xbfffffff]
[    0.564688] e820: reserve RAM buffer [mem 0x43f000000-0x43fffffff]
[    0.564755] NetLabel: Initializing
[    0.564756] NetLabel:  domain hash size = 128
[    0.564757] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.564766] NetLabel:  unlabeled traffic allowed by default
[    0.564837] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[    0.564840] hpet0: 3 comparators, 32-bit 14.318180 MHz counter
[    0.566917] Switched to clocksource hpet
[    0.572685] AppArmor: AppArmor Filesystem Enabled
[    0.572701] pnp: PnP ACPI init
[    0.572710] ACPI: bus type PNP registered
[    0.572797] system 00:00: [mem 0xe0000000-0xefffffff] has been reserved
[    0.572800] system 00:00: Plug and Play ACPI device, IDs PNP0c01 (active)
[    0.573318] system 00:01: [io  0x040b] has been reserved
[    0.573320] system 00:01: [io  0x04d6] has been reserved
[    0.573322] system 00:01: [io  0x0c00-0x0c01] has been reserved
[    0.573324] system 00:01: [io  0x0c14] has been reserved
[    0.573326] system 00:01: [io  0x0c50-0x0c51] has been reserved
[    0.573327] system 00:01: [io  0x0c52] has been reserved
[    0.573329] system 00:01: [io  0x0c6c] has been reserved
[    0.573331] system 00:01: [io  0x0c6f] has been reserved
[    0.573333] system 00:01: [io  0x0cd0-0x0cd1] has been reserved
[    0.573334] system 00:01: [io  0x0cd2-0x0cd3] has been reserved
[    0.573336] system 00:01: [io  0x0cd4-0x0cd5] has been reserved
[    0.573338] system 00:01: [io  0x0cd6-0x0cd7] has been reserved
[    0.573340] system 00:01: [io  0x0cd8-0x0cdf] has been reserved
[    0.573341] system 00:01: [io  0x0800-0x089f] could not be reserved
[    0.573343] system 00:01: [io  0x0b20-0x0b3f] has been reserved
[    0.573345] system 00:01: [io  0x0900-0x090f] has been reserved
[    0.573347] system 00:01: [io  0x0910-0x091f] has been reserved
[    0.573349] system 00:01: [io  0xfe00-0xfefe] has been reserved
[    0.573351] system 00:01: [mem 0xfec00000-0xfec00fff] could not be reserved
[    0.573353] system 00:01: [mem 0xfee00000-0xfee00fff] has been reserved
[    0.573355] system 00:01: [mem 0xfed80000-0xfed8ffff] has been reserved
[    0.573357] system 00:01: [mem 0xfed61000-0xfed70fff] has been reserved
[    0.573359] system 00:01: [mem 0xfec10000-0xfec10fff] has been reserved
[    0.573361] system 00:01: [mem 0xfed00000-0xfed00fff] has been reserved
[    0.573363] system 00:01: [mem 0xff800000-0xffffffff] has been reserved
[    0.573365] system 00:01: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.573505] system 00:02: [io  0x0290-0x02af] has been reserved
[    0.573508] system 00:02: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.573520] pnp 00:03: [dma 4]
[    0.573535] pnp 00:03: Plug and Play ACPI device, IDs PNP0200 (active)
[    0.573564] pnp 00:04: Plug and Play ACPI device, IDs PNP0b00 (active)
[    0.573583] pnp 00:05: Plug and Play ACPI device, IDs PNP0800 (active)
[    0.573637] system 00:06: [io  0x04d0-0x04d1] has been reserved
[    0.573639] system 00:06: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.573661] pnp 00:07: Plug and Play ACPI device, IDs PNP0c04 (active)
[    0.573696] system 00:08: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.573737] pnp 00:09: Plug and Play ACPI device, IDs PNP0303 PNP030b (active)
[    0.573909] pnp 00:0a: [dma 0 disabled]
[    0.573948] pnp 00:0a: Plug and Play ACPI device, IDs PNP0501 (active)
[    0.574080] system 00:0b: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.574193] system 00:0c: [mem 0xfec20000-0xfec200ff] could not be reserved
[    0.574195] system 00:0c: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.574371] pnp 00:0d: Plug and Play ACPI device, IDs PNP0103 (active)
[    0.574376] pnp: PnP ACPI: found 14 devices
[    0.574377] ACPI: bus type PNP unregistered
[    0.580761] pci 0000:00:02.0: PCI bridge to [bus 01]
[    0.580764] pci 0000:00:02.0:   bridge window [io  0xe000-0xefff]
[    0.580768] pci 0000:00:02.0:   bridge window [mem 0xfea00000-0xfeafffff]
[    0.580771] pci 0000:00:02.0:   bridge window [mem 0xc0000000-0xcfffffff 64bit pref]
[    0.580775] pci 0000:00:04.0: PCI bridge to [bus 02]
[    0.580777] pci 0000:00:04.0:   bridge window [io  0xd000-0xdfff]
[    0.580782] pci 0000:00:04.0:   bridge window [mem 0xd0000000-0xd00fffff 64bit pref]
[    0.580786] pci 0000:00:05.0: PCI bridge to [bus 03]
[    0.580789] pci 0000:00:05.0:   bridge window [mem 0xfe900000-0xfe9fffff]
[    0.580795] pci 0000:00:06.0: PCI bridge to [bus 04]
[    0.580797] pci 0000:00:06.0:   bridge window [io  0xc000-0xcfff]
[    0.580800] pci 0000:00:06.0:   bridge window [mem 0xfe800000-0xfe8fffff]
[    0.580805] pci 0000:00:07.0: PCI bridge to [bus 05]
[    0.580808] pci 0000:00:07.0:   bridge window [mem 0xfe700000-0xfe7fffff]
[    0.580813] pci 0000:00:14.4: PCI bridge to [bus 06]
[    0.580816] pci 0000:00:14.4:   bridge window [io  0xb000-0xbfff]
[    0.580821] pci 0000:00:14.4:   bridge window [mem 0xfe600000-0xfe6fffff]
[    0.580829] pci_bus 0000:00: resource 4 [io  0x0000-0x03af]
[    0.580830] pci_bus 0000:00: resource 5 [io  0x03e0-0x0cf7]
[    0.580832] pci_bus 0000:00: resource 6 [io  0x03b0-0x03df]
[    0.580834] pci_bus 0000:00: resource 7 [io  0x0d00-0xffff]
[    0.580835] pci_bus 0000:00: resource 8 [mem 0x000a0000-0x000bffff]
[    0.580837] pci_bus 0000:00: resource 9 [mem 0x000c0000-0x000dffff]
[    0.580838] pci_bus 0000:00: resource 10 [mem 0xc0000000-0xffffffff]
[    0.580840] pci_bus 0000:01: resource 0 [io  0xe000-0xefff]
[    0.580842] pci_bus 0000:01: resource 1 [mem 0xfea00000-0xfeafffff]
[    0.580843] pci_bus 0000:01: resource 2 [mem 0xc0000000-0xcfffffff 64bit pref]
[    0.580845] pci_bus 0000:02: resource 0 [io  0xd000-0xdfff]
[    0.580846] pci_bus 0000:02: resource 2 [mem 0xd0000000-0xd00fffff 64bit pref]
[    0.580848] pci_bus 0000:03: resource 1 [mem 0xfe900000-0xfe9fffff]
[    0.580850] pci_bus 0000:04: resource 0 [io  0xc000-0xcfff]
[    0.580851] pci_bus 0000:04: resource 1 [mem 0xfe800000-0xfe8fffff]
[    0.580853] pci_bus 0000:05: resource 1 [mem 0xfe700000-0xfe7fffff]
[    0.580854] pci_bus 0000:06: resource 0 [io  0xb000-0xbfff]
[    0.580856] pci_bus 0000:06: resource 1 [mem 0xfe600000-0xfe6fffff]
[    0.580857] pci_bus 0000:06: resource 4 [io  0x0000-0x03af]
[    0.580859] pci_bus 0000:06: resource 5 [io  0x03e0-0x0cf7]
[    0.580861] pci_bus 0000:06: resource 6 [io  0x03b0-0x03df]
[    0.580862] pci_bus 0000:06: resource 7 [io  0x0d00-0xffff]
[    0.580864] pci_bus 0000:06: resource 8 [mem 0x000a0000-0x000bffff]
[    0.580865] pci_bus 0000:06: resource 9 [mem 0x000c0000-0x000dffff]
[    0.580867] pci_bus 0000:06: resource 10 [mem 0xc0000000-0xffffffff]
[    0.580889] NET: Registered protocol family 2
[    0.581087] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.581373] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    0.581567] TCP: Hash tables configured (established 131072 bind 65536)
[    0.581594] TCP: reno registered
[    0.581616] UDP hash table entries: 8192 (order: 6, 262144 bytes)
[    0.581687] UDP-Lite hash table entries: 8192 (order: 6, 262144 bytes)
[    0.581789] NET: Registered protocol family 1
[    0.871585] pci 0000:01:00.0: Boot video device
[    0.871866] PCI: CLS 64 bytes, default 64
[    0.871925] Trying to unpack rootfs image as initramfs...
[    1.239691] Freeing initrd memory: 27392K (ffff880034a70000 - ffff880036530000)
[    1.240042] PCI-DMA: Disabling AGP.
[    1.240119] PCI-DMA: aperture base @ b0000000 size 65536 KB
[    1.240121] PCI-DMA: using GART IOMMU.
[    1.240123] PCI-DMA: Reserving 64MB of IOMMU area in the AGP aperture
[    1.244295] perf: AMD NB counters detected
[    1.244327] LVT offset 0 assigned for vector 0x400
[    1.244353] perf: AMD IBS detected (0x000000ff)
[    1.244390] microcode: CPU0: patch_level=0x06000822
[    1.244395] microcode: CPU1: patch_level=0x06000822
[    1.244404] microcode: CPU2: patch_level=0x06000822
[    1.244412] microcode: CPU3: patch_level=0x06000822
[    1.244419] microcode: CPU4: patch_level=0x06000822
[    1.244427] microcode: CPU5: patch_level=0x06000822
[    1.244435] microcode: CPU6: patch_level=0x06000822
[    1.244443] microcode: CPU7: patch_level=0x06000822
[    1.244515] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[    1.244518] Scanning for low memory corruption every 60 seconds
[    1.244825] Initialise system trusted keyring
[    1.244862] audit: initializing netlink socket (disabled)
[    1.244877] type=2000 audit(1413715992.936:1): initialized
[    1.266446] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    1.267768] zbud: loaded
[    1.267879] VFS: Disk quotas dquot_6.5.2
[    1.267924] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    1.268322] fuse init (API version 7.22)
[    1.268386] msgmni has been set to 31894
[    1.268433] Key type big_key registered
[    1.268822] Key type asymmetric registered
[    1.268824] Asymmetric key parser 'x509' registered
[    1.268851] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 252)
[    1.268894] io scheduler noop registered
[    1.268896] io scheduler deadline registered (default)
[    1.268918] io scheduler cfq registered
[    1.269293] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    1.269306] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    1.269353] ipmi message handler version 39.2
[    1.269405] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0
[    1.269409] ACPI: Power Button [PWRB]
[    1.269438] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
[    1.269440] ACPI: Power Button [PWRF]
[    1.269496] ACPI: acpi_idle registered with cpuidle
[    1.270038] GHES: HEST is not enabled!
[    1.270122] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    1.290532] 00:0a: ttyS0 at I/O 0x3f8 (irq = 4, base_baud = 115200) is a 16550A
[    1.291958] Linux agpgart interface v0.103
[    1.293137] brd: module loaded
[    1.293775] loop: module loaded
[    1.294115] libphy: Fixed MDIO Bus: probed
[    1.294191] tun: Universal TUN/TAP device driver, 1.6
[    1.294192] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    1.294238] PPP generic driver version 2.4.2
[    1.294283] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    1.294293] ehci-pci: EHCI PCI platform driver
[    1.294386] QUIRK: Enable AMD PLL fix
[    1.294404] ehci-pci 0000:00:12.2: EHCI Host Controller
[    1.294409] ehci-pci 0000:00:12.2: new USB bus registered, assigned bus number 1
[    1.294413] ehci-pci 0000:00:12.2: applying AMD SB700/SB800/Hudson-2/3 EHCI dummy qh workaround
[    1.294422] ehci-pci 0000:00:12.2: debug port 1
[    1.294459] ehci-pci 0000:00:12.2: irq 17, io mem 0xfeb09000
[    1.307995] ehci-pci 0000:00:12.2: USB 2.0 started, EHCI 1.00
[    1.308040] usb usb1: New USB device found, idVendor=1d6b, idProduct=0002
[    1.308042] usb usb1: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.308044] usb usb1: Product: EHCI Host Controller
[    1.308046] usb usb1: Manufacturer: Linux 3.13.0-36-generic ehci_hcd
[    1.308047] usb usb1: SerialNumber: 0000:00:12.2
[    1.308147] hub 1-0:1.0: USB hub found
[    1.308154] hub 1-0:1.0: 5 ports detected
[    1.308344] ehci-pci 0000:00:13.2: EHCI Host Controller
[    1.308349] ehci-pci 0000:00:13.2: new USB bus registered, assigned bus number 2
[    1.308352] ehci-pci 0000:00:13.2: applying AMD SB700/SB800/Hudson-2/3 EHCI dummy qh workaround
[    1.308360] ehci-pci 0000:00:13.2: debug port 1
[    1.308393] ehci-pci 0000:00:13.2: irq 21, io mem 0xfeb07000
[    1.320021] ehci-pci 0000:00:13.2: USB 2.0 started, EHCI 1.00
[    1.320067] usb usb2: New USB device found, idVendor=1d6b, idProduct=0002
[    1.320069] usb usb2: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.320070] usb usb2: Product: EHCI Host Controller
[    1.320072] usb usb2: Manufacturer: Linux 3.13.0-36-generic ehci_hcd
[    1.320073] usb usb2: SerialNumber: 0000:00:13.2
[    1.320197] hub 2-0:1.0: USB hub found
[    1.320203] hub 2-0:1.0: 5 ports detected
[    1.320378] ehci-pci 0000:00:16.2: EHCI Host Controller
[    1.320382] ehci-pci 0000:00:16.2: new USB bus registered, assigned bus number 3
[    1.320384] ehci-pci 0000:00:16.2: applying AMD SB700/SB800/Hudson-2/3 EHCI dummy qh workaround
[    1.320393] ehci-pci 0000:00:16.2: debug port 1
[    1.320420] ehci-pci 0000:00:16.2: irq 23, io mem 0xfeb04000
[    1.332074] ehci-pci 0000:00:16.2: USB 2.0 started, EHCI 1.00
[    1.332110] usb usb3: New USB device found, idVendor=1d6b, idProduct=0002
[    1.332112] usb usb3: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.332114] usb usb3: Product: EHCI Host Controller
[    1.332115] usb usb3: Manufacturer: Linux 3.13.0-36-generic ehci_hcd
[    1.332117] usb usb3: SerialNumber: 0000:00:16.2
[    1.332229] hub 3-0:1.0: USB hub found
[    1.332235] hub 3-0:1.0: 4 ports detected
[    1.332351] ehci-platform: EHCI generic platform driver
[    1.332358] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    1.332359] ohci-pci: OHCI PCI platform driver
[    1.332446] ohci-pci 0000:00:12.0: OHCI PCI host controller
[    1.332451] ohci-pci 0000:00:12.0: new USB bus registered, assigned bus number 4
[    1.332469] ohci-pci 0000:00:12.0: irq 18, io mem 0xfeb0a000
[    1.392179] usb usb4: New USB device found, idVendor=1d6b, idProduct=0001
[    1.392182] usb usb4: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.392184] usb usb4: Product: OHCI PCI host controller
[    1.392186] usb usb4: Manufacturer: Linux 3.13.0-36-generic ohci_hcd
[    1.392187] usb usb4: SerialNumber: 0000:00:12.0
[    1.392305] hub 4-0:1.0: USB hub found
[    1.392314] hub 4-0:1.0: 5 ports detected
[    1.392480] ohci-pci 0000:00:13.0: OHCI PCI host controller
[    1.392485] ohci-pci 0000:00:13.0: new USB bus registered, assigned bus number 5
[    1.392503] ohci-pci 0000:00:13.0: irq 20, io mem 0xfeb08000
[    1.452245] usb usb5: New USB device found, idVendor=1d6b, idProduct=0001
[    1.452248] usb usb5: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.452249] usb usb5: Product: OHCI PCI host controller
[    1.452251] usb usb5: Manufacturer: Linux 3.13.0-36-generic ohci_hcd
[    1.452252] usb usb5: SerialNumber: 0000:00:13.0
[    1.452378] hub 5-0:1.0: USB hub found
[    1.452386] hub 5-0:1.0: 5 ports detected
[    1.452554] ohci-pci 0000:00:14.5: OHCI PCI host controller
[    1.452559] ohci-pci 0000:00:14.5: new USB bus registered, assigned bus number 6
[    1.452569] ohci-pci 0000:00:14.5: irq 18, io mem 0xfeb06000
[    1.512355] usb usb6: New USB device found, idVendor=1d6b, idProduct=0001
[    1.512357] usb usb6: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.512359] usb usb6: Product: OHCI PCI host controller
[    1.512360] usb usb6: Manufacturer: Linux 3.13.0-36-generic ohci_hcd
[    1.512362] usb usb6: SerialNumber: 0000:00:14.5
[    1.512537] hub 6-0:1.0: USB hub found
[    1.512544] hub 6-0:1.0: 2 ports detected
[    1.512690] ohci-pci 0000:00:16.0: OHCI PCI host controller
[    1.512694] ohci-pci 0000:00:16.0: new USB bus registered, assigned bus number 7
[    1.512714] ohci-pci 0000:00:16.0: irq 22, io mem 0xfeb05000
[    1.572364] usb usb7: New USB device found, idVendor=1d6b, idProduct=0001
[    1.572366] usb usb7: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.572368] usb usb7: Product: OHCI PCI host controller
[    1.572369] usb usb7: Manufacturer: Linux 3.13.0-36-generic ohci_hcd
[    1.572370] usb usb7: SerialNumber: 0000:00:16.0
[    1.572597] hub 7-0:1.0: USB hub found
[    1.572605] hub 7-0:1.0: 4 ports detected
[    1.572689] ohci-platform: OHCI generic platform driver
[    1.572696] uhci_hcd: USB Universal Host Controller Interface driver
[    1.572763] xhci_hcd 0000:03:00.0: xHCI Host Controller
[    1.572768] xhci_hcd 0000:03:00.0: new USB bus registered, assigned bus number 8
[    1.632210] xhci_hcd 0000:03:00.0: irq 72 for MSI/MSI-X
[    1.632216] xhci_hcd 0000:03:00.0: irq 73 for MSI/MSI-X
[    1.632222] xhci_hcd 0000:03:00.0: irq 74 for MSI/MSI-X
[    1.632226] xhci_hcd 0000:03:00.0: irq 75 for MSI/MSI-X
[    1.632231] xhci_hcd 0000:03:00.0: irq 76 for MSI/MSI-X
[    1.632236] xhci_hcd 0000:03:00.0: irq 77 for MSI/MSI-X
[    1.632240] xhci_hcd 0000:03:00.0: irq 78 for MSI/MSI-X
[    1.632245] xhci_hcd 0000:03:00.0: irq 79 for MSI/MSI-X
[    1.632344] usb usb8: New USB device found, idVendor=1d6b, idProduct=0002
[    1.632346] usb usb8: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.632347] usb usb8: Product: xHCI Host Controller
[    1.632348] usb usb8: Manufacturer: Linux 3.13.0-36-generic xhci_hcd
[    1.632349] usb usb8: SerialNumber: 0000:03:00.0
[    1.632516] hub 8-0:1.0: USB hub found
[    1.632523] hub 8-0:1.0: 2 ports detected
[    1.632586] xhci_hcd 0000:03:00.0: xHCI Host Controller
[    1.632589] xhci_hcd 0000:03:00.0: new USB bus registered, assigned bus number 9
[    1.632626] usb usb9: New USB device found, idVendor=1d6b, idProduct=0003
[    1.632628] usb usb9: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.632629] usb usb9: Product: xHCI Host Controller
[    1.632631] usb usb9: Manufacturer: Linux 3.13.0-36-generic xhci_hcd
[    1.632632] usb usb9: SerialNumber: 0000:03:00.0
[    1.632702] hub 9-0:1.0: USB hub found
[    1.632709] hub 9-0:1.0: 2 ports detected
[    1.640648] xhci_hcd 0000:05:00.0: xHCI Host Controller
[    1.640654] xhci_hcd 0000:05:00.0: new USB bus registered, assigned bus number 10
[    1.700118] xhci_hcd 0000:05:00.0: irq 80 for MSI/MSI-X
[    1.700133] xhci_hcd 0000:05:00.0: irq 81 for MSI/MSI-X
[    1.700138] xhci_hcd 0000:05:00.0: irq 82 for MSI/MSI-X
[    1.700171] xhci_hcd 0000:05:00.0: irq 83 for MSI/MSI-X
[    1.700177] xhci_hcd 0000:05:00.0: irq 84 for MSI/MSI-X
[    1.700183] xhci_hcd 0000:05:00.0: irq 85 for MSI/MSI-X
[    1.700190] xhci_hcd 0000:05:00.0: irq 86 for MSI/MSI-X
[    1.700198] xhci_hcd 0000:05:00.0: irq 87 for MSI/MSI-X
[    1.700307] usb usb10: New USB device found, idVendor=1d6b, idProduct=0002
[    1.700309] usb usb10: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.700311] usb usb10: Product: xHCI Host Controller
[    1.700312] usb usb10: Manufacturer: Linux 3.13.0-36-generic xhci_hcd
[    1.700313] usb usb10: SerialNumber: 0000:05:00.0
[    1.700398] hub 10-0:1.0: USB hub found
[    1.700405] hub 10-0:1.0: 2 ports detected
[    1.700464] xhci_hcd 0000:05:00.0: xHCI Host Controller
[    1.700467] xhci_hcd 0000:05:00.0: new USB bus registered, assigned bus number 11
[    1.700513] usb usb11: New USB device found, idVendor=1d6b, idProduct=0003
[    1.700515] usb usb11: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.700516] usb usb11: Product: xHCI Host Controller
[    1.700517] usb usb11: Manufacturer: Linux 3.13.0-36-generic xhci_hcd
[    1.700519] usb usb11: SerialNumber: 0000:05:00.0
[    1.700661] hub 11-0:1.0: USB hub found
[    1.700668] hub 11-0:1.0: 2 ports detected
[    1.708754] i8042: PNP: PS/2 Controller [PNP0303:PS2K] at 0x60,0x64 irq 1
[    1.708756] i8042: PNP: PS/2 appears to have AUX port disabled, if this is incorrect please boot with i8042.nopnp
[    1.708875] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.709013] mousedev: PS/2 mouse device common for all mice
[    1.709138] rtc_cmos 00:04: RTC can wake from S4
[    1.709240] rtc_cmos 00:04: rtc core: registered rtc_cmos as rtc0
[    1.709261] rtc_cmos 00:04: alarms up to one month, y3k, 114 bytes nvram, hpet irqs
[    1.709322] device-mapper: uevent: version 1.0.3
[    1.709386] device-mapper: ioctl: 4.27.0-ioctl (2013-10-30) initialised: dm-devel@redhat.com
[    1.709392] ledtrig-cpu: registered to indicate activity on CPUs
[    1.709474] TCP: cubic registered
[    1.709556] NET: Registered protocol family 10
[    1.709702] NET: Registered protocol family 17
[    1.709708] Key type dns_resolver registered
[    1.710383] Loading compiled-in X.509 certificates
[    1.711190] Loaded X.509 cert 'Magrathea: Glacier signing key: 38f3b6c63a85affdfbbe0e53339df8e0c6b6c9d5'
[    1.711198] registered taskstats version 1
[    1.713534] Key type trusted registered
[    1.715488] Key type encrypted registered
[    1.717187] AppArmor: AppArmor sha1 policy hashing enabled
[    1.717190] IMA: No TPM chip found, activating TPM-bypass!
[    1.717462] regulator-dummy: disabling
[    1.717520]   Magic number: 2:850:881
[    1.717599] rtc_cmos 00:04: setting system clock to 2014-10-19 10:53:14 UTC (1413715994)
[    1.717725] acpi-cpufreq: overriding BIOS provided _PSD data
[    1.718068] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.718069] EDD information not available.
[    1.718108] PM: Hibernation image not present or could not be loaded.
[    1.719288] Freeing unused kernel memory: 1336K (ffffffff81d1f000 - ffffffff81e6d000)
[    1.719289] Write protecting the kernel read-only data: 12288k
[    1.722115] Freeing unused kernel memory: 808K (ffff880001736000 - ffff880001800000)
[    1.724451] Freeing unused kernel memory: 692K (ffff880001b53000 - ffff880001c00000)
[    1.736231] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input2
[    1.737951] systemd-udevd[147]: starting version 204
[    1.748908] wmi: Mapper loaded
[    1.753509] r8168: module verification failed: signature and/or  required key missing - tainting kernel
[    1.753874] r8168 Gigabit Ethernet driver 8.037.00-NAPI loaded
[    1.753980] r8168 0000:02:00.0: irq 88 for MSI/MSI-X
[    1.756445] ahci 0000:00:11.0: version 3.0
[    1.756622] ahci 0000:00:11.0: AHCI 0001.0200 32 slots 3 ports 6 Gbps 0xb impl SATA mode
[    1.756626] ahci 0000:00:11.0: flags: 64bit ncq sntf ilck pm led clo pmp pio slum part 
[    1.757338] scsi0 : ahci
[    1.757590] [drm] Initialized drm 1.1.0 20060810
[    1.758095] scsi1 : ahci
[    1.758199] scsi2 : ahci
[    1.758271] scsi3 : ahci
[    1.758314] ata1: SATA max UDMA/133 abar m1024@0xfeb0b000 port 0xfeb0b100 irq 19
[    1.758316] ata2: SATA max UDMA/133 abar m1024@0xfeb0b000 port 0xfeb0b180 irq 19
[    1.758318] ata3: DUMMY
[    1.758321] ata4: SATA max UDMA/133 abar m1024@0xfeb0b000 port 0xfeb0b280 irq 19
[    1.758435] ahci 0000:04:00.0: irq 89 for MSI/MSI-X
[    1.758467] ahci 0000:04:00.0: SSS flag set, parallel bus scan disabled
[    1.758497] ahci 0000:04:00.0: AHCI 0001.0200 32 slots 2 ports 6 Gbps 0x3 impl SATA mode
[    1.758500] ahci 0000:04:00.0: flags: 64bit ncq sntf stag led clo pmp pio slum part ccc sxs 
[    1.758988] scsi4 : ahci
[    1.759140] scsi5 : ahci
[    1.759202] ata5: SATA max UDMA/133 abar m512@0xfe800000 port 0xfe800100 irq 89
[    1.759205] ata6: SATA max UDMA/133 abar m512@0xfe800000 port 0xfe800180 irq 89
[    1.774953] eth%d: 0xffffc9000189a000, ac:22:0b:82:7e:4d, IRQ 88
[    1.775103] r8168: This product is covered by one or more of the following patents: US6,570,884, US6,115,776, and US6,327,625.
[    1.775108] r8168  Copyright (C) 2013  Realtek NIC software team <nicfae@realtek.com> 
[    1.775108]  This program comes with ABSOLUTELY NO WARRANTY; for details, please see <http://www.gnu.org/licenses/>. 
[    1.775108]  This is free software, and you are welcome to redistribute it under certain conditions; see <http://www.gnu.org/licenses/>. 
[    1.779479] [drm] radeon kernel modesetting enabled.
[    1.779711] [drm] initializing kernel modesetting (JUNIPER 0x1002:0x68B8 0x174B:0x1482).
[    1.779727] [drm] register mmio base: 0xFEA20000
[    1.779728] [drm] register mmio size: 131072
[    1.779784] ATOM BIOS: JUNIPER
[    1.779837] radeon 0000:01:00.0: VRAM: 1024M 0x0000000000000000 - 0x000000003FFFFFFF (1024M used)
[    1.779839] radeon 0000:01:00.0: GTT: 1024M 0x0000000040000000 - 0x000000007FFFFFFF
[    1.779841] [drm] Detected VRAM RAM=1024M, BAR=256M
[    1.779842] [drm] RAM width 128bits DDR
[    1.779906] [TTM] Zone  kernel: Available graphics memory: 8166330 kiB
[    1.779908] [TTM] Zone   dma32: Available graphics memory: 2097152 kiB
[    1.779909] [TTM] Initializing pool allocator
[    1.779913] [TTM] Initializing DMA pool allocator
[    1.779943] [drm] radeon: 1024M of VRAM memory ready
[    1.779944] [drm] radeon: 1024M of GTT memory ready.
[    1.779955] [drm] Loading JUNIPER Microcode
[    1.780213] [drm] GART: num cpu pages 262144, num gpu pages 262144
[    1.781422] [drm] enabling PCIE gen 2 link speeds, disable with radeon.pcie_gen2=0
[    1.791040] [drm] PCIE GART of 1024M enabled (table at 0x000000000025D000).
[    1.791117] radeon 0000:01:00.0: WB enabled
[    1.791119] radeon 0000:01:00.0: fence driver on ring 0 use gpu addr 0x0000000040000c00 and cpu addr 0xffff88042197dc00
[    1.791121] radeon 0000:01:00.0: fence driver on ring 3 use gpu addr 0x0000000040000c0c and cpu addr 0xffff88042197dc0c
[    1.791488] radeon 0000:01:00.0: fence driver on ring 5 use gpu addr 0x000000000005c418 and cpu addr 0xffffc90011c9c418
[    1.791490] [drm] Supports vblank timestamp caching Rev 2 (21.10.2013).
[    1.791491] [drm] Driver supports precise vblank timestamp query.
[    1.791529] radeon 0000:01:00.0: irq 90 for MSI/MSI-X
[    1.791538] radeon 0000:01:00.0: radeon: using MSI.
[    1.791559] [drm] radeon: irq initialized.
[    1.807717] [drm] ring test on 0 succeeded in 1 usecs
[    1.807772] [drm] ring test on 3 succeeded in 1 usecs
[    1.824800] firewire_ohci 0000:06:07.0: added OHCI v1.10 device as card 0, 4 IR + 8 IT contexts, quirks 0x11
[    2.013504] [drm] ring test on 5 succeeded in 1 usecs
[    2.013508] [drm] UVD initialized successfully.
[    2.013598] [drm] Enabling audio 0 support
[    2.013618] [drm] ib test on ring 0 succeeded in 0 usecs
[    2.013637] [drm] ib test on ring 3 succeeded in 0 usecs
[    2.077152] ata5: SATA link down (SStatus 0 SControl 300)
[    2.183882] [drm] ib test on ring 5 succeeded
[    2.184257] [drm] Radeon Display Connectors
[    2.184258] [drm] Connector 0:
[    2.184260] [drm]   DP-1
[    2.184261] [drm]   HPD4
[    2.184262] [drm]   DDC: 0x6440 0x6440 0x6444 0x6444 0x6448 0x6448 0x644c 0x644c
[    2.184263] [drm]   Encoders:
[    2.184264] [drm]     DFP1: INTERNAL_UNIPHY2
[    2.184265] [drm] Connector 1:
[    2.184266] [drm]   HDMI-A-1
[    2.184266] [drm]   HPD5
[    2.184268] [drm]   DDC: 0x6430 0x6430 0x6434 0x6434 0x6438 0x6438 0x643c 0x643c
[    2.184268] [drm]   Encoders:
[    2.184269] [drm]     DFP2: INTERNAL_UNIPHY2
[    2.184270] [drm] Connector 2:
[    2.184271] [drm]   DVI-I-1
[    2.184272] [drm]   HPD1
[    2.184273] [drm]   DDC: 0x6460 0x6460 0x6464 0x6464 0x6468 0x6468 0x646c 0x646c
[    2.184274] [drm]   Encoders:
[    2.184274] [drm]     DFP3: INTERNAL_UNIPHY1
[    2.184275] [drm]     CRT2: INTERNAL_KLDSCP_DAC2
[    2.184276] [drm] Connector 3:
[    2.184277] [drm]   DVI-I-2
[    2.184278] [drm]   HPD6
[    2.184279] [drm]   DDC: 0x6450 0x6450 0x6454 0x6454 0x6458 0x6458 0x645c 0x645c
[    2.184280] [drm]   Encoders:
[    2.184280] [drm]     DFP4: INTERNAL_UNIPHY
[    2.184281] [drm]     CRT1: INTERNAL_KLDSCP_DAC1
[    2.184316] [drm] Internal thermal controller with fan control
[    2.193776] [drm] radeon: dpm initialized
[    2.217308] usb 4-1: new low-speed USB device number 2 using ohci-pci
[    2.245362] tsc: Refined TSC clocksource calibration: 3511.787 MHz
[    2.249312] ata4: SATA link up 6.0 Gbps (SStatus 133 SControl 300)
[    2.249369] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    2.249391] ata2: SATA link up 6.0 Gbps (SStatus 133 SControl 300)
[    2.250309] ata4.00: ATA-8: SanDisk SDSSDH2256G, X2306RL, max UDMA/133
[    2.250312] ata4.00: 500118192 sectors, multi 1: LBA48 NCQ (depth 31/32), AA
[    2.251238] ata2.00: supports DRM functions and may not be fully accessible
[    2.251361] ata2.00: failed to get NCQ Send/Recv Log Emask 0x1
[    2.251364] ata2.00: ATA-9: Samsung SSD 840 EVO 1TB, EXT0BB6Q, max UDMA/133
[    2.251366] ata2.00: 1953525168 sectors, multi 1: LBA48 NCQ (depth 31/32), AA
[    2.251458] ata4.00: configured for UDMA/133
[    2.251592] ata2.00: supports DRM functions and may not be fully accessible
[    2.251651] ata2.00: failed to get NCQ Send/Recv Log Emask 0x1
[    2.251655] ata2.00: configured for UDMA/133
[    2.255717] ata1.00: ATA-8: WDC WD20EARS-00S8B1, 80.00A80, max UDMA/133
[    2.255719] ata1.00: 3907029168 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
[    2.261610] ata1.00: configured for UDMA/133
[    2.261821] scsi 0:0:0:0: Direct-Access     ATA      WDC WD20EARS-00S 80.0 PQ: 0 ANSI: 5
[    2.261992] sd 0:0:0:0: [sda] 3907029168 512-byte logical blocks: (2.00 TB/1.81 TiB)
[    2.261995] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    2.262091] sd 0:0:0:0: [sda] Write Protect is off
[    2.262095] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    2.262136] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.262150] scsi 1:0:0:0: Direct-Access     ATA      Samsung SSD 840  EXT0 PQ: 0 ANSI: 5
[    2.262268] sd 1:0:0:0: [sdb] 1953525168 512-byte logical blocks: (1.00 TB/931 GiB)
[    2.262293] sd 1:0:0:0: Attached scsi generic sg1 type 0
[    2.262360] sd 1:0:0:0: [sdb] Write Protect is off
[    2.262364] sd 1:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[    2.262412] sd 1:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.262414] scsi 3:0:0:0: Direct-Access     ATA      SanDisk SDSSDH22 X230 PQ: 0 ANSI: 5
[    2.262545] sd 3:0:0:0: [sdc] 500118192 512-byte logical blocks: (256 GB/238 GiB)
[    2.262571] sd 3:0:0:0: Attached scsi generic sg2 type 0
[    2.262630] sd 3:0:0:0: [sdc] Write Protect is off
[    2.262633] sd 3:0:0:0: [sdc] Mode Sense: 00 3a 00 00
[    2.262685] sd 3:0:0:0: [sdc] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.262834]  sdb: sdb1
[    2.263161]  sdc: sdc1 sdc2
[    2.263174] sd 1:0:0:0: [sdb] Attached SCSI disk
[    2.263486] sd 3:0:0:0: [sdc] Attached SCSI disk
[    2.298975]  sda: sda1
[    2.299248] sd 0:0:0:0: [sda] Attached SCSI disk
[    2.313638] [drm] fb mappable at 0xC045E000
[    2.313640] [drm] vram apper at 0xC0000000
[    2.313641] [drm] size 8294400
[    2.313642] [drm] fb depth is 24
[    2.313643] [drm]    pitch is 7680
[    2.313771] fbcon: radeondrmfb (fb0) is primary device
[    2.325609] firewire_core 0000:06:07.0: created device fw0: GUID 001e8c0000671455, S400
[    2.354413] Console: switching to colour frame buffer device 240x67
[    2.358089] radeon 0000:01:00.0: fb0: radeondrmfb frame buffer device
[    2.358090] radeon 0000:01:00.0: registered panic notifier
[    2.358093] [drm] Initialized radeon 2.36.0 20080528 for 0000:01:00.0 on minor 0
[    2.390673] usb 4-1: New USB device found, idVendor=046d, idProduct=c050
[    2.390680] usb 4-1: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[    2.390685] usb 4-1: Product: USB-PS/2 Optical Mouse
[    2.390689] usb 4-1: Manufacturer: Logitech
[    2.395505] hidraw: raw HID events driver (C) Jiri Kosina
[    2.402961] usbcore: registered new interface driver usbhid
[    2.402962] usbhid: USB HID core driver
[    2.404472] input: Logitech USB-PS/2 Optical Mouse as /devices/pci0000:00/0000:00:12.0/usb4/4-1/4-1:1.0/input/input3
[    2.404590] hid-generic 0003:046D:C050.0001: input,hidraw0: USB HID v1.10 Mouse [Logitech USB-PS/2 Optical Mouse] on usb-0000:00:12.0-1/input0
[    2.581853] ata6: SATA link down (SStatus 0 SControl 300)
[    2.654050] usb 4-2: new full-speed USB device number 3 using ohci-pci
[    2.676947] md: bind<sda1>
[    2.679455] md: raid1 personality registered for level 1
[    2.679748] md/raid1:md2: active with 1 out of 2 mirrors
[    2.679765] md2: detected capacity change from 0 to 2000263667712
[    2.717049]  md2: unknown partition table
[    2.877348] usb 4-2: New USB device found, idVendor=1852, idProduct=7022
[    2.877355] usb 4-2: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[    2.877360] usb 4-2: Product: UAC1 DAC
[    2.877364] usb 4-2: Manufacturer: Binary Audio
[    2.893494] input: Binary Audio UAC1 DAC as /devices/pci0000:00/0000:00:12.0/usb4/4-2/4-2:1.0/input/input4
[    2.893677] hid-generic 0003:1852:7022.0002: input,hidraw1: USB HID v1.00 Device [Binary Audio UAC1 DAC] on usb-0000:00:12.0-2/input0
[    3.155252] md: linear personality registered for level -1
[    3.157650] md: multipath personality registered for level -4
[    3.159891] md: raid0 personality registered for level 0
[    3.230665] raid6: sse2x1    6776 MB/s
[    3.298758] raid6: sse2x2   11034 MB/s
[    3.366853] raid6: sse2x4   13132 MB/s
[    3.366854] raid6: using algorithm sse2x4 (13132 MB/s)
[    3.366856] raid6: using ssse3x2 recovery algorithm
[    3.367135] Switched to clocksource tsc
[    3.368086] xor: automatically using best checksumming function:
[    3.406910]    avx       :  4441.000 MB/sec
[    3.408039] async_tx: api initialized (async)
[    3.414010] md: raid6 personality registered for level 6
[    3.414013] md: raid5 personality registered for level 5
[    3.414014] md: raid4 personality registered for level 4
[    3.419433] md: raid10 personality registered for level 10
[    3.468035] EXT4-fs (sdb1): mounted filesystem with ordered data mode. Opts: (null)
[    3.546230] random: init urandom read with 95 bits of entropy available
[    3.791355] random: nonblocking pool is initialized
[    4.024472] ata2.00: exception Emask 0x10 SAct 0x7fffffff SErr 0x280100 action 0x6 frozen
[    4.024479] ata2.00: irq_stat 0x08000000, interface fatal error
[    4.024484] ata2: SError: { UnrecovData 10B8B BadCRC }
[    4.024490] ata2.00: failed command: READ FPDMA QUEUED
[    4.024500] ata2.00: cmd 60/88:00:80:38:4c/02:00:3a:00:00/40 tag 0 ncq 331776 in
[    4.024500]          res 40/00:40:40:52:4c/00:00:3a:00:00/40 Emask 0x10 (ATA bus error)
[    4.024505] ata2.00: status: { DRDY }
[    4.024509] ata2.00: failed command: READ FPDMA QUEUED
[    4.024517] ata2.00: cmd 60/00:08:a8:3d:4c/01:00:3a:00:00/40 tag 1 ncq 131072 in
[    4.024517]          res 40/00:40:40:52:4c/00:00:3a:00:00/40 Emask 0x10 (ATA bus error)
[    4.024521] ata2.00: status: { DRDY }
[    4.024524] ata2.00: failed command: READ FPDMA QUEUED
[    4.024532] ata2.00: cmd 60/88:10:d8:3f:4c/00:00:3a:00:00/40 tag 2 ncq 69632 in
[    4.024532]          res 40/00:40:40:52:4c/00:00:3a:00:00/40 Emask 0x10 (ATA bus error)
[    4.024536] ata2.00: status: { DRDY }
[    4.024539] ata2.00: failed command: READ FPDMA QUEUED
[    4.024546] ata2.00: cmd 60/70:18:40:41:4c/02:00:3a:00:00/40 tag 3 ncq 319488 in
[    4.024546]          res 40/00:40:40:52:4c/00:00:3a:00:00/40 Emask 0x10 (ATA bus error)
[    4.024550] ata2.00: status: { DRDY }
[    4.024553] ata2.00: failed command: READ FPDMA QUEUED
[    4.024561] ata2.00: cmd 60/d8:20:08:45:4c/03:00:3a:00:00/40 tag 4 ncq 503808 in
[    4.024561]          res 40/00:40:40:52:4c/00:00:3a:00:00/40 Emask 0x10 (ATA bus error)
[    4.024564] ata2.00: status: { DRDY }
[    4.024568] ata2.00: failed command: READ FPDMA QUEUED
[    4.024575] ata2.00: cmd 60/e8:28:60:49:4c/00:00:3a:00:00/40 tag 5 ncq 118784 in
[    4.024575]          res 40/00:40:40:52:4c/00:00:3a:00:00/40 Emask 0x10 (ATA bus error)
[    4.024579] ata2.00: status: { DRDY }
[    4.024582] ata2.00: failed command: READ FPDMA QUEUED
[    4.024589] ata2.00: cmd 60/00:30:50:4b:4c/04:00:3a:00:00/40 tag 6 ncq 524288 in
[    4.024589]          res 40/00:40:40:52:4c/00:00:3a:00:00/40 Emask 0x10 (ATA bus error)
[    4.024593] ata2.00: status: { DRDY }
[    4.024596] ata2.00: failed command: READ FPDMA QUEUED
[    4.024603] ata2.00: cmd 60/a8:38:50:4f:4c/01:00:3a:00:00/40 tag 7 ncq 217088 in
[    4.024603]          res 40/00:40:40:52:4c/00:00:3a:00:00/40 Emask 0x10 (ATA bus error)
[    4.024607] ata2.00: status: { DRDY }
[    4.024611] ata2.00: failed command: READ FPDMA QUEUED
[    4.024618] ata2.00: cmd 60/88:40:40:52:4c/01:00:3a:00:00/40 tag 8 ncq 200704 in
[    4.024618]          res 40/00:40:40:52:4c/00:00:3a:00:00/40 Emask 0x10 (ATA bus error)
[    4.024621] ata2.00: status: { DRDY }
[    4.024625] ata2.00: failed command: READ FPDMA QUEUED
[    4.024632] ata2.00: cmd 60/58:48:f8:53:4c/02:00:3a:00:00/40 tag 9 ncq 307200 in
[    4.024632]          res 40/00:40:40:52:4c/00:00:3a:00:00/40 Emask 0x10 (ATA bus error)
[    4.024636] ata2.00: status: { DRDY }
[    4.024639] ata2.00: failed command: READ FPDMA QUEUED
[    4.024647] ata2.00: cmd 60/a8:50:a8:56:4c/01:00:3a:00:00/40 tag 10 ncq 217088 in
[    4.024647]          res 40/00:40:40:52:4c/00:00:3a:00:00/40 Emask 0x10 (ATA bus error)
[    4.024651] ata2.00: status: { DRDY }
[    4.024654] ata2.00: failed command: READ FPDMA QUEUED
[    4.024661] ata2.00: cmd 60/00:58:70:58:4c/04:00:3a:00:00/40 tag 11 ncq 524288 in
[    4.024661]          res 40/00:40:40:52:4c/00:00:3a:00:00/40 Emask 0x10 (ATA bus error)
[    4.024665] ata2.00: status: { DRDY }
[    4.024669] ata2.00: failed command: READ FPDMA QUEUED
[    4.024676] ata2.00: cmd 60/10:60:70:5c:4c/00:00:3a:00:00/40 tag 12 ncq 8192 in
[    4.024676]          res 40/00:40:40:52:4c/00:00:3a:00:00/40 Emask 0x10 (ATA bus error)
[    4.024680] ata2.00: status: { DRDY }
[    4.024683] ata2.00: failed command: READ FPDMA QUEUED
[    4.024695] ata2.00: cmd 60/58:68:b8:5c:4c/03:00:3a:00:00/40 tag 13 ncq 438272 in
[    4.024695]          res 40/00:40:40:52:4c/00:00:3a:00:00/40 Emask 0x10 (ATA bus error)
[    4.024697] ata2.00: status: { DRDY }
[    4.024698] ata2.00: failed command: READ FPDMA QUEUED
[    4.024701] ata2.00: cmd 60/80:70:28:60:4c/01:00:3a:00:00/40 tag 14 ncq 196608 in
[    4.024701]          res 40/00:40:40:52:4c/00:00:3a:00:00/40 Emask 0x10 (ATA bus error)
[    4.024702] ata2.00: status: { DRDY }
[    4.024703] ata2.00: failed command: READ FPDMA QUEUED
[    4.024706] ata2.00: cmd 60/88:78:20:63:4c/00:00:3a:00:00/40 tag 15 ncq 69632 in
[    4.024706]          res 40/00:40:40:52:4c/00:00:3a:00:00/40 Emask 0x10 (ATA bus error)
[    4.024707] ata2.00: status: { DRDY }
[    4.024709] ata2.00: failed command: READ FPDMA QUEUED
[    4.024711] ata2.00: cmd 60/e8:80:00:64:4c/00:00:3a:00:00/40 tag 16 ncq 118784 in
[    4.024711]          res 40/00:40:40:52:4c/00:00:3a:00:00/40 Emask 0x10 (ATA bus error)
[    4.024713] ata2.00: status: { DRDY }
[    4.024714] ata2.00: failed command: READ FPDMA QUEUED
[    4.024717] ata2.00: cmd 60/78:88:80:72:4c/02:00:3a:00:00/40 tag 17 ncq 323584 in
[    4.024717]          res 40/00:40:40:52:4c/00:00:3a:00:00/40 Emask 0x10 (ATA bus error)
[    4.024718] ata2.00: status: { DRDY }
[    4.024719] ata2.00: failed command: READ FPDMA QUEUED
[    4.024722] ata2.00: cmd 60/b8:90:e0:75:4c/00:00:3a:00:00/40 tag 18 ncq 94208 in
[    4.024722]          res 40/00:40:40:52:4c/00:00:3a:00:00/40 Emask 0x10 (ATA bus error)
[    4.024724] ata2.00: status: { DRDY }
[    4.024725] ata2.00: failed command: READ FPDMA QUEUED
[    4.024728] ata2.00: cmd 60/b8:98:e0:76:4c/01:00:3a:00:00/40 tag 19 ncq 225280 in
[    4.024728]          res 40/00:40:40:52:4c/00:00:3a:00:00/40 Emask 0x10 (ATA bus error)
[    4.024729] ata2.00: status: { DRDY }
[    4.024730] ata2.00: failed command: READ FPDMA QUEUED
[    4.024733] ata2.00: cmd 60/90:a0:40:19:4c/03:00:3a:00:00/40 tag 20 ncq 466944 in
[    4.024733]          res 40/00:40:40:52:4c/00:00:3a:00:00/40 Emask 0x10 (ATA bus error)
[    4.024734] ata2.00: status: { DRDY }
[    4.024736] ata2.00: failed command: READ FPDMA QUEUED
[    4.024738] ata2.00: cmd 60/00:a8:10:1f:4c/01:00:3a:00:00/40 tag 21 ncq 131072 in
[    4.024738]          res 40/00:40:40:52:4c/00:00:3a:00:00/40 Emask 0x10 (ATA bus error)
[    4.024740] ata2.00: status: { DRDY }
[    4.024741] ata2.00: failed command: READ FPDMA QUEUED
[    4.024744] ata2.00: cmd 60/88:b0:88:24:4c/00:00:3a:00:00/40 tag 22 ncq 69632 in
[    4.024744]          res 40/00:40:40:52:4c/00:00:3a:00:00/40 Emask 0x10 (ATA bus error)
[    4.024745] ata2.00: status: { DRDY }
[    4.024746] ata2.00: failed command: READ FPDMA QUEUED
[    4.024751] ata2.00: cmd 60/00:b8:00:26:4c/04:00:3a:00:00/40 tag 23 ncq 524288 in
[    4.024751]          res 40/00:40:40:52:4c/00:00:3a:00:00/40 Emask 0x10 (ATA bus error)
[    4.024752] ata2.00: status: { DRDY }
[    4.024753] ata2.00: failed command: READ FPDMA QUEUED
[    4.024756] ata2.00: cmd 60/28:c0:00:2a:4c/00:00:3a:00:00/40 tag 24 ncq 20480 in
[    4.024756]          res 40/00:40:40:52:4c/00:00:3a:00:00/40 Emask 0x10 (ATA bus error)
[    4.024758] ata2.00: status: { DRDY }
[    4.024759] ata2.00: failed command: READ FPDMA QUEUED
[    4.024768] ata2.00: cmd 60/40:c8:b8:2a:4c/01:00:3a:00:00/40 tag 25 ncq 163840 in
[    4.024768]          res 40/00:40:40:52:4c/00:00:3a:00:00/40 Emask 0x10 (ATA bus error)
[    4.024769] ata2.00: status: { DRDY }
[    4.024770] ata2.00: failed command: READ FPDMA QUEUED
[    4.024773] ata2.00: cmd 60/48:d0:f8:2c:4c/01:00:3a:00:00/40 tag 26 ncq 167936 in
[    4.024773]          res 40/00:40:40:52:4c/00:00:3a:00:00/40 Emask 0x10 (ATA bus error)
[    4.024774] ata2.00: status: { DRDY }
[    4.024775] ata2.00: failed command: READ FPDMA QUEUED
[    4.024778] ata2.00: cmd 60/00:d8:68:2e:4c/02:00:3a:00:00/40 tag 27 ncq 262144 in
[    4.024778]          res 40/00:40:40:52:4c/00:00:3a:00:00/40 Emask 0x10 (ATA bus error)
[    4.024779] ata2.00: status: { DRDY }
[    4.024780] ata2.00: failed command: READ FPDMA QUEUED
[    4.024783] ata2.00: cmd 60/30:e0:f0:30:4c/03:00:3a:00:00/40 tag 28 ncq 417792 in
[    4.024783]          res 40/00:40:40:52:4c/00:00:3a:00:00/40 Emask 0x10 (ATA bus error)
[    4.024784] ata2.00: status: { DRDY }
[    4.024785] ata2.00: failed command: READ FPDMA QUEUED
[    4.024787] ata2.00: cmd 60/00:e8:40:35:4c/01:00:3a:00:00/40 tag 29 ncq 131072 in
[    4.024787]          res 40/00:40:40:52:4c/00:00:3a:00:00/40 Emask 0x10 (ATA bus error)
[    4.024789] ata2.00: status: { DRDY }
[    4.024790] ata2.00: failed command: READ FPDMA QUEUED
[    4.024792] ata2.00: cmd 60/00:f0:60:36:4c/01:00:3a:00:00/40 tag 30 ncq 131072 in
[    4.024792]          res 40/00:40:40:52:4c/00:00:3a:00:00/40 Emask 0x10 (ATA bus error)
[    4.024794] ata2.00: status: { DRDY }
[    4.024796] ata2: hard resetting link
[    4.516568] ata2: SATA link up 6.0 Gbps (SStatus 133 SControl 300)
[    4.516773] ata2.00: supports DRM functions and may not be fully accessible
[    4.516899] ata2.00: failed to get NCQ Send/Recv Log Emask 0x1
[    4.517120] ata2.00: supports DRM functions and may not be fully accessible
[    4.517169] ata2.00: failed to get NCQ Send/Recv Log Emask 0x1
[    4.517173] ata2.00: configured for UDMA/133
[    4.517204] ata2: EH complete
[    4.812362] EXT4-fs (sdb1): re-mounted. Opts: errors=remount-ro
[    4.863043] EXT4-fs (sdc1): mounted filesystem with ordered data mode. Opts: (null)
[    5.831233] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[    5.866209] FS-Cache: Loaded
[    5.872416] RPC: Registered named UNIX socket transport module.
[    5.872419] RPC: Registered udp transport module.
[    5.872420] RPC: Registered tcp transport module.
[    5.872422] RPC: Registered tcp NFSv4.1 backchannel transport module.
[    5.877329] systemd-udevd[586]: starting version 204
[    5.880108] FS-Cache: Netfs 'nfs' registered for caching
[    5.893299] Installing knfsd (copyright (C) 1996 okir@monad.swb.de).
[    5.906183] lp: driver loaded but no devices found
[    5.944680] piix4_smbus 0000:00:14.0: SMBus Host Controller at 0xb00, revision 0
[    5.944735] piix4_smbus 0000:00:14.0: Auxiliary SMBus Host Controller at 0xb20
[    5.945970] sp5100_tco: SP5100/SB800 TCO WatchDog Timer Driver v0.05
[    5.946032] sp5100_tco: PCI Revision ID: 0x42
[    5.946066] sp5100_tco: Using 0xfed80b00 for watchdog MMIO address
[    5.946078] sp5100_tco: Last reboot was not triggered by watchdog.
[    5.946190] sp5100_tco: initialized (0xffffc90011b7eb00). heartbeat=60 sec (nowayout=0)
[    5.955166] hda-intel 0000:00:14.2: Using LPIB position fix
[    5.959590] hda-intel 0000:00:14.2: Enable sync_write for stable communication
[    5.960851] ppdev: user-space parallel port driver
[    5.968707] SKU: Nid=0x1d sku_cfg=0x4007e629
[    5.968711] SKU: port_connectivity=0x1
[    5.968713] SKU: enable_pcbeep=0x0
[    5.968714] SKU: check_sum=0x00000007
[    5.968716] SKU: customization=0x000000e6
[    5.968717] SKU: external_amp=0x5
[    5.968718] SKU: platform_type=0x0
[    5.968719] SKU: swap=0x0
[    5.968720] SKU: override=0x1
[    5.969211] autoconfig: line_outs=4 (0x14/0x15/0x16/0x17/0x0) type:line
[    5.969213]    speaker_outs=0 (0x0/0x0/0x0/0x0/0x0)
[    5.969214]    hp_outs=1 (0x1b/0x0/0x0/0x0/0x0)
[    5.969215]    mono: mono_out=0x0
[    5.969216]    dig-out=0x11/0x1e
[    5.969217]    inputs:
[    5.969218]      Front Mic=0x19
[    5.969219]      Rear Mic=0x18
[    5.969221]      Line=0x1a
[    5.969222] realtek: No valid SSID, checking pincfg 0x4007e629 for NID 0x1d
[    5.969223] realtek: Enabling init ASM_ID=0xe629 CODEC_ID=10ec0892
[    5.973025] MCE: In-kernel MCE decoding enabled.
[    5.975304] EDAC MC: Ver: 3.0.0
[    5.977663] AMD64 EDAC driver v3.4.0
[    5.987399] init: idmapd-mounting (/mnt/nasdisk) main process (477) killed by TERM signal
[    6.000841] input: HDA ATI SB Front Headphone as /devices/pci0000:00/0000:00:14.2/sound/card0/input12
[    6.000976] input: HDA ATI SB Line Out Side as /devices/pci0000:00/0000:00:14.2/sound/card0/input11
[    6.001788] input: HDA ATI SB Line Out CLFE as /devices/pci0000:00/0000:00:14.2/sound/card0/input10
[    6.001898] input: HDA ATI SB Line Out Surround as /devices/pci0000:00/0000:00:14.2/sound/card0/input9
[    6.002035] input: HDA ATI SB Line Out Front as /devices/pci0000:00/0000:00:14.2/sound/card0/input8
[    6.002213] input: HDA ATI SB Line as /devices/pci0000:00/0000:00:14.2/sound/card0/input7
[    6.002352] input: HDA ATI SB Rear Mic as /devices/pci0000:00/0000:00:14.2/sound/card0/input6
[    6.002504] input: HDA ATI SB Front Mic as /devices/pci0000:00/0000:00:14.2/sound/card0/input5
[    6.002626] Bluetooth: Core ver 2.17
[    6.002642] NET: Registered protocol family 31
[    6.002644] Bluetooth: HCI device and connection manager initialized
[    6.002653] Bluetooth: HCI socket layer initialized
[    6.002656] Bluetooth: L2CAP socket layer initialized
[    6.002661] Bluetooth: SCO socket layer initialized
[    6.003233] hda-intel 0000:01:00.1: Handle VGA-switcheroo audio client
[    6.003236] hda-intel 0000:01:00.1: Using LPIB position fix
[    6.003258] EDAC amd64: DRAM ECC disabled.
[    6.003270] EDAC amd64: ECC disabled in the BIOS or no ECC capability, module will not load.
[    6.003270]  Either enable ECC checking or force module loading by setting 'ecc_enable_override'.
[    6.003270]  (Note that use of the override may cause unknown side effects.)
[    6.003278] snd_hda_intel 0000:01:00.1: irq 91 for MSI/MSI-X
[    6.005670] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[    6.005672] Bluetooth: BNEP filters: protocol multicast
[    6.005678] Bluetooth: BNEP socket layer initialized
[    6.007168] hda-intel 0000:01:00.1: Enable sync_write for stable communication
[    6.011565] HDMI ATI/AMD: no speaker allocation for ELD
[    6.011639] input: HDA ATI HDMI HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:02.0/0000:01:00.1/sound/card1/input13
[    6.023130] Bluetooth: RFCOMM TTY layer initialized
[    6.023141] Bluetooth: RFCOMM socket layer initialized
[    6.023147] Bluetooth: RFCOMM ver 1.11
[    6.069253] kvm: Nested Virtualization enabled
[    6.069258] kvm: Nested Paging enabled
[    6.094877] type=1400 audit(1413715998.870:2): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/cups/backend/cups-pdf" pid=927 comm="apparmor_parser"
[    6.094884] type=1400 audit(1413715998.870:3): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/sbin/cupsd" pid=927 comm="apparmor_parser"
[    6.094985] asus_wmi: ASUS WMI generic driver loaded
[    6.095271] type=1400 audit(1413715998.870:4): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/sbin/cupsd" pid=927 comm="apparmor_parser"
[    6.096503] asus_wmi: Initialization: 0x0
[    6.096536] asus_wmi: BIOS WMI version: 0.9
[    6.096613] asus_wmi: SFUN value: 0x0
[    6.097153] input: Eee PC WMI hotkeys as /devices/platform/eeepc-wmi/input/input14
[    6.098481] asus_wmi: Disabling ACPI video driver
[    6.106808] usbcore: registered new interface driver snd-usb-audio
[    6.137330] type=1400 audit(1413715998.910:5): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/sbin/dhclient" pid=953 comm="apparmor_parser"
[    6.137336] type=1400 audit(1413715998.910:6): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=953 comm="apparmor_parser"
[    6.137340] type=1400 audit(1413715998.910:7): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=953 comm="apparmor_parser"
[    6.137673] type=1400 audit(1413715998.910:8): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=953 comm="apparmor_parser"
[    6.137679] type=1400 audit(1413715998.910:9): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=953 comm="apparmor_parser"
[    6.137842] type=1400 audit(1413715998.910:10): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=953 comm="apparmor_parser"
[    6.138299] init: cups main process (932) killed by HUP signal
[    6.138308] init: cups main process ended, respawning
[    6.315235] init: failsafe main process (982) killed by TERM signal
[    6.342554] init: samba-ad-dc main process (1025) terminated with status 1
[    6.345547] init: Failed to obtain startpar-bridge instance: Unknown parameter: INSTANCE
[    6.378746] init: statd-mounting (/mnt/nasdisk) main process (479) killed by TERM signal
[    6.391430] NFS: Registering the id_resolver key type
[    6.391440] Key type id_resolver registered
[    6.391442] Key type id_legacy registered
[    6.432012] type=1400 audit(1413715999.206:11): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/bin/lxc-start" pid=1177 comm="apparmor_parser"
[    6.432856] type=1400 audit(1413715999.206:12): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/libvirt/virt-aa-helper" pid=1178 comm="apparmor_parser"
[    6.433336] type=1400 audit(1413715999.206:13): apparmor="STATUS" operation="profile_load" profile="unconfined" name="docker-default" pid=1170 comm="apparmor_parser"
[    6.434362] type=1400 audit(1413715999.206:14): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/sbin/cups-browsed" pid=1180 comm="apparmor_parser"
[    6.434440] type=1400 audit(1413715999.206:15): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/sbin/dhclient" pid=1173 comm="apparmor_parser"
[    6.434447] type=1400 audit(1413715999.206:16): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=1173 comm="apparmor_parser"
[    6.434451] type=1400 audit(1413715999.206:17): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=1173 comm="apparmor_parser"
[    6.434859] type=1400 audit(1413715999.206:18): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=1173 comm="apparmor_parser"
[    6.434865] type=1400 audit(1413715999.206:19): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=1173 comm="apparmor_parser"
[    6.435050] type=1400 audit(1413715999.206:20): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=1173 comm="apparmor_parser"
[    6.518442] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[    6.518631] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[    6.677158] ip_tables: (C) 2000-2006 Netfilter Core Team
[    6.689224] Bridge firewalling registered
[    6.712663] nf_conntrack version 0.5.0 (16384 buckets, 65536 max)
[    6.867433] vboxdrv: Found 8 processor cores.
[    6.868563] vboxdrv: fAsync=0 offMin=0x35c offMax=0x3dba
[    6.868654] vboxdrv: TSC mode is 'synchronous', kernel timer mode is 'normal'.
[    6.868655] vboxdrv: Successfully loaded version 4.3.18 (interface 0x001a0008).
[    6.949725] Ebtables v2.0 registered
[    6.963061] ip6_tables: (C) 2000-2006 Netfilter Core Team
[    7.078322] vboxpci: IOMMU not found (not registered)
[    7.455137] init: plymouth-upstart-bridge main process ended, respawning
[    7.460450] init: plymouth-upstart-bridge main process (1780) terminated with status 1
[    7.460459] init: plymouth-upstart-bridge main process ended, respawning
[    9.066717] IPv6: ADDRCONF(NETDEV_UP): virbr0: link is not ready
[   11.442373] retire_capture_urb: 1844 callbacks suppressed
[   11.539991] r8168: eth0: link up
[   11.540026] IPv6: ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   13.777025] RPC: AUTH_GSS upcall failed. Please check user daemon is running.
[   13.806267] aufs 3.13-20140303
[   13.819806] IPv6: ADDRCONF(NETDEV_UP): docker0: link is not ready
[   16.642624] retire_capture_urb: 976 callbacks suppressed
[   21.653668] retire_capture_urb: 2492 callbacks suppressed
[   36.219388] audit_printk_skb: 66 callbacks suppressed
[   36.219391] type=1400 audit(1413716028.293:80): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/cups/backend/cups-pdf" pid=3847 comm="apparmor_parser"
[   36.219397] type=1400 audit(1413716028.293:81): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/sbin/cupsd" pid=3847 comm="apparmor_parser"
[   36.219719] type=1400 audit(1413716028.293:82): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/sbin/cupsd" pid=3847 comm="apparmor_parser"
```

Notable messages from dmesg regarding ata2 (Samsung SSD):

```
[    1.758316] ata2: SATA max UDMA/133 abar m1024@0xfeb0b000 port 0xfeb0b180 irq 19
[    2.249391] ata2: SATA link up 6.0 Gbps (SStatus 133 SControl 300)
[    2.251238] ata2.00: supports DRM functions and may not be fully accessible
[    2.251361] ata2.00: failed to get NCQ Send/Recv Log Emask 0x1
[    2.251364] ata2.00: ATA-9: Samsung SSD 840 EVO 1TB, EXT0BB6Q, max UDMA/133
[    2.251366] ata2.00: 1953525168 sectors, multi 1: LBA48 NCQ (depth 31/32), AA
[    2.251592] ata2.00: supports DRM functions and may not be fully accessible
[    2.251651] ata2.00: failed to get NCQ Send/Recv Log Emask 0x1
[    2.251655] ata2.00: configured for UDMA/133
[    4.024472] ata2.00: exception Emask 0x10 SAct 0x7fffffff SErr 0x280100 action 0x6 frozen
[    4.024479] ata2.00: irq_stat 0x08000000, interface fatal error
[    4.024484] ata2: SError: { UnrecovData 10B8B BadCRC }
[    4.024490] ata2.00: failed command: READ FPDMA QUEUED
[    4.024500] ata2.00: cmd 60/88:00:80:38:4c/02:00:3a:00:00/40 tag 0 ncq 331776 in
[    4.024505] ata2.00: status: { DRDY }
[    4.024509] ata2.00: failed command: READ FPDMA QUEUED
[    4.024517] ata2.00: cmd 60/00:08:a8:3d:4c/01:00:3a:00:00/40 tag 1 ncq 131072 in
[    4.024521] ata2.00: status: { DRDY }
[    4.024524] ata2.00: failed command: READ FPDMA QUEUED
[    4.024532] ata2.00: cmd 60/88:10:d8:3f:4c/00:00:3a:00:00/40 tag 2 ncq 69632 in
[    4.024536] ata2.00: status: { DRDY }
[    4.024539] ata2.00: failed command: READ FPDMA QUEUED
[    4.024546] ata2.00: cmd 60/70:18:40:41:4c/02:00:3a:00:00/40 tag 3 ncq 319488 in
[    4.024550] ata2.00: status: { DRDY }
[    4.024553] ata2.00: failed command: READ FPDMA QUEUED
[    4.024561] ata2.00: cmd 60/d8:20:08:45:4c/03:00:3a:00:00/40 tag 4 ncq 503808 in
[    4.024564] ata2.00: status: { DRDY }
[    4.024568] ata2.00: failed command: READ FPDMA QUEUED
[    4.024575] ata2.00: cmd 60/e8:28:60:49:4c/00:00:3a:00:00/40 tag 5 ncq 118784 in
[    4.024579] ata2.00: status: { DRDY }
[    4.024582] ata2.00: failed command: READ FPDMA QUEUED
[    4.024589] ata2.00: cmd 60/00:30:50:4b:4c/04:00:3a:00:00/40 tag 6 ncq 524288 in
[    4.024593] ata2.00: status: { DRDY }
[    4.024596] ata2.00: failed command: READ FPDMA QUEUED
[    4.024603] ata2.00: cmd 60/a8:38:50:4f:4c/01:00:3a:00:00/40 tag 7 ncq 217088 in
[    4.024607] ata2.00: status: { DRDY }
[    4.024611] ata2.00: failed command: READ FPDMA QUEUED
[    4.024618] ata2.00: cmd 60/88:40:40:52:4c/01:00:3a:00:00/40 tag 8 ncq 200704 in
[    4.024621] ata2.00: status: { DRDY }
[    4.024625] ata2.00: failed command: READ FPDMA QUEUED
[    4.024632] ata2.00: cmd 60/58:48:f8:53:4c/02:00:3a:00:00/40 tag 9 ncq 307200 in
[    4.024636] ata2.00: status: { DRDY }
[    4.024639] ata2.00: failed command: READ FPDMA QUEUED
[    4.024647] ata2.00: cmd 60/a8:50:a8:56:4c/01:00:3a:00:00/40 tag 10 ncq 217088 in
[    4.024651] ata2.00: status: { DRDY }
[    4.024654] ata2.00: failed command: READ FPDMA QUEUED
[    4.024661] ata2.00: cmd 60/00:58:70:58:4c/04:00:3a:00:00/40 tag 11 ncq 524288 in
[    4.024665] ata2.00: status: { DRDY }
[    4.024669] ata2.00: failed command: READ FPDMA QUEUED
[    4.024676] ata2.00: cmd 60/10:60:70:5c:4c/00:00:3a:00:00/40 tag 12 ncq 8192 in
[    4.024680] ata2.00: status: { DRDY }
[    4.024683] ata2.00: failed command: READ FPDMA QUEUED
[    4.024695] ata2.00: cmd 60/58:68:b8:5c:4c/03:00:3a:00:00/40 tag 13 ncq 438272 in
[    4.024697] ata2.00: status: { DRDY }
[    4.024698] ata2.00: failed command: READ FPDMA QUEUED
[    4.024701] ata2.00: cmd 60/80:70:28:60:4c/01:00:3a:00:00/40 tag 14 ncq 196608 in
[    4.024702] ata2.00: status: { DRDY }
[    4.024703] ata2.00: failed command: READ FPDMA QUEUED
[    4.024706] ata2.00: cmd 60/88:78:20:63:4c/00:00:3a:00:00/40 tag 15 ncq 69632 in
[    4.024707] ata2.00: status: { DRDY }
[    4.024709] ata2.00: failed command: READ FPDMA QUEUED
[    4.024711] ata2.00: cmd 60/e8:80:00:64:4c/00:00:3a:00:00/40 tag 16 ncq 118784 in
[    4.024713] ata2.00: status: { DRDY }
[    4.024714] ata2.00: failed command: READ FPDMA QUEUED
[    4.024717] ata2.00: cmd 60/78:88:80:72:4c/02:00:3a:00:00/40 tag 17 ncq 323584 in
[    4.024718] ata2.00: status: { DRDY }
[    4.024719] ata2.00: failed command: READ FPDMA QUEUED
[    4.024722] ata2.00: cmd 60/b8:90:e0:75:4c/00:00:3a:00:00/40 tag 18 ncq 94208 in
[    4.024724] ata2.00: status: { DRDY }
[    4.024725] ata2.00: failed command: READ FPDMA QUEUED
[    4.024728] ata2.00: cmd 60/b8:98:e0:76:4c/01:00:3a:00:00/40 tag 19 ncq 225280 in
[    4.024729] ata2.00: status: { DRDY }
[    4.024730] ata2.00: failed command: READ FPDMA QUEUED
[    4.024733] ata2.00: cmd 60/90:a0:40:19:4c/03:00:3a:00:00/40 tag 20 ncq 466944 in
[    4.024734] ata2.00: status: { DRDY }
[    4.024736] ata2.00: failed command: READ FPDMA QUEUED
[    4.024738] ata2.00: cmd 60/00:a8:10:1f:4c/01:00:3a:00:00/40 tag 21 ncq 131072 in
[    4.024740] ata2.00: status: { DRDY }
[    4.024741] ata2.00: failed command: READ FPDMA QUEUED
[    4.024744] ata2.00: cmd 60/88:b0:88:24:4c/00:00:3a:00:00/40 tag 22 ncq 69632 in
[    4.024745] ata2.00: status: { DRDY }
[    4.024746] ata2.00: failed command: READ FPDMA QUEUED
[    4.024751] ata2.00: cmd 60/00:b8:00:26:4c/04:00:3a:00:00/40 tag 23 ncq 524288 in
[    4.024752] ata2.00: status: { DRDY }
[    4.024753] ata2.00: failed command: READ FPDMA QUEUED
[    4.024756] ata2.00: cmd 60/28:c0:00:2a:4c/00:00:3a:00:00/40 tag 24 ncq 20480 in
[    4.024758] ata2.00: status: { DRDY }
[    4.024759] ata2.00: failed command: READ FPDMA QUEUED
[    4.024768] ata2.00: cmd 60/40:c8:b8:2a:4c/01:00:3a:00:00/40 tag 25 ncq 163840 in
[    4.024769] ata2.00: status: { DRDY }
[    4.024770] ata2.00: failed command: READ FPDMA QUEUED
[    4.024773] ata2.00: cmd 60/48:d0:f8:2c:4c/01:00:3a:00:00/40 tag 26 ncq 167936 in
[    4.024774] ata2.00: status: { DRDY }
[    4.024775] ata2.00: failed command: READ FPDMA QUEUED
[    4.024778] ata2.00: cmd 60/00:d8:68:2e:4c/02:00:3a:00:00/40 tag 27 ncq 262144 in
[    4.024779] ata2.00: status: { DRDY }
[    4.024780] ata2.00: failed command: READ FPDMA QUEUED
[    4.024783] ata2.00: cmd 60/30:e0:f0:30:4c/03:00:3a:00:00/40 tag 28 ncq 417792 in
[    4.024784] ata2.00: status: { DRDY }
[    4.024785] ata2.00: failed command: READ FPDMA QUEUED
[    4.024787] ata2.00: cmd 60/00:e8:40:35:4c/01:00:3a:00:00/40 tag 29 ncq 131072 in
[    4.024789] ata2.00: status: { DRDY }
[    4.024790] ata2.00: failed command: READ FPDMA QUEUED
[    4.024792] ata2.00: cmd 60/00:f0:60:36:4c/01:00:3a:00:00/40 tag 30 ncq 131072 in
[    4.024794] ata2.00: status: { DRDY }
[    4.024796] ata2: hard resetting link
[    4.516568] ata2: SATA link up 6.0 Gbps (SStatus 133 SControl 300)
[    4.516773] ata2.00: supports DRM functions and may not be fully accessible
[    4.516899] ata2.00: failed to get NCQ Send/Recv Log Emask 0x1
[    4.517120] ata2.00: supports DRM functions and may not be fully accessible
[    4.517169] ata2.00: failed to get NCQ Send/Recv Log Emask 0x1
[    4.517173] ata2.00: configured for UDMA/133
[    4.517204] ata2: EH complete

```

Does anyone have any idea what's going on here?

---

### Post by oldfred on 2014-10-19
Did you see this on read performance issues? 
[http://www.anandtech.com/show/8550/samsung-acknowledges-the-ssd-840-evo-read-performance-bug-fix-is-on-the-way](http://www.anandtech.com/show/8550/samsung-acknowledges-the-ssd-840-evo-read-performance-bug-fix-is-on-the-way)

Do you have trim configured correctly?
Is system booting in UEFI or BIOS boot mode?

---

### Post by runesvend on 2014-10-20
> **oldfred said:**
> Did you see this on read performance issues? 
[http://www.anandtech.com/show/8550/samsung-acknowledges-the-ssd-840-evo-read-performance-bug-fix-is-on-the-way](http://www.anandtech.com/show/8550/samsung-acknowledges-the-ssd-840-evo-read-performance-bug-fix-is-on-the-way)

Here's the benchmark for my Samsung SSD:

[ATTACH=CONFIG]257392[/ATTACH]

So it seems I am not affected by this yet.

But I would kill for low performance, as long as the drive is bootable from a cold bootup.

> 
Do you have trim configured correctly?

Where would I configure that? I assume I've turned it on in the BIOS.

These are the options the various partitions are mounted with:

```
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sdd2 during installation
UUID=6ddf5dd3-db41-4a1d-99b6-e470a40a4928 /               ext4    errors=remount-ro 0       1
# /home was on /dev/sdd1 during installation
#Sandisk
UUID=5250b4cd-738d-4768-96ec-d075e78d7524 /home           ext4    defaults        0       2
#Samsung
#UUID=b619852e-b350-4d95-9491-a4644e182b00 /home           ext4    defaults        0       2

#/tmp in RAM
tmpfs /tmp tmpfs defaults,noatime,nosuid,nodev,mode=1777 0 0

```

Here I am running Ubuntu from my old SSD (5250b4cd-738d-4768-96ec-d075e78d7524) instead of the Samsung partition (b619852e-b350-4d95-9491-a4644e182b00).


> Is system booting in UEFI or BIOS boot mode?
BIOS.

---

### Post by oldfred on 2014-10-20
For trim to work you have to have AHCI on in BIOS.
When I turned that on in my BIOS XP stopped working, which then was a good thing as it forced me to finally give up on it a couple of years ago. With newer Windows drivers for AHCI need to be installed or may already be installed.

I orginally followed this advice and added discard in fstab, but since changed to a cron task with fstrim. With 14.04 it may add a weekly task automatically for some brands of SSD.

 You still need discard for trim and noatime to reduce writes. You can also use ext4 but turn journal off. I think that was about all I actually did. If using any newer version of gparted you should have alignment or first partition starts at sector 2048 and all partition starts are divisible by 8.
Info on trim and ext4 without journal, ext2 does not support trim, with newer SSDs realtime a reasonalbe alternative to noatime and works with some apps that need timestamps like mutt

      
 Trim in 14.04
[https://launchpad.net/ubuntu/+source/util-linux/2.20.1-5.1ubuntu11](https://launchpad.net/ubuntu/+source/util-linux/2.20.1-5.1ubuntu11)
HOWTO: Check If TRIM On Ext4 Is Enabled And Working On Ubuntu And Other Distributions
[http://sites.google.com/site/lightrush/random-1/checkiftrimonext4isenabledandworking](http://sites.google.com/site/lightrush/random-1/checkiftrimonext4isenabledandworking)

This is what I changed to.

 Shows both discard & fstrim methods for trim
[http://www.webupd8.org/2013/01/enable-trim-on-ssd-solid-state-drives.html](http://www.webupd8.org/2013/01/enable-trim-on-ssd-solid-state-drives.html)
gksu gedit /etc/cron.daily/trim
sudo chmod +x /etc/cron.daily/trim

   #!/bin/sh
# trim
LOG=/var/log/trim.log
echo "*** $(date -R) ***" >> $LOG
fstrim -v / >> $LOG
# fstrim -v /home >> $LOG

Manually running it:
   fred@fred-Precise:~$ sudo fstrim -v /
/: 23267893248 bytes were trimmed

---

### Post by WinEunuchs2Unix on 2014-10-20
I noticed your drives all load up about the same time:

```

[    2.249312] ata4: SATA link up 6.0 Gbps (SStatus 133 SControl 300)
[    2.249369] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    2.249391] ata2: SATA link up 6.0 Gbps (SStatus 133 SControl 300)
[    2.250309] ata4.00: ATA-8: SanDisk SDSSDH2256G, X2306RL, max UDMA/133
[    2.250312] ata4.00: 500118192 sectors, multi 1: LBA48 NCQ (depth 31/32), AA
[    2.251238] ata2.00: supports DRM functions and may not be fully accessible
[    2.251361] ata2.00: failed to get NCQ Send/Recv Log Emask 0x1
[    2.251364] ata2.00: ATA-9: Samsung SSD 840 EVO 1TB, EXT0BB6Q, max UDMA/133
[    2.251366] ata2.00: 1953525168 sectors, multi 1: LBA48 NCQ (depth 31/32), AA
[    2.251458] ata4.00: configured for UDMA/133
[    2.251592] ata2.00: supports DRM functions and may not be fully accessible
[    2.251651] ata2.00: failed to get NCQ Send/Recv Log Emask 0x1
[    2.251655] ata2.00: configured for UDMA/133
[    2.255717] ata1.00: ATA-8: WDC WD20EARS-00S8B1, 80.00A80, max UDMA/133
[    2.255719] ata1.00: 3907029168 sectors, multi 16: LBA48 NCQ (depth 31/32), AA [COLOR=#000000][FONT=Ubuntu Mono][    2.261610] ata1.00: configured for UDMA/133
[/FONT][/COLOR]
```

You do have UUID`s setup in `éetcévstab and UUID`s are not disabled in grub rightÉ

sorry for the funny characters it`s time to reboot Windows 7 again.

---

### Post by runesvend on 2014-10-21
> **WinEunuchs2Unix said:**
> I noticed your drives all load up about the same time:

```

[    2.249312] ata4: SATA link up 6.0 Gbps (SStatus 133 SControl 300)
[    2.249369] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    2.249391] ata2: SATA link up 6.0 Gbps (SStatus 133 SControl 300)
[    2.250309] ata4.00: ATA-8: SanDisk SDSSDH2256G, X2306RL, max UDMA/133
[    2.250312] ata4.00: 500118192 sectors, multi 1: LBA48 NCQ (depth 31/32), AA
[    2.251238] ata2.00: supports DRM functions and may not be fully accessible
[    2.251361] ata2.00: failed to get NCQ Send/Recv Log Emask 0x1
[    2.251364] ata2.00: ATA-9: Samsung SSD 840 EVO 1TB, EXT0BB6Q, max UDMA/133
[    2.251366] ata2.00: 1953525168 sectors, multi 1: LBA48 NCQ (depth 31/32), AA
[    2.251458] ata4.00: configured for UDMA/133
[    2.251592] ata2.00: supports DRM functions and may not be fully accessible
[    2.251651] ata2.00: failed to get NCQ Send/Recv Log Emask 0x1
[    2.251655] ata2.00: configured for UDMA/133
[    2.255717] ata1.00: ATA-8: WDC WD20EARS-00S8B1, 80.00A80, max UDMA/133
[    2.255719] ata1.00: 3907029168 sectors, multi 16: LBA48 NCQ (depth 31/32), AA [COLOR=#000000][FONT=Ubuntu Mono][    2.261610] ata1.00: configured for UDMA/133
[/FONT][/COLOR]
```

You do have UUID`s setup in `éetcévstab and UUID`s are not disabled in grub rightÉ

Yes, UUIDs in /etc/fstab. I'm running Ubuntu with an fstab that contains UUIDs now, so I guess they aren't disabled in GRUB, or I wouldn't be able to boot.

---

### Post by tgalati4 on 2014-10-21
I would check your power supply.  Whenever I have a piece of hardware that requires a "double-pump" to get started, that usually means the power supply is either failing, or not rated to provide enough current that your system requires.  Measure the 12VDC power during startup.  If it sags more than 10%, then that would be your answer.

---

### Post by runesvend on 2014-10-21
> **tgalati4 said:**
> I would check your power supply.  Whenever I have a piece of hardware that requires a "double-pump" to get started, that usually means the power supply is either failing, or not rated to provide enough current that your system requires.  Measure the 12VDC power during startup.  If it sags more than 10%, then that would be your answer.

This makes sense theoretically. The probability of me having two SSDs from two different manufacturers displaying the exact same symptoms is small.

I'm not sure I know to to measure the 12VDC power, but I can plug my PC in a kill-a-wat and see if it hits the limit of my PSU (FSP Zen 400w).

I'll report back.

---

### Post by runesvend on 2014-10-21
I just plugged in the kill-a-watt. It never gets above 223W. But I've just ordered a new PSU anyway. The one I have currently is over six years old. I'll try the new one and send it back if it doesn't fix the problem.

---

### Post by Scooby-2 on 2014-10-23
I don't think it's your power supply - you would be having other problems if so. It's your BIOS or setup. Make sure you have the latest BIOS and swap the HDD and SSD. I had the same problem in my laptop and I had to put the HDD in the DVD caddy and the SSD in the hard drive bay. Hey presto, solved.

Please advise if this fixes your problem too.

---

### Post by runesvend on 2014-10-26
> **tgalati4 said:**
> I would check your power supply.  Whenever I have a piece of hardware that requires a "double-pump" to get started, that usually means the power supply is either failing, or not rated to provide enough current that your system requires.  Measure the 12VDC power during startup.  If it sags more than 10%, then that would be your answer.
Looks like you were right, tgalati4.

I just replaced my six year old Fortron ZEN FSP-400 with a brand new Seasonic P-460FL2 F3 (460W) PSU. Just booted it up from cold today, and everything worked fine. All my bootable hard drives were recognized immediately by the BIOS. Yay! :)

Here's the dmesg with the new PSU installed, in case someone can figure out something useful from it:

```
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Initializing cgroup subsys cpuacct
[    0.000000] Linux version 3.13.0-37-generic (buildd@kapok) (gcc version 4.8.2 (Ubuntu 4.8.2-19ubuntu1) ) #64-Ubuntu SMP Mon Sep 22 21:28:38 UTC 2014 (Ubuntu 3.13.0-37.64-generic 3.13.11.7)
[    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-3.13.0-37-generic root=UUID=675f4bd2-1144-410d-9a88-bcb20b920581 ro quiet splash nomdmonddf nomdmonisw nomdmonddf nomdmonisw nomdmonddf nomdmonisw vt.handoff=7
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   Centaur CentaurHauls
[    0.000000] e820: BIOS-provided physical RAM map:
[    0.000000] BIOS-e820: [mem 0x0000000000000000-0x000000000009e7ff] usable
[    0.000000] BIOS-e820: [mem 0x000000000009e800-0x000000000009ffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000000e0000-0x00000000000fffff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000000100000-0x00000000ba867fff] usable
[    0.000000] BIOS-e820: [mem 0x00000000ba868000-0x00000000bab43fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000bab44000-0x00000000bab53fff] ACPI data
[    0.000000] BIOS-e820: [mem 0x00000000bab54000-0x00000000bb959fff] ACPI NVS
[    0.000000] BIOS-e820: [mem 0x00000000bb95a000-0x00000000bca36fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000bca37000-0x00000000bca37fff] usable
[    0.000000] BIOS-e820: [mem 0x00000000bca38000-0x00000000bcc3dfff] ACPI NVS
[    0.000000] BIOS-e820: [mem 0x00000000bcc3e000-0x00000000bd082fff] usable
[    0.000000] BIOS-e820: [mem 0x00000000bd083000-0x00000000bd7f3fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000bd7f4000-0x00000000bd7fffff] usable
[    0.000000] BIOS-e820: [mem 0x00000000fec00000-0x00000000fec00fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fec10000-0x00000000fec10fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fec20000-0x00000000fec20fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fed00000-0x00000000fed00fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fed61000-0x00000000fed70fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fed80000-0x00000000fed8ffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fef00000-0x00000000ffffffff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000100001000-0x000000043effffff] usable
[    0.000000] NX (Execute Disable) protection: active
[    0.000000] SMBIOS 2.7 present.
[    0.000000] DMI: To be filled by O.E.M. To be filled by O.E.M./M5A97 EVO R2.0, BIOS 2201 11/25/2013
[    0.000000] e820: update [mem 0x00000000-0x00000fff] usable ==> reserved
[    0.000000] e820: remove [mem 0x000a0000-0x000fffff] usable
[    0.000000] No AGP bridge found
[    0.000000] e820: last_pfn = 0x43f000 max_arch_pfn = 0x400000000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF write-through
[    0.000000]   C0000-CFFFF write-protect
[    0.000000]   D0000-EBFFF uncachable
[    0.000000]   EC000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000000 mask FFFF80000000 write-back
[    0.000000]   1 base 000080000000 mask FFFFC0000000 write-back
[    0.000000]   2 base 0000BD800000 mask FFFFFF800000 uncachable
[    0.000000]   3 base 0000BE000000 mask FFFFFE000000 uncachable
[    0.000000]   4 disabled
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] TOM2: 000000043f000000 aka 17392M
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] original variable MTRRs
[    0.000000] reg 0, base: 0GB, range: 2GB, type WB
[    0.000000] reg 1, base: 2GB, range: 1GB, type WB
[    0.000000] reg 2, base: 3032MB, range: 8MB, type UC
[    0.000000] reg 3, base: 3040MB, range: 32MB, type UC
[    0.000000] total RAM covered: 3032M
[    0.000000] Found optimal setting for mtrr clean up
[    0.000000]  gran_size: 64K 	chunk_size: 64M 	num_reg: 4  	lose cover RAM: 0G
[    0.000000] New variable MTRRs
[    0.000000] reg 0, base: 0GB, range: 2GB, type WB
[    0.000000] reg 1, base: 2GB, range: 1GB, type WB
[    0.000000] reg 2, base: 3032MB, range: 8MB, type UC
[    0.000000] reg 3, base: 3040MB, range: 32MB, type UC
[    0.000000] e820: update [mem 0xbd800000-0xffffffff] usable ==> reserved
[    0.000000] e820: last_pfn = 0xbd800 max_arch_pfn = 0x400000000
[    0.000000] Scanning 1 areas for low memory corruption
[    0.000000] Base memory trampoline at [ffff880000098000] 98000 size 24576
[    0.000000] Using GB pages for direct mapping
[    0.000000] init_memory_mapping: [mem 0x00000000-0x000fffff]
[    0.000000]  [mem 0x00000000-0x000fffff] page 4k
[    0.000000] BRK [0x01fe1000, 0x01fe1fff] PGTABLE
[    0.000000] BRK [0x01fe2000, 0x01fe2fff] PGTABLE
[    0.000000] BRK [0x01fe3000, 0x01fe3fff] PGTABLE
[    0.000000] init_memory_mapping: [mem 0x43ee00000-0x43effffff]
[    0.000000]  [mem 0x43ee00000-0x43effffff] page 2M
[    0.000000] BRK [0x01fe4000, 0x01fe4fff] PGTABLE
[    0.000000] init_memory_mapping: [mem 0x43c000000-0x43edfffff]
[    0.000000]  [mem 0x43c000000-0x43edfffff] page 2M
[    0.000000] init_memory_mapping: [mem 0x400000000-0x43bffffff]
[    0.000000]  [mem 0x400000000-0x43bffffff] page 2M
[    0.000000] init_memory_mapping: [mem 0x00100000-0xba867fff]
[    0.000000]  [mem 0x00100000-0x001fffff] page 4k
[    0.000000]  [mem 0x00200000-0x3fffffff] page 2M
[    0.000000]  [mem 0x40000000-0x7fffffff] page 1G
[    0.000000]  [mem 0x80000000-0xba7fffff] page 2M
[    0.000000]  [mem 0xba800000-0xba867fff] page 4k
[    0.000000] init_memory_mapping: [mem 0xbca37000-0xbca37fff]
[    0.000000]  [mem 0xbca37000-0xbca37fff] page 4k
[    0.000000] BRK [0x01fe5000, 0x01fe5fff] PGTABLE
[    0.000000] init_memory_mapping: [mem 0xbcc3e000-0xbd082fff]
[    0.000000]  [mem 0xbcc3e000-0xbcdfffff] page 4k
[    0.000000]  [mem 0xbce00000-0xbcffffff] page 2M
[    0.000000]  [mem 0xbd000000-0xbd082fff] page 4k
[    0.000000] BRK [0x01fe6000, 0x01fe6fff] PGTABLE
[    0.000000] init_memory_mapping: [mem 0xbd7f4000-0xbd7fffff]
[    0.000000]  [mem 0xbd7f4000-0xbd7fffff] page 4k
[    0.000000] init_memory_mapping: [mem 0x100001000-0x3ffffffff]
[    0.000000]  [mem 0x100001000-0x1001fffff] page 4k
[    0.000000]  [mem 0x100200000-0x13fffffff] page 2M
[    0.000000]  [mem 0x140000000-0x3ffffffff] page 1G
[    0.000000] RAMDISK: [mem 0x34a6c000-0x3652dfff]
[    0.000000] ACPI: RSDP 00000000000f0490 000024 (v02 ALASKA)
[    0.000000] ACPI: XSDT 00000000bab4b070 000054 (v01 ALASKA    A M I 01072009 AMI  00010013)
[    0.000000] ACPI: FACP 00000000bab52260 00010C (v05 ALASKA    A M I 01072009 AMI  00010013)
[    0.000000] ACPI BIOS Warning (bug): Optional FADT field Pm2ControlBlock has zero address or length: 0x0000000000000000/0x1 (20131115/tbfadt-603)
[    0.000000] ACPI: DSDT 00000000bab4b158 007101 (v02 ALASKA    A M I 00000000 INTL 20051117)
[    0.000000] ACPI: FACS 00000000bb954f80 000040
[    0.000000] ACPI: APIC 00000000bab52370 00009E (v03 ALASKA    A M I 01072009 AMI  00010013)
[    0.000000] ACPI: FPDT 00000000bab52410 000044 (v01 ALASKA    A M I 01072009 AMI  00010013)
[    0.000000] ACPI: MCFG 00000000bab52458 00003C (v01 ALASKA    A M I 01072009 MSFT 00010013)
[    0.000000] ACPI: HPET 00000000bab52498 000038 (v01 ALASKA    A M I 01072009 AMI  00000005)
[    0.000000] ACPI: SSDT 00000000bab52528 001714 (v01 AMD    POWERNOW 00000001 AMD  00000001)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at [mem 0x0000000000000000-0x000000043effffff]
[    0.000000] Initmem setup node 0 [mem 0x00000000-0x43effffff]
[    0.000000]   NODE_DATA [mem 0x43eff5000-0x43eff9fff]
[    0.000000]  [ffffea0000000000-ffffea0010ffffff] PMD -> [ffff88042e600000-ffff88043e5fffff] on node 0
[    0.000000] Zone ranges:
[    0.000000]   DMA      [mem 0x00001000-0x00ffffff]
[    0.000000]   DMA32    [mem 0x01000000-0xffffffff]
[    0.000000]   Normal   [mem 0x100000000-0x43effffff]
[    0.000000] Movable zone start for each node
[    0.000000] Early memory node ranges
[    0.000000]   node   0: [mem 0x00001000-0x0009dfff]
[    0.000000]   node   0: [mem 0x00100000-0xba867fff]
[    0.000000]   node   0: [mem 0xbca37000-0xbca37fff]
[    0.000000]   node   0: [mem 0xbcc3e000-0xbd082fff]
[    0.000000]   node   0: [mem 0xbd7f4000-0xbd7fffff]
[    0.000000]   node   0: [mem 0x100001000-0x43effffff]
[    0.000000] On node 0 totalpages: 4168790
[    0.000000]   DMA zone: 64 pages used for memmap
[    0.000000]   DMA zone: 21 pages reserved
[    0.000000]   DMA zone: 3997 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 11891 pages used for memmap
[    0.000000]   DMA32 zone: 761018 pages, LIFO batch:31
[    0.000000]   Normal zone: 53184 pages used for memmap
[    0.000000]   Normal zone: 3403775 pages, LIFO batch:31
[    0.000000] ACPI: PM-Timer IO Port: 0x808
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x10] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x11] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x12] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x13] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x05] lapic_id[0x14] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x06] lapic_id[0x15] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x07] lapic_id[0x16] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x08] lapic_id[0x17] enabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0xff] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x09] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 9, version 33, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: IOAPIC (id[0x0a] address[0xfec20000] gsi_base[24])
[    0.000000] IOAPIC[1]: apic_id 10, version 33, address 0xfec20000, GSI 24-55
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 low level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x43538210 base: 0xfed00000
[    0.000000] smpboot: Allowing 8 CPUs, 0 hotplug CPUs
[    0.000000] nr_irqs_gsi: 72
[    0.000000] PM: Registered nosave memory: [mem 0x0009e000-0x0009efff]
[    0.000000] PM: Registered nosave memory: [mem 0x0009f000-0x0009ffff]
[    0.000000] PM: Registered nosave memory: [mem 0x000a0000-0x000dffff]
[    0.000000] PM: Registered nosave memory: [mem 0x000e0000-0x000fffff]
[    0.000000] PM: Registered nosave memory: [mem 0xba868000-0xbab43fff]
[    0.000000] PM: Registered nosave memory: [mem 0xbab44000-0xbab53fff]
[    0.000000] PM: Registered nosave memory: [mem 0xbab54000-0xbb959fff]
[    0.000000] PM: Registered nosave memory: [mem 0xbb95a000-0xbca36fff]
[    0.000000] PM: Registered nosave memory: [mem 0xbca38000-0xbcc3dfff]
[    0.000000] PM: Registered nosave memory: [mem 0xbd083000-0xbd7f3fff]
[    0.000000] PM: Registered nosave memory: [mem 0xbd800000-0xfebfffff]
[    0.000000] PM: Registered nosave memory: [mem 0xfec00000-0xfec00fff]
[    0.000000] PM: Registered nosave memory: [mem 0xfec01000-0xfec0ffff]
[    0.000000] PM: Registered nosave memory: [mem 0xfec10000-0xfec10fff]
[    0.000000] PM: Registered nosave memory: [mem 0xfec11000-0xfec1ffff]
[    0.000000] PM: Registered nosave memory: [mem 0xfec20000-0xfec20fff]
[    0.000000] PM: Registered nosave memory: [mem 0xfec21000-0xfecfffff]
[    0.000000] PM: Registered nosave memory: [mem 0xfed00000-0xfed00fff]
[    0.000000] PM: Registered nosave memory: [mem 0xfed01000-0xfed60fff]
[    0.000000] PM: Registered nosave memory: [mem 0xfed61000-0xfed70fff]
[    0.000000] PM: Registered nosave memory: [mem 0xfed71000-0xfed7ffff]
[    0.000000] PM: Registered nosave memory: [mem 0xfed80000-0xfed8ffff]
[    0.000000] PM: Registered nosave memory: [mem 0xfed90000-0xfeefffff]
[    0.000000] PM: Registered nosave memory: [mem 0xfef00000-0xffffffff]
[    0.000000] PM: Registered nosave memory: [mem 0x100000000-0x100000fff]
[    0.000000] e820: [mem 0xbd800000-0xfebfffff] available for PCI devices
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] setup_percpu: NR_CPUS:256 nr_cpumask_bits:256 nr_cpu_ids:8 nr_node_ids:1
[    0.000000] PERCPU: Embedded 29 pages/cpu @ffff88043ec00000 s86400 r8192 d24192 u262144
[    0.000000] pcpu-alloc: s86400 r8192 d24192 u262144 alloc=1*2097152
[    0.000000] pcpu-alloc: [0] 0 1 2 3 4 5 6 7 
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 4103630
[    0.000000] Policy zone: Normal
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.13.0-37-generic root=UUID=675f4bd2-1144-410d-9a88-bcb20b920581 ro quiet splash nomdmonddf nomdmonisw nomdmonddf nomdmonisw nomdmonddf nomdmonisw vt.handoff=7
[    0.000000] PID hash table entries: 4096 (order: 3, 32768 bytes)
[    0.000000] xsave: enabled xstate_bv 0x7, cntxt size 0x340
[    0.000000] Checking aperture...
[    0.000000] No AGP bridge found
[    0.000000] Node 0: aperture @ 0 size 32 MB
[    0.000000] Your BIOS doesn't leave a aperture memory hole
[    0.000000] Please enable the IOMMU option in the BIOS setup
[    0.000000] This costs you 64 MB of RAM
[    0.000000] Mapping aperture over 65536 KB of RAM @ b0000000
[    0.000000] PM: Registered nosave memory: [mem 0xb0000000-0xb3ffffff]
[    0.000000] Memory: 16236432K/16675160K available (7375K kernel code, 1144K rwdata, 3404K rodata, 1336K init, 1444K bss, 438728K reserved)
[    0.000000] SLUB: HWalign=64, Order=0-3, MinObjects=0, CPUs=8, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000] 	RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000] 	RCU restricting CPUs from NR_CPUS=256 to nr_cpu_ids=8.
[    0.000000] 	Offload RCU callbacks from all CPUs
[    0.000000] 	Offload RCU callbacks from CPUs: 0-7.
[    0.000000] NR_IRQS:16640 nr_irqs:1288 16
[    0.000000] spurious 8259A interrupt: IRQ7.
[    0.000000] Console: colour dummy device 80x25
[    0.000000] console [tty0] enabled
[    0.000000] allocated 67108864 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] hpet clockevent registered
[    0.000000] tsc: Fast TSC calibration using PIT
[    0.004000] tsc: Detected 3511.946 MHz processor
[    0.000003] Calibrating delay loop (skipped), value calculated using timer frequency.. 7023.89 BogoMIPS (lpj=14047784)
[    0.000006] pid_max: default: 32768 minimum: 301
[    0.000032] Security Framework initialized
[    0.000049] AppArmor: AppArmor initialized
[    0.000050] Yama: becoming mindful.
[    0.001163] Dentry cache hash table entries: 2097152 (order: 12, 16777216 bytes)
[    0.005227] Inode-cache hash table entries: 1048576 (order: 11, 8388608 bytes)
[    0.007013] Mount-cache hash table entries: 32768 (order: 6, 262144 bytes)
[    0.007033] Mountpoint-cache hash table entries: 32768 (order: 6, 262144 bytes)
[    0.007293] Initializing cgroup subsys memory
[    0.007298] Initializing cgroup subsys devices
[    0.007300] Initializing cgroup subsys freezer
[    0.007301] Initializing cgroup subsys blkio
[    0.007303] Initializing cgroup subsys perf_event
[    0.007305] Initializing cgroup subsys hugetlb
[    0.007322] tseg: 00bd800000
[    0.007324] CPU: Physical Processor ID: 0
[    0.007325] CPU: Processor Core ID: 0
[    0.007327] mce: CPU supports 7 MCE banks
[    0.007333] LVT offset 1 assigned for vector 0xf9
[    0.007338] Last level iTLB entries: 4KB 512, 2MB 1024, 4MB 512
[    0.007338] Last level dTLB entries: 4KB 1024, 2MB 1024, 4MB 512
[    0.007338] tlb_flushall_shift: 5
[    0.007421] Freeing SMP alternatives memory: 32K (ffffffff81e6e000 - ffffffff81e76000)
[    0.008179] ACPI: Core revision 20131115
[    0.010481] ACPI: All ACPI Tables successfully acquired
[    0.217053] ftrace: allocating 28541 entries in 112 pages
[    0.226032] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.265775] smpboot: CPU0: AMD FX(tm)-8320 Eight-Core Processor (fam: 15, model: 02, stepping: 00)
[    0.370261] Performance Events: Fam15h core perfctr, AMD PMU driver.
[    0.370265] ... version:                0
[    0.370266] ... bit width:              48
[    0.370267] ... generic registers:      6
[    0.370268] ... value mask:             0000ffffffffffff
[    0.370269] ... max period:             00007fffffffffff
[    0.370270] ... fixed-purpose events:   0
[    0.370271] ... event mask:             000000000000003f
[    0.371851] NMI watchdog: enabled on all CPUs, permanently consumes one hw-PMU counter.
[    0.371919] x86: Booting SMP configuration:
[    0.371921] .... node  #0, CPUs:      #1 #2 #3 #4 #5 #6 #7
[    0.464176] x86: Booted up 1 node, 8 CPUs
[    0.464180] smpboot: Total of 8 processors activated (56191.13 BogoMIPS)
[    0.474532] devtmpfs: initialized
[    0.477883] EVM: security.selinux
[    0.477884] EVM: security.SMACK64
[    0.477885] EVM: security.ima
[    0.477886] EVM: security.capability
[    0.477972] PM: Registering ACPI NVS region [mem 0xbab54000-0xbb959fff] (14704640 bytes)
[    0.478200] PM: Registering ACPI NVS region [mem 0xbca38000-0xbcc3dfff] (2121728 bytes)
[    0.479025] pinctrl core: initialized pinctrl subsystem
[    0.479081] regulator-dummy: no parameters
[    0.479109] RTC time: 21:53:12, date: 10/26/14
[    0.479142] NET: Registered protocol family 16
[    0.479271] cpuidle: using governor ladder
[    0.479272] cpuidle: using governor menu
[    0.479361] ACPI: bus type PCI registered
[    0.479363] acpiphp: ACPI Hot Plug PCI Controller Driver version: 0.5
[    0.479416] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xe0000000-0xefffffff] (base 0xe0000000)
[    0.479418] PCI: not using MMCONFIG
[    0.479419] PCI: Using configuration type 1 for base access
[    0.479420] PCI: Using configuration type 1 for extended access
[    0.480625] bio: create slab <bio-0> at 0
[    0.480835] ACPI: Added _OSI(Module Device)
[    0.480836] ACPI: Added _OSI(Processor Device)
[    0.480838] ACPI: Added _OSI(3.0 _SCP Extensions)
[    0.480839] ACPI: Added _OSI(Processor Aggregator Device)
[    0.482877] ACPI: Executed 2 blocks of module-level executable AML code
[    0.486929] ACPI: Interpreter enabled
[    0.486934] ACPI Exception: AE_NOT_FOUND, While evaluating Sleep State [\_S1_] (20131115/hwxface-580)
[    0.486938] ACPI Exception: AE_NOT_FOUND, While evaluating Sleep State [\_S2_] (20131115/hwxface-580)
[    0.486953] ACPI: (supports S0 S3 S4 S5)
[    0.486954] ACPI: Using IOAPIC for interrupt routing
[    0.487097] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xe0000000-0xefffffff] (base 0xe0000000)
[    0.487137] PCI: MMCONFIG at [mem 0xe0000000-0xefffffff] reserved in ACPI motherboard resources
[    0.502104] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[    0.502228] ACPI: No dock devices found.
[    0.510143] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
[    0.510149] acpi PNP0A03:00: _OSC: OS supports [ExtendedConfig ASPM ClockPM Segments MSI]
[    0.510154] acpi PNP0A03:00: _OSC failed (AE_NOT_FOUND); disabling ASPM
[    0.510653] PCI host bridge to bus 0000:00
[    0.510656] pci_bus 0000:00: root bus resource [bus 00-ff]
[    0.510658] pci_bus 0000:00: root bus resource [io  0x0000-0x03af]
[    0.510660] pci_bus 0000:00: root bus resource [io  0x03e0-0x0cf7]
[    0.510661] pci_bus 0000:00: root bus resource [io  0x03b0-0x03df]
[    0.510663] pci_bus 0000:00: root bus resource [io  0x0d00-0xffff]
[    0.510665] pci_bus 0000:00: root bus resource [mem 0x000a0000-0x000bffff]
[    0.510667] pci_bus 0000:00: root bus resource [mem 0x000c0000-0x000dffff]
[    0.510668] pci_bus 0000:00: root bus resource [mem 0xc0000000-0xffffffff]
[    0.510683] pci 0000:00:00.0: [1002:5a14] type 00 class 0x060000
[    0.510868] pci 0000:00:02.0: [1002:5a16] type 01 class 0x060400
[    0.510918] pci 0000:00:02.0: PME# supported from D0 D3hot D3cold
[    0.510980] pci 0000:00:02.0: System wakeup disabled by ACPI
[    0.511010] pci 0000:00:04.0: [1002:5a18] type 01 class 0x060400
[    0.511059] pci 0000:00:04.0: PME# supported from D0 D3hot D3cold
[    0.511120] pci 0000:00:04.0: System wakeup disabled by ACPI
[    0.511152] pci 0000:00:05.0: [1002:5a19] type 01 class 0x060400
[    0.511201] pci 0000:00:05.0: PME# supported from D0 D3hot D3cold
[    0.511262] pci 0000:00:05.0: System wakeup disabled by ACPI
[    0.511289] pci 0000:00:06.0: [1002:5a1a] type 01 class 0x060400
[    0.511338] pci 0000:00:06.0: PME# supported from D0 D3hot D3cold
[    0.511400] pci 0000:00:06.0: System wakeup disabled by ACPI
[    0.511428] pci 0000:00:07.0: [1002:5a1b] type 01 class 0x060400
[    0.511476] pci 0000:00:07.0: PME# supported from D0 D3hot D3cold
[    0.511538] pci 0000:00:07.0: System wakeup disabled by ACPI
[    0.511579] pci 0000:00:11.0: [1002:4391] type 00 class 0x010601
[    0.511598] pci 0000:00:11.0: reg 0x10: [io  0xf040-0xf047]
[    0.511607] pci 0000:00:11.0: reg 0x14: [io  0xf030-0xf033]
[    0.511616] pci 0000:00:11.0: reg 0x18: [io  0xf020-0xf027]
[    0.511625] pci 0000:00:11.0: reg 0x1c: [io  0xf010-0xf013]
[    0.511634] pci 0000:00:11.0: reg 0x20: [io  0xf000-0xf00f]
[    0.511643] pci 0000:00:11.0: reg 0x24: [mem 0xfeb0b000-0xfeb0b3ff]
[    0.511762] pci 0000:00:12.0: [1002:4397] type 00 class 0x0c0310
[    0.511775] pci 0000:00:12.0: reg 0x10: [mem 0xfeb0a000-0xfeb0afff]
[    0.511880] pci 0000:00:12.0: System wakeup disabled by ACPI
[    0.511912] pci 0000:00:12.2: [1002:4396] type 00 class 0x0c0320
[    0.511931] pci 0000:00:12.2: reg 0x10: [mem 0xfeb09000-0xfeb090ff]
[    0.512038] pci 0000:00:12.2: supports D1 D2
[    0.512039] pci 0000:00:12.2: PME# supported from D0 D1 D2 D3hot
[    0.512099] pci 0000:00:12.2: System wakeup disabled by ACPI
[    0.512132] pci 0000:00:13.0: [1002:4397] type 00 class 0x0c0310
[    0.512145] pci 0000:00:13.0: reg 0x10: [mem 0xfeb08000-0xfeb08fff]
[    0.512250] pci 0000:00:13.0: System wakeup disabled by ACPI
[    0.512283] pci 0000:00:13.2: [1002:4396] type 00 class 0x0c0320
[    0.512301] pci 0000:00:13.2: reg 0x10: [mem 0xfeb07000-0xfeb070ff]
[    0.512380] pci 0000:00:13.2: supports D1 D2
[    0.512381] pci 0000:00:13.2: PME# supported from D0 D1 D2 D3hot
[    0.512441] pci 0000:00:13.2: System wakeup disabled by ACPI
[    0.512473] pci 0000:00:14.0: [1002:4385] type 00 class 0x0c0500
[    0.512614] pci 0000:00:14.2: [1002:4383] type 00 class 0x040300
[    0.512634] pci 0000:00:14.2: reg 0x10: [mem 0xfeb00000-0xfeb03fff 64bit]
[    0.512698] pci 0000:00:14.2: PME# supported from D0 D3hot D3cold
[    0.512756] pci 0000:00:14.2: System wakeup disabled by ACPI
[    0.512781] pci 0000:00:14.3: [1002:439d] type 00 class 0x060100
[    0.512916] pci 0000:00:14.4: [1002:4384] type 01 class 0x060401
[    0.513000] pci 0000:00:14.4: System wakeup disabled by ACPI
[    0.513025] pci 0000:00:14.5: [1002:4399] type 00 class 0x0c0310
[    0.513038] pci 0000:00:14.5: reg 0x10: [mem 0xfeb06000-0xfeb06fff]
[    0.513144] pci 0000:00:14.5: System wakeup disabled by ACPI
[    0.513199] pci 0000:00:16.0: [1002:4397] type 00 class 0x0c0310
[    0.513212] pci 0000:00:16.0: reg 0x10: [mem 0xfeb05000-0xfeb05fff]
[    0.513317] pci 0000:00:16.0: System wakeup disabled by ACPI
[    0.513350] pci 0000:00:16.2: [1002:4396] type 00 class 0x0c0320
[    0.513368] pci 0000:00:16.2: reg 0x10: [mem 0xfeb04000-0xfeb040ff]
[    0.513447] pci 0000:00:16.2: supports D1 D2
[    0.513448] pci 0000:00:16.2: PME# supported from D0 D1 D2 D3hot
[    0.513508] pci 0000:00:16.2: System wakeup disabled by ACPI
[    0.513539] pci 0000:00:18.0: [1022:1600] type 00 class 0x060000
[    0.513636] pci 0000:00:18.1: [1022:1601] type 00 class 0x060000
[    0.513721] pci 0000:00:18.2: [1022:1602] type 00 class 0x060000
[    0.513807] pci 0000:00:18.3: [1022:1603] type 00 class 0x060000
[    0.513898] pci 0000:00:18.4: [1022:1604] type 00 class 0x060000
[    0.513982] pci 0000:00:18.5: [1022:1605] type 00 class 0x060000
[    0.514281] pci 0000:01:00.0: [1002:68b8] type 00 class 0x030000
[    0.514296] pci 0000:01:00.0: reg 0x10: [mem 0xc0000000-0xcfffffff 64bit pref]
[    0.514307] pci 0000:01:00.0: reg 0x18: [mem 0xfea20000-0xfea3ffff 64bit]
[    0.514315] pci 0000:01:00.0: reg 0x20: [io  0xe000-0xe0ff]
[    0.514329] pci 0000:01:00.0: reg 0x30: [mem 0xfea00000-0xfea1ffff pref]
[    0.514365] pci 0000:01:00.0: supports D1 D2
[    0.514419] pci 0000:01:00.1: [1002:aa58] type 00 class 0x040300
[    0.514433] pci 0000:01:00.1: reg 0x10: [mem 0xfea40000-0xfea43fff 64bit]
[    0.514502] pci 0000:01:00.1: supports D1 D2
[    0.522481] pci 0000:00:02.0: PCI bridge to [bus 01]
[    0.522486] pci 0000:00:02.0:   bridge window [io  0xe000-0xefff]
[    0.522489] pci 0000:00:02.0:   bridge window [mem 0xfea00000-0xfeafffff]
[    0.522493] pci 0000:00:02.0:   bridge window [mem 0xc0000000-0xcfffffff 64bit pref]
[    0.522717] pci 0000:02:00.0: [10ec:8168] type 00 class 0x020000
[    0.522732] pci 0000:02:00.0: reg 0x10: [io  0xd000-0xd0ff]
[    0.522755] pci 0000:02:00.0: reg 0x18: [mem 0xd0004000-0xd0004fff 64bit pref]
[    0.522770] pci 0000:02:00.0: reg 0x20: [mem 0xd0000000-0xd0003fff 64bit pref]
[    0.522834] pci 0000:02:00.0: supports D1 D2
[    0.522836] pci 0000:02:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.530493] pci 0000:00:04.0: PCI bridge to [bus 02]
[    0.530498] pci 0000:00:04.0:   bridge window [io  0xd000-0xdfff]
[    0.530503] pci 0000:00:04.0:   bridge window [mem 0xd0000000-0xd00fffff 64bit pref]
[    0.530566] pci 0000:03:00.0: [1b21:1042] type 00 class 0x0c0330
[    0.530587] pci 0000:03:00.0: reg 0x10: [mem 0xfe900000-0xfe907fff 64bit]
[    0.530688] pci 0000:03:00.0: PME# supported from D3hot D3cold
[    0.538502] pci 0000:00:05.0: PCI bridge to [bus 03]
[    0.538508] pci 0000:00:05.0:   bridge window [mem 0xfe900000-0xfe9fffff]
[    0.538568] pci 0000:04:00.0: [1b21:0612] type 00 class 0x010601
[    0.538581] pci 0000:04:00.0: reg 0x10: [io  0xc050-0xc057]
[    0.538590] pci 0000:04:00.0: reg 0x14: [io  0xc040-0xc043]
[    0.538599] pci 0000:04:00.0: reg 0x18: [io  0xc030-0xc037]
[    0.538608] pci 0000:04:00.0: reg 0x1c: [io  0xc020-0xc023]
[    0.538617] pci 0000:04:00.0: reg 0x20: [io  0xc000-0xc01f]
[    0.538626] pci 0000:04:00.0: reg 0x24: [mem 0xfe800000-0xfe8001ff]
[    0.546512] pci 0000:00:06.0: PCI bridge to [bus 04]
[    0.546517] pci 0000:00:06.0:   bridge window [io  0xc000-0xcfff]
[    0.546520] pci 0000:00:06.0:   bridge window [mem 0xfe800000-0xfe8fffff]
[    0.546585] pci 0000:05:00.0: [1b21:1042] type 00 class 0x0c0330
[    0.546605] pci 0000:05:00.0: reg 0x10: [mem 0xfe700000-0xfe707fff 64bit]
[    0.546707] pci 0000:05:00.0: PME# supported from D3hot D3cold
[    0.554524] pci 0000:00:07.0: PCI bridge to [bus 05]
[    0.554530] pci 0000:00:07.0:   bridge window [mem 0xfe700000-0xfe7fffff]
[    0.554610] pci 0000:06:07.0: [1106:3044] type 00 class 0x0c0010
[    0.554632] pci 0000:06:07.0: reg 0x10: [mem 0xfe600000-0xfe6007ff]
[    0.554644] pci 0000:06:07.0: reg 0x14: [io  0xb000-0xb07f]
[    0.554733] pci 0000:06:07.0: supports D2
[    0.554735] pci 0000:06:07.0: PME# supported from D2 D3hot D3cold
[    0.554801] pci 0000:00:14.4: PCI bridge to [bus 06] (subtractive decode)
[    0.554805] pci 0000:00:14.4:   bridge window [io  0xb000-0xbfff]
[    0.554808] pci 0000:00:14.4:   bridge window [mem 0xfe600000-0xfe6fffff]
[    0.554812] pci 0000:00:14.4:   bridge window [io  0x0000-0x03af] (subtractive decode)
[    0.554814] pci 0000:00:14.4:   bridge window [io  0x03e0-0x0cf7] (subtractive decode)
[    0.554816] pci 0000:00:14.4:   bridge window [io  0x03b0-0x03df] (subtractive decode)
[    0.554817] pci 0000:00:14.4:   bridge window [io  0x0d00-0xffff] (subtractive decode)
[    0.554819] pci 0000:00:14.4:   bridge window [mem 0x000a0000-0x000bffff] (subtractive decode)
[    0.554820] pci 0000:00:14.4:   bridge window [mem 0x000c0000-0x000dffff] (subtractive decode)
[    0.554822] pci 0000:00:14.4:   bridge window [mem 0xc0000000-0xffffffff] (subtractive decode)
[    0.555230] ACPI: PCI Interrupt Link [LNKA] (IRQs 4 7 10 11 14 15) *0
[    0.555303] ACPI: PCI Interrupt Link [LNKB] (IRQs 4 7 10 11 14 15) *0
[    0.555379] ACPI: PCI Interrupt Link [LNKC] (IRQs 4 7 10 11 14 15) *0
[    0.555453] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 10 11 14 15) *0
[    0.555513] ACPI: PCI Interrupt Link [LNKE] (IRQs 4 7 10 11 14 15) *0
[    0.555562] ACPI: PCI Interrupt Link [LNKF] (IRQs 4 7 10 11 14 15) *0
[    0.555611] ACPI: PCI Interrupt Link [LNKG] (IRQs 4 7 10 11 14 15) *0
[    0.555659] ACPI: PCI Interrupt Link [LNKH] (IRQs 4 7 10 11 14 15) *0
[    0.555791] ACPI: Enabled 1 GPEs in block 00 to 1F
[    0.555797] ACPI: \_SB_.PCI0: notify handler is installed
[    0.555835] Found 1 acpi root devices
[    0.555853] ACPI : EC: GPE = 0xa, I/O: command/status = 0x66, data = 0x62
[    0.555948] vgaarb: device added: PCI:0000:01:00.0,decodes=io+mem,owns=io+mem,locks=none
[    0.555950] vgaarb: loaded
[    0.555951] vgaarb: bridge control possible 0000:01:00.0
[    0.556110] SCSI subsystem initialized
[    0.556161] libata version 3.00 loaded.
[    0.556178] ACPI: bus type USB registered
[    0.556193] usbcore: registered new interface driver usbfs
[    0.556200] usbcore: registered new interface driver hub
[    0.556222] usbcore: registered new device driver usb
[    0.556342] PCI: Using ACPI for IRQ routing
[    0.564617] PCI: pci_cache_line_size set to 64 bytes
[    0.564687] e820: reserve RAM buffer [mem 0x0009e800-0x0009ffff]
[    0.564689] e820: reserve RAM buffer [mem 0xba868000-0xbbffffff]
[    0.564690] e820: reserve RAM buffer [mem 0xbca38000-0xbfffffff]
[    0.564691] e820: reserve RAM buffer [mem 0xbd083000-0xbfffffff]
[    0.564693] e820: reserve RAM buffer [mem 0xbd800000-0xbfffffff]
[    0.564694] e820: reserve RAM buffer [mem 0x43f000000-0x43fffffff]
[    0.564761] NetLabel: Initializing
[    0.564762] NetLabel:  domain hash size = 128
[    0.564763] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.564772] NetLabel:  unlabeled traffic allowed by default
[    0.564847] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[    0.564850] hpet0: 3 comparators, 32-bit 14.318180 MHz counter
[    0.566921] Switched to clocksource hpet
[    0.572687] AppArmor: AppArmor Filesystem Enabled
[    0.572704] pnp: PnP ACPI init
[    0.572714] ACPI: bus type PNP registered
[    0.572801] system 00:00: [mem 0xe0000000-0xefffffff] has been reserved
[    0.572804] system 00:00: Plug and Play ACPI device, IDs PNP0c01 (active)
[    0.573326] system 00:01: [io  0x040b] has been reserved
[    0.573328] system 00:01: [io  0x04d6] has been reserved
[    0.573330] system 00:01: [io  0x0c00-0x0c01] has been reserved
[    0.573332] system 00:01: [io  0x0c14] has been reserved
[    0.573334] system 00:01: [io  0x0c50-0x0c51] has been reserved
[    0.573336] system 00:01: [io  0x0c52] has been reserved
[    0.573337] system 00:01: [io  0x0c6c] has been reserved
[    0.573339] system 00:01: [io  0x0c6f] has been reserved
[    0.573341] system 00:01: [io  0x0cd0-0x0cd1] has been reserved
[    0.573342] system 00:01: [io  0x0cd2-0x0cd3] has been reserved
[    0.573344] system 00:01: [io  0x0cd4-0x0cd5] has been reserved
[    0.573346] system 00:01: [io  0x0cd6-0x0cd7] has been reserved
[    0.573347] system 00:01: [io  0x0cd8-0x0cdf] has been reserved
[    0.573349] system 00:01: [io  0x0800-0x089f] could not be reserved
[    0.573351] system 00:01: [io  0x0b20-0x0b3f] has been reserved
[    0.573353] system 00:01: [io  0x0900-0x090f] has been reserved
[    0.573354] system 00:01: [io  0x0910-0x091f] has been reserved
[    0.573356] system 00:01: [io  0xfe00-0xfefe] has been reserved
[    0.573359] system 00:01: [mem 0xfec00000-0xfec00fff] could not be reserved
[    0.573361] system 00:01: [mem 0xfee00000-0xfee00fff] has been reserved
[    0.573363] system 00:01: [mem 0xfed80000-0xfed8ffff] has been reserved
[    0.573365] system 00:01: [mem 0xfed61000-0xfed70fff] has been reserved
[    0.573367] system 00:01: [mem 0xfec10000-0xfec10fff] has been reserved
[    0.573369] system 00:01: [mem 0xfed00000-0xfed00fff] has been reserved
[    0.573371] system 00:01: [mem 0xff800000-0xffffffff] has been reserved
[    0.573373] system 00:01: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.573513] system 00:02: [io  0x0290-0x02af] has been reserved
[    0.573515] system 00:02: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.573528] pnp 00:03: [dma 4]
[    0.573542] pnp 00:03: Plug and Play ACPI device, IDs PNP0200 (active)
[    0.573571] pnp 00:04: Plug and Play ACPI device, IDs PNP0b00 (active)
[    0.573590] pnp 00:05: Plug and Play ACPI device, IDs PNP0800 (active)
[    0.573642] system 00:06: [io  0x04d0-0x04d1] has been reserved
[    0.573645] system 00:06: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.573666] pnp 00:07: Plug and Play ACPI device, IDs PNP0c04 (active)
[    0.573701] system 00:08: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.573742] pnp 00:09: Plug and Play ACPI device, IDs PNP0303 PNP030b (active)
[    0.573913] pnp 00:0a: [dma 0 disabled]
[    0.573952] pnp 00:0a: Plug and Play ACPI device, IDs PNP0501 (active)
[    0.574084] system 00:0b: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.574196] system 00:0c: [mem 0xfec20000-0xfec200ff] could not be reserved
[    0.574199] system 00:0c: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.574376] pnp 00:0d: Plug and Play ACPI device, IDs PNP0103 (active)
[    0.574381] pnp: PnP ACPI: found 14 devices
[    0.574382] ACPI: bus type PNP unregistered
[    0.580717] pci 0000:00:02.0: PCI bridge to [bus 01]
[    0.580720] pci 0000:00:02.0:   bridge window [io  0xe000-0xefff]
[    0.580724] pci 0000:00:02.0:   bridge window [mem 0xfea00000-0xfeafffff]
[    0.580727] pci 0000:00:02.0:   bridge window [mem 0xc0000000-0xcfffffff 64bit pref]
[    0.580731] pci 0000:00:04.0: PCI bridge to [bus 02]
[    0.580733] pci 0000:00:04.0:   bridge window [io  0xd000-0xdfff]
[    0.580738] pci 0000:00:04.0:   bridge window [mem 0xd0000000-0xd00fffff 64bit pref]
[    0.580742] pci 0000:00:05.0: PCI bridge to [bus 03]
[    0.580745] pci 0000:00:05.0:   bridge window [mem 0xfe900000-0xfe9fffff]
[    0.580750] pci 0000:00:06.0: PCI bridge to [bus 04]
[    0.580752] pci 0000:00:06.0:   bridge window [io  0xc000-0xcfff]
[    0.580755] pci 0000:00:06.0:   bridge window [mem 0xfe800000-0xfe8fffff]
[    0.580760] pci 0000:00:07.0: PCI bridge to [bus 05]
[    0.580763] pci 0000:00:07.0:   bridge window [mem 0xfe700000-0xfe7fffff]
[    0.580768] pci 0000:00:14.4: PCI bridge to [bus 06]
[    0.580771] pci 0000:00:14.4:   bridge window [io  0xb000-0xbfff]
[    0.580775] pci 0000:00:14.4:   bridge window [mem 0xfe600000-0xfe6fffff]
[    0.580784] pci_bus 0000:00: resource 4 [io  0x0000-0x03af]
[    0.580785] pci_bus 0000:00: resource 5 [io  0x03e0-0x0cf7]
[    0.580787] pci_bus 0000:00: resource 6 [io  0x03b0-0x03df]
[    0.580788] pci_bus 0000:00: resource 7 [io  0x0d00-0xffff]
[    0.580790] pci_bus 0000:00: resource 8 [mem 0x000a0000-0x000bffff]
[    0.580792] pci_bus 0000:00: resource 9 [mem 0x000c0000-0x000dffff]
[    0.580793] pci_bus 0000:00: resource 10 [mem 0xc0000000-0xffffffff]
[    0.580795] pci_bus 0000:01: resource 0 [io  0xe000-0xefff]
[    0.580796] pci_bus 0000:01: resource 1 [mem 0xfea00000-0xfeafffff]
[    0.580798] pci_bus 0000:01: resource 2 [mem 0xc0000000-0xcfffffff 64bit pref]
[    0.580799] pci_bus 0000:02: resource 0 [io  0xd000-0xdfff]
[    0.580801] pci_bus 0000:02: resource 2 [mem 0xd0000000-0xd00fffff 64bit pref]
[    0.580803] pci_bus 0000:03: resource 1 [mem 0xfe900000-0xfe9fffff]
[    0.580804] pci_bus 0000:04: resource 0 [io  0xc000-0xcfff]
[    0.580806] pci_bus 0000:04: resource 1 [mem 0xfe800000-0xfe8fffff]
[    0.580807] pci_bus 0000:05: resource 1 [mem 0xfe700000-0xfe7fffff]
[    0.580809] pci_bus 0000:06: resource 0 [io  0xb000-0xbfff]
[    0.580810] pci_bus 0000:06: resource 1 [mem 0xfe600000-0xfe6fffff]
[    0.580812] pci_bus 0000:06: resource 4 [io  0x0000-0x03af]
[    0.580813] pci_bus 0000:06: resource 5 [io  0x03e0-0x0cf7]
[    0.580815] pci_bus 0000:06: resource 6 [io  0x03b0-0x03df]
[    0.580816] pci_bus 0000:06: resource 7 [io  0x0d00-0xffff]
[    0.580818] pci_bus 0000:06: resource 8 [mem 0x000a0000-0x000bffff]
[    0.580819] pci_bus 0000:06: resource 9 [mem 0x000c0000-0x000dffff]
[    0.580821] pci_bus 0000:06: resource 10 [mem 0xc0000000-0xffffffff]
[    0.580843] NET: Registered protocol family 2
[    0.581082] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.581369] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    0.581562] TCP: Hash tables configured (established 131072 bind 65536)
[    0.581588] TCP: reno registered
[    0.581610] UDP hash table entries: 8192 (order: 6, 262144 bytes)
[    0.581682] UDP-Lite hash table entries: 8192 (order: 6, 262144 bytes)
[    0.581784] NET: Registered protocol family 1
[    0.871596] pci 0000:01:00.0: Boot video device
[    0.871854] PCI: CLS 64 bytes, default 64
[    0.871912] Trying to unpack rootfs image as initramfs...
[    1.239037] Freeing initrd memory: 27400K (ffff880034a6c000 - ffff88003652e000)
[    1.239395] PCI-DMA: Disabling AGP.
[    1.239472] PCI-DMA: aperture base @ b0000000 size 65536 KB
[    1.239473] PCI-DMA: using GART IOMMU.
[    1.239475] PCI-DMA: Reserving 64MB of IOMMU area in the AGP aperture
[    1.243713] perf: AMD NB counters detected
[    1.243744] LVT offset 0 assigned for vector 0x400
[    1.243770] perf: AMD IBS detected (0x000000ff)
[    1.243806] microcode: CPU0: patch_level=0x06000822
[    1.243811] microcode: CPU1: patch_level=0x06000822
[    1.243820] microcode: CPU2: patch_level=0x06000822
[    1.243828] microcode: CPU3: patch_level=0x06000822
[    1.243837] microcode: CPU4: patch_level=0x06000822
[    1.243844] microcode: CPU5: patch_level=0x06000822
[    1.243852] microcode: CPU6: patch_level=0x06000822
[    1.243859] microcode: CPU7: patch_level=0x06000822
[    1.243907] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[    1.243908] Scanning for low memory corruption every 60 seconds
[    1.244195] Initialise system trusted keyring
[    1.244230] audit: initializing netlink socket (disabled)
[    1.244239] type=2000 audit(1414360391.936:1): initialized
[    1.266444] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    1.267756] zbud: loaded
[    1.267867] VFS: Disk quotas dquot_6.5.2
[    1.267914] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    1.268325] fuse init (API version 7.22)
[    1.268389] msgmni has been set to 31894
[    1.268436] Key type big_key registered
[    1.268896] Key type asymmetric registered
[    1.268898] Asymmetric key parser 'x509' registered
[    1.268923] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 252)
[    1.268971] io scheduler noop registered
[    1.268973] io scheduler deadline registered (default)
[    1.268994] io scheduler cfq registered
[    1.269416] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    1.269428] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    1.269465] vesafb: mode is 640x480x32, linelength=2560, pages=0
[    1.269466] vesafb: scrolling: redraw
[    1.269468] vesafb: Truecolor: size=0:8:8:8, shift=0:16:8:0
[    1.269548] vesafb: framebuffer at 0xc0000000, mapped to 0xffffc90011b80000, using 1216k, total 1216k
[    1.272297] Console: switching to colour frame buffer device 80x30
[    1.274953] fb0: VESA VGA frame buffer device
[    1.274970] ipmi message handler version 39.2
[    1.275024] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0
[    1.275028] ACPI: Power Button [PWRB]
[    1.275056] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
[    1.275057] ACPI: Power Button [PWRF]
[    1.275100] ACPI: acpi_idle registered with cpuidle
[    1.275661] GHES: HEST is not enabled!
[    1.275757] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    1.296172] 00:0a: ttyS0 at I/O 0x3f8 (irq = 4, base_baud = 115200) is a 16550A
[    1.297573] Linux agpgart interface v0.103
[    1.298794] brd: module loaded
[    1.299442] loop: module loaded
[    1.299783] libphy: Fixed MDIO Bus: probed
[    1.299861] tun: Universal TUN/TAP device driver, 1.6
[    1.299862] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    1.299899] PPP generic driver version 2.4.2
[    1.299939] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    1.299942] ehci-pci: EHCI PCI platform driver
[    1.300040] QUIRK: Enable AMD PLL fix
[    1.300057] ehci-pci 0000:00:12.2: EHCI Host Controller
[    1.300062] ehci-pci 0000:00:12.2: new USB bus registered, assigned bus number 1
[    1.300066] ehci-pci 0000:00:12.2: applying AMD SB700/SB800/Hudson-2/3 EHCI dummy qh workaround
[    1.300087] ehci-pci 0000:00:12.2: debug port 1
[    1.300121] ehci-pci 0000:00:12.2: irq 17, io mem 0xfeb09000
[    1.312013] ehci-pci 0000:00:12.2: USB 2.0 started, EHCI 1.00
[    1.312060] usb usb1: New USB device found, idVendor=1d6b, idProduct=0002
[    1.312062] usb usb1: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.312064] usb usb1: Product: EHCI Host Controller
[    1.312065] usb usb1: Manufacturer: Linux 3.13.0-37-generic ehci_hcd
[    1.312067] usb usb1: SerialNumber: 0000:00:12.2
[    1.312190] hub 1-0:1.0: USB hub found
[    1.312197] hub 1-0:1.0: 5 ports detected
[    1.312406] ehci-pci 0000:00:13.2: EHCI Host Controller
[    1.312411] ehci-pci 0000:00:13.2: new USB bus registered, assigned bus number 2
[    1.312414] ehci-pci 0000:00:13.2: applying AMD SB700/SB800/Hudson-2/3 EHCI dummy qh workaround
[    1.312422] ehci-pci 0000:00:13.2: debug port 1
[    1.312454] ehci-pci 0000:00:13.2: irq 21, io mem 0xfeb07000
[    1.324075] ehci-pci 0000:00:13.2: USB 2.0 started, EHCI 1.00
[    1.324118] usb usb2: New USB device found, idVendor=1d6b, idProduct=0002
[    1.324120] usb usb2: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.324121] usb usb2: Product: EHCI Host Controller
[    1.324123] usb usb2: Manufacturer: Linux 3.13.0-37-generic ehci_hcd
[    1.324124] usb usb2: SerialNumber: 0000:00:13.2
[    1.324234] hub 2-0:1.0: USB hub found
[    1.324240] hub 2-0:1.0: 5 ports detected
[    1.324449] ehci-pci 0000:00:16.2: EHCI Host Controller
[    1.324453] ehci-pci 0000:00:16.2: new USB bus registered, assigned bus number 3
[    1.324455] ehci-pci 0000:00:16.2: applying AMD SB700/SB800/Hudson-2/3 EHCI dummy qh workaround
[    1.324464] ehci-pci 0000:00:16.2: debug port 1
[    1.324492] ehci-pci 0000:00:16.2: irq 23, io mem 0xfeb04000
[    1.336090] ehci-pci 0000:00:16.2: USB 2.0 started, EHCI 1.00
[    1.336126] usb usb3: New USB device found, idVendor=1d6b, idProduct=0002
[    1.336128] usb usb3: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.336130] usb usb3: Product: EHCI Host Controller
[    1.336131] usb usb3: Manufacturer: Linux 3.13.0-37-generic ehci_hcd
[    1.336133] usb usb3: SerialNumber: 0000:00:16.2
[    1.336246] hub 3-0:1.0: USB hub found
[    1.336252] hub 3-0:1.0: 4 ports detected
[    1.336338] ehci-platform: EHCI generic platform driver
[    1.336345] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    1.336346] ohci-pci: OHCI PCI platform driver
[    1.336433] ohci-pci 0000:00:12.0: OHCI PCI host controller
[    1.336438] ohci-pci 0000:00:12.0: new USB bus registered, assigned bus number 4
[    1.336455] ohci-pci 0000:00:12.0: irq 18, io mem 0xfeb0a000
[    1.396196] usb usb4: New USB device found, idVendor=1d6b, idProduct=0001
[    1.396199] usb usb4: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.396201] usb usb4: Product: OHCI PCI host controller
[    1.396202] usb usb4: Manufacturer: Linux 3.13.0-37-generic ohci_hcd
[    1.396203] usb usb4: SerialNumber: 0000:00:12.0
[    1.396320] hub 4-0:1.0: USB hub found
[    1.396329] hub 4-0:1.0: 5 ports detected
[    1.396496] ohci-pci 0000:00:13.0: OHCI PCI host controller
[    1.396500] ohci-pci 0000:00:13.0: new USB bus registered, assigned bus number 5
[    1.396519] ohci-pci 0000:00:13.0: irq 20, io mem 0xfeb08000
[    1.456267] usb usb5: New USB device found, idVendor=1d6b, idProduct=0001
[    1.456270] usb usb5: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.456271] usb usb5: Product: OHCI PCI host controller
[    1.456273] usb usb5: Manufacturer: Linux 3.13.0-37-generic ohci_hcd
[    1.456274] usb usb5: SerialNumber: 0000:00:13.0
[    1.456455] hub 5-0:1.0: USB hub found
[    1.456462] hub 5-0:1.0: 5 ports detected
[    1.456631] ohci-pci 0000:00:14.5: OHCI PCI host controller
[    1.456635] ohci-pci 0000:00:14.5: new USB bus registered, assigned bus number 6
[    1.456646] ohci-pci 0000:00:14.5: irq 18, io mem 0xfeb06000
[    1.516409] usb usb6: New USB device found, idVendor=1d6b, idProduct=0001
[    1.516411] usb usb6: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.516413] usb usb6: Product: OHCI PCI host controller
[    1.516415] usb usb6: Manufacturer: Linux 3.13.0-37-generic ohci_hcd
[    1.516416] usb usb6: SerialNumber: 0000:00:14.5
[    1.516597] hub 6-0:1.0: USB hub found
[    1.516604] hub 6-0:1.0: 2 ports detected
[    1.516750] ohci-pci 0000:00:16.0: OHCI PCI host controller
[    1.516754] ohci-pci 0000:00:16.0: new USB bus registered, assigned bus number 7
[    1.516775] ohci-pci 0000:00:16.0: irq 22, io mem 0xfeb05000
[    1.576431] usb usb7: New USB device found, idVendor=1d6b, idProduct=0001
[    1.576434] usb usb7: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.576435] usb usb7: Product: OHCI PCI host controller
[    1.576437] usb usb7: Manufacturer: Linux 3.13.0-37-generic ohci_hcd
[    1.576438] usb usb7: SerialNumber: 0000:00:16.0
[    1.576610] hub 7-0:1.0: USB hub found
[    1.576621] hub 7-0:1.0: 4 ports detected
[    1.576703] ohci-platform: OHCI generic platform driver
[    1.576710] uhci_hcd: USB Universal Host Controller Interface driver
[    1.576777] xhci_hcd 0000:03:00.0: xHCI Host Controller
[    1.576781] xhci_hcd 0000:03:00.0: new USB bus registered, assigned bus number 8
[    1.636236] xhci_hcd 0000:03:00.0: irq 72 for MSI/MSI-X
[    1.636242] xhci_hcd 0000:03:00.0: irq 73 for MSI/MSI-X
[    1.636248] xhci_hcd 0000:03:00.0: irq 74 for MSI/MSI-X
[    1.636252] xhci_hcd 0000:03:00.0: irq 75 for MSI/MSI-X
[    1.636257] xhci_hcd 0000:03:00.0: irq 76 for MSI/MSI-X
[    1.636262] xhci_hcd 0000:03:00.0: irq 77 for MSI/MSI-X
[    1.636267] xhci_hcd 0000:03:00.0: irq 78 for MSI/MSI-X
[    1.636272] xhci_hcd 0000:03:00.0: irq 79 for MSI/MSI-X
[    1.636375] usb usb8: New USB device found, idVendor=1d6b, idProduct=0002
[    1.636377] usb usb8: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.636378] usb usb8: Product: xHCI Host Controller
[    1.636379] usb usb8: Manufacturer: Linux 3.13.0-37-generic xhci_hcd
[    1.636381] usb usb8: SerialNumber: 0000:03:00.0
[    1.636545] hub 8-0:1.0: USB hub found
[    1.636553] hub 8-0:1.0: 2 ports detected
[    1.636611] xhci_hcd 0000:03:00.0: xHCI Host Controller
[    1.636614] xhci_hcd 0000:03:00.0: new USB bus registered, assigned bus number 9
[    1.636653] usb usb9: New USB device found, idVendor=1d6b, idProduct=0003
[    1.636654] usb usb9: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.636656] usb usb9: Product: xHCI Host Controller
[    1.636657] usb usb9: Manufacturer: Linux 3.13.0-37-generic xhci_hcd
[    1.636658] usb usb9: SerialNumber: 0000:03:00.0
[    1.636732] hub 9-0:1.0: USB hub found
[    1.636738] hub 9-0:1.0: 2 ports detected
[    1.644716] xhci_hcd 0000:05:00.0: xHCI Host Controller
[    1.644721] xhci_hcd 0000:05:00.0: new USB bus registered, assigned bus number 10
[    1.704157] xhci_hcd 0000:05:00.0: irq 80 for MSI/MSI-X
[    1.704162] xhci_hcd 0000:05:00.0: irq 81 for MSI/MSI-X
[    1.704167] xhci_hcd 0000:05:00.0: irq 82 for MSI/MSI-X
[    1.704172] xhci_hcd 0000:05:00.0: irq 83 for MSI/MSI-X
[    1.704177] xhci_hcd 0000:05:00.0: irq 84 for MSI/MSI-X
[    1.704181] xhci_hcd 0000:05:00.0: irq 85 for MSI/MSI-X
[    1.704186] xhci_hcd 0000:05:00.0: irq 86 for MSI/MSI-X
[    1.704190] xhci_hcd 0000:05:00.0: irq 87 for MSI/MSI-X
[    1.704296] usb usb10: New USB device found, idVendor=1d6b, idProduct=0002
[    1.704297] usb usb10: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.704299] usb usb10: Product: xHCI Host Controller
[    1.704300] usb usb10: Manufacturer: Linux 3.13.0-37-generic xhci_hcd
[    1.704302] usb usb10: SerialNumber: 0000:05:00.0
[    1.704435] hub 10-0:1.0: USB hub found
[    1.704441] hub 10-0:1.0: 2 ports detected
[    1.704547] xhci_hcd 0000:05:00.0: xHCI Host Controller
[    1.704551] xhci_hcd 0000:05:00.0: new USB bus registered, assigned bus number 11
[    1.704595] usb usb11: New USB device found, idVendor=1d6b, idProduct=0003
[    1.704597] usb usb11: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.704598] usb usb11: Product: xHCI Host Controller
[    1.704600] usb usb11: Manufacturer: Linux 3.13.0-37-generic xhci_hcd
[    1.704601] usb usb11: SerialNumber: 0000:05:00.0
[    1.704680] hub 11-0:1.0: USB hub found
[    1.704686] hub 11-0:1.0: 2 ports detected
[    1.712803] i8042: PNP: PS/2 Controller [PNP0303:PS2K] at 0x60,0x64 irq 1
[    1.712805] i8042: PNP: PS/2 appears to have AUX port disabled, if this is incorrect please boot with i8042.nopnp
[    1.712926] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.713105] mousedev: PS/2 mouse device common for all mice
[    1.713287] rtc_cmos 00:04: RTC can wake from S4
[    1.713382] rtc_cmos 00:04: rtc core: registered rtc_cmos as rtc0
[    1.713402] rtc_cmos 00:04: alarms up to one month, y3k, 114 bytes nvram, hpet irqs
[    1.713467] device-mapper: uevent: version 1.0.3
[    1.713526] device-mapper: ioctl: 4.27.0-ioctl (2013-10-30) initialised: dm-devel@redhat.com
[    1.713531] ledtrig-cpu: registered to indicate activity on CPUs
[    1.713623] TCP: cubic registered
[    1.713707] NET: Registered protocol family 10
[    1.713847] NET: Registered protocol family 17
[    1.713852] Key type dns_resolver registered
[    1.714574] Loading compiled-in X.509 certificates
[    1.715361] Loaded X.509 cert 'Magrathea: Glacier signing key: 2cb1133b35f95a9e24deabeeb12ba449bcbabbc9'
[    1.715369] registered taskstats version 1
[    1.717920] Key type trusted registered
[    1.719906] Key type encrypted registered
[    1.721842] AppArmor: AppArmor sha1 policy hashing enabled
[    1.721845] IMA: No TPM chip found, activating TPM-bypass!
[    1.722169] regulator-dummy: disabling
[    1.722232]   Magic number: 2:547:905
[    1.722312] rtc_cmos 00:04: setting system clock to 2014-10-26 21:53:13 UTC (1414360393)
[    1.722432] acpi-cpufreq: overriding BIOS provided _PSD data
[    1.722806] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.722807] EDD information not available.
[    1.722847] PM: Hibernation image not present or could not be loaded.
[    1.724067] Freeing unused kernel memory: 1336K (ffffffff81d20000 - ffffffff81e6e000)
[    1.724068] Write protecting the kernel read-only data: 12288k
[    1.726916] Freeing unused kernel memory: 804K (ffff880001737000 - ffff880001800000)
[    1.729270] Freeing unused kernel memory: 692K (ffff880001b53000 - ffff880001c00000)
[    1.740236] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input2
[    1.742564] systemd-udevd[148]: starting version 204
[    1.753808] r8168: module verification failed: signature and/or  required key missing - tainting kernel
[    1.754294] r8168 Gigabit Ethernet driver 8.037.00-NAPI loaded
[    1.754409] wmi: Mapper loaded
[    1.754443] r8168 0000:02:00.0: irq 88 for MSI/MSI-X
[    1.758037] [drm] Initialized drm 1.1.0 20060810
[    1.759830] ahci 0000:00:11.0: version 3.0
[    1.760038] ahci 0000:00:11.0: AHCI 0001.0200 32 slots 3 ports 6 Gbps 0xb impl SATA mode
[    1.760041] ahci 0000:00:11.0: flags: 64bit ncq sntf ilck pm led clo pmp pio slum part 
[    1.763706] scsi0 : ahci
[    1.763926] scsi1 : ahci
[    1.764124] scsi2 : ahci
[    1.764500] scsi3 : ahci
[    1.764917] ata1: SATA max UDMA/133 abar m1024@0xfeb0b000 port 0xfeb0b100 irq 19
[    1.764921] ata2: SATA max UDMA/133 abar m1024@0xfeb0b000 port 0xfeb0b180 irq 19
[    1.764923] ata3: DUMMY
[    1.764926] ata4: SATA max UDMA/133 abar m1024@0xfeb0b000 port 0xfeb0b280 irq 19
[    1.765060] ahci 0000:04:00.0: irq 89 for MSI/MSI-X
[    1.765089] ahci 0000:04:00.0: SSS flag set, parallel bus scan disabled
[    1.765114] ahci 0000:04:00.0: AHCI 0001.0200 32 slots 2 ports 6 Gbps 0x3 impl SATA mode
[    1.765117] ahci 0000:04:00.0: flags: 64bit ncq sntf stag led clo pmp pio slum part ccc sxs 
[    1.767053] scsi4 : ahci
[    1.767138] scsi5 : ahci
[    1.767192] ata5: SATA max UDMA/133 abar m512@0xfe800000 port 0xfe800100 irq 89
[    1.767196] ata6: SATA max UDMA/133 abar m512@0xfe800000 port 0xfe800180 irq 89
[    1.775414] eth%d: 0xffffc9000189a000, ac:22:0b:82:7e:4d, IRQ 88
[    1.775821] r8168: This product is covered by one or more of the following patents: US6,570,884, US6,115,776, and US6,327,625.
[    1.775826] r8168  Copyright (C) 2013  Realtek NIC software team <nicfae@realtek.com> 
[    1.775826]  This program comes with ABSOLUTELY NO WARRANTY; for details, please see <http://www.gnu.org/licenses/>. 
[    1.775826]  This is free software, and you are welcome to redistribute it under certain conditions; see <http://www.gnu.org/licenses/>. 
[    1.781734] [drm] radeon kernel modesetting enabled.
[    1.781798] checking generic (c0000000 130000) vs hw (c0000000 10000000)
[    1.781800] fb: conflicting fb hw usage radeondrmfb vs VESA VGA - removing generic driver
[    1.781815] Console: switching to colour dummy device 80x25
[    1.782194] [drm] initializing kernel modesetting (JUNIPER 0x1002:0x68B8 0x174B:0x1482).
[    1.782211] [drm] register mmio base: 0xFEA20000
[    1.782213] [drm] register mmio size: 131072
[    1.782267] ATOM BIOS: JUNIPER
[    1.782319] radeon 0000:01:00.0: VRAM: 1024M 0x0000000000000000 - 0x000000003FFFFFFF (1024M used)
[    1.782321] radeon 0000:01:00.0: GTT: 1024M 0x0000000040000000 - 0x000000007FFFFFFF
[    1.782323] [drm] Detected VRAM RAM=1024M, BAR=256M
[    1.782324] [drm] RAM width 128bits DDR
[    1.782406] [TTM] Zone  kernel: Available graphics memory: 8166324 kiB
[    1.782408] [TTM] Zone   dma32: Available graphics memory: 2097152 kiB
[    1.782409] [TTM] Initializing pool allocator
[    1.782413] [TTM] Initializing DMA pool allocator
[    1.782435] [drm] radeon: 1024M of VRAM memory ready
[    1.782436] [drm] radeon: 1024M of GTT memory ready.
[    1.782461] [drm] Loading JUNIPER Microcode
[    1.782725] [drm] GART: num cpu pages 262144, num gpu pages 262144
[    1.783956] [drm] enabling PCIE gen 2 link speeds, disable with radeon.pcie_gen2=0
[    1.797919] [drm] PCIE GART of 1024M enabled (table at 0x000000000025D000).
[    1.797998] radeon 0000:01:00.0: WB enabled
[    1.798000] radeon 0000:01:00.0: fence driver on ring 0 use gpu addr 0x0000000040000c00 and cpu addr 0xffff8800b9ccfc00
[    1.798002] radeon 0000:01:00.0: fence driver on ring 3 use gpu addr 0x0000000040000c0c and cpu addr 0xffff8800b9ccfc0c
[    1.798399] radeon 0000:01:00.0: fence driver on ring 5 use gpu addr 0x000000000005c418 and cpu addr 0xffffc90011d9c418
[    1.798401] [drm] Supports vblank timestamp caching Rev 2 (21.10.2013).
[    1.798402] [drm] Driver supports precise vblank timestamp query.
[    1.798419] radeon 0000:01:00.0: irq 90 for MSI/MSI-X
[    1.798429] radeon 0000:01:00.0: radeon: using MSI.
[    1.798450] [drm] radeon: irq initialized.
[    1.814632] [drm] ring test on 0 succeeded in 1 usecs
[    1.814690] [drm] ring test on 3 succeeded in 1 usecs
[    1.828791] firewire_ohci 0000:06:07.0: added OHCI v1.10 device as card 0, 4 IR + 8 IT contexts, quirks 0x11
[    2.020450] [drm] ring test on 5 succeeded in 1 usecs
[    2.020454] [drm] UVD initialized successfully.
[    2.020543] [drm] Enabling audio 0 support
[    2.020563] [drm] ib test on ring 0 succeeded in 0 usecs
[    2.020581] [drm] ib test on ring 3 succeeded in 0 usecs
[    2.089180] ata5: SATA link down (SStatus 0 SControl 300)
[    2.190835] [drm] ib test on ring 5 succeeded
[    2.191204] [drm] Radeon Display Connectors
[    2.191205] [drm] Connector 0:
[    2.191206] [drm]   DP-1
[    2.191207] [drm]   HPD4
[    2.191209] [drm]   DDC: 0x6440 0x6440 0x6444 0x6444 0x6448 0x6448 0x644c 0x644c
[    2.191210] [drm]   Encoders:
[    2.191211] [drm]     DFP1: INTERNAL_UNIPHY2
[    2.191212] [drm] Connector 1:
[    2.191212] [drm]   HDMI-A-1
[    2.191213] [drm]   HPD5
[    2.191214] [drm]   DDC: 0x6430 0x6430 0x6434 0x6434 0x6438 0x6438 0x643c 0x643c
[    2.191215] [drm]   Encoders:
[    2.191216] [drm]     DFP2: INTERNAL_UNIPHY2
[    2.191217] [drm] Connector 2:
[    2.191218] [drm]   DVI-I-1
[    2.191218] [drm]   HPD1
[    2.191220] [drm]   DDC: 0x6460 0x6460 0x6464 0x6464 0x6468 0x6468 0x646c 0x646c
[    2.191220] [drm]   Encoders:
[    2.191221] [drm]     DFP3: INTERNAL_UNIPHY1
[    2.191222] [drm]     CRT2: INTERNAL_KLDSCP_DAC2
[    2.191223] [drm] Connector 3:
[    2.191224] [drm]   DVI-I-2
[    2.191224] [drm]   HPD6
[    2.191226] [drm]   DDC: 0x6450 0x6450 0x6454 0x6454 0x6458 0x6458 0x645c 0x645c
[    2.191226] [drm]   Encoders:
[    2.191227] [drm]     DFP4: INTERNAL_UNIPHY
[    2.191228] [drm]     CRT1: INTERNAL_KLDSCP_DAC1
[    2.191264] [drm] Internal thermal controller with fan control
[    2.200722] [drm] radeon: dpm initialized
[    2.221318] usb 4-1: new low-speed USB device number 2 using ohci-pci
[    2.247321] tsc: Refined TSC clocksource calibration: 3511.790 MHz
[    2.261340] ata2: SATA link up 6.0 Gbps (SStatus 133 SControl 300)
[    2.261414] ata4: SATA link up 6.0 Gbps (SStatus 133 SControl 300)
[    2.261456] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    2.261499] ata2.00: supports DRM functions and may not be fully accessible
[    2.261565] ata2.00: failed to get NCQ Send/Recv Log Emask 0x1
[    2.261568] ata2.00: ATA-9: Samsung SSD 840 EVO 1TB, EXT0BB6Q, max UDMA/133
[    2.261570] ata2.00: 1953525168 sectors, multi 1: LBA48 NCQ (depth 31/32), AA
[    2.261740] ata2.00: supports DRM functions and may not be fully accessible
[    2.261800] ata2.00: failed to get NCQ Send/Recv Log Emask 0x1
[    2.261805] ata2.00: configured for UDMA/133
[    2.262399] ata4.00: ATA-8: SanDisk SDSSDH2256G, X2306RL, max UDMA/133
[    2.262401] ata4.00: 500118192 sectors, multi 1: LBA48 NCQ (depth 31/32), AA
[    2.263398] ata4.00: configured for UDMA/133
[    2.267849] ata1.00: ATA-8: WDC WD20EARS-00S8B1, 80.00A80, max UDMA/133
[    2.267852] ata1.00: 3907029168 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
[    2.273855] ata1.00: configured for UDMA/133
[    2.274137] scsi 0:0:0:0: Direct-Access     ATA      WDC WD20EARS-00S 80.0 PQ: 0 ANSI: 5
[    2.274281] sd 0:0:0:0: [sda] 3907029168 512-byte logical blocks: (2.00 TB/1.81 TiB)
[    2.274297] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    2.274391] sd 0:0:0:0: [sda] Write Protect is off
[    2.274394] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    2.274437] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.274469] scsi 1:0:0:0: Direct-Access     ATA      Samsung SSD 840  EXT0 PQ: 0 ANSI: 5
[    2.274632] sd 1:0:0:0: Attached scsi generic sg1 type 0
[    2.274665] sd 1:0:0:0: [sdb] 1953525168 512-byte logical blocks: (1.00 TB/931 GiB)
[    2.274793] sd 1:0:0:0: [sdb] Write Protect is off
[    2.274795] sd 1:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[    2.274808] scsi 3:0:0:0: Direct-Access     ATA      SanDisk SDSSDH22 X230 PQ: 0 ANSI: 5
[    2.274834] sd 1:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.274920] sd 3:0:0:0: [sdc] 500118192 512-byte logical blocks: (256 GB/238 GiB)
[    2.274984] sd 3:0:0:0: Attached scsi generic sg2 type 0
[    2.275044] sd 3:0:0:0: [sdc] Write Protect is off
[    2.275046] sd 3:0:0:0: [sdc] Mode Sense: 00 3a 00 00
[    2.275095] sd 3:0:0:0: [sdc] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.275279]  sdb: sdb1
[    2.275517]  sdc: sdc1 sdc2
[    2.275565] sd 1:0:0:0: [sdb] Attached SCSI disk
[    2.275850] sd 3:0:0:0: [sdc] Attached SCSI disk
[    2.306366]  sda: sda1
[    2.306813] sd 0:0:0:0: [sda] Attached SCSI disk
[    2.317644] [drm] fb mappable at 0xC045E000
[    2.317646] [drm] vram apper at 0xC0000000
[    2.317647] [drm] size 8294400
[    2.317648] [drm] fb depth is 24
[    2.317649] [drm]    pitch is 7680
[    2.317714] fbcon: radeondrmfb (fb0) is primary device
[    2.329584] firewire_core 0000:06:07.0: created device fw0: GUID 001e8c0000671455, S400
[    2.354691] Console: switching to colour frame buffer device 240x67
[    2.358481] radeon 0000:01:00.0: fb0: radeondrmfb frame buffer device
[    2.358483] radeon 0000:01:00.0: registered panic notifier
[    2.358487] [drm] Initialized radeon 2.36.0 20080528 for 0000:01:00.0 on minor 0
[    2.390724] usb 4-1: New USB device found, idVendor=046d, idProduct=c050
[    2.390732] usb 4-1: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[    2.390737] usb 4-1: Product: USB-PS/2 Optical Mouse
[    2.390741] usb 4-1: Manufacturer: Logitech
[    2.395485] hidraw: raw HID events driver (C) Jiri Kosina
[    2.401800] usbcore: registered new interface driver usbhid
[    2.401802] usbhid: USB HID core driver
[    2.403244] input: Logitech USB-PS/2 Optical Mouse as /devices/pci0000:00/0000:00:12.0/usb4/4-1/4-1:1.0/input/input3
[    2.403362] hid-generic 0003:046D:C050.0001: input,hidraw0: USB HID v1.10 Mouse [Logitech USB-PS/2 Optical Mouse] on usb-0000:00:12.0-1/input0
[    2.593881] ata6: SATA link down (SStatus 0 SControl 300)
[    2.653966] usb 4-2: new full-speed USB device number 3 using ohci-pci
[    2.695022] md: bind<sda1>
[    2.697607] md: raid1 personality registered for level 1
[    2.697859] md/raid1:md2: active with 1 out of 2 mirrors
[    2.697873] md2: detected capacity change from 0 to 2000263667712
[    2.735458]  md2: unknown partition table
[    2.877399] usb 4-2: New USB device found, idVendor=1852, idProduct=7022
[    2.877406] usb 4-2: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[    2.877411] usb 4-2: Product: UAC1 DAC
[    2.877415] usb 4-2: Manufacturer: Binary Audio
[    2.893545] input: Binary Audio UAC1 DAC as /devices/pci0000:00/0000:00:12.0/usb4/4-2/4-2:1.0/input/input4
[    2.893734] hid-generic 0003:1852:7022.0002: input,hidraw1: USB HID v1.00 Device [Binary Audio UAC1 DAC] on usb-0000:00:12.0-2/input0
[    3.155169] md: linear personality registered for level -1
[    3.157519] md: multipath personality registered for level -4
[    3.159847] md: raid0 personality registered for level 0
[    3.230676] raid6: sse2x1    6668 MB/s
[    3.298773] raid6: sse2x2    8751 MB/s
[    3.366874] raid6: sse2x4    8983 MB/s
[    3.366876] raid6: using algorithm sse2x4 (8983 MB/s)
[    3.366878] raid6: using ssse3x2 recovery algorithm
[    3.366897] Switched to clocksource tsc
[    3.368052] xor: automatically using best checksumming function:
[    3.406924]    avx       :  4960.000 MB/sec
[    3.408135] async_tx: api initialized (async)
[    3.414144] md: raid6 personality registered for level 6
[    3.414145] md: raid5 personality registered for level 5
[    3.414147] md: raid4 personality registered for level 4
[    3.419375] md: raid10 personality registered for level 10
[    3.465563] EXT4-fs (sdb1): mounted filesystem with ordered data mode. Opts: (null)
[    3.668734] random: init urandom read with 98 bits of entropy available
[    4.069361] random: nonblocking pool is initialized
[    5.447822] EXT4-fs (sdb1): re-mounted. Opts: errors=remount-ro
[    5.507333] EXT4-fs (sdc1): mounted filesystem with ordered data mode. Opts: (null)
[    6.464032] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[    6.501069] systemd-udevd[535]: starting version 204
[    6.514400] FS-Cache: Loaded
[    6.521845] RPC: Registered named UNIX socket transport module.
[    6.521849] RPC: Registered udp transport module.
[    6.521851] RPC: Registered tcp transport module.
[    6.521853] RPC: Registered tcp NFSv4.1 backchannel transport module.
[    6.534338] FS-Cache: Netfs 'nfs' registered for caching
[    6.550136] Installing knfsd (copyright (C) 1996 okir@monad.swb.de).
[    6.552880] lp: driver loaded but no devices found
[    6.603739] MCE: In-kernel MCE decoding enabled.
[    6.610437] piix4_smbus 0000:00:14.0: SMBus Host Controller at 0xb00, revision 0
[    6.610499] piix4_smbus 0000:00:14.0: Auxiliary SMBus Host Controller at 0xb20
[    6.612251] EDAC MC: Ver: 3.0.0
[    6.618057] init: idmapd-mounting (/mnt/nasdisk) main process (483) killed by TERM signal
[    6.618986] sp5100_tco: SP5100/SB800 TCO WatchDog Timer Driver v0.05
[    6.619080] AMD64 EDAC driver v3.4.0
[    6.619110] EDAC amd64: DRAM ECC disabled.
[    6.619117] EDAC amd64: ECC disabled in the BIOS or no ECC capability, module will not load.
[    6.619117]  Either enable ECC checking or force module loading by setting 'ecc_enable_override'.
[    6.619117]  (Note that use of the override may cause unknown side effects.)
[    6.620442] sp5100_tco: PCI Revision ID: 0x42
[    6.620486] sp5100_tco: Using 0xfed80b00 for watchdog MMIO address
[    6.620498] sp5100_tco: Last reboot was not triggered by watchdog.
[    6.620554] sp5100_tco: initialized (0xffffc90011ca6b00). heartbeat=60 sec (nowayout=0)
[    6.635927] Bluetooth: Core ver 2.17
[    6.635945] NET: Registered protocol family 31
[    6.635946] Bluetooth: HCI device and connection manager initialized
[    6.635954] Bluetooth: HCI socket layer initialized
[    6.635956] Bluetooth: L2CAP socket layer initialized
[    6.635960] Bluetooth: SCO socket layer initialized
[    6.639454] hda-intel 0000:00:14.2: Using LPIB position fix
[    6.640900] ppdev: user-space parallel port driver
[    6.643196] hda-intel 0000:00:14.2: Enable sync_write for stable communication
[    6.646758] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[    6.646761] Bluetooth: BNEP filters: protocol multicast
[    6.646769] Bluetooth: BNEP socket layer initialized
[    6.656051] Bluetooth: RFCOMM TTY layer initialized
[    6.656062] Bluetooth: RFCOMM socket layer initialized
[    6.656067] Bluetooth: RFCOMM ver 1.11
[    6.659635] SKU: Nid=0x1d sku_cfg=0x4007e629
[    6.659638] SKU: port_connectivity=0x1
[    6.659640] SKU: enable_pcbeep=0x0
[    6.659641] SKU: check_sum=0x00000007
[    6.659643] SKU: customization=0x000000e6
[    6.659644] SKU: external_amp=0x5
[    6.659646] SKU: platform_type=0x0
[    6.659647] SKU: swap=0x0
[    6.659648] SKU: override=0x1
[    6.660099] autoconfig: line_outs=4 (0x14/0x15/0x16/0x17/0x0) type:line
[    6.660101]    speaker_outs=0 (0x0/0x0/0x0/0x0/0x0)
[    6.660102]    hp_outs=1 (0x1b/0x0/0x0/0x0/0x0)
[    6.660104]    mono: mono_out=0x0
[    6.660105]    dig-out=0x11/0x1e
[    6.660107]    inputs:
[    6.660109]      Front Mic=0x19
[    6.660110]      Rear Mic=0x18
[    6.660112]      Line=0x1a
[    6.660114] realtek: No valid SSID, checking pincfg 0x4007e629 for NID 0x1d
[    6.660116] realtek: Enabling init ASM_ID=0xe629 CODEC_ID=10ec0892
[    6.674090] input: HDA ATI SB Front Headphone as /devices/pci0000:00/0000:00:14.2/sound/card0/input12
[    6.675957] input: HDA ATI SB Line Out Side as /devices/pci0000:00/0000:00:14.2/sound/card0/input11
[    6.676409] input: HDA ATI SB Line Out CLFE as /devices/pci0000:00/0000:00:14.2/sound/card0/input10
[    6.676933] input: HDA ATI SB Line Out Surround as /devices/pci0000:00/0000:00:14.2/sound/card0/input9
[    6.677269] input: HDA ATI SB Line Out Front as /devices/pci0000:00/0000:00:14.2/sound/card0/input8
[    6.677829] input: HDA ATI SB Line as /devices/pci0000:00/0000:00:14.2/sound/card0/input7
[    6.678841] input: HDA ATI SB Rear Mic as /devices/pci0000:00/0000:00:14.2/sound/card0/input6
[    6.678925] input: HDA ATI SB Front Mic as /devices/pci0000:00/0000:00:14.2/sound/card0/input5
[    6.679273] hda-intel 0000:01:00.1: Handle VGA-switcheroo audio client
[    6.679276] hda-intel 0000:01:00.1: Using LPIB position fix
[    6.679314] snd_hda_intel 0000:01:00.1: irq 91 for MSI/MSI-X
[    6.685094] hda-intel 0000:01:00.1: Enable sync_write for stable communication
[    6.691588] HDMI ATI/AMD: no speaker allocation for ELD
[    6.691656] input: HDA ATI HDMI HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:02.0/0000:01:00.1/sound/card1/input13
[    6.733780] type=1400 audit(1414360398.500:2): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/cups/backend/cups-pdf" pid=858 comm="apparmor_parser"
[    6.733788] type=1400 audit(1414360398.500:3): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/sbin/cupsd" pid=858 comm="apparmor_parser"
[    6.734141] type=1400 audit(1414360398.500:4): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/sbin/cupsd" pid=858 comm="apparmor_parser"
[    6.735069] kvm: Nested Virtualization enabled
[    6.735075] kvm: Nested Paging enabled
[    6.740407] type=1400 audit(1414360398.508:5): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/sbin/dhclient" pid=866 comm="apparmor_parser"
[    6.740414] type=1400 audit(1414360398.508:6): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=866 comm="apparmor_parser"
[    6.740419] type=1400 audit(1414360398.508:7): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=866 comm="apparmor_parser"
[    6.740781] type=1400 audit(1414360398.508:8): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=866 comm="apparmor_parser"
[    6.740788] type=1400 audit(1414360398.508:9): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=866 comm="apparmor_parser"
[    6.741025] type=1400 audit(1414360398.508:10): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=866 comm="apparmor_parser"
[    6.782054] asus_wmi: ASUS WMI generic driver loaded
[    6.784531] asus_wmi: Initialization: 0x0
[    6.784564] asus_wmi: BIOS WMI version: 0.9
[    6.784630] asus_wmi: SFUN value: 0x0
[    6.785110] input: Eee PC WMI hotkeys as /devices/platform/eeepc-wmi/input/input14
[    6.788814] asus_wmi: Disabling ACPI video driver
[    6.796101] usbcore: registered new interface driver snd-usb-audio
[    6.803338] init: cups main process (867) killed by HUP signal
[    6.803348] init: cups main process ended, respawning
[    6.958123] init: failsafe main process (938) killed by TERM signal
[    6.967407] init: Failed to obtain startpar-bridge instance: Unknown parameter: INSTANCE
[    7.041055] init: statd-mounting (/mnt/nasdisk) main process (484) killed by TERM signal
[    7.049986] init: samba-ad-dc main process (1020) terminated with status 1
[    7.057306] NFS: Registering the id_resolver key type
[    7.057317] Key type id_resolver registered
[    7.057319] Key type id_legacy registered
[    7.108095] type=1400 audit(1414360398.872:11): apparmor="STATUS" operation="profile_load" profile="unconfined" name="docker-default" pid=1126 comm="apparmor_parser"
[    7.192829] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[    7.193094] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[    7.542270] ip_tables: (C) 2000-2006 Netfilter Core Team
[    7.566181] Bridge firewalling registered
[    7.593669] nf_conntrack version 0.5.0 (16384 buckets, 65536 max)
[    7.796251] vboxdrv: Found 8 processor cores.
[    7.797456] vboxdrv: fAsync=0 offMin=0x34f offMax=0x162b6
[    7.797554] vboxdrv: TSC mode is 'synchronous', kernel timer mode is 'normal'.
[    7.797555] vboxdrv: Successfully loaded version 4.3.18 (interface 0x001a0008).
[    7.864043] Ebtables v2.0 registered
[    7.874877] ip6_tables: (C) 2000-2006 Netfilter Core Team
[    8.008704] vboxpci: IOMMU not found (not registered)
[    8.380684] init: plymouth-upstart-bridge main process ended, respawning
[    8.388135] init: plymouth-upstart-bridge main process (1797) terminated with status 1
[    8.388148] init: plymouth-upstart-bridge main process ended, respawning
[   10.163470] IPv6: ADDRCONF(NETDEV_UP): virbr0: link is not ready
[   10.172554] ------------[ cut here ]------------
[   10.172561] WARNING: CPU: 1 PID: 190 at /build/buildd/linux-3.13.0/fs/proc/generic.c:522 remove_proc_entry+0x19f/0x1b0()
[   10.172563] remove_proc_entry: removing non-empty directory 'fs/nfsfs', leaking at least 'volumes'
[   10.172564] Modules linked in: xt_conntrack ipt_REJECT snd_hrtimer pci_stub vboxpci(OX) vboxnetadp(OX) vboxnetflt(OX) ip6table_filter ip6_tables ebtable_nat ebtables vboxdrv(OX) xt_CHECKSUM iptable_mangle ipt_MASQUERADE iptable_nat nf_conntrack_ipv4 nf_defrag_ipv4 nf_nat_ipv4 nf_nat nf_conntrack xt_tcpudp bridge stp llc iptable_filter ip_tables x_tables nfsv4 eeepc_wmi asus_wmi sparse_keymap video kvm_amd kvm crct10dif_pclmul crc32_pclmul ghash_clmulni_intel snd_usb_audio snd_usbmidi_lib snd_hda_codec_hdmi aesni_intel aes_x86_64 lrw snd_hda_codec_realtek gf128mul rfcomm glue_helper ablk_helper parport_pc bnep cryptd snd_hda_intel ppdev bluetooth snd_hda_codec snd_hwdep snd_seq_midi serio_raw snd_pcm sp5100_tco snd_seq_midi_event k10temp edac_core i2c_piix4 fam15h_power edac_mce_amd snd_rawmidi snd_page_alloc snd_seq snd_seq_device snd_timer snd soundcore mac_hid binfmt_misc nfsd lp auth_rpcgss nfs_acl parport nfs lockd sunrpc fscache raid10 raid456 async_raid6_recov async_memcpy async_pq async_xor async_tx xor raid6_pq raid0 multipath linear raid1 hid_generic usbhid hid mxm_wmi radeon firewire_ohci firewire_core crc_itu_t i2c_algo_bit ttm drm_kms_helper ahci libahci drm wmi r8168(OX)
[   10.172620] CPU: 1 PID: 190 Comm: kworker/u16:7 Tainted: G           OX 3.13.0-37-generic #64-Ubuntu
[   10.172622] Hardware name: To be filled by O.E.M. To be filled by O.E.M./M5A97 EVO R2.0, BIOS 2201 11/25/2013
[   10.172626] Workqueue: netns cleanup_net
[   10.172627]  0000000000000009 ffff880422d41c80 ffffffff8171ed09 ffff880422d41cc8
[   10.172631]  ffff880422d41cb8 ffffffff8106773d ffff8804224b2800 0000000000000005
[   10.172633]  ffffffffa03e28a8 ffff880421b36f30 ffff8804224b2875 ffff880422d41d18
[   10.172636] Call Trace:
[   10.172640]  [<ffffffff8171ed09>] dump_stack+0x45/0x56
[   10.172643]  [<ffffffff8106773d>] warn_slowpath_common+0x7d/0xa0
[   10.172647]  [<ffffffff810677ac>] warn_slowpath_fmt+0x4c/0x50
[   10.172649]  [<ffffffff8122989f>] remove_proc_entry+0x19f/0x1b0
[   10.172666]  [<ffffffffa03c24e2>] nfs_fs_proc_net_exit+0x62/0x70 [nfs]
[   10.172675]  [<ffffffffa03c85b2>] nfs_net_exit+0x12/0x20 [nfs]
[   10.172677]  [<ffffffff8161b409>] ops_exit_list.isra.1+0x39/0x60
[   10.172681]  [<ffffffff8161bc90>] cleanup_net+0x110/0x250
[   10.172684]  [<ffffffff810839c2>] process_one_work+0x182/0x450
[   10.172686]  [<ffffffff810847b1>] worker_thread+0x121/0x410
[   10.172689]  [<ffffffff81084690>] ? rescuer_thread+0x430/0x430
[   10.172691]  [<ffffffff8108b492>] kthread+0xd2/0xf0
[   10.172694]  [<ffffffff8108b3c0>] ? kthread_create_on_node+0x1c0/0x1c0
[   10.172696]  [<ffffffff8172f77c>] ret_from_fork+0x7c/0xb0
[   10.172698]  [<ffffffff8108b3c0>] ? kthread_create_on_node+0x1c0/0x1c0
[   10.172700] ---[ end trace 09a7d6631cda25b7 ]---
[   11.743838] retire_capture_urb: 1465 callbacks suppressed
[   12.212936] r8168: eth0: link up
[   12.212967] IPv6: ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   14.457400] RPC: AUTH_GSS upcall failed. Please check user daemon is running.
[   14.501975] aufs 3.13-20140303
[   14.540805] IPv6: ADDRCONF(NETDEV_UP): docker0: link is not ready
[   14.929957] netlink: 1 bytes leftover after parsing attributes in process `docker.io'.
[   14.930489] device veth566c entered promiscuous mode
[   14.930661] IPv6: ADDRCONF(NETDEV_UP): veth566c: link is not ready
[   14.930665] docker0: port 1(veth566c) entered forwarding state
[   14.930674] docker0: port 1(veth566c) entered forwarding state
[   14.955500] IPv6: ADDRCONF(NETDEV_CHANGE): veth566c: link becomes ready
[   14.955557] IPv6: ADDRCONF(NETDEV_CHANGE): docker0: link becomes ready
[   25.671381] retire_capture_urb: 1391 callbacks suppressed
[   29.971939] docker0: port 1(veth566c) entered forwarding state
[   30.682428] retire_capture_urb: 2492 callbacks suppressed
[   36.846403] audit_printk_skb: 68 callbacks suppressed
[   36.846406] type=1400 audit(1414360428.580:80): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/cups/backend/cups-pdf" pid=3613 comm="apparmor_parser"
[   36.846412] type=1400 audit(1414360428.580:81): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/sbin/cupsd" pid=3613 comm="apparmor_parser"
[   36.846756] type=1400 audit(1414360428.580:82): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/sbin/cupsd" pid=3613 comm="apparmor_parser"
[ 3409.978408] systemd-hostnamed[15960]: Warning: nss-myhostname is not installed. Changing the local hostname might make it unresolveable. Please install nss-myhostname!
```

---

### Post by tgalati4 on 2014-10-27
Even I get lucky once in a while.

When you boot in BIOS, sometimes there is a "Health Management" or "Performance Monitor" that will give voltages.  Unfortunately, that is only a snapshot, since the real load that happens during boot can only be measured when you are booting normally.  Using a voltmeter attached to one of your harddisk connectors or stuck into the backside of the motherboard power header (black and yellow wires) you can watch the 12VDC during boot.  If it sags too much, then your disks don't spin up to speed quickly enough to be enumerated.  The "double-pump" allows the disks to spin up and stay spinning, which reduces current load and allows the disks to get up to speed.  SSD's can use a lot of current.

A power supply can fail in the 12VDC circuit only, and not exceed the total watts as displayed in your kill-a-watt.

---

### Post by WinEunuchs2Unix on 2014-10-27
> **tgalati4 said:**
> Even I get lucky once in a while.

When you boot in BIOS, sometimes there is a "Health Management" or "Performance Monitor" that will give voltages.  Unfortunately, that is only a snapshot, since the real load that happens during boot can only be measured when you are booting normally.  Using a voltmeter attached to one of your harddisk connectors or stuck into the backside of the motherboard power header (black and yellow wires) you can watch the 12VDC during boot.  If it sags too much, then your disks don't spin up to speed quickly enough to be enumerated.  The "double-pump" allows the disks to spin up and stay spinning, which reduces current load and allows the disks to get up to speed.  SSD's can use a lot of current.

A power supply can fail in the 12VDC circuit only, and not exceed the total watts as displayed in your kill-a-watt.

Congrats tgalati4.  If I knew how to vote you up I would.

Gotta love the depth of knowledge in these forums.  I for one would never have imagined the multi-meter purchased for my car and house could be used on a PC in the fashion you detailed.

---

