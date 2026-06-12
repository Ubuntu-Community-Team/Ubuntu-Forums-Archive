---
title: "Bluetooth suddenly disconnects and reconnects"
date: 2019-08-13
forum: Hardware
---

### Post by jeferbc on 2019-08-13
Hi everyone,

I'm having issues with the bluetooth of my lenovo Y400 laptop, my headphones A2DP connects without issues, but after random x minutes, my headphones suddenly disconnects and reconnects again. Besides, when I connect my headphones and my mx master mouse bluetooth at the same time, the headphones sound starts to lagging, is like skipping the music when i move the mouse. Can someone help me. Thanks

---

### Post by jeferbc on 2019-08-13
I attached the result of > dmesg after suddenly disconnects and connects

```
[ 0.000000] microcode: microcode updated early to revision 0x21, date = 2019-02-13[ 0.000000] Linux version 5.0.0-23-generic (buildd@lgw01-amd64-030) (gcc version 7.4.0 (Ubuntu 7.4.0-1ubuntu1~18.04.1)) #24~18.04.1-Ubuntu SMP Mon Jul 29 16:12:28 UTC 2019 (Ubuntu 5.0.0-23.24~18.04.1-generic 5.0.15)
[ 0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-5.0.0-23-generic root=UUID=1461fced-a151-4b5b-bc7f-f54871e5ec87 ro quiet splash vt.handoff=1
[ 0.000000] KERNEL supported cpus:
[ 0.000000] Intel GenuineIntel
[ 0.000000] AMD AuthenticAMD
[ 0.000000] Hygon HygonGenuine
[ 0.000000] Centaur CentaurHauls
[ 0.000000] x86/fpu: Supporting XSAVE feature 0x001: 'x87 floating point registers'
[ 0.000000] x86/fpu: Supporting XSAVE feature 0x002: 'SSE registers'
[ 0.000000] x86/fpu: Supporting XSAVE feature 0x004: 'AVX registers'
[ 0.000000] x86/fpu: xstate_offset[2]: 576, xstate_sizes[2]: 256
[ 0.000000] x86/fpu: Enabled xstate features 0x7, context size is 832 bytes, using 'standard' format.
[ 0.000000] BIOS-provided physical RAM map:
[ 0.000000] BIOS-e820: [mem 0x0000000000000000-0x0000000000087fff] usable
[ 0.000000] BIOS-e820: [mem 0x0000000000088000-0x00000000000bffff] reserved
[ 0.000000] BIOS-e820: [mem 0x0000000000100000-0x00000000a95affff] usable
[ 0.000000] BIOS-e820: [mem 0x00000000a95b0000-0x00000000aa9affff] reserved
[ 0.000000] BIOS-e820: [mem 0x00000000aa9b0000-0x00000000aefbefff] usable
[ 0.000000] BIOS-e820: [mem 0x00000000aefbf000-0x00000000af04dfff] type 20
[ 0.000000] BIOS-e820: [mem 0x00000000af04e000-0x00000000af04ffff] reserved
[ 0.000000] BIOS-e820: [mem 0x00000000af050000-0x00000000af065fff] type 20
[ 0.000000] BIOS-e820: [mem 0x00000000af066000-0x00000000af066fff] reserved
[ 0.000000] BIOS-e820: [mem 0x00000000af067000-0x00000000af07efff] type 20
[ 0.000000] BIOS-e820: [mem 0x00000000af07f000-0x00000000af07ffff] reserved
[ 0.000000] BIOS-e820: [mem 0x00000000af080000-0x00000000af08afff] type 20
[ 0.000000] BIOS-e820: [mem 0x00000000af08b000-0x00000000af08bfff] reserved
[ 0.000000] BIOS-e820: [mem 0x00000000af08c000-0x00000000af090fff] type 20
[ 0.000000] BIOS-e820: [mem 0x00000000af091000-0x00000000af091fff] reserved
[ 0.000000] BIOS-e820: [mem 0x00000000af092000-0x00000000af09ffff] type 20
[ 0.000000] BIOS-e820: [mem 0x00000000af0a0000-0x00000000af0a0fff] reserved
[ 0.000000] BIOS-e820: [mem 0x00000000af0a1000-0x00000000af0f1fff] type 20
[ 0.000000] BIOS-e820: [mem 0x00000000af0f2000-0x00000000af136fff] reserved
[ 0.000000] BIOS-e820: [mem 0x00000000af137000-0x00000000af1befff] type 20
[ 0.000000] BIOS-e820: [mem 0x00000000af1bf000-0x00000000af6befff] reserved
[ 0.000000] BIOS-e820: [mem 0x00000000af6bf000-0x00000000af7befff] ACPI NVS
[ 0.000000] BIOS-e820: [mem 0x00000000af7bf000-0x00000000af7fefff] ACPI data
[ 0.000000] BIOS-e820: [mem 0x00000000af7ff000-0x00000000af7fffff] usable
[ 0.000000] BIOS-e820: [mem 0x00000000af800000-0x00000000afffffff] reserved
[ 0.000000] BIOS-e820: [mem 0x00000000f0000000-0x00000000f3ffffff] reserved
[ 0.000000] BIOS-e820: [mem 0x00000000feb00000-0x00000000feb03fff] reserved
[ 0.000000] BIOS-e820: [mem 0x00000000fec00000-0x00000000fec00fff] reserved
[ 0.000000] BIOS-e820: [mem 0x00000000fed10000-0x00000000fed19fff] reserved
[ 0.000000] BIOS-e820: [mem 0x00000000fed1c000-0x00000000fed1ffff] reserved
[ 0.000000] BIOS-e820: [mem 0x00000000fee00000-0x00000000fee00fff] reserved
[ 0.000000] BIOS-e820: [mem 0x00000000ffb80000-0x00000000ffffffff] reserved
[ 0.000000] BIOS-e820: [mem 0x0000000100000000-0x000000024effffff] usable
[ 0.000000] NX (Execute Disable) protection: active
[ 0.000000] efi: EFI v2.31 by INSYDE Corp.
[ 0.000000] efi: ACPI=0xaf7fe000 ACPI 2.0=0xaf7fe014 SMBIOS=0xaf6bef98 
[ 0.000000] secureboot: Secure boot could not be determined (mode 0)
[ 0.000000] SMBIOS 2.7 present.
[ 0.000000] DMI: LENOVO 20192/INVALID, BIOS 6BCN34WW(V1.05) 11/29/2012
[ 0.000000] tsc: Fast TSC calibration using PIT
[ 0.000000] tsc: Detected 2394.526 MHz processor
[ 0.000048] e820: update [mem 0x00000000-0x00000fff] usable ==> reserved
[ 0.000050] e820: remove [mem 0x000a0000-0x000fffff] usable
[ 0.000062] last_pfn = 0x24f000 max_arch_pfn = 0x400000000
[ 0.000066] MTRR default type: uncachable
[ 0.000067] MTRR fixed ranges enabled:
[ 0.000068] 00000-9FFFF write-back
[ 0.000069] A0000-BFFFF uncachable
[ 0.000070] C0000-E7FFF write-protect
[ 0.000071] E8000-EFFFF write-combining
[ 0.000072] F0000-FFFFF write-protect
[ 0.000072] MTRR variable ranges enabled:
[ 0.000074] 0 base 000000000 mask F80000000 write-back
[ 0.000075] 1 base 080000000 mask FC0000000 write-back
[ 0.000075] 2 base 0AF800000 mask FFF800000 uncachable
[ 0.000076] 3 base 0B0000000 mask FF0000000 uncachable
[ 0.000077] 4 base 0FF800000 mask FFF800000 write-protect
[ 0.000078] 5 base 100000000 mask F00000000 write-back
[ 0.000079] 6 base 200000000 mask F80000000 write-back
[ 0.000080] 7 base 24F000000 mask FFF000000 uncachable
[ 0.000080] 8 base 250000000 mask FF0000000 uncachable
[ 0.000081] 9 base 260000000 mask FE0000000 uncachable
[ 0.000913] x86/PAT: Configuration [0-7]: WB WC UC- UC WB WP UC- WT 
[ 0.001054] last_pfn = 0xaf800 max_arch_pfn = 0x400000000
[ 0.012513] check: Scanning 1 areas for low memory corruption
[ 0.012520] BRK [0x232601000, 0x232601fff] PGTABLE
[ 0.012522] BRK [0x232602000, 0x232602fff] PGTABLE
[ 0.012523] BRK [0x232603000, 0x232603fff] PGTABLE
[ 0.012574] BRK [0x232604000, 0x232604fff] PGTABLE
[ 0.012576] BRK [0x232605000, 0x232605fff] PGTABLE
[ 0.012819] BRK [0x232606000, 0x232606fff] PGTABLE
[ 0.012832] BRK [0x232607000, 0x232607fff] PGTABLE
[ 0.012886] BRK [0x232608000, 0x232608fff] PGTABLE
[ 0.012949] BRK [0x232609000, 0x232609fff] PGTABLE
[ 0.013039] BRK [0x23260a000, 0x23260afff] PGTABLE
[ 0.013099] BRK [0x23260b000, 0x23260bfff] PGTABLE
[ 0.013146] BRK [0x23260c000, 0x23260cfff] PGTABLE
[ 0.013251] RAMDISK: [mem 0x3333f000-0x35996fff]
[ 0.013260] ACPI: Early table checksum verification disabled
[ 0.013264] ACPI: RSDP 0x00000000AF7FE014 000024 (v02 LENOVO)
[ 0.013267] ACPI: XSDT 0x00000000AF7FE210 0000AC (v01 LENOVO CB-01 00000001 01000013)
[ 0.013273] ACPI: FACP 0x00000000AF7FA000 00010C (v05 LENOVO CB-01 00000001 ACPI 00040000)
[ 0.013279] ACPI: DSDT 0x00000000AF7ED000 009D93 (v01 LENOVO CB-01 00000001 ACPI 00040000)
[ 0.013282] ACPI: FACS 0x00000000AF7BB000 000040
[ 0.013285] ACPI: SLIC 0x00000000AF7FD000 000176 (v01 LENOVO CB-01 00000001 ACPI 00040000)
[ 0.013288] ACPI: UEFI 0x00000000AF7FC000 000236 (v01 LENOVO CB-01 00000001 ACPI 00040000)
[ 0.013290] ACPI: ASF! 0x00000000AF7FB000 0000A5 (v32 LENOVO CB-01 00000001 ACPI 00040000)
[ 0.013294] ACPI: HPET 0x00000000AF7F9000 000038 (v01 LENOVO CB-01 00000001 ACPI 00040000)
[ 0.013296] ACPI: APIC 0x00000000AF7F8000 00008C (v03 LENOVO CB-01 00000001 ACPI 00040000)
[ 0.013299] ACPI: MCFG 0x00000000AF7F7000 00003C (v01 LENOVO CB-01 00000001 ACPI 00040000)
[ 0.013302] ACPI: SSDT 0x00000000AF7EC000 0006FE (v01 LENOVO CB-01 00000001 ACPI 00040000)
[ 0.013305] ACPI: BOOT 0x00000000AF7EA000 000028 (v01 LENOVO CB-01 00000001 ACPI 00040000)
[ 0.013308] ACPI: ASPT 0x00000000AF7E5000 000034 (v07 LENOVO CB-01 00000001 ACPI 00040000)
[ 0.013310] ACPI: DBGP 0x00000000AF7E4000 000034 (v01 LENOVO CB-01 00000001 ACPI 00040000)
[ 0.013313] ACPI: FPDT 0x00000000AF7E2000 000044 (v01 LENOVO CB-01 00000001 ACPI 00040000)
[ 0.013316] ACPI: MSDM 0x00000000AF7E1000 000055 (v03 LENOVO CB-01 00000001 ACPI 00040000)
[ 0.013319] ACPI: SSDT 0x00000000AF7E0000 000926 (v01 LENOVO CB-01 00000001 ACPI 00040000)
[ 0.013322] ACPI: SSDT 0x00000000AF7DF000 000B22 (v01 LENOVO CB-01 00000001 ACPI 00040000)
[ 0.013325] ACPI: SSDT 0x00000000AF7DC000 0010F1 (v01 LENOVO CB-01 00000001 ACPI 00040000)
[ 0.013327] ACPI: BGRT 0x00000000AF7DE000 000038 (v01 LENOVO CB-01 00000001 ACPI 00040000)
[ 0.013337] ACPI: Local APIC address 0xfee00000
[ 0.013428] No NUMA configuration found
[ 0.013429] Faking a node at [mem 0x0000000000000000-0x000000024effffff]
[ 0.013439] NODE_DATA(0) allocated [mem 0x24efd1000-0x24effbfff]
[ 0.013695] Zone ranges:
[ 0.013696] DMA [mem 0x0000000000001000-0x0000000000ffffff]
[ 0.013697] DMA32 [mem 0x0000000001000000-0x00000000ffffffff]
[ 0.013698] Normal [mem 0x0000000100000000-0x000000024effffff]
[ 0.013699] Device empty
[ 0.013700] Movable zone start for each node
[ 0.013703] Early memory node ranges
[ 0.013704] node 0: [mem 0x0000000000001000-0x0000000000087fff]
[ 0.013705] node 0: [mem 0x0000000000100000-0x00000000a95affff]
[ 0.013706] node 0: [mem 0x00000000aa9b0000-0x00000000aefbefff]
[ 0.013706] node 0: [mem 0x00000000af7ff000-0x00000000af7fffff]
[ 0.013707] node 0: [mem 0x0000000100000000-0x000000024effffff]
[ 0.013891] Zeroed struct page in unavailable ranges: 9401 pages
[ 0.013893] Initmem setup node 0 [mem 0x0000000000001000-0x000000024effffff]
[ 0.013894] On node 0 totalpages: 2083655
[ 0.013895] DMA zone: 64 pages used for memmap
[ 0.013895] DMA zone: 25 pages reserved
[ 0.013896] DMA zone: 3975 pages, LIFO batch:0
[ 0.014013] DMA32 zone: 11055 pages used for memmap
[ 0.014014] DMA32 zone: 707520 pages, LIFO batch:63
[ 0.035340] Normal zone: 21440 pages used for memmap
[ 0.035342] Normal zone: 1372160 pages, LIFO batch:63
[ 0.073874] ACPI: PM-Timer IO Port: 0x408
[ 0.073877] ACPI: Local APIC address 0xfee00000
[ 0.073894] IOAPIC[0]: apic_id 0, version 32, address 0xfec00000, GSI 0-23
[ 0.073896] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[ 0.073897] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[ 0.073899] ACPI: IRQ0 used by override.
[ 0.073900] ACPI: IRQ9 used by override.
[ 0.073902] Using ACPI (MADT) for SMP configuration information
[ 0.073903] ACPI: HPET id: 0x8086a201 base: 0xfed00000
[ 0.073916] smpboot: Allowing 8 CPUs, 0 hotplug CPUs
[ 0.073951] PM: Registered nosave memory: [mem 0x00000000-0x00000fff]
[ 0.073953] PM: Registered nosave memory: [mem 0x00088000-0x000bffff]
[ 0.073954] PM: Registered nosave memory: [mem 0x000c0000-0x000fffff]
[ 0.073955] PM: Registered nosave memory: [mem 0xa95b0000-0xaa9affff]
[ 0.073957] PM: Registered nosave memory: [mem 0xaefbf000-0xaf04dfff]
[ 0.073958] PM: Registered nosave memory: [mem 0xaf04e000-0xaf04ffff]
[ 0.073958] PM: Registered nosave memory: [mem 0xaf050000-0xaf065fff]
[ 0.073959] PM: Registered nosave memory: [mem 0xaf066000-0xaf066fff]
[ 0.073960] PM: Registered nosave memory: [mem 0xaf067000-0xaf07efff]
[ 0.073960] PM: Registered nosave memory: [mem 0xaf07f000-0xaf07ffff]
[ 0.073961] PM: Registered nosave memory: [mem 0xaf080000-0xaf08afff]
[ 0.073961] PM: Registered nosave memory: [mem 0xaf08b000-0xaf08bfff]
[ 0.073962] PM: Registered nosave memory: [mem 0xaf08c000-0xaf090fff]
[ 0.073962] PM: Registered nosave memory: [mem 0xaf091000-0xaf091fff]
[ 0.073963] PM: Registered nosave memory: [mem 0xaf092000-0xaf09ffff]
[ 0.073963] PM: Registered nosave memory: [mem 0xaf0a0000-0xaf0a0fff]
[ 0.073964] PM: Registered nosave memory: [mem 0xaf0a1000-0xaf0f1fff]
[ 0.073965] PM: Registered nosave memory: [mem 0xaf0f2000-0xaf136fff]
[ 0.073965] PM: Registered nosave memory: [mem 0xaf137000-0xaf1befff]
[ 0.073966] PM: Registered nosave memory: [mem 0xaf1bf000-0xaf6befff]
[ 0.073966] PM: Registered nosave memory: [mem 0xaf6bf000-0xaf7befff]
[ 0.073967] PM: Registered nosave memory: [mem 0xaf7bf000-0xaf7fefff]
[ 0.073969] PM: Registered nosave memory: [mem 0xaf800000-0xafffffff]
[ 0.073969] PM: Registered nosave memory: [mem 0xb0000000-0xefffffff]
[ 0.073970] PM: Registered nosave memory: [mem 0xf0000000-0xf3ffffff]
[ 0.073970] PM: Registered nosave memory: [mem 0xf4000000-0xfeafffff]
[ 0.073971] PM: Registered nosave memory: [mem 0xfeb00000-0xfeb03fff]
[ 0.073972] PM: Registered nosave memory: [mem 0xfeb04000-0xfebfffff]
[ 0.073972] PM: Registered nosave memory: [mem 0xfec00000-0xfec00fff]
[ 0.073973] PM: Registered nosave memory: [mem 0xfec01000-0xfed0ffff]
[ 0.073973] PM: Registered nosave memory: [mem 0xfed10000-0xfed19fff]
[ 0.073974] PM: Registered nosave memory: [mem 0xfed1a000-0xfed1bfff]
[ 0.073974] PM: Registered nosave memory: [mem 0xfed1c000-0xfed1ffff]
[ 0.073975] PM: Registered nosave memory: [mem 0xfed20000-0xfedfffff]
[ 0.073975] PM: Registered nosave memory: [mem 0xfee00000-0xfee00fff]
[ 0.073976] PM: Registered nosave memory: [mem 0xfee01000-0xffb7ffff]
[ 0.073977] PM: Registered nosave memory: [mem 0xffb80000-0xffffffff]
[ 0.073979] [mem 0xb0000000-0xefffffff] available for PCI devices
[ 0.073980] Booting paravirtualized kernel on bare hardware
[ 0.073983] clocksource: refined-jiffies: mask: 0xffffffff max_cycles: 0xffffffff, max_idle_ns: 7645519600211568 ns
[ 0.073992] random: get_random_bytes called from start_kernel+0x97/0x516 with crng_init=0
[ 0.074000] setup_percpu: NR_CPUS:8192 nr_cpumask_bits:8 nr_cpu_ids:8 nr_node_ids:1
[ 0.074229] percpu: Embedded 46 pages/cpu s151552 r8192 d28672 u262144
[ 0.074237] pcpu-alloc: s151552 r8192 d28672 u262144 alloc=1*2097152
[ 0.074238] pcpu-alloc: [0] 0 1 2 3 4 5 6 7 
[ 0.074269] Built 1 zonelists, mobility grouping on. Total pages: 2051071
[ 0.074270] Policy zone: Normal
[ 0.074272] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-5.0.0-23-generic root=UUID=1461fced-a151-4b5b-bc7f-f54871e5ec87 ro quiet splash vt.handoff=1
[ 0.078005] Calgary: detecting Calgary via BIOS EBDA area
[ 0.078007] Calgary: Unable to locate Rio Grande table in EBDA - bailing!
[ 0.099269] Memory: 7990572K/8334620K available (14339K kernel code, 2335K rwdata, 4312K rodata, 2584K init, 5196K bss, 344048K reserved, 0K cma-reserved)
[ 0.099402] SLUB: HWalign=64, Order=0-3, MinObjects=0, CPUs=8, Nodes=1
[ 0.099408] Kernel/User page tables isolation: enabled
[ 0.099425] ftrace: allocating 41572 entries in 163 pages
[ 0.118046] rcu: Hierarchical RCU implementation.
[ 0.118047] rcu: RCU restricting CPUs from NR_CPUS=8192 to nr_cpu_ids=8.
[ 0.118048] Tasks RCU enabled.
[ 0.118048] rcu: RCU calculated value of scheduler-enlistment delay is 25 jiffies.
[ 0.118049] rcu: Adjusting geometry for rcu_fanout_leaf=16, nr_cpu_ids=8
[ 0.121275] NR_IRQS: 524544, nr_irqs: 488, preallocated irqs: 16
[ 0.121480] vt handoff: transparent VT on vt#1
[ 0.121485] Console: colour dummy device 80x25
[ 0.121490] printk: console [tty0] enabled
[ 0.121506] ACPI: Core revision 20181213
[ 0.121729] clocksource: hpet: mask: 0xffffffff max_cycles: 0xffffffff, max_idle_ns: 133484882848 ns
[ 0.121739] hpet clockevent registered
[ 0.121744] APIC: Switch to symmetric I/O mode setup
[ 0.121815] x2apic: IRQ remapping doesn't support X2APIC mode
[ 0.122255] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[ 0.141744] clocksource: tsc-early: mask: 0xffffffffffffffff max_cycles: 0x22840486f8e, max_idle_ns: 440795274724 ns
[ 0.141757] Calibrating delay loop (skipped), value calculated using timer frequency.. 4789.05 BogoMIPS (lpj=9578104)
[ 0.141759] pid_max: default: 32768 minimum: 301
[ 0.152497] LSM: Security Framework initializing
[ 0.152508] Yama: becoming mindful.
[ 0.152529] AppArmor: AppArmor initialized
[ 0.153659] Dentry cache hash table entries: 1048576 (order: 11, 8388608 bytes)
[ 0.154210] Inode-cache hash table entries: 524288 (order: 10, 4194304 bytes)
[ 0.154242] Mount-cache hash table entries: 16384 (order: 5, 131072 bytes)
[ 0.154261] Mountpoint-cache hash table entries: 16384 (order: 5, 131072 bytes)
[ 0.154481] ENERGY_PERF_BIAS: Set to 'normal', was 'performance'
[ 0.154482] ENERGY_PERF_BIAS: View and update with x86_energy_perf_policy(8)
[ 0.154486] mce: CPU supports 9 MCE banks
[ 0.154497] mce: CPU0: Thermal monitoring enabled (TM1)
[ 0.154509] process: using mwait in idle threads
[ 0.154511] Last level iTLB entries: 4KB 512, 2MB 8, 4MB 8
[ 0.154512] Last level dTLB entries: 4KB 512, 2MB 32, 4MB 32, 1GB 0
[ 0.154514] Spectre V2 : Mitigation: Full generic retpoline
[ 0.154515] Spectre V2 : Spectre v2 / SpectreRSB mitigation: Filling RSB on context switch
[ 0.154515] Spectre V2 : Enabling Restricted Speculation for firmware calls
[ 0.154524] Spectre V2 : mitigation: Enabling conditional Indirect Branch Prediction Barrier
[ 0.154525] Spectre V2 : User space: Mitigation: STIBP via seccomp and prctl
[ 0.154526] Speculative Store Bypass: Mitigation: Speculative Store Bypass disabled via prctl and seccomp
[ 0.154559] MDS: Mitigation: Clear CPU buffers
[ 0.154734] Freeing SMP alternatives memory: 36K
[ 0.157825] TSC deadline timer enabled
[ 0.157829] smpboot: CPU0: Intel(R) Core(TM) i7-3630QM CPU @ 2.40GHz (family: 0x6, model: 0x3a, stepping: 0x9)
[ 0.157934] Performance Events: PEBS fmt1+, IvyBridge events, 16-deep LBR, full-width counters, Intel PMU driver.
[ 0.157956] ... version: 3
[ 0.157956] ... bit width: 48
[ 0.157957] ... generic registers: 4
[ 0.157958] ... value mask: 0000ffffffffffff
[ 0.157958] ... max period: 00007fffffffffff
[ 0.157959] ... fixed-purpose events: 3
[ 0.157959] ... event mask: 000000070000000f
[ 0.157997] rcu: Hierarchical SRCU implementation.
[ 0.158699] random: crng done (trusting CPU's manufacturer)
[ 0.159132] NMI watchdog: Enabled. Permanently consumes one hw-PMU counter.
[ 0.159213] smp: Bringing up secondary CPUs ...
[ 0.159308] x86: Booting SMP configuration:
[ 0.159309] .... node #0, CPUs: #1
[ 0.161896] MDS CPU bug present and SMT on, data leak possible. See [https://www.kernel.org/doc/html/latest/admin-guide/hw-vuln/mds.html](https://www.kernel.org/doc/html/latest/admin-guide/hw-vuln/mds.html) for more details.
[ 0.161911] #2 #3 #4 #5 #6 #7
[ 0.176201] smp: Brought up 1 node, 8 CPUs
[ 0.176201] smpboot: Max logical packages: 1
[ 0.176201] smpboot: Total of 8 processors activated (38312.41 BogoMIPS)
[ 0.178055] devtmpfs: initialized
[ 0.178055] x86/mm: Memory block size: 128MB
[ 0.178489] PM: Registering ACPI NVS region [mem 0xaf6bf000-0xaf7befff] (1048576 bytes)
[ 0.178489] clocksource: jiffies: mask: 0xffffffff max_cycles: 0xffffffff, max_idle_ns: 7645041785100000 ns
[ 0.178489] futex hash table entries: 2048 (order: 5, 131072 bytes)
[ 0.178489] pinctrl core: initialized pinctrl subsystem
[ 0.178489] RTC time: 13:29:18, date: 2019-08-13
[ 0.178489] NET: Registered protocol family 16
[ 0.178489] audit: initializing netlink subsys (disabled)
[ 0.178489] audit: type=2000 audit(1565702958.056:1): state=initialized audit_enabled=0 res=1
[ 0.178489] EISA bus registered
[ 0.178489] cpuidle: using governor ladder
[ 0.178489] cpuidle: using governor menu
[ 0.178489] Simple Boot Flag at 0x44 set to 0x1
[ 0.178489] ACPI FADT declares the system doesn't support PCIe ASPM, so disable it
[ 0.178489] ACPI: bus type PCI registered
[ 0.178489] acpiphp: ACPI Hot Plug PCI Controller Driver version: 0.5
[ 0.178489] PCI: MMCONFIG for domain 0000 [bus 00-3f] at [mem 0xf0000000-0xf3ffffff] (base 0xf0000000)
[ 0.178489] PCI: MMCONFIG at [mem 0xf0000000-0xf3ffffff] reserved in E820
[ 0.178489] PCI: Using configuration type 1 for base access
[ 0.178489] core: PMU erratum BJ122, BV98, HSD29 worked around, HT is on
[ 0.179142] HugeTLB registered 2.00 MiB page size, pre-allocated 0 pages
[ 0.179142] ACPI: Added _OSI(Module Device)
[ 0.179142] ACPI: Added _OSI(Processor Device)
[ 0.179142] ACPI: Added _OSI(3.0 _SCP Extensions)
[ 0.179142] ACPI: Added _OSI(Processor Aggregator Device)
[ 0.179142] ACPI: Added _OSI(Linux-Dell-Video)
[ 0.179142] ACPI: Added _OSI(Linux-Lenovo-NV-HDMI-Audio)
[ 0.179142] ACPI: Added _OSI(Linux-HPI-Hybrid-Graphics)
[ 0.192928] ACPI: 5 ACPI AML tables successfully acquired and loaded
[ 0.194913] ACPI: [Firmware Bug]: BIOS _OSI(Linux) query ignored
[ 0.194913] ACPI: Dynamic OEM Table Load:
[ 0.194913] ACPI: SSDT 0xFFFF8CC1852BD000 00083B (v01 PmRef Cpu0Cst 00003001 INTL 20120111)
[ 0.194913] ACPI: Dynamic OEM Table Load:
[ 0.194913] ACPI: SSDT 0xFFFF8CC18520B000 000303 (v01 PmRef ApIst 00003000 INTL 20120111)
[ 0.194913] ACPI: Dynamic OEM Table Load:
[ 0.194913] ACPI: SSDT 0xFFFF8CC184D53600 000119 (v01 PmRef ApCst 00003000 INTL 20120111)
[ 0.199955] ACPI: EC: EC started
[ 0.199955] ACPI: EC: interrupt blocked
[ 0.200158] ACPI: \_SB_.PCI0.LPCB.EC0_: Used as first EC
[ 0.200160] ACPI: \_SB_.PCI0.LPCB.EC0_: GPE=0x17, EC_CMD/EC_SC=0x66, EC_DATA=0x62
[ 0.200161] ACPI: \_SB_.PCI0.LPCB.EC0_: Used as boot DSDT EC to handle transactions
[ 0.200162] ACPI: Interpreter enabled
[ 0.200189] ACPI: (supports S0 S3 S4 S5)
[ 0.200189] ACPI: Using IOAPIC for interrupt routing
[ 0.200220] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[ 0.200652] ACPI: Enabled 8 GPEs in block 00 to 3F
[ 0.221782] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-3e])
[ 0.221787] acpi PNP0A08:00: _OSC: OS supports [ExtendedConfig ASPM ClockPM Segments MSI]
[ 0.222001] acpi PNP0A08:00: _OSC failed (AE_ERROR); disabling ASPM
[ 0.222587] PCI host bridge to bus 0000:00
[ 0.222590] pci_bus 0000:00: root bus resource [io 0x0000-0x0cf7 window]
[ 0.222591] pci_bus 0000:00: root bus resource [io 0x0d00-0xffff window]
[ 0.222592] pci_bus 0000:00: root bus resource [mem 0x000a0000-0x000bffff window]
[ 0.222593] pci_bus 0000:00: root bus resource [mem 0x000c0000-0x000c3fff window]
[ 0.222594] pci_bus 0000:00: root bus resource [mem 0x000c4000-0x000c7fff window]
[ 0.222595] pci_bus 0000:00: root bus resource [mem 0x000c8000-0x000cbfff window]
[ 0.222596] pci_bus 0000:00: root bus resource [mem 0x000cc000-0x000cffff window]
[ 0.222597] pci_bus 0000:00: root bus resource [mem 0x000d0000-0x000d3fff window]
[ 0.222599] pci_bus 0000:00: root bus resource [mem 0x000d4000-0x000d7fff window]
[ 0.222600] pci_bus 0000:00: root bus resource [mem 0x000d8000-0x000dbfff window]
[ 0.222601] pci_bus 0000:00: root bus resource [mem 0x000dc000-0x000dffff window]
[ 0.222602] pci_bus 0000:00: root bus resource [mem 0xb0000000-0xfeafffff window]
[ 0.222603] pci_bus 0000:00: root bus resource [bus 00-3e]
[ 0.222610] pci 0000:00:00.0: [8086:0154] type 00 class 0x060000
[ 0.222715] pci 0000:00:01.0: [8086:0151] type 01 class 0x060400
[ 0.222756] pci 0000:00:01.0: PME# supported from D0 D3hot D3cold
[ 0.222874] pci 0000:00:14.0: [8086:1e31] type 00 class 0x0c0330
[ 0.222900] pci 0000:00:14.0: reg 0x10: [mem 0xc3400000-0xc340ffff 64bit]
[ 0.222972] pci 0000:00:14.0: PME# supported from D3hot D3cold
[ 0.223065] pci 0000:00:16.0: [8086:1e3a] type 00 class 0x078000
[ 0.223092] pci 0000:00:16.0: reg 0x10: [mem 0xc3414000-0xc341400f 64bit]
[ 0.223168] pci 0000:00:16.0: PME# supported from D0 D3hot D3cold
[ 0.223266] pci 0000:00:1a.0: [8086:1e2d] type 00 class 0x0c0320
[ 0.223289] pci 0000:00:1a.0: reg 0x10: [mem 0xc3419000-0xc34193ff]
[ 0.223375] pci 0000:00:1a.0: PME# supported from D0 D3hot D3cold
[ 0.223474] pci 0000:00:1b.0: [8086:1e20] type 00 class 0x040300
[ 0.223497] pci 0000:00:1b.0: reg 0x10: [mem 0xc3410000-0xc3413fff 64bit]
[ 0.223574] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[ 0.223671] pci 0000:00:1c.0: [8086:1e10] type 01 class 0x060400
[ 0.223762] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[ 0.223865] pci 0000:00:1c.1: [8086:1e12] type 01 class 0x060400
[ 0.223954] pci 0000:00:1c.1: PME# supported from D0 D3hot D3cold
[ 0.224058] pci 0000:00:1c.3: [8086:1e16] type 01 class 0x060400
[ 0.224147] pci 0000:00:1c.3: PME# supported from D0 D3hot D3cold
[ 0.224252] pci 0000:00:1d.0: [8086:1e26] type 00 class 0x0c0320
[ 0.224275] pci 0000:00:1d.0: reg 0x10: [mem 0xc3418000-0xc34183ff]
[ 0.224360] pci 0000:00:1d.0: PME# supported from D0 D3hot D3cold
[ 0.224457] pci 0000:00:1f.0: [8086:1e59] type 00 class 0x060100
[ 0.224649] pci 0000:00:1f.2: [8086:1e03] type 00 class 0x010601
[ 0.224668] pci 0000:00:1f.2: reg 0x10: [io 0x4048-0x404f]
[ 0.224675] pci 0000:00:1f.2: reg 0x14: [io 0x4054-0x4057]
[ 0.224683] pci 0000:00:1f.2: reg 0x18: [io 0x4040-0x4047]
[ 0.224691] pci 0000:00:1f.2: reg 0x1c: [io 0x4050-0x4053]
[ 0.224698] pci 0000:00:1f.2: reg 0x20: [io 0x4020-0x403f]
[ 0.224706] pci 0000:00:1f.2: reg 0x24: [mem 0xc3417000-0xc34177ff]
[ 0.224750] pci 0000:00:1f.2: PME# supported from D3hot
[ 0.224838] pci 0000:00:1f.3: [8086:1e22] type 00 class 0x0c0500
[ 0.224858] pci 0000:00:1f.3: reg 0x10: [mem 0xc3415000-0xc34150ff 64bit]
[ 0.224879] pci 0000:00:1f.3: reg 0x20: [io 0x4000-0x401f]
[ 0.225030] pci 0000:01:00.0: [10de:0fd1] type 00 class 0x030000
[ 0.225048] pci 0000:01:00.0: reg 0x10: [mem 0xc2000000-0xc2ffffff]
[ 0.225058] pci 0000:01:00.0: reg 0x14: [mem 0xb0000000-0xbfffffff 64bit pref]
[ 0.225067] pci 0000:01:00.0: reg 0x1c: [mem 0xc0000000-0xc1ffffff 64bit pref]
[ 0.225074] pci 0000:01:00.0: reg 0x24: [io 0x3000-0x307f]
[ 0.225081] pci 0000:01:00.0: reg 0x30: [mem 0xfff80000-0xffffffff pref]
[ 0.225097] pci 0000:01:00.0: BAR 1: assigned to efifb
[ 0.225152] pci 0000:01:00.0: 16.000 Gb/s available PCIe bandwidth, limited by 2.5 GT/s x8 link at 0000:00:01.0 (capable of 126.016 Gb/s with 8 GT/s x16 link)
[ 0.225233] pci 0000:01:00.1: [10de:0e1b] type 00 class 0x040300
[ 0.225248] pci 0000:01:00.1: reg 0x10: [mem 0xc3000000-0xc3003fff]
[ 0.225389] pci 0000:00:01.0: PCI bridge to [bus 01]
[ 0.225391] pci 0000:00:01.0: bridge window [io 0x3000-0x3fff]
[ 0.225393] pci 0000:00:01.0: bridge window [mem 0xc2000000-0xc30fffff]
[ 0.225396] pci 0000:00:01.0: bridge window [mem 0xb0000000-0xc1ffffff 64bit pref]
[ 0.225701] pci 0000:02:00.0: [1969:1091] type 00 class 0x020000
[ 0.226151] pci 0000:02:00.0: reg 0x10: [mem 0xc3300000-0xc333ffff 64bit]
[ 0.226360] pci 0000:02:00.0: reg 0x18: [io 0x2000-0x207f]
[ 0.228107] pci 0000:02:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[ 0.228828] pci 0000:00:1c.0: PCI bridge to [bus 02]
[ 0.228832] pci 0000:00:1c.0: bridge window [io 0x2000-0x2fff]
[ 0.228836] pci 0000:00:1c.0: bridge window [mem 0xc3300000-0xc33fffff]
[ 0.228915] pci 0000:03:00.0: [168c:0032] type 00 class 0x028000
[ 0.228957] pci 0000:03:00.0: reg 0x10: [mem 0xc3200000-0xc327ffff 64bit]
[ 0.229021] pci 0000:03:00.0: reg 0x30: [mem 0xffff0000-0xffffffff pref]
[ 0.229119] pci 0000:03:00.0: supports D1 D2
[ 0.229120] pci 0000:03:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[ 0.229244] pci 0000:00:1c.1: PCI bridge to [bus 03]
[ 0.229250] pci 0000:00:1c.1: bridge window [mem 0xc3200000-0xc32fffff]
[ 0.229366] pci 0000:04:00.0: [197b:2392] type 00 class 0x088000
[ 0.229413] pci 0000:04:00.0: reg 0x10: [mem 0xc3103000-0xc31030ff]
[ 0.229545] pci 0000:04:00.0: Enabling fixed DMA alias to 00.1
[ 0.229755] pci 0000:04:00.2: [197b:2391] type 00 class 0x080501
[ 0.229801] pci 0000:04:00.2: reg 0x10: [mem 0xc3102000-0xc31020ff]
[ 0.230124] pci 0000:04:00.3: [197b:2393] type 00 class 0x088000
[ 0.230170] pci 0000:04:00.3: reg 0x10: [mem 0xc3101000-0xc31010ff]
[ 0.230489] pci 0000:04:00.4: [197b:2394] type 00 class 0x088000
[ 0.230533] pci 0000:04:00.4: reg 0x10: [mem 0xc3100000-0xc31000ff]
[ 0.230887] pci 0000:00:1c.3: PCI bridge to [bus 04]
[ 0.230893] pci 0000:00:1c.3: bridge window [mem 0xc3100000-0xc31fffff]
[ 0.306089] ACPI: PCI Interrupt Link [LNKA] (IRQs 1 3 4 5 6 10 11 12 14 15) *0, disabled.
[ 0.306179] ACPI: PCI Interrupt Link [LNKB] (IRQs 1 3 4 5 6 10 11 12 14 15) *0, disabled.
[ 0.306264] ACPI: PCI Interrupt Link [LNKC] (IRQs 1 3 4 5 6 10 11 12 14 15) *0, disabled.
[ 0.306346] ACPI: PCI Interrupt Link [LNKD] (IRQs 1 3 4 5 6 10 11 12 14 15) *0, disabled.
[ 0.306428] ACPI: PCI Interrupt Link [LNKE] (IRQs 1 3 4 5 6 10 11 12 14 15) *0, disabled.
[ 0.306511] ACPI: PCI Interrupt Link [LNKF] (IRQs 1 3 4 5 6 10 11 12 14 15) *0, disabled.
[ 0.306592] ACPI: PCI Interrupt Link [LNKG] (IRQs 1 3 4 5 6 10 11 12 14 15) *0, disabled.
[ 0.306674] ACPI: PCI Interrupt Link [LNKH] (IRQs 1 3 4 5 6 10 11 12 14 15) *0, disabled.
[ 0.306837] ACPI: EC: interrupt unblocked
[ 0.306847] ACPI: EC: event unblocked
[ 0.306854] ACPI: \_SB_.PCI0.LPCB.EC0_: GPE=0x17, EC_CMD/EC_SC=0x66, EC_DATA=0x62
[ 0.306856] ACPI: \_SB_.PCI0.LPCB.EC0_: Used as boot DSDT EC to handle transactions and events
[ 0.306921] SCSI subsystem initialized
[ 0.306921] libata version 3.00 loaded.
[ 0.306921] pci 0000:01:00.0: vgaarb: setting as boot VGA device
[ 0.306921] pci 0000:01:00.0: vgaarb: VGA device added: decodes=io+mem,owns=io+mem,locks=none
[ 0.306921] pci 0000:01:00.0: vgaarb: bridge control possible
[ 0.306921] vgaarb: loaded
[ 0.306921] ACPI: bus type USB registered
[ 0.306921] usbcore: registered new interface driver usbfs
[ 0.306921] usbcore: registered new interface driver hub
[ 0.306921] usbcore: registered new device driver usb
[ 0.306921] pps_core: LinuxPPS API ver. 1 registered
[ 0.306921] pps_core: Software ver. 5.3.6 - Copyright 2005-2007 Rodolfo Giometti <giometti@linux.it>
[ 0.306921] PTP clock support registered
[ 0.306921] EDAC MC: Ver: 3.0.0
[ 0.306921] Registered efivars operations
[ 0.310712] PCI: Using ACPI for IRQ routing
[ 0.314793] PCI: pci_cache_line_size set to 64 bytes
[ 0.314954] e820: reserve RAM buffer [mem 0x00088000-0x0008ffff]
[ 0.314956] e820: reserve RAM buffer [mem 0xa95b0000-0xabffffff]
[ 0.314957] e820: reserve RAM buffer [mem 0xaefbf000-0xafffffff]
[ 0.314959] e820: reserve RAM buffer [mem 0xaf800000-0xafffffff]
[ 0.314960] e820: reserve RAM buffer [mem 0x24f000000-0x24fffffff]
[ 0.315058] NetLabel: Initializing
[ 0.315059] NetLabel: domain hash size = 128
[ 0.315059] NetLabel: protocols = UNLABELED CIPSOv4 CALIPSO
[ 0.315074] NetLabel: unlabeled traffic allowed by default
[ 0.315088] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0, 0, 0, 0, 0
[ 0.315088] hpet0: 8 comparators, 64-bit 14.318180 MHz counter
[ 0.316298] clocksource: Switched to clocksource tsc-early
[ 0.325976] VFS: Disk quotas dquot_6.6.0
[ 0.325993] VFS: Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[ 0.326100] AppArmor: AppArmor Filesystem Enabled
[ 0.326129] pnp: PnP ACPI init
[ 0.326294] system 00:00: [io 0x0680-0x069f] has been reserved
[ 0.326296] system 00:00: [io 0x1100-0x110f] has been reserved
[ 0.326297] system 00:00: [io 0xffff] has been reserved
[ 0.326299] system 00:00: [io 0xffff] has been reserved
[ 0.326300] system 00:00: [io 0x0400-0x0453] has been reserved
[ 0.326303] system 00:00: [io 0x0458-0x047f] has been reserved
[ 0.326304] system 00:00: [io 0x0500-0x057f] has been reserved
[ 0.326305] system 00:00: [io 0x164e-0x164f] has been reserved
[ 0.326306] system 00:00: [io 0x0d60-0x0d63] has been reserved
[ 0.326312] system 00:00: Plug and Play ACPI device, IDs PNP0c02 (active)
[ 0.326340] pnp 00:01: Plug and Play ACPI device, IDs PNP0b00 (active)
[ 0.326404] system 00:02: [io 0x0454-0x0457] has been reserved
[ 0.326408] system 00:02: Plug and Play ACPI device, IDs INT3f0d PNP0c02 (active)
[ 0.326435] pnp 00:03: Plug and Play ACPI device, IDs PNP0303 (active)
[ 0.326484] pnp 00:04: Plug and Play ACPI device, IDs SYN2b02 SYN2b00 SYN0002 PNP0f13 (active)
[ 0.405973] system 00:05: [mem 0xfed1c000-0xfed1ffff] has been reserved
[ 0.405974] system 00:05: [mem 0xfed10000-0xfed17fff] has been reserved
[ 0.405976] system 00:05: [mem 0xfed18000-0xfed18fff] has been reserved
[ 0.405977] system 00:05: [mem 0xfed19000-0xfed19fff] has been reserved
[ 0.405979] system 00:05: [mem 0xf0000000-0xf3ffffff] has been reserved
[ 0.405980] system 00:05: [mem 0xfed20000-0xfed3ffff] has been reserved
[ 0.405981] system 00:05: [mem 0xfed90000-0xfed93fff] has been reserved
[ 0.405982] system 00:05: [mem 0xff000000-0xff000fff] has been reserved
[ 0.405984] system 00:05: [mem 0xff010000-0xffffffff] could not be reserved
[ 0.405985] system 00:05: [mem 0xfee00000-0xfeefffff] could not be reserved
[ 0.405987] system 00:05: [mem 0xc3500000-0xc3500fff] has been reserved
[ 0.405991] system 00:05: Plug and Play ACPI device, IDs PNP0c02 (active)
[ 0.406316] system 00:06: [mem 0x20000000-0x201fffff] could not be reserved
[ 0.406318] system 00:06: [mem 0x40004000-0x40004fff] could not be reserved
[ 0.406321] system 00:06: Plug and Play ACPI device, IDs PNP0c01 (active)
[ 0.406345] pnp: PnP ACPI: found 7 devices
[ 0.412173] clocksource: acpi_pm: mask: 0xffffff max_cycles: 0xffffff, max_idle_ns: 2085701024 ns
[ 0.412177] pci 0000:01:00.0: can't claim BAR 6 [mem 0xfff80000-0xffffffff pref]: no compatible bridge window
[ 0.412180] pci 0000:03:00.0: can't claim BAR 6 [mem 0xffff0000-0xffffffff pref]: no compatible bridge window
[ 0.412215] pci 0000:01:00.0: BAR 6: assigned [mem 0xc3080000-0xc30fffff pref]
[ 0.412217] pci 0000:00:01.0: PCI bridge to [bus 01]
[ 0.412219] pci 0000:00:01.0: bridge window [io 0x3000-0x3fff]
[ 0.412222] pci 0000:00:01.0: bridge window [mem 0xc2000000-0xc30fffff]
[ 0.412224] pci 0000:00:01.0: bridge window [mem 0xb0000000-0xc1ffffff 64bit pref]
[ 0.412227] pci 0000:00:1c.0: PCI bridge to [bus 02]
[ 0.412230] pci 0000:00:1c.0: bridge window [io 0x2000-0x2fff]
[ 0.412235] pci 0000:00:1c.0: bridge window [mem 0xc3300000-0xc33fffff]
[ 0.412243] pci 0000:03:00.0: BAR 6: assigned [mem 0xc3280000-0xc328ffff pref]
[ 0.412245] pci 0000:00:1c.1: PCI bridge to [bus 03]
[ 0.412250] pci 0000:00:1c.1: bridge window [mem 0xc3200000-0xc32fffff]
[ 0.412258] pci 0000:00:1c.3: PCI bridge to [bus 04]
[ 0.412262] pci 0000:00:1c.3: bridge window [mem 0xc3100000-0xc31fffff]
[ 0.412272] pci_bus 0000:00: resource 4 [io 0x0000-0x0cf7 window]
[ 0.412273] pci_bus 0000:00: resource 5 [io 0x0d00-0xffff window]
[ 0.412274] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff window]
[ 0.412275] pci_bus 0000:00: resource 7 [mem 0x000c0000-0x000c3fff window]
[ 0.412276] pci_bus 0000:00: resource 8 [mem 0x000c4000-0x000c7fff window]
[ 0.412277] pci_bus 0000:00: resource 9 [mem 0x000c8000-0x000cbfff window]
[ 0.412278] pci_bus 0000:00: resource 10 [mem 0x000cc000-0x000cffff window]
[ 0.412280] pci_bus 0000:00: resource 11 [mem 0x000d0000-0x000d3fff window]
[ 0.412281] pci_bus 0000:00: resource 12 [mem 0x000d4000-0x000d7fff window]
[ 0.412282] pci_bus 0000:00: resource 13 [mem 0x000d8000-0x000dbfff window]
[ 0.412283] pci_bus 0000:00: resource 14 [mem 0x000dc000-0x000dffff window]
[ 0.412284] pci_bus 0000:00: resource 15 [mem 0xb0000000-0xfeafffff window]
[ 0.412285] pci_bus 0000:01: resource 0 [io 0x3000-0x3fff]
[ 0.412286] pci_bus 0000:01: resource 1 [mem 0xc2000000-0xc30fffff]
[ 0.412287] pci_bus 0000:01: resource 2 [mem 0xb0000000-0xc1ffffff 64bit pref]
[ 0.412289] pci_bus 0000:02: resource 0 [io 0x2000-0x2fff]
[ 0.412290] pci_bus 0000:02: resource 1 [mem 0xc3300000-0xc33fffff]
[ 0.412291] pci_bus 0000:03: resource 1 [mem 0xc3200000-0xc32fffff]
[ 0.412292] pci_bus 0000:04: resource 1 [mem 0xc3100000-0xc31fffff]
[ 0.412417] NET: Registered protocol family 2
[ 0.412562] tcp_listen_portaddr_hash hash table entries: 4096 (order: 4, 65536 bytes)
[ 0.412590] TCP established hash table entries: 65536 (order: 7, 524288 bytes)
[ 0.412710] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[ 0.412817] TCP: Hash tables configured (established 65536 bind 65536)
[ 0.412853] UDP hash table entries: 4096 (order: 5, 131072 bytes)
[ 0.412873] UDP-Lite hash table entries: 4096 (order: 5, 131072 bytes)
[ 0.412951] NET: Registered protocol family 1
[ 0.412955] NET: Registered protocol family 44
[ 1.141879] pci 0000:00:1a.0: quirk_usb_early_handoff+0x0/0x6a0 took 710450 usecs
[ 1.161874] pci 0000:00:1d.0: quirk_usb_early_handoff+0x0/0x6a0 took 19506 usecs
[ 1.161906] pci 0000:01:00.0: Video device with shadowed ROM at [mem 0x000c0000-0x000dffff]
[ 1.161917] pci 0000:01:00.1: Linked as a consumer to 0000:01:00.0
[ 1.161924] pci 0000:02:00.0: set MSI_INTX_DISABLE_BUG flag
[ 1.161981] PCI: CLS 64 bytes, default 64
[ 1.162059] Unpacking initramfs...
[ 1.714383] Freeing initrd memory: 39264K
[ 1.714416] PCI-DMA: Using software bounce buffering for IO (SWIOTLB)
[ 1.714418] software IO TLB: mapped [mem 0xa39c0000-0xa79c0000] (64MB)
[ 1.714715] check: Scanning for low memory corruption every 60 seconds
[ 1.716519] Initialise system trusted keyrings
[ 1.716527] Key type blacklist registered
[ 1.716560] workingset: timestamp_bits=36 max_order=21 bucket_order=0
[ 1.717978] zbud: loaded
[ 1.718414] squashfs: version 4.0 (2009/01/31) Phillip Lougher
[ 1.718605] fuse init (API version 7.28)
[ 1.758336] Key type asymmetric registered
[ 1.758337] Asymmetric key parser 'x509' registered
[ 1.758347] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 243)
[ 1.758387] io scheduler mq-deadline registered
[ 1.759096] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[ 1.759155] efifb: probing for efifb
[ 1.759163] pmd_set_huge: Cannot satisfy [mem 0xb0000000-0xb0200000] with a huge-page mapping due to MTRR override.
[ 1.759174] efifb: framebuffer at 0xb0000000, using 4224k, total 4224k
[ 1.759175] efifb: mode is 1366x768x32, linelength=5632, pages=1
[ 1.759176] efifb: scrolling: redraw
[ 1.759177] efifb: Truecolor: size=8:8:8:8, shift=24:16:8:0
[ 1.759270] Console: switching to colour frame buffer device 170x48
[ 1.759289] fb0: EFI VGA frame buffer device
[ 1.759297] intel_idle: MWAIT substates: 0x21120
[ 1.759298] intel_idle: v0.4.1 model 0x3A
[ 1.759693] intel_idle: lapic_timer_reliable_states 0xffffffff
[ 1.759821] ACPI: AC Adapter [ACAD] (on-line)
[ 1.759885] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:01/PNP0C0C:00/input/input0
[ 1.759893] ACPI: Power Button [PWRB]
[ 1.759921] input: Sleep Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:01/PNP0C0E:00/input/input1
[ 1.759927] ACPI: Sleep Button [SLPB]
[ 1.759970] input: Lid Switch as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0D:00/input/input2
[ 1.760011] ACPI: Lid Switch [LID0]
[ 1.760064] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input3
[ 1.760081] ACPI: Power Button [PWRF]
[ 1.764081] thermal LNXTHERM:00: registered as thermal_zone0
[ 1.764083] ACPI: Thermal Zone [TZ00] (0 C)
[ 1.764249] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[ 1.766041] Linux agpgart interface v0.103
[ 1.768556] loop: module loaded
[ 1.768740] libphy: Fixed MDIO Bus: probed
[ 1.768741] tun: Universal TUN/TAP device driver, 1.6
[ 1.768767] PPP generic driver version 2.4.2
[ 1.768800] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[ 1.768803] ehci-pci: EHCI PCI platform driver
[ 1.768931] ehci-pci 0000:00:1a.0: EHCI Host Controller
[ 1.768936] ehci-pci 0000:00:1a.0: new USB bus registered, assigned bus number 1
[ 1.768948] ehci-pci 0000:00:1a.0: debug port 2
[ 1.772853] ehci-pci 0000:00:1a.0: cache line size of 64 is not supported
[ 1.772865] ehci-pci 0000:00:1a.0: irq 16, io mem 0xc3419000
[ 1.785844] ehci-pci 0000:00:1a.0: USB 2.0 started, EHCI 1.00
[ 1.785913] usb usb1: New USB device found, idVendor=1d6b, idProduct=0002, bcdDevice= 5.00
[ 1.785914] usb usb1: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[ 1.785916] usb usb1: Product: EHCI Host Controller
[ 1.785917] usb usb1: Manufacturer: Linux 5.0.0-23-generic ehci_hcd
[ 1.785918] usb usb1: SerialNumber: 0000:00:1a.0
[ 1.786177] hub 1-0:1.0: USB hub found
[ 1.786186] hub 1-0:1.0: 2 ports detected
[ 1.786497] ehci-pci 0000:00:1d.0: EHCI Host Controller
[ 1.786503] ehci-pci 0000:00:1d.0: new USB bus registered, assigned bus number 2
[ 1.786514] ehci-pci 0000:00:1d.0: debug port 2
[ 1.790401] ehci-pci 0000:00:1d.0: cache line size of 64 is not supported
[ 1.790416] ehci-pci 0000:00:1d.0: irq 23, io mem 0xc3418000
[ 1.805839] ehci-pci 0000:00:1d.0: USB 2.0 started, EHCI 1.00
[ 1.805918] usb usb2: New USB device found, idVendor=1d6b, idProduct=0002, bcdDevice= 5.00
[ 1.805919] usb usb2: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[ 1.805920] usb usb2: Product: EHCI Host Controller
[ 1.805921] usb usb2: Manufacturer: Linux 5.0.0-23-generic ehci_hcd
[ 1.805922] usb usb2: SerialNumber: 0000:00:1d.0
[ 1.806155] hub 2-0:1.0: USB hub found
[ 1.806164] hub 2-0:1.0: 2 ports detected
[ 1.806326] ehci-platform: EHCI generic platform driver
[ 1.806344] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[ 1.806350] ohci-pci: OHCI PCI platform driver
[ 1.806363] ohci-platform: OHCI generic platform driver
[ 1.806373] uhci_hcd: USB Universal Host Controller Interface driver
[ 1.806584] xhci_hcd 0000:00:14.0: xHCI Host Controller
[ 1.806593] xhci_hcd 0000:00:14.0: new USB bus registered, assigned bus number 3
[ 1.807650] xhci_hcd 0000:00:14.0: hcc params 0x20007181 hci version 0x100 quirks 0x000000000000b930
[ 1.807656] xhci_hcd 0000:00:14.0: cache line size of 64 is not supported
[ 1.807820] usb usb3: New USB device found, idVendor=1d6b, idProduct=0002, bcdDevice= 5.00
[ 1.807821] usb usb3: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[ 1.807823] usb usb3: Product: xHCI Host Controller
[ 1.807824] usb usb3: Manufacturer: Linux 5.0.0-23-generic xhci-hcd
[ 1.807825] usb usb3: SerialNumber: 0000:00:14.0
[ 1.808019] hub 3-0:1.0: USB hub found
[ 1.808032] hub 3-0:1.0: 4 ports detected
[ 1.808486] xhci_hcd 0000:00:14.0: xHCI Host Controller
[ 1.808490] xhci_hcd 0000:00:14.0: new USB bus registered, assigned bus number 4
[ 1.808493] xhci_hcd 0000:00:14.0: Host supports USB 3.0 SuperSpeed
[ 1.808528] usb usb4: New USB device found, idVendor=1d6b, idProduct=0003, bcdDevice= 5.00
[ 1.808529] usb usb4: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[ 1.808530] usb usb4: Product: xHCI Host Controller
[ 1.808531] usb usb4: Manufacturer: Linux 5.0.0-23-generic xhci-hcd
[ 1.808532] usb usb4: SerialNumber: 0000:00:14.0
[ 1.808703] hub 4-0:1.0: USB hub found
[ 1.808715] hub 4-0:1.0: 4 ports detected
[ 1.809156] i8042: PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:MSS0] at 0x60,0x64 irq 1,12
[ 1.811438] serio: i8042 KBD port at 0x60,0x64 irq 1
[ 1.811443] serio: i8042 AUX port at 0x60,0x64 irq 12
[ 1.811697] mousedev: PS/2 mouse device common for all mice
[ 1.812077] rtc_cmos 00:01: RTC can wake from S4
[ 1.812220] rtc_cmos 00:01: registered as rtc0
[ 1.812237] rtc_cmos 00:01: alarms up to one month, 242 bytes nvram, hpet irqs
[ 1.812244] i2c /dev entries driver
[ 1.812328] device-mapper: uevent: version 1.0.3
[ 1.812382] device-mapper: ioctl: 4.39.0-ioctl (2018-04-03) initialised: [EMAIL="dm-devel@redhat.com"]dm-devel@redhat.com[/EMAIL]
[ 1.812402] platform eisa.0: Probing EISA bus 0
[ 1.812403] platform eisa.0: EISA: Cannot allocate resource for mainboard
[ 1.812404] platform eisa.0: Cannot allocate resource for EISA slot 1
[ 1.812405] platform eisa.0: Cannot allocate resource for EISA slot 2
[ 1.812406] platform eisa.0: Cannot allocate resource for EISA slot 3
[ 1.812407] platform eisa.0: Cannot allocate resource for EISA slot 4
[ 1.812408] platform eisa.0: Cannot allocate resource for EISA slot 5
[ 1.812409] platform eisa.0: Cannot allocate resource for EISA slot 6
[ 1.812410] platform eisa.0: Cannot allocate resource for EISA slot 7
[ 1.812411] platform eisa.0: Cannot allocate resource for EISA slot 8
[ 1.812412] platform eisa.0: EISA: Detected 0 cards
[ 1.812417] intel_pstate: Intel P-state driver initializing
[ 1.812832] ledtrig-cpu: registered to indicate activity on CPUs
[ 1.812834] EFI Variables Facility v0.08 2004-May-17
[ 1.818437] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input4
[ 1.819434] NET: Registered protocol family 10
[ 1.824279] Segment Routing with IPv6
[ 1.824294] NET: Registered protocol family 17
[ 1.824325] Key type dns_resolver registered
[ 1.824640] RAS: Correctable Errors collector initialized.
[ 1.824660] microcode: sig=0x306a9, pf=0x10, revision=0x21
[ 1.824727] microcode: Microcode Update Driver: v2.2.
[ 1.824736] sched_clock: Marking stable (1824438156, 286107)->(1851825309, -27101046)
[ 1.824918] registered taskstats version 1
[ 1.824925] Loading compiled-in X.509 certificates
[ 1.826360] Loaded X.509 cert 'Build time autogenerated kernel key: caf27ed67be6a8d4c681ef3325a4613a9f2d2943'
[ 1.827256] Loaded UEFI:db cert 'Microsoft Windows Production PCA 2011: a92902398e16c49778cd90f99e4f9ae17c55af53' linked to secondary sys keyring
[ 1.827273] Loaded UEFI:db cert 'Microsoft Corporation UEFI CA 2011: 13adbf4309bd82709c8cd54f316ed522988a1bd4' linked to secondary sys keyring
[ 1.827284] Couldn't get size: 0x800000000000000e
[ 1.827286] MODSIGN: Couldn't get UEFI MokListRT
[ 1.828599] zswap: loaded using pool lzo/zbud
[ 1.834043] Key type big_key registered
[ 1.834046] Key type trusted registered
[ 1.836350] Key type encrypted registered
[ 1.836353] AppArmor: AppArmor sha1 policy hashing enabled
[ 1.837776] battery: ACPI: Battery Slot [BAT1] (battery absent)
[ 1.838711] ima: No TPM chip found, activating TPM-bypass!
[ 1.838713] ima: Allocated hash algorithm: sha1
[ 1.838719] No architecture policies found
[ 1.838729] evm: Initialising EVM extended attributes:
[ 1.838729] evm: security.selinux
[ 1.838730] evm: security.SMACK64
[ 1.838730] evm: security.SMACK64EXEC
[ 1.838730] evm: security.SMACK64TRANSMUTE
[ 1.838731] evm: security.SMACK64MMAP
[ 1.838731] evm: security.apparmor
[ 1.838731] evm: security.ima
[ 1.838732] evm: security.capability
[ 1.838732] evm: HMAC attrs: 0x1
[ 1.839050] Magic number: 15:293:483
[ 1.839166] rtc_cmos 00:01: setting system clock to 2019-08-13T13:29:20 UTC (1565702960)
[ 1.840331] Freeing unused decrypted memory: 2040K
[ 1.840681] Freeing unused kernel image memory: 2584K
[ 1.865772] Write protecting the kernel read-only data: 22528k
[ 1.866263] Freeing unused kernel image memory: 2016K
[ 1.866476] Freeing unused kernel image memory: 1832K
[ 1.874752] x86/mm: Checked W+X mappings: passed, no W+X pages found.
[ 1.874753] x86/mm: Checking user space page tables
[ 1.882679] x86/mm: Checked W+X mappings: passed, no W+X pages found.
[ 1.882680] Run /init as init process
[ 1.951918] sdhci: Secure Digital Host Controller Interface driver
[ 1.951919] sdhci: Copyright(c) Pierre Ossman
[ 1.954797] ahci 0000:00:1f.2: version 3.0
[ 1.954818] sdhci-pci 0000:04:00.0: SDHCI controller found [197b:2392] (rev 30)
[ 1.956183] ahci 0000:00:1f.2: SSS flag set, parallel bus scan disabled
[ 1.956558] mmc0 bounce up to 128 segments into one, max segment size 65536 bytes
[ 1.956693] mmc0: SDHCI controller on PCI [0000:04:00.0] using DMA
[ 1.956715] sdhci-pci 0000:04:00.2: SDHCI controller found [197b:2391] (rev 30)
[ 1.957157] sdhci-pci 0000:04:00.2: Refusing to bind to secondary interface.
[ 1.962681] ACPI: Video Device [PEGP] (multi-head: yes rom: yes post: no)
[ 1.966270] ahci 0000:00:1f.2: AHCI 0001.0300 32 slots 6 ports 6 Gbps 0x6 impl SATA mode
[ 1.966274] ahci 0000:00:1f.2: flags: 64bit ncq stag pm led clo pio slum part ems apst 
[ 1.973029] acpi device:3b: registered as cooling_device8
[ 1.974835] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:3a/LNXVIDEO:00/input/input7
[ 1.974896] [Firmware Bug]: Duplicate ACPI video bus devices for the same VGA controller, please try module parameter "video.allow_duplicates=1"if the current driver doesn't work.
[ 1.974900] [Firmware Bug]: Duplicate ACPI video bus devices for the same VGA controller, please try module parameter "video.allow_duplicates=1"if the current driver doesn't work.
[ 1.974904] [Firmware Bug]: Duplicate ACPI video bus devices for the same VGA controller, please try module parameter "video.allow_duplicates=1"if the current driver doesn't work.
[ 1.974909] [Firmware Bug]: Duplicate ACPI video bus devices for the same VGA controller, please try module parameter "video.allow_duplicates=1"if the current driver doesn't work.
[ 1.974913] [Firmware Bug]: Duplicate ACPI video bus devices for the same VGA controller, please try module parameter "video.allow_duplicates=1"if the current driver doesn't work.
[ 1.978282] scsi host0: ahci
[ 1.978471] scsi host1: ahci
[ 1.978611] scsi host2: ahci
[ 1.978696] scsi host3: ahci
[ 1.978761] scsi host4: ahci
[ 1.980392] scsi host5: ahci
[ 1.980466] ata1: DUMMY
[ 1.980470] ata2: SATA max UDMA/133 abar m2048@0xc3417000 port 0xc3417180 irq 25
[ 1.980473] ata3: SATA max UDMA/133 abar m2048@0xc3417000 port 0xc3417200 irq 25
[ 1.980473] ata4: DUMMY
[ 1.980474] ata5: DUMMY
[ 1.980475] ata6: DUMMY
[ 1.980667] alx 0000:02:00.0 eth0: Qualcomm Atheros AR816x/AR817x Ethernet [b8:88:e3:91:7b:fe]
[ 1.981369] alx 0000:02:00.0 enp2s0: renamed from eth0
[ 2.045836] tsc: Refined TSC clocksource calibration: 2394.574 MHz
[ 2.045855] clocksource: tsc: mask: 0xffffffffffffffff max_cycles: 0x2284319c3df, max_idle_ns: 440795223778 ns
[ 2.045909] clocksource: Switched to clocksource tsc
[ 2.089805] usb 2-1: new high-speed USB device number 2 using ehci-pci
[ 2.089836] usb 1-1: new high-speed USB device number 2 using ehci-pci
[ 2.246540] usb 1-1: New USB device found, idVendor=8087, idProduct=0024, bcdDevice= 0.00
[ 2.246542] usb 1-1: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[ 2.246584] usb 2-1: New USB device found, idVendor=8087, idProduct=0024, bcdDevice= 0.00
[ 2.246585] usb 2-1: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[ 2.246861] hub 2-1:1.0: USB hub found
[ 2.246906] hub 1-1:1.0: USB hub found
[ 2.246919] hub 2-1:1.0: 6 ports detected
[ 2.247053] hub 1-1:1.0: 6 ports detected
[ 2.292829] ata2: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[ 2.299386] ata2.00: ATA-8: ST1000LM024 HN-M101MBB, 2AR10001, max UDMA/100
[ 2.299388] ata2.00: 1953525168 sectors, multi 0: LBA48 NCQ (depth 32)
[ 2.306060] ata2.00: configured for UDMA/100
[ 2.306476] scsi 1:0:0:0: Direct-Access ATA ST1000LM024 HN-M 0001 PQ: 0 ANSI: 5
[ 2.306903] sd 1:0:0:0: Attached scsi generic sg0 type 0
[ 2.307077] sd 1:0:0:0: [sda] 1953525168 512-byte logical blocks: (1.00 TB/932 GiB)
[ 2.307079] sd 1:0:0:0: [sda] 4096-byte physical blocks
[ 2.307151] sd 1:0:0:0: [sda] Write Protect is off
[ 2.307152] sd 1:0:0:0: [sda] Mode Sense: 00 3a 00 00
[ 2.307240] sd 1:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[ 2.334387] sda:
[ 2.335200] sd 1:0:0:0: [sda] Attached SCSI disk
[ 2.342728] psmouse serio1: synaptics: queried max coordinates: x [..5702], y [..4730]
[ 2.374376] psmouse serio1: synaptics: queried min coordinates: x [1242..], y [1124..]
[ 2.374382] psmouse serio1: synaptics: Your touchpad (PNP: SYN2b02 SYN2b00 SYN0002 PNP0f13) says it can support a different bus. If i2c-hid and hid-rmi are not used, you might want to try setting psmouse.synaptics_intertouch to 1 and report this to [EMAIL="linux-input@vger.kernel.org"]linux-input@vger.kernel.org[/EMAIL].
[ 2.433928] psmouse serio1: synaptics: Touchpad model: 1, fw: 8.1, id: 0x1e2b1, caps: 0xd00123/0x840300/0x126c00/0x0, board id: 2132, fw id: 1180104
[ 2.473911] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input6
[ 2.533845] usb 2-1.6: new full-speed USB device number 3 using ehci-pci
[ 2.533848] usb 1-1.3: new full-speed USB device number 3 using ehci-pci
[ 2.621276] ata3: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[ 2.635215] ata3.00: ATA-8: KINGSTON SV300S37A120G, 605ABBF2, max UDMA/133
[ 2.635217] ata3.00: 234441648 sectors, multi 1: LBA48 NCQ (depth 32), AA
[ 2.641467] ata3.00: configured for UDMA/133
[ 2.644339] usb 1-1.3: New USB device found, idVendor=0cf3, idProduct=3004, bcdDevice= 0.01
[ 2.644342] usb 1-1.3: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[ 2.644345] usb 1-1.3: Product: Bluetooth USB Host Controller
[ 2.644347] usb 1-1.3: Manufacturer: Atheros Communications
[ 2.644349] usb 1-1.3: SerialNumber: Alaska Day 2006
[ 2.645582] usb 2-1.6: New USB device found, idVendor=046d, idProduct=c52b, bcdDevice=12.03
[ 2.645584] usb 2-1.6: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[ 2.645585] usb 2-1.6: Product: USB Receiver
[ 2.645585] usb 2-1.6: Manufacturer: Logitech
[ 2.649420] hidraw: raw HID events driver (C) Jiri Kosina
[ 2.651674] scsi 2:0:0:0: Direct-Access ATA KINGSTON SV300S3 BBF2 PQ: 0 ANSI: 5
[ 2.651874] sd 2:0:0:0: Attached scsi generic sg1 type 0
[ 2.651920] sd 2:0:0:0: [sdb] 234441648 512-byte logical blocks: (120 GB/112 GiB)
[ 2.651934] sd 2:0:0:0: [sdb] Write Protect is off
[ 2.651936] sd 2:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[ 2.651959] sd 2:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[ 2.652866] sdb: sdb1 sdb2
[ 2.653143] sd 2:0:0:0: [sdb] Attached SCSI disk
[ 2.655187] usbcore: registered new interface driver usbhid
[ 2.655188] usbhid: USB HID core driver
[ 2.658473] logitech-djreceiver 0003:046D:C52B.0003: hiddev0,hidraw0: USB HID v1.11 Device [Logitech USB Receiver] on usb-0000:00:1d.0-1.6/input2
[ 2.779500] input: Logitech Unifying Device. Wireless PID:4060 Keyboard as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.6/2-1.6:1.2/0003:046D:C52B.0003/0003:046D:4060.0004/input/input8
[ 2.779567] input: Logitech Unifying Device. Wireless PID:4060 Mouse as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.6/2-1.6:1.2/0003:046D:C52B.0003/0003:046D:4060.0004/input/input9
[ 2.779644] input: Logitech Unifying Device. Wireless PID:4060 Consumer Control as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.6/2-1.6:1.2/0003:046D:C52B.0003/0003:046D:4060.0004/input/input10
[ 2.779685] input: Logitech Unifying Device. Wireless PID:4060 System Control as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.6/2-1.6:1.2/0003:046D:C52B.0003/0003:046D:4060.0004/input/input11
[ 2.779731] hid-generic 0003:046D:4060.0004: input,hidraw1: USB HID v1.11 Keyboard [Logitech Unifying Device. Wireless PID:4060] on usb-0000:00:1d.0-1.6:1
[ 2.850390] usb 4-1: new SuperSpeed Gen 1 USB device number 2 using xhci_hcd
[ 2.953451] input: Logitech MX Master as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.6/2-1.6:1.2/0003:046D:C52B.0003/0003:046D:4060.0004/input/input15
[ 2.953583] logitech-hidpp-device 0003:046D:4060.0004: input,hidraw1: USB HID v1.11 Keyboard [Logitech MX Master] on usb-0000:00:1d.0-1.6:1
[ 2.997786] usb 3-3: new low-speed USB device number 3 using xhci_hcd
[ 3.003253] EXT4-fs (sdb2): mounted filesystem with ordered data mode. Opts: (null)
[ 3.054595] usb 4-1: New USB device found, idVendor=04f2, idProduct=b331, bcdDevice=60.10
[ 3.054599] usb 4-1: New USB device strings: Mfr=3, Product=1, SerialNumber=2
[ 3.054601] usb 4-1: Product: Lenovo EasyCamera
[ 3.054603] usb 4-1: Manufacturer: Chicony Electronics Co.,Ltd.
[ 3.054605] usb 4-1: SerialNumber: 0x0001
[ 3.140875] systemd[1]: systemd 237 running in system mode. (+PAM +AUDIT +SELINUX +IMA +APPARMOR +SMACK +SYSVINIT +UTMP +LIBCRYPTSETUP +GCRYPT +GNUTLS +ACL +XZ +LZ4 +SECCOMP +BLKID +ELFUTILS +KMOD -IDN2 +IDN -PCRE2 default-hierarchy=hybrid)
[ 3.158244] systemd[1]: Detected architecture x86-64.
[ 3.160883] systemd[1]: Set hostname to <jeffe-Lenovo-IdeaPad-Y400>.
[ 3.165653] usb 3-3: New USB device found, idVendor=04d9, idProduct=4545, bcdDevice= 1.05
[ 3.165655] usb 3-3: New USB device strings: Mfr=0, Product=2, SerialNumber=0
[ 3.165655] usb 3-3: Product: USB Keyboard
[ 3.176160] input: USB Keyboard as /devices/pci0000:00/0000:00:14.0/usb3/3-3/3-3:1.0/0003:04D9:4545.0005/input/input16
[ 3.233844] hid-generic 0003:04D9:4545.0005: input,hidraw2: USB HID v1.10 Keyboard [USB Keyboard] on usb-0000:00:14.0-3/input0
[ 3.256371] input: USB Keyboard Consumer Control as /devices/pci0000:00/0000:00:14.0/usb3/3-3/3-3:1.1/0003:04D9:4545.0006/input/input17
[ 3.274518] systemd[1]: Started Forward Password Requests to Wall Directory Watch.
[ 3.274545] systemd[1]: Reached target User and Group Name Lookups.
[ 3.274696] systemd[1]: Created slice User and Session Slice.
[ 3.274852] systemd[1]: Set up automount Arbitrary Executable File Formats File System Automount Point.
[ 3.274966] systemd[1]: Created slice System Slice.
[ 3.275051] systemd[1]: Listening on Journal Socket.
[ 3.275604] systemd[1]: Starting Create list of required static device nodes for the current kernel...
[ 3.291085] lp: driver loaded but no devices found
[ 3.292893] EXT4-fs (sdb2): re-mounted. Opts: errors=remount-ro
[ 3.295894] ppdev: user-space parallel port driver
[ 3.313871] input: USB Keyboard System Control as /devices/pci0000:00/0000:00:14.0/usb3/3-3/3-3:1.1/0003:04D9:4545.0006/input/input18
[ 3.313979] hid-generic 0003:04D9:4545.0006: input,hidraw3: USB HID v1.10 Device [USB Keyboard] on usb-0000:00:14.0-3/input1
[ 3.376096] Adding 2097148k swap on /swapfile. Priority:-2 extents:6 across:2260988k SSFS
[ 3.414154] systemd-journald[363]: Received request to flush runtime journal from PID 1
[ 3.552279] ACPI Warning: SystemIO range 0x0000000000000428-0x000000000000042F conflicts with OpRegion 0x0000000000000400-0x000000000000047F (\PMIO) (20181213/utaddress-213)
[ 3.552286] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[ 3.552289] ACPI Warning: SystemIO range 0x0000000000000540-0x000000000000054F conflicts with OpRegion 0x0000000000000500-0x0000000000000563 (\GPIO) (20181213/utaddress-213)
[ 3.552293] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[ 3.552294] ACPI Warning: SystemIO range 0x0000000000000530-0x000000000000053F conflicts with OpRegion 0x0000000000000500-0x0000000000000563 (\GPIO) (20181213/utaddress-213)
[ 3.552298] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[ 3.552299] ACPI Warning: SystemIO range 0x0000000000000500-0x000000000000052F conflicts with OpRegion 0x0000000000000500-0x0000000000000563 (\GPIO) (20181213/utaddress-213)
[ 3.552303] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[ 3.552303] lpc_ich: Resource conflict(s) found affecting gpio_ich
[ 3.562515] input: Ideapad extra buttons as /devices/pci0000:00/0000:00:1f.0/PNP0C09:00/VPC2004:00/input/input19
[ 3.621927] cfg80211: Loading compiled-in X.509 certificates for regulatory database
[ 3.625052] RAPL PMU: API unit is 2^-32 Joules, 3 fixed counters, 163840 ms ovfl timer
[ 3.625054] RAPL PMU: hw unit of domain pp0-core 2^-16 Joules
[ 3.625055] RAPL PMU: hw unit of domain package 2^-16 Joules
[ 3.625055] RAPL PMU: hw unit of domain pp1-gpu 2^-16 Joules
[ 3.627290] cfg80211: Loaded X.509 cert 'sforshee: 00b28ddf47aef9cea7'
[ 3.647888] IPMI message handler: version 39.2
[ 3.648490] snd_hda_intel 0000:01:00.1: Disabling MSI
[ 3.648495] snd_hda_intel 0000:01:00.1: Handle vga_switcheroo audio client
[ 3.656017] cryptd: max_cpu_qlen set to 1000
[ 3.656044] Bluetooth: Core ver 2.22
[ 3.656062] NET: Registered protocol family 31
[ 3.656063] Bluetooth: HCI device and connection manager initialized
[ 3.656067] Bluetooth: HCI socket layer initialized
[ 3.656069] Bluetooth: L2CAP socket layer initialized
[ 3.656072] Bluetooth: SCO socket layer initialized
[ 3.657493] ipmi device interface
[ 3.678661] AVX version of gcm_enc/dec engaged.
[ 3.678662] AES CTR mode by8 optimization enabled
[ 3.680923] usbcore: registered new interface driver btusb
[ 3.692090] snd_hda_codec_realtek hdaudioC0D0: autoconfig for ALC269VC: line_outs=1 (0x1a/0x0/0x0/0x0/0x0) type:speaker
[ 3.692091] snd_hda_codec_realtek hdaudioC0D0: speaker_outs=0 (0x0/0x0/0x0/0x0/0x0)
[ 3.692092] snd_hda_codec_realtek hdaudioC0D0: hp_outs=1 (0x15/0x0/0x0/0x0/0x0)
[ 3.692093] snd_hda_codec_realtek hdaudioC0D0: mono: mono_out=0x0
[ 3.692094] snd_hda_codec_realtek hdaudioC0D0: dig-out=0x1e/0x0
[ 3.692095] snd_hda_codec_realtek hdaudioC0D0: inputs:
[ 3.692096] snd_hda_codec_realtek hdaudioC0D0: Mic=0x18
[ 3.692097] snd_hda_codec_realtek hdaudioC0D0: Internal Mic=0x12
[ 3.693519] ath: phy0: Set BT/WLAN RX diversity capability
[ 3.699707] input: HDA Intel PCH Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input20
[ 3.699762] input: HDA Intel PCH Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card0/input21
[ 3.701047] ath: phy0: ASPM enabled: 0x42
[ 3.701049] ath: EEPROM regdomain: 0x65
[ 3.701050] ath: EEPROM indicates we should expect a direct regpair map
[ 3.701051] ath: Country alpha2 being used: 00
[ 3.701052] ath: Regpair used: 0x65
[ 3.714595] media: Linux media interface: v0.10
[ 3.718082] ieee80211 phy0: Selected rate control algorithm 'minstrel_ht'
[ 3.718329] ieee80211 phy0: Atheros AR9485 Rev:1 mem=0xffffb01e03400000, irq=17
[ 3.736093] videodev: Linux video capture interface: v2.00
[ 3.745969] usbcore: registered new interface driver ath3k
[ 3.787308] uvcvideo: Found UVC 1.00 device Lenovo EasyCamera (04f2:b331)
[ 3.816654] uvcvideo 4-1:1.0: Entity type for entity Extension 4 was not initialized!
[ 3.816656] uvcvideo 4-1:1.0: Entity type for entity Processing 2 was not initialized!
[ 3.816657] uvcvideo 4-1:1.0: Entity type for entity Camera 1 was not initialized!
[ 3.816706] input: Lenovo EasyCamera: Lenovo EasyC as /devices/pci0000:00/0000:00:14.0/usb4/4-1/4-1:1.0/input/input22
[ 3.816759] usbcore: registered new interface driver uvcvideo
[ 3.816760] USB Video Class driver (1.1.1)
[ 3.822136] usb 1-1.3: USB disconnect, device number 3
[ 3.878197] PKCS#7 signature not signed with a trusted key
[ 3.878212] nvidia: loading out-of-tree module taints kernel.
[ 3.878218] nvidia: module license 'NVIDIA' taints kernel.
[ 3.878220] Disabling lock debugging due to kernel taint
[ 3.882190] nvidia: module verification failed: signature and/or required key missing - tainting kernel
[ 3.889068] nvidia-nvlink: Nvlink Core is being initialized, major device number 237
[ 3.889427] nvidia 0000:01:00.0: vgaarb: changed VGA decodes: olddecodes=io+mem,decodes=none:owns=io+mem
[ 3.889525] NVRM: loading NVIDIA UNIX x86_64 Kernel Module 390.116 Sun Jan 27 07:21:36 PST 2019 (using threaded interrupts)
[ 3.904732] PKCS#7 signature not signed with a trusted key
[ 3.905638] nvidia-modeset: Loading NVIDIA Kernel Mode Setting Driver for UNIX platforms 390.116 Sun Jan 27 06:30:32 PST 2019
[ 3.912482] PKCS#7 signature not signed with a trusted key
[ 3.913177] [drm] [nvidia-drm] [GPU ID 0x00000100] Loading driver
[ 3.913178] [drm] Initialized nvidia-drm 0.0.0 20160202 for 0000:01:00.0 on minor 0
[ 3.926556] intel_rapl: Found RAPL domain package
[ 3.926558] intel_rapl: Found RAPL domain core
[ 3.926562] intel_rapl: RAPL package 0 domain package locked by BIOS
[ 3.932551] ath9k 0000:03:00.0 wlp3s0: renamed from wlan0
[ 3.972584] PKCS#7 signature not signed with a trusted key
[ 3.974582] nvidia-uvm: Loaded the UVM driver in 8 mode, major device number 236
[ 4.034382] ACPI Warning: \_SB.PCI0.PEG0.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20181213/nsarguments-66)
[ 4.049758] usb 1-1.3: new full-speed USB device number 4 using ehci-pci
[ 4.262172] input: HDA NVidia HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card1/input23
[ 4.869646] audit: type=1400 audit(1565702963.522:2): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/bin/man" pid=818 comm="apparmor_parser"
[ 4.869651] audit: type=1400 audit(1565702963.522:3): apparmor="STATUS" operation="profile_load" profile="unconfined" name="man_filter" pid=818 comm="apparmor_parser"
[ 4.869653] audit: type=1400 audit(1565702963.522:4): apparmor="STATUS" operation="profile_load" profile="unconfined" name="man_groff" pid=818 comm="apparmor_parser"
[ 4.870546] audit: type=1400 audit(1565702963.526:5): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/sbin/dhclient" pid=815 comm="apparmor_parser"
[ 4.870550] audit: type=1400 audit(1565702963.526:6): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=815 comm="apparmor_parser"
[ 4.870552] audit: type=1400 audit(1565702963.526:7): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-helper" pid=815 comm="apparmor_parser"
[ 4.870554] audit: type=1400 audit(1565702963.526:8): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=815 comm="apparmor_parser"
[ 4.870714] audit: type=1400 audit(1565702963.526:9): apparmor="STATUS" operation="profile_load" profile="unconfined" name="libreoffice-senddoc" pid=820 comm="apparmor_parser"
[ 4.871259] audit: type=1400 audit(1565702963.526:10): apparmor="STATUS" operation="profile_load" profile="unconfined" name="libreoffice-oopslash" pid=819 comm="apparmor_parser"
[ 6.004198] nvidia-modeset: WARNING: GPU:0: Correcting number of heads for current head configuration (0x03)
[ 6.255876] wlp3s0: authenticate with 10:93:97:9d:27:c2
[ 6.270231] wlp3s0: send auth to 10:93:97:9d:27:c2 (try 1/3)
[ 6.271680] wlp3s0: authenticated
[ 6.273794] wlp3s0: associate with 10:93:97:9d:27:c2 (try 1/3)
[ 6.279458] wlp3s0: RX AssocResp from 10:93:97:9d:27:c2 (capab=0xc31 status=0 aid=2)
[ 6.279581] wlp3s0: associated
[ 6.279644] ath: EEPROM regdomain sanitized
[ 6.279645] ath: EEPROM regdomain: 0x64
[ 6.279645] ath: EEPROM indicates we should expect a direct regpair map
[ 6.279646] ath: Country alpha2 being used: 00
[ 6.279647] ath: Regpair used: 0x64
[ 6.279647] ath: regdomain 0x64 dynamically updated by country element
[ 6.388910] IPv6: ADDRCONF(NETDEV_CHANGE): wlp3s0: link becomes ready
[ 9.420394] usb 1-1.3: New USB device found, idVendor=0cf3, idProduct=3004, bcdDevice= 0.02
[ 9.420399] usb 1-1.3: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[ 9.420401] usb 1-1.3: Product: Bluetooth USB Host Controller
[ 9.420403] usb 1-1.3: Manufacturer: Atheros Communications
[ 9.420405] usb 1-1.3: SerialNumber: Alaska Day 2006
[ 9.442137] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[ 9.442138] Bluetooth: BNEP filters: protocol multicast
[ 9.442141] Bluetooth: BNEP socket layer initialized
[ 9.889561] Bluetooth: RFCOMM TTY layer initialized
[ 9.889566] Bluetooth: RFCOMM socket layer initialized
[ 9.889569] Bluetooth: RFCOMM ver 1.11
[ 10.949126] rfkill: input handler disabled
[ 26.616854] logitech-hidpp-device 0003:046D:4060.0004: HID++ 4.5 device connected.
[ 26.832996] logitech-hidpp-device 0003:046D:4060.0004: multiplier = 8
[ 27.279200] input: 00:16:94:25:A7:D1 as /devices/virtual/input/input24
[ 42.150119] kauditd_printk_skb: 42 callbacks suppressed
[ 42.150121] audit: type=1400 audit(1565703000.586:53): apparmor="DENIED" operation="file_lock" profile="snap.opera.opera" name="/snap/opera/45/usr/lib/x86_64-linux-gnu/opera/opera_autoupdate" pid=1956 comm="opera" requested_mask="w" denied_mask="w" fsuid=1000 ouid=0
[ 42.368772] audit: type=1400 audit(1565703000.798:54): apparmor="DENIED" operation="file_lock" profile="snap.opera.opera" name="/snap/opera/45/usr/lib/x86_64-linux-gnu/opera/opera_autoupdate" pid=2725 comm="opera_autoupdat" requested_mask="w" denied_mask="w" fsuid=1000 ouid=0
[ 48.596922] audit: type=1400 audit(1565703006.940:55): apparmor="DENIED" operation="open" profile="snap.opera.opera" name="/run/udev/data/c238:0" pid=1956 comm="ThreadPoolForeg" requested_mask="r" denied_mask="r" fsuid=1000 ouid=0
[ 1185.757328] usb 1-1.3: USB disconnect, device number 4
[ 1186.042910] usb 1-1.3: new full-speed USB device number 5 using ehci-pci
[ 1186.156810] usb 1-1.3: New USB device found, idVendor=0cf3, idProduct=3004, bcdDevice= 0.01
[ 1186.156811] usb 1-1.3: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[ 1186.156813] usb 1-1.3: Product: Bluetooth USB Host Controller
[ 1186.156813] usb 1-1.3: Manufacturer: Atheros Communications
[ 1186.156814] usb 1-1.3: SerialNumber: Alaska Day 2006
[ 1186.206400] audit: type=1400 audit(1565704144.513:56): apparmor="DENIED" operation="open" profile="snap.opera.opera" name="/sys/devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.3/busnum" pid=1956 comm="ThreadPoolForeg" requested_mask="r" denied_mask="r" fsuid=1000 ouid=0
[ 1186.206479] audit: type=1400 audit(1565704144.513:57): apparmor="DENIED" operation="open" profile="snap.opera.opera" name="/sys/devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.3/devnum" pid=1956 comm="ThreadPoolForeg" requested_mask="r" denied_mask="r" fsuid=1000 ouid=0
[ 1186.269421] usb 1-1.3: USB disconnect, device number 5
[ 1186.502902] usb 1-1.3: new full-speed USB device number 6 using ehci-pci
[ 1191.716748] usb 1-1.3: New USB device found, idVendor=0cf3, idProduct=3004, bcdDevice= 0.02
[ 1191.716750] usb 1-1.3: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[ 1191.716751] usb 1-1.3: Product: Bluetooth USB Host Controller
[ 1191.716752] usb 1-1.3: Manufacturer: Atheros Communications
[ 1191.716752] usb 1-1.3: SerialNumber: Alaska Day 2006
[ 1191.723847] audit: type=1400 audit(1565704150.033:58): apparmor="DENIED" operation="open" profile="snap.opera.opera" name="/sys/devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.3/busnum" pid=1956 comm="ThreadPoolForeg" requested_mask="r" denied_mask="r" fsuid=1000 ouid=0
[ 1191.723851] audit: type=1400 audit(1565704150.033:59): apparmor="DENIED" operation="open" profile="snap.opera.opera" name="/sys/devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.3/devnum" pid=1956 comm="ThreadPoolForeg" requested_mask="r" denied_mask="r" fsuid=1000 ouid=0
[ 1210.133886] input: 00:16:94:25:A7:D1 as /devices/virtual/input/input25
[ 1274.491130] logitech-hidpp-device 0003:046D:4060.0004: multiplier = 8
[ 2598.368311] logitech-hidpp-device 0003:046D:4060.0004: multiplier = 8
[ 2995.977322] logitech-hidpp-device 0003:046D:4060.0004: multiplier = 8
[ 3267.950262] audit: type=1107 audit(1565706226.288:60): pid=921 uid=103 auid=4294967295 ses=4294967295 msg='apparmor="DENIED" operation="dbus_method_call" bus="system" path="/org/freedesktop/UPower" interface="org.freedesktop.DBus.Properties" member="Get" mask="send" name="org.freedesktop.UPower" pid=7974 label="snap.spotify.spotify" peer_pid=1476 peer_label="unconfined"
exe="/usr/bin/dbus-daemon" sauid=103 hostname=? addr=? terminal=?'
[ 3267.950394] audit: type=1107 audit(1565706226.288:61): pid=921 uid=103 auid=4294967295 ses=4294967295 msg='apparmor="DENIED" operation="dbus_method_call" bus="system" path="/org/freedesktop/UPower" interface="org.freedesktop.UPower" member="GetDisplayDevice" mask="send" name="org.freedesktop.UPower" pid=7974 label="snap.spotify.spotify" peer_pid=1476 peer_label="unconfined"
exe="/usr/bin/dbus-daemon" sauid=103 hostname=? addr=? terminal=?'
[ 3267.950511] audit: type=1107 audit(1565706226.288:62): pid=921 uid=103 auid=4294967295 ses=4294967295 msg='apparmor="DENIED" operation="dbus_method_call" bus="system" path="/org/freedesktop/UPower" interface="org.freedesktop.UPower" member="EnumerateDevices" mask="send" name="org.freedesktop.UPower" pid=7974 label="snap.spotify.spotify" peer_pid=1476 peer_label="unconfined"
exe="/usr/bin/dbus-daemon" sauid=103 hostname=? addr=? terminal=?'
[ 3740.539853] logitech-hidpp-device 0003:046D:4060.0004: multiplier = 8
[ 4893.371324] logitech-hidpp-device 0003:046D:4060.0004: multiplier = 8
[ 5829.595192] perf: interrupt took too long (2503 > 2500), lowering kernel.perf_event_max_sample_rate to 79750
[ 7888.169680] perf: interrupt took too long (3170 > 3128), lowering kernel.perf_event_max_sample_rate to 63000
[ 8873.434965] usb 1-1.3: USB disconnect, device number 6
[ 8873.703980] usb 1-1.3: new full-speed USB device number 7 using ehci-pci
[ 8873.814106] usb 1-1.3: New USB device found, idVendor=0cf3, idProduct=3004, bcdDevice= 0.01
[ 8873.814111] usb 1-1.3: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[ 8873.814114] usb 1-1.3: Product: Bluetooth USB Host Controller
[ 8873.814116] usb 1-1.3: Manufacturer: Atheros Communications
[ 8873.814118] usb 1-1.3: SerialNumber: Alaska Day 2006
[ 8873.868856] audit: type=1400 audit(1565711832.280:63): apparmor="DENIED" operation="open" profile="snap.opera.opera" name="/sys/devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.3/busnum" pid=1956 comm="ThreadPoolForeg" requested_mask="r" denied_mask="r" fsuid=1000 ouid=0
[ 8873.869018] audit: type=1400 audit(1565711832.280:64): apparmor="DENIED" operation="open" profile="snap.opera.opera" name="/sys/devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.3/devnum" pid=1956 comm="ThreadPoolForeg" requested_mask="r" denied_mask="r" fsuid=1000 ouid=0
[ 8873.947111] usb 1-1.3: USB disconnect, device number 7
[ 8874.167974] usb 1-1.3: new full-speed USB device number 8 using ehci-pci
[ 8879.298070] usb 1-1.3: New USB device found, idVendor=0cf3, idProduct=3004, bcdDevice= 0.02
[ 8879.298073] usb 1-1.3: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[ 8879.298074] usb 1-1.3: Product: Bluetooth USB Host Controller
[ 8879.298076] usb 1-1.3: Manufacturer: Atheros Communications
[ 8879.298077] usb 1-1.3: SerialNumber: Alaska Day 2006
[ 8879.307128] audit: type=1400 audit(1565711837.716:65): apparmor="DENIED" operation="open" profile="snap.opera.opera" name="/sys/devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.3/busnum" pid=1956 comm="ThreadPoolForeg" requested_mask="r" denied_mask="r" fsuid=1000 ouid=0
[ 8879.307351] audit: type=1400 audit(1565711837.716:66): apparmor="DENIED" operation="open" profile="snap.opera.opera" name="/sys/devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.3/devnum" pid=1956 comm="ThreadPoolForeg" requested_mask="r" denied_mask="r" fsuid=1000 ouid=0
[ 8898.963498] input: 00:16:94:25:A7:D1 as /devices/virtual/input/input26

```

---

