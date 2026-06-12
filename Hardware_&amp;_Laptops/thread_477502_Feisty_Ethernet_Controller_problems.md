---
title: "Feisty: Ethernet Controller problems"
date: 2007-06-18
forum: Hardware &amp; Laptops
---

### Post by Bennell on 2007-06-18
I've installed Feisty on my Acer Aspire 3003 WLMi, and my Ethernet controller does not receive an IP address from my router (DHCP). This is the output of dmesg:

```
[    0.000000] Linux version 2.6.20-16-generic (root@terranova) (gcc version 4.1.2 (Ubuntu 4.1.2-0ubuntu4)) #2 SMP Thu Jun 7 20:19:32 UTC 2007 (Ubuntu 2.6.20-16.29-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000] sanitize start
[    0.000000] sanitize end
[    0.000000] copy_e820_map() start: 0000000000000000 size: 000000000009f400 end: 000000000009f400 type: 1
[    0.000000] copy_e820_map() type is E820_RAM
[    0.000000] copy_e820_map() start: 000000000009f400 size: 0000000000000c00 end: 00000000000a0000 type: 2
[    0.000000] copy_e820_map() start: 00000000000dc000 size: 0000000000024000 end: 0000000000100000 type: 2
[    0.000000] copy_e820_map() start: 0000000000100000 size: 000000001bdf0000 end: 000000001bef0000 type: 1
[    0.000000] copy_e820_map() type is E820_RAM
[    0.000000] copy_e820_map() start: 000000001bef0000 size: 000000000000a000 end: 000000001befa000 type: 3
[    0.000000] copy_e820_map() start: 000000001befa000 size: 0000000000006000 end: 000000001bf00000 type: 4
[    0.000000] copy_e820_map() start: 000000001bf00000 size: 0000000004100000 end: 0000000020000000 type: 2
[    0.000000] copy_e820_map() start: 00000000fff00000 size: 0000000000100000 end: 0000000100000000 type: 2
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f400 (usable)
[    0.000000]  BIOS-e820: 000000000009f400 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000dc000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000001bef0000 (usable)
[    0.000000]  BIOS-e820: 000000001bef0000 - 000000001befa000 (ACPI data)
[    0.000000]  BIOS-e820: 000000001befa000 - 000000001bf00000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000001bf00000 - 0000000020000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fff00000 - 0000000100000000 (reserved)
[    0.000000] 0MB HIGHMEM available.
[    0.000000] 446MB LOWMEM available.
[    0.000000] found SMP MP-table at 000f7fd0
[    0.000000] Entering add_active_range(0, 0, 114416) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   114416
[    0.000000]   HighMem    114416 ->   114416
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   114416
[    0.000000] On node 0 totalpages: 114416
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 861 pages used for memmap
[    0.000000]   Normal zone: 109459 pages, LIFO batch:31
[    0.000000]   HighMem zone: 0 pages used for memmap
[    0.000000] DMI present.
[    0.000000] ACPI: RSDP (v000 PTLTD                                 ) @ 0x000f7f60
[    0.000000] ACPI: RSDT (v001 PTLTD    RSDT   0x06040000  LTP 0x00000000) @ 0x1bef619d
[    0.000000] ACPI: FADT (v001 SiS    755F     0x06040000 PTL  0x000f4240) @ 0x1bef9e3e
[    0.000000] ACPI: SSDT (v001 PTLTD  POWERNOW 0x06040000  LTP 0x00000001) @ 0x1bef9eb2
[    0.000000] ACPI: MADT (v001 PTLTD  	 APIC   0x06040000  LTP 0x00000000) @ 0x1bef9f88
[    0.000000] ACPI: BOOT (v001 PTLTD  $SBFTBL$ 0x06040000  LTP 0x00000001) @ 0x1bef9fd8
[    0.000000] ACPI: DSDT (v001 PTLTD       755 0x06040000 MSFT 0x0100000e) @ 0x00000000
[    0.000000] ACPI: PM-Timer IO Port: 0x8008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] Processor #0 15:12 APIC version 16
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: Skipping IOAPIC probe due to 'noapic' option.
[    0.000000] Using ACPI for processor (LAPIC) configuration information
[    0.000000] Intel MultiProcessor Specification v1.4
[    0.000000]     Virtual Wire compatibility mode.
[    0.000000] OEM ID:          Product ID:              APIC at: 0xFEE00000
[    0.000000] I/O APIC #1 Version 17 at 0xFEC00000.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] Processors: 1
[    0.000000] Allocating PCI resources starting at 30000000 (gap: 20000000:dff00000)
[    0.000000] Detected 1800.126 MHz processor.
[   12.346310] Built 1 zonelists.  Total pages: 113523
[   12.346313] Kernel command line: root=UUID=a262233e-0256-4038-9977-e2b57f96ffea ro quiet splash noapic
[   12.346456] mapped APIC to ffffd000 (fee00000)
[   12.346459] mapped IOAPIC to ffffc000 (fec00000)
[   12.346462] Enabling fast FPU save and restore... done.
[   12.346464] Enabling unmasked SIMD FPU exception support... done.
[   12.346472] Initializing CPU#0
[   12.346517] PID hash table entries: 2048 (order: 11, 8192 bytes)
[   12.347281] Console: colour VGA+ 80x25
[   12.347542] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
[   12.348054] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
[   12.357104] Memory: 442680k/457664k available (1992k kernel code, 14460k reserved, 900k data, 328k init, 0k highmem)
[   12.357115] virtual kernel memory layout:
[   12.357116]     fixmap  : 0xfff4e000 - 0xfffff000   ( 708 kB)
[   12.357118]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   12.357119]     vmalloc : 0xdc800000 - 0xff7fe000   ( 559 MB)
[   12.357120]     lowmem  : 0xc0000000 - 0xdbef0000   ( 446 MB)
[   12.357122]       .init : 0xc03d9000 - 0xc042b000   ( 328 kB)
[   12.357123]       .data : 0xc02f2374 - 0xc03d36d4   ( 900 kB)
[   12.357124]       .text : 0xc0100000 - 0xc02f2374   (1992 kB)
[   12.357128] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   12.434392] Calibrating delay using timer specific routine.. 3602.20 BogoMIPS (lpj=7204418)
[   12.434432] Security Framework v1.0.0 initialized
[   12.434438] SELinux:  Disabled at boot.
[   12.434453] Mount-cache hash table entries: 512
[   12.434575] CPU: After generic identify, caps: 078bfbff c3d3fbff 00000000 00000000 00000001 00000000 00000001
[   12.434584] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[   12.434586] CPU: L2 Cache: 128K (64 bytes/line)
[   12.434589] CPU: After all inits, caps: 078bfbff c3d3fbff 00000000 00000410 00000001 00000000 00000001
[   12.434599] Compat vDSO mapped to ffffe000.
[   12.434603] Remapping vsyscall page to ffffe000
[   12.434612] Checking 'hlt' instruction... OK.
[   12.450499] SMP alternatives: switching to UP code
[   12.450799] Freeing SMP alternatives: 11k freed
[   12.451059] Early unpacking initramfs... done
[   12.762177] ACPI: Core revision 20060707
[   12.762406] ACPI: Looking for DSDT in initramfs... file /DSDT.aml not found, using machine DSDT.
[   12.763613] ACPI: setting ELCR to 0800 (from 0eb8)
[   12.765631] CPU0: AMD Mobile AMD Sempron(tm) Processor 3000+ stepping 02
[   12.765651] Total of 1 processors activated (3602.20 BogoMIPS).
[   12.869803] Brought up 1 CPUs
[   12.870013] Booting paravirtualized kernel on bare hardware
[   12.870091] Time: 15:38:45  Date: 05/18/107
[   12.870121] NET: Registered protocol family 16
[   12.870219] EISA bus registered
[   12.870223] ACPI: bus type pci registered
[   12.870356] PCI: PCI BIOS revision 2.10 entry at 0xfd776, last bus=1
[   12.870358] PCI: Using configuration type 1
[   12.870360] Setting up standard PCI resources
[   12.872782] ACPI: Interpreter enabled
[   12.872786] ACPI: Using PIC for interrupt routing
[   12.873139] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   12.873145] PCI: Probing PCI hardware (bus 00)
[   12.874298] Enabling SiS 96x SMBus.
[   12.874683] Boot video device is 0000:01:00.0
[   12.874745] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   12.896472] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 *7 9 10 11)
[   12.896675] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 *4 5 7 9 10 11)
[   12.896875] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 *5 7 9 10 11)
[   12.897070] ACPI: PCI Interrupt Link [LNKD] (IRQs *3 4 5 7 9 10 11)
[   12.897282] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 7 *9 10 11)
[   12.897484] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 7 9 10 *11)
[   12.897681] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 7 9 10 11) *0, disabled.
[   12.897889] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 7 9 *10 11)
[   12.898199] Linux Plug and Play Support v0.97 (c) Adam Belay
[   12.898215] pnp: PnP ACPI init
[   12.899919] pnp: PnP ACPI: found 8 devices
[   12.899925] PnPBIOS: Disabled by ACPI PNP
[   12.899978] PCI: Using ACPI for IRQ routing
[   12.899981] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   12.902116] NET: Registered protocol family 8
[   12.902118] NET: Registered protocol family 20
[   12.902309] pnp: 00:04: ioport range 0x8000-0x807f could not be reserved
[   12.902313] pnp: 00:04: ioport range 0x8080-0x80ff has been reserved
[   12.902316] pnp: 00:04: ioport range 0x8100-0x811f has been reserved
[   12.902319] pnp: 00:04: ioport range 0x4d0-0x4d1 has been reserved
[   12.902571] PCI: Ignore bogus resource 6 [0:0] of 0000:01:00.0
[   12.902575] PCI: Bridge: 0000:00:01.0
[   12.902577]   IO window: a000-afff
[   12.902581]   MEM window: e2100000-e21fffff
[   12.902585]   PREFETCH window: e8000000-efffffff
[   12.902589] PCI: Bus 2, cardbus bridge: 0000:00:06.0
[   12.902592]   IO window: 00002400-000024ff
[   12.902595]   IO window: 00002800-000028ff
[   12.902599]   PREFETCH window: 30000000-33ffffff
[   12.902602]   MEM window: 34000000-37ffffff
[   12.902618] PCI: Enabling device 0000:00:06.0 (0000 -> 0003)
[   12.902624] ACPI: Unable to derive IRQ for device 0000:00:06.0
[   12.902626] ACPI: PCI Interrupt 0000:00:06.0[A]: no GSI
[   12.902652] NET: Registered protocol family 2
[   12.937739] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
[   12.937824] TCP established hash table entries: 16384 (order: 5, 131072 bytes)
[   12.937950] TCP bind hash table entries: 8192 (order: 4, 65536 bytes)
[   12.938029] TCP: Hash tables configured (established 16384 bind 8192)
[   12.938032] TCP reno registered
[   12.949775] checking if image is initramfs... it is
[   13.562067] Freeing initrd memory: 6772k freed
[   13.562251] Simple Boot Flag at 0x38 set to 0x1
[   13.562501] audit: initializing netlink socket (disabled)
[   13.562516] audit(1182181125.300:1): initialized
[   13.562629] VFS: Disk quotas dquot_6.5.1
[   13.562650] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   13.562699] io scheduler noop registered
[   13.562701] io scheduler anticipatory registered
[   13.562703] io scheduler deadline registered
[   13.562711] io scheduler cfq registered (default)
[   14.000305] isapnp: Scanning for PnP cards...
[   14.353198] isapnp: No Plug & Play device found
[   14.393072] Real Time Clock Driver v1.12ac
[   14.393112] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   14.394240] ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 5
[   14.394245] PCI: setting IRQ 5 as level-triggered
[   14.394248] ACPI: PCI Interrupt 0000:00:02.6[C] -> Link [LNKC] -> GSI 5 (level, low) -> IRQ 5
[   14.394256] ACPI: PCI interrupt for device 0000:00:02.6 disabled
[   14.394340] mice: PS/2 mouse device common for all mice
[   14.394776] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   14.395025] input: Macintosh mouse button emulation as /class/input/input0
[   14.395054] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[   14.395059] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[   14.395266] PNP: PS/2 Controller [PNP0303:KBC,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[   14.397696] serio: i8042 KBD port at 0x60,0x64 irq 1
[   14.397702] serio: i8042 AUX port at 0x60,0x64 irq 12
[   14.397860] EISA: Probing bus 0 at eisa.0
[   14.397871] Cannot allocate resource for EISA slot 1
[   14.397873] Cannot allocate resource for EISA slot 2
[   14.397891] Cannot allocate resource for EISA slot 8
[   14.397893] EISA: Detected 0 cards.
[   14.427936] TCP cubic registered
[   14.427943] NET: Registered protocol family 1
[   14.427965] Using IPI No-Shortcut mode
[   14.428029] ACPI: (supports S0 S3 S4 S5)
[   14.428063]   Magic number: 11:523:639
[   14.428512] Freeing unused kernel memory: 328k freed
[   14.431456] Time: tsc clocksource has been installed.
[   14.444685] input: AT Translated Set 2 keyboard as /class/input/input1
[   15.668200] Capability LSM initialized
[   15.709312] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[   15.712576] ACPI: Thermal Zone [THRM] (58 C)
[   16.277394] SCSI subsystem initialized
[   16.281959] libata version 2.20 loaded.
[   16.284784] pata_sis 0000:00:02.5: version 0.5.1
[   16.285012] ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 7
[   16.285015] PCI: setting IRQ 7 as level-triggered
[   16.285018] ACPI: PCI Interrupt 0000:00:02.5[A] -> Link [LNKA] -> GSI 7 (level, low) -> IRQ 7
[   16.285090] ata1: PATA max UDMA/133 cmd 0x000101f0 ctl 0x000103f6 bmdma 0x00012000 irq 14
[   16.285116] ata2: PATA max UDMA/133 cmd 0x00010170 ctl 0x00010376 bmdma 0x00012008 irq 15
[   16.285130] scsi0 : pata_sis
[   16.306814] usbcore: registered new interface driver usbfs
[   16.306835] usbcore: registered new interface driver hub
[   16.306855] usbcore: registered new device driver usb
[   16.344876] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
[   16.382081] sis900.c: v1.08.10 Apr. 2 2006
[   16.448701] ata1.00: ATA-6: WDC WD600UE-22HCT0, 09.07D09, max UDMA/100
[   16.448706] ata1.00: 117210240 sectors, multi 16: LBA 
[   16.456694] ata1.00: configured for UDMA/100
[   16.456709] scsi1 : pata_sis
[    3.672000] Time: acpi_pm clocksource has been installed.
[    3.936000] ata2.00: ATAPI, max UDMA/33
[    4.100000] ata2.00: configured for UDMA/33
[    4.100000] scsi 0:0:0:0: Direct-Access     ATA      WDC WD600UE-22HC 09.0 PQ: 0 ANSI: 5
[    4.104000] scsi 1:0:0:0: CD-ROM            HL-DT-ST DVD-RW GCA-4080N 0H38 PQ: 0 ANSI: 5
[    4.108000] ACPI: PCI Interrupt Link [LNKE] enabled at IRQ 9
[    4.108000] PCI: setting IRQ 9 as level-triggered
[    4.108000] ACPI: PCI Interrupt 0000:00:03.0[A] -> Link [LNKE] -> GSI 9 (level, low) -> IRQ 9
[    4.108000] ohci_hcd 0000:00:03.0: OHCI Host Controller
[    4.108000] ohci_hcd 0000:00:03.0: new USB bus registered, assigned bus number 1
[    4.108000] ohci_hcd 0000:00:03.0: irq 9, io mem 0xe2002000
[    4.128000] SCSI device sda: 117210240 512-byte hdwr sectors (60012 MB)
[    4.128000] sda: Write Protect is off
[    4.128000] sda: Mode Sense: 00 3a 00 00
[    4.128000] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.128000] SCSI device sda: 117210240 512-byte hdwr sectors (60012 MB)
[    4.128000] sda: Write Protect is off
[    4.128000] sda: Mode Sense: 00 3a 00 00
[    4.128000] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.128000]  sda:sr0: scsi3-mmc drive: 24x/24x writer cd/rw xa/form2 cdda tray
[    4.136000] Uniform CD-ROM driver Revision: 3.20
[    4.136000] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    4.140000] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    4.140000] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    4.164000] usb usb1: configuration #1 chosen from 1 choice
[    4.164000] hub 1-0:1.0: USB hub found
[    4.164000] hub 1-0:1.0: 3 ports detected
[    4.268000] ACPI: PCI Interrupt Link [LNKF] enabled at IRQ 11
[    4.268000] PCI: setting IRQ 11 as level-triggered
[    4.268000] ACPI: PCI Interrupt 0000:00:03.1[B] -> Link [LNKF] -> GSI 11 (level, low) -> IRQ 11
[    4.268000] ohci_hcd 0000:00:03.1: OHCI Host Controller
[    4.268000] ohci_hcd 0000:00:03.1: new USB bus registered, assigned bus number 2
[    4.268000] ohci_hcd 0000:00:03.1: irq 11, io mem 0xe2003000
[    4.324000] usb usb2: configuration #1 chosen from 1 choice
[    4.324000] hub 2-0:1.0: USB hub found
[    4.324000] hub 2-0:1.0: 3 ports detected
[    4.412000]  sda1 sda2 sda3 sda4 <<4>ACPI: Unable to derive IRQ for device 0000:00:04.0
[    4.428000] ACPI: PCI Interrupt 0000:00:04.0[A]: no GSI - using IRQ 3
[    4.428000] PCI: setting IRQ 3 as level-triggered
[    4.432000] 0000:00:04.0: Realtek RTL8201 PHY transceiver found at address 13.
[    4.436000] 0000:00:04.0: Using transceiver found at address 13 as default
[    4.436000] eth0: SiS 900 PCI Fast Ethernet at 0x1800, IRQ 3, 00:c0:9f:d2:e0:53.
[    4.436000] ACPI: PCI Interrupt Link [LNKH] enabled at IRQ 10
[    4.436000] PCI: setting IRQ 10 as level-triggered
[    4.436000] ACPI: PCI Interrupt 0000:00:03.2[D] -> Link [LNKH] -> GSI 10 (level, low) -> IRQ 10
[    4.436000] ehci_hcd 0000:00:03.2: EHCI Host Controller
[    4.436000] ehci_hcd 0000:00:03.2: new USB bus registered, assigned bus number 3
[    4.436000] PCI: cache line size of 64 is not supported by device 0000:00:03.2
[    4.436000] ehci_hcd 0000:00:03.2: irq 10, io mem 0xe2004000
[    4.436000] ehci_hcd 0000:00:03.2: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    4.436000] usb usb3: configuration #1 chosen from 1 choice
[    4.436000] hub 3-0:1.0: USB hub found
[    4.436000] hub 3-0:1.0: 6 ports detected
[    4.440000]  sda5 sda6 sda7 sda8 sda9 >
[    4.508000] sd 0:0:0:0: Attached scsi disk sda
[    5.076000] usb 2-2: new low speed USB device using ohci_hcd and address 2
[    5.088000] Attempting manual resume
[    5.088000] swsusp: Resume From Partition 8:2
[    5.088000] PM: Checking swsusp image.
[    5.092000] PM: Resume from disk failed.
[    5.100000] ReiserFS: sda3: found reiserfs format "3.6" with standard journal
[    5.100000] ReiserFS: sda3: using ordered data mode
[    5.108000] ReiserFS: sda3: journal params: device sda3, size 8192, journal first block 18, max trans len 1024, max batch 900, max commit age 30, max trans age 30
[    5.108000] ReiserFS: sda3: checking transaction log (sda3)
[    5.132000] ReiserFS: sda3: Using r5 hash to sort names
[    5.288000] usb 2-2: configuration #1 chosen from 1 choice
[    6.880000] eth0: Media Link Off
[    7.260000] irq 3: nobody cared (try booting with the "irqpoll" option)
[    7.260000]  [<c01543a4>] __report_bad_irq+0x24/0x80
[    7.260000]  [<c015465e>] note_interrupt+0x25e/0x290
[    7.260000]  [<c01538d0>] handle_IRQ_event+0x30/0x60
[    7.260000]  [<c01551db>] handle_level_irq+0xeb/0x120
[    7.260000]  [<c0105b70>] do_IRQ+0x40/0x80
[    7.260000]  [<c0104233>] common_interrupt+0x23/0x30
[    7.260000]  =======================
[    7.260000] handlers:
[    7.260000] [<dc8dee90>] (sis900_interrupt+0x0/0x710 [sis900])
[    7.260000] Disabling IRQ #3
[    8.652000] NET: Registered protocol family 17
[    8.668000] Linux agpgart interface v0.102 (c) Dave Jones
[    8.676000] agpgart: Detected AGP bridge 0
[    8.676000] agpgart: AGP aperture is 32M @ 0xe0000000
[    8.868000] sis96x_smbus 0000:00:02.1: SiS96x SMBus base address: 0x8100
[    9.148000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    9.152000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[    9.168000] Yenta: CardBus bridge found at 0000:00:06.0 [1025:0083]
[    9.168000] Yenta: Using CSCINT to route CSC interrupts to PCI
[    9.168000] Yenta: Routing CardBus interrupts to PCI
[    9.168000] Yenta TI: socket 0000:00:06.0, mfunc 0x00521d22, devctl 0x64
[    9.168000] Yenta: request_irq() in yenta_probe_cb_irq() failed!
[    9.168000] Yenta TI: socket 0000:00:06.0 no PCI interrupts. Fish. Please report.
[    9.168000] Yenta: no PCI IRQ, CardBus support disabled for this socket.
[    9.168000] Yenta: check your BIOS CardBus, BIOS IRQ or ACPI settings.
[    9.296000] Yenta: ISA IRQ mask 0x0050, PCI irq 0
[    9.296000] Socket status: 30000006
[    9.372000] input: PC Speaker as /class/input/input2
[    9.388000] ieee80211_crypt: registered algorithm 'NULL'
[    9.400000] ieee80211: 802.11 data/management/control stack, git-1.1.13
[    9.400000] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
[    9.436000] bcm43xx driver
[    9.436000] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 4
[    9.436000] PCI: setting IRQ 4 as level-triggered
[    9.436000] ACPI: PCI Interrupt 0000:00:0b.0[A] -> Link [LNKB] -> GSI 4 (level, low) -> IRQ 4
[    9.752000] usbcore: registered new interface driver hiddev
[    9.784000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[    9.852000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[    9.900000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[    9.952000] input: Logitech Optical USB Mouse as /class/input/input3
[    9.952000] input: USB HID v1.10 Mouse [Logitech Optical USB Mouse] on usb-0000:00:03.1-2
[    9.952000] usbcore: registered new interface driver usbhid
[    9.952000] drivers/usb/input/hid-core.c: v2.6:USB HID core driver
[    9.968000] ACPI: PCI Interrupt 0000:00:02.7[C] -> Link [LNKC] -> GSI 5 (level, low) -> IRQ 5
[    9.992000] cs: IO port probe 0x100-0x3af: clean.
[   10.028000] cs: IO port probe 0x3e0-0x4ff: excluding 0x480-0x48f
[   10.028000] cs: IO port probe 0x820-0x8ff: clean.
[   10.032000] cs: IO port probe 0xc00-0xcf7: clean.
[   10.032000] cs: IO port probe 0xa00-0xaff: clean.
[   10.220000] Synaptics Touchpad, model: 1, fw: 5.9, id: 0x126eb1, caps: 0xa04713/0x4000
[   10.256000] input: SynPS/2 Synaptics TouchPad as /class/input/input4
[   10.788000] intel8x0_measure_ac97_clock: measured 55467 usecs
[   10.788000] intel8x0: clocking to 48000
[   10.944000] fuse init (API version 7.8)
[   10.996000] lp: driver loaded but no devices found
[   11.020000] Adding 498004k swap on /dev/disk/by-uuid/d7e799de-8575-4931-9104-6f60603cb946.  Priority:-1 extents:1 across:498004k
[   34.340000] ReiserFS: sda9: found reiserfs format "3.6" with standard journal
[   34.340000] ReiserFS: sda9: using ordered data mode
[   34.348000] ReiserFS: sda9: journal params: device sda9, size 8192, journal first block 18, max trans len 1024, max batch 900, max commit age 30, max trans age 30
[   34.352000] ReiserFS: sda9: checking transaction log (sda9)
[   34.416000] ReiserFS: sda9: Using r5 hash to sort names
[   34.472000] ReiserFS: sda8: found reiserfs format "3.6" with standard journal
[   34.472000] ReiserFS: sda8: using ordered data mode
[   34.484000] ReiserFS: sda8: journal params: device sda8, size 8192, journal first block 18, max trans len 1024, max batch 900, max commit age 30, max trans age 30
[   34.488000] ReiserFS: sda8: checking transaction log (sda8)
[   34.512000] ReiserFS: sda8: Using r5 hash to sort names
[   34.540000] ReiserFS: sda5: found reiserfs format "3.6" with standard journal
[   34.540000] ReiserFS: sda5: using ordered data mode
[   34.552000] ReiserFS: sda5: journal params: device sda5, size 8192, journal first block 18, max trans len 1024, max batch 900, max commit age 30, max trans age 30
[   34.552000] ReiserFS: sda5: checking transaction log (sda5)
[   34.608000] ReiserFS: sda5: Using r5 hash to sort names
[   34.660000] ReiserFS: sda6: found reiserfs format "3.6" with standard journal
[   34.660000] ReiserFS: sda6: using ordered data mode
[   34.664000] ReiserFS: sda6: journal params: device sda6, size 8192, journal first block 18, max trans len 1024, max batch 900, max commit age 30, max trans age 30
[   34.664000] ReiserFS: sda6: checking transaction log (sda6)
[   34.684000] ReiserFS: sda6: Using r5 hash to sort names
[   34.708000] ReiserFS: sda7: found reiserfs format "3.6" with standard journal
[   34.708000] ReiserFS: sda7: using ordered data mode
[   34.720000] ReiserFS: sda7: journal params: device sda7, size 8192, journal first block 18, max trans len 1024, max batch 900, max commit age 30, max trans age 30
[   34.720000] ReiserFS: sda7: checking transaction log (sda7)
[   34.744000] ReiserFS: sda7: Using r5 hash to sort names
[   44.704000] Using specific hotkey driver
[   44.784000] ACPI: AC Adapter [ACAD] (on-line)
[   44.804000] No dock devices found.
[   44.900000] input: Power Button (FF) as /class/input/input5
[   44.904000] ACPI: Power Button (FF) [PWRF]
[   44.936000] input: Lid Switch as /class/input/input6
[   44.940000] ACPI: Lid Switch [LID]
[   44.972000] input: Power Button (CM) as /class/input/input7
[   44.976000] ACPI: Power Button (CM) [PWRB]
[   45.008000] input: Sleep Button (CM) as /class/input/input8
[   45.012000] ACPI: Sleep Button (CM) [SLPB]
[   45.060000] ibm_acpi: ec object not found
[   45.104000] ACPI: Battery Slot [BAT1] (battery present)
[   45.156000] pcc_acpi: loading...
[   45.416000] powernow-k8: Found 1 Mobile AMD Sempron(tm) Processor 3000+ processors (version 2.00.00)
[   45.416000] powernow-k8:    0 : fid 0xa (1800 MHz), vid 0xa
[   45.416000] powernow-k8:    1 : fid 0x8 (1600 MHz), vid 0xc
[   45.416000] powernow-k8:    2 : fid 0x0 (800 MHz), vid 0x13
[   45.564000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[   45.644000] NET: Registered protocol family 10
[   45.644000] lo: Disabled Privacy Extensions
[   45.644000] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   59.352000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[   59.744000] ppdev: user-space parallel port driver
[   64.056000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[   67.124000] apm: BIOS not found.
[   67.332000] Bluetooth: Core ver 2.11
[   67.332000] NET: Registered protocol family 31
[   67.332000] Bluetooth: HCI device and connection manager initialized
[   67.332000] Bluetooth: HCI socket layer initialized
[   67.376000] Bluetooth: L2CAP ver 2.8
[   67.376000] Bluetooth: L2CAP socket layer initialized
[   67.460000] Bluetooth: RFCOMM socket layer initialized
[   67.460000] Bluetooth: RFCOMM TTY layer initialized
[   67.460000] Bluetooth: RFCOMM ver 1.8
[   88.840000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[  113.128000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[  136.368000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[  159.600000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[  165.616000] usb 3-3: new high speed USB device using ehci_hcd and address 3
[  167.356000] usb 3-3: configuration #1 chosen from 1 choice
[  167.684000] usbcore: registered new interface driver libusual
[  167.708000] Initializing USB Mass Storage driver...
[  167.708000] scsi2 : SCSI emulation for USB Mass Storage devices
[  167.708000] usbcore: registered new interface driver usb-storage
[  167.708000] USB Mass Storage support registered.
[  167.708000] usb-storage: device found at 3
[  167.708000] usb-storage: waiting for device to settle before scanning
[  172.708000] usb-storage: device scan complete
[  172.708000] scsi 2:0:0:0: Direct-Access     Creative NOMAD MuVo TX    1105 PQ: 0 ANSI: 4
[  172.708000] SCSI device sdb: 2038272 512-byte hdwr sectors (1044 MB)
[  172.712000] sdb: Write Protect is off
[  172.712000] sdb: Mode Sense: 03 00 00 00
[  172.712000] sdb: assuming drive cache: write through
[  172.712000] SCSI device sdb: 2038272 512-byte hdwr sectors (1044 MB)
[  172.716000] sdb: Write Protect is off
[  172.716000] sdb: Mode Sense: 03 00 00 00
[  172.716000] sdb: assuming drive cache: write through
[  172.716000]  sdb: sdb1
[  172.716000] sd 2:0:0:0: Attached scsi removable disk sdb
[  172.716000] sd 2:0:0:0: Attached scsi generic sg2 type 0
[  182.804000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[  256.492000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[  306.068000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[  315.520000] usb 3-3: USB disconnect, address 3
[  315.520000] Buffer I/O error on device sdb1, logical block 1
[  315.520000] lost page write due to I/O error on sdb1
[  315.520000] Buffer I/O error on device sdb1, logical block 250
[  315.520000] lost page write due to I/O error on sdb1
[  315.520000] Buffer I/O error on device sdb1, logical block 499
[  315.520000] lost page write due to I/O error on sdb1
[  315.532000] scsi 2:0:0:0: rejecting I/O to dead device
[  315.532000] scsi 2:0:0:0: rejecting I/O to dead device
[  315.532000] scsi 2:0:0:0: rejecting I/O to dead device
[  315.532000] scsi 2:0:0:0: rejecting I/O to dead device
[  315.532000] sdb : READ CAPACITY failed.
[  315.532000] sdb : status=0, message=00, host=1, driver=00 
[  315.532000] sdb : sense not available. 
[  315.532000] scsi 2:0:0:0: rejecting I/O to dead device
[  315.532000] sdb: Write Protect is off
[  315.532000] sdb: Mode Sense: 00 00 00 00
[  315.532000] sdb: assuming drive cache: write through
[  429.300000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[  552.520000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[  612.460000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[  649.980000] usb 3-3: new high speed USB device using ehci_hcd and address 4
[  651.728000] usb 3-3: configuration #1 chosen from 1 choice
[  651.728000] scsi3 : SCSI emulation for USB Mass Storage devices
[  651.728000] usb-storage: device found at 4
[  651.728000] usb-storage: waiting for device to settle before scanning
[  656.728000] usb-storage: device scan complete
[  656.728000] scsi 3:0:0:0: Direct-Access     Creative NOMAD MuVo TX    1105 PQ: 0 ANSI: 4
[  656.728000] SCSI device sdb: 2038272 512-byte hdwr sectors (1044 MB)
[  656.732000] sdb: Write Protect is off
[  656.732000] sdb: Mode Sense: 03 00 00 00
[  656.732000] sdb: assuming drive cache: write through
[  656.732000] SCSI device sdb: 2038272 512-byte hdwr sectors (1044 MB)
[  656.736000] sdb: Write Protect is off
[  656.736000] sdb: Mode Sense: 03 00 00 00
[  656.736000] sdb: assuming drive cache: write through
[  656.736000]  sdb: sdb1
[  656.736000] sd 3:0:0:0: Attached scsi removable disk sdb
[  656.736000] sd 3:0:0:0: Attached scsi generic sg2 type 0
[  675.716000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.

```

```
$ lspci
0000:00:04:0 Ethernet Controller: Silicon Integrated Systems [SiS] SiS900 PCI Fast Ethernet (rev 91)
```

Everything works fine if I pass "acpi=off" as a parameter at boot time.

---

### Post by ukripper on 2007-06-19
Can you post your ifconfig  here:

---

