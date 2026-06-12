---
title: "CDROM drives in Fiesty"
date: 2007-06-02
forum: Hardware &amp; Laptops
---

### Post by laidbackwebsage on 2007-06-02
OK, I've poured through all, and I mean ALL the posts on problems with CD ROM drives, and I still cannot get mine to work, either reading or burning CDs.

It worked with Dapper and Edgy, stopped working with Fiesty. So, the problem is with Fiesty.

What I need to know is when this is going to be fixed. If it's going to fixed in the next couple of weeks, fine, I'll wait. If it's not going to be fixed for a month or more, I need to know that so I can revert.

I know this post is starting to sound like a flame, and I apologize. But, like I said, I've been through every post about fiesty and cd roms, and I have found nothing that works, and I'm just a wee bit frustrated... 

For what its worth, my system sees my Samsung CDRW drive (SM-332B) as a SCSI device (its ATAPI/IDE). It's supposed top be /dev/hdc and /media/cdrom but neither of these work. K#b works sometimes; most of the time, it doesn't even see the drive.

If you know how to fix this, please share...

Thanks.

Kevin J

---

### Post by taurus on 2007-06-02
Can you post the output of these two commands from a terminal?

```
cat /etc/fstab
dmesg
```

---

### Post by laidbackwebsage on 2007-06-04
Yes, and thank you!  (Sorry for the delay in replying; I've been working double shifts...)

```

cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=cff90019-c871-4f61-b834-29d91c09ba4a /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda2
UUID=a9c93e1c-ff28-44e4-bae1-4e97a9b9875d /home           ext3    defaults        0       2
# /dev/hda3
UUID=b41a243a-13bd-42fc-9e88-41998aa1a305 none            swap    sw              0       0
#/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdc        /media/cdrom0 auto user,noauto 0 0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

```

```

dmesg
[    0.000000] Linux version 2.6.20-16-generic (root@terranova) (gcc version 4.1.2 (Ubuntu 4.1.2-0ubuntu4)) #2 SMP Wed May 23 01:46:23 UTC 2007 (Ubuntu 2.6.20-16.28-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000] sanitize start
[    0.000000] sanitize end
[    0.000000] copy_e820_map() start: 0000000000000000 size: 000000000009fc00 end: 000000000009fc00 type: 1
[    0.000000] copy_e820_map() type is E820_RAM
[    0.000000] copy_e820_map() start: 000000000009fc00 size: 0000000000000400 end: 00000000000a0000 type: 2
[    0.000000] copy_e820_map() start: 00000000000f0000 size: 0000000000010000 end: 0000000000100000 type: 2
[    0.000000] copy_e820_map() start: 0000000000100000 size: 000000003fef0000 end: 000000003fff0000 type: 1
[    0.000000] copy_e820_map() type is E820_RAM
[    0.000000] copy_e820_map() start: 000000003fff0000 size: 0000000000008000 end: 000000003fff8000 type: 3
[    0.000000] copy_e820_map() start: 000000003fff8000 size: 0000000000008000 end: 0000000040000000 type: 4
[    0.000000] copy_e820_map() start: 00000000fec00000 size: 0000000000001000 end: 00000000fec01000 type: 2
[    0.000000] copy_e820_map() start: 00000000fee00000 size: 0000000000001000 end: 00000000fee01000 type: 2
[    0.000000] copy_e820_map() start: 00000000ffee0000 size: 0000000000020000 end: 00000000fff00000 type: 2
[    0.000000] copy_e820_map() start: 00000000fffc0000 size: 0000000000040000 end: 0000000100000000 type: 2
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000003fff0000 (usable)
[    0.000000]  BIOS-e820: 000000003fff0000 - 000000003fff8000 (ACPI data)
[    0.000000]  BIOS-e820: 000000003fff8000 - 0000000040000000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000ffee0000 - 00000000fff00000 (reserved)
[    0.000000]  BIOS-e820: 00000000fffc0000 - 0000000100000000 (reserved)
[    0.000000] 127MB HIGHMEM available.
[    0.000000] 896MB LOWMEM available.
[    0.000000] Entering add_active_range(0, 0, 262128) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   229376
[    0.000000]   HighMem    229376 ->   262128
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   262128
[    0.000000] On node 0 totalpages: 262128
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 1760 pages used for memmap
[    0.000000]   Normal zone: 223520 pages, LIFO batch:31
[    0.000000]   HighMem zone: 255 pages used for memmap
[    0.000000]   HighMem zone: 32497 pages, LIFO batch:7
[    0.000000] DMI 2.3 present.
[    0.000000] ACPI: RSDP (v000 AMI                                   ) @ 0x000fa340
[    0.000000] ACPI: RSDT (v001 AMIINT SiS735XX 0x00001000 MSFT 0x0100000b) @ 0x3fff0000
[    0.000000] ACPI: FADT (v001 AMIINT SiS735XX 0x00001000 MSFT 0x0100000b) @ 0x3fff0030
[    0.000000] ACPI: DSDT (v001    SiS      735 0x00000100 MSFT 0x0100000d) @ 0x00000000
[    0.000000] ACPI: PM-Timer IO Port: 0x808
[    0.000000] Allocating PCI resources starting at 50000000 (gap: 40000000:bec00000)
[    0.000000] Detected 995.823 MHz processor.
[   31.053845] Built 1 zonelists.  Total pages: 260081
[   31.053853] Kernel command line: root=UUID=cff90019-c871-4f61-b834-29d91c09ba4a ro quiet splash
[   31.054182] Local APIC disabled by BIOS -- you can enable it with "lapic"
[   31.054200] mapped APIC to ffffd000 (0180c000)
[   31.054207] Enabling fast FPU save and restore... done.
[   31.054228] Initializing CPU#0
[   31.054324] PID hash table entries: 4096 (order: 12, 16384 bytes)
[   31.055947] Console: colour VGA+ 80x25
[   31.057635] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[   31.060520] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[   31.134052] Memory: 1028308k/1048512k available (1992k kernel code, 19464k reserved, 896k data, 328k init, 131008k highmem)
[   31.134076] virtual kernel memory layout:
[   31.134078]     fixmap  : 0xfff4e000 - 0xfffff000   ( 708 kB)
[   31.134081]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   31.134084]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
[   31.134087]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
[   31.134090]       .init : 0xc03d9000 - 0xc042b000   ( 328 kB)
[   31.134092]       .data : 0xc02f2354 - 0xc03d26d4   ( 896 kB)
[   31.134095]       .text : 0xc0100000 - 0xc02f2354   (1992 kB)
[   31.134102] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   31.210283] Calibrating delay using timer specific routine.. 1992.84 BogoMIPS (lpj=3985680)
[   31.210380] Security Framework v1.0.0 initialized
[   31.210397] SELinux:  Disabled at boot.
[   31.210433] Mount-cache hash table entries: 512
[   31.210785] CPU: After generic identify, caps: 0183f9ff c1c7f9ff 00000000 00000000 00000000 00000000 00000000
[   31.210803] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[   31.210809] CPU: L2 Cache: 256K (64 bytes/line)
[   31.210814] CPU: After all inits, caps: 0183f9ff c1c7f9ff 00000000 00000420 00000000 00000000 00000000
[   31.210841] Compat vDSO mapped to ffffe000.
[   31.210856] Remapping vsyscall page to ffffe000
[   31.210878] Checking 'hlt' instruction... OK.
[   31.226351] SMP alternatives: switching to UP code
[   31.226916] Freeing SMP alternatives: 11k freed
[   31.227394] Early unpacking initramfs... done
[   31.830876] ACPI: Core revision 20060707
[   31.831990] ACPI: Looking for DSDT in initramfs... file /DSDT.aml not found, using machine DSDT.
[   31.834461] ACPI: setting ELCR to 0200 (from 1820)
[   31.837457] CPU0: AMD Athlon(tm) Processor stepping 04
[   31.837468] SMP motherboard not detected.
[   31.837475] Local APIC not detected. Using dummy APIC emulation.
[   31.837569] Brought up 1 CPUs
[   31.838146] Booting paravirtualized kernel on bare hardware
[   31.838269] Time: 21:03:15  Date: 05/04/107
[   31.838340] NET: Registered protocol family 16
[   31.838545] EISA bus registered
[   31.838553] ACPI: bus type pci registered
[   31.840269] PCI: PCI BIOS revision 2.10 entry at 0xfdb01, last bus=1
[   31.840274] PCI: Using configuration type 1
[   31.840278] Setting up standard PCI resources
[   31.848276] ACPI: Interpreter enabled
[   31.848285] ACPI: Using PIC for interrupt routing
[   31.848913] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   31.848928] PCI: Probing PCI hardware (bus 00)
[   31.850207] Enabling SiS 96x SMBus.
[   31.851003] Boot video device is 0000:01:00.0
[   31.851066] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   31.859512] ACPI: Power Resource [URP1] (off)
[   31.859632] ACPI: Power Resource [URP2] (off)
[   31.859752] ACPI: Power Resource [FDDP] (off)
[   31.859870] ACPI: Power Resource [LPTP] (off)
[   31.861119] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 *5 7 10 11 12 14 15)
[   31.861533] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 7 10 11 *12 14 15)
[   31.861943] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 7 10 *11 12 14 15)
[   31.862391] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 7 10 *11 12 14 15)
[   31.862820] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 7 10 11 12 14 15) *0, disabled.
[   31.863222] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 7 10 11 12 14 15) *0, disabled.
[   31.863623] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 7 10 11 12 14 15) *0, disabled.
[   31.864027] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 7 10 11 *12 14 15)
[   31.864301] Linux Plug and Play Support v0.97 (c) Adam Belay
[   31.864327] pnp: PnP ACPI init
[   31.870997] pnp: PnP ACPI: found 12 devices
[   31.871009] PnPBIOS: Disabled by ACPI PNP
[   31.871128] PCI: Using ACPI for IRQ routing
[   31.871136] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   31.875059] NET: Registered protocol family 8
[   31.875063] NET: Registered protocol family 20
[   31.875757] PCI: Bridge: 0000:00:01.0
[   31.875764]   IO window: 9000-9fff
[   31.875774]   MEM window: cfe00000-cfefffff
[   31.875781]   PREFETCH window: bfc00000-cfcfffff
[   31.875852] NET: Registered protocol family 2
[   31.910271] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[   31.910748] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[   31.915782] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[   31.918442] TCP: Hash tables configured (established 131072 bind 65536)
[   31.918450] TCP reno registered
[   31.930366] checking if image is initramfs... it is
[   33.088122] Freeing initrd memory: 6771k freed
[   33.089027] audit: initializing netlink socket (disabled)
[   33.089057] audit(1180990997.216:1): initialized
[   33.089194] highmem bounce pool size: 64 pages
[   33.089321] VFS: Disk quotas dquot_6.5.1
[   33.089369] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   33.089483] io scheduler noop registered
[   33.089489] io scheduler anticipatory registered
[   33.089494] io scheduler deadline registered
[   33.089509] io scheduler cfq registered (default)
[   33.090054] isapnp: Scanning for PnP cards...
[   33.443588] isapnp: No Plug & Play device found
[   33.496280] Real Time Clock Driver v1.12ac
[   33.496378] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   33.496586] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   33.496959] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[   33.498207] 00:07: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   33.498785] 00:08: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[   33.499298] mice: PS/2 mouse device common for all mice
[   33.500389] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   33.500918] input: Macintosh mouse button emulation as /class/input/input0
[   33.500987] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[   33.500996] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[   33.501382] PNP: PS/2 Controller [PNP0303:PS2K] at 0x60,0x64 irq 1
[   33.501388] PNP: PS/2 controller doesn't have AUX irq; using default 12
[   33.511988] serio: i8042 KBD port at 0x60,0x64 irq 1
[   33.512248] EISA: Probing bus 0 at eisa.0
[   33.512301] EISA: Detected 0 cards.
[   33.542697] TCP cubic registered
[   33.542713] NET: Registered protocol family 1
[   33.542762] Using IPI No-Shortcut mode
[   33.542967] ACPI: (supports S0 S1 S4 S5)
[   33.543044]   Magic number: 11:41:95
[   33.544177] Freeing unused kernel memory: 328k freed
[   33.545617] Time: tsc clocksource has been installed.
[   35.078416] Capability LSM initialized
[   36.162328] usbcore: registered new interface driver usbfs
[   36.162395] usbcore: registered new interface driver hub
[   36.162447] usbcore: registered new device driver usb
[   36.164111] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
[   36.164581] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 11
[   36.164589] PCI: setting IRQ 11 as level-triggered
[   36.164594] ACPI: PCI Interrupt 0000:00:02.2[D] -> Link [LNKD] -> GSI 11 (level, low) -> IRQ 11
[   36.164621] ohci_hcd 0000:00:02.2: OHCI Host Controller
[   36.164951] ohci_hcd 0000:00:02.2: new USB bus registered, assigned bus number 1
[   36.164984] ohci_hcd 0000:00:02.2: irq 11, io mem 0xcfffe000
[   36.206082] SCSI subsystem initialized
[   36.216251] libata version 2.20 loaded.
[   36.260164] usb usb1: configuration #1 chosen from 1 choice
[   36.260225] hub 1-0:1.0: USB hub found
[   36.260254] hub 1-0:1.0: 3 ports detected
[   36.361538] ACPI: PCI Interrupt Link [LNKH] enabled at IRQ 12
[   36.361551] PCI: setting IRQ 12 as level-triggered
[   36.361557] ACPI: PCI Interrupt 0000:00:02.3[A] -> Link [LNKH] -> GSI 12 (level, low) -> IRQ 12
[   36.361588] ohci_hcd 0000:00:02.3: OHCI Host Controller
[   36.361636] ohci_hcd 0000:00:02.3: new USB bus registered, assigned bus number 2
[   36.361667] ohci_hcd 0000:00:02.3: irq 12, io mem 0xcffff000
[   36.419069] usb usb2: configuration #1 chosen from 1 choice
[   36.419135] hub 2-0:1.0: USB hub found
[   36.419161] hub 2-0:1.0: 3 ports detected
[   36.495625] Floppy drive(s): fd0 is 1.44M
[   36.521468] ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 5
[   36.521480] PCI: setting IRQ 5 as level-triggered
[   36.521486] ACPI: PCI Interrupt 0000:00:09.0[A] -> Link [LNKA] -> GSI 5 (level, low) -> IRQ 5
[   36.521517] ohci_hcd 0000:00:09.0: OHCI Host Controller
[   36.521570] ohci_hcd 0000:00:09.0: new USB bus registered, assigned bus number 3
[   36.521609] ohci_hcd 0000:00:09.0: irq 5, io mem 0xcfffb000
[   36.571924] FDC 0 is a post-1991 82077
[   36.606805] usb usb3: configuration #1 chosen from 1 choice
[   36.606875] hub 3-0:1.0: USB hub found
[   36.606902] hub 3-0:1.0: 3 ports detected
[   36.664781] usb 1-1: new low speed USB device using ohci_hcd and address 2
[   36.709343] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 12
[   36.709355] ACPI: PCI Interrupt 0000:00:09.1[B] -> Link [LNKB] -> GSI 12 (level, low) -> IRQ 12
[   36.709387] ohci_hcd 0000:00:09.1: OHCI Host Controller
[   36.709440] ohci_hcd 0000:00:09.1: new USB bus registered, assigned bus number 4
[   36.709472] ohci_hcd 0000:00:09.1: irq 12, io mem 0xcfffc000
[   36.794745] usb usb4: configuration #1 chosen from 1 choice
[   36.794821] hub 4-0:1.0: USB hub found
[   36.794847] hub 4-0:1.0: 2 ports detected
[   36.887776] usb 1-1: configuration #1 chosen from 1 choice
[   36.897094] pata_sis 0000:00:02.5: version 0.5.1
[   36.897312] ata1: PATA max UDMA/100 cmd 0x000101f0 ctl 0x000103f6 bmdma 0x0001ff00 irq 14
[   36.897386] ata2: PATA max UDMA/100 cmd 0x00010170 ctl 0x00010376 bmdma 0x0001ff08 irq 15
[   36.897410] scsi0 : pata_sis
[   37.061643] ata1.00: ata_hpa_resize 1: sectors = 117231408, hpa_sectors = 117231408
[   37.061655] ata1.00: ATA-5: WDC WD600BB-00CAA1, 17.07W17, max UDMA/100
[   37.061661] ata1.00: 117231408 sectors, multi 16: LBA
[   37.069595] ata1.00: ata_hpa_resize 1: sectors = 117231408, hpa_sectors = 117231408
[   37.069601] ata1.00: configured for UDMA/100
[   37.069625] scsi1 : pata_sis
[   37.192569] usb 2-1: new full speed USB device using ohci_hcd and address 2
[   37.389126] ata2.00: ATAPI, max UDMA/33
[   37.396519] usb 2-1: configuration #1 chosen from 1 choice
[   37.399478] hub 2-1:1.0: USB hub found
[   37.402347] hub 2-1:1.0: 4 ports detected
[   37.553064] ata2.00: configured for UDMA/33
[   37.553353] scsi 0:0:0:0: Direct-Access     ATA      WDC WD600BB-00CA 17.0 PQ: 0 ANSI: 5
[   37.554347] scsi 1:0:0:0: CD-ROM            SAMSUNG  CDRW/DVD SM-332B T406 PQ: 0 ANSI: 5
[   37.563375] ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 11
[   37.563387] ACPI: PCI Interrupt 0000:00:09.2[C] -> Link [LNKC] -> GSI 11 (level, low) -> IRQ 11
[   37.563413] ehci_hcd 0000:00:09.2: EHCI Host Controller
[   37.563480] ehci_hcd 0000:00:09.2: new USB bus registered, assigned bus number 5
[   37.584547] ehci_hcd 0000:00:09.2: irq 11, io mem 0xcfffdf00
[   37.584563] ehci_hcd 0000:00:09.2: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   37.584811] usb usb5: configuration #1 chosen from 1 choice
[   37.584879] hub 5-0:1.0: USB hub found
[   37.584907] hub 5-0:1.0: 5 ports detected
[   37.590407] SCSI device sda: 117231408 512-byte hdwr sectors (60022 MB)
[   37.590471] sda: Write Protect is off
[   37.590476] sda: Mode Sense: 00 3a 00 00
[   37.590507] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   37.590651] SCSI device sda: 117231408 512-byte hdwr sectors (60022 MB)
[   37.590669] sda: Write Protect is off
[   37.590673] sda: Mode Sense: 00 3a 00 00
[   37.590699] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   37.590708]  sda: sda1 sda2 sda3
[   37.635826] sd 0:0:0:0: Attached scsi disk sda
[   37.645563] sd 0:0:0:0: Attached scsi generic sg0 type 0
[   37.645805] sr 1:0:0:0: Attached scsi generic sg1 type 5
[   37.676003] sr0: scsi3-mmc drive: 0x/40x writer cd/rw xa/form2 cdda tray
[   37.676016] Uniform CD-ROM driver Revision: 3.20
[   37.676610] sr 1:0:0:0: Attached scsi CD-ROM sr0
[   37.735624] ata2.00: 12 bytes trailing data
[   37.735854] ata2.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
[   37.735863] ata2.00: (BMDMA stat 0x65)
[   37.735876] ata2.00: cmd a0/01:00:00:00:00/00:00:00:00:00/a0 tag 0 cdb 0x12 data 254 in
[   37.735880]          res 51/51:03:00:00:00/00:00:00:00:00/a0 Emask 0x3 (HSM violation)
[   37.735913] ata2: soft resetting port
[   37.742146] usb 2-1.4: new full speed USB device using ohci_hcd and address 3
[   37.865278] usb 2-1.4: configuration #1 chosen from 1 choice
[   37.869102] usbcore: registered new interface driver hiddev
[   37.875392] input: Logitech USB-PS/2 Optical Mouse as /class/input/input1
[   37.875445] input: USB HID v1.10 Mouse [Logitech USB-PS/2 Optical Mouse] on usb-0000:00:02.2-1
[   37.875494] usbcore: registered new interface driver usbhid
[   37.875502] drivers/usb/input/hid-core.c: v2.6:USB HID core driver
[   37.989404] Attempting manual resume
[   37.989413] swsusp: Resume From Partition 8:3
[   37.989417] PM: Checking swsusp image.
[   37.989784] PM: Resume from disk failed.
[   38.042677] kjournald starting.  Commit interval 5 seconds
[   38.042704] EXT3-fs: mounted filesystem with ordered data mode.
[   38.044505] ata2.00: revalidation failed (errno=-2)
[   38.044520] ata2: failed to recover some devices, retrying in 5 secs
[   39.617328] input: AT Translated Set 2 keyboard as /class/input/input2
[   43.046909] ata2: soft resetting port
[   43.358898] ata2.00: revalidation failed (errno=-2)
[   43.358911] ata2: failed to recover some devices, retrying in 5 secs
[   48.361436] ata2: soft resetting port
[   48.673472] ata2.00: revalidation failed (errno=-2)
[   48.673486] ata2.00: disabled
[   49.177229] ata2: EH complete
[   52.519898] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   52.538780] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   52.551916] sis630_smbus 0000:00:02.0: SIS630 comp. bus not detected, module not inserted.
[   52.554672] sis96x_smbus 0000:00:02.1: SiS96x SMBus base address: 0x0c00
[   53.056562] Linux video capture interface: v2.00
[   53.099250] bttv: driver version 0.9.16 loaded
[   53.099262] bttv: using 8 buffers with 2080k (520 pages) each for capture
[   53.099379] bttv: Bt8xx card found (0).
[   53.099414] ACPI: PCI Interrupt 0000:00:0d.0[A] -> Link [LNKC] -> GSI 11 (level, low) -> IRQ 11
[   53.099435] bttv0: Bt878 (rev 2) at 0000:00:0d.0, irq: 11, latency: 64, mmio: 0xcfdfe000
[   53.099456] bttv0: detected: ATI TV Wonder/VE [card=64], PCI subsystem ID is 1002:0003
[   53.099463] bttv0: using: ATI TV-Wonder VE [card=64,autodetected]
[   53.099514] bttv0: gpio: en=00000000, out=00000000 in=00ffffff [init]
[   53.100091] bttv0: using tuner=19
[   53.100100] bttv0: i2c: checking for TDA9875 @ 0xb0... not found
[   53.100824] bttv0: i2c: checking for TDA7432 @ 0x8a... not found
[   53.101541] bttv0: i2c: checking for TDA9887 @ 0x86... not found
[   53.137740] tuner 1-0060: All bytes are equal. It is not a TEA5767
[   53.137752] tuner 1-0060: chip found @ 0xc0 (bt878 #0 [sw])
[   53.137819] tuner 1-0060: type set to 19 (Temic PAL* auto (4006 FN5))
[   53.137828] tuner 1-0060: type set to 19 (Temic PAL* auto (4006 FN5))
[   53.148910] bttv0: registered device video0
[   53.149020] bttv0: registered device vbi0
[   53.149046] bttv0: PLL: 28636363 => 35468950 .. ok
[   53.202735] bt878: AUDIO driver version 0.0.0 loaded
[   53.202824] bt878: Bt878 AUDIO function found (0).
[   53.202851] ACPI: PCI Interrupt 0000:00:0d.1[A] -> Link [LNKC] -> GSI 11 (level, low) -> IRQ 11
[   53.202865] bt878_probe: card id=[0x31002], Unknown card.
[   53.202868] Exiting..
[   53.202877] ACPI: PCI interrupt for device 0000:00:0d.1 disabled
[   53.202886] bt878: probe of 0000:00:0d.1 failed with error -22
[   53.232392] ath_hal: module license 'Proprietary' taints kernel.
[   53.234132] ath_hal: 0.9.18.0 (AR5210, AR5211, AR5212, RF5111, RF5112, RF2413, RF5413)
[   53.592077] Linux agpgart interface v0.102 (c) Dave Jones
[   53.660102] wlan: 0.8.4.2 (0.9.3)
[   53.700819] ath_pci: 0.9.4.5 (0.9.3)
[   53.700944] ACPI: PCI Interrupt 0000:00:0b.0[A] -> Link [LNKB] -> GSI 12 (level, low) -> IRQ 12
[   54.957275] ath_rate_sample: 1.2 (0.9.3)
[   54.957985] wifi0: 11b rates: 1Mbps 2Mbps 5.5Mbps 11Mbps
[   54.957995] wifi0: 11g rates: 1Mbps 2Mbps 5.5Mbps 11Mbps 6Mbps 9Mbps 12Mbps 18Mbps 24Mbps 36Mbps 48Mbps 54Mbps
[   54.958011] wifi0: turboG rates: 6Mbps 12Mbps 18Mbps 24Mbps 36Mbps 48Mbps 54Mbps
[   54.958022] wifi0: H/W encryption support: WEP AES AES_CCM TKIP
[   54.958029] wifi0: mac 7.9 phy 4.5 radio 5.6
[   54.958037] wifi0: Use hw queue 1 for WME_AC_BE traffic
[   54.958042] wifi0: Use hw queue 0 for WME_AC_BK traffic
[   54.958046] wifi0: Use hw queue 2 for WME_AC_VI traffic
[   54.958051] wifi0: Use hw queue 3 for WME_AC_VO traffic
[   54.958055] wifi0: Use hw queue 8 for CAB traffic
[   54.958058] wifi0: Use hw queue 9 for beacons
[   54.974529] wifi0: Atheros 5212: mem=0xcffe0000, irq=12
[   54.974576] agpgart: Detected SiS 735 chipset
[   54.981019] agpgart: AGP aperture is 64M @ 0xd0000000
[   55.051612] input: PC Speaker as /class/input/input3
[   55.310973] ACPI: PCI Interrupt 0000:00:11.0[A] -> Link [LNKB] -> GSI 12 (level, low) -> IRQ 12
[   55.634281] ACPI: PCI Interrupt 0000:00:02.7[C] -> Link [LNKC] -> GSI 11 (level, low) -> IRQ 11
[   55.947161] intel8x0_measure_ac97_clock: measured 55699 usecs
[   55.947171] intel8x0: clocking to 48000
[   56.141225] parport: PnPBIOS parport detected.
[   56.141294] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
[   56.371365] drivers/usb/class/usblp.c: usblp0: USB Bidirectional printer dev 3 if 1 alt 0 proto 2 vid 0x03F0 pid 0x3D11
[   56.371405] usbcore: registered new interface driver usblp
[   56.371412] drivers/usb/class/usblp.c: v0.13: USB Printer Device Class driver
[   57.256056] NET: Registered protocol family 10
[   57.256255] lo: Disabled Privacy Extensions
[   57.619422] fuse init (API version 7.8)
[   57.663772] lp0: using parport0 (interrupt-driven).
[   57.740759] Adding 2289252k swap on /dev/disk/by-uuid/b41a243a-13bd-42fc-9e88-41998aa1a305.  Priority:-1 extents:1 across:2289252k
[   57.896172] EXT3 FS on sda1, internal journal
[   58.215943] kjournald starting.  Commit interval 5 seconds
[   58.216130] EXT3 FS on sda2, internal journal
[   58.216142] EXT3-fs: mounted filesystem with ordered data mode.
[   59.907834] NET: Registered protocol family 17
[   64.885358] input: Power Button (FF) as /class/input/input4
[   64.895317] ACPI: Power Button (FF) [PWRF]
[   64.944637] input: Sleep Button (CM) as /class/input/input5
[   64.945186] ACPI: Sleep Button (CM) [SLPB]
[   65.125055] Using specific hotkey driver
[   65.369690] ibm_acpi: ec object not found
[   65.465965] No dock devices found.
[   65.505771] pcc_acpi: loading...
[   65.890271] powernow: No powernow capabilities detected
[   67.283873] ath0: no IPv6 routers present
[   68.344042] cdrom: This disc doesn't have any tracks I recognize!
[   68.349536] Buffer I/O error on device sr0, logical block 0
[   68.349554] Buffer I/O error on device sr0, logical block 1
[   68.349560] Buffer I/O error on device sr0, logical block 2
[   68.349566] Buffer I/O error on device sr0, logical block 3
[   68.349571] Buffer I/O error on device sr0, logical block 4
[   68.349576] Buffer I/O error on device sr0, logical block 5
[   68.349581] Buffer I/O error on device sr0, logical block 6
[   68.349586] Buffer I/O error on device sr0, logical block 7
[   68.351915] Buffer I/O error on device sr0, logical block 0
[   68.352207] Buffer I/O error on device sr0, logical block 1
[   69.568166] ppdev: user-space parallel port driver
[   72.827334] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[   72.827346] apm: overridden by ACPI.
[   75.688991] Bluetooth: Core ver 2.11
[   75.689129] NET: Registered protocol family 31
[   75.689134] Bluetooth: HCI device and connection manager initialized
[   75.689143] Bluetooth: HCI socket layer initialized
[   75.747555] Bluetooth: L2CAP ver 2.8
[   75.747566] Bluetooth: L2CAP socket layer initialized
[   75.892660] Bluetooth: RFCOMM socket layer initialized
[   75.892697] Bluetooth: RFCOMM TTY layer initialized
[   75.892702] Bluetooth: RFCOMM ver 1.8
[   79.625862] [drm] Initialized drm 1.1.0 20060810
[   79.646363] ACPI: PCI Interrupt 0000:01:00.0[A] -> Link [LNKA] -> GSI 5 (level, low) -> IRQ 5
[   79.647518] [drm] Initialized radeon 1.25.0 20060524 on minor 0
[   81.478329] agpgart: Found an AGP 2.0 compliant device at 0000:00:00.0.
[   81.478366] agpgart: Putting AGP V2 device at 0000:00:00.0 into 1x mode
[   81.478421] agpgart: Putting AGP V2 device at 0000:01:00.0 into 1x mode
[   81.767849] [drm] Setting GART location based on new memory map
[   81.767914] [drm] writeback test succeeded in 1 usecs

```

Thanks again!

Kevin J

---

### Post by taurus on 2007-06-04
Feisty sees your CD-ROM as sr0, bot hdc anymore.

```
[   37.676003] sr0: scsi3-mmc drive: 0x/40x writer cd/rw xa/form2 cdda tray
[   37.676016] Uniform CD-ROM driver Revision: 3.20
[   37.676610] sr 1:0:0:0: Attached scsi CD-ROM sr0
```
So, edit /etc/fstab and replace /dev/hdc with /dev/sr0.  Reboot and see if you can use your CD-ROM now.

---

### Post by laidbackwebsage on 2007-06-04
taurus,

Below are the changes I made to /etc/fstab file:

```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=cff90019-c871-4f61-b834-29d91c09ba4a /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda2
UUID=a9c93e1c-ff28-44e4-bae1-4e97a9b9875d /home           ext3    defaults        0       2
# /dev/hda3
UUID=b41a243a-13bd-42fc-9e88-41998aa1a305 none            swap    sw              0       0
#/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
#/dev/hdc        /media/cdrom0 auto user,noauto 0 0
#/dev/sr0       /media/cdrom0 auto user,noauto 0 0
/dev/sr0        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0


```

Still not being seen by k3b, or anything else, for tha matter...   :sad:

Any other thoughts?

Thanks!

Kevin J

---

### Post by CaseyR on 2007-06-06
it looks like you may have commented out the wrong entry

you have:

#/dev/sr0       /media/cdrom0 auto user,noauto 0 0
/dev/sr0        /media/cdrom0   udf,iso9660 user,noauto     0       0

it may need to be:

/dev/sr0       /media/cdrom0 auto user,noauto 0 0
#/dev/sr0        /media/cdrom0   udf,iso9660 user,noauto     0       0

---

### Post by laidbackwebsage on 2007-06-06
CaseyR,

Thanks, but I tried it both ways, neither worked...   <sigh>

I'll probably have to revert this coming weekend...

Thanks.

Kevin J

---

### Post by laidbackwebsage on 2007-06-16
<bump> to the top

---

### Post by Coombabah on 2007-06-20
I also have a SAMSUNG  CDRW/DVD SM-332B that has the same problem in Feisty.

It's in a Dell Optiplex GX260. 
It won't boot the live CD without workarounds either.
Had to press F6, add break -top, then modprobe piix, exit, to get the install to work.

Hoping that in the future Dell hardware and Linux are better friends.

---

### Post by Coombabah on 2007-11-29
> **Coombabah said:**
> I also have a SAMSUNG  CDRW/DVD SM-332B that has the same problem in Feisty.

It's in a Dell Optiplex GX260. 
It won't boot the live CD without workarounds either.
Had to press F6, add break -top, then modprobe piix, exit, to get the install to work.

Hoping that in the future Dell hardware and Linux are better friends.

Update: After upgrading to Gutsy the CDROM is working again. The Dell GX260 will also boot from the Gutsy Live CD without any workarounds. :)

---

### Post by laidbackwebsage on 2007-11-29
Yep, me, too!  :)

---

