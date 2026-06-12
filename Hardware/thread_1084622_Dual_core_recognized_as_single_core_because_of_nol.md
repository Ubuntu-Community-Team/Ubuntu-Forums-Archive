---
title: "Dual core recognized as single core because of nolapic?"
date: 2009-03-02
forum: Hardware
---

### Post by afeasfaerw23231233 on 2009-03-02
SOLVED

Sorry that I made duplicated thread. I think it is the right board for my problem. 

My OS is Ubuntu 8.10 and my hardware is Celeron Dual-core T1600 and SiS 671MX chipset. 

The boot loading bar freezed and I found out adding nolapic on the kernel line of /boot/grub/menu.lst solved the problem. But now my cpu only has one core activated. Here's the extract of dmesg is as follow: 
```

[    0.000000] MPTABLE: OEM ID: SiS     
[    0.000000] MPTABLE: Product ID: 671MX       
[    0.000000] MPTABLE: APIC at: 0xFEE00000

[    0.022266] ACPI: Core revision 20080609
[    0.025121] ACPI: Checking initramfs for custom DSDT
[    0.427585] ACPI: setting ELCR to 0800 (from 0eb8)
[    0.428100] BIOS bug, local APIC #0 not detected!...
[    0.428142] ... forcing use of dummy APIC emulation.(tell your hw vendor)
[    0.428181] SMP disabled
[    0.428254] Brought up 1 CPUs
[    0.428257] Total of 1 processors activated (3333.25 BogoMIPS).
```
I searched this forum and the net as well and realized that many people having this problem are using the same chipset as mine: SiS 671MX, with a dual-core processor. So would it not be a problem of the BIOS but the compatibility issue of SiS 671MX with Linux? 

Such as this closed thread, [http://ubuntuforums.org/showthread.php?p=4890758](http://ubuntuforums.org/showthread.php?p=4890758) the OP had SiS 671MX too. 
the last post of this closed thread says his dual-core worked after adding this option **"noapic nolapic pci=assign-busses apicmaintimer idle=poll reboot=cold,hard "**
but I tried it and doesn't work for me. 

On this thread [http://ubuntuforums.org/showthread.php?t=1020157](http://ubuntuforums.org/showthread.php?t=1020157) the OP #1 post his dmesg showed that he had SiSMX too and had exactly the same error lines as mine (see the extract of my dmesg above)[although his problem was system freeze but not dual-core downgraded to single-core question, I bet his notebook was running on one core only]. And in post #14 and #15 it was mentioned that his amd dual-core cpu would have one core disable if booting with the apci / noapic / nolapic stuff. 

Here's my full dmesg (something about eth0 is cut)
 ```

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
[    0.000000] Intel MultiProcessor Specification v1.4
[    0.000000]     Virtual Wire compatibility mode.
[    0.000000] MPTABLE: OEM ID: SiS     
[    0.000000] MPTABLE: Product ID: 671MX       
[    0.000000] MPTABLE: APIC at: 0xFEE00000
[    0.000000] Processor #0 (Bootup-CPU)
[    0.000000] Processor #1
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
[    0.000000] Kernel command line: root=UUID=24df0199-31f4-47b6-b604-94a521ddad60 ro  nolapic  quiet  
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] Extended CMOS year: 2000
[    0.000000] TSC: PIT calibration confirmed by PMTIMER.
[    0.000000] TSC: using PMTIMER calibration value
[    0.000000] Detected 1666.622 MHz processor.
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
[    0.004011] Calibrating delay loop (skipped), value calculated using timer frequency.. 3333.24 BogoMIPS (lpj=6666488)
[    0.004030] Security Framework initialized
[    0.004036] SELinux:  Disabled at boot.
[    0.004057] AppArmor: AppArmor initialized
[    0.004065] Mount-cache hash table entries: 512
[    0.004237] Initializing cgroup subsys ns
[    0.004242] Initializing cgroup subsys cpuacct
[    0.004245] Initializing cgroup subsys memory
[    0.004261] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.004265] CPU: L2 cache: 1024K
[    0.004268] CPU: Physical Processor ID: 0
[    0.004270] CPU: Processor Core ID: 0
[    0.004274] using mwait in idle threads.
[    0.004281] Checking 'hlt' instruction... OK.
[    0.022269] ACPI: Core revision 20080609
[    0.025126] ACPI: Checking initramfs for custom DSDT
[    0.427658] ACPI: setting ELCR to 0800 (from 0eb8)
[    0.428100] BIOS bug, local APIC #0 not detected!...
[    0.428142] ... forcing use of dummy APIC emulation.(tell your hw vendor)
[    0.428181] SMP disabled
[    0.428255] Brought up 1 CPUs
[    0.428258] Total of 1 processors activated (3333.24 BogoMIPS).
[    0.428271] CPU0 attaching NULL sched-domain.
[    0.428540] net_namespace: 840 bytes
[    0.428564] Booting paravirtualized kernel on bare hardware
[    0.428791] Time: 19:06:58  Date: 03/02/09
[    0.428825] NET: Registered protocol family 16
[    0.429170] EISA bus registered
[    0.429192] ACPI: bus type pci registered
[    0.429324] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 0
[    0.429328] PCI: MCFG area at e0000000 reserved in E820
[    0.429330] PCI: Using MMCONFIG for extended config space
[    0.429333] PCI: Using configuration type 1 for base access
[    0.433976] ACPI: EC: Look up EC in DSDT
[    0.438634] ACPI: Interpreter enabled
[    0.438645] ACPI: (supports S0 S3 S4 S5)
[    0.438660] ACPI: Using PIC for interrupt routing
[    0.440276] ACPI: EC: non-query interrupt received, switching to interrupt mode
[    0.448097] ACPI: EC: GPE = 0x13, I/O: command/status = 0x66, data = 0x62
[    0.448100] ACPI: EC: driver started in interrupt mode
[    0.448181] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.448273] PCI: 0000:00:00.0 reg 10 32bit mmio: [a0000000, afffffff]
[    0.448438] PCI: 0000:00:02.5 reg 10 io port: [1f0, 1f7]
[    0.448446] PCI: 0000:00:02.5 reg 14 io port: [3f4, 3f7]
[    0.448454] PCI: 0000:00:02.5 reg 18 io port: [170, 177]
[    0.448462] PCI: 0000:00:02.5 reg 1c io port: [374, 377]
[    0.448469] PCI: 0000:00:02.5 reg 20 io port: [1080, 108f]
[    0.448499] pci 0000:00:02.5: PME# supported from D3cold
[    0.448505] pci 0000:00:02.5: PME# disabled
[    0.448527] PCI: 0000:00:03.0 reg 10 32bit mmio: [b0104000, b0104fff]
[    0.448583] PCI: 0000:00:03.1 reg 10 32bit mmio: [b0105000, b0105fff]
[    0.448653] PCI: 0000:00:03.3 reg 10 32bit mmio: [b0106000, b0106fff]
[    0.448700] pci 0000:00:03.3: PME# supported from D0 D3hot D3cold
[    0.448705] pci 0000:00:03.3: PME# disabled
[    0.448742] PCI: 0000:00:04.0 reg 10 32bit mmio: [b0307000, b030707f]
[    0.448750] PCI: 0000:00:04.0 reg 14 io port: [1000, 107f]
[    0.448793] pci 0000:00:04.0: supports D1
[    0.448795] pci 0000:00:04.0: supports D2
[    0.448797] pci 0000:00:04.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.448802] pci 0000:00:04.0: PME# disabled
[    0.448834] PCI: 0000:00:05.0 reg 10 io port: [10c8, 10cf]
[    0.448842] PCI: 0000:00:05.0 reg 14 io port: [10bc, 10bf]
[    0.448850] PCI: 0000:00:05.0 reg 18 io port: [10c0, 10c7]
[    0.448858] PCI: 0000:00:05.0 reg 1c io port: [10b8, 10bb]
[    0.448866] PCI: 0000:00:05.0 reg 20 io port: [10a0, 10af]
[    0.448894] pci 0000:00:05.0: PME# supported from D3cold
[    0.448899] pci 0000:00:05.0: PME# disabled
[    0.448946] PCI: 0000:00:0f.0 reg 10 32bit mmio: [b0100000, b0103fff]
[    0.448994] pci 0000:00:0f.0: PME# supported from D0 D3hot D3cold
[    0.448999] pci 0000:00:0f.0: PME# disabled
[    0.449059] PCI: 0000:01:00.0 reg 10 32bit mmio: [c0000000, cfffffff]
[    0.449066] PCI: 0000:01:00.0 reg 14 32bit mmio: [b0000000, b001ffff]
[    0.449073] PCI: 0000:01:00.0 reg 18 io port: [9000, 907f]
[    0.449104] pci 0000:01:00.0: supports D1
[    0.449106] pci 0000:01:00.0: supports D2
[    0.449144] PCI: bridge 0000:00:01.0 io port: [9000, 9fff]
[    0.449149] PCI: bridge 0000:00:01.0 32bit mmio: [b0000000, b00fffff]
[    0.449154] PCI: bridge 0000:00:01.0 32bit mmio pref: [c0000000, cfffffff]
[    0.449164] bus 00 -> node 0
[    0.449171] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.458190] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 7 *9 10 11)
[    0.458335] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 *5 7 9 10 11)
[    0.458477] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 *4 5 7 9 10 11)
[    0.458618] ACPI: PCI Interrupt Link [LNKD] (IRQs *3 4 5 7 9 10 11)
[    0.458788] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 7 9 10 *11)
[    0.458930] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 7 9 *10 11)
[    0.459071] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 *7 9 10 11)
[    0.459211] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 7 9 10 11) *0, disabled.
[    0.459657] Linux Plug and Play Support v0.97 (c) Adam Belay
[    0.459701] pnp: PnP ACPI init
[    0.459714] ACPI: bus type pnp registered
[    0.462171] pnp 00:05: IRQ 13 override to level, low
[    0.462175] PCI: setting IRQ 13 as level-triggered
[    0.462381] pnp 00:07: IRQ 12 override to level, low
[    0.462384] PCI: setting IRQ 12 as level-triggered
[    0.463212] pnp: PnP ACPI: found 10 devices
[    0.463215] ACPI: ACPI bus type pnp unregistered
[    0.463221] PnPBIOS: Disabled by ACPI PNP
[    0.464288] PCI: Using ACPI for IRQ routing
[    0.464418] NET: Registered protocol family 8
[    0.464418] NET: Registered protocol family 20
[    0.464418] NetLabel: Initializing
[    0.464418] NetLabel:  domain hash size = 128
[    0.464418] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.464418] NetLabel:  unlabeled traffic allowed by default
[    0.464418] tracer: 772 pages allocated for 65536 entries of 48 bytes
[    0.464422]    actual entries 65620
[    0.464548] AppArmor: AppArmor Filesystem Enabled
[    0.464575] system 00:04: ioport range 0x8000-0x80be has been reserved
[    0.464575] system 00:04: ioport range 0x8100-0x812f has been reserved
[    0.464575] system 00:04: ioport range 0x4d0-0x4d1 has been reserved
[    0.464575] system 00:04: ioport range 0xfe00-0xfe00 has been reserved
[    0.464575] system 00:04: ioport range 0x200-0x20f has been reserved
[    0.464575] system 00:04: ioport range 0x290-0x297 has been reserved
[    0.464575] system 00:04: iomem range 0xe0000000-0xefffffff could not be reserved
[    0.464575] system 00:04: iomem range 0xfec00000-0xfecfffff could not be reserved
[    0.464575] system 00:04: iomem range 0xfee00000-0xfeefffff could not be reserved
[    0.464575] system 00:04: iomem range 0xffb80000-0xffbfffff has been reserved
[    0.464575] system 00:04: iomem range 0xffc00000-0xffc00fff has been reserved
[    0.464575] system 00:04: iomem range 0xffe00000-0xffe00fff has been reserved
[    0.464575] system 00:04: iomem range 0xffe80000-0xffefffff has been reserved
[    0.500227] pci 0000:00:01.0: PCI bridge, secondary bus 0000:01
[    0.500232] pci 0000:00:01.0:   IO window: 0x9000-0x9fff
[    0.500239] pci 0000:00:01.0:   MEM window: 0xb0000000-0xb00fffff
[    0.500245] pci 0000:00:01.0:   PREFETCH window: 0x000000c0000000-0x000000cfffffff
[    0.500263] pci 0000:00:01.0: setting latency timer to 64
[    0.500267] bus: 00 index 0 io port: [0, ffff]
[    0.500270] bus: 00 index 1 mmio: [0, ffffffff]
[    0.500273] bus: 01 index 0 io port: [9000, 9fff]
[    0.500275] bus: 01 index 1 mmio: [b0000000, b00fffff]
[    0.500278] bus: 01 index 2 mmio: [c0000000, cfffffff]
[    0.500280] bus: 01 index 3 mmio: [0, 0]
[    0.500292] NET: Registered protocol family 2
[    0.500448] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.500755] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.501544] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.502093] TCP: Hash tables configured (established 131072 bind 65536)
[    0.502098] TCP reno registered
[    0.502313] NET: Registered protocol family 1
[    0.502483] checking if image is initramfs... it is
[    1.004088] Switched to high resolution mode on CPU 0
[    1.322785] Freeing initrd memory: 8011k freed
[    1.323667] audit: initializing netlink socket (disabled)
[    1.323695] type=2000 audit(1236020818.320:1): initialized
[    1.330773] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    1.333460] VFS: Disk quotas dquot_6.5.1
[    1.333570] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    1.333701] msgmni has been set to 1759
[    1.333849] io scheduler noop registered
[    1.333853] io scheduler anticipatory registered
[    1.333856] io scheduler deadline registered
[    1.333871] io scheduler cfq registered (default)
[    1.333928] pci 0000:01:00.0: Boot video device
[    1.334312] isapnp: Scanning for PnP cards...
[    1.687884] isapnp: No Plug & Play device found
[    1.728199] hpet_acpi_add: no address or irqs in _CRS
[    1.728276] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
[    1.730854] brd: module loaded
[    1.730944] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[    1.731113] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    1.736379] i8042.c: Detected active multiplexing controller, rev 1.1.
[    1.739293] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.739300] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[    1.739303] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[    1.739306] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[    1.739309] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[    1.739816] mice: PS/2 mouse device common for all mice
[    1.739984] rtc_cmos 00:02: rtc core: registered rtc_cmos as rtc0
[    1.740003] rtc0: alarms up to one year, y3k
[    1.740156] EISA: Probing bus 0 at eisa.0
[    1.740164] Cannot allocate resource for EISA slot 1
[    1.740189] Cannot allocate resource for EISA slot 8
[    1.740191] EISA: Detected 0 cards.
[    1.740195] cpuidle: using governor ladder
[    1.740199] cpuidle: using governor menu
[    1.740829] TCP cubic registered
[    1.740865] Using IPI No-Shortcut mode
[    1.741096] registered taskstats version 1
[    1.741198]   Magic number: 1:211:141
[    1.741206] block ram6: hash matches
[    1.741345] acpi device:12: hash matches
[    1.741389] rtc_cmos 00:02: setting system clock to 2009-03-02 19:06:59 UTC (1236020819)
[    1.741392] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.741395] EDD information not available.
[    1.741667] Freeing unused kernel memory: 424k freed
[    1.741709] Write protecting the kernel text: 2580k
[    1.741739] Write protecting the kernel read-only data: 940k
[    1.776816] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[    1.889091] fuse init (API version 7.9)
[    1.918825] ACPI: SSDT 37D9389E, 0518 (r1  PmRef  Cpu0Cst     3001 INTL 20050228)
[    1.919558] Monitor-Mwait will be used to enter C-1 state
[    1.919562] Monitor-Mwait will be used to enter C-2 state
[    1.919566] Monitor-Mwait will be used to enter C-3 state
[    1.919839] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[    1.919912] processor ACPI0007:00: registered as cooling_device0
[    1.919918] ACPI: Processor [CPU0] (supports 8 throttling states)
[    1.925254] Marking TSC unstable due to TSC halts in idle
[    1.926121] thermal LNXTHERM:01: registered as thermal_zone0
[    1.928981] ACPI: Thermal Zone [TZ01] (45 C)
[    2.464234] No dock devices found.
[    2.518661] SCSI subsystem initialized
[    2.602882] libata version 3.00 loaded.
[    2.616367] usbcore: registered new interface driver usbfs
[    2.616401] usbcore: registered new interface driver hub
[    2.626437] pata_sis 0000:00:02.5: version 0.5.2
[    2.626749] ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 9
[    2.626753] PCI: setting IRQ 9 as level-triggered
[    2.626758] pata_sis 0000:00:02.5: PCI INT A -> Link[LNKA] -> GSI 9 (level, low) -> IRQ 9
[    2.636139] usbcore: registered new device driver usb
[    2.660071] scsi0 : pata_sis
[    2.674301] scsi1 : pata_sis
[    2.674748] ata1: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0x1080 irq 14
[    2.674752] ata2: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0x1088 irq 15
[    2.677301] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
[    2.852404] ata1.00: ATAPI: TSSTcorp CDDVDW TS-L632H, CH01, max UDMA/33
[    2.884334] ata1.00: configured for UDMA/33
[    2.884389] ata2: port disabled. ignoring.
[    2.888101] scsi 0:0:0:0: CD-ROM            TSSTcorp CDDVDW TS-L632H  CH01 PQ: 0 ANSI: 5
[    2.888582] ACPI: PCI Interrupt Link [LNKE] enabled at IRQ 11
[    2.888586] PCI: setting IRQ 11 as level-triggered
[    2.888590] ohci_hcd 0000:00:03.0: PCI INT A -> Link[LNKE] -> GSI 11 (level, low) -> IRQ 11
[    2.888611] ohci_hcd 0000:00:03.0: OHCI Host Controller
[    2.888668] ohci_hcd 0000:00:03.0: new USB bus registered, assigned bus number 1
[    2.888687] ohci_hcd 0000:00:03.0: irq 11, io mem 0xb0104000
[    2.944284] usb usb1: configuration #1 chosen from 1 choice
[    2.944320] hub 1-0:1.0: USB hub found
[    2.944331] hub 1-0:1.0: 4 ports detected
[    3.152703] ACPI: PCI Interrupt Link [LNKF] enabled at IRQ 10
[    3.152708] PCI: setting IRQ 10 as level-triggered
[    3.152713] ohci_hcd 0000:00:03.1: PCI INT B -> Link[LNKF] -> GSI 10 (level, low) -> IRQ 10
[    3.152734] ohci_hcd 0000:00:03.1: OHCI Host Controller
[    3.152768] ohci_hcd 0000:00:03.1: new USB bus registered, assigned bus number 2
[    3.152787] ohci_hcd 0000:00:03.1: irq 10, io mem 0xb0105000
[    3.210226] usb usb2: configuration #1 chosen from 1 choice
[    3.210262] hub 2-0:1.0: USB hub found
[    3.210273] hub 2-0:1.0: 4 ports detected
[    3.328079] usb 1-1: new full speed USB device using ohci_hcd and address 2
[    3.417674] ACPI: PCI Interrupt Link [LNKG] enabled at IRQ 7
[    3.417678] PCI: setting IRQ 7 as level-triggered
[    3.417683] ehci_hcd 0000:00:03.3: PCI INT C -> Link[LNKG] -> GSI 7 (level, low) -> IRQ 7
[    3.417700] ehci_hcd 0000:00:03.3: EHCI Host Controller
[    3.417742] ehci_hcd 0000:00:03.3: new USB bus registered, assigned bus number 3
[    3.417785] ehci_hcd 0000:00:03.3: irq 7, io mem 0xb0106000
[    3.516072] ehci_hcd 0000:00:03.3: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    3.516261] usb usb3: configuration #1 chosen from 1 choice
[    3.516294] hub 3-0:1.0: USB hub found
[    3.516303] hub 3-0:1.0: 8 ports detected
[    3.731265] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 5
[    3.731269] PCI: setting IRQ 5 as level-triggered
[    3.731274] pata_acpi 0000:00:05.0: PCI INT A -> Link[LNKB] -> GSI 5 (level, low) -> IRQ 5
[    3.731323] pata_acpi 0000:00:05.0: PCI INT A disabled
[    3.735969] sata_sis 0000:00:05.0: version 1.0
[    3.735988] sata_sis 0000:00:05.0: PCI INT A -> Link[LNKB] -> GSI 5 (level, low) -> IRQ 5
[    3.735994] sata_sis 0000:00:05.0: Detected SiS 1183/966/966L/968/680 controller in PATA mode
[    3.743242] scsi2 : sata_sis
[    3.746912] scsi 0:0:0:0: Attached scsi generic sg0 type 5
[    3.748176] scsi3 : sata_sis
[    3.748829] ata3: PATA max UDMA/133 cmd 0x10c8 ctl 0x10bc bmdma 0x10a0 irq 5
[    3.748833] ata4: PATA max UDMA/133 cmd 0x10c0 ctl 0x10b8 bmdma 0x10a8 irq 5
[    3.793030] Driver 'sr' needs updating - please use bus_type methods
[    3.807519] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[    3.807526] Uniform CD-ROM driver Revision: 3.20
[    3.807653] sr 0:0:0:0: Attached scsi CD-ROM sr0
[    3.912310] usb 1-1: device not accepting address 2, error -62
[    3.960203] ata3.00: ATA-8: WDC WD1600BEVT-22ZCT0, 11.01A11, max UDMA/133
[    3.960207] ata3.00: 312581808 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    3.968189] hub 1-0:1.0: unable to enumerate USB device on port 1
[    3.976926] ata3.00: configured for UDMA/133
[    4.142956] scsi 2:0:0:0: Direct-Access     ATA      WDC WD1600BEVT-2 11.0 PQ: 0 ANSI: 5
[    4.143157] scsi 2:0:0:0: Attached scsi generic sg1 type 0
[    4.182103] Driver 'sd' needs updating - please use bus_type methods
[    4.182234] sd 2:0:0:0: [sda] 312581808 512-byte hardware sectors (160042 MB)
[    4.182253] sd 2:0:0:0: [sda] Write Protect is off
[    4.182257] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    4.182286] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.182366] sd 2:0:0:0: [sda] 312581808 512-byte hardware sectors (160042 MB)
[    4.182384] sd 2:0:0:0: [sda] Write Protect is off
[    4.182387] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    4.182416] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.182420]  sda: sda1 sda2 < sda5 sda6 sda7 sda8 sda9 sda10 >
[    4.268491] sd 2:0:0:0: [sda] Attached SCSI disk
[    4.464084] usb 3-1: new high speed USB device using ehci_hcd and address 2
[    4.603738] usb 3-1: configuration #1 chosen from 1 choice
[    4.686115] PM: Starting manual resume from disk
[    4.686120] PM: Resume from partition 8:10
[    4.686122] PM: Checking hibernation image.
[    4.686348] PM: Resume from disk failed.
[    4.732642] kjournald starting.  Commit interval 5 seconds
[    4.732661] EXT3-fs: mounted filesystem with ordered data mode.
[    4.776083] usb 3-6: new high speed USB device using ehci_hcd and address 4
[    5.463740] usb 3-6: configuration #1 chosen from 1 choice
[    5.768082] usb 1-3: new low speed USB device using ohci_hcd and address 4
[    5.979306] usb 1-3: configuration #1 chosen from 1 choice
[   10.258737] udevd version 124 started
[   10.810163] Linux agpgart interface v0.103
[   10.868831] agpgart-sis 0000:00:00.0: SiS chipset [1039/0671]
[   10.888164] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   11.028221] agpgart-sis 0000:00:00.0: AGP aperture is 256M @ 0xa0000000
[   11.028336] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   11.112240] sis190 Gigabit Ethernet driver 1.2 loaded.
[   11.112521] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 3
[   11.112525] PCI: setting IRQ 3 as level-triggered
[   11.112530] sis190 0000:00:04.0: PCI INT A -> Link[LNKD] -> GSI 3 (level, low) -> IRQ 3
[   11.112543] sis190 0000:00:04.0: setting latency timer to 64
[   11.112555] 0000:00:04.0: Read MAC address from EEPROM
[   11.200038] 0000:00:04.0: Realtek PHY RTL8201 transceiver at address 1.
[   11.480330] input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input2
[   11.492060] ACPI: Power Button (FF) [PWRF]
[   11.492264] input: Power Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input3
[   11.508036] ACPI: Power Button (CM) [PWRB]
[   11.508198] input: Sleep Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input4
[   11.524047] ACPI: Sleep Button (CM) [SLPB]
[   11.524184] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input5
[   11.524614] ACPI: Lid Switch [LID0]
[   11.525142] ACPI: AC Adapter [AC0] (on-line)
[   11.562523] ACPI: Battery Slot [BAT0] (battery absent)
[   11.712038] 0000:00:04.0: Using transceiver at address 1 as default.
[   11.744472] 0000:00:04.0: SiS 191 PCI Gigabit Ethernet adapter at f8888000 (IRQ: 3), 00:03:0d:af:c3:b5
[   11.744476] eth0: GMII mode.
[   11.744483] eth0: Enabling Auto-negotiation.
[   12.229546] acpi device:0f: registered as cooling_device1
[   12.229727] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A03:00/device:0c/device:0d/input/input6
[   12.240058] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[   12.708460] ndiswrapper version 1.53 loaded (smp=yes, preempt=no)
[   12.948070] usb 3-1: reset high speed USB device using ehci_hcd and address 2
[   13.095541] input: PC Speaker as /devices/platform/pcspkr/input/input7
[   13.110055] ndiswrapper: driver netrtuw (Realtek Semiconductor Corp.,06/13/2008,5.1313.0613.2008) loaded
[   14.117715] ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 4
[   14.117720] PCI: setting IRQ 4 as level-triggered
[   14.117725] HDA Intel 0000:00:0f.0: PCI INT A -> Link[LNKC] -> GSI 4 (level, low) -> IRQ 4
[   14.117755] HDA Intel 0000:00:0f.0: setting latency timer to 64
[   14.149968] hda_codec: Unknown model for ALC662, trying auto-probe from BIOS...
[   14.245252] Synaptics Touchpad, model: 1, fw: 6.2, id: 0x1a0b1, caps: 0xa04711/0x200000
[   14.284697] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio4/input/input8
[   16.784619] wlan0: ethernet device 00:22:43:74:7b:05 using NDIS driver: netrtuw, version: 0x1, NDIS version: 0x500, vendor: 'NDIS Network Adapter', 0BDA:8187.F.conf
[   16.784668] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK
[   16.787850] usbcore: registered new interface driver ndiswrapper
[   16.788408] usbcore: registered new interface driver hiddev
[   16.788454] usbcore: registered new interface driver libusual
[   16.795521] input: USB Optical Mouse as /devices/pci0000:00/0000:00:03.0/usb1/1-3/1-3:1.0/input/input9
[   16.814843] input,hiddev96,hidraw0: USB HID v1.10 Mouse [USB Optical Mouse] on usb-0000:00:03.0-3
[   16.814878] usbcore: registered new interface driver usbhid
[   16.814926] usbhid: v2.6:USB HID core driver
[   16.824459] Initializing USB Mass Storage driver...
[   16.826980] scsi4 : SCSI emulation for USB Mass Storage devices
[   16.827151] usbcore: registered new interface driver usb-storage
[   16.827157] USB Mass Storage support registered.
[   16.827346] usb-storage: device found at 4
[   16.827349] usb-storage: waiting for device to settle before scanning
[   17.236578] lp: driver loaded but no devices found
[   17.504532] Adding 979924k swap on /dev/sda10.  Priority:-1 extents:1 across:979924k
[   17.975156] EXT3 FS on sda8, internal journal
[   19.079174] kjournald starting.  Commit interval 5 seconds
[   19.079471] EXT3 FS on sda6, internal journal
[   19.079477] EXT3-fs: mounted filesystem with ordered data mode.
[   19.134588] kjournald starting.  Commit interval 5 seconds
[   19.134918] EXT3 FS on sda9, internal journal
[   19.134924] EXT3-fs: mounted filesystem with ordered data mode.
[   19.170412] kjournald starting.  Commit interval 5 seconds
[   19.170683] EXT3 FS on sda7, internal journal
[   19.170689] EXT3-fs: mounted filesystem with ordered data mode.
[   19.458210] type=1505 audit(1235992037.364:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=3907
[   19.663122] type=1505 audit(1235992037.568:3): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=3912
[   19.663435] type=1505 audit(1235992037.568:4): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=3912
[   19.793344] ip_tables: (C) 2000-2006 Netfilter Core Team
[   21.076490] NET: Registered protocol family 17
[   21.824285] usb-storage: device scan complete
[   21.830656] scsi 4:0:0:0: Direct-Access     Generic- Multi-Card       1.00 PQ: 0 ANSI: 0 CCS
[   21.836721] sd 4:0:0:0: [sdb] Attached SCSI removable disk
[   21.836868] sd 4:0:0:0: Attached scsi generic sg2 type 0
[   35.644887] NET: Registered protocol family 10
[   35.645494] lo: Disabled Privacy Extensions
[   36.294113] wlan0: duplicate address detected!
[   36.414773] ACPI: WMI: Mapper loaded
[   37.267707] warning: `avahi-daemon' uses 32-bit capabilities (legacy support in use)
[   37.349718] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[   37.349725] apm: overridden by ACPI.
[   37.531285] ppdev: user-space parallel port driver
[   39.000808] vboxdrv: Trying to deactivate the NMI watchdog permanently...
[   39.000815] vboxdrv: Successfully done.
[   39.000818] vboxdrv: Found 1 processor cores.
[   39.002648] vboxdrv: TSC mode is 'synchronous', kernel timer mode is 'normal'.
[   39.002656] vboxdrv: Successfully loaded version 2.0.4_OSE (interface 0x00090000).
[   44.439339] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   46.338883] [drm] Initialized drm 1.1.0 20060810
[   46.344589] pci 0000:01:00.0: PCI INT A -> Link[LNKA] -> GSI 9 (level, low) -> IRQ 9
[   46.344601] pci 0000:01:00.0: setting latency timer to 64
[   46.346317] [drm] Initialized sis 1.3.0 20070626 on minor 0
[   46.347590] agpgart-sis 0000:00:00.0: AGP 3.5 bridge
[   46.347620] agpgart-sis 0000:00:00.0: putting AGP V3 device into 4x mode
[   46.347670] pci 0000:01:00.0: putting AGP V3 device into 4x mode
[   50.812758] hda-intel: IRQ timing workaround is activated for card #0. Suggest a bigger bdl_pos_adj.
[   70.814444] CPU0 attaching NULL sched-domain.
[   70.815092] CPU0 attaching NULL sched-domain. 
```

Here's my /boot/grub/menu.lst
```

title		Ubuntu 8.10, kernel 2.6.27-11-generic
uuid		25053297-13ad-4ad2-8e86-e4bb594c5f7d
kernel		/vmlinuz-2.6.27-11-generic root=UUID=24df0199-31f4-47b6-b604-94a521ddad60 ro quiet  acpi=on nolapic  
initrd		/initrd.img-2.6.27-11-generic

```

Here's my /proc/cpuinfo
```

processor	: 0
vendor_id	: GenuineIntel
cpu family	: 6
model		: 15
model name	: Genuine Intel(R) CPU           T1600  @ 1.66GHz
stepping	: 13
cpu MHz		: 1666.622
cache size	: 1024 KB
physical id	: 0
siblings	: 1
core id		: 0
cpu cores	: 1
apicid		: 0
initial apicid	: 0
fdiv_bug	: no
hlt_bug		: no
f00f_bug	: no
coma_bug	: no
fpu		: yes
fpu_exception	: yes
cpuid level	: 10
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm constant_tsc arch_perfmon pebs bts pni monitor ds_cpl tm2 ssse3 cx16 xtpr lahf_lm
bogomips	: 3333.24
clflush size	: 64
power management:



```


Here's my lshw
```

 *-cpu
          product: Genuine Intel(R) CPU           T1600  @ 1.66GHz
          vendor: Intel Corp.
          physical id: 1
          bus info: cpu@0
          version: 6.15.13
          serial: 0000-06FD-0000-0000-0000-0000
          size: 1700MHz
          width: 64 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx x86-64 constant_tsc arch_perfmon pebs bts pni monitor ds_cpl tm2 ssse3 cx16 xtpr lahf_lm
          configuration: id=0
        *-logicalcpu:0
             description: Logical CPU
             physical id: 0.1
             width: 64 bits
             capabilities: logical
        *-logicalcpu:1
             description: Logical CPU
             physical id: 0.2
             width: 64 bits
             capabilities: logical

```

Many thanks for any help!

Update: from wikipedia [http://en.wikipedia.org/wiki/Intel_APIC_Architecture](http://en.wikipedia.org/wiki/Intel_APIC_Architecture) it said apic is needed to keep SMP running well. Now I suspect if it is the "nolapic" causing the second core fail to work. If you [google with [nolapic "one core"] ]("http://www.google.com/search?ie=UTF-8&oe=UTF-8&sourceid=navclient&gfns=1&q=nolapic+%22one+core%22") then there are bunches of reports complaining about this issue. 
But without "nolapic" ubuntu fails to boot! What can I do? Poor Celeron only has one core working!

**Update:** I finally get both core working. I added these options to the kernel line in /boot/grub/menu.lst 
**noapic pci=assign-busses apicmaintimer idle=poll reboot=cold,hard** 
And two cores were brought up. 

Hope it may help anyone who has an SiS 671MX with a dual-core cpu. 

Here's the extract of my /boot/grub/menu.lst
```
title		Ubuntu 8.10, kernel 2.6.27-11-generic
uuid		25053297-13ad-4ad2-8e86-e4bb594c5f7d
kernel		/vmlinuz-2.6.27-11-generic root=UUID=24df0199-31f4-47b6-b604-94a521ddad60 ro quiet noapic pci=assign-busses apicmaintimer idle=poll reboot=cold,hard
initrd		/initrd.img-2.6.27-11-generic

```

---

### Post by weboide on 2011-02-01
That solved it for me! Thanks a lot!

I have a Dell Optiplex 760 with a Dual Core 2 Duo 7200.

---

### Post by IPEX-731BA5DD06 on 2012-02-16
Yeah, it worked for me as well, and I have a Pentium 4 3 Ghz so couple down on your's but still dual core. 

I know have both cores back. Thanks very much, it did indeed help me.

P.S. Using Kernal 3.0.0.15-17 pae and Ubuntue Oneiric 11.10 (and precise 12.04 Alpha 2) Yeah so happy now

---

### Post by overdrank on 2012-02-17
Back to sleep thread, thread closed.

---

