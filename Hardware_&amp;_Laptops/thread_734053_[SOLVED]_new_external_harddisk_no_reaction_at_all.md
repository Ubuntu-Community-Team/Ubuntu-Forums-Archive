---
title: "[SOLVED] new external harddisk no reaction at all"
date: 2008-03-24
forum: Hardware &amp; Laptops
---

### Post by Ampi on 2008-03-24
I just bought a new external harddisk (sata) for my computer and tried it both in my old (and for sure working) USB 1.1 and in my new (might not work) USB 2.0. 
In both cases I get a green light on my harddisk but nothing on my screen seems to detect it.

Before 'breaking' it by trying different stuff I just want to be sure I don't miss anything important. 
I have no idea about the disk itself, meaning format or anything like that. 

It does seem to be a problem with the partition table as you can see in my fdisk output. 

Is there a general way of using external harddisks that I just don't know or should I do something special?

Thanks for helping...


[HTML]$ sudo fdisk -l
Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

Disk /dev/sda doesn't contain a valid partition table[/HTML]

---

### Post by chewearn on 2008-03-25
I think the disk is simply not partitioned (since it's new).  After you plug in the HD, check output of dmesg command for any error message from the kernel.

---

### Post by Ampi on 2008-03-25
Okay, something definitely goes wrong and I am not that experienced with linux....

any idea?


```

$ dmesg
[    0.000000] Linux version 2.6.22-14-generic (buildd@terranova) (gcc version 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)) #1 SMP Tue Feb 12 07:42:25 UTC 2008 (Ubuntu 2.6.22-14.52-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000000fff0000 (usable)
[    0.000000]  BIOS-e820: 000000000fff0000 - 000000000fff8000 (ACPI data)
[    0.000000]  BIOS-e820: 000000000fff8000 - 0000000010000000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fff80000 - 0000000100000000 (reserved)
[    0.000000] 0MB HIGHMEM available.
[    0.000000] 255MB LOWMEM available.
[    0.000000] found SMP MP-table at 000fb880
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
[    0.000000] ACPI: RSDP signature @ 0xC00FA610 checksum 0
[    0.000000] ACPI: RSDP 000FA610, 0014 (r0 AMI   )
[    0.000000] ACPI: RSDT 0FFF0000, 002C (r1 AMIINT VIA_K7         10 MSFT       97)
[    0.000000] ACPI: FACP 0FFF0030, 0081 (r1 AMIINT VIA_K7         11 MSFT       97)
[    0.000000] ACPI: DSDT 0FFF0120, 319A (r1    VIA   VIA_K7     1000 MSFT  100000D)
[    0.000000] ACPI: FACS 0FFF8000, 0040
[    0.000000] ACPI: APIC 0FFF00C0, 0054 (r1 AMIINT VIA_K7          9 MSFT       97)
[    0.000000] ACPI: PM-Timer IO Port: 0x808
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] Processor #0 6:6 APIC version 16
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 17, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 low level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] Allocating PCI resources starting at 20000000 (gap: 10000000:eec00000)
[    0.000000] Built 1 zonelists.  Total pages: 65009
[    0.000000] Kernel command line: root=UUID=2596ce7d-0a93-4975-a56c-14b9bf57272e ro quiet splash
[    0.000000] mapped APIC to ffffd000 (fee00000)
[    0.000000] mapped IOAPIC to ffffc000 (fec00000)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 1024 (order: 10, 4096 bytes)
[    0.000000] Detected 1150.037 MHz processor.
[   17.993652] Console: colour VGA+ 80x25
[   17.993988] Dentry cache hash table entries: 32768 (order: 5, 131072 bytes)
[   17.994206] Inode-cache hash table entries: 16384 (order: 4, 65536 bytes)
[   18.006568] Memory: 247820k/262080k available (2015k kernel code, 13728k reserved, 915k data, 364k init, 0k highmem)
[   18.006586] virtual kernel memory layout:
[   18.006588]     fixmap  : 0xfff4d000 - 0xfffff000   ( 712 kB)
[   18.006591]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   18.006593]     vmalloc : 0xd0800000 - 0xff7fe000   ( 751 MB)
[   18.006595]     lowmem  : 0xc0000000 - 0xcfff0000   ( 255 MB)
[   18.006597]       .init : 0xc03e3000 - 0xc043e000   ( 364 kB)
[   18.006599]       .data : 0xc02f7e86 - 0xc03dce84   ( 915 kB)
[   18.006602]       .text : 0xc0100000 - 0xc02f7e86   (2015 kB)
[   18.006607] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   18.006682] SLUB: Genslabs=22, HWalign=32, Order=0-1, MinObjects=4, CPUs=1, Nodes=1
[   18.086680] Calibrating delay using timer specific routine.. 2302.49 BogoMIPS (lpj=4604990)
[   18.086733] Security Framework v1.0.0 initialized
[   18.086746] SELinux:  Disabled at boot.
[   18.086773] Mount-cache hash table entries: 512
[   18.087013] CPU: After generic identify, caps: 0383fbff c1cbfbff 00000000 00000000 00000000 00000000 00000000
[   18.087030] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[   18.087035] CPU: L2 Cache: 256K (64 bytes/line)
[   18.087040] CPU: After all inits, caps: 0383fbff c1cbfbff 00000000 00000420 00000000 00000000 00000000
[   18.087059] Compat vDSO mapped to ffffe000.
[   18.087080] Checking 'hlt' instruction... OK.
[   18.102897] SMP alternatives: switching to UP code
[   18.103314] Freeing SMP alternatives: 11k freed
[   18.103919] Early unpacking initramfs... done
[   18.679076] ACPI: Core revision 20070126
[   18.679221] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[   18.681911] CPU0: AMD Athlon(tm) Processor stepping 02
[   18.681949] Total of 1 processors activated (2302.49 BogoMIPS).
[   18.682730] ENABLING IO-APIC IRQs
[   18.683055] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[   18.830472] Brought up 1 CPUs
[   18.830736] Booting paravirtualized kernel on bare hardware
[   18.830840] Time: 17:07:29  Date: 02/25/108
[   18.830890] NET: Registered protocol family 16
[   18.831070] EISA bus registered
[   18.831091] ACPI: bus type pci registered
[   18.832785] PCI: PCI BIOS revision 2.10 entry at 0xfdb21, last bus=1
[   18.832790] PCI: Using configuration type 1
[   18.832793] Setting up standard PCI resources
[   18.838058] ACPI: EC: Look up EC in DSDT
[   18.843664] ACPI: Interpreter enabled
[   18.843670] ACPI: (supports S0 S1 S4 S5)
[   18.843696] ACPI: Using IOAPIC for interrupt routing
[   18.850631] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   18.850655] PCI: Probing PCI hardware (bus 00)
[   18.851379] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   18.866313] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 10 *11 12 14 15)
[   18.866493] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[   18.866641] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 *5 6 7 10 11 12 14 15)
[   18.866784] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 *10 11 12 14 15)
[   18.866959] ACPI: Power Resource [URP1] (off)
[   18.867006] ACPI: Power Resource [URP2] (off)
[   18.867051] ACPI: Power Resource [FDDP] (off)
[   18.867096] ACPI: Power Resource [LPTP] (off)
[   18.867116] Linux Plug and Play Support v0.97 (c) Adam Belay
[   18.867137] pnp: PnP ACPI init
[   18.867154] ACPI: bus type pnp registered
[   18.871406] pnp: PnP ACPI: found 12 devices
[   18.871411] ACPI: ACPI bus type pnp unregistered
[   18.871419] PnPBIOS: Disabled by ACPI PNP
[   18.871519] PCI: Using ACPI for IRQ routing
[   18.871524] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   18.873317] NET: Registered protocol family 8
[   18.873321] NET: Registered protocol family 20
[   18.874380] Time: tsc clocksource has been installed.
[   18.903966] PCI: Bridge: 0000:00:01.0
[   18.903969]   IO window: disabled.
[   18.903976]   MEM window: dde00000-dfefffff
[   18.903982]   PREFETCH window: cdc00000-ddcfffff
[   18.904007] PCI: Setting latency timer of device 0000:00:01.0 to 64
[   18.904026] NET: Registered protocol family 2
[   18.934438] IP route cache hash table entries: 2048 (order: 1, 8192 bytes)
[   18.934525] TCP established hash table entries: 8192 (order: 4, 98304 bytes)
[   18.934773] TCP bind hash table entries: 8192 (order: 4, 65536 bytes)
[   18.934942] TCP: Hash tables configured (established 8192 bind 8192)
[   18.934948] TCP reno registered
[   18.946570] checking if image is initramfs...<6>Switched to high resolution mode on CPU 0
[   19.446505]  it is
[   20.041905] Freeing initrd memory: 7601k freed
[   20.042692] audit: initializing netlink socket (disabled)
[   20.042718] audit(1206464849.764:1): initialized
[   20.046038] VFS: Disk quotas dquot_6.5.1
[   20.046139] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   20.046338] io scheduler noop registered
[   20.046342] io scheduler anticipatory registered
[   20.046346] io scheduler deadline registered
[   20.046370] io scheduler cfq registered (default)
[   20.046391] PCI: VIA PCI bridge detected. Disabling DAC.
[   20.046448] Boot video device is 0000:01:00.0
[   20.046713] isapnp: Scanning for PnP cards...
[   20.400401] isapnp: No Plug & Play device found
[   20.452315] Real Time Clock Driver v1.12ac
[   20.452481] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   20.452593] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   20.452955] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[   20.454060] 00:02: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   20.454609] 00:03: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[   20.456010] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   20.456401] input: Macintosh mouse button emulation as /class/input/input0
[   20.456543] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[   20.459546] serio: i8042 KBD port at 0x60,0x64 irq 1
[   20.459560] serio: i8042 AUX port at 0x60,0x64 irq 12
[   20.459923] mice: PS/2 mouse device common for all mice
[   20.460133] EISA: Probing bus 0 at eisa.0
[   20.460183] EISA: Detected 0 cards.
[   20.460360] TCP cubic registered
[   20.460376] NET: Registered protocol family 1
[   20.460412] Using IPI No-Shortcut mode
[   20.460667]   Magic number: 0:727:138
[   20.461756] Freeing unused kernel memory: 364k freed
[   20.497652] input: AT Translated Set 2 keyboard as /class/input/input1
[   21.833772] AppArmor: AppArmor initialized<5>audit(1206464851.264:2):  type=1505 info="AppArmor initialized" pid=1174
[   21.845166] fuse init (API version 7.8)
[   21.853711] Failure registering capabilities with primary security module.
[   21.878030] ACPI: Processor [CPU1] (supports 16 throttling states)
[   21.904401] device-mapper: ioctl: 4.11.0-ioctl (2006-10-12) initialised: dm-devel@redhat.com
[   22.912225] 8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)
[   22.912276] 8139cp 0000:00:08.0: This (id 10ec:8139 rev 10) is not an 8139C+ compatible chip
[   22.912283] 8139cp 0000:00:08.0: Try the "8139too" driver instead.
[   22.914556] 8139too Fast Ethernet driver 0.9.28
[   22.914641] ACPI: PCI Interrupt 0000:00:08.0[A] -> GSI 19 (level, low) -> IRQ 16
[   22.915057] eth0: RealTek RTL8139 at 0xd084cf00, 00:50:bf:61:94:72, IRQ 16
[   22.915061] eth0:  Identified 8139 chip type 'RTL-8139C'
[   22.955559] SCSI subsystem initialized
[   22.964369] libata version 2.21 loaded.
[   22.974101] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[   22.974114] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[   22.975315] VP_IDE: IDE controller at PCI slot 0000:00:11.1
[   22.975356] VP_IDE: chipset revision 6
[   22.975360] VP_IDE: not 100% native mode: will probe irqs later
[   22.975378] VP_IDE: VIA vt8233 (rev 00) IDE UDMA100 controller on pci0000:00:11.1
[   22.975391]     ide0: BM-DMA at 0xfc00-0xfc07, BIOS settings: hda:DMA, hdb:DMA
[   22.975410]     ide1: BM-DMA at 0xfc08-0xfc0f, BIOS settings: hdc:pio, hdd:DMA
[   22.975422] Probing IDE interface ide0...
[   23.022168] usbcore: registered new interface driver usbfs
[   23.022219] usbcore: registered new interface driver hub
[   23.022263] usbcore: registered new device driver usb
[   23.023884] USB Universal Host Controller Interface driver v3.0
[   23.223143] Floppy drive(s): fd0 is 1.44M
[   23.287829] FDC 0 is a post-1991 82077
[   23.420150] hda: Maxtor 6E040L0, ATA DISK drive
[   23.700002] hdb: MAXTOR 6L040J2, ATA DISK drive
[   23.756443] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[   23.764326] Probing IDE interface ide1...
[   24.907380] hdd: BENQ DVD DD DW1640, ATAPI CD/DVD-ROM drive
[   24.964104] ide1 at 0x170-0x177,0x376 on irq 15
[   24.966328] ACPI: PCI Interrupt 0000:00:11.2[D] -> GSI 10 (level, low) -> IRQ 10
[   24.966353] uhci_hcd 0000:00:11.2: UHCI Host Controller
[   24.966905] uhci_hcd 0000:00:11.2: new USB bus registered, assigned bus number 1
[   24.966955] uhci_hcd 0000:00:11.2: irq 10, io base 0x0000dc00
[   24.967752] usb usb1: configuration #1 chosen from 1 choice
[   24.967993] hub 1-0:1.0: USB hub found
[   24.968009] hub 1-0:1.0: 2 ports detected
[   24.979822] hda: max request size: 128KiB
[   25.002793] hda: 80293248 sectors (41110 MB) w/2048KiB Cache, CHS=65535/16/63, UDMA(100)
[   25.005682] hda: cache flushes supported
[   25.005776]  hda: hda1 hda2
[   25.012676] hdb: max request size: 128KiB
[   25.012830] hdb: 78177792 sectors (40027 MB) w/1819KiB Cache, CHS=65535/16/63, UDMA(100)
[   25.013002] hdb: cache flushes supported
[   25.013039]  hdb: hdb1 hdb2 < hdb5 >
[   25.071487] ACPI: PCI Interrupt 0000:00:11.3[D] -> GSI 10 (level, low) -> IRQ 10
[   25.071514] uhci_hcd 0000:00:11.3: UHCI Host Controller
[   25.071562] uhci_hcd 0000:00:11.3: new USB bus registered, assigned bus number 2
[   25.071597] uhci_hcd 0000:00:11.3: irq 10, io base 0x0000e000
[   25.071808] usb usb2: configuration #1 chosen from 1 choice
[   25.071857] hub 2-0:1.0: USB hub found
[   25.071874] hub 2-0:1.0: 2 ports detected
[   25.096105] hdd: ATAPI 48X DVD-ROM DVD-R CD-R/RW drive, 2048kB Cache, UDMA(33)
[   25.096124] Uniform CD-ROM driver Revision: 3.20
[   25.175373] ACPI: PCI Interrupt 0000:00:11.4[D] -> GSI 10 (level, low) -> IRQ 10
[   25.175399] uhci_hcd 0000:00:11.4: UHCI Host Controller
[   25.175446] uhci_hcd 0000:00:11.4: new USB bus registered, assigned bus number 3
[   25.175480] uhci_hcd 0000:00:11.4: irq 10, io base 0x0000e400
[   25.175662] usb usb3: configuration #1 chosen from 1 choice
[   25.175722] hub 3-0:1.0: USB hub found
[   25.175738] hub 3-0:1.0: 2 ports detected
[   25.439017] usb 1-2: new full speed USB device using uhci_hcd and address 2
[   25.571310] Attempting manual resume
[   25.571318] swsusp: Resume From Partition 3:69
[   25.571321] PM: Checking swsusp image.
[   25.595126] PM: Resume from disk failed.
[   25.635775] usb 1-2: configuration #1 chosen from 1 choice
[   25.772386] kjournald starting.  Commit interval 5 seconds
[   25.772525] EXT3-fs: mounted filesystem with ordered data mode.
[   37.066964] Linux agpgart interface v0.102 (c) Dave Jones
[   37.196788] agpgart: Detected VIA KT266/KY266x/KT333 chipset
[   37.202851] agpgart: AGP aperture is 64M @ 0xe0000000
[   37.220781] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   37.257797] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   37.282356] irda_init()
[   37.282397] NET: Registered protocol family 23
[   38.169730] input: ImExPS/2 Generic Explorer Mouse as /class/input/input2
[   38.531493] nvidia: module license 'NVIDIA' taints kernel.
[   38.788282] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 17
[   38.789082] NVRM: loading NVIDIA Linux x86 Kernel Module  1.0-9639  Mon Apr 16 20:20:06 PDT 2007
[   39.006856] parport_pc 00:04: reported by Plug and Play ACPI
[   39.006980] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,EPP,ECP,DMA]
[   39.131578] input: PC Speaker as /class/input/input3
[   39.469395] usbcore: registered new interface driver snd-usb-audio
[   39.790992] ACPI: PCI Interrupt 0000:00:11.5[C] -> GSI 5 (level, low) -> IRQ 5
[   39.791157] PCI: Setting latency timer of device 0000:00:11.5 to 64
[   41.587522] lp0: using parport0 (interrupt-driven).
[   41.665658] Adding 746980k swap on /dev/hdb5.  Priority:-1 extents:1 across:746980k
[   42.062684] EXT3 FS on hdb1, internal journal
[   43.848456] No dock devices found.
[   43.954133] input: Power Button (FF) as /class/input/input4
[   43.962793] ACPI: Power Button (FF) [PWRF]
[   44.021508] input: Power Button (CM) as /class/input/input5
[   44.022015] ACPI: Power Button (CM) [PWRB]
[   44.053489] input: Sleep Button (CM) as /class/input/input6
[   44.054407] ACPI: Sleep Button (CM) [SLPB]
[   46.493285] eth0: link up, 100Mbps, full-duplex, lpa 0x41E1
[   48.866536] NET: Registered protocol family 10
[   48.866703] lo: Disabled Privacy Extensions
[   49.205665] agpgart: Found an AGP 2.0 compliant device at 0000:00:00.0.
[   49.205900] agpgart: Putting AGP V2 device at 0000:00:00.0 into 4x mode
[   49.206107] agpgart: Putting AGP V2 device at 0000:01:00.0 into 4x mode
[   49.395370] ppdev: user-space parallel port driver
[   49.853094] audit(1206464879.953:3):  type=1503 operation="inode_permission" requested_mask="a" denied_mask="a" name="/dev/tty" pid=4898 profile="/usr/sbin/cupsd"
[   50.159362] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[   50.159372] apm: overridden by ACPI.
[   51.916710] Failure registering capabilities with primary security module.
[   52.217870] Bluetooth: Core ver 2.11
[   52.218581] NET: Registered protocol family 31
[   52.218586] Bluetooth: HCI device and connection manager initialized
[   52.218593] Bluetooth: HCI socket layer initialized
[   52.280825] Bluetooth: L2CAP ver 2.8
[   52.280835] Bluetooth: L2CAP socket layer initialized
[   52.420133] Bluetooth: RFCOMM socket layer initialized
[   52.420646] Bluetooth: RFCOMM TTY layer initialized
[   52.420651] Bluetooth: RFCOMM ver 1.8
[   57.443097] NET: Registered protocol family 17
[   71.287458] eth0: no IPv6 routers present
[ 2711.967560] usb 3-1: new full speed USB device using uhci_hcd and address 2
[ 2722.130211] usb 3-1: configuration #1 chosen from 1 choice
[ 2722.741895] usbcore: registered new interface driver libusual
[ 2723.017140] Initializing USB Mass Storage driver...
[ 2723.022025] scsi0 : SCSI emulation for USB Mass Storage devices
[ 2723.023288] usb-storage: device found at 2
[ 2723.023298] usb-storage: waiting for device to settle before scanning
[ 2723.023631] usbcore: registered new interface driver usb-storage
[ 2723.023791] USB Mass Storage support registered.
[ 2728.021258] usb-storage: device scan complete
[ 2728.025243] scsi 0:0:0:0: Direct-Access     MAXTOR S TM3250310AS           PQ: 0 ANSI: 2
[ 2728.105150] sd 0:0:0:0: [sda] 488397168 512-byte hardware sectors (250059 MB)
[ 2728.110142] sd 0:0:0:0: [sda] Write Protect is off
[ 2728.110150] sd 0:0:0:0: [sda] Mode Sense: 38 00 00 00
[ 2728.110155] sd 0:0:0:0: [sda] Assuming drive cache: write through
[ 2728.115136] sd 0:0:0:0: [sda] 488397168 512-byte hardware sectors (250059 MB)
[ 2728.120135] sd 0:0:0:0: [sda] Write Protect is off
[ 2728.120142] sd 0:0:0:0: [sda] Mode Sense: 38 00 00 00
[ 2728.120146] sd 0:0:0:0: [sda] Assuming drive cache: write through
[ 2728.120153]  sda: unknown partition table
[ 2728.153795] sd 0:0:0:0: [sda] Attached SCSI disk
[ 2728.174179] sd 0:0:0:0: Attached scsi generic sg0 type 0


```

---

### Post by Whiffle on 2008-03-25
Yep, looks like the disk isn't partitioned.  If thats true, then you'll need to partition it (gparted does this), and pick a filesystem for it.

---

### Post by Ampi on 2008-03-25
okay, sounds easy..

What file system should I choose, I mean, what's the difference??

---

### Post by Whiffle on 2008-03-25
Well, 3 choices come to mind, and they all have pros and cons:

fat32 (aka vfat)- read easily by all operating systems, 4GB file limit
ntfs - can be read by linux with ntfs-3g driver, i have no idea how good the support is though
ext3 - easily read by linux, can be read by windows using the [www.fs-driver.org](www.fs-driver.org) driver.

---

### Post by chewearn on 2008-03-25
If you are still using Windows, I recommend fat32 over ntfs, if you can live with the 4GB filesize limit.

Why?  I still see occasional users posting here about problems with ntfs formatted HD or partitions (despite complete linux ntfs r/w support available now).  On the other hand, I almost never see any user posting about fat32 problem.

---

### Post by Ampi on 2008-03-26
Yes well, the ntfs is not going to be an option. The last time I used windows it gave me a lot of problems, so byebye microsoft!
Then ext3 and vfat would be options....I guess 4Gb limit is not a problem, I don't have stuff that big and pretty much all the people I know have windows, so I thing I'm going for the vfat.

Thanks a lot, you really helped me!


And actually while being at it I have another question about the same.

Apart form having this external HD I also have two internal HD's, one with ubuntu and one with fedora. What I want is to format the HD with Fedora so I can use it as a storage device to put my home directory into it.
The biggest problem with this is that I am not really sure which HD is the one with Ubuntu (because the fdisk -l gives both linux...)

The fedora HD doesn't have any important files, I already got everything I needed....

So how do I know which HD is mine (without looking into the physical computer) and how do I partition it entirely so I can use it as my home dorectory....?

Thanks again...

---

### Post by Ampi on 2008-03-26
I for got

```

$sudo fdisk -l
Disk /dev/hda: 41.1 GB, 41110142976 bytes
255 heads, 63 sectors/track, 4998 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000d34c0

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1          13      104391   83  Linux
/dev/hda2              14        4998    40042012+  8e  Linux LVM

Disk /dev/hdb: 40.0 GB, 40027029504 bytes
255 heads, 63 sectors/track, 4866 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00098445

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1        4773    38339091   83  Linux
/dev/hdb2            4774        4866      747022+   5  Extended
/dev/hdb5            4774        4866      746991   82  Linux swap / Solaris

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00033ab7

   Device Boot      Start         End      Blocks   Id  System
```

---

### Post by chewearn on 2008-03-26
Boot into ubuntu and run gparted.  It's located under:
System > Administration > Partition Editor

If you have not installed it, this command will do it:
```
sudo apt-get install gparted
```When you ran gparted, you will find that the partitions used by ubuntu will be locked (there is a lock icon), and you can't modify it.

You can also use gparted to wipe your Fedora HD.  Once you format the HD, and reboot, ubuntu should be autodetecting the new HD, and an entry appearing under Places.  This is the simpler way to use it for storage.

Else, if you really want to remap your /home to the new HD, this the howto:
[http://ubuntuforums.org/showthread.php?t=46866](http://ubuntuforums.org/showthread.php?t=46866)

Extra reading material, if you want to know more:
[http://ubuntuforums.org/showthread.php?t=282018](http://ubuntuforums.org/showthread.php?t=282018)

---

### Post by Ampi on 2008-03-26
So I got rid of the partitions I already had and I wanted to make a complete new partition of the whole HD. It took 17 minutes and then it said the following....
So why can't a make a new partition??

The webpage they put in is about making bug reports and screen shots so I'm not sure what to do. 

```

IMPORTANT
If you want support, you need to provide the saved details!
See http://gparted.sourceforge.net/larry/tips/save_details.htm for more information.

```

---

### Post by Ampi on 2008-03-26
save_details.htm


```
GParted 0.3.3

Libparted 1.7.1

Delete /dev/hda2 (unknown, 38.19 GiB) from /dev/hda  00:01    ( SUCCES )
     	
calibrate /dev/hda2  00:00    ( SUCCES )
     	
path: /dev/hda2
start: 208845
end: 80292869
size: 80084025 (38.19 GiB)
delete partition  00:00    ( SUCCES )

========================================

Delete /dev/hda1 (ext3, 101.94 MiB) from /dev/hda  00:00    ( SUCCES )
     	
calibrate /dev/hda1  00:00    ( SUCCES )
     	
path: /dev/hda1
start: 63
end: 208844
size: 208782 (101.94 MiB)
delete partition  00:00    ( SUCCES )

========================================

Create Primary Partition #1 (ext3, 38.29 GiB) on /dev/hda  17:09    ( ERROR )
     	
create empty partition  08:14    ( SUCCES )
     	
path: /dev/hda1
start: 63
end: 80292869
size: 80292807 (38.29 GiB)
set partitiontype on /dev/hda1  08:55    ( SUCCES )
     	
new partitiontype: ext3
create new ext3 filesystem  00:00    ( ERROR )
     	
mkfs.ext3 /dev/hda1
     	
mke2fs 1.40.2 (12-Jul-2007)
Could not stat /dev/hda1 --- No such file or directory

The device apparently does not exist; did you specify it correctly?
libparted messages    ( INFO )
     	
Error informing the kernel about modifications to partition /dev/hda1 -- Device or resource busy. This means Linux won't know about any changes you made to /dev/hda1 until you reboot -- so you shouldn't mount it or use it in any way before rebooting.
The kernel was unable to re-read the partition table on /dev/hda (Device or resource busy). This means Linux won't know anything about the modifications you made until you reboot. You should reboot your computer before doing anything with /dev/hda.
Error informing the kernel about modifications to partition /dev/hda1 -- Device or resource busy. This means Linux won't know about any changes you made to /dev/hda1 until you reboot -- so you shouldn't mount it or use it in any way before rebooting.
The kernel was unable to re-read the partition table on /dev/hda (Device or resource busy). This means Linux won't know anything about the modifications you made until you reboot. You should reboot your computer before doing anything with /dev/hda.

========================================

```

---

### Post by chewearn on 2008-03-26
Not sure what is going on with the error.  Maybe a restart will fix it.

---

### Post by NICO2008 on 2008-03-26
> **Ampi said:**
> I for got

```

$sudo fdisk -l
Disk /dev/hda: 41.1 GB, 41110142976 bytes
255 heads, 63 sectors/track, 4998 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000d34c0

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1          13      104391   83  Linux
/dev/hda2              14        4998    40042012+  8e  Linux LVM

Disk /dev/hdb: 40.0 GB, 40027029504 bytes
255 heads, 63 sectors/track, 4866 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00098445

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1        4773    38339091   83  Linux
/dev/hdb2            4774        4866      747022+   5  Extended
/dev/hdb5            4774        4866      746991   82  Linux swap / Solaris

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00033ab7

   Device Boot      Start         End      Blocks   Id  System
```


I got a Maxtor OneTouch4 and had partitioned in windows with fat32, after a lot of trouble. Gparted (with NTFSTools instaled) does not recognize the external HD under Kubuntu gutsy gibon 
7.10

---

### Post by nabiscOGrahams on 2008-03-26
i know nothing about linux. my external hard drive isnt recognized either!

what does this mean? this is when i type dmesg in terminal

```
[ 1166.588000] usb 5-2: new high speed USB device using ehci_hcd and address 90
[ 1166.940000] usb 5-2: new high speed USB device using ehci_hcd and address 91
[ 1167.288000] usb 5-2: new high speed USB device using ehci_hcd and address 92
[ 1167.636000] usb 5-2: new high speed USB device using ehci_hcd and address 93
[ 1167.984000] usb 5-2: new high speed USB device using ehci_hcd and address 94
[ 1168.332000] usb 5-2: new high speed USB device using ehci_hcd and address 95
[ 1168.684000] usb 5-2: new high speed USB device using ehci_hcd and address 96
[ 1169.032000] usb 5-2: new high speed USB device using ehci_hcd and address 97
[ 1169.380000] usb 5-2: new high speed USB device using ehci_hcd and address 98
[ 1169.728000] usb 5-2: new high speed USB device using ehci_hcd and address 99
[ 1170.076000] usb 5-2: new high speed USB device using ehci_hcd and address 100
[ 1170.428000] usb 5-2: new high speed USB device using ehci_hcd and address 101
[ 1170.776000] usb 5-2: new high speed USB device using ehci_hcd and address 102
[ 1171.124000] usb 5-2: new high speed USB device using ehci_hcd and address 103
[ 1171.472000] usb 5-2: new high speed USB device using ehci_hcd and address 104
[ 1171.820000] usb 5-2: new high speed USB device using ehci_hcd and address 105
[ 1172.172000] usb 5-2: new high speed USB device using ehci_hcd and address 106
[ 1172.520000] usb 5-2: new high speed USB device using ehci_hcd and address 107
[ 1172.868000] usb 5-2: new high speed USB device using ehci_hcd and address 108
[ 1173.216000] usb 5-2: new high speed USB device using ehci_hcd and address 109
[ 1173.564000] usb 5-2: new high speed USB device using ehci_hcd and address 110
[ 1173.916000] usb 5-2: new high speed USB device using ehci_hcd and address 111
[ 1174.264000] usb 5-2: new high speed USB device using ehci_hcd and address 112
[ 1174.612000] usb 5-2: new high speed USB device using ehci_hcd and address 113
[ 1174.960000] usb 5-2: new high speed USB device using ehci_hcd and address 114
[ 1175.308000] usb 5-2: new high speed USB device using ehci_hcd and address 115
[ 1175.672000] usb 5-2: new high speed USB device using ehci_hcd and address 116
[ 1176.008000] usb 5-2: new high speed USB device using ehci_hcd and address 117
[ 1176.356000] usb 5-2: new high speed USB device using ehci_hcd and address 118
[ 1176.704000] usb 5-2: new high speed USB device using ehci_hcd and address 119
[ 1177.052000] usb 5-2: new high speed USB device using ehci_hcd and address 120
[ 1177.404000] usb 5-2: new high speed USB device using ehci_hcd and address 121
[ 1177.752000] usb 5-2: new high speed USB device using ehci_hcd and address 122
[ 1178.100000] usb 5-2: new high speed USB device using ehci_hcd and address 123
[ 1178.448000] usb 5-2: new high speed USB device using ehci_hcd and address 124
[ 1178.796000] usb 5-2: new high speed USB device using ehci_hcd and address 125
[ 1179.148000] usb 5-2: new high speed USB device using ehci_hcd and address 126
[ 1179.496000] usb 5-2: new high speed USB device using ehci_hcd and address 127
[ 1179.844000] usb 5-2: new high speed USB device using ehci_hcd and address 2
[ 1180.192000] usb 5-2: new high speed USB device using ehci_hcd and address 3
[ 1180.540000] usb 5-2: new high speed USB device using ehci_hcd and address 4
[ 1180.892000] usb 5-2: new high speed USB device using ehci_hcd and address 5
[ 1181.240000] usb 5-2: new high speed USB device using ehci_hcd and address 6
[ 1181.588000] usb 5-2: new high speed USB device using ehci_hcd and address 7
[ 1181.936000] usb 5-2: new high speed USB device using ehci_hcd and address 8
[ 1182.284000] usb 5-2: new high speed USB device using ehci_hcd and address 9
[ 1182.636000] usb 5-2: new high speed USB device using ehci_hcd and address 10
[ 1182.984000] usb 5-2: new high speed USB device using ehci_hcd and address 11
[ 1183.332000] usb 5-2: new high speed USB device using ehci_hcd and address 12
[ 1183.680000] usb 5-2: new high speed USB device using ehci_hcd and address 13
[ 1184.028000] usb 5-2: new high speed USB device using ehci_hcd and address 14
[ 1184.380000] usb 5-2: new high speed USB device using ehci_hcd and address 15
[ 1184.728000] usb 5-2: new high speed USB device using ehci_hcd and address 16
[ 1185.076000] usb 5-2: new high speed USB device using ehci_hcd and address 17
[ 1185.424000] usb 5-2: new high speed USB device using ehci_hcd and address 18
[ 1186.124000] usb 5-2: new high speed USB device using ehci_hcd and address 20

```

how do i get it to work?

---

### Post by chewearn on 2008-03-26
> **NICO2008 said:**
> I got a Maxtor OneTouch4 and had partitioned in windows with fat32, after a lot of trouble. Gparted (with NTFSTools instaled) does not recognize the external HD under Kubuntu gutsy gibon
7.10

> **nabiscOGrahams said:**
> i know nothing about linux. my external hard drive isnt recognized either!

what does this mean? this is when i type dmesg in terminal
how do i get it to work?

Sorry guys, would you mind posting your own threads?   Let's not muddle this thread with multiple unrelated conversations; it will be tough to focus on each problem.  Thanks.;)

PS: you can post a link here, so I will know where to find your new thread.   No promise that I can help though.

---

### Post by Ampi on 2008-03-27
thanks, the rebooting actually did work!

---

