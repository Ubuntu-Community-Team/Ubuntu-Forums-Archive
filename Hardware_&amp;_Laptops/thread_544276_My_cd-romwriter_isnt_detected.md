---
title: "My cd-rom/writer isnt detected"
date: 2007-09-06
forum: Hardware &amp; Laptops
---

### Post by LokeTheDog on 2007-09-06
When i try to mount it in the GUI, i get this: "mount: special device /dev/scd0 does not exist".
Its a liteon, its set to secondary master, it is detected in windows and has worked occationally before on ubuntu. Any ideas? Btw, I am pretty much a newbie, so take it slow ;)

Dmesg and fstab:

```
[    0.000000] Linux version 2.6.20-16-generic (root@terranova) (gcc version 4.1.2 (Ubuntu 4.1.2-0ubuntu4)) #2 SMP Fri Aug 31 00:55:27 UTC 2007 (Ubuntu 2.6.20-16.31-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000] sanitize start
[    0.000000] sanitize end
[    0.000000] copy_e820_map() start: 0000000000000000 size: 000000000009fc00 end: 000000000009fc00 type: 1
[    0.000000] copy_e820_map() type is E820_RAM
[    0.000000] copy_e820_map() start: 000000000009fc00 size: 0000000000000400 end: 00000000000a0000 type: 2
[    0.000000] copy_e820_map() start: 00000000000f0000 size: 0000000000010000 end: 0000000000100000 type: 2
[    0.000000] copy_e820_map() start: 0000000000100000 size: 000000001feec000 end: 000000001ffec000 type: 1
[    0.000000] copy_e820_map() type is E820_RAM
[    0.000000] copy_e820_map() start: 000000001ffec000 size: 0000000000003000 end: 000000001ffef000 type: 3
[    0.000000] copy_e820_map() start: 000000001ffef000 size: 0000000000010000 end: 000000001ffff000 type: 2
[    0.000000] copy_e820_map() start: 000000001ffff000 size: 0000000000001000 end: 0000000020000000 type: 4
[    0.000000] copy_e820_map() start: 00000000fec00000 size: 0000000000080000 end: 00000000fec80000 type: 2
[    0.000000] copy_e820_map() start: 00000000fee00000 size: 0000000000100000 end: 00000000fef00000 type: 2
[    0.000000] copy_e820_map() start: 00000000ffff0000 size: 0000000000010000 end: 0000000100000000 type: 2
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000001ffec000 (usable)
[    0.000000]  BIOS-e820: 000000001ffec000 - 000000001ffef000 (ACPI data)
[    0.000000]  BIOS-e820: 000000001ffef000 - 000000001ffff000 (reserved)
[    0.000000]  BIOS-e820: 000000001ffff000 - 0000000020000000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec80000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fef00000 (reserved)
[    0.000000]  BIOS-e820: 00000000ffff0000 - 0000000100000000 (reserved)
[    0.000000] 0MB HIGHMEM available.
[    0.000000] 511MB LOWMEM available.
[    0.000000] found SMP MP-table at 000f0410
[    0.000000] Entering add_active_range(0, 0, 131052) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   131052
[    0.000000]   HighMem    131052 ->   131052
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   131052
[    0.000000] On node 0 totalpages: 131052
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 991 pages used for memmap
[    0.000000]   Normal zone: 125965 pages, LIFO batch:31
[    0.000000]   HighMem zone: 0 pages used for memmap
[    0.000000] DMI 2.3 present.
[    0.000000] ACPI: RSDP (v000 ASUS                                  ) @ 0x000f5930
[    0.000000] ACPI: RSDT (v001 ASUS   P4T533-C 0x42302e31 MSFT 0x31313031) @ 0x1ffec000
[    0.000000] ACPI: FADT (v001 ASUS   P4T533-C 0x42302e31 MSFT 0x31313031) @ 0x1ffec0c0
[    0.000000] ACPI: BOOT (v001 ASUS   P4T533-C 0x42302e31 MSFT 0x31313031) @ 0x1ffec030
[    0.000000] ACPI: MADT (v001 ASUS   P4T533-C 0x42302e31 MSFT 0x31313031) @ 0x1ffec058
[    0.000000] ACPI: DSDT (v001   ASUS P4T533-C 0x00001000 MSFT 0x0100000b) @ 0x00000000
[    0.000000] ACPI: PM-Timer IO Port: 0xe408
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] Processor #0 15:2 APIC version 20
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x04] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 4, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl edge)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] Allocating PCI resources starting at 30000000 (gap: 20000000:dec00000)
[    0.000000] Detected 2663.242 MHz processor.
[   37.599428] Built 1 zonelists.  Total pages: 130029
[   37.599433] Kernel command line: root=UUID=a3f2c8d8-7a9b-4978-8425-287620776715 ro quiet splash
[   37.599593] mapped APIC to ffffd000 (fee00000)
[   37.599596] mapped IOAPIC to ffffc000 (fec00000)
[   37.599599] Enabling fast FPU save and restore... done.
[   37.599603] Enabling unmasked SIMD FPU exception support... done.
[   37.599615] Initializing CPU#0
[   37.599700] PID hash table entries: 2048 (order: 11, 8192 bytes)
[   37.600774] Console: colour VGA+ 80x25
[   37.601108] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
[   37.601407] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
[   37.611454] Memory: 508728k/524208k available (1993k kernel code, 14956k reserved, 900k data, 328k init, 0k highmem)
[   37.611464] virtual kernel memory layout:
[   37.611465]     fixmap  : 0xfff4e000 - 0xfffff000   ( 708 kB)
[   37.611467]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   37.611468]     vmalloc : 0xe0800000 - 0xff7fe000   ( 495 MB)
[   37.611469]     lowmem  : 0xc0000000 - 0xdffec000   ( 511 MB)
[   37.611470]       .init : 0xc03d9000 - 0xc042b000   ( 328 kB)
[   37.611471]       .data : 0xc02f2434 - 0xc03d36d4   ( 900 kB)
[   37.611472]       .text : 0xc0100000 - 0xc02f2434   (1993 kB)
[   37.611475] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   37.687596] Calibrating delay using timer specific routine.. 5330.57 BogoMIPS (lpj=10661156)
[   37.687638] Security Framework v1.0.0 initialized
[   37.687645] SELinux:  Disabled at boot.
[   37.687662] Mount-cache hash table entries: 512
[   37.687810] CPU: After generic identify, caps: bfebfbff 00000000 00000000 00000000 00000400 00000000 00000000
[   37.687823] CPU: Trace cache: 12K uops, L1 D cache: 8K
[   37.687826] CPU: L2 cache: 512K
[   37.687829] CPU: Hyper-Threading is disabled
[   37.687831] CPU: After all inits, caps: bfebfbff 00000000 00000000 00003080 00000400 00000000 00000000
[   37.687842] Compat vDSO mapped to ffffe000.
[   37.687845] Remapping vsyscall page to ffffe000
[   37.687858] Checking 'hlt' instruction... OK.
[   37.703669] SMP alternatives: switching to UP code
[   37.703845] Freeing SMP alternatives: 11k freed
[   37.704044] Early unpacking initramfs... done
[   37.992359] ACPI: Core revision 20060707
[   37.993284] ACPI: Looking for DSDT in initramfs... file /DSDT.aml not found, using machine DSDT.
[   37.994410] CPU0: Intel(R) Pentium(R) 4 CPU 2.40GHz stepping 07
[   37.994453] Total of 1 processors activated (5330.57 BogoMIPS).
[   37.994576] ENABLING IO-APIC IRQs
[   37.994760] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[   38.139078] Brought up 1 CPUs
[   38.139326] Booting paravirtualized kernel on bare hardware
[   38.139402] Time: 11:06:34  Date: 08/06/107
[   38.139432] NET: Registered protocol family 16
[   38.139524] EISA bus registered
[   38.139529] ACPI: bus type pci registered
[   38.141416] PCI: PCI BIOS revision 2.10 entry at 0xf1670, last bus=2
[   38.141419] PCI: Using configuration type 1
[   38.141421] Setting up standard PCI resources
[   38.150122] ACPI: Interpreter enabled
[   38.150126] ACPI: Using IOAPIC for interrupt routing
[   38.150808] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
[   38.151034] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[   38.151240] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[   38.151456] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 *5 6 7 9 10 11 12 14 15)
[   38.151660] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[   38.151862] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[   38.152068] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[   38.152281] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 *9 10 11 12 14 15)
[   38.152382] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   38.152389] PCI: Probing PCI hardware (bus 00)
[   38.152719] ACPI: Assume root bridge [\_SB_.PCI0] bus is 0
[   38.153004] PCI: Enabled i801 SMBus device
[   38.153011] PCI quirk: region e400-e47f claimed by ICH4 ACPI/GPIO/TCO
[   38.153015] PCI quirk: region ec00-ec3f claimed by ICH4 GPIO
[   38.153276] Boot video device is 0000:01:00.0
[   38.153763] PCI: Transparent bridge - 0000:00:1e.0
[   38.153788] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   38.154869] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCI1._PRT]
[   38.155015] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCI2._PRT]
[   38.160220] Linux Plug and Play Support v0.97 (c) Adam Belay
[   38.160233] pnp: PnP ACPI init
[   38.165258] pnp: PnP ACPI: found 14 devices
[   38.165263] PnPBIOS: Disabled by ACPI PNP
[   38.165318] PCI: Using ACPI for IRQ routing
[   38.165322] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   38.173357] NET: Registered protocol family 8
[   38.173360] NET: Registered protocol family 20
[   38.173624] pnp: 00:02: ioport range 0xe400-0xe47f could not be reserved
[   38.173627] pnp: 00:02: ioport range 0xe800-0xe81f could not be reserved
[   38.173630] pnp: 00:02: ioport range 0xec00-0xec3f has been reserved
[   38.173632] pnp: 00:02: ioport range 0x4d6-0x4d6 has been reserved
[   38.173647] pnp: 00:0d: ioport range 0x295-0x296 has been reserved
[   38.173956] PCI: Bridge: 0000:00:01.0
[   38.173959]   IO window: d000-dfff
[   38.173963]   MEM window: d7000000-d7ffffff
[   38.173967]   PREFETCH window: d8000000-efffffff
[   38.173972] PCI: Bridge: 0000:00:1e.0
[   38.173974]   IO window: b000-bfff
[   38.173980]   MEM window: cf000000-d6ffffff
[   38.173983]   PREFETCH window: disabled.
[   38.173995] PCI: Setting latency timer of device 0000:00:01.0 to 64
[   38.174004] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[   38.174034] NET: Registered protocol family 2
[   38.211029] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
[   38.211112] TCP established hash table entries: 16384 (order: 5, 131072 bytes)
[   38.211195] TCP bind hash table entries: 8192 (order: 4, 65536 bytes)
[   38.211237] TCP: Hash tables configured (established 16384 bind 8192)
[   38.211240] TCP reno registered
[   38.223060] checking if image is initramfs... it is
[   38.795268] Freeing initrd memory: 6760k freed
[   38.795460] Simple Boot Flag at 0x3a set to 0x1
[   38.795695] audit: initializing netlink socket (disabled)
[   38.795709] audit(1189076795.276:1): initialized
[   38.795846] VFS: Disk quotas dquot_6.5.1
[   38.795865] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   38.795918] io scheduler noop registered
[   38.795921] io scheduler anticipatory registered
[   38.795923] io scheduler deadline registered
[   38.795933] io scheduler cfq registered (default)
[   38.796199] isapnp: Scanning for PnP cards...
[   39.149516] isapnp: No Plug & Play device found
[   39.175799] Real Time Clock Driver v1.12ac
[   39.175853] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   39.175963] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   39.176130] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[   39.176775] 00:0a: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   39.177079] 00:0b: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[   39.177318] mice: PS/2 mouse device common for all mice
[   39.177987] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   39.178242] input: Macintosh mouse button emulation as /class/input/input0
[   39.178279] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[   39.178283] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[   39.178514] PNP: PS/2 Controller [PNP0303:PS2K] at 0x60,0x64 irq 1
[   39.178517] PNP: PS/2 controller doesn't have AUX irq; using default 12
[   39.181711] serio: i8042 KBD port at 0x60,0x64 irq 1
[   39.181718] serio: i8042 AUX port at 0x60,0x64 irq 12
[   39.181889] EISA: Probing bus 0 at eisa.0
[   39.181923] EISA: Detected 0 cards.
[   39.211988] TCP cubic registered
[   39.211995] NET: Registered protocol family 1
[   39.212017] Using IPI No-Shortcut mode
[   39.212081] ACPI: (supports S0 S1 S4 S5)
[   39.212126]   Magic number: 7:697:124
[   39.212648] Freeing unused kernel memory: 328k freed
[   39.213688] Time: tsc clocksource has been installed.
[   39.226941] input: AT Translated Set 2 keyboard as /class/input/input1
[   40.474510] ACPI: Invalid PBLK length [5]
[   40.474546] ACPI Exception (acpi_processor-0677): AE_NOT_FOUND, Processor Device is not present [20060707]
[   41.005385] usbcore: registered new interface driver usbfs
[   41.005409] usbcore: registered new interface driver hub
[   41.005434] usbcore: registered new device driver usb
[   41.006365] USB Universal Host Controller Interface driver v3.0
[   41.006421] ACPI: PCI Interrupt 0000:00:1f.2[D] -> GSI 19 (level, low) -> IRQ 16
[   41.006434] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[   41.006438] uhci_hcd 0000:00:1f.2: UHCI Host Controller
[   41.006588] uhci_hcd 0000:00:1f.2: new USB bus registered, assigned bus number 1
[   41.006615] uhci_hcd 0000:00:1f.2: irq 16, io base 0x0000a400
[   41.006726] usb usb1: configuration #1 chosen from 1 choice
[   41.006753] hub 1-0:1.0: USB hub found
[   41.006760] hub 1-0:1.0: 2 ports detected
[   41.040824] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
[   41.084222] SCSI subsystem initialized
[   41.089793] libata version 2.20 loaded.
[   41.107632] ACPI: PCI Interrupt 0000:00:1f.4[C] -> GSI 23 (level, low) -> IRQ 17
[   41.107646] PCI: Setting latency timer of device 0000:00:1f.4 to 64
[   41.107650] uhci_hcd 0000:00:1f.4: UHCI Host Controller
[   41.107673] uhci_hcd 0000:00:1f.4: new USB bus registered, assigned bus number 2
[   41.107700] uhci_hcd 0000:00:1f.4: irq 17, io base 0x0000a000
[   41.107793] usb usb2: configuration #1 chosen from 1 choice
[   41.107819] hub 2-0:1.0: USB hub found
[   41.107827] hub 2-0:1.0: 2 ports detected
[   41.211659] PCI: Enabling device 0000:02:04.0 (0014 -> 0016)
[   41.211671] ACPI: PCI Interrupt 0000:02:04.0[A] -> GSI 21 (level, low) -> IRQ 18
[   41.211686] ohci_hcd 0000:02:04.0: OHCI Host Controller
[   41.211718] ohci_hcd 0000:02:04.0: new USB bus registered, assigned bus number 3
[   41.211735] ohci_hcd 0000:02:04.0: irq 18, io mem 0xd6800000
[   41.226664] Floppy drive(s): fd0 is 1.44M
[   41.256241] FDC 0 is a post-1991 82077
[   41.781063] usb usb3: configuration #1 chosen from 1 choice
[   41.781095] hub 3-0:1.0: USB hub found
[   41.781104] hub 3-0:1.0: 3 ports detected
[   41.826562] usb 1-1: new low speed USB device using uhci_hcd and address 2
[   42.005257] usb 1-1: configuration #1 chosen from 1 choice
[   42.019359] usbcore: registered new interface driver hiddev
[   42.035384] input: Razer Razer Diamondback Optical Mouse as /class/input/input2
[   42.035501] input: USB HID v1.10 Mouse [Razer Razer Diamondback Optical Mouse] on usb-0000:00:1f.2-1
[   42.035517] usbcore: registered new interface driver usbhid
[   42.035521] drivers/usb/input/hid-core.c: v2.6:USB HID core driver
[   42.294119] PCI: Enabling device 0000:02:04.2 (0014 -> 0016)
[   42.294127] ACPI: PCI Interrupt 0000:02:04.2[C] -> GSI 23 (level, low) -> IRQ 17
[   42.294142] ehci_hcd 0000:02:04.2: EHCI Host Controller
[   42.294166] ehci_hcd 0000:02:04.2: new USB bus registered, assigned bus number 4
[   42.317963] ehci_hcd 0000:02:04.2: irq 17, io mem 0xd5800000
[   42.317972] ehci_hcd 0000:02:04.2: USB 2.0 started, EHCI 0.95, driver 10 Dec 2004
[   42.318079] usb usb4: configuration #1 chosen from 1 choice
[   42.318110] hub 4-0:1.0: USB hub found
[   42.318120] hub 4-0:1.0: 5 ports detected
[   42.423899] ata_piix 0000:00:1f.1: version 2.10ac1
[   42.423929] PCI: Setting latency timer of device 0000:00:1f.1 to 64
[   42.423986] ata1: PATA max UDMA/100 cmd 0x000101f0 ctl 0x000103f6 bmdma 0x0001a800 irq 14
[   42.424020] ata2: PATA max UDMA/100 cmd 0x00010170 ctl 0x00010376 bmdma 0x0001a808 irq 15
[   42.424040] scsi0 : ata_piix
[   42.424196] PCI: Enabling device 0000:02:04.1 (0014 -> 0016)
[   42.424206] ACPI: PCI Interrupt 0000:02:04.1[B] -> GSI 22 (level, low) -> IRQ 19
[   42.424218] ohci_hcd 0000:02:04.1: OHCI Host Controller
[   42.424246] ohci_hcd 0000:02:04.1: new USB bus registered, assigned bus number 5
[   42.424260] ohci_hcd 0000:02:04.1: irq 19, io mem 0xd6000000
[   42.984360] usb usb5: configuration #1 chosen from 1 choice
[   42.984561] hub 5-0:1.0: USB hub found
[   42.984574] hub 5-0:1.0: 2 ports detected
[   43.020521] ata1.00: ata_hpa_resize 1: sectors = 488397168, hpa_sectors = 488397168
[   43.020526] ata1.00: ATA-7: WDC WD2500JB-00REA0, 20.00K20, max UDMA/100
[   43.020529] ata1.00: 488397168 sectors, multi 16: LBA48 
[   43.020705] ata1.01: ata_hpa_resize 1: sectors = 320173056, hpa_sectors = 320173056
[   43.020707] ata1.01: ATA-7: Maxtor 6Y160P0, YAR41BW0, max UDMA/133
[   43.020710] ata1.01: 320173056 sectors, multi 16: LBA48 
[   43.029425] ata1.00: ata_hpa_resize 1: sectors = 488397168, hpa_sectors = 488397168
[   43.029428] ata1.00: configured for UDMA/100
[   43.037432] ata1.01: ata_hpa_resize 1: sectors = 320173056, hpa_sectors = 320173056
[   43.037435] ata1.01: configured for UDMA/100
[   43.037447] scsi1 : ata_piix
[   43.356873] ata2.00: ATAPI, max UDMA/33
[   73.320229] ata2.00: qc timeout (cmd 0xef)
[   73.320238] ata2.00: failed to set xfermode (err_mask=0x4)
[   73.320243] ata2: failed to recover some devices, retrying in 5 secs
[  108.601274] ata2.00: qc timeout (cmd 0xef)
[  108.601283] ata2.00: failed to set xfermode (err_mask=0x4)
[  108.601289] ata2.00: limiting speed to UDMA/33:PIO3
[  108.601291] ata2: failed to recover some devices, retrying in 5 secs
[  143.882319] ata2.00: qc timeout (cmd 0xef)
[  143.882328] ata2.00: failed to set xfermode (err_mask=0x4)
[  143.882332] ata2.00: disabled
[  144.385825] scsi 0:0:0:0: Direct-Access     ATA      WDC WD2500JB-00R 20.0 PQ: 0 ANSI: 5
[  144.386218] scsi 0:0:1:0: Direct-Access     ATA      Maxtor 6Y160P0   YAR4 PQ: 0 ANSI: 5
[  144.401330] SCSI device sda: 488397168 512-byte hdwr sectors (250059 MB)
[  144.401352] sda: Write Protect is off
[  144.401355] sda: Mode Sense: 00 3a 00 00
[  144.401373] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[  144.401435] SCSI device sda: 488397168 512-byte hdwr sectors (250059 MB)
[  144.401446] sda: Write Protect is off
[  144.401448] sda: Mode Sense: 00 3a 00 00
[  144.401465] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[  144.401471]  sda: sda1 sda2 sda3 sda4 < sda5 >
[  144.434092] sd 0:0:0:0: Attached scsi disk sda
[  144.434247] SCSI device sdb: 320173056 512-byte hdwr sectors (163929 MB)
[  144.434260] sdb: Write Protect is off
[  144.434263] sdb: Mode Sense: 00 3a 00 00
[  144.434281] SCSI device sdb: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[  144.434326] SCSI device sdb: 320173056 512-byte hdwr sectors (163929 MB)
[  144.434336] sdb: Write Protect is off
[  144.434339] sdb: Mode Sense: 00 3a 00 00
[  144.434356] SCSI device sdb: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[  144.434360]  sdb: sdb1
[  144.442648] sd 0:0:1:0: Attached scsi disk sdb
[  144.447419] sd 0:0:0:0: Attached scsi generic sg0 type 0
[  144.447533] sd 0:0:1:0: Attached scsi generic sg1 type 0
[  144.755899] Attempting manual resume
[  144.755903] swsusp: Resume From Partition 8:5
[  144.755905] PM: Checking swsusp image.
[  144.756120] PM: Resume from disk failed.
[  144.789413] kjournald starting.  Commit interval 5 seconds
[  144.789426] EXT3-fs: mounted filesystem with ordered data mode.
[  155.229520] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[  155.254803] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[  155.345681] Linux agpgart interface v0.102 (c) Dave Jones
[  155.352206] intel_rng: FWH not detected
[  155.354623] agpgart: Detected an Intel i850 Chipset.
[  155.359816] agpgart: AGP aperture is 128M @ 0xf0000000
[  155.385875] iTCO_vendor_support: vendor-support=0
[  155.387007] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.01 (11-Nov-2006)
[  155.387096] iTCO_wdt: failed to reset NO_REBOOT flag, reboot disabled by hardware
[  155.387105] iTCO_wdt: No card detected
[  155.934526] input: PC Speaker as /class/input/input3
[  156.007418] parport: PnPBIOS parport detected.
[  156.007509] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,EPP,ECP,DMA]
[  156.032128] acx: Loaded combined PCI/USB driver, firmware_ver=default
[  156.032132] acx: compiled to use 32bit I/O access. I/O timing issues might occur, such as non-working firmware upload. Report them
[  156.032190] PCI: Enabling device 0000:02:0d.0 (0004 -> 0006)
[  156.032201] ACPI: PCI Interrupt 0000:02:0d.0[A] -> GSI 18 (level, low) -> IRQ 20
[  156.032215] acx: found ACX111-based wireless network card at 0000:02:0d.0, irq:20, phymem1:0xCF800000, phymem2:0xCF000000, mem1:0xe0924000, mem1_size:8192, mem2:0xe0a40000, mem2_size:131072
[  156.033217] acx: loading firmware for acx1111 chipset with radio ID 16
[  157.034777] NVS_vendor_offs:01CD probe_delay:200 eof_memory:1114112
[  157.034782] CCAModes:04 Diversity:01 ShortPreOpt:01 PBCC:01 ChanAgil:00 PHY:05 Temp:01
[  157.034785] AntennaID:00 Len:02 Data:01 02 
[  157.034788] PowerLevelID:01 Len:02 Data:001E 000A 
[  157.034792] DataRatesID:02 Len:05 Data:02 04 11 22 44 
[  157.034797] DomainID:03 Len:06 Data:30 20 30 31 32 40 
[  157.034802] ProductID:04 Len:09 Data:TI ACX100
[  157.034805] ManufacturerID:05 Len:07 Data:TI Test
[  157.094231] acx: === chipset TNETW1130, radio type 0x16 (Radia), form factor 0x01 ((mini-)PCI / CardBus), EEPROM version 0x05: uploaded firmware 'Rev 1.2.1.34' ===
[  157.094359] acx v0.3.36: net device wlan0, driver compiled against wireless extensions 21 and Linux 2.6.20-16-generic
[  157.094408] usbcore: registered new interface driver acx_usb
[  157.094913] PCI: Enabling device 0000:02:0c.1 (0004 -> 0005)
[  157.110536] gameport: EMU10K1 is pci0000:02:0c.1/gameport0, io 0xb000, speed 1046kHz
[  157.112288] PCI: Enabling device 0000:02:0c.0 (0004 -> 0005)
[  157.112301] ACPI: PCI Interrupt 0000:02:0c.0[A] -> GSI 20 (level, low) -> IRQ 21
[  157.353555] fuse init (API version 7.8)
[  157.374569] lp0: using parport0 (interrupt-driven).
[  157.409481] Adding 1510068k swap on /dev/disk/by-uuid/4d38ff3f-a021-4748-966f-2e7eae4fa0c0.  Priority:-1 extents:1 across:1510068k
[  157.547358] EXT3 FS on sda3, internal journal
[  158.510384] NET: Registered protocol family 17
[  161.386961] NET: Registered protocol family 10
[  161.387060] lo: Disabled Privacy Extensions
[  162.282006] wlan0: duplicate address detected!
[  163.245183] input: Power Button (FF) as /class/input/input4
[  163.249525] ACPI: Power Button (FF) [PWRF]
[  163.281496] input: Power Button (CM) as /class/input/input5
[  163.285742] ACPI: Power Button (CM) [PWRB]
[  163.377279] Using specific hotkey driver
[  163.482820] ibm_acpi: ec object not found
[  163.524333] No dock devices found.
[  163.592496] pcc_acpi: loading...
[  188.604484] ppdev: user-space parallel port driver
[  190.193298] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
[  190.200816] [fglrx] Maximum main memory to use for locked dma buffers: 431 MBytes.
[  190.201098] [fglrx] module loaded - fglrx 8.34.8 [Feb 20 2007] on minor 0
[  190.497525] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 22
[  192.539529] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[  192.539535] apm: overridden by ACPI.
[  193.045660] [fglrx] Internal AGP support requested, but kernel AGP support active.
[  193.045669] [fglrx] Have to use kernel AGP support to avoid conflicts.
[  193.045674] [fglrx] AGP detected, AgpState   = 0x1f000217 (hardware caps of chipset)
[  193.046351] agpgart: Found an AGP 2.0 compliant device at 0000:00:00.0.
[  193.046550] agpgart: Putting AGP V2 device at 0000:00:00.0 into 4x mode
[  193.046729] agpgart: Putting AGP V2 device at 0000:01:00.0 into 4x mode
[  193.046938] [fglrx] AGP enabled,  AgpCommand = 0x1f000314 (selected caps)
[  193.055931] [fglrx] total      GART = 134217728
[  193.055940] [fglrx] free       GART = 118222848
[  193.055942] [fglrx] max single GART = 118222848
[  193.055944] [fglrx] total      LFB  = 134217728
[  193.055946] [fglrx] free       LFB  = 94367744
[  193.055949] [fglrx] max single LFB  = 94367744
[  193.055950] [fglrx] total      Inv  = 0
[  193.055952] [fglrx] free       Inv  = 0
[  193.055954] [fglrx] max single Inv  = 0
[  193.055956] [fglrx] total      TIM  = 0
[  195.566575] Installing knfsd (copyright (C) 1996 okir@monad.swb.de).
[  195.710636] NFSD: Using /var/lib/nfs/v4recovery as the NFSv4 state recovery directory
[  195.711030] NFSD: starting 90-second grace period
[  196.909232] Bluetooth: Core ver 2.11
[  196.909291] NET: Registered protocol family 31
[  196.909293] Bluetooth: HCI device and connection manager initialized
[  196.909297] Bluetooth: HCI socket layer initialized
[  196.944339] Bluetooth: L2CAP ver 2.8
[  196.944343] Bluetooth: L2CAP socket layer initialized
[  197.199193] Bluetooth: RFCOMM socket layer initialized
[  197.199208] Bluetooth: RFCOMM TTY layer initialized
[  197.199210] Bluetooth: RFCOMM ver 1.8

```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=a3f2c8d8-7a9b-4978-8425-287620776715 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=4d38ff3f-a021-4748-966f-2e7eae4fa0c0 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

---

### Post by banewman on 2007-09-06
Well, according to fstab it is mounted in /media. Try this in a terminal - type the one word - eject. If the system can "see" the cd drive the tray will open. Always a good first check for this problem. :)

---

### Post by LokeTheDog on 2007-09-06
That didnt work. Gave me some error message, but its in swedish, and I guess its not that important anyway... Anyway, when I check in media, there is a directory there called cdrom0, but there's nothing in there. So I guess it hasn't mounted correctty. 

Whats next? :)

---

### Post by banewman on 2007-09-07
The eject error message would have been helpful to know as it would give an indication of what is going on. When I don't have a cd in the drive my /media/cdrom0 folder is mt but it is full when I put a written cd in the drive. Look there again when a written cd is in the drive and if it is mt then try the eject command in the terminal and tell us the error message pls. :)

---

### Post by LokeTheDog on 2007-09-07
I had a written cd in it when I checked...

The eject message is as follows.

eject: försökte använda "/dev/scd0" som ett enhetsnamn men det är ingen blockenhet
eject: kunde inte hitta eller öppna enheten för: "cdrom"

which translates to:

tried to use "/dev/scd0" as a device name but its not a block device
could not find or open the device for: "cdrom"

---

### Post by banewman on 2007-09-07
OK. The fact that it is listed in fstab and there is a folder for it - /media/cdrom0 - means that the system has found it, but you can't use it. Now so the next step - there is a file - /etc/mtab - that lists all devices known to the system during this session, can you check it for a listing for the cd drive?

---

### Post by LokeTheDog on 2007-09-09
/dev/sda3 / ext3 rw,errors=remount-ro 0 0
proc /proc proc rw,noexec,nosuid,nodev 0 0
/sys /sys sysfs rw,noexec,nosuid,nodev 0 0
varrun /var/run tmpfs rw,noexec,nosuid,nodev,mode=0755 0 0
varlock /var/lock tmpfs rw,noexec,nosuid,nodev,mode=1777 0 0
procbususb /proc/bus/usb usbfs rw 0 0
udev /dev tmpfs rw,mode=0755 0 0
devshm /dev/shm tmpfs rw 0 0
devpts /dev/pts devpts rw,gid=5,mode=620 0 0
lrm /lib/modules/2.6.20-16-generic/volatile tmpfs rw 0 0
nfsd /proc/fs/nfsd nfsd rw 0 0
rpc_pipefs /var/lib/nfs/rpc_pipefs rpc_pipefs rw 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw 0 0

Doesn't seem to be there, does it? 

If someone with the same problem happens to read this thread, there is another thread: [http://ubuntuforums.org/showthread.php?t=540008](http://ubuntuforums.org/showthread.php?t=540008) which deals with what seems to be the same problem. There's no solution in there, but on the last page, someone says that it works in Gutsy, so hopefully, its release will solve it if nothing else does.

---

### Post by banewman on 2007-09-09
OK, started with the easiest options first. In your dmesg there is a line that says :
"38.165322] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report"
The kernel is having an issue with the interrupt requests and the way around this is to add to the first kernel line in menu.lst  So type :
" sudo gedit /boot/grub/menu.lst " at the terminal prompt, then give your password. Scroll down towards the bottom and you will see the entry " end default options". Three lines under that the line starts " kernel " and ends with " quiet splash ". Add to the end of that line by typing - noapic nolapic - then save the file and reboot. That in the majority of cases solves the problem but sometimes other wording is needed. If it doesn't get the cd working and everything else working at the same time re-edit menu.lst, replacing    " noapic nolapic " with one of the following
 noapic acpi=noirq
OR
 noapic acpi=off
OR
 noapictimer
OR
 noapictimer irqpoll
OR
 noapic acpi=off
OR
 noapic acpi=noirq nolapic
until you get all devices working. The first option, as I said, works in the majority of cases. :)

---

### Post by LokeTheDog on 2007-09-10
None of them worked :(

---

### Post by banewman on 2007-09-10
Time to throw in the live cd to see if it works or open the box and check the cables. :)
New post page two...

---

### Post by banewman on 2007-09-10
If that checks out ok then the next step :
At the grub menu use the keyboard to select the kernel that you normally boot
press the " e " key on your keyboard
A new menu comes up. Select the kernel option with the arrow keys
Press the " e" key
At the end of the line type a space then " nofb irqpoll " without the quotes
Press enter
Press the " b " key and the system should boot and hopefully have the cd working. :)

---

### Post by LokeTheDog on 2007-09-11
The strangest thing just happened: 

I booted with the live CD, and selected "boot from hard drive" in the live CD menu. And that worked: Now my CD drive works just fine in ubuntu. What's your theory on that?

---

### Post by banewman on 2007-09-11
I have absolutely no idea. Glad it is working for you! I was convinced from rereading your dmesg that it was a loose cable...Hope it continues to work well. :lolflag:

---

### Post by Tavathlon on 2007-09-26
*bumping*

Have the same problem, exactly - except that it did not help to choose "boot from hard drive" when starting with the live cd inserted...  Also, I use Gutsy, so the "fix" suggested in the other thread (upgrading to Gutsy) is not really of any help to me...  *rolleyes*

There are some different threads on this issue, I'm trying to bump them up - seems to be some people having this problem out there. I'm one of them..  =P

Anyone who have had the time to look into it yet?

---

### Post by banewman on 2007-09-26
Tavathlon - the first post here says the drive worked sometimes in ubuntu so I'm pretty sure this case was a loose cable... maybe. Doesn't help you much but if you look at his dmesg you will see where the system timed out looking for the drive. Run dmesg and check for something similar - might be something simple like a loose cable. Worth checking just to save the frustration. :)

---

### Post by Tavathlon on 2007-09-26
Thank you banewman, but I don't think there is any loose cables - the drive works perfectly when Ubuntu is not running (I installed Ubuntu using it, and I am still able to boot from a live cd at any time - it's just when Ubuntu is running that I can't access it), and it's somewhat difficult for me to check the cables anyway since it's a laptop...  =P

So probably, the problem might not be the same, but the symptom is - the error message that comes up when I try to access the cdrom.

---

### Post by Fidelio on 2007-09-26
I've got this too with Feisty, It was fine with Edgy, worked fine to start with in Feisty, but suddenly stopped. I don't know if it's coincidental, but it also started taking ages to boot. 
CD drive is fine in windows. It looks more like a bug than a loose wire to me.

---

### Post by Tavathlon on 2007-09-26
Hm, I actually managed to solve it now, though, following the advice in this thread: [http://ubuntuforums.org/showthread.php?p=3426098](http://ubuntuforums.org/showthread.php?p=3426098) about fiddling around in BIOS. I changed the cdrom setting from 'auto' to 'user', and then it worked...  So perhaps that would be something worth trying?

Well, problem solved for me now anyway, I hope it'll be the same thing for everyone else with this quite annoying problem...  =P

---

### Post by pt123 on 2007-09-28
If you are getting failed to set xfermode on older CD drives try this solution:
[http://fak3r.com/2007/06/22/failed-to-set-xfermode-solved/](http://fak3r.com/2007/06/22/failed-to-set-xfermode-solved/)

In grub, &#8220;&#8230;at the end of this new menu item add it as an argument to the line:
```

# defoptions=quiet splash irqpoll

```


You just need to ad `irqpoll` to your grub line. So in so in /boot/grub/menu.lst I added irqpoll to the kernel line:
```

kernel /boot/vmlinuz-2.6.20-15-generic root=UUID=495b ro quiet splash irqpoll

```

---

### Post by LokeTheDog on 2007-10-04
> **banewman said:**
> Tavathlon - the first post here says the drive worked sometimes in ubuntu so I'm pretty sure this case was a loose cable... maybe. Doesn't help you much but if you look at his dmesg you will see where the system timed out looking for the drive. Run dmesg and check for something similar - might be something simple like a loose cable. Worth checking just to save the frustration. :)

Well, would a lose cable work in windows every time? That just seems strange to me...

---

