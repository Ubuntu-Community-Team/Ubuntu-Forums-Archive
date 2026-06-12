---
title: "CD/DVD unrecognized. Install from drive worked fine."
date: 2011-05-01
forum: Hardware
---

### Post by Althippie on 2011-05-01
Hello Community,

I am working on an "Fujitsu Siemens Computers" Notebook (Amilo Pi 2550) and had to change the cd/dvd drive. Although in former times the Ubuntu (8.04) worked fine for me and recognized the cd/dvd drive perfectly AND the installation from the BRANDNEW Matshita UJ-831s of Ubuntu worked perfectly too, there is no possibility for me to access the cd/dvd-drive after installation.
Disk-Utility shows no information about cd/dvd drive (harddrive is recognized well) and lspci gives no feedback about my optical drive, too. 
The Ubuntu-Version I tried were: Ubuntu 10.10 and Ubuntu 11.04 (and Linux Mint 9 and Linux Mint 10). 
Nothing worked fine for me. 
Optical drive seems to work (otherwise installation would'nt work :-))

I would be glad to receive help for this problem and will do everything to help you help me. 


Here is the output of lspci
```

00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 03)
00:01.0 PCI bridge: Intel Corporation Mobile PM965/GM965/GL960 PCI Express Root Port (rev 03)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
01:00.0 VGA compatible controller: ATI Technologies Inc Mobility Radeon HD 2400
04:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)
05:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 01)


```

from dmesg
```

[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.38-8-generic-pae (buildd@vernadsky) (gcc version 4.5.2 (Ubuntu/Linaro 4.5.2-8ubuntu3) ) #42-Ubuntu SMP Mon Apr 11 05:17:09 UTC 2011 (Ubuntu 2.6.38-8.42-generic-pae 2.6.38.2)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
[    0.000000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 00000000bfed0000 (usable)
[    0.000000]  BIOS-e820: 00000000bfed0000 - 00000000bfedc000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000bfedc000 - 00000000c0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed00000 - 00000000fed00400 (reserved)
[    0.000000]  BIOS-e820: 00000000fed14000 - 00000000fed1a000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed1c000 - 00000000fed90000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000ff000000 - 0000000100000000 (reserved)
[    0.000000]  BIOS-e820: 0000000100000000 - 0000000140000000 (usable)
[    0.000000] NX (Execute Disable) protection: active
[    0.000000] DMI present.
[    0.000000] DMI: FUJITSU SIEMENS AMILO Pi 2550/F45                             , BIOS 1.12C 05/16/2008
[    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
[    0.000000] e820 remove range: 00000000000a0000 - 0000000000100000 (usable)
[    0.000000] last_pfn = 0x140000 max_arch_pfn = 0x1000000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 0C0000000 mask FC0000000 uncachable
[    0.000000]   1 base 000000000 mask F00000000 write-back
[    0.000000]   2 base 100000000 mask FC0000000 write-back
[    0.000000]   3 base 0BFF00000 mask FFFF00000 uncachable
[    0.000000]   4 disabled
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] e820 update range: 00000000bff00000 - 0000000100000000 (usable) ==> (reserved)
[    0.000000] found SMP MP-table at [c00f8030] f8030
[    0.000000] initial memory mapped : 0 - 01e00000
[    0.000000] init_memory_mapping: 0000000000000000-0000000037bfe000
[    0.000000]  0000000000 - 0000200000 page 4k
[    0.000000]  0000200000 - 0037a00000 page 2M
[    0.000000]  0037a00000 - 0037bfe000 page 4k
[    0.000000] kernel direct mapping tables up to 37bfe000 @ 1dfb000-1e00000
[    0.000000] RAMDISK: 36786000 - 373bb000
[    0.000000] ACPI: RSDP 000f8000 00024 (v02 PTLTD )
[    0.000000] ACPI: XSDT bfed24d6 0007C (v01 FSC    PC       06040000  LTP 00000000)
[    0.000000] ACPI: FACP bfed8c6c 000F4 (v03 INTEL  CRESTLNE 06040000 ALAN 00000001)
[    0.000000] ACPI: DSDT bfed3ae1 05117 (v02 ECS    F45      06040000 INTL 20050624)
[    0.000000] ACPI: FACS bfedbfc0 00040
[    0.000000] ACPI: HPET bfed8d60 00038 (v01 INTEL  CRESTLNE 06040000 LOHR 0000005A)
[    0.000000] ACPI: MCFG bfed8d98 0003C (v01 INTEL  CRESTLNE 06040000 LOHR 0000005A)
[    0.000000] ACPI: TMOR bfed8dd4 00026 (v01 PTLTD           06040000 PTL  00000003)
[    0.000000] ACPI: APIC bfed8dfa 00068 (v01 PTLTD  ? APIC   06040000  LTP 00000000)
[    0.000000] ACPI: BOOT bfed8e62 00028 (v01 PTLTD  $SBFTBL$ 06040000  LTP 00000001)
[    0.000000] ACPI: SLIC bfed8e8a 00176 (v01 FSC    PC       06040000  LTP 00000000)
[    0.000000] ACPI: SSDT bfed3804 002DD (v01 SataRe SataAhci 00001000 INTL 20050624)
[    0.000000] ACPI: SSDT bfed2b0e 0025F (v01  PmRef  Cpu0Tst 00003000 INTL 20050624)
[    0.000000] ACPI: SSDT bfed2a68 000A6 (v01  PmRef  Cpu1Tst 00003000 INTL 20050624)
[    0.000000] ACPI: SSDT bfed2552 00516 (v01  PmRef    CpuPm 00003000 INTL 20050624)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] 4228MB HIGHMEM available.
[    0.000000] 891MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 37bfe000
[    0.000000]   low ram: 0 - 37bfe000
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x00037bfe
[    0.000000]   HighMem  0x00037bfe -> 0x00140000
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[3] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x0000009f
[    0.000000]     0: 0x00000100 -> 0x000bfed0
[    0.000000]     0: 0x00100000 -> 0x00140000
[    0.000000] On node 0 totalpages: 1048159
[    0.000000] free_area_init_node: node 0, pgdat c17babc0, node_mem_map f3f86200
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3951 pages, LIFO batch:0
[    0.000000]   Normal zone: 1752 pages used for memmap
[    0.000000]   Normal zone: 222502 pages, LIFO batch:31
[    0.000000]   HighMem zone: 8457 pages used for memmap
[    0.000000]   HighMem zone: 811465 pages, LIFO batch:31
[    0.000000] Using APIC driver default
[    0.000000] ACPI: PM-Timer IO Port: 0x1008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 high edge)
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
[    0.000000] Allocating PCI resources starting at c0000000 (gap: c0000000:20000000)
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] setup_percpu: NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:2 nr_node_ids:1
[    0.000000] PERCPU: Embedded 13 pages/cpu @f7800000 s32320 r0 d20928 u1048576
[    0.000000] pcpu-alloc: s32320 r0 d20928 u1048576 alloc=1*2097152
[    0.000000] pcpu-alloc: [0] 0 1 
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 1037918
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.38-8-generic-pae root=UUID=8be9ef43-4b64-4558-be79-2bd6d4de096f ro quiet splash vt.handoff=7
[    0.000000] PID hash table entries: 4096 (order: 2, 16384 bytes)
[    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.000000] Initializing CPU#0
[    0.000000] allocated 26214080 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] Initializing HighMem for node 0 (00037bfe:00140000)
[    0.000000] Memory: 4102960k/5242880k available (5349k kernel code, 89676k reserved, 2599k data, 720k init, 3279688k highmem)
[    0.000000] virtual kernel memory layout:
[    0.000000]     fixmap  : 0xfff16000 - 0xfffff000   ( 932 kB)
[    0.000000]     pkmap   : 0xffc00000 - 0xffe00000   (2048 kB)
[    0.000000]     vmalloc : 0xf83fe000 - 0xffbfe000   ( 120 MB)
[    0.000000]     lowmem  : 0xc0000000 - 0xf7bfe000   ( 891 MB)
[    0.000000]       .init : 0xc17c4000 - 0xc1878000   ( 720 kB)
[    0.000000]       .data : 0xc1539545 - 0xc17c3540   (2599 kB)
[    0.000000]       .text : 0xc1000000 - 0xc1539545   (5349 kB)
[    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.000000] SLUB: Genslabs=15, HWalign=64, Order=0-3, MinObjects=0, CPUs=2, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000] 	RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000] 	RCU-based detection of stalled CPUs is disabled.
[    0.000000] NR_IRQS:2304 nr_irqs:512 16
[    0.000000] CPU 0 irqstacks, hard=f7408000 soft=f740a000
[    0.000000] Extended CMOS year: 2000
[    0.000000] vt handoff: transparent VT on vt#7
[    0.000000] Console: colour dummy device 80x25
[    0.000000] console [tty0] enabled
[    0.000000] hpet clockevent registered
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 2394.179 MHz processor.
[    0.004003] Calibrating delay loop (skipped), value calculated using timer frequency.. 4788.35 BogoMIPS (lpj=9576716)
[    0.004007] pid_max: default: 32768 minimum: 301
[    0.004025] Security Framework initialized
[    0.004039] AppArmor: AppArmor initialized
[    0.004041] Yama: becoming mindful.
[    0.004091] Mount-cache hash table entries: 512
[    0.004210] Initializing cgroup subsys ns
[    0.004214] ns_cgroup deprecated: consider using the 'clone_children' flag without the ns_cgroup.
[    0.004216] Initializing cgroup subsys cpuacct
[    0.004220] Initializing cgroup subsys memory
[    0.004227] Initializing cgroup subsys devices
[    0.004229] Initializing cgroup subsys freezer
[    0.004231] Initializing cgroup subsys net_cls
[    0.004233] Initializing cgroup subsys blkio
[    0.004264] CPU: Physical Processor ID: 0
[    0.004266] CPU: Processor Core ID: 0
[    0.004268] mce: CPU supports 6 MCE banks
[    0.004276] CPU0: Thermal monitoring enabled (TM2)
[    0.004279] using mwait in idle threads.
[    0.006539] ACPI: Core revision 20110112
[    0.011863] ftrace: allocating 24250 entries in 48 pages
[    0.016046] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.016390] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.057069] CPU0: Intel(R) Core(TM)2 Duo CPU     T8300  @ 2.40GHz stepping 06
[    0.060003] Performance Events: PEBS fmt0+, Core2 events, Intel PMU driver.
[    0.060003] ... version:                2
[    0.060003] ... bit width:              40
[    0.060003] ... generic registers:      2
[    0.060003] ... value mask:             000000ffffffffff
[    0.060003] ... max period:             000000007fffffff
[    0.060003] ... fixed-purpose events:   3
[    0.060003] ... event mask:             0000000700000003
[    0.060003] CPU 1 irqstacks, hard=f74ca000 soft=f74cc000
[    0.060003] Booting Node   0, Processors  #1 Ok.
[    0.008000] Initializing CPU#1
[    0.148024] Brought up 2 CPUs
[    0.148027] Total of 2 processors activated (9576.30 BogoMIPS).
[    0.148661] devtmpfs: initialized
[    0.149080] print_constraints: dummy: 
[    0.149110] Time: 14:19:10  Date: 05/01/11
[    0.149144] NET: Registered protocol family 16
[    0.149169] Trying to unpack rootfs image as initramfs...
[    0.149254] EISA bus registered
[    0.149272] ACPI: bus type pci registered
[    0.149343] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xe0000000-0xefffffff] (base 0xe0000000)
[    0.149346] PCI: MMCONFIG at [mem 0xe0000000-0xefffffff] reserved in E820
[    0.149348] PCI: Using MMCONFIG for extended config space
[    0.149349] PCI: Using configuration type 1 for base access
[    0.164069] bio: create slab <bio-0> at 0
[    0.165257] ACPI: EC: Look up EC in DSDT
[    0.167410] [Firmware Bug]: ACPI: BIOS _OSI(Linux) query ignored
[    0.168184] ACPI: SSDT bfed33fe 0033E (v01  PmRef  Cpu0Ist 00003000 INTL 20050624)
[    0.168467] ACPI: Dynamic OEM Table Load:
[    0.168470] ACPI: SSDT   (null) 0033E (v01  PmRef  Cpu0Ist 00003000 INTL 20050624)
[    0.168616] ACPI: SSDT bfed2d6d 0060C (v01  PmRef  Cpu0Cst 00003001 INTL 20050624)
[    0.168881] ACPI: Dynamic OEM Table Load:
[    0.168884] ACPI: SSDT   (null) 0060C (v01  PmRef  Cpu0Cst 00003001 INTL 20050624)
[    0.169132] ACPI: SSDT bfed373c 000C8 (v01  PmRef  Cpu1Ist 00003000 INTL 20050624)
[    0.169406] ACPI: Dynamic OEM Table Load:
[    0.169409] ACPI: SSDT   (null) 000C8 (v01  PmRef  Cpu1Ist 00003000 INTL 20050624)
[    0.169508] ACPI: SSDT bfed3379 00085 (v01  PmRef  Cpu1Cst 00003000 INTL 20050624)
[    0.169774] ACPI: Dynamic OEM Table Load:
[    0.169777] ACPI: SSDT   (null) 00085 (v01  PmRef  Cpu1Cst 00003000 INTL 20050624)
[    0.248067] ACPI: Interpreter enabled
[    0.248077] ACPI: (supports S0 S3 S4 S5)
[    0.248104] ACPI: Using IOAPIC for interrupt routing
[    0.293282] ACPI: EC: GPE = 0x11, I/O: command/status = 0x66, data = 0x62
[    0.293459] ACPI: No dock devices found.
[    0.293462] HEST: Table not found.
[    0.293466] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[    0.293783] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
[    0.294401] pci_root PNP0A08:00: host bridge window [io  0x0000-0x0cf7]
[    0.294403] pci_root PNP0A08:00: host bridge window [io  0x0d00-0xffff]
[    0.294406] pci_root PNP0A08:00: host bridge window [mem 0x000a0000-0x000bffff]
[    0.294409] pci_root PNP0A08:00: host bridge window [mem 0x000d0000-0x000d3fff]
[    0.294411] pci_root PNP0A08:00: host bridge window [mem 0x000d4000-0x000d7fff]
[    0.294413] pci_root PNP0A08:00: host bridge window [mem 0x000d8000-0x000dbfff]
[    0.294416] pci_root PNP0A08:00: host bridge window [mem 0x000dc000-0x000dffff]
[    0.294418] pci_root PNP0A08:00: host bridge window [mem 0xc0000000-0xdfffffff]
[    0.294421] pci_root PNP0A08:00: host bridge window [mem 0xf0000000-0xfebfffff]
[    0.294437] pci 0000:00:00.0: [8086:2a00] type 0 class 0x000600
[    0.294483] pci 0000:00:01.0: [8086:2a01] type 1 class 0x000604
[    0.294517] pci 0000:00:01.0: PME# supported from D0 D3hot D3cold
[    0.294521] pci 0000:00:01.0: PME# disabled
[    0.294576] pci 0000:00:1a.0: [8086:2834] type 0 class 0x000c03
[    0.294635] pci 0000:00:1a.0: reg 20: [io  0x1800-0x181f]
[    0.294676] pci 0000:00:1a.1: [8086:2835] type 0 class 0x000c03
[    0.294734] pci 0000:00:1a.1: reg 20: [io  0x1820-0x183f]
[    0.294790] pci 0000:00:1a.7: [8086:283a] type 0 class 0x000c03
[    0.294815] pci 0000:00:1a.7: reg 10: [mem 0xf0404800-0xf0404bff]
[    0.294911] pci 0000:00:1a.7: PME# supported from D0 D3hot D3cold
[    0.294916] pci 0000:00:1a.7: PME# disabled
[    0.294946] pci 0000:00:1b.0: [8086:284b] type 0 class 0x000403
[    0.294969] pci 0000:00:1b.0: reg 10: [mem 0xf0400000-0xf0403fff 64bit]
[    0.295054] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    0.295059] pci 0000:00:1b.0: PME# disabled
[    0.295088] pci 0000:00:1c.0: [8086:283f] type 1 class 0x000604
[    0.295177] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.295181] pci 0000:00:1c.0: PME# disabled
[    0.295214] pci 0000:00:1c.2: [8086:2843] type 1 class 0x000604
[    0.295303] pci 0000:00:1c.2: PME# supported from D0 D3hot D3cold
[    0.295308] pci 0000:00:1c.2: PME# disabled
[    0.295340] pci 0000:00:1c.3: [8086:2845] type 1 class 0x000604
[    0.295428] pci 0000:00:1c.3: PME# supported from D0 D3hot D3cold
[    0.295433] pci 0000:00:1c.3: PME# disabled
[    0.295466] pci 0000:00:1d.0: [8086:2830] type 0 class 0x000c03
[    0.295524] pci 0000:00:1d.0: reg 20: [io  0x1840-0x185f]
[    0.295565] pci 0000:00:1d.1: [8086:2831] type 0 class 0x000c03
[    0.295625] pci 0000:00:1d.1: reg 20: [io  0x1860-0x187f]
[    0.295665] pci 0000:00:1d.2: [8086:2832] type 0 class 0x000c03
[    0.295723] pci 0000:00:1d.2: reg 20: [io  0x1880-0x189f]
[    0.295777] pci 0000:00:1d.7: [8086:2836] type 0 class 0x000c03
[    0.295802] pci 0000:00:1d.7: reg 10: [mem 0xf0404c00-0xf0404fff]
[    0.295898] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
[    0.295903] pci 0000:00:1d.7: PME# disabled
[    0.295928] pci 0000:00:1e.0: [8086:2448] type 1 class 0x000604
[    0.296026] pci 0000:00:1f.0: [8086:2815] type 0 class 0x000601
[    0.296134] pci 0000:00:1f.0: quirk: [io  0x1000-0x107f] claimed by ICH6 ACPI/GPIO/TCO
[    0.296140] pci 0000:00:1f.0: quirk: [io  0x1180-0x11bf] claimed by ICH6 GPIO
[    0.296145] pci 0000:00:1f.0: ICH7 LPC Generic IO decode 1 PIO at 0068 (mask 0007)
[    0.296149] pci 0000:00:1f.0: ICH7 LPC Generic IO decode 2 PIO at 0260 (mask 0003)
[    0.296193] pci 0000:00:1f.1: [8086:2850] type 0 class 0x000101
[    0.296211] pci 0000:00:1f.1: reg 10: [io  0x0000-0x0007]
[    0.296223] pci 0000:00:1f.1: reg 14: [io  0x0000-0x0003]
[    0.296236] pci 0000:00:1f.1: reg 18: [io  0x0000-0x0007]
[    0.296248] pci 0000:00:1f.1: reg 1c: [io  0x0000-0x0003]
[    0.296261] pci 0000:00:1f.1: reg 20: [io  0x18a0-0x18af]
[    0.296314] pci 0000:00:1f.2: [8086:2829] type 0 class 0x000106
[    0.296341] pci 0000:00:1f.2: reg 10: [io  0x18d8-0x18df]
[    0.296354] pci 0000:00:1f.2: reg 14: [io  0x18cc-0x18cf]
[    0.296366] pci 0000:00:1f.2: reg 18: [io  0x18d0-0x18d7]
[    0.296378] pci 0000:00:1f.2: reg 1c: [io  0x18c8-0x18cb]
[    0.296390] pci 0000:00:1f.2: reg 20: [io  0x18e0-0x18ff]
[    0.296402] pci 0000:00:1f.2: reg 24: [mem 0xf0404000-0xf04047ff]
[    0.296450] pci 0000:00:1f.2: PME# supported from D3hot
[    0.296454] pci 0000:00:1f.2: PME# disabled
[    0.296476] pci 0000:00:1f.3: [8086:283e] type 0 class 0x000c05
[    0.296493] pci 0000:00:1f.3: reg 10: [mem 0x00000000-0x000000ff]
[    0.296536] pci 0000:00:1f.3: reg 20: [io  0x1c00-0x1c1f]
[    0.296618] pci 0000:01:00.0: [1002:94c9] type 0 class 0x000300
[    0.296641] pci 0000:01:00.0: reg 10: [mem 0xd0000000-0xdfffffff 64bit pref]
[    0.296659] pci 0000:01:00.0: reg 18: [mem 0xcfef0000-0xcfefffff 64bit]
[    0.296671] pci 0000:01:00.0: reg 20: [io  0x2000-0x20ff]
[    0.296693] pci 0000:01:00.0: reg 30: [mem 0x00000000-0x0001ffff pref]
[    0.296724] pci 0000:01:00.0: supports D1 D2
[    0.296758] pci 0000:00:01.0: PCI bridge to [bus 01-01]
[    0.296762] pci 0000:00:01.0:   bridge window [io  0x2000-0x2fff]
[    0.296766] pci 0000:00:01.0:   bridge window [mem 0xcfe00000-0xcfefffff]
[    0.296771] pci 0000:00:01.0:   bridge window [mem 0xd0000000-0xdfffffff 64bit pref]
[    0.296834] pci 0000:00:1c.0: PCI bridge to [bus 02-03]
[    0.296839] pci 0000:00:1c.0:   bridge window [io  0xf000-0xffff]
[    0.296844] pci 0000:00:1c.0:   bridge window [mem 0xfb000000-0xfcffffff]
[    0.296852] pci 0000:00:1c.0:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    0.296974] pci 0000:04:00.0: [8086:4222] type 0 class 0x000280
[    0.297029] pci 0000:04:00.0: reg 10: [mem 0xf0200000-0xf0200fff]
[    0.297365] pci 0000:04:00.0: PME# supported from D0 D3hot D3cold
[    0.297378] pci 0000:04:00.0: PME# disabled
[    0.297447] pci 0000:04:00.0: disabling ASPM on pre-1.1 PCIe device.  You can enable it with 'pcie_aspm=force'
[    0.297486] pci 0000:00:1c.2: PCI bridge to [bus 04-04]
[    0.297491] pci 0000:00:1c.2:   bridge window [io  0xf000-0x0000] (disabled)
[    0.297496] pci 0000:00:1c.2:   bridge window [mem 0xf0200000-0xf02fffff]
[    0.297503] pci 0000:00:1c.2:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    0.297596] pci 0000:05:00.0: [10ec:8136] type 0 class 0x000200
[    0.297619] pci 0000:05:00.0: reg 10: [io  0x3000-0x30ff]
[    0.297662] pci 0000:05:00.0: reg 18: [mem 0xf0300000-0xf0300fff 64bit]
[    0.297710] pci 0000:05:00.0: reg 30: [mem 0x00000000-0x0001ffff pref]
[    0.297771] pci 0000:05:00.0: supports D1 D2
[    0.297773] pci 0000:05:00.0: PME# supported from D1 D2 D3hot D3cold
[    0.297779] pci 0000:05:00.0: PME# disabled
[    0.297808] pci 0000:05:00.0: disabling ASPM on pre-1.1 PCIe device.  You can enable it with 'pcie_aspm=force'
[    0.297820] pci 0000:00:1c.3: PCI bridge to [bus 05-05]
[    0.297825] pci 0000:00:1c.3:   bridge window [io  0x3000-0x3fff]
[    0.297830] pci 0000:00:1c.3:   bridge window [mem 0xf0300000-0xf03fffff]
[    0.297838] pci 0000:00:1c.3:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    0.297926] pci 0000:00:1e.0: PCI bridge to [bus 06-06] (subtractive decode)
[    0.297931] pci 0000:00:1e.0:   bridge window [io  0xf000-0x0000] (disabled)
[    0.297936] pci 0000:00:1e.0:   bridge window [mem 0xfff00000-0x000fffff] (disabled)
[    0.297944] pci 0000:00:1e.0:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    0.297946] pci 0000:00:1e.0:   bridge window [io  0x0000-0x0cf7] (subtractive decode)
[    0.297949] pci 0000:00:1e.0:   bridge window [io  0x0d00-0xffff] (subtractive decode)
[    0.297951] pci 0000:00:1e.0:   bridge window [mem 0x000a0000-0x000bffff] (subtractive decode)
[    0.297953] pci 0000:00:1e.0:   bridge window [mem 0x000d0000-0x000d3fff] (subtractive decode)
[    0.297956] pci 0000:00:1e.0:   bridge window [mem 0x000d4000-0x000d7fff] (subtractive decode)
[    0.297958] pci 0000:00:1e.0:   bridge window [mem 0x000d8000-0x000dbfff] (subtractive decode)
[    0.297961] pci 0000:00:1e.0:   bridge window [mem 0x000dc000-0x000dffff] (subtractive decode)
[    0.297963] pci 0000:00:1e.0:   bridge window [mem 0xc0000000-0xdfffffff] (subtractive decode)
[    0.297965] pci 0000:00:1e.0:   bridge window [mem 0xf0000000-0xfebfffff] (subtractive decode)
[    0.297995] pci_bus 0000:00: on NUMA node 0
[    0.297998] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.298198] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEGP._PRT]
[    0.298257] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP01._PRT]
[    0.298313] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP03._PRT]
[    0.298367] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP04._PRT]
[    0.298449] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIB._PRT]
[    0.298492]  pci0000:00: Requesting ACPI _OSC control (0x1d)
[    0.303942] ACPI: PCI Interrupt Link [LNKA] (IRQs 1 3 4 *5 6 7 10 12 14 15)
[    0.303995] ACPI: PCI Interrupt Link [LNKB] (IRQs 1 3 4 5 6 7 11 12 14 15) *10
[    0.304055] ACPI: PCI Interrupt Link [LNKC] (IRQs 1 3 4 5 6 *7 10 12 14 15)
[    0.304104] ACPI: PCI Interrupt Link [LNKD] (IRQs 1 3 4 5 6 7 11 12 14 15) *10
[    0.304153] ACPI: PCI Interrupt Link [LNKE] (IRQs 1 3 4 5 6 7 10 12 14 15) *0, disabled.
[    0.304203] ACPI: PCI Interrupt Link [LNKF] (IRQs 1 3 4 5 6 7 *11 12 14 15)
[    0.304252] ACPI: PCI Interrupt Link [LNKG] (IRQs 1 3 4 5 6 7 10 12 14 15) *11
[    0.304302] ACPI: PCI Interrupt Link [LNKH] (IRQs 1 3 4 5 6 7 11 12 14 15) *10
[    0.304427] vgaarb: device added: PCI:0000:01:00.0,decodes=io+mem,owns=io+mem,locks=none
[    0.304430] vgaarb: loaded
[    0.304630] SCSI subsystem initialized
[    0.304693] libata version 3.00 loaded.
[    0.304740] usbcore: registered new interface driver usbfs
[    0.304751] usbcore: registered new interface driver hub
[    0.304778] usbcore: registered new device driver usb
[    0.304982] wmi: Mapper loaded
[    0.304984] PCI: Using ACPI for IRQ routing
[    0.304987] PCI: pci_cache_line_size set to 64 bytes
[    0.305092] reserve RAM buffer: 000000000009f800 - 000000000009ffff 
[    0.305095] reserve RAM buffer: 00000000bfed0000 - 00000000bfffffff 
[    0.305199] NetLabel: Initializing
[    0.305201] NetLabel:  domain hash size = 128
[    0.305202] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.305213] NetLabel:  unlabeled traffic allowed by default
[    0.305248] HPET: 3 timers in total, 0 timers will be used for per-cpu timer
[    0.305254] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[    0.305259] hpet0: 3 comparators, 64-bit 14.318180 MHz counter
[    0.312065] Switching to clocksource hpet
[    0.315829] Switched to NOHz mode on CPU #0
[    0.315925] Switched to NOHz mode on CPU #1
[    0.319457] AppArmor: AppArmor Filesystem Enabled
[    0.319489] pnp: PnP ACPI init
[    0.319515] ACPI: bus type pnp registered
[    0.336359] pnp 00:00: [bus 00-ff]
[    0.336363] pnp 00:00: [io  0x0000-0x0cf7 window]
[    0.336365] pnp 00:00: [io  0x0cf8-0x0cff]
[    0.336367] pnp 00:00: [io  0x0d00-0xffff window]
[    0.336370] pnp 00:00: [mem 0x000a0000-0x000bffff window]
[    0.336372] pnp 00:00: [mem 0x000c0000-0x000c3fff window]
[    0.336374] pnp 00:00: [mem 0x000c4000-0x000c7fff window]
[    0.336376] pnp 00:00: [mem 0x000c8000-0x000cbfff window]
[    0.336379] pnp 00:00: [mem 0x000cc000-0x000cffff window]
[    0.336381] pnp 00:00: [mem 0x000d0000-0x000d3fff window]
[    0.336383] pnp 00:00: [mem 0x000d4000-0x000d7fff window]
[    0.336385] pnp 00:00: [mem 0x000d8000-0x000dbfff window]
[    0.336387] pnp 00:00: [mem 0x000dc000-0x000dffff window]
[    0.336390] pnp 00:00: [mem 0x000e0000-0x000e3fff window]
[    0.336392] pnp 00:00: [mem 0x000e4000-0x000e7fff window]
[    0.336394] pnp 00:00: [mem 0x000e8000-0x000ebfff window]
[    0.336396] pnp 00:00: [mem 0x000ec000-0x000effff window]
[    0.336398] pnp 00:00: [mem 0x000f0000-0x000fffff window]
[    0.336401] pnp 00:00: [mem 0xc0000000-0xdfffffff window]
[    0.336403] pnp 00:00: [mem 0xf0000000-0xfebfffff window]
[    0.336405] pnp 00:00: [mem 0xfed40000-0xfed44fff window]
[    0.336507] pnp 00:00: Plug and Play ACPI device, IDs PNP0a08 PNP0a03 (active)
[    0.336587] pnp 00:01: [mem 0xfed1c000-0xfed1ffff]
[    0.336589] pnp 00:01: [mem 0xfed14000-0xfed17fff]
[    0.336592] pnp 00:01: [mem 0xfed18000-0xfed18fff]
[    0.336594] pnp 00:01: [mem 0xfed19000-0xfed19fff]
[    0.336596] pnp 00:01: [mem 0xe0000000-0xefffffff]
[    0.336597] pnp 00:01: [mem 0xfed20000-0xfed3ffff]
[    0.336599] pnp 00:01: [mem 0xfed40000-0xfed44fff]
[    0.336601] pnp 00:01: [mem 0xfed45000-0xfed8ffff]
[    0.336669] system 00:01: [mem 0xfed1c000-0xfed1ffff] has been reserved
[    0.336672] system 00:01: [mem 0xfed14000-0xfed17fff] has been reserved
[    0.336675] system 00:01: [mem 0xfed18000-0xfed18fff] has been reserved
[    0.336677] system 00:01: [mem 0xfed19000-0xfed19fff] has been reserved
[    0.336680] system 00:01: [mem 0xe0000000-0xefffffff] has been reserved
[    0.336682] system 00:01: [mem 0xfed20000-0xfed3ffff] has been reserved
[    0.336685] system 00:01: [mem 0xfed40000-0xfed44fff] has been reserved
[    0.336688] system 00:01: [mem 0xfed45000-0xfed8ffff] has been reserved
[    0.336691] system 00:01: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.336923] pnp 00:02: [io  0x0068]
[    0.336925] pnp 00:02: [io  0x006c]
[    0.336927] pnp 00:02: [io  0x0260-0x0261]
[    0.336939] pnp 00:02: [irq 10]
[    0.336989] pnp 00:02: Plug and Play ACPI device, IDs ITE8709 (active)
[    0.337000] pnp 00:03: [io  0x0000-0x001f]
[    0.337002] pnp 00:03: [io  0x0081-0x0091]
[    0.337004] pnp 00:03: [io  0x0093-0x009f]
[    0.337006] pnp 00:03: [io  0x00c0-0x00df]
[    0.337008] pnp 00:03: [dma 4]
[    0.337054] pnp 00:03: Plug and Play ACPI device, IDs PNP0200 (active)
[    0.337063] pnp 00:04: [mem 0xff000000-0xffffffff]
[    0.337110] pnp 00:04: Plug and Play ACPI device, IDs INT0800 (active)
[    0.337178] pnp 00:05: [mem 0xfed00000-0xfed003ff]
[    0.337245] system 00:05: [mem 0xfed00000-0xfed003ff] has been reserved
[    0.337248] system 00:05: Plug and Play ACPI device, IDs PNP0103 PNP0c01 (active)
[    0.337259] pnp 00:06: [io  0x00f0]
[    0.337265] pnp 00:06: [irq 13]
[    0.337315] pnp 00:06: Plug and Play ACPI device, IDs PNP0c04 (active)
[    0.337326] pnp 00:07: [io  0x002e-0x002f]
[    0.337328] pnp 00:07: [io  0x004e-0x004f]
[    0.337330] pnp 00:07: [io  0x0061]
[    0.337332] pnp 00:07: [io  0x0063]
[    0.337334] pnp 00:07: [io  0x0065]
[    0.337336] pnp 00:07: [io  0x0067]
[    0.337338] pnp 00:07: [io  0x0080]
[    0.337339] pnp 00:07: [io  0x0092]
[    0.337344] pnp 00:07: [io  0x00b2-0x00b3]
[    0.337346] pnp 00:07: [io  0x0680-0x069f]
[    0.337348] pnp 00:07: [io  0x0800-0x080f]
[    0.337350] pnp 00:07: [io  0x1000-0x107f]
[    0.337352] pnp 00:07: [io  0x1180-0x11bf]
[    0.337354] pnp 00:07: [io  0x1640-0x164f]
[    0.337355] pnp 00:07: [io  0xfe00]
[    0.337367] pnp 00:07: disabling [io  0xfe00] because it overlaps 0000:00:1c.0 BAR 13 [io  0xf000-0xffff]
[    0.337438] system 00:07: [io  0x0680-0x069f] has been reserved
[    0.337441] system 00:07: [io  0x0800-0x080f] has been reserved
[    0.337443] system 00:07: [io  0x1000-0x107f] has been reserved
[    0.337446] system 00:07: [io  0x1180-0x11bf] has been reserved
[    0.337448] system 00:07: [io  0x1640-0x164f] has been reserved
[    0.337452] system 00:07: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.337461] pnp 00:08: [io  0x0070-0x0077]
[    0.337466] pnp 00:08: [irq 8]
[    0.337514] pnp 00:08: Plug and Play ACPI device, IDs PNP0b00 (active)
[    0.337564] pnp 00:09: [io  0x0060]
[    0.337566] pnp 00:09: [io  0x0064]
[    0.337572] pnp 00:09: [irq 1]
[    0.337626] pnp 00:09: Plug and Play ACPI device, IDs PNP0303 (active)
[    0.337638] pnp 00:0a: [irq 12]
[    0.337691] pnp 00:0a: Plug and Play ACPI device, IDs SYN0804 SYN0800 PNP0f13 (active)
[    0.337713] pnp: PnP ACPI: found 11 devices
[    0.337714] ACPI: ACPI bus type pnp unregistered
[    0.337718] PnPBIOS: Disabled by ACPI PNP
[    0.374075] pci 0000:00:1c.0: BAR 15: assigned [mem 0xc0000000-0xc01fffff 64bit pref]
[    0.374081] pci 0000:00:1c.2: BAR 15: assigned [mem 0xc0200000-0xc03fffff 64bit pref]
[    0.374086] pci 0000:00:1c.3: BAR 15: assigned [mem 0xc0400000-0xc05fffff pref]
[    0.374090] pci 0000:00:1c.2: BAR 13: assigned [io  0x4000-0x4fff]
[    0.374094] pci 0000:00:1f.3: BAR 0: assigned [mem 0xc0600000-0xc06000ff]
[    0.374100] pci 0000:00:1f.3: BAR 0: set to [mem 0xc0600000-0xc06000ff] (PCI address [0xc0600000-0xc06000ff])
[    0.374105] pci 0000:01:00.0: BAR 6: assigned [mem 0xcfe00000-0xcfe1ffff pref]
[    0.374107] pci 0000:00:01.0: PCI bridge to [bus 01-01]
[    0.374110] pci 0000:00:01.0:   bridge window [io  0x2000-0x2fff]
[    0.374114] pci 0000:00:01.0:   bridge window [mem 0xcfe00000-0xcfefffff]
[    0.374117] pci 0000:00:01.0:   bridge window [mem 0xd0000000-0xdfffffff 64bit pref]
[    0.374122] pci 0000:00:1c.0: PCI bridge to [bus 02-03]
[    0.374125] pci 0000:00:1c.0:   bridge window [io  0xf000-0xffff]
[    0.374132] pci 0000:00:1c.0:   bridge window [mem 0xfb000000-0xfcffffff]
[    0.374136] pci 0000:00:1c.0:   bridge window [mem 0xc0000000-0xc01fffff 64bit pref]
[    0.374144] pci 0000:00:1c.2: PCI bridge to [bus 04-04]
[    0.374147] pci 0000:00:1c.2:   bridge window [io  0x4000-0x4fff]
[    0.374154] pci 0000:00:1c.2:   bridge window [mem 0xf0200000-0xf02fffff]
[    0.374158] pci 0000:00:1c.2:   bridge window [mem 0xc0200000-0xc03fffff 64bit pref]
[    0.374167] pci 0000:05:00.0: BAR 6: assigned [mem 0xc0400000-0xc041ffff pref]
[    0.374169] pci 0000:00:1c.3: PCI bridge to [bus 05-05]
[    0.374172] pci 0000:00:1c.3:   bridge window [io  0x3000-0x3fff]
[    0.374179] pci 0000:00:1c.3:   bridge window [mem 0xf0300000-0xf03fffff]
[    0.374183] pci 0000:00:1c.3:   bridge window [mem 0xc0400000-0xc05fffff pref]
[    0.374191] pci 0000:00:1e.0: PCI bridge to [bus 06-06]
[    0.374193] pci 0000:00:1e.0:   bridge window [io  disabled]
[    0.374199] pci 0000:00:1e.0:   bridge window [mem disabled]
[    0.374204] pci 0000:00:1e.0:   bridge window [mem pref disabled]
[    0.374230] pci 0000:00:01.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.374235] pci 0000:00:01.0: setting latency timer to 64
[    0.374245] pci 0000:00:1c.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    0.374251] pci 0000:00:1c.0: setting latency timer to 64
[    0.374261] pci 0000:00:1c.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.374266] pci 0000:00:1c.2: setting latency timer to 64
[    0.374276] pci 0000:00:1c.3: PCI INT D -> GSI 19 (level, low) -> IRQ 19
[    0.374282] pci 0000:00:1c.3: setting latency timer to 64
[    0.374291] pci 0000:00:1e.0: setting latency timer to 64
[    0.374295] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
[    0.374297] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
[    0.374300] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
[    0.374302] pci_bus 0000:00: resource 7 [mem 0x000d0000-0x000d3fff]
[    0.374304] pci_bus 0000:00: resource 8 [mem 0x000d4000-0x000d7fff]
[    0.374306] pci_bus 0000:00: resource 9 [mem 0x000d8000-0x000dbfff]
[    0.374309] pci_bus 0000:00: resource 10 [mem 0x000dc000-0x000dffff]
[    0.374311] pci_bus 0000:00: resource 11 [mem 0xc0000000-0xdfffffff]
[    0.374313] pci_bus 0000:00: resource 12 [mem 0xf0000000-0xfebfffff]
[    0.374316] pci_bus 0000:01: resource 0 [io  0x2000-0x2fff]
[    0.374318] pci_bus 0000:01: resource 1 [mem 0xcfe00000-0xcfefffff]
[    0.374320] pci_bus 0000:01: resource 2 [mem 0xd0000000-0xdfffffff 64bit pref]
[    0.374323] pci_bus 0000:02: resource 0 [io  0xf000-0xffff]
[    0.374325] pci_bus 0000:02: resource 1 [mem 0xfb000000-0xfcffffff]
[    0.374327] pci_bus 0000:02: resource 2 [mem 0xc0000000-0xc01fffff 64bit pref]
[    0.374330] pci_bus 0000:04: resource 0 [io  0x4000-0x4fff]
[    0.374332] pci_bus 0000:04: resource 1 [mem 0xf0200000-0xf02fffff]
[    0.374335] pci_bus 0000:04: resource 2 [mem 0xc0200000-0xc03fffff 64bit pref]
[    0.374337] pci_bus 0000:05: resource 0 [io  0x3000-0x3fff]
[    0.374339] pci_bus 0000:05: resource 1 [mem 0xf0300000-0xf03fffff]
[    0.374342] pci_bus 0000:05: resource 2 [mem 0xc0400000-0xc05fffff pref]
[    0.374344] pci_bus 0000:06: resource 4 [io  0x0000-0x0cf7]
[    0.374346] pci_bus 0000:06: resource 5 [io  0x0d00-0xffff]
[    0.374348] pci_bus 0000:06: resource 6 [mem 0x000a0000-0x000bffff]
[    0.374351] pci_bus 0000:06: resource 7 [mem 0x000d0000-0x000d3fff]
[    0.374353] pci_bus 0000:06: resource 8 [mem 0x000d4000-0x000d7fff]
[    0.374355] pci_bus 0000:06: resource 9 [mem 0x000d8000-0x000dbfff]
[    0.374357] pci_bus 0000:06: resource 10 [mem 0x000dc000-0x000dffff]
[    0.374360] pci_bus 0000:06: resource 11 [mem 0xc0000000-0xdfffffff]
[    0.374362] pci_bus 0000:06: resource 12 [mem 0xf0000000-0xfebfffff]
[    0.374408] NET: Registered protocol family 2
[    0.374477] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.374715] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.375166] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.375398] TCP: Hash tables configured (established 131072 bind 65536)
[    0.375401] TCP reno registered
[    0.375404] UDP hash table entries: 512 (order: 2, 16384 bytes)
[    0.375413] UDP-Lite hash table entries: 512 (order: 2, 16384 bytes)
[    0.375489] NET: Registered protocol family 1
[    0.375655] pci 0000:01:00.0: Boot video device
[    0.375669] PCI: CLS 64 bytes, default 64
[    0.375698] Simple Boot Flag at 0x36 set to 0x1
[    0.375891] cpufreq-nforce2: No nForce2 chipset.
[    0.376041] audit: initializing netlink socket (disabled)
[    0.376050] type=2000 audit(1304259550.372:1): initialized
[    0.385231] highmem bounce pool size: 64 pages
[    0.385236] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    0.386916] VFS: Disk quotas dquot_6.5.2
[    0.386973] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.387605] fuse init (API version 7.16)
[    0.387692] msgmni has been set to 1607
[    0.387912] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.387938] io scheduler noop registered
[    0.387939] io scheduler deadline registered
[    0.387953] io scheduler cfq registered (default)
[    0.388084] pcieport 0000:00:01.0: setting latency timer to 64
[    0.388118] pcieport 0000:00:01.0: irq 40 for MSI/MSI-X
[    0.388169] pcieport 0000:00:1c.0: setting latency timer to 64
[    0.388225] pcieport 0000:00:1c.0: irq 41 for MSI/MSI-X
[    0.388304] pcieport 0000:00:1c.2: setting latency timer to 64
[    0.388359] pcieport 0000:00:1c.2: irq 42 for MSI/MSI-X
[    0.388440] pcieport 0000:00:1c.3: setting latency timer to 64
[    0.388496] pcieport 0000:00:1c.3: irq 43 for MSI/MSI-X
[    0.388595] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.388619] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.388674] intel_idle: MWAIT substates: 0x3122220
[    0.388676] intel_idle: does not run on family 6 model 23
[    0.388966] ACPI: Deprecated procfs I/F for AC is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
[    0.389285] ACPI: AC Adapter [AC0] (on-line)
[    0.389360] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input0
[    0.389378] ACPI: Lid Switch [LID0]
[    0.389420] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1
[    0.389424] ACPI: Power Button [PWRB]
[    0.389465] input: Sleep Button as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input2
[    0.389468] ACPI: Sleep Button [SLPB]
[    0.389524] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input3
[    0.389527] ACPI: Power Button [PWRF]
[    0.389695] ACPI: acpi_idle registered with cpuidle
[    0.400168] Monitor-Mwait will be used to enter C-1 state
[    0.400200] Monitor-Mwait will be used to enter C-3 state
[    0.400208] Marking TSC unstable due to TSC halts in idle
[    0.407587] Freeing initrd memory: 12500k freed
[    0.422123] thermal LNXTHERM:00: registered as thermal_zone0
[    0.422127] ACPI: Thermal Zone [THRM] (57 C)
[    0.422148] ACPI: Deprecated procfs I/F for battery is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
[    0.422211] ERST: Table is not found!
[    0.422346] isapnp: Scanning for PnP cards...
[    0.422361] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    0.467559] ACPI: Battery Slot [BAT0] (battery present)
[    0.776419] isapnp: No Plug & Play device found
[    0.860418] Linux agpgart interface v0.103
[    0.861784] brd: module loaded
[    0.862366] loop: module loaded
[    0.862451] i2c-core: driver [adp5520] using legacy suspend method
[    0.862453] i2c-core: driver [adp5520] using legacy resume method
[    0.862575] ata_piix 0000:00:1f.1: version 2.13
[    0.862588] ata_piix 0000:00:1f.1: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    0.862630] ata_piix 0000:00:1f.1: setting latency timer to 64
[    0.862956] scsi0 : ata_piix
[    0.863047] scsi1 : ata_piix
[    0.863441] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0x18a0 irq 14
[    0.863443] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x18a8 irq 15
[    0.863793] Fixed MDIO Bus: probed
[    0.863825] PPP generic driver version 2.4.2
[    0.863867] tun: Universal TUN/TAP device driver, 1.6
[    0.863869] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.863956] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.863970] ehci_hcd 0000:00:1a.7: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.863981] ehci_hcd 0000:00:1a.7: setting latency timer to 64
[    0.863985] ehci_hcd 0000:00:1a.7: EHCI Host Controller
[    0.864034] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 1
[    0.864087] ehci_hcd 0000:00:1a.7: debug port 1
[    0.867976] ehci_hcd 0000:00:1a.7: cache line size of 64 is not supported
[    0.868012] ehci_hcd 0000:00:1a.7: irq 18, io mem 0xf0404800
[    0.880016] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00
[    0.880134] hub 1-0:1.0: USB hub found
[    0.880138] hub 1-0:1.0: 4 ports detected
[    0.880218] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    0.880231] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    0.880234] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    0.880269] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 2
[    0.880319] ehci_hcd 0000:00:1d.7: debug port 1
[    0.884219] ehci_hcd 0000:00:1d.7: cache line size of 64 is not supported
[    0.884235] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xf0404c00
[    0.900016] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    0.900118] hub 2-0:1.0: USB hub found
[    0.900122] hub 2-0:1.0: 6 ports detected
[    0.900198] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.900210] uhci_hcd: USB Universal Host Controller Interface driver
[    0.900231] uhci_hcd 0000:00:1a.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.900238] uhci_hcd 0000:00:1a.0: setting latency timer to 64
[    0.900241] uhci_hcd 0000:00:1a.0: UHCI Host Controller
[    0.900281] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 3
[    0.900336] uhci_hcd 0000:00:1a.0: irq 16, io base 0x00001800
[    0.900454] hub 3-0:1.0: USB hub found
[    0.900458] hub 3-0:1.0: 2 ports detected
[    0.900533] uhci_hcd 0000:00:1a.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[    0.900539] uhci_hcd 0000:00:1a.1: setting latency timer to 64
[    0.900543] uhci_hcd 0000:00:1a.1: UHCI Host Controller
[    0.900581] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 4
[    0.900634] uhci_hcd 0000:00:1a.1: irq 21, io base 0x00001820
[    0.900750] hub 4-0:1.0: USB hub found
[    0.900753] hub 4-0:1.0: 2 ports detected
[    0.900823] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    0.900829] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    0.900833] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    0.900869] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 5
[    0.904049] uhci_hcd 0000:00:1d.0: irq 23, io base 0x00001840
[    0.904165] hub 5-0:1.0: USB hub found
[    0.904168] hub 5-0:1.0: 2 ports detected
[    0.904232] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    0.904238] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    0.904242] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    0.904278] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 6
[    0.904330] uhci_hcd 0000:00:1d.1: irq 19, io base 0x00001860
[    0.904448] hub 6-0:1.0: USB hub found
[    0.904451] hub 6-0:1.0: 2 ports detected
[    0.904523] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.904530] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    0.904533] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    0.904567] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 7
[    0.904609] uhci_hcd 0000:00:1d.2: irq 18, io base 0x00001880
[    0.904729] hub 7-0:1.0: USB hub found
[    0.904732] hub 7-0:1.0: 2 ports detected
[    0.904854] i8042: PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    0.907075] i8042: Detected active multiplexing controller, rev 1.1
[    0.909411] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.909416] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[    0.909444] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[    0.909469] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[    0.909495] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[    0.909601] mousedev: PS/2 mouse device common for all mice
[    0.909840] rtc_cmos 00:08: rtc core: registered rtc_cmos as rtc0
[    0.909870] rtc0: alarms up to one month, y3k, 242 bytes nvram, hpet irqs
[    0.909946] device-mapper: uevent: version 1.0.3
[    0.910022] device-mapper: ioctl: 4.19.1-ioctl (2011-01-07) initialised: dm-devel@redhat.com
[    0.910085] device-mapper: multipath: version 1.2.0 loaded
[    0.910088] device-mapper: multipath round-robin: version 1.0.0 loaded
[    0.910155] EISA: Probing bus 0 at eisa.0
[    0.910158] EISA: Cannot allocate resource for mainboard
[    0.910160] Cannot allocate resource for EISA slot 1
[    0.910162] Cannot allocate resource for EISA slot 2
[    0.910163] Cannot allocate resource for EISA slot 3
[    0.910165] Cannot allocate resource for EISA slot 4
[    0.910167] Cannot allocate resource for EISA slot 5
[    0.910169] Cannot allocate resource for EISA slot 6
[    0.910170] Cannot allocate resource for EISA slot 7
[    0.910172] Cannot allocate resource for EISA slot 8
[    0.910174] EISA: Detected 0 cards.
[    0.910286] cpuidle: using governor ladder
[    0.910379] cpuidle: using governor menu
[    0.910648] TCP cubic registered
[    0.910772] NET: Registered protocol family 10
[    0.911305] NET: Registered protocol family 17
[    0.911318] Registering the dns_resolver key type
[    0.946023] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input4
[    0.952114] Using IPI No-Shortcut mode
[    0.952194] PM: Hibernation image not present or could not be loaded.
[    0.952205] registered taskstats version 1
[    0.952554]   Magic number: 11:821:332
[    0.952571] tty tty53: hash matches
[    0.952657] rtc_cmos 00:08: setting system clock to 2011-05-01 14:19:11 UTC (1304259551)
[    0.952659] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.952661] EDD information not available.
[    1.039515] Freeing unused kernel memory: 720k freed
[    1.039874] Write protecting the kernel text: 5352k
[    1.039938] Write protecting the kernel read-only data: 2188k
[    1.039939] NX-protecting the kernel data: 4888k
[    1.060814] <30>udev[70]: starting version 167
[    1.114739] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    1.114762] r8169 0000:05:00.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    1.114817] r8169 0000:05:00.0: setting latency timer to 64
[    1.114948] r8169 0000:05:00.0: irq 44 for MSI/MSI-X
[    1.145500] r8169 0000:05:00.0: eth0: RTL8101e at 0xf841c000, 00:03:0d:91:2c:64, XID 94200000 IRQ 44
[    1.155627] ahci 0000:00:1f.2: version 3.0
[    1.155644] ahci 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    1.155704] ahci 0000:00:1f.2: irq 45 for MSI/MSI-X
[    1.155776] ahci 0000:00:1f.2: AHCI 0001.0100 32 slots 3 ports 3 Gbps 0x7 impl SATA mode
[    1.155779] ahci 0000:00:1f.2: flags: 64bit ncq sntf pm led clo pio slum part ccc 
[    1.155785] ahci 0000:00:1f.2: setting latency timer to 64
[    1.165044] scsi2 : ahci
[    1.166644] scsi3 : ahci
[    1.167014] scsi4 : ahci
[    1.167158] ata3: SATA max UDMA/133 abar m2048@0xf0404000 port 0xf0404100 irq 45
[    1.167162] ata4: SATA max UDMA/133 abar m2048@0xf0404000 port 0xf0404180 irq 45
[    1.167166] ata5: SATA max UDMA/133 abar m2048@0xf0404000 port 0xf0404200 irq 45
[    1.396070] usb 5-1: new low speed USB device using uhci_hcd and address 2
[    1.484063] ata3: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    1.484087] ata5: SATA link down (SStatus 0 SControl 300)
[    1.484113] ata4: SATA link down (SStatus 0 SControl 300)
[    1.488160] ata3.00: unexpected _GTF length (8)
[    1.570110] ata3.00: ATA-8: WDC WD3200BEVT-22ZCT0, 11.01A11, max UDMA/133
[    1.570113] ata3.00: 625142448 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
[    1.573194] ata3.00: unexpected _GTF length (8)
[    1.580048] ata3.00: configured for UDMA/133
[    1.580209] scsi 2:0:0:0: Direct-Access     ATA      WDC WD3200BEVT-2 11.0 PQ: 0 ANSI: 5
[    1.580385] sd 2:0:0:0: Attached scsi generic sg0 type 0
[    1.580404] sd 2:0:0:0: [sda] 625142448 512-byte logical blocks: (320 GB/298 GiB)
[    1.580456] sd 2:0:0:0: [sda] Write Protect is off
[    1.580459] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.580481] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.616050]  sda: sda1 sda2 < sda5 >
[    1.616414] sd 2:0:0:0: [sda] Attached SCSI disk
[    1.688157] input: MLK Wireless Desktop as /devices/pci0000:00/0000:00:1d.0/usb5/5-1/5-1:1.0/input/input5
[    1.688301] generic-usb 0003:046A:0101.0001: input,hidraw0: USB HID v1.00 Keyboard [MLK Wireless Desktop] on usb-0000:00:1d.0-1/input0
[    1.714061] input: MLK Wireless Desktop as /devices/pci0000:00/0000:00:1d.0/usb5/5-1/5-1:1.1/input/input6
[    1.714209] generic-usb 0003:046A:0101.0002: input,hiddev0,hidraw1: USB HID v1.00 Mouse [MLK Wireless Desktop] on usb-0000:00:1d.0-1/input1
[    1.714222] usbcore: registered new interface driver usbhid
[    1.714224] usbhid: USB HID core driver
[    2.824524] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)
[   15.781095] Adding 4192252k swap on /dev/sda5.  Priority:-1 extents:1 across:4192252k 
[   18.540758] <30>udev[289]: starting version 167
[   20.177545] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
[   20.780387] type=1400 audit(1304259571.323:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=451 comm="apparmor_parser"
[   20.780397] type=1400 audit(1304259571.323:3): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=471 comm="apparmor_parser"
[   20.781175] type=1400 audit(1304259571.323:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=451 comm="apparmor_parser"
[   20.781188] type=1400 audit(1304259571.323:5): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=471 comm="apparmor_parser"
[   20.781680] type=1400 audit(1304259571.323:6): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=451 comm="apparmor_parser"
[   20.781694] type=1400 audit(1304259571.323:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=471 comm="apparmor_parser"
[   22.016395] lp: driver loaded but no devices found
[   22.511179] lirc_dev: IR Remote Control driver registered, major 250 
[   22.664902] acpi device:04: registered as cooling_device2
[   22.664921] ACPI: Cant attach device
[   22.665016] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:02/LNXVIDEO:00/input/input7
[   22.665075] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[   23.414791] lirc_ite8709: module is from the staging directory, the quality is unknown, you have been warned.
[   23.415576] lirc_ite8709 00:02: lirc_dev: driver lirc_ite8709 registered at minor = 0
[   23.421811] lirc_ite8709: device found : irq=10 io=0x260
[   23.511928] cfg80211: Calling CRDA to update world regulatory domain
[   24.050238] Synaptics Touchpad, model: 1, fw: 6.2, id: 0x1a0b1, caps: 0xa04711/0x200000/0x0
[   24.089527] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio4/input/input8
[   25.400298] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
[   25.400302] Disabling lock debugging due to kernel taint
[   25.505162] [fglrx] Maximum main memory to use for locked dma buffers: 3856 MBytes.
[   25.505721] [fglrx]   vendor: 1002 device: 94c9 count: 1
[   25.506250] [fglrx] ioport: bar 4, base 0x2000, size: 0x100
[   25.506266] pci 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   25.506272] pci 0000:01:00.0: setting latency timer to 64
[   25.506514] [fglrx] Kernel PAT support is enabled
[   25.506532] [fglrx] module loaded - fglrx 8.84.60 [Mar 24 2011] with 1 minors
[   26.064819] cfg80211: World regulatory domain updated:
[   26.064822] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   26.064824] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   26.064827] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   26.064829] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   26.064831] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   26.064833] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   26.136162] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   26.136222] HDA Intel 0000:00:1b.0: irq 46 for MSI/MSI-X
[   26.136253] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   26.550393] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, in-tree:s
[   26.550396] iwl3945: Copyright(c) 2003-2010 Intel Corporation
[   26.550467] iwl3945 0000:04:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[   26.550481] iwl3945 0000:04:00.0: setting latency timer to 64
[   26.605379] iwl3945 0000:04:00.0: Tunable channels: 13 802.11bg, 23 802.11a channels
[   26.605382] iwl3945 0000:04:00.0: Detected Intel Wireless WiFi Link 3945ABG
[   26.605526] iwl3945 0000:04:00.0: irq 47 for MSI/MSI-X
[   26.605723] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain 
[   26.868978] hda_codec: ALC883: SKU not ready 0x598301f0
[   26.890103] input: HDA Intel Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card0/input9
[   27.542621] ieee80211 phy0: Selected rate control algorithm 'iwl-3945-rs'
[   29.506869] type=1400 audit(1304259580.047:8): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=739 comm="apparmor_parser"
[   29.507607] type=1400 audit(1304259580.047:9): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=739 comm="apparmor_parser"
[   29.508200] type=1400 audit(1304259580.051:10): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=739 comm="apparmor_parser"
[   29.928171] type=1400 audit(1304259580.471:11): apparmor="STATUS" operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" pid=738 comm="apparmor_parser"
[   31.181404] type=1400 audit(1304259581.723:12): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=742 comm="apparmor_parser"
[   31.182324] type=1400 audit(1304259581.723:13): apparmor="STATUS" operation="profile_load" name="/usr/sbin/cupsd" pid=742 comm="apparmor_parser"
[   31.401460] vesafb: framebuffer at 0xd0000000, mapped to 0xf9c80000, using 3072k, total 3072k
[   31.401463] vesafb: mode is 1024x768x32, linelength=4096, pages=0
[   31.401465] vesafb: scrolling: redraw
[   31.401468] vesafb: Truecolor: size=0:8:8:8, shift=0:16:8:0
[   31.401617] Console: switching to colour frame buffer device 128x48
[   31.401639] fb0: VESA VGA frame buffer device
[   31.458523] type=1400 audit(1304259581.999:14): apparmor="STATUS" operation="profile_load" name="/usr/sbin/tcpdump" pid=756 comm="apparmor_parser"
[   31.826664] type=1400 audit(1304259582.367:15): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince" pid=740 comm="apparmor_parser"
[   31.837399] type=1400 audit(1304259582.379:16): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince-previewer" pid=740 comm="apparmor_parser"
[   31.843293] type=1400 audit(1304259582.383:17): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince-thumbnailer" pid=740 comm="apparmor_parser"
[   33.139020] ppdev: user-space parallel port driver
[   41.072568] iwl3945 0000:04:00.0: loaded firmware version 15.32.2.9
[   41.176300] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   41.191603] r8169 0000:05:00.0: eth0: link down
[   41.191761] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   42.737828] cfg80211: Found new beacon on frequency: 2472 MHz (Ch 13) on phy0
[   46.615267] fglrx_pci 0000:01:00.0: irq 48 for MSI/MSI-X
[   46.615944] [fglrx] Firegl kernel thread PID: 1059
[   46.615999] [fglrx] Firegl kernel thread PID: 1060
[   46.616147] [fglrx] Firegl kernel thread PID: 1061
[   46.616393] [fglrx] IRQ 48 Enabled
[   47.122911] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=0
[   48.262310] [fglrx] Gart USWC size:1256 M.
[   48.262314] [fglrx] Gart cacheable size:498 M.
[   48.262318] [fglrx] Reserved FB block: Shared offset:0, size:1000000 
[   48.262320] [fglrx] Reserved FB block: Unshared offset:fc0d000, size:3ef000 
[   48.262322] [fglrx] Reserved FB block: Unshared offset:fffc000, size:4000 
[   66.583566] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=0
[   95.639365] wlan0: authenticate with 40:4a:03:00:16:94 (try 1)
[   95.641151] wlan0: authenticated
[   95.642103] wlan0: associate with 40:4a:03:00:16:94 (try 1)
[   95.645178] wlan0: RX AssocResp from 40:4a:03:00:16:94 (capab=0xc31 status=0 aid=2)
[   95.645182] wlan0: associated
[   95.646733] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   98.366853] iwl3945 0000:04:00.0: Queue 4 stuck for 2000 ms.
[   98.366857] iwl3945 0000:04:00.0: On demand firmware reload
[   98.368174] psmouse.c: TouchPad at isa0060/serio4/input0 lost synchronization, throwing 1 bytes away.
[   98.938000] Intel AES-NI instructions are not detected.
[   99.157433] padlock_aes: VIA PadLock not detected.
[  108.384066] wlan0: no IPv6 routers present
[  313.144172] usb 5-1: USB disconnect, address 2
[ 1098.396657] iwl3945 0000:04:00.0: Microcode SW error detected. Restarting 0x82000008.
[ 1098.396669] iwl3945 0000:04:00.0: Loaded firmware version: 15.32.2.9
[ 1098.396707] iwl3945 0000:04:00.0: Start IWL Error Log Dump:
[ 1098.396715] iwl3945 0000:04:00.0: Status: 0x000202E4, count: 1
[ 1098.396721] iwl3945 0000:04:00.0: Desc       Time       asrtPC  blink2 ilink1  nmiPC   Line
[ 1098.396956] iwl3945 0000:04:00.0: UNKNOWN       (0x13) 1748293617 0x008B6 0x00274 0x00320 0x0092C 112
[ 1098.396960] 
[ 1098.397094] iwl3945 0000:04:00.0: Start IWL Event Log Dump: display last 20 count
[ 1098.397141] iwl3945 0000:04:00.0: 1748092069	0x00000000	0502
[ 1098.397169] iwl3945 0000:04:00.0: 1748093565	0x000000c3	0310
[ 1098.397196] iwl3945 0000:04:00.0: 1748093566	0x00000000	0314
[ 1098.397223] iwl3945 0000:04:00.0: 1748093568	0x0000031a	0501
[ 1098.397250] iwl3945 0000:04:00.0: 1748093572	0x000003fc	0504
[ 1098.397277] iwl3945 0000:04:00.0: 1748093573	0x6831ca82	0503
[ 1098.397305] iwl3945 0000:04:00.0: 1748093573	0x00000005	0503
[ 1098.397332] iwl3945 0000:04:00.0: 1748093574	0x8400957e	0503
[ 1098.397359] iwl3945 0000:04:00.0: 1748093575	0x6831ca82	0503
[ 1098.397386] iwl3945 0000:04:00.0: 1748093575	0x00000005	0503
[ 1098.397413] iwl3945 0000:04:00.0: 1748093576	0x8400957e	0503
[ 1098.397439] iwl3945 0000:04:00.0: 1748093578	0x84009576	0500
[ 1098.397466] iwl3945 0000:04:00.0: 1748093580	0x84009576	0600
[ 1098.397493] iwl3945 0000:04:00.0: 1748093580	0x00000000	0600
[ 1098.397519] iwl3945 0000:04:00.0: 1748093590	0x000000a2	0600
[ 1098.397546] iwl3945 0000:04:00.0: 1748093596	0x00000004	0631
[ 1098.397573] iwl3945 0000:04:00.0: 1748093608	0x85000190	0630
[ 1098.397600] iwl3945 0000:04:00.0: 1748093609	0x86008c78	0630
[ 1098.397627] iwl3945 0000:04:00.0: 1748293615	0x00000002	0123
[ 1098.397654] iwl3945 0000:04:00.0: 1748293618	0x00000100	0125
[ 1098.403794] iwl3945 0000:04:00.0: Can't stop Rx DMA.
[ 1104.104170] usb 2-1: new high speed USB device using ehci_hcd and address 3
[ 1104.473669] usbcore: registered new interface driver uas
[ 1104.764783] Initializing USB Mass Storage driver...
[ 1104.764901] scsi5 : usb-storage 2-1:1.0
[ 1104.765006] usbcore: registered new interface driver usb-storage
[ 1104.765008] USB Mass Storage support registered.
[ 1106.252189] scsi 5:0:0:0: Direct-Access     Corsair  Flash Voyager    1100 PQ: 0 ANSI: 0 CCS
[ 1106.253725] sd 5:0:0:0: Attached scsi generic sg1 type 0
[ 1106.257334] sd 5:0:0:0: [sdb] 15794176 512-byte logical blocks: (8.08 GB/7.53 GiB)
[ 1106.258194] sd 5:0:0:0: [sdb] Write Protect is off
[ 1106.258204] sd 5:0:0:0: [sdb] Mode Sense: 43 00 00 00
[ 1106.259686] sd 5:0:0:0: [sdb] No Caching mode page present
[ 1106.259694] sd 5:0:0:0: [sdb] Assuming drive cache: write through
[ 1106.264719] sd 5:0:0:0: [sdb] No Caching mode page present
[ 1106.264728] sd 5:0:0:0: [sdb] Assuming drive cache: write through
[ 1106.265881]  sdb: sdb1
[ 1106.268458] sd 5:0:0:0: [sdb] No Caching mode page present
[ 1106.268467] sd 5:0:0:0: [sdb] Assuming drive cache: write through
[ 1106.268474] sd 5:0:0:0: [sdb] Attached SCSI removable disk


```

from fstab
```

# <file system> <mount point>             <type>          <options>                    <dump> <pass>
/dev/root       /                         rootfs          defaults                          0 1
none            /proc                     proc            nodev,noexec,nosuid               0 0
none            /proc/sys/fs/binfmt_misc  binfmt_misc     nodev,noexec,nosuid,optional      0 0
none            /sys                      sysfs           nodev,noexec,nosuid               0 0
none            /sys/fs/fuse/connections  fusectl         optional                          0 0
none            /sys/kernel/debug         debugfs         optional                          0 0
none            /sys/kernel/security      securityfs      optional                          0 0
none            /spu                      spufs           gid=spu,optional                  0 0
none            /dev                      devtmpfs,tmpfs  mode=0755                         0 0
none            /dev/pts                  devpts          noexec,nosuid,gid=tty,mode=0620   0 0
none            /dev/shm                  tmpfs           nosuid,nodev                      0 0
none            /tmp                      none            defaults                          0 0
none            /var/run                  tmpfs           mode=0755,nosuid,showthrough      0 0
none            /var/lock                 tmpfs           nodev,noexec,nosuid,showthrough   0 0
none            /lib/init/rw              tmpfs           mode=0755,nosuid,optional         0 0

```
and from ls -lah /dev/
```

drwxr-xr-x  19 root root        4.1K 2011-05-01 16:19 .
drwxr-xr-x  22 root root        4.0K 2011-05-01 15:24 ..
drwxr-xr-x   2 root root          60 2011-05-01 16:19 ati
crw-------   1 root root     10, 235 2011-05-01 16:19 autofs
drwxr-xr-x   2 root root         600 2011-05-01 16:19 block
drwxr-xr-x   2 root root          60 2011-05-01 16:19 bsg
crw-------   1 root root     10, 234 2011-05-01 16:19 btrfs-control
drwxr-xr-x   3 root root          60 2011-05-01 16:19 bus
drwxr-xr-x   2 root root        3.7K 2011-05-01 16:19 char
crw-------   1 root root      5,   1 2011-05-01 16:19 console
lrwxrwxrwx   1 root root          11 2011-05-01 16:19 core -> /proc/kcore
drwxr-xr-x   2 root root          60 2011-05-01 16:19 cpu
crw-------   1 root root     10,  59 2011-05-01 16:19 cpu_dma_latency
drwxr-xr-x   5 root root         100 2011-05-01 16:19 disk
crw-------   1 root root     10,  61 2011-05-01 16:19 ecryptfs
crw-rw----   1 root video    29,   0 2011-05-01 16:19 fb0
lrwxrwxrwx   1 root root          13 2011-05-01 16:19 fd -> /proc/self/fd
crw-rw-rw-   1 root root      1,   7 2011-05-01 16:19 full
crw-rw-rw-   1 root fuse     10, 229 2011-05-01 16:19 fuse
crw-------   1 root root    251,   0 2011-05-01 16:19 hidraw0
crw-------   1 root root    251,   1 2011-05-01 16:19 hidraw1
crw-------   1 root root     10, 228 2011-05-01 16:19 hpet
drwxr-xr-x   2 root root          40 2011-05-01 16:19 .initramfs
-rw-r--r--   1 root root           0 2011-05-01 16:19 .initramfs-tools
drwxr-xr-x   4 root root         340 2011-05-01 16:19 input
crw-------   1 root root      1,  11 2011-05-01 16:19 kmsg
crw-------   1 root root    250,   0 2011-05-01 16:19 lirc0
srw-rw-rw-   1 root root           0 2011-05-01 16:19 log
brw-rw----   1 root disk      7,   0 2011-05-01 16:19 loop0
brw-rw----   1 root disk      7,   1 2011-05-01 16:19 loop1
brw-rw----   1 root disk      7,   2 2011-05-01 16:19 loop2
brw-rw----   1 root disk      7,   3 2011-05-01 16:19 loop3
brw-rw----   1 root disk      7,   4 2011-05-01 16:19 loop4
brw-rw----   1 root disk      7,   5 2011-05-01 16:19 loop5
brw-rw----   1 root disk      7,   6 2011-05-01 16:19 loop6
brw-rw----   1 root disk      7,   7 2011-05-01 16:19 loop7
drwxr-xr-x   2 root root          60 2011-05-01 16:19 mapper
crw-------   1 root root     10, 227 2011-05-01 16:19 mcelog
crw-r-----   1 root kmem      1,   1 2011-05-01 16:19 mem
drwxr-xr-x   2 root root          60 2011-04-26 00:51 net
crw-------   1 root root     10,  58 2011-05-01 16:19 network_latency
crw-------   1 root root     10,  57 2011-05-01 16:19 network_throughput
crw-rw-rw-   1 root root      1,   3 2011-05-01 16:19 null
crw-------   1 root root      1,  12 2011-05-01 16:19 oldmem
drwxr-xr-x   2 root root          60 2011-05-01 16:19 pktcdvd
crw-r-----   1 root kmem      1,   4 2011-05-01 16:19 port
crw-------   1 root root    108,   0 2011-05-01 16:19 ppp
crw-------   1 root root     10,   1 2011-05-01 16:19 psaux
crw-rw-rw-   1 root tty       5,   2 2011-05-01 16:23 ptmx
drwxr-xr-x   2 root root           0 2011-04-07 14:43 pts
brw-rw----   1 root disk      1,   0 2011-05-01 16:19 ram0
brw-rw----   1 root disk      1,   1 2011-05-01 16:19 ram1
brw-rw----   1 root disk      1,  10 2011-05-01 16:19 ram10
brw-rw----   1 root disk      1,  11 2011-05-01 16:19 ram11
brw-rw----   1 root disk      1,  12 2011-05-01 16:19 ram12
brw-rw----   1 root disk      1,  13 2011-05-01 16:19 ram13
brw-rw----   1 root disk      1,  14 2011-05-01 16:19 ram14
brw-rw----   1 root disk      1,  15 2011-05-01 16:19 ram15
brw-rw----   1 root disk      1,   2 2011-05-01 16:19 ram2
brw-rw----   1 root disk      1,   3 2011-05-01 16:19 ram3
brw-rw----   1 root disk      1,   4 2011-05-01 16:19 ram4
brw-rw----   1 root disk      1,   5 2011-05-01 16:19 ram5
brw-rw----   1 root disk      1,   6 2011-05-01 16:19 ram6
brw-rw----   1 root disk      1,   7 2011-05-01 16:19 ram7
brw-rw----   1 root disk      1,   8 2011-05-01 16:19 ram8
brw-rw----   1 root disk      1,   9 2011-05-01 16:19 ram9
crw-rw-rw-   1 root root      1,   8 2011-05-01 16:19 random
crw-rw-r--+  1 root root     10,  62 2011-05-01 16:19 rfkill
lrwxrwxrwx   1 root root           4 2011-05-01 16:19 root -> sda1
lrwxrwxrwx   1 root root           4 2011-05-01 16:19 rtc -> rtc0
crw-------   1 root root    254,   0 2011-05-01 16:19 rtc0
brw-rw----   1 root disk      8,   0 2011-05-01 16:19 sda
brw-rw----   1 root disk      8,   1 2011-05-01 16:19 sda1
brw-rw----   1 root disk      8,   2 2011-05-01 16:19 sda2
brw-rw----   1 root disk      8,   5 2011-05-01 16:19 sda5
crw-rw----   1 root disk     21,   0 2011-05-01 16:19 sg0
drwxrwxrwt   2 root root         120 2011-05-01 16:20 shm
crw-------   1 root root     10, 231 2011-05-01 16:19 snapshot
drwxr-xr-x   3 root root         280 2011-05-01 16:19 snd
lrwxrwxrwx   1 root root          15 2011-05-01 16:19 stderr -> /proc/self/fd/2
lrwxrwxrwx   1 root root          15 2011-05-01 16:19 stdin -> /proc/self/fd/0
lrwxrwxrwx   1 root root          15 2011-05-01 16:19 stdout -> /proc/self/fd/1
crw-rw-rw-   1 root tty       5,   0 2011-05-01 16:22 tty
crw--w----   1 root tty       4,   0 2011-05-01 16:19 tty0
crw-------   1 root root      4,   1 2011-05-01 16:19 tty1
crw--w----   1 root tty       4,  10 2011-05-01 16:19 tty10
crw--w----   1 root tty       4,  11 2011-05-01 16:19 tty11
crw--w----   1 root tty       4,  12 2011-05-01 16:19 tty12
crw--w----   1 root tty       4,  13 2011-05-01 16:19 tty13
crw--w----   1 root tty       4,  14 2011-05-01 16:19 tty14
crw--w----   1 root tty       4,  15 2011-05-01 16:19 tty15
crw--w----   1 root tty       4,  16 2011-05-01 16:19 tty16
crw--w----   1 root tty       4,  17 2011-05-01 16:19 tty17
crw--w----   1 root tty       4,  18 2011-05-01 16:19 tty18
crw--w----   1 root tty       4,  19 2011-05-01 16:19 tty19
crw-------   1 root root      4,   2 2011-05-01 16:19 tty2
crw--w----   1 root tty       4,  20 2011-05-01 16:19 tty20
crw--w----   1 root tty       4,  21 2011-05-01 16:19 tty21
crw--w----   1 root tty       4,  22 2011-05-01 16:19 tty22
crw--w----   1 root tty       4,  23 2011-05-01 16:19 tty23
crw--w----   1 root tty       4,  24 2011-05-01 16:19 tty24
crw--w----   1 root tty       4,  25 2011-05-01 16:19 tty25
crw--w----   1 root tty       4,  26 2011-05-01 16:19 tty26
crw--w----   1 root tty       4,  27 2011-05-01 16:19 tty27
crw--w----   1 root tty       4,  28 2011-05-01 16:19 tty28
crw--w----   1 root tty       4,  29 2011-05-01 16:19 tty29
crw-------   1 root root      4,   3 2011-05-01 16:19 tty3
crw--w----   1 root tty       4,  30 2011-05-01 16:19 tty30
crw--w----   1 root tty       4,  31 2011-05-01 16:19 tty31
crw--w----   1 root tty       4,  32 2011-05-01 16:19 tty32
crw--w----   1 root tty       4,  33 2011-05-01 16:19 tty33
crw--w----   1 root tty       4,  34 2011-05-01 16:19 tty34
crw--w----   1 root tty       4,  35 2011-05-01 16:19 tty35
crw--w----   1 root tty       4,  36 2011-05-01 16:19 tty36
crw--w----   1 root tty       4,  37 2011-05-01 16:19 tty37
crw--w----   1 root tty       4,  38 2011-05-01 16:19 tty38
crw--w----   1 root tty       4,  39 2011-05-01 16:19 tty39
crw-------   1 root root      4,   4 2011-05-01 16:19 tty4
crw--w----   1 root tty       4,  40 2011-05-01 16:19 tty40
crw--w----   1 root tty       4,  41 2011-05-01 16:19 tty41
crw--w----   1 root tty       4,  42 2011-05-01 16:19 tty42
crw--w----   1 root tty       4,  43 2011-05-01 16:19 tty43
crw--w----   1 root tty       4,  44 2011-05-01 16:19 tty44
crw--w----   1 root tty       4,  45 2011-05-01 16:19 tty45
crw--w----   1 root tty       4,  46 2011-05-01 16:19 tty46
crw--w----   1 root tty       4,  47 2011-05-01 16:19 tty47
crw--w----   1 root tty       4,  48 2011-05-01 16:19 tty48
crw--w----   1 root tty       4,  49 2011-05-01 16:19 tty49
crw-------   1 root root      4,   5 2011-05-01 16:19 tty5
crw--w----   1 root tty       4,  50 2011-05-01 16:19 tty50
crw--w----   1 root tty       4,  51 2011-05-01 16:19 tty51
crw--w----   1 root tty       4,  52 2011-05-01 16:19 tty52
crw--w----   1 root tty       4,  53 2011-05-01 16:19 tty53
crw--w----   1 root tty       4,  54 2011-05-01 16:19 tty54
crw--w----   1 root tty       4,  55 2011-05-01 16:19 tty55
crw--w----   1 root tty       4,  56 2011-05-01 16:19 tty56
crw--w----   1 root tty       4,  57 2011-05-01 16:19 tty57
crw--w----   1 root tty       4,  58 2011-05-01 16:19 tty58
crw--w----   1 root tty       4,  59 2011-05-01 16:19 tty59
crw-------   1 root root      4,   6 2011-05-01 16:19 tty6
crw--w----   1 root tty       4,  60 2011-05-01 16:19 tty60
crw--w----   1 root tty       4,  61 2011-05-01 16:19 tty61
crw--w----   1 root tty       4,  62 2011-05-01 16:19 tty62
crw--w----   1 root tty       4,  63 2011-05-01 16:19 tty63
crw--w----   1 root tty       4,   7 2011-05-01 16:19 tty7
crw--w----   1 root tty       4,   8 2011-05-01 16:19 tty8
crw--w----   1 root tty       4,   9 2011-05-01 16:19 tty9
crw-------   1 root root      5,   3 2011-05-01 16:19 ttyprintk
crw-rw----   1 root dialout   4,  64 2011-05-01 16:19 ttyS0
crw-rw----   1 root dialout   4,  65 2011-05-01 16:19 ttyS1
crw-rw----   1 root dialout   4,  74 2011-05-01 16:19 ttyS10
crw-rw----   1 root dialout   4,  75 2011-05-01 16:19 ttyS11
crw-rw----   1 root dialout   4,  76 2011-05-01 16:19 ttyS12
crw-rw----   1 root dialout   4,  77 2011-05-01 16:19 ttyS13
crw-rw----   1 root dialout   4,  78 2011-05-01 16:19 ttyS14
crw-rw----   1 root dialout   4,  79 2011-05-01 16:19 ttyS15
crw-rw----   1 root dialout   4,  80 2011-05-01 16:19 ttyS16
crw-rw----   1 root dialout   4,  81 2011-05-01 16:19 ttyS17
crw-rw----   1 root dialout   4,  82 2011-05-01 16:19 ttyS18
crw-rw----   1 root dialout   4,  83 2011-05-01 16:19 ttyS19
crw-rw----   1 root dialout   4,  66 2011-05-01 16:19 ttyS2
crw-rw----   1 root dialout   4,  84 2011-05-01 16:19 ttyS20
crw-rw----   1 root dialout   4,  85 2011-05-01 16:19 ttyS21
crw-rw----   1 root dialout   4,  86 2011-05-01 16:19 ttyS22
crw-rw----   1 root dialout   4,  87 2011-05-01 16:19 ttyS23
crw-rw----   1 root dialout   4,  88 2011-05-01 16:19 ttyS24
crw-rw----   1 root dialout   4,  89 2011-05-01 16:19 ttyS25
crw-rw----   1 root dialout   4,  90 2011-05-01 16:19 ttyS26
crw-rw----   1 root dialout   4,  91 2011-05-01 16:19 ttyS27
crw-rw----   1 root dialout   4,  92 2011-05-01 16:19 ttyS28
crw-rw----   1 root dialout   4,  93 2011-05-01 16:19 ttyS29
crw-rw----   1 root dialout   4,  67 2011-05-01 16:19 ttyS3
crw-rw----   1 root dialout   4,  94 2011-05-01 16:19 ttyS30
crw-rw----   1 root dialout   4,  95 2011-05-01 16:19 ttyS31
crw-rw----   1 root dialout   4,  68 2011-05-01 16:19 ttyS4
crw-rw----   1 root dialout   4,  69 2011-05-01 16:19 ttyS5
crw-rw----   1 root dialout   4,  70 2011-05-01 16:19 ttyS6
crw-rw----   1 root dialout   4,  71 2011-05-01 16:19 ttyS7
crw-rw----   1 root dialout   4,  72 2011-05-01 16:19 ttyS8
crw-rw----   1 root dialout   4,  73 2011-05-01 16:19 ttyS9
drwxr-xr-x   7 root root         160 2011-05-01 16:19 .udev
crw-r-----   1 root root     10, 223 2011-05-01 16:19 uinput
crw-rw-rw-   1 root root      1,   9 2011-05-01 16:19 urandom
drwxr-xr-x   2 root root          60 2011-05-01 16:19 usb
crw-------   1 root root    252,   0 2011-05-01 16:19 usbmon0
crw-------   1 root root    252,   1 2011-05-01 16:19 usbmon1
crw-------   1 root root    252,   2 2011-05-01 16:19 usbmon2
crw-------   1 root root    252,   3 2011-05-01 16:19 usbmon3
crw-------   1 root root    252,   4 2011-05-01 16:19 usbmon4
crw-------   1 root root    252,   5 2011-05-01 16:19 usbmon5
crw-------   1 root root    252,   6 2011-05-01 16:19 usbmon6
crw-------   1 root root    252,   7 2011-05-01 16:19 usbmon7
crw-rw----   1 root tty       7,   0 2011-05-01 16:19 vcs
crw-rw----   1 root tty       7,   1 2011-05-01 16:19 vcs1
crw-rw----   1 root tty       7,   2 2011-05-01 16:19 vcs2
crw-rw----   1 root tty       7,   3 2011-05-01 16:19 vcs3
crw-rw----   1 root tty       7,   4 2011-05-01 16:19 vcs4
crw-rw----   1 root tty       7,   5 2011-05-01 16:19 vcs5
crw-rw----   1 root tty       7,   6 2011-05-01 16:19 vcs6
crw-rw----   1 root tty       7, 128 2011-05-01 16:19 vcsa
crw-rw----   1 root tty       7, 129 2011-05-01 16:19 vcsa1
crw-rw----   1 root tty       7, 130 2011-05-01 16:19 vcsa2
crw-rw----   1 root tty       7, 131 2011-05-01 16:19 vcsa3
crw-rw----   1 root tty       7, 132 2011-05-01 16:19 vcsa4
crw-rw----   1 root tty       7, 133 2011-05-01 16:19 vcsa5
crw-rw----   1 root tty       7, 134 2011-05-01 16:19 vcsa6
crw-------   1 root root     10,  63 2011-05-01 16:19 vga_arbiter
crw-rw-rw-   1 root root      1,   5 2011-05-01 16:19 zero


```

---

### Post by Althippie on 2011-05-02
need help

---

### Post by Althippie on 2011-05-06
:-(

---

