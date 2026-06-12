---
title: "Modem Huawei E156G on Ubuntu 10.10"
date: 2011-01-16
forum: Hardware
---

### Post by vmalep on 2011-01-16
Hi,

I am connecting my computer to internet through a Huawei E156G modem on Ubuntu 10.10. It was working fine with older version of Ubuntu (9.04 and 9.10), but I am experiencing strange problems with the last one:
If I plug the modem at the beginning of the boot in a live session, it works fine, even if I unplug it and plug it back after login. But if I plug the modem only after the live session has logged in or on a installed system, the modem is not recongnized as a modem and does not work.

Hereunder are the dmesg outputs for the 2 cases scenario.

Thanks for your help!
Pierre

Modem plugged during the boot and unplugged-replugged after login:
```

[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.35-22-generic (buildd@rothera) (gcc version 4.4.5 (Ubuntu/Linaro 4.4.4-14ubuntu4) ) #33-Ubuntu SMP Sun Sep 19 20:34:50 UTC 2010 (Ubuntu 2.6.35-22.33-generic 2.6.35.4)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000003f7d0000 (usable)
[    0.000000]  BIOS-e820: 000000003f7d0000 - 000000003f7efc00 (reserved)
[    0.000000]  BIOS-e820: 000000003f7efc00 - 000000003f7fb000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000003f7fb000 - 000000003f800000 (reserved)
[    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec02000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed20000 - 00000000fed9b000 (reserved)
[    0.000000]  BIOS-e820: 00000000feda0000 - 00000000fedc0000 (reserved)
[    0.000000]  BIOS-e820: 00000000ffb00000 - 00000000ffc00000 (reserved)
[    0.000000]  BIOS-e820: 00000000fff00000 - 0000000100000000 (reserved)
[    0.000000] Notice: NX (Execute Disable) protection cannot be enabled: non-PAE kernel!
[    0.000000] DMI 2.3 present.
[    0.000000] e820 update range: 0000000000000000 - 0000000000001000 (usable) ==> (reserved)
[    0.000000] e820 remove range: 00000000000a0000 - 0000000000100000 (usable)
[    0.000000] last_pfn = 0x3f7d0 max_arch_pfn = 0x100000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-CFFFF write-protect
[    0.000000]   D0000-EFFFF uncachable
[    0.000000]   F0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000 mask FC0000000 write-back
[    0.000000]   1 base 03F800000 mask FFF800000 uncachable
[    0.000000]   2 base 0FEDA0000 mask FFFFE0000 uncachable
[    0.000000]   3 disabled
[    0.000000]   4 disabled
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] PAT not supported by CPU.
[    0.000000] e820 update range: 0000000000002000 - 0000000000010000 (usable) ==> (reserved)
[    0.000000] Scanning 1 areas for low memory corruption
[    0.000000] modified physical RAM map:
[    0.000000]  modified: 0000000000000000 - 0000000000001000 (reserved)
[    0.000000]  modified: 0000000000001000 - 0000000000002000 (usable)
[    0.000000]  modified: 0000000000002000 - 0000000000010000 (reserved)
[    0.000000]  modified: 0000000000010000 - 000000000009fc00 (usable)
[    0.000000]  modified: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  modified: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  modified: 0000000000100000 - 000000003f7d0000 (usable)
[    0.000000]  modified: 000000003f7d0000 - 000000003f7efc00 (reserved)
[    0.000000]  modified: 000000003f7efc00 - 000000003f7fb000 (ACPI NVS)
[    0.000000]  modified: 000000003f7fb000 - 000000003f800000 (reserved)
[    0.000000]  modified: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  modified: 00000000fec00000 - 00000000fec02000 (reserved)
[    0.000000]  modified: 00000000fed20000 - 00000000fed9b000 (reserved)
[    0.000000]  modified: 00000000feda0000 - 00000000fedc0000 (reserved)
[    0.000000]  modified: 00000000ffb00000 - 00000000ffc00000 (reserved)
[    0.000000]  modified: 00000000fff00000 - 0000000100000000 (reserved)
[    0.000000] initial memory mapped : 0 - 00c00000
[    0.000000] init_memory_mapping: 0000000000000000-00000000377fe000
[    0.000000]  0000000000 - 0000400000 page 4k
[    0.000000]  0000400000 - 0037400000 page 2M
[    0.000000]  0037400000 - 00377fe000 page 4k
[    0.000000] kernel direct mapping tables up to 377fe000 @ 15000-1a000
[    0.000000] RAMDISK: 3ecef000 - 3f7d0000
[    0.000000] Allocated new RAMDISK: 009a5000 - 0148516f
[    0.000000] Move RAMDISK from 000000003ecef000 - 000000003f7cf16e to 009a5000 - 0148516e
[    0.000000] ACPI: RSDP 000fe270 00014 (v00 HP    )
[    0.000000] ACPI: RSDT 3f7efc84 00038 (v01 HP     0944     21110520 HP   00000001)
[    0.000000] ACPI: FACP 3f7efc00 00084 (v02 HP     0944     00000002 HP   00000001)
[    0.000000] ACPI: DSDT 3f7efd54 08345 (v01 HP       nc6200 00010000 MSFT 0100000E)
[    0.000000] ACPI: FACS 3f7fae80 00040
[    0.000000] ACPI: APIC 3f7efcbc 0005A (v01 HP     0944     00000001 HP   00000001)
[    0.000000] ACPI: MCFG 3f7efd18 0003C (v01 HP     0944     00000001 HP   00000001)
[    0.000000] ACPI: SSDT 3f7f8099 00371 (v01 HP       HPQPpc 00001001 MSFT 0100000E)
[    0.000000] ACPI: SSDT 3f7f840a 00059 (v01 HP       HPQNLP 00000001 MSFT 0100000E)
[    0.000000] ACPI: Local APIC address 0xfec01000
[    0.000000] 127MB HIGHMEM available.
[    0.000000] 887MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 377fe000
[    0.000000]   low ram: 0 - 377fe000
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000001 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x000377fe
[    0.000000]   HighMem  0x000377fe -> 0x0003f7d0
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[3] active PFN ranges
[    0.000000]     0: 0x00000001 -> 0x00000002
[    0.000000]     0: 0x00000010 -> 0x0000009f
[    0.000000]     0: 0x00000100 -> 0x0003f7d0
[    0.000000] On node 0 totalpages: 259936
[    0.000000] free_area_init_node: node 0, pgdat c07ffd40, node_mem_map c1487020
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3952 pages, LIFO batch:0
[    0.000000]   Normal zone: 1744 pages used for memmap
[    0.000000]   Normal zone: 221486 pages, LIFO batch:31
[    0.000000]   HighMem zone: 256 pages used for memmap
[    0.000000]   HighMem zone: 32466 pages, LIFO batch:7
[    0.000000] Using APIC driver default
[    0.000000] ACPI: PM-Timer IO Port: 0x1008
[    0.000000] ACPI: Local APIC address 0xfec01000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 1, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] SMP: Allowing 1 CPUs, 0 hotplug CPUs
[    0.000000] nr_irqs_gsi: 40
[    0.000000] early_res array is doubled to 64 at [16000 - 167ff]
[    0.000000] PM: Registered nosave memory: 0000000000002000 - 0000000000010000
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
[    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 3f800000 (gap: 3f800000:a0800000)
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] setup_percpu: NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:1 nr_node_ids:1
[    0.000000] PERCPU: Embedded 14 pages/cpu @c2000000 s36416 r0 d20928 u4194304
[    0.000000] pcpu-alloc: s36416 r0 d20928 u4194304 alloc=1*4194304
[    0.000000] pcpu-alloc: [0] 0 
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 257904
[    0.000000] Kernel command line: file=/cdrom/preseed/edubuntu.seed boot=casper initrd=/casper/initrd.lz quiet splash -- console-setup/layoutcode=ch console-setup/variantcode=fr
[    0.000000] PID hash table entries: 4096 (order: 2, 16384 bytes)
[    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] allocated 5200940 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] Subtract (47 early reservations)
[    0.000000]   #1 [0000001000 - 0000002000]   EX TRAMPOLINE
[    0.000000]   #2 [0000100000 - 00009a0adc]   TEXT DATA BSS
[    0.000000]   #3 [000009fc00 - 0000100000]   BIOS reserved
[    0.000000]   #4 [00009a1000 - 00009a415c]             BRK
[    0.000000]   #5 [0000010000 - 0000011000]      TRAMPOLINE
[    0.000000]   #6 [0000011000 - 0000015000]     ACPI WAKEUP
[    0.000000]   #7 [0000015000 - 0000016000]         PGTABLE
[    0.000000]   #8 [00009a5000 - 0001486000]     NEW RAMDISK
[    0.000000]   #9 [0001486000 - 0001487000]         BOOTMEM
[    0.000000]   #10 [0001487000 - 0001c77000]         BOOTMEM
[    0.000000]   #11 [0001c77000 - 0001c77004]         BOOTMEM
[    0.000000]   #12 [0001c77040 - 0001c77100]         BOOTMEM
[    0.000000]   #13 [0001c77100 - 0001c77154]         BOOTMEM
[    0.000000]   #14 [0001c77180 - 0001c7a180]         BOOTMEM
[    0.000000]   #15 [0001c7a180 - 0001c7a18c]         BOOTMEM
[    0.000000]   #16 [0001c7a1c0 - 0001c7a7c0]         BOOTMEM
[    0.000000]   #17 [0001c7a7c0 - 0001c7a7e7]         BOOTMEM
[    0.000000]   #18 [0001c7a800 - 0001c7a9c0]         BOOTMEM
[    0.000000]   #19 [0001c7a9c0 - 0001c7aa00]         BOOTMEM
[    0.000000]   #20 [0001c7aa00 - 0001c7aa40]         BOOTMEM
[    0.000000]   #21 [0001c7aa40 - 0001c7aa80]         BOOTMEM
[    0.000000]   #22 [0001c7aa80 - 0001c7aac0]         BOOTMEM
[    0.000000]   #23 [0001c7aac0 - 0001c7ab00]         BOOTMEM
[    0.000000]   #24 [0001c7ab00 - 0001c7ab40]         BOOTMEM
[    0.000000]   #25 [0001c7ab40 - 0001c7ab80]         BOOTMEM
[    0.000000]   #26 [0001c7ab80 - 0001c7abc0]         BOOTMEM
[    0.000000]   #27 [0001c7abc0 - 0001c7ac00]         BOOTMEM
[    0.000000]   #28 [0001c7ac00 - 0001c7ac40]         BOOTMEM
[    0.000000]   #29 [0001c7ac40 - 0001c7ac80]         BOOTMEM
[    0.000000]   #30 [0001c7ac80 - 0001c7acc0]         BOOTMEM
[    0.000000]   #31 [0001c7acc0 - 0001c7ad00]         BOOTMEM
[    0.000000]   #32 [0001c7ad00 - 0001c7ad10]         BOOTMEM
[    0.000000]   #33 [0001c7ad40 - 0001c7ad50]         BOOTMEM
[    0.000000]   #34 [0001c7ad80 - 0001c7ae10]         BOOTMEM
[    0.000000]   #35 [0001c7ae40 - 0001c7aed0]         BOOTMEM
[    0.000000]   #36 [0002000000 - 000200e000]         BOOTMEM
[    0.000000]   #37 [0001c7cf00 - 0001c7cf04]         BOOTMEM
[    0.000000]   #38 [0001c7cf40 - 0001c7cf44]         BOOTMEM
[    0.000000]   #39 [0001c7cf80 - 0001c7cf84]         BOOTMEM
[    0.000000]   #40 [0001c7cfc0 - 0001c7cfc4]         BOOTMEM
[    0.000000]   #41 [0001c7d000 - 0001c7d0b0]         BOOTMEM
[    0.000000]   #42 [0001c7d0c0 - 0001c7d168]         BOOTMEM
[    0.000000]   #43 [0001c7d180 - 0001c81180]         BOOTMEM
[    0.000000]   #44 [0001c81180 - 0001d01180]         BOOTMEM
[    0.000000]   #45 [0001d01180 - 0001d41180]         BOOTMEM
[    0.000000]   #46 [000200e000 - 0002503c2c]         BOOTMEM
[    0.000000] Initializing HighMem for node 0 (000377fe:0003f7d0)
[    0.000000] Memory: 1005648k/1040192k available (4928k kernel code, 34096k reserved, 2336k data, 684k init, 130888k highmem)
[    0.000000] virtual kernel memory layout:
[    0.000000]     fixmap  : 0xfff16000 - 0xfffff000   ( 932 kB)
[    0.000000]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[    0.000000]     vmalloc : 0xf7ffe000 - 0xff7fe000   ( 120 MB)
[    0.000000]     lowmem  : 0xc0000000 - 0xf77fe000   ( 887 MB)
[    0.000000]       .init : 0xc0819000 - 0xc08c4000   ( 684 kB)
[    0.000000]       .data : 0xc05d029e - 0xc0818668   (2336 kB)
[    0.000000]       .text : 0xc0100000 - 0xc05d029e   (4928 kB)
[    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.000000] SLUB: Genslabs=13, HWalign=64, Order=0-3, MinObjects=0, CPUs=1, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000] 	RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000] 	RCU-based detection of stalled CPUs is disabled.
[    0.000000] 	Verbose stalled-CPUs detection is disabled.
[    0.000000] NR_IRQS:2304 nr_irqs:256
[    0.000000] Console: colour VGA+ 80x25
[    0.000000] console [tty0] enabled
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 798.087 MHz processor.
[    0.004007] Calibrating delay loop (skipped), value calculated using timer frequency.. 1596.17 BogoMIPS (lpj=3192348)
[    0.004020] pid_max: default: 32768 minimum: 301
[    0.004068] Security Framework initialized
[    0.004107] AppArmor: AppArmor initialized
[    0.004114] Yama: becoming mindful.
[    0.004244] Mount-cache hash table entries: 512
[    0.004511] Initializing cgroup subsys ns
[    0.004520] Initializing cgroup subsys cpuacct
[    0.004531] Initializing cgroup subsys memory
[    0.004554] Initializing cgroup subsys devices
[    0.004560] Initializing cgroup subsys freezer
[    0.004566] Initializing cgroup subsys net_cls
[    0.004627] mce: CPU supports 5 MCE banks
[    0.004645] CPU0: Thermal monitoring enabled (TM2)
[    0.004660] Performance Events: p6 PMU driver.
[    0.004678] ... version:                0
[    0.004683] ... bit width:              32
[    0.004688] ... generic registers:      2
[    0.004693] ... value mask:             00000000ffffffff
[    0.004699] ... max period:             000000007fffffff
[    0.004704] ... fixed-purpose events:   0
[    0.004710] ... event mask:             0000000000000003
[    0.006619] SMP alternatives: switching to UP code
[    0.024871] Freeing SMP alternatives: 24k freed
[    0.024890] ACPI: Core revision 20100428
[    0.048033] ftrace: converting mcount calls to 0f 1f 44 00 00
[    0.048050] ftrace: allocating 21758 entries in 43 pages
[    0.052092] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.052492] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.094822] CPU0: Intel(R) Pentium(R) M processor 1.86GHz stepping 08
[    0.096000] Brought up 1 CPUs
[    0.096000] Total of 1 processors activated (1596.17 BogoMIPS).
[    0.096000] devtmpfs: initialized
[    0.096000] HP Compaq Laptop series board detected. Selecting BIOS-method for reboots.
[    0.096000] regulator: core version 0.5
[    0.096000] Time: 13:45:36  Date: 01/16/11
[    0.096000] NET: Registered protocol family 16
[    0.096170] EISA bus registered
[    0.096188] ACPI: bus type pci registered
[    0.096338] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xe0000000-0xefffffff] (base 0xe0000000)
[    0.096347] PCI: MMCONFIG at [mem 0xe0000000-0xefffffff] reserved in E820
[    0.096352] PCI: Using MMCONFIG for extended config space
[    0.096358] PCI: Using configuration type 1 for base access
[    0.098766] bio: create slab <bio-0> at 0
[    0.102303] ACPI: EC: Look up EC in DSDT
[    0.152307] ACPI: Interpreter enabled
[    0.152320] ACPI: (supports S0 S3 S4 S5)
[    0.152368] ACPI: Using IOAPIC for interrupt routing
[    0.180680] ACPI: EC: GPE = 0x10, I/O: command/status = 0x66, data = 0x62
[    0.180872] ACPI: Power Resource [C1CF] (on)
[    0.181225] ACPI: Power Resource [C1A9] (on)
[    0.181581] ACPI: Power Resource [C1B1] (on)
[    0.181908] ACPI: Power Resource [C1B8] (on)
[    0.182004] ACPI: Power Resource [C1C8] (on)
[    0.182229] ACPI: Power Resource [C24F] (off)
[    0.182431] ACPI: Power Resource [C250] (off)
[    0.182631] ACPI: Power Resource [C251] (off)
[    0.182832] ACPI: Power Resource [C252] (off)
[    0.183458] ACPI: No dock devices found.
[    0.183470] PCI: Ignoring host bridge windows from ACPI; if necessary, use "pci=use_crs" and report a bug
[    0.194784] ACPI: PCI Root Bridge [C002] (domain 0000 [bus 00-ff])
[    0.217444] pci_root PNP0A08:00: host bridge window [io  0x0000-0x0cf7] (ignored)
[    0.217453] pci_root PNP0A08:00: host bridge window [io  0x0d00-0xffff] (ignored)
[    0.217461] pci_root PNP0A08:00: host bridge window [mem 0x000a0000-0x000bffff] (ignored)
[    0.217469] pci_root PNP0A08:00: host bridge window [mem 0x3f800000-0xfec00fff] (ignored)
[    0.217477] pci_root PNP0A08:00: host bridge window [mem 0xfec02000-0xffffffff] (ignored)
[    0.217485] pci_root PNP0A08:00: host bridge window [mem 0x000d0000-0x000dffff] (ignored)
[    0.217577] pci 0000:00:02.0: reg 10: [mem 0xd0800000-0xd087ffff]
[    0.217588] pci 0000:00:02.0: reg 14: [io  0x5000-0x5007]
[    0.217598] pci 0000:00:02.0: reg 18: [mem 0xc0000000-0xcfffffff pref]
[    0.217608] pci 0000:00:02.0: reg 1c: [mem 0xd0880000-0xd08bffff]
[    0.217658] pci 0000:00:02.1: reg 10: [mem 0xd0900000-0xd097ffff]
[    0.217849] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.217858] pci 0000:00:1c.0: PME# disabled
[    0.217979] pci 0000:00:1c.1: PME# supported from D0 D3hot D3cold
[    0.217988] pci 0000:00:1c.1: PME# disabled
[    0.218074] pci 0000:00:1d.0: reg 20: [io  0x2000-0x201f]
[    0.218152] pci 0000:00:1d.1: reg 20: [io  0x2020-0x203f]
[    0.218230] pci 0000:00:1d.2: reg 20: [io  0x2040-0x205f]
[    0.218307] pci 0000:00:1d.7: reg 10: [mem 0xd0980000-0xd09803ff]
[    0.218383] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
[    0.218393] pci 0000:00:1d.7: PME# disabled
[    0.218522] pci 0000:00:1e.2: reg 10: [io  0x2100-0x21ff]
[    0.218535] pci 0000:00:1e.2: reg 14: [io  0x2200-0x223f]
[    0.218548] pci 0000:00:1e.2: reg 18: [mem 0xd0981000-0xd09811ff]
[    0.218561] pci 0000:00:1e.2: reg 1c: [mem 0xd0982000-0xd09820ff]
[    0.218610] pci 0000:00:1e.2: PME# supported from D0 D3hot D3cold
[    0.218619] pci 0000:00:1e.2: PME# disabled
[    0.218664] pci 0000:00:1e.3: reg 10: [io  0x2400-0x24ff]
[    0.218677] pci 0000:00:1e.3: reg 14: [io  0x2500-0x257f]
[    0.218739] pci 0000:00:1e.3: PME# supported from D0 D3hot D3cold
[    0.218748] pci 0000:00:1e.3: PME# disabled
[    0.218859] pci 0000:00:1f.0: Force enabled HPET at 0xfed00000
[    0.218872] pci 0000:00:1f.0: quirk: [io  0x1000-0x107f] claimed by ICH6 ACPI/GPIO/TCO
[    0.218881] pci 0000:00:1f.0: quirk: [io  0x1100-0x113f] claimed by ICH6 GPIO
[    0.218891] pci 0000:00:1f.0: LPC Generic IO decode 1 PIO at 0500-057f
[    0.218935] pci 0000:00:1f.1: reg 10: [io  0x0000-0x0007]
[    0.218947] pci 0000:00:1f.1: reg 14: [io  0x0000-0x0003]
[    0.218960] pci 0000:00:1f.1: reg 18: [io  0x0000-0x0007]
[    0.218972] pci 0000:00:1f.1: reg 1c: [io  0x0000-0x0003]
[    0.218985] pci 0000:00:1f.1: reg 20: [io  0x2580-0x258f]
[    0.219156] pci 0000:10:00.0: reg 10: [mem 0xd0000000-0xd000ffff 64bit]
[    0.219267] pci 0000:10:00.0: PME# supported from D3hot D3cold
[    0.219277] pci 0000:10:00.0: PME# disabled
[    0.219306] pci 0000:10:00.0: disabling ASPM on pre-1.1 PCIe device.  You can enable it with 'pcie_aspm=force'
[    0.219329] pci 0000:00:1c.0: PCI bridge to [bus 10-10]
[    0.219339] pci 0000:00:1c.0:   bridge window [io  0xf000-0x0000] (disabled)
[    0.219350] pci 0000:00:1c.0:   bridge window [mem 0xd0000000-0xd03fffff]
[    0.219364] pci 0000:00:1c.0:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    0.219440] pci 0000:00:1c.1: PCI bridge to [bus 20-20]
[    0.219450] pci 0000:00:1c.1:   bridge window [io  0x0000-0x0000] (disabled)
[    0.219460] pci 0000:00:1c.1:   bridge window [mem 0x00000000-0x000fffff] (disabled)
[    0.219473] pci 0000:00:1c.1:   bridge window [mem 0x00000000-0x000fffff pref] (disabled)
[    0.219572] pci 0000:02:06.0: reg 10: [mem 0xd0400000-0xd0400fff]
[    0.219610] pci 0000:02:06.0: supports D1 D2
[    0.219616] pci 0000:02:06.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.219626] pci 0000:02:06.0: PME# disabled
[    0.219686] pci 0000:02:06.3: reg 10: [mem 0xd0402000-0xd0403fff]
[    0.219773] pci 0000:02:06.3: supports D1 D2
[    0.219778] pci 0000:02:06.3: PME# supported from D0 D1 D2 D3hot
[    0.219788] pci 0000:02:06.3: PME# disabled
[    0.219844] pci 0000:02:06.4: reg 10: [mem 0xd0404000-0xd04040ff]
[    0.219859] pci 0000:02:06.4: reg 14: [mem 0xd0405000-0xd04050ff]
[    0.219874] pci 0000:02:06.4: reg 18: [mem 0xd0406000-0xd04060ff]
[    0.219944] pci 0000:02:06.4: supports D1 D2
[    0.219950] pci 0000:02:06.4: PME# supported from D0 D1 D2 D3hot
[    0.219959] pci 0000:02:06.4: PME# disabled
[    0.220020] pci 0000:02:06.5: reg 10: [mem 0xd0407000-0xd0407fff]
[    0.220035] pci 0000:02:06.5: reg 14: [mem 0xd0408000-0xd0408fff]
[    0.220050] pci 0000:02:06.5: reg 18: [mem 0xd0409000-0xd0409fff]
[    0.220065] pci 0000:02:06.5: reg 1c: [mem 0xd040a000-0xd040afff]
[    0.220127] pci 0000:02:06.5: supports D1 D2
[    0.220133] pci 0000:02:06.5: PME# supported from D0 D1 D2 D3hot
[    0.220143] pci 0000:02:06.5: PME# disabled
[    0.220218] pci 0000:00:1e.0: PCI bridge to [bus 02-03] (subtractive decode)
[    0.220228] pci 0000:00:1e.0:   bridge window [io  0xf000-0x0000] (disabled)
[    0.220238] pci 0000:00:1e.0:   bridge window [mem 0xd0400000-0xd07fffff]
[    0.220251] pci 0000:00:1e.0:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    0.220259] pci 0000:00:1e.0:   bridge window [io  0x0000-0xffff] (subtractive decode)
[    0.220266] pci 0000:00:1e.0:   bridge window [mem 0x00000000-0xffffffff] (subtractive decode)
[    0.220338] pci_bus 0000:03: [bus 03-06] partially hidden behind transparent bridge 0000:02 [bus 02-03]
[    0.220370] pci_bus 0000:00: on NUMA node 0
[    0.220381] ACPI: PCI Interrupt Routing Table [\_SB_.C002._PRT]
[    0.220927] ACPI: PCI Interrupt Routing Table [\_SB_.C002.C06D._PRT]
[    0.221353] ACPI: PCI Interrupt Routing Table [\_SB_.C002.C006._PRT]
[    0.221579] ACPI: PCI Interrupt Routing Table [\_SB_.C002.C0DE._PRT]
[    0.287663] ACPI: PCI Interrupt Link [C0DA] (IRQs *10 11)
[    0.288133] ACPI: PCI Interrupt Link [C0DB] (IRQs 10 *11)
[    0.288584] ACPI: PCI Interrupt Link [C0DC] (IRQs 10 *11)
[    0.289037] ACPI: PCI Interrupt Link [C0DD] (IRQs *10 11)
[    0.289485] ACPI: PCI Interrupt Link [C0F0] (IRQs *10 11)
[    0.289943] ACPI: PCI Interrupt Link [C0F1] (IRQs 10 *11)
[    0.290394] ACPI: PCI Interrupt Link [C0F2] (IRQs *10 11)
[    0.290594] ACPI Exception: AE_NOT_FOUND, Evaluating _PRS (20100428/pci_link-185)
[    0.290809] HEST: Table is not found!
[    0.290965] vgaarb: device added: PCI:0000:00:02.0,decodes=io+mem,owns=io+mem,locks=none
[    0.290989] vgaarb: loaded
[    0.291375] SCSI subsystem initialized
[    0.291470] libata version 3.00 loaded.
[    0.291593] usbcore: registered new interface driver usbfs
[    0.291625] usbcore: registered new interface driver hub
[    0.291684] usbcore: registered new device driver usb
[    0.292203] ACPI: WMI: Mapper loaded
[    0.292208] PCI: Using ACPI for IRQ routing
[    0.292214] PCI: pci_cache_line_size set to 64 bytes
[    0.292342] reserve RAM buffer: 0000000000002000 - 000000000000ffff 
[    0.292349] reserve RAM buffer: 000000000009fc00 - 000000000009ffff 
[    0.292356] reserve RAM buffer: 000000003f7d0000 - 000000003fffffff 
[    0.292582] NetLabel: Initializing
[    0.292587] NetLabel:  domain hash size = 128
[    0.292591] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.292620] NetLabel:  unlabeled traffic allowed by default
[    0.292957] hpet clockevent registered
[    0.292965] HPET: 3 timers in total, 0 timers will be used for per-cpu timer
[    0.292977] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[    0.292990] hpet0: 3 comparators, 64-bit 14.318180 MHz counter
[    0.296042] Switching to clocksource tsc
[    0.321063] AppArmor: AppArmor Filesystem Enabled
[    0.321100] pnp: PnP ACPI init
[    0.321142] ACPI: bus type pnp registered
[    0.347351] pnp: PnP ACPI: found 14 devices
[    0.347357] ACPI: ACPI bus type pnp unregistered
[    0.347366] PnPBIOS: Disabled by ACPI PNP
[    0.347394] system 00:00: [mem 0x00000000-0x0009ffff] could not be reserved
[    0.347404] system 00:00: [mem 0x000e0000-0x000fffff] could not be reserved
[    0.347412] system 00:00: [mem 0x00100000-0x3f7fffff] could not be reserved
[    0.347435] system 00:0b: [io  0x0500-0x057f] has been reserved
[    0.347444] system 00:0b: [mem 0xffb00000-0xffbfffff] has been reserved
[    0.347453] system 00:0b: [mem 0xfff00000-0xffffffff] has been reserved
[    0.347465] system 00:0c: [io  0x04d0-0x04d1] has been reserved
[    0.347473] system 00:0c: [io  0x1000-0x107f] has been reserved
[    0.347481] system 00:0c: [io  0x1100-0x113f] has been reserved
[    0.347488] system 00:0c: [io  0x1200-0x121f] has been reserved
[    0.347496] system 00:0c: [mem 0xe0000000-0xefffffff] has been reserved
[    0.347505] system 00:0c: [mem 0xfec00000-0xfec000ff] could not be reserved
[    0.347513] system 00:0c: [mem 0xfed20000-0xfed8ffff] has been reserved
[    0.347521] system 00:0c: [mem 0xfed90000-0xfed9afff] has been reserved
[    0.347534] system 00:0d: [mem 0xfeda0000-0xfedbffff] has been reserved
[    0.347542] system 00:0d: [mem 0xfec01000-0xfec01fff] has been reserved
[    0.385859] pci 0000:00:1e.0: BAR 15: assigned [mem 0x40000000-0x43ffffff pref]
[    0.385870] pci 0000:00:1c.0: BAR 15: assigned [mem 0x44000000-0x441fffff 64bit pref]
[    0.385878] pci 0000:00:1c.1: BAR 14: assigned [mem 0x44200000-0x443fffff]
[    0.385887] pci 0000:00:1c.1: BAR 15: assigned [mem 0x44400000-0x445fffff 64bit pref]
[    0.385896] pci 0000:00:1c.0: BAR 13: assigned [io  0x3000-0x3fff]
[    0.385904] pci 0000:00:1c.1: BAR 13: assigned [io  0x4000-0x4fff]
[    0.385912] pci 0000:00:1e.0: BAR 13: assigned [io  0x6000-0x6fff]
[    0.385920] pci 0000:00:1c.0: PCI bridge to [bus 10-10]
[    0.385928] pci 0000:00:1c.0:   bridge window [io  0x3000-0x3fff]
[    0.385940] pci 0000:00:1c.0:   bridge window [mem 0xd0000000-0xd03fffff]
[    0.385950] pci 0000:00:1c.0:   bridge window [mem 0x44000000-0x441fffff 64bit pref]
[    0.385963] pci 0000:00:1c.1: PCI bridge to [bus 20-20]
[    0.385971] pci 0000:00:1c.1:   bridge window [io  0x4000-0x4fff]
[    0.385983] pci 0000:00:1c.1:   bridge window [mem 0x44200000-0x443fffff]
[    0.385993] pci 0000:00:1c.1:   bridge window [mem 0x44400000-0x445fffff 64bit pref]
[    0.386009] pci 0000:02:06.0: BAR 15: assigned [mem 0x40000000-0x43ffffff pref]
[    0.386018] pci 0000:02:06.0: BAR 16: assigned [mem 0x48000000-0x4bffffff]
[    0.386026] pci 0000:02:06.0: BAR 13: assigned [io  0x6000-0x60ff]
[    0.386033] pci 0000:02:06.0: BAR 14: assigned [io  0x6400-0x64ff]
[    0.386040] pci 0000:02:06.0: CardBus bridge to [bus 03-06]
[    0.386046] pci 0000:02:06.0:   bridge window [io  0x6000-0x60ff]
[    0.386057] pci 0000:02:06.0:   bridge window [io  0x6400-0x64ff]
[    0.386068] pci 0000:02:06.0:   bridge window [mem 0x40000000-0x43ffffff pref]
[    0.386079] pci 0000:02:06.0:   bridge window [mem 0x48000000-0x4bffffff]
[    0.386090] pci 0000:00:1e.0: PCI bridge to [bus 02-03]
[    0.386097] pci 0000:00:1e.0:   bridge window [io  0x6000-0x6fff]
[    0.386109] pci 0000:00:1e.0:   bridge window [mem 0xd0400000-0xd07fffff]
[    0.386119] pci 0000:00:1e.0:   bridge window [mem 0x40000000-0x43ffffff pref]
[    0.386149]   alloc irq_desc for 16 on node -1
[    0.386154]   alloc kstat_irqs on node -1
[    0.386168] pci 0000:00:1c.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.386179] pci 0000:00:1c.0: setting latency timer to 64
[    0.386196] pci 0000:00:1c.1: enabling device (0000 -> 0003)
[    0.386204]   alloc irq_desc for 17 on node -1
[    0.386209]   alloc kstat_irqs on node -1
[    0.386218] pci 0000:00:1c.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    0.386229] pci 0000:00:1c.1: setting latency timer to 64
[    0.386244] pci 0000:00:1e.0: setting latency timer to 64
[    0.386265]   alloc irq_desc for 18 on node -1
[    0.386270]   alloc kstat_irqs on node -1
[    0.386279] pci 0000:02:06.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    0.386292] pci_bus 0000:00: resource 0 [io  0x0000-0xffff]
[    0.386299] pci_bus 0000:00: resource 1 [mem 0x00000000-0xffffffff]
[    0.386306] pci_bus 0000:10: resource 0 [io  0x3000-0x3fff]
[    0.386313] pci_bus 0000:10: resource 1 [mem 0xd0000000-0xd03fffff]
[    0.386320] pci_bus 0000:10: resource 2 [mem 0x44000000-0x441fffff 64bit pref]
[    0.386327] pci_bus 0000:20: resource 0 [io  0x4000-0x4fff]
[    0.386334] pci_bus 0000:20: resource 1 [mem 0x44200000-0x443fffff]
[    0.386341] pci_bus 0000:20: resource 2 [mem 0x44400000-0x445fffff 64bit pref]
[    0.386348] pci_bus 0000:02: resource 0 [io  0x6000-0x6fff]
[    0.386355] pci_bus 0000:02: resource 1 [mem 0xd0400000-0xd07fffff]
[    0.386362] pci_bus 0000:02: resource 2 [mem 0x40000000-0x43ffffff pref]
[    0.386369] pci_bus 0000:02: resource 4 [io  0x0000-0xffff]
[    0.386376] pci_bus 0000:02: resource 5 [mem 0x00000000-0xffffffff]
[    0.386383] pci_bus 0000:03: resource 0 [io  0x6000-0x60ff]
[    0.386389] pci_bus 0000:03: resource 1 [io  0x6400-0x64ff]
[    0.386396] pci_bus 0000:03: resource 2 [mem 0x40000000-0x43ffffff pref]
[    0.386403] pci_bus 0000:03: resource 3 [mem 0x48000000-0x4bffffff]
[    0.386479] NET: Registered protocol family 2
[    0.386628] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.387176] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.388756] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.389554] TCP: Hash tables configured (established 131072 bind 65536)
[    0.389560] TCP reno registered
[    0.389568] UDP hash table entries: 512 (order: 2, 16384 bytes)
[    0.389597] UDP-Lite hash table entries: 512 (order: 2, 16384 bytes)
[    0.389805] NET: Registered protocol family 1
[    0.389844] pci 0000:00:02.0: Boot video device
[    0.390000] PCI: CLS 64 bytes, default 64
[    0.390334] cpufreq-nforce2: No nForce2 chipset.
[    0.390402] Scanning for low memory corruption every 60 seconds
[    0.390756] audit: initializing netlink socket (disabled)
[    0.390779] type=2000 audit(1295185535.384:1): initialized
[    0.419512] Trying to unpack rootfs image as initramfs...
[    6.540175] highmem bounce pool size: 64 pages
[    6.540189] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    6.544045] VFS: Disk quotas dquot_6.5.2
[    6.544199] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    6.545743] fuse init (API version 7.14)
[    6.545964] msgmni has been set to 1708
[    6.546548] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    6.546556] io scheduler noop registered
[    6.546561] io scheduler deadline registered
[    6.546595] io scheduler cfq registered (default)
[    6.546840] pcieport 0000:00:1c.0: setting latency timer to 64
[    6.546902]   alloc irq_desc for 40 on node -1
[    6.546907]   alloc kstat_irqs on node -1
[    6.546926] pcieport 0000:00:1c.0: irq 40 for MSI/MSI-X
[    6.547108] pcieport 0000:00:1c.1: setting latency timer to 64
[    6.547164]   alloc irq_desc for 41 on node -1
[    6.547169]   alloc kstat_irqs on node -1
[    6.547183] pcieport 0000:00:1c.1: irq 41 for MSI/MSI-X
[    6.547402] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    6.547562] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    6.550134] ACPI: AC Adapter [C175] (off-line)
[    6.550336] input: Sleep Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0E:00/input/input0
[    6.550352] ACPI: Sleep Button [C1F0]
[    6.550471] input: Lid Switch as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0D:00/input/input1
[    6.550607] ACPI: Lid Switch [C1F1]
[    6.550730] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input2
[    6.550739] ACPI: Power Button [PWRF]
[    6.551240] ACPI: Fan [C253] (off)
[    6.551665] ACPI: Fan [C254] (off)
[    6.552165] ACPI: Fan [C255] (off)
[    6.552591] ACPI: Fan [C256] (off)
[    6.553212] ACPI: acpi_idle registered with cpuidle
[    6.554246] Marking TSC unstable due to TSC halts in idle
[    6.564065] Switching to clocksource hpet
[    6.609620] thermal LNXTHERM:01: registered as thermal_zone0
[    6.609648] ACPI: Thermal Zone [TZ1] (45 C)
[    6.640584] thermal LNXTHERM:02: registered as thermal_zone1
[    6.640612] ACPI: Thermal Zone [TZ2] (45 C)
[    6.653192] thermal LNXTHERM:03: registered as thermal_zone2
[    6.653220] ACPI: Thermal Zone [TZ3] (31 C)
[    6.656782] thermal LNXTHERM:04: registered as thermal_zone3
[    6.656809] ACPI: Thermal Zone [TZ4] (15 C)
[    6.657065] ERST: Table is not found!
[    6.657383] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    6.657558] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    6.657793] serial8250: ttyS2 at I/O 0x3e8 (irq = 4) is a 16550A
[    6.658264] 00:02: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    6.658865]   alloc irq_desc for 22 on node -1
[    6.658870]   alloc kstat_irqs on node -1
[    6.658885] serial 0000:00:1e.3: PCI INT B -> GSI 22 (level, low) -> IRQ 22
[    6.658898] serial 0000:00:1e.3: PCI INT B disabled
[    6.665850] brd: module loaded
[    6.667229] loop: module loaded
[    6.667715] ata_piix 0000:00:1f.1: version 2.13
[    6.667747] ata_piix 0000:00:1f.1: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    6.667824] ata_piix 0000:00:1f.1: setting latency timer to 64
[    6.671176] ACPI: Battery Slot [C176] (battery absent)
[    6.671217] isapnp: Scanning for PnP cards...
[    6.676809] scsi0 : ata_piix
[    6.679826] scsi1 : ata_piix
[    6.681632] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0x2580 irq 14
[    6.681641] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x2588 irq 15
[    6.683240] Fixed MDIO Bus: probed
[    6.683332] PPP generic driver version 2.4.2
[    6.683469] tun: Universal TUN/TAP device driver, 1.6
[    6.683474] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    6.683676] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    6.683719]   alloc irq_desc for 20 on node -1
[    6.683725]   alloc kstat_irqs on node -1
[    6.683739] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    6.683978] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    6.683986] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    6.684118] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 1
[    6.684172] ehci_hcd 0000:00:1d.7: debug port 1
[    6.688067] ehci_hcd 0000:00:1d.7: cache line size of 64 is not supported
[    6.692067] ata2: port disabled. ignoring.
[    6.738193] ehci_hcd 0000:00:1d.7: irq 20, io mem 0xd0980000
[    6.764064] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    6.764448] hub 1-0:1.0: USB hub found
[    6.764461] hub 1-0:1.0: 8 ports detected
[    6.764637] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    6.764682] uhci_hcd: USB Universal Host Controller Interface driver
[    6.764764] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    6.764782] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    6.764790] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    6.764881] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    6.764924] uhci_hcd 0000:00:1d.0: irq 20, io base 0x00002000
[    6.765234] hub 2-0:1.0: USB hub found
[    6.765245] hub 2-0:1.0: 2 ports detected
[    6.765368] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    6.765381] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    6.765389] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    6.765472] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3
[    6.765535] uhci_hcd 0000:00:1d.1: irq 17, io base 0x00002020
[    6.765812] hub 3-0:1.0: USB hub found
[    6.765822] hub 3-0:1.0: 2 ports detected
[    6.765941] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    6.765954] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    6.765962] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    6.766039] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4
[    6.766094] uhci_hcd 0000:00:1d.2: irq 18, io base 0x00002040
[    6.766376] hub 4-0:1.0: USB hub found
[    6.766386] hub 4-0:1.0: 2 ports detected
[    6.766692] PNP: PS/2 Controller [PNP0303:C1C5,PNP0f13:C1C6] at 0x60,0x64 irq 1,12
[    6.768399] i8042.c: Detected active multiplexing controller, rev 1.1.
[    6.772699] serio: i8042 KBD port at 0x60,0x64 irq 1
[    6.772716] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[    6.772849] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[    6.772909] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[    6.773007] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[    6.773305] mice: PS/2 mouse device common for all mice
[    6.773658] rtc_cmos 00:08: RTC can wake from S4
[    6.773757] rtc_cmos 00:08: rtc core: registered rtc_cmos as rtc0
[    6.774932] ACPI: Battery Slot [C177] (battery present)
[    6.774958] rtc0: alarms up to one month, y3k, 114 bytes nvram, hpet irqs
[    6.775261] device-mapper: uevent: version 1.0.3
[    6.780397] device-mapper: ioctl: 4.17.0-ioctl (2010-03-05) initialised: dm-devel@redhat.com
[    7.526925] device-mapper: multipath: version 1.1.1 loaded
[    7.526935] device-mapper: multipath round-robin: version 1.0.0 loaded
[    7.527347] EISA: Probing bus 0 at eisa.0
[    7.527361] Cannot allocate resource for EISA slot 1
[    7.527367] Cannot allocate resource for EISA slot 2
[    7.527374] Cannot allocate resource for EISA slot 3
[    7.527380] Cannot allocate resource for EISA slot 4
[    7.527386] Cannot allocate resource for EISA slot 5
[    7.527392] Cannot allocate resource for EISA slot 6
[    7.527409] EISA: Detected 0 cards.
[    7.527623] cpuidle: using governor ladder
[    7.527801] cpuidle: using governor menu
[    7.528515] TCP cubic registered
[    7.528870] NET: Registered protocol family 10
[    7.529690] lo: Disabled Privacy Extensions
[    7.530237] NET: Registered protocol family 17
[    7.536185] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3
[    7.540487] ata1.00: ATA-7: ST96023A, 3.07, max UDMA/100
[    7.540496] ata1.00: 117210240 sectors, multi 16: LBA 
[    7.540585] ata1.01: ATAPI: MATSHITADVD-RAM UJ-832S, 1.02, max MWDMA2
[    7.586622] Using IPI No-Shortcut mode
[    7.586695] PM: Resume from disk failed.
[    7.586708] registered taskstats version 1
[    7.586969]   Magic number: 11:783:786
[    7.587096] rtc_cmos 00:08: setting system clock to 2011-01-16 13:45:43 UTC (1295185543)
[    7.587100] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    7.587102] EDD information not available.
[    7.631283] ata1.00: configured for UDMA/100
[    7.719389] ata1.01: configured for MWDMA2
[    7.806498] usb 1-1: new high speed USB device using ehci_hcd and address 2
[    7.850126] isapnp: No Plug & Play device found
[    7.850277] scsi 0:0:0:0: Direct-Access     ATA      ST96023A         3.07 PQ: 0 ANSI: 5
[    7.850421] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    7.852263] scsi 0:0:1:0: CD-ROM            MATSHITA DVD-RAM UJ-832S  1.02 PQ: 0 ANSI: 5
[    7.852437] sd 0:0:0:0: [sda] 117210240 512-byte logical blocks: (60.0 GB/55.8 GiB)
[    7.856536] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[    7.856542] Uniform CD-ROM driver Revision: 3.20
[    7.856697] sr 0:0:1:0: Attached scsi CD-ROM sr0
[    7.856791] sr 0:0:1:0: Attached scsi generic sg1 type 5
[    7.856877] sd 0:0:0:0: [sda] Write Protect is off
[    7.856880] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    7.856907] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    7.857067]  sda:
[    7.864788] Freeing initrd memory: 11140k freed
[    8.097494]  sda1 sda2 sda3 sda4
[    8.108034] usb 1-3: new high speed USB device using ehci_hcd and address 3
[    8.114089] sd 0:0:0:0: [sda] Attached SCSI disk
[    8.114111] Freeing unused kernel memory: 684k freed
[    8.114619] Write protecting the kernel text: 4932k
[    8.114659] Write protecting the kernel read-only data: 1976k
[    8.134563] udev[75]: starting version 163
[    8.426253] sdhci: Secure Digital Host Controller Interface driver
[    8.426258] sdhci: Copyright(c) Pierre Ossman
[    8.438948] tg3.c:v3.110 (April 9, 2010)
[    8.438978] tg3 0000:10:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    8.438990] tg3 0000:10:00.0: setting latency timer to 64
[    8.459328] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/LNXVIDEO:00/input/input4
[    8.459393] ACPI: Video Device [C05A] (multi-head: yes  rom: no  post: no)
[    8.503733] Linux agpgart interface v0.103
[    8.532456] sdhci-pci 0000:02:06.4: SDHCI controller found [104c:8034] (rev 0)
[    8.532547] sdhci-pci 0000:02:06.4: PCI INT C -> GSI 22 (level, low) -> IRQ 22
[    8.535692] Registered led device: mmc0::
[    8.535790] mmc0: SDHCI controller on PCI [0000:02:06.4] using PIO
[    8.535874] Registered led device: mmc1::
[    8.535932] mmc1: SDHCI controller on PCI [0000:02:06.4] using PIO
[    8.536023] Registered led device: mmc2::
[    8.536083] mmc2: SDHCI controller on PCI [0000:02:06.4] using PIO
[    8.555820] agpgart-intel 0000:00:00.0: Intel 915GM Chipset
[    8.556646] agpgart-intel 0000:00:00.0: detected 7932K stolen memory
[    8.559922] Initializing USB Mass Storage driver...
[    8.573299] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xc0000000
[    8.608398] scsi4 : usb-storage 1-1:1.2
[    8.609558] tg3 0000:10:00.0: eth0: Tigon3 [partno(BCM95751M) rev 4101] (PCI Express) MAC address 00:15:60:b1:80:c5
[    8.609562] tg3 0000:10:00.0: eth0: attached PHY is 5750 (10/100/1000Base-T Ethernet) (WireSpeed[1])
[    8.609566] tg3 0000:10:00.0: eth0: RXcsums[1] LinkChgREG[0] MIirq[0] ASF[0] TSOcap[1]
[    8.609570] tg3 0000:10:00.0: eth0: dma_rwctrl[76180000] dma_mask[64-bit]
[    8.610527] scsi5 : usb-storage 1-1:1.3
[    8.611351] [drm] Initialized drm 1.1.0 20060810
[    8.618928] scsi6 : usb-storage 1-3:1.0
[    8.619070] usbcore: registered new interface driver usb-storage
[    8.619072] USB Mass Storage support registered.
[    8.666131] i915 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    8.666138] i915 0000:00:02.0: setting latency timer to 64
[    8.669827] [drm] set up 7M of stolen space
[    9.157714] vgaarb: device changed decodes: PCI:0000:00:02.0,olddecodes=io+mem,decodes=io+mem:owns=io+mem
[    9.158141] [drm] initialized overlay support
[    9.611520] scsi 4:0:0:0: CD-ROM            HUAWEI   Mass Storage     2.31 PQ: 0 ANSI: 2
[    9.613636] scsi 5:0:0:0: Direct-Access     HUAWEI   MMC Storage      2.31 PQ: 0 ANSI: 2
[    9.616760] scsi 6:0:0:0: Direct-Access     Kingston DataTraveler 2.0 PMAP PQ: 0 ANSI: 0 CCS
[    9.628176] Skipping EDID probe due to cached edid
[    9.648544] sr1: scsi-1 drive
[    9.648663] sr 4:0:0:0: Attached scsi CD-ROM sr1
[    9.648737] sr 4:0:0:0: Attached scsi generic sg2 type 5
[    9.649204] sd 5:0:0:0: Attached scsi generic sg3 type 0
[    9.650253] sd 6:0:0:0: Attached scsi generic sg4 type 0
[    9.660878] sd 6:0:0:0: [sdc] 8060928 512-byte logical blocks: (4.12 GB/3.84 GiB)
[    9.661370] sd 6:0:0:0: [sdc] Write Protect is off
[    9.661374] sd 6:0:0:0: [sdc] Mode Sense: 23 00 00 00
[    9.661377] sd 6:0:0:0: [sdc] Assuming drive cache: write through
[    9.664236] sd 6:0:0:0: [sdc] Assuming drive cache: write through
[    9.664243]  sdc: sdc1
[    9.667083] sd 5:0:0:0: [sdb] Attached SCSI removable disk
[    9.668236] sd 6:0:0:0: [sdc] Assuming drive cache: write through
[    9.668240] sd 6:0:0:0: [sdc] Attached SCSI removable disk
[   10.052247] Console: switching to colour frame buffer device 128x48
[   10.056049] fb0: inteldrmfb frame buffer device
[   10.056052] drm: registered panic notifier
[   10.056056] Slow work thread pool: Starting up
[   10.056098] Slow work thread pool: Ready
[   10.056108] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
[   10.560318] Skipping EDID probe due to cached edid
[   11.105834] Btrfs loaded
[   11.111008] xor: automatically using best checksumming function: pIII_sse
[   11.128009]    pIII_sse  :  4836.000 MB/sec
[   11.128012] xor: using function: pIII_sse (4836.000 MB/sec)
[   11.136063] device-mapper: dm-raid45: initialized v0.2594b
[   12.020346] EXT4-fs (sda4): INFO: recovery required on readonly filesystem
[   12.020352] EXT4-fs (sda4): write access will be enabled during recovery
[   12.049825] EXT4-fs (sda4): recovery complete
[   12.050311] EXT4-fs (sda4): mounted filesystem with ordered data mode. Opts: (null)
[   12.264710] aufs 2-standalone.tree-35-rcN-20100705
[   12.283185] squashfs: version 4.0 (2009/01/31) Phillip Lougher
[   28.223398] Adding 1951892k swap on /dev/sda3.  Priority:-1 extents:1 across:1951892k 
[   28.357041] udev[1527]: starting version 163
[   28.825691] intel_rng: FWH not detected
[   29.268127] usbcore: registered new interface driver usbserial
[   29.268172] USB Serial support registered for generic
[   29.269237] usbcore: registered new interface driver usbserial_generic
[   29.269241] usbserial: USB Serial Driver core
[   29.476320]   alloc irq_desc for 19 on node -1
[   29.476324]   alloc kstat_irqs on node -1
[   29.476334] tifm_7xx1 0000:02:06.3: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[   29.477959] yenta_cardbus 0000:02:06.0: CardBus bridge found [103c:0944]
[   29.477981] yenta_cardbus 0000:02:06.0: Enabling burst memory read transactions
[   29.477988] yenta_cardbus 0000:02:06.0: Using INTVAL to route CSC interrupts to PCI
[   29.477991] yenta_cardbus 0000:02:06.0: Routing CardBus interrupts to PCI
[   29.477998] yenta_cardbus 0000:02:06.0: TI: mfunc 0x01111b22, devctl 0x64
[   29.478794] USB Serial support registered for GSM modem (1-port)
[   29.479221] option 1-1:1.0: GSM modem (1-port) converter detected
[   29.479504] usb 1-1: GSM modem (1-port) converter now attached to ttyUSB0
[   29.479520] option 1-1:1.1: GSM modem (1-port) converter detected
[   29.479717] usb 1-1: GSM modem (1-port) converter now attached to ttyUSB1
[   29.480697] usbcore: registered new interface driver option
[   29.480700] option: v0.7.2:USB Driver for GSM modems
[   29.488845] input: HP WMI hotkeys as /devices/virtual/input/input5
[   29.559857] parport_pc 00:04: reported by Plug and Play ACPI
[   29.559932] parport0: PC-style at 0x378 (0x778), irq 7, dma 1 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
[   29.701495] Synaptics Touchpad, model: 1, fw: 6.2, id: 0x25a0b1, caps: 0xa04793/0x300000/0x0
[   29.701500] Synaptics: Clickpad mode enabled
[   29.701505] serio: Synaptics pass-through port at isa0060/serio4/input0
[   29.708713] yenta_cardbus 0000:02:06.0: ISA IRQ mask 0x0c78, PCI irq 18
[   29.708719] yenta_cardbus 0000:02:06.0: Socket status: 30000006
[   29.708725] pci_bus 0000:02: Raising subordinate bus# of parent bus (#02) from #03 to #06
[   29.708738] yenta_cardbus 0000:02:06.0: pcmcia: parent PCI bridge window: [io  0x6000-0x6fff]
[   29.708742] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x6000-0x6fff: excluding 0x6000-0x60ff 0x6400-0x64ff
[   29.713015] ppdev: user-space parallel port driver
[   29.734958] 
[   29.734966] yenta_cardbus 0000:02:06.0: pcmcia: parent PCI bridge window: [mem 0xd0400000-0xd07fffff]
[   29.734972] pcmcia_socket pcmcia_socket0: cs: memory probe 0xd0400000-0xd07fffff: excluding 0xd0400000-0xd043ffff
[   29.734988] yenta_cardbus 0000:02:06.0: pcmcia: parent PCI bridge window: [mem 0x40000000-0x43ffffff pref]
[   29.734992] pcmcia_socket pcmcia_socket0: cs: memory probe 0x40000000-0x43ffffff: excluding 0x40000000-0x43ffffff
[   29.744167] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio4/input/input6
[   29.765543] irda_init()
[   29.765565] NET: Registered protocol family 23
[   29.894581] found SMC SuperIO Chip (devid=0x7a rev=00 base=0x004e): LPC47N227
[   29.894605] smsc_superio_flat(): fir: 0x100, sir: 0x3e8, dma: 03, irq: 3, mode: 0x0e
[   29.894611] smsc_ircc_present: can't get sir_base of 0x3e8
[   30.084696] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x100-0x3af: excluding 0x170-0x177 0x1f0-0x1f7 0x370-0x37f
[   30.094393] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x3e0-0x4ff: excluding 0x3e8-0x3ff 0x4d0-0x4d7
[   30.095853] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x820-0x8ff: clean.
[   30.096677] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xc00-0xcf7: clean.
[   30.112853] pcmcia_socket pcmcia_socket0: cs: memory probe 0x0c0000-0x0fffff: excluding 0xc0000-0xc7fff 0xe0000-0xfffff
[   30.112977] pcmcia_socket pcmcia_socket0: cs: memory probe 0xa0000000-0xa0ffffff: clean.
[   30.113213] pcmcia_socket pcmcia_socket0: cs: memory probe 0x60000000-0x60ffffff: clean.
[   30.113283] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xa00-0xaff: clean.
[   30.538415] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   30.612172] Intel ICH 0000:00:1e.2: power state changed by ACPI to D0
[   30.612234] Intel ICH 0000:00:1e.2: power state changed by ACPI to D0
[   30.612246]   alloc irq_desc for 21 on node -1
[   30.612249]   alloc kstat_irqs on node -1
[   30.612257] Intel ICH 0000:00:1e.2: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[   30.612300] Intel ICH 0000:00:1e.2: setting latency timer to 64
[   31.552135] intel8x0_measure_ac97_clock: measured 55481 usecs (2673 samples)
[   31.552140] intel8x0: clocking to 48000
[   31.958502] lp0: using parport0 (interrupt-driven).
[   32.023370] Skipping EDID probe due to cached edid
[   32.452671] psmouse serio5: ID: 10 00 64
[   33.232355] Skipping EDID probe due to cached edid
[   35.193164] input: PS/2 Generic Mouse as /devices/platform/i8042/serio4/serio5/input/input7
[   40.224540] ip_tables: (C) 2000-2006 Netfilter Core Team
[   41.389916] Skipping EDID probe due to cached edid
[   42.276214] Skipping EDID probe due to cached edid
[   42.984189] Skipping EDID probe due to cached edid
[   43.692190] Skipping EDID probe due to cached edid
[   44.532254] Skipping EDID probe due to cached edid
[   49.952240] Skipping EDID probe due to cached edid
[   51.932237] Skipping EDID probe due to cached edid
[   85.933791] usb 1-1: USB disconnect, address 2
[   85.933870] option: option_instat_callback: error -108
[   85.934019] option1 ttyUSB0: GSM modem (1-port) converter now disconnected from ttyUSB0
[   85.934039] option 1-1:1.0: device disconnected
[   85.934108] option1 ttyUSB1: GSM modem (1-port) converter now disconnected from ttyUSB1
[   85.934123] option 1-1:1.1: device disconnected
[   97.096043] usb 1-1: new high speed USB device using ehci_hcd and address 4
[   97.248402] scsi7 : usb-storage 1-1:1.0
[   97.255658] usb 1-1: USB disconnect, address 4
[  103.800085] usb 1-1: new high speed USB device using ehci_hcd and address 5
[  103.954809] option 1-1:1.0: GSM modem (1-port) converter detected
[  103.954951] usb 1-1: GSM modem (1-port) converter now attached to ttyUSB0
[  103.962889] option 1-1:1.1: GSM modem (1-port) converter detected
[  103.963002] usb 1-1: GSM modem (1-port) converter now attached to ttyUSB1
[  103.988071] scsi10 : usb-storage 1-1:1.2
[  104.008993] scsi11 : usb-storage 1-1:1.3
[  105.000823] scsi 10:0:0:0: CD-ROM            HUAWEI   Mass Storage     2.31 PQ: 0 ANSI: 2
[  105.022292] sr1: scsi-1 drive
[  105.022477] sr 10:0:0:0: Attached scsi CD-ROM sr1
[  105.022577] sr 10:0:0:0: Attached scsi generic sg2 type 5
[  105.027445] scsi 11:0:0:0: Direct-Access     HUAWEI   MMC Storage      2.31 PQ: 0 ANSI: 2
[  105.029367] sd 11:0:0:0: Attached scsi generic sg3 type 0
[  105.050164] sd 11:0:0:0: [sdb] Attached SCSI removable disk
[  123.216844] EXT4-fs (sda4): mounted filesystem with ordered data mode. Opts: (null)

```

Modem plugged after login only (does not work):
```

[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.35-22-generic (buildd@rothera) (gcc version 4.4.5 (Ubuntu/Linaro 4.4.4-14ubuntu4) ) #33-Ubuntu SMP Sun Sep 19 20:34:50 UTC 2010 (Ubuntu 2.6.35-22.33-generic 2.6.35.4)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000003f7d0000 (usable)
[    0.000000]  BIOS-e820: 000000003f7d0000 - 000000003f7efc00 (reserved)
[    0.000000]  BIOS-e820: 000000003f7efc00 - 000000003f7fb000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000003f7fb000 - 000000003f800000 (reserved)
[    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec02000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed20000 - 00000000fed9b000 (reserved)
[    0.000000]  BIOS-e820: 00000000feda0000 - 00000000fedc0000 (reserved)
[    0.000000]  BIOS-e820: 00000000ffb00000 - 00000000ffc00000 (reserved)
[    0.000000]  BIOS-e820: 00000000fff00000 - 0000000100000000 (reserved)
[    0.000000] Notice: NX (Execute Disable) protection cannot be enabled: non-PAE kernel!
[    0.000000] DMI 2.3 present.
[    0.000000] e820 update range: 0000000000000000 - 0000000000001000 (usable) ==> (reserved)
[    0.000000] e820 remove range: 00000000000a0000 - 0000000000100000 (usable)
[    0.000000] last_pfn = 0x3f7d0 max_arch_pfn = 0x100000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-CFFFF write-protect
[    0.000000]   D0000-EFFFF uncachable
[    0.000000]   F0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000 mask FC0000000 write-back
[    0.000000]   1 base 03F800000 mask FFF800000 uncachable
[    0.000000]   2 base 0FEDA0000 mask FFFFE0000 uncachable
[    0.000000]   3 disabled
[    0.000000]   4 disabled
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] PAT not supported by CPU.
[    0.000000] e820 update range: 0000000000002000 - 0000000000010000 (usable) ==> (reserved)
[    0.000000] Scanning 1 areas for low memory corruption
[    0.000000] modified physical RAM map:
[    0.000000]  modified: 0000000000000000 - 0000000000001000 (reserved)
[    0.000000]  modified: 0000000000001000 - 0000000000002000 (usable)
[    0.000000]  modified: 0000000000002000 - 0000000000010000 (reserved)
[    0.000000]  modified: 0000000000010000 - 000000000009fc00 (usable)
[    0.000000]  modified: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  modified: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  modified: 0000000000100000 - 000000003f7d0000 (usable)
[    0.000000]  modified: 000000003f7d0000 - 000000003f7efc00 (reserved)
[    0.000000]  modified: 000000003f7efc00 - 000000003f7fb000 (ACPI NVS)
[    0.000000]  modified: 000000003f7fb000 - 000000003f800000 (reserved)
[    0.000000]  modified: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  modified: 00000000fec00000 - 00000000fec02000 (reserved)
[    0.000000]  modified: 00000000fed20000 - 00000000fed9b000 (reserved)
[    0.000000]  modified: 00000000feda0000 - 00000000fedc0000 (reserved)
[    0.000000]  modified: 00000000ffb00000 - 00000000ffc00000 (reserved)
[    0.000000]  modified: 00000000fff00000 - 0000000100000000 (reserved)
[    0.000000] initial memory mapped : 0 - 00c00000
[    0.000000] init_memory_mapping: 0000000000000000-00000000377fe000
[    0.000000]  0000000000 - 0000400000 page 4k
[    0.000000]  0000400000 - 0037400000 page 2M
[    0.000000]  0037400000 - 00377fe000 page 4k
[    0.000000] kernel direct mapping tables up to 377fe000 @ 15000-1a000
[    0.000000] RAMDISK: 3ecef000 - 3f7d0000
[    0.000000] Allocated new RAMDISK: 009a5000 - 0148516f
[    0.000000] Move RAMDISK from 000000003ecef000 - 000000003f7cf16e to 009a5000 - 0148516e
[    0.000000] ACPI: RSDP 000fe270 00014 (v00 HP    )
[    0.000000] ACPI: RSDT 3f7efc84 00038 (v01 HP     0944     21110520 HP   00000001)
[    0.000000] ACPI: FACP 3f7efc00 00084 (v02 HP     0944     00000002 HP   00000001)
[    0.000000] ACPI: DSDT 3f7efd54 08345 (v01 HP       nc6200 00010000 MSFT 0100000E)
[    0.000000] ACPI: FACS 3f7fae80 00040
[    0.000000] ACPI: APIC 3f7efcbc 0005A (v01 HP     0944     00000001 HP   00000001)
[    0.000000] ACPI: MCFG 3f7efd18 0003C (v01 HP     0944     00000001 HP   00000001)
[    0.000000] ACPI: SSDT 3f7f8099 00371 (v01 HP       HPQPpc 00001001 MSFT 0100000E)
[    0.000000] ACPI: SSDT 3f7f840a 00059 (v01 HP       HPQNLP 00000001 MSFT 0100000E)
[    0.000000] ACPI: Local APIC address 0xfec01000
[    0.000000] 127MB HIGHMEM available.
[    0.000000] 887MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 377fe000
[    0.000000]   low ram: 0 - 377fe000
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000001 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x000377fe
[    0.000000]   HighMem  0x000377fe -> 0x0003f7d0
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[3] active PFN ranges
[    0.000000]     0: 0x00000001 -> 0x00000002
[    0.000000]     0: 0x00000010 -> 0x0000009f
[    0.000000]     0: 0x00000100 -> 0x0003f7d0
[    0.000000] On node 0 totalpages: 259936
[    0.000000] free_area_init_node: node 0, pgdat c07ffd40, node_mem_map c1487020
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3952 pages, LIFO batch:0
[    0.000000]   Normal zone: 1744 pages used for memmap
[    0.000000]   Normal zone: 221486 pages, LIFO batch:31
[    0.000000]   HighMem zone: 256 pages used for memmap
[    0.000000]   HighMem zone: 32466 pages, LIFO batch:7
[    0.000000] Using APIC driver default
[    0.000000] ACPI: PM-Timer IO Port: 0x1008
[    0.000000] ACPI: Local APIC address 0xfec01000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 1, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] SMP: Allowing 1 CPUs, 0 hotplug CPUs
[    0.000000] nr_irqs_gsi: 40
[    0.000000] early_res array is doubled to 64 at [16000 - 167ff]
[    0.000000] PM: Registered nosave memory: 0000000000002000 - 0000000000010000
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
[    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 3f800000 (gap: 3f800000:a0800000)
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] setup_percpu: NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:1 nr_node_ids:1
[    0.000000] PERCPU: Embedded 14 pages/cpu @c2000000 s36416 r0 d20928 u4194304
[    0.000000] pcpu-alloc: s36416 r0 d20928 u4194304 alloc=1*4194304
[    0.000000] pcpu-alloc: [0] 0 
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 257904
[    0.000000] Kernel command line: file=/cdrom/preseed/edubuntu.seed boot=casper initrd=/casper/initrd.lz quiet splash -- console-setup/layoutcode=ch console-setup/variantcode=fr
[    0.000000] PID hash table entries: 4096 (order: 2, 16384 bytes)
[    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] allocated 5200940 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] Subtract (47 early reservations)
[    0.000000]   #1 [0000001000 - 0000002000]   EX TRAMPOLINE
[    0.000000]   #2 [0000100000 - 00009a0adc]   TEXT DATA BSS
[    0.000000]   #3 [000009fc00 - 0000100000]   BIOS reserved
[    0.000000]   #4 [00009a1000 - 00009a415c]             BRK
[    0.000000]   #5 [0000010000 - 0000011000]      TRAMPOLINE
[    0.000000]   #6 [0000011000 - 0000015000]     ACPI WAKEUP
[    0.000000]   #7 [0000015000 - 0000016000]         PGTABLE
[    0.000000]   #8 [00009a5000 - 0001486000]     NEW RAMDISK
[    0.000000]   #9 [0001486000 - 0001487000]         BOOTMEM
[    0.000000]   #10 [0001487000 - 0001c77000]         BOOTMEM
[    0.000000]   #11 [0001c77000 - 0001c77004]         BOOTMEM
[    0.000000]   #12 [0001c77040 - 0001c77100]         BOOTMEM
[    0.000000]   #13 [0001c77100 - 0001c77154]         BOOTMEM
[    0.000000]   #14 [0001c77180 - 0001c7a180]         BOOTMEM
[    0.000000]   #15 [0001c7a180 - 0001c7a18c]         BOOTMEM
[    0.000000]   #16 [0001c7a1c0 - 0001c7a7c0]         BOOTMEM
[    0.000000]   #17 [0001c7a7c0 - 0001c7a7e7]         BOOTMEM
[    0.000000]   #18 [0001c7a800 - 0001c7a9c0]         BOOTMEM
[    0.000000]   #19 [0001c7a9c0 - 0001c7aa00]         BOOTMEM
[    0.000000]   #20 [0001c7aa00 - 0001c7aa40]         BOOTMEM
[    0.000000]   #21 [0001c7aa40 - 0001c7aa80]         BOOTMEM
[    0.000000]   #22 [0001c7aa80 - 0001c7aac0]         BOOTMEM
[    0.000000]   #23 [0001c7aac0 - 0001c7ab00]         BOOTMEM
[    0.000000]   #24 [0001c7ab00 - 0001c7ab40]         BOOTMEM
[    0.000000]   #25 [0001c7ab40 - 0001c7ab80]         BOOTMEM
[    0.000000]   #26 [0001c7ab80 - 0001c7abc0]         BOOTMEM
[    0.000000]   #27 [0001c7abc0 - 0001c7ac00]         BOOTMEM
[    0.000000]   #28 [0001c7ac00 - 0001c7ac40]         BOOTMEM
[    0.000000]   #29 [0001c7ac40 - 0001c7ac80]         BOOTMEM
[    0.000000]   #30 [0001c7ac80 - 0001c7acc0]         BOOTMEM
[    0.000000]   #31 [0001c7acc0 - 0001c7ad00]         BOOTMEM
[    0.000000]   #32 [0001c7ad00 - 0001c7ad10]         BOOTMEM
[    0.000000]   #33 [0001c7ad40 - 0001c7ad50]         BOOTMEM
[    0.000000]   #34 [0001c7ad80 - 0001c7ae10]         BOOTMEM
[    0.000000]   #35 [0001c7ae40 - 0001c7aed0]         BOOTMEM
[    0.000000]   #36 [0002000000 - 000200e000]         BOOTMEM
[    0.000000]   #37 [0001c7cf00 - 0001c7cf04]         BOOTMEM
[    0.000000]   #38 [0001c7cf40 - 0001c7cf44]         BOOTMEM
[    0.000000]   #39 [0001c7cf80 - 0001c7cf84]         BOOTMEM
[    0.000000]   #40 [0001c7cfc0 - 0001c7cfc4]         BOOTMEM
[    0.000000]   #41 [0001c7d000 - 0001c7d0b0]         BOOTMEM
[    0.000000]   #42 [0001c7d0c0 - 0001c7d168]         BOOTMEM
[    0.000000]   #43 [0001c7d180 - 0001c81180]         BOOTMEM
[    0.000000]   #44 [0001c81180 - 0001d01180]         BOOTMEM
[    0.000000]   #45 [0001d01180 - 0001d41180]         BOOTMEM
[    0.000000]   #46 [000200e000 - 0002503c2c]         BOOTMEM
[    0.000000] Initializing HighMem for node 0 (000377fe:0003f7d0)
[    0.000000] Memory: 1005648k/1040192k available (4928k kernel code, 34096k reserved, 2336k data, 684k init, 130888k highmem)
[    0.000000] virtual kernel memory layout:
[    0.000000]     fixmap  : 0xfff16000 - 0xfffff000   ( 932 kB)
[    0.000000]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[    0.000000]     vmalloc : 0xf7ffe000 - 0xff7fe000   ( 120 MB)
[    0.000000]     lowmem  : 0xc0000000 - 0xf77fe000   ( 887 MB)
[    0.000000]       .init : 0xc0819000 - 0xc08c4000   ( 684 kB)
[    0.000000]       .data : 0xc05d029e - 0xc0818668   (2336 kB)
[    0.000000]       .text : 0xc0100000 - 0xc05d029e   (4928 kB)
[    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.000000] SLUB: Genslabs=13, HWalign=64, Order=0-3, MinObjects=0, CPUs=1, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000] 	RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000] 	RCU-based detection of stalled CPUs is disabled.
[    0.000000] 	Verbose stalled-CPUs detection is disabled.
[    0.000000] NR_IRQS:2304 nr_irqs:256
[    0.000000] Console: colour VGA+ 80x25
[    0.000000] console [tty0] enabled
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 798.179 MHz processor.
[    0.008007] Calibrating delay loop (skipped), value calculated using timer frequency.. 1596.35 BogoMIPS (lpj=3192716)
[    0.008020] pid_max: default: 32768 minimum: 301
[    0.008068] Security Framework initialized
[    0.008107] AppArmor: AppArmor initialized
[    0.008112] Yama: becoming mindful.
[    0.008244] Mount-cache hash table entries: 512
[    0.008510] Initializing cgroup subsys ns
[    0.008518] Initializing cgroup subsys cpuacct
[    0.008529] Initializing cgroup subsys memory
[    0.008552] Initializing cgroup subsys devices
[    0.008558] Initializing cgroup subsys freezer
[    0.008564] Initializing cgroup subsys net_cls
[    0.008629] mce: CPU supports 5 MCE banks
[    0.008647] CPU0: Thermal monitoring enabled (TM2)
[    0.008663] Performance Events: p6 PMU driver.
[    0.008681] ... version:                0
[    0.008686] ... bit width:              32
[    0.008691] ... generic registers:      2
[    0.008696] ... value mask:             00000000ffffffff
[    0.008702] ... max period:             000000007fffffff
[    0.008708] ... fixed-purpose events:   0
[    0.008713] ... event mask:             0000000000000003
[    0.010618] SMP alternatives: switching to UP code
[    0.028483] Freeing SMP alternatives: 24k freed
[    0.028502] ACPI: Core revision 20100428
[    0.048033] ftrace: converting mcount calls to 0f 1f 44 00 00
[    0.048049] ftrace: allocating 21758 entries in 43 pages
[    0.052092] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.052495] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.093130] CPU0: Intel(R) Pentium(R) M processor 1.86GHz stepping 08
[    0.096000] Brought up 1 CPUs
[    0.096000] Total of 1 processors activated (1596.35 BogoMIPS).
[    0.096000] devtmpfs: initialized
[    0.096000] HP Compaq Laptop series board detected. Selecting BIOS-method for reboots.
[    0.096000] regulator: core version 0.5
[    0.096000] Time: 13:34:28  Date: 01/16/11
[    0.096000] NET: Registered protocol family 16
[    0.096175] EISA bus registered
[    0.096195] ACPI: bus type pci registered
[    0.096345] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xe0000000-0xefffffff] (base 0xe0000000)
[    0.096354] PCI: MMCONFIG at [mem 0xe0000000-0xefffffff] reserved in E820
[    0.096359] PCI: Using MMCONFIG for extended config space
[    0.096365] PCI: Using configuration type 1 for base access
[    0.098772] bio: create slab <bio-0> at 0
[    0.102312] ACPI: EC: Look up EC in DSDT
[    0.152307] ACPI: Interpreter enabled
[    0.152319] ACPI: (supports S0 S3 S4 S5)
[    0.152367] ACPI: Using IOAPIC for interrupt routing
[    0.181025] ACPI: EC: GPE = 0x10, I/O: command/status = 0x66, data = 0x62
[    0.181215] ACPI: Power Resource [C1CF] (on)
[    0.181566] ACPI: Power Resource [C1A9] (on)
[    0.181918] ACPI: Power Resource [C1B1] (on)
[    0.182246] ACPI: Power Resource [C1B8] (on)
[    0.182341] ACPI: Power Resource [C1C8] (on)
[    0.182564] ACPI: Power Resource [C24F] (off)
[    0.182767] ACPI: Power Resource [C250] (off)
[    0.182971] ACPI: Power Resource [C251] (off)
[    0.183170] ACPI: Power Resource [C252] (off)
[    0.183796] ACPI: No dock devices found.
[    0.183807] PCI: Ignoring host bridge windows from ACPI; if necessary, use "pci=use_crs" and report a bug
[    0.195124] ACPI: PCI Root Bridge [C002] (domain 0000 [bus 00-ff])
[    0.217769] pci_root PNP0A08:00: host bridge window [io  0x0000-0x0cf7] (ignored)
[    0.217777] pci_root PNP0A08:00: host bridge window [io  0x0d00-0xffff] (ignored)
[    0.217785] pci_root PNP0A08:00: host bridge window [mem 0x000a0000-0x000bffff] (ignored)
[    0.217793] pci_root PNP0A08:00: host bridge window [mem 0x3f800000-0xfec00fff] (ignored)
[    0.217801] pci_root PNP0A08:00: host bridge window [mem 0xfec02000-0xffffffff] (ignored)
[    0.217808] pci_root PNP0A08:00: host bridge window [mem 0x000d0000-0x000dffff] (ignored)
[    0.217901] pci 0000:00:02.0: reg 10: [mem 0xd0800000-0xd087ffff]
[    0.217911] pci 0000:00:02.0: reg 14: [io  0x5000-0x5007]
[    0.217921] pci 0000:00:02.0: reg 18: [mem 0xc0000000-0xcfffffff pref]
[    0.217931] pci 0000:00:02.0: reg 1c: [mem 0xd0880000-0xd08bffff]
[    0.217982] pci 0000:00:02.1: reg 10: [mem 0xd0900000-0xd097ffff]
[    0.218171] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.218180] pci 0000:00:1c.0: PME# disabled
[    0.218300] pci 0000:00:1c.1: PME# supported from D0 D3hot D3cold
[    0.218309] pci 0000:00:1c.1: PME# disabled
[    0.218395] pci 0000:00:1d.0: reg 20: [io  0x2000-0x201f]
[    0.218474] pci 0000:00:1d.1: reg 20: [io  0x2020-0x203f]
[    0.218553] pci 0000:00:1d.2: reg 20: [io  0x2040-0x205f]
[    0.218630] pci 0000:00:1d.7: reg 10: [mem 0xd0980000-0xd09803ff]
[    0.218706] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
[    0.218715] pci 0000:00:1d.7: PME# disabled
[    0.218843] pci 0000:00:1e.2: reg 10: [io  0x2100-0x21ff]
[    0.218856] pci 0000:00:1e.2: reg 14: [io  0x2200-0x223f]
[    0.218869] pci 0000:00:1e.2: reg 18: [mem 0xd0981000-0xd09811ff]
[    0.218882] pci 0000:00:1e.2: reg 1c: [mem 0xd0982000-0xd09820ff]
[    0.218932] pci 0000:00:1e.2: PME# supported from D0 D3hot D3cold
[    0.218940] pci 0000:00:1e.2: PME# disabled
[    0.218985] pci 0000:00:1e.3: reg 10: [io  0x2400-0x24ff]
[    0.218998] pci 0000:00:1e.3: reg 14: [io  0x2500-0x257f]
[    0.219059] pci 0000:00:1e.3: PME# supported from D0 D3hot D3cold
[    0.219068] pci 0000:00:1e.3: PME# disabled
[    0.219178] pci 0000:00:1f.0: Force enabled HPET at 0xfed00000
[    0.219191] pci 0000:00:1f.0: quirk: [io  0x1000-0x107f] claimed by ICH6 ACPI/GPIO/TCO
[    0.219201] pci 0000:00:1f.0: quirk: [io  0x1100-0x113f] claimed by ICH6 GPIO
[    0.219210] pci 0000:00:1f.0: LPC Generic IO decode 1 PIO at 0500-057f
[    0.219255] pci 0000:00:1f.1: reg 10: [io  0x0000-0x0007]
[    0.219267] pci 0000:00:1f.1: reg 14: [io  0x0000-0x0003]
[    0.219280] pci 0000:00:1f.1: reg 18: [io  0x0000-0x0007]
[    0.219292] pci 0000:00:1f.1: reg 1c: [io  0x0000-0x0003]
[    0.219305] pci 0000:00:1f.1: reg 20: [io  0x2580-0x258f]
[    0.219475] pci 0000:10:00.0: reg 10: [mem 0xd0000000-0xd000ffff 64bit]
[    0.219585] pci 0000:10:00.0: PME# supported from D3hot D3cold
[    0.219596] pci 0000:10:00.0: PME# disabled
[    0.219624] pci 0000:10:00.0: disabling ASPM on pre-1.1 PCIe device.  You can enable it with 'pcie_aspm=force'
[    0.219646] pci 0000:00:1c.0: PCI bridge to [bus 10-10]
[    0.219656] pci 0000:00:1c.0:   bridge window [io  0xf000-0x0000] (disabled)
[    0.219667] pci 0000:00:1c.0:   bridge window [mem 0xd0000000-0xd03fffff]
[    0.219680] pci 0000:00:1c.0:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    0.219757] pci 0000:00:1c.1: PCI bridge to [bus 20-20]
[    0.219766] pci 0000:00:1c.1:   bridge window [io  0x0000-0x0000] (disabled)
[    0.219776] pci 0000:00:1c.1:   bridge window [mem 0x00000000-0x000fffff] (disabled)
[    0.219789] pci 0000:00:1c.1:   bridge window [mem 0x00000000-0x000fffff pref] (disabled)
[    0.219888] pci 0000:02:06.0: reg 10: [mem 0xd0400000-0xd0400fff]
[    0.219925] pci 0000:02:06.0: supports D1 D2
[    0.219931] pci 0000:02:06.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.219941] pci 0000:02:06.0: PME# disabled
[    0.220011] pci 0000:02:06.3: reg 10: [mem 0xd0402000-0xd0403fff]
[    0.220098] pci 0000:02:06.3: supports D1 D2
[    0.220104] pci 0000:02:06.3: PME# supported from D0 D1 D2 D3hot
[    0.220113] pci 0000:02:06.3: PME# disabled
[    0.220169] pci 0000:02:06.4: reg 10: [mem 0xd0404000-0xd04040ff]
[    0.220184] pci 0000:02:06.4: reg 14: [mem 0xd0405000-0xd04050ff]
[    0.220199] pci 0000:02:06.4: reg 18: [mem 0xd0406000-0xd04060ff]
[    0.220269] pci 0000:02:06.4: supports D1 D2
[    0.220275] pci 0000:02:06.4: PME# supported from D0 D1 D2 D3hot
[    0.220284] pci 0000:02:06.4: PME# disabled
[    0.220340] pci 0000:02:06.5: reg 10: [mem 0xd0407000-0xd0407fff]
[    0.220355] pci 0000:02:06.5: reg 14: [mem 0xd0408000-0xd0408fff]
[    0.220370] pci 0000:02:06.5: reg 18: [mem 0xd0409000-0xd0409fff]
[    0.220385] pci 0000:02:06.5: reg 1c: [mem 0xd040a000-0xd040afff]
[    0.220446] pci 0000:02:06.5: supports D1 D2
[    0.220452] pci 0000:02:06.5: PME# supported from D0 D1 D2 D3hot
[    0.220462] pci 0000:02:06.5: PME# disabled
[    0.220537] pci 0000:00:1e.0: PCI bridge to [bus 02-03] (subtractive decode)
[    0.220547] pci 0000:00:1e.0:   bridge window [io  0xf000-0x0000] (disabled)
[    0.220557] pci 0000:00:1e.0:   bridge window [mem 0xd0400000-0xd07fffff]
[    0.220570] pci 0000:00:1e.0:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    0.220578] pci 0000:00:1e.0:   bridge window [io  0x0000-0xffff] (subtractive decode)
[    0.220585] pci 0000:00:1e.0:   bridge window [mem 0x00000000-0xffffffff] (subtractive decode)
[    0.220657] pci_bus 0000:03: [bus 03-06] partially hidden behind transparent bridge 0000:02 [bus 02-03]
[    0.220688] pci_bus 0000:00: on NUMA node 0
[    0.220699] ACPI: PCI Interrupt Routing Table [\_SB_.C002._PRT]
[    0.221243] ACPI: PCI Interrupt Routing Table [\_SB_.C002.C06D._PRT]
[    0.221667] ACPI: PCI Interrupt Routing Table [\_SB_.C002.C006._PRT]
[    0.221895] ACPI: PCI Interrupt Routing Table [\_SB_.C002.C0DE._PRT]
[    0.287981] ACPI: PCI Interrupt Link [C0DA] (IRQs *10 11)
[    0.288450] ACPI: PCI Interrupt Link [C0DB] (IRQs 10 *11)
[    0.288899] ACPI: PCI Interrupt Link [C0DC] (IRQs 10 *11)
[    0.289350] ACPI: PCI Interrupt Link [C0DD] (IRQs *10 11)
[    0.289799] ACPI: PCI Interrupt Link [C0F0] (IRQs *10 11)
[    0.290257] ACPI: PCI Interrupt Link [C0F1] (IRQs 10 *11)
[    0.290706] ACPI: PCI Interrupt Link [C0F2] (IRQs *10 11)
[    0.290904] ACPI Exception: AE_NOT_FOUND, Evaluating _PRS (20100428/pci_link-185)
[    0.291119] HEST: Table is not found!
[    0.291275] vgaarb: device added: PCI:0000:00:02.0,decodes=io+mem,owns=io+mem,locks=none
[    0.291299] vgaarb: loaded
[    0.291685] SCSI subsystem initialized
[    0.291781] libata version 3.00 loaded.
[    0.291902] usbcore: registered new interface driver usbfs
[    0.291933] usbcore: registered new interface driver hub
[    0.291993] usbcore: registered new device driver usb
[    0.292513] ACPI: WMI: Mapper loaded
[    0.292518] PCI: Using ACPI for IRQ routing
[    0.292524] PCI: pci_cache_line_size set to 64 bytes
[    0.292652] reserve RAM buffer: 0000000000002000 - 000000000000ffff 
[    0.292659] reserve RAM buffer: 000000000009fc00 - 000000000009ffff 
[    0.292666] reserve RAM buffer: 000000003f7d0000 - 000000003fffffff 
[    0.292892] NetLabel: Initializing
[    0.292898] NetLabel:  domain hash size = 128
[    0.292902] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.292930] NetLabel:  unlabeled traffic allowed by default
[    0.293267] hpet clockevent registered
[    0.293275] HPET: 3 timers in total, 0 timers will be used for per-cpu timer
[    0.293288] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[    0.293300] hpet0: 3 comparators, 64-bit 14.318180 MHz counter
[    0.296041] Switching to clocksource tsc
[    0.321060] AppArmor: AppArmor Filesystem Enabled
[    0.321097] pnp: PnP ACPI init
[    0.321139] ACPI: bus type pnp registered
[    0.347325] pnp: PnP ACPI: found 14 devices
[    0.347332] ACPI: ACPI bus type pnp unregistered
[    0.347341] PnPBIOS: Disabled by ACPI PNP
[    0.347367] system 00:00: [mem 0x00000000-0x0009ffff] could not be reserved
[    0.347377] system 00:00: [mem 0x000e0000-0x000fffff] could not be reserved
[    0.347386] system 00:00: [mem 0x00100000-0x3f7fffff] could not be reserved
[    0.347409] system 00:0b: [io  0x0500-0x057f] has been reserved
[    0.347419] system 00:0b: [mem 0xffb00000-0xffbfffff] has been reserved
[    0.347427] system 00:0b: [mem 0xfff00000-0xffffffff] has been reserved
[    0.347440] system 00:0c: [io  0x04d0-0x04d1] has been reserved
[    0.347447] system 00:0c: [io  0x1000-0x107f] has been reserved
[    0.347455] system 00:0c: [io  0x1100-0x113f] has been reserved
[    0.347462] system 00:0c: [io  0x1200-0x121f] has been reserved
[    0.347470] system 00:0c: [mem 0xe0000000-0xefffffff] has been reserved
[    0.347479] system 00:0c: [mem 0xfec00000-0xfec000ff] could not be reserved
[    0.347487] system 00:0c: [mem 0xfed20000-0xfed8ffff] has been reserved
[    0.347495] system 00:0c: [mem 0xfed90000-0xfed9afff] has been reserved
[    0.347508] system 00:0d: [mem 0xfeda0000-0xfedbffff] has been reserved
[    0.347516] system 00:0d: [mem 0xfec01000-0xfec01fff] has been reserved
[    0.385829] pci 0000:00:1e.0: BAR 15: assigned [mem 0x40000000-0x43ffffff pref]
[    0.385840] pci 0000:00:1c.0: BAR 15: assigned [mem 0x44000000-0x441fffff 64bit pref]
[    0.385848] pci 0000:00:1c.1: BAR 14: assigned [mem 0x44200000-0x443fffff]
[    0.385857] pci 0000:00:1c.1: BAR 15: assigned [mem 0x44400000-0x445fffff 64bit pref]
[    0.385866] pci 0000:00:1c.0: BAR 13: assigned [io  0x3000-0x3fff]
[    0.385874] pci 0000:00:1c.1: BAR 13: assigned [io  0x4000-0x4fff]
[    0.385882] pci 0000:00:1e.0: BAR 13: assigned [io  0x6000-0x6fff]
[    0.385890] pci 0000:00:1c.0: PCI bridge to [bus 10-10]
[    0.385898] pci 0000:00:1c.0:   bridge window [io  0x3000-0x3fff]
[    0.385909] pci 0000:00:1c.0:   bridge window [mem 0xd0000000-0xd03fffff]
[    0.385920] pci 0000:00:1c.0:   bridge window [mem 0x44000000-0x441fffff 64bit pref]
[    0.385933] pci 0000:00:1c.1: PCI bridge to [bus 20-20]
[    0.385941] pci 0000:00:1c.1:   bridge window [io  0x4000-0x4fff]
[    0.385952] pci 0000:00:1c.1:   bridge window [mem 0x44200000-0x443fffff]
[    0.385963] pci 0000:00:1c.1:   bridge window [mem 0x44400000-0x445fffff 64bit pref]
[    0.385980] pci 0000:02:06.0: BAR 15: assigned [mem 0x40000000-0x43ffffff pref]
[    0.385989] pci 0000:02:06.0: BAR 16: assigned [mem 0x48000000-0x4bffffff]
[    0.385996] pci 0000:02:06.0: BAR 13: assigned [io  0x6000-0x60ff]
[    0.386003] pci 0000:02:06.0: BAR 14: assigned [io  0x6400-0x64ff]
[    0.386010] pci 0000:02:06.0: CardBus bridge to [bus 03-06]
[    0.386016] pci 0000:02:06.0:   bridge window [io  0x6000-0x60ff]
[    0.386027] pci 0000:02:06.0:   bridge window [io  0x6400-0x64ff]
[    0.386038] pci 0000:02:06.0:   bridge window [mem 0x40000000-0x43ffffff pref]
[    0.386049] pci 0000:02:06.0:   bridge window [mem 0x48000000-0x4bffffff]
[    0.386060] pci 0000:00:1e.0: PCI bridge to [bus 02-03]
[    0.386067] pci 0000:00:1e.0:   bridge window [io  0x6000-0x6fff]
[    0.386079] pci 0000:00:1e.0:   bridge window [mem 0xd0400000-0xd07fffff]
[    0.386089] pci 0000:00:1e.0:   bridge window [mem 0x40000000-0x43ffffff pref]
[    0.386117]   alloc irq_desc for 16 on node -1
[    0.386123]   alloc kstat_irqs on node -1
[    0.386136] pci 0000:00:1c.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.386147] pci 0000:00:1c.0: setting latency timer to 64
[    0.386164] pci 0000:00:1c.1: enabling device (0000 -> 0003)
[    0.386172]   alloc irq_desc for 17 on node -1
[    0.386177]   alloc kstat_irqs on node -1
[    0.386186] pci 0000:00:1c.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    0.386197] pci 0000:00:1c.1: setting latency timer to 64
[    0.386211] pci 0000:00:1e.0: setting latency timer to 64
[    0.386232]   alloc irq_desc for 18 on node -1
[    0.386237]   alloc kstat_irqs on node -1
[    0.386246] pci 0000:02:06.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    0.386259] pci_bus 0000:00: resource 0 [io  0x0000-0xffff]
[    0.386265] pci_bus 0000:00: resource 1 [mem 0x00000000-0xffffffff]
[    0.386273] pci_bus 0000:10: resource 0 [io  0x3000-0x3fff]
[    0.386279] pci_bus 0000:10: resource 1 [mem 0xd0000000-0xd03fffff]
[    0.386287] pci_bus 0000:10: resource 2 [mem 0x44000000-0x441fffff 64bit pref]
[    0.386294] pci_bus 0000:20: resource 0 [io  0x4000-0x4fff]
[    0.386301] pci_bus 0000:20: resource 1 [mem 0x44200000-0x443fffff]
[    0.386308] pci_bus 0000:20: resource 2 [mem 0x44400000-0x445fffff 64bit pref]
[    0.386315] pci_bus 0000:02: resource 0 [io  0x6000-0x6fff]
[    0.386322] pci_bus 0000:02: resource 1 [mem 0xd0400000-0xd07fffff]
[    0.386329] pci_bus 0000:02: resource 2 [mem 0x40000000-0x43ffffff pref]
[    0.386336] pci_bus 0000:02: resource 4 [io  0x0000-0xffff]
[    0.386342] pci_bus 0000:02: resource 5 [mem 0x00000000-0xffffffff]
[    0.386349] pci_bus 0000:03: resource 0 [io  0x6000-0x60ff]
[    0.386356] pci_bus 0000:03: resource 1 [io  0x6400-0x64ff]
[    0.386363] pci_bus 0000:03: resource 2 [mem 0x40000000-0x43ffffff pref]
[    0.386370] pci_bus 0000:03: resource 3 [mem 0x48000000-0x4bffffff]
[    0.386446] NET: Registered protocol family 2
[    0.386596] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.387147] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.388730] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.389527] TCP: Hash tables configured (established 131072 bind 65536)
[    0.389534] TCP reno registered
[    0.389542] UDP hash table entries: 512 (order: 2, 16384 bytes)
[    0.389573] UDP-Lite hash table entries: 512 (order: 2, 16384 bytes)
[    0.389776] NET: Registered protocol family 1
[    0.389813] pci 0000:00:02.0: Boot video device
[    0.389973] PCI: CLS 64 bytes, default 64
[    0.390308] cpufreq-nforce2: No nForce2 chipset.
[    0.390378] Scanning for low memory corruption every 60 seconds
[    0.390730] audit: initializing netlink socket (disabled)
[    0.390754] type=2000 audit(1295184867.384:1): initialized
[    0.419478] Trying to unpack rootfs image as initramfs...
[    6.539591] highmem bounce pool size: 64 pages
[    6.539605] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    6.543476] VFS: Disk quotas dquot_6.5.2
[    6.543630] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    6.545191] fuse init (API version 7.14)
[    6.545412] msgmni has been set to 1708
[    6.545998] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    6.546006] io scheduler noop registered
[    6.546011] io scheduler deadline registered
[    6.546045] io scheduler cfq registered (default)
[    6.546289] pcieport 0000:00:1c.0: setting latency timer to 64
[    6.546351]   alloc irq_desc for 40 on node -1
[    6.546356]   alloc kstat_irqs on node -1
[    6.546375] pcieport 0000:00:1c.0: irq 40 for MSI/MSI-X
[    6.546557] pcieport 0000:00:1c.1: setting latency timer to 64
[    6.546613]   alloc irq_desc for 41 on node -1
[    6.546618]   alloc kstat_irqs on node -1
[    6.546633] pcieport 0000:00:1c.1: irq 41 for MSI/MSI-X
[    6.546851] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    6.547013] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    6.549789] ACPI: AC Adapter [C175] (off-line)
[    6.549994] input: Sleep Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0E:00/input/input0
[    6.550007] ACPI: Sleep Button [C1F0]
[    6.550127] input: Lid Switch as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0D:00/input/input1
[    6.550264] ACPI: Lid Switch [C1F1]
[    6.550387] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input2
[    6.550396] ACPI: Power Button [PWRF]
[    6.550898] ACPI: Fan [C253] (off)
[    6.551323] ACPI: Fan [C254] (off)
[    6.551753] ACPI: Fan [C255] (off)
[    6.556335] ACPI: Fan [C256] (off)
[    6.556978] ACPI: acpi_idle registered with cpuidle
[    6.558043] Marking TSC unstable due to TSC halts in idle
[    6.568082] Switching to clocksource hpet
[    6.613620] thermal LNXTHERM:01: registered as thermal_zone0
[    6.613647] ACPI: Thermal Zone [TZ1] (44 C)
[    6.636731] thermal LNXTHERM:02: registered as thermal_zone1
[    6.636757] ACPI: Thermal Zone [TZ2] (43 C)
[    6.647848] thermal LNXTHERM:03: registered as thermal_zone2
[    6.647875] ACPI: Thermal Zone [TZ3] (29 C)
[    6.651430] thermal LNXTHERM:04: registered as thermal_zone3
[    6.651458] ACPI: Thermal Zone [TZ4] (15 C)
[    6.651712] ERST: Table is not found!
[    6.652082] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    6.652256] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    6.652491] serial8250: ttyS2 at I/O 0x3e8 (irq = 4) is a 16550A
[    6.652963] 00:02: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    6.653562]   alloc irq_desc for 22 on node -1
[    6.653568]   alloc kstat_irqs on node -1
[    6.653583] serial 0000:00:1e.3: PCI INT B -> GSI 22 (level, low) -> IRQ 22
[    6.653595] serial 0000:00:1e.3: PCI INT B disabled
[    6.660574] brd: module loaded
[    6.661960] loop: module loaded
[    6.662443] ata_piix 0000:00:1f.1: version 2.13
[    6.662476] ata_piix 0000:00:1f.1: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    6.662552] ata_piix 0000:00:1f.1: setting latency timer to 64
[    6.665836] ACPI: Battery Slot [C176] (battery absent)
[    6.665880] isapnp: Scanning for PnP cards...
[    6.671467] scsi0 : ata_piix
[    6.674418] scsi1 : ata_piix
[    6.676214] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0x2580 irq 14
[    6.676223] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x2588 irq 15
[    6.677827] Fixed MDIO Bus: probed
[    6.677917] PPP generic driver version 2.4.2
[    6.678050] tun: Universal TUN/TAP device driver, 1.6
[    6.678056] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    6.678245] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    6.678288]   alloc irq_desc for 20 on node -1
[    6.678294]   alloc kstat_irqs on node -1
[    6.678308] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    6.678339] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    6.678379] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    6.678637] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 1
[    6.678690] ehci_hcd 0000:00:1d.7: debug port 1
[    6.682586] ehci_hcd 0000:00:1d.7: cache line size of 64 is not supported
[    6.685624] ata2: port disabled. ignoring.
[    6.736082] ehci_hcd 0000:00:1d.7: irq 20, io mem 0xd0980000
[    6.748079] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    6.748461] hub 1-0:1.0: USB hub found
[    6.748474] hub 1-0:1.0: 8 ports detected
[    6.748708] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    6.748745] uhci_hcd: USB Universal Host Controller Interface driver
[    6.748828] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    6.748845] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    6.748853] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    6.748945] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    6.748987] uhci_hcd 0000:00:1d.0: irq 20, io base 0x00002000
[    6.749267] hub 2-0:1.0: USB hub found
[    6.749277] hub 2-0:1.0: 2 ports detected
[    6.749401] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    6.749413] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    6.749421] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    6.749498] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3
[    6.749559] uhci_hcd 0000:00:1d.1: irq 17, io base 0x00002020
[    6.749835] hub 3-0:1.0: USB hub found
[    6.749845] hub 3-0:1.0: 2 ports detected
[    6.749963] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    6.749976] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    6.749983] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    6.750067] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4
[    6.750122] uhci_hcd 0000:00:1d.2: irq 18, io base 0x00002040
[    6.750405] hub 4-0:1.0: USB hub found
[    6.750415] hub 4-0:1.0: 2 ports detected
[    6.750730] PNP: PS/2 Controller [PNP0303:C1C5,PNP0f13:C1C6] at 0x60,0x64 irq 1,12
[    6.752498] i8042.c: Detected active multiplexing controller, rev 1.1.
[    6.756693] serio: i8042 KBD port at 0x60,0x64 irq 1
[    6.756709] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[    6.756893] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[    6.756955] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[    6.757021] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[    6.757311] mice: PS/2 mouse device common for all mice
[    6.757666] rtc_cmos 00:08: RTC can wake from S4
[    6.757834] rtc_cmos 00:08: rtc core: registered rtc_cmos as rtc0
[    6.757900] rtc0: alarms up to one month, y3k, 114 bytes nvram, hpet irqs
[    6.758208] device-mapper: uevent: version 1.0.3
[    6.761999] device-mapper: ioctl: 4.17.0-ioctl (2010-03-05) initialised: dm-devel@redhat.com
[    6.765928] ACPI: Battery Slot [C177] (battery present)
[    6.769837] device-mapper: multipath: version 1.1.1 loaded
[    6.769847] device-mapper: multipath round-robin: version 1.0.0 loaded
[    6.770239] EISA: Probing bus 0 at eisa.0
[    6.770253] Cannot allocate resource for EISA slot 1
[    6.770259] Cannot allocate resource for EISA slot 2
[    6.770266] Cannot allocate resource for EISA slot 3
[    6.770272] Cannot allocate resource for EISA slot 4
[    6.770278] Cannot allocate resource for EISA slot 5
[    6.770285] Cannot allocate resource for EISA slot 6
[    6.770301] EISA: Detected 0 cards.
[    6.773514] cpuidle: using governor ladder
[    6.773701] cpuidle: using governor menu
[    6.774416] TCP cubic registered
[    6.774782] NET: Registered protocol family 10
[    6.775609] lo: Disabled Privacy Extensions
[    6.776206] NET: Registered protocol family 17
[    6.778963] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3
[    7.539569] Using IPI No-Shortcut mode
[    7.539666] PM: Resume from disk failed.
[    7.539682] registered taskstats version 1
[    7.540197]   Magic number: 11:577:584
[    7.540325] rtc_cmos 00:08: setting system clock to 2011-01-16 13:34:35 UTC (1295184875)
[    7.540329] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    7.540331] EDD information not available.
[    7.628515] ata1.00: ATA-7: ST96023A, 3.07, max UDMA/100
[    7.628519] ata1.00: 117210240 sectors, multi 16: LBA 
[    7.628557] ata1.01: ATAPI: MATSHITADVD-RAM UJ-832S, 1.02, max MWDMA2
[    7.716332] ata1.00: configured for UDMA/100
[    7.804304] ata1.01: configured for MWDMA2
[    7.847983] isapnp: No Plug & Play device found
[    7.848024] usb 1-3: new high speed USB device using ehci_hcd and address 2
[    7.848180] scsi 0:0:0:0: Direct-Access     ATA      ST96023A         3.07 PQ: 0 ANSI: 5
[    7.848346] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    7.850206] scsi 0:0:1:0: CD-ROM            MATSHITA DVD-RAM UJ-832S  1.02 PQ: 0 ANSI: 5
[    7.850386] sd 0:0:0:0: [sda] 117210240 512-byte logical blocks: (60.0 GB/55.8 GiB)
[    7.854599] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[    7.854605] Uniform CD-ROM driver Revision: 3.20
[    7.854761] sr 0:0:1:0: Attached scsi CD-ROM sr0
[    7.854853] sr 0:0:1:0: Attached scsi generic sg1 type 5
[    7.854942] sd 0:0:0:0: [sda] Write Protect is off
[    7.854946] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    7.854973] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    7.855132]  sda:
[    7.862807] Freeing initrd memory: 11140k freed
[    8.092157]  sda1 sda2 sda3 sda4
[    8.108750] sd 0:0:0:0: [sda] Attached SCSI disk
[    8.108771] Freeing unused kernel memory: 684k freed
[    8.109279] Write protecting the kernel text: 4932k
[    8.109319] Write protecting the kernel read-only data: 1976k
[    8.129446] udev[75]: starting version 163
[    8.443835] tg3.c:v3.110 (April 9, 2010)
[    8.443863] tg3 0000:10:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    8.443875] tg3 0000:10:00.0: setting latency timer to 64
[    8.453557] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/LNXVIDEO:00/input/input4
[    8.453611] ACPI: Video Device [C05A] (multi-head: yes  rom: no  post: no)
[    8.472451] Linux agpgart interface v0.103
[    8.480380] sdhci: Secure Digital Host Controller Interface driver
[    8.480383] sdhci: Copyright(c) Pierre Ossman
[    8.482519] sdhci-pci 0000:02:06.4: SDHCI controller found [104c:8034] (rev 0)
[    8.482541] sdhci-pci 0000:02:06.4: PCI INT C -> GSI 22 (level, low) -> IRQ 22
[    8.482651] Registered led device: mmc0::
[    8.482732] mmc0: SDHCI controller on PCI [0000:02:06.4] using PIO
[    8.482799] Registered led device: mmc1::
[    8.482852] mmc1: SDHCI controller on PCI [0000:02:06.4] using PIO
[    8.482921] Registered led device: mmc2::
[    8.482974] mmc2: SDHCI controller on PCI [0000:02:06.4] using PIO
[    8.518232] agpgart-intel 0000:00:00.0: Intel 915GM Chipset
[    8.518884] agpgart-intel 0000:00:00.0: detected 7932K stolen memory
[    8.522201] Initializing USB Mass Storage driver...
[    8.522288] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xc0000000
[    8.536037] scsi2 : usb-storage 1-3:1.0
[    8.558584] usbcore: registered new interface driver usb-storage
[    8.558587] USB Mass Storage support registered.
[    8.580863] tg3 0000:10:00.0: eth0: Tigon3 [partno(BCM95751M) rev 4101] (PCI Express) MAC address 00:15:60:b1:80:c5
[    8.580868] tg3 0000:10:00.0: eth0: attached PHY is 5750 (10/100/1000Base-T Ethernet) (WireSpeed[1])
[    8.580873] tg3 0000:10:00.0: eth0: RXcsums[1] LinkChgREG[0] MIirq[0] ASF[0] TSOcap[1]
[    8.580876] tg3 0000:10:00.0: eth0: dma_rwctrl[76180000] dma_mask[64-bit]
[    8.582428] [drm] Initialized drm 1.1.0 20060810
[    8.641721] i915 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    8.641728] i915 0000:00:02.0: setting latency timer to 64
[    8.645636] [drm] set up 7M of stolen space
[    9.134717] vgaarb: device changed decodes: PCI:0000:00:02.0,olddecodes=io+mem,decodes=io+mem:owns=io+mem
[    9.135158] [drm] initialized overlay support
[    9.556929] scsi 2:0:0:0: Direct-Access     Kingston DataTraveler 2.0 PMAP PQ: 0 ANSI: 0 CCS
[    9.557827] sd 2:0:0:0: Attached scsi generic sg2 type 0
[    9.560774] sd 2:0:0:0: [sdb] 8060928 512-byte logical blocks: (4.12 GB/3.84 GiB)
[    9.561275] sd 2:0:0:0: [sdb] Write Protect is off
[    9.561278] sd 2:0:0:0: [sdb] Mode Sense: 23 00 00 00
[    9.561281] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[    9.563520] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[    9.563526]  sdb: sdb1
[    9.567392] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[    9.567396] sd 2:0:0:0: [sdb] Attached SCSI removable disk
[    9.600182] Skipping EDID probe due to cached edid
[   10.016018] Console: switching to colour frame buffer device 128x48
[   10.019744] fb0: inteldrmfb frame buffer device
[   10.019746] drm: registered panic notifier
[   10.019750] Slow work thread pool: Starting up
[   10.019801] Slow work thread pool: Ready
[   10.019810] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
[   10.492317] Skipping EDID probe due to cached edid
[   11.049705] Btrfs loaded
[   11.054877] xor: automatically using best checksumming function: pIII_sse
[   11.072009]    pIII_sse  :  4835.000 MB/sec
[   11.072012] xor: using function: pIII_sse (4835.000 MB/sec)
[   11.079914] device-mapper: dm-raid45: initialized v0.2594b
[   11.950451] EXT4-fs (sda4): mounted filesystem with ordered data mode. Opts: (null)
[   12.118038] aufs 2-standalone.tree-35-rcN-20100705
[   12.136387] squashfs: version 4.0 (2009/01/31) Phillip Lougher
[   28.700574] Adding 1951892k swap on /dev/sda3.  Priority:-1 extents:1 across:1951892k 
[   28.893657] udev[1503]: starting version 163
[   29.399207] intel_rng: FWH not detected
[   29.668549] input: HP WMI hotkeys as /devices/virtual/input/input5
[   29.931348]   alloc irq_desc for 19 on node -1
[   29.931353]   alloc kstat_irqs on node -1
[   29.931362] tifm_7xx1 0000:02:06.3: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[   29.931993] yenta_cardbus 0000:02:06.0: CardBus bridge found [103c:0944]
[   29.932077] yenta_cardbus 0000:02:06.0: Enabling burst memory read transactions
[   29.932084] yenta_cardbus 0000:02:06.0: Using INTVAL to route CSC interrupts to PCI
[   29.932087] yenta_cardbus 0000:02:06.0: Routing CardBus interrupts to PCI
[   29.932094] yenta_cardbus 0000:02:06.0: TI: mfunc 0x01111b22, devctl 0x64
[   30.044817] parport_pc 00:04: reported by Plug and Play ACPI
[   30.044896] parport0: PC-style at 0x378 (0x778), irq 7, dma 1 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
[   30.166277] yenta_cardbus 0000:02:06.0: ISA IRQ mask 0x0c78, PCI irq 18
[   30.166284] yenta_cardbus 0000:02:06.0: Socket status: 30000006
[   30.166289] pci_bus 0000:02: Raising subordinate bus# of parent bus (#02) from #03 to #06
[   30.166302] yenta_cardbus 0000:02:06.0: pcmcia: parent PCI bridge window: [io  0x6000-0x6fff]
[   30.166307] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x6000-0x6fff: excluding 0x6000-0x60ff 0x6400-0x64ff
[   30.241565] yenta_cardbus 0000:02:06.0: pcmcia: parent PCI bridge window: [mem 0xd0400000-0xd07fffff]
[   30.241571] pcmcia_socket pcmcia_socket0: cs: memory probe 0xd0400000-0xd07fffff: excluding 0xd0400000-0xd043ffff
[   30.241588] yenta_cardbus 0000:02:06.0: pcmcia: parent PCI bridge window: [mem 0x40000000-0x43ffffff pref]
[   30.241592] pcmcia_socket pcmcia_socket0: cs: memory probe 0x40000000-0x43ffffff: excluding 0x40000000-0x43ffffff
[   30.264991] Synaptics Touchpad, model: 1, fw: 6.2, id: 0x25a0b1, caps: 0xa04793/0x300000/0x0
[   30.264995] Synaptics: Clickpad mode enabled
[   30.265000] serio: Synaptics pass-through port at isa0060/serio4/input0
[   30.269466] irda_init()
[   30.269485] NET: Registered protocol family 23
[   30.270729] ppdev: user-space parallel port driver
[   30.306224] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio4/input/input6
[   30.395698] found SMC SuperIO Chip (devid=0x7a rev=00 base=0x004e): LPC47N227
[   30.395723] smsc_superio_flat(): fir: 0x100, sir: 0x3e8, dma: 03, irq: 3, mode: 0x0e
[   30.395729] smsc_ircc_present: can't get sir_base of 0x3e8
[   30.552766] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x100-0x3af: excluding 0x170-0x177 0x1f0-0x1f7 0x370-0x37f
[   30.555303] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x3e0-0x4ff: excluding 0x3e8-0x3ff 0x4d0-0x4d7
[   30.559156] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x820-0x8ff: clean.
[   30.559800] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xc00-0xcf7: clean.
[   30.560624] pcmcia_socket pcmcia_socket0: cs: memory probe 0x0c0000-0x0fffff: excluding 0xc0000-0xc7fff 0xe0000-0xfffff
[   30.560687] pcmcia_socket pcmcia_socket0: cs: memory probe 0xa0000000-0xa0ffffff: clean.
[   30.560750] pcmcia_socket pcmcia_socket0: cs: memory probe 0x60000000-0x60ffffff: clean.
[   30.560816] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xa00-0xaff: clean.
[   30.832727] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   30.994040] Intel ICH 0000:00:1e.2: power state changed by ACPI to D0
[   30.994103] Intel ICH 0000:00:1e.2: power state changed by ACPI to D0
[   30.994114]   alloc irq_desc for 21 on node -1
[   30.994117]   alloc kstat_irqs on node -1
[   30.994126] Intel ICH 0000:00:1e.2: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[   30.994168] Intel ICH 0000:00:1e.2: setting latency timer to 64
[   31.924064] intel8x0_measure_ac97_clock: measured 55391 usecs (2669 samples)
[   31.924068] intel8x0: clocking to 48000
[   32.284867] lp0: using parport0 (interrupt-driven).
[   32.436986] Skipping EDID probe due to cached edid
[   33.010647] psmouse serio5: ID: 10 00 64
[   33.676273] Skipping EDID probe due to cached edid
[   35.747694] input: PS/2 Generic Mouse as /devices/platform/i8042/serio4/serio5/input/input7
[   40.403661] ip_tables: (C) 2000-2006 Netfilter Core Team
[   41.525050] Skipping EDID probe due to cached edid
[   42.420251] Skipping EDID probe due to cached edid
[   43.128334] Skipping EDID probe due to cached edid
[   43.836324] Skipping EDID probe due to cached edid
[   44.668254] Skipping EDID probe due to cached edid
[   49.886924] Skipping EDID probe due to cached edid
[   52.884217] Skipping EDID probe due to cached edid
[   68.172040] usb 1-1: new high speed USB device using ehci_hcd and address 3
[   68.324232] scsi3 : usb-storage 1-1:1.0
[   68.329407] usb 1-1: USB disconnect, address 3
[   69.459048] EXT4-fs (sda4): mounted filesystem with ordered data mode. Opts: (null)
[   74.816176] usb 1-1: new high speed USB device using ehci_hcd and address 4
[   74.971686] scsi6 : usb-storage 1-1:1.2
[   74.981182] scsi7 : usb-storage 1-1:1.3
[   75.983496] scsi 6:0:0:0: CD-ROM            HUAWEI   Mass Storage     2.31 PQ: 0 ANSI: 2
[   75.987117] scsi 7:0:0:0: Direct-Access     HUAWEI   MMC Storage      2.31 PQ: 0 ANSI: 2
[   76.005086] sr1: scsi-1 drive
[   76.005229] sr 6:0:0:0: Attached scsi CD-ROM sr1
[   76.005318] sr 6:0:0:0: Attached scsi generic sg3 type 5
[   76.009252] sd 7:0:0:0: Attached scsi generic sg4 type 0
[   76.024217] sd 7:0:0:0: [sdc] Attached SCSI removable disk

```

---

### Post by vmalep on 2011-01-22
Hu? Ho idea, really?

---

### Post by mahela007 on 2011-02-05
hi... Many many people have the same problem and frankly, I'm pretty frustrated with whoever is responsible for fixing these issues on ubuntu.. Anyway, you could try Wvdial. I haven't used it personally but I have seen people mentioning it from time to time.. I have the same problem with the modem. Please PM me if you find a solution (or post in this thread) thanks.

EDIT [http://abhilekh.wordpress.com/2010/09/14/huawei-e156g-usb-modem-installation-on-ubuntu-10-04/](http://abhilekh.wordpress.com/2010/09/14/huawei-e156g-usb-modem-installation-on-ubuntu-10-04/)

---

### Post by drleekl on 2011-07-27
My Huawei E156G works on Ubuntu 11.04 with Wvdial

Find and install Wvdial from Ubuntu Software Centre.

---

### Post by mahela007 on 2011-07-28
Thanks.. I'll try that. I have to update my verison of Ubuntu first though.

---

