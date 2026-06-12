---
title: "E-sata read problem on intrepid"
date: 2009-02-15
forum: Hardware
---

### Post by Thiras on 2009-02-15
Hi. I am on Ubuntu Intrepid. I have got WD mybook home Edition 1TB(ntfs). It's connected to my pc with e-sata. There is no problem expect its little bit slow when i am coping the datas to it. But when sometimes i am copying the big datas from mybook to internal hdd the connection is lost and i cant reach "mybook" without reboot. Here is dmesg logs.

Thank you for your help.

```
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.27-11-generic (buildd@rothera) (gcc version 4.3.2 (Ubuntu 4.3.2-1ubuntu11) ) #1 SMP Thu Jan 29 19:24:39 UTC 2009 (Ubuntu 2.6.27-11.27-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e4000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000003ff80000 (usable)
[    0.000000]  BIOS-e820: 000000003ff80000 - 000000003ff8e000 (ACPI data)
[    0.000000]  BIOS-e820: 000000003ff8e000 - 000000003ffe0000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000003ffe0000 - 0000000040000000 (reserved)
[    0.000000]  BIOS-e820: 00000000ffb00000 - 0000000100000000 (reserved)
[    0.000000] DMI 2.4 present.
[    0.000000] AMI BIOS detected: BIOS may corrupt low RAM, working it around.
[    0.000000] last_pfn = 0x3ff80 max_arch_pfn = 0x100000
[    0.000000] kernel direct mapping tables up to 38000000 @ 10000-15000
[    0.000000] RAMDISK: 3781d000 - 37fefc12
[    0.000000] ACPI: RSDP 000FAF20, 0014 (r0 ACPIAM)
[    0.000000] ACPI: RSDT 3FF80000, 0040 (r1 A_M_I_ OEMRSDT  11000716 MSFT       97)
[    0.000000] ACPI: FACP 3FF80200, 0081 (r1 A_M_I_ OEMFACP  11000716 MSFT       97)
[    0.000000] ACPI: DSDT 3FF80590, 9560 (r1  A0543 A0543000        0 INTL 20060113)
[    0.000000] ACPI: FACS 3FF8E000, 0040
[    0.000000] ACPI: APIC 3FF80390, 0080 (r1 A_M_I_ OEMAPIC  11000716 MSFT       97)
[    0.000000] ACPI: OEMB 3FF8E040, 0066 (r1 A_M_I_ AMI_OEM  11000716 MSFT       97)
[    0.000000] ACPI: HPET 3FF89AF0, 0038 (r1 A_M_I_ OEMHPET  11000716 MSFT       97)
[    0.000000] ACPI: MCFG 3FF89B30, 003C (r1 A_M_I_ OEMMCFG  11000716 MSFT       97)
[    0.000000] ACPI: SSDT 3FF8E0B0, 01C6 (r1    AMI   CPU1PM        1 INTL 20060113)
[    0.000000] ACPI: SSDT 3FF8E280, 013A (r1    AMI   CPU2PM        1 INTL 20060113)
[    0.000000] 127MB HIGHMEM available.
[    0.000000] 896MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 38000000
[    0.000000]   low ram: 00000000 - 38000000
[    0.000000]   bootmap 00011000 - 00018000
[    0.000000] (9 early reservations) ==> bootmem [0000000000 - 0038000000]
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000]   #1 [0000001000 - 0000002000]    EX TRAMPOLINE ==> [0000001000 - 0000002000]
[    0.000000]   #2 [0000006000 - 0000007000]       TRAMPOLINE ==> [0000006000 - 0000007000]
[    0.000000]   #3 [0000100000 - 00005c29e0]    TEXT DATA BSS ==> [0000100000 - 00005c29e0]
[    0.000000]   #4 [003781d000 - 0037fefc12]          RAMDISK ==> [003781d000 - 0037fefc12]
[    0.000000]   #5 [00005c3000 - 00005c6000]    INIT_PG_TABLE ==> [00005c3000 - 00005c6000]
[    0.000000]   #6 [000009fc00 - 0000100000]    BIOS reserved ==> [000009fc00 - 0000100000]
[    0.000000]   #7 [0000010000 - 0000011000]          PGTABLE ==> [0000010000 - 0000011000]
[    0.000000]   #8 [0000011000 - 0000018000]          BOOTMAP ==> [0000011000 - 0000018000]
[    0.000000] found SMP MP-table at [c00ff780] 000ff780
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x00038000
[    0.000000]   HighMem  0x00038000 -> 0x0003ff80
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[2] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x0000009f
[    0.000000]     0: 0x00000100 -> 0x0003ff80
[    0.000000] On node 0 totalpages: 261903
[    0.000000] free_area_init_node: node 0, pgdat c048c680, node_mem_map c1000240
[    0.000000]   DMA zone: 3947 pages, LIFO batch:0
[    0.000000]   Normal zone: 223300 pages, LIFO batch:31
[    0.000000]   HighMem zone: 32353 pages, LIFO batch:7
[    0.000000] ACPI: PM-Timer IO Port: 0x808
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x82] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x83] disabled)
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
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
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e4000
[    0.000000] PM: Registered nosave memory: 00000000000e4000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 50000000 (gap: 40000000:bfb00000)
[    0.000000] PERCPU: Allocating 41628 bytes of per cpu data
[    0.000000] NR_CPUS: 64, nr_cpu_ids: 4, nr_node_ids 1
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 259600
[    0.000000] Kernel command line: root=UUID=ef836df2-ee4a-4a41-8c75-670e96c0d39f ro quiet splash 
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] TSC: PIT calibration confirmed by PMTIMER.
[    0.000000] TSC: using PMTIMER calibration value
[    0.000000] Detected 1869.855 MHz processor.
[    0.004000] Console: colour VGA+ 80x25
[    0.004000] console [tty0] enabled
[    0.004000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.004000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.004000] Memory: 1024104k/1048064k available (2576k kernel code, 23120k reserved, 1165k data, 424k init, 130560k highmem)
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
[    0.004000] Calibrating delay loop (skipped), value calculated using timer frequency.. 3739.71 BogoMIPS (lpj=7479420)
[    0.004000] Security Framework initialized
[    0.004000] SELinux:  Disabled at boot.
[    0.004000] AppArmor: AppArmor initialized
[    0.004000] Mount-cache hash table entries: 512
[    0.004000] Initializing cgroup subsys ns
[    0.004000] Initializing cgroup subsys cpuacct
[    0.004000] Initializing cgroup subsys memory
[    0.004000] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.004000] CPU: L2 cache: 2048K
[    0.004000] CPU: Physical Processor ID: 0
[    0.004000] CPU: Processor Core ID: 0
[    0.004000] using mwait in idle threads.
[    0.004000] Checking 'hlt' instruction... OK.
[    0.017902] ACPI: Core revision 20080609
[    0.020860] ACPI: Checking initramfs for custom DSDT
[    0.384216] ENABLING IO-APIC IRQs
[    0.384388] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.425437] CPU0: Intel(R) Core(TM)2 CPU          6300  @ 1.86GHz stepping 06
[    0.428026] Booting processor 1/1 ip 6000
[    0.004000] Initializing CPU#1
[    0.004000] Calibrating delay using timer specific routine.. 3517.60 BogoMIPS (lpj=7035209)
[    0.004000] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.004000] CPU: L2 cache: 2048K
[    0.004000] CPU: Physical Processor ID: 0
[    0.004000] CPU: Processor Core ID: 1
[    0.512524] CPU1: Intel(R) Core(TM)2 CPU          6300  @ 1.86GHz stepping 06
[    0.512540] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
[    0.516051] Brought up 2 CPUs
[    0.516054] Total of 2 processors activated (7257.31 BogoMIPS).
[    0.516075] CPU0 attaching sched-domain:
[    0.516078]  domain 0: span 0-1 level MC
[    0.516081]   groups: 0 1
[    0.516087] CPU1 attaching sched-domain:
[    0.516089]  domain 0: span 0-1 level MC
[    0.516092]   groups: 1 0
[    0.516169] net_namespace: 840 bytes
[    0.516169] Booting paravirtualized kernel on bare hardware
[    0.516300] Time: 14:34:15  Date: 02/15/09
[    0.516325] NET: Registered protocol family 16
[    0.516345] EISA bus registered
[    0.516345] ACPI: bus type pci registered
[    0.516345] PCI: MCFG configuration 0: base f0000000 segment 0 buses 0 - 63
[    0.516345] PCI: Not using MMCONFIG.
[    0.516345] PCI: PCI BIOS revision 3.00 entry at 0xf0031, last bus=6
[    0.516345] PCI: Using configuration type 1 for base access
[    0.517156] ACPI: EC: Look up EC in DSDT
[    0.535960] ACPI: Interpreter enabled
[    0.535967] ACPI: (supports S0 S1 S3 S4 S5)
[    0.535986] ACPI: Using IOAPIC for interrupt routing
[    0.536060] PCI: MCFG configuration 0: base f0000000 segment 0 buses 0 - 63
[    0.539474] PCI: MCFG area at f0000000 reserved in ACPI motherboard resources
[    0.539477] PCI: Using MMCONFIG for extended config space
[    0.548185] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.548185] pci 0000:00:01.0: PME# supported from D0 D3hot D3cold
[    0.548185] pci 0000:00:01.0: PME# disabled
[    0.548185] PCI: 0000:00:1b.0 reg 10 64bit mmio: [ffafc000, ffafffff]
[    0.548209] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    0.548213] pci 0000:00:1b.0: PME# disabled
[    0.548261] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.548265] pci 0000:00:1c.0: PME# disabled
[    0.548316] pci 0000:00:1c.3: PME# supported from D0 D3hot D3cold
[    0.548320] pci 0000:00:1c.3: PME# disabled
[    0.548370] pci 0000:00:1c.4: PME# supported from D0 D3hot D3cold
[    0.548374] pci 0000:00:1c.4: PME# disabled
[    0.548423] pci 0000:00:1c.5: PME# supported from D0 D3hot D3cold
[    0.548427] pci 0000:00:1c.5: PME# disabled
[    0.548462] PCI: 0000:00:1d.0 reg 20 io port: [e480, e49f]
[    0.548510] PCI: 0000:00:1d.1 reg 20 io port: [e800, e81f]
[    0.548557] PCI: 0000:00:1d.2 reg 20 io port: [e880, e89f]
[    0.548604] PCI: 0000:00:1d.3 reg 20 io port: [ec00, ec1f]
[    0.548656] PCI: 0000:00:1d.7 reg 10 32bit mmio: [ffafbc00, ffafbfff]
[    0.548702] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
[    0.548706] pci 0000:00:1d.7: PME# disabled
[    0.548818] pci 0000:00:1f.0: quirk: region 0800-087f claimed by ICH6 ACPI/GPIO/TCO
[    0.548822] pci 0000:00:1f.0: quirk: region 0480-04bf claimed by ICH6 GPIO
[    0.548845] PCI: 0000:00:1f.1 reg 10 io port: [0, 7]
[    0.548852] PCI: 0000:00:1f.1 reg 14 io port: [0, 3]
[    0.548859] PCI: 0000:00:1f.1 reg 18 io port: [0, 7]
[    0.548865] PCI: 0000:00:1f.1 reg 1c io port: [0, 3]
[    0.548872] PCI: 0000:00:1f.1 reg 20 io port: [ffa0, ffaf]
[    0.548911] PCI: 0000:00:1f.2 reg 10 io port: [e400, e407]
[    0.548917] PCI: 0000:00:1f.2 reg 14 io port: [e080, e083]
[    0.548923] PCI: 0000:00:1f.2 reg 18 io port: [e000, e007]
[    0.548929] PCI: 0000:00:1f.2 reg 1c io port: [dc00, dc03]
[    0.548935] PCI: 0000:00:1f.2 reg 20 io port: [d880, d88f]
[    0.548942] PCI: 0000:00:1f.2 reg 24 32bit mmio: [ffafb800, ffafbbff]
[    0.548959] pci 0000:00:1f.2: PME# supported from D3hot
[    0.548963] pci 0000:00:1f.2: PME# disabled
[    0.549004] PCI: 0000:00:1f.3 reg 20 io port: [400, 41f]
[    0.549054] PCI: 0000:06:00.0 reg 10 64bit mmio: [d0000000, dfffffff]
[    0.549064] PCI: 0000:06:00.0 reg 18 64bit mmio: [ff9f0000, ff9fffff]
[    0.549070] PCI: 0000:06:00.0 reg 20 io port: [c800, c8ff]
[    0.549079] PCI: 0000:06:00.0 reg 30 32bit mmio: [ff9c0000, ff9dffff]
[    0.549094] pci 0000:06:00.0: supports D1
[    0.549096] pci 0000:06:00.0: supports D2
[    0.549120] PCI: 0000:06:00.1 reg 10 64bit mmio: [ff9e0000, ff9effff]
[    0.549151] pci 0000:06:00.1: supports D1
[    0.549153] pci 0000:06:00.1: supports D2
[    0.549192] PCI: bridge 0000:00:01.0 io port: [c000, cfff]
[    0.549196] PCI: bridge 0000:00:01.0 32bit mmio: [ff900000, ff9fffff]
[    0.549201] PCI: bridge 0000:00:01.0 64bit mmio pref: [cff00000, efefffff]
[    0.549247] PCI: bridge 0000:00:1c.0 64bit mmio pref: [cfe00000, cfefffff]
[    0.549307] PCI: 0000:04:00.0 reg 10 64bit mmio: [ff8fc000, ff8fffff]
[    0.549316] PCI: 0000:04:00.0 reg 18 io port: [b800, b8ff]
[    0.549343] PCI: 0000:04:00.0 reg 30 32bit mmio: [ff8c0000, ff8dffff]
[    0.549363] pci 0000:04:00.0: supports D1
[    0.549365] pci 0000:04:00.0: supports D2
[    0.549367] pci 0000:04:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.549373] pci 0000:04:00.0: PME# disabled
[    0.549407] PCI: bridge 0000:00:1c.3 io port: [b000, bfff]
[    0.549412] PCI: bridge 0000:00:1c.3 32bit mmio: [ff800000, ff8fffff]
[    0.549475] PCI: 0000:03:00.0 reg 10 64bit mmio: [ff7fc000, ff7fffff]
[    0.549484] PCI: 0000:03:00.0 reg 18 io port: [a800, a8ff]
[    0.549511] PCI: 0000:03:00.0 reg 30 32bit mmio: [ff7c0000, ff7dffff]
[    0.549531] pci 0000:03:00.0: supports D1
[    0.549533] pci 0000:03:00.0: supports D2
[    0.549535] pci 0000:03:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.549540] pci 0000:03:00.0: PME# disabled
[    0.549575] PCI: bridge 0000:00:1c.4 io port: [a000, afff]
[    0.549579] PCI: bridge 0000:00:1c.4 32bit mmio: [ff700000, ff7fffff]
[    0.549676] PCI: 0000:02:00.0 reg 24 32bit mmio: [ff6fe000, ff6fffff]
[    0.549686] PCI: 0000:02:00.0 reg 30 32bit mmio: [ff6e0000, ff6effff]
[    0.549710] pci 0000:02:00.0: PME# supported from D3hot
[    0.549716] pci 0000:02:00.0: PME# disabled
[    0.549757] PCI: 0000:02:00.1 reg 10 io port: [9c00, 9c07]
[    0.549766] PCI: 0000:02:00.1 reg 14 io port: [9880, 9883]
[    0.549775] PCI: 0000:02:00.1 reg 18 io port: [9800, 9807]
[    0.549785] PCI: 0000:02:00.1 reg 1c io port: [9480, 9483]
[    0.549794] PCI: 0000:02:00.1 reg 20 io port: [9400, 940f]
[    0.549874] PCI: bridge 0000:00:1c.5 io port: [9000, 9fff]
[    0.549878] PCI: bridge 0000:00:1c.5 32bit mmio: [ff600000, ff6fffff]
[    0.549921] PCI: 0000:01:03.0 reg 10 32bit mmio: [ff5ff800, ff5fffff]
[    0.549929] PCI: 0000:01:03.0 reg 14 32bit mmio: [ff5f8000, ff5fbfff]
[    0.549969] pci 0000:01:03.0: supports D1
[    0.549971] pci 0000:01:03.0: supports D2
[    0.549973] pci 0000:01:03.0: PME# supported from D0 D1 D2 D3hot
[    0.549978] pci 0000:01:03.0: PME# disabled
[    0.550016] pci 0000:00:1e.0: transparent bridge
[    0.550022] PCI: bridge 0000:00:1e.0 32bit mmio: [ff500000, ff5fffff]
[    0.550052] bus 00 -> node 0
[    0.550059] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.550367] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P1._PRT]
[    0.550508] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P3._PRT]
[    0.550743] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P4._PRT]
[    0.550884] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P7._PRT]
[    0.550996] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P8._PRT]
[    0.552119] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P9._PRT]
[    0.556181] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 10 *11 12 14 15)
[    0.556352] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 *10 11 12 14 15)
[    0.556520] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 *7 10 11 12 14 15)
[    0.556688] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 *5 6 7 10 11 12 14 15)
[    0.556854] ACPI: PCI Interrupt Link [LNKE] (IRQs *3 4 5 6 7 10 11 12 14 15)
[    0.557021] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 10 *11 12 14 15)
[    0.557188] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[    0.557356] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 *10 11 12 14 15)
[    0.557433] ACPI Warning (tbutils-0217): Incorrect checksum in table [OEMB] - EE, should be E5 [20080609]
[    0.557433] Linux Plug and Play Support v0.97 (c) Adam Belay
[    0.557433] pnp: PnP ACPI init
[    0.557433] ACPI: bus type pnp registered
[    0.560810] pnp: PnP ACPI: found 16 devices
[    0.560810] ACPI: ACPI bus type pnp unregistered
[    0.560810] PnPBIOS: Disabled by ACPI PNP
[    0.560810] PCI: Using ACPI for IRQ routing
[    0.568041] NET: Registered protocol family 8
[    0.568043] NET: Registered protocol family 20
[    0.568060] NetLabel: Initializing
[    0.568060] NetLabel:  domain hash size = 128
[    0.568060] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.568068] NetLabel:  unlabeled traffic allowed by default
[    0.568074] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[    0.568079] hpet0: 3 64-bit timers, 14318180 Hz
[    0.570060] tracer: 772 pages allocated for 65536 entries of 48 bytes
[    0.570063]    actual entries 65620
[    0.570147] AppArmor: AppArmor Filesystem Enabled
[    0.570166] ACPI: RTC can wake from S4
[    0.572041] Switched to high resolution mode on CPU 0
[    0.572557] Switched to high resolution mode on CPU 1
[    0.576023] system 00:01: iomem range 0xfed13000-0xfed19fff has been reserved
[    0.576033] system 00:07: ioport range 0x290-0x297 has been reserved
[    0.576047] system 00:08: ioport range 0x4d0-0x4d1 has been reserved
[    0.576050] system 00:08: ioport range 0x800-0x87f has been reserved
[    0.576053] system 00:08: ioport range 0x400-0x41f has been reserved
[    0.576056] system 00:08: ioport range 0x480-0x4bf has been reserved
[    0.576059] system 00:08: iomem range 0xfed1c000-0xfed1ffff has been reserved
[    0.576063] system 00:08: iomem range 0xfed20000-0xfed3ffff has been reserved
[    0.576066] system 00:08: iomem range 0xfed50000-0xfed8ffff has been reserved
[    0.576069] system 00:08: iomem range 0xffb00000-0xffbfffff could not be reserved
[    0.576073] system 00:08: iomem range 0xfff00000-0xffffffff could not be reserved
[    0.576082] system 00:0c: iomem range 0xfec00000-0xfec00fff has been reserved
[    0.576085] system 00:0c: iomem range 0xfee00000-0xfee00fff has been reserved
[    0.576094] system 00:0e: iomem range 0xf0000000-0xf3ffffff has been reserved
[    0.576101] system 00:0f: iomem range 0x0-0x9ffff could not be reserved
[    0.576104] system 00:0f: iomem range 0xc0000-0xdffff could not be reserved
[    0.576107] system 00:0f: iomem range 0xe0000-0xfffff could not be reserved
[    0.576111] system 00:0f: iomem range 0x100000-0x3fffffff could not be reserved
[    0.611250] pci 0000:00:01.0: PCI bridge, secondary bus 0000:06
[    0.611253] pci 0000:00:01.0:   IO window: 0xc000-0xcfff
[    0.611258] pci 0000:00:01.0:   MEM window: 0xff900000-0xff9fffff
[    0.611262] pci 0000:00:01.0:   PREFETCH window: 0x000000cff00000-0x000000efefffff
[    0.611267] pci 0000:00:1c.0: PCI bridge, secondary bus 0000:05
[    0.611269] pci 0000:00:1c.0:   IO window: disabled
[    0.611274] pci 0000:00:1c.0:   MEM window: disabled
[    0.611278] pci 0000:00:1c.0:   PREFETCH window: 0x000000cfe00000-0x000000cfefffff
[    0.611285] pci 0000:00:1c.3: PCI bridge, secondary bus 0000:04
[    0.611288] pci 0000:00:1c.3:   IO window: 0xb000-0xbfff
[    0.611293] pci 0000:00:1c.3:   MEM window: 0xff800000-0xff8fffff
[    0.611297] pci 0000:00:1c.3:   PREFETCH window: disabled
[    0.611303] pci 0000:00:1c.4: PCI bridge, secondary bus 0000:03
[    0.611307] pci 0000:00:1c.4:   IO window: 0xa000-0xafff
[    0.611312] pci 0000:00:1c.4:   MEM window: 0xff700000-0xff7fffff
[    0.611316] pci 0000:00:1c.4:   PREFETCH window: disabled
[    0.611322] pci 0000:00:1c.5: PCI bridge, secondary bus 0000:02
[    0.611326] pci 0000:00:1c.5:   IO window: 0x9000-0x9fff
[    0.611331] pci 0000:00:1c.5:   MEM window: 0xff600000-0xff6fffff
[    0.611335] pci 0000:00:1c.5:   PREFETCH window: disabled
[    0.611341] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:01
[    0.611343] pci 0000:00:1e.0:   IO window: disabled
[    0.611348] pci 0000:00:1e.0:   MEM window: 0xff500000-0xff5fffff
[    0.611352] pci 0000:00:1e.0:   PREFETCH window: disabled
[    0.611366] pci 0000:00:01.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.611371] pci 0000:00:01.0: setting latency timer to 64
[    0.611378] pci 0000:00:1c.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.611382] pci 0000:00:1c.0: setting latency timer to 64
[    0.611390] pci 0000:00:1c.3: PCI INT D -> GSI 19 (level, low) -> IRQ 19
[    0.611395] pci 0000:00:1c.3: setting latency timer to 64
[    0.611402] pci 0000:00:1c.4: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.611407] pci 0000:00:1c.4: setting latency timer to 64
[    0.611415] pci 0000:00:1c.5: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    0.611419] pci 0000:00:1c.5: setting latency timer to 64
[    0.611426] pci 0000:00:1e.0: setting latency timer to 64
[    0.611430] bus: 00 index 0 io port: [0, ffff]
[    0.611432] bus: 00 index 1 mmio: [0, ffffffff]
[    0.611434] bus: 06 index 0 io port: [c000, cfff]
[    0.611437] bus: 06 index 1 mmio: [ff900000, ff9fffff]
[    0.611439] bus: 06 index 2 mmio: [cff00000, efefffff]
[    0.611441] bus: 06 index 3 mmio: [0, 0]
[    0.611443] bus: 05 index 0 mmio: [0, 0]
[    0.611445] bus: 05 index 1 mmio: [0, 0]
[    0.611448] bus: 05 index 2 mmio: [cfe00000, cfefffff]
[    0.611450] bus: 05 index 3 mmio: [0, 0]
[    0.611452] bus: 04 index 0 io port: [b000, bfff]
[    0.611454] bus: 04 index 1 mmio: [ff800000, ff8fffff]
[    0.611457] bus: 04 index 2 mmio: [0, 0]
[    0.611459] bus: 04 index 3 mmio: [0, 0]
[    0.611461] bus: 03 index 0 io port: [a000, afff]
[    0.611463] bus: 03 index 1 mmio: [ff700000, ff7fffff]
[    0.611465] bus: 03 index 2 mmio: [0, 0]
[    0.611467] bus: 03 index 3 mmio: [0, 0]
[    0.611470] bus: 02 index 0 io port: [9000, 9fff]
[    0.611472] bus: 02 index 1 mmio: [ff600000, ff6fffff]
[    0.611474] bus: 02 index 2 mmio: [0, 0]
[    0.611476] bus: 02 index 3 mmio: [0, 0]
[    0.611478] bus: 01 index 0 mmio: [0, 0]
[    0.611480] bus: 01 index 1 mmio: [ff500000, ff5fffff]
[    0.611483] bus: 01 index 2 mmio: [0, 0]
[    0.611485] bus: 01 index 3 io port: [0, ffff]
[    0.611487] bus: 01 index 4 mmio: [0, ffffffff]
[    0.611495] NET: Registered protocol family 2
[    0.624053] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.624290] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.624669] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.624877] TCP: Hash tables configured (established 131072 bind 65536)
[    0.624880] TCP reno registered
[    0.632082] NET: Registered protocol family 1
[    0.632195] checking if image is initramfs... it is
[    1.361376] Freeing initrd memory: 8011k freed
[    1.362537] audit: initializing netlink socket (disabled)
[    1.362561] type=2000 audit(1234708455.360:1): initialized
[    1.368834] highmem bounce pool size: 64 pages
[    1.368840] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    1.371286] VFS: Disk quotas dquot_6.5.1
[    1.371377] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    1.371483] msgmni has been set to 1761
[    1.371610] io scheduler noop registered
[    1.371613] io scheduler anticipatory registered
[    1.371616] io scheduler deadline registered
[    1.371628] io scheduler cfq registered (default)
[    1.371726] pci 0000:06:00.0: Boot video device
[    1.371856] pcieport-driver 0000:00:01.0: setting latency timer to 64
[    1.371892] pcieport-driver 0000:00:01.0: found MSI capability
[    1.371923] pci_express 0000:00:01.0:pcie00: allocate port service
[    1.371968] pci_express 0000:00:01.0:pcie03: allocate port service
[    1.372059] pcieport-driver 0000:00:1c.0: setting latency timer to 64
[    1.372092] pcieport-driver 0000:00:1c.0: found MSI capability
[    1.372125] pci_express 0000:00:1c.0:pcie00: allocate port service
[    1.372173] pci_express 0000:00:1c.0:pcie02: allocate port service
[    1.372214] pci_express 0000:00:1c.0:pcie03: allocate port service
[    1.372303] pcieport-driver 0000:00:1c.3: setting latency timer to 64
[    1.372335] pcieport-driver 0000:00:1c.3: found MSI capability
[    1.372369] pci_express 0000:00:1c.3:pcie00: allocate port service
[    1.372409] pci_express 0000:00:1c.3:pcie03: allocate port service
[    1.372498] pcieport-driver 0000:00:1c.4: setting latency timer to 64
[    1.372536] pcieport-driver 0000:00:1c.4: found MSI capability
[    1.372569] pci_express 0000:00:1c.4:pcie00: allocate port service
[    1.372610] pci_express 0000:00:1c.4:pcie03: allocate port service
[    1.372698] pcieport-driver 0000:00:1c.5: setting latency timer to 64
[    1.372731] pcieport-driver 0000:00:1c.5: found MSI capability
[    1.372763] pci_express 0000:00:1c.5:pcie00: allocate port service
[    1.372804] pci_express 0000:00:1c.5:pcie03: allocate port service
[    1.373141] isapnp: Scanning for PnP cards...
[    1.705199] isapnp: No Plug & Play device found
[    1.739656] hpet_resources: 0xfed00000 is busy
[    1.739729] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
[    1.739852] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.740672] 00:0d: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.742572] brd: module loaded
[    1.742648] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[    1.742783] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f03:PS2M] at 0x60,0x64 irq 1,12
[    1.745318] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.745325] serio: i8042 AUX port at 0x60,0x64 irq 12
[    1.745553] mice: PS/2 mouse device common for all mice
[    1.745682] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0
[    1.745704] rtc0: alarms up to one month, hpet irqs
[    1.745841] EISA: Probing bus 0 at eisa.0
[    1.745868] EISA: Detected 0 cards.
[    1.745871] cpuidle: using governor ladder
[    1.745874] cpuidle: using governor menu
[    1.746410] TCP cubic registered
[    1.746437] Using IPI No-Shortcut mode
[    1.746614] registered taskstats version 1
[    1.746758]   Magic number: 13:614:586
[    1.746787] tty ptyc4: hash matches
[    1.746845] rtc_cmos 00:03: setting system clock to 2009-02-15 14:34:16 UTC (1234708456)
[    1.746849] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.746851] EDD information not available.
[    1.747040] Freeing unused kernel memory: 424k freed
[    1.747079] Write protecting the kernel text: 2580k
[    1.747107] Write protecting the kernel read-only data: 940k
[    1.763308] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[    1.894099] fuse init (API version 7.9)
[    1.996926] ACPI Error (psparse-0530): Method parse/execution failed [\_PR_.CPU1._OSC] (Node f7411198), AE_ALREADY_EXISTS
[    1.996937] ACPI: Marking method _OSC as Serialized because of AE_ALREADY_EXISTS error
[    1.996986] ACPI Error (psparse-0530): Method parse/execution failed [\_PR_.CPU1._PDC] (Node f7411180), AE_ALREADY_EXISTS
[    1.996993] ACPI: Marking method _PDC as Serialized because of AE_ALREADY_EXISTS error
[    1.997117] processor ACPI0007:00: registered as cooling_device0
[    1.997122] ACPI: Processor [CPU1] (supports 8 throttling states)
[    1.997431] ACPI Error (psparse-0530): Method parse/execution failed [\_PR_.CPU2._OSC] (Node f7411270), AE_ALREADY_EXISTS
[    1.997439] ACPI: Marking method _OSC as Serialized because of AE_ALREADY_EXISTS error
[    1.997484] ACPI Error (psparse-0530): Method parse/execution failed [\_PR_.CPU2._PDC] (Node f7411258), AE_ALREADY_EXISTS
[    1.997491] ACPI: Marking method _PDC as Serialized because of AE_ALREADY_EXISTS error
[    1.997605] processor ACPI0007:01: registered as cooling_device1
[    1.997610] ACPI: Processor [CPU2] (supports 8 throttling states)
[    2.319968] usbcore: registered new interface driver usbfs
[    2.319992] usbcore: registered new interface driver hub
[    2.320039] usbcore: registered new device driver usb
[    2.330058] USB Universal Host Controller Interface driver v3.0
[    2.330120] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    2.330130] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    2.330133] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    2.330189] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[    2.330220] uhci_hcd 0000:00:1d.0: irq 20, io base 0x0000e480
[    2.330366] usb usb1: configuration #1 chosen from 1 choice
[    2.330394] hub 1-0:1.0: USB hub found
[    2.330401] hub 1-0:1.0: 2 ports detected
[    2.332397] No dock devices found.
[    2.347780] SCSI subsystem initialized
[    2.432231] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    2.432242] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    2.432245] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    2.432272] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[    2.432303] uhci_hcd 0000:00:1d.1: irq 17, io base 0x0000e800
[    2.432394] usb usb2: configuration #1 chosen from 1 choice
[    2.432426] hub 2-0:1.0: USB hub found
[    2.432436] hub 2-0:1.0: 2 ports detected
[    2.439862] libata version 3.00 loaded.
[    2.455368] Warning! ehci_hcd should always be loaded before uhci_hcd and ohci_hcd, not after
[    2.536284] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    2.536295] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    2.536299] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    2.536327] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
[    2.536358] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000e880
[    2.536451] usb usb3: configuration #1 chosen from 1 choice
[    2.536484] hub 3-0:1.0: USB hub found
[    2.536491] hub 3-0:1.0: 2 ports detected
[    2.640260] uhci_hcd 0000:00:1d.3: PCI INT D -> GSI 19 (level, low) -> IRQ 19
[    2.640272] uhci_hcd 0000:00:1d.3: setting latency timer to 64
[    2.640276] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[    2.640303] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 4
[    2.640335] uhci_hcd 0000:00:1d.3: irq 19, io base 0x0000ec00
[    2.640428] usb usb4: configuration #1 chosen from 1 choice
[    2.640456] hub 4-0:1.0: USB hub found
[    2.640463] hub 4-0:1.0: 2 ports detected
[    2.849075] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    2.849091] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    2.849095] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    2.849125] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 5
[    2.853021] ehci_hcd 0000:00:1d.7: debug port 1
[    2.853027] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
[    2.853035] ehci_hcd 0000:00:1d.7: irq 20, io mem 0xffafbc00
[    2.960016] usb 4-1: new full speed USB device using uhci_hcd and address 2
[    2.972012] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    2.972148] usb usb5: configuration #1 chosen from 1 choice
[    2.972178] hub 5-0:1.0: USB hub found
[    2.972186] hub 5-0:1.0: 8 ports detected
[    3.028038] hub 4-0:1.0: unable to enumerate USB device on port 1
[    3.180190] ata_piix 0000:00:1f.1: version 2.12
[    3.180206] ata_piix 0000:00:1f.1: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[    3.180245] ata_piix 0000:00:1f.1: setting latency timer to 64
[    3.180308] scsi0 : ata_piix
[    3.180398] scsi1 : ata_piix
[    3.181940] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xffa0 irq 14
[    3.181943] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xffa8 irq 15
[    3.292014] usb 5-7: new high speed USB device using ehci_hcd and address 2
[    3.344330] ata1.00: ATAPI: HL-DT-ST DVDRAM GSA-H10N, JL10, max UDMA/33
[    3.360268] ata1.00: configured for UDMA/33
[    3.425407] usb 5-7: configuration #1 chosen from 1 choice
[    3.425853] hub 5-7:1.0: USB hub found
[    3.426083] hub 5-7:1.0: 4 ports detected
[    3.530472] scsi 0:0:0:0: CD-ROM            HL-DT-ST DVDRAM GSA-H10N  JL10 PQ: 0 ANSI: 5
[    3.530894] ata_piix 0000:00:1f.2: PCI INT B -> GSI 23 (level, low) -> IRQ 23
[    3.530899] ata_piix 0000:00:1f.2: MAP [ P0 P2 P1 P3 ]
[    3.684020] ata_piix 0000:00:1f.2: setting latency timer to 64
[    3.684074] scsi2 : ata_piix
[    3.684359] scsi3 : ata_piix
[    3.684411] ata3: SATA max UDMA/133 cmd 0xe400 ctl 0xe080 bmdma 0xd880 irq 23
[    3.684414] ata4: SATA max UDMA/133 cmd 0xe000 ctl 0xdc00 bmdma 0xd888 irq 23
[    3.704341] usb 5-7.3: new high speed USB device using ehci_hcd and address 3
[    3.802670] usb 5-7.3: configuration #1 chosen from 1 choice
[    3.892262] ata3.00: ATA-7: ST3250820AS, 3.AAC, max UDMA/133
[    3.892265] ata3.00: 488397168 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    3.958900] ata3.00: configured for UDMA/133
[    4.560285] ata4.00: unsupported device, disabling
[    4.560287] ata4.00: disabled
[    4.560384] scsi 2:0:0:0: Direct-Access     ATA      ST3250820AS      3.AA PQ: 0 ANSI: 5
[    4.560481] sky2 0000:04:00.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    4.560490] sky2 0000:04:00.0: setting latency timer to 64
[    4.560518] sky2 0000:04:00.0: v1.22 addr 0xff8fc000 irq 19 Yukon-2 EC rev 2
[    4.560946] sky2 eth0: addr 00:18:f3:64:78:25
[    4.560963] sky2 0000:03:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    4.560970] sky2 0000:03:00.0: setting latency timer to 64
[    4.560986] sky2 0000:03:00.0: v1.22 addr 0xff7fc000 irq 16 Yukon-2 EC rev 2
[    4.561395] sky2 eth1: addr 00:18:f3:64:53:6d
[    4.561431] pata_jmicron 0000:02:00.1: enabling device (0000 -> 0001)
[    4.561438] pata_jmicron 0000:02:00.1: PCI INT B -> GSI 18 (level, low) -> IRQ 18
[    4.561470] pata_jmicron 0000:02:00.1: setting latency timer to 64
[    4.561527] scsi4 : pata_jmicron
[    4.561704] scsi5 : pata_jmicron
[    4.562546] ata5: PATA max UDMA/100 cmd 0x9c00 ctl 0x9880 bmdma 0x9400 irq 18
[    4.562549] ata6: PATA max UDMA/100 cmd 0x9800 ctl 0x9480 bmdma 0x9408 irq 18
[    4.882855] ahci 0000:02:00.0: version 3.0
[    4.882874] ahci 0000:02:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    4.896036] ahci 0000:02:00.0: AHCI 0001.0000 32 slots 2 ports 3 Gbps 0x3 impl SATA mode
[    4.896040] ahci 0000:02:00.0: flags: 64bit ncq pm led clo pmp pio slum part 
[    4.896047] ahci 0000:02:00.0: setting latency timer to 64
[    4.896168] scsi6 : ahci
[    4.896536] scsi7 : ahci
[    4.896610] ata7: SATA max UDMA/133 abar m8192@0xff6fe000 port 0xff6fe100 irq 17
[    4.896614] ata8: SATA max UDMA/133 abar m8192@0xff6fe000 port 0xff6fe180 irq 17
[    5.380020] ata7: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    5.517948] ata7.00: ATA-6: WD My Book, 01.01B01, max UDMA/133
[    5.517951] ata7.00: 1953525168 sectors, multi 0: LBA48 NCQ (depth 1)
[    5.690932] ata7.00: configured for UDMA/133
[    6.024024] ata8: SATA link down (SStatus 0 SControl 300)
[    6.040108] scsi 6:0:0:0: Direct-Access     ATA      WD My Book       01.0 PQ: 0 ANSI: 5
[    6.040248] ohci1394 0000:01:03.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[    6.089980] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[21]  MMIO=[ff5ff800-ff5fffff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[    6.100708] scsi 0:0:0:0: Attached scsi generic sg0 type 5
[    6.100749] scsi 2:0:0:0: Attached scsi generic sg1 type 0
[    6.100789] scsi 6:0:0:0: Attached scsi generic sg2 type 0
[    6.125563] Driver 'sd' needs updating - please use bus_type methods
[    6.125674] sd 2:0:0:0: [sda] 488397168 512-byte hardware sectors (250059 MB)
[    6.125692] sd 2:0:0:0: [sda] Write Protect is off
[    6.125695] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    6.125723] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    6.125796] sd 2:0:0:0: [sda] 488397168 512-byte hardware sectors (250059 MB)
[    6.125812] sd 2:0:0:0: [sda] Write Protect is off
[    6.125815] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    6.125843] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    6.125847]  sda:<4>Driver 'sr' needs updating - please use bus_type methods
[    6.139263]  sda1 sda2 <sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
[    6.146028] Uniform CD-ROM driver Revision: 3.20
[    6.146113] sr 0:0:0:0: Attached scsi CD-ROM sr0
[    6.151231]  sda5 sda6 >
[    6.158765] sd 2:0:0:0: [sda] Attached SCSI disk
[    6.158840] sd 6:0:0:0: [sdb] 1953525168 512-byte hardware sectors (1000205 MB)
[    6.158857] sd 6:0:0:0: [sdb] Write Protect is off
[    6.158860] sd 6:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[    6.158888] sd 6:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    6.158947] sd 6:0:0:0: [sdb] 1953525168 512-byte hardware sectors (1000205 MB)
[    6.158963] sd 6:0:0:0: [sdb] Write Protect is off
[    6.158966] sd 6:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[    6.158993] sd 6:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    6.158997]  sdb: sdb1
[    6.533946] sd 6:0:0:0: [sdb] Attached SCSI disk
[    6.818865] PM: Starting manual resume from disk
[    6.818868] PM: Resume from partition 8:5
[    6.818870] PM: Checking hibernation image.
[    6.819045] PM: Resume from disk failed.
[    6.856258] EXT3-fs: INFO: recovery required on readonly filesystem.
[    6.856262] EXT3-fs: write access will be enabled during recovery.
[    7.364269] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[0011d80000df310b]
[   16.901174] kjournald starting.  Commit interval 5 seconds
[   16.901184] EXT3-fs: recovery complete.
[   16.917759] EXT3-fs: mounted filesystem with ordered data mode.
[   21.132351] udevd version 124 started
[   21.649134] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   21.689391] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   21.768639] EDAC MC: Ver: 2.1.0 Jan 29 2009
[   21.937937] iTCO_vendor_support: vendor-support=0
[   21.992696] input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input2
[   22.012037] ACPI: Power Button (FF) [PWRF]
[   22.012195] input: Power Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input3
[   22.044023] ACPI: Power Button (CM) [PWRB]
[   22.120517] EDAC i82975x: ECC disabled on both channels.
[   22.164131] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.03 (30-Apr-2008)
[   22.167260] iTCO_wdt: Found a ICH7 or ICH7R TCO device (Version=2, TCOBASE=0x0860)
[   22.167345] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   22.288286] Linux agpgart interface v0.103
[   22.332002] intel_rng: FWH not detected
[   22.513844] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
[   22.558835] [fglrx] Maximum main memory to use for locked dma buffers: 926 MBytes.
[   22.559289] [fglrx]   vendor: 1002 device: 71ce count: 1
[   22.560380] [fglrx] ioport: bar 4, base 0xc800, size: 0x100
[   22.560395] pci 0000:06:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   22.560401] pci 0000:06:00.0: setting latency timer to 64
[   22.561958] [fglrx] PAT is enabled successfully!
[   22.562029] [fglrx] module loaded - fglrx 8.54.3 [Oct 10 2008] with 1 minors
[   22.647253] input: PC Speaker as /devices/platform/pcspkr/input/input4
[   22.979788] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[   22.979808] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   23.138449] phy0: Selected rate control algorithm 'pid'
[   23.321244] phy0: hwaddr 00:15:af:09:ae:b5, RTL8187vB (default) V1 + rtl8225z2
[   23.321270] usbcore: registered new interface driver rtl8187
[   23.488736] input: ImPS/2 Generic Wheel Mouse as /devices/platform/i8042/serio1/input/input5
[   24.061722] lp: driver loaded but no devices found
[   24.241871] Adding 2634620k swap on /dev/sda5.  Priority:-1 extents:1 across:2634620k
[   24.788095] EXT3 FS on sda1, internal journal
[   69.781528] ReiserFS: sda6: found reiserfs format "3.6" with standard journal
[   69.781539] ReiserFS: sda6: using ordered data mode
[   69.788721] ReiserFS: sda6: journal params: device sda6, size 8192, journal first block 18, max trans len 1024, max batch 900, max commit age 30, max trans age 30
[   69.788930] ReiserFS: sda6: checking transaction log (sda6)
[   69.847531] ReiserFS: sda6: Using r5 hash to sort names
[   70.019998] type=1505 audit(1234708525.084:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=5082
[   70.190201] type=1505 audit(1234708525.256:3): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=5087
[   70.190410] type=1505 audit(1234708525.256:4): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=5087
[   70.278744] ip_tables: (C) 2000-2006 Netfilter Core Team
[   70.701467] ACPI: WMI: Mapper loaded
[   71.422124] warning: `avahi-daemon' uses 32-bit capabilities (legacy support in use)
[   71.577706] NET: Registered protocol family 10
[   71.578548] lo: Disabled Privacy Extensions
[   71.648998] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[   71.649003] apm: disabled - APM is not SMP safe.
[   71.868022] ppdev: user-space parallel port driver
[   74.193593] Bluetooth: Core ver 2.13
[   74.194040] NET: Registered protocol family 31
[   74.194045] Bluetooth: HCI device and connection manager initialized
[   74.194049] Bluetooth: HCI socket layer initialized
[   74.212792] Bluetooth: L2CAP ver 2.11
[   74.212798] Bluetooth: L2CAP socket layer initialized
[   74.224734] Bluetooth: SCO (Voice Link) ver 0.6
[   74.224742] Bluetooth: SCO socket layer initialized
[   74.245876] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   74.245882] Bluetooth: BNEP filters: protocol multicast
[   74.281244] Bridge firewalling registered
[   74.343715] Bluetooth: RFCOMM socket layer initialized
[   74.343918] Bluetooth: RFCOMM TTY layer initialized
[   74.343923] Bluetooth: RFCOMM ver 1.10
[   76.437631] [fglrx] Reserved FB block: Shared offset:0, size:1000000 
[   76.437640] [fglrx] Reserved FB block: Unshared offset:1000000, size:5000 
[   76.437643] [fglrx] Reserved FB block: Unshared offset:ffbb000, size:44000 
[   76.437649] [fglrx] Reserved FB block: Unshared offset:ffff000, size:1000 
[   78.440239] sky2 eth1: enabling interface
[   78.442482] ADDRCONF(NETDEV_UP): eth1: link is not ready
[   78.443487] sky2 eth0: enabling interface
[   78.445715] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   87.065623] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   87.140943] NET: Registered protocol family 17
[  187.941345] wlan0: authenticate with AP 00:1d:19:15:a8:e8
[  187.943068] wlan0: authenticated
[  187.943074] wlan0: associate with AP 00:1d:19:15:a8:e8
[  187.946320] wlan0: RX AssocResp from 00:1d:19:15:a8:e8 (capab=0x451 status=0 aid=1)
[  187.946325] wlan0: associated
[  187.946821] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  189.037945] padlock: VIA PadLock not detected.
[  198.540021] wlan0: no IPv6 routers present
[13384.825211] ata7.00: exception Emask 0x10 SAct 0x1 SErr 0x780100 action 0x6
[13384.825219] ata7.00: irq_stat 0x08000000
[13384.825222] ata7: SError: { UnrecovData 10B8B Dispar BadCRC Handshk }
[13384.825229] ata7.00: cmd 60/f8:00:27:0a:92/00:00:03:00:00/40 tag 0 ncq 126976 in
[13384.825231]          res 40/00:04:27:0a:92/00:00:03:00:00/40 Emask 0x10 (ATA bus error)
[13384.825235] ata7.00: status: { DRDY }
[13384.825241] ata7: hard resetting link
[13385.144031] ata7: SATA link down (SStatus 0 SControl 300)
[13390.144017] ata7: hard resetting link
[13390.468033] ata7: SATA link down (SStatus 0 SControl 300)
[13395.468017] ata7: hard resetting link
[13395.788033] ata7: SATA link down (SStatus 0 SControl 300)
[13395.788045] ata7.00: disabled
[13395.788068] sd 6:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[13395.788074] sd 6:0:0:0: [sdb] Sense Key : Aborted Command [current] [descriptor]
[13395.788080] Descriptor sense data with sense descriptors (in hex):
[13395.788083]         72 0b 00 00 00 00 00 0c 00 0a 80 00 00 00 00 00 
[13395.788096]         03 92 0a 27 
[13395.788102] sd 6:0:0:0: [sdb] Add. Sense: No additional sense information
[13395.788108] end_request: I/O error, dev sdb, sector 59902503
[13395.788114] Buffer I/O error on device sdb1, logical block 7487805
[13395.788123] Buffer I/O error on device sdb1, logical block 7487806
[13395.788127] Buffer I/O error on device sdb1, logical block 7487807
[13395.788132] Buffer I/O error on device sdb1, logical block 7487808
[13395.788136] Buffer I/O error on device sdb1, logical block 7487809
[13395.788140] Buffer I/O error on device sdb1, logical block 7487810
[13395.788144] Buffer I/O error on device sdb1, logical block 7487811
[13395.788148] Buffer I/O error on device sdb1, logical block 7487812
[13395.788152] Buffer I/O error on device sdb1, logical block 7487813
[13395.788156] Buffer I/O error on device sdb1, logical block 7487814
[13395.788194] ata7: EH complete
[13395.788204] ata7.00: detaching (SCSI 6:0:0:0)
[13395.830704] sd 6:0:0:0: [sdb] Synchronizing SCSI cache
[13395.830769] sd 6:0:0:0: [sdb] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK,SUGGEST_OK
[13395.830778] sd 6:0:0:0: [sdb] Stopping disk
[13395.831585] sd 6:0:0:0: [sdb] START_STOP FAILED
[13395.831591] sd 6:0:0:0: [sdb] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK,SUGGEST_OK
```

---

### Post by Thiras on 2009-02-15
Anyone help?

---

### Post by cariboo on 2009-02-15
You are getting errors, I would suggest you unmount the drive and run fsck on the drive eg:

```
sudo fsck -a /dev/sdx
```

Where /dev/sdx is the device label of your external drive.

Jim

---

### Post by Thiras on 2009-02-24
i checked my disk. Everything is OK. Its perfecty working on MS Win. But same problem still continue on Ubuntu Intrepid.

---

### Post by RaZoR1394 on 2009-02-26
What firmware are you running on the WD MyBook case? I'm running 1.034 and I'm also having this problem:

> 
[ 1314.963386] ata12: exception Emask 0x10 SAct 0x0 SErr 0x4010000 action 0xe frozen
[ 1314.963390] ata12: edma_err_cause=00000010 pp_flags=00000000, dev connect
[ 1314.963394] ata12: SError: { PHYRdyChg DevExch }
[ 1314.963401] ata12: hard resetting link
[ 1316.837039] ata12: SATA link down (SStatus 0 SControl 300)
[ 1316.837050] ata12: EH complete


I can't even use it because it doesn't show up but dmesg shows that message instead when I try to connect the cable.

> 
04:00.0 SCSI storage controller: Marvell Technology Group Ltd. 88SX7042 PCI-e 4-port SATA-II (rev 02)


That's the controller I use. I've updated the WD enclosure firmware but I have not updated my Marvell card.

---

### Post by Guilden_NL on 2009-02-27
This popped up out of nowhere for me on an HP HDX notebook. Ran smartmontools and everything is fine.  Spent 5+ hours combing the net and I came to the conclusion that a recent Ubuntu update re-introduced a bug back in.  Not sure if there was a kernel update recently, but it's a good place to look.

I found this thread when it popped up on my hand built desktop when I connected to my one month old WD Mybook 1TB drive.  

Soooo, looks like someone screwed up with a very recent update.
More reading to do tonight about recent changes to Intrepid.... :mad:

---

### Post by finite9 on 2009-03-02
this post is not helpful in any way... more of a warning to others...

Damn im glad I sold my 2 WD Mybook 500GB drives that I was running in RAID-0.  Major issues with speed ( it really was slow), drives going to sleep and upon wake up doing raid resync, and controller issues.  It took me forever to sell them, but I bought some WD RE3 1TB drives instead and they are fantastic.  I now avoid external hard drives like the plague... especially from WD in any case.

---

### Post by RaZoR1394 on 2009-03-08
I fixed my problem by removing 3mm of rubber on the male connector on the cable. The female connector on the enclosure was badly designed as the data pins are buried too deep, thus you need a special cable or modify your own. I have only tried on two machines with Windows with different controller cards but these computers could not use the drive at all without the modification and I'm sure it should work in Linux as well.

This was only a solution for my problem (if you can't use the drive at all and the drive seems to get detected if you push a standard male cable connector as deep as you can and the computer looses the drive as soon as you stop pushing it).

---

