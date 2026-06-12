---
title: "Sandisk 6-in-1 PCMCIA card reader not working under Ubuntu 8.10"
date: 2009-03-11
forum: Hardware
---

### Post by softbomb on 2009-03-11
Hi, I've just bought this card reader and tried to use it with a Kingston 1Gb SD card, but the card doesn't appear on the desktop as I might have expected. The laptop is an IBM ThinkPad R50e.

pccardctl ident gives this output:

Socket 0:
  product info: "             ", "Memory Card Adapter II", "V1.00", ""
  manfid: 0x0045, 0x0401
  function: 4 (fixed disk)

Not at all sure where I should go next with this? All suggestions gratefully received!

---

### Post by softbomb on 2009-03-13
Output of dmesg:

```
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.27-11-generic (buildd@rothera) (gcc version 4.3.2 (Ubuntu 4.3.2-1ubuntu11) ) #1 SMP Thu Jan 29 19:24:39 UTC 2009 (Ubuntu 2.6.27-11.27-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f000 (usable)
[    0.000000]  BIOS-e820: 000000000009f000 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000dc000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000002f6e0000 (usable)
[    0.000000]  BIOS-e820: 000000002f6e0000 - 000000002f6f7000 (ACPI data)
[    0.000000]  BIOS-e820: 000000002f6f7000 - 000000002f6f9000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000002f700000 - 0000000030000000 (reserved)
[    0.000000]  BIOS-e820: 00000000ff800000 - 0000000100000000 (reserved)
[    0.000000] DMI present.
[    0.000000] last_pfn = 0x2f6e0 max_arch_pfn = 0x100000
[    0.000000] kernel direct mapping tables up to 2f6e0000 @ 7000-d000
[    0.000000] RAMDISK: 2ef02000 - 2f6cf80c
[    0.000000] ACPI: RSDP 000F6EC0, 0024 (r2 IBM   )
[    0.000000] ACPI: XSDT 2F6EF33D, 004C (r1 IBM    TP-1W        2020  LTP        0)
[    0.000000] ACPI: FACP 2F6EF400, 00F4 (r3 IBM    TP-1W        2020 IBM         1)
[    0.000000] ACPI Warning (tbfadt-0442): Optional field "Gpe1Block" has zero address or length: 000000000000102C/0 [20080609]
[    0.000000] ACPI: DSDT 2F6EF5E7, 7865 (r1 IBM    TP-1W        2020 MSFT  100000E)
[    0.000000] ACPI: FACS 2F6F8000, 0040
[    0.000000] ACPI: SSDT 2F6EF5B4, 0033 (r1 IBM    TP-1W        2020 MSFT  100000E)
[    0.000000] ACPI: ECDT 2F6F6E4C, 0052 (r1 IBM    TP-1W        2020 IBM         1)
[    0.000000] ACPI: TCPA 2F6F6E9E, 0032 (r1 IBM    TP-1W        2020 PTL         1)
[    0.000000] ACPI: BOOT 2F6F6FD8, 0028 (r1 IBM    TP-1W        2020  LTP        1)
[    0.000000] 0MB HIGHMEM available.
[    0.000000] 758MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 2f6e0000
[    0.000000]   low ram: 00000000 - 2f6e0000
[    0.000000]   bootmap 00009000 - 0000eedc
[    0.000000] (9 early reservations) ==> bootmem [0000000000 - 002f6e0000]
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000]   #1 [0000001000 - 0000002000]    EX TRAMPOLINE ==> [0000001000 - 0000002000]
[    0.000000]   #2 [0000006000 - 0000007000]       TRAMPOLINE ==> [0000006000 - 0000007000]
[    0.000000]   #3 [0000100000 - 00005c29e0]    TEXT DATA BSS ==> [0000100000 - 00005c29e0]
[    0.000000]   #4 [002ef02000 - 002f6cf80c]          RAMDISK ==> [002ef02000 - 002f6cf80c]
[    0.000000]   #5 [00005c3000 - 00005c6000]    INIT_PG_TABLE ==> [00005c3000 - 00005c6000]
[    0.000000]   #6 [000009f000 - 0000100000]    BIOS reserved ==> [000009f000 - 0000100000]
[    0.000000]   #7 [0000007000 - 0000009000]          PGTABLE ==> [0000007000 - 0000009000]
[    0.000000]   #8 [0000009000 - 000000f000]          BOOTMAP ==> [0000009000 - 000000f000]
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000000 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x0002f6e0
[    0.000000]   HighMem  0x0002f6e0 -> 0x0002f6e0
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[2] active PFN ranges
[    0.000000]     0: 0x00000000 -> 0x0000009f
[    0.000000]     0: 0x00000100 -> 0x0002f6e0
[    0.000000] On node 0 totalpages: 194175
[    0.000000] free_area_init_node: node 0, pgdat c048c680, node_mem_map c1000000
[    0.000000]   DMA zone: 3963 pages, LIFO batch:0
[    0.000000]   Normal zone: 188504 pages, LIFO batch:31
[    0.000000] ACPI: PM-Timer IO Port: 0x1008
[    0.000000] SMP: Allowing 1 CPUs, 0 hotplug CPUs
[    0.000000] Local APIC disabled by BIOS -- you can enable it with "lapic"
[    0.000000] mapped APIC to ffffb000 (016b2000)
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000dc000
[    0.000000] PM: Registered nosave memory: 00000000000dc000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 40000000 (gap: 30000000:cf800000)
[    0.000000] PERCPU: Allocating 41628 bytes of per cpu data
[    0.000000] NR_CPUS: 64, nr_cpu_ids: 1, nr_node_ids 1
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 192467
[    0.000000] Kernel command line: root=UUID=b8d4758b-f37f-4beb-b712-c7f3f783d985 ro quiet splash 
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] Extended CMOS year: 2000
[    0.000000] TSC: PIT calibration confirmed by PMTIMER.
[    0.000000] TSC: using PMTIMER calibration value
[    0.000000] Detected 1398.810 MHz processor.
[    0.004000] Console: colour VGA+ 80x25
[    0.004000] console [tty0] enabled
[    0.004000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.004000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.004000] Memory: 755900k/777088k available (2576k kernel code, 20612k reserved, 1165k data, 424k init, 0k highmem)
[    0.004000] virtual kernel memory layout:
[    0.004000]     fixmap  : 0xffc77000 - 0xfffff000   (3616 kB)
[    0.004000]     pkmap   : 0xff400000 - 0xff800000   (4096 kB)
[    0.004000]     vmalloc : 0xf0000000 - 0xff3fe000   ( 243 MB)
[    0.004000]     lowmem  : 0xc0000000 - 0xef6e0000   ( 758 MB)
[    0.004000]       .init : 0xc04ad000 - 0xc0517000   ( 424 kB)
[    0.004000]       .data : 0xc03840da - 0xc04a7680   (1165 kB)
[    0.004000]       .text : 0xc0100000 - 0xc03840da   (2576 kB)
[    0.004000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.004000] CPA: page pool initialized 1 of 1 pages preallocated
[    0.004000] SLUB: Genslabs=12, HWalign=64, Order=0-3, MinObjects=0, CPUs=1, Nodes=1
[    0.004012] Calibrating delay loop (skipped), value calculated using timer frequency.. 2797.62 BogoMIPS (lpj=5595240)
[    0.004037] Security Framework initialized
[    0.004047] SELinux:  Disabled at boot.
[    0.004074] AppArmor: AppArmor initialized
[    0.004085] Mount-cache hash table entries: 512
[    0.004296] Initializing cgroup subsys ns
[    0.004303] Initializing cgroup subsys cpuacct
[    0.004307] Initializing cgroup subsys memory
[    0.004328] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.004332] CPU: L2 cache: 1024K
[    0.004345] Checking 'hlt' instruction... OK.
[    0.020616] SMP alternatives: switching to UP code
[    0.027895] Freeing SMP alternatives: 11k freed
[    0.027900] ACPI: Core revision 20080609
[    0.032318] ACPI: Checking initramfs for custom DSDT
[    0.517048] ACPI: setting ELCR to 0200 (from 0800)
[    0.520099] weird, boot CPU (#0) not listedby the BIOS.
[    0.520102] SMP motherboard not detected.
[    0.520106] Local APIC not detected. Using dummy APIC emulation.
[    0.520110] SMP disabled
[    0.520191] Brought up 1 CPUs
[    0.520195] Total of 1 processors activated (2797.62 BogoMIPS).
[    0.520211] CPU0 attaching NULL sched-domain.
[    0.524134] net_namespace: 840 bytes
[    0.524145] Booting paravirtualized kernel on bare hardware
[    0.524399] Time: 22:34:51  Date: 03/13/09
[    0.524437] NET: Registered protocol family 16
[    0.524821] EISA bus registered
[    0.524841] ACPI: bus type pci registered
[    0.525128] PCI: PCI BIOS revision 2.10 entry at 0xfd8c6, last bus=5
[    0.525132] PCI: Using configuration type 1 for base access
[    0.527607] ACPI: EC: EC description table is found, configuring boot EC
[    0.535544] ACPI: EC: non-query interrupt received, switching to interrupt mode
[    0.537299] ACPI: Interpreter enabled
[    0.537304] ACPI: (supports S0 S3 S4 S5)
[    0.537325] ACPI: Using PIC for interrupt routing
[    0.548954] ACPI: EC: GPE = 0x1c, I/O: command/status = 0x66, data = 0x62
[    0.548958] ACPI: EC: driver started in interrupt mode
[    0.549032] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.549211] PCI: 0000:00:02.0 reg 10 32bit mmio: [e0000000, e7ffffff]
[    0.549218] PCI: 0000:00:02.0 reg 14 32bit mmio: [d0000000, d007ffff]
[    0.549224] PCI: 0000:00:02.0 reg 18 io port: [1800, 1807]
[    0.549244] pci 0000:00:02.0: supports D1
[    0.549260] PCI: 0000:00:02.1 reg 10 32bit mmio: [e8000000, efffffff]
[    0.549266] PCI: 0000:00:02.1 reg 14 32bit mmio: [d0080000, d00fffff]
[    0.549288] pci 0000:00:02.1: supports D1
[    0.549356] PCI: 0000:00:1d.0 reg 20 io port: [1820, 183f]
[    0.549406] PCI: 0000:00:1d.1 reg 20 io port: [1840, 185f]
[    0.549455] PCI: 0000:00:1d.2 reg 20 io port: [1860, 187f]
[    0.549510] PCI: 0000:00:1d.7 reg 10 32bit mmio: [d0100000, d01003ff]
[    0.549560] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
[    0.549566] pci 0000:00:1d.7: PME# disabled
[    0.549637] HPET not enabled in BIOS. You might try hpet=force boot option
[    0.549645] pci 0000:00:1f.0: quirk: region 1000-107f claimed by ICH4 ACPI/GPIO/TCO
[    0.549651] pci 0000:00:1f.0: quirk: region 1180-11bf claimed by ICH4 GPIO
[    0.549670] PCI: 0000:00:1f.1 reg 10 io port: [0, 7]
[    0.549677] PCI: 0000:00:1f.1 reg 14 io port: [0, 3]
[    0.549685] PCI: 0000:00:1f.1 reg 18 io port: [0, 7]
[    0.549692] PCI: 0000:00:1f.1 reg 1c io port: [0, 3]
[    0.549700] PCI: 0000:00:1f.1 reg 20 io port: [1810, 181f]
[    0.549707] PCI: 0000:00:1f.1 reg 24 32bit mmio: [0, 3ff]
[    0.549754] PCI: 0000:00:1f.3 reg 20 io port: [1880, 189f]
[    0.549793] PCI: 0000:00:1f.5 reg 10 io port: [1c00, 1cff]
[    0.549800] PCI: 0000:00:1f.5 reg 14 io port: [18c0, 18ff]
[    0.549807] PCI: 0000:00:1f.5 reg 18 32bit mmio: [d0100c00, d0100dff]
[    0.549814] PCI: 0000:00:1f.5 reg 1c 32bit mmio: [d0100800, d01008ff]
[    0.549840] pci 0000:00:1f.5: PME# supported from D0 D3hot D3cold
[    0.549845] pci 0000:00:1f.5: PME# disabled
[    0.549870] PCI: 0000:00:1f.6 reg 10 io port: [2400, 24ff]
[    0.549877] PCI: 0000:00:1f.6 reg 14 io port: [2000, 207f]
[    0.549910] pci 0000:00:1f.6: PME# supported from D0 D3hot D3cold
[    0.549915] pci 0000:00:1f.6: PME# disabled
[    0.552038] PCI: 0000:02:00.0 reg 10 32bit mmio: [b0000000, b0000fff]
[    0.552053] pci 0000:02:00.0: supports D1
[    0.552055] pci 0000:02:00.0: supports D2
[    0.552058] pci 0000:02:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.552064] pci 0000:02:00.0: PME# disabled
[    0.552091] PCI: 0000:02:02.0 reg 10 32bit mmio: [d0200000, d0200fff]
[    0.552131] pci 0000:02:02.0: PME# supported from D0 D3hot D3cold
[    0.552136] pci 0000:02:02.0: PME# disabled
[    0.552165] PCI: 0000:02:08.0 reg 10 32bit mmio: [d0201000, d0201fff]
[    0.552173] PCI: 0000:02:08.0 reg 14 io port: [7000, 703f]
[    0.552205] pci 0000:02:08.0: supports D1
[    0.552208] pci 0000:02:08.0: supports D2
[    0.552211] pci 0000:02:08.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.552216] pci 0000:02:08.0: PME# disabled
[    0.552242] pci 0000:00:1e.0: transparent bridge
[    0.552248] PCI: bridge 0000:00:1e.0 io port: [3000, 7fff]
[    0.552254] PCI: bridge 0000:00:1e.0 32bit mmio: [d0200000, dfffffff]
[    0.552260] PCI: bridge 0000:00:1e.0 32bit mmio pref: [f0000000, f7ffffff]
[    0.552283] bus 00 -> node 0
[    0.552293] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.552402] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCI1._PRT]
[    0.556092] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 9 10 *11)
[    0.556387] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 9 10 *11)
[    0.556679] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 9 10 *11)
[    0.556966] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 9 10 *11)
[    0.557253] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 9 10 *11)
[    0.557542] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 9 10 *11)
[    0.557806] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 9 10 11) *0, disabled.
[    0.558096] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 9 10 *11)
[    0.558304] ACPI: Power Resource [PUBS] (on)
[    0.558304] Linux Plug and Play Support v0.97 (c) Adam Belay
[    0.558304] pnp: PnP ACPI init
[    0.558304] ACPI: bus type pnp registered
[    0.562007] pnp: PnP ACPI: found 10 devices
[    0.562007] ACPI: ACPI bus type pnp unregistered
[    0.562007] PnPBIOS: Disabled by ACPI PNP
[    0.562007] PCI: Using ACPI for IRQ routing
[    0.562007] NET: Registered protocol family 8
[    0.562007] NET: Registered protocol family 20
[    0.562007] NetLabel: Initializing
[    0.562007] NetLabel:  domain hash size = 128
[    0.562007] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.562007] NetLabel:  unlabeled traffic allowed by default
[    0.562007] tracer: 772 pages allocated for 65536 entries of 48 bytes
[    0.562007]    actual entries 65620
[    0.562007] AppArmor: AppArmor Filesystem Enabled
[    0.562007] ACPI: RTC can wake from S4
[    0.562007] system 00:00: iomem range 0x0-0x9ffff could not be reserved
[    0.562007] system 00:00: iomem range 0xc0000-0xc3fff could not be reserved
[    0.562007] system 00:00: iomem range 0xc4000-0xc7fff could not be reserved
[    0.562007] system 00:00: iomem range 0xc8000-0xcbfff has been reserved
[    0.562007] system 00:00: iomem range 0xcc000-0xcffff could not be reserved
[    0.562007] system 00:00: iomem range 0xdc000-0xdffff could not be reserved
[    0.562007] system 00:00: iomem range 0xe0000-0xe3fff could not be reserved
[    0.562007] system 00:00: iomem range 0xe4000-0xe7fff could not be reserved
[    0.562007] system 00:00: iomem range 0xe8000-0xebfff could not be reserved
[    0.562007] system 00:00: iomem range 0xec000-0xeffff could not be reserved
[    0.562007] system 00:00: iomem range 0xf0000-0xfffff could not be reserved
[    0.562007] system 00:00: iomem range 0x100000-0x2fffffff could not be reserved
[    0.562007] system 00:00: iomem range 0xfec00000-0xffffffff could not be reserved
[    0.562007] system 00:02: ioport range 0x1000-0x107f has been reserved
[    0.562007] system 00:02: ioport range 0x1180-0x11bf has been reserved
[    0.562007] system 00:02: ioport range 0x15e0-0x15ef has been reserved
[    0.562007] system 00:02: ioport range 0x1600-0x167f has been reserved
[    0.599204] pci 0000:02:00.0: CardBus bridge, secondary bus 0000:03
[    0.599208] pci 0000:02:00.0:   IO window: 0x003000-0x0030ff
[    0.599214] pci 0000:02:00.0:   IO window: 0x003400-0x0034ff
[    0.599220] pci 0000:02:00.0:   PREFETCH window: 0xf0000000-0xf3ffffff
[    0.599225] pci 0000:02:00.0:   MEM window: 0xd4000000-0xd7ffffff
[    0.599231] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:02
[    0.599235] pci 0000:00:1e.0:   IO window: 0x3000-0x7fff
[    0.599242] pci 0000:00:1e.0:   MEM window: 0xd0200000-0xdfffffff
[    0.599248] pci 0000:00:1e.0:   PREFETCH window: 0x000000f0000000-0x000000f7ffffff
[    0.599266] pci 0000:00:1e.0: setting latency timer to 64
[    0.599847] ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 11
[    0.599851] PCI: setting IRQ 11 as level-triggered
[    0.599857] pci 0000:02:00.0: PCI INT A -> Link[LNKA] -> GSI 11 (level, low) -> IRQ 11
[    0.599864] bus: 00 index 0 io port: [0, ffff]
[    0.599868] bus: 00 index 1 mmio: [0, ffffffff]
[    0.599871] bus: 02 index 0 io port: [3000, 7fff]
[    0.599874] bus: 02 index 1 mmio: [d0200000, dfffffff]
[    0.599877] bus: 02 index 2 mmio: [f0000000, f7ffffff]
[    0.599880] bus: 02 index 3 io port: [0, ffff]
[    0.599883] bus: 02 index 4 mmio: [0, ffffffff]
[    0.599886] bus: 03 index 0 io port: [3000, 30ff]
[    0.599889] bus: 03 index 1 io port: [3400, 34ff]
[    0.599892] bus: 03 index 2 mmio: [f0000000, f3ffffff]
[    0.599895] bus: 03 index 3 mmio: [d4000000, d7ffffff]
[    0.599911] NET: Registered protocol family 2
[    0.600094] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.600445] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.602005] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.603090] TCP: Hash tables configured (established 131072 bind 65536)
[    0.603097] TCP reno registered
[    0.603332] NET: Registered protocol family 1
[    0.603532] checking if image is initramfs... it is
[    1.100082] Switched to high resolution mode on CPU 0
[    1.586570] Freeing initrd memory: 7990k freed
[    1.586892] Simple Boot Flag at 0x35 set to 0x1
[    1.587424] audit: initializing netlink socket (disabled)
[    1.587451] type=2000 audit(1236983691.584:1): initialized
[    1.596238] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    1.599288] VFS: Disk quotas dquot_6.5.1
[    1.599425] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    1.599568] msgmni has been set to 1492
[    1.599746] io scheduler noop registered
[    1.599750] io scheduler anticipatory registered
[    1.599754] io scheduler deadline registered
[    1.599771] io scheduler cfq registered (default)
[    1.599796] pci 0000:00:02.0: Boot video device
[    1.599881] pci 0000:02:08.0: Firmware left e100 interrupts enabled; disabling
[    1.600352] isapnp: Scanning for PnP cards...
[    1.953235] isapnp: No Plug & Play device found
[    2.000514] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
[    2.001944] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 11
[    2.001951] serial 0000:00:1f.6: PCI INT B -> Link[LNKB] -> GSI 11 (level, low) -> IRQ 11
[    2.001961] serial 0000:00:1f.6: PCI INT B disabled
[    2.004425] brd: module loaded
[    2.004538] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[    2.004703] PNP: PS/2 Controller [PNP0303:KBD,PNP0f13:MOU] at 0x60,0x64 irq 1,12
[    2.011945] serio: i8042 KBD port at 0x60,0x64 irq 1
[    2.011953] serio: i8042 AUX port at 0x60,0x64 irq 12
[    2.012390] mice: PS/2 mouse device common for all mice
[    2.012571] rtc_cmos 00:06: rtc core: registered rtc_cmos as rtc0
[    2.012591] rtc0: alarms up to one month, y3k
[    2.012744] EISA: Probing bus 0 at eisa.0
[    2.012752] Cannot allocate resource for EISA slot 1
[    2.012756] Cannot allocate resource for EISA slot 2
[    2.012759] Cannot allocate resource for EISA slot 3
[    2.012762] Cannot allocate resource for EISA slot 4
[    2.012765] Cannot allocate resource for EISA slot 5
[    2.012768] Cannot allocate resource for EISA slot 6
[    2.012772] Cannot allocate resource for EISA slot 7
[    2.012777] EISA: Detected 0 cards.
[    2.012781] cpuidle: using governor ladder
[    2.012785] cpuidle: using governor menu
[    2.013493] TCP cubic registered
[    2.013534] Using IPI No-Shortcut mode
[    2.013840] registered taskstats version 1
[    2.013989]   Magic number: 1:322:603
[    2.014089] tty ptyd7: hash matches
[    2.014105] tty ptyaa: hash matches
[    2.014255] rtc_cmos 00:06: setting system clock to 2009-03-13 22:34:53 UTC (1236983693)
[    2.014260] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    2.014263] EDD information not available.
[    2.014541] Freeing unused kernel memory: 424k freed
[    2.014608] Write protecting the kernel text: 2580k
[    2.014649] Write protecting the kernel read-only data: 940k
[    2.018215] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[    2.304056] fuse init (API version 7.9)
[    2.451673] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[    2.451750] processor ACPI0007:00: registered as cooling_device0
[    2.451756] ACPI: Processor [CPU] (supports 8 throttling states)
[    2.455302] Marking TSC unstable due to TSC halts in idle
[    2.456407] thermal LNXTHERM:01: registered as thermal_zone0
[    2.459557] ACPI: Thermal Zone [THM0] (59 C)
[    3.300121] usbcore: registered new interface driver usbfs
[    3.300161] usbcore: registered new interface driver hub
[    3.300214] usbcore: registered new device driver usb
[    3.304188] USB Universal Host Controller Interface driver v3.0
[    3.308426] uhci_hcd 0000:00:1d.0: power state changed by ACPI to D0
[    3.308441] uhci_hcd 0000:00:1d.0: PCI INT A -> Link[LNKA] -> GSI 11 (level, low) -> IRQ 11
[    3.308454] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    3.308460] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    3.308535] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[    3.308563] uhci_hcd 0000:00:1d.0: irq 11, io base 0x00001820
[    3.308827] usb usb1: configuration #1 chosen from 1 choice
[    3.308865] hub 1-0:1.0: USB hub found
[    3.308876] hub 1-0:1.0: 2 ports detected
[    3.308976] Warning! ehci_hcd should always be loaded before uhci_hcd and ohci_hcd, not after
[    3.348169] e100: Intel(R) PRO/100 Network Driver, 3.5.23-k4-NAPI
[    3.348174] e100: Copyright(c) 1999-2006 Intel Corporation
[    3.364275] No dock devices found.
[    3.412814] uhci_hcd 0000:00:1d.1: power state changed by ACPI to D0
[    3.413333] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 11
[    3.413339] uhci_hcd 0000:00:1d.1: PCI INT B -> Link[LNKD] -> GSI 11 (level, low) -> IRQ 11
[    3.413352] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    3.413357] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    3.413407] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[    3.413436] uhci_hcd 0000:00:1d.1: irq 11, io base 0x00001840
[    3.413577] usb usb2: configuration #1 chosen from 1 choice
[    3.413614] hub 2-0:1.0: USB hub found
[    3.413625] hub 2-0:1.0: 2 ports detected
[    3.417302] SCSI subsystem initialized
[    3.510709] libata version 3.00 loaded.
[    3.620980] ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 11
[    3.620988] uhci_hcd 0000:00:1d.2: PCI INT C -> Link[LNKC] -> GSI 11 (level, low) -> IRQ 11
[    3.621002] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    3.621007] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    3.621046] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
[    3.621076] uhci_hcd 0000:00:1d.2: irq 11, io base 0x00001860
[    3.621222] usb usb3: configuration #1 chosen from 1 choice
[    3.621259] hub 3-0:1.0: USB hub found
[    3.621270] hub 3-0:1.0: 2 ports detected
[    3.725031] ehci_hcd 0000:00:1d.7: power state changed by ACPI to D0
[    3.725555] ACPI: PCI Interrupt Link [LNKH] enabled at IRQ 11
[    3.725561] ehci_hcd 0000:00:1d.7: PCI INT D -> Link[LNKH] -> GSI 11 (level, low) -> IRQ 11
[    3.725582] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    3.725587] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    3.725636] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 4
[    3.729554] ehci_hcd 0000:00:1d.7: debug port 1
[    3.729562] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
[    3.729574] ehci_hcd 0000:00:1d.7: irq 11, io mem 0xd0100000
[    3.733465] usb 2-1: new low speed USB device using uhci_hcd and address 2
[    3.744039] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    3.744274] usb usb4: configuration #1 chosen from 1 choice
[    3.744319] hub 4-0:1.0: USB hub found
[    3.744332] hub 4-0:1.0: 6 ports detected
[    3.800107] hub 2-0:1.0: unable to enumerate USB device on port 1
[    3.954069] ACPI: PCI Interrupt Link [LNKE] enabled at IRQ 11
[    3.954078] e100 0000:02:08.0: PCI INT A -> Link[LNKE] -> GSI 11 (level, low) -> IRQ 11
[    3.977593] e100 0000:02:08.0: PME# disabled
[    3.978945] e100: eth0: e100_probe: addr 0xd0201000, irq 11, MAC addr 00:0a:e4:3a:ec:31
[    3.985245] pata_acpi 0000:00:1f.1: enabling device (0005 -> 0007)
[    3.985257] pata_acpi 0000:00:1f.1: PCI INT A -> Link[LNKC] -> GSI 11 (level, low) -> IRQ 11
[    3.985298] pata_acpi 0000:00:1f.1: setting latency timer to 64
[    3.985316] pata_acpi 0000:00:1f.1: PCI INT A disabled
[    3.992888] ata_piix 0000:00:1f.1: version 2.12
[    3.992906] ata_piix 0000:00:1f.1: PCI INT A -> Link[LNKC] -> GSI 11 (level, low) -> IRQ 11
[    3.992955] ata_piix 0000:00:1f.1: setting latency timer to 64
[    3.993288] scsi0 : ata_piix
[    3.993883] scsi1 : ata_piix
[    3.994902] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0x1810 irq 14
[    3.994906] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x1818 irq 15
[    4.156425] ata1.00: ATA-6: WDC WD600VE-75HDT0, 09.07D09, max UDMA/100
[    4.156431] ata1.00: 117210240 sectors, multi 16: LBA 
[    4.164367] ata1.00: configured for UDMA/100
[    4.328454] ata2.00: ATAPI: MATSHITADVD-RAM UJ-830Sx, 1.00, max UDMA/33
[    4.344388] ata2.00: configured for UDMA/33
[    4.344538] scsi 0:0:0:0: Direct-Access     ATA      WDC WD600VE-75HD 09.0 PQ: 0 ANSI: 5
[    4.346578] scsi 1:0:0:0: CD-ROM            MATSHITA DVD-RAM UJ-830Sx 1.00 PQ: 0 ANSI: 5
[    4.355983] scsi 0:0:0:0: Attached scsi generic sg0 type 0
[    4.356057] scsi 1:0:0:0: Attached scsi generic sg1 type 5
[    4.360110] usb 2-1: new low speed USB device using uhci_hcd and address 3
[    4.380539] Driver 'sd' needs updating - please use bus_type methods
[    4.380678] sd 0:0:0:0: [sda] 117210240 512-byte hardware sectors (60012 MB)
[    4.380701] sd 0:0:0:0: [sda] Write Protect is off
[    4.380705] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    4.380740] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.380828] sd 0:0:0:0: [sda] 117210240 512-byte hardware sectors (60012 MB)
[    4.380848] sd 0:0:0:0: [sda] Write Protect is off
[    4.380851] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    4.380886] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.380891]  sda:<4>Driver 'sr' needs updating - please use bus_type methods
[    4.534755] usb 2-1: configuration #1 chosen from 1 choice
[    4.564214] usbcore: registered new interface driver hiddev
[    4.582876] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:1d.1/usb2/2-1/2-1:1.0/input/input2
[    4.583321] input,hidraw0: USB HID v1.11 Mouse [Logitech USB Receiver] on usb-0000:00:1d.1-1
[    4.583350] usbcore: registered new interface driver usbhid
[    4.583354] usbhid: v2.6:USB HID core driver
[    4.667593]  sda1 sda2 < sda5 >
[    4.700364] sd 0:0:0:0: [sda] Attached SCSI disk
[    4.715644] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[    4.715652] Uniform CD-ROM driver Revision: 3.20
[    4.715788] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    5.017977] PM: Starting manual resume from disk
[    5.017983] PM: Resume from partition 8:5
[    5.017985] PM: Checking hibernation image.
[    5.018200] PM: Resume from disk failed.
[    5.094357] kjournald starting.  Commit interval 5 seconds
[    5.094377] EXT3-fs: mounted filesystem with ordered data mode.
[   13.024729] udevd version 124 started
[   14.454495] Linux agpgart interface v0.103
[   14.541738] iTCO_vendor_support: vendor-support=0
[   14.596243] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.03 (30-Apr-2008)
[   14.596381] iTCO_wdt: Found a ICH4-M TCO device (Version=1, TCOBASE=0x1060)
[   14.596590] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   14.632843] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   14.718915] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   14.823740] intel_rng: FWH not detected
[   14.868221] agpgart-intel 0000:00:00.0: Intel 855GM Chipset
[   14.868477] agpgart-intel 0000:00:00.0: detected 8060K stolen memory
[   14.877539] agpgart-intel 0000:00:00.0: AGP aperture is 128M @ 0xe0000000
[   15.094575] input: PC Speaker as /devices/platform/pcspkr/input/input3
[   15.480344] input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input4
[   15.492060] ACPI: Power Button (FF) [PWRF]
[   15.492236] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input5
[   15.500168] ACPI: Lid Switch [LID]
[   15.500264] input: Sleep Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input6
[   15.512036] ACPI: Sleep Button (CM) [SLPB]
[   16.412931] parport_pc 00:09: reported by Plug and Play ACPI
[   16.412973] parport0: PC-style at 0x3bc, irq 7 [PCSPP,TRISTATE]
[   16.702323] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A03:00/device:03/input/input7
[   16.712071] ACPI: Video Device [VID] (multi-head: yes  rom: no  post: no)
[   16.921242] ieee80211_crypt: registered algorithm 'NULL'
[   16.937184] ieee80211: 802.11 data/management/control stack, git-1.1.13
[   16.937189] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
[   16.981314] Yenta: CardBus bridge found at 0000:02:00.0 [1014:0512]
[   16.981336] Yenta: Using INTVAL to route CSC interrupts to PCI
[   16.981339] Yenta: Routing CardBus interrupts to PCI
[   16.981345] Yenta TI: socket 0000:02:00.0, mfunc 0x01d21022, devctl 0x64
[   17.132232] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.2.2kmprq
[   17.132238] ipw2200: Copyright(c) 2003-2006 Intel Corporation
[   17.212601] Yenta: ISA IRQ mask 0x0478, PCI irq 11
[   17.212606] Socket status: 30000007
[   17.212612] pcmcia: parent PCI bridge I/O window: 0x3000 - 0x7fff
[   17.212616] cs: IO port probe 0x3000-0x7fff: clean.
[   17.214127] pcmcia: parent PCI bridge Memory window: 0xd0200000 - 0xdfffffff
[   17.214131] pcmcia: parent PCI bridge Memory window: 0xf0000000 - 0xf7ffffff
[   17.215217] ACPI: PCI Interrupt Link [LNKF] enabled at IRQ 11
[   17.215224] ipw2200 0000:02:02.0: PCI INT A -> Link[LNKF] -> GSI 11 (level, low) -> IRQ 11
[   17.228099] ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection
[   17.228160] firmware: requesting ipw2200-bss.fw
[   17.610306] IBM TrackPoint firmware: 0x0e, buttons: 3/3
[   17.621730] ACPI: AC Adapter [AC] (on-line)
[   17.625551] input: TPPS/2 IBM TrackPoint as /devices/platform/i8042/serio1/input/input8
[   17.869458] ACPI: Battery Slot [BAT0] (battery present)
[   18.220417] usbcore: registered new interface driver lmpcm_usb
[   18.220439] lmpcm_usb: v0.5.5:USB Logitech MediaPlay Cordless Mouse driver
[   18.564531] Non-volatile memory driver v1.2
[   18.719482] thinkpad_acpi: ThinkPad ACPI Extras v0.21
[   18.719487] thinkpad_acpi: http://ibm-acpi.sf.net/
[   18.719490] thinkpad_acpi: ThinkPad BIOS 1WET82WW (2.02 ), EC 1VHT28WW-1.04
[   18.719494] thinkpad_acpi: IBM ThinkPad R50e, model 1834S5G
[   18.724271] Registered led device: tpacpi::thinklight
[   18.724356] Registered led device: tpacpi::power
[   18.724396] Registered led device: tpacpi:orange:batt
[   18.724435] Registered led device: tpacpi:green:batt
[   18.724472] Registered led device: tpacpi::dock_active
[   18.724514] Registered led device: tpacpi::bay_active
[   18.724553] Registered led device: tpacpi::dock_batt
[   18.724591] Registered led device: tpacpi::unknown_led
[   18.724628] Registered led device: tpacpi::standby
[   18.727291] input: ThinkPad Extra Buttons as /devices/virtual/input/input9
[   20.981399] ipw2200: Detected geography ZZR (14 802.11bg channels, 0 802.11a channels)
[   20.981460] Intel ICH 0000:00:1f.5: PCI INT B -> Link[LNKB] -> GSI 11 (level, low) -> IRQ 11
[   20.981496] Intel ICH 0000:00:1f.5: setting latency timer to 64
[   21.115829] cs: IO port probe 0x100-0x3af: clean.
[   21.116712] cs: IO port probe 0x3e0-0x4ff: excluding 0x4d0-0x4d7
[   21.117097] cs: IO port probe 0x820-0x8ff: clean.
[   21.117416] cs: IO port probe 0xc00-0xcf7: clean.
[   21.117894] cs: IO port probe 0xa00-0xaff: clean.
[   21.904031] intel8x0_measure_ac97_clock: measured 55444 usecs
[   21.904036] intel8x0: clocking to 48000
[   22.930360] lp0: using parport0 (interrupt-driven).
[   23.034694] Adding 2241028k swap on /dev/sda5.  Priority:-1 extents:1 across:2241028k
[   23.588238] EXT3 FS on sda1, internal journal
[   24.894802] type=1505 audit(1236983716.366:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=3929
[   25.177028] type=1505 audit(1236983716.650:3): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=3934
[   25.177453] type=1505 audit(1236983716.650:4): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=3934
[   25.586595] ip_tables: (C) 2000-2006 Netfilter Core Team
[   26.379869] ACPI: WMI: Mapper loaded
[   27.541945] warning: `avahi-daemon' uses 32-bit capabilities (legacy support in use)
[   27.641823] IBM machine detected. Enabling interrupts during APM calls.
[   27.641830] apm: BIOS not found.
[   27.824344] ppdev: user-space parallel port driver
[   29.180417] vboxdrv: Trying to deactivate the NMI watchdog permanently...
[   29.180425] vboxdrv: Successfully done.
[   29.180427] vboxdrv: Found 1 processor cores.
[   29.182449] vboxdrv: TSC mode is 'synchronous', kernel timer mode is 'normal'.
[   29.182457] vboxdrv: Successfully loaded version 2.0.4_OSE (interface 0x00090000).
[   31.584240] Bluetooth: Core ver 2.13
[   31.586122] NET: Registered protocol family 31
[   31.586128] Bluetooth: HCI device and connection manager initialized
[   31.586132] Bluetooth: HCI socket layer initialized
[   31.609061] Bluetooth: L2CAP ver 2.11
[   31.609068] Bluetooth: L2CAP socket layer initialized
[   31.628166] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   31.628173] Bluetooth: BNEP filters: protocol multicast
[   31.644587] Bluetooth: RFCOMM socket layer initialized
[   31.644896] Bluetooth: RFCOMM TTY layer initialized
[   31.644901] Bluetooth: RFCOMM ver 1.10
[   31.675578] Bridge firewalling registered
[   31.689941] Bluetooth: SCO (Voice Link) ver 0.6
[   31.689948] Bluetooth: SCO socket layer initialized
[   35.446409] [drm] Initialized drm 1.1.0 20060810
[   35.478298] pci 0000:00:02.0: power state changed by ACPI to D0
[   35.481622] pci 0000:00:02.0: PCI INT A -> Link[LNKA] -> GSI 11 (level, low) -> IRQ 11
[   35.481637] pci 0000:00:02.0: setting latency timer to 64
[   35.482367] [drm] Initialized i915 1.6.0 20060119 on minor 0
[   35.482390] pci 0000:00:02.1: setting latency timer to 64
[   35.482861] [drm] Initialized i915 1.6.0 20060119 on minor 1
[   35.882081] NET: Registered protocol family 17
[   36.345416] thinkpad_acpi: CMOS NVRAM (7) and EC (5) do not agree on display brightness level
[   61.832164] ieee80211_crypt: registered algorithm 'WEP'
[   67.848411] NET: Registered protocol family 10
[   67.849428] lo: Disabled Privacy Extensions
[   67.850859] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   78.736037] eth1: no IPv6 routers present
[  130.464314] ppdev0: registered pardevice
[  130.512439] ppdev0: unregistered pardevice
[  130.633896] ppdev0: registered pardevice
[  130.680071] ppdev0: unregistered pardevice
[  132.372803] ppdev0: registered pardevice
[  132.420291] ppdev0: unregistered pardevice
[  214.812045] pccard: PCMCIA card inserted into slot 0
[  214.812655] cs: memory probe 0xf0000000-0xf7ffffff: excluding 0xf0000000-0xf7ffffff
[  214.812684] cs: memory probe 0xd0200000-0xdfffffff: excluding 0xd0200000-0xd11fffff 0xd1a00000-0xd21fffff 0xd2a00000-0xd31fffff 0xd3a00000-0xd81fffff 0xd8a00000-0xd91fffff 0xd9a00000-0xda1fffff 0xdaa00000-0xdb1fffff 0xdba00000-0xdc1fffff 0xdca00000-0xdd1fffff 0xdda00000-0xde1fffff 0xdea00000-0xdf1fffff 0xdfa00000-0xe01fffff
[  214.822519] pcmcia: registering new device pcmcia0.0
[  215.009881] scsi2 : pata_pcmcia
[  215.010582] ata3: PATA max PIO0 cmd 0x3100 ctl 0x310e irq 3
[  215.183654] ata3.01: failed to IDENTIFY (I/O error, err_mask=0x2)
[  225.368041] ata3: link is slow to respond, please be patient (ready=0)
[  230.184041] ata3: SRST failed (errno=-16)
[  235.380039] ata3: link is slow to respond, please be patient (ready=0)
[  240.200050] ata3: SRST failed (errno=-16)
[  245.396037] ata3: link is slow to respond, please be patient (ready=0)
[  275.212044] ata3: SRST failed (errno=-16)
[  280.240040] ata3: SRST failed (errno=-16)
[  280.240051] ata3: reset failed, giving up
[  285.284041] ata3: link is slow to respond, please be patient (ready=0)
[  290.268041] ata3: device not ready (errno=-16), forcing hardreset
[  290.268054] ata3: soft resetting link
[  295.464042] ata3: link is slow to respond, please be patient (ready=0)
[  300.280041] ata3: SRST failed (errno=-16)
[  300.280055] ata3: soft resetting link
[  305.448040] ata3: link is slow to respond, please be patient (ready=0)
[  310.324051] ata3: SRST failed (errno=-16)
[  310.324066] ata3: soft resetting link
[  315.524050] ata3: link is slow to respond, please be patient (ready=0)
[  345.376040] ata3: SRST failed (errno=-16)
[  345.376055] ata3: soft resetting link
[  350.404054] ata3: SRST failed (errno=-16)
[  350.404066] ata3: reset failed, giving up
[  350.404074] ata3: EH complete
```

---

### Post by softbomb on 2009-03-27
Bump. Any ideas? 

Will there be support for such basic peripherals as PCMCIA memory card readers in the next version of Ubuntu? Let's hope so.

---

### Post by beatryder on 2009-08-04
I'm also having this same problem.

---

