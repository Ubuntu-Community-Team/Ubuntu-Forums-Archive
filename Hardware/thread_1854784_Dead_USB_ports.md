---
title: "Dead USB ports"
date: 2011-10-05
forum: Hardware
---

### Post by scarface87 on 2011-10-05
Hey.
My USB ports are all dead, they are not sending power or register.

I have been searching for 2 days now so i hope someone can help.

**lsusb** says: *_even with a usb mouse pluged in_*
```
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```

**dmesg** says:
```
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.35-30-generic (buildd@dubnium) (gcc version 4.4.5 (Ubuntu/Linaro 4.4.4-14ubuntu5) ) #56moonos1-Ubuntu SMP Tue Aug 9 20:02:27 UTC 2011 (Ubuntu 2.6.35-30.56moonos1-generic 2.6.35.13)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009dc00 (usable)
[    0.000000]  BIOS-e820: 000000000009dc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000d0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000006fe90000 (usable)
[    0.000000]  BIOS-e820: 000000006fe90000 - 000000006fe9d000 (ACPI data)
[    0.000000]  BIOS-e820: 000000006fe9d000 - 000000006ff00000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000006ff00000 - 0000000080000000 (reserved)
[    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fff80000 - 0000000100000000 (reserved)
[    0.000000] Notice: NX (Execute Disable) protection cannot be enabled in hardware: non-PAE kernel!
[    0.000000] NX (Execute Disable) protection: approximated by x86 segment limits
[    0.000000] DMI present.
[    0.000000] e820 update range: 0000000000000000 - 0000000000001000 (usable) ==> (reserved)
[    0.000000] e820 remove range: 00000000000a0000 - 0000000000100000 (usable)
[    0.000000] last_pfn = 0x6fe90 max_arch_pfn = 0x100000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-CFFFF write-protect
[    0.000000]   D0000-E3FFF uncachable
[    0.000000]   E4000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 0000000000 mask FF80000000 write-back
[    0.000000]   1 base 0070000000 mask FFF0000000 uncachable
[    0.000000]   2 disabled
[    0.000000]   3 disabled
[    0.000000]   4 disabled
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] e820 update range: 0000000000002000 - 0000000000010000 (usable) ==> (reserved)
[    0.000000] Scanning 1 areas for low memory corruption
[    0.000000] modified physical RAM map:
[    0.000000]  modified: 0000000000000000 - 0000000000001000 (reserved)
[    0.000000]  modified: 0000000000001000 - 0000000000002000 (usable)
[    0.000000]  modified: 0000000000002000 - 0000000000010000 (reserved)
[    0.000000]  modified: 0000000000010000 - 000000000009dc00 (usable)
[    0.000000]  modified: 000000000009dc00 - 00000000000a0000 (reserved)
[    0.000000]  modified: 00000000000d0000 - 0000000000100000 (reserved)
[    0.000000]  modified: 0000000000100000 - 000000006fe90000 (usable)
[    0.000000]  modified: 000000006fe90000 - 000000006fe9d000 (ACPI data)
[    0.000000]  modified: 000000006fe9d000 - 000000006ff00000 (ACPI NVS)
[    0.000000]  modified: 000000006ff00000 - 0000000080000000 (reserved)
[    0.000000]  modified: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  modified: 00000000fec00000 - 00000000fec10000 (reserved)
[    0.000000]  modified: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  modified: 00000000fff80000 - 0000000100000000 (reserved)
[    0.000000] initial memory mapped : 0 - 00c00000
[    0.000000] found SMP MP-table at [c00f8a70] f8a70
[    0.000000] init_memory_mapping: 0000000000000000-00000000377fe000
[    0.000000]  0000000000 - 0000400000 page 4k
[    0.000000]  0000400000 - 0037400000 page 2M
[    0.000000]  0037400000 - 00377fe000 page 4k
[    0.000000] kernel direct mapping tables up to 377fe000 @ 15000-1a000
[    0.000000] RAMDISK: 375a2000 - 37ff0000
[    0.000000] Allocated new RAMDISK: 009ab000 - 013f8176
[    0.000000] Move RAMDISK from 00000000375a2000 - 0000000037fef175 to 009ab000 - 013f8175
[    0.000000] ACPI: RSDP 000f8a40 00014 (v00 PTLTD )
[    0.000000] ACPI: RSDT 6fe96049 00038 (v01 ACRSYS ACRPRDCT 06040000  LTP 00000000)
[    0.000000] ACPI: FACP 6fe9cd52 00074 (v01 ATI    Bowfin   06040000 ATI  000F4240)
[    0.000000] ACPI: DSDT 6fe96081 06CD1 (v01    ATI    SB460 06040000 MSFT 02000002)
[    0.000000] ACPI: FACS 6fe9dfc0 00040
[    0.000000] ACPI: SSDT 6fe9cdc6 00182 (v01 PTLTD  POWERNOW 06040000  LTP 00000001)
[    0.000000] ACPI: APIC 6fe9cf48 00054 (v01 PTLTD  ? APIC   06040000  LTP 00000000)
[    0.000000] ACPI: MCFG 6fe9cf9c 0003C (v01 PTLTD    MCFG   06040000  LTP 00000000)
[    0.000000] ACPI: BOOT 6fe9cfd8 00028 (v01 PTLTD  $SBFTBL$ 06040000  LTP 00000001)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] 902MB HIGHMEM available.
[    0.000000] 887MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 377fe000
[    0.000000]   low ram: 0 - 377fe000
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000001 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x000377fe
[    0.000000]   HighMem  0x000377fe -> 0x0006fe90
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[3] active PFN ranges
[    0.000000]     0: 0x00000001 -> 0x00000002
[    0.000000]     0: 0x00000010 -> 0x0000009d
[    0.000000]     0: 0x00000100 -> 0x0006fe90
[    0.000000] On node 0 totalpages: 458270
[    0.000000] free_area_init_node: node 0, pgdat c0804000, node_mem_map c13fa020
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3950 pages, LIFO batch:0
[    0.000000]   Normal zone: 1744 pages used for memmap
[    0.000000]   Normal zone: 221486 pages, LIFO batch:31
[    0.000000]   HighMem zone: 1806 pages used for memmap
[    0.000000]   HighMem zone: 229252 pages, LIFO batch:31
[    0.000000] Using APIC driver default
[    0.000000] SB4X0 revision 0x83
[    0.000000] Ignoring ACPI timer override.
[    0.000000] If you got timer trouble try acpi_use_timer_override
[    0.000000] Detected use of extended apic ids on hypertransport bus
[    0.000000] ACPI: PM-Timer IO Port: 0x8008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 33, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] SMP: Allowing 2 CPUs, 0 hotplug CPUs
[    0.000000] nr_irqs_gsi: 40
[    0.000000] early_res array is doubled to 64 at [16000 - 167ff]
[    0.000000] PM: Registered nosave memory: 0000000000002000 - 0000000000010000
[    0.000000] PM: Registered nosave memory: 000000000009d000 - 000000000009e000
[    0.000000] PM: Registered nosave memory: 000000000009e000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000d0000
[    0.000000] PM: Registered nosave memory: 00000000000d0000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 80000000 (gap: 80000000:60000000)
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] setup_percpu: NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:2 nr_node_ids:1
[    0.000000] PERCPU: Embedded 14 pages/cpu @c2400000 s36416 r0 d20928 u2097152
[    0.000000] pcpu-alloc: s36416 r0 d20928 u2097152 alloc=1*4194304
[    0.000000] pcpu-alloc: [0] 0 1 
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 454688
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.35-30-generic root=UUID=ef0a9fd2-c295-4a64-8377-ad010238d69a ro quiet splash
[    0.000000] PID hash table entries: 4096 (order: 2, 16384 bytes)
[    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] allocated 9167660 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] Subtract (50 early reservations)
[    0.000000]   #1 [0000001000 - 0000002000]   EX TRAMPOLINE
[    0.000000]   #2 [0000100000 - 00009a6adc]   TEXT DATA BSS
[    0.000000]   #3 [00009a7000 - 00009aa170]             BRK
[    0.000000]   #4 [00000f8a80 - 0000100000]   BIOS reserved
[    0.000000]   #5 [00000f8a70 - 00000f8a80]    MP-table mpf
[    0.000000]   #6 [000009dc00 - 000009e171]   BIOS reserved
[    0.000000]   #7 [000009e29d - 00000f8a70]   BIOS reserved
[    0.000000]   #8 [000009e171 - 000009e29d]    MP-table mpc
[    0.000000]   #9 [0000010000 - 0000011000]      TRAMPOLINE
[    0.000000]   #10 [0000011000 - 0000015000]     ACPI WAKEUP
[    0.000000]   #11 [0000015000 - 0000016000]         PGTABLE
[    0.000000]   #12 [00009ab000 - 00013f9000]     NEW RAMDISK
[    0.000000]   #13 [00013f9000 - 00013fa000]         BOOTMEM
[    0.000000]   #14 [00013fa000 - 00021fa000]         BOOTMEM
[    0.000000]   #15 [00021fa000 - 00021fa004]         BOOTMEM
[    0.000000]   #16 [00021fa040 - 00021fa100]         BOOTMEM
[    0.000000]   #17 [00021fa100 - 00021fa154]         BOOTMEM
[    0.000000]   #18 [00021fa180 - 00021fd180]         BOOTMEM
[    0.000000]   #19 [00021fd180 - 00021fd1d8]         BOOTMEM
[    0.000000]   #20 [00021fd200 - 0002200200]         BOOTMEM
[    0.000000]   #21 [0002200200 - 0002200227]         BOOTMEM
[    0.000000]   #22 [0002200240 - 00022003c8]         BOOTMEM
[    0.000000]   #23 [0002200400 - 0002200440]         BOOTMEM
[    0.000000]   #24 [0002200440 - 0002200480]         BOOTMEM
[    0.000000]   #25 [0002200480 - 00022004c0]         BOOTMEM
[    0.000000]   #26 [00022004c0 - 0002200500]         BOOTMEM
[    0.000000]   #27 [0002200500 - 0002200540]         BOOTMEM
[    0.000000]   #28 [0002200540 - 0002200580]         BOOTMEM
[    0.000000]   #29 [0002200580 - 00022005c0]         BOOTMEM
[    0.000000]   #30 [00022005c0 - 0002200600]         BOOTMEM
[    0.000000]   #31 [0002200600 - 0002200640]         BOOTMEM
[    0.000000]   #32 [0002200640 - 0002200680]         BOOTMEM
[    0.000000]   #33 [0002200680 - 00022006c0]         BOOTMEM
[    0.000000]   #34 [00022006c0 - 00022006d0]         BOOTMEM
[    0.000000]   #35 [0002200700 - 0002200710]         BOOTMEM
[    0.000000]   #36 [0002200740 - 00022007aa]         BOOTMEM
[    0.000000]   #37 [00022007c0 - 000220082a]         BOOTMEM
[    0.000000]   #38 [0002400000 - 000240e000]         BOOTMEM
[    0.000000]   #39 [0002600000 - 000260e000]         BOOTMEM
[    0.000000]   #40 [0002202840 - 0002202844]         BOOTMEM
[    0.000000]   #41 [0002202880 - 0002202884]         BOOTMEM
[    0.000000]   #42 [00022028c0 - 00022028c8]         BOOTMEM
[    0.000000]   #43 [0002202900 - 0002202908]         BOOTMEM
[    0.000000]   #44 [0002202940 - 00022029e8]         BOOTMEM
[    0.000000]   #45 [0002202a00 - 0002202a68]         BOOTMEM
[    0.000000]   #46 [0002202a80 - 0002206a80]         BOOTMEM
[    0.000000]   #47 [0002206a80 - 0002286a80]         BOOTMEM
[    0.000000]   #48 [0002286a80 - 00022c6a80]         BOOTMEM
[    0.000000]   #49 [000260e000 - 0002ecc32c]         BOOTMEM
[    0.000000] Initializing HighMem for node 0 (000377fe:0006fe90)
[    0.000000] Memory: 1789400k/1833536k available (4944k kernel code, 43680k reserved, 2337k data, 688k init, 924232k highmem)
[    0.000000] virtual kernel memory layout:
[    0.000000]     fixmap  : 0xfff16000 - 0xfffff000   ( 932 kB)
[    0.000000]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[    0.000000]     vmalloc : 0xf7ffe000 - 0xff7fe000   ( 120 MB)
[    0.000000]     lowmem  : 0xc0000000 - 0xf77fe000   ( 887 MB)
[    0.000000]       .init : 0xc081d000 - 0xc08c9000   ( 688 kB)
[    0.000000]       .data : 0xc05d42ce - 0xc081c7e8   (2337 kB)
[    0.000000]       .text : 0xc0100000 - 0xc05d42ce   (4944 kB)
[    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.000000] SLUB: Genslabs=13, HWalign=64, Order=0-3, MinObjects=0, CPUs=2, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000] 	RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000] 	RCU-based detection of stalled CPUs is disabled.
[    0.000000] 	Verbose stalled-CPUs detection is disabled.
[    0.000000] NR_IRQS:2304 nr_irqs:512
[    0.000000] spurious 8259A interrupt: IRQ7.
[    0.000000] Console: colour VGA+ 80x25
[    0.000000] console [tty0] enabled
[    0.000000] Fast TSC calibration failed
[    0.000000] TSC: PIT calibration matches PMTIMER. 1 loops
[    0.000000] Detected 1599.972 MHz processor.
[    0.008005] Calibrating delay loop (skipped), value calculated using timer frequency.. 3199.94 BogoMIPS (lpj=6399888)
[    0.008014] pid_max: default: 32768 minimum: 301
[    0.008043] Security Framework initialized
[    0.008076] AppArmor: AppArmor initialized
[    0.008080] Yama: becoming mindful.
[    0.008166] Mount-cache hash table entries: 512
[    0.008349] Initializing cgroup subsys ns
[    0.008356] Initializing cgroup subsys cpuacct
[    0.008363] Initializing cgroup subsys memory
[    0.008376] Initializing cgroup subsys devices
[    0.008381] Initializing cgroup subsys freezer
[    0.008385] Initializing cgroup subsys net_cls
[    0.008418] CPU: Physical Processor ID: 0
[    0.008422] CPU: Processor Core ID: 0
[    0.008427] mce: CPU supports 5 MCE banks
[    0.008442] using C1E aware idle routine
[    0.008451] Performance Events: AMD PMU driver.
[    0.008463] ... version:                0
[    0.008466] ... bit width:              48
[    0.008470] ... generic registers:      4
[    0.008474] ... value mask:             0000ffffffffffff
[    0.008478] ... max period:             00007fffffffffff
[    0.008482] ... fixed-purpose events:   0
[    0.008485] ... event mask:             000000000000000f
[    0.014575] ACPI: Core revision 20100428
[    0.028014] ftrace: converting mcount calls to 0f 1f 44 00 00
[    0.028024] ftrace: allocating 21793 entries in 43 pages
[    0.032090] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.032462] ..TIMER: vector=0x30 apic1=0 pin1=0 apic2=-1 pin2=-1
[    0.074956] CPU0: AMD Turion(tm) 64 X2 Mobile Technology TL-50 stepping 02
[    0.076000] [Firmware Warn]: MTRR: CPU 0: SYSCFG[MtrrFixDramModEn] not cleared by BIOS, clearing this bit
[    0.076000] Booting Node   0, Processors  #1 Ok.
[    0.012000] Initializing CPU#1
[    0.012000] System has AMD C1E enabled
[    0.012000] Switch to broadcast mode on CPU1
[    0.160110] Brought up 2 CPUs
[    0.160114] Total of 2 processors activated (6400.10 BogoMIPS).
[    0.160504] Switch to broadcast mode on CPU0
[    0.160504] devtmpfs: initialized
[    0.161327] regulator: core version 0.5
[    0.161370] Time:  7:48:23  Date: 10/05/11
[    0.161429] NET: Registered protocol family 16
[    0.161469] Trying to unpack rootfs image as initramfs...
[    0.161626] EISA bus registered
[    0.161633] node 0 link 0: io port [1000, fffff]
[    0.161638] TOM: 0000000080000000 aka 2048M
[    0.161643] node 0 link 0: mmio [d0000000, dfffffff]
[    0.161647] node 0 link 0: mmio [c0000000, cfffffff]
[    0.161651] node 0 link 0: mmio [a0000, bffff]
[    0.161655] node 0 link 0: mmio [f0000000, ffffffff]
[    0.161660] node 0 link 0: mmio [e0000000, efffffff]
[    0.161664] node 0 link 0: mmio [80000000, bfffffff]
[    0.161668] bus: [00, ff] on node 0 link 0
[    0.161672] bus: 00 index 0 [io  0x0000-0xffff]
[    0.161676] bus: 00 index 1 [mem 0x80000000-0xefffffff]
[    0.161679] bus: 00 index 2 [mem 0x000a0000-0x000bffff]
[    0.161682] bus: 00 index 3 [mem 0xf0000000-0xffffffff]
[    0.161692] ACPI: bus type pci registered
[    0.161787] PCI: MMCONFIG for domain 0000 [bus 00-08] at [mem 0xe0000000-0xe08fffff] (base 0xe0000000)
[    0.161792] PCI: MMCONFIG at [mem 0xe0000000-0xe08fffff] reserved in E820
[    0.161795] PCI: Using MMCONFIG for extended config space
[    0.161797] PCI: Using configuration type 1 for base access
[    0.168161] bio: create slab <bio-0> at 0
[    0.169716] ACPI: EC: Look up EC in DSDT
[    0.196123] ACPI: Interpreter enabled
[    0.196128] ACPI: (supports S0 S3 S4 S5)
[    0.196153] ACPI: Using IOAPIC for interrupt routing
[    0.199621] ACPI: EC: GPE = 0x14, I/O: command/status = 0x66, data = 0x62
[    0.199621] ACPI: No dock devices found.
[    0.199621] PCI: Ignoring host bridge windows from ACPI; if necessary, use "pci=use_crs" and report a bug
[    0.199621] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
[    0.201154] pci_root PNP0A03:00: host bridge window [mem 0x000a0000-0x000bffff] (ignored)
[    0.201159] pci_root PNP0A03:00: host bridge window [mem 0x000d0000-0x000d1fff] (ignored)
[    0.201163] pci_root PNP0A03:00: host bridge window [mem 0x000d2000-0x000d3fff] (ignored)
[    0.201167] pci_root PNP0A03:00: host bridge window [mem 0x000d4000-0x000d5fff] (ignored)
[    0.201171] pci_root PNP0A03:00: host bridge window [mem 0x000d6000-0x000d7fff] (ignored)
[    0.201175] pci_root PNP0A03:00: host bridge window [mem 0x000d8000-0x000d9fff] (ignored)
[    0.201179] pci_root PNP0A03:00: host bridge window [mem 0x000da000-0x000dbfff] (ignored)
[    0.201183] pci_root PNP0A03:00: host bridge window [mem 0x000dc000-0x000ddfff] (ignored)
[    0.201187] pci_root PNP0A03:00: host bridge window [mem 0x000de000-0x000dffff] (ignored)
[    0.201191] pci_root PNP0A03:00: host bridge window [mem 0x000e0000-0x000e1fff] (ignored)
[    0.201195] pci_root PNP0A03:00: host bridge window [mem 0x000e2000-0x000e3fff] (ignored)
[    0.201199] pci_root PNP0A03:00: host bridge window [mem 0x80000000-0xffffffff] (ignored)
[    0.201203] pci_root PNP0A03:00: host bridge window [io  0x0000-0x0cf7] (ignored)
[    0.201207] pci_root PNP0A03:00: host bridge window [io  0x0d00-0xffff] (ignored)
[    0.201318] pci 0000:00:04.0: PME# supported from D0 D3hot D3cold
[    0.201322] pci 0000:00:04.0: PME# disabled
[    0.201365] pci 0000:00:05.0: PME# supported from D0 D3hot D3cold
[    0.201369] pci 0000:00:05.0: PME# disabled
[    0.201412] pci 0000:00:06.0: PME# supported from D0 D3hot D3cold
[    0.201416] pci 0000:00:06.0: PME# disabled
[    0.201459] pci 0000:00:07.0: PME# supported from D0 D3hot D3cold
[    0.201463] pci 0000:00:07.0: PME# disabled
[    0.201531] pci 0000:00:12.0: reg 10: [io  0x8440-0x8447]
[    0.201541] pci 0000:00:12.0: reg 14: [io  0x8434-0x8437]
[    0.201551] pci 0000:00:12.0: reg 18: [io  0x8438-0x843f]
[    0.201560] pci 0000:00:12.0: reg 1c: [io  0x8430-0x8433]
[    0.201570] pci 0000:00:12.0: reg 20: [io  0x8400-0x840f]
[    0.201580] pci 0000:00:12.0: reg 24: [mem 0xb0004000-0xb00041ff]
[    0.201591] pci 0000:00:12.0: reg 30: [mem 0x00000000-0x0007ffff pref]
[    0.201626] pci 0000:00:12.0: supports D1 D2
[    0.201671] pci 0000:00:13.0: reg 10: [mem 0xb0005000-0xb0005fff]
[    0.201777] pci 0000:00:13.1: reg 10: [mem 0xb0006000-0xb0006fff]
[    0.201889] pci 0000:00:13.2: reg 10: [mem 0xb0007000-0xb0007fff]
[    0.201962] pci 0000:00:13.2: supports D1 D2
[    0.201965] pci 0000:00:13.2: PME# supported from D0 D1 D2 D3hot
[    0.201971] pci 0000:00:13.2: PME# disabled
[    0.202023] pci 0000:00:14.0: reg 10: [io  0x8410-0x841f]
[    0.202033] pci 0000:00:14.0: reg 14: [mem 0xfed00000-0xfed003ff]
[    0.202071] HPET not enabled in BIOS. You might try hpet=force boot option
[    0.202134] pci 0000:00:14.1: reg 10: [io  0x01f0-0x01f7]
[    0.202143] pci 0000:00:14.1: reg 14: [io  0x03f4-0x03f7]
[    0.202153] pci 0000:00:14.1: reg 18: [io  0x0000-0x0007]
[    0.202163] pci 0000:00:14.1: reg 1c: [io  0x0000-0x0003]
[    0.202173] pci 0000:00:14.1: reg 20: [io  0x8420-0x842f]
[    0.202267] pci 0000:00:14.2: reg 10: [mem 0xb0000000-0xb0003fff 64bit]
[    0.202334] pci 0000:00:14.2: PME# supported from D0 D3hot D3cold
[    0.202340] pci 0000:00:14.2: PME# disabled
[    0.202578] PCI: peer root bus 00 res updated from pci conf
[    0.202614] pci 0000:01:05.0: reg 10: [mem 0xc0000000-0xcfffffff pref]
[    0.202619] pci 0000:01:05.0: reg 14: [io  0x9000-0x90ff]
[    0.202625] pci 0000:01:05.0: reg 18: [mem 0xb0100000-0xb010ffff]
[    0.202637] pci 0000:01:05.0: reg 30: [mem 0x00000000-0x0001ffff pref]
[    0.202649] pci 0000:01:05.0: supports D1 D2
[    0.202667] pci 0000:00:01.0: PCI bridge to [bus 01-01]
[    0.202673] pci 0000:00:01.0:   bridge window [io  0x9000-0x9fff]
[    0.202677] pci 0000:00:01.0:   bridge window [mem 0xb0100000-0xb01fffff]
[    0.202683] pci 0000:00:01.0:   bridge window [mem 0xc0000000-0xcfffffff 64bit pref]
[    0.202715] pci 0000:00:04.0: PCI bridge to [bus 02-02]
[    0.202720] pci 0000:00:04.0:   bridge window [io  0x0000-0x0000] (disabled)
[    0.202725] pci 0000:00:04.0:   bridge window [mem 0x00000000-0x000fffff] (disabled)
[    0.202731] pci 0000:00:04.0:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    0.202762] pci 0000:00:05.0: PCI bridge to [bus 03-03]
[    0.202768] pci 0000:00:05.0:   bridge window [io  0x0000-0x0000] (disabled)
[    0.202772] pci 0000:00:05.0:   bridge window [mem 0x00000000-0x000fffff] (disabled)
[    0.202778] pci 0000:00:05.0:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    0.202809] pci 0000:00:06.0: PCI bridge to [bus 06-06]
[    0.202814] pci 0000:00:06.0:   bridge window [io  0x0000-0x0000] (disabled)
[    0.202819] pci 0000:00:06.0:   bridge window [mem 0x00000000-0x000fffff] (disabled)
[    0.202825] pci 0000:00:06.0:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    0.202855] pci 0000:00:07.0: PCI bridge to [bus 07-07]
[    0.202861] pci 0000:00:07.0:   bridge window [io  0x0000-0x0000] (disabled)
[    0.202865] pci 0000:00:07.0:   bridge window [mem 0x00000000-0x000fffff] (disabled)
[    0.202871] pci 0000:00:07.0:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    0.202934] pci 0000:08:01.0: reg 10: [mem 0xb0210000-0xb0210fff]
[    0.202968] pci 0000:08:01.0: supports D1 D2
[    0.202971] pci 0000:08:01.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.202978] pci 0000:08:01.0: PME# disabled
[    0.203029] pci 0000:08:01.1: reg 10: [mem 0xb0211000-0xb021107f]
[    0.203113] pci 0000:08:01.1: supports D1 D2
[    0.203116] pci 0000:08:01.1: PME# supported from D0 D1 D2 D3hot
[    0.203123] pci 0000:08:01.1: PME# disabled
[    0.203175] pci 0000:08:01.2: reg 10: [mem 0xb0211400-0xb02114ff]
[    0.203259] pci 0000:08:01.2: supports D1 D2
[    0.203262] pci 0000:08:01.2: PME# supported from D0 D1 D2 D3hot
[    0.203269] pci 0000:08:01.2: PME# disabled
[    0.203320] pci 0000:08:01.3: reg 10: [mem 0xb0211800-0xb021187f]
[    0.203404] pci 0000:08:01.3: supports D1 D2
[    0.203407] pci 0000:08:01.3: PME# supported from D0 D1 D2 D3hot
[    0.203414] pci 0000:08:01.3: PME# disabled
[    0.203465] pci 0000:08:01.4: reg 10: [mem 0x00000000-0x000000ff]
[    0.203549] pci 0000:08:01.4: supports D1 D2
[    0.203552] pci 0000:08:01.4: PME# supported from D0 D1 D2 D3hot
[    0.203560] pci 0000:08:01.4: PME# disabled
[    0.203616] pci 0000:08:02.0: reg 10: [io  0xa000-0xa0ff]
[    0.203628] pci 0000:08:02.0: reg 14: [mem 0xb0211c00-0xb0211cff]
[    0.203701] pci 0000:08:02.0: supports D1 D2
[    0.203704] pci 0000:08:02.0: PME# supported from D1 D2 D3hot D3cold
[    0.203711] pci 0000:08:02.0: PME# disabled
[    0.203764] pci 0000:08:04.0: reg 10: [mem 0xb0200000-0xb020ffff]
[    0.203912] pci 0000:00:14.4: PCI bridge to [bus 08-09] (subtractive decode)
[    0.203922] pci 0000:00:14.4:   bridge window [io  0xa000-0xafff]
[    0.203929] pci 0000:00:14.4:   bridge window [mem 0xb0200000-0xb02fffff]
[    0.203936] pci 0000:00:14.4:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    0.203940] pci 0000:00:14.4:   bridge window [io  0x0000-0xffff] (subtractive decode)
[    0.203944] pci 0000:00:14.4:   bridge window [mem 0x80000000-0xefffffff] (subtractive decode)
[    0.203948] pci 0000:00:14.4:   bridge window [mem 0x000a0000-0x000bffff] (subtractive decode)
[    0.203952] pci 0000:00:14.4:   bridge window [mem 0xf0000000-0xffffffff] (subtractive decode)
[    0.204026] pci_bus 0000:09: [bus 09-0c] partially hidden behind transparent bridge 0000:08 [bus 08-09]
[    0.204050] pci_bus 0000:00: on NUMA node 0
[    0.204055] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.204185] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PB4_._PRT]
[    0.204266] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PB5_._PRT]
[    0.204347] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PB6_._PRT]
[    0.204427] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PB7_._PRT]
[    0.204530] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P2P_._PRT]
[    0.204636] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.AGP_._PRT]
[    0.209112] ACPI: PCI Interrupt Link [LNKA] (IRQs 10 11) *0, disabled.
[    0.209250] ACPI: PCI Interrupt Link [LNKB] (IRQs 10 11) *0, disabled.
[    0.209385] ACPI: PCI Interrupt Link [LNKC] (IRQs 10 11) *0, disabled.
[    0.209520] ACPI: PCI Interrupt Link [LNKD] (IRQs 10 11) *0, disabled.
[    0.209654] ACPI: PCI Interrupt Link [LNKE] (IRQs 10 11) *0, disabled.
[    0.209790] ACPI: PCI Interrupt Link [LNKF] (IRQs 10 11) *0, disabled.
[    0.209924] ACPI: PCI Interrupt Link [LNKG] (IRQs 10 11) *0, disabled.
[    0.210057] ACPI: PCI Interrupt Link [LNKH] (IRQs 10 11) *0, disabled.
[    0.210196] ACPI: PCI Interrupt Link [LNKU] (IRQs 3 4 5 7) *0, disabled.
[    0.210242] HEST: Table is not found!
[    0.210368] vgaarb: device added: PCI:0000:01:05.0,decodes=io+mem,owns=io+mem,locks=none
[    0.210376] vgaarb: loaded
[    0.210586] SCSI subsystem initialized
[    0.212000] libata version 3.00 loaded.
[    0.212000] usbcore: registered new interface driver usbfs
[    0.212000] usbcore: registered new interface driver hub
[    0.212000] usbcore: registered new device driver usb
[    0.212000] ACPI: WMI: Mapper loaded
[    0.212000] PCI: Using ACPI for IRQ routing
[    0.212000] PCI: pci_cache_line_size set to 64 bytes
[    0.212000] reserve RAM buffer: 0000000000002000 - 000000000000ffff 
[    0.212000] reserve RAM buffer: 000000000009dc00 - 000000000009ffff 
[    0.212000] reserve RAM buffer: 000000006fe90000 - 000000006fffffff 
[    0.212000] NetLabel: Initializing
[    0.212000] NetLabel:  domain hash size = 128
[    0.212000] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.212000] NetLabel:  unlabeled traffic allowed by default
[    0.224074] AppArmor: AppArmor Filesystem Enabled
[    0.224095] pnp: PnP ACPI init
[    0.224118] ACPI: bus type pnp registered
[    0.226999] pnp 00:09: disabling [mem 0x00000000-0x00000fff] because it overlaps 0000:00:12.0 BAR 6 [mem 0x00000000-0x0007ffff pref]
[    0.227018] pnp 00:09: disabling [mem 0x00000000-0x00000fff disabled] because it overlaps 0000:01:05.0 BAR 6 [mem 0x00000000-0x0001ffff pref]
[    0.227132] pnp: PnP ACPI: found 10 devices
[    0.227135] ACPI: ACPI bus type pnp unregistered
[    0.227139] PnPBIOS: Disabled by ACPI PNP
[    0.227154] system 00:01: [mem 0xe0000000-0xefffffff] has been reserved
[    0.227159] system 00:01: [mem 0xfec00000-0xfec00fff] could not be reserved
[    0.227163] system 00:01: [mem 0xfee00000-0xfee00fff] has been reserved
[    0.227172] system 00:08: [io  0x1080] has been reserved
[    0.227177] system 00:08: [io  0x0220-0x022f] has been reserved
[    0.227181] system 00:08: [io  0x040b] has been reserved
[    0.227184] system 00:08: [io  0x04d0-0x04d1] has been reserved
[    0.227188] system 00:08: [io  0x04d6] has been reserved
[    0.227192] system 00:08: [io  0x0530-0x0537] has been reserved
[    0.227196] system 00:08: [io  0x0c00-0x0c01] has been reserved
[    0.227200] system 00:08: [io  0x0c14] has been reserved
[    0.227204] system 00:08: [io  0x0c50-0x0c52] has been reserved
[    0.227207] system 00:08: [io  0x0c6c] has been reserved
[    0.227211] system 00:08: [io  0x0c6f] has been reserved
[    0.227215] system 00:08: [io  0x0cd4-0x0cd5] has been reserved
[    0.227219] system 00:08: [io  0x0cd6-0x0cd7] has been reserved
[    0.227223] system 00:08: [io  0x0cd8-0x0cdf] has been reserved
[    0.227227] system 00:08: [io  0x8000-0x805f] has been reserved
[    0.227231] system 00:08: [io  0x8100-0x81ff window] has been reserved
[    0.227235] system 00:08: [io  0x8200-0x82ff window] has been reserved
[    0.227239] system 00:08: [io  0x0f40-0x0f47] has been reserved
[    0.227243] system 00:08: [io  0x087f] has been reserved
[    0.227250] system 00:09: [mem 0x000e0000-0x000fffff] could not be reserved
[    0.227255] system 00:09: [mem 0xfff00000-0xffffffff] could not be reserved
[    0.263756] Switching to clocksource acpi_pm
[    0.264000] pci 0000:00:14.4: BAR 15: assigned [mem 0x80000000-0x83ffffff pref]
[    0.264000] pci 0000:00:12.0: BAR 6: assigned [mem 0x84000000-0x8407ffff pref]
[    0.264131] pci 0000:01:05.0: BAR 6: assigned [mem 0xb0120000-0xb013ffff pref]
[    0.264135] pci 0000:00:01.0: PCI bridge to [bus 01-01]
[    0.264139] pci 0000:00:01.0:   bridge window [io  0x9000-0x9fff]
[    0.264144] pci 0000:00:01.0:   bridge window [mem 0xb0100000-0xb01fffff]
[    0.264149] pci 0000:00:01.0:   bridge window [mem 0xc0000000-0xcfffffff 64bit pref]
[    0.264155] pci 0000:00:04.0: PCI bridge to [bus 02-02]
[    0.264158] pci 0000:00:04.0:   bridge window [io  disabled]
[    0.264162] pci 0000:00:04.0:   bridge window [mem disabled]
[    0.264165] pci 0000:00:04.0:   bridge window [mem pref disabled]
[    0.264170] pci 0000:00:05.0: PCI bridge to [bus 03-03]
[    0.264173] pci 0000:00:05.0:   bridge window [io  disabled]
[    0.264177] pci 0000:00:05.0:   bridge window [mem disabled]
[    0.264180] pci 0000:00:05.0:   bridge window [mem pref disabled]
[    0.264186] pci 0000:00:06.0: PCI bridge to [bus 06-06]
[    0.264188] pci 0000:00:06.0:   bridge window [io  disabled]
[    0.264192] pci 0000:00:06.0:   bridge window [mem disabled]
[    0.264196] pci 0000:00:06.0:   bridge window [mem pref disabled]
[    0.264201] pci 0000:00:07.0: PCI bridge to [bus 07-07]
[    0.264203] pci 0000:00:07.0:   bridge window [io  disabled]
[    0.264207] pci 0000:00:07.0:   bridge window [mem disabled]
[    0.264211] pci 0000:00:07.0:   bridge window [mem pref disabled]
[    0.264219] pci 0000:08:01.0: BAR 15: assigned [mem 0x80000000-0x83ffffff pref]
[    0.264223] pci 0000:08:01.0: BAR 16: assigned [mem 0x88000000-0x8bffffff]
[    0.264227] pci 0000:08:01.0: BAR 13: assigned [io  0xa400-0xa4ff]
[    0.264231] pci 0000:08:01.0: BAR 14: assigned [io  0xa800-0xa8ff]
[    0.264235] pci 0000:08:01.4: BAR 0: assigned [mem 0xb0211100-0xb02111ff]
[    0.264247] pci 0000:08:01.4: BAR 0: set to [mem 0xb0211100-0xb02111ff] (PCI address [0xb0211100-0xb02111ff]
[    0.264251] pci 0000:08:01.0: CardBus bridge to [bus 09-0c]
[    0.264255] pci 0000:08:01.0:   bridge window [io  0xa400-0xa4ff]
[    0.264262] pci 0000:08:01.0:   bridge window [io  0xa800-0xa8ff]
[    0.264270] pci 0000:08:01.0:   bridge window [mem 0x80000000-0x83ffffff pref]
[    0.264278] pci 0000:08:01.0:   bridge window [mem 0x88000000-0x8bffffff]
[    0.264285] pci 0000:00:14.4: PCI bridge to [bus 08-09]
[    0.264290] pci 0000:00:14.4:   bridge window [io  0xa000-0xafff]
[    0.264299] pci 0000:00:14.4:   bridge window [mem 0xb0200000-0xb02fffff]
[    0.264305] pci 0000:00:14.4:   bridge window [mem 0x80000000-0x83ffffff pref]
[    0.264327] pci 0000:00:04.0: setting latency timer to 64
[    0.264335] pci 0000:00:05.0: setting latency timer to 64
[    0.264343] pci 0000:00:06.0: setting latency timer to 64
[    0.264351] pci 0000:00:07.0: setting latency timer to 64
[    0.264374] pci 0000:08:01.0: enabling device (0004 -> 0007)
[    0.264383]   alloc irq_desc for 23 on node -1
[    0.264386]   alloc kstat_irqs on node -1
[    0.264395] pci 0000:08:01.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    0.264404] pci_bus 0000:00: resource 4 [io  0x0000-0xffff]
[    0.264408] pci_bus 0000:00: resource 5 [mem 0x80000000-0xefffffff]
[    0.264412] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
[    0.264415] pci_bus 0000:00: resource 7 [mem 0xf0000000-0xffffffff]
[    0.264419] pci_bus 0000:01: resource 0 [io  0x9000-0x9fff]
[    0.264423] pci_bus 0000:01: resource 1 [mem 0xb0100000-0xb01fffff]
[    0.264426] pci_bus 0000:01: resource 2 [mem 0xc0000000-0xcfffffff 64bit pref]
[    0.264431] pci_bus 0000:08: resource 0 [io  0xa000-0xafff]
[    0.264434] pci_bus 0000:08: resource 1 [mem 0xb0200000-0xb02fffff]
[    0.264438] pci_bus 0000:08: resource 2 [mem 0x80000000-0x83ffffff pref]
[    0.264441] pci_bus 0000:08: resource 4 [io  0x0000-0xffff]
[    0.264445] pci_bus 0000:08: resource 5 [mem 0x80000000-0xefffffff]
[    0.264449] pci_bus 0000:08: resource 6 [mem 0x000a0000-0x000bffff]
[    0.264452] pci_bus 0000:08: resource 7 [mem 0xf0000000-0xffffffff]
[    0.264456] pci_bus 0000:09: resource 0 [io  0xa400-0xa4ff]
[    0.264459] pci_bus 0000:09: resource 1 [io  0xa800-0xa8ff]
[    0.264463] pci_bus 0000:09: resource 2 [mem 0x80000000-0x83ffffff pref]
[    0.264466] pci_bus 0000:09: resource 3 [mem 0x88000000-0x8bffffff]
[    0.264519] NET: Registered protocol family 2
[    0.264608] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.264992] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.265729] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.266088] TCP: Hash tables configured (established 131072 bind 65536)
[    0.266092] TCP reno registered
[    0.266097] UDP hash table entries: 512 (order: 2, 16384 bytes)
[    0.266110] UDP-Lite hash table entries: 512 (order: 2, 16384 bytes)
[    0.266216] NET: Registered protocol family 1
[    0.266230] pci 0000:00:00.0: MSI quirk detected; MSI disabled
[    0.266238] pci 0000:00:01.0: MSI quirk detected; subordinate MSI disabled
[    0.266340] pci 0000:01:05.0: Boot video device
[    0.266372] PCI: CLS 32 bytes, default 64
[    0.266405] Simple Boot Flag at 0x36 set to 0x1
[    0.266664] cpufreq-nforce2: No nForce2 chipset.
[    0.266705] Scanning for low memory corruption every 60 seconds
[    0.266897] audit: initializing netlink socket (disabled)
[    0.266912] type=2000 audit(1317800902.264:1): initialized
[    0.281183] highmem bounce pool size: 64 pages
[    0.281190] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    0.283021] VFS: Disk quotas dquot_6.5.2
[    0.283097] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.283850] fuse init (API version 7.14)
[    0.283966] msgmni has been set to 1689
[    0.544870] Freeing initrd memory: 10552k freed
[    0.555448] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.555453] io scheduler noop registered
[    0.555456] io scheduler deadline registered
[    0.555475] io scheduler cfq registered (default)
[    0.555640] pcieport 0000:00:04.0: setting latency timer to 64
[    0.555706] pcieport 0000:00:05.0: setting latency timer to 64
[    0.555762] pcieport 0000:00:06.0: setting latency timer to 64
[    0.555818] pcieport 0000:00:07.0: setting latency timer to 64
[    0.555909] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.555944] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.559576] ACPI: AC Adapter [ACAD] (on-line)
[    0.559657] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0
[    0.559666] ACPI: Power Button [PWRB]
[    0.559733] input: Lid Switch as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0D:00/input/input1
[    0.561180] ACPI: Lid Switch [LID]
[    0.561239] input: Sleep Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0E:00/input/input2
[    0.561244] ACPI: Sleep Button [SLPB]
[    0.561298] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input3
[    0.561303] ACPI: Power Button [PWRF]
[    0.561492] ACPI: acpi_idle registered with cpuidle
[    0.561524] ACPI: processor limited to max C-state 1
[    0.566489] thermal LNXTHERM:01: registered as thermal_zone0
[    0.566499] ACPI: Thermal Zone [THRM] (54 C)
[    0.566585] ERST: Table is not found!
[    0.566630] ACPI: Battery Slot [BAT1] (battery absent)
[    0.566662] isapnp: Scanning for PnP cards...
[    0.566796] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    0.568575] brd: module loaded
[    0.569304] loop: module loaded
[    0.569635]   alloc irq_desc for 22 on node -1
[    0.569639]   alloc kstat_irqs on node -1
[    0.569650] pata_acpi 0000:00:12.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[    0.569723]   alloc irq_desc for 16 on node -1
[    0.569726]   alloc kstat_irqs on node -1
[    0.569732] pata_acpi 0000:00:14.1: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.569754] pata_acpi 0000:00:14.1: setting latency timer to 64
[    0.570200] Fixed MDIO Bus: probed
[    0.570247] PPP generic driver version 2.4.2
[    0.570304] tun: Universal TUN/TAP device driver, 1.6
[    0.570307] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.570412] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.570435]   alloc irq_desc for 19 on node -1
[    0.570438]   alloc kstat_irqs on node -1
[    0.570444] ehci_hcd 0000:00:13.2: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    0.570467] ehci_hcd 0000:00:13.2: EHCI Host Controller
[    0.570512] ehci_hcd 0000:00:13.2: new USB bus registered, assigned bus number 1
[    0.570588] ehci_hcd 0000:00:13.2: irq 19, io mem 0xb0007000
[    0.581038] ehci_hcd 0000:00:13.2: USB 2.0 started, EHCI 1.00
[    0.581184] hub 1-0:1.0: USB hub found
[    0.581190] hub 1-0:1.0: 8 ports detected
[    0.581312] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.581330] ohci_hcd 0000:00:13.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    0.581347] ohci_hcd 0000:00:13.0: OHCI Host Controller
[    0.581391] ohci_hcd 0000:00:13.0: new USB bus registered, assigned bus number 2
[    0.581415] ohci_hcd 0000:00:13.0: irq 19, io mem 0xb0005000
[    0.637179] hub 2-0:1.0: USB hub found
[    0.637191] hub 2-0:1.0: 4 ports detected
[    0.637275] ohci_hcd 0000:00:13.1: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    0.637292] ohci_hcd 0000:00:13.1: OHCI Host Controller
[    0.637335] ohci_hcd 0000:00:13.1: new USB bus registered, assigned bus number 3
[    0.637358] ohci_hcd 0000:00:13.1: irq 19, io mem 0xb0006000
[    0.693181] hub 3-0:1.0: USB hub found
[    0.693192] hub 3-0:1.0: 4 ports detected
[    0.693291] uhci_hcd: USB Universal Host Controller Interface driver
[    0.693398] PNP: PS/2 Controller [PNP0303:KBC0,PNP0f13:MSE0] at 0x60,0x64 irq 1,12
[    0.696517] i8042.c: Detected active multiplexing controller, rev 1.1.
[    0.700104] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.700112] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[    0.700148] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[    0.700180] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[    0.700209] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[    0.700356] mice: PS/2 mouse device common for all mice
[    0.700577] rtc_cmos 00:04: RTC can wake from S4
[    0.700633] rtc_cmos 00:04: rtc core: registered rtc_cmos as rtc0
[    0.700667] rtc0: alarms up to one month, 114 bytes nvram
[    0.700806] device-mapper: uevent: version 1.0.3
[    0.700968] device-mapper: ioctl: 4.17.0-ioctl (2010-03-05) initialised: [email]dm-devel@redhat.com[/email]
[    0.701080] device-mapper: multipath: version 1.1.1 loaded
[    0.701083] device-mapper: multipath round-robin: version 1.0.0 loaded
[    0.701241] EISA: Probing bus 0 at eisa.0
[    0.701245] EISA: Cannot allocate resource for mainboard
[    0.701249] Cannot allocate resource for EISA slot 1
[    0.701252] Cannot allocate resource for EISA slot 2
[    0.701255] Cannot allocate resource for EISA slot 3
[    0.701258] Cannot allocate resource for EISA slot 4
[    0.701262] Cannot allocate resource for EISA slot 5
[    0.701265] Cannot allocate resource for EISA slot 6
[    0.701268] Cannot allocate resource for EISA slot 7
[    0.701271] Cannot allocate resource for EISA slot 8
[    0.701274] EISA: Detected 0 cards.
[    0.701372] cpuidle: using governor ladder
[    0.701375] cpuidle: using governor menu
[    0.701759] TCP cubic registered
[    0.701919] NET: Registered protocol family 10
[    0.702369] lo: Disabled Privacy Extensions
[    0.702668] NET: Registered protocol family 17
[    0.702711] powernow-k8: Found 1 AMD Turion(tm) 64 X2 Mobile Technology TL-50 (2 cpu cores) (version 2.20.00)
[    0.702759] powernow-k8:    0 : fid 0x8 (1600 MHz), vid 0x13
[    0.702762] powernow-k8:    1 : fid 0x0 (800 MHz), vid 0x1e
[    0.704182] Using IPI No-Shortcut mode
[    0.704315] PM: Resume from disk failed.
[    0.704331] registered taskstats version 1
[    0.704700]   Magic number: 15:925:823
[    0.704817] rtc_cmos 00:04: setting system clock to 2011-10-05 07:48:24 UTC (1317800904)
[    0.704821] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.704824] EDD information not available.
[    0.733044] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input4
[    0.923766] isapnp: No Plug & Play device found
[    0.923814] Freeing unused kernel memory: 688k freed
[    0.924382] Write protecting the kernel text: 4948k
[    0.924437] Write protecting the kernel read-only data: 1976k
[    0.951938] udev[74]: starting version 163
[    1.090788] scsi0 : pata_atiixp
[    1.109154] sdhci: Secure Digital Host Controller Interface driver
[    1.109159] sdhci: Copyright(c) Pierre Ossman
[    1.111147] sdhci-pci 0000:08:01.2: SDHCI controller found [1524:0550] (rev 1)
[    1.111175] sdhci-pci 0000:08:01.2: PCI INT B -> GSI 22 (level, low) -> IRQ 22
[    1.111276] Registered led device: mmc0::
[    1.115389] scsi1 : pata_atiixp
[    1.115621] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0x8420 irq 14
[    1.115626] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x8428 irq 15
[    1.115855] sata_sil 0000:00:12.0: version 2.4
[    1.146910] mmc0: SDHCI controller on PCI [0000:08:01.2] using PIO
[    1.146945] sdhci-pci 0000:08:01.4: SDHCI controller found [1524:0551] (rev 1)
[    1.146967] sdhci-pci 0000:08:01.4: enabling device (0000 -> 0002)
[    1.146979] sdhci-pci 0000:08:01.4: PCI INT B -> GSI 22 (level, low) -> IRQ 22
[    1.147083] Registered led device: mmc1::
[    1.147143] mmc1: SDHCI controller on PCI [0000:08:01.4] using PIO
[    1.147333] scsi2 : sata_sil
[    1.149756] scsi3 : sata_sil
[    1.150273] ata3: SATA max UDMA/100 mmio m512@0xb0004000 tf 0xb0004080 irq 22
[    1.150279] ata4: SATA max UDMA/100 mmio m512@0xb0004000 tf 0xb00040c0 irq 22
[    1.151900] 8139cp: 8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)
[    1.151939] 8139cp 0000:08:02.0: This (id 10ec:8139 rev 10) is not an 8139C+ compatible chip, use 8139too
[    1.284941] ata1.00: ATA-6: HTS541060G9AT00, MB3OA60A, max UDMA/100
[    1.284947] ata1.00: 117210240 sectors, multi 16: LBA48 
[    1.284990] ata1.01: ATAPI: MATSHITADVD-RAM UJ-850S, 1.20, max UDMA/33
[    1.300955] ata1.00: configured for UDMA/100
[    1.316715] ata1.01: configured for UDMA/33
[    1.317332] scsi 0:0:0:0: Direct-Access     ATA      HTS541060G9AT00  MB3O PQ: 0 ANSI: 5
[    1.317556] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.318717] sd 0:0:0:0: [sda] 117210240 512-byte logical blocks: (60.0 GB/55.8 GiB)
[    1.319512] scsi 0:0:1:0: CD-ROM            MATSHITA DVD-RAM UJ-850S  1.20 PQ: 0 ANSI: 5
[    1.324087] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[    1.324094] Uniform CD-ROM driver Revision: 3.20
[    1.324259] sr 0:0:1:0: Attached scsi CD-ROM sr0
[    1.324346] sr 0:0:1:0: Attached scsi generic sg1 type 5
[    1.324424] sd 0:0:0:0: [sda] Write Protect is off
[    1.324428] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.324471] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.324687]  sda: sda1 sda2 < sda5 >
[    1.364566] sd 0:0:0:0: [sda] Attached SCSI disk
[    1.468097] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
[    1.526094] ata3.00: NODEV after polling detection
[    1.844089] ata4: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
[    1.902078] ata4.00: NODEV after polling detection
[    1.906055] 8139too: 8139too Fast Ethernet driver 0.9.28
[    1.906117]   alloc irq_desc for 20 on node -1
[    1.906121]   alloc kstat_irqs on node -1
[    1.906131] 8139too 0000:08:02.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    1.910039] 8139too 0000:08:02.0: eth0: RealTek RTL8139 at 0xa000, 00:16:36:96:80:39, IRQ 20
[    2.281465] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)
[   18.122496] udev[332]: starting version 163
[   18.214453] Linux agpgart interface v0.103
[   18.216488] Adding 2437116k swap on /dev/sda5.  Priority:-1 extents:1 across:2437116k 
[   18.231207] piix4_smbus 0000:00:14.0: SMBus Host Controller at 0x8410, revision 0
[   18.231741] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   18.275377] k8temp 0000:00:18.3: Temperature readouts might be wrong - check erratum #141
[   18.301994] lp: driver loaded but no devices found
[   18.363799] yenta_cardbus 0000:08:01.0: CardBus bridge found [1025:010f]
[   18.363837] yenta_cardbus 0000:08:01.0: Using CSCINT to route CSC interrupts to PCI
[   18.363841] yenta_cardbus 0000:08:01.0: Routing CardBus interrupts to PCI
[   18.363850] yenta_cardbus 0000:08:01.0: TI: mfunc 0x00001202, devctl 0x44
[   18.591616] cfg80211: Calling CRDA to update world regulatory domain
[   18.612893] yenta_cardbus 0000:08:01.0: ISA IRQ mask 0x0cf8, PCI irq 23
[   18.612900] yenta_cardbus 0000:08:01.0: Socket status: 30000006
[   18.612907] pci_bus 0000:08: Raising subordinate bus# of parent bus (#08) from #09 to #0c
[   18.612923] yenta_cardbus 0000:08:01.0: pcmcia: parent PCI bridge window: [io  0xa000-0xafff]
[   18.612929] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xa000-0xafff: excluding 0xa000-0xa0ff 0xa400-0xa4ff 0xa800-0xa8ff
[   18.621123] yenta_cardbus 0000:08:01.0: pcmcia: parent PCI bridge window: [mem 0xb0200000-0xb02fffff]
[   18.621128] pcmcia_socket pcmcia_socket0: cs: memory probe 0xb0200000-0xb02fffff: excluding 0xb0200000-0xb021ffff
[   18.621144] yenta_cardbus 0000:08:01.0: pcmcia: parent PCI bridge window: [mem 0x80000000-0x83ffffff pref]
[   18.621149] pcmcia_socket pcmcia_socket0: cs: memory probe 0x80000000-0x83ffffff: excluding 0x80000000-0x83ffffff
[   18.648592] cfg80211: World regulatory domain updated:
[   18.648598]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   18.648603]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   18.648608]     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   18.648612]     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   18.648616]     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   18.648620]     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   18.672172] [drm] Initialized drm 1.1.0 20060810
[   18.707874] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x100-0x3af: excluding 0x170-0x177 0x1f0-0x1f7 0x220-0x22f 0x370-0x377
[   18.710335] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x3e0-0x4ff: excluding 0x3f0-0x3f7 0x408-0x40f 0x4d0-0x4d7
[   18.711372] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x820-0x8ff: excluding 0x878-0x87f
[   18.712648] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xc00-0xcf7: excluding 0xc00-0xc07 0xc10-0xc17 0xc50-0xc57 0xc68-0xc6f 0xcd0-0xcdf
[   18.713464] pcmcia_socket pcmcia_socket0: cs: memory probe 0x0c0000-0x0fffff: excluding 0xc0000-0xfffff
[   18.713541] pcmcia_socket pcmcia_socket0: cs: memory probe 0xa0000000-0xa0ffffff: clean.
[   18.713619] pcmcia_socket pcmcia_socket0: cs: memory probe 0x60000000-0x60ffffff: excluding 0x60000000-0x60ffffff
[   18.713705] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xa00-0xaff: clean.
[   18.725648]   alloc irq_desc for 21 on node -1
[   18.725654]   alloc kstat_irqs on node -1
[   18.725664] ath5k 0000:08:04.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[   18.725811] ath5k 0000:08:04.0: registered as 'phy0'
[   18.786096] [drm] radeon defaulting to kernel modesetting.
[   18.786102] [drm] radeon kernel modesetting enabled.
[   18.786200]   alloc irq_desc for 17 on node -1
[   18.786203]   alloc kstat_irqs on node -1
[   18.786214] radeon 0000:01:05.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   18.788745] [drm] initializing kernel modesetting (RS480 0x1002:0x5975).
[   18.800099] [drm] register mmio base: 0xB0100000
[   18.800104] [drm] register mmio size: 65536
[   18.800297] [drm:rs400_gart_adjust_size] *ERROR* Forcing to 32M GART size (because of ASIC bug ?)
[   18.800352] [drm] Generation 2 PCI interface, using max accessible memory
[   18.800359] radeon 0000:01:05.0: VRAM: 256M 0x70000000 - 0x7FFFFFFF (256M used)
[   18.800364] radeon 0000:01:05.0: GTT: 32M 0x80000000 - 0x81FFFFFF
[   18.800415] [drm] radeon: irq initialized.
[   19.387659] [drm] Detected VRAM RAM=256M, BAR=256M
[   19.387665] [drm] RAM width 128bits DDR
[   19.396188] [TTM] Zone  kernel: Available graphics memory: 438204 kiB.
[   19.396193] [TTM] Zone highmem: Available graphics memory: 900320 kiB.
[   19.396197] [TTM] Initializing pool allocator.
[   19.396225] [drm] radeon: 256M of VRAM memory ready
[   19.396228] [drm] radeon: 32M of GTT memory ready.
[   19.396257] [drm] GART: num cpu pages 8192, num gpu pages 8192
[   19.397023] [drm] radeon: 1 quad pipes, 1 z pipes initialized.
[   19.398301] [drm] Loading R300 Microcode
[   19.454984] HDA Intel 0000:00:14.2: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   19.466647] [drm] radeon: ring at 0x0000000080000000
[   19.466669] [drm] ring test succeeded in 1 usecs
[   19.466896] [drm] radeon: ib pool ready.
[   19.466994] [drm] ib test succeeded in 0 usecs
[   19.467036] [drm] Default TV standard: NTSC
[   19.467038] [drm] 14.318180000 MHz TV ref clk
[   19.467137] [drm] Panel ID String: LPL                     
[   19.467140] [drm] Panel Size 1280x800
[   19.467207] [drm] Default TV standard: NTSC
[   19.467209] [drm] 14.318180000 MHz TV ref clk
[   19.467247] [drm] Radeon Display Connectors
[   19.467250] [drm] Connector 0:
[   19.467252] [drm]   VGA
[   19.467256] [drm]   DDC: 0x68 0x68 0x68 0x68 0x68 0x68 0x68 0x68
[   19.467258] [drm]   Encoders:
[   19.467260] [drm]     CRT1: INTERNAL_DAC2
[   19.467263] [drm] Connector 1:
[   19.467265] [drm]   LVDS
[   19.467268] [drm]   DDC: 0x198 0x198 0x19c 0x19c 0x1a0 0x1a0 0x1a4 0x1a4
[   19.467270] [drm]   Encoders:
[   19.467273] [drm]     LCD1: INTERNAL_LVDS
[   19.467275] [drm] Connector 2:
[   19.467277] [drm]   S-video
[   19.467279] [drm]   Encoders:
[   19.467281] [drm]     TV1: INTERNAL_DAC2
[   19.477431] ath: EEPROM regdomain: 0x63
[   19.477435] ath: EEPROM indicates we should expect a direct regpair map
[   19.477441] ath: Country alpha2 being used: 00
[   19.477444] ath: Regpair used: 0x63
[   19.516957] phy0: Selected rate control algorithm 'minstrel'
[   19.517793] ath5k phy0: Atheros AR2413 chip found (MAC: 0x78, PHY: 0x45)
[   19.546040] [drm] radeon: power management initialized
[   19.657432] hda_codec: ALC883: BIOS auto-probing.
[   19.657440] hda_codec: ALC883: SKU not ready 0x411111f0
[   19.672331] [drm] fb mappable at 0xC0040000
[   19.672336] [drm] vram apper at 0xC0000000
[   19.672339] [drm] size 4096000
[   19.672341] [drm] fb depth is 24
[   19.672344] [drm]    pitch is 5120
[   19.674227] Synaptics Touchpad, model: 1, fw: 6.2, id: 0x12a0b1, caps: 0xa04713/0x204000/0x0
[   19.724039] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio4/input/input5
[   19.739561] Console: switching to colour frame buffer device 160x50
[   19.750617] fb0: radeondrmfb frame buffer device
[   19.750620] drm: registered panic notifier
[   19.752352] Slow work thread pool: Starting up
[   19.757257] Slow work thread pool: Ready
[   19.757274] [drm] Initialized radeon 2.5.0 20080528 for 0000:01:05.0 on minor 0
[   30.567909] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
[   30.795351] ppdev: user-space parallel port driver
[   30.893563] eth0: link down
[   30.893957] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   30.927926] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   32.273673] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=0
[   32.970327] cfg80211: Found new beacon on frequency: 2472 MHz (Ch 13) on phy0
[   33.057064] wlan0: authenticate with 00:1d:70:99:4b:c1 (try 1)
[   33.058476] wlan0: authenticated
[   33.058502] wlan0: associate with 00:1d:70:99:4b:c1 (try 1)
[   33.060485] wlan0: RX AssocResp from 00:1d:70:99:4b:c1 (capab=0x421 status=0 aid=1)
[   33.060490] wlan0: associated
[   33.061471] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   33.799201] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=0
[   43.617028] wlan0: no IPv6 routers present
[   93.160066] Clocksource tsc unstable (delta = -113622594 ns)
[  116.269138] lo: Disabled Privacy Extensions
```

---

