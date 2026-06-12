---
title: "thinkpad W500: FN + F7 doesn't work after ubuntu recent update"
date: 2009-03-03
forum: Hardware
---

### Post by Bashar &quot; on 2009-03-03
Hello,
for some reason the FN + F7 key does not work anymore when i press it, it used to work just fine but after yesterday or day before update for ubuntu it stopped working

any idea what might be the problem or how to manually press it? because my DisplayPort is not enabled by default even when mirroring the screens it doesn't work, only the VGA port when mirroring screens works

Please advise.

Thank you

---

### Post by K. Hendrik on 2009-03-03
Can you please post the result of
```
xev
```
start xev move the mouse over the square and press Fn+F7
when you move the mouse lots of values will flod the terminal just post the lines which pop up when you press Fn+F7 it could be that no value pops up than please post the last 10-20 line of the result of
```
dmesg
```

---

### Post by Bashar &quot; on 2009-03-03
no lines pops when i press Fn+F7 

and here is dmesg output:
```
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.27-11-generic (buildd@rothera) (gcc version 4.3.2 (Ubuntu 4.3.2-1ubuntu11) ) #1 SMP Thu Jan 29 19:24:39 UTC 2009 (Ubuntu 2.6.27-11.27-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009ac00 (usable)
[    0.000000]  BIOS-e820: 000000000009ac00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000d6000 - 00000000000d8000 (reserved)
[    0.000000]  BIOS-e820: 00000000000dc000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 00000000bf8a1000 (usable)
[    0.000000]  BIOS-e820: 00000000bf8a1000 - 00000000bf8a7000 (reserved)
[    0.000000]  BIOS-e820: 00000000bf8a7000 - 00000000bf9b7000 (usable)
[    0.000000]  BIOS-e820: 00000000bf9b7000 - 00000000bfa0f000 (reserved)
[    0.000000]  BIOS-e820: 00000000bfa0f000 - 00000000bfac7000 (usable)
[    0.000000]  BIOS-e820: 00000000bfac7000 - 00000000bfad2000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000bfad2000 - 00000000bfad5000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000bfad5000 - 00000000bfad9000 (reserved)
[    0.000000]  BIOS-e820: 00000000bfad9000 - 00000000bfadd000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000bfadd000 - 00000000bfae0000 (reserved)
[    0.000000]  BIOS-e820: 00000000bfae0000 - 00000000bfb07000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000bfb07000 - 00000000bfb08000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000bfb08000 - 00000000bfd0f000 (reserved)
[    0.000000]  BIOS-e820: 00000000bfd0f000 - 00000000bfd9f000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000bfd9f000 - 00000000bfdff000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000bfdff000 - 00000000bfe00000 (usable)
[    0.000000]  BIOS-e820: 00000000bfe00000 - 00000000c0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed00000 - 00000000fed00400 (reserved)
[    0.000000]  BIOS-e820: 00000000fed10000 - 00000000fed14000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed18000 - 00000000fed1a000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed1c000 - 00000000fed90000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000ff800000 - 0000000100000000 (reserved)
[    0.000000]  BIOS-e820: 0000000100000000 - 000000013c000000 (usable)
[    0.000000] DMI present.
[    0.000000] last_pfn = 0xbfe00 max_arch_pfn = 0x100000
[    0.000000] kernel direct mapping tables up to 38000000 @ 7000-c000
[    0.000000] RAMDISK: 3782b000 - 37fefe0c
[    0.000000] ACPI: RSDP 000F6550, 0024 (r2 LENOVO)
[    0.000000] ACPI: XSDT BFD6A4DE, 0094 (r1 LENOVO TP-6F        1130  LTP        0)
[    0.000000] ACPI: FACP BFD6A600, 00F4 (r3 LENOVO TP-6F        1130 LNVO        1)
[    0.000000] ACPI: DSDT BFD6A9DB, F190 (r1 LENOVO TP-6F        1130 MSFT  3000000)
[    0.000000] ACPI: FACS BFD8E000, 0040
[    0.000000] ACPI: SSDT BFD6A7B4, 0227 (r1 LENOVO TP-6F        1130 MSFT  3000000)
[    0.000000] ACPI: ECDT BFD79B6B, 0052 (r1 LENOVO TP-6F        1130 LNVO        1)
[    0.000000] ACPI: APIC BFD79BBD, 0078 (r1 LENOVO TP-6F        1130 LNVO        1)
[    0.000000] ACPI: MCFG BFD79C35, 003C (r1 LENOVO TP-6F        1130 LNVO        1)
[    0.000000] ACPI: HPET BFD79C71, 0038 (r1 LENOVO TP-6F        1130 LNVO        1)
[    0.000000] ACPI: SLIC BFD79DC2, 0176 (r1 LENOVO TP-6F        1130  LTP        0)
[    0.000000] ACPI: BOOT BFD79F38, 0028 (r1 LENOVO TP-6F        1130  LTP        1)
[    0.000000] ACPI: ASF! BFD79F60, 00A0 (r16 LENOVO TP-6F        1130 PTL         1)
[    0.000000] ACPI: SSDT BFD8D213, 054F (r1 LENOVO TP-6F        1130 INTL 20050513)
[    0.000000] ACPI: TCPA BFB07000, 0032 (r0                        0             0)
[    0.000000] ACPI: SSDT BFAD4000, 0655 (r1  PmRef    CpuPm     3000 INTL 20050624)
[    0.000000] ACPI: SSDT BFAD3000, 0274 (r1  PmRef  Cpu0Tst     3000 INTL 20050624)
[    0.000000] ACPI: SSDT BFAD2000, 0242 (r1  PmRef    ApTst     3000 INTL 20050624)
[    0.000000] 2174MB HIGHMEM available.
[    0.000000] 896MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 38000000
[    0.000000]   low ram: 00000000 - 38000000
[    0.000000]   bootmap 00008000 - 0000f000
[    0.000000] (9 early reservations) ==> bootmem [0000000000 - 0038000000]
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000]   #1 [0000001000 - 0000002000]    EX TRAMPOLINE ==> [0000001000 - 0000002000]
[    0.000000]   #2 [0000006000 - 0000007000]       TRAMPOLINE ==> [0000006000 - 0000007000]
[    0.000000]   #3 [0000100000 - 00005c29e0]    TEXT DATA BSS ==> [0000100000 - 00005c29e0]
[    0.000000]   #4 [003782b000 - 0037fefe0c]          RAMDISK ==> [003782b000 - 0037fefe0c]
[    0.000000]   #5 [00005c3000 - 00005c6000]    INIT_PG_TABLE ==> [00005c3000 - 00005c6000]
[    0.000000]   #6 [000009ac00 - 0000100000]    BIOS reserved ==> [000009ac00 - 0000100000]
[    0.000000]   #7 [0000007000 - 0000008000]          PGTABLE ==> [0000007000 - 0000008000]
[    0.000000]   #8 [0000008000 - 000000f000]          BOOTMAP ==> [0000008000 - 000000f000]
[    0.000000] found SMP MP-table at [c00f6590] 000f6590
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000000 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x00038000
[    0.000000]   HighMem  0x00038000 -> 0x000bfe00
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[5] active PFN ranges
[    0.000000]     0: 0x00000000 -> 0x0000009a
[    0.000000]     0: 0x00000100 -> 0x000bf8a1
[    0.000000]     0: 0x000bf8a7 -> 0x000bf9b7
[    0.000000]     0: 0x000bfa0f -> 0x000bfac7
[    0.000000]     0: 0x000bfdff -> 0x000bfe00
[    0.000000] On node 0 totalpages: 784900
[    0.000000] free_area_init_node: node 0, pgdat c048c680, node_mem_map c1000000
[    0.000000]   DMA zone: 3958 pages, LIFO batch:0
[    0.000000]   Normal zone: 223300 pages, LIFO batch:31
[    0.000000]   HighMem zone: 550734 pages, LIFO batch:31
[    0.000000] ACPI: PM-Timer IO Port: 0x1008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x02] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x03] disabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 1, version 32, address 0xfec00000, GSI 0-23
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
[    0.000000] PM: Registered nosave memory: 000000000009a000 - 000000000009b000
[    0.000000] PM: Registered nosave memory: 000000000009b000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000d6000
[    0.000000] PM: Registered nosave memory: 00000000000d6000 - 00000000000d8000
[    0.000000] PM: Registered nosave memory: 00000000000d8000 - 00000000000dc000
[    0.000000] PM: Registered nosave memory: 00000000000dc000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at c2000000 (gap: c0000000:20000000)
[    0.000000] PERCPU: Allocating 41628 bytes of per cpu data
[    0.000000] NR_CPUS: 64, nr_cpu_ids: 4, nr_node_ids 1
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 777992
[    0.000000] Kernel command line: root=UUID=b11aac09-e8e0-4fd4-8e6e-05fef00f0182 ro quiet splash 
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] Extended CMOS year: 2000
[    0.000000] TSC: PIT calibration confirmed by PMTIMER.
[    0.000000] TSC: using PMTIMER calibration value
[    0.000000] Detected 2792.984 MHz processor.
[    0.004000] Console: colour VGA+ 80x25
[    0.004000] console [tty0] enabled
[    0.004000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.004000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.004000] Memory: 3097140k/3143680k available (2576k kernel code, 41556k reserved, 1165k data, 424k init, 2222504k highmem)
[    0.004000] virtual kernel memory layout:
[    0.004000]     fixmap  : 0xffc77000 - 0xfffff000   (3616 kB)
[    0.004000]     pkmap   : 0xff400000 - 0xff800000   (4096 kB)
[    0.004000]     vmalloc : 0xf8800000 - 0xff3fe000   ( 107 MB)
[    0.004000]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
[    0.004000]       .init : 0xc04ad000 - 0xc0517000   ( 424 kB)
[    0.004000]       .data : 0xc03840da - 0xc04a7680   (1165 kB)
[    0.004000]       .text : 0xc0100000 - 0xc03840da   (2576 kB)
[    0.004000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.004000] CPA: page pool initialized 1 of 1 pages preallocated
[    0.004000] SLUB: Genslabs=12, HWalign=64, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
[    0.004000] hpet clockevent registered
[    0.004000] Calibrating delay loop (skipped), value calculated using timer frequency.. 5585.96 BogoMIPS (lpj=11171936)
[    0.004000] Security Framework initialized
[    0.004000] SELinux:  Disabled at boot.
[    0.004000] AppArmor: AppArmor initialized
[    0.004000] Mount-cache hash table entries: 512
[    0.004000] Initializing cgroup subsys ns
[    0.004000] Initializing cgroup subsys cpuacct
[    0.004000] Initializing cgroup subsys memory
[    0.004000] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.004000] CPU: L2 cache: 6144K
[    0.004000] CPU: Physical Processor ID: 0
[    0.004000] CPU: Processor Core ID: 0
[    0.004000] using mwait in idle threads.
[    0.004000] Checking 'hlt' instruction... OK.
[    0.017456] ACPI: Core revision 20080609
[    0.022513] ACPI: Checking initramfs for custom DSDT
[    0.272220] ENABLING IO-APIC IRQs
[    0.276170] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.315853] CPU0: Intel(R) Core(TM)2 Duo CPU     T9600  @ 2.80GHz stepping 06
[    0.316019] Booting processor 1/1 ip 6000
[    0.004000] Initializing CPU#1
[    0.004000] Calibrating delay using timer specific routine.. 5585.87 BogoMIPS (lpj=11171744)
[    0.004000] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.004000] CPU: L2 cache: 6144K
[    0.004000] CPU: Physical Processor ID: 0
[    0.004000] CPU: Processor Core ID: 1
[    0.400827] CPU1: Intel(R) Core(TM)2 Duo CPU     T9600  @ 2.80GHz stepping 06
[    0.400840] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
[    0.404039] Brought up 2 CPUs
[    0.404041] Total of 2 processors activated (11171.84 BogoMIPS).
[    0.404059] CPU0 attaching sched-domain:
[    0.404061]  domain 0: span 0-1 level MC
[    0.404063]   groups: 0 1
[    0.404067] CPU1 attaching sched-domain:
[    0.404069]  domain 0: span 0-1 level MC
[    0.404070]   groups: 1 0
[    0.404128] net_namespace: 840 bytes
[    0.404128] Booting paravirtualized kernel on bare hardware
[    0.404213] Time: 22:07:00  Date: 03/03/09
[    0.404231] NET: Registered protocol family 16
[    0.404245] EISA bus registered
[    0.404245] ACPI FADT declares the system doesn't support PCIe ASPM, so disable it
[    0.404245] ACPI: bus type pci registered
[    0.404245] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 63
[    0.404245] PCI: MCFG area at e0000000 reserved in E820
[    0.404245] PCI: Using MMCONFIG for extended config space
[    0.404245] PCI: Using configuration type 1 for base access
[    0.405254] ACPI: EC: EC description table is found, configuring boot EC
[    0.413746] ACPI: BIOS _OSI(Linux) query ignored
[    0.413748] ACPI: If "acpi_osi=Linux" works better, please notify linux-acpi@vger.kernel.org
[    0.412042] ACPI: EC: non-query interrupt received, switching to interrupt mode
[    0.426059] ACPI: Interpreter enabled
[    0.426062] ACPI: (supports S0 S3 S4 S5)
[    0.426068] ACPI: Using IOAPIC for interrupt routing
[    0.448445] ACPI: EC: GPE = 0x11, I/O: command/status = 0x66, data = 0x62
[    0.448445] ACPI: EC: driver started in interrupt mode
[    0.448445] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.448445] pci 0000:00:01.0: PME# supported from D0 D3hot D3cold
[    0.448445] pci 0000:00:01.0: PME# disabled
[    0.448445] PCI: 0000:00:03.0 reg 10 64bit mmio: [fc226800, fc22680f]
[    0.448445] pci 0000:00:03.0: PME# supported from D0 D3hot D3cold
[    0.448445] pci 0000:00:03.0: PME# disabled
[    0.448445] PCI: 0000:00:19.0 reg 10 32bit mmio: [fc200000, fc21ffff]
[    0.448445] PCI: 0000:00:19.0 reg 14 32bit mmio: [fc225000, fc225fff]
[    0.448445] PCI: 0000:00:19.0 reg 18 io port: [1840, 185f]
[    0.448445] pci 0000:00:19.0: PME# supported from D0 D3hot D3cold
[    0.448445] pci 0000:00:19.0: PME# disabled
[    0.448445] PCI: 0000:00:1a.0 reg 20 io port: [1860, 187f]
[    0.448445] PCI: 0000:00:1a.1 reg 20 io port: [1880, 189f]
[    0.448486] PCI: 0000:00:1a.2 reg 20 io port: [18a0, 18bf]
[    0.448562] PCI: 0000:00:1a.7 reg 10 32bit mmio: [fc226c00, fc226fff]
[    0.448614] pci 0000:00:1a.7: PME# supported from D0 D3hot D3cold
[    0.448619] pci 0000:00:1a.7: PME# disabled
[    0.448660] PCI: 0000:00:1b.0 reg 10 64bit mmio: [fc220000, fc223fff]
[    0.448707] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    0.448711] pci 0000:00:1b.0: PME# disabled
[    0.448775] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.448779] pci 0000:00:1c.0: PME# disabled
[    0.448841] pci 0000:00:1c.1: PME# supported from D0 D3hot D3cold
[    0.448845] pci 0000:00:1c.1: PME# disabled
[    0.448908] pci 0000:00:1c.2: PME# supported from D0 D3hot D3cold
[    0.448912] pci 0000:00:1c.2: PME# disabled
[    0.448974] pci 0000:00:1c.3: PME# supported from D0 D3hot D3cold
[    0.448978] pci 0000:00:1c.3: PME# disabled
[    0.449041] pci 0000:00:1c.4: PME# supported from D0 D3hot D3cold
[    0.449045] pci 0000:00:1c.4: PME# disabled
[    0.449100] PCI: 0000:00:1d.0 reg 20 io port: [18c0, 18df]
[    0.449175] PCI: 0000:00:1d.1 reg 20 io port: [18e0, 18ff]
[    0.449249] PCI: 0000:00:1d.2 reg 20 io port: [1c00, 1c1f]
[    0.449325] PCI: 0000:00:1d.7 reg 10 32bit mmio: [fc227000, fc2273ff]
[    0.449378] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
[    0.449383] pci 0000:00:1d.7: PME# disabled
[    0.449583] PCI: 0000:00:1f.2 reg 10 io port: [1c40, 1c47]
[    0.449590] PCI: 0000:00:1f.2 reg 14 io port: [1834, 1837]
[    0.449596] PCI: 0000:00:1f.2 reg 18 io port: [1838, 183f]
[    0.449603] PCI: 0000:00:1f.2 reg 1c io port: [1830, 1833]
[    0.449610] PCI: 0000:00:1f.2 reg 20 io port: [1c20, 1c3f]
[    0.449616] PCI: 0000:00:1f.2 reg 24 32bit mmio: [fc226000, fc2267ff]
[    0.449648] pci 0000:00:1f.2: PME# supported from D3hot
[    0.449652] pci 0000:00:1f.2: PME# disabled
[    0.449675] PCI: 0000:00:1f.3 reg 10 64bit mmio: [fc227400, fc2274ff]
[    0.449692] PCI: 0000:00:1f.3 reg 20 io port: [1c60, 1c7f]
[    0.449745] PCI: 0000:01:00.0 reg 10 32bit mmio: [d0000000, dfffffff]
[    0.449752] PCI: 0000:01:00.0 reg 14 io port: [2000, 20ff]
[    0.449759] PCI: 0000:01:00.0 reg 18 32bit mmio: [cfff0000, cfffffff]
[    0.449781] PCI: 0000:01:00.0 reg 30 32bit mmio: [0, 1ffff]
[    0.449800] pci 0000:01:00.0: supports D1
[    0.449801] pci 0000:01:00.0: supports D2
[    0.449845] PCI: bridge 0000:00:01.0 io port: [2000, 2fff]
[    0.449848] PCI: bridge 0000:00:01.0 32bit mmio: [cff00000, cfffffff]
[    0.449851] PCI: bridge 0000:00:01.0 64bit mmio pref: [d0000000, dfffffff]
[    0.449996] PCI: 0000:03:00.0 reg 10 64bit mmio: [f4200000, f4201fff]
[    0.450089] pci 0000:03:00.0: PME# supported from D0 D3hot D3cold
[    0.450096] pci 0000:03:00.0: PME# disabled
[    0.450144] PCI: bridge 0000:00:1c.1 32bit mmio: [f4200000, f42fffff]
[    0.450218] PCI: 0000:04:00.0 reg 10 32bit mmio: [f4300000, f43003ff]
[    0.450238] PCI: 0000:04:00.0 reg 18 io port: [3000, 30ff]
[    0.450278] PCI: 0000:04:00.0 reg 30 32bit mmio: [0, ffff]
[    0.450358] PCI: bridge 0000:00:1c.2 io port: [3000, 3fff]
[    0.450362] PCI: bridge 0000:00:1c.2 32bit mmio: [f4300000, f43fffff]
[    0.450420] PCI: bridge 0000:00:1c.3 io port: [4000, 4fff]
[    0.450424] PCI: bridge 0000:00:1c.3 32bit mmio: [f8000000, f9ffffff]
[    0.450431] PCI: bridge 0000:00:1c.3 64bit mmio pref: [f4000000, f40fffff]
[    0.450484] PCI: bridge 0000:00:1c.4 io port: [5000, 5fff]
[    0.450488] PCI: bridge 0000:00:1c.4 32bit mmio: [fa000000, fbffffff]
[    0.450495] PCI: bridge 0000:00:1c.4 64bit mmio pref: [f4100000, f41fffff]
[    0.450542] PCI: 0000:15:00.0 reg 10 32bit mmio: [f4400000, f4400fff]
[    0.450561] pci 0000:15:00.0: supports D1
[    0.450563] pci 0000:15:00.0: supports D2
[    0.450564] pci 0000:15:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.450569] pci 0000:15:00.0: PME# disabled
[    0.450608] PCI: 0000:15:00.1 reg 10 32bit mmio: [f4401000, f44017ff]
[    0.450670] pci 0000:15:00.1: supports D1
[    0.450671] pci 0000:15:00.1: supports D2
[    0.450672] pci 0000:15:00.1: PME# supported from D0 D1 D2 D3hot D3cold
[    0.450677] pci 0000:15:00.1: PME# disabled
[    0.450717] PCI: 0000:15:00.2 reg 10 32bit mmio: [f4401800, f44018ff]
[    0.450779] pci 0000:15:00.2: supports D1
[    0.450780] pci 0000:15:00.2: supports D2
[    0.450781] pci 0000:15:00.2: PME# supported from D0 D1 D2 D3hot D3cold
[    0.450786] pci 0000:15:00.2: PME# disabled
[    0.450825] PCI: 0000:15:00.3 reg 10 32bit mmio: [f4401c00, f4401cff]
[    0.450887] pci 0000:15:00.3: supports D1
[    0.450888] pci 0000:15:00.3: supports D2
[    0.450890] pci 0000:15:00.3: PME# supported from D0 D1 D2 D3hot D3cold
[    0.450895] pci 0000:15:00.3: PME# disabled
[    0.450934] PCI: 0000:15:00.4 reg 10 32bit mmio: [f4402000, f44020ff]
[    0.450995] pci 0000:15:00.4: supports D1
[    0.450996] pci 0000:15:00.4: supports D2
[    0.450998] pci 0000:15:00.4: PME# supported from D0 D1 D2 D3hot D3cold
[    0.451003] pci 0000:15:00.4: PME# disabled
[    0.451042] PCI: 0000:15:00.5 reg 10 32bit mmio: [f4402400, f44024ff]
[    0.451104] pci 0000:15:00.5: supports D1
[    0.451105] pci 0000:15:00.5: supports D2
[    0.451106] pci 0000:15:00.5: PME# supported from D0 D1 D2 D3hot D3cold
[    0.451111] pci 0000:15:00.5: PME# disabled
[    0.451174] pci 0000:00:1e.0: transparent bridge
[    0.451178] PCI: bridge 0000:00:1e.0 io port: [6000, 9fff]
[    0.451182] PCI: bridge 0000:00:1e.0 32bit mmio: [f4400000, f7ffffff]
[    0.451189] PCI: bridge 0000:00:1e.0 64bit mmio pref: [f0000000, f3ffffff]
[    0.451246] bus 00 -> node 0
[    0.451252] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.452246] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.AGP_._PRT]
[    0.452366] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.EXP0._PRT]
[    0.452490] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.EXP1._PRT]
[    0.452614] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.EXP2._PRT]
[    0.452737] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.EXP3._PRT]
[    0.452863] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.EXP4._PRT]
[    0.452988] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCI1._PRT]
[    0.456171] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 9 10 *11)
[    0.456370] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 9 10 *11)
[    0.456567] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 9 10 *11)
[    0.456764] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 9 10 *11)
[    0.456963] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 9 10 *11)
[    0.457160] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 9 10 *11)
[    0.457357] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 9 10 *11)
[    0.457553] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 9 10 *11)
[    0.457648] ACPI: Power Resource [PUBS] (on)
[    0.457648] Linux Plug and Play Support v0.97 (c) Adam Belay
[    0.457648] pnp: PnP ACPI init
[    0.457648] ACPI: bus type pnp registered
[    0.472523] pnp: PnP ACPI: found 10 devices
[    0.472525] ACPI: ACPI bus type pnp unregistered
[    0.472527] PnPBIOS: Disabled by ACPI PNP
[    0.472769] PCI: Using ACPI for IRQ routing
[    0.476044] NET: Registered protocol family 8
[    0.476046] NET: Registered protocol family 20
[    0.476063] NetLabel: Initializing
[    0.476063] NetLabel:  domain hash size = 128
[    0.476063] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.476063] NetLabel:  unlabeled traffic allowed by default
[    0.476063] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0
[    0.476063] hpet0: 4 64-bit timers, 14318180 Hz
[    0.477686] tracer: 772 pages allocated for 65536 entries of 48 bytes
[    0.477688]    actual entries 65620
[    0.477748] AppArmor: AppArmor Filesystem Enabled
[    0.477772] ACPI: RTC can wake from S4
[    0.480866] system 00:00: iomem range 0x0-0x9ffff could not be reserved
[    0.480868] system 00:00: iomem range 0xc0000-0xc3fff could not be reserved
[    0.480870] system 00:00: iomem range 0xc4000-0xc7fff could not be reserved
[    0.480872] system 00:00: iomem range 0xc8000-0xcbfff could not be reserved
[    0.480874] system 00:00: iomem range 0xcc000-0xcffff could not be reserved
[    0.480876] system 00:00: iomem range 0xd0000-0xd3fff could not be reserved
[    0.480878] system 00:00: iomem range 0xd4000-0xd7fff could not be reserved
[    0.480880] system 00:00: iomem range 0xdc000-0xdffff could not be reserved
[    0.480882] system 00:00: iomem range 0xe0000-0xe3fff could not be reserved
[    0.480884] system 00:00: iomem range 0xe4000-0xe7fff could not be reserved
[    0.480886] system 00:00: iomem range 0xe8000-0xebfff could not be reserved
[    0.480888] system 00:00: iomem range 0xec000-0xeffff could not be reserved
[    0.480891] system 00:00: iomem range 0xf0000-0xfffff could not be reserved
[    0.480893] system 00:00: iomem range 0x100000-0xbfffffff could not be reserved
[    0.480895] system 00:00: iomem range 0xfec00000-0xfed3ffff could not be reserved
[    0.480897] system 00:00: iomem range 0xfed4c000-0xffffffff could not be reserved
[    0.480903] system 00:02: ioport range 0x164e-0x164f has been reserved
[    0.480905] system 00:02: ioport range 0x1000-0x107f has been reserved
[    0.480907] system 00:02: ioport range 0x1180-0x11ff has been reserved
[    0.480909] system 00:02: ioport range 0x800-0x80f has been reserved
[    0.480911] system 00:02: ioport range 0x15e0-0x15ef has been reserved
[    0.480915] system 00:02: ioport range 0x1600-0x1641 has been reserved
[    0.480917] system 00:02: ioport range 0x1600-0x161b has been reserved
[    0.480919] system 00:02: iomem range 0xe0000000-0xefffffff could not be reserved
[    0.480921] system 00:02: iomem range 0xfed1c000-0xfed1ffff could not be reserved
[    0.480924] system 00:02: iomem range 0xfed10000-0xfed13fff could not be reserved
[    0.480926] system 00:02: iomem range 0xfed18000-0xfed18fff could not be reserved
[    0.480928] system 00:02: iomem range 0xfed19000-0xfed19fff could not be reserved
[    0.480930] system 00:02: iomem range 0xfed45000-0xfed4bfff could not be reserved
[    0.500860] Switched to high resolution mode on CPU 1
[    0.504031] Switched to high resolution mode on CPU 0
[    0.515822] pci 0000:00:01.0: PCI bridge, secondary bus 0000:01
[    0.515824] pci 0000:00:01.0:   IO window: 0x2000-0x2fff
[    0.515827] pci 0000:00:01.0:   MEM window: 0xcff00000-0xcfffffff
[    0.515830] pci 0000:00:01.0:   PREFETCH window: 0x000000d0000000-0x000000dfffffff
[    0.515833] pci 0000:00:1c.0: PCI bridge, secondary bus 0000:02
[    0.515835] pci 0000:00:1c.0:   IO window: disabled
[    0.515840] pci 0000:00:1c.0:   MEM window: disabled
[    0.515844] pci 0000:00:1c.0:   PREFETCH window: disabled
[    0.515851] pci 0000:00:1c.1: PCI bridge, secondary bus 0000:03
[    0.515852] pci 0000:00:1c.1:   IO window: disabled
[    0.515857] pci 0000:00:1c.1:   MEM window: 0xf4200000-0xf42fffff
[    0.515861] pci 0000:00:1c.1:   PREFETCH window: disabled
[    0.515868] pci 0000:00:1c.2: PCI bridge, secondary bus 0000:04
[    0.515871] pci 0000:00:1c.2:   IO window: 0x3000-0x3fff
[    0.515876] pci 0000:00:1c.2:   MEM window: 0xf4300000-0xf43fffff
[    0.515880] pci 0000:00:1c.2:   PREFETCH window: 0x000000c2000000-0x000000c20fffff
[    0.515887] pci 0000:00:1c.3: PCI bridge, secondary bus 0000:05
[    0.515890] pci 0000:00:1c.3:   IO window: 0x4000-0x4fff
[    0.515895] pci 0000:00:1c.3:   MEM window: 0xf8000000-0xf9ffffff
[    0.515899] pci 0000:00:1c.3:   PREFETCH window: 0x000000f4000000-0x000000f40fffff
[    0.515906] pci 0000:00:1c.4: PCI bridge, secondary bus 0000:0d
[    0.515909] pci 0000:00:1c.4:   IO window: 0x5000-0x5fff
[    0.515914] pci 0000:00:1c.4:   MEM window: 0xfa000000-0xfbffffff
[    0.515918] pci 0000:00:1c.4:   PREFETCH window: 0x000000f4100000-0x000000f41fffff
[    0.515927] pci 0000:15:00.0: CardBus bridge, secondary bus 0000:16
[    0.515928] pci 0000:15:00.0:   IO window: 0x006000-0x0060ff
[    0.515933] pci 0000:15:00.0:   IO window: 0x006400-0x0064ff
[    0.515938] pci 0000:15:00.0:   PREFETCH window: 0xf0000000-0xf3ffffff
[    0.515943] pci 0000:15:00.0:   MEM window: 0xc4000000-0xc7ffffff
[    0.515948] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:15
[    0.515951] pci 0000:00:1e.0:   IO window: 0x6000-0x9fff
[    0.515956] pci 0000:00:1e.0:   MEM window: 0xf4400000-0xf7ffffff
[    0.515960] pci 0000:00:1e.0:   PREFETCH window: 0x000000f0000000-0x000000f3ffffff
[    0.515972] pci 0000:00:01.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.515975] pci 0000:00:01.0: setting latency timer to 64
[    0.515982] pci 0000:00:1c.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    0.515987] pci 0000:00:1c.0: setting latency timer to 64
[    0.515995] pci 0000:00:1c.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[    0.515999] pci 0000:00:1c.1: setting latency timer to 64
[    0.516007] pci 0000:00:1c.2: PCI INT C -> GSI 22 (level, low) -> IRQ 22
[    0.516011] pci 0000:00:1c.2: setting latency timer to 64
[    0.516019] pci 0000:00:1c.3: PCI INT D -> GSI 23 (level, low) -> IRQ 23
[    0.516023] pci 0000:00:1c.3: setting latency timer to 64
[    0.516031] pci 0000:00:1c.4: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    0.516035] pci 0000:00:1c.4: setting latency timer to 64
[    0.516042] pci 0000:00:1e.0: setting latency timer to 64
[    0.516051] pci 0000:15:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.516057] bus: 00 index 0 io port: [0, ffff]
[    0.516058] bus: 00 index 1 mmio: [0, ffffffff]
[    0.516060] bus: 01 index 0 io port: [2000, 2fff]
[    0.516061] bus: 01 index 1 mmio: [cff00000, cfffffff]
[    0.516063] bus: 01 index 2 mmio: [d0000000, dfffffff]
[    0.516064] bus: 01 index 3 mmio: [0, 0]
[    0.516065] bus: 02 index 0 mmio: [0, 0]
[    0.516067] bus: 02 index 1 mmio: [0, 0]
[    0.516068] bus: 02 index 2 mmio: [0, 0]
[    0.516069] bus: 02 index 3 mmio: [0, 0]
[    0.516070] bus: 03 index 0 mmio: [0, 0]
[    0.516072] bus: 03 index 1 mmio: [f4200000, f42fffff]
[    0.516073] bus: 03 index 2 mmio: [0, 0]
[    0.516074] bus: 03 index 3 mmio: [0, 0]
[    0.516076] bus: 04 index 0 io port: [3000, 3fff]
[    0.516077] bus: 04 index 1 mmio: [f4300000, f43fffff]
[    0.516079] bus: 04 index 2 mmio: [c2000000, c20fffff]
[    0.516080] bus: 04 index 3 mmio: [0, 0]
[    0.516081] bus: 05 index 0 io port: [4000, 4fff]
[    0.516083] bus: 05 index 1 mmio: [f8000000, f9ffffff]
[    0.516084] bus: 05 index 2 mmio: [f4000000, f40fffff]
[    0.516085] bus: 05 index 3 mmio: [0, 0]
[    0.516087] bus: 0d index 0 io port: [5000, 5fff]
[    0.516088] bus: 0d index 1 mmio: [fa000000, fbffffff]
[    0.516090] bus: 0d index 2 mmio: [f4100000, f41fffff]
[    0.516091] bus: 0d index 3 mmio: [0, 0]
[    0.516092] bus: 15 index 0 io port: [6000, 9fff]
[    0.516094] bus: 15 index 1 mmio: [f4400000, f7ffffff]
[    0.516095] bus: 15 index 2 mmio: [f0000000, f3ffffff]
[    0.516097] bus: 15 index 3 io port: [0, ffff]
[    0.516098] bus: 15 index 4 mmio: [0, ffffffff]
[    0.516099] bus: 16 index 0 io port: [6000, 60ff]
[    0.516101] bus: 16 index 1 io port: [6400, 64ff]
[    0.516102] bus: 16 index 2 mmio: [f0000000, f3ffffff]
[    0.516104] bus: 16 index 3 mmio: [c4000000, c7ffffff]
[    0.516109] NET: Registered protocol family 2
[    0.528537] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.528698] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.528925] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.529034] TCP: Hash tables configured (established 131072 bind 65536)
[    0.529036] TCP reno registered
[    0.532545] NET: Registered protocol family 1
[    0.532609] checking if image is initramfs... it is
[    1.020676] Freeing initrd memory: 7955k freed
[    1.020930] Simple Boot Flag at 0x35 set to 0x1
[    1.021462] audit: initializing netlink socket (disabled)
[    1.021474] type=2000 audit(1236118020.020:1): initialized
[    1.025807] highmem bounce pool size: 64 pages
[    1.025811] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    1.027334] VFS: Disk quotas dquot_6.5.1
[    1.027389] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    1.027464] msgmni has been set to 1725
[    1.027548] io scheduler noop registered
[    1.027550] io scheduler anticipatory registered
[    1.027552] io scheduler deadline registered
[    1.027560] io scheduler cfq registered (default)
[    1.027706] pci 0000:01:00.0: Boot video device
[    1.027800] pcieport-driver 0000:00:01.0: setting latency timer to 64
[    1.027828] pcieport-driver 0000:00:01.0: found MSI capability
[    1.027852] pci_express 0000:00:01.0:pcie00: allocate port service
[    1.027881] pci_express 0000:00:01.0:pcie02: allocate port service
[    1.027907] pci_express 0000:00:01.0:pcie03: allocate port service
[    1.027970] pcieport-driver 0000:00:1c.0: setting latency timer to 64
[    1.028013] pcieport-driver 0000:00:1c.0: found MSI capability
[    1.028055] pci_express 0000:00:1c.0:pcie00: allocate port service
[    1.028082] pci_express 0000:00:1c.0:pcie02: allocate port service
[    1.028107] pci_express 0000:00:1c.0:pcie03: allocate port service
[    1.028197] pcieport-driver 0000:00:1c.1: setting latency timer to 64
[    1.028241] pcieport-driver 0000:00:1c.1: found MSI capability
[    1.028282] pci_express 0000:00:1c.1:pcie00: allocate port service
[    1.028308] pci_express 0000:00:1c.1:pcie02: allocate port service
[    1.028334] pci_express 0000:00:1c.1:pcie03: allocate port service
[    1.028423] pcieport-driver 0000:00:1c.2: setting latency timer to 64
[    1.028466] pcieport-driver 0000:00:1c.2: found MSI capability
[    1.028511] pci_express 0000:00:1c.2:pcie00: allocate port service
[    1.028538] pci_express 0000:00:1c.2:pcie02: allocate port service
[    1.028563] pci_express 0000:00:1c.2:pcie03: allocate port service
[    1.028651] pcieport-driver 0000:00:1c.3: setting latency timer to 64
[    1.028695] pcieport-driver 0000:00:1c.3: found MSI capability
[    1.028736] pci_express 0000:00:1c.3:pcie00: allocate port service
[    1.028762] pci_express 0000:00:1c.3:pcie02: allocate port service
[    1.028789] pci_express 0000:00:1c.3:pcie03: allocate port service
[    1.028878] pcieport-driver 0000:00:1c.4: setting latency timer to 64
[    1.028921] pcieport-driver 0000:00:1c.4: found MSI capability
[    1.028963] pci_express 0000:00:1c.4:pcie00: allocate port service
[    1.028989] pci_express 0000:00:1c.4:pcie02: allocate port service
[    1.029016] pci_express 0000:00:1c.4:pcie03: allocate port service
[    1.029266] isapnp: Scanning for PnP cards...
[    1.383350] isapnp: No Plug & Play device found
[    1.404907] hpet_resources: 0xfed00000 is busy
[    1.404969] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
[    1.406506] brd: module loaded
[    1.406554] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[    1.406634] PNP: PS/2 Controller [PNP0303:KBD,PNP0f13:MOU] at 0x60,0x64 irq 1,12
[    1.416257] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.416261] serio: i8042 AUX port at 0x60,0x64 irq 12
[    1.420072] mice: PS/2 mouse device common for all mice
[    1.420152] rtc_cmos 00:07: rtc core: registered rtc_cmos as rtc0
[    1.420178] rtc0: alarms up to one month, y3k, hpet irqs
[    1.420258] EISA: Probing bus 0 at eisa.0
[    1.420264] Cannot allocate resource for EISA slot 1
[    1.420266] Cannot allocate resource for EISA slot 2
[    1.420267] Cannot allocate resource for EISA slot 3
[    1.420269] Cannot allocate resource for EISA slot 4
[    1.420270] Cannot allocate resource for EISA slot 5
[    1.420272] Cannot allocate resource for EISA slot 6
[    1.420273] Cannot allocate resource for EISA slot 7
[    1.420274] Cannot allocate resource for EISA slot 8
[    1.420276] EISA: Detected 0 cards.
[    1.420278] cpuidle: using governor ladder
[    1.420280] cpuidle: using governor menu
[    1.420624] TCP cubic registered
[    1.420643] Using IPI No-Shortcut mode
[    1.420755] registered taskstats version 1
[    1.420867]   Magic number: 1:604:147
[    1.420875] tty ttyp1: hash matches
[    1.420889] acpi device:18: hash matches
[    1.420918] rtc_cmos 00:07: setting system clock to 2009-03-03 22:07:01 UTC (1236118021)
[    1.420920] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.420922] EDD information not available.
[    1.421157] Freeing unused kernel memory: 424k freed
[    1.421183] Write protecting the kernel text: 2580k
[    1.421202] Write protecting the kernel read-only data: 940k
[    1.436526] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[    1.540043] fuse init (API version 7.9)
[    1.588492] ACPI: SSDT BFAD7AA0, 030A (r1  PmRef  Cpu0Ist     3000 INTL 20050624)
[    1.588926] ACPI: SSDT BFAD5020, 087A (r1  PmRef  Cpu0Cst     3001 INTL 20050624)
[    1.591219] Monitor-Mwait will be used to enter C-1 state
[    1.591221] Monitor-Mwait will be used to enter C-2 state
[    1.591223] Monitor-Mwait will be used to enter C-3 state
[    1.591344] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[    1.591380] processor ACPI0007:00: registered as cooling_device0
[    1.591383] ACPI: Processor [CPU0] (supports 8 throttling states)
[    1.591777] ACPI: SSDT BFAD6CA0, 01CF (r1  PmRef    ApIst     3000 INTL 20050624)
[    1.592227] ACPI: SSDT BFAD6F20, 008D (r1  PmRef    ApCst     3000 INTL 20050624)
[    1.599998] Marking TSC unstable due to TSC halts in idle
[    1.697035] ACPI: CPU1 (power states: C1[C1] C2[C2] C3[C3])
[    1.697087] processor ACPI0007:01: registered as cooling_device1
[    1.697090] ACPI: Processor [CPU1] (supports 8 throttling states)
[    1.700871] thermal LNXTHERM:01: registered as thermal_zone0
[    1.704275] ACPI: Thermal Zone [THM0] (48 C)
[    1.705271] thermal LNXTHERM:02: registered as thermal_zone1
[    1.706513] ACPI: Thermal Zone [THM1] (46 C)
[    1.905331] usbcore: registered new interface driver usbfs
[    1.905347] usbcore: registered new interface driver hub
[    1.905368] usbcore: registered new device driver usb
[    1.912590] USB Universal Host Controller Interface driver v3.0
[    1.913157] uhci_hcd 0000:00:1a.0: power state changed by ACPI to D0
[    1.913165] uhci_hcd 0000:00:1a.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    1.913172] uhci_hcd 0000:00:1a.0: setting latency timer to 64
[    1.913175] uhci_hcd 0000:00:1a.0: UHCI Host Controller
[    1.913204] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 1
[    1.913240] uhci_hcd 0000:00:1a.0: irq 20, io base 0x00001860
[    1.913339] usb usb1: configuration #1 chosen from 1 choice
[    1.913357] hub 1-0:1.0: USB hub found
[    1.913362] hub 1-0:1.0: 2 ports detected
[    1.973961] Warning! ehci_hcd should always be loaded before uhci_hcd and ohci_hcd, not after
[    1.992163] e1000e: Intel(R) PRO/1000 Network Driver - 0.3.3.3-k6
[    1.992165] e1000e: Copyright (c) 1999-2008 Intel Corporation.
[    1.996344] ACPI: ACPI Dock Station Driver
[    2.010548] SCSI subsystem initialized
[    2.051090] libata version 3.00 loaded.
[    2.120186] uhci_hcd 0000:00:1a.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[    2.120194] uhci_hcd 0000:00:1a.1: setting latency timer to 64
[    2.120197] uhci_hcd 0000:00:1a.1: UHCI Host Controller
[    2.120215] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 2
[    2.120247] uhci_hcd 0000:00:1a.1: irq 21, io base 0x00001880
[    2.120313] usb usb2: configuration #1 chosen from 1 choice
[    2.120332] hub 2-0:1.0: USB hub found
[    2.120340] hub 2-0:1.0: 2 ports detected
[    2.232071] usb 1-1: new low speed USB device using uhci_hcd and address 2
[    2.329128] uhci_hcd 0000:00:1a.2: power state changed by ACPI to D0
[    2.329134] uhci_hcd 0000:00:1a.2: PCI INT C -> GSI 22 (level, low) -> IRQ 22
[    2.329141] uhci_hcd 0000:00:1a.2: setting latency timer to 64
[    2.329144] uhci_hcd 0000:00:1a.2: UHCI Host Controller
[    2.329163] uhci_hcd 0000:00:1a.2: new USB bus registered, assigned bus number 3
[    2.329192] uhci_hcd 0000:00:1a.2: irq 22, io base 0x000018a0
[    2.329255] usb usb3: configuration #1 chosen from 1 choice
[    2.329273] hub 3-0:1.0: USB hub found
[    2.329278] hub 3-0:1.0: 2 ports detected
[    2.414434] usb 1-1: configuration #1 chosen from 1 choice
[    2.500066] Clocksource tsc unstable (delta = -261127304 ns)
[    2.528111] usb 2-1: new full speed USB device using uhci_hcd and address 2
[    2.536398] e1000e 0000:00:19.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    2.536405] e1000e 0000:00:19.0: setting latency timer to 64
[    2.626507] 0000:00:19.0: eth0: (PCI Express:2.5GB/s:Width x1) 00:1c:25:95:b8:56
[    2.626509] 0000:00:19.0: eth0: Intel(R) PRO/1000 Network Connection
[    2.626536] 0000:00:19.0: eth0: MAC: 5, PHY: 8, PBA No: 1008ff-0ff
[    2.627597] ehci_hcd 0000:00:1a.7: power state changed by ACPI to D0
[    2.627604] ehci_hcd 0000:00:1a.7: PCI INT D -> GSI 23 (level, low) -> IRQ 23
[    2.627610] ehci_hcd 0000:00:1a.7: setting latency timer to 64
[    2.627613] ehci_hcd 0000:00:1a.7: EHCI Host Controller
[    2.627631] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 4
[    2.631527] ehci_hcd 0000:00:1a.7: debug port 1
[    2.631532] ehci_hcd 0000:00:1a.7: cache line size of 32 is not supported
[    2.631540] ehci_hcd 0000:00:1a.7: irq 23, io mem 0xfc226c00
[    2.641784] Monitor-Mwait will be used to enter C-3 state
[    2.652106] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    2.652194] usb usb4: configuration #1 chosen from 1 choice
[    2.652226] hub 4-0:1.0: USB hub found
[    2.652234] hub 4-0:1.0: 6 ports detected
[    2.860892] uhci_hcd 0000:00:1d.0: power state changed by ACPI to D0
[    2.860899] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    2.860907] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    2.860911] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    2.860945] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 5
[    2.860981] uhci_hcd 0000:00:1d.0: irq 16, io base 0x000018c0
[    2.861080] usb usb5: configuration #1 chosen from 1 choice
[    2.861111] hub 5-0:1.0: USB hub found
[    2.861118] hub 5-0:1.0: 2 ports detected
[    2.964250] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    2.964256] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    2.964259] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    2.964276] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 6
[    2.964303] uhci_hcd 0000:00:1d.1: irq 17, io base 0x000018e0
[    2.964362] usb usb6: configuration #1 chosen from 1 choice
[    2.964385] hub 6-0:1.0: USB hub found
[    2.964390] hub 6-0:1.0: 2 ports detected
[    3.052609] usb 2-1: device not accepting address 2, error -71
[    3.108091] hub 2-0:1.0: unable to enumerate USB device on port 1
[    3.173026] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    3.173031] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    3.173034] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    3.173051] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 7
[    3.173078] uhci_hcd 0000:00:1d.2: irq 18, io base 0x00001c00
[    3.173136] usb usb7: configuration #1 chosen from 1 choice
[    3.173164] hub 7-0:1.0: USB hub found
[    3.173168] hub 7-0:1.0: 2 ports detected
[    3.277707] ehci_hcd 0000:00:1d.7: power state changed by ACPI to D0
[    3.277715] ehci_hcd 0000:00:1d.7: PCI INT D -> GSI 19 (level, low) -> IRQ 19
[    3.277722] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    3.277725] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    3.277743] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 8
[    3.281646] ehci_hcd 0000:00:1d.7: debug port 1
[    3.281652] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
[    3.281660] ehci_hcd 0000:00:1d.7: irq 19, io mem 0xfc227000
[    3.296013] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    3.296070] usb usb8: configuration #1 chosen from 1 choice
[    3.296088] hub 8-0:1.0: USB hub found
[    3.296093] hub 8-0:1.0: 6 ports detected
[    3.504536] ahci 0000:00:1f.2: version 3.0
[    3.504547] ahci 0000:00:1f.2: PCI INT B -> GSI 16 (level, low) -> IRQ 16
[    3.504631] ahci 0000:00:1f.2: AHCI 0001.0200 32 slots 4 ports 3 Gbps 0x3 impl SATA mode
[    3.504634] ahci 0000:00:1f.2: flags: 64bit ncq sntf stag pm led clo pio slum part 
[    3.504639] ahci 0000:00:1f.2: setting latency timer to 64
[    3.504779] scsi0 : ahci
[    3.505006] scsi1 : ahci
[    3.505219] scsi2 : ahci
[    3.505434] scsi3 : ahci
[    3.506150] ata1: SATA max UDMA/133 abar m2048@0xfc226000 port 0xfc226100 irq 217
[    3.506153] ata2: SATA max UDMA/133 abar m2048@0xfc226000 port 0xfc226180 irq 217
[    3.506154] ata3: DUMMY
[    3.506155] ata4: DUMMY
[    3.756063] usb 4-6: new high speed USB device using ehci_hcd and address 5
[    3.824072] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    3.825301] ata1.00: ACPI cmd ef/02:00:00:00:00:a0 succeeded
[    3.825303] ata1.00: ACPI cmd f5/00:00:00:00:00:a0 filtered out
[    3.825543] ata1.00: ACPI cmd ef/5f:00:00:00:00:a0 succeeded
[    3.825545] ata1.00: ACPI cmd ef/10:03:00:00:00:a0 filtered out
[    3.826527] ata1.00: ATA-8: HITACHI HTS722016K9SA00, DCDZC75A, max UDMA/133
[    3.826529] ata1.00: 312581808 sectors, multi 16: LBA48 NCQ (depth 31/32)
[    3.827976] ata1.00: ACPI cmd ef/02:00:00:00:00:a0 succeeded
[    3.827978] ata1.00: ACPI cmd f5/00:00:00:00:00:a0 filtered out
[    3.828211] ata1.00: ACPI cmd ef/5f:00:00:00:00:a0 succeeded
[    3.828213] ata1.00: ACPI cmd ef/10:03:00:00:00:a0 filtered out
[    3.829192] ata1.00: configured for UDMA/133
[    3.846283] ata1.00: configured for UDMA/133
[    3.846285] ata1: EH complete
[    3.894138] usb 4-6: configuration #1 chosen from 1 choice
[    3.895012] usbcore: registered new interface driver hiddev
[    3.895166] usb 1-1: USB disconnect, address 2
[    4.132580] usb 1-1: new low speed USB device using uhci_hcd and address 3
[    4.164099] ata2: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    4.166049] ata2.00: ACPI cmd ef/02:00:00:00:00:a0 succeeded
[    4.166052] ata2.00: ACPI cmd f5/00:00:00:00:00:a0 filtered out
[    4.166053] ata2.00: ACPI cmd ef/10:03:00:00:00:a0 filtered out
[    4.166248] ata2.00: ATA-7: SAMSUNG SSD RBX Series 64GB, PS105D14, max UDMA/100
[    4.166250] ata2.00: 125045424 sectors, multi 16: LBA48 
[    4.168005] ata2.00: ACPI cmd ef/02:00:00:00:00:a0 succeeded
[    4.168007] ata2.00: ACPI cmd f5/00:00:00:00:00:a0 filtered out
[    4.168009] ata2.00: ACPI cmd ef/10:03:00:00:00:a0 filtered out
[    4.168207] ata2.00: configured for UDMA/100
[    4.184580] ata2.00: configured for UDMA/100
[    4.184583] ata2: EH complete
[    4.184806] scsi 0:0:0:0: Direct-Access     ATA      HITACHI HTS72201 DCDZ PQ: 0 ANSI: 5
[    4.184896] scsi 1:0:0:0: Direct-Access     ATA      SAMSUNG SSD RBX  PS10 PQ: 0 ANSI: 5
[    4.184972] ohci1394 0000:15:00.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    4.237749] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[17]  MMIO=[f4401000-f44017ff]  Max Packet=[2048]  IR/IT contexts=[4/4]
[    4.249533] scsi 0:0:0:0: Attached scsi generic sg0 type 0
[    4.249557] scsi 1:0:0:0: Attached scsi generic sg1 type 0
[    4.271455] Driver 'sd' needs updating - please use bus_type methods
[    4.271510] sd 0:0:0:0: [sda] 312581808 512-byte hardware sectors (160042 MB)
[    4.271521] sd 0:0:0:0: [sda] Write Protect is off
[    4.271523] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    4.271540] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.271585] sd 0:0:0:0: [sda] 312581808 512-byte hardware sectors (160042 MB)
[    4.271600] sd 0:0:0:0: [sda] Write Protect is off
[    4.271602] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    4.271618] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.271620]  sda: sda1 sda2 sda3 sda4 < sda5 sda6 sda7 >
[    4.320307] sd 0:0:0:0: [sda] Attached SCSI disk
[    4.320347] sd 1:0:0:0: [sdb] 125045424 512-byte hardware sectors (64023 MB)
[    4.320358] sd 1:0:0:0: [sdb] Write Protect is off
[    4.320360] sd 1:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[    4.320378] sd 1:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.320417] sd 1:0:0:0: [sdb] 125045424 512-byte hardware sectors (64023 MB)
[    4.320427] sd 1:0:0:0: [sdb] Write Protect is off
[    4.320429] sd 1:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[    4.320446] sd 1:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.320448]  sdb: sdb1 sdb2
[    4.321660] sd 1:0:0:0: [sdb] Attached SCSI disk
[    4.362385] usb 1-1: configuration #1 chosen from 1 choice
[    4.604680] usb 2-1: new full speed USB device using uhci_hcd and address 4
[    4.775498] usb 2-1: configuration #1 chosen from 1 choice
[    5.016072] usb 2-2: new full speed USB device using uhci_hcd and address 5
[    5.182371] usb 2-2: configuration #1 chosen from 1 choice
[    5.424082] usb 8-4: new high speed USB device using ehci_hcd and address 2
[    5.512374] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[00016c00006a68d3]
[    5.634911] usb 8-4: configuration #1 chosen from 2 choices
[    5.708514] input: Microsoft Microsoft 3-Button Mouse with IntelliEye(TM) as /devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1:1.0/input/input2
[    5.708661] input,hidraw0: USB HID v1.10 Mouse [Microsoft Microsoft 3-Button Mouse with IntelliEye(TM)] on usb-0000:00:1a.0-1
[    5.708680] usbcore: registered new interface driver usbhid
[    5.708682] usbhid: v2.6:USB HID core driver
[    5.743954] PM: Starting manual resume from disk
[    5.743956] PM: Resume from partition 8:6
[    5.743957] PM: Checking hibernation image.
[    5.744134] PM: Resume from disk failed.
[    5.773692] kjournald starting.  Commit interval 5 seconds
[    5.773702] EXT3-fs: mounted filesystem with ordered data mode.
[   11.809916] udevd version 124 started
[   12.056085] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   12.144051] Linux agpgart interface v0.103
[   12.285126] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   12.326179] input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input3
[   12.352018] ACPI: Power Button (FF) [PWRF]
[   12.352069] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input4
[   12.352681] ACPI: Lid Switch [LID]
[   12.352730] input: Sleep Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input5
[   12.372516] ACPI: Sleep Button (CM) [SLPB]
[   12.372667] ACPI: WMI: Mapper loaded
[   12.390702] ACPI: \_SB_.PCI0.SATA.PRT1: found ejectable bay
[   12.390706] ACPI: \_SB_.PCI0.SATA.PRT1: Adding notify handler
[   12.404675] ACPI: Error installing bay notify handler
[   12.452706] acpi device:03: registered as cooling_device2
[   12.452898] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:02/input/input6
[   12.484525] ACPI: Video Device [VID] (multi-head: yes  rom: no  post: no)
[   12.486130] acpi device:0a: registered as cooling_device3
[   12.486296] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:08/device:09/input/input7
[   12.487677] ACPI: AC Adapter [AC] (on-line)
[   12.516518] ACPI: Video Device [VID1] (multi-head: yes  rom: no  post: no)
[   12.576090] ACPI: Battery Slot [BAT0] (battery present)
[   12.749004] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
[   12.765275] [fglrx] Maximum main memory to use for locked dma buffers: 2887 MBytes.
[   12.765900] [fglrx]   vendor: 1002 device: 9591 count: 1
[   12.766737] [fglrx] ioport: bar 1, base 0x2000, size: 0x100
[   12.766809] pci 0000:01:00.0: power state changed by ACPI to D0
[   12.766815] pci 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   12.766820] pci 0000:01:00.0: setting latency timer to 64
[   12.769531] [fglrx] PAT is enabled successfully!
[   12.769573] [fglrx] module loaded - fglrx 8.54.3 [Oct 10 2008] with 1 minors
[   12.819603] Bluetooth: Core ver 2.13
[   12.834357] NET: Registered protocol family 31
[   12.834359] Bluetooth: HCI device and connection manager initialized
[   12.834361] Bluetooth: HCI socket layer initialized
[   12.914770] Linux video capture interface: v2.00
[   12.940336] ricoh-mmc: Ricoh MMC Controller disabling driver
[   12.940338] ricoh-mmc: Copyright(c) Philip Langdale
[   12.940400] ricoh-mmc: Ricoh MMC controller found at 0000:15:00.3 [1180:0843] (rev 11)
[   12.940421] ricoh-mmc: Controller is now disabled.
[   13.068546] Bluetooth: Generic Bluetooth USB driver ver 0.3
[   13.068627] usbcore: registered new interface driver btusb
[   13.167723] usbcore: registered new interface driver usbserial
[   13.167735] usbserial: USB Serial support registered for generic
[   13.167812] usbcore: registered new interface driver usbserial_generic
[   13.167813] usbserial: USB Serial Driver core
[   13.215515] usbserial: USB Serial support registered for GSM modem (1-port)
[   13.215552] option 8-4:1.0: GSM modem (1-port) converter detected
[   13.215662] usb 8-4: GSM modem (1-port) converter now attached to ttyUSB0
[   13.215673] option 8-4:1.1: GSM modem (1-port) converter detected
[   13.215727] usb 8-4: GSM modem (1-port) converter now attached to ttyUSB1
[   13.215738] option 8-4:1.2: GSM modem (1-port) converter detected
[   13.215782] usb 8-4: GSM modem (1-port) converter now attached to ttyUSB2
[   13.215793] option 8-4:1.3: GSM modem (1-port) converter detected
[   13.215840] usb 8-4: GSM modem (1-port) converter now attached to ttyUSB3
[   13.215851] option 8-4:1.4: GSM modem (1-port) converter detected
[   13.215896] usb 8-4: GSM modem (1-port) converter now attached to ttyUSB4
[   13.215907] option 8-4:1.5: GSM modem (1-port) converter detected
[   13.215954] usb 8-4: GSM modem (1-port) converter now attached to ttyUSB5
[   13.215965] option 8-4:1.6: GSM modem (1-port) converter detected
[   13.216013] usb 8-4: GSM modem (1-port) converter now attached to ttyUSB6
[   13.216024] option 8-4:1.7: GSM modem (1-port) converter detected
[   13.216077] usb 8-4: GSM modem (1-port) converter now attached to ttyUSB7
[   13.216088] option 8-4:1.8: GSM modem (1-port) converter detected
[   13.216134] usb 8-4: GSM modem (1-port) converter now attached to ttyUSB8
[   13.216144] option 8-4:1.9: GSM modem (1-port) converter detected
[   13.216192] usb 8-4: GSM modem (1-port) converter now attached to ttyUSB9
[   13.216203] option 8-4:1.10: GSM modem (1-port) converter detected
[   13.216248] usb 8-4: GSM modem (1-port) converter now attached to ttyUSB10
[   13.216258] usbcore: registered new interface driver option
[   13.216260] option: USB Driver for GSM modems: v0.7.2
[   13.242137] Yenta: CardBus bridge found at 0000:15:00.0 [17aa:20c6]
[   13.290618] usbcore: registered new interface driver cdc_acm
[   13.290630] cdc_acm: v0.26:USB Abstract Control Model driver for USB modems and ISDN adapters
[   13.295162] sdhci: Secure Digital Host Controller Interface driver
[   13.295164] sdhci: Copyright(c) Pierre Ossman
[   13.297131] usbcore: registered new interface driver cdc_wdm
[   13.361969] Non-volatile memory driver v1.2
[   13.369293] Yenta: ISA IRQ mask 0x0cb8, PCI irq 16
[   13.369296] Socket status: 30000006
[   13.369299] pcmcia: parent PCI bridge I/O window: 0x6000 - 0x9fff
[   13.369313] cs: IO port probe 0x6000-0x9fff: clean.
[   13.369974] pcmcia: parent PCI bridge Memory window: 0xf4400000 - 0xf7ffffff
[   13.369985] pcmcia: parent PCI bridge Memory window: 0xf0000000 - 0xf3ffffff
[   13.370615] sdhci-pci 0000:15:00.2: SDHCI controller found [1180:0822] (rev 21)
[   13.370630] sdhci-pci 0000:15:00.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[   13.371637] sdhci-pci 0000:15:00.2: Will use DMA mode even though HW doesn't fully claim to support it.
[   13.373674] mmc0: SDHCI controller on PCI [0000:15:00.2] using DMA
[   13.412265] uvcvideo: Found UVC 1.00 device <unnamed> (17ef:4807)
[   13.417443] input: UVC Camera (17ef:4807) as /devices/pci0000:00/0000:00:1a.7/usb4/4-6/4-6:1.0/input/input8
[   13.464624] usbcore: registered new interface driver uvcvideo
[   13.464627] USB Video Class driver (v0.1.0)
[   13.477727] usbcore: registered new interface driver cdc_ether
[   13.524441] usbcore: registered new interface driver zaurus
[   13.581620] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, 1.3.27ks
[   13.581622] iwlagn: Copyright(c) 2003-2008 Intel Corporation
[   13.582424] iwlagn 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   13.582432] iwlagn 0000:03:00.0: setting latency timer to 64
[   13.582455] iwlagn: Detected Intel Wireless WiFi Link 5100AGN REV=0x54
[   13.612008] iwlagn: Tunable channels: 13 802.11bg, 24 802.11a channels
[   13.665266] iwlagn 0000:03:00.0: PCI INT A disabled
[   13.665588] phy0: Selected rate control algorithm 'iwl-agn-rs'
[   14.135788] Synaptics Touchpad, model: 1, fw: 7.0, id: 0x1c0b1, caps: 0xd04791/0xb00000
[   14.135792] serio: Synaptics pass-through port at isa0060/serio1/input0
[   14.180680] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input9
[   14.208180] thinkpad_acpi: ThinkPad ACPI Extras v0.21
[   14.208182] thinkpad_acpi: http://ibm-acpi.sf.net/
[   14.208183] thinkpad_acpi: ThinkPad BIOS 6FET43WW (1.13 ), EC 7VHT12WW-1.01
[   14.208185] thinkpad_acpi: Lenovo ThinkPad W500, model 406224U
[   14.209105] thinkpad_acpi: radio switch found; radios are enabled
[   14.209212] thinkpad_acpi: This ThinkPad has standard ACPI backlight brightness control, supported by the ACPI video driver
[   14.209214] thinkpad_acpi: Disabling thinkpad-acpi brightness events by default...
[   14.222559] Registered led device: tpacpi::thinklight
[   14.222594] Registered led device: tpacpi::power
[   14.222615] Registered led device: tpacpi:orange:batt
[   14.222636] Registered led device: tpacpi:green:batt
[   14.222659] Registered led device: tpacpi::dock_active
[   14.222680] Registered led device: tpacpi::bay_active
[   14.222702] Registered led device: tpacpi::dock_batt
[   14.222724] Registered led device: tpacpi::unknown_led
[   14.222745] Registered led device: tpacpi::standby
[   14.225822] thinkpad_acpi: Lenovo BIOS switched to ACPI backlight control mode
[   14.225824] thinkpad_acpi: standard ACPI backlight interface available, not loading native one...
[   14.226162] input: ThinkPad Extra Buttons as /devices/virtual/input/input10
[   14.388709] HDA Intel 0000:00:1b.0: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[   14.388727] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   14.493802] cs: IO port probe 0x100-0x3af: clean.
[   14.495518] cs: IO port probe 0x3e0-0x4ff: excluding 0x4d0-0x4d7
[   14.496231] cs: IO port probe 0x820-0x8ff: clean.
[   14.497197] cs: IO port probe 0xc00-0xcf7: clean.
[   14.497889] cs: IO port probe 0xa00-0xaff: clean.
[   14.806339] lp: driver loaded but no devices found
[   14.961465] Adding 997880k swap on /dev/sda6.  Priority:-1 extents:1 across:997880k
[   15.489765] EXT3 FS on sda7, internal journal
[   16.390967] type=1505 audit(1236107236.744:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=4696
[   16.428071] type=1505 audit(1236107236.783:3): operation="profile_load" name="/usr/bin/freshclam" name2="default" pid=4701
[   16.533574] type=1505 audit(1236107236.887:4): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=4705
[   16.533705] type=1505 audit(1236107236.887:5): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=4705
[   16.670570] ip_tables: (C) 2000-2006 Netfilter Core Team
[   17.136304] NET: Registered protocol family 10
[   17.136662] lo: Disabled Privacy Extensions
[   17.137070] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   17.777789] ACPI: \_SB_.PCI0.SATA.PRT1: found ejectable bay
[   17.777794] ACPI: \_SB_.PCI0.SATA.PRT1: Adding notify handler
[   17.777816] ACPI: Error installing bay notify handler
[   18.522956] warning: `avahi-daemon' uses 32-bit capabilities (legacy support in use)
[   18.706860] apm: BIOS not found.
[   19.577201] ppdev: user-space parallel port driver
[   20.158794] IBM TrackPoint firmware: 0x0e, buttons: 3/3
[   20.447132] input: TPPS/2 IBM TrackPoint as /devices/platform/i8042/serio1/serio2/input/input11
[   20.786413] vboxdrv: Trying to deactivate the NMI watchdog permanently...
[   20.786418] vboxdrv: Successfully done.
[   20.786419] vboxdrv: Found 2 processor cores.
[   20.786512] vboxdrv: fAsync=0 offMin=0x20d offMax=0xc98
[   20.786515] vboxdrv: TSC mode is 'synchronous', kernel timer mode is 'normal'.
[   20.786517] vboxdrv: Successfully loaded version 2.0.4_OSE (interface 0x00090000).
[   23.219070] Bluetooth: L2CAP ver 2.11
[   23.219082] Bluetooth: L2CAP socket layer initialized
[   23.251438] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   23.251449] Bluetooth: BNEP filters: protocol multicast
[   23.310539] Bridge firewalling registered
[   23.358737] Bluetooth: SCO (Voice Link) ver 0.6
[   23.358747] Bluetooth: SCO socket layer initialized
[   23.376819] Bluetooth: RFCOMM socket layer initialized
[   23.377175] Bluetooth: RFCOMM TTY layer initialized
[   23.377184] Bluetooth: RFCOMM ver 1.10
[   27.608932] iwlagn 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   27.609052] iwlagn 0000:03:00.0: restoring config space at offset 0x1 (was 0x100102, writing 0x100106)
[   27.609290] firmware: requesting iwlwifi-5000-1.ucode
[   30.198700] Registered led device: iwl-phy0:radio
[   30.198862] Registered led device: iwl-phy0:assoc
[   30.198977] Registered led device: iwl-phy0:RX
[   30.199086] Registered led device: iwl-phy0:TX
[   30.240767] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   30.348631] NET: Registered protocol family 17
[   31.949432] wlan0: authenticate with AP 00:14:c1:19:12:6c
[   31.951361] wlan0: authenticated
[   31.951373] wlan0: associate with AP 00:14:c1:19:12:6c
[   31.953777] wlan0: RX AssocResp from 00:14:c1:19:12:6c (capab=0x401 status=0 aid=1)
[   31.953790] wlan0: associated
[   31.958643] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   31.961612] wlan0: disassociating by local choice (reason=3)
[   42.552583] wlan0: no IPv6 routers present
[   53.469071] wlan0: associate with AP 00:14:c1:19:12:6c
[   53.471671] wlan0: RX ReassocResp from 00:14:c1:19:12:6c (capab=0x401 status=0 aid=1)
[   53.471685] wlan0: associated
[   53.478469] wlan0: disassociating by local choice (reason=3)
[   68.242678] CPU0 attaching NULL sched-domain.
[   68.242696] CPU1 attaching NULL sched-domain.
[   68.249404] CPU0 attaching sched-domain:
[   68.249415]  domain 0: span 0-1 level MC
[   68.249421]   groups: 0 1
[   68.249434] CPU1 attaching sched-domain:
[   68.249439]  domain 0: span 0-1 level MC
[   68.249444]   groups: 1 0
[   72.105376] wlan0: associate with AP 00:14:c1:19:12:6c
[   72.108357] wlan0: RX ReassocResp from 00:14:c1:19:12:6c (capab=0x401 status=0 aid=1)
[   72.108368] wlan0: associated
[   72.114176] wlan0: authenticate with AP 00:14:c1:19:12:6c
[   72.116171] wlan0: authenticated
[   72.116182] wlan0: associate with AP 00:14:c1:19:12:6c
[   72.118386] wlan0: RX ReassocResp from 00:14:c1:19:12:6c (capab=0x401 status=0 aid=1)
[   72.118395] wlan0: associated
[  137.616706] type=1503 audit(1236107357.972:6): operation="inode_permission" requested_mask="w::" denied_mask="w::" fsuid=0 name="/dev/ttyUSB0" pid=8849 profile="/usr/sbin/cupsd"
[  137.619649] type=1503 audit(1236107357.972:7): operation="inode_permission" requested_mask="w::" denied_mask="w::" fsuid=0 name="/dev/ttyUSB1" pid=8849 profile="/usr/sbin/cupsd"
[  137.622538] type=1503 audit(1236107357.976:8): operation="inode_permission" requested_mask="w::" denied_mask="w::" fsuid=0 name="/dev/ttyUSB2" pid=8849 profile="/usr/sbin/cupsd"
[  137.625487] type=1503 audit(1236107357.980:9): operation="inode_permission" requested_mask="w::" denied_mask="w::" fsuid=0 name="/dev/ttyUSB3" pid=8849 profile="/usr/sbin/cupsd"
[  137.628098] type=1503 audit(1236107357.980:10): operation="inode_permission" requested_mask="w::" denied_mask="w::" fsuid=0 name="/dev/ttyUSB4" pid=8849 profile="/usr/sbin/cupsd"
[  137.628137] type=1503 audit(1236107357.980:11): operation="inode_permission" requested_mask="w::" denied_mask="w::" fsuid=0 name="/dev/ttyUSB5" pid=8849 profile="/usr/sbin/cupsd"
[  137.628174] type=1503 audit(1236107357.980:12): operation="inode_permission" requested_mask="w::" denied_mask="w::" fsuid=0 name="/dev/ttyUSB6" pid=8849 profile="/usr/sbin/cupsd"
[  137.628212] type=1503 audit(1236107357.980:13): operation="inode_permission" requested_mask="w::" denied_mask="w::" fsuid=0 name="/dev/ttyUSB7" pid=8849 profile="/usr/sbin/cupsd"
[  137.628249] type=1503 audit(1236107357.980:14): operation="inode_permission" requested_mask="w::" denied_mask="w::" fsuid=0 name="/dev/ttyUSB8" pid=8849 profile="/usr/sbin/cupsd"
[  137.628286] type=1503 audit(1236107357.980:15): operation="inode_permission" requested_mask="w::" denied_mask="w::" fsuid=0 name="/dev/ttyUSB9" pid=8849 profile="/usr/sbin/cupsd"

```

---

### Post by Bashar &quot; on 2009-03-03
no lines pops when i press Fn+F7 

and here is dmesg output:
```

[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.27-11-generic (buildd@rothera) (gcc version 4.3.2 (Ubuntu 4.3.2-1ubuntu11) ) #1 SMP Thu Jan 29 19:24:39 UTC 2009 (Ubuntu 2.6.27-11.27-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009ac00 (usable)
[    0.000000]  BIOS-e820: 000000000009ac00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000d6000 - 00000000000d8000 (reserved)
[    0.000000]  BIOS-e820: 00000000000dc000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 00000000bf8a1000 (usable)
[    0.000000]  BIOS-e820: 00000000bf8a1000 - 00000000bf8a7000 (reserved)
[    0.000000]  BIOS-e820: 00000000bf8a7000 - 00000000bf9b7000 (usable)
[    0.000000]  BIOS-e820: 00000000bf9b7000 - 00000000bfa0f000 (reserved)
[    0.000000]  BIOS-e820: 00000000bfa0f000 - 00000000bfac7000 (usable)
[    0.000000]  BIOS-e820: 00000000bfac7000 - 00000000bfad2000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000bfad2000 - 00000000bfad5000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000bfad5000 - 00000000bfad9000 (reserved)
[    0.000000]  BIOS-e820: 00000000bfad9000 - 00000000bfadd000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000bfadd000 - 00000000bfae0000 (reserved)
[    0.000000]  BIOS-e820: 00000000bfae0000 - 00000000bfb07000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000bfb07000 - 00000000bfb08000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000bfb08000 - 00000000bfd0f000 (reserved)
[    0.000000]  BIOS-e820: 00000000bfd0f000 - 00000000bfd9f000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000bfd9f000 - 00000000bfdff000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000bfdff000 - 00000000bfe00000 (usable)
[    0.000000]  BIOS-e820: 00000000bfe00000 - 00000000c0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed00000 - 00000000fed00400 (reserved)
[    0.000000]  BIOS-e820: 00000000fed10000 - 00000000fed14000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed18000 - 00000000fed1a000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed1c000 - 00000000fed90000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000ff800000 - 0000000100000000 (reserved)
[    0.000000]  BIOS-e820: 0000000100000000 - 000000013c000000 (usable)
[    0.000000] DMI present.
[    0.000000] last_pfn = 0xbfe00 max_arch_pfn = 0x100000
[    0.000000] kernel direct mapping tables up to 38000000 @ 7000-c000
[    0.000000] RAMDISK: 3782b000 - 37fefe0c
[    0.000000] ACPI: RSDP 000F6550, 0024 (r2 LENOVO)
[    0.000000] ACPI: XSDT BFD6A4DE, 0094 (r1 LENOVO TP-6F        1130  LTP        0)
[    0.000000] ACPI: FACP BFD6A600, 00F4 (r3 LENOVO TP-6F        1130 LNVO        1)
[    0.000000] ACPI: DSDT BFD6A9DB, F190 (r1 LENOVO TP-6F        1130 MSFT  3000000)
[    0.000000] ACPI: FACS BFD8E000, 0040
[    0.000000] ACPI: SSDT BFD6A7B4, 0227 (r1 LENOVO TP-6F        1130 MSFT  3000000)
[    0.000000] ACPI: ECDT BFD79B6B, 0052 (r1 LENOVO TP-6F        1130 LNVO        1)
[    0.000000] ACPI: APIC BFD79BBD, 0078 (r1 LENOVO TP-6F        1130 LNVO        1)
[    0.000000] ACPI: MCFG BFD79C35, 003C (r1 LENOVO TP-6F        1130 LNVO        1)
[    0.000000] ACPI: HPET BFD79C71, 0038 (r1 LENOVO TP-6F        1130 LNVO        1)
[    0.000000] ACPI: SLIC BFD79DC2, 0176 (r1 LENOVO TP-6F        1130  LTP        0)
[    0.000000] ACPI: BOOT BFD79F38, 0028 (r1 LENOVO TP-6F        1130  LTP        1)
[    0.000000] ACPI: ASF! BFD79F60, 00A0 (r16 LENOVO TP-6F        1130 PTL         1)
[    0.000000] ACPI: SSDT BFD8D213, 054F (r1 LENOVO TP-6F        1130 INTL 20050513)
[    0.000000] ACPI: TCPA BFB07000, 0032 (r0                        0             0)
[    0.000000] ACPI: SSDT BFAD4000, 0655 (r1  PmRef    CpuPm     3000 INTL 20050624)
[    0.000000] ACPI: SSDT BFAD3000, 0274 (r1  PmRef  Cpu0Tst     3000 INTL 20050624)
[    0.000000] ACPI: SSDT BFAD2000, 0242 (r1  PmRef    ApTst     3000 INTL 20050624)
[    0.000000] 2174MB HIGHMEM available.
[    0.000000] 896MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 38000000
[    0.000000]   low ram: 00000000 - 38000000
[    0.000000]   bootmap 00008000 - 0000f000
[    0.000000] (9 early reservations) ==> bootmem [0000000000 - 0038000000]
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000]   #1 [0000001000 - 0000002000]    EX TRAMPOLINE ==> [0000001000 - 0000002000]
[    0.000000]   #2 [0000006000 - 0000007000]       TRAMPOLINE ==> [0000006000 - 0000007000]
[    0.000000]   #3 [0000100000 - 00005c29e0]    TEXT DATA BSS ==> [0000100000 - 00005c29e0]
[    0.000000]   #4 [003782b000 - 0037fefe0c]          RAMDISK ==> [003782b000 - 0037fefe0c]
[    0.000000]   #5 [00005c3000 - 00005c6000]    INIT_PG_TABLE ==> [00005c3000 - 00005c6000]
[    0.000000]   #6 [000009ac00 - 0000100000]    BIOS reserved ==> [000009ac00 - 0000100000]
[    0.000000]   #7 [0000007000 - 0000008000]          PGTABLE ==> [0000007000 - 0000008000]
[    0.000000]   #8 [0000008000 - 000000f000]          BOOTMAP ==> [0000008000 - 000000f000]
[    0.000000] found SMP MP-table at [c00f6590] 000f6590
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000000 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x00038000
[    0.000000]   HighMem  0x00038000 -> 0x000bfe00
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[5] active PFN ranges
[    0.000000]     0: 0x00000000 -> 0x0000009a
[    0.000000]     0: 0x00000100 -> 0x000bf8a1
[    0.000000]     0: 0x000bf8a7 -> 0x000bf9b7
[    0.000000]     0: 0x000bfa0f -> 0x000bfac7
[    0.000000]     0: 0x000bfdff -> 0x000bfe00
[    0.000000] On node 0 totalpages: 784900
[    0.000000] free_area_init_node: node 0, pgdat c048c680, node_mem_map c1000000
[    0.000000]   DMA zone: 3958 pages, LIFO batch:0
[    0.000000]   Normal zone: 223300 pages, LIFO batch:31
[    0.000000]   HighMem zone: 550734 pages, LIFO batch:31
[    0.000000] ACPI: PM-Timer IO Port: 0x1008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x02] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x03] disabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 1, version 32, address 0xfec00000, GSI 0-23
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
[    0.000000] PM: Registered nosave memory: 000000000009a000 - 000000000009b000
[    0.000000] PM: Registered nosave memory: 000000000009b000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000d6000
[    0.000000] PM: Registered nosave memory: 00000000000d6000 - 00000000000d8000
[    0.000000] PM: Registered nosave memory: 00000000000d8000 - 00000000000dc000
[    0.000000] PM: Registered nosave memory: 00000000000dc000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at c2000000 (gap: c0000000:20000000)
[    0.000000] PERCPU: Allocating 41628 bytes of per cpu data
[    0.000000] NR_CPUS: 64, nr_cpu_ids: 4, nr_node_ids 1
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 777992
[    0.000000] Kernel command line: root=UUID=b11aac09-e8e0-4fd4-8e6e-05fef00f0182 ro quiet splash 
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] Extended CMOS year: 2000
[    0.000000] TSC: PIT calibration confirmed by PMTIMER.
[    0.000000] TSC: using PMTIMER calibration value
[    0.000000] Detected 2792.984 MHz processor.
[    0.004000] Console: colour VGA+ 80x25
[    0.004000] console [tty0] enabled
[    0.004000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.004000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.004000] Memory: 3097140k/3143680k available (2576k kernel code, 41556k reserved, 1165k data, 424k init, 2222504k highmem)
[    0.004000] virtual kernel memory layout:
[    0.004000]     fixmap  : 0xffc77000 - 0xfffff000   (3616 kB)
[    0.004000]     pkmap   : 0xff400000 - 0xff800000   (4096 kB)
[    0.004000]     vmalloc : 0xf8800000 - 0xff3fe000   ( 107 MB)
[    0.004000]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
[    0.004000]       .init : 0xc04ad000 - 0xc0517000   ( 424 kB)
[    0.004000]       .data : 0xc03840da - 0xc04a7680   (1165 kB)
[    0.004000]       .text : 0xc0100000 - 0xc03840da   (2576 kB)
[    0.004000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.004000] CPA: page pool initialized 1 of 1 pages preallocated
[    0.004000] SLUB: Genslabs=12, HWalign=64, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
[    0.004000] hpet clockevent registered
[    0.004000] Calibrating delay loop (skipped), value calculated using timer frequency.. 5585.96 BogoMIPS (lpj=11171936)
[    0.004000] Security Framework initialized
[    0.004000] SELinux:  Disabled at boot.
[    0.004000] AppArmor: AppArmor initialized
[    0.004000] Mount-cache hash table entries: 512
[    0.004000] Initializing cgroup subsys ns
[    0.004000] Initializing cgroup subsys cpuacct
[    0.004000] Initializing cgroup subsys memory
[    0.004000] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.004000] CPU: L2 cache: 6144K
[    0.004000] CPU: Physical Processor ID: 0
[    0.004000] CPU: Processor Core ID: 0
[    0.004000] using mwait in idle threads.
[    0.004000] Checking 'hlt' instruction... OK.
[    0.017456] ACPI: Core revision 20080609
[    0.022513] ACPI: Checking initramfs for custom DSDT
[    0.272220] ENABLING IO-APIC IRQs
[    0.276170] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.315853] CPU0: Intel(R) Core(TM)2 Duo CPU     T9600  @ 2.80GHz stepping 06
[    0.316019] Booting processor 1/1 ip 6000
[    0.004000] Initializing CPU#1
[    0.004000] Calibrating delay using timer specific routine.. 5585.87 BogoMIPS (lpj=11171744)
[    0.004000] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.004000] CPU: L2 cache: 6144K
[    0.004000] CPU: Physical Processor ID: 0
[    0.004000] CPU: Processor Core ID: 1
[    0.400827] CPU1: Intel(R) Core(TM)2 Duo CPU     T9600  @ 2.80GHz stepping 06
[    0.400840] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
[    0.404039] Brought up 2 CPUs
[    0.404041] Total of 2 processors activated (11171.84 BogoMIPS).
[    0.404059] CPU0 attaching sched-domain:
[    0.404061]  domain 0: span 0-1 level MC
[    0.404063]   groups: 0 1
[    0.404067] CPU1 attaching sched-domain:
[    0.404069]  domain 0: span 0-1 level MC
[    0.404070]   groups: 1 0
[    0.404128] net_namespace: 840 bytes
[    0.404128] Booting paravirtualized kernel on bare hardware
[    0.404213] Time: 22:07:00  Date: 03/03/09
[    0.404231] NET: Registered protocol family 16
[    0.404245] EISA bus registered
[    0.404245] ACPI FADT declares the system doesn't support PCIe ASPM, so disable it
[    0.404245] ACPI: bus type pci registered
[    0.404245] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 63
[    0.404245] PCI: MCFG area at e0000000 reserved in E820
[    0.404245] PCI: Using MMCONFIG for extended config space
[    0.404245] PCI: Using configuration type 1 for base access
[    0.405254] ACPI: EC: EC description table is found, configuring boot EC
[    0.413746] ACPI: BIOS _OSI(Linux) query ignored
[    0.413748] ACPI: If "acpi_osi=Linux" works better, please notify [email]linux-acpi@vger.kernel.org[/email]
[    0.412042] ACPI: EC: non-query interrupt received, switching to interrupt mode
[    0.426059] ACPI: Interpreter enabled
[    0.426062] ACPI: (supports S0 S3 S4 S5)
[    0.426068] ACPI: Using IOAPIC for interrupt routing
[    0.448445] ACPI: EC: GPE = 0x11, I/O: command/status = 0x66, data = 0x62
[    0.448445] ACPI: EC: driver started in interrupt mode
[    0.448445] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.448445] pci 0000:00:01.0: PME# supported from D0 D3hot D3cold
[    0.448445] pci 0000:00:01.0: PME# disabled
[    0.448445] PCI: 0000:00:03.0 reg 10 64bit mmio: [fc226800, fc22680f]
[    0.448445] pci 0000:00:03.0: PME# supported from D0 D3hot D3cold
[    0.448445] pci 0000:00:03.0: PME# disabled
[    0.448445] PCI: 0000:00:19.0 reg 10 32bit mmio: [fc200000, fc21ffff]
[    0.448445] PCI: 0000:00:19.0 reg 14 32bit mmio: [fc225000, fc225fff]
[    0.448445] PCI: 0000:00:19.0 reg 18 io port: [1840, 185f]
[    0.448445] pci 0000:00:19.0: PME# supported from D0 D3hot D3cold
[    0.448445] pci 0000:00:19.0: PME# disabled
[    0.448445] PCI: 0000:00:1a.0 reg 20 io port: [1860, 187f]
[    0.448445] PCI: 0000:00:1a.1 reg 20 io port: [1880, 189f]
[    0.448486] PCI: 0000:00:1a.2 reg 20 io port: [18a0, 18bf]
[    0.448562] PCI: 0000:00:1a.7 reg 10 32bit mmio: [fc226c00, fc226fff]
[    0.448614] pci 0000:00:1a.7: PME# supported from D0 D3hot D3cold
[    0.448619] pci 0000:00:1a.7: PME# disabled
[    0.448660] PCI: 0000:00:1b.0 reg 10 64bit mmio: [fc220000, fc223fff]
[    0.448707] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    0.448711] pci 0000:00:1b.0: PME# disabled
[    0.448775] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.448779] pci 0000:00:1c.0: PME# disabled
[    0.448841] pci 0000:00:1c.1: PME# supported from D0 D3hot D3cold
[    0.448845] pci 0000:00:1c.1: PME# disabled
[    0.448908] pci 0000:00:1c.2: PME# supported from D0 D3hot D3cold
[    0.448912] pci 0000:00:1c.2: PME# disabled
[    0.448974] pci 0000:00:1c.3: PME# supported from D0 D3hot D3cold
[    0.448978] pci 0000:00:1c.3: PME# disabled
[    0.449041] pci 0000:00:1c.4: PME# supported from D0 D3hot D3cold
[    0.449045] pci 0000:00:1c.4: PME# disabled
[    0.449100] PCI: 0000:00:1d.0 reg 20 io port: [18c0, 18df]
[    0.449175] PCI: 0000:00:1d.1 reg 20 io port: [18e0, 18ff]
[    0.449249] PCI: 0000:00:1d.2 reg 20 io port: [1c00, 1c1f]
[    0.449325] PCI: 0000:00:1d.7 reg 10 32bit mmio: [fc227000, fc2273ff]
[    0.449378] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
[    0.449383] pci 0000:00:1d.7: PME# disabled
[    0.449583] PCI: 0000:00:1f.2 reg 10 io port: [1c40, 1c47]
[    0.449590] PCI: 0000:00:1f.2 reg 14 io port: [1834, 1837]
[    0.449596] PCI: 0000:00:1f.2 reg 18 io port: [1838, 183f]
[    0.449603] PCI: 0000:00:1f.2 reg 1c io port: [1830, 1833]
[    0.449610] PCI: 0000:00:1f.2 reg 20 io port: [1c20, 1c3f]
[    0.449616] PCI: 0000:00:1f.2 reg 24 32bit mmio: [fc226000, fc2267ff]
[    0.449648] pci 0000:00:1f.2: PME# supported from D3hot
[    0.449652] pci 0000:00:1f.2: PME# disabled
[    0.449675] PCI: 0000:00:1f.3 reg 10 64bit mmio: [fc227400, fc2274ff]
[    0.449692] PCI: 0000:00:1f.3 reg 20 io port: [1c60, 1c7f]
[    0.449745] PCI: 0000:01:00.0 reg 10 32bit mmio: [d0000000, dfffffff]
[    0.449752] PCI: 0000:01:00.0 reg 14 io port: [2000, 20ff]
[    0.449759] PCI: 0000:01:00.0 reg 18 32bit mmio: [cfff0000, cfffffff]
[    0.449781] PCI: 0000:01:00.0 reg 30 32bit mmio: [0, 1ffff]
[    0.449800] pci 0000:01:00.0: supports D1
[    0.449801] pci 0000:01:00.0: supports D2
[    0.449845] PCI: bridge 0000:00:01.0 io port: [2000, 2fff]
[    0.449848] PCI: bridge 0000:00:01.0 32bit mmio: [cff00000, cfffffff]
[    0.449851] PCI: bridge 0000:00:01.0 64bit mmio pref: [d0000000, dfffffff]
[    0.449996] PCI: 0000:03:00.0 reg 10 64bit mmio: [f4200000, f4201fff]
[    0.450089] pci 0000:03:00.0: PME# supported from D0 D3hot D3cold
[    0.450096] pci 0000:03:00.0: PME# disabled
[    0.450144] PCI: bridge 0000:00:1c.1 32bit mmio: [f4200000, f42fffff]
[    0.450218] PCI: 0000:04:00.0 reg 10 32bit mmio: [f4300000, f43003ff]
[    0.450238] PCI: 0000:04:00.0 reg 18 io port: [3000, 30ff]
[    0.450278] PCI: 0000:04:00.0 reg 30 32bit mmio: [0, ffff]
[    0.450358] PCI: bridge 0000:00:1c.2 io port: [3000, 3fff]
[    0.450362] PCI: bridge 0000:00:1c.2 32bit mmio: [f4300000, f43fffff]
[    0.450420] PCI: bridge 0000:00:1c.3 io port: [4000, 4fff]
[    0.450424] PCI: bridge 0000:00:1c.3 32bit mmio: [f8000000, f9ffffff]
[    0.450431] PCI: bridge 0000:00:1c.3 64bit mmio pref: [f4000000, f40fffff]
[    0.450484] PCI: bridge 0000:00:1c.4 io port: [5000, 5fff]
[    0.450488] PCI: bridge 0000:00:1c.4 32bit mmio: [fa000000, fbffffff]
[    0.450495] PCI: bridge 0000:00:1c.4 64bit mmio pref: [f4100000, f41fffff]
[    0.450542] PCI: 0000:15:00.0 reg 10 32bit mmio: [f4400000, f4400fff]
[    0.450561] pci 0000:15:00.0: supports D1
[    0.450563] pci 0000:15:00.0: supports D2
[    0.450564] pci 0000:15:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.450569] pci 0000:15:00.0: PME# disabled
[    0.450608] PCI: 0000:15:00.1 reg 10 32bit mmio: [f4401000, f44017ff]
[    0.450670] pci 0000:15:00.1: supports D1
[    0.450671] pci 0000:15:00.1: supports D2
[    0.450672] pci 0000:15:00.1: PME# supported from D0 D1 D2 D3hot D3cold
[    0.450677] pci 0000:15:00.1: PME# disabled
[    0.450717] PCI: 0000:15:00.2 reg 10 32bit mmio: [f4401800, f44018ff]
[    0.450779] pci 0000:15:00.2: supports D1
[    0.450780] pci 0000:15:00.2: supports D2
[    0.450781] pci 0000:15:00.2: PME# supported from D0 D1 D2 D3hot D3cold
[    0.450786] pci 0000:15:00.2: PME# disabled
[    0.450825] PCI: 0000:15:00.3 reg 10 32bit mmio: [f4401c00, f4401cff]
[    0.450887] pci 0000:15:00.3: supports D1
[    0.450888] pci 0000:15:00.3: supports D2
[    0.450890] pci 0000:15:00.3: PME# supported from D0 D1 D2 D3hot D3cold
[    0.450895] pci 0000:15:00.3: PME# disabled
[    0.450934] PCI: 0000:15:00.4 reg 10 32bit mmio: [f4402000, f44020ff]
[    0.450995] pci 0000:15:00.4: supports D1
[    0.450996] pci 0000:15:00.4: supports D2
[    0.450998] pci 0000:15:00.4: PME# supported from D0 D1 D2 D3hot D3cold
[    0.451003] pci 0000:15:00.4: PME# disabled
[    0.451042] PCI: 0000:15:00.5 reg 10 32bit mmio: [f4402400, f44024ff]
[    0.451104] pci 0000:15:00.5: supports D1
[    0.451105] pci 0000:15:00.5: supports D2
[    0.451106] pci 0000:15:00.5: PME# supported from D0 D1 D2 D3hot D3cold
[    0.451111] pci 0000:15:00.5: PME# disabled
[    0.451174] pci 0000:00:1e.0: transparent bridge
[    0.451178] PCI: bridge 0000:00:1e.0 io port: [6000, 9fff]
[    0.451182] PCI: bridge 0000:00:1e.0 32bit mmio: [f4400000, f7ffffff]
[    0.451189] PCI: bridge 0000:00:1e.0 64bit mmio pref: [f0000000, f3ffffff]
[    0.451246] bus 00 -> node 0
[    0.451252] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.452246] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.AGP_._PRT]
[    0.452366] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.EXP0._PRT]
[    0.452490] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.EXP1._PRT]
[    0.452614] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.EXP2._PRT]
[    0.452737] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.EXP3._PRT]
[    0.452863] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.EXP4._PRT]
[    0.452988] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCI1._PRT]
[    0.456171] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 9 10 *11)
[    0.456370] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 9 10 *11)
[    0.456567] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 9 10 *11)
[    0.456764] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 9 10 *11)
[    0.456963] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 9 10 *11)
[    0.457160] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 9 10 *11)
[    0.457357] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 9 10 *11)
[    0.457553] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 9 10 *11)
[    0.457648] ACPI: Power Resource [PUBS] (on)
[    0.457648] Linux Plug and Play Support v0.97 (c) Adam Belay
[    0.457648] pnp: PnP ACPI init
[    0.457648] ACPI: bus type pnp registered
[    0.472523] pnp: PnP ACPI: found 10 devices
[    0.472525] ACPI: ACPI bus type pnp unregistered
[    0.472527] PnPBIOS: Disabled by ACPI PNP
[    0.472769] PCI: Using ACPI for IRQ routing
[    0.476044] NET: Registered protocol family 8
[    0.476046] NET: Registered protocol family 20
[    0.476063] NetLabel: Initializing
[    0.476063] NetLabel:  domain hash size = 128
[    0.476063] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.476063] NetLabel:  unlabeled traffic allowed by default
[    0.476063] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0
[    0.476063] hpet0: 4 64-bit timers, 14318180 Hz
[    0.477686] tracer: 772 pages allocated for 65536 entries of 48 bytes
[    0.477688]    actual entries 65620
[    0.477748] AppArmor: AppArmor Filesystem Enabled
[    0.477772] ACPI: RTC can wake from S4
[    0.480866] system 00:00: iomem range 0x0-0x9ffff could not be reserved
[    0.480868] system 00:00: iomem range 0xc0000-0xc3fff could not be reserved
[    0.480870] system 00:00: iomem range 0xc4000-0xc7fff could not be reserved
[    0.480872] system 00:00: iomem range 0xc8000-0xcbfff could not be reserved
[    0.480874] system 00:00: iomem range 0xcc000-0xcffff could not be reserved
[    0.480876] system 00:00: iomem range 0xd0000-0xd3fff could not be reserved
[    0.480878] system 00:00: iomem range 0xd4000-0xd7fff could not be reserved
[    0.480880] system 00:00: iomem range 0xdc000-0xdffff could not be reserved
[    0.480882] system 00:00: iomem range 0xe0000-0xe3fff could not be reserved
[    0.480884] system 00:00: iomem range 0xe4000-0xe7fff could not be reserved
[    0.480886] system 00:00: iomem range 0xe8000-0xebfff could not be reserved
[    0.480888] system 00:00: iomem range 0xec000-0xeffff could not be reserved
[    0.480891] system 00:00: iomem range 0xf0000-0xfffff could not be reserved
[    0.480893] system 00:00: iomem range 0x100000-0xbfffffff could not be reserved
[    0.480895] system 00:00: iomem range 0xfec00000-0xfed3ffff could not be reserved
[    0.480897] system 00:00: iomem range 0xfed4c000-0xffffffff could not be reserved
[    0.480903] system 00:02: ioport range 0x164e-0x164f has been reserved
[    0.480905] system 00:02: ioport range 0x1000-0x107f has been reserved
[    0.480907] system 00:02: ioport range 0x1180-0x11ff has been reserved
[    0.480909] system 00:02: ioport range 0x800-0x80f has been reserved
[    0.480911] system 00:02: ioport range 0x15e0-0x15ef has been reserved
[    0.480915] system 00:02: ioport range 0x1600-0x1641 has been reserved
[    0.480917] system 00:02: ioport range 0x1600-0x161b has been reserved
[    0.480919] system 00:02: iomem range 0xe0000000-0xefffffff could not be reserved
[    0.480921] system 00:02: iomem range 0xfed1c000-0xfed1ffff could not be reserved
[    0.480924] system 00:02: iomem range 0xfed10000-0xfed13fff could not be reserved
[    0.480926] system 00:02: iomem range 0xfed18000-0xfed18fff could not be reserved
[    0.480928] system 00:02: iomem range 0xfed19000-0xfed19fff could not be reserved
[    0.480930] system 00:02: iomem range 0xfed45000-0xfed4bfff could not be reserved
[    0.500860] Switched to high resolution mode on CPU 1
[    0.504031] Switched to high resolution mode on CPU 0
[    0.515822] pci 0000:00:01.0: PCI bridge, secondary bus 0000:01
[    0.515824] pci 0000:00:01.0:   IO window: 0x2000-0x2fff
[    0.515827] pci 0000:00:01.0:   MEM window: 0xcff00000-0xcfffffff
[    0.515830] pci 0000:00:01.0:   PREFETCH window: 0x000000d0000000-0x000000dfffffff
[    0.515833] pci 0000:00:1c.0: PCI bridge, secondary bus 0000:02
[    0.515835] pci 0000:00:1c.0:   IO window: disabled
[    0.515840] pci 0000:00:1c.0:   MEM window: disabled
[    0.515844] pci 0000:00:1c.0:   PREFETCH window: disabled
[    0.515851] pci 0000:00:1c.1: PCI bridge, secondary bus 0000:03
[    0.515852] pci 0000:00:1c.1:   IO window: disabled
[    0.515857] pci 0000:00:1c.1:   MEM window: 0xf4200000-0xf42fffff
[    0.515861] pci 0000:00:1c.1:   PREFETCH window: disabled
[    0.515868] pci 0000:00:1c.2: PCI bridge, secondary bus 0000:04
[    0.515871] pci 0000:00:1c.2:   IO window: 0x3000-0x3fff
[    0.515876] pci 0000:00:1c.2:   MEM window: 0xf4300000-0xf43fffff
[    0.515880] pci 0000:00:1c.2:   PREFETCH window: 0x000000c2000000-0x000000c20fffff
[    0.515887] pci 0000:00:1c.3: PCI bridge, secondary bus 0000:05
[    0.515890] pci 0000:00:1c.3:   IO window: 0x4000-0x4fff
[    0.515895] pci 0000:00:1c.3:   MEM window: 0xf8000000-0xf9ffffff
[    0.515899] pci 0000:00:1c.3:   PREFETCH window: 0x000000f4000000-0x000000f40fffff
[    0.515906] pci 0000:00:1c.4: PCI bridge, secondary bus 0000:0d
[    0.515909] pci 0000:00:1c.4:   IO window: 0x5000-0x5fff
[    0.515914] pci 0000:00:1c.4:   MEM window: 0xfa000000-0xfbffffff
[    0.515918] pci 0000:00:1c.4:   PREFETCH window: 0x000000f4100000-0x000000f41fffff
[    0.515927] pci 0000:15:00.0: CardBus bridge, secondary bus 0000:16
[    0.515928] pci 0000:15:00.0:   IO window: 0x006000-0x0060ff
[    0.515933] pci 0000:15:00.0:   IO window: 0x006400-0x0064ff
[    0.515938] pci 0000:15:00.0:   PREFETCH window: 0xf0000000-0xf3ffffff
[    0.515943] pci 0000:15:00.0:   MEM window: 0xc4000000-0xc7ffffff
[    0.515948] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:15
[    0.515951] pci 0000:00:1e.0:   IO window: 0x6000-0x9fff
[    0.515956] pci 0000:00:1e.0:   MEM window: 0xf4400000-0xf7ffffff
[    0.515960] pci 0000:00:1e.0:   PREFETCH window: 0x000000f0000000-0x000000f3ffffff
[    0.515972] pci 0000:00:01.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.515975] pci 0000:00:01.0: setting latency timer to 64
[    0.515982] pci 0000:00:1c.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    0.515987] pci 0000:00:1c.0: setting latency timer to 64
[    0.515995] pci 0000:00:1c.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[    0.515999] pci 0000:00:1c.1: setting latency timer to 64
[    0.516007] pci 0000:00:1c.2: PCI INT C -> GSI 22 (level, low) -> IRQ 22
[    0.516011] pci 0000:00:1c.2: setting latency timer to 64
[    0.516019] pci 0000:00:1c.3: PCI INT D -> GSI 23 (level, low) -> IRQ 23
[    0.516023] pci 0000:00:1c.3: setting latency timer to 64
[    0.516031] pci 0000:00:1c.4: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    0.516035] pci 0000:00:1c.4: setting latency timer to 64
[    0.516042] pci 0000:00:1e.0: setting latency timer to 64
[    0.516051] pci 0000:15:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.516057] bus: 00 index 0 io port: [0, ffff]
[    0.516058] bus: 00 index 1 mmio: [0, ffffffff]
[    0.516060] bus: 01 index 0 io port: [2000, 2fff]
[    0.516061] bus: 01 index 1 mmio: [cff00000, cfffffff]
[    0.516063] bus: 01 index 2 mmio: [d0000000, dfffffff]
[    0.516064] bus: 01 index 3 mmio: [0, 0]
[    0.516065] bus: 02 index 0 mmio: [0, 0]
[    0.516067] bus: 02 index 1 mmio: [0, 0]
[    0.516068] bus: 02 index 2 mmio: [0, 0]
[    0.516069] bus: 02 index 3 mmio: [0, 0]
[    0.516070] bus: 03 index 0 mmio: [0, 0]
[    0.516072] bus: 03 index 1 mmio: [f4200000, f42fffff]
[    0.516073] bus: 03 index 2 mmio: [0, 0]
[    0.516074] bus: 03 index 3 mmio: [0, 0]
[    0.516076] bus: 04 index 0 io port: [3000, 3fff]
[    0.516077] bus: 04 index 1 mmio: [f4300000, f43fffff]
[    0.516079] bus: 04 index 2 mmio: [c2000000, c20fffff]
[    0.516080] bus: 04 index 3 mmio: [0, 0]
[    0.516081] bus: 05 index 0 io port: [4000, 4fff]
[    0.516083] bus: 05 index 1 mmio: [f8000000, f9ffffff]
[    0.516084] bus: 05 index 2 mmio: [f4000000, f40fffff]
[    0.516085] bus: 05 index 3 mmio: [0, 0]
[    0.516087] bus: 0d index 0 io port: [5000, 5fff]
[    0.516088] bus: 0d index 1 mmio: [fa000000, fbffffff]
[    0.516090] bus: 0d index 2 mmio: [f4100000, f41fffff]
[    0.516091] bus: 0d index 3 mmio: [0, 0]
[    0.516092] bus: 15 index 0 io port: [6000, 9fff]
[    0.516094] bus: 15 index 1 mmio: [f4400000, f7ffffff]
[    0.516095] bus: 15 index 2 mmio: [f0000000, f3ffffff]
[    0.516097] bus: 15 index 3 io port: [0, ffff]
[    0.516098] bus: 15 index 4 mmio: [0, ffffffff]
[    0.516099] bus: 16 index 0 io port: [6000, 60ff]
[    0.516101] bus: 16 index 1 io port: [6400, 64ff]
[    0.516102] bus: 16 index 2 mmio: [f0000000, f3ffffff]
[    0.516104] bus: 16 index 3 mmio: [c4000000, c7ffffff]
[    0.516109] NET: Registered protocol family 2
[    0.528537] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.528698] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.528925] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.529034] TCP: Hash tables configured (established 131072 bind 65536)
[    0.529036] TCP reno registered
[    0.532545] NET: Registered protocol family 1
[    0.532609] checking if image is initramfs... it is
[    1.020676] Freeing initrd memory: 7955k freed
[    1.020930] Simple Boot Flag at 0x35 set to 0x1
[    1.021462] audit: initializing netlink socket (disabled)
[    1.021474] type=2000 audit(1236118020.020:1): initialized
[    1.025807] highmem bounce pool size: 64 pages
[    1.025811] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    1.027334] VFS: Disk quotas dquot_6.5.1
[    1.027389] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    1.027464] msgmni has been set to 1725
[    1.027548] io scheduler noop registered
[    1.027550] io scheduler anticipatory registered
[    1.027552] io scheduler deadline registered
[    1.027560] io scheduler cfq registered (default)
[    1.027706] pci 0000:01:00.0: Boot video device
[    1.027800] pcieport-driver 0000:00:01.0: setting latency timer to 64
[    1.027828] pcieport-driver 0000:00:01.0: found MSI capability
[    1.027852] pci_express 0000:00:01.0:pcie00: allocate port service
[    1.027881] pci_express 0000:00:01.0:pcie02: allocate port service
[    1.027907] pci_express 0000:00:01.0:pcie03: allocate port service
[    1.027970] pcieport-driver 0000:00:1c.0: setting latency timer to 64
[    1.028013] pcieport-driver 0000:00:1c.0: found MSI capability
[    1.028055] pci_express 0000:00:1c.0:pcie00: allocate port service
[    1.028082] pci_express 0000:00:1c.0:pcie02: allocate port service
[    1.028107] pci_express 0000:00:1c.0:pcie03: allocate port service
[    1.028197] pcieport-driver 0000:00:1c.1: setting latency timer to 64
[    1.028241] pcieport-driver 0000:00:1c.1: found MSI capability
[    1.028282] pci_express 0000:00:1c.1:pcie00: allocate port service
[    1.028308] pci_express 0000:00:1c.1:pcie02: allocate port service
[    1.028334] pci_express 0000:00:1c.1:pcie03: allocate port service
[    1.028423] pcieport-driver 0000:00:1c.2: setting latency timer to 64
[    1.028466] pcieport-driver 0000:00:1c.2: found MSI capability
[    1.028511] pci_express 0000:00:1c.2:pcie00: allocate port service
[    1.028538] pci_express 0000:00:1c.2:pcie02: allocate port service
[    1.028563] pci_express 0000:00:1c.2:pcie03: allocate port service
[    1.028651] pcieport-driver 0000:00:1c.3: setting latency timer to 64
[    1.028695] pcieport-driver 0000:00:1c.3: found MSI capability
[    1.028736] pci_express 0000:00:1c.3:pcie00: allocate port service
[    1.028762] pci_express 0000:00:1c.3:pcie02: allocate port service
[    1.028789] pci_express 0000:00:1c.3:pcie03: allocate port service
[    1.028878] pcieport-driver 0000:00:1c.4: setting latency timer to 64
[    1.028921] pcieport-driver 0000:00:1c.4: found MSI capability
[    1.028963] pci_express 0000:00:1c.4:pcie00: allocate port service
[    1.028989] pci_express 0000:00:1c.4:pcie02: allocate port service
[    1.029016] pci_express 0000:00:1c.4:pcie03: allocate port service
[    1.029266] isapnp: Scanning for PnP cards...
[    1.383350] isapnp: No Plug & Play device found
[    1.404907] hpet_resources: 0xfed00000 is busy
[    1.404969] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
[    1.406506] brd: module loaded
[    1.406554] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[    1.406634] PNP: PS/2 Controller [PNP0303:KBD,PNP0f13:MOU] at 0x60,0x64 irq 1,12
[    1.416257] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.416261] serio: i8042 AUX port at 0x60,0x64 irq 12
[    1.420072] mice: PS/2 mouse device common for all mice
[    1.420152] rtc_cmos 00:07: rtc core: registered rtc_cmos as rtc0
[    1.420178] rtc0: alarms up to one month, y3k, hpet irqs
[    1.420258] EISA: Probing bus 0 at eisa.0
[    1.420264] Cannot allocate resource for EISA slot 1
[    1.420266] Cannot allocate resource for EISA slot 2
[    1.420267] Cannot allocate resource for EISA slot 3
[    1.420269] Cannot allocate resource for EISA slot 4
[    1.420270] Cannot allocate resource for EISA slot 5
[    1.420272] Cannot allocate resource for EISA slot 6
[    1.420273] Cannot allocate resource for EISA slot 7
[    1.420274] Cannot allocate resource for EISA slot 8
[    1.420276] EISA: Detected 0 cards.
[    1.420278] cpuidle: using governor ladder
[    1.420280] cpuidle: using governor menu
[    1.420624] TCP cubic registered
[    1.420643] Using IPI No-Shortcut mode
[    1.420755] registered taskstats version 1
[    1.420867]   Magic number: 1:604:147
[    1.420875] tty ttyp1: hash matches
[    1.420889] acpi device:18: hash matches
[    1.420918] rtc_cmos 00:07: setting system clock to 2009-03-03 22:07:01 UTC (1236118021)
[    1.420920] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.420922] EDD information not available.
[    1.421157] Freeing unused kernel memory: 424k freed
[    1.421183] Write protecting the kernel text: 2580k
[    1.421202] Write protecting the kernel read-only data: 940k
[    1.436526] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[    1.540043] fuse init (API version 7.9)
[    1.588492] ACPI: SSDT BFAD7AA0, 030A (r1  PmRef  Cpu0Ist     3000 INTL 20050624)
[    1.588926] ACPI: SSDT BFAD5020, 087A (r1  PmRef  Cpu0Cst     3001 INTL 20050624)
[    1.591219] Monitor-Mwait will be used to enter C-1 state
[    1.591221] Monitor-Mwait will be used to enter C-2 state
[    1.591223] Monitor-Mwait will be used to enter C-3 state
[    1.591344] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[    1.591380] processor ACPI0007:00: registered as cooling_device0
[    1.591383] ACPI: Processor [CPU0] (supports 8 throttling states)
[    1.591777] ACPI: SSDT BFAD6CA0, 01CF (r1  PmRef    ApIst     3000 INTL 20050624)
[    1.592227] ACPI: SSDT BFAD6F20, 008D (r1  PmRef    ApCst     3000 INTL 20050624)
[    1.599998] Marking TSC unstable due to TSC halts in idle
[    1.697035] ACPI: CPU1 (power states: C1[C1] C2[C2] C3[C3])
[    1.697087] processor ACPI0007:01: registered as cooling_device1
[    1.697090] ACPI: Processor [CPU1] (supports 8 throttling states)
[    1.700871] thermal LNXTHERM:01: registered as thermal_zone0
[    1.704275] ACPI: Thermal Zone [THM0] (48 C)
[    1.705271] thermal LNXTHERM:02: registered as thermal_zone1
[    1.706513] ACPI: Thermal Zone [THM1] (46 C)
[    1.905331] usbcore: registered new interface driver usbfs
[    1.905347] usbcore: registered new interface driver hub
[    1.905368] usbcore: registered new device driver usb
[    1.912590] USB Universal Host Controller Interface driver v3.0
[    1.913157] uhci_hcd 0000:00:1a.0: power state changed by ACPI to D0
[    1.913165] uhci_hcd 0000:00:1a.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    1.913172] uhci_hcd 0000:00:1a.0: setting latency timer to 64
[    1.913175] uhci_hcd 0000:00:1a.0: UHCI Host Controller
[    1.913204] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 1
[    1.913240] uhci_hcd 0000:00:1a.0: irq 20, io base 0x00001860
[    1.913339] usb usb1: configuration #1 chosen from 1 choice
[    1.913357] hub 1-0:1.0: USB hub found
[    1.913362] hub 1-0:1.0: 2 ports detected
[    1.973961] Warning! ehci_hcd should always be loaded before uhci_hcd and ohci_hcd, not after
[    1.992163] e1000e: Intel(R) PRO/1000 Network Driver - 0.3.3.3-k6
[    1.992165] e1000e: Copyright (c) 1999-2008 Intel Corporation.
[    1.996344] ACPI: ACPI Dock Station Driver
[    2.010548] SCSI subsystem initialized
[    2.051090] libata version 3.00 loaded.
[    2.120186] uhci_hcd 0000:00:1a.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[    2.120194] uhci_hcd 0000:00:1a.1: setting latency timer to 64
[    2.120197] uhci_hcd 0000:00:1a.1: UHCI Host Controller
[    2.120215] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 2
[    2.120247] uhci_hcd 0000:00:1a.1: irq 21, io base 0x00001880
[    2.120313] usb usb2: configuration #1 chosen from 1 choice
[    2.120332] hub 2-0:1.0: USB hub found
[    2.120340] hub 2-0:1.0: 2 ports detected
[    2.232071] usb 1-1: new low speed USB device using uhci_hcd and address 2
[    2.329128] uhci_hcd 0000:00:1a.2: power state changed by ACPI to D0
[    2.329134] uhci_hcd 0000:00:1a.2: PCI INT C -> GSI 22 (level, low) -> IRQ 22
[    2.329141] uhci_hcd 0000:00:1a.2: setting latency timer to 64
[    2.329144] uhci_hcd 0000:00:1a.2: UHCI Host Controller
[    2.329163] uhci_hcd 0000:00:1a.2: new USB bus registered, assigned bus number 3
[    2.329192] uhci_hcd 0000:00:1a.2: irq 22, io base 0x000018a0
[    2.329255] usb usb3: configuration #1 chosen from 1 choice
[    2.329273] hub 3-0:1.0: USB hub found
[    2.329278] hub 3-0:1.0: 2 ports detected
[    2.414434] usb 1-1: configuration #1 chosen from 1 choice
[    2.500066] Clocksource tsc unstable (delta = -261127304 ns)
[    2.528111] usb 2-1: new full speed USB device using uhci_hcd and address 2
[    2.536398] e1000e 0000:00:19.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    2.536405] e1000e 0000:00:19.0: setting latency timer to 64
[    2.626507] 0000:00:19.0: eth0: (PCI Express:2.5GB/s:Width x1) 00:1c:25:95:b8:56
[    2.626509] 0000:00:19.0: eth0: Intel(R) PRO/1000 Network Connection
[    2.626536] 0000:00:19.0: eth0: MAC: 5, PHY: 8, PBA No: 1008ff-0ff
[    2.627597] ehci_hcd 0000:00:1a.7: power state changed by ACPI to D0
[    2.627604] ehci_hcd 0000:00:1a.7: PCI INT D -> GSI 23 (level, low) -> IRQ 23
[    2.627610] ehci_hcd 0000:00:1a.7: setting latency timer to 64
[    2.627613] ehci_hcd 0000:00:1a.7: EHCI Host Controller
[    2.627631] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 4
[    2.631527] ehci_hcd 0000:00:1a.7: debug port 1
[    2.631532] ehci_hcd 0000:00:1a.7: cache line size of 32 is not supported
[    2.631540] ehci_hcd 0000:00:1a.7: irq 23, io mem 0xfc226c00
[    2.641784] Monitor-Mwait will be used to enter C-3 state
[    2.652106] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    2.652194] usb usb4: configuration #1 chosen from 1 choice
[    2.652226] hub 4-0:1.0: USB hub found
[    2.652234] hub 4-0:1.0: 6 ports detected
[    2.860892] uhci_hcd 0000:00:1d.0: power state changed by ACPI to D0
[    2.860899] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    2.860907] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    2.860911] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    2.860945] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 5
[    2.860981] uhci_hcd 0000:00:1d.0: irq 16, io base 0x000018c0
[    2.861080] usb usb5: configuration #1 chosen from 1 choice
[    2.861111] hub 5-0:1.0: USB hub found
[    2.861118] hub 5-0:1.0: 2 ports detected
[    2.964250] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    2.964256] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    2.964259] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    2.964276] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 6
[    2.964303] uhci_hcd 0000:00:1d.1: irq 17, io base 0x000018e0
[    2.964362] usb usb6: configuration #1 chosen from 1 choice
[    2.964385] hub 6-0:1.0: USB hub found
[    2.964390] hub 6-0:1.0: 2 ports detected
[    3.052609] usb 2-1: device not accepting address 2, error -71
[    3.108091] hub 2-0:1.0: unable to enumerate USB device on port 1
[    3.173026] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    3.173031] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    3.173034] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    3.173051] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 7
[    3.173078] uhci_hcd 0000:00:1d.2: irq 18, io base 0x00001c00
[    3.173136] usb usb7: configuration #1 chosen from 1 choice
[    3.173164] hub 7-0:1.0: USB hub found
[    3.173168] hub 7-0:1.0: 2 ports detected
[    3.277707] ehci_hcd 0000:00:1d.7: power state changed by ACPI to D0
[    3.277715] ehci_hcd 0000:00:1d.7: PCI INT D -> GSI 19 (level, low) -> IRQ 19
[    3.277722] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    3.277725] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    3.277743] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 8
[    3.281646] ehci_hcd 0000:00:1d.7: debug port 1
[    3.281652] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
[    3.281660] ehci_hcd 0000:00:1d.7: irq 19, io mem 0xfc227000
[    3.296013] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    3.296070] usb usb8: configuration #1 chosen from 1 choice
[    3.296088] hub 8-0:1.0: USB hub found
[    3.296093] hub 8-0:1.0: 6 ports detected
[    3.504536] ahci 0000:00:1f.2: version 3.0
[    3.504547] ahci 0000:00:1f.2: PCI INT B -> GSI 16 (level, low) -> IRQ 16
[    3.504631] ahci 0000:00:1f.2: AHCI 0001.0200 32 slots 4 ports 3 Gbps 0x3 impl SATA mode
[    3.504634] ahci 0000:00:1f.2: flags: 64bit ncq sntf stag pm led clo pio slum part 
[    3.504639] ahci 0000:00:1f.2: setting latency timer to 64
[    3.504779] scsi0 : ahci
[    3.505006] scsi1 : ahci
[    3.505219] scsi2 : ahci
[    3.505434] scsi3 : ahci
[    3.506150] ata1: SATA max UDMA/133 abar m2048@0xfc226000 port 0xfc226100 irq 217
[    3.506153] ata2: SATA max UDMA/133 abar m2048@0xfc226000 port 0xfc226180 irq 217
[    3.506154] ata3: DUMMY
[    3.506155] ata4: DUMMY
[    3.756063] usb 4-6: new high speed USB device using ehci_hcd and address 5
[    3.824072] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    3.825301] ata1.00: ACPI cmd ef/02:00:00:00:00:a0 succeeded
[    3.825303] ata1.00: ACPI cmd f5/00:00:00:00:00:a0 filtered out
[    3.825543] ata1.00: ACPI cmd ef/5f:00:00:00:00:a0 succeeded
[    3.825545] ata1.00: ACPI cmd ef/10:03:00:00:00:a0 filtered out
[    3.826527] ata1.00: ATA-8: HITACHI HTS722016K9SA00, DCDZC75A, max UDMA/133
[    3.826529] ata1.00: 312581808 sectors, multi 16: LBA48 NCQ (depth 31/32)
[    3.827976] ata1.00: ACPI cmd ef/02:00:00:00:00:a0 succeeded
[    3.827978] ata1.00: ACPI cmd f5/00:00:00:00:00:a0 filtered out
[    3.828211] ata1.00: ACPI cmd ef/5f:00:00:00:00:a0 succeeded
[    3.828213] ata1.00: ACPI cmd ef/10:03:00:00:00:a0 filtered out
[    3.829192] ata1.00: configured for UDMA/133
[    3.846283] ata1.00: configured for UDMA/133
[    3.846285] ata1: EH complete
[    3.894138] usb 4-6: configuration #1 chosen from 1 choice
[    3.895012] usbcore: registered new interface driver hiddev
[    3.895166] usb 1-1: USB disconnect, address 2
[    4.132580] usb 1-1: new low speed USB device using uhci_hcd and address 3
[    4.164099] ata2: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    4.166049] ata2.00: ACPI cmd ef/02:00:00:00:00:a0 succeeded
[    4.166052] ata2.00: ACPI cmd f5/00:00:00:00:00:a0 filtered out
[    4.166053] ata2.00: ACPI cmd ef/10:03:00:00:00:a0 filtered out
[    4.166248] ata2.00: ATA-7: SAMSUNG SSD RBX Series 64GB, PS105D14, max UDMA/100
[    4.166250] ata2.00: 125045424 sectors, multi 16: LBA48 
[    4.168005] ata2.00: ACPI cmd ef/02:00:00:00:00:a0 succeeded
[    4.168007] ata2.00: ACPI cmd f5/00:00:00:00:00:a0 filtered out
[    4.168009] ata2.00: ACPI cmd ef/10:03:00:00:00:a0 filtered out
[    4.168207] ata2.00: configured for UDMA/100
[    4.184580] ata2.00: configured for UDMA/100
[    4.184583] ata2: EH complete
[    4.184806] scsi 0:0:0:0: Direct-Access     ATA      HITACHI HTS72201 DCDZ PQ: 0 ANSI: 5
[    4.184896] scsi 1:0:0:0: Direct-Access     ATA      SAMSUNG SSD RBX  PS10 PQ: 0 ANSI: 5
[    4.184972] ohci1394 0000:15:00.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    4.237749] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[17]  MMIO=[f4401000-f44017ff]  Max Packet=[2048]  IR/IT contexts=[4/4]
[    4.249533] scsi 0:0:0:0: Attached scsi generic sg0 type 0
[    4.249557] scsi 1:0:0:0: Attached scsi generic sg1 type 0
[    4.271455] Driver 'sd' needs updating - please use bus_type methods
[    4.271510] sd 0:0:0:0: [sda] 312581808 512-byte hardware sectors (160042 MB)
[    4.271521] sd 0:0:0:0: [sda] Write Protect is off
[    4.271523] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    4.271540] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.271585] sd 0:0:0:0: [sda] 312581808 512-byte hardware sectors (160042 MB)
[    4.271600] sd 0:0:0:0: [sda] Write Protect is off
[    4.271602] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    4.271618] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.271620]  sda: sda1 sda2 sda3 sda4 < sda5 sda6 sda7 >
[    4.320307] sd 0:0:0:0: [sda] Attached SCSI disk
[    4.320347] sd 1:0:0:0: [sdb] 125045424 512-byte hardware sectors (64023 MB)
[    4.320358] sd 1:0:0:0: [sdb] Write Protect is off
[    4.320360] sd 1:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[    4.320378] sd 1:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.320417] sd 1:0:0:0: [sdb] 125045424 512-byte hardware sectors (64023 MB)
[    4.320427] sd 1:0:0:0: [sdb] Write Protect is off
[    4.320429] sd 1:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[    4.320446] sd 1:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.320448]  sdb: sdb1 sdb2
[    4.321660] sd 1:0:0:0: [sdb] Attached SCSI disk
[    4.362385] usb 1-1: configuration #1 chosen from 1 choice
[    4.604680] usb 2-1: new full speed USB device using uhci_hcd and address 4
[    4.775498] usb 2-1: configuration #1 chosen from 1 choice
[    5.016072] usb 2-2: new full speed USB device using uhci_hcd and address 5
[    5.182371] usb 2-2: configuration #1 chosen from 1 choice
[    5.424082] usb 8-4: new high speed USB device using ehci_hcd and address 2
[    5.512374] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[00016c00006a68d3]
[    5.634911] usb 8-4: configuration #1 chosen from 2 choices
[    5.708514] input: Microsoft Microsoft 3-Button Mouse with IntelliEye(TM) as /devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1:1.0/input/input2
[    5.708661] input,hidraw0: USB HID v1.10 Mouse [Microsoft Microsoft 3-Button Mouse with IntelliEye(TM)] on usb-0000:00:1a.0-1
[    5.708680] usbcore: registered new interface driver usbhid
[    5.708682] usbhid: v2.6:USB HID core driver
[    5.743954] PM: Starting manual resume from disk
[    5.743956] PM: Resume from partition 8:6
[    5.743957] PM: Checking hibernation image.
[    5.744134] PM: Resume from disk failed.
[    5.773692] kjournald starting.  Commit interval 5 seconds
[    5.773702] EXT3-fs: mounted filesystem with ordered data mode.
[   11.809916] udevd version 124 started
[   12.056085] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   12.144051] Linux agpgart interface v0.103
[   12.285126] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   12.326179] input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input3
[   12.352018] ACPI: Power Button (FF) [PWRF]
[   12.352069] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input4
[   12.352681] ACPI: Lid Switch [LID]
[   12.352730] input: Sleep Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input5
[   12.372516] ACPI: Sleep Button (CM) [SLPB]
[   12.372667] ACPI: WMI: Mapper loaded
[   12.390702] ACPI: \_SB_.PCI0.SATA.PRT1: found ejectable bay
[   12.390706] ACPI: \_SB_.PCI0.SATA.PRT1: Adding notify handler
[   12.404675] ACPI: Error installing bay notify handler
[   12.452706] acpi device:03: registered as cooling_device2
[   12.452898] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:02/input/input6
[   12.484525] ACPI: Video Device [VID] (multi-head: yes  rom: no  post: no)
[   12.486130] acpi device:0a: registered as cooling_device3
[   12.486296] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:08/device:09/input/input7
[   12.487677] ACPI: AC Adapter [AC] (on-line)
[   12.516518] ACPI: Video Device [VID1] (multi-head: yes  rom: no  post: no)
[   12.576090] ACPI: Battery Slot [BAT0] (battery present)
[   12.749004] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
[   12.765275] [fglrx] Maximum main memory to use for locked dma buffers: 2887 MBytes.
[   12.765900] [fglrx]   vendor: 1002 device: 9591 count: 1
[   12.766737] [fglrx] ioport: bar 1, base 0x2000, size: 0x100
[   12.766809] pci 0000:01:00.0: power state changed by ACPI to D0
[   12.766815] pci 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   12.766820] pci 0000:01:00.0: setting latency timer to 64
[   12.769531] [fglrx] PAT is enabled successfully!
[   12.769573] [fglrx] module loaded - fglrx 8.54.3 [Oct 10 2008] with 1 minors
[   12.819603] Bluetooth: Core ver 2.13
[   12.834357] NET: Registered protocol family 31
[   12.834359] Bluetooth: HCI device and connection manager initialized
[   12.834361] Bluetooth: HCI socket layer initialized
[   12.914770] Linux video capture interface: v2.00
[   12.940336] ricoh-mmc: Ricoh MMC Controller disabling driver
[   12.940338] ricoh-mmc: Copyright(c) Philip Langdale
[   12.940400] ricoh-mmc: Ricoh MMC controller found at 0000:15:00.3 [1180:0843] (rev 11)
[   12.940421] ricoh-mmc: Controller is now disabled.
[   13.068546] Bluetooth: Generic Bluetooth USB driver ver 0.3
[   13.068627] usbcore: registered new interface driver btusb
[   13.167723] usbcore: registered new interface driver usbserial
[   13.167735] usbserial: USB Serial support registered for generic
[   13.167812] usbcore: registered new interface driver usbserial_generic
[   13.167813] usbserial: USB Serial Driver core
[   13.215515] usbserial: USB Serial support registered for GSM modem (1-port)
[   13.215552] option 8-4:1.0: GSM modem (1-port) converter detected
[   13.215662] usb 8-4: GSM modem (1-port) converter now attached to ttyUSB0
[   13.215673] option 8-4:1.1: GSM modem (1-port) converter detected
[   13.215727] usb 8-4: GSM modem (1-port) converter now attached to ttyUSB1
[   13.215738] option 8-4:1.2: GSM modem (1-port) converter detected
[   13.215782] usb 8-4: GSM modem (1-port) converter now attached to ttyUSB2
[   13.215793] option 8-4:1.3: GSM modem (1-port) converter detected
[   13.215840] usb 8-4: GSM modem (1-port) converter now attached to ttyUSB3
[   13.215851] option 8-4:1.4: GSM modem (1-port) converter detected
[   13.215896] usb 8-4: GSM modem (1-port) converter now attached to ttyUSB4
[   13.215907] option 8-4:1.5: GSM modem (1-port) converter detected
[   13.215954] usb 8-4: GSM modem (1-port) converter now attached to ttyUSB5
[   13.215965] option 8-4:1.6: GSM modem (1-port) converter detected
[   13.216013] usb 8-4: GSM modem (1-port) converter now attached to ttyUSB6
[   13.216024] option 8-4:1.7: GSM modem (1-port) converter detected
[   13.216077] usb 8-4: GSM modem (1-port) converter now attached to ttyUSB7
[   13.216088] option 8-4:1.8: GSM modem (1-port) converter detected
[   13.216134] usb 8-4: GSM modem (1-port) converter now attached to ttyUSB8
[   13.216144] option 8-4:1.9: GSM modem (1-port) converter detected
[   13.216192] usb 8-4: GSM modem (1-port) converter now attached to ttyUSB9
[   13.216203] option 8-4:1.10: GSM modem (1-port) converter detected
[   13.216248] usb 8-4: GSM modem (1-port) converter now attached to ttyUSB10
[   13.216258] usbcore: registered new interface driver option
[   13.216260] option: USB Driver for GSM modems: v0.7.2
[   13.242137] Yenta: CardBus bridge found at 0000:15:00.0 [17aa:20c6]
[   13.290618] usbcore: registered new interface driver cdc_acm
[   13.290630] cdc_acm: v0.26:USB Abstract Control Model driver for USB modems and ISDN adapters
[   13.295162] sdhci: Secure Digital Host Controller Interface driver
[   13.295164] sdhci: Copyright(c) Pierre Ossman
[   13.297131] usbcore: registered new interface driver cdc_wdm
[   13.361969] Non-volatile memory driver v1.2
[   13.369293] Yenta: ISA IRQ mask 0x0cb8, PCI irq 16
[   13.369296] Socket status: 30000006
[   13.369299] pcmcia: parent PCI bridge I/O window: 0x6000 - 0x9fff
[   13.369313] cs: IO port probe 0x6000-0x9fff: clean.
[   13.369974] pcmcia: parent PCI bridge Memory window: 0xf4400000 - 0xf7ffffff
[   13.369985] pcmcia: parent PCI bridge Memory window: 0xf0000000 - 0xf3ffffff
[   13.370615] sdhci-pci 0000:15:00.2: SDHCI controller found [1180:0822] (rev 21)
[   13.370630] sdhci-pci 0000:15:00.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[   13.371637] sdhci-pci 0000:15:00.2: Will use DMA mode even though HW doesn't fully claim to support it.
[   13.373674] mmc0: SDHCI controller on PCI [0000:15:00.2] using DMA
[   13.412265] uvcvideo: Found UVC 1.00 device <unnamed> (17ef:4807)
[   13.417443] input: UVC Camera (17ef:4807) as /devices/pci0000:00/0000:00:1a.7/usb4/4-6/4-6:1.0/input/input8
[   13.464624] usbcore: registered new interface driver uvcvideo
[   13.464627] USB Video Class driver (v0.1.0)
[   13.477727] usbcore: registered new interface driver cdc_ether
[   13.524441] usbcore: registered new interface driver zaurus
[   13.581620] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, 1.3.27ks
[   13.581622] iwlagn: Copyright(c) 2003-2008 Intel Corporation
[   13.582424] iwlagn 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   13.582432] iwlagn 0000:03:00.0: setting latency timer to 64
[   13.582455] iwlagn: Detected Intel Wireless WiFi Link 5100AGN REV=0x54
[   13.612008] iwlagn: Tunable channels: 13 802.11bg, 24 802.11a channels
[   13.665266] iwlagn 0000:03:00.0: PCI INT A disabled
[   13.665588] phy0: Selected rate control algorithm 'iwl-agn-rs'
[   14.135788] Synaptics Touchpad, model: 1, fw: 7.0, id: 0x1c0b1, caps: 0xd04791/0xb00000
[   14.135792] serio: Synaptics pass-through port at isa0060/serio1/input0
[   14.180680] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input9
[   14.208180] thinkpad_acpi: ThinkPad ACPI Extras v0.21
[   14.208182] thinkpad_acpi: [http://ibm-acpi.sf.net/](http://ibm-acpi.sf.net/)
[   14.208183] thinkpad_acpi: ThinkPad BIOS 6FET43WW (1.13 ), EC 7VHT12WW-1.01
[   14.208185] thinkpad_acpi: Lenovo ThinkPad W500, model 406224U
[   14.209105] thinkpad_acpi: radio switch found; radios are enabled
[   14.209212] thinkpad_acpi: This ThinkPad has standard ACPI backlight brightness control, supported by the ACPI video driver
[   14.209214] thinkpad_acpi: Disabling thinkpad-acpi brightness events by default...
[   14.222559] Registered led device: tpacpi::thinklight
[   14.222594] Registered led device: tpacpi::power
[   14.222615] Registered led device: tpacpi:orange:batt
[   14.222636] Registered led device: tpacpi:green:batt
[   14.222659] Registered led device: tpacpi::dock_active
[   14.222680] Registered led device: tpacpi::bay_active
[   14.222702] Registered led device: tpacpi::dock_batt
[   14.222724] Registered led device: tpacpi::unknown_led
[   14.222745] Registered led device: tpacpi::standby
[   14.225822] thinkpad_acpi: Lenovo BIOS switched to ACPI backlight control mode
[   14.225824] thinkpad_acpi: standard ACPI backlight interface available, not loading native one...
[   14.226162] input: ThinkPad Extra Buttons as /devices/virtual/input/input10
[   14.388709] HDA Intel 0000:00:1b.0: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[   14.388727] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   14.493802] cs: IO port probe 0x100-0x3af: clean.
[   14.495518] cs: IO port probe 0x3e0-0x4ff: excluding 0x4d0-0x4d7
[   14.496231] cs: IO port probe 0x820-0x8ff: clean.
[   14.497197] cs: IO port probe 0xc00-0xcf7: clean.
[   14.497889] cs: IO port probe 0xa00-0xaff: clean.
[   14.806339] lp: driver loaded but no devices found
[   14.961465] Adding 997880k swap on /dev/sda6.  Priority:-1 extents:1 across:997880k
[   15.489765] EXT3 FS on sda7, internal journal
[   16.390967] type=1505 audit(1236107236.744:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=4696
[   16.428071] type=1505 audit(1236107236.783:3): operation="profile_load" name="/usr/bin/freshclam" name2="default" pid=4701
[   16.533574] type=1505 audit(1236107236.887:4): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=4705
[   16.533705] type=1505 audit(1236107236.887:5): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=4705
[   16.670570] ip_tables: (C) 2000-2006 Netfilter Core Team
[   17.136304] NET: Registered protocol family 10
[   17.136662] lo: Disabled Privacy Extensions
[   17.137070] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   17.777789] ACPI: \_SB_.PCI0.SATA.PRT1: found ejectable bay
[   17.777794] ACPI: \_SB_.PCI0.SATA.PRT1: Adding notify handler
[   17.777816] ACPI: Error installing bay notify handler
[   18.522956] warning: `avahi-daemon' uses 32-bit capabilities (legacy support in use)
[   18.706860] apm: BIOS not found.
[   19.577201] ppdev: user-space parallel port driver
[   20.158794] IBM TrackPoint firmware: 0x0e, buttons: 3/3
[   20.447132] input: TPPS/2 IBM TrackPoint as /devices/platform/i8042/serio1/serio2/input/input11
[   20.786413] vboxdrv: Trying to deactivate the NMI watchdog permanently...
[   20.786418] vboxdrv: Successfully done.
[   20.786419] vboxdrv: Found 2 processor cores.
[   20.786512] vboxdrv: fAsync=0 offMin=0x20d offMax=0xc98
[   20.786515] vboxdrv: TSC mode is 'synchronous', kernel timer mode is 'normal'.
[   20.786517] vboxdrv: Successfully loaded version 2.0.4_OSE (interface 0x00090000).
[   23.219070] Bluetooth: L2CAP ver 2.11
[   23.219082] Bluetooth: L2CAP socket layer initialized
[   23.251438] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   23.251449] Bluetooth: BNEP filters: protocol multicast
[   23.310539] Bridge firewalling registered
[   23.358737] Bluetooth: SCO (Voice Link) ver 0.6
[   23.358747] Bluetooth: SCO socket layer initialized
[   23.376819] Bluetooth: RFCOMM socket layer initialized
[   23.377175] Bluetooth: RFCOMM TTY layer initialized
[   23.377184] Bluetooth: RFCOMM ver 1.10
[   27.608932] iwlagn 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   27.609052] iwlagn 0000:03:00.0: restoring config space at offset 0x1 (was 0x100102, writing 0x100106)
[   27.609290] firmware: requesting iwlwifi-5000-1.ucode
[   30.198700] Registered led device: iwl-phy0:radio
[   30.198862] Registered led device: iwl-phy0:assoc
[   30.198977] Registered led device: iwl-phy0:RX
[   30.199086] Registered led device: iwl-phy0:TX
[   30.240767] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   30.348631] NET: Registered protocol family 17
[   31.949432] wlan0: authenticate with AP 00:14:c1:19:12:6c
[   31.951361] wlan0: authenticated
[   31.951373] wlan0: associate with AP 00:14:c1:19:12:6c
[   31.953777] wlan0: RX AssocResp from 00:14:c1:19:12:6c (capab=0x401 status=0 aid=1)
[   31.953790] wlan0: associated
[   31.958643] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   31.961612] wlan0: disassociating by local choice (reason=3)
[   42.552583] wlan0: no IPv6 routers present
[   53.469071] wlan0: associate with AP 00:14:c1:19:12:6c
[   53.471671] wlan0: RX ReassocResp from 00:14:c1:19:12:6c (capab=0x401 status=0 aid=1)
[   53.471685] wlan0: associated
[   53.478469] wlan0: disassociating by local choice (reason=3)
[   68.242678] CPU0 attaching NULL sched-domain.
[   68.242696] CPU1 attaching NULL sched-domain.
[   68.249404] CPU0 attaching sched-domain:
[   68.249415]  domain 0: span 0-1 level MC
[   68.249421]   groups: 0 1
[   68.249434] CPU1 attaching sched-domain:
[   68.249439]  domain 0: span 0-1 level MC
[   68.249444]   groups: 1 0
[   72.105376] wlan0: associate with AP 00:14:c1:19:12:6c
[   72.108357] wlan0: RX ReassocResp from 00:14:c1:19:12:6c (capab=0x401 status=0 aid=1)
[   72.108368] wlan0: associated
[   72.114176] wlan0: authenticate with AP 00:14:c1:19:12:6c
[   72.116171] wlan0: authenticated
[   72.116182] wlan0: associate with AP 00:14:c1:19:12:6c
[   72.118386] wlan0: RX ReassocResp from 00:14:c1:19:12:6c (capab=0x401 status=0 aid=1)
[   72.118395] wlan0: associated
[  137.616706] type=1503 audit(1236107357.972:6): operation="inode_permission" requested_mask="w::" denied_mask="w::" fsuid=0 name="/dev/ttyUSB0" pid=8849 profile="/usr/sbin/cupsd"
[  137.619649] type=1503 audit(1236107357.972:7): operation="inode_permission" requested_mask="w::" denied_mask="w::" fsuid=0 name="/dev/ttyUSB1" pid=8849 profile="/usr/sbin/cupsd"
[  137.622538] type=1503 audit(1236107357.976:8): operation="inode_permission" requested_mask="w::" denied_mask="w::" fsuid=0 name="/dev/ttyUSB2" pid=8849 profile="/usr/sbin/cupsd"
[  137.625487] type=1503 audit(1236107357.980:9): operation="inode_permission" requested_mask="w::" denied_mask="w::" fsuid=0 name="/dev/ttyUSB3" pid=8849 profile="/usr/sbin/cupsd"
[  137.628098] type=1503 audit(1236107357.980:10): operation="inode_permission" requested_mask="w::" denied_mask="w::" fsuid=0 name="/dev/ttyUSB4" pid=8849 profile="/usr/sbin/cupsd"
[  137.628137] type=1503 audit(1236107357.980:11): operation="inode_permission" requested_mask="w::" denied_mask="w::" fsuid=0 name="/dev/ttyUSB5" pid=8849 profile="/usr/sbin/cupsd"
[  137.628174] type=1503 audit(1236107357.980:12): operation="inode_permission" requested_mask="w::" denied_mask="w::" fsuid=0 name="/dev/ttyUSB6" pid=8849 profile="/usr/sbin/cupsd"
[  137.628212] type=1503 audit(1236107357.980:13): operation="inode_permission" requested_mask="w::" denied_mask="w::" fsuid=0 name="/dev/ttyUSB7" pid=8849 profile="/usr/sbin/cupsd"
[  137.628249] type=1503 audit(1236107357.980:14): operation="inode_permission" requested_mask="w::" denied_mask="w::" fsuid=0 name="/dev/ttyUSB8" pid=8849 profile="/usr/sbin/cupsd"
[  137.628286] type=1503 audit(1236107357.980:15): operation="inode_permission" requested_mask="w::" denied_mask="w::" fsuid=0 name="/dev/ttyUSB9" pid=8849 profile="/usr/sbin/cupsd"

```

---

### Post by Bashar &quot; on 2009-03-03
no lines pops when i press Fn+F7 

and here is dmesg output:
```

[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.27-11-generic (buildd@rothera) (gcc version 4.3.2 (Ubuntu 4.3.2-1ubuntu11) ) #1 SMP Thu Jan 29 19:24:39 UTC 2009 (Ubuntu 2.6.27-11.27-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009ac00 (usable)
[    0.000000]  BIOS-e820: 000000000009ac00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000d6000 - 00000000000d8000 (reserved)
[    0.000000]  BIOS-e820: 00000000000dc000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 00000000bf8a1000 (usable)
[    0.000000]  BIOS-e820: 00000000bf8a1000 - 00000000bf8a7000 (reserved)
[    0.000000]  BIOS-e820: 00000000bf8a7000 - 00000000bf9b7000 (usable)
[    0.000000]  BIOS-e820: 00000000bf9b7000 - 00000000bfa0f000 (reserved)
[    0.000000]  BIOS-e820: 00000000bfa0f000 - 00000000bfac7000 (usable)
[    0.000000]  BIOS-e820: 00000000bfac7000 - 00000000bfad2000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000bfad2000 - 00000000bfad5000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000bfad5000 - 00000000bfad9000 (reserved)
[    0.000000]  BIOS-e820: 00000000bfad9000 - 00000000bfadd000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000bfadd000 - 00000000bfae0000 (reserved)
[    0.000000]  BIOS-e820: 00000000bfae0000 - 00000000bfb07000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000bfb07000 - 00000000bfb08000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000bfb08000 - 00000000bfd0f000 (reserved)
[    0.000000]  BIOS-e820: 00000000bfd0f000 - 00000000bfd9f000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000bfd9f000 - 00000000bfdff000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000bfdff000 - 00000000bfe00000 (usable)
[    0.000000]  BIOS-e820: 00000000bfe00000 - 00000000c0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed00000 - 00000000fed00400 (reserved)
[    0.000000]  BIOS-e820: 00000000fed10000 - 00000000fed14000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed18000 - 00000000fed1a000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed1c000 - 00000000fed90000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000ff800000 - 0000000100000000 (reserved)
[    0.000000]  BIOS-e820: 0000000100000000 - 000000013c000000 (usable)
[    0.000000] DMI present.
[    0.000000] last_pfn = 0xbfe00 max_arch_pfn = 0x100000
[    0.000000] kernel direct mapping tables up to 38000000 @ 7000-c000
[    0.000000] RAMDISK: 3782b000 - 37fefe0c
[    0.000000] ACPI: RSDP 000F6550, 0024 (r2 LENOVO)
[    0.000000] ACPI: XSDT BFD6A4DE, 0094 (r1 LENOVO TP-6F        1130  LTP        0)
[    0.000000] ACPI: FACP BFD6A600, 00F4 (r3 LENOVO TP-6F        1130 LNVO        1)
[    0.000000] ACPI: DSDT BFD6A9DB, F190 (r1 LENOVO TP-6F        1130 MSFT  3000000)
[    0.000000] ACPI: FACS BFD8E000, 0040
[    0.000000] ACPI: SSDT BFD6A7B4, 0227 (r1 LENOVO TP-6F        1130 MSFT  3000000)
[    0.000000] ACPI: ECDT BFD79B6B, 0052 (r1 LENOVO TP-6F        1130 LNVO        1)
[    0.000000] ACPI: APIC BFD79BBD, 0078 (r1 LENOVO TP-6F        1130 LNVO        1)
[    0.000000] ACPI: MCFG BFD79C35, 003C (r1 LENOVO TP-6F        1130 LNVO        1)
[    0.000000] ACPI: HPET BFD79C71, 0038 (r1 LENOVO TP-6F        1130 LNVO        1)
[    0.000000] ACPI: SLIC BFD79DC2, 0176 (r1 LENOVO TP-6F        1130  LTP        0)
[    0.000000] ACPI: BOOT BFD79F38, 0028 (r1 LENOVO TP-6F        1130  LTP        1)
[    0.000000] ACPI: ASF! BFD79F60, 00A0 (r16 LENOVO TP-6F        1130 PTL         1)
[    0.000000] ACPI: SSDT BFD8D213, 054F (r1 LENOVO TP-6F        1130 INTL 20050513)
[    0.000000] ACPI: TCPA BFB07000, 0032 (r0                        0             0)
[    0.000000] ACPI: SSDT BFAD4000, 0655 (r1  PmRef    CpuPm     3000 INTL 20050624)
[    0.000000] ACPI: SSDT BFAD3000, 0274 (r1  PmRef  Cpu0Tst     3000 INTL 20050624)
[    0.000000] ACPI: SSDT BFAD2000, 0242 (r1  PmRef    ApTst     3000 INTL 20050624)
[    0.000000] 2174MB HIGHMEM available.
[    0.000000] 896MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 38000000
[    0.000000]   low ram: 00000000 - 38000000
[    0.000000]   bootmap 00008000 - 0000f000
[    0.000000] (9 early reservations) ==> bootmem [0000000000 - 0038000000]
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000]   #1 [0000001000 - 0000002000]    EX TRAMPOLINE ==> [0000001000 - 0000002000]
[    0.000000]   #2 [0000006000 - 0000007000]       TRAMPOLINE ==> [0000006000 - 0000007000]
[    0.000000]   #3 [0000100000 - 00005c29e0]    TEXT DATA BSS ==> [0000100000 - 00005c29e0]
[    0.000000]   #4 [003782b000 - 0037fefe0c]          RAMDISK ==> [003782b000 - 0037fefe0c]
[    0.000000]   #5 [00005c3000 - 00005c6000]    INIT_PG_TABLE ==> [00005c3000 - 00005c6000]
[    0.000000]   #6 [000009ac00 - 0000100000]    BIOS reserved ==> [000009ac00 - 0000100000]
[    0.000000]   #7 [0000007000 - 0000008000]          PGTABLE ==> [0000007000 - 0000008000]
[    0.000000]   #8 [0000008000 - 000000f000]          BOOTMAP ==> [0000008000 - 000000f000]
[    0.000000] found SMP MP-table at [c00f6590] 000f6590
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000000 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x00038000
[    0.000000]   HighMem  0x00038000 -> 0x000bfe00
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[5] active PFN ranges
[    0.000000]     0: 0x00000000 -> 0x0000009a
[    0.000000]     0: 0x00000100 -> 0x000bf8a1
[    0.000000]     0: 0x000bf8a7 -> 0x000bf9b7
[    0.000000]     0: 0x000bfa0f -> 0x000bfac7
[    0.000000]     0: 0x000bfdff -> 0x000bfe00
[    0.000000] On node 0 totalpages: 784900
[    0.000000] free_area_init_node: node 0, pgdat c048c680, node_mem_map c1000000
[    0.000000]   DMA zone: 3958 pages, LIFO batch:0
[    0.000000]   Normal zone: 223300 pages, LIFO batch:31
[    0.000000]   HighMem zone: 550734 pages, LIFO batch:31
[    0.000000] ACPI: PM-Timer IO Port: 0x1008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x02] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x03] disabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 1, version 32, address 0xfec00000, GSI 0-23
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
[    0.000000] PM: Registered nosave memory: 000000000009a000 - 000000000009b000
[    0.000000] PM: Registered nosave memory: 000000000009b000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000d6000
[    0.000000] PM: Registered nosave memory: 00000000000d6000 - 00000000000d8000
[    0.000000] PM: Registered nosave memory: 00000000000d8000 - 00000000000dc000
[    0.000000] PM: Registered nosave memory: 00000000000dc000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at c2000000 (gap: c0000000:20000000)
[    0.000000] PERCPU: Allocating 41628 bytes of per cpu data
[    0.000000] NR_CPUS: 64, nr_cpu_ids: 4, nr_node_ids 1
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 777992
[    0.000000] Kernel command line: root=UUID=b11aac09-e8e0-4fd4-8e6e-05fef00f0182 ro quiet splash 
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] Extended CMOS year: 2000
[    0.000000] TSC: PIT calibration confirmed by PMTIMER.
[    0.000000] TSC: using PMTIMER calibration value
[    0.000000] Detected 2792.984 MHz processor.
[    0.004000] Console: colour VGA+ 80x25
[    0.004000] console [tty0] enabled
[    0.004000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.004000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.004000] Memory: 3097140k/3143680k available (2576k kernel code, 41556k reserved, 1165k data, 424k init, 2222504k highmem)
[    0.004000] virtual kernel memory layout:
[    0.004000]     fixmap  : 0xffc77000 - 0xfffff000   (3616 kB)
[    0.004000]     pkmap   : 0xff400000 - 0xff800000   (4096 kB)
[    0.004000]     vmalloc : 0xf8800000 - 0xff3fe000   ( 107 MB)
[    0.004000]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
[    0.004000]       .init : 0xc04ad000 - 0xc0517000   ( 424 kB)
[    0.004000]       .data : 0xc03840da - 0xc04a7680   (1165 kB)
[    0.004000]       .text : 0xc0100000 - 0xc03840da   (2576 kB)
[    0.004000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.004000] CPA: page pool initialized 1 of 1 pages preallocated
[    0.004000] SLUB: Genslabs=12, HWalign=64, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
[    0.004000] hpet clockevent registered
[    0.004000] Calibrating delay loop (skipped), value calculated using timer frequency.. 5585.96 BogoMIPS (lpj=11171936)
[    0.004000] Security Framework initialized
[    0.004000] SELinux:  Disabled at boot.
[    0.004000] AppArmor: AppArmor initialized
[    0.004000] Mount-cache hash table entries: 512
[    0.004000] Initializing cgroup subsys ns
[    0.004000] Initializing cgroup subsys cpuacct
[    0.004000] Initializing cgroup subsys memory
[    0.004000] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.004000] CPU: L2 cache: 6144K
[    0.004000] CPU: Physical Processor ID: 0
[    0.004000] CPU: Processor Core ID: 0
[    0.004000] using mwait in idle threads.
[    0.004000] Checking 'hlt' instruction... OK.
[    0.017456] ACPI: Core revision 20080609
[    0.022513] ACPI: Checking initramfs for custom DSDT
[    0.272220] ENABLING IO-APIC IRQs
[    0.276170] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.315853] CPU0: Intel(R) Core(TM)2 Duo CPU     T9600  @ 2.80GHz stepping 06
[    0.316019] Booting processor 1/1 ip 6000
[    0.004000] Initializing CPU#1
[    0.004000] Calibrating delay using timer specific routine.. 5585.87 BogoMIPS (lpj=11171744)
[    0.004000] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.004000] CPU: L2 cache: 6144K
[    0.004000] CPU: Physical Processor ID: 0
[    0.004000] CPU: Processor Core ID: 1
[    0.400827] CPU1: Intel(R) Core(TM)2 Duo CPU     T9600  @ 2.80GHz stepping 06
[    0.400840] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
[    0.404039] Brought up 2 CPUs
[    0.404041] Total of 2 processors activated (11171.84 BogoMIPS).
[    0.404059] CPU0 attaching sched-domain:
[    0.404061]  domain 0: span 0-1 level MC
[    0.404063]   groups: 0 1
[    0.404067] CPU1 attaching sched-domain:
[    0.404069]  domain 0: span 0-1 level MC
[    0.404070]   groups: 1 0
[    0.404128] net_namespace: 840 bytes
[    0.404128] Booting paravirtualized kernel on bare hardware
[    0.404213] Time: 22:07:00  Date: 03/03/09
[    0.404231] NET: Registered protocol family 16
[    0.404245] EISA bus registered
[    0.404245] ACPI FADT declares the system doesn't support PCIe ASPM, so disable it
[    0.404245] ACPI: bus type pci registered
[    0.404245] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 63
[    0.404245] PCI: MCFG area at e0000000 reserved in E820
[    0.404245] PCI: Using MMCONFIG for extended config space
[    0.404245] PCI: Using configuration type 1 for base access
[    0.405254] ACPI: EC: EC description table is found, configuring boot EC
[    0.413746] ACPI: BIOS _OSI(Linux) query ignored
[    0.413748] ACPI: If "acpi_osi=Linux" works better, please notify [email]linux-acpi@vger.kernel.org[/email]
[    0.412042] ACPI: EC: non-query interrupt received, switching to interrupt mode
[    0.426059] ACPI: Interpreter enabled
[    0.426062] ACPI: (supports S0 S3 S4 S5)
[    0.426068] ACPI: Using IOAPIC for interrupt routing
[    0.448445] ACPI: EC: GPE = 0x11, I/O: command/status = 0x66, data = 0x62
[    0.448445] ACPI: EC: driver started in interrupt mode
[    0.448445] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.448445] pci 0000:00:01.0: PME# supported from D0 D3hot D3cold
[    0.448445] pci 0000:00:01.0: PME# disabled
[    0.448445] PCI: 0000:00:03.0 reg 10 64bit mmio: [fc226800, fc22680f]
[    0.448445] pci 0000:00:03.0: PME# supported from D0 D3hot D3cold
[    0.448445] pci 0000:00:03.0: PME# disabled
[    0.448445] PCI: 0000:00:19.0 reg 10 32bit mmio: [fc200000, fc21ffff]
[    0.448445] PCI: 0000:00:19.0 reg 14 32bit mmio: [fc225000, fc225fff]
[    0.448445] PCI: 0000:00:19.0 reg 18 io port: [1840, 185f]
[    0.448445] pci 0000:00:19.0: PME# supported from D0 D3hot D3cold
[    0.448445] pci 0000:00:19.0: PME# disabled
[    0.448445] PCI: 0000:00:1a.0 reg 20 io port: [1860, 187f]
[    0.448445] PCI: 0000:00:1a.1 reg 20 io port: [1880, 189f]
[    0.448486] PCI: 0000:00:1a.2 reg 20 io port: [18a0, 18bf]
[    0.448562] PCI: 0000:00:1a.7 reg 10 32bit mmio: [fc226c00, fc226fff]
[    0.448614] pci 0000:00:1a.7: PME# supported from D0 D3hot D3cold
[    0.448619] pci 0000:00:1a.7: PME# disabled
[    0.448660] PCI: 0000:00:1b.0 reg 10 64bit mmio: [fc220000, fc223fff]
[    0.448707] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    0.448711] pci 0000:00:1b.0: PME# disabled
[    0.448775] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.448779] pci 0000:00:1c.0: PME# disabled
[    0.448841] pci 0000:00:1c.1: PME# supported from D0 D3hot D3cold
[    0.448845] pci 0000:00:1c.1: PME# disabled
[    0.448908] pci 0000:00:1c.2: PME# supported from D0 D3hot D3cold
[    0.448912] pci 0000:00:1c.2: PME# disabled
[    0.448974] pci 0000:00:1c.3: PME# supported from D0 D3hot D3cold
[    0.448978] pci 0000:00:1c.3: PME# disabled
[    0.449041] pci 0000:00:1c.4: PME# supported from D0 D3hot D3cold
[    0.449045] pci 0000:00:1c.4: PME# disabled
[    0.449100] PCI: 0000:00:1d.0 reg 20 io port: [18c0, 18df]
[    0.449175] PCI: 0000:00:1d.1 reg 20 io port: [18e0, 18ff]
[    0.449249] PCI: 0000:00:1d.2 reg 20 io port: [1c00, 1c1f]
[    0.449325] PCI: 0000:00:1d.7 reg 10 32bit mmio: [fc227000, fc2273ff]
[    0.449378] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
[    0.449383] pci 0000:00:1d.7: PME# disabled
[    0.449583] PCI: 0000:00:1f.2 reg 10 io port: [1c40, 1c47]
[    0.449590] PCI: 0000:00:1f.2 reg 14 io port: [1834, 1837]
[    0.449596] PCI: 0000:00:1f.2 reg 18 io port: [1838, 183f]
[    0.449603] PCI: 0000:00:1f.2 reg 1c io port: [1830, 1833]
[    0.449610] PCI: 0000:00:1f.2 reg 20 io port: [1c20, 1c3f]
[    0.449616] PCI: 0000:00:1f.2 reg 24 32bit mmio: [fc226000, fc2267ff]
[    0.449648] pci 0000:00:1f.2: PME# supported from D3hot
[    0.449652] pci 0000:00:1f.2: PME# disabled
[    0.449675] PCI: 0000:00:1f.3 reg 10 64bit mmio: [fc227400, fc2274ff]
[    0.449692] PCI: 0000:00:1f.3 reg 20 io port: [1c60, 1c7f]
[    0.449745] PCI: 0000:01:00.0 reg 10 32bit mmio: [d0000000, dfffffff]
[    0.449752] PCI: 0000:01:00.0 reg 14 io port: [2000, 20ff]
[    0.449759] PCI: 0000:01:00.0 reg 18 32bit mmio: [cfff0000, cfffffff]
[    0.449781] PCI: 0000:01:00.0 reg 30 32bit mmio: [0, 1ffff]
[    0.449800] pci 0000:01:00.0: supports D1
[    0.449801] pci 0000:01:00.0: supports D2
[    0.449845] PCI: bridge 0000:00:01.0 io port: [2000, 2fff]
[    0.449848] PCI: bridge 0000:00:01.0 32bit mmio: [cff00000, cfffffff]
[    0.449851] PCI: bridge 0000:00:01.0 64bit mmio pref: [d0000000, dfffffff]
[    0.449996] PCI: 0000:03:00.0 reg 10 64bit mmio: [f4200000, f4201fff]
[    0.450089] pci 0000:03:00.0: PME# supported from D0 D3hot D3cold
[    0.450096] pci 0000:03:00.0: PME# disabled
[    0.450144] PCI: bridge 0000:00:1c.1 32bit mmio: [f4200000, f42fffff]
[    0.450218] PCI: 0000:04:00.0 reg 10 32bit mmio: [f4300000, f43003ff]
[    0.450238] PCI: 0000:04:00.0 reg 18 io port: [3000, 30ff]
[    0.450278] PCI: 0000:04:00.0 reg 30 32bit mmio: [0, ffff]
[    0.450358] PCI: bridge 0000:00:1c.2 io port: [3000, 3fff]
[    0.450362] PCI: bridge 0000:00:1c.2 32bit mmio: [f4300000, f43fffff]
[    0.450420] PCI: bridge 0000:00:1c.3 io port: [4000, 4fff]
[    0.450424] PCI: bridge 0000:00:1c.3 32bit mmio: [f8000000, f9ffffff]
[    0.450431] PCI: bridge 0000:00:1c.3 64bit mmio pref: [f4000000, f40fffff]
[    0.450484] PCI: bridge 0000:00:1c.4 io port: [5000, 5fff]
[    0.450488] PCI: bridge 0000:00:1c.4 32bit mmio: [fa000000, fbffffff]
[    0.450495] PCI: bridge 0000:00:1c.4 64bit mmio pref: [f4100000, f41fffff]
[    0.450542] PCI: 0000:15:00.0 reg 10 32bit mmio: [f4400000, f4400fff]
[    0.450561] pci 0000:15:00.0: supports D1
[    0.450563] pci 0000:15:00.0: supports D2
[    0.450564] pci 0000:15:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.450569] pci 0000:15:00.0: PME# disabled
[    0.450608] PCI: 0000:15:00.1 reg 10 32bit mmio: [f4401000, f44017ff]
[    0.450670] pci 0000:15:00.1: supports D1
[    0.450671] pci 0000:15:00.1: supports D2
[    0.450672] pci 0000:15:00.1: PME# supported from D0 D1 D2 D3hot D3cold
[    0.450677] pci 0000:15:00.1: PME# disabled
[    0.450717] PCI: 0000:15:00.2 reg 10 32bit mmio: [f4401800, f44018ff]
[    0.450779] pci 0000:15:00.2: supports D1
[    0.450780] pci 0000:15:00.2: supports D2
[    0.450781] pci 0000:15:00.2: PME# supported from D0 D1 D2 D3hot D3cold
[    0.450786] pci 0000:15:00.2: PME# disabled
[    0.450825] PCI: 0000:15:00.3 reg 10 32bit mmio: [f4401c00, f4401cff]
[    0.450887] pci 0000:15:00.3: supports D1
[    0.450888] pci 0000:15:00.3: supports D2
[    0.450890] pci 0000:15:00.3: PME# supported from D0 D1 D2 D3hot D3cold
[    0.450895] pci 0000:15:00.3: PME# disabled
[    0.450934] PCI: 0000:15:00.4 reg 10 32bit mmio: [f4402000, f44020ff]
[    0.450995] pci 0000:15:00.4: supports D1
[    0.450996] pci 0000:15:00.4: supports D2
[    0.450998] pci 0000:15:00.4: PME# supported from D0 D1 D2 D3hot D3cold
[    0.451003] pci 0000:15:00.4: PME# disabled
[    0.451042] PCI: 0000:15:00.5 reg 10 32bit mmio: [f4402400, f44024ff]
[    0.451104] pci 0000:15:00.5: supports D1
[    0.451105] pci 0000:15:00.5: supports D2
[    0.451106] pci 0000:15:00.5: PME# supported from D0 D1 D2 D3hot D3cold
[    0.451111] pci 0000:15:00.5: PME# disabled
[    0.451174] pci 0000:00:1e.0: transparent bridge
[    0.451178] PCI: bridge 0000:00:1e.0 io port: [6000, 9fff]
[    0.451182] PCI: bridge 0000:00:1e.0 32bit mmio: [f4400000, f7ffffff]
[    0.451189] PCI: bridge 0000:00:1e.0 64bit mmio pref: [f0000000, f3ffffff]
[    0.451246] bus 00 -> node 0
[    0.451252] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.452246] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.AGP_._PRT]
[    0.452366] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.EXP0._PRT]
[    0.452490] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.EXP1._PRT]
[    0.452614] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.EXP2._PRT]
[    0.452737] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.EXP3._PRT]
[    0.452863] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.EXP4._PRT]
[    0.452988] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCI1._PRT]
[    0.456171] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 9 10 *11)
[    0.456370] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 9 10 *11)
[    0.456567] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 9 10 *11)
[    0.456764] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 9 10 *11)
[    0.456963] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 9 10 *11)
[    0.457160] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 9 10 *11)
[    0.457357] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 9 10 *11)
[    0.457553] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 9 10 *11)
[    0.457648] ACPI: Power Resource [PUBS] (on)
[    0.457648] Linux Plug and Play Support v0.97 (c) Adam Belay
[    0.457648] pnp: PnP ACPI init
[    0.457648] ACPI: bus type pnp registered
[    0.472523] pnp: PnP ACPI: found 10 devices
[    0.472525] ACPI: ACPI bus type pnp unregistered
[    0.472527] PnPBIOS: Disabled by ACPI PNP
[    0.472769] PCI: Using ACPI for IRQ routing
[    0.476044] NET: Registered protocol family 8
[    0.476046] NET: Registered protocol family 20
[    0.476063] NetLabel: Initializing
[    0.476063] NetLabel:  domain hash size = 128
[    0.476063] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.476063] NetLabel:  unlabeled traffic allowed by default
[    0.476063] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0
[    0.476063] hpet0: 4 64-bit timers, 14318180 Hz
[    0.477686] tracer: 772 pages allocated for 65536 entries of 48 bytes
[    0.477688]    actual entries 65620
[    0.477748] AppArmor: AppArmor Filesystem Enabled
[    0.477772] ACPI: RTC can wake from S4
[    0.480866] system 00:00: iomem range 0x0-0x9ffff could not be reserved
[    0.480868] system 00:00: iomem range 0xc0000-0xc3fff could not be reserved
[    0.480870] system 00:00: iomem range 0xc4000-0xc7fff could not be reserved
[    0.480872] system 00:00: iomem range 0xc8000-0xcbfff could not be reserved
[    0.480874] system 00:00: iomem range 0xcc000-0xcffff could not be reserved
[    0.480876] system 00:00: iomem range 0xd0000-0xd3fff could not be reserved
[    0.480878] system 00:00: iomem range 0xd4000-0xd7fff could not be reserved
[    0.480880] system 00:00: iomem range 0xdc000-0xdffff could not be reserved
[    0.480882] system 00:00: iomem range 0xe0000-0xe3fff could not be reserved
[    0.480884] system 00:00: iomem range 0xe4000-0xe7fff could not be reserved
[    0.480886] system 00:00: iomem range 0xe8000-0xebfff could not be reserved
[    0.480888] system 00:00: iomem range 0xec000-0xeffff could not be reserved
[    0.480891] system 00:00: iomem range 0xf0000-0xfffff could not be reserved
[    0.480893] system 00:00: iomem range 0x100000-0xbfffffff could not be reserved
[    0.480895] system 00:00: iomem range 0xfec00000-0xfed3ffff could not be reserved
[    0.480897] system 00:00: iomem range 0xfed4c000-0xffffffff could not be reserved
[    0.480903] system 00:02: ioport range 0x164e-0x164f has been reserved
[    0.480905] system 00:02: ioport range 0x1000-0x107f has been reserved
[    0.480907] system 00:02: ioport range 0x1180-0x11ff has been reserved
[    0.480909] system 00:02: ioport range 0x800-0x80f has been reserved
[    0.480911] system 00:02: ioport range 0x15e0-0x15ef has been reserved
[    0.480915] system 00:02: ioport range 0x1600-0x1641 has been reserved
[    0.480917] system 00:02: ioport range 0x1600-0x161b has been reserved
[    0.480919] system 00:02: iomem range 0xe0000000-0xefffffff could not be reserved
[    0.480921] system 00:02: iomem range 0xfed1c000-0xfed1ffff could not be reserved
[    0.480924] system 00:02: iomem range 0xfed10000-0xfed13fff could not be reserved
[    0.480926] system 00:02: iomem range 0xfed18000-0xfed18fff could not be reserved
[    0.480928] system 00:02: iomem range 0xfed19000-0xfed19fff could not be reserved
[    0.480930] system 00:02: iomem range 0xfed45000-0xfed4bfff could not be reserved
[    0.500860] Switched to high resolution mode on CPU 1
[    0.504031] Switched to high resolution mode on CPU 0
[    0.515822] pci 0000:00:01.0: PCI bridge, secondary bus 0000:01
[    0.515824] pci 0000:00:01.0:   IO window: 0x2000-0x2fff
[    0.515827] pci 0000:00:01.0:   MEM window: 0xcff00000-0xcfffffff
[    0.515830] pci 0000:00:01.0:   PREFETCH window: 0x000000d0000000-0x000000dfffffff
[    0.515833] pci 0000:00:1c.0: PCI bridge, secondary bus 0000:02
[    0.515835] pci 0000:00:1c.0:   IO window: disabled
[    0.515840] pci 0000:00:1c.0:   MEM window: disabled
[    0.515844] pci 0000:00:1c.0:   PREFETCH window: disabled
[    0.515851] pci 0000:00:1c.1: PCI bridge, secondary bus 0000:03
[    0.515852] pci 0000:00:1c.1:   IO window: disabled
[    0.515857] pci 0000:00:1c.1:   MEM window: 0xf4200000-0xf42fffff
[    0.515861] pci 0000:00:1c.1:   PREFETCH window: disabled
[    0.515868] pci 0000:00:1c.2: PCI bridge, secondary bus 0000:04
[    0.515871] pci 0000:00:1c.2:   IO window: 0x3000-0x3fff
[    0.515876] pci 0000:00:1c.2:   MEM window: 0xf4300000-0xf43fffff
[    0.515880] pci 0000:00:1c.2:   PREFETCH window: 0x000000c2000000-0x000000c20fffff
[    0.515887] pci 0000:00:1c.3: PCI bridge, secondary bus 0000:05
[    0.515890] pci 0000:00:1c.3:   IO window: 0x4000-0x4fff
[    0.515895] pci 0000:00:1c.3:   MEM window: 0xf8000000-0xf9ffffff
[    0.515899] pci 0000:00:1c.3:   PREFETCH window: 0x000000f4000000-0x000000f40fffff
[    0.515906] pci 0000:00:1c.4: PCI bridge, secondary bus 0000:0d
[    0.515909] pci 0000:00:1c.4:   IO window: 0x5000-0x5fff
[    0.515914] pci 0000:00:1c.4:   MEM window: 0xfa000000-0xfbffffff
[    0.515918] pci 0000:00:1c.4:   PREFETCH window: 0x000000f4100000-0x000000f41fffff
[    0.515927] pci 0000:15:00.0: CardBus bridge, secondary bus 0000:16
[    0.515928] pci 0000:15:00.0:   IO window: 0x006000-0x0060ff
[    0.515933] pci 0000:15:00.0:   IO window: 0x006400-0x0064ff
[    0.515938] pci 0000:15:00.0:   PREFETCH window: 0xf0000000-0xf3ffffff
[    0.515943] pci 0000:15:00.0:   MEM window: 0xc4000000-0xc7ffffff
[    0.515948] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:15
[    0.515951] pci 0000:00:1e.0:   IO window: 0x6000-0x9fff
[    0.515956] pci 0000:00:1e.0:   MEM window: 0xf4400000-0xf7ffffff
[    0.515960] pci 0000:00:1e.0:   PREFETCH window: 0x000000f0000000-0x000000f3ffffff
[    0.515972] pci 0000:00:01.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.515975] pci 0000:00:01.0: setting latency timer to 64
[    0.515982] pci 0000:00:1c.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    0.515987] pci 0000:00:1c.0: setting latency timer to 64
[    0.515995] pci 0000:00:1c.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[    0.515999] pci 0000:00:1c.1: setting latency timer to 64
[    0.516007] pci 0000:00:1c.2: PCI INT C -> GSI 22 (level, low) -> IRQ 22
[    0.516011] pci 0000:00:1c.2: setting latency timer to 64
[    0.516019] pci 0000:00:1c.3: PCI INT D -> GSI 23 (level, low) -> IRQ 23
[    0.516023] pci 0000:00:1c.3: setting latency timer to 64
[    0.516031] pci 0000:00:1c.4: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    0.516035] pci 0000:00:1c.4: setting latency timer to 64
[    0.516042] pci 0000:00:1e.0: setting latency timer to 64
[    0.516051] pci 0000:15:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.516057] bus: 00 index 0 io port: [0, ffff]
[    0.516058] bus: 00 index 1 mmio: [0, ffffffff]
[    0.516060] bus: 01 index 0 io port: [2000, 2fff]
[    0.516061] bus: 01 index 1 mmio: [cff00000, cfffffff]
[    0.516063] bus: 01 index 2 mmio: [d0000000, dfffffff]
[    0.516064] bus: 01 index 3 mmio: [0, 0]
[    0.516065] bus: 02 index 0 mmio: [0, 0]
[    0.516067] bus: 02 index 1 mmio: [0, 0]
[    0.516068] bus: 02 index 2 mmio: [0, 0]
[    0.516069] bus: 02 index 3 mmio: [0, 0]
[    0.516070] bus: 03 index 0 mmio: [0, 0]
[    0.516072] bus: 03 index 1 mmio: [f4200000, f42fffff]
[    0.516073] bus: 03 index 2 mmio: [0, 0]
[    0.516074] bus: 03 index 3 mmio: [0, 0]
[    0.516076] bus: 04 index 0 io port: [3000, 3fff]
[    0.516077] bus: 04 index 1 mmio: [f4300000, f43fffff]
[    0.516079] bus: 04 index 2 mmio: [c2000000, c20fffff]
[    0.516080] bus: 04 index 3 mmio: [0, 0]
[    0.516081] bus: 05 index 0 io port: [4000, 4fff]
[    0.516083] bus: 05 index 1 mmio: [f8000000, f9ffffff]
[    0.516084] bus: 05 index 2 mmio: [f4000000, f40fffff]
[    0.516085] bus: 05 index 3 mmio: [0, 0]
[    0.516087] bus: 0d index 0 io port: [5000, 5fff]
[    0.516088] bus: 0d index 1 mmio: [fa000000, fbffffff]
[    0.516090] bus: 0d index 2 mmio: [f4100000, f41fffff]
[    0.516091] bus: 0d index 3 mmio: [0, 0]
[    0.516092] bus: 15 index 0 io port: [6000, 9fff]
[    0.516094] bus: 15 index 1 mmio: [f4400000, f7ffffff]
[    0.516095] bus: 15 index 2 mmio: [f0000000, f3ffffff]
[    0.516097] bus: 15 index 3 io port: [0, ffff]
[    0.516098] bus: 15 index 4 mmio: [0, ffffffff]
[    0.516099] bus: 16 index 0 io port: [6000, 60ff]
[    0.516101] bus: 16 index 1 io port: [6400, 64ff]
[    0.516102] bus: 16 index 2 mmio: [f0000000, f3ffffff]
[    0.516104] bus: 16 index 3 mmio: [c4000000, c7ffffff]
[    0.516109] NET: Registered protocol family 2
[    0.528537] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.528698] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.528925] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.529034] TCP: Hash tables configured (established 131072 bind 65536)
[    0.529036] TCP reno registered
[    0.532545] NET: Registered protocol family 1
[    0.532609] checking if image is initramfs... it is
[    1.020676] Freeing initrd memory: 7955k freed
[    1.020930] Simple Boot Flag at 0x35 set to 0x1
[    1.021462] audit: initializing netlink socket (disabled)
[    1.021474] type=2000 audit(1236118020.020:1): initialized
[    1.025807] highmem bounce pool size: 64 pages
[    1.025811] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    1.027334] VFS: Disk quotas dquot_6.5.1
[    1.027389] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    1.027464] msgmni has been set to 1725
[    1.027548] io scheduler noop registered
[    1.027550] io scheduler anticipatory registered
[    1.027552] io scheduler deadline registered
[    1.027560] io scheduler cfq registered (default)
[    1.027706] pci 0000:01:00.0: Boot video device
[    1.027800] pcieport-driver 0000:00:01.0: setting latency timer to 64
[    1.027828] pcieport-driver 0000:00:01.0: found MSI capability
[    1.027852] pci_express 0000:00:01.0:pcie00: allocate port service
[    1.027881] pci_express 0000:00:01.0:pcie02: allocate port service
[    1.027907] pci_express 0000:00:01.0:pcie03: allocate port service
[    1.027970] pcieport-driver 0000:00:1c.0: setting latency timer to 64
[    1.028013] pcieport-driver 0000:00:1c.0: found MSI capability
[    1.028055] pci_express 0000:00:1c.0:pcie00: allocate port service
[    1.028082] pci_express 0000:00:1c.0:pcie02: allocate port service
[    1.028107] pci_express 0000:00:1c.0:pcie03: allocate port service
[    1.028197] pcieport-driver 0000:00:1c.1: setting latency timer to 64
[    1.028241] pcieport-driver 0000:00:1c.1: found MSI capability
[    1.028282] pci_express 0000:00:1c.1:pcie00: allocate port service
[    1.028308] pci_express 0000:00:1c.1:pcie02: allocate port service
[    1.028334] pci_express 0000:00:1c.1:pcie03: allocate port service
[    1.028423] pcieport-driver 0000:00:1c.2: setting latency timer to 64
[    1.028466] pcieport-driver 0000:00:1c.2: found MSI capability
[    1.028511] pci_express 0000:00:1c.2:pcie00: allocate port service
[    1.028538] pci_express 0000:00:1c.2:pcie02: allocate port service
[    1.028563] pci_express 0000:00:1c.2:pcie03: allocate port service
[    1.028651] pcieport-driver 0000:00:1c.3: setting latency timer to 64
[    1.028695] pcieport-driver 0000:00:1c.3: found MSI capability
[    1.028736] pci_express 0000:00:1c.3:pcie00: allocate port service
[    1.028762] pci_express 0000:00:1c.3:pcie02: allocate port service
[    1.028789] pci_express 0000:00:1c.3:pcie03: allocate port service
[    1.028878] pcieport-driver 0000:00:1c.4: setting latency timer to 64
[    1.028921] pcieport-driver 0000:00:1c.4: found MSI capability
[    1.028963] pci_express 0000:00:1c.4:pcie00: allocate port service
[    1.028989] pci_express 0000:00:1c.4:pcie02: allocate port service
[    1.029016] pci_express 0000:00:1c.4:pcie03: allocate port service
[    1.029266] isapnp: Scanning for PnP cards...
[    1.383350] isapnp: No Plug & Play device found
[    1.404907] hpet_resources: 0xfed00000 is busy
[    1.404969] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
[    1.406506] brd: module loaded
[    1.406554] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[    1.406634] PNP: PS/2 Controller [PNP0303:KBD,PNP0f13:MOU] at 0x60,0x64 irq 1,12
[    1.416257] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.416261] serio: i8042 AUX port at 0x60,0x64 irq 12
[    1.420072] mice: PS/2 mouse device common for all mice
[    1.420152] rtc_cmos 00:07: rtc core: registered rtc_cmos as rtc0
[    1.420178] rtc0: alarms up to one month, y3k, hpet irqs
[    1.420258] EISA: Probing bus 0 at eisa.0
[    1.420264] Cannot allocate resource for EISA slot 1
[    1.420266] Cannot allocate resource for EISA slot 2
[    1.420267] Cannot allocate resource for EISA slot 3
[    1.420269] Cannot allocate resource for EISA slot 4
[    1.420270] Cannot allocate resource for EISA slot 5
[    1.420272] Cannot allocate resource for EISA slot 6
[    1.420273] Cannot allocate resource for EISA slot 7
[    1.420274] Cannot allocate resource for EISA slot 8
[    1.420276] EISA: Detected 0 cards.
[    1.420278] cpuidle: using governor ladder
[    1.420280] cpuidle: using governor menu
[    1.420624] TCP cubic registered
[    1.420643] Using IPI No-Shortcut mode
[    1.420755] registered taskstats version 1
[    1.420867]   Magic number: 1:604:147
[    1.420875] tty ttyp1: hash matches
[    1.420889] acpi device:18: hash matches
[    1.420918] rtc_cmos 00:07: setting system clock to 2009-03-03 22:07:01 UTC (1236118021)
[    1.420920] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.420922] EDD information not available.
[    1.421157] Freeing unused kernel memory: 424k freed
[    1.421183] Write protecting the kernel text: 2580k
[    1.421202] Write protecting the kernel read-only data: 940k
[    1.436526] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[    1.540043] fuse init (API version 7.9)
[    1.588492] ACPI: SSDT BFAD7AA0, 030A (r1  PmRef  Cpu0Ist     3000 INTL 20050624)
[    1.588926] ACPI: SSDT BFAD5020, 087A (r1  PmRef  Cpu0Cst     3001 INTL 20050624)
[    1.591219] Monitor-Mwait will be used to enter C-1 state
[    1.591221] Monitor-Mwait will be used to enter C-2 state
[    1.591223] Monitor-Mwait will be used to enter C-3 state
[    1.591344] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[    1.591380] processor ACPI0007:00: registered as cooling_device0
[    1.591383] ACPI: Processor [CPU0] (supports 8 throttling states)
[    1.591777] ACPI: SSDT BFAD6CA0, 01CF (r1  PmRef    ApIst     3000 INTL 20050624)
[    1.592227] ACPI: SSDT BFAD6F20, 008D (r1  PmRef    ApCst     3000 INTL 20050624)
[    1.599998] Marking TSC unstable due to TSC halts in idle
[    1.697035] ACPI: CPU1 (power states: C1[C1] C2[C2] C3[C3])
[    1.697087] processor ACPI0007:01: registered as cooling_device1
[    1.697090] ACPI: Processor [CPU1] (supports 8 throttling states)
[    1.700871] thermal LNXTHERM:01: registered as thermal_zone0
[    1.704275] ACPI: Thermal Zone [THM0] (48 C)
[    1.705271] thermal LNXTHERM:02: registered as thermal_zone1
[    1.706513] ACPI: Thermal Zone [THM1] (46 C)
[    1.905331] usbcore: registered new interface driver usbfs
[    1.905347] usbcore: registered new interface driver hub
[    1.905368] usbcore: registered new device driver usb
[    1.912590] USB Universal Host Controller Interface driver v3.0
[    1.913157] uhci_hcd 0000:00:1a.0: power state changed by ACPI to D0
[    1.913165] uhci_hcd 0000:00:1a.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    1.913172] uhci_hcd 0000:00:1a.0: setting latency timer to 64
[    1.913175] uhci_hcd 0000:00:1a.0: UHCI Host Controller
[    1.913204] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 1
[    1.913240] uhci_hcd 0000:00:1a.0: irq 20, io base 0x00001860
[    1.913339] usb usb1: configuration #1 chosen from 1 choice
[    1.913357] hub 1-0:1.0: USB hub found
[    1.913362] hub 1-0:1.0: 2 ports detected
[    1.973961] Warning! ehci_hcd should always be loaded before uhci_hcd and ohci_hcd, not after
[    1.992163] e1000e: Intel(R) PRO/1000 Network Driver - 0.3.3.3-k6
[    1.992165] e1000e: Copyright (c) 1999-2008 Intel Corporation.
[    1.996344] ACPI: ACPI Dock Station Driver
[    2.010548] SCSI subsystem initialized
[    2.051090] libata version 3.00 loaded.
[    2.120186] uhci_hcd 0000:00:1a.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[    2.120194] uhci_hcd 0000:00:1a.1: setting latency timer to 64
[    2.120197] uhci_hcd 0000:00:1a.1: UHCI Host Controller
[    2.120215] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 2
[    2.120247] uhci_hcd 0000:00:1a.1: irq 21, io base 0x00001880
[    2.120313] usb usb2: configuration #1 chosen from 1 choice
[    2.120332] hub 2-0:1.0: USB hub found
[    2.120340] hub 2-0:1.0: 2 ports detected
[    2.232071] usb 1-1: new low speed USB device using uhci_hcd and address 2
[    2.329128] uhci_hcd 0000:00:1a.2: power state changed by ACPI to D0
[    2.329134] uhci_hcd 0000:00:1a.2: PCI INT C -> GSI 22 (level, low) -> IRQ 22
[    2.329141] uhci_hcd 0000:00:1a.2: setting latency timer to 64
[    2.329144] uhci_hcd 0000:00:1a.2: UHCI Host Controller
[    2.329163] uhci_hcd 0000:00:1a.2: new USB bus registered, assigned bus number 3
[    2.329192] uhci_hcd 0000:00:1a.2: irq 22, io base 0x000018a0
[    2.329255] usb usb3: configuration #1 chosen from 1 choice
[    2.329273] hub 3-0:1.0: USB hub found
[    2.329278] hub 3-0:1.0: 2 ports detected
[    2.414434] usb 1-1: configuration #1 chosen from 1 choice
[    2.500066] Clocksource tsc unstable (delta = -261127304 ns)
[    2.528111] usb 2-1: new full speed USB device using uhci_hcd and address 2
[    2.536398] e1000e 0000:00:19.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    2.536405] e1000e 0000:00:19.0: setting latency timer to 64
[    2.626507] 0000:00:19.0: eth0: (PCI Express:2.5GB/s:Width x1) 00:1c:25:95:b8:56
[    2.626509] 0000:00:19.0: eth0: Intel(R) PRO/1000 Network Connection
[    2.626536] 0000:00:19.0: eth0: MAC: 5, PHY: 8, PBA No: 1008ff-0ff
[    2.627597] ehci_hcd 0000:00:1a.7: power state changed by ACPI to D0
[    2.627604] ehci_hcd 0000:00:1a.7: PCI INT D -> GSI 23 (level, low) -> IRQ 23
[    2.627610] ehci_hcd 0000:00:1a.7: setting latency timer to 64
[    2.627613] ehci_hcd 0000:00:1a.7: EHCI Host Controller
[    2.627631] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 4
[    2.631527] ehci_hcd 0000:00:1a.7: debug port 1
[    2.631532] ehci_hcd 0000:00:1a.7: cache line size of 32 is not supported
[    2.631540] ehci_hcd 0000:00:1a.7: irq 23, io mem 0xfc226c00
[    2.641784] Monitor-Mwait will be used to enter C-3 state
[    2.652106] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    2.652194] usb usb4: configuration #1 chosen from 1 choice
[    2.652226] hub 4-0:1.0: USB hub found
[    2.652234] hub 4-0:1.0: 6 ports detected
[    2.860892] uhci_hcd 0000:00:1d.0: power state changed by ACPI to D0
[    2.860899] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    2.860907] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    2.860911] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    2.860945] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 5
[    2.860981] uhci_hcd 0000:00:1d.0: irq 16, io base 0x000018c0
[    2.861080] usb usb5: configuration #1 chosen from 1 choice
[    2.861111] hub 5-0:1.0: USB hub found
[    2.861118] hub 5-0:1.0: 2 ports detected
[    2.964250] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    2.964256] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    2.964259] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    2.964276] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 6
[    2.964303] uhci_hcd 0000:00:1d.1: irq 17, io base 0x000018e0
[    2.964362] usb usb6: configuration #1 chosen from 1 choice
[    2.964385] hub 6-0:1.0: USB hub found
[    2.964390] hub 6-0:1.0: 2 ports detected
[    3.052609] usb 2-1: device not accepting address 2, error -71
[    3.108091] hub 2-0:1.0: unable to enumerate USB device on port 1
[    3.173026] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    3.173031] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    3.173034] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    3.173051] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 7
[    3.173078] uhci_hcd 0000:00:1d.2: irq 18, io base 0x00001c00
[    3.173136] usb usb7: configuration #1 chosen from 1 choice
[    3.173164] hub 7-0:1.0: USB hub found
[    3.173168] hub 7-0:1.0: 2 ports detected
[    3.277707] ehci_hcd 0000:00:1d.7: power state changed by ACPI to D0
[    3.277715] ehci_hcd 0000:00:1d.7: PCI INT D -> GSI 19 (level, low) -> IRQ 19
[    3.277722] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    3.277725] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    3.277743] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 8
[    3.281646] ehci_hcd 0000:00:1d.7: debug port 1
[    3.281652] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
[    3.281660] ehci_hcd 0000:00:1d.7: irq 19, io mem 0xfc227000
[    3.296013] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    3.296070] usb usb8: configuration #1 chosen from 1 choice
[    3.296088] hub 8-0:1.0: USB hub found
[    3.296093] hub 8-0:1.0: 6 ports detected
[    3.504536] ahci 0000:00:1f.2: version 3.0
[    3.504547] ahci 0000:00:1f.2: PCI INT B -> GSI 16 (level, low) -> IRQ 16
[    3.504631] ahci 0000:00:1f.2: AHCI 0001.0200 32 slots 4 ports 3 Gbps 0x3 impl SATA mode
[    3.504634] ahci 0000:00:1f.2: flags: 64bit ncq sntf stag pm led clo pio slum part 
[    3.504639] ahci 0000:00:1f.2: setting latency timer to 64
[    3.504779] scsi0 : ahci
[    3.505006] scsi1 : ahci
[    3.505219] scsi2 : ahci
[    3.505434] scsi3 : ahci
[    3.506150] ata1: SATA max UDMA/133 abar m2048@0xfc226000 port 0xfc226100 irq 217
[    3.506153] ata2: SATA max UDMA/133 abar m2048@0xfc226000 port 0xfc226180 irq 217
[    3.506154] ata3: DUMMY
[    3.506155] ata4: DUMMY
[    3.756063] usb 4-6: new high speed USB device using ehci_hcd and address 5
[    3.824072] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    3.825301] ata1.00: ACPI cmd ef/02:00:00:00:00:a0 succeeded
[    3.825303] ata1.00: ACPI cmd f5/00:00:00:00:00:a0 filtered out
[    3.825543] ata1.00: ACPI cmd ef/5f:00:00:00:00:a0 succeeded
[    3.825545] ata1.00: ACPI cmd ef/10:03:00:00:00:a0 filtered out
[    3.826527] ata1.00: ATA-8: HITACHI HTS722016K9SA00, DCDZC75A, max UDMA/133
[    3.826529] ata1.00: 312581808 sectors, multi 16: LBA48 NCQ (depth 31/32)
[    3.827976] ata1.00: ACPI cmd ef/02:00:00:00:00:a0 succeeded
[    3.827978] ata1.00: ACPI cmd f5/00:00:00:00:00:a0 filtered out
[    3.828211] ata1.00: ACPI cmd ef/5f:00:00:00:00:a0 succeeded
[    3.828213] ata1.00: ACPI cmd ef/10:03:00:00:00:a0 filtered out
[    3.829192] ata1.00: configured for UDMA/133
[    3.846283] ata1.00: configured for UDMA/133
[    3.846285] ata1: EH complete
[    3.894138] usb 4-6: configuration #1 chosen from 1 choice
[    3.895012] usbcore: registered new interface driver hiddev
[    3.895166] usb 1-1: USB disconnect, address 2
[    4.132580] usb 1-1: new low speed USB device using uhci_hcd and address 3
[    4.164099] ata2: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    4.166049] ata2.00: ACPI cmd ef/02:00:00:00:00:a0 succeeded
[    4.166052] ata2.00: ACPI cmd f5/00:00:00:00:00:a0 filtered out
[    4.166053] ata2.00: ACPI cmd ef/10:03:00:00:00:a0 filtered out
[    4.166248] ata2.00: ATA-7: SAMSUNG SSD RBX Series 64GB, PS105D14, max UDMA/100
[    4.166250] ata2.00: 125045424 sectors, multi 16: LBA48 
[    4.168005] ata2.00: ACPI cmd ef/02:00:00:00:00:a0 succeeded
[    4.168007] ata2.00: ACPI cmd f5/00:00:00:00:00:a0 filtered out
[    4.168009] ata2.00: ACPI cmd ef/10:03:00:00:00:a0 filtered out
[    4.168207] ata2.00: configured for UDMA/100
[    4.184580] ata2.00: configured for UDMA/100
[    4.184583] ata2: EH complete
[    4.184806] scsi 0:0:0:0: Direct-Access     ATA      HITACHI HTS72201 DCDZ PQ: 0 ANSI: 5
[    4.184896] scsi 1:0:0:0: Direct-Access     ATA      SAMSUNG SSD RBX  PS10 PQ: 0 ANSI: 5
[    4.184972] ohci1394 0000:15:00.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    4.237749] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[17]  MMIO=[f4401000-f44017ff]  Max Packet=[2048]  IR/IT contexts=[4/4]
[    4.249533] scsi 0:0:0:0: Attached scsi generic sg0 type 0
[    4.249557] scsi 1:0:0:0: Attached scsi generic sg1 type 0
[    4.271455] Driver 'sd' needs updating - please use bus_type methods
[    4.271510] sd 0:0:0:0: [sda] 312581808 512-byte hardware sectors (160042 MB)
[    4.271521] sd 0:0:0:0: [sda] Write Protect is off
[    4.271523] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    4.271540] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.271585] sd 0:0:0:0: [sda] 312581808 512-byte hardware sectors (160042 MB)
[    4.271600] sd 0:0:0:0: [sda] Write Protect is off
[    4.271602] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    4.271618] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.271620]  sda: sda1 sda2 sda3 sda4 < sda5 sda6 sda7 >
[    4.320307] sd 0:0:0:0: [sda] Attached SCSI disk
[    4.320347] sd 1:0:0:0: [sdb] 125045424 512-byte hardware sectors (64023 MB)
[    4.320358] sd 1:0:0:0: [sdb] Write Protect is off
[    4.320360] sd 1:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[    4.320378] sd 1:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.320417] sd 1:0:0:0: [sdb] 125045424 512-byte hardware sectors (64023 MB)
[    4.320427] sd 1:0:0:0: [sdb] Write Protect is off
[    4.320429] sd 1:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[    4.320446] sd 1:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.320448]  sdb: sdb1 sdb2
[    4.321660] sd 1:0:0:0: [sdb] Attached SCSI disk
[    4.362385] usb 1-1: configuration #1 chosen from 1 choice
[    4.604680] usb 2-1: new full speed USB device using uhci_hcd and address 4
[    4.775498] usb 2-1: configuration #1 chosen from 1 choice
[    5.016072] usb 2-2: new full speed USB device using uhci_hcd and address 5
[    5.182371] usb 2-2: configuration #1 chosen from 1 choice
[    5.424082] usb 8-4: new high speed USB device using ehci_hcd and address 2
[    5.512374] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[00016c00006a68d3]
[    5.634911] usb 8-4: configuration #1 chosen from 2 choices
[    5.708514] input: Microsoft Microsoft 3-Button Mouse with IntelliEye(TM) as /devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1:1.0/input/input2
[    5.708661] input,hidraw0: USB HID v1.10 Mouse [Microsoft Microsoft 3-Button Mouse with IntelliEye(TM)] on usb-0000:00:1a.0-1
[    5.708680] usbcore: registered new interface driver usbhid
[    5.708682] usbhid: v2.6:USB HID core driver
[    5.743954] PM: Starting manual resume from disk
[    5.743956] PM: Resume from partition 8:6
[    5.743957] PM: Checking hibernation image.
[    5.744134] PM: Resume from disk failed.
[    5.773692] kjournald starting.  Commit interval 5 seconds
[    5.773702] EXT3-fs: mounted filesystem with ordered data mode.
[   11.809916] udevd version 124 started
[   12.056085] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   12.144051] Linux agpgart interface v0.103
[   12.285126] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   12.326179] input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input3
[   12.352018] ACPI: Power Button (FF) [PWRF]
[   12.352069] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input4
[   12.352681] ACPI: Lid Switch [LID]
[   12.352730] input: Sleep Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input5
[   12.372516] ACPI: Sleep Button (CM) [SLPB]
[   12.372667] ACPI: WMI: Mapper loaded
[   12.390702] ACPI: \_SB_.PCI0.SATA.PRT1: found ejectable bay
[   12.390706] ACPI: \_SB_.PCI0.SATA.PRT1: Adding notify handler
[   12.404675] ACPI: Error installing bay notify handler
[   12.452706] acpi device:03: registered as cooling_device2
[   12.452898] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:02/input/input6
[   12.484525] ACPI: Video Device [VID] (multi-head: yes  rom: no  post: no)
[   12.486130] acpi device:0a: registered as cooling_device3
[   12.486296] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:08/device:09/input/input7
[   12.487677] ACPI: AC Adapter [AC] (on-line)
[   12.516518] ACPI: Video Device [VID1] (multi-head: yes  rom: no  post: no)
[   12.576090] ACPI: Battery Slot [BAT0] (battery present)
[   12.749004] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
[   12.765275] [fglrx] Maximum main memory to use for locked dma buffers: 2887 MBytes.
[   12.765900] [fglrx]   vendor: 1002 device: 9591 count: 1
[   12.766737] [fglrx] ioport: bar 1, base 0x2000, size: 0x100
[   12.766809] pci 0000:01:00.0: power state changed by ACPI to D0
[   12.766815] pci 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   12.766820] pci 0000:01:00.0: setting latency timer to 64
[   12.769531] [fglrx] PAT is enabled successfully!
[   12.769573] [fglrx] module loaded - fglrx 8.54.3 [Oct 10 2008] with 1 minors
[   12.819603] Bluetooth: Core ver 2.13
[   12.834357] NET: Registered protocol family 31
[   12.834359] Bluetooth: HCI device and connection manager initialized
[   12.834361] Bluetooth: HCI socket layer initialized
[   12.914770] Linux video capture interface: v2.00
[   12.940336] ricoh-mmc: Ricoh MMC Controller disabling driver
[   12.940338] ricoh-mmc: Copyright(c) Philip Langdale
[   12.940400] ricoh-mmc: Ricoh MMC controller found at 0000:15:00.3 [1180:0843] (rev 11)
[   12.940421] ricoh-mmc: Controller is now disabled.
[   13.068546] Bluetooth: Generic Bluetooth USB driver ver 0.3
[   13.068627] usbcore: registered new interface driver btusb
[   13.167723] usbcore: registered new interface driver usbserial
[   13.167735] usbserial: USB Serial support registered for generic
[   13.167812] usbcore: registered new interface driver usbserial_generic
[   13.167813] usbserial: USB Serial Driver core
[   13.215515] usbserial: USB Serial support registered for GSM modem (1-port)
[   13.215552] option 8-4:1.0: GSM modem (1-port) converter detected
[   13.215662] usb 8-4: GSM modem (1-port) converter now attached to ttyUSB0
[   13.215673] option 8-4:1.1: GSM modem (1-port) converter detected
[   13.215727] usb 8-4: GSM modem (1-port) converter now attached to ttyUSB1
[   13.215738] option 8-4:1.2: GSM modem (1-port) converter detected
[   13.215782] usb 8-4: GSM modem (1-port) converter now attached to ttyUSB2
[   13.215793] option 8-4:1.3: GSM modem (1-port) converter detected
[   13.215840] usb 8-4: GSM modem (1-port) converter now attached to ttyUSB3
[   13.215851] option 8-4:1.4: GSM modem (1-port) converter detected
[   13.215896] usb 8-4: GSM modem (1-port) converter now attached to ttyUSB4
[   13.215907] option 8-4:1.5: GSM modem (1-port) converter detected
[   13.215954] usb 8-4: GSM modem (1-port) converter now attached to ttyUSB5
[   13.215965] option 8-4:1.6: GSM modem (1-port) converter detected
[   13.216013] usb 8-4: GSM modem (1-port) converter now attached to ttyUSB6
[   13.216024] option 8-4:1.7: GSM modem (1-port) converter detected
[   13.216077] usb 8-4: GSM modem (1-port) converter now attached to ttyUSB7
[   13.216088] option 8-4:1.8: GSM modem (1-port) converter detected
[   13.216134] usb 8-4: GSM modem (1-port) converter now attached to ttyUSB8
[   13.216144] option 8-4:1.9: GSM modem (1-port) converter detected
[   13.216192] usb 8-4: GSM modem (1-port) converter now attached to ttyUSB9
[   13.216203] option 8-4:1.10: GSM modem (1-port) converter detected
[   13.216248] usb 8-4: GSM modem (1-port) converter now attached to ttyUSB10
[   13.216258] usbcore: registered new interface driver option
[   13.216260] option: USB Driver for GSM modems: v0.7.2
[   13.242137] Yenta: CardBus bridge found at 0000:15:00.0 [17aa:20c6]
[   13.290618] usbcore: registered new interface driver cdc_acm
[   13.290630] cdc_acm: v0.26:USB Abstract Control Model driver for USB modems and ISDN adapters
[   13.295162] sdhci: Secure Digital Host Controller Interface driver
[   13.295164] sdhci: Copyright(c) Pierre Ossman
[   13.297131] usbcore: registered new interface driver cdc_wdm
[   13.361969] Non-volatile memory driver v1.2
[   13.369293] Yenta: ISA IRQ mask 0x0cb8, PCI irq 16
[   13.369296] Socket status: 30000006
[   13.369299] pcmcia: parent PCI bridge I/O window: 0x6000 - 0x9fff
[   13.369313] cs: IO port probe 0x6000-0x9fff: clean.
[   13.369974] pcmcia: parent PCI bridge Memory window: 0xf4400000 - 0xf7ffffff
[   13.369985] pcmcia: parent PCI bridge Memory window: 0xf0000000 - 0xf3ffffff
[   13.370615] sdhci-pci 0000:15:00.2: SDHCI controller found [1180:0822] (rev 21)
[   13.370630] sdhci-pci 0000:15:00.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[   13.371637] sdhci-pci 0000:15:00.2: Will use DMA mode even though HW doesn't fully claim to support it.
[   13.373674] mmc0: SDHCI controller on PCI [0000:15:00.2] using DMA
[   13.412265] uvcvideo: Found UVC 1.00 device <unnamed> (17ef:4807)
[   13.417443] input: UVC Camera (17ef:4807) as /devices/pci0000:00/0000:00:1a.7/usb4/4-6/4-6:1.0/input/input8
[   13.464624] usbcore: registered new interface driver uvcvideo
[   13.464627] USB Video Class driver (v0.1.0)
[   13.477727] usbcore: registered new interface driver cdc_ether
[   13.524441] usbcore: registered new interface driver zaurus
[   13.581620] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, 1.3.27ks
[   13.581622] iwlagn: Copyright(c) 2003-2008 Intel Corporation
[   13.582424] iwlagn 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   13.582432] iwlagn 0000:03:00.0: setting latency timer to 64
[   13.582455] iwlagn: Detected Intel Wireless WiFi Link 5100AGN REV=0x54
[   13.612008] iwlagn: Tunable channels: 13 802.11bg, 24 802.11a channels
[   13.665266] iwlagn 0000:03:00.0: PCI INT A disabled
[   13.665588] phy0: Selected rate control algorithm 'iwl-agn-rs'
[   14.135788] Synaptics Touchpad, model: 1, fw: 7.0, id: 0x1c0b1, caps: 0xd04791/0xb00000
[   14.135792] serio: Synaptics pass-through port at isa0060/serio1/input0
[   14.180680] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input9
[   14.208180] thinkpad_acpi: ThinkPad ACPI Extras v0.21
[   14.208182] thinkpad_acpi: [http://ibm-acpi.sf.net/](http://ibm-acpi.sf.net/)
[   14.208183] thinkpad_acpi: ThinkPad BIOS 6FET43WW (1.13 ), EC 7VHT12WW-1.01
[   14.208185] thinkpad_acpi: Lenovo ThinkPad W500, model 406224U
[   14.209105] thinkpad_acpi: radio switch found; radios are enabled
[   14.209212] thinkpad_acpi: This ThinkPad has standard ACPI backlight brightness control, supported by the ACPI video driver
[   14.209214] thinkpad_acpi: Disabling thinkpad-acpi brightness events by default...
[   14.222559] Registered led device: tpacpi::thinklight
[   14.222594] Registered led device: tpacpi::power
[   14.222615] Registered led device: tpacpi:orange:batt
[   14.222636] Registered led device: tpacpi:green:batt
[   14.222659] Registered led device: tpacpi::dock_active
[   14.222680] Registered led device: tpacpi::bay_active
[   14.222702] Registered led device: tpacpi::dock_batt
[   14.222724] Registered led device: tpacpi::unknown_led
[   14.222745] Registered led device: tpacpi::standby
[   14.225822] thinkpad_acpi: Lenovo BIOS switched to ACPI backlight control mode
[   14.225824] thinkpad_acpi: standard ACPI backlight interface available, not loading native one...
[   14.226162] input: ThinkPad Extra Buttons as /devices/virtual/input/input10
[   14.388709] HDA Intel 0000:00:1b.0: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[   14.388727] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   14.493802] cs: IO port probe 0x100-0x3af: clean.
[   14.495518] cs: IO port probe 0x3e0-0x4ff: excluding 0x4d0-0x4d7
[   14.496231] cs: IO port probe 0x820-0x8ff: clean.
[   14.497197] cs: IO port probe 0xc00-0xcf7: clean.
[   14.497889] cs: IO port probe 0xa00-0xaff: clean.
[   14.806339] lp: driver loaded but no devices found
[   14.961465] Adding 997880k swap on /dev/sda6.  Priority:-1 extents:1 across:997880k
[   15.489765] EXT3 FS on sda7, internal journal
[   16.390967] type=1505 audit(1236107236.744:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=4696
[   16.428071] type=1505 audit(1236107236.783:3): operation="profile_load" name="/usr/bin/freshclam" name2="default" pid=4701
[   16.533574] type=1505 audit(1236107236.887:4): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=4705
[   16.533705] type=1505 audit(1236107236.887:5): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=4705
[   16.670570] ip_tables: (C) 2000-2006 Netfilter Core Team
[   17.136304] NET: Registered protocol family 10
[   17.136662] lo: Disabled Privacy Extensions
[   17.137070] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   17.777789] ACPI: \_SB_.PCI0.SATA.PRT1: found ejectable bay
[   17.777794] ACPI: \_SB_.PCI0.SATA.PRT1: Adding notify handler
[   17.777816] ACPI: Error installing bay notify handler
[   18.522956] warning: `avahi-daemon' uses 32-bit capabilities (legacy support in use)
[   18.706860] apm: BIOS not found.
[   19.577201] ppdev: user-space parallel port driver
[   20.158794] IBM TrackPoint firmware: 0x0e, buttons: 3/3
[   20.447132] input: TPPS/2 IBM TrackPoint as /devices/platform/i8042/serio1/serio2/input/input11
[   20.786413] vboxdrv: Trying to deactivate the NMI watchdog permanently...
[   20.786418] vboxdrv: Successfully done.
[   20.786419] vboxdrv: Found 2 processor cores.
[   20.786512] vboxdrv: fAsync=0 offMin=0x20d offMax=0xc98
[   20.786515] vboxdrv: TSC mode is 'synchronous', kernel timer mode is 'normal'.
[   20.786517] vboxdrv: Successfully loaded version 2.0.4_OSE (interface 0x00090000).
[   23.219070] Bluetooth: L2CAP ver 2.11
[   23.219082] Bluetooth: L2CAP socket layer initialized
[   23.251438] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   23.251449] Bluetooth: BNEP filters: protocol multicast
[   23.310539] Bridge firewalling registered
[   23.358737] Bluetooth: SCO (Voice Link) ver 0.6
[   23.358747] Bluetooth: SCO socket layer initialized
[   23.376819] Bluetooth: RFCOMM socket layer initialized
[   23.377175] Bluetooth: RFCOMM TTY layer initialized
[   23.377184] Bluetooth: RFCOMM ver 1.10
[   27.608932] iwlagn 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   27.609052] iwlagn 0000:03:00.0: restoring config space at offset 0x1 (was 0x100102, writing 0x100106)
[   27.609290] firmware: requesting iwlwifi-5000-1.ucode
[   30.198700] Registered led device: iwl-phy0:radio
[   30.198862] Registered led device: iwl-phy0:assoc
[   30.198977] Registered led device: iwl-phy0:RX
[   30.199086] Registered led device: iwl-phy0:TX
[   30.240767] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   30.348631] NET: Registered protocol family 17
[   31.949432] wlan0: authenticate with AP 00:14:c1:19:12:6c
[   31.951361] wlan0: authenticated
[   31.951373] wlan0: associate with AP 00:14:c1:19:12:6c
[   31.953777] wlan0: RX AssocResp from 00:14:c1:19:12:6c (capab=0x401 status=0 aid=1)
[   31.953790] wlan0: associated
[   31.958643] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   31.961612] wlan0: disassociating by local choice (reason=3)
[   42.552583] wlan0: no IPv6 routers present
[   53.469071] wlan0: associate with AP 00:14:c1:19:12:6c
[   53.471671] wlan0: RX ReassocResp from 00:14:c1:19:12:6c (capab=0x401 status=0 aid=1)
[   53.471685] wlan0: associated
[   53.478469] wlan0: disassociating by local choice (reason=3)
[   68.242678] CPU0 attaching NULL sched-domain.
[   68.242696] CPU1 attaching NULL sched-domain.
[   68.249404] CPU0 attaching sched-domain:
[   68.249415]  domain 0: span 0-1 level MC
[   68.249421]   groups: 0 1
[   68.249434] CPU1 attaching sched-domain:
[   68.249439]  domain 0: span 0-1 level MC
[   68.249444]   groups: 1 0
[   72.105376] wlan0: associate with AP 00:14:c1:19:12:6c
[   72.108357] wlan0: RX ReassocResp from 00:14:c1:19:12:6c (capab=0x401 status=0 aid=1)
[   72.108368] wlan0: associated
[   72.114176] wlan0: authenticate with AP 00:14:c1:19:12:6c
[   72.116171] wlan0: authenticated
[   72.116182] wlan0: associate with AP 00:14:c1:19:12:6c
[   72.118386] wlan0: RX ReassocResp from 00:14:c1:19:12:6c (capab=0x401 status=0 aid=1)
[   72.118395] wlan0: associated
[  137.616706] type=1503 audit(1236107357.972:6): operation="inode_permission" requested_mask="w::" denied_mask="w::" fsuid=0 name="/dev/ttyUSB0" pid=8849 profile="/usr/sbin/cupsd"
[  137.619649] type=1503 audit(1236107357.972:7): operation="inode_permission" requested_mask="w::" denied_mask="w::" fsuid=0 name="/dev/ttyUSB1" pid=8849 profile="/usr/sbin/cupsd"
[  137.622538] type=1503 audit(1236107357.976:8): operation="inode_permission" requested_mask="w::" denied_mask="w::" fsuid=0 name="/dev/ttyUSB2" pid=8849 profile="/usr/sbin/cupsd"
[  137.625487] type=1503 audit(1236107357.980:9): operation="inode_permission" requested_mask="w::" denied_mask="w::" fsuid=0 name="/dev/ttyUSB3" pid=8849 profile="/usr/sbin/cupsd"
[  137.628098] type=1503 audit(1236107357.980:10): operation="inode_permission" requested_mask="w::" denied_mask="w::" fsuid=0 name="/dev/ttyUSB4" pid=8849 profile="/usr/sbin/cupsd"
[  137.628137] type=1503 audit(1236107357.980:11): operation="inode_permission" requested_mask="w::" denied_mask="w::" fsuid=0 name="/dev/ttyUSB5" pid=8849 profile="/usr/sbin/cupsd"
[  137.628174] type=1503 audit(1236107357.980:12): operation="inode_permission" requested_mask="w::" denied_mask="w::" fsuid=0 name="/dev/ttyUSB6" pid=8849 profile="/usr/sbin/cupsd"
[  137.628212] type=1503 audit(1236107357.980:13): operation="inode_permission" requested_mask="w::" denied_mask="w::" fsuid=0 name="/dev/ttyUSB7" pid=8849 profile="/usr/sbin/cupsd"
[  137.628249] type=1503 audit(1236107357.980:14): operation="inode_permission" requested_mask="w::" denied_mask="w::" fsuid=0 name="/dev/ttyUSB8" pid=8849 profile="/usr/sbin/cupsd"
[  137.628286] type=1503 audit(1236107357.980:15): operation="inode_permission" requested_mask="w::" denied_mask="w::" fsuid=0 name="/dev/ttyUSB9" pid=8849 profile="/usr/sbin/cupsd"

```

---

### Post by K. Hendrik on 2009-03-03
ok nothing in dmesg so the combination should have a keycode, but that should be recognized by xev... 

one thing i thought that could lead to this is that ubuntu 8.04 and 8.10 could have different fdi files i checked that and indeed they are different. you could try to copy the file /usr/share/hal/fdi/information/10freedesktop/30-keymap-dell.fdi from a live ubuntu 8.04 cd and replace your fdi at the same possition with it, but i don't really know if that will solve the problem but it's the last thing i can think of.

---

### Post by Bashar &quot; on 2009-03-03
it was working just fine till ubuntu decided to update few things a week or two ago
it was kinda big update then these functions stopped working... :(

---

### Post by K. Hendrik on 2009-03-03
ahh ok i thought you did an upgrade from 8.04 too 8.10
what exactly was the funktion of Fn+F7 for your laptop

---

### Post by Bashar &quot; on 2009-03-04
switching between laptop screen and external monitor

other Fn+F? are working fine such as lock, hibernate, disable/enable touchpad

---

### Post by K. Hendrik on 2009-03-04
i really can't think of anything which could cause this, sorry

---

