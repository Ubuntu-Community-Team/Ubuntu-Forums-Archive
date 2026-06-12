---
title: "Help: USB working or not?"
date: 2007-03-12
forum: Hardware &amp; Laptops
---

### Post by oasiscity on 2007-03-12
Hi guys,

sorry for lengthy post.
but can someone of you help to tell whether my usb is working or not?

I tried my digital camera, it doesn't work.

thanks!

--------------------------

me@me-desktop:~$ lsusb
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000 

me@me-desktop:~$ dmesg
[17179569.184000] Linux version 2.6.17-10-generic (root@terranova) (gcc version 4.1.2 20060928 (prerelease) (Ubuntu 4.1.1-13ubuntu5)) #2 SMP Tue Dec 5 22:28:26 UTC 2006 (Ubuntu 2.6.17-10.34-generic)
[17179569.184000] BIOS-provided physical RAM map:
[17179569.184000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[17179569.184000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[17179569.184000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[17179569.184000]  BIOS-e820: 0000000000100000 - 000000001fff0000 (usable)
[17179569.184000]  BIOS-e820: 000000001fff0000 - 000000001fff8000 (ACPI data)
[17179569.184000]  BIOS-e820: 000000001fff8000 - 0000000020000000 (ACPI NVS)
[17179569.184000]  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
[17179569.184000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[17179569.184000]  BIOS-e820: 00000000fff80000 - 0000000100000000 (reserved)
[17179569.184000] 0MB HIGHMEM available.
[17179569.184000] 511MB LOWMEM available.
[17179569.184000] found SMP MP-table at 000fb930
[17179569.184000] On node 0 totalpages: 131056
[17179569.184000]   DMA zone: 4096 pages, LIFO batch:0
[17179569.184000]   Normal zone: 126960 pages, LIFO batch:31
[17179569.184000] DMI 2.3 present.
[17179569.184000] ACPI: RSDP (v000 AMI                                   ) @ 0x000fa940
[17179569.184000] ACPI: RSDT (v001 AMIINT VIA_K7   0x00000010 MSFT 0x00000097) @ 0x1fff0000
[17179569.184000] ACPI: FADT (v001 AMIINT VIA_K7   0x00000011 MSFT 0x00000097) @ 0x1fff0030
[17179569.184000] ACPI: MADT (v001 AMIINT VIA_K7   0x00000009 MSFT 0x00000097) @ 0x1fff00c0
[17179569.184000] ACPI: DSDT (v001    VIA   VIA_K7 0x00001000 MSFT 0x0100000d) @ 0x00000000
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
[17179569.184000] Allocating PCI resources starting at 30000000 (gap: 20000000:dec00000)
[17179569.184000] Built 1 zonelists
[17179569.184000] Kernel command line: root=UUID=bc097c30-7f1c-43e0-a724-bda958455558 ro quiet splash
[17179569.184000] mapped APIC to ffffd000 (fee00000)
[17179569.184000] mapped IOAPIC to ffffc000 (fec00000)
[17179569.184000] Enabling fast FPU save and restore... done.
[17179569.184000] Enabling unmasked SIMD FPU exception support... done.
[17179569.184000] Initializing CPU#0
[17179569.184000] PID hash table entries: 2048 (order: 11, 8192 bytes)
[17179569.184000] Detected 1488.960 MHz processor.
[17179569.184000] Using pmtmr for high-res timesource
[17179569.184000] Console: colour VGA+ 80x25
[17179569.768000] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
[17179569.768000] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
[17179569.784000] Memory: 508264k/524224k available (1910k kernel code, 15348k reserved, 1069k data, 308k init, 0k highmem)
[17179569.784000] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[17179569.864000] Calibrating delay using timer specific routine.. 2980.79 BogoMIPS (lpj=5961588)
[17179569.864000] Security Framework v1.0.0 initialized
[17179569.864000] SELinux:  Disabled at boot.
[17179569.864000] Mount-cache hash table entries: 512
[17179569.864000] CPU: After generic identify, caps: 0383fbff c1c3fbff 00000000 00000000 00000000 00000000 00000000
[17179569.864000] CPU: After vendor identify, caps: 0383fbff c1c3fbff 00000000 00000000 00000000 00000000 00000000
[17179569.864000] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[17179569.864000] CPU: L2 Cache: 256K (64 bytes/line)
[17179569.864000] CPU: After all inits, caps: 0383fbff c1c3fbff 00000000 00000420 00000000 00000000 00000000
[17179569.864000] Checking 'hlt' instruction... OK.
[17179569.880000] SMP alternatives: switching to UP code
[17179569.880000] Freeing SMP alternatives: 16k freed
[17179569.880000] checking if image is initramfs... it is
[17179570.664000] Freeing initrd memory: 7075k freed
[17179570.664000] ACPI: Core revision 20060707
[17179570.664000] ACPI: Looking for DSDT ... not found!
[17179570.668000] CPU0: AMD mobile AMD Athlon(tm) XP-M 1700+ stepping 00
[17179570.668000] Total of 1 processors activated (2980.79 BogoMIPS).
[17179570.668000] ENABLING IO-APIC IRQs
[17179570.668000] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[17179570.812000] Brought up 1 CPUs
[17179570.812000] migration_cost=0
[17179570.812000] NET: Registered protocol family 16
[17179570.812000] EISA bus registered
[17179570.812000] ACPI: bus type pci registered
[17179570.812000] PCI: PCI BIOS revision 2.10 entry at 0xfdaf1, last bus=1
[17179570.812000] PCI: Using configuration type 1
[17179570.812000] Setting up standard PCI resources
[17179570.820000] ACPI: Interpreter enabled
[17179570.820000] ACPI: Using IOAPIC for interrupt routing
[17179570.824000] ACPI: PCI Root Bridge [PCI0] (0000:00)
[17179570.824000] PCI: Probing PCI hardware (bus 00)
[17179570.824000] PCI quirk: region 0800-087f claimed by vt8235 PM
[17179570.824000] PCI quirk: region 0400-040f claimed by vt8235 SMB
[17179570.824000] PCI: Ignoring BAR0-3 of IDE controller 0000:00:11.1
[17179570.824000] Boot video device is 0000:01:00.0
[17179570.828000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[17179570.832000] ACPI: Power Resource [URP1] (off)
[17179570.832000] ACPI: Power Resource [URP2] (off)
[17179570.832000] ACPI: Power Resource [FDDP] (off)
[17179570.832000] ACPI: Power Resource [LPTP] (off)
[17179570.832000] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 10 *11 12 14 15)
[17179570.832000] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[17179570.832000] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 *5 6 7 10 11 12 14 15)
[17179570.832000] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 *10 11 12 14 15)
[17179570.832000] Linux Plug and Play Support v0.97 (c) Adam Belay
[17179570.832000] pnp: PnP ACPI init
[17179570.836000] pnp: PnP ACPI: found 12 devices
[17179570.836000] PnPBIOS: Disabled by ACPI PNP
[17179570.836000] PCI: Using ACPI for IRQ routing
[17179570.836000] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[17179570.840000] PCI: Bridge: 0000:00:01.0
[17179570.840000]   IO window: disabled.
[17179570.840000]   MEM window: dde00000-dfefffff
[17179570.840000]   PREFETCH window: cdd00000-ddcfffff
[17179570.840000] PCI: Setting latency timer of device 0000:00:01.0 to 64
[17179570.840000] NET: Registered protocol family 2
[17179570.880000] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
[17179570.880000] TCP established hash table entries: 16384 (order: 5, 131072 bytes)
[17179570.880000] TCP bind hash table entries: 8192 (order: 4, 65536 bytes)
[17179570.880000] TCP: Hash tables configured (established 16384 bind 8192)
[17179570.880000] TCP reno registered
[17179570.880000] audit: initializing netlink socket (disabled)
[17179570.880000] audit(1173742573.880:1): initialized
[17179570.880000] VFS: Disk quotas dquot_6.5.1
[17179570.880000] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[17179570.880000] Initializing Cryptographic API
[17179570.880000] io scheduler noop registered
[17179570.880000] io scheduler anticipatory registered
[17179570.880000] io scheduler deadline registered
[17179570.880000] io scheduler cfq registered (default)
[17179570.880000] isapnp: Scanning for PnP cards...
[17179571.232000] isapnp: No Plug & Play device found
[17179571.260000] Real Time Clock Driver v1.12ac
[17179571.260000] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[17179571.260000] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[17179571.260000] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[17179571.264000] 00:09: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[17179571.264000] 00:0a: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[17179571.264000] mice: PS/2 mouse device common for all mice
[17179571.264000] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[17179571.264000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[17179571.264000] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[17179571.264000] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[17179571.264000] serio: i8042 AUX port at 0x60,0x64 irq 12
[17179571.264000] serio: i8042 KBD port at 0x60,0x64 irq 1
[17179571.264000] EISA: Probing bus 0 at eisa.0
[17179571.264000] EISA: Detected 0 cards.
[17179571.264000] TCP bic registered
[17179571.264000] NET: Registered protocol family 1
[17179571.264000] NET: Registered protocol family 8
[17179571.264000] NET: Registered protocol family 20
[17179571.264000] Using IPI No-Shortcut mode
[17179571.264000] ACPI: (supports S0 S1 S4 S5)
[17179571.264000] Freeing unused kernel memory: 308k freed
[17179571.288000] input: AT Translated Set 2 keyboard as /class/input/input0
[17179572.420000] Capability LSM initialized
[17179573.084000] VP_IDE: IDE controller at PCI slot 0000:00:11.1
[17179573.084000] ACPI: Unable to derive IRQ for device 0000:00:11.1
[17179573.084000] ACPI: PCI Interrupt 0000:00:11.1[A]: no GSI
[17179573.084000] PCI: Via IRQ fixup for 0000:00:11.1, from 255 to 15
[17179573.084000] VP_IDE: chipset revision 6
[17179573.084000] VP_IDE: not 100% native mode: will probe irqs later
[17179573.084000] VP_IDE: VIA vt8235 (rev 00) IDE UDMA133 controller on pci0000:00:11.1
[17179573.084000]     ide0: BM-DMA at 0xfc00-0xfc07, BIOS settings: hda:DMA, hdb:DMA
[17179573.084000]     ide1: BM-DMA at 0xfc08-0xfc0f, BIOS settings: hdc:pio, hdd:pio
[17179573.084000] Probing IDE interface ide0...
[17179573.528000] hda: ST380011A, ATA DISK drive
[17179574.000000] hdb: ATAPI-CD ROM-DRIVE-50MAX, ATAPI CD/DVD-ROM drive
[17179574.060000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[17179574.064000] Probing IDE interface ide1...
[17179574.660000] hda: max request size: 512KiB
[17179574.672000] hda: 156301488 sectors (80026 MB) w/2048KiB Cache, CHS=16383/255/63, UDMA(100)
[17179574.672000] hda: cache flushes supported
[17179574.672000]  hda: hda1 hda2 < hda5 hda6 > hda3
[17179574.728000] hdb: ATAPI 50X CD-ROM drive, 128kB Cache, UDMA(33)
[17179574.728000] Uniform CD-ROM driver Revision: 3.20
[17179575.084000] Probing IDE interface ide1...
[17179575.124000] usbcore: registered new driver usbfs
[17179575.124000] usbcore: registered new driver hub
[17179575.128000] USB Universal Host Controller Interface driver v3.0
[17179575.128000] ACPI: PCI Interrupt 0000:00:10.0[A] -> GSI 21 (level, low) -> IRQ 169
[17179575.128000] PCI: Via IRQ fixup for 0000:00:10.0, from 11 to 9
[17179575.128000] uhci_hcd 0000:00:10.0: UHCI Host Controller
[17179575.128000] uhci_hcd 0000:00:10.0: new USB bus registered, assigned bus number 1
[17179575.128000] uhci_hcd 0000:00:10.0: irq 169, io base 0x0000ec00
[17179575.128000] usb usb1: configuration #1 chosen from 1 choice
[17179575.128000] hub 1-0:1.0: USB hub found
[17179575.128000] hub 1-0:1.0: 2 ports detected
[17179575.236000] ACPI: PCI Interrupt 0000:00:10.3[D] -> GSI 21 (level, low) -> IRQ 169
[17179575.236000] PCI: Via IRQ fixup for 0000:00:10.3, from 10 to 9
[17179575.236000] ehci_hcd 0000:00:10.3: EHCI Host Controller
[17179575.236000] ehci_hcd 0000:00:10.3: new USB bus registered, assigned bus number 2
[17179575.236000] ehci_hcd 0000:00:10.3: irq 169, io mem 0xdfffff00
[17179575.236000] ehci_hcd 0000:00:10.3: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[17179575.236000] usb usb2: configuration #1 chosen from 1 choice
[17179575.236000] hub 2-0:1.0: USB hub found
[17179575.236000] hub 2-0:1.0: 2 ports detected
[17179575.980000] kjournald starting.  Commit interval 5 seconds
[17179575.980000] EXT3-fs: mounted filesystem with ordered data mode.
[17179588.380000] Floppy drive(s): fd0 is 1.44M
[17179588.416000] FDC 0 is a post-1991 82077
[17179588.728000] via-rhine.c:v1.10-LK1.2.0-2.6 June-10-2004 Written by Donald Becker
[17179588.728000] ACPI: PCI Interrupt 0000:00:12.0[A] -> GSI 23 (level, low) -> IRQ 177
[17179588.728000] PCI: Via IRQ fixup for 0000:00:12.0, from 11 to 1
[17179588.732000] eth0: VIA Rhine II at 0x1e400, 00:0c:76:3f:76:b4, IRQ 177.
[17179588.736000] eth0: MII PHY found at address 1, status 0x786d advertising 05e1 Link 45e1.
[17179588.832000] parport: PnPBIOS parport detected.
[17179588.832000] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,EPP,ECP,DMA]
[17179588.928000] input: ImPS/2 Generic Wheel Mouse as /class/input/input1
[17179588.996000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[17179589.000000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[17179589.056000] input: PC Speaker as /class/input/input2
[17179589.104000] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[17179589.144000] Linux agpgart interface v0.101 (c) Dave Jones
[17179589.212000] agpgart: Detected VIA KT400/KT400A/KT600 chipset
[17179589.220000] agpgart: AGP aperture is 128M @ 0xe0000000
[17179589.468000] irda_init()
[17179589.468000] NET: Registered protocol family 23
[17179589.664000] ts: Compaq touchscreen protocol output
[17179590.008000] nvidia: module license 'NVIDIA' taints kernel.
[17179590.012000] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 185
[17179590.012000] NVRM: loading NVIDIA Linux x86 Kernel Module  1.0-8776  Mon Oct 16 21:56:04 PDT 2006
[17179590.332000] NET: Registered protocol family 17
[17179590.384000] ACPI: PCI Interrupt 0000:00:11.5[C] -> GSI 22 (level, low) -> IRQ 193
[17179590.384000] PCI: Via IRQ fixup for 0000:00:11.5, from 5 to 1
[17179590.384000] PCI: Setting latency timer of device 0000:00:11.5 to 64
[17179591.232000] lp0: using parport0 (interrupt-driven).
[17179591.304000] Adding 746980k swap on /dev/hda6.  Priority:-1 extents:1 across:746980k
[17179591.432000] EXT3 FS on hda3, internal journal
[17179591.692000] md: md driver 0.90.3 MAX_MD_DEVS=256, MD_SB_DISKS=27
[17179591.692000] md: bitmap version 4.39
[17179591.912000] device-mapper: 4.6.0-ioctl (2006-02-17) initialised: [email]dm-devel@redhat.com[/email]
[17179595.676000] NTFS driver 2.1.27 [Flags: R/O MODULE].
[17179595.772000] NTFS volume version 3.1.
[17179601.204000] CSLIP: code copyright 1989 Regents of the University of California
[17179601.216000] PPP generic driver version 2.4.2
[17179604.284000] ACPI: Power Button (FF) [PWRF]
[17179604.284000] ACPI: Power Button (CM) [PWRB]
[17179604.284000] ACPI: Sleep Button (CM) [SLPB]
[17179604.424000] ibm_acpi: ec object not found
[17179604.464000] pcc_acpi: loading...
[17179604.916000] powernow: PowerNOW! Technology present. Can scale: frequency and voltage.
[17179604.920000] powernow: Trying ACPI perflib
[17179604.920000] powernow: ACPI perflib can not be used in this platform
[17179604.920000] powernow: ACPI and legacy methods failed
[17179604.920000] powernow: See [http://www.codemonkey.org.uk/projects/cpufreq/powernow-k7.shtml](http://www.codemonkey.org.uk/projects/cpufreq/powernow-k7.shtml)
[17179608.092000] agpgart: Found an AGP 3.5 compliant device at 0000:00:00.0.
[17179608.092000] agpgart: Putting AGP V3 device at 0000:00:00.0 into 8x mode
[17179608.092000] agpgart: Putting AGP V3 device at 0000:01:00.0 into 8x mode

---

### Post by apjone on 2007-03-13
Insert camera, then do a 'lsusb' and 'dmesg' in a console and post here

---

### Post by oasiscity on 2007-03-14
> **apjone said:**
> Insert camera, then do a 'lsusb' and 'dmesg' in a console and post here

hello,
here it is! 
any finding?

me@me-desktop:~$ lsusb
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  

me@me-desktop:~$ dmesg
[17179569.184000] Linux version 2.6.17-10-generic (root@terranova) (gcc version 4.1.2 20060928 (prerelease) (Ubuntu 4.1.1-13ubuntu5)) #2 SMP Tue Dec 5 22:28:26 UTC 2006 (Ubuntu 2.6.17-10.34-generic)
[17179569.184000] BIOS-provided physical RAM map:
[17179569.184000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[17179569.184000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[17179569.184000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[17179569.184000]  BIOS-e820: 0000000000100000 - 000000001fff0000 (usable)
[17179569.184000]  BIOS-e820: 000000001fff0000 - 000000001fff8000 (ACPI data)
[17179569.184000]  BIOS-e820: 000000001fff8000 - 0000000020000000 (ACPI NVS)
[17179569.184000]  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
[17179569.184000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[17179569.184000]  BIOS-e820: 00000000fff80000 - 0000000100000000 (reserved)
[17179569.184000] 0MB HIGHMEM available.
[17179569.184000] 511MB LOWMEM available.
[17179569.184000] found SMP MP-table at 000fb930
[17179569.184000] On node 0 totalpages: 131056
[17179569.184000]   DMA zone: 4096 pages, LIFO batch:0
[17179569.184000]   Normal zone: 126960 pages, LIFO batch:31
[17179569.184000] DMI 2.3 present.
[17179569.184000] ACPI: RSDP (v000 AMI                                   ) @ 0x000fa940
[17179569.184000] ACPI: RSDT (v001 AMIINT VIA_K7   0x00000010 MSFT 0x00000097) @ 0x1fff0000
[17179569.184000] ACPI: FADT (v001 AMIINT VIA_K7   0x00000011 MSFT 0x00000097) @ 0x1fff0030
[17179569.184000] ACPI: MADT (v001 AMIINT VIA_K7   0x00000009 MSFT 0x00000097) @ 0x1fff00c0
[17179569.184000] ACPI: DSDT (v001    VIA   VIA_K7 0x00001000 MSFT 0x0100000d) @ 0x00000000
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
[17179569.184000] Allocating PCI resources starting at 30000000 (gap: 20000000:dec00000)
[17179569.184000] Built 1 zonelists
[17179569.184000] Kernel command line: root=UUID=bc097c30-7f1c-43e0-a724-bda958455558 ro quiet splash
[17179569.184000] mapped APIC to ffffd000 (fee00000)
[17179569.184000] mapped IOAPIC to ffffc000 (fec00000)
[17179569.184000] Enabling fast FPU save and restore... done.
[17179569.184000] Enabling unmasked SIMD FPU exception support... done.
[17179569.184000] Initializing CPU#0
[17179569.184000] PID hash table entries: 2048 (order: 11, 8192 bytes)
[17179569.184000] Detected 1488.960 MHz processor.
[17179569.184000] Using pmtmr for high-res timesource
[17179569.184000] Console: colour VGA+ 80x25
[17179569.440000] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
[17179569.440000] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
[17179569.456000] Memory: 508264k/524224k available (1910k kernel code, 15348k reserved, 1069k data, 308k init, 0k highmem)
[17179569.456000] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[17179569.536000] Calibrating delay using timer specific routine.. 2980.78 BogoMIPS (lpj=5961574)
[17179569.536000] Security Framework v1.0.0 initialized
[17179569.536000] SELinux:  Disabled at boot.
[17179569.536000] Mount-cache hash table entries: 512
[17179569.536000] CPU: After generic identify, caps: 0383fbff c1c3fbff 00000000 00000000 00000000 00000000 00000000
[17179569.536000] CPU: After vendor identify, caps: 0383fbff c1c3fbff 00000000 00000000 00000000 00000000 00000000
[17179569.536000] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[17179569.536000] CPU: L2 Cache: 256K (64 bytes/line)
[17179569.536000] CPU: After all inits, caps: 0383fbff c1c3fbff 00000000 00000420 00000000 00000000 00000000
[17179569.536000] Checking 'hlt' instruction... OK.
[17179569.552000] SMP alternatives: switching to UP code
[17179569.552000] Freeing SMP alternatives: 16k freed
[17179569.552000] checking if image is initramfs... it is
[17179570.336000] Freeing initrd memory: 7075k freed
[17179570.336000] ACPI: Core revision 20060707
[17179570.336000] ACPI: Looking for DSDT ... not found!
[17179570.340000] CPU0: AMD mobile AMD Athlon(tm) XP-M 1700+ stepping 00
[17179570.340000] Total of 1 processors activated (2980.78 BogoMIPS).
[17179570.340000] ENABLING IO-APIC IRQs
[17179570.340000] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[17179570.484000] Brought up 1 CPUs
[17179570.484000] migration_cost=0
[17179570.484000] NET: Registered protocol family 16
[17179570.484000] EISA bus registered
[17179570.484000] ACPI: bus type pci registered
[17179570.484000] PCI: PCI BIOS revision 2.10 entry at 0xfdaf1, last bus=1
[17179570.484000] PCI: Using configuration type 1
[17179570.484000] Setting up standard PCI resources
[17179570.492000] ACPI: Interpreter enabled
[17179570.492000] ACPI: Using IOAPIC for interrupt routing
[17179570.496000] ACPI: PCI Root Bridge [PCI0] (0000:00)
[17179570.496000] PCI: Probing PCI hardware (bus 00)
[17179570.496000] PCI quirk: region 0800-087f claimed by vt8235 PM
[17179570.496000] PCI quirk: region 0400-040f claimed by vt8235 SMB
[17179570.496000] PCI: Ignoring BAR0-3 of IDE controller 0000:00:11.1
[17179570.496000] Boot video device is 0000:01:00.0
[17179570.500000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[17179570.504000] ACPI: Power Resource [URP1] (off)
[17179570.504000] ACPI: Power Resource [URP2] (off)
[17179570.504000] ACPI: Power Resource [FDDP] (off)
[17179570.504000] ACPI: Power Resource [LPTP] (off)
[17179570.504000] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 10 *11 12 14 15)
[17179570.504000] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[17179570.504000] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 *5 6 7 10 11 12 14 15)
[17179570.504000] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 *10 11 12 14 15)
[17179570.504000] Linux Plug and Play Support v0.97 (c) Adam Belay
[17179570.504000] pnp: PnP ACPI init
[17179570.508000] pnp: PnP ACPI: found 12 devices
[17179570.508000] PnPBIOS: Disabled by ACPI PNP
[17179570.508000] PCI: Using ACPI for IRQ routing
[17179570.508000] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[17179570.512000] PCI: Bridge: 0000:00:01.0
[17179570.512000]   IO window: disabled.
[17179570.512000]   MEM window: dde00000-dfefffff
[17179570.512000]   PREFETCH window: cdd00000-ddcfffff
[17179570.512000] PCI: Setting latency timer of device 0000:00:01.0 to 64
[17179570.512000] NET: Registered protocol family 2
[17179570.552000] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
[17179570.552000] TCP established hash table entries: 16384 (order: 5, 131072 bytes)
[17179570.552000] TCP bind hash table entries: 8192 (order: 4, 65536 bytes)
[17179570.552000] TCP: Hash tables configured (established 16384 bind 8192)
[17179570.552000] TCP reno registered
[17179570.552000] audit: initializing netlink socket (disabled)
[17179570.552000] audit(1173902895.552:1): initialized
[17179570.552000] VFS: Disk quotas dquot_6.5.1
[17179570.552000] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[17179570.552000] Initializing Cryptographic API
[17179570.552000] io scheduler noop registered
[17179570.552000] io scheduler anticipatory registered
[17179570.552000] io scheduler deadline registered
[17179570.552000] io scheduler cfq registered (default)
[17179570.552000] isapnp: Scanning for PnP cards...
[17179570.904000] isapnp: No Plug & Play device found
[17179570.932000] Real Time Clock Driver v1.12ac
[17179570.932000] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[17179570.932000] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[17179570.932000] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[17179570.936000] 00:09: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[17179570.936000] 00:0a: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[17179570.936000] mice: PS/2 mouse device common for all mice
[17179570.936000] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[17179570.936000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[17179570.936000] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[17179570.936000] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[17179570.936000] serio: i8042 AUX port at 0x60,0x64 irq 12
[17179570.936000] serio: i8042 KBD port at 0x60,0x64 irq 1
[17179570.936000] EISA: Probing bus 0 at eisa.0
[17179570.936000] EISA: Detected 0 cards.
[17179570.936000] TCP bic registered
[17179570.936000] NET: Registered protocol family 1
[17179570.936000] NET: Registered protocol family 8
[17179570.936000] NET: Registered protocol family 20
[17179570.936000] Using IPI No-Shortcut mode
[17179570.936000] ACPI: (supports S0 S1 S4 S5)
[17179570.936000] Freeing unused kernel memory: 308k freed
[17179570.960000] input: AT Translated Set 2 keyboard as /class/input/input0
[17179572.084000] Capability LSM initialized
[17179572.736000] VP_IDE: IDE controller at PCI slot 0000:00:11.1
[17179572.736000] ACPI: Unable to derive IRQ for device 0000:00:11.1
[17179572.736000] ACPI: PCI Interrupt 0000:00:11.1[A]: no GSI
[17179572.736000] PCI: Via IRQ fixup for 0000:00:11.1, from 255 to 15
[17179572.736000] VP_IDE: chipset revision 6
[17179572.736000] VP_IDE: not 100% native mode: will probe irqs later
[17179572.736000] VP_IDE: VIA vt8235 (rev 00) IDE UDMA133 controller on pci0000:00:11.1
[17179572.736000]     ide0: BM-DMA at 0xfc00-0xfc07, BIOS settings: hda:DMA, hdb:DMA
[17179572.736000]     ide1: BM-DMA at 0xfc08-0xfc0f, BIOS settings: hdc:pio, hdd:pio
[17179572.736000] Probing IDE interface ide0...
[17179573.152000] hda: ST380011A, ATA DISK drive
[17179573.600000] hdb: ATAPI-CD ROM-DRIVE-50MAX, ATAPI CD/DVD-ROM drive
[17179573.656000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[17179573.660000] Probing IDE interface ide1...
[17179574.240000] hda: max request size: 512KiB
[17179574.244000] hda: 156301488 sectors (80026 MB) w/2048KiB Cache, CHS=16383/255/63, UDMA(100)
[17179574.244000] hda: cache flushes supported
[17179574.244000]  hda: hda1 hda2 < hda5 hda6 > hda3
[17179574.304000] hdb: ATAPI 50X CD-ROM drive, 128kB Cache, UDMA(33)
[17179574.304000] Uniform CD-ROM driver Revision: 3.20
[17179574.648000] Probing IDE interface ide1...
[17179574.688000] usbcore: registered new driver usbfs
[17179574.688000] usbcore: registered new driver hub
[17179574.692000] USB Universal Host Controller Interface driver v3.0
[17179574.692000] ACPI: PCI Interrupt 0000:00:10.0[A] -> GSI 21 (level, low) -> IRQ 169
[17179574.692000] PCI: Via IRQ fixup for 0000:00:10.0, from 11 to 9
[17179574.692000] uhci_hcd 0000:00:10.0: UHCI Host Controller
[17179574.692000] uhci_hcd 0000:00:10.0: new USB bus registered, assigned bus number 1
[17179574.692000] uhci_hcd 0000:00:10.0: irq 169, io base 0x0000ec00
[17179574.692000] usb usb1: configuration #1 chosen from 1 choice
[17179574.692000] hub 1-0:1.0: USB hub found
[17179574.692000] hub 1-0:1.0: 2 ports detected
[17179574.812000] ACPI: PCI Interrupt 0000:00:10.3[D] -> GSI 21 (level, low) -> IRQ 169
[17179574.812000] PCI: Via IRQ fixup for 0000:00:10.3, from 10 to 9
[17179574.812000] ehci_hcd 0000:00:10.3: EHCI Host Controller
[17179574.812000] ehci_hcd 0000:00:10.3: new USB bus registered, assigned bus number 2
[17179574.812000] ehci_hcd 0000:00:10.3: irq 169, io mem 0xdfffff00
[17179574.812000] ehci_hcd 0000:00:10.3: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[17179574.812000] usb usb2: configuration #1 chosen from 1 choice
[17179574.812000] hub 2-0:1.0: USB hub found
[17179574.812000] hub 2-0:1.0: 2 ports detected
[17179575.612000] kjournald starting.  Commit interval 5 seconds
[17179575.612000] EXT3-fs: mounted filesystem with ordered data mode.
[17179587.820000] irda_init()
[17179587.820000] NET: Registered protocol family 23
[17179588.648000] via-rhine.c:v1.10-LK1.2.0-2.6 June-10-2004 Written by Donald Becker
[17179588.648000] ACPI: PCI Interrupt 0000:00:12.0[A] -> GSI 23 (level, low) -> IRQ 177
[17179588.648000] PCI: Via IRQ fixup for 0000:00:12.0, from 11 to 1
[17179588.652000] eth0: VIA Rhine II at 0x1e400, 00:0c:76:3f:76:b4, IRQ 177.
[17179588.652000] eth0: MII PHY found at address 1, status 0x786d advertising 05e1 Link 45e1.
[17179588.704000] parport: PnPBIOS parport detected.
[17179588.704000] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,EPP,ECP,DMA]
[17179588.760000] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[17179588.808000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[17179588.812000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[17179588.824000] input: PC Speaker as /class/input/input1
[17179588.916000] Floppy drive(s): fd0 is 1.44M
[17179588.936000] FDC 0 is a post-1991 82077
[17179589.040000] Linux agpgart interface v0.101 (c) Dave Jones
[17179589.040000] agpgart: Detected VIA KT400/KT400A/KT600 chipset
[17179589.048000] agpgart: AGP aperture is 128M @ 0xe0000000
[17179589.320000] nvidia: module license 'NVIDIA' taints kernel.
[17179589.328000] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 185
[17179589.328000] NVRM: loading NVIDIA Linux x86 Kernel Module  1.0-8776  Mon Oct 16 21:56:04 PDT 2006
[17179589.660000] input: ImPS/2 Generic Wheel Mouse as /class/input/input2
[17179589.688000] ACPI: PCI Interrupt 0000:00:11.5[C] -> GSI 22 (level, low) -> IRQ 193
[17179589.688000] PCI: Via IRQ fixup for 0000:00:11.5, from 5 to 1
[17179589.688000] PCI: Setting latency timer of device 0000:00:11.5 to 64
[17179589.720000] ts: Compaq touchscreen protocol output
[17179589.828000] NET: Registered protocol family 17
[17179590.508000] lp0: using parport0 (interrupt-driven).
[17179590.576000] Adding 746980k swap on /dev/hda6.  Priority:-1 extents:1 across:746980k
[17179590.704000] EXT3 FS on hda3, internal journal
[17179590.968000] md: md driver 0.90.3 MAX_MD_DEVS=256, MD_SB_DISKS=27
[17179590.968000] md: bitmap version 4.39
[17179591.192000] device-mapper: 4.6.0-ioctl (2006-02-17) initialised: [email]dm-devel@redhat.com[/email]
[17179595.072000] NTFS driver 2.1.27 [Flags: R/O MODULE].
[17179595.176000] NTFS volume version 3.1.
[17179600.600000] CSLIP: code copyright 1989 Regents of the University of California
[17179600.612000] PPP generic driver version 2.4.2
[17179604.620000] ACPI: Power Button (FF) [PWRF]
[17179604.620000] ACPI: Power Button (CM) [PWRB]
[17179604.620000] ACPI: Sleep Button (CM) [SLPB]
[17179604.760000] ibm_acpi: ec object not found
[17179604.800000] pcc_acpi: loading...
[17179605.268000] powernow: PowerNOW! Technology present. Can scale: frequency and voltage.
[17179605.272000] powernow: Trying ACPI perflib
[17179605.272000] powernow: ACPI perflib can not be used in this platform
[17179605.272000] powernow: ACPI and legacy methods failed
[17179605.272000] powernow: See [http://www.codemonkey.org.uk/projects/cpufreq/powernow-k7.shtml](http://www.codemonkey.org.uk/projects/cpufreq/powernow-k7.shtml)
[17179608.664000] agpgart: Found an AGP 3.5 compliant device at 0000:00:00.0.
[17179608.664000] agpgart: Putting AGP V3 device at 0000:00:00.0 into 8x mode
[17179608.664000] agpgart: Putting AGP V3 device at 0000:01:00.0 into 8x mode

---

### Post by apjone on 2007-03-14
seems its not picking it up. umm not sure

---

### Post by teaker1s on 2007-03-15
make sure your camera is on, some camera's require the camera to be set in transfer mode or pc mode. we are looking for something like this
daniel@ubuntu:~$ lsusb
Bus 005 Device 002: ID 0a5c:200a Broadcom Corp.
Bus 005 Device 001: ID 0000:0000
Bus 006 Device 001: ID 0000:0000
Bus 004 Device 002: ID 152e:2507 LG (HLDS)
[COLOR="Red"]Bus 004 Device 003: ID 04b8:0813[/COLOR] Seiko Epson Corp.
Bus 004 Device 001: ID 0000:0000
Bus 003 Device 001: ID 0000:0000
Bus 001 Device 001: ID 0000:0000
Bus 002 Device 001: ID 0000:0000
daniel@ubuntu:~$

the other way that may help is if you give us the full camera make and model-we may be able to find some information for you.

---

