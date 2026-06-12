---
title: "ata3 failure during bootup"
date: 2008-11-01
forum: General Help
---

### Post by chipw on 2008-11-01
```

[   54.073211] ata3.01: qc timeout (cmd 0xa1)
[   54.090471] ata3.01: failed to IDENTIFY (I/O error, err_mask=0x4)
[   54.090477] ata3: failed to recover some devices, retrying in 5 secs
[   64.116445] ata3: port is slow to respond, please be patient (Status 0x80)
[   69.108123] ata3: device not ready (errno=-16), forcing hardreset

```

I am getting the above every time I boot up ubuntu, it repeats 3 times then quits and continues. (Adds about 3 minutes to the bootup time)

This is the last line, I believe, before it goes on to ACPI, PCI, SCSI and more:

```

[  160.244227] ata_piix 0000:00:1f.2: MAP [ P1 -- P0 -- ]

```

Is it possible this is related to my cd drive? (It doesn't work, maybe not recognized at all)

I've attached my entire dmesg .txt file

OK, so attaching it is too big, so here it is -

```

[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.24-19-generic (buildd@terranova) (gcc version 4.2.3 (Ubuntu 4.2.3-2ubuntu7)) #1 SMP Wed Aug 20 22:56:21 UTC 2008 (Ubuntu 2.6.24-19.41-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
[    0.000000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000007fff0000 (usable)
[    0.000000]  BIOS-e820: 000000007fff0000 - 000000007fff3000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000007fff3000 - 0000000080000000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000fec00000 - 0000000100000000 (reserved)
[    0.000000] 1151MB HIGHMEM available.
[    0.000000] 896MB LOWMEM available.
[    0.000000] found SMP MP-table at 000f5d10
[    0.000000] Entering add_active_range(0, 0, 524272) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   229376
[    0.000000]   HighMem    229376 ->   524272
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   524272
[    0.000000] On node 0 totalpages: 524272
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 1760 pages used for memmap
[    0.000000]   Normal zone: 223520 pages, LIFO batch:31
[    0.000000]   HighMem zone: 2303 pages used for memmap
[    0.000000]   HighMem zone: 292593 pages, LIFO batch:31
[    0.000000]   Movable zone: 0 pages used for memmap
[    0.000000] DMI 2.2 present.
[    0.000000] ACPI: RSDP signature @ 0xC00F95E0 checksum 0
[    0.000000] ACPI: RSDP 000F95E0, 0014 (r0 IntelR)
[    0.000000] ACPI: RSDT 7FFF3000, 002C (r1 IntelR AWRDACPI 42302E31 AWRD        0)
[    0.000000] ACPI: FACP 7FFF3040, 0074 (r1 IntelR AWRDACPI 42302E31 AWRD        0)
[    0.000000] ACPI: DSDT 7FFF30C0, 496A (r1 INTELR AWRDACPI     1000 MSFT  100000E)
[    0.000000] ACPI: FACS 7FFF0000, 0040
[    0.000000] ACPI: APIC 7FFF7A40, 0068 (r1 IntelR AWRDACPI 42302E31 AWRD        0)
[    0.000000] ACPI: PM-Timer IO Port: 0x408
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] Processor #0 15:3 APIC version 20
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
[    0.000000] Processor #1 15:3 APIC version 20
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] Allocating PCI resources starting at 88000000 (gap: 80000000:7ec00000)
[    0.000000] swsusp: Registered nosave memory region: 000000000009f000 - 00000000000a0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000a0000 - 00000000000f0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000f0000 - 0000000000100000
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 520177
[    0.000000] Kernel command line: root=UUID=e346a514-fbed-4464-a5bd-fb596e0b2257 ro vga=792
[    0.000000] mapped APIC to ffffb000 (fee00000)
[    0.000000] mapped IOAPIC to ffffa000 (fec00000)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] Detected 3407.844 MHz processor.
[   18.558770] Console: colour dummy device 80x25
[   18.558774] console [tty0] enabled
[   18.559299] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[   18.559723] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[   18.664055] Memory: 2066680k/2097088k available (2177k kernel code, 29116k reserved, 1006k data, 368k init, 1179584k highmem)
[   18.664074] virtual kernel memory layout:
[   18.664075]     fixmap  : 0xfff4b000 - 0xfffff000   ( 720 kB)
[   18.664076]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   18.664077]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
[   18.664078]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
[   18.664078]       .init : 0xc0421000 - 0xc047d000   ( 368 kB)
[   18.664079]       .data : 0xc03204c4 - 0xc041bdc4   (1006 kB)
[   18.664080]       .text : 0xc0100000 - 0xc03204c4   (2177 kB)
[   18.664096] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   18.664145] SLUB: Genslabs=11, HWalign=64, Order=0-1, MinObjects=4, CPUs=2, Nodes=1
[   18.744043] Calibrating delay using timer specific routine.. 6820.73 BogoMIPS (lpj=13641472)
[   18.744075] Security Framework initialized
[   18.744083] SELinux:  Disabled at boot.
[   18.744100] AppArmor: AppArmor initialized
[   18.744105] Failure registering capabilities with primary security module.
[   18.744115] Mount-cache hash table entries: 512
[   18.744246] Initializing cgroup subsys ns
[   18.744253] Initializing cgroup subsys cpuacct
[   18.744266] CPU: After generic identify, caps: bfebfbff 00000000 00000000 00000000 0000441d 00000000 00000000 00000000
[   18.744274] monitor/mwait feature present.
[   18.744277] using mwait in idle threads.
[   18.744284] CPU: Trace cache: 12K uops, L1 D cache: 16K
[   18.744288] CPU: L2 cache: 1024K
[   18.744292] CPU: Physical Processor ID: 0
[   18.744295] CPU: After all inits, caps: bfebfbff 00000000 00000000 0000b180 0000441d 00000000 00000000 00000000
[   18.744306] Compat vDSO mapped to ffffe000.
[   18.744323] Checking 'hlt' instruction... OK.
[   18.760435] SMP alternatives: switching to UP code
[   18.762157] Early unpacking initramfs... done
[   19.034914] ACPI: Core revision 20070126
[   19.034963] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[   19.049435] CPU0: Intel(R) Pentium(R) 4 CPU 3.40GHz stepping 04
[   19.049455] SMP alternatives: switching to SMP code
[   19.050200] Booting processor 1/1 eip 3000
[   19.060294] Initializing CPU#1
[   19.139413] Calibrating delay using timer specific routine.. 6815.93 BogoMIPS (lpj=13631878)
[   19.139423] CPU: After generic identify, caps: bfebfbff 00000000 00000000 00000000 0000441d 00000000 00000000 00000000
[   19.139429] monitor/mwait feature present.
[   19.139435] CPU: Trace cache: 12K uops, L1 D cache: 16K
[   19.139438] CPU: L2 cache: 1024K
[   19.139440] CPU: Physical Processor ID: 0
[   19.139442] CPU: After all inits, caps: bfebfbff 00000000 00000000 0000b180 0000441d 00000000 00000000 00000000
[   19.139695] CPU1: Intel(R) Pentium(R) 4 CPU 3.40GHz stepping 04
[   19.139754] Total of 2 processors activated (13636.67 BogoMIPS).
[   19.139884] ENABLING IO-APIC IRQs
[   19.140054] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[   19.287312] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
[   19.307298] Brought up 2 CPUs
[   19.307323] CPU0 attaching sched-domain:
[   19.307326]  domain 0: span 03
[   19.307328]   groups: 01 02
[   19.307331]   domain 1: span 03
[   19.307333]    groups: 03
[   19.307335] CPU1 attaching sched-domain:
[   19.307336]  domain 0: span 03
[   19.307338]   groups: 02 01
[   19.307341]   domain 1: span 03
[   19.307342]    groups: 03
[   19.307589] net_namespace: 64 bytes
[   19.307598] Booting paravirtualized kernel on bare hardware
[   19.308105] Time:  5:53:14  Date: 11/01/08
[   19.308130] NET: Registered protocol family 16
[   19.308371] EISA bus registered
[   19.308378] ACPI: bus type pci registered
[   19.332253] PCI: PCI BIOS revision 2.10 entry at 0xfb720, last bus=3
[   19.332258] PCI: Using configuration type 1
[   19.332266] Setting up standard PCI resources
[   19.333936] ACPI: EC: Look up EC in DSDT
[   19.337701] ACPI: Interpreter enabled
[   19.337707] ACPI: (supports S0 S1 S4 S5)
[   19.337724] ACPI: Using IOAPIC for interrupt routing
[   19.342327] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   19.342796] Force enabled HPET at base address 0xfed00000
[   19.342802] PCI quirk: region 0400-047f claimed by ICH4 ACPI/GPIO/TCO
[   19.342808] PCI quirk: region 0480-04bf claimed by ICH4 GPIO
[   19.343455] PCI: Transparent bridge - 0000:00:1e.0
[   19.343485] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   19.343617] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.HUB0._PRT]
[   19.350199] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 7 9 10 11 *12 14 15)
[   19.350305] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 *5 7 9 10 11 12 14 15)
[   19.350407] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 7 9 10 *11 12 14 15)
[   19.350508] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 7 9 *10 11 12 14 15)
[   19.350610] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.
[   19.350714] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.
[   19.350818] ACPI: PCI Interrupt Link [LNK0] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.
[   19.350922] ACPI: PCI Interrupt Link [LNK1] (IRQs *3 4 5 7 9 10 11 12 14 15)
[   19.451014] ACPI: Power Resource [PFAN] (on)
[   19.451069] Linux Plug and Play Support v0.97 (c) Adam Belay
[   19.451110] pnp: PnP ACPI init
[   19.451120] ACPI: bus type pnp registered
[   19.453787] pnpacpi: exceeded the max number of mem resources: 12
[   19.453856] pnp: PnP ACPI: found 13 devices
[   19.453860] ACPI: ACPI bus type pnp unregistered
[   19.453866] PnPBIOS: Disabled by ACPI PNP
[   19.454141] PCI: Using ACPI for IRQ routing
[   19.454147] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   19.486883] NET: Registered protocol family 8
[   19.486887] NET: Registered protocol family 20
[   19.486991] hpet clockevent registered
[   19.486996] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[   19.487003] hpet0: 3 64-bit timers, 14318180 Hz
[   19.488044] AppArmor: AppArmor Filesystem Enabled
[   19.490868] Time: tsc clocksource has been installed.
[   19.502897] system 00:01: ioport range 0xb78-0xb7b has been reserved
[   19.502903] system 00:01: ioport range 0xf78-0xf7b has been reserved
[   19.502907] system 00:01: ioport range 0xa78-0xa7b has been reserved
[   19.502911] system 00:01: ioport range 0xe78-0xe7b has been reserved
[   19.502915] system 00:01: ioport range 0xbbc-0xbbf has been reserved
[   19.502919] system 00:01: ioport range 0xfbc-0xfbf has been reserved
[   19.502923] system 00:01: ioport range 0x4d0-0x4d1 has been reserved
[   19.502927] system 00:01: ioport range 0x294-0x297 has been reserved
[   19.502941] system 00:0a: ioport range 0x400-0x4bf could not be reserved
[   19.502950] system 00:0c: iomem range 0xf0000-0xf3fff could not be reserved
[   19.502954] system 00:0c: iomem range 0xf4000-0xf7fff could not be reserved
[   19.502959] system 00:0c: iomem range 0xf8000-0xfbfff could not be reserved
[   19.502963] system 00:0c: iomem range 0xfc000-0xfffff could not be reserved
[   19.502967] system 00:0c: iomem range 0x7fff0000-0x7fffffff could not be reserved
[   19.502972] system 00:0c: iomem range 0x0-0x9ffff could not be reserved
[   19.502977] system 00:0c: iomem range 0x100000-0x7ffeffff could not be reserved
[   19.502984] system 00:0c: iomem range 0xfec00000-0xfec00fff could not be reserved
[   19.502989] system 00:0c: iomem range 0xfec01000-0xfed8ffff could not be reserved
[   19.502994] system 00:0c: iomem range 0xfee00000-0xfee00fff could not be reserved
[   19.502999] system 00:0c: iomem range 0xffb00000-0xffb7ffff could not be reserved
[   19.503004] system 00:0c: iomem range 0xfff00000-0xffffffff could not be reserved
[   19.533449] PCI: Bridge: 0000:00:01.0
[   19.533454]   IO window: a000-afff
[   19.533460]   MEM window: f8000000-f9ffffff
[   19.533465]   PREFETCH window: e8000000-f7ffffff
[   19.533471] PCI: Bridge: 0000:00:03.0
[   19.533475]   IO window: 9000-9fff
[   19.533480]   MEM window: fc000000-fc0fffff
[   19.533484]   PREFETCH window: disabled.
[   19.533491] PCI: Bridge: 0000:00:1e.0
[   19.533495]   IO window: 7000-8fff
[   19.533501]   MEM window: fa000000-fbffffff
[   19.533505]   PREFETCH window: disabled.
[   19.533526] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[   19.533537] NET: Registered protocol family 2
[   19.570809] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[   19.571113] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[   19.571682] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[   19.572076] TCP: Hash tables configured (established 131072 bind 65536)
[   19.572081] TCP reno registered
[   19.582908] checking if image is initramfs... it is
[   19.986218] Switched to high resolution mode on CPU 1
[   19.990076] Switched to high resolution mode on CPU 0
[   20.121580] Freeing initrd memory: 7732k freed
[   20.122470] audit: initializing netlink socket (disabled)
[   20.122491] audit(1225518794.332:1): initialized
[   20.122726] highmem bounce pool size: 64 pages
[   20.124919] VFS: Disk quotas dquot_6.5.1
[   20.125009] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   20.125150] io scheduler noop registered
[   20.125154] io scheduler anticipatory registered
[   20.125158] io scheduler deadline registered
[   20.125170] io scheduler cfq registered (default)
[   20.125253] Boot video device is 0000:01:00.0
[   20.125591] isapnp: Scanning for PnP cards...
[   20.476671] isapnp: No Plug & Play device found
[   20.509455] Real Time Clock Driver v1.12ac
[   20.509572] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   20.509686] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   20.510424] 00:07: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   20.511366] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   20.511442] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[   20.511560] PNP: PS/2 Controller [PNP0303:PS2K] at 0x60,0x64 irq 1
[   20.511565] PNP: PS/2 appears to have AUX port disabled, if this is incorrect please boot with i8042.nopnp
[   20.511982] serio: i8042 KBD port at 0x60,0x64 irq 1
[   20.529444] mice: PS/2 mouse device common for all mice
[   20.529593] EISA: Probing bus 0 at eisa.0
[   20.529625] Cannot allocate resource for EISA slot 7
[   20.529628] Cannot allocate resource for EISA slot 8
[   20.529631] EISA: Detected 0 cards.
[   20.529636] cpuidle: using governor ladder
[   20.529639] cpuidle: using governor menu
[   20.529718] NET: Registered protocol family 1
[   20.529747] Using IPI No-Shortcut mode
[   20.529778] registered taskstats version 1
[   20.529877]   Magic number: 0:970:869
[   20.529942]   hash matches device ptyw7
[   20.529951]   hash matches device ptyta
[   20.529991] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[   20.529994] EDD information not available.
[   20.530255] Freeing unused kernel memory: 368k freed
[   20.550407] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[   20.633992] vesafb: framebuffer at 0xe8000000, mapped to 0xf8880000, using 4608k, total 16384k
[   20.634004] vesafb: mode is 1024x768x24, linelength=3072, pages=6
[   20.634008] vesafb: protected mode interface info at c000:551b
[   20.634012] vesafb: pmi: set display start = c00c55af, set palette = c00c55fb
[   20.634016] vesafb: pmi: ports = a010 a016 a054 a038 a03c a05c a000 a004 a0b0 a0b2 a0b4 
[   20.634028] vesafb: scrolling: redraw
[   20.634032] vesafb: Truecolor: size=0:8:8:8, shift=0:16:8:0
[   20.634159] Console: switching to colour frame buffer device 128x48
[   20.671153] fb0: VESA VGA frame buffer device
[   20.809463] fuse init (API version 7.9)
[   21.120232] ACPI: Fan [FAN] (on)
[   21.224295] ACPI: Invalid passive threshold
[   21.324065] ACPI: Thermal Zone [THRM] (61 C)
[   21.492632] usbcore: registered new interface driver usbfs
[   21.493096] usbcore: registered new interface driver hub
[   21.502405] usbcore: registered new device driver usb
[   21.505217] USB Universal Host Controller Interface driver v3.0
[   21.505847] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 16 (level, low) -> IRQ 16
[   21.506502] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[   21.506508] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[   21.507176] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[   21.507780] uhci_hcd 0000:00:1d.0: irq 16, io base 0x0000bc00
[   21.508384] usb usb1: configuration #1 chosen from 1 choice
[   21.508832] hub 1-0:1.0: USB hub found
[   21.509112] hub 1-0:1.0: 2 ports detected
[   21.612456] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 19 (level, low) -> IRQ 17
[   21.613034] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[   21.613040] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[   21.613454] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[   21.628311] uhci_hcd 0000:00:1d.1: irq 17, io base 0x0000b000
[   21.643401] usb usb2: configuration #1 chosen from 1 choice
[   21.643435] hub 2-0:1.0: USB hub found
[   21.643443] hub 2-0:1.0: 2 ports detected
[   21.748263] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 18
[   21.748277] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[   21.748282] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[   21.748321] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
[   21.748349] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000b400
[   21.748500] usb usb3: configuration #1 chosen from 1 choice
[   21.748536] hub 3-0:1.0: USB hub found
[   21.748545] hub 3-0:1.0: 2 ports detected
[   21.900013] ACPI: PCI Interrupt 0000:00:1d.3[A] -> GSI 16 (level, low) -> IRQ 16
[   21.916103] PCI: Setting latency timer of device 0000:00:1d.3 to 64
[   21.916109] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[   21.931837] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 4
[   21.949134] uhci_hcd 0000:00:1d.3: irq 16, io base 0x0000b800
[   21.949304] usb usb4: configuration #1 chosen from 1 choice
[   21.949346] hub 4-0:1.0: USB hub found
[   21.949353] hub 4-0:1.0: 2 ports detected
[   22.032114] Intel(R) PRO/1000 Network Driver - version 7.3.20-k2-NAPI
[   22.047974] Copyright (c) 1999-2006 Intel Corporation.
[   22.062818] ACPI: PCI Interrupt 0000:00:1d.7[D] -> GSI 23 (level, low) -> IRQ 19
[   22.078480] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[   22.078485] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[   22.093900] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 5
[   22.112731] PCI: cache line size of 128 is not supported by device 0000:00:1d.7
[   22.112745] ehci_hcd 0000:00:1d.7: irq 19, io mem 0xfc100000
[   22.143453] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   22.159800] usb usb5: configuration #1 chosen from 1 choice
[   22.176429] hub 5-0:1.0: USB hub found
[   22.192874] hub 5-0:1.0: 8 ports detected
[   22.210596] SCSI subsystem initialized
[   22.311374] ACPI: PCI Interrupt 0000:02:01.0[A] -> GSI 18 (level, low) -> IRQ 18
[   22.314266] libata version 3.00 loaded.
[   22.326833] PCI: Setting latency timer of device 0000:02:01.0 to 64
[   22.373864] FDC 0 is a post-1991 82077
[   22.589656] e1000: 0000:02:01.0: e1000_probe: (PCI:33MHz:32-bit) 00:50:8d:d5:fe:1d
[   22.780621] e1000: eth0: e1000_probe: Intel(R) PRO/1000 Network Connection
[   22.800071] ACPI: PCI Interrupt 0000:03:02.0[A] -> GSI 18 (level, low) -> IRQ 18
[   22.865581] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[18]  MMIO=[fb005000-fb0057ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[   22.907911] sata_sil 0000:03:03.0: version 2.3
[   22.907954] ACPI: PCI Interrupt 0000:03:03.0[A] -> GSI 19 (level, low) -> IRQ 17
[   22.925434] scsi0 : sata_sil
[   22.944754] scsi1 : sata_sil
[   22.965274] ata1: SATA max UDMA/100 mmio m512@0xfb004000 tf 0xfb004080 irq 17
[   22.986238] ata2: SATA max UDMA/100 mmio m512@0xfb004000 tf 0xfb0040c0 irq 17
[   23.236615] usb 4-1: new full speed USB device using uhci_hcd and address 2
[   23.312501] ata1: SATA link down (SStatus 0 SControl 310)
[   23.425621] usb 4-1: configuration #1 chosen from 1 choice
[   23.639949] ata2: SATA link down (SStatus 0 SControl 310)
[   23.656197] ata_piix 0000:00:1f.1: version 2.12
[   23.656219] ACPI: PCI Interrupt 0000:00:1f.1[A] -> GSI 18 (level, low) -> IRQ 18
[   23.672965] PCI: Setting latency timer of device 0000:00:1f.1 to 64
[   23.673022] scsi2 : ata_piix
[   23.683876] usb 4-2: new low speed USB device using uhci_hcd and address 3
[   23.706097] scsi3 : ata_piix
[   23.723134] ata3: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xf000 irq 14
[   23.739525] ata4: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xf008 irq 15
[   23.856844] usb 4-2: configuration #1 chosen from 1 choice
[   23.888781] usbcore: registered new interface driver hiddev
[   23.924012] input: Logitech Trackball as /devices/pci0000:00/0000:00:1d.3/usb4/4-2/4-2:1.0/input/input2
[   23.964447] input,hidraw0: USB HID v1.10 Mouse [Logitech Trackball] on usb-0000:00:1d.3-2
[   23.982114] usbcore: registered new interface driver usbhid
[   23.999291] /build/buildd/linux-2.6.24/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
[   24.191162] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[00508d0000d4fe1d]
[   54.073211] ata3.01: qc timeout (cmd 0xa1)
[   54.090471] ata3.01: failed to IDENTIFY (I/O error, err_mask=0x4)
[   54.090477] ata3: failed to recover some devices, retrying in 5 secs
[   64.116445] ata3: port is slow to respond, please be patient (Status 0x80)
[   69.108123] ata3: device not ready (errno=-16), forcing hardreset
[   99.442553] ata3.01: qc timeout (cmd 0xa1)
[   99.459794] ata3.01: failed to IDENTIFY (I/O error, err_mask=0x4)
[   99.477104] ata3: failed to recover some devices, retrying in 5 secs
[  109.520730] ata3: port is slow to respond, please be patient (Status 0x80)
[  114.512403] ata3: device not ready (errno=-16), forcing hardreset
[  144.845839] ata3.01: qc timeout (cmd 0xa1)
[  144.862948] ata3.01: failed to IDENTIFY (I/O error, err_mask=0x4)
[  144.880416] ata3: failed to recover some devices, retrying in 5 secs
[  154.925012] ata3: port is slow to respond, please be patient (Status 0x80)
[  159.916690] ata3: device not ready (errno=-16), forcing hardreset
[  160.244227] ata_piix 0000:00:1f.2: MAP [ P1 -- P0 -- ]
[  160.261699] ACPI: PCI Interrupt 0000:00:1f.2[A] -> GSI 18 (level, low) -> IRQ 18
[  160.279456] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[  160.279509] scsi4 : ata_piix
[  160.297382] scsi5 : ata_piix
[  160.315330] ata5: SATA max UDMA/133 cmd 0xc000 ctl 0xc400 bmdma 0xd000 irq 18
[  160.332687] ata6: SATA max UDMA/133 cmd 0xc800 ctl 0xcc00 bmdma 0xd008 irq 18
[  160.514207] ata5.00: ATA-6: WDC WD2500JD-00HBB0, 08.02D08, max UDMA/133
[  160.531214] ata5.00: 488397168 sectors, multi 16: LBA48 
[  160.566117] ata5.00: configured for UDMA/133
[  160.744820] ata6.00: ATA-6: WDC WD2500JD-00HBB0, 08.02D08, max UDMA/133
[  160.761311] ata6.00: 488397168 sectors, multi 16: LBA48 
[  160.792714] ata6.00: configured for UDMA/133
[  160.808718] scsi 4:0:0:0: Direct-Access     ATA      WDC WD2500JD-00H 08.0 PQ: 0 ANSI: 5
[  160.825086] scsi 5:0:0:0: Direct-Access     ATA      WDC WD2500JD-00H 08.0 PQ: 0 ANSI: 5
[  160.856590] Driver 'sd' needs updating - please use bus_type methods
[  160.873193] sd 4:0:0:0: [sda] 488397168 512-byte hardware sectors (250059 MB)
[  160.889822] sd 4:0:0:0: [sda] Write Protect is off
[  160.905877] sd 4:0:0:0: [sda] Mode Sense: 00 3a 00 00
[  160.905901] sd 4:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[  160.922296] sd 4:0:0:0: [sda] 488397168 512-byte hardware sectors (250059 MB)
[  160.938561] sd 4:0:0:0: [sda] Write Protect is off
[  160.954658] sd 4:0:0:0: [sda] Mode Sense: 00 3a 00 00
[  160.954692] sd 4:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[  160.971178]  sda: sda1 sda2 < sda5 >
[  161.024592] sd 4:0:0:0: [sda] Attached SCSI disk
[  161.040846] sd 5:0:0:0: [sdb] 488397168 512-byte hardware sectors (250059 MB)
[  161.057125] sd 5:0:0:0: [sdb] Write Protect is off
[  161.073115] sd 5:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[  161.073392] sd 5:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[  161.090409] sd 5:0:0:0: [sdb] 488397168 512-byte hardware sectors (250059 MB)
[  161.106950] sd 5:0:0:0: [sdb] Write Protect is off
[  161.123337] sd 5:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[  161.123361] sd 5:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[  161.139698]  sdb: sdb1
[  161.173097] sd 5:0:0:0: [sdb] Attached SCSI disk
[  161.196987] sd 4:0:0:0: Attached scsi generic sg0 type 0
[  161.213107] sd 5:0:0:0: Attached scsi generic sg1 type 0
[  161.496980] Attempting manual resume
[  161.512433] swsusp: Resume From Partition 8:5
[  161.512435] PM: Checking swsusp image.
[  161.512587] PM: Resume from disk failed.
[  161.562430] EXT3-fs: INFO: recovery required on readonly filesystem.
[  161.577885] EXT3-fs: write access will be enabled during recovery.
[  162.156996] kjournald starting.  Commit interval 5 seconds
[  162.157006] EXT3-fs: recovery complete.
[  162.159178] EXT3-fs: mounted filesystem with ordered data mode.
[  169.772694] input: PC Speaker as /devices/platform/pcspkr/input/input3
[  169.920107] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[  169.992027] Linux agpgart interface v0.102
[  170.045087] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[  170.127869] agpgart: Detected an Intel i875 Chipset.
[  170.149396] agpgart: AGP aperture is 128M @ 0xe0000000
[  170.315637] EDAC MC: Ver: 2.1.0 Aug 20 2008
[  170.396260] intel_rng: FWH not detected
[  170.432717] EDAC i82875p: i82875p init one
[  170.448723] PCI: Unable to reserve mem region #1:1000@fecf0000 for device 0000:00:06.0
[  170.465115] EDAC MC0: Giving out device to 'i82875p_edac' 'i82875p': DEV 0000:00:00.0
[  170.481118] EDAC PCI0: Giving out device to module 'i82875p_edac' controller 'EDAC PCI controller': DEV '0000:00:00.0' (POLLED)
[  170.682845] iTCO_vendor_support: vendor-support=0
[  170.734769] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.02 (26-Jul-2007)
[  170.751223] iTCO_wdt: Found a ICH5 or ICH5R TCO device (Version=1, TCOBASE=0x0460)
[  170.767808] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[  170.829270] input: Power Button (FF) as /devices/virtual/input/input4
[  170.874425] ACPI: Power Button (FF) [PWRF]
[  170.890715] input: Power Button (CM) as /devices/virtual/input/input5
[  170.930332] ACPI: Power Button (CM) [PWRB]
[  171.122424] parport_pc 00:08: reported by Plug and Play ACPI
[  171.139554] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
[  172.643864] e1000: eth0: e1000_watchdog: NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[  172.675591] ACPI: PCI Interrupt 0000:00:1f.5[B] -> GSI 17 (level, low) -> IRQ 20
[  172.693041] PCI: Setting latency timer of device 0000:00:1f.5 to 64
[  173.014861] intel8x0_measure_ac97_clock: measured 52819 usecs
[  173.032228] intel8x0: clocking to 48000
[  173.101290] usblp0: USB Bidirectional printer dev 2 if 0 alt 0 proto 2 vid 0x04F9 pid 0x016D
[  173.118431] usbcore: registered new interface driver usblp
[  173.371622] NET: Registered protocol family 10
[  173.395066] lo: Disabled Privacy Extensions
[  174.555893] lp0: using parport0 (interrupt-driven).
[  174.698659] Adding 6080560k swap on /dev/sda5.  Priority:-1 extents:1 across:6080560k
[  175.112979] EXT3 FS on sda1, internal journal
[  175.220950] device-mapper: uevent: version 1.0.3
[  175.220990] device-mapper: ioctl: 4.12.0-ioctl (2007-10-02) initialised: dm-devel@redhat.com
[  175.621187] kjournald starting.  Commit interval 5 seconds
[  175.621428] EXT3 FS on sdb1, internal journal
[  175.621431] EXT3-fs: recovery complete.
[  175.621557] EXT3-fs: mounted filesystem with ordered data mode.
[  176.099645] ip_tables: (C) 2000-2006 Netfilter Core Team
[  176.814070] No dock devices found.
[  177.945839] apm: BIOS not found.
[  178.138349] ppdev: user-space parallel port driver
[  178.350907] audit(1225518952.900:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=9420 profile="/usr/sbin/cupsd" namespace="default"
[  180.754592] Bluetooth: Core ver 2.11
[  180.755049] NET: Registered protocol family 31
[  180.755056] Bluetooth: HCI device and connection manager initialized
[  180.755062] Bluetooth: HCI socket layer initialized
[  180.773984] Bluetooth: L2CAP ver 2.9
[  180.773990] Bluetooth: L2CAP socket layer initialized
[  180.982953] Bluetooth: RFCOMM socket layer initialized
[  180.982974] Bluetooth: RFCOMM TTY layer initialized
[  180.982977] Bluetooth: RFCOMM ver 1.8
[  182.187031] [drm] Initialized drm 1.1.0 20060810
[  182.197359] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 16
[  182.197825] [drm] Initialized radeon 1.28.0 20060524 on minor 0
[  182.695339] agpgart: Found an AGP 3.0 compliant device at 0000:00:00.0.
[  182.695361] agpgart: Putting AGP V3 device at 0000:00:00.0 into 8x mode
[  182.695395] agpgart: Putting AGP V3 device at 0000:01:00.0 into 8x mode
[  183.049744] [drm] Setting GART location based on new memory map
[  183.049754] [drm] Loading R200 Microcode
[  183.049796] [drm] writeback test succeeded in 1 usecs
[  183.968575] eth0: no IPv6 routers present
[  197.844189] usb 4-1: usbfs: interface 0 claimed by usblp while 'brscan-skey-0.2' sets config #1

```
The very last line gets repeated many many many times, but that's another issue.

---

### Post by l1nuxb0x on 2008-12-04
is ata3 your cd drive?

Can you post your results from fdisk?

---

### Post by chipw on 2008-12-04
I discovered the problem - the dvd drive itself is bad. Gotta buy a new one, or wait and see if Santa brings me one for christmas. :)

---

### Post by l1nuxb0x on 2008-12-04
cool, glad to hear you got it figured out

---

