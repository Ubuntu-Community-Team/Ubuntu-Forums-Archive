---
title: "Ubuntu + Usb = ?Hell?"
date: 2007-03-23
forum: Hardware &amp; Laptops
---

### Post by RaZoR-x11 on 2007-03-23
Hey there,

This has happend once before but, now it's happend again, Right the problem is the usb
it work's love for about 15 min's or so but this is  random and then it slow's right down,
the usb on the mobo is 2.0 but in the device manger it's 1.1, So my guess would be that the wrong driver's are bin used or ?

Thank's in advance.

---

### Post by apjone on 2007-03-23
Strange , check out dmesg from a console see if that gives any info.

---

### Post by RaZoR-x11 on 2007-03-25
Right this is what it came out with,
```

[COLOR=Red][17179569.184000] Linux version 2.6.17-11-generic (root@terranova) (gcc version 4.1.2 20060928 (prerelease) (Ubuntu 4.1.1-13ubuntu5)) #2 SMP Thu Feb 1 19:52:28 UTC 2007 (Ubuntu 2.6.17-11.35-generic)
[17179569.184000] BIOS-provided physical RAM map:
[17179569.184000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[17179569.184000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[17179569.184000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[17179569.184000]  BIOS-e820: 0000000000100000 - 000000000fff0000 (usable)
[17179569.184000]  BIOS-e820: 000000000fff0000 - 000000000fff8000 (ACPI data)
[17179569.184000]  BIOS-e820: 000000000fff8000 - 0000000010000000 (ACPI NVS)
[17179569.184000]  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
[17179569.184000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[17179569.184000]  BIOS-e820: 00000000fff80000 - 0000000100000000 (reserved)
[17179569.184000] 0MB HIGHMEM available.
[17179569.184000] 255MB LOWMEM available.
[17179569.184000] On node 0 totalpages: 65520
[17179569.184000]   DMA zone: 4096 pages, LIFO batch:0
[17179569.184000]   Normal zone: 61424 pages, LIFO batch:15
[17179569.184000] DMI 2.3 present.
[17179569.184000] ACPI: RSDP (v000 AMI                                   ) @ 0x000fa910
[17179569.184000] ACPI: RSDT (v001 AMIINT VIA_K7   0x00000010 MSFT 0x00000097) @ 0x0fff0000
[17179569.184000] ACPI: FADT (v001 AMIINT VIA_K7   0x00000011 MSFT 0x00000097) @ 0x0fff0030
[17179569.184000] ACPI: MADT (v001 AMIINT VIA_K7   0x00000009 MSFT 0x00000097) @ 0x0fff00c0
[17179569.184000] ACPI: DSDT (v001    VIA    K7VT4 0x00001000 MSFT 0x0100000d) @ 0x00000000
[17179569.184000] ACPI: PM-Timer IO Port: 0x808
[17179569.184000] ACPI: Local APIC address 0xfee00000
[17179569.184000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[17179569.184000] Processor #0 6:8 APIC version 16
[17179569.184000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[17179569.184000] IOAPIC[0]: apic_id 2, version 3, address 0xfec00000, GSI 0-23
[17179569.184000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[17179569.184000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 low level)
[17179569.184000] ACPI: IRQ0 used by override.
[17179569.184000] ACPI: IRQ2 used by override.
[17179569.184000] ACPI: IRQ9 used by override.
[17179569.184000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[17179569.184000] Using ACPI (MADT) for SMP configuration information
[17179569.184000] Allocating PCI resources starting at 20000000 (gap: 10000000:eec00000)
[17179569.184000] Built 1 zonelists
[17179569.184000] Kernel command line: root=/dev/hda2 ro quiet splash
[17179569.184000] mapped APIC to ffffd000 (fee00000)
[17179569.184000] mapped IOAPIC to ffffc000 (fec00000)
[17179569.184000] Enabling fast FPU save and restore... done.
[17179569.184000] Enabling unmasked SIMD FPU exception support... done.
[17179569.184000] Initializing CPU#0
[17179569.184000] PID hash table entries: 1024 (order: 10, 4096 bytes)
[17179569.184000] Detected 1398.928 MHz processor.
[17179569.184000] Using pmtmr for high-res timesource
[17179569.184000] Console: colour VGA+ 80x25
[17179572.804000] Dentry cache hash table entries: 32768 (order: 5, 131072 bytes)
[17179572.804000] Inode-cache hash table entries: 16384 (order: 4, 65536 bytes)
[17179572.812000] Memory: 250208k/262080k available (1911k kernel code, 11364k reserved, 1073k data, 308k init, 0k highmem)
[17179572.812000] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[17179572.892000] Calibrating delay using timer specific routine.. 2801.23 BogoMIPS (lpj=5602463)
[17179572.892000] Security Framework v1.0.0 initialized
[17179572.892000] SELinux:  Disabled at boot.
[17179572.892000] Mount-cache hash table entries: 512
[17179572.892000] CPU: After generic identify, caps: 0383fbff c1cbfbff 00000000 00000000 00000000 00000000 00000000
[17179572.892000] CPU: After vendor identify, caps: 0383fbff c1cbfbff 00000000 00000000 00000000 00000000 00000000
[17179572.892000] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[17179572.892000] CPU: L2 Cache: 256K (64 bytes/line)
[17179572.892000] CPU: After all inits, caps: 0383fbff c1cbfbff 00000000 00000420 00000000 00000000 00000000
[17179572.892000] Checking 'hlt' instruction... OK.
[17179572.908000] SMP alternatives: switching to UP code
[17179572.908000] Freeing SMP alternatives: 16k freed
[17179572.908000] checking if image is initramfs... it is
[17179573.556000] Freeing initrd memory: 5327k freed
[17179573.556000] ACPI: Core revision 20060707
[17179573.560000] ACPI: Looking for DSDT ... not found!
[17179573.564000] CPU0: AMD Athlon(tm) XP 1600+ stepping 01
[17179573.564000] Total of 1 processors activated (2801.23 BogoMIPS).
[17179573.564000] ENABLING IO-APIC IRQs
[17179573.564000] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[17179573.708000] Brought up 1 CPUs
[17179573.708000] migration_cost=0
[17179573.708000] NET: Registered protocol family 16
[17179573.708000] EISA bus registered
[17179573.708000] ACPI: bus type pci registered
[17179573.716000] PCI: PCI BIOS revision 2.10 entry at 0xfdae1, last bus=1
[17179573.716000] PCI: Using configuration type 1
[17179573.716000] Setting up standard PCI resources
[17179573.728000] ACPI: Interpreter enabled
[17179573.728000] ACPI: Using IOAPIC for interrupt routing
[17179573.728000] ACPI: PCI Root Bridge [PCI0] (0000:00)
[17179573.728000] PCI: Probing PCI hardware (bus 00)
[17179573.732000] PCI quirk: region 0800-087f claimed by vt8235 PM
[17179573.732000] PCI quirk: region 0400-040f claimed by vt8235 SMB
[17179573.732000] PCI: Ignoring BAR0-3 of IDE controller 0000:00:11.1
[17179573.732000] Boot video device is 0000:01:00.0
[17179573.732000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[17179573.748000] ACPI: Power Resource [URP1] (off)
[17179573.748000] ACPI: Power Resource [URP2] (off)
[17179573.748000] ACPI: Power Resource [FDDP] (off)
[17179573.748000] ACPI: Power Resource [LPTP] (off)
[17179573.748000] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 7 10 *11 12 14 15)
[17179573.748000] ACPI: PCI Interrupt Link [LNKB] (IRQs *3 4 5 7 10 11 12 14 15)
[17179573.752000] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 7 10 11 *12 14 15)
[17179573.752000] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 7 *10 11 12 14 15)
[17179573.752000] Linux Plug and Play Support v0.97 (c) Adam Belay
[17179573.752000] pnp: PnP ACPI init
[17179573.752000] pnp: PnP ACPI: found 8 devices
[17179573.752000] PnPBIOS: Disabled by ACPI PNP
[17179573.752000] PCI: Using ACPI for IRQ routing
[17179573.752000] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[17179573.756000] PCI: Bridge: 0000:00:01.0
[17179573.756000]   IO window: disabled.
[17179573.756000]   MEM window: dde00000-dfefffff
[17179573.756000]   PREFETCH window: cdd00000-ddcfffff
[17179573.756000] PCI: Setting latency timer of device 0000:00:01.0 to 64
[17179573.756000] NET: Registered protocol family 2
[17179573.788000] IP route cache hash table entries: 2048 (order: 1, 8192 bytes)
[17179573.788000] TCP established hash table entries: 8192 (order: 4, 65536 bytes)
[17179573.788000] TCP bind hash table entries: 4096 (order: 3, 32768 bytes)
[17179573.788000] TCP: Hash tables configured (established 8192 bind 4096)
[17179573.788000] TCP reno registered
[17179573.788000] audit: initializing netlink socket (disabled)
[17179573.788000] audit(1174851291.788:1): initialized
[17179573.788000] VFS: Disk quotas dquot_6.5.1
[17179573.788000] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[17179573.788000] Initializing Cryptographic API
[17179573.788000] io scheduler noop registered
[17179573.788000] io scheduler anticipatory registered
[17179573.788000] io scheduler deadline registered
[17179573.788000] io scheduler cfq registered (default)
[17179573.788000] isapnp: Scanning for PnP cards...
[17179574.144000] isapnp: No Plug & Play device found
[17179574.176000] Real Time Clock Driver v1.12ac
[17179574.176000] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[17179574.176000] mice: PS/2 mouse device common for all mice
[17179574.176000] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[17179574.176000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[17179574.176000] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[17179574.176000] PNP: PS/2 Controller [PNP0303:PS2K] at 0x60,0x64 irq 1
[17179574.176000] PNP: PS/2 controller doesn't have AUX irq; using default 12
[17179574.176000] serio: i8042 AUX port at 0x60,0x64 irq 12
[17179574.176000] serio: i8042 KBD port at 0x60,0x64 irq 1
[17179574.176000] EISA: Probing bus 0 at eisa.0
[17179574.176000] EISA: Detected 0 cards.
[17179574.176000] TCP bic registered
[17179574.176000] NET: Registered protocol family 1
[17179574.176000] NET: Registered protocol family 8
[17179574.176000] NET: Registered protocol family 20
[17179574.176000] Using IPI No-Shortcut mode
[17179574.176000] ACPI: (supports S0 S1 S4 S5)
[17179574.180000] Freeing unused kernel memory: 308k freed
[17179574.224000] input: AT Translated Set 2 keyboard as /class/input/input0
[17179575.340000] Capability LSM initialized
[17179576.020000] VP_IDE: IDE controller at PCI slot 0000:00:11.1
[17179576.020000] ACPI: Unable to derive IRQ for device 0000:00:11.1
[17179576.020000] ACPI: PCI Interrupt 0000:00:11.1[A]: no GSI
[17179576.020000] PCI: Via IRQ fixup for 0000:00:11.1, from 255 to 15
[17179576.020000] VP_IDE: chipset revision 6
[17179576.020000] VP_IDE: not 100% native mode: will probe irqs later
[17179576.020000] VP_IDE: VIA vt8235 (rev 00) IDE UDMA133 controller on pci0000:00:11.1
[17179576.020000]     ide0: BM-DMA at 0xfc00-0xfc07, BIOS settings: hda:DMA, hdb:pio
[17179576.020000]     ide1: BM-DMA at 0xfc08-0xfc0f, BIOS settings: hdc:DMA, hdd:pio
[17179576.020000] Probing IDE interface ide0...
[17179576.448000] hda: SAMSUNG SP2514N, ATA DISK drive
[17179577.164000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[17179577.168000] Probing IDE interface ide1...
[17179578.048000] hdc: ATAPI DVD DD 2X16X4X16, ATAPI CD/DVD-ROM drive
[17179578.724000] ide1 at 0x170-0x177,0x376 on irq 15
[17179578.732000] hda: max request size: 512KiB
[17179578.744000] hda: 488397168 sectors (250059 MB) w/8192KiB Cache, CHS=30401/255/63, UDMA(33)
[17179578.744000] hda: cache flushes supported
[17179578.744000]  hda: hda1 hda2 hda3 hda4
[17179578.788000] hdc: ATAPI 40X DVD-ROM DVD-R CD-R/RW drive, 2048kB Cache, UDMA(33)
[17179578.788000] Uniform CD-ROM driver Revision: 3.20
[17179579.116000] usbcore: registered new driver usbfs
[17179579.120000] usbcore: registered new driver hub
[17179579.120000] USB Universal Host Controller Interface driver v3.0
[17179579.124000] ACPI: PCI Interrupt 0000:00:10.0[A] -> GSI 21 (level, low) -> IRQ 169
[17179579.124000] PCI: Via IRQ fixup for 0000:00:10.0, from 11 to 9
[17179579.124000] uhci_hcd 0000:00:10.0: UHCI Host Controller
[17179579.124000] uhci_hcd 0000:00:10.0: new USB bus registered, assigned bus number 1
[17179579.124000] uhci_hcd 0000:00:10.0: irq 169, io base 0x0000dc00
[17179579.124000] usb usb1: configuration #1 chosen from 1 choice
[17179579.124000] hub 1-0:1.0: USB hub found
[17179579.124000] hub 1-0:1.0: 2 ports detected
[17179579.232000] ACPI: PCI Interrupt 0000:00:10.1[B] -> GSI 21 (level, low) -> IRQ 169
[17179579.232000] PCI: Via IRQ fixup for 0000:00:10.1, from 3 to 9
[17179579.232000] uhci_hcd 0000:00:10.1: UHCI Host Controller
[17179579.232000] uhci_hcd 0000:00:10.1: new USB bus registered, assigned bus number 2
[17179579.232000] uhci_hcd 0000:00:10.1: irq 169, io base 0x0000e000
[17179579.232000] usb usb2: configuration #1 chosen from 1 choice
[17179579.232000] hub 2-0:1.0: USB hub found
[17179579.232000] hub 2-0:1.0: 2 ports detected
[17179579.340000] ACPI: PCI Interrupt 0000:00:10.2[C] -> GSI 21 (level, low) -> IRQ 169
[17179579.340000] PCI: Via IRQ fixup for 0000:00:10.2, from 12 to 9
[17179579.340000] uhci_hcd 0000:00:10.2: UHCI Host Controller
[17179579.340000] uhci_hcd 0000:00:10.2: new USB bus registered, assigned bus number 3
[17179579.340000] uhci_hcd 0000:00:10.2: irq 169, io base 0x0000e400
[17179579.340000] usb usb3: configuration #1 chosen from 1 choice
[17179579.340000] hub 3-0:1.0: USB hub found
[17179579.340000] hub 3-0:1.0: 2 ports detected
[17179579.460000] ACPI: PCI Interrupt 0000:00:10.3[D] -> GSI 21 (level, low) -> IRQ 169
[17179579.460000] PCI: Via IRQ fixup for 0000:00:10.3, from 10 to 9
[17179579.460000] ehci_hcd 0000:00:10.3: EHCI Host Controller
[17179579.460000] ehci_hcd 0000:00:10.3: new USB bus registered, assigned bus number 4
[17179579.460000] ehci_hcd 0000:00:10.3: irq 169, io mem 0xdfffff00
[17179579.460000] ehci_hcd 0000:00:10.3: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[17179579.460000] usb usb4: configuration #1 chosen from 1 choice
[17179579.460000] hub 4-0:1.0: USB hub found
[17179579.460000] hub 4-0:1.0: 6 ports detected
[17179579.616000] Attempting manual resume
[17179579.632000] EXT3-fs: INFO: recovery required on readonly filesystem.
[17179579.632000] EXT3-fs: write access will be enabled during recovery.
[17179580.588000] usb 2-1: new low speed USB device using uhci_hcd and address 2
[17179580.776000] usb 2-1: configuration #1 chosen from 1 choice
[17179580.788000] usbcore: registered new driver hiddev
[17179580.808000] input: Logitech USB-PS/2 Optical Mouse as /class/input/input1
[17179580.808000] input: USB HID v1.10 Mouse [Logitech USB-PS/2 Optical Mouse] on usb-0000:00:10.1-1
[17179580.808000] usbcore: registered new driver usbhid
[17179580.808000] drivers/usb/input/hid-core.c: v2.6:USB HID core driver
[17179581.708000] kjournald starting.  Commit interval 5 seconds
[17179581.708000] EXT3-fs: recovery complete.
[17179581.708000] EXT3-fs: mounted filesystem with ordered data mode.
[17179591.204000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[17179591.208000] Linux agpgart interface v0.101 (c) Dave Jones
[17179591.220000] agpgart: Detected VIA KT400/KT400A/KT600 chipset
[17179591.228000] agpgart: AGP aperture is 128M @ 0xe0000000
[17179591.444000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[17179591.468000] irda_init()
[17179591.468000] NET: Registered protocol family 23
[17179591.544000] via-rhine.c:v1.10-LK1.2.0-2.6 June-10-2004 Written by Donald Becker
[17179591.544000] ACPI: PCI Interrupt 0000:00:12.0[A] -> GSI 23 (level, low) -> IRQ 177
[17179591.544000] PCI: Via IRQ fixup for 0000:00:12.0, from 11 to 1
[17179591.544000] eth0: VIA Rhine II at 0x1d800, 00:0b:6a:6e:f8:7f, IRQ 177.
[17179591.544000] eth0: MII PHY found at address 1, status 0x786d advertising 05e1 Link 45e1.
[17179591.792000] input: PC Speaker as /class/input/input2
[17179591.824000] gameport: EMU10K1 is pci0000:00:0b.1/gameport0, io 0xec00, speed 1217kHz
[17179592.088000] ACPI: PCI Interrupt 0000:00:0b.0[A] -> GSI 19 (level, low) -> IRQ 185
[17179592.324000] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[17179592.468000] ts: Compaq touchscreen protocol output
[17179593.356000] NET: Registered protocol family 17
[17179594.184000] floppy0: no floppy controllers found
[17179594.388000] lp: driver loaded but no devices found
[17179594.432000] Adding 1622556k swap on /dev/disk/by-uuid/2cae741d-ffe1-4481-a5a1-5f2039b95a55.  Priority:-1 extents:1 across:1622556k
[17179594.588000] EXT3 FS on hda2, internal journal
[17179608.464000] NET: Registered protocol family 10
[17179608.464000] lo: Disabled Privacy Extensions
[17179608.464000] IPv6 over IPv4 tunneling driver
[17179618.488000] eth0: no IPv6 routers present
[17179646.104000] APIC error on CPU0: 00(08)
[17179647.784000] kjournald starting.  Commit interval 5 seconds
[17179647.792000] EXT3 FS on hda3, internal journal
[17179647.792000] EXT3-fs: mounted filesystem with ordered data mode.
[17179656.492000] ACPI: Power Button (FF) [PWRF]
[17179656.492000] ACPI: Power Button (CM) [PWRB]
[17179656.492000] ACPI: Sleep Button (CM) [SLPB]
[17179656.648000] ibm_acpi: ec object not found
[17179656.692000] pcc_acpi: loading...
[17179663.128000] apm: BIOS not found.
[17179670.048000] Bluetooth: Core ver 2.8
[17179670.048000] NET: Registered protocol family 31
[17179670.048000] Bluetooth: HCI device and connection manager initialized
[17179670.048000] Bluetooth: HCI socket layer initialized
[17179670.136000] Bluetooth: L2CAP ver 2.8
[17179670.136000] Bluetooth: L2CAP socket layer initialized
[17179670.184000] Bluetooth: RFCOMM socket layer initialized
[17179670.184000] Bluetooth: RFCOMM TTY layer initialized
[17179670.184000] Bluetooth: RFCOMM ver 1.7
[17179709.048000] APIC error on CPU0: 08(02)
[17179733.016000] APIC error on CPU0: 02(08)
[17179779.496000] APIC error on CPU0: 08(04)
[17179810.284000] APIC error on CPU0: 04(08)[/COLOR]
```

---

### Post by timcredible on 2007-03-25
are you sure the usb 2.0 on the motherboard isn't connected to an external usb 1.1 hub or that the device is usb 1.1?  because mixing 1.1 and 2.0 on ubuntu doesn't seem to work properly for me (i don't know why)

---

