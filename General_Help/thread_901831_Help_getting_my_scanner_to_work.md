---
title: "Help getting my scanner to work"
date: 2008-08-26
forum: General Help
---

### Post by dagoth_pie on 2008-08-26
I got given this old scanner and printer by a friend, i got the printer working easy (easier than years ago when i last got one to work on windows 98...) but no luck with the scanner, the printout from running lsusb is:
 "Bus 001 Device 004: ID 04a5:2060 Acer Peripherals Inc. (now BenQ Corp.) Prisa 620U+/640U"

When I run xsane I get a error saying 
"failed to open device "snapscan:libusb:001:004':invalid argument"

Andy halp would be appreciated

---

### Post by Crafty Kisses on 2008-08-26
Not sure if your scanner is supported. 

For scanners you can look through this list > [http://www.sane-project.org/sane-mfgs.html](http://www.sane-project.org/sane-mfgs.html)

[http://www.linuxfoundation.org/en/OpenPrinting/Database/SuggestedPrinters](http://www.linuxfoundation.org/en/OpenPrinting/Database/SuggestedPrinters)
[http://www.linuxfoundation.org/en/OpenPrinting/Database/LinuxSupportByPrinterVendors](http://www.linuxfoundation.org/en/OpenPrinting/Database/LinuxSupportByPrinterVendors)

---

### Post by dagoth_pie on 2008-08-26
It claims to be, I was thinking it might have something to do with the usb setup, but i dont know enough to know where to start looking for errors

---

### Post by Crafty Kisses on 2008-08-26
Post results of > dmesg

---

### Post by dagoth_pie on 2008-08-26
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.24-19-generic (buildd@terranova) (gcc version 4.2.3 (Ubuntu 4.2.3-2ubuntu7)) #1 SMP Wed Aug 20 22:56:21 UTC 2008 (Ubuntu 2.6.24-19.41-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000002fff0000 (usable)
[    0.000000]  BIOS-e820: 000000002fff0000 - 000000002fff8000 (ACPI data)
[    0.000000]  BIOS-e820: 000000002fff8000 - 0000000030000000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000ffff0000 - 0000000100000000 (reserved)
[    0.000000] 0MB HIGHMEM available.
[    0.000000] 767MB LOWMEM available.
[    0.000000] found SMP MP-table at 000fb110
[    0.000000] Entering add_active_range(0, 0, 196592) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   196592
[    0.000000]   HighMem    196592 ->   196592
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   196592
[    0.000000] On node 0 totalpages: 196592
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 1503 pages used for memmap
[    0.000000]   Normal zone: 190993 pages, LIFO batch:31
[    0.000000]   HighMem zone: 0 pages used for memmap
[    0.000000]   Movable zone: 0 pages used for memmap
[    0.000000] DMI 2.3 present.
[    0.000000] ACPI: RSDP signature @ 0xC00FC590 checksum 0
[    0.000000] ACPI: RSDP 000FC590, 0014 (r0 AMI   )
[    0.000000] ACPI: RSDT 2FFF0000, 002C (r1 AMIINT                10 MSFT       99)
[    0.000000] ACPI: FACP 2FFF0030, 0074 (r1 AMIINT                11 MSFT       99)
[    0.000000] ACPI: DSDT 2FFF0110, 2F9D (r1    VIA APOLLO-P     1000 MSFT  100000B)
[    0.000000] ACPI: FACS 2FFF8000, 0040
[    0.000000] ACPI: APIC 2FFF00B0, 005C (r1 AMIINT                 9 MSFT       99)
[    0.000000] ACPI: PM-Timer IO Port: 0x808
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] Processor #0 6:8 APIC version 17
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
[    0.000000] Processor #1 6:8 APIC version 17
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 17, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 11 global_irq 11 low level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ11 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] Allocating PCI resources starting at 40000000 (gap: 30000000:cec00000)
[    0.000000] swsusp: Registered nosave memory region: 000000000009f000 - 00000000000a0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000a0000 - 00000000000f0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000f0000 - 0000000000100000
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 195057
[    0.000000] Kernel command line: root=UUID=466ff370-5871-41f4-b630-33c12804ebbf ro quiet splash
[    0.000000] mapped APIC to ffffb000 (fee00000)
[    0.000000] mapped IOAPIC to ffffa000 (fec00000)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] Detected 996.629 MHz processor.
[   34.295335] Console: colour VGA+ 80x25
[   34.295348] console [tty0] enabled
[   34.296587] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[   34.300046] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[   34.379051] Memory: 767364k/786368k available (2177k kernel code, 18428k reserved, 1006k data, 368k init, 0k highmem)
[   34.379070] virtual kernel memory layout:
[   34.379073]     fixmap  : 0xfff4b000 - 0xfffff000   ( 720 kB)
[   34.379076]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   34.379079]     vmalloc : 0xf0800000 - 0xff7fe000   ( 239 MB)
[   34.379082]     lowmem  : 0xc0000000 - 0xefff0000   ( 767 MB)
[   34.379084]       .init : 0xc0421000 - 0xc047d000   ( 368 kB)
[   34.379087]       .data : 0xc03204c4 - 0xc041bdc4   (1006 kB)
[   34.379090]       .text : 0xc0100000 - 0xc03204c4   (2177 kB)
[   34.379097] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   34.379177] SLUB: Genslabs=11, HWalign=32, Order=0-1, MinObjects=4, CPUs=2, Nodes=1
[   34.459174] Calibrating delay using timer specific routine.. 1995.51 BogoMIPS (lpj=3991030)
[   34.459227] Security Framework initialized
[   34.459244] SELinux:  Disabled at boot.
[   34.459274] AppArmor: AppArmor initialized
[   34.459282] Failure registering capabilities with primary security module.
[   34.459300] Mount-cache hash table entries: 512
[   34.459543] Initializing cgroup subsys ns
[   34.459552] Initializing cgroup subsys cpuacct
[   34.459571] CPU: After generic identify, caps: 0383fbff 00000000 00000000 00000000 00000000 00000000 00000000 00000000
[   34.459594] CPU: L1 I cache: 16K, L1 D cache: 16K
[   34.459599] CPU: L2 cache: 256K
[   34.459606] CPU: After all inits, caps: 0383fbff 00000000 00000000 00000040 00000000 00000000 00000000 00000000
[   34.459624] Compat vDSO mapped to ffffe000.
[   34.459655] Checking 'hlt' instruction... OK.
[   34.475724] SMP alternatives: switching to UP code
[   34.478816] Early unpacking initramfs... done
[   35.195879] ACPI: Core revision 20070126
[   35.196088] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[   35.199669] CPU0: Intel Pentium III (Coppermine) stepping 0a
[   35.199721] SMP alternatives: switching to SMP code
[   35.200689] Booting processor 1/1 eip 3000
[   35.211071] Initializing CPU#1
[   35.290772] Calibrating delay using timer specific routine.. 1993.22 BogoMIPS (lpj=3986449)
[   35.290786] CPU: After generic identify, caps: 0383fbff 00000000 00000000 00000000 00000000 00000000 00000000 00000000
[   35.290805] CPU: L1 I cache: 16K, L1 D cache: 16K
[   35.290809] CPU: L2 cache: 256K
[   35.290816] CPU: After all inits, caps: 0383fbff 00000000 00000000 00000040 00000000 00000000 00000000 00000000
[   35.291251] CPU1: Intel Pentium III (Coppermine) stepping 0a
[   35.291297] Total of 2 processors activated (3988.73 BogoMIPS).
[   35.292062] ENABLING IO-APIC IRQs
[   35.292397] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[   35.439011] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
[   35.459048] Brought up 2 CPUs
[   35.459164] CPU0 attaching sched-domain:
[   35.459171]  domain 0: span 03
[   35.459175]   groups: 01 02
[   35.459183] CPU1 attaching sched-domain:
[   35.459187]  domain 0: span 03
[   35.459191]   groups: 02 01
[   35.459757] net_namespace: 64 bytes
[   35.459780] Booting paravirtualized kernel on bare hardware
[   35.461009] Time: 23:28:39  Date: 08/25/08
[   35.461095] NET: Registered protocol family 16
[   35.461645] EISA bus registered
[   35.461659] ACPI: bus type pci registered
[   35.464459] PCI: PCI BIOS revision 2.10 entry at 0xfdb01, last bus=1
[   35.464465] PCI: Using configuration type 1
[   35.464500] Setting up standard PCI resources
[   35.468235] mtrr: your CPUs had inconsistent variable MTRR settings
[   35.468241] mtrr: probably your BIOS does not setup all CPUs.
[   35.468245] mtrr: corrected configuration.
[   35.470605] ACPI: EC: Look up EC in DSDT
[   35.478097] ACPI: Interpreter enabled
[   35.478107] ACPI: (supports S0 S1 S4 S5)
[   35.478137] ACPI: Using IOAPIC for interrupt routing
[   35.485457] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   35.485890] PCI quirk: region 0c00-0c7f claimed by vt82c686 HW-mon
[   35.485898] PCI quirk: region 0400-040f claimed by vt82c686 SMB
[   35.486198] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   35.488804] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
[   35.489002] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 *9 10 11 12 14 15)
[   35.489189] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 9 *10 11 12 14 15)
[   35.489377] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 9 10 11 *12 14 15)
[   35.489619] ACPI: Power Resource [URP1] (off)
[   35.489680] ACPI: Power Resource [URP2] (off)
[   35.489740] ACPI: Power Resource [FDDP] (off)
[   35.489800] ACPI: Power Resource [LPTP] (off)
[   35.489925] Linux Plug and Play Support v0.97 (c) Adam Belay
[   35.490006] pnp: PnP ACPI init
[   35.490029] ACPI: bus type pnp registered
[   35.494384] pnp: PnP ACPI: found 10 devices
[   35.494393] ACPI: ACPI bus type pnp unregistered
[   35.494404] PnPBIOS: Disabled by ACPI PNP
[   35.495045] PCI: Using ACPI for IRQ routing
[   35.495054] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   35.526709] NET: Registered protocol family 8
[   35.526715] NET: Registered protocol family 20
[   35.526906] AppArmor: AppArmor Filesystem Enabled
[   35.530686] Time: tsc clocksource has been installed.
[   35.569799] PCI: Bridge: 0000:00:01.0
[   35.569806]   IO window: 9000-9fff
[   35.569814]   MEM window: dde00000-dfefffff
[   35.569820]   PREFETCH window: cdc00000-ddcfffff
[   35.569842] PCI: Setting latency timer of device 0000:00:01.0 to 64
[   35.569873] NET: Registered protocol family 2
[   35.606842] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[   35.607573] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[   35.613486] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[   35.616540] TCP: Hash tables configured (established 131072 bind 65536)
[   35.616552] TCP reno registered
[   35.627093] checking if image is initramfs...<7>Switched to high resolution mode on CPU 1
[   36.070447] Switched to high resolution mode on CPU 0
[   36.227912]  it is
[   36.970042] Freeing initrd memory: 7311k freed
[   36.971601] audit: initializing netlink socket (disabled)
[   36.971639] audit(1219706920.472:1): initialized
[   36.977162] VFS: Disk quotas dquot_6.5.1
[   36.977399] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   36.977813] io scheduler noop registered
[   36.977821] io scheduler anticipatory registered
[   36.977825] io scheduler deadline registered
[   36.977872] io scheduler cfq registered (default)
[   36.977902] Applying VIA southbridge workaround.
[   36.977911] PCI: VIA PCI bridge detected. Disabling DAC.
[   36.977959] PCI: Enabling Via external APIC routing
[   36.978012] Boot video device is 0000:01:00.0
[   36.978689] isapnp: Scanning for PnP cards...
[   37.333120] isapnp: No Plug & Play device found
[   37.415606] Real Time Clock Driver v1.12ac
[   37.415837] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   37.416061] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   37.416422] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[   37.417862] 00:07: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   37.418619] 00:08: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[   37.420552] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   37.420728] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[   37.420977] PNP: PS/2 Controller [PNP0303:PS2K] at 0x60,0x64 irq 1
[   37.420985] PNP: PS/2 appears to have AUX port disabled, if this is incorrect please boot with i8042.nopnp
[   37.421233] serio: i8042 KBD port at 0x60,0x64 irq 1
[   37.433983] mice: PS/2 mouse device common for all mice
[   37.434283] EISA: Probing bus 0 at eisa.0
[   37.434343] EISA: Detected 0 cards.
[   37.434350] cpuidle: using governor ladder
[   37.434355] cpuidle: using governor menu
[   37.434758] NET: Registered protocol family 1
[   37.434837] Using IPI No-Shortcut mode
[   37.434912] registered taskstats version 1
[   37.435117]   Magic number: 4:259:505
[   37.435125]   hash matches device i8042
[   37.435359] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[   37.435363] EDD information not available.
[   37.436045] Freeing unused kernel memory: 368k freed
[   37.493732] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[   38.988175] fuse init (API version 7.9)
[   39.050439] ACPI: Thermal Zone [THRM] (30 C)
[   39.672226] SCSI subsystem initialized
[   39.796041] libata version 3.00 loaded.
[   39.802722] usbcore: registered new interface driver usbfs
[   39.802787] usbcore: registered new interface driver hub
[   39.803024] pata_via 0000:00:07.1: version 0.3.3
[   39.805690] usbcore: registered new device driver usb
[   39.805735] scsi0 : pata_via
[   39.810509] scsi1 : pata_via
[   39.814002] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xffa0 irq 14
[   39.814010] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xffa8 irq 15
[   39.814330] 8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)
[   39.818635] USB Universal Host Controller Interface driver v3.0
[   39.949794] FDC 0 is a post-1991 82077
[   39.985966] ata1.00: ATA-6: Maxtor 32049H2, YAH814Y0, max UDMA/100
[   39.985978] ata1.00: 40021632 sectors, multi 16: LBA 
[   39.993680] ata1.01: HPA unlocked: 312579695 -> 312581808, native 312581808
[   39.993689] ata1.01: ATA-6: ST3160023A, 8.01, max UDMA/100
[   39.993694] ata1.01: 312581808 sectors, multi 0: LBA48 
[   40.010465] ata1.00: configured for UDMA/100
[   40.025936] ata1.01: configured for UDMA/100
[   40.345623] ata2.00: ATAPI: SONY    CD-RW  CRX230ED, 4YS1, max UDMA/33
[   40.517611] ata2.00: configured for UDMA/33
[   40.517924] scsi 0:0:0:0: Direct-Access     ATA      Maxtor 32049H2   YAH8 PQ: 0 ANSI: 5
[   40.518181] scsi 0:0:1:0: Direct-Access     ATA      ST3160023A       8.01 PQ: 0 ANSI: 5
[   40.519302] scsi 1:0:0:0: CD-ROM            SONY     CD-RW  CRX230ED  4YS1 PQ: 0 ANSI: 5
[   40.525442] 8139cp 0000:00:0d.0: This (id 10ec:8139 rev 10) is not an 8139C+ compatible chip
[   40.525454] 8139cp 0000:00:0d.0: Try the "8139too" driver instead.
[   40.525912] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 10
[   40.525929] ACPI: PCI Interrupt 0000:00:07.2[D] -> Link [LNKD] -> GSI 10 (level, low) -> IRQ 10
[   40.525941] PCI: VIA VLink IRQ fixup for 0000:00:07.2, from 12 to 10
[   40.525974] uhci_hcd 0000:00:07.2: UHCI Host Controller
[   40.526520] uhci_hcd 0000:00:07.2: new USB bus registered, assigned bus number 1
[   40.526569] uhci_hcd 0000:00:07.2: irq 10, io base 0x0000cc00
[   40.526878] usb usb1: configuration #1 chosen from 1 choice
[   40.526935] hub 1-0:1.0: USB hub found
[   40.526949] hub 1-0:1.0: 2 ports detected
[   40.537439] 8139too Fast Ethernet driver 0.9.28
[   40.629495] ACPI: PCI Interrupt 0000:00:07.3[D] -> Link [LNKD] -> GSI 10 (level, low) -> IRQ 10
[   40.629515] PCI: VIA VLink IRQ fixup for 0000:00:07.3, from 12 to 10
[   40.629558] uhci_hcd 0000:00:07.3: UHCI Host Controller
[   40.629642] uhci_hcd 0000:00:07.3: new USB bus registered, assigned bus number 2
[   40.629689] uhci_hcd 0000:00:07.3: irq 10, io base 0x0000d000
[   40.629999] usb usb2: configuration #1 chosen from 1 choice
[   40.630059] hub 2-0:1.0: USB hub found
[   40.630076] hub 2-0:1.0: 2 ports detected
[   40.733745] ACPI: PCI Interrupt 0000:00:0d.0[A] -> GSI 17 (level, low) -> IRQ 16
[   40.734513] eth0: RealTek RTL8139 at 0xc800, 00:06:4f:02:19:d8, IRQ 16
[   40.734520] eth0:  Identified 8139 chip type 'RTL-8139C'
[   40.867990] usb 1-1: new full speed USB device using uhci_hcd and address 2
[   41.037648] usb 1-1: configuration #1 chosen from 1 choice
[   41.178662] Driver 'sd' needs updating - please use bus_type methods
[   41.184053] sd 0:0:0:0: [sda] 40021632 512-byte hardware sectors (20491 MB)
[   41.184099] sd 0:0:0:0: [sda] Write Protect is off
[   41.184107] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   41.184157] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   41.184541] sd 0:0:0:0: [sda] 40021632 512-byte hardware sectors (20491 MB)
[   41.184589] sd 0:0:0:0: [sda] Write Protect is off
[   41.184596] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   41.184651] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   41.184670]  sda:<4>Driver 'sr' needs updating - please use bus_type methods
[   41.214699]  sda1 sda2 < sda5 >
[   41.251465] sd 0:0:0:0: [sda] Attached SCSI disk
[   41.251695] sd 0:0:1:0: [sdb] 312581808 512-byte hardware sectors (160042 MB)
[   41.251727] sd 0:0:1:0: [sdb] Write Protect is off
[   41.251735] sd 0:0:1:0: [sdb] Mode Sense: 00 3a 00 00
[   41.251784] sd 0:0:1:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   41.251980] sd 0:0:1:0: [sdb] 312581808 512-byte hardware sectors (160042 MB)
[   41.252006] sd 0:0:1:0: [sdb] Write Protect is off
[   41.252013] sd 0:0:1:0: [sdb] Mode Sense: 00 3a 00 00
[   41.252057] sd 0:0:1:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   41.252066]  sdb: sdb1 sdb2 < sdb5<6>usb 1-2: new full speed USB device using uhci_hcd and address 3
[   41.290061]  sdb6 > sdb3
[   41.290376] sd 0:0:1:0: [sdb] Attached SCSI disk
[   41.310469] sr0: scsi3-mmc drive: 109x/52x writer cd/rw xa/form2 cdda tray
[   41.310485] Uniform CD-ROM driver Revision: 3.20
[   41.310625] sr 1:0:0:0: Attached scsi CD-ROM sr0
[   41.311435] sd 0:0:0:0: Attached scsi generic sg0 type 0
[   41.311484] sd 0:0:1:0: Attached scsi generic sg1 type 0
[   41.311526] sr 1:0:0:0: Attached scsi generic sg2 type 5
[   41.454287] usb 1-2: configuration #1 chosen from 1 choice
[   41.714632] usbcore: registered new interface driver hiddev
[   41.719820] input: Logitech USB Gaming Mouse as /devices/pci0000:00/0000:00:07.2/usb1/1-2/1-2:1.0/input/input2
[   41.748639] input,hidraw0: USB HID v1.11 Mouse [Logitech USB Gaming Mouse] on usb-0000:00:07.2-2
[   41.754968] hiddev96hidraw1: USB HID v1.11 Device [Logitech USB Gaming Mouse] on usb-0000:00:07.2-2
[   41.755056] usbcore: registered new interface driver usbhid
[   41.755071] /build/buildd/linux-2.6.24/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
[   41.991744] Attempting manual resume
[   41.991753] swsusp: Resume From Partition 8:5
[   41.991757] PM: Checking swsusp image.
[   41.992357] PM: Resume from disk failed.
[   42.069654] kjournald starting.  Commit interval 5 seconds
[   42.069680] EXT3-fs: mounted filesystem with ordered data mode.
[   58.556012] input: PC Speaker as /devices/platform/pcspkr/input/input3
[   59.555831] parport_pc: VIA 686A/8231 detected
[   59.555844] parport_pc: probing current configuration
[   59.555866] parport_pc: Current parallel port base: 0x378
[   59.555949] parport0: PC-style at 0x378 (0x778), irq 7, using FIFO [PCSPP,TRISTATE,COMPAT,ECP]
[   59.628925] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   59.635167] parport0: Printer, HEWLETT-PACKARD DESKJET 720C
[   59.635310] parport_pc: VIA parallel port: io=0x378, irq=7
[   59.677491] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   59.743565] Linux agpgart interface v0.102
[   60.114621] input: Power Button (FF) as /devices/virtual/input/input4
[   60.166237] ACPI: Power Button (FF) [PWRF]
[   60.166413] input: Power Button (CM) as /devices/virtual/input/input5
[   60.192899] agpgart: Detected VIA Apollo Pro 133 chipset
[   60.210019] ACPI: Power Button (CM) [PWRB]
[   60.210282] input: Sleep Button (CM) as /devices/virtual/input/input6
[   60.234362] agpgart: AGP aperture is 256M @ 0xe0000000
[   60.270192] ACPI: Sleep Button (CM) [SLPB]
[   62.088710] nvidia: module license 'NVIDIA' taints kernel.
[   62.387382] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 17
[   62.388601] NVRM: loading NVIDIA UNIX x86 Kernel Module  173.14.12  Thu Jul 17 18:11:36 PDT 2008
[   62.935154] ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 9
[   62.935180] ACPI: PCI Interrupt 0000:00:07.5[C] -> Link [LNKC] -> GSI 9 (level, low) -> IRQ 9
[   62.935193] PCI: VIA VLink IRQ fixup for 0000:00:07.5, from 10 to 9
[   62.935386] PCI: Setting latency timer of device 0000:00:07.5 to 64
[   65.254306] lp0: using parport0 (interrupt-driven).
[   65.375931] Adding 875500k swap on /dev/sda5.  Priority:-1 extents:1 across:875500k
[   66.043141] EXT3 FS on sda1, internal journal
[   68.544068] ip_tables: (C) 2000-2006 Netfilter Core Team
[   69.484237] No dock devices found.
[   72.240712] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[   72.240728] apm: disabled - APM is not SMP safe.
[   72.487806] ppdev: user-space parallel port driver
[   72.874367] audit(1219706956.903:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=4851 profile="/usr/sbin/cupsd" namespace="default"
[   79.029302] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[   79.197046] Bluetooth: Core ver 2.11
[   79.198353] NET: Registered protocol family 31
[   79.198364] Bluetooth: HCI device and connection manager initialized
[   79.198374] Bluetooth: HCI socket layer initialized
[   79.222289] Bluetooth: L2CAP ver 2.9
[   79.222306] Bluetooth: L2CAP socket layer initialized
[   79.346807] Bluetooth: RFCOMM socket layer initialized
[   79.346860] Bluetooth: RFCOMM TTY layer initialized
[   79.346865] Bluetooth: RFCOMM ver 1.8
[   82.777495] agpgart: Found an AGP 2.0 compliant device at 0000:00:00.0.
[   82.777525] agpgart: Putting AGP V2 device at 0000:00:00.0 into 4x mode
[   82.777567] agpgart: Putting AGP V2 device at 0000:01:00.0 into 4x mode
[   83.412535] NET: Registered protocol family 17
[   88.233002] NET: Registered protocol family 10
[   88.234053] lo: Disabled Privacy Extensions
[   98.258769] eth0: no IPv6 routers present
[  160.357533] process `skype' is using obsolete setsockopt SO_BSDCOMPAT
[ 7024.710080] usb 1-1: USB disconnect, address 2
[79181.627231] operapluginwrap[13434]: segfault at 8c000000 eip b7610a9b esp bfc73f10 error 4
[79369.485692] operapluginwrap[16671]: segfault at 00000001 eip b76d3a9b esp b59ffda0 error 4
[87080.061924] usb 1-1: new full speed USB device using uhci_hcd and address 4
[87080.233444] usb 1-1: configuration #1 chosen from 1 choice

---

