---
title: "Leadtek Winfast 2000XP Expert"
date: 2007-12-18
forum: Hardware &amp; Laptops
---

### Post by blueyez on 2007-12-18
i don't know if this should be at Multimedia & Video but i'll post it here

i have a Leadtek Winfast 2000XP Expert tv tunner 
and i can't make it work.
tips ? what should i do :(

dmesg

> 
[    0.000000] Linux version 2.6.22-14-generic (buildd@palmer) (gcc version 4.1.
3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)) #1 SMP Sun Oct 14 23:05:12 GMT
 2007 (Ubuntu 2.6.22-14.46-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e4000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000002ffc0000 (usable)
[    0.000000]  BIOS-e820: 000000002ffc0000 - 000000002ffd0000 (ACPI data)
[    0.000000]  BIOS-e820: 000000002ffd0000 - 0000000030000000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000ff780000 - 0000000100000000 (reserved)
[    0.000000] 0MB HIGHMEM available.
[    0.000000] 767MB LOWMEM available.
[    0.000000] found SMP MP-table at 000ff780
[    0.000000] Entering add_active_range(0, 0, 196544) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   196544
[    0.000000]   HighMem    196544 ->   196544
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   196544
[    0.000000] On node 0 totalpages: 196544
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 1503 pages used for memmap
[    0.000000]   Normal zone: 190945 pages, LIFO batch:31
[    0.000000]   HighMem zone: 0 pages used for memmap
[    0.000000] DMI 2.3 present.
[    0.000000] ACPI: RSDP signature @ 0xC00F9ED0 checksum 0
[    0.000000] ACPI: RSDP 000F9ED0, 0014 (r0 ACPIAM)
[    0.000000] ACPI: RSDT 2FFC0000, 0030 (r1 A M I  OEMRSDT   2000616 MSFT
 97)
[    0.000000] ACPI: FACP 2FFC0200, 0081 (r2 A M I  OEMFACP   2000616 MSFT
 97)
[    0.000000] ACPI: DSDT 2FFC0400, 441D (r1  A0128 A0128003        3 INTL  2002
026)
[    0.000000] ACPI: FACS 2FFD0000, 0040
[    0.000000] ACPI: APIC 2FFC0390, 0068 (r1 A M I  OEMAPIC   2000616 MSFT
 97)
[    0.000000] ACPI: OEMB 2FFD0040, 0041 (r1 A M I  OEMBIOS   2000616 MSFT
 97)
[    0.000000] Nvidia board detected. Ignoring ACPI timer override.
[    0.000000] If you got timer trouble try acpi_use_timer_override
[    0.000000] ACPI: PM-Timer IO Port: 0x4008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] Processor #0 15:12 APIC version 16
[    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 1, version 17, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: BIOS IRQ0 pin2 override ignored.
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 14 global_irq 14 high edge)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 15 global_irq 15 high edge)
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] ACPI: IRQ14 used by override.
[    0.000000] ACPI: IRQ15 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] Allocating PCI resources starting at 40000000 (gap: 30000000:cec0
0000)
[    0.000000] Built 1 zonelists.  Total pages: 195009
[    0.000000] Kernel command line: root=UUID=2fec30e6-04b5-4495-a13b-5221dc58c9
56 ro quiet splash
[    0.000000] mapped APIC to ffffd000 (fee00000)
[    0.000000] mapped IOAPIC to ffffc000 (fec00000)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] Detected 1607.837 MHz processor.
[   25.509525] spurious 8259A interrupt: IRQ7.
[   25.510687] Console: colour VGA+ 80x25
[   25.511176] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[   25.512046] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[   25.527657] Memory: 767500k/786176k available (2015k kernel code, 18144k rese
rved, 916k data, 364k init, 0k highmem)
[   25.527668] virtual kernel memory layout:
[   25.527670]     fixmap  : 0xfff4d000 - 0xfffff000   ( 712 kB)
[   25.527671]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   25.527673]     vmalloc : 0xf0800000 - 0xff7fe000   ( 239 MB)
[   25.527674]     lowmem  : 0xc0000000 - 0xeffc0000   ( 767 MB)
[   25.527676]       .init : 0xc03e3000 - 0xc043e000   ( 364 kB)
[   25.527677]       .data : 0xc02f7d26 - 0xc03dce84   ( 916 kB)
[   25.527679]       .text : 0xc0100000 - 0xc02f7d26   (2015 kB)
[   25.527682] Checking if this processor honours the WP bit even in supervisor
mode... Ok.
[   25.527720] SLUB: Genslabs=22, HWalign=64, Order=0-1, MinObjects=4, CPUs=1, N
odes=1
[   25.607630] Calibrating delay using timer specific routine.. 3217.83 BogoMIPS
 (lpj=6435672)
[   25.607654] Security Framework v1.0.0 initialized
[   25.607659] SELinux:  Disabled at boot.
[   25.607673] Mount-cache hash table entries: 512
[   25.607781] CPU: After generic identify, caps: 078bfbff e3d3fbff 00000000 000
00000 00000001 00000000 00000001
[   25.607791] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[   25.607794] CPU: L2 Cache: 256K (64 bytes/line)
[   25.607797] CPU: After all inits, caps: 078bfbff e3d3fbff 00000000 00000410 0
0000001 00000000 00000001
[   25.607806] Compat vDSO mapped to ffffe000.
[   25.607816] Checking 'hlt' instruction... OK.
[   25.623728] SMP alternatives: switching to UP code
[   25.623937] Freeing SMP alternatives: 11k freed
[   25.624258] Early unpacking initramfs... done
[   25.992249] ACPI: Core revision 20070126
[   25.992323] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not
found.
[   25.994567] CPU0: AMD Sempron(tm) Processor 2800+ stepping 02
[   25.994584] Total of 1 processors activated (3217.83 BogoMIPS).
[   25.994726] ENABLING IO-APIC IRQs
[   25.994921] ..TIMER: vector=0x31 apic1=0 pin1=0 apic2=-1 pin2=-1
[   26.138975] Brought up 1 CPUs
[   26.139097] Booting paravirtualized kernel on bare hardware
[   26.139145] Time: 18:25:51  Date: 11/18/107
[   26.139171] NET: Registered protocol family 16
[   26.139256] EISA bus registered
[   26.139265] ACPI: bus type pci registered
[   26.139950] PCI: PCI BIOS revision 2.10 entry at 0xf0031, last bus=2
[   26.139952] PCI: Using configuration type 1
[   26.139954] Setting up standard PCI resources
[   26.146968] ACPI: EC: Look up EC in DSDT
[   26.151000] ACPI: Interpreter enabled
[   26.151003] ACPI: (supports S0 S1 S3 S4 S5)
[   26.151020] ACPI: Using IOAPIC for interrupt routing
[   26.160080] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   26.160091] PCI: Probing PCI hardware (bus 00)
[   26.160834] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   26.160992] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P1._PRT]
[   26.166982] ACPI: PCI Interrupt Link [LNKA] (IRQs 16 17 18 19) *0, disabled.
[   26.167180] ACPI: PCI Interrupt Link [LNKB] (IRQs 16 17 18 19) *11
[   26.167372] ACPI: PCI Interrupt Link [LNKC] (IRQs 16 17 18 19) *0, disabled.
[   26.167564] ACPI: PCI Interrupt Link [LNKD] (IRQs 16 17 18 19) *9
[   26.167760] ACPI: PCI Interrupt Link [LNKE] (IRQs 16 17 18 19) *11
[   26.167978] ACPI: PCI Interrupt Link [LUS0] (IRQs 20 21 22) *3
[   26.168193] ACPI: PCI Interrupt Link [LUS1] (IRQs 20 21 22) *9
[   26.168380] ACPI: PCI Interrupt Link [LUS2] (IRQs 20 21 22) *10
[   26.168568] ACPI: PCI Interrupt Link [LKLN] (IRQs 20 21 22) *7
[   26.168756] ACPI: PCI Interrupt Link [LAUI] (IRQs 20 21 22) *10
[   26.168943] ACPI: PCI Interrupt Link [LKMO] (IRQs 20 21 22) *0, disabled.
[   26.169131] ACPI: PCI Interrupt Link [LKSM] (IRQs 20 21 22) *0, disabled.
[   26.169319] ACPI: PCI Interrupt Link [LTID] (IRQs 20 21 22) *0
[   26.169519] ACPI: PCI Interrupt Link [LTIE] (IRQs 20 21 22) *0, disabled.
[   26.169748] ACPI: PCI Interrupt Link [LATA] (IRQs 20 21 22) *14
[   26.169875] ACPI: Power Resource [ISAV] (on)
[   26.169889] Linux Plug and Play Support v0.97 (c) Adam Belay
[   26.169900] pnp: PnP ACPI init
[   26.169914] ACPI: bus type pnp registered
[   26.174753] pnp: PnP ACPI: found 15 devices
[   26.174756] ACPI: ACPI bus type pnp unregistered
[   26.174761] PnPBIOS: Disabled by ACPI PNP
[   26.174812] PCI: Using ACPI for IRQ routing
[   26.174815] PCI: If a device doesn't work, try "pci=routeirq".  If it helps,
post a report
[   26.178847] NET: Registered protocol family 8
[   26.178849] NET: Registered protocol family 20
[   26.178886] Time: tsc clocksource has been installed.
[   26.178944] pnp: 00:08: iomem range 0xfec00000-0xfec00fff could not be reserv
ed
[   26.178948] pnp: 00:08: iomem range 0xfee00000-0xfeefffff could not be reserv
ed
[   26.178952] pnp: 00:08: iomem range 0xff780000-0xff7bffff could not be reserv
ed
[   26.178959] pnp: 00:0b: ioport range 0x480-0x487 has been reserved
[   26.178963] pnp: 00:0b: ioport range 0xd00-0xd07 has been reserved
[   26.178969] pnp: 00:0e: iomem range 0x0-0x9ffff could not be reserved
[   26.178973] pnp: 00:0e: iomem range 0xc0000-0xdffff could not be reserved
[   26.178976] pnp: 00:0e: iomem range 0xe0000-0xfffff could not be reserved
[   26.178980] pnp: 00:0e: iomem range 0x100000-0x2fffffff could not be reserved
[   26.209203] PCI: Bridge: 0000:00:0b.0
[   26.209206]   IO window: a000-afff
[   26.209211]   MEM window: fc900000-fc9fffff
[   26.209215]   PREFETCH window: ac800000-ec7fffff
[   26.209219] PCI: Bridge: 0000:00:0e.0
[   26.209222]   IO window: b000-bfff
[   26.209225]   MEM window: fca00000-feafffff
[   26.209228]   PREFETCH window: disabled.
[   26.209238] PCI: Setting latency timer of device 0000:00:0e.0 to 64
[   26.209251] NET: Registered protocol family 2
[   26.246837] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[   26.246972] TCP established hash table entries: 131072 (order: 8, 1572864 byt
es)
[   26.248746] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[   26.249358] TCP: Hash tables configured (established 131072 bind 65536)
[   26.249362] TCP reno registered
[   26.258923] checking if image is initramfs... it is
[   26.710193] Switched to high resolution mode on CPU 0
[   26.983659] Freeing initrd memory: 7326k freed
[   26.984028] audit: initializing netlink socket (disabled)
[   26.984040] audit(1198002351.052:1): initialized
[   26.985894] VFS: Disk quotas dquot_6.5.1
[   26.985949] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   26.986044] io scheduler noop registered
[   26.986046] io scheduler anticipatory registered
[   26.986049] io scheduler deadline registered
[   26.986064] io scheduler cfq registered (default)
[   27.017692] Boot video device is 0000:01:00.0
[   27.017849] isapnp: Scanning for PnP cards...
[   27.371091] isapnp: No Plug & Play device found
[   27.398383] Real Time Clock Driver v1.12ac
[   27.398470] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing
enabled
[   27.398552] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   27.399365] 00:0d: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   27.400059] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 bloc
ksize
[   27.400281] input: Macintosh mouse button emulation as /class/input/input0
[   27.400359] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f03:PS2M] at 0x60,0x64 irq
 1,12
[   27.402862] serio: i8042 KBD port at 0x60,0x64 irq 1
[   27.402868] serio: i8042 AUX port at 0x60,0x64 irq 12
[   27.403040] mice: PS/2 mouse device common for all mice
[   27.403152] EISA: Probing bus 0 at eisa.0
[   27.403167] Cannot allocate resource for EISA slot 4
[   27.403170] Cannot allocate resource for EISA slot 5
[   27.403178] EISA: Detected 0 cards.
[   27.403272] TCP cubic registered
[   27.403285] NET: Registered protocol family 1
[   27.403308] Using IPI No-Shortcut mode
[   27.403468]   Magic number: 3:673:443
[   27.403855] Freeing unused kernel memory: 364k freed
[   27.445112] input: AT Translated Set 2 keyboard as /class/input/input1
[   28.623170] AppArmor: AppArmor initialized<5>audit(1198002352.552:2):  type=1
505 info="AppArmor initialized" pid=1213
[   28.672878] fuse init (API version 7.8)
[   28.678709] Failure registering capabilities with primary security module.
[   29.237792] usbcore: registered new interface driver usbfs
[   29.237817] usbcore: registered new interface driver hub
[   29.237839] usbcore: registered new device driver usb
[   29.238589] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Dr
iver
[   29.238937] ACPI: PCI Interrupt Link [LUS0] enabled at IRQ 22
[   29.238946] ACPI: PCI Interrupt 0000:00:02.0[A] -> Link [LUS0] -> GSI 22 (lev
el, low) -> IRQ 16
[   29.238958] PCI: Setting latency timer of device 0000:00:02.0 to 64
[   29.238962] ohci_hcd 0000:00:02.0: OHCI Host Controller
[   29.239101] ohci_hcd 0000:00:02.0: new USB bus registered, assigned bus numbe
r 1
[   29.239118] ohci_hcd 0000:00:02.0: irq 16, io mem 0xfebfd000
[   29.264457] forcedeth.c: Reverse Engineered nForce ethernet driver. Version 0
.60.
[   29.297923] usb usb1: configuration #1 chosen from 1 choice
[   29.297954] hub 1-0:1.0: USB hub found
[   29.297965] hub 1-0:1.0: 4 ports detected
[   29.308942] SCSI subsystem initialized
[   29.313900] libata version 2.21 loaded.
[   29.398712] ACPI: PCI Interrupt Link [LUS1] enabled at IRQ 21
[   29.398723] ACPI: PCI Interrupt 0000:00:02.1[B] -> Link [LUS1] -> GSI 21 (lev
el, low) -> IRQ 17
[   29.398735] PCI: Setting latency timer of device 0000:00:02.1 to 64
[   29.398738] ohci_hcd 0000:00:02.1: OHCI Host Controller
[   29.398763] ohci_hcd 0000:00:02.1: new USB bus registered, assigned bus numbe
r 2
[   29.398779] ohci_hcd 0000:00:02.1: irq 17, io mem 0xfebfe000
[   29.456331] usb usb2: configuration #1 chosen from 1 choice
[   29.456361] hub 2-0:1.0: USB hub found
[   29.456371] hub 2-0:1.0: 4 ports detected
[   29.558717] ACPI: PCI Interrupt Link [LUS2] enabled at IRQ 20
[   29.558728] ACPI: PCI Interrupt 0000:00:02.2[C] -> Link [LUS2] -> GSI 20 (lev
el, low) -> IRQ 18
[   29.558739] PCI: Setting latency timer of device 0000:00:02.2 to 64
[   29.558743] ehci_hcd 0000:00:02.2: EHCI Host Controller
[   29.558780] ehci_hcd 0000:00:02.2: new USB bus registered, assigned bus numbe
r 3
[   29.558808] ehci_hcd 0000:00:02.2: debug port 1
[   29.558812] PCI: cache line size of 64 is not supported by device 0000:00:02.
2
[   29.558822] ehci_hcd 0000:00:02.2: irq 18, io mem 0xfebffc00
[   29.561989] 8139too Fast Ethernet driver 0.9.28
[   29.580940] FDC 0 is a post-1991 82077
[   29.701823] usb 1-3: new full speed USB device using ohci_hcd and address 2
[   29.701842] ehci_hcd 0000:00:02.2: USB 2.0 started, EHCI 1.00, driver 10 Dec
2004
[   29.701949] usb usb3: configuration #1 chosen from 1 choice
[   29.701976] hub 3-0:1.0: USB hub found
[   29.701984] hub 3-0:1.0: 8 ports detected
[   29.806164] ACPI: PCI Interrupt Link [LKLN] enabled at IRQ 22
[   29.806169] ACPI: PCI Interrupt 0000:00:05.0[A] -> Link [LKLN] -> GSI 22 (lev
el, low) -> IRQ 16
[   29.806176] PCI: Setting latency timer of device 0000:00:05.0 to 64
[   30.257012] usb 3-5: new high speed USB device using ehci_hcd and address 2
[   30.325342] eth0: forcedeth.c: subsystem: 01043:80a7 bound to 0000:00:05.0
[   30.329973] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[   30.329979] ide: Assuming 33MHz system bus speed for PIO modes; override with
 idebus=xx
[   30.331783] NFORCE3-250: IDE controller at PCI slot 0000:00:08.0
[   30.331864] NFORCE3-250: chipset revision 162
[   30.331867] NFORCE3-250: not 100% native mode: will probe irqs later
[   30.331873] NFORCE3-250: 0000:00:08.0 (rev a2) UDMA133 controller
[   30.331883]     ide0: BM-DMA at 0xffa0-0xffa7, BIOS settings: hda:DMA, hdb:pi
o
[   30.331893]     ide1: BM-DMA at 0xffa8-0xffaf, BIOS settings: hdc:pio, hdd:pi
o
[   30.331901] Probing IDE interface ide0...
[   30.391139] usb 3-5: configuration #1 chosen from 1 choice
[   30.628481] usb 3-6: new high speed USB device using ehci_hcd and address 3
[   31.063930] hda: HL-DT-ST DVDRAM GSA-4167B, ATAPI CD/DVD-ROM drive
[   31.307556] usb 3-6: configuration #1 chosen from 1 choice
[   31.308888] usbcore: registered new interface driver libusual
[   31.313475] Initializing USB Mass Storage driver...
[   31.313959] scsi0 : SCSI emulation for USB Mass Storage devices
[   31.314248] usb-storage: device found at 2
[   31.314250] usb-storage: waiting for device to settle before scanning
[   31.314290] scsi1 : SCSI emulation for USB Mass Storage devices
[   31.314460] usb-storage: device found at 3
[   31.314463] usb-storage: waiting for device to settle before scanning
[   31.314479] usbcore: registered new interface driver usb-storage
[   31.314483] USB Mass Storage support registered.
[   31.400637] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[   31.403602] Probing IDE interface ide1...
[   31.970997] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 19
[   31.971008] ACPI: PCI Interrupt 0000:02:07.0[A] -> Link [LNKB] -> GSI 19 (lev
el, low) -> IRQ 19
[   31.971571] eth1: RealTek RTL8139 at 0xf083ec00, 00:40:f4:a6:80:70, IRQ 19
[   31.971574] eth1:  Identified 8139 chip type 'RTL-8100B/8139D'
[   31.975428] 8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)
[   31.975922] sata_nv 0000:00:0a.0: version 3.4
[   31.976311] ACPI: PCI Interrupt Link [LTID] BIOS reported IRQ 0, using IRQ 21
[   31.976314] ACPI: PCI Interrupt Link [LTID] enabled at IRQ 21
[   31.976318] ACPI: PCI Interrupt 0000:00:0a.0[A] -> Link [LTID] -> GSI 21 (lev
el, low) -> IRQ 17
[   31.976360] PCI: Setting latency timer of device 0000:00:0a.0 to 64
[   31.976399] scsi2 : sata_nv
[   31.976694] scsi3 : sata_nv
[   31.976907] ata1: SATA max UDMA/133 cmd 0x000109f0 ctl 0x00010bf2 bmdma 0x000
1c800 irq 17
[   31.976911] ata2: SATA max UDMA/133 cmd 0x00010970 ctl 0x00010b72 bmdma 0x000
1c808 irq 17
[   31.988287] hda: ATAPI 48X DVD-ROM DVD-R-RAM CD-R/RW drive, 2048kB Cache, UDM
A(33)
[   31.988297] Uniform CD-ROM driver Revision: 3.20
[   32.286087] ata1: SATA link down (SStatus 0 SControl 300)
[   32.597638] ata2: SATA link down (SStatus 0 SControl 300)
[   36.304389] usb-storage: device scan complete
[   36.304506] usb-storage: device scan complete
[   36.305012] scsi 0:0:0:0: Direct-Access     Generic  USB SD Reader    1.00 PQ
: 0 ANSI: 0
[   36.305383] scsi 1:0:0:0: Direct-Access     Sycron   MicroDisk        1.32 PQ
: 0 ANSI: 2
[   36.305534] scsi 0:0:0:1: Direct-Access     Generic  USB CF Reader    1.01 PQ
: 0 ANSI: 0
[   36.308339] scsi 0:0:0:2: Direct-Access     Generic  USB SM Reader    1.02 PQ
: 0 ANSI: 0
[   36.312327] scsi 0:0:0:3: Direct-Access     Generic  USB MS Reader    1.03 PQ
: 0 ANSI: 0
[   36.316337] sd 1:0:0:0: [sda] 7897087 512-byte hardware sectors (4043 MB)
[   36.320309] sd 1:0:0:0: [sda] Write Protect is off
[   36.320314] sd 1:0:0:0: [sda] Mode Sense: 00 00 00 00
[   36.320317] sd 1:0:0:0: [sda] Assuming drive cache: write through
[   36.328318] sd 1:0:0:0: [sda] 7897087 512-byte hardware sectors (4043 MB)
[   36.329097] sd 1:0:0:0: [sda] Write Protect is off
[   36.329100] sd 1:0:0:0: [sda] Mode Sense: 00 00 00 00
[   36.329103] sd 1:0:0:0: [sda] Assuming drive cache: write through
[   36.329109]  sda: sda1 sda2
[   36.556351] sd 1:0:0:0: [sda] Attached SCSI removable disk
[   36.557304] sd 0:0:0:0: [sdb] Attached SCSI removable disk
[   36.558165] sd 0:0:0:1: [sdc] Attached SCSI removable disk
[   36.559041] sd 0:0:0:2: [sdd] Attached SCSI removable disk
[   36.559917] sd 0:0:0:3: [sde] Attached SCSI removable disk
[   36.564014] sd 1:0:0:0: Attached scsi generic sg0 type 0
[   36.564040] sd 0:0:0:0: Attached scsi generic sg1 type 0
[   36.564058] sd 0:0:0:1: Attached scsi generic sg2 type 0
[   36.564078] sd 0:0:0:2: Attached scsi generic sg3 type 0
[   36.564097] sd 0:0:0:3: Attached scsi generic sg4 type 0
[   36.968002] Attempting manual resume
[   36.968006] swsusp: Resume From Partition 8:2
[   36.968008] PM: Checking swsusp image.
[   36.969432] PM: Resume from disk failed.
[   36.987380] kjournald starting.  Commit interval 5 seconds
[   36.987391] EXT3-fs: mounted filesystem with ordered data mode.
[   44.802826] Linux agpgart interface v0.102 (c) Dave Jones
[   44.847098] agpgart: Detected AGP bridge 0
[   44.847114] agpgart: Setting up Nforce3 AGP.
[   44.847118] agpgart: aperture base > 4G
[   44.946362] i2c-adapter i2c-0: nForce2 SMBus adapter at 0x5000
[   44.946384] i2c-adapter i2c-1: nForce2 SMBus adapter at 0x5040
[   45.237197] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   45.251081] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   46.344806] input: PC Speaker as /class/input/input2
[   46.642318] Linux video capture interface: v2.00
[   46.778366] cx2388x v4l2 driver version 0.0.6 loaded
[   46.779463] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 18
[   46.779474] ACPI: PCI Interrupt 0000:02:09.0[A] -> Link [LNKD] -> GSI 18 (lev
el, low) -> IRQ 20
[   46.779530] cx88[0]: Your board isn't known (yet) to the driver.  You can
[   46.779531] cx88[0]: try to pick one of the existing card configs via
[   46.779533] cx88[0]: card=<n> insmod option.  Updating to the latest
[   46.779535] cx88[0]: version might help as well.
[   46.779537] cx88[0]: Here is a list of valid choices for the card=<n> insmod
option:
[   46.779540] cx88[0]:    card=0 -> UNKNOWN/GENERIC
[   46.779542] cx88[0]:    card=1 -> Hauppauge WinTV 34xxx models
[   46.779545] cx88[0]:    card=2 -> GDI Black Gold
[   46.779547] cx88[0]:    card=3 -> PixelView
[   46.779549] cx88[0]:    card=4 -> ATI TV Wonder Pro
[   46.779551] cx88[0]:    card=5 -> Leadtek Winfast 2000XP Expert
[   46.779553] cx88[0]:    card=6 -> AverTV Studio 303 (M126)
[   46.779556] cx88[0]:    card=7 -> MSI TV-@nywhere Master
[   46.779558] cx88[0]:    card=8 -> Leadtek Winfast DV2000
[   46.779560] cx88[0]:    card=9 -> Leadtek PVR 2000
[   46.779562] cx88[0]:    card=10 -> IODATA GV-VCP3/PCI
[   46.779564] cx88[0]:    card=11 -> Prolink PlayTV PVR
[   46.779567] cx88[0]:    card=12 -> ASUS PVR-416
[   46.779569] cx88[0]:    card=13 -> MSI TV-@nywhere
[   46.779571] cx88[0]:    card=14 -> KWorld/VStream XPert DVB-T
[   46.779573] cx88[0]:    card=15 -> DViCO FusionHDTV DVB-T1
[   46.779576] cx88[0]:    card=16 -> KWorld LTV883RF
[   46.779578] cx88[0]:    card=17 -> DViCO FusionHDTV 3 Gold-Q
[   46.779580] cx88[0]:    card=18 -> Hauppauge Nova-T DVB-T
[   46.779583] cx88[0]:    card=19 -> Conexant DVB-T reference design
[   46.779585] cx88[0]:    card=20 -> Provideo PV259
[   46.779587] cx88[0]:    card=21 -> DViCO FusionHDTV DVB-T Plus
[   46.779590] cx88[0]:    card=22 -> pcHDTV HD3000 HDTV
[   46.779592] cx88[0]:    card=23 -> digitalnow DNTV Live! DVB-T
[   46.779594] cx88[0]:    card=24 -> Hauppauge WinTV 28xxx (Roslyn) models
[   46.779597] cx88[0]:    card=25 -> Digital-Logic MICROSPACE Entertainment Cen
ter (MEC)
[   46.779600] cx88[0]:    card=26 -> IODATA GV/BCTV7E
[   46.779602] cx88[0]:    card=27 -> PixelView PlayTV Ultra Pro (Stereo)
[   46.779604] cx88[0]:    card=28 -> DViCO FusionHDTV 3 Gold-T
[   46.779607] cx88[0]:    card=29 -> ADS Tech Instant TV DVB-T PCI
[   46.779609] cx88[0]:    card=30 -> TerraTec Cinergy 1400 DVB-T
[   46.779612] cx88[0]:    card=31 -> DViCO FusionHDTV 5 Gold
[   46.779614] cx88[0]:    card=32 -> AverMedia UltraTV Media Center PCI 550
[   46.779617] cx88[0]:    card=33 -> Kworld V-Stream Xpert DVD
[   46.779619] cx88[0]:    card=34 -> ATI HDTV Wonder
[   46.779621] cx88[0]:    card=35 -> WinFast DTV1000-T
[   46.779623] cx88[0]:    card=36 -> AVerTV 303 (M126)
[   46.779626] cx88[0]:    card=37 -> Hauppauge Nova-S-Plus DVB-S
[   46.779628] cx88[0]:    card=38 -> Hauppauge Nova-SE2 DVB-S
[   46.779630] cx88[0]:    card=39 -> KWorld DVB-S 100
[   46.779633] cx88[0]:    card=40 -> Hauppauge WinTV-HVR1100 DVB-T/Hybrid
[   46.779635] cx88[0]:    card=41 -> Hauppauge WinTV-HVR1100 DVB-T/Hybrid (Low
Profile)
[   46.779638] cx88[0]:    card=42 -> digitalnow DNTV Live! DVB-T Pro
[   46.779641] cx88[0]:    card=43 -> KWorld/VStream XPert DVB-T with cx22702
[   46.779643] cx88[0]:    card=44 -> DViCO FusionHDTV DVB-T Dual Digital
[   46.779646] cx88[0]:    card=45 -> KWorld HardwareMpegTV XPert
[   46.779648] cx88[0]:    card=46 -> DViCO FusionHDTV DVB-T Hybrid
[   46.779651] cx88[0]:    card=47 -> pcHDTV HD5500 HDTV
[   46.779653] cx88[0]:    card=48 -> Kworld MCE 200 Deluxe
[   46.779655] cx88[0]:    card=49 -> PixelView PlayTV P7000
[   46.779657] cx88[0]:    card=50 -> NPG Tech Real TV FM Top 10
[   46.779660] cx88[0]:    card=51 -> WinFast DTV2000 H
[   46.779662] cx88[0]:    card=52 -> Geniatech DVB-S
[   46.779664] cx88[0]:    card=53 -> Hauppauge WinTV-HVR3000 TriMode Analog/DVB
-S/DVB-T
[   46.779667] cx88[0]:    card=54 -> Norwood Micro TV Tuner
[   46.779669] cx88[0]:    card=55 -> Shenzhen Tungsten Ages Tech TE-DTV-250 / S
wann OEM
[   46.779672] cx88[0]:    card=56 -> Hauppauge WinTV-HVR1300 DVB-T/Hybrid MPEG
Encoder
[   46.779676] CORE cx88[0]: subsystem: 107d:6f18, board: UNKNOWN/GENERIC [card=
0,autodetected]
[   46.779680] TV tuner -1 at 0x1fe, Radio tuner -1 at 0x1fe
[   46.809697] ACPI: PCI Interrupt Link [LAUI] enabled at IRQ 20
[   46.809703] ACPI: PCI Interrupt 0000:00:06.0[A] -> Link [LAUI] -> GSI 20 (lev
el, low) -> IRQ 18
[   46.809723] PCI: Setting latency timer of device 0000:00:06.0 to 64
[   46.923511] cx88[0]/0: found at 0000:02:09.0, rev: 5, irq: 20, latency: 64, m
mio: 0xfd000000
[   46.943483] tuner 2-0061: chip found @ 0xc2 (cx88[0])
[   46.950221] cx88[0]/0: registered device video0 [v4l2]
[   46.950252] cx88[0]/0: registered device vbi0
[   46.950267] tuner 2-0061: tuner type not set
[   47.030767] input: ImPS/2 Generic Wheel Mouse as /class/input/input3
[   47.132688] intel8x0_measure_ac97_clock: measured 54702 usecs
[   47.132692] intel8x0: clocking to 46888
[   48.025662] lp: driver loaded but no devices found
[   48.062220] Adding 522104k swap on /dev/sda2.  Priority:-1 extents:1 across:5
22104k
[   48.132039] EXT3 FS on sda1, internal journal
[   49.506425] No dock devices found.
[   49.675358] input: Power Button (FF) as /class/input/input4
[   49.679814] ACPI: Power Button (FF) [PWRF]
[   49.722388] input: Power Button (CM) as /class/input/input5
[   49.726805] ACPI: Power Button (CM) [PWRB]
[   49.923809] powernow-k8: Power state transitions not supported
[   50.478162] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[   50.478167] apm: overridden by ACPI.
[   50.915623] eth0: no link during initialization.
[   50.975047] Failure registering capabilities with primary security module.
[   50.986616] eth1: link up, 100Mbps, full-duplex, lpa 0x45E1
[   51.779202] [drm] Initialized drm 1.1.0 20060810
[   51.790311] ACPI: PCI Interrupt Link [LNKE] enabled at IRQ 17
[   51.790323] ACPI: PCI Interrupt 0000:01:00.0[A] -> Link [LNKE] -> GSI 17 (lev                                            el, low) -> IRQ 21
[   51.793166] [drm] Initialized radeon 1.27.0 20060524 on minor 0
[   68.567017] [drm:radeon_cp_init] *ERROR* radeon_cp_init called without lock h                                            eld
[   68.567057] [drm:drm_unlock] *ERROR* Process 5331 using kernel context 0
[   81.802914] NET: Registered protocol family 17
[   92.926105] NET: Registered protocol family 10
[   92.926295] lo: Disabled Privacy Extensions
[   92.926536] ADDRCONF(NETDEV_UP): eth0: link is not ready
[  103.787027] eth1: no IPv6 routers present


> 
00:00.0 Host bridge: nVidia Corporation nForce3 250Gb Host Bridge (rev a1)
        Subsystem: ASUSTeK Computer Inc. K8N-E
        Flags: bus master, 66MHz, fast devsel, latency 0
        Memory at f0000000 (32-bit, prefetchable) [size=128M]
        Capabilities: [44] HyperTransport: Slave or Primary Interface
        Capabilities: [c0] AGP version 3.0

00:01.0 ISA bridge: nVidia Corporation nForce3 250Gb LPC Bridge (rev a2)
        Subsystem: ASUSTeK Computer Inc. K8N-E
        Flags: bus master, 66MHz, fast devsel, latency 0

00:01.1 SMBus: nVidia Corporation nForce 250Gb PCI System Management (rev a1)
        Subsystem: ASUSTeK Computer Inc. K8N-E
        Flags: 66MHz, fast devsel
        I/O ports at 5080 [size=32]
        I/O ports at 5000 [size=64]
        I/O ports at 5040 [size=64]
        Capabilities: [44] Power Management version 2

00:02.0 USB Controller: nVidia Corporation CK8S USB Controller (rev a1) (prog-if 10 [OHCI])
        Subsystem: ASUSTeK Computer Inc. K8N-E
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 16
        Memory at febfd000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: [44] Power Management version 2

00:02.1 USB Controller: nVidia Corporation CK8S USB Controller (rev a1) (prog-if 10 [OHCI])
        Subsystem: ASUSTeK Computer Inc. K8N-E
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 17
        Memory at febfe000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: [44] Power Management version 2

00:02.2 USB Controller: nVidia Corporation nForce3 EHCI USB 2.0 Controller (rev a2) (prog-if 20 [EHCI])
        Subsystem: ASUSTeK Computer Inc. K8N-E
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 18
        Memory at febffc00 (32-bit, non-prefetchable) [size=256]
        Capabilities: [44] Debug port
        Capabilities: [80] Power Management version 2

00:05.0 Bridge: nVidia Corporation CK8S Ethernet Controller (rev a2)
        Subsystem: ASUSTeK Computer Inc. K8N-E
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 16
        Memory at febfc000 (32-bit, non-prefetchable) [size=4K]
        I/O ports at ec00 [size=8]
        Capabilities: [44] Power Management version 2

00:06.0 Multimedia audio controller: nVidia Corporation nForce3 250Gb AC'97 Audio Controller (rev a1)
        Subsystem: ASUSTeK Computer Inc. Unknown device 812a
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 18
        I/O ports at e800 [size=256]
        I/O ports at e400 [size=128]
        Memory at febfb000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: [44] Power Management version 2

00:08.0 IDE interface: nVidia Corporation CK8S Parallel ATA Controller (v2.5) (rev a2) (prog-if 8a [Master SecP PriP])
        Subsystem: ASUSTeK Computer Inc. K8N-E
        Flags: bus master, 66MHz, fast devsel, latency 0
        [virtual] Memory at 000001f0 (32-bit, non-prefetchable) [disabled] [size=8]
        [virtual] Memory at 000003f0 (type 3, non-prefetchable) [disabled] [size=1]
        [virtual] Memory at 00000170 (32-bit, non-prefetchable) [disabled] [size=8]
        [virtual] Memory at 00000370 (type 3, non-prefetchable) [disabled] [size=1]
        I/O ports at ffa0 [size=16]
        Capabilities: [44] Power Management version 2

00:0a.0 IDE interface: nVidia Corporation CK8S Serial ATA Controller (v2.5) (rev a2) (prog-if 85 [Master SecO PriO])
        Subsystem: ASUSTeK Computer Inc. K8N-E
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 17
        I/O ports at 09f0 [size=8]
        I/O ports at 0bf0 [size=4]
        I/O ports at 0970 [size=8]
        I/O ports at 0b70 [size=4]
        I/O ports at c800 [size=16]
        I/O ports at c400 [size=128]
        Capabilities: [44] Power Management version 2

00:0b.0 PCI bridge: nVidia Corporation nForce3 250Gb AGP Host to PCI Bridge (rev a2) (prog-if 00 [Normal decode])
        Flags: bus master, 66MHz, medium devsel, latency 16
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=10
        I/O behind bridge: 0000a000-0000afff
        Memory behind bridge: fc900000-fc9fffff
        Prefetchable memory behind bridge: ac800000-ec7fffff

00:0e.0 PCI bridge: nVidia Corporation nForce3 250Gb PCI-to-PCI Bridge (rev a2) (prog-if 00 [Normal decode])
        Flags: bus master, 66MHz, fast devsel, latency 0
        Bus: primary=00, secondary=02, subordinate=02, sec-latency=128
        I/O behind bridge: 0000b000-0000bfff
        Memory behind bridge: fca00000-feafffff

00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
        Flags: fast devsel
        Capabilities: [80] HyperTransport: Host or Secondary Interface

00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
        Flags: fast devsel

00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
        Flags: fast devsel

00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
        Flags: fast devsel

01:00.0 VGA compatible controller: ATI Technologies Inc RV350 AS [Radeon 9550] (prog-if 00 [VGA])
        Subsystem: ASUSTeK Computer Inc. A9550GE/TD
        Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 21
        Memory at d0000000 (32-bit, prefetchable) [size=256M]
        I/O ports at a800 [size=256]
        Memory at fc9f0000 (32-bit, non-prefetchable) [size=64K]
        Expansion ROM at fc9c0000 [disabled] [size=128K]
        Capabilities: [58] AGP version 3.0
        Capabilities: [50] Power Management version 2

01:00.1 Display controller: ATI Technologies Inc RV350 AS [Radeon 9550] (Secondary)
        Subsystem: ASUSTeK Computer Inc. A9550GE/TD (Secondary)
        Flags: bus master, 66MHz, medium devsel, latency 64
        Memory at c0000000 (32-bit, prefetchable) [size=256M]
        Memory at fc9e0000 (32-bit, non-prefetchable) [size=64K]
        Capabilities: [50] Power Management version 2

02:07.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
        Subsystem: Realtek Semiconductor Co., Ltd. RT8139
        Flags: bus master, medium devsel, latency 64, IRQ 19
        I/O ports at b800 [size=256]
        Memory at feaffc00 (32-bit, non-prefetchable) [size=256]
        Capabilities: [50] Power Management version 2

02:09.0 Multimedia video controller: Conexant CX23880/1/2/3 PCI Video and Audio Decoder (rev 05)
        Subsystem: LeadTek Research Inc. Unknown device 6f18
        Flags: bus master, medium devsel, latency 64, IRQ 20
        Memory at fd000000 (32-bit, non-prefetchable) [size=16M]
        Capabilities: [44] Vital Product Data
        Capabilities: [4c] Power Management version 2



/etc/modules.conf
> 
cx88xx card=5 tuner=5
cx8800 video_nr=0 radio_nr=0


tvtime-scanner
> Reading configuration from /etc/tvtime/tvtime.xml
Reading configuration from /root/.tvtime/tvtime.xml
Scanning using TV standard PAL.
videoinput: Can't get tuner info: Invalid argument
videoinput: Can't get tuner info: Invalid argument

    No tuner found on input 0.  If you have a tuner, please
    select a different input using --input=<num>.


---

### Post by asbjorn on 2007-12-19
What version of Ubuntu are you using?
On my setup, I don't use the "old" config file.
Try the following
edit /etc/modprobe.d/options
And add your configs there
cx88xx card=5 tuner=5
cx8800 video_nr=0 radio_nr=0

(I'm not sure about the second line. try with and without it...)
/Martin

---

### Post by blueyez on 2007-12-20
old config file ?
what tv tuner you have ?
i use 7.10

i'll try your way.

---

### Post by alphaniner on 2007-12-21
I have the same TV card (although it is several years old) and the lines from dmesg relating to it are:

```
[   12.376000] Linux video capture interface: v2.00
[   12.424000] hdb: ATAPI 40X DVD-ROM DVD-R-RAM CD-R/RW drive, 2048kB Cache, UDMA(66)
[   12.464000] cx2388x v4l2 driver version 0.0.6 loaded
[   12.468000] ACPI: PCI Interrupt 0000:02:01.0[A] -> GSI 21 (level, low) -> IRQ 19
[   12.468000] CORE cx88[0]: subsystem: 107d:6613, board: Leadtek Winfast 2000XP Expert [card=5,autodetected]
[   12.468000] TV tuner 44 at 0x1fe, Radio tuner -1 at 0x1fe
[   12.576000] ACPI: PCI Interrupt 0000:00:14.2[A] -> GSI 16 (level, low) -> IRQ 16
[   12.616000] cx88[0]: Leadtek Winfast 2000XP Expert config: tuner=43, eeprom[0]=0x01
[   12.616000] input: cx88 IR (Leadtek Winfast 2000XP as /class/input/input6
[   12.616000] cx88[0]/0: found at 0000:02:01.0, rev: 5, irq: 19, latency: 64, mmio: 0xfb000000
[   12.632000] tuner 1-0043: chip found @ 0x86 (cx88[0])
[   12.632000] tda9887 1-0043: tda988[5/6/7] found @ 0x43 (tuner)
[   12.636000] tuner 1-0060: All bytes are equal. It is not a TEA5767
[   12.636000] tuner 1-0060: chip found @ 0xc0 (cx88[0])
[   12.636000] tuner 1-0060: type set to 43 (Philips NTSC MK3 (FM1236MK3 or FM1236/F))
[   12.636000] tuner 1-0060: type set to 43 (Philips NTSC MK3 (FM1236MK3 or FM1236/F))
[   12.640000] cx88[0]/0: registered device video0 [v4l2]
[   12.640000] cx88[0]/0: registered device vbi0
[   12.640000] cx88[0]/0: registered device radio0
```

On another thread ([[COLOR="Blue"]Leadtek Winfast TV2000 XP Expert[/COLOR]]("http://ubuntuforums.org/showthread.php?t=20003")) someone managed to get the card working, but was unsure exactly *how*.  I followed his suggestions and was unsuccessful.

```
sudo modprobe -v cx88xx
```

returns absolutely nothing before and after following his advice.  As for the modifications to /etc/modprobe.d/options suggested on this thread, I tried that then when I ran ```
sudo modprobe -v cx88xx
``` it responded with

```
WARNING: /etc/modprobe.d/options line 8: ignoring bad line starting with 'cx88xx'
WARNING: /etc/modprobe.d/options line 9: ignoring bad line starting with 'cx8800'

```

I have done quite a bit of searching on these forums and elsewhere and while some people have gotten the card to work, it seems that they never really know how.

The strangest thing is, after I tried all this, I ran tvtime-scanner:

```
eading configuration from /etc/tvtime/tvtime.xml
Reading configuration from /home/alphaniner/.tvtime/tvtime.xml
Scanning using TV standard NTSC.
Scanning from  44.00 MHz to 958.00 MHz.
Found a channel at  54.75 MHz (53.00 - 56.25 MHz), adding to channel list.
I/O warning : failed to load external entity "/home/alphaniner/.tvtime/stationlist.xml"
station: No station file found, creating a new one.
Found a channel at  60.50 MHz (59.00 - 62.00 MHz), adding to channel list.
Found a channel at  66.50 MHz (65.00 - 68.00 MHz), adding to channel list.
...
Found a channel at 492.50 MHz (491.00 - 494.00 MHz), adding to channel list.
Found a channel at 498.50 MHz (497.00 - 500.00 MHz), adding to channel list.
```

But when I try to run TVTime from the Applications menu I still get the same result as I did right after I installed it: a brief flash on the screen about the shape and size of the player in Windows, then it's gone, including the application 'button' on the panel.

---

### Post by alphaniner on 2007-12-22
I found some more info in ~/.xsession-errors but I don't really know what to make of it:

```
Running tvtime 1.0.2.
Reading configuration from /etc/tvtime/tvtime.xml
Reading configuration from /home/alphaniner/.tvtime/tvtime.xml
xvoutput: No XVIDEO port found which supports YUY2 images.

*** tvtime requires hardware YUY2 overlay support from your video card
*** driver.  If you are using an older NVIDIA card (TNT2), then
*** this capability is only available with their binary drivers.
*** For some ATI cards, this feature may be found in the experimental
*** GATOS drivers: http://gatos.souceforge.net/
*** If unsure, please check with your distribution to see if your
*** X driver supports hardware overlay surfaces.


(gecko:6068): Gtk-CRITICAL **: gtk_text_buffer_get_insert: assertion `GTK_IS_TEXT_BUFFER (buffer)' failed

(gecko:6068): Gtk-CRITICAL **: gtk_text_buffer_get_iter_at_mark: assertion `GTK_IS_TEXT_MARK (mark)' failed

(gecko:6068): Gtk-CRITICAL **: _gtk_text_layout_get_block_cursor: assertion `layout != NULL' failed

(gecko:6068): Gtk-CRITICAL **: gtk_text_layout_get_cursor_locations: assertion `layout != NULL' failed

(gecko:6068): Gdk-CRITICAL **: gdk_window_invalidate_rect: assertion `window != NULL' failed

(gecko:6068): Gdk-CRITICAL **: gdk_window_invalidate_rect: assertion `window != NULL' failed

(gecko:6068): Gtk-CRITICAL **: gtk_text_buffer_get_insert: assertion `GTK_IS_TEXT_BUFFER (buffer)' failed

(gecko:6068): Gtk-CRITICAL **: gtk_text_buffer_get_iter_at_mark: assertion `GTK_IS_TEXT_MARK (mark)' failed

(gecko:6068): Gtk-CRITICAL **: _gtk_text_layout_get_block_cursor: assertion `layout != NULL' failed

(gecko:6068): Gtk-CRITICAL **: gtk_text_layout_get_cursor_locations: assertion `layout != NULL' failed

(gecko:6068): Gdk-CRITICAL **: gdk_window_invalidate_rect: assertion `window != NULL' failed

(gecko:6068): Gdk-CRITICAL **: gdk_window_invalidate_rect: assertion `window != NULL' failed
Window manager warning: Log level 8: gtk_menu_shell_insert: assertion `GTK_IS_MENU_ITEM (child)' failed
Window manager warning: Log level 8: gtk_widget_show: assertion `GTK_IS_WIDGET (widget)' failed
Running tvtime 1.0.2.
Reading configuration from /etc/tvtime/tvtime.xml
Reading configuration from /home/alphaniner/.tvtime/tvtime.xml
xvoutput: No XVIDEO port found which supports YUY2 images.

*** tvtime requires hardware YUY2 overlay support from your video card
*** driver.  If you are using an older NVIDIA card (TNT2), then
*** this capability is only available with their binary drivers.
*** For some ATI cards, this feature may be found in the experimental
*** GATOS drivers: http://gatos.souceforge.net/
*** If unsure, please check with your distribution to see if your
*** X driver supports hardware overlay surfaces.

Window manager warning: Log level 8: gtk_menu_shell_insert: assertion `GTK_IS_MENU_ITEM (child)' failed
Window manager warning: Log level 8: gtk_widget_show: assertion `GTK_IS_WIDGET (widget)' failed
Window manager warning: Log level 8: gtk_menu_shell_insert: assertion `GTK_IS_MENU_ITEM (child)' failed
Window manager warning: Log level 8: gtk_widget_show: assertion `GTK_IS_WIDGET (widget)' failed
checking for valid crashreport now
Window manager warning: Log level 8: gtk_menu_shell_insert: assertion `GTK_IS_MENU_ITEM (child)' failed
Window manager warning: Log level 8: gtk_widget_show: assertion `GTK_IS_WIDGET (widget)' failed
keybinding-properties-Message: title: Sound
keybinding-properties-Message: title: Desktop
keybinding-properties-Message: title: Desktop
keybinding-properties-Message: title: Window Management
Window manager warning: Log level 8: gtk_menu_shell_insert: assertion `GTK_IS_MENU_ITEM (child)' failed
Window manager warning: Log level 8: gtk_widget_show: assertion `GTK_IS_WIDGET (widget)' failed
keybinding-properties-Message: title: Sound
keybinding-properties-Message: title: Desktop
keybinding-properties-Message: title: Desktop
keybinding-properties-Message: title: Window Management
Running tvtime 1.0.2.
Reading configuration from /etc/tvtime/tvtime.xml
Reading configuration from /home/alphaniner/.tvtime/tvtime.xml
xvoutput: No XVIDEO port found which supports YUY2 images.

*** tvtime requires hardware YUY2 overlay support from your video card
*** driver.  If you are using an older NVIDIA card (TNT2), then
*** this capability is only available with their binary drivers.
*** For some ATI cards, this feature may be found in the experimental
*** GATOS drivers: http://gatos.souceforge.net/
*** If unsure, please check with your distribution to see if your
*** X driver supports hardware overlay surfaces.

```

---

### Post by rvickers on 2007-12-28
Just had the same thing happen to me after playing around with VirtialBox. Reloaded Gutsy and TvTime and it's ok now. An extreme solution but that's the only way I could get TvTime back.

---

### Post by LeDechaine on 2008-02-03
This card automatically worked for me with 7.10, but don't even expect to have any sound coming from it. You may be masochist enough to start messing with "modprobe" and try all the cards and all the modules and all the tuners, but if you consider that "time is money", buying another TV card or even a freaking TV will actually make you **SAVE**.

---

### Post by LeDechaine on 2008-03-18
(Finally, my problem may not be the card but the Audigy 2 sound card driver which is useless for this TV card, because the AUX Input of the sound card doesn't works, and this is where the TV Card must be plugged to output sound.)

Waiting for a better driver..

---

### Post by TransplantedCanuck on 2008-03-21
After 3 hours of trying, googling, trolling through forums, I've decided to give up on getting this card working on my own. I am at exactly the same point as the OP and have no clue how to procede from here.

I'm a total ubuntu noob, but after my battles with: sound, thunderbird and now the tv card, I'm starting to learn something. 


SO, does anyone have a step for step guide on how to ACTUALLY get the card to work?

---

