---
title: "Freezing after upgrade to 8.04 on laptop"
date: 2008-07-05
forum: Hardware
---

### Post by Christobevii3 on 2008-07-05
On my laptop now, i'm getting a decent amount of complete lockups after it goes into a blank screen mode from being idle.  Moving the mouse, banging on the keyboard, and the power button are all unresponsive to bring it back up.  I've just had to manually power it down and start it back up now to get it going again.

Last night it looked to have frozen about an hour after i went to bed.

The motherboard uses an sis chipset and videocard, amd turion, etc.  Is there a log that I can look at that might tell me or is this just an xorg problem causing it?

Thanks

---

### Post by apswartz on 2008-07-05
```
cd /var/log
less Xorg.0.log
```

after that try...
```
dmesg
```

---

### Post by Christobevii3 on 2008-07-05
I didn't see much in the xorg log, except that it says since i have onboard sis graphics on an amd platform with shared memory that most features are disabled.

Here's the dmesg

```
dmesg
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.24-19-generic (buildd@yellow) (gcc version 4.2.3 (Ubuntu 4.2.3-2ubuntu7)) #1 SMP Wed Jun 18 14:15:37 UTC 2008 (Ubuntu 2.6.24-19.34-generic)
[    0.000000] Command line: root=UUID=cae74848-9873-46e7-be08-e21e2344eb34 ro quiet splash
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 0000000057fd0000 (usable)
[    0.000000]  BIOS-e820: 0000000057fd0000 - 0000000057fdf000 (ACPI data)
[    0.000000]  BIOS-e820: 0000000057fdf000 - 0000000058000000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000ff780000 - 0000000100000000 (reserved)
[    0.000000] Entering add_active_range(0, 0, 159) 0 entries of 3200 used
[    0.000000] Entering add_active_range(0, 256, 360400) 1 entries of 3200 used
[    0.000000] end_pfn_map = 1048576
[    0.000000] DMI 2.3 present.
[    0.000000] ACPI: RSDP signature @ 0xFFFF8100000F7220 checksum 0
[    0.000000] ACPI: RSDP 000F7220, 0014 (r0 MSI   )
[    0.000000] ACPI: RSDT 57FD0000, 0030 (r1 MSI    1011      9282005 MSFT       97)
[    0.000000] ACPI: FACP 57FD0200, 0081 (r2 MSI    1011      9282005 MSFT       97)
[    0.000000] ACPI: DSDT 57FD03F0, 350F (r1    MSI     1011  9282005 INTL  2002026)
[    0.000000] ACPI: FACS 57FDF000, 0040
[    0.000000] ACPI: APIC 57FD0390, 0054 (r1 MSI    OEMAPIC   9282005 MSFT       97)
[    0.000000] ACPI: OEMB 57FDF040, 0041 (r1 MSI    AMI_OEM   9282005 MSFT       97)
[    0.000000] Scanning NUMA topology in Northbridge 24
[    0.000000] CPU has 1 num_cores
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at 0000000000000000-0000000057fd0000
[    0.000000] Entering add_active_range(0, 0, 159) 0 entries of 3200 used
[    0.000000] Entering add_active_range(0, 256, 360400) 1 entries of 3200 used
[    0.000000] Bootmem setup node 0 0000000000000000-0000000057fd0000
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   DMA32        4096 ->  1048576
[    0.000000]   Normal    1048576 ->  1048576
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[2] active PFN ranges
[    0.000000]     0:        0 ->      159
[    0.000000]     0:      256 ->   360400
[    0.000000] On node 0 totalpages: 360303
[    0.000000]   DMA zone: 56 pages used for memmap
[    0.000000]   DMA zone: 1220 pages reserved
[    0.000000]   DMA zone: 2723 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 4871 pages used for memmap
[    0.000000]   DMA32 zone: 351433 pages, LIFO batch:31
[    0.000000]   Normal zone: 0 pages used for memmap
[    0.000000]   Movable zone: 0 pages used for memmap
[    0.000000] ACPI: PM-Timer IO Port: 0x808
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] Processor #0 (Bootup-CPU)
[    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 1, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 low level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Setting APIC routing to flat
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] swsusp: Registered nosave memory region: 000000000009f000 - 00000000000a0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000a0000 - 00000000000e0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000e0000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 60000000 (gap: 58000000:a7780000)
[    0.000000] SMP: Allowing 1 CPUs, 0 hotplug CPUs
[    0.000000] PERCPU: Allocating 34656 bytes of per cpu data
[    0.000000] Built 1 zonelists in Node order, mobility grouping on.  Total pages: 354156
[    0.000000] Policy zone: DMA32
[    0.000000] Kernel command line: root=UUID=cae74848-9873-46e7-be08-e21e2344eb34 ro quiet splash
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 32768 bytes)
[    0.000000] TSC calibrated against PM_TIMER
[    9.026547] time.c: Detected 1800.063 MHz processor.
[    9.027269] Console: colour VGA+ 80x25
[    9.027273] console [tty0] enabled
[    9.027290] Checking aperture...
[    9.027294] CPU 0: aperture @ e0000000 size 64 MB
[    9.053002] Memory: 1408504k/1441600k available (2489k kernel code, 32708k reserved, 1318k data, 320k init)
[    9.053055] SLUB: Genslabs=12, HWalign=64, Order=0-1, MinObjects=4, CPUs=1, Nodes=1
[    9.132383] Calibrating delay using timer specific routine.. 3602.04 BogoMIPS (lpj=7204094)
[    9.132432] Security Framework initialized
[    9.132442] SELinux:  Disabled at boot.
[    9.132462] AppArmor: AppArmor initialized
[    9.132467] Failure registering capabilities with primary security module.
[    9.132662] Dentry cache hash table entries: 262144 (order: 9, 2097152 bytes)
[    9.135464] Inode-cache hash table entries: 131072 (order: 8, 1048576 bytes)
[    9.136882] Mount-cache hash table entries: 256
[    9.137083] Initializing cgroup subsys ns
[    9.137088] Initializing cgroup subsys cpuacct
[    9.137105] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[    9.137107] CPU: L2 Cache: 512K (64 bytes/line)
[    9.137110] CPU 0/0 -> Node 0
[    9.137139] SMP alternatives: switching to UP code
[    9.137789] Freeing SMP alternatives: 24k freed
[    9.138374] Early unpacking initramfs... done
[    9.499787] ACPI: Core revision 20070126
[    9.499851] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[    9.542137] Using local APIC timer interrupts.
[    9.597610] APIC timer calibration result 12500443
[    9.597612] Detected 12.500 MHz APIC timer.
[    9.597674] Brought up 1 CPUs
[    9.597728] CPU0 attaching sched-domain:
[    9.597731]  domain 0: span 01
[    9.597733]   groups: 01
[    9.597910] net_namespace: 120 bytes
[    9.598320] Time: 14:01:54  Date: 07/05/08
[    9.598361] NET: Registered protocol family 16
[    9.598545] ACPI: bus type pci registered
[    9.598612] PCI: Using configuration type 1
[    9.600519] ACPI: EC: Look up EC in DSDT
[    9.602064] ACPI: Interpreter enabled
[    9.602067] ACPI: (supports S0 S1 S3 S4 S5)
[    9.602081] ACPI: Using IOAPIC for interrupt routing
[    9.604661] ACPI: EC: non-query interrupt received, switching to interrupt mode
[    9.607888] ACPI: EC: GPE = 0x1a, I/O: command/status = 0x66, data = 0x62
[    9.607890] ACPI: EC: driver started in interrupt mode
[    9.607970] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    9.608113] Enabling SiS 96x SMBus.
[    9.608598] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    9.608704] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P1._PRT]
[    9.615801] ACPI: PCI Interrupt Link [LNKA] (IRQs 4 5 6 7 10 11 12 14 15) *0, disabled.
[    9.615888] ACPI: PCI Interrupt Link [LNKB] (IRQs 4 5 6 7 10 11 12 14 15) *0, disabled.
[    9.615972] ACPI: PCI Interrupt Link [LNKC] (IRQs 4 5 6 7 10 *11 12 14 15)
[    9.616059] ACPI: PCI Interrupt Link [LNKD] (IRQs *4 5 6 7 10 11 12 14 15)
[    9.616144] ACPI: PCI Interrupt Link [LNKE] (IRQs 4 5 6 *7 10 11 12 14 15)
[    9.616229] ACPI: PCI Interrupt Link [LNKF] (IRQs 4 *5 6 7 10 11 12 14 15)
[    9.616314] ACPI: PCI Interrupt Link [LNKG] (IRQs 4 5 6 7 10 11 12 14 15) *0, disabled.
[    9.616398] ACPI: PCI Interrupt Link [LNKH] (IRQs 4 5 6 7 *10 11 12 14 15)
[    9.616500] Linux Plug and Play Support v0.97 (c) Adam Belay
[    9.616530] pnp: PnP ACPI init
[    9.616538] ACPI: bus type pnp registered
[    9.617647] pnp: PnP ACPI: found 9 devices
[    9.617650] ACPI: ACPI bus type pnp unregistered
[    9.617895] PCI: Using ACPI for IRQ routing
[    9.617899] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[    9.617911] PCI: Cannot allocate resource region 0 of device 0000:00:00.0
[    9.633585] NET: Registered protocol family 8
[    9.633587] NET: Registered protocol family 20
[    9.633653] agpgart: Detected AGP bridge 0
[    9.636513] agpgart: AGP aperture is 64M @ 0xe0000000
[    9.636593] AppArmor: AppArmor Filesystem Enabled
[    9.637567] Time: tsc clocksource has been installed.
[    9.645599] system 00:07: ioport range 0x480-0x48f has been reserved
[    9.645602] system 00:07: ioport range 0x4d0-0x4d1 has been reserved
[    9.645605] system 00:07: ioport range 0x800-0x87f has been reserved
[    9.645607] system 00:07: ioport range 0x880-0x8ff has been reserved
[    9.645610] system 00:07: ioport range 0xc00-0xc1f has been reserved
[    9.645615] system 00:07: iomem range 0xfff80000-0xffffffff could not be reserved
[    9.645617] system 00:07: iomem range 0xffe80000-0xffefffff could not be reserved
[    9.645620] system 00:07: iomem range 0xfed00000-0xfed003ff has been reserved
[    9.645627] system 00:08: iomem range 0xffb80000-0xffbfffff could not be reserved
[    9.645630] system 00:08: iomem range 0xfec00000-0xfec00fff has been reserved
[    9.645633] system 00:08: iomem range 0xfee00000-0xfee00fff could not be reserved
[    9.646013] PCI: Bridge: 0000:00:01.0
[    9.646016]   IO window: c000-cfff
[    9.646019]   MEM window: dfe00000-dfefffff
[    9.646022]   PREFETCH window: cfd00000-dfcfffff
[    9.646026] PCI: Bus 2, cardbus bridge: 0000:00:0a.0
[    9.646029]   IO window: 00001000-000010ff
[    9.646032]   IO window: 00001400-000014ff
[    9.646035]   PREFETCH window: 60000000-63ffffff
[    9.646038]   MEM window: 64000000-67ffffff
[    9.646067] ACPI: PCI Interrupt 0000:00:0a.0[A] -> GSI 17 (level, low) -> IRQ 17
[    9.646072] PCI: Setting latency timer of device 0000:00:0a.0 to 64
[    9.646114] NET: Registered protocol family 2
[    9.681610] IP route cache hash table entries: 65536 (order: 7, 524288 bytes)
[    9.682610] TCP established hash table entries: 262144 (order: 10, 4194304 bytes)
[    9.688138] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    9.689523] TCP: Hash tables configured (established 262144 bind 65536)
[    9.689527] TCP reno registered
[    9.701665] checking if image is initramfs... it is
[   10.148786] Switched to high resolution mode on CPU 0
[   10.396366] Freeing initrd memory: 7945k freed
[   10.406763] audit: initializing netlink socket (disabled)
[   10.406779] audit(1215266514.332:1): initialized
[   10.408802] VFS: Disk quotas dquot_6.5.1
[   10.408884] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[   10.409034] io scheduler noop registered
[   10.409037] io scheduler anticipatory registered
[   10.409038] io scheduler deadline registered
[   10.409144] io scheduler cfq registered (default)
[   10.456491] Boot video device is 0000:01:00.0
[   10.484571] Real Time Clock Driver v1.12ac
[   10.484669] Linux agpgart interface v0.102
[   10.484672] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   10.485145] ACPI: PCI Interrupt 0000:00:02.6[C] -> GSI 18 (level, low) -> IRQ 18
[   10.485153] ACPI: PCI interrupt for device 0000:00:02.6 disabled
[   10.485745] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   10.485812] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[   10.485897] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f03:PS2M] at 0x60,0x64 irq 1,12
[   10.494384] i8042.c: Detected active multiplexing controller, rev 1.1.
[   10.498357] serio: i8042 KBD port at 0x60,0x64 irq 1
[   10.498361] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[   10.498363] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[   10.498365] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[   10.498367] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[   10.508244] mice: PS/2 mouse device common for all mice
[   10.508279] cpuidle: using governor ladder
[   10.508281] cpuidle: using governor menu
[   10.508438] NET: Registered protocol family 1
[   10.508548] registered taskstats version 1
[   10.508660]   Magic number: 0:825:29
[   10.508669]   hash matches device ttydc
[   10.508808] /build/buildd/linux-2.6.24/drivers/rtc/hctosys.c: unable to open rtc device (rtc0)
[   10.508811] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[   10.508813] EDD information not available.
[   10.508822] Freeing unused kernel memory: 320k freed
[   10.516027] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[   11.717200] fuse init (API version 7.9)
[   11.747361] ACPI: Thermal Zone [THRM] (56 C)
[   12.309616] SCSI subsystem initialized
[   12.361248] libata version 3.00 loaded.
[   12.375193] usbcore: registered new interface driver usbfs
[   12.375217] usbcore: registered new interface driver hub
[   12.391339] usbcore: registered new device driver usb
[   12.401243] sis900.c: v1.08.10 Apr. 2 2006
[   12.403078] ACPI: PCI Interrupt 0000:00:04.0[A] -> GSI 19 (level, low) -> IRQ 19
[   12.404228] 0000:00:04.0: Realtek RTL8201 PHY transceiver found at address 1.
[   12.413858] 0000:00:04.0: Using transceiver found at address 1 as default
[   12.414664] eth0: SiS 900 PCI Fast Ethernet at 0xd800, IRQ 19, 00:0c:76:f7:f2:b5
[   12.446041] pata_sis 0000:00:02.5: version 0.5.2
[   12.458680] scsi0 : pata_sis
[   12.469522] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
[   12.477629] scsi1 : pata_sis
[   12.478225] ata1: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xffa0 irq 14
[   12.478229] ata2: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xffa8 irq 15
[   12.641127] ata1.00: ATA-6: TOSHIBA MK6026GAX, PA202G, max UDMA/100
[   12.641132] ata1.00: 117210240 sectors, multi 16: LBA 
[   12.641143] ata1.00: limited to UDMA/33 due to 40-wire cable
[   12.649147] ata1.00: configured for UDMA/33
[   12.968542] ata2.00: ATAPI: HL-DT-STCD-RW/DVD DRIVE GCC-4244N, 1.00, max UDMA/33
[   13.140231] ata2.00: configured for UDMA/33
[   13.140359] scsi 0:0:0:0: Direct-Access     ATA      TOSHIBA MK6026GA PA20 PQ: 0 ANSI: 5
[   13.144340] scsi 1:0:0:0: CD-ROM            HL-DT-ST RW/DVD GCC-4244N 1.00 PQ: 0 ANSI: 5
[   13.144544] ACPI: PCI Interrupt 0000:00:03.0[A] -> GSI 20 (level, low) -> IRQ 20
[   13.144695] ohci_hcd 0000:00:03.0: OHCI Host Controller
[   13.144971] ohci_hcd 0000:00:03.0: new USB bus registered, assigned bus number 1
[   13.144995] ohci_hcd 0000:00:03.0: irq 20, io mem 0xdfffd000
[   13.153950] Driver 'sd' needs updating - please use bus_type methods
[   13.154044] sd 0:0:0:0: [sda] 117210240 512-byte hardware sectors (60012 MB)
[   13.154055] sd 0:0:0:0: [sda] Write Protect is off
[   13.154058] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   13.154072] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   13.154118] sd 0:0:0:0: [sda] 117210240 512-byte hardware sectors (60012 MB)
[   13.154126] sd 0:0:0:0: [sda] Write Protect is off
[   13.154128] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   13.154141] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   13.154146]  sda:<4>Driver 'sr' needs updating - please use bus_type methods
[   13.202060] usb usb1: configuration #1 chosen from 1 choice
[   13.202087] hub 1-0:1.0: USB hub found
[   13.202095] hub 1-0:1.0: 3 ports detected
[   13.211612]  sda1 sda2 < sda5 >
[   13.239933] sd 0:0:0:0: [sda] Attached SCSI disk
[   13.245603] sd 0:0:0:0: Attached scsi generic sg0 type 0
[   13.245624] sr 1:0:0:0: Attached scsi generic sg1 type 5
[   13.260040] sr0: scsi3-mmc drive: 24x/24x writer cd/rw xa/form2 cdda tray
[   13.260047] Uniform CD-ROM driver Revision: 3.20
[   13.260100] sr 1:0:0:0: Attached scsi CD-ROM sr0
[   13.303929] ACPI: PCI Interrupt 0000:00:03.1[B] -> GSI 21 (level, low) -> IRQ 21
[   13.304116] ohci_hcd 0000:00:03.1: OHCI Host Controller
[   13.304185] ohci_hcd 0000:00:03.1: new USB bus registered, assigned bus number 2
[   13.304205] ohci_hcd 0000:00:03.1: irq 21, io mem 0xdfffe000
[   13.361819] usb usb2: configuration #1 chosen from 1 choice
[   13.361845] hub 2-0:1.0: USB hub found
[   13.361854] hub 2-0:1.0: 3 ports detected
[   13.419789] Attempting manual resume
[   13.419793] swsusp: Resume From Partition 8:5
[   13.419795] PM: Checking swsusp image.
[   13.420110] PM: Resume from disk failed.
[   13.435734] EXT3-fs: INFO: recovery required on readonly filesystem.
[   13.435740] EXT3-fs: write access will be enabled during recovery.
[   13.463749] ACPI: PCI Interrupt 0000:00:03.3[D] -> GSI 23 (level, low) -> IRQ 23
[   13.463905] ehci_hcd 0000:00:03.3: EHCI Host Controller
[   13.463973] ehci_hcd 0000:00:03.3: new USB bus registered, assigned bus number 3
[   13.464010] PCI: cache line size of 64 is not supported by device 0000:00:03.3
[   13.464021] ehci_hcd 0000:00:03.3: irq 23, io mem 0xdffff000
[   13.475527] ehci_hcd 0000:00:03.3: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   13.475657] usb usb3: configuration #1 chosen from 1 choice
[   13.475679] hub 3-0:1.0: USB hub found
[   13.475687] hub 3-0:1.0: 6 ports detected
[   25.656135] kjournald starting.  Commit interval 5 seconds
[   25.656162] EXT3-fs: sda1: orphan cleanup on readonly fs
[   25.656171] ext3_orphan_cleanup: deleting unreferenced inode 1212580
[   25.718530] ext3_orphan_cleanup: deleting unreferenced inode 1212571
[   25.718540] ext3_orphan_cleanup: deleting unreferenced inode 1212575
[   25.718549] ext3_orphan_cleanup: deleting unreferenced inode 1212581
[   25.718557] ext3_orphan_cleanup: deleting unreferenced inode 1212584
[   25.718565] ext3_orphan_cleanup: deleting unreferenced inode 1212582
[   25.718574] ext3_orphan_cleanup: deleting unreferenced inode 1212520
[   25.718582] ext3_orphan_cleanup: deleting unreferenced inode 1212578
[   25.718591] ext3_orphan_cleanup: deleting unreferenced inode 1212574
[   25.718598] ext3_orphan_cleanup: deleting unreferenced inode 1212524
[   25.718606] ext3_orphan_cleanup: deleting unreferenced inode 1212523
[   25.718614] ext3_orphan_cleanup: deleting unreferenced inode 1212522
[   25.718623] ext3_orphan_cleanup: deleting unreferenced inode 1212570
[   25.718631] ext3_orphan_cleanup: deleting unreferenced inode 1212558
[   25.718639] ext3_orphan_cleanup: deleting unreferenced inode 1212521
[   25.718648] ext3_orphan_cleanup: deleting unreferenced inode 1212519
[   25.718658] ext3_orphan_cleanup: deleting unreferenced inode 1213200
[   25.718666] ext3_orphan_cleanup: deleting unreferenced inode 1212585
[   25.718676] ext3_orphan_cleanup: deleting unreferenced inode 1212572
[   25.718694] ext3_orphan_cleanup: deleting unreferenced inode 1212579
[   25.718702] ext3_orphan_cleanup: deleting unreferenced inode 1212577
[   25.747598] ext3_orphan_cleanup: deleting unreferenced inode 1212542
[   25.747607] ext3_orphan_cleanup: deleting unreferenced inode 1212538
[   25.747616] ext3_orphan_cleanup: deleting unreferenced inode 1212518
[   25.747629] ext3_orphan_cleanup: deleting unreferenced inode 1212474
[   25.747654] ext3_orphan_cleanup: deleting unreferenced inode 1212437
[   25.747666] ext3_orphan_cleanup: deleting unreferenced inode 540686
[   25.826388] ext3_orphan_cleanup: deleting unreferenced inode 541063
[   25.941307] ext3_orphan_cleanup: deleting unreferenced inode 6602831
[   25.986663] ext3_orphan_cleanup: deleting unreferenced inode 3326037
[   25.986671] EXT3-fs: sda1: 30 orphan inodes deleted
[   25.986673] EXT3-fs: recovery complete.
[   26.001356] EXT3-fs: mounted filesystem with ordered data mode.
[   38.752969] input: PC Speaker as /devices/platform/pcspkr/input/input2
[   39.122878] Yenta: CardBus bridge found at 0000:00:0a.0 [1462:0111]
[   39.122894] Yenta: Enabling burst memory read transactions
[   39.122897] Yenta: Using CSCINT to route CSC interrupts to PCI
[   39.122899] Yenta: Routing CardBus interrupts to PCI
[   39.122903] Yenta TI: socket 0000:00:0a.0, mfunc 0x00001002, devctl 0x44
[   39.324354] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   39.355187] Yenta: ISA IRQ mask 0x0830, PCI irq 17
[   39.355192] Socket status: 30000006
[   39.434550] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   39.474262] ieee80211_crypt: registered algorithm 'NULL'
[   39.659453] sis96x_smbus 0000:00:02.1: SiS96x SMBus base address: 0x0c00
[   39.688225] input: Power Button (FF) as /devices/virtual/input/input3
[   39.713898] ACPI: Power Button (FF) [PWRF]
[   39.713978] input: Lid Switch as /devices/virtual/input/input4
[   39.729921] ACPI: Lid Switch [LID0]
[   39.729986] input: Sleep Button (CM) as /devices/virtual/input/input5
[   39.757824] ACPI: Sleep Button (CM) [SLPB]
[   39.757883] input: Power Button (CM) as /devices/virtual/input/input6
[   39.773851] ACPI: PCI Interrupt 0000:00:0e.0[A] -> GSI 18 (level, low) -> IRQ 18
[   39.774135] hostap_pci: Registered netdevice wifi0
[   39.774151] wifi0: Original COR value: 0x0
[   39.785762] ACPI: Power Button (CM) [PWRB]
[   39.981578] prism2_hw_init: initialized in 204 ms
[   39.982454] wifi0: NIC: id=0x8013 v1.0.0
[   39.982603] wifi0: PRI: id=0x15 v1.1.0
[   39.983186] wifi0: STA: id=0x1f v1.4.9
[   39.995511] wifi0: defaulting to bogus WDS frame as a workaround for firmware bug in Host AP mode WDS
[   40.053254] wifi0: Intersil Prism2.5 PCI: mem=0xdfdff000, irq=18
[   40.053569] wifi0: registered netdevice wlan0
[   40.354075] input: PS/2 Mouse as /devices/virtual/input/input7
[   40.399798] input: AlpsPS/2 ALPS GlidePoint as /devices/platform/i8042/serio1/input/input8
[   40.534259] eth0: Media Link Off
[   41.053481] ACPI: AC Adapter [ADP1] (on-line)
[   41.103740] ACPI: PCI Interrupt 0000:00:02.7[C] -> GSI 18 (level, low) -> IRQ 18
[   41.351427] ACPI: Battery Slot [BAT1] (battery present)
[   41.930346] intel8x0_measure_ac97_clock: measured 55435 usecs
[   41.930351] intel8x0: clocking to 48000
[   42.161119] NET: Registered protocol family 17
[   43.153053] lp: driver loaded but no devices found
[   43.408239] Adding 1301224k swap on /dev/sda5.  Priority:-1 extents:1 across:1301224k
[   43.961753] EXT3 FS on sda1, internal journal
[   44.107853] device-mapper: uevent: version 1.0.3
[   44.107887] device-mapper: ioctl: 4.12.0-ioctl (2007-10-02) initialised: dm-devel@redhat.com
[   45.713053] ip_tables: (C) 2000-2006 Netfilter Core Team
[   49.341398] No dock devices found.
[   49.785010] powernow-k8: Found 1 AMD Turion(tm) 64 Mobile Technology MT-32 processors (1 cpu cores) (version 2.20.00)
[   49.785057] powernow-k8:    0 : fid 0xa (1800 MHz), vid 0xa
[   49.785059] powernow-k8:    1 : fid 0x8 (1600 MHz), vid 0xc
[   49.785062] powernow-k8:    2 : fid 0x0 (800 MHz), vid 0x13
[   49.785099] powernow-k8: ph2 null fid transition 0xa
[   51.170432] ppdev: user-space parallel port driver
[   51.576278] audit(1215266556.571:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=4952 profile="/usr/sbin/cupsd" namespace="default"
[   51.966824] RPC: Registered udp transport module.
[   51.966830] RPC: Registered tcp transport module.
[   52.115603] Installing knfsd (copyright (C) 1996 okir@monad.swb.de).
[   52.196754] NFSD: Using /var/lib/nfs/v4recovery as the NFSv4 state recovery directory
[   52.213084] NFSD: starting 90-second grace period
[   53.476127] Marking TSC unstable due to cpufreq changes
[   53.479994] Time: acpi_pm clocksource has been installed.
[   53.744489] Clocksource tsc unstable (delta = -277781024 ns)
[   57.479292] wifi0: LinkStatus=2 (Disconnected)
[   57.479558] wifi0: LinkStatus: BSSID=44:44:44:44:44:44
[   57.608192] Bluetooth: Core ver 2.11
[   57.608928] NET: Registered protocol family 31
[   57.608933] Bluetooth: HCI device and connection manager initialized
[   57.608937] Bluetooth: HCI socket layer initialized
[   57.633015] Bluetooth: L2CAP ver 2.9
[   57.633020] Bluetooth: L2CAP socket layer initialized
[   57.766787] Bluetooth: RFCOMM socket layer initialized
[   57.766810] Bluetooth: RFCOMM TTY layer initialized
[   57.766812] Bluetooth: RFCOMM ver 1.8
[   58.752903] wifi0: LinkStatus=1 (Connected)
[   58.753171] wifi0: LinkStatus: BSSID=00:18:f3:70:5d:cc
[   69.816251] NET: Registered protocol family 10
[   69.816631] lo: Disabled Privacy Extensions
[   69.817130] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   74.313658] wlan0: no IPv6 routers present
[   79.438445] ieee80211_crypt: registered algorithm 'WEP'
[   79.754333] wifi0: CMD=0x0121 => res=0x7f, resp0=0x0004
[   79.754341] wifi0: hfa384x_set_rid: CMDCODE_ACCESS_WRITE failed (res=127, rid=fc48, len=2)
[   79.756397] wifi0: LinkStatus=2 (Disconnected)
[   79.777154] wifi0: LinkStatus: BSSID=44:44:44:44:44:44
[   79.779108] wifi0: LinkStatus=2 (Disconnected)
[   79.789522] wlan0: Preferred AP (SIOCSIWAP) is used only in Managed mode when host_roaming is enabled
[   79.816416] wifi0: LinkStatus: BSSID=44:44:44:44:44:44
[   80.459581] wifi0: LinkStatus=1 (Connected)
[   80.459962] wifi0: LinkStatus: BSSID=00:18:f3:70:5d:cc
[   99.664481] wlan0: no IPv6 routers present

```

---

### Post by apswartz on 2008-07-05
try...
```
less /var/log/messages
```
and scroll through it looking for errors, especially segfaults.

---

### Post by Christobevii3 on 2008-07-09
It seems that as long as i leave firefox closed it hasn't been locking up.  I guess i give up :confused:

---

### Post by apswartz on 2008-07-10
How many plugins do you use with Firefox?

I found that plugins occasionally conflict with each other or are just buggy enough by themselves to cause problems.

If you use plugins you may want to try disabling this all and then installing one and using it for a while. If no problems, install a second, and so on.

---

