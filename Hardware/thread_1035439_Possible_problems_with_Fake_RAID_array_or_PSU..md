---
title: "Possible problems with Fake RAID array or PSU."
date: 2009-01-09
forum: Hardware
---

### Post by james.king@4act.com on 2009-01-09
I have a new custom built Quad Core with 4GB of RAM and 3 500MB Western Digital HD's in a fake RAID array and two external smaller usb HD's. NVidia video card with 512MB of NVRAM (I don't remember model number). 550Watt PSU (I don't remember manufacturer or model number) and a house with not so great electrical wiring (lights go dim for a second when certain large appliances turn on).

I have been having some trouble recently and I was hoping to get some ideas on how to troubleshoot whether it is an issue with power, hard drives going bad, or anything.

I run dmesg and see a lot of errors (I think. I am still a bit of a newb).

I installed an update that required a reboot this morning and grub continually failed with error 15 (I think...sorry) while trying to reboot.

I booted into my alternate install cd where it recognised my RAID array, but it would not let me select it as my root partition. It only gave me choices of sda1, sda2, sdd, sde, and sdf (I think sdf was my thumb drive). It did not even give me options for sdb and sdc (the other two drives in my RAID) which made me nervous that they might not be working. I tried to choose sda1 and sda2 a few times, but it threw errors that it could not mount those partitions.

Finally I gave up with that and rebooted going into bios to verify that my HD's were in fact registering in BIOS. I did not make any changes, but saved them anyway and this time when I booted off the CD I chose "boot off first hard disk" and it booted fine.

I immediately started backing up my family's important files and downloading an ubuntu desktop CD in case it happened again and I needed to get back into a Gnome Session (which I could never figure out on my own without google which I could not load without an X-Session). However, my wife's pictures were backing up at an incredibly slow rate of 800KB/s. AFterwards I began backing up my files which were copying at a great rate of 40MB/s however, about halfway through I started to hear clicking sounds coming from my box (not sure if it was the hard drive powering up and down or not). Then the copy failed and I had to start it over again. The second time it worked beautifully.


Now, I am posting here because I am not sure where to start debugging. 

1. PSU 
2. HD's (I have had fsck run a few times at boot in the past and not seen any errors).

here is the ouput from dmesg (it's so long) probably a lot of trouble going on.



[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.27-9-generic (buildd@yellow) (gcc version 4.3.2 (Ubuntu 4.3.2-1ubuntu11) ) #1 SMP Thu Nov 20 22:15:32 UTC 2008 (Ubuntu 2.6.27-9.19-generic)
[    0.000000] Command line: root=/dev/mapper/isw_cidhfbaebi_raidical1 ro quiet splash 
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   Centaur CentaurHauls
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 0000000000095c00 (usable)
[    0.000000]  BIOS-e820: 0000000000095c00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e4000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 00000000bff70000 (usable)
[    0.000000]  BIOS-e820: 00000000bff70000 - 00000000bff7e000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000bff7e000 - 00000000bffd0000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000bffd0000 - 00000000c0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fff00000 - 0000000100000000 (reserved)
[    0.000000]  BIOS-e820: 0000000100000000 - 0000000140000000 (usable)
[    0.000000] last_pfn = 0x140000 max_arch_pfn = 0x3ffffffff
[    0.000000] last_pfn = 0xbff70 max_arch_pfn = 0x3ffffffff
[    0.000000] init_memory_mapping
[    0.000000]  0000000000 - 00bfe00000 page 2M
[    0.000000]  00bfe00000 - 00bff70000 page 4k
[    0.000000] kernel direct mapping tables up to bff70000 @ 8000-d000
[    0.000000] last_map_addr: bff70000 end: bff70000
[    0.000000] init_memory_mapping
[    0.000000]  0100000000 - 0140000000 page 2M
[    0.000000] kernel direct mapping tables up to 140000000 @ b000-11000
[    0.000000] last_map_addr: 140000000 end: 140000000
[    0.000000] RAMDISK: 37784000 - 37fefe1d
[    0.000000] DMI present.
[    0.000000] ACPI: RSDP 000FB2C0, 0024 (r2 ACPIAM)
[    0.000000] ACPI: XSDT BFF70100, 005C (r1 A_M_I_ OEMXSDT   7000828 MSFT       97)
[    0.000000] ACPI: FACP BFF70290, 00F4 (r3 A_M_I_ OEMFACP   7000828 MSFT       97)
[    0.000000] ACPI: DSDT BFF70440, 907B (r1  A1013 A1013001        1 INTL 20051117)
[    0.000000] ACPI: FACS BFF7E000, 0040
[    0.000000] ACPI: APIC BFF70390, 006C (r1 A_M_I_ OEMAPIC   7000828 MSFT       97)
[    0.000000] ACPI: MCFG BFF70400, 003C (r1 A_M_I_ OEMMCFG   7000828 MSFT       97)
[    0.000000] ACPI: OEMB BFF7E040, 0081 (r1 A_M_I_ AMI_OEM   7000828 MSFT       97)
[    0.000000] ACPI: HPET BFF794C0, 0038 (r1 A_M_I_ OEMHPET   7000828 MSFT       97)
[    0.000000] ACPI: OSFR BFF79500, 00B0 (r1 A_M_I_ OEMOSFR   7000828 MSFT       97)
[    0.000000] ACPI: SSDT BFF7E9D0, 0A7C (r1 DpgPmm    CpuPm       12 INTL 20051117)
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at 0000000000000000-0000000140000000
[    0.000000] Bootmem setup node 0 0000000000000000-0000000140000000
[    0.000000]   NODE_DATA [0000000000001000 - 0000000000005fff]
[    0.000000]   bootmap [000000000000c000 -  0000000000033fff] pages 28
[    0.000000] (7 early reservations) ==> bootmem [0000000000 - 0140000000]
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000]   #1 [0000006000 - 0000008000]       TRAMPOLINE ==> [0000006000 - 0000008000]
[    0.000000]   #2 [0000200000 - 00008b8f9c]    TEXT DATA BSS ==> [0000200000 - 00008b8f9c]
[    0.000000]   #3 [0037784000 - 0037fefe1d]          RAMDISK ==> [0037784000 - 0037fefe1d]
[    0.000000]   #4 [0000095c00 - 0000100000]    BIOS reserved ==> [0000095c00 - 0000100000]
[    0.000000]   #5 [0000008000 - 000000b000]          PGTABLE ==> [0000008000 - 000000b000]
[    0.000000]   #6 [000000b000 - 000000c000]          PGTABLE ==> [000000b000 - 000000c000]
[    0.000000] found SMP MP-table at [ffff8800000ff780] 000ff780
[    0.000000]  [ffffe20000000000-ffffe20004ffffff] PMD -> [ffff880028200000-ffff88002c1fffff] on node 0
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000000 -> 0x00001000
[    0.000000]   DMA32    0x00001000 -> 0x00100000
[    0.000000]   Normal   0x00100000 -> 0x00140000
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[3] active PFN ranges
[    0.000000]     0: 0x00000000 -> 0x00000095
[    0.000000]     0: 0x00000100 -> 0x000bff70
[    0.000000]     0: 0x00100000 -> 0x00140000
[    0.000000] On node 0 totalpages: 1048325
[    0.000000]   DMA zone: 2090 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 765872 pages, LIFO batch:31
[    0.000000]   Normal zone: 258048 pages, LIFO batch:31
[    0.000000] ACPI: PM-Timer IO Port: 0x808
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x02] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x03] enabled)
[    0.000000] ACPI: IOAPIC (id[0x04] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 4, version 0, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Setting APIC routing to flat
[    0.000000] ACPI: HPET id: 0x8086a301 base: 0xfed00000
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] SMP: Allowing 4 CPUs, 0 hotplug CPUs
[    0.000000] PM: Registered nosave memory: 0000000000095000 - 0000000000096000
[    0.000000] PM: Registered nosave memory: 0000000000096000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e4000
[    0.000000] PM: Registered nosave memory: 00000000000e4000 - 0000000000100000
[    0.000000] PM: Registered nosave memory: 00000000bff70000 - 00000000bff7e000
[    0.000000] PM: Registered nosave memory: 00000000bff7e000 - 00000000bffd0000
[    0.000000] PM: Registered nosave memory: 00000000bffd0000 - 00000000c0000000
[    0.000000] PM: Registered nosave memory: 00000000c0000000 - 00000000fee00000
[    0.000000] PM: Registered nosave memory: 00000000fee00000 - 00000000fee01000
[    0.000000] PM: Registered nosave memory: 00000000fee01000 - 00000000fff00000
[    0.000000] PM: Registered nosave memory: 00000000fff00000 - 0000000100000000
[    0.000000] Allocating PCI resources starting at c4000000 (gap: c0000000:3ee00000)
[    0.000000] PERCPU: Allocating 64928 bytes of per cpu data
[    0.000000] NR_CPUS: 64, nr_cpu_ids: 4, nr_node_ids 1
[    0.000000] Built 1 zonelists in Node order, mobility grouping on.  Total pages: 1026010
[    0.000000] Policy zone: Normal
[    0.000000] Kernel command line: root=/dev/mapper/isw_cidhfbaebi_raidical1 ro quiet splash 
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 32768 bytes)
[    0.000000] Extended CMOS year: 2000
[    0.000000] TSC: PIT calibration confirmed by PMTIMER.
[    0.000000] TSC: using PMTIMER calibration value
[    0.000000] Detected 2830.489 MHz processor.
[    0.004000] Console: colour VGA+ 80x25
[    0.004000] console [tty0] enabled
[    0.004000] Checking aperture...
[    0.004000] No AGP bridge found
[    0.004000] Calgary: detecting Calgary via BIOS EBDA area
[    0.004000] Calgary: Unable to locate Rio Grande table in EBDA - bailing!
[    0.004000] PCI-DMA: Using software bounce buffering for IO (SWIOTLB)
[    0.004000] Placing software IO TLB between 0x20000000 - 0x24000000
[    0.004000] Memory: 4045792k/5242880k available (3112k kernel code, 147508k reserved, 1575k data, 536k init)
[    0.004000] CPA: page pool initialized 1 of 1 pages preallocated
[    0.004000] SLUB: Genslabs=13, HWalign=64, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
[    0.004000] hpet clockevent registered
[    0.004000] Calibrating delay loop (skipped), value calculated using timer frequency.. 5660.97 BogoMIPS (lpj=11321956)
[    0.004000] Security Framework initialized
[    0.004000] SELinux:  Disabled at boot.
[    0.004000] AppArmor: AppArmor initialized
[    0.004000] Dentry cache hash table entries: 524288 (order: 10, 4194304 bytes)
[    0.004000] Inode-cache hash table entries: 262144 (order: 9, 2097152 bytes)
[    0.004000] Mount-cache hash table entries: 256
[    0.004000] Initializing cgroup subsys ns
[    0.004000] Initializing cgroup subsys cpuacct
[    0.004000] Initializing cgroup subsys memory
[    0.004000] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.004000] CPU: L2 cache: 6144K
[    0.004000] CPU 0/0 -> Node 0
[    0.004000] CPU: Physical Processor ID: 0
[    0.004000] CPU: Processor Core ID: 0
[    0.004000] CPU0: Thermal monitoring enabled (TM2)
[    0.004000] using mwait in idle threads.
[    0.004012] ACPI: Core revision 20080609
[    0.007109] ACPI: Checking initramfs for custom DSDT
[    0.288391] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.330731] CPU0: Intel(R) Core(TM)2 Quad  CPU   Q9550  @ 2.83GHz stepping 07
[    0.330734] Using local APIC timer interrupts.
[    0.332021] APIC timer calibration result 6640152
[    0.332022] Detected 6.640 MHz APIC timer.
[    0.332115] Booting processor 1/1 ip 6000
[    0.004000] Initializing CPU#1
[    0.004000] Calibrating delay using timer specific routine.. 1806.13 BogoMIPS (lpj=3612273)
[    0.004000] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.004000] CPU: L2 cache: 6144K
[    0.004000] CPU 1/1 -> Node 0
[    0.004000] CPU: Physical Processor ID: 0
[    0.004000] CPU: Processor Core ID: 1
[    0.004000] CPU1: Thermal monitoring enabled (TM2)
[    0.444808] CPU1: Intel(R) Core(TM)2 Quad  CPU   Q9550  @ 2.83GHz stepping 07
[    0.444824] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
[    0.448126] Booting processor 2/2 ip 6000
[    0.004000] Initializing CPU#2
[    0.004000] Calibrating delay using timer specific routine.. 1806.15 BogoMIPS (lpj=3612309)
[    0.004000] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.004000] CPU: L2 cache: 6144K
[    0.004000] CPU 2/2 -> Node 0
[    0.004000] CPU: Physical Processor ID: 0
[    0.004000] CPU: Processor Core ID: 2
[    0.004000] CPU2: Thermal monitoring enabled (TM2)
[    0.560808] CPU2: Intel(R) Core(TM)2 Quad  CPU   Q9550  @ 2.83GHz stepping 07
[    0.560824] checking TSC synchronization [CPU#0 -> CPU#2]: passed.
[    0.564105] Booting processor 3/3 ip 6000
[    0.004000] Initializing CPU#3
[    0.004000] Calibrating delay using timer specific routine.. 1806.15 BogoMIPS (lpj=3612306)
[    0.004000] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.004000] CPU: L2 cache: 6144K
[    0.004000] CPU 3/3 -> Node 0
[    0.004000] CPU: Physical Processor ID: 0
[    0.004000] CPU: Processor Core ID: 3
[    0.004000] CPU3: Thermal monitoring enabled (TM2)
[    0.676879] CPU3: Intel(R) Core(TM)2 Quad  CPU   Q9550  @ 2.83GHz stepping 07
[    0.676894] checking TSC synchronization [CPU#0 -> CPU#3]: passed.
[    0.680046] Brought up 4 CPUs
[    0.680049] Total of 4 processors activated (11079.42 BogoMIPS).
[    0.680095] CPU0 attaching sched-domain:
[    0.680096]  domain 0: span 0-1 level MC
[    0.680098]   groups: 0 1
[    0.680101]   domain 1: span 0-3 level CPU
[    0.680102]    groups: 0-1 2-3
[    0.680104]    domain 2: span 0-3 level NODE
[    0.680105]     groups: 0-3
[    0.680108] CPU1 attaching sched-domain:
[    0.680109]  domain 0: span 0-1 level MC
[    0.680110]   groups: 1 0
[    0.680112]   domain 1: span 0-3 level CPU
[    0.680114]    groups: 0-1 2-3
[    0.680116]    domain 2: span 0-3 level NODE
[    0.680117]     groups: 0-3
[    0.680119] CPU2 attaching sched-domain:
[    0.680120]  domain 0: span 2-3 level MC
[    0.680121]   groups: 2 3
[    0.680123]   domain 1: span 0-3 level CPU
[    0.680124]    groups: 2-3 0-1
[    0.680126]    domain 2: span 0-3 level NODE
[    0.680127]     groups: 0-3
[    0.680130] CPU3 attaching sched-domain:
[    0.680131]  domain 0: span 2-3 level MC
[    0.680132]   groups: 3 2
[    0.680134]   domain 1: span 0-3 level CPU
[    0.680135]    groups: 2-3 0-1
[    0.680137]    domain 2: span 0-3 level NODE
[    0.680138]     groups: 0-3
[    0.680251] net_namespace: 1552 bytes
[    0.680251] Booting paravirtualized kernel on bare hardware
[    0.680251] Time: 18:34:33  Date: 01/09/09
[    0.680251] NET: Registered protocol family 16
[    0.684067] ACPI: bus type pci registered
[    0.684076] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 255
[    0.684076] PCI: Not using MMCONFIG.
[    0.684076] PCI: Using configuration type 1 for base access
[    0.692421] ACPI: EC: Look up EC in DSDT
[    0.732649] ACPI: Interpreter enabled
[    0.732650] ACPI: (supports S0 S1 S3 S4 S5)
[    0.732662] ACPI: Using IOAPIC for interrupt routing
[    0.732713] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 255
[    0.740787] PCI: MCFG area at e0000000 reserved in ACPI motherboard resources
[    0.760334] PCI: Using MMCONFIG at e0000000 - efffffff
[    0.788157] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.788157] pci 0000:00:01.0: PME# supported from D0 D3hot D3cold
[    0.788157] pci 0000:00:01.0: PME# disabled
[    0.788157] PCI: 0000:00:1a.0 reg 20 io port: [b800, b81f]
[    0.788187] PCI: 0000:00:1a.1 reg 20 io port: [b880, b89f]
[    0.788234] PCI: 0000:00:1a.2 reg 20 io port: [bc00, bc1f]
[    0.788286] PCI: 0000:00:1a.7 reg 10 32bit mmio: [f9fffc00, f9ffffff]
[    0.788323] pci 0000:00:1a.7: PME# supported from D0 D3hot D3cold
[    0.788327] pci 0000:00:1a.7: PME# disabled
[    0.788350] PCI: 0000:00:1b.0 reg 10 64bit mmio: [f9ff8000, f9ffbfff]
[    0.788377] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    0.788380] pci 0000:00:1b.0: PME# disabled
[    0.788414] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.788417] pci 0000:00:1c.0: PME# disabled
[    0.792050] pci 0000:00:1c.4: PME# supported from D0 D3hot D3cold
[    0.792053] pci 0000:00:1c.4: PME# disabled
[    0.792087] pci 0000:00:1c.5: PME# supported from D0 D3hot D3cold
[    0.792090] pci 0000:00:1c.5: PME# disabled
[    0.792124] PCI: 0000:00:1d.0 reg 20 io port: [b080, b09f]
[    0.792171] PCI: 0000:00:1d.1 reg 20 io port: [b400, b41f]
[    0.792218] PCI: 0000:00:1d.2 reg 20 io port: [b480, b49f]
[    0.792269] PCI: 0000:00:1d.7 reg 10 32bit mmio: [f9fff800, f9fffbff]
[    0.792306] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
[    0.792309] pci 0000:00:1d.7: PME# disabled
[    0.792427] PCI: 0000:00:1f.2 reg 10 io port: [ac00, ac07]
[    0.792431] PCI: 0000:00:1f.2 reg 14 io port: [a880, a883]
[    0.792435] PCI: 0000:00:1f.2 reg 18 io port: [a800, a807]
[    0.792439] PCI: 0000:00:1f.2 reg 1c io port: [a480, a483]
[    0.792443] PCI: 0000:00:1f.2 reg 20 io port: [a400, a41f]
[    0.792452] PCI: 0000:00:1f.2 reg 24 32bit mmio: [f9ffe800, f9ffefff]
[    0.792474] pci 0000:00:1f.2: PME# supported from D3hot
[    0.792476] pci 0000:00:1f.2: PME# disabled
[    0.792490] PCI: 0000:00:1f.3 reg 10 64bit mmio: [f9fff400, f9fff4ff]
[    0.792500] PCI: 0000:00:1f.3 reg 20 io port: [400, 41f]
[    0.792545] PCI: 0000:01:00.0 reg 10 32bit mmio: [fd000000, fdffffff]
[    0.792549] PCI: 0000:01:00.0 reg 14 32bit mmio: [c0000000, dfffffff]
[    0.792558] PCI: 0000:01:00.0 reg 1c 64bit mmio: [fa000000, fbffffff]
[    0.792562] PCI: 0000:01:00.0 reg 24 io port: [cc00, cc7f]
[    0.792566] PCI: 0000:01:00.0 reg 30 32bit mmio: [fe8e0000, fe8fffff]
[    0.792600] PCI: bridge 0000:00:01.0 io port: [c000, cfff]
[    0.792601] PCI: bridge 0000:00:01.0 32bit mmio: [fa000000, fe8fffff]
[    0.792604] PCI: bridge 0000:00:01.0 64bit mmio pref: [c0000000, dfffffff]
[    0.792638] PCI: bridge 0000:00:1c.0 64bit mmio pref: [f8f00000, f8ffffff]
[    0.792675] PCI: 0000:03:00.0 reg 10 io port: [ec00, ec07]
[    0.792681] PCI: 0000:03:00.0 reg 14 io port: [e880, e883]
[    0.792687] PCI: 0000:03:00.0 reg 18 io port: [e800, e807]
[    0.792693] PCI: 0000:03:00.0 reg 1c io port: [e480, e483]
[    0.792700] PCI: 0000:03:00.0 reg 20 io port: [e400, e40f]
[    0.792706] PCI: 0000:03:00.0 reg 24 32bit mmio: [feaffc00, feaffdff]
[    0.792732] pci 0000:03:00.0: supports D1
[    0.792733] pci 0000:03:00.0: PME# supported from D0 D1 D3hot
[    0.792736] pci 0000:03:00.0: PME# disabled
[    0.792761] PCI: bridge 0000:00:1c.4 io port: [e000, efff]
[    0.792763] PCI: bridge 0000:00:1c.4 32bit mmio: [fea00000, feafffff]
[    0.792810] PCI: 0000:02:00.0 reg 10 64bit mmio: [fe9c0000, fe9fffff]
[    0.792817] PCI: 0000:02:00.0 reg 18 io port: [dc00, dc7f]
[    0.792858] pci 0000:02:00.0: PME# supported from D3hot D3cold
[    0.792862] pci 0000:02:00.0: PME# disabled
[    0.792886] PCI: bridge 0000:00:1c.5 io port: [d000, dfff]
[    0.792889] PCI: bridge 0000:00:1c.5 32bit mmio: [fe900000, fe9fffff]
[    0.792919] PCI: 0000:05:00.0 reg 10 32bit mmio: [febf0000, febfffff]
[    0.792986] pci 0000:00:1e.0: transparent bridge
[    0.792990] PCI: bridge 0000:00:1e.0 32bit mmio: [feb00000, febfffff]
[    0.793012] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.793219] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P2._PRT]
[    0.796042] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P1._PRT]
[    0.796185] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P8._PRT]
[    0.796276] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P9._PRT]
[    0.796380] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P4._PRT]
[    0.852135] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 *10 11 12 14 15)
[    0.852252] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 10 *11 12 14 15)
[    0.852369] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 *5 6 7 10 11 12 14 15)
[    0.852485] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 *4 5 6 7 10 11 12 14 15)
[    0.852601] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[    0.852718] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 10 11 12 14 *15)
[    0.856065] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 10 11 12 *14 15)
[    0.856181] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 *7 10 11 12 14 15)
[    0.856239] ACPI Warning (tbutils-0217): Incorrect checksum in table [OEMB] - 19, should be 18 [20080609]
[    0.856239] Linux Plug and Play Support v0.97 (c) Adam Belay
[    0.856239] pnp: PnP ACPI init
[    0.856239] ACPI: bus type pnp registered
[    0.868279] pnp: PnP ACPI: found 17 devices
[    0.868281] ACPI: ACPI bus type pnp unregistered
[    0.868298] PCI: Using ACPI for IRQ routing
[    0.884039] NET: Registered protocol family 8
[    0.884041] NET: Registered protocol family 20
[    0.884056] NetLabel: Initializing
[    0.884056] NetLabel:  domain hash size = 128
[    0.884056] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.884056] NetLabel:  unlabeled traffic allowed by default
[    0.884066] PCI-GART: No AMD northbridge found.
[    0.884071] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0
[    0.884075] hpet0: 4 64-bit timers, 14318180 Hz
[    0.888036] Switched to high resolution mode on CPU 0
[    0.888428] Switched to high resolution mode on CPU 1
[    0.888465] Switched to high resolution mode on CPU 2
[    0.888531] Switched to high resolution mode on CPU 3
[    0.889594] tracer: 1286 pages allocated for 65536 entries of 80 bytes
[    0.889595]    actual entries 65586
[    0.889650] AppArmor: AppArmor Filesystem Enabled
[    0.889664] ACPI: RTC can wake from S4
[    0.908016] system 00:01: iomem range 0xfed14000-0xfed19fff has been reserved
[    0.908023] system 00:06: ioport range 0x290-0x29f has been reserved
[    0.908029] system 00:07: ioport range 0x4d0-0x4d1 has been reserved
[    0.908031] system 00:07: ioport range 0x800-0x87f has been reserved
[    0.908033] system 00:07: ioport range 0x500-0x57f has been reserved
[    0.908035] system 00:07: iomem range 0xfed08000-0xfed08fff has been reserved
[    0.908038] system 00:07: iomem range 0xfed1c000-0xfed1ffff has been reserved
[    0.908040] system 00:07: iomem range 0xfed20000-0xfed3ffff has been reserved
[    0.908042] system 00:07: iomem range 0xfed50000-0xfed8ffff has been reserved
[    0.908053] system 00:0a: iomem range 0xffc00000-0xffefffff has been reserved
[    0.908056] system 00:0b: iomem range 0xfec00000-0xfec00fff has been reserved
[    0.908058] system 00:0b: iomem range 0xfee00000-0xfee00fff could not be reserved
[    0.908063] system 00:0f: iomem range 0xe0000000-0xefffffff has been reserved
[    0.908066] system 00:10: iomem range 0x0-0x9ffff could not be reserved
[    0.908068] system 00:10: iomem range 0xc0000-0xcffff has been reserved
[    0.908070] system 00:10: iomem range 0xe0000-0xfffff could not be reserved
[    0.908071] system 00:10: iomem range 0x100000-0xbfffffff could not be reserved
[    0.913549] pci 0000:00:01.0: PCI bridge, secondary bus 0000:01
[    0.913551] pci 0000:00:01.0:   IO window: 0xc000-0xcfff
[    0.913554] pci 0000:00:01.0:   MEM window: 0xfa000000-0xfe8fffff
[    0.913556] pci 0000:00:01.0:   PREFETCH window: 0x000000c0000000-0x000000dfffffff
[    0.913559] pci 0000:00:1c.0: PCI bridge, secondary bus 0000:04
[    0.913560] pci 0000:00:1c.0:   IO window: disabled
[    0.913563] pci 0000:00:1c.0:   MEM window: disabled
[    0.913566] pci 0000:00:1c.0:   PREFETCH window: 0x000000f8f00000-0x000000f8ffffff
[    0.913570] pci 0000:00:1c.4: PCI bridge, secondary bus 0000:03
[    0.913572] pci 0000:00:1c.4:   IO window: 0xe000-0xefff
[    0.913575] pci 0000:00:1c.4:   MEM window: 0xfea00000-0xfeafffff
[    0.913578] pci 0000:00:1c.4:   PREFETCH window: disabled
[    0.913582] pci 0000:00:1c.5: PCI bridge, secondary bus 0000:02
[    0.913584] pci 0000:00:1c.5:   IO window: 0xd000-0xdfff
[    0.913587] pci 0000:00:1c.5:   MEM window: 0xfe900000-0xfe9fffff
[    0.913590] pci 0000:00:1c.5:   PREFETCH window: disabled
[    0.913594] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:05
[    0.913595] pci 0000:00:1e.0:   IO window: disabled
[    0.913598] pci 0000:00:1e.0:   MEM window: 0xfeb00000-0xfebfffff
[    0.913601] pci 0000:00:1e.0:   PREFETCH window: disabled
[    0.913610] pci 0000:00:01.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.913612] pci 0000:00:01.0: setting latency timer to 64
[    0.913618] pci 0000:00:1c.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    0.913620] pci 0000:00:1c.0: setting latency timer to 64
[    0.913625] pci 0000:00:1c.4: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    0.913628] pci 0000:00:1c.4: setting latency timer to 64
[    0.913632] pci 0000:00:1c.5: PCI INT B -> GSI 16 (level, low) -> IRQ 16
[    0.913635] pci 0000:00:1c.5: setting latency timer to 64
[    0.913640] pci 0000:00:1e.0: setting latency timer to 64
[    0.913642] bus: 00 index 0 io port: [0, ffff]
[    0.913643] bus: 00 index 1 mmio: [0, ffffffffffffffff]
[    0.913645] bus: 01 index 0 io port: [c000, cfff]
[    0.913646] bus: 01 index 1 mmio: [fa000000, fe8fffff]
[    0.913647] bus: 01 index 2 mmio: [c0000000, dfffffff]
[    0.913648] bus: 01 index 3 mmio: [0, 0]
[    0.913649] bus: 04 index 0 mmio: [0, 0]
[    0.913650] bus: 04 index 1 mmio: [0, 0]
[    0.913651] bus: 04 index 2 mmio: [f8f00000, f8ffffff]
[    0.913652] bus: 04 index 3 mmio: [0, 0]
[    0.913653] bus: 03 index 0 io port: [e000, efff]
[    0.913654] bus: 03 index 1 mmio: [fea00000, feafffff]
[    0.913655] bus: 03 index 2 mmio: [0, 0]
[    0.913656] bus: 03 index 3 mmio: [0, 0]
[    0.913657] bus: 02 index 0 io port: [d000, dfff]
[    0.913659] bus: 02 index 1 mmio: [fe900000, fe9fffff]
[    0.913660] bus: 02 index 2 mmio: [0, 0]
[    0.913661] bus: 02 index 3 mmio: [0, 0]
[    0.913662] bus: 05 index 0 mmio: [0, 0]
[    0.913663] bus: 05 index 1 mmio: [feb00000, febfffff]
[    0.913664] bus: 05 index 2 mmio: [0, 0]
[    0.913665] bus: 05 index 3 io port: [0, ffff]
[    0.913666] bus: 05 index 4 mmio: [0, ffffffffffffffff]
[    0.913672] NET: Registered protocol family 2
[    0.952129] IP route cache hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.953014] TCP established hash table entries: 524288 (order: 11, 8388608 bytes)
[    0.955503] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    0.955910] TCP: Hash tables configured (established 524288 bind 65536)
[    0.955912] TCP reno registered
[    0.964115] NET: Registered protocol family 1
[    0.964213] checking if image is initramfs... it is
[    1.525215] Freeing initrd memory: 8623k freed
[    1.529274] audit: initializing netlink socket (disabled)
[    1.529295] type=2000 audit(1231526073.528:1): initialized
[    1.533780] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    1.536839] VFS: Disk quotas dquot_6.5.1
[    1.536893] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    1.536957] msgmni has been set to 7918
[    1.537034] io scheduler noop registered
[    1.537035] io scheduler anticipatory registered
[    1.537037] io scheduler deadline registered
[    1.537120] io scheduler cfq registered (default)
[    1.537240] pci 0000:01:00.0: Boot video device
[    1.537321] pcieport-driver 0000:00:01.0: setting latency timer to 64
[    1.537342] pcieport-driver 0000:00:01.0: found MSI capability
[    1.537360] pci_express 0000:00:01.0:pcie00: allocate port service
[    1.537388] pci_express 0000:00:01.0:pcie03: allocate port service
[    1.537442] pcieport-driver 0000:00:1c.0: setting latency timer to 64
[    1.537466] pcieport-driver 0000:00:1c.0: found MSI capability
[    1.537492] pci_express 0000:00:1c.0:pcie00: allocate port service
[    1.537524] pci_express 0000:00:1c.0:pcie02: allocate port service
[    1.537553] pci_express 0000:00:1c.0:pcie03: allocate port service
[    1.537613] pcieport-driver 0000:00:1c.4: setting latency timer to 64
[    1.537637] pcieport-driver 0000:00:1c.4: found MSI capability
[    1.537661] pci_express 0000:00:1c.4:pcie00: allocate port service
[    1.537686] pci_express 0000:00:1c.4:pcie02: allocate port service
[    1.537711] pci_express 0000:00:1c.4:pcie03: allocate port service
[    1.537771] pcieport-driver 0000:00:1c.5: setting latency timer to 64
[    1.537805] pcieport-driver 0000:00:1c.5: found MSI capability
[    1.537829] pci_express 0000:00:1c.5:pcie00: allocate port service
[    1.537855] pci_express 0000:00:1c.5:pcie02: allocate port service
[    1.537879] pci_express 0000:00:1c.5:pcie03: allocate port service
[    1.566475] hpet_resources: 0xfed00000 is busy
[    1.566568] Linux agpgart interface v0.103
[    1.566576] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
[    1.566814] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[    1.567397] 00:0e: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[    1.569591] brd: module loaded
[    1.569636] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[    1.569715] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f03:PS2M] at 0x60,0x64 irq 1,12
[    1.571707] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.571711] serio: i8042 AUX port at 0x60,0x64 irq 12
[    1.593640] mice: PS/2 mouse device common for all mice
[    1.593785] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0
[    1.593810] rtc0: alarms up to one month, y3k, hpet irqs
[    1.593866] cpuidle: using governor ladder
[    1.593867] cpuidle: using governor menu
[    1.594115] TCP cubic registered
[    1.594331] registered taskstats version 1
[    1.594417]   Magic number: 9:582:594
[    1.594487] rtc_cmos 00:03: setting system clock to 2009-01-09 18:34:34 UTC (1231526074)
[    1.594494] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.594495] EDD information not available.
[    1.594522] Freeing unused kernel memory: 536k freed
[    1.594643] Write protecting the kernel read-only data: 4348k
[    1.620741] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[    1.688976] device-mapper: uevent: version 1.0.3
[    1.689093] device-mapper: ioctl: 4.14.0-ioctl (2008-04-23) initialised: [email]dm-devel@redhat.com[/email]
[    1.698224] device-mapper: dm-raid45: initialized v0.2427
[    1.703192] fuse init (API version 7.9)
[    1.716017] ACPI: SSDT BFF7E0D0, 0235 (r1 DpgPmm  P001Ist       11 INTL 20051117)
[    1.716509] processor ACPI0007:00: registered as cooling_device0
[    1.716834] ACPI: SSDT BFF7E310, 0235 (r1 DpgPmm  P002Ist       12 INTL 20051117)
[    1.717318] processor ACPI0007:01: registered as cooling_device1
[    1.717646] ACPI: SSDT BFF7E550, 0235 (r1 DpgPmm  P003Ist       12 INTL 20051117)
[    1.718122] processor ACPI0007:02: registered as cooling_device2
[    1.718454] ACPI: SSDT BFF7E790, 0235 (r1 DpgPmm  P004Ist       12 INTL 20051117)
[    1.718929] processor ACPI0007:03: registered as cooling_device3
[    1.823512] usbcore: registered new interface driver usbfs
[    1.823528] usbcore: registered new interface driver hub
[    1.823666] usbcore: registered new device driver usb
[    1.825710] USB Universal Host Controller Interface driver v3.0
[    1.825748] uhci_hcd 0000:00:1a.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.825757] uhci_hcd 0000:00:1a.0: setting latency timer to 64
[    1.825760] uhci_hcd 0000:00:1a.0: UHCI Host Controller
[    1.825788] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 1
[    1.825821] uhci_hcd 0000:00:1a.0: irq 16, io base 0x0000b800
[    1.825926] usb usb1: configuration #1 chosen from 1 choice
[    1.825942] hub 1-0:1.0: USB hub found
[    1.825947] hub 1-0:1.0: 2 ports detected
[    1.864706] No dock devices found.
[    1.874437] SCSI subsystem initialized
[    1.883727] libata version 3.00 loaded.
[    1.929724] uhci_hcd 0000:00:1a.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[    1.929733] uhci_hcd 0000:00:1a.1: setting latency timer to 64
[    1.929736] uhci_hcd 0000:00:1a.1: UHCI Host Controller
[    1.929753] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 2
[    1.929785] uhci_hcd 0000:00:1a.1: irq 21, io base 0x0000b880
[    1.929849] usb usb2: configuration #1 chosen from 1 choice
[    1.929868] hub 2-0:1.0: USB hub found
[    1.929874] hub 2-0:1.0: 2 ports detected
[    2.033726] uhci_hcd 0000:00:1a.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    2.033735] uhci_hcd 0000:00:1a.2: setting latency timer to 64
[    2.033738] uhci_hcd 0000:00:1a.2: UHCI Host Controller
[    2.033760] uhci_hcd 0000:00:1a.2: new USB bus registered, assigned bus number 3
[    2.033792] uhci_hcd 0000:00:1a.2: irq 18, io base 0x0000bc00
[    2.033860] usb usb3: configuration #1 chosen from 1 choice
[    2.033879] hub 3-0:1.0: USB hub found
[    2.033884] hub 3-0:1.0: 2 ports detected
[    2.137779] ehci_hcd 0000:00:1a.7: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    2.137793] ehci_hcd 0000:00:1a.7: setting latency timer to 64
[    2.137796] ehci_hcd 0000:00:1a.7: EHCI Host Controller
[    2.137814] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 4
[    2.141732] ehci_hcd 0000:00:1a.7: debug port 1
[    2.141737] ehci_hcd 0000:00:1a.7: cache line size of 32 is not supported
[    2.141742] ehci_hcd 0000:00:1a.7: irq 18, io mem 0xf9fffc00
[    2.157508] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    2.157557] usb usb4: configuration #1 chosen from 1 choice
[    2.157574] hub 4-0:1.0: USB hub found
[    2.157579] hub 4-0:1.0: 6 ports detected
[    2.260254] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    2.260259] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    2.260261] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    2.260276] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 5
[    2.260298] uhci_hcd 0000:00:1d.0: irq 23, io base 0x0000b080
[    2.260361] usb usb5: configuration #1 chosen from 1 choice
[    2.260377] hub 5-0:1.0: USB hub found
[    2.260381] hub 5-0:1.0: 2 ports detected
[    2.468744] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    2.468748] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    2.468751] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    2.468769] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 6
[    2.468789] uhci_hcd 0000:00:1d.1: irq 19, io base 0x0000b400
[    2.468852] usb usb6: configuration #1 chosen from 1 choice
[    2.468870] hub 6-0:1.0: USB hub found
[    2.468874] hub 6-0:1.0: 2 ports detected
[    2.580010] usb 5-2: new full speed USB device using uhci_hcd and address 2
[    2.640025] hub 5-0:1.0: unable to enumerate USB device on port 2
[    2.678302] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    2.678306] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    2.678309] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    2.678326] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 7
[    2.678341] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000b480
[    2.678396] usb usb7: configuration #1 chosen from 1 choice
[    2.678412] hub 7-0:1.0: USB hub found
[    2.678416] hub 7-0:1.0: 2 ports detected
[    2.824024] hub 5-0:1.0: unable to enumerate USB device on port 2
[    2.885619] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    2.885625] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    2.885627] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    2.885644] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 8
[    2.889540] ehci_hcd 0000:00:1d.7: debug port 1
[    2.889544] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
[    2.889548] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xf9fff800
[    2.936011] usb 6-2: new full speed USB device using uhci_hcd and address 2
[    2.948010] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    2.948074] usb usb8: configuration #1 chosen from 1 choice
[    2.948097] hub 8-0:1.0: USB hub found
[    2.948105] hub 8-0:1.0: 6 ports detected
[    3.004032] hub 6-0:1.0: unable to enumerate USB device on port 2
[    3.157793] ahci 0000:00:1f.2: version 3.0
[    3.157801] ahci 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    3.157874] ahci 0000:00:1f.2: AHCI 0001.0200 32 slots 6 ports 3 Gbps 0x3f impl RAID mode
[    3.157877] ahci 0000:00:1f.2: flags: 64bit ncq sntf stag pm led clo pmp pio slum part ems 
[    3.157880] ahci 0000:00:1f.2: setting latency timer to 64
[    3.158141] scsi0 : ahci
[    3.158241] scsi1 : ahci
[    3.158306] scsi2 : ahci
[    3.158374] scsi3 : ahci
[    3.158437] scsi4 : ahci
[    3.158509] scsi5 : ahci
[    3.158599] ata1: SATA max UDMA/133 abar m2048@0xf9ffe800 port 0xf9ffe900 irq 2299
[    3.158601] ata2: SATA max UDMA/133 abar m2048@0xf9ffe800 port 0xf9ffe980 irq 2299
[    3.158603] ata3: SATA max UDMA/133 abar m2048@0xf9ffe800 port 0xf9ffea00 irq 2299
[    3.158605] ata4: SATA max UDMA/133 abar m2048@0xf9ffe800 port 0xf9ffea80 irq 2299
[    3.158607] ata5: SATA max UDMA/133 abar m2048@0xf9ffe800 port 0xf9ffeb00 irq 2299
[    3.158609] ata6: SATA max UDMA/133 abar m2048@0xf9ffe800 port 0xf9ffeb80 irq 2299
[    3.376516] usb 8-2: new high speed USB device using ehci_hcd and address 2
[    3.637093] usb 8-2: configuration #1 chosen from 1 choice
[    3.645791] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    3.652112] ata1.00: ATA-7: SAMSUNG HD502IJ, 1AA01112, max UDMA7
[    3.652115] ata1.00: 976773168 sectors, multi 0: LBA48 NCQ (depth 31/32)
[    3.658481] ata1.00: configured for UDMA/133
[    3.860011] usb 8-5: new high speed USB device using ehci_hcd and address 4
[    3.993082] usb 8-5: configuration #1 chosen from 1 choice
[    3.993276] hub 8-5:1.0: USB hub found
[    3.993362] hub 8-5:1.0: 7 ports detected
[    4.160015] ata2: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    4.166318] ata2.00: ATA-7: SAMSUNG HD502IJ, 1AA01112, max UDMA7
[    4.166321] ata2.00: 976773168 sectors, multi 0: LBA48 NCQ (depth 31/32)
[    4.172701] ata2.00: configured for UDMA/133
[    4.280033] hub 6-0:1.0: unable to enumerate USB device on port 2
[    4.552024] hub 6-0:1.0: unable to enumerate USB device on port 2
[    4.672013] ata3: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    4.678320] ata3.00: ATA-7: SAMSUNG HD502IJ, 1AA01112, max UDMA7
[    4.678322] ata3.00: 976773168 sectors, multi 0: LBA48 NCQ (depth 31/32)
[    4.684686] ata3.00: configured for UDMA/133
[    4.800026] hub 6-0:1.0: unable to enumerate USB device on port 2
[    5.020013] ata4: SATA link down (SStatus 0 SControl 300)
[    5.104009] usb 6-2: new full speed USB device using uhci_hcd and address 6
[    5.302887] usb 6-2: configuration #1 chosen from 1 choice
[    5.356018] ata5: SATA link down (SStatus 0 SControl 300)
[    5.696014] ata6: SATA link down (SStatus 0 SControl 300)
[    5.712109] scsi 0:0:0:0: Direct-Access     ATA      SAMSUNG HD502IJ  1AA0 PQ: 0 ANSI: 5
[    5.712210] scsi 1:0:0:0: Direct-Access     ATA      SAMSUNG HD502IJ  1AA0 PQ: 0 ANSI: 5
[    5.712288] scsi 2:0:0:0: Direct-Access     ATA      SAMSUNG HD502IJ  1AA0 PQ: 0 ANSI: 5
[    5.712394] ATL1E 0000:02:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    5.712409] ATL1E 0000:02:00.0: setting latency timer to 64
[    5.712449] pata_marvell 0000:03:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    5.712468] pata_marvell 0000:03:00.0: setting latency timer to 64
[    5.712580] scsi6 : pata_marvell
[    5.712807] scsi7 : pata_marvell
[    5.712834] ata7: PATA max UDMA/100 cmd 0xec00 ctl 0xe880 bmdma 0xe400 irq 16
[    5.712836] ata8: DUMMY
[    5.756778] scsi 0:0:0:0: Attached scsi generic sg0 type 0
[    5.756806] scsi 1:0:0:0: Attached scsi generic sg1 type 0
[    5.756842] scsi 2:0:0:0: Attached scsi generic sg2 type 0
[    5.767664] Driver 'sd' needs updating - please use bus_type methods
[    5.767747] sd 0:0:0:0: [sda] 976773168 512-byte hardware sectors (500108 MB)
[    5.767762] sd 0:0:0:0: [sda] Write Protect is off
[    5.767764] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    5.767783] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    5.767835] sd 0:0:0:0: [sda] 976773168 512-byte hardware sectors (500108 MB)
[    5.767845] sd 0:0:0:0: [sda] Write Protect is off
[    5.767847] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    5.767866] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    5.767868]  sda: sda1 sda2 < >
[    5.779903] sda: p1 exceeds device capacity
[    5.779920] sda: p2 exceeds device capacity
[    5.780008] sd 0:0:0:0: [sda] Attached SCSI disk
[    5.780061] sd 1:0:0:0: [sdb] 976773168 512-byte hardware sectors (500108 MB)
[    5.780073] sd 1:0:0:0: [sdb] Write Protect is off
[    5.780074] sd 1:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[    5.780095] sd 1:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    5.780138] sd 1:0:0:0: [sdb] 976773168 512-byte hardware sectors (500108 MB)
[    5.780149] sd 1:0:0:0: [sdb] Write Protect is off
[    5.780151] sd 1:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[    5.780171] sd 1:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    5.780173]  sdb: unknown partition table
[    5.790783] sd 1:0:0:0: [sdb] Attached SCSI disk
[    5.790846] sd 2:0:0:0: [sdc] 976773168 512-byte hardware sectors (500108 MB)
[    5.790858] sd 2:0:0:0: [sdc] Write Protect is off
[    5.790859] sd 2:0:0:0: [sdc] Mode Sense: 00 3a 00 00
[    5.790880] sd 2:0:0:0: [sdc] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    5.790919] sd 2:0:0:0: [sdc] 976773168 512-byte hardware sectors (500108 MB)
[    5.790930] sd 2:0:0:0: [sdc] Write Protect is off
[    5.790932] sd 2:0:0:0: [sdc] Mode Sense: 00 3a 00 00
[    5.790952] sd 2:0:0:0: [sdc] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    5.790955]  sdc: unknown partition table
[    5.798169] sd 2:0:0:0: [sdc] Attached SCSI disk
[    6.068334] ata7.00: ATAPI: SONY    CD-RW  CRX195E1, ZYS5, max UDMA/33
[    6.068343] ata7.01: ATAPI: ATAPI   DVD A  DH20A4P, 9P59, max UDMA/66
[    6.068349] ata7.01: limited to UDMA/33 due to 40-wire cable
[    6.084847] ata7.00: configured for UDMA/33
[    6.116334] ata7.01: configured for UDMA/33
[    6.116773] scsi 6:0:0:0: CD-ROM            SONY     CD-RW  CRX195E1  ZYS5 PQ: 0 ANSI: 5
[    6.116901] scsi 6:0:0:0: Attached scsi generic sg3 type 5
[    6.117915] scsi 6:0:1:0: CD-ROM            ATAPI    DVD A  DH20A4P   9P59 PQ: 0 ANSI: 5
[    6.117971] scsi 6:0:1:0: Attached scsi generic sg4 type 5
[    6.136148] Driver 'sr' needs updating - please use bus_type methods
[    6.137163] sr0: scsi3-mmc drive: 40x/40x writer cd/rw xa/form2 cdda tray
[    6.137165] Uniform CD-ROM driver Revision: 3.20
[    6.137233] sr 6:0:0:0: Attached scsi CD-ROM sr0
[    6.142187] sr1: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
[    6.142289] sr 6:0:1:0: Attached scsi CD-ROM sr1
[    6.857310] attempt to access beyond end of device
[    6.857314] sda: rw=0, want=2906544062, limit=976773168
[    6.857316] Buffer I/O error on device sda2, logical block 0
[    6.857324] attempt to access beyond end of device
[    6.857325] sda: rw=0, want=2906544062, limit=976773168
[    6.857327] Buffer I/O error on device sda2, logical block 0
[    6.863519] attempt to access beyond end of device
[    6.863523] sda: rw=0, want=2906543808, limit=976773168
[    6.863526] Buffer I/O error on device sda1, logical block 2906543744
[    6.863530] attempt to access beyond end of device
[    6.863531] sda: rw=0, want=2906543809, limit=976773168
[    6.863533] Buffer I/O error on device sda1, logical block 2906543745
[    6.863535] attempt to access beyond end of device
[    6.863537] sda: rw=0, want=2906543810, limit=976773168
[    6.863539] Buffer I/O error on device sda1, logical block 2906543746
[    6.863541] attempt to access beyond end of device
[    6.863543] sda: rw=0, want=2906543811, limit=976773168
[    6.863545] Buffer I/O error on device sda1, logical block 2906543747
[    6.863547] attempt to access beyond end of device
[    6.863548] sda: rw=0, want=2906543812, limit=976773168
[    6.863550] Buffer I/O error on device sda1, logical block 2906543748
[    6.863553] attempt to access beyond end of device
[    6.863554] sda: rw=0, want=2906543813, limit=976773168
[    6.863556] Buffer I/O error on device sda1, logical block 2906543749
[    6.863558] attempt to access beyond end of device
[    6.863560] sda: rw=0, want=2906543814, limit=976773168
[    6.863562] Buffer I/O error on device sda1, logical block 2906543750
[    6.863564] attempt to access beyond end of device
[    6.863566] sda: rw=0, want=2906543815, limit=976773168
[    6.863567] Buffer I/O error on device sda1, logical block 2906543751
[    6.863570] attempt to access beyond end of device
[    6.863572] sda: rw=0, want=2906543808, limit=976773168
[    6.863574] attempt to access beyond end of device
[    6.863576] sda: rw=0, want=2906543809, limit=976773168
[    6.863578] attempt to access beyond end of device
[    6.863580] sda: rw=0, want=2906543810, limit=976773168
[    6.863582] attempt to access beyond end of device
[    6.863584] sda: rw=0, want=2906543811, limit=976773168
[    6.863586] attempt to access beyond end of device
[    6.863587] sda: rw=0, want=2906543812, limit=976773168
[    6.863589] attempt to access beyond end of device
[    6.863591] sda: rw=0, want=2906543813, limit=976773168
[    6.863593] attempt to access beyond end of device
[    6.863600] sda: rw=0, want=2906543814, limit=976773168
[    6.863602] attempt to access beyond end of device
[    6.863603] sda: rw=0, want=2906543815, limit=976773168
[    6.863614] attempt to access beyond end of device
[    6.863615] sda: rw=0, want=2906544040, limit=976773168
[    6.863617] attempt to access beyond end of device
[    6.863618] sda: rw=0, want=2906544041, limit=976773168
[    6.863619] attempt to access beyond end of device
[    6.863620] sda: rw=0, want=2906544042, limit=976773168
[    6.863622] attempt to access beyond end of device
[    6.863623] sda: rw=0, want=2906544043, limit=976773168
[    6.863624] attempt to access beyond end of device
[    6.863626] sda: rw=0, want=2906544044, limit=976773168
[    6.863627] attempt to access beyond end of device
[    6.863628] sda: rw=0, want=2906544045, limit=976773168
[    6.863630] attempt to access beyond end of device
[    6.863631] sda: rw=0, want=2906544046, limit=976773168
[    6.863632] attempt to access beyond end of device
[    6.863634] sda: rw=0, want=2906544047, limit=976773168
[    6.863635] attempt to access beyond end of device
[    6.863637] sda: rw=0, want=2906544040, limit=976773168
[    6.863638] attempt to access beyond end of device
[    6.863639] sda: rw=0, want=2906544041, limit=976773168
[    6.863641] attempt to access beyond end of device
[    6.863642] sda: rw=0, want=2906544042, limit=976773168
[    6.863643] attempt to access beyond end of device
[    6.863644] sda: rw=0, want=2906544043, limit=976773168
[    6.863646] attempt to access beyond end of device
[    6.863647] sda: rw=0, want=2906544044, limit=976773168
[    6.863649] attempt to access beyond end of device
[    6.863650] sda: rw=0, want=2906544045, limit=976773168
[    6.863651] attempt to access beyond end of device
[    6.863652] sda: rw=0, want=2906544046, limit=976773168
[    6.863660] attempt to access beyond end of device
[    6.863661] sda: rw=0, want=2906544047, limit=976773168
[    6.863693] attempt to access beyond end of device
[    6.863695] sda: rw=0, want=2906544056, limit=976773168
[    6.863697] attempt to access beyond end of device
[    6.863698] sda: rw=0, want=2906544057, limit=976773168
[    6.863699] attempt to access beyond end of device
[    6.863701] sda: rw=0, want=2906544058, limit=976773168
[    6.863702] attempt to access beyond end of device
[    6.863703] sda: rw=0, want=2906544059, limit=976773168
[    6.863705] attempt to access beyond end of device
[    6.863706] sda: rw=0, want=2906544060, limit=976773168
[    6.863708] attempt to access beyond end of device
[    6.863709] sda: rw=0, want=2906544056, limit=976773168
[    6.863710] attempt to access beyond end of device
[    6.863712] sda: rw=0, want=2906544057, limit=976773168
[    6.863713] attempt to access beyond end of device
[    6.863714] sda: rw=0, want=2906544058, limit=976773168
[    6.863716] attempt to access beyond end of device
[    6.863717] sda: rw=0, want=2906544059, limit=976773168
[    6.863718] attempt to access beyond end of device
[    6.863720] sda: rw=0, want=2906544060, limit=976773168
[    6.863724] attempt to access beyond end of device
[    6.863725] sda: rw=0, want=2906544056, limit=976773168
[    6.863727] attempt to access beyond end of device
[    6.863728] sda: rw=0, want=2906544057, limit=976773168
[    6.863729] attempt to access beyond end of device
[    6.863730] sda: rw=0, want=2906544058, limit=976773168
[    6.863732] attempt to access beyond end of device
[    6.863733] sda: rw=0, want=2906544059, limit=976773168
[    6.863735] attempt to access beyond end of device
[    6.863736] sda: rw=0, want=2906544060, limit=976773168
[    6.863739] attempt to access beyond end of device
[    6.863741] sda: rw=0, want=2906544056, limit=976773168
[    6.863742] attempt to access beyond end of device
[    6.863743] sda: rw=0, want=2906544057, limit=976773168
[    6.863745] attempt to access beyond end of device
[    6.863746] sda: rw=0, want=2906544058, limit=976773168
[    6.863748] attempt to access beyond end of device
[    6.863749] sda: rw=0, want=2906544059, limit=976773168
[    6.863750] attempt to access beyond end of device
[    6.863752] sda: rw=0, want=2906544060, limit=976773168
[    6.863755] attempt to access beyond end of device
[    6.863756] sda: rw=0, want=2906544056, limit=976773168
[    6.863758] attempt to access beyond end of device
[    6.863760] sda: rw=0, want=2906544057, limit=976773168
[    6.863761] attempt to access beyond end of device
[    6.863762] sda: rw=0, want=2906544058, limit=976773168
[    6.863764] attempt to access beyond end of device
[    6.863765] sda: rw=0, want=2906544059, limit=976773168
[    6.863766] attempt to access beyond end of device
[    6.863768] sda: rw=0, want=2906544060, limit=976773168
[    6.863772] attempt to access beyond end of device
[    6.863773] sda: rw=0, want=2906544056, limit=976773168
[    6.863775] attempt to access beyond end of device
[    6.863776] sda: rw=0, want=2906544057, limit=976773168
[    6.863777] attempt to access beyond end of device
[    6.863778] sda: rw=0, want=2906544058, limit=976773168
[    6.863780] attempt to access beyond end of device
[    6.863781] sda: rw=0, want=2906544059, limit=976773168
[    6.863782] attempt to access beyond end of device
[    6.863783] sda: rw=0, want=2906544060, limit=976773168
[    6.863787] attempt to access beyond end of device
[    6.863788] sda: rw=0, want=2906544056, limit=976773168
[    6.863790] attempt to access beyond end of device
[    6.863791] sda: rw=0, want=2906544057, limit=976773168
[    6.863793] attempt to access beyond end of device
[    6.863794] sda: rw=0, want=2906544058, limit=976773168
[    6.863795] attempt to access beyond end of device
[    6.863796] sda: rw=0, want=2906544059, limit=976773168
[    6.863798] attempt to access beyond end of device
[    6.863799] sda: rw=0, want=2906544060, limit=976773168
[    6.863805] attempt to access beyond end of device
[    6.863806] sda: rw=0, want=2906543992, limit=976773168
[    6.863807] attempt to access beyond end of device
[    6.863809] sda: rw=0, want=2906543993, limit=976773168
[    6.863810] attempt to access beyond end of device
[    6.863811] sda: rw=0, want=2906543994, limit=976773168
[    6.863813] attempt to access beyond end of device
[    6.863814] sda: rw=0, want=2906543995, limit=976773168
[    6.863815] attempt to access beyond end of device
[    6.863816] sda: rw=0, want=2906543996, limit=976773168
[    6.863818] attempt to access beyond end of device
[    6.863819] sda: rw=0, want=2906543997, limit=976773168
[    6.863820] attempt to access beyond end of device
[    6.863822] sda: rw=0, want=2906543998, limit=976773168
[    6.863823] attempt to access beyond end of device
[    6.863824] sda: rw=0, want=2906543999, limit=976773168
[    6.863830] attempt to access beyond end of device
[    6.863831] sda: rw=0, want=2906544048, limit=976773168
[    6.863833] attempt to access beyond end of device
[    6.863834] sda: rw=0, want=2906544049, limit=976773168
[    6.863835] attempt to access beyond end of device
[    6.863837] sda: rw=0, want=2906544050, limit=976773168
[    6.863838] attempt to access beyond end of device
[    6.863839] sda: rw=0, want=2906544051, limit=976773168
[    6.863841] attempt to access beyond end of device
[    6.863842] sda: rw=0, want=2906544052, limit=976773168
[    6.863843] attempt to access beyond end of device
[    6.863845] sda: rw=0, want=2906544053, limit=976773168
[    6.863846] attempt to access beyond end of device
[    6.863847] sda: rw=0, want=2906544054, limit=976773168
[    6.863849] attempt to access beyond end of device
[    6.863850] sda: rw=0, want=2906544055, limit=976773168
[    6.863854] attempt to access beyond end of device
[    6.863855] sda: rw=0, want=2906544056, limit=976773168
[    6.863857] attempt to access beyond end of device
[    6.863858] sda: rw=0, want=2906544057, limit=976773168
[    6.863859] attempt to access beyond end of device
[    6.863860] sda: rw=0, want=2906544058, limit=976773168
[    6.863862] attempt to access beyond end of device
[    6.863863] sda: rw=0, want=2906544059, limit=976773168
[    6.863864] attempt to access beyond end of device
[    6.863866] sda: rw=0, want=2906544060, limit=976773168
[    6.863869] attempt to access beyond end of device
[    6.863871] sda: rw=0, want=2906544056, limit=976773168
[    6.863873] attempt to access beyond end of device
[    6.863874] sda: rw=0, want=2906544057, limit=976773168
[    6.863876] attempt to access beyond end of device
[    6.863877] sda: rw=0, want=2906544058, limit=976773168
[    6.863878] attempt to access beyond end of device
[    6.863879] sda: rw=0, want=2906544059, limit=976773168
[    6.863881] attempt to access beyond end of device
[    6.863882] sda: rw=0, want=2906544060, limit=976773168
[    6.898213] PM: Starting manual resume from disk
[    6.898215] PM: Resume from partition 254:2
[    6.898216] PM: Checking hibernation image.
[    6.898322] PM: Resume from disk failed.
[    6.996740] kjournald starting.  Commit interval 5 seconds
[    6.996755] EXT3-fs: mounted filesystem with ordered data mode.
[   11.231356] udevd version 124 started
[   11.463524] input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input2
[   11.484424] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   11.489516] ACPI: Power Button (FF) [PWRF]
[   11.489595] input: Power Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input3
[   11.496727] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   11.521524] ACPI: Power Button (CM) [PWRB]
[   11.639010] ath_hal: module license 'Proprietary' taints kernel.
[   11.639783] ath_hal: 0.9.18.0 (AR5210, AR5211, AR5212, RF5111, RF5112, RF2413, RF5413)
[   11.645889] wlan: 0.9.4
[   11.652033] ath_pci: 0.9.4
[   11.652067] ath_pci 0000:05:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   12.237565] ath_rate_sample: 1.2 (0.9.4)
[   12.237959] wifi0: 11b rates: 1Mbps 2Mbps 5.5Mbps 11Mbps
[   12.237963] wifi0: 11g rates: 1Mbps 2Mbps 5.5Mbps 11Mbps 6Mbps 9Mbps 12Mbps 18Mbps 24Mbps 36Mbps 48Mbps 54Mbps
[   12.237969] wifi0: turboG rates: 6Mbps 12Mbps 18Mbps 24Mbps 36Mbps 48Mbps 54Mbps
[   12.237973] wifi0: H/W encryption support: WEP AES AES_CCM TKIP
[   12.237976] wifi0: mac 7.9 phy 4.5 radio 5.6
[   12.237978] wifi0: Use hw queue 1 for WME_AC_BE traffic
[   12.237979] wifi0: Use hw queue 0 for WME_AC_BK traffic
[   12.237980] wifi0: Use hw queue 2 for WME_AC_VI traffic
[   12.237981] wifi0: Use hw queue 3 for WME_AC_VO traffic
[   12.237982] wifi0: Use hw queue 8 for CAB traffic
[   12.237983] wifi0: Use hw queue 9 for beacons
[   12.511474] wifi0: Atheros 5212: mem=0xfebf0000, irq=16
[   12.511512] nvidia 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   12.511520] nvidia 0000:01:00.0: setting latency timer to 64
[   12.511602] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  177.82  Tue Nov  4 16:50:05 PST 2008
[   12.544942] usblp0: USB Bidirectional printer dev 6 if 1 alt 0 proto 2 vid 0x03F0 pid 0x3F11
[   12.544956] usbcore: registered new interface driver usblp
[   12.552663] input: PC Speaker as /devices/platform/pcspkr/input/input4
[   12.567254] Linux video capture interface: v2.00
[   12.613812] uvcvideo: Found UVC 1.00 device <unnamed> (046d:0994)
[   12.643662] input: UVC Camera (046d:0994) as /devices/pci0000:00/0000:00:1d.7/usb8/8-2/8-2:1.0/input/input5
[   12.723446] usbcore: registered new interface driver uvcvideo
[   12.723449] USB Video Class driver (v0.1.0)
[   12.723460] usbcore: registered new interface driver snd-usb-audio
[   12.877702] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   12.877724] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   12.913956] hda_codec: Unknown model for ALC883, trying auto-probe from BIOS...
[   13.016990] attempt to access beyond end of device
[   13.016993] sda: rw=0, want=2906544062, limit=976773168
[   13.016995] __ratelimit: 85 callbacks suppressed
[   13.016997] Buffer I/O error on device sda2, logical block 0
[   13.017000] attempt to access beyond end of device
[   13.017001] sda: rw=0, want=2906544062, limit=976773168
[   13.017003] Buffer I/O error on device sda2, logical block 0
[   13.017219] attempt to access beyond end of device
[   13.017221] sda: rw=0, want=2906543808, limit=976773168
[   13.017223] Buffer I/O error on device sda1, logical block 2906543744
[   13.017229] attempt to access beyond end of device
[   13.017230] sda: rw=0, want=2906543809, limit=976773168
[   13.017231] Buffer I/O error on device sda1, logical block 2906543745
[   13.017233] attempt to access beyond end of device
[   13.017234] sda: rw=0, want=2906543810, limit=976773168
[   13.017236] Buffer I/O error on device sda1, logical block 2906543746
[   13.017237] attempt to access beyond end of device
[   13.017238] sda: rw=0, want=2906543811, limit=976773168
[   13.017240] Buffer I/O error on device sda1, logical block 2906543747
[   13.017241] attempt to access beyond end of device
[   13.017242] sda: rw=0, want=2906543812, limit=976773168
[   13.017244] Buffer I/O error on device sda1, logical block 2906543748
[   13.017245] attempt to access beyond end of device
[   13.017246] sda: rw=0, want=2906543813, limit=976773168
[   13.017248] Buffer I/O error on device sda1, logical block 2906543749
[   13.017249] attempt to access beyond end of device
[   13.017250] sda: rw=0, want=2906543814, limit=976773168
[   13.017252] Buffer I/O error on device sda1, logical block 2906543750
[   13.017253] attempt to access beyond end of device
[   13.017254] sda: rw=0, want=2906543815, limit=976773168
[   13.017256] Buffer I/O error on device sda1, logical block 2906543751
[   13.017258] attempt to access beyond end of device
[   13.017259] sda: rw=0, want=2906543808, limit=976773168
[   13.017260] attempt to access beyond end of device
[   13.017262] sda: rw=0, want=2906543809, limit=976773168
[   13.017263] attempt to access beyond end of device
[   13.017264] sda: rw=0, want=2906543810, limit=976773168
[   13.017266] attempt to access beyond end of device
[   13.017267] sda: rw=0, want=2906543811, limit=976773168
[   13.017268] attempt to access beyond end of device
[   13.017270] sda: rw=0, want=2906543812, limit=976773168
[   13.017271] attempt to access beyond end of device
[   13.017272] sda: rw=0, want=2906543813, limit=976773168
[   13.017274] attempt to access beyond end of device
[   13.017275] sda: rw=0, want=2906543814, limit=976773168
[   13.017276] attempt to access beyond end of device
[   13.017277] sda: rw=0, want=2906543815, limit=976773168
[   13.017290] attempt to access beyond end of device
[   13.017291] sda: rw=0, want=2906544040, limit=976773168
[   13.017295] attempt to access beyond end of device
[   13.017296] sda: rw=0, want=2906544041, limit=976773168
[   13.017298] attempt to access beyond end of device
[   13.017299] sda: rw=0, want=2906544042, limit=976773168
[   13.017301] attempt to access beyond end of device
[   13.017302] sda: rw=0, want=2906544043, limit=976773168
[   13.017303] attempt to access beyond end of device
[   13.017305] sda: rw=0, want=2906544044, limit=976773168
[   13.017306] attempt to access beyond end of device
[   13.017307] sda: rw=0, want=2906544045, limit=976773168
[   13.017309] attempt to access beyond end of device
[   13.017310] sda: rw=0, want=2906544046, limit=976773168
[   13.017311] attempt to access beyond end of device
[   13.017313] sda: rw=0, want=2906544047, limit=976773168
[   13.017314] attempt to access beyond end of device
[   13.017316] sda: rw=0, want=2906544040, limit=976773168
[   13.017317] attempt to access beyond end of device
[   13.017318] sda: rw=0, want=2906544041, limit=976773168
[   13.017320] attempt to access beyond end of device
[   13.017321] sda: rw=0, want=2906544042, limit=976773168
[   13.017323] attempt to access beyond end of device
[   13.017324] sda: rw=0, want=2906544043, limit=976773168
[   13.017325] attempt to access beyond end of device
[   13.017326] sda: rw=0, want=2906544044, limit=976773168
[   13.017328] attempt to access beyond end of device
[   13.017329] sda: rw=0, want=2906544045, limit=976773168
[   13.017330] attempt to access beyond end of device
[   13.017332] sda: rw=0, want=2906544046, limit=976773168
[   13.017333] attempt to access beyond end of device
[   13.017334] sda: rw=0, want=2906544047, limit=976773168
[   13.017383] attempt to access beyond end of device
[   13.017385] sda: rw=0, want=2906544056, limit=976773168
[   13.017387] attempt to access beyond end of device
[   13.017388] sda: rw=0, want=2906544057, limit=976773168
[   13.017390] attempt to access beyond end of device
[   13.017391] sda: rw=0, want=2906544058, limit=976773168
[   13.017392] attempt to access beyond end of device
[   13.017393] sda: rw=0, want=2906544059, limit=976773168
[   13.017395] attempt to access beyond end of device
[   13.017396] sda: rw=0, want=2906544060, limit=976773168
[   13.017398] attempt to access beyond end of device
[   13.017399] sda: rw=0, want=2906544056, limit=976773168
[   13.017401] attempt to access beyond end of device
[   13.017402] sda: rw=0, want=2906544057, limit=976773168
[   13.017403] attempt to access beyond end of device
[   13.017404] sda: rw=0, want=2906544058, limit=976773168
[   13.017406] attempt to access beyond end of device
[   13.017407] sda: rw=0, want=2906544059, limit=976773168
[   13.017408] attempt to access beyond end of device
[   13.017410] sda: rw=0, want=2906544060, limit=976773168
[   13.017414] attempt to access beyond end of device
[   13.017415] sda: rw=0, want=2906544056, limit=976773168
[   13.017417] attempt to access beyond end of device
[   13.017418] sda: rw=0, want=2906544057, limit=976773168
[   13.017420] attempt to access beyond end of device
[   13.017421] sda: rw=0, want=2906544058, limit=976773168
[   13.017422] attempt to access beyond end of device
[   13.017423] sda: rw=0, want=2906544059, limit=976773168
[   13.017425] attempt to access beyond end of device
[   13.017426] sda: rw=0, want=2906544060, limit=976773168
[   13.017430] attempt to access beyond end of device
[   13.017431] sda: rw=0, want=2906544056, limit=976773168
[   13.017433] attempt to access beyond end of device
[   13.017434] sda: rw=0, want=2906544057, limit=976773168
[   13.017435] attempt to access beyond end of device
[   13.017436] sda: rw=0, want=2906544058, limit=976773168
[   13.017438] attempt to access beyond end of device
[   13.017439] sda: rw=0, want=2906544059, limit=976773168
[   13.017441] attempt to access beyond end of device
[   13.017442] sda: rw=0, want=2906544060, limit=976773168
[   13.017445] attempt to access beyond end of device
[   13.017446] sda: rw=0, want=2906544056, limit=976773168
[   13.017448] attempt to access beyond end of device
[   13.017449] sda: rw=0, want=2906544057, limit=976773168
[   13.017451] attempt to access beyond end of device
[   13.017452] sda: rw=0, want=2906544058, limit=976773168
[   13.017454] attempt to access beyond end of device
[   13.017455] sda: rw=0, want=2906544059, limit=976773168
[   13.017456] attempt to access beyond end of device
[   13.017457] sda: rw=0, want=2906544060, limit=976773168
[   13.017461] attempt to access beyond end of device
[   13.017463] sda: rw=0, want=2906544056, limit=976773168
[   13.017464] attempt to access beyond end of device
[   13.017466] sda: rw=0, want=2906544057, limit=976773168
[   13.017467] attempt to access beyond end of device
[   13.017468] sda: rw=0, want=2906544058, limit=976773168
[   13.017470] attempt to access beyond end of device
[   13.017471] sda: rw=0, want=2906544059, limit=976773168
[   13.017472] attempt to access beyond end of device
[   13.017474] sda: rw=0, want=2906544060, limit=976773168
[   13.017477] attempt to access beyond end of device
[   13.017478] sda: rw=0, want=2906544056, limit=976773168
[   13.017480] attempt to access beyond end of device
[   13.017481] sda: rw=0, want=2906544057, limit=976773168
[   13.017483] attempt to access beyond end of device
[   13.017484] sda: rw=0, want=2906544058, limit=976773168
[   13.017486] attempt to access beyond end of device
[   13.017487] sda: rw=0, want=2906544059, limit=976773168
[   13.017488] attempt to access beyond end of device
[   13.017490] sda: rw=0, want=2906544060, limit=976773168
[   13.017495] attempt to access beyond end of device
[   13.017497] sda: rw=0, want=2906543992, limit=976773168
[   13.017498] attempt to access beyond end of device
[   13.017500] sda: rw=0, want=2906543993, limit=976773168
[   13.017501] attempt to access beyond end of device
[   13.017502] sda: rw=0, want=2906543994, limit=976773168
[   13.017504] attempt to access beyond end of device
[   13.017505] sda: rw=0, want=2906543995, limit=976773168
[   13.017506] attempt to access beyond end of device
[   13.017508] sda: rw=0, want=2906543996, limit=976773168
[   13.017509] attempt to access beyond end of device
[   13.017510] sda: rw=0, want=2906543997, limit=976773168
[   13.017512] attempt to access beyond end of device
[   13.017513] sda: rw=0, want=2906543998, limit=976773168
[   13.017514] attempt to access beyond end of device
[   13.017515] sda: rw=0, want=2906543999, limit=976773168
[   13.017522] attempt to access beyond end of device
[   13.017523] sda: rw=0, want=2906544048, limit=976773168
[   13.017525] attempt to access beyond end of device
[   13.017526] sda: rw=0, want=2906544049, limit=976773168
[   13.017528] attempt to access beyond end of device
[   13.017529] sda: rw=0, want=2906544050, limit=976773168
[   13.017530] attempt to access beyond end of device
[   13.017532] sda: rw=0, want=2906544051, limit=976773168
[   13.017533] attempt to access beyond end of device
[   13.017534] sda: rw=0, want=2906544052, limit=976773168
[   13.017536] attempt to access beyond end of device
[   13.017537] sda: rw=0, want=2906544053, limit=976773168
[   13.017538] attempt to access beyond end of device
[   13.017539] sda: rw=0, want=2906544054, limit=976773168
[   13.017541] attempt to access beyond end of device
[   13.017542] sda: rw=0, want=2906544055, limit=976773168
[   13.017546] attempt to access beyond end of device
[   13.017547] sda: rw=0, want=2906544056, limit=976773168
[   13.017549] attempt to access beyond end of device
[   13.017550] sda: rw=0, want=2906544057, limit=976773168
[   13.017551] attempt to access beyond end of device
[   13.017553] sda: rw=0, want=2906544058, limit=976773168
[   13.017554] attempt to access beyond end of device
[   13.017555] sda: rw=0, want=2906544059, limit=976773168
[   13.017557] attempt to access beyond end of device
[   13.017558] sda: rw=0, want=2906544060, limit=976773168
[   13.017562] attempt to access beyond end of device
[   13.017563] sda: rw=0, want=2906544056, limit=976773168
[   13.017564] attempt to access beyond end of device
[   13.017565] sda: rw=0, want=2906544057, limit=976773168
[   13.017567] attempt to access beyond end of device
[   13.017568] sda: rw=0, want=2906544058, limit=976773168
[   13.017570] attempt to access beyond end of device
[   13.017571] sda: rw=0, want=2906544059, limit=976773168
[   13.017572] attempt to access beyond end of device
[   13.017573] sda: rw=0, want=2906544060, limit=976773168
[   13.299463] input: ImPS/2 Generic Wheel Mouse as /devices/platform/i8042/serio1/input/input6
[   15.085143] loop: module loaded
[   15.128684] lp: driver loaded but no devices found
[   15.225919] Adding 11871992k swap on /dev/mapper/isw_cidhfbaebi_raidical5.  Priority:-1 extents:1 across:11871992k
[   15.759621] EXT3 FS on dm-1, internal journal
[   16.984186] ip_tables: (C) 2000-2006 Netfilter Core Team
[   17.463188] ACPI: WMI: Mapper loaded
[   18.429960] warning: `avahi-daemon' uses 32-bit capabilities (legacy support in use)
[   18.849492] NET: Registered protocol family 10
[   18.849943] lo: Disabled Privacy Extensions
[   19.137914] ppdev: user-space parallel port driver
[   22.552425] vboxdrv: Trying to deactivate the NMI watchdog permanently...
[   22.552434] vboxdrv: Successfully done.
[   22.552436] vboxdrv: Found 4 processor cores.
[   22.553052] VBoxDrv: dbg - g_abExecMemory=ffffffffa0caafc0
[   22.553104] vboxdrv: fAsync=0 offMin=0x525 offMax=0x1f8b
[   22.554223] vboxdrv: TSC mode is 'synchronous', kernel timer mode is 'normal'.
[   22.554225] vboxdrv: Successfully loaded version 2.1.0 (interface 0x000a0008).
[   23.916816] attempt to access beyond end of device
[   23.916823] sda: rw=0, want=2906543808, limit=976773168
[   23.916825] __ratelimit: 94 callbacks suppressed
[   23.916829] Buffer I/O error on device sda1, logical block 2906543744
[   23.916832] attempt to access beyond end of device
[   23.916834] sda: rw=0, want=2906543809, limit=976773168
[   23.916836] Buffer I/O error on device sda1, logical block 2906543745
[   23.916839] attempt to access beyond end of device
[   23.916840] sda: rw=0, want=2906543810, limit=976773168
[   23.916842] Buffer I/O error on device sda1, logical block 2906543746
[   23.916844] attempt to access beyond end of device
[   23.916846] sda: rw=0, want=2906543811, limit=976773168
[   23.916848] Buffer I/O error on device sda1, logical block 2906543747
[   23.916850] attempt to access beyond end of device
[   23.916852] sda: rw=0, want=2906543812, limit=976773168
[   23.916855] Buffer I/O error on device sda1, logical block 2906543748
[   23.916857] attempt to access beyond end of device
[   23.916858] sda: rw=0, want=2906543813, limit=976773168
[   23.916860] Buffer I/O error on device sda1, logical block 2906543749
[   23.916863] attempt to access beyond end of device
[   23.916865] sda: rw=0, want=2906543814, limit=976773168
[   23.916867] Buffer I/O error on device sda1, logical block 2906543750
[   23.916870] attempt to access beyond end of device
[   23.916872] sda: rw=0, want=2906543815, limit=976773168
[   23.916873] Buffer I/O error on device sda1, logical block 2906543751
[   23.916877] attempt to access beyond end of device
[   23.916879] sda: rw=0, want=2906543808, limit=976773168
[   23.916881] Buffer I/O error on device sda1, logical block 2906543744
[   23.916883] attempt to access beyond end of device
[   23.916885] sda: rw=0, want=2906543809, limit=976773168
[   23.916888] Buffer I/O error on device sda1, logical block 2906543745
[   23.916890] attempt to access beyond end of device
[   23.916892] sda: rw=0, want=2906543810, limit=976773168
[   23.916895] attempt to access beyond end of device
[   23.916897] sda: rw=0, want=2906543811, limit=976773168
[   23.916899] attempt to access beyond end of device
[   23.916901] sda: rw=0, want=2906543812, limit=976773168
[   23.916903] attempt to access beyond end of device
[   23.916905] sda: rw=0, want=2906543813, limit=976773168
[   23.916908] attempt to access beyond end of device
[   23.916910] sda: rw=0, want=2906543814, limit=976773168
[   23.916912] attempt to access beyond end of device
[   23.916915] sda: rw=0, want=2906543815, limit=976773168
[   23.916926] attempt to access beyond end of device
[   23.916929] sda: rw=0, want=2906544040, limit=976773168
[   23.916931] attempt to access beyond end of device
[   23.916933] sda: rw=0, want=2906544041, limit=976773168
[   23.916936] attempt to access beyond end of device
[   23.916937] sda: rw=0, want=2906544042, limit=976773168
[   23.916940] attempt to access beyond end of device
[   23.916942] sda: rw=0, want=2906544043, limit=976773168
[   23.916944] attempt to access beyond end of device
[   23.916946] sda: rw=0, want=2906544044, limit=976773168
[   23.916949] attempt to access beyond end of device
[   23.916950] sda: rw=0, want=2906544045, limit=976773168
[   23.916953] attempt to access beyond end of device
[   23.916955] sda: rw=0, want=2906544046, limit=976773168
[   23.916957] attempt to access beyond end of device
[   23.916959] sda: rw=0, want=2906544047, limit=976773168
[   23.916962] attempt to access beyond end of device
[   23.916964] sda: rw=0, want=2906544040, limit=976773168
[   23.916966] attempt to access beyond end of device
[   23.916968] sda: rw=0, want=2906544041, limit=976773168
[   23.916970] attempt to access beyond end of device
[   23.916973] sda: rw=0, want=2906544042, limit=976773168
[   23.916975] attempt to access beyond end of device
[   23.916977] sda: rw=0, want=2906544043, limit=976773168
[   23.916980] attempt to access beyond end of device
[   23.916981] sda: rw=0, want=2906544044, limit=976773168
[   23.916983] attempt to access beyond end of device
[   23.916986] sda: rw=0, want=2906544045, limit=976773168
[   23.916988] attempt to access beyond end of device
[   23.916990] sda: rw=0, want=2906544046, limit=976773168
[   23.916993] attempt to access beyond end of device
[   23.916994] sda: rw=0, want=2906544047, limit=976773168
[   23.917037] attempt to access beyond end of device
[   23.917039] sda: rw=0, want=2906544056, limit=976773168
[   23.917042] attempt to access beyond end of device
[   23.917044] sda: rw=0, want=2906544057, limit=976773168
[   23.917046] attempt to access beyond end of device
[   23.917048] sda: rw=0, want=2906544058, limit=976773168
[   23.917050] attempt to access beyond end of device
[   23.917053] sda: rw=0, want=2906544059, limit=976773168
[   23.917055] attempt to access beyond end of device
[   23.917056] sda: rw=0, want=2906544060, limit=976773168
[   23.917060] attempt to access beyond end of device
[   23.917062] sda: rw=0, want=2906544056, limit=976773168
[   23.917064] attempt to access beyond end of device
[   23.917066] sda: rw=0, want=2906544057, limit=976773168
[   23.917068] attempt to access beyond end of device
[   23.917071] sda: rw=0, want=2906544058, limit=976773168
[   23.917073] attempt to access beyond end of device
[   23.917074] sda: rw=0, want=2906544059, limit=976773168
[   23.917077] attempt to access beyond end of device
[   23.917079] sda: rw=0, want=2906544060, limit=976773168
[   23.917088] attempt to access beyond end of device
[   23.917090] sda: rw=0, want=2906544056, limit=976773168
[   23.917092] attempt to access beyond end of device
[   23.917095] sda: rw=0, want=2906544057, limit=976773168
[   23.917097] attempt to access beyond end of device
[   23.917099] sda: rw=0, want=2906544058, limit=976773168
[   23.917102] attempt to access beyond end of device
[   23.917103] sda: rw=0, want=2906544059, limit=976773168
[   23.917105] attempt to access beyond end of device
[   23.917108] sda: rw=0, want=2906544060, limit=976773168
[   23.917114] attempt to access beyond end of device
[   23.917115] sda: rw=0, want=2906544056, limit=976773168
[   23.917118] attempt to access beyond end of device
[   23.917120] sda: rw=0, want=2906544057, limit=976773168
[   23.917123] attempt to access beyond end of device
[   23.917124] sda: rw=0, want=2906544058, limit=976773168
[   23.917127] attempt to access beyond end of device
[   23.917129] sda: rw=0, want=2906544059, limit=976773168
[   23.917131] attempt to access beyond end of device
[   23.917133] sda: rw=0, want=2906544060, limit=976773168
[   23.917139] attempt to access beyond end of device
[   23.917141] sda: rw=0, want=2906544056, limit=976773168
[   23.917143] attempt to access beyond end of device
[   23.917146] sda: rw=0, want=2906544057, limit=976773168
[   23.917148] attempt to access beyond end of device
[   23.917150] sda: rw=0, want=2906544058, limit=976773168
[   23.917152] attempt to access beyond end of device
[   23.917154] sda: rw=0, want=2906544059, limit=976773168
[   23.917156] attempt to access beyond end of device
[   23.917159] sda: rw=0, want=2906544060, limit=976773168
[   23.917164] attempt to access beyond end of device
[   23.917166] sda: rw=0, want=2906544056, limit=976773168
[   23.917168] attempt to access beyond end of device
[   23.917171] sda: rw=0, want=2906544057, limit=976773168
[   23.917173] attempt to access beyond end of device
[   23.917175] sda: rw=0, want=2906544058, limit=976773168
[   23.917178] attempt to access beyond end of device
[   23.917179] sda: rw=0, want=2906544059, limit=976773168
[   23.917182] attempt to access beyond end of device
[   23.917184] sda: rw=0, want=2906544060, limit=976773168
[   23.917190] attempt to access beyond end of device
[   23.917191] sda: rw=0, want=2906544056, limit=976773168
[   23.917194] attempt to access beyond end of device
[   23.917196] sda: rw=0, want=2906544057, limit=976773168
[   23.917199] attempt to access beyond end of device
[   23.917200] sda: rw=0, want=2906544058, limit=976773168
[   23.917202] attempt to access beyond end of device
[   23.917204] sda: rw=0, want=2906544059, limit=976773168
[   23.917206] attempt to access beyond end of device
[   23.917208] sda: rw=0, want=2906544060, limit=976773168
[   23.917220] attempt to access beyond end of device
[   23.917222] sda: rw=0, want=2906543992, limit=976773168
[   23.917224] attempt to access beyond end of device
[   23.917226] sda: rw=0, want=2906543993, limit=976773168
[   23.917228] attempt to access beyond end of device
[   23.917230] sda: rw=0, want=2906543994, limit=976773168
[   23.917232] attempt to access beyond end of device
[   23.917233] sda: rw=0, want=2906543995, limit=976773168
[   23.917235] attempt to access beyond end of device
[   23.917237] sda: rw=0, want=2906543996, limit=976773168
[   23.917239] attempt to access beyond end of device
[   23.917241] sda: rw=0, want=2906543997, limit=976773168
[   23.917243] attempt to access beyond end of device
[   23.917245] sda: rw=0, want=2906543998, limit=976773168
[   23.917247] attempt to access beyond end of device
[   23.917248] sda: rw=0, want=2906543999, limit=976773168
[   23.917256] attempt to access beyond end of device
[   23.917258] sda: rw=0, want=2906544048, limit=976773168
[   23.917261] attempt to access beyond end of device
[   23.917262] sda: rw=0, want=2906544049, limit=976773168
[   23.917264] attempt to access beyond end of device
[   23.917266] sda: rw=0, want=2906544050, limit=976773168
[   23.917268] attempt to access beyond end of device
[   23.917270] sda: rw=0, want=2906544051, limit=976773168
[   23.917272] attempt to access beyond end of device
[   23.917273] sda: rw=0, want=2906544052, limit=976773168
[   23.917275] attempt to access beyond end of device
[   23.917278] sda: rw=0, want=2906544053, limit=976773168
[   23.917281] attempt to access beyond end of device
[   23.917283] sda: rw=0, want=2906544054, limit=976773168
[   23.917285] attempt to access beyond end of device
[   23.917286] sda: rw=0, want=2906544055, limit=976773168
[   23.917292] attempt to access beyond end of device
[   23.917295] sda: rw=0, want=2906544056, limit=976773168
[   23.917297] attempt to access beyond end of device
[   23.917299] sda: rw=0, want=2906544057, limit=976773168
[   23.917302] attempt to access beyond end of device
[   23.917303] sda: rw=0, want=2906544058, limit=976773168
[   23.917306] attempt to access beyond end of device
[   23.917308] sda: rw=0, want=2906544059, limit=976773168
[   23.917310] attempt to access beyond end of device
[   23.917312] sda: rw=0, want=2906544060, limit=976773168
[   23.917317] attempt to access beyond end of device
[   23.917319] sda: rw=0, want=2906544056, limit=976773168
[   23.917322] attempt to access beyond end of device
[   23.917323] sda: rw=0, want=2906544057, limit=976773168
[   23.917326] attempt to access beyond end of device
[   23.917328] sda: rw=0, want=2906544058, limit=976773168
[   23.917330] attempt to access beyond end of device
[   23.917332] sda: rw=0, want=2906544059, limit=976773168
[   23.917335] attempt to access beyond end of device
[   23.917337] sda: rw=0, want=2906544060, limit=976773168
[   23.978891] attempt to access beyond end of device
[   23.978895] sda: rw=0, want=2906544062, limit=976773168
[   23.978899] attempt to access beyond end of device
[   23.978901] sda: rw=0, want=2906544062, limit=976773168
[   24.378993] Bluetooth: Core ver 2.13
[   24.379061] NET: Registered protocol family 31
[   24.379063] Bluetooth: HCI device and connection manager initialized
[   24.379067] Bluetooth: HCI socket layer initialized
[   24.399590] Bluetooth: L2CAP ver 2.11
[   24.399595] Bluetooth: L2CAP socket layer initialized
[   24.413212] Bluetooth: SCO (Voice Link) ver 0.6
[   24.413216] Bluetooth: SCO socket layer initialized
[   24.425011] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   24.425016] Bluetooth: BNEP filters: protocol multicast
[   24.453778] Bridge firewalling registered
[   24.453908] pan0: Dropping NETIF_F_UFO since no NETIF_F_HW_CSUM feature.
[   24.614476] Bluetooth: RFCOMM socket layer initialized
[   24.614887] Bluetooth: RFCOMM TTY layer initialized
[   24.614891] Bluetooth: RFCOMM ver 1.10
[   28.737208] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   28.784927] NET: Registered protocol family 17
[   39.292507] ath0: no IPv6 routers present
[   63.287113] UDF-fs: No VRS found
[   63.304129] ISO 9660 Extensions: Microsoft Joliet Level 3
[   63.323495] ISO 9660 Extensions: RRIP_1991A
[  112.216012] usb 8-1: new high speed USB device using ehci_hcd and address 5
[  112.349631] usb 8-1: configuration #1 chosen from 1 choice
[  112.394995] usbcore: registered new interface driver libusual
[  112.429022] Initializing USB Mass Storage driver...
[  112.429818] scsi8 : SCSI emulation for USB Mass Storage devices
[  112.431414] usbcore: registered new interface driver usb-storage
[  112.431418] USB Mass Storage support registered.
[  112.431466] usb-storage: device found at 5
[  112.431470] usb-storage: waiting for device to settle before scanning
[  117.428215] usb-storage: device scan complete
[  119.077199] scsi 8:0:0:0: Direct-Access     WDC      WD1200BB-55GUA0  08.0 PQ: 0 ANSI: 2
[  119.080304] sd 8:0:0:0: [sdd] 234441648 512-byte hardware sectors (120034 MB)
[  119.081675] sd 8:0:0:0: [sdd] Write Protect is off
[  119.081679] sd 8:0:0:0: [sdd] Mode Sense: 53 00 00 08
[  119.081681] sd 8:0:0:0: [sdd] Assuming drive cache: write through
[  119.083679] sd 8:0:0:0: [sdd] 234441648 512-byte hardware sectors (120034 MB)
[  119.085555] sd 8:0:0:0: [sdd] Write Protect is off
[  119.085560] sd 8:0:0:0: [sdd] Mode Sense: 53 00 00 08
[  119.085562] sd 8:0:0:0: [sdd] Assuming drive cache: write through
[  119.086845]  sdd: sdd1
[  119.093801] sd 8:0:0:0: [sdd] Attached SCSI disk
[  119.094315] sd 8:0:0:0: Attached scsi generic sg5 type 0
[  135.780018] usb 8-3: new high speed USB device using ehci_hcd and address 6
[  135.914440] usb 8-3: configuration #1 chosen from 1 choice
[  135.938990] scsi9 : SCSI emulation for USB Mass Storage devices
[  135.939191] usb-storage: device found at 6
[  135.939195] usb-storage: waiting for device to settle before scanning
[  140.936177] usb-storage: device scan complete
[  140.936904] scsi 9:0:0:0: Direct-Access     HITACHI_ DK23FA-40        A0A2 PQ: 0 ANSI: 2 CCS
[  140.939383] sd 9:0:0:0: [sde] 78140160 512-byte hardware sectors (40008 MB)
[  140.940131] sd 9:0:0:0: [sde] Write Protect is off
[  140.940135] sd 9:0:0:0: [sde] Mode Sense: 00 38 00 00
[  140.940138] sd 9:0:0:0: [sde] Assuming drive cache: write through
[  140.940756] sd 9:0:0:0: [sde] 78140160 512-byte hardware sectors (40008 MB)
[  140.941508] sd 9:0:0:0: [sde] Write Protect is off
[  140.941510] sd 9:0:0:0: [sde] Mode Sense: 00 38 00 00
[  140.941513] sd 9:0:0:0: [sde] Assuming drive cache: write through
[  140.941516]  sde: sde1 sde2 < sde5 >
[  141.795255] sd 9:0:0:0: [sde] Attached SCSI disk
[  141.796943] sd 9:0:0:0: Attached scsi generic sg6 type 0
[  142.192433] kjournald starting.  Commit interval 5 seconds
[  142.192439] EXT3-fs warning: maximal mount count reached, running e2fsck is recommended
[  142.193013] EXT3 FS on sde1, internal journal
[  142.193017] EXT3-fs: mounted filesystem with ordered data mode.
[ 2641.851270] cdrom: This disc doesn't have any tracks I recognize!
[ 2641.872951] end_request: I/O error, dev sr0, sector 0
[ 2641.872959] __ratelimit: 85 callbacks suppressed
[ 2641.872962] Buffer I/O error on device sr0, logical block 0
[ 2641.874390] end_request: I/O error, dev sr0, sector 0
[ 2641.874397] Buffer I/O error on device sr0, logical block 0
[ 2928.895130] UDF-fs: No VRS found
[ 2928.910441] ISO 9660 Extensions: Microsoft Joliet Level 3
[ 2928.923149] ISO 9660 Extensions: RRIP_1991A
[ 8267.114147] sd 9:0:0:0: [sde] Sense Key : No Sense [current] 
[ 8267.114154] sd 9:0:0:0: [sde] Add. Sense: No additional sense information
[ 8291.335240] sd 9:0:0:0: [sde] Sense Key : No Sense [current] 
[ 8291.335246] sd 9:0:0:0: [sde] Add. Sense: No additional sense information
[ 8505.944014] usb 8-3: reset high speed USB device using ehci_hcd and address 6
[ 8506.056016] usb 8-3: device descriptor read/64, error -71
[ 8506.272013] usb 8-3: device descriptor read/64, error -71
[ 8506.488512] usb 8-3: reset high speed USB device using ehci_hcd and address 6
[ 8506.600019] usb 8-3: device descriptor read/64, error -71
[ 8506.816013] usb 8-3: device descriptor read/64, error -71
[ 8507.032014] usb 8-3: reset high speed USB device using ehci_hcd and address 6
[ 8507.440008] usb 8-3: device not accepting address 6, error -71
[ 8507.552011] usb 8-3: reset high speed USB device using ehci_hcd and address 6
[ 8507.960010] usb 8-3: device not accepting address 6, error -71
[ 8507.960039] usb 8-3: USB disconnect, address 6
[ 8507.960067] sd 9:0:0:0: Device offlined - not ready after error recovery
[ 8507.960078] sd 9:0:0:0: [sde] Result: hostbyte=DID_ABORT driverbyte=DRIVER_OK,SUGGEST_OK
[ 8507.960084] end_request: I/O error, dev sde, sector 59674607
[ 8507.960089] Buffer I/O error on device sde1, logical block 7459318
[ 8507.960092] lost page write due to I/O error on sde1
[ 8507.960099] Buffer I/O error on device sde1, logical block 7459319
[ 8507.960100] lost page write due to I/O error on sde1
[ 8507.960103] Buffer I/O error on device sde1, logical block 7459320
[ 8507.960105] lost page write due to I/O error on sde1
[ 8507.960108] Buffer I/O error on device sde1, logical block 7459321
[ 8507.960111] lost page write due to I/O error on sde1
[ 8507.960114] Buffer I/O error on device sde1, logical block 7459322
[ 8507.960116] lost page write due to I/O error on sde1
[ 8507.960119] Buffer I/O error on device sde1, logical block 7459323
[ 8507.960121] lost page write due to I/O error on sde1
[ 8507.960123] Buffer I/O error on device sde1, logical block 7459324
[ 8507.960126] lost page write due to I/O error on sde1
[ 8507.960128] Buffer I/O error on device sde1, logical block 7459325
[ 8507.960130] lost page write due to I/O error on sde1
[ 8507.960133] Buffer I/O error on device sde1, logical block 7459326
[ 8507.960135] lost page write due to I/O error on sde1
[ 8507.960138] Buffer I/O error on device sde1, logical block 7459327
[ 8507.960140] lost page write due to I/O error on sde1
[ 8507.960157] sd 9:0:0:0: rejecting I/O to offline device
[ 8507.960161] sd 9:0:0:0: rejecting I/O to offline device
[ 8507.960183] sd 9:0:0:0: rejecting I/O to offline device
[ 8507.960209] sd 9:0:0:0: rejecting I/O to offline device
[ 8507.960230] sd 9:0:0:0: rejecting I/O to offline device
[ 8507.960248] sd 9:0:0:0: rejecting I/O to offline device
[ 8507.960267] sd 9:0:0:0: rejecting I/O to offline device
[ 8507.960286] sd 9:0:0:0: rejecting I/O to offline device
[ 8507.960306] sd 9:0:0:0: rejecting I/O to offline device
[ 8507.960323] sd 9:0:0:0: rejecting I/O to offline device
[ 8507.960340] sd 9:0:0:0: rejecting I/O to offline device
[ 8507.960357] sd 9:0:0:0: rejecting I/O to offline device
[ 8507.960374] sd 9:0:0:0: rejecting I/O to offline device
[ 8507.960393] sd 9:0:0:0: rejecting I/O to offline device
[ 8507.960409] sd 9:0:0:0: rejecting I/O to offline device
[ 8507.960426] sd 9:0:0:0: rejecting I/O to offline device
[ 8507.960442] sd 9:0:0:0: rejecting I/O to offline device
[ 8507.960458] sd 9:0:0:0: rejecting I/O to offline device
[ 8507.960462] sd 9:0:0:0: rejecting I/O to offline device
[ 8507.960483] sd 9:0:0:0: rejecting I/O to offline device
[ 8507.960500] sd 9:0:0:0: rejecting I/O to offline device
[ 8507.960518] sd 9:0:0:0: rejecting I/O to offline device
[ 8507.960534] sd 9:0:0:0: rejecting I/O to offline device
[ 8507.960552] sd 9:0:0:0: rejecting I/O to offline device
[ 8507.960569] sd 9:0:0:0: rejecting I/O to offline device
[ 8507.960585] sd 9:0:0:0: rejecting I/O to offline device
[ 8507.960602] sd 9:0:0:0: rejecting I/O to offline device
[ 8507.960622] sd 9:0:0:0: rejecting I/O to offline device
[ 8507.960644] sd 9:0:0:0: rejecting I/O to offline device
[ 8507.960666] sd 9:0:0:0: rejecting I/O to offline device
[ 8507.960689] sd 9:0:0:0: rejecting I/O to offline device
[ 8507.960709] sd 9:0:0:0: rejecting I/O to offline device
[ 8507.960729] sd 9:0:0:0: rejecting I/O to offline device
[ 8507.960749] sd 9:0:0:0: rejecting I/O to offline device
[ 8507.960767] sd 9:0:0:0: rejecting I/O to offline device
[ 8507.960788] sd 9:0:0:0: rejecting I/O to offline device
[ 8507.960805] sd 9:0:0:0: rejecting I/O to offline device
[ 8507.960825] sd 9:0:0:0: rejecting I/O to offline device
[ 8507.960842] sd 9:0:0:0: rejecting I/O to offline device
[ 8507.960859] sd 9:0:0:0: rejecting I/O to offline device
[ 8507.960877] sd 9:0:0:0: rejecting I/O to offline device
[ 8507.960895] sd 9:0:0:0: rejecting I/O to offline device
[ 8507.960912] sd 9:0:0:0: rejecting I/O to offline device
[ 8507.960929] sd 9:0:0:0: rejecting I/O to offline device
[ 8507.960949] sd 9:0:0:0: rejecting I/O to offline device
[ 8507.960966] sd 9:0:0:0: rejecting I/O to offline device
[ 8507.960983] sd 9:0:0:0: rejecting I/O to offline device
[ 8507.961003] sd 9:0:0:0: rejecting I/O to offline device
[ 8507.961020] sd 9:0:0:0: rejecting I/O to offline device
[ 8507.961038] sd 9:0:0:0: rejecting I/O to offline device
[ 8507.961056] sd 9:0:0:0: rejecting I/O to offline device
[ 8507.962607] sd 9:0:0:0: [sde] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK,SUGGEST_OK
[ 8507.962610] end_request: I/O error, dev sde, sector 59674847
[ 8508.025637] JBD: Detected IO errors while flushing file data on sde1
[ 8508.025738] journal_bmap: journal block not found at offset 2060 on sde1
[ 8508.025741] Aborting journal on device sde1.
[ 8508.025879] ext3_abort called.
[ 8508.025882] EXT3-fs error (device sde1): ext3_journal_start_sb: Detected aborted journal
[ 8508.025885] Remounting filesystem read-only
[ 8508.094487] JBD: Detected IO errors while flushing file data on sde1
[ 8508.094555] __journal_remove_journal_head: freeing b_committed_data
[ 8508.094565] __journal_remove_journal_head: freeing b_frozen_data
[ 8508.094570] __journal_remove_journal_head: freeing b_frozen_data
[ 8508.094573] __journal_remove_journal_head: freeing b_committed_data
[ 8508.338517] ------------[ cut here ]------------
[ 8508.338522] WARNING: at /build/buildd/linux-2.6.27/fs/buffer.c:1186 mark_buffer_dirty+0x8c/0xb0()
[ 8508.338529] Modules linked in: usb_storage libusual wlan_tkip wlan_ccmp isofs udf crc_itu_t af_packet binfmt_misc rfcomm bridge stp bnep sco l2cap bluetooth vboxnetflt vboxdrv ppdev ipv6 acpi_cpufreq cpufreq_conservative cpufreq_stats cpufreq_powersave cpufreq_ondemand cpufreq_userspace freq_table sbs pci_slot wmi container video output sbshc battery iptable_filter ip_tables x_tables ac parport_pc lp parport loop snd_hda_intel snd_pcm_oss snd_usb_audio snd_mixer_oss uvcvideo snd_usb_lib snd_pcm compat_ioctl32 serio_raw snd_hwdep videodev pcspkr snd_seq_dummy usblp v4l1_compat snd_seq_oss psmouse evdev wlan_scan_sta nvidia(P) ath_rate_sample i2c_core snd_seq_midi ath_pci snd_rawmidi wlan ath_hal(P) snd_seq_midi_event snd_seq snd_timer snd_seq_device snd soundcore intel_agp shpchp snd_page_alloc pci_hotplug button ext3 jbd mbcache sr_mod cdrom ata_generic pata_acpi sd_mod crc_t10dif sg pata_marvell ahci libata scsi_mod atl1e dock ehci_hcd uhci_hcd usbcore thermal processor fan fbcon tileblit font bitblit softcursor fuse dm_raid4_5 dm_region_hash dm_mem_cache dm_message dm_mirror dm_log dm_mod
[ 8508.338610] Pid: 7605, comm: umount Tainted: P          2.6.27-9-generic #1
[ 8508.338612] 
[ 8508.338612] Call Trace:
[ 8508.338617]  [<ffffffff8024e9b4>] warn_on_slowpath+0x64/0x90
[ 8508.338621]  [<ffffffff805006da>] ? thread_return+0x6d/0x3c3
[ 8508.338623]  [<ffffffff802475bd>] ? default_wake_function+0xd/0x10
[ 8508.338627]  [<ffffffff80267143>] ? finish_wait+0x63/0x90
[ 8508.338629]  [<ffffffff8050263e>] ? _spin_lock+0xe/0x20
[ 8508.338632]  [<ffffffff80314abc>] mark_buffer_dirty+0x8c/0xb0
[ 8508.338639]  [<ffffffffa01abc8e>] journal_update_superblock+0x8e/0xf0 [jbd]
[ 8508.338644]  [<ffffffffa01ac0eb>] journal_destroy+0xbb/0x120 [jbd]
[ 8508.338653]  [<ffffffffa01c7275>] ext3_put_super+0x35/0x230 [ext3]
[ 8508.338657]  [<ffffffff802ebcd2>] generic_shutdown_super+0x72/0x130
[ 8508.338661]  [<ffffffff802ebdaa>] kill_block_super+0x1a/0x40
[ 8508.338662]  [<ffffffff802ec10a>] deactivate_super+0x7a/0xa0
[ 8508.338666]  [<ffffffff80305e88>] mntput_no_expire+0xe8/0x160
[ 8508.338668]  [<ffffffff803065d8>] sys_umount+0x58/0xc0
[ 8508.338674]  [<ffffffff8021285a>] system_call_fastpath+0x16/0x1b
[ 8508.338676] 
[ 8508.338677] ---[ end trace f07d79ac968564dc ]---
[ 8508.364026] usb 8-3: new high speed USB device using ehci_hcd and address 7
[ 8508.480021] usb 8-3: device descriptor read/64, error -71
[ 8508.692011] usb 8-3: device descriptor read/64, error -71
[ 8508.908010] usb 8-3: new high speed USB device using ehci_hcd and address 8
[ 8509.020011] usb 8-3: device descriptor read/64, error -71
[ 8509.237518] usb 8-3: device descriptor read/64, error -71
[ 8509.452015] usb 8-3: new high speed USB device using ehci_hcd and address 9
[ 8509.860009] usb 8-3: device not accepting address 9, error -71
[ 8509.972013] usb 8-3: new high speed USB device using ehci_hcd and address 10
[ 8510.380012] usb 8-3: device not accepting address 10, error -71
[ 8510.380026] hub 8-0:1.0: unable to enumerate USB device on port 3
[ 8510.772512] usb 6-1: new full speed USB device using uhci_hcd and address 7
[ 8510.836028] hub 6-0:1.0: unable to enumerate USB device on port 1
[ 8511.256015] usb 6-1: new full speed USB device using uhci_hcd and address 8
[ 8511.320027] hub 6-0:1.0: unable to enumerate USB device on port 1
[ 8511.752012] usb 6-1: new full speed USB device using uhci_hcd and address 9
[ 8511.816030] hub 6-0:1.0: unable to enumerate USB device on port 1
[ 8512.248015] usb 6-1: new full speed USB device using uhci_hcd and address 10
[ 8512.368011] usb 6-1: device descriptor read/64, error -71
[ 8512.592012] usb 6-1: device descriptor read/64, error -71
[ 8512.808013] usb 6-1: new full speed USB device using uhci_hcd and address 11
[ 8512.928014] usb 6-1: device descriptor read/64, error -71
[ 8513.152010] usb 6-1: device descriptor read/64, error -71
[ 8513.368016] usb 6-1: new full speed USB device using uhci_hcd and address 12
[ 8513.776012] usb 6-1: device not accepting address 12, error -71
[ 8513.832027] hub 6-0:1.0: unable to enumerate USB device on port 1
[ 8514.072011] usb 6-1: new full speed USB device using uhci_hcd and address 14
[ 8514.192013] usb 6-1: device descriptor read/64, error -71
[ 8514.364028] hub 6-0:1.0: unable to enumerate USB device on port 1
[ 8514.728013] usb 6-1: new full speed USB device using uhci_hcd and address 15
[ 8514.852010] usb 6-1: device descriptor read/64, error -71
[ 8515.076011] usb 6-1: device descriptor read/64, error -71
[ 8515.293512] usb 6-1: new full speed USB device using uhci_hcd and address 16
[ 8515.416011] usb 6-1: device descriptor read/64, error -71
[ 8515.640011] usb 6-1: device descriptor read/64, error -71
[ 8515.857290] usb 6-1: new full speed USB device using uhci_hcd and address 17
[ 8516.273286] usb 6-1: device not accepting address 17, error -71
[ 8516.384010] usb 6-1: new full speed USB device using uhci_hcd and address 18
[ 8516.792009] usb 6-1: device not accepting address 18, error -71
[ 8516.792023] hub 6-0:1.0: unable to enumerate USB device on port 1

---

