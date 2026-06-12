---
title: "ALI15X3: chipset revision 196  + Hang at startup."
date: 2007-02-14
forum: Hardware &amp; Laptops
---

### Post by thebrowser on 2007-02-14
Hi everyone,

My computer has some troubles loading linux.
When the computer just started on ubuntu, the progress bar hangs at something like 0.5% for about a minute. Then it starts progressing again, and everything is fine.
It is very frustrating to wait..

I have this issue booting on ubuntu, but also on Knoppix and Slax. However, it has no problem booting XP.

I think i have find out the lines in the dmesg where the the boot hangs.
```

[17179574.752000] Probing IDE interface ide1...
[17179585.176000] hdc: no response (status = 0xa1), resetting drive
[17179590.384000] hdc: no response (status = 0xa1)
[17179600.856000] hdd: no response (status = 0xa1), resetting drive
[17179606.064000] hdd: no response (status = 0xa1)
...
[17179651.744000] hdc: no response (status = 0xa1), resetting drive
[17179656.952000] hdc: no response (status = 0xa1)
[17179667.424000] hdd: no response (status = 0xa1), resetting drive
[17179672.632000] hdd: no response (status = 0xa1)

```

The fact that the kernel probes IDE interace is likely due to the kernel not supporting at hunderd percent the motherboard chipset.
```

[17179573.900000] ALI15X3: chipset revision 196
[17179573.900000] ALI15X3: not 100% native mode: will probe irqs later
[17179573.900000]     ide0: BM-DMA at 0xb400-0xb407, BIOS settings: hda:DMA, hdb:DMA
[17179573.900000]     ide1: BM-DMA at 0xb408-0xb40f, BIOS settings: hdc:pio, hdd:pio

```

Besides, after some search on google, i found that some other people having the same chipset "ALI15X3: chipset revision 196" are experiencing the same issue.

Here i am. I really dunno what to do next. Any help would be greatly welcom.
If you want any other information about my computer, just ask me.

thebrowser

Here is the complet dmesg:

```

[17179569.184000] Linux version 2.6.17-11-generic (root@terranova) (gcc version 4.1.2 20060928 (prerelease) (Ubuntu 4.1.1-13ubuntu5)) #2 SMP Thu Feb 1 19:52:28 UTC 2007 (Ubuntu 2.6.17-11.35-generic)
[17179569.184000] BIOS-provided physical RAM map:
[17179569.184000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[17179569.184000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[17179569.184000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[17179569.184000]  BIOS-e820: 0000000000100000 - 000000003ffec000 (usable)
[17179569.184000]  BIOS-e820: 000000003ffec000 - 000000003ffef000 (ACPI data)
[17179569.184000]  BIOS-e820: 000000003ffef000 - 000000003ffff000 (reserved)
[17179569.184000]  BIOS-e820: 000000003ffff000 - 0000000040000000 (ACPI NVS)
[17179569.184000]  BIOS-e820: 00000000ffff0000 - 0000000100000000 (reserved)
[17179569.184000] 127MB HIGHMEM available.
[17179569.184000] 896MB LOWMEM available.
[17179569.184000] On node 0 totalpages: 262124
[17179569.184000]   DMA zone: 4096 pages, LIFO batch:0
[17179569.184000]   Normal zone: 225280 pages, LIFO batch:31
[17179569.184000]   HighMem zone: 32748 pages, LIFO batch:7
[17179569.184000] DMI 2.3 present.
[17179569.184000] ACPI: RSDP (v000 ASUS                                  ) @ 0x000f7930
[17179569.184000] ACPI: RSDT (v001 ASUS   A7A266-E 0x42302e31 MSFT 0x31313031) @ 0x3ffec000
[17179569.184000] ACPI: FADT (v001 ASUS   A7A266-E 0x42302e31 MSFT 0x31313031) @ 0x3ffec080
[17179569.184000] ACPI: BOOT (v001 ASUS   A7A266-E 0x42302e31 MSFT 0x31313031) @ 0x3ffec040
[17179569.184000] ACPI: DSDT (v001   ASUS A7A266-E 0x00001000 MSFT 0x0100000b) @ 0x00000000
[17179569.184000] ACPI: PM-Timer IO Port: 0xe408
[17179569.184000] Allocating PCI resources starting at 50000000 (gap: 40000000:bfff0000)
[17179569.184000] Built 1 zonelists
[17179569.184000] Kernel command line: root=/dev/hda3 ro quiet splash
[17179569.184000] Local APIC disabled by BIOS (or by default) -- you can enable it with "lapic"
[17179569.184000] mapped APIC to ffffd000 (0180c000)
[17179569.184000] Enabling fast FPU save and restore... done.
[17179569.184000] Enabling unmasked SIMD FPU exception support... done.
[17179569.184000] Initializing CPU#0
[17179569.184000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[17179569.184000] Detected 1544.800 MHz processor.
[17179569.184000] Using pmtmr for high-res timesource
[17179569.184000] Console: colour VGA+ 80x25
[17179570.540000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[17179570.544000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[17179570.584000] Memory: 1029628k/1048496k available (1911k kernel code, 18108k reserved, 1073k data, 308k init, 130992k highmem)
[17179570.584000] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[17179570.664000] Calibrating delay using timer specific routine.. 3091.78 BogoMIPS (lpj=6183560)
[17179570.664000] Security Framework v1.0.0 initialized
[17179570.664000] SELinux:  Disabled at boot.
[17179570.664000] Mount-cache hash table entries: 512
[17179570.664000] CPU: After generic identify, caps: 0383f9ff c1cbf9ff 00000000 00000000 00000000 00000000 00000000
[17179570.664000] CPU: After vendor identify, caps: 0383f9ff c1cbf9ff 00000000 00000000 00000000 00000000 00000000
[17179570.664000] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[17179570.664000] CPU: L2 Cache: 256K (64 bytes/line)
[17179570.664000] CPU: After all inits, caps: 0383f9ff c1cbf9ff 00000000 00000420 00000000 00000000 00000000
[17179570.664000] Checking 'hlt' instruction... OK.
[17179570.680000] SMP alternatives: switching to UP code
[17179570.680000] Freeing SMP alternatives: 16k freed
[17179570.680000] checking if image is initramfs... it is
[17179571.272000] Freeing initrd memory: 5326k freed
[17179571.272000] ACPI: Core revision 20060707
[17179571.272000] ACPI: Looking for DSDT ... not found!
[17179571.272000] ACPI: setting ELCR to 0200 (from 0a00)
[17179571.272000] CPU0: AMD Athlon(TM) XP1800+ stepping 02
[17179571.272000] SMP motherboard not detected.
[17179571.272000] Local APIC not detected. Using dummy APIC emulation.
[17179571.272000] Brought up 1 CPUs
[17179571.272000] migration_cost=0
[17179571.272000] NET: Registered protocol family 16
[17179571.272000] EISA bus registered
[17179571.272000] ACPI: bus type pci registered
[17179571.276000] PCI: PCI BIOS revision 2.10 entry at 0xf1170, last bus=1
[17179571.276000] PCI: Using configuration type 1
[17179571.276000] Setting up standard PCI resources
[17179571.284000] ACPI: Interpreter enabled
[17179571.284000] ACPI: Using PIC for interrupt routing
[17179571.284000] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
[17179571.284000] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[17179571.284000] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[17179571.284000] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[17179571.284000] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 *9 10 11 12 14 15)
[17179571.288000] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[17179571.288000] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[17179571.288000] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[17179571.288000] ACPI: PCI Interrupt Link [LNKI] (IRQs 3 4 5 6 7 *9 10 11 12 14 15)
[17179571.288000] ACPI: PCI Root Bridge [PCI0] (0000:00)
[17179571.288000] PCI: Probing PCI hardware (bus 00)
[17179571.288000] ACPI: Assume root bridge [\_SB_.PCI0] bus is 0
[17179571.292000] PCI: Ignoring BAR0-3 of IDE controller 0000:00:04.0
[17179571.292000] PCI quirk: region e400-e43f claimed by ali7101 ACPI
[17179571.292000] PCI quirk: region e800-e81f claimed by ali7101 SMB
[17179571.292000] Boot video device is 0000:01:00.0
[17179571.292000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[17179571.292000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCI1._PRT]
[17179571.296000] Linux Plug and Play Support v0.97 (c) Adam Belay
[17179571.296000] pnp: PnP ACPI init
[17179571.300000] pnp: PnP ACPI: found 15 devices
[17179571.300000] PnPBIOS: Disabled by ACPI PNP
[17179571.300000] PCI: Using ACPI for IRQ routing
[17179571.300000] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[17179571.308000] pnp: 00:02: ioport range 0xe400-0xe47f could not be reserved
[17179571.308000] pnp: 00:02: ioport range 0xe800-0xe81f has been reserved
[17179571.308000] pnp: 00:02: ioport range 0x40b-0x40b has been reserved
[17179571.308000] pnp: 00:02: ioport range 0x480-0x48f has been reserved
[17179571.308000] pnp: 00:02: ioport range 0x4d6-0x4d6 has been reserved
[17179571.308000] PCI: Bridge: 0000:00:01.0
[17179571.308000]   IO window: d000-dfff
[17179571.308000]   MEM window: be800000-bfefffff
[17179571.308000]   PREFETCH window: c0000000-efffffff
[17179571.308000] PCI: Setting latency timer of device 0000:00:01.0 to 64
[17179571.308000] NET: Registered protocol family 2
[17179571.348000] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[17179571.348000] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[17179571.348000] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[17179571.352000] TCP: Hash tables configured (established 131072 bind 65536)
[17179571.352000] TCP reno registered
[17179571.352000] Simple Boot Flag at 0x3a set to 0x1
[17179571.352000] audit: initializing netlink socket (disabled)
[17179571.352000] audit(1171188412.352:1): initialized
[17179571.352000] highmem bounce pool size: 64 pages
[17179571.352000] VFS: Disk quotas dquot_6.5.1
[17179571.352000] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[17179571.352000] Initializing Cryptographic API
[17179571.352000] io scheduler noop registered
[17179571.352000] io scheduler anticipatory registered
[17179571.352000] io scheduler deadline registered
[17179571.352000] io scheduler cfq registered (default)
[17179571.352000] Limiting direct PCI/PCI transfers.
[17179571.352000] Activating ISA DMA hang workarounds.
[17179571.352000] isapnp: Scanning for PnP cards...
[17179571.708000] isapnp: No Plug & Play device found
[17179571.732000] Real Time Clock Driver v1.12ac
[17179571.732000] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[17179571.732000] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[17179571.736000] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[17179571.736000] 00:0b: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[17179571.736000] 00:0c: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[17179571.736000] mice: PS/2 mouse device common for all mice
[17179571.736000] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[17179571.736000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[17179571.736000] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[17179571.736000] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[17179571.740000] serio: i8042 AUX port at 0x60,0x64 irq 12
[17179571.740000] serio: i8042 KBD port at 0x60,0x64 irq 1
[17179571.740000] EISA: Probing bus 0 at eisa.0
[17179571.740000] EISA: Detected 0 cards.
[17179571.740000] TCP bic registered
[17179571.740000] NET: Registered protocol family 1
[17179571.740000] NET: Registered protocol family 8
[17179571.740000] NET: Registered protocol family 20
[17179571.740000] Using IPI No-Shortcut mode
[17179571.740000] ACPI: (supports S0 S1 S4 S5)
[17179571.740000] Freeing unused kernel memory: 308k freed
[17179571.764000] input: AT Translated Set 2 keyboard as /class/input/input0
[17179573.080000] Capability LSM initialized
[17179573.124000] ACPI: Invalid PBLK length [5]
[17179573.900000] ALI15X3: IDE controller at PCI slot 0000:00:04.0
[17179573.900000] ACPI: Unable to derive IRQ for device 0000:00:04.0
[17179573.900000] ACPI: PCI Interrupt 0000:00:04.0[A]: no GSI
[17179573.900000] ALI15X3: chipset revision 196
[17179573.900000] ALI15X3: not 100% native mode: will probe irqs later
[17179573.900000]     ide0: BM-DMA at 0xb400-0xb407, BIOS settings: hda:DMA, hdb:DMA
[17179573.900000]     ide1: BM-DMA at 0xb408-0xb40f, BIOS settings: hdc:pio, hdd:pio
[17179573.900000] Probing IDE interface ide0...
[17179574.232000] hda: Maxtor 6Y080P0, ATA DISK drive
[17179574.680000] hdb: HL-DT-ST GCE-8160B, ATAPI CD/DVD-ROM drive
[17179574.736000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[17179574.752000] Probing IDE interface ide1...
[17179585.176000] hdc: no response (status = 0xa1), resetting drive
[17179590.384000] hdc: no response (status = 0xa1)
[17179600.856000] hdd: no response (status = 0xa1), resetting drive
[17179606.064000] hdd: no response (status = 0xa1)
[17179606.128000] hda: max request size: 128KiB
[17179606.140000] hda: 160086528 sectors (81964 MB) w/7936KiB Cache, CHS=16383/255/63, UDMA(100)
[17179606.140000] hda: cache flushes supported
[17179606.140000]  hda: hda1 hda2 hda3 hda4 < hda5 >
[17179606.172000] hdb: ATAPI 40X CD-ROM CD-R/RW drive, 2048kB Cache, DMA
[17179606.172000] Uniform CD-ROM driver Revision: 3.20
[17179606.488000] Probing IDE interface ide1...
[17179641.272000] ide1: Wait for ready failed before probe !
[17179641.320000] usbcore: registered new driver usbfs
[17179641.320000] usbcore: registered new driver hub
[17179641.324000] ohci_hcd: 2005 April 22 USB 1.1 'Open' Host Controller (OHCI) Driver (PCI)
[17179641.324000] ACPI: PCI Interrupt Link [LNKI] enabled at IRQ 9
[17179641.324000] PCI: setting IRQ 9 as level-triggered
[17179641.324000] ACPI: PCI Interrupt 0000:00:02.0[A] -> Link [LNKI] -> GSI 9 (level, low) -> IRQ 9
[17179641.324000] ohci_hcd 0000:00:02.0: OHCI Host Controller
[17179641.324000] ohci_hcd 0000:00:02.0: new USB bus registered, assigned bus number 1
[17179641.324000] ohci_hcd 0000:00:02.0: irq 9, io mem 0xbe000000
[17179641.380000] usb usb1: configuration #1 chosen from 1 choice
[17179641.380000] hub 1-0:1.0: USB hub found
[17179641.380000] hub 1-0:1.0: 4 ports detected
[17179641.484000] ACPI: PCI Interrupt Link [LNKE] enabled at IRQ 9
[17179641.484000] ACPI: PCI Interrupt 0000:00:06.0[A] -> Link [LNKE] -> GSI 9 (level, low) -> IRQ 9
[17179641.484000] ohci_hcd 0000:00:06.0: OHCI Host Controller
[17179641.484000] ohci_hcd 0000:00:06.0: new USB bus registered, assigned bus number 2
[17179641.484000] ohci_hcd 0000:00:06.0: irq 9, io mem 0xbd000000
[17179641.540000] usb usb2: configuration #1 chosen from 1 choice
[17179641.540000] hub 2-0:1.0: USB hub found
[17179641.540000] hub 2-0:1.0: 2 ports detected
[17179641.788000] usb 1-2: new full speed USB device using ohci_hcd and address 2
[17179641.996000] usb 1-2: configuration #1 chosen from 1 choice
[17179651.744000] hdc: no response (status = 0xa1), resetting drive
[17179656.952000] hdc: no response (status = 0xa1)
[17179667.424000] hdd: no response (status = 0xa1), resetting drive
[17179672.632000] hdd: no response (status = 0xa1)
[17179672.700000] Attempting manual resume
[17179672.724000] kjournald starting.  Commit interval 5 seconds
[17179672.724000] EXT3-fs: mounted filesystem with ordered data mode.
[17179684.072000] PCI: Enabling device 0000:00:0a.0 (0014 -> 0017)
[17179684.072000] ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 11
[17179684.072000] PCI: setting IRQ 11 as level-triggered
[17179684.072000] ACPI: PCI Interrupt 0000:00:0a.0[A] -> Link [LNKC] -> GSI 11 (level, low) -> IRQ 11
[17179684.072000] 3c59x: Donald Becker and others. www.scyld.com/network/vortex.html
[17179684.072000] 0000:00:0a.0: 3Com PCI 3c905C Tornado at f8836000.
[17179684.112000] input: PC Speaker as /class/input/input1
[17179684.124000] Linux agpgart interface v0.101 (c) Dave Jones
[17179684.128000] agpgart: Detected ALi M1647 chipset
[17179684.136000] agpgart: AGP aperture is 128M @ 0xf0000000
[17179684.160000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[17179684.172000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[17179684.200000] ali15x3_smbus 0000:00:11.0: ALI15X3_smb region uninitialized - upgrade BIOS or use force_addr=0xaddr
[17179684.200000] ali15x3_smbus 0000:00:11.0: ALI15X3 not detected, module not inserted.
[17179684.272000] Floppy drive(s): fd0 is 1.44M
[17179684.280000] acx: Loaded combined PCI/USB driver, firmware_ver=default
[17179684.280000] acx: compiled to use 32bit I/O access. I/O timing issues might occur, such as non-working firmware upload. Report them
[17179684.280000] PCI: Enabling device 0000:00:09.0 (0004 -> 0006)
[17179684.284000] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 11
[17179684.284000] ACPI: PCI Interrupt 0000:00:09.0[A] -> Link [LNKD] -> GSI 11 (level, low) -> IRQ 11
[17179684.284000] acx: found ACX111-based wireless network card at 0000:00:09.0, irq:11, phymem1:0xBC000000, phymem2:0xBB800000, mem1:0xf88fc000, mem1_size:8192, mem2:0xf89c0000, mem2_size:131072
[17179684.304000] FDC 0 is a post-1991 82077
[17179684.808000] parport: PnPBIOS parport detected.
[17179684.808000] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
[17179684.860000] ACPI: PCI Interrupt 0000:00:0a.0[A] -> Link [LNKC] -> GSI 11 (level, low) -> IRQ 11
[17179684.864000] eth0:  setting half-duplex.
[17179684.892000] Linux video capture interface: v1.00
[17179684.964000] input: PS2++ Logitech Wheel Mouse as /class/input/input2
[17179685.052000] quickcam: QuickCam USB camera found (driver version QuickCam USB 0.6.3 $Date: 2005/04/15 19:32:49 $)
[17179685.052000] quickcam: Kernel:2.6.17-11-generic bus:1 class:FF subclass:FF vendor:046D product:0870
[17179685.156000] quickcam: Sensor HDCS-1020 detected
[17179685.164000] quickcam: Registered device: /dev/video0
[17179685.164000] usbcore: registered new driver quickcam
[17179685.324000] ts: Compaq touchscreen protocol output
[17179685.460000] acx: form factor 0x01 ((mini-)PCI / CardBus), radio type 0x16 (Radia), EEPROM version 0x05, uploaded firmware 'Rev 1.2.1.34' (0x03010101)
[17179685.460000] acx v0.3.21: net device wlan0, driver compiled against wireless extensions 20 and Linux 2.6.17-11-generic
[17179685.460000] usbcore: registered new driver acx_usb
[17179685.460000] PCI: Enabling device 0000:00:05.0 (0084 -> 0085)
[17179685.460000] ACPI: PCI Interrupt Link [LNKF] enabled at IRQ 11
[17179685.460000] ACPI: PCI Interrupt 0000:00:05.0[A] -> Link [LNKF] -> GSI 11 (level, low) -> IRQ 11
[17179685.692000] wlan0 (WE) : Driver using old /proc/net/wireless support, please fix driver !
[17179685.900000] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
[17179685.904000] [fglrx] Maximum main memory to use for locked dma buffers: 929 MBytes.
[17179685.904000] [fglrx] module loaded - fglrx 8.33.6 [Jan  8 2007] on minor 0
[17179685.952000] lp0: using parport0 (interrupt-driven).
[17179686.048000] Adding 586332k swap on /dev/disk/by-uuid/3af482da-20bb-4775-8ef2-21bdb74babe5.  Priority:-1 extents:1 across:586332k
[17179686.076000] NET: Registered protocol family 17
[17179686.116000] EXT3 FS on hda3, internal journal
[17179686.388000] NTFS driver 2.1.27 [Flags: R/O MODULE].
[17179686.464000] NTFS volume version 3.1.
[17179691.800000] ACPI: Power Button (FF) [PWRF]
[17179691.800000] ACPI: Power Button (CM) [PWRB]
[17179691.952000] ibm_acpi: ec object not found
[17179691.992000] pcc_acpi: loading...
[17179696.152000] ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 11
[17179696.152000] ACPI: PCI Interrupt 0000:01:00.0[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
[17179698.388000] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[17179698.388000] apm: overridden by ACPI.
[17179698.976000] [fglrx] Internal AGP support requested, but kernel AGP support active.
[17179698.976000] [fglrx] Have to use kernel AGP support to avoid conflicts.
[17179698.976000] [fglrx] AGP detected, AgpState   = 0x1b000217 (hardware caps of chipset)
[17179698.980000] agpgart: Found an AGP 2.0 compliant device at 0000:00:00.0.
[17179698.980000] agpgart: Putting AGP V2 device at 0000:00:00.0 into 4x mode
[17179698.980000] agpgart: Putting AGP V2 device at 0000:01:00.0 into 4x mode
[17179698.980000] [fglrx] AGP enabled,  AgpCommand = 0x1b000314 (selected caps)
[17179698.992000] [fglrx] total      GART = 134217728
[17179698.992000] [fglrx] free       GART = 118222848
[17179698.992000] [fglrx] max single GART = 118222848
[17179698.992000] [fglrx] total      LFB  = 134217728
[17179698.992000] [fglrx] free       LFB  = 116002816
[17179698.992000] [fglrx] max single LFB  = 116002816
[17179698.992000] [fglrx] total      Inv  = 0
[17179698.992000] [fglrx] free       Inv  = 0
[17179698.992000] [fglrx] max single Inv  = 0
[17179698.992000] [fglrx] total      TIM  = 0
[17179704.036000] Bluetooth: Core ver 2.8
[17179704.036000] NET: Registered protocol family 31
[17179704.036000] Bluetooth: HCI device and connection manager initialized
[17179704.036000] Bluetooth: HCI socket layer initialized
[17179704.072000] Bluetooth: L2CAP ver 2.8
[17179704.072000] Bluetooth: L2CAP socket layer initialized
[17179704.076000] Bluetooth: RFCOMM socket layer initialized
[17179704.076000] Bluetooth: RFCOMM TTY layer initialized
[17179704.076000] Bluetooth: RFCOMM ver 1.7
[17179714.536000] NET: Registered protocol family 10
[17179714.536000] lo: Disabled Privacy Extensions
[17179714.536000] ADDRCONF(NETDEV_UP): eth0: link is not ready
[17179714.536000] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[17179714.536000] IPv6 over IPv4 tunneling driver

```

---

