---
title: "Can't install from live cd ide hard drive missing"
date: 2009-01-23
forum: Installation &amp; Upgrades
---

### Post by wayne666 on 2009-01-23
I am trying to install ubuntu 8.4 from the live cd. Problem is my internal ide hard drive does not show up. I have tried a knoppix live cd and the drive is visible. Any help would be most appreciatted.

---

### Post by wayne666 on 2009-01-23
here is my dmesg

[    0.000000] Linux version 2.6.24-16-generic (buildd@palmer) (gcc version 4.2.3 (Ubuntu 4.2.3-2ubuntu7)) #1 SMP Thu Apr 10 13:23:42 UTC 2008 (Ubuntu 2.6.24-16.30-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 00000000bfff0000 (usable)
[    0.000000]  BIOS-e820: 00000000bfff0000 - 00000000bfff3000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000bfff3000 - 00000000c0000000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000ffff0000 - 0000000100000000 (reserved)
[    0.000000] 2175MB HIGHMEM available.
[    0.000000] 896MB LOWMEM available.
[    0.000000] Entering add_active_range(0, 0, 786416) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   229376
[    0.000000]   HighMem    229376 ->   786416
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   786416
[    0.000000] On node 0 totalpages: 786416
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 1760 pages used for memmap
[    0.000000]   Normal zone: 223520 pages, LIFO batch:31
[    0.000000]   HighMem zone: 4351 pages used for memmap
[    0.000000]   HighMem zone: 552689 pages, LIFO batch:31
[    0.000000]   Movable zone: 0 pages used for memmap
[    0.000000] DMI 2.2 present.
[    0.000000] ACPI: RSDP signature @ 0xC00F6E00 checksum 0
[    0.000000] ACPI: RSDP 000F6E00, 0014 (r0 VIA694)
[    0.000000] ACPI: RSDT BFFF3000, 0028 (r1 VIA694 AWRDACPI 42302E31 AWRD        0)
[    0.000000] ACPI: FACP BFFF3040, 0074 (r1 VIA694 AWRDACPI 42302E31 AWRD        0)
[    0.000000] ACPI: DSDT BFFF30C0, 2B6C (r1 VIA694 AWRDACPI     1000 MSFT  100000C)
[    0.000000] ACPI: FACS BFFF0000, 0040
[    0.000000] ACPI: PM-Timer IO Port: 0x4008
[    0.000000] Allocating PCI resources starting at c4000000 (gap: c0000000:3ec00000)
[    0.000000] swsusp: Registered nosave memory region: 000000000009f000 - 00000000000a0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000a0000 - 00000000000f0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000f0000 - 0000000000100000
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 780273
[    0.000000] Kernel command line: BOOT_IMAGE=/casper/vmlinuz file=/cdrom/preseed/ubuntu.seed boot=casper initrd=/casper/initrd.gz quiet splash --
[    0.000000] Found and enabled local APIC!
[    0.000000] mapped APIC to ffffb000 (fee00000)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] Detected 1400.700 MHz processor.
[   61.921162] Console: colour VGA+ 80x25
[   61.921168] console [tty0] enabled
[   61.922244] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[   61.924107] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[   62.184956] Memory: 3107444k/3145664k available (2157k kernel code, 37196k reserved, 998k data, 364k init, 2228160k highmem)
[   62.184969] virtual kernel memory layout:
[   62.184970]     fixmap  : 0xfff4b000 - 0xfffff000   ( 720 kB)
[   62.184972]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   62.184974]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
[   62.184976]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
[   62.184977]       .init : 0xc041b000 - 0xc0476000   ( 364 kB)
[   62.184979]       .data : 0xc031b5a4 - 0xc0414dc4   ( 998 kB)
[   62.184981]       .text : 0xc0100000 - 0xc031b5a4   (2157 kB)
[   62.184986] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   62.185062] SLUB: Genslabs=11, HWalign=32, Order=0-1, MinObjects=4, CPUs=1, Nodes=1
[   62.265085] Calibrating delay using timer specific routine.. 2803.98 BogoMIPS (lpj=5607970)
[   62.265146] Security Framework initialized
[   62.265162] SELinux:  Disabled at boot.
[   62.265199] AppArmor: AppArmor initialized
[   62.265207] Failure registering capabilities with primary security module.
[   62.265224] Mount-cache hash table entries: 512
[   62.265476] CPU: After generic identify, caps: 0383fbff c1c3fbff 00000000 00000000 00000000 00000000 00000000 00000000
[   62.265491] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[   62.265495] CPU: L2 Cache: 256K (64 bytes/line)
[   62.265500] CPU: After all inits, caps: 0383fbff c1c3fbff 00000000 00000420 00000000 00000000 00000000 00000000
[   62.265519] Compat vDSO mapped to ffffe000.
[   62.265544] Checking 'hlt' instruction... OK.
[   62.281460] SMP alternatives: switching to UP code
[   62.283065] Freeing SMP alternatives: 11k freed
[   62.283270] Early unpacking initramfs... done
[   62.780615] ACPI: Core revision 20070126
[   62.780746] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[   62.782433] ACPI: setting ELCR to 0200 (from 0e20)
[   62.784008] CPU0: AMD Athlon(tm) XP 1600+ stepping 02
[   62.784023] SMP motherboard not detected.
[   62.889113] Brought up 1 CPUs
[   62.889144] CPU0 attaching sched-domain:
[   62.889148]  domain 0: span 01
[   62.889150]   groups: 01
[   62.889471] net_namespace: 64 bytes
[   62.889480] Booting paravirtualized kernel on bare hardware
[   62.890173] Time: 16:24:29  Date: 01/23/09
[   62.890221] NET: Registered protocol family 16
[   62.890536] EISA bus registered
[   62.890569] ACPI: bus type pci registered
[   62.966696] PCI: PCI BIOS revision 2.10 entry at 0xfb4d0, last bus=1
[   62.966700] PCI: Using configuration type 1
[   62.966703] Setting up standard PCI resources
[   62.971033] ACPI: EC: Look up EC in DSDT
[   62.974525] ACPI: Interpreter enabled
[   62.974530] ACPI: (supports S0 S1 S4 S5)
[   62.974556] ACPI: Using PIC for interrupt routing
[   62.978929] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   62.979906] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   62.997749] ACPI: PCI Interrupt Link [LNKA] (IRQs 1 3 4 5 6 7 10 *11 12 14 15)
[   62.997922] ACPI: PCI Interrupt Link [LNKB] (IRQs 1 3 4 5 6 7 *10 11 12 14 15)
[   62.998092] ACPI: PCI Interrupt Link [LNKC] (IRQs 1 3 4 5 6 7 10 *11 12 14 15)
[   62.998262] ACPI: PCI Interrupt Link [LNKD] (IRQs 1 3 4 *5 6 7 10 11 12 14 15)
[   62.998428] Linux Plug and Play Support v0.97 (c) Adam Belay
[   62.998478] pnp: PnP ACPI init
[   62.998490] ACPI: bus type pnp registered
[   63.001673] pnp: PnP ACPI: found 13 devices
[   63.001677] ACPI: ACPI bus type pnp unregistered
[   63.001683] PnPBIOS: Disabled by ACPI PNP
[   63.002059] PCI: Using ACPI for IRQ routing
[   63.002064] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   63.037084] NET: Registered protocol family 8
[   63.037087] NET: Registered protocol family 20
[   63.037214] AppArmor: AppArmor Filesystem Enabled
[   63.041024] Time: tsc clocksource has been installed.
[   63.049081] system 00:00: iomem range 0xcbc00-0xcbfff has been reserved
[   63.049086] system 00:00: iomem range 0xf0000-0xf7fff could not be reserved
[   63.049091] system 00:00: iomem range 0xf8000-0xfbfff could not be reserved
[   63.049094] system 00:00: iomem range 0xfc000-0xfffff could not be reserved
[   63.049098] system 00:00: iomem range 0xbfff0000-0xbfffffff could not be reserved
[   63.049103] system 00:00: iomem range 0xffff0000-0xffffffff could not be reserved
[   63.049107] system 00:00: iomem range 0x0-0x9ffff could not be reserved
[   63.049111] system 00:00: iomem range 0x100000-0xbffeffff could not be reserved
[   63.049115] system 00:00: iomem range 0xfec00000-0xfec00fff could not be reserved
[   63.049119] system 00:00: iomem range 0xfee00000-0xfee00fff could not be reserved
[   63.049123] system 00:00: iomem range 0xfff80000-0xfffeffff has been reserved
[   63.049133] system 00:02: ioport range 0x4d0-0x4d1 has been reserved
[   63.049137] system 00:02: ioport range 0x294-0x297 has been reserved
[   63.079791] PCI: Bridge: 0000:00:01.0
[   63.079794]   IO window: disabled.
[   63.079800]   MEM window: d4000000-dbffffff
[   63.079805]   PREFETCH window: dc000000-e3ffffff
[   63.079825] PCI: Setting latency timer of device 0000:00:01.0 to 64
[   63.079844] NET: Registered protocol family 2
[   63.117162] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[   63.117742] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[   63.120587] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[   63.122128] TCP: Hash tables configured (established 131072 bind 65536)
[   63.122134] TCP reno registered
[   63.133283] checking if image is initramfs... it is
[   63.580982] Switched to high resolution mode on CPU 0
[   64.065683] Freeing initrd memory: 7665k freed
[   64.066748] audit: initializing netlink socket (disabled)
[   64.066774] audit(1232727869.776:1): initialized
[   64.067142] highmem bounce pool size: 64 pages
[   64.069998] VFS: Disk quotas dquot_6.5.1
[   64.070125] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   64.070346] io scheduler noop registered
[   64.070350] io scheduler anticipatory registered
[   64.070353] io scheduler deadline registered
[   64.070368] io scheduler cfq registered (default)
[   64.070396] PCI: VIA PCI bridge detected. Disabling DAC.
[   64.070480] Boot video device is 0000:01:00.0
[   64.070918] isapnp: Scanning for PnP cards...
[   64.424645] isapnp: No Plug & Play device found
[   64.466664] Real Time Clock Driver v1.12ac
[   64.466813] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   64.466970] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   64.467132] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[   64.467955] 00:08: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   64.468431] 00:09: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[   64.470070] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   64.470179] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[   64.470340] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[   64.470691] serio: i8042 KBD port at 0x60,0x64 irq 1
[   64.470699] serio: i8042 AUX port at 0x60,0x64 irq 12
[   64.480940] mice: PS/2 mouse device common for all mice
[   64.481126] EISA: Probing bus 0 at eisa.0
[   64.481150] Cannot allocate resource for EISA slot 4
[   64.481170] EISA: Detected 0 cards.
[   64.481175] cpuidle: using governor ladder
[   64.481178] cpuidle: using governor menu
[   64.481399] NET: Registered protocol family 1
[   64.481443] Using IPI No-Shortcut mode
[   64.481497] registered taskstats version 1
[   64.481645]   Magic number: 9:767:439
[   64.481923] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[   64.481926] EDD information not available.
[   64.482579] Freeing unused kernel memory: 364k freed
[   64.508858] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[   65.848661] fuse init (API version 7.9)
[   65.876515] ACPI: Fan [FAN] (on)
[   65.887482] ACPI: CPU0 (power states: C1[C1] C2[C2])
[   65.887492] ACPI: Processor [CPU0] (supports 2 throttling states)
[   65.889929] ACPI: Thermal Zone [THRM] (57 C)
[   66.766285] usbcore: registered new interface driver usbfs
[   66.766324] usbcore: registered new interface driver hub
[   66.785293] usbcore: registered new device driver usb
[   66.797801] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
[   66.798302] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 5
[   66.798307] PCI: setting IRQ 5 as level-triggered
[   66.798314] ACPI: PCI Interrupt 0000:00:09.0[B] -> Link [LNKD] -> GSI 5 (level, low) -> IRQ 5
[   66.798336] ohci_hcd 0000:00:09.0: OHCI Host Controller
[   66.798747] ohci_hcd 0000:00:09.0: new USB bus registered, assigned bus number 1
[   66.798777] ohci_hcd 0000:00:09.0: irq 5, io mem 0xe401a000
[   66.854751] usb usb1: configuration #1 chosen from 1 choice
[   66.854798] hub 1-0:1.0: USB hub found
[   66.854813] hub 1-0:1.0: 2 ports detected
[   66.912562] USB Universal Host Controller Interface driver v3.0
[   66.950233] SCSI subsystem initialized
[   66.960934] ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 11
[   66.960942] PCI: setting IRQ 11 as level-triggered
[   66.960948] ACPI: PCI Interrupt 0000:00:09.1[C] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
[   66.960972] ohci_hcd 0000:00:09.1: OHCI Host Controller
[   66.961013] ohci_hcd 0000:00:09.1: new USB bus registered, assigned bus number 2
[   66.961039] ohci_hcd 0000:00:09.1: irq 11, io mem 0xe401b000
[   67.018642] usb usb2: configuration #1 chosen from 1 choice
[   67.018691] hub 2-0:1.0: USB hub found
[   67.018711] hub 2-0:1.0: 2 ports detected
[   67.036509] libata version 3.00 loaded.
[   67.121095] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 10
[   67.121103] PCI: setting IRQ 10 as level-triggered
[   67.121109] ACPI: PCI Interrupt 0000:00:09.2[D] -> Link [LNKB] -> GSI 10 (level, low) -> IRQ 10
[   67.121132] ohci_hcd 0000:00:09.2: OHCI Host Controller
[   67.121178] ohci_hcd 0000:00:09.2: new USB bus registered, assigned bus number 3
[   67.121201] ohci_hcd 0000:00:09.2: irq 10, io mem 0xe4018000
[   67.174392] Floppy drive(s): fd0 is 1.44M
[   67.178649] usb usb3: configuration #1 chosen from 1 choice
[   67.178690] hub 3-0:1.0: USB hub found
[   67.178705] hub 3-0:1.0: 2 ports detected
[   67.196249] FDC 0 is a post-1991 82077
[   67.281294] ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 11
[   67.281302] ACPI: PCI Interrupt 0000:00:09.3[A] -> Link [LNKC] -> GSI 11 (level, low) -> IRQ 11
[   67.281323] ehci_hcd 0000:00:09.3: EHCI Host Controller
[   67.281367] ehci_hcd 0000:00:09.3: new USB bus registered, assigned bus number 4
[   67.281434] ehci_hcd 0000:00:09.3: debug port 1
[   67.281451] ehci_hcd 0000:00:09.3: irq 11, io mem 0xe4019000
[   67.292440] ehci_hcd 0000:00:09.3: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   67.292644] usb usb4: configuration #1 chosen from 1 choice
[   67.292689] hub 4-0:1.0: USB hub found
[   67.292702] hub 4-0:1.0: 6 ports detected
[   67.396775] ACPI: PCI Interrupt 0000:00:11.2[D] -> Link [LNKD] -> GSI 5 (level, low) -> IRQ 5
[   67.396800] uhci_hcd 0000:00:11.2: UHCI Host Controller
[   67.396842] uhci_hcd 0000:00:11.2: new USB bus registered, assigned bus number 5
[   67.396873] uhci_hcd 0000:00:11.2: irq 5, io base 0x0000e000
[   67.397066] usb usb5: configuration #1 chosen from 1 choice
[   67.397104] hub 5-0:1.0: USB hub found
[   67.397114] hub 5-0:1.0: 2 ports detected
[   67.500599] ACPI: PCI Interrupt 0000:00:11.3[D] -> Link [LNKD] -> GSI 5 (level, low) -> IRQ 5
[   67.500624] uhci_hcd 0000:00:11.3: UHCI Host Controller
[   67.500667] uhci_hcd 0000:00:11.3: new USB bus registered, assigned bus number 6
[   67.500697] uhci_hcd 0000:00:11.3: irq 5, io base 0x0000e400
[   67.500879] usb usb6: configuration #1 chosen from 1 choice
[   67.500916] hub 6-0:1.0: USB hub found
[   67.500926] hub 6-0:1.0: 2 ports detected
[   67.604599] ACPI: PCI Interrupt 0000:00:11.4[D] -> Link [LNKD] -> GSI 5 (level, low) -> IRQ 5
[   67.604623] uhci_hcd 0000:00:11.4: UHCI Host Controller
[   67.604671] uhci_hcd 0000:00:11.4: new USB bus registered, assigned bus number 7
[   67.604701] uhci_hcd 0000:00:11.4: irq 5, io base 0x0000e800
[   67.604874] usb usb7: configuration #1 chosen from 1 choice
[   67.604912] hub 7-0:1.0: USB hub found
[   67.604922] hub 7-0:1.0: 2 ports detected
[   67.680441] usb 4-6: new high speed USB device using ehci_hcd and address 2
[   67.715240] ACPI: PCI Interrupt 0000:00:11.1[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
[   67.715253] PCI: VIA VLink IRQ fixup for 0000:00:11.1, from 255 to 11
[   67.715365] ACPI: PCI interrupt for device 0000:00:11.1 disabled
[   67.722014] pata_via 0000:00:11.1: version 0.3.3
[   67.722054] ACPI: PCI Interrupt 0000:00:11.1[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
[   67.722064] PCI: VIA VLink IRQ fixup for 0000:00:11.1, from 255 to 11
[   67.724889] scsi0 : pata_via
[   67.726444] scsi1 : pata_via
[   67.726550] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xdc00 irq 14
[   67.726555] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xdc08 irq 15
[   67.813276] usb 4-6: configuration #1 chosen from 1 choice
[   67.813516] hub 4-6:1.0: USB hub found
[   67.813732] hub 4-6:1.0: 4 ports detected
[   68.208676] ata1.00: ATAPI: LITEON  DVD-ROM LTD163D, GHR3, max UDMA/33
[   68.208707] ata1.01: ATAPI: CW038D ATAPI CD-R/RW, V120c, max UDMA/33
[   68.372555] ata1.00: configured for UDMA/33
[   68.452270] end_request: I/O error, dev fd0, sector 0
[   68.540249] usb 6-2: new low speed USB device using uhci_hcd and address 2
[   68.544603] ata1.01: configured for UDMA/33
[   68.733613] usb 6-2: configuration #1 chosen from 1 choice
[   69.220296] usb 4-6.1: new full speed USB device using ehci_hcd and address 3
[   69.335573] usb 4-6.1: configuration #1 chosen from 1 choice
[   69.336822] usbcore: registered new interface driver hiddev
[   69.500119] end_request: I/O error, dev fd0, sector 0
[   69.826172] hiddev96hidraw0: USB HID v1.00 Device [American Power Conversion Back-UPS Office 500 FW: 4.3.D USB FW: d1] on usb-0000:00:11.3-2
[   69.826213] usbcore: registered new interface driver usbhid
[   69.826219] /build/buildd/linux-2.6.24/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
[   69.827903] usbcore: registered new interface driver libusual
[   69.836207] Initializing USB Mass Storage driver...
[   69.839242] scsi2 : SCSI emulation for USB Mass Storage devices
[   69.840476] usbcore: registered new interface driver usb-storage
[   69.840487] USB Mass Storage support registered.
[   69.840671] usb-storage: device found at 3
[   69.840675] usb-storage: waiting for device to settle before scanning
[   70.547972] end_request: I/O error, dev fd0, sector 0
[   71.595818] end_request: I/O error, dev fd0, sector 0
[   72.643671] end_request: I/O error, dev fd0, sector 0
[   73.691519] end_request: I/O error, dev fd0, sector 0
[   73.739505] ata2: port is slow to respond, please be patient (Status 0x80)
[   74.739368] end_request: I/O error, dev fd0, sector 0
[   74.840564] usb-storage: device scan complete
[   74.841563] scsi 2:0:0:0: Direct-Access     SanDisk  ImageMate CF-SM  0100 PQ: 0 ANSI: 0 CCS
[   74.842529] scsi 2:0:0:1: Direct-Access     SanDisk  ImageMate CF-SM  0100 PQ: 0 ANSI: 0 CCS
[   74.856690] Driver 'sd' needs updating - please use bus_type methods
[   74.858889] sd 2:0:0:0: [sda] Attached SCSI removable disk
[   74.861024] sd 2:0:0:1: [sdb] Attached SCSI removable disk
[   74.873292] sd 2:0:0:0: Attached scsi generic sg0 type 0
[   74.873324] sd 2:0:0:1: Attached scsi generic sg1 type 0
[   75.787218] end_request: I/O error, dev fd0, sector 0
[   76.947052] end_request: I/O error, dev fd0, sector 0
[   77.658634] sd 2:0:0:0: [sda] 62652416 512-byte hardware sectors (32078 MB)
[   77.659882] sd 2:0:0:0: [sda] Write Protect is off
[   77.659886] sd 2:0:0:0: [sda] Mode Sense: 43 00 00 00
[   77.659890] sd 2:0:0:0: [sda] Assuming drive cache: write through
[   77.662126] sd 2:0:0:0: [sda] 62652416 512-byte hardware sectors (32078 MB)
[   77.663382] sd 2:0:0:0: [sda] Write Protect is off
[   77.663386] sd 2:0:0:0: [sda] Mode Sense: 43 00 00 00
[   77.663390] sd 2:0:0:0: [sda] Assuming drive cache: write through
[   77.663397]  sda: sda1
[   78.554818] ata2: SRST failed (errno=-16)
[   78.723423] scsi 0:0:0:0: CD-ROM            LITEON   DVD-ROM LTD163D  GHR3 PQ: 0 ANSI: 5
[   78.723575] scsi 0:0:0:0: Attached scsi generic sg2 type 5
[   78.726008] scsi 0:0:1:0: CD-ROM            CyberDrv CW038D CD-R/RW   120C PQ: 0 ANSI: 5
[   78.726161] scsi 0:0:1:0: Attached scsi generic sg3 type 5
[   78.769421] Driver 'sr' needs updating - please use bus_type methods
[   78.771546] sr0: scsi3-mmc drive: 24x/48x cd/rw xa/form2 cdda tray
[   78.771556] Uniform CD-ROM driver Revision: 3.20
[   78.771622] sr 0:0:0:0: Attached scsi CD-ROM sr0
[   78.779022] sr1: scsi3-mmc drive: 4x/40x writer cd/rw xa/form2 cdda tray
[   78.779139] sr 0:0:1:0: Attached scsi CD-ROM sr1
[   79.003820] sd 2:0:0:1: [sdb] 16000 512-byte hardware sectors (8 MB)
[   79.005067] sd 2:0:0:1: [sdb] Write Protect is off
[   79.005071] sd 2:0:0:1: [sdb] Mode Sense: 43 00 00 00
[   79.005075] sd 2:0:0:1: [sdb] Assuming drive cache: write through
[   79.007311] sd 2:0:0:1: [sdb] 16000 512-byte hardware sectors (8 MB)
[   79.008689] sd 2:0:0:1: [sdb] Write Protect is off
[   79.008694] sd 2:0:0:1: [sdb] Mode Sense: 43 00 00 00
[   79.008697] sd 2:0:0:1: [sdb] Assuming drive cache: write through
[   79.008705]  sdb: sdb1
[   81.074465] end_request: I/O error, dev fd0, sector 0
[   83.389423] ISO 9660 Extensions: Microsoft Joliet Level 3
[   83.415457] ISO 9660 Extensions: RRIP_1991A
[   83.699652] Registering unionfs 1.4
[   83.699661] unionfs: debugging is not enabled
[   83.719192] loop: module loaded
[   84.020592] squashfs: version 3.3 (2007/10/31) Phillip Lougher
[  140.175699] input: PC Speaker as /devices/platform/pcspkr/input/input2
[  141.133221] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[  141.199712] input: ImExPS/2 Generic Explorer Mouse as /devices/platform/i8042/serio1/input/input3
[  141.343872] irda_init()
[  141.343906] NET: Registered protocol family 23
[  141.677822] Linux agpgart interface v0.102
[  141.877908] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[  142.185846] agpgart: Detected VIA KT266/KY266x/KT333 chipset
[  142.190844] agpgart: AGP aperture is 64M @ 0xd0000000
[  142.281862] parport_pc 00:0a: reported by Plug and Play ACPI
[  142.281918] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
[  142.463003] gameport: EMU10K1 is pci0000:00:0b.1/gameport0, io 0xd400, speed 1193kHz
[  142.653868] input: Power Button (FF) as /devices/virtual/input/input4
[  142.681734] ACPI: Power Button (FF) [PWRF]
[  142.681836] input: Power Button (CM) as /devices/virtual/input/input5
[  142.705682] ACPI: Power Button (CM) [PWRB]
[  142.705773] input: Sleep Button (CM) as /devices/virtual/input/input6
[  142.735800] ACPI: Sleep Button (CM) [SLPB]
[  143.521864] ACPI: PCI Interrupt 0000:00:0f.0[A] -> Link [LNKB] -> GSI 10 (level, low) -> IRQ 10
[  143.544645] phy0: Selected rate control algorithm 'simple'
[  145.825851] ACPI: PCI Interrupt 0000:00:0b.0[A] -> Link [LNKD] -> GSI 5 (level, low) -> IRQ 5
[  150.840536] ip_tables: (C) 2000-2006 Netfilter Core Team

---

### Post by wayne666 on 2009-01-25
I fixed the problem by searching the forums. I added noprobe=ata1 to the live cd boot line. I was then able to see my ide drive and install.:D

---

