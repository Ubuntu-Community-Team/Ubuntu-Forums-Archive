---
title: "K3B cannot write to my DVD-RW/CD-RW combo drive"
date: 2008-10-20
forum: Hardware
---

### Post by SkittleLinux18 on 2008-10-20
Which I don't find surprising since this drive is the reason I could not boot into the Kubuntu LiveCD. (Has something to do with SCSI Emulation. I can find page if anyone wants it for understanding.) When I try to burn a CD or DVD, I get these error messages:

[IMG]http://i17.photobucket.com/albums/b62/keving1/K3B-Error-Messages.jpg[/IMG]

First, I have tried doing the things suggested on the following pages:
[chmod 777 to /dev/scd0]("http://ubuntuforums.org/showthread.php?t=676848")
[setting cdrdao parameters]("http://ph.ubuntuforums.com/showthread.php?t=789848")
[Adding cdrom Privileges to groups and users settings]("https://answers.launchpad.net/ubuntu/+source/k3b/+question/23198")

Commands I have tried:

> kevbuntu@kevbuntu-desktop:~$ sudo chmod 777 /dev/scd0
[sudo] password for kevbuntu:
kevbuntu@kevbuntu-desktop:~$

> kevbuntu@kevbuntu-desktop:~$ groups
kevbuntu adm dialout fax cdrom floppy audio dip video plugdev syslog fuse lpadmin admin
kevbuntu@kevbuntu-desktop:~$


> kevbuntu@kevbuntu-desktop:~$ dmesg | grep -i cd | grep -i rom
[   49.728807] scsi 3:0:0:0: CD-ROM            PIONEER  DVD-RW  DVR-111D 1.19 PQ: 0 ANSI: 5
[   49.965268] Uniform CD-ROM driver Revision: 3.20
[   49.965366] sr 3:0:0:0: Attached scsi CD-ROM sr0
[45389.817907] cdrom: This disc doesn't have any tracks I recognize!
[47521.420064] cdrom: This disc doesn't have any tracks I recognize!


This is a link to a snapshot of my current Disks and Filesystems Configuration [here]("http://i17.photobucket.com/albums/b62/keving1/Disks-Filesystems-Config.jpg").

I've tried everything I could find for three hours. Any other suggestions before my only option is a new DVD burner?? Thanks, everyone!

SL18

P.S. dmesg output:

> root@kevbuntu-desktop:~# dmesg
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.24-19-generic (buildd@palmer) (gcc version 4.2.3 (Ubuntu 4.2.3-2ubuntu7)) #1 SMP Wed Jun 18 14:43:41 UTC 2008 (Ubuntu 2.6.24-19.34-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000005fff0000 (usable)
[    0.000000]  BIOS-e820: 000000005fff0000 - 000000005fff8000 (ACPI data)
[    0.000000]  BIOS-e820: 000000005fff8000 - 0000000060000000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fff80000 - 0000000100000000 (reserved)
[    0.000000] 639MB HIGHMEM available.
[    0.000000] 896MB LOWMEM available.
[    0.000000] found SMP MP-table at 000fb930
[    0.000000] Entering add_active_range(0, 0, 393200) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   229376
[    0.000000]   HighMem    229376 ->   393200
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   393200
[    0.000000] On node 0 totalpages: 393200
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 1760 pages used for memmap
[    0.000000]   Normal zone: 223520 pages, LIFO batch:31
[    0.000000]   HighMem zone: 1279 pages used for memmap
[    0.000000]   HighMem zone: 162545 pages, LIFO batch:31
[    0.000000]   Movable zone: 0 pages used for memmap
[    0.000000] DMI 2.3 present.
[    0.000000] ACPI: RSDP signature @ 0xC00FA970 checksum 0
[    0.000000] ACPI: RSDP 000FA970, 0014 (r0 AMI   )
[    0.000000] ACPI: RSDT 5FFF0000, 002C (r1 AMIINT VIA_K7         10 MSFT       97)
[    0.000000] ACPI: FACP 5FFF0030, 0081 (r1 AMIINT VIA_K7         11 MSFT       97)
[    0.000000] ACPI: DSDT 5FFF0120, 36AC (r1    VIA   VIA_K7     1000 MSFT  100000D)
[    0.000000] ACPI: FACS 5FFF8000, 0040
[    0.000000] ACPI: APIC 5FFF00C0, 0054 (r1 AMIINT VIA_K7          9 MSFT       97)
[    0.000000] ACPI: PM-Timer IO Port: 0x808
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] Processor #0 6:10 APIC version 16
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 3, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 low level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] Allocating PCI resources starting at 70000000 (gap: 60000000:9ec00000)
[    0.000000] swsusp: Registered nosave memory region: 000000000009f000 - 00000000000a0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000a0000 - 00000000000f0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000f0000 - 0000000000100000
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 390129
[    0.000000] Kernel command line: root=UUID=1c8dd6d2-5cda-4cc7-aed7-77b1214d4b5d ro quiet splash
[    0.000000] mapped APIC to ffffb000 (fee00000)
[    0.000000] mapped IOAPIC to ffffa000 (fec00000)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] Detected 1305.897 MHz processor.
[   42.813491] Console: colour VGA+ 80x25
[   42.813498] console [tty0] enabled
[   42.814696] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[   42.815586] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[   42.927012] Memory: 1546376k/1572800k available (2177k kernel code, 25200k reserved, 1006k data, 368k init, 655296k highmem)
[   42.927026] virtual kernel memory layout:
[   42.927027]     fixmap  : 0xfff4b000 - 0xfffff000   ( 720 kB)
[   42.927029]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   42.927031]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
[   42.927033]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
[   42.927035]       .init : 0xc0421000 - 0xc047d000   ( 368 kB)
[   42.927037]       .data : 0xc0320434 - 0xc041bdc4   (1006 kB)
[   42.927039]       .text : 0xc0100000 - 0xc0320434   (2177 kB)
[   42.927044] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   42.927127] SLUB: Genslabs=11, HWalign=32, Order=0-1, MinObjects=4, CPUs=1, Nodes=1
[   43.007148] Calibrating delay using timer specific routine.. 2614.69 BogoMIPS (lpj=5229385)
[   43.007206] Security Framework initialized
[   43.007221] SELinux:  Disabled at boot.
[   43.007258] AppArmor: AppArmor initialized
[   43.007266] Failure registering capabilities with primary security module.
[   43.007282] Mount-cache hash table entries: 512
[   43.007530] Initializing cgroup subsys ns
[   43.007539] Initializing cgroup subsys cpuacct
[   43.007558] CPU: After generic identify, caps: 0383fbff c1c3fbff 00000000 00000000 00000000 00000000 00000000 00000000
[   43.007573] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[   43.007578] CPU: L2 Cache: 512K (64 bytes/line)
[   43.007583] CPU: After all inits, caps: 0383fbff c1c3fbff 00000000 00000420 00000000 00000000 00000000 00000000
[   43.007603] Compat vDSO mapped to ffffe000.
[   43.007627] Checking 'hlt' instruction... OK.
[   43.023565] SMP alternatives: switching to UP code
[   43.025385] Freeing SMP alternatives: 11k freed
[   43.025586] Early unpacking initramfs... done
[   43.575397] ACPI: Core revision 20070126
[   43.575524] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[   43.578116] CPU0: AMD Athlon(tm) XP 1700+ stepping 00
[   43.578152] Total of 1 processors activated (2614.69 BogoMIPS).
[   43.578912] ENABLING IO-APIC IRQs
[   43.579254] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[   43.723152] Brought up 1 CPUs
[   43.723229] CPU0 attaching sched-domain:
[   43.723234]  domain 0: span 01
[   43.723236]   groups: 01
[   43.723560] net_namespace: 64 bytes
[   43.723571] Booting paravirtualized kernel on bare hardware
[   43.724280] Time: 11:56:47  Date: 10/19/08
[   43.724329] NET: Registered protocol family 16
[   43.724699] EISA bus registered
[   43.724732] ACPI: bus type pci registered
[   43.726372] PCI: PCI BIOS revision 2.10 entry at 0xfdab1, last bus=1
[   43.726377] PCI: Using configuration type 1
[   43.726384] Setting up standard PCI resources
[   43.746230] ACPI: EC: Look up EC in DSDT
[   43.751903] ACPI: Interpreter enabled
[   43.751907] ACPI: (supports S0 S1 S4 S5)
[   43.751927] ACPI: Using IOAPIC for interrupt routing
[   43.757428] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   43.758394] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   43.761621] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 10 *11 12 14 15)
[   43.761756] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 *10 11 12 14 15)
[   43.761886] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 10 11 *12 14 15)
[   43.762016] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 *5 6 7 10 11 12 14 15)
[   43.762144] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[   43.762274] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[   43.762404] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[   43.762534] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[   43.762681] ACPI: Power Resource [URP1] (off)
[   43.762723] ACPI: Power Resource [URP2] (off)
[   43.762763] ACPI: Power Resource [FDDP] (off)
[   43.762803] ACPI: Power Resource [LPTP] (off)
[   43.762875] Linux Plug and Play Support v0.97 (c) Adam Belay
[   43.762932] pnp: PnP ACPI init
[   43.762943] ACPI: bus type pnp registered
[   43.766079] pnp: PnP ACPI: found 8 devices
[   43.766083] ACPI: ACPI bus type pnp unregistered
[   43.766089] PnPBIOS: Disabled by ACPI PNP
[   43.766470] PCI: Using ACPI for IRQ routing
[   43.766475] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   43.783075] NET: Registered protocol family 8
[   43.783079] NET: Registered protocol family 20
[   43.783199] AppArmor: AppArmor Filesystem Enabled
[   43.787060] Time: tsc clocksource has been installed.
[   43.795117] system 00:01: ioport range 0x290-0x297 has been reserved
[   43.795122] system 00:01: ioport range 0x3f0-0x3f1 has been reserved
[   43.795127] system 00:01: ioport range 0x4d0-0x4d1 has been reserved
[   43.795131] system 00:01: ioport range 0x400-0x40f has been reserved
[   43.795135] system 00:01: ioport range 0x820-0x821 has been reserved
[   43.795141] system 00:01: iomem range 0xfee00000-0xfee00fff could not be reserved
[   43.825820] PCI: Bridge: 0000:00:01.0
[   43.825824]   IO window: disabled.
[   43.825831]   MEM window: dbe00000-dfefffff
[   43.825836]   PREFETCH window: bbd00000-dbcfffff
[   43.825858] PCI: Setting latency timer of device 0000:00:01.0 to 64
[   43.825876] NET: Registered protocol family 2
[   43.863187] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[   43.863804] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[   43.866571] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[   43.868025] TCP: Hash tables configured (established 131072 bind 65536)
[   43.868030] TCP reno registered
[   43.879308] checking if image is initramfs...<7>Switched to high resolution mode on CPU 0
[   44.343015]  it is
[   44.910421] Freeing initrd memory: 7961k freed
[   44.911629] audit: initializing netlink socket (disabled)
[   44.911656] audit(1224417407.880:1): initialized
[   44.911956] highmem bounce pool size: 64 pages
[   44.915126] VFS: Disk quotas dquot_6.5.1
[   44.915247] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   44.915474] io scheduler noop registered
[   44.915478] io scheduler anticipatory registered
[   44.915482] io scheduler deadline registered
[   44.915498] io scheduler cfq registered (default)
[   44.915524] PCI: VIA PCI bridge detected. Disabling DAC.
[   44.915604] PCI: Bypassing VIA 8237 APIC De-Assert Message
[   44.915629] Boot video device is 0000:01:00.0
[   44.916082] isapnp: Scanning for PnP cards...
[   45.270164] isapnp: No Plug & Play device found
[   45.317034] Real Time Clock Driver v1.12ac
[   45.317206] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   45.317375] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   45.318318] 00:06: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   45.319854] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   45.319966] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[   45.320193] PNP: No PS/2 controller found. Probing ports directly.
[   45.570740] serio: i8042 KBD port at 0x60,0x64 irq 1
[   45.582739] mice: PS/2 mouse device common for all mice
[   45.582920] EISA: Probing bus 0 at eisa.0
[   45.582966] EISA: Detected 0 cards.
[   45.582972] cpuidle: using governor ladder
[   45.582975] cpuidle: using governor menu
[   45.583200] NET: Registered protocol family 1
[   45.583244] Using IPI No-Shortcut mode
[   45.583299] registered taskstats version 1
[   45.583453]   Magic number: 12:508:934
[   45.583750] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[   45.583754] EDD information not available.
[   45.584498] Freeing unused kernel memory: 368k freed
[   46.936046] fuse init (API version 7.9)
[   47.886518] SCSI subsystem initialized
[   47.986231] usbcore: registered new interface driver usbfs
[   47.986273] usbcore: registered new interface driver hub
[   48.003712] libata version 3.00 loaded.
[   48.026354] usbcore: registered new device driver usb
[   48.054219] sata_via 0000:00:0f.0: version 2.3
[   48.054271] ACPI: PCI Interrupt 0000:00:0f.0[B] -> GSI 20 (level, low) -> IRQ 16
[   48.054369] sata_via 0000:00:0f.0: routed to hard irq line 10
[   48.067197] scsi0 : sata_via
[   48.076234] USB Universal Host Controller Interface driver v3.0
[   48.082416] scsi1 : sata_via
[   48.082505] ata1: SATA max UDMA/133 cmd 0xec00 ctl 0xe800 bmdma 0xdc00 irq 16
[   48.082510] ata2: SATA max UDMA/133 cmd 0xe400 ctl 0xe000 bmdma 0xdc08 irq 16
[   48.095964] via-rhine.c:v1.10-LK1.4.3 2007-03-06 Written by Donald Becker
[   48.286080] ata1: SATA link down 1.5 Gbps (SStatus 0 SControl 300)
[   48.498042] ata2: SATA link down 1.5 Gbps (SStatus 0 SControl 300)
[   48.509160] ACPI: PCI Interrupt 0000:00:10.0[A] -> GSI 21 (level, low) -> IRQ 17
[   48.509181] uhci_hcd 0000:00:10.0: UHCI Host Controller
[   48.509612] uhci_hcd 0000:00:10.0: new USB bus registered, assigned bus number 1
[   48.509653] uhci_hcd 0000:00:10.0: irq 17, io base 0x0000c400
[   48.509894] usb usb1: configuration #1 chosen from 1 choice
[   48.509932] hub 1-0:1.0: USB hub found
[   48.509942] hub 1-0:1.0: 2 ports detected
[   48.610168] ACPI: PCI Interrupt 0000:00:10.1[A] -> GSI 21 (level, low) -> IRQ 17
[   48.610190] uhci_hcd 0000:00:10.1: UHCI Host Controller
[   48.610232] uhci_hcd 0000:00:10.1: new USB bus registered, assigned bus number 2
[   48.610262] uhci_hcd 0000:00:10.1: irq 17, io base 0x0000c800
[   48.610445] usb usb2: configuration #1 chosen from 1 choice
[   48.610482] hub 2-0:1.0: USB hub found
[   48.610492] hub 2-0:1.0: 2 ports detected
[   48.714208] ACPI: PCI Interrupt 0000:00:10.2[B] -> GSI 21 (level, low) -> IRQ 17
[   48.714231] uhci_hcd 0000:00:10.2: UHCI Host Controller
[   48.714270] uhci_hcd 0000:00:10.2: new USB bus registered, assigned bus number 3
[   48.714300] uhci_hcd 0000:00:10.2: irq 17, io base 0x0000cc00
[   48.714495] usb usb3: configuration #1 chosen from 1 choice
[   48.714540] hub 3-0:1.0: USB hub found
[   48.714550] hub 3-0:1.0: 2 ports detected
[   48.818108] ACPI: PCI Interrupt 0000:00:10.3[B] -> GSI 21 (level, low) -> IRQ 17
[   48.818131] uhci_hcd 0000:00:10.3: UHCI Host Controller
[   48.818172] uhci_hcd 0000:00:10.3: new USB bus registered, assigned bus number 4
[   48.818202] uhci_hcd 0000:00:10.3: irq 17, io base 0x0000d000
[   48.818414] usb usb4: configuration #1 chosen from 1 choice
[   48.818453] hub 4-0:1.0: USB hub found
[   48.818463] hub 4-0:1.0: 2 ports detected
[   48.922561] pata_via 0000:00:0f.1: version 0.3.3
[   48.922618] ACPI: PCI Interrupt 0000:00:0f.1[A] -> GSI 20 (level, low) -> IRQ 16
[   48.926077] scsi2 : pata_via
[   48.927134] scsi3 : pata_via
[   48.929482] ata3: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xfc00 irq 14
[   48.929488] ata4: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xfc08 irq 15
[   49.120759] ata3.00: ATA-7: WDC WD2000JB-00REA0, 20.00K20, max UDMA/100
[   49.120768] ata3.00: 390721968 sectors, multi 16: LBA48
[   49.165221] ata3.01: ATA-7: ST3160815A, 3.AAC, max UDMA/100
[   49.165226] ata3.01: 312581808 sectors, multi 16: LBA48
[   49.165246] ata3.00: limited to UDMA/33 due to 40-wire cable
[   49.165250] ata3.01: limited to UDMA/33 due to 40-wire cable
[   49.170184] ata3.00: configured for UDMA/33
[   49.231711] ata3.01: configured for UDMA/33
[   49.361780] usb 3-1: new full speed USB device using uhci_hcd and address 2
[   49.511231] usb 3-1: configuration #1 chosen from 1 choice
[   49.513155] hub 3-1:1.0: USB hub found
[   49.515092] hub 3-1:1.0: 4 ports detected
[   49.550146] ata4.00: ATAPI: PIONEER DVD-RW  DVR-111D, 1.19, max UDMA/66
[   49.721974] ata4.00: configured for UDMA/66
[   49.722184] scsi 2:0:0:0: Direct-Access     ATA      WDC WD2000JB-00R 20.0 PQ: 0 ANSI: 5
[   49.722822] scsi 2:0:1:0: Direct-Access     ATA      ST3160815A       3.AA PQ: 0 ANSI: 5
[   49.728807] scsi 3:0:0:0: CD-ROM            PIONEER  DVD-RW  DVR-111D 1.19 PQ: 0 ANSI: 5
[   49.733599] ACPI: PCI Interrupt 0000:00:12.0[A] -> GSI 23 (level, low) -> IRQ 18
[   49.734013] eth0: VIA Rhine II at 0xdfffbd00, 00:0c:76:bb:82:a6, IRQ 18.
[   49.734722] eth0: MII PHY found at address 1, status 0x786d advertising 01e1 Link c5e1.
[   49.734772] ACPI: PCI Interrupt 0000:00:10.4[C] -> GSI 21 (level, low) -> IRQ 17
[   49.734785] ehci_hcd 0000:00:10.4: EHCI Host Controller
[   49.734832] ehci_hcd 0000:00:10.4: new USB bus registered, assigned bus number 5
[   49.734897] ehci_hcd 0000:00:10.4: irq 17, io mem 0xdfffbe00
[   49.745694] ehci_hcd 0000:00:10.4: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   49.745930] usb usb5: configuration #1 chosen from 1 choice
[   49.745986] hub 5-0:1.0: USB hub found
[   49.745999] hub 5-0:1.0: 8 ports detected
[   49.871444] Driver 'sd' needs updating - please use bus_type methods
[   49.871607] sd 2:0:0:0: [sda] 390721968 512-byte hardware sectors (200050 MB)
[   49.871631] sd 2:0:0:0: [sda] Write Protect is off
[   49.871636] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   49.871665] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   49.871748] sd 2:0:0:0: [sda] 390721968 512-byte hardware sectors (200050 MB)
[   49.871765] sd 2:0:0:0: [sda] Write Protect is off
[   49.871769] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   49.871794] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   49.871800]  sda: sda1 sda2 <<4>Driver 'sr' needs updating - please use bus_type methods
[   49.903340]  sda5 >
[   49.903505] sd 2:0:0:0: [sda] Attached SCSI disk
[   49.903631] sd 2:0:1:0: [sdb] 312581808 512-byte hardware sectors (160042 MB)
[   49.903656] sd 2:0:1:0: [sdb] Write Protect is off
[   49.903660] sd 2:0:1:0: [sdb] Mode Sense: 00 3a 00 00
[   49.903690] sd 2:0:1:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   49.903762] sd 2:0:1:0: [sdb] 312581808 512-byte hardware sectors (160042 MB)
[   49.903779] sd 2:0:1:0: [sdb] Write Protect is off
[   49.903783] sd 2:0:1:0: [sdb] Mode Sense: 00 3a 00 00
[   49.903809] sd 2:0:1:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   49.903816]  sdb: sdb1
[   49.928209] sd 2:0:1:0: [sdb] Attached SCSI disk
[   49.940918] sd 2:0:0:0: Attached scsi generic sg0 type 0
[   49.940982] sd 2:0:1:0: Attached scsi generic sg1 type 0
[   49.941020] sr 3:0:0:0: Attached scsi generic sg2 type 5
[   49.965257] sr0: scsi3-mmc drive: 40x/40x writer cd/rw xa/form2 cdda tray
[   49.965268] Uniform CD-ROM driver Revision: 3.20
[   49.965366] sr 3:0:0:0: Attached scsi CD-ROM sr0
[   50.005668] usb 3-1: USB disconnect, address 2
[   50.328406] Attempting manual resume
[   50.328413] swsusp: Resume From Partition 8:5
[   50.328416] PM: Checking swsusp image.
[   50.328718] PM: Resume from disk failed.
[   50.382985] kjournald starting.  Commit interval 5 seconds
[   50.383012] EXT3-fs: mounted filesystem with ordered data mode.
[   50.613492] usb 3-1: new full speed USB device using uhci_hcd and address 3
[   50.762830] usb 3-1: configuration #1 chosen from 1 choice
[   50.765647] hub 3-1:1.0: USB hub found
[   50.767610] hub 3-1:1.0: 4 ports detected
[   51.082532] usb 3-1.1: new low speed USB device using uhci_hcd and address 4
[   51.245621] usb 3-1.1: configuration #1 chosen from 1 choice
[   51.450370] usb 3-1.2: new low speed USB device using uhci_hcd and address 5
[   51.589474] usb 3-1.2: configuration #1 chosen from 1 choice
[   59.675083] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   59.736222] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   59.867434] Linux agpgart interface v0.102
[   59.939570] agpgart: Detected VIA KT400/KT400A/KT600 chipset
[   59.950387] agpgart: AGP aperture is 128M @ 0xe0000000
[   61.019987] input: Power Button (FF) as /devices/virtual/input/input1
[   61.031129] ACPI: Power Button (FF) [PWRF]
[   61.031287] input: Power Button (CM) as /devices/virtual/input/input2
[   61.043093] ACPI: Power Button (CM) [PWRB]
[   61.043220] input: Sleep Button (CM) as /devices/virtual/input/input3
[   61.059104] ACPI: Sleep Button (CM) [SLPB]
[   61.411215] ACPI: PCI Interrupt 0000:00:11.5[C] -> GSI 22 (level, low) -> IRQ 19
[   61.411370] PCI: Setting latency timer of device 0000:00:11.5 to 64
[   62.183010] ACPI: PCI Interrupt 0000:00:08.0[A] -> GSI 18 (level, low) -> IRQ 20
[   62.393836] eth0: link up, 100Mbps, full-duplex, lpa 0xC5E1
[   63.004784] input: PC Speaker as /devices/platform/pcspkr/input/input4
[   64.178941] nvidia: module license 'NVIDIA' taints kernel.
[   64.715564] NET: Registered protocol family 10
[   64.715902] lo: Disabled Privacy Extensions
[   64.727735] parport_pc 00:07: reported by Plug and Play ACPI
[   64.727843] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,EPP,ECP,DMA]
[   65.147321] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 21
[   65.148004] NVRM: loading NVIDIA UNIX x86 Kernel Module  169.12  Thu Feb 14 17:53:07 PST 2008
[   65.190861] usbcore: registered new interface driver hiddev
[   65.213789] input: Logitech Logitech USB Keyboard as /devices/pci0000:00/0000:00:10.2/usb3/3-1/3-1.1/3-1.1:1.0/input/input5
[   65.238286] input,hidraw0: USB HID v1.10 Keyboard [Logitech Logitech USB Keyboard] on usb-0000:00:10.2-1.1
[   65.268509] input: Logitech USB-PS/2 Optical Mouse as /devices/pci0000:00/0000:00:10.2/usb3/3-1/3-1.2/3-1.2:1.0/input/input6
[   65.298178] input,hidraw1: USB HID v1.10 Mouse [Logitech USB-PS/2 Optical Mouse] on usb-0000:00:10.2-1.2
[   65.298213] usbcore: registered new interface driver usbhid
[   65.298220] /build/buildd/linux-2.6.24/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
[   68.164563] lp0: using parport0 (interrupt-driven).
[   68.251034] Adding 4554388k swap on /dev/sda5.  Priority:-1 extents:1 across:4554388k
[   68.852391] EXT3 FS on sda1, internal journal
[   69.077972] device-mapper: uevent: version 1.0.3
[   69.078037] device-mapper: ioctl: 4.12.0-ioctl (2007-10-02) initialised: [email]dm-devel@redhat.com[/email]
[   70.018806] kjournald starting.  Commit interval 5 seconds
[   70.025251] EXT3 FS on sdb1, internal journal
[   70.025259] EXT3-fs: mounted filesystem with ordered data mode.
[   70.665184] ip_tables: (C) 2000-2006 Netfilter Core Team
[   71.233022] No dock devices found.
[   74.449216] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[   74.449227] apm: overridden by ACPI.
[   74.728428] ppdev: user-space parallel port driver
[   74.763943] eth0: no IPv6 routers present
[   75.364286] audit(1224417439.344:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=4992 profile="/usr/sbin/cupsd" namespace="default"
[   75.916726] agpgart: Found an AGP 3.5 compliant device at 0000:00:00.0.
[   75.916752] agpgart: Putting AGP V3 device at 0000:00:00.0 into 8x mode
[   75.916817] agpgart: Putting AGP V3 device at 0000:01:00.0 into 8x mode
[   78.083360] NET: Registered protocol family 17
[   78.255146] device eth0 entered promiscuous mode
[   78.255169] audit(1224417442.236:3): dev=eth0 prom=256 old_prom=0 auid=4294967295
[   84.956424] Bluetooth: Core ver 2.11
[   84.957577] NET: Registered protocol family 31
[   84.957584] Bluetooth: HCI device and connection manager initialized
[   84.957591] Bluetooth: HCI socket layer initialized
[   84.993699] Bluetooth: L2CAP ver 2.9
[   84.993709] Bluetooth: L2CAP socket layer initialized
[   85.089883] Bluetooth: RFCOMM socket layer initialized
[   85.089918] Bluetooth: RFCOMM TTY layer initialized
[   85.089921] Bluetooth: RFCOMM ver 1.8
[  442.110430] usb 3-1.2: USB disconnect, address 5
[ 1345.022079] usb 3-1.2: new low speed USB device using uhci_hcd and address 6
[ 1345.161199] usb 3-1.2: configuration #1 chosen from 1 choice
[ 1345.182489] input: Logitech USB-PS/2 Optical Mouse as /devices/pci0000:00/0000:00:10.2/usb3/3-1/3-1.2/3-1.2:1.0/input/input7
[ 1345.212501] input,hidraw1: USB HID v1.10 Mouse [Logitech USB-PS/2 Optical Mouse] on usb-0000:00:10.2-1.2
[ 1353.648916] usb 3-1.2: USB disconnect, address 6
[ 1437.148374] usb 3-1.2: new low speed USB device using uhci_hcd and address 7
[ 1437.287499] usb 3-1.2: configuration #1 chosen from 1 choice
[ 1437.309775] input: Logitech USB-PS/2 Optical Mouse as /devices/pci0000:00/0000:00:10.2/usb3/3-1/3-1.2/3-1.2:1.0/input/input8
[ 1437.339373] input,hidraw1: USB HID v1.10 Mouse [Logitech USB-PS/2 Optical Mouse] on usb-0000:00:10.2-1.2
[ 1636.297501] usb 3-1.2: USB disconnect, address 7
[ 1654.282926] usb 3-1.2: new low speed USB device using uhci_hcd and address 8
[ 1654.420055] usb 3-1.2: configuration #1 chosen from 1 choice
[ 1654.444325] input: Logitech USB-PS/2 Optical Mouse as /devices/pci0000:00/0000:00:10.2/usb3/3-1/3-1.2/3-1.2:1.0/input/input9
[ 1654.465494] input,hidraw1: USB HID v1.10 Mouse [Logitech USB-PS/2 Optical Mouse] on usb-0000:00:10.2-1.2
[34266.664314] usb 1-1: new full speed USB device using uhci_hcd and address 2
[34266.887522] usb 1-1: configuration #1 chosen from 1 choice
[34320.835942] usb 1-1: USB disconnect, address 2
[41170.504640] usb 3-1.2: USB disconnect, address 8
[41187.337501] usb 3-1.2: new low speed USB device using uhci_hcd and address 9
[41187.475615] usb 3-1.2: configuration #1 chosen from 1 choice
[41187.498983] input: Logitech USB-PS/2 Optical Mouse as /devices/pci0000:00/0000:00:10.2/usb3/3-1/3-1.2/3-1.2:1.0/input/input10
[41187.524040] input,hidraw1: USB HID v1.10 Mouse [Logitech USB-PS/2 Optical Mouse] on usb-0000:00:10.2-1.2
[45389.817907] cdrom: This disc doesn't have any tracks I recognize!
[45505.472841] usb 5-1: new high speed USB device using ehci_hcd and address 4
[45505.605891] usb 5-1: configuration #1 chosen from 1 choice
[45505.820926] usbcore: registered new interface driver libusual
[45505.882707] Initializing USB Mass Storage driver...
[45505.895876] scsi4 : SCSI emulation for USB Mass Storage devices
[45505.903564] usbcore: registered new interface driver usb-storage
[45505.904061] USB Mass Storage support registered.
[45505.904482] usb-storage: device found at 4
[45505.904488] usb-storage: waiting for device to settle before scanning
[45510.907569] usb-storage: device scan complete
[45510.908579] scsi 4:0:0:0: Direct-Access     SanDisk  U3 Cruzer Micro  3.27 PQ: 0 ANSI: 2
[45510.923732] sd 4:0:0:0: [sdc] 4013710 512-byte hardware sectors (2055 MB)
[45510.924403] sd 4:0:0:0: [sdc] Write Protect is off
[45510.924410] sd 4:0:0:0: [sdc] Mode Sense: 03 00 00 00
[45510.924414] sd 4:0:0:0: [sdc] Assuming drive cache: write through
[45510.927022] sd 4:0:0:0: [sdc] 4013710 512-byte hardware sectors (2055 MB)
[45510.927650] sd 4:0:0:0: [sdc] Write Protect is off
[45510.927656] sd 4:0:0:0: [sdc] Mode Sense: 03 00 00 00
[45510.927659] sd 4:0:0:0: [sdc] Assuming drive cache: write through
[45510.927666]  sdc: sdc1
[45510.928644] sd 4:0:0:0: [sdc] Attached SCSI removable disk
[45510.928711] sd 4:0:0:0: Attached scsi generic sg3 type 0
[45547.313355] usb 5-1: USB disconnect, address 4
[47521.420064] cdrom: This disc doesn't have any tracks I recognize!
root@kevbuntu-desktop:~#   

---

### Post by cariboo on 2008-10-20
Is your device an external usb drive? If there is any way to do it can you connect it directly to an ide cable to see if it works that way. You didn't indicate whether your computer was a desktop or laptop.

Oops I see by the listing it is a desktop computer.

Jim

---

### Post by SkittleLinux18 on 2008-10-20
> **cariboo907 said:**
> Is your device an external usb drive? If there is any way to do it can you connect it directly to an ide cable to see if it works that way. You didn't indicate whether your computer was a desktop or laptop.

Oops I see by the listing it is a desktop computer.

Jim

Hey, sorry! Good call. It is a desktop. The drive is internal and is connected to an IDE cable. It's the only drive in the tower.

---

