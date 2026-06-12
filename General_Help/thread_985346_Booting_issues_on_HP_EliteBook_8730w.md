---
title: "Booting issues on HP EliteBook 8730w"
date: 2008-11-17
forum: General Help
---

### Post by Joh_ on 2008-11-17
I just installed 8.10 x86-64 on my brand new [EliteBook 8730w](http://h10010.www1.hp.com/wwpc/us/en/sm/WF06a/321957-321957-64295-3740645-3329741-3784202.html) with the T9400, 4 GB RAM, 250 GB hdd, Quadro FX 2700M and the LightScribe writer, however when I try to boot it won't always agree but freezes randomly. I have no idea why and don't know where to start looking. Since it won't manage to boot I can't check dmesg. Is there some place where dmesg keeps logs of previous boots? Any idea of what might be the issue? Any input would be much appreciated.

The attached "screenshot" shows where it freezes and below is the dmesg output of a successful boot.

```

[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.27-7-generic (buildd@yellow) (gcc version 4.3.2 (Ubuntu 4.3.2-1ubuntu10) ) #1 SMP Fri Oct 24 06:40:41 UTC 2008 (Ubuntu 2.6.27-7.14-generic)
[    0.000000] Command line: root=UUID=00c119b0-10ca-4296-a8f8-437e3411144d ro
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   Centaur CentaurHauls
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000ef000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 00000000bcf81000 (usable)
[    0.000000]  BIOS-e820: 00000000bcf81000 - 00000000bcf83000 (reserved)
[    0.000000]  BIOS-e820: 00000000bcf83000 - 00000000bd8ce000 (usable)
[    0.000000]  BIOS-e820: 00000000bd8ce000 - 00000000bdace000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000bdace000 - 00000000bfc70000 (usable)
[    0.000000]  BIOS-e820: 00000000bfc70000 - 00000000bfc80000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000bfc80000 - 00000000bfd93000 (usable)
[    0.000000]  BIOS-e820: 00000000bfd93000 - 00000000bfd9b000 (reserved)
[    0.000000]  BIOS-e820: 00000000bfd9b000 - 00000000bfdbf000 (usable)
[    0.000000]  BIOS-e820: 00000000bfdbf000 - 00000000bfdcf000 (reserved)
[    0.000000]  BIOS-e820: 00000000bfdcf000 - 00000000bfecf000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000bfecf000 - 00000000bfeff000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000bfeff000 - 00000000bff00000 (usable)
[    0.000000]  BIOS-e820: 00000000bff00000 - 00000000c0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed10000 - 00000000fed14000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed18000 - 00000000fed1a000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed1c000 - 00000000fed20000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000ffe80000 - 0000000100000000 (reserved)
[    0.000000]  BIOS-e820: 0000000100000000 - 000000013c000000 (usable)
[    0.000000] last_pfn = 0x13c000 max_arch_pfn = 0x3ffffffff
[    0.000000] last_pfn = 0xbff00 max_arch_pfn = 0x3ffffffff
[    0.000000] init_memory_mapping
[    0.000000]  0000000000 - 00bfe00000 page 2M
[    0.000000]  00bfe00000 - 00bff00000 page 4k
[    0.000000] kernel direct mapping tables up to bff00000 @ 8000-d000
[    0.000000] last_map_addr: bff00000 end: bff00000
[    0.000000] init_memory_mapping
[    0.000000]  0100000000 - 013c000000 page 2M
[    0.000000] kernel direct mapping tables up to 13c000000 @ b000-11000
[    0.000000] last_map_addr: 13c000000 end: 13c000000
[    0.000000] RAMDISK: 377b1000 - 37fef019
[    0.000000] DMI 2.4 present.
[    0.000000] ACPI: RSDP 000F68B0, 0024 (r2 HPQOEM)
[    0.000000] ACPI: XSDT BFEFE120, 0094 (r1 HPQOEM SLIC-MPC        F       1000013)
[    0.000000] ACPI: FACP BFEFC000, 00F4 (r3 HPQOEM 30EC            F HP          1)
[    0.000000] ACPI: DSDT BFEE0000, 16708 (r1 HPQOEM 30EC            1 INTL 20060912)
[    0.000000] ACPI: FACS BFE9D000, 0040
[    0.000000] ACPI: HPET BFEFB000, 0038 (r1 HPQOEM 30EC            1 HP          1)
[    0.000000] ACPI: APIC BFEFA000, 0084 (r1 HPQOEM 30EC            1 HP          1)
[    0.000000] ACPI: MCFG BFEF9000, 003C (r1 HPQOEM 30EC            1 HP          1)
[    0.000000] ACPI: TCPA BFEF7000, 0032 (r2 HPQOEM 30EC            0 HP          1)
[    0.000000] ACPI: SSDT BFEDF000, 064F (r1 HPQOEM  SataPri     1000 INTL 20060912)
[    0.000000] ACPI: SSDT BFEDE000, 069C (r1 HPQOEM  SataSec     1000 INTL 20060912)
[    0.000000] ACPI: SLIC BFEDB000, 0176 (r1 HPQOEM SLIC-MPC        1 HP          1)
[    0.000000] ACPI: SSDT BFED8000, 1D4F (r1 HPQOEM NVIDIAGF        1 INTL 20060912)
[    0.000000] ACPI: DMAR BFED7000, 0098 (r1                       1             0)
[    0.000000] ACPI: ASF! BFEF8000, 0095 (r32 HPQOEM 30EC            1 HP          1)
[    0.000000] ACPI: SSDT BFED6000, 066C (r1  PmRef    CpuPm     3000 INTL 20060912)
[    0.000000] ACPI: SSDT BFED5000, 0288 (r1  PmRef  Cpu0Tst     3000 INTL 20060912)
[    0.000000] ACPI: SSDT BFED4000, 0225 (r1  PmRef    ApTst     3000 INTL 20060912)
[    0.000000] ACPI: DMI detected: Hewlett-Packard
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at 0000000000000000-000000013c000000
[    0.000000] Bootmem setup node 0 0000000000000000-000000013c000000
[    0.000000]   NODE_DATA [0000000000001000 - 0000000000005fff]
[    0.000000]   bootmap [000000000000c000 -  00000000000337ff] pages 28
[    0.000000] (7 early reservations) ==> bootmem [0000000000 - 013c000000]
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000]   #1 [0000006000 - 0000008000]       TRAMPOLINE ==> [0000006000 - 0000008000]
[    0.000000]   #2 [0000200000 - 00008b8f9c]    TEXT DATA BSS ==> [0000200000 - 00008b8f9c]
[    0.000000]   #3 [00377b1000 - 0037fef019]          RAMDISK ==> [00377b1000 - 0037fef019]
[    0.000000]   #4 [000009fc00 - 0000100000]    BIOS reserved ==> [000009fc00 - 0000100000]
[    0.000000]   #5 [0000008000 - 000000b000]          PGTABLE ==> [0000008000 - 000000b000]
[    0.000000]   #6 [000000b000 - 000000c000]          PGTABLE ==> [000000b000 - 000000c000]
[    0.000000]  [ffffe20000000000-ffffe20004ffffff] PMD -> [ffff880028200000-ffff88002c1fffff] on node 0
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000000 -> 0x00001000
[    0.000000]   DMA32    0x00001000 -> 0x00100000
[    0.000000]   Normal   0x00100000 -> 0x0013c000
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[8] active PFN ranges
[    0.000000]     0: 0x00000000 -> 0x0000009f
[    0.000000]     0: 0x00000100 -> 0x000bcf81
[    0.000000]     0: 0x000bcf83 -> 0x000bd8ce
[    0.000000]     0: 0x000bdace -> 0x000bfc70
[    0.000000]     0: 0x000bfc80 -> 0x000bfd93
[    0.000000]     0: 0x000bfd9b -> 0x000bfdbf
[    0.000000]     0: 0x000bfeff -> 0x000bff00
[    0.000000]     0: 0x00100000 -> 0x0013c000
[    0.000000] On node 0 totalpages: 1030981
[    0.000000]   DMA zone: 2112 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 764902 pages, LIFO batch:31
[    0.000000]   Normal zone: 241920 pages, LIFO batch:31
[    0.000000] ACPI: PM-Timer IO Port: 0x408
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x00] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x00] disabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x02] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x03] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 1, version 0, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Setting APIC routing to flat
[    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] SMP: Allowing 4 CPUs, 2 hotplug CPUs
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000ef000
[    0.000000] PM: Registered nosave memory: 00000000000ef000 - 0000000000100000
[    0.000000] PM: Registered nosave memory: 00000000bcf81000 - 00000000bcf83000
[    0.000000] PM: Registered nosave memory: 00000000bd8ce000 - 00000000bdace000
[    0.000000] PM: Registered nosave memory: 00000000bfc70000 - 00000000bfc80000
[    0.000000] PM: Registered nosave memory: 00000000bfd93000 - 00000000bfd9b000
[    0.000000] PM: Registered nosave memory: 00000000bfdbf000 - 00000000bfdcf000
[    0.000000] PM: Registered nosave memory: 00000000bfdcf000 - 00000000bfecf000
[    0.000000] PM: Registered nosave memory: 00000000bfecf000 - 00000000bfeff000
[    0.000000] PM: Registered nosave memory: 00000000bff00000 - 00000000c0000000
[    0.000000] PM: Registered nosave memory: 00000000c0000000 - 00000000e0000000
[    0.000000] PM: Registered nosave memory: 00000000e0000000 - 00000000f0000000
[    0.000000] PM: Registered nosave memory: 00000000f0000000 - 00000000fec00000
[    0.000000] PM: Registered nosave memory: 00000000fec00000 - 00000000fec01000
[    0.000000] PM: Registered nosave memory: 00000000fec01000 - 00000000fed10000
[    0.000000] PM: Registered nosave memory: 00000000fed10000 - 00000000fed14000
[    0.000000] PM: Registered nosave memory: 00000000fed14000 - 00000000fed18000
[    0.000000] PM: Registered nosave memory: 00000000fed18000 - 00000000fed1a000
[    0.000000] PM: Registered nosave memory: 00000000fed1a000 - 00000000fed1c000
[    0.000000] PM: Registered nosave memory: 00000000fed1c000 - 00000000fed20000
[    0.000000] PM: Registered nosave memory: 00000000fed20000 - 00000000fee00000
[    0.000000] PM: Registered nosave memory: 00000000fee00000 - 00000000fee01000
[    0.000000] PM: Registered nosave memory: 00000000fee01000 - 00000000ffe80000
[    0.000000] PM: Registered nosave memory: 00000000ffe80000 - 0000000100000000
[    0.000000] Allocating PCI resources starting at c2000000 (gap: c0000000:20000000)
[    0.000000] PERCPU: Allocating 64928 bytes of per cpu data
[    0.000000] NR_CPUS: 64, nr_cpu_ids: 4, nr_node_ids 1
[    0.000000] Built 1 zonelists in Node order, mobility grouping on.  Total pages: 1008934
[    0.000000] Policy zone: Normal
[    0.000000] Kernel command line: root=UUID=00c119b0-10ca-4296-a8f8-437e3411144d ro
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 32768 bytes)
[    0.000000] Extended CMOS year: 2000
[    0.000000] TSC: PIT calibration confirmed by PMTIMER.
[    0.000000] TSC: using PIT calibration value
[    0.000000] Detected 2526.985 MHz processor.
[    0.004000] Console: colour VGA+ 80x25
[    0.004000] console [tty0] enabled
[    0.004000] Checking aperture...
[    0.004000] No AGP bridge found
[    0.004000] Calgary: detecting Calgary via BIOS EBDA area
[    0.004000] Calgary: Unable to locate Rio Grande table in EBDA - bailing!
[    0.004000] PCI-DMA: Using software bounce buffering for IO (SWIOTLB)
[    0.004000] Placing software IO TLB between 0x20000000 - 0x24000000
[    0.004000] Memory: 3976596k/5177344k available (3112k kernel code, 147328k reserved, 1575k data, 536k init)
[    0.004000] CPA: page pool initialized 1 of 1 pages preallocated
[    0.004000] SLUB: Genslabs=13, HWalign=64, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
[    0.004000] hpet clockevent registered
[    0.004000] Calibrating delay loop (skipped), value calculated using timer frequency.. 5053.97 BogoMIPS (lpj=10107940)
[    0.004000] Security Framework initialized
[    0.004000] SELinux:  Disabled at boot.
[    0.004000] AppArmor: AppArmor initialized
[    0.004000] Dentry cache hash table entries: 524288 (order: 10, 4194304 bytes)
[    0.004000] Inode-cache hash table entries: 262144 (order: 9, 2097152 bytes)
[    0.004988] Mount-cache hash table entries: 256
[    0.005408] Initializing cgroup subsys ns
[    0.005664] Initializing cgroup subsys cpuacct
[    0.005929] Initializing cgroup subsys memory
[    0.006206] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.006649] CPU: L2 cache: 6144K
[    0.006913] CPU 0/0 -> Node 0
[    0.007175] CPU: Physical Processor ID: 0
[    0.007392] CPU: Processor Core ID: 0
[    0.007641] CPU0: Thermal monitoring handled by SMI
[    0.007643] using mwait in idle threads.
[    0.009833] ACPI: Core revision 20080609
[    0.017417] ACPI: Checking initramfs for custom DSDT
[    0.332528] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.372542] CPU0: Intel(R) Core(TM)2 Duo CPU     T9400  @ 2.53GHz stepping 06
[    0.373249] Using local APIC timer interrupts.
[    0.380024] APIC timer calibration result 16624951
[    0.380026] Detected 16.624 MHz APIC timer.
[    0.380395] Booting processor 1/1 ip 6000
[    0.004000] Initializing CPU#1
[    0.004000] Calibrating delay using timer specific routine.. 5053.97 BogoMIPS (lpj=10107953)
[    0.004000] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.004000] CPU: L2 cache: 6144K
[    0.004000] CPU 1/1 -> Node 0
[    0.004000] CPU: Physical Processor ID: 0
[    0.004000] CPU: Processor Core ID: 1
[    0.004000] CPU1: Thermal monitoring enabled (TM2)
[    0.468837] CPU1: Intel(R) Core(TM)2 Duo CPU     T9400  @ 2.53GHz stepping 06
[    0.471543] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
[    0.472057] Brought up 2 CPUs
[    0.472317] Total of 2 processors activated (10107.94 BogoMIPS).
[    0.472585] CPU0 attaching sched-domain:
[    0.472588]  domain 0: span 0-1 level MC
[    0.472589]   groups: 0 1
[    0.472592]   domain 1: span 0-1 level NODE
[    0.472594]    groups: 0-1
[    0.472597] CPU1 attaching sched-domain:
[    0.472599]  domain 0: span 0-1 level MC
[    0.472600]   groups: 1 0
[    0.472602]   domain 1: span 0-1 level NODE
[    0.472603]    groups: 0-1
[    0.472679] net_namespace: 1552 bytes
[    0.472679] Booting paravirtualized kernel on bare hardware
[    0.472767] Time: 21:00:41  Date: 11/17/08
[    0.473057] NET: Registered protocol family 16
[    0.473334] ACPI FADT declares the system doesn't support PCIe ASPM, so disable it
[    0.473334] ACPI: bus type pci registered
[    0.473334] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 255
[    0.473334] PCI: MCFG area at e0000000 reserved in E820
[    0.484566] PCI: Using MMCONFIG at e0000000 - efffffff
[    0.484826] PCI: Using configuration type 1 for base access
[    0.485143] ACPI: EC: Look up EC in DSDT
[    0.488050] ACPI: EC: non-query interrupt received, switching to interrupt mode
[    0.556241] ACPI Error (dswstate-0097): Result stack is empty! State=ffff88013b1e9c00 [20080609]
[    0.556967] ACPI Exception (dsutils-0645): AE_AML_NO_RETURN_VALUE, Missing or null operand [20080609]
[    0.557762] ACPI Exception (dsutils-0762): AE_AML_NO_RETURN_VALUE, While creating Arg 0 [20080609]
[    0.558484] ACPI Error (psparse-0530): Method parse/execution failed [\_TZ_.PSWT] (Node ffff88013ba33660), AE_AML_NO_RETURN_VALUE
[    0.560073] ACPI Error (psparse-0530): Method parse/execution failed [\_TZ_.FOAA] (Node ffff88013ba33ae0), AE_AML_NO_RETURN_VALUE
[    0.561084] ACPI Error (psparse-0530): Method parse/execution failed [\_SB_.PCI0.LPCB.EC0_.PRIT] (Node ffff88013ba3cd80), AE_AML_NO_RETURN_VALUE
[    0.562098] ACPI Error (psparse-0530): Method parse/execution failed [\_SB_.PCI0.LPCB.EC0_.ECRI] (Node ffff88013ba39e60), AE_AML_NO_RETURN_VALUE
[    0.563113] ACPI Error (psparse-0530): Method parse/execution failed [\_SB_.PCI0.LPCB.EC0_._REG] (Node ffff88013ba39e80), AE_AML_NO_RETURN_VALUE
[    0.578371] ACPI: BIOS _OSI(Linux) query ignored via DMI
[    0.591841] ACPI: Interpreter enabled
[    0.592033] ACPI: (supports S0 S3 S4 S5)
[    0.593235] ACPI: Using IOAPIC for interrupt routing
[    0.604304] ACPI: EC: GPE = 0x16, I/O: command/status = 0x66, data = 0x62
[    0.604398] ACPI: EC: driver started in poll mode
[    0.604680] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.604680] pci 0000:00:01.0: PME# supported from D0 D3hot D3cold
[    0.604680] pci 0000:00:01.0: PME# disabled
[    0.604680] PCI: 0000:00:03.0 reg 10 64bit mmio: [db326800, db32680f]
[    0.604680] pci 0000:00:03.0: PME# supported from D0 D3hot D3cold
[    0.604889] pci 0000:00:03.0: PME# disabled
[    0.605181] PCI: 0000:00:03.2 reg 10 io port: [8160, 8167]
[    0.605185] PCI: 0000:00:03.2 reg 14 io port: [817c, 817f]
[    0.605189] PCI: 0000:00:03.2 reg 18 io port: [8158, 815f]
[    0.605194] PCI: 0000:00:03.2 reg 1c io port: [8178, 817b]
[    0.605198] PCI: 0000:00:03.2 reg 20 io port: [8120, 812f]
[    0.605235] PCI: 0000:00:03.3 reg 10 io port: [8150, 8157]
[    0.605239] PCI: 0000:00:03.3 reg 14 32bit mmio: [db325000, db325fff]
[    0.605407] PCI: 0000:00:19.0 reg 10 32bit mmio: [db300000, db31ffff]
[    0.605414] PCI: 0000:00:19.0 reg 14 32bit mmio: [db324000, db324fff]
[    0.605420] PCI: 0000:00:19.0 reg 18 io port: [80c0, 80df]
[    0.605462] pci 0000:00:19.0: PME# supported from D0 D3hot D3cold
[    0.605737] pci 0000:00:19.0: PME# disabled
[    0.608121] PCI: 0000:00:1a.0 reg 20 io port: [80a0, 80bf]
[    0.608231] PCI: 0000:00:1a.1 reg 20 io port: [8080, 809f]
[    0.608341] PCI: 0000:00:1a.2 reg 20 io port: [8060, 807f]
[    0.608437] PCI: 0000:00:1a.7 reg 10 32bit mmio: [db326400, db3267ff]
[    0.608489] pci 0000:00:1a.7: PME# supported from D0 D3hot D3cold
[    0.608757] pci 0000:00:1a.7: PME# disabled
[    0.609096] PCI: 0000:00:1b.0 reg 10 64bit mmio: [db320000, db323fff]
[    0.609178] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    0.609424] pci 0000:00:1b.0: PME# disabled
[    0.609757] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.610033] pci 0000:00:1c.0: PME# disabled
[    0.610411] pci 0000:00:1c.1: PME# supported from D0 D3hot D3cold
[    0.610628] pci 0000:00:1c.1: PME# disabled
[    0.611001] pci 0000:00:1c.2: PME# supported from D0 D3hot D3cold
[    0.611270] pci 0000:00:1c.2: PME# disabled
[    0.611579] pci 0000:00:1c.4: PME# supported from D0 D3hot D3cold
[    0.611844] pci 0000:00:1c.4: PME# disabled
[    0.612143] PCI: 0000:00:1d.0 reg 20 io port: [8040, 805f]
[    0.612270] PCI: 0000:00:1d.1 reg 20 io port: [8020, 803f]
[    0.612359] PCI: 0000:00:1d.2 reg 20 io port: [8000, 801f]
[    0.612449] PCI: 0000:00:1d.7 reg 10 32bit mmio: [db326000, db3263ff]
[    0.612527] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
[    0.612802] pci 0000:00:1d.7: PME# disabled
[    0.613343] PCI: 0000:00:1f.2 reg 10 io port: [8148, 814f]
[    0.613350] PCI: 0000:00:1f.2 reg 14 io port: [8174, 8177]
[    0.613356] PCI: 0000:00:1f.2 reg 18 io port: [8140, 8147]
[    0.613363] PCI: 0000:00:1f.2 reg 1c io port: [8170, 8173]
[    0.613369] PCI: 0000:00:1f.2 reg 20 io port: [8110, 811f]
[    0.613376] PCI: 0000:00:1f.2 reg 24 io port: [8100, 810f]
[    0.613450] PCI: 0000:00:1f.5 reg 10 io port: [8138, 813f]
[    0.613462] PCI: 0000:00:1f.5 reg 14 io port: [816c, 816f]
[    0.613474] PCI: 0000:00:1f.5 reg 18 io port: [8130, 8137]
[    0.613486] PCI: 0000:00:1f.5 reg 1c io port: [8168, 816b]
[    0.613498] PCI: 0000:00:1f.5 reg 20 io port: [80f0, 80ff]
[    0.613510] PCI: 0000:00:1f.5 reg 24 io port: [80e0, 80ef]
[    0.613641] PCI: 0000:01:00.0 reg 10 32bit mmio: [da000000, daffffff]
[    0.613655] PCI: 0000:01:00.0 reg 14 32bit mmio: [c0000000, cfffffff]
[    0.613681] PCI: 0000:01:00.0 reg 1c 64bit mmio: [d8000000, d9ffffff]
[    0.613694] PCI: 0000:01:00.0 reg 24 io port: [7000, 707f]
[    0.613708] PCI: 0000:01:00.0 reg 30 32bit mmio: [fff80000, ffffffff]
[    0.613880] PCI: bridge 0000:00:01.0 io port: [7000, 7fff]
[    0.613882] PCI: bridge 0000:00:01.0 32bit mmio: [d8000000, daffffff]
[    0.613886] PCI: bridge 0000:00:01.0 64bit mmio pref: [c0000000, cfffffff]
[    0.614062] PCI: bridge 0000:00:1c.0 32bit mmio: [db200000, db2fffff]
[    0.614271] PCI: 0000:03:00.0 reg 10 64bit mmio: [db100000, db101fff]
[    0.614397] pci 0000:03:00.0: PME# supported from D0 D3hot D3cold
[    0.614679] pci 0000:03:00.0: PME# disabled
[    0.615086] PCI: bridge 0000:00:1c.1 32bit mmio: [db100000, db1fffff]
[    0.615265] PCI: bridge 0000:00:1c.2 io port: [5000, 6fff]
[    0.615274] PCI: bridge 0000:00:1c.2 32bit mmio: [d4000000, d7ffffff]
[    0.615357] PCI: bridge 0000:00:1c.4 io port: [3000, 4fff]
[    0.615361] PCI: bridge 0000:00:1c.4 32bit mmio: [d0000000, d3ffffff]
[    0.615429] PCI: 0000:86:06.0 reg 10 32bit mmio: [db001000, db0017ff]
[    0.615507] pci 0000:86:06.0: supports D1
[    0.615508] pci 0000:86:06.0: supports D2
[    0.615510] pci 0000:86:06.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.615786] pci 0000:86:06.0: PME# disabled
[    0.616094] PCI: 0000:86:06.1 reg 10 32bit mmio: [db001b00, db001bff]
[    0.616166] pci 0000:86:06.1: supports D1
[    0.616167] pci 0000:86:06.1: supports D2
[    0.616169] pci 0000:86:06.1: PME# supported from D0 D1 D2 D3hot D3cold
[    0.616393] pci 0000:86:06.1: PME# disabled
[    0.616718] PCI: 0000:86:06.2 reg 10 32bit mmio: [db001a00, db001aff]
[    0.616803] pci 0000:86:06.2: supports D1
[    0.616804] pci 0000:86:06.2: supports D2
[    0.616805] pci 0000:86:06.2: PME# supported from D0 D1 D2 D3hot D3cold
[    0.617082] pci 0000:86:06.2: PME# disabled
[    0.617366] PCI: 0000:86:06.3 reg 10 32bit mmio: [db001900, db0019ff]
[    0.617433] pci 0000:86:06.3: supports D1
[    0.617434] pci 0000:86:06.3: supports D2
[    0.617436] pci 0000:86:06.3: PME# supported from D0 D1 D2 D3hot D3cold
[    0.617712] pci 0000:86:06.3: PME# disabled
[    0.618043] PCI: 0000:86:06.4 reg 10 32bit mmio: [db001800, db0018ff]
[    0.618122] pci 0000:86:06.4: supports D1
[    0.618123] pci 0000:86:06.4: supports D2
[    0.618124] pci 0000:86:06.4: PME# supported from D0 D1 D2 D3hot D3cold
[    0.618359] pci 0000:86:06.4: PME# disabled
[    0.618661] PCI: 0000:86:06.5 reg 10 32bit mmio: [db000000, db000fff]
[    0.618693] pci 0000:86:06.5: supports D1
[    0.618694] pci 0000:86:06.5: supports D2
[    0.618695] pci 0000:86:06.5: PME# supported from D0 D1 D2 D3hot D3cold
[    0.618958] pci 0000:86:06.5: PME# disabled
[    0.619310] pci 0000:00:1e.0: transparent bridge
[    0.619542] PCI: bridge 0000:00:1e.0 io port: [2000, 2fff]
[    0.619552] PCI: bridge 0000:00:1e.0 32bit mmio: [db000000, db0fffff]
[    0.619670] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.620283] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEGP._PRT]
[    0.620458] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP01._PRT]
[    0.620619] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP02._PRT]
[    0.620781] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP03._PRT]
[    0.620958] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP05._PRT]
[    0.621160] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIB._PRT]
[    0.640915] ACPI: PCI Interrupt Link [LNKA] (IRQs 1 3 4 5 6 7 *10 12 14 15)
[    0.645799] ACPI: PCI Interrupt Link [LNKB] (IRQs 1 3 4 5 6 7 11 12 14 15) *10
[    0.649124] ACPI: PCI Interrupt Link [LNKC] (IRQs 1 3 4 5 6 7 10 12 14 15) *11
[    0.652636] ACPI: PCI Interrupt Link [LNKD] (IRQs 1 3 4 5 6 7 11 12 14 15) *10
[    0.656178] ACPI: PCI Interrupt Link [LNKE] (IRQs 1 3 4 5 6 7 *10 12 14 15)
[    0.659384] ACPI: PCI Interrupt Link [LNKF] (IRQs 1 3 4 5 6 7 11 12 14 15) *10
[    0.662736] ACPI: PCI Interrupt Link [LNKG] (IRQs 1 3 4 5 6 7 *10 12 14 15)
[    0.665809] ACPI: PCI Interrupt Link [LNKH] (IRQs 1 3 4 5 6 7 11 12 14 15) *0, disabled.
[    0.669500] ACPI: Power Resource [APPR] (off)
[    0.669500] ACPI: Power Resource [LPP] (on)
[    0.669500] ACPI: Power Resource [PGF0] (off)
[    0.669500] Linux Plug and Play Support v0.97 (c) Adam Belay
[    0.669500] pnp: PnP ACPI init
[    0.669500] ACPI: bus type pnp registered
[    0.676597] pnp: PnP ACPI: found 13 devices
[    0.676855] ACPI: ACPI bus type pnp unregistered
[    0.677077] PCI: Using ACPI for IRQ routing
[    0.692037] NET: Registered protocol family 8
[    0.692301] NET: Registered protocol family 20
[    0.692534] NetLabel: Initializing
[    0.692534] NetLabel:  domain hash size = 128
[    0.692570] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.692844] NetLabel:  unlabeled traffic allowed by default
[    0.693080] PCI-GART: No AMD northbridge found.
[    0.693353] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0
[    0.694798] hpet0: 4 64-bit timers, 14318180 Hz
[    0.697909] tracer: 1286 pages allocated for 65536 entries of 80 bytes
[    0.698130]    actual entries 65586
[    0.698459] AppArmor: AppArmor Filesystem Enabled
[    0.698752] ACPI: RTC can wake from S4
[    0.700042] Switched to high resolution mode on CPU 0
[    0.700072] Switched to high resolution mode on CPU 1
[    0.716013] system 00:01: iomem range 0xfed1c000-0xfed1ffff could not be reserved
[    0.716288] system 00:01: iomem range 0xfed10000-0xfed13fff could not be reserved
[    0.716523] system 00:01: iomem range 0xfed18000-0xfed18fff could not be reserved
[    0.716787] system 00:01: iomem range 0xfed19000-0xfed19fff could not be reserved
[    0.717067] system 00:01: iomem range 0xe0000000-0xefffffff could not be reserved
[    0.717348] system 00:01: iomem range 0xfec00000-0xfec00fff could not be reserved
[    0.717588] system 00:01: iomem range 0xfed20000-0xfed3ffff has been reserved
[    0.717853] system 00:01: iomem range 0xfed45000-0xfed8ffff has been reserved
[    0.718121] system 00:05: iomem range 0xfed00000-0xfed003ff has been reserved
[    0.718385] system 00:07: ioport range 0x200-0x27f has been reserved
[    0.718602] system 00:07: ioport range 0x1000-0x1003 has been reserved
[    0.718867] system 00:07: ioport range 0x1010-0x101f has been reserved
[    0.719132] system 00:07: ioport range 0xffff-0xffff has been reserved
[    0.719396] system 00:07: ioport range 0x400-0x47f has been reserved
[    0.719617] system 00:07: ioport range 0x500-0x57f has been reserved
[    0.719881] system 00:07: ioport range 0xef80-0xef9f has been reserved
[    0.725185] pci 0000:01:00.0: BAR 6: can't allocate mem resource [0xd0000000-0xcfffffff]
[    0.725463] pci 0000:00:01.0: PCI bridge, secondary bus 0000:01
[    0.725678] pci 0000:00:01.0:   IO window: 0x7000-0x7fff
[    0.725943] pci 0000:00:01.0:   MEM window: 0xd8000000-0xdaffffff
[    0.726211] pci 0000:00:01.0:   PREFETCH window: 0x000000c0000000-0x000000cfffffff
[    0.726477] pci 0000:00:1c.0: PCI bridge, secondary bus 0000:02
[    0.726702] pci 0000:00:1c.0:   IO window: disabled
[    0.726972] pci 0000:00:1c.0:   MEM window: 0xdb200000-0xdb2fffff
[    0.727247] pci 0000:00:1c.0:   PREFETCH window: disabled
[    0.727491] pci 0000:00:1c.1: PCI bridge, secondary bus 0000:03
[    0.727722] pci 0000:00:1c.1:   IO window: disabled
[    0.727997] pci 0000:00:1c.1:   MEM window: 0xdb100000-0xdb1fffff
[    0.728269] pci 0000:00:1c.1:   PREFETCH window: disabled
[    0.728505] pci 0000:00:1c.2: PCI bridge, secondary bus 0000:04
[    0.728751] pci 0000:00:1c.2:   IO window: 0x5000-0x6fff
[    0.729012] pci 0000:00:1c.2:   MEM window: 0xd4000000-0xd7ffffff
[    0.729275] pci 0000:00:1c.2:   PREFETCH window: disabled
[    0.729511] pci 0000:00:1c.4: PCI bridge, secondary bus 0000:45
[    0.729761] pci 0000:00:1c.4:   IO window: 0x3000-0x4fff
[    0.730032] pci 0000:00:1c.4:   MEM window: 0xd0000000-0xd3ffffff
[    0.730307] pci 0000:00:1c.4:   PREFETCH window: disabled
[    0.730530] pci 0000:86:06.5: CardBus bridge, secondary bus 0000:87
[    0.730787] pci 0000:86:06.5:   IO window: 0x002000-0x0020ff
[    0.731060] pci 0000:86:06.5:   IO window: 0x002400-0x0024ff
[    0.731336] pci 0000:86:06.5:   PREFETCH window: 0xdc000000-0xdfffffff
[    0.731559] pci 0000:86:06.5:   MEM window: 0xf0000000-0xf3ffffff
[    0.731819] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:86
[    0.732095] pci 0000:00:1e.0:   IO window: 0x2000-0x2fff
[    0.732364] pci 0000:00:1e.0:   MEM window: 0xdb000000-0xdb0fffff
[    0.732580] pci 0000:00:1e.0:   PREFETCH window: 0x000000dc000000-0x000000dfffffff
[    0.732873] pci 0000:00:01.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.733135] pci 0000:00:01.0: setting latency timer to 64
[    0.733153] pci 0000:00:1c.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.733421] pci 0000:00:1c.0: setting latency timer to 64
[    0.733447] pci 0000:00:1c.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    0.733677] pci 0000:00:1c.1: setting latency timer to 64
[    0.733703] pci 0000:00:1c.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.737879] pci 0000:00:1c.2: setting latency timer to 64
[    0.737899] pci 0000:00:1c.4: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.738172] pci 0000:00:1c.4: setting latency timer to 64
[    0.738191] pci 0000:00:1e.0: setting latency timer to 64
[    0.738212] pci 0000:86:06.5: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    0.738471] pci 0000:86:06.5: setting latency timer to 64
[    0.738474] bus: 00 index 0 io port: [0, ffff]
[    0.738686] bus: 00 index 1 mmio: [0, ffffffffffffffff]
[    0.738942] bus: 01 index 0 io port: [7000, 7fff]
[    0.739207] bus: 01 index 1 mmio: [d8000000, daffffff]
[    0.739460] bus: 01 index 2 mmio: [c0000000, cfffffff]
[    0.739677] bus: 01 index 3 mmio: [0, 0]
[    0.739940] bus: 02 index 0 mmio: [0, 0]
[    0.740206] bus: 02 index 1 mmio: [db200000, db2fffff]
[    0.740460] bus: 02 index 2 mmio: [0, 0]
[    0.740676] bus: 02 index 3 mmio: [0, 0]
[    0.740939] bus: 03 index 0 mmio: [0, 0]
[    0.741202] bus: 03 index 1 mmio: [db100000, db1fffff]
[    0.741461] bus: 03 index 2 mmio: [0, 0]
[    0.741677] bus: 03 index 3 mmio: [0, 0]
[    0.741941] bus: 04 index 0 io port: [5000, 6fff]
[    0.742205] bus: 04 index 1 mmio: [d4000000, d7ffffff]
[    0.742464] bus: 04 index 2 mmio: [0, 0]
[    0.742677] bus: 04 index 3 mmio: [0, 0]
[    0.742940] bus: 45 index 0 io port: [3000, 4fff]
[    0.743205] bus: 45 index 1 mmio: [d0000000, d3ffffff]
[    0.743458] bus: 45 index 2 mmio: [0, 0]
[    0.743675] bus: 45 index 3 mmio: [0, 0]
[    0.743939] bus: 86 index 0 io port: [2000, 2fff]
[    0.744207] bus: 86 index 1 mmio: [db000000, db0fffff]
[    0.744460] bus: 86 index 2 mmio: [dc000000, dfffffff]
[    0.744678] bus: 86 index 3 io port: [0, ffff]
[    0.744942] bus: 86 index 4 mmio: [0, ffffffffffffffff]
[    0.745207] bus: 87 index 0 io port: [2000, 20ff]
[    0.745460] bus: 87 index 1 io port: [2400, 24ff]
[    0.745678] bus: 87 index 2 mmio: [dc000000, dfffffff]
[    0.745942] bus: 87 index 3 mmio: [f0000000, f3ffffff]
[    0.746213] NET: Registered protocol family 2
[    0.788123] IP route cache hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.789453] TCP established hash table entries: 524288 (order: 11, 8388608 bytes)
[    0.792932] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    0.793677] TCP: Hash tables configured (established 524288 bind 65536)
[    0.793945] TCP reno registered
[    0.804109] NET: Registered protocol family 1
[    0.804463] checking if image is initramfs... it is
[    1.415536] Freeing initrd memory: 8440k freed
[    1.419431] audit: initializing netlink socket (disabled)
[    1.419675] type=2000 audit(1226955641.416:1): initialized
[    1.424783] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    1.426939] VFS: Disk quotas dquot_6.5.1
[    1.427263] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    1.427590] msgmni has been set to 7783
[    1.427941] io scheduler noop registered
[    1.428205] io scheduler anticipatory registered
[    1.428469] io scheduler deadline registered
[    1.428769] io scheduler cfq registered (default)
[    1.429457] pci 0000:01:00.0: Boot video device
[    1.429566] pcieport-driver 0000:00:01.0: setting latency timer to 64
[    1.429592] pcieport-driver 0000:00:01.0: found MSI capability
[    1.429881] pci_express 0000:00:01.0:pcie00: allocate port service
[    1.429912] pci_express 0000:00:01.0:pcie02: allocate port service
[    1.429941] pci_express 0000:00:01.0:pcie03: allocate port service
[    1.430022] pcieport-driver 0000:00:1c.0: setting latency timer to 64
[    1.430130] pcieport-driver 0000:00:1c.0: found MSI capability
[    1.430478] pci_express 0000:00:1c.0:pcie00: allocate port service
[    1.430509] pci_express 0000:00:1c.0:pcie02: allocate port service
[    1.430538] pci_express 0000:00:1c.0:pcie03: allocate port service
[    1.430769] pcieport-driver 0000:00:1c.1: setting latency timer to 64
[    1.430865] pcieport-driver 0000:00:1c.1: found MSI capability
[    1.431200] pci_express 0000:00:1c.1:pcie00: allocate port service
[    1.431236] pci_express 0000:00:1c.1:pcie02: allocate port service
[    1.431270] pci_express 0000:00:1c.1:pcie03: allocate port service
[    1.431473] pcieport-driver 0000:00:1c.2: setting latency timer to 64
[    1.431569] pcieport-driver 0000:00:1c.2: found MSI capability
[    1.431905] pci_express 0000:00:1c.2:pcie00: allocate port service
[    1.431935] pci_express 0000:00:1c.2:pcie02: allocate port service
[    1.431964] pci_express 0000:00:1c.2:pcie03: allocate port service
[    1.432157] pcieport-driver 0000:00:1c.4: setting latency timer to 64
[    1.432246] pcieport-driver 0000:00:1c.4: found MSI capability
[    1.432618] pci_express 0000:00:1c.4:pcie00: allocate port service
[    1.432653] pci_express 0000:00:1c.4:pcie02: allocate port service
[    1.432681] pci_express 0000:00:1c.4:pcie03: allocate port service
[    1.456777] hpet_resources: 0xfed00000 is busy
[    1.456838] Linux agpgart interface v0.103
[    1.457111] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
[    1.457874] serial 0000:00:03.3: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    1.458282] 0000:00:03.3: ttyS0 at I/O 0x8150 (irq = 17) is a 16550A
[    1.459807] brd: module loaded
[    1.460123] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[    1.460492] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    1.462770] i8042.c: Detected active multiplexing controller, rev 1.1.
[    1.463841] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.464109] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[    1.464374] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[    1.464643] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[    1.464909] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[    1.488578] mice: PS/2 mouse device common for all mice
[    1.488943] rtc_cmos 00:08: rtc core: registered rtc_cmos as rtc0
[    1.489255] rtc0: alarms up to one month, y3k, hpet irqs
[    1.489549] cpuidle: using governor ladder
[    1.489813] cpuidle: using governor menu
[    1.490358] TCP cubic registered
[    1.490763] registered taskstats version 1
[    1.491157]   Magic number: 0:498:45
[    1.491422] tty ttyee: hash matches
[    1.491782] rtc_cmos 00:08: setting system clock to 2008-11-17 21:00:42 UTC (1226955642)
[    1.492064] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.492330] EDD information not available.
[    1.492667] Freeing unused kernel memory: 536k freed
[    1.493111] Write protecting the kernel read-only data: 4348k
[    1.510477] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[    1.557910] fuse init (API version 7.9)
[    1.568036] ACPI: Transitioning device [FANG] to D3
[    1.568341] fan PNP0C0B:00: registered as cooling_device0
[    1.568611] ACPI: Fan [FANG] (off)
[    1.573667] ACPI: SSDT BFDC7C18, 0275 (r1  PmRef  Cpu0Ist     3000 INTL 20060912)
[    1.574928] ACPI: SSDT BFDC5618, 057B (r1  PmRef  Cpu0Cst     3001 INTL 20060912)
[    1.578123] Monitor-Mwait will be used to enter C-1 state
[    1.578125] Monitor-Mwait will be used to enter C-2 state
[    1.578361] ACPI: CPU0 (power states: C1[C1] C2[C2])
[    1.579412] processor ACPI0007:00: registered as cooling_device1
[    1.579680] ACPI: Processor [CPU0] (supports 8 throttling states)
[    1.580900] ACPI: SSDT BFDC6E18, 01D7 (r1  PmRef    ApIst     3000 INTL 20060912)
[    1.582116] ACPI: SSDT BFDC7F18, 008D (r1  PmRef    ApCst     3000 INTL 20060912)
[    1.584141] Marking TSC unstable due to TSC halts in idle
[    1.584571] ACPI: CPU1 (power states: C1[C1] C2[C2])
[    1.585638] processor ACPI0007:01: registered as cooling_device2
[    1.585912] ACPI: Processor [CPU1] (supports 8 throttling states)
[    1.590383] thermal LNXTHERM:01: registered as thermal_zone0
[    1.591152] ACPI: Thermal Zone [GFXZ] (30 C)
[    1.596907] thermal LNXTHERM:02: registered as thermal_zone1
[    1.597615] ACPI: Thermal Zone [DTSZ] (50 C)
[    2.000719] Clocksource tsc unstable (delta = -385192326 ns)
[    2.604252] ACPI Exception (evregion-0419): AE_TIME, Returned by Handler for [EmbeddedControl] [20080609]
[    2.605104] ACPI Error (psparse-0530): Method parse/execution failed [\_TZ_.GTTP] (Node ffff88013ba33620), AE_TIME
[    2.606178] ACPI Error (psparse-0530): Method parse/execution failed [\_TZ_.BATZ._TMP] (Node ffff88013ba338a0), AE_TIME
[    2.611319] thermal LNXTHERM:04: registered as thermal_zone2
[    2.613693] ACPI: Thermal Zone [CPUZ] (51 C)
[    2.617701] thermal LNXTHERM:05: registered as thermal_zone3
[    2.619911] ACPI: Thermal Zone [LOCZ] (42 C)
[    2.624075] thermal LNXTHERM:06: registered as thermal_zone4
[    2.626396] ACPI: Thermal Zone [CP2Z] (16 C)
[    2.833583] No dock devices found.
[    2.842133] SCSI subsystem initialized
[    2.851960] libata version 3.00 loaded.
[    2.854648] pata_acpi 0000:00:03.2: enabling device (0000 -> 0001)
[    2.854918] pata_acpi 0000:00:03.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    2.855220] pata_acpi 0000:00:03.2: setting latency timer to 64
[    2.855228] pata_acpi 0000:00:03.2: PCI INT C disabled
[    2.855526] pata_acpi 0000:00:1f.2: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[    2.855831] pata_acpi 0000:00:1f.2: setting latency timer to 64
[    2.855851] pata_acpi 0000:00:1f.2: PCI INT A disabled
[    2.856168] pata_acpi 0000:00:1f.5: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    2.856480] pata_acpi 0000:00:1f.5: setting latency timer to 64
[    2.856500] pata_acpi 0000:00:1f.5: PCI INT C disabled
[    2.884789] usbcore: registered new interface driver usbfs
[    2.885104] usbcore: registered new interface driver hub
[    2.885567] usbcore: registered new device driver usb
[    2.890406] e1000e: Intel(R) PRO/1000 Network Driver - 0.3.3.3-k6
[    2.890673] e1000e: Copyright (c) 1999-2008 Intel Corporation.
[    2.891013] e1000e 0000:00:19.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[    2.891299] e1000e 0000:00:19.0: setting latency timer to 64
[    2.894810] USB Universal Host Controller Interface driver v3.0
[    2.983143] 0000:00:19.0: eth0: (PCI Express:2.5GB/s:Width x1) 00:22:64:56:80:11
[    2.983454] 0000:00:19.0: eth0: Intel(R) PRO/1000 Network Connection
[    2.983777] 0000:00:19.0: eth0: MAC: 5, PHY: 8, PBA No: 1052ff-0ff
[    2.984648] uhci_hcd 0000:00:1a.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    2.984964] uhci_hcd 0000:00:1a.0: setting latency timer to 64
[    2.984973] uhci_hcd 0000:00:1a.0: UHCI Host Controller
[    2.985275] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 1
[    2.985631] uhci_hcd 0000:00:1a.0: irq 16, io base 0x000080a0
[    2.986035] usb usb1: configuration #1 chosen from 1 choice
[    2.986335] hub 1-0:1.0: USB hub found
[    2.986605] hub 1-0:1.0: 2 ports detected
[    3.192339] uhci_hcd 0000:00:1a.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    3.192701] uhci_hcd 0000:00:1a.1: setting latency timer to 64
[    3.192710] uhci_hcd 0000:00:1a.1: UHCI Host Controller
[    3.192948] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 2
[    3.193309] uhci_hcd 0000:00:1a.1: irq 17, io base 0x00008080
[    3.193660] usb usb2: configuration #1 chosen from 1 choice
[    3.193918] hub 2-0:1.0: USB hub found
[    3.194201] hub 2-0:1.0: 2 ports detected
[    3.304584] usb 1-1: new full speed USB device using uhci_hcd and address 2
[    3.400408] uhci_hcd 0000:00:1a.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    3.400660] uhci_hcd 0000:00:1a.2: setting latency timer to 64
[    3.400669] uhci_hcd 0000:00:1a.2: UHCI Host Controller
[    3.400922] uhci_hcd 0000:00:1a.2: new USB bus registered, assigned bus number 3
[    3.405171] uhci_hcd 0000:00:1a.2: irq 18, io base 0x00008060
[    3.405516] usb usb3: configuration #1 chosen from 1 choice
[    3.405758] hub 3-0:1.0: USB hub found
[    3.405979] hub 3-0:1.0: 2 ports detected
[    3.469121] usb 1-1: configuration #1 chosen from 1 choice
[    3.580090] usb 2-1: new full speed USB device using uhci_hcd and address 2
[    3.612328] ehci_hcd 0000:00:1a.7: PCI INT D -> GSI 19 (level, low) -> IRQ 19
[    3.612562] ehci_hcd 0000:00:1a.7: setting latency timer to 64
[    3.612565] ehci_hcd 0000:00:1a.7: EHCI Host Controller
[    3.612810] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 4
[    3.617013] ehci_hcd 0000:00:1a.7: debug port 1
[    3.617288] ehci_hcd 0000:00:1a.7: cache line size of 32 is not supported
[    3.617303] ehci_hcd 0000:00:1a.7: irq 19, io mem 0xdb326400
[    3.704095] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    3.704445] usb usb4: configuration #1 chosen from 1 choice
[    3.704687] hub 4-0:1.0: USB hub found
[    3.704919] hub 4-0:1.0: 6 ports detected
[    3.912520] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    3.912764] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    3.912772] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    3.913006] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 5
[    3.913332] uhci_hcd 0000:00:1d.0: irq 20, io base 0x00008040
[    3.913618] usb usb5: configuration #1 chosen from 1 choice
[    3.913888] hub 5-0:1.0: USB hub found
[    3.914114] hub 5-0:1.0: 2 ports detected
[    4.100098] usb 2-1: device not accepting address 2, error -71
[    4.120379] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 22 (level, low) -> IRQ 22
[    4.120565] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    4.120568] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    4.120809] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 6
[    4.121100] uhci_hcd 0000:00:1d.1: irq 22, io base 0x00008020
[    4.121434] usb usb6: configuration #1 chosen from 1 choice
[    4.121623] hub 6-0:1.0: USB hub found
[    4.121883] hub 6-0:1.0: 2 ports detected
[    4.156124] hub 2-0:1.0: unable to enumerate USB device on port 1
[    4.224431] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    4.224629] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    4.224631] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    4.224906] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 7
[    4.225185] uhci_hcd 0000:00:1d.2: irq 18, io base 0x00008000
[    4.225473] usb usb7: configuration #1 chosen from 1 choice
[    4.225668] hub 7-0:1.0: USB hub found
[    4.225911] hub 7-0:1.0: 2 ports detected
[    4.284155] usb 1-1: USB disconnect, address 2
[    4.328322] ehci_hcd 0000:00:1d.7: PCI INT D -> GSI 20 (level, low) -> IRQ 20
[    4.328503] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    4.328506] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    4.328717] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 8
[    4.332879] ehci_hcd 0000:00:1d.7: debug port 1
[    4.333108] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
[    4.333112] ehci_hcd 0000:00:1d.7: irq 20, io mem 0xdb326000
[    4.348109] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    4.348424] usb usb8: configuration #1 chosen from 1 choice
[    4.348634] hub 8-0:1.0: USB hub found
[    4.348900] hub 8-0:1.0: 6 ports detected
[    4.556356] ata_piix 0000:00:1f.2: version 2.12
[    4.556362] ata_piix 0000:00:1f.2: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[    4.556551] ata_piix 0000:00:1f.2: MAP [ P0 -- P1 -- ]
[    4.557874] ata_piix 0000:00:1f.2: setting latency timer to 64
[    4.557976] scsi0 : ata_piix
[    4.558365] scsi1 : ata_piix
[    4.559697] ata1: SATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0x8110 irq 14
[    4.559938] ata2: SATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0x8118 irq 15
[    4.752100] usb 4-5: new high speed USB device using ehci_hcd and address 4
[    4.931836] usb 4-5: configuration #1 chosen from 1 choice
[    5.036246] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    5.044400] ata1.00: ATA-8: FUJITSU MHZ2250BJ G2, 891A, max UDMA/100
[    5.044587] ata1.00: 488397168 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    5.060405] ata1.00: configured for UDMA/100
[    5.356120] usb 1-1: new full speed USB device using uhci_hcd and address 3
[    5.527700] usb 1-1: configuration #1 chosen from 1 choice
[    5.536700] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    5.560411] ata2.00: ATAPI: Optiarc DVD RW AD-7561S, AH03, max UDMA/100
[    5.592427] ata2.00: configured for UDMA/100
[    5.592735] scsi 0:0:0:0: Direct-Access     ATA      FUJITSU MHZ2250B 891A PQ: 0 ANSI: 5
[    5.594163] scsi 1:0:0:0: CD-ROM            Optiarc  DVD RW AD-7561S  AH03 PQ: 0 ANSI: 5
[    5.595877] ata_piix 0000:00:1f.5: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    5.596168] ata_piix 0000:00:1f.5: MAP [ P0 -- P1 -- ]
[    5.597607] ata_piix 0000:00:1f.5: setting latency timer to 64
[    5.597833] scsi2 : ata_piix
[    5.598194] scsi3 : ata_piix
[    5.598491] ata3: SATA max UDMA/133 cmd 0x8138 ctl 0x816c bmdma 0x80f0 irq 18
[    5.598670] ata4: SATA max UDMA/133 cmd 0x8130 ctl 0x8168 bmdma 0x80f8 irq 18
[    5.772165] usb 2-1: new full speed USB device using uhci_hcd and address 4
[    5.931141] ata3: SATA link down (SStatus 0 SControl 300)
[    5.950287] usb 2-1: configuration #1 chosen from 1 choice
[    6.192139] usb 5-1: new low speed USB device using uhci_hcd and address 2
[    6.263272] ata4: SATA link down (SStatus 0 SControl 310)
[    6.263784] ohci1394 0000:86:06.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    6.264029] ohci1394 0000:86:06.0: setting latency timer to 64
[    6.316762] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[16]  MMIO=[db001000-db0017ff]  Max Packet=[2048]  IR/IT contexts=[4/4]
[    6.327535] scsi 0:0:0:0: Attached scsi generic sg0 type 0
[    6.327968] scsi 1:0:0:0: Attached scsi generic sg1 type 5
[    6.339479] Driver 'sr' needs updating - please use bus_type methods
[    6.343193] Driver 'sd' needs updating - please use bus_type methods
[    6.343593] sd 0:0:0:0: [sda] 488397168 512-byte hardware sectors (250059 MB)
[    6.343838] sd 0:0:0:0: [sda] Write Protect is off
[    6.344198] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    6.344398] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    6.344820] sd 0:0:0:0: [sda] 488397168 512-byte hardware sectors (250059 MB)
[    6.345084] sd 0:0:0:0: [sda] Write Protect is off
[    6.345372] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    6.345571] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    6.345829]  sda:sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[    6.348645] Uniform CD-ROM driver Revision: 3.20
[    6.348945] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    6.378799] usb 5-1: configuration #1 chosen from 1 choice
[    6.390592] usbcore: registered new interface driver hiddev
[    6.406220]  sda1 sda2 <<6>input: Logitech USB RECEIVER as /devices/pci0000:00/0000:00:1d.0/usb5/5-1/5-1:1.0/input/input2
[    6.420816]  sda5 > sda3 sda4
[    6.428124] input,hidraw0: USB HID v1.11 Mouse [Logitech USB RECEIVER] on usb-0000:00:1d.0-1
[    6.429322] usbcore: registered new interface driver usbhid
[    6.429579] usbhid: v2.6:USB HID core driver
[    6.439444] sd 0:0:0:0: [sda] Attached SCSI disk
[    6.712301] PM: Starting manual resume from disk
[    6.712571] PM: Resume from partition 8:4
[    6.712572] PM: Checking hibernation image.
[    6.712798] PM: Resume from disk failed.
[    6.753157] kjournald starting.  Commit interval 5 seconds
[    6.753430] EXT3-fs: mounted filesystem with ordered data mode.
[    7.596168] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[5566778811223344]
[   12.206514] udevd version 124 started
[   12.598171] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   12.636492] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   12.659963] input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input3
[   12.692095] ACPI: Power Button (FF) [PWRF]
[   12.692587] input: Sleep Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input4
[   12.720054] ACPI: Sleep Button (CM) [SLPB]
[   12.720371] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input5
[   12.720856] ACPI: Lid Switch [LID]
[   12.721563] ACPI: AC Adapter [AC] (on-line)
[   12.959205] tpm_inf_pnp 00:04: Found GTPM with ID IFX0102
[   12.959521] tpm_inf_pnp 00:04: TPM found: config base 0xfe00, data base 0xfe80, chip version 0x000b, vendor id 0x15d1 (Infineon), product id 0x000b (SLB 9635 TT 1.2)
[   13.558679] nvidia: module license 'NVIDIA' taints kernel.
[   13.811081] ACPI Exception (evregion-0419): AE_TIME, Returned by Handler for [EmbeddedControl] [20080609]
[   13.811831] ACPI Error (psparse-0530): Method parse/execution failed [\_SB_.PCI0.LPCB.EC0_.BTIF] (Node ffff88013ba3cb20), AE_TIME
[   13.812856] ACPI Error (psparse-0530): Method parse/execution failed [\_SB_.BTIF] (Node ffff88013b0005a0), AE_TIME
[   13.813858] ACPI Error (psparse-0530): Method parse/execution failed [\_SB_.BAT0._BIF] (Node ffff88013b000680), AE_TIME
[   13.814862] ACPI Exception (battery-0330): AE_TIME, Evaluating _BIF [20080609]
[   13.815569] ACPI: Battery Slot [BAT0] (battery present)
[   13.816089] Bluetooth: Core ver 2.13
[   13.817681] ACPI: Battery Slot [BAT1] (battery absent)
[   13.818672] ACPI: WMI: Mapper loaded
[   13.818987] NET: Registered protocol family 31
[   13.819229] Bluetooth: HCI device and connection manager initialized
[   13.819476] Bluetooth: HCI socket layer initialized
[   13.829475] ricoh-mmc: Ricoh MMC Controller disabling driver
[   13.829745] ricoh-mmc: Copyright(c) Philip Langdale
[   13.872638] input: PC Speaker as /devices/platform/pcspkr/input/input6
[   13.885602] usbcore: registered new interface driver lmpcm_usb
[   13.885868] lmpcm_usb: v0.5.5:USB Logitech MediaPlay Cordless Mouse driver
[   13.933202] Bluetooth: Generic Bluetooth USB driver ver 0.3
[   13.940852] usbcore: registered new interface driver btusb
[   13.992545] sdhci: Secure Digital Host Controller Interface driver
[   13.992822] sdhci: Copyright(c) Pierre Ossman
[   14.035192] Linux video capture interface: v2.00
[   14.120152] uvcvideo: Found UVC 1.00 device CKA7216 (04f2:b053)
[   14.140193] input: CKA7216 as /devices/pci0000:00/0000:00:1a.7/usb4/4-5/4-5:1.0/input/input7
[   14.160215] usbcore: registered new interface driver uvcvideo
[   14.160480] USB Video Class driver (v0.1.0)
[   14.196486] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, 1.3.27ks
[   14.196791] iwlagn: Copyright(c) 2003-2008 Intel Corporation
[   14.317946] acpi device:04: registered as cooling_device3
[   14.568839] Synaptics Touchpad, model: 1, fw: 6.5, id: 0x1c0b1, caps: 0xa44791/0xb00000
[   14.569072] serio: Synaptics pass-through port at isa0060/serio4/input0
[   14.618899] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio4/input/input8
[   14.820062] ACPI Exception (evregion-0419): AE_TIME, Returned by Handler for [EmbeddedControl] [20080609]
[   14.820884] ACPI Error (psparse-0530): Method parse/execution failed [\_SB_.PCI0.LPCB.EC0_.SAST] (Node ffff88013ba3c820), AE_TIME
[   14.821847] ACPI Error (psparse-0530): Method parse/execution failed [\_SB_.PCI0.HDEF.APPR._ON_] (Node ffff88013ba3f8a0), AE_TIME
[   14.822796] ACPI: Transitioning device [HDEF] to D0
[   14.822988] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   14.823261] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   14.824159] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:02/device:03/input/input9
[   14.868187] ACPI: Video Device [DGFX] (multi-head: yes  rom: no  post: no)
[   14.925724] parport_pc 00:09: reported by Plug and Play ACPI
[   14.926012] parport0: PC-style at 0x378 (0x778), irq 5, using FIFO [PCSPP,TRISTATE,COMPAT,ECP]
[   15.272875] nvidia 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   15.273090] nvidia 0000:01:00.0: setting latency timer to 64
[   15.273231] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  180.06  Sat Nov  8 17:50:38 PST 2008
[   15.273429] iwlagn 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   15.273464] iwlagn 0000:03:00.0: setting latency timer to 64
[   15.273565] iwlagn: Detected Intel Wireless WiFi Link 5300AGN REV=0x24
[   15.308427] iwlagn: Tunable channels: 13 802.11bg, 24 802.11a channels
[   15.308755] ricoh-mmc: Ricoh MMC controller found at 0000:86:06.2 [1180:0843] (rev 14)
[   15.309007] ricoh-mmc: Controller is now disabled.
[   15.309296] sdhci-pci 0000:86:06.1: SDHCI controller found [1180:0822] (rev 25)
[   15.309610] sdhci-pci 0000:86:06.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[   15.312954] mmc0: SDHCI controller on PCI [0000:86:06.1] using PIO
[   15.313646] Yenta: CardBus bridge found at 0000:86:06.5 [103c:30ec]
[   15.316548] iwlagn 0000:03:00.0: PCI INT A disabled
[   15.317176] phy0: Selected rate control algorithm 'iwl-agn-rs'
[   15.440931] Yenta: ISA IRQ mask 0x0c98, PCI irq 17
[   15.441176] Socket status: 30000810
[   15.441407] Yenta: Raising subordinate bus# of parent bus (#86) from #87 to #8a
[   15.441688] pcmcia: parent PCI bridge I/O window: 0x2000 - 0x2fff
[   15.441914] pcmcia: parent PCI bridge Memory window: 0xdb000000 - 0xdb0fffff
[   15.442134] pcmcia: parent PCI bridge Memory window: 0xdc000000 - 0xdfffffff
[   15.535831] NET: Registered protocol family 10
[   15.536448] lo: Disabled Privacy Extensions
[   16.076086] pccard: PCMCIA card inserted into slot 0
[   16.076338] cs: memory probe 0xdb000000-0xdb0fffff: excluding 0xdb000000-0xdb00ffff
[   16.082579] cs: memory probe 0xdc000000-0xdfffffff: excluding 0xdc000000-0xdfffffff
[   16.083643] pcmcia: registering new device pcmcia0.0
[   16.193908] scsi4 : pata_pcmcia
[   16.194239] ata5: PATA max PIO0 cmd 0x2100 ctl 0x210e irq 17
[   17.168539] loop: module loaded
[   17.175712] lp0: using parport0 (interrupt-driven).
[   17.315123] Adding 1759108k swap on /dev/sda4.  Priority:-1 extents:1 across:1759108k
[   17.686679] EXT3 FS on sda3, internal journal
[   18.048237] type=1505 audit(1226952058.938:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=4657
[   18.140552] type=1505 audit(1226952059.030:3): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=4662
[   18.140715] type=1505 audit(1226952059.030:4): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=4662
[   18.252374] ip_tables: (C) 2000-2006 Netfilter Core Team
[   19.417903] input: PS/2 Generic Mouse as /devices/platform/i8042/serio4/serio5/input/input10
[   19.657311] warning: `avahi-daemon' uses 32-bit capabilities (legacy support in use)
[   19.791501] ppdev: user-space parallel port driver
[   21.560630] Bluetooth: L2CAP ver 2.11
[   21.560649] Bluetooth: L2CAP socket layer initialized
[   21.573318] Bluetooth: RFCOMM socket layer initialized
[   21.573353] Bluetooth: RFCOMM TTY layer initialized
[   21.573357] Bluetooth: RFCOMM ver 1.10
[   21.613224] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   21.613237] Bluetooth: BNEP filters: protocol multicast
[   21.686338] Bridge firewalling registered
[   21.688802] pan0: Dropping NETIF_F_UFO since no NETIF_F_HW_CSUM feature.
[   21.722409] Bluetooth: SCO (Voice Link) ver 0.6
[   21.722428] Bluetooth: SCO socket layer initialized
[   26.020958] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   26.023172] iwlagn 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   26.024026] iwlagn 0000:03:00.0: restoring config space at offset 0x1 (was 0x100002, writing 0x100006)
[   26.025691] firmware: requesting iwlwifi-5000-1.ucode
[   27.920782] 0000:00:19.0: eth0: Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[   27.920788] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[   30.100780] iwlagn: START_ALIVE timeout after 4000ms.
[   30.100854] iwlagn 0000:03:00.0: PCI INT A disabled
[   30.102612] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   30.117218] iwlagn 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   30.117333] iwlagn 0000:03:00.0: restoring config space at offset 0x1 (was 0x100002, writing 0x100006)
[   30.121875] iwlagn: Microcode SW error detected.  Restarting 0x2000000.
[   32.149148] Registered led device: iwl-phy0:radio
[   32.150541] Registered led device: iwl-phy0:assoc
[   32.153345] Registered led device: iwl-phy0:RX
[   32.153390] Registered led device: iwl-phy0:TX
[   32.175519] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   32.288632] NET: Registered protocol family 17
[   39.432487] ecryptfs_parse_options: eCryptfs: unrecognized option 'rw'
[   39.434057] ecryptfs_parse_options: eCryptfs: unrecognized option 'user=johan'
[   42.112190] eth0: no IPv6 routers present
[   61.729489] canberra-gtk-pl[6130]: segfault at 10094ac60 ip 00007f7d5c2b86ec sp 00000000415c8bd0 error 6 in libc-2.8.90.so[7f7d5c23c000+169000]
[   66.797142] CPU0 attaching NULL sched-domain.
[   66.797163] CPU1 attaching NULL sched-domain.
[   66.812876] CPU0 attaching sched-domain:
[   66.812890]  domain 0: span 0-1 level MC
[   66.812896]   groups: 0 1
[   66.812905]   domain 1: span 0-1 level NODE
[   66.812910]    groups: 0-1
[   66.812921] CPU1 attaching sched-domain:
[   66.812925]  domain 0: span 0-1 level MC
[   66.812929]   groups: 1 0
[   66.812936]   domain 1: span 0-1 level NODE
[   66.812941]    groups: 0-1
[  130.525252] ppdev0: registered pardevice
[  130.572605] ppdev0: unregistered pardevice
[  130.702253] ppdev0: registered pardevice
[  130.748863] ppdev0: unregistered pardevice
[  131.929585] type=1503 audit(1226952172.818:5): operation="inode_permission" requested_mask="r::" denied_mask="r::" fsuid=7 name="/proc/6346/net/" pid=6346 profile="/usr/sbin/cupsd"
[  132.968457] type=1503 audit(1226952173.858:6): operation="inode_permission" requested_mask="r::" denied_mask="r::" fsuid=7 name="/proc/6358/net/" pid=6358 profile="/usr/sbin/cupsd"
[  132.969180] type=1503 audit(1226952173.858:7): operation="socket_create" family="ax25" sock_type="dgram" protocol=0 pid=6358 profile="/usr/sbin/cupsd"
[  132.972246] type=1503 audit(1226952173.862:8): operation="socket_create" family="netrom" sock_type="seqpacket" protocol=0 pid=6358 profile="/usr/sbin/cupsd"
[  132.975424] type=1503 audit(1226952173.862:9): operation="socket_create" family="rose" sock_type="dgram" protocol=0 pid=6358 profile="/usr/sbin/cupsd"
[  132.978530] type=1503 audit(1226952173.866:10): operation="socket_create" family="ipx" sock_type="dgram" protocol=0 pid=6358 profile="/usr/sbin/cupsd"
[  132.981733] type=1503 audit(1226952173.870:11): operation="socket_create" family="appletalk" sock_type="dgram" protocol=0 pid=6358 profile="/usr/sbin/cupsd"
[  132.984966] type=1503 audit(1226952173.874:12): operation="socket_create" family="econet" sock_type="dgram" protocol=0 pid=6358 profile="/usr/sbin/cupsd"
[  132.988123] type=1503 audit(1226952173.878:13): operation="socket_create" family="ash" sock_type="dgram" protocol=0 pid=6358 profile="/usr/sbin/cupsd"
[  133.060482] ppdev0: registered pardevice
[  133.108329] ppdev0: unregistered pardevice
[  693.964088] CE: hpet increasing min_delta_ns to 15000 nsec

```

---

### Post by Joh_ on 2008-11-17
After waiting forever I actually got an error message. What exactly does it mean and how do I fix? :(

I took a picture of it, but it's barely readable so I'm re-typing it.
```

 * Loading hardware drivers...
[   11.861228] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   11.905969] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   80.972622] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6 frozen
[   80.972895] ata1.00: cmd 25/00:38:e8:07:12/00:00:17:00:00/e0 tag 0 dma 28672
in
[   80.972896]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeo
ut)
[   80.973404] ata1.00: status: { DRDY }
[   80.973636] ata1: hard resetting link

```

---

### Post by Steffen185 on 2008-11-21
You have to switch the BIOS option "Disable FAN always ON on AC Power", see here: [http://www.linlap.com/wiki/HP+EliteBook+8530W](http://www.linlap.com/wiki/HP+EliteBook+8530W)

---

