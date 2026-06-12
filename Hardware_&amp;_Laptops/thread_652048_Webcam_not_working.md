---
title: "Webcam not working"
date: 2007-12-28
forum: Hardware &amp; Laptops
---

### Post by kasio on 2007-12-28
Hi,

I have a Mikomi AP-7121 webcam that I hoped would be supported  in Ubuntu Gutsy, but haven't managed to get it working.

lsusb gives: 0c45:60fe Microdia

Any help on how to find and install drivers for this?

---

### Post by tinycamp on 2007-12-28
have you tried uvcvideo driver?

try [www.linuxtv.org](www.linuxtv.org)

---

### Post by justagamer on 2007-12-28
I had a issue with my webcam as well i was looking around for a program I found Camorama , but that didn't work so i used a program called Cheese and it works fine. So check into both of those. I belive the installs for both are in the package manager.

Hope that helpped

---

### Post by tinycamp on 2007-12-28
could you post the output of:

```
dmesg

```

when you connect the camera?

you can also try ekiga, it has a very good setup interface for webcams, try the v4l2 option

---

### Post by kasio on 2007-12-29
Here's the output from dmesg:

```
[    0.000000] Linux version 2.6.22-14-generic (buildd@terranova) (gcc version 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)) #1 SMP Tue Dec 18 08:02:57 UTC 2007 (Ubuntu 2.6.22-14.47-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000d0000 - 00000000000d4000 (reserved)
[    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000000fff0000 (usable)
[    0.000000]  BIOS-e820: 000000000fff0000 - 000000000fff8000 (ACPI data)
[    0.000000]  BIOS-e820: 000000000fff8000 - 0000000010000000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fff80000 - 0000000100000000 (reserved)
[    0.000000] 0MB HIGHMEM available.
[    0.000000] 255MB LOWMEM available.
[    0.000000] found SMP MP-table at 000fbe40
[    0.000000] Entering add_active_range(0, 0, 65520) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->    65520
[    0.000000]   HighMem     65520 ->    65520
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->    65520
[    0.000000] On node 0 totalpages: 65520
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 479 pages used for memmap
[    0.000000]   Normal zone: 60945 pages, LIFO batch:15
[    0.000000]   HighMem zone: 0 pages used for memmap
[    0.000000] DMI 2.3 present.
[    0.000000] ACPI: RSDP signature @ 0xC00FABB0 checksum 0
[    0.000000] ACPI: RSDP 000FABB0, 0014 (r0 AMI   )
[    0.000000] ACPI: RSDT 0FFF0000, 002C (r1 AMIINT VIA_K7         11 MSFT       97)
[    0.000000] ACPI: FACP 0FFF0030, 0074 (r1 AMIINT VIA_K7         11 MSFT       97)
[    0.000000] ACPI: DSDT 0FFF0110, 298C (r1    VIA   VIA_K7     1000 MSFT  100000D)
[    0.000000] ACPI: FACS 0FFF8000, 0040
[    0.000000] ACPI: APIC 0FFF00B0, 0054 (r1 AMIINT                 9 MSFT       97)
[    0.000000] ACPI: DMI BIOS year==0, assuming ACPI-capable machine
[    0.000000] ACPI: PM-Timer IO Port: 0x808
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] Processor #0 6:4 APIC version 16
[    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 1, version 17, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 low level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] Allocating PCI resources starting at 20000000 (gap: 10000000:eec00000)
[    0.000000] Built 1 zonelists.  Total pages: 65009
[    0.000000] Kernel command line: root=UUID=43fbdd43-f538-4ddd-bf8f-963afa5e61ff ro quiet #splash
[    0.000000] mapped APIC to ffffd000 (fee00000)
[    0.000000] mapped IOAPIC to ffffc000 (fec00000)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 1024 (order: 10, 4096 bytes)
[    0.000000] Detected 1302.984 MHz processor.
[   22.655454] Console: colour VGA+ 80x25
[   22.655923] Dentry cache hash table entries: 32768 (order: 5, 131072 bytes)
[   22.656159] Inode-cache hash table entries: 16384 (order: 4, 65536 bytes)
[   22.672164] Memory: 248460k/262080k available (2015k kernel code, 13156k reserved, 916k data, 364k init, 0k highmem)
[   22.672183] virtual kernel memory layout:
[   22.672184]     fixmap  : 0xfff4d000 - 0xfffff000   ( 712 kB)
[   22.672187]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   22.672189]     vmalloc : 0xd0800000 - 0xff7fe000   ( 751 MB)
[   22.672191]     lowmem  : 0xc0000000 - 0xcfff0000   ( 255 MB)
[   22.672193]       .init : 0xc03e3000 - 0xc043e000   ( 364 kB)
[   22.672195]       .data : 0xc02f7de6 - 0xc03dce84   ( 916 kB)
[   22.672197]       .text : 0xc0100000 - 0xc02f7de6   (2015 kB)
[   22.672204] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   22.672282] SLUB: Genslabs=22, HWalign=32, Order=0-1, MinObjects=4, CPUs=1, Nodes=1
[   22.752226] Calibrating delay using timer specific routine.. 2630.17 BogoMIPS (lpj=5260359)
[   22.752281] Security Framework v1.0.0 initialized
[   22.752294] SELinux:  Disabled at boot.
[   22.752328] Mount-cache hash table entries: 512
[   22.752572] CPU: After generic identify, caps: 0183fbff c1c7fbff 00000000 00000000 00000000 00000000 00000000
[   22.752588] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[   22.752592] CPU: L2 Cache: 256K (64 bytes/line)
[   22.752597] CPU: After all inits, caps: 0183fbff c1c7fbff 00000000 00000420 00000000 00000000 00000000
[   22.752616] Compat vDSO mapped to ffffe000.
[   22.752639] Checking 'hlt' instruction... OK.
[   22.768270] SMP alternatives: switching to UP code
[   22.768718] Freeing SMP alternatives: 11k freed
[   22.769370] Early unpacking initramfs... done
[   23.271188] ACPI: Core revision 20070126
[   23.271375] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[   23.273515] CPU0: AMD Athlon(tm) Processor stepping 04
[   23.273553] Total of 1 processors activated (2630.17 BogoMIPS).
[   23.274281] ENABLING IO-APIC IRQs
[   23.274629] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[   23.419607] Brought up 1 CPUs
[   23.419888] Booting paravirtualized kernel on bare hardware
[   23.420006] Time: 13:55:29  Date: 11/29/107
[   23.420066] NET: Registered protocol family 16
[   23.420256] EISA bus registered
[   23.420278] ACPI: bus type pci registered
[   23.452013] PCI: PCI BIOS revision 2.10 entry at 0xfdb51, last bus=1
[   23.452018] PCI: Using configuration type 1
[   23.452021] Setting up standard PCI resources
[   23.459144] ACPI: EC: Look up EC in DSDT
[   23.463190] ACPI: Interpreter enabled
[   23.463196] ACPI: (supports S0 S3 S4 S5)
[   23.463220] ACPI: Using IOAPIC for interrupt routing
[   23.467842] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   23.467861] PCI: Probing PCI hardware (bus 00)
[   23.467991] Disabling VIA memory write queue (PCI ID 0305, rev 81): [55] b8 & 3f -> 38
[   23.468243] PCI quirk: region 0c00-0c7f claimed by vt82c686 HW-mon
[   23.468248] PCI quirk: region 0400-040f claimed by vt82c686 SMB
[   23.468545] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   23.470139] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 10 *11 12 14 15)
[   23.470257] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[   23.470370] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 *10 11 12 14 15)
[   23.470481] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 *5 6 7 10 11 12 14 15)
[   23.470617] ACPI: Power Resource [URP1] (off)
[   23.470655] ACPI: Power Resource [URP2] (off)
[   23.470692] ACPI: Power Resource [FDDP] (off)
[   23.470727] ACPI: Power Resource [LPTP] (off)
[   23.470744] Linux Plug and Play Support v0.97 (c) Adam Belay
[   23.470765] pnp: PnP ACPI init
[   23.470778] ACPI: bus type pnp registered
[   23.473224] pnp: PnP ACPI: found 9 devices
[   23.473229] ACPI: ACPI bus type pnp unregistered
[   23.473237] PnPBIOS: Disabled by ACPI PNP
[   23.473343] PCI: Using ACPI for IRQ routing
[   23.473349] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   23.474989] NET: Registered protocol family 8
[   23.474993] NET: Registered protocol family 20
[   23.475463] Time: tsc clocksource has been installed.
[   23.505659] PCI: Bridge: 0000:00:01.0
[   23.505663]   IO window: disabled.
[   23.505671]   MEM window: dde00000-dfefffff
[   23.505676]   PREFETCH window: d5b00000-ddcfffff
[   23.505698] PCI: Setting latency timer of device 0000:00:01.0 to 64
[   23.505721] NET: Registered protocol family 2
[   23.543503] IP route cache hash table entries: 2048 (order: 1, 8192 bytes)
[   23.543606] TCP established hash table entries: 8192 (order: 4, 98304 bytes)
[   23.543930] TCP bind hash table entries: 8192 (order: 4, 65536 bytes)
[   23.544205] TCP: Hash tables configured (established 8192 bind 8192)
[   23.544210] TCP reno registered
[   23.555614] checking if image is initramfs... it is
[   24.006909] Switched to high resolution mode on CPU 0
[   24.498140] Freeing initrd memory: 7031k freed
[   24.498980] audit: initializing netlink socket (disabled)
[   24.499008] audit(1198936529.700:1): initialized
[   24.502450] VFS: Disk quotas dquot_6.5.1
[   24.502546] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   24.502749] io scheduler noop registered
[   24.502753] io scheduler anticipatory registered
[   24.502757] io scheduler deadline registered
[   24.502799] io scheduler cfq registered (default)
[   24.502831] Applying VIA southbridge workaround.
[   24.502837] PCI: VIA PCI bridge detected. Disabling DAC.
[   24.502842] PCI: Enabling Via external APIC routing
[   24.502883] Boot video device is 0000:01:00.0
[   24.503163] isapnp: Scanning for PnP cards...
[   24.860119] isapnp: No Plug & Play device found
[   24.907455] Real Time Clock Driver v1.12ac
[   24.907620] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   24.907775] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   24.909183] 00:07: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   24.910597] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   24.911039] input: Macintosh mouse button emulation as /class/input/input0
[   24.911165] PNP: PS/2 Controller [PNP0303:PS2K] at 0x60,0x64 irq 1
[   24.911170] PNP: PS/2 controller doesn't have AUX irq; using default 12
[   24.911617] serio: i8042 KBD port at 0x60,0x64 irq 1
[   24.911627] serio: i8042 AUX port at 0x60,0x64 irq 12
[   24.911907] mice: PS/2 mouse device common for all mice
[   24.912093] EISA: Probing bus 0 at eisa.0
[   24.912153] EISA: Detected 0 cards.
[   24.912526] TCP cubic registered
[   24.912543] NET: Registered protocol family 1
[   24.912578] Using IPI No-Shortcut mode
[   24.912857]   Magic number: 3:486:939
[   24.913053]   hash matches device ptyya
[   24.914219] Freeing unused kernel memory: 364k freed
[   24.953889] input: AT Translated Set 2 keyboard as /class/input/input1
[   25.236066] AppArmor: AppArmor initialized<5>audit(1198936530.200:2):  type=1505 info="AppArmor initialized" pid=1143
[   25.247465] fuse init (API version 7.8)
[   25.255744] Failure registering capabilities with primary security module.
[   25.275026] ACPI: Processor [CPU1] (supports 2 throttling states)
[   26.203525] SCSI subsystem initialized
[   26.211545] libata version 2.21 loaded.
[   26.220831] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[   26.220843] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[   26.222024] VP_IDE: IDE controller at PCI slot 0000:00:07.1
[   26.222066] VP_IDE: chipset revision 6
[   26.222070] VP_IDE: not 100% native mode: will probe irqs later
[   26.222086] VP_IDE: VIA vt82c686b (rev 40) IDE UDMA100 controller on pci0000:00:07.1
[   26.222098]     ide0: BM-DMA at 0xfc00-0xfc07, BIOS settings: hda:DMA, hdb:pio
[   26.222117]     ide1: BM-DMA at 0xfc08-0xfc0f, BIOS settings: hdc:DMA, hdd:DMA
[   26.222127] Probing IDE interface ide0...
[   26.270456] usbcore: registered new interface driver usbfs
[   26.270515] usbcore: registered new interface driver hub
[   26.270564] usbcore: registered new device driver usb
[   26.272274] USB Universal Host Controller Interface driver v3.0
[   26.376420] 8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)
[   26.486437] Floppy drive(s): fd0 is 1.44M
[   26.538840] FDC 0 is a post-1991 82077
[   26.671861] hda: Maxtor 6Y080L0, ATA DISK drive
[   27.343154] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[   27.349895] Probing IDE interface ide1...
[   28.214030] hdc: PIONEER DVD-ROM DVD-117, ATAPI CD/DVD-ROM drive
[   28.997101] hdd: R/RW 12x8x32, ATAPI CD/DVD-ROM drive
[   29.053816] ide1 at 0x170-0x177,0x376 on irq 15
[   29.057224] ACPI: PCI Interrupt 0000:00:07.2[D] -> GSI 5 (level, low) -> IRQ 5
[   29.057250] uhci_hcd 0000:00:07.2: UHCI Host Controller
[   29.057808] uhci_hcd 0000:00:07.2: new USB bus registered, assigned bus number 1
[   29.057855] uhci_hcd 0000:00:07.2: irq 5, io base 0x0000c800
[   29.058567] usb usb1: configuration #1 chosen from 1 choice
[   29.058787] hub 1-0:1.0: USB hub found
[   29.058801] hub 1-0:1.0: 2 ports detected
[   29.070798] hda: max request size: 128KiB
[   29.093825] hda: 160086528 sectors (81964 MB) w/2048KiB Cache, CHS=65535/16/63, UDMA(100)
[   29.094001] hda: cache flushes supported
[   29.094124]  hda: hda1 hda2 hda3 < hda5 >
[   29.137501] hdc: ATAPI 40X DVD-ROM drive, 256kB Cache, UDMA(33)
[   29.137518] Uniform CD-ROM driver Revision: 3.20
[   29.140917] hdd: ATAPI 32X CD-ROM CD-R/RW drive, 4096kB Cache, DMA
[   29.161026] ACPI: PCI Interrupt 0000:00:07.3[D] -> GSI 5 (level, low) -> IRQ 5
[   29.161053] uhci_hcd 0000:00:07.3: UHCI Host Controller
[   29.161098] uhci_hcd 0000:00:07.3: new USB bus registered, assigned bus number 2
[   29.161131] uhci_hcd 0000:00:07.3: irq 5, io base 0x0000cc00
[   29.161308] usb usb2: configuration #1 chosen from 1 choice
[   29.161351] hub 2-0:1.0: USB hub found
[   29.161366] hub 2-0:1.0: 2 ports detected
[   29.265097] 8139cp 0000:00:08.0: This (id 10ec:8139 rev 10) is not an 8139C+ compatible chip
[   29.265165] 8139cp 0000:00:08.0: Try the "8139too" driver instead.
[   29.269115] 8139too Fast Ethernet driver 0.9.28
[   29.269209] ACPI: PCI Interrupt 0000:00:08.0[A] -> GSI 16 (level, low) -> IRQ 16
[   29.269651] eth0: RealTek RTL8139 at 0xd0836f00, 00:08:54:44:f3:e2, IRQ 16
[   29.269655] eth0:  Identified 8139 chip type 'RTL-8100B/8139D'
[   29.528343] usb 1-2: new low speed USB device using uhci_hcd and address 2
[   29.554864] Attempting manual resume
[   29.554871] swsusp: Resume From Partition 3:5
[   29.554874] PM: Checking swsusp image.
[   29.567680] PM: Resume from disk failed.
[   29.623290] kjournald starting.  Commit interval 5 seconds
[   29.623315] EXT3-fs: mounted filesystem with ordered data mode.
[   29.704272] usb 1-2: configuration #1 chosen from 1 choice
[   37.909597] eth1: link up, 10Mbps, half-duplex, lpa 0x0000
[   38.872434] NET: Registered protocol family 10
[   38.872606] lo: Disabled Privacy Extensions
[   40.679248] Linux agpgart interface v0.102 (c) Dave Jones
[   40.739687] agpgart: Detected VIA Twister-K/KT133x/KM133 chipset
[   40.745875] agpgart: AGP aperture is 64M @ 0xe0000000
[   40.817356] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   40.820279] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   40.905055] parport_pc: VIA 686A/8231 detected
[   40.905063] parport_pc: probing current configuration
[   40.905083] parport_pc: Current parallel port base: 0x378
[   40.905173] parport0: PC-style at 0x378 (0x778), irq 7, using FIFO [PCSPP,TRISTATE,COMPAT,ECP]
[   40.994704] parport_pc: VIA parallel port: io=0x378, irq=7
[   41.735985] input: PC Speaker as /class/input/input2
[   42.156111] nvidia: module license 'NVIDIA' taints kernel.
[   42.577002] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 16
[   42.578148] NVRM: loading NVIDIA Linux x86 Kernel Module  1.0-9639  Mon Apr 16 20:20:06 PDT 2007
[   42.780316] usbcore: registered new interface driver hiddev
[   42.793284] input: Logitech Optical USB Mouse as /class/input/input3
[   42.793402] input: USB HID v1.10 Mouse [Logitech Optical USB Mouse] on usb-0000:00:07.2-2
[   42.793433] usbcore: registered new interface driver usbhid
[   42.793440] /build/buildd/linux-source-2.6.22-2.6.22/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
[   43.169879] ACPI: PCI Interrupt 0000:00:07.5[C] -> GSI 10 (level, low) -> IRQ 10
[   43.170044] PCI: Setting latency timer of device 0000:00:07.5 to 64
[   43.696032] ACPI: PCI Interrupt 0000:00:07.6[C] -> GSI 10 (level, low) -> IRQ 10
[   43.699484] PCI: Setting latency timer of device 0000:00:07.6 to 64
[   45.423363] lp0: using parport0 (interrupt-driven).
[   45.506590] Linux video capture interface: v2.00
[   45.607277] sn9c102: V4L2 driver for SN9C1xx PC Camera Controllers v1:1.48
[   45.610612] usbcore: registered new interface driver sn9c102
[   45.687158] Adding 1494004k swap on /dev/hda5.  Priority:-1 extents:1 across:1494004k
[   49.640354] eth1: no IPv6 routers present
[  146.169819] EXT3 FS on hda1, internal journal
[  152.480554] No dock devices found.
[  152.773182] input: Power Button (FF) as /class/input/input4
[  152.776909] ACPI: Power Button (FF) [PWRF]
[  152.822500] input: Power Button (CM) as /class/input/input5
[  152.822922] ACPI: Power Button (CM) [PWRB]
[  153.340303] powernow: No powernow capabilities detected
[  155.164094] ppdev: user-space parallel port driver
[  156.343047] audit(1198936662.233:3):  type=1503 operation="inode_permission" requested_mask="a" denied_mask="a" name="/dev/tty" pid=4743 profile="/usr/sbin/cupsd"
[  156.599097] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[  156.599106] apm: overridden by ACPI.
[  158.559007] Failure registering capabilities with primary security module.
[  159.091219] Bluetooth: Core ver 2.11
[  159.091352] NET: Registered protocol family 31
[  159.091356] Bluetooth: HCI device and connection manager initialized
[  159.091363] Bluetooth: HCI socket layer initialized
[  159.145916] Bluetooth: L2CAP ver 2.8
[  159.145924] Bluetooth: L2CAP socket layer initialized
[  159.235528] Bluetooth: RFCOMM socket layer initialized
[  159.235561] Bluetooth: RFCOMM TTY layer initialized
[  159.235565] Bluetooth: RFCOMM ver 1.8
[  162.099636] agpgart: Found an AGP 2.0 compliant device at 0000:00:00.0.
[  162.099666] agpgart: Putting AGP V2 device at 0000:00:00.0 into 4x mode
[  162.099710] agpgart: Putting AGP V2 device at 0000:01:00.0 into 4x mode
[ 2768.999577] usb 2-1: new full speed USB device using uhci_hcd and address 2
[ 2769.162522] usb 2-1: configuration #1 chosen from 1 choice
[ 2769.167319] usb 2-1: SN9C105 PC Camera Controller detected (vid:pid 0x0C45:0x60FE)
[ 2769.259212] usb 2-1: OV7630 image sensor detected
[ 2769.754549] usb 2-1: Initialization succeeded
[ 2769.754625] usb 2-1: V4L2 device registered as /dev/video0
[ 2769.754676] BUG: unable to handle kernel paging request at virtual address 05100070
[ 2769.754684]  printing eip:
[ 2769.754687] c02f313b
[ 2769.754689] *pde = 00000000
[ 2769.754695] Oops: 0002 [#1]
[ 2769.754697] SMP 
[ 2769.754703] Modules linked in: binfmt_misc rfcomm l2cap bluetooth ppdev cpufreq_powersave cpufreq_stats cpufreq_ondemand freq_table cpufreq_userspace cpufreq_conservative sbs button container dock video ac battery sn9c102 compat_ioctl32 videodev v4l1_compat v4l2_common lp snd_via82xx_modem snd_via82xx snd_seq_dummy gameport snd_ac97_codec ac97_bus snd_pcm_oss snd_mixer_oss snd_seq_oss usbhid snd_pcm hid snd_mpu401_uart nvidia(P) snd_seq_midi snd_seq_midi_event snd_seq snd_timer snd_rawmidi snd_seq_device pcspkr serio_raw psmouse snd snd_page_alloc i2c_viapro via686a i2c_isa soundcore i2c_core parport_pc parport shpchp pci_hotplug via_agp agpgart ipv6 evdev ext3 jbd mbcache 8139too ide_cd cdrom ide_disk floppy 8139cp mii uhci_hcd usbcore via82cxxx ide_core ata_generic libata scsi_mod thermal processor fan fuse apparmor commoncap
[ 2769.754788] CPU:    0
[ 2769.754790] EIP:    0060:[<c02f313b>]    Tainted: P       VLI
[ 2769.754792] EFLAGS: 00010246   (2.6.22-14-generic #1)
[ 2769.754809] EIP is at mutex_lock+0xb/0x20
[ 2769.754814] eax: 05100070   ebx: 05100070   ecx: 00000004   edx: cfb66000
[ 2769.754819] esi: c3b41e08   edi: ffffffef   ebp: 00000000   esp: cfb67cb4
[ 2769.754824] ds: 007b   es: 007b   fs: 00d8  gs: 0000  ss: 0068
[ 2769.754830] Process khubd (pid: 1946, ti=cfb66000 task=cfad2a60 task.ti=cfb66000)
[ 2769.754833] Stack: d0ce898c c01c3317 d0b7b3a9 c3b41e48 00000004 ca6e01a4 00000000 cbeae25c 
[ 2769.754843]        cbeac000 c3b41dd0 00000000 cbeae25c cbeac000 d0ccdfbc d0ce3bc8 d0865df9 
[ 2769.754852]        ca6e8d10 00000000 000060fe d0cd3bc8 d0859dc7 cef8f200 00000000 00000000 
[ 2769.754861] Call Trace:
[ 2769.754867]  [<c01c3317>] sysfs_add_file+0x37/0x90
[ 2769.754876]  [<d0b7b3a9>] video_register_device+0x139/0x280 [videodev]
[ 2769.754902]  [<d0ccdfbc>] sn9c102_usb_probe+0x11c/0x840 [sn9c102]
[ 2769.754942]  [<d0859dc7>] usb_match_one_id+0x27/0xb0 [usbcore]
[ 2769.755019]  [<d085af66>] usb_probe_interface+0x96/0xe0 [usbcore]
[ 2769.755043]  [<c026110e>] driver_probe_device+0x8e/0x190
[ 2769.755054]  [<c02f16f3>] klist_next+0x53/0xa0
[ 2769.755066]  [<c02603c4>] bus_for_each_drv+0x44/0x70
[ 2769.755089]  [<c02612d6>] device_attach+0x86/0x90
[ 2769.755095]  [<c0261210>] __device_attach+0x0/0x10
[ 2769.755102]  [<c026032d>] bus_attach_device+0x4d/0xa0
[ 2769.755108]  [<c0260779>] bus_add_device+0x129/0x160
[ 2769.755121]  [<c025efff>] device_add+0x49f/0x570
[ 2769.755144]  [<d0858f22>] usb_set_configuration+0x2a2/0x4f0 [usbcore]
[ 2769.755182]  [<d0860e1d>] generic_probe+0x16d/0x250 [usbcore]
[ 2769.755224]  [<d085ac33>] usb_probe_device+0x33/0x40 [usbcore]
[ 2769.755242]  [<c026110e>] driver_probe_device+0x8e/0x190
[ 2769.755249]  [<c02f16f3>] klist_next+0x53/0xa0
[ 2769.755261]  [<c02603c4>] bus_for_each_drv+0x44/0x70
[ 2769.755275]  [<c02612d6>] device_attach+0x86/0x90
[ 2769.755280]  [<c0261210>] __device_attach+0x0/0x10
[ 2769.755287]  [<c026032d>] bus_attach_device+0x4d/0xa0
[ 2769.755293]  [<c0260779>] bus_add_device+0x129/0x160
[ 2769.755305]  [<c025efff>] device_add+0x49f/0x570
[ 2769.755328]  [<d085428d>] usb_new_device+0x8d/0x110 [usbcore]
[ 2769.755355]  [<d0854f6e>] hub_thread+0x78e/0xc30 [usbcore]
[ 2769.755375]  [<c02f204a>] schedule+0x2ca/0x890
[ 2769.755400]  [<c013bdd0>] autoremove_wake_function+0x0/0x50
[ 2769.755422]  [<d08547e0>] hub_thread+0x0/0xc30 [usbcore]
[ 2769.755441]  [<c013bb12>] kthread+0x42/0x70
[ 2769.755447]  [<c013bad0>] kthread+0x0/0x70
[ 2769.755454]  [<c0105487>] kernel_thread_helper+0x7/0x10
[ 2769.755470]  =======================
[ 2769.755473] Code: 53 89 c3 e8 48 f5 ff ff b8 ff ff ff ff 90 0f c1 03 83 e8 01 78 04 5b 31 c0 c3 89 d8 5b eb 21 90 53 89 c3 e8 28 f5 ff ff 89 d8 90 <ff> 08 79 05 e8 0c 01 00 00 5b c3 8d 76 00 8d bc 27 00 00 00 00 
[ 2769.755508] EIP: [<c02f313b>] mutex_lock+0xb/0x20 SS:ESP 0068:cfb67cb4
[ 2790.971566] BUG: unable to handle kernel paging request at virtual address 00002261
[ 2790.971582]  printing eip:
[ 2790.971585] c02f400d
[ 2790.971587] *pde = 00000000
[ 2790.971593] Oops: 0002 [#2]
[ 2790.971595] SMP 
[ 2790.971600] Modules linked in: binfmt_misc rfcomm l2cap bluetooth ppdev cpufreq_powersave cpufreq_stats cpufreq_ondemand freq_table cpufreq_userspace cpufreq_conservative sbs button container dock video ac battery sn9c102 compat_ioctl32 videodev v4l1_compat v4l2_common lp snd_via82xx_modem snd_via82xx snd_seq_dummy gameport snd_ac97_codec ac97_bus snd_pcm_oss snd_mixer_oss snd_seq_oss usbhid snd_pcm hid snd_mpu401_uart nvidia(P) snd_seq_midi snd_seq_midi_event snd_seq snd_timer snd_rawmidi snd_seq_device pcspkr serio_raw psmouse snd snd_page_alloc i2c_viapro via686a i2c_isa soundcore i2c_core parport_pc parport shpchp pci_hotplug via_agp agpgart ipv6 evdev ext3 jbd mbcache 8139too ide_cd cdrom ide_disk floppy 8139cp mii uhci_hcd usbcore via82cxxx ide_core ata_generic libata scsi_mod thermal processor fan fuse apparmor commoncap
[ 2790.971685] CPU:    0
[ 2790.971687] EIP:    0060:[<c02f400d>]    Tainted: P       VLI
[ 2790.971690] EFLAGS: 00210046   (2.6.22-14-generic #1)
[ 2790.971709] EIP is at _spin_lock_irq+0xd/0x20
[ 2790.971713] eax: 00002261   ebx: 0000225d   ecx: 00000000   edx: 00002261
[ 2790.971719] esi: 00002261   edi: 00000001   ebp: cd86be64   esp: cd86be44
[ 2790.971724] ds: 007b   es: 007b   fs: 00d8  gs: 0033  ss: 0068
[ 2790.971730] Process camorama (pid: 5551, ti=cd86a000 task=c000ca60 task.ti=cd86a000)
[ 2790.971733] Stack: c02f2cb9 00000101 00000001 00000000 00000006 00000001 d0b7f260 fffffe00 
[ 2790.971743]        00000000 d0ccd302 c1bab000 c1bab008 c99f5000 d082d8ce 00000000 c656dc30 
[ 2790.971752]        00000006 cd86bf30 c81df960 cff3fa80 00000006 c80d57e0 c01fa1ff d0b81880 
[ 2790.971761] Call Trace:
[ 2790.971765]  [<c02f2cb9>] wait_for_completion_interruptible+0x19/0x110
[ 2790.971784]  [<d0ccd302>] sn9c102_open+0x42/0x6b0 [sn9c102]
[ 2790.971829]  [<c01fa1ff>] kobject_get+0xf/0x20
[ 2790.971841]  [<c0182f3e>] cdev_get+0x2e/0x50
[ 2790.971857]  [<d0b7ed68>] video_open+0x98/0x130 [videodev]
[ 2790.971871]  [<c0182ce0>] exact_match+0x0/0x10
[ 2790.971878]  [<d0b7ecd0>] video_open+0x0/0x130 [videodev]
[ 2790.971889]  [<c0183416>] chrdev_open+0xa6/0x190
[ 2790.971899]  [<c0183370>] chrdev_open+0x0/0x190
[ 2790.971905]  [<c017ebf8>] __dentry_open+0xb8/0x1c0
[ 2790.971925]  [<c017edb5>] nameidata_to_filp+0x35/0x40
[ 2790.971935]  [<c017ee10>] do_filp_open+0x50/0x60
[ 2790.971966]  [<c017ee6e>] do_sys_open+0x4e/0xf0
[ 2790.971979]  [<c017ef4c>] sys_open+0x1c/0x20
[ 2790.971986]  [<c01041d2>] sysenter_past_esp+0x6b/0xa9
[ 2790.972012]  =======================
[ 2790.972014] Code: 3a 00 7e f9 fa 8d 04 05 00 00 00 00 90 90 eb d6 f3 90 80 3a 00 7f cf eb f7 89 c8 c3 66 90 89 c2 fa 8d 04 05 00 00 00 00 90 90 90 <fe> 0a 79 09 f3 90 80 3a 00 7e f9 eb f2 c3 90 8d 74 26 00 53 89 
[ 2790.972050] EIP: [<c02f400d>] _spin_lock_irq+0xd/0x20 SS:ESP 0068:cd86be44
```

I'll try Ekiga.

---

### Post by tinycamp on 2007-12-29
it seems that the camera is being correctly detected and initialized, but the errors that follow the detection seem to be related to the camera....

those are out of my league, cant help you with those..... does the camera work fine with other computer??

---

### Post by kasio on 2007-12-29
Nope...doesn't work on another. I'll try windows.

---

### Post by tinycamp on 2007-12-29
but just try... don't stick!!!!! lol


have you checked [www.linuxtv.org?](www.linuxtv.org?)

---

### Post by kasio on 2007-12-30
Windows works fine, using the software provided. Any idea about the bug produced?

---

### Post by intel on 2008-01-07
For all those with microdia (0c45:xxxy) webcams, please visit this website

https://groups.google.com/group/microdia

and provide/add details about your specific webcam, join the group,
this will help in getting decent drivers.

0c45:608f, 0c45:60ec, 0c45:60fe, 0c45:6242, 0c45:6260, 0c45:6270, 0c45:60c0, 0c45:613b, 0c45:613c, 0c45:624f, 0c45:627b, 0c45:8105

---

