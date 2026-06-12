---
title: "All usb malfunction. &quot;ehci_hcd should always be loaded before uhci_hcd and ohci_hcd,"
date: 2009-03-05
forum: Hardware
---

### Post by afeasfaerw23231233 on 2009-03-05
All usb malfunction again. 

My usb wlan card (internal) suddent didn't work and I don't want to reboot the system so I searched the forum and found this thread. [http://ubuntuforums.org/showthread.php?t=241396](http://ubuntuforums.org/showthread.php?t=241396) In the last post he said 
```

Restart USB :
sudo rmmod ehci_hcd
sudo modprobe ehci_hcd

```
I did that but my usb wlan still failed, so I rebooted the system.
But now all usb ports malfunction. lsusb never returned any result and pressing ctrl+c didn't terminate it. Reboot / power off and on again doesn't help. 
A line in dmesg says
```

[    2.402199] Warning! ehci_hcd should always be loaded before uhci_hcd and ohci_hcd, not after


```
Were these two command ```
 sudo rmmod ehci_hcd
sudo modprobe ehci_hcd 
``` I ran before causing the problem? 
How to fix it?

Here's the full dmesg ```


[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.27-11-generic (buildd@rothera) (gcc version 4.3.2 (Ubuntu 4.3.2-1ubuntu11) ) #1 SMP Thu Jan 29 19:24:39 UTC 2009 (Ubuntu 2.6.27-11.27-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009dc00 (usable)
[    0.000000]  BIOS-e820: 000000000009dc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e4000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 0000000037d90000 (usable)
[    0.000000]  BIOS-e820: 0000000037d90000 - 0000000037d9b000 (ACPI data)
[    0.000000]  BIOS-e820: 0000000037d9b000 - 0000000037d9c000 (ACPI NVS)
[    0.000000]  BIOS-e820: 0000000037d9c000 - 0000000038000000 (reserved)
[    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fff00000 - 0000000100000000 (reserved)
[    0.000000] using polling idle threads.
[    0.000000] DMI present.
[    0.000000] last_pfn = 0x37d90 max_arch_pfn = 0x100000
[    0.000000] kernel direct mapping tables up to 37d90000 @ 7000-d000
[    0.000000] RAMDISK: 375ad000 - 37d7fc43
[    0.000000] ACPI: RSDP 000F8580, 0024 (r2 PTLTD )
[    0.000000] ACPI: XSDT 37D91D00, 0094 (r1  HASEE PARADISE  6040000  LTP        0)
[    0.000000] ACPI: FACP 37D9AB86, 00F4 (r3 SiS    671MX     6040000 PTL     F4240)
[    0.000000] ACPI: DSDT 37D95D1A, 4DF8 (r1 PTLTD       671  6040000 MSFT  3000000)
[    0.000000] ACPI: FACS 37D9BFC0, 0040
[    0.000000] ACPI: APIC 37D9AC7A, 005E (r1 PTLTD  	 APIC    6040000  LTP        0)
[    0.000000] ACPI: SLIC 37D9ACD8, 0176 (r1  HASEE PARADISE  6040000  LTP        0)
[    0.000000] ACPI: MCFG 37D9AE4E, 003C (r1 PTLTD    MCFG    6040000  LTP        0)
[    0.000000] ACPI: SLIC 37D9AE8A, 0176 (r1  HASEE PARADISE  6040000  LTP        0)
[    0.000000] ACPI: SSDT 37D9363F, 025F (r1  PmRef  Cpu0Tst     3000 INTL 20050228)
[    0.000000] ACPI: SSDT 37D93599, 00A6 (r1  PmRef  Cpu7Tst     3000 INTL 20050228)
[    0.000000] ACPI: SSDT 37D934F3, 00A6 (r1  PmRef  Cpu6Tst     3000 INTL 20050228)
[    0.000000] ACPI: SSDT 37D9344D, 00A6 (r1  PmRef  Cpu5Tst     3000 INTL 20050228)
[    0.000000] ACPI: SSDT 37D933A7, 00A6 (r1  PmRef  Cpu4Tst     3000 INTL 20050228)
[    0.000000] ACPI: SSDT 37D93301, 00A6 (r1  PmRef  Cpu3Tst     3000 INTL 20050228)
[    0.000000] ACPI: SSDT 37D9325B, 00A6 (r1  PmRef  Cpu2Tst     3000 INTL 20050228)
[    0.000000] ACPI: SSDT 37D931B5, 00A6 (r1  PmRef  Cpu1Tst     3000 INTL 20050228)
[    0.000000] ACPI: SSDT 37D91D94, 1421 (r1  PmRef    CpuPm     3000 INTL 20050228)
[    0.000000] 0MB HIGHMEM available.
[    0.000000] 893MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 37d90000
[    0.000000]   low ram: 00000000 - 37d90000
[    0.000000]   bootmap 00009000 - 0000ffb4
[    0.000000] (9 early reservations) ==> bootmem [0000000000 - 0037d90000]
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000]   #1 [0000001000 - 0000002000]    EX TRAMPOLINE ==> [0000001000 - 0000002000]
[    0.000000]   #2 [0000006000 - 0000007000]       TRAMPOLINE ==> [0000006000 - 0000007000]
[    0.000000]   #3 [0000100000 - 00005c29e0]    TEXT DATA BSS ==> [0000100000 - 00005c29e0]
[    0.000000]   #4 [00375ad000 - 0037d7fc43]          RAMDISK ==> [00375ad000 - 0037d7fc43]
[    0.000000]   #5 [00005c3000 - 00005c6000]    INIT_PG_TABLE ==> [00005c3000 - 00005c6000]
[    0.000000]   #6 [000009dc00 - 0000100000]    BIOS reserved ==> [000009dc00 - 0000100000]
[    0.000000]   #7 [0000007000 - 0000009000]          PGTABLE ==> [0000007000 - 0000009000]
[    0.000000]   #8 [0000009000 - 0000010000]          BOOTMAP ==> [0000009000 - 0000010000]
[    0.000000] found SMP MP-table at [c00f85b0] 000f85b0
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000000 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x00037d90
[    0.000000]   HighMem  0x00037d90 -> 0x00037d90
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[2] active PFN ranges
[    0.000000]     0: 0x00000000 -> 0x0000009d
[    0.000000]     0: 0x00000100 -> 0x00037d90
[    0.000000] On node 0 totalpages: 228653
[    0.000000] free_area_init_node: node 0, pgdat c048c680, node_mem_map c1000000
[    0.000000]   DMA zone: 3961 pages, LIFO batch:0
[    0.000000]   Normal zone: 222681 pages, LIFO batch:31
[    0.000000] ACPI: PM-Timer IO Port: 0x8008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: Skipping IOAPIC probe due to 'noapic' option.
[    0.000000] Using ACPI for processor (LAPIC) configuration information
[    0.000000] Intel MultiProcessor Specification v1.4
[    0.000000]     Virtual Wire compatibility mode.
[    0.000000] MPTABLE: OEM ID: SiS     
[    0.000000] MPTABLE: Product ID: 671MX       
[    0.000000] MPTABLE: APIC at: 0xFEE00000
[    0.000000] I/O APIC #2 Version 20 at 0xFEC00000.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] Processors: 2
[    0.000000] SMP: Allowing 2 CPUs, 0 hotplug CPUs
[    0.000000] mapped APIC to ffffb000 (fee00000)
[    0.000000] mapped IOAPIC to ffffa000 (fec00000)
[    0.000000] PM: Registered nosave memory: 000000000009d000 - 000000000009e000
[    0.000000] PM: Registered nosave memory: 000000000009e000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e4000
[    0.000000] PM: Registered nosave memory: 00000000000e4000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 40000000 (gap: 38000000:a8000000)
[    0.000000] PERCPU: Allocating 41628 bytes of per cpu data
[    0.000000] NR_CPUS: 64, nr_cpu_ids: 2, nr_node_ids 1
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 226642
[    0.000000] Kernel command line: root=UUID=24df0199-31f4-47b6-b604-94a521ddad60 ro quiet noapic pci=assign-busses apicmaintimer idle=poll reboot=cold,hard
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] Extended CMOS year: 2000
[    0.000000] TSC: PIT calibration confirmed by PMTIMER.
[    0.000000] TSC: using PMTIMER calibration value
[    0.000000] Detected 1666.628 MHz processor.
[    0.004000] Console: colour VGA+ 80x25
[    0.004000] console [tty0] enabled
[    0.004000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.004000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.004000] Memory: 892596k/915008k available (2576k kernel code, 21892k reserved, 1165k data, 424k init, 0k highmem)
[    0.004000] virtual kernel memory layout:
[    0.004000]     fixmap  : 0xffc77000 - 0xfffff000   (3616 kB)
[    0.004000]     pkmap   : 0xff400000 - 0xff800000   (4096 kB)
[    0.004000]     vmalloc : 0xf8800000 - 0xff3fe000   ( 107 MB)
[    0.004000]     lowmem  : 0xc0000000 - 0xf7d90000   ( 893 MB)
[    0.004000]       .init : 0xc04ad000 - 0xc0517000   ( 424 kB)
[    0.004000]       .data : 0xc03840da - 0xc04a7680   (1165 kB)
[    0.004000]       .text : 0xc0100000 - 0xc03840da   (2576 kB)
[    0.004000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.004000] CPA: page pool initialized 1 of 1 pages preallocated
[    0.004000] SLUB: Genslabs=12, HWalign=64, Order=0-3, MinObjects=0, CPUs=2, Nodes=1
[    0.004011] Calibrating delay loop (skipped), value calculated using timer frequency.. 3333.25 BogoMIPS (lpj=6666512)
[    0.004030] Security Framework initialized
[    0.004036] SELinux:  Disabled at boot.
[    0.004057] AppArmor: AppArmor initialized
[    0.004065] Mount-cache hash table entries: 512
[    0.004235] Initializing cgroup subsys ns
[    0.004241] Initializing cgroup subsys cpuacct
[    0.004244] Initializing cgroup subsys memory
[    0.004260] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.004263] CPU: L2 cache: 1024K
[    0.004266] CPU: Physical Processor ID: 0
[    0.004269] CPU: Processor Core ID: 0
[    0.004277] Checking 'hlt' instruction... OK.
[    0.022267] ACPI: Core revision 20080609
[    0.025123] ACPI: Checking initramfs for custom DSDT
[    0.427646] ACPI: setting ELCR to 0800 (from 0eb8)
[    0.428104] CPU0: Intel Genuine Intel(R) CPU           T1600  @ 1.66GHz stepping 0d
[    0.432027] Booting processor 1/1 ip 6000
[    0.004000] Initializing CPU#1
[    0.004000] Calibrating delay using timer specific routine.. 3333.50 BogoMIPS (lpj=6667006)
[    0.004000] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.004000] CPU: L2 cache: 1024K
[    0.004000] CPU: Physical Processor ID: 0
[    0.004000] CPU: Processor Core ID: 1
[    0.516526] CPU1: Intel Genuine Intel(R) CPU           T1600  @ 1.66GHz stepping 0d
[    0.516547] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
[    0.520058] Brought up 2 CPUs
[    0.520061] Total of 2 processors activated (6666.75 BogoMIPS).
[    0.520079] CPU0 attaching sched-domain:
[    0.520083]  domain 0: span 0-1 level MC
[    0.520087]   groups: 0 1
[    0.520094] CPU1 attaching sched-domain:
[    0.520096]  domain 0: span 0-1 level MC
[    0.520099]   groups: 1 0
[    0.520198] net_namespace: 840 bytes
[    0.520198] Booting paravirtualized kernel on bare hardware
[    0.520356] Time: 20:35:20  Date: 03/05/09
[    0.520391] NET: Registered protocol family 16
[    0.520416] EISA bus registered
[    0.520416] ACPI: bus type pci registered
[    0.520416] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 0
[    0.520416] PCI: MCFG area at e0000000 reserved in E820
[    0.520416] PCI: Using MMCONFIG for extended config space
[    0.520416] PCI: Using configuration type 1 for base access
[    0.520892] ACPI: EC: Look up EC in DSDT
[    0.528473] ACPI: Interpreter enabled
[    0.528483] ACPI: (supports S0 S3 S4 S5)
[    0.528498] ACPI: Using PIC for interrupt routing
[    0.528558] ACPI: EC: non-query interrupt received, switching to interrupt mode
[    0.536457] ACPI: EC: GPE = 0x13, I/O: command/status = 0x66, data = 0x62
[    0.536457] ACPI: EC: driver started in interrupt mode
[    0.536457] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.536457] PCI: 0000:00:00.0 reg 10 32bit mmio: [a0000000, afffffff]
[    0.536457] PCI: 0000:00:02.5 reg 10 io port: [1f0, 1f7]
[    0.536457] PCI: 0000:00:02.5 reg 14 io port: [3f4, 3f7]
[    0.536457] PCI: 0000:00:02.5 reg 18 io port: [170, 177]
[    0.536457] PCI: 0000:00:02.5 reg 1c io port: [374, 377]
[    0.536457] PCI: 0000:00:02.5 reg 20 io port: [1080, 108f]
[    0.536457] pci 0000:00:02.5: PME# supported from D3cold
[    0.536457] pci 0000:00:02.5: PME# disabled
[    0.536457] PCI: 0000:00:03.0 reg 10 32bit mmio: [b0104000, b0104fff]
[    0.536457] PCI: 0000:00:03.1 reg 10 32bit mmio: [b0105000, b0105fff]
[    0.536457] PCI: 0000:00:03.3 reg 10 32bit mmio: [b0106000, b0106fff]
[    0.536491] pci 0000:00:03.3: PME# supported from D0 D3hot D3cold
[    0.536496] pci 0000:00:03.3: PME# disabled
[    0.536536] PCI: 0000:00:04.0 reg 10 32bit mmio: [b0307000, b030707f]
[    0.536544] PCI: 0000:00:04.0 reg 14 io port: [1000, 107f]
[    0.536586] pci 0000:00:04.0: supports D1
[    0.536588] pci 0000:00:04.0: supports D2
[    0.536591] pci 0000:00:04.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.536596] pci 0000:00:04.0: PME# disabled
[    0.536627] PCI: 0000:00:05.0 reg 10 io port: [10c8, 10cf]
[    0.536635] PCI: 0000:00:05.0 reg 14 io port: [10bc, 10bf]
[    0.536643] PCI: 0000:00:05.0 reg 18 io port: [10c0, 10c7]
[    0.536650] PCI: 0000:00:05.0 reg 1c io port: [10b8, 10bb]
[    0.536658] PCI: 0000:00:05.0 reg 20 io port: [10a0, 10af]
[    0.536686] pci 0000:00:05.0: PME# supported from D3cold
[    0.536691] pci 0000:00:05.0: PME# disabled
[    0.536736] PCI: 0000:00:0f.0 reg 10 32bit mmio: [b0100000, b0103fff]
[    0.536784] pci 0000:00:0f.0: PME# supported from D0 D3hot D3cold
[    0.536789] pci 0000:00:0f.0: PME# disabled
[    0.536858] PCI: 0000:01:00.0 reg 10 32bit mmio: [c0000000, cfffffff]
[    0.536865] PCI: 0000:01:00.0 reg 14 32bit mmio: [b0000000, b001ffff]
[    0.536872] PCI: 0000:01:00.0 reg 18 io port: [9000, 907f]
[    0.536902] pci 0000:01:00.0: supports D1
[    0.536904] pci 0000:01:00.0: supports D2
[    0.536942] PCI: bridge 0000:00:01.0 io port: [9000, 9fff]
[    0.536947] PCI: bridge 0000:00:01.0 32bit mmio: [b0000000, b00fffff]
[    0.536953] PCI: bridge 0000:00:01.0 32bit mmio pref: [c0000000, cfffffff]
[    0.536958] bus 00 -> node 0
[    0.536966] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.544814] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 7 *9 10 11)
[    0.544814] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 *5 7 9 10 11)
[    0.544814] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 *4 5 7 9 10 11)
[    0.544814] ACPI: PCI Interrupt Link [LNKD] (IRQs *3 4 5 7 9 10 11)
[    0.544814] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 7 9 10 *11)
[    0.544902] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 7 9 *10 11)
[    0.545042] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 *7 9 10 11)
[    0.545188] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 7 9 10 11) *0, disabled.
[    0.548263] Linux Plug and Play Support v0.97 (c) Adam Belay
[    0.548277] pnp: PnP ACPI init
[    0.548277] ACPI: bus type pnp registered
[    0.552302] pnp: PnP ACPI: found 10 devices
[    0.552304] ACPI: ACPI bus type pnp unregistered
[    0.552310] PnPBIOS: Disabled by ACPI PNP
[    0.552331] PCI: Using ACPI for IRQ routing
[    0.552331] NET: Registered protocol family 8
[    0.552331] NET: Registered protocol family 20
[    0.552331] NetLabel: Initializing
[    0.552331] NetLabel:  domain hash size = 128
[    0.552331] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.552331] NetLabel:  unlabeled traffic allowed by default
[    0.552639] tracer: 772 pages allocated for 65536 entries of 48 bytes
[    0.552643]    actual entries 65620
[    0.552757] AppArmor: AppArmor Filesystem Enabled
[    0.552785] system 00:04: ioport range 0x8000-0x80be has been reserved
[    0.552785] system 00:04: ioport range 0x8100-0x812f has been reserved
[    0.552785] system 00:04: ioport range 0x4d0-0x4d1 has been reserved
[    0.552785] system 00:04: ioport range 0xfe00-0xfe00 has been reserved
[    0.552785] system 00:04: ioport range 0x200-0x20f has been reserved
[    0.552785] system 00:04: ioport range 0x290-0x297 has been reserved
[    0.552785] system 00:04: iomem range 0xe0000000-0xefffffff could not be reserved
[    0.552785] system 00:04: iomem range 0xfec00000-0xfecfffff could not be reserved
[    0.552785] system 00:04: iomem range 0xfee00000-0xfeefffff could not be reserved
[    0.552785] system 00:04: iomem range 0xffb80000-0xffbfffff has been reserved
[    0.552785] system 00:04: iomem range 0xffc00000-0xffc00fff has been reserved
[    0.552785] system 00:04: iomem range 0xffe00000-0xffe00fff has been reserved
[    0.552785] system 00:04: iomem range 0xffe80000-0xffefffff has been reserved
[    0.588909] pci 0000:00:01.0: PCI bridge, secondary bus 0000:01
[    0.588914] pci 0000:00:01.0:   IO window: 0x9000-0x9fff
[    0.588921] pci 0000:00:01.0:   MEM window: 0xb0000000-0xb00fffff
[    0.588926] pci 0000:00:01.0:   PREFETCH window: 0x000000c0000000-0x000000cfffffff
[    0.588944] pci 0000:00:01.0: setting latency timer to 64
[    0.588949] bus: 00 index 0 io port: [0, ffff]
[    0.588952] bus: 00 index 1 mmio: [0, ffffffff]
[    0.588955] bus: 01 index 0 io port: [9000, 9fff]
[    0.588957] bus: 01 index 1 mmio: [b0000000, b00fffff]
[    0.588960] bus: 01 index 2 mmio: [c0000000, cfffffff]
[    0.588962] bus: 01 index 3 mmio: [0, 0]
[    0.588974] NET: Registered protocol family 2
[    0.589122] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.589426] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.590174] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.590726] TCP: Hash tables configured (established 131072 bind 65536)
[    0.590732] TCP reno registered
[    0.590970] NET: Registered protocol family 1
[    0.591160] checking if image is initramfs... it is
[    1.088607] Switched to high resolution mode on CPU 1
[    1.092065] Switched to high resolution mode on CPU 0
[    1.409629] Freeing initrd memory: 8011k freed
[    1.411072] audit: initializing netlink socket (disabled)
[    1.411110] type=2000 audit(1236285320.409:1): initialized
[    1.418188] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    1.420802] VFS: Disk quotas dquot_6.5.1
[    1.420903] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    1.421032] msgmni has been set to 1759
[    1.421186] io scheduler noop registered
[    1.421189] io scheduler anticipatory registered
[    1.421192] io scheduler deadline registered
[    1.421207] io scheduler cfq registered (default)
[    1.421275] pci 0000:01:00.0: Boot video device
[    1.421632] isapnp: Scanning for PnP cards...
[    1.775089] isapnp: No Plug & Play device found
[    1.814104] hpet_acpi_add: no address or irqs in _CRS
[    1.814176] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
[    1.816710] brd: module loaded
[    1.816798] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[    1.816947] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    1.819917] i8042.c: Detected active multiplexing controller, rev 1.1.
[    1.822837] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.822845] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[    1.822848] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[    1.822851] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[    1.822854] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[    1.823303] mice: PS/2 mouse device common for all mice
[    1.823476] rtc_cmos 00:02: rtc core: registered rtc_cmos as rtc0
[    1.823496] rtc0: alarms up to one year, y3k
[    1.823635] EISA: Probing bus 0 at eisa.0
[    1.823643] Cannot allocate resource for EISA slot 1
[    1.823669] Cannot allocate resource for EISA slot 8
[    1.823671] EISA: Detected 0 cards.
[    1.823675] cpuidle: using governor ladder
[    1.823678] cpuidle: using governor menu
[    1.824309] TCP cubic registered
[    1.824348] Using IPI No-Shortcut mode
[    1.824568] registered taskstats version 1
[    1.824674]   Magic number: 1:507:598
[    1.824742] tty ptyd2: hash matches
[    1.824851] rtc_cmos 00:02: setting system clock to 2009-03-05 20:35:21 UTC (1236285321)
[    1.824855] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.824858] EDD information not available.
[    1.825128] Freeing unused kernel memory: 424k freed
[    1.825173] Write protecting the kernel text: 2580k
[    1.825205] Write protecting the kernel read-only data: 940k
[    1.984569] fuse init (API version 7.9)
[    2.014249] ACPI: SSDT 37D9389E, 0518 (r1  PmRef  Cpu0Cst     3001 INTL 20050228)
[    2.014990] processor ACPI0007:00: registered as cooling_device0
[    2.014997] ACPI: Processor [CPU0] (supports 8 throttling states)
[    2.015657] ACPI: SSDT 37D93DB6, 0085 (r1  PmRef  Cpu1Cst     3000 INTL 20050228)
[    2.016332] processor ACPI0007:01: registered as cooling_device1
[    2.016337] ACPI: Processor [CPU1] (supports 8 throttling states)
[    2.022239] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[    2.024777] thermal LNXTHERM:01: registered as thermal_zone0
[    2.025742] ACPI: Thermal Zone [TZ01] (52 C)
[    2.356548] usbcore: registered new interface driver usbfs
[    2.356586] usbcore: registered new interface driver hub
[    2.356667] No dock devices found.
[    2.356821] usbcore: registered new device driver usb
[    2.374433] SCSI subsystem initialized
[    2.390285] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
[    2.390885] ACPI: PCI Interrupt Link [LNKE] enabled at IRQ 11
[    2.390890] PCI: setting IRQ 11 as level-triggered
[    2.390895] ohci_hcd 0000:00:03.0: PCI INT A -> Link[LNKE] -> GSI 11 (level, low) -> IRQ 11
[    2.390916] ohci_hcd 0000:00:03.0: OHCI Host Controller
[    2.391007] ohci_hcd 0000:00:03.0: new USB bus registered, assigned bus number 1
[    2.391025] ohci_hcd 0000:00:03.0: irq 11, io mem 0xb0104000
[    2.402199] Warning! ehci_hcd should always be loaded before uhci_hcd and ohci_hcd, not after
[    2.448283] usb usb1: configuration #1 chosen from 1 choice
[    2.448370] hub 1-0:1.0: USB hub found
[    2.448383] hub 1-0:1.0: 4 ports detected
[    2.448438] libata version 3.00 loaded.
[    2.552788] ACPI: PCI Interrupt Link [LNKF] enabled at IRQ 10
[    2.552795] PCI: setting IRQ 10 as level-triggered
[    2.552800] ohci_hcd 0000:00:03.1: PCI INT B -> Link[LNKF] -> GSI 10 (level, low) -> IRQ 10
[    2.552828] ohci_hcd 0000:00:03.1: OHCI Host Controller
[    2.552875] ohci_hcd 0000:00:03.1: new USB bus registered, assigned bus number 2
[    2.552904] ohci_hcd 0000:00:03.1: irq 10, io mem 0xb0105000
[    2.607340] usb usb2: configuration #1 chosen from 1 choice
[    2.607378] hub 2-0:1.0: USB hub found
[    2.607395] hub 2-0:1.0: 4 ports detected
[    2.812351] pata_sis 0000:00:02.5: version 0.5.2
[    2.812673] ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 9
[    2.812678] PCI: setting IRQ 9 as level-triggered
[    2.812683] pata_sis 0000:00:02.5: PCI INT A -> Link[LNKA] -> GSI 9 (level, low) -> IRQ 9
[    2.812827] scsi0 : pata_sis
[    2.812956] scsi1 : pata_sis
[    2.813362] ata1: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0x1080 irq 14
[    2.813366] ata2: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0x1088 irq 15
[    2.988017] usb 2-3: new full speed USB device using ohci_hcd and address 2
[    2.992258] ata1.00: ATAPI: TSSTcorp CDDVDW TS-L632H, CH01, max UDMA/33
[    3.024262] ata1.00: configured for UDMA/33
[    3.024304] ata2: port disabled. ignoring.
[    3.026792] scsi 0:0:0:0: CD-ROM            TSSTcorp CDDVDW TS-L632H  CH01 PQ: 0 ANSI: 5
[    3.027897] ACPI: PCI Interrupt Link [LNKG] enabled at IRQ 7
[    3.027902] PCI: setting IRQ 7 as level-triggered
[    3.027908] ehci_hcd 0000:00:03.3: PCI INT C -> Link[LNKG] -> GSI 7 (level, low) -> IRQ 7
[    3.027927] ehci_hcd 0000:00:03.3: EHCI Host Controller
[    3.027983] ehci_hcd 0000:00:03.3: new USB bus registered, assigned bus number 3
[    3.028038] ehci_hcd 0000:00:03.3: irq 7, io mem 0xb0106000
[    3.041063] ehci_hcd 0000:00:03.3: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    3.041266] usb usb3: configuration #1 chosen from 1 choice
[    3.041301] hub 3-0:1.0: USB hub found
[    3.041311] hub 3-0:1.0: 8 ports detected
[    3.252419] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 5
[    3.252426] PCI: setting IRQ 5 as level-triggered
[    3.252431] pata_acpi 0000:00:05.0: PCI INT A -> Link[LNKB] -> GSI 5 (level, low) -> IRQ 5
[    3.252493] pata_acpi 0000:00:05.0: PCI INT A disabled
[    3.257512] sata_sis 0000:00:05.0: version 1.0
[    3.257532] sata_sis 0000:00:05.0: PCI INT A -> Link[LNKB] -> GSI 5 (level, low) -> IRQ 5
[    3.257539] sata_sis 0000:00:05.0: Detected SiS 1183/966/966L/968/680 controller in PATA mode
[    3.258237] scsi2 : sata_sis
[    3.258329] scsi3 : sata_sis
[    3.258954] ata3: PATA max UDMA/133 cmd 0x10c8 ctl 0x10bc bmdma 0x10a0 irq 5
[    3.258958] ata4: PATA max UDMA/133 cmd 0x10c0 ctl 0x10b8 bmdma 0x10a8 irq 5
[    3.274614] scsi 0:0:0:0: Attached scsi generic sg0 type 5
[    3.288964] Driver 'sr' needs updating - please use bus_type methods
[    3.300724] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[    3.300729] Uniform CD-ROM driver Revision: 3.20
[    3.300858] sr 0:0:0:0: Attached scsi CD-ROM sr0
[    3.467814] ata3.00: ATA-8: WDC WD1600BEVT-22ZCT0, 11.01A11, max UDMA/133
[    3.467818] ata3.00: 312581808 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    3.481220] ata3.00: configured for UDMA/133
[    3.646936] scsi 2:0:0:0: Direct-Access     ATA      WDC WD1600BEVT-2 11.0 PQ: 0 ANSI: 5
[    3.647173] scsi 2:0:0:0: Attached scsi generic sg1 type 0
[    3.675108] Driver 'sd' needs updating - please use bus_type methods
[    3.675241] sd 2:0:0:0: [sda] 312581808 512-byte hardware sectors (160042 MB)
[    3.675261] sd 2:0:0:0: [sda] Write Protect is off
[    3.675264] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    3.675293] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    3.675380] sd 2:0:0:0: [sda] 312581808 512-byte hardware sectors (160042 MB)
[    3.675397] sd 2:0:0:0: [sda] Write Protect is off
[    3.675400] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    3.675430] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    3.675434]  sda: sda1 sda2 < sda5 sda6 sda7 sda8 sda9 sda10 >
[    3.763887] sd 2:0:0:0: [sda] Attached SCSI disk
[    4.240045] PM: Starting manual resume from disk
[    4.240049] PM: Resume from partition 8:10
[    4.240051] PM: Checking hibernation image.
[    4.240281] PM: Resume from disk failed.
[    4.295887] kjournald starting.  Commit interval 5 seconds
[    4.295904] EXT3-fs: mounted filesystem with ordered data mode.
[    7.988021] ohci_hcd 0000:00:03.1: Unlink after no-IRQ?  Controller is probably using the wrong IRQ.
[   10.133327] udevd version 124 started
[   10.556814] input: PC Speaker as /devices/platform/pcspkr/input/input2
[   10.724178] Linux agpgart interface v0.103
[   10.776230] agpgart-sis 0000:00:00.0: SiS chipset [1039/0671]
[   10.805895] agpgart-sis 0000:00:00.0: AGP aperture is 256M @ 0xa0000000
[   10.852205] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   10.916440] sis190 Gigabit Ethernet driver 1.2 loaded.
[   10.916730] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 3
[   10.916735] PCI: setting IRQ 3 as level-triggered
[   10.916741] sis190 0000:00:04.0: PCI INT A -> Link[LNKD] -> GSI 3 (level, low) -> IRQ 3
[   10.916755] sis190 0000:00:04.0: setting latency timer to 64
[   10.916769] 0000:00:04.0: Read MAC address from EEPROM
[   11.008029] 0000:00:04.0: Realtek PHY RTL8201 transceiver at address 1.
[   11.047798] input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input3
[   11.068056] ACPI: Power Button (FF) [PWRF]
[   11.090998] ACPI: AC Adapter [AC0] (on-line)
[   11.091217] input: Power Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input4
[   11.116051] ACPI: Power Button (CM) [PWRB]
[   11.116169] input: Sleep Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input5
[   11.148053] ACPI: Sleep Button (CM) [SLPB]
[   11.148214] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input6
[   11.161713] ACPI: Lid Switch [LID0]
[   11.169636] ACPI: Battery Slot [BAT0] (battery absent)
[   11.370906] acpi device:0f: registered as cooling_device2
[   11.371098] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A03:00/device:0c/device:0d/input/input7
[   11.388036] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[   11.552022] 0000:00:04.0: Using transceiver at address 1 as default.
[   11.584396] 0000:00:04.0: SiS 191 PCI Gigabit Ethernet adapter at f89d8000 (IRQ: 3), 00:03:0d:af:c3:b5
[   11.584400] eth0: GMII mode.
[   11.584408] eth0: Enabling Auto-negotiation.
[   11.616128] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   11.763338] Synaptics Touchpad, model: 1, fw: 6.2, id: 0x1a0b1, caps: 0xa04711/0x200000
[   11.803948] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio4/input/input8
[   11.825631] ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 4
[   11.825637] PCI: setting IRQ 4 as level-triggered
[   11.825642] HDA Intel 0000:00:0f.0: PCI INT A -> Link[LNKC] -> GSI 4 (level, low) -> IRQ 4
[   11.825679] HDA Intel 0000:00:0f.0: setting latency timer to 64
[   11.858137] hda_codec: Unknown model for ALC662, trying auto-probe from BIOS...
[   14.130620] lp: driver loaded but no devices found
[   14.332695] Adding 979924k swap on /dev/sda10.  Priority:-1 extents:1 across:979924k
[   14.780870] EXT3 FS on sda8, internal journal
[   15.862854] kjournald starting.  Commit interval 5 seconds
[   15.863097] EXT3 FS on sda6, internal journal
[   15.863104] EXT3-fs: mounted filesystem with ordered data mode.
[   15.903344] kjournald starting.  Commit interval 5 seconds
[   15.903624] EXT3 FS on sda9, internal journal
[   15.903630] EXT3-fs: mounted filesystem with ordered data mode.
[   15.942940] kjournald starting.  Commit interval 5 seconds
[   15.943235] EXT3 FS on sda7, internal journal
[   15.943240] EXT3-fs: mounted filesystem with ordered data mode.
[   16.218474] type=1505 audit(1236256536.262:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=3904
[   16.422593] type=1505 audit(1236256536.467:3): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=3909
[   16.422902] type=1505 audit(1236256536.467:4): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=3909
[   16.588492] ip_tables: (C) 2000-2006 Netfilter Core Team
[   17.497377] ACPI: WMI: Mapper loaded
[   18.341152] warning: `avahi-daemon' uses 32-bit capabilities (legacy support in use)
[   18.445658] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[   18.445668] apm: disabled - APM is not SMP safe.
[   18.626262] ppdev: user-space parallel port driver
[   20.139284] vboxdrv: Trying to deactivate the NMI watchdog permanently...
[   20.139294] vboxdrv: Successfully done.
[   20.139297] vboxdrv: Found 2 processor cores.
[   20.140768] vboxdrv: fAsync=0 offMin=0x1a4 offMax=0x1022
[   20.140778] vboxdrv: TSC mode is 'synchronous', kernel timer mode is 'normal'.
[   20.140780] vboxdrv: Successfully loaded version 2.0.4_OSE (interface 0x00090000).
[   20.295492] NET: Registered protocol family 10
[   20.296265] lo: Disabled Privacy Extensions
[   22.691129] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   27.231018] [drm] Initialized drm 1.1.0 20060810
[   27.235242] pci 0000:01:00.0: PCI INT A -> Link[LNKA] -> GSI 9 (level, low) -> IRQ 9
[   27.235258] pci 0000:01:00.0: setting latency timer to 64
[   27.237814] [drm] Initialized sis 1.3.0 20070626 on minor 0
[   27.238483] agpgart-sis 0000:00:00.0: AGP 3.5 bridge
[   27.238509] agpgart-sis 0000:00:00.0: putting AGP V3 device into 4x mode
[   27.238559] pci 0000:01:00.0: putting AGP V3 device into 4x mode
[   31.198763] hda-intel: IRQ timing workaround is activated for card #0. Suggest a bigger bdl_pos_adj.
[   32.712013] eth0: auto-negotiating...
[   42.736012] eth0: auto-negotiating...
[   51.481917] CPU0 attaching NULL sched-domain.
[   51.481930] CPU1 attaching NULL sched-domain.
[   51.482935] CPU0 attaching sched-domain:
[   51.482941]  domain 0: span 0-1 level MC
[   51.482946]   groups: 0 1
[   51.482953] CPU1 attaching sched-domain:
[   51.482956]  domain 0: span 0-1 level MC
[   51.482959]   groups: 1 0
[   52.760011] eth0: auto-negotiating...
[   62.784012] eth0: auto-negotiating...
[   72.808011] eth0: auto-negotiating...
[   76.883491] atkbd.c: Unknown key pressed (translated set 2, code 0xad on isa0060/serio0).
[   76.883499] atkbd.c: Use 'setkeycodes e02d <keycode>' to make it known.
[   76.893487] atkbd.c: Unknown key released (translated set 2, code 0xad on isa0060/serio0).
[   76.893492] atkbd.c: Use 'setkeycodes e02d <keycode>' to make it known.
[   76.923414] atkbd.c: Unknown key pressed (translated set 2, code 0xbb on isa0060/serio0).
[   76.923419] atkbd.c: Use 'setkeycodes e03b <keycode>' to make it known.
[   76.933414] atkbd.c: Unknown key released (translated set 2, code 0xbb on isa0060/serio0).
[   76.933419] atkbd.c: Use 'setkeycodes e03b <keycode>' to make it known.
[   77.023263] atkbd.c: Unknown key pressed (translated set 2, code 0xbb on isa0060/serio0).
[   77.023272] atkbd.c: Use 'setkeycodes e03b <keycode>' to make it known.
[   77.033251] atkbd.c: Unknown key released (translated set 2, code 0xbb on isa0060/serio0).
[   77.033258] atkbd.c: Use 'setkeycodes e03b <keycode>' to make it known.
[   77.083161] atkbd.c: Unknown key pressed (translated set 2, code 0xad on isa0060/serio0).
[   77.083171] atkbd.c: Use 'setkeycodes e02d <keycode>' to make it known.
[   77.093149] atkbd.c: Unknown key released (translated set 2, code 0xad on isa0060/serio0).
[   77.093154] atkbd.c: Use 'setkeycodes e02d <keycode>' to make it known.
[   82.832011] eth0: auto-negotiating...
[   92.856011] eth0: auto-negotiating...
[  102.880011] eth0: auto-negotiating...
[  112.904012] eth0: auto-negotiating...
[  122.928011] eth0: auto-negotiating...
[  132.952011] eth0: auto-negotiating...
[  136.783859] atkbd.c: Unknown key pressed (translated set 2, code 0xad on isa0060/serio0).
[  136.783866] atkbd.c: Use 'setkeycodes e02d <keycode>' to make it known.
[  136.793854] atkbd.c: Unknown key released (translated set 2, code 0xad on isa0060/serio0).
[  136.793860] atkbd.c: Use 'setkeycodes e02d <keycode>' to make it known.
[  136.823783] atkbd.c: Unknown key pressed (translated set 2, code 0xbb on isa0060/serio0).
[  136.823788] atkbd.c: Use 'setkeycodes e03b <keycode>' to make it known.
[  136.833784] atkbd.c: Unknown key released (translated set 2, code 0xbb on isa0060/serio0).
[  136.833789] atkbd.c: Use 'setkeycodes e03b <keycode>' to make it known.
[  136.923616] atkbd.c: Unknown key pressed (translated set 2, code 0xbb on isa0060/serio0).
[  136.923621] atkbd.c: Use 'setkeycodes e03b <keycode>' to make it known.
[  136.933620] atkbd.c: Unknown key released (translated set 2, code 0xbb on isa0060/serio0).
[  136.933625] atkbd.c: Use 'setkeycodes e03b <keycode>' to make it known.
[  136.983529] atkbd.c: Unknown key pressed (translated set 2, code 0xad on isa0060/serio0).
[  136.983537] atkbd.c: Use 'setkeycodes e02d <keycode>' to make it known.
[  136.993522] atkbd.c: Unknown key released (translated set 2, code 0xad on isa0060/serio0).
[  136.993528] atkbd.c: Use 'setkeycodes e02d <keycode>' to make it known.
[  142.976013] eth0: auto-negotiating...
[  153.005023] eth0: auto-negotiating...
[  163.028012] eth0: auto-negotiating...
[  173.052011] eth0: auto-negotiating...
[  183.076011] eth0: auto-negotiating...
[  193.100011] eth0: auto-negotiating... 
```
Many thanks!!

EDIT: I google around and find this bug report [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/296710](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/296710)

and I did what fishor said 

[B]1. sudo vi /etc/initramfs-tools/initramfs.conf
change MODULES=list
2. sudo lsmod | sed 's/\([[:graph:]]*\).*/\1/' >>
/etc/initramfs-tools/modules
3. sudo vi /etc/initramfs-tools/modules
remove "Module", move ehci_hcd to the first place
4. sudo update-initramfs -u

instead of complete modules list you can add only one: "ehci_hcd"[/B]
And usb works again. Problem solved.

---

