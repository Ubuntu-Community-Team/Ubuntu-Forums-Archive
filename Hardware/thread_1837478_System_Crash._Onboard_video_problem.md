---
title: "System Crash. Onboard video problem?"
date: 2011-09-01
forum: Hardware
---

### Post by oblador on 2011-09-01
Hi, 

I'm running Ubuntu 11.04, kernel 2.6.38.11, Gnome 2.32.1, Unity 3d.

All of sudden I had a system crash. I was browsing the web, typping in Libre Office Writter... 
I was doing nothing exceptional, but the VirtualBox the I had just loaded.

The screen went black, the keyboard didn't answer, I tried to Ctrl-Alt-F1, F2 and nothing happened... I tried to Ctrl-Alt-Del, again, nothing.

[B][COLOR="Black"]My onboard video is Intel 965.[/COLOR]
[/B]

Is it a video related problem?
Is it related to the video driver?



Here is part of my syslog (at least what I think that matters):

```
Sep  1 18:17:01 lagreca-pc CRON[2116]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Sep  1 18:50:21 lagreca-pc kernel: [ 2960.795789] warning: `VirtualBox' uses 32-bit capabilities (legacy support in use)
Sep  1 18:51:51 lagreca-pc kernel: [ 3050.916150] [drm:i915_hangcheck_elapsed] *ERROR* Hangcheck timer elapsed... GPU hung
Sep  1 18:51:51 lagreca-pc kernel: [ 3050.917837] [drm:i915_do_wait_request] *ERROR* i915_do_wait_request returns -11 (awaiting 606559 at 606541, next 606560)
Sep  1 18:54:01 lagreca-pc kernel: imklog 4.6.4, log source = /proc/kmsg started.
Sep  1 18:54:01 lagreca-pc rsyslogd: [origin software="rsyslogd" swVersion="4.6.4" x-pid="732" x-info="http://www.rsyslog.com"] (re)start
Sep  1 18:54:01 lagreca-pc rsyslogd: rsyslogd's groupid changed to 103
Sep  1 18:54:01 lagreca-pc rsyslogd: rsyslogd's userid changed to 101
Sep  1 18:54:01 lagreca-pc rsyslogd-2039: Could no open output pipe '/dev/xconsole' [try http://www.rsyslog.com/e/2039 ]
Sep  1 18:54:01 lagreca-pc kernel: [    0.000000] Initializing cgroup subsys cpuset
Sep  1 18:54:01 lagreca-pc kernel: [    0.000000] Initializing cgroup subsys cpu
Sep  1 18:54:01 lagreca-pc kernel: [    0.000000] Linux version 2.6.38-11-generic (buildd@rothera) (gcc version 4.5.2 (Ubuntu/Linaro 4.5.2-8ubuntu4) ) #48-Ubuntu SMP Fri Jul 29 19:05:14 UTC 2011 (Ubuntu 2.6.38-11.48-generic 2.6.38.8)
Sep  1 18:54:01 lagreca-pc kernel: [    0.000000] BIOS-provided physical RAM map:
Sep  1 18:54:01 lagreca-pc kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f000 (usable)
Sep  1 18:54:01 lagreca-pc kernel: [    0.000000]  BIOS-e820: 000000000009f000 - 00000000000a0000 (reserved)
Sep  1 18:54:01 lagreca-pc kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 000000007f66d800 (usable)
Sep  1 18:54:01 lagreca-pc kernel: [    0.000000]  BIOS-e820: 000000007f66d800 - 0000000080000000 (reserved)
Sep  1 18:54:01 lagreca-pc kernel: [    0.000000]  BIOS-e820: 00000000f8000000 - 00000000fc000000 (reserved)
Sep  1 18:54:01 lagreca-pc kernel: [    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
Sep  1 18:54:01 lagreca-pc kernel: [    0.000000]  BIOS-e820: 00000000fed18000 - 00000000fed1c000 (reserved)
Sep  1 18:54:01 lagreca-pc kernel: [    0.000000]  BIOS-e820: 00000000fed20000 - 00000000fed90000 (reserved)
Sep  1 18:54:01 lagreca-pc kernel: [    0.000000]  BIOS-e820: 00000000feda0000 - 00000000feda6000 (reserved)
Sep  1 18:54:01 lagreca-pc kernel: [    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee10000 (reserved)
Sep  1 18:54:01 lagreca-pc kernel: [    0.000000]  BIOS-e820: 00000000ffe00000 - 0000000100000000 (reserved)
Sep  1 18:54:01 lagreca-pc kernel: [    0.000000] Notice: NX (Execute Disable) protection cannot be enabled in hardware: non-PAE kernel!
Sep  1 18:54:01 lagreca-pc kernel: [    0.000000] NX (Execute Disable) protection: approximated by x86 segment limits
Sep  1 18:54:01 lagreca-pc kernel: [    0.000000] DMI 2.4 present.
Sep  1 18:54:01 lagreca-pc kernel: [    0.000000] DMI: Dell Inc. Inspiron 1525                   /0D109D, BIOS A13 06/27/2008
Sep  1 18:54:01 lagreca-pc kernel: [    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
Sep  1 18:54:01 lagreca-pc kernel: [    0.000000] e820 remove range: 00000000000a0000 - 0000000000100000 (usable)
Sep  1 18:54:01 lagreca-pc kernel: [    0.000000] last_pfn = 0x7f66d max_arch_pfn = 0x100000
Sep  1 18:54:01 lagreca-pc kernel: [    0.000000] MTRR default type: uncachable
Sep  1 18:54:01 lagreca-pc kernel: [    0.000000] MTRR fixed ranges enabled:
Sep  1 18:54:01 lagreca-pc kernel: [    0.000000]   00000-9FFFF write-back
Sep  1 18:54:01 lagreca-pc kernel: [    0.000000]   A0000-BFFFF uncachable
Sep  1 18:54:01 lagreca-pc kernel: [    0.000000]   C0000-CFFFF write-protect
Sep  1 18:54:01 lagreca-pc kernel: [    0.000000]   D0000-EFFFF uncachable
Sep  1 18:54:01 lagreca-pc kernel: [    0.000000]   F0000-FFFFF write-protect
Sep  1 18:54:01 lagreca-pc kernel: [    0.000000] MTRR variable ranges enabled:
Sep  1 18:54:01 lagreca-pc kernel: [    0.000000]   0 base 000000000 mask F80000000 write-back
Sep  1 18:54:01 lagreca-pc kernel: [    0.000000]   1 base 07F800000 mask FFF800000 uncachable
Sep  1 18:54:01 lagreca-pc kernel: [    0.000000]   2 base 07F700000 mask FFFF00000 uncachable
Sep  1 18:54:01 lagreca-pc kernel: [    0.000000]   3 disabled
Sep  1 18:54:01 lagreca-pc kernel: [    0.000000]   4 disabled
Sep  1 18:54:01 lagreca-pc kernel: [    0.000000]   5 disabled
Sep  1 18:54:01 lagreca-pc kernel: [    0.000000]   6 disabled
Sep  1 18:54:01 lagreca-pc kernel: [    0.000000]   7 disabled
Sep  1 18:54:01 lagreca-pc kernel: [    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
Sep  1 18:54:01 lagreca-pc kernel: [    0.000000] initial memory mapped : 0 - 01c00000
Sep  1 18:54:01 lagreca-pc kernel: [    0.000000] init_memory_mapping: 0000000000000000-00000000377fe000
Sep  1 18:54:01 lagreca-pc kernel: [    0.000000]  0000000000 - 0000400000 page 4k
Sep  1 18:54:01 lagreca-pc kernel: [    0.000000]  0000400000 - 0037400000 page 2M
Sep  1 18:54:01 lagreca-pc kernel: [    0.000000]  0037400000 - 00377fe000 page 4k
Sep  1 18:54:01 lagreca-pc kernel: [    0.000000] kernel direct mapping tables up to 377fe000 @ 1bfb000-1c00000
Sep  1 18:54:01 lagreca-pc kernel: [    0.000000] RAMDISK: 36768000 - 373ac000
Sep  1 18:54:01 lagreca-pc kernel: [    0.000000] ACPI: RSDP 000fbc60 00024 (v02 DELL  )
Sep  1 18:54:01 lagreca-pc kernel: [    0.000000] ACPI: XSDT 7f66f200 00064 (v01 DELL    M08     27D8061B ASL  00000061)
Sep  1 18:54:01 lagreca-pc kernel: [    0.000000] ACPI: FACP 7f66f09c 000F4 (v04 DELL    M08     27D8061B ASL  00000061)
Sep  1 18:54:01 lagreca-pc kernel: [    0.000000] ACPI: DSDT 7f66f800 05477 (v02 INT430 SYSFexxx 00001001 INTL 20050624)
Sep  1 18:54:01 lagreca-pc kernel: [    0.000000] ACPI: FACS 7f67e000 00040
Sep  1 18:54:01 lagreca-pc kernel: [    0.000000] ACPI: HPET 7f66f300 00038 (v01 DELL    M08     00000001 ASL  00000061)
Sep  1 18:54:01 lagreca-pc kernel: [    0.000000] ACPI: APIC 7f66f400 00068 (v01 DELL    M08     27D8061B ASL  00000047)
Sep  1 18:54:01 lagreca-pc kernel: [    0.000000] ACPI: MCFG 7f66f3c0 0003E (v16 DELL    M08     27D8061B ASL  00000061)
Sep  1 18:54:01 lagreca-pc kernel: [    0.000000] ACPI: SLIC 7f66f49c 00176 (v01 DELL    M08     27D8061B ASL  00000061)
Sep  1 18:54:01 lagreca-pc kernel: [    0.000000] ACPI: OSFR 7f66ea00 0002C (v01 DELL    M08     27D8061B ASL  00000061)
Sep  1 18:54:01 lagreca-pc kernel: [    0.000000] ACPI: BOOT 7f66efc0 00028 (v01 DELL    M08     27D8061B ASL  00000061)
Sep  1 18:54:01 lagreca-pc kernel: [    0.000000] ACPI: SSDT 7f66d9c0 004CC (v01  PmRef    CpuPm 00003000 INTL 20050624)
Sep  1 18:54:01 lagreca-pc kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Sep  1 18:54:01 lagreca-pc kernel: [    0.000000] 1150MB HIGHMEM available.
Sep  1 18:54:01 lagreca-pc kernel: [    0.000000] 887MB LOWMEM available.
Sep  1 18:54:01 lagreca-pc kernel: [    0.000000]   mapped low ram: 0 - 377fe000
Sep  1 18:54:01 lagreca-pc kernel: [    0.000000]   low ram: 0 - 377fe000
Sep  1 18:54:01 lagreca-pc kernel: [    0.000000] Zone PFN ranges:
Sep  1 18:54:01 lagreca-pc kernel: [    0.000000]   DMA      0x00000010 -> 0x00001000
Sep  1 18:54:01 lagreca-pc kernel: [    0.000000]   Normal   0x00001000 -> 0x000377fe
Sep  1 18:54:01 lagreca-pc kernel: [    0.000000]   HighMem  0x000377fe -> 0x0007f66d
Sep  1 18:54:01 lagreca-pc kernel: [    0.000000] Movable zone start PFN for each node
Sep  1 18:54:01 lagreca-pc kernel: [    0.000000] early_node_map[2] active PFN ranges
Sep  1 18:54:01 lagreca-pc kernel: [    0.000000]     0: 0x00000010 -> 0x0000009f
Sep  1 18:54:01 lagreca-pc kernel: [    0.000000]     0: 0x00000100 -> 0x0007f66d
Sep  1 18:54:01 lagreca-pc kernel: [    0.000000] On node 0 totalpages: 521724
Sep  1 18:54:01 lagreca-pc kernel: [    0.000000] free_area_init_node: node 0, pgdat c1784180, node_mem_map f5778200
Sep  1 18:54:01 lagreca-pc kernel: [    0.000000]   DMA zone: 32 pages used for memmap
Sep  1 18:54:01 lagreca-pc kernel: [    0.000000]   DMA zone: 0 pages reserved
Sep  1 18:54:01 lagreca-pc kernel: [    0.000000]   DMA zone: 3951 pages, LIFO batch:0
Sep  1 18:54:01 lagreca-pc kernel: [    0.000000]   Normal zone: 1744 pages used for memmap
Sep  1 18:54:01 lagreca-pc kernel: [    0.000000]   Normal zone: 221486 pages, LIFO batch:31
Sep  1 18:54:01 lagreca-pc kernel: [    0.000000]   HighMem zone: 2301 pages used for memmap
Sep  1 18:54:01 lagreca-pc kernel: [    0.000000]   HighMem zone: 292210 pages, LIFO batch:31
Sep  1 18:54:01 lagreca-pc kernel: [    0.000000] Using APIC driver default
Sep  1 18:54:01 lagreca-pc kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x1008
Sep  1 18:54:01 lagreca-pc kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Sep  1 18:54:01 lagreca-pc kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
Sep  1 18:54:01 lagreca-pc kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
Sep  1 18:54:01 lagreca-pc kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
Sep  1 18:54:01 lagreca-pc kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
Sep  1 18:54:01 lagreca-pc kernel: [    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
Sep  1 18:54:01 lagreca-pc kernel: [    0.000000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
Sep  1 18:54:01 lagreca-pc kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
Sep  1 18:54:01 lagreca-pc kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
Sep  1 18:54:01 lagreca-pc kernel: [    0.000000] ACPI: IRQ0 used by override.
Sep  1 18:54:01 lagreca-pc kernel: [    0.000000] ACPI: IRQ2 used by override.
Sep  1 18:54:01 lagreca-pc kernel: [    0.000000] ACPI: IRQ9 used by override.
Sep  1 18:54:01 lagreca-pc kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
Sep  1 18:54:01 lagreca-pc kernel: [    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
Sep  1 18:54:01 lagreca-pc kernel: [    0.000000] SMP: Allowing 2 CPUs, 0 hotplug CPUs
Sep  1 18:54:01 lagreca-pc kernel: [    0.000000] nr_irqs_gsi: 40
Sep  1 18:54:01 lagreca-pc kernel: [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
Sep  1 18:54:01 lagreca-pc kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 0000000000100000
Sep  1 18:54:01 lagreca-pc kernel: [    0.000000] Allocating PCI resources starting at 80000000 (gap: 80000000:78000000)
Sep  1 18:54:01 lagreca-pc kernel: [    0.000000] Booting paravirtualized kernel on bare hardware
Sep  1 18:54:01 lagreca-pc kernel: [    0.000000] setup_percpu: NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:2 nr_node_ids:1
Sep  1 18:54:01 lagreca-pc kernel: [    0.000000] PERCPU: Embedded 13 pages/cpu @f5000000 s28800 r0 d24448 u2097152
Sep  1 18:54:01 lagreca-pc kernel: [    0.000000] pcpu-alloc: s28800 r0 d24448 u2097152 alloc=1*4194304
Sep  1 18:54:01 lagreca-pc kernel: [    0.000000] pcpu-alloc: [0] 0 1 
Sep  1 18:54:01 lagreca-pc kernel: [    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 517647
Sep  1 18:54:01 lagreca-pc kernel: [    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.38-11-generic root=UUID=b51b98c2-2566-4e5f-a510-fe28f77f9de2 ro quiet splash vt.handoff=7
Sep  1 18:54:01 lagreca-pc kernel: [    0.000000] PID hash table entries: 4096 (order: 2, 16384 bytes)
Sep  1 18:54:01 lagreca-pc kernel: [    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
Sep  1 18:54:01 lagreca-pc kernel: [    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
Sep  1 18:54:01 lagreca-pc kernel: [    0.000000] Initializing CPU#0
Sep  1 18:54:01 lagreca-pc kernel: [    0.000000] allocated 10436420 bytes of page_cgroup
Sep  1 18:54:01 lagreca-pc kernel: [    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
Sep  1 18:54:01 lagreca-pc kernel: [    0.000000] Initializing HighMem for node 0 (000377fe:0007f66d)
Sep  1 18:54:01 lagreca-pc kernel: [    0.000000] Memory: 2037508k/2087348k available (5190k kernel code, 49388k reserved, 2538k data, 700k init, 1178044k highmem)
Sep  1 18:54:01 lagreca-pc kernel: [    0.000000] virtual kernel memory layout:
Sep  1 18:54:01 lagreca-pc kernel: [    0.000000]     fixmap  : 0xfff16000 - 0xfffff000   ( 932 kB)
Sep  1 18:54:01 lagreca-pc kernel: [    0.000000]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
Sep  1 18:54:01 lagreca-pc kernel: [    0.000000]     vmalloc : 0xf7ffe000 - 0xff7fe000   ( 120 MB)
Sep  1 18:54:01 lagreca-pc kernel: [    0.000000]     lowmem  : 0xc0000000 - 0xf77fe000   ( 887 MB)
Sep  1 18:54:01 lagreca-pc kernel: [    0.000000]       .init : 0xc178d000 - 0xc183c000   ( 700 kB)
Sep  1 18:54:01 lagreca-pc kernel: [    0.000000]       .data : 0xc1511ba1 - 0xc178c500   (2538 kB)
Sep  1 18:54:01 lagreca-pc kernel: [    0.000000]       .text : 0xc1000000 - 0xc1511ba1   (5190 kB)
Sep  1 18:54:01 lagreca-pc kernel: [    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
Sep  1 18:54:01 lagreca-pc kernel: [    0.000000] SLUB: Genslabs=15, HWalign=64, Order=0-3, MinObjects=0, CPUs=2, Nodes=1
Sep  1 18:54:01 lagreca-pc kernel: [    0.000000] Hierarchical RCU implementation.
Sep  1 18:54:01 lagreca-pc kernel: [    0.000000] 	RCU dyntick-idle grace-period acceleration is enabled.
Sep  1 18:54:01 lagreca-pc kernel: [    0.000000] 	RCU-based detection of stalled CPUs is disabled.
Sep  1 18:54:01 lagreca-pc kernel: [    0.000000] NR_IRQS:2304 nr_irqs:512 16
Sep  1 18:54:01 lagreca-pc kernel: [    0.000000] CPU 0 irqstacks, hard=f4008000 soft=f400a000
Sep  1 18:54:01 lagreca-pc kernel: [    0.000000] Extended CMOS year: 2000
Sep  1 18:54:01 lagreca-pc kernel: [    0.000000] vt handoff: transparent VT on vt#7
Sep  1 18:54:01 lagreca-pc kernel: [    0.000000] Console: colour dummy device 80x25
Sep  1 18:54:01 lagreca-pc kernel: [    0.000000] console [tty0] enabled
Sep  1 18:54:01 lagreca-pc kernel: [    0.000000] hpet clockevent registered
Sep  1 18:54:01 lagreca-pc kernel: [    0.000000] Fast TSC calibration using PIT
Sep  1 18:54:01 lagreca-pc kernel: [    0.000000] Detected 1995.093 MHz processor.
Sep  1 18:54:01 lagreca-pc kernel: [    0.004003] Calibrating delay loop (skipped), value calculated using timer frequency.. 3990.18 BogoMIPS (lpj=7980372)
Sep  1 18:54:01 lagreca-pc kernel: [    0.004008] pid_max: default: 32768 minimum: 301
Sep  1 18:54:01 lagreca-pc kernel: [    0.004033] Security Framework initialized
Sep  1 18:54:01 lagreca-pc kernel: [    0.004049] AppArmor: AppArmor initialized
Sep  1 18:54:01 lagreca-pc kernel: [    0.004051] Yama: becoming mindful.
Sep  1 18:54:01 lagreca-pc kernel: [    0.004112] Mount-cache hash table entries: 512
Sep  1 18:54:01 lagreca-pc kernel: [    0.004257] Initializing cgroup subsys ns
Sep  1 18:54:01 lagreca-pc kernel: [    0.004262] ns_cgroup deprecated: consider using the 'clone_children' flag without the ns_cgroup.
Sep  1 18:54:01 lagreca-pc kernel: [    0.004265] Initializing cgroup subsys cpuacct
Sep  1 18:54:01 lagreca-pc kernel: [    0.004270] Initializing cgroup subsys memory
Sep  1 18:54:01 lagreca-pc kernel: [    0.004279] Initializing cgroup subsys devices
Sep  1 18:54:01 lagreca-pc kernel: [    0.004282] Initializing cgroup subsys freezer
Sep  1 18:54:01 lagreca-pc kernel: [    0.004284] Initializing cgroup subsys net_cls
Sep  1 18:54:01 lagreca-pc kernel: [    0.004286] Initializing cgroup subsys blkio
Sep  1 18:54:01 lagreca-pc kernel: [    0.004324] CPU: Physical Processor ID: 0
Sep  1 18:54:01 lagreca-pc kernel: [    0.004326] CPU: Processor Core ID: 0
Sep  1 18:54:01 lagreca-pc kernel: [    0.004330] mce: CPU supports 6 MCE banks
Sep  1 18:54:01 lagreca-pc kernel: [    0.004339] CPU0: Thermal monitoring enabled (TM2)
Sep  1 18:54:01 lagreca-pc kernel: [    0.004344] using mwait in idle threads.
Sep  1 18:54:01 lagreca-pc kernel: [    0.009139] ACPI: Core revision 20110112
Sep  1 18:54:01 lagreca-pc kernel: [    0.015817] ftrace: allocating 23649 entries in 47 pages
Sep  1 18:54:01 lagreca-pc kernel: [    0.020058] Enabling APIC mode:  Flat.  Using 1 I/O APICs
Sep  1 18:54:01 lagreca-pc kernel: [    0.020442] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
Sep  1 18:54:01 lagreca-pc kernel: [    0.063017] CPU0: Intel(R) Core(TM)2 Duo CPU     T7250  @ 2.00GHz stepping 0d
Sep  1 18:54:01 lagreca-pc kernel: [    0.064003] Performance Events: PEBS fmt0+, Core2 events, Intel PMU driver.
Sep  1 18:54:01 lagreca-pc kernel: [    0.064003] PEBS disabled due to CPU errata.
Sep  1 18:54:01 lagreca-pc kernel: [    0.064003] ... version:                2
Sep  1 18:54:01 lagreca-pc kernel: [    0.064003] ... bit width:              40
Sep  1 18:54:01 lagreca-pc kernel: [    0.064003] ... generic registers:      2
Sep  1 18:54:01 lagreca-pc kernel: [    0.064003] ... value mask:             000000ffffffffff
Sep  1 18:54:01 lagreca-pc kernel: [    0.064003] ... max period:             000000007fffffff
Sep  1 18:54:01 lagreca-pc kernel: [    0.064003] ... fixed-purpose events:   3
Sep  1 18:54:01 lagreca-pc kernel: [    0.064003] ... event mask:             0000000700000003
Sep  1 18:54:01 lagreca-pc kernel: [    0.064003] CPU 1 irqstacks, hard=f40aa000 soft=f40ac000
Sep  1 18:54:01 lagreca-pc kernel: [    0.064003] Booting Node   0, Processors  #1 Ok.
Sep  1 18:54:01 lagreca-pc kernel: [    0.008000] Initializing CPU#1
Sep  1 18:54:01 lagreca-pc kernel: [    0.152025] Brought up 2 CPUs
Sep  1 18:54:01 lagreca-pc kernel: [    0.152029] Total of 2 processors activated (7980.15 BogoMIPS).
```


I believe the beginning of the file shows the problem, but I don't know what to do.


Should I change the video driver? How?

Thanks.

---

### Post by oblador on 2011-09-02
up

---

### Post by abtekk on 2011-09-02
I have had problems like this running in VM and native, it seems to be an 11.04 issue. Try switching to gnome classic and see if it does it again.

---

