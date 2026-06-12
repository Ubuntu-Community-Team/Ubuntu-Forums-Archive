---
title: "Touchpad Edge Scrolling Not Working AAO 532H"
date: 2010-07-28
forum: Hardware
---

### Post by MountainX on 2010-07-28
I just installed Ubuntu 10.04 on an Acer Aspire One 532H. I have installed previously on almost identical netbooks and I was able to get the touchpad edge scrolling working by this code.

```
sudo modprobe -r psmouse
sudo modprobe psmouse proto=imps
```

That does **not** work on this model 532H-2789. I'm looking for suggestions. What to do next?

Here is some info that might help:

Devices:
> I: Bus=0019 Vendor=0000 Product=0001 Version=0000
N: Name="Power Button"
P: Phys=PNP0C0C/button/input0
S: Sysfs=/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0
U: Uniq=
H: Handlers=kbd event0 
B: EV=3
B: KEY=100000 0 0 0

I: Bus=0019 Vendor=0000 Product=0003 Version=0000
N: Name="Sleep Button"
P: Phys=PNP0C0E/button/input0
S: Sysfs=/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0E:00/input/input1
U: Uniq=
H: Handlers=kbd event1 
B: EV=3
B: KEY=4000 0 0 0 0

I: Bus=0019 Vendor=0000 Product=0005 Version=0000
N: Name="Lid Switch"
P: Phys=PNP0C0D/button/input0
S: Sysfs=/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0D:00/input/input2
U: Uniq=
H: Handlers=event2 
B: EV=21
B: SW=1

I: Bus=0019 Vendor=0000 Product=0001 Version=0000
N: Name="Power Button"
P: Phys=LNXPWRBN/button/input0
S: Sysfs=/devices/LNXSYSTM:00/LNXPWRBN:00/input/input3
U: Uniq=
H: Handlers=kbd event3 
B: EV=3
B: KEY=100000 0 0 0

I: Bus=0017 Vendor=0001 Product=0001 Version=0100
N: Name="Macintosh mouse button emulation"
P: Phys=
S: Sysfs=/devices/virtual/input/input4
U: Uniq=
H: Handlers=mouse0 event4 
B: EV=7
B: KEY=70000 0 0 0 0 0 0 0 0
B: REL=3

I: Bus=0011 Vendor=0001 Product=0001 Version=ab41
N: Name="AT Translated Set 2 keyboard"
P: Phys=isa0060/serio0/input0
S: Sysfs=/devices/platform/i8042/serio0/input/input5
U: Uniq=
H: Handlers=kbd event5 
B: EV=120013
B: KEY=10000 c0200 0 0 0 0 0 700f 2000003 3803078 f830f401 febfffdf ffefffff ffffffff ffffffff
B: MSC=10
B: LED=7

I: Bus=0019 Vendor=0000 Product=0006 Version=0000
N: Name="Video Bus"
P: Phys=LNXVIDEO/video/input0
S: Sysfs=/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/LNXVIDEO:00/input/input6
U: Uniq=
H: Handlers=kbd event6 
B: EV=3
B: KEY=3f000b 0 0 0 0 0 0 0

I: Bus=0003 Vendor=064e Product=a102 Version=0222
N: Name="WebCam"
P: Phys=usb-0000:00:1d.7-4/button
S: Sysfs=/devices/pci0000:00/0000:00:1d.7/usb1/1-4/1-4:1.0/input/input7
U: Uniq=
H: Handlers=kbd event7 
B: EV=3
B: KEY=100000 0 0 0 0 0 0

I: Bus=0001 Vendor=10ec Product=0272 Version=0001
N: Name="HDA Digital PCBeep"
P: Phys=card0/codec#0/beep0
S: Sysfs=/devices/pci0000:00/0000:00:1b.0/input/input8
U: Uniq=
H: Handlers=kbd event8 
B: EV=40001
B: SND=6

I: Bus=0011 Vendor=0002 Product=0001 Version=0000
N: Name="PS/2 Synaptics TouchPad"
P: Phys=isa0060/serio1/input0
S: Sysfs=/devices/platform/i8042/serio1/input/input9
U: Uniq=
H: Handlers=mouse1 event9 
B: EV=7
B: KEY=70000 0 0 0 0 0 0 0 0
B: REL=3

Dmesg
> [    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.32-21-generic (buildd@rothera) (gcc version 4.4.3 (Ubuntu 4.4.3-4ubuntu5) ) #32-Ubuntu SMP Fri Apr 16 08:10:02 UTC 2010 (Ubuntu 2.6.32-21.32-generic 2.6.32.11+drm33.2)
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   NSC Geode by NSC
[    0.000000]   Cyrix CyrixInstead
[    0.000000]   Centaur CentaurHauls
[    0.000000]   Transmeta GenuineTMx86
[    0.000000]   Transmeta TransmetaCPU
[    0.000000]   UMC UMC UMC UMC
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000003f494000 (usable)
[    0.000000]  BIOS-e820: 000000003f494000 - 000000003f4bf000 (reserved)
[    0.000000]  BIOS-e820: 000000003f4bf000 - 000000003f576000 (usable)
[    0.000000]  BIOS-e820: 000000003f576000 - 000000003f5bf000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000003f5bf000 - 000000003f5ee000 (usable)
[    0.000000]  BIOS-e820: 000000003f5ee000 - 000000003f5ff000 (ACPI data)
[    0.000000]  BIOS-e820: 000000003f5ff000 - 000000003f600000 (usable)
[    0.000000]  BIOS-e820: 000000003f600000 - 0000000040000000 (reserved)
[    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed14000 - 00000000fed1a000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed1c000 - 00000000fed20000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fff00000 - 0000000100000000 (reserved)
[    0.000000] DMI 2.6 present.
[    0.000000] last_pfn = 0x3f600 max_arch_pfn = 0x100000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-DFFFF write-through
[    0.000000]   E0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 0FFF00000 mask 0FFF00000 write-protect
[    0.000000]   1 base 000000000 mask 0E0000000 write-back
[    0.000000]   2 base 020000000 mask 0E0000000 write-back
[    0.000000]   3 base 03F800000 mask 0FF800000 uncachable
[    0.000000]   4 disabled
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] e820 update range: 0000000000002000 - 0000000000006000 (usable) ==> (reserved)
[    0.000000] Scanning 1 areas for low memory corruption
[    0.000000] modified physical RAM map:
[    0.000000]  modified: 0000000000000000 - 0000000000002000 (usable)
[    0.000000]  modified: 0000000000002000 - 0000000000006000 (reserved)
[    0.000000]  modified: 0000000000006000 - 000000000009fc00 (usable)
[    0.000000]  modified: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  modified: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  modified: 0000000000100000 - 000000003f494000 (usable)
[    0.000000]  modified: 000000003f494000 - 000000003f4bf000 (reserved)
[    0.000000]  modified: 000000003f4bf000 - 000000003f576000 (usable)
[    0.000000]  modified: 000000003f576000 - 000000003f5bf000 (ACPI NVS)
[    0.000000]  modified: 000000003f5bf000 - 000000003f5ee000 (usable)
[    0.000000]  modified: 000000003f5ee000 - 000000003f5ff000 (ACPI data)
[    0.000000]  modified: 000000003f5ff000 - 000000003f600000 (usable)
[    0.000000]  modified: 000000003f600000 - 0000000040000000 (reserved)
[    0.000000]  modified: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  modified: 00000000fec00000 - 00000000fec01000 (reserved)
[    0.000000]  modified: 00000000fed14000 - 00000000fed1a000 (reserved)
[    0.000000]  modified: 00000000fed1c000 - 00000000fed20000 (reserved)
[    0.000000]  modified: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  modified: 00000000fff00000 - 0000000100000000 (reserved)
[    0.000000] initial memory mapped : 0 - 00c00000
[    0.000000] init_memory_mapping: 0000000000000000-00000000377fe000
[    0.000000] Using x86 segment limits to approximate NX protection
[    0.000000]  0000000000 - 0000400000 page 4k
[    0.000000]  0000400000 - 0037400000 page 2M
[    0.000000]  0037400000 - 00377fe000 page 4k
[    0.000000] kernel direct mapping tables up to 377fe000 @ 7000-c000
[    0.000000] RAMDISK: 2ea97000 - 2f7ae241
[    0.000000] ACPI: RSDP 000fe020 00024 (v02 ACRSYS)
[    0.000000] ACPI: XSDT 3f5fe120 00064 (v01 ACRSYS ACRPRDCT 00000001      01000013)
[    0.000000] ACPI: FACP 3f5fd000 000F4 (v04 ACRSYS ACRPRDCT 00000001 1025 01000013)
[    0.000000] ACPI: DSDT 3f5f3000 069F8 (v01 ACRSYS ACRPRDCT 00000001 1025 01000013)
[    0.000000] ACPI: FACS 3f584000 00040
[    0.000000] ACPI: HPET 3f5fc000 00038 (v01 ACRSYS ACRPRDCT 00000001 1025 01000013)
[    0.000000] ACPI: APIC 3f5fb000 00078 (v02 ACRSYS ACRPRDCT 00000001 1025 01000013)
[    0.000000] ACPI: MCFG 3f5fa000 0003C (v01 ACRSYS ACRPRDCT 00000001 1025 01000013)
[    0.000000] ACPI: SLIC 3f5f2000 00176 (v01 ACRSYS ACRPRDCT 00000001 1025 01000013)
[    0.000000] ACPI: BOOT 3f5f1000 00028 (v01 ACRSYS ACRPRDCT 00000001 1025 01000013)
[    0.000000] ACPI: SSDT 3f5ef000 004C4 (v02  PmRef    CpuPm 00003000 INTL 20051117)
[    0.000000] ACPI: WDAT 3f5ee000 00194 (v01 INSYDE INSYDE   00000001 MSFT 01000013)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] 126MB HIGHMEM available.
[    0.000000] 887MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 377fe000
[    0.000000]   low ram: 0 - 377fe000
[    0.000000]   node 0 low ram: 00000000 - 377fe000
[    0.000000]   node 0 bootmap 00008000 - 0000ef00
[    0.000000] (9 early reservations) ==> bootmem [0000000000 - 00377fe000]
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000]   #1 [0000001000 - 0000002000]    EX TRAMPOLINE ==> [0000001000 - 0000002000]
[    0.000000]   #2 [0000006000 - 0000007000]       TRAMPOLINE ==> [0000006000 - 0000007000]
[    0.000000]   #3 [0000100000 - 00008d9e98]    TEXT DATA BSS ==> [0000100000 - 00008d9e98]
[    0.000000]   #4 [002ea97000 - 002f7ae241]          RAMDISK ==> [002ea97000 - 002f7ae241]
[    0.000000]   #5 [000009fc00 - 0000100000]    BIOS reserved ==> [000009fc00 - 0000100000]
[    0.000000]   #6 [00008da000 - 00008dd287]              BRK ==> [00008da000 - 00008dd287]
[    0.000000]   #7 [0000007000 - 0000008000]          PGTABLE ==> [0000007000 - 0000008000]
[    0.000000]   #8 [0000008000 - 000000f000]          BOOTMAP ==> [0000008000 - 000000f000]
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000000 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x000377fe
[    0.000000]   HighMem  0x000377fe -> 0x0003f600
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[6] active PFN ranges
[    0.000000]     0: 0x00000000 -> 0x00000002
[    0.000000]     0: 0x00000006 -> 0x0000009f
[    0.000000]     0: 0x00000100 -> 0x0003f494
[    0.000000]     0: 0x0003f4bf -> 0x0003f576
[    0.000000]     0: 0x0003f5bf -> 0x0003f5ee
[    0.000000]     0: 0x0003f5ff -> 0x0003f600
[    0.000000] On node 0 totalpages: 259350
[    0.000000] free_area_init_node: node 0, pgdat c0798720, node_mem_map c1001000
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3963 pages, LIFO batch:0
[    0.000000]   Normal zone: 1744 pages used for memmap
[    0.000000]   Normal zone: 221486 pages, LIFO batch:31
[    0.000000]   HighMem zone: 253 pages used for memmap
[    0.000000]   HighMem zone: 31872 pages, LIFO batch:7
[    0.000000] Using APIC driver default
[    0.000000] ACPI: PM-Timer IO Port: 0x408
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x00] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x00] disabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] dfl dfl lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x02] dfl dfl lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x04] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 4, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
[    0.000000] SMP: Allowing 4 CPUs, 2 hotplug CPUs
[    0.000000] nr_irqs_gsi: 24
[    0.000000] PM: Registered nosave memory: 0000000000002000 - 0000000000006000
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
[    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 40000000 (gap: 40000000:a0000000)
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:4 nr_node_ids:1
[    0.000000] PERCPU: Embedded 14 pages/cpu @c1800000 s36024 r0 d21320 u1048576
[    0.000000] pcpu-alloc: s36024 r0 d21320 u1048576 alloc=1*4194304
[    0.000000] pcpu-alloc: [0] 0 1 2 3 
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 257321
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.32-21-generic root=LABEL=hdd160 ro quiet splash
[    0.000000] PID hash table entries: 4096 (order: 2, 16384 bytes)
[    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] allocated 5191680 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] Initializing HighMem for node 0 (000377fe:0003f600)
[    0.000000] Memory: 1000884k/1038336k available (4673k kernel code, 35732k reserved, 2122k data, 656k init, 128500k highmem)
[    0.000000] virtual kernel memory layout:
[    0.000000]     fixmap  : 0xfff1d000 - 0xfffff000   ( 904 kB)
[    0.000000]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[    0.000000]     vmalloc : 0xf7ffe000 - 0xff7fe000   ( 120 MB)
[    0.000000]     lowmem  : 0xc0000000 - 0xf77fe000   ( 887 MB)
[    0.000000]       .init : 0xc07a3000 - 0xc0847000   ( 656 kB)
[    0.000000]       .data : 0xc0590613 - 0xc07a2e48   (2122 kB)
[    0.000000]       .text : 0xc0100000 - 0xc0590613   (4673 kB)
[    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.000000] SLUB: Genslabs=13, HWalign=64, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000] NR_IRQS:2304 nr_irqs:440
[    0.000000] Console: colour VGA+ 80x25
[    0.000000] console [tty0] enabled
[    0.000000] hpet clockevent registered
[    0.000000] HPET: 3 timers in total, 0 timers will be used for per-cpu timer
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 1662.559 MHz processor.
[    0.004009] Calibrating delay loop (skipped), value calculated using timer frequency.. 3325.11 BogoMIPS (lpj=6650236)
[    0.004045] Security Framework initialized
[    0.004085] AppArmor: AppArmor initialized
[    0.004101] Mount-cache hash table entries: 512
[    0.008080] Initializing cgroup subsys ns
[    0.008089] Initializing cgroup subsys cpuacct
[    0.008099] Initializing cgroup subsys memory
[    0.008113] Initializing cgroup subsys devices
[    0.008119] Initializing cgroup subsys freezer
[    0.008124] Initializing cgroup subsys net_cls
[    0.008160] CPU: L1 I cache: 32K, L1 D cache: 24K
[    0.008166] CPU: L2 cache: 512K
[    0.008172] CPU: Physical Processor ID: 0
[    0.008176] CPU: Processor Core ID: 0
[    0.008183] mce: CPU supports 5 MCE banks
[    0.008195] CPU0: Thermal monitoring handled by SMI
[    0.008203] using mwait in idle threads.
[    0.008214] Performance Events: Atom events, Intel PMU driver.
[    0.008230] ... version:                3
[    0.008234] ... bit width:              40
[    0.008239] ... generic registers:      2
[    0.008243] ... value mask:             000000ffffffffff
[    0.008249] ... max period:             000000007fffffff
[    0.008253] ... fixed-purpose events:   3
[    0.008258] ... event mask:             0000000700000003
[    0.008266] Checking 'hlt' instruction... OK.
[    0.024008] Disabling 4MB page tables to avoid TLB bug
[    0.028275] ACPI: Core revision 20090903
[    0.048018] ftrace: converting mcount calls to 0f 1f 44 00 00
[    0.048029] ftrace: allocating 21771 entries in 43 pages
[    0.056098] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.056500] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.099798] CPU0: Intel(R) Atom(TM) CPU N450   @ 1.66GHz stepping 0a
[    0.100001] Booting processor 1 APIC 0x1 ip 0x6000
[    0.008000] Initializing CPU#1
[    0.008000] CPU: L1 I cache: 32K, L1 D cache: 24K
[    0.008000] CPU: L2 cache: 512K
[    0.008000] CPU: Physical Processor ID: 0
[    0.008000] CPU: Processor Core ID: 0
[    0.008000] CPU1: Thermal monitoring handled by SMI
[    0.184122] CPU1: Intel(R) Atom(TM) CPU N450   @ 1.66GHz stepping 0a
[    0.184149] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
[    0.188033] Brought up 2 CPUs
[    0.188041] Total of 2 processors activated (6650.44 BogoMIPS).
[    0.188279] CPU0 attaching sched-domain:
[    0.188289]  domain 0: span 0-1 level SIBLING
[    0.188294]   groups: 0 (cpu_power = 589) 1 (cpu_power = 589)
[    0.188306]   domain 1: span 0-1 level MC
[    0.188312]    groups: 0-1 (cpu_power = 1178)
[    0.188324] CPU1 attaching sched-domain:
[    0.188329]  domain 0: span 0-1 level SIBLING
[    0.188334]   groups: 1 (cpu_power = 589) 0 (cpu_power = 589)
[    0.188345]   domain 1: span 0-1 level MC
[    0.188350]    groups: 0-1 (cpu_power = 1178)
[    0.188576] devtmpfs: initialized
[    0.188576] regulator: core version 0.5
[    0.188576] Time: 22:09:20  Date: 07/28/10
[    0.188576] NET: Registered protocol family 16
[    0.188576] Trying to unpack rootfs image as initramfs...
[    0.188576] EISA bus registered
[    0.188576] ACPI: bus type pci registered
[    0.188740] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 255
[    0.188749] PCI: MCFG area at e0000000 reserved in E820
[    0.188755] PCI: Using MMCONFIG for extended config space
[    0.188761] PCI: Using configuration type 1 for base access
[    0.193548] bio: create slab <bio-0> at 0
[    0.196866] ACPI: EC: Look up EC in DSDT
[    0.302216] ACPI: Executed 1 blocks of module-level executable AML code
[    0.307551] ACPI: BIOS _OSI(Linux) query ignored
[    0.309598] ACPI: Interpreter enabled
[    0.309598] ACPI: (supports S0 S3 S4 S5)
[    0.309598] ACPI: Using IOAPIC for interrupt routing
[    0.587168] ACPI: EC: GPE = 0x19, I/O: command/status = 0x66, data = 0x62
[    0.587356] ACPI: Power Resource [FN00] (on)
[    0.588014] ACPI: No dock devices found.
[    0.589805] ACPI Warning for \_SB_.PCI0._OSC: Parameter count mismatch - ASL declared 5, ACPI requires 4 (20090903/nspredef-336)
[    0.589832] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.590018] pci 0000:00:02.0: reg 10 32bit mmio: [0x58180000-0x581fffff]
[    0.590031] pci 0000:00:02.0: reg 14 io port: [0x60c0-0x60c7]
[    0.590042] pci 0000:00:02.0: reg 18 32bit mmio pref: [0x40000000-0x4fffffff]
[    0.590054] pci 0000:00:02.0: reg 1c 32bit mmio: [0x58000000-0x580fffff]
[    0.590115] pci 0000:00:02.1: reg 10 32bit mmio: [0x58100000-0x5817ffff]
[    0.590280] pci 0000:00:1b.0: reg 10 64bit mmio: [0x58200000-0x58203fff]
[    0.590376] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    0.590388] pci 0000:00:1b.0: PME# disabled
[    0.590524] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.590535] pci 0000:00:1c.0: PME# disabled
[    0.590670] pci 0000:00:1c.1: PME# supported from D0 D3hot D3cold
[    0.590681] pci 0000:00:1c.1: PME# disabled
[    0.590782] pci 0000:00:1d.0: reg 20 io port: [0x6080-0x609f]
[    0.590885] pci 0000:00:1d.1: reg 20 io port: [0x6060-0x607f]
[    0.590983] pci 0000:00:1d.2: reg 20 io port: [0x6040-0x605f]
[    0.591079] pci 0000:00:1d.3: reg 20 io port: [0x6020-0x603f]
[    0.591181] pci 0000:00:1d.7: reg 10 32bit mmio: [0x58204400-0x582047ff]
[    0.591270] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
[    0.591281] pci 0000:00:1d.7: PME# disabled
[    0.591593] pci 0000:00:1f.2: reg 10 io port: [0x60b8-0x60bf]
[    0.591611] pci 0000:00:1f.2: reg 14 io port: [0x60cc-0x60cf]
[    0.591627] pci 0000:00:1f.2: reg 18 io port: [0x60b0-0x60b7]
[    0.591643] pci 0000:00:1f.2: reg 1c io port: [0x60c8-0x60cb]
[    0.591658] pci 0000:00:1f.2: reg 20 io port: [0x60a0-0x60af]
[    0.591674] pci 0000:00:1f.2: reg 24 32bit mmio: [0x58204000-0x582043ff]
[    0.591729] pci 0000:00:1f.2: PME# supported from D3hot
[    0.591739] pci 0000:00:1f.2: PME# disabled
[    0.591818] pci 0000:00:1f.3: reg 20 io port: [0x6000-0x601f]
[    0.591954] pci 0000:01:00.0: reg 10 64bit mmio: [0x57000000-0x5703ffff]
[    0.591972] pci 0000:01:00.0: reg 18 io port: [0x5000-0x507f]
[    0.592104] pci 0000:01:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.592117] pci 0000:01:00.0: PME# disabled
[    0.592222] pci 0000:00:1c.0: bridge io port: [0x5000-0x5fff]
[    0.592235] pci 0000:00:1c.0: bridge 32bit mmio: [0x57000000-0x57ffffff]
[    0.592252] pci 0000:00:1c.0: bridge 64bit mmio pref: [0x50000000-0x50ffffff]
[    0.592356] pci 0000:02:00.0: reg 10 64bit mmio: [0x56000000-0x5600ffff]
[    0.592466] pci 0000:02:00.0: supports D1
[    0.592473] pci 0000:02:00.0: PME# supported from D0 D1 D3hot
[    0.592485] pci 0000:02:00.0: PME# disabled
[    0.592594] pci 0000:00:1c.1: bridge io port: [0x4000-0x4fff]
[    0.592606] pci 0000:00:1c.1: bridge 32bit mmio: [0x56000000-0x56ffffff]
[    0.592622] pci 0000:00:1c.1: bridge 64bit mmio pref: [0x51000000-0x51ffffff]
[    0.592707] pci 0000:00:1e.0: transparent bridge
[    0.592754] pci_bus 0000:00: on NUMA node 0
[    0.592777] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.593403] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.EXP1._PRT]
[    0.593684] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.EXP2._PRT]
[    0.594364] ACPI Warning for \_SB_.PCI0._OSC: Parameter count mismatch - ASL declared 5, ACPI requires 4 (20090903/nspredef-336)
[    0.605647] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 7 9 10 *11 12)
[    0.606015] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 7 9 *10 11 12)
[    0.606369] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 7 9 10 *11 12)
[    0.606716] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 7 9 10 *11 12)
[    0.607115] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 7 9 10 11 12) *0, disabled.
[    0.607472] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 7 9 10 11 12) *0, disabled.
[    0.607834] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 7 9 10 11 12) *0, disabled.
[    0.608223] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 7 9 10 11 12) *0, disabled.
[    0.608587] vgaarb: device added: PCI:0000:00:02.0,decodes=io+mem,owns=io+mem,locks=none
[    0.608616] vgaarb: loaded
[    0.608962] SCSI subsystem initialized
[    0.609193] libata version 3.00 loaded.
[    0.609419] usbcore: registered new interface driver usbfs
[    0.609466] usbcore: registered new interface driver hub
[    0.609577] usbcore: registered new device driver usb
[    0.610202] ACPI: WMI: Mapper loaded
[    0.610209] PCI: Using ACPI for IRQ routing
[    0.610599] NetLabel: Initializing
[    0.610606] NetLabel:  domain hash size = 128
[    0.610611] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.610643] NetLabel:  unlabeled traffic allowed by default
[    0.610750] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[    0.610765] hpet0: 3 comparators, 64-bit 14.318180 MHz counter
[    0.616171] Switching to clocksource tsc
[    0.620738] AppArmor: AppArmor Filesystem Enabled
[    0.620774] pnp: PnP ACPI init
[    0.620811] ACPI: bus type pnp registered
[    0.755103] pnp: PnP ACPI: found 9 devices
[    0.755113] ACPI: ACPI bus type pnp unregistered
[    0.755122] PnPBIOS: Disabled by ACPI PNP
[    0.755158] system 00:01: ioport range 0x164e-0x164f has been reserved
[    0.755169] system 00:01: ioport range 0x600-0x60f has been reserved
[    0.755178] system 00:01: ioport range 0x610-0x610 has been reserved
[    0.755187] system 00:01: ioport range 0x800-0x80f has been reserved
[    0.755197] system 00:01: ioport range 0x810-0x817 has been reserved
[    0.755206] system 00:01: ioport range 0x400-0x47f has been reserved
[    0.755215] system 00:01: ioport range 0x500-0x53f has been reserved
[    0.755226] system 00:01: ioport range 0xff2c-0xff2f has been reserved
[    0.755238] system 00:01: iomem range 0xe0000000-0xefffffff has been reserved
[    0.755249] system 00:01: iomem range 0xfed1c000-0xfed1ffff has been reserved
[    0.755259] system 00:01: iomem range 0xfed14000-0xfed17fff has been reserved
[    0.755269] system 00:01: iomem range 0xfed18000-0xfed18fff has been reserved
[    0.755279] system 00:01: iomem range 0xfed19000-0xfed19fff has been reserved
[    0.755297] system 00:01: iomem range 0xfec00000-0xfec00fff could not be reserved
[    0.755308] system 00:01: iomem range 0xfee00000-0xfee00fff has been reserved
[    0.790531] pci 0000:00:1c.0: PCI bridge, secondary bus 0000:01
[    0.790544] pci 0000:00:1c.0:   IO window: 0x5000-0x5fff
[    0.790557] pci 0000:00:1c.0:   MEM window: 0x57000000-0x57ffffff
[    0.790569] pci 0000:00:1c.0:   PREFETCH window: 0x00000050000000-0x00000050ffffff
[    0.790586] pci 0000:00:1c.1: PCI bridge, secondary bus 0000:02
[    0.790595] pci 0000:00:1c.1:   IO window: 0x4000-0x4fff
[    0.790607] pci 0000:00:1c.1:   MEM window: 0x56000000-0x56ffffff
[    0.790619] pci 0000:00:1c.1:   PREFETCH window: 0x00000051000000-0x00000051ffffff
[    0.790635] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:05
[    0.790641] pci 0000:00:1e.0:   IO window: disabled
[    0.790652] pci 0000:00:1e.0:   MEM window: disabled
[    0.790661] pci 0000:00:1e.0:   PREFETCH window: disabled
[    0.790698]   alloc irq_desc for 16 on node -1
[    0.790705]   alloc kstat_irqs on node -1
[    0.790722] pci 0000:00:1c.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.790734] pci 0000:00:1c.0: setting latency timer to 64
[    0.790755]   alloc irq_desc for 17 on node -1
[    0.790761]   alloc kstat_irqs on node -1
[    0.790772] pci 0000:00:1c.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    0.790783] pci 0000:00:1c.1: setting latency timer to 64
[    0.790800] pci 0000:00:1e.0: setting latency timer to 64
[    0.790811] pci_bus 0000:00: resource 0 io:  [0x00-0xffff]
[    0.790820] pci_bus 0000:00: resource 1 mem: [0x000000-0xffffffff]
[    0.790828] pci_bus 0000:01: resource 0 io:  [0x5000-0x5fff]
[    0.790837] pci_bus 0000:01: resource 1 mem: [0x57000000-0x57ffffff]
[    0.790845] pci_bus 0000:01: resource 2 pref mem [0x50000000-0x50ffffff]
[    0.790853] pci_bus 0000:02: resource 0 io:  [0x4000-0x4fff]
[    0.790862] pci_bus 0000:02: resource 1 mem: [0x56000000-0x56ffffff]
[    0.790870] pci_bus 0000:02: resource 2 pref mem [0x51000000-0x51ffffff]
[    0.790879] pci_bus 0000:05: resource 3 io:  [0x00-0xffff]
[    0.790887] pci_bus 0000:05: resource 4 mem: [0x000000-0xffffffff]
[    0.790977] NET: Registered protocol family 2
[    0.791263] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.792172] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.793292] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.793820] TCP: Hash tables configured (established 131072 bind 65536)
[    0.793828] TCP reno registered
[    0.794091] NET: Registered protocol family 1
[    0.794150] pci 0000:00:02.0: Boot video device
[    0.794467] Simple Boot Flag at 0x44 set to 0x1
[    0.794967] cpufreq-nforce2: No nForce2 chipset.
[    0.795044] Scanning for low memory corruption every 60 seconds
[    0.795390] audit: initializing netlink socket (disabled)
[    0.795416] type=2000 audit(1280354960.791:1): initialized
[    0.816005] highmem bounce pool size: 64 pages
[    0.816020] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    0.821013] VFS: Disk quotas dquot_6.5.2
[    0.821194] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.823131] fuse init (API version 7.13)
[    0.823403] msgmni has been set to 1705
[    0.824093] alg: No test for stdrng (krng)
[    0.824275] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.824284] io scheduler noop registered
[    0.824290] io scheduler anticipatory registered
[    0.824296] io scheduler deadline registered
[    0.824436] io scheduler cfq registered (default)
[    0.824772]   alloc irq_desc for 24 on node -1
[    0.824780]   alloc kstat_irqs on node -1
[    0.824802] pcieport 0000:00:1c.0: irq 24 for MSI/MSI-X
[    0.824822] pcieport 0000:00:1c.0: setting latency timer to 64
[    0.825097]   alloc irq_desc for 25 on node -1
[    0.825103]   alloc kstat_irqs on node -1
[    0.825121] pcieport 0000:00:1c.1: irq 25 for MSI/MSI-X
[    0.825139] pcieport 0000:00:1c.1: setting latency timer to 64
[    0.825383] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.825418] Firmware did not grant requested _OSC control
[    0.825479] Firmware did not grant requested _OSC control
[    0.825579] Firmware did not grant requested _OSC control
[    0.825632] Firmware did not grant requested _OSC control
[    0.825698] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.834865] Freeing initrd memory: 13404k freed
[    1.024202] ACPI: AC Adapter [AC] (off-line)
[    1.024406] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0
[    1.024415] ACPI: Power Button [PWRB]
[    1.024540] input: Sleep Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0E:00/input/input1
[    1.024547] ACPI: Sleep Button [SLPB]
[    1.024646] input: Lid Switch as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0D:00/input/input2
[    1.024752] ACPI: Lid Switch [LID0]
[    1.024872] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input3
[    1.024879] ACPI: Power Button [PWRF]
[    1.025158] fan PNP0C0B:00: registered as cooling_device0
[    1.025170] ACPI: Fan [FAN] (on)
[    1.026460] ACPI: SSDT 3f497c90 001F7 (v02  PmRef  Cpu0Ist 00003000 INTL 20051117)
[    1.027323] ACPI: SSDT 3f496e10 001C7 (v02  PmRef  Cpu0Cst 00003001 INTL 20051117)
[    1.028335] Marking TSC unstable due to TSC halts in idle
[    1.028469] Switching to clocksource hpet
[    1.028489] processor LNXCPU:00: registered as cooling_device1
[    1.029395] ACPI: SSDT 3f497f10 000D0 (v02  PmRef  Cpu1Ist 00003000 INTL 20051117)
[    1.030181] ACPI: SSDT 3f495f10 00083 (v02  PmRef  Cpu1Cst 00003000 INTL 20051117)
[    1.031335] processor LNXCPU:01: registered as cooling_device2
[    1.165640] thermal LNXTHERM:01: registered as thermal_zone0
[    1.165659] ACPI: Thermal Zone [THRM] (44 C)
[    1.166095] isapnp: Scanning for PnP cards...
[    1.170367] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    1.173930] brd: module loaded
[    1.175333] loop: module loaded
[    1.175581] input: Macintosh mouse button emulation as /devices/virtual/input/input4
[    1.176817] Fixed MDIO Bus: probed
[    1.176921] PPP generic driver version 2.4.2
[    1.177031] tun: Universal TUN/TAP device driver, 1.6
[    1.177037] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    1.177251] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    1.177301] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.177336] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    1.177345] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    1.177444] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 1
[    1.177487] ehci_hcd 0000:00:1d.7: using broken periodic workaround
[    1.177507] ehci_hcd 0000:00:1d.7: debug port 1
[    1.181414] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
[    1.181450] ehci_hcd 0000:00:1d.7: irq 16, io mem 0x58204400
[    1.196036] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    1.196252] usb usb1: configuration #1 chosen from 1 choice
[    1.196333] hub 1-0:1.0: USB hub found
[    1.196355] hub 1-0:1.0: 8 ports detected
[    1.196523] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    1.196565] uhci_hcd: USB Universal Host Controller Interface driver
[    1.196635] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.196651] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    1.196660] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    1.196753] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    1.196797] uhci_hcd 0000:00:1d.0: irq 16, io base 0x00006080
[    1.197047] usb usb2: configuration #1 chosen from 1 choice
[    1.197131] hub 2-0:1.0: USB hub found
[    1.197149] hub 2-0:1.0: 2 ports detected
[    1.197270] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    1.197284] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    1.197293] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    1.197383] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3
[    1.197439] uhci_hcd 0000:00:1d.1: irq 17, io base 0x00006060
[    1.197673] usb usb3: configuration #1 chosen from 1 choice
[    1.197753] hub 3-0:1.0: USB hub found
[    1.197772] hub 3-0:1.0: 2 ports detected
[    1.197876]   alloc irq_desc for 18 on node -1
[    1.197883]   alloc kstat_irqs on node -1
[    1.197897] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    1.197911] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    1.197920] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    1.198011] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4
[    1.198066] uhci_hcd 0000:00:1d.2: irq 18, io base 0x00006040
[    1.198319] usb usb4: configuration #1 chosen from 1 choice
[    1.198395] hub 4-0:1.0: USB hub found
[    1.198415] hub 4-0:1.0: 2 ports detected
[    1.198520]   alloc irq_desc for 19 on node -1
[    1.198526]   alloc kstat_irqs on node -1
[    1.198539] uhci_hcd 0000:00:1d.3: PCI INT D -> GSI 19 (level, low) -> IRQ 19
[    1.198553] uhci_hcd 0000:00:1d.3: setting latency timer to 64
[    1.198562] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[    1.198659] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 5
[    1.198714] uhci_hcd 0000:00:1d.3: irq 19, io base 0x00006020
[    1.198952] usb usb5: configuration #1 chosen from 1 choice
[    1.199028] hub 5-0:1.0: USB hub found
[    1.199047] hub 5-0:1.0: 2 ports detected
[    1.199267] PNP: PS/2 Controller [PNP0303:KBC0,PNP0f13:MSS0] at 0x60,0x64 irq 1,12
[    1.212976] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.212998] serio: i8042 AUX port at 0x60,0x64 irq 12
[    1.213354] mice: PS/2 mouse device common for all mice
[    1.213984] rtc_cmos 00:03: RTC can wake from S4
[    1.214080] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0
[    1.214123] rtc0: alarms up to one month, 242 bytes nvram, hpet irqs
[    1.214431] device-mapper: uevent: version 1.0.3
[    1.214721] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: [email]dm-devel@redhat.com[/email]
[    1.214921] device-mapper: multipath: version 1.1.0 loaded
[    1.214929] device-mapper: multipath round-robin: version 1.0.0 loaded
[    1.215253] EISA: Probing bus 0 at eisa.0
[    1.215279] Cannot allocate resource for EISA slot 4
[    1.215285] Cannot allocate resource for EISA slot 5
[    1.215292] Cannot allocate resource for EISA slot 6
[    1.215308] EISA: Detected 0 cards.
[    1.215748] cpuidle: using governor ladder
[    1.216109] cpuidle: using governor menu
[    1.217351] TCP cubic registered
[    1.217820] NET: Registered protocol family 10
[    1.219055] lo: Disabled Privacy Extensions
[    1.219932] NET: Registered protocol family 17
[    1.221348] Using IPI No-Shortcut mode
[    1.221587] PM: Resume from disk failed.
[    1.221614] registered taskstats version 1
[    1.222223]   Magic number: 2:63:200
[    1.222353] rtc_cmos 00:03: setting system clock to 2010-07-28 22:09:21 UTC (1280354961)
[    1.222362] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.222367] EDD information not available.
[    1.230139] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input5
[    1.520339] isapnp: No Plug & Play device found
[    1.520409] Freeing unused kernel memory: 656k freed
[    1.520944] Write protecting the kernel text: 4676k
[    1.521019] Write protecting the kernel read-only data: 1840k
[    1.544083] usb 1-4: new high speed USB device using ehci_hcd and address 2
[    1.560943] udev: starting version 151
[    1.706208] ahci 0000:00:1f.2: version 3.0
[    1.706246] ahci 0000:00:1f.2: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    1.706319]   alloc irq_desc for 26 on node -1
[    1.706327]   alloc kstat_irqs on node -1
[    1.706351] ahci 0000:00:1f.2: irq 26 for MSI/MSI-X
[    1.706439] ahci: SSS flag set, parallel bus scan disabled
[    1.706499] ahci 0000:00:1f.2: AHCI 0001.0100 32 slots 4 ports 3 Gbps 0x3 impl SATA mode
[    1.706511] ahci 0000:00:1f.2: flags: 64bit ncq ilck stag pm led clo pmp pio slum part 
[    1.706524] ahci 0000:00:1f.2: setting latency timer to 64
[    1.706988] scsi0 : ahci
[    1.717165] usb 1-4: configuration #1 chosen from 1 choice
[    1.743337] scsi1 : ahci
[    1.769982] scsi2 : ahci
[    1.798531] scsi3 : ahci
[    1.799296] ata1: SATA max UDMA/133 abar m1024@0x58204000 port 0x58204100 irq 26
[    1.799309] ata2: SATA max UDMA/133 abar m1024@0x58204000 port 0x58204180 irq 26
[    1.799318] ata3: DUMMY
[    1.799323] ata4: DUMMY
[    1.859305] Linux agpgart interface v0.103
[    2.280154] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    2.281136] ACPI Warning for \_SB_.PCI0.SATA.PRT0._GTF: Return type mismatch - found Integer, expected Buffer (20090903/nspredef-1006)
[    2.281154] ata1.00: _GTF unexpected object type 0x1
[    2.281545] ata1.00: ATA-8: Hitachi HTS545016B9A300, PBBOC60F, max UDMA/133
[    2.281558] ata1.00: 312581808 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
[    2.282735] ata1.00: _GTF unexpected object type 0x1
[    2.283183] ata1.00: configured for UDMA/133
[    2.296365] scsi 0:0:0:0: Direct-Access     ATA      Hitachi HTS54501 PBBO PQ: 0 ANSI: 5
[    2.296851] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    2.297186] sd 0:0:0:0: [sda] 312581808 512-byte logical blocks: (160 GB/149 GiB)
[    2.297460] sd 0:0:0:0: [sda] Write Protect is off
[    2.297469] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    2.297564] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.298013]  sda: sda1 sda2 < sda5 >
[    2.346990] sd 0:0:0:0: [sda] Attached SCSI disk
[    2.616174] ata2: SATA link down (SStatus 0 SControl 300)
[    2.642692] agpgart-intel 0000:00:00.0: Intel IGD Chipset
[    2.643183] agpgart-intel 0000:00:00.0: detected 8188K stolen memory
[    2.657716] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0x40000000
[    2.713207] [drm] Initialized drm 1.1.0 20060810
[    2.785749] i915 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    2.785759] i915 0000:00:02.0: setting latency timer to 64
[    2.798933]   alloc irq_desc for 27 on node -1
[    2.798940]   alloc kstat_irqs on node -1
[    2.798955] i915 0000:00:02.0: irq 27 for MSI/MSI-X
[    2.798966] [drm] set up 7M of stolen space
[    2.902486] [drm] initialized overlay support
[    3.108270] ACPI: Battery Slot [BAT0] (battery present)
[    3.322778] fb0: inteldrmfb frame buffer device
[    3.322786] registered panic notifier
[    3.537035] acpi device:24: registered as cooling_device3
[    3.538053] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/LNXVIDEO:00/input/input6
[    3.538191] ACPI: Video Device [OVGA] (multi-head: yes  rom: no  post: no)
[    3.538247] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
[    3.544355] vga16fb: initializing
[    3.544366] vga16fb: mapped to 0xc00a0000
[    3.544376] vga16fb: not registering due to another framebuffer present
[    3.560336] [drm] Big FIFO is enabled
[    3.632208] [drm] Big FIFO is enabled
[    3.632221] [drm] Big FIFO is enabled
[    3.638107] [drm] Big FIFO is enabled
[    3.668051] Console: switching to colour frame buffer device 128x37
[    4.525385] [drm] Big FIFO is enabled
[    4.548336] [drm] Big FIFO is enabled
[    4.893978] xor: automatically using best checksumming function: pIII_sse
[    4.912022]    pIII_sse  :  4922.000 MB/sec
[    4.912031] xor: using function: pIII_sse (4922.000 MB/sec)
[    4.919018] device-mapper: dm-raid45: initialized v0.2594b
[   10.140024] EXT4-fs (sda1): mounted filesystem with ordered data mode
[   23.631928] Adding 2963952k swap on /dev/sda5.  Priority:-1 extents:1 across:2963952k 
[   23.685442] udev: starting version 151
[   23.864635] lp: driver loaded but no devices found
[   25.136845] atl1c 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   25.136869] atl1c 0000:01:00.0: setting latency timer to 64
[   25.267373] atl1c 0000:01:00.0: version 1.0.0.1-NAPI
[   25.417120] cfg80211: Calling CRDA to update world regulatory domain
[   25.454265] udev: renamed network interface eth0 to eth5
[   25.463620] Linux video capture interface: v2.00
[   25.464867] acer-wmi: Acer Laptop ACPI-WMI Extras
[   25.553637] cfg80211: World regulatory domain updated:
[   25.553647] 	(start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   25.553657] 	(2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   25.553665] 	(2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   25.553673] 	(2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   25.553681] 	(5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   25.553689] 	(5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   25.554622] uvcvideo: Found UVC 1.00 device WebCam (064e:a102)
[   25.570940]   alloc irq_desc for 28 on node -1
[   25.570949]   alloc kstat_irqs on node -1
[   25.570981] atl1c 0000:01:00.0: irq 28 for MSI/MSI-X
[   25.571901] ADDRCONF(NETDEV_UP): eth5: link is not ready
[   25.581768] input: WebCam as /devices/pci0000:00/0000:00:1d.7/usb1/1-4/1-4:1.0/input/input7
[   25.581968] usbcore: registered new interface driver uvcvideo
[   25.581980] USB Video Class driver (v0.1.0)
[   25.592378] ath9k 0000:02:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   25.592402] ath9k 0000:02:00.0: setting latency timer to 64
[   25.592822] acer-wmi: Brightness must be controlled by generic video driver
[   25.642469] ath: EEPROM regdomain: 0x65
[   25.642477] ath: EEPROM indicates we should expect a direct regpair map
[   25.642488] ath: Country alpha2 being used: 00
[   25.642494] ath: Regpair used: 0x65
[   25.894820] phy0: Selected rate control algorithm 'ath9k_rate_control'
[   25.897114] Registered led device: ath9k-phy0::radio
[   25.897176] Registered led device: ath9k-phy0::assoc
[   25.897233] Registered led device: ath9k-phy0::tx
[   25.897296] Registered led device: ath9k-phy0::rx
[   25.897334] phy0: Atheros AR9285 MAC/BB Rev:2 AR5133 RF Rev:e0: mem=0xf8c40000, irq=17
[   25.953656] udev: renamed network interface wlan0 to wlan5
[   25.999358] ADDRCONF(NETDEV_UP): wlan5: link is not ready
[   26.239587] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   26.239649] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   26.270706] atkbd.c: Unknown key pressed (translated set 2, code 0x0 on isa0060/serio0).
[   26.270717] atkbd.c: Use 'setkeycodes 00 <keycode>' to make it known.
[   26.354100] hda_codec: ALC272: BIOS auto-probing.
[   26.355860] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:1b.0/input/input8
[   26.373437] input: PS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input9
[   26.804552] atl1c 0000:01:00.0: atl1c: eth5 NIC Link is Up<100 Mbps Full Duplex>
[   26.805077] ADDRCONF(NETDEV_CHANGE): eth5: link becomes ready
[   27.356547] hda-intel: azx_get_response timeout, switching to polling mode: last cmd=0x022f000e
[   27.815922] ppdev: user-space parallel port driver
[   28.243436] CPU0 attaching NULL sched-domain.
[   28.243448] CPU1 attaching NULL sched-domain.
[   28.264702] CPU0 attaching sched-domain:
[   28.264713]  domain 0: span 0-1 level SIBLING
[   28.264722]   groups: 0 (cpu_power = 589) 1 (cpu_power = 589)
[   28.264739]   domain 1: span 0-1 level MC
[   28.264746]    groups: 0-1 (cpu_power = 1178)
[   28.264761] CPU1 attaching sched-domain:
[   28.264767]  domain 0: span 0-1 level SIBLING
[   28.264773]   groups: 1 (cpu_power = 589) 0 (cpu_power = 589)
[   28.264788]   domain 1: span 0-1 level MC
[   28.264794]    groups: 0-1 (cpu_power = 1178)
[   32.300570] usb 1-2: new high speed USB device using ehci_hcd and address 3
[   32.435340] usb 1-2: configuration #1 chosen from 1 choice
[   32.634217] Initializing USB Mass Storage driver...
[   32.642438] scsi4 : SCSI emulation for USB Mass Storage devices
[   32.648163] usbcore: registered new interface driver usb-storage
[   32.648175] USB Mass Storage support registered.
[   32.656732] usb-storage: device found at 3
[   32.656740] usb-storage: waiting for device to settle before scanning
[   33.465104] CPU0 attaching NULL sched-domain.
[   33.465119] CPU1 attaching NULL sched-domain.
[   33.496707] CPU0 attaching sched-domain:
[   33.496718]  domain 0: span 0-1 level SIBLING
[   33.496727]   groups: 0 (cpu_power = 589) 1 (cpu_power = 589)
[   33.496746]   domain 1: span 0-1 level MC
[   33.496754]    groups: 0-1 (cpu_power = 1178)
[   33.496770] CPU1 attaching sched-domain:
[   33.496777]  domain 0: span 0-1 level SIBLING
[   33.496784]   groups: 1 (cpu_power = 589) 0 (cpu_power = 589)
[   33.496802]   domain 1: span 0-1 level MC
[   33.496810]    groups: 0-1 (cpu_power = 1178)
[   37.360033] eth5: no IPv6 routers present
[   37.668581] usb-storage: device scan complete
[   37.669234] scsi 4:0:0:0: Direct-Access              USB Flash Memory PMAP PQ: 0 ANSI: 0 CCS
[   37.674114] sd 4:0:0:0: Attached scsi generic sg1 type 0
[   39.882838] sd 4:0:0:0: [sdb] 3966976 512-byte logical blocks: (2.03 GB/1.89 GiB)
[   39.883489] sd 4:0:0:0: [sdb] Write Protect is off
[   39.883501] sd 4:0:0:0: [sdb] Mode Sense: 23 00 00 00
[   39.883509] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[   39.889351] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[   39.889368]  sdb: sdb1
[   39.943328] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[   39.943344] sd 4:0:0:0: [sdb] Attached SCSI removable disk


XOrg
> 
X.Org X Server 1.7.6
Release Date: 2010-03-17
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-25-server i686 Ubuntu
Current Operating System: Linux mynetbook 2.6.32-21-generic #32-Ubuntu SMP Fri Apr 16 08:10:02 UTC 2010 i686
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.32-21-generic root=LABEL=hdd160 ro quiet splash
Build Date: 23 April 2010  05:11:50PM
xorg-server 2:1.7.6-2ubuntu7 (Bryce Harrington <bryce@ubuntu.com>) 
Current version of pixman: 0.16.4
	Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
	to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Wed Jul 28 22:09:46 2010
(==) Using config directory: "/usr/lib/X11/xorg.conf.d"
(==) No Layout section.  Using the first Screen section.
(==) No screen section available. Using defaults.
(**) |-->Screen "Default Screen Section" (0)
(**) |   |-->Monitor "<default monitor>"
(==) No monitor specified for screen "Default Screen Section".
	Using a default monitor configuration.
(==) Automatically adding devices
(==) Automatically enabling devices
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
	Entry deleted from font path.
(==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	built-ins
(==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
(II) The server relies on udev to provide the list of input devices.
	If no devices become available, reconfigure udev or disable AutoAddDevices.
(II) Loader magic: 0x81f0e80
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.4
	X.Org Video Driver: 6.0
	X.Org XInput driver : 7.0
	X.Org Server Extension : 2.0
(++) using VT number 7

(--) PCI:*(0:0:2:0) 8086:a011:1025:0349 Intel Corporation N10 Family Integrated Graphics Controller rev 0, Mem @ 0x58180000/524288, 0x40000000/268435456, 0x58000000/1048576, I/O @ 0x000060c0/8
(--) PCI: (0:0:2:1) 8086:a012:1025:0349 Intel Corporation N10 Family Integrated Graphics Controller rev 0, Mem @ 0x58100000/524288
(WW) Open ACPI failed (/var/run/acpid.socket) (No such file or directory)
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension MIT-SCREEN-SAVER
(II) Loading extension XFree86-VidModeExtension
(II) Loading extension XFree86-DGA
(II) Loading extension DPMS
(II) Loading extension XVideo
(II) Loading extension XVideo-MotionCompensation
(II) Loading extension X-Resource
(II) LoadModule: "dbe"
(II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions/libglx.so
(II) Module glx: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.0.0
	ABI class: X.Org Server Extension, version 2.0
(==) AIGLX enabled
(II) Loading extension GLX
(II) LoadModule: "record"
(II) Loading /usr/lib/xorg/modules/extensions/librecord.so
(II) Module record: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.13.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension RECORD
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions/libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.0.0
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension XFree86-DRI
(II) LoadModule: "dri2"
(II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
(II) Module dri2: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.1.0
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DRI2
(==) Matched intel as autoconfigured driver 0
(==) Matched vesa as autoconfigured driver 1
(==) Matched fbdev as autoconfigured driver 2
(==) Assigned the driver to the xf86ConfigLayout
(II) LoadModule: "intel"
(II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
(II) Module intel: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 2.9.1
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 6.0
(II) LoadModule: "vesa"
(II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
(II) Module vesa: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 2.3.0
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 6.0
(II) LoadModule: "fbdev"
(II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
(II) Module fbdev: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 0.4.1
	ABI class: X.Org Video Driver, version 6.0
(II) intel: Driver for Intel Integrated Graphics Chipsets: i810,
	i810-dc100, i810e, i815, i830M, 845G, 852GM/855GM, 865G, 915G,
	E7221 (i915), 915GM, 945G, 945GM, 945GME, Pineview GM, Pineview G,
	965G, G35, 965Q, 946GZ, 965GM, 965GME/GLE, G33, Q35, Q33, GM45,
	4 Series, G45/G43, Q45/Q43, G41, B43, Clarkdale, Arrandale
(II) VESA: driver for VESA chipsets: vesa
(II) FBDEV: driver for framebuffer: fbdev
(II) Primary Device is: PCI 00@00:02:0
(WW) Falling back to old probe method for vesa
(WW) Falling back to old probe method for fbdev
(II) Loading sub module "fbdevhw"
(II) LoadModule: "fbdevhw"
(II) Loading /usr/lib/xorg/modules/linux/libfbdevhw.so
(II) Module fbdevhw: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 0.0.2
	ABI class: X.Org Video Driver, version 6.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 8, (OK)
drmOpenByBusid: Searching for BusID pci:0000:00:02.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 8, (OK)
drmOpenByBusid: drmOpenMinor returns 8
drmOpenByBusid: drmGetBusid reports pci:0000:00:02.0
(II) intel(0): Creating default Display subsection in Screen section
	"Default Screen Section" for depth/fbbpp 24/32
(==) intel(0): Depth 24, (--) framebuffer bpp 32
(==) intel(0): RGB weight 888
(==) intel(0): Default visual is TrueColor
(II) intel(0): Integrated Graphics Chipset: Intel(R) Pineview GM
(--) intel(0): Chipset: "Pineview GM"
(II) intel(0): Output VGA1 has no monitor section
(II) intel(0): Output LVDS1 has no monitor section
(II) intel(0): found backlight control interface /sys/class/backlight/acpi_video0
(II) intel(0): EDID for output VGA1
(II) intel(0): EDID for output LVDS1
(II) intel(0): Manufacturer: AUO  Model: 30d2  Serial#: 0
(II) intel(0): Year: 2008  Week: 1
(II) intel(0): EDID Version: 1.3
(II) intel(0): Digital Display Input
(II) intel(0): Max Image Size [cm]: horiz.: 22  vert.: 13
(II) intel(0): Gamma: 2.20
(II) intel(0): No DPMS capabilities specified
(II) intel(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) intel(0): First detailed timing is preferred mode
(II) intel(0): redX: 0.588 redY: 0.351   greenX: 0.342 greenY: 0.567
(II) intel(0): blueX: 0.158 blueY: 0.123   whiteX: 0.313 whiteY: 0.329
(II) intel(0): Manufacturer's mask: 0
(II) intel(0): Supported detailed timing:
(II) intel(0): clock: 52.0 MHz   Image Size:  223 x 125 mm
(II) intel(0): h_active: 1024  h_sync: 1048  h_sync_end 1184 h_blank_end 1344 h_border: 0
(II) intel(0): v_active: 600  v_sync: 603  v_sync_end 604 v_blanking: 644 v_border: 0
(II) intel(0): Unknown vendor-specific block f
(II) intel(0):  AUO
(II) intel(0):  B101AW03 V0
(II) intel(0): EDID (in hex):
(II) intel(0): 	00ffffffffffff0006afd23000000000
(II) intel(0): 	0112010380160d780ab9a59659579128
(II) intel(0): 	1f505400000001010101010101010101
(II) intel(0): 	0101010101015014004041582c201888
(II) intel(0): 	3100df7d000000180000000f00000000
(II) intel(0): 	00000000000000000020000000fe0041
(II) intel(0): 	554f0a202020202020202020000000fe
(II) intel(0): 	004231303141573033205630200a003c
(II) intel(0): Not using default mode "320x175" (doublescan mode not supported)
(II) intel(0): Not using default mode "320x200" (doublescan mode not supported)
(II) intel(0): Not using default mode "360x200" (doublescan mode not supported)
(II) intel(0): Not using default mode "320x240" (doublescan mode not supported)
(II) intel(0): Not using default mode "320x240" (doublescan mode not supported)
(II) intel(0): Not using default mode "320x240" (doublescan mode not supported)
(II) intel(0): Not using default mode "320x240" (doublescan mode not supported)
(II) intel(0): Not using default mode "400x300" (doublescan mode not supported)
(II) intel(0): Not using default mode "400x300" (doublescan mode not supported)
(II) intel(0): Not using default mode "400x300" (doublescan mode not supported)
(II) intel(0): Not using default mode "400x300" (doublescan mode not supported)
(II) intel(0): Not using default mode "400x300" (doublescan mode not supported)
(II) intel(0): Not using default mode "1024x768" (interlace mode not supported)
(II) intel(0): Not using default mode "512x384" (doublescan mode not supported)
(II) intel(0): Not using default mode "1024x768" (exceeds panel dimensions)
(II) intel(0): Not using default mode "512x384" (doublescan mode not supported)
(II) intel(0): Not using default mode "1024x768" (exceeds panel dimensions)
(II) intel(0): Not using default mode "512x384" (doublescan mode not supported)
(II) intel(0): Not using default mode "1024x768" (exceeds panel dimensions)
(II) intel(0): Not using default mode "512x384" (doublescan mode not supported)
(II) intel(0): Not using default mode "1024x768" (exceeds panel dimensions)
(II) intel(0): Not using default mode "512x384" (doublescan mode not supported)
(II) intel(0): Not using default mode "1152x864" (exceeds panel dimensions)
(II) intel(0): Not using default mode "576x432" (doublescan mode not supported)
(II) intel(0): Not using default mode "1280x960" (exceeds panel dimensions)
(II) intel(0): Not using default mode "640x480" (doublescan mode not supported)
(II) intel(0): Not using default mode "1280x960" (exceeds panel dimensions)
(II) intel(0): Not using default mode "640x480" (doublescan mode not supported)
(II) intel(0): Not using default mode "1280x1024" (exceeds panel dimensions)
(II) intel(0): Not using default mode "640x512" (doublescan mode not supported)
(II) intel(0): Not using default mode "1280x1024" (exceeds panel dimensions)
(II) intel(0): Not using default mode "640x512" (doublescan mode not supported)
(II) intel(0): Not using default mode "1280x1024" (exceeds panel dimensions)
(II) intel(0): Not using default mode "640x512" (doublescan mode not supported)
(II) intel(0): Not using default mode "1600x1200" (exceeds panel dimensions)
(II) intel(0): Not using default mode "800x600" (doublescan mode not supported)
(II) intel(0): Not using default mode "1600x1200" (exceeds panel dimensions)
(II) intel(0): Not using default mode "800x600" (doublescan mode not supported)
(II) intel(0): Not using default mode "1600x1200" (exceeds panel dimensions)
(II) intel(0): Not using default mode "800x600" (doublescan mode not supported)
(II) intel(0): Not using default mode "1600x1200" (exceeds panel dimensions)
(II) intel(0): Not using default mode "800x600" (doublescan mode not supported)
(II) intel(0): Not using default mode "1600x1200" (exceeds panel dimensions)
(II) intel(0): Not using default mode "800x600" (doublescan mode not supported)
(II) intel(0): Not using default mode "1792x1344" (exceeds panel dimensions)
(II) intel(0): Not using default mode "896x672" (doublescan mode not supported)
(II) intel(0): Not using default mode "1792x1344" (exceeds panel dimensions)
(II) intel(0): Not using default mode "896x672" (doublescan mode not supported)
(II) intel(0): Not using default mode "1856x1392" (exceeds panel dimensions)
(II) intel(0): Not using default mode "928x696" (doublescan mode not supported)
(II) intel(0): Not using default mode "1856x1392" (exceeds panel dimensions)
(II) intel(0): Not using default mode "928x696" (doublescan mode not supported)
(II) intel(0): Not using default mode "1920x1440" (exceeds panel dimensions)
(II) intel(0): Not using default mode "960x720" (doublescan mode not supported)
(II) intel(0): Not using default mode "1920x1440" (exceeds panel dimensions)
(II) intel(0): Not using default mode "960x720" (doublescan mode not supported)
(II) intel(0): Not using default mode "832x624" (exceeds panel dimensions)
(II) intel(0): Not using default mode "416x312" (doublescan mode not supported)
(II) intel(0): Not using default mode "1152x864" (exceeds panel dimensions)
(II) intel(0): Not using default mode "576x432" (doublescan mode not supported)
(II) intel(0): Not using default mode "1152x864" (exceeds panel dimensions)
(II) intel(0): Not using default mode "576x432" (doublescan mode not supported)
(II) intel(0): Not using default mode "1152x864" (exceeds panel dimensions)
(II) intel(0): Not using default mode "576x432" (doublescan mode not supported)
(II) intel(0): Not using default mode "1152x864" (exceeds panel dimensions)
(II) intel(0): Not using default mode "576x432" (doublescan mode not supported)
(II) intel(0): Not using default mode "1152x864" (exceeds panel dimensions)
(II) intel(0): Not using default mode "576x432" (doublescan mode not supported)
(II) intel(0): Not using default mode "1152x864" (exceeds panel dimensions)
(II) intel(0): Not using default mode "576x432" (doublescan mode not supported)
(II) intel(0): Not using default mode "1360x768" (monitor doesn't support reduced blanking)
(II) intel(0): Not using default mode "680x384" (doublescan mode not supported)
(II) intel(0): Not using default mode "1360x768" (exceeds panel dimensions)
(II) intel(0): Not using default mode "680x384" (doublescan mode not supported)
(II) intel(0): Not using default mode "1400x1050" (exceeds panel dimensions)
(II) intel(0): Not using default mode "700x525" (doublescan mode not supported)
(II) intel(0): Not using default mode "1400x1050" (exceeds panel dimensions)
(II) intel(0): Not using default mode "700x525" (doublescan mode not supported)
(II) intel(0): Not using default mode "1400x1050" (exceeds panel dimensions)
(II) intel(0): Not using default mode "700x525" (doublescan mode not supported)
(II) intel(0): Not using default mode "1400x1050" (exceeds panel dimensions)
(II) intel(0): Not using default mode "700x525" (doublescan mode not supported)
(II) intel(0): Not using default mode "1440x900" (exceeds panel dimensions)
(II) intel(0): Not using default mode "720x450" (doublescan mode not supported)
(II) intel(0): Not using default mode "1600x1024" (exceeds panel dimensions)
(II) intel(0): Not using default mode "800x512" (doublescan mode not supported)
(II) intel(0): Not using default mode "1680x1050" (monitor doesn't support reduced blanking)
(II) intel(0): Not using default mode "840x525" (doublescan mode not supported)
(II) intel(0): Not using default mode "1680x1050" (exceeds panel dimensions)
(II) intel(0): Not using default mode "840x525" (doublescan mode not supported)
(II) intel(0): Not using default mode "1680x1050" (exceeds panel dimensions)
(II) intel(0): Not using default mode "840x525" (doublescan mode not supported)
(II) intel(0): Not using default mode "1680x1050" (exceeds panel dimensions)
(II) intel(0): Not using default mode "840x525" (doublescan mode not supported)
(II) intel(0): Not using default mode "1680x1050" (exceeds panel dimensions)
(II) intel(0): Not using default mode "840x525" (doublescan mode not supported)
(II) intel(0): Not using default mode "1920x1080" (monitor doesn't support reduced blanking)
(II) intel(0): Not using default mode "960x540" (doublescan mode not supported)
(II) intel(0): Not using default mode "1920x1200" (monitor doesn't support reduced blanking)
(II) intel(0): Not using default mode "960x600" (doublescan mode not supported)
(II) intel(0): Not using default mode "1920x1440" (exceeds panel dimensions)
(II) intel(0): Not using default mode "960x720" (doublescan mode not supported)
(II) intel(0): Not using default mode "2048x1536" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1024x768" (doublescan mode not supported)
(II) intel(0): Not using default mode "2048x1536" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1024x768" (doublescan mode not supported)
(II) intel(0): Not using default mode "2048x1536" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1024x768" (doublescan mode not supported)
(II) intel(0): Printing probed modes for output LVDS1
(II) intel(0): Modeline "1024x600"x60.1   52.00  1024 1048 1184 1344  600 603 604 644 -hsync -vsync (38.7 kHz)
(II) intel(0): Modeline "800x600"x85.1   56.30  800 832 896 1048  600 601 604 631 +hsync +vsync (53.7 kHz)
(II) intel(0): Modeline "800x600"x72.2   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(II) intel(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) intel(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) intel(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) intel(0): Modeline "640x480"x85.0   36.00  640 696 752 832  480 481 484 509 -hsync -vsync (43.3 kHz)
(II) intel(0): Modeline "640x480"x72.8   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
(II) intel(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) intel(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) intel(0): Modeline "720x400"x85.0   35.50  720 756 828 936  400 401 404 446 -hsync +vsync (37.9 kHz)
(II) intel(0): Modeline "640x400"x85.1   31.50  640 672 736 832  400 401 404 445 -hsync +vsync (37.9 kHz)
(II) intel(0): Modeline "640x350"x85.1   31.50  640 672 736 832  350 382 385 445 +hsync -vsync (37.9 kHz)
(II) intel(0): Output VGA1 disconnected
(II) intel(0): Output LVDS1 connected
(II) intel(0): Using exact sizes for initial modes
(II) intel(0): Output LVDS1 using initial mode 1024x600
(II) intel(0): Using default gamma of (1.0, 1.0, 1.0) unless otherwise stated.
(==) intel(0): video overlay key set to 0x101fe
(==) intel(0): DPI set to (96, 96)
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules/libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.4
(II) UnloadModule: "vesa"
(II) Unloading /usr/lib/xorg/modules/drivers/vesa_drv.so
(II) UnloadModule: "fbdev"
(II) Unloading /usr/lib/xorg/modules/drivers/fbdev_drv.so
(II) UnloadModule: "fbdevhw"
(II) Unloading /usr/lib/xorg/modules/linux/libfbdevhw.so
(==) Depth 24 pixmap format is 32 bpp
(II) intel(0): [DRI2] Setup complete
(**) intel(0): Framebuffer compression disabled
(**) intel(0): Tiling enabled
(**) intel(0): SwapBuffers wait enabled
(==) intel(0): VideoRam: 262144 KB
(II) intel(0): Attempting memory allocation with tiled buffers.
(II) intel(0): Tiled allocation successful.
(II) UXA(0): Driver registered support for the following operations:
(II)         solid
(II)         copy
(II)         composite (RENDER acceleration)
(==) intel(0): Backing store disabled
(==) intel(0): Silken mouse enabled
(II) intel(0): Initializing HW Cursor
(II) intel(0): No memory allocations
(II) intel(0): RandR 1.2 enabled, ignore the following RandR disabled message.
(==) intel(0): DPMS enabled
(==) intel(0): Intel XvMC decoder disabled
(II) intel(0): Set up textured video
(II) intel(0): Set up overlay video
(II) intel(0): direct rendering: DRI2 Enabled
(--) RandR disabled
(II) Initializing built-in extension Generic Event Extension
(II) Initializing built-in extension SHAPE
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension BIG-REQUESTS
(II) Initializing built-in extension SYNC
(II) Initializing built-in extension XKEYBOARD
(II) Initializing built-in extension XC-MISC
(II) Initializing built-in extension SECURITY
(II) Initializing built-in extension XINERAMA
(II) Initializing built-in extension XFIXES
(II) Initializing built-in extension RENDER
(II) Initializing built-in extension RANDR
(II) Initializing built-in extension COMPOSITE
(II) Initializing built-in extension DAMAGE
(II) AIGLX: enabled GLX_MESA_copy_sub_buffer
(II) AIGLX: enabled GLX_SGI_make_current_read
(II) AIGLX: enabled GLX_SGI_swap_control and GLX_MESA_swap_control
(II) AIGLX: GLX_EXT_texture_from_pixmap backed by buffer objects
(II) AIGLX: Loaded and initialized /usr/lib/dri/i915_dri.so
(II) GLX: Initialized DRI2 GL provider for screen 0
(II) intel(0): Setting screen physical size to 270 x 158
(II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
(II) config/udev: Adding input device Power Button (/dev/input/event3)
(**) Power Button: Applying InputClass "evdev keyboard catchall"
(II) LoadModule: "evdev"
(II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
(II) Module evdev: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 2.3.2
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 7.0
(**) Power Button: always reports core events
(**) Power Button: Device: "/dev/input/event3"
(II) Power Button: Found keys
(II) Power Button: Configuring as keyboard
(II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(II) config/udev: Adding input device Video Bus (/dev/input/event6)
(**) Video Bus: Applying InputClass "evdev keyboard catchall"
(**) Video Bus: always reports core events
(**) Video Bus: Device: "/dev/input/event6"
(II) Video Bus: Found keys
(II) Video Bus: Configuring as keyboard
(II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(II) config/udev: Adding input device Power Button (/dev/input/event0)
(**) Power Button: Applying InputClass "evdev keyboard catchall"
(**) Power Button: always reports core events
(**) Power Button: Device: "/dev/input/event0"
(II) Power Button: Found keys
(II) Power Button: Configuring as keyboard
(II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(II) config/udev: Adding input device Lid Switch (/dev/input/event2)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: Adding input device Sleep Button (/dev/input/event1)
(**) Sleep Button: Applying InputClass "evdev keyboard catchall"
(**) Sleep Button: always reports core events
(**) Sleep Button: Device: "/dev/input/event1"
(II) Sleep Button: Found keys
(II) Sleep Button: Configuring as keyboard
(II) XINPUT: Adding extended input device "Sleep Button" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(II) config/udev: Adding input device HDA Digital PCBeep (/dev/input/event8)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: Adding input device WebCam (/dev/input/event7)
(**) WebCam: Applying InputClass "evdev keyboard catchall"
(**) WebCam: always reports core events
(**) WebCam: Device: "/dev/input/event7"
(II) WebCam: Found keys
(II) WebCam: Configuring as keyboard
(II) XINPUT: Adding extended input device "WebCam" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event5)
(**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
(**) AT Translated Set 2 keyboard: always reports core events
(**) AT Translated Set 2 keyboard: Device: "/dev/input/event5"
(II) AT Translated Set 2 keyboard: Found keys
(II) AT Translated Set 2 keyboard: Configuring as keyboard
(II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(II) config/udev: Adding input device PS/2 Synaptics TouchPad (/dev/input/event9)
(**) PS/2 Synaptics TouchPad: Applying InputClass "evdev pointer catchall"
(**) PS/2 Synaptics TouchPad: always reports core events
(**) PS/2 Synaptics TouchPad: Device: "/dev/input/event9"
(II) PS/2 Synaptics TouchPad: Found 3 mouse buttons
(II) PS/2 Synaptics TouchPad: Found relative axes
(II) PS/2 Synaptics TouchPad: Found x and y relative axes
(II) PS/2 Synaptics TouchPad: Configuring as mouse
(**) PS/2 Synaptics TouchPad: YAxisMapping: buttons 4 and 5
(**) PS/2 Synaptics TouchPad: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "PS/2 Synaptics TouchPad" (type: MOUSE)
(II) PS/2 Synaptics TouchPad: initialized for relative axes.
(II) config/udev: Adding input device PS/2 Synaptics TouchPad (/dev/input/mouse1)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: Adding input device Macintosh mouse button emulation (/dev/input/event4)
(**) Macintosh mouse button emulation: Applying InputClass "evdev pointer catchall"
(**) Macintosh mouse button emulation: always reports core events
(**) Macintosh mouse button emulation: Device: "/dev/input/event4"
(II) Macintosh mouse button emulation: Found 3 mouse buttons
(II) Macintosh mouse button emulation: Found relative axes
(II) Macintosh mouse button emulation: Found x and y relative axes
(II) Macintosh mouse button emulation: Configuring as mouse
(**) Macintosh mouse button emulation: YAxisMapping: buttons 4 and 5
(**) Macintosh mouse button emulation: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "Macintosh mouse button emulation" (type: MOUSE)
(II) Macintosh mouse button emulation: initialized for relative axes.
(II) config/udev: Adding input device Macintosh mouse button emulation (/dev/input/mouse0)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: Adding input device HDA Digital PCBeep (/dev/input/event8)
(II) No input driver/identifier specified (ignoring)
(II) intel(0): EDID vendor "AUO", prod id 12498
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1024x600"x0.0   52.00  1024 1048 1184 1344  600 603 604 644 -hsync -vsync (38.7 kHz)
(II) intel(0): EDID vendor "AUO", prod id 12498
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1024x600"x0.0   52.00  1024 1048 1184 1344  600 603 604 644 -hsync -vsync (38.7 kHz)
(II) intel(0): EDID vendor "AUO", prod id 12498
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1024x600"x0.0   52.00  1024 1048 1184 1344  600 603 604 644 -hsync -vsync (38.7 kHz)
(II) intel(0): EDID vendor "AUO", prod id 12498
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1024x600"x0.0   52.00  1024 1048 1184 1344  600 603 604 644 -hsync -vsync (38.7 kHz)
(II) intel(0): EDID vendor "AUO", prod id 12498
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1024x600"x0.0   52.00  1024 1048 1184 1344  600 603 604 644 -hsync -vsync (38.7 kHz)
(II) intel(0): EDID vendor "AUO", prod id 12498
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1024x600"x0.0   52.00  1024 1048 1184 1344  600 603 604 644 -hsync -vsync (38.7 kHz)


---

### Post by MountainX on 2010-07-31
reinstalled fresh Linux Mint 9 and the touchpad, including edge scrolling, works out of the box.

---

