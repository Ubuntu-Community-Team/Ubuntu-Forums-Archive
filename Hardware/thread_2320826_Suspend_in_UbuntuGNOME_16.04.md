---
title: "Suspend in UbuntuGNOME 16.04"
date: 2016-04-17
forum: Hardware
---

### Post by james208 on 2016-04-17
I apologize off the bat if this isn't the right place. I'd try to file a bug instead if I knew what package it was and how to file one. I've search these forums and the internet in general for the last couple of hours without much luck. 

I installed the final freeze of 16.04 LTS UbuntuGNOME on my computer today as I had freeze issues with both 15.04 and 15.10. They appear to be gone but I have one remaining problem- my laptop will not properly go into or come out of suspend. Suspend worked perfectly in 15.10 but does not in 16.04. 

I have trying both clicking the suspend button (from the gnome extension that gives you a suspend button), running systemctl suspend, and installing pm-utils and running pm-suspend. All cause the same problem. The screen goes black, but rather than the power light flashing and it waking up on keypress, the power button and all other lights on when I hit the button (caps lock, mute) still on and the system refuses to wake up, not by mouse, any key, hitting the power button once, plugging in power or a usb mouse, nothing. I can't find anything in my logs afterwards, but I don't really know what to look for. The laptop is an HP 11.6 x360 convertible with a braswell quad core Pentium. 

dmesg:

```
dmesg[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Initializing cgroup subsys cpuacct
[    0.000000] Linux version 4.4.0-18-generic (buildd@lcy01-05) (gcc version 5.3.1 20160405 (Ubuntu 5.3.1-13ubuntu4) ) #34-Ubuntu SMP Wed Apr 6 14:01:02 UTC 2016 (Ubuntu 4.4.0-18.34-generic 4.4.6)
[    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-4.4.0-18-generic.efi.signed root=UUID=3cd78087-95c0-4e86-b53a-2ef7f9165518 ro quiet splash vt.handoff=7
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   Centaur CentaurHauls
[    0.000000] x86/fpu: Legacy x87 FPU detected.
[    0.000000] x86/fpu: Using 'lazy' FPU context switches.
[    0.000000] e820: BIOS-provided physical RAM map:
[    0.000000] BIOS-e820: [mem 0x0000000000000000-0x000000000006efff] usable
[    0.000000] BIOS-e820: [mem 0x000000000006f000-0x000000000006ffff] ACPI NVS
[    0.000000] BIOS-e820: [mem 0x0000000000070000-0x0000000000085fff] usable
[    0.000000] BIOS-e820: [mem 0x0000000000086000-0x000000000009ffff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000000100000-0x000000001fffffff] usable
[    0.000000] BIOS-e820: [mem 0x0000000020000000-0x00000000201fffff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000020200000-0x0000000076252fff] usable
[    0.000000] BIOS-e820: [mem 0x0000000076253000-0x0000000076c52fff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000076c53000-0x0000000076e52fff] ACPI NVS
[    0.000000] BIOS-e820: [mem 0x0000000076e53000-0x0000000076e92fff] ACPI data
[    0.000000] BIOS-e820: [mem 0x0000000076e93000-0x0000000077ffffff] usable
[    0.000000] BIOS-e820: [mem 0x00000000e00f8000-0x00000000e00f8fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fed01000-0x00000000fed01fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000ffa00000-0x00000000ffffffff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000100000000-0x000000017fffffff] usable
[    0.000000] NX (Execute Disable) protection: active
[    0.000000] e820: update [mem 0x70e1a018-0x70e2a057] usable ==> usable
[    0.000000] extended physical RAM map:
[    0.000000] reserve setup_data: [mem 0x0000000000000000-0x000000000006efff] usable
[    0.000000] reserve setup_data: [mem 0x000000000006f000-0x000000000006ffff] ACPI NVS
[    0.000000] reserve setup_data: [mem 0x0000000000070000-0x0000000000085fff] usable
[    0.000000] reserve setup_data: [mem 0x0000000000086000-0x000000000009ffff] reserved
[    0.000000] reserve setup_data: [mem 0x0000000000100000-0x000000001fffffff] usable
[    0.000000] reserve setup_data: [mem 0x0000000020000000-0x00000000201fffff] reserved
[    0.000000] reserve setup_data: [mem 0x0000000020200000-0x0000000070e1a017] usable
[    0.000000] reserve setup_data: [mem 0x0000000070e1a018-0x0000000070e2a057] usable
[    0.000000] reserve setup_data: [mem 0x0000000070e2a058-0x0000000076252fff] usable
[    0.000000] reserve setup_data: [mem 0x0000000076253000-0x0000000076c52fff] reserved
[    0.000000] reserve setup_data: [mem 0x0000000076c53000-0x0000000076e52fff] ACPI NVS
[    0.000000] reserve setup_data: [mem 0x0000000076e53000-0x0000000076e92fff] ACPI data
[    0.000000] reserve setup_data: [mem 0x0000000076e93000-0x0000000077ffffff] usable
[    0.000000] reserve setup_data: [mem 0x00000000e00f8000-0x00000000e00f8fff] reserved
[    0.000000] reserve setup_data: [mem 0x00000000fed01000-0x00000000fed01fff] reserved
[    0.000000] reserve setup_data: [mem 0x00000000ffa00000-0x00000000ffffffff] reserved
[    0.000000] reserve setup_data: [mem 0x0000000100000000-0x000000017fffffff] usable
[    0.000000] efi: EFI v2.40 by INSYDE Corp.
[    0.000000] efi:  ACPI 2.0=0x76e92014  SMBIOS=0x765e0000  ESRT=0x765def18 
[    0.000000] esrt: Reserving ESRT space from 0x00000000765def18 to 0x00000000765def50.
[    0.000000] SMBIOS 2.8 present.
[    0.000000] DMI: HP HP Pavilion x360 Convertible/8074, BIOS F.35 08/20/2015
[    0.000000] e820: update [mem 0x00000000-0x00000fff] usable ==> reserved
[    0.000000] e820: remove [mem 0x000a0000-0x000fffff] usable
[    0.000000] e820: last_pfn = 0x180000 max_arch_pfn = 0x400000000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 0FFC00000 mask FFFC00000 write-protect
[    0.000000]   1 base 0FFA00000 mask FFFE00000 write-protect
[    0.000000]   2 base 000000000 mask F80000000 write-back
[    0.000000]   3 base 07C000000 mask FFC000000 uncachable
[    0.000000]   4 base 07BC00000 mask FFFC00000 uncachable
[    0.000000]   5 base 100000000 mask F80000000 write-back
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] x86/PAT: Configuration [0-7]: WB  WC  UC- UC  WB  WC  UC- WT  
[    0.000000] e820: last_pfn = 0x78000 max_arch_pfn = 0x400000000
[    0.000000] Scanning 1 areas for low memory corruption
[    0.000000] Base memory trampoline at [ffff880000080000] 80000 size 24576
[    0.000000] BRK [0x021fe000, 0x021fefff] PGTABLE
[    0.000000] BRK [0x021ff000, 0x021fffff] PGTABLE
[    0.000000] BRK [0x02200000, 0x02200fff] PGTABLE
[    0.000000] BRK [0x02201000, 0x02201fff] PGTABLE
[    0.000000] BRK [0x02202000, 0x02202fff] PGTABLE
[    0.000000] BRK [0x02203000, 0x02203fff] PGTABLE
[    0.000000] RAMDISK: [mem 0x3ddb1000-0x3fffafff]
[    0.000000] ACPI: Early table checksum verification disabled
[    0.000000] ACPI: RSDP 0x0000000076E92014 000024 (v02 HPQOEM)
[    0.000000] ACPI: XSDT 0x0000000076E92120 0000AC (v01 HPQOEM SLIC-MPC 00000003 HP   01000013)
[    0.000000] ACPI: FACP 0x0000000076E88000 00010C (v05 HPQOEM SLIC-MPC 00000003 HP   00040000)
[    0.000000] ACPI: DSDT 0x0000000076E70000 013064 (v02 HPQOEM SLIC-MPC 00000003 ACPI 00040000)
[    0.000000] ACPI: FACS 0x0000000076E4E000 000040
[    0.000000] ACPI: UEFI 0x0000000076E91000 000236 (v01 HPQOEM INSYDE   00000001 HP   00040000)
[    0.000000] ACPI: MSDM 0x0000000076E90000 000055 (v03 HPQOEM SLIC-MPC 00000001 HP   00040000)
[    0.000000] ACPI: TCPA 0x0000000076E8F000 000032 (v02 HPQOEM INSYDE   00000000 HP   00040000)
[    0.000000] ACPI: UEFI 0x0000000076E8E000 000042 (v01 HPQOEM INSYDE   00000000 HP   00040000)
[    0.000000] ACPI: SSDT 0x0000000076E89000 00450A (v01 HPQOEM INSYDE   00001000 ACPI 00040000)
[    0.000000] ACPI: APIC 0x0000000076E87000 000084 (v03 HPQOEM SLIC-MPC 00000003 HP   00040000)
[    0.000000] ACPI: MCFG 0x0000000076E86000 00003C (v01 HPQOEM INSYDE   00000003 HP   00040000)
[    0.000000] ACPI: SSDT 0x0000000076E85000 0005B3 (v01 HPQOEM CpuDptf  00000003 ACPI 00040000)
[    0.000000] ACPI: SSDT 0x0000000076E84000 000E2C (v01 HPQOEM DptfTab  00000003 ACPI 00040000)
[    0.000000] ACPI: SSDT 0x0000000076E6F000 000763 (v01 HPQOEM INSYDE   00003000 ACPI 00040000)
[    0.000000] ACPI: SSDT 0x0000000076E6E000 000290 (v01 HPQOEM INSYDE   00003000 ACPI 00040000)
[    0.000000] ACPI: SSDT 0x0000000076E6D000 00017A (v01 HPQOEM INSYDE   00003000 ACPI 00040000)
[    0.000000] ACPI: SSDT 0x0000000076E6C000 000432 (v01 HPQOEM INSYDE   00001000 ACPI 00040000)
[    0.000000] ACPI: TPM2 0x0000000076E6B000 000034 (v03 HPQOEM INSYDE   00000000 HP   00040000)
[    0.000000] ACPI: FPDT 0x0000000076E6A000 000044 (v01 HPQOEM SLIC-MPC 00000002 HP   00040000)
[    0.000000] ACPI: BGRT 0x0000000076E69000 000038 (v01 HPQOEM INSYDE   00000001 HP   00040000)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at [mem 0x0000000000000000-0x000000017fffffff]
[    0.000000] NODE_DATA(0) allocated [mem 0x17fff9000-0x17fffdfff]
[    0.000000] Zone ranges:
[    0.000000]   DMA      [mem 0x0000000000001000-0x0000000000ffffff]
[    0.000000]   DMA32    [mem 0x0000000001000000-0x00000000ffffffff]
[    0.000000]   Normal   [mem 0x0000000100000000-0x000000017fffffff]
[    0.000000]   Device   empty
[    0.000000] Movable zone start for each node
[    0.000000] Early memory node ranges
[    0.000000]   node   0: [mem 0x0000000000001000-0x000000000006efff]
[    0.000000]   node   0: [mem 0x0000000000070000-0x0000000000085fff]
[    0.000000]   node   0: [mem 0x0000000000100000-0x000000001fffffff]
[    0.000000]   node   0: [mem 0x0000000020200000-0x0000000076252fff]
[    0.000000]   node   0: [mem 0x0000000076e93000-0x0000000077ffffff]
[    0.000000]   node   0: [mem 0x0000000100000000-0x000000017fffffff]
[    0.000000] Initmem setup node 0 [mem 0x0000000000001000-0x000000017fffffff]
[    0.000000] On node 0 totalpages: 1012036
[    0.000000]   DMA zone: 64 pages used for memmap
[    0.000000]   DMA zone: 21 pages reserved
[    0.000000]   DMA zone: 3972 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 7559 pages used for memmap
[    0.000000]   DMA32 zone: 483776 pages, LIFO batch:31
[    0.000000]   Normal zone: 8192 pages used for memmap
[    0.000000]   Normal zone: 524288 pages, LIFO batch:31
[    0.000000] tboot: non-0 tboot_addr but it is not of type E820_RESERVED
[    0.000000] Reserving Intel graphics stolen memory at 0x7c800000-0x7e7fffff
[    0.000000] ACPI: PM-Timer IO Port: 0x408
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high level lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x02] high level lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x03] high level lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x04] high level lint[0x1])
[    0.000000] IOAPIC[0]: apic_id 1, version 32, address 0xfec00000, GSI 0-114
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] smpboot: Allowing 4 CPUs, 0 hotplug CPUs
[    0.000000] PM: Registered nosave memory: [mem 0x00000000-0x00000fff]
[    0.000000] PM: Registered nosave memory: [mem 0x0006f000-0x0006ffff]
[    0.000000] PM: Registered nosave memory: [mem 0x00086000-0x0009ffff]
[    0.000000] PM: Registered nosave memory: [mem 0x000a0000-0x000fffff]
[    0.000000] PM: Registered nosave memory: [mem 0x20000000-0x201fffff]
[    0.000000] PM: Registered nosave memory: [mem 0x70e1a000-0x70e1afff]
[    0.000000] PM: Registered nosave memory: [mem 0x70e2a000-0x70e2afff]
[    0.000000] PM: Registered nosave memory: [mem 0x76253000-0x76c52fff]
[    0.000000] PM: Registered nosave memory: [mem 0x76c53000-0x76e52fff]
[    0.000000] PM: Registered nosave memory: [mem 0x76e53000-0x76e92fff]
[    0.000000] PM: Registered nosave memory: [mem 0x78000000-0x7c7fffff]
[    0.000000] PM: Registered nosave memory: [mem 0x7c800000-0x7e7fffff]
[    0.000000] PM: Registered nosave memory: [mem 0x7e800000-0xe00f7fff]
[    0.000000] PM: Registered nosave memory: [mem 0xe00f8000-0xe00f8fff]
[    0.000000] PM: Registered nosave memory: [mem 0xe00f9000-0xfed00fff]
[    0.000000] PM: Registered nosave memory: [mem 0xfed01000-0xfed01fff]
[    0.000000] PM: Registered nosave memory: [mem 0xfed02000-0xff9fffff]
[    0.000000] PM: Registered nosave memory: [mem 0xffa00000-0xffffffff]
[    0.000000] e820: [mem 0x7e800000-0xe00f7fff] available for PCI devices
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] clocksource: refined-jiffies: mask: 0xffffffff max_cycles: 0xffffffff, max_idle_ns: 7645519600211568 ns
[    0.000000] setup_percpu: NR_CPUS:256 nr_cpumask_bits:256 nr_cpu_ids:4 nr_node_ids:1
[    0.000000] PERCPU: Embedded 33 pages/cpu @ffff88017fc00000 s98008 r8192 d28968 u524288
[    0.000000] pcpu-alloc: s98008 r8192 d28968 u524288 alloc=1*2097152
[    0.000000] pcpu-alloc: [0] 0 1 2 3 
[    0.000000] Built 1 zonelists in Node order, mobility grouping on.  Total pages: 996200
[    0.000000] Policy zone: Normal
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-4.4.0-18-generic.efi.signed root=UUID=3cd78087-95c0-4e86-b53a-2ef7f9165518 ro quiet splash vt.handoff=7
[    0.000000] PID hash table entries: 4096 (order: 3, 32768 bytes)
[    0.000000] Calgary: detecting Calgary via BIOS EBDA area
[    0.000000] Calgary: Unable to locate Rio Grande table in EBDA - bailing!
[    0.000000] Memory: 3825748K/4048144K available (8355K kernel code, 1278K rwdata, 3920K rodata, 1476K init, 1292K bss, 222396K reserved, 0K cma-reserved)
[    0.000000] SLUB: HWalign=64, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000]     Build-time adjustment of leaf fanout to 64.
[    0.000000]     RCU restricting CPUs from NR_CPUS=256 to nr_cpu_ids=4.
[    0.000000] RCU: Adjusting geometry for rcu_fanout_leaf=64, nr_cpu_ids=4
[    0.000000] NR_IRQS:16640 nr_irqs:1024 16
[    0.000000] vt handoff: transparent VT on vt#7
[    0.000000] Console: colour dummy device 80x25
[    0.000000] console [tty0] enabled
[    0.000000] tsc: PIT calibration matches PMTIMER. 1 loops
[    0.000000] tsc: Detected 1599.269 MHz processor
[    0.000049] Calibrating delay loop (skipped), value calculated using timer frequency.. 3198.53 BogoMIPS (lpj=6397076)
[    0.000055] pid_max: default: 32768 minimum: 301
[    0.000071] ACPI: Core revision 20150930
[    0.041729] ACPI: 8 ACPI AML tables successfully acquired and loaded
[    0.052186] Security Framework initialized
[    0.052195] Yama: becoming mindful.
[    0.052234] AppArmor: AppArmor initialized
[    0.052849] Dentry cache hash table entries: 524288 (order: 10, 4194304 bytes)
[    0.055188] Inode-cache hash table entries: 262144 (order: 9, 2097152 bytes)
[    0.056243] Mount-cache hash table entries: 8192 (order: 4, 65536 bytes)
[    0.056264] Mountpoint-cache hash table entries: 8192 (order: 4, 65536 bytes)
[    0.056738] Initializing cgroup subsys io
[    0.056751] Initializing cgroup subsys memory
[    0.056768] Initializing cgroup subsys devices
[    0.056775] Initializing cgroup subsys freezer
[    0.056782] Initializing cgroup subsys net_cls
[    0.056787] Initializing cgroup subsys perf_event
[    0.056794] Initializing cgroup subsys net_prio
[    0.056799] Initializing cgroup subsys hugetlb
[    0.056808] Initializing cgroup subsys pids
[    0.056841] CPU: Physical Processor ID: 0
[    0.056845] CPU: Processor Core ID: 0
[    0.056852] ENERGY_PERF_BIAS: Set to 'normal', was 'performance'
[    0.056855] ENERGY_PERF_BIAS: View and update with x86_energy_perf_policy(8)
[    0.062318] mce: CPU supports 6 MCE banks
[    0.062333] CPU0: Thermal monitoring enabled (TM1)
[    0.062341] process: using mwait in idle threads
[    0.062348] Last level iTLB entries: 4KB 48, 2MB 0, 4MB 0
[    0.062352] Last level dTLB entries: 4KB 256, 2MB 16, 4MB 16, 1GB 0
[    0.062818] Freeing SMP alternatives memory: 28K (ffffffff820b2000 - ffffffff820b9000)
[    0.071351] ftrace: allocating 31877 entries in 125 pages
[    0.094559] smpboot: Max logical packages: 1
[    0.096562] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.136282] TSC deadline timer enabled
[    0.136288] smpboot: CPU0: Intel(R) Pentium(R) CPU  N3700  @ 1.60GHz (family: 0x6, model: 0x4c, stepping: 0x3)
[    0.136325] Performance Events: PEBS fmt2+, 8-deep LBR, Silvermont events, full-width counters, Intel PMU driver.
[    0.136345] ... version:                3
[    0.136348] ... bit width:              40
[    0.136350] ... generic registers:      2
[    0.136354] ... value mask:             000000ffffffffff
[    0.136356] ... max period:             000000ffffffffff
[    0.136359] ... fixed-purpose events:   3
[    0.136361] ... event mask:             0000000700000003
[    0.138273] x86: Booting SMP configuration:
[    0.138280] .... node  #0, CPUs:      #1
[    0.146102] NMI watchdog: enabled on all CPUs, permanently consumes one hw-PMU counter.
[    0.146374]  #2 #3
[    0.161752] x86: Booted up 1 node, 4 CPUs
[    0.161758] smpboot: Total of 4 processors activated (12794.15 BogoMIPS)
[    0.162949] devtmpfs: initialized
[    0.171468] evm: security.selinux
[    0.171473] evm: security.SMACK64
[    0.171475] evm: security.SMACK64EXEC
[    0.171478] evm: security.SMACK64TRANSMUTE
[    0.171480] evm: security.SMACK64MMAP
[    0.171482] evm: security.ima
[    0.171484] evm: security.capability
[    0.171638] PM: Registering ACPI NVS region [mem 0x0006f000-0x0006ffff] (4096 bytes)
[    0.171643] PM: Registering ACPI NVS region [mem 0x76c53000-0x76e52fff] (2097152 bytes)
[    0.171901] clocksource: jiffies: mask: 0xffffffff max_cycles: 0xffffffff, max_idle_ns: 7645041785100000 ns
[    0.172093] pinctrl core: initialized pinctrl subsystem
[    0.172357] RTC time:  0:44:47, date: 01/01/15
[    0.172702] NET: Registered protocol family 16
[    0.186476] cpuidle: using governor ladder
[    0.198492] cpuidle: using governor menu
[    0.198500] PCCT header not found.
[    0.198695] ACPI: bus type PCI registered
[    0.198702] acpiphp: ACPI Hot Plug PCI Controller Driver version: 0.5
[    0.198871] PCI: MMCONFIG for domain 0000 [bus 00-3f] at [mem 0xe0000000-0xe3ffffff] (base 0xe0000000)
[    0.198877] PCI: not using MMCONFIG
[    0.198881] PCI: Using configuration type 1 for base access
[    0.211499] ACPI: Added _OSI(Module Device)
[    0.211505] ACPI: Added _OSI(Processor Device)
[    0.211508] ACPI: Added _OSI(3.0 _SCP Extensions)
[    0.211511] ACPI: Added _OSI(Processor Aggregator Device)
[    0.234043] ACPI: Dynamic OEM Table Load:
[    0.234064] ACPI: SSDT 0xFFFF88017AA8A000 0005D1 (v01 PmRef  Cpu0Ist  00003000 INTL 20130117)
[    0.235723] ACPI: Dynamic OEM Table Load:
[    0.235738] ACPI: SSDT 0xFFFF88017AA96800 0003A5 (v01 PmRef  Cpu0Cst  00003001 INTL 20130117)
[    0.237839] ACPI: Dynamic OEM Table Load:
[    0.237853] ACPI: SSDT 0xFFFF88017AB12000 00015F (v01 PmRef  ApIst    00003000 INTL 20130117)
[    0.239434] ACPI: Dynamic OEM Table Load:
[    0.239447] ACPI: SSDT 0xFFFF88017AAA5780 00008D (v01 PmRef  ApCst    00003000 INTL 20130117)
[    0.242748] ACPI : EC: EC started
[    0.469470] ACPI: Interpreter enabled
[    0.469490] ACPI Exception: AE_NOT_FOUND, While evaluating Sleep State [\_S1_] (20150930/hwxface-580)
[    0.469503] ACPI Exception: AE_NOT_FOUND, While evaluating Sleep State [\_S2_] (20150930/hwxface-580)
[    0.469548] ACPI: (supports S0 S3 S4 S5)
[    0.469553] ACPI: Using IOAPIC for interrupt routing
[    0.469633] PCI: MMCONFIG for domain 0000 [bus 00-3f] at [mem 0xe0000000-0xe3ffffff] (base 0xe0000000)
[    0.472166] PCI: MMCONFIG at [mem 0xe0000000-0xe3ffffff] reserved in ACPI motherboard resources
[    0.472191] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[    0.475668] ACPI: Power Resource [USBC] (on)
[    0.484269] ACPI: Power Resource [CLK0] (on)
[    0.484381] ACPI: Power Resource [CLK1] (on)
[    0.492694] ACPI: Power Resource [ID3C] (on)
[    0.501164] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
[    0.501179] acpi PNP0A08:00: _OSC: OS supports [ExtendedConfig ASPM ClockPM Segments MSI]
[    0.501280] \_SB_.PCI0:_OSC invalid UUID
[    0.501284] _OSC request data:1 1f 0 
[    0.501294] acpi PNP0A08:00: _OSC failed (AE_ERROR); disabling ASPM
[    0.501323] acpi PNP0A08:00: [Firmware Info]: MMCONFIG for domain 0000 [bus 00-3f] only partially covers this bridge
[    0.502073] PCI host bridge to bus 0000:00
[    0.502081] pci_bus 0000:00: root bus resource [io  0x0070-0x0077]
[    0.502086] pci_bus 0000:00: root bus resource [io  0x0000-0x006f window]
[    0.502091] pci_bus 0000:00: root bus resource [io  0x0078-0x0cf7 window]
[    0.502096] pci_bus 0000:00: root bus resource [io  0x0d00-0xffff window]
[    0.502100] pci_bus 0000:00: root bus resource [mem 0x000a0000-0x000bffff window]
[    0.502105] pci_bus 0000:00: root bus resource [mem 0x000c0000-0x000dffff window]
[    0.502109] pci_bus 0000:00: root bus resource [mem 0x000e0000-0x000fffff window]
[    0.502114] pci_bus 0000:00: root bus resource [mem 0x80000000-0xdfffffff window]
[    0.502119] pci_bus 0000:00: root bus resource [mem 0xfe800000-0xfe80ffff window]
[    0.502124] pci_bus 0000:00: root bus resource [bus 00-ff]
[    0.502140] pci 0000:00:00.0: [8086:2280] type 00 class 0x060000
[    0.502459] pci 0000:00:02.0: [8086:22b1] type 00 class 0x030000
[    0.502499] pci 0000:00:02.0: reg 0x10: [mem 0x90000000-0x90ffffff 64bit]
[    0.502516] pci 0000:00:02.0: reg 0x18: [mem 0x80000000-0x8fffffff 64bit pref]
[    0.502529] pci 0000:00:02.0: reg 0x20: [io  0x3000-0x303f]
[    0.502786] pci 0000:00:0b.0: [8086:22dc] type 00 class 0x118000
[    0.502823] pci 0000:00:0b.0: reg 0x10: [mem 0x91618000-0x91618fff 64bit]
[    0.503121] pci 0000:00:13.0: [8086:22a3] type 00 class 0x010601
[    0.503202] pci 0000:00:13.0: reg 0x20: [io  0x3060-0x307f]
[    0.503216] pci 0000:00:13.0: reg 0x24: [mem 0x91621000-0x916217ff]
[    0.503273] pci 0000:00:13.0: PME# supported from D3hot
[    0.503493] pci 0000:00:14.0: [8086:22b5] type 00 class 0x0c0330
[    0.503543] pci 0000:00:14.0: reg 0x10: [mem 0x91600000-0x9160ffff 64bit]
[    0.503639] pci 0000:00:14.0: PME# supported from D3hot D3cold
[    0.503805] pci 0000:00:14.0: System wakeup disabled by ACPI
[    0.503916] pci 0000:00:1a.0: [8086:2298] type 00 class 0x108000
[    0.503956] pci 0000:00:1a.0: reg 0x10: [mem 0x91500000-0x915fffff]
[    0.503971] pci 0000:00:1a.0: reg 0x14: [mem 0x91400000-0x914fffff]
[    0.504058] pci 0000:00:1a.0: PME# supported from D0 D3hot
[    0.504365] pci 0000:00:1b.0: [8086:2284] type 00 class 0x040300
[    0.504418] pci 0000:00:1b.0: reg 0x10: [mem 0x91610000-0x91613fff 64bit]
[    0.504520] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    0.504667] pci 0000:00:1b.0: System wakeup disabled by ACPI
[    0.504768] pci 0000:00:1c.0: [8086:22c8] type 01 class 0x060400
[    0.504886] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.505017] pci 0000:00:1c.0: System wakeup disabled by ACPI
[    0.505115] pci 0000:00:1c.1: [8086:22ca] type 01 class 0x060400
[    0.505233] pci 0000:00:1c.1: PME# supported from D0 D3hot D3cold
[    0.505366] pci 0000:00:1c.1: System wakeup disabled by ACPI
[    0.505464] pci 0000:00:1c.2: [8086:22cc] type 01 class 0x060400
[    0.505580] pci 0000:00:1c.2: PME# supported from D0 D3hot D3cold
[    0.505713] pci 0000:00:1c.2: System wakeup disabled by ACPI
[    0.505813] pci 0000:00:1c.3: [8086:22ce] type 01 class 0x060400
[    0.505928] pci 0000:00:1c.3: PME# supported from D0 D3hot D3cold
[    0.506060] pci 0000:00:1c.3: System wakeup disabled by ACPI
[    0.506166] pci 0000:00:1f.0: [8086:229c] type 00 class 0x060100
[    0.506503] pci 0000:00:1f.3: [8086:2292] type 00 class 0x0c0500
[    0.506585] pci 0000:00:1f.3: reg 0x10: [mem 0x91619000-0x9161901f]
[    0.506705] pci 0000:00:1f.3: reg 0x20: [io  0x3040-0x305f]
[    0.507156] pci 0000:00:1c.0: PCI bridge to [bus 01]
[    0.507357] pci 0000:02:00.0: [10ec:8136] type 00 class 0x020000
[    0.507541] pci 0000:02:00.0: reg 0x10: [io  0x2000-0x20ff]
[    0.507659] pci 0000:02:00.0: reg 0x18: [mem 0x91300000-0x91300fff 64bit]
[    0.507738] pci 0000:02:00.0: reg 0x20: [mem 0x91000000-0x91003fff 64bit pref]
[    0.508074] pci 0000:02:00.0: supports D1 D2
[    0.508079] pci 0000:02:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.510888] pci 0000:02:00.0: System wakeup disabled by ACPI
[    0.518942] pci 0000:00:1c.1: PCI bridge to [bus 02]
[    0.518952] pci 0000:00:1c.1:   bridge window [io  0x2000-0x2fff]
[    0.518959] pci 0000:00:1c.1:   bridge window [mem 0x91300000-0x913fffff]
[    0.518970] pci 0000:00:1c.1:   bridge window [mem 0x91000000-0x910fffff 64bit pref]
[    0.519211] pci 0000:03:00.0: [8086:3165] type 00 class 0x028000
[    0.519508] pci 0000:03:00.0: reg 0x10: [mem 0x91200000-0x91201fff 64bit]
[    0.520220] pci 0000:03:00.0: PME# supported from D0 D3hot D3cold
[    0.520438] pci 0000:03:00.0: System wakeup disabled by ACPI
[    0.526967] pci 0000:00:1c.2: PCI bridge to [bus 03]
[    0.526979] pci 0000:00:1c.2:   bridge window [mem 0x91200000-0x912fffff]
[    0.527126] pci 0000:04:00.0: [10ec:5229] type 00 class 0xff0000
[    0.527190] pci 0000:04:00.0: reg 0x10: [mem 0x91100000-0x91100fff]
[    0.527380] pci 0000:04:00.0: supports D1 D2
[    0.527385] pci 0000:04:00.0: PME# supported from D1 D2 D3hot
[    0.527467] pci 0000:04:00.0: System wakeup disabled by ACPI
[    0.534935] pci 0000:00:1c.3: PCI bridge to [bus 04]
[    0.534947] pci 0000:00:1c.3:   bridge window [mem 0x91100000-0x911fffff]
[    0.541851] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 10 11 12 14 15) *0, disabled.
[    0.542021] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 10 11 12 14 15) *0, disabled.
[    0.542181] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 10 11 12 14 15) *0, disabled.
[    0.542341] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 10 11 12 14 15) *0, disabled.
[    0.542498] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 10 11 12 14 15) *0, disabled.
[    0.542655] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 10 11 12 14 15) *0, disabled.
[    0.542812] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 10 11 12 14 15) *0, disabled.
[    0.542985] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 10 11 12 14 15) *0, disabled.
[    0.545012] ACPI: Enabled 4 GPEs in block 00 to 3F
[    0.545131] ACPI : EC: GPE = 0x16, I/O: command/status = 0x66, data = 0x62
[    0.545474] vgaarb: setting as boot device: PCI:0000:00:02.0
[    0.545483] vgaarb: device added: PCI:0000:00:02.0,decodes=io+mem,owns=io+mem,locks=none
[    0.545493] vgaarb: loaded
[    0.545498] vgaarb: bridge control possible 0000:00:02.0
[    0.546182] SCSI subsystem initialized
[    0.546319] libata version 3.00 loaded.
[    0.546377] ACPI: bus type USB registered
[    0.546426] usbcore: registered new interface driver usbfs
[    0.546450] usbcore: registered new interface driver hub
[    0.546500] usbcore: registered new device driver usb
[    0.547020] PCI: Using ACPI for IRQ routing
[    0.549605] PCI: pci_cache_line_size set to 64 bytes
[    0.549733] e820: reserve RAM buffer [mem 0x0006f000-0x0006ffff]
[    0.549737] e820: reserve RAM buffer [mem 0x00086000-0x0008ffff]
[    0.549740] e820: reserve RAM buffer [mem 0x70e1a018-0x73ffffff]
[    0.549743] e820: reserve RAM buffer [mem 0x76253000-0x77ffffff]
[    0.550028] NetLabel: Initializing
[    0.550032] NetLabel:  domain hash size = 128
[    0.550035] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.550060] NetLabel:  unlabeled traffic allowed by default
[    0.550299] clocksource: Switched to clocksource refined-jiffies
[    0.564732] AppArmor: AppArmor Filesystem Enabled
[    0.564911] pnp: PnP ACPI init
[    0.565132] system 00:00: [io  0x0680-0x069f] has been reserved
[    0.565138] system 00:00: [io  0x0400-0x047f] has been reserved
[    0.565143] system 00:00: [io  0x0500-0x05fe] has been reserved
[    0.565153] system 00:00: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.565417] pnp 00:01: Plug and Play ACPI device, IDs HPQ8001 PNP0303 (active)
[    0.565652] pnp 00:02: Plug and Play ACPI device, IDs SYN1ee9 SYN1e00 SYN0002 PNP0f13 (active)
[    0.568350] system 00:03: [mem 0x91620000-0x91620fff] has been reserved
[    0.568359] system 00:03: [mem 0x9161e000-0x9161efff] has been reserved
[    0.568364] system 00:03: [mem 0x9161c000-0x9161cfff] has been reserved
[    0.568369] system 00:03: [mem 0x9161a000-0x9161afff] has been reserved
[    0.568377] system 00:03: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.568587] system 00:04: [mem 0xe0000000-0xefffffff] could not be reserved
[    0.568593] system 00:04: [mem 0xfea00000-0xfeafffff] has been reserved
[    0.568600] system 00:04: [mem 0xfed01000-0xfed01fff] has been reserved
[    0.568605] system 00:04: [mem 0xfed03000-0xfed03fff] has been reserved
[    0.568610] system 00:04: [mem 0xfed06000-0xfed06fff] has been reserved
[    0.568615] system 00:04: [mem 0xfed08000-0xfed09fff] has been reserved
[    0.568620] system 00:04: [mem 0xfed80000-0xfedbffff] could not be reserved
[    0.568626] system 00:04: [mem 0xfed1c000-0xfed1cfff] has been reserved
[    0.568631] system 00:04: [mem 0xfee00000-0xfeefffff] has been reserved
[    0.568638] system 00:04: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.569012] pnp 00:05: Plug and Play ACPI device, IDs PNP0b00 (active)
[    0.569561] pnp: PnP ACPI: found 6 devices
[    0.579188] clocksource: acpi_pm: mask: 0xffffff max_cycles: 0xffffff, max_idle_ns: 2085701024 ns
[    0.579223] clocksource: Switched to clocksource acpi_pm
[    0.579260] pci 0000:00:1c.0: bridge window [io  0x1000-0x0fff] to [bus 01] add_size 1000
[    0.579268] pci 0000:00:1c.0: bridge window [mem 0x00100000-0x000fffff 64bit pref] to [bus 01] add_size 200000 add_align 100000
[    0.579274] pci 0000:00:1c.0: bridge window [mem 0x00100000-0x000fffff] to [bus 01] add_size 200000 add_align 100000
[    0.579322] pci 0000:00:1c.0: res[14]=[mem 0x00100000-0x000fffff] res_to_dev_res add_size 200000 min_align 100000
[    0.579328] pci 0000:00:1c.0: res[14]=[mem 0x00100000-0x002fffff] res_to_dev_res add_size 200000 min_align 100000
[    0.579334] pci 0000:00:1c.0: res[15]=[mem 0x00100000-0x000fffff 64bit pref] res_to_dev_res add_size 200000 min_align 100000
[    0.579339] pci 0000:00:1c.0: res[15]=[mem 0x00100000-0x002fffff 64bit pref] res_to_dev_res add_size 200000 min_align 100000
[    0.579345] pci 0000:00:1c.0: res[13]=[io  0x1000-0x0fff] res_to_dev_res add_size 1000 min_align 1000
[    0.579350] pci 0000:00:1c.0: res[13]=[io  0x1000-0x1fff] res_to_dev_res add_size 1000 min_align 1000
[    0.579364] pci 0000:00:1c.0: BAR 14: assigned [mem 0x91700000-0x918fffff]
[    0.579377] pci 0000:00:1c.0: BAR 15: assigned [mem 0x91900000-0x91afffff 64bit pref]
[    0.579385] pci 0000:00:1c.0: BAR 13: assigned [io  0x1000-0x1fff]
[    0.579393] pci 0000:00:1c.0: PCI bridge to [bus 01]
[    0.579401] pci 0000:00:1c.0:   bridge window [io  0x1000-0x1fff]
[    0.579411] pci 0000:00:1c.0:   bridge window [mem 0x91700000-0x918fffff]
[    0.579419] pci 0000:00:1c.0:   bridge window [mem 0x91900000-0x91afffff 64bit pref]
[    0.579430] pci 0000:00:1c.1: PCI bridge to [bus 02]
[    0.579435] pci 0000:00:1c.1:   bridge window [io  0x2000-0x2fff]
[    0.579444] pci 0000:00:1c.1:   bridge window [mem 0x91300000-0x913fffff]
[    0.579451] pci 0000:00:1c.1:   bridge window [mem 0x91000000-0x910fffff 64bit pref]
[    0.579463] pci 0000:00:1c.2: PCI bridge to [bus 03]
[    0.579472] pci 0000:00:1c.2:   bridge window [mem 0x91200000-0x912fffff]
[    0.579487] pci 0000:00:1c.3: PCI bridge to [bus 04]
[    0.579495] pci 0000:00:1c.3:   bridge window [mem 0x91100000-0x911fffff]
[    0.579510] pci_bus 0000:00: resource 4 [io  0x0070-0x0077]
[    0.579515] pci_bus 0000:00: resource 5 [io  0x0000-0x006f window]
[    0.579520] pci_bus 0000:00: resource 6 [io  0x0078-0x0cf7 window]
[    0.579524] pci_bus 0000:00: resource 7 [io  0x0d00-0xffff window]
[    0.579530] pci_bus 0000:00: resource 8 [mem 0x000a0000-0x000bffff window]
[    0.579534] pci_bus 0000:00: resource 9 [mem 0x000c0000-0x000dffff window]
[    0.579539] pci_bus 0000:00: resource 10 [mem 0x000e0000-0x000fffff window]
[    0.579544] pci_bus 0000:00: resource 11 [mem 0x80000000-0xdfffffff window]
[    0.579548] pci_bus 0000:00: resource 12 [mem 0xfe800000-0xfe80ffff window]
[    0.579553] pci_bus 0000:01: resource 0 [io  0x1000-0x1fff]
[    0.579557] pci_bus 0000:01: resource 1 [mem 0x91700000-0x918fffff]
[    0.579562] pci_bus 0000:01: resource 2 [mem 0x91900000-0x91afffff 64bit pref]
[    0.579566] pci_bus 0000:02: resource 0 [io  0x2000-0x2fff]
[    0.579570] pci_bus 0000:02: resource 1 [mem 0x91300000-0x913fffff]
[    0.579575] pci_bus 0000:02: resource 2 [mem 0x91000000-0x910fffff 64bit pref]
[    0.579580] pci_bus 0000:03: resource 1 [mem 0x91200000-0x912fffff]
[    0.579585] pci_bus 0000:04: resource 1 [mem 0x91100000-0x911fffff]
[    0.579661] NET: Registered protocol family 2
[    0.580044] TCP established hash table entries: 32768 (order: 6, 262144 bytes)
[    0.580230] TCP bind hash table entries: 32768 (order: 7, 524288 bytes)
[    0.580430] TCP: Hash tables configured (established 32768 bind 32768)
[    0.580519] UDP hash table entries: 2048 (order: 4, 65536 bytes)
[    0.580570] UDP-Lite hash table entries: 2048 (order: 4, 65536 bytes)
[    0.580750] NET: Registered protocol family 1
[    0.580791] pci 0000:00:02.0: Video device with shadowed ROM
[    0.584624] PCI: CLS 64 bytes, default 64
[    0.584762] Trying to unpack rootfs image as initramfs...
[    1.765712] Freeing initrd memory: 35112K (ffff88003ddb1000 - ffff88003fffb000)
[    1.765738] PCI-DMA: Using software bounce buffering for IO (SWIOTLB)
[    1.765744] software IO TLB [mem 0x6a17e000-0x6e17e000] (64MB) mapped at [ffff88006a17e000-ffff88006e17dfff]
[    1.766162] Scanning for low memory corruption every 60 seconds
[    1.767187] futex hash table entries: 1024 (order: 4, 65536 bytes)
[    1.767258] audit: initializing netlink subsys (disabled)
[    1.767297] audit: type=2000 audit(1420073088.755:1): initialized
[    1.768206] Initialise system trusted keyring
[    1.768543] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    1.772582] zbud: loaded
[    1.773094] VFS: Disk quotas dquot_6.6.0
[    1.773198] VFS: Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    1.774569] fuse init (API version 7.23)
[    1.774961] Key type big_key registered
[    1.776623] Key type asymmetric registered
[    1.776631] Asymmetric key parser 'x509' registered
[    1.776731] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 249)
[    1.776888] io scheduler noop registered
[    1.776895] io scheduler deadline registered (default)
[    1.776984] io scheduler cfq registered
[    1.778054] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    1.778071] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    1.778152] efifb: probing for efifb
[    1.778194] efifb: framebuffer at 0x80000000, mapped to 0xffffc90000800000, using 4128k, total 4128k
[    1.778198] efifb: mode is 1366x768x32, linelength=5504, pages=1
[    1.778200] efifb: scrolling: redraw
[    1.778204] efifb: Truecolor: size=8:8:8:8, shift=24:16:8:0
[    1.778473] Console: switching to colour frame buffer device 170x48
[    1.778519] fb0: EFI VGA frame buffer device
[    1.778540] intel_idle: MWAIT substates: 0x33000020
[    1.778544] intel_idle: v0.4.1 model 0x4C
[    1.778547] intel_idle: lapic_timer_reliable_states 0xffffffff
[    1.781002] ACPI: AC Adapter [ADP1] (on-line)
[    1.781208] input: Lid Switch as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0D:00/input/input0
[    1.781261] ACPI: Lid Switch [LID0]
[    1.781368] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input1
[    1.781376] ACPI: Power Button [PWRB]
[    1.781477] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input2
[    1.781484] ACPI: Power Button [PWRF]
[    1.816760] thermal LNXTHERM:00: registered as thermal_zone0
[    1.816768] ACPI: Thermal Zone [TZS0] (49 C)
[    1.828972] thermal LNXTHERM:01: registered as thermal_zone1
[    1.828979] ACPI: Thermal Zone [TZS1] (42 C)
[    1.829103] GHES: HEST is not enabled!
[    1.829389] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    1.834873] ACPI: Battery Slot [BAT0] (battery present)
[    1.840448] Linux agpgart interface v0.103
[    1.851838] brd: module loaded
[    1.856188] loop: module loaded
[    1.856762] libphy: Fixed MDIO Bus: probed
[    1.856770] tun: Universal TUN/TAP device driver, 1.6
[    1.856773] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    1.857176] PPP generic driver version 2.4.2
[    1.857368] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    1.857383] ehci-pci: EHCI PCI platform driver
[    1.857414] ehci-platform: EHCI generic platform driver
[    1.857453] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    1.857477] ohci-pci: OHCI PCI platform driver
[    1.857508] ohci-platform: OHCI generic platform driver
[    1.857536] uhci_hcd: USB Universal Host Controller Interface driver
[    1.857907] xhci_hcd 0000:00:14.0: xHCI Host Controller
[    1.857923] xhci_hcd 0000:00:14.0: new USB bus registered, assigned bus number 1
[    1.859105] xhci_hcd 0000:00:14.0: hcc params 0x200077c1 hci version 0x100 quirks 0x00109810
[    1.859121] xhci_hcd 0000:00:14.0: cache line size of 64 is not supported
[    1.859470] usb usb1: New USB device found, idVendor=1d6b, idProduct=0002
[    1.859475] usb usb1: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.859480] usb usb1: Product: xHCI Host Controller
[    1.859484] usb usb1: Manufacturer: Linux 4.4.0-18-generic xhci-hcd
[    1.859488] usb usb1: SerialNumber: 0000:00:14.0
[    1.859856] hub 1-0:1.0: USB hub found
[    1.859888] hub 1-0:1.0: 7 ports detected
[    1.861181] xhci_hcd 0000:00:14.0: xHCI Host Controller
[    1.861190] xhci_hcd 0000:00:14.0: new USB bus registered, assigned bus number 2
[    1.861293] usb usb2: New USB device found, idVendor=1d6b, idProduct=0003
[    1.861299] usb usb2: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.861303] usb usb2: Product: xHCI Host Controller
[    1.861307] usb usb2: Manufacturer: Linux 4.4.0-18-generic xhci-hcd
[    1.861311] usb usb2: SerialNumber: 0000:00:14.0
[    1.861780] hub 2-0:1.0: USB hub found
[    1.861808] hub 2-0:1.0: 6 ports detected
[    1.863118] i8042: PNP: PS/2 Controller [PNP0303:KBD0,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    1.867515] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.867527] serio: i8042 AUX port at 0x60,0x64 irq 12
[    1.868737] mousedev: PS/2 mouse device common for all mice
[    1.870719] rtc_cmos 00:05: RTC can wake from S4
[    1.871033] rtc_cmos 00:05: rtc core: registered rtc_cmos as rtc0
[    1.871085] rtc_cmos 00:05: alarms up to one month, y3k, 242 bytes nvram
[    1.871107] i2c /dev entries driver
[    1.871279] device-mapper: uevent: version 1.0.3
[    1.871536] device-mapper: ioctl: 4.34.0-ioctl (2015-10-28) initialised: dm-devel@redhat.com
[    1.871588] Intel P-state driver initializing.
[    1.872528] ledtrig-cpu: registered to indicate activity on CPUs
[    1.872556] EFI Variables Facility v0.08 2004-May-17
[    1.881157] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3
[    1.908835] NET: Registered protocol family 10
[    1.909703] NET: Registered protocol family 17
[    1.909726] Key type dns_resolver registered
[    1.910641] microcode: CPU0 sig=0x406c3, pf=0x1, revision=0x34f
[    1.910651] microcode: CPU1 sig=0x406c3, pf=0x1, revision=0x34f
[    1.910725] microcode: CPU2 sig=0x406c3, pf=0x1, revision=0x34f
[    1.910809] microcode: CPU3 sig=0x406c3, pf=0x1, revision=0x34f
[    1.911088] microcode: Microcode Update Driver: v2.01 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[    1.911723] registered taskstats version 1
[    1.911748] Loading compiled-in X.509 certificates
[    1.913374] Loaded X.509 cert 'Build time autogenerated kernel key: 46aac491f1b0fe5a07252157966e4fbbb99d02a4'
[    1.913413] zswap: loaded using pool lzo/zbud
[    1.919628] Key type trusted registered
[    1.935253] Key type encrypted registered
[    1.935281] AppArmor: AppArmor sha1 policy hashing enabled
[    1.935289] ima: No TPM chip found, activating TPM-bypass!
[    1.935378] evm: HMAC attrs: 0x1
[    1.937195]   Magic number: 15:721:707
[    1.937790] rtc_cmos 00:05: setting system clock to 2015-01-01 00:44:49 UTC (1420073089)
[    1.938166] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.938169] EDD information not available.
[    1.938328] PM: Hibernation image not present or could not be loaded.
[    1.941103] Freeing unused kernel memory: 1476K (ffffffff81f41000 - ffffffff820b2000)
[    1.941111] Write protecting the kernel read-only data: 14336k
[    1.943372] Freeing unused kernel memory: 1872K (ffff88000182c000 - ffff880001a00000)
[    1.944696] Freeing unused kernel memory: 176K (ffff880001dd4000 - ffff880001e00000)
[    1.978988] random: systemd-udevd urandom read with 9 bits of entropy available
[    2.061411] FUJITSU Extended Socket Network Device Driver - version 1.0 - Copyright (c) 2015 FUJITSU LIMITED
[    2.064365] sdhci: Secure Digital Host Controller Interface driver
[    2.064371] sdhci: Copyright(c) Pierre Ossman
[    2.072439] hidraw: raw HID events driver (C) Jiri Kosina
[    2.097769] wmi: Mapper loaded
[    2.109136] ahci 0000:00:13.0: version 3.0
[    2.109399] ahci 0000:00:13.0: AHCI 0001.0301 32 slots 2 ports 6 Gbps 0x1 impl SATA mode
[    2.109408] ahci 0000:00:13.0: flags: 64bit ncq pm led clo only pio slum part deso sadm apst 
[    2.113367] [drm] Initialized drm 1.1.0 20060810
[    2.113708] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    2.113730] r8169 0000:02:00.0: can't disable ASPM; OS doesn't have ASPM control
[    2.113902] scsi host0: ahci
[    2.114481] r8169 0000:02:00.0 eth0: RTL8106e at 0xffffc900007b8000, dc:4a:3e:aa:2b:86, XID 04900000 IRQ 311
[    2.115199] scsi host1: ahci
[    2.115374] ata1: SATA max UDMA/133 abar m2048@0x91621000 port 0x91621100 irq 310
[    2.115379] ata2: DUMMY
[    2.116460] rtsx_pci 0000:04:00.0: rtsx_pci_acquire_irq: pcr->msi_en = 1, pci->irq = 312
[    2.165944] [drm] Memory usable by graphics device = 2048M
[    2.165956] checking generic (80000000 408000) vs hw (80000000 10000000)
[    2.165959] fb: switching to inteldrmfb from EFI VGA
[    2.166011] Console: switching to colour dummy device 80x25
[    2.166182] [drm] Replacing VGA console driver
[    2.166568] [drm] Supports vblank timestamp caching Rev 2 (21.10.2013).
[    2.166572] [drm] Driver supports precise vblank timestamp query.
[    2.197168] r8169 0000:02:00.0 enp2s0: renamed from eth0
[    2.232568] vgaarb: device changed decodes: PCI:0000:00:02.0,olddecodes=io+mem,decodes=io+mem:owns=io+mem
[    2.232636] usb 1-2: new full-speed USB device number 2 using xhci_hcd
[    2.306807] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)
[    2.307139] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/LNXVIDEO:00/input/input6
[    2.307365] [drm] Initialized i915 1.6.0 20151010 for 0000:00:02.0 on minor 0
[    2.365133] usb 1-2: New USB device found, idVendor=0483, idProduct=91d1
[    2.365141] usb 1-2: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[    2.365146] usb 1-2: Product: ST_SENSOR_HUB
[    2.365151] usb 1-2: Manufacturer: STMicroelectronics
[    2.365155] usb 1-2: SerialNumber: ST_SENSOR_HUB
[    2.444469] ata1: SATA link up 6.0 Gbps (SStatus 133 SControl 300)
[    2.444888] ata1.00: supports DRM functions and may not be fully accessible
[    2.445459] ata1.00: READ LOG DMA EXT failed, trying unqueued
[    2.445532] ata1.00: failed to get NCQ Send/Recv Log Emask 0x1
[    2.445537] ata1.00: ATA-9: Samsung SSD 840 EVO 250GB, EXT0CB6Q, max UDMA/133
[    2.445541] ata1.00: 488397168 sectors, multi 1: LBA48 NCQ (depth 31/32), AA
[    2.446927] ata1.00: supports DRM functions and may not be fully accessible
[    2.447207] ata1.00: failed to get NCQ Send/Recv Log Emask 0x1
[    2.447220] ata1.00: configured for UDMA/133
[    2.453529] scsi 0:0:0:0: Direct-Access     ATA      Samsung SSD 840  CB6Q PQ: 0 ANSI: 5
[    2.454209] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    2.454586] sd 0:0:0:0: [sda] 488397168 512-byte logical blocks: (250 GB/233 GiB)
[    2.455513] sd 0:0:0:0: [sda] Write Protect is off
[    2.455521] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    2.455929] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.463049]  sda: sda1 sda2 sda3
[    2.464266] sd 0:0:0:0: [sda] Attached SCSI disk
[    2.488358] [drm] GMBUS [i915 gmbus panel] timed out, falling back to bit banging on pin 3
[    2.532383] usb 1-5: new high-speed USB device number 3 using xhci_hcd
[    2.578758] fbcon: inteldrmfb (fb0) is primary device
[    2.578943] Console: switching to colour frame buffer device 170x48
[    2.578997] i915 0000:00:02.0: fb0: inteldrmfb frame buffer device
[    2.667905] usb 1-5: New USB device found, idVendor=05e3, idProduct=0610
[    2.667915] usb 1-5: New USB device strings: Mfr=0, Product=1, SerialNumber=0
[    2.667921] usb 1-5: Product: USB2.0 Hub
[    2.669230] hub 1-5:1.0: USB hub found
[    2.670091] hub 1-5:1.0: 4 ports detected
[    2.693272] usbcore: registered new interface driver usbhid
[    2.693277] usbhid: USB HID core driver
[    2.764235] tsc: Refined TSC clocksource calibration: 1599.948 MHz
[    2.764244] clocksource: tsc: mask: 0xffffffffffffffff max_cycles: 0x170ff3c37d3, max_idle_ns: 440795211487 ns
[    2.841994] psmouse serio1: synaptics: queried max coordinates: x [..5686], y [..4758]
[    2.873279] psmouse serio1: synaptics: queried min coordinates: x [1304..], y [1164..]
[    2.932514] psmouse serio1: synaptics: Touchpad model: 1, fw: 8.1, id: 0x1e2b1, caps: 0xf00123/0x840300/0x12e800/0x0, board id: 3103, fw id: 1805798
[    2.948789] usb 1-5.1: new full-speed USB device number 4 using xhci_hcd
[    2.970856] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input5
[    3.038644] usb 1-5.1: New USB device found, idVendor=8087, idProduct=0a2a
[    3.038650] usb 1-5.1: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[    3.116497] usb 1-5.2: new high-speed USB device number 5 using xhci_hcd
[    3.190238] mmc0: cannot verify signal voltage switch
[    3.233118] usb 1-5.2: New USB device found, idVendor=0bda, idProduct=57c4
[    3.233127] usb 1-5.2: New USB device strings: Mfr=3, Product=1, SerialNumber=2
[    3.233131] usb 1-5.2: Product: HP Truevision HD
[    3.233135] usb 1-5.2: Manufacturer: Generic
[    3.233139] usb 1-5.2: SerialNumber: DETGR019I9X33S
[    3.338436] mmc0: new ultra high speed SDR50 SDXC card at address b368
[    3.343757] mmcblk0: mmc0:b368       59.7 GiB 
[    3.349251] EXT4-fs (sda2): mounted filesystem with ordered data mode. Opts: (null)
[    3.387611]  mmcblk0: p1
[    3.527295] systemd[1]: System time before build time, advancing clock.
[    3.641106] systemd[1]: systemd 229 running in system mode. (+PAM +AUDIT +SELINUX +IMA +APPARMOR +SMACK +SYSVINIT +UTMP +LIBCRYPTSETUP +GCRYPT +GNUTLS +ACL +XZ -LZ4 +SECCOMP +BLKID +ELFUTILS +KMOD -IDN)
[    3.641420] systemd[1]: Detected architecture x86-64.
[    3.641729] systemd[1]: Set hostname to <Red>.
[    3.765100] clocksource: Switched to clocksource tsc
[    3.798300] systemd[1]: Listening on fsck to fsckd communication Socket.
[    3.798490] systemd[1]: Listening on Journal Socket.
[    3.798521] systemd[1]: Reached target Encrypted Volumes.
[    3.798597] systemd[1]: Listening on udev Control Socket.
[    3.798873] systemd[1]: Created slice System Slice.
[    3.799077] systemd[1]: Created slice system-systemd\x2dfsck.slice.
[    3.818354] systemd[1]: Starting Load Kernel Modules...
[    3.818836] systemd[1]: Created slice User and Session Slice.
[    3.820099] systemd[1]: Starting Create list of required static device nodes for the current kernel...
[    3.820528] systemd[1]: Created slice system-getty.slice.
[    3.821812] systemd[1]: Mounting POSIX Message Queue File System...
[    3.821983] systemd[1]: Listening on Syslog Socket.
[    3.822042] systemd[1]: Reached target Remote File Systems (Pre).
[    3.822241] systemd[1]: Listening on Journal Audit Socket.
[    3.823613] systemd[1]: Starting Braille Device Support...
[    3.823810] systemd[1]: Started Forward Password Requests to Wall Directory Watch.
[    3.823889] systemd[1]: Reached target Remote File Systems.
[    3.824000] systemd[1]: Listening on udev Kernel Socket.
[    3.828675] systemd[1]: Listening on /dev/initctl Compatibility Named Pipe.
[    3.829905] systemd[1]: Starting Uncomplicated firewall...
[    3.830103] systemd[1]: Listening on Journal Socket (/dev/log).
[    3.831427] systemd[1]: Starting Journal Service...
[    3.831478] systemd[1]: Reached target User and Group Name Lookups.
[    3.832979] systemd[1]: Started Read required files in advance.
[    3.834811] systemd[1]: Mounting Debug File System...
[    3.835202] systemd[1]: Set up automount Arbitrary Executable File Formats File System Automount Point.
[    3.842773] systemd[1]: Mounting Huge Pages File System...
[    3.844307] systemd[1]: Starting Nameserver information manager...
[    3.844371] systemd[1]: Reached target Slices.
[    3.853741] systemd[1]: Started Create list of required static device nodes for the current kernel.
[    3.864422] systemd[1]: Started Uncomplicated firewall.
[    3.871518] systemd[1]: Mounted Huge Pages File System.
[    3.871700] systemd[1]: Mounted Debug File System.
[    3.871783] systemd[1]: Mounted POSIX Message Queue File System.
[    3.883105] lp: driver loaded but no devices found
[    3.885138] systemd[1]: Started Nameserver information manager.
[    3.896008] ppdev: user-space parallel port driver
[    3.910359] systemd[1]: Started Load Kernel Modules.
[    3.917918] systemd[1]: Started Braille Device Support.
[    3.934741] systemd[1]: Started Journal Service.
[    4.100423] EXT4-fs (sda2): re-mounted. Opts: errors=remount-ro
[    4.135743] systemd-journald[238]: Received request to flush runtime journal from PID 1
[    4.328594] Initializing HPQ6001 module
[    4.334499] input: HP Wireless hotkeys as /devices/virtual/input/input7
[    4.363748] hp_accel: laptop model unknown, using default axes configuration
[    4.441100] lis3lv02d: unknown sensor type 0x0
[    4.441120] hp_accel: probe of HPQ6007:00 failed with error -22
[    4.518427] random: nonblocking pool is initialized
[    4.560781] dw_dmac INTL9C60:01: DesignWare DMA Controller, 8 channels
[    4.584760] Bluetooth: Core ver 2.21
[    4.584810] NET: Registered protocol family 31
[    4.584816] Bluetooth: HCI device and connection manager initialized
[    4.584898] Bluetooth: HCI socket layer initialized
[    4.584905] Bluetooth: L2CAP socket layer initialized
[    4.584949] Bluetooth: SCO socket layer initialized
[    4.589261] media: Linux media interface: v0.10
[    4.609286] usbcore: registered new interface driver btusb
[    4.612513] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[    4.613256] Linux video capture interface: v2.00
[    4.627816] Bluetooth: hci0: read Intel version: 370810011003110e00
[    4.639479] Bluetooth: hci0: Intel Bluetooth firmware file: intel/ibt-hw-37.8.10-fw-1.10.3.11.e.bseq
[    4.640012] uvcvideo: Found UVC 1.00 device HP Truevision HD (0bda:57c4)
[    4.644873] nfc: nfc_init: NFC Core ver 0.1
[    4.644916] NET: Registered protocol family 39
[    4.647536] input: HP Truevision HD as /devices/pci0000:00/0000:00:14.0/usb1/1-5/1-5.2/1-5.2:1.0/input/input8
[    4.647659] usbcore: registered new interface driver uvcvideo
[    4.647662] USB Video Class driver (1.1.1)
[    4.695173] Intel(R) Wireless WiFi driver for Linux
[    4.695179] Copyright(c) 2003- 2015 Intel Corporation
[    4.696202] iwlwifi 0000:03:00.0: Direct firmware load for iwlwifi-7265D-19.ucode failed with error -2
[    4.696234] iwlwifi 0000:03:00.0: Direct firmware load for iwlwifi-7265D-18.ucode failed with error -2
[    4.696259] iwlwifi 0000:03:00.0: Direct firmware load for iwlwifi-7265D-17.ucode failed with error -2
[    4.702177] iwlwifi 0000:03:00.0: loaded firmware version 16.242414.0 op_mode iwlmvm
[    4.717480] snd_hda_intel 0000:00:1b.0: bound 0000:00:02.0 (ops i915_audio_component_bind_ops [i915])
[    4.739101] Adding 4047868k swap on /dev/sda3.  Priority:-1 extents:1 across:4047868k SSFS
[    4.774497] SSE version of gcm_enc/dec engaged.
[    4.779379] iwlwifi 0000:03:00.0: Detected Intel(R) Dual Band Wireless AC 3165, REV=0x210
[    4.779528] iwlwifi 0000:03:00.0: L1 Enabled - LTR Enabled
[    4.779757] iwlwifi 0000:03:00.0: L1 Enabled - LTR Enabled
[    4.792558] snd_hda_codec_realtek hdaudioC0D0: autoconfig for ALC3227: line_outs=1 (0x14/0x0/0x0/0x0/0x0) type:speaker
[    4.792568] snd_hda_codec_realtek hdaudioC0D0:    speaker_outs=0 (0x0/0x0/0x0/0x0/0x0)
[    4.792571] snd_hda_codec_realtek hdaudioC0D0:    hp_outs=1 (0x21/0x0/0x0/0x0/0x0)
[    4.792574] snd_hda_codec_realtek hdaudioC0D0:    mono: mono_out=0x0
[    4.792576] snd_hda_codec_realtek hdaudioC0D0:    inputs:
[    4.792580] snd_hda_codec_realtek hdaudioC0D0:      Mic=0x19
[    4.792583] snd_hda_codec_realtek hdaudioC0D0:      Internal Mic=0x12
[    4.860694] input: HDA Intel PCH Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input9
[    4.860858] input: HDA Intel PCH Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card0/input10
[    4.861021] input: HDA Intel PCH HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:1b.0/sound/card0/input11
[    4.877362] ieee80211 phy0: Selected rate control algorithm 'iwl-mvm-rs'
[    4.914022] Bluetooth: hci0: Intel Bluetooth firmware patch completed and activated
[    4.949407] kvm: disabled by bios
[    4.963798] intel_rapl: Found RAPL domain package
[    4.963807] intel_rapl: Found RAPL domain core
[    5.014386] kvm: disabled by bios
[    5.057380] acer_wmi: Acer Laptop ACPI-WMI Extras
[    5.066020] input: Acer BMA150 accelerometer as /devices/virtual/input/input13
[    5.125285] input: SYNA7508:00 06CB:12A4 Pen as /devices/pci0000:00/808622C1:00/i2c-9/i2c-SYNA7508:00/0018:06CB:12A4.0002/input/input14
[    5.126487] input: SYNA7508:00 06CB:12A4 as /devices/pci0000:00/808622C1:00/i2c-9/i2c-SYNA7508:00/0018:06CB:12A4.0002/input/input15
[    5.126939] hid-multitouch 0018:06CB:12A4.0002: input,hidraw0: I2C HID v1.00 Device [SYNA7508:00 06CB:12A4] on i2c-SYNA7508:00
[    5.188169] audit: type=1400 audit(1460932952.833:2): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/telepathy/mission-control-5" pid=565 comm="apparmor_parser"
[    5.188186] audit: type=1400 audit(1460932952.833:3): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/telepathy/telepathy-*" pid=565 comm="apparmor_parser"
[    5.188198] audit: type=1400 audit(1460932952.833:4): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/telepathy/telepathy-*//pxgsettings" pid=565 comm="apparmor_parser"
[    5.188208] audit: type=1400 audit(1460932952.833:5): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/telepathy/telepathy-*//sanitized_helper" pid=565 comm="apparmor_parser"
[    5.188217] audit: type=1400 audit(1460932952.833:6): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/telepathy/telepathy-ofono" pid=565 comm="apparmor_parser"
[    5.191555] audit: type=1400 audit(1460932952.837:7): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/sbin/cups-browsed" pid=567 comm="apparmor_parser"
[    5.191771] audit: type=1400 audit(1460932952.837:8): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/sbin/dhclient" pid=561 comm="apparmor_parser"
[    5.191793] audit: type=1400 audit(1460932952.837:9): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=561 comm="apparmor_parser"
[    5.191806] audit: type=1400 audit(1460932952.837:10): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-helper" pid=561 comm="apparmor_parser"
[    5.208660] iwlwifi 0000:03:00.0 wlp3s0: renamed from wlan0
[    5.359766] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[    5.359773] Bluetooth: BNEP filters: protocol multicast
[    5.359782] Bluetooth: BNEP socket layer initialized
[    5.501249] cfg80211: World regulatory domain updated:
[    5.501258] cfg80211:  DFS Master region: unset
[    5.501260] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp), (dfs_cac_time)
[    5.501264] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A, 2000 mBm), (N/A)
[    5.501267] cfg80211:   (2457000 KHz - 2482000 KHz @ 40000 KHz), (N/A, 2000 mBm), (N/A)
[    5.501269] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (N/A, 2000 mBm), (N/A)
[    5.501272] cfg80211:   (5170000 KHz - 5250000 KHz @ 80000 KHz, 160000 KHz AUTO), (N/A, 2000 mBm), (N/A)
[    5.501276] cfg80211:   (5250000 KHz - 5330000 KHz @ 80000 KHz, 160000 KHz AUTO), (N/A, 2000 mBm), (0 s)
[    5.501279] cfg80211:   (5490000 KHz - 5730000 KHz @ 160000 KHz), (N/A, 2000 mBm), (0 s)
[    5.501281] cfg80211:   (5735000 KHz - 5835000 KHz @ 80000 KHz), (N/A, 2000 mBm), (N/A)
[    5.501284] cfg80211:   (57240000 KHz - 63720000 KHz @ 2160000 KHz), (N/A, 0 mBm), (N/A)
[    5.740991] input: HP WMI hotkeys as /devices/virtual/input/input12
[    5.816195] IPv6: ADDRCONF(NETDEV_UP): wlp3s0: link is not ready
[    5.825177] IPv6: ADDRCONF(NETDEV_UP): enp2s0: link is not ready
[    6.006773] r8169 0000:02:00.0 enp2s0: link down
[    6.006936] IPv6: ADDRCONF(NETDEV_UP): enp2s0: link is not ready
[    7.810163] Bluetooth: RFCOMM TTY layer initialized
[    7.810179] Bluetooth: RFCOMM socket layer initialized
[    7.810193] Bluetooth: RFCOMM ver 1.11
[   16.024043] iwlwifi 0000:03:00.0: L1 Enabled - LTR Enabled
[   16.024376] iwlwifi 0000:03:00.0: L1 Enabled - LTR Enabled
[   16.085272] iwlwifi 0000:03:00.0: L1 Enabled - LTR Enabled
[   16.085517] iwlwifi 0000:03:00.0: L1 Enabled - LTR Enabled
[   16.106272] IPv6: ADDRCONF(NETDEV_UP): wlp3s0: link is not ready
[   16.189925] IPv6: ADDRCONF(NETDEV_UP): wlp3s0: link is not ready
[   59.548511] FAT-fs (mmcblk0p1): Volume was not properly unmounted. Some data may be corrupt. Please run fsck.
[  333.121094] acer_wmi: Acer Laptop WMI Extras unloaded
[  333.125117] iwlwifi 0000:03:00.0: L1 Enabled - LTR Enabled
[  333.125343] iwlwifi 0000:03:00.0: L1 Enabled - LTR Enabled
[  333.185693] iwlwifi 0000:03:00.0: L1 Enabled - LTR Enabled
[  333.185911] iwlwifi 0000:03:00.0: L1 Enabled - LTR Enabled
[  333.201799] IPv6: ADDRCONF(NETDEV_UP): wlp3s0: link is not ready
[  333.328807] iwlwifi 0000:03:00.0: L1 Enabled - LTR Enabled
[  333.519730] Intel(R) Wireless WiFi driver for Linux
[  333.519737] Copyright(c) 2003- 2015 Intel Corporation
[  333.520613] iwlwifi 0000:03:00.0: Direct firmware load for iwlwifi-7265D-19.ucode failed with error -2
[  333.520646] iwlwifi 0000:03:00.0: Direct firmware load for iwlwifi-7265D-18.ucode failed with error -2
[  333.520665] iwlwifi 0000:03:00.0: Direct firmware load for iwlwifi-7265D-17.ucode failed with error -2
[  333.523167] iwlwifi 0000:03:00.0: loaded firmware version 16.242414.0 op_mode iwlmvm
[  333.560219] iwlwifi 0000:03:00.0: Detected Intel(R) Dual Band Wireless AC 3165, REV=0x210
[  333.560338] iwlwifi 0000:03:00.0: L1 Enabled - LTR Enabled
[  333.560599] iwlwifi 0000:03:00.0: L1 Enabled - LTR Enabled
[  333.593057] cfg80211: World regulatory domain updated:
[  333.593065] cfg80211:  DFS Master region: unset
[  333.593067] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp), (dfs_cac_time)
[  333.593071] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A, 2000 mBm), (N/A)
[  333.593074] cfg80211:   (2457000 KHz - 2482000 KHz @ 40000 KHz), (N/A, 2000 mBm), (N/A)
[  333.593077] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (N/A, 2000 mBm), (N/A)
[  333.593080] cfg80211:   (5170000 KHz - 5250000 KHz @ 80000 KHz, 160000 KHz AUTO), (N/A, 2000 mBm), (N/A)
[  333.593083] cfg80211:   (5250000 KHz - 5330000 KHz @ 80000 KHz, 160000 KHz AUTO), (N/A, 2000 mBm), (0 s)
[  333.593086] cfg80211:   (5490000 KHz - 5730000 KHz @ 160000 KHz), (N/A, 2000 mBm), (0 s)
[  333.593089] cfg80211:   (5735000 KHz - 5835000 KHz @ 80000 KHz), (N/A, 2000 mBm), (N/A)
[  333.593091] cfg80211:   (57240000 KHz - 63720000 KHz @ 2160000 KHz), (N/A, 0 mBm), (N/A)
[  333.625668] ieee80211 phy0: Selected rate control algorithm 'iwl-mvm-rs'
[  333.633332] iwlwifi 0000:03:00.0 wlp3s0: renamed from wlan0
[  333.654239] iwlwifi 0000:03:00.0: L1 Enabled - LTR Enabled
[  333.654472] iwlwifi 0000:03:00.0: L1 Enabled - LTR Enabled
[  333.717787] iwlwifi 0000:03:00.0: L1 Enabled - LTR Enabled
[  333.718020] iwlwifi 0000:03:00.0: L1 Enabled - LTR Enabled
[  333.740066] IPv6: ADDRCONF(NETDEV_UP): wlp3s0: link is not ready
[  333.740823] IPv6: ADDRCONF(NETDEV_UP): wlp3s0: link is not ready
[  333.758399] IPv6: ADDRCONF(NETDEV_UP): wlp3s0: link is not ready
[  337.292365] wlp3s0: authenticate with 58:6d:8f:bf:ea:06
[  337.297098] wlp3s0: send auth to 58:6d:8f:bf:ea:06 (try 1/3)
[  337.299379] wlp3s0: authenticated
[  337.302496] wlp3s0: associate with 58:6d:8f:bf:ea:06 (try 1/3)
[  337.306928] wlp3s0: RX AssocResp from 58:6d:8f:bf:ea:06 (capab=0x411 status=0 aid=2)
[  337.317122] wlp3s0: associated
[  337.317283] IPv6: ADDRCONF(NETDEV_CHANGE): wlp3s0: link becomes ready
[  467.108369] wlp3s0: authenticate with 20:10:7a:b4:8e:c6
[  467.111143] wlp3s0: send auth to 20:10:7a:b4:8e:c6 (try 1/3)
[  467.113158] wlp3s0: authenticated
[  467.117791] wlp3s0: associate with 20:10:7a:b4:8e:c6 (try 1/3)
[  467.121522] wlp3s0: RX AssocResp from 20:10:7a:b4:8e:c6 (capab=0x411 status=0 aid=4)
[  467.123185] wlp3s0: associated
[  550.311639] wlp3s0: authenticate with 58:6d:8f:bf:ea:06
[  550.314455] wlp3s0: send auth to 58:6d:8f:bf:ea:06 (try 1/3)
[  550.316324] wlp3s0: authenticated
[  550.320579] wlp3s0: associate with 58:6d:8f:bf:ea:06 (try 1/3)
[  550.324504] wlp3s0: RX AssocResp from 58:6d:8f:bf:ea:06 (capab=0x411 status=0 aid=2)
[  550.326667] wlp3s0: associated
[  656.870577] wlp3s0: authenticate with 20:10:7a:b4:8e:c6
[  656.873106] wlp3s0: send auth to 20:10:7a:b4:8e:c6 (try 1/3)
[  656.876830] wlp3s0: authenticated
[  656.877980] wlp3s0: associate with 20:10:7a:b4:8e:c6 (try 1/3)
[  656.881354] wlp3s0: RX AssocResp from 20:10:7a:b4:8e:c6 (capab=0x411 status=0 aid=4)
[  656.882324] wlp3s0: associated
[ 1133.469045] wlp3s0: authenticate with 58:6d:8f:bf:ea:06
[ 1133.472832] wlp3s0: send auth to 58:6d:8f:bf:ea:06 (try 1/3)
[ 1133.474703] wlp3s0: authenticated
[ 1133.476193] wlp3s0: associate with 58:6d:8f:bf:ea:06 (try 1/3)
[ 1133.480100] wlp3s0: RX AssocResp from 58:6d:8f:bf:ea:06 (capab=0x411 status=0 aid=2)
[ 1133.481346] wlp3s0: associated
[ 1373.527191] wlp3s0: authenticate with 20:10:7a:b4:8e:c6
[ 1373.530271] wlp3s0: send auth to 20:10:7a:b4:8e:c6 (try 1/3)
[ 1373.532549] wlp3s0: authenticated
[ 1373.534783] wlp3s0: associate with 20:10:7a:b4:8e:c6 (try 1/3)
[ 1373.538236] wlp3s0: RX AssocResp from 20:10:7a:b4:8e:c6 (capab=0x411 status=0 aid=4)
[ 1373.549180] wlp3s0: associated
jlloyd13@Red:~$ 

```

---

### Post by dFlyer on 2016-04-22
Unity suspend is not working correctly also. If I set suspend to timeout in 10 minutes the computer will suspend after 10 minutes of non use. If I click suspend in the main menu it will suspend. If I close the lid it will wait until the time has pass that I've set it to suspend or 10 minutes in my case. My current work around is to suspend from the main menu before I close the lid.

---

### Post by sammiev on 2016-04-22
Just tested it on Ubuntu-Gnome 16.04 and it worked as expected with no issues.

---

### Post by james208 on 2016-05-04
> **sammiev said:**
> Just tested it on Ubuntu-Gnome 16.04 and it worked as expected with no issues.

Well that doesn't exactly help. Are you using the same laptop model? Probably not. If it didn't work as expected on the majority of hardware then it would've been fixed before release. This is clearly a hardware specific issue. That's why I posted dmesg output. If outputs from more commands are needed to help sort the issue out I can provide but simply stating that there isn't an issue in general when there is one on my laptop defeats the point of a help forum.

---

### Post by james208 on 2016-05-04
[ATTACH=CONFIG]268845[/ATTACH][ATTACH=CONFIG]268846[/ATTACH][ATTACH=CONFIG]268847[/ATTACH][ATTACH=CONFIG]268848[/ATTACH][ATTACH=CONFIG]268849[/ATTACH]
Ok, this most recent time I tried it I got a Ubuntu error thingy. Wouldn't let me copy the text but I have screenshots of the whole thing. I can only put 5 per post so another post will be coming with more screenshots. They may be out of order.

---

### Post by james208 on 2016-05-04
[ATTACH=CONFIG]268850[/ATTACH][ATTACH=CONFIG]268851[/ATTACH][ATTACH=CONFIG]268852[/ATTACH][ATTACH=CONFIG]268853[/ATTACH]

And there are the others. Hopefully this will help

---

### Post by james208 on 2016-05-09
Fixed with kernel update!

---

