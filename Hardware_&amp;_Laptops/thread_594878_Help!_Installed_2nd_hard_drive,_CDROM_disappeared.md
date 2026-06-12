---
title: "Help! Installed 2nd hard drive, CDROM disappeared"
date: 2007-10-28
forum: Hardware &amp; Laptops
---

### Post by geomantic8 on 2007-10-28
Hi all,

I recently installed a 2nd hard drive. Works fine, no issues. Somehow, in the process, my CDROM was deleted. I mean, vanished. I've gone through everything I know to do and come up blank, -lshw, lsmod, lspci list nothing to do with 'CD' or 'CD-ROM' or anything remotely close. Also, dmesg | grep CD  turns up nothing.

Curiously, it shows up in Nautilus as CD-ROM1, but when I try to mount, I get an error, 'mount: unknown filesystem type ''   '.  But I take this to mean the mount points exist and that it can't find the device.

Any suggestions? Thanks in advance,
-g8

FWIW, posted below is the contents of /etc/fstab:
[INDENT]# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1 -- converted during upgrade to edgy
UUID=2b462b05-778e-4b63-818b-3fe3df6b1f61 / ext3 defaults,errors=remount-ro 0 1
# /dev/hda6 -- converted during upgrade to edgy
UUID=828a05f0-688c-410a-9b8d-41d642ad7b61 /home ext3 defaults 0 2
# /dev/hda5 -- converted during upgrade to edgy
UUID=4c9a64a2-6374-443b-9789-be291e7640c3 /usr ext3 defaults 0 2
# /dev/hda2 -- converted during upgrade to edgy
UUID=4d6aa428-5902-43b9-b836-4106671056c8 none swap sw 0 0
#
/dev/cdrom     /media/cdrom   udf,iso9660, user,noauto     0       0
#
# /dev/sdb -- second hard drive (Maxtor)
 /dev/sdb1	/storage      ext3     defaults           0       0
[/INDENT]

---

### Post by Swankyman on 2007-10-28
Hey

Did you see if the both drives (old and new) are detected by the bios. You may have connected both drives to the same cable with both as either slave or master !!!!

rich

---

### Post by geomantic8 on 2007-10-28
Thanks for the prompt response.

Yes, I checked cabling last night. Both hard drives are connected appropriately as the cable is marked 'master' and 'slave'. And the separate cable connects the CD drive. 

In other words, the CD cable was left intact; I simply plugged in the 2nd hard drive to the 'slave' connector and rebooted.

---

### Post by Swankyman on 2007-10-28
did you check your bios though

???

It should see them both!

---

### Post by geomantic8 on 2007-10-28
Okay, just checked the BIOS and...no, the CD does not show up.

Primary IDE Master = IBM DTLA 30745
Primary IDE Slave = Maxtor 51023H2
Secondary IDE Master = none
Secondary IDE Slave = none

1st Boot device = ATAPI CDROM
2nd Boot device = floppy
3rd Boot device = IDE-HDD

CD/DVD detection was disabled, so I enabled it and continued with boot. No CD was detected, so I hit 'enter' to continue booting w/out CD.

Thanks again for the quick response.
-g8

---

### Post by Swankyman on 2007-10-28
Are you connecting the drives to the Secondary IDE? and are the jumpers on the two drives set to cable select or master/slave?

---

### Post by geomantic8 on 2007-10-28
Well, the primary cable is connected to the two hard drives. It has labels which indicating which plug is master and which is slave. The other cable (secondary, I suppose) is connected to the CD drive. I have not changed any jumper settings. 

Just to clarify, both hard drives are working correctly, it's just the CD drive that is missing.

Thanks once again,
-g8

---

### Post by Swankyman on 2007-10-29
Sorry I thought maybe it was a hardware thing!!! Just to double check can you get the computer to boot into any CD (i.e. something like the LiveCD)

If yes then reboot and attach the output of 

dmesg

typed into a terminal

Rich

---

### Post by geomantic8 on 2007-10-29
Sure, here is the output from dmesg.  Just to be sure, I did dmesg | grep CD (and variants) and turned up nothing. I really don't get what's going on here. At any rate, thanks again. 
-g8

[    0.000000] Linux version 2.6.20-16-386 (root@terranova) (gcc version 4.1.2 (Ubuntu 4.1.2-0ubuntu4)) #2 Sun Sep 23 19:47:10 UTC 2007 (Ubuntu 2.6.20-16.32-386)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000] sanitize start
[    0.000000] sanitize end
[    0.000000] copy_e820_map() start: 0000000000000000 size: 000000000009fc00 end: 000000000009fc00 type: 1
[    0.000000] copy_e820_map() type is E820_RAM
[    0.000000] copy_e820_map() start: 000000000009fc00 size: 0000000000000400 end: 00000000000a0000 type: 2
[    0.000000] copy_e820_map() start: 00000000000e0000 size: 0000000000020000 end: 0000000000100000 type: 2
[    0.000000] copy_e820_map() start: 0000000000100000 size: 000000001fec0000 end: 000000001ffc0000 type: 1
[    0.000000] copy_e820_map() type is E820_RAM
[    0.000000] copy_e820_map() start: 000000001ffc0000 size: 0000000000038000 end: 000000001fff8000 type: 3
[    0.000000] copy_e820_map() start: 000000001fff8000 size: 0000000000008000 end: 0000000020000000 type: 4
[    0.000000] copy_e820_map() start: 00000000ffb80000 size: 0000000000080000 end: 00000000ffc00000 type: 2
[    0.000000] copy_e820_map() start: 00000000fff00000 size: 0000000000100000 end: 0000000100000000 type: 2
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000001ffc0000 (usable)
[    0.000000]  BIOS-e820: 000000001ffc0000 - 000000001fff8000 (ACPI data)
[    0.000000]  BIOS-e820: 000000001fff8000 - 0000000020000000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000ffb80000 - 00000000ffc00000 (reserved)
[    0.000000]  BIOS-e820: 00000000fff00000 - 0000000100000000 (reserved)
[    0.000000] 0MB HIGHMEM available.
[    0.000000] 511MB LOWMEM available.
[    0.000000] Entering add_active_range(0, 0, 131008) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   131008
[    0.000000]   HighMem    131008 ->   131008
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   131008
[    0.000000] On node 0 totalpages: 131008
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 991 pages used for memmap
[    0.000000]   Normal zone: 125921 pages, LIFO batch:31
[    0.000000]   HighMem zone: 0 pages used for memmap
[    0.000000] DMI 2.3 present.
[    0.000000] ACPI: RSDP (v000 AMI                                   ) @ 0x000ff980
[    0.000000] ACPI: RSDT (v001 GATEWA EA81510A 0x20010423 MSFT 0x00001011) @ 0x1fff0000
[    0.000000] ACPI: FADT (v001 GATEWA EA81510A 0x20010423 MSFT 0x00001011) @ 0x1fff1000
[    0.000000] ACPI: BOOT (v001 GATEWA EA81510A 0x20010423 MSFT 0x00001011) @ 0x1fff4000
[    0.000000] ACPI: DSDT (v001 GATEWA N0CPP058 0x00000012 MSFT 0x0100000b) @ 0x00000000
[    0.000000] ACPI: PM-Timer IO Port: 0x408
[    0.000000] Allocating PCI resources starting at 30000000 (gap: 20000000:dfb80000)
[    0.000000] Detected 996.744 MHz processor.
[  306.694500] Built 1 zonelists.  Total pages: 129985
[  306.694505] Kernel command line: root=UUID=2b462b05-778e-4b63-818b-3fe3df6b1f61 ro quiet splash
[  306.694907] Local APIC disabled by BIOS -- you can enable it with "lapic"
[  306.694924] mapped APIC to ffffd000 (01402000)
[  306.694932] Enabling fast FPU save and restore... done.
[  306.694937] Enabling unmasked SIMD FPU exception support... done.
[  306.694955] Initializing CPU#0
[  306.695034] PID hash table entries: 2048 (order: 11, 8192 bytes)
[  306.696377] Console: colour VGA+ 80x25
[  306.697114] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
[  306.698117] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
[  306.739269] Memory: 507336k/524032k available (1917k kernel code, 16080k reserved, 867k data, 328k init, 0k highmem)
[  306.739292] virtual kernel memory layout:
[  306.739295]     fixmap  : 0xfffa9000 - 0xfffff000   ( 344 kB)
[  306.739298]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[  306.739301]     vmalloc : 0xe0800000 - 0xff7fe000   ( 495 MB)
[  306.739304]     lowmem  : 0xc0000000 - 0xdffc0000   ( 511 MB)
[  306.739307]       .init : 0xc03bc000 - 0xc040e000   ( 328 kB)
[  306.739310]       .data : 0xc02df4d8 - 0xc03b8434   ( 867 kB)
[  306.739313]       .text : 0xc0100000 - 0xc02df4d8   (1917 kB)
[  306.739320] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[  306.818996] Calibrating delay using timer specific routine.. 1994.82 BogoMIPS (lpj=3989643)
[  306.819060] Security Framework v1.0.0 initialized
[  306.819074] SELinux:  Disabled at boot.
[  306.819099] Mount-cache hash table entries: 512
[  306.819284] CPU: After generic identify, caps: 0383f9ff 00000000 00000000 00000000 00000000 00000000 00000000
[  306.819304] CPU: L1 I cache: 16K, L1 D cache: 16K
[  306.819309] CPU: L2 cache: 256K
[  306.819315] CPU: After all inits, caps: 0383f9ff 00000000 00000000 00000040 00000000 00000000 00000000
[  306.819332] Compat vDSO mapped to ffffe000.
[  306.819346] Remapping vsyscall page to ffffe000
[  306.819361] CPU: Intel Pentium III (Coppermine) stepping 06
[  306.819373] Checking 'hlt' instruction... OK.
[  306.835695] Early unpacking initramfs... done
[  307.603812] ACPI: Core revision 20060707
[  307.604767] ACPI: Looking for DSDT in initramfs... file /DSDT.aml not found, using machine DSDT.
[  307.607961] ACPI: setting ELCR to 0200 (from 0e08)
[  307.609408] Booting paravirtualized kernel on bare hardware
[  307.609516] Time: 20:42:25  Date: 09/29/107
[  307.609581] NET: Registered protocol family 16
[  307.609755] EISA bus registered
[  307.609764] ACPI: bus type pci registered
[  307.610319] PCI: PCI BIOS revision 2.10 entry at 0xfda95, last bus=2
[  307.610325] PCI: Using configuration type 1
[  307.610329] Setting up standard PCI resources
[  307.621357] ACPI: Interpreter enabled
[  307.621368] ACPI: Using PIC for interrupt routing
[  307.622205] ACPI: PCI Root Bridge [PCI0] (0000:00)
[  307.622221] PCI: Probing PCI hardware (bus 00)
[  307.623052] PCI quirk: region 0400-047f claimed by ICH4 ACPI/GPIO/TCO
[  307.623061] PCI quirk: region 0500-053f claimed by ICH4 GPIO
[  307.623346] Boot video device is 0000:01:00.0
[  307.623661] PCI: Transparent bridge - 0000:00:1e.0
[  307.623696] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[  307.625779] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCI1._PRT]
[  307.630231] ACPI: Power Resource [URP1] (off)
[  307.630354] ACPI: Power Resource [URP2] (off)
[  307.630478] ACPI: Power Resource [FDDP] (off)
[  307.630598] ACPI: Power Resource [LPTP] (off)
[  307.632206] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 9 10 *11 12)
[  307.632650] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 9 *10 11 12)
[  307.633091] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 9 10 11 12) *0, disabled.
[  307.633529] ACPI: PCI Interrupt Link [LNKD] (IRQs *3 4 5 6 7 9 10 11 12)
[  307.633977] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 9 10 11 12) *0, disabled.
[  307.634440] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 9 10 *11 12)
[  307.635347] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 9 10 *11 12)
[  307.635787] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 *9 10 11 12)
[  307.636000] Linux Plug and Play Support v0.97 (c) Adam Belay
[  307.636022] pnp: PnP ACPI init
[  307.642037] pnp: PnP ACPI: found 12 devices
[  307.642049] PnPBIOS: Disabled by ACPI PNP
[  307.642156] PCI: Using ACPI for IRQ routing
[  307.642164] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[  307.645692] NET: Registered protocol family 8
[  307.645697] NET: Registered protocol family 20
[  307.646992] PCI: Bridge: 0000:00:01.0
[  307.646999]   IO window: disabled.
[  307.647007]   MEM window: fc900000-fe9fffff
[  307.647014]   PREFETCH window: e4600000-f46fffff
[  307.647023] PCI: Bridge: 0000:00:1e.0
[  307.647028]   IO window: d000-dfff
[  307.647035]   MEM window: fea00000-feafffff
[  307.647042]   PREFETCH window: f4700000-f47fffff
[  307.647064] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[  307.647115] NET: Registered protocol family 2
[  307.686801] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
[  307.686962] TCP established hash table entries: 16384 (order: 4, 65536 bytes)
[  307.687134] TCP bind hash table entries: 8192 (order: 3, 32768 bytes)
[  307.687224] TCP: Hash tables configured (established 16384 bind 8192)
[  307.687230] TCP reno registered
[  307.699306] checking if image is initramfs... it is
[  309.152825] Freeing initrd memory: 8057k freed
[  309.153262] Simple Boot Flag at 0x7a set to 0x1
[  309.153619] audit: initializing netlink socket (disabled)
[  309.153649] audit(1193690546.640:1): initialized
[  309.153886] VFS: Disk quotas dquot_6.5.1
[  309.153928] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[  309.154447] io scheduler noop registered
[  309.154454] io scheduler anticipatory registered
[  309.154458] io scheduler deadline registered
[  309.154477] io scheduler cfq registered (default)
[  309.154980] isapnp: Scanning for PnP cards...
[  309.508671] isapnp: No Plug & Play device found
[  309.564700] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[  309.564876] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[  309.566324] 00:08: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[  309.566801] mice: PS/2 mouse device common for all mice
[  309.567838] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[  309.568343] input: Macintosh mouse button emulation as /class/input/input0
[  309.568411] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[  309.568420] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[  309.568781] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f03:PS2M] at 0x60,0x64 irq 1,12
[  309.572919] serio: i8042 KBD port at 0x60,0x64 irq 1
[  309.572934] serio: i8042 AUX port at 0x60,0x64 irq 12
[  309.573259] EISA: Probing bus 0 at eisa.0
[  309.573306] EISA: Detected 0 cards.
[  309.603469] TCP cubic registered
[  309.603484] NET: Registered protocol family 1
[  309.603527] Using IPI Shortcut mode
[  309.603646] ACPI: (supports S0 S1 S4 S5)
[  309.603731]   Magic number: 11:12:752
[  309.603738]   hash matches device ttyS3
[  309.604811] Freeing unused kernel memory: 328k freed
[  309.606042] Time: tsc clocksource has been installed.
[  309.618518] input: AT Translated Set 2 keyboard as /class/input/input1
[  311.133991] Capability LSM initialized
[  311.172097] device-mapper: ioctl: 4.11.0-ioctl (2006-10-12) initialised: [email]dm-devel@redhat.com[/email]
[  311.361716] md: linear personality registered for level -1
[  311.416589] md: multipath personality registered for level -4
[  311.424214] md: raid0 personality registered for level 0
[  311.433621] md: raid1 personality registered for level 1
[  311.440897] raid5: automatically using best checksumming function: pIII_sse
[  311.457406]    pIII_sse  :  1969.000 MB/sec
[  311.457411] raid5: using function: pIII_sse (1969.000 MB/sec)
[  311.529387] raid6: int32x1    305 MB/s
[  311.597421] raid6: int32x2    358 MB/s
[  311.665415] raid6: int32x4    289 MB/s
[  311.733334] raid6: int32x8    257 MB/s
[  311.801326] raid6: mmxx1      899 MB/s
[  311.869250] raid6: mmxx2     1130 MB/s
[  311.937276] raid6: sse1x1     792 MB/s
[  312.005210] raid6: sse1x2    1132 MB/s
[  312.005214] raid6: using algorithm sse1x2 (1132 MB/s)
[  312.005222] md: raid6 personality registered for level 6
[  312.005227] md: raid5 personality registered for level 5
[  312.005231] md: raid4 personality registered for level 4
[  312.081646] md: raid10 personality registered for level 10
[  313.011759] SCSI subsystem initialized
[  313.030418] libata version 2.20 loaded.
[  313.041356] ata_piix 0000:00:1f.1: version 2.10ac1
[  313.041404] PCI: Setting latency timer of device 0000:00:1f.1 to 64
[  313.041547] ata1: PATA max UDMA/100 cmd 0x000101f0 ctl 0x000103f6 bmdma 0x0001ffa0 irq 14
[  313.041600] ata2: PATA max UDMA/100 cmd 0x00010170 ctl 0x00010376 bmdma 0x0001ffa8 irq 15
[  313.041630] scsi0 : ata_piix
[  313.069117] usbcore: registered new interface driver usbfs
[  313.069179] usbcore: registered new interface driver hub
[  313.069221] usbcore: registered new device driver usb
[  313.072152] USB Universal Host Controller Interface driver v3.0
[  313.138489] 8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)
[  313.235034] ata1.00: ata_hpa_resize 1: sectors = 90069840, hpa_sectors = 90069840
[  313.235046] ata1.00: ATA-5: IBM-DTLA-307045, TX6GA50C, max UDMA/100
[  313.235052] ata1.00: 90069840 sectors, multi 16: LBA 
[  313.235309] ata1.01: ata_hpa_resize 1: sectors = 30015216, hpa_sectors = 30015216
[  313.235316] ata1.01: ATA-6: Maxtor 51023H2, JAC61HU0, max UDMA/100
[  313.235322] ata1.01: 30015216 sectors, multi 16: LBA 
[  313.251545] ata1.00: ata_hpa_resize 1: sectors = 90069840, hpa_sectors = 90069840
[  313.251557] ata1.00: configured for UDMA/100
[  313.257242] ata1.01: ata_hpa_resize 1: sectors = 30015216, hpa_sectors = 30015216
[  313.257251] ata1.01: configured for UDMA/100
[  313.257272] scsi1 : ata_piix
[  313.257404] ata2: port disabled. ignoring.
[  313.264829] scsi 0:0:0:0: Direct-Access     ATA      IBM-DTLA-307045  TX6G PQ: 0 ANSI: 5
[  313.272863] scsi 0:0:1:0: Direct-Access     ATA      Maxtor 51023H2   JAC6 PQ: 0 ANSI: 5
[  313.274025] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 3
[  313.274035] PCI: setting IRQ 3 as level-triggered
[  313.274041] ACPI: PCI Interrupt 0000:00:1f.2[D] -> Link [LNKD] -> GSI 3 (level, low) -> IRQ 3
[  313.274060] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[  313.274068] uhci_hcd 0000:00:1f.2: UHCI Host Controller
[  313.274290] uhci_hcd 0000:00:1f.2: new USB bus registered, assigned bus number 1
[  313.274327] uhci_hcd 0000:00:1f.2: irq 3, io base 0x0000ef40
[  313.274554] usb usb1: configuration #1 chosen from 1 choice
[  313.274619] hub 1-0:1.0: USB hub found
[  313.274636] hub 1-0:1.0: 2 ports detected
[  313.377444] ACPI: PCI Interrupt Link [LNKH] enabled at IRQ 9
[  313.377455] PCI: setting IRQ 9 as level-triggered
[  313.377460] ACPI: PCI Interrupt 0000:00:1f.4[C] -> Link [LNKH] -> GSI 9 (level, low) -> IRQ 9
[  313.377480] PCI: Setting latency timer of device 0000:00:1f.4 to 64
[  313.377486] uhci_hcd 0000:00:1f.4: UHCI Host Controller
[  313.377546] uhci_hcd 0000:00:1f.4: new USB bus registered, assigned bus number 2
[  313.377580] uhci_hcd 0000:00:1f.4: irq 9, io base 0x0000ef80
[  313.377771] usb usb2: configuration #1 chosen from 1 choice
[  313.377820] hub 2-0:1.0: USB hub found
[  313.377836] hub 2-0:1.0: 2 ports detected
[  313.447881] Floppy drive(s): fd0 is 1.44M
[  313.481331] FDC 0 is a post-1991 82077
[  313.481969] 8139cp 0000:02:0b.0: This (id 10ec:8139 rev 10) is not an 8139C+ compatible chip
[  313.481977] 8139cp 0000:02:0b.0: Try the "8139too" driver instead.
[  313.486845] 8139too Fast Ethernet driver 0.9.28
[  313.486929] ACPI: PCI Interrupt 0000:02:0b.0[A] -> Link [LNKH] -> GSI 9 (level, low) -> IRQ 9
[  313.487291] eth0: RealTek RTL8139 at 0xe0858c00, 00:14:6c:86:3c:34, IRQ 9
[  313.487297] eth0:  Identified 8139 chip type 'RTL-8100B/8139D'
[  313.538135] SCSI device sda: 90069840 512-byte hdwr sectors (46116 MB)
[  313.538166] sda: Write Protect is off
[  313.538172] sda: Mode Sense: 00 3a 00 00
[  313.538202] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[  313.538328] SCSI device sda: 90069840 512-byte hdwr sectors (46116 MB)
[  313.538346] sda: Write Protect is off
[  313.538351] sda: Mode Sense: 00 3a 00 00
[  313.538379] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[  313.538386]  sda: sda1 sda2 sda3 < sda5 sda6 >
[  313.619475] sd 0:0:0:0: Attached scsi disk sda
[  313.619757] SCSI device sdb: 30015216 512-byte hdwr sectors (15368 MB)
[  313.619781] sdb: Write Protect is off
[  313.619786] sdb: Mode Sense: 00 3a 00 00
[  313.619816] SCSI device sdb: write cache: disabled, read cache: enabled, doesn't support DPO or FUA
[  313.619901] SCSI device sdb: 30015216 512-byte hdwr sectors (15368 MB)
[  313.619919] sdb: Write Protect is off
[  313.619924] sdb: Mode Sense: 00 3a 00 00
[  313.619951] SCSI device sdb: write cache: disabled, read cache: enabled, doesn't support DPO or FUA
[  313.619959]  sdb: sdb1
[  313.626683] sd 0:0:1:0: Attached scsi disk sdb
[  313.641426] sd 0:0:0:0: Attached scsi generic sg0 type 0
[  313.641633] sd 0:0:1:0: Attached scsi generic sg1 type 0
[  314.111155] kjournald starting.  Commit interval 5 seconds
[  314.111178] EXT3-fs: mounted filesystem with ordered data mode.
[  320.594898] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[  321.898549] NET: Registered protocol family 17
[  323.309926] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[  323.340895] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[  323.367893] iTCO_vendor_support: vendor-support=0
[  323.370418] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.01 (11-Nov-2006)
[  323.370523] iTCO_wdt: Found a ICH2 TCO device (Version=1, TCOBASE=0x0460)
[  323.370571] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[  323.444070] intel_rng: Firmware space is locked read-only. If you can't or
[  323.444076] intel_rng: don't want to disable this in firmware setup, and if
[  323.444079] intel_rng: you are certain that your system has a functional
[  323.444083] intel_rng: RNG, try using the 'no_fwh_detect' option.
[  324.045777] Linux agpgart interface v0.102 (c) Dave Jones
[  324.094779] agpgart: Detected an Intel i815 Chipset.
[  324.098831] agpgart: AGP aperture is 64M @ 0xf8000000
[  324.381121] input: PC Speaker as /class/input/input2
[  325.140806] Real Time Clock Driver v1.12ac
[  325.216688] parport: PnPBIOS parport detected.
[  325.216744] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
[  325.318361] input: PS2++ Logitech Wheel Mouse as /class/input/input3
[  326.251164] ACPI: PCI Interrupt Link [LNKG] enabled at IRQ 11
[  326.251175] PCI: setting IRQ 11 as level-triggered
[  326.251181] ACPI: PCI Interrupt 0000:02:0a.0[A] -> Link [LNKG] -> GSI 11 (level, low) -> IRQ 11
[  327.350552] lp0: using parport0 (interrupt-driven).
[  327.420865] ndiswrapper version 1.38 loaded (preempt=no,smp=no)
[  327.480625] usbcore: registered new interface driver ndiswrapper
[  327.520812] ide0: I/O resource 0x3F6-0x3F6 not free.
[  327.520822] ide0: ports already in use, skipping probe
[  327.520828] ide1: I/O resource 0x376-0x376 not free.
[  327.520832] ide1: ports already in use, skipping probe
[  327.674249] EXT3 FS on sda1, internal journal
[  329.668015] kjournald starting.  Commit interval 5 seconds
[  329.668235] EXT3 FS on dm-3, internal journal
[  329.668245] EXT3-fs: mounted filesystem with ordered data mode.
[  329.691388] kjournald starting.  Commit interval 5 seconds
[  329.691609] EXT3 FS on dm-2, internal journal
[  329.691618] EXT3-fs: mounted filesystem with ordered data mode.
[  329.719528] kjournald starting.  Commit interval 5 seconds
[  329.719557] EXT3-fs warning: maximal mount count reached, running e2fsck is recommended
[  329.727143] EXT3 FS on sdb1, internal journal
[  329.727152] EXT3-fs: mounted filesystem with ordered data mode.
[  333.977894] NET: Registered protocol family 10
[  333.978082] lo: Disabled Privacy Extensions
[  339.171878] input: Power Button (FF) as /class/input/input4
[  339.172298] ACPI: Power Button (FF) [PWRF]
[  339.191897] input: Sleep Button (CM) as /class/input/input5
[  339.192342] ACPI: Sleep Button (CM) [SBTN]
[  339.354649] Using specific hotkey driver
[  339.409474] No dock devices found.
[  339.500182] ibm_acpi: ec object not found
[  339.731702] pcc_acpi: loading...
[  344.302036] eth0: no IPv6 routers present
[  353.270208] ppdev: user-space parallel port driver
[  353.872799] apm: BIOS version 1.2 Flags 0x0b (Driver version 1.16ac)
[  353.872808] apm: overridden by ACPI.
[  354.661420] ip_tables: (C) 2000-2006 Netfilter Core Team
[  355.017237] Netfilter messages via NETLINK v0.30.
[  355.242957] nf_conntrack version 0.5.0 (4094 buckets, 32752 max)
[  365.518694] eth0: no IPv6 routers present

---

### Post by geomantic8 on 2007-10-29
Oh, I completely failed to answer your question. No, I can't get it to boot from a CD. I inserted the live CD and rebooted but no go. Thanks,
-g8

---

### Post by geomantic8 on 2007-10-31
<Bump>
Sure, lots of stuff in the dmesg output, but no CD. Anyone? Running out of things to look for, I re-checked the cabling for connections. It's all secure, so not sure what's going on here...

Thanks hardware gurus,
-g8
 </bump>

---

### Post by theDaveTheRave on 2007-10-31
Hi there.

I recall having a similar issue with my 2 HDD and 2 CD drives when I amalgamated an old machine with a new one!

Have you tried daisy chaining the CD/VD to the primary HDD and then connecting the second HDD separately... I seem to recall that is what I ended up doing and then everything suddenly jumped into life!

Which was to say the least a relief!

Dave

---

### Post by geomantic8 on 2007-10-31
No, haven't tried your suggestion...yet. But at this point desperation is setting in and I'm almost to the point where I'll do anything to get it to work. 

I suppose I could do w/out the CD, but it sure does limit the usefulness of the machine...

Thanks for your suggestion.

---

