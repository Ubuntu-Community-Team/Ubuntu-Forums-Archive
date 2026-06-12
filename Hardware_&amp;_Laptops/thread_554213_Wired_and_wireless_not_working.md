---
title: "Wired and wireless not working"
date: 2007-09-18
forum: Hardware &amp; Laptops
---

### Post by Super TWiT on 2007-09-18
I am working on a friend's computer.  He says that the wireless is working on XP and has asked me how to get it working.  The wired connection we figured out doesn't work either on Ubuntu.  I don't remember if he said it was working or not.  I copied and pasted the output of dmesg from the laptop.  I can't even figure out what the what the wireless card is.  Here is the output from dmesg ```
[    0.000000] Linux version 2.6.20-15-generic (root@palmer) (gcc version 4.1.2 (Ubuntu 4.1.2-0ubuntu4)) #2 SMP Sun Apr 15 07:36:31 UTC 2007 (Ubuntu 2.6.20-15.27-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000] sanitize start
[    0.000000] sanitize end
[    0.000000] copy_e820_map() start: 0000000000000000 size: 000000000009fc00 end: 000000000009fc00 type: 1
[    0.000000] copy_e820_map() type is E820_RAM
[    0.000000] copy_e820_map() start: 000000000009fc00 size: 0000000000000400 end: 00000000000a0000 type: 2
[    0.000000] copy_e820_map() start: 0000000000100000 size: 0000000027ee2800 end: 0000000027fe2800 type: 1
[    0.000000] copy_e820_map() type is E820_RAM
[    0.000000] copy_e820_map() start: 0000000027fe2800 size: 000000000001d800 end: 0000000028000000 type: 2
[    0.000000] copy_e820_map() start: 00000000feda0000 size: 0000000000060000 end: 00000000fee00000 type: 2
[    0.000000] copy_e820_map() start: 00000000ffb80000 size: 0000000000480000 end: 0000000100000000 type: 2
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 0000000027fe2800 (usable)
[    0.000000]  BIOS-e820: 0000000027fe2800 - 0000000028000000 (reserved)
[    0.000000]  BIOS-e820: 00000000feda0000 - 00000000fee00000 (reserved)
[    0.000000]  BIOS-e820: 00000000ffb80000 - 0000000100000000 (reserved)
[    0.000000] 0MB HIGHMEM available.
[    0.000000] 639MB LOWMEM available.
[    0.000000] Entering add_active_range(0, 0, 163810) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   163810
[    0.000000]   HighMem    163810 ->   163810
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   163810
[    0.000000] On node 0 totalpages: 163810
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 1247 pages used for memmap
[    0.000000]   Normal zone: 158467 pages, LIFO batch:31
[    0.000000]   HighMem zone: 0 pages used for memmap
[    0.000000] DMI 2.3 present.
[    0.000000] ACPI: RSDP (v000 DELL                                  ) @ 0x000fde50
[    0.000000] ACPI: RSDT (v001 DELL    CPi R   0x27d40107 ASL  0x00000061) @ 0x000fde64
[    0.000000] ACPI: FADT (v001 DELL    CPi R   0x27d40107 ASL  0x00000061) @ 0x000fde90
[    0.000000] ACPI: DSDT (v001 INT430 SYSFexxx 0x00001001 MSFT 0x0100000e) @ 0x00000000
[    0.000000] ACPI: PM-Timer IO Port: 0x808
[    0.000000] Allocating PCI resources starting at 30000000 (gap: 28000000:d6da0000)
[    0.000000] Detected 1695.033 MHz processor.
[    8.337393] Built 1 zonelists.  Total pages: 162531
[    8.337400] Kernel command line: root=UUID=065ef24c-a563-438d-ad3b-a554b9bcb7ec ro quiet splash
[    8.337657] Local APIC disabled by BIOS -- you can enable it with "lapic"
[    8.337669] mapped APIC to ffffd000 (0150c000)
[    8.337674] Enabling fast FPU save and restore... done.
[    8.337680] Enabling unmasked SIMD FPU exception support... done.
[    8.337699] Initializing CPU#0
[    8.337807] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    8.340281] Console: colour VGA+ 80x25
[    8.341231] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    8.342258] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    8.366696] Memory: 638272k/655240k available (1992k kernel code, 16404k reserved, 893k data, 328k init, 0k highmem)
[    8.366711] virtual kernel memory layout:
[    8.366712]     fixmap  : 0xfff4e000 - 0xfffff000   ( 708 kB)
[    8.366714]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[    8.366716]     vmalloc : 0xe8800000 - 0xff7fe000   ( 367 MB)
[    8.366718]     lowmem  : 0xc0000000 - 0xe7fe2000   ( 639 MB)
[    8.366720]       .init : 0xc03d7000 - 0xc0429000   ( 328 kB)
[    8.366722]       .data : 0xc02f2264 - 0xc03d16d4   ( 893 kB)
[    8.366723]       .text : 0xc0100000 - 0xc02f2264   (1992 kB)
[    8.366728] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[    8.445797] Calibrating delay using timer specific routine.. 3393.65 BogoMIPS (lpj=6787310)
[    8.445865] Security Framework v1.0.0 initialized
[    8.445875] SELinux:  Disabled at boot.
[    8.445902] Mount-cache hash table entries: 512
[    8.446133] CPU: After generic identify, caps: 3febf9ff 00000000 00000000 00000000 00000000 00000000 00000000
[    8.446153] CPU: Trace cache: 12K uops, L1 D cache: 8K
[    8.446157] CPU: L2 cache: 512K
[    8.446161] CPU: Hyper-Threading is disabled
[    8.446164] CPU: After all inits, caps: 3febf9ff 00000000 00000000 00003080 00000000 00000000 00000000
[    8.446182] Compat vDSO mapped to ffffe000.
[    8.446187] Remapping vsyscall page to ffffe000
[    8.446206] Checking 'hlt' instruction... OK.
[    8.461999] SMP alternatives: switching to UP code
[    8.462332] Freeing SMP alternatives: 11k freed
[    8.462691] Early unpacking initramfs... done
[    8.943489] ACPI: Core revision 20060707
[    8.949646] ACPI: Looking for DSDT in initramfs... file /DSDT.aml not found, using machine DSDT.
[    8.985925] ACPI: setting ELCR to 0200 (from 0800)
[    8.988490] CPU0: Intel(R) Pentium(R) 4 Mobile CPU 1.70GHz stepping 04
[    8.988500] SMP motherboard not detected.
[    8.988504] Local APIC not detected. Using dummy APIC emulation.
[    8.988562] Brought up 1 CPUs
[    8.988992] Booting paravirtualized kernel on bare hardware
[    8.989083] Time: 10:45:34  Date: 08/18/107
[    8.989135] NET: Registered protocol family 16
[    8.989285] EISA bus registered[
[    8.989293] ACPI: bus type pci registered
[    9.016306] PCI: PCI BIOS revision 2.10 entry at 0xfbfee, last bus=2
[    9.016310] PCI: Using configuration type 1
[    9.016313] Setting up standard PCI resources
[    9.046572] ACPI: Interpreter enabled
[    9.046578] ACPI: Using PIC for interrupt routing
[    9.048055] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    9.048070] PCI: Probing PCI hardware (bus 00)
[    9.048436] ACPI: Assume root bridge [\_SB_.PCI0] bus is 0
[    9.085024] PCI quirk: region 0800-087f claimed by ICH4 ACPI/GPIO/TCO
[    9.085030] PCI quirk: region 0880-08bf claimed by ICH4 GPIO
[    9.085345] Boot video device is 0000:01:00.0
[    9.085715] PCI: Transparent bridge - 0000:00:1e.0
[    9.085896] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    9.210796] ACPI: PCI Interrupt Link [LNKA] (IRQs 9 10 *11)
[    9.211835] ACPI: PCI Interrupt Link [LNKB] (IRQs 5 7) *11
[    9.212860] ACPI: PCI Interrupt Link [LNKC] (IRQs 9 10 *11)
[    9.213902] ACPI: PCI Interrupt Link [LNKD] (IRQs 5 7 9 10 *11)
[    9.217008] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.AGP_._PRT]
[    9.217371] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIE._PRT]
[    9.219004] ACPI: Power Resource [PADA] (on)
[    9.219381] Linux Plug and Play Support v0.97 (c) Adam Belay
[    9.219399] pnp: PnP ACPI init
[    9.433756] pnp: PnP ACPI: found 17 devices
[    9.433765] PnPBIOS: Disabled by ACPI PNP
[    9.433856] PCI: Using ACPI for IRQ routing
[    9.433861] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[    9.442476] NET: Registered protocol family 8
[    9.442480] NET: Registered protocol family 20
[    9.474170] pnp: 00:02: ioport range 0x4d0-0x4d1 has been reserved
[    9.474181] pnp: 00:02: ioport range 0x800-0x805 could not be reserved
[    9.474185] pnp: 00:02: ioport range 0x808-0x80f could not be reserved
[    9.474195] pnp: 00:03: ioport range 0x806-0x807 has been reserved
[    9.474200] pnp: 00:03: ioport range 0x810-0x85f could not be reserved
[    9.474204] pnp: 00:03: ioport range 0x860-0x87f has been reserved
[    9.474208] pnp: 00:03: ioport range 0x880-0x8bf has been reserved
[    9.474212] pnp: 00:03: ioport range 0x8c0-0x8df has been reserved
[    9.474216] pnp: 00:03: ioport range 0x8e0-0x8ff has been reserved
[    9.474225] pnp: 00:04: ioport range 0xf000-0xf0fe has been reserved
[    9.474229] pnp: 00:04: ioport range 0xf100-0xf1fe has been reserved
[    9.474233] pnp: 00:04: ioport range 0xf200-0xf2fe has been reserved
[    9.474237] pnp: 00:04: ioport range 0xf400-0xf4fe has been reserved
[    9.474241] pnp: 00:04: ioport range 0xf500-0xf5fe has been reserved
[    9.474245] pnp: 00:04: ioport range 0xf600-0xf6fe has been reserved
[    9.474249] pnp: 00:04: ioport range 0xf800-0xf8fe has been reserved
[    9.474253] pnp: 00:04: ioport range 0xf900-0xf9fe has been reserved
[    9.474266] pnp: 00:09: ioport range 0x900-0x91f has been reserved
[    9.474269] pnp: 00:09: ioport range 0x3f0-0x3f1 has been reserved
[    9.474283] pnp: 00:0f: ioport range 0xbf40-0xbf5f has been reserved
[    9.474778] PCI: Bridge: 0000:00:01.0
[    9.474783]   IO window: c000-cfff
[    9.474789]   MEM window: fc000000-fdffffff
[    9.474794]   PREFETCH window: e0000000-e7ffffff
[    9.474816] PCI: Bus 3, cardbus bridge: 0000:02:01.0
[    9.474820]   IO window: 0000e000-0000e0ff
[    9.474826]   IO window: 0000e400-0000e4ff
[    9.474832]   PREFETCH window: 30000000-33ffffff
[    9.474838]   MEM window: f4000000-f7ffffff
[    9.474844] PCI: Bus 7, cardbus bridge: 0000:02:01.1
[    9.474847]   IO window: 0000e800-0000e8ff
[    9.474852]   IO window: 00001000-000010ff
[    9.474858]   PREFETCH window: 34000000-37ffffff
[    9.474865]   MEM window: 3c000000-3fffffff
[    9.474870] PCI: Bridge: 0000:00:1e.0
[    9.474875]   IO window: e000-ffff
[    9.474882]   MEM window: f4000000-fbffffff
[    9.474888]   PREFETCH window: 30000000-39ffffff
[    9.474912] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[    9.474931] PCI: Enabling device 0000:02:01.0 (0000 -> 0003)
[    9.475811] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 11
[    9.475816] PCI: setting IRQ 11 as level-triggered
[    9.475821] ACPI: PCI Interrupt 0000:02:01.0[A] -> Link [LNKD] -> GSI 11 (level, low) -> IRQ 11
[    9.475846] PCI: Enabling device 0000:02:01.1 (0000 -> 0003)
[    9.475851] ACPI: PCI Interrupt 0000:02:01.1[A] -> Link [LNKD] -> GSI 11 (level, low) -> IRQ 11
[    9.475905] NET: Registered protocol family 2
[    9.509747] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    9.510070] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    9.511563] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    9.512520] TCP: Hash tables configured (established 131072 bind 65536)
[    9.512527] TCP reno registered
[    9.521887] checking if image is initramfs... it is
[   10.475233] Freeing initrd memory: 6789k freed
[   10.475821] audit: initializing netlink socket (disabled)
[   10.475844] audit(1190112336.320:1): initialized
[   10.476080] VFS: Disk quotas dquot_6.5.1
[   10.476115] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   10.476201] io scheduler noop registered
[   10.476206] io scheduler anticipatory registered
[   10.476210] io scheduler deadline registered
[   10.476227] io scheduler cfq registered (default)
[   10.476612] isapnp: Scanning for PnP cards...
[   10.830071] isapnp: No Plug & Play device found
[   10.872820] Real Time Clock Driver v1.12ac
[   10.872908] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   10.873160] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   10.874443] 00:0d: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   10.875656] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 5
[   10.875662] PCI: setting IRQ 5 as level-triggered
[   10.875667] ACPI: PCI Interrupt 0000:00:1f.6[B] -> Link [LNKB] -> GSI 5 (level, low) -> IRQ 5
[   10.875680] ACPI: PCI interrupt for device 0000:00:1f.6 disabled
[   10.875803] mice: PS/2 mouse device common for all mice
[   10.876749] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   10.877142] input: Macintosh mouse button emulation as /class/input/input0
[   10.877202] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[   10.877208] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[   10.877571] PNP: PS/2 Controller [PNP0303:KBC,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[   10.882565] serio: i8042 KBD port at 0x60,0x64 irq 1
[   10.882573] serio: i8042 AUX port at 0x60,0x64 irq 12
[   10.882766] EISA: Probing bus 0 at eisa.0
[   10.882778] Cannot allocate resource for EISA slot 1
[   10.882802] EISA: Detected 0 cards.
[   10.912945] TCP cubic registered
[   10.912959] NET: Registered protocol family 1
[   10.912997] Using IPI No-Shortcut mode
[   10.913109] ACPI: (supports S0 S1 S3 S4 S5)
[   10.913181]   Magic number: 7:665:780
[   10.913402] Time: tsc clocksource has been installed.
[   10.913415]   hash matches device ptyq2
[   10.913956] Freeing unused kernel memory: 328k freed
[   10.915924] input: AT Translated Set 2 keyboard as /class/input/input1
[   12.252078] Capability LSM initialized
[   12.318798] ACPI: CPU0 (power states: C1[C1] C2[C2])
[   12.318808] ACPI: Processor [CPU0] (supports 8 throttling states)
[   12.339854] ACPI: Thermal Zone [THM] (31 C)
[   13.141909] usbcore: registered new interface driver usbfs
[   13.141951] usbcore: registered new interface driver hub
[   13.141987] usbcore: registered new device driver usb
[   13.143558] USB Universal Host Controller Interface driver v3.0
[   13.144550] ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 11
[   13.144555] ACPI: PCI Interrupt 0000:00:1d.0[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
[   13.144574] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[   13.144579] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[   13.144767] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[   13.144801] uhci_hcd 0000:00:1d.0: irq 11, io base 0x0000bf80
[   13.144975] usb usb1: configuration #1 chosen from 1 choice
[   13.145021] hub 1-0:1.0: USB hub found
[   13.145035] hub 1-0:1.0: 2 ports detected
[   13.274196] ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 11
[   13.274203] ACPI: PCI Interrupt 0000:00:1d.2[C] -> Link [LNKC] -> GSI 11 (level, low) -> IRQ 11
[   13.274221] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[   13.274227] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[   13.274265] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 2
[   13.274296] uhci_hcd 0000:00:1d.2: irq 11, io base 0x0000bf20
[   13.274440] usb usb2: configuration #1 chosen from 1 choice
[   13.274490] hub 2-0:1.0: USB hub found
[   13.274502] hub 2-0:1.0: 2 ports detected
[   13.330603] ieee1394: Initialized config rom entry `ip1394'
[   13.418895] SCSI subsystem initialized
[   13.428685] libata version 2.20 loaded.
[   13.431373] ata_piix 0000:00:1f.1: version 2.10ac1
[   13.431395] PCI: Enabling device 0000:00:1f.1 (0005 -> 0007)
[   13.431410] ACPI: PCI Interrupt 0000:00:1f.1[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
[   13.431439] PCI: Setting latency timer of device 0000:00:1f.1 to 64
[   13.431519] ata1: PATA max UDMA/100 cmd 0x000101f0 ctl 0x000103f6 bmdma 0x0001bfa0 irq 14
[   13.448447] ata2: PATA max UDMA/100 cmd 0x00010170 ctl 0x00010376 bmdma 0x0001bfa8 irq 15
[   13.448493] scsi0 : ata_piix
[   13.522956] Floppy drive(s): fd0 is 1.44M
[   13.583826] FDC 0 is a post-1991 82077
[    5.364000] Time: acpi_pm clocksource has been installed.
[    5.452000] ata1.00: ata_hpa_resize 1: sectors = 117210240, hpa_sectors = 117210240
[    5.452000] ata1.00: ATA-6: IC25N060ATMR04-0, MO3OAD0A, max UDMA/100
[    5.452000] ata1.00: 117210240 sectors, multi 8: LBA48 
[    5.452000] ata1.01: ATAPI, max UDMA/33
[    5.460000] ata1.00: ata_hpa_resize 1: sectors = 117210240, hpa_sectors = 117210240
[    5.460000] ata1.00: configured for UDMA/100
[    5.648000] ata1.01: configured for UDMA/33
[    5.648000] scsi1 : ata_piix
[   36.000000] ata2.00: ATAPI, max UDMA/33
[   36.180000] ata2.00: configured for UDMA/33
[   36.180000] scsi 0:0:0:0: Direct-Access     ATA      IC25N060ATMR04-0 MO3O PQ: 0 ANSI: 5
[   36.204000] scsi 0:0:1:0: CD-ROM            TOSHIBA  DVD-ROM SD-C2612 1D21 PQ: 0 ANSI: 5
[   36.220000] scsi 1:0:0:0: CD-ROM            MATSHITA UJDA360          1.02 PQ: 0 ANSI: 5
[   36.232000] ACPI: PCI Interrupt 0000:02:00.0[A] -> Link [LNKC] -> GSI 11 (level, low) -> IRQ 11
[   36.232000] 3c59x: Donald Becker and others. www.scyld.com/network/vortex.html
[   36.232000] 0000:02:00.0: 3Com PCI 3c905C Tornado at e881ec00.
[   36.252000] ACPI: PCI Interrupt 0000:02:01.2[A] -> Link [LNKD] -> GSI 11 (level, low) -> IRQ 11
[   36.304000] ohci1394: fw-host0: OHCI-1394 1.0 (PCI): IRQ=[11]  MMIO=[f8fff000-f8fff7ff]  Max Packet=[2048]  IR/IT contexts=[4/4]
[   36.340000] SCSI device sda: 117210240 512-byte hdwr sectors (60012 MB)
[   36.340000] sda: Write Protect is off
[   36.340000] sda: Mode Sense: 00 3a 00 00
[   36.340000] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   36.340000] SCSI device sda: 117210240 512-byte hdwr sectors (60012 MB)
[   36.340000] sda: Write Protect is off
[   36.340000] sda: Mode Sense: 00 3a 00 00
[   36.340000] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   36.340000]  sda: sda1 sda2 sda3 < sda5 >
[   36.732000] sd 0:0:0:0: Attached scsi disk sda
[   36.736000] sd 0:0:0:0: Attached scsi generic sg0 type 0
[   36.736000] scsi 0:0:1:0: Attached scsi generic sg1 type 5
[   36.736000] scsi 1:0:0:0: Attached scsi generic sg2 type 5
[   36.780000] sr0: scsi3-mmc drive: 24x/24x cd/rw xa/form2 cdda tray
[   36.780000] Uniform CD-ROM driver Revision: 3.20
[   36.780000] sr 0:0:1:0: Attached scsi CD-ROM sr0
[   36.804000] sr1: scsi3-mmc drive: 24x/24x writer cd/rw xa/form2 cdda tray
[   36.804000] sr 1:0:0:0: Attached scsi CD-ROM sr1
[   37.136000] Attempting manual resume
[   37.136000] swsusp: Resume From Partition 8:5
[   37.136000] PM: Checking swsusp image.
[   37.136000] PM: Resume from disk failed.
[   37.196000] kjournald starting.  Commit interval 5 seconds
[   37.196000] EXT3-fs: mounted filesystem with ordered data mode.
[   37.580000] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[314fc00027c27821]
[   53.068000] eth0:  setting full-duplex.
[   54.132000] NET: Registered protocol family 10
[   54.136000] lo: Disabled Privacy Extensions
[   55.300000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   55.348000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   55.476000] Intel 82802 RNG detected
[   55.532000] Linux agpgart interface v0.102 (c) Dave Jones
[   55.540000] iTCO_vendor_support: vendor-support=0
[   55.544000] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.01 (11-Nov-2006)
[   55.544000] iTCO_wdt: Found a ICH3-M TCO device (Version=1, TCOBASE=0x0860)
[   55.544000] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   55.556000] agpgart: Detected an Intel i845 Chipset.
[   55.560000] agpgart: AGP aperture is 64M @ 0xe8000000
[   56.504000] Yenta: CardBus bridge found at 0000:02:01.0 [1028:00d4]
[   56.504000] Yenta: Using CSCINT to route CSC interrupts to PCI
[   56.504000] Yenta: Routing CardBus interrupts to PCI
[   56.504000] Yenta TI: socket 0000:02:01.0, mfunc 0x05033002, devctl 0x64
[   56.736000] Yenta: ISA IRQ mask 0x0498, PCI irq 11
[   56.736000] Socket status: 30000006
[   56.736000] pcmcia: parent PCI bridge I/O window: 0xe000 - 0xffff
[   56.736000] cs: IO port probe 0xe000-0xffff: clean.
[   56.736000] pcmcia: parent PCI bridge Memory window: 0xf4000000 - 0xfbffffff
[   56.736000] pcmcia: parent PCI bridge Memory window: 0x30000000 - 0x39ffffff
[   56.736000] Yenta: CardBus bridge found at 0000:02:01.1 [1028:00d4]
[   56.736000] Yenta: Using CSCINT to route CSC interrupts to PCI
[   56.736000] Yenta: Routing CardBus interrupts to PCI
[   56.736000] Yenta TI: socket 0000:02:01.1, mfunc 0x05033002, devctl 0x64
[   56.796000] input: PC Speaker as /class/input/input2
[   56.888000] parport: PnPBIOS parport detected.
[   56.892000] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
[   56.968000] Yenta: ISA IRQ mask 0x0418, PCI irq 11
[   56.968000] Socket status: 30000020
[   56.968000] pcmcia: parent PCI bridge I/O window: 0xe000 - 0xffff
[   56.968000] cs: IO port probe 0xe000-0xffff: clean.
[   56.968000] pcmcia: parent PCI bridge Memory window: 0xf4000000 - 0xfbffffff
[   56.968000] pcmcia: parent PCI bridge Memory window: 0x30000000 - 0x39ffffff
[   57.028000] input: DualPoint Stick as /class/input/input3
[   57.072000] nvidia: module license 'NVIDIA' taints kernel.
[   57.328000] input: AlpsPS/2 ALPS DualPoint TouchPad as /class/input/input4
[   57.336000] ACPI: PCI Interrupt 0000:01:00.0[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
[   57.340000] NVRM: loading NVIDIA Linux x86 Kernel Module  1.0-9631  Thu Nov  9 17:38:10 PST 2006
[   57.820000] ACPI: PCI Interrupt 0000:00:1f.5[B] -> Link [LNKB] -> GSI 5 (level, low) -> IRQ 5
[   57.820000] PCI: Setting latency timer of device 0000:00:1f.5 to 64
[   57.836000] pccard: CardBus card inserted into slot 1
[   58.144000] cs: IO port probe 0x100-0x3af: clean.
[   58.144000] cs: IO port probe 0x3e0-0x4ff: clean.
[   58.144000] cs: IO port probe 0x820-0x8ff: clean.
[   58.144000] cs: IO port probe 0xc00-0xcf7: clean.
[   58.144000] cs: IO port probe 0xa00-0xaff: clean.
[   58.192000] cs: IO port probe 0x100-0x3af: clean.
[   58.196000] cs: IO port probe 0x3e0-0x4ff: clean.
[   58.196000] cs: IO port probe 0x820-0x8ff: clean.
[   58.196000] cs: IO port probe 0xc00-0xcf7: clean.
[   58.196000] cs: IO port probe 0xa00-0xaff: clean.
[   58.388000] intel8x0_measure_ac97_clock: measured 55390 usecs
[   58.388000] intel8x0: clocking to 48000
[   58.588000] lp0: using parport0 (interrupt-driven).
[   58.692000] fuse init (API version 7.8)
[   58.752000] Adding 1253028k swap on /dev/disk/by-uuid/02efa288-c145-4586-8af0-95bf2be74cd9.  Priority:-1 extents:1 across:1253028k
[   58.916000] EXT3 FS on sda2, internal journal
[   61.008000] ACPI: AC Adapter [AC] (on-line)
[   61.120000] input: Lid Switch as /class/input/input5
[   61.124000] ACPI: Lid Switch [LID]
[   61.180000] input: Power Button (CM) as /class/input/input6
[   61.188000] ACPI: Power Button (CM) [PBTN]
[   61.236000] input: Sleep Button (CM) as /class/input/input7
[   61.236000] ACPI: Sleep Button (CM) [SBTN]
[   61.276000] ACPI: Battery Slot [BAT0] (battery absent)
[   61.384000] ACPI: Battery Slot [BAT1] (battery present)
[   61.408000] Using specific hotkey driver
[   61.488000] ibm_acpi: ec object not found
[   61.588000] ACPI: ACPI Dock Station Driver 
[   61.632000] ACPI: Video Device [VID] (multi-head: yes  rom: no  post: no)
[   61.792000] pcc_acpi: loading...
[   64.604000] eth0: no IPv6 routers present
[   71.240000] agpgart: Found an AGP 2.0 compliant device at 0000:00:00.0.
[   71.240000] agpgart: Putting AGP V2 device at 0000:00:00.0 into 4x mode
[   71.240000] agpgart: Putting AGP V2 device at 0000:01:00.0 into 4x mode
[   71.392000] ppdev: user-space parallel port driver
[   71.508000] **WARNING** I2C adapter driver [NVIDIA i2c adapter 0 at 1:00.0] forgot to specify physical device; fix it!
[   71.508000] **WARNING** I2C adapter driver [NVIDIA i2c adapter 1 at 1:00.0] forgot to specify physical device; fix it!
[   73.632000] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[   73.632000] apm: overridden by ACPI.
[   74.032000] Installing knfsd (copyright (C) 1996 okir@monad.swb.de).
[   74.260000] NFSD: Using /var/lib/nfs/v4recovery as the NFSv4 state recovery directory
[   74.272000] NFSD: starting 90-second grace period
[   79.112000] Bluetooth: Core ver 2.11
[   79.112000] NET: Registered protocol family 31
[   79.112000] Bluetooth: HCI device and connection manager initialized
[   79.112000] Bluetooth: HCI socket layer initialized
[   79.180000] Bluetooth: L2CAP ver 2.8
[   79.180000] Bluetooth: L2CAP socket layer initialized
[   79.240000] Bluetooth: RFCOMM socket layer initialized
[   79.240000] Bluetooth: RFCOMM TTY layer initialized
[   79.240000] Bluetooth: RFCOMM ver 1.8
[  254.848000] usb 1-1: new full speed USB device using uhci_hcd and address 2
[  255.016000] usb 1-1: configuration #1 chosen from 1 choice
[  255.208000] usbcore: registered new interface driver libusual
[  255.232000] Initializing USB Mass Storage driver...
[  255.232000] scsi2 : SCSI emulation for USB Mass Storage devices
[  255.232000] usbcore: registered new interface driver usb-storage
[  255.232000] USB Mass Storage support registered.
[  255.232000] usb-storage: device found at 2
[  255.232000] usb-storage: waiting for device to settle before scanning
[  260.232000] usb-storage: device scan complete
[  260.236000] scsi 2:0:0:0: Direct-Access     Memorex  TD Classic 003B  PMAP PQ: 0 ANSI: 0 CCS
[  260.940000] SCSI device sdb: 2009088 512-byte hdwr sectors (1029 MB)
[  260.944000] sdb: Write Protect is off
[  260.944000] sdb: Mode Sense: 23 00 00 00
[  260.944000] sdb: assuming drive cache: write through
[  260.956000] SCSI device sdb: 2009088 512-byte hdwr sectors (1029 MB)
[  260.956000] sdb: Write Protect is off
[  260.956000] sdb: Mode Sense: 23 00 00 00
[  260.956000] sdb: assuming drive cache: write through
[  260.956000]  sdb: sdb1
[  260.964000] sd 2:0:0:0: Attached scsi removable disk sdb
[  260.964000] sd 2:0:0:0: Attached scsi generic sg3 type 0
```

Also, the laptop hangs while for about 5 minutes while loading the hard drive drivers.  The computer has a decent CPU and 600 MB of ram.  They also designated 1.6 GB of swap space.  Also, the computer froze up well simply opening some application.  Thanks in advance to anyone who responds.  This community is great!:KS

---

### Post by Super TWiT on 2007-09-19
Anyone?

---

