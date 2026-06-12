---
title: "laptop will not power down on shutdown"
date: 2009-09-25
forum: Hardware
---

### Post by Neill_R on 2009-09-25
Hi

I have a HP n5271 pavillon laptop. I have dual boot on this PC.
Under windows XP it will power-off on shutdown.

Under my newly installed Xubuntu 9.04 OS it does not. 

As far as I can tell my BIOS is the latest available  GC.M1.63 
by sudo dmidecode -s bios-version

If you have a suggestion / solution i am new to Linux so please explain clearly or point me to a good how to to achieve the task step(s).

Points notice but not understood

[    0.000000] ACPI: BIOS age (1992) fails cutoff (2000), acpi=force is required to enable 
[    0.000000] ACPI: Disabling ACPI support

[    0.365749] Local APIC not detected. Using dummy APIC emulation.



The full Dmesg 
[    0.000000] BIOS EBDA/lowmem at: 0009f800/0009f800
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.28-15-generic (buildd@palmer) (gcc version 4.3.3 (Ubuntu 4.3.3-5ubuntu4) ) #49-Ubuntu SMP Tue Aug 18 18:40:08 UTC 2009 (Ubuntu 2.6.28-15.49-generic)
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
[    0.000000]  BIOS-e820: 00000000000eac00 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000000fff0000 (usable)
[    0.000000]  BIOS-e820: 000000000fff0000 - 000000000ffffc00 (ACPI data)
[    0.000000]  BIOS-e820: 000000000ffffc00 - 0000000010000000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000fff80000 - 0000000100000000 (reserved)
[    0.000000] DMI 2.2 present.
[    0.000000] Phoenix BIOS detected: BIOS may corrupt low RAM, working it around.
[    0.000000] last_pfn = 0xfff0 max_arch_pfn = 0x100000
[    0.000000] Scanning 0 areas for low memory corruption
[    0.000000] modified physical RAM map:
[    0.000000]  modified: 0000000000000000 - 0000000000010000 (reserved)
[    0.000000]  modified: 0000000000010000 - 000000000009f800 (usable)
[    0.000000]  modified: 000000000009f800 - 00000000000a0000 (reserved)
[    0.000000]  modified: 00000000000eac00 - 0000000000100000 (reserved)
[    0.000000]  modified: 0000000000100000 - 000000000fff0000 (usable)
[    0.000000]  modified: 000000000fff0000 - 000000000ffffc00 (ACPI data)
[    0.000000]  modified: 000000000ffffc00 - 0000000010000000 (ACPI NVS)
[    0.000000]  modified: 00000000fff80000 - 0000000100000000 (reserved)
[    0.000000] kernel direct mapping tables up to fff0000 @ 10000-16000
[    0.000000] RAMDISK: 0f89e000 - 0ffdf4ff
[    0.000000] ACPI: RSDP 000F6A70, 0014 (r0 PTLTD )
[    0.000000] ACPI: RSDT 0FFFCF33, 002C (r1 PTLTD    RSDT    6040000  LTP        0)
[    0.000000] ACPI: FACP 0FFFFB65, 0074 (r1 COMPAL N32NC     6040000 PTL         1)
[    0.000000] ACPI: DSDT 0FFFCF5F, 2C06 (r1 Compal     32NC  6040000 MSFT  100000B)
[    0.000000] ACPI: FACS 0FFFFFC0, 0040
[    0.000000] ACPI: BOOT 0FFFFBD9, 0027 (r1 PTLTD  $SBFTBL$  6040000  LTP        1)
[    0.000000] ACPI: BIOS age (1992) fails cutoff (2000), acpi=force is required to enable ACPI
[    0.000000] ACPI: Disabling ACPI support
[    0.000000] 0MB HIGHMEM available.
[    0.000000] 255MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 0fff0000
[    0.000000]   low ram: 00000000 - 0fff0000
[    0.000000]   bootmap 00012000 - 00014000
[    0.000000] (9 early reservations) ==> bootmem [0000000000 - 000fff0000]
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000]   #1 [0000001000 - 0000002000]    EX TRAMPOLINE ==> [0000001000 - 0000002000]
[    0.000000]   #2 [0000006000 - 0000007000]       TRAMPOLINE ==> [0000006000 - 0000007000]
[    0.000000]   #3 [0000100000 - 00008780ac]    TEXT DATA BSS ==> [0000100000 - 00008780ac]
[    0.000000]   #4 [000f89e000 - 000ffdf4ff]          RAMDISK ==> [000f89e000 - 000ffdf4ff]
[    0.000000]   #5 [0000879000 - 000087d000]    INIT_PG_TABLE ==> [0000879000 - 000087d000]
[    0.000000]   #6 [000009f800 - 0000100000]    BIOS reserved ==> [000009f800 - 0000100000]
[    0.000000]   #7 [0000010000 - 0000012000]          PGTABLE ==> [0000010000 - 0000012000]
[    0.000000]   #8 [0000012000 - 0000014000]          BOOTMAP ==> [0000012000 - 0000014000]
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x0000fff0
[    0.000000]   HighMem  0x0000fff0 -> 0x0000fff0
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[2] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x0000009f
[    0.000000]     0: 0x00000100 -> 0x0000fff0
[    0.000000] On node 0 totalpages: 65407
[    0.000000] free_area_init_node: node 0, pgdat c06cb500, node_mem_map c1000200
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3951 pages, LIFO batch:0
[    0.000000]   Normal zone: 480 pages used for memmap
[    0.000000]   Normal zone: 60944 pages, LIFO batch:15
[    0.000000]   HighMem zone: 0 pages used for memmap
[    0.000000]   Movable zone: 0 pages used for memmap
[    0.000000] SMP: Allowing 1 CPUs, 0 hotplug CPUs
[    0.000000] Local APIC disabled by BIOS -- you can enable it with "lapic"
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000eb000
[    0.000000] PM: Registered nosave memory: 00000000000eb000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 20000000 (gap: 10000000:eff80000)
[    0.000000] PERCPU: Allocating 45056 bytes of per cpu data
[    0.000000] NR_CPUS: 64, nr_cpu_ids: 1, nr_node_ids 1
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 64895
[    0.000000] Kernel command line: root=UUID=894c9d79-fcd6-4f44-a72a-f852270ef696 ro quiet splash 
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 1024 (order: 10, 4096 bytes)
[    0.000000] TSC: Using PIT calibration value
[    0.000000] Detected 696.934 MHz processor.
[    0.004000] Console: colour VGA+ 80x25
[    0.004000] console [tty0] enabled
[    0.004000] Dentry cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.004000] Inode-cache hash table entries: 16384 (order: 4, 65536 bytes)
[    0.004000] allocated 1310080 bytes of page_cgroup
[    0.004000] please try cgroup_disable=memory option if you don't want
[    0.004000] Scanning for low memory corruption every 60 seconds
[    0.004000] Memory: 242604k/262080k available (4115k kernel code, 18716k reserved, 2199k data, 532k init, 0k highmem)
[    0.004000] virtual kernel memory layout:
[    0.004000]     fixmap  : 0xffc77000 - 0xfffff000   (3616 kB)
[    0.004000]     pkmap   : 0xff400000 - 0xff800000   (4096 kB)
[    0.004000]     vmalloc : 0xd07f0000 - 0xff3fe000   ( 748 MB)
[    0.004000]     lowmem  : 0xc0000000 - 0xcfff0000   ( 255 MB)
[    0.004000]       .init : 0xc0733000 - 0xc07b8000   ( 532 kB)
[    0.004000]       .data : 0xc0504f5f - 0xc072ae60   (2199 kB)
[    0.004000]       .text : 0xc0100000 - 0xc0504f5f   (4115 kB)
[    0.004000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.004000] SLUB: Genslabs=12, HWalign=32, Order=0-3, MinObjects=0, CPUs=1, Nodes=1
[    0.004022] Calibrating delay loop (skipped), value calculated using timer frequency.. 1393.86 BogoMIPS (lpj=2787736)
[    0.004078] Security Framework initialized
[    0.004100] SELinux:  Disabled at boot.
[    0.004162] AppArmor: AppArmor initialized
[    0.004187] Mount-cache hash table entries: 512
[    0.004570] Initializing cgroup subsys ns
[    0.004583] Initializing cgroup subsys cpuacct
[    0.004592] Initializing cgroup subsys memory
[    0.004604] Initializing cgroup subsys freezer
[    0.004646] CPU: L1 I cache: 16K, L1 D cache: 16K
[    0.004656] CPU: L2 cache: 256K
[    0.004700] Checking 'hlt' instruction... OK.
[    0.021293] SMP alternatives: switching to UP code
[    0.365449] Freeing SMP alternatives: 18k freed
[    0.365729] weird, boot CPU (#0) not listedby the BIOS.
[    0.365740] SMP motherboard not detected.
[    0.365749] Local APIC not detected. Using dummy APIC emulation.
[    0.365756] SMP disabled
[    0.367046] Brought up 1 CPUs
[    0.367064] Total of 1 processors activated (1393.86 BogoMIPS).
[    0.367137] CPU0 attaching NULL sched-domain.
[    0.368301] net_namespace: 776 bytes
[    0.368340] Booting paravirtualized kernel on bare hardware
[    0.369194] Time: 10:57:24  Date: 09/23/09
[    0.369214] regulator: core version 0.5
[    0.369336] NET: Registered protocol family 16
[    0.369774] EISA bus registered
[    0.392996] PCI: PCI BIOS revision 2.10 entry at 0xfd9be, last bus=1
[    0.393006] PCI: Using configuration type 1 for base access
[    0.396480] ACPI: Interpreter disabled.
[    0.397030] SCSI subsystem initialized
[    0.397182] libata version 3.00 loaded.
[    0.397358] usbcore: registered new interface driver usbfs
[    0.397415] usbcore: registered new interface driver hub
[    0.397517] usbcore: registered new device driver usb
[    0.397937] PCI: Probing PCI hardware
[    0.397948] PCI: Probing PCI hardware (bus 00)
[    0.398057] pci 0000:00:00.0: reg 10 32bit mmio: [0xf8000000-0xfbffffff]
[    0.398172] pci 0000:00:04.0: reg 10 32bit mmio: [0x30100000-0x30100fff]
[    0.398190] pci 0000:00:04.0: supports D1 D2
[    0.398198] pci 0000:00:04.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.398208] pci 0000:00:04.0: PME# disabled
[    0.398253] pci 0000:00:04.1: reg 10 32bit mmio: [0x30101000-0x30101fff]
[    0.398271] pci 0000:00:04.1: supports D1 D2
[    0.398278] pci 0000:00:04.1: PME# supported from D0 D1 D2 D3hot D3cold
[    0.398287] pci 0000:00:04.1: PME# disabled
[    0.398416] pci 0000:00:07.1: reg 20 io port: [0x1050-0x105f]
[    0.398487] pci 0000:00:07.2: reg 20 io port: [0x1060-0x107f]
[    0.398578] pci 0000:00:07.3: quirk: region 1000-103f claimed by PIIX4 ACPI
[    0.398588] pci 0000:00:07.3: quirk: region 1040-104f claimed by PIIX4 SMB
[    0.398603] pci 0000:00:07.3: PIIX4 devres E PIO at 0378-037f
[    0.398614] pci 0000:00:07.3: PIIX4 devres G PIO at 002e-002f
[    0.398667] pci 0000:00:08.0: reg 10 io port: [0x1400-0x14ff]
[    0.398716] pci 0000:00:08.0: supports D1 D2
[    0.398723] pci 0000:00:08.0: PME# supported from D1 D2 D3hot
[    0.398733] pci 0000:00:08.0: PME# disabled
[    0.398776] pci 0000:00:08.1: reg 10 io port: [0x1800-0x18ff]
[    0.398826] pci 0000:00:08.1: supports D1 D2
[    0.398833] pci 0000:00:08.1: PME# supported from D1 D2 D3hot D3cold
[    0.398842] pci 0000:00:08.1: PME# disabled
[    0.398939] pci 0000:01:01.0: reg 10 32bit mmio: [0xf0000000-0xf7ffffff]
[    0.398974] pci 0000:01:01.0: reg 30 32bit mmio: [0x000000-0x00ffff]
[    0.398990] pci 0000:01:01.0: supports D1 D2
[    0.399045] pci 0000:00:01.0: bridge 32bit mmio: [0xf0000000-0xf7ffffff]
[    0.400081] pci 0000:00:07.0: PIIX/ICH IRQ router [8086:7110]
[    0.400119] PCI: setting IRQ 11 as level-triggered
[    0.400129] pci 0000:00:04.0: found PCI INT A -> IRQ 11
[    0.400146] pci 0000:00:04.0: sharing IRQ 11 with 0000:00:04.1
[    0.400172] pci 0000:00:04.0: sharing IRQ 11 with 0000:01:01.0
[    0.400417] Bluetooth: Core ver 2.13
[    0.400417] NET: Registered protocol family 31
[    0.400417] Bluetooth: HCI device and connection manager initialized
[    0.400417] Bluetooth: HCI socket layer initialized
[    0.400417] NET: Registered protocol family 8
[    0.400417] NET: Registered protocol family 20
[    0.400417] NetLabel: Initializing
[    0.400417] NetLabel:  domain hash size = 128
[    0.400417] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.400417] NetLabel:  unlabeled traffic allowed by default
[    0.400657] AppArmor: AppArmor Filesystem Enabled
[    0.400666] pnp: PnP ACPI: disabled
[    0.400677] PnPBIOS: Scanning system for PnP BIOS support...
[    0.400734] PnPBIOS: Found PnP BIOS installation structure at 0xc00f6ae0
[    0.400743] PnPBIOS: PnP BIOS version 1.0, entry 0xf0000:0x9f67, dseg 0x400
[    0.405641] PnPBIOS: 17 nodes reported by PnP BIOS; 17 recorded by driver
[    0.405675] system 00:00: iomem range 0xfff80000-0xffffffff has been reserved
[    0.405696] system 00:01: iomem range 0x0-0x9ffff could not be reserved
[    0.405706] system 00:01: iomem range 0xe8000-0xfffff could not be reserved
[    0.405716] system 00:01: iomem range 0x100000-0xfffffff could not be reserved
[    0.405743] system 00:0a: ioport range 0x4d0-0x4d1 has been reserved
[    0.405752] system 00:0a: ioport range 0x1000-0x103f has been reserved
[    0.405762] system 00:0a: ioport range 0x1040-0x104f has been reserved
[    0.405783] system 00:0b: iomem range 0xdc000-0xdffff has been reserved
[    0.406425] pci 0000:00:01.0: PCI bridge, secondary bus 0000:01
[    0.406434] pci 0000:00:01.0:   IO window: disabled
[    0.406447] pci 0000:00:01.0:   MEM window: 0xf0000000-0xf7ffffff
[    0.406457] pci 0000:00:01.0:   PREFETCH window: 0x00000030000000-0x000000300fffff
[    0.406471] pci 0000:00:04.0: CardBus bridge, secondary bus 0000:02
[    0.406479] pci 0000:00:04.0:   IO window: 0x001c00-0x001cff
[    0.406489] pci 0000:00:04.0:   IO window: 0x002000-0x0020ff
[    0.406499] pci 0000:00:04.0:   PREFETCH window: 0x20000000-0x23ffffff
[    0.406510] pci 0000:00:04.0:   MEM window: 0x24000000-0x27ffffff
[    0.406520] pci 0000:00:04.1: CardBus bridge, secondary bus 0000:06
[    0.406528] pci 0000:00:04.1:   IO window: 0x002400-0x0024ff
[    0.406537] pci 0000:00:04.1:   IO window: 0x002800-0x0028ff
[    0.406547] pci 0000:00:04.1:   PREFETCH window: 0x28000000-0x2bffffff
[    0.406557] pci 0000:00:04.1:   MEM window: 0x2c000000-0x2fffffff
[    0.406592] pci 0000:00:04.0: found PCI INT A -> IRQ 11
[    0.406610] pci 0000:00:04.0: sharing IRQ 11 with 0000:00:04.1
[    0.406637] pci 0000:00:04.0: sharing IRQ 11 with 0000:01:01.0
[    0.406659] pci 0000:00:04.1: found PCI INT A -> IRQ 11
[    0.406674] pci 0000:00:04.1: sharing IRQ 11 with 0000:00:04.0
[    0.406703] pci 0000:00:04.1: sharing IRQ 11 with 0000:01:01.0
[    0.406717] bus: 00 index 0 io port: [0x00-0xffff]
[    0.406725] bus: 00 index 1 mmio: [0x000000-0xffffffff]
[    0.406732] bus: 01 index 0 mmio: [0x0-0x0]
[    0.406739] bus: 01 index 1 mmio: [0xf0000000-0xf7ffffff]
[    0.406747] bus: 01 index 2 mmio: [0x30000000-0x300fffff]
[    0.406754] bus: 01 index 3 mmio: [0x0-0x0]
[    0.406761] bus: 02 index 0 io port: [0x1c00-0x1cff]
[    0.406768] bus: 02 index 1 io port: [0x2000-0x20ff]
[    0.406776] bus: 02 index 2 mmio: [0x20000000-0x23ffffff]
[    0.406783] bus: 02 index 3 mmio: [0x24000000-0x27ffffff]
[    0.406791] bus: 06 index 0 io port: [0x2400-0x24ff]
[    0.406798] bus: 06 index 1 io port: [0x2800-0x28ff]
[    0.406805] bus: 06 index 2 mmio: [0x28000000-0x2bffffff]
[    0.406813] bus: 06 index 3 mmio: [0x2c000000-0x2fffffff]
[    0.406844] NET: Registered protocol family 2
[    0.407291] IP route cache hash table entries: 2048 (order: 1, 8192 bytes)
[    0.408174] TCP established hash table entries: 8192 (order: 4, 65536 bytes)
[    0.408403] TCP bind hash table entries: 8192 (order: 4, 65536 bytes)
[    0.408625] TCP: Hash tables configured (established 8192 bind 8192)
[    0.408634] TCP reno registered
[    0.408977] NET: Registered protocol family 1
[    0.409393] checking if image is initramfs... it is
[    2.416570] Freeing initrd memory: 7429k freed
[    2.416708] Simple Boot Flag at 0x38 set to 0x1
[    2.416794] cpufreq: No nForce2 chipset.
[    2.417213] audit: initializing netlink socket (disabled)
[    2.417269] type=2000 audit(1253703446.416:1): initialized
[    2.441883] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    2.446689] VFS: Disk quotas dquot_6.5.1
[    2.446910] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    2.449277] fuse init (API version 7.10)
[    2.449586] msgmni has been set to 488
[    2.450282] alg: No test for stdrng (krng)
[    2.450331] io scheduler noop registered
[    2.450339] io scheduler anticipatory registered
[    2.450346] io scheduler deadline registered
[    2.450431] io scheduler cfq registered (default)
[    2.450472] pci 0000:00:00.0: Limiting direct PCI/PCI transfers
[    2.450542] pci 0000:01:01.0: Boot video device
[    2.450774] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    2.450805] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    2.451044] isapnp: Scanning for PnP cards...
[    2.805002] isapnp: No Plug & Play device found
[    2.808774] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
[    2.808931] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    2.810018] 00:0d: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    2.812599] brd: module loaded
[    2.813700] loop: module loaded
[    2.813980] Fixed MDIO Bus: probed
[    2.814002] PPP generic driver version 2.4.2
[    2.814209] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[    2.814325] Driver 'sd' needs updating - please use bus_type methods
[    2.814357] Driver 'sr' needs updating - please use bus_type methods
[    2.814598] ata_piix 0000:00:07.1: version 2.12
[    2.815095] scsi0 : ata_piix
[    2.815481] scsi1 : ata_piix
[    2.815595] ata1: PATA max UDMA/33 cmd 0x1f0 ctl 0x3f6 bmdma 0x1050 irq 14
[    2.815606] ata2: PATA max UDMA/33 cmd 0x170 ctl 0x376 bmdma 0x1058 irq 15
[    2.976850] ata1.00: ATA-6: FUJITSU MHT2060AT, 009B, max UDMA/100
[    2.976860] ata1.00: 117210240 sectors, multi 16: LBA 
[    2.992793] ata1.00: configured for UDMA/33
[    3.156595] ata2.00: ATAPI: MATSHITADVD-ROM SR-8175, G035, max UDMA/33
[    3.172573] ata2.00: configured for UDMA/33
[    3.173210] scsi 0:0:0:0: Direct-Access     ATA      FUJITSU MHT2060A 009B PQ: 0 ANSI: 5
[    3.173574] sd 0:0:0:0: [sda] 117210240 512-byte hardware sectors: (60.0 GB/55.8 GiB)
[    3.173638] sd 0:0:0:0: [sda] Write Protect is off
[    3.173648] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    3.173749] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    3.173971] sd 0:0:0:0: [sda] 117210240 512-byte hardware sectors: (60.0 GB/55.8 GiB)
[    3.174027] sd 0:0:0:0: [sda] Write Protect is off
[    3.174035] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    3.174133] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    3.174148]  sda: sda1 sda2 < sda5 sda6 sda7 sda8 sda9 > sda3 sda4
[    3.342712] sd 0:0:0:0: [sda] Attached SCSI disk
[    3.342917] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    3.344049] scsi 1:0:0:0: CD-ROM            MATSHITA DVD-ROM SR-8175  G035 PQ: 0 ANSI: 5
[    3.346647] sr0: scsi3-mmc drive: 61x/61x cd/rw xa/form2 cdda tray
[    3.346658] Uniform CD-ROM driver Revision: 3.20
[    3.346998] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    3.347162] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    3.349191] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    3.349253] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    3.349301] uhci_hcd: USB Universal Host Controller Interface driver
[    3.349428] PCI: setting IRQ 5 as level-triggered
[    3.349438] uhci_hcd 0000:00:07.2: found PCI INT D -> IRQ 5
[    3.349495] uhci_hcd 0000:00:07.2: UHCI Host Controller
[    3.349707] uhci_hcd 0000:00:07.2: new USB bus registered, assigned bus number 1
[    3.349757] uhci_hcd 0000:00:07.2: irq 5, io base 0x00001060
[    3.350050] usb usb1: configuration #1 chosen from 1 choice
[    3.350153] hub 1-0:1.0: USB hub found
[    3.350189] hub 1-0:1.0: 2 ports detected
[    3.350657] PNP: PS/2 Controller [PNP0303,PNP0f13] at 0x60,0x64 irq 1,12
[    3.365079] serio: i8042 KBD port at 0x60,0x64 irq 1
[    3.365100] serio: i8042 AUX port at 0x60,0x64 irq 12
[    3.365437] mice: PS/2 mouse device common for all mice
[    3.365737] rtc_cmos 00:05: rtc core: registered rtc_cmos as rtc0
[    3.365780] rtc0: alarms up to one day, 114 bytes nvram
[    3.366048] device-mapper: uevent: version 1.0.3
[    3.368734] device-mapper: ioctl: 4.14.0-ioctl (2008-04-23) initialised: [email]dm-devel@redhat.com[/email]
[    3.368927] device-mapper: multipath: version 1.0.5 loaded
[    3.368938] device-mapper: multipath round-robin: version 1.0.0 loaded
[    3.369274] EISA: Probing bus 0 at eisa.0
[    3.369294] Cannot allocate resource for EISA slot 1
[    3.369303] Cannot allocate resource for EISA slot 2
[    3.369346] EISA: Detected 0 cards.
[    3.369476] cpuidle: using governor ladder
[    3.369484] cpuidle: using governor menu
[    3.371374] TCP cubic registered
[    3.371762] NET: Registered protocol family 10
[    3.373288] lo: Disabled Privacy Extensions
[    3.374437] NET: Registered protocol family 17
[    3.374509] Bluetooth: L2CAP ver 2.11
[    3.374515] Bluetooth: L2CAP socket layer initialized
[    3.374525] Bluetooth: SCO (Voice Link) ver 0.6
[    3.374531] Bluetooth: SCO socket layer initialized
[    3.374697] Bluetooth: RFCOMM socket layer initialized
[    3.374725] Bluetooth: RFCOMM TTY layer initialized
[    3.374732] Bluetooth: RFCOMM ver 1.10
[    3.374857] IO APIC resources could be not be allocated.
[    3.374920] Using IPI No-Shortcut mode
[    3.375205] registered taskstats version 1
[    3.375456]   Magic number: 9:249:983
[    3.375610] rtc_cmos 00:05: setting system clock to 2009-09-23 10:57:27 UTC (1253703447)
[    3.375621] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    3.375628] EDD information not available.
[    3.378391] Freeing unused kernel memory: 532k freed
[    3.378838] Write protecting the kernel text: 4116k
[    3.378967] Write protecting the kernel read-only data: 1528k
[    3.412643] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[    3.661179] usb 1-1: new full speed USB device using uhci_hcd and address 2
[    3.823072] usb 1-1: configuration #1 chosen from 1 choice
[    3.826904] hub 1-1:1.0: USB hub found
[    3.828836] hub 1-1:1.0: 4 ports detected
[    3.968414] usb 1-2: new full speed USB device using uhci_hcd and address 3
[    4.150041] usb 1-2: configuration #1 chosen from 1 choice
[    4.153995] hub 1-2:1.0: USB hub found
[    4.160345] hub 1-2:1.0: 4 ports detected
[    4.241840] usb 1-1.4: new full speed USB device using uhci_hcd and address 4
[    4.368084] usb 1-1.4: configuration #1 chosen from 1 choice
[    4.372007] hub 1-1.4:1.0: USB hub found
[    4.373786] hub 1-1.4:1.0: 4 ports detected
[    4.469842] usb 1-2.1: new full speed USB device using uhci_hcd and address 5
[    4.611048] usb 1-2.1: configuration #1 chosen from 1 choice
[    4.693795] usb 1-2.2: new full speed USB device using uhci_hcd and address 6
[    4.847002] usb 1-2.2: configuration #1 chosen from 1 choice
[    4.925843] usb 1-2.3: new low speed USB device using uhci_hcd and address 7
[    5.090031] usb 1-2.3: configuration #1 chosen from 1 choice
[    5.173732] usb 1-2.4: new full speed USB device using uhci_hcd and address 8
[    5.305207] usb 1-2.4: configuration #1 chosen from 1 choice
[    5.387343] usb 1-1.4.4: new full speed USB device using uhci_hcd and address 9
[    5.523584] Initializing USB Mass Storage driver...
[    5.537386] scsi2 : SCSI emulation for USB Mass Storage devices
[    5.543115] usb 1-1.4.4: configuration #1 chosen from 1 choice
[    5.543159] usb-storage: device found at 5
[    5.543166] usb-storage: waiting for device to settle before scanning
[    5.549898] scsi3 : SCSI emulation for USB Mass Storage devices
[    5.550311] usb-storage: device found at 8
[    5.550319] usb-storage: waiting for device to settle before scanning
[    5.560666] usb-storage: probe of 1-1.4.4:1.0 failed with error -5
[    5.560919] usb-storage: probe of 1-1.4.4:1.1 failed with error -5
[    5.590679] usb-storage: probe of 1-1.4.4:1.2 failed with error -5
[    5.590768] usbcore: registered new interface driver usb-storage
[    5.590782] USB Mass Storage support registered.
[    5.601455] usbcore: registered new interface driver hiddev
[    5.643232] input: HID 1241:1111 as /devices/pci0000:00/0000:00:07.2/usb1/1-2/1-2.3/1-2.3:1.0/input/input2
[    5.674265] generic-usb 0003:1241:1111.0001: input,hidraw0: USB HID v1.10 Mouse [HID 1241:1111] on usb-0000:00:07.2-2.3/input0
[    5.674340] usbcore: registered new interface driver usbhid
[    5.674352] usbhid: v2.6:USB HID core driver
[    5.879198] PM: Starting manual resume from disk
[    5.879212] PM: Resume from partition 8:3
[    5.879218] PM: Checking hibernation image.
[    5.879665] PM: Resume from disk failed.
[    5.927274] kjournald starting.  Commit interval 5 seconds
[    5.927320] EXT3-fs: mounted filesystem with ordered data mode.
[   10.543241] usb-storage: device scan complete
[   10.546275] scsi 2:0:0:0: Direct-Access              Flash Disk       4.00 PQ: 0 ANSI: 2
[   10.550193] usb-storage: device scan complete
[   10.552106] sd 2:0:0:0: [sdb] 510975 512-byte hardware sectors: (261 MB/249 MiB)
[   10.553432] scsi 3:0:0:0: Direct-Access     SanDisk  Cruzer Mini      0.2  PQ: 0 ANSI: 2
[   10.555088] sd 2:0:0:0: [sdb] Write Protect is off
[   10.555098] sd 2:0:0:0: [sdb] Mode Sense: 00 00 00 00
[   10.555106] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[   10.564179] sd 2:0:0:0: [sdb] 510975 512-byte hardware sectors: (261 MB/249 MiB)
[   10.567086] sd 2:0:0:0: [sdb] Write Protect is off
[   10.567095] sd 2:0:0:0: [sdb] Mode Sense: 00 00 00 00
[   10.567102] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[   10.567119]  sdb: sdb1
[   10.575300] sd 2:0:0:0: [sdb] Attached SCSI removable disk
[   10.575531] sd 2:0:0:0: Attached scsi generic sg2 type 0
[   10.580179] sd 3:0:0:0: [sdc] 2001888 512-byte hardware sectors: (1.02 GB/977 MiB)
[   10.583077] sd 3:0:0:0: [sdc] Write Protect is off
[   10.583086] sd 3:0:0:0: [sdc] Mode Sense: 03 00 00 00
[   10.583094] sd 3:0:0:0: [sdc] Assuming drive cache: write through
[   10.595099] sd 3:0:0:0: [sdc] 2001888 512-byte hardware sectors: (1.02 GB/977 MiB)
[   10.598084] sd 3:0:0:0: [sdc] Write Protect is off
[   10.598094] sd 3:0:0:0: [sdc] Mode Sense: 03 00 00 00
[   10.598102] sd 3:0:0:0: [sdc] Assuming drive cache: write through
[   10.598120]  sdc: sdc1
[   10.604486] sd 3:0:0:0: [sdc] Attached SCSI removable disk
[   10.604700] sd 3:0:0:0: Attached scsi generic sg3 type 0
[   15.896638] udev: starting version 141
[   16.899275] Linux agpgart interface v0.103
[   16.950036] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   16.971774] hso: /build/buildd/linux-2.6.28/drivers/net/usb/hso.c: 1.2 Option Wireless
[   16.975209] hso0: Disabled Privacy Extensions
[   16.977476] usbcore: registered new interface driver hso
[   17.082569] piix4_smbus 0000:00:07.3: SMBus Host Controller at 0x1040, revision 0
[   17.150159] usblp0: USB Bidirectional printer dev 6 if 0 alt 0 proto 3 vid 0x03F0 pid 0x0011
[   17.150244] usbcore: registered new interface driver usblp
[   17.311182] yenta_cardbus 0000:00:04.0: CardBus bridge found [103c:0014]
[   17.311213] yenta_cardbus 0000:00:04.0: Enabling burst memory read transactions
[   17.311224] yenta_cardbus 0000:00:04.0: Using CSCINT to route CSC interrupts to PCI
[   17.311233] yenta_cardbus 0000:00:04.0: Routing CardBus interrupts to PCI
[   17.311244] yenta_cardbus 0000:00:04.0: TI: mfunc 0x01ac1b22, devctl 0x66
[   17.544364] yenta_cardbus 0000:00:04.0: ISA IRQ mask 0x0698, PCI irq 11
[   17.544381] yenta_cardbus 0000:00:04.0: Socket status: 30000010
[   17.574490] yenta_cardbus 0000:00:04.1: CardBus bridge found [103c:0014]
[   17.574519] yenta_cardbus 0000:00:04.1: Using CSCINT to route CSC interrupts to PCI
[   17.574527] yenta_cardbus 0000:00:04.1: Routing CardBus interrupts to PCI
[   17.574539] yenta_cardbus 0000:00:04.1: TI: mfunc 0x01ac1b22, devctl 0x66
[   17.808334] yenta_cardbus 0000:00:04.1: ISA IRQ mask 0x0698, PCI irq 11
[   17.808350] yenta_cardbus 0000:00:04.1: Socket status: 30000006
[   18.003363] input: PC Speaker as /devices/platform/pcspkr/input/input3
[   18.176160] agpgart-intel 0000:00:00.0: Intel 440BX Chipset
[   18.180938] agpgart-intel 0000:00:00.0: AGP aperture is 64M @ 0xf8000000
[   18.210937] pcmcia_socket pcmcia_socket0: pccard: PCMCIA card inserted into slot 0
[   18.409658] synaptics was reset on resume, see synaptics_resume_reset if you have trouble on resume
[   18.777608] pcmcia_socket pcmcia_socket1: cs: IO port probe 0x100-0x3af: excluding 0x200-0x207 0x378-0x37f
[   18.780271] pcmcia_socket pcmcia_socket1: cs: IO port probe 0x3e0-0x4ff: clean.
[   18.781388] pcmcia_socket pcmcia_socket1: cs: IO port probe 0x820-0x8ff: clean.
[   18.782391] pcmcia_socket pcmcia_socket1: cs: IO port probe 0xc00-0xcf7: clean.
[   18.783801] pcmcia_socket pcmcia_socket1: cs: IO port probe 0xa00-0xaff: clean.
[   19.199989] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x100-0x3af: excluding 0x200-0x207 0x378-0x37f
[   19.202221] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x3e0-0x4ff: clean.
[   19.203142] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x820-0x8ff: clean.
[   19.203944] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xc00-0xcf7: clean.
[   19.205169] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xa00-0xaff: clean.
[   19.206194] pcmcia_socket pcmcia_socket0: cs: memory probe 0xa0000000-0xa0ffffff: clean.
[   19.212052] pcmcia 0.0: pcmcia: registering new device pcmcia0.0
[   19.212909] ip_tables: (C) 2000-2006 Netfilter Core Team
[   19.643412] nf_conntrack version 0.5.0 (4095 buckets, 16380 max)
[   19.644406] CONFIG_NF_CT_ACCT is deprecated and will be removed soon. Please use
[   19.644417] nf_conntrack.acct=1 kernel paramater, acct=1 nf_conntrack module option or
[   19.644426] sysctl net.netfilter.nf_conntrack_acct=1 to enable it.
[   19.647328] eth0: NE2000 (DL10022 rev 30): io 0x300, irq 3, hw_addr 00:40:05:89:07:c0
[   19.651333] Synaptics Touchpad, model: 1, fw: 5.1, id: 0x8f40b1, caps: 0x80471b/0x0
[   19.674837] Maestro3 0000:00:08.0: found PCI INT A -> IRQ 5
[   19.674884] Maestro3 0000:00:08.0: sharing IRQ 5 with 0000:00:08.1
[   19.674906] Maestro3 0000:00:08.0: firmware: requesting ess/maestro3_assp_kernel.fw
[   19.768274] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input4
[   19.846254] Maestro3 0000:00:08.0: firmware: requesting ess/maestro3_assp_minisrc.fw
[   25.440865] lp: driver loaded but no devices found
[   25.726577] Adding 2104504k swap on /dev/sda3.  Priority:-1 extents:1 across:2104504k
[   26.357443] EXT3 FS on sda4, internal journal
[   28.226272] type=1505 audit(1253699872.347:2): operation="profile_load" name="/sbin/dhclient-script" name2="default" pid=2009
[   28.227068] type=1505 audit(1253699872.347:3): operation="profile_load" name="/sbin/dhclient3" name2="default" pid=2009
[   28.227412] type=1505 audit(1253699872.351:4): operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" name2="default" pid=2009
[   28.227623] type=1505 audit(1253699872.351:5): operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" name2="default" pid=2009
[   28.798989] type=1505 audit(1253699872.919:6): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=2014
[   28.800102] type=1505 audit(1253699872.923:7): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=2014
[   28.933125] type=1505 audit(1253699873.055:8): operation="profile_load" name="/usr/sbin/mysqld" name2="default" pid=2018
[   29.047718] type=1505 audit(1253699873.171:9): operation="profile_load" name="/usr/sbin/tcpdump" name2="default" pid=2022
[   39.564104] spurious 8259A interrupt: IRQ7.
[   40.820642] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   40.820653] Bluetooth: BNEP filters: protocol multicast
[   41.346668] Bridge firewalling registered
[   43.479559] mtrr: base(0xf2000000) is not aligned on a size(0x5000000) boundary
[   44.068818] ppdev: user-space parallel port driver
[   46.091461] [drm] Initialized drm 1.1.0 20060810
[   46.117831] pci 0000:01:01.0: found PCI INT A -> IRQ 11
[   46.117853] pci 0000:01:01.0: sharing IRQ 11 with 0000:00:04.0
[   46.117864] pci 0000:01:01.0: sharing IRQ 11 with 0000:00:04.1
[   46.118518] [drm] Initialized savage 2.4.1 20050313 on minor 0
[   46.165954] mtrr: base(0xf2000000) is not aligned on a size(0x5000000) boundary
[   48.879696] eth0: found link beat
[   48.879716] eth0: autonegotiation complete: 100baseT-FD selected
[   56.974192] eth0: no IPv6 routers present
[  116.261454] Inbound IN=hso0 OUT= MAC= SRC=81.107.213.200 DST=89.194.193.213 LEN=52 TOS=0x00 PREC=0x00 TTL=112 ID=6441 DF PROTO=TCP SPT=49375 DPT=15027 WINDOW=8192 RES=0x00 SYN URGP=0 
[  116.582324] Inbound IN=hso0 OUT= MAC= SRC=81.107.213.200 DST=89.194.193.213 LEN=47 TOS=0x00 PREC=0x00 TTL=112 ID=6444 PROTO=UDP SPT=59859 DPT=15027 LEN=27 
[  119.263068] Inbound IN=hso0 OUT= MAC= SRC=81.107.213.200 DST=89.194.193.213 LEN=52 TOS=0x00 PREC=0x00 TTL=112 ID=6453 DF PROTO=TCP SPT=49375 DPT=15027 WINDOW=8192 RES=0x00 SYN URGP=0 
[  125.262306] Inbound IN=hso0 OUT= MAC= SRC=81.107.213.200 DST=89.194.193.213 LEN=48 TOS=0x00 PREC=0x00 TTL=112 ID=6489 DF PROTO=TCP SPT=49375 DPT=15027 WINDOW=8192 RES=0x00 SYN URGP=0 
[  178.699303] Inbound IN=hso0 OUT= MAC= SRC=86.169.87.108 DST=89.194.193.213 LEN=52 TOS=0x00 PREC=0x00 TTL=104 ID=1145 DF PROTO=TCP SPT=49285 DPT=41190 WINDOW=8192 RES=0x00 SYN URGP=0 
[  178.700191] Inbound IN=hso0 OUT= MAC= SRC=86.169.87.108 DST=89.194.193.213 LEN=47 TOS=0x00 PREC=0x00 TTL=104 ID=1147 PROTO=UDP SPT=18098 DPT=41190 LEN=27 
[  181.699959] Inbound IN=hso0 OUT= MAC= SRC=86.169.87.108 DST=89.194.193.213 LEN=52 TOS=0x00 PREC=0x00 TTL=104 ID=1148 DF PROTO=TCP SPT=49285 DPT=41190 WINDOW=8192 RES=0x00 SYN URGP=0 
[  187.733222] Inbound IN=hso0 OUT= MAC= SRC=86.169.87.108 DST=89.194.193.213 LEN=48 TOS=0x00 PREC=0x00 TTL=104 ID=1149 DF PROTO=TCP SPT=49285 DPT=41190 WINDOW=8192 RES=0x00 SYN URGP=0

---

