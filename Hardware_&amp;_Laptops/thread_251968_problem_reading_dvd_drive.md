---
title: "problem reading dvd drive"
date: 2006-09-06
forum: Hardware &amp; Laptops
---

### Post by shivling on 2006-09-06
Dear all,

Just installed linux - Ubuntu Dapper Drake the first time. It cannot detect my Samsung DVD Drive though when I insert a CD it plays normally. 

SK

---

### Post by zxee on 2006-09-06
Are you saying that an audio cd inserted in this drive plays?
If that's so then the drive _is_ being detected. 
Are you having problems playing movies? If that is the problem then you need to install software to get that capability. 
You may want to check out automatix or the video forum.

---

### Post by Valencik on 2006-09-06
I have pretty much the same problem (with a samsung DVD writer too). However, mine won't play any CD, does not even detect the CD being there. So now what? If it doesn't detect any CD/DVD I can't mount it. :(

---

### Post by zxee on 2006-09-07
> **Valencik said:**
> I have pretty much the same problem (with a samsung DVD writer too). However, mine won't play any CD, does not even detect the CD being there. So now what? If it doesn't detect any CD/DVD I can't mount it. :(

Does the drive spin up when you put a cd in it? If it's not a mechanical or some other problem with the drive itself check if the drive is appearing in the output of dmesg (typed in a terminal) How is the drive connected to your computer and are the master/slave settings correct?

---

### Post by Valencik on 2006-09-11
> **zxee said:**
> Does the drive spin up when you put a cd in it? If it's not a mechanical or some other problem with the drive itself check if the drive is appearing in the output of dmesg (typed in a terminal) How is the drive connected to your computer and are the master/slave settings correct?

I put a DVD in and about 3 seconds later the drive makes a little beep, but other than that nothing strange. When I open it the disc is in a different position so it must spin.
I've installed drives before (not with linux) so I am quite sure I have the master slave settings correct.

If i go into Places > Computer, I can see both my CD and DVD drive. However, if I put a DVD in the DVD drive nothing happens. If I try and manually mount the drive I get this:
"mount: no medium found"

Here is my output dmesg, i'm not sure what to look for.
> andrew@Andrew-ubuntu:~$ dmesg
[17179569.184000] Linux version 2.6.15-26-386 (buildd@terranova) (gcc version 4.0.3 (Ubuntu 4.0.3-1ubuntu5)) #1 PREEMPT Thu Aug 3 02:52:00 UTC 2006
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
[17179569.184000]   DMA32 zone: 0 pages, LIFO batch:0
[17179569.184000]   Normal zone: 61424 pages, LIFO batch:15
[17179569.184000]   HighMem zone: 0 pages, LIFO batch:0
[17179569.184000] DMI 2.3 present.
[17179569.184000] ACPI: RSDP (v000 AMI                                   ) @ 0x000fa760
[17179569.184000] ACPI: RSDT (v001 AMIINT VIA_K7   0x00000010 MSFT 0x00000097) @ 0x0fff0000
[17179569.184000] ACPI: FADT (v001 AMIINT VIA_K7   0x00000011 MSFT 0x00000097) @ 0x0fff0030
[17179569.184000] ACPI: DSDT (v001    VIA   VIA_K7 0x00001000 MSFT 0x0100000d) @ 0x00000000
[17179569.184000] ACPI: PM-Timer IO Port: 0x808
[17179569.184000] Allocating PCI resources starting at 20000000 (gap: 10000000:eec00000)
[17179569.184000] Built 1 zonelists
[17179569.184000] Kernel command line: root=/dev/hda2 ro quiet splash
[17179569.184000] Local APIC disabled by BIOS (or by default) -- you can enable it with "lapic"
[17179569.184000] mapped APIC to ffffd000 (01201000)
[17179569.184000] Initializing CPU#0
[17179569.184000] PID hash table entries: 1024 (order: 10, 16384 bytes)
[17179569.184000] Detected 1533.643 MHz processor.
[17179569.184000] Using pmtmr for high-res timesource
[17179569.184000] Console: colour VGA+ 80x25
[17179572.048000] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
[17179572.048000] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)[17179572.056000] Memory: 249140k/262080k available (1976k kernel code, 12356k reserved, 606k data, 288k init, 0k highmem)
[17179572.056000] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[17179572.136000] Calibrating delay using timer specific routine.. 3070.75 BogoMIPS (lpj=6141519)
[17179572.136000] Security Framework v1.0.0 initialized
[17179572.136000] SELinux:  Disabled at boot.
[17179572.136000] Mount-cache hash table entries: 512
[17179572.136000] CPU: After generic identify, caps: 0383f9ff c1c3f9ff 00000000 00000000 00000000 00000000 00000000
[17179572.136000] CPU: After vendor identify, caps: 0383f9ff c1c3f9ff 00000000 00000000 00000000 00000000 00000000
[17179572.136000] CPU: CLK_CTL MSR was 6003d22f. Reprogramming to 2003d22f
[17179572.136000] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[17179572.136000] CPU: L2 Cache: 256K (64 bytes/line)
[17179572.136000] CPU: After all inits, caps: 0383f9ff c1c3f9ff 00000000 00000420 00000000 00000000 00000000
[17179572.136000] mtrr: v2.0 (20020519)
[17179572.136000] CPU: AMD Athlon(tm) XP 1800+ stepping 01
[17179572.136000] Enabling fast FPU save and restore... done.
[17179572.136000] Enabling unmasked SIMD FPU exception support... done.
[17179572.136000] Checking 'hlt' instruction... OK.
[17179572.152000] checking if image is initramfs... it is
[17179572.836000] Freeing initrd memory: 6617k freed
[17179572.856000] ACPI: Looking for DSDT ... not found!
[17179572.856000] ACPI: setting ELCR to 0200 (from 1820)
[17179572.856000] NET: Registered protocol family 16
[17179572.856000] EISA bus registered
[17179572.856000] ACPI: bus type pci registered
[17179572.860000] PCI: PCI BIOS revision 2.10 entry at 0xfdaf1, last bus=1
[17179572.860000] PCI: Using configuration type 1
[17179572.860000] ACPI: Subsystem revision 20051216
[17179572.868000] ACPI: Interpreter enabled
[17179572.868000] ACPI: Using PIC for interrupt routing
[17179572.868000] ACPI: PCI Root Bridge [PCI0] (0000:00)
[17179572.868000] PCI: Probing PCI hardware (bus 00)
[17179572.872000] PCI quirk: region 0800-087f claimed by vt8235 PM
[17179572.872000] PCI quirk: region 0400-040f claimed by vt8235 SMB
[17179572.872000] Boot video device is 0000:01:00.0
[17179572.872000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[17179572.876000] ACPI: Power Resource [URP1] (off)
[17179572.876000] ACPI: Power Resource [URP2] (off)
[17179572.876000] ACPI: Power Resource [FDDP] (off)
[17179572.876000] ACPI: Power Resource [LPTP] (off)
[17179572.876000] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 *5 6 7 10 11 12 14 15)
[17179572.880000] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 *5 6 7 10 11 12 14 15)
[17179572.880000] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 10 11 *12 14 15)
[17179572.880000] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 10 *11 12 14 15)
[17179572.880000] Linux Plug and Play Support v0.97 (c) Adam Belay
[17179572.880000] pnp: PnP ACPI init
[17179572.884000] pnp: PnP ACPI: found 10 devices
[17179572.884000] PnPBIOS: Disabled by ACPI PNP
[17179572.884000] PCI: Using ACPI for IRQ routing
[17179572.884000] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[17179572.884000] PCI: Bridge: 0000:00:01.0
[17179572.884000]   IO window: c000-cfff
[17179572.884000]   MEM window: dfe00000-dfefffff
[17179572.884000]   PREFETCH window: cfd00000-dfcfffff
[17179572.884000] PCI: Setting latency timer of device 0000:00:01.0 to 64
[17179572.884000] audit: initializing netlink socket (disabled)
[17179572.884000] audit(1158001789.884:1): initialized
[17179572.884000] VFS: Disk quotas dquot_6.5.1
[17179572.884000] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[17179572.888000] Initializing Cryptographic API
[17179572.888000] io scheduler noop registered
[17179572.888000] io scheduler anticipatory registered
[17179572.888000] io scheduler deadline registered
[17179572.888000] io scheduler cfq registered
[17179572.888000] isapnp: Scanning for PnP cards...
[17179573.240000] isapnp: No Plug & Play device found
[17179573.256000] PNP: PS/2 Controller [PNP0303:PS2K] at 0x60,0x64 irq 1
[17179573.256000] PNP: PS/2 controller doesn't have AUX irq; using default 12
[17179573.256000] serio: i8042 AUX port at 0x60,0x64 irq 12
[17179573.256000] serio: i8042 KBD port at 0x60,0x64 irq 1
[17179573.256000] Serial: 8250/16550 driver $Revision: 1.90 $ 48 ports, IRQ sharing enabled
[17179573.256000] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[17179573.260000] 00:06: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[17179573.260000] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[17179573.260000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[17179573.260000] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[17179573.260000] mice: PS/2 mouse device common for all mice
[17179573.260000] EISA: Probing bus 0 at eisa.0
[17179573.260000] EISA: Detected 0 cards.
[17179573.260000] NET: Registered protocol family 2
[17179573.300000] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
[17179573.300000] TCP established hash table entries: 16384 (order: 4, 65536 bytes)
[17179573.300000] TCP bind hash table entries: 16384 (order: 4, 65536 bytes)
[17179573.300000] TCP: Hash tables configured (established 16384 bind 16384)
[17179573.300000] TCP reno registered
[17179573.300000] TCP bic registered
[17179573.300000] NET: Registered protocol family 1
[17179573.300000] NET: Registered protocol family 8
[17179573.300000] NET: Registered protocol family 20
[17179573.300000] Using IPI Shortcut mode
[17179573.300000] ACPI wakeup devices:
[17179573.300000] PCI0 USB1 USB2 USB3 EHCI UAR1  AC9  MC9 ILAN SLT1 SLT2 SLPB
[17179573.300000] ACPI: (supports S0 S1 S4 S5)
[17179573.300000] Freeing unused kernel memory: 288k freed
[17179573.356000] vga16fb: initializing
[17179573.356000] vga16fb: mapped to 0xc00a0000
[17179573.376000] input: AT Translated Set 2 keyboard as /class/input/input0
[17179573.472000] Console: switching to colour frame buffer device 80x25
[17179573.472000] fb0: VGA16 VGA frame buffer device
[17179574.496000] Capability LSM initialized
[17179574.612000] ACPI: Processor [CPU1] (supports 16 throttling states)
[17179575.288000] VP_IDE: IDE controller at PCI slot 0000:00:11.1
[17179575.288000] ACPI: PCI Interrupt 0000:00:11.1[A]: no GSI
[17179575.288000] PCI: VIA IRQ fixup for 0000:00:11.1, from 255 to 15
[17179575.288000] VP_IDE: chipset revision 6
[17179575.288000] VP_IDE: not 100% native mode: will probe irqs later
[17179575.288000] VP_IDE: VIA vt8235 (rev 00) IDE UDMA133 controller on pci0000:00:11.1
[17179575.288000]     ide0: BM-DMA at 0xfc00-0xfc07, BIOS settings: hda:DMA, hdb:DMA
[17179575.288000]     ide1: BM-DMA at 0xfc08-0xfc0f, BIOS settings: hdc:DMA, hdd:DMA
[17179575.288000] Probing IDE interface ide0...
[17179575.704000] hda: WDC WD800BB-75CAA0, ATA DISK drive
[17179575.984000] hdb: QUANTUM FIREBALL EX10.2A, ATA DISK drive
[17179576.040000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[17179576.064000] Probing IDE interface ide1...
[17179576.932000] hdc: TSSTcorpCD/DVDW SH-S162A, ATAPI CD/DVD-ROM drive
[17179577.716000] hdd: ATAPI CD-RW 52XMax, ATAPI CD/DVD-ROM drive
[17179577.772000] ide1 at 0x170-0x177,0x376 on irq 15
[17179577.780000] hda: max request size: 128KiB
[17179577.804000] hda: Host Protected Area detected.
[17179577.804000]       current capacity is 156250000 sectors (80000 MB)
[17179577.804000]       native  capacity is 156301488 sectors (80026 MB)
[17179577.804000] hda: Host Protected Area disabled.
[17179577.804000] hda: 156301488 sectors (80026 MB) w/2048KiB Cache, CHS=65535/16/63, UDMA(100)
[17179577.804000] hda: cache flushes not supported
[17179577.804000]  hda: hda1 hda2 hda3 < hda5 >
[17179577.856000] hdb: max request size: 128KiB
[17179577.856000] hdb: 20044080 sectors (10262 MB) w/418KiB Cache, CHS=19885/16/63, UDMA(33)
[17179577.856000] hdb: cache flushes not supported
[17179577.856000]  hdb:
[17179577.860000] hdc: ATAPI 48X DVD-ROM DVD-R-RAM CD-R/RW drive, 2048kB Cache, UDMA(33)
[17179577.860000] Uniform CD-ROM driver Revision: 3.20
[17179577.864000] hdd: ATAPI 52X CD-ROM CD-R/RW drive, 2048kB Cache, UDMA(33)
[17179578.264000] usbcore: registered new driver usbfs
[17179578.264000] usbcore: registered new driver hub
[17179578.268000] USB Universal Host Controller Interface driver v2.3
[17179578.268000] **** SET: Misaligned resource pointer: cfb2ce02 Type 07 Len 0
[17179578.268000] ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 5
[17179578.268000] PCI: setting IRQ 5 as level-triggered
[17179578.268000] ACPI: PCI Interrupt 0000:00:10.0[A] -> Link [LNKA] -> GSI 5 (level, low) -> IRQ 5
[17179578.268000] uhci_hcd 0000:00:10.0: UHCI Host Controller
[17179578.268000] uhci_hcd 0000:00:10.0: new USB bus registered, assigned bus number 1
[17179578.268000] uhci_hcd 0000:00:10.0: irq 5, io base 0x0000e400
[17179578.268000] hub 1-0:1.0: USB hub found
[17179578.268000] hub 1-0:1.0: 2 ports detected
[17179578.372000] **** SET: Misaligned resource pointer: cfb2cb02 Type 07 Len 0
[17179578.372000] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 5
[17179578.372000] ACPI: PCI Interrupt 0000:00:10.1[B] -> Link [LNKB] -> GSI 5 (level, low) -> IRQ 5
[17179578.372000] uhci_hcd 0000:00:10.1: UHCI Host Controller
[17179578.372000] uhci_hcd 0000:00:10.1: new USB bus registered, assigned bus number 2
[17179578.372000] uhci_hcd 0000:00:10.1: irq 5, io base 0x0000e800
[17179578.372000] hub 2-0:1.0: USB hub found
[17179578.372000] hub 2-0:1.0: 2 ports detected
[17179578.476000] **** SET: Misaligned resource pointer: cfb2c802 Type 07 Len 0
[17179578.476000] ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 12
[17179578.476000] PCI: setting IRQ 12 as level-triggered
[17179578.476000] ACPI: PCI Interrupt 0000:00:10.2[C] -> Link [LNKC] -> GSI 12 (level, low) -> IRQ 12
[17179578.476000] uhci_hcd 0000:00:10.2: UHCI Host Controller
[17179578.476000] uhci_hcd 0000:00:10.2: new USB bus registered, assigned bus number 3
[17179578.476000] uhci_hcd 0000:00:10.2: irq 12, io base 0x0000ec00
[17179578.476000] hub 3-0:1.0: USB hub found
[17179578.476000] hub 3-0:1.0: 2 ports detected
[17179578.580000] **** SET: Misaligned resource pointer: cfb2c502 Type 07 Len 0
[17179578.580000] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 11
[17179578.580000] PCI: setting IRQ 11 as level-triggered
[17179578.580000] ACPI: PCI Interrupt 0000:00:10.3[D] -> Link [LNKD] -> GSI 11 (level, low) -> IRQ 11
[17179578.580000] ehci_hcd 0000:00:10.3: EHCI Host Controller
[17179578.580000] ehci_hcd 0000:00:10.3: new USB bus registered, assigned bus number 4
[17179578.580000] ehci_hcd 0000:00:10.3: irq 11, io mem 0xdfffff00
[17179578.580000] ehci_hcd 0000:00:10.3: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[17179578.580000] hub 4-0:1.0: USB hub found
[17179578.580000] hub 4-0:1.0: 6 ports detected
[17179578.612000] usb 1-1: new low speed USB device using uhci_hcd and address 2[17179578.780000] Attempting manual resume
[17179578.808000] EXT3-fs: mounted filesystem with ordered data mode.
[17179578.820000] kjournald starting.  Commit interval 5 seconds
[17179579.872000] usb 1-1: new low speed USB device using uhci_hcd and address 3[17179591.124000] Linux agpgart interface v0.101 (c) Dave Jones
[17179591.132000] agpgart: Detected VIA PM266/KM266 chipset
[17179591.136000] agpgart: AGP aperture is 64M @ 0xe0000000
[17179591.152000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[17179591.240000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[17179591.564000] via-rhine.c:v1.10-LK1.2.0-2.6 June-10-2004 Written by Donald Becker
[17179591.564000] ACPI: PCI Interrupt 0000:00:12.0[A] -> Link [LNKA] -> GSI 5 (level, low) -> IRQ 5
[17179591.568000] eth0: VIA Rhine II at 0x1dc00, 00:0a:e6:60:e1:9b, IRQ 5.
[17179591.568000] eth0: MII PHY found at address 1, status 0x786d advertising 05e1 Link 45e1.
[17179591.728000] Real Time Clock Driver v1.12
[17179591.752000] usbcore: registered new driver hiddev
[17179591.764000] input: PC Speaker as /class/input/input1
[17179591.772000] input: Microsoft Microsoft 3-Button Mouse with IntelliEye(TM) as /class/input/input2
[17179591.772000] input: USB HID v1.10 Mouse [Microsoft Microsoft 3-Button Mouse with IntelliEye(TM)] on usb-0000:00:10.0-1
[17179591.772000] usbcore: registered new driver usbhid
[17179591.772000] drivers/usb/input/hid-core.c: v2.6:USB HID core driver
[17179591.780000] irda_init()
[17179591.780000] NET: Registered protocol family 23
[17179592.352000] ts: Compaq touchscreen protocol output
[17179592.364000] Floppy drive(s): fd0 is 1.44M
[17179592.384000] FDC 0 is a post-1991 82077
[17179592.384000] parport: PnPBIOS parport detected.
[17179592.384000] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
[17179592.460000] parport0: Printer, HEWLETT-PACKARD DESKJET 960C
[17179592.460000] ACPI: PCI Interrupt 0000:00:11.5[C] -> Link [LNKC] -> GSI 12 (level, low) -> IRQ 12
[17179592.460000] PCI: Setting latency timer of device 0000:00:11.5 to 64
[17179593.436000] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[17179594.244000] Intel ISA PCIC probe: not found.
[17179594.456000] lp0: using parport0 (interrupt-driven).
[17179594.468000] NET: Registered protocol family 17
[17179594.568000] Adding 746980k swap on /dev/hda5.  Priority:-1 extents:1 across:746980k
[17179594.696000] EXT3 FS on hda2, internal journal
[17179594.856000] device-mapper: 4.4.0-ioctl (2005-01-12) initialised: [email]dm-devel@redhat.com[/email]
[17179595.036000] md: md driver 0.90.3 MAX_MD_DEVS=256, MD_SB_DISKS=27
[17179595.036000] md: bitmap version 4.39
[17179595.808000] cdrom: open failed.
[17179596.240000] cdrom: open failed.
[17179596.244000] cdrom: open failed.
[17179598.068000] NET: Registered protocol family 10
[17179598.068000] lo: Disabled Privacy Extensions
[17179598.068000] IPv6 over IPv4 tunneling driver
[17179598.396000] ACPI: Power Button (FF) [PWRF]
[17179598.396000] ACPI: Power Button (CM) [PWRB]
[17179598.396000] ACPI: Sleep Button (CM) [SLPB]
[17179598.536000] ibm_acpi: ec object not found
[17179598.580000] pcc_acpi: loading...
[17179604.888000] ppdev: user-space parallel port driver
[17179605.504000] [drm] Initialized drm 1.0.1 20051102
[17179605.532000] [drm] Initialized radeon 1.24.0 20060225 on minor 0
[17179606.684000] agpgart: Found an AGP 2.0 compliant device at 0000:00:00.0.
[17179606.684000] agpgart: Putting AGP V2 device at 0000:00:00.0 into 1x mode
[17179606.684000] agpgart: Putting AGP V2 device at 0000:01:00.0 into 1x mode
[17179606.892000] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[17179606.892000] apm: overridden by ACPI.
[17179607.416000] [drm] Setting GART location based on new memory map
[17179607.416000] [drm] writeback test succeeded in 1 usecs
[17179608.408000] eth0: no IPv6 routers present
[17179610.956000] Bluetooth: Core ver 2.8
[17179610.956000] NET: Registered protocol family 31
[17179610.956000] Bluetooth: HCI device and connection manager initialized
[17179610.956000] Bluetooth: HCI socket layer initialized
[17179610.988000] Bluetooth: L2CAP ver 2.8
[17179610.988000] Bluetooth: L2CAP socket layer initialized
[17179611.016000] Bluetooth: RFCOMM socket layer initialized
[17179611.016000] Bluetooth: RFCOMM TTY layer initialized
[17179611.016000] Bluetooth: RFCOMM ver 1.7


---

### Post by Valencik on 2006-09-12
What should i be looking for? I still can't figure it out.

---

### Post by SamChameleon on 2006-10-01
Hello,

I faced the same problem since my new installation of dapper drake. I have two cdrom attached. One DVD-ROM (/dev/hdc) and one CDRW (/dev/hdd). I found out that only the CDRW is referred to in /dev. Perhaps you have the same problem.

Perhaps this helps:
Look up how cdrom is linked (ls -al cd* will show you where cdrom and cdrw are linked to). In my case, the DVD is first device on CD IDE-Cable and CDRW is second. Then it should look like this:

```
ls -al /dev/cd*
lrwxrwxrwx 1 root root 3 2006-10-01 10:45 /dev/cdrom -> hdc
lrwxrwxrwx 1 root root 3 2006-10-01 11:23 /dev/cdrw -> hdd

```

But after installation of dapper, it looked like this:
```
ls -al /dev/cd*
lrwxrwxrwx 1 root root 3 2006-10-01 10:45 /dev/cdrom -> hdd
lrwxrwxrwx 1 root root 3 2006-10-01 11:23 /dev/cdrw -> hdd

```

So you have to relink the cdrom.

---

### Post by PixelCloud on 2006-10-02
i just replaced a cdrom drive with a dvdrw drive

ls -al shows 

cdrom and cdrw linked to hdb

what should i do?

---

### Post by Ciego on 2006-10-03
How do you relink the CDROM?

---

### Post by Ciego on 2006-10-04
OK ... I figured out how to relink the CDROM but every time I reboot, it reverts to the orignal configuration.  Check out the thread that I started on the subject.

[http://www.ubuntuforums.org/showthread.php?p=1581875#post1581875](http://www.ubuntuforums.org/showthread.php?p=1581875#post1581875)

Any help is greatly appreciated.

---

