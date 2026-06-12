---
title: "TV Card Drivers for HP Laptop Philips Semiconductors SAA7160"
date: 2013-03-08
forum: Hardware
---

### Post by m_dk29 on 2013-03-08
I am unable to make my tv tuner card work with Ubuntu 12.10. Below are the driver details.


```
04:00.0 Multimedia controller [0480]: Philips Semiconductors SAA7160 [1131:7160] (rev 03)
    Subsystem: Avermedia Technologies Inc Device [1461:1055]
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0, Cache Line Size: 64 bytes
    Interrupt: pin A routed to IRQ 11
    Region 0: Memory at da100000 (64-bit, non-prefetchable) [size=1M]
    Capabilities: <access denied>
```


I tired to lookup on the internet but no help was found. Seems like the developemt project that was started earlier was frozen. 

Any pointers or help to get my TV working is greately appreciated.

Thanks

---

### Post by gordintoronto on 2013-03-08
[http://linuxtv.org/wiki/index.php/TBS6284](http://linuxtv.org/wiki/index.php/TBS6284)

---

### Post by m_dk29 on 2013-03-09
> **gordintoronto said:**
> [http://linuxtv.org/wiki/index.php/TBS6284](http://linuxtv.org/wiki/index.php/TBS6284)


I have follwed all the instructions mentioned till end but no luck.

```
$ sudo modprobe -v tbs62x0fe
$ insmod /lib/modules/3.7.0-7-generic/kernel/drivers/media/dvb/frontends/tbs62x0fe.ko
```

but when issued 

dmesg /var/log/syslogit does't display driver as mentioned in wiki.

output of dmesg.

```
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 3.7.0-7-generic (buildd@meitnerium) (gcc version 4.7.2 (Ubuntu/Linaro 4.7.2-2ubuntu1) ) #15-Ubuntu SMP Sat Dec 15 16:34:25 UTC 2012 (Ubuntu 3.7.0-7.15-generic 3.7.0)
[    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-3.7.0-7-generic root=UUID=e5d2d4ce-b4d9-4646-a918-b2bfeb72f8be ro quiet splash thermal.off=1 acpi_osi=
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   Centaur CentaurHauls
[    0.000000] e820: BIOS-provided physical RAM map:
[    0.000000] BIOS-e820: [mem 0x0000000000000000-0x000000000009cfff] usable
[    0.000000] BIOS-e820: [mem 0x000000000009d000-0x000000000009ffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000000e0000-0x00000000000fffff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000000100000-0x00000000bf680fff] usable
[    0.000000] BIOS-e820: [mem 0x00000000bf681000-0x00000000bf6befff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000bf6bf000-0x00000000bf75bfff] usable
[    0.000000] BIOS-e820: [mem 0x00000000bf75c000-0x00000000bf7befff] ACPI NVS
[    0.000000] BIOS-e820: [mem 0x00000000bf7bf000-0x00000000bf7e0fff] usable
[    0.000000] BIOS-e820: [mem 0x00000000bf7e1000-0x00000000bf7fefff] ACPI data
[    0.000000] BIOS-e820: [mem 0x00000000bf7ff000-0x00000000bf7fffff] usable
[    0.000000] BIOS-e820: [mem 0x00000000bf800000-0x00000000bfffffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000e0000000-0x00000000efffffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000feb00000-0x00000000feb03fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fec00000-0x00000000fec00fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fed10000-0x00000000fed13fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fed18000-0x00000000fed19fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fed1b000-0x00000000fed1ffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fee00000-0x00000000fee00fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000ffe80000-0x00000000ffffffff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000100000000-0x00000001bfffffff] usable
[    0.000000] NX (Execute Disable) protection: active
[    0.000000] DMI 2.6 present.
[    0.000000] DMI: Hewlett-Packard HP Pavilion dv6 Notebook PC/363E, BIOS F.1C 05/17/2010
[    0.000000] e820: update [mem 0x00000000-0x0000ffff] usable ==> reserved
[    0.000000] e820: remove [mem 0x000a0000-0x000fffff] usable
[    0.000000] No AGP bridge found
[    0.000000] e820: last_pfn = 0x1c0000 max_arch_pfn = 0x400000000
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
[    0.000000]   3 base 0BF800000 mask FFF800000 uncachable
[    0.000000]   4 base 100000000 mask F80000000 write-back
[    0.000000]   5 base 180000000 mask FC0000000 write-back
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] e820: last_pfn = 0xbf800 max_arch_pfn = 0x400000000
[    0.000000] initial memory mapped: [mem 0x00000000-0x1fffffff]
[    0.000000] Base memory trampoline at [ffff880000097000] 97000 size 24576
[    0.000000] init_memory_mapping: [mem 0x00000000-0xbf7fffff]
[    0.000000]  [mem 0x00000000-0xbf7fffff] page 2M
[    0.000000] kernel direct mapping tables up to 0xbf7fffff @ [mem 0x1fffc000-0x1fffffff]
[    0.000000] init_memory_mapping: [mem 0x100000000-0x1bfffffff]
[    0.000000]  [mem 0x100000000-0x1bfffffff] page 2M
[    0.000000] kernel direct mapping tables up to 0x1bfffffff @ [mem 0xbf7dd000-0xbf7e0fff]
[    0.000000] RAMDISK: [mem 0x35272000-0x36930fff]
[    0.000000] ACPI: RSDP 00000000000fe020 00024 (v02 HPQOEM)
[    0.000000] ACPI: XSDT 00000000bf7fe120 00074 (v01 HPQOEM SLIC-MPC 00000001      01000013)
[    0.000000] ACPI: FACP 00000000bf7fc000 000F4 (v04 HPQOEM SLIC-MPC 00000001 MSFT 01000013)
[    0.000000] ACPI: DSDT 00000000bf7eb000 0DC7D (v02 HPQOEM SLIC-MPC 00000001 MSFT 01000013)
[    0.000000] ACPI: FACS 00000000bf76f000 00040
[    0.000000] ACPI: ASF! 00000000bf7fd000 000A5 (v32 HPQOEM SLIC-MPC 00000001 MSFT 01000013)
[    0.000000] ACPI: HPET 00000000bf7fb000 00038 (v01 HPQOEM SLIC-MPC 00000001 MSFT 01000013)
[    0.000000] ACPI: APIC 00000000bf7fa000 0008C (v02 HPQOEM SLIC-MPC 00000001 MSFT 01000013)
[    0.000000] ACPI: MCFG 00000000bf7f9000 0003C (v01 HPQOEM SLIC-MPC 00000001 MSFT 01000013)
[    0.000000] ACPI: SLIC 00000000bf7ea000 00176 (v01 HPQOEM SLIC-MPC 00000001 SLIC 000F4240)
[    0.000000] ACPI: BOOT 00000000bf7e7000 00028 (v01 HPQOEM SLIC-MPC 00000001 MSFT 01000013)
[    0.000000] ACPI: ASPT 00000000bf7e3000 00034 (v04 HPQOEM SLIC-MPC 00000001 MSFT 01000013)
[    0.000000] ACPI: WDRT 00000000bf7e2000 00047 (v01 HPQOEM SLIC-MPC 00000000 MSFT 01000013)
[    0.000000] ACPI: SSDT 00000000bf7e1000 009F1 (v01  PmRef    CpuPm 00003000 INTL 20051117)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at [mem 0x0000000000000000-0x00000001bfffffff]
[    0.000000] Initmem setup node 0 [mem 0x00000000-0x1bfffffff]
[    0.000000]   NODE_DATA [mem 0x1bfffc000-0x1bfffffff]
[    0.000000]  [ffffea0000000000-ffffea0006ffffff] PMD -> [ffff8801b9600000-ffff8801bf5fffff] on node 0
[    0.000000] Zone ranges:
[    0.000000]   DMA      [mem 0x00010000-0x00ffffff]
[    0.000000]   DMA32    [mem 0x01000000-0xffffffff]
[    0.000000]   Normal   [mem 0x100000000-0x1bfffffff]
[    0.000000] Movable zone start for each node
[    0.000000] Early memory node ranges
[    0.000000]   node   0: [mem 0x00010000-0x0009cfff]
[    0.000000]   node   0: [mem 0x00100000-0xbf680fff]
[    0.000000]   node   0: [mem 0xbf6bf000-0xbf75bfff]
[    0.000000]   node   0: [mem 0xbf7bf000-0xbf7e0fff]
[    0.000000]   node   0: [mem 0xbf7ff000-0xbf7fffff]
[    0.000000]   node   0: [mem 0x100000000-0x1bfffffff]
[    0.000000] On node 0 totalpages: 1570510
[    0.000000]   DMA zone: 64 pages used for memmap
[    0.000000]   DMA zone: 6 pages reserved
[    0.000000]   DMA zone: 3911 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 16320 pages used for memmap
[    0.000000]   DMA32 zone: 763777 pages, LIFO batch:31
[    0.000000]   Normal zone: 12288 pages used for memmap
[    0.000000]   Normal zone: 774144 pages, LIFO batch:31
[    0.000000] ACPI: PM-Timer IO Port: 0x408
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x02] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x04] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x06] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x05] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x06] lapic_id[0x03] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x07] lapic_id[0x05] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x08] lapic_id[0x07] enabled)
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
[    0.000000] smpboot: Allowing 8 CPUs, 0 hotplug CPUs
[    0.000000] nr_irqs_gsi: 40
[    0.000000] PM: Registered nosave memory: 000000000009d000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
[    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
[    0.000000] PM: Registered nosave memory: 00000000bf681000 - 00000000bf6bf000
[    0.000000] PM: Registered nosave memory: 00000000bf75c000 - 00000000bf7bf000
[    0.000000] PM: Registered nosave memory: 00000000bf7e1000 - 00000000bf7ff000
[    0.000000] PM: Registered nosave memory: 00000000bf800000 - 00000000c0000000
[    0.000000] PM: Registered nosave memory: 00000000c0000000 - 00000000e0000000
[    0.000000] PM: Registered nosave memory: 00000000e0000000 - 00000000f0000000
[    0.000000] PM: Registered nosave memory: 00000000f0000000 - 00000000feb00000
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
[    0.000000] PM: Registered nosave memory: 00000000fee01000 - 00000000ffe80000
[    0.000000] PM: Registered nosave memory: 00000000ffe80000 - 0000000100000000
[    0.000000] e820: [mem 0xc0000000-0xdfffffff] available for PCI devices
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] setup_percpu: NR_CPUS:256 nr_cpumask_bits:256 nr_cpu_ids:8 nr_node_ids:1
[    0.000000] PERCPU: Embedded 28 pages/cpu @ffff8801bfc00000 s84736 r8192 d21760 u262144
[    0.000000] pcpu-alloc: s84736 r8192 d21760 u262144 alloc=1*2097152
[    0.000000] pcpu-alloc: [0] 0 1 2 3 4 5 6 7 
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 1541832
[    0.000000] Policy zone: Normal
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.7.0-7-generic root=UUID=e5d2d4ce-b4d9-4646-a918-b2bfeb72f8be ro quiet splash thermal.off=1 acpi_osi=
[    0.000000] ACPI: _OSI method disabled
[    0.000000] PID hash table entries: 4096 (order: 3, 32768 bytes)
[    0.000000] __ex_table already sorted, skipping sort
[    0.000000] Checking aperture...
[    0.000000] No AGP bridge found
[    0.000000] Calgary: detecting Calgary via BIOS EBDA area
[    0.000000] Calgary: Unable to locate Rio Grande table in EBDA - bailing!
[    0.000000] Memory: 6077540k/7340032k available (6900k kernel code, 1057992k absent, 204500k reserved, 6312k data, 984k init)
[    0.000000] SLUB: Genslabs=15, HWalign=64, Order=0-3, MinObjects=0, CPUs=8, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000]     RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000]     RCU restricting CPUs from NR_CPUS=256 to nr_cpu_ids=8.
[    0.000000] NR_IRQS:16640 nr_irqs:744 16
[    0.000000] Extended CMOS year: 2000
[    0.000000] Console: colour VGA+ 80x25
[    0.000000] console [tty0] enabled
[    0.000000] allocated 25165824 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] hpet clockevent registered
[    0.000000] tsc: Fast TSC calibration using PIT
[    0.004000] tsc: Detected 1729.009 MHz processor
[    0.000003] Calibrating delay loop (skipped), value calculated using timer frequency.. 3458.01 BogoMIPS (lpj=6916036)
[    0.000006] pid_max: default: 32768 minimum: 301
[    0.000035] Security Framework initialized
[    0.000049] AppArmor: AppArmor initialized
[    0.000050] Yama: becoming mindful.
[    0.000744] Dentry cache hash table entries: 1048576 (order: 11, 8388608 bytes)
[    0.003369] Inode-cache hash table entries: 524288 (order: 10, 4194304 bytes)
[    0.004498] Mount-cache hash table entries: 256
[    0.004718] Initializing cgroup subsys cpuacct
[    0.004720] Initializing cgroup subsys memory
[    0.004727] Initializing cgroup subsys devices
[    0.004729] Initializing cgroup subsys freezer
[    0.004730] Initializing cgroup subsys blkio
[    0.004732] Initializing cgroup subsys perf_event
[    0.004734] Initializing cgroup subsys hugetlb
[    0.004758] CPU: Physical Processor ID: 0
[    0.004759] CPU: Processor Core ID: 0
[    0.004764] mce: CPU supports 9 MCE banks
[    0.004775] CPU0: Thermal monitoring enabled (TM1)
[    0.004782] process: using mwait in idle threads
[    0.004786] Last level iTLB entries: 4KB 512, 2MB 7, 4MB 7
[    0.004786] Last level dTLB entries: 4KB 512, 2MB 32, 4MB 32
[    0.004786] tlb_flushall_shift: 6
[    0.004937] Freeing SMP alternatives: 24k freed
[    0.007367] ACPI: Core revision 20120913
[    0.034484] ftrace: allocating 25955 entries in 102 pages
[    0.050538] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.090206] smpboot: CPU0: Intel(R) Core(TM) i7 CPU       Q 820  @ 1.73GHz (fam: 06, model: 1e, stepping: 05)
[    0.196912] Performance Events: PEBS fmt1+, 16-deep LBR, Nehalem events, Intel PMU driver.
[    0.196918] perf_event_intel: CPU erratum AAJ80 worked around
[    0.196920] perf_event_intel: CPUID marked event: 'bus cycles' unavailable
[    0.196921] ... version:                3
[    0.196922] ... bit width:              48
[    0.196923] ... generic registers:      4
[    0.196925] ... value mask:             0000ffffffffffff
[    0.196926] ... max period:             000000007fffffff
[    0.196927] ... fixed-purpose events:   3
[    0.196928] ... event mask:             000000070000000f
[    1.251717] NMI watchdog: enabled on all CPUs, permanently consumes one hw-PMU counter.
[    0.198096] smpboot: Booting Node   0, Processors  #1 #2 #3 #4 #5 #6 #7 OK
[    1.331112] Brought up 8 CPUs
[    1.331117] smpboot: Total of 8 processors activated (27664.14 BogoMIPS)
[    1.338065] devtmpfs: initialized
[    1.339403] EVM: security.selinux
[    1.339404] EVM: security.SMACK64
[    1.339406] EVM: security.capability
[    1.339454] PM: Registering ACPI NVS region [mem 0xbf75c000-0xbf7befff] (405504 bytes)
[    1.340480] regulator-dummy: no parameters
[    1.340535] NET: Registered protocol family 16
[    1.340700] ACPI FADT declares the system doesn't support PCIe ASPM, so disable it
[    1.340702] ACPI: bus type pci registered
[    1.340787] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xe0000000-0xefffffff] (base 0xe0000000)
[    1.340790] PCI: MMCONFIG at [mem 0xe0000000-0xefffffff] reserved in E820
[    1.368121] PCI: Using configuration type 1 for base access
[    1.368383] mtrr: your CPUs had inconsistent variable MTRR settings
[    1.368385] mtrr: probably your BIOS does not setup all CPUs.
[    1.368385] mtrr: corrected configuration.
[    1.369219] bio: create slab <bio-0> at 0
[    1.369310] ACPI: Added _OSI(Module Device)
[    1.369312] ACPI: Added _OSI(Processor Device)
[    1.369314] ACPI: Added _OSI(3.0 _SCP Extensions)
[    1.369315] ACPI: Added _OSI(Processor Aggregator Device)
[    1.371502] ACPI: EC: Look up EC in DSDT
[    1.373676] ACPI: Executed 1 blocks of module-level executable AML code
[    1.377197] ACPI: SSDT 00000000bf691c18 00298 (v01  PmRef  Cpu0Ist 00003000 INTL 20051117)
[    1.377732] ACPI: Dynamic OEM Table Load:
[    1.377734] ACPI: SSDT           (null) 00298 (v01  PmRef  Cpu0Ist 00003000 INTL 20051117)
[    1.377920] ACPI: SSDT 00000000bf68f618 005CD (v01  PmRef  Cpu0Cst 00003001 INTL 20051117)
[    1.378436] ACPI: Dynamic OEM Table Load:
[    1.378439] ACPI: SSDT           (null) 005CD (v01  PmRef  Cpu0Cst 00003001 INTL 20051117)
[    1.403905] ACPI: SSDT 00000000bf690a98 00303 (v01  PmRef    ApIst 00003000 INTL 20051117)
[    1.404493] ACPI: Dynamic OEM Table Load:
[    1.404495] ACPI: SSDT           (null) 00303 (v01  PmRef    ApIst 00003000 INTL 20051117)
[    1.423739] ACPI: SSDT 00000000bf68ed98 00119 (v01  PmRef    ApCst 00003000 INTL 20051117)
[    1.424290] ACPI: Dynamic OEM Table Load:
[    1.424293] ACPI: SSDT           (null) 00119 (v01  PmRef    ApCst 00003000 INTL 20051117)
[    1.444845] ACPI: Interpreter enabled
[    1.444849] ACPI: (supports S0 S3 S4 S5)
[    1.444884] ACPI: Using IOAPIC for interrupt routing
[    1.450963] ACPI: EC: GPE = 0x16, I/O: command/status = 0x66, data = 0x62
[    1.451157] ACPI: No dock devices found.
[    1.451161] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[    1.451582] \_SB_.PCI0:_OSC invalid UUID
[    1.451584] _OSC request data:1 8 1f 
[    1.451589] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-fe])
[    1.452277] PCI host bridge to bus 0000:00
[    1.452280] pci_bus 0000:00: root bus resource [bus 00-fe]
[    1.452282] pci_bus 0000:00: root bus resource [io  0x0000-0x0cf7]
[    1.452284] pci_bus 0000:00: root bus resource [io  0x0d00-0xffff]
[    1.452287] pci_bus 0000:00: root bus resource [mem 0x000a0000-0x000bffff]
[    1.452289] pci_bus 0000:00: root bus resource [mem 0xc0000000-0xfeafffff]
[    1.452299] pci 0000:00:00.0: [8086:d132] type 00 class 0x060000
[    1.452359] pci 0000:00:03.0: [8086:d138] type 01 class 0x060400
[    1.452415] pci 0000:00:03.0: PME# supported from D0 D3hot D3cold
[    1.452443] pci 0000:00:08.0: [8086:d155] type 00 class 0x088000
[    1.452502] pci 0000:00:08.1: [8086:d156] type 00 class 0x088000
[    1.452562] pci 0000:00:08.2: [8086:d157] type 00 class 0x088000
[    1.452619] pci 0000:00:08.3: [8086:d158] type 00 class 0x088000
[    1.452681] pci 0000:00:10.0: [8086:d150] type 00 class 0x088000
[    1.452726] pci 0000:00:10.1: [8086:d151] type 00 class 0x088000
[    1.452810] pci 0000:00:1a.0: [8086:3b3c] type 00 class 0x0c0320
[    1.453135] pci 0000:00:1a.0: reg 10: [mem 0xdd105c00-0xdd105fff]
[    1.454972] pci 0000:00:1a.0: PME# supported from D0 D3hot D3cold
[    1.455016] pci 0000:00:1b.0: [8086:3b56] type 00 class 0x040300
[    1.455036] pci 0000:00:1b.0: reg 10: [mem 0xdd100000-0xdd103fff 64bit]
[    1.455113] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    1.455148] pci 0000:00:1c.0: [8086:3b42] type 01 class 0x060400
[    1.455226] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    1.455262] pci 0000:00:1c.1: [8086:3b44] type 01 class 0x060400
[    1.455340] pci 0000:00:1c.1: PME# supported from D0 D3hot D3cold
[    1.455377] pci 0000:00:1c.3: [8086:3b48] type 01 class 0x060400
[    1.455461] pci 0000:00:1c.3: PME# supported from D0 D3hot D3cold
[    1.455497] pci 0000:00:1c.4: [8086:3b4a] type 01 class 0x060400
[    1.455575] pci 0000:00:1c.4: PME# supported from D0 D3hot D3cold
[    1.455608] pci 0000:00:1c.7: [8086:3b50] type 01 class 0x060400
[    1.455687] pci 0000:00:1c.7: PME# supported from D0 D3hot D3cold
[    1.455723] pci 0000:00:1d.0: [8086:3b34] type 00 class 0x0c0320
[    1.456049] pci 0000:00:1d.0: reg 10: [mem 0xdd105800-0xdd105bff]
[    1.457934] pci 0000:00:1d.0: PME# supported from D0 D3hot D3cold
[    1.457975] pci 0000:00:1e.0: [8086:2448] type 01 class 0x060401
[    1.458056] pci 0000:00:1f.0: [8086:3b03] type 00 class 0x060100
[    1.458193] pci 0000:00:1f.2: [8086:3b2f] type 00 class 0x010601
[    1.458217] pci 0000:00:1f.2: reg 10: [io  0x8048-0x804f]
[    1.458230] pci 0000:00:1f.2: reg 14: [io  0x8054-0x8057]
[    1.458242] pci 0000:00:1f.2: reg 18: [io  0x8040-0x8047]
[    1.458255] pci 0000:00:1f.2: reg 1c: [io  0x8050-0x8053]
[    1.458267] pci 0000:00:1f.2: reg 20: [io  0x8020-0x803f]
[    1.458279] pci 0000:00:1f.2: reg 24: [mem 0xdd105000-0xdd1057ff]
[    1.458335] pci 0000:00:1f.2: PME# supported from D3hot
[    1.458367] pci 0000:00:1f.3: [8086:3b30] type 00 class 0x0c0500
[    1.458387] pci 0000:00:1f.3: reg 10: [mem 0xdd106000-0xdd1060ff 64bit]
[    1.458412] pci 0000:00:1f.3: reg 20: [io  0x8000-0x801f]
[    1.458490] pci 0000:01:00.0: [10de:0a28] type 00 class 0x030000
[    1.458499] pci 0000:01:00.0: reg 10: [mem 0xd2000000-0xd2ffffff]
[    1.458509] pci 0000:01:00.0: reg 14: [mem 0xc0000000-0xcfffffff 64bit pref]
[    1.458519] pci 0000:01:00.0: reg 1c: [mem 0xd0000000-0xd1ffffff 64bit pref]
[    1.458526] pci 0000:01:00.0: reg 24: [io  0x7000-0x707f]
[    1.458533] pci 0000:01:00.0: reg 30: [mem 0xfff80000-0xffffffff pref]
[    1.458584] pci 0000:01:00.1: [10de:0be2] type 00 class 0x040300
[    1.458594] pci 0000:01:00.1: reg 10: [mem 0xd3000000-0xd3003fff]
[    1.464390] pci 0000:00:03.0: PCI bridge to [bus 01]
[    1.464396] pci 0000:00:03.0:   bridge window [io  0x7000-0x7fff]
[    1.464401] pci 0000:00:03.0:   bridge window [mem 0xd2000000-0xd30fffff]
[    1.464408] pci 0000:00:03.0:   bridge window [mem 0xc0000000-0xd1ffffff 64bit pref]
[    1.464545] pci 0000:02:00.0: [8086:4237] type 00 class 0x028000
[    1.464632] pci 0000:02:00.0: reg 10: [mem 0xdc100000-0xdc101fff 64bit]
[    1.465059] pci 0000:02:00.0: PME# supported from D0 D3hot D3cold
[    1.472414] pci 0000:00:1c.0: PCI bridge to [bus 02]
[    1.472425] pci 0000:00:1c.0:   bridge window [io  0x6000-0x6fff]
[    1.472435] pci 0000:00:1c.0:   bridge window [mem 0xdc100000-0xdd0fffff]
[    1.472447] pci 0000:00:1c.0:   bridge window [mem 0xd3100000-0xd40fffff 64bit pref]
[    1.472542] pci 0000:03:00.0: [10ec:8168] type 00 class 0x020000
[    1.472641] pci 0000:03:00.0: reg 10: [io  0x5000-0x50ff]
[    1.472674] pci 0000:03:00.0: reg 18: [mem 0xd4104000-0xd4104fff 64bit pref]
[    1.472697] pci 0000:03:00.0: reg 20: [mem 0xd4100000-0xd4103fff 64bit pref]
[    1.472714] pci 0000:03:00.0: reg 30: [mem 0xffff0000-0xffffffff pref]
[    1.472824] pci 0000:03:00.0: supports D1 D2
[    1.472826] pci 0000:03:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    1.472943] pci 0000:00:1c.1: PCI bridge to [bus 03]
[    1.472952] pci 0000:00:1c.1:   bridge window [io  0x5000-0x5fff]
[    1.472960] pci 0000:00:1c.1:   bridge window [mem 0xdb100000-0xdc0fffff]
[    1.472970] pci 0000:00:1c.1:   bridge window [mem 0xd4100000-0xd50fffff 64bit pref]
[    1.473046] pci 0000:04:00.0: [1131:7160] type 00 class 0x048000
[    1.473076] pci 0000:04:00.0: reg 10: [mem 0xda100000-0xda1fffff 64bit]
[    1.473216] pci 0000:04:00.0: supports D1 D2
[    1.473218] pci 0000:04:00.0: PME# supported from D0 D1 D2
[    1.480398] pci 0000:00:1c.3: PCI bridge to [bus 04]
[    1.480408] pci 0000:00:1c.3:   bridge window [io  0x4000-0x4fff]
[    1.480419] pci 0000:00:1c.3:   bridge window [mem 0xda100000-0xdb0fffff]
[    1.480431] pci 0000:00:1c.3:   bridge window [mem 0xd5100000-0xd60fffff 64bit pref]
[    1.480550] pci 0000:05:00.0: [197b:2380] type 00 class 0x0c0010
[    1.480623] pci 0000:05:00.0: reg 10: [mem 0xd9100000-0xd91007ff]
[    1.480674] pci 0000:05:00.0: reg 14: [mem 0xd9100d00-0xd9100d7f]
[    1.480827] pci 0000:05:00.0: reg 20: [mem 0xd9100c80-0xd9100cff]
[    1.480878] pci 0000:05:00.0: reg 24: [mem 0xd9100c00-0xd9100c7f]
[    1.481301] pci 0000:05:00.1: [197b:2382] type 00 class 0x088000
[    1.481371] pci 0000:05:00.1: reg 10: [mem 0xd9100b00-0xd9100bff]
[    1.482004] pci 0000:05:00.2: [197b:2381] type 00 class 0x080501
[    1.482069] pci 0000:05:00.2: reg 10: [mem 0xd9100a00-0xd9100aff]
[    1.482666] pci 0000:05:00.3: [197b:2383] type 00 class 0x088000
[    1.482736] pci 0000:05:00.3: reg 10: [mem 0xd9100900-0xd91009ff]
[    1.483307] pci 0000:05:00.4: [197b:2384] type 00 class 0x088000
[    1.483377] pci 0000:05:00.4: reg 10: [mem 0xd9100800-0xd91008ff]
[    1.484161] pci 0000:00:1c.4: PCI bridge to [bus 05]
[    1.484169] pci 0000:00:1c.4:   bridge window [io  0x3000-0x3fff]
[    1.484178] pci 0000:00:1c.4:   bridge window [mem 0xd9100000-0xda0fffff]
[    1.484188] pci 0000:00:1c.4:   bridge window [mem 0xd6100000-0xd70fffff 64bit pref]
[    1.484241] pci 0000:00:1c.7: PCI bridge to [bus 06-09]
[    1.484249] pci 0000:00:1c.7:   bridge window [io  0x2000-0x2fff]
[    1.484258] pci 0000:00:1c.7:   bridge window [mem 0xd8100000-0xd90fffff]
[    1.484268] pci 0000:00:1c.7:   bridge window [mem 0xd7100000-0xd80fffff 64bit pref]
[    1.484332] pci 0000:00:1e.0: PCI bridge to [bus 0a] (subtractive decode)
[    1.484346] pci 0000:00:1e.0:   bridge window [io  0x0000-0x0cf7] (subtractive decode)
[    1.484349] pci 0000:00:1e.0:   bridge window [io  0x0d00-0xffff] (subtractive decode)
[    1.484351] pci 0000:00:1e.0:   bridge window [mem 0x000a0000-0x000bffff] (subtractive decode)
[    1.484353] pci 0000:00:1e.0:   bridge window [mem 0xc0000000-0xfeafffff] (subtractive decode)
[    1.484398] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    1.484511] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P2._PRT]
[    1.484552] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P1._PRT]
[    1.484570] ACPI Warning: For \_SB_.PCI0.P0P1._PRT: Return Package has no elements (empty) (20120913/nspredef-463)
[    1.484603] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP01._PRT]
[    1.484640] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP02._PRT]
[    1.484680] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP04._PRT]
[    1.484714] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP05._PRT]
[    1.484770] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP08._PRT]
[    1.484852] \_SB_.PCI0:_OSC invalid UUID
[    1.484854] _OSC request data:1 1f 1f 
[    1.484858]  pci0000:00: ACPI _OSC support notification failed, disabling PCIe ASPM
[    1.484860]  pci0000:00: Unable to request _OSC control (_OSC support mask: 0x08)
[    1.491924] ACPI: PCI Root Bridge [CPBG] (domain 0000 [bus ff])
[    1.491984] PCI host bridge to bus 0000:ff
[    1.491987] pci_bus 0000:ff: root bus resource [bus ff]
[    1.491993] pci 0000:ff:00.0: [8086:2c52] type 00 class 0x060000
[    1.492015] pci 0000:ff:00.1: [8086:2c81] type 00 class 0x060000
[    1.492041] pci 0000:ff:02.0: [8086:2c90] type 00 class 0x060000
[    1.492061] pci 0000:ff:02.1: [8086:2c91] type 00 class 0x060000
[    1.492083] pci 0000:ff:03.0: [8086:2c98] type 00 class 0x060000
[    1.492103] pci 0000:ff:03.1: [8086:2c99] type 00 class 0x060000
[    1.492124] pci 0000:ff:03.4: [8086:2c9c] type 00 class 0x060000
[    1.492145] pci 0000:ff:04.0: [8086:2ca0] type 00 class 0x060000
[    1.492165] pci 0000:ff:04.1: [8086:2ca1] type 00 class 0x060000
[    1.492185] pci 0000:ff:04.2: [8086:2ca2] type 00 class 0x060000
[    1.492207] pci 0000:ff:04.3: [8086:2ca3] type 00 class 0x060000
[    1.492229] pci 0000:ff:05.0: [8086:2ca8] type 00 class 0x060000
[    1.492249] pci 0000:ff:05.1: [8086:2ca9] type 00 class 0x060000
[    1.492269] pci 0000:ff:05.2: [8086:2caa] type 00 class 0x060000
[    1.492289] pci 0000:ff:05.3: [8086:2cab] type 00 class 0x060000
[    1.492327]  pci0000:ff: ACPI _OSC support notification failed, disabling PCIe ASPM
[    1.492329]  pci0000:ff: Unable to request _OSC control (_OSC support mask: 0x08)
[    1.492751] ACPI: PCI Interrupt Link [LNKA] (IRQs 1 3 4 *5 6 7 10 12 14 15)
[    1.492810] ACPI: PCI Interrupt Link [LNKB] (IRQs 1 3 4 *5 6 7 11 12 14 15)
[    1.492868] ACPI: PCI Interrupt Link [LNKC] (IRQs 1 3 4 5 6 7 10 12 14 15) *11
[    1.492927] ACPI: PCI Interrupt Link [LNKD] (IRQs 1 3 4 5 6 7 *11 12 14 15)
[    1.492985] ACPI: PCI Interrupt Link [LNKE] (IRQs 1 3 4 5 6 7 10 12 14 15) *0, disabled.
[    1.493043] ACPI: PCI Interrupt Link [LNKF] (IRQs 1 3 4 *5 6 7 11 12 14 15)
[    1.493101] ACPI: PCI Interrupt Link [LNKG] (IRQs 1 3 4 5 6 7 *10 12 14 15)
[    1.493158] ACPI: PCI Interrupt Link [LNKH] (IRQs 1 3 4 5 6 7 11 12 14 15) *0, disabled.
[    1.493262] vgaarb: device added: PCI:0000:01:00.0,decodes=io+mem,owns=io+mem,locks=none
[    1.493267] vgaarb: loaded
[    1.493269] vgaarb: bridge control possible 0000:01:00.0
[    1.493437] SCSI subsystem initialized
[    1.493439] ACPI: bus type scsi registered
[    1.493471] libata version 3.00 loaded.
[    1.493488] ACPI: bus type usb registered
[    1.493506] usbcore: registered new interface driver usbfs
[    1.493514] usbcore: registered new interface driver hub
[    1.493532] usbcore: registered new device driver usb
[    1.493605] PCI: Using ACPI for IRQ routing
[    1.499891] PCI: pci_cache_line_size set to 64 bytes
[    1.500063] e820: reserve RAM buffer [mem 0x0009d000-0x0009ffff]
[    1.500065] e820: reserve RAM buffer [mem 0xbf681000-0xbfffffff]
[    1.500066] e820: reserve RAM buffer [mem 0xbf75c000-0xbfffffff]
[    1.500068] e820: reserve RAM buffer [mem 0xbf7e1000-0xbfffffff]
[    1.500070] e820: reserve RAM buffer [mem 0xbf800000-0xbfffffff]
[    1.500152] NetLabel: Initializing
[    1.500154] NetLabel:  domain hash size = 128
[    1.500154] NetLabel:  protocols = UNLABELED CIPSOv4
[    1.500165] NetLabel:  unlabeled traffic allowed by default
[    1.500261] HPET: 8 timers in total, 5 timers will be used for per-cpu timer
[    1.500270] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 40, 41, 42, 43, 44, 0
[    1.500276] hpet0: 8 comparators, 64-bit 14.318180 MHz counter
[    1.502329] hpet: hpet2 irq 40 for MSI
[    1.502398] hpet: hpet3 irq 41 for MSI
[    1.502462] hpet: hpet4 irq 42 for MSI
[    1.502522] hpet: hpet5 irq 43 for MSI
[    1.502576] hpet: hpet6 irq 44 for MSI
[    1.502656] Switching to clocksource hpet
[    1.507943] AppArmor: AppArmor Filesystem Enabled
[    1.507963] pnp: PnP ACPI init
[    1.507973] ACPI: bus type pnp registered
[    1.508671] pnp 00:00: [bus 00-fe]
[    1.508675] pnp 00:00: [io  0x0000-0x0cf7 window]
[    1.508677] pnp 00:00: [io  0x0cf8-0x0cff]
[    1.508679] pnp 00:00: [io  0x0d00-0xffff window]
[    1.508681] pnp 00:00: [mem 0x000a0000-0x000bffff window]
[    1.508683] pnp 00:00: [mem 0x000c0000-0x000c3fff window]
[    1.508685] pnp 00:00: [mem 0x000c4000-0x000c7fff window]
[    1.508687] pnp 00:00: [mem 0x000c8000-0x000cbfff window]
[    1.508689] pnp 00:00: [mem 0x000cc000-0x000cffff window]
[    1.508691] pnp 00:00: [mem 0x000d0000-0x000d3fff window]
[    1.508693] pnp 00:00: [mem 0x000d4000-0x000d7fff window]
[    1.508695] pnp 00:00: [mem 0x000d8000-0x000dbfff window]
[    1.508697] pnp 00:00: [mem 0x000dc000-0x000dffff window]
[    1.508699] pnp 00:00: [mem 0x000e0000-0x000e3fff window]
[    1.508700] pnp 00:00: [mem 0x000e4000-0x000e7fff window]
[    1.508702] pnp 00:00: [mem 0x000e8000-0x000ebfff window]
[    1.508704] pnp 00:00: [mem 0x000ec000-0x000effff window]
[    1.508706] pnp 00:00: [mem 0x000f0000-0x000fffff window]
[    1.508708] pnp 00:00: [mem 0xc0000000-0xfeafffff window]
[    1.508710] pnp 00:00: [mem 0xfed40000-0xfed44fff window]
[    1.508741] pnp 00:00: Plug and Play ACPI device, IDs PNP0a08 PNP0a03 (active)
[    1.508812] pnp 00:01: [io  0x0380-0x038e]
[    1.508825] pnp 00:01: [irq 4]
[    1.508847] pnp 00:01: Plug and Play ACPI device, IDs ENE0100 (active)
[    1.508856] pnp 00:02: [io  0x0000-0x001f]
[    1.508858] pnp 00:02: [io  0x0081-0x0091]
[    1.508860] pnp 00:02: [io  0x0093-0x009f]
[    1.508862] pnp 00:02: [io  0x00c0-0x00df]
[    1.508864] pnp 00:02: [dma 4]
[    1.508882] pnp 00:02: Plug and Play ACPI device, IDs PNP0200 (active)
[    1.508890] pnp 00:03: [mem 0xff000000-0xffffffff]
[    1.508906] pnp 00:03: Plug and Play ACPI device, IDs INT0800 (active)
[    1.509028] pnp 00:04: [mem 0xfed00000-0xfed003ff]
[    1.509047] pnp 00:04: Plug and Play ACPI device, IDs PNP0103 (active)
[    1.509057] pnp 00:05: [io  0x00f0]
[    1.509066] pnp 00:05: [irq 13]
[    1.509085] pnp 00:05: Plug and Play ACPI device, IDs PNP0c04 (active)
[    1.509096] pnp 00:06: [io  0x002e-0x002f]
[    1.509098] pnp 00:06: [io  0x004e-0x004f]
[    1.509100] pnp 00:06: [io  0x0061]
[    1.509102] pnp 00:06: [io  0x0063]
[    1.509104] pnp 00:06: [io  0x0065]
[    1.509105] pnp 00:06: [io  0x0067]
[    1.509107] pnp 00:06: [io  0x0070]
[    1.509109] pnp 00:06: [io  0x0080]
[    1.509111] pnp 00:06: [io  0x0092]
[    1.509115] pnp 00:06: [io  0x00b2-0x00b3]
[    1.509117] pnp 00:06: [io  0x0680-0x069f]
[    1.509118] pnp 00:06: [io  0x0800-0x080f]
[    1.509120] pnp 00:06: [io  0xffff]
[    1.509122] pnp 00:06: [io  0xffff]
[    1.509124] pnp 00:06: [io  0x0400-0x047f]
[    1.509126] pnp 00:06: [io  0x0500-0x057f]
[    1.509128] pnp 00:06: [io  0x164e-0x164f]
[    1.509129] pnp 00:06: [io  0x0380-0x038e]
[    1.509173] system 00:06: [io  0x0680-0x069f] has been reserved
[    1.509176] system 00:06: [io  0x0800-0x080f] has been reserved
[    1.509178] system 00:06: [io  0xffff] has been reserved
[    1.509181] system 00:06: [io  0xffff] has been reserved
[    1.509183] system 00:06: [io  0x0400-0x047f] has been reserved
[    1.509185] system 00:06: [io  0x0500-0x057f] has been reserved
[    1.509188] system 00:06: [io  0x164e-0x164f] has been reserved
[    1.509190] system 00:06: [io  0x0380-0x038e] has been reserved
[    1.509193] system 00:06: Plug and Play ACPI device, IDs PNP0c02 (active)
[    1.509202] pnp 00:07: [io  0x0070-0x0077]
[    1.509212] pnp 00:07: [irq 8]
[    1.509231] pnp 00:07: Plug and Play ACPI device, IDs PNP0b00 (active)
[    1.509241] pnp 00:08: [io  0x0060]
[    1.509243] pnp 00:08: [io  0x0064]
[    1.509251] pnp 00:08: [irq 1]
[    1.509271] pnp 00:08: Plug and Play ACPI device, IDs PNP0303 (active)
[    1.509294] pnp 00:09: [irq 12]
[    1.509318] pnp 00:09: Plug and Play ACPI device, IDs SYN1e10 SYN1e00 SYN0002 PNP0f13 (active)
[    1.509676] pnp 00:0a: [mem 0xfed1c000-0xfed1ffff]
[    1.509679] pnp 00:0a: [mem 0x00000000-0xffffffffffffffff disabled]
[    1.509681] pnp 00:0a: [mem 0xfed1b000-0xfed1bfff]
[    1.509683] pnp 00:0a: [mem 0x00000000-0xffffffffffffffff disabled]
[    1.509685] pnp 00:0a: [mem 0xe0000000-0xefffffff]
[    1.509687] pnp 00:0a: [mem 0xfed20000-0xfed3ffff]
[    1.509688] pnp 00:0a: [mem 0xfed90000-0xfed8ffff disabled]
[    1.509690] pnp 00:0a: [mem 0xfed45000-0xfed8ffff]
[    1.509692] pnp 00:0a: [mem 0xff000000-0xffffffff]
[    1.509694] pnp 00:0a: [mem 0xfee00000-0xfeefffff]
[    1.509696] pnp 00:0a: [mem 0xdd200000-0xdd200fff]
[    1.509745] system 00:0a: [mem 0xfed1c000-0xfed1ffff] has been reserved
[    1.509747] system 00:0a: [mem 0xfed1b000-0xfed1bfff] has been reserved
[    1.509750] system 00:0a: [mem 0xe0000000-0xefffffff] has been reserved
[    1.509752] system 00:0a: [mem 0xfed20000-0xfed3ffff] has been reserved
[    1.509755] system 00:0a: [mem 0xfed45000-0xfed8ffff] has been reserved
[    1.509757] system 00:0a: [mem 0xff000000-0xffffffff] could not be reserved
[    1.509760] system 00:0a: [mem 0xfee00000-0xfeefffff] could not be reserved
[    1.509762] system 00:0a: [mem 0xdd200000-0xdd200fff] has been reserved
[    1.509766] system 00:0a: Plug and Play ACPI device, IDs PNP0c02 (active)
[    1.509937] pnp 00:0b: [bus ff]
[    1.509959] pnp 00:0b: Plug and Play ACPI device, IDs PNP0a03 (active)
[    1.509978] pnp: PnP ACPI: found 12 devices
[    1.509979] ACPI: ACPI bus type pnp unregistered
[    1.516911] pci 0000:01:00.0: no compatible bridge window for [mem 0xfff80000-0xffffffff pref]
[    1.516915] pci 0000:03:00.0: no compatible bridge window for [mem 0xffff0000-0xffffffff pref]
[    1.516982] pci 0000:01:00.0: BAR 6: assigned [mem 0xd3080000-0xd30fffff pref]
[    1.516985] pci 0000:00:03.0: PCI bridge to [bus 01]
[    1.516987] pci 0000:00:03.0:   bridge window [io  0x7000-0x7fff]
[    1.516992] pci 0000:00:03.0:   bridge window [mem 0xd2000000-0xd30fffff]
[    1.516995] pci 0000:00:03.0:   bridge window [mem 0xc0000000-0xd1ffffff 64bit pref]
[    1.517000] pci 0000:00:1c.0: PCI bridge to [bus 02]
[    1.517007] pci 0000:00:1c.0:   bridge window [io  0x6000-0x6fff]
[    1.517016] pci 0000:00:1c.0:   bridge window [mem 0xdc100000-0xdd0fffff]
[    1.517024] pci 0000:00:1c.0:   bridge window [mem 0xd3100000-0xd40fffff 64bit pref]
[    1.517035] pci 0000:03:00.0: BAR 6: assigned [mem 0xd4110000-0xd411ffff pref]
[    1.517037] pci 0000:00:1c.1: PCI bridge to [bus 03]
[    1.517044] pci 0000:00:1c.1:   bridge window [io  0x5000-0x5fff]
[    1.517053] pci 0000:00:1c.1:   bridge window [mem 0xdb100000-0xdc0fffff]
[    1.517062] pci 0000:00:1c.1:   bridge window [mem 0xd4100000-0xd50fffff 64bit pref]
[    1.517072] pci 0000:00:1c.3: PCI bridge to [bus 04]
[    1.517080] pci 0000:00:1c.3:   bridge window [io  0x4000-0x4fff]
[    1.517088] pci 0000:00:1c.3:   bridge window [mem 0xda100000-0xdb0fffff]
[    1.517097] pci 0000:00:1c.3:   bridge window [mem 0xd5100000-0xd60fffff 64bit pref]
[    1.517108] pci 0000:00:1c.4: PCI bridge to [bus 05]
[    1.517115] pci 0000:00:1c.4:   bridge window [io  0x3000-0x3fff]
[    1.517124] pci 0000:00:1c.4:   bridge window [mem 0xd9100000-0xda0fffff]
[    1.517133] pci 0000:00:1c.4:   bridge window [mem 0xd6100000-0xd70fffff 64bit pref]
[    1.517143] pci 0000:00:1c.7: PCI bridge to [bus 06-09]
[    1.517151] pci 0000:00:1c.7:   bridge window [io  0x2000-0x2fff]
[    1.517159] pci 0000:00:1c.7:   bridge window [mem 0xd8100000-0xd90fffff]
[    1.517168] pci 0000:00:1c.7:   bridge window [mem 0xd7100000-0xd80fffff 64bit pref]
[    1.517178] pci 0000:00:1e.0: PCI bridge to [bus 0a]
[    1.517259] pci 0000:00:1e.0: setting latency timer to 64
[    1.517267] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
[    1.517269] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
[    1.517271] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
[    1.517273] pci_bus 0000:00: resource 7 [mem 0xc0000000-0xfeafffff]
[    1.517276] pci_bus 0000:01: resource 0 [io  0x7000-0x7fff]
[    1.517278] pci_bus 0000:01: resource 1 [mem 0xd2000000-0xd30fffff]
[    1.517280] pci_bus 0000:01: resource 2 [mem 0xc0000000-0xd1ffffff 64bit pref]
[    1.517282] pci_bus 0000:02: resource 0 [io  0x6000-0x6fff]
[    1.517284] pci_bus 0000:02: resource 1 [mem 0xdc100000-0xdd0fffff]
[    1.517286] pci_bus 0000:02: resource 2 [mem 0xd3100000-0xd40fffff 64bit pref]
[    1.517288] pci_bus 0000:03: resource 0 [io  0x5000-0x5fff]
[    1.517290] pci_bus 0000:03: resource 1 [mem 0xdb100000-0xdc0fffff]
[    1.517292] pci_bus 0000:03: resource 2 [mem 0xd4100000-0xd50fffff 64bit pref]
[    1.517294] pci_bus 0000:04: resource 0 [io  0x4000-0x4fff]
[    1.517296] pci_bus 0000:04: resource 1 [mem 0xda100000-0xdb0fffff]
[    1.517298] pci_bus 0000:04: resource 2 [mem 0xd5100000-0xd60fffff 64bit pref]
[    1.517300] pci_bus 0000:05: resource 0 [io  0x3000-0x3fff]
[    1.517302] pci_bus 0000:05: resource 1 [mem 0xd9100000-0xda0fffff]
[    1.517304] pci_bus 0000:05: resource 2 [mem 0xd6100000-0xd70fffff 64bit pref]
[    1.517306] pci_bus 0000:06: resource 0 [io  0x2000-0x2fff]
[    1.517308] pci_bus 0000:06: resource 1 [mem 0xd8100000-0xd90fffff]
[    1.517310] pci_bus 0000:06: resource 2 [mem 0xd7100000-0xd80fffff 64bit pref]
[    1.517312] pci_bus 0000:0a: resource 4 [io  0x0000-0x0cf7]
[    1.517314] pci_bus 0000:0a: resource 5 [io  0x0d00-0xffff]
[    1.517316] pci_bus 0000:0a: resource 6 [mem 0x000a0000-0x000bffff]
[    1.517318] pci_bus 0000:0a: resource 7 [mem 0xc0000000-0xfeafffff]
[    1.517355] NET: Registered protocol family 2
[    1.518050] TCP established hash table entries: 524288 (order: 11, 8388608 bytes)
[    1.521125] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    1.521499] TCP: Hash tables configured (established 524288 bind 65536)
[    1.521531] TCP: reno registered
[    1.521545] UDP hash table entries: 4096 (order: 5, 131072 bytes)
[    1.521623] UDP-Lite hash table entries: 4096 (order: 5, 131072 bytes)
[    1.521764] NET: Registered protocol family 1
[    1.550763] pci 0000:01:00.0: Boot video device
[    1.550842] PCI: CLS 64 bytes, default 64
[    1.550893] Trying to unpack rootfs image as initramfs...
[    2.024453] Freeing initrd memory: 23292k freed
[    2.028107] PCI-DMA: Using software bounce buffering for IO (SWIOTLB)
[    2.028113] software IO TLB [mem 0xbb681000-0xbf680fff] (64MB) mapped at [ffff8800bb681000-ffff8800bf680fff]
[    2.028162] Simple Boot Flag at 0x44 set to 0x1
[    2.028689] Initialise module verification
[    2.028735] audit: initializing netlink socket (disabled)
[    2.028745] type=2000 audit(1362867502.968:1): initialized
[    2.062847] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    2.064412] VFS: Disk quotas dquot_6.5.2
[    2.064461] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    2.064980] fuse init (API version 7.20)
[    2.065074] msgmni has been set to 11915
[    2.065653] Key type asymmetric registered
[    2.065655] Asymmetric key parser 'x509' registered
[    2.065687] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 252)
[    2.065726] io scheduler noop registered
[    2.065728] io scheduler deadline registered (default)
[    2.065733] io scheduler cfq registered
[    2.066078] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    2.066099] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    2.066144] intel_idle: MWAIT substates: 0x1120
[    2.066161] intel_idle: v0.4 model 0x1E
[    2.066162] intel_idle: lapic_timer_reliable_states 0x2
[    2.066913] ACPI: AC Adapter [ACAD] (on-line)
[    2.067014] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0
[    2.067018] ACPI: Power Button [PWRB]
[    2.067074] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input1
[    2.067533] ACPI: Lid Switch [LID0]
[    2.067605] input: Sleep Button as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input2
[    2.067609] ACPI: Sleep Button [SLPB]
[    2.067648] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input3
[    2.067651] ACPI: Power Button [PWRF]
[    2.067800] ACPI: Requesting acpi_cpufreq
[    2.073406] ACPI: thermal control disabled
[    2.073427] GHES: HEST is not enabled!
[    2.073507] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    2.075783] Linux agpgart interface v0.103
[    2.077410] brd: module loaded
[    2.078207] loop: module loaded
[    2.078299] ahci 0000:00:1f.2: version 3.0
[    2.078384] ahci 0000:00:1f.2: irq 45 for MSI/MSI-X
[    2.078487] ahci 0000:00:1f.2: AHCI 0001.0300 32 slots 6 ports 3 Gbps 0x33 impl SATA mode
[    2.078491] ahci 0000:00:1f.2: flags: 64bit ncq sntf ilck pm led clo pio slum part ems sxs apst 
[    2.078499] ahci 0000:00:1f.2: setting latency timer to 64
[    2.102857] scsi0 : ahci
[    2.102933] scsi1 : ahci
[    2.102997] scsi2 : ahci
[    2.103066] scsi3 : ahci
[    2.103126] scsi4 : ahci
[    2.103186] scsi5 : ahci
[    2.103220] ata1: SATA max UDMA/133 abar m2048@0xdd105000 port 0xdd105100 irq 45
[    2.103227] ata2: SATA max UDMA/133 abar m2048@0xdd105000 port 0xdd105180 irq 45
[    2.103229] ata3: DUMMY
[    2.103230] ata4: DUMMY
[    2.103237] ata5: SATA max UDMA/133 abar m2048@0xdd105000 port 0xdd105300 irq 45
[    2.103243] ata6: SATA max UDMA/133 abar m2048@0xdd105000 port 0xdd105380 irq 45
[    2.103525] libphy: Fixed MDIO Bus: probed
[    2.103579] tun: Universal TUN/TAP device driver, 1.6
[    2.103580] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    2.103658] PPP generic driver version 2.4.2
[    2.103719] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    2.103761] ehci_hcd 0000:00:1a.0: setting latency timer to 64
[    2.103769] ehci_hcd 0000:00:1a.0: EHCI Host Controller
[    2.103774] ehci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 1
[    2.107720] ehci_hcd 0000:00:1a.0: debug port 2
[    2.107735] ehci_hcd 0000:00:1a.0: cache line size of 64 is not supported
[    2.107755] ehci_hcd 0000:00:1a.0: irq 16, io mem 0xdd105c00
[    2.118457] ehci_hcd 0000:00:1a.0: USB 2.0 started, EHCI 1.00
[    2.118484] usb usb1: New USB device found, idVendor=1d6b, idProduct=0002
[    2.118488] usb usb1: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    2.118491] usb usb1: Product: EHCI Host Controller
[    2.118495] usb usb1: Manufacturer: Linux 3.7.0-7-generic ehci_hcd
[    2.118498] usb usb1: SerialNumber: 0000:00:1a.0
[    2.118616] hub 1-0:1.0: USB hub found
[    2.118621] hub 1-0:1.0: 3 ports detected
[    2.118759] ehci_hcd 0000:00:1d.0: setting latency timer to 64
[    2.118767] ehci_hcd 0000:00:1d.0: EHCI Host Controller
[    2.118772] ehci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    2.122698] ehci_hcd 0000:00:1d.0: debug port 2
[    2.122709] ehci_hcd 0000:00:1d.0: cache line size of 64 is not supported
[    2.122728] ehci_hcd 0000:00:1d.0: irq 21, io mem 0xdd105800
[    2.134449] ehci_hcd 0000:00:1d.0: USB 2.0 started, EHCI 1.00
[    2.134489] usb usb2: New USB device found, idVendor=1d6b, idProduct=0002
[    2.134493] usb usb2: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    2.134497] usb usb2: Product: EHCI Host Controller
[    2.134500] usb usb2: Manufacturer: Linux 3.7.0-7-generic ehci_hcd
[    2.134503] usb usb2: SerialNumber: 0000:00:1d.0
[    2.134674] hub 2-0:1.0: USB hub found
[    2.134679] hub 2-0:1.0: 3 ports detected
[    2.134790] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    2.134807] uhci_hcd: USB Universal Host Controller Interface driver
[    2.134867] i8042: PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    2.140468] ACPI: Battery Slot [BAT0] (battery present)
[    2.167300] serio: i8042 KBD port at 0x60,0x64 irq 1
[    2.167306] serio: i8042 AUX port at 0x60,0x64 irq 12
[    2.167446] mousedev: PS/2 mouse device common for all mice
[    2.169111] rtc_cmos 00:07: RTC can wake from S4
[    2.169261] rtc_cmos 00:07: rtc core: registered rtc_cmos as rtc0
[    2.169298] rtc0: alarms up to one year, y3k, 242 bytes nvram, hpet irqs
[    2.169386] device-mapper: uevent: version 1.0.3
[    2.169460] device-mapper: ioctl: 4.23.0-ioctl (2012-07-25) initialised: dm-devel@redhat.com
[    2.169574] cpuidle: using governor ladder
[    2.169724] cpuidle: using governor menu
[    2.169728] ledtrig-cpu: registered to indicate activity on CPUs
[    2.169730] EFI Variables Facility v0.08 2004-May-17
[    2.169916] ashmem: initialized
[    2.170038] TCP: cubic registered
[    2.170134] NET: Registered protocol family 10
[    2.170310] NET: Registered protocol family 17
[    2.170322] Key type dns_resolver registered
[    2.170699] Loading module verification certificates
[    2.171850] MODSIGN: Loaded cert 'Magrathea: Glacier signing key: a37e8d8f17247a12bca04fac461c3b30422126d5'
[    2.171863] registered taskstats version 1
[    2.174744] Key type trusted registered
[    2.179422] Key type encrypted registered
[    2.185358] rtc_cmos 00:07: setting system clock to 2013-03-09 22:18:24 UTC (1362867504)
[    2.187584] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    2.187586] EDD information not available.
[    2.189905] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input4
[    2.422594] ata5: SATA link down (SStatus 0 SControl 300)
[    2.422642] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    2.422667] ata6: SATA link down (SStatus 0 SControl 300)
[    2.422700] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    2.425043] ata1.00: ATA-8: WDC WD3200BEKT-60V5T1, 12.01A12, max UDMA/100
[    2.425048] ata1.00: 625142448 sectors, multi 0: LBA48 NCQ (depth 31/32), AA
[    2.425262] ata1.00: failed to get Identify Device Data, Emask 0x1
[    2.425701] ata2.00: ATAPI: hp      DVDRAM GT30L, mP04, max UDMA/100
[    2.427980] ata1.00: failed to get Identify Device Data, Emask 0x1
[    2.427988] ata1.00: configured for UDMA/100
[    2.428470] scsi 0:0:0:0: Direct-Access     ATA      WDC WD3200BEKT-6 12.0 PQ: 0 ANSI: 5
[    2.428780] sd 0:0:0:0: [sda] 625142448 512-byte logical blocks: (320 GB/298 GiB)
[    2.428860] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    2.429049] sd 0:0:0:0: [sda] Write Protect is off
[    2.429053] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    2.429110] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.430391] ata2.00: configured for UDMA/100
[    2.430416] usb 1-1: new high-speed USB device number 2 using ehci_hcd
[    2.435420] scsi 1:0:0:0: CD-ROM            hp       DVDRAM GT30L     mP04 PQ: 0 ANSI: 5
[    2.439468] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[    2.439472] cdrom: Uniform CD-ROM driver Revision: 3.20
[    2.439627] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    2.439705] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    2.466499]  sda: sda1 sda2 < sda5 sda6 >
[    2.468427] sd 0:0:0:0: [sda] Attached SCSI disk
[    2.469711] Freeing unused kernel memory: 984k freed
[    2.469846] Write protecting the kernel read-only data: 12288k
[    2.472795] Freeing unused kernel memory: 1280k freed
[    2.475363] Freeing unused kernel memory: 1148k freed
[    2.495219] udevd[147]: starting version 175
[    2.516151] Disabling lock debugging due to kernel taint
[    2.532356] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    2.532805] r8169 0000:03:00.0: irq 46 for MSI/MSI-X
[    2.533141] r8169 0000:03:00.0 eth0: RTL8168d/8111d at 0xffffc90011594000, 00:26:9e:d0:71:c7, XID 083000c0 IRQ 46
[    2.533145] r8169 0000:03:00.0 eth0: jumbo features [frames: 9200 bytes, tx checksumming: ko]
[    2.534774] sdhci: Secure Digital Host Controller Interface driver
[    2.534777] sdhci: Copyright(c) Pierre Ossman
[    2.538846] sdhci-pci 0000:05:00.1: SDHCI controller found [197b:2382] (rev 0)
[    2.538936] mmc0: no vqmmc regulator found
[    2.538939] mmc0: no vmmc regulator found
[    2.538991] Registered led device: mmc0::
[    2.542564] acpi device:0c: registered as cooling_device8
[    2.542604] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[    2.542679] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:09/LNXVIDEO:01/input/input5
[    2.562774] usb 1-1: New USB device found, idVendor=8087, idProduct=0020
[    2.562778] usb 1-1: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[    2.563182] hub 1-1:1.0: USB hub found
[    2.563262] hub 1-1:1.0: 6 ports detected
[    2.570377] mmc0: SDHCI controller on PCI [0000:05:00.1] using DMA
[    2.570406] sdhci-pci 0000:05:00.2: SDHCI controller found [197b:2381] (rev 0)
[    2.570432] sdhci-pci 0000:05:00.2: Refusing to bind to secondary interface.
[    2.634506] firewire_ohci 0000:05:00.0: added OHCI v1.10 device as card 0, 4 IR + 4 IT contexts, quirks 0x10
[    2.674351] usb 2-1: new high-speed USB device number 2 using ehci_hcd
[    2.806786] usb 2-1: New USB device found, idVendor=8087, idProduct=0020
[    2.806788] usb 2-1: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[    2.807277] hub 2-1:1.0: USB hub found
[    2.807452] hub 2-1:1.0: 8 ports detected
[    3.026149] tsc: Refined TSC clocksource calibration: 1728.999 MHz
[    3.026156] Switching to clocksource tsc
[    3.078315] usb 2-1.5: new high-speed USB device number 3 using ehci_hcd
[    3.134377] firewire_core 0000:05:00.0: created device fw0: GUID 00241b008b5cb701, S400
[    3.205124] usb 2-1.5: New USB device found, idVendor=064e, idProduct=a127
[    3.205129] usb 2-1.5: New USB device strings: Mfr=2, Product=1, SerialNumber=3
[    3.205133] usb 2-1.5: Product: HP Webcam
[    3.205137] usb 2-1.5: Manufacturer: SuYin
[    3.205140] usb 2-1.5: SerialNumber: CN0316-S30C-OV10-VH-R02.01.00
[    3.278266] usb 2-1.7: new full-speed USB device number 4 using ehci_hcd
[    3.373930] usb 2-1.7: New USB device found, idVendor=03f0, idProduct=231d
[    3.373936] usb 2-1.7: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[    3.373940] usb 2-1.7: Product: HP Integrated Module
[    3.373943] usb 2-1.7: Manufacturer: Broadcom Corp
[    4.006946] xor: automatically using best checksumming function:
[    4.045739]    generic_sse: 10858.000 MB/sec
[    4.047625] device-mapper: dm-raid45: initialized v0.2594b
[    4.128450] Btrfs loaded
[    4.305175] EXT4-fs (sda1): INFO: recovery required on readonly filesystem
[    4.305180] EXT4-fs (sda1): write access will be enabled during recovery
[    6.195143] EXT4-fs (sda1): recovery complete
[    6.202708] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)
[    9.849510] Adding 5859324k swap on /dev/sda5.  Priority:-1 extents:1 across:5859324k 
[    9.898552] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[    9.939981] udevd[479]: starting version 175
[   10.391084] lp: driver loaded but no devices found
[   10.831132] wmi: Mapper loaded
[   10.925346] ACPI Warning: 0x0000000000000428-0x000000000000042f SystemIO conflicts with Region \PMIO 1 (20120913/utaddress-251)
[   10.925354] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   10.925357] ACPI Warning: 0x0000000000000540-0x000000000000054f SystemIO conflicts with Region \GPIO 1 (20120913/utaddress-251)
[   10.925361] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   10.925362] ACPI Warning: 0x0000000000000530-0x000000000000053f SystemIO conflicts with Region \GPIO 1 (20120913/utaddress-251)
[   10.925366] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   10.925367] ACPI Warning: 0x0000000000000500-0x000000000000052f SystemIO conflicts with Region \GPIO 1 (20120913/utaddress-251)
[   10.925370] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   10.925371] lpc_ich: Resource conflict(s) found affecting gpio_ich
[   11.095565] input: HP WMI hotkeys as /devices/virtual/input/input6
[   11.109177] EDAC MC: Ver: 3.0.0
[   11.129360] ene_ir: chip is 0x3926 - kbver = 0x00, rev = 0xd2
[   11.129361] ene_ir: PLL freq = 1406
[   11.129361] ene_ir: KB3926D or higher detected
[   11.129387] ene_ir: Firmware regs: c0 01
[   11.129388] ene_ir: Hardware features:
[   11.129388] ene_ir: * Uses GPIO 40 for IR demodulated input
[   11.152011] EDAC i7core: Device not found: dev 00.0 PCI ID 8086:2c50
[   11.161527] cfg80211: Calling CRDA to update world regulatory domain
[   11.194639] Registered IR keymap rc-rc6-mce
[   11.194757] input: ENE eHome Infrared Remote Receiver as /devices/virtual/rc/rc0/input7
[   11.194927] rc0: ENE eHome Infrared Remote Receiver as /devices/virtual/rc/rc0
[   11.195013] ene_ir: driver has been successfully loaded
[   11.301051] IR NEC protocol handler initialized
[   11.361224] IR RC5(x) protocol handler initialized
[   11.367102] IR RC6 protocol handler initialized
[   11.368218] Bluetooth: Core ver 2.16
[   11.368244] NET: Registered protocol family 31
[   11.368246] Bluetooth: HCI device and connection manager initialized
[   11.368254] Bluetooth: HCI socket layer initialized
[   11.368258] Bluetooth: L2CAP socket layer initialized
[   11.368266] Bluetooth: SCO socket layer initialized
[   11.413292] microcode: CPU0 sig=0x106e5, pf=0x10, revision=0x3
[   11.423080] Intel(R) Wireless WiFi driver for Linux, in-tree:
[   11.423083] Copyright(c) 2003-2012 Intel Corporation
[   11.423154] iwlwifi 0000:02:00.0: pci_resource_len = 0x00002000
[   11.423157] iwlwifi 0000:02:00.0: pci_resource_base = ffffc90011590000
[   11.423159] iwlwifi 0000:02:00.0: HW Revision ID = 0x0
[   11.423326] iwlwifi 0000:02:00.0: irq 47 for MSI/MSI-X
[   11.440217] usbcore: registered new interface driver btusb
[   11.494759] device-mapper: multipath: version 1.5.0 loaded
[   11.502887] IR JVC protocol handler initialized
[   11.504398] IR Sony protocol handler initialized
[   11.517178] input: MCE IR Keyboard/Mouse (ene_ir) as /devices/virtual/input/input8
[   11.517279] IR MCE Keyboard/mouse protocol handler initialized
[   11.518877] lirc_dev: IR Remote Control driver registered, major 250 
[   11.552507] microcode: CPU1 sig=0x106e5, pf=0x10, revision=0x3
[   11.553703] microcode: CPU2 sig=0x106e5, pf=0x10, revision=0x3
[   11.554946] microcode: CPU3 sig=0x106e5, pf=0x10, revision=0x3
[   11.556106] microcode: CPU4 sig=0x106e5, pf=0x10, revision=0x3
[   11.557172] microcode: CPU5 sig=0x106e5, pf=0x10, revision=0x3
[   11.558571] microcode: CPU6 sig=0x106e5, pf=0x10, revision=0x3
[   11.559850] microcode: CPU7 sig=0x106e5, pf=0x10, revision=0x3
[   11.561154] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[   11.658548] rc rc0: lirc_dev: driver ir-lirc-codec (ene_ir) registered at minor = 0
[   11.658553] IR LIRC bridge handler initialized
[   11.676693] iwlwifi 0000:02:00.0: loaded firmware version 8.83.5.1 build 33692
[   11.907035] Linux media interface: v0.10
[   11.949339] Linux video capture interface: v2.00
[   11.963820] uvcvideo: Found UVC 1.00 device HP Webcam (064e:a127)
[   11.980966] input: HP Webcam as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.5/2-1.5:1.0/input/input9
[   11.981066] usbcore: registered new interface driver uvcvideo
[   11.981068] USB Video Class driver (1.1.1)
[   12.023611] kvm: disabled by bios
[   12.027186] kvm: disabled by bios
[   12.071570] type=1400 audit(1362867514.387:2): apparmor="STATUS" operation="profile_load" name="/usr/sbin/ntpd" pid=853 comm="apparmor_parser"
[   12.071595] type=1400 audit(1362867514.387:3): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/ntpd" pid=826 comm="apparmor_parser"
[   12.233671] nvidia: module license 'NVIDIA' taints kernel.
[   12.243776] vgaarb: device changed decodes: PCI:0000:01:00.0,olddecodes=io+mem,decodes=none:owns=io+mem
[   12.243928] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  313.26  Wed Feb 27 13:04:31 PST 2013
[   12.258998] iwldvm: Intel(R) Wireless WiFi Link AGN driver for Linux, in-tree:
[   12.259000] iwldvm: Copyright(c) 2003-2012 Intel Corporation
[   12.259022] iwlwifi 0000:02:00.0: CONFIG_IWLWIFI_DEBUG disabled
[   12.259025] iwlwifi 0000:02:00.0: CONFIG_IWLWIFI_DEBUGFS enabled
[   12.259026] iwlwifi 0000:02:00.0: CONFIG_IWLWIFI_DEVICE_TRACING enabled
[   12.259028] iwlwifi 0000:02:00.0: CONFIG_IWLWIFI_DEVICE_TESTMODE enabled
[   12.259030] iwlwifi 0000:02:00.0: CONFIG_IWLWIFI_P2P disabled
[   12.259032] iwlwifi 0000:02:00.0: Detected Intel(R) WiFi Link 5100 AGN, REV=0x54
[   12.259082] iwlwifi 0000:02:00.0: L1 Enabled; Disabling L0S
[   12.262077] iwlwifi 0000:02:00.0: RF_KILL bit toggled to enable radio.
[   12.271048] snd_hda_intel 0000:00:1b.0: irq 48 for MSI/MSI-X
[   12.280734] iwlwifi 0000:02:00.0: device EEPROM VER=0x11f, CALIB=0x4
[   12.280737] iwlwifi 0000:02:00.0: Device SKU: 0xF0
[   12.280739] iwlwifi 0000:02:00.0: Valid Tx ant: 0x2, Valid Rx ant: 0x3
[   12.280858] Registered led device: phy0-led
[   12.290447] cfg80211: World regulatory domain updated:
[   12.290448] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   12.290450] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   12.290451] cfg80211:   (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   12.290452] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   12.290453] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   12.290454] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   12.326843] input: HDA Intel MID Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input10
[   12.327067] input: HDA Intel MID Front Line Out as /devices/pci0000:00/0000:00:1b.0/sound/card0/input11
[   12.328087] hda_intel: Disabling MSI
[   12.328095] hda-intel: 0000:01:00.1: Handle VGA-switcheroo audio client
[   12.332708] ieee80211 phy0: Selected rate control algorithm 'iwl-agn-rs'
[   12.647100] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
[   12.783641] psmouse serio1: synaptics: Touchpad model: 1, fw: 6.5, id: 0x1c0b1, caps: 0xa04751/0xa00000/0x0, board id: 3655, fw id: 428212
[   12.858168] EXT4-fs (sda6): mounted filesystem with ordered data mode. Opts: (null)
[   12.876032] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input12
[   12.926674] init: failsafe main process (1063) killed by TERM signal
[   13.285442] type=1400 audit(1362867515.599:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/x86_64-linux-gnu/lightdm-remote-session-freerdp/freerdp-session-wrapper" pid=1130 comm="apparmor_parser"
[   13.285668] type=1400 audit(1362867515.599:5): apparmor="STATUS" operation="profile_load" name="/usr/lib/x86_64-linux-gnu/lightdm-remote-session-freerdp/freerdp-session-wrapper//chromium_browser" pid=1130 comm="apparmor_parser"
[   13.287609] type=1400 audit(1362867515.603:6): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/ntpd" pid=1138 comm="apparmor_parser"
[   13.301535] type=1400 audit(1362867515.615:7): apparmor="STATUS" operation="profile_load" name="/usr/lib/lightdm/lightdm/lightdm-guest-session-wrapper" pid=1129 comm="apparmor_parser"
[   13.301947] type=1400 audit(1362867515.619:8): apparmor="STATUS" operation="profile_load" name="/usr/lib/lightdm/lightdm/lightdm-guest-session-wrapper//chromium_browser" pid=1129 comm="apparmor_parser"
[   13.305929] input: HDA NVidia HDMI/DP,pcm=9 as /devices/pci0000:00/0000:00:03.0/0000:01:00.1/sound/card1/input13
[   13.306075] input: HDA NVidia HDMI/DP,pcm=8 as /devices/pci0000:00/0000:00:03.0/0000:01:00.1/sound/card1/input14
[   13.306246] input: HDA NVidia HDMI/DP,pcm=7 as /devices/pci0000:00/0000:00:03.0/0000:01:00.1/sound/card1/input15
[   13.306484] input: HDA NVidia HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:03.0/0000:01:00.1/sound/card1/input16
[   13.309450] type=1400 audit(1362867515.623:9): apparmor="STATUS" operation="profile_load" name="/usr/lib/x86_64-linux-gnu/lightdm-remote-session-uccsconfigure/uccsconfigure-session-wrapper" pid=1131 comm="apparmor_parser"
[   13.309830] type=1400 audit(1362867515.627:10): apparmor="STATUS" operation="profile_load" name="/usr/lib/x86_64-linux-gnu/lightdm-remote-session-uccsconfigure/uccsconfigure-session-wrapper//chromium_browser" pid=1131 comm="apparmor_parser"
[   13.392510] type=1400 audit(1362867515.711:11): apparmor="STATUS" operation="profile_load" name="/usr/sbin/mysqld" pid=1137 comm="apparmor_parser"
[   13.858263] init: Failed to spawn mysql main process: unable to execute: No such file or directory
[   13.981283] ppdev: user-space parallel port driver
[   14.328932] vboxdrv: Found 8 processor cores.
[   14.329290] vboxdrv: fAsync=0 offMin=0x1ef offMax=0x6be4
[   14.329357] vboxdrv: TSC mode is 'synchronous', kernel timer mode is 'normal'.
[   14.329358] vboxdrv: Successfully loaded version 4.1.24 (interface 0x00190000).
[   14.712614] vboxpci: IOMMU not found (not registered)
[   14.839170] Bluetooth: RFCOMM TTY layer initialized
[   14.839181] Bluetooth: RFCOMM socket layer initialized
[   14.839182] Bluetooth: RFCOMM ver 1.11
[   14.890165] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   14.890168] Bluetooth: BNEP filters: protocol multicast
[   14.890173] Bluetooth: BNEP socket layer initialized
[   15.505377] init: udev-fallback-graphics main process (1468) terminated with status 1
[   16.750892] iwlwifi 0000:02:00.0: L1 Enabled; Disabling L0S
[   16.753951] iwlwifi 0000:02:00.0: Radio type=0x1-0x2-0x0
[   16.956933] iwlwifi 0000:02:00.0: L1 Enabled; Disabling L0S
[   16.959944] iwlwifi 0000:02:00.0: Radio type=0x1-0x2-0x0
[   17.101958] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   17.102308] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   17.213375] r8169 0000:03:00.0 eth0: link down
[   17.213419] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   17.213662] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   23.711793] wlan0: authenticate with cc:af:78:4c:79:50
[   23.716320] wlan0: send auth to cc:af:78:4c:79:50 (try 1/3)
[   23.722078] wlan0: authenticated
[   23.722292] iwlwifi 0000:02:00.0 wlan0: disabling HT/VHT due to WEP/TKIP use
[   23.725437] wlan0: associate with cc:af:78:4c:79:50 (try 1/3)
[   23.731485] wlan0: RX AssocResp from cc:af:78:4c:79:50 (capab=0x411 status=0 aid=1)
[   23.744729] wlan0: associated
[   23.744752] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   26.944330] init: mythtv-backend main process (2157) terminated with status 127
[   26.944356] init: mythtv-backend main process ended, respawning
[   26.948047] init: mythtv-backend main process (2201) terminated with status 127
[   26.948065] init: mythtv-backend main process ended, respawning
[   26.950857] init: mythtv-backend main process (2204) terminated with status 127
[   26.950881] init: mythtv-backend respawning too fast, stopped
```

Pls advise.

---

### Post by m_dk29 on 2013-03-19
Any help?

---

