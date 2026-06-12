---
title: "New CD drive not working"
date: 2007-09-08
forum: Hardware &amp; Laptops
---

### Post by geomantic8 on 2007-09-08
Hi ubutu-gurus,

How do I get my BIOS to check for, and mount my CD-ROM on boot? Here's the story...

I just installed a new CD drive as the old one was failing. Because the other one was failing, it would take *forever* to boot so when I was offered the option of hitting <ENTER> to continue or <ESC> to never see the message again, I hit an <ESC>.   I think my problem is that when I hit <ESC> I told the BIOS not to check for CD on boot.  

FWIW, the CD drive shows up in Nautilus, and it's listed in /etc/fstab. But when I try to mount I get the error, "special device /dev/hdc does not exist". Furthermore, when I list /dev/s*, only my two internal and one external drives are listed. 

Any suggestions? Thanks in advance.

-g8

---

### Post by geraldm on 2007-09-08
The dialog <ENTER> or <ESC> probably came from a loading program.  This should not
make any changes to the BIOS.  Certainly this should have been a big WARNING in the
dialog that it would try to change a BIOS setting.  The dialog choice affected any 
subsequent loading, 

The hardware discovered is in file /var/log/dmesg and you can look at it with a text editor
or enter the command dmesg

If you do not know how to proceed after looking at that file, then post dmesg.

Gerald

---

### Post by geomantic8 on 2007-09-09
Thanks for the reply. Output from dmesg posted below. Curiously, dmesg | grep CD returns nothing. Argh. Again, any insight greatly appreciated.

-g8
________________________

[    0.000000] Linux version 2.6.20-16-386 (root@terranova) (gcc version 4.1.2 (Ubuntu 4.1.2-0ubuntu4)) #2 Fri Aug 31 00:51:58 UTC 2007 (Ubuntu 2.6.20-16.31-386)
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
[    0.000000] Detected 996.751 MHz processor.
[   15.675801] Built 1 zonelists.  Total pages: 129985
[   15.675807] Kernel command line: root=UUID=2b462b05-778e-4b63-818b-3fe3df6b1f61 ro quiet splash
[   15.676212] Local APIC disabled by BIOS -- you can enable it with "lapic"
[   15.676229] mapped APIC to ffffd000 (01402000)
[   15.676237] Enabling fast FPU save and restore... done.
[   15.676242] Enabling unmasked SIMD FPU exception support... done.
[   15.676260] Initializing CPU#0
[   15.676340] PID hash table entries: 2048 (order: 11, 8192 bytes)
[   15.677692] Console: colour VGA+ 80x25
[   15.678421] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
[   15.679424] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
[   15.720623] Memory: 507336k/524032k available (1917k kernel code, 16080k reserved, 867k data, 328k init, 0k highmem)
[   15.720645] virtual kernel memory layout:
[   15.720648]     fixmap  : 0xfffa9000 - 0xfffff000   ( 344 kB)
[   15.720651]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   15.720654]     vmalloc : 0xe0800000 - 0xff7fe000   ( 495 MB)
[   15.720657]     lowmem  : 0xc0000000 - 0xdffc0000   ( 511 MB)
[   15.720660]       .init : 0xc03bc000 - 0xc040e000   ( 328 kB)
[   15.720663]       .data : 0xc02df4e3 - 0xc03b8434   ( 867 kB)
[   15.720666]       .text : 0xc0100000 - 0xc02df4e3   (1917 kB)
[   15.720673] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   15.800300] Calibrating delay using timer specific routine.. 1994.76 BogoMIPS (lpj=3989522)
[   15.800364] Security Framework v1.0.0 initialized
[   15.800378] SELinux:  Disabled at boot.
[   15.800404] Mount-cache hash table entries: 512
[   15.800589] CPU: After generic identify, caps: 0383f9ff 00000000 00000000 00000000 00000000 00000000 00000000
[   15.800608] CPU: L1 I cache: 16K, L1 D cache: 16K
[   15.800613] CPU: L2 cache: 256K
[   15.800619] CPU: After all inits, caps: 0383f9ff 00000000 00000000 00000040 00000000 00000000 00000000
[   15.800636] Compat vDSO mapped to ffffe000.
[   15.800650] Remapping vsyscall page to ffffe000
[   15.800666] CPU: Intel Pentium III (Coppermine) stepping 06
[   15.800677] Checking 'hlt' instruction... OK.
[   15.816999] Early unpacking initramfs... done
[   16.575918] ACPI: Core revision 20060707
[   16.576910] ACPI: Looking for DSDT in initramfs... file /DSDT.aml not found, using machine DSDT.
[   16.580104] ACPI: setting ELCR to 0200 (from 0e08)
[   16.581552] Booting paravirtualized kernel on bare hardware
[   16.581660] Time: 20:12:57  Date: 08/07/107
[   16.581722] NET: Registered protocol family 16
[   16.581897] EISA bus registered
[   16.581906] ACPI: bus type pci registered
[   16.582458] PCI: PCI BIOS revision 2.10 entry at 0xfda95, last bus=2
[   16.582463] PCI: Using configuration type 1
[   16.582467] Setting up standard PCI resources
[   16.593606] ACPI: Interpreter enabled
[   16.593618] ACPI: Using PIC for interrupt routing
[   16.594437] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   16.594453] PCI: Probing PCI hardware (bus 00)
[   16.595252] PCI quirk: region 0400-047f claimed by ICH4 ACPI/GPIO/TCO
[   16.595260] PCI quirk: region 0500-053f claimed by ICH4 GPIO
[   16.595548] Boot video device is 0000:01:00.0
[   16.595861] PCI: Transparent bridge - 0000:00:1e.0
[   16.595893] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   16.597994] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCI1._PRT]
[   16.602804] ACPI: Power Resource [URP1] (off)
[   16.602933] ACPI: Power Resource [URP2] (off)
[   16.603060] ACPI: Power Resource [FDDP] (off)
[   16.603182] ACPI: Power Resource [LPTP] (off)
[   16.604799] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 9 10 *11 12)
[   16.605246] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 9 *10 11 12)
[   16.605696] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 9 10 11 12) *0, disabled.
[   16.606138] ACPI: PCI Interrupt Link [LNKD] (IRQs *3 4 5 6 7 9 10 11 12)
[   16.606585] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 9 10 11 12) *0, disabled.
[   16.607044] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 9 10 *11 12)
[   16.607485] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 9 10 *11 12)
[   16.607927] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 *9 10 11 12)
[   16.608176] Linux Plug and Play Support v0.97 (c) Adam Belay
[   16.608198] pnp: PnP ACPI init
[   16.614278] pnp: PnP ACPI: found 12 devices
[   16.614291] PnPBIOS: Disabled by ACPI PNP
[   16.614396] PCI: Using ACPI for IRQ routing
[   16.614404] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   16.618382] NET: Registered protocol family 8
[   16.618387] NET: Registered protocol family 20
[   16.619649] PCI: Bridge: 0000:00:01.0
[   16.619656]   IO window: disabled.
[   16.619664]   MEM window: fc900000-fe9fffff
[   16.619670]   PREFETCH window: e4600000-f46fffff
[   16.619680] PCI: Bridge: 0000:00:1e.0
[   16.619685]   IO window: d000-dfff
[   16.619692]   MEM window: fea00000-feafffff
[   16.619699]   PREFETCH window: f4700000-f47fffff
[   16.619721] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[   16.619770] NET: Registered protocol family 2
[   16.656109] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
[   16.656267] TCP established hash table entries: 16384 (order: 4, 65536 bytes)
[   16.656438] TCP bind hash table entries: 8192 (order: 3, 32768 bytes)
[   16.656526] TCP: Hash tables configured (established 16384 bind 8192)
[   16.656532] TCP reno registered
[   16.668246] checking if image is initramfs... it is
[   18.121964] Freeing initrd memory: 8057k freed
[   18.122403] Simple Boot Flag at 0x7a set to 0x1
[   18.122763] audit: initializing netlink socket (disabled)
[   18.122792] audit(1189195978.632:1): initialized
[   18.123030] VFS: Disk quotas dquot_6.5.1
[   18.123072] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   18.123174] io scheduler noop registered
[   18.123180] io scheduler anticipatory registered
[   18.123185] io scheduler deadline registered
[   18.123203] io scheduler cfq registered (default)
[   18.123738] isapnp: Scanning for PnP cards...
[   18.477436] isapnp: No Plug & Play device found
[   18.535464] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   18.535644] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   18.537017] 00:08: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   18.537483] mice: PS/2 mouse device common for all mice
[   18.538537] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   18.539039] input: Macintosh mouse button emulation as /class/input/input0
[   18.539107] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[   18.539116] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[   18.539579] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f03:PS2M] at 0x60,0x64 irq 1,12
[   18.543639] serio: i8042 KBD port at 0x60,0x64 irq 1
[   18.543654] serio: i8042 AUX port at 0x60,0x64 irq 12
[   18.543980] EISA: Probing bus 0 at eisa.0
[   18.544027] EISA: Detected 0 cards.
[   18.574191] TCP cubic registered
[   18.574206] NET: Registered protocol family 1
[   18.574247] Using IPI Shortcut mode
[   18.574365] ACPI: (supports S0 S1 S4 S5)
[   18.574449]   Magic number: 7:832:244
[   18.574499]   hash matches device ttyw0
[   18.575357] Time: tsc clocksource has been installed.
[   18.575552] Freeing unused kernel memory: 328k freed
[   18.589034] input: AT Translated Set 2 keyboard as /class/input/input1
[   20.103308] Capability LSM initialized
[   20.141327] device-mapper: ioctl: 4.11.0-ioctl (2006-10-12) initialised: [email]dm-devel@redhat.com[/email]
[   20.331816] md: linear personality registered for level -1
[   20.386420] md: multipath personality registered for level -4
[   20.394065] md: raid0 personality registered for level 0
[   20.403440] md: raid1 personality registered for level 1
[   20.410698] raid5: automatically using best checksumming function: pIII_sse
[   20.430700]    pIII_sse  :  1969.000 MB/sec
[   20.430705] raid5: using function: pIII_sse (1969.000 MB/sec)
[   20.502697] raid6: int32x1    305 MB/s
[   20.570728] raid6: int32x2    358 MB/s
[   20.638721] raid6: int32x4    289 MB/s
[   20.706642] raid6: int32x8    257 MB/s
[   20.774633] raid6: mmxx1      899 MB/s
[   20.842557] raid6: mmxx2     1130 MB/s
[   20.910581] raid6: sse1x1     792 MB/s
[   20.978518] raid6: sse1x2    1132 MB/s
[   20.978522] raid6: using algorithm sse1x2 (1132 MB/s)
[   20.978530] md: raid6 personality registered for level 6
[   20.978534] md: raid5 personality registered for level 5
[   20.978538] md: raid4 personality registered for level 4
[   21.053478] md: raid10 personality registered for level 10
[   21.971986] SCSI subsystem initialized
[   21.990625] libata version 2.20 loaded.
[   22.001529] ata_piix 0000:00:1f.1: version 2.10ac1
[   22.001577] PCI: Setting latency timer of device 0000:00:1f.1 to 64
[   22.001721] ata1: PATA max UDMA/100 cmd 0x000101f0 ctl 0x000103f6 bmdma 0x0001ffa0 irq 14
[   22.001770] ata2: PATA max UDMA/100 cmd 0x00010170 ctl 0x00010376 bmdma 0x0001ffa8 irq 15
[   22.001799] scsi0 : ata_piix
[   22.055699] 8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)
[   22.117204] usbcore: registered new interface driver usbfs
[   22.117253] usbcore: registered new interface driver hub
[   22.117298] usbcore: registered new device driver usb
[   22.120267] USB Universal Host Controller Interface driver v3.0
[   22.189938] ata1.00: ata_hpa_resize 1: sectors = 90069840, hpa_sectors = 90069840
[   22.189950] ata1.00: ATA-5: IBM-DTLA-307045, TX6GA50C, max UDMA/100
[   22.189956] ata1.00: 90069840 sectors, multi 16: LBA 
[   22.190200] ata1.01: ata_hpa_resize 1: sectors = 30015216, hpa_sectors = 30015216
[   22.190206] ata1.01: ATA-6: Maxtor 51023H2, JAC61HU0, max UDMA/100
[   22.190212] ata1.01: 30015216 sectors, multi 16: LBA 
[   22.206477] ata1.00: ata_hpa_resize 1: sectors = 90069840, hpa_sectors = 90069840
[   22.206491] ata1.00: configured for UDMA/100
[   22.214544] ata1.01: ata_hpa_resize 1: sectors = 30015216, hpa_sectors = 30015216
[   22.214554] ata1.01: configured for UDMA/100
[   22.214575] scsi1 : ata_piix
[   22.214712] ata2: port disabled. ignoring.
[   22.222197] scsi 0:0:0:0: Direct-Access     ATA      IBM-DTLA-307045  TX6G PQ: 0 ANSI: 5
[   22.230160] scsi 0:0:1:0: Direct-Access     ATA      Maxtor 51023H2   JAC6 PQ: 0 ANSI: 5
[   22.230946] 8139cp 0000:02:0b.0: This (id 10ec:8139 rev 10) is not an 8139C+ compatible chip
[   22.230953] 8139cp 0000:02:0b.0: Try the "8139too" driver instead.
[   22.235719] 8139too Fast Ethernet driver 0.9.28
[   22.236179] ACPI: PCI Interrupt Link [LNKH] enabled at IRQ 9
[   22.236186] PCI: setting IRQ 9 as level-triggered
[   22.236191] ACPI: PCI Interrupt 0000:02:0b.0[A] -> Link [LNKH] -> GSI 9 (level, low) -> IRQ 9
[   22.236552] eth0: RealTek RTL8139 at 0xe0872c00, 00:14:6c:86:3c:34, IRQ 9
[   22.236558] eth0:  Identified 8139 chip type 'RTL-8100B/8139D'
[   22.237028] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 3
[   22.237035] PCI: setting IRQ 3 as level-triggered
[   22.237040] ACPI: PCI Interrupt 0000:00:1f.2[D] -> Link [LNKD] -> GSI 3 (level, low) -> IRQ 3
[   22.237055] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[   22.237061] uhci_hcd 0000:00:1f.2: UHCI Host Controller
[   22.237285] uhci_hcd 0000:00:1f.2: new USB bus registered, assigned bus number 1
[   22.237322] uhci_hcd 0000:00:1f.2: irq 3, io base 0x0000ef40
[   22.237541] usb usb1: configuration #1 chosen from 1 choice
[   22.237591] hub 1-0:1.0: USB hub found
[   22.237613] hub 1-0:1.0: 2 ports detected
[   22.319213] Floppy drive(s): fd0 is 1.44M
[   22.338307] ACPI: PCI Interrupt 0000:00:1f.4[C] -> Link [LNKH] -> GSI 9 (level, low) -> IRQ 9
[   22.338331] PCI: Setting latency timer of device 0000:00:1f.4 to 64
[   22.338338] uhci_hcd 0000:00:1f.4: UHCI Host Controller
[   22.338385] uhci_hcd 0000:00:1f.4: new USB bus registered, assigned bus number 2
[   22.338418] uhci_hcd 0000:00:1f.4: irq 9, io base 0x0000ef80
[   22.338609] usb usb2: configuration #1 chosen from 1 choice
[   22.338658] hub 2-0:1.0: USB hub found
[   22.338674] hub 2-0:1.0: 2 ports detected
[   22.416348] FDC 0 is a post-1991 82077
[   22.483296] SCSI device sda: 90069840 512-byte hdwr sectors (46116 MB)
[   22.483325] sda: Write Protect is off
[   22.483331] sda: Mode Sense: 00 3a 00 00
[   22.483360] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   22.483485] SCSI device sda: 90069840 512-byte hdwr sectors (46116 MB)
[   22.483503] sda: Write Protect is off
[   22.483508] sda: Mode Sense: 00 3a 00 00
[   22.483535] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   22.483543]  sda: sda1 sda2 sda3 < sda5 sda6 >
[   22.582614] sd 0:0:0:0: Attached scsi disk sda
[   22.582890] SCSI device sdb: 30015216 512-byte hdwr sectors (15368 MB)
[   22.582915] sdb: Write Protect is off
[   22.582920] sdb: Mode Sense: 00 3a 00 00
[   22.582950] SCSI device sdb: write cache: disabled, read cache: enabled, doesn't support DPO or FUA
[   22.583034] SCSI device sdb: 30015216 512-byte hdwr sectors (15368 MB)
[   22.583051] sdb: Write Protect is off
[   22.583056] sdb: Mode Sense: 00 3a 00 00
[   22.583084] SCSI device sdb: write cache: disabled, read cache: enabled, doesn't support DPO or FUA
[   22.583091]  sdb: sdb1
[   22.587691] sd 0:0:1:0: Attached scsi disk sdb
[   22.597999] sd 0:0:0:0: Attached scsi generic sg0 type 0
[   22.598212] sd 0:0:1:0: Attached scsi generic sg1 type 0
[   23.008044] kjournald starting.  Commit interval 5 seconds
[   23.008067] EXT3-fs: mounted filesystem with ordered data mode.
[   29.430756] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[   31.072800] NET: Registered protocol family 17
[   31.827193] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   31.831329] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   32.117520] iTCO_vendor_support: vendor-support=0
[   32.120119] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.01 (11-Nov-2006)
[   32.120225] iTCO_wdt: Found a ICH2 TCO device (Version=1, TCOBASE=0x0460)
[   32.120273] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   32.180193] intel_rng: Firmware space is locked read-only. If you can't or
[   32.180199] intel_rng: don't want to disable this in firmware setup, and if
[   32.180202] intel_rng: you are certain that your system has a functional
[   32.180205] intel_rng: RNG, try using the 'no_fwh_detect' option.
[   32.796942] Linux agpgart interface v0.102 (c) Dave Jones
[   33.619005] Real Time Clock Driver v1.12ac
[   33.664367] agpgart: Detected an Intel i815 Chipset.
[   33.668429] agpgart: AGP aperture is 64M @ 0xf8000000
[   33.747051] parport: PnPBIOS parport detected.
[   33.747106] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
[   33.770244] input: PC Speaker as /class/input/input2
[   34.176128] input: PS2++ Logitech Wheel Mouse as /class/input/input3
[   35.365246] ACPI: PCI Interrupt Link [LNKG] enabled at IRQ 11
[   35.365256] PCI: setting IRQ 11 as level-triggered
[   35.365262] ACPI: PCI Interrupt 0000:02:0a.0[A] -> Link [LNKG] -> GSI 11 (level, low) -> IRQ 11
[   36.466477] lp0: using parport0 (interrupt-driven).
[   36.550030] ndiswrapper version 1.38 loaded (preempt=no,smp=no)
[   36.607320] usbcore: registered new interface driver ndiswrapper
[   36.642048] ide0: I/O resource 0x3F6-0x3F6 not free.
[   36.642057] ide0: ports already in use, skipping probe
[   36.642063] ide1: I/O resource 0x376-0x376 not free.
[   36.642067] ide1: ports already in use, skipping probe
[   36.775011] EXT3 FS on sda1, internal journal
[   38.959916] kjournald starting.  Commit interval 5 seconds
[   38.960140] EXT3 FS on dm-3, internal journal
[   38.960150] EXT3-fs: mounted filesystem with ordered data mode.
[   38.981549] kjournald starting.  Commit interval 5 seconds
[   38.981756] EXT3 FS on dm-2, internal journal
[   38.981765] EXT3-fs: mounted filesystem with ordered data mode.
[   39.381405] kjournald starting.  Commit interval 5 seconds
[   39.396162] EXT3 FS on sdb1, internal journal
[   39.396173] EXT3-fs: mounted filesystem with ordered data mode.

---

### Post by geomantic8 on 2007-09-13
Bump, bump, nudge, nudge. More info: when I try to mount the CD-rom from Nautilus I get a '/dev/sdc/ does not exist'.

Hope someone can help. Thanks,
-g8

---

