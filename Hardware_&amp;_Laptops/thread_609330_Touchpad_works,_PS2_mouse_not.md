---
title: "Touchpad works, PS/2 mouse not"
date: 2007-11-10
forum: Hardware &amp; Laptops
---

### Post by suchard on 2007-11-10
I have installed the Ubuntu 7,10 on my Compaq Presario 1200 P3 800 (12XL530).
All is ok, but my mouse (ps/2) does not works!
I have tried fix it on bios, on /etc/X11/xorg.conf, on /etc/modules.. and i did not have success on it...
Is there anybody that can help me?

here is some information about my hardware/software:


uname -a

Linux ubuntu 2.6.22-14-generic #1 SMP Sun Oct 14 23:05:12 GMT 2007 i686 GNU/Linux

-------------------------------------------------

dmesg.log

[    0.000000] Linux version 2.6.22-14-generic (buildd@palmer) (gcc version 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)) #1 SMP Sun Oct 14 23:05:12 GMT 2007 (Ubuntu 2.6.22-14.46-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
[    0.000000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000ea000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000000b7f0000 (usable)
[    0.000000]  BIOS-e820: 000000000b7f0000 - 000000000b7ffc00 (ACPI data)
[    0.000000]  BIOS-e820: 000000000b7ffc00 - 000000000b800000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000fffe0000 - 0000000100000000 (reserved)
[    0.000000] 0MB HIGHMEM available.
[    0.000000] 183MB LOWMEM available.
[    0.000000] Entering add_active_range(0, 0, 47088) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->    47088
[    0.000000]   HighMem     47088 ->    47088
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->    47088
[    0.000000] On node 0 totalpages: 47088
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 335 pages used for memmap
[    0.000000]   Normal zone: 42657 pages, LIFO batch:7
[    0.000000]   HighMem zone: 0 pages used for memmap
[    0.000000] DMI 2.3 present.
[    0.000000] ACPI: RSDP signature @ 0xC00F72A0 checksum 0
[    0.000000] ACPI: RSDP 000F72A0, 0014 (r0 PTLTD )
[    0.000000] ACPI: RSDT 0B7FC7C0, 0028 (r1 PTLTD    RSDT    6040000  LTP        0)
[    0.000000] ACPI: FACP 0B7FFB8C, 0074 (r1 COMPAQ Wrangler  6040000 PTL_    F4240)
[    0.000000] ACPI: DSDT 0B7FC7E8, 33A4 (r1 Compaq Wrangler  6040000 MSFT  100000B)
[    0.000000] ACPI: FACS 0B7FFFC0, 0040
[    0.000000] ACPI: PM-Timer IO Port: 0x8008
[    0.000000] Allocating PCI resources starting at 10000000 (gap: 0b800000:f47e0000)
[    0.000000] Built 1 zonelists.  Total pages: 46721
[    0.000000] Kernel command line: root=UUID=7bebcd2a-f419-4138-979d-f9fbe058b15b ro quiet splash
[    0.000000] Local APIC disabled by BIOS -- you can enable it with "lapic"
[    0.000000] mapped APIC to ffffd000 (0117c000)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 1024 (order: 10, 4096 bytes)
[    0.000000] Detected 846.883 MHz processor.
[  335.790968] Console: colour VGA+ 80x25
[  335.791364] Dentry cache hash table entries: 32768 (order: 5, 131072 bytes)
[  335.791816] Inode-cache hash table entries: 16384 (order: 4, 65536 bytes)
[  335.817109] Memory: 175200k/188352k available (2015k kernel code, 12608k reserved, 916k data, 364k init, 0k highmem)
[  335.817137] virtual kernel memory layout:
[  335.817140]     fixmap  : 0xfff4d000 - 0xfffff000   ( 712 kB)
[  335.817144]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[  335.817148]     vmalloc : 0xcc000000 - 0xff7fe000   ( 823 MB)
[  335.817151]     lowmem  : 0xc0000000 - 0xcb7f0000   ( 183 MB)
[  335.817155]       .init : 0xc03e3000 - 0xc043e000   ( 364 kB)
[  335.817158]       .data : 0xc02f7d26 - 0xc03dce84   ( 916 kB)
[  335.817162]       .text : 0xc0100000 - 0xc02f7d26   (2015 kB)
[  335.817171] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[  335.817279] SLUB: Genslabs=22, HWalign=32, Order=0-1, MinObjects=4, CPUs=1, Nodes=1
[  335.897316] Calibrating delay using timer specific routine.. 1695.98 BogoMIPS (lpj=3391977)
[  335.897391] Security Framework v1.0.0 initialized
[  335.897421] SELinux:  Disabled at boot.
[  335.897463] Mount-cache hash table entries: 512
[  335.897821] CPU: After generic identify, caps: 0387f9ff 00000000 00000000 00000000 00000000 00000000 00000000
[  335.897850] CPU: L1 I cache: 16K, L1 D cache: 16K
[  335.897857] CPU: L2 cache: 256K
[  335.897865] CPU serial number disabled.
[  335.897871] CPU: After all inits, caps: 0383f9ff 00000000 00000000 00000040 00000000 00000000 00000000
[  335.897897] Compat vDSO mapped to ffffe000.
[  335.897939] Checking 'hlt' instruction... OK.
[  335.913603] SMP alternatives: switching to UP code
[  335.914099] Freeing SMP alternatives: 11k freed
[  335.914948] Early unpacking initramfs... done
[  336.766984] ACPI: Core revision 20070126
[  336.767308] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[  336.770002] ACPI: setting ELCR to 0400 (from 0a00)
[  336.775035] CPU0: Intel Pentium III (Coppermine) stepping 06
[  336.775051] SMP motherboard not detected.
[  336.775058] Local APIC not detected. Using dummy APIC emulation.
[  336.775173] Brought up 1 CPUs
[  336.775527] Booting paravirtualized kernel on bare hardware
[  336.775695] Time:  4:43:38  Date: 10/09/107
[  336.775779] NET: Registered protocol family 16
[  336.776092] EISA bus registered
[  336.776126] ACPI: bus type pci registered
[  336.778047] PCI: PCI BIOS revision 2.10 entry at 0xfd83e, last bus=1
[  336.778054] PCI: Using configuration type 1
[  336.778060] Setting up standard PCI resources
[  336.781679] ACPI: EC: Look up EC in DSDT
[  336.783941] ACPI: EC: GPE=0x06, ports=0x66, 0x62
[  336.787651] ACPI: Interpreter enabled
[  336.787664] ACPI: (supports S0 S1 S4 S5)
[  336.787700] ACPI: Using PIC for interrupt routing
[  336.797141] ACPI: EC: GPE=0x06, ports=0x66, 0x62
[  336.797334] ACPI: PCI Root Bridge [PCI0] (0000:00)
[  336.797356] PCI: Probing PCI hardware (bus 00)
[  336.797782] PCI quirk: region 8000-80ff claimed by vt82c586 ACPI
[  336.797794] PCI quirk: region 8080-808f claimed by vt82c686 SMB
[  336.798250] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[  336.802415] ACPI: PCI Interrupt Link [LNKA] (IRQs 7 9 *11 12)
[  336.802604] ACPI: PCI Interrupt Link [LNKB] (IRQs 9) *0, disabled.
[  336.802821] ACPI: PCI Interrupt Link [LNKC] (IRQs 7 *9 11 12)
[  336.803046] ACPI: PCI Interrupt Link [LNKD] (IRQs 7 9 *11 12)
[  336.803268] Linux Plug and Play Support v0.97 (c) Adam Belay
[  336.803305] pnp: PnP ACPI init
[  336.803341] ACPI: bus type pnp registered
[  336.809164] pnp: PnP ACPI: found 11 devices
[  336.809174] ACPI: ACPI bus type pnp unregistered
[  336.809185] PnPBIOS: Disabled by ACPI PNP
[  336.809397] PCI: Using ACPI for IRQ routing
[  336.809406] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[  336.811028] NET: Registered protocol family 8
[  336.811034] NET: Registered protocol family 20
[  336.811314] pnp: 00:05: iomem range 0x0-0x9ffff could not be reserved
[  336.811323] pnp: 00:05: iomem range 0xdc000-0xdffff has been reserved
[  336.811331] pnp: 00:05: iomem range 0xe0000-0xfffff could not be reserved
[  336.811340] pnp: 00:05: iomem range 0xfffe0000-0xffffffff could not be reserved
[  336.811357] pnp: 00:06: ioport range 0x4d0-0x4d1 has been reserved
[  336.811364] pnp: 00:06: ioport range 0x220-0x22f has been reserved
[  336.811372] pnp: 00:06: ioport range 0x388-0x38b has been reserved
[  336.811381] pnp: 00:06: ioport range 0x8000-0x808f could not be reserved
[  336.811388] pnp: 00:06: ioport range 0x9050-0x9051 has been reserved
[  336.813253] Time: tsc clocksource has been installed.
[  336.842299] PCI: Bridge: 0000:00:01.0
[  336.842304]   IO window: disabled.
[  336.842312]   MEM window: f4100000-f57fffff
[  336.842320]   PREFETCH window: 18000000-180fffff
[  336.842329] PCI: Bus 2, cardbus bridge: 0000:00:0a.0
[  336.842335]   IO window: 00001800-000018ff
[  336.842342]   IO window: 00001c00-00001cff
[  336.842350]   PREFETCH window: 10000000-13ffffff
[  336.842358]   MEM window: 14000000-17ffffff
[  336.842379] PCI: Setting latency timer of device 0000:00:01.0 to 64
[  336.842961] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 9
[  336.842970] PCI: setting IRQ 9 as level-triggered
[  336.842978] ACPI: PCI Interrupt 0000:00:0a.0[A] -> Link [LNKB] -> GSI 9 (level, low) -> IRQ 9
[  336.843022] NET: Registered protocol family 2
[  336.881372] IP route cache hash table entries: 2048 (order: 1, 8192 bytes)
[  336.881520] TCP established hash table entries: 8192 (order: 4, 98304 bytes)
[  336.881972] TCP bind hash table entries: 8192 (order: 4, 65536 bytes)
[  336.882311] TCP: Hash tables configured (established 8192 bind 8192)
[  336.882319] TCP reno registered
[  336.893623] checking if image is initramfs...<6>Switched to high resolution mode on CPU 0
[  337.579702]  it is
[  338.463323] Freeing initrd memory: 7053k freed
[  338.464357] audit: initializing netlink socket (disabled)
[  338.464400] audit(1194583419.500:1): initialized
[  338.470712] VFS: Disk quotas dquot_6.5.1
[  338.470940] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[  338.471354] io scheduler noop registered
[  338.471364] io scheduler anticipatory registered
[  338.471370] io scheduler deadline registered
[  338.471440] io scheduler cfq registered (default)
[  338.471482] PCI: VIA PCI bridge detected. Disabling DAC.
[  338.471491] PCI: Disabling Via external APIC routing
[  338.471535] Boot video device is 0000:01:00.0
[  338.472043] isapnp: Scanning for PnP cards...
[  338.826857] isapnp: No Plug & Play device found
[  338.923825] Real Time Clock Driver v1.12ac
[  338.924097] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[  338.928185] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[  338.929131] input: Macintosh mouse button emulation as /class/input/input0
[  338.929385] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[  338.931670] serio: i8042 KBD port at 0x60,0x64 irq 1
[  338.931688] serio: i8042 AUX port at 0x60,0x64 irq 12
[  338.932234] mice: PS/2 mouse device common for all mice
[  338.932513] EISA: Probing bus 0 at eisa.0
[  338.932535] Cannot allocate resource for EISA slot 1
[  338.932579] Cannot allocate resource for EISA slot 8
[  338.932585] EISA: Detected 0 cards.
[  338.932858] TCP cubic registered
[  338.932955] NET: Registered protocol family 1
[  338.933031] Using IPI No-Shortcut mode
[  338.933449]   Magic number: 15:810:716
[  338.934554] Freeing unused kernel memory: 364k freed
[  339.001024] input: AT Translated Set 2 keyboard as /class/input/input1
[  339.001207] atkbd.c: Spurious ACK on isa0060/serio0. Some program might be trying access hardware directly.
[  340.539801] AppArmor: AppArmor initialized<5>audit(1194583421.500:2):  type=1505 info="AppArmor initialized" pid=1160
[  340.559685] fuse init (API version 7.8)
[  340.574951] Failure registering capabilities with primary security module.
[  340.618052] ACPI: CPU0 (power states: C1[C1] C2[C2])
[    4.808000] Marking TSC unstable due to: possible TSC halt in C2.
[    4.808000] ACPI: Thermal Zone [THRM] (51 C)
[    4.812000] Time: acpi_pm clocksource has been installed.
[    6.528000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[    6.528000] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[    6.528000] VP_IDE: IDE controller at PCI slot 0000:00:07.1
[    6.528000] VP_IDE: chipset revision 16
[    6.528000] VP_IDE: not 100% native mode: will probe irqs later
[    6.528000] VP_IDE: VIA vt82c686a (rev 22) IDE UDMA66 controller on pci0000:00:07.1
[    6.528000]     ide0: BM-DMA at 0x1420-0x1427, BIOS settings: hda:DMA, hdb:pio
[    6.528000]     ide1: BM-DMA at 0x1428-0x142f, BIOS settings: hdc:DMA, hdd:pio
[    6.528000] Probing IDE interface ide0...
[    6.612000] usbcore: registered new interface driver usbfs
[    6.616000] usbcore: registered new interface driver hub
[    6.616000] usbcore: registered new device driver usb
[    6.620000] USB Universal Host Controller Interface driver v3.0
[    7.000000] hda: TOSHIBA MK1516GAP, ATA DISK drive
[    7.036000] Floppy drive(s): fd0 is 1.44M
[    7.068000] FDC 0 is a post-1991 82077
[    7.672000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[    7.672000] Probing IDE interface ide1...
[    8.536000] hdc: TOSHIBA DVD-ROM SD-C2502, ATAPI CD/DVD-ROM drive
[    9.216000] ide1 at 0x170-0x177,0x376 on irq 15
[    9.224000] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 11
[    9.224000] PCI: setting IRQ 11 as level-triggered
[    9.224000] ACPI: PCI Interrupt 0000:00:07.2[D] -> Link [LNKD] -> GSI 11 (level, low) -> IRQ 11
[    9.224000] uhci_hcd 0000:00:07.2: UHCI Host Controller
[    9.224000] uhci_hcd 0000:00:07.2: new USB bus registered, assigned bus number 1
[    9.224000] uhci_hcd 0000:00:07.2: irq 11, io base 0x00001400
[    9.224000] usb usb1: configuration #1 chosen from 1 choice
[    9.228000] hub 1-0:1.0: USB hub found
[    9.228000] hub 1-0:1.0: 2 ports detected
[    9.252000] SCSI subsystem initialized
[    9.276000] libata version 2.21 loaded.
[    9.360000] hda: max request size: 128KiB
[    9.732000] hda: 29486016 sectors (15096 MB), CHS=29252/16/63, UDMA(33)
[    9.732000] hda: cache flushes not supported
[    9.732000]  hda: hda1 hda2 < hda5 >
[    9.828000] hdc: ATAPI 24X DVD-ROM drive, 128kB Cache, UDMA(33)
[    9.828000] Uniform CD-ROM driver Revision: 3.20
[   10.268000] Attempting manual resume
[   10.268000] swsusp: Resume From Partition 3:5
[   10.268000] PM: Checking swsusp image.
[   10.268000] PM: Resume from disk failed.
[   10.336000] kjournald starting.  Commit interval 5 seconds
[   10.336000] EXT3-fs: mounted filesystem with ordered data mode.
[   26.936000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   26.944000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   27.044000] Linux agpgart interface v0.102 (c) Dave Jones
[   27.064000] agpgart: Detected VIA Apollo ProMedia/PLE133Ta chipset
[   27.072000] agpgart: AGP aperture is 64M @ 0xf8000000
[   27.620000] parport_pc: VIA 686A/8231 detected
[   27.620000] parport_pc: probing current configuration
[   27.620000] parport_pc: Current parallel port base: 0x378
[   27.620000] parport0: PC-style at 0x378 (0x778), irq 7, using FIFO [PCSPP,TRISTATE,COMPAT,ECP]
[   27.884000] parport_pc: VIA parallel port: io=0x378, irq=7
[   28.784000] input: PC Speaker as /class/input/input2
[   28.988000] Yenta: CardBus bridge found at 0000:00:0a.0 [0e11:b103]
[   28.988000] Yenta: Enabling burst memory read transactions
[   28.988000] Yenta: Using CSCINT to route CSC interrupts to PCI
[   28.988000] Yenta: Routing CardBus interrupts to PCI
[   28.988000] Yenta TI: socket 0000:00:0a.0, mfunc 0x01001002, devctl 0x64
[   29.220000] Yenta: ISA IRQ mask 0x0018, PCI irq 9
[   29.220000] Socket status: 30000006
[   29.336000] via686a 0000:00:07.4: base address not set - upgrade BIOS or use force_addr=0xaddr
[   29.752000] Synaptics Touchpad, model: 1, fw: 4.6, id: 0xf42a1, caps: 0x80471b/0x0
[   29.824000] input: SynPS/2 Synaptics TouchPad as /class/input/input3
[   30.776000] cs: IO port probe 0x100-0x3af: excluding 0x200-0x207
[   30.780000] cs: IO port probe 0x3e0-0x4ff: clean.
[   30.780000] cs: IO port probe 0x820-0x8ff: clean.
[   30.780000] cs: IO port probe 0xc00-0xcf7: clean.
[   30.784000] cs: IO port probe 0xa00-0xaff: clean.
[   31.100000] ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 9
[   31.100000] ACPI: PCI Interrupt 0000:00:07.5[C] -> Link [LNKC] -> GSI 9 (level, low) -> IRQ 9
[   31.100000] PCI: Setting latency timer of device 0000:00:07.5 to 64
[   32.972000] loop: module loaded
[   33.024000] lp0: using parport0 (interrupt-driven).
[   33.216000] Adding 546168k swap on /dev/hda5.  Priority:-1 extents:1 across:546168k
[   33.836000] EXT3 FS on hda1, internal journal
[   36.676000] ACPI: AC Adapter [AC] (off-line)
[   36.768000] input: Power Button (FF) as /class/input/input4
[   36.768000] ACPI: Power Button (FF) [PWRF]
[   36.796000] input: Power Button (CM) as /class/input/input5
[   36.796000] ACPI: Power Button (CM) [PWRB]
[   36.808000] input: Sleep Button (CM) as /class/input/input6
[   36.808000] ACPI: Sleep Button (CM) [SLPB]
[   37.196000] No dock devices found.
[   37.236000] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[   37.292000] ACPI: Battery Slot [BAT0] (battery present)
[   40.740000] ppdev: user-space parallel port driver
[   41.040000] audit(1194590658.096:3):  type=1503 operation="inode_permission" requested_mask="a" denied_mask="a" name="/dev/tty" pid=4488 profile="/usr/sbin/cupsd"
[   41.180000] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[   41.180000] apm: overridden by ACPI.
[   41.976000] Failure registering capabilities with primary security module.
[   42.616000] input: Mouseemu virtual keyboard as /class/input/input7
[   42.716000] input: Mouseemu virtual mouse as /class/input/input8
[   71.672000] psmouse.c: TouchPad at isa0060/serio1/input0 lost sync at byte 1
[   71.676000] psmouse.c: TouchPad at isa0060/serio1/input0 lost sync at byte 1
[   71.676000] psmouse.c: TouchPad at isa0060/serio1/input0 lost sync at byte 1
[   71.720000] psmouse.c: TouchPad at isa0060/serio1/input0 lost sync at byte 1
[   71.720000] psmouse.c: TouchPad at isa0060/serio1/input0 lost sync at byte 1
[   71.720000] psmouse.c: issuing reconnect request
[  346.164000] psmouse.c: TouchPad at isa0060/serio1/input0 lost sync at byte 1
[  346.168000] psmouse.c: TouchPad at isa0060/serio1/input0 lost sync at byte 1
[  346.168000] psmouse.c: TouchPad at isa0060/serio1/input0 lost sync at byte 1
[  346.212000] psmouse.c: TouchPad at isa0060/serio1/input0 lost sync at byte 1
[  346.216000] psmouse.c: TouchPad at isa0060/serio1/input0 lost sync at byte 1
[  346.216000] psmouse.c: issuing reconnect request
[  347.012000] psmouse.c: TouchPad at isa0060/serio1/input0 lost sync at byte 1
[  347.016000] psmouse.c: TouchPad at isa0060/serio1/input0 lost sync at byte 1
[  347.016000] psmouse.c: TouchPad at isa0060/serio1/input0 lost sync at byte 1
[  348.628000] psmouse.c: TouchPad at isa0060/serio1/input0 lost sync at byte 1
[  348.676000] psmouse.c: TouchPad at isa0060/serio1/input0 lost sync at byte 4
[  348.676000] psmouse.c: issuing reconnect request
[  349.608000] psmouse.c: TouchPad at isa0060/serio1/input0 lost sync at byte 1
[  349.608000] psmouse.c: TouchPad at isa0060/serio1/input0 lost sync at byte 1
[  349.608000] psmouse.c: TouchPad at isa0060/serio1/input0 lost sync at byte 1
[  349.672000] psmouse.c: TouchPad at isa0060/serio1/input0 lost sync at byte 1
[  349.672000] psmouse.c: TouchPad at isa0060/serio1/input0 lost sync at byte 1
[  349.672000] psmouse.c: issuing reconnect request
[  360.160000] psmouse.c: TouchPad at isa0060/serio1/input0 lost sync at byte 1
[  360.164000] psmouse.c: TouchPad at isa0060/serio1/input0 lost sync at byte 1
[  360.164000] psmouse.c: TouchPad at isa0060/serio1/input0 lost sync at byte 1
[ 3063.148000] psmouse.c: TouchPad at isa0060/serio1/input0 - driver resynched.
[ 4797.844000] UDF-fs: No VRS found
[ 4797.900000] ISO 9660 Extensions: Microsoft Joliet Level 3
[ 4798.036000] ISO 9660 Extensions: RRIP_1991A
[ 4821.204000] usb 1-1: new full speed USB device using uhci_hcd and address 2
[ 4821.368000] usb 1-1: configuration #1 chosen from 1 choice
[ 4822.524000] eth0: register 'cdc_ether' at usb-0000:00:07.2-1, CDC Ethernet Device, 00:14:f8:62:bc:5d
[ 4822.524000] usbcore: registered new interface driver cdc_ether
[ 4830.208000] NET: Registered protocol family 17
[ 4836.796000] NET: Registered protocol family 10
[ 4836.800000] lo: Disabled Privacy Extensions
[ 4846.980000] eth0: no IPv6 routers present
[ 4887.252000] psmouse.c: TouchPad at isa0060/serio1/input0 lost sync at byte 1
[ 4887.256000] psmouse.c: TouchPad at isa0060/serio1/input0 lost sync at byte 1
[ 4887.256000] psmouse.c: TouchPad at isa0060/serio1/input0 lost sync at byte 1
[ 4887.340000] psmouse.c: TouchPad at isa0060/serio1/input0 lost sync at byte 1
[ 4887.340000] psmouse.c: TouchPad at isa0060/serio1/input0 lost sync at byte 1
[ 4887.340000] psmouse.c: issuing reconnect request
[ 4891.856000] psmouse.c: TouchPad at isa0060/serio1/input0 lost sync at byte 1
[ 4891.856000] psmouse.c: TouchPad at isa0060/serio1/input0 lost sync at byte 1
[ 4891.860000] psmouse.c: TouchPad at isa0060/serio1/input0 lost sync at byte 1
[ 4902.780000] psmouse.c: TouchPad at isa0060/serio1/input0 - driver resynched.
[ 5523.556000] psmouse.c: TouchPad at isa0060/serio1/input0 lost sync at byte 1
[ 5523.556000] psmouse.c: TouchPad at isa0060/serio1/input0 lost sync at byte 1
[ 5523.556000] psmouse.c: TouchPad at isa0060/serio1/input0 lost sync at byte 1
[ 5523.608000] psmouse.c: TouchPad at isa0060/serio1/input0 lost sync at byte 1
[ 5523.612000] psmouse.c: TouchPad at isa0060/serio1/input0 lost sync at byte 1
[ 5523.612000] psmouse.c: issuing reconnect request
[14891.864000] usb 1-1: USB disconnect, address 2
[14891.864000] eth0: unregister 'cdc_ether' usb-0000:00:07.2-1, CDC Ethernet Device
[19479.584000] usb 1-1: new full speed USB device using uhci_hcd and address 3
[19479.752000] usb 1-1: configuration #1 chosen from 1 choice
[19479.760000] eth0: register 'cdc_ether' at usb-0000:00:07.2-1, CDC Ethernet Device, 00:14:f8:62:bc:5d
[19502.600000] eth0: no IPv6 routers present
[25423.036000] usb 1-1: USB disconnect, address 3
[25423.036000] eth0: unregister 'cdc_ether' usb-0000:00:07.2-1, CDC Ethernet Device
[30779.684000] usb 1-1: new full speed USB device using uhci_hcd and address 4
[30779.852000] usb 1-1: configuration #1 chosen from 1 choice
[30779.860000] eth0: register 'cdc_ether' at usb-0000:00:07.2-1, CDC Ethernet Device, 00:14:f8:62:bc:5d
[30801.324000] eth0: no IPv6 routers present
[31035.428000] UDF-fs: Partition marked readonly; forcing readonly mount
[31036.000000] UDF-fs INFO UDF 0.9.8.1 (2004/29/09) Mounting volume 'DAVID_GILMOUR', timestamp 2007/05/07 01:04 (1f88)
[31575.000000] usb 1-2: new full speed USB device using uhci_hcd and address 5
[31575.160000] usb 1-2: configuration #1 chosen from 1 choice
[31580.700000] Linux video capture interface: v2.00
[31581.200000] /build/buildd/linux-ubuntu-modules-2.6.22-2.6.22/debian/build/build-generic/media/gspcav1/gspca_core.c: USB SPCA5XX camera found. SONIX sn9c10[1 2]
[31581.204000] usbcore: registered new interface driver gspca
[31581.204000] /build/buildd/linux-ubuntu-modules-2.6.22-2.6.22/debian/build/build-generic/media/gspcav1/gspca_core.c: gspca driver 01.00.12 registered
[31581.696000] sn9c102: V4L2 driver for SN9C1xx PC Camera Controllers v1:1.44
[31581.700000] usbcore: registered new interface driver sn9c102
[32355.176000] UDF-fs: Partition marked readonly; forcing readonly mount
[32355.232000] UDF-fs INFO UDF 0.9.8.1 (2004/29/09) Mounting volume 'DAVID_GILMOUR', timestamp 2007/05/07 01:04 (1f88)
[32500.432000] psmouse.c: bad data from KBC - timeout
[34214.448000] /build/buildd/linux-ubuntu-modules-2.6.22-2.6.22/debian/build/build-generic/media/gspcav1/gspca_core.c: VIDIOCMCAPTURE: invalid format (7)
[34214.964000] /build/buildd/linux-ubuntu-modules-2.6.22-2.6.22/debian/build/build-generic/media/gspcav1/gspca_core.c: VIDIOCMCAPTURE: invalid format (9)
[34214.964000] /build/buildd/linux-ubuntu-modules-2.6.22-2.6.22/debian/build/build-generic/media/gspcav1/gspca_core.c: VIDIOCMCAPTURE: invalid format (14)
[34214.964000] /build/buildd/linux-ubuntu-modules-2.6.22-2.6.22/debian/build/build-generic/media/gspcav1/gspca_core.c: VIDIOCMCAPTURE: invalid format (13)
[34214.964000] /build/buildd/linux-ubuntu-modules-2.6.22-2.6.22/debian/build/build-generic/media/gspcav1/gspca_core.c: VIDIOCMCAPTURE: invalid format (16)
[34214.964000] /build/buildd/linux-ubuntu-modules-2.6.22-2.6.22/debian/build/build-generic/media/gspcav1/gspca_core.c: VIDIOCMCAPTURE: invalid format (11)
[34214.964000] /build/buildd/linux-ubuntu-modules-2.6.22-2.6.22/debian/build/build-generic/media/gspcav1/gspca_core.c: VIDIOCMCAPTURE: invalid format (6)
[35282.548000] UDF-fs: No VRS found
[35282.648000] ISO 9660 Extensions: Microsoft Joliet Level 3
[35282.692000] ISO 9660 Extensions: RRIP_1991A
[35284.604000] hdc: media error (bad sector): status=0x51 { DriveReady SeekComplete Error }
[35284.604000] hdc: media error (bad sector): error=0x30 { LastFailedSense=0x03 }
[35284.604000] ide: failed opcode was: unknown
[35284.604000] hdc: error code: 0x70  sense_key: 0x03  asc: 0x11  ascq: 0x00
[35284.604000] end_request: I/O error, dev hdc, sector 745688
[35284.604000] Buffer I/O error on device hdc, logical block 186422
[35284.604000] Buffer I/O error on device hdc, logical block 186423
[35284.604000] Buffer I/O error on device hdc, logical block 186424
[35284.604000] Buffer I/O error on device hdc, logical block 186425
[35284.604000] Buffer I/O error on device hdc, logical block 186426
[35284.604000] Buffer I/O error on device hdc, logical block 186427
[35284.604000] Buffer I/O error on device hdc, logical block 186428
[35284.604000] Buffer I/O error on device hdc, logical block 186429
[35284.604000] Buffer I/O error on device hdc, logical block 186430
[35284.604000] Buffer I/O error on device hdc, logical block 186431
[35286.104000] hdc: media error (bad sector): status=0x51 { DriveReady SeekComplete Error }
[35286.104000] hdc: media error (bad sector): error=0x30 { LastFailedSense=0x03 }
[35286.104000] ide: failed opcode was: unknown
[35286.104000] hdc: error code: 0x70  sense_key: 0x03  asc: 0x11  ascq: 0x00
[35286.104000] end_request: I/O error, dev hdc, sector 745748
[35849.520000] UDF-fs: No VRS found
[35849.572000] ISO 9660 Extensions: Microsoft Joliet Level 3
[35849.636000] ISO 9660 Extensions: RRIP_1991A
[36033.956000] hdc: media error (bad sector): status=0x51 { DriveReady SeekComplete Error }
[36033.956000] hdc: media error (bad sector): error=0x30 { LastFailedSense=0x03 }
[36033.956000] ide: failed opcode was: unknown
[36033.956000] hdc: error code: 0x70  sense_key: 0x03  asc: 0x11  ascq: 0x00
[36033.956000] end_request: I/O error, dev hdc, sector 745688
[36033.956000] printk: 37 messages suppressed.
[36033.956000] Buffer I/O error on device hdc, logical block 186422
[36033.956000] Buffer I/O error on device hdc, logical block 186423
[36033.956000] Buffer I/O error on device hdc, logical block 186424
[36033.956000] Buffer I/O error on device hdc, logical block 186425
[36033.956000] Buffer I/O error on device hdc, logical block 186426
[36033.956000] Buffer I/O error on device hdc, logical block 186427
[36033.956000] Buffer I/O error on device hdc, logical block 186428
[36033.956000] Buffer I/O error on device hdc, logical block 186429
[36033.956000] Buffer I/O error on device hdc, logical block 186430
[36034.780000] hdc: media error (bad sector): status=0x51 { DriveReady SeekComplete Error }
[36034.780000] hdc: media error (bad sector): error=0x30 { LastFailedSense=0x03 }
[36034.780000] ide: failed opcode was: unknown
[36034.780000] hdc: error code: 0x70  sense_key: 0x03  asc: 0x11  ascq: 0x06
[36034.780000] end_request: I/O error, dev hdc, sector 745724
[36034.780000] Buffer I/O error on device hdc, logical block 186431
[38502.004000] psmouse.c: bad data from KBC - timeout


-------------------------------------------------------------------------------------------------------------------
-------------------------------------------------------------------------------------------------------------------


lspci-vvnn.log


00:00.0 Host bridge [0600]: VIA Technologies, Inc. VT8601 [Apollo ProMedia] [1106:0601] (rev 05)
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort+ >SERR- <PERR+
	Latency: 0
	Region 0: Memory at f8000000 (32-bit, prefetchable) [size=64M]
	Capabilities: [a0] AGP version 2.0
		Status: RQ=8 Iso- ArqSz=0 Cal=0 SBA+ ITACoh- GART64- HTrans- 64bit- FW- AGP3- Rate=x1,x2
		Command: RQ=1 ArqSz=0 Cal=0 SBA- AGP- GART64- 64bit- FW- Rate=<none>

00:01.0 PCI bridge [0604]: VIA Technologies, Inc. VT8601 [Apollo ProMedia AGP] [1106:8601] (prog-if 00 [Normal decode])
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz+ UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort+ >SERR- <PERR+
	Latency: 0
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
	Memory behind bridge: f4100000-f57fffff
	Prefetchable memory behind bridge: 18000000-180fffff
	Secondary status: 66MHz- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- <SERR- <PERR-
	BridgeCtl: Parity- SERR- NoISA+ VGA+ MAbort- >Reset- FastB2B-

00:07.0 ISA bridge [0601]: VIA Technologies, Inc. VT82C686 [Apollo Super South] [1106:0686] (rev 22)
	Subsystem: VIA Technologies, Inc. VT82C686/A PCI to ISA Bridge [1106:0000]
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping+ SERR- FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0

00:07.1 IDE interface [0101]: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE [1106:0571] (rev 10) (prog-if 8a [Master SecP PriP])
	Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 64
	Region 0: [virtual] Memory at 000001f0 (32-bit, non-prefetchable) [disabled] [size=8]
	Region 1: [virtual] Memory at 000003f0 (type 3, non-prefetchable) [disabled] [size=1]
	Region 2: [virtual] Memory at 00000170 (32-bit, non-prefetchable) [disabled] [size=8]
	Region 3: [virtual] Memory at 00000370 (type 3, non-prefetchable) [disabled] [size=1]
	Region 4: I/O ports at 1420 [size=16]
	Capabilities: [c0] Power Management version 2
		Flags: PMEClk- DSI- D1- D2- AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot-,D3cold-)
		Status: D0 PME-Enable- DSel=0 DScale=0 PME-

00:07.2 USB Controller [0c03]: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller [1106:3038] (rev 10) (prog-if 00 [UHCI])
	Subsystem: First International Computer, Inc. VA-502 Mainboard [0925:1234]
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV+ VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 64, Cache Line Size: 32 bytes
	Interrupt: pin D routed to IRQ 11
	Region 4: I/O ports at 1400 [size=32]
	Capabilities: [80] Power Management version 2
		Flags: PMEClk- DSI- D1- D2- AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot-,D3cold-)
		Status: D0 PME-Enable- DSel=0 DScale=0 PME-

00:07.4 ISA bridge [0601]: VIA Technologies, Inc. VT82C686 [Apollo Super ACPI] [1106:3057] (rev 30)
	Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Interrupt: pin ? routed to IRQ 10
	Capabilities: [68] Power Management version 2
		Flags: PMEClk- DSI- D1- D2- AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot-,D3cold-)
		Status: D0 PME-Enable- DSel=0 DScale=0 PME-

00:07.5 Multimedia audio controller [0401]: VIA Technologies, Inc. VT82C686 AC97 Audio Controller [1106:3058] (rev 20)
	Subsystem: Compaq Computer Corporation Soundmax integrated digital audio [0e11:b194]
	Control: I/O+ Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Interrupt: pin C routed to IRQ 9
	Region 0: I/O ports at 1000 [size=256]
	Region 1: I/O ports at 1434 [size=4]
	Region 2: I/O ports at 1430 [size=4]
	Capabilities: [c0] Power Management version 2
		Flags: PMEClk- DSI- D1- D2- AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot-,D3cold-)
		Status: D0 PME-Enable- DSel=0 DScale=0 PME-

00:09.0 Communication controller [0780]: Conexant HSF 56k Data/Fax Modem [14f1:2013] (rev 01)
	Subsystem: Compaq Computer Corporation Bear [0e11:b195]
	Control: I/O+ Mem+ BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Interrupt: pin A routed to IRQ 11
	Region 0: Memory at f4000000 (32-bit, non-prefetchable) [size=64K]
	Region 1: I/O ports at 1438 [size=8]
	Capabilities: [40] Power Management version 2
		Flags: PMEClk- DSI+ D1- D2- AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot+,D3cold+)
		Status: D0 PME-Enable+ DSel=0 DScale=0 PME-

00:0a.0 CardBus bridge [0607]: Texas Instruments PCI1410 PC card Cardbus Controller [104c:ac50] (rev 01)
	Subsystem: Compaq Computer Corporation Unknown device [0e11:b103]
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 168, Cache Line Size: 128 bytes
	Interrupt: pin A routed to IRQ 9
	Region 0: Memory at 18100000 (32-bit, non-prefetchable) [size=4K]
	Bus: primary=00, secondary=02, subordinate=05, sec-latency=176
	Memory window 0: 10000000-13fff000 (prefetchable)
	Memory window 1: 14000000-17fff000
	I/O window 0: 00001800-000018ff
	I/O window 1: 00001c00-00001cff
	BridgeCtl: Parity- SERR- ISA- VGA- MAbort- >Reset+ 16bInt+ PostWrite+
	16-bit legacy interface ports at 0001

01:00.0 VGA compatible controller [0300]: Trident Microsystems CyberBlade i1 [1023:8520] (rev 6a) (prog-if 00 [VGA])
	Subsystem: Compaq Computer Corporation CyberBlade i1 AGP [0e11:b16e]
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B+
	Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 64
	Interrupt: pin A routed to IRQ 9
	Region 0: Memory at f5000000 (32-bit, non-prefetchable) [size=8M]
	Region 1: Memory at f4100000 (32-bit, non-prefetchable) [size=128K]
	Region 2: Memory at f4800000 (32-bit, non-prefetchable) [size=8M]
	[virtual] Expansion ROM at 18000000 [disabled] [size=64K]
	Capabilities: [80] AGP version 1.0
		Status: RQ=33 Iso- ArqSz=0 Cal=0 SBA+ ITACoh- GART64- HTrans- 64bit- FW- AGP3- Rate=x1,x2
		Command: RQ=1 ArqSz=0 Cal=0 SBA- AGP- GART64- 64bit- FW- Rate=<none>
	Capabilities: [90] Power Management version 1
		Flags: PMEClk- DSI+ D1+ D2+ AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot-,D3cold-)
		Status: D0 PME-Enable- DSel=0 DScale=0 PME-






THANKS!!

---

### Post by suchard on 2007-11-11
no one knows?

---

### Post by RepoMonkey on 2008-02-18
Having the same problem - anyone have a fix?

---

### Post by Jay Jay on 2008-02-18
Same here, haven't seen a solution for it yet...

---

