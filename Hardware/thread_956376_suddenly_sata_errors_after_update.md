---
title: "suddenly sata errors after update????"
date: 2008-10-23
forum: Hardware
---

### Post by Ashrael on 2008-10-23
hi, i upgraded from 2.6.24-19 to 2.6.24.21 and since then my pc is not going very fast, so, did a dmesg and found out that my hd (/, swap and /home) is somehow acting up, but it doesn't do it all the time it seems????

here is output of dmesg (would have attached it as text, but it is too big they say, it's not taking any less space now i guess, but hey..)

ANY CLUES? anyone?

> [    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.24-21-386 (buildd@palmer) (gcc version 4.2.3 (Ubuntu 4.2.3-2ubuntu7)) #1 Mon Aug 25 16:58:26 UTC 2008 (Ubuntu 2.6.24-21.42-386)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f400 (usable)
[    0.000000]  BIOS-e820: 000000000009f400 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000003fffc000 (usable)
[    0.000000]  BIOS-e820: 000000003fffc000 - 000000003ffff000 (ACPI data)
[    0.000000]  BIOS-e820: 000000003ffff000 - 0000000040000000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000ffff0000 - 0000000100000000 (reserved)
[    0.000000] 127MB HIGHMEM available.
[    0.000000] 896MB LOWMEM available.
[    0.000000] Entering add_active_range(0, 0, 262140) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   229376
[    0.000000]   HighMem    229376 ->   262140
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   262140
[    0.000000] On node 0 totalpages: 262140
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 1760 pages used for memmap
[    0.000000]   Normal zone: 223520 pages, LIFO batch:31
[    0.000000]   HighMem zone: 255 pages used for memmap
[    0.000000]   HighMem zone: 32509 pages, LIFO batch:7
[    0.000000]   Movable zone: 0 pages used for memmap
[    0.000000] DMI 2.3 present.
[    0.000000] ACPI: RSDP signature @ 0xC00F5810 checksum 0
[    0.000000] ACPI: RSDP 000F5810, 0014 (r0 ASUS  )
[    0.000000] ACPI: RSDT 3FFFC000, 0030 (r1 ASUS   P4S8X    42302E31 MSFT 31313031)
[    0.000000] ACPI: FACP 3FFFC0C0, 0074 (r1 ASUS   P4S8X    42302E31 MSFT 31313031)
[    0.000000] ACPI: DSDT 3FFFC134, 2A21 (r1   ASUS P4S8X        1000 MSFT  100000B)
[    0.000000] ACPI: FACS 3FFFF000, 0040
[    0.000000] ACPI: BOOT 3FFFC030, 0028 (r1 ASUS   P4S8X    42302E31 MSFT 31313031)
[    0.000000] ACPI: APIC 3FFFC058, 005A (r1 ASUS   P4S8X    42302E31 MSFT 31313031)
[    0.000000] ACPI: PM-Timer IO Port: 0xe408
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] Processor #0 15:2 APIC version 20
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 128, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl edge)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 20 low level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] Allocating PCI resources starting at 50000000 (gap: 40000000:bec00000)
[    0.000000] swsusp: Registered nosave memory region: 000000000009f000 - 00000000000a0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000a0000 - 00000000000f0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000f0000 - 0000000000100000
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 260093
[    0.000000] Kernel command line: root=UUID=ce3a3d81-dcdc-4568-b813-499b650a1921 ro quiet splash
[    0.000000] mapped APIC to ffffb000 (fee00000)
[    0.000000] mapped IOAPIC to ffffa000 (fec00000)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] Detected 2400.219 MHz processor.
[   31.852554] Console: colour VGA+ 80x25
[   31.852559] console [tty0] enabled
[   31.853386] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[   31.854165] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[   31.881490] Memory: 1027656k/1048560k available (2079k kernel code, 20148k reserved, 977k data, 364k init, 131056k highmem)
[   31.881502] virtual kernel memory layout:
[   31.881503]     fixmap  : 0xfffa6000 - 0xfffff000   ( 356 kB)
[   31.881504]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   31.881505]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
[   31.881507]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
[   31.881508]       .init : 0xc0400000 - 0xc045b000   ( 364 kB)
[   31.881509]       .data : 0xc0307ee4 - 0xc03fc3a4   ( 977 kB)
[   31.881510]       .text : 0xc0100000 - 0xc0307ee4   (2079 kB)
[   31.881514] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   31.881585] SLUB: Genslabs=11, HWalign=64, Order=0-1, MinObjects=4, CPUs=1, Nodes=1
[   31.961495] Calibrating delay using timer specific routine.. 4803.56 BogoMIPS (lpj=9607133)
[   31.961536] Security Framework initialized
[   31.961550] SELinux:  Disabled at boot.
[   31.961568] AppArmor: AppArmor initialized
[   31.961574] Failure registering capabilities with primary security module.
[   31.961581] Mount-cache hash table entries: 512
[   31.961756] Initializing cgroup subsys ns
[   31.961762] Initializing cgroup subsys cpuacct
[   31.961777] CPU: After generic identify, caps: bfebfbff 00000000 00000000 00000000 00000400 00000000 00000000 00000000
[   31.961789] CPU: Trace cache: 12K uops, L1 D cache: 8K
[   31.961792] CPU: L2 cache: 512K
[   31.961794] CPU: After all inits, caps: bfebfbff 00000000 00000000 00043080 00000400 00000000 00000000 00000000
[   31.961807] Compat vDSO mapped to ffffe000.
[   31.961821] CPU: Intel(R) Pentium(R) 4 CPU 2.40GHz stepping 07
[   31.961828] Checking 'hlt' instruction... OK.
[   31.979227] Freeing SMP alternatives: 0k freed
[   31.979379] Early unpacking initramfs... done
[   32.325684] ACPI: Core revision 20070126
[   32.325739] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[   32.327113] ENABLING IO-APIC IRQs
[   32.327278] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[   32.472908] net_namespace: 64 bytes
[   32.472920] Booting paravirtualized kernel on bare hardware
[   32.473501] Time: 10:06:21  Date: 10/23/08
[   32.473532] NET: Registered protocol family 16
[   32.473756] EISA bus registered
[   32.473779] ACPI: bus type pci registered
[   32.475675] PCI: PCI BIOS revision 2.10 entry at 0xf11b0, last bus=1
[   32.475678] PCI: Using configuration type 1
[   32.475694] Setting up standard PCI resources
[   32.485713] ACPI: EC: Look up EC in DSDT
[   32.492224] ACPI: Interpreter enabled
[   32.492228] ACPI: (supports S0 S1 S4 S5)
[   32.492243] ACPI: Using IOAPIC for interrupt routing
[   32.497773] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   32.498039] Enabling SiS 96x SMBus.
[   32.499329] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   32.499544] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCI1._PRT]
[   32.501121] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 10 *11 12 14 15)
[   32.501222] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 *10 11 12 14 15)
[   32.501305] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[   32.501388] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[   32.501483] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 *7 10 11 12 14 15)
[   32.501578] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 *5 6 7 10 11 12 14 15)
[   32.501673] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 10 11 12 14 15) *9
[   32.501759] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[   32.501873] Linux Plug and Play Support v0.97 (c) Adam Belay
[   32.501907] pnp: PnP ACPI init
[   32.501917] ACPI: bus type pnp registered
[   32.505560] pnp: PnP ACPI: found 13 devices
[   32.505563] ACPI: ACPI bus type pnp unregistered
[   32.505569] PnPBIOS: Disabled by ACPI PNP
[   32.505828] PCI: Using ACPI for IRQ routing
[   32.505831] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   32.532675] NET: Registered protocol family 8
[   32.532678] NET: Registered protocol family 20
[   32.532754] AppArmor: AppArmor Filesystem Enabled
[   32.536661] Time: tsc clocksource has been installed.
[   32.544695] system 00:00: iomem range 0x0-0x9ffff could not be reserved
[   32.544699] system 00:00: iomem range 0xf0000-0xfffff could not be reserved
[   32.544702] system 00:00: iomem range 0x100000-0x3fffffff could not be reserved
[   32.544706] system 00:00: iomem range 0xfec00000-0xfec000ff could not be reserved
[   32.544709] system 00:00: iomem range 0xfee00000-0xfee00fff could not be reserved
[   32.544718] system 00:02: ioport range 0xe400-0xe47f has been reserved
[   32.544720] system 00:02: ioport range 0xe480-0xe4ff has been reserved
[   32.544723] system 00:02: ioport range 0xe600-0xe61f has been reserved
[   32.544726] system 00:02: ioport range 0x480-0x48f has been reserved
[   32.544729] system 00:02: iomem range 0xffee0000-0xffefffff has been reserved
[   32.544736] system 00:03: iomem range 0xfffe0000-0xffffffff could not be reserved
[   32.544742] system 00:04: ioport range 0x4d0-0x4d1 has been reserved
[   32.544753] system 00:0c: ioport range 0x295-0x296 has been reserved
[   32.575167] PCI: Bridge: 0000:00:01.0
[   32.575170]   IO window: disabled.
[   32.575178]   MEM window: be000000-bfffffff
[   32.575183]   PREFETCH window: dff00000-febfffff
[   32.575202] PCI: Setting latency timer of device 0000:00:01.0 to 64
[   32.575216] NET: Registered protocol family 2
[   32.612618] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[   32.613013] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[   32.614088] TCP bind hash table entries: 65536 (order: 6, 262144 bytes)
[   32.614416] TCP: Hash tables configured (established 131072 bind 65536)
[   32.614419] TCP reno registered
[   32.624760] checking if image is initramfs... it is
[   33.075876] Switched to high resolution mode on CPU 0
[   33.305517] Freeing initrd memory: 7300k freed
[   33.305753] Simple Boot Flag at 0x3a set to 0x1
[   33.306191] audit: initializing netlink socket (disabled)
[   33.306211] audit(1224756381.320:1): initialized
[   33.306418] highmem bounce pool size: 64 pages
[   33.308372] VFS: Disk quotas dquot_6.5.1
[   33.308401] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   33.308556] io scheduler noop registered
[   33.308559] io scheduler anticipatory registered
[   33.308561] io scheduler deadline registered
[   33.308579] io scheduler cfq registered (default)
[   33.308643] Boot video device is 0000:01:00.0
[   33.308934] isapnp: Scanning for PnP cards...
[   33.662233] isapnp: No Plug & Play device found
[   33.693944] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   33.695245] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   33.695324] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[   33.695437] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[   33.695735] serio: i8042 KBD port at 0x60,0x64 irq 1
[   33.695740] serio: i8042 AUX port at 0x60,0x64 irq 12
[   33.707017] mice: PS/2 mouse device common for all mice
[   33.707149] EISA: Probing bus 0 at eisa.0
[   33.707177] Cannot allocate resource for EISA slot 7
[   33.707179] Cannot allocate resource for EISA slot 8
[   33.707181] EISA: Detected 0 cards.
[   33.707185] cpuidle: using governor ladder
[   33.707296] NET: Registered protocol family 1
[   33.707331] Using IPI Shortcut mode
[   33.707369] registered taskstats version 1
[   33.707481]   Magic number: 12:875:123
[   33.707625] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[   33.707627] EDD information not available.
[   33.708090] Freeing unused kernel memory: 364k freed
[   33.738834] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[   34.974322] fuse init (API version 7.9)
[   34.998503] ACPI: Invalid PBLK length [5]
[   35.628722] SCSI subsystem initialized
[   35.679079] sis900.c: v1.08.10 Apr. 2 2006
[   35.679134] PCI: Enabling device 0000:00:04.0 (0004 -> 0007)
[   35.679149] ACPI: PCI Interrupt 0000:00:04.0[A] -> GSI 19 (level, low) -> IRQ 16
[   35.680511] 0000:00:04.0: Realtek RTL8201 PHY transceiver found at address 1.
[   35.691340] 0000:00:04.0: Using transceiver found at address 1 as default
[   35.703899] usbcore: registered new interface driver usbfs
[   35.703928] usbcore: registered new interface driver hub
[   35.707448] 8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)
[   35.731838] usbcore: registered new device driver usb
[   35.733156] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
[   35.747336] libata version 3.00 loaded.
[   35.767945] eth0: SiS 900 PCI Fast Ethernet at 0x9800, IRQ 16, 00:e0:18:a2:45:46
[   35.768029] ACPI: PCI Interrupt 0000:00:03.0[A] -> GSI 20 (level, low) -> IRQ 20
[   35.768051] ohci_hcd 0000:00:03.0: OHCI Host Controller
[   35.768378] ohci_hcd 0000:00:03.0: new USB bus registered, assigned bus number 1
[   35.768396] ohci_hcd 0000:00:03.0: irq 20, io mem 0xbd000000
[   35.825786] usb usb1: configuration #1 chosen from 1 choice
[   35.825816] hub 1-0:1.0: USB hub found
[   35.825827] hub 1-0:1.0: 2 ports detected
[   35.927626] ACPI: PCI Interrupt 0000:00:03.1[B] -> GSI 21 (level, low) -> IRQ 17
[   35.927649] ohci_hcd 0000:00:03.1: OHCI Host Controller
[   35.927680] ohci_hcd 0000:00:03.1: new USB bus registered, assigned bus number 2
[   35.927697] ohci_hcd 0000:00:03.1: irq 17, io mem 0xbc800000
[   35.953970] Floppy drive(s): fd0 is 1.44M
[   35.972450] FDC 0 is a post-1991 82077
[   35.985523] usb usb2: configuration #1 chosen from 1 choice
[   35.985554] hub 2-0:1.0: USB hub found
[   35.985565] hub 2-0:1.0: 2 ports detected
[   36.087349] ACPI: PCI Interrupt 0000:00:03.2[C] -> GSI 22 (level, low) -> IRQ 18
[   36.087372] ohci_hcd 0000:00:03.2: OHCI Host Controller
[   36.087401] ohci_hcd 0000:00:03.2: new USB bus registered, assigned bus number 3
[   36.087418] ohci_hcd 0000:00:03.2: irq 18, io mem 0xbc000000
[   36.145308] usb usb3: configuration #1 chosen from 1 choice
[   36.145341] hub 3-0:1.0: USB hub found
[   36.145351] hub 3-0:1.0: 2 ports detected
[   36.231016] usb 1-1: new full speed USB device using ohci_hcd and address 2
[   36.247336] PCI: Enabling device 0000:00:03.3 (0004 -> 0006)
[   36.247352] ACPI: PCI Interrupt 0000:00:03.3[D] -> GSI 23 (level, low) -> IRQ 19
[   36.247369] ehci_hcd 0000:00:03.3: EHCI Host Controller
[   36.247403] ehci_hcd 0000:00:03.3: new USB bus registered, assigned bus number 4
[   36.247449] PCI: cache line size of 128 is not supported by device 0000:00:03.3
[   36.247458] ehci_hcd 0000:00:03.3: irq 19, io mem 0xbb800000
[   36.418715] ehci_hcd 0000:00:03.3: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   36.418873] usb usb4: configuration #1 chosen from 1 choice
[   36.418904] hub 4-0:1.0: USB hub found
[   36.418913] hub 4-0:1.0: 6 ports detected
[   36.522876] pata_sis 0000:00:02.5: version 0.5.2
[   36.522923] ACPI: PCI Interrupt 0000:00:02.5[A] -> GSI 16 (level, low) -> IRQ 21
[   36.524361] scsi0 : pata_sis
[   36.525418] scsi1 : pata_sis
[   36.525974] ata1: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xb400 irq 14
[   36.525978] ata2: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xb408 irq 15
[   36.814092] usb 1-1: device not accepting address 2, error -62
[   36.850411] ata1.00: ATA-5: MAXTOR 6L040J2, A93.0500, max UDMA/133
[   36.850415] ata1.00: 78177792 sectors, multi 16: LBA 
[   36.850441] ata1.01: ATAPI: _NEC DVD_RW ND-3500AG, 2.98, max UDMA/33
[   36.866413] ata1.00: configured for UDMA/133
[   37.030016] ata1.01: configured for UDMA/33
[   37.213786] ata2.01: ATA-7: SAMSUNG SP2514N, VF100-50, max UDMA/100
[   37.213791] ata2.01: 488397168 sectors, multi 16: LBA48 
[   37.245734] ata2.01: configured for UDMA/100
[   37.245880] scsi 0:0:0:0: Direct-Access     ATA      MAXTOR 6L040J2   A93. PQ: 0 ANSI: 5
[   37.247134] scsi 0:0:1:0: CD-ROM            _NEC     DVD_RW ND-3500AG 2.98 PQ: 0 ANSI: 5
[   37.247549] scsi 1:0:1:0: Direct-Access     ATA      SAMSUNG SP2514N  VF10 PQ: 0 ANSI: 5
[   37.252187] 8139cp 0000:00:0a.0: This (id 10ec:8139 rev 10) is not an 8139C+ compatible chip
[   37.252193] 8139cp 0000:00:0a.0: Try the "8139too" driver instead.
[   37.254708] 8139too Fast Ethernet driver 0.9.28
[   37.254758] PCI: Enabling device 0000:00:0a.0 (0004 -> 0007)
[   37.254772] ACPI: PCI Interrupt 0000:00:0a.0[A] -> GSI 18 (level, low) -> IRQ 22
[   37.255432] eth1: RealTek RTL8139 at 0x9400, 00:16:0a:07:a9:ae, IRQ 22
[   37.255435] eth1:  Identified 8139 chip type 'RTL-8100B/8139D'
[B][   37.256569] sata_sil 0000:00:0d.0: version 2.3
[   37.256627] ACPI: PCI Interrupt 0000:00:0d.0[A] -> GSI 17 (level, low) -> IRQ 23
[   37.258772] scsi2 : sata_sil
[   37.259446] scsi3 : sata_sil
[   37.259500] ata3: SATA max UDMA/100 mmio m512@0xb9000000 tf 0xb9000080 irq 23
[   37.259504] ata4: SATA max UDMA/100 mmio m512@0xb9000000 tf 0xb90000c0 irq 23[/B]
[   37.266604] Driver 'sd' needs updating - please use bus_type methods
[   37.269909] sd 0:0:0:0: [sda] 78177792 512-byte hardware sectors (40027 MB)
[   37.269928] sd 0:0:0:0: [sda] Write Protect is off
[   37.269931] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   37.269952] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   37.270025] sd 0:0:0:0: [sda] 78177792 512-byte hardware sectors (40027 MB)
[   37.270037] sd 0:0:0:0: [sda] Write Protect is off
[   37.270040] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   37.270058] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   37.270063]  sda:<4>Driver 'sr' needs updating - please use bus_type methods
[   37.280284]  sda3
[   37.280373] sd 0:0:0:0: [sda] Attached SCSI disk
[   37.280469] sd 1:0:1:0: [sdb] 488397168 512-byte hardware sectors (250059 MB)
[   37.280485] sd 1:0:1:0: [sdb] Write Protect is off
[   37.280487] sd 1:0:1:0: [sdb] Mode Sense: 00 3a 00 00
[   37.280507] sd 1:0:1:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   37.280557] sd 1:0:1:0: [sdb] 488397168 512-byte hardware sectors (250059 MB)
[   37.280569] sd 1:0:1:0: [sdb] Write Protect is off
[   37.280571] sd 1:0:1:0: [sdb] Mode Sense: 00 3a 00 00
[   37.280590] sd 1:0:1:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   37.280594]  sdb:sr0: scsi3-mmc drive: 48x/48x writer cd/rw xa/form2 cdda tray
[   37.284532] Uniform CD-ROM driver Revision: 3.20
[   37.284602] sr 0:0:1:0: Attached scsi CD-ROM sr0
[   37.289195]  sdb1 sdb2
[   37.289294] sd 1:0:1:0: [sdb] Attached SCSI disk
[   37.295743] sd 0:0:0:0: Attached scsi generic sg0 type 0
[   37.295769] sr 0:0:1:0: Attached scsi generic sg1 type 5
[   37.295789] sd 1:0:1:0: Attached scsi generic sg2 type 0
[   37.541004] usb 1-1: new full speed USB device using ohci_hcd and address 4
[B][   37.724716] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
[   37.733060] ata3.00: ATA-7: SAMSUNG HD502IJ, 1AA01110, max UDMA7
[   37.733064] ata3.00: 976773168 sectors, multi 16: LBA48 NCQ (depth 0/32)
[   37.741052] ata3.00: configured for UDMA/100[/B]
[   37.750758] usb 1-1: configuration #1 chosen from 1 choice
[   38.052201] ata4: SATA link down (SStatus 0 SControl 310)
[   38.052369] scsi 2:0:0:0: Direct-Access     ATA      SAMSUNG HD502IJ  1AA0 PQ: 0 ANSI: 5
[   38.052832] sd 2:0:0:0: [sdc] 976773168 512-byte hardware sectors (500108 MB)
[   38.052848] sd 2:0:0:0: [sdc] Write Protect is off
[   38.052851] sd 2:0:0:0: [sdc] Mode Sense: 00 3a 00 00
[   38.052871] sd 2:0:0:0: [sdc] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   38.052934] sd 2:0:0:0: [sdc] 976773168 512-byte hardware sectors (500108 MB)
[   38.052945] sd 2:0:0:0: [sdc] Write Protect is off
[   38.052948] sd 2:0:0:0: [sdc] Mode Sense: 00 3a 00 00
[   38.052966] sd 2:0:0:0: [sdc] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   38.052970]  sdc: sdc1 sdc2 sdc3 sdc4
[   38.076692] sd 2:0:0:0: [sdc] Attached SCSI disk
[   38.076739] sd 2:0:0:0: Attached scsi generic sg3 type 0
[   38.076954] PCI: Enabling device 0000:00:0b.0 (0014 -> 0016)
[   38.076963] ACPI: PCI Interrupt 0000:00:0b.0[A] -> GSI 19 (level, low) -> IRQ 16
[   38.127688] ohci1394: fw-host0: OHCI-1394 1.0 (PCI): IRQ=[16]  MMIO=[ba000000-ba0007ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[   38.403727] Attempting manual resume
[   38.403731] swsusp: Resume From Partition 8:34
[   38.403733] PM: Checking swsusp image.
[   38.403939] PM: Resume from disk failed.
[   38.429199] kjournald starting.  Commit interval 5 seconds
[   38.429217] EXT3-fs: mounted filesystem with ordered data mode.
[   39.426222] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[00309526100416f9]
[B][   43.578321] ata3.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2
[   43.578328] ata3.00: BMDMA2 stat 0x86d1309
[   43.578336] ata3.00: cmd c8/00:18:ff:b2:d9/00:00:00:00:00/e0 tag 0 dma 12288 in
[   43.578337]          res 00/13:64:00:08:13/00:00:00:00:00/64 Emask 0x2 (HSM violation)
[   43.578340] ata3.00: error: { IDNF }
[   43.887313] ata3: soft resetting link
[   44.043067] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
[   44.043190] ata3.00: revalidation failed (errno=-2)
[   44.043196] ata3: failed to recover some devices, retrying in 5 secs
[   49.039387] ata3: hard resetting link
[   49.514664] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
[   49.531005] ata3.00: configured for UDMA/100
[   49.531027] ata3: EH complete
[   49.559892] sd 2:0:0:0: [sdc] 976773168 512-byte hardware sectors (500108 MB)
[   49.560373] sd 2:0:0:0: [sdc] Write Protect is off
[   49.560377] sd 2:0:0:0: [sdc] Mode Sense: 00 3a 00 00
[   49.560413] sd 2:0:0:0: [sdc] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA[/B]
[   49.702751] input: PC Speaker as /devices/platform/pcspkr/input/input2
[   49.930165] Real Time Clock Driver v1.12ac
[   51.073913] PCI: Enabling device 0000:00:0c.1 (0004 -> 0005)
[   51.089499] gameport: EMU10K1 is pci0000:00:0c.1/gameport0, io 0x8800, speed 1125kHz
[   51.104121] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   51.121413] Linux agpgart interface v0.102
[   51.139807] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   51.158212] agpgart: Detected SiS chipset - id:1608
[   51.281142] agpgart: AGP aperture is 256M @ 0xc0000000
[   51.281177] sis96x_smbus 0000:00:02.1: SiS96x SMBus base address: 0xe600
[   51.482933] input: ImExPS/2 Generic Explorer Mouse as /devices/platform/i8042/serio1/input/input3
[   51.784050] input: Power Button (FF) as /devices/virtual/input/input4
[   51.811226] ACPI: Power Button (FF) [PWRF]
[   51.811326] input: Power Button (CM) as /devices/virtual/input/input5
[   51.843214] ACPI: Power Button (CM) [PWRB]
[   52.315524] eth1: link up, 100Mbps, full-duplex, lpa 0x41E1
[   52.726809] nvidia: module license 'NVIDIA' taints kernel.
[B][   53.149796] ata3.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2
[   53.149803] ata3.00: BMDMA2 stat 0x86d1309
[   53.149810] ata3.00: cmd c8/00:30:17:8e:f3/00:00:00:00:00/e0 tag 0 dma 24576 in
[   53.149811]          res 00/13:64:00:08:13/00:00:00:00:00/64 Emask 0x2 (HSM violation)
[   53.149814] ata3.00: error: { IDNF }
[   53.460622] ata3: soft resetting link
[   53.616402] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
[   53.616526] ata3.00: revalidation failed (errno=-2)
[   53.616531] ata3: failed to recover some devices, retrying in 5 secs[/B]
[   54.203893] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 21
[   54.204220] NVRM: loading NVIDIA UNIX x86 Kernel Module  169.12  Thu Feb 14 17:53:07 PST 2008
[B][   58.612734] ata3: hard resetting link
[   59.088012] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
[   59.104351] ata3.00: configured for UDMA/100
[   59.104373] ata3: EH complete[/B]
[   59.119145] sd 2:0:0:0: [sdc] 976773168 512-byte hardware sectors (500108 MB)
[   59.123498] sd 2:0:0:0: [sdc] Write Protect is off
[   59.123502] sd 2:0:0:0: [sdc] Mode Sense: 00 3a 00 00
[   59.127354] sd 2:0:0:0: [sdc] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   59.233401] Linux video capture interface: v2.00
[   59.282052] NET: Registered protocol family 17
[   59.291318] /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-386/media/gspcav1/gspca_core.c: USB GSPCA camera found. SONIX JPEG (sn9c1xx) 
[   59.299875] usbcore: registered new interface driver gspca
[   59.299883] /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-386/media/gspcav1/gspca_core.c: gspca driver 01.00.20 registered
[   59.337110] PCI: Enabling device 0000:00:0c.0 (0004 -> 0005)
[   59.337121] ACPI: PCI Interrupt 0000:00:0c.0[A] -> GSI 16 (level, low) -> IRQ 21
[   60.334372] lp: driver loaded but no devices found
[   60.560888] Adding 2096472k swap on /dev/sdc2.  Priority:-1 extents:1 across:2096472k
[   61.124776] EXT3 FS on sdc1, internal journal
[   62.487075] NET: Registered protocol family 10
[   62.487324] lo: Disabled Privacy Extensions
[   62.992806] kjournald starting.  Commit interval 5 seconds
[   62.992984] EXT3 FS on sdc3, internal journal
[   62.992989] EXT3-fs: mounted filesystem with ordered data mode.
[   63.009331] kjournald starting.  Commit interval 5 seconds
[   63.014201] EXT3 FS on sda3, internal journal
[   63.014206] EXT3-fs: mounted filesystem with ordered data mode.
[   63.042307] kjournald starting.  Commit interval 5 seconds
[   63.050069] EXT3 FS on sdb1, internal journal
[   63.050073] EXT3-fs: mounted filesystem with ordered data mode.
[   63.080117] kjournald starting.  Commit interval 5 seconds
[   63.080367] EXT3 FS on sdc4, internal journal
[   63.080371] EXT3-fs: mounted filesystem with ordered data mode.
[   63.115044] kjournald starting.  Commit interval 5 seconds
[   63.118024] EXT3 FS on sdb2, internal journal
[   63.118028] EXT3-fs: mounted filesystem with ordered data mode.
[   63.677454] ip_tables: (C) 2000-2006 Netfilter Core Team
[   65.595643] No dock devices found.
[   66.863391] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[   66.863398] apm: overridden by ACPI.
[   67.015166] ppdev: user-space parallel port driver
[   67.193062] audit(1224756415.485:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=5087 profile="/usr/sbin/cupsd" namespace="default"
[   67.942266] RPC: Registered udp transport module.
[   67.942273] RPC: Registered tcp transport module.
[   67.978215] Installing knfsd (copyright (C) 1996 [email]okir@monad.swb.de[/email]).
[   68.050595] NFSD: Using /var/lib/nfs/v4recovery as the NFSv4 state recovery directory
[   68.059144] NFSD: starting 90-second grace period
[   72.735126] eth1: no IPv6 routers present
[   74.392850] Bluetooth: Core ver 2.11
[   74.394830] NET: Registered protocol family 31
[   74.394836] Bluetooth: HCI device and connection manager initialized
[   74.394840] Bluetooth: HCI socket layer initialized
[   74.433651] Bluetooth: L2CAP ver 2.9
[   74.433659] Bluetooth: L2CAP socket layer initialized
[   74.508453] Bluetooth: RFCOMM socket layer initialized
[   74.508741] Bluetooth: RFCOMM TTY layer initialized
[   74.508745] Bluetooth: RFCOMM ver 1.8
[   76.262759] eth0: Media Link On 100mbps full-duplex 
[   76.468829] agpgart: Found an AGP 3.0 compliant device at 0000:00:00.0.
[   76.468856] agpgart: Putting AGP V3 device at 0000:00:00.0 into 4x mode
[   76.468861] agpgart: SiS delay workaround: giving bridge time to recover.
[   76.483314] agpgart: Putting AGP V3 device at 0000:01:00.0 into 4x mode
[   89.033894] eth0: no IPv6 routers present
[ 2282.652535] end_request: I/O error, dev fd0, sector 0
[ 2282.688478] end_request: I/O error, dev fd0, sector 0

---

### Post by j_alapeno on 2008-10-23
Hi I *was* getting similar errors with 8.4.1, but tried the 8.10 beta version which seems to have fixed what ever the issue with Samsung SATA discs was.

See [http://ubuntuforums.org/showthread.php?t=953028](http://ubuntuforums.org/showthread.php?t=953028)

---

### Post by Ashrael on 2008-10-24
thanks! i will try that soon... 
keep ya posted.

---

### Post by Ashrael on 2008-11-05
Installed the new ubuntu release(intrepid) and this did not make a difference, it still gives me errors and a lot of delay...BUT, I bought a new cable and replaced the one that came with my motherboard and now it's gone..
SO: check your cables if you get this error first...

HTH

---

