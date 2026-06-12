---
title: "Linux randomly complete locks up"
date: 2010-05-23
forum: Hardware
---

### Post by shadylookin on 2010-05-23
I've been having an issue where my computer will just lock up. Not just the mouse or keyboard either programs as well. There doesn't seem to be a pattern to it either. Sometimes it happens 5 minutes after boot somethings over a week. Sometimes after it locks up it will reboot, other times it won't. I don't think this is just an ubuntu issue either since It's happened on Ubuntu, Debian, Mint, and Sabayon(which isn't even debian based).

Recently it happened at 12:10 and these are the closest log messages to it.

```

22 23:57:34 bdt kernel: [ 2566.518730] __ratelimit: 9 callbacks suppressed
May 22 23:57:34 bdt kernel: [ 2566.518734] evince[5182]: segfault at 666e77 ip 00007f3009712fe3 sp 00007f2fff92c570 error 4 in libfontconfig.so.1.4.4[7f3009709000+33000]
May 23 00:00:58 bdt kernel: [ 2770.629594] VBoxDrv: dbg - g_abExecMemory=ffffffffa03faa20
May 23 00:00:58 bdt kernel: [ 2770.629663] vboxdrv: fAsync=0 offMin=0x1a0 offMax=0x3380
May 23 00:00:58 bdt kernel: [ 2770.629713] vboxdrv: TSC mode is 'synchronous', kernel timer mode is 'normal'.
May 23 00:01:55 bdt sudo: pam_sm_authenticate: Called
May 23 00:01:55 bdt sudo: pam_sm_authenticate: username = [bpoconner]
May 23 00:01:55 bdt sudo: pam_sm_authenticate: /home/bpoconner is already mounted
```

Here's an entire session from starting at 12:18 and it locked up at 12:26

```

May 23 00:18:48 bdt kernel: imklog 4.2.0, log source = /proc/kmsg started.
May 23 00:18:48 bdt rsyslogd: [origin software="rsyslogd" swVersion="4.2.0" x-pid="1011" x-info="http://www.rsyslog.com"] (re)start
May 23 00:18:48 bdt rsyslogd: rsyslogd's groupid changed to 103
May 23 00:18:48 bdt rsyslogd: rsyslogd's userid changed to 101
May 23 00:18:48 bdt kernel: [    0.000000] Initializing cgroup subsys cpuset
May 23 00:18:48 bdt kernel: [    0.000000] Initializing cgroup subsys cpu
May 23 00:18:48 bdt kernel: [    0.000000] Linux version 2.6.32-21-generic (buildd@yellow) (gcc version 4.4.3 (Ubuntu 4.4.3-4ubuntu5) ) #32-Ubuntu SMP Fri Apr 16 08:09:38 UTC 2010 (Ubuntu 2.6.32-21.32-generic 2.6.32.11+drm33.2)
May 23 00:18:48 bdt kernel: [    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-2.6.32-21-generic root=UUID=426b3181-4dd8-4420-99d5-4b476b5c3b3e ro quiet splash
May 23 00:18:48 bdt kernel: [    0.000000] KERNEL supported cpus:
May 23 00:18:48 bdt kernel: [    0.000000]   Intel GenuineIntel
May 23 00:18:48 bdt kernel: [    0.000000]   AMD AuthenticAMD
May 23 00:18:48 bdt kernel: [    0.000000]   Centaur CentaurHauls
May 23 00:18:48 bdt kernel: [    0.000000] BIOS-provided physical RAM map:
May 23 00:18:48 bdt kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 0000000000095c00 (usable)
May 23 00:18:48 bdt kernel: [    0.000000]  BIOS-e820: 0000000000095c00 - 00000000000a0000 (reserved)
May 23 00:18:48 bdt kernel: [    0.000000]  BIOS-e820: 00000000000e5000 - 0000000000100000 (reserved)
May 23 00:18:48 bdt kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 00000000bff90000 (usable)
May 23 00:18:48 bdt kernel: [    0.000000]  BIOS-e820: 00000000bff90000 - 00000000bff9e000 (ACPI data)
May 23 00:18:48 bdt kernel: [    0.000000]  BIOS-e820: 00000000bff9e000 - 00000000bffe0000 (ACPI NVS)
May 23 00:18:48 bdt kernel: [    0.000000]  BIOS-e820: 00000000bffe0000 - 00000000c0000000 (reserved)
May 23 00:18:48 bdt kernel: [    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
May 23 00:18:48 bdt kernel: [    0.000000]  BIOS-e820: 00000000ffb00000 - 0000000100000000 (reserved)
May 23 00:18:48 bdt kernel: [    0.000000]  BIOS-e820: 0000000100000000 - 0000000240000000 (usable)
May 23 00:18:48 bdt kernel: [    0.000000] DMI present.
May 23 00:18:48 bdt kernel: [    0.000000] AMI BIOS detected: BIOS may corrupt low RAM, working around it.
May 23 00:18:48 bdt kernel: [    0.000000] last_pfn = 0x240000 max_arch_pfn = 0x400000000
May 23 00:18:48 bdt kernel: [    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
May 23 00:18:48 bdt kernel: [    0.000000] last_pfn = 0xbff90 max_arch_pfn = 0x400000000
May 23 00:18:48 bdt kernel: [    0.000000] Scanning 0 areas for low memory corruption
May 23 00:18:48 bdt kernel: [    0.000000] modified physical RAM map:
May 23 00:18:48 bdt kernel: [    0.000000]  modified: 0000000000000000 - 0000000000010000 (reserved)
May 23 00:18:48 bdt kernel: [    0.000000]  modified: 0000000000010000 - 0000000000095c00 (usable)
May 23 00:18:48 bdt kernel: [    0.000000]  modified: 0000000000095c00 - 00000000000a0000 (reserved)
May 23 00:18:48 bdt kernel: [    0.000000]  modified: 00000000000e5000 - 0000000000100000 (reserved)
May 23 00:18:48 bdt kernel: [    0.000000]  modified: 0000000000100000 - 00000000bff90000 (usable)
May 23 00:18:48 bdt kernel: [    0.000000]  modified: 00000000bff90000 - 00000000bff9e000 (ACPI data)
May 23 00:18:48 bdt kernel: [    0.000000]  modified: 00000000bff9e000 - 00000000bffe0000 (ACPI NVS)
May 23 00:18:48 bdt kernel: [    0.000000]  modified: 00000000bffe0000 - 00000000c0000000 (reserved)
May 23 00:18:48 bdt kernel: [    0.000000]  modified: 00000000fee00000 - 00000000fee01000 (reserved)
May 23 00:18:48 bdt kernel: [    0.000000]  modified: 00000000ffb00000 - 0000000100000000 (reserved)
May 23 00:18:48 bdt kernel: [    0.000000]  modified: 0000000100000000 - 0000000240000000 (usable)
May 23 00:18:48 bdt kernel: [    0.000000] init_memory_mapping: 0000000000000000-00000000bff90000
May 23 00:18:48 bdt kernel: [    0.000000] NX (Execute Disable) protection: active
May 23 00:18:48 bdt kernel: [    0.000000] init_memory_mapping: 0000000100000000-0000000240000000
May 23 00:18:48 bdt kernel: [    0.000000] NX (Execute Disable) protection: active
May 23 00:18:48 bdt kernel: [    0.000000] RAMDISK: 3728a000 - 37fef9ef
May 23 00:18:48 bdt kernel: [    0.000000] ACPI: RSDP 00000000000fa7a0 00014 (v00 ACPIAM)
May 23 00:18:48 bdt kernel: [    0.000000] ACPI: RSDT 00000000bff90000 00048 (v01 ACRSYS ACRPRDCT 20090818 MSFT 00000097)
May 23 00:18:48 bdt kernel: [    0.000000] ACPI: FACP 00000000bff90200 00084 (v01 081809 FACP1629 20090818 MSFT 00000097)
May 23 00:18:48 bdt kernel: [    0.000000] ACPI: DSDT 00000000bff905c0 06BDB (v01  1AAAA 1AAAA000 00000000 INTL 20051117)
May 23 00:18:48 bdt kernel: [    0.000000] ACPI: FACS 00000000bff9e000 00040
May 23 00:18:48 bdt kernel: [    0.000000] ACPI: APIC 00000000bff90390 0006C (v01 081809 APIC1629 20090818 MSFT 00000097)
May 23 00:18:48 bdt kernel: [    0.000000] ACPI: MCFG 00000000bff90400 0003C (v01 081809 OEMMCFG  20090818 MSFT 00000097)
May 23 00:18:48 bdt kernel: [    0.000000] ACPI: SLIC 00000000bff90440 00176 (v01 ACRSYS ACRPRDCT 20090818 MSFT 00000097)
May 23 00:18:48 bdt kernel: [    0.000000] ACPI: OEMB 00000000bff9e040 00072 (v01 081809 OEMB1629 20090818 MSFT 00000097)
May 23 00:18:48 bdt kernel: [    0.000000] ACPI: HPET 00000000bff985c0 00038 (v01 081809 OEMHPET  20090818 MSFT 00000097)
May 23 00:18:48 bdt kernel: [    0.000000] ACPI: GSCI 00000000bff9e0c0 02024 (v01 081809 GMCHSCI  20090818 MSFT 00000097)
May 23 00:18:48 bdt kernel: [    0.000000] ACPI: AWMI 00000000bffa00f0 0004E (v01 081809 OEMB1629 20090818 MSFT 00000097)
May 23 00:18:48 bdt kernel: [    0.000000] ACPI: SSDT 00000000bffa10b0 00A7C (v01 DpgPmm    CpuPm 00000012 INTL 20051117)
May 23 00:18:48 bdt kernel: [    0.000000] No NUMA configuration found
May 23 00:18:48 bdt kernel: [    0.000000] Faking a node at 0000000000000000-0000000240000000
May 23 00:18:48 bdt kernel: [    0.000000] Bootmem setup node 0 0000000000000000-0000000240000000
May 23 00:18:48 bdt kernel: [    0.000000]   NODE_DATA [0000000000018000 - 000000000001cfff]
May 23 00:18:48 bdt kernel: [    0.000000]   bootmap [000000000001d000 -  0000000000064fff] pages 48
May 23 00:18:48 bdt kernel: [    0.000000] (8 early reservations) ==> bootmem [0000000000 - 0240000000]
May 23 00:18:48 bdt kernel: [    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
May 23 00:18:48 bdt kernel: [    0.000000]   #1 [0000006000 - 0000008000]       TRAMPOLINE ==> [0000006000 - 0000008000]
May 23 00:18:48 bdt kernel: [    0.000000]   #2 [0001000000 - 0001a29e64]    TEXT DATA BSS ==> [0001000000 - 0001a29e64]
May 23 00:18:48 bdt kernel: [    0.000000]   #3 [003728a000 - 0037fef9ef]          RAMDISK ==> [003728a000 - 0037fef9ef]
May 23 00:18:48 bdt kernel: [    0.000000]   #4 [0000095c00 - 0000100000]    BIOS reserved ==> [0000095c00 - 0000100000]
May 23 00:18:48 bdt kernel: [    0.000000]   #5 [0001a2a000 - 0001a2a250]              BRK ==> [0001a2a000 - 0001a2a250]
May 23 00:18:48 bdt kernel: [    0.000000]   #6 [0000010000 - 0000013000]          PGTABLE ==> [0000010000 - 0000013000]
May 23 00:18:48 bdt kernel: [    0.000000]   #7 [0000013000 - 0000018000]          PGTABLE ==> [0000013000 - 0000018000]
May 23 00:18:48 bdt kernel: [    0.000000] found SMP MP-table at [ffff8800000ff780] ff780
May 23 00:18:48 bdt kernel: [    0.000000] Zone PFN ranges:
May 23 00:18:48 bdt kernel: [    0.000000]   DMA      0x00000010 -> 0x00001000
May 23 00:18:48 bdt kernel: [    0.000000]   DMA32    0x00001000 -> 0x00100000
May 23 00:18:48 bdt kernel: [    0.000000]   Normal   0x00100000 -> 0x00240000
May 23 00:18:48 bdt kernel: [    0.000000] Movable zone start PFN for each node
May 23 00:18:48 bdt kernel: [    0.000000] early_node_map[3] active PFN ranges
May 23 00:18:48 bdt kernel: [    0.000000]     0: 0x00000010 -> 0x00000095
May 23 00:18:48 bdt kernel: [    0.000000]     0: 0x00000100 -> 0x000bff90
May 23 00:18:48 bdt kernel: [    0.000000]     0: 0x00100000 -> 0x00240000
May 23 00:18:48 bdt kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x808
May 23 00:18:48 bdt kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
May 23 00:18:48 bdt kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
May 23 00:18:48 bdt kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x02] enabled)
May 23 00:18:48 bdt kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x03] enabled)
May 23 00:18:48 bdt kernel: [    0.000000] ACPI: IOAPIC (id[0x04] address[0xfec00000] gsi_base[0])
May 23 00:18:48 bdt kernel: [    0.000000] IOAPIC[0]: apic_id 4, version 32, address 0xfec00000, GSI 0-23
May 23 00:18:48 bdt kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
May 23 00:18:48 bdt kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
May 23 00:18:48 bdt kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
May 23 00:18:48 bdt kernel: [    0.000000] ACPI: HPET id: 0x8086a301 base: 0xfed00000
May 23 00:18:48 bdt kernel: [    0.000000] SMP: Allowing 4 CPUs, 0 hotplug CPUs
May 23 00:18:48 bdt kernel: [    0.000000] PM: Registered nosave memory: 0000000000095000 - 0000000000096000
May 23 00:18:48 bdt kernel: [    0.000000] PM: Registered nosave memory: 0000000000096000 - 00000000000a0000
May 23 00:18:48 bdt kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e5000
May 23 00:18:48 bdt kernel: [    0.000000] PM: Registered nosave memory: 00000000000e5000 - 0000000000100000
May 23 00:18:48 bdt kernel: [    0.000000] PM: Registered nosave memory: 00000000bff90000 - 00000000bff9e000
May 23 00:18:48 bdt kernel: [    0.000000] PM: Registered nosave memory: 00000000bff9e000 - 00000000bffe0000
May 23 00:18:48 bdt kernel: [    0.000000] PM: Registered nosave memory: 00000000bffe0000 - 00000000c0000000
May 23 00:18:48 bdt kernel: [    0.000000] PM: Registered nosave memory: 00000000c0000000 - 00000000fee00000
May 23 00:18:48 bdt kernel: [    0.000000] PM: Registered nosave memory: 00000000fee00000 - 00000000fee01000
May 23 00:18:48 bdt kernel: [    0.000000] PM: Registered nosave memory: 00000000fee01000 - 00000000ffb00000
May 23 00:18:48 bdt kernel: [    0.000000] PM: Registered nosave memory: 00000000ffb00000 - 0000000100000000
May 23 00:18:48 bdt kernel: [    0.000000] Allocating PCI resources starting at c0000000 (gap: c0000000:3ee00000)
May 23 00:18:48 bdt kernel: [    0.000000] Booting paravirtualized kernel on bare hardware
May 23 00:18:48 bdt kernel: [    0.000000] NR_CPUS:64 nr_cpumask_bits:64 nr_cpu_ids:4 nr_node_ids:1
May 23 00:18:48 bdt kernel: [    0.000000] PERCPU: Embedded 30 pages/cpu @ffff880028200000 s91544 r8192 d23144 u524288
May 23 00:18:48 bdt kernel: [    0.000000] pcpu-alloc: s91544 r8192 d23144 u524288 alloc=1*2097152
May 23 00:18:48 bdt kernel: [    0.000000] pcpu-alloc: [0] 0 1 2 3 
May 23 00:18:48 bdt kernel: [    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 2064544
May 23 00:18:48 bdt kernel: [    0.000000] Policy zone: Normal
May 23 00:18:48 bdt kernel: [    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.32-21-generic root=UUID=426b3181-4dd8-4420-99d5-4b476b5c3b3e ro quiet splash
May 23 00:18:48 bdt kernel: [    0.000000] PID hash table entries: 4096 (order: 3, 32768 bytes)
May 23 00:18:48 bdt kernel: [    0.000000] Initializing CPU#0
May 23 00:18:48 bdt kernel: [    0.000000] xsave/xrstor: enabled xstate_bv 0x3, cntxt size 0x240
May 23 00:18:48 bdt kernel: [    0.000000] Checking aperture...
May 23 00:18:48 bdt kernel: [    0.000000] No AGP bridge found
May 23 00:18:48 bdt kernel: [    0.000000] PCI-DMA: Using software bounce buffering for IO (SWIOTLB)
May 23 00:18:48 bdt kernel: [    0.000000] Placing 64MB software IO TLB between ffff880020000000 - ffff880024000000
May 23 00:18:48 bdt kernel: [    0.000000] software IO TLB at phys 0x20000000 - 0x24000000
May 23 00:18:48 bdt kernel: [    0.000000] Memory: 8182080k/9437184k available (5409k kernel code, 1049516k absent, 205588k reserved, 2976k data, 876k init)
May 23 00:18:48 bdt kernel: [    0.000000] SLUB: Genslabs=14, HWalign=64, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
May 23 00:18:48 bdt kernel: [    0.000000] Hierarchical RCU implementation.
May 23 00:18:48 bdt kernel: [    0.000000] NR_IRQS:4352 nr_irqs:440
May 23 00:18:48 bdt kernel: [    0.000000] Console: colour VGA+ 80x25
May 23 00:18:48 bdt kernel: [    0.000000] console [tty0] enabled
May 23 00:18:48 bdt kernel: [    0.000000] allocated 83886080 bytes of page_cgroup
May 23 00:18:48 bdt kernel: [    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
May 23 00:18:48 bdt kernel: [    0.000000] HPET: 4 timers in total, 0 timers will be used for per-cpu timer
May 23 00:18:48 bdt kernel: [    0.000000] Fast TSC calibration using PIT
May 23 00:18:48 bdt kernel: [    0.000000] Detected 2666.843 MHz processor.
May 23 00:18:48 bdt kernel: [    0.000006] Calibrating delay loop (skipped), value calculated using timer frequency.. 5333.68 BogoMIPS (lpj=26668430)
May 23 00:18:48 bdt kernel: [    0.000029] Security Framework initialized
May 23 00:18:48 bdt kernel: [    0.000045] AppArmor: AppArmor initialized
May 23 00:18:48 bdt kernel: [    0.010320] Dentry cache hash table entries: 1048576 (order: 11, 8388608 bytes)
May 23 00:18:48 bdt kernel: [    0.013464] Inode-cache hash table entries: 524288 (order: 10, 4194304 bytes)
May 23 00:18:48 bdt kernel: [    0.014892] Mount-cache hash table entries: 256
May 23 00:18:48 bdt kernel: [    0.015018] Initializing cgroup subsys ns
May 23 00:18:48 bdt kernel: [    0.015023] Initializing cgroup subsys cpuacct
May 23 00:18:48 bdt kernel: [    0.015026] Initializing cgroup subsys memory
May 23 00:18:48 bdt kernel: [    0.015032] Initializing cgroup subsys devices
May 23 00:18:48 bdt kernel: [    0.015034] Initializing cgroup subsys freezer
May 23 00:18:48 bdt kernel: [    0.015036] Initializing cgroup subsys net_cls
May 23 00:18:48 bdt kernel: [    0.015052] CPU: L1 I cache: 32K, L1 D cache: 32K
May 23 00:18:48 bdt kernel: [    0.015054] CPU: L2 cache: 2048K
May 23 00:18:48 bdt kernel: [    0.015057] CPU 0/0x0 -> Node 0
May 23 00:18:48 bdt kernel: [    0.015059] CPU: Physical Processor ID: 0
May 23 00:18:48 bdt kernel: [    0.015060] CPU: Processor Core ID: 0
May 23 00:18:48 bdt kernel: [    0.015063] mce: CPU supports 6 MCE banks
May 23 00:18:48 bdt kernel: [    0.015070] CPU0: Thermal monitoring enabled (TM2)
May 23 00:18:48 bdt kernel: [    0.015074] using mwait in idle threads.
May 23 00:18:48 bdt kernel: [    0.015075] Performance Events: Core2 events, Intel PMU driver.
May 23 00:18:48 bdt kernel: [    0.015080] ... version:                2
May 23 00:18:48 bdt kernel: [    0.015082] ... bit width:              40
May 23 00:18:48 bdt kernel: [    0.015083] ... generic registers:      2
May 23 00:18:48 bdt kernel: [    0.015084] ... value mask:             000000ffffffffff
May 23 00:18:48 bdt kernel: [    0.015085] ... max period:             000000007fffffff
May 23 00:18:48 bdt kernel: [    0.015087] ... fixed-purpose events:   3
May 23 00:18:48 bdt kernel: [    0.015088] ... event mask:             0000000700000003
May 23 00:18:48 bdt kernel: [    0.017837] ACPI: Core revision 20090903
May 23 00:18:48 bdt kernel: [    0.030006] ftrace: converting mcount calls to 0f 1f 44 00 00
May 23 00:18:48 bdt kernel: [    0.030011] ftrace: allocating 22518 entries in 89 pages
May 23 00:18:48 bdt kernel: [    0.037903] Setting APIC routing to flat
May 23 00:18:48 bdt kernel: [    0.038202] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
May 23 00:18:48 bdt kernel: [    0.138326] CPU0: Intel(R) Core(TM)2 Quad CPU    Q8400  @ 2.66GHz stepping 0a
May 23 00:18:48 bdt kernel: [    0.140000] APIC calibration not consistent with PM-Timer: 109ms instead of 100ms
May 23 00:18:48 bdt kernel: [    0.140000] APIC delta adjusted to PM-Timer: 2083299 (2291627)
May 23 00:18:48 bdt kernel: [    0.140000] Booting processor 1 APIC 0x1 ip 0x6000
May 23 00:18:48 bdt kernel: [    0.010000] Initializing CPU#1
May 23 00:18:48 bdt kernel: [    0.010000] CPU: L1 I cache: 32K, L1 D cache: 32K
May 23 00:18:48 bdt kernel: [    0.010000] CPU: L2 cache: 2048K
May 23 00:18:48 bdt kernel: [    0.010000] CPU 1/0x1 -> Node 0
May 23 00:18:48 bdt kernel: [    0.010000] CPU: Physical Processor ID: 0
May 23 00:18:48 bdt kernel: [    0.010000] CPU: Processor Core ID: 1
May 23 00:18:48 bdt kernel: [    0.010000] CPU1: Thermal monitoring enabled (TM2)
May 23 00:18:48 bdt kernel: [    0.290113] CPU1: Intel(R) Core(TM)2 Quad CPU    Q8400  @ 2.66GHz stepping 0a
May 23 00:18:48 bdt kernel: [    0.290118] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
May 23 00:18:48 bdt kernel: [    0.300091] Booting processor 2 APIC 0x2 ip 0x6000
May 23 00:18:48 bdt kernel: [    0.010000] Initializing CPU#2
May 23 00:18:48 bdt kernel: [    0.010000] CPU: L1 I cache: 32K, L1 D cache: 32K
May 23 00:18:48 bdt kernel: [    0.010000] CPU: L2 cache: 2048K
May 23 00:18:48 bdt kernel: [    0.010000] CPU 2/0x2 -> Node 0
May 23 00:18:48 bdt kernel: [    0.010000] CPU: Physical Processor ID: 0
May 23 00:18:48 bdt kernel: [    0.010000] CPU: Processor Core ID: 2
May 23 00:18:48 bdt kernel: [    0.010000] CPU2: Thermal monitoring enabled (TM2)
May 23 00:18:48 bdt kernel: [    0.460087] CPU2: Intel(R) Core(TM)2 Quad CPU    Q8400  @ 2.66GHz stepping 0a
May 23 00:18:48 bdt kernel: [    0.460093] checking TSC synchronization [CPU#0 -> CPU#2]: passed.
May 23 00:18:48 bdt kernel: [    0.470067] Booting processor 3 APIC 0x3 ip 0x6000
May 23 00:18:48 bdt kernel: [    0.010000] Initializing CPU#3
May 23 00:18:48 bdt kernel: [    0.010000] CPU: L1 I cache: 32K, L1 D cache: 32K
May 23 00:18:48 bdt kernel: [    0.010000] CPU: L2 cache: 2048K
May 23 00:18:48 bdt kernel: [    0.010000] CPU 3/0x3 -> Node 0
May 23 00:18:48 bdt kernel: [    0.010000] CPU: Physical Processor ID: 0
May 23 00:18:48 bdt kernel: [    0.010000] CPU: Processor Core ID: 3
May 23 00:18:48 bdt kernel: [    0.010000] CPU3: Thermal monitoring enabled (TM2)
May 23 00:18:48 bdt kernel: [    0.630074] CPU3: Intel(R) Core(TM)2 Quad CPU    Q8400  @ 2.66GHz stepping 0a
May 23 00:18:48 bdt kernel: [    0.630080] checking TSC synchronization [CPU#0 -> CPU#3]: passed.
May 23 00:18:48 bdt kernel: [    0.640010] Brought up 4 CPUs
May 23 00:18:48 bdt kernel: [    0.640012] Total of 4 processors activated (21333.49 BogoMIPS).
May 23 00:18:48 bdt kernel: [    0.641379] devtmpfs: initialized
May 23 00:18:48 bdt kernel: [    0.641379] regulator: core version 0.5
May 23 00:18:48 bdt kernel: [    0.641379] Time:  0:18:34  Date: 05/23/10
May 23 00:18:48 bdt kernel: [    0.641379] NET: Registered protocol family 16
May 23 00:18:48 bdt kernel: [    0.641379] Trying to unpack rootfs image as initramfs...
May 23 00:18:48 bdt kernel: [    0.641379] ACPI: bus type pci registered
May 23 00:18:48 bdt kernel: [    0.641379] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 255
May 23 00:18:48 bdt kernel: [    0.641379] PCI: Not using MMCONFIG.
May 23 00:18:48 bdt kernel: [    0.641379] PCI: Using configuration type 1 for base access
May 23 00:18:48 bdt kernel: [    0.641379] bio: create slab <bio-0> at 0
May 23 00:18:48 bdt kernel: [    0.644342] ACPI: Executed 1 blocks of module-level executable AML code
May 23 00:18:48 bdt kernel: [    0.652888] ACPI: Interpreter enabled
May 23 00:18:48 bdt kernel: [    0.652891] ACPI: (supports S0 S3 S4 S5)
May 23 00:18:48 bdt kernel: [    0.652906] ACPI: Using IOAPIC for interrupt routing
May 23 00:18:48 bdt kernel: [    0.652953] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 255
May 23 00:18:48 bdt kernel: [    0.658043] PCI: MCFG area at e0000000 reserved in ACPI motherboard resources
May 23 00:18:48 bdt kernel: [    0.664306] PCI: Using MMCONFIG at e0000000 - efffffff
May 23 00:18:48 bdt kernel: [    0.674387] ACPI: No dock devices found.
May 23 00:18:48 bdt kernel: [    0.674656] ACPI: PCI Root Bridge [PCI0] (0000:00)
May 23 00:18:48 bdt kernel: [    0.674740] pci 0000:00:01.0: PME# supported from D0 D3hot D3cold
May 23 00:18:48 bdt kernel: [    0.674742] pci 0000:00:01.0: PME# disabled
May 23 00:18:48 bdt kernel: [    0.674837] pci 0000:00:19.0: PME# supported from D0 D3hot D3cold
May 23 00:18:48 bdt kernel: [    0.674840] pci 0000:00:19.0: PME# disabled
May 23 00:18:48 bdt kernel: [    0.675104] pci 0000:00:1a.7: PME# supported from D0 D3hot D3cold
May 23 00:18:48 bdt kernel: [    0.675108] pci 0000:00:1a.7: PME# disabled
May 23 00:18:48 bdt kernel: [    0.675176] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
May 23 00:18:48 bdt kernel: [    0.675179] pci 0000:00:1b.0: PME# disabled
May 23 00:18:48 bdt kernel: [    0.675230] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
May 23 00:18:48 bdt kernel: [    0.675233] pci 0000:00:1c.0: PME# disabled
May 23 00:18:48 bdt kernel: [    0.675286] pci 0000:00:1c.1: PME# supported from D0 D3hot D3cold
May 23 00:18:48 bdt kernel: [    0.675289] pci 0000:00:1c.1: PME# disabled
May 23 00:18:48 bdt kernel: [    0.675561] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
May 23 00:18:48 bdt kernel: [    0.675565] pci 0000:00:1d.7: PME# disabled
May 23 00:18:48 bdt kernel: [    0.675671] pci 0000:00:1f.0: quirk: region 0800-087f claimed by ICH6 ACPI/GPIO/TCO
May 23 00:18:48 bdt kernel: [    0.675674] pci 0000:00:1f.0: quirk: region 0480-04bf claimed by ICH6 GPIO
May 23 00:18:48 bdt kernel: [    0.675677] pci 0000:00:1f.0: ICH7 LPC Generic IO decode 1 PIO at 0a00 (mask 00ff)
May 23 00:18:48 bdt kernel: [    0.675779] pci 0000:00:1f.2: PME# supported from D3hot
May 23 00:18:48 bdt kernel: [    0.675782] pci 0000:00:1f.2: PME# disabled
May 23 00:18:48 bdt kernel: [    0.676116] pci 0000:02:00.0: PME# supported from D0 D1 D2 D3hot
May 23 00:18:48 bdt kernel: [    0.676121] pci 0000:02:00.0: PME# disabled
May 23 00:18:48 bdt kernel: [    0.676278] pci 0000:03:00.0: PME# supported from D2 D3hot D3cold
May 23 00:18:48 bdt kernel: [    0.676283] pci 0000:03:00.0: PME# disabled
May 23 00:18:48 bdt kernel: [    0.676443] pci 0000:00:1e.0: transparent bridge
May 23 00:18:48 bdt kernel: [    0.691649] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 6 7 *10 11 12 14 15)
May 23 00:18:48 bdt kernel: [    0.691753] ACPI: PCI Interrupt Link [LNKB] (IRQs *5)
May 23 00:18:48 bdt kernel: [    0.691853] ACPI: PCI Interrupt Link [LNKC] (IRQs *3 4 6 7 10 11 12 14 15)
May 23 00:18:48 bdt kernel: [    0.691956] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 6 7 10 *11 12 14 15)
May 23 00:18:48 bdt kernel: [    0.692059] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 6 7 10 11 12 14 *15)
May 23 00:18:48 bdt kernel: [    0.692161] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 6 7 10 11 12 *14 15)
May 23 00:18:48 bdt kernel: [    0.692263] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 6 *7 10 11 12 14 15)
May 23 00:18:48 bdt kernel: [    0.692366] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 *4 6 7 10 11 12 14 15)
May 23 00:18:48 bdt kernel: [    0.692465] vgaarb: device added: PCI:0000:01:00.0,decodes=io+mem,owns=io+mem,locks=none
May 23 00:18:48 bdt kernel: [    0.692468] vgaarb: loaded
May 23 00:18:48 bdt kernel: [    0.692558] SCSI subsystem initialized
May 23 00:18:48 bdt kernel: [    0.692593] usbcore: registered new interface driver usbfs
May 23 00:18:48 bdt kernel: [    0.692593] usbcore: registered new interface driver hub
May 23 00:18:48 bdt kernel: [    0.692593] usbcore: registered new device driver usb
May 23 00:18:48 bdt kernel: [    0.692593] ACPI: WMI: Mapper loaded
May 23 00:18:48 bdt kernel: [    0.692593] PCI: Using ACPI for IRQ routing
May 23 00:18:48 bdt kernel: [    0.692593] NetLabel: Initializing
May 23 00:18:48 bdt kernel: [    0.692593] NetLabel:  domain hash size = 128
May 23 00:18:48 bdt kernel: [    0.692593] NetLabel:  protocols = UNLABELED CIPSOv4
May 23 00:18:48 bdt kernel: [    0.692593] NetLabel:  unlabeled traffic allowed by default
May 23 00:18:48 bdt kernel: [    0.692593] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0
May 23 00:18:48 bdt kernel: [    0.692593] hpet0: 4 comparators, 64-bit 14.318180 MHz counter
May 23 00:18:48 bdt kernel: [    0.720030] Switching to clocksource tsc
May 23 00:18:48 bdt kernel: [    0.721655] AppArmor: AppArmor Filesystem Enabled
May 23 00:18:48 bdt kernel: [    0.721673] pnp: PnP ACPI init
May 23 00:18:48 bdt kernel: [    0.721693] ACPI: bus type pnp registered
May 23 00:18:48 bdt kernel: [    0.725660] pnp: PnP ACPI: found 16 devices
May 23 00:18:48 bdt kernel: [    0.725662] ACPI: ACPI bus type pnp unregistered
May 23 00:18:48 bdt kernel: [    0.725675] system 00:01: iomem range 0xfed14000-0xfed19fff has been reserved
May 23 00:18:48 bdt kernel: [    0.725678] system 00:01: iomem range 0xfed90000-0xfed93fff has been reserved
May 23 00:18:48 bdt kernel: [    0.725684] system 00:08: ioport range 0xa00-0xa0f has been reserved
May 23 00:18:48 bdt kernel: [    0.725687] system 00:08: ioport range 0xa10-0xa1f has been reserved
May 23 00:18:48 bdt kernel: [    0.725689] system 00:08: ioport range 0xa20-0xa2f has been reserved
May 23 00:18:48 bdt kernel: [    0.725691] system 00:08: ioport range 0xa30-0xa3f has been reserved
May 23 00:18:48 bdt kernel: [    0.725695] system 00:09: ioport range 0x4d0-0x4d1 has been reserved
May 23 00:18:48 bdt kernel: [    0.725697] system 00:09: ioport range 0x4c0-0x4cf has been reserved
May 23 00:18:48 bdt kernel: [    0.725699] system 00:09: ioport range 0x4d2-0x4ff has been reserved
May 23 00:18:48 bdt kernel: [    0.725701] system 00:09: ioport range 0x800-0x87f has been reserved
May 23 00:18:48 bdt kernel: [    0.725703] system 00:09: ioport range 0x480-0x4bf has been reserved
May 23 00:18:48 bdt kernel: [    0.725706] system 00:09: iomem range 0xfed1c000-0xfed1ffff has been reserved
May 23 00:18:48 bdt kernel: [    0.725708] system 00:09: iomem range 0xfed20000-0xfed3ffff has been reserved
May 23 00:18:48 bdt kernel: [    0.725710] system 00:09: iomem range 0xfed40000-0xfed8ffff has been reserved
May 23 00:18:48 bdt kernel: [    0.725715] system 00:0c: iomem range 0xffc00000-0xffefffff has been reserved
May 23 00:18:48 bdt kernel: [    0.725719] system 00:0d: iomem range 0xfec00000-0xfec00fff could not be reserved
May 23 00:18:48 bdt kernel: [    0.725721] system 00:0d: iomem range 0xfee00000-0xfee00fff has been reserved
May 23 00:18:48 bdt kernel: [    0.725725] system 00:0e: iomem range 0xe0000000-0xefffffff has been reserved
May 23 00:18:48 bdt kernel: [    0.725729] system 00:0f: iomem range 0x0-0x9ffff could not be reserved
May 23 00:18:48 bdt kernel: [    0.725732] system 00:0f: iomem range 0xc0000-0xcffff has been reserved
May 23 00:18:48 bdt kernel: [    0.725734] system 00:0f: iomem range 0xe0000-0xfffff could not be reserved
May 23 00:18:48 bdt kernel: [    0.725736] system 00:0f: iomem range 0x100000-0xbfffffff could not be reserved
May 23 00:18:48 bdt kernel: [    0.725738] system 00:0f: iomem range 0xfed90000-0xffffffff could not be reserved
May 23 00:18:48 bdt kernel: [    0.730462] pci 0000:00:01.0: PCI bridge, secondary bus 0000:01
May 23 00:18:48 bdt kernel: [    0.730464] pci 0000:00:01.0:   IO window: 0xd000-0xdfff
May 23 00:18:48 bdt kernel: [    0.730467] pci 0000:00:01.0:   MEM window: 0xfd000000-0xfe7fffff
May 23 00:18:48 bdt kernel: [    0.730470] pci 0000:00:01.0:   PREFETCH window: 0x000000ce000000-0x000000dfffffff
May 23 00:18:48 bdt kernel: [    0.730473] pci 0000:00:1c.0: PCI bridge, secondary bus 0000:02
May 23 00:18:48 bdt kernel: [    0.730476] pci 0000:00:1c.0:   IO window: 0x1000-0x1fff
May 23 00:18:48 bdt kernel: [    0.730480] pci 0000:00:1c.0:   MEM window: 0xfe800000-0xfe9fffff
May 23 00:18:48 bdt kernel: [    0.730483] pci 0000:00:1c.0:   PREFETCH window: 0x000000c0000000-0x000000c01fffff
May 23 00:18:48 bdt kernel: [    0.730487] pci 0000:00:1c.1: PCI bridge, secondary bus 0000:03
May 23 00:18:48 bdt kernel: [    0.730490] pci 0000:00:1c.1:   IO window: 0xe000-0xefff
May 23 00:18:48 bdt kernel: [    0.730493] pci 0000:00:1c.1:   MEM window: 0xfea00000-0xfeafffff
May 23 00:18:48 bdt kernel: [    0.730497] pci 0000:00:1c.1:   PREFETCH window: 0x000000c0200000-0x000000c03fffff
May 23 00:18:48 bdt kernel: [    0.730501] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:04
May 23 00:18:48 bdt kernel: [    0.730503] pci 0000:00:1e.0:   IO window: disabled
May 23 00:18:48 bdt kernel: [    0.730506] pci 0000:00:1e.0:   MEM window: 0xfeb00000-0xfebfffff
May 23 00:18:48 bdt kernel: [    0.730509] pci 0000:00:1e.0:   PREFETCH window: disabled
May 23 00:18:48 bdt kernel: [    0.730528] pci 0000:00:01.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
May 23 00:18:48 bdt kernel: [    0.730537] pci 0000:00:1c.0: enabling device (0106 -> 0107)
May 23 00:18:48 bdt kernel: [    0.730543] pci 0000:00:1c.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
May 23 00:18:48 bdt kernel: [    0.730553] pci 0000:00:1c.1: PCI INT B -> GSI 16 (level, low) -> IRQ 16
May 23 00:18:48 bdt kernel: [    0.730622] NET: Registered protocol family 2
May 23 00:18:48 bdt kernel: [    0.730828] IP route cache hash table entries: 262144 (order: 9, 2097152 bytes)
May 23 00:18:48 bdt kernel: [    0.732045] TCP established hash table entries: 524288 (order: 11, 8388608 bytes)
May 23 00:18:48 bdt kernel: [    0.735375] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
May 23 00:18:48 bdt kernel: [    0.735756] TCP: Hash tables configured (established 524288 bind 65536)
May 23 00:18:48 bdt kernel: [    0.735758] TCP reno registered
May 23 00:18:48 bdt kernel: [    0.735866] NET: Registered protocol family 1
May 23 00:18:48 bdt kernel: [    0.736337] Scanning for low memory corruption every 60 seconds
May 23 00:18:48 bdt kernel: [    0.736449] audit: initializing netlink socket (disabled)
May 23 00:18:48 bdt kernel: [    0.736458] type=2000 audit(1274573913.729:1): initialized
May 23 00:18:48 bdt kernel: [    0.744184] HugeTLB registered 2 MB page size, pre-allocated 0 pages
May 23 00:18:48 bdt kernel: [    0.745382] VFS: Disk quotas dquot_6.5.2
May 23 00:18:48 bdt kernel: [    0.745428] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
May 23 00:18:48 bdt kernel: [    0.745912] fuse init (API version 7.13)
May 23 00:18:48 bdt kernel: [    0.745973] msgmni has been set to 15980
May 23 00:18:48 bdt kernel: [    0.746269] alg: No test for stdrng (krng)
May 23 00:18:48 bdt kernel: [    0.746313] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
May 23 00:18:48 bdt kernel: [    0.746316] io scheduler noop registered
May 23 00:18:48 bdt kernel: [    0.746317] io scheduler anticipatory registered
May 23 00:18:48 bdt kernel: [    0.746319] io scheduler deadline registered
May 23 00:18:48 bdt kernel: [    0.746346] io scheduler cfq registered (default)
May 23 00:18:48 bdt kernel: [    0.746724] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
May 23 00:18:48 bdt kernel: [    0.746795] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
May 23 00:18:48 bdt kernel: [    0.746897] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0
May 23 00:18:48 bdt kernel: [    0.746906] ACPI: Power Button [PWRB]
May 23 00:18:48 bdt kernel: [    0.746941] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
May 23 00:18:48 bdt kernel: [    0.746943] ACPI: Power Button [PWRF]
May 23 00:18:48 bdt kernel: [    0.747551] ACPI: SSDT 00000000bffa0140 00235 (v01 DpgPmm  P001Ist 00000011 INTL 20051117)
May 23 00:18:48 bdt kernel: [    0.747937] ACPI: SSDT 00000000bffa0a40 004B2 (v01  PmRef  P001Cst 00003001 INTL 20051117)
May 23 00:18:48 bdt kernel: [    0.748298] Marking TSC unstable due to TSC halts in idle
May 23 00:18:48 bdt kernel: [    0.748362] Switching to clocksource hpet
May 23 00:18:48 bdt kernel: [    0.748373] processor LNXCPU:00: registered as cooling_device0
May 23 00:18:48 bdt kernel: [    0.748949] ACPI: SSDT 00000000bffa0380 00235 (v01 DpgPmm  P002Ist 00000012 INTL 20051117)
May 23 00:18:48 bdt kernel: [    0.749225] ACPI: SSDT 00000000bffa0f00 00085 (v01  PmRef  P002Cst 00003000 INTL 20051117)
May 23 00:18:48 bdt kernel: [    0.749634] processor LNXCPU:01: registered as cooling_device1
May 23 00:18:48 bdt kernel: [    0.749994] ACPI: SSDT 00000000bffa05c0 00235 (v01 DpgPmm  P003Ist 00000012 INTL 20051117)
May 23 00:18:48 bdt kernel: [    0.750294] ACPI: SSDT 00000000bffa0f90 00085 (v01  PmRef  P003Cst 00003000 INTL 20051117)
May 23 00:18:48 bdt kernel: [    0.750699] processor LNXCPU:02: registered as cooling_device2
May 23 00:18:48 bdt kernel: [    0.751051] ACPI: SSDT 00000000bffa0800 00235 (v01 DpgPmm  P004Ist 00000012 INTL 20051117)
May 23 00:18:48 bdt kernel: [    0.751343] ACPI: SSDT 00000000bffa1020 00085 (v01  PmRef  P004Cst 00003000 INTL 20051117)
May 23 00:18:48 bdt kernel: [    0.764053] processor LNXCPU:03: registered as cooling_device3
May 23 00:18:48 bdt kernel: [    0.769993] Linux agpgart interface v0.103
May 23 00:18:48 bdt kernel: [    0.770035] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
May 23 00:18:48 bdt kernel: [    0.771037] brd: module loaded
May 23 00:18:48 bdt kernel: [    0.771396] loop: module loaded
May 23 00:18:48 bdt kernel: [    0.771462] input: Macintosh mouse button emulation as /devices/virtual/input/input2
May 23 00:18:48 bdt kernel: [    0.771768] Fixed MDIO Bus: probed
May 23 00:18:48 bdt kernel: [    0.771792] PPP generic driver version 2.4.2
May 23 00:18:48 bdt kernel: [    0.771814] tun: Universal TUN/TAP device driver, 1.6
May 23 00:18:48 bdt kernel: [    0.771816] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
May 23 00:18:48 bdt kernel: [    0.771873] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
May 23 00:18:48 bdt kernel: [    0.771900] ehci_hcd 0000:00:1a.7: PCI INT C -> GSI 18 (level, low) -> IRQ 18
May 23 00:18:48 bdt kernel: [    0.771933] ehci_hcd 0000:00:1a.7: EHCI Host Controller
May 23 00:18:48 bdt kernel: [    0.771965] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 1
May 23 00:18:48 bdt kernel: [    0.771991] ehci_hcd 0000:00:1a.7: debug port 1
May 23 00:18:48 bdt kernel: [    0.775896] ehci_hcd 0000:00:1a.7: irq 18, io mem 0xfcfdec00
May 23 00:18:48 bdt kernel: [    0.792520] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00
May 23 00:18:48 bdt kernel: [    0.792626] usb usb1: configuration #1 chosen from 1 choice
May 23 00:18:48 bdt kernel: [    0.792649] hub 1-0:1.0: USB hub found
May 23 00:18:48 bdt kernel: [    0.792657] hub 1-0:1.0: 6 ports detected
May 23 00:18:48 bdt kernel: [    0.792723] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
May 23 00:18:48 bdt kernel: [    0.792744] ehci_hcd 0000:00:1d.7: EHCI Host Controller
May 23 00:18:48 bdt kernel: [    0.792772] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 2
May 23 00:18:48 bdt kernel: [    0.792795] ehci_hcd 0000:00:1d.7: debug port 1
May 23 00:18:48 bdt kernel: [    0.796678] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xfcfde800
May 23 00:18:48 bdt kernel: [    0.812518] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
May 23 00:18:48 bdt kernel: [    0.812634] usb usb2: configuration #1 chosen from 1 choice
May 23 00:18:48 bdt kernel: [    0.812658] hub 2-0:1.0: USB hub found
May 23 00:18:48 bdt kernel: [    0.812665] hub 2-0:1.0: 6 ports detected
May 23 00:18:48 bdt kernel: [    0.812718] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
May 23 00:18:48 bdt kernel: [    0.812733] uhci_hcd: USB Universal Host Controller Interface driver
May 23 00:18:48 bdt kernel: [    0.812768] uhci_hcd 0000:00:1a.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
May 23 00:18:48 bdt kernel: [    0.812778] uhci_hcd 0000:00:1a.0: UHCI Host Controller
May 23 00:18:48 bdt kernel: [    0.812810] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 3
May 23 00:18:48 bdt kernel: [    0.812842] uhci_hcd 0000:00:1a.0: irq 16, io base 0x0000c880
May 23 00:18:48 bdt kernel: [    0.812915] usb usb3: configuration #1 chosen from 1 choice
May 23 00:18:48 bdt kernel: [    0.812932] hub 3-0:1.0: USB hub found
May 23 00:18:48 bdt kernel: [    0.812939] hub 3-0:1.0: 2 ports detected
May 23 00:18:48 bdt kernel: [    0.812981] uhci_hcd 0000:00:1a.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
May 23 00:18:48 bdt kernel: [    0.812988] uhci_hcd 0000:00:1a.1: UHCI Host Controller
May 23 00:18:48 bdt kernel: [    0.813012] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 4
May 23 00:18:48 bdt kernel: [    0.813039] uhci_hcd 0000:00:1a.1: irq 21, io base 0x0000c800
May 23 00:18:48 bdt kernel: [    0.813102] usb usb4: configuration #1 chosen from 1 choice
May 23 00:18:48 bdt kernel: [    0.813120] hub 4-0:1.0: USB hub found
May 23 00:18:48 bdt kernel: [    0.813124] hub 4-0:1.0: 2 ports detected
May 23 00:18:48 bdt kernel: [    0.813162] uhci_hcd 0000:00:1a.2: PCI INT D -> GSI 19 (level, low) -> IRQ 19
May 23 00:18:48 bdt kernel: [    0.813168] uhci_hcd 0000:00:1a.2: UHCI Host Controller
May 23 00:18:48 bdt kernel: [    0.813193] uhci_hcd 0000:00:1a.2: new USB bus registered, assigned bus number 5
May 23 00:18:48 bdt kernel: [    0.813218] uhci_hcd 0000:00:1a.2: irq 19, io base 0x0000c480
May 23 00:18:48 bdt kernel: [    0.813279] usb usb5: configuration #1 chosen from 1 choice
May 23 00:18:48 bdt kernel: [    0.813300] hub 5-0:1.0: USB hub found
May 23 00:18:48 bdt kernel: [    0.813305] hub 5-0:1.0: 2 ports detected
May 23 00:18:48 bdt kernel: [    0.813338] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
May 23 00:18:48 bdt kernel: [    0.813345] uhci_hcd 0000:00:1d.0: UHCI Host Controller
May 23 00:18:48 bdt kernel: [    0.813371] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 6
May 23 00:18:48 bdt kernel: [    0.813390] uhci_hcd 0000:00:1d.0: irq 23, io base 0x0000c400
May 23 00:18:48 bdt kernel: [    0.813449] usb usb6: configuration #1 chosen from 1 choice
May 23 00:18:48 bdt kernel: [    0.813470] hub 6-0:1.0: USB hub found
May 23 00:18:48 bdt kernel: [    0.813474] hub 6-0:1.0: 2 ports detected
May 23 00:18:48 bdt kernel: [    0.813508] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
May 23 00:18:48 bdt kernel: [    0.813514] uhci_hcd 0000:00:1d.1: UHCI Host Controller
May 23 00:18:48 bdt kernel: [    0.813537] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 7
May 23 00:18:48 bdt kernel: [    0.813556] uhci_hcd 0000:00:1d.1: irq 19, io base 0x0000c080
May 23 00:18:48 bdt kernel: [    0.813622] usb usb7: configuration #1 chosen from 1 choice
May 23 00:18:48 bdt kernel: [    0.813639] hub 7-0:1.0: USB hub found
May 23 00:18:48 bdt kernel: [    0.813644] hub 7-0:1.0: 2 ports detected
May 23 00:18:48 bdt kernel: [    0.813678] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
May 23 00:18:48 bdt kernel: [    0.813685] uhci_hcd 0000:00:1d.2: UHCI Host Controller
May 23 00:18:48 bdt kernel: [    0.813708] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 8
May 23 00:18:48 bdt kernel: [    0.813730] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000c000
May 23 00:18:48 bdt kernel: [    0.813793] usb usb8: configuration #1 chosen from 1 choice
May 23 00:18:48 bdt kernel: [    0.813812] hub 8-0:1.0: USB hub found
May 23 00:18:48 bdt kernel: [    0.813818] hub 8-0:1.0: 2 ports detected
May 23 00:18:48 bdt kernel: [    0.813891] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f03:PS2M] at 0x60,0x64 irq 1,12
May 23 00:18:48 bdt kernel: [    0.814247] serio: i8042 KBD port at 0x60,0x64 irq 1
May 23 00:18:48 bdt kernel: [    0.814252] serio: i8042 AUX port at 0x60,0x64 irq 12
May 23 00:18:48 bdt kernel: [    0.814339] mice: PS/2 mouse device common for all mice
May 23 00:18:48 bdt kernel: [    0.814421] rtc_cmos 00:03: RTC can wake from S4
May 23 00:18:48 bdt kernel: [    0.814451] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0
May 23 00:18:48 bdt kernel: [    0.814471] rtc0: alarms up to one month, y3k, 114 bytes nvram, hpet irqs
May 23 00:18:48 bdt kernel: [    0.814576] device-mapper: uevent: version 1.0.3
May 23 00:18:48 bdt kernel: [    0.814666] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: [email]dm-devel@redhat.com[/email]
May 23 00:18:48 bdt kernel: [    0.814814] device-mapper: multipath: version 1.1.0 loaded
May 23 00:18:48 bdt kernel: [    0.814816] device-mapper: multipath round-robin: version 1.0.0 loaded
May 23 00:18:48 bdt kernel: [    0.815137] cpuidle: using governor ladder
May 23 00:18:48 bdt kernel: [    0.815259] cpuidle: using governor menu
May 23 00:18:48 bdt kernel: [    0.815509] TCP cubic registered
May 23 00:18:48 bdt kernel: [    0.815607] NET: Registered protocol family 10
May 23 00:18:48 bdt kernel: [    0.815932] lo: Disabled Privacy Extensions
May 23 00:18:48 bdt kernel: [    0.816137] NET: Registered protocol family 17
May 23 00:18:48 bdt kernel: [    0.817058] registered taskstats version 1
May 23 00:18:48 bdt kernel: [    0.817414]   Magic number: 10:987:304
May 23 00:18:48 bdt kernel: [    0.817438] tty tty33: hash matches
May 23 00:18:48 bdt kernel: [    0.817497] rtc_cmos 00:03: setting system clock to 2010-05-23 00:18:34 UTC (1274573914)
May 23 00:18:48 bdt kernel: [    0.817499] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
May 23 00:18:48 bdt kernel: [    0.817500] EDD information not available.
May 23 00:18:48 bdt kernel: [    0.834982] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3
May 23 00:18:48 bdt kernel: [    0.872816] Freeing initrd memory: 13718k freed
May 23 00:18:48 bdt kernel: [    0.876714] Freeing unused kernel memory: 876k freed
May 23 00:18:48 bdt kernel: [    0.876898] Write protecting the kernel read-only data: 7680k
May 23 00:18:48 bdt kernel: [    0.891043] udev: starting version 151
May 23 00:18:48 bdt kernel: [    0.930772] ahci 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
May 23 00:18:48 bdt kernel: [    0.930843] ahci 0000:00:1f.2: controller can't do SNTF, turning off CAP_SNTF
May 23 00:18:48 bdt kernel: [    0.930888] ahci: SSS flag set, parallel bus scan disabled
May 23 00:18:48 bdt kernel: [    0.930922] ahci 0000:00:1f.2: AHCI 0001.0200 32 slots 6 ports 3 Gbps 0x3f impl RAID mode
May 23 00:18:48 bdt kernel: [    0.930925] ahci 0000:00:1f.2: flags: 64bit ncq stag pm led clo pio slum part ccc ems sxs 
May 23 00:18:48 bdt kernel: [    0.934262] e1000e: Intel(R) PRO/1000 Network Driver - 1.0.2-k2
May 23 00:18:48 bdt kernel: [    0.934264] e1000e: Copyright (c) 1999-2008 Intel Corporation.
May 23 00:18:48 bdt kernel: [    0.948782] [drm] Initialized drm 1.1.0 20060810
May 23 00:18:48 bdt kernel: [    0.965129] ohci1394 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
May 23 00:18:48 bdt kernel: [    0.975583] nouveau 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
May 23 00:18:48 bdt kernel: [    0.977800] [drm] nouveau 0000:01:00.0: Detected an NV50 generation card (0x0a5000a2)
May 23 00:18:48 bdt kernel: [    0.978559] [drm] nouveau 0000:01:00.0: Attempting to load BIOS image from PRAMIN
May 23 00:18:48 bdt kernel: [    1.021355] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[17]  MMIO=[feaff800-feafffff]  Max Packet=[2048]  IR/IT contexts=[4/8]
May 23 00:18:48 bdt kernel: [    1.023891] scsi0 : ahci
May 23 00:18:48 bdt kernel: [    1.024047] scsi1 : ahci
May 23 00:18:48 bdt kernel: [    1.024131] scsi2 : ahci
May 23 00:18:48 bdt kernel: [    1.024217] scsi3 : ahci
May 23 00:18:48 bdt kernel: [    1.024299] scsi4 : ahci
May 23 00:18:48 bdt kernel: [    1.024382] scsi5 : ahci
May 23 00:18:48 bdt kernel: [    1.024533] ata1: SATA max UDMA/133 abar m2048@0xfcfde000 port 0xfcfde100 irq 27
May 23 00:18:48 bdt kernel: [    1.024537] ata2: SATA max UDMA/133 abar m2048@0xfcfde000 port 0xfcfde180 irq 27
May 23 00:18:48 bdt kernel: [    1.024539] ata3: SATA max UDMA/133 abar m2048@0xfcfde000 port 0xfcfde200 irq 27
May 23 00:18:48 bdt kernel: [    1.024542] ata4: SATA max UDMA/133 abar m2048@0xfcfde000 port 0xfcfde280 irq 27
May 23 00:18:48 bdt kernel: [    1.024544] ata5: SATA max UDMA/133 abar m2048@0xfcfde000 port 0xfcfde300 irq 27
May 23 00:18:48 bdt kernel: [    1.024546] ata6: SATA max UDMA/133 abar m2048@0xfcfde000 port 0xfcfde380 irq 27
May 23 00:18:48 bdt kernel: [    1.024672] e1000e 0000:00:19.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
May 23 00:18:48 bdt kernel: [    1.045526] [drm] nouveau 0000:01:00.0: ... appears to be valid
May 23 00:18:48 bdt kernel: [    1.045529] [drm] nouveau 0000:01:00.0: BIT BIOS found
May 23 00:18:48 bdt kernel: [    1.045531] [drm] nouveau 0000:01:00.0: Bios version 70.16.0e.00
May 23 00:18:48 bdt kernel: [    1.045536] [drm] nouveau 0000:01:00.0: TMDS table revision 2.0 not currently supported
May 23 00:18:48 bdt kernel: [    1.045538] [drm] nouveau 0000:01:00.0: Found Display Configuration Block version 4.0
May 23 00:18:48 bdt kernel: [    1.045540] [drm] nouveau 0000:01:00.0: DCB connector table: VHER 0x40 5 16 4
May 23 00:18:48 bdt kernel: [    1.045543] [drm] nouveau 0000:01:00.0:   0: 0x00001030: type 0x30 idx 0 tag 0x07
May 23 00:18:48 bdt kernel: [    1.045545] [drm] nouveau 0000:01:00.0:   1: 0x00002161: type 0x61 idx 1 tag 0x08
May 23 00:18:48 bdt kernel: [    1.045547] [drm] nouveau 0000:01:00.0:   2: 0x00000200: type 0x00 idx 2 tag 0xff
May 23 00:18:48 bdt kernel: [    1.045549] [drm] nouveau 0000:01:00.0: Raw DCB entry 0: 02000300 00000000
May 23 00:18:48 bdt kernel: [    1.045551] [drm] nouveau 0000:01:00.0: Raw DCB entry 1: 01000302 00020030
May 23 00:18:48 bdt kernel: [    1.045553] [drm] nouveau 0000:01:00.0: Raw DCB entry 2: 01032310 00000000
May 23 00:18:48 bdt kernel: [    1.045554] [drm] nouveau 0000:01:00.0: Raw DCB entry 3: 02021362 00020010
May 23 00:18:48 bdt kernel: [    1.045562] [drm] nouveau 0000:01:00.0: Parsing VBIOS init table 0 at offset 0xCED3
May 23 00:18:48 bdt kernel: [    1.092534] [drm] nouveau 0000:01:00.0: 0xD1E3: Condition still not met after 20ms, skipping following opcodes
May 23 00:18:48 bdt kernel: [    1.122546] [drm] nouveau 0000:01:00.0: 0xD20E: Condition still not met after 20ms, skipping following opcodes
May 23 00:18:48 bdt kernel: [    1.122559] [drm] nouveau 0000:01:00.0: Parsing VBIOS init table 1 at offset 0xD38A
May 23 00:18:48 bdt kernel: [    1.162435] 0000:00:19.0: eth0: (PCI Express:2.5GB/s:Width x1) 00:25:11:59:d4:ca
May 23 00:18:48 bdt kernel: [    1.162437] 0000:00:19.0: eth0: Intel(R) PRO/1000 Network Connection
May 23 00:18:48 bdt kernel: [    1.162456] 0000:00:19.0: eth0: MAC: 7, PHY: 8, PBA No: ffffff-0ff
May 23 00:18:48 bdt kernel: [    1.180228] [drm] nouveau 0000:01:00.0: Parsing VBIOS init table 2 at offset 0xE221
May 23 00:18:48 bdt kernel: [    1.180235] [drm] nouveau 0000:01:00.0: Parsing VBIOS init table 3 at offset 0xE25F
May 23 00:18:48 bdt kernel: [    1.241581] [drm] nouveau 0000:01:00.0: Parsing VBIOS init table 4 at offset 0xE43E
May 23 00:18:48 bdt kernel: [    1.241583] [drm] nouveau 0000:01:00.0: Parsing VBIOS init table at offset 0xE4A3
May 23 00:18:48 bdt kernel: [    1.241601] usb 2-4: new high speed USB device using ehci_hcd and address 2
May 23 00:18:48 bdt kernel: [    1.270036] [drm] nouveau 0000:01:00.0: 0xE4A3: Condition still not met after 20ms, skipping following opcodes
May 23 00:18:48 bdt kernel: [    1.270042] [drm] nouveau 0000:01:00.0: 0xBB95: parsing output script 0
May 23 00:18:48 bdt kernel: [    1.270045] [drm] nouveau 0000:01:00.0: 0xBB95: parsing output script 0
May 23 00:18:48 bdt kernel: [    1.370062] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
May 23 00:18:48 bdt kernel: [    1.392191] usb 2-4: configuration #1 chosen from 1 choice
May 23 00:18:48 bdt kernel: [    1.397560] ata1.00: ATA-8: WDC WD10EADS-22M2B0, 01.00A01, max UDMA/133
May 23 00:18:48 bdt kernel: [    1.397563] ata1.00: 1953525168 sectors, multi 0: LBA48 NCQ (depth 31/32), AA
May 23 00:18:48 bdt kernel: [    1.397621] Initializing USB Mass Storage driver...
May 23 00:18:48 bdt kernel: [    1.397789] scsi6 : SCSI emulation for USB Mass Storage devices
May 23 00:18:48 bdt kernel: [    1.397936] usbcore: registered new interface driver usb-storage
May 23 00:18:48 bdt kernel: [    1.397998] USB Mass Storage support registered.
May 23 00:18:48 bdt kernel: [    1.399371] ata1.00: configured for UDMA/133
May 23 00:18:48 bdt kernel: [    1.404640] [TTM] Zone  kernel: Available graphics memory: 4098338 kiB.
May 23 00:18:48 bdt kernel: [    1.404642] [TTM] Zone   dma32: Available graphics memory: 2097152 kiB.
May 23 00:18:48 bdt kernel: [    1.404652] [drm] nouveau 0000:01:00.0: 1024 MiB VRAM
May 23 00:18:48 bdt kernel: [    1.410121] scsi 0:0:0:0: Direct-Access     ATA      WDC WD10EADS-22M 01.0 PQ: 0 ANSI: 5
May 23 00:18:48 bdt kernel: [    1.410276] sd 0:0:0:0: Attached scsi generic sg0 type 0
May 23 00:18:48 bdt kernel: [    1.410312] sd 0:0:0:0: [sda] 1953525168 512-byte logical blocks: (1.00 TB/931 GiB)
May 23 00:18:48 bdt kernel: [    1.410366] sd 0:0:0:0: [sda] Write Protect is off
May 23 00:18:48 bdt kernel: [    1.410386] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
May 23 00:18:48 bdt kernel: [    1.410503]  sda: sda1 sda2 sda3
May 23 00:18:48 bdt kernel: [    1.417987] sd 0:0:0:0: [sda] Attached SCSI disk
May 23 00:18:48 bdt kernel: [    1.419229] [drm] nouveau 0000:01:00.0: 512 MiB GART (aperture)
May 23 00:18:48 bdt kernel: [    1.419236] mtrr: type mismatch for d0000000,10000000 old: write-back new: write-combining
May 23 00:18:48 bdt kernel: [    1.419422] [drm] nouveau 0000:01:00.0: Allocating FIFO number 1
May 23 00:18:48 bdt kernel: [    1.422417] [drm] nouveau 0000:01:00.0: nouveau_channel_alloc: initialised FIFO 1
May 23 00:18:48 bdt kernel: [    1.422963] [drm] nouveau 0000:01:00.0: Detected a DAC output
May 23 00:18:48 bdt kernel: [    1.422970] [drm] nouveau 0000:01:00.0: Detected a TMDS output
May 23 00:18:48 bdt kernel: [    1.422972] [drm] nouveau 0000:01:00.0: Detected a DAC output
May 23 00:18:48 bdt kernel: [    1.422973] [drm] nouveau 0000:01:00.0: Detected a TMDS output
May 23 00:18:48 bdt kernel: [    1.422976] [drm] nouveau 0000:01:00.0: Detected a DVI-I connector
May 23 00:18:48 bdt kernel: [    1.423014] [drm] nouveau 0000:01:00.0: Detected a VGA connector
May 23 00:18:48 bdt kernel: [    1.423034] [drm] nouveau 0000:01:00.0: Detected a DVI-D connector
May 23 00:18:48 bdt kernel: [    1.670031] usb 4-2: new low speed USB device using uhci_hcd and address 2
May 23 00:18:48 bdt kernel: [    1.750249] [drm] nouveau 0000:01:00.0: allocated 1280x1024 fb: 0x40250000, bo ffff880231cdd600
May 23 00:18:48 bdt kernel: [    1.750291] fb0: nouveaufb frame buffer device
May 23 00:18:48 bdt kernel: [    1.750292] registered panic notifier
May 23 00:18:48 bdt kernel: [    1.750296] [drm] Initialized nouveau 0.0.15 20090420 for 0000:01:00.0 on minor 0
May 23 00:18:48 bdt kernel: [    1.842144] usb 4-2: configuration #1 chosen from 1 choice
May 23 00:18:48 bdt kernel: [    1.848835] usbcore: registered new interface driver hiddev
May 23 00:18:48 bdt kernel: [    1.849972] generic-usb: probe of 0003:0A48:4001.0001 failed with error -22
May 23 00:18:48 bdt kernel: [    1.864341] input: USB Optical Mouse as /devices/pci0000:00/0000:00:1a.1/usb4/4-2/4-2:1.0/input/input4
May 23 00:18:48 bdt kernel: [    1.864428] generic-usb 0003:0461:4D64.0002: input,hidraw0: USB HID v1.11 Mouse [USB Optical Mouse] on usb-0000:00:1a.1-2/input0
May 23 00:18:48 bdt kernel: [    1.864445] usbcore: registered new interface driver usbhid
May 23 00:18:48 bdt kernel: [    1.864447] usbhid: v2.6:USB HID core driver
May 23 00:18:48 bdt kernel: [    2.160039] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
May 23 00:18:48 bdt kernel: [    2.164149] ata2.00: ATAPI: HL-DT-ST DVDRAM GH41N, MN01, max UDMA/100, ATAPI AN
May 23 00:18:48 bdt kernel: [    2.168483] ata2.00: configured for UDMA/100
May 23 00:18:48 bdt kernel: [    2.192302] scsi 1:0:0:0: CD-ROM            HL-DT-ST DVDRAM GH41N     MN01 PQ: 0 ANSI: 5
May 23 00:18:48 bdt kernel: [    2.213236] sr0: scsi3-mmc drive: 40x/40x writer dvd-ram cd/rw xa/form2 cdda tray
May 23 00:18:48 bdt kernel: [    2.213239] Uniform CD-ROM driver Revision: 3.20
May 23 00:18:48 bdt kernel: [    2.213423] sr 1:0:0:0: Attached scsi generic sg1 type 5
May 23 00:18:48 bdt kernel: [    2.560028] ata3: SATA link down (SStatus 0 SControl 300)
May 23 00:18:48 bdt kernel: [    2.930037] ata4: SATA link down (SStatus 0 SControl 300)
May 23 00:18:48 bdt kernel: [    3.300041] ata5: SATA link down (SStatus 0 SControl 300)
May 23 00:18:48 bdt kernel: [    3.670037] ata6: SATA link down (SStatus 0 SControl 300)
May 23 00:18:48 bdt kernel: [    3.691964] vga16fb: mapped to 0xffff8800000a0000
May 23 00:18:48 bdt kernel: [    3.691968] vga16fb: not registering due to another framebuffer present
May 23 00:18:48 bdt kernel: [    3.697727] [drm] nouveau 0000:01:00.0: 0x1231: parsing clock script 0
May 23 00:18:48 bdt kernel: [    3.697860] Console: switching to colour frame buffer device 160x64
May 23 00:18:48 bdt kernel: [    4.176193] EXT4-fs (sda2): INFO: recovery required on readonly filesystem
May 23 00:18:48 bdt kernel: [    4.176197] EXT4-fs (sda2): write access will be enabled during recovery
May 23 00:18:48 bdt kernel: [    5.504743] EXT4-fs (sda2): orphan cleanup on readonly fs
May 23 00:18:48 bdt kernel: [    5.598486] EXT4-fs (sda2): 17 orphan inodes deleted
May 23 00:18:48 bdt kernel: [    5.598489] EXT4-fs (sda2): recovery complete
May 23 00:18:48 bdt kernel: [    5.890669] EXT4-fs (sda2): mounted filesystem with ordered data mode
May 23 00:18:48 bdt kernel: [    6.394511] scsi 6:0:0:0: Direct-Access     Generic  USB SD Reader    1.00 PQ: 0 ANSI: 0
May 23 00:18:48 bdt kernel: [    6.395009] scsi 6:0:0:1: Direct-Access     Generic  USB CF Reader    1.01 PQ: 0 ANSI: 0
May 23 00:18:48 bdt kernel: [    6.395515] scsi 6:0:0:2: Direct-Access     Generic  USB xD/SM Reader 1.02 PQ: 0 ANSI: 0
May 23 00:18:48 bdt kernel: [    6.396136] scsi 6:0:0:3: Direct-Access     Generic  USB MS Reader    1.03 PQ: 0 ANSI: 0 CCS
May 23 00:18:48 bdt kernel: [    6.396758] scsi 6:0:0:4: Direct-Access     Generic  Mini SD Reader   1.06 PQ: 0 ANSI: 0
May 23 00:18:48 bdt kernel: [    6.397129] sd 6:0:0:0: Attached scsi generic sg2 type 0
May 23 00:18:48 bdt kernel: [    6.397223] sd 6:0:0:1: Attached scsi generic sg3 type 0
May 23 00:18:48 bdt kernel: [    6.397319] sd 6:0:0:2: Attached scsi generic sg4 type 0
May 23 00:18:48 bdt kernel: [    6.397430] sd 6:0:0:3: Attached scsi generic sg5 type 0
May 23 00:18:48 bdt kernel: [    6.397525] sd 6:0:0:4: Attached scsi generic sg6 type 0
May 23 00:18:48 bdt kernel: [    6.401127] sd 6:0:0:0: [sdb] Attached SCSI removable disk
May 23 00:18:48 bdt kernel: [    6.401756] sd 6:0:0:1: [sdc] Attached SCSI removable disk
May 23 00:18:48 bdt kernel: [    6.402375] sd 6:0:0:2: [sdd] Attached SCSI removable disk
May 23 00:18:48 bdt kernel: [    6.403001] sd 6:0:0:3: [sde] Attached SCSI removable disk
May 23 00:18:48 bdt kernel: [    6.403627] sd 6:0:0:4: [sdf] Attached SCSI removable disk
May 23 00:18:48 bdt kernel: [    7.815475] udev: starting version 151
May 23 00:18:48 bdt kernel: [    8.167051] type=1505 audit(1274588321.842:2):  operation="profile_load" pid=595 name="/sbin/dhclient3"
May 23 00:18:48 bdt kernel: [    8.167579] type=1505 audit(1274588321.842:3):  operation="profile_load" pid=595 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
May 23 00:18:48 bdt kernel: [    8.167846] type=1505 audit(1274588321.842:4):  operation="profile_load" pid=595 name="/usr/lib/connman/scripts/dhclient-script"
May 23 00:18:48 bdt kernel: [    8.392328] cfg80211: Calling CRDA to update world regulatory domain
May 23 00:18:48 bdt kernel: [    8.497070] ath5k 0000:04:02.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
May 23 00:18:48 bdt kernel: [    8.497138] ath5k 0000:04:02.0: registered as 'phy0'
May 23 00:18:48 bdt kernel: [    8.604466] Linux video capture interface: v2.00
May 23 00:18:48 bdt kernel: [    8.633599] cx23885 driver version 0.0.2 loaded
May 23 00:18:48 bdt kernel: [    8.633812] cx23885 0000:02:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
May 23 00:18:48 bdt kernel: [    8.633815] cx23885[0]: Your board isn't known (yet) to the driver.
May 23 00:18:48 bdt kernel: [    8.633816] cx23885[0]: Try to pick one of the existing card configs via
May 23 00:18:48 bdt kernel: [    8.633817] cx23885[0]: card=<n> insmod option.  Updating to the latest
May 23 00:18:48 bdt kernel: [    8.633817] cx23885[0]: version might help as well.
May 23 00:18:48 bdt kernel: [    8.633819] cx23885[0]: Here is a list of valid choices for the card=<n> insmod option:
May 23 00:18:48 bdt kernel: [    8.633821] cx23885[0]:    card=0 -> UNKNOWN/GENERIC
May 23 00:18:48 bdt kernel: [    8.633822] cx23885[0]:    card=1 -> Hauppauge WinTV-HVR1800lp
May 23 00:18:48 bdt kernel: [    8.633824] cx23885[0]:    card=2 -> Hauppauge WinTV-HVR1800
May 23 00:18:48 bdt kernel: [    8.633825] cx23885[0]:    card=3 -> Hauppauge WinTV-HVR1250
May 23 00:18:48 bdt kernel: [    8.633827] cx23885[0]:    card=4 -> DViCO FusionHDTV5 Express
May 23 00:18:48 bdt kernel: [    8.633828] cx23885[0]:    card=5 -> Hauppauge WinTV-HVR1500Q
May 23 00:18:48 bdt kernel: [    8.633830] cx23885[0]:    card=6 -> Hauppauge WinTV-HVR1500
May 23 00:18:48 bdt kernel: [    8.633831] cx23885[0]:    card=7 -> Hauppauge WinTV-HVR1200
May 23 00:18:48 bdt kernel: [    8.633832] cx23885[0]:    card=8 -> Hauppauge WinTV-HVR1700
May 23 00:18:48 bdt kernel: [    8.633834] cx23885[0]:    card=9 -> Hauppauge WinTV-HVR1400
May 23 00:18:48 bdt kernel: [    8.633835] cx23885[0]:    card=10 -> DViCO FusionHDTV7 Dual Express
May 23 00:18:48 bdt kernel: [    8.633837] cx23885[0]:    card=11 -> DViCO FusionHDTV DVB-T Dual Express
May 23 00:18:48 bdt kernel: [    8.633839] cx23885[0]:    card=12 -> Leadtek Winfast PxDVR3200 H
May 23 00:18:48 bdt kernel: [    8.633840] cx23885[0]:    card=13 -> Compro VideoMate E650F
May 23 00:18:48 bdt kernel: [    8.633842] cx23885[0]:    card=14 -> TurboSight TBS 6920
May 23 00:18:48 bdt kernel: [    8.633843] cx23885[0]:    card=15 -> TeVii S470
May 23 00:18:48 bdt kernel: [    8.633844] cx23885[0]:    card=16 -> DVBWorld DVB-S2 2005
May 23 00:18:48 bdt kernel: [    8.633846] cx23885[0]:    card=17 -> NetUP Dual DVB-S2 CI
May 23 00:18:48 bdt kernel: [    8.633847] cx23885[0]:    card=18 -> Hauppauge WinTV-HVR1270
May 23 00:18:48 bdt kernel: [    8.633849] cx23885[0]:    card=19 -> Hauppauge WinTV-HVR1275
May 23 00:18:48 bdt kernel: [    8.633850] cx23885[0]:    card=20 -> Hauppauge WinTV-HVR1255
May 23 00:18:48 bdt kernel: [    8.633852] cx23885[0]:    card=21 -> Hauppauge WinTV-HVR1210
May 23 00:18:48 bdt kernel: [    8.633853] cx23885[0]:    card=22 -> Mygica X8506 DMB-TH
May 23 00:18:48 bdt kernel: [    8.633855] cx23885[0]:    card=23 -> Magic-Pro ProHDTV Extreme 2
May 23 00:18:48 bdt kernel: [    8.633856] cx23885[0]:    card=24 -> Hauppauge WinTV-HVR1850
May 23 00:18:48 bdt kernel: [    8.633858] cx23885[0]:    card=25 -> Compro VideoMate E800
May 23 00:18:48 bdt kernel: [    8.634011] CORE cx23885[0]: subsystem: 12ab:d575, board: UNKNOWN/GENERIC [card=0,autodetected]
May 23 00:18:48 bdt kernel: [    8.761540] cx23885_dev_checkrevision() Hardware revision = 0xa5
May 23 00:18:48 bdt kernel: [    8.761547] cx23885[0]/0: found at 0000:02:00.0, rev: 4, irq: 16, latency: 0, mmio: 0xfe800000
May 23 00:18:48 bdt kernel: [    8.761556] IRQ 16/cx23885[0]: IRQF_DISABLED is not guaranteed on shared IRQs
May 23 00:18:48 bdt kernel: [    9.166400] lp: driver loaded but no devices found
May 23 00:18:48 bdt kernel: [    9.177767] ath5k phy0: Atheros AR5414 chip found (MAC: 0xa2, PHY: 0x61)
May 23 00:18:48 bdt kernel: [    9.409158] cfg80211: World regulatory domain updated:
May 23 00:18:48 bdt kernel: [    9.409161] 	(start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
May 23 00:18:48 bdt kernel: [    9.409164] 	(2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
May 23 00:18:48 bdt kernel: [    9.409166] 	(2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
May 23 00:18:48 bdt kernel: [    9.409168] 	(2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
May 23 00:18:48 bdt kernel: [    9.409170] 	(5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
May 23 00:18:48 bdt kernel: [    9.409171] 	(5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
May 23 00:18:48 bdt kernel: [    9.679716] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
May 23 00:18:48 bdt kernel: [   10.760009] hda-intel: azx_get_response timeout, switching to polling mode: last cmd=0x300f0000
May 23 00:18:48 bdt kernel: [   11.770003] hda-intel: Codec #3 probe error; disabling it...
May 23 00:18:48 bdt kernel: [   11.953534] hda_codec: ALC888: BIOS auto-probing.
May 23 00:18:48 bdt kernel: [   11.954954] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:1b.0/input/input5
May 23 00:18:48 bdt kernel: [   11.963082] HDA Intel 0000:01:00.1: PCI INT A -> GSI 16 (level, low) -> IRQ 16
May 23 00:18:48 bdt kernel: [   11.963085] hda_intel: Disable MSI for Nvidia chipset
May 23 00:18:48 bdt kernel: [   14.010503] EXT4-fs (sda3): mounted filesystem with ordered data mode
May 23 00:18:50 bdt kernel: [   17.043188] type=1505 audit(1274588330.722:5):  operation="profile_load" pid=1298 name="/usr/share/gdm/guest-session/Xsession"
May 23 00:18:50 bdt kernel: [   17.044783] type=1505 audit(1274588330.722:6):  operation="profile_replace" pid=1299 name="/sbin/dhclient3"
May 23 00:18:50 bdt kernel: [   17.045287] type=1505 audit(1274588330.722:7):  operation="profile_replace" pid=1299 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
May 23 00:18:50 bdt kernel: [   17.045560] type=1505 audit(1274588330.722:8):  operation="profile_replace" pid=1299 name="/usr/lib/connman/scripts/dhclient-script"
May 23 00:18:50 bdt kernel: [   17.228830] type=1505 audit(1274588330.902:9):  operation="profile_load" pid=1300 name="/usr/bin/evince"
May 23 00:18:50 bdt kernel: [   17.235392] type=1505 audit(1274588330.912:10):  operation="profile_load" pid=1300 name="/usr/bin/evince-previewer"
May 23 00:18:50 bdt kernel: [   17.239302] type=1505 audit(1274588330.912:11):  operation="profile_load" pid=1300 name="/usr/bin/evince-thumbnailer"
May 23 00:18:51 bdt kernel: [   17.361320] type=1505 audit(1274588331.042:12):  operation="profile_load" pid=1305 name="/usr/lib/cups/backend/cups-pdf"
May 23 00:18:51 bdt kernel: [   17.361956] type=1505 audit(1274588331.042:13):  operation="profile_load" pid=1305 name="/usr/sbin/cupsd"
May 23 00:18:51 bdt kernel: [   17.364465] type=1505 audit(1274588331.042:14):  operation="profile_load" pid=1306 name="/usr/sbin/tcpdump"
May 23 00:18:51 bdt kernel: [   17.543436] ADDRCONF(NETDEV_UP): eth0: link is not ready
May 23 00:18:51 bdt kernel: [   17.832092] ADDRCONF(NETDEV_UP): wlan0: link is not ready
May 23 00:18:52 bdt kernel: [   18.567550] VBoxDrv: dbg - g_abExecMemory=ffffffffa03eea20
May 23 00:18:52 bdt kernel: [   18.567612] vboxdrv: fAsync=0 offMin=0x310 offMax=0x3938
May 23 00:18:52 bdt kernel: [   18.567914] vboxdrv: TSC mode is 'synchronous', kernel timer mode is 'normal'.
May 23 00:18:52 bdt kernel: [   19.092007] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
May 23 00:18:52 bdt kernel: [   19.092010] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
May 23 00:18:52 bdt kernel: [   19.092795] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
May 23 00:18:53 bdt kernel: [   19.946777] [drm] nouveau 0000:01:00.0: Allocating FIFO number 2
May 23 00:18:53 bdt kernel: [   19.949742] [drm] nouveau 0000:01:00.0: nouveau_channel_alloc: initialised FIFO 2
May 23 00:18:53 bdt kernel: [   19.996076] [drm] nouveau 0000:01:00.0: 0x1231: parsing clock script 0
May 23 00:18:53 bdt kernel: [   20.102230] ppdev: user-space parallel port driver
May 23 00:19:07 bdt kernel: [   33.376907] Intel AES-NI instructions are not detected.
May 23 00:19:07 bdt kernel: [   33.462970] padlock: VIA PadLock not detected.
May 23 00:22:58 bdt sudo: pam_sm_authenticate: Called
May 23 00:22:58 bdt sudo: pam_sm_authenticate: username = [bpoconner]
May 23 00:22:58 bdt sudo: pam_sm_authenticate: /home/bpoconner is already mounted
May 23 00:23:12 bdt sudo: pam_sm_authenticate: Called
May 23 00:23:12 bdt sudo: pam_sm_authenticate: username = [bpoconner]
May 23 00:23:12 bdt sudo: pam_sm_authenticate: /home/bpoconner is already mounted

```

I'm not very knowledgebale about what all that means, but none of it looks suspicious to me.

Here's my output from dmesg log

```

[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.32-21-generic (buildd@yellow) (gcc version 4.4.3 (Ubuntu 4.4.3-4ubuntu5) ) #32-Ubuntu SMP Fri Apr 16 08:09:38 UTC 2010 (Ubuntu 2.6.32-21.32-generic 2.6.32.11+drm33.2)
[    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-2.6.32-21-generic root=UUID=426b3181-4dd8-4420-99d5-4b476b5c3b3e ro quiet splash
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   Centaur CentaurHauls
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 0000000000095c00 (usable)
[    0.000000]  BIOS-e820: 0000000000095c00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e5000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 00000000bff90000 (usable)
[    0.000000]  BIOS-e820: 00000000bff90000 - 00000000bff9e000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000bff9e000 - 00000000bffe0000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000bffe0000 - 00000000c0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000ffb00000 - 0000000100000000 (reserved)
[    0.000000]  BIOS-e820: 0000000100000000 - 0000000240000000 (usable)
[    0.000000] DMI present.
[    0.000000] AMI BIOS detected: BIOS may corrupt low RAM, working around it.
[    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
[    0.000000] last_pfn = 0x240000 max_arch_pfn = 0x400000000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-D3FFF write-protect
[    0.000000]   D4000-DFFFF uncachable
[    0.000000]   E0000-EFFFF write-through
[    0.000000]   F0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000 mask E00000000 write-back
[    0.000000]   1 base 200000000 mask FC0000000 write-back
[    0.000000]   2 base 0C0000000 mask FC0000000 uncachable
[    0.000000]   3 disabled
[    0.000000]   4 disabled
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] e820 update range: 00000000c0000000 - 0000000100000000 (usable) ==> (reserved)
[    0.000000] last_pfn = 0xbff90 max_arch_pfn = 0x400000000
[    0.000000] Scanning 0 areas for low memory corruption
[    0.000000] modified physical RAM map:
[    0.000000]  modified: 0000000000000000 - 0000000000010000 (reserved)
[    0.000000]  modified: 0000000000010000 - 0000000000095c00 (usable)
[    0.000000]  modified: 0000000000095c00 - 00000000000a0000 (reserved)
[    0.000000]  modified: 00000000000e5000 - 0000000000100000 (reserved)
[    0.000000]  modified: 0000000000100000 - 00000000bff90000 (usable)
[    0.000000]  modified: 00000000bff90000 - 00000000bff9e000 (ACPI data)
[    0.000000]  modified: 00000000bff9e000 - 00000000bffe0000 (ACPI NVS)
[    0.000000]  modified: 00000000bffe0000 - 00000000c0000000 (reserved)
[    0.000000]  modified: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  modified: 00000000ffb00000 - 0000000100000000 (reserved)
[    0.000000]  modified: 0000000100000000 - 0000000240000000 (usable)
[    0.000000] initial memory mapped : 0 - 20000000
[    0.000000] init_memory_mapping: 0000000000000000-00000000bff90000
[    0.000000] NX (Execute Disable) protection: active
[    0.000000]  0000000000 - 00bfe00000 page 2M
[    0.000000]  00bfe00000 - 00bff90000 page 4k
[    0.000000] kernel direct mapping tables up to bff90000 @ 10000-15000
[    0.000000] init_memory_mapping: 0000000100000000-0000000240000000
[    0.000000] NX (Execute Disable) protection: active
[    0.000000]  0100000000 - 0240000000 page 2M
[    0.000000] kernel direct mapping tables up to 240000000 @ 13000-1d000
[    0.000000] RAMDISK: 3728a000 - 37fef9ef
[    0.000000] ACPI: RSDP 00000000000fa7a0 00014 (v00 ACPIAM)
[    0.000000] ACPI: RSDT 00000000bff90000 00048 (v01 ACRSYS ACRPRDCT 20090818 MSFT 00000097)
[    0.000000] ACPI: FACP 00000000bff90200 00084 (v01 081809 FACP1629 20090818 MSFT 00000097)
[    0.000000] ACPI: DSDT 00000000bff905c0 06BDB (v01  1AAAA 1AAAA000 00000000 INTL 20051117)
[    0.000000] ACPI: FACS 00000000bff9e000 00040
[    0.000000] ACPI: APIC 00000000bff90390 0006C (v01 081809 APIC1629 20090818 MSFT 00000097)
[    0.000000] ACPI: MCFG 00000000bff90400 0003C (v01 081809 OEMMCFG  20090818 MSFT 00000097)
[    0.000000] ACPI: SLIC 00000000bff90440 00176 (v01 ACRSYS ACRPRDCT 20090818 MSFT 00000097)
[    0.000000] ACPI: OEMB 00000000bff9e040 00072 (v01 081809 OEMB1629 20090818 MSFT 00000097)
[    0.000000] ACPI: HPET 00000000bff985c0 00038 (v01 081809 OEMHPET  20090818 MSFT 00000097)
[    0.000000] ACPI: GSCI 00000000bff9e0c0 02024 (v01 081809 GMCHSCI  20090818 MSFT 00000097)
[    0.000000] ACPI: AWMI 00000000bffa00f0 0004E (v01 081809 OEMB1629 20090818 MSFT 00000097)
[    0.000000] ACPI: SSDT 00000000bffa10b0 00A7C (v01 DpgPmm    CpuPm 00000012 INTL 20051117)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at 0000000000000000-0000000240000000
[    0.000000] Bootmem setup node 0 0000000000000000-0000000240000000
[    0.000000]   NODE_DATA [0000000000018000 - 000000000001cfff]
[    0.000000]   bootmap [000000000001d000 -  0000000000064fff] pages 48
[    0.000000] (8 early reservations) ==> bootmem [0000000000 - 0240000000]
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000]   #1 [0000006000 - 0000008000]       TRAMPOLINE ==> [0000006000 - 0000008000]
[    0.000000]   #2 [0001000000 - 0001a29e64]    TEXT DATA BSS ==> [0001000000 - 0001a29e64]
[    0.000000]   #3 [003728a000 - 0037fef9ef]          RAMDISK ==> [003728a000 - 0037fef9ef]
[    0.000000]   #4 [0000095c00 - 0000100000]    BIOS reserved ==> [0000095c00 - 0000100000]
[    0.000000]   #5 [0001a2a000 - 0001a2a250]              BRK ==> [0001a2a000 - 0001a2a250]
[    0.000000]   #6 [0000010000 - 0000013000]          PGTABLE ==> [0000010000 - 0000013000]
[    0.000000]   #7 [0000013000 - 0000018000]          PGTABLE ==> [0000013000 - 0000018000]
[    0.000000] found SMP MP-table at [ffff8800000ff780] ff780
[    0.000000]  [ffffea0000000000-ffffea0007dfffff] PMD -> [ffff880028600000-ffff88002f5fffff] on node 0
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   DMA32    0x00001000 -> 0x00100000
[    0.000000]   Normal   0x00100000 -> 0x00240000
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[3] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x00000095
[    0.000000]     0: 0x00000100 -> 0x000bff90
[    0.000000]     0: 0x00100000 -> 0x00240000
[    0.000000] On node 0 totalpages: 2096917
[    0.000000]   DMA zone: 56 pages used for memmap
[    0.000000]   DMA zone: 117 pages reserved
[    0.000000]   DMA zone: 3800 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 14280 pages used for memmap
[    0.000000]   DMA32 zone: 767944 pages, LIFO batch:31
[    0.000000]   Normal zone: 17920 pages used for memmap
[    0.000000]   Normal zone: 1292800 pages, LIFO batch:31
[    0.000000] ACPI: PM-Timer IO Port: 0x808
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x02] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x03] enabled)
[    0.000000] ACPI: IOAPIC (id[0x04] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 4, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x8086a301 base: 0xfed00000
[    0.000000] SMP: Allowing 4 CPUs, 0 hotplug CPUs
[    0.000000] nr_irqs_gsi: 24
[    0.000000] PM: Registered nosave memory: 0000000000095000 - 0000000000096000
[    0.000000] PM: Registered nosave memory: 0000000000096000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e5000
[    0.000000] PM: Registered nosave memory: 00000000000e5000 - 0000000000100000
[    0.000000] PM: Registered nosave memory: 00000000bff90000 - 00000000bff9e000
[    0.000000] PM: Registered nosave memory: 00000000bff9e000 - 00000000bffe0000
[    0.000000] PM: Registered nosave memory: 00000000bffe0000 - 00000000c0000000
[    0.000000] PM: Registered nosave memory: 00000000c0000000 - 00000000fee00000
[    0.000000] PM: Registered nosave memory: 00000000fee00000 - 00000000fee01000
[    0.000000] PM: Registered nosave memory: 00000000fee01000 - 00000000ffb00000
[    0.000000] PM: Registered nosave memory: 00000000ffb00000 - 0000000100000000
[    0.000000] Allocating PCI resources starting at c0000000 (gap: c0000000:3ee00000)
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] NR_CPUS:64 nr_cpumask_bits:64 nr_cpu_ids:4 nr_node_ids:1
[    0.000000] PERCPU: Embedded 30 pages/cpu @ffff880028200000 s91544 r8192 d23144 u524288
[    0.000000] pcpu-alloc: s91544 r8192 d23144 u524288 alloc=1*2097152
[    0.000000] pcpu-alloc: [0] 0 1 2 3 
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 2064544
[    0.000000] Policy zone: Normal
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.32-21-generic root=UUID=426b3181-4dd8-4420-99d5-4b476b5c3b3e ro quiet splash
[    0.000000] PID hash table entries: 4096 (order: 3, 32768 bytes)
[    0.000000] Initializing CPU#0
[    0.000000] xsave/xrstor: enabled xstate_bv 0x3, cntxt size 0x240
[    0.000000] Checking aperture...
[    0.000000] No AGP bridge found
[    0.000000] Calgary: detecting Calgary via BIOS EBDA area
[    0.000000] Calgary: Unable to locate Rio Grande table in EBDA - bailing!
[    0.000000] PCI-DMA: Using software bounce buffering for IO (SWIOTLB)
[    0.000000] Placing 64MB software IO TLB between ffff880020000000 - ffff880024000000
[    0.000000] software IO TLB at phys 0x20000000 - 0x24000000
[    0.000000] Memory: 8182080k/9437184k available (5409k kernel code, 1049516k absent, 205588k reserved, 2976k data, 876k init)
[    0.000000] SLUB: Genslabs=14, HWalign=64, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000] NR_IRQS:4352 nr_irqs:440
[    0.000000] Console: colour VGA+ 80x25
[    0.000000] console [tty0] enabled
[    0.000000] allocated 83886080 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] hpet clockevent registered
[    0.000000] HPET: 4 timers in total, 0 timers will be used for per-cpu timer
[    0.000000] Fast TSC calibration failed
[    0.000000] TSC: PIT calibration matches HPET. 1 loops
[    0.000000] Detected 2666.626 MHz processor.
[    0.010005] Calibrating delay loop (skipped), value calculated using timer frequency.. 5333.25 BogoMIPS (lpj=26666260)
[    0.010028] Security Framework initialized
[    0.010045] AppArmor: AppArmor initialized
[    0.010628] Dentry cache hash table entries: 1048576 (order: 11, 8388608 bytes)
[    0.022619] Inode-cache hash table entries: 524288 (order: 10, 4194304 bytes)
[    0.024048] Mount-cache hash table entries: 256
[    0.024174] Initializing cgroup subsys ns
[    0.024180] Initializing cgroup subsys cpuacct
[    0.024182] Initializing cgroup subsys memory
[    0.024188] Initializing cgroup subsys devices
[    0.024190] Initializing cgroup subsys freezer
[    0.024192] Initializing cgroup subsys net_cls
[    0.024209] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.024211] CPU: L2 cache: 2048K
[    0.024214] CPU 0/0x0 -> Node 0
[    0.024216] CPU: Physical Processor ID: 0
[    0.024217] CPU: Processor Core ID: 0
[    0.024220] mce: CPU supports 6 MCE banks
[    0.024226] CPU0: Thermal monitoring enabled (TM2)
[    0.024230] using mwait in idle threads.
[    0.024232] Performance Events: Core2 events, Intel PMU driver.
[    0.024237] ... version:                2
[    0.024238] ... bit width:              40
[    0.024239] ... generic registers:      2
[    0.024240] ... value mask:             000000ffffffffff
[    0.024242] ... max period:             000000007fffffff
[    0.024243] ... fixed-purpose events:   3
[    0.024244] ... event mask:             0000000700000003
[    0.027005] ACPI: Core revision 20090903
[    0.040006] ftrace: converting mcount calls to 0f 1f 44 00 00
[    0.040010] ftrace: allocating 22518 entries in 89 pages
[    0.050049] Setting APIC routing to flat
[    0.050350] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.157463] CPU0: Intel(R) Core(TM)2 Quad CPU    Q8400  @ 2.66GHz stepping 0a
[    0.160000] APIC calibration not consistent with PM-Timer: 109ms instead of 100ms
[    0.160000] APIC delta adjusted to PM-Timer: 2083298 (2291626)
[    0.160000] Booting processor 1 APIC 0x1 ip 0x6000
[    0.020000] Initializing CPU#1
[    0.020000] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.020000] CPU: L2 cache: 2048K
[    0.020000] CPU 1/0x1 -> Node 0
[    0.020000] CPU: Physical Processor ID: 0
[    0.020000] CPU: Processor Core ID: 1
[    0.020000] CPU1: Thermal monitoring enabled (TM2)
[    0.310113] CPU1: Intel(R) Core(TM)2 Quad CPU    Q8400  @ 2.66GHz stepping 0a
[    0.310119] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
[    0.320092] Booting processor 2 APIC 0x2 ip 0x6000
[    0.020000] Initializing CPU#2
[    0.020000] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.020000] CPU: L2 cache: 2048K
[    0.020000] CPU 2/0x2 -> Node 0
[    0.020000] CPU: Physical Processor ID: 0
[    0.020000] CPU: Processor Core ID: 2
[    0.020000] CPU2: Thermal monitoring enabled (TM2)
[    0.480084] CPU2: Intel(R) Core(TM)2 Quad CPU    Q8400  @ 2.66GHz stepping 0a
[    0.480090] checking TSC synchronization [CPU#0 -> CPU#2]: passed.
[    0.490065] Booting processor 3 APIC 0x3 ip 0x6000
[    0.020000] Initializing CPU#3
[    0.020000] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.020000] CPU: L2 cache: 2048K
[    0.020000] CPU 3/0x3 -> Node 0
[    0.020000] CPU: Physical Processor ID: 0
[    0.020000] CPU: Processor Core ID: 3
[    0.020000] CPU3: Thermal monitoring enabled (TM2)
[    0.650089] CPU3: Intel(R) Core(TM)2 Quad CPU    Q8400  @ 2.66GHz stepping 0a
[    0.650095] checking TSC synchronization [CPU#0 -> CPU#3]: passed.
[    0.660010] Brought up 4 CPUs
[    0.660012] Total of 4 processors activated (21333.06 BogoMIPS).
[    0.661196] CPU0 attaching sched-domain:
[    0.661199]  domain 0: span 0-1 level MC
[    0.661201]   groups: 0 1
[    0.661204]   domain 1: span 0-3 level CPU
[    0.661206]    groups: 0-1 (cpu_power = 2048) 2-3 (cpu_power = 2048)
[    0.661212] CPU1 attaching sched-domain:
[    0.661213]  domain 0: span 0-1 level MC
[    0.661215]   groups: 1 0
[    0.661218]   domain 1: span 0-3 level CPU
[    0.661219]    groups: 0-1 (cpu_power = 2048) 2-3 (cpu_power = 2048)
[    0.661224] CPU2 attaching sched-domain:
[    0.661226]  domain 0: span 2-3 level MC
[    0.661227]   groups: 2 3
[    0.661230]   domain 1: span 0-3 level CPU
[    0.661231]    groups: 2-3 (cpu_power = 2048) 0-1 (cpu_power = 2048)
[    0.661236] CPU3 attaching sched-domain:
[    0.661237]  domain 0: span 2-3 level MC
[    0.661239]   groups: 3 2
[    0.661241]   domain 1: span 0-3 level CPU
[    0.661243]    groups: 2-3 (cpu_power = 2048) 0-1 (cpu_power = 2048)
[    0.661379] devtmpfs: initialized
[    0.661379] regulator: core version 0.5
[    0.661379] Time:  0:30:55  Date: 05/23/10
[    0.661379] NET: Registered protocol family 16
[    0.661379] Trying to unpack rootfs image as initramfs...
[    0.661379] ACPI: bus type pci registered
[    0.661379] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 255
[    0.661379] PCI: Not using MMCONFIG.
[    0.661379] PCI: Using configuration type 1 for base access
[    0.661379] bio: create slab <bio-0> at 0
[    0.661379] ACPI: EC: Look up EC in DSDT
[    0.664362] ACPI: Executed 1 blocks of module-level executable AML code
[    0.672916] ACPI: Interpreter enabled
[    0.672918] ACPI: (supports S0 S3 S4 S5)
[    0.672934] ACPI: Using IOAPIC for interrupt routing
[    0.672980] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 255
[    0.678090] PCI: MCFG area at e0000000 reserved in ACPI motherboard resources
[    0.684406] PCI: Using MMCONFIG at e0000000 - efffffff
[    0.694486] ACPI: No dock devices found.
[    0.694754] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.694839] pci 0000:00:01.0: PME# supported from D0 D3hot D3cold
[    0.694841] pci 0000:00:01.0: PME# disabled
[    0.694895] pci 0000:00:19.0: reg 10 32bit mmio: [0xfcfe0000-0xfcffffff]
[    0.694900] pci 0000:00:19.0: reg 14 32bit mmio: [0xfcfdf000-0xfcfdffff]
[    0.694905] pci 0000:00:19.0: reg 18 io port: [0xcc00-0xcc1f]
[    0.694937] pci 0000:00:19.0: PME# supported from D0 D3hot D3cold
[    0.694940] pci 0000:00:19.0: PME# disabled
[    0.694982] pci 0000:00:1a.0: reg 20 io port: [0xc880-0xc89f]
[    0.695041] pci 0000:00:1a.1: reg 20 io port: [0xc800-0xc81f]
[    0.695098] pci 0000:00:1a.2: reg 20 io port: [0xc480-0xc49f]
[    0.695160] pci 0000:00:1a.7: reg 10 32bit mmio: [0xfcfdec00-0xfcfdefff]
[    0.695206] pci 0000:00:1a.7: PME# supported from D0 D3hot D3cold
[    0.695210] pci 0000:00:1a.7: PME# disabled
[    0.695243] pci 0000:00:1b.0: reg 10 64bit mmio: [0xfcfd8000-0xfcfdbfff]
[    0.695277] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    0.695280] pci 0000:00:1b.0: PME# disabled
[    0.695331] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.695334] pci 0000:00:1c.0: PME# disabled
[    0.695388] pci 0000:00:1c.1: PME# supported from D0 D3hot D3cold
[    0.695391] pci 0000:00:1c.1: PME# disabled
[    0.695441] pci 0000:00:1d.0: reg 20 io port: [0xc400-0xc41f]
[    0.695498] pci 0000:00:1d.1: reg 20 io port: [0xc080-0xc09f]
[    0.695556] pci 0000:00:1d.2: reg 20 io port: [0xc000-0xc01f]
[    0.695617] pci 0000:00:1d.7: reg 10 32bit mmio: [0xfcfde800-0xfcfdebff]
[    0.695665] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
[    0.695668] pci 0000:00:1d.7: PME# disabled
[    0.695773] pci 0000:00:1f.0: quirk: region 0800-087f claimed by ICH6 ACPI/GPIO/TCO
[    0.695776] pci 0000:00:1f.0: quirk: region 0480-04bf claimed by ICH6 GPIO
[    0.695779] pci 0000:00:1f.0: ICH7 LPC Generic IO decode 1 PIO at 0a00 (mask 00ff)
[    0.695834] pci 0000:00:1f.2: reg 10 io port: [0xbc00-0xbc07]
[    0.695838] pci 0000:00:1f.2: reg 14 io port: [0xb880-0xb883]
[    0.695843] pci 0000:00:1f.2: reg 18 io port: [0xb800-0xb807]
[    0.695848] pci 0000:00:1f.2: reg 1c io port: [0xb480-0xb483]
[    0.695853] pci 0000:00:1f.2: reg 20 io port: [0xb400-0xb41f]
[    0.695857] pci 0000:00:1f.2: reg 24 32bit mmio: [0xfcfde000-0xfcfde7ff]
[    0.695883] pci 0000:00:1f.2: PME# supported from D3hot
[    0.695885] pci 0000:00:1f.2: PME# disabled
[    0.695911] pci 0000:00:1f.3: reg 10 64bit mmio: [0xfcfddc00-0xfcfddcff]
[    0.695922] pci 0000:00:1f.3: reg 20 io port: [0x400-0x41f]
[    0.695961] pci 0000:01:00.0: reg 10 32bit mmio: [0xfd000000-0xfdffffff]
[    0.695968] pci 0000:01:00.0: reg 14 64bit mmio pref: [0xd0000000-0xdfffffff]
[    0.695975] pci 0000:01:00.0: reg 1c 64bit mmio pref: [0xce000000-0xcfffffff]
[    0.695980] pci 0000:01:00.0: reg 24 io port: [0xdc00-0xdc7f]
[    0.695984] pci 0000:01:00.0: reg 30 32bit mmio pref: [0xfe780000-0xfe7fffff]
[    0.696028] pci 0000:01:00.1: reg 10 32bit mmio: [0xfe77c000-0xfe77ffff]
[    0.696097] pci 0000:00:01.0: bridge io port: [0xd000-0xdfff]
[    0.696099] pci 0000:00:01.0: bridge 32bit mmio: [0xfd000000-0xfe7fffff]
[    0.696103] pci 0000:00:01.0: bridge 64bit mmio pref: [0xce000000-0xdfffffff]
[    0.696146] pci 0000:02:00.0: reg 10 64bit mmio: [0xfe800000-0xfe9fffff]
[    0.696219] pci 0000:02:00.0: supports D1 D2
[    0.696220] pci 0000:02:00.0: PME# supported from D0 D1 D2 D3hot
[    0.696225] pci 0000:02:00.0: PME# disabled
[    0.696274] pci 0000:00:1c.0: bridge 32bit mmio: [0xfe800000-0xfe9fffff]
[    0.696324] pci 0000:03:00.0: reg 10 64bit mmio: [0xfeaff800-0xfeafffff]
[    0.696331] pci 0000:03:00.0: reg 18 io port: [0xe800-0xe8ff]
[    0.696382] pci 0000:03:00.0: supports D2
[    0.696383] pci 0000:03:00.0: PME# supported from D2 D3hot D3cold
[    0.696387] pci 0000:03:00.0: PME# disabled
[    0.696431] pci 0000:00:1c.1: bridge io port: [0xe000-0xefff]
[    0.696434] pci 0000:00:1c.1: bridge 32bit mmio: [0xfea00000-0xfeafffff]
[    0.696471] pci 0000:04:02.0: reg 10 32bit mmio: [0xfebf0000-0xfebfffff]
[    0.696549] pci 0000:00:1e.0: transparent bridge
[    0.696554] pci 0000:00:1e.0: bridge 32bit mmio: [0xfeb00000-0xfebfffff]
[    0.696572] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.696691] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P1._PRT]
[    0.696778] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P4._PRT]
[    0.696824] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P5._PRT]
[    0.711744] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 6 7 *10 11 12 14 15)
[    0.711848] ACPI: PCI Interrupt Link [LNKB] (IRQs *5)
[    0.711949] ACPI: PCI Interrupt Link [LNKC] (IRQs *3 4 6 7 10 11 12 14 15)
[    0.712052] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 6 7 10 *11 12 14 15)
[    0.712156] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 6 7 10 11 12 14 *15)
[    0.712259] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 6 7 10 11 12 *14 15)
[    0.712362] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 6 *7 10 11 12 14 15)
[    0.712464] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 *4 6 7 10 11 12 14 15)
[    0.712564] vgaarb: device added: PCI:0000:01:00.0,decodes=io+mem,owns=io+mem,locks=none
[    0.712568] vgaarb: loaded
[    0.712662] SCSI subsystem initialized
[    0.712698] libata version 3.00 loaded.
[    0.712698] usbcore: registered new interface driver usbfs
[    0.712698] usbcore: registered new interface driver hub
[    0.712698] usbcore: registered new device driver usb
[    0.712698] ACPI: WMI: Mapper loaded
[    0.712698] PCI: Using ACPI for IRQ routing
[    0.712698] NetLabel: Initializing
[    0.712698] NetLabel:  domain hash size = 128
[    0.712698] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.712698] NetLabel:  unlabeled traffic allowed by default
[    0.712698] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0
[    0.712698] hpet0: 4 comparators, 64-bit 14.318180 MHz counter
[    0.730168] Switching to clocksource tsc
[    0.731681] AppArmor: AppArmor Filesystem Enabled
[    0.731701] pnp: PnP ACPI init
[    0.731724] ACPI: bus type pnp registered
[    0.735690] pnp: PnP ACPI: found 16 devices
[    0.735692] ACPI: ACPI bus type pnp unregistered
[    0.735703] system 00:01: iomem range 0xfed14000-0xfed19fff has been reserved
[    0.735706] system 00:01: iomem range 0xfed90000-0xfed93fff has been reserved
[    0.735712] system 00:08: ioport range 0xa00-0xa0f has been reserved
[    0.735714] system 00:08: ioport range 0xa10-0xa1f has been reserved
[    0.735717] system 00:08: ioport range 0xa20-0xa2f has been reserved
[    0.735719] system 00:08: ioport range 0xa30-0xa3f has been reserved
[    0.735723] system 00:09: ioport range 0x4d0-0x4d1 has been reserved
[    0.735725] system 00:09: ioport range 0x4c0-0x4cf has been reserved
[    0.735727] system 00:09: ioport range 0x4d2-0x4ff has been reserved
[    0.735729] system 00:09: ioport range 0x800-0x87f has been reserved
[    0.735731] system 00:09: ioport range 0x480-0x4bf has been reserved
[    0.735734] system 00:09: iomem range 0xfed1c000-0xfed1ffff has been reserved
[    0.735736] system 00:09: iomem range 0xfed20000-0xfed3ffff has been reserved
[    0.735738] system 00:09: iomem range 0xfed40000-0xfed8ffff has been reserved
[    0.735743] system 00:0c: iomem range 0xffc00000-0xffefffff has been reserved
[    0.735747] system 00:0d: iomem range 0xfec00000-0xfec00fff could not be reserved
[    0.735749] system 00:0d: iomem range 0xfee00000-0xfee00fff has been reserved
[    0.735753] system 00:0e: iomem range 0xe0000000-0xefffffff has been reserved
[    0.735758] system 00:0f: iomem range 0x0-0x9ffff could not be reserved
[    0.735760] system 00:0f: iomem range 0xc0000-0xcffff has been reserved
[    0.735762] system 00:0f: iomem range 0xe0000-0xfffff could not be reserved
[    0.735764] system 00:0f: iomem range 0x100000-0xbfffffff could not be reserved
[    0.735767] system 00:0f: iomem range 0xfed90000-0xffffffff could not be reserved
[    0.740481] pci 0000:00:01.0: PCI bridge, secondary bus 0000:01
[    0.740484] pci 0000:00:01.0:   IO window: 0xd000-0xdfff
[    0.740486] pci 0000:00:01.0:   MEM window: 0xfd000000-0xfe7fffff
[    0.740489] pci 0000:00:01.0:   PREFETCH window: 0x000000ce000000-0x000000dfffffff
[    0.740493] pci 0000:00:1c.0: PCI bridge, secondary bus 0000:02
[    0.740495] pci 0000:00:1c.0:   IO window: 0x1000-0x1fff
[    0.740499] pci 0000:00:1c.0:   MEM window: 0xfe800000-0xfe9fffff
[    0.740502] pci 0000:00:1c.0:   PREFETCH window: 0x000000c0000000-0x000000c01fffff
[    0.740507] pci 0000:00:1c.1: PCI bridge, secondary bus 0000:03
[    0.740509] pci 0000:00:1c.1:   IO window: 0xe000-0xefff
[    0.740513] pci 0000:00:1c.1:   MEM window: 0xfea00000-0xfeafffff
[    0.740516] pci 0000:00:1c.1:   PREFETCH window: 0x000000c0200000-0x000000c03fffff
[    0.740520] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:04
[    0.740522] pci 0000:00:1e.0:   IO window: disabled
[    0.740525] pci 0000:00:1e.0:   MEM window: 0xfeb00000-0xfebfffff
[    0.740528] pci 0000:00:1e.0:   PREFETCH window: disabled
[    0.740540]   alloc irq_desc for 16 on node -1
[    0.740541]   alloc kstat_irqs on node -1
[    0.740546] pci 0000:00:01.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.740549] pci 0000:00:01.0: setting latency timer to 64
[    0.740556] pci 0000:00:1c.0: enabling device (0106 -> 0107)
[    0.740558]   alloc irq_desc for 17 on node -1
[    0.740560]   alloc kstat_irqs on node -1
[    0.740562] pci 0000:00:1c.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    0.740565] pci 0000:00:1c.0: setting latency timer to 64
[    0.740572] pci 0000:00:1c.1: PCI INT B -> GSI 16 (level, low) -> IRQ 16
[    0.740575] pci 0000:00:1c.1: setting latency timer to 64
[    0.740580] pci 0000:00:1e.0: setting latency timer to 64
[    0.740583] pci_bus 0000:00: resource 0 io:  [0x00-0xffff]
[    0.740585] pci_bus 0000:00: resource 1 mem: [0x000000-0xffffffffffffffff]
[    0.740587] pci_bus 0000:01: resource 0 io:  [0xd000-0xdfff]
[    0.740589] pci_bus 0000:01: resource 1 mem: [0xfd000000-0xfe7fffff]
[    0.740591] pci_bus 0000:01: resource 2 pref mem [0xce000000-0xdfffffff]
[    0.740593] pci_bus 0000:02: resource 0 io:  [0x1000-0x1fff]
[    0.740595] pci_bus 0000:02: resource 1 mem: [0xfe800000-0xfe9fffff]
[    0.740597] pci_bus 0000:02: resource 2 pref mem [0xc0000000-0xc01fffff]
[    0.740599] pci_bus 0000:03: resource 0 io:  [0xe000-0xefff]
[    0.740600] pci_bus 0000:03: resource 1 mem: [0xfea00000-0xfeafffff]
[    0.740602] pci_bus 0000:03: resource 2 pref mem [0xc0200000-0xc03fffff]
[    0.740604] pci_bus 0000:04: resource 1 mem: [0xfeb00000-0xfebfffff]
[    0.740606] pci_bus 0000:04: resource 3 io:  [0x00-0xffff]
[    0.740608] pci_bus 0000:04: resource 4 mem: [0x000000-0xffffffffffffffff]
[    0.740642] NET: Registered protocol family 2
[    0.740848] IP route cache hash table entries: 262144 (order: 9, 2097152 bytes)
[    0.742063] TCP established hash table entries: 524288 (order: 11, 8388608 bytes)
[    0.745397] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    0.745798] TCP: Hash tables configured (established 524288 bind 65536)
[    0.745800] TCP reno registered
[    0.745901] NET: Registered protocol family 1
[    0.746063] pci 0000:01:00.0: Boot video device
[    0.746374] Scanning for low memory corruption every 60 seconds
[    0.746494] audit: initializing netlink socket (disabled)
[    0.746503] type=2000 audit(1274574654.739:1): initialized
[    0.754230] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    0.755419] VFS: Disk quotas dquot_6.5.2
[    0.755462] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    0.755944] fuse init (API version 7.13)
[    0.756005] msgmni has been set to 15980
[    0.756296] alg: No test for stdrng (krng)
[    0.756342] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.756346] io scheduler noop registered
[    0.756347] io scheduler anticipatory registered
[    0.756348] io scheduler deadline registered
[    0.756375] io scheduler cfq registered (default)
[    0.756485]   alloc irq_desc for 24 on node -1
[    0.756487]   alloc kstat_irqs on node -1
[    0.756494] pcieport 0000:00:01.0: irq 24 for MSI/MSI-X
[    0.756499] pcieport 0000:00:01.0: setting latency timer to 64
[    0.756576]   alloc irq_desc for 25 on node -1
[    0.756577]   alloc kstat_irqs on node -1
[    0.756583] pcieport 0000:00:1c.0: irq 25 for MSI/MSI-X
[    0.756589] pcieport 0000:00:1c.0: setting latency timer to 64
[    0.756675]   alloc irq_desc for 26 on node -1
[    0.756677]   alloc kstat_irqs on node -1
[    0.756682] pcieport 0000:00:1c.1: irq 26 for MSI/MSI-X
[    0.756688] pcieport 0000:00:1c.1: setting latency timer to 64
[    0.756752] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.756768] Firmware did not grant requested _OSC control
[    0.756781] Firmware did not grant requested _OSC control
[    0.756802] Firmware did not grant requested _OSC control
[    0.756812] Firmware did not grant requested _OSC control
[    0.756823] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.756930] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0
[    0.756938] ACPI: Power Button [PWRB]
[    0.756973] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
[    0.756975] ACPI: Power Button [PWRF]
[    0.757575] ACPI: SSDT 00000000bffa0140 00235 (v01 DpgPmm  P001Ist 00000011 INTL 20051117)
[    0.757963] ACPI: SSDT 00000000bffa0a40 004B2 (v01  PmRef  P001Cst 00003001 INTL 20051117)
[    0.758278] Monitor-Mwait will be used to enter C-1 state
[    0.758319] Monitor-Mwait will be used to enter C-2 state
[    0.758326] Marking TSC unstable due to TSC halts in idle
[    0.758390] Switching to clocksource hpet
[    0.758402] processor LNXCPU:00: registered as cooling_device0
[    0.758876] ACPI: SSDT 00000000bffa0380 00235 (v01 DpgPmm  P002Ist 00000012 INTL 20051117)
[    0.759154] ACPI: SSDT 00000000bffa0f00 00085 (v01  PmRef  P002Cst 00003000 INTL 20051117)
[    0.759578] processor LNXCPU:01: registered as cooling_device1
[    0.759926] ACPI: SSDT 00000000bffa05c0 00235 (v01 DpgPmm  P003Ist 00000012 INTL 20051117)
[    0.760225] ACPI: SSDT 00000000bffa0f90 00085 (v01  PmRef  P003Cst 00003000 INTL 20051117)
[    0.760637] processor LNXCPU:02: registered as cooling_device2
[    0.760988] ACPI: SSDT 00000000bffa0800 00235 (v01 DpgPmm  P004Ist 00000012 INTL 20051117)
[    0.761279] ACPI: SSDT 00000000bffa1020 00085 (v01  PmRef  P004Cst 00003000 INTL 20051117)
[    0.773944] processor LNXCPU:03: registered as cooling_device3
[    0.779873] Linux agpgart interface v0.103
[    0.779909] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    0.780932] brd: module loaded
[    0.781305] loop: module loaded
[    0.781370] input: Macintosh mouse button emulation as /devices/virtual/input/input2
[    0.781682] Fixed MDIO Bus: probed
[    0.781706] PPP generic driver version 2.4.2
[    0.781730] tun: Universal TUN/TAP device driver, 1.6
[    0.781731] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.781787] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.781807]   alloc irq_desc for 18 on node -1
[    0.781809]   alloc kstat_irqs on node -1
[    0.781815] ehci_hcd 0000:00:1a.7: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.781846] ehci_hcd 0000:00:1a.7: setting latency timer to 64
[    0.781849] ehci_hcd 0000:00:1a.7: EHCI Host Controller
[    0.781884] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 1
[    0.781910] ehci_hcd 0000:00:1a.7: debug port 1
[    0.785803] ehci_hcd 0000:00:1a.7: cache line size of 32 is not supported
[    0.785818] ehci_hcd 0000:00:1a.7: irq 18, io mem 0xfcfdec00
[    0.802530] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00
[    0.802644] usb usb1: configuration #1 chosen from 1 choice
[    0.802668] hub 1-0:1.0: USB hub found
[    0.802677] hub 1-0:1.0: 6 ports detected
[    0.802735]   alloc irq_desc for 23 on node -1
[    0.802737]   alloc kstat_irqs on node -1
[    0.802742] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    0.802762] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    0.802765] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    0.802793] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 2
[    0.802817] ehci_hcd 0000:00:1d.7: debug port 1
[    0.806707] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
[    0.806723] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xfcfde800
[    0.822524] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    0.822634] usb usb2: configuration #1 chosen from 1 choice
[    0.822658] hub 2-0:1.0: USB hub found
[    0.822667] hub 2-0:1.0: 6 ports detected
[    0.822723] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.822738] uhci_hcd: USB Universal Host Controller Interface driver
[    0.822772] uhci_hcd 0000:00:1a.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.822780] uhci_hcd 0000:00:1a.0: setting latency timer to 64
[    0.822783] uhci_hcd 0000:00:1a.0: UHCI Host Controller
[    0.822812] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 3
[    0.822845] uhci_hcd 0000:00:1a.0: irq 16, io base 0x0000c880
[    0.822917] usb usb3: configuration #1 chosen from 1 choice
[    0.822937] hub 3-0:1.0: USB hub found
[    0.822942] hub 3-0:1.0: 2 ports detected
[    0.822976]   alloc irq_desc for 21 on node -1
[    0.822978]   alloc kstat_irqs on node -1
[    0.822982] uhci_hcd 0000:00:1a.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[    0.822987] uhci_hcd 0000:00:1a.1: setting latency timer to 64
[    0.822989] uhci_hcd 0000:00:1a.1: UHCI Host Controller
[    0.823015] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 4
[    0.823043] uhci_hcd 0000:00:1a.1: irq 21, io base 0x0000c800
[    0.823106] usb usb4: configuration #1 chosen from 1 choice
[    0.823123] hub 4-0:1.0: USB hub found
[    0.823128] hub 4-0:1.0: 2 ports detected
[    0.823159]   alloc irq_desc for 19 on node -1
[    0.823160]   alloc kstat_irqs on node -1
[    0.823164] uhci_hcd 0000:00:1a.2: PCI INT D -> GSI 19 (level, low) -> IRQ 19
[    0.823169] uhci_hcd 0000:00:1a.2: setting latency timer to 64
[    0.823171] uhci_hcd 0000:00:1a.2: UHCI Host Controller
[    0.823197] uhci_hcd 0000:00:1a.2: new USB bus registered, assigned bus number 5
[    0.823222] uhci_hcd 0000:00:1a.2: irq 19, io base 0x0000c480
[    0.823283] usb usb5: configuration #1 chosen from 1 choice
[    0.823303] hub 5-0:1.0: USB hub found
[    0.823308] hub 5-0:1.0: 2 ports detected
[    0.823341] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    0.823345] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    0.823347] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    0.823374] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 6
[    0.823394] uhci_hcd 0000:00:1d.0: irq 23, io base 0x0000c400
[    0.823454] usb usb6: configuration #1 chosen from 1 choice
[    0.823476] hub 6-0:1.0: USB hub found
[    0.823480] hub 6-0:1.0: 2 ports detected
[    0.823512] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    0.823516] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    0.823519] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    0.823541] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 7
[    0.823560] uhci_hcd 0000:00:1d.1: irq 19, io base 0x0000c080
[    0.823628] usb usb7: configuration #1 chosen from 1 choice
[    0.823645] hub 7-0:1.0: USB hub found
[    0.823649] hub 7-0:1.0: 2 ports detected
[    0.823683] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.823687] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    0.823690] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    0.823712] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 8
[    0.823734] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000c000
[    0.823800] usb usb8: configuration #1 chosen from 1 choice
[    0.823817] hub 8-0:1.0: USB hub found
[    0.823824] hub 8-0:1.0: 2 ports detected
[    0.823898] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f03:PS2M] at 0x60,0x64 irq 1,12
[    0.824249] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.824255] serio: i8042 AUX port at 0x60,0x64 irq 12
[    0.824347] mice: PS/2 mouse device common for all mice
[    0.824431] rtc_cmos 00:03: RTC can wake from S4
[    0.824463] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0
[    0.824483] rtc0: alarms up to one month, y3k, 114 bytes nvram, hpet irqs
[    0.824590] device-mapper: uevent: version 1.0.3
[    0.824683] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: [email]dm-devel@redhat.com[/email]
[    0.824838] device-mapper: multipath: version 1.1.0 loaded
[    0.824841] device-mapper: multipath round-robin: version 1.0.0 loaded
[    0.825183] cpuidle: using governor ladder
[    0.825306] cpuidle: using governor menu
[    0.825557] TCP cubic registered
[    0.825652] NET: Registered protocol family 10
[    0.825980] lo: Disabled Privacy Extensions
[    0.826185] NET: Registered protocol family 17
[    0.827106] PM: Resume from disk failed.
[    0.827116] registered taskstats version 1
[    0.827468]   Magic number: 10:196:507
[    0.827554] rtc_cmos 00:03: setting system clock to 2010-05-23 00:30:55 UTC (1274574655)
[    0.827557] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.827558] EDD information not available.
[    0.845831] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3
[    0.892919] Freeing initrd memory: 13718k freed
[    0.896809] Freeing unused kernel memory: 876k freed
[    0.896988] Write protecting the kernel read-only data: 7680k
[    0.911158] udev: starting version 151
[    0.927461] e1000e: Intel(R) PRO/1000 Network Driver - 1.0.2-k2
[    0.927465] e1000e: Copyright (c) 1999-2008 Intel Corporation.
[    0.927503]   alloc irq_desc for 20 on node -1
[    0.927505]   alloc kstat_irqs on node -1
[    0.927511] e1000e 0000:00:19.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    0.927519] e1000e 0000:00:19.0: setting latency timer to 64
[    0.927605]   alloc irq_desc for 27 on node -1
[    0.927606]   alloc kstat_irqs on node -1
[    0.927615] e1000e 0000:00:19.0: irq 27 for MSI/MSI-X
[    0.972566] [drm] Initialized drm 1.1.0 20060810
[    0.976405] ohci1394 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    0.976411] ohci1394 0000:03:00.0: setting latency timer to 64
[    0.995078] nouveau 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.995083] nouveau 0000:01:00.0: setting latency timer to 64
[    0.997320] [drm] nouveau 0000:01:00.0: Detected an NV50 generation card (0x0a5000a2)
[    0.998079] [drm] nouveau 0000:01:00.0: Attempting to load BIOS image from PRAMIN
[    1.041361] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[17]  MMIO=[feaff800-feafffff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[    1.064900] [drm] nouveau 0000:01:00.0: ... appears to be valid
[    1.064903] [drm] nouveau 0000:01:00.0: BIT BIOS found
[    1.064905] [drm] nouveau 0000:01:00.0: Bios version 70.16.0e.00
[    1.064907] [drm] nouveau 0000:01:00.0: Pointer to BIT loadval table invalid
[    1.064909] [drm] nouveau 0000:01:00.0: TMDS table revision 2.0 not currently supported
[    1.064911] [drm] nouveau 0000:01:00.0: Found Display Configuration Block version 4.0
[    1.064914] [drm] nouveau 0000:01:00.0: DCB connector table: VHER 0x40 5 16 4
[    1.064916] [drm] nouveau 0000:01:00.0:   0: 0x00001030: type 0x30 idx 0 tag 0x07
[    1.064918] [drm] nouveau 0000:01:00.0:   1: 0x00002161: type 0x61 idx 1 tag 0x08
[    1.064920] [drm] nouveau 0000:01:00.0:   2: 0x00000200: type 0x00 idx 2 tag 0xff
[    1.064922] [drm] nouveau 0000:01:00.0: Raw DCB entry 0: 02000300 00000000
[    1.064924] [drm] nouveau 0000:01:00.0: Raw DCB entry 1: 01000302 00020030
[    1.064926] [drm] nouveau 0000:01:00.0: Raw DCB entry 2: 01032310 00000000
[    1.064928] [drm] nouveau 0000:01:00.0: Raw DCB entry 3: 02021362 00020010
[    1.064936] [drm] nouveau 0000:01:00.0: Parsing VBIOS init table 0 at offset 0xCED3
[    1.073707] 0000:00:19.0: eth0: (PCI Express:2.5GB/s:Width x1) 00:25:11:59:d4:ca
[    1.073709] 0000:00:19.0: eth0: Intel(R) PRO/1000 Network Connection
[    1.073729] 0000:00:19.0: eth0: MAC: 7, PHY: 8, PBA No: ffffff-0ff
[    1.073918] ahci 0000:00:1f.2: version 3.0
[    1.073935] ahci 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    1.073977]   alloc irq_desc for 28 on node -1
[    1.073978]   alloc kstat_irqs on node -1
[    1.073987] ahci 0000:00:1f.2: irq 28 for MSI/MSI-X
[    1.073995] ahci 0000:00:1f.2: controller can't do SNTF, turning off CAP_SNTF
[    1.074034] ahci: SSS flag set, parallel bus scan disabled
[    1.074063] ahci 0000:00:1f.2: AHCI 0001.0200 32 slots 6 ports 3 Gbps 0x3f impl RAID mode
[    1.074065] ahci 0000:00:1f.2: flags: 64bit ncq stag pm led clo pio slum part ccc ems sxs 
[    1.074069] ahci 0000:00:1f.2: setting latency timer to 64
[    1.120075] [drm] nouveau 0000:01:00.0: 0xD1E3: Condition still not met after 20ms, skipping following opcodes
[    1.150022] [drm] nouveau 0000:01:00.0: 0xD20E: Condition still not met after 20ms, skipping following opcodes
[    1.150035] [drm] nouveau 0000:01:00.0: Parsing VBIOS init table 1 at offset 0xD38A
[    1.180084] scsi0 : ahci
[    1.180235] scsi1 : ahci
[    1.180327] scsi2 : ahci
[    1.180413] scsi3 : ahci
[    1.180506] scsi4 : ahci
[    1.180582] scsi5 : ahci
[    1.180722] ata1: SATA max UDMA/133 abar m2048@0xfcfde000 port 0xfcfde100 irq 28
[    1.180725] ata2: SATA max UDMA/133 abar m2048@0xfcfde000 port 0xfcfde180 irq 28
[    1.180727] ata3: SATA max UDMA/133 abar m2048@0xfcfde000 port 0xfcfde200 irq 28
[    1.180729] ata4: SATA max UDMA/133 abar m2048@0xfcfde000 port 0xfcfde280 irq 28
[    1.180732] ata5: SATA max UDMA/133 abar m2048@0xfcfde000 port 0xfcfde300 irq 28
[    1.180734] ata6: SATA max UDMA/133 abar m2048@0xfcfde000 port 0xfcfde380 irq 28
[    1.193789] usb 2-4: new high speed USB device using ehci_hcd and address 2
[    1.200033] [drm] nouveau 0000:01:00.0: Parsing VBIOS init table 2 at offset 0xE221
[    1.200042] [drm] nouveau 0000:01:00.0: Parsing VBIOS init table 3 at offset 0xE25F
[    1.261568] [drm] nouveau 0000:01:00.0: Parsing VBIOS init table 4 at offset 0xE43E
[    1.261570] [drm] nouveau 0000:01:00.0: Parsing VBIOS init table at offset 0xE4A3
[    1.290035] [drm] nouveau 0000:01:00.0: 0xE4A3: Condition still not met after 20ms, skipping following opcodes
[    1.290041] [drm] nouveau 0000:01:00.0: 0xBB95: parsing output script 0
[    1.290044] [drm] nouveau 0000:01:00.0: 0xBB95: parsing output script 0
[    1.364488] usb 2-4: configuration #1 chosen from 1 choice
[    1.369787] Initializing USB Mass Storage driver...
[    1.372585] scsi6 : SCSI emulation for USB Mass Storage devices
[    1.372684] usbcore: registered new interface driver usb-storage
[    1.372687] USB Mass Storage support registered.
[    1.372694] usb-storage: device found at 2
[    1.372695] usb-storage: waiting for device to settle before scanning
[    1.424575] [TTM] Zone  kernel: Available graphics memory: 4098338 kiB.
[    1.424577] [TTM] Zone   dma32: Available graphics memory: 2097152 kiB.
[    1.424589] [drm] nouveau 0000:01:00.0: 1024 MiB VRAM
[    1.438974] [drm] nouveau 0000:01:00.0: 512 MiB GART (aperture)
[    1.438979] mtrr: type mismatch for d0000000,10000000 old: write-back new: write-combining
[    1.439161] [drm] nouveau 0000:01:00.0: Allocating FIFO number 1
[    1.442144] [drm] nouveau 0000:01:00.0: nouveau_channel_alloc: initialised FIFO 1
[    1.442652] [drm] nouveau 0000:01:00.0: Detected a DAC output
[    1.442659] [drm] nouveau 0000:01:00.0: Detected a TMDS output
[    1.442660] [drm] nouveau 0000:01:00.0: Detected a DAC output
[    1.442662] [drm] nouveau 0000:01:00.0: Detected a TMDS output
[    1.442665] [drm] nouveau 0000:01:00.0: Detected a DVI-I connector
[    1.442706] [drm] nouveau 0000:01:00.0: Detected a VGA connector
[    1.442724] [drm] nouveau 0000:01:00.0: Detected a DVI-D connector
[    1.522535] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    1.551607] ata1.00: ATA-8: WDC WD10EADS-22M2B0, 01.00A01, max UDMA/133
[    1.551610] ata1.00: 1953525168 sectors, multi 0: LBA48 NCQ (depth 31/32), AA
[    1.553452] ata1.00: configured for UDMA/133
[    1.572607] scsi 0:0:0:0: Direct-Access     ATA      WDC WD10EADS-22M 01.0 PQ: 0 ANSI: 5
[    1.572735] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.572787] sd 0:0:0:0: [sda] 1953525168 512-byte logical blocks: (1.00 TB/931 GiB)
[    1.572823] sd 0:0:0:0: [sda] Write Protect is off
[    1.572825] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.572846] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.572954]  sda: sda1 sda2 sda3
[    1.584494] sd 0:0:0:0: [sda] Attached SCSI disk
[    1.642528] usb 4-2: new low speed USB device using uhci_hcd and address 2
[    1.782777] [drm] nouveau 0000:01:00.0: allocated 1280x1024 fb: 0x40250000, bo ffff880232039e00
[    1.782831] fb0: nouveaufb frame buffer device
[    1.782833] registered panic notifier
[    1.782837] [drm] Initialized nouveau 0.0.15 20090420 for 0000:01:00.0 on minor 0
[    1.814148] usb 4-2: configuration #1 chosen from 1 choice
[    1.821021] usbcore: registered new interface driver hiddev
[    1.822143] generic-usb: probe of 0003:0A48:4001.0001 failed with error -22
[    1.837333] input: USB Optical Mouse as /devices/pci0000:00/0000:00:1a.1/usb4/4-2/4-2:1.0/input/input4
[    1.837414] generic-usb 0003:0461:4D64.0002: input,hidraw0: USB HID v1.11 Mouse [USB Optical Mouse] on usb-0000:00:1a.1-2/input0
[    1.837430] usbcore: registered new interface driver usbhid
[    1.837432] usbhid: v2.6:USB HID core driver
[    2.322532] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    2.326645] ata2.00: ATAPI: HL-DT-ST DVDRAM GH41N, MN01, max UDMA/100, ATAPI AN
[    2.330979] ata2.00: configured for UDMA/100
[    2.352838] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[00001921ff3f2c88]
[    2.354822] scsi 1:0:0:0: CD-ROM            HL-DT-ST DVDRAM GH41N     MN01 PQ: 0 ANSI: 5
[    2.375757] sr0: scsi3-mmc drive: 40x/40x writer dvd-ram cd/rw xa/form2 cdda tray
[    2.375761] Uniform CD-ROM driver Revision: 3.20
[    2.375868] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    2.375925] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    2.730039] ata3: SATA link down (SStatus 0 SControl 300)
[    3.100044] ata4: SATA link down (SStatus 0 SControl 300)
[    3.480045] ata5: SATA link down (SStatus 0 SControl 300)
[    3.862540] ata6: SATA link down (SStatus 0 SControl 300)
[    3.884377] vga16fb: initializing
[    3.884381] vga16fb: mapped to 0xffff8800000a0000
[    3.884384] vga16fb: not registering due to another framebuffer present
[    3.889929] [drm] nouveau 0000:01:00.0: 0x1231: parsing clock script 0
[    3.890063] Console: switching to colour frame buffer device 160x64
[    4.330936] EXT4-fs (sda2): INFO: recovery required on readonly filesystem
[    4.330940] EXT4-fs (sda2): write access will be enabled during recovery
[    4.471185] EXT4-fs (sda2): orphan cleanup on readonly fs
[    4.471192] EXT4-fs (sda2): ext4_orphan_cleanup: deleting unreferenced inode 1966139
[    4.471237] EXT4-fs (sda2): ext4_orphan_cleanup: deleting unreferenced inode 1966138
[    4.471250] EXT4-fs (sda2): ext4_orphan_cleanup: deleting unreferenced inode 1966137
[    4.471264] EXT4-fs (sda2): 3 orphan inodes deleted
[    4.471266] EXT4-fs (sda2): recovery complete
[    4.744273] EXT4-fs (sda2): mounted filesystem with ordered data mode
[    6.370217] usb-storage: device scan complete
[    6.370797] scsi 6:0:0:0: Direct-Access     Generic  USB SD Reader    1.00 PQ: 0 ANSI: 0
[    6.371295] scsi 6:0:0:1: Direct-Access     Generic  USB CF Reader    1.01 PQ: 0 ANSI: 0
[    6.371804] scsi 6:0:0:2: Direct-Access     Generic  USB xD/SM Reader 1.02 PQ: 0 ANSI: 0
[    6.372426] scsi 6:0:0:3: Direct-Access     Generic  USB MS Reader    1.03 PQ: 0 ANSI: 0 CCS
[    6.372918] scsi 6:0:0:4: Direct-Access     Generic  Mini SD Reader   1.06 PQ: 0 ANSI: 0
[    6.373244] sd 6:0:0:0: Attached scsi generic sg2 type 0
[    6.373362] sd 6:0:0:1: Attached scsi generic sg3 type 0
[    6.373467] sd 6:0:0:2: Attached scsi generic sg4 type 0
[    6.373578] sd 6:0:0:3: Attached scsi generic sg5 type 0
[    6.373693] sd 6:0:0:4: Attached scsi generic sg6 type 0
[    6.377045] sd 6:0:0:0: [sdb] Attached SCSI removable disk
[    6.377665] sd 6:0:0:1: [sdc] Attached SCSI removable disk
[    6.378294] sd 6:0:0:2: [sdd] Attached SCSI removable disk
[    6.378912] sd 6:0:0:3: [sde] Attached SCSI removable disk
[    6.379544] sd 6:0:0:4: [sdf] Attached SCSI removable disk
[   10.317207] udev: starting version 151
[   10.326711] lp: driver loaded but no devices found
[   10.412035] Linux video capture interface: v2.00
[   10.437480] type=1505 audit(1274589065.102:2):  operation="profile_load" pid=663 name="/sbin/dhclient3"
[   10.437986] type=1505 audit(1274589065.102:3):  operation="profile_load" pid=663 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[   10.438259] type=1505 audit(1274589065.102:4):  operation="profile_load" pid=663 name="/usr/lib/connman/scripts/dhclient-script"
[   10.462881] cfg80211: Calling CRDA to update world regulatory domain
[   10.483939] cx23885 driver version 0.0.2 loaded
[   10.483987] cx23885 0000:02:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   10.483990] cx23885[0]: Your board isn't known (yet) to the driver.
[   10.483991] cx23885[0]: Try to pick one of the existing card configs via
[   10.483992] cx23885[0]: card=<n> insmod option.  Updating to the latest
[   10.483993] cx23885[0]: version might help as well.
[   10.483995] cx23885[0]: Here is a list of valid choices for the card=<n> insmod option:
[   10.483996] cx23885[0]:    card=0 -> UNKNOWN/GENERIC
[   10.483998] cx23885[0]:    card=1 -> Hauppauge WinTV-HVR1800lp
[   10.484000] cx23885[0]:    card=2 -> Hauppauge WinTV-HVR1800
[   10.484001] cx23885[0]:    card=3 -> Hauppauge WinTV-HVR1250
[   10.484003] cx23885[0]:    card=4 -> DViCO FusionHDTV5 Express
[   10.484004] cx23885[0]:    card=5 -> Hauppauge WinTV-HVR1500Q
[   10.484006] cx23885[0]:    card=6 -> Hauppauge WinTV-HVR1500
[   10.484007] cx23885[0]:    card=7 -> Hauppauge WinTV-HVR1200
[   10.484009] cx23885[0]:    card=8 -> Hauppauge WinTV-HVR1700
[   10.484010] cx23885[0]:    card=9 -> Hauppauge WinTV-HVR1400
[   10.484012] cx23885[0]:    card=10 -> DViCO FusionHDTV7 Dual Express
[   10.484014] cx23885[0]:    card=11 -> DViCO FusionHDTV DVB-T Dual Express
[   10.484015] cx23885[0]:    card=12 -> Leadtek Winfast PxDVR3200 H
[   10.484017] cx23885[0]:    card=13 -> Compro VideoMate E650F
[   10.484018] cx23885[0]:    card=14 -> TurboSight TBS 6920
[   10.484020] cx23885[0]:    card=15 -> TeVii S470
[   10.484021] cx23885[0]:    card=16 -> DVBWorld DVB-S2 2005
[   10.484023] cx23885[0]:    card=17 -> NetUP Dual DVB-S2 CI
[   10.484025] cx23885[0]:    card=18 -> Hauppauge WinTV-HVR1270
[   10.484026] cx23885[0]:    card=19 -> Hauppauge WinTV-HVR1275
[   10.484028] cx23885[0]:    card=20 -> Hauppauge WinTV-HVR1255
[   10.484029] cx23885[0]:    card=21 -> Hauppauge WinTV-HVR1210
[   10.484031] cx23885[0]:    card=22 -> Mygica X8506 DMB-TH
[   10.484032] cx23885[0]:    card=23 -> Magic-Pro ProHDTV Extreme 2
[   10.484034] cx23885[0]:    card=24 -> Hauppauge WinTV-HVR1850
[   10.484035] cx23885[0]:    card=25 -> Compro VideoMate E800
[   10.484128] CORE cx23885[0]: subsystem: 12ab:d575, board: UNKNOWN/GENERIC [card=0,autodetected]
[   10.491111] ath5k 0000:04:02.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[   10.491161] ath5k 0000:04:02.0: registered as 'phy0'
[   10.501891] cfg80211: World regulatory domain updated:
[   10.501894] 	(start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   10.501897] 	(2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   10.501899] 	(2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   10.501901] 	(2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   10.501902] 	(5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   10.501904] 	(5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   10.537220]   alloc irq_desc for 22 on node -1
[   10.537223]   alloc kstat_irqs on node -1
[   10.537230] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   10.537284] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   10.611799] cx23885_dev_checkrevision() Hardware revision = 0xa5
[   10.611808] cx23885[0]/0: found at 0000:02:00.0, rev: 4, irq: 16, latency: 0, mmio: 0xfe800000
[   10.611814] cx23885 0000:02:00.0: setting latency timer to 64
[   10.611818] IRQ 16/cx23885[0]: IRQF_DISABLED is not guaranteed on shared IRQs
[   11.083000] ath: EEPROM regdomain: 0x65
[   11.083003] ath: EEPROM indicates we should expect a direct regpair map
[   11.083005] ath: Country alpha2 being used: 00
[   11.083006] ath: Regpair used: 0x65
[   11.087084] phy0: Selected rate control algorithm 'minstrel'
[   11.087574] ath5k phy0: Atheros AR5414 chip found (MAC: 0xa2, PHY: 0x61)
[   11.621381] hda-intel: azx_get_response timeout, switching to polling mode: last cmd=0x300f0000
[   12.631260] hda-intel: Codec #3 probe error; disabling it...
[   12.776855] hda_codec: ALC888: BIOS auto-probing.
[   12.778285] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:1b.0/input/input5
[   12.786399] HDA Intel 0000:01:00.1: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   12.786403] hda_intel: Disable MSI for Nvidia chipset
[   12.786464] HDA Intel 0000:01:00.1: setting latency timer to 64
[   14.063847] EXT4-fs (sda3): mounted filesystem with ordered data mode
[   14.176894] type=1505 audit(1274589068.842:5):  operation="profile_load" pid=1003 name="/usr/share/gdm/guest-session/Xsession"
[   14.178301] type=1505 audit(1274589068.842:6):  operation="profile_replace" pid=1004 name="/sbin/dhclient3"
[   14.178807] type=1505 audit(1274589068.842:7):  operation="profile_replace" pid=1004 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[   14.179081] type=1505 audit(1274589068.842:8):  operation="profile_replace" pid=1004 name="/usr/lib/connman/scripts/dhclient-script"
[   14.181551] type=1505 audit(1274589068.852:9):  operation="profile_load" pid=1005 name="/usr/bin/evince"
[   14.187977] type=1505 audit(1274589068.852:10):  operation="profile_load" pid=1005 name="/usr/bin/evince-previewer"
[   14.191944] type=1505 audit(1274589068.862:11):  operation="profile_load" pid=1005 name="/usr/bin/evince-thumbnailer"
[   14.232683] e1000e 0000:00:19.0: irq 27 for MSI/MSI-X
[   14.292624] e1000e 0000:00:19.0: irq 27 for MSI/MSI-X
[   14.293473] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   14.334462] vboxdrv: Trying to deactivate the NMI watchdog permanently...
[   14.334465] vboxdrv: Warning: 2.6.31+ kernel detected. Most likely the hardware performance
[   14.334466] vboxdrv: counter framework which can generate NMIs is active. You have to prevent
[   14.334467] vboxdrv: the usage of hardware performance counters by
[   14.334468] vboxdrv:   echo 2 > /proc/sys/kernel/perf_counter_paranoid
[   14.334471] vboxdrv: Found 4 processor cores.
[   14.334631] VBoxDrv: dbg - g_abExecMemory=ffffffffa03f5a20
[   14.334680] vboxdrv: fAsync=0 offMin=0x4a8 offMax=0x1ba8
[   14.335042] vboxdrv: TSC mode is 'synchronous', kernel timer mode is 'normal'.
[   14.335044] vboxdrv: Successfully loaded version 3.1.6_OSE (interface 0x00100001).
[/quote]

and here's my lspci output

[quote]
00:00.0 Host bridge: Intel Corporation 4 Series Chipset DRAM Controller (rev 03)
00:01.0 PCI bridge: Intel Corporation 4 Series Chipset PCI Express Root Port (rev 03)
00:19.0 Ethernet controller: Intel Corporation 82567V-2 Gigabit Network Connection
00:1a.0 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #4
00:1a.1 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #5
00:1a.2 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #6
00:1a.7 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB2 EHCI Controller #2
00:1b.0 Audio device: Intel Corporation 82801JI (ICH10 Family) HD Audio Controller
00:1c.0 PCI bridge: Intel Corporation 82801JI (ICH10 Family) PCI Express Root Port 1
00:1c.1 PCI bridge: Intel Corporation 82801JI (ICH10 Family) PCI Express Port 2
00:1d.0 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #1
00:1d.1 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #2
00:1d.2 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #3
00:1d.7 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB2 EHCI Controller #1
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 90)
00:1f.0 ISA bridge: Intel Corporation 82801JIR (ICH10R) LPC Interface Controller
00:1f.2 RAID bus controller: Intel Corporation 82801 SATA RAID Controller
00:1f.3 SMBus: Intel Corporation 82801JI (ICH10 Family) SMBus Controller
01:00.0 VGA compatible controller: nVidia Corporation GT216 [GeForce GT 220] (rev a2)
01:00.1 Audio device: nVidia Corporation High Definition Audio Controller (rev a1)
02:00.0 Multimedia video controller: Conexant Systems, Inc. CX23885 PCI Video and Audio Decoder (rev 04)
03:00.0 FireWire (IEEE 1394): VIA Technologies, Inc. Device 3403
04:02.0 Ethernet controller: Atheros Communications Inc. AR5413 802.11abg NIC (rev 01)

```

I'm guessing it's a hardware issue, but I really don't know.

Any assistance would be greatly appreciated.

---

### Post by shadylookin on 2010-05-23
It happened again at about 2:50pm

```
May 23 12:40:19 bdt os-prober: debug: running /usr/lib/os-probes/mounted/10freedos on mounted /dev/sda3
May 23 12:40:19 bdt 10freedos: debug: /dev/sda3 is not a FAT partition: exiting
May 23 12:40:19 bdt os-prober: debug: running /usr/lib/os-probes/mounted/10qnx on mounted /dev/sda3
May 23 12:40:19 bdt 10qnx: debug: /dev/sda3 is not a QNX4 partition: exiting
May 23 12:40:19 bdt os-prober: debug: running /usr/lib/os-probes/mounted/20macosx on mounted /dev/sda3
May 23 12:40:19 bdt macosx-prober: debug: /dev/sda3 is not an HFS+ partition: exiting
May 23 12:40:19 bdt os-prober: debug: running /usr/lib/os-probes/mounted/20microsoft on mounted /dev/sda3
May 23 12:40:19 bdt 20microsoft: debug: /dev/sda3 is not a MS partition: exiting
May 23 12:40:19 bdt os-prober: debug: running /usr/lib/os-probes/mounted/30utility on mounted /dev/sda3
May 23 12:40:19 bdt 30utility: debug: /dev/sda3 is not a FAT partition: exiting
May 23 12:40:19 bdt os-prober: debug: running /usr/lib/os-probes/mounted/40lsb on mounted /dev/sda3
May 23 12:40:19 bdt os-prober: debug: running /usr/lib/os-probes/mounted/70hurd on mounted /dev/sda3
May 23 12:40:19 bdt os-prober: debug: running /usr/lib/os-probes/mounted/80minix on mounted /dev/sda3
May 23 12:40:19 bdt os-prober: debug: running /usr/lib/os-probes/mounted/90linux-distro on mounted /dev/sda3
May 23 12:40:19 bdt os-prober: debug: running /usr/lib/os-probes/mounted/90solaris on mounted /dev/sda3
May 23 12:47:44 bdt kernel: [  944.538528] Either the lower file is not in a valid eCryptfs format, or the key could not be retrieved. Plaintext passthrough mode is not enabled; returning -EIO
May 23 12:56:25 bdt sudo: pam_sm_authenticate: Called
May 23 12:56:25 bdt sudo: pam_sm_authenticate: username = [bpoconner]
May 23 12:56:25 bdt sudo: pam_sm_authenticate: /home/bpoconner is already mounted
May 23 12:56:29 bdt kernel: [ 1468.788857] alg: No test for xts(twofish) (xts(twofish-generic))
May 23 12:56:29 bdt kernel: [ 1469.021072] alg: No test for xts(serpent) (xts(serpent-generic))
May 23 12:56:29 bdt kernel: [ 1469.093250] kjournald starting.  Commit interval 5 seconds
May 23 12:56:29 bdt kernel: [ 1469.093260] EXT3-fs warning: maximal mount count reached, running e2fsck is recommended
May 23 12:56:29 bdt kernel: [ 1469.093522] EXT3 FS on dm-1, internal journal
May 23 12:56:29 bdt kernel: [ 1469.093525] EXT3-fs: recovery complete.
May 23 12:56:29 bdt kernel: [ 1469.093529] EXT3-fs: mounted filesystem with ordered data mode.
May 23 13:20:30 bdt kernel: [ 2910.205344] ath5k phy0: unsupported jumbo
May 23 13:35:49 bdt gnome-screensaver-dialog: pam_sm_authenticate: Called
May 23 13:35:49 bdt gnome-screensaver-dialog: pam_sm_authenticate: username = [bpoconner]
May 23 13:35:49 bdt gnome-screensaver-dialog: pam_sm_authenticate: /home/bpoconner is already mounted
May 23 14:45:48 bdt gnome-screensaver-dialog: pam_sm_authenticate: Called
May 23 14:45:48 bdt gnome-screensaver-dialog: pam_sm_authenticate: username = [bpoconner]
May 23 14:45:48 bdt gnome-screensaver-dialog: pam_sm_authenticate: /home/bpoconner is already mounted
May 23 14:46:57 bdt pulseaudio[1983]: ratelimit.c: 12 events suppressed
May 23 14:47:18 bdt kernel: [ 8118.611916] ath5k phy0: unsupported jumbo
```

Anyone know whats going on?

---

