---
title: "USB DAC not detected at all"
date: 2016-11-02
forum: Hardware
---

### Post by tbone3421 on 2016-11-02
Hi,

I've been happily using my USB DAC for a long time, and recently it stopped working possibly after an Ubuntu update, but I'm not certain.  It is a Schitt Modi DAC, and has previously been detected.  
When I run  aplay -l, I get:
```
**** List of PLAYBACK Hardware Devices ****
card 0: PCH [HDA Intel PCH], device 0: 92HD73E1X5 Analog [92HD73E1X5 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: PCH [HDA Intel PCH], device 1: 92HD73E1X5 Digital [92HD73E1X5 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: HDMI [HDA ATI HDMI], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #

It is not detected.   I also tried looking for it with lsusb, which yields:
lsusb
Bus 002 Device 003: ID 0461:4dd6 Primax Electronics, Ltd 
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 005: ID 0a5c:217d Broadcom Corp. HP Bluethunder
Bus 001 Device 003: ID 058f:6362 Alcor Micro Corp. Flash Card Reader/Writer
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 003: ID 04d9:0169 Holtek Semiconductor, Inc. 
Bus 003 Device 002: ID 1058:1110 Western Digital Technologies, Inc. My Book Essential (WDBAAF), My Book for Mac (WDBAAG)
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

Still nothing showing up.   So I tried looking into dmesg, though I don't really know how to interpret the output.   Anyone have any idea why my USB DAC isn't recognized at all?  Perhaps I'm missing some driver or package?   Here is the dmesg output below.  Thanks for any insights!
dmesg
[    0.000000] microcode: CPU0 microcode updated early to revision 0x29, date = 2013-06-12
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Initializing cgroup subsys cpuacct
[    0.000000] Linux version 4.4.0-45-generic (buildd@lgw01-34) (gcc version 5.4.0 20160609 (Ubuntu 5.4.0-6ubuntu1~16.04.2) ) #66-Ubuntu SMP Wed Oct 19 14:12:37 UTC 2016 (Ubuntu 4.4.0-45.66-generic 4.4.21)
[    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-4.4.0-45-generic.efi.signed root=UUID=e40db2de-5153-4289-9e96-ea2791382804 ro quiet splash vt.handoff=7
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   Centaur CentaurHauls
[    0.000000] x86/fpu: xstate_offset[2]:  576, xstate_sizes[2]:  256
[    0.000000] x86/fpu: Supporting XSAVE feature 0x01: 'x87 floating point registers'
[    0.000000] x86/fpu: Supporting XSAVE feature 0x02: 'SSE registers'
[    0.000000] x86/fpu: Supporting XSAVE feature 0x04: 'AVX registers'
[    0.000000] x86/fpu: Enabled xstate features 0x7, context size is 832 bytes, using 'standard' format.
[    0.000000] x86/fpu: Using 'eager' FPU context switches.
[    0.000000] e820: BIOS-provided physical RAM map:
[    0.000000] BIOS-e820: [mem 0x0000000000000000-0x000000000009efff] usable
[    0.000000] BIOS-e820: [mem 0x000000000009f000-0x000000000009ffff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000000100000-0x00000000dda07fff] usable
[    0.000000] BIOS-e820: [mem 0x00000000dda08000-0x00000000ddbadfff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000ddbae000-0x00000000ddbb9fff] ACPI data
[    0.000000] BIOS-e820: [mem 0x00000000ddbba000-0x00000000ddc15fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000ddc16000-0x00000000ddc1bfff] ACPI data
[    0.000000] BIOS-e820: [mem 0x00000000ddc1c000-0x00000000ddc9efff] usable
[    0.000000] BIOS-e820: [mem 0x00000000ddc9f000-0x00000000ddd36fff] ACPI NVS
[    0.000000] BIOS-e820: [mem 0x00000000ddd37000-0x00000000de120fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000de121000-0x00000000de1e8fff] type 20
[    0.000000] BIOS-e820: [mem 0x00000000de1e9000-0x00000000de1e9fff] usable
[    0.000000] BIOS-e820: [mem 0x00000000de1ea000-0x00000000de22cfff] ACPI NVS
[    0.000000] BIOS-e820: [mem 0x00000000de22d000-0x00000000ded5cfff] usable
[    0.000000] BIOS-e820: [mem 0x00000000ded5d000-0x00000000deff1fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000deff2000-0x00000000deffffff] usable
[    0.000000] BIOS-e820: [mem 0x00000000f8000000-0x00000000fbffffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fec00000-0x00000000fec00fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fed00000-0x00000000fed03fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fed1c000-0x00000000fed1ffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fee00000-0x00000000fee00fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000ff000000-0x00000000ffffffff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000100000000-0x000000031effffff] usable
[    0.000000] NX (Execute Disable) protection: active
[    0.000000] efi: EFI v2.31 by American Megatrends
[    0.000000] efi:  ACPI=0xddbae000  ACPI 2.0=0xddbae000  SMBIOS=0xf0480  MPS=0xfc960 
[    0.000000] SMBIOS 2.7 present.
[    0.000000] DMI: Hewlett-Packard h8-1250/2AD5, BIOS 7.15 07/02/2012
[    0.000000] e820: update [mem 0x00000000-0x00000fff] usable ==> reserved
[    0.000000] e820: remove [mem 0x000a0000-0x000fffff] usable
[    0.000000] e820: last_pfn = 0x31f000 max_arch_pfn = 0x400000000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-DBFFF write-protect
[    0.000000]   DC000-DFFFF uncachable
[    0.000000]   E0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000 mask E00000000 write-back
[    0.000000]   1 base 200000000 mask F00000000 write-back
[    0.000000]   2 base 300000000 mask FF0000000 write-back
[    0.000000]   3 base 310000000 mask FF8000000 write-back
[    0.000000]   4 base 318000000 mask FFC000000 write-back
[    0.000000]   5 base 31C000000 mask FFE000000 write-back
[    0.000000]   6 base 31E000000 mask FFF000000 write-back
[    0.000000]   7 base 0E0000000 mask FE0000000 uncachable
[    0.000000]   8 disabled
[    0.000000]   9 disabled
[    0.000000] x86/PAT: Configuration [0-7]: WB  WC  UC- UC  WB  WC  UC- WT  
[    0.000000] original variable MTRRs
[    0.000000] reg 0, base: 0GB, range: 8GB, type WB
[    0.000000] reg 1, base: 8GB, range: 4GB, type WB
[    0.000000] reg 2, base: 12GB, range: 256MB, type WB
[    0.000000] reg 3, base: 12544MB, range: 128MB, type WB
[    0.000000] reg 4, base: 12672MB, range: 64MB, type WB
[    0.000000] reg 5, base: 12736MB, range: 32MB, type WB
[    0.000000] reg 6, base: 12768MB, range: 16MB, type WB
[    0.000000] reg 7, base: 3584MB, range: 512MB, type UC
[    0.000000] total RAM covered: 12272M
[    0.000000] Found optimal setting for mtrr clean up
[    0.000000]  gran_size: 64K 	chunk_size: 32M 	num_reg: 7  	lose cover RAM: 0G
[    0.000000] New variable MTRRs
[    0.000000] reg 0, base: 0GB, range: 2GB, type WB
[    0.000000] reg 1, base: 2GB, range: 1GB, type WB
[    0.000000] reg 2, base: 3GB, range: 512MB, type WB
[    0.000000] reg 3, base: 4GB, range: 4GB, type WB
[    0.000000] reg 4, base: 8GB, range: 4GB, type WB
[    0.000000] reg 5, base: 12GB, range: 512MB, type WB
[    0.000000] reg 6, base: 12784MB, range: 16MB, type UC
[    0.000000] e820: update [mem 0xe0000000-0xffffffff] usable ==> reserved
[    0.000000] e820: last_pfn = 0xdf000 max_arch_pfn = 0x400000000
[    0.000000] found SMP MP-table at [mem 0x000fcc70-0x000fcc7f] mapped at [ffff8800000fcc70]
[    0.000000] Scanning 1 areas for low memory corruption
[    0.000000] Base memory trampoline at [ffff880000097000] 97000 size 24576
[    0.000000] BRK [0x02201000, 0x02201fff] PGTABLE
[    0.000000] BRK [0x02202000, 0x02202fff] PGTABLE
[    0.000000] BRK [0x02203000, 0x02203fff] PGTABLE
[    0.000000] BRK [0x02204000, 0x02204fff] PGTABLE
[    0.000000] BRK [0x02205000, 0x02205fff] PGTABLE
[    0.000000] BRK [0x02206000, 0x02206fff] PGTABLE
[    0.000000] RAMDISK: [mem 0x337ba000-0x35bd4fff]
[    0.000000] ACPI: Early table checksum verification disabled
[    0.000000] ACPI: RSDP 0x00000000DDBAE000 000024 (v02 HPQOEM)
[    0.000000] ACPI: XSDT 0x00000000DDBAE080 00007C (v01 HPQOEM SLIC-CPC 01072009 AMI  00010013)
[    0.000000] ACPI: FACP 0x00000000DDBB7720 0000F4 (v04 HPQOEM SLIC-CPC 01072009 AMI  00010013)
[    0.000000] ACPI: DSDT 0x00000000DDBAE188 009597 (v02 HPQOEM SLIC-CPC 00000000 INTL 20051117)
[    0.000000] ACPI: FACS 0x00000000DDD35F80 000040
[    0.000000] ACPI: APIC 0x00000000DDBB7818 000092 (v03 HPQOEM SLIC-CPC 01072009 AMI  00010013)
[    0.000000] ACPI: FPDT 0x00000000DDBB78B0 000044 (v01 HPQOEM SLIC-CPC 01072009 AMI  00010013)
[    0.000000] ACPI: MCFG 0x00000000DDBB78F8 00003C (v01 HPQOEM SLIC-CPC 01072009 MSFT 00000097)
[    0.000000] ACPI: SLIC 0x00000000DDBB7938 000176 (v01 HPQOEM SLIC-CPC 01072009 AMI  00010013)
[    0.000000] ACPI: HPET 0x00000000DDBB7AB0 000038 (v01 HPQOEM SLIC-CPC 01072009 AMI. 00000005)
[    0.000000] ACPI: SSDT 0x00000000DDBB7AE8 00036D (v01 HPQOEM SLIC-CPC 00001000 INTL 20091112)
[    0.000000] ACPI: SSDT 0x00000000DDBB7E58 0009AA (v01 HPQOEM SLIC-CPC 00003000 INTL 20051117)
[    0.000000] ACPI: SSDT 0x00000000DDBB8808 000A92 (v01 HPQOEM SLIC-CPC 00003000 INTL 20051117)
[    0.000000] ACPI: DMAR 0x00000000DDBB92A0 000080 (v01 HPQOEM SLIC-CPC 00000001 INTL 00000001)
[    0.000000] ACPI: DBGP 0x00000000DDBB9320 000034 (v01 HPQOEM SLIC-CPC 01072009 AMI  00010013)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at [mem 0x0000000000000000-0x000000031effffff]
[    0.000000] NODE_DATA(0) allocated [mem 0x31efec000-0x31eff0fff]
[    0.000000] Zone ranges:
[    0.000000]   DMA      [mem 0x0000000000001000-0x0000000000ffffff]
[    0.000000]   DMA32    [mem 0x0000000001000000-0x00000000ffffffff]
[    0.000000]   Normal   [mem 0x0000000100000000-0x000000031effffff]
[    0.000000]   Device   empty
[    0.000000] Movable zone start for each node
[    0.000000] Early memory node ranges
[    0.000000]   node   0: [mem 0x0000000000001000-0x000000000009efff]
[    0.000000]   node   0: [mem 0x0000000000100000-0x00000000dda07fff]
[    0.000000]   node   0: [mem 0x00000000ddc1c000-0x00000000ddc9efff]
[    0.000000]   node   0: [mem 0x00000000de1e9000-0x00000000de1e9fff]
[    0.000000]   node   0: [mem 0x00000000de22d000-0x00000000ded5cfff]
[    0.000000]   node   0: [mem 0x00000000deff2000-0x00000000deffffff]
[    0.000000]   node   0: [mem 0x0000000100000000-0x000000031effffff]
[    0.000000] Initmem setup node 0 [mem 0x0000000000001000-0x000000031effffff]
[    0.000000] On node 0 totalpages: 3134824
[    0.000000]   DMA zone: 64 pages used for memmap
[    0.000000]   DMA zone: 26 pages reserved
[    0.000000]   DMA zone: 3998 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 14168 pages used for memmap
[    0.000000]   DMA32 zone: 906698 pages, LIFO batch:31
[    0.000000]   Normal zone: 34752 pages used for memmap
[    0.000000]   Normal zone: 2224128 pages, LIFO batch:31
[    0.000000] ACPI: PM-Timer IO Port: 0x408
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0xff] high edge lint[0x1])
[    0.000000] IOAPIC[0]: apic_id 0, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x8086a701 base: 0xfed00000
[    0.000000] smpboot: Allowing 8 CPUs, 0 hotplug CPUs
[    0.000000] PM: Registered nosave memory: [mem 0x00000000-0x00000fff]
[    0.000000] PM: Registered nosave memory: [mem 0x0009f000-0x0009ffff]
[    0.000000] PM: Registered nosave memory: [mem 0x000a0000-0x000fffff]
[    0.000000] PM: Registered nosave memory: [mem 0xdda08000-0xddbadfff]
[    0.000000] PM: Registered nosave memory: [mem 0xddbae000-0xddbb9fff]
[    0.000000] PM: Registered nosave memory: [mem 0xddbba000-0xddc15fff]
[    0.000000] PM: Registered nosave memory: [mem 0xddc16000-0xddc1bfff]
[    0.000000] PM: Registered nosave memory: [mem 0xddc9f000-0xddd36fff]
[    0.000000] PM: Registered nosave memory: [mem 0xddd37000-0xde120fff]
[    0.000000] PM: Registered nosave memory: [mem 0xde121000-0xde1e8fff]
[    0.000000] PM: Registered nosave memory: [mem 0xde1ea000-0xde22cfff]
[    0.000000] PM: Registered nosave memory: [mem 0xded5d000-0xdeff1fff]
[    0.000000] PM: Registered nosave memory: [mem 0xdf000000-0xf7ffffff]
[    0.000000] PM: Registered nosave memory: [mem 0xf8000000-0xfbffffff]
[    0.000000] PM: Registered nosave memory: [mem 0xfc000000-0xfebfffff]
[    0.000000] PM: Registered nosave memory: [mem 0xfec00000-0xfec00fff]
[    0.000000] PM: Registered nosave memory: [mem 0xfec01000-0xfecfffff]
[    0.000000] PM: Registered nosave memory: [mem 0xfed00000-0xfed03fff]
[    0.000000] PM: Registered nosave memory: [mem 0xfed04000-0xfed1bfff]
[    0.000000] PM: Registered nosave memory: [mem 0xfed1c000-0xfed1ffff]
[    0.000000] PM: Registered nosave memory: [mem 0xfed20000-0xfedfffff]
[    0.000000] PM: Registered nosave memory: [mem 0xfee00000-0xfee00fff]
[    0.000000] PM: Registered nosave memory: [mem 0xfee01000-0xfeffffff]
[    0.000000] PM: Registered nosave memory: [mem 0xff000000-0xffffffff]
[    0.000000] e820: [mem 0xdf000000-0xf7ffffff] available for PCI devices
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] clocksource: refined-jiffies: mask: 0xffffffff max_cycles: 0xffffffff, max_idle_ns: 7645519600211568 ns
[    0.000000] setup_percpu: NR_CPUS:256 nr_cpumask_bits:256 nr_cpu_ids:8 nr_node_ids:1
[    0.000000] PERCPU: Embedded 33 pages/cpu @ffff88031ec00000 s98008 r8192 d28968 u262144
[    0.000000] pcpu-alloc: s98008 r8192 d28968 u262144 alloc=1*2097152
[    0.000000] pcpu-alloc: [0] 0 1 2 3 4 5 6 7 
[    0.000000] Built 1 zonelists in Node order, mobility grouping on.  Total pages: 3085814
[    0.000000] Policy zone: Normal
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-4.4.0-45-generic.efi.signed root=UUID=e40db2de-5153-4289-9e96-ea2791382804 ro quiet splash vt.handoff=7
[    0.000000] PID hash table entries: 4096 (order: 3, 32768 bytes)
[    0.000000] Calgary: detecting Calgary via BIOS EBDA area
[    0.000000] Calgary: Unable to locate Rio Grande table in EBDA - bailing!
[    0.000000] Memory: 12002084K/12539296K available (8409K kernel code, 1283K rwdata, 3944K rodata, 1480K init, 1292K bss, 537212K reserved, 0K cma-reserved)
[    0.000000] SLUB: HWalign=64, Order=0-3, MinObjects=0, CPUs=8, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000] 	Build-time adjustment of leaf fanout to 64.
[    0.000000] 	RCU restricting CPUs from NR_CPUS=256 to nr_cpu_ids=8.
[    0.000000] RCU: Adjusting geometry for rcu_fanout_leaf=64, nr_cpu_ids=8
[    0.000000] NR_IRQS:16640 nr_irqs:488 16
[    0.000000] vt handoff: transparent VT on vt#7
[    0.000000] Console: colour dummy device 80x25
[    0.000000] console [tty0] enabled
[    0.000000] clocksource: hpet: mask: 0xffffffff max_cycles: 0xffffffff, max_idle_ns: 133484882848 ns
[    0.000000] hpet clockevent registered
[    0.000000] tsc: Fast TSC calibration using PIT
[    0.000000] tsc: Detected 3392.120 MHz processor
[    0.000026] Calibrating delay loop (skipped), value calculated using timer frequency.. 6784.24 BogoMIPS (lpj=13568480)
[    0.000028] pid_max: default: 32768 minimum: 301
[    0.000032] ACPI: Core revision 20150930
[    0.004706] ACPI: 4 ACPI AML tables successfully acquired and loaded
[    0.043217] Security Framework initialized
[    0.043218] Yama: becoming mindful.
[    0.043230] AppArmor: AppArmor initialized
[    0.043929] Dentry cache hash table entries: 2097152 (order: 12, 16777216 bytes)
[    0.046231] Inode-cache hash table entries: 1048576 (order: 11, 8388608 bytes)
[    0.047220] Mount-cache hash table entries: 32768 (order: 6, 262144 bytes)
[    0.047233] Mountpoint-cache hash table entries: 32768 (order: 6, 262144 bytes)
[    0.047416] Initializing cgroup subsys io
[    0.047419] Initializing cgroup subsys memory
[    0.047424] Initializing cgroup subsys devices
[    0.047425] Initializing cgroup subsys freezer
[    0.047427] Initializing cgroup subsys net_cls
[    0.047428] Initializing cgroup subsys perf_event
[    0.047430] Initializing cgroup subsys net_prio
[    0.047432] Initializing cgroup subsys hugetlb
[    0.047433] Initializing cgroup subsys pids
[    0.047449] CPU: Physical Processor ID: 0
[    0.047450] CPU: Processor Core ID: 0
[    0.047454] ENERGY_PERF_BIAS: Set to 'normal', was 'performance'
[    0.047454] ENERGY_PERF_BIAS: View and update with x86_energy_perf_policy(8)
[    0.047456] mce: CPU supports 9 MCE banks
[    0.047466] CPU0: Thermal monitoring enabled (TM1)
[    0.047470] process: using mwait in idle threads
[    0.047473] Last level iTLB entries: 4KB 512, 2MB 8, 4MB 8
[    0.047474] Last level dTLB entries: 4KB 512, 2MB 32, 4MB 32, 1GB 0
[    0.047782] Freeing SMP alternatives memory: 32K (ffffffff820b4000 - ffffffff820bc000)
[    0.053802] ftrace: allocating 32007 entries in 126 pages
[    0.065335] smpboot: Max logical packages: 2
[    0.065336] smpboot: APIC(0) Converting physical 0 to logical package 0
[    0.065341] DMAR: Host address width 36
[    0.065342] DMAR: DRHD base: 0x000000fed90000 flags: 0x1
[    0.065348] DMAR: dmar0: reg_base_addr fed90000 ver 1:0 cap c9008020660262 ecap f0105a
[    0.065349] DMAR: RMRR base: 0x000000ddb8e000 end: 0x000000ddba9fff
[    0.065351] DMAR-IR: IOAPIC id 0 under DRHD base  0xfed90000 IOMMU 0
[    0.065352] DMAR-IR: HPET id 0 under DRHD base 0xfed90000
[    0.065353] DMAR-IR: Queued invalidation will be enabled to support x2apic and Intr-remapping.
[    0.065532] DMAR-IR: Enabled IRQ remapping in x2apic mode
[    0.065533] x2apic enabled
[    0.065538] Switched APIC routing to cluster x2apic.
[    0.065950] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.105637] TSC deadline timer enabled
[    0.105640] smpboot: CPU0: Intel(R) Core(TM) i7-2600 CPU @ 3.40GHz (family: 0x6, model: 0x2a, stepping: 0x7)
[    0.105653] Performance Events: PEBS fmt1+, 16-deep LBR, SandyBridge events, full-width counters, Intel PMU driver.
[    0.105669] ... version:                3
[    0.105670] ... bit width:              48
[    0.105670] ... generic registers:      4
[    0.105671] ... value mask:             0000ffffffffffff
[    0.105672] ... max period:             0000ffffffffffff
[    0.105672] ... fixed-purpose events:   3
[    0.105673] ... event mask:             000000070000000f
[    0.106261] x86: Booting SMP configuration:
[    0.106262] .... node  #0, CPUs:      #1
[    0.106878] microcode: CPU1 microcode updated early to revision 0x29, date = 2013-06-12
[    0.109033] NMI watchdog: enabled on all CPUs, permanently consumes one hw-PMU counter.
[    0.109096]  #2
[    0.109645] microcode: CPU2 microcode updated early to revision 0x29, date = 2013-06-12
[    0.111775]  #3
[    0.112303] microcode: CPU3 microcode updated early to revision 0x29, date = 2013-06-12
[    0.114433]  #4 #5 #6 #7
[    0.124018] x86: Booted up 1 node, 8 CPUs
[    0.124021] smpboot: Total of 8 processors activated (54273.92 BogoMIPS)
[    0.130638] devtmpfs: initialized
[    0.132827] evm: security.selinux
[    0.132828] evm: security.SMACK64
[    0.132828] evm: security.SMACK64EXEC
[    0.132829] evm: security.SMACK64TRANSMUTE
[    0.132830] evm: security.SMACK64MMAP
[    0.132830] evm: security.ima
[    0.132831] evm: security.capability
[    0.132878] PM: Registering ACPI NVS region [mem 0xddc9f000-0xddd36fff] (622592 bytes)
[    0.132884] PM: Registering ACPI NVS region [mem 0xde1ea000-0xde22cfff] (274432 bytes)
[    0.132946] clocksource: jiffies: mask: 0xffffffff max_cycles: 0xffffffff, max_idle_ns: 7645041785100000 ns
[    0.133012] pinctrl core: initialized pinctrl subsystem
[    0.133102] RTC time:  2:26:31, date: 11/03/16
[    0.133184] NET: Registered protocol family 16
[    0.142487] cpuidle: using governor ladder
[    0.158485] cpuidle: using governor menu
[    0.158495] PCCT header not found.
[    0.158593] ACPI FADT declares the system doesn't support PCIe ASPM, so disable it
[    0.158594] ACPI: bus type PCI registered
[    0.158596] acpiphp: ACPI Hot Plug PCI Controller Driver version: 0.5
[    0.158652] PCI: MMCONFIG for domain 0000 [bus 00-3f] at [mem 0xf8000000-0xfbffffff] (base 0xf8000000)
[    0.158654] PCI: MMCONFIG at [mem 0xf8000000-0xfbffffff] reserved in E820
[    0.158662] PCI: Using configuration type 1 for base access
[    0.158688] core: PMU erratum BJ122, BV98, HSD29 worked around, HT is on
[    0.172052] ACPI: Added _OSI(Module Device)
[    0.172053] ACPI: Added _OSI(Processor Device)
[    0.172054] ACPI: Added _OSI(3.0 _SCP Extensions)
[    0.172055] ACPI: Added _OSI(Processor Aggregator Device)
[    0.173896] ACPI: Executed 1 blocks of module-level executable AML code
[    0.175532] ACPI: Dynamic OEM Table Load:
[    0.175537] ACPI: SSDT 0xFFFF88030FC4D000 00083B (v01 HPQOEM SLIC-CPC 00003001 INTL 20051117)
[    0.175896] ACPI: Dynamic OEM Table Load:
[    0.175900] ACPI: SSDT 0xFFFF88030FD1C000 000303 (v01 HPQOEM SLIC-CPC 00003000 INTL 20051117)
[    0.176202] ACPI: Dynamic OEM Table Load:
[    0.176204] ACPI: SSDT 0xFFFF88030FD13000 000119 (v01 HPQOEM SLIC-CPC 00003000 INTL 20051117)
[    0.177202] ACPI: Interpreter enabled
[    0.177207] ACPI Exception: AE_NOT_FOUND, While evaluating Sleep State [\_S1_] (20150930/hwxface-580)
[    0.177210] ACPI Exception: AE_NOT_FOUND, While evaluating Sleep State [\_S2_] (20150930/hwxface-580)
[    0.177220] ACPI: (supports S0 S3 S4 S5)
[    0.177221] ACPI: Using IOAPIC for interrupt routing
[    0.177238] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[    0.181507] ACPI: Power Resource [FN00] (off)
[    0.181565] ACPI: Power Resource [FN01] (off)
[    0.181622] ACPI: Power Resource [FN02] (off)
[    0.181679] ACPI: Power Resource [FN03] (off)
[    0.181735] ACPI: Power Resource [FN04] (off)
[    0.182153] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-3e])
[    0.182156] acpi PNP0A08:00: _OSC: OS supports [ExtendedConfig ASPM ClockPM Segments MSI]
[    0.892998] acpi PNP0A08:00: _OSC: platform does not support [PCIeHotplug PME]
[    0.893088] acpi PNP0A08:00: _OSC: OS now controls [AER PCIeCapability]
[    0.893090] acpi PNP0A08:00: FADT indicates ASPM is unsupported, using BIOS configuration
[    0.893429] PCI host bridge to bus 0000:00
[    0.893431] pci_bus 0000:00: root bus resource [io  0x0000-0x0cf7 window]
[    0.893433] pci_bus 0000:00: root bus resource [io  0x0d00-0xffff window]
[    0.893434] pci_bus 0000:00: root bus resource [mem 0x000a0000-0x000bffff window]
[    0.893435] pci_bus 0000:00: root bus resource [mem 0x000dc000-0x000dffff window]
[    0.893437] pci_bus 0000:00: root bus resource [mem 0xe0000000-0xfeafffff window]
[    0.893438] pci_bus 0000:00: root bus resource [bus 00-3e]
[    0.893444] pci 0000:00:00.0: [8086:0100] type 00 class 0x060000
[    0.893512] pci 0000:00:01.0: [8086:0101] type 01 class 0x060400
[    0.893536] pci 0000:00:01.0: PME# supported from D0 D3hot D3cold
[    0.893566] pci 0000:00:01.0: System wakeup disabled by ACPI
[    0.893620] pci 0000:00:14.0: [8086:1e31] type 00 class 0x0c0330
[    0.893648] pci 0000:00:14.0: reg 0x10: [mem 0xf7f00000-0xf7f0ffff 64bit]
[    0.893704] pci 0000:00:14.0: PME# supported from D3hot D3cold
[    0.893737] pci 0000:00:14.0: System wakeup disabled by ACPI
[    0.893767] pci 0000:00:16.0: [8086:1e3a] type 00 class 0x078000
[    0.893797] pci 0000:00:16.0: reg 0x10: [mem 0xf7f1a000-0xf7f1a00f 64bit]
[    0.893856] pci 0000:00:16.0: PME# supported from D0 D3hot D3cold
[    0.893923] pci 0000:00:1a.0: [8086:1e2d] type 00 class 0x0c0320
[    0.893950] pci 0000:00:1a.0: reg 0x10: [mem 0xf7f18000-0xf7f183ff]
[    0.894019] pci 0000:00:1a.0: PME# supported from D0 D3hot D3cold
[    0.894062] pci 0000:00:1a.0: System wakeup disabled by ACPI
[    0.894094] pci 0000:00:1b.0: [8086:1e20] type 00 class 0x040300
[    0.894117] pci 0000:00:1b.0: reg 0x10: [mem 0xf7f10000-0xf7f13fff 64bit]
[    0.894168] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    0.894205] pci 0000:00:1b.0: System wakeup disabled by ACPI
[    0.894239] pci 0000:00:1c.0: [8086:1e10] type 01 class 0x060400
[    0.894363] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.894408] pci 0000:00:1c.0: System wakeup disabled by ACPI
[    0.894439] pci 0000:00:1c.4: [8086:1e18] type 01 class 0x060400
[    0.894510] pci 0000:00:1c.4: PME# supported from D0 D3hot D3cold
[    0.894546] pci 0000:00:1c.4: System wakeup disabled by ACPI
[    0.894576] pci 0000:00:1c.5: [8086:1e1a] type 01 class 0x060400
[    0.894646] pci 0000:00:1c.5: PME# supported from D0 D3hot D3cold
[    0.894683] pci 0000:00:1c.5: System wakeup disabled by ACPI
[    0.894714] pci 0000:00:1d.0: [8086:1e26] type 00 class 0x0c0320
[    0.894741] pci 0000:00:1d.0: reg 0x10: [mem 0xf7f17000-0xf7f173ff]
[    0.894810] pci 0000:00:1d.0: PME# supported from D0 D3hot D3cold
[    0.894853] pci 0000:00:1d.0: System wakeup disabled by ACPI
[    0.894884] pci 0000:00:1f.0: [8086:1e46] type 00 class 0x060100
[    0.895034] pci 0000:00:1f.2: [8086:1e02] type 00 class 0x010601
[    0.895056] pci 0000:00:1f.2: reg 0x10: [io  0xf070-0xf077]
[    0.895063] pci 0000:00:1f.2: reg 0x14: [io  0xf060-0xf063]
[    0.895071] pci 0000:00:1f.2: reg 0x18: [io  0xf050-0xf057]
[    0.895078] pci 0000:00:1f.2: reg 0x1c: [io  0xf040-0xf043]
[    0.895085] pci 0000:00:1f.2: reg 0x20: [io  0xf020-0xf03f]
[    0.895093] pci 0000:00:1f.2: reg 0x24: [mem 0xf7f16000-0xf7f167ff]
[    0.895122] pci 0000:00:1f.2: PME# supported from D3hot
[    0.895179] pci 0000:00:1f.3: [8086:1e22] type 00 class 0x0c0500
[    0.895195] pci 0000:00:1f.3: reg 0x10: [mem 0xf7f15000-0xf7f150ff 64bit]
[    0.895214] pci 0000:00:1f.3: reg 0x20: [io  0xf000-0xf01f]
[    0.895314] pci 0000:01:00.0: [1002:675d] type 00 class 0x030000
[    0.895338] pci 0000:01:00.0: reg 0x10: [mem 0xe0000000-0xefffffff 64bit pref]
[    0.895348] pci 0000:01:00.0: reg 0x18: [mem 0xf7e20000-0xf7e3ffff 64bit]
[    0.895355] pci 0000:01:00.0: reg 0x20: [io  0xe000-0xe0ff]
[    0.895367] pci 0000:01:00.0: reg 0x30: [mem 0xf7e00000-0xf7e1ffff pref]
[    0.895393] pci 0000:01:00.0: supports D1 D2
[    0.895434] pci 0000:01:00.1: [1002:aa90] type 00 class 0x040300
[    0.895456] pci 0000:01:00.1: reg 0x10: [mem 0xf7e40000-0xf7e43fff 64bit]
[    0.895501] pci 0000:01:00.1: supports D1 D2
[    0.900991] pci 0000:00:01.0: PCI bridge to [bus 01]
[    0.900996] pci 0000:00:01.0:   bridge window [io  0xe000-0xefff]
[    0.900999] pci 0000:00:01.0:   bridge window [mem 0xf7e00000-0xf7efffff]
[    0.901004] pci 0000:00:01.0:   bridge window [mem 0xe0000000-0xefffffff 64bit pref]
[    0.901083] pci 0000:00:1c.0: PCI bridge to [bus 02]
[    0.901177] pci 0000:03:00.0: [14e4:4357] type 00 class 0x028000
[    0.901256] pci 0000:03:00.0: reg 0x10: [mem 0xf7d00000-0xf7d03fff 64bit]
[    0.901436] pci 0000:03:00.0: supports D1 D2
[    0.901492] pci 0000:03:00.0: System wakeup disabled by ACPI
[    0.909011] pci 0000:00:1c.4: PCI bridge to [bus 03]
[    0.909020] pci 0000:00:1c.4:   bridge window [mem 0xf7d00000-0xf7dfffff]
[    0.909184] pci 0000:04:00.0: [1969:1091] type 00 class 0x020000
[    0.909376] pci 0000:04:00.0: reg 0x10: [mem 0xf7c00000-0xf7c3ffff 64bit]
[    0.909423] pci 0000:04:00.0: reg 0x18: [io  0xd000-0xd07f]
[    0.909785] pci 0000:04:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.909892] pci 0000:04:00.0: System wakeup disabled by ACPI
[    0.917030] pci 0000:00:1c.5: PCI bridge to [bus 04]
[    0.917036] pci 0000:00:1c.5:   bridge window [io  0xd000-0xdfff]
[    0.917042] pci 0000:00:1c.5:   bridge window [mem 0xf7c00000-0xf7cfffff]
[    0.917384] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 10 *11 12 14 15)
[    0.917422] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 *10 11 12 14 15)
[    0.917458] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 10 *11 12 14 15)
[    0.917494] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 *5 6 10 11 12 14 15)
[    0.917530] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 10 11 12 14 15) *0, disabled.
[    0.917566] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 10 11 12 14 15) *0, disabled.
[    0.917602] ACPI: PCI Interrupt Link [LNKG] (IRQs *3 4 5 6 10 11 12 14 15)
[    0.917638] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 *4 5 6 10 11 12 14 15)
[    0.917806] ACPI: Enabled 4 GPEs in block 00 to 3F
[    0.917894] vgaarb: setting as boot device: PCI:0000:01:00.0
[    0.917895] vgaarb: device added: PCI:0000:01:00.0,decodes=io+mem,owns=io+mem,locks=none
[    0.917896] vgaarb: loaded
[    0.917897] vgaarb: bridge control possible 0000:01:00.0
[    0.918050] SCSI subsystem initialized
[    0.918074] libata version 3.00 loaded.
[    0.918089] ACPI: bus type USB registered
[    0.918101] usbcore: registered new interface driver usbfs
[    0.918106] usbcore: registered new interface driver hub
[    0.918120] usbcore: registered new device driver usb
[    0.918249] PCI: Using ACPI for IRQ routing
[    0.919691] PCI: pci_cache_line_size set to 64 bytes
[    0.919753] e820: reserve RAM buffer [mem 0x0009f000-0x0009ffff]
[    0.919754] e820: reserve RAM buffer [mem 0xdda08000-0xdfffffff]
[    0.919756] e820: reserve RAM buffer [mem 0xddc9f000-0xdfffffff]
[    0.919757] e820: reserve RAM buffer [mem 0xde1ea000-0xdfffffff]
[    0.919758] e820: reserve RAM buffer [mem 0xded5d000-0xdfffffff]
[    0.919759] e820: reserve RAM buffer [mem 0xdf000000-0xdfffffff]
[    0.919760] e820: reserve RAM buffer [mem 0x31f000000-0x31fffffff]
[    0.919840] NetLabel: Initializing
[    0.919841] NetLabel:  domain hash size = 128
[    0.919842] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.919851] NetLabel:  unlabeled traffic allowed by default
[    0.919901] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0, 0, 0, 0, 0
[    0.919904] hpet0: 8 comparators, 64-bit 14.318180 MHz counter
[    0.922919] amd_nb: Cannot enumerate AMD northbridges
[    0.922931] clocksource: Switched to clocksource hpet
[    0.927189] AppArmor: AppArmor Filesystem Enabled
[    0.927240] pnp: PnP ACPI init
[    0.927314] system 00:00: [mem 0xfed40000-0xfed44fff] has been reserved
[    0.927318] system 00:00: Plug and Play ACPI device, IDs PNP0c01 (active)
[    0.927375] system 00:01: [io  0x0680-0x069f] has been reserved
[    0.927376] system 00:01: [io  0x0200-0x020f] has been reserved
[    0.927378] system 00:01: [io  0xffff] has been reserved
[    0.927379] system 00:01: [io  0xffff] has been reserved
[    0.927381] system 00:01: [io  0x0400-0x0453] could not be reserved
[    0.927382] system 00:01: [io  0x0458-0x047f] has been reserved
[    0.927383] system 00:01: [io  0x0500-0x057f] has been reserved
[    0.927384] system 00:01: [io  0x164e-0x164f] has been reserved
[    0.927386] system 00:01: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.927406] pnp 00:02: Plug and Play ACPI device, IDs PNP0b00 (active)
[    0.927441] system 00:03: [io  0x0454-0x0457] has been reserved
[    0.927444] system 00:03: Plug and Play ACPI device, IDs INT3f0d PNP0c02 (active)
[    0.927496] system 00:04: [io  0x0290-0x029f] has been reserved
[    0.927498] system 00:04: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.927548] system 00:05: [io  0x04d0-0x04d1] has been reserved
[    0.927550] system 00:05: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.927713] system 00:06: [mem 0xfed1c000-0xfed1ffff] has been reserved
[    0.927715] system 00:06: [mem 0xfed10000-0xfed17fff] has been reserved
[    0.927716] system 00:06: [mem 0xfed18000-0xfed18fff] has been reserved
[    0.927718] system 00:06: [mem 0xfed19000-0xfed19fff] has been reserved
[    0.927719] system 00:06: [mem 0xf8000000-0xfbffffff] has been reserved
[    0.927720] system 00:06: [mem 0xfed20000-0xfed3ffff] has been reserved
[    0.927722] system 00:06: [mem 0xfed90000-0xfed93fff] could not be reserved
[    0.927723] system 00:06: [mem 0xfed45000-0xfed8ffff] has been reserved
[    0.927724] system 00:06: [mem 0xff000000-0xffffffff] has been reserved
[    0.927726] system 00:06: [mem 0xfee00000-0xfeefffff] could not be reserved
[    0.927727] system 00:06: [mem 0xf0000000-0xf0000fff] has been reserved
[    0.927729] system 00:06: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.927823] pnp: PnP ACPI: found 7 devices
[    0.933745] clocksource: acpi_pm: mask: 0xffffff max_cycles: 0xffffff, max_idle_ns: 2085701024 ns
[    0.933781] pci 0000:00:01.0: PCI bridge to [bus 01]
[    0.933783] pci 0000:00:01.0:   bridge window [io  0xe000-0xefff]
[    0.933786] pci 0000:00:01.0:   bridge window [mem 0xf7e00000-0xf7efffff]
[    0.933788] pci 0000:00:01.0:   bridge window [mem 0xe0000000-0xefffffff 64bit pref]
[    0.933790] pci 0000:00:1c.0: PCI bridge to [bus 02]
[    0.933808] pci 0000:00:1c.4: PCI bridge to [bus 03]
[    0.933812] pci 0000:00:1c.4:   bridge window [mem 0xf7d00000-0xf7dfffff]
[    0.933820] pci 0000:00:1c.5: PCI bridge to [bus 04]
[    0.933822] pci 0000:00:1c.5:   bridge window [io  0xd000-0xdfff]
[    0.933827] pci 0000:00:1c.5:   bridge window [mem 0xf7c00000-0xf7cfffff]
[    0.933835] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7 window]
[    0.933837] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff window]
[    0.933838] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff window]
[    0.933839] pci_bus 0000:00: resource 7 [mem 0x000dc000-0x000dffff window]
[    0.933841] pci_bus 0000:00: resource 8 [mem 0xe0000000-0xfeafffff window]
[    0.933842] pci_bus 0000:01: resource 0 [io  0xe000-0xefff]
[    0.933843] pci_bus 0000:01: resource 1 [mem 0xf7e00000-0xf7efffff]
[    0.933844] pci_bus 0000:01: resource 2 [mem 0xe0000000-0xefffffff 64bit pref]
[    0.933846] pci_bus 0000:03: resource 1 [mem 0xf7d00000-0xf7dfffff]
[    0.933847] pci_bus 0000:04: resource 0 [io  0xd000-0xdfff]
[    0.933848] pci_bus 0000:04: resource 1 [mem 0xf7c00000-0xf7cfffff]
[    0.933869] NET: Registered protocol family 2
[    0.934002] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.934164] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    0.934267] TCP: Hash tables configured (established 131072 bind 65536)
[    0.934289] UDP hash table entries: 8192 (order: 6, 262144 bytes)
[    0.934329] UDP-Lite hash table entries: 8192 (order: 6, 262144 bytes)
[    0.934389] NET: Registered protocol family 1
[    0.975046] pci 0000:01:00.0: Video device with shadowed ROM
[    0.975058] pci 0000:04:00.0: set MSI_INTX_DISABLE_BUG flag
[    0.975066] PCI: CLS 64 bytes, default 64
[    0.975103] Trying to unpack rootfs image as initramfs...
[    1.390027] Freeing initrd memory: 36972K (ffff8800337ba000 - ffff880035bd5000)
[    1.390060] PCI-DMA: Using software bounce buffering for IO (SWIOTLB)
[    1.390062] software IO TLB [mem 0xcc153000-0xd0153000] (64MB) mapped at [ffff8800cc153000-ffff8800d0152fff]
[    1.390121] RAPL PMU detected, API unit is 2^-32 Joules, 3 fixed counters 163840 ms ovfl timer
[    1.390122] hw unit of domain pp0-core 2^-16 Joules
[    1.390123] hw unit of domain package 2^-16 Joules
[    1.390123] hw unit of domain pp1-gpu 2^-16 Joules
[    1.390264] Scanning for low memory corruption every 60 seconds
[    1.390541] futex hash table entries: 2048 (order: 5, 131072 bytes)
[    1.390571] audit: initializing netlink subsys (disabled)
[    1.390582] audit: type=2000 audit(1478139991.640:1): initialized
[    1.390928] Initialise system trusted keyring
[    1.391043] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    1.392113] zbud: loaded
[    1.392256] VFS: Disk quotas dquot_6.6.0
[    1.392281] VFS: Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    1.392469] squashfs: version 4.0 (2009/01/31) Phillip Lougher
[    1.392641] fuse init (API version 7.23)
[    1.392741] Key type big_key registered
[    1.392760] Allocating IMA MOK and blacklist keyrings.
[    1.393064] Key type asymmetric registered
[    1.393066] Asymmetric key parser 'x509' registered
[    1.393090] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 249)
[    1.393124] io scheduler noop registered
[    1.393126] io scheduler deadline registered (default)
[    1.393147] io scheduler cfq registered
[    1.393602] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    1.393607] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    1.393632] efifb: probing for efifb
[    1.393639] efifb: framebuffer at 0xe0000000, mapped to 0xffffc90001c00000, using 1920k, total 1920k
[    1.393640] efifb: mode is 800x600x32, linelength=3200, pages=1
[    1.393641] efifb: scrolling: redraw
[    1.393642] efifb: Truecolor: size=8:8:8:8, shift=24:16:8:0
[    1.393698] Console: switching to colour frame buffer device 100x37
[    1.393706] fb0: EFI VGA frame buffer device
[    1.393713] intel_idle: MWAIT substates: 0x1120
[    1.393714] intel_idle: v0.4.1 model 0x2A
[    1.393714] intel_idle: lapic_timer_reliable_states 0xffffffff
[    1.393955] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0
[    1.393958] ACPI: Power Button [PWRB]
[    1.393984] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
[    1.393986] ACPI: Power Button [PWRF]
[    1.394574] thermal LNXTHERM:00: registered as thermal_zone0
[    1.394575] ACPI: Thermal Zone [TZ00] (28 C)
[    1.394741] thermal LNXTHERM:01: registered as thermal_zone1
[    1.394742] ACPI: Thermal Zone [TZ01] (30 C)
[    1.394767] GHES: HEST is not enabled!
[    1.394831] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    1.395981] Linux agpgart interface v0.103
[    1.398642] brd: module loaded
[    1.399818] loop: module loaded
[    1.399967] libphy: Fixed MDIO Bus: probed
[    1.399969] tun: Universal TUN/TAP device driver, 1.6
[    1.399970] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    1.400001] PPP generic driver version 2.4.2
[    1.400041] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    1.400044] ehci-pci: EHCI PCI platform driver
[    1.400114] ehci-pci 0000:00:1a.0: EHCI Host Controller
[    1.400119] ehci-pci 0000:00:1a.0: new USB bus registered, assigned bus number 1
[    1.400129] ehci-pci 0000:00:1a.0: debug port 2
[    1.404029] ehci-pci 0000:00:1a.0: cache line size of 64 is not supported
[    1.404041] ehci-pci 0000:00:1a.0: irq 16, io mem 0xf7f18000
[    1.414965] ehci-pci 0000:00:1a.0: USB 2.0 started, EHCI 1.00
[    1.414992] usb usb1: New USB device found, idVendor=1d6b, idProduct=0002
[    1.414993] usb usb1: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.414995] usb usb1: Product: EHCI Host Controller
[    1.414996] usb usb1: Manufacturer: Linux 4.4.0-45-generic ehci_hcd
[    1.414997] usb usb1: SerialNumber: 0000:00:1a.0
[    1.415109] hub 1-0:1.0: USB hub found
[    1.415114] hub 1-0:1.0: 2 ports detected
[    1.415263] ehci-pci 0000:00:1d.0: EHCI Host Controller
[    1.415267] ehci-pci 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    1.415277] ehci-pci 0000:00:1d.0: debug port 2
[    1.419165] ehci-pci 0000:00:1d.0: cache line size of 64 is not supported
[    1.419175] ehci-pci 0000:00:1d.0: irq 23, io mem 0xf7f17000
[    1.430979] ehci-pci 0000:00:1d.0: USB 2.0 started, EHCI 1.00
[    1.431020] usb usb2: New USB device found, idVendor=1d6b, idProduct=0002
[    1.431023] usb usb2: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.431025] usb usb2: Product: EHCI Host Controller
[    1.431035] usb usb2: Manufacturer: Linux 4.4.0-45-generic ehci_hcd
[    1.431036] usb usb2: SerialNumber: 0000:00:1d.0
[    1.431137] hub 2-0:1.0: USB hub found
[    1.431140] hub 2-0:1.0: 2 ports detected
[    1.431224] ehci-platform: EHCI generic platform driver
[    1.431232] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    1.431235] ohci-pci: OHCI PCI platform driver
[    1.431242] ohci-platform: OHCI generic platform driver
[    1.431247] uhci_hcd: USB Universal Host Controller Interface driver
[    1.431320] xhci_hcd 0000:00:14.0: xHCI Host Controller
[    1.431324] xhci_hcd 0000:00:14.0: new USB bus registered, assigned bus number 3
[    1.432406] xhci_hcd 0000:00:14.0: hcc params 0x20007181 hci version 0x100 quirks 0x0000b930
[    1.432411] xhci_hcd 0000:00:14.0: cache line size of 64 is not supported
[    1.432478] usb usb3: New USB device found, idVendor=1d6b, idProduct=0002
[    1.432480] usb usb3: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.432481] usb usb3: Product: xHCI Host Controller
[    1.432482] usb usb3: Manufacturer: Linux 4.4.0-45-generic xhci-hcd
[    1.432483] usb usb3: SerialNumber: 0000:00:14.0
[    1.432586] hub 3-0:1.0: USB hub found
[    1.432594] hub 3-0:1.0: 4 ports detected
[    1.432829] xhci_hcd 0000:00:14.0: xHCI Host Controller
[    1.432831] xhci_hcd 0000:00:14.0: new USB bus registered, assigned bus number 4
[    1.432853] usb usb4: New USB device found, idVendor=1d6b, idProduct=0003
[    1.432855] usb usb4: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.432856] usb usb4: Product: xHCI Host Controller
[    1.432857] usb usb4: Manufacturer: Linux 4.4.0-45-generic xhci-hcd
[    1.432858] usb usb4: SerialNumber: 0000:00:14.0
[    1.432961] hub 4-0:1.0: USB hub found
[    1.432969] hub 4-0:1.0: 4 ports detected
[    1.433230] i8042: PNP: No PS/2 controller found. Probing ports directly.
[    1.433641] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.433646] serio: i8042 AUX port at 0x60,0x64 irq 12
[    1.433771] mousedev: PS/2 mouse device common for all mice
[    1.433972] rtc_cmos 00:02: RTC can wake from S4
[    1.434111] rtc_cmos 00:02: rtc core: registered rtc_cmos as rtc0
[    1.434140] rtc_cmos 00:02: alarms up to one month, y3k, 242 bytes nvram, hpet irqs
[    1.434146] i2c /dev entries driver
[    1.434184] device-mapper: uevent: version 1.0.3
[    1.434234] device-mapper: ioctl: 4.34.0-ioctl (2015-10-28) initialised: [email]dm-devel@redhat.com[/email]
[    1.434249] Intel P-state driver initializing.
[    1.434530] ledtrig-cpu: registered to indicate activity on CPUs
[    1.434537] EFI Variables Facility v0.08 2004-May-17
[    1.645642] NET: Registered protocol family 10
[    1.645948] NET: Registered protocol family 17
[    1.645958] Key type dns_resolver registered
[    1.646237] microcode: CPU0 sig=0x206a7, pf=0x2, revision=0x29
[    1.646241] microcode: CPU1 sig=0x206a7, pf=0x2, revision=0x29
[    1.646265] microcode: CPU2 sig=0x206a7, pf=0x2, revision=0x29
[    1.646286] microcode: CPU3 sig=0x206a7, pf=0x2, revision=0x29
[    1.646319] microcode: CPU4 sig=0x206a7, pf=0x2, revision=0x29
[    1.646327] microcode: CPU5 sig=0x206a7, pf=0x2, revision=0x29
[    1.646364] microcode: CPU6 sig=0x206a7, pf=0x2, revision=0x29
[    1.646370] microcode: CPU7 sig=0x206a7, pf=0x2, revision=0x29
[    1.646409] microcode: Microcode Update Driver: v2.01 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[    1.646524] registered taskstats version 1
[    1.646534] Loading compiled-in X.509 certificates
[    1.647185] Loaded X.509 cert 'Build time autogenerated kernel key: 5295ae568fdd4deae5e4e5c175542790e6aaeab9'
[    1.647203] zswap: loaded using pool lzo/zbud
[    1.648919] Key type trusted registered
[    1.652075] Key type encrypted registered
[    1.652080] AppArmor: AppArmor sha1 policy hashing enabled
[    1.652082] ima: No TPM chip found, activating TPM-bypass!
[    1.652096] evm: HMAC attrs: 0x1
[    1.652504]   Magic number: 8:837:408
[    1.652647] rtc_cmos 00:02: setting system clock to 2016-11-03 02:26:33 UTC (1478139993)
[    1.652777] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.652778] EDD information not available.
[    1.652834] PM: Hibernation image not present or could not be loaded.
[    1.653868] Freeing unused kernel memory: 1480K (ffffffff81f42000 - ffffffff820b4000)
[    1.653869] Write protecting the kernel read-only data: 14336k
[    1.654306] Freeing unused kernel memory: 1820K (ffff880001839000 - ffff880001a00000)
[    1.654600] Freeing unused kernel memory: 152K (ffff880001dda000 - ffff880001e00000)
[    1.661421] random: systemd-udevd: uninitialized urandom read (16 bytes read, 1 bits of entropy available)
[    1.661474] random: systemd-udevd: uninitialized urandom read (16 bytes read, 1 bits of entropy available)
[    1.661484] random: systemd-udevd: uninitialized urandom read (16 bytes read, 1 bits of entropy available)
[    1.661725] random: udevadm: uninitialized urandom read (16 bytes read, 1 bits of entropy available)
[    1.661757] random: udevadm: uninitialized urandom read (16 bytes read, 1 bits of entropy available)
[    1.662062] random: udevadm: uninitialized urandom read (16 bytes read, 1 bits of entropy available)
[    1.662105] random: udevadm: uninitialized urandom read (16 bytes read, 1 bits of entropy available)
[    1.662141] random: udevadm: uninitialized urandom read (16 bytes read, 1 bits of entropy available)
[    1.662176] random: udevadm: uninitialized urandom read (16 bytes read, 1 bits of entropy available)
[    1.662209] random: udevadm: uninitialized urandom read (16 bytes read, 1 bits of entropy available)
[    1.680709] FUJITSU Extended Socket Network Device Driver - version 1.0 - Copyright (c) 2015 FUJITSU LIMITED
[    1.694799] ahci 0000:00:1f.2: version 3.0
[    1.696302] alx 0000:04:00.0 eth0: Qualcomm Atheros AR816x/AR817x Ethernet [4c:72:b9:58:2a:bc]
[    1.696342] ahci 0000:00:1f.2: AHCI 0001.0300 32 slots 6 ports 6 Gbps 0x3f impl SATA mode
[    1.696347] ahci 0000:00:1f.2: flags: 64bit ncq pm led clo pio slum part ems apst 
[    1.698524] [drm] Initialized drm 1.1.0 20060810
[    1.717817] alx 0000:04:00.0 enp4s0: renamed from eth0
[    1.728069] [drm] radeon kernel modesetting enabled.
[    1.729712] AMD IOMMUv2 driver by Joerg Roedel <jroedel@suse.de>
[    1.729714] AMD IOMMUv2 functionality not available on this system
[    1.731005] usb 1-1: new high-speed USB device number 2 using ehci-pci
[    1.732074] CRAT table not found
[    1.732075] Finished initializing topology ret=0
[    1.732146] kfd kfd: Initialized module
[    1.732336] checking generic (e0000000 1e0000) vs hw (e0000000 10000000)
[    1.732338] fb: switching to radeondrmfb from EFI VGA
[    1.732357] Console: switching to colour dummy device 80x25
[    1.732601] [drm] initializing kernel modesetting (TURKS 0x1002:0x675D 0x1B0A:0x90B5).
[    1.732609] [drm] register mmio base: 0xF7E20000
[    1.732609] [drm] register mmio size: 131072
[    1.732642] ATOM BIOS: HP
[    1.732805] radeon 0000:01:00.0: VRAM: 1024M 0x0000000000000000 - 0x000000003FFFFFFF (1024M used)
[    1.732807] radeon 0000:01:00.0: GTT: 1024M 0x0000000040000000 - 0x000000007FFFFFFF
[    1.732807] [drm] Detected VRAM RAM=1024M, BAR=256M
[    1.732808] [drm] RAM width 128bits DDR
[    1.732849] [TTM] Zone  kernel: Available graphics memory: 6130088 kiB
[    1.732850] [TTM] Zone   dma32: Available graphics memory: 2097152 kiB
[    1.732851] [TTM] Initializing pool allocator
[    1.732854] [TTM] Initializing DMA pool allocator
[    1.732867] [drm] radeon: 1024M of VRAM memory ready
[    1.732867] [drm] radeon: 1024M of GTT memory ready.
[    1.732874] [drm] Loading TURKS Microcode
[    1.732924] [drm] Internal thermal controller with fan control
[    1.737213] [drm] radeon: dpm initialized
[    1.737265] [drm] GART: num cpu pages 262144, num gpu pages 262144
[    1.737696] [drm] enabling PCIE gen 2 link speeds, disable with radeon.pcie_gen2=0
[    1.739761] scsi host0: ahci
[    1.740134] scsi host1: ahci
[    1.740467] scsi host2: ahci
[    1.740761] scsi host3: ahci
[    1.740958] scsi host4: ahci
[    1.741142] scsi host5: ahci
[    1.741189] ata1: SATA max UDMA/133 abar m2048@0xf7f16000 port 0xf7f16100 irq 27
[    1.741192] ata2: SATA max UDMA/133 abar m2048@0xf7f16000 port 0xf7f16180 irq 27
[    1.741195] ata3: SATA max UDMA/133 abar m2048@0xf7f16000 port 0xf7f16200 irq 27
[    1.741199] ata4: SATA max UDMA/133 abar m2048@0xf7f16000 port 0xf7f16280 irq 27
[    1.741202] ata5: SATA max UDMA/133 abar m2048@0xf7f16000 port 0xf7f16300 irq 27
[    1.741205] ata6: SATA max UDMA/133 abar m2048@0xf7f16000 port 0xf7f16380 irq 27
[    1.743053] usb 2-1: new high-speed USB device number 2 using ehci-pci
[    1.743075] usb 3-3: new high-speed USB device number 2 using xhci_hcd
[    1.749404] [drm] PCIE GART of 1024M enabled (table at 0x0000000000274000).
[    1.749508] radeon 0000:01:00.0: WB enabled
[    1.749510] radeon 0000:01:00.0: fence driver on ring 0 use gpu addr 0x0000000040000c00 and cpu addr 0xffff880309eeec00
[    1.749511] radeon 0000:01:00.0: fence driver on ring 3 use gpu addr 0x0000000040000c0c and cpu addr 0xffff880309eeec0c
[    1.750967] radeon 0000:01:00.0: fence driver on ring 5 use gpu addr 0x0000000000072118 and cpu addr 0xffffc90002032118
[    1.750968] [drm] Supports vblank timestamp caching Rev 2 (21.10.2013).
[    1.750969] [drm] Driver supports precise vblank timestamp query.
[    1.750970] radeon 0000:01:00.0: radeon: MSI limited to 32-bit
[    1.751055] radeon 0000:01:00.0: radeon: using MSI.
[    1.751082] [drm] radeon: irq initialized.
[    1.767474] [drm] ring test on 0 succeeded in 2 usecs
[    1.767487] [drm] ring test on 3 succeeded in 9 usecs
[    1.863382] usb 1-1: New USB device found, idVendor=8087, idProduct=0024
[    1.863384] usb 1-1: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[    1.863666] hub 1-1:1.0: USB hub found
[    1.863755] hub 1-1:1.0: 6 ports detected
[    1.871937] usb 3-3: New USB device found, idVendor=1058, idProduct=1110
[    1.871939] usb 3-3: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[    1.871941] usb 3-3: Product: My Book 1110
[    1.871942] usb 3-3: Manufacturer: Western Digital
[    1.871944] usb 3-3: SerialNumber: 574341563535383035383733
[    1.875372] usb 2-1: New USB device found, idVendor=8087, idProduct=0024
[    1.875374] usb 2-1: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[    1.875646] hub 2-1:1.0: USB hub found
[    1.875745] hub 2-1:1.0: 8 ports detected
[    1.943411] [drm] ring test on 5 succeeded in 2 usecs
[    1.943421] [drm] UVD initialized successfully.
[    1.943691] [drm] ib test on ring 0 succeeded in 0 usecs
[    1.943744] [drm] ib test on ring 3 succeeded in 0 usecs
[    2.039010] usb 3-4: new low-speed USB device number 3 using xhci_hcd
[    2.059029] ata6: SATA link down (SStatus 4 SControl 300)
[    2.059066] ata5: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    2.059086] ata3: SATA link down (SStatus 4 SControl 300)
[    2.059113] ata4: SATA link down (SStatus 4 SControl 300)
[    2.059146] ata2: SATA link down (SStatus 4 SControl 300)
[    2.059167] ata1: SATA link up 6.0 Gbps (SStatus 133 SControl 300)
[    2.059583] ACPI Error: [DSSP] Namespace lookup failure, AE_NOT_FOUND (20150930/psargs-359)
[    2.059587] ACPI Error: Method parse/execution failed [\_SB.PCI0.SAT0.SPT0._GTF] (Node ffff8803120d3230), AE_NOT_FOUND (20150930/psparse-542)
[    2.059730] ata1.00: ATA-8: ST2000DM001-9YN164, HP16, max UDMA/100
[    2.059732] ata1.00: 3907029168 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
[    2.060146] ACPI Error: [DSSP] Namespace lookup failure, AE_NOT_FOUND (20150930/psargs-359)
[    2.060150] ACPI Error: Method parse/execution failed [\_SB.PCI0.SAT0.SPT0._GTF] (Node ffff8803120d3230), AE_NOT_FOUND (20150930/psparse-542)
[    2.060279] ata1.00: configured for UDMA/100
[    2.060507] scsi 0:0:0:0: Direct-Access     ATA      ST2000DM001-9YN1 HP16 PQ: 0 ANSI: 5
[    2.060814] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    2.060816] sd 0:0:0:0: [sda] 3907029168 512-byte logical blocks: (2.00 TB/1.82 TiB)
[    2.060817] sd 0:0:0:0: [sda] 4096-byte physical blocks
[    2.060849] sd 0:0:0:0: [sda] Write Protect is off
[    2.060851] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    2.060862] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.062835] ACPI Error: [DSSP] Namespace lookup failure, AE_NOT_FOUND (20150930/psargs-359)
[    2.062839] ACPI Error: Method parse/execution failed [\_SB.PCI0.SAT0.SPT4._GTF] (Node ffff8803120d3410), AE_NOT_FOUND (20150930/psparse-542)
[    2.062846] ata5.00: ATAPI: hp      DVD-RAM GH80N, RF04, max UDMA/100
[    2.067691] ACPI Error: [DSSP] Namespace lookup failure, AE_NOT_FOUND (20150930/psargs-359)
[    2.067695] ACPI Error: Method parse/execution failed [\_SB.PCI0.SAT0.SPT4._GTF] (Node ffff8803120d3410), AE_NOT_FOUND (20150930/psparse-542)
[    2.067702] ata5.00: configured for UDMA/100
[    2.076132] scsi 4:0:0:0: CD-ROM            hp       DVD-RAM GH80N    RF04 PQ: 0 ANSI: 5
[    2.098504]  sda: sda1 sda2 sda3
[    2.098556] sr 4:0:0:0: [sr0] scsi3-mmc drive: 40x/40x writer dvd-ram cd/rw xa/form2 cdda tray
[    2.098558] cdrom: Uniform CD-ROM driver Revision: 3.20
[    2.098663] sr 4:0:0:0: Attached scsi CD-ROM sr0
[    2.098719] sr 4:0:0:0: Attached scsi generic sg1 type 5
[    2.098767] sd 0:0:0:0: [sda] Attached SCSI disk
[    2.135038] usb 1-1.3: new high-speed USB device number 3 using ehci-pci
[    2.215038] usb 2-1.5: new full-speed USB device number 3 using ehci-pci
[    2.229280] usb 1-1.3: New USB device found, idVendor=058f, idProduct=6362
[    2.229285] usb 1-1.3: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[    2.229288] usb 1-1.3: Product: Mass Storage Device
[    2.229290] usb 1-1.3: Manufacturer: Generic
[    2.229293] usb 1-1.3: SerialNumber: 058F63626476
[    2.232144] usb-storage 3-3:1.0: USB Mass Storage device detected
[    2.232316] scsi host6: usb-storage 3-3:1.0
[    2.232377] usb-storage 1-1.3:1.0: USB Mass Storage device detected
[    2.232461] scsi host7: usb-storage 1-1.3:1.0
[    2.232499] usbcore: registered new interface driver usb-storage
[    2.233592] usbcore: registered new interface driver uas
[    2.241138] usb 3-4: New USB device found, idVendor=04d9, idProduct=0169
[    2.241140] usb 3-4: New USB device strings: Mfr=0, Product=2, SerialNumber=0
[    2.241141] usb 3-4: Product: USB Keyboard
[    2.241202] usb 3-4: ep 0x81 - rounding interval to 64 microframes, ep desc says 80 microframes
[    2.241205] usb 3-4: ep 0x82 - rounding interval to 64 microframes, ep desc says 80 microframes
[    2.244754] hidraw: raw HID events driver (C) Jiri Kosina
[    2.277472] usbcore: registered new interface driver usbhid
[    2.277474] usbhid: USB HID core driver
[    2.278680] input: USB Keyboard as /devices/pci0000:00/0000:00:14.0/usb3/3-4/3-4:1.0/0003:04D9:0169.0001/input/input5
[    2.311122] usb 2-1.5: New USB device found, idVendor=0461, idProduct=4dd6
[    2.311125] usb 2-1.5: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[    2.311126] usb 2-1.5: Product: HP Wireless Keyboard Kit
[    2.311127] usb 2-1.5: Manufacturer: Hewlett Packard
[    2.312630] input: Hewlett Packard HP Wireless Keyboard Kit as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.5/2-1.5:1.0/0003:0461:4DD6.0003/input/input6
[    2.319014] usb 1-1.5: new full-speed USB device number 5 using ehci-pci
[    2.331078] hid-generic 0003:04D9:0169.0001: input,hidraw0: USB HID v1.10 Keyboard [USB Keyboard] on usb-0000:00:14.0-4/input0
[    2.331152] input: USB Keyboard as /devices/pci0000:00/0000:00:14.0/usb3/3-4/3-4:1.1/0003:04D9:0169.0002/input/input7
[    2.387018] tsc: Refined TSC clocksource calibration: 3392.294 MHz
[    2.387020] clocksource: tsc: mask: 0xffffffffffffffff max_cycles: 0x30e5debfb38, max_idle_ns: 440795265279 ns
[    2.387126] hid-generic 0003:0461:4DD6.0003: input,hidraw1: USB HID v1.11 Keyboard [Hewlett Packard HP Wireless Keyboard Kit] on usb-0000:00:1d.0-1.5/input0
[    2.390285] input: Hewlett Packard HP Wireless Keyboard Kit as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.5/2-1.5:1.1/0003:0461:4DD6.0004/input/input8
[    2.415279] usb 1-1.5: New USB device found, idVendor=0a5c, idProduct=217d
[    2.415282] usb 1-1.5: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[    2.415283] usb 1-1.5: Product: HP Bluetooth Module
[    2.415284] usb 1-1.5: Manufacturer: Broadcom Corp
[    2.415286] usb 1-1.5: SerialNumber: 446D5756D09B
[    2.443137] hid-generic 0003:04D9:0169.0002: input,hidraw2: USB HID v1.10 Device [USB Keyboard] on usb-0000:00:14.0-4/input1
[    2.499112] hid-generic 0003:0461:4DD6.0004: input,hiddev0,hidraw3: USB HID v1.11 Device [Hewlett Packard HP Wireless Keyboard Kit] on usb-0000:00:1d.0-1.5/input1
[    2.500407] input: Hewlett Packard HP Wireless Keyboard Kit as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.5/2-1.5:1.2/0003:0461:4DD6.0005/input/input9
[    2.500478] hid-generic 0003:0461:4DD6.0005: input,hidraw4: USB HID v1.11 Mouse [Hewlett Packard HP Wireless Keyboard Kit] on usb-0000:00:1d.0-1.5/input2
[    2.591117] [drm] ib test on ring 5 succeeded
[    2.592030] [drm] Radeon Display Connectors
[    2.592032] [drm] Connector 0:
[    2.592032] [drm]   DP-1
[    2.592033] [drm]   HPD4
[    2.592034] [drm]   DDC: 0x6450 0x6450 0x6454 0x6454 0x6458 0x6458 0x645c 0x645c
[    2.592035] [drm]   Encoders:
[    2.592035] [drm]     DFP1: INTERNAL_UNIPHY2
[    2.592036] [drm] Connector 1:
[    2.592037] [drm]   HDMI-A-1
[    2.592037] [drm]   HPD5
[    2.592038] [drm]   DDC: 0x6470 0x6470 0x6474 0x6474 0x6478 0x6478 0x647c 0x647c
[    2.592039] [drm]   Encoders:
[    2.592039] [drm]     DFP2: INTERNAL_UNIPHY2
[    2.592040] [drm] Connector 2:
[    2.592040] [drm]   DVI-I-1
[    2.592041] [drm]   HPD1
[    2.592042] [drm]   DDC: 0x6460 0x6460 0x6464 0x6464 0x6468 0x6468 0x646c 0x646c
[    2.592042] [drm]   Encoders:
[    2.592043] [drm]     DFP3: INTERNAL_UNIPHY
[    2.592044] [drm]     CRT1: INTERNAL_KLDSCP_DAC1
[    2.722109] [drm] fb mappable at 0xE0475000
[    2.722110] [drm] vram apper at 0xE0000000
[    2.722111] [drm] size 8294400
[    2.722111] [drm] fb depth is 24
[    2.722112] [drm]    pitch is 7680
[    2.722149] fbcon: radeondrmfb (fb0) is primary device
[    2.722205] Console: switching to colour frame buffer device 240x67
[    2.722224] radeon 0000:01:00.0: fb0: radeondrmfb frame buffer device
[    2.739104] [drm] Initialized radeon 2.43.0 20080528 for 0000:01:00.0 on minor 0
[    2.919816] EXT4-fs (sda2): mounted filesystem with ordered data mode. Opts: (null)
[    3.232128] scsi 6:0:0:0: Direct-Access     WD       My Book 1110     1032 PQ: 0 ANSI: 4
[    3.232129] scsi 7:0:0:0: Direct-Access     Generic- SD/MMC           1.00 PQ: 0 ANSI: 0
[    3.232823] scsi 7:0:0:1: Direct-Access     Generic- Compact Flash    1.01 PQ: 0 ANSI: 0
[    3.232856] scsi 6:0:0:1: Enclosure         WD       SES Device       1032 PQ: 0 ANSI: 4
[    3.233517] scsi 7:0:0:2: Direct-Access     Generic- SM/xD-Picture    1.02 PQ: 0 ANSI: 0
[    3.234168] scsi 7:0:0:3: Direct-Access     Generic- MS/MS-Pro        1.03 PQ: 0 ANSI: 0 CCS
[    3.235613] sd 6:0:0:0: Attached scsi generic sg2 type 0
[    3.235765] scsi 6:0:0:1: Attached scsi generic sg3 type 13
[    3.235777] sd 6:0:0:0: [sdb] 1952151552 512-byte logical blocks: (1000 GB/931 GiB)
[    3.235942] sd 7:0:0:0: Attached scsi generic sg4 type 0
[    3.236074] sd 7:0:0:1: Attached scsi generic sg5 type 0
[    3.236203] sd 7:0:0:2: Attached scsi generic sg6 type 0
[    3.236305] sd 7:0:0:3: Attached scsi generic sg7 type 0
[    3.237217] sd 6:0:0:0: [sdb] Write Protect is off
[    3.237219] sd 6:0:0:0: [sdb] Mode Sense: 23 00 10 00
[    3.238656] sd 6:0:0:0: [sdb] No Caching mode page found
[    3.238658] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[    3.241541] sd 7:0:0:0: [sdc] Attached SCSI removable disk
[    3.242100]  sdb: sdb1
[    3.242172] sd 7:0:0:1: [sdd] Attached SCSI removable disk
[    3.242917] sd 7:0:0:2: [sde] Attached SCSI removable disk
[    3.243548] sd 7:0:0:3: [sdf] Attached SCSI removable disk
[    3.245540] sd 6:0:0:0: [sdb] Attached SCSI disk
[    3.387223] clocksource: Switched to clocksource tsc
[    3.743890] random: nonblocking pool is initialized
[    5.786316] systemd[1]: systemd 229 running in system mode. (+PAM +AUDIT +SELINUX +IMA +APPARMOR +SMACK +SYSVINIT +UTMP +LIBCRYPTSETUP +GCRYPT +GNUTLS +ACL +XZ -LZ4 +SECCOMP +BLKID +ELFUTILS +KMOD -IDN)
[    5.786438] systemd[1]: Detected architecture x86-64.
[    5.797730] systemd[1]: Set hostname to <Bayes>.
[    6.893054] systemd[1]: Listening on Journal Audit Socket.
[    6.893079] systemd[1]: Reached target User and Group Name Lookups.
[    6.893137] systemd[1]: Created slice User and Session Slice.
[    6.893165] systemd[1]: Listening on Journal Socket.
[    6.893247] systemd[1]: Set up automount Arbitrary Executable File Formats File System Automount Point.
[    6.893257] systemd[1]: Reached target Encrypted Volumes.
[    6.893299] systemd[1]: Created slice System Slice.
[    6.903320] systemd[1]: Starting Uncomplicated firewall...
[    6.903582] systemd[1]: Started Read required files in advance.
[    6.904015] systemd[1]: Starting Create list of required static device nodes for the current kernel...
[    6.904400] systemd[1]: Mounting Debug File System...
[    6.904422] systemd[1]: Reached target Slices.
[    7.091394] systemd[1]: Starting Load Kernel Modules...
[    7.093398] systemd[1]: Started Braille Device Support.
[    7.093741] systemd[1]: Mounting Huge Pages File System...
[    7.093788] systemd[1]: Listening on /dev/initctl Compatibility Named Pipe.
[    7.093837] systemd[1]: Started Forward Password Requests to Wall Directory Watch.
[    7.093881] systemd[1]: Listening on udev Control Socket.
[    7.093950] systemd[1]: Created slice system-systemd\x2dfsck.slice.
[    7.094219] systemd[1]: Starting Set console keymap...
[    7.094244] systemd[1]: Listening on fsck to fsckd communication Socket.
[    7.094282] systemd[1]: Listening on Syslog Socket.
[    7.094294] systemd[1]: Reached target Remote File Systems (Pre).
[    7.094304] systemd[1]: Reached target Remote File Systems.
[    7.094335] systemd[1]: Listening on udev Kernel Socket.
[    7.094358] systemd[1]: Listening on Journal Socket (/dev/log).
[    7.094621] systemd[1]: Starting Journal Service...
[    7.094897] systemd[1]: Mounting POSIX Message Queue File System...
[    7.095883] systemd[1]: Started Uncomplicated firewall.
[    7.096012] systemd[1]: Started Create list of required static device nodes for the current kernel.
[    7.109128] systemd[1]: Starting Create Static Device Nodes in /dev...
[    7.377698] systemd[1]: Mounted POSIX Message Queue File System.
[    7.377726] systemd[1]: Mounted Debug File System.
[    7.377744] systemd[1]: Mounted Huge Pages File System.
[    7.434488] systemd[1]: Started Journal Service.
[    7.488859] lp: driver loaded but no devices found
[    7.510897] ppdev: user-space parallel port driver
[    8.013360] wmi: Mapper loaded
[    9.361979] EXT4-fs (sda2): re-mounted. Opts: errors=remount-ro
[    9.607461] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[    9.728906] ACPI Warning: SystemIO range 0x0000000000000428-0x000000000000042F conflicts with OpRegion 0x0000000000000400-0x000000000000047F (\PMIO) (20150930/utaddress-254)
[    9.728911] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[    9.728914] ACPI Warning: SystemIO range 0x0000000000000540-0x000000000000054F conflicts with OpRegion 0x0000000000000500-0x0000000000000563 (\GPIO) (20150930/utaddress-254)
[    9.728917] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[    9.728918] ACPI Warning: SystemIO range 0x0000000000000530-0x000000000000053F conflicts with OpRegion 0x0000000000000500-0x0000000000000563 (\GPIO) (20150930/utaddress-254)
[    9.728920] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[    9.728921] ACPI Warning: SystemIO range 0x0000000000000500-0x000000000000052F conflicts with OpRegion 0x0000000000000500-0x0000000000000563 (\GPIO) (20150930/utaddress-254)
[    9.728922] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[    9.728923] lpc_ich: Resource conflict(s) found affecting gpio_ich
[    9.812509] systemd-journald[307]: Received request to flush runtime journal from PID 1
[    9.832309] AVX version of gcm_enc/dec engaged.
[    9.832311] AES CTR mode by8 optimization enabled
[    9.999272] wl: module license 'MIXED/Proprietary' taints kernel.
[    9.999275] Disabling lock debugging due to kernel taint
[   10.000593] wl: module verification failed: signature and/or required key missing - tainting kernel
[   10.001953] wl 0000:03:00.0: enabling device (0100 -> 0102)
[   10.082418] wlan0: Broadcom BCM4357 802.11 Hybrid Wireless Controller 6.30.223.248 (r487574)
[   10.196099] snd_hda_intel 0000:00:1b.0: enabling device (0100 -> 0102)
[   10.196285] snd_hda_intel 0000:01:00.1: enabling device (0100 -> 0102)
[   10.196314] snd_hda_intel 0000:01:00.1: Handle vga_switcheroo audio client
[   10.202399] snd_hda_codec_hdmi hdaudioC1D0: HDMI ATI/AMD: no speaker allocation for ELD
[   10.204009] input: HDA ATI HDMI HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card1/input10
[   10.208667] snd_hda_codec_idt hdaudioC0D0: autoconfig for 92HD73E1X5: line_outs=4 (0xc/0xf/0x10/0x11/0x0) type:speaker
[   10.208670] snd_hda_codec_idt hdaudioC0D0:    speaker_outs=0 (0x0/0x0/0x0/0x0/0x0)
[   10.208671] snd_hda_codec_idt hdaudioC0D0:    hp_outs=1 (0xa/0x0/0x0/0x0/0x0)
[   10.208672] snd_hda_codec_idt hdaudioC0D0:    mono: mono_out=0x0
[   10.208673] snd_hda_codec_idt hdaudioC0D0:    dig-out=0x22/0x0
[   10.208674] snd_hda_codec_idt hdaudioC0D0:    inputs:
[   10.208676] snd_hda_codec_idt hdaudioC0D0:      Front Mic=0xb
[   10.208677] snd_hda_codec_idt hdaudioC0D0:      Rear Mic=0xe
[   10.208678] snd_hda_codec_idt hdaudioC0D0:      Line=0xd
[   10.223666] input: HDA Intel PCH Front Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input11
[   10.223714] input: HDA Intel PCH Rear Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input12
[   10.223760] input: HDA Intel PCH Line as /devices/pci0000:00/0000:00:1b.0/sound/card0/input13
[   10.223806] input: HDA Intel PCH Speaker Front as /devices/pci0000:00/0000:00:1b.0/sound/card0/input14
[   10.223849] input: HDA Intel PCH Speaker Surround as /devices/pci0000:00/0000:00:1b.0/sound/card0/input15
[   10.223894] input: HDA Intel PCH Speaker CLFE as /devices/pci0000:00/0000:00:1b.0/sound/card0/input16
[   10.223938] input: HDA Intel PCH Speaker Side as /devices/pci0000:00/0000:00:1b.0/sound/card0/input17
[   10.223981] input: HDA Intel PCH Front Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card0/input18
[   10.312216] wl 0000:03:00.0 wlp3s0: renamed from wlan0
[   10.640843] cfg80211: World regulatory domain updated:
[   10.640845] cfg80211:  DFS Master region: unset
[   10.640846] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp), (dfs_cac_time)
[   10.640848] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A, 2000 mBm), (N/A)
[   10.640849] cfg80211:   (2457000 KHz - 2482000 KHz @ 40000 KHz), (N/A, 2000 mBm), (N/A)
[   10.640850] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (N/A, 2000 mBm), (N/A)
[   10.640851] cfg80211:   (5170000 KHz - 5250000 KHz @ 80000 KHz, 160000 KHz AUTO), (N/A, 2000 mBm), (N/A)
[   10.640852] cfg80211:   (5250000 KHz - 5330000 KHz @ 80000 KHz, 160000 KHz AUTO), (N/A, 2000 mBm), (0 s)
[   10.640853] cfg80211:   (5490000 KHz - 5730000 KHz @ 160000 KHz), (N/A, 2000 mBm), (0 s)
[   10.640854] cfg80211:   (5735000 KHz - 5835000 KHz @ 80000 KHz), (N/A, 2000 mBm), (N/A)
[   10.640856] cfg80211:   (57240000 KHz - 63720000 KHz @ 2160000 KHz), (N/A, 0 mBm), (N/A)
[   10.821205] intel_rapl: Found RAPL domain package
[   10.821208] intel_rapl: Found RAPL domain core
[   10.821210] intel_rapl: Found RAPL domain uncore
[   10.868911] ses 6:0:0:1: Attached Enclosure device
[   11.030990] Bluetooth: Core ver 2.21
[   11.031000] NET: Registered protocol family 31
[   11.031001] Bluetooth: HCI device and connection manager initialized
[   11.031004] Bluetooth: HCI socket layer initialized
[   11.031005] Bluetooth: L2CAP socket layer initialized
[   11.031009] Bluetooth: SCO socket layer initialized
[   11.152350] usbcore: registered new interface driver btusb
[   12.360376] Adding 12539900k swap on /dev/sda3.  Priority:-1 extents:1 across:12539900k FS
[   19.005426] audit: type=1400 audit(1478140010.846:2): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/snapd/snap-confine" pid=864 comm="apparmor_parser"
[   19.005432] audit: type=1400 audit(1478140010.846:3): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/snapd/snap-confine//mount-namespace-capture-helper" pid=864 comm="apparmor_parser"
[   19.036027] audit: type=1400 audit(1478140010.878:4): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/sbin/ippusbxd" pid=868 comm="apparmor_parser"
[   19.069256] audit: type=1400 audit(1478140010.910:5): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/sbin/cups-browsed" pid=866 comm="apparmor_parser"
[   19.070306] audit: type=1400 audit(1478140010.910:6): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/sbin/mysqld" pid=869 comm="apparmor_parser"
[   19.072789] audit: type=1400 audit(1478140010.914:7): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/cups/backend/cups-pdf" pid=867 comm="apparmor_parser"
[   19.072793] audit: type=1400 audit(1478140010.914:8): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/sbin/cupsd" pid=867 comm="apparmor_parser"
[   19.072797] audit: type=1400 audit(1478140010.914:9): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/sbin/cupsd//third_party" pid=867 comm="apparmor_parser"
[   19.103985] audit: type=1400 audit(1478140010.946:10): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/lightdm/lightdm-guest-session" pid=859 comm="apparmor_parser"
[   19.103990] audit: type=1400 audit(1478140010.946:11): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/lightdm/lightdm-guest-session//chromium" pid=859 comm="apparmor_parser"
[   19.815514] cgroup: new mount options do not match the existing superblock, will be ignored
[   22.366411] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   22.366413] Bluetooth: BNEP filters: protocol multicast
[   22.366416] Bluetooth: BNEP socket layer initialized
[   27.201520] IPv6: ADDRCONF(NETDEV_UP): wlp3s0: link is not ready
[   27.205192] IPv6: ADDRCONF(NETDEV_UP): enp4s0: link is not ready
[   27.207206] IPv6: ADDRCONF(NETDEV_UP): enp4s0: link is not ready
[   33.194314] vboxdrv: Found 8 processor cores
[   33.212732] vboxdrv: TSC mode is Invariant, tentative frequency 3392285966 Hz
[   33.212735] vboxdrv: Successfully loaded version 5.0.24_Ubuntu (interface 0x00240000)
[   33.215707] VBoxNetFlt: Successfully started.
[   33.218699] VBoxNetAdp: Successfully started.
[   33.221573] VBoxPciLinuxInit
[   33.223319] vboxpci: IOMMU not found (not registered)
[   36.535814] Bluetooth: RFCOMM TTY layer initialized
[   36.535821] Bluetooth: RFCOMM socket layer initialized
[   36.535825] Bluetooth: RFCOMM ver 1.11
[   50.116598] sd 6:0:0:0: [sdb] tag#0 FAILED Result: hostbyte=DID_ERROR driverbyte=DRIVER_SENSE
[   50.116602] sd 6:0:0:0: [sdb] tag#0 Sense Key : Hardware Error [current] [descriptor] 
[   50.116603] sd 6:0:0:0: [sdb] tag#0 Add. Sense: No additional sense information
[   50.116606] sd 6:0:0:0: [sdb] tag#0 CDB: ATA command pass through(16) 85 06 20 00 00 00 00 00 00 00 00 00 00 00 e5 00
[   50.223404] sd 6:0:0:0: [sdb] tag#0 FAILED Result: hostbyte=DID_ERROR driverbyte=DRIVER_SENSE
[   50.223407] sd 6:0:0:0: [sdb] tag#0 Sense Key : Hardware Error [current] [descriptor] 
[   50.223408] sd 6:0:0:0: [sdb] tag#0 Add. Sense: No additional sense information
[   50.223410] sd 6:0:0:0: [sdb] tag#0 CDB: ATA command pass through(12)/Blank a1 06 20 da 00 00 4f c2 00 b0 00 00
[  650.184434] sd 6:0:0:0: [sdb] tag#0 FAILED Result: hostbyte=DID_ERROR driverbyte=DRIVER_SENSE
[  650.184442] sd 6:0:0:0: [sdb] tag#0 Sense Key : Hardware Error [current] [descriptor] 
[  650.184448] sd 6:0:0:0: [sdb] tag#0 Add. Sense: No additional sense information
[  650.184455] sd 6:0:0:0: [sdb] tag#0 CDB: ATA command pass through(16) 85 06 20 00 00 00 00 00 00 00 00 00 00 00 e5 00
[  650.291341] sd 6:0:0:0: [sdb] tag#0 FAILED Result: hostbyte=DID_ERROR driverbyte=DRIVER_SENSE
[  650.291345] sd 6:0:0:0: [sdb] tag#0 Sense Key : Hardware Error [current] [descriptor] 
[  650.291348] sd 6:0:0:0: [sdb] tag#0 Add. Sense: No additional sense information
[  650.291351] sd 6:0:0:0: [sdb] tag#0 CDB: ATA command pass through(12)/Blank a1 06 20 da 00 00 4f c2 00 b0 00 00
```

---

### Post by tbone3421 on 2016-11-03
Maybe my question was too detailed at first.   Essentially, if a USB device is not showing up when listing  lsusb or aplay -l, what is the next step to determine why the hardware isn't recognized?  Any ideas?  Thanks!

---

