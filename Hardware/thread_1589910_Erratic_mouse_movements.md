---
title: "Erratic mouse movements"
date: 2010-10-07
forum: Hardware
---

### Post by blofse on 2010-10-07
I'm having a problem where, when I move the mouse, the mouse will  suddenly jolt in a different direction, occasionally acting as if I  pressed the mouse button as well. Pretty annoying when it does some random clicks and seemingly (not sure  how) doing random pasting of text!

I'm running Ubuntu 10.04  and a "Microsoft Basic Opitical Mouse 1.0A". 
This problem only impacts optical mice, but however it is now not an option to use a rollerball.

See various threads for ref:
[http://wwww.ubuntuforums.org/showthread.php?p=9926755](http://wwww.ubuntuforums.org/showthread.php?p=9926755)
[http://wwww.ubuntuforums.org/showthread.php?t=20731](http://wwww.ubuntuforums.org/showthread.php?t=20731)
[http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1501363](http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1501363)

I have just checked and it appears I don't have an xorg.conf in the standard place! Secondly, I have had very bad past experiences with editing that file and so without explicitly getting a absolute answer I would rather check with you guys.

So has anyone had a go at this? Did you have any luck and what exactly did you change?

ps. 
I seem to remember this problem a long time ago on windows when optical  first came out. This was fixed by a newer driver (some patch for windows  - which ever version is was using - probably win2k), so could this be  the same on Ubuntu? Has something taken a step back or has someone  implemented this bad code from M$?

---

### Post by P4man on 2010-10-07
I assume you are certain the mouse is fine?

Some questions first: is this a PS/2 or USB mouse?  Is this a laptop with touchpad or a desktop? If its a laptop, did you try disabling the touchpad to make sure its not "interference" ?

As for xorg.conf, this file is optional nowadays. You can create one to set custom settings, but its normal if you dont have one. You can create a default file by running:

```
sudo Xorg -configure
```

(note the upcase X). That will create one in the current folder (probably your home folder) called "xorg.conf.new". You can move it to its correct name and location by running

```
sudo mv ./xorg.conf.new /etc/X11/xorg.conf
```

But to be honest, I dont think its a xorg issue. I suspect you have a PS2 mouse and its a kernel/bios issue. Perhaps you can post the output of 

```
dmesg
```

?

---

### Post by blofse on 2010-10-08
Thank you very much for your reply!

As for the mouse being fine, I have not confirmed on other machines so I will do that in a bit when I get a chance to try on someone else's machine (windows box so I can double check).

It is a USB mouse.

Here is the requested output:
> 
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.32-25-generic (buildd@rothera) (gcc version 4.4.3 (Ubuntu 4.4.3-4ubuntu5) ) #44-Ubuntu SMP Fri Sep 17 20:26:08 UTC 2010 (Ubuntu 2.6.32-25.44-generic 2.6.32.21+drm33.7)
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
[    0.000000]  BIOS-e820: 0000000000000000 - 00000000000a0000 (usable)
[    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 00000000bfe86c00 (usable)
[    0.000000]  BIOS-e820: 00000000bfe86c00 - 00000000bfe88c00 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000bfe88c00 - 00000000bfe8ac00 (ACPI data)
[    0.000000]  BIOS-e820: 00000000bfe8ac00 - 00000000c0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fed00400 (reserved)
[    0.000000]  BIOS-e820: 00000000fed20000 - 00000000feda0000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fef00000 (reserved)
[    0.000000]  BIOS-e820: 00000000ffb00000 - 0000000100000000 (reserved)
[    0.000000] DMI 2.3 present.
[    0.000000] last_pfn = 0xbfe86 max_arch_pfn = 0x100000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-CFFFF write-protect
[    0.000000]   D0000-EFFFF uncachable
[    0.000000]   F0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000 mask F80000000 write-back
[    0.000000]   1 base 080000000 mask FC0000000 write-back
[    0.000000]   2 base 0BFF00000 mask FFFF00000 uncachable
[    0.000000]   3 disabled
[    0.000000]   4 disabled
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] e820 update range: 0000000000002000 - 0000000000006000 (usable) ==> (reserved)
[    0.000000] Scanning 1 areas for low memory corruption
[    0.000000] modified physical RAM map:
[    0.000000]  modified: 0000000000000000 - 0000000000002000 (usable)
[    0.000000]  modified: 0000000000002000 - 0000000000006000 (reserved)
[    0.000000]  modified: 0000000000006000 - 00000000000a0000 (usable)
[    0.000000]  modified: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  modified: 0000000000100000 - 00000000bfe86c00 (usable)
[    0.000000]  modified: 00000000bfe86c00 - 00000000bfe88c00 (ACPI NVS)
[    0.000000]  modified: 00000000bfe88c00 - 00000000bfe8ac00 (ACPI data)
[    0.000000]  modified: 00000000bfe8ac00 - 00000000c0000000 (reserved)
[    0.000000]  modified: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  modified: 00000000fec00000 - 00000000fed00400 (reserved)
[    0.000000]  modified: 00000000fed20000 - 00000000feda0000 (reserved)
[    0.000000]  modified: 00000000fee00000 - 00000000fef00000 (reserved)
[    0.000000]  modified: 00000000ffb00000 - 0000000100000000 (reserved)
[    0.000000] initial memory mapped : 0 - 00c00000
[    0.000000] init_memory_mapping: 0000000000000000-00000000377fe000
[    0.000000] Using x86 segment limits to approximate NX protection
[    0.000000]  0000000000 - 0000400000 page 4k
[    0.000000]  0000400000 - 0037400000 page 2M
[    0.000000]  0037400000 - 00377fe000 page 4k
[    0.000000] kernel direct mapping tables up to 377fe000 @ 7000-c000
[    0.000000] RAMDISK: 37796000 - 37fef98b
[    0.000000] Allocated new RAMDISK: 008e1000 - 0113a98b
[    0.000000] Move RAMDISK from 0000000037796000 - 0000000037fef98a to 008e1000 - 0113a98a
[    0.000000] ACPI: RSDP 000fec00 00014 (v00 DELL  )
[    0.000000] ACPI: RSDT 000fcc05 00040 (v01 DELL    GX280   00000007 ASL  00000061)
[    0.000000] ACPI: FACP 000fcc45 00074 (v01 DELL    GX280   00000007 ASL  00000061)
[    0.000000] ACPI: DSDT fffd060c 030BF (v01   DELL    dt_ex 00001000 MSFT 0100000D)
[    0.000000] ACPI: FACS bfe86c00 00040
[    0.000000] ACPI: SSDT fffd3808 000BA (v01   DELL    st_ex 00001000 MSFT 0100000D)
[    0.000000] ACPI: APIC 000fccb9 00072 (v01 DELL    GX280   00000007 ASL  00000061)
[    0.000000] ACPI: BOOT 000fcd2b 00028 (v01 DELL    GX280   00000007 ASL  00000061)
[    0.000000] ACPI: ASF! 000fcd53 00067 (v16 DELL    GX280   00000007 ASL  00000061)
[    0.000000] ACPI: MCFG 000fcdba 0003E (v01 DELL    GX280   00000007 ASL  00000061)
[    0.000000] ACPI: HPET 000fcdf8 00038 (v01 DELL    GX280   00000007 ASL  00000061)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] 2182MB HIGHMEM available.
[    0.000000] 887MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 377fe000
[    0.000000]   low ram: 0 - 377fe000
[    0.000000]   node 0 low ram: 00000000 - 377fe000
[    0.000000]   node 0 bootmap 00008000 - 0000ef00
[    0.000000] (9 early reservations) ==> bootmem [0000000000 - 00377fe000]
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000]   #1 [0000001000 - 0000002000]    EX TRAMPOLINE ==> [0000001000 - 0000002000]
[    0.000000]   #2 [0000006000 - 0000007000]       TRAMPOLINE ==> [0000006000 - 0000007000]
[    0.000000]   #3 [0000100000 - 00008dced8]    TEXT DATA BSS ==> [0000100000 - 00008dced8]
[    0.000000]   #4 [000009fc00 - 0000100000]    BIOS reserved ==> [000009fc00 - 0000100000]
[    0.000000]   #5 [00008dd000 - 00008e0190]              BRK ==> [00008dd000 - 00008e0190]
[    0.000000]   #6 [0000007000 - 0000008000]          PGTABLE ==> [0000007000 - 0000008000]
[    0.000000]   #7 [00008e1000 - 000113a98b]      NEW RAMDISK ==> [00008e1000 - 000113a98b]
[    0.000000]   #8 [0000008000 - 000000f000]          BOOTMAP ==> [0000008000 - 000000f000]
[    0.000000] found SMP MP-table at [c00fe710] fe710
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000000 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x000377fe
[    0.000000]   HighMem  0x000377fe -> 0x000bfe86
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[3] active PFN ranges
[    0.000000]     0: 0x00000000 -> 0x00000002
[    0.000000]     0: 0x00000006 -> 0x000000a0
[    0.000000]     0: 0x00000100 -> 0x000bfe86
[    0.000000] On node 0 totalpages: 785954
[    0.000000] free_area_init_node: node 0, pgdat c079a760, node_mem_map c113c000
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3964 pages, LIFO batch:0
[    0.000000]   Normal zone: 1744 pages used for memmap
[    0.000000]   Normal zone: 221486 pages, LIFO batch:31
[    0.000000]   HighMem zone: 4366 pages used for memmap
[    0.000000]   HighMem zone: 554362 pages, LIFO batch:31
[    0.000000] Using APIC driver default
[    0.000000] ACPI: PM-Timer IO Port: 0x808
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x01] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x07] disabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0xff] high level lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x08] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 8, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
[    0.000000] SMP: Allowing 4 CPUs, 3 hotplug CPUs
[    0.000000] nr_irqs_gsi: 24
[    0.000000] PM: Registered nosave memory: 0000000000002000 - 0000000000006000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000f0000
[    0.000000] PM: Registered nosave memory: 00000000000f0000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at c0000000 (gap: c0000000:20000000)
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:4 nr_node_ids:1
[    0.000000] PERCPU: Embedded 14 pages/cpu @c2c00000 s36056 r0 d21288 u1048576
[    0.000000] pcpu-alloc: s36056 r0 d21288 u1048576 alloc=1*4194304
[    0.000000] pcpu-alloc: [0] 0 1 2 3 
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 779812
[    0.000000] Kernel command line: root=UUID=970f7fdd-2279-47ea-8aae-a39134537753 ro quiet splash 
[    0.000000] PID hash table entries: 4096 (order: 2, 16384 bytes)
[    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] allocated 15721080 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] Initializing HighMem for node 0 (000377fe:000bfe86)
[    0.000000] Memory: 3084996k/3144216k available (4680k kernel code, 57672k reserved, 2122k data, 656k init, 2234912k highmem)
[    0.000000] virtual kernel memory layout:
[    0.000000]     fixmap  : 0xfff1d000 - 0xfffff000   ( 904 kB)
[    0.000000]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[    0.000000]     vmalloc : 0xf7ffe000 - 0xff7fe000   ( 120 MB)
[    0.000000]     lowmem  : 0xc0000000 - 0xf77fe000   ( 887 MB)
[    0.000000]       .init : 0xc07a5000 - 0xc0849000   ( 656 kB)
[    0.000000]       .data : 0xc05922c7 - 0xc07a4e68   (2122 kB)
[    0.000000]       .text : 0xc0100000 - 0xc05922c7   (4680 kB)
[    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.000000] SLUB: Genslabs=13, HWalign=128, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000] NR_IRQS:2304 nr_irqs:440
[    0.000000] Console: colour VGA+ 80x25
[    0.000000] console [tty0] enabled
[    0.000000] hpet clockevent registered
[    0.000000] HPET: 3 timers in total, 0 timers will be used for per-cpu timer
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 2993.067 MHz processor.
[    0.004007] Calibrating delay loop (skipped), value calculated using timer frequency.. 5986.13 BogoMIPS (lpj=11972268)
[    0.004028] Security Framework initialized
[    0.004052] AppArmor: AppArmor initialized
[    0.004062] Mount-cache hash table entries: 512
[    0.004222] Initializing cgroup subsys ns
[    0.004228] Initializing cgroup subsys cpuacct
[    0.004234] Initializing cgroup subsys memory
[    0.004243] Initializing cgroup subsys devices
[    0.004246] Initializing cgroup subsys freezer
[    0.004249] Initializing cgroup subsys net_cls
[    0.004279] CPU: Trace cache: 12K uops, L1 D cache: 16K
[    0.004283] CPU: L2 cache: 1024K
[    0.004286] CPU: Physical Processor ID: 0
[    0.004289] CPU: Processor Core ID: 0
[    0.004294] mce: CPU supports 4 MCE banks
[    0.004308] CPU0: Thermal monitoring enabled (TM1)
[    0.004314] using mwait in idle threads.
[    0.004322] Performance Events: no PMU driver, software events only.
[    0.004330] Checking 'hlt' instruction... OK.
[    0.021110] SMP alternatives: switching to UP code
[    0.033370] ACPI: Core revision 20090903
[    0.082923] ftrace: converting mcount calls to 0f 1f 44 00 00
[    0.082930] ftrace: allocating 21789 entries in 43 pages
[    0.084068] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.084386] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.124325] CPU0: Intel(R) Pentium(R) 4 CPU 3.00GHz stepping 01
[    0.128001] Brought up 1 CPUs
[    0.128001] Total of 1 processors activated (5986.13 BogoMIPS).
[    0.128001] CPU0 attaching NULL sched-domain.
[    0.128001] devtmpfs: initialized
[    0.128001] regulator: core version 0.5
[    0.128001] Time: 13:39:03  Date: 10/07/10
[    0.128001] NET: Registered protocol family 16
[    0.128001] EISA bus registered
[    0.128001] ACPI: bus type pci registered
[    0.128001] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 255
[    0.128001] PCI: MCFG area at e0000000 reserved in E820
[    0.128001] PCI: Using MMCONFIG for extended config space
[    0.128001] PCI: Using configuration type 1 for base access
[    0.128001] bio: create slab <bio-0> at 0
[    0.128001] ACPI: EC: Look up EC in DSDT
[    0.154863] ACPI: Interpreter enabled
[    0.154870] ACPI: (supports S0 S1 S3 S4 S5)
[    0.154899] ACPI: Using IOAPIC for interrupt routing
[    0.188707] ACPI: No dock devices found.
[    0.191619] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.191753] pci 0000:00:01.0: PME# supported from D0 D3hot D3cold
[    0.191758] pci 0000:00:01.0: PME# disabled
[    0.191851] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.191856] pci 0000:00:1c.0: PME# disabled
[    0.191925] pci 0000:00:1c.1: PME# supported from D0 D3hot D3cold
[    0.191930] pci 0000:00:1c.1: PME# disabled
[    0.191984] pci 0000:00:1d.0: reg 20 io port: [0xff80-0xff9f]
[    0.192047] pci 0000:00:1d.1: reg 20 io port: [0xff60-0xff7f]
[    0.192101] pci 0000:00:1d.2: reg 20 io port: [0xff40-0xff5f]
[    0.192153] pci 0000:00:1d.3: reg 20 io port: [0xff20-0xff3f]
[    0.192211] pci 0000:00:1d.7: reg 10 32bit mmio: [0xffa80800-0xffa80bff]
[    0.192265] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
[    0.192270] pci 0000:00:1d.7: PME# disabled
[    0.192357] pci 0000:00:1e.2: reg 10 io port: [0xec00-0xecff]
[    0.192364] pci 0000:00:1e.2: reg 14 io port: [0xe8c0-0xe8ff]
[    0.192371] pci 0000:00:1e.2: reg 18 32bit mmio: [0xdffffe00-0xdfffffff]
[    0.192378] pci 0000:00:1e.2: reg 1c 32bit mmio: [0xdffffd00-0xdffffdff]
[    0.192407] pci 0000:00:1e.2: PME# supported from D0 D3hot D3cold
[    0.192412] pci 0000:00:1e.2: PME# disabled
[    0.192482] pci 0000:00:1f.0: quirk: region 0800-087f claimed by ICH6 ACPI/GPIO/TCO
[    0.192486] pci 0000:00:1f.0: quirk: region 0880-08bf claimed by ICH6 GPIO
[    0.192491] pci 0000:00:1f.0: LPC Generic IO decode 1 PIO at 0c00-0c7f
[    0.192495] pci 0000:00:1f.0: LPC Generic IO decode 2 PIO at 00e0-00ef
[    0.192521] pci 0000:00:1f.1: reg 10 io port: [0x1f0-0x1f7]
[    0.192528] pci 0000:00:1f.1: reg 14 io port: [0x3f4-0x3f7]
[    0.192535] pci 0000:00:1f.1: reg 18 io port: [0x170-0x177]
[    0.192543] pci 0000:00:1f.1: reg 1c io port: [0x374-0x377]
[    0.192550] pci 0000:00:1f.1: reg 20 io port: [0xffa0-0xffaf]
[    0.192599] pci 0000:00:1f.2: reg 10 io port: [0xfe00-0xfe07]
[    0.192606] pci 0000:00:1f.2: reg 14 io port: [0xfe10-0xfe13]
[    0.192612] pci 0000:00:1f.2: reg 18 io port: [0xfe20-0xfe27]
[    0.192619] pci 0000:00:1f.2: reg 1c io port: [0xfe30-0xfe33]
[    0.192625] pci 0000:00:1f.2: reg 20 io port: [0xfea0-0xfeaf]
[    0.192652] pci 0000:00:1f.2: PME# supported from D3hot
[    0.192656] pci 0000:00:1f.2: PME# disabled
[    0.192704] pci 0000:00:1f.3: reg 20 io port: [0xe8a0-0xe8bf]
[    0.192761] pci 0000:01:00.0: reg 10 32bit mmio pref: [0xd0000000-0xd7ffffff]
[    0.192768] pci 0000:01:00.0: reg 14 io port: [0xdc00-0xdcff]
[    0.192774] pci 0000:01:00.0: reg 18 32bit mmio: [0xdfde0000-0xdfdeffff]
[    0.192792] pci 0000:01:00.0: reg 30 32bit mmio pref: [0xdfe00000-0xdfe1ffff]
[    0.192813] pci 0000:01:00.0: supports D1 D2
[    0.192846] pci 0000:01:00.1: reg 10 32bit mmio: [0xdfdf0000-0xdfdfffff]
[    0.192887] pci 0000:01:00.1: supports D1 D2
[    0.192933] pci 0000:00:01.0: bridge io port: [0xd000-0xdfff]
[    0.192937] pci 0000:00:01.0: bridge 32bit mmio: [0xdfd00000-0xdfefffff]
[    0.192942] pci 0000:00:01.0: bridge 32bit mmio pref: [0xd0000000-0xd7ffffff]
[    0.193007] pci 0000:02:00.0: reg 10 64bit mmio: [0xdfcf0000-0xdfcfffff]
[    0.193083] pci 0000:02:00.0: PME# supported from D3hot D3cold
[    0.193089] pci 0000:02:00.0: PME# disabled
[    0.193139] pci 0000:00:1c.0: bridge 32bit mmio: [0xdfc00000-0xdfcfffff]
[    0.193188] pci 0000:00:1c.1: bridge 32bit mmio: [0xdfb00000-0xdfbfffff]
[    0.193243] pci 0000:00:1e.0: transparent bridge
[    0.193269] pci_bus 0000:00: on NUMA node 0
[    0.193275] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.193585] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCI1._PRT]
[    0.193949] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCI2._PRT]
[    0.194140] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCI3._PRT]
[    0.194329] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCI4._PRT]
[    0.477908] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 9 10 *11 12 15)
[    0.478248] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 9 *10 11 12 15)
[    0.478588] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 *4 5 6 7 9 10 11 12 15)
[    0.478920] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 9 10 11 12 15) *0, disabled.
[    0.479258] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 9 *10 11 12 15)
[    0.479595] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 *9 10 11 12 15)
[    0.479930] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 *5 6 7 9 10 11 12 15)
[    0.480281] ACPI: PCI Interrupt Link [LNKH] (IRQs *3 4 5 6 7 9 10 11 12 15)
[    0.480466] vgaarb: device added: PCI:0000:01:00.0,decodes=io+mem,owns=io+mem,locks=none
[    0.480470] vgaarb: loaded
[    0.480626] SCSI subsystem initialized
[    0.480690] libata version 3.00 loaded.
[    0.480782] usbcore: registered new interface driver usbfs
[    0.480799] usbcore: registered new interface driver hub
[    0.480830] usbcore: registered new device driver usb
[    0.480984] ACPI: WMI: Mapper loaded
[    0.480987] PCI: Using ACPI for IRQ routing
[    0.481153] NetLabel: Initializing
[    0.481157] NetLabel:  domain hash size = 128
[    0.481158] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.481173] NetLabel:  unlabeled traffic allowed by default
[    0.481214] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[    0.481221] hpet0: 3 comparators, 64-bit 14.318180 MHz counter
[    0.484025] Switching to clocksource tsc
[    0.486148] AppArmor: AppArmor Filesystem Enabled
[    0.486164] pnp: PnP ACPI init
[    0.486179] ACPI: bus type pnp registered
[    0.490666] pnp 00:01: io resource (0x800-0x85f) overlaps 0000:00:1f.0 BAR 13 (0x800-0x87f), disabling
[    0.490672] pnp 00:01: io resource (0x860-0x8ff) overlaps 0000:00:1f.0 BAR 13 (0x800-0x87f), disabling
[    0.508274] pnp: PnP ACPI: found 9 devices
[    0.508277] ACPI: ACPI bus type pnp unregistered
[    0.508282] PnPBIOS: Disabled by ACPI PNP
[    0.508297] system 00:01: ioport range 0xc00-0xc7f has been reserved
[    0.508307] system 00:06: iomem range 0x0-0x9ffff could not be reserved
[    0.508311] system 00:06: iomem range 0x100000-0xffffff could not be reserved
[    0.508315] system 00:06: iomem range 0x1000000-0xbfe86bff could not be reserved
[    0.508318] system 00:06: iomem range 0xc0000-0xfffff could not be reserved
[    0.508322] system 00:06: iomem range 0xfec00000-0xfecfffff could not be reserved
[    0.508325] system 00:06: iomem range 0xfee00000-0xfeefffff has been reserved
[    0.508329] system 00:06: iomem range 0xfed20000-0xfed9ffff has been reserved
[    0.508332] system 00:06: iomem range 0xffb00000-0xffbfffff has been reserved
[    0.508335] system 00:06: iomem range 0xffc00000-0xffffffff has been reserved
[    0.508342] system 00:07: ioport range 0x100-0x1fe could not be reserved
[    0.508346] system 00:07: ioport range 0x200-0x277 has been reserved
[    0.508349] system 00:07: ioport range 0x280-0x2e7 has been reserved
[    0.508352] system 00:07: ioport range 0x2f0-0x2f7 has been reserved
[    0.508355] system 00:07: ioport range 0x300-0x377 could not be reserved
[    0.508358] system 00:07: ioport range 0x380-0x3bb has been reserved
[    0.508362] system 00:07: ioport range 0x3c0-0x3e7 could not be reserved
[    0.508365] system 00:07: ioport range 0x3f6-0x3f7 could not be reserved
[    0.508368] system 00:07: ioport range 0x400-0x4cf has been reserved
[    0.508371] system 00:07: ioport range 0x4d2-0x57f has been reserved
[    0.508374] system 00:07: ioport range 0x580-0x677 has been reserved
[    0.508378] system 00:07: ioport range 0x680-0x777 has been reserved
[    0.508381] system 00:07: ioport range 0x780-0x7bb has been reserved
[    0.508384] system 00:07: ioport range 0x7c0-0x7ff has been reserved
[    0.508387] system 00:07: ioport range 0x8e0-0x8ff has been reserved
[    0.508390] system 00:07: ioport range 0x900-0x9fe has been reserved
[    0.508393] system 00:07: ioport range 0xa00-0xafe has been reserved
[    0.508396] system 00:07: ioport range 0xb00-0xbfe has been reserved
[    0.508399] system 00:07: ioport range 0xc80-0xcaf has been reserved
[    0.508403] system 00:07: ioport range 0xcc0-0xcf7 has been reserved
[    0.508406] system 00:07: ioport range 0xd00-0xdfe has been reserved
[    0.508409] system 00:07: ioport range 0xe00-0xefe has been reserved
[    0.508412] system 00:07: ioport range 0xf00-0xffe has been reserved
[    0.508415] system 00:07: ioport range 0x2000-0x20fe has been reserved
[    0.508419] system 00:07: ioport range 0x2100-0x21fe has been reserved
[    0.508422] system 00:07: ioport range 0x2200-0x22fe has been reserved
[    0.508425] system 00:07: ioport range 0x2300-0x23fe has been reserved
[    0.508428] system 00:07: ioport range 0x2400-0x24fe has been reserved
[    0.508431] system 00:07: ioport range 0x2500-0x25fe has been reserved
[    0.508435] system 00:07: ioport range 0x2600-0x26fe has been reserved
[    0.508438] system 00:07: ioport range 0x2700-0x27fe has been reserved
[    0.508441] system 00:07: ioport range 0x2800-0x28fe has been reserved
[    0.508444] system 00:07: ioport range 0x2900-0x29fe has been reserved
[    0.508448] system 00:07: ioport range 0x2a00-0x2afe has been reserved
[    0.508451] system 00:07: ioport range 0x2b00-0x2bfe has been reserved
[    0.508454] system 00:07: ioport range 0x2c00-0x2cfe has been reserved
[    0.508457] system 00:07: ioport range 0x2d00-0x2dfe has been reserved
[    0.508461] system 00:07: ioport range 0x2e00-0x2efe has been reserved
[    0.508464] system 00:07: ioport range 0x2f00-0x2ffe has been reserved
[    0.508467] system 00:07: ioport range 0x5000-0x50fe has been reserved
[    0.508470] system 00:07: ioport range 0x5100-0x51fe has been reserved
[    0.508474] system 00:07: ioport range 0x5200-0x52fe has been reserved
[    0.508477] system 00:07: ioport range 0x5300-0x53fe has been reserved
[    0.508480] system 00:07: ioport range 0x5400-0x54fe has been reserved
[    0.508484] system 00:07: ioport range 0x5500-0x55fe has been reserved
[    0.508489] system 00:07: ioport range 0x5600-0x56fe has been reserved
[    0.508493] system 00:07: ioport range 0x5700-0x57fe has been reserved
[    0.508496] system 00:07: ioport range 0x5800-0x58fe has been reserved
[    0.508500] system 00:07: ioport range 0x5900-0x59fe has been reserved
[    0.508503] system 00:07: ioport range 0x5a00-0x5afe has been reserved
[    0.508506] system 00:07: ioport range 0x5b00-0x5bfe has been reserved
[    0.508510] system 00:07: ioport range 0x5c00-0x5cfe has been reserved
[    0.508513] system 00:07: ioport range 0x5d00-0x5dfe has been reserved
[    0.508516] system 00:07: ioport range 0x5e00-0x5efe has been reserved
[    0.508520] system 00:07: ioport range 0x5f00-0x5ffe has been reserved
[    0.508523] system 00:07: ioport range 0x6000-0x60fe has been reserved
[    0.508527] system 00:07: ioport range 0x6100-0x61fe has been reserved
[    0.508530] system 00:07: ioport range 0x6200-0x62fe has been reserved
[    0.508533] system 00:07: ioport range 0x6300-0x63fe has been reserved
[    0.508537] system 00:07: ioport range 0x6400-0x64fe has been reserved
[    0.508540] system 00:07: ioport range 0x6500-0x65fe has been reserved
[    0.508544] system 00:07: ioport range 0x6600-0x66fe has been reserved
[    0.508547] system 00:07: ioport range 0x6700-0x67fe has been reserved
[    0.508553] system 00:07: ioport range 0x6800-0x68fe has been reserved
[    0.508557] system 00:07: ioport range 0x6900-0x69fe has been reserved
[    0.508560] system 00:07: ioport range 0x6a00-0x6afe has been reserved
[    0.508564] system 00:07: ioport range 0x6b00-0x6bfe has been reserved
[    0.508567] system 00:07: ioport range 0x6c00-0x6cfe has been reserved
[    0.508571] system 00:07: ioport range 0x6d00-0x6dfe has been reserved
[    0.508574] system 00:07: ioport range 0x6e00-0x6efe has been reserved
[    0.508578] system 00:07: ioport range 0x6f00-0x6ffe has been reserved
[    0.508581] system 00:07: ioport range 0xa000-0xa0fe has been reserved
[    0.508585] system 00:07: ioport range 0xa100-0xa1fe has been reserved
[    0.508588] system 00:07: ioport range 0xa200-0xa2fe has been reserved
[    0.508592] system 00:07: ioport range 0xa300-0xa3fe has been reserved
[    0.508595] system 00:07: ioport range 0xa400-0xa4fe has been reserved
[    0.508599] system 00:07: ioport range 0xa500-0xa5fe has been reserved
[    0.508602] system 00:07: ioport range 0xa600-0xa6fe has been reserved
[    0.508606] system 00:07: ioport range 0xa700-0xa7fe has been reserved
[    0.508610] system 00:07: ioport range 0xa800-0xa8fe has been reserved
[    0.508613] system 00:07: ioport range 0xa900-0xa9fe has been reserved
[    0.508617] system 00:07: ioport range 0xaa00-0xaafe has been reserved
[    0.508621] system 00:07: ioport range 0xab00-0xabfe has been reserved
[    0.508624] system 00:07: ioport range 0xac00-0xacfe has been reserved
[    0.508628] system 00:07: ioport range 0xad00-0xadfe has been reserved
[    0.508632] system 00:07: ioport range 0xae00-0xaefe has been reserved
[    0.508636] system 00:07: ioport range 0xaf00-0xaffe has been reserved
[    0.508640] system 00:07: iomem range 0xe0000000-0xefffffff has been reserved
[    0.508643] system 00:07: iomem range 0xfeda0000-0xfedacfff has been reserved
[    0.543424] pci 0000:00:01.0: PCI bridge, secondary bus 0000:01
[    0.543428] pci 0000:00:01.0:   IO window: 0xd000-0xdfff
[    0.543433] pci 0000:00:01.0:   MEM window: 0xdfd00000-0xdfefffff
[    0.543437] pci 0000:00:01.0:   PREFETCH window: 0xd0000000-0xd7ffffff
[    0.543443] pci 0000:00:1c.0: PCI bridge, secondary bus 0000:02
[    0.543446] pci 0000:00:1c.0:   IO window: 0x1000-0x1fff
[    0.543452] pci 0000:00:1c.0:   MEM window: 0xdfc00000-0xdfcfffff
[    0.543456] pci 0000:00:1c.0:   PREFETCH window: 0x000000c0000000-0x000000c01fffff
[    0.543463] pci 0000:00:1c.1: PCI bridge, secondary bus 0000:03
[    0.543465] pci 0000:00:1c.1:   IO window: disabled
[    0.543470] pci 0000:00:1c.1:   MEM window: 0xdfb00000-0xdfbfffff
[    0.543475] pci 0000:00:1c.1:   PREFETCH window: disabled
[    0.543481] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:04
[    0.543483] pci 0000:00:1e.0:   IO window: disabled
[    0.543488] pci 0000:00:1e.0:   MEM window: disabled
[    0.543492] pci 0000:00:1e.0:   PREFETCH window: disabled
[    0.543507]   alloc irq_desc for 16 on node -1
[    0.543509]   alloc kstat_irqs on node -1
[    0.543516] pci 0000:00:01.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.543521] pci 0000:00:01.0: setting latency timer to 64
[    0.543531] pci 0000:00:1c.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.543536] pci 0000:00:1c.0: setting latency timer to 64
[    0.543544]   alloc irq_desc for 17 on node -1
[    0.543546]   alloc kstat_irqs on node -1
[    0.543551] pci 0000:00:1c.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    0.543555] pci 0000:00:1c.1: setting latency timer to 64
[    0.543563] pci 0000:00:1e.0: setting latency timer to 64
[    0.543568] pci_bus 0000:00: resource 0 io:  [0x00-0xffff]
[    0.543571] pci_bus 0000:00: resource 1 mem: [0x000000-0xffffffff]
[    0.543574] pci_bus 0000:01: resource 0 io:  [0xd000-0xdfff]
[    0.543577] pci_bus 0000:01: resource 1 mem: [0xdfd00000-0xdfefffff]
[    0.543580] pci_bus 0000:01: resource 2 pref mem [0xd0000000-0xd7ffffff]
[    0.543584] pci_bus 0000:02: resource 0 io:  [0x1000-0x1fff]
[    0.543586] pci_bus 0000:02: resource 1 mem: [0xdfc00000-0xdfcfffff]
[    0.543589] pci_bus 0000:02: resource 2 pref mem [0xc0000000-0xc01fffff]
[    0.543593] pci_bus 0000:03: resource 1 mem: [0xdfb00000-0xdfbfffff]
[    0.543596] pci_bus 0000:04: resource 3 io:  [0x00-0xffff]
[    0.543599] pci_bus 0000:04: resource 4 mem: [0x000000-0xffffffff]
[    0.543642] NET: Registered protocol family 2
[    0.543757] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.544141] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.544641] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.544945] TCP: Hash tables configured (established 131072 bind 65536)
[    0.544948] TCP reno registered
[    0.545084] NET: Registered protocol family 1
[    0.545203] pci 0000:01:00.0: Boot video device
[    0.545309] Simple Boot Flag value 0x87 read from CMOS RAM was invalid
[    0.545312] Simple Boot Flag at 0x7a set to 0x1
[    0.545446] cpufreq-nforce2: No nForce2 chipset.
[    0.545488] Scanning for low memory corruption every 60 seconds
[    0.545618] audit: initializing netlink socket (disabled)
[    0.545631] type=2000 audit(1286458743.543:1): initialized
[    0.554602] Trying to unpack rootfs image as initramfs...
[    0.564498] highmem bounce pool size: 64 pages
[    0.564507] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    0.569707] VFS: Disk quotas dquot_6.5.2
[    0.569778] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.570470] fuse init (API version 7.13)
[    0.570577] msgmni has been set to 1662
[    0.576094] alg: No test for stdrng (krng)
[    0.576182] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.576187] io scheduler noop registered
[    0.576189] io scheduler anticipatory registered
[    0.576191] io scheduler deadline registered
[    0.576241] io scheduler cfq registered (default)
[    0.576397]   alloc irq_desc for 24 on node -1
[    0.576400]   alloc kstat_irqs on node -1
[    0.576411] pcieport 0000:00:01.0: irq 24 for MSI/MSI-X
[    0.576418] pcieport 0000:00:01.0: setting latency timer to 64
[    0.576535]   alloc irq_desc for 25 on node -1
[    0.576538]   alloc kstat_irqs on node -1
[    0.576546] pcieport 0000:00:1c.0: irq 25 for MSI/MSI-X
[    0.576555] pcieport 0000:00:1c.0: setting latency timer to 64
[    0.576685]   alloc irq_desc for 26 on node -1
[    0.576687]   alloc kstat_irqs on node -1
[    0.576696] pcieport 0000:00:1c.1: irq 26 for MSI/MSI-X
[    0.576704] pcieport 0000:00:1c.1: setting latency timer to 64
[    0.576795] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.576869] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.576976] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0
[    0.576986] ACPI: Power Button [VBTN]
[    0.577046] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
[    0.577050] ACPI: Power Button [PWRF]
[    0.577482] processor LNXCPU:00: registered as cooling_device0
[    0.638016] isapnp: Scanning for PnP cards...
[    0.643843] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    0.645431] brd: module loaded
[    0.646025] loop: module loaded
[    0.646136] input: Macintosh mouse button emulation as /devices/virtual/input/input2
[    0.646251] ata_piix 0000:00:1f.1: version 2.13
[    0.646268] ata_piix 0000:00:1f.1: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.646316] ata_piix 0000:00:1f.1: setting latency timer to 64
[    0.648101] scsi0 : ata_piix
[    0.695426] scsi1 : ata_piix
[    0.695478] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xffa0 irq 14
[    0.695482] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xffa8 irq 15
[    0.695533]   alloc irq_desc for 20 on node -1
[    0.695536]   alloc kstat_irqs on node -1
[    0.695544] ata_piix 0000:00:1f.2: PCI INT C -> GSI 20 (level, low) -> IRQ 20
[    0.695550] ata_piix 0000:00:1f.2: MAP [ P0 P2 P1 P3 ]
[    0.695760] ata2: port disabled. ignoring.
[    0.867560] ata_piix 0000:00:1f.2: setting latency timer to 64
[    0.868100] ata1.00: ATAPI: Lite-On LTN486S 48x Max, YDS8, max UDMA/33
[    0.872172] scsi2 : ata_piix
[    0.872282] scsi3 : ata_piix
[    0.872324] ata3: SATA max UDMA/133 cmd 0xfe00 ctl 0xfe10 bmdma 0xfea0 irq 20
[    0.872328] ata4: SATA max UDMA/133 cmd 0xfe20 ctl 0xfe30 bmdma 0xfea8 irq 20
[    0.872777] Fixed MDIO Bus: probed
[    0.872824] PPP generic driver version 2.4.2
[    0.872895] tun: Universal TUN/TAP device driver, 1.6
[    0.872898] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.873012] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.873037]   alloc irq_desc for 21 on node -1
[    0.873040]   alloc kstat_irqs on node -1
[    0.873048] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[    0.873065] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    0.873069] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    0.873115] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 1
[    0.873145] ehci_hcd 0000:00:1d.7: debug port 1
[    0.877029] ehci_hcd 0000:00:1d.7: cache line size of 128 is not supported
[    0.877420] ata1.00: configured for UDMA/33
[    0.880139] ehci_hcd 0000:00:1d.7: irq 21, io mem 0xffa80800
[    0.899953] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    0.900096] usb usb1: configuration #1 chosen from 1 choice
[    0.900134] hub 1-0:1.0: USB hub found
[    0.900147] hub 1-0:1.0: 8 ports detected
[    0.900229] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.900250] uhci_hcd: USB Universal Host Controller Interface driver
[    0.900296] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[    0.900309] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    0.900313] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    0.900362] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    0.900391] uhci_hcd 0000:00:1d.0: irq 21, io base 0x0000ff80
[    0.900495] usb usb2: configuration #1 chosen from 1 choice
[    0.900529] hub 2-0:1.0: USB hub found
[    0.900539] hub 2-0:1.0: 2 ports detected
[    0.900589]   alloc irq_desc for 22 on node -1
[    0.900593]   alloc kstat_irqs on node -1
[    0.900600] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 22 (level, low) -> IRQ 22
[    0.900607] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    0.900610] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    0.900650] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3
[    0.900684] uhci_hcd 0000:00:1d.1: irq 22, io base 0x0000ff60
[    0.900784] usb usb3: configuration #1 chosen from 1 choice
[    0.900817] hub 3-0:1.0: USB hub found
[    0.900826] hub 3-0:1.0: 2 ports detected
[    0.900875]   alloc irq_desc for 18 on node -1
[    0.900878]   alloc kstat_irqs on node -1
[    0.900883] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.900890] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    0.900894] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    0.900934] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4
[    0.900965] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000ff40
[    0.901072] usb usb4: configuration #1 chosen from 1 choice
[    0.901105] hub 4-0:1.0: USB hub found
[    0.901116] hub 4-0:1.0: 2 ports detected
[    0.901166]   alloc irq_desc for 23 on node -1
[    0.901168]   alloc kstat_irqs on node -1
[    0.901174] uhci_hcd 0000:00:1d.3: PCI INT D -> GSI 23 (level, low) -> IRQ 23
[    0.901183] uhci_hcd 0000:00:1d.3: setting latency timer to 64
[    0.901186] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[    0.901228] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 5
[    0.901262] uhci_hcd 0000:00:1d.3: irq 23, io base 0x0000ff20
[    0.901368] usb usb5: configuration #1 chosen from 1 choice
[    0.901401] hub 5-0:1.0: USB hub found
[    0.901411] hub 5-0:1.0: 2 ports detected
[    0.901526] PNP: No PS/2 controller found. Probing ports directly.
[    0.909064] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.909075] serio: i8042 AUX port at 0x60,0x64 irq 12
[    0.909259] mice: PS/2 mouse device common for all mice
[    0.909422] rtc_cmos 00:05: RTC can wake from S4
[    0.909473] rtc_cmos 00:05: rtc core: registered rtc_cmos as rtc0
[    0.909501] rtc0: alarms up to one day, 242 bytes nvram, hpet irqs
[    0.909640] device-mapper: uevent: version 1.0.3
[    0.909768] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: [email]dm-devel@redhat.com[/email]
[    0.911996] device-mapper: multipath: version 1.1.0 loaded
[    0.912000] device-mapper: multipath round-robin: version 1.0.0 loaded
[    0.912166] EISA: Probing bus 0 at eisa.0
[    0.912171] EISA: Cannot allocate resource for mainboard
[    0.912174] Cannot allocate resource for EISA slot 1
[    0.912177] Cannot allocate resource for EISA slot 2
[    0.912186] Cannot allocate resource for EISA slot 5
[    0.912189] Cannot allocate resource for EISA slot 6
[    0.912198] EISA: Detected 0 cards.
[    0.916241] cpuidle: using governor ladder
[    0.916244] cpuidle: using governor menu
[    0.916776] TCP cubic registered
[    0.916928] NET: Registered protocol family 10
[    0.917451] lo: Disabled Privacy Extensions
[    0.917818] NET: Registered protocol family 17
[    0.917876] Using IPI No-Shortcut mode
[    0.917989] PM: Resume from disk failed.
[    0.918004] registered taskstats version 1
[    0.918302]   Magic number: 14:61:685
[    0.918377] rtc_cmos 00:05: setting system clock to 2010-10-07 13:39:04 UTC (1286458744)
[    0.918382] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.918384] EDD information not available.
[    1.096020] Freeing initrd memory: 8550k freed
[    1.144486] ata3.00: ATA-7: ST3160811AS, 3.AAE, max UDMA/133
[    1.144491] ata3.00: 312581808 sectors, multi 8: LBA48 NCQ (depth 0/32)
[    1.231756] isapnp: No Plug & Play device found
[    1.232406] scsi 0:0:0:0: CD-ROM            Lite-On  LTN486S 48x Max  YDS8 PQ: 0 ANSI: 5
[    1.235543] sr0: scsi3-mmc drive: 48x/48x cd/rw xa/form2 cdda tray
[    1.235547] Uniform CD-ROM driver Revision: 3.20
[    1.235687] sr 0:0:0:0: Attached scsi CD-ROM sr0
[    1.235768] sr 0:0:0:0: Attached scsi generic sg0 type 5
[    1.260547] ata3.00: configured for UDMA/133
[    1.260653] scsi 2:0:0:0: Direct-Access     ATA      ST3160811AS      3.AA PQ: 0 ANSI: 5
[    1.260796] sd 2:0:0:0: Attached scsi generic sg1 type 0
[    1.260888] sd 2:0:0:0: [sda] 312581808 512-byte logical blocks: (160 GB/149 GiB)
[    1.260957] sd 2:0:0:0: [sda] Write Protect is off
[    1.260961] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.260997] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.261171]  sda: sda1 sda2 < sda5 > sda3 sda4
[    1.337764] sd 2:0:0:0: [sda] Attached SCSI disk
[    1.484012] usb 3-1: new low speed USB device using uhci_hcd and address 2
[    1.658670] usb 3-1: configuration #1 chosen from 1 choice
[    1.916011] usb 3-2: new low speed USB device using uhci_hcd and address 3
[    2.092586] usb 3-2: configuration #1 chosen from 1 choice
[    2.728067] Freeing unused kernel memory: 656k freed
[    2.728492] Write protecting the kernel text: 4684k
[    2.728525] Write protecting the kernel read-only data: 1840k
[    2.752529] udev: starting version 151
[    2.987882] tg3.c:v3.102 (September 1, 2009)
[    2.987902] tg3 0000:02:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    2.987913] tg3 0000:02:00.0: setting latency timer to 64
[    2.999955] usbcore: registered new interface driver hiddev
[    3.005391] eth0: Tigon3 [partno(BCM95751) rev 4001] (PCI Express) MAC address 00:11:43:20:5e:26
[    3.005396] eth0: attached PHY is 5750 (10/100/1000Base-T Ethernet) (WireSpeed[1])
[    3.005399] eth0: RXcsums[1] LinkChgREG[0] MIirq[0] ASF[0] TSOcap[1]
[    3.005402] eth0: dma_rwctrl[76180000] dma_mask[64-bit]
[    3.019949] input: Dell Dell USB Keyboard as /devices/pci0000:00/0000:00:1d.1/usb3/3-1/3-1:1.0/input/input3
[    3.020172] generic-usb 0003:413C:2003.0001: input,hidraw0: USB HID v1.10 Keyboard [Dell Dell USB Keyboard] on usb-0000:00:1d.1-1/input0
[    3.032649] input: Microsoft Basic Optical Mouse as /devices/pci0000:00/0000:00:1d.1/usb3/3-2/3-2:1.0/input/input4
[    3.032884] generic-usb 0003:045E:0083.0002: input,hidraw1: USB HID v1.10 Mouse [Microsoft Basic Optical Mouse] on usb-0000:00:1d.1-2/input0
[    3.032916] usbcore: registered new interface driver usbhid
[    3.033046] usbhid: v2.6:USB HID core driver
[    3.297208] EXT3-fs: INFO: recovery required on readonly filesystem.
[    3.297213] EXT3-fs: write access will be enabled during recovery.
[   10.339295] kjournald starting.  Commit interval 5 seconds
[   10.339318] EXT3-fs: sda4: orphan cleanup on readonly fs
[   10.339326] ext3_orphan_cleanup: deleting unreferenced inode 2689216
[   10.339366] ext3_orphan_cleanup: deleting unreferenced inode 2689217
[   10.339382] ext3_orphan_cleanup: deleting unreferenced inode 2689218
[   10.339397] ext3_orphan_cleanup: deleting unreferenced inode 1913511
[   10.339416] ext3_orphan_cleanup: deleting unreferenced inode 1913510
[   10.360478] ext3_orphan_cleanup: deleting unreferenced inode 1913071
[   10.360493] ext3_orphan_cleanup: deleting unreferenced inode 1912974
[   10.360507] ext3_orphan_cleanup: deleting unreferenced inode 1912971
[   10.360519] ext3_orphan_cleanup: deleting unreferenced inode 1912970
[   10.363874] ext3_orphan_cleanup: deleting unreferenced inode 1912968
[   10.370168] ext3_orphan_cleanup: deleting unreferenced inode 1912967
[   10.378906] ext3_orphan_cleanup: deleting unreferenced inode 1912966
[   10.387814] ext3_orphan_cleanup: deleting unreferenced inode 1912965
[   10.391892] ext3_orphan_cleanup: deleting unreferenced inode 1912963
[   10.427760] ext3_orphan_cleanup: deleting unreferenced inode 1912961
[   10.434127] ext3_orphan_cleanup: deleting unreferenced inode 1912960
[   10.440642] ext3_orphan_cleanup: deleting unreferenced inode 1912959
[   10.450271] ext3_orphan_cleanup: deleting unreferenced inode 1912958
[   10.453207] ext3_orphan_cleanup: deleting unreferenced inode 1912872
[   10.458957] ext3_orphan_cleanup: deleting unreferenced inode 1912871
[   10.465196] ext3_orphan_cleanup: deleting unreferenced inode 1912869
[   10.465208] ext3_orphan_cleanup: deleting unreferenced inode 1912865
[   10.468434] ext3_orphan_cleanup: deleting unreferenced inode 1912862
[   10.471734] ext3_orphan_cleanup: deleting unreferenced inode 1912858
[   10.471748] ext3_orphan_cleanup: deleting unreferenced inode 1912857
[   10.482545] ext3_orphan_cleanup: deleting unreferenced inode 1912854
[   10.482559] ext3_orphan_cleanup: deleting unreferenced inode 1912851
[   10.484817] ext3_orphan_cleanup: deleting unreferenced inode 1912850
[   10.484828] ext3_orphan_cleanup: deleting unreferenced inode 1912849
[   10.484839] ext3_orphan_cleanup: deleting unreferenced inode 1912846
[   10.494142] ext3_orphan_cleanup: deleting unreferenced inode 1912843
[   10.505873] ext3_orphan_cleanup: deleting unreferenced inode 1912842
[   10.514732] ext3_orphan_cleanup: deleting unreferenced inode 1912841
[   10.520551] ext3_orphan_cleanup: deleting unreferenced inode 1912840
[   10.523205] ext3_orphan_cleanup: deleting unreferenced inode 1912839
[   10.530024] ext3_orphan_cleanup: deleting unreferenced inode 1912838
[   10.535487] ext3_orphan_cleanup: deleting unreferenced inode 1912835
[   10.540389] ext3_orphan_cleanup: deleting unreferenced inode 1912834
[   10.540404] ext3_orphan_cleanup: deleting unreferenced inode 2083188
[   10.540430] ext3_orphan_cleanup: deleting unreferenced inode 712610
[   10.540458] ext3_orphan_cleanup: deleting unreferenced inode 2009957
[   10.540480] ext3_orphan_cleanup: deleting unreferenced inode 698864
[   10.556291] ext3_orphan_cleanup: deleting unreferenced inode 699061
[   10.556307] ext3_orphan_cleanup: deleting unreferenced inode 4189680
[   10.568707] ext3_orphan_cleanup: deleting unreferenced inode 1745835
[   10.568729] ext3_orphan_cleanup: deleting unreferenced inode 1133059
[   10.592014] ext3_orphan_cleanup: deleting unreferenced inode 1133729
[   10.595800] ext3_orphan_cleanup: deleting unreferenced inode 4189689
[   10.595814] ext3_orphan_cleanup: deleting unreferenced inode 1132857
[   10.604642] ext3_orphan_cleanup: deleting unreferenced inode 1131341
[   10.604661] ext3_orphan_cleanup: deleting unreferenced inode 1744975
[   10.604682] ext3_orphan_cleanup: deleting unreferenced inode 2401762
[   10.619960] ext3_orphan_cleanup: deleting unreferenced inode 698826
[   10.700291] ext3_orphan_cleanup: deleting unreferenced inode 4189643
[   10.737700] ext3_orphan_cleanup: deleting unreferenced inode 1747234
[   10.751743] ext3_orphan_cleanup: deleting unreferenced inode 698953
[   10.760770] ext3_orphan_cleanup: deleting unreferenced inode 698832
[   10.760782] ext3_orphan_cleanup: deleting unreferenced inode 698968
[   10.774090] ext3_orphan_cleanup: deleting unreferenced inode 698940
[   10.783983] ext3_orphan_cleanup: deleting unreferenced inode 698698
[   10.820359] ext3_orphan_cleanup: deleting unreferenced inode 4205362
[   10.860957] EXT3-fs: sda4: 61 orphan inodes deleted
[   10.860960] EXT3-fs: recovery complete.
[   11.241163] EXT3-fs: mounted filesystem with ordered data mode.
[   15.010008] Adding 4200988k swap on /dev/sda3.  Priority:-1 extents:1 across:4200988k 
[   16.089243] EXT3 FS on sda4, internal journal
[   16.192397] udev: starting version 151
[   17.725685] dcdbas dcdbas: Dell Systems Management Base Driver (version 5.6.0-3.2)
[   17.769267] dell-wmi: No known WMI GUID found
[   18.469267] type=1505 audit(1286458762.049:2):  operation="profile_load" pid=474 name="/sbin/dhclient3"
[   18.469955] type=1505 audit(1286458762.049:3):  operation="profile_load" pid=474 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[   18.470330] type=1505 audit(1286458762.049:4):  operation="profile_load" pid=474 name="/usr/lib/connman/scripts/dhclient-script"
[   18.769365] lp: driver loaded but no devices found
[   20.618621] Linux agpgart interface v0.103
[   20.697473] [drm] Initialized drm 1.1.0 20060810
[   21.077920] intel_rng: Firmware space is locked read-only. If you can't or
[   21.077923] intel_rng: don't want to disable this in firmware setup, and if
[   21.077924] intel_rng: you are certain that your system has a functional
[   21.077926] intel_rng: RNG, try using the 'no_fwh_detect' option.
[   21.551200] [drm] radeon defaulting to kernel modesetting.
[   21.551205] [drm] radeon kernel modesetting enabled.
[   21.551255] radeon 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   21.551262] radeon 0000:01:00.0: setting latency timer to 64
[   21.553354] [drm] radeon: Initializing kernel modesetting.
[   21.553434] [drm] register mmio base: 0xDFDE0000
[   21.553437] [drm] register mmio size: 65536
[   21.553690] [drm] GPU reset succeed (RBBM_STATUS=0x00000140)
[   21.553710] [drm] Generation 2 PCI interface, using max accessible memory
[   21.553714] [drm] radeon: VRAM 128M
[   21.553717] [drm] radeon: VRAM from 0x00000000 to 0x07FFFFFF
[   21.553719] [drm] radeon: GTT 512M
[   21.553721] [drm] radeon: GTT from 0x20000000 to 0x3FFFFFFF
[   21.553758]   alloc irq_desc for 27 on node -1
[   21.553761]   alloc kstat_irqs on node -1
[   21.553774] radeon 0000:01:00.0: irq 27 for MSI/MSI-X
[   21.553780] [drm] radeon: using MSI.
[   21.553804] [drm] radeon: irq initialized.
[   21.554015] [drm] Detected VRAM RAM=128M, BAR=128M
[   21.554020] [drm] RAM width 64bits DDR
[   21.554111] [TTM] Zone  kernel: Available graphics memory: 430218 kiB.
[   21.554114] [TTM] Zone highmem: Available graphics memory: 1547674 kiB.
[   21.554132] [drm] radeon: 128M of VRAM memory ready
[   21.554135] [drm] radeon: 512M of GTT memory ready.
[   21.554152] [drm] GART: num cpu pages 131072, num gpu pages 131072
[   21.554866] [drm] radeon: 1 quad pipes, 1 Z pipes initialized.
[   21.554903] [drm] PCIE GART of 512M enabled (table at 0x00040000).
[   21.554914] [drm] radeon: cp idle (0x10000C03)
[   21.554966] [drm] Loading R300 Microcode
[   21.555374] platform radeon_cp.0: firmware: requesting radeon/R300_cp.bin
[   22.278069] [drm] radeon: ring at 0x0000000020000000
[   22.278090] [drm] ring test succeeded in 1 usecs
[   22.278244] [drm] radeon: ib pool ready.
[   22.278320] [drm] ib test succeeded in 0 usecs
[   22.278350] [drm] DFP table revision: 4
[   22.278436] [drm] External TMDS Table revision: 2
[   22.278519] [drm] Radeon Display Connectors
[   22.278522] [drm] Connector 0:
[   22.278524] [drm]   DVI-I
[   22.278526] [drm]   HPD1
[   22.278529] [drm]   DDC: 0x64 0x64 0x64 0x64 0x64 0x64 0x64 0x64
[   22.278530] [drm]   Encoders:
[   22.278532] [drm]     CRT2: INTERNAL_DAC2
[   22.278534] [drm]     DFP1: INTERNAL_TMDS1
[   22.278536] [drm] Connector 1:
[   22.278538] [drm]   DVI-I
[   22.278539] [drm]   HPD2
[   22.278542] [drm]   DDC: 0x60 0x60 0x60 0x60 0x60 0x60 0x60 0x60
[   22.278543] [drm]   Encoders:
[   22.278545] [drm]     CRT1: INTERNAL_DAC1
[   22.278547] [drm]     DFP2: INTERNAL_DVO1
[   22.517906] [drm] fb mappable at 0xD00C0000
[   22.517910] [drm] vram apper at 0xD0000000
[   22.517912] [drm] size 5242880
[   22.517914] [drm] fb depth is 24
[   22.517916] [drm]    pitch is 5120
[   22.518151] fb0: radeondrmfb frame buffer device
[   22.518154] registered panic notifier
[   22.518161] [drm] Initialized radeon 2.0.0 20080528 for 0000:01:00.0 on minor 0
[   22.581797] vga16fb: initializing
[   22.581802] vga16fb: mapped to 0xc00a0000
[   22.581808] vga16fb: not registering due to another framebuffer present
[   23.182102] Console: switching to colour frame buffer device 160x64
[   23.871844] Intel ICH 0000:00:1e.2: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[   23.871881] Intel ICH 0000:00:1e.2: setting latency timer to 64
[   24.292016] intel8x0_measure_ac97_clock: measured 53925 usecs (2599 samples)
[   24.292020] intel8x0: clocking to 48000
[   30.109515] kjournald starting.  Commit interval 5 seconds
[   30.109526] EXT3-fs warning: checktime reached, running e2fsck is recommended
[   30.109737] EXT3 FS on dm-0, internal journal
[   30.109743] EXT3-fs: mounted filesystem with ordered data mode.
[   30.437795] kjournald starting.  Commit interval 5 seconds
[   30.437805] EXT3-fs warning: checktime reached, running e2fsck is recommended
[   30.438017] EXT3 FS on dm-1, internal journal
[   30.438022] EXT3-fs: mounted filesystem with ordered data mode.
[   30.561450] kjournald starting.  Commit interval 5 seconds
[   30.561461] EXT3-fs warning: checktime reached, running e2fsck is recommended
[   30.561661] EXT3 FS on dm-2, internal journal
[   30.561667] EXT3-fs: mounted filesystem with ordered data mode.
[   30.712446] kjournald starting.  Commit interval 5 seconds
[   30.712456] EXT3-fs warning: checktime reached, running e2fsck is recommended
[   30.712640] EXT3 FS on dm-3, internal journal
[   30.712646] EXT3-fs: mounted filesystem with ordered data mode.
[   30.765685] kjournald starting.  Commit interval 5 seconds
[   30.765695] EXT3-fs warning: checktime reached, running e2fsck is recommended
[   30.765901] EXT3 FS on dm-4, internal journal
[   30.765907] EXT3-fs: mounted filesystem with ordered data mode.
[   30.904449] kjournald starting.  Commit interval 5 seconds
[   30.904459] EXT3-fs warning: checktime reached, running e2fsck is recommended
[   30.904654] EXT3 FS on dm-5, internal journal
[   30.904660] EXT3-fs: mounted filesystem with ordered data mode.
[   31.269772] kjournald starting.  Commit interval 5 seconds
[   31.269782] EXT3-fs warning: checktime reached, running e2fsck is recommended
[   31.269975] EXT3 FS on dm-6, internal journal
[   31.269980] EXT3-fs: mounted filesystem with ordered data mode.
[   35.320247] type=1505 audit(1286458778.901:5):  operation="profile_load" pid=792 name="/usr/share/gdm/guest-session/Xsession"
[   35.325741] type=1505 audit(1286458778.905:6):  operation="profile_replace" pid=795 name="/sbin/dhclient3"
[   35.326445] type=1505 audit(1286458778.905:7):  operation="profile_replace" pid=795 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[   35.326829] type=1505 audit(1286458778.905:8):  operation="profile_replace" pid=795 name="/usr/lib/connman/scripts/dhclient-script"
[   35.432969] type=1505 audit(1286458779.013:9):  operation="profile_load" pid=796 name="/usr/bin/evince"
[   35.454024] type=1505 audit(1286458779.033:10):  operation="profile_load" pid=796 name="/usr/bin/evince-previewer"
[   35.469489] type=1505 audit(1286458779.049:11):  operation="profile_load" pid=796 name="/usr/bin/evince-thumbnailer"
[   35.530256] type=1505 audit(1286458779.109:12):  operation="profile_load" pid=798 name="/usr/bin/freshclam"
[   35.649855] type=1505 audit(1286458779.229:13):  operation="profile_load" pid=799 name="/usr/lib/cups/backend/cups-pdf"
[   35.650667] type=1505 audit(1286458779.229:14):  operation="profile_load" pid=799 name="/usr/sbin/cupsd"
[   37.298258] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[   37.298263] apm: overridden by ACPI.
[   41.488566] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   43.097089] tg3: eth0: Link is up at 100 Mbps, full duplex.
[   43.097093] tg3: eth0: Flow control is on for TX and on for RX.
[   43.097233] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   47.881448] RPC: Registered udp transport module.
[   47.881452] RPC: Registered tcp transport module.
[   47.881454] RPC: Registered tcp NFSv4.1 backchannel transport module.
[   54.020006] eth0: no IPv6 routers present
[   57.503738] CPU0 attaching NULL sched-domain.
[   57.503801] CPU0 attaching NULL sched-domain.
[   58.387329] svc: failed to register lockdv1 RPC service (errno 97).
[   83.549414] vboxdrv: Trying to deactivate the NMI watchdog permanently...
[   83.549420] vboxdrv: Successfully done.
[   83.549422] vboxdrv: Found 1 processor cores.
[   83.552391] vboxdrv: TSC mode is 'synchronous', kernel timer mode is 'normal'.
[   83.552395] vboxdrv: Successfully loaded version 3.2.8 (interface 0x00140001).
[   85.402217] ppdev: user-space parallel port driver


I hope these details help and please let me know if you need anything further.

---

### Post by P4man on 2010-10-08
I dont see anything wrong in there (other then some filesystem issues probably caused by a unclean shutdown. And you seem to be using ext3 instead of the default ext4 but of course that has nothing to do with the mouse problem)

Check the mouse on a different machine first. If that works okay we can experiment some more. Try unplugging and plugging it back in, then check dmesg again. Try different USB ports.

---

### Post by blofse on 2010-10-08
Okay thanks for the advice.

With ubuntu 10.10 on the way I might reinstall anyway, which may fix the issue.

I will try as soon as I can on another machine - however not for a few hours yet.

Thanks again.

---

