---
title: "Laptop freezing after random time, only when in use"
date: 2009-07-23
forum: Hardware
---

### Post by B-D_ on 2009-07-23
This is a new install on freshly formatted drive, I was thinking that the old and upgraded version had some defects in installation, so I wiped the drive and installed the newest distro 9.04.

But my problem remains: my laptop freezes after random period of time (~1 or 2 hours) in random applications (firefox, wine, terminal...).

It doesn't freeze when idle but **only when in use**, like it's waiting for I/O. After freezing nothing is responsive, mouse is dead, caps-numlock are dead, ctrl-alt-f1 terminals are dead, only sysrq works... but music from VLC **keeps playing**, so system didn't hang completely.

The ctrl-alt-sysrq+REISUB is not ignored and saves system from fsck after reboot, it reboots fine.


I have tried searching the forums before and using multiple boot options but nothing changed.

at the moment I'm using:
```
 ro quiet noapic nolapic
```using this one
```
 ro quiet noapic nolapic acpi=off
```just makes it freeze a lot sooner (after ~10 minutes of use)


If you need any specs or logs just say command and i'll post the response...

---

### Post by B-D_ on 2009-07-23
Maybe this will be of help:
```
$ dmesg
[    0.000000] BIOS EBDA/lowmem at: 0009f800/0009f800
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.28-14-generic (buildd@rothera) (gcc version 4.3.3 (Ubuntu 4.3.3-5ubuntu4) ) #46-Ubuntu SMP Wed Jul 8 07:21:34 UTC 2009 (Ubuntu 2.6.28-14.46-generic)
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
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
[    0.000000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000ce000 - 00000000000d0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000d8000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000001f6e0000 (usable)
[    0.000000]  BIOS-e820: 000000001f6e0000 - 000000001f6eb000 (ACPI data)
[    0.000000]  BIOS-e820: 000000001f6eb000 - 000000001f700000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000001f700000 - 0000000020000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec10000 - 00000000fec20000 (reserved)
[    0.000000]  BIOS-e820: 00000000ff800000 - 00000000ffc00000 (reserved)
[    0.000000]  BIOS-e820: 00000000fffffc00 - 0000000100000000 (reserved)
[    0.000000] DMI present.
[    0.000000] Phoenix BIOS detected: BIOS may corrupt low RAM, working it around.
[    0.000000] last_pfn = 0x1f6e0 max_arch_pfn = 0x100000
[    0.000000] Scanning 0 areas for low memory corruption
[    0.000000] modified physical RAM map:
[    0.000000]  modified: 0000000000000000 - 0000000000010000 (reserved)
[    0.000000]  modified: 0000000000010000 - 000000000009f800 (usable)
[    0.000000]  modified: 000000000009f800 - 00000000000a0000 (reserved)
[    0.000000]  modified: 00000000000ce000 - 00000000000d0000 (reserved)
[    0.000000]  modified: 00000000000d8000 - 0000000000100000 (reserved)
[    0.000000]  modified: 0000000000100000 - 000000001f6e0000 (usable)
[    0.000000]  modified: 000000001f6e0000 - 000000001f6eb000 (ACPI data)
[    0.000000]  modified: 000000001f6eb000 - 000000001f700000 (ACPI NVS)
[    0.000000]  modified: 000000001f700000 - 0000000020000000 (reserved)
[    0.000000]  modified: 00000000fec10000 - 00000000fec20000 (reserved)
[    0.000000]  modified: 00000000ff800000 - 00000000ffc00000 (reserved)
[    0.000000]  modified: 00000000fffffc00 - 0000000100000000 (reserved)
[    0.000000] kernel direct mapping tables up to 1f6e0000 @ 10000-16000
[    0.000000] RAMDISK: 1ef9b000 - 1f6cff4f
[    0.000000] ACPI: RSDP 000F6560, 0014 (r0 PTLTD )
[    0.000000] ACPI: RSDT 1F6E6530, 0030 (r1 PTLTD  Montara   6040000  LTP        0)
[    0.000000] ACPI: FACP 1F6EAED2, 0074 (r1 INTEL  MONTARAG  6040000 PTL        50)
[    0.000000] ACPI: DSDT 1F6E6A38, 449A (r1 INTEL  MONTARAG  6040000 MSFT  100000E)
[    0.000000] ACPI: FACS 1F6FBFC0, 0040
[    0.000000] ACPI: BOOT 1F6EAFD8, 0028 (r1 PTLTD  $SBFTBL$  6040000  LTP        1)
[    0.000000] ACPI: SSDT 1F6E6560, 04D0 (r1 INTEL    GV3Ref     1001 MSFT  100000E)
[    0.000000] 0MB HIGHMEM available.
[    0.000000] 502MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 1f6e0000
[    0.000000]   low ram: 00000000 - 1f6e0000
[    0.000000]   bootmap 00012000 - 00015edc
[    0.000000] (9 early reservations) ==> bootmem [0000000000 - 001f6e0000]
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000]   #1 [0000001000 - 0000002000]    EX TRAMPOLINE ==> [0000001000 - 0000002000]
[    0.000000]   #2 [0000006000 - 0000007000]       TRAMPOLINE ==> [0000006000 - 0000007000]
[    0.000000]   #3 [0000100000 - 00008760ac]    TEXT DATA BSS ==> [0000100000 - 00008760ac]
[    0.000000]   #4 [001ef9b000 - 001f6cff4f]          RAMDISK ==> [001ef9b000 - 001f6cff4f]
[    0.000000]   #5 [0000877000 - 000087b000]    INIT_PG_TABLE ==> [0000877000 - 000087b000]
[    0.000000]   #6 [000009f800 - 0000100000]    BIOS reserved ==> [000009f800 - 0000100000]
[    0.000000]   #7 [0000010000 - 0000012000]          PGTABLE ==> [0000010000 - 0000012000]
[    0.000000]   #8 [0000012000 - 0000016000]          BOOTMAP ==> [0000012000 - 0000016000]
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x0001f6e0
[    0.000000]   HighMem  0x0001f6e0 -> 0x0001f6e0
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[2] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x0000009f
[    0.000000]     0: 0x00000100 -> 0x0001f6e0
[    0.000000] On node 0 totalpages: 128623
[    0.000000] free_area_init_node: node 0, pgdat c06c9500, node_mem_map c1000200
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3951 pages, LIFO batch:0
[    0.000000]   Normal zone: 974 pages used for memmap
[    0.000000]   Normal zone: 123666 pages, LIFO batch:31
[    0.000000]   HighMem zone: 0 pages used for memmap
[    0.000000]   Movable zone: 0 pages used for memmap
[    0.000000] ACPI: PM-Timer IO Port: 0x1008
[    0.000000] SMP: Allowing 1 CPUs, 0 hotplug CPUs
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000ce000
[    0.000000] PM: Registered nosave memory: 00000000000ce000 - 00000000000d0000
[    0.000000] PM: Registered nosave memory: 00000000000d0000 - 00000000000d8000
[    0.000000] PM: Registered nosave memory: 00000000000d8000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 30000000 (gap: 20000000:dec10000)
[    0.000000] PERCPU: Allocating 45056 bytes of per cpu data
[    0.000000] NR_CPUS: 64, nr_cpu_ids: 1, nr_node_ids 1
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 127617
[    0.000000] Kernel command line: root=UUID=8deb2014-487f-4d24-b61b-b2e4f9cbb1ed ro noapic nolapic
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 2048 (order: 11, 8192 bytes)
[    0.000000] TSC: PIT calibration matches PMTIMER. 1 loops
[    0.000000] Detected 599.908 MHz processor.
[    0.004000] Console: colour VGA+ 80x25
[    0.004000] console [tty0] enabled
[    0.004000] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.004000] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.004000] allocated 2574400 bytes of page_cgroup
[    0.004000] please try cgroup_disable=memory option if you don't want
[    0.004000] Scanning for low memory corruption every 60 seconds
[    0.004000] Memory: 492212k/514944k available (4111k kernel code, 22076k reserved, 2196k data, 532k init, 0k highmem)
[    0.004000] virtual kernel memory layout:
[    0.004000]     fixmap  : 0xffc77000 - 0xfffff000   (3616 kB)
[    0.004000]     pkmap   : 0xff400000 - 0xff800000   (4096 kB)
[    0.004000]     vmalloc : 0xdfee0000 - 0xff3fe000   ( 501 MB)
[    0.004000]     lowmem  : 0xc0000000 - 0xdf6e0000   ( 502 MB)
[    0.004000]       .init : 0xc0731000 - 0xc07b6000   ( 532 kB)
[    0.004000]       .data : 0xc0503d2f - 0xc0728e60   (2196 kB)
[    0.004000]       .text : 0xc0100000 - 0xc0503d2f   (4111 kB)
[    0.004000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.004000] SLUB: Genslabs=12, HWalign=64, Order=0-3, MinObjects=0, CPUs=1, Nodes=1
[    0.004021] Calibrating delay loop (skipped), value calculated using timer frequency.. 1199.81 BogoMIPS (lpj=2399632)
[    0.004176] Security Framework initialized
[    0.004245] SELinux:  Disabled at boot.
[    0.004350] AppArmor: AppArmor initialized
[    0.004424] Mount-cache hash table entries: 512
[    0.004787] Initializing cgroup subsys ns
[    0.004852] Initializing cgroup subsys cpuacct
[    0.004915] Initializing cgroup subsys memory
[    0.004980] Initializing cgroup subsys freezer
[    0.005070] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.005165] CPU: L2 cache: 1024K
[    0.005244] Checking 'hlt' instruction... OK.
[    0.021705] SMP alternatives: switching to UP code
[    0.333205] Freeing SMP alternatives: 18k freed
[    0.333273] ACPI: Core revision 20080926
[    0.339407] ACPI: Checking initramfs for custom DSDT
[    1.328069] ACPI: setting ELCR to 0200 (from 0c00)
[    1.332110] weird, boot CPU (#0) not listedby the BIOS.
[    1.332174] SMP motherboard not detected.
[    1.332234] Local APIC not detected. Using dummy APIC emulation.
[    1.332296] SMP disabled
[    1.332983] Brought up 1 CPUs
[    1.333042] Total of 1 processors activated (1199.81 BogoMIPS).
[    1.333128] CPU0 attaching NULL sched-domain.
[    1.333688] net_namespace: 776 bytes
[    1.333767] Booting paravirtualized kernel on bare hardware
[    1.334542] Time: 18:33:01  Date: 07/23/09
[    1.334610] regulator: core version 0.5
[    1.336081] NET: Registered protocol family 16
[    1.336484] EISA bus registered
[    1.336567] ACPI: bus type pci registered
[    1.338479] PCI: PCI BIOS revision 2.10 entry at 0xfd6c4, last bus=3
[    1.338544] PCI: Using configuration type 1 for base access
[    1.343015] ACPI: EC: Look up EC in DSDT
[    1.349722] ACPI: Interpreter enabled
[    1.349789] ACPI: (supports S0 S3 S4 S5)
[    1.350020] ACPI: Using PIC for interrupt routing
[    1.350644] ACPI: EC: non-query interrupt received, switching to interrupt mode
[    1.759612] ACPI: EC: GPE = 0x1c, I/O: command/status = 0x66, data = 0x62
[    1.759681] ACPI: EC: driver started in interrupt mode
[    1.760084] ACPI: No dock devices found.
[    1.760173] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    1.760480] pci 0000:00:02.0: reg 10 32bit mmio: [0xe8000000-0xefffffff]
[    1.760493] pci 0000:00:02.0: reg 14 32bit mmio: [0xe0000000-0xe007ffff]
[    1.760505] pci 0000:00:02.0: reg 18 io port: [0x1800-0x1807]
[    1.760536] pci 0000:00:02.0: supports D1
[    1.760569] pci 0000:00:02.1: reg 10 32bit mmio: [0xf0000000-0xf7ffffff]
[    1.760581] pci 0000:00:02.1: reg 14 32bit mmio: [0xe0080000-0xe00fffff]
[    1.760615] pci 0000:00:02.1: supports D1
[    1.760713] pci 0000:00:1d.0: reg 20 io port: [0x1820-0x183f]
[    1.760782] pci 0000:00:1d.1: reg 20 io port: [0x1840-0x185f]
[    1.760852] pci 0000:00:1d.2: reg 20 io port: [0x1860-0x187f]
[    1.760931] pci 0000:00:1d.7: reg 10 32bit mmio: [0xe0100000-0xe01003ff]
[    1.760989] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
[    1.761057] pci 0000:00:1d.7: PME# disabled
[    1.761220] HPET not enabled in BIOS. You might try hpet=force boot option
[    1.761291] pci 0000:00:1f.0: quirk: region 1000-107f claimed by ICH4 ACPI/GPIO/TCO
[    1.761374] pci 0000:00:1f.0: quirk: region 1180-11bf claimed by ICH4 GPIO
[    1.761464] pci 0000:00:1f.1: reg 10 io port: [0x00-0x07]
[    1.761477] pci 0000:00:1f.1: reg 14 io port: [0x00-0x03]
[    1.761489] pci 0000:00:1f.1: reg 18 io port: [0x00-0x07]
[    1.761502] pci 0000:00:1f.1: reg 1c io port: [0x00-0x03]
[    1.761515] pci 0000:00:1f.1: reg 20 io port: [0x1810-0x181f]
[    1.761528] pci 0000:00:1f.1: reg 24 32bit mmio: [0x000000-0x0003ff]
[    1.761595] pci 0000:00:1f.3: reg 20 io port: [0x1880-0x189f]
[    1.761654] pci 0000:00:1f.5: reg 10 io port: [0x1c00-0x1cff]
[    1.761666] pci 0000:00:1f.5: reg 14 io port: [0x18c0-0x18ff]
[    1.761679] pci 0000:00:1f.5: reg 18 32bit mmio: [0xe0100c00-0xe0100dff]
[    1.761693] pci 0000:00:1f.5: reg 1c 32bit mmio: [0xe0100800-0xe01008ff]
[    1.761726] pci 0000:00:1f.5: PME# supported from D0 D3hot D3cold
[    1.761791] pci 0000:00:1f.5: PME# disabled
[    1.761887] pci 0000:00:1f.6: reg 10 io port: [0x2400-0x24ff]
[    1.761899] pci 0000:00:1f.6: reg 14 io port: [0x2000-0x207f]
[    1.761943] pci 0000:00:1f.6: PME# supported from D0 D3hot D3cold
[    1.762009] pci 0000:00:1f.6: PME# disabled
[    1.762120] pci 0000:02:03.0: reg 10 32bit mmio: [0xe0202000-0xe0202fff]
[    1.762169] pci 0000:02:03.0: supports D1 D2
[    1.762175] pci 0000:02:03.0: PME# supported from D0 D1 D2 D3hot
[    1.762242] pci 0000:02:03.0: PME# disabled
[    1.762340] pci 0000:02:05.0: reg 10 32bit mmio: [0xe0200000-0xe0201fff]
[    1.762379] pci 0000:02:05.0: reg 30 32bit mmio: [0x000000-0x00ffff]
[    1.762395] pci 0000:02:05.0: supports D1 D2
[    1.762402] pci 0000:02:05.0: PME# supported from D0 D1 D2 D3hot D3cold
[    1.762469] pci 0000:02:05.0: PME# disabled
[    1.762569] pci 0000:02:06.0: reg 10 32bit mmio: [0xe0203000-0xe0203fff]
[    1.762664] pci 0000:02:09.0: reg 10 32bit mmio: [0x000000-0x000fff]
[    1.762681] pci 0000:02:09.0: supports D1 D2
[    1.762687] pci 0000:02:09.0: PME# supported from D0 D1 D2 D3hot D3cold
[    1.762754] pci 0000:02:09.0: PME# disabled
[    1.762850] pci 0000:00:1e.0: transparent bridge
[    1.762917] pci 0000:00:1e.0: bridge 32bit mmio: [0xe0200000-0xe02fffff]
[    1.762957] bus 00 -> node 0
[    1.762975] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    1.763716] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIB._PRT]
[    1.776132] ACPI: PCI Interrupt Link [LNKA] (IRQs 10 *11)
[    1.776607] ACPI: PCI Interrupt Link [LNKB] (IRQs *10 11)
[    1.777073] ACPI: PCI Interrupt Link [LNKC] (IRQs 10 *11)
[    1.777537] ACPI: PCI Interrupt Link [LNKD] (IRQs *11)
[    1.777968] ACPI: PCI Interrupt Link [LNKE] (IRQs *10 11)
[    1.778431] ACPI: PCI Interrupt Link [LNKF] (IRQs *10 11)
[    1.778892] ACPI: PCI Interrupt Link [LNKG] (IRQs *10 11)
[    1.779356] ACPI: PCI Interrupt Link [LNKH] (IRQs 10 *11)
[    1.779835] ACPI: WMI: Mapper loaded
[    1.780355] SCSI subsystem initialized
[    1.780514] libata version 3.00 loaded.
[    1.780639] usbcore: registered new interface driver usbfs
[    1.780742] usbcore: registered new interface driver hub
[    1.781845] usbcore: registered new device driver usb
[    1.782211] PCI: Using ACPI for IRQ routing
[    1.782466] Bluetooth: Core ver 2.13
[    1.782466] NET: Registered protocol family 31
[    1.782466] Bluetooth: HCI device and connection manager initialized
[    1.782466] Bluetooth: HCI socket layer initialized
[    1.782466] NET: Registered protocol family 8
[    1.782466] NET: Registered protocol family 20
[    1.782466] NetLabel: Initializing
[    1.782466] NetLabel:  domain hash size = 128
[    1.782466] NetLabel:  protocols = UNLABELED CIPSOv4
[    1.782466] NetLabel:  unlabeled traffic allowed by default
[    1.782466] AppArmor: AppArmor Filesystem Enabled
[    1.782466] pnp: PnP ACPI init
[    1.782466] ACPI: bus type pnp registered
[    1.993414] pnp: PnP ACPI: found 12 devices
[    1.993477] ACPI: ACPI bus type pnp unregistered
[    1.993541] PnPBIOS: Disabled by ACPI PNP
[    1.993623] system 00:04: ioport range 0x600-0x60f has been reserved
[    1.993689] system 00:04: ioport range 0x700-0x70f has been reserved
[    1.993754] system 00:04: ioport range 0x800-0x80f has been reserved
[    1.993820] system 00:04: ioport range 0x1000-0x107f has been reserved
[    1.993886] system 00:04: ioport range 0x1180-0x11bf has been reserved
[    1.993954] system 00:04: iomem range 0xfec10000-0xfec1ffff has been reserved
[    2.029098] pci 0000:02:09.0: CardBus bridge, secondary bus 0000:03
[    2.029166] pci 0000:02:09.0:   IO window: 0x003000-0x0030ff
[    2.029231] pci 0000:02:09.0:   IO window: 0x003400-0x0034ff
[    2.029298] pci 0000:02:09.0:   PREFETCH window: 0x30000000-0x33ffffff
[    2.029366] pci 0000:02:09.0:   MEM window: 0x38000000-0x3bffffff
[    2.029432] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:02
[    2.029496] pci 0000:00:1e.0:   IO window: 0x3000-0x3fff
[    2.029563] pci 0000:00:1e.0:   MEM window: 0xe0200000-0xe02fffff
[    2.029631] pci 0000:00:1e.0:   PREFETCH window: 0x00000030000000-0x00000035ffffff
[    2.029724] pci 0000:00:1e.0: enabling device (0005 -> 0007)
[    2.029793] pci 0000:00:1e.0: setting latency timer to 64
[    2.030231] ACPI: PCI Interrupt Link [LNKF] enabled at IRQ 10
[    2.030295] PCI: setting IRQ 10 as level-triggered
[    2.030306] pci 0000:02:09.0: PCI INT A -> Link[LNKF] -> GSI 10 (level, low) -> IRQ 10
[    2.030394] bus: 00 index 0 io port: [0x00-0xffff]
[    2.030456] bus: 00 index 1 mmio: [0x000000-0xffffffff]
[    2.030519] bus: 02 index 0 io port: [0x3000-0x3fff]
[    2.030580] bus: 02 index 1 mmio: [0xe0200000-0xe02fffff]
[    2.030643] bus: 02 index 2 mmio: [0x30000000-0x35ffffff]
[    2.030705] bus: 02 index 3 io port: [0x00-0xffff]
[    2.030766] bus: 02 index 4 mmio: [0x000000-0xffffffff]
[    2.030829] bus: 03 index 0 io port: [0x3000-0x30ff]
[    2.030889] bus: 03 index 1 io port: [0x3400-0x34ff]
[    2.030951] bus: 03 index 2 mmio: [0x30000000-0x33ffffff]
[    2.031014] bus: 03 index 3 mmio: [0x38000000-0x3bffffff]
[    2.031093] NET: Registered protocol family 2
[    2.031484] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
[    2.032304] TCP established hash table entries: 16384 (order: 5, 131072 bytes)
[    2.032547] TCP bind hash table entries: 16384 (order: 5, 131072 bytes)
[    2.032767] TCP: Hash tables configured (established 16384 bind 16384)
[    2.032832] TCP reno registered
[    2.033093] NET: Registered protocol family 1
[    2.033468] checking if image is initramfs...<7>Switched to high resolution mode on CPU 0
[    3.010472]  it is
[    4.049135] Freeing initrd memory: 7379k freed
[    4.049287] Simple Boot Flag at 0x36 set to 0x1
[    4.049402] cpufreq: No nForce2 chipset.
[    4.049827] audit: initializing netlink socket (disabled)
[    4.049922] type=2000 audit(1248373984.048:1): initialized
[    4.075246] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    4.079862] VFS: Disk quotas dquot_6.5.1
[    4.080127] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    4.082302] fuse init (API version 7.10)
[    4.082638] msgmni has been set to 976
[    4.083207] alg: No test for stdrng (krng)
[    4.083298] io scheduler noop registered
[    4.083358] io scheduler anticipatory registered
[    4.083419] io scheduler deadline registered
[    4.083531] io scheduler cfq registered (default)
[    4.083627] pci 0000:00:02.0: Boot video device
[    4.487200] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    4.487286] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    4.495754] ACPI: AC Adapter [AC] (on-line)
[    4.696523] ACPI: Battery Slot [BAT0] (battery absent)
[    4.696780] input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input0
[    4.696862] ACPI: Power Button (FF) [PWRF]
[    4.697052] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input1
[    4.697248] ACPI: Lid Switch [LID]
[    4.697433] input: Sleep Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input2
[    4.697517] ACPI: Sleep Button (CM) [SLP2]
[    4.698334] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[    4.698584] processor ACPI_CPU:00: registered as cooling_device0
[    4.698652] ACPI: Processor [CPU0] (supports 8 throttling states)
[    4.968608] thermal LNXTHERM:01: registered as thermal_zone0
[    5.002804] ACPI: Thermal Zone [THRS] (44 C)
[    5.070917] thermal LNXTHERM:02: registered as thermal_zone1
[    5.105117] ACPI: Thermal Zone [THRC] (40 C)
[    5.105295] isapnp: Scanning for PnP cards...
[    5.459445] isapnp: No Plug & Play device found
[    5.462970] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
[    5.463224] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[    5.464667] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 10
[    5.464737] serial 0000:00:1f.6: PCI INT B -> Link[LNKB] -> GSI 10 (level, low) -> IRQ 10
[    5.464827] serial 0000:00:1f.6: PCI INT B disabled
[    5.466829] brd: module loaded
[    5.467815] loop: module loaded
[    5.468106] Fixed MDIO Bus: probed
[    5.468175] PPP generic driver version 2.4.2
[    5.468399] input: Macintosh mouse button emulation as /devices/virtual/input/input3
[    5.468556] Driver 'sd' needs updating - please use bus_type methods
[    5.468640] Driver 'sr' needs updating - please use bus_type methods
[    5.468902] ata_piix 0000:00:1f.1: version 2.12
[    5.468918] ata_piix 0000:00:1f.1: enabling device (0005 -> 0007)
[    5.469406] ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 11
[    5.469470] PCI: setting IRQ 11 as level-triggered
[    5.469481] ata_piix 0000:00:1f.1: PCI INT A -> Link[LNKC] -> GSI 11 (level, low) -> IRQ 11
[    5.469635] ata_piix 0000:00:1f.1: setting latency timer to 64
[    5.469799] scsi0 : ata_piix
[    5.470087] scsi1 : ata_piix
[    5.472867] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0x1810 irq 14
[    5.472935] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x1818 irq 15
[    5.636612] ata1.00: ATA-6: FUJITSU MHT2060AT, 0022, max UDMA/100
[    5.636678] ata1.00: 117210240 sectors, multi 16: LBA 
[    5.652604] ata1.00: configured for UDMA/100
[    5.816337] ata2.00: ATAPI: QSI CD-RW/DVD-ROM SBW-242, UX10, max UDMA/33
[    5.832356] ata2.00: configured for UDMA/33
[    5.832881] scsi 0:0:0:0: Direct-Access     ATA      FUJITSU MHT2060A 0022 PQ: 0 ANSI: 5
[    5.833220] sd 0:0:0:0: [sda] 117210240 512-byte hardware sectors: (60.0 GB/55.8 GiB)
[    5.833342] sd 0:0:0:0: [sda] Write Protect is off
[    5.833404] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    5.833477] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    5.833712] sd 0:0:0:0: [sda] 117210240 512-byte hardware sectors: (60.0 GB/55.8 GiB)
[    5.833828] sd 0:0:0:0: [sda] Write Protect is off
[    5.833890] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    5.833961] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    5.834047]  sda: sda1 sda2 < sda5 >
[    5.950796] sd 0:0:0:0: [sda] Attached SCSI disk
[    5.950976] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    5.951715] scsi 1:0:0:0: CD-ROM            QSI      CDRW/DVD SBW-242 UX10 PQ: 0 ANSI: 5
[    5.954766] sr0: scsi3-mmc drive: 4x/24x writer cd/rw xa/form2 cdda tray
[    5.954834] Uniform CD-ROM driver Revision: 3.20
[    5.955130] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    5.955253] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    5.957180] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    5.957722] ACPI: PCI Interrupt Link [LNKH] enabled at IRQ 11
[    5.957790] ehci_hcd 0000:00:1d.7: PCI INT D -> Link[LNKH] -> GSI 11 (level, low) -> IRQ 11
[    5.957909] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    5.957918] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    5.958144] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 1
[    5.962168] ehci_hcd 0000:00:1d.7: debug port 1
[    5.962233] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
[    5.962253] ehci_hcd 0000:00:1d.7: irq 11, io mem 0xe0100000
[    5.976039] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    5.976298] usb usb1: configuration #1 chosen from 1 choice
[    5.976444] hub 1-0:1.0: USB hub found
[    5.976516] hub 1-0:1.0: 6 ports detected
[    5.976881] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    5.976987] uhci_hcd: USB Universal Host Controller Interface driver
[    5.977535] ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 11
[    5.977603] uhci_hcd 0000:00:1d.0: PCI INT A -> Link[LNKA] -> GSI 11 (level, low) -> IRQ 11
[    5.977692] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    5.977701] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    5.977880] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    5.977987] uhci_hcd 0000:00:1d.0: irq 11, io base 0x00001820
[    5.978284] usb usb2: configuration #1 chosen from 1 choice
[    5.978416] hub 2-0:1.0: USB hub found
[    5.978486] hub 2-0:1.0: 2 ports detected
[    5.979177] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 11
[    5.979245] uhci_hcd 0000:00:1d.1: PCI INT B -> Link[LNKD] -> GSI 11 (level, low) -> IRQ 11
[    5.979333] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    5.979342] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    5.979518] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3
[    5.979623] uhci_hcd 0000:00:1d.1: irq 11, io base 0x00001840
[    5.979896] usb usb3: configuration #1 chosen from 1 choice
[    5.980053] hub 3-0:1.0: USB hub found
[    5.980124] hub 3-0:1.0: 2 ports detected
[    5.980405] uhci_hcd 0000:00:1d.2: PCI INT C -> Link[LNKC] -> GSI 11 (level, low) -> IRQ 11
[    5.981464] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    5.981473] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    5.981643] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4
[    5.981748] uhci_hcd 0000:00:1d.2: irq 11, io base 0x00001860
[    5.982025] usb usb4: configuration #1 chosen from 1 choice
[    5.982156] hub 4-0:1.0: USB hub found
[    5.982225] hub 4-0:1.0: 2 ports detected
[    5.982654] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    5.985050] i8042.c: Detected active multiplexing controller, rev 1.1.
[    5.986954] serio: i8042 KBD port at 0x60,0x64 irq 1
[    5.987023] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[    5.987084] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[    5.987146] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[    5.987207] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[    5.987705] mice: PS/2 mouse device common for all mice
[    5.988187] rtc_cmos 00:01: RTC can wake from S4
[    5.988360] rtc_cmos 00:01: rtc core: registered rtc_cmos as rtc0
[    5.988444] rtc0: alarms up to one month, y3k, 242 bytes nvram
[    5.988711] device-mapper: uevent: version 1.0.3
[    5.989049] device-mapper: ioctl: 4.14.0-ioctl (2008-04-23) initialised: dm-devel@redhat.com
[    5.989256] device-mapper: multipath: version 1.0.5 loaded
[    5.989320] device-mapper: multipath round-robin: version 1.0.0 loaded
[    5.989610] EISA: Probing bus 0 at eisa.0
[    5.989677] Cannot allocate resource for EISA slot 1
[    5.989739] Cannot allocate resource for EISA slot 2
[    5.989800] Cannot allocate resource for EISA slot 3
[    5.989891] EISA: Detected 0 cards.
[    5.990118] cpuidle: using governor ladder
[    5.990352] cpuidle: using governor menu
[    5.992183] TCP cubic registered
[    5.992604] NET: Registered protocol family 10
[    5.994012] lo: Disabled Privacy Extensions
[    5.995158] NET: Registered protocol family 17
[    5.995257] Bluetooth: L2CAP ver 2.11
[    5.995313] Bluetooth: L2CAP socket layer initialized
[    5.995376] Bluetooth: SCO (Voice Link) ver 0.6
[    5.995434] Bluetooth: SCO socket layer initialized
[    5.995552] Bluetooth: RFCOMM socket layer initialized
[    5.995624] Bluetooth: RFCOMM TTY layer initialized
[    5.995684] Bluetooth: RFCOMM ver 1.10
[    5.996324] Marking TSC unstable due to cpufreq changes
[    5.996402] IO APIC resources could be not be allocated.
[    5.996425] Using IPI No-Shortcut mode
[    5.996528] registered taskstats version 1
[    5.996664]   Magic number: 1:673:595
[    5.996739] rtc_cmos 00:01: setting system clock to 2009-07-23 18:33:06 UTC (1248373986)
[    5.996770] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    5.996794] EDD information not available.
[    5.997053] Freeing unused kernel memory: 532k freed
[    5.997199] Write protecting the kernel text: 4112k
[    5.997265] Write protecting the kernel read-only data: 1524k
[    6.032879] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input4
[    6.604061] usb 2-1: new full speed USB device using uhci_hcd and address 2
[    6.780777] ohci1394 0000:02:03.0: PCI INT A -> Link[LNKF] -> GSI 10 (level, low) -> IRQ 10
[    6.920091] ohci1394: fw-host0: OHCI-1394 1.0 (PCI): IRQ=[10]  MMIO=[e0202000-e02027ff]  Max Packet=[2048]  IR/IT contexts=[8/8]
[    6.992450] usb 2-1: configuration #1 chosen from 1 choice
[    7.040427] ACPI: PCI Interrupt Link [LNKE] enabled at IRQ 10
[    7.040457] b44 0000:02:05.0: PCI INT A -> Link[LNKE] -> GSI 10 (level, low) -> IRQ 10
[    7.100090] ssb: Sonics Silicon Backplane found on PCI device 0000:02:05.0
[    7.100137] b44.c:v2.0
[    7.120817] eth0: Broadcom 44xx/47xx 10/100BaseT Ethernet 00:0a:e4:21:17:e5
[    7.596095] usbcore: registered new interface driver hiddev
[    7.601166] input: Razer Razer Copperhead Laser Mouse as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1:1.0/input/input5
[    7.611273] generic-usb 0003:1532:0101.0001: input,hidraw0: USB HID v10.01 Mouse [Razer Razer Copperhead Laser Mouse] on usb-0000:00:1d.0-1/input0
[    7.613087] input: Razer Razer Copperhead Laser Mouse as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1:1.1/input/input6
[    7.619651] generic-usb 0003:1532:0101.0002: input,hidraw1: USB HID v10.01 Keyboard [Razer Razer Copperhead Laser Mouse] on usb-0000:00:1d.0-1/input1
[    7.619704] usbcore: registered new interface driver usbhid
[    7.619730] usbhid: v2.6:USB HID core driver
[    7.697739] PM: Starting manual resume from disk
[    7.697763] PM: Resume from partition 8:5
[    7.697765] PM: Checking hibernation image.
[    7.699090] PM: Resume from disk failed.
[    7.774176] kjournald starting.  Commit interval 5 seconds
[    7.774207] EXT3-fs: mounted filesystem with ordered data mode.
[    8.316135] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[03e40a00a5012038]
[   17.072248] udev: starting version 141
[   17.304272] Linux agpgart interface v0.103
[   17.388227] agpgart-intel 0000:00:00.0: Intel 855GM Chipset
[   17.388449] agpgart-intel 0000:00:00.0: detected 8060K stolen memory
[   17.389275] agpgart-intel 0000:00:00.0: AGP aperture is 128M @ 0xe8000000
[   17.493362] wbsd: Winbond W83L51xD SD/MMC card interface driver
[   17.493389] wbsd: Copyright(c) Pierre Ossman
[   17.508578] mmc0: W83L51xD id 7112 at 0x820 irq 6 FIFO PnP
[   17.520376] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A03:00/device:03/input/input7
[   17.556331] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[   17.616792] irda_init()
[   17.616805] NET: Registered protocol family 23
[   17.636448] parport_pc 00:08: reported by Plug and Play ACPI
[   17.636494] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
[   17.736646] nsc_ircc_pnp_probe() : From PnP, found firbase 0x2F8 ; irq 3 ; dma 1.
[   17.736668] nsc-ircc, chip->init
[   17.736696] nsc-ircc, Found chip at base=0x02e
[   17.736727] nsc-ircc, driver loaded (Dag Brattli)
[   17.736751] nsc_ircc_open(), can't get iobase of 0x2f8
[   17.736784] nsc-ircc, Found chip at base=0x02e
[   17.736814] nsc-ircc, driver loaded (Dag Brattli)
[   17.736837] nsc_ircc_open(), can't get iobase of 0x2f8
[   17.737034] nsc-ircc 00:09: disabled
[   17.740980] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   17.744589] intel_rng: FWH not detected
[   17.804374] iTCO_vendor_support: vendor-support=0
[   18.080843] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.05
[   18.080978] iTCO_wdt: Found a ICH4-M TCO device (Version=1, TCOBASE=0x1060)
[   18.081077] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   18.089042] ieee80211_crypt: registered algorithm 'NULL'
[   18.117103] ieee80211: 802.11 data/management/control stack, git-1.1.13
[   18.117132] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
[   18.441263] ipw2100: Intel(R) PRO/Wireless 2100 Network Driver, git-1.2.2
[   18.441291] ipw2100: Copyright(c) 2003-2006 Intel Corporation
[   18.445006] ACPI: PCI Interrupt Link [LNKG] enabled at IRQ 10
[   18.445035] ipw2100 0000:02:06.0: PCI INT A -> Link[LNKG] -> GSI 10 (level, low) -> IRQ 10
[   18.445468] ipw2100: Detected Intel PRO/Wireless 2100 Network Connection
[   18.445503] ipw2100 0000:02:06.0: firmware: requesting ipw2100-1.3.fw
[   18.749255] input: PC Speaker as /devices/platform/pcspkr/input/input8
[   18.788064] ppdev: user-space parallel port driver
[   19.056373] synaptics was reset on resume, see synaptics_resume_reset if you have trouble on resume
[   19.300348] yenta_cardbus 0000:02:09.0: CardBus bridge found [17c0:3003]
[   19.300383] yenta_cardbus 0000:02:09.0: Using CSCINT to route CSC interrupts to PCI
[   19.300414] yenta_cardbus 0000:02:09.0: Routing CardBus interrupts to PCI
[   19.300440] yenta_cardbus 0000:02:09.0: TI: mfunc 0x01001002, devctl 0x64
[   19.396707] Intel ICH 0000:00:1f.5: PCI INT B -> Link[LNKB] -> GSI 10 (level, low) -> IRQ 10
[   19.396777] Intel ICH 0000:00:1f.5: setting latency timer to 64
[   19.532558] yenta_cardbus 0000:02:09.0: ISA IRQ mask 0x0018, PCI irq 10
[   19.532583] yenta_cardbus 0000:02:09.0: Socket status: 30000007
[   19.532607] pci_bus 0000:02: Raising subordinate bus# of parent bus (#02) from #02 to #06
[   19.532641] yenta_cardbus 0000:02:09.0: pcmcia: parent PCI bridge I/O window: 0x3000 - 0x3fff
[   19.532673] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x3000-0x3fff: clean.
[   19.532968] yenta_cardbus 0000:02:09.0: pcmcia: parent PCI bridge Memory window: 0xe0200000 - 0xe02fffff
[   19.533001] yenta_cardbus 0000:02:09.0: pcmcia: parent PCI bridge Memory window: 0x30000000 - 0x35ffffff
[   19.913525] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x100-0x3af: clean.
[   19.914254] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x3e0-0x4ff: excluding 0x4d0-0x4d7
[   19.916287] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x820-0x8ff: excluding 0x840-0x847
[   19.916965] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xc00-0xcf7: clean.
[   19.917412] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xa00-0xaff: clean.
[   20.030850] Synaptics Touchpad, model: 1, fw: 5.8, id: 0x9248b1, caps: 0x904713/0x4000
[   20.073068] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio4/input/input9
[   20.668035] intel8x0_measure_ac97_clock: measured 55248 usecs
[   20.668062] intel8x0: clocking to 48000
[   20.916036] lp0: using parport0 (interrupt-driven).
[   21.172268] Adding 1461872k swap on /dev/sda5.  Priority:-1 extents:1 across:1461872k
[   21.773462] EXT3 FS on sda1, internal journal
[   22.792169] type=1505 audit(1248374003.294:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=2017
[   22.952639] type=1505 audit(1248374003.454:3): operation="profile_load" name="/sbin/dhclient-script" name2="default" pid=2021
[   22.952762] type=1505 audit(1248374003.454:4): operation="profile_load" name="/sbin/dhclient3" name2="default" pid=2021
[   22.952813] type=1505 audit(1248374003.454:5): operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" name2="default" pid=2021
[   22.952860] type=1505 audit(1248374003.454:6): operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" name2="default" pid=2021
[   23.428546] type=1505 audit(1248374003.930:7): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=2026
[   23.428742] type=1505 audit(1248374003.930:8): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=2026
[   23.544848] type=1505 audit(1248374004.046:9): operation="profile_load" name="/usr/sbin/mysqld" name2="default" pid=2030
[   23.632049] type=1505 audit(1248374004.130:10): operation="profile_load" name="/usr/sbin/tcpdump" name2="default" pid=2034
[   33.458676] ttyS1: LSR safety check engaged!
[   37.744993] [drm] Initialized drm 1.1.0 20060810
[   37.820596] pci 0000:00:02.0: PCI INT A -> Link[LNKA] -> GSI 11 (level, low) -> IRQ 11
[   37.820602] pci 0000:00:02.0: setting latency timer to 64
[   37.820770] [drm] Initialized i915 1.6.0 20080730 on minor 0
[   37.825108] [drm:i915_setparam] *ERROR* unknown parameter 4
[   37.825129] [drm:i915_getparam] *ERROR* Unknown parameter 6
[   38.505594] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   38.509749] ADDRCONF(NETDEV_UP): eth1: link is not ready
[   39.664258] [drm:i915_getparam] *ERROR* Unknown parameter 6
[   41.816077] b44: eth0: Link is up at 100 Mbps, full duplex.
[   41.816080] b44: eth0: Flow control is off for TX and off for RX.
[   41.816405] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   52.072027] eth0: no IPv6 routers present
[   65.685134] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
[   66.665151] ieee80211_crypt: registered algorithm 'CCMP'
[   66.973542] padlock: VIA PadLock not detected.
[   67.680845] ieee80211_crypt: registered algorithm 'TKIP'
[   76.512021] eth1: no IPv6 routers present
``````
$ lspci
00:00.0 Host bridge: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:00.1 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:00.3 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
00:02.1 Display controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 83)
00:1f.0 ISA bridge: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801DBM (ICH4-M) IDE Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 03)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 03)
00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 03)
02:03.0 FireWire (IEEE 1394): Agere Systems FW323 (rev 61)
02:05.0 Ethernet controller: Broadcom Corporation BCM4401 100Base-T (rev 01)
02:06.0 Network controller: Intel Corporation PRO/Wireless LAN 2100 3B Mini PCI Adapter (rev 04)
02:09.0 CardBus bridge: Texas Instruments PCI1510 PC card Cardbus Controller
```

---

### Post by B-D_ on 2009-07-24
If no one wants to help I guess I'll have to reinstall XP+putty because Ubuntu is just way too unstable to be usefull for my work. :rolleyes: How ironic...

---

### Post by B-D_ on 2009-07-24
Rebooted again... feels like win '95 :popcorn:


I left it on for 5 minutes before rebooting.

X server hangs (desktop is dead, no clock updates, clock stuck on the same time) but mouse cursor keeps moving on the screen. Music also keeps playing stream from the internet, so audio and network keeps working.

After ctrl-alt-sysrq-R my keyboard gets me back to raw mode and I can use caps lock again, but nothing else works, not even ctrl-alt-f1 so I can't get to virtual terminals to investigate. After E music stops because it got the term signal...

Point of error is unresponsive desktop (so no clicking) and keyboard ignore until raw (so no virtual terminals or x restarts).

---

### Post by B-D_ on 2009-07-24
I am trying tricks from here, hope they help...

[http://www.ubuntu.com/getubuntu/releasenotes/904#Display%20freezes%20with%20Intel%20graphics%20cards](http://www.ubuntu.com/getubuntu/releasenotes/904#Display%20freezes%20with%20Intel%20graphics%20cards)

---

### Post by Whiffle on 2009-07-24
Maybe look in /var/log/syslog or /var/log/kern.log (or any of the other log files in there), there might be some clues.

---

### Post by B-D_ on 2009-07-24
Checked, found something just before reboot:

```
Jul 24 13:59:09 bidi-laptop kernel: [   41.816081] b44: eth0: Link is up at 100 Mbps, full duplex.
Jul 24 13:59:09 bidi-laptop kernel: [   41.816085] b44: eth0: Flow control is off for TX and off for RX.
Jul 24 13:59:09 bidi-laptop kernel: [   41.816160] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
Jul 24 13:59:19 bidi-laptop kernel: [   52.220030] eth0: no IPv6 routers present
Jul 24 13:59:32 bidi-laptop kernel: [   64.696716] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
Jul 24 13:59:33 bidi-laptop kernel: [   65.692837] ieee80211_crypt: registered algorithm 'CCMP'
Jul 24 13:59:33 bidi-laptop kernel: [   65.976573] padlock: VIA PadLock not detected.
Jul 24 13:59:34 bidi-laptop kernel: [   66.620651] ieee80211_crypt: registered algorithm 'TKIP'
Jul 24 13:59:43 bidi-laptop kernel: [   75.664033] eth1: no IPv6 routers present
Jul 24 14:21:53 bidi-laptop kernel: [ 1405.846836] [drm:i915_getparam] *ERROR* Unknown parameter 6
Jul 24 14:23:54 bidi-laptop kernel: [ 1527.008960] mtrr: no MTRR for e8000000,8000000 found
Jul 24 14:24:45 bidi-laptop kernel: Inspecting /boot/System.map-2.6.28-14-generic
Jul 24 14:24:46 bidi-laptop kernel: Cannot find map file.
Jul 24 14:24:46 bidi-laptop kernel: Loaded 55699 symbols from 55 modules.
Jul 24 14:24:46 bidi-laptop kernel: [    0.000000] BIOS EBDA/lowmem at: 0009f800/0009f800
Jul 24 14:24:46 bidi-laptop kernel: [    0.000000] Initializing cgroup subsys cpuset
Jul 24 14:24:46 bidi-laptop kernel: [    0.000000] Initializing cgroup subsys cpu

```

---

### Post by Whiffle on 2009-07-24
I think I would give this a shot, the Intel drivers seems to be all kinds of screwed up on Jaunty.
[https://wiki.ubuntu.com/ReinhardTartler/X/RevertingIntelDriverTo2.4](https://wiki.ubuntu.com/ReinhardTartler/X/RevertingIntelDriverTo2.4)

---

### Post by B-D_ on 2009-07-24
Thanks for the tip, I reverted my drivers now.

If it crashes again I'll try to skip over Jaunty and upgrade to Koala because people on forums are saying the problem is much deeper than drivers (in the core) but resolved in next distro.

---

### Post by wabbalee on 2009-07-24
What is the brand and type of your laptop? I have and Acer TM2480 and I have an almost similar problem and it does not only happen in Linux; I am very rarely on XP but since I am doing some work in MS ACCESS, purely to learn a little about databases I have been in XP a few times and noticed that the same problem occurs there too: my system goes into a waiting mode for periods of no more than one minute or less at random intervals. It has been doing this from day one, about three years ago when I got it new. Acer technicians were unable to even discover the problem let alone fixing it. The mouse remains moveable during this time every click I do in this time seems ignored but after the period of waiting is over it turns out that all clicks and keystrokes are registered and executed. streams continue to work like with your system. If I watch a movie or listen to music from the harddrive this can be particularly annoying as it will just stop and go again after the period of waiting time. The workaround for watching movies for me is to run the movie or music file from usb stick. That said lets one think there is a problem with the harddrive, but I am pretty certain that this is not the case as this is the third harddrive and they all had it. there is nothing wrong with the other two harddrives except their small capacity which is why I am not using those any more.

what I did to monitor what happens is to run a cli program named 'top', it gives a dynamic list of services and programs active on the system, everytime I had this happens to me it is at 100%WA (wa for waiting?) unfortunately I was unable to resolve this problem, which is most likely a hardware related problem. 

> like it's waiting for I/O.

sounds very familiar and I think there is something with the bus. this laptop has a celeron cpu, what does yours have? I have two other laptops in this house that run Hardy but with mobile centrino cpu's and they do not even show the slightest bit of this problem.

so what are your specs?

Ron

---

### Post by B-D_ on 2009-07-24
My specs are in lspci above, laptop is some rebranded noname.

Proc is Pentium M 1600 and works fine in windows XP with no problems. It also worked fine on older distros, debian, knoppix... guess my problem is Jaunty specific.

---

### Post by wabbalee on 2009-07-24
I have wrestled myself through your dmesg output, comparing it to mine. There were a few things that caught my attention but since I have no fix/solution I can only point them out to you:

```
[    0.000000] Phoenix BIOS detected: BIOS may corrupt low RAM, working it around.
[    0.000000] last_pfn = 0x1f6e0 max_arch_pfn = 0x100000
[    0.000000] Scanning 0 areas for low memory corruption
[    0.000000] modified physical RAM map:
[    0.000000]  modified: 0000000000000000 - 0000000000010000 (reserved)
[    0.000000]  modified: 0000000000010000 - 000000000009f800 (usable)
[    0.000000]  modified: 000000000009f800 - 00000000000a0000 (reserved)
[    0.000000]  modified: 00000000000ce000 - 00000000000d0000 (reserved)
[    0.000000]  modified: 00000000000d8000 - 0000000000100000 (reserved)
[    0.000000]  modified: 0000000000100000 - 000000001f6e0000 (usable)
[    0.000000]  modified: 000000001f6e0000 - 000000001f6eb000 (ACPI data)
[    0.000000]  modified: 000000001f6eb000 - 000000001f700000 (ACPI NVS)
[    0.000000]  modified: 000000001f700000 - 0000000020000000 (reserved)
[    0.000000]  modified: 00000000fec10000 - 00000000fec20000 (reserved)
[    0.000000]  modified: 00000000ff800000 - 00000000ffc00000 (reserved)
[    0.000000]  modified: 00000000fffffc00 - 0000000100000000 (reserved)
```
'BIOS may corrupt low RAM' sounds a bit strange to me, no such line in my dmesg.

yours:
```
weird, boot CPU (#0) not listedby the BIOS.
SMP motherboard not detected.
[    1.332234] Local APIC not detected. Using dummy APIC emulation.
[    1.332296] SMP disabled
[    1.332983] Brought up 1 CPUs
[    1.333042] Total of 1 processors activated (1199.81 BogoMIPS).
[    1.333128] CPU0 attaching NULL sched-domain.
[    1.333688] net_namespace: 776 bytes
```

mine:
```
[    0.539257] CPU0: Intel(R) Celeron(R) M CPU        430  @ 1.73GHz stepping 08                                                                             
[    0.540002] Brought up 1 CPUs                                                                                                                             
[    0.540002] Total of 1 processors activated (3467.31 BogoMIPS).                                                                                           
[    0.540002] CPU0 attaching NULL sched-domain.                                                                                                             
[    0.540002] net_namespace: 776 bytes 
```


and last but not least and possibly (y)our problem:
```
[drm] Initialized i915 1.6.0 20080730 on minor 0
[   37.825108] [drm:i915_setparam] *ERROR* unknown parameter 4
[   37.825129] [drm:i915_getparam] *ERROR* Unknown parameter 6
[   38.505594] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   38.509749] ADDRCONF(NETDEV_UP): eth1: link is not ready
[   39.664258] [drm:i915_getparam] *ERROR* Unknown parameter 6
```
I am referring to the i915 error, which is similar to mine.

and then I would like to comment on this:
> If no one wants to help I guess I'll have to reinstall XP+putty because Ubuntu is just way too unstable to be usefull for my work.  How ironic...

although I do not quite understand what the irony is, I would like to stipulate that Ubuntu and Linux in general is free of any cost. All help given on these forums is voluntary done by its users and developers; nobody tells anybody to go here and help others. In my case I really *want* to help you resolve your issue but I do not *know* how.

I have been using Linux for 6 or 7 years now and it hasn't always been the 'easy' way but I have learned a great deal about this wonderful OS and its philosophy, it is a way of life and I have gained knowledge from lots of people that I do not even know. In return I have managed to help a handful of people myself and it all becomes part of the overall Linux experience, something far sought in the mad and costly world of Windows.

all the best
Ron

---

### Post by B-D_ on 2009-07-25
Irony is that in my case windows would be more stable than Linux if I couldn't resolve the issue... 


I guess the problem was with the driver because I haven't had a problem since I downgraded to 2.4 version of Intel graphic driver.

Thanks to everyone for support :KS

---

### Post by cooper77z on 2009-07-25
I don't think the driver is the problem, the hardware just isn't digital, or there is some type of encryption. Just guessing ? Perhaps you need better hardware?

---

### Post by jimbean on 2009-08-08
have you looked in your bios for things 
like if you don`t use your usb for more than 10 minutes its put into a energy saving mode to save battery life or checked to see if your computers advanced power management {apm} is compatible with linux

---

