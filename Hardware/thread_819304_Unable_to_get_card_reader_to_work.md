---
title: "Unable to get card reader to work"
date: 2008-06-05
forum: Hardware
---

### Post by thorombolo1 on 2008-06-05
I have an external generic All in 1 USB card reader/writer that works fine under windows XP but in Ubuntu Hardy the light on the reader flashes and I can get it to work. No reading of any card. Please help :confused:

My lsusb reads:
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 003: ID 09ef:0101 Xitel MD-Port DG2 MiniDisc Interface ([COLOR="Red"]NOT card reader it is MP3 optic Driver[/COLOR])
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 005: ID 0458:2011 KYE Systems Corp. (Mouse Systems) ColorPage-Vivid3x Scanner
Bus 001 Device 001: ID 0000:0000

My dmesg without card:
[    0.000000]   HighMem zone: 32052 pages, LIFO batch:7
[    0.000000]   Movable zone: 0 pages used for memmap
[    0.000000] DMI 2.3 present.
[    0.000000] ACPI: RSDP signature @ 0xC00F62C0 checksum 0
[    0.000000] ACPI: RSDP 000F62C0, 0014 (r0 ACPIAM)
[    0.000000] ACPI: RSDT 3FF30000, 0034 (r1 INTEL  D865PERL 20050213 MSFT       97)
[    0.000000] ACPI: FACP 3FF30200, 0081 (r2 INTEL  D865PERL 20050213 MSFT       97)
[    0.000000] ACPI: DSDT 3FF30370, 4272 (r1 INTEL  D865PERL        6 MSFT  100000D)
[    0.000000] ACPI: FACS 3FF40000, 0040
[    0.000000] ACPI: APIC 3FF30300, 0068 (r1 INTEL  D865PERL 20050213 MSFT       97)
[    0.000000] ACPI: ASF! 3FF345F0, 0099 (r16 LEGEND I865PASF        1 MSFT  100000D)
[    0.000000] ACPI: WDDT 3FF34689, 0040 (r1 INTEL  OEMWDDT         1 MSFT  100000D)
[    0.000000] ACPI: PM-Timer IO Port: 0x408
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] Processor #0 15:3 APIC version 20
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
[    0.000000] Processor #1 15:3 APIC version 20
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] dfl dfl lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x02] dfl dfl lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] Allocating PCI resources starting at 50000000 (gap: 40000000:becf0000)
[    0.000000] swsusp: Registered nosave memory region: 000000000009f000 - 00000000000a0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000a0000 - 00000000000e6000
[    0.000000] swsusp: Registered nosave memory region: 00000000000e6000 - 0000000000100000
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 259636
[    0.000000] Kernel command line: root=UUID=fb4bb8c9-c9d6-4c65-ba06-46bac7401020 ro quiet splash
[    0.000000] mapped APIC to ffffb000 (fee00000)
[    0.000000] mapped IOAPIC to ffffa000 (fec00000)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] Detected 2793.143 MHz processor.
[   15.797012] Console: colour VGA+ 80x25
[   15.797016] console [tty0] enabled
[   15.797424] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[   15.797829] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[   15.826551] Memory: 1025568k/1046720k available (2176k kernel code, 20420k reserved, 1006k data, 368k init, 129216k highmem)
[   15.826560] virtual kernel memory layout:
[   15.826561]     fixmap  : 0xfff4b000 - 0xfffff000   ( 720 kB)
[   15.826563]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   15.826564]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
[   15.826565]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
[   15.826566]       .init : 0xc0421000 - 0xc047d000   ( 368 kB)
[   15.826567]       .data : 0xc03201f4 - 0xc041bdc4   (1006 kB)
[   15.826568]       .text : 0xc0100000 - 0xc03201f4   (2176 kB)
[   15.826572] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   15.826618] SLUB: Genslabs=11, HWalign=64, Order=0-1, MinObjects=4, CPUs=2, Nodes=1
[   15.906508] Calibrating delay using timer specific routine.. 5590.87 BogoMIPS (lpj=11181741)
[   15.906539] Security Framework initialized
[   15.906546] SELinux:  Disabled at boot.
[   15.906562] AppArmor: AppArmor initialized
[   15.906567] Failure registering capabilities with primary security module.
[   15.906576] Mount-cache hash table entries: 512
[   15.906726] Initializing cgroup subsys ns
[   15.906731] Initializing cgroup subsys cpuacct
[   15.906745] CPU: After generic identify, caps: bfebfbff 00000000 00000000 00000000 0000041d 00000000 00000000 00000000
[   15.906755] monitor/mwait feature present.
[   15.906757] using mwait in idle threads.
[   15.906764] CPU: Trace cache: 12K uops, L1 D cache: 16K
[   15.906767] CPU: L2 cache: 1024K
[   15.906770] CPU: Physical Processor ID: 0
[   15.906773] CPU: After all inits, caps: bfebfbff 00000000 00000000 0000b180 0000041d 00000000 00000000 00000000
[   15.906785] Compat vDSO mapped to ffffe000.
[   15.906803] Checking 'hlt' instruction... OK.
[   15.922947] SMP alternatives: switching to UP code
[   15.924919] Early unpacking initramfs... done
[   16.238436] ACPI: Core revision 20070126
[   16.238490] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[   16.240744] CPU0: Intel(R) Pentium(R) 4 CPU 2.80GHz stepping 03
[   16.240765] SMP alternatives: switching to SMP code
[   16.241570] Booting processor 1/1 eip 3000
[   16.251693] Initializing CPU#1
[   16.329800] Calibrating delay using timer specific routine.. 5586.41 BogoMIPS (lpj=11172828)
[   16.329812] CPU: After generic identify, caps: bfebfbff 00000000 00000000 00000000 0000041d 00000000 00000000 00000000
[   16.329820] monitor/mwait feature present.
[   16.329827] CPU: Trace cache: 12K uops, L1 D cache: 16K
[   16.329830] CPU: L2 cache: 1024K
[   16.329832] CPU: Physical Processor ID: 0
[   16.329835] CPU: After all inits, caps: bfebfbff 00000000 00000000 0000b180 0000041d 00000000 00000000 00000000
[   16.330225] CPU1: Intel(R) Pentium(R) 4 CPU 2.80GHz stepping 03
[   16.330271] Total of 2 processors activated (11177.28 BogoMIPS).
[   16.330399] ENABLING IO-APIC IRQs
[   16.330573] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[   16.477710] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
[   16.497695] Brought up 2 CPUs
[   16.497722] CPU0 attaching sched-domain:
[   16.497726]  domain 0: span 03
[   16.497728]   groups: 01 02
[   16.497733]   domain 1: span 03
[   16.497735]    groups: 03
[   16.497738] CPU1 attaching sched-domain:
[   16.497740]  domain 0: span 03
[   16.497742]   groups: 02 01
[   16.497746]   domain 1: span 03
[   16.497748]    groups: 03
[   16.498050] net_namespace: 64 bytes
[   16.498064] Booting paravirtualized kernel on bare hardware
[   16.498726] Time:  8:55:56  Date: 06/05/08
[   16.498752] NET: Registered protocol family 16
[   16.499046] EISA bus registered
[   16.499053] ACPI: bus type pci registered
[   16.500382] PCI: PCI BIOS revision 3.00 entry at 0xf0031, last bus=2
[   16.500385] PCI: Using configuration type 1
[   16.500387] Setting up standard PCI resources
[   16.511956] ACPI: EC: Look up EC in DSDT
[   16.515851] ACPI: Interpreter enabled
[   16.515855] ACPI: (supports S0 S1 S4 S5)
[   16.515873] ACPI: Using IOAPIC for interrupt routing
[   16.522853] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   16.523377] Force enabled HPET at base address 0xfed00000
[   16.523384] PCI quirk: region 0400-047f claimed by ICH4 ACPI/GPIO/TCO
[   16.523389] PCI quirk: region 0500-053f claimed by ICH4 GPIO
[   16.523929] PCI: Transparent bridge - 0000:00:1e.0
[   16.523956] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   16.524070] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P1._PRT]
[   16.524150] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P3._PRT]
[   16.526561] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
[   16.526736] ACPI: PCI Interrupt Link [LNKB] (IRQs *3 4 5 6 7 9 10 11 12 14 15)
[   16.526908] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 9 *10 11 12 14 15)
[   16.527078] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 *5 6 7 9 10 11 12 14 15)
[   16.527248] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[   16.527420] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[   16.527594] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[   16.527766] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 *9 10 11 12 14 15)
[   16.527939] ACPI: Power Resource [URP1] (off)
[   16.527977] ACPI: Power Resource [FDDP] (off)
[   16.528014] ACPI: Power Resource [LPTP] (off)
[   16.528087] Linux Plug and Play Support v0.97 (c) Adam Belay
[   16.528136] pnp: PnP ACPI init
[   16.528145] ACPI: bus type pnp registered
[   16.532051] pnp: PnP ACPI: found 14 devices
[   16.532054] ACPI: ACPI bus type pnp unregistered
[   16.532059] PnPBIOS: Disabled by ACPI PNP
[   16.532403] PCI: Using ACPI for IRQ routing
[   16.532407] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   16.553454] NET: Registered protocol family 8
[   16.553457] NET: Registered protocol family 20
[   16.553583] hpet clockevent registered
[   16.553589] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[   16.553597] hpet0: 3 64-bit timers, 14318180 Hz
[   16.554642] AppArmor: AppArmor Filesystem Enabled
[   16.557436] Time: tsc clocksource has been installed.
[   16.569481] system 00:0a: ioport range 0x4d0-0x4d1 has been reserved
[   16.569490] system 00:0c: ioport range 0x400-0x47f has been reserved
[   16.569493] system 00:0c: ioport range 0x680-0x6ff has been reserved
[   16.569496] system 00:0c: ioport range 0x500-0x53f has been reserved
[   16.569499] system 00:0c: iomem range 0xfec00000-0xfec00fff has been reserved
[   16.569502] system 00:0c: iomem range 0xfee00000-0xfee00fff has been reserved
[   16.569506] system 00:0c: iomem range 0xfed20000-0xfed9ffff could not be reserved
[   16.569513] system 00:0d: iomem range 0x0-0x9ffff could not be reserved
[   16.569516] system 00:0d: iomem range 0xc0000-0xd7fff could not be reserved
[   16.569519] system 00:0d: iomem range 0xe0000-0xfffff could not be reserved
[   16.569522] system 00:0d: iomem range 0x100000-0x3fffffff could not be reserved
[   16.569525] system 00:0d: iomem range 0x0-0x0 could not be reserved
[   16.600077] PCI: Bridge: 0000:00:01.0
[   16.600082]   IO window: a000-afff
[   16.600087]   MEM window: ff800000-ff8fffff
[   16.600091]   PREFETCH window: e0000000-efffffff
[   16.600098] PCI: Bridge: 0000:00:1e.0
[   16.600101]   IO window: b000-bfff
[   16.600107]   MEM window: ff900000-ff9fffff
[   16.600111]   PREFETCH window: disabled.
[   16.600129] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[   16.600142] NET: Registered protocol family 2
[   16.637384] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[   16.637723] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[   16.638347] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[   16.638752] TCP: Hash tables configured (established 131072 bind 65536)
[   16.638755] TCP reno registered
[   16.649490] checking if image is initramfs... it is
[   17.052764] Switched to high resolution mode on CPU 1
[   17.056601] Switched to high resolution mode on CPU 0
[   17.269352] Freeing initrd memory: 7250k freed
[   17.270387] audit: initializing netlink socket (disabled)
[   17.270407] audit(1212656156.324:1): initialized
[   17.270640] highmem bounce pool size: 64 pages
[   17.273351] VFS: Disk quotas dquot_6.5.1
[   17.273458] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   17.273629] io scheduler noop registered
[   17.273632] io scheduler anticipatory registered
[   17.273634] io scheduler deadline registered
[   17.273647] io scheduler cfq registered (default)
[   25.258388] 0000:00:1d.7 EHCI: BIOS handoff failed (BIOS bug ?) 01010001
[   25.258516] Boot video device is 0000:01:00.0
[   25.258914] isapnp: Scanning for PnP cards...
[   25.612027] isapnp: No Plug & Play device found
[   25.652820] Real Time Clock Driver v1.12ac
[   25.652954] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   25.653079] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   25.654042] 00:08: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   25.655187] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   25.655280] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[   25.655431] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f03:PS2M] at 0x60,0x64 irq 1,12
[   25.659684] serio: i8042 KBD port at 0x60,0x64 irq 1
[   25.659691] serio: i8042 AUX port at 0x60,0x64 irq 12
[   25.681759] mice: PS/2 mouse device common for all mice
[   25.681946] EISA: Probing bus 0 at eisa.0
[   25.681987] EISA: Detected 0 cards.
[   25.681990] cpuidle: using governor ladder
[   25.681992] cpuidle: using governor menu
[   25.682080] NET: Registered protocol family 1
[   25.682114] Using IPI No-Shortcut mode
[   25.682148] registered taskstats version 1
[   25.682252]   Magic number: 12:112:927
[   25.682309]   hash matches device ptyxc
[   25.682359] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[   25.682361] EDD information not available.
[   25.682589] Freeing unused kernel memory: 368k freed
[   25.705042] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[   26.963326] fuse init (API version 7.9)
[   26.992763] ACPI: Processor [CPU1] (supports 8 throttling states)
[   26.992804] ACPI: Processor [CPU2] (supports 8 throttling states)
[   27.223120] usbcore: registered new interface driver usbfs
[   27.223157] usbcore: registered new interface driver hub
[   27.231051] usbcore: registered new device driver usb
[   27.240183] USB Universal Host Controller Interface driver v3.0
[   27.240264] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 16 (level, low) -> IRQ 16
[   27.240283] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[   27.240289] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[   27.240580] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[   27.240617] uhci_hcd 0000:00:1d.0: irq 16, io base 0x0000cc00
[   27.240834] usb usb1: configuration #1 chosen from 1 choice
[   27.240885] hub 1-0:1.0: USB hub found
[   27.240897] hub 1-0:1.0: 2 ports detected
[   27.308181] SCSI subsystem initialized
[   27.346929] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 19 (level, low) -> IRQ 17
[   27.346947] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[   27.346953] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[   27.346991] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[   27.347021] uhci_hcd 0000:00:1d.1: irq 17, io base 0x0000d000
[   27.347205] usb usb2: configuration #1 chosen from 1 choice
[   27.347247] hub 2-0:1.0: USB hub found
[   27.347257] hub 2-0:1.0: 2 ports detected
[   27.375544] libata version 3.00 loaded.
[   27.450774] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 18
[   27.450791] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[   27.450797] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[   27.450840] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
[   27.450872] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000d400
[   27.451058] usb usb3: configuration #1 chosen from 1 choice
[   27.451104] hub 3-0:1.0: USB hub found
[   27.451113] hub 3-0:1.0: 2 ports detected
[   27.554568] ACPI: PCI Interrupt 0000:00:1d.3[A] -> GSI 16 (level, low) -> IRQ 16
[   27.554586] PCI: Setting latency timer of device 0000:00:1d.3 to 64
[   27.554592] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[   27.554641] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 4
[   27.554669] uhci_hcd 0000:00:1d.3: irq 16, io base 0x0000d800
[   27.554853] usb usb4: configuration #1 chosen from 1 choice
[   27.554898] hub 4-0:1.0: USB hub found
[   27.554909] hub 4-0:1.0: 2 ports detected
[   27.586395] usb 1-1: new full speed USB device using uhci_hcd and address 2
[   27.658567] ACPI: PCI Interrupt 0000:00:1d.7[D] -> GSI 23 (level, low) -> IRQ 19
[   27.658586] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[   27.658592] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[   27.658633] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 5
[   27.662543] ehci_hcd 0000:00:1d.7: debug port 1
[   27.662552] PCI: cache line size of 128 is not supported by device 0000:00:1d.7
[   27.662566] ehci_hcd 0000:00:1d.7: irq 19, io mem 0xffa00000
[   27.714151] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   27.714354] usb usb5: configuration #1 chosen from 1 choice
[   27.714400] hub 5-0:1.0: USB hub found
[   27.714412] hub 5-0:1.0: 8 ports detected
[   27.818189] ACPI: PCI Interrupt 0000:02:04.0[A] -> GSI 18 (level, low) -> IRQ 18
[   27.818202] 3c59x: Donald Becker and others.
[   27.818209] 0000:02:04.0: 3Com PCI 3c905B Cyclone 100baseTx at f8860800.
[   27.848250] PCI: Enabling device 0000:00:1f.1 (0005 -> 0007)
[   27.848261] ACPI: PCI Interrupt 0000:00:1f.1[A] -> GSI 18 (level, low) -> IRQ 18
[   27.848311] PCI: Setting latency timer of device 0000:00:1f.1 to 64
[   27.848327] ACPI: PCI interrupt for device 0000:00:1f.1 disabled
[   27.848347] ACPI: PCI Interrupt 0000:00:1f.2[A] -> GSI 18 (level, low) -> IRQ 18
[   27.848381] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[   27.848395] ACPI: PCI interrupt for device 0000:00:1f.2 disabled
[   27.855543] ata_piix 0000:00:1f.1: version 2.12
[   27.855565] ACPI: PCI Interrupt 0000:00:1f.1[A] -> GSI 18 (level, low) -> IRQ 18
[   27.855621] PCI: Setting latency timer of device 0000:00:1f.1 to 64
[   27.863627] scsi0 : ata_piix
[   27.865348] Floppy drive(s): fd0 is 1.44M
[   27.870692] scsi1 : ata_piix
[   27.872674] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xffa0 irq 14
[   27.872679] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xffa8 irq 15
[   27.882772] FDC 0 is a National Semiconductor PC87306
[   28.046006] ata1.00: ATA-5: ST360021A, 3.19, max UDMA/100
[   28.046011] ata1.00: 117231408 sectors, multi 16: LBA 
[   28.046217] ata1.01: ATA-7: Maxtor 6Y120L0, YAR41BW0, max UDMA/133
[   28.046220] ata1.01: 240121728 sectors, multi 16: LBA 
[   28.062014] ata1.00: configured for UDMA/100
[   28.077959] ata1.01: configured for UDMA/100
[   28.117453] usb 1-1: device not accepting address 2, error -71
[   28.394267] ata2.00: ATAPI: LITE-ON DVDRW LDW-411S, FS0K, max UDMA/33
[   28.566021] ata2.00: configured for UDMA/33
[   28.566188] scsi 0:0:0:0: Direct-Access     ATA      ST360021A        3.19 PQ: 0 ANSI: 5
[   28.566380] scsi 0:0:1:0: Direct-Access     ATA      Maxtor 6Y120L0   YAR4 PQ: 0 ANSI: 5
[   28.567328] scsi 1:0:0:0: CD-ROM            LITE-ON  DVDRW LDW-411S   FS0K PQ: 0 ANSI: 5
[   28.567464] ata_piix 0000:00:1f.2: MAP [ P0 -- P1 -- ]
[   28.567494] ACPI: PCI Interrupt 0000:00:1f.2[A] -> GSI 18 (level, low) -> IRQ 18
[   28.567551] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[   28.569635] scsi2 : ata_piix
[   28.570912] scsi3 : ata_piix
[   28.572077] ata3: SATA max UDMA/133 cmd 0xec00 ctl 0xe800 bmdma 0xdc00 irq 18
[   28.572083] ata4: SATA max UDMA/133 cmd 0xe400 ctl 0xe000 bmdma 0xdc08 irq 18
[   28.899905] ACPI: PCI Interrupt 0000:02:02.0[A] -> GSI 17 (level, low) -> IRQ 20
[   28.952623] ohci1394: fw-host0: OHCI-1394 1.0 (PCI): IRQ=[20]  MMIO=[ff920000-ff9207ff]  Max Packet=[2048]  IR/IT contexts=[8/8]
[   28.959689] Driver 'sd' needs updating - please use bus_type methods
[   28.959844] sd 0:0:0:0: [sda] 117231408 512-byte hardware sectors (60022 MB)
[   28.959875] sd 0:0:0:0: [sda] Write Protect is off
[   28.959883] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   28.959930] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   28.960059] sd 0:0:0:0: [sda] 117231408 512-byte hardware sectors (60022 MB)
[   28.960086] sd 0:0:0:0: [sda] Write Protect is off
[   28.960092] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   28.960138] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   28.960146]  sda:<4>Driver 'sr' needs updating - please use bus_type methods
[   28.977968]  sda1 sda2 sda3
[   28.996680] sd 0:0:0:0: [sda] Attached SCSI disk
[   28.996785] sd 0:0:1:0: [sdb] 240121728 512-byte hardware sectors (122942 MB)
[   28.996808] sd 0:0:1:0: [sdb] Write Protect is off
[   28.996813] sd 0:0:1:0: [sdb] Mode Sense: 00 3a 00 00
[   28.996851] sd 0:0:1:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   28.996936] sd 0:0:1:0: [sdb] 240121728 512-byte hardware sectors (122942 MB)
[   28.996958] sd 0:0:1:0: [sdb] Write Protect is off
[   28.996963] sd 0:0:1:0: [sdb] Mode Sense: 00 3a 00 00
[   28.997004] sd 0:0:1:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   28.997011]  sdb: sdb1
[   29.005949] sd 0:0:1:0: [sdb] Attached SCSI disk
[   29.014511] sd 0:0:0:0: Attached scsi generic sg0 type 0
[   29.014551] sd 0:0:1:0: Attached scsi generic sg1 type 0
[   29.014586] sr 1:0:0:0: Attached scsi generic sg2 type 5
[   29.016924] usb 1-1: new full speed USB device using uhci_hcd and address 4
[   29.017069] sr0: scsi3-mmc drive: 40x/40x writer cd/rw xa/form2 cdda tray
[   29.017075] Uniform CD-ROM driver Revision: 3.20
[   29.017161] sr 1:0:0:0: Attached scsi CD-ROM sr0
[   29.173166] usb 1-1: configuration #1 chosen from 1 choice
[   29.415229] usb 2-1: new full speed USB device using uhci_hcd and address 2
[   29.470101] Attempting manual resume
[   29.470106] swsusp: Resume From Partition 8:3
[   29.470108] PM: Checking swsusp image.
[   29.470372] PM: Resume from disk failed.
[   29.648833] usb 2-1: configuration #1 chosen from 1 choice
[   30.230004] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[00110600b91b067f]
[   40.349501] input: PC Speaker as /devices/platform/pcspkr/input/input2
[   40.857795] iTCO_vendor_support: vendor-support=0
[   40.880457] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.02 (26-Jul-2007)
[   40.880647] iTCO_wdt: Found a ICH5 or ICH5R TCO device (Version=1, TCOBASE=0x0460)
[   40.880715] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   40.956348] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   41.004326] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   41.092086] Linux agpgart interface v0.102
[   41.124088] agpgart: Detected an Intel 865 Chipset.
[   41.127585] agpgart: AGP aperture is 64M @ 0xf0000000
[   41.355689] intel_rng: Firmware space is locked read-only. If you can't or
[   41.355693] intel_rng: don't want to disable this in firmware setup, and if
[   41.355696] intel_rng: you are certain that your system has a functional
[   41.355698] intel_rng: RNG, try using the 'no_fwh_detect' option.
[   42.027655] input: Power Button (FF) as /devices/virtual/input/input3
[   42.077434] ACPI: Power Button (FF) [PWRF]
[   42.077591] input: Sleep Button (CM) as /devices/virtual/input/input4
[   42.113349] ACPI: Sleep Button (CM) [SLPB]
[   42.847046] input: PS2++ Logitech Mouse as /devices/platform/i8042/serio1/input/input5
[   43.151607] ACPI: PCI Interrupt 0000:00:1f.5[B] -> GSI 17 (level, low) -> IRQ 20
[   43.151643] PCI: Setting latency timer of device 0000:00:1f.5 to 64
[   43.577219] intel8x0_measure_ac97_clock: measured 58417 usecs
[   43.577228] intel8x0: clocking to 48000
[   43.663948] usbcore: registered new interface driver hiddev
[   43.664069] usbcore: registered new interface driver snd-usb-audio
[   43.678334] input: XITEL MD-PORT DG2 as /devices/pci0000:00/0000:00:1d.1/usb2/2-1/2-1:1.2/input/input6
[   43.706604] input,hidraw0: USB HID v1.00 Device [XITEL MD-PORT DG2] on usb-0000:00:1d.1-1
[   43.706626] usbcore: registered new interface driver usbhid
[   43.706632] /build/buildd/linux-2.6.24/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
[   45.026882] lp: driver loaded but no devices found
[   45.122044] Adding 2104504k swap on /dev/sda3.  Priority:-1 extents:1 across:2104504k
[   46.885740] ip_tables: (C) 2000-2006 Netfilter Core Team
[   47.365290] No dock devices found.
[   48.797372] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[   48.797381] apm: disabled - APM is not SMP safe.
[   48.953566] ppdev: user-space parallel port driver
[   49.126865] audit(1212674188.227:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=4981 profile="/usr/sbin/cupsd" namespace="default"
[   50.202281] eth0:  setting full-duplex.
[   50.296439] Bluetooth: Core ver 2.11
[   50.296943] NET: Registered protocol family 31
[   50.296950] Bluetooth: HCI device and connection manager initialized
[   50.296958] Bluetooth: HCI socket layer initialized
[   50.331488] Bluetooth: L2CAP ver 2.9
[   50.331496] Bluetooth: L2CAP socket layer initialized
[   50.377329] Bluetooth: RFCOMM socket layer initialized
[   50.377347] Bluetooth: RFCOMM TTY layer initialized
[   50.377351] Bluetooth: RFCOMM ver 1.8
[   52.162357] [drm] Initialized drm 1.1.0 20060810
[   52.179148] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 16
[   52.179684] [drm] Initialized radeon 1.28.0 20060524 on minor 0
[   52.766207] agpgart: Found an AGP 3.0 compliant device at 0000:00:00.0.
[   52.766232] agpgart: Device is in legacy mode, falling back to 2.x
[   52.766243] agpgart: Putting AGP V2 device at 0000:00:00.0 into 4x mode
[   52.766283] agpgart: Putting AGP V2 device at 0000:01:00.0 into 4x mode
[   53.052090] [drm] Setting GART location based on new memory map
[   53.052104] [drm] Loading R200 Microcode
[   53.052151] [drm] writeback test succeeded in 1 usecs
[   54.389566] NET: Registered protocol family 17
[   59.130227] agpgart: Found an AGP 3.0 compliant device at 0000:00:00.0.
[   59.130563] agpgart: Device is in legacy mode, falling back to 2.x
[   59.130791] agpgart: Putting AGP V2 device at 0000:00:00.0 into 4x mode
[   59.131043] agpgart: Putting AGP V2 device at 0000:01:00.0 into 4x mode
[   59.295092] NET: Registered protocol family 10
[   59.295664] lo: Disabled Privacy Extensions
[   59.384937] [drm] Setting GART location based on new memory map
[   59.384949] [drm] Loading R200 Microcode
[   59.384993] [drm] writeback test succeeded in 1 usecs
[   65.436642] agpgart: Found an AGP 3.0 compliant device at 0000:00:00.0.
[   65.436667] agpgart: Device is in legacy mode, falling back to 2.x
[   65.436678] agpgart: Putting AGP V2 device at 0000:00:00.0 into 4x mode
[   65.436722] agpgart: Putting AGP V2 device at 0000:01:00.0 into 4x mode
[   65.689476] [drm] Setting GART location based on new memory map
[   65.689489] [drm] Loading R200 Microcode
[   65.689534] [drm] writeback test succeeded in 1 usecs
[   70.136774] eth0: no IPv6 routers present

My dmesg with card:
[   15.797016] console [tty0] enabled
[   15.797424] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[   15.797829] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[   15.826551] Memory: 1025568k/1046720k available (2176k kernel code, 20420k reserved, 1006k data, 368k init, 129216k highmem)
[   15.826560] virtual kernel memory layout:
[   15.826561]     fixmap  : 0xfff4b000 - 0xfffff000   ( 720 kB)
[   15.826563]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   15.826564]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
[   15.826565]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
[   15.826566]       .init : 0xc0421000 - 0xc047d000   ( 368 kB)
[   15.826567]       .data : 0xc03201f4 - 0xc041bdc4   (1006 kB)
[   15.826568]       .text : 0xc0100000 - 0xc03201f4   (2176 kB)
[   15.826572] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   15.826618] SLUB: Genslabs=11, HWalign=64, Order=0-1, MinObjects=4, CPUs=2, Nodes=1
[   15.906508] Calibrating delay using timer specific routine.. 5590.87 BogoMIPS (lpj=11181741)
[   15.906539] Security Framework initialized
[   15.906546] SELinux:  Disabled at boot.
[   15.906562] AppArmor: AppArmor initialized
[   15.906567] Failure registering capabilities with primary security module.
[   15.906576] Mount-cache hash table entries: 512
[   15.906726] Initializing cgroup subsys ns
[   15.906731] Initializing cgroup subsys cpuacct
[   15.906745] CPU: After generic identify, caps: bfebfbff 00000000 00000000 00000000 0000041d 00000000 00000000 00000000
[   15.906755] monitor/mwait feature present.
[   15.906757] using mwait in idle threads.
[   15.906764] CPU: Trace cache: 12K uops, L1 D cache: 16K
[   15.906767] CPU: L2 cache: 1024K
[   15.906770] CPU: Physical Processor ID: 0
[   15.906773] CPU: After all inits, caps: bfebfbff 00000000 00000000 0000b180 0000041d 00000000 00000000 00000000
[   15.906785] Compat vDSO mapped to ffffe000.
[   15.906803] Checking 'hlt' instruction... OK.
[   15.922947] SMP alternatives: switching to UP code
[   15.924919] Early unpacking initramfs... done
[   16.238436] ACPI: Core revision 20070126
[   16.238490] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[   16.240744] CPU0: Intel(R) Pentium(R) 4 CPU 2.80GHz stepping 03
[   16.240765] SMP alternatives: switching to SMP code
[   16.241570] Booting processor 1/1 eip 3000
[   16.251693] Initializing CPU#1
[   16.329800] Calibrating delay using timer specific routine.. 5586.41 BogoMIPS (lpj=11172828)
[   16.329812] CPU: After generic identify, caps: bfebfbff 00000000 00000000 00000000 0000041d 00000000 00000000 00000000
[   16.329820] monitor/mwait feature present.
[   16.329827] CPU: Trace cache: 12K uops, L1 D cache: 16K
[   16.329830] CPU: L2 cache: 1024K
[   16.329832] CPU: Physical Processor ID: 0
[   16.329835] CPU: After all inits, caps: bfebfbff 00000000 00000000 0000b180 0000041d 00000000 00000000 00000000
[   16.330225] CPU1: Intel(R) Pentium(R) 4 CPU 2.80GHz stepping 03
[   16.330271] Total of 2 processors activated (11177.28 BogoMIPS).
[   16.330399] ENABLING IO-APIC IRQs
[   16.330573] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[   16.477710] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
[   16.497695] Brought up 2 CPUs
[   16.497722] CPU0 attaching sched-domain:
[   16.497726]  domain 0: span 03
[   16.497728]   groups: 01 02
[   16.497733]   domain 1: span 03
[   16.497735]    groups: 03
[   16.497738] CPU1 attaching sched-domain:
[   16.497740]  domain 0: span 03
[   16.497742]   groups: 02 01
[   16.497746]   domain 1: span 03
[   16.497748]    groups: 03
[   16.498050] net_namespace: 64 bytes
[   16.498064] Booting paravirtualized kernel on bare hardware
[   16.498726] Time:  8:55:56  Date: 06/05/08
[   16.498752] NET: Registered protocol family 16
[   16.499046] EISA bus registered
[   16.499053] ACPI: bus type pci registered
[   16.500382] PCI: PCI BIOS revision 3.00 entry at 0xf0031, last bus=2
[   16.500385] PCI: Using configuration type 1
[   16.500387] Setting up standard PCI resources
[   16.511956] ACPI: EC: Look up EC in DSDT
[   16.515851] ACPI: Interpreter enabled
[   16.515855] ACPI: (supports S0 S1 S4 S5)
[   16.515873] ACPI: Using IOAPIC for interrupt routing
[   16.522853] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   16.523377] Force enabled HPET at base address 0xfed00000
[   16.523384] PCI quirk: region 0400-047f claimed by ICH4 ACPI/GPIO/TCO
[   16.523389] PCI quirk: region 0500-053f claimed by ICH4 GPIO
[   16.523929] PCI: Transparent bridge - 0000:00:1e.0
[   16.523956] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   16.524070] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P1._PRT]
[   16.524150] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P3._PRT]
[   16.526561] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
[   16.526736] ACPI: PCI Interrupt Link [LNKB] (IRQs *3 4 5 6 7 9 10 11 12 14 15)
[   16.526908] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 9 *10 11 12 14 15)
[   16.527078] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 *5 6 7 9 10 11 12 14 15)
[   16.527248] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[   16.527420] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[   16.527594] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[   16.527766] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 *9 10 11 12 14 15)
[   16.527939] ACPI: Power Resource [URP1] (off)
[   16.527977] ACPI: Power Resource [FDDP] (off)
[   16.528014] ACPI: Power Resource [LPTP] (off)
[   16.528087] Linux Plug and Play Support v0.97 (c) Adam Belay
[   16.528136] pnp: PnP ACPI init
[   16.528145] ACPI: bus type pnp registered
[   16.532051] pnp: PnP ACPI: found 14 devices
[   16.532054] ACPI: ACPI bus type pnp unregistered
[   16.532059] PnPBIOS: Disabled by ACPI PNP
[   16.532403] PCI: Using ACPI for IRQ routing
[   16.532407] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   16.553454] NET: Registered protocol family 8
[   16.553457] NET: Registered protocol family 20
[   16.553583] hpet clockevent registered
[   16.553589] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[   16.553597] hpet0: 3 64-bit timers, 14318180 Hz
[   16.554642] AppArmor: AppArmor Filesystem Enabled
[   16.557436] Time: tsc clocksource has been installed.
[   16.569481] system 00:0a: ioport range 0x4d0-0x4d1 has been reserved
[   16.569490] system 00:0c: ioport range 0x400-0x47f has been reserved
[   16.569493] system 00:0c: ioport range 0x680-0x6ff has been reserved
[   16.569496] system 00:0c: ioport range 0x500-0x53f has been reserved
[   16.569499] system 00:0c: iomem range 0xfec00000-0xfec00fff has been reserved
[   16.569502] system 00:0c: iomem range 0xfee00000-0xfee00fff has been reserved
[   16.569506] system 00:0c: iomem range 0xfed20000-0xfed9ffff could not be reserved
[   16.569513] system 00:0d: iomem range 0x0-0x9ffff could not be reserved
[   16.569516] system 00:0d: iomem range 0xc0000-0xd7fff could not be reserved
[   16.569519] system 00:0d: iomem range 0xe0000-0xfffff could not be reserved
[   16.569522] system 00:0d: iomem range 0x100000-0x3fffffff could not be reserved
[   16.569525] system 00:0d: iomem range 0x0-0x0 could not be reserved
[   16.600077] PCI: Bridge: 0000:00:01.0
[   16.600082]   IO window: a000-afff
[   16.600087]   MEM window: ff800000-ff8fffff
[   16.600091]   PREFETCH window: e0000000-efffffff
[   16.600098] PCI: Bridge: 0000:00:1e.0
[   16.600101]   IO window: b000-bfff
[   16.600107]   MEM window: ff900000-ff9fffff
[   16.600111]   PREFETCH window: disabled.
[   16.600129] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[   16.600142] NET: Registered protocol family 2
[   16.637384] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[   16.637723] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[   16.638347] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[   16.638752] TCP: Hash tables configured (established 131072 bind 65536)
[   16.638755] TCP reno registered
[   16.649490] checking if image is initramfs... it is
[   17.052764] Switched to high resolution mode on CPU 1
[   17.056601] Switched to high resolution mode on CPU 0
[   17.269352] Freeing initrd memory: 7250k freed
[   17.270387] audit: initializing netlink socket (disabled)
[   17.270407] audit(1212656156.324:1): initialized
[   17.270640] highmem bounce pool size: 64 pages
[   17.273351] VFS: Disk quotas dquot_6.5.1
[   17.273458] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   17.273629] io scheduler noop registered
[   17.273632] io scheduler anticipatory registered
[   17.273634] io scheduler deadline registered
[   17.273647] io scheduler cfq registered (default)
[   25.258388] 0000:00:1d.7 EHCI: BIOS handoff failed (BIOS bug ?) 01010001
[   25.258516] Boot video device is 0000:01:00.0
[   25.258914] isapnp: Scanning for PnP cards...
[   25.612027] isapnp: No Plug & Play device found
[   25.652820] Real Time Clock Driver v1.12ac
[   25.652954] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   25.653079] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   25.654042] 00:08: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   25.655187] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   25.655280] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[   25.655431] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f03:PS2M] at 0x60,0x64 irq 1,12
[   25.659684] serio: i8042 KBD port at 0x60,0x64 irq 1
[   25.659691] serio: i8042 AUX port at 0x60,0x64 irq 12
[   25.681759] mice: PS/2 mouse device common for all mice
[   25.681946] EISA: Probing bus 0 at eisa.0
[   25.681987] EISA: Detected 0 cards.
[   25.681990] cpuidle: using governor ladder
[   25.681992] cpuidle: using governor menu
[   25.682080] NET: Registered protocol family 1
[   25.682114] Using IPI No-Shortcut mode
[   25.682148] registered taskstats version 1
[   25.682252]   Magic number: 12:112:927
[   25.682309]   hash matches device ptyxc
[   25.682359] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[   25.682361] EDD information not available.
[   25.682589] Freeing unused kernel memory: 368k freed
[   25.705042] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[   26.963326] fuse init (API version 7.9)
[   26.992763] ACPI: Processor [CPU1] (supports 8 throttling states)
[   26.992804] ACPI: Processor [CPU2] (supports 8 throttling states)
[   27.223120] usbcore: registered new interface driver usbfs
[   27.223157] usbcore: registered new interface driver hub
[   27.231051] usbcore: registered new device driver usb
[   27.240183] USB Universal Host Controller Interface driver v3.0
[   27.240264] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 16 (level, low) -> IRQ 16
[   27.240283] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[   27.240289] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[   27.240580] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[   27.240617] uhci_hcd 0000:00:1d.0: irq 16, io base 0x0000cc00
[   27.240834] usb usb1: configuration #1 chosen from 1 choice
[   27.240885] hub 1-0:1.0: USB hub found
[   27.240897] hub 1-0:1.0: 2 ports detected
[   27.308181] SCSI subsystem initialized
[   27.346929] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 19 (level, low) -> IRQ 17
[   27.346947] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[   27.346953] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[   27.346991] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[   27.347021] uhci_hcd 0000:00:1d.1: irq 17, io base 0x0000d000
[   27.347205] usb usb2: configuration #1 chosen from 1 choice
[   27.347247] hub 2-0:1.0: USB hub found
[   27.347257] hub 2-0:1.0: 2 ports detected
[   27.375544] libata version 3.00 loaded.
[   27.450774] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 18
[   27.450791] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[   27.450797] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[   27.450840] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
[   27.450872] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000d400
[   27.451058] usb usb3: configuration #1 chosen from 1 choice
[   27.451104] hub 3-0:1.0: USB hub found
[   27.451113] hub 3-0:1.0: 2 ports detected
[   27.554568] ACPI: PCI Interrupt 0000:00:1d.3[A] -> GSI 16 (level, low) -> IRQ 16
[   27.554586] PCI: Setting latency timer of device 0000:00:1d.3 to 64
[   27.554592] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[   27.554641] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 4
[   27.554669] uhci_hcd 0000:00:1d.3: irq 16, io base 0x0000d800
[   27.554853] usb usb4: configuration #1 chosen from 1 choice
[   27.554898] hub 4-0:1.0: USB hub found
[   27.554909] hub 4-0:1.0: 2 ports detected
[   27.586395] usb 1-1: new full speed USB device using uhci_hcd and address 2
[   27.658567] ACPI: PCI Interrupt 0000:00:1d.7[D] -> GSI 23 (level, low) -> IRQ 19
[   27.658586] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[   27.658592] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[   27.658633] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 5
[   27.662543] ehci_hcd 0000:00:1d.7: debug port 1
[   27.662552] PCI: cache line size of 128 is not supported by device 0000:00:1d.7
[   27.662566] ehci_hcd 0000:00:1d.7: irq 19, io mem 0xffa00000
[   27.714151] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   27.714354] usb usb5: configuration #1 chosen from 1 choice
[   27.714400] hub 5-0:1.0: USB hub found
[   27.714412] hub 5-0:1.0: 8 ports detected
[   27.818189] ACPI: PCI Interrupt 0000:02:04.0[A] -> GSI 18 (level, low) -> IRQ 18
[   27.818202] 3c59x: Donald Becker and others.
[   27.818209] 0000:02:04.0: 3Com PCI 3c905B Cyclone 100baseTx at f8860800.
[   27.848250] PCI: Enabling device 0000:00:1f.1 (0005 -> 0007)
[   27.848261] ACPI: PCI Interrupt 0000:00:1f.1[A] -> GSI 18 (level, low) -> IRQ 18
[   27.848311] PCI: Setting latency timer of device 0000:00:1f.1 to 64
[   27.848327] ACPI: PCI interrupt for device 0000:00:1f.1 disabled
[   27.848347] ACPI: PCI Interrupt 0000:00:1f.2[A] -> GSI 18 (level, low) -> IRQ 18
[   27.848381] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[   27.848395] ACPI: PCI interrupt for device 0000:00:1f.2 disabled
[   27.855543] ata_piix 0000:00:1f.1: version 2.12
[   27.855565] ACPI: PCI Interrupt 0000:00:1f.1[A] -> GSI 18 (level, low) -> IRQ 18
[   27.855621] PCI: Setting latency timer of device 0000:00:1f.1 to 64
[   27.863627] scsi0 : ata_piix
[   27.865348] Floppy drive(s): fd0 is 1.44M
[   27.870692] scsi1 : ata_piix
[   27.872674] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xffa0 irq 14
[   27.872679] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xffa8 irq 15
[   27.882772] FDC 0 is a National Semiconductor PC87306
[   28.046006] ata1.00: ATA-5: ST360021A, 3.19, max UDMA/100
[   28.046011] ata1.00: 117231408 sectors, multi 16: LBA 
[   28.046217] ata1.01: ATA-7: Maxtor 6Y120L0, YAR41BW0, max UDMA/133
[   28.046220] ata1.01: 240121728 sectors, multi 16: LBA 
[   28.062014] ata1.00: configured for UDMA/100
[   28.077959] ata1.01: configured for UDMA/100
[   28.117453] usb 1-1: device not accepting address 2, error -71
[   28.394267] ata2.00: ATAPI: LITE-ON DVDRW LDW-411S, FS0K, max UDMA/33
[   28.566021] ata2.00: configured for UDMA/33
[   28.566188] scsi 0:0:0:0: Direct-Access     ATA      ST360021A        3.19 PQ: 0 ANSI: 5
[   28.566380] scsi 0:0:1:0: Direct-Access     ATA      Maxtor 6Y120L0   YAR4 PQ: 0 ANSI: 5
[   28.567328] scsi 1:0:0:0: CD-ROM            LITE-ON  DVDRW LDW-411S   FS0K PQ: 0 ANSI: 5
[   28.567464] ata_piix 0000:00:1f.2: MAP [ P0 -- P1 -- ]
[   28.567494] ACPI: PCI Interrupt 0000:00:1f.2[A] -> GSI 18 (level, low) -> IRQ 18
[   28.567551] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[   28.569635] scsi2 : ata_piix
[   28.570912] scsi3 : ata_piix
[   28.572077] ata3: SATA max UDMA/133 cmd 0xec00 ctl 0xe800 bmdma 0xdc00 irq 18
[   28.572083] ata4: SATA max UDMA/133 cmd 0xe400 ctl 0xe000 bmdma 0xdc08 irq 18
[   28.899905] ACPI: PCI Interrupt 0000:02:02.0[A] -> GSI 17 (level, low) -> IRQ 20
[   28.952623] ohci1394: fw-host0: OHCI-1394 1.0 (PCI): IRQ=[20]  MMIO=[ff920000-ff9207ff]  Max Packet=[2048]  IR/IT contexts=[8/8]
[   28.959689] Driver 'sd' needs updating - please use bus_type methods
[   28.959844] sd 0:0:0:0: [sda] 117231408 512-byte hardware sectors (60022 MB)
[   28.959875] sd 0:0:0:0: [sda] Write Protect is off
[   28.959883] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   28.959930] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   28.960059] sd 0:0:0:0: [sda] 117231408 512-byte hardware sectors (60022 MB)
[   28.960086] sd 0:0:0:0: [sda] Write Protect is off
[   28.960092] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   28.960138] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   28.960146]  sda:<4>Driver 'sr' needs updating - please use bus_type methods
[   28.977968]  sda1 sda2 sda3
[   28.996680] sd 0:0:0:0: [sda] Attached SCSI disk
[   28.996785] sd 0:0:1:0: [sdb] 240121728 512-byte hardware sectors (122942 MB)
[   28.996808] sd 0:0:1:0: [sdb] Write Protect is off
[   28.996813] sd 0:0:1:0: [sdb] Mode Sense: 00 3a 00 00
[   28.996851] sd 0:0:1:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   28.996936] sd 0:0:1:0: [sdb] 240121728 512-byte hardware sectors (122942 MB)
[   28.996958] sd 0:0:1:0: [sdb] Write Protect is off
[   28.996963] sd 0:0:1:0: [sdb] Mode Sense: 00 3a 00 00
[   28.997004] sd 0:0:1:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   28.997011]  sdb: sdb1
[   29.005949] sd 0:0:1:0: [sdb] Attached SCSI disk
[   29.014511] sd 0:0:0:0: Attached scsi generic sg0 type 0
[   29.014551] sd 0:0:1:0: Attached scsi generic sg1 type 0
[   29.014586] sr 1:0:0:0: Attached scsi generic sg2 type 5
[   29.016924] usb 1-1: new full speed USB device using uhci_hcd and address 4
[   29.017069] sr0: scsi3-mmc drive: 40x/40x writer cd/rw xa/form2 cdda tray
[   29.017075] Uniform CD-ROM driver Revision: 3.20
[   29.017161] sr 1:0:0:0: Attached scsi CD-ROM sr0
[   29.173166] usb 1-1: configuration #1 chosen from 1 choice
[   29.415229] usb 2-1: new full speed USB device using uhci_hcd and address 2
[   29.470101] Attempting manual resume
[   29.470106] swsusp: Resume From Partition 8:3
[   29.470108] PM: Checking swsusp image.
[   29.470372] PM: Resume from disk failed.
[   29.648833] usb 2-1: configuration #1 chosen from 1 choice
[   30.230004] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[00110600b91b067f]
[   40.349501] input: PC Speaker as /devices/platform/pcspkr/input/input2
[   40.857795] iTCO_vendor_support: vendor-support=0
[   40.880457] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.02 (26-Jul-2007)
[   40.880647] iTCO_wdt: Found a ICH5 or ICH5R TCO device (Version=1, TCOBASE=0x0460)
[   40.880715] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   40.956348] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   41.004326] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   41.092086] Linux agpgart interface v0.102
[   41.124088] agpgart: Detected an Intel 865 Chipset.
[   41.127585] agpgart: AGP aperture is 64M @ 0xf0000000
[   41.355689] intel_rng: Firmware space is locked read-only. If you can't or
[   41.355693] intel_rng: don't want to disable this in firmware setup, and if
[   41.355696] intel_rng: you are certain that your system has a functional
[   41.355698] intel_rng: RNG, try using the 'no_fwh_detect' option.
[   42.027655] input: Power Button (FF) as /devices/virtual/input/input3
[   42.077434] ACPI: Power Button (FF) [PWRF]
[   42.077591] input: Sleep Button (CM) as /devices/virtual/input/input4
[   42.113349] ACPI: Sleep Button (CM) [SLPB]
[   42.847046] input: PS2++ Logitech Mouse as /devices/platform/i8042/serio1/input/input5
[   43.151607] ACPI: PCI Interrupt 0000:00:1f.5[B] -> GSI 17 (level, low) -> IRQ 20
[   43.151643] PCI: Setting latency timer of device 0000:00:1f.5 to 64
[   43.577219] intel8x0_measure_ac97_clock: measured 58417 usecs
[   43.577228] intel8x0: clocking to 48000
[   43.663948] usbcore: registered new interface driver hiddev
[   43.664069] usbcore: registered new interface driver snd-usb-audio
[   43.678334] input: XITEL MD-PORT DG2 as /devices/pci0000:00/0000:00:1d.1/usb2/2-1/2-1:1.2/input/input6
[   43.706604] input,hidraw0: USB HID v1.00 Device [XITEL MD-PORT DG2] on usb-0000:00:1d.1-1
[   43.706626] usbcore: registered new interface driver usbhid
[   43.706632] /build/buildd/linux-2.6.24/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
[   45.026882] lp: driver loaded but no devices found
[   45.122044] Adding 2104504k swap on /dev/sda3.  Priority:-1 extents:1 across:2104504k
[   46.885740] ip_tables: (C) 2000-2006 Netfilter Core Team
[   47.365290] No dock devices found.
[   48.797372] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[   48.797381] apm: disabled - APM is not SMP safe.
[   48.953566] ppdev: user-space parallel port driver
[   49.126865] audit(1212674188.227:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=4981 profile="/usr/sbin/cupsd" namespace="default"
[   50.202281] eth0:  setting full-duplex.
[   50.296439] Bluetooth: Core ver 2.11
[   50.296943] NET: Registered protocol family 31
[   50.296950] Bluetooth: HCI device and connection manager initialized
[   50.296958] Bluetooth: HCI socket layer initialized
[   50.331488] Bluetooth: L2CAP ver 2.9
[   50.331496] Bluetooth: L2CAP socket layer initialized
[   50.377329] Bluetooth: RFCOMM socket layer initialized
[   50.377347] Bluetooth: RFCOMM TTY layer initialized
[   50.377351] Bluetooth: RFCOMM ver 1.8
[   52.162357] [drm] Initialized drm 1.1.0 20060810
[   52.179148] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 16
[   52.179684] [drm] Initialized radeon 1.28.0 20060524 on minor 0
[   52.766207] agpgart: Found an AGP 3.0 compliant device at 0000:00:00.0.
[   52.766232] agpgart: Device is in legacy mode, falling back to 2.x
[   52.766243] agpgart: Putting AGP V2 device at 0000:00:00.0 into 4x mode
[   52.766283] agpgart: Putting AGP V2 device at 0000:01:00.0 into 4x mode
[   53.052090] [drm] Setting GART location based on new memory map
[   53.052104] [drm] Loading R200 Microcode
[   53.052151] [drm] writeback test succeeded in 1 usecs
[   54.389566] NET: Registered protocol family 17
[   59.130227] agpgart: Found an AGP 3.0 compliant device at 0000:00:00.0.
[   59.130563] agpgart: Device is in legacy mode, falling back to 2.x
[   59.130791] agpgart: Putting AGP V2 device at 0000:00:00.0 into 4x mode
[   59.131043] agpgart: Putting AGP V2 device at 0000:01:00.0 into 4x mode
[   59.295092] NET: Registered protocol family 10
[   59.295664] lo: Disabled Privacy Extensions
[   59.384937] [drm] Setting GART location based on new memory map
[   59.384949] [drm] Loading R200 Microcode
[   59.384993] [drm] writeback test succeeded in 1 usecs
[   65.436642] agpgart: Found an AGP 3.0 compliant device at 0000:00:00.0.
[   65.436667] agpgart: Device is in legacy mode, falling back to 2.x
[   65.436678] agpgart: Putting AGP V2 device at 0000:00:00.0 into 4x mode
[   65.436722] agpgart: Putting AGP V2 device at 0000:01:00.0 into 4x mode
[   65.689476] [drm] Setting GART location based on new memory map
[   65.689489] [drm] Loading R200 Microcode
[   65.689534] [drm] writeback test succeeded in 1 usecs
[   70.136774] eth0: no IPv6 routers present
[  344.498305] usb 5-7: new high speed USB device using ehci_hcd and address 16
[  344.797788] usb 5-7: new high speed USB device using ehci_hcd and address 17
[  345.660294] usb 5-7: new high speed USB device using ehci_hcd and address 21
[  348.024208] usb 5-7: new high speed USB device using ehci_hcd and address 33
[  348.323691] usb 5-7: new high speed USB device using ehci_hcd and address 34
[  348.623171] usb 5-7: new high speed USB device using ehci_hcd and address 35
[  349.298007] usb 5-7: new high speed USB device using ehci_hcd and address 38
[  355.227751] usb 5-7: new high speed USB device using ehci_hcd and address 69
[  355.902585] usb 5-7: new high speed USB device using ehci_hcd and address 72
[  357.328120] usb 5-7: new high speed USB device using ehci_hcd and address 79
[  357.815276] usb 5-7: new high speed USB device using ehci_hcd and address 81
[  361.305247] usb 5-7: new high speed USB device using ehci_hcd and address 99
[  361.604722] usb 5-7: new high speed USB device using ehci_hcd and address 100
[  363.030259] usb 5-7: new high speed USB device using ehci_hcd and address 107
[  365.206493] usb 5-7: new high speed USB device using ehci_hcd and address 118
[  365.693650] usb 5-7: new high speed USB device using ehci_hcd and address 120
[  366.556161] usb 5-7: new high speed USB device using ehci_hcd and address 124
[  367.606344] usb 5-7: new high speed USB device using ehci_hcd and address 3
[  368.468852] usb 5-7: new high speed USB device using ehci_hcd and address 7
[  369.143693] usb 5-7: new high speed USB device using ehci_hcd and address 10
[  370.007194] usb 5-7: new high speed USB device using ehci_hcd and address 14
[  370.493357] usb 5-7: new high speed USB device using ehci_hcd and address 16
[  371.168192] usb 5-7: new high speed USB device using ehci_hcd and address 19
[  371.843023] usb 5-7: new high speed USB device using ehci_hcd and address 22
[  374.582291] usb 5-7: new high speed USB device using ehci_hcd and address 36
[  376.200486] usb 5-7: new high speed USB device using ehci_hcd and address 44
[  376.878320] usb 5-7: new high speed USB device using ehci_hcd and address 47
[  377.553149] usb 5-7: new high speed USB device using ehci_hcd and address 50
[  379.917056] usb 5-7: new high speed USB device using ehci_hcd and address 62
[  381.534258] usb 5-7: new high speed USB device using ehci_hcd and address 70
[  382.209089] usb 5-7: new high speed USB device using ehci_hcd and address 73
[  382.883933] usb 5-7: new high speed USB device using ehci_hcd and address 76
[  383.183407] usb 5-7: new high speed USB device using ehci_hcd and address 77
[  383.482893] usb 5-7: new high speed USB device using ehci_hcd and address 78
[  383.970053] usb 5-7: new high speed USB device using ehci_hcd and address 80
[  384.461125] usb 5-7: new high speed USB device using ehci_hcd and address 82
[  386.266077] usb 5-7: new high speed USB device using ehci_hcd and address 91
[  390.131462] usb 5-7: new high speed USB device using ehci_hcd and address 111
[  390.431240] usb 5-7: new high speed USB device using ehci_hcd and address 112
[  390.730365] usb 5-7: new high speed USB device using ehci_hcd and address 113
[  392.159966] usb 5-7: new high speed USB device using ehci_hcd and address 120
[  393.022414] usb 5-7: new high speed USB device using ehci_hcd and address 124
[  396.887711] usb 5-7: new high speed USB device using ehci_hcd and address 18
[  397.937893] usb 5-7: new high speed USB device using ehci_hcd and address 23
[  398.425060] usb 5-7: new high speed USB device using ehci_hcd and address 25
[  398.913205] usb 5-7: new high speed USB device using ehci_hcd and address 27
[  399.399380] usb 5-7: new high speed USB device using ehci_hcd and address 29
[  400.449549] usb 5-7: new high speed USB device using ehci_hcd and address 34
[  401.687411] usb 5-7: new high speed USB device using ehci_hcd and address 40
[  402.925262] usb 5-7: new high speed USB device using ehci_hcd and address 46
[  403.412423] usb 5-7: new high speed USB device using ehci_hcd and address 48
[  403.899661] usb 5-7: new high speed USB device using ehci_hcd and address 50
[  412.085422] usb 5-7: new high speed USB device using ehci_hcd and address 93
[  414.644995] usb 5-7: new high speed USB device using ehci_hcd and address 106

---

