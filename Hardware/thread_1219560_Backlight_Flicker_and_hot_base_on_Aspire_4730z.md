---
title: "Backlight Flicker and hot base on Aspire 4730z"
date: 2009-07-21
forum: Hardware
---

### Post by doyleman on 2009-07-21
I went and installed 9.04, and for the most part everything clicked with out a problem. I can honestly probably live with my few problems, but i'm curious if i cant get them all washed away.

The main problems i have that i just cant get fixed, even after reading similar threads in the forum, were my backglight flickering. Certain programs drop the brightness to 0, and then i have to try to tinker with it again through the brightness applet/fn + arrow keys. It basically doesnt stick (8.04 and 8.10 had it working, but i had bigger problems on those).

And lastly, my system idles at around 46 celsius. I'm not too worried about that, but instead more about the base of my laptop, right around where the battery/hdd go/are.

After leaving the laptop alone for a couple hours, its pretty hot--much more hot than any other part of the laptop (and the base).

I use the scaling and have it set to powersave, but it didnt do anything for the heat, just reduced my cpu temp from around 50 to 46.

any pointers on what i can do?

---

### Post by doyleman on 2009-07-23
Bump

Ok, so I got 8.10 again, and did some other tweaks; this way the backlight is up and working, but the base of the laptop is still rediculously hot compared to then, say, Windows XP.

Anyone have any suggestions?

---

### Post by doyleman on 2009-07-24
bump.

here's the output of my dmesg if it helps any.
```
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.27-14-generic (buildd@rothera) (gcc version 4.3.2 (Ubuntu 4.3.2-1ubuntu11) ) #1 SMP Tue Jun 30 19:57:39 UTC 2009 (Ubuntu 2.6.27-14.35-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000007b974000 (usable)
[    0.000000]  BIOS-e820: 000000007b974000 - 000000007b9bf000 (reserved)
[    0.000000]  BIOS-e820: 000000007b9bf000 - 000000007ba83000 (usable)
[    0.000000]  BIOS-e820: 000000007ba83000 - 000000007babf000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000007babf000 - 000000007baec000 (usable)
[    0.000000]  BIOS-e820: 000000007baec000 - 000000007baff000 (ACPI data)
[    0.000000]  BIOS-e820: 000000007baff000 - 000000007bb00000 (usable)
[    0.000000]  BIOS-e820: 000000007bb00000 - 0000000080000000 (reserved)
[    0.000000]  BIOS-e820: 00000000f8000000 - 00000000fc000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed10000 - 00000000fed14000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed18000 - 00000000fed1a000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed1c000 - 00000000fed20000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fff00000 - 0000000100000000 (reserved)
[    0.000000] DMI 2.4 present.
[    0.000000] last_pfn = 0x7bb00 max_arch_pfn = 0x100000
[    0.000000] kernel direct mapping tables up to 38000000 @ 7000-c000
[    0.000000] RAMDISK: 3781c000 - 37fef992
[    0.000000] ACPI: RSDP 000FE020, 0024 (r2 ACRSYS)
[    0.000000] ACPI: XSDT 7BAFE120, 0064 (r1 ACRSYS ACRPRDCT        1       1000013)
[    0.000000] ACPI: FACP 7BAFD000, 00F4 (r4 ACRSYS ACRPRDCT        1 1025  1000013)
[    0.000000] ACPI: DSDT 7BAEE000, 92F2 (r1 ACRSYS ACRPRDCT        1 1025  1000013)
[    0.000000] ACPI: FACS 7BA8F000, 0040
[    0.000000] ACPI: HPET 7BAFC000, 0038 (r1 ACRSYS ACRPRDCT        1 1025  1000013)
[    0.000000] ACPI: APIC 7BAFB000, 006C (r2 ACRSYS ACRPRDCT        1 1025  1000013)
[    0.000000] ACPI: MCFG 7BAFA000, 003C (r1 ACRSYS ACRPRDCT        1 1025  1000013)
[    0.000000] ACPI: ASF! 7BAF9000, 00A5 (r32 ACRSYS ACRPRDCT        1 1025  1000013)
[    0.000000] ACPI: SLIC 7BAF8000, 0176 (r1 ACRSYS ACRPRDCT        1 1025  1000013)
[    0.000000] ACPI: BOOT 7BAED000, 0028 (r1 ACRSYS ACRPRDCT        1 1025  1000013)
[    0.000000] ACPI: SSDT 7BAEC000, 0655 (r1  PmRef    CpuPm     3000 INTL 20051117)
[    0.000000] ACPI: DMI detected: Acer
[    0.000000] 1083MB HIGHMEM available.
[    0.000000] 896MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 38000000
[    0.000000]   low ram: 00000000 - 38000000
[    0.000000]   bootmap 00008000 - 0000f000
[    0.000000] (9 early reservations) ==> bootmem [0000000000 - 0038000000]
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000]   #1 [0000001000 - 0000002000]    EX TRAMPOLINE ==> [0000001000 - 0000002000]
[    0.000000]   #2 [0000006000 - 0000007000]       TRAMPOLINE ==> [0000006000 - 0000007000]
[    0.000000]   #3 [0000100000 - 00005c39e0]    TEXT DATA BSS ==> [0000100000 - 00005c39e0]
[    0.000000]   #4 [003781c000 - 0037fef992]          RAMDISK ==> [003781c000 - 0037fef992]
[    0.000000]   #5 [00005c4000 - 00005c7000]    INIT_PG_TABLE ==> [00005c4000 - 00005c7000]
[    0.000000]   #6 [000009fc00 - 0000100000]    BIOS reserved ==> [000009fc00 - 0000100000]
[    0.000000]   #7 [0000007000 - 0000008000]          PGTABLE ==> [0000007000 - 0000008000]
[    0.000000]   #8 [0000008000 - 000000f000]          BOOTMAP ==> [0000008000 - 000000f000]
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000000 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x00038000
[    0.000000]   HighMem  0x00038000 -> 0x0007bb00
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[5] active PFN ranges
[    0.000000]     0: 0x00000000 -> 0x0000009f
[    0.000000]     0: 0x00000100 -> 0x0007b974
[    0.000000]     0: 0x0007b9bf -> 0x0007ba83
[    0.000000]     0: 0x0007babf -> 0x0007baec
[    0.000000]     0: 0x0007baff -> 0x0007bb00
[    0.000000] On node 0 totalpages: 506373
[    0.000000] free_area_init_node: node 0, pgdat c048c700, node_mem_map c1000000
[    0.000000]   DMA zone: 3963 pages, LIFO batch:0
[    0.000000]   Normal zone: 223300 pages, LIFO batch:31
[    0.000000]   HighMem zone: 274657 pages, LIFO batch:31
[    0.000000] ACPI: PM-Timer IO Port: 0x408
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x00] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x00] disabled)
[    0.000000] ACPI: IOAPIC (id[0x04] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 4, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] SMP: Allowing 4 CPUs, 2 hotplug CPUs
[    0.000000] mapped APIC to ffffb000 (fee00000)
[    0.000000] mapped IOAPIC to ffffa000 (fec00000)
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
[    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 88000000 (gap: 80000000:78000000)
[    0.000000] PERCPU: Allocating 41628 bytes of per cpu data
[    0.000000] NR_CPUS: 64, nr_cpu_ids: 4, nr_node_ids 1
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 501920
[    0.000000] Kernel command line: root=UUID=89cf4995-bf7f-4225-aa00-a1ecccd1e7f0 ro quiet splash 
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] TSC: PIT calibration confirmed by PMTIMER.
[    0.000000] TSC: using PIT calibration value
[    0.000000] Detected 1994.970 MHz processor.
[    0.004000] Console: colour VGA+ 80x25
[    0.004000] console [tty0] enabled
[    0.004000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.004000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.004000] Memory: 1992744k/2026496k available (2579k kernel code, 31764k reserved, 1162k data, 428k init, 1108376k highmem)
[    0.004000] virtual kernel memory layout:
[    0.004000]     fixmap  : 0xffc77000 - 0xfffff000   (3616 kB)
[    0.004000]     pkmap   : 0xff400000 - 0xff800000   (4096 kB)
[    0.004000]     vmalloc : 0xf8800000 - 0xff3fe000   ( 107 MB)
[    0.004000]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
[    0.004000]       .init : 0xc04ad000 - 0xc0518000   ( 428 kB)
[    0.004000]       .data : 0xc0384caa - 0xc04a7680   (1162 kB)
[    0.004000]       .text : 0xc0100000 - 0xc0384caa   (2579 kB)
[    0.004000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.004000] CPA: page pool initialized 1 of 1 pages preallocated
[    0.004000] SLUB: Genslabs=12, HWalign=64, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
[    0.004000] hpet clockevent registered
[    0.004000] Calibrating delay loop (skipped), value calculated using timer frequency.. 3989.94 BogoMIPS (lpj=7979880)
[    0.004000] Security Framework initialized
[    0.004000] SELinux:  Disabled at boot.
[    0.004000] AppArmor: AppArmor initialized
[    0.004000] Mount-cache hash table entries: 512
[    0.004000] Initializing cgroup subsys ns
[    0.004000] Initializing cgroup subsys cpuacct
[    0.004000] Initializing cgroup subsys memory
[    0.004000] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.004000] CPU: L2 cache: 1024K
[    0.004000] CPU: Physical Processor ID: 0
[    0.004000] CPU: Processor Core ID: 0
[    0.004000] using mwait in idle threads.
[    0.004000] Checking 'hlt' instruction... OK.
[    0.018107] ACPI: Core revision 20080609
[    0.021446] ACPI: Checking initramfs for custom DSDT
[    0.376232] ENABLING IO-APIC IRQs
[    0.376419] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.417400] CPU0: Intel(R) Pentium(R) Dual  CPU  T3200  @ 2.00GHz stepping 0d
[    0.420026] Booting processor 1/1 ip 6000
[    0.004000] Initializing CPU#1
[    0.004000] Calibrating delay using timer specific routine.. 3990.00 BogoMIPS (lpj=7980016)
[    0.004000] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.004000] CPU: L2 cache: 1024K
[    0.004000] CPU: Physical Processor ID: 0
[    0.004000] CPU: Processor Core ID: 1
[    0.504418] CPU1: Intel(R) Pentium(R) Dual  CPU  T3200  @ 2.00GHz stepping 0d
[    0.504437] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
[    0.508053] Brought up 2 CPUs
[    0.508057] Total of 2 processors activated (7979.94 BogoMIPS).
[    0.508080] CPU0 attaching sched-domain:
[    0.508083]  domain 0: span 0-1 level MC
[    0.508086]   groups: 0 1
[    0.508092] CPU1 attaching sched-domain:
[    0.508094]  domain 0: span 0-1 level MC
[    0.508097]   groups: 1 0
[    0.508191] net_namespace: 840 bytes
[    0.508191] Booting paravirtualized kernel on bare hardware
[    0.508308] Time: 11:39:12  Date: 07/24/09
[    0.508339] NET: Registered protocol family 16
[    0.508361] EISA bus registered
[    0.508361] ACPI: bus type pci registered
[    0.508361] PCI: MCFG configuration 0: base f8000000 segment 0 buses 0 - 63
[    0.508361] PCI: MCFG area at f8000000 reserved in E820
[    0.508361] PCI: Using MMCONFIG for extended config space
[    0.508361] PCI: Using configuration type 1 for base access
[    0.512390] ACPI: EC: Look up EC in DSDT
[    0.618000] ACPI: BIOS _OSI(Linux) query ignored via DMI
[    0.618513] ACPI: Interpreter enabled
[    0.618518] ACPI: (supports S0 S3 S4 S5)
[    0.618530] ACPI: Using IOAPIC for interrupt routing
[    0.620609] ACPI: EC: non-query interrupt received, switching to interrupt mode
[    0.870467] ACPI: EC: GPE = 0x1c, I/O: command/status = 0x66, data = 0x62
[    0.870467] ACPI: EC: driver started in interrupt mode
[    0.870467] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.870467] PCI: 0000:00:02.0 reg 10 64bit mmio: [90000000, 903fffff]
[    0.870467] PCI: 0000:00:02.0 reg 18 64bit mmio: [80000000, 8fffffff]
[    0.870467] PCI: 0000:00:02.0 reg 20 io port: [6140, 6147]
[    0.870467] PCI: 0000:00:02.1 reg 10 64bit mmio: [94500000, 945fffff]
[    0.870467] PCI: 0000:00:1a.0 reg 20 io port: [60c0, 60df]
[    0.870467] PCI: 0000:00:1a.1 reg 20 io port: [60a0, 60bf]
[    0.870467] PCI: 0000:00:1a.7 reg 10 32bit mmio: [98805400, 988057ff]
[    0.870467] pci 0000:00:1a.7: PME# supported from D0 D3hot D3cold
[    0.870467] pci 0000:00:1a.7: PME# disabled
[    0.870467] PCI: 0000:00:1b.0 reg 10 64bit mmio: [98800000, 98803fff]
[    0.870467] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    0.870467] pci 0000:00:1b.0: PME# disabled
[    0.870467] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.870467] pci 0000:00:1c.0: PME# disabled
[    0.872034] pci 0000:00:1c.1: PME# supported from D0 D3hot D3cold
[    0.872039] pci 0000:00:1c.1: PME# disabled
[    0.872113] pci 0000:00:1c.2: PME# supported from D0 D3hot D3cold
[    0.872118] pci 0000:00:1c.2: PME# disabled
[    0.872195] pci 0000:00:1c.4: PME# supported from D0 D3hot D3cold
[    0.872200] pci 0000:00:1c.4: PME# disabled
[    0.872262] PCI: 0000:00:1d.0 reg 20 io port: [6080, 609f]
[    0.872360] PCI: 0000:00:1d.1 reg 20 io port: [6060, 607f]
[    0.872457] PCI: 0000:00:1d.2 reg 20 io port: [6040, 605f]
[    0.872555] PCI: 0000:00:1d.3 reg 20 io port: [6020, 603f]
[    0.872648] PCI: 0000:00:1d.7 reg 10 32bit mmio: [98805000, 988053ff]
[    0.872728] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
[    0.872733] pci 0000:00:1d.7: PME# disabled
[    0.872924] PCI: 0000:00:1f.2 reg 10 io port: [6138, 613f]
[    0.872931] PCI: 0000:00:1f.2 reg 14 io port: [6154, 6157]
[    0.872938] PCI: 0000:00:1f.2 reg 18 io port: [6130, 6137]
[    0.872945] PCI: 0000:00:1f.2 reg 1c io port: [6150, 6153]
[    0.872952] PCI: 0000:00:1f.2 reg 20 io port: [6110, 611f]
[    0.872959] PCI: 0000:00:1f.2 reg 24 io port: [6100, 610f]
[    0.873017] PCI: 0000:00:1f.3 reg 10 64bit mmio: [98805800, 988058ff]
[    0.873034] PCI: 0000:00:1f.3 reg 20 io port: [6000, 601f]
[    0.873088] PCI: 0000:00:1f.5 reg 10 io port: [6128, 612f]
[    0.873095] PCI: 0000:00:1f.5 reg 14 io port: [614c, 614f]
[    0.873102] PCI: 0000:00:1f.5 reg 18 io port: [6120, 6127]
[    0.873109] PCI: 0000:00:1f.5 reg 1c io port: [6148, 614b]
[    0.873116] PCI: 0000:00:1f.5 reg 20 io port: [60f0, 60ff]
[    0.873123] PCI: 0000:00:1f.5 reg 24 io port: [60e0, 60ef]
[    0.873199] PCI: 0000:00:1f.6 reg 10 64bit mmio: [98804000, 98804fff]
[    0.873310] PCI: bridge 0000:00:1c.0 io port: [5000, 5fff]
[    0.873314] PCI: bridge 0000:00:1c.0 32bit mmio: [97800000, 987fffff]
[    0.873322] PCI: bridge 0000:00:1c.0 64bit mmio pref: [90400000, 913fffff]
[    0.873383] PCI: 0000:04:00.0 reg 10 64bit mmio: [96700000, 9670ffff]
[    0.873481] pci 0000:04:00.0: supports D1
[    0.873483] pci 0000:04:00.0: PME# supported from D0 D1 D3hot
[    0.873488] pci 0000:04:00.0: PME# disabled
[    0.873530] PCI: bridge 0000:00:1c.1 io port: [4000, 4fff]
[    0.873535] PCI: bridge 0000:00:1c.1 32bit mmio: [96700000, 977fffff]
[    0.873542] PCI: bridge 0000:00:1c.1 64bit mmio pref: [91400000, 923fffff]
[    0.873595] PCI: 0000:05:00.0 reg 10 io port: [2000, 20ff]
[    0.873619] PCI: 0000:05:00.0 reg 18 64bit mmio: [92410000, 92410fff]
[    0.873635] PCI: 0000:05:00.0 reg 20 64bit mmio: [92400000, 9240ffff]
[    0.873645] PCI: 0000:05:00.0 reg 30 32bit mmio: [ffff0000, ffffffff]
[    0.873711] pci 0000:05:00.0: supports D1
[    0.873712] pci 0000:05:00.0: supports D2
[    0.873714] pci 0000:05:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.873720] pci 0000:05:00.0: PME# disabled
[    0.873762] PCI: bridge 0000:00:1c.2 io port: [2000, 3fff]
[    0.873767] PCI: bridge 0000:00:1c.2 32bit mmio: [95700000, 966fffff]
[    0.873774] PCI: bridge 0000:00:1c.2 64bit mmio pref: [92400000, 934fffff]
[    0.873825] PCI: 0000:07:00.0 reg 10 32bit mmio: [94600300, 946003ff]
[    0.873877] PCI: 0000:07:00.0 reg 30 32bit mmio: [ffff8000, ffffffff]
[    0.873979] PCI: 0000:07:00.2 reg 10 32bit mmio: [94600200, 946002ff]
[    0.874129] PCI: 0000:07:00.3 reg 10 32bit mmio: [94600100, 946001ff]
[    0.874280] PCI: 0000:07:00.4 reg 10 32bit mmio: [94600000, 946000ff]
[    0.874431] PCI: bridge 0000:00:1c.4 io port: [1000, 1fff]
[    0.874436] PCI: bridge 0000:00:1c.4 32bit mmio: [94600000, 956fffff]
[    0.874443] PCI: bridge 0000:00:1c.4 64bit mmio pref: [93500000, 944fffff]
[    0.874500] pci 0000:00:1e.0: transparent bridge
[    0.874538] bus 00 -> node 0
[    0.874550] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.875238] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.EXP1._PRT]
[    0.875464] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.EXP2._PRT]
[    0.875687] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.EXP3._PRT]
[    0.875913] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.EXP5._PRT]
[    0.888653] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 7 9 10 *11 12)
[    0.888653] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 7 9 10 *11 12)
[    0.888653] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 7 9 10 *11 12)
[    0.888766] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 7 9 10 *11 12)
[    0.892130] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 7 9 10 11 12) *0, disabled.
[    0.892326] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 7 9 *10 11 12)
[    0.892520] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 7 9 10 *11 12)
[    0.892716] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 7 9 10 *11 12)
[    0.892849] Linux Plug and Play Support v0.97 (c) Adam Belay
[    0.892849] pnp: PnP ACPI init
[    0.892849] ACPI: bus type pnp registered
[    1.004802] pnp 00:01: io resource (0x164e-0x164f) overlaps 0000:00:1c.4 BAR 7 (0x1000-0x1fff), disabling
[    1.004887] pnp: PnP ACPI: found 9 devices
[    1.004887] ACPI: ACPI bus type pnp unregistered
[    1.004887] PnPBIOS: Disabled by ACPI PNP
[    1.004887] PCI: Using ACPI for IRQ routing
[    1.012041] NET: Registered protocol family 8
[    1.012044] NET: Registered protocol family 20
[    1.012060] NetLabel: Initializing
[    1.012060] NetLabel:  domain hash size = 128
[    1.012060] NetLabel:  protocols = UNLABELED CIPSOv4
[    1.012066] NetLabel:  unlabeled traffic allowed by default
[    1.012074] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0
[    1.012079] hpet0: 4 64-bit timers, 14318180 Hz
[    1.014093] tracer: 772 pages allocated for 65536 entries of 48 bytes
[    1.014096]    actual entries 65620
[    1.014218] AppArmor: AppArmor Filesystem Enabled
[    1.014242] ACPI: RTC can wake from S4
[    1.016040] Switched to high resolution mode on CPU 0
[    1.016455] Switched to high resolution mode on CPU 1
[    1.020025] system 00:01: ioport range 0x600-0x60f has been reserved
[    1.020028] system 00:01: ioport range 0x610-0x610 has been reserved
[    1.020031] system 00:01: ioport range 0x800-0x80f has been reserved
[    1.020035] system 00:01: ioport range 0x810-0x817 has been reserved
[    1.020037] system 00:01: ioport range 0x820-0x823 has been reserved
[    1.020040] system 00:01: ioport range 0x400-0x47f has been reserved
[    1.020043] system 00:01: ioport range 0x500-0x57f has been reserved
[    1.020047] system 00:01: ioport range 0xff2c-0xff2f has been reserved
[    1.020052] system 00:01: iomem range 0xf8000000-0xfbffffff could not be reserved
[    1.020056] system 00:01: iomem range 0xfed1c000-0xfed1ffff could not be reserved
[    1.020059] system 00:01: iomem range 0xfed10000-0xfed13fff could not be reserved
[    1.020062] system 00:01: iomem range 0xfed18000-0xfed18fff could not be reserved
[    1.020065] system 00:01: iomem range 0xfed19000-0xfed19fff could not be reserved
[    1.020069] system 00:01: iomem range 0xfec00000-0xfec00fff could not be reserved
[    1.020072] system 00:01: iomem range 0xfed20000-0xfed8ffff has been reserved
[    1.020075] system 00:01: iomem range 0xfee00000-0xfee00fff could not be reserved
[    1.055196] pci 0000:00:1c.0: PCI bridge, secondary bus 0000:02
[    1.055200] pci 0000:00:1c.0:   IO window: 0x5000-0x5fff
[    1.055206] pci 0000:00:1c.0:   MEM window: 0x97800000-0x987fffff
[    1.055212] pci 0000:00:1c.0:   PREFETCH window: 0x00000090400000-0x000000913fffff
[    1.055220] pci 0000:00:1c.1: PCI bridge, secondary bus 0000:04
[    1.055224] pci 0000:00:1c.1:   IO window: 0x4000-0x4fff
[    1.055230] pci 0000:00:1c.1:   MEM window: 0x96700000-0x977fffff
[    1.055235] pci 0000:00:1c.1:   PREFETCH window: 0x00000091400000-0x000000923fffff
[    1.055244] pci 0000:00:1c.2: PCI bridge, secondary bus 0000:05
[    1.055248] pci 0000:00:1c.2:   IO window: 0x2000-0x3fff
[    1.055254] pci 0000:00:1c.2:   MEM window: 0x95700000-0x966fffff
[    1.055258] pci 0000:00:1c.2:   PREFETCH window: 0x00000092400000-0x000000934fffff
[    1.055266] pci 0000:00:1c.4: PCI bridge, secondary bus 0000:07
[    1.055270] pci 0000:00:1c.4:   IO window: 0x1000-0x1fff
[    1.055275] pci 0000:00:1c.4:   MEM window: 0x94600000-0x956fffff
[    1.055280] pci 0000:00:1c.4:   PREFETCH window: 0x00000093500000-0x000000944fffff
[    1.055287] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:08
[    1.055289] pci 0000:00:1e.0:   IO window: disabled
[    1.055295] pci 0000:00:1e.0:   MEM window: disabled
[    1.055299] pci 0000:00:1e.0:   PREFETCH window: disabled
[    1.055313] pci 0000:00:1c.0: enabling device (0001 -> 0003)
[    1.055323] pci 0000:00:1c.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    1.055330] pci 0000:00:1c.0: setting latency timer to 64
[    1.055340] pci 0000:00:1c.1: PCI INT B -> GSI 16 (level, low) -> IRQ 16
[    1.055344] pci 0000:00:1c.1: setting latency timer to 64
[    1.055354] pci 0000:00:1c.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    1.055358] pci 0000:00:1c.2: setting latency timer to 64
[    1.055367] pci 0000:00:1c.4: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    1.055371] pci 0000:00:1c.4: setting latency timer to 64
[    1.055379] pci 0000:00:1e.0: setting latency timer to 64
[    1.055383] bus: 00 index 0 io port: [0, ffff]
[    1.055385] bus: 00 index 1 mmio: [0, ffffffff]
[    1.055387] bus: 02 index 0 io port: [5000, 5fff]
[    1.055390] bus: 02 index 1 mmio: [97800000, 987fffff]
[    1.055392] bus: 02 index 2 mmio: [90400000, 913fffff]
[    1.055394] bus: 02 index 3 mmio: [0, 0]
[    1.055396] bus: 04 index 0 io port: [4000, 4fff]
[    1.055398] bus: 04 index 1 mmio: [96700000, 977fffff]
[    1.055400] bus: 04 index 2 mmio: [91400000, 923fffff]
[    1.055402] bus: 04 index 3 mmio: [0, 0]
[    1.055404] bus: 05 index 0 io port: [2000, 3fff]
[    1.055406] bus: 05 index 1 mmio: [95700000, 966fffff]
[    1.055408] bus: 05 index 2 mmio: [92400000, 934fffff]
[    1.055410] bus: 05 index 3 mmio: [0, 0]
[    1.055412] bus: 07 index 0 io port: [1000, 1fff]
[    1.055414] bus: 07 index 1 mmio: [94600000, 956fffff]
[    1.055416] bus: 07 index 2 mmio: [93500000, 944fffff]
[    1.055418] bus: 07 index 3 mmio: [0, 0]
[    1.055420] bus: 08 index 0 mmio: [0, 0]
[    1.055422] bus: 08 index 1 mmio: [0, 0]
[    1.055423] bus: 08 index 2 mmio: [0, 0]
[    1.055425] bus: 08 index 3 io port: [0, ffff]
[    1.055427] bus: 08 index 4 mmio: [0, ffffffff]
[    1.055439] NET: Registered protocol family 2
[    1.068059] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    1.068325] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    1.068924] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    1.069281] TCP: Hash tables configured (established 131072 bind 65536)
[    1.069285] TCP reno registered
[    1.076130] NET: Registered protocol family 1
[    1.076263] checking if image is initramfs... it is
[    1.793639] Freeing initrd memory: 8014k freed
[    1.793819] Simple Boot Flag value 0x5 read from CMOS RAM was invalid
[    1.793822] Simple Boot Flag at 0x44 set to 0x1
[    1.794762] audit: initializing netlink socket (disabled)
[    1.794787] type=2000 audit(1248435552.792:1): initialized
[    1.800346] highmem bounce pool size: 64 pages
[    1.800354] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    1.802651] VFS: Disk quotas dquot_6.5.1
[    1.802740] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    1.802845] msgmni has been set to 1744
[    1.802967] io scheduler noop registered
[    1.802970] io scheduler anticipatory registered
[    1.802973] io scheduler deadline registered
[    1.802986] io scheduler cfq registered (default)
[    1.803002] pci 0000:00:02.0: Boot video device
[    1.832162] pcieport-driver 0000:00:1c.0: setting latency timer to 64
[    1.832209] pcieport-driver 0000:00:1c.0: found MSI capability
[    1.832256] pci_express 0000:00:1c.0:pcie00: allocate port service
[    1.832296] pci_express 0000:00:1c.0:pcie02: allocate port service
[    1.832337] pci_express 0000:00:1c.0:pcie03: allocate port service
[    1.832442] pcieport-driver 0000:00:1c.1: setting latency timer to 64
[    1.832487] pcieport-driver 0000:00:1c.1: found MSI capability
[    1.832536] pci_express 0000:00:1c.1:pcie00: allocate port service
[    1.832574] pci_express 0000:00:1c.1:pcie02: allocate port service
[    1.832611] pci_express 0000:00:1c.1:pcie03: allocate port service
[    1.832716] pcieport-driver 0000:00:1c.2: setting latency timer to 64
[    1.832762] pcieport-driver 0000:00:1c.2: found MSI capability
[    1.832806] pci_express 0000:00:1c.2:pcie00: allocate port service
[    1.832844] pci_express 0000:00:1c.2:pcie02: allocate port service
[    1.832881] pci_express 0000:00:1c.2:pcie03: allocate port service
[    1.832986] pcieport-driver 0000:00:1c.4: setting latency timer to 64
[    1.833032] pcieport-driver 0000:00:1c.4: found MSI capability
[    1.833077] pci_express 0000:00:1c.4:pcie00: allocate port service
[    1.833115] pci_express 0000:00:1c.4:pcie02: allocate port service
[    1.833152] pci_express 0000:00:1c.4:pcie03: allocate port service
[    1.833494] isapnp: Scanning for PnP cards...
[    2.186985] isapnp: No Plug & Play device found
[    2.219419] hpet_resources: 0xfed00000 is busy
[    2.219537] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
[    2.221671] brd: module loaded
[    2.221737] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[    2.221853] PNP: PS/2 Controller [PNP0303:KBC0,PNP0f13:MSE0] at 0x60,0x64 irq 1,12
[    2.282477] serio: i8042 KBD port at 0x60,0x64 irq 1
[    2.282483] serio: i8042 AUX port at 0x60,0x64 irq 12
[    2.282742] mice: PS/2 mouse device common for all mice
[    2.285046] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0
[    2.285075] rtc0: alarms up to one month, hpet irqs
[    2.285198] EISA: Probing bus 0 at eisa.0
[    2.285205] Cannot allocate resource for EISA slot 1
[    2.285207] Cannot allocate resource for EISA slot 2
[    2.285209] Cannot allocate resource for EISA slot 3
[    2.285211] Cannot allocate resource for EISA slot 4
[    2.285213] Cannot allocate resource for EISA slot 5
[    2.285216] Cannot allocate resource for EISA slot 6
[    2.285227] EISA: Detected 0 cards.
[    2.285230] cpuidle: using governor ladder
[    2.285233] cpuidle: using governor menu
[    2.285764] TCP cubic registered
[    2.285794] Using IPI No-Shortcut mode
[    2.285966] registered taskstats version 1
[    2.286150]   Magic number: 1:109:682
[    2.286314] rtc_cmos 00:03: setting system clock to 2009-07-24 11:39:14 UTC (1248435554)
[    2.286318] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    2.286320] EDD information not available.
[    2.286603] Freeing unused kernel memory: 428k freed
[    2.286642] Write protecting the kernel text: 2580k
[    2.286670] Write protecting the kernel read-only data: 940k
[    2.331300] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[    2.472562] fuse init (API version 7.9)
[    2.537316] ACPI: SSDT 7B97DC18, 0265 (r1  PmRef  Cpu0Ist     3000 INTL 20051117)
[    2.537942] ACPI: SSDT 7B97B598, 0537 (r1  PmRef  Cpu0Cst     3001 INTL 20051117)
[    2.693298] Monitor-Mwait will be used to enter C-1 state
[    2.693302] Monitor-Mwait will be used to enter C-2 state
[    2.693462] ACPI: CPU0 (power states: C1[C1] C2[C2])
[    2.693525] processor ACPI0007:00: registered as cooling_device0
[    2.693530] ACPI: Processor [CPU0] (supports 8 throttling states)
[    2.694137] ACPI: SSDT 7B97CE18, 01CF (r1  PmRef    ApIst     3000 INTL 20051117)
[    2.694812] ACPI: SSDT 7B97DF18, 008D (r1  PmRef    ApCst     3000 INTL 20051117)
[    2.695861] ACPI: CPU1 (power states: C1[C1] C2[C2])
[    2.695906] processor ACPI0007:01: registered as cooling_device1
[    2.695911] ACPI: Processor [CPU1] (supports 8 throttling states)
[    2.696513] Marking TSC unstable due to TSC halts in idle
[    2.722728] thermal LNXTHERM:01: registered as thermal_zone0
[    2.772760] ACPI: Thermal Zone [TZ01] (37 C)
[    3.000018] Clocksource tsc unstable (delta = -69003585 ns)
[    3.063735] usbcore: registered new interface driver usbfs
[    3.063760] usbcore: registered new interface driver hub
[    3.064098] usbcore: registered new device driver usb
[    3.067401] USB Universal Host Controller Interface driver v3.0
[    3.067457] uhci_hcd 0000:00:1a.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    3.067469] uhci_hcd 0000:00:1a.0: setting latency timer to 64
[    3.067473] uhci_hcd 0000:00:1a.0: UHCI Host Controller
[    3.067518] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 1
[    3.067555] uhci_hcd 0000:00:1a.0: irq 20, io base 0x000060c0
[    3.067711] usb usb1: configuration #1 chosen from 1 choice
[    3.067744] hub 1-0:1.0: USB hub found
[    3.067751] hub 1-0:1.0: 2 ports detected
[    3.081335] Warning! ehci_hcd should always be loaded before uhci_hcd and ohci_hcd, not after
[    3.167022] No dock devices found.
[    3.181482] SCSI subsystem initialized
[    3.197822] libata version 3.00 loaded.
[    3.276314] uhci_hcd 0000:00:1a.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[    3.276327] uhci_hcd 0000:00:1a.1: setting latency timer to 64
[    3.276331] uhci_hcd 0000:00:1a.1: UHCI Host Controller
[    3.276368] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 2
[    3.276408] uhci_hcd 0000:00:1a.1: irq 21, io base 0x000060a0
[    3.276519] usb usb2: configuration #1 chosen from 1 choice
[    3.276549] hub 2-0:1.0: USB hub found
[    3.276557] hub 2-0:1.0: 2 ports detected
[    3.380351] ehci_hcd 0000:00:1a.7: PCI INT D -> GSI 21 (level, low) -> IRQ 21
[    3.380371] ehci_hcd 0000:00:1a.7: setting latency timer to 64
[    3.380375] ehci_hcd 0000:00:1a.7: EHCI Host Controller
[    3.380410] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 3
[    3.384335] ehci_hcd 0000:00:1a.7: debug port 1
[    3.384344] ehci_hcd 0000:00:1a.7: cache line size of 32 is not supported
[    3.384354] ehci_hcd 0000:00:1a.7: irq 21, io mem 0x98805400
[    3.388243] usb 1-1: new full speed USB device using uhci_hcd and address 2
[    3.400030] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    3.400204] usb usb3: configuration #1 chosen from 1 choice
[    3.400241] hub 3-0:1.0: USB hub found
[    3.400252] hub 3-0:1.0: 4 ports detected
[    3.456078] hub 1-0:1.0: unable to enumerate USB device on port 1
[    3.608325] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    3.608337] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    3.608341] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    3.608370] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 4
[    3.608409] uhci_hcd 0000:00:1d.0: irq 23, io base 0x00006080
[    3.608525] usb usb4: configuration #1 chosen from 1 choice
[    3.608554] hub 4-0:1.0: USB hub found
[    3.608563] hub 4-0:1.0: 2 ports detected
[    3.712271] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    3.712280] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    3.712284] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    3.712310] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 5
[    3.712344] uhci_hcd 0000:00:1d.1: irq 19, io base 0x00006060
[    3.712445] usb usb5: configuration #1 chosen from 1 choice
[    3.712473] hub 5-0:1.0: USB hub found
[    3.712481] hub 5-0:1.0: 2 ports detected
[    3.720056] usb 3-1: new high speed USB device using ehci_hcd and address 2
[    3.816268] uhci_hcd 0000:00:1d.2: PCI INT D -> GSI 20 (level, low) -> IRQ 20
[    3.816277] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    3.816281] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    3.816310] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 6
[    3.816338] uhci_hcd 0000:00:1d.2: irq 20, io base 0x00006040
[    3.816432] usb usb6: configuration #1 chosen from 1 choice
[    3.816460] hub 6-0:1.0: USB hub found
[    3.816467] hub 6-0:1.0: 2 ports detected
[    3.920265] uhci_hcd 0000:00:1d.3: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    3.920274] uhci_hcd 0000:00:1d.3: setting latency timer to 64
[    3.920278] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[    3.920304] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 7
[    3.920340] uhci_hcd 0000:00:1d.3: irq 18, io base 0x00006020
[    3.920436] usb usb7: configuration #1 chosen from 1 choice
[    3.920465] hub 7-0:1.0: USB hub found
[    3.920471] hub 7-0:1.0: 2 ports detected
[    4.024340] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    4.024358] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    4.024362] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    4.024390] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 8
[    4.028295] ehci_hcd 0000:00:1d.7: debug port 1
[    4.028302] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
[    4.028310] ehci_hcd 0000:00:1d.7: irq 23, io mem 0x98805000
[    4.044014] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    4.044110] usb usb8: configuration #1 chosen from 1 choice
[    4.044143] hub 8-0:1.0: USB hub found
[    4.044150] hub 8-0:1.0: 8 ports detected
[    4.142897] usb 3-1: configuration #1 chosen from 1 choice
[    4.149888] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    4.149909] r8169 0000:05:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    4.149932] r8169 0000:05:00.0: setting latency timer to 64
[    4.150317] eth0: RTL8168c/8111c at 0xf8846000, 00:1e:ec:c3:a1:d1, XID 3c4000c0 IRQ 219
[    4.156247] pata_acpi 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    4.156287] pata_acpi 0000:00:1f.2: setting latency timer to 64
[    4.156304] pata_acpi 0000:00:1f.2: PCI INT B disabled
[    4.156325] pata_acpi 0000:00:1f.5: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    4.156343] pata_acpi 0000:00:1f.5: setting latency timer to 64
[    4.156354] pata_acpi 0000:00:1f.5: PCI INT B disabled
[    4.175215] ata_piix 0000:00:1f.2: version 2.12
[    4.175236] ata_piix 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    4.175242] ata_piix 0000:00:1f.2: MAP [ P0 -- P1 -- ]
[    4.175306] ata_piix 0000:00:1f.2: setting latency timer to 64
[    4.176712] scsi0 : ata_piix
[    4.176823] scsi1 : ata_piix
[    4.178294] ata1: SATA max UDMA/133 cmd 0x6138 ctl 0x6154 bmdma 0x6110 irq 19
[    4.178300] ata2: SATA max UDMA/133 cmd 0x6130 ctl 0x6150 bmdma 0x6118 irq 19
[    4.656112] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    4.709447] ata1.00: ATA-8: WDC WD1200BEVS-22UST0, 01.01A01, max UDMA/133
[    4.709450] ata1.00: 234441648 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    4.725469] ata1.00: configured for UDMA/133
[    5.200099] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    5.208761] ata2.00: ATAPI: HL-DT-ST DVDRAM GSA-T50N, RP05, max UDMA/133
[    5.224301] ata2.00: configured for UDMA/133
[    5.224409] scsi 0:0:0:0: Direct-Access     ATA      WDC WD1200BEVS-2 01.0 PQ: 0 ANSI: 5
[    5.230251] scsi 1:0:0:0: CD-ROM            HL-DT-ST DVDRAM GSA-T50N  RP05 PQ: 0 ANSI: 5
[    5.230339] ata_piix 0000:00:1f.5: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    5.230344] ata_piix 0000:00:1f.5: MAP [ P0 -- P1 -- ]
[    5.384081] ata_piix 0000:00:1f.5: setting latency timer to 64
[    5.384194] scsi2 : ata_piix
[    5.384508] scsi3 : ata_piix
[    5.385848] ata3: SATA max UDMA/133 cmd 0x6128 ctl 0x614c bmdma 0x60f0 irq 19
[    5.385853] ata4: SATA max UDMA/133 cmd 0x6120 ctl 0x6148 bmdma 0x60f8 irq 19
[    5.715032] ata3: SATA link down (SStatus 0 SControl 300)
[    6.043038] ata4: SATA link down (SStatus 0 SControl 300)
[    6.050945] scsi 0:0:0:0: Attached scsi generic sg0 type 0
[    6.050987] scsi 1:0:0:0: Attached scsi generic sg1 type 5
[    6.064800] Driver 'sd' needs updating - please use bus_type methods
[    6.064907] sd 0:0:0:0: [sda] 234441648 512-byte hardware sectors (120034 MB)
[    6.064923] sd 0:0:0:0: [sda] Write Protect is off
[    6.064926] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    6.064950] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    6.065013] sd 0:0:0:0: [sda] 234441648 512-byte hardware sectors (120034 MB)
[    6.065027] sd 0:0:0:0: [sda] Write Protect is off
[    6.065030] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    6.065054] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    6.065057]  sda:<4>Driver 'sr' needs updating - please use bus_type methods
[    6.107096]  sda1 sda2 < sda5 sda6 sda7 >
[    6.156037] sd 0:0:0:0: [sda] Attached SCSI disk
[    6.380388] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[    6.380393] Uniform CD-ROM driver Revision: 3.20
[    6.380511] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    6.878078] PM: Starting manual resume from disk
[    6.878082] PM: Resume from partition 8:7
[    6.878084] PM: Checking hibernation image.
[    6.878280] PM: Resume from disk failed.
[    6.947142] kjournald starting.  Commit interval 5 seconds
[    6.947160] EXT3-fs: mounted filesystem with ordered data mode.
[   12.707514] udevd version 124 started
[   13.021387] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   13.057505] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   13.067302] Linux agpgart interface v0.103
[   13.073830] agpgart-intel 0000:00:00.0: Intel Mobile Intel® GM45 Express Chipset
[   13.074172] agpgart-intel 0000:00:00.0: detected 65532K stolen memory
[   13.078443] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0x80000000
[   13.196804] input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input2
[   13.220046] ACPI: Power Button (FF) [PWRF]
[   13.220195] input: Power Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:0e/PNP0C0C:00/input/input3
[   13.256028] ACPI: Power Button (CM) [PWRB]
[   13.256159] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:0e/PNP0C0D:00/input/input4
[   13.256308] ACPI: Lid Switch [LID0]
[   13.256379] input: Sleep Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:0e/PNP0C0E:00/input/input5
[   13.288021] ACPI: Sleep Button (CM) [SLPB]
[   13.340494] ACPI: WMI: Mapper loaded
[   13.404682] ACPI: AC Adapter [AC] (on-line)
[   13.741522] acpi device:0a: registered as cooling_device2
[   13.741961] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:07/input/input6
[   13.760544] ACPI: Video Device [OVGA] (multi-head: yes  rom: no  post: no)
[   13.920535] sdhci: Secure Digital Host Controller Interface driver
[   13.920538] sdhci: Copyright(c) Pierre Ossman
[   13.937833] Linux video capture interface: v2.00
[   14.029012] uvcvideo: Found UVC 1.00 device Acer Crystal Eye webcam (5986:0105)
[   14.032610] input: Acer Crystal Eye webcam as /devices/pci0000:00/0000:00:1a.7/usb3/3-1/3-1:1.0/input/input7
[   14.032654] usbcore: registered new interface driver uvcvideo
[   14.032670] USB Video Class driver (v0.1.0)
[   14.094483] sdhci-pci 0000:07:00.0: SDHCI controller found [197b:2382] (rev 0)
[   14.094508] sdhci-pci 0000:07:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   14.094548] sdhci-pci 0000:07:00.0: setting latency timer to 64
[   14.094616] mmc0: SDHCI controller on PCI [0000:07:00.0] using ADMA
[   14.097652] sdhci-pci 0000:07:00.2: SDHCI controller found [197b:2381] (rev 0)
[   14.097676] sdhci-pci 0000:07:00.2: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   14.097689] sdhci-pci 0000:07:00.2: Refusing to bind to secondary interface.
[   14.097697] sdhci-pci 0000:07:00.2: PCI INT A disabled
[   14.233807] input: PC Speaker as /devices/platform/pcspkr/input/input8
[   14.389010] ath9k: 0.1
[   14.395307] ath9k 0000:04:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   14.395324] ath9k 0000:04:00.0: setting latency timer to 64
[   14.828745] phy0: Selected rate control algorithm 'ath9k_rate_control'
[   14.952055] phy0: Atheros 9280: mem=0xf8e00000, irq=17
[   14.990091] acer-wmi: Acer Laptop ACPI-WMI Extras
[   15.020676] acer-wmi: Unable to detect available WMID devices
[   15.063437] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   15.063471] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   15.094288] hda_codec: Unknown model for ALC268, trying auto-probe from BIOS...
[   15.420719] ACPI: Battery Slot [BAT0] (battery present)
[   15.825802] input: PS/2 Mouse as /devices/platform/i8042/serio1/input/input9
[   15.928539] input: AlpsPS/2 ALPS GlidePoint as /devices/platform/i8042/serio1/input/input10
[   16.705279] lp: driver loaded but no devices found
[   16.833763] Adding 3976048k swap on /dev/sda7.  Priority:-1 extents:1 across:3976048k
[   17.388672] EXT3 FS on sda5, internal journal
[   18.253571] kjournald starting.  Commit interval 5 seconds
[   18.253885] EXT3 FS on sda6, internal journal
[   18.253890] EXT3-fs: mounted filesystem with ordered data mode.
[   18.557414] type=1505 audit(1248453571.016:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=4218
[   18.737215] type=1505 audit(1248453571.196:3): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=4223
[   18.737431] type=1505 audit(1248453571.196:4): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=4223
[   18.876534] ip_tables: (C) 2000-2006 Netfilter Core Team
[   20.370012] warning: `avahi-daemon' uses 32-bit capabilities (legacy support in use)
[   20.431790] apm: BIOS not found.
[   20.606408] ppdev: user-space parallel port driver
[   26.863736] [drm] Initialized drm 1.1.0 20060810
[   26.884383] pci 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   26.884400] pci 0000:00:02.0: setting latency timer to 64
[   26.887223] [drm] Initialized i915 1.6.0 20060119 on minor 0
[   27.193131] r8169: eth0: link down
[   27.286247] NET: Registered protocol family 17
[   28.030118] set status page addr 0x03fff000
[   28.043176] wlan0: authenticate with AP 00:18:f8:e3:0a:68
[   28.046645] wlan0: authenticated
[   28.046660] wlan0: associate with AP 00:18:f8:e3:0a:68
[   28.048547] wlan0: RX AssocResp from 00:18:f8:e3:0a:68 (capab=0x401 status=0 aid=2)
[   28.048557] wlan0: associated
[   28.060864] wlan0: disassociating by local choice (reason=3)
[   59.650536] wlan0: authenticate with AP 00:18:f8:e3:0a:68
[   59.650650] wlan0: authenticate with AP 00:18:f8:e3:0a:68
[   59.653016] wlan0: authenticated
[   59.653026] wlan0: associate with AP 00:18:f8:e3:0a:68
[   59.658308] wlan0: RX ReassocResp from 00:18:f8:e3:0a:68 (capab=0x401 status=0 aid=2)
[   59.658317] wlan0: associated
[   60.945427] CPU0 attaching NULL sched-domain.
[   60.945440] CPU1 attaching NULL sched-domain.
[   60.953311] CPU0 attaching sched-domain:
[   60.953317]  domain 0: span 0-1 level MC
[   60.953320]   groups: 0 1
[   60.953325] CPU1 attaching sched-domain:
[   60.953328]  domain 0: span 0-1 level MC
[   60.953330]   groups: 1 0
[   64.963526] NET: Registered protocol family 10
[   64.964759] lo: Disabled Privacy Extensions
[   64.965895] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   75.532569] wlan0: no IPv6 routers present

```

---

### Post by doyleman on 2009-07-27
bump

---

