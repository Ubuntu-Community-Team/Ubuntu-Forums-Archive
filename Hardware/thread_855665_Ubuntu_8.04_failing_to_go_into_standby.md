---
title: "Ubuntu 8.04 failing to go into standby"
date: 2008-07-10
forum: Hardware
---

### Post by mark.earth on 2008-07-10
I have recently installed Ubuntu 8.04 and cannot get this desktop machine into suspend. (standby under Windows-XP worked fine).
After selecting System > Quit... > Suspend the screen fades to black for a few seconds and appears to attempt to turn off, but instead turns straight back on again and then hangs on a blank screen.
This machine has an NVIDA graphics card the proprietary drivers.
Attached are hopefully useful log files.
Thanks! Mark.

---

### Post by mark.earth on 2008-07-10
Forgot to include dmesg output...

[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.24-19-generic (buildd@palmer) (gcc version 4.2.3 (Ubuntu 4.2.3-2ubuntu7)) #1 SMP Wed Jun 18 14:43:41 UTC 2008 (Ubuntu 2.6.24-19.34-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
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
[    0.000000] ACPI: RSDP signature @ 0xC00F6000 checksum 0
[    0.000000] ACPI: RSDP 000F6000, 0014 (r0 ASUS  )
[    0.000000] ACPI: RSDT 3FFFC000, 0030 (r1 ASUS   A7V8X    42302E31 MSFT 31313031)
[    0.000000] ACPI: FACP 3FFFC0B2, 0074 (r1 ASUS   A7V8X    42302E31 MSFT 31313031)
[    0.000000] ACPI: DSDT 3FFFC126, 283E (r1   ASUS A7V8X        1000 MSFT  100000B)
[    0.000000] ACPI: FACS 3FFFF000, 0040
[    0.000000] ACPI: BOOT 3FFFC030, 0028 (r1 ASUS   A7V8X    42302E31 MSFT 31313031)
[    0.000000] ACPI: APIC 3FFFC058, 005A (r1 ASUS   A7V8X    42302E31 MSFT 31313031)
[    0.000000] ACPI: PM-Timer IO Port: 0xe408
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] Processor #0 6:8 APIC version 16
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 3, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl edge)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 low level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] Allocating PCI resources starting at 50000000 (gap: 40000000:bec00000)
[    0.000000] swsusp: Registered nosave memory region: 000000000009f000 - 00000000000a0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000a0000 - 00000000000f0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000f0000 - 0000000000100000
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 260093
[    0.000000] Kernel command line: root=UUID=3acb21f0-cc42-4e76-946a-77bf8eafbbbe ro quiet splash
[    0.000000] mapped APIC to ffffb000 (fee00000)
[    0.000000] mapped IOAPIC to ffffa000 (fec00000)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] Detected 2166.580 MHz processor.
[   21.809631] Console: colour VGA+ 80x25
[   21.809635] console [tty0] enabled
[   21.810470] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[   21.811833] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[   21.848491] Memory: 1027032k/1048560k available (2177k kernel code, 20868k reserved, 1006k data, 368k init, 131056k highmem)
[   21.848499] virtual kernel memory layout:
[   21.848500]     fixmap  : 0xfff4b000 - 0xfffff000   ( 720 kB)
[   21.848501]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   21.848502]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
[   21.848503]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
[   21.848505]       .init : 0xc0421000 - 0xc047d000   ( 368 kB)
[   21.848506]       .data : 0xc0320434 - 0xc041bdc4   (1006 kB)
[   21.848507]       .text : 0xc0100000 - 0xc0320434   (2177 kB)
[   21.848510] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   21.848564] SLUB: Genslabs=11, HWalign=32, Order=0-1, MinObjects=4, CPUs=1, Nodes=1
[   21.928481] Calibrating delay using timer specific routine.. 4336.94 BogoMIPS (lpj=8673893)
[   21.928520] Security Framework initialized
[   21.928530] SELinux:  Disabled at boot.
[   21.928556] AppArmor: AppArmor initialized
[   21.928562] Failure registering capabilities with primary security module.
[   21.928573] Mount-cache hash table entries: 512
[   21.928741] Initializing cgroup subsys ns
[   21.928747] Initializing cgroup subsys cpuacct
[   21.928759] CPU: After generic identify, caps: 0383fbff c1c3fbff 00000000 00000000 00000000 00000000 00000000 00000000
[   21.928769] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[   21.928771] CPU: L2 Cache: 256K (64 bytes/line)
[   21.928775] CPU: After all inits, caps: 0383fbff c1c3fbff 00000000 00000420 00000000 00000000 00000000 00000000
[   21.928787] Compat vDSO mapped to ffffe000.
[   21.928804] Checking 'hlt' instruction... OK.
[   21.944731] SMP alternatives: switching to UP code
[   21.945870] Freeing SMP alternatives: 11k freed
[   21.946017] Early unpacking initramfs... done
[   22.271652] ACPI: Core revision 20070126
[   22.271734] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[   22.275142] CPU0: AMD Athlon(TM) XP 2700+ stepping 01
[   22.275166] Total of 1 processors activated (4336.94 BogoMIPS).
[   22.275871] ENABLING IO-APIC IRQs
[   22.276192] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[   22.419888] Brought up 1 CPUs
[   22.419955] CPU0 attaching sched-domain:
[   22.419958]  domain 0: span 01
[   22.419959]   groups: 01
[   22.420181] net_namespace: 64 bytes
[   22.420189] Booting paravirtualized kernel on bare hardware
[   22.420643] Time: 20:51:01  Date: 07/10/08
[   22.420680] NET: Registered protocol family 16
[   22.420905] EISA bus registered
[   22.420934] ACPI: bus type pci registered
[   22.422143] PCI: PCI BIOS revision 2.10 entry at 0xf1a90, last bus=1
[   22.422146] PCI: Using configuration type 1
[   22.422154] Setting up standard PCI resources
[   22.433462] ACPI: EC: Look up EC in DSDT
[   22.437962] ACPI: Interpreter enabled
[   22.437965] ACPI: (supports S0 S1 S3 S4 S5)
[   22.437980] ACPI: Using IOAPIC for interrupt routing
[   22.447956] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   22.448462] PCI quirk: region e400-e47f claimed by vt8235 PM
[   22.448466] PCI quirk: region e800-e80f claimed by vt8235 SMB
[   22.448694] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   22.448851] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCI1._PRT]
[   22.510727] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 9 10 *11 12)
[   22.510793] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 9 10 11 12) *0, disabled.
[   22.510857] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 9 10 11 12) *0, disabled.
[   22.510919] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 9 10 11 12) *0, disabled.
[   22.510990] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 *6 7 9 10 11 12)
[   22.511083] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 *9 10 11 12)
[   22.511194] Linux Plug and Play Support v0.97 (c) Adam Belay
[   22.511230] pnp: PnP ACPI init
[   22.511240] ACPI: bus type pnp registered
[   22.514949] pnp: PnP ACPI: found 14 devices
[   22.514952] ACPI: ACPI bus type pnp unregistered
[   22.514957] PnPBIOS: Disabled by ACPI PNP
[   22.515222] PCI: Using ACPI for IRQ routing
[   22.515226] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   22.535681] NET: Registered protocol family 8
[   22.535684] NET: Registered protocol family 20
[   22.535770] AppArmor: AppArmor Filesystem Enabled
[   22.539667] Time: tsc clocksource has been installed.
[   22.547698] system 00:00: iomem range 0x0-0x9ffff could not be reserved
[   22.547702] system 00:00: iomem range 0xf0000-0xfffff could not be reserved
[   22.547705] system 00:00: iomem range 0x100000-0x3fffffff could not be reserved
[   22.547708] system 00:00: iomem range 0xfec00000-0xfec000ff could not be reserved
[   22.547710] system 00:00: iomem range 0xfee00000-0xfee00fff could not be reserved
[   22.547718] system 00:02: ioport range 0xe400-0xe47f has been reserved
[   22.547721] system 00:02: ioport range 0xe800-0xe81f could not be reserved
[   22.547724] system 00:02: iomem range 0xfff80000-0xffffffff could not be reserved
[   22.547727] system 00:02: iomem range 0xffb80000-0xffbfffff has been reserved
[   22.547733] system 00:03: ioport range 0x4d0-0x4d1 has been reserved
[   22.547744] system 00:0d: ioport range 0x290-0x291 has been reserved
[   22.547747] system 00:0d: ioport range 0x370-0x372 has been reserved
[   22.578170] PCI: Bridge: 0000:00:01.0
[   22.578172]   IO window: disabled.
[   22.578177]   MEM window: db000000-dddfffff
[   22.578181]   PREFETCH window: dff00000-efffffff
[   22.578203] PCI: Setting latency timer of device 0000:00:01.0 to 64
[   22.578215] NET: Registered protocol family 2
[   22.615673] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[   22.616063] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[   22.617982] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[   22.618945] TCP: Hash tables configured (established 131072 bind 65536)
[   22.618949] TCP reno registered
[   22.627721] checking if image is initramfs... it is
[   23.078957] Switched to high resolution mode on CPU 0
[   23.237497] Freeing initrd memory: 7732k freed
[   23.237700] Simple Boot Flag at 0x3a set to 0x1
[   23.238261] audit: initializing netlink socket (disabled)
[   23.238278] audit(1215723061.284:1): initialized
[   23.238454] highmem bounce pool size: 64 pages
[   23.240417] VFS: Disk quotas dquot_6.5.1
[   23.240499] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   23.240650] io scheduler noop registered
[   23.240652] io scheduler anticipatory registered
[   23.240654] io scheduler deadline registered
[   23.240665] io scheduler cfq registered (default)
[   23.240694] PCI: VIA PCI bridge detected. Disabling DAC.
[   23.240763] Boot video device is 0000:01:00.0
[   23.241062] isapnp: Scanning for PnP cards...
[   23.594162] isapnp: No Plug & Play device found
[   23.623843] Real Time Clock Driver v1.12ac
[   23.623959] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   23.624080] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   23.624204] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[   23.624801] 00:09: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   23.625170] 00:0a: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[   23.626018] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   23.626090] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[   23.626216] PNP: PS/2 Controller [PNP0303:PS2K] at 0x60,0x64 irq 1
[   23.626219] PNP: PS/2 appears to have AUX port disabled, if this is incorrect please boot with i8042.nopnp
[   23.626789] serio: i8042 KBD port at 0x60,0x64 irq 1
[   23.630567] mice: PS/2 mouse device common for all mice
[   23.630709] EISA: Probing bus 0 at eisa.0
[   23.630744] EISA: Detected 0 cards.
[   23.630747] cpuidle: using governor ladder
[   23.630749] cpuidle: using governor menu
[   23.630903] NET: Registered protocol family 1
[   23.630937] Using IPI No-Shortcut mode
[   23.630974] registered taskstats version 1
[   23.631076]   Magic number: 0:219:902
[   23.631204]   hash matches device ptyvf
[   23.631287] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[   23.631289] EDD information not available.
[   23.631779] Freeing unused kernel memory: 368k freed
[   23.658125] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[   24.876133] fuse init (API version 7.9)
[   25.455747] PCI: Enabling device 0000:00:09.0 (0004 -> 0006)
[   25.455761] ACPI: PCI Interrupt 0000:00:09.0[A] -> GSI 18 (level, low) -> IRQ 16
[   25.475581] ssb: Core 0 found: Fast Ethernet (cc 0x806, rev 0x04, vendor 0x4243)
[   25.475590] ssb: Core 1 found: V90 (cc 0x807, rev 0x01, vendor 0x4243)
[   25.475595] ssb: Core 2 found: PCI (cc 0x804, rev 0x02, vendor 0x4243)
[   25.479601] e100: Intel(R) PRO/100 Network Driver, 3.5.23-k4-NAPI
[   25.479604] e100: Copyright(c) 1999-2006 Intel Corporation
[   25.519611] ssb: Sonics Silicon Backplane found on PCI device 0000:00:09.0
[   25.519650] b44.c:v2.0
[   25.539796] eth0: Broadcom 44xx/47xx 10/100BaseT Ethernet 00:e0:18:e4:84:c4
[   25.539843] PCI: Enabling device 0000:00:0d.0 (0004 -> 0007)
[   25.539855] ACPI: PCI Interrupt 0000:00:0d.0[A] -> GSI 16 (level, low) -> IRQ 17
[   25.560445] usbcore: registered new interface driver usbfs
[   25.560471] usbcore: registered new interface driver hub
[   25.570106] e100: eth1: e100_probe: addr 0xde000000, irq 17, MAC addr 00:20:35:22:29:64
[   25.570140] PCI: Enabling device 0000:00:0f.0 (0014 -> 0017)
[   25.570148] ACPI: PCI Interrupt 0000:00:0f.0[A] -> GSI 18 (level, low) -> IRQ 16
[   25.622890] ohci1394: fw-host0: OHCI-1394 1.0 (PCI): IRQ=[16]  MMIO=[d9800000-d98007ff]  Max Packet=[2048]  IR/IT contexts=[8/8]
[   25.651372] usbcore: registered new device driver usb
[   25.676782] SCSI subsystem initialized
[   25.691305] USB Universal Host Controller Interface driver v3.0
[   25.735209] libata version 3.00 loaded.
[   25.790554] ACPI: PCI Interrupt 0000:00:10.0[A] -> GSI 21 (level, low) -> IRQ 18
[   25.790570] uhci_hcd 0000:00:10.0: UHCI Host Controller
[   25.790939] uhci_hcd 0000:00:10.0: new USB bus registered, assigned bus number 1
[   25.790976] uhci_hcd 0000:00:10.0: irq 18, io base 0x0000d000
[   25.791193] usb usb1: configuration #1 chosen from 1 choice
[   25.791219] hub 1-0:1.0: USB hub found
[   25.791227] hub 1-0:1.0: 2 ports detected
[   25.895141] ACPI: PCI Interrupt 0000:00:10.1[B] -> GSI 21 (level, low) -> IRQ 18
[   25.895157] uhci_hcd 0000:00:10.1: UHCI Host Controller
[   25.895190] uhci_hcd 0000:00:10.1: new USB bus registered, assigned bus number 2
[   25.895213] uhci_hcd 0000:00:10.1: irq 18, io base 0x0000b800
[   25.895332] usb usb2: configuration #1 chosen from 1 choice
[   25.895355] hub 2-0:1.0: USB hub found
[   25.895362] hub 2-0:1.0: 2 ports detected
[   25.998991] ACPI: PCI Interrupt 0000:00:10.2[C] -> GSI 21 (level, low) -> IRQ 18
[   25.999006] uhci_hcd 0000:00:10.2: UHCI Host Controller
[   25.999037] uhci_hcd 0000:00:10.2: new USB bus registered, assigned bus number 3
[   25.999061] uhci_hcd 0000:00:10.2: irq 18, io base 0x0000b400
[   25.999183] usb usb3: configuration #1 chosen from 1 choice
[   25.999208] hub 3-0:1.0: USB hub found
[   25.999215] hub 3-0:1.0: 2 ports detected
[   26.103000] ACPI: PCI Interrupt 0000:00:10.3[D] -> GSI 21 (level, low) -> IRQ 18
[   26.103017] ehci_hcd 0000:00:10.3: EHCI Host Controller
[   26.103054] ehci_hcd 0000:00:10.3: new USB bus registered, assigned bus number 4
[   26.103101] ehci_hcd 0000:00:10.3: irq 18, io mem 0xd9000000
[   26.114726] ehci_hcd 0000:00:10.3: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   26.114924] usb usb4: configuration #1 chosen from 1 choice
[   26.114954] hub 4-0:1.0: USB hub found
[   26.114963] hub 4-0:1.0: 6 ports detected
[   26.218813] ACPI: Unable to derive IRQ for device 0000:00:11.1
[   26.218893] ACPI: Unable to derive IRQ for device 0000:00:11.1
[   26.222990] pata_via 0000:00:11.1: version 0.3.3
[   26.223025] ACPI: Unable to derive IRQ for device 0000:00:11.1
[   26.225422] scsi0 : pata_via
[   26.226558] scsi1 : pata_via
[   26.227000] ata1: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xb000 irq 14
[   26.227003] ata2: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xb008 irq 15
[   26.390828] ata1.00: ATA-7: Maxtor 6Y200P0, YAR41VW0, max UDMA/133
[   26.390835] ata1.00: 398297088 sectors, multi 16: LBA48 
[   26.390847] ata1.00: limited to UDMA/33 due to 40-wire cable
[   26.406671] ata1.00: configured for UDMA/33
[   26.850083] ata2.01: ATAPI: JLMS DVD-ROM LTD-165H, CH0U, max UDMA/44
[   27.005725] ata2.01: configured for UDMA/44
[   27.005877] scsi 0:0:0:0: Direct-Access     ATA      Maxtor 6Y200P0   YAR4 PQ: 0 ANSI: 5
[   27.006577] scsi 1:0:1:0: CD-ROM            JLMS     DVD-ROM LTD-165H CH0U PQ: 0 ANSI: 5
[   27.021131] Driver 'sd' needs updating - please use bus_type methods
[   27.021243] sd 0:0:0:0: [sda] 398297088 512-byte hardware sectors (203928 MB)
[   27.021259] sd 0:0:0:0: [sda] Write Protect is off
[   27.021261] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   27.021279] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   27.021329] sd 0:0:0:0: [sda] 398297088 512-byte hardware sectors (203928 MB)
[   27.021339] sd 0:0:0:0: [sda] Write Protect is off
[   27.021341] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   27.021356] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   27.021360]  sda: sda1 sda2 <<4>Driver 'sr' needs updating - please use bus_type methods
[   27.045834]  sda5 > sda3
[   27.045964] sd 0:0:0:0: [sda] Attached SCSI disk
[   27.053591] sd 0:0:0:0: Attached scsi generic sg0 type 0
[   27.053614] sr 1:0:1:0: Attached scsi generic sg1 type 5
[   27.054881] sr0: scsi3-mmc drive: 48x/48x cd/rw xa/form2 cdda tray
[   27.054889] Uniform CD-ROM driver Revision: 3.20
[   27.054954] sr 1:0:1:0: Attached scsi CD-ROM sr0
[   27.059155] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[0090e60088880654]
[   27.312670] Attempting manual resume
[   27.312675] swsusp: Resume From Partition 8:5
[   27.312677] PM: Checking swsusp image.
[   27.313055] PM: Resume from disk failed.
[   27.352130] kjournald starting.  Commit interval 5 seconds
[   27.352151] EXT3-fs: mounted filesystem with ordered data mode.
[   27.420847] usb 4-4: new high speed USB device using ehci_hcd and address 4
[   27.553997] usb 4-4: configuration #1 chosen from 1 choice
[   27.554291] hub 4-4:1.0: USB hub found
[   27.554636] hub 4-4:1.0: 4 ports detected
[   27.896174] usb 1-2: new low speed USB device using uhci_hcd and address 2
[   28.051579] usb 1-2: configuration #1 chosen from 1 choice
[   28.291617] usb 2-1: new full speed USB device using uhci_hcd and address 2
[   28.462314] usb 2-1: configuration #1 chosen from 1 choice
[   28.663406] usb 4-4.1: new high speed USB device using ehci_hcd and address 5
[   28.756285] usb 4-4.1: configuration #1 chosen from 1 choice
[   28.756544] hub 4-4.1:1.0: USB hub found
[   28.756892] hub 4-4.1:1.0: 4 ports detected
[   29.058836] usb 4-4.3: new full speed USB device using ehci_hcd and address 6
[   29.188634] usb 4-4.3: configuration #1 chosen from 1 choice
[   37.079410] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   37.151390] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   37.199199] Linux agpgart interface v0.102
[   37.462811] Linux video capture interface: v2.00
[   37.522793] agpgart: Detected VIA KT400/KT400A/KT600 chipset
[   37.530303] agpgart: AGP aperture is 128M @ 0xf0000000
[   37.830315] irda_init()
[   37.830345] NET: Registered protocol family 23
[   37.874875] input: Power Button (FF) as /devices/virtual/input/input2
[   37.890191] ACPI: Power Button (FF) [PWRF]
[   37.890345] input: Power Button (CM) as /devices/virtual/input/input3
[   37.906152] ACPI: Power Button (CM) [PWRB]
[   38.423035] bttv: driver version 0.9.17 loaded
[   38.423042] bttv: using 8 buffers with 2080k (520 pages) each for capture
[   38.423125] bttv: Bt8xx card found (0).
[   38.423138] PCI: Enabling device 0000:00:0b.0 (0004 -> 0006)
[   38.423151] ACPI: PCI Interrupt 0000:00:0b.0[A] -> GSI 19 (level, low) -> IRQ 19
[   38.423164] bttv0: Bt878 (rev 2) at 0000:00:0b.0, irq: 19, latency: 32, mmio: 0xdf000000
[   38.423245] bttv0: detected: Hauppauge WinTV [card=10], PCI subsystem ID is 0070:13eb
[   38.423249] bttv0: using: Hauppauge (bt878) [card=10,autodetected]
[   38.423285] bttv0: gpio: en=00000000, out=00000000 in=00fffffb [init]
[   38.425769] bttv0: Hauppauge/Voodoo msp34xx: reset line init [5]
[   38.451981] tveeprom 1-0050: Hauppauge model 38105, rev B235, serial# 3724392
[   38.451984] tveeprom 1-0050: tuner model is Temic 4066FY5 (idx 35, type 18)
[   38.451987] tveeprom 1-0050: TV standards PAL(I) (eeprom 0x10)
[   38.451990] tveeprom 1-0050: audio processor is None (idx 0)
[   38.451992] tveeprom 1-0050: has no radio
[   38.451994] bttv0: Hauppauge eeprom indicates model#38105
[   38.451997] bttv0: tuner type=18
[   38.453680] bttv0: i2c: checking for MSP34xx @ 0x80... not found
[   38.454740] bttv0: i2c: checking for TDA9875 @ 0xb0... not found
[   38.455232] bttv0: i2c: checking for TDA7432 @ 0x8a... not found
[   38.717240] input: PC Speaker as /devices/platform/pcspkr/input/input4
[   39.239739] nvidia: module license 'NVIDIA' taints kernel.
[   39.773916] tuner 1-0061: chip found @ 0xc2 (bt878 #0 [sw])
[   39.773958] tuner-simple 1-0061: type set to 18 (Temic PAL_I (4066 FY5))
[   39.773961] tuner 1-0061: type set to Temic PAL_I (4066 F
[   39.773965] tuner-simple 1-0061: type set to 18 (Temic PAL_I (4066 FY5))
[   39.773967] tuner 1-0061: type set to Temic PAL_I (4066 F
[   39.900142] bttv0: registered device video0
[   39.900166] bttv0: registered device vbi0
[   39.900188] bttv0: PLL: 28636363 => 35468950 .. ok
[   39.932490] ACPI: PCI Interrupt 0000:00:11.5[C] -> GSI 22 (level, low) -> IRQ 20
[   39.932833] PCI: Setting latency timer of device 0000:00:11.5 to 64
[   40.181203] /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-generic/media/gspcav1/gspca_core.c: USB GSPCA camera found. (SPCA501 )
[   40.450664] PCI: Enabling device 0000:00:0b.1 (0004 -> 0006)
[   40.450676] ACPI: PCI Interrupt 0000:00:0b.1[A] -> GSI 19 (level, low) -> IRQ 19
[   40.451119] ALSA /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-generic/sound/alsa-driver/pci/bt87x.c:947: bt87x0: Using board 1, analog, digital (rate 32000 Hz)
[   40.488257] usbcore: registered new interface driver gspca
[   40.488266] /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-generic/media/gspcav1/gspca_core.c: gspca driver 01.00.20 registered
[   40.488338] usbcore: registered new interface driver hiddev
[   40.501030] input: HID 04b3:310b as /devices/pci0000:00/0000:00:10.0/usb1/1-2/1-2:1.0/input/input5
[   40.514590] input,hidraw0: USB HID v1.00 Mouse [HID 04b3:310b] on usb-0000:00:10.0-2
[   40.514621] usbcore: registered new interface driver usbhid
[   40.514626] /build/buildd/linux-2.6.24/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
[   40.522533] bt878: AUDIO driver version 0.0.0 loaded
[   40.666490] usblp0: USB Bidirectional printer dev 6 if 0 alt 1 proto 2 vid 0x03F0 pid 0x1004
[   40.666514] usbcore: registered new interface driver usblp
[   40.832624] parport_pc 00:08: reported by Plug and Play ACPI
[   40.832669] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
[   40.922518] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 17
[   40.923021] NVRM: loading NVIDIA UNIX x86 Kernel Module  169.12  Thu Feb 14 17:53:07 PST 2008
[   43.133838] lp0: using parport0 (interrupt-driven).
[   43.234672] Adding 3028212k swap on /dev/sda5.  Priority:-1 extents:1 across:3028212k
[   43.810896] EXT3 FS on sda1, internal journal
[   44.004805] device-mapper: uevent: version 1.0.3
[   44.004844] device-mapper: ioctl: 4.12.0-ioctl (2007-10-02) initialised: [email]dm-devel@redhat.com[/email]
[   44.807490] kjournald starting.  Commit interval 5 seconds
[   44.807804] EXT3 FS on sda3, internal journal
[   44.807810] EXT3-fs: mounted filesystem with ordered data mode.
[   45.304781] ip_tables: (C) 2000-2006 Netfilter Core Team
[   45.777028] No dock devices found.
[   47.008081] apm: BIOS version 1.2 Flags 0x0b (Driver version 1.16ac)
[   47.008088] apm: overridden by ACPI.
[   47.142830] ppdev: user-space parallel port driver
[   47.271170] NET: Registered protocol family 10
[   47.271709] lo: Disabled Privacy Extensions
[   47.367945] audit(1215723086.344:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=4967 profile="/usr/sbin/cupsd" namespace="default"
[   49.345248] ADDRCONF(NETDEV_UP): eth1: link is not ready
[   49.379988] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   49.560926] Bluetooth: Core ver 2.11
[   49.561831] NET: Registered protocol family 31
[   49.561837] Bluetooth: HCI device and connection manager initialized
[   49.561842] Bluetooth: HCI socket layer initialized
[   49.660206] Bluetooth: L2CAP ver 2.9
[   49.660213] Bluetooth: L2CAP socket layer initialized
[   49.675972] Bluetooth: RFCOMM socket layer initialized
[   49.676274] Bluetooth: RFCOMM TTY layer initialized
[   49.676278] Bluetooth: RFCOMM ver 1.8
[   52.725516] b44: eth0: Link is up at 100 Mbps, full duplex.
[   52.725523] b44: eth0: Flow control is off for TX and off for RX.
[   52.761366] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   52.786830] NVRM: not using NVAGP, an AGPGART backend is loaded!
[   55.141218] NET: Registered protocol family 17
[   67.379822] eth0: no IPv6 routers present
[  376.268714] atkbd.c: Unknown key pressed (translated set 2, code 0xa3 on isa0060/serio0).
[  376.268722] atkbd.c: Use 'setkeycodes e023 <keycode>' to make it known.
[  376.545210] atkbd.c: Unknown key released (translated set 2, code 0xa3 on isa0060/serio0).
[  376.545218] atkbd.c: Use 'setkeycodes e023 <keycode>' to make it known.
[  376.770266] atkbd.c: Unknown key pressed (translated set 2, code 0xa3 on isa0060/serio0).
[  376.770274] atkbd.c: Use 'setkeycodes e023 <keycode>' to make it known.
[  376.941180] atkbd.c: Unknown key released (translated set 2, code 0xa3 on isa0060/serio0).
[  376.941188] atkbd.c: Use 'setkeycodes e023 <keycode>' to make it known.

---

