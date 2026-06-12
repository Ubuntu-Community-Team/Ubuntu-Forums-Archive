---
title: "no sound"
date: 2009-05-29
forum: Hardware
---

### Post by tommah04 on 2009-05-29
hey all...

I talked my friend into getting ubuntu and now I feel bad cause I can't get sound to work on his laptop...

I pretty much tried everything on this troubleshooting page..
[https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting)

ubuntu recognizes my card and its installed
but still no sound through speakers or headphones....any ideas?

*edit*
sorry, this is my info 
jaunty
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 03)

---

### Post by tommah04 on 2009-05-30
bump?

---

### Post by albinootje on 2009-05-30
> **tommah04 said:**
> 
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 03)

Can you also post the output of :
```

aplay -l
alsactl -v
dmesg

```
And this is a laptop ? If so, please provide the brand name and the exact type.
And you did start "alsamixer" and checked the volume ?

---

### Post by tommah04 on 2009-05-31
tweak@tweak-laptop:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: I82801DBICH4 [Intel 82801DB-ICH4], device 0: Intel ICH [Intel 82801DB-ICH4]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: I82801DBICH4 [Intel 82801DB-ICH4], device 4: Intel ICH - IEC958 [Intel 82801DB-ICH4 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0



tweak@tweak-laptop:~$ alsactl -v
alsactl version 1.0.18



tweak@tweak-laptop:~$ dmesg
[    0.000000] BIOS EBDA/lowmem at: 0009f800/0009f800
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.28-11-generic (buildd@palmer) (gcc version 4.3.3 (Ubuntu 4.3.3-5ubuntu4) ) #42-Ubuntu SMP Fri Apr 17 01:57:59 UTC 2009 (Ubuntu 2.6.28-11.42-generic)
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
[    0.000000]  BIOS-e820: 00000000000dc000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000001dee0000 (usable)
[    0.000000]  BIOS-e820: 000000001dee0000 - 000000001deeb000 (ACPI data)
[    0.000000]  BIOS-e820: 000000001deeb000 - 000000001df00000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000001df00000 - 0000000020000000 (reserved)
[    0.000000]  BIOS-e820: 00000000ff800000 - 00000000ffc00000 (reserved)
[    0.000000]  BIOS-e820: 00000000fffffc00 - 0000000100000000 (reserved)
[    0.000000] DMI present.
[    0.000000] last_pfn = 0x1dee0 max_arch_pfn = 0x100000
[    0.000000] Scanning 2 areas for low memory corruption
[    0.000000] modified physical RAM map:
[    0.000000]  modified: 0000000000000000 - 0000000000002000 (usable)
[    0.000000]  modified: 0000000000002000 - 0000000000006000 (reserved)
[    0.000000]  modified: 0000000000006000 - 0000000000007000 (usable)
[    0.000000]  modified: 0000000000007000 - 0000000000010000 (reserved)
[    0.000000]  modified: 0000000000010000 - 0000000000092800 (usable)
[    0.000000]  modified: 000000000009f800 - 00000000000a0000 (reserved)
[    0.000000]  modified: 00000000000ce000 - 00000000000d0000 (reserved)
[    0.000000]  modified: 00000000000dc000 - 0000000000100000 (reserved)
[    0.000000]  modified: 0000000000100000 - 000000001dee0000 (usable)
[    0.000000]  modified: 000000001dee0000 - 000000001deeb000 (ACPI data)
[    0.000000]  modified: 000000001deeb000 - 000000001df00000 (ACPI NVS)
[    0.000000]  modified: 000000001df00000 - 0000000020000000 (reserved)
[    0.000000]  modified: 00000000ff800000 - 00000000ffc00000 (reserved)
[    0.000000]  modified: 00000000fffffc00 - 0000000100000000 (reserved)
[    0.000000] kernel direct mapping tables up to 1dee0000 @ 10000-16000
[    0.000000] RAMDISK: 1d79f000 - 1decffe6
[    0.000000] ACPI: RSDP 000F7780, 0014 (r0 PTLTD )
[    0.000000] ACPI: RSDT 1DEE69CD, 0030 (r1 PTLTD  ManiaDth  6040000  LTP        0)
[    0.000000] ACPI: FACP 1DEEAEC4, 0074 (r1 INTEL  MONTARA   6040000 PTL        50)
[    0.000000] ACPI: DSDT 1DEE6F0E, 3FB6 (r1 INTEL  MONTARAG  6040000 MSFT  100000E)
[    0.000000] ACPI: FACS 1DEFBFC0, 0040
[    0.000000] ACPI: BOOT 1DEEAFD8, 0028 (r1 PTLTD  $SBFTBL$  6040000  LTP        1)
[    0.000000] ACPI: SSDT 1DEE6DFD, 0109 (r1 INTEL  CPU0CST         1 INTL 20030224)
[    0.000000] 0MB HIGHMEM available.
[    0.000000] 478MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 1dee0000
[    0.000000]   low ram: 00000000 - 1dee0000
[    0.000000]   bootmap 00012000 - 00015bdc
[    0.000000] (9 early reservations) ==> bootmem [0000000000 - 001dee0000]
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000]   #1 [0000001000 - 0000002000]    EX TRAMPOLINE ==> [0000001000 - 0000002000]
[    0.000000]   #2 [0000006000 - 0000007000]       TRAMPOLINE ==> [0000006000 - 0000007000]
[    0.000000]   #3 [0000100000 - 000087c52c]    TEXT DATA BSS ==> [0000100000 - 000087c52c]
[    0.000000]   #4 [001d79f000 - 001decffe6]          RAMDISK ==> [001d79f000 - 001decffe6]
[    0.000000]   #5 [000087d000 - 0000881000]    INIT_PG_TABLE ==> [000087d000 - 0000881000]
[    0.000000]   #6 [000009f800 - 0000100000]    BIOS reserved ==> [000009f800 - 0000100000]
[    0.000000]   #7 [0000010000 - 0000012000]          PGTABLE ==> [0000010000 - 0000012000]
[    0.000000]   #8 [0000012000 - 0000016000]          BOOTMAP ==> [0000012000 - 0000016000]
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000000 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x0001dee0
[    0.000000]   HighMem  0x0001dee0 -> 0x0001dee0
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[4] active PFN ranges
[    0.000000]     0: 0x00000000 -> 0x00000002
[    0.000000]     0: 0x00000006 -> 0x00000007
[    0.000000]     0: 0x00000010 -> 0x00000092
[    0.000000]     0: 0x00000100 -> 0x0001dee0
[    0.000000] On node 0 totalpages: 122469
[    0.000000] free_area_init_node: node 0, pgdat c06d0f80, node_mem_map c1000000
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3941 pages, LIFO batch:0
[    0.000000]   Normal zone: 926 pages used for memmap
[    0.000000]   Normal zone: 117570 pages, LIFO batch:31
[    0.000000]   HighMem zone: 0 pages used for memmap
[    0.000000]   Movable zone: 0 pages used for memmap
[    0.000000] ACPI: PM-Timer IO Port: 0x1008
[    0.000000] SMP: Allowing 1 CPUs, 0 hotplug CPUs
[    0.000000] Local APIC disabled by BIOS -- you can enable it with "lapic"
[    0.000000] PM: Registered nosave memory: 0000000000002000 - 0000000000006000
[    0.000000] PM: Registered nosave memory: 0000000000007000 - 0000000000010000
[    0.000000] PM: Registered nosave memory: 0000000000092000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000ce000
[    0.000000] PM: Registered nosave memory: 00000000000ce000 - 00000000000d0000
[    0.000000] PM: Registered nosave memory: 00000000000d0000 - 00000000000dc000
[    0.000000] PM: Registered nosave memory: 00000000000dc000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 30000000 (gap: 20000000:df800000)
[    0.000000] PERCPU: Allocating 45056 bytes of per cpu data
[    0.000000] NR_CPUS: 64, nr_cpu_ids: 1, nr_node_ids 1
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 121511
[    0.000000] Kernel command line: root=UUID=1ea2f819-e7d2-43e6-bc61-2a9f6b088f46 ro quiet splash 
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 2048 (order: 11, 8192 bytes)
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 1395.591 MHz processor.
[    0.004000] Console: colour VGA+ 80x25
[    0.004000] console [tty0] enabled
[    0.004000] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.004000] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.004000] allocated 2451840 bytes of page_cgroup
[    0.004000] please try cgroup_disable=memory option if you don't want
[    0.004000] Scanning for low memory corruption every 60 seconds
[    0.004000] Memory: 467816k/490368k available (4126k kernel code, 21780k reserved, 2208k data, 532k init, 0k highmem)
[    0.004000] virtual kernel memory layout:
[    0.004000]     fixmap  : 0xffc77000 - 0xfffff000   (3616 kB)
[    0.004000]     pkmap   : 0xff400000 - 0xff800000   (4096 kB)
[    0.004000]     vmalloc : 0xde6e0000 - 0xff3fe000   ( 525 MB)
[    0.004000]     lowmem  : 0xc0000000 - 0xddee0000   ( 478 MB)
[    0.004000]       .init : 0xc0737000 - 0xc07bc000   ( 532 kB)
[    0.004000]       .data : 0xc0507a6f - 0xc072fe60   (2208 kB)
[    0.004000]       .text : 0xc0100000 - 0xc0507a6f   (4126 kB)
[    0.004000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.004000] SLUB: Genslabs=12, HWalign=64, Order=0-3, MinObjects=0, CPUs=1, Nodes=1
[    0.004014] Calibrating delay loop (skipped), value calculated using timer frequency.. 2791.18 BogoMIPS (lpj=5582364)
[    0.004036] Security Framework initialized
[    0.004047] SELinux:  Disabled at boot.
[    0.004072] AppArmor: AppArmor initialized
[    0.004082] Mount-cache hash table entries: 512
[    0.004244] Initializing cgroup subsys ns
[    0.004250] Initializing cgroup subsys cpuacct
[    0.004254] Initializing cgroup subsys memory
[    0.004259] Initializing cgroup subsys freezer
[    0.004277] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.004281] CPU: L2 cache: 1024K
[    0.004296] Checking 'hlt' instruction... OK.
[    0.020844] SMP alternatives: switching to UP code
[    0.160611] Freeing SMP alternatives: 18k freed
[    0.160616] ACPI: Core revision 20080926
[    0.162950] ACPI: Checking initramfs for custom DSDT
[    0.584664] ACPI: setting ELCR to 0200 (from 0c28)
[    0.588072] weird, boot CPU (#0) not listedby the BIOS.
[    0.588075] SMP motherboard not detected.
[    0.588079] Local APIC not detected. Using dummy APIC emulation.
[    0.588081] SMP disabled
[    0.588387] Brought up 1 CPUs
[    0.588391] Total of 1 processors activated (2791.18 BogoMIPS).
[    0.588407] CPU0 attaching NULL sched-domain.
[    0.588764] net_namespace: 776 bytes
[    0.588778] Booting paravirtualized kernel on bare hardware
[    0.592010] Time: 20:41:36  Date: 05/30/09
[    0.592017] regulator: core version 0.5
[    0.592060] NET: Registered protocol family 16
[    0.592221] EISA bus registered
[    0.592240] ACPI: bus type pci registered
[    0.592744] PCI: PCI BIOS revision 2.10 entry at 0xfd932, last bus=2
[    0.592748] PCI: Using configuration type 1 for base access
[    0.594600] ACPI: EC: Look up EC in DSDT
[    0.597317] ACPI: Interpreter enabled
[    0.597323] ACPI: (supports S0 S3 S4 S5)
[    0.597345] ACPI: Using PIC for interrupt routing
[    0.597747] ACPI: EC: non-query interrupt received, switching to interrupt mode
[    0.601344] ACPI: EC: GPE = 0x1c, I/O: command/status = 0x66, data = 0x62
[    0.601348] ACPI: EC: driver started in interrupt mode
[    0.601478] ACPI: No dock devices found.
[    0.601494] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.601640] pci 0000:00:02.0: reg 10 32bit mmio: [0xe8000000-0xefffffff]
[    0.601646] pci 0000:00:02.0: reg 14 32bit mmio: [0xe0000000-0xe007ffff]
[    0.601652] pci 0000:00:02.0: reg 18 io port: [0x1800-0x1807]
[    0.601669] pci 0000:00:02.0: supports D1
[    0.601688] pci 0000:00:02.1: reg 10 32bit mmio: [0xf0000000-0xf7ffffff]
[    0.601694] pci 0000:00:02.1: reg 14 32bit mmio: [0xe0080000-0xe00fffff]
[    0.601713] pci 0000:00:02.1: supports D1
[    0.601783] pci 0000:00:1d.0: reg 20 io port: [0x1820-0x183f]
[    0.601833] pci 0000:00:1d.1: reg 20 io port: [0x1840-0x185f]
[    0.601881] pci 0000:00:1d.2: reg 20 io port: [0x1860-0x187f]
[    0.601936] pci 0000:00:1d.7: reg 10 32bit mmio: [0xe0100000-0xe01003ff]
[    0.601978] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
[    0.601984] pci 0000:00:1d.7: PME# disabled
[    0.602060] HPET not enabled in BIOS. You might try hpet=force boot option
[    0.602067] pci 0000:00:1f.0: quirk: region 1000-107f claimed by ICH4 ACPI/GPIO/TCO
[    0.602072] pci 0000:00:1f.0: quirk: region 1180-11bf claimed by ICH4 GPIO
[    0.602092] pci 0000:00:1f.1: reg 10 io port: [0x00-0x07]
[    0.602099] pci 0000:00:1f.1: reg 14 io port: [0x00-0x03]
[    0.602106] pci 0000:00:1f.1: reg 18 io port: [0x00-0x07]
[    0.602114] pci 0000:00:1f.1: reg 1c io port: [0x00-0x03]
[    0.602121] pci 0000:00:1f.1: reg 20 io port: [0x1810-0x181f]
[    0.602128] pci 0000:00:1f.1: reg 24 32bit mmio: [0x000000-0x0003ff]
[    0.602175] pci 0000:00:1f.3: reg 20 io port: [0x1880-0x189f]
[    0.602214] pci 0000:00:1f.5: reg 10 io port: [0x1c00-0x1cff]
[    0.602221] pci 0000:00:1f.5: reg 14 io port: [0x18c0-0x18ff]
[    0.602229] pci 0000:00:1f.5: reg 18 32bit mmio: [0xe0100c00-0xe0100dff]
[    0.602236] pci 0000:00:1f.5: reg 1c 32bit mmio: [0xe0100800-0xe01008ff]
[    0.602257] pci 0000:00:1f.5: PME# supported from D0 D3hot D3cold
[    0.602262] pci 0000:00:1f.5: PME# disabled
[    0.602290] pci 0000:00:1f.6: reg 10 io port: [0x2400-0x24ff]
[    0.602298] pci 0000:00:1f.6: reg 14 io port: [0x2000-0x207f]
[    0.602326] pci 0000:00:1f.6: PME# supported from D0 D3hot D3cold
[    0.602331] pci 0000:00:1f.6: PME# disabled
[    0.602374] pci 0000:02:07.0: reg 10 32bit mmio: [0x000000-0x000fff]
[    0.602383] pci 0000:02:07.0: supports D1 D2
[    0.602385] pci 0000:02:07.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.602390] pci 0000:02:07.0: PME# disabled
[    0.602419] pci 0000:02:07.1: reg 10 32bit mmio: [0x000000-0x000fff]
[    0.602429] pci 0000:02:07.1: supports D1 D2
[    0.602431] pci 0000:02:07.1: PME# supported from D0 D1 D2 D3hot D3cold
[    0.602436] pci 0000:02:07.1: PME# disabled
[    0.602465] pci 0000:02:07.2: reg 10 32bit mmio: [0xe0202000-0xe02027ff]
[    0.602498] pci 0000:02:07.2: PME# supported from D0 D3hot D3cold
[    0.602502] pci 0000:02:07.2: PME# disabled
[    0.602536] pci 0000:02:08.0: reg 10 io port: [0x3000-0x30ff]
[    0.602544] pci 0000:02:08.0: reg 14 32bit mmio: [0xe0202800-0xe02028ff]
[    0.602573] pci 0000:02:08.0: supports D1 D2
[    0.602576] pci 0000:02:08.0: PME# supported from D1 D2 D3hot D3cold
[    0.602581] pci 0000:02:08.0: PME# disabled
[    0.602601] pci 0000:02:09.0: reg 10 32bit mmio: [0xe0200000-0xe0201fff]
[    0.602653] pci 0000:00:1e.0: transparent bridge
[    0.602659] pci 0000:00:1e.0: bridge io port: [0x3000-0x3fff]
[    0.602664] pci 0000:00:1e.0: bridge 32bit mmio: [0xe0200000-0xe02fffff]
[    0.602705] bus 00 -> node 0
[    0.602713] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.603052] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIB._PRT]
[    0.606212] ACPI: PCI Interrupt Link [LNKA] (IRQs *5)
[    0.606342] ACPI: PCI Interrupt Link [LNKB] (IRQs *10)
[    0.606468] ACPI: PCI Interrupt Link [LNKC] (IRQs *10)
[    0.606593] ACPI: PCI Interrupt Link [LNKD] (IRQs *11)
[    0.606717] ACPI: PCI Interrupt Link [LNKE] (IRQs 1 3 4 5 6 7 10 12 14 15) *0, disabled.
[    0.606851] ACPI: PCI Interrupt Link [LNKF] (IRQs 1 3 4 5 6 7 11 12 14 15) *0, disabled.
[    0.606983] ACPI: PCI Interrupt Link [LNKG] (IRQs 1 3 4 5 6 7 10 12 14 15) *0, disabled.
[    0.607115] ACPI: PCI Interrupt Link [LNKH] (IRQs 1 *3 4 5 6 7 11 12 14 15)
[    0.607261] ACPI: WMI: Mapper loaded
[    0.607486] SCSI subsystem initialized
[    0.607536] libata version 3.00 loaded.
[    0.607598] usbcore: registered new interface driver usbfs
[    0.607620] usbcore: registered new interface driver hub
[    0.607652] usbcore: registered new device driver usb
[    0.607793] PCI: Using ACPI for IRQ routing
[    0.607904] Bluetooth: Core ver 2.13
[    0.607904] NET: Registered protocol family 31
[    0.607904] Bluetooth: HCI device and connection manager initialized
[    0.607904] Bluetooth: HCI socket layer initialized
[    0.607904] NET: Registered protocol family 8
[    0.607904] NET: Registered protocol family 20
[    0.608020] NetLabel: Initializing
[    0.608022] NetLabel:  domain hash size = 128
[    0.608024] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.608042] NetLabel:  unlabeled traffic allowed by default
[    0.608136] AppArmor: AppArmor Filesystem Enabled
[    0.608147] pnp: PnP ACPI init
[    0.608147] ACPI: bus type pnp registered
[    0.609831] pnp: PnP ACPI: found 8 devices
[    0.609834] ACPI: ACPI bus type pnp unregistered
[    0.609839] PnPBIOS: Disabled by ACPI PNP
[    0.609853] system 00:04: ioport range 0x600-0x60f has been reserved
[    0.609857] system 00:04: ioport range 0x700-0x70f has been reserved
[    0.609861] system 00:04: ioport range 0x800-0x80f has been reserved
[    0.609864] system 00:04: ioport range 0x1000-0x107f has been reserved
[    0.609868] system 00:04: ioport range 0x1180-0x11bf has been reserved
[    0.609873] system 00:04: iomem range 0xfec10000-0xfec1ffff has been reserved
[    0.609877] system 00:04: iomem range 0xe0000000-0xefffffff could not be reserved
[    0.645069] pci 0000:02:07.0: CardBus bridge, secondary bus 0000:03
[    0.645072] pci 0000:02:07.0:   IO window: 0x003400-0x0034ff
[    0.645078] pci 0000:02:07.0:   IO window: 0x003800-0x0038ff
[    0.645083] pci 0000:02:07.0:   PREFETCH window: 0x30000000-0x33ffffff
[    0.645088] pci 0000:02:07.0:   MEM window: 0x3c000000-0x3fffffff
[    0.645093] pci 0000:02:07.1: CardBus bridge, secondary bus 0000:07
[    0.645096] pci 0000:02:07.1:   IO window: 0x003c00-0x003cff
[    0.645100] pci 0000:02:07.1:   IO window: 0x001400-0x0014ff
[    0.645105] pci 0000:02:07.1:   PREFETCH window: 0x34000000-0x37ffffff
[    0.645110] pci 0000:02:07.1:   MEM window: 0x40000000-0x43ffffff
[    0.645115] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:02
[    0.645119] pci 0000:00:1e.0:   IO window: 0x3000-0x3fff
[    0.645125] pci 0000:00:1e.0:   MEM window: 0xe0200000-0xe02fffff
[    0.645131] pci 0000:00:1e.0:   PREFETCH window: 0x00000030000000-0x00000037ffffff
[    0.645146] pci 0000:00:1e.0: setting latency timer to 64
[    0.645349] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 11
[    0.645352] PCI: setting IRQ 11 as level-triggered
[    0.645358] pci 0000:02:07.0: PCI INT A -> Link[LNKD] -> GSI 11 (level, low) -> IRQ 11
[    0.645364] pci 0000:02:07.0: setting latency timer to 64
[    0.645552] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 10
[    0.645555] PCI: setting IRQ 10 as level-triggered
[    0.645560] pci 0000:02:07.1: PCI INT B -> Link[LNKB] -> GSI 10 (level, low) -> IRQ 10
[    0.645565] pci 0000:02:07.1: setting latency timer to 64
[    0.645571] bus: 00 index 0 io port: [0x00-0xffff]
[    0.645574] bus: 00 index 1 mmio: [0x000000-0xffffffff]
[    0.645577] bus: 02 index 0 io port: [0x3000-0x3fff]
[    0.645580] bus: 02 index 1 mmio: [0xe0200000-0xe02fffff]
[    0.645583] bus: 02 index 2 mmio: [0x30000000-0x37ffffff]
[    0.645586] bus: 02 index 3 io port: [0x00-0xffff]
[    0.645589] bus: 02 index 4 mmio: [0x000000-0xffffffff]
[    0.645592] bus: 03 index 0 io port: [0x3400-0x34ff]
[    0.645595] bus: 03 index 1 io port: [0x3800-0x38ff]
[    0.645598] bus: 03 index 2 mmio: [0x30000000-0x33ffffff]
[    0.645601] bus: 03 index 3 mmio: [0x3c000000-0x3fffffff]
[    0.645604] bus: 07 index 0 io port: [0x3c00-0x3cff]
[    0.645607] bus: 07 index 1 io port: [0x1400-0x14ff]
[    0.645610] bus: 07 index 2 mmio: [0x34000000-0x37ffffff]
[    0.645613] bus: 07 index 3 mmio: [0x40000000-0x43ffffff]
[    0.645625] NET: Registered protocol family 2
[    0.645764] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
[    0.646038] TCP established hash table entries: 16384 (order: 5, 131072 bytes)
[    0.646167] TCP bind hash table entries: 16384 (order: 5, 131072 bytes)
[    0.646299] TCP: Hash tables configured (established 16384 bind 16384)
[    0.646303] TCP reno registered
[    0.646387] NET: Registered protocol family 1
[    0.646546] checking if image is initramfs... it is
[    1.148014] Switched to high resolution mode on CPU 0
[    1.510328] Freeing initrd memory: 7363k freed
[    1.510396] Simple Boot Flag at 0x36 set to 0x1
[    1.510436] cpufreq: No nForce2 chipset.
[    1.510635] audit: initializing netlink socket (disabled)
[    1.510664] type=2000 audit(1243716096.508:1): initialized
[    1.521110] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    1.522837] VFS: Disk quotas dquot_6.5.1
[    1.522922] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    1.523727] fuse init (API version 7.10)
[    1.523832] msgmni has been set to 928
[    1.524110] alg: No test for stdrng (krng)
[    1.524126] io scheduler noop registered
[    1.524129] io scheduler anticipatory registered
[    1.524131] io scheduler deadline registered
[    1.524151] io scheduler cfq registered (default)
[    1.524174] pci 0000:00:02.0: Boot video device
[    1.526596] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    1.526608] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    1.527087] ACPI: AC Adapter [AC] (on-line)
[    1.555958] ACPI: Battery Slot [BAT0] (battery present)
[    1.556065] input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input0
[    1.556069] ACPI: Power Button (FF) [PWRF]
[    1.556126] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input1
[    1.556947] ACPI: Lid Switch [LID0]
[    1.557013] input: Sleep Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input2
[    1.557020] ACPI: Sleep Button (CM) [SLPB]
[    1.557073] input: Power Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input3
[    1.557078] ACPI: Power Button (CM) [PWRB]
[    1.557457] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[    1.557490] processor ACPI_CPU:00: registered as cooling_device0
[    1.557494] ACPI: Processor [CPU0] (supports 8 throttling states)
[    1.559377] thermal LNXTHERM:01: registered as thermal_zone0
[    1.560070] ACPI: Thermal Zone [THRM] (42 C)
[    1.560122] isapnp: Scanning for PnP cards...
[    1.913711] isapnp: No Plug & Play device found
[    1.915225] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
[    1.915626] serial 0000:00:1f.6: PCI INT B -> Link[LNKB] -> GSI 10 (level, low) -> IRQ 10
[    1.915634] serial 0000:00:1f.6: PCI INT B disabled
[    1.916517] brd: module loaded
[    1.916909] loop: module loaded
[    1.917007] Fixed MDIO Bus: probed
[    1.917015] PPP generic driver version 2.4.2
[    1.917089] input: Macintosh mouse button emulation as /devices/virtual/input/input4
[    1.917123] Driver 'sd' needs updating - please use bus_type methods
[    1.917135] Driver 'sr' needs updating - please use bus_type methods
[    1.917231] ata_piix 0000:00:1f.1: version 2.12
[    1.917239] ata_piix 0000:00:1f.1: enabling device (0005 -> 0007)
[    1.917469] ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 10
[    1.917474] ata_piix 0000:00:1f.1: PCI INT A -> Link[LNKC] -> GSI 10 (level, low) -> IRQ 10
[    1.917520] ata_piix 0000:00:1f.1: setting latency timer to 64
[    1.917634] scsi0 : ata_piix
[    1.917868] scsi1 : ata_piix
[    1.919156] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0x1810 irq 14
[    1.919160] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x1818 irq 15
[    2.080446] ata1.00: ATA-5: HITACHI_DK23FA-60, 00M4A0A2, max UDMA/100
[    2.080450] ata1.00: 117210240 sectors, multi 16: LBA 
[    2.096355] ata1.00: configured for UDMA/100
[    2.260287] ata2.00: ATAPI: TSSTcorpCD/DVDW TS-L532A, TI51, max UDMA/33
[    2.276257] ata2.00: configured for UDMA/33
[    2.276532] scsi 0:0:0:0: Direct-Access     ATA      HITACHI_DK23FA-6 00M4 PQ: 0 ANSI: 5
[    2.276661] sd 0:0:0:0: [sda] 117210240 512-byte hardware sectors: (60.0 GB/55.8 GiB)
[    2.276683] sd 0:0:0:0: [sda] Write Protect is off
[    2.276686] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    2.276719] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.276798] sd 0:0:0:0: [sda] 117210240 512-byte hardware sectors: (60.0 GB/55.8 GiB)
[    2.276816] sd 0:0:0:0: [sda] Write Protect is off
[    2.276819] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    2.276850] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.276856]  sda: sda1 sda2 < sda5 >
[    2.332580] sd 0:0:0:0: [sda] Attached SCSI disk
[    2.332638] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    2.333238] scsi 1:0:0:0: CD-ROM            TSSTcorp CD/DVDW TS-L532A TI51 PQ: 0 ANSI: 5
[    2.333745] sr0: scsi3-mmc drive: 24x/24x writer cd/rw xa/form2 cdda tray
[    2.333750] Uniform CD-ROM driver Revision: 3.20
[    2.333857] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    2.333902] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    2.334686] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    2.334925] ACPI: PCI Interrupt Link [LNKH] enabled at IRQ 3
[    2.334929] PCI: setting IRQ 3 as level-triggered
[    2.334934] ehci_hcd 0000:00:1d.7: PCI INT D -> Link[LNKH] -> GSI 3 (level, low) -> IRQ 3
[    2.334965] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    2.334969] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    2.335062] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 1
[    2.338978] ehci_hcd 0000:00:1d.7: debug port 1
[    2.338985] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
[    2.338997] ehci_hcd 0000:00:1d.7: irq 3, io mem 0xe0100000
[    2.352026] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    2.352114] usb usb1: configuration #1 chosen from 1 choice
[    2.352149] hub 1-0:1.0: USB hub found
[    2.352160] hub 1-0:1.0: 6 ports detected
[    2.352301] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    2.352322] uhci_hcd: USB Universal Host Controller Interface driver
[    2.352558] ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 5
[    2.352562] PCI: setting IRQ 5 as level-triggered
[    2.352567] uhci_hcd 0000:00:1d.0: PCI INT A -> Link[LNKA] -> GSI 5 (level, low) -> IRQ 5
[    2.352575] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    2.352579] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    2.352640] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    2.352663] uhci_hcd 0000:00:1d.0: irq 5, io base 0x00001820
[    2.352765] usb usb2: configuration #1 chosen from 1 choice
[    2.352800] hub 2-0:1.0: USB hub found
[    2.352809] hub 2-0:1.0: 2 ports detected
[    2.352907] uhci_hcd 0000:00:1d.1: PCI INT B -> Link[LNKD] -> GSI 11 (level, low) -> IRQ 11
[    2.352914] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    2.352918] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    2.352967] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3
[    2.352988] uhci_hcd 0000:00:1d.1: irq 11, io base 0x00001840
[    2.353077] usb usb3: configuration #1 chosen from 1 choice
[    2.353108] hub 3-0:1.0: USB hub found
[    2.353116] hub 3-0:1.0: 2 ports detected
[    2.353211] uhci_hcd 0000:00:1d.2: PCI INT C -> Link[LNKC] -> GSI 10 (level, low) -> IRQ 10
[    2.353218] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    2.353222] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    2.353270] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4
[    2.353291] uhci_hcd 0000:00:1d.2: irq 10, io base 0x00001860
[    2.353375] usb usb4: configuration #1 chosen from 1 choice
[    2.353406] hub 4-0:1.0: USB hub found
[    2.353415] hub 4-0:1.0: 2 ports detected
[    2.353559] usbcore: registered new interface driver libusual
[    2.353604] usbcore: registered new interface driver usbserial
[    2.353618] USB Serial support registered for generic
[    2.353636] usbcore: registered new interface driver usbserial_generic
[    2.353639] usbserial: USB Serial Driver core
[    2.353700] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    2.356637] serio: i8042 KBD port at 0x60,0x64 irq 1
[    2.356645] serio: i8042 AUX port at 0x60,0x64 irq 12
[    2.356783] mice: PS/2 mouse device common for all mice
[    2.356999] rtc_cmos 00:01: RTC can wake from S4
[    2.357059] rtc_cmos 00:01: rtc core: registered rtc_cmos as rtc0
[    2.357077] rtc0: alarms up to one month, y3k, 242 bytes nvram
[    2.357171] device-mapper: uevent: version 1.0.3
[    2.357318] device-mapper: ioctl: 4.14.0-ioctl (2008-04-23) initialised: [email]dm-devel@redhat.com[/email]
[    2.357377] device-mapper: multipath: version 1.0.5 loaded
[    2.357381] device-mapper: multipath round-robin: version 1.0.0 loaded
[    2.357479] EISA: Probing bus 0 at eisa.0
[    2.357488] Cannot allocate resource for EISA slot 1
[    2.357492] Cannot allocate resource for EISA slot 2
[    2.357495] Cannot allocate resource for EISA slot 3
[    2.357517] EISA: Detected 0 cards.
[    2.357600] cpuidle: using governor ladder
[    2.357677] cpuidle: using governor menu
[    2.358310] TCP cubic registered
[    2.358444] NET: Registered protocol family 10
[    2.358942] lo: Disabled Privacy Extensions
[    2.359328] NET: Registered protocol family 17
[    2.359350] Bluetooth: L2CAP ver 2.11
[    2.359352] Bluetooth: L2CAP socket layer initialized
[    2.359356] Bluetooth: SCO (Voice Link) ver 0.6
[    2.359358] Bluetooth: SCO socket layer initialized
[    2.359393] Bluetooth: RFCOMM socket layer initialized
[    2.359401] Bluetooth: RFCOMM TTY layer initialized
[    2.359404] Bluetooth: RFCOMM ver 1.10
[    2.359450] IO APIC resources could be not be allocated.
[    2.359500] Using IPI No-Shortcut mode
[    2.359607] registered taskstats version 1
[    2.359753]   Magic number: 9:503:701
[    2.359856] rtc_cmos 00:01: setting system clock to 2009-05-30 20:41:38 UTC (1243716098)
[    2.359861] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    2.359864] EDD information not available.
[    2.360257] Freeing unused kernel memory: 532k freed
[    2.360408] Write protecting the kernel text: 4128k
[    2.360460] Write protecting the kernel read-only data: 1532k
[    2.576492] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input5
[    3.046214] 8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)
[    3.046265] 8139cp 0000:02:08.0: This (id 10ec:8139 rev 10) is not an 8139C+ compatible chip, use 8139too
[    3.050109] 8139too Fast Ethernet driver 0.9.28
[    3.050156] 8139too 0000:02:08.0: PCI INT A -> Link[LNKB] -> GSI 10 (level, low) -> IRQ 10
[    3.051208] eth0: RealTek RTL8139 at 0x3000, 00:03:25:1f:d1:47, IRQ 10
[    3.051211] eth0:  Identified 8139 chip type 'RTL-8101'
[    3.064028] ohci1394 0000:02:07.2: PCI INT C -> Link[LNKC] -> GSI 10 (level, low) -> IRQ 10
[    3.116821] ohci1394: fw-host0: OHCI-1394 1.0 (PCI): IRQ=[10]  MMIO=[e0202000-e02027ff]  Max Packet=[2048]  IR/IT contexts=[4/4]
[    3.130057] b43-pci-bridge 0000:02:09.0: PCI INT A -> Link[LNKB] -> GSI 10 (level, low) -> IRQ 10
[    3.133463] ssb: Sonics Silicon Backplane found on PCI device 0000:02:09.0
[    3.462650] Marking TSC unstable due to TSC halts in idle
[    3.519395] PM: Starting manual resume from disk
[    3.519401] PM: Resume from partition 8:5
[    3.519403] PM: Checking hibernation image.
[    3.519636] PM: Resume from disk failed.
[    3.523023] EXT3-fs: INFO: recovery required on readonly filesystem.
[    3.523027] EXT3-fs: write access will be enabled during recovery.
[    4.401022] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[0003252135021455]
[    4.529566] kjournald starting.  Commit interval 5 seconds
[    4.529589] EXT3-fs: sda1: orphan cleanup on readonly fs
[    4.529596] ext3_orphan_cleanup: deleting unreferenced inode 3268933
[    4.529632] ext3_orphan_cleanup: deleting unreferenced inode 1564698
[    4.529640] EXT3-fs: sda1: 2 orphan inodes deleted
[    4.529643] EXT3-fs: recovery complete.
[    4.565780] EXT3-fs: mounted filesystem with ordered data mode.
[   12.474181] udev: starting version 141
[   12.631737] Linux agpgart interface v0.103
[   12.768731] agpgart-intel 0000:00:00.0: Intel 855GM Chipset
[   12.769080] agpgart-intel 0000:00:00.0: detected 32636K stolen memory
[   12.770746] agpgart-intel 0000:00:00.0: AGP aperture is 128M @ 0xe8000000
[   12.774798] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   12.795910] intel_rng: FWH not detected
[   12.987192] acpi device:05: registered as cooling_device1
[   12.987406] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A03:00/device:03/input/input6
[   13.020226] ACPI: Video Device [GFX0] (multi-head: yes  rom: yes  post: no)
[   13.199471] yenta_cardbus 0000:02:07.0: CardBus bridge found [161f:203a]
[   13.277547] input: PC Speaker as /devices/platform/pcspkr/input/input7
[   13.324968] yenta_cardbus 0000:02:07.0: ISA IRQ mask 0x0090, PCI irq 11
[   13.324974] yenta_cardbus 0000:02:07.0: Socket status: 30000006
[   13.324979] pci_bus 0000:02: Raising subordinate bus# of parent bus (#02) from #02 to #06
[   13.324991] yenta_cardbus 0000:02:07.0: pcmcia: parent PCI bridge I/O window: 0x3000 - 0x3fff
[   13.324996] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x3000-0x3fff: clean.
[   13.325287] yenta_cardbus 0000:02:07.0: pcmcia: parent PCI bridge Memory window: 0xe0200000 - 0xe02fffff
[   13.325291] yenta_cardbus 0000:02:07.0: pcmcia: parent PCI bridge Memory window: 0x30000000 - 0x37ffffff
[   13.326655] yenta_cardbus 0000:02:07.1: CardBus bridge found [161f:203a]
[   13.452875] yenta_cardbus 0000:02:07.1: ISA IRQ mask 0x0090, PCI irq 10
[   13.452882] yenta_cardbus 0000:02:07.1: Socket status: 30000006
[   13.452887] pci_bus 0000:02: Raising subordinate bus# of parent bus (#02) from #06 to #0a
[   13.452898] yenta_cardbus 0000:02:07.1: pcmcia: parent PCI bridge I/O window: 0x3000 - 0x3fff
[   13.452903] pcmcia_socket pcmcia_socket1: cs: IO port probe 0x3000-0x3fff: clean.
[   13.453195] yenta_cardbus 0000:02:07.1: pcmcia: parent PCI bridge Memory window: 0xe0200000 - 0xe02fffff
[   13.453199] yenta_cardbus 0000:02:07.1: pcmcia: parent PCI bridge Memory window: 0x30000000 - 0x37ffffff
[   13.499993] iTCO_vendor_support: vendor-support=0
[   13.502499] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.05
[   13.502653] iTCO_wdt: Found a ICH4-M TCO device (Version=1, TCOBASE=0x1060)
[   13.502763] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   13.594884] synaptics was reset on resume, see synaptics_resume_reset if you have trouble on resume
[   13.668473] cfg80211: Calling CRDA to update world regulatory domain
[   13.712416] pcmcia_socket pcmcia_socket1: cs: IO port probe 0x100-0x3af: clean.
[   13.714077] pcmcia_socket pcmcia_socket1: cs: IO port probe 0x3e0-0x4ff: excluding 0x4d0-0x4d7
[   13.714787] pcmcia_socket pcmcia_socket1: cs: IO port probe 0x820-0x8ff: clean.
[   13.715377] pcmcia_socket pcmcia_socket1: cs: IO port probe 0xc00-0xcf7: clean.
[   13.716187] pcmcia_socket pcmcia_socket1: cs: IO port probe 0xa00-0xaff: clean.
[   13.875400] cfg80211: World regulatory domain updated:
[   13.875408]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   13.875412]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   13.875415]     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   13.875419]     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   13.875422]     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   13.875426]     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   13.984062] b43-phy0: Broadcom 4306 WLAN found
[   14.033214] phy0: Selected rate control algorithm 'pid'
[   14.128121] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x100-0x3af: clean.
[   14.129784] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x3e0-0x4ff: excluding 0x4d0-0x4d7
[   14.130495] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x820-0x8ff: clean.
[   14.131085] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xc00-0xcf7: clean.
[   14.131864] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xa00-0xaff: clean.
[   14.170784] Intel ICH 0000:00:1f.5: PCI INT B -> Link[LNKB] -> GSI 10 (level, low) -> IRQ 10
[   14.170971] Intel ICH 0000:00:1f.5: setting latency timer to 64
[   14.184397] Broadcom 43xx driver loaded [ Features: PLR, Firmware-ID: FW13 ]
[   14.541168] Synaptics Touchpad, model: 1, fw: 5.9, id: 0x236eb3, caps: 0x904713/0x10008
[   14.577966] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input8
[   14.644136] Clocksource tsc unstable (delta = -363697752 ns)
[   14.932463] ALSA /usr/src/modules/alsa-driver/pci/ac97/ac97_codec.c:2871: applying quirk type 3 failed (-2)
[   14.988045] intel8x0_measure_ac97_clock: measured 55277 usecs
[   14.988048] intel8x0: clocking to 48000
[   15.185355] lp: driver loaded but no devices found
[   15.277315] snd_via82xx: disagrees about version of symbol snd_ac97_resume
[   15.277322] snd_via82xx: Unknown symbol snd_ac97_resume
[   15.277457] snd_via82xx: disagrees about version of symbol snd_pcm_new
[   15.277459] snd_via82xx: Unknown symbol snd_pcm_new
[   15.277638] snd_via82xx: disagrees about version of symbol snd_pcm_limit_hw_rates
[   15.277641] snd_via82xx: Unknown symbol snd_pcm_limit_hw_rates
[   15.278121] snd_via82xx: disagrees about version of symbol snd_pcm_lib_preallocate_pages_for_all
[   15.278125] snd_via82xx: Unknown symbol snd_pcm_lib_preallocate_pages_for_all
[   15.278561] snd_via82xx: disagrees about version of symbol snd_ac97_set_rate
[   15.278564] snd_via82xx: Unknown symbol snd_ac97_set_rate
[   15.278834] snd_via82xx: disagrees about version of symbol snd_ac97_update_bits
[   15.278837] snd_via82xx: Unknown symbol snd_ac97_update_bits
[   15.279016] snd_via82xx: disagrees about version of symbol snd_ac97_mixer
[   15.279018] snd_via82xx: Unknown symbol snd_ac97_mixer
[   15.279213] snd_via82xx: disagrees about version of symbol snd_ac97_bus
[   15.279216] snd_via82xx: Unknown symbol snd_ac97_bus
[   15.280069] snd_via82xx: Unknown symbol snd_ac97_update_power
[   15.280207] snd_via82xx: disagrees about version of symbol snd_pcm_sgbuf_get_chunk_size
[   15.280210] snd_via82xx: Unknown symbol snd_pcm_sgbuf_get_chunk_size
[   15.280483] snd_via82xx: disagrees about version of symbol snd_ac97_suspend
[   15.280486] snd_via82xx: Unknown symbol snd_ac97_suspend
[   15.280777] snd_via82xx: disagrees about version of symbol snd_pcm_lib_malloc_pages
[   15.280780] snd_via82xx: Unknown symbol snd_pcm_lib_malloc_pages
[   15.281182] snd_via82xx: disagrees about version of symbol snd_pcm_lib_ioctl
[   15.281185] snd_via82xx: Unknown symbol snd_pcm_lib_ioctl
[   15.281461] snd_via82xx: disagrees about version of symbol snd_pcm_lib_free_pages
[   15.281464] snd_via82xx: Unknown symbol snd_pcm_lib_free_pages
[   15.281694] snd_via82xx: disagrees about version of symbol snd_pcm_set_ops
[   15.281697] snd_via82xx: Unknown symbol snd_pcm_set_ops
[   15.281850] snd_via82xx: disagrees about version of symbol snd_pcm_hw_constraint_list
[   15.281853] snd_via82xx: Unknown symbol snd_pcm_hw_constraint_list
[   15.282183] snd_via82xx: disagrees about version of symbol snd_pcm_sgbuf_ops_page
[   15.282186] snd_via82xx: Unknown symbol snd_pcm_sgbuf_ops_page
[   15.282502] snd_via82xx: disagrees about version of symbol snd_ac97_get_short_name
[   15.282505] snd_via82xx: Unknown symbol snd_ac97_get_short_name
[   15.282638] snd_via82xx: disagrees about version of symbol snd_pcm_suspend_all
[   15.282641] snd_via82xx: Unknown symbol snd_pcm_suspend_all
[   15.282921] snd_via82xx: disagrees about version of symbol snd_pcm_hw_constraint_integer
[   15.282924] snd_via82xx: Unknown symbol snd_pcm_hw_constraint_integer
[   15.283203] snd_via82xx: disagrees about version of symbol snd_pci_quirk_lookup
[   15.283206] snd_via82xx: Unknown symbol snd_pci_quirk_lookup
[   15.283676] snd_via82xx: disagrees about version of symbol snd_pcm_period_elapsed
[   15.283679] snd_via82xx: Unknown symbol snd_pcm_period_elapsed
[   15.283817] snd_via82xx: disagrees about version of symbol snd_ac97_tune_hardware
[   15.283820] snd_via82xx: Unknown symbol snd_ac97_tune_hardware
[   15.391882] Adding 1397612k swap on /dev/sda5.  Priority:-1 extents:1 across:1397612k
[   15.936083] EXT3 FS on sda1, internal journal
[   17.045253] type=1505 audit(1243716113.184:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=1965
[   17.116703] type=1505 audit(1243716113.256:3): operation="profile_load" name="/sbin/dhclient-script" name2="default" pid=1969
[   17.116924] type=1505 audit(1243716113.256:4): operation="profile_load" name="/sbin/dhclient3" name2="default" pid=1969
[   17.117008] type=1505 audit(1243716113.256:5): operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" name2="default" pid=1969
[   17.117073] type=1505 audit(1243716113.256:6): operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" name2="default" pid=1969
[   17.328812] type=1505 audit(1243716113.468:7): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=1974
[   17.329170] type=1505 audit(1243716113.468:8): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=1974
[   17.369936] type=1505 audit(1243716113.508:9): operation="profile_load" name="/usr/sbin/tcpdump" name2="default" pid=1978
[   20.635810] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   20.635814] Bluetooth: BNEP filters: protocol multicast
[   20.661649] Bridge firewalling registered
[   22.326910] ppdev: user-space parallel port driver
[   23.702196] [drm] Initialized drm 1.1.0 20060810
[   23.711961] pci 0000:00:02.0: PCI INT A -> Link[LNKA] -> GSI 5 (level, low) -> IRQ 5
[   23.711970] pci 0000:00:02.0: setting latency timer to 64
[   23.712667] [drm] Initialized i915 1.6.0 20080730 on minor 0
[   23.815444] [drm:i915_setparam] *ERROR* unknown parameter 4
[   23.815477] [drm:i915_getparam] *ERROR* Unknown parameter 6
[   24.945591] [drm:i915_getparam] *ERROR* Unknown parameter 6
[   25.861658] eth0: link down
[   25.861784] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   26.168546] input: b43-phy0 as /devices/virtual/input/input9
[   26.204059] b43 ssb0:0: firmware: requesting b43/ucode5.fw
[   26.381100] b43 ssb0:0: firmware: requesting b43/pcm5.fw
[   26.494094] b43 ssb0:0: firmware: requesting b43/b0g0initvals5.fw
[   26.686663] b43 ssb0:0: firmware: requesting b43/b0g0bsinitvals5.fw
[   26.836056] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
[   26.897028] Registered led device: b43-phy0::tx
[   26.897052] Registered led device: b43-phy0::rx
[   26.897075] Registered led device: b43-phy0::radio
[   26.912063] b43-phy0: Radio turned on by software
[   26.912240] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   29.964562] wlan0: authenticate with AP 00:1c:10:04:6b:2b
[   29.966078] wlan0: authenticated
[   29.966082] wlan0: associate with AP 00:1c:10:04:6b:2b
[   29.968526] wlan0: RX AssocResp from 00:1c:10:04:6b:2b (capab=0x411 status=0 aid=2)
[   29.968530] wlan0: associated
[   29.970513] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   34.670627] spurious 8259A interrupt: IRQ7.
[   37.086059] [drm:i915_getparam] *ERROR* Unknown parameter 6
[   40.808027] wlan0: no IPv6 routers present
[   49.907032] UDF-fs: Partition marked readonly; forcing readonly mount
[   49.948102] UDF-fs INFO UDF: Mounting volume 'SHANGHAI_KNIGHTS', timestamp 2003/05/20 18:24 (1000)
[ 1399.128594] [drm:i915_getparam] *ERROR* Unknown parameter 6
[ 6271.066671] [drm:i915_getparam] *ERROR* Unknown parameter 6
[ 9531.090037] [drm:i915_getparam] *ERROR* Unknown parameter 6
[12386.041519] [drm:i915_getparam] *ERROR* Unknown parameter 6



I did try alsa mixer and its a gateway laptop.....sorry, but its a friends so I'm not sure of the model number because for some reason its not on the sticker :-/..... need to know anything else?

---

### Post by tommah04 on 2009-05-31
aw crap, forgot about the smilies.....

---

### Post by albinootje on 2009-05-31
> **tommah04 said:**
> 
[   14.932463] ALSA /usr/src/modules/alsa-driver/pci/ac97/ac97_codec.c:2871: applying quirk type 3 failed (-2)
[   14.988045] intel8x0_measure_ac97_clock: measured 55277 usecs
[   14.988048] intel8x0: clocking to 48000
[   15.185355] lp: driver loaded but no devices found
[   15.277315] snd_via82xx: disagrees about version of symbol snd_ac97_resume
[   15.277322] snd_via82xx: Unknown symbol snd_ac97_resume
[   15.277457] snd_via82xx: disagrees about version of symbol snd_pcm_new

It looks like you added something to /etc/modprobe.d/alsa or /etc/modprobe.d/alsa-base.conf, which can't be applied.
Did you compile alsa from source ?
Did you try different settings without PulseAudio ?

---

### Post by tommah04 on 2009-05-31
I did try adding a few things in alsa-base.conf since it wasn't working out of the box, if I added to it, would that prevent it from working, or would it just ignore those lines?

I thought pulse audio was supposed to work flawlessly with alsa
if I should turn pulseaudio off, how would I do that



also, if possible, I'd like to know what I should delete....


# autoloader aliases
install sound-slot-0 /sbin/modprobe snd-card-0
install sound-slot-1 /sbin/modprobe snd-card-1
install sound-slot-2 /sbin/modprobe snd-card-2
install sound-slot-3 /sbin/modprobe snd-card-3
install sound-slot-4 /sbin/modprobe snd-card-4
install sound-slot-5 /sbin/modprobe snd-card-5
install sound-slot-6 /sbin/modprobe snd-card-6
install sound-slot-7 /sbin/modprobe snd-card-7

# Cause optional modules to be loaded above generic modules
install snd /sbin/modprobe --ignore-install snd $CMDLINE_OPTS && { /sbin/modpro$
#
# Workaround at bug #499695 (reverted in Ubuntu see LP #319505)
install snd-pcm /sbin/modprobe --ignore-install snd-pcm $CMDLINE_OPTS && { /sbi$
install snd-mixer /sbin/modprobe --ignore-install snd-mixer $CMDLINE_OPTS && { $
install snd-seq /sbin/modprobe --ignore-install snd-seq $CMDLINE_OPTS && { /sbi$
#
install snd-rawmidi /sbin/modprobe --ignore-install snd-rawmidi $CMDLINE_OPTS &$

# Cause optional modules to be loaded above generic modules
install snd /sbin/modprobe --ignore-install snd $CMDLINE_OPTS && { /sbin/modpro$
#
# Workaround at bug #499695 (reverted in Ubuntu see LP #319505)
install snd-pcm /sbin/modprobe --ignore-install snd-pcm $CMDLINE_OPTS && { /sbi$
install snd-mixer /sbin/modprobe --ignore-install snd-mixer $CMDLINE_OPTS && { $
install snd-seq /sbin/modprobe --ignore-install snd-seq $CMDLINE_OPTS && { /sbi$
#
install snd-rawmidi /sbin/modprobe --ignore-install snd-rawmidi $CMDLINE_OPTS &$
# Cause optional modules to be loaded above sound card driver modules
install snd-emu10k1 /sbin/modprobe --ignore-install snd-emu10k1 $CMDLINE_OPTS &$
install snd-via82xx /sbin/modprobe --ignore-install snd-via82xx $CMDLINE_OPTS &$

# Load saa7134-alsa instead of saa7134 (which gets dragged in by it anyway)
install saa7134 /sbin/modprobe --ignore-install saa7134 $CMDLINE_OPTS && { /sbi$
# Prevent abnormal drivers from grabbing index 0
options bt87x index=-2
options cx88_alsa index=-2

install snd-rawmidi /sbin/modprobe --ignore-install snd-rawmidi $CMDLINE_OPTS &$
# Cause optional modules to be loaded above sound card driver modules
install snd-emu10k1 /sbin/modprobe --ignore-install snd-emu10k1 $CMDLINE_OPTS &$
install snd-via82xx /sbin/modprobe --ignore-install snd-via82xx $CMDLINE_OPTS &$

# Load saa7134-alsa instead of saa7134 (which gets dragged in by it anyway)
install saa7134 /sbin/modprobe --ignore-install saa7134 $CMDLINE_OPTS && { /sbi$
# Prevent abnormal drivers from grabbing index 0

options bt87x index=-2
options cx88_alsa index=-2
options saa7134-alsa index=-2
options snd-atiixp-modem index=-2
options snd-intel8x0m index=-2
options snd-via82xx-modem index=-2
options snd-usb-audio index=-2
options snd-usb-us122l index=-2
options snd-usb-usx2y index=-2
options snd-usb-caiaq index=-2
# Ubuntu #62691, enable MPU for snd-cmipci
options snd-cmipci mpu_port=0x330 fm_port=0x388
# Keep snd-pcsp from beeing loaded as first soundcard
options snd-pcsp index=-2
options snd-intel8x0 ac97_quirk=3

---

### Post by albinootje on 2009-05-31
> **tommah04 said:**
> 
# Keep snd-pcsp from beeing loaded as first soundcard
options snd-pcsp index=-2
options snd-intel8x0 ac97_quirk=3
[/quote]
I suggest to comment out those two lines, unless you find that these will help for sure.

And have a careful look at these links :
[http://www.ubuntux.org/no-sound-on-ubuntu-dapper](http://www.ubuntux.org/no-sound-on-ubuntu-dapper)
[http://ubuntuforums.org/showthread.php?t=757479](http://ubuntuforums.org/showthread.php?t=757479)
[http://ubuntuforums.org/showthread.php?t=479060](http://ubuntuforums.org/showthread.php?t=479060)

---

### Post by tommah04 on 2009-05-31
well....no sound is working.....so they aren't HELPING, ha

they = suggested lines to delete

---

### Post by tommah04 on 2009-05-31
I suggest to comment out those two lines, unless you find that these will help for sure.

And have a careful look at these links :
[http://www.ubuntux.org/no-sound-on-ubuntu-dapper](http://www.ubuntux.org/no-sound-on-ubuntu-dapper)
[http://ubuntuforums.org/showthread.php?t=757479](http://ubuntuforums.org/showthread.php?t=757479)
[http://ubuntuforums.org/showthread.php?t=479060](http://ubuntuforums.org/showthread.php?t=479060)[/quote]



wow.... that first site actually helped.... I've been trying to fix this for days

tried so many different things and it turns out I just had to play with some settings.....

well thanks a bunch, speakers and headphones working perfectly

*thumbs up*

---

