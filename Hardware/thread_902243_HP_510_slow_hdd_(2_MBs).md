---
title: "HP 510 slow hdd (2 MB/s)"
date: 2008-08-27
forum: Hardware
---

### Post by milosv on 2008-08-27
Hello

recently I installed new version of Hardy (using 7.04 before).

At first I had a problems with occasionaly freezing of system - every 1-5 minutes system got frozen at 1-4 seconds and then continued working further.

Now I do not have this problem, but the system (ie hdd) is very slow.
Look at this:

> 
/dev/hda:
 Timing cached reads:   722 MB in  2.00 seconds = 360.77 MB/sec
 Timing buffered disk reads:    6 MB in  3.00 seconds =   2.00 MB/sec



Attached I am sending my dmesg and lspci.

The system is not booting and behaving so slowly for 2 MB/s, but is at least twice so slow as 7.04 previously; and during normal work (ie looking at this forum) the cursor gets occassionaly freezes of ~0.2 seconds - enough to notice the lagging.

Has somebody idea what could I do here and where to start?
Thanks in advance.



> 
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.24-19-generic (buildd@terranova) (gcc version 4.2.3 (Ubuntu 4.2.3-2ubuntu7)) #1 SMP Wed Aug 20 22:56:21 UTC 2008 (Ubuntu 2.6.24-19.41-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000003f7d0000 (usable)
[    0.000000]  BIOS-e820: 000000003f7d0000 - 000000003f7efc00 (reserved)
[    0.000000]  BIOS-e820: 000000003f7efc00 - 000000003f7fb000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000003f7fb000 - 000000003f800000 (reserved)
[    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec02000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed20000 - 00000000fed9b000 (reserved)
[    0.000000]  BIOS-e820: 00000000feda0000 - 00000000fedc0000 (reserved)
[    0.000000]  BIOS-e820: 00000000ffb00000 - 00000000ffc00000 (reserved)
[    0.000000]  BIOS-e820: 00000000fff00000 - 0000000100000000 (reserved)
[    0.000000] 119MB HIGHMEM available.
[    0.000000] 896MB LOWMEM available.
[    0.000000] Entering add_active_range(0, 0, 260048) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   229376
[    0.000000]   HighMem    229376 ->   260048
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   260048
[    0.000000] On node 0 totalpages: 260048
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 1760 pages used for memmap
[    0.000000]   Normal zone: 223520 pages, LIFO batch:31
[    0.000000]   HighMem zone: 239 pages used for memmap
[    0.000000]   HighMem zone: 30433 pages, LIFO batch:7
[    0.000000]   Movable zone: 0 pages used for memmap
[    0.000000] DMI 2.3 present.
[    0.000000] ACPI: RSDP signature @ 0xC00FE270 checksum 0
[    0.000000] ACPI: RSDP 000FE270, 0014 (r0 HP    )
[    0.000000] ACPI: RSDT 3F7EFC84, 0034 (r1 HP     30C4     31100620 HP          1)
[    0.000000] ACPI: FACP 3F7EFC00, 0084 (r2 HP     30C4            2 HP          1)
[    0.000000] ACPI: DSDT 3F7EFD50, 6948 (r1 HP       DAU00     10000 MSFT  100000E)
[    0.000000] ACPI: FACS 3F7FAE80, 0040
[    0.000000] ACPI: APIC 3F7EFCB8, 005A (r1 HP     30C4            1 HP          1)
[    0.000000] ACPI: MCFG 3F7EFD14, 003C (r1 HP     30C4            1 HP          1)
[    0.000000] ACPI: SSDT 3F7F6698, 0371 (r1 HP       HPQPpc     1001 MSFT  100000E)
[    0.000000] ACPI: DMI detected: Hewlett-Packard
[    0.000000] ACPI: PM-Timer IO Port: 0x1008
[    0.000000] ACPI: Local APIC address 0xfec01000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] Processor #0 6:13 APIC version 20
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 1, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] Allocating PCI resources starting at 40000000 (gap: 3f800000:a0800000)
[    0.000000] swsusp: Registered nosave memory region: 000000000009f000 - 00000000000a0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000a0000 - 00000000000e0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000e0000 - 0000000000100000
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 258017
[    0.000000] Kernel command line: root=UUID=57ea1c62-18bb-459e-942c-0c5309224aa4 ro quiet splash
[    0.000000] mapped APIC to ffffb000 (fec01000)
[    0.000000] mapped IOAPIC to ffffa000 (fec00000)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] Detected 2128.060 MHz processor.
[    7.078616] Console: colour VGA+ 80x25
[    7.078619] console [tty0] enabled
[    7.078764] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    7.079023] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    7.105467] Memory: 1019044k/1040192k available (2177k kernel code, 20392k reserved, 1006k data, 368k init, 122688k highmem)
[    7.105477] virtual kernel memory layout:
[    7.105478]     fixmap  : 0xfff4b000 - 0xfffff000   ( 720 kB)
[    7.105479]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[    7.105480]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
[    7.105481]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
[    7.105482]       .init : 0xc0421000 - 0xc047d000   ( 368 kB)
[    7.105483]       .data : 0xc03204c4 - 0xc041bdc4   (1006 kB)
[    7.105484]       .text : 0xc0100000 - 0xc03204c4   (2177 kB)
[    7.105487] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[    7.105518] SLUB: Genslabs=11, HWalign=64, Order=0-1, MinObjects=4, CPUs=1, Nodes=1
[    7.185512] Calibrating delay using timer specific routine.. 4260.50 BogoMIPS (lpj=8521004)
[    7.185532] Security Framework initialized
[    7.185538] SELinux:  Disabled at boot.
[    7.185551] AppArmor: AppArmor initialized
[    7.185554] Failure registering capabilities with primary security module.
[    7.185561] Mount-cache hash table entries: 512
[    7.185665] Initializing cgroup subsys ns
[    7.185669] Initializing cgroup subsys cpuacct
[    7.185677] CPU: After generic identify, caps: afe9fbff 00100000 00000000 00000000 00000180 00000000 00000000 00000000
[    7.185687] CPU: L1 I cache: 32K, L1 D cache: 32K
[    7.185689] CPU: L2 cache: 2048K
[    7.185691] CPU: After all inits, caps: afe9fbff 00100000 00000000 00002040 00000180 00000000 00000000 00000000
[    7.185698] Compat vDSO mapped to ffffe000.
[    7.185708] Checking 'hlt' instruction... OK.
[    7.201841] SMP alternatives: switching to UP code
[    7.204537] Freeing SMP alternatives: 11k freed
[    7.204636] Early unpacking initramfs... done
[    7.497731] ACPI: Core revision 20070126
[    7.497796] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[    7.533099] CPU0: Intel(R) Pentium(R) M processor 2.13GHz stepping 08
[    7.533124] Total of 1 processors activated (4260.50 BogoMIPS).
[    7.533312] ENABLING IO-APIC IRQs
[    7.533496] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[    7.677379] Brought up 1 CPUs
[    7.677405] CPU0 attaching sched-domain:
[    7.677407]  domain 0: span 01
[    7.677409]   groups: 01
[    7.677555] net_namespace: 64 bytes
[    7.677564] Booting paravirtualized kernel on bare hardware
[    7.677941] Time: 11:03:35  Date: 08/27/08
[    7.677964] NET: Registered protocol family 16
[    7.678114] EISA bus registered
[    7.678138] ACPI: bus type pci registered
[    7.679209] PCI: PCI BIOS revision 2.10 entry at 0xf0322, last bus=3
[    7.679211] PCI: Using configuration type 1
[    7.679222] Setting up standard PCI resources
[    7.680528] ACPI: EC: Look up EC in DSDT
[    7.683476] ACPI: EC: non-query interrupt received, switching to interrupt mode
[    7.691964] ACPI: Interpreter enabled
[    7.691967] ACPI: (supports S0 S3 S4 S5)
[    7.691977] ACPI: Using IOAPIC for interrupt routing
[    7.697433] ACPI: EC: GPE = 0x10, I/O: command/status = 0x66, data = 0x62
[    7.697435] ACPI: EC: driver started in interrupt mode
[    7.697468] ACPI: PCI Root Bridge [C002] (0000:00)
[    7.697970] Force enabled HPET at base address 0xfed00000
[    7.697975] PCI quirk: region 1000-107f claimed by ICH6 ACPI/GPIO/TCO
[    7.697979] PCI quirk: region 1100-113f claimed by ICH6 GPIO
[    7.698295] PCI: Transparent bridge - 0000:00:1e.0
[    7.698358] ACPI: PCI Interrupt Routing Table [\_SB_.C002._PRT]
[    7.698544] ACPI: PCI Interrupt Routing Table [\_SB_.C002.C067._PRT]
[    7.713762] ACPI: PCI Interrupt Link [C0D8] (IRQs 10 *11)
[    7.713911] ACPI: PCI Interrupt Link [C0D9] (IRQs *10 11)
[    7.714057] ACPI: PCI Interrupt Link [C0DA] (IRQs *10 11)
[    7.714206] ACPI: PCI Interrupt Link [C0DB] (IRQs *10 11)
[    7.714351] ACPI: PCI Interrupt Link [C0EE] (IRQs *10 11)
[    7.714497] ACPI: PCI Interrupt Link [C0EF] (IRQs 10 *11)
[    7.714636] ACPI: PCI Interrupt Link [C0F0] (IRQs 10 11) *0, disabled.
[    7.714706] ACPI Exception (pci_link-0184): AE_NOT_FOUND, Evaluating _PRS [20070126]
[    7.714924] ACPI: Power Resource [C19E] (on)
[    7.714954] ACPI: Power Resource [C1A7] (on)
[    7.714987] Linux Plug and Play Support v0.97 (c) Adam Belay
[    7.715011] pnp: PnP ACPI init
[    7.715017] ACPI: bus type pnp registered
[    7.720928] pnp: PnP ACPI: found 12 devices
[    7.720930] ACPI: ACPI bus type pnp unregistered
[    7.720933] PnPBIOS: Disabled by ACPI PNP
[    7.721093] PCI: Using ACPI for IRQ routing
[    7.721095] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[    7.761320] NET: Registered protocol family 8
[    7.761322] NET: Registered protocol family 20
[    7.761451] hpet clockevent registered
[    7.761457] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[    7.761460] hpet0: 3 64-bit timers, 14318180 Hz
[    7.762489] AppArmor: AppArmor Filesystem Enabled
[    7.765314] Time: tsc clocksource has been installed.
[    7.773339] system 00:00: iomem range 0x0-0x9ffff could not be reserved
[    7.773341] system 00:00: iomem range 0xe0000-0xfffff could not be reserved
[    7.773344] system 00:00: iomem range 0x100000-0x3f7fffff could not be reserved
[    7.773351] system 00:09: ioport range 0x200-0x203 has been reserved
[    7.773353] system 00:09: ioport range 0x500-0x57f has been reserved
[    7.773356] system 00:09: iomem range 0xffb00000-0xffbfffff could not be reserved
[    7.773359] system 00:09: iomem range 0xfff00000-0xffffffff could not be reserved
[    7.773363] system 00:0a: ioport range 0x4d0-0x4d1 has been reserved
[    7.773365] system 00:0a: ioport range 0x1000-0x107f has been reserved
[    7.773367] system 00:0a: ioport range 0x1100-0x113f has been reserved
[    7.773370] system 00:0a: ioport range 0x1200-0x121f has been reserved
[    7.773372] system 00:0a: iomem range 0xe0000000-0xefffffff could not be reserved
[    7.773375] system 00:0a: iomem range 0xfec00000-0xfec000ff could not be reserved
[    7.773378] system 00:0a: iomem range 0xfed20000-0xfed8ffff could not be reserved
[    7.773380] system 00:0a: iomem range 0xfed90000-0xfed9afff could not be reserved
[    7.773384] system 00:0b: iomem range 0xfeda0000-0xfedbffff could not be reserved
[    7.773387] system 00:0b: iomem range 0xfec01000-0xfec01fff could not be reserved
[    7.803696] PCI: Bus 3, cardbus bridge: 0000:02:06.0
[    7.803698]   IO window: 00002400-000024ff
[    7.803703]   IO window: 00002800-000028ff
[    7.803708]   PREFETCH window: 40000000-43ffffff
[    7.803713]   MEM window: 44000000-47ffffff
[    7.803718] PCI: Bridge: 0000:00:1e.0
[    7.803720]   IO window: 2000-2fff
[    7.803726]   MEM window: d0000000-d05fffff
[    7.803729]   PREFETCH window: disabled.
[    7.803745] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[    7.803764] ACPI: PCI Interrupt 0000:02:06.0[A] -> GSI 18 (level, low) -> IRQ 16
[    7.803776] NET: Registered protocol family 2
[    7.841331] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    7.841515] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    7.842170] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    7.842580] TCP: Hash tables configured (established 131072 bind 65536)
[    7.842583] TCP reno registered
[    7.853422] checking if image is initramfs... it is
[    8.265145] Switched to high resolution mode on CPU 0
[    8.416777] Freeing initrd memory: 7321k freed
[    8.417362] audit: initializing netlink socket (disabled)
[    8.417377] audit(1219835015.180:1): initialized
[    8.417538] highmem bounce pool size: 64 pages
[    8.419101] VFS: Disk quotas dquot_6.5.1
[    8.419168] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    8.419292] io scheduler noop registered
[    8.419295] io scheduler anticipatory registered
[    8.419296] io scheduler deadline registered
[    8.419310] io scheduler cfq registered (default)
[    8.419324] Boot video device is 0000:00:02.0
[    8.419367] PCI: Firmware left 0000:02:08.0 e100 interrupts enabled, disabling
[    8.419581] isapnp: Scanning for PnP cards...
[    8.773560] isapnp: No Plug & Play device found
[    8.795311] Real Time Clock Driver v1.12ac
[    8.795413] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[    8.795927] ACPI: PCI Interrupt 0000:00:1e.3[B] -> GSI 17 (level, low) -> IRQ 17
[    8.795937] ACPI: PCI interrupt for device 0000:00:1e.3 disabled
[    8.796432] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[    8.796491] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[    8.796570] PNP: PS/2 Controller [PNP0303:C1A4,PNP0f13:C1A5] at 0x60,0x64 irq 1,12
[    8.817618] serio: i8042 KBD port at 0x60,0x64 irq 1
[    8.817622] serio: i8042 AUX port at 0x60,0x64 irq 12
[    8.828879] mice: PS/2 mouse device common for all mice
[    8.828971] EISA: Probing bus 0 at eisa.0
[    8.828978] Cannot allocate resource for EISA slot 1
[    8.828980] Cannot allocate resource for EISA slot 2
[    8.828981] Cannot allocate resource for EISA slot 3
[    8.829000] EISA: Detected 0 cards.
[    8.829003] cpuidle: using governor ladder
[    8.829005] cpuidle: using governor menu
[    8.829087] NET: Registered protocol family 1
[    8.829111] Using IPI No-Shortcut mode
[    8.829140] registered taskstats version 1
[    8.829221]   Magic number: 4:719:75
[    8.829313] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    8.829315] EDD information not available.
[    8.829496] Freeing unused kernel memory: 368k freed
[    8.848852] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[   10.015465] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[   10.015471] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[   10.015811] Probing IDE interface ide0...
[   10.600322] hdb: TSSTcorpCD/DVDW TS-L632D, ATAPI CD/DVD-ROM drive
[   10.936170] hda: WDC WD600UE-22KVT0, ATA DISK drive
[   10.936179] Probing IDE interface ide1...
[   11.495656] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[   11.509084] hdb: ATAPI 24X DVD-ROM DVD-R-RAM CD-R/RW drive, 2048kB Cache
[   11.509089] Uniform CD-ROM driver Revision: 3.20
[   11.515023] hda: max request size: 512KiB
[   11.568533] hda: 117210240 sectors (60011 MB) w/2048KiB Cache, CHS=16383/255/63
[   11.568620] hda: cache flushes supported
[   11.568642]  hda: hda1 hda2 < hda5 > hda3
[   11.660098] fuse init (API version 7.9)
[   11.676196] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[   11.676201] ACPI: Processor [C000] (supports 8 throttling states)
[   11.677941] ACPI: Thermal Zone [TZ1] (57 C)
[   12.420312] usbcore: registered new interface driver usbfs
[   12.420334] usbcore: registered new interface driver hub
[   12.430993] usbcore: registered new device driver usb
[   12.474212] USB Universal Host Controller Interface driver v3.0
[   12.476338] ACPI: PCI Interrupt 0000:00:1d.0[D] -> GSI 19 (level, low) -> IRQ 18
[   12.476349] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[   12.476353] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[   12.476701] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[   12.476732] uhci_hcd 0000:00:1d.0: irq 18, io base 0x00003020
[   12.476848] usb usb1: configuration #1 chosen from 1 choice
[   12.476868] hub 1-0:1.0: USB hub found
[   12.476872] hub 1-0:1.0: 2 ports detected
[   12.579289] ACPI: PCI Interrupt 0000:00:1d.7[D] -> GSI 19 (level, low) -> IRQ 18
[   12.579303] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[   12.579307] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[   12.579326] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 2
[   12.583225] ehci_hcd 0000:00:1d.7: debug port 1
[   12.583231] PCI: cache line size of 32 is not supported by device 0000:00:1d.7
[   12.583237] ehci_hcd 0000:00:1d.7: irq 18, io mem 0xd0780000
[   12.603145] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   12.603261] usb usb2: configuration #1 chosen from 1 choice
[   12.603281] hub 2-0:1.0: USB hub found
[   12.603287] hub 2-0:1.0: 8 ports detected
[   12.603329] e100: Intel(R) PRO/100 Network Driver, 3.5.23-k4-NAPI
[   12.603330] e100: Copyright(c) 1999-2006 Intel Corporation
[   12.704082] SCSI subsystem initialized
[   12.710579] ACPI: PCI Interrupt 0000:02:08.0[A] -> GSI 20 (level, low) -> IRQ 19
[   12.795564] libata version 3.00 loaded.
[   12.799664] e100: eth0: e100_probe: addr 0xd0002000, irq 19, MAC addr 00:16:d4:bb:69:bf
[   12.799678] ata_piix 0000:00:1f.1: version 2.12
[   12.799698] ACPI: PCI Interrupt 0000:00:1f.1[A] -> GSI 16 (level, low) -> IRQ 20
[   12.799720] PCI: Unable to reserve I/O region #1:8@1f0 for device 0000:00:1f.1
[   12.799722] ata_piix 0000:00:1f.1: failed to request/iomap BARs for port 0 (errno=-16)
[   12.799735] PCI: Setting latency timer of device 0000:00:1f.1 to 64
[   12.799936] scsi0 : ata_piix
[   12.800648] scsi1 : ata_piix
[   12.801100] ata1: DUMMY
[   12.801102] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x3588 irq 15
[   12.801142] ata2: port disabled. ignoring.
[   13.259595] Clocksource tsc unstable (delta = -5209848227 ns)
[   13.263066] Time: hpet clocksource has been installed.
[   13.339814] Attempting manual resume
[   13.339817] swsusp: Resume From Partition 3:3
[   13.339819] PM: Checking swsusp image.
[   13.342239] PM: Resume from disk failed.
[   13.366325] kjournald starting.  Commit interval 5 seconds
[   13.366333] EXT3-fs: mounted filesystem with ordered data mode.
[   13.390971] usb 1-1: new low speed USB device using uhci_hcd and address 2
[   13.531023] usb 1-1: configuration #1 chosen from 1 choice
[   13.643057] usb 1-2: new low speed USB device using uhci_hcd and address 3
[   14.124037] usb 1-2: configuration #1 chosen from 1 choice
[   60.034692] input: PC Speaker as /devices/platform/pcspkr/input/input2
[   60.719158] iTCO_vendor_support: vendor-support=0
[   60.794207] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.02 (26-Jul-2007)
[   60.794300] iTCO_wdt: Found a ICH6-M TCO device (Version=2, TCOBASE=0x1060)
[   60.794340] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   60.977033] parport_pc 00:02: reported by Plug and Play ACPI
[   60.977739] parport_pc 00:02: disabled
[   61.178624] intel_rng: FWH not detected
[   61.289789] Linux agpgart interface v0.102
[   61.575311] ieee80211_crypt: registered algorithm 'NULL'
[   61.795601] ieee80211: 802.11 data/management/control stack, git-1.1.13
[   61.795900] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
[   62.205585] Yenta: CardBus bridge found at 0000:02:06.0 [103c:30c4]
[   62.205612] Yenta: Using CSCINT to route CSC interrupts to PCI
[   62.205613] Yenta: Routing CardBus interrupts to PCI
[   62.205618] Yenta TI: socket 0000:02:06.0, mfunc 0x01be1b32, devctl 0x44
[   62.269550] agpgart: Detected an Intel 915GM Chipset.
[   62.270076] agpgart: Detected 7932K stolen memory.
[   62.287916] agpgart: AGP aperture is 256M @ 0xc0000000
[   62.455123] Yenta: ISA IRQ mask 0x0cf8, PCI irq 16
[   62.455128] Socket status: 30000006
[   62.455130] Yenta: Raising subordinate bus# of parent bus (#02) from #03 to #06
[   62.455136] pcmcia: parent PCI bridge I/O window: 0x2000 - 0x2fff
[   62.455228] cs: IO port probe 0x2000-0x2fff: clean.
[   62.501582] pcmcia: parent PCI bridge Memory window: 0xd0000000 - 0xd05fffff
[   62.551704] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.2.2kmprq
[   62.551708] ipw2200: Copyright(c) 2003-2006 Intel Corporation
[   62.637548] ACPI: AC Adapter [C15D] (on-line)
[   62.685394] input: Power Button (FF) as /devices/virtual/input/input3
[   62.717295] ACPI: Power Button (FF) [PWRF]
[   62.717361] input: Sleep Button (CM) as /devices/virtual/input/input4
[   62.745284] ACPI: Sleep Button (CM) [C1CE]
[   62.745320] input: Lid Switch as /devices/virtual/input/input5
[   62.777297] ACPI: Lid Switch [C1CF]
[   62.843575] ACPI: Battery Slot [C15E] (battery present)
[   62.945284] ACPI: WMI-Acer: Mapper loaded
[   63.073368] ACPI: PCI Interrupt 0000:02:04.0[A] -> GSI 21 (level, low) -> IRQ 21
[   63.190496] ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection
[   63.334203] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/LNXVIDEO:00/input/input6
[   63.360991] ACPI: Video Device [C054] (multi-head: yes  rom: no  post: no)
[   63.888251] Synaptics Touchpad, model: 1, fw: 6.3, id: 0x1a0b1, caps: 0xa04713/0x200000
[   63.951927] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input7
[   64.570340] usbcore: registered new interface driver hiddev
[   64.583378] input: Logitech Optical USB Mouse as /devices/pci0000:00/0000:00:1d.0/usb1/1-1/1-1:1.0/input/input8
[   64.600429] input,hidraw0: USB HID v1.10 Mouse [Logitech Optical USB Mouse] on usb-0000:00:1d.0-1
[   64.614377] input: CHESEN PS2 to USB Converter as /devices/pci0000:00/0000:00:1d.0/usb1/1-2/1-2:1.0/input/input9
[   64.632398] input,hidraw1: USB HID v1.10 Keyboard [CHESEN PS2 to USB Converter] on usb-0000:00:1d.0-2
[   64.657503] input: CHESEN PS2 to USB Converter as /devices/pci0000:00/0000:00:1d.0/usb1/1-2/1-2:1.1/input/input10
[   64.688389] input,hidraw2: USB HID v1.10 Mouse [CHESEN PS2 to USB Converter] on usb-0000:00:1d.0-2
[   64.688405] usbcore: registered new interface driver usbhid
[   64.688409] /build/buildd/linux-2.6.24/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
[   65.843101] ipw2200: Detected geography ZZR (14 802.11bg channels, 0 802.11a channels)
[   65.847815] ACPI: PCI Interrupt 0000:00:1e.2[B] -> GSI 17 (level, low) -> IRQ 17
[   65.847835] PCI: Setting latency timer of device 0000:00:1e.2 to 64
[   66.143609] intel8x0_measure_ac97_clock: measured 56702 usecs
[   66.143613] intel8x0: clocking to 48000
[   66.264565] cs: IO port probe 0x100-0x3af: clean.
[   66.266224] cs: IO port probe 0x3e0-0x4ff: clean.
[   66.266930] cs: IO port probe 0x820-0x8ff: clean.
[   66.267509] cs: IO port probe 0xc00-0xcf7: clean.
[   66.268222] cs: IO port probe 0xa00-0xaff: clean.
[   66.373573] lp: driver loaded but no devices found
[   66.426065] Adding 317512k swap on /dev/hda3.  Priority:-1 extents:1 across:317512k
[   67.413865] NET: Registered protocol family 17
[   67.419151] EXT3 FS on hda5, internal journal
[   68.162121] ip_tables: (C) 2000-2006 Netfilter Core Team
[   68.614252] No dock devices found.
[   70.761110] apm: BIOS not found.
[   70.842022] ppdev: user-space parallel port driver
[   71.252502] audit(1219827892.824:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=4827 profile="/usr/sbin/cupsd" namespace="default"
[  191.431650] Marking TSC unstable due to: cpufreq changes.
[  192.625088] NET: Registered protocol family 10
[  192.625786] lo: Disabled Privacy Extensions
[   72.879043] ADDRCONF(NETDEV_UP): eth0: link is not ready
[  195.169622] Bluetooth: Core ver 2.11
[  195.170398] NET: Registered protocol family 31
[  195.170405] Bluetooth: HCI device and connection manager initialized
[  195.170412] Bluetooth: HCI socket layer initialized
[  195.412305] Bluetooth: L2CAP ver 2.9
[  195.412313] Bluetooth: L2CAP socket layer initialized
[  195.608502] Bluetooth: RFCOMM socket layer initialized
[  195.608525] Bluetooth: RFCOMM TTY layer initialized
[  195.608529] Bluetooth: RFCOMM ver 1.8
[  200.855630] [drm] Initialized drm 1.1.0 20060810
[  200.885636] ACPI: PCI Interrupt 0000:00:02.0[A] -> GSI 16 (level, low) -> IRQ 20
[  200.885649] PCI: Setting latency timer of device 0000:00:02.0 to 64
[  200.885757] [drm] Initialized i915 1.6.0 20060119 on minor 0
[  203.292224] eth1: no IPv6 routers present
[  122.001135] tun: Universal TUN/TAP device driver, 1.6
[  122.001139] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[  122.001922] tun0: Disabled Privacy Extensions
[  406.319958] ipw2200: Firmware error detected.  Restarting.
[  415.978076] ipw2200: Firmware error detected.  Restarting.
[  418.980276] ipw2200: Firmware error detected.  Restarting.
[  427.283757] ipw2200: Firmware error detected.  Restarting.




> 
00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d3)
00:1e.2 Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 03)
00:1e.3 Modem: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Modem Controller (rev 03)
00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 03)
02:04.0 Network controller: Intel Corporation PRO/Wireless 2200BG Network Connection (rev 05)
02:06.0 CardBus bridge: ENE Technology Inc CB1410 Cardbus Controller (rev 01)
02:08.0 Ethernet controller: Intel Corporation PRO/100 VE Network Connection (rev 03)


---

