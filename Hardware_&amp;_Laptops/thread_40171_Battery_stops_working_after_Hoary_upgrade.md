---
title: "Battery stops working after Hoary upgrade"
date: 2005-06-08
forum: Hardware &amp; Laptops
---

### Post by mcleod9 on 2005-06-08
Hi. I'll do my best to be specific so anyone with ideas has the most info to go on. Thank you in advance :) Here's the issue:

After upgrading my laptop to Hoary 5.04 the battery stopped working. Basically, the computer is fine when plugged in, but evidently no power is getting to the machine, as it turns off when unplugged. 

This is even stranger because dmesg shows the battery as being present and the gnome battery applet shows it as being charged 100% (when plugged in , of course)

I looked through the output of dmesg and thought that some parts didn't look right, but I'm just not sure. After doing as much research on my own, I decided that if the problem is to be solved, this forum might do the trick.

The only thing that made sense to me up front was the idea to upgrade the BIOS. I didn't get anywhere with that do to ASUS.com being down and not being entirely clear on which to flash to, so again, I'm here.

Here's the output of dmesg:

Linux version 2.6.10-5-386 (buildd@rothera) (gcc version 3.3.5 (Debian 1:3.3.5-8ubuntu2)) #1 Fri May 20 13:52:48 UTC 2005
BIOS-provided physical RAM map:
 BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
 BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
 BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
 BIOS-e820: 0000000000100000 - 000000001f7f0000 (usable)
 BIOS-e820: 000000001f7f0000 - 000000001f7fffc0 (ACPI data)
 BIOS-e820: 000000001f7fffc0 - 000000001f800000 (ACPI NVS)
 BIOS-e820: 00000000fffc0000 - 0000000100000000 (reserved)
503MB LOWMEM available.
On node 0 totalpages: 129008
  DMA zone: 4096 pages, LIFO batch:1
  Normal zone: 124912 pages, LIFO batch:16
  HighMem zone: 0 pages, LIFO batch:1
DMI 2.2 present.
ACPI: RSDP (v000 OID_00                                ) @ 0x000e4010
ACPI: RSDT (v001 OID_00 RSDT_000 0x30303030 & 0x00010000) @ 0x1f7ffbd0
ACPI: FADT (v001 INSYDE FACP_000 0x00000100 & 0x00010000) @ 0x1f7ffb20
ACPI: BOOT (v001 INSYDE ISC_BOOT 0x00000100 & 0x00010000) @ 0x1f7ffba0
ACPI: DSDT (v001 SiS630 INSYDESW 0x00001001 MSFT 0x0100000a) @ 0x00000000
ACPI: PM-Timer IO Port: 0x1008
Built 1 zonelists
Kernel command line: root=/dev/hda1 ro quiet splash acpi=force
Local APIC disabled by BIOS -- you can enable it with "lapic"
mapped APIC to ffffd000 (013f6000)
Initializing CPU#0
PID hash table entries: 2048 (order: 11, 32768 bytes)
Detected 997.128 MHz processor.
Using pmtmr for high-res timesource
Console: colour VGA+ 80x25
Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
Memory: 503964k/516032k available (1436k kernel code, 11416k reserved, 754k data, 224k init, 0k highmem)
Checking if this processor honours the WP bit even in supervisor mode... Ok.
Calibrating delay loop... 1982.46 BogoMIPS (lpj=991232)
Security Framework v1.0.0 initialized
SELinux:  Disabled at boot.
Mount-cache hash table entries: 512 (order: 0, 4096 bytes)
CPU: After generic identify, caps: 0383f9ff 00000000 00000000 00000000 00000000 00000000
CPU: After vendor identify, caps: 0383f9ff 00000000 00000000 00000000 00000000 00000000
CPU: L1 I cache: 16K, L1 D cache: 16K
CPU: L2 cache: 256K
CPU: After all inits, caps: 0383f9ff 00000000 00000000 00000040 00000000 00000000
CPU: Intel Pentium III (Coppermine) stepping 0a
Enabling fast FPU save and restore... done.
Enabling unmasked SIMD FPU exception support... done.
Checking 'hlt' instruction... OK.
Checking for popad bug... OK.
ACPI: Looking for DSDT in initrd... not found!
ACPI: setting ELCR to 0200 (from 0c20)
checking if image is initramfs...it isn't (bad gzip magic numbers); looks like an initrd
Freeing initrd memory: 4300k freed
NET: Registered protocol family 16
EISA bus registered
PCI: PCI BIOS revision 2.10 entry at 0xeb2e0, last bus=1
PCI: Using configuration type 1
mtrr: v2.0 (20020519)
ACPI: Subsystem revision 20050211
    ACPI-0169: *** Error: No object was returned from [\_SB_.PCI0.LPC_.LPT_._STA] (Node df3a1500), AE_NOT_EXIST
    ACPI-0169: *** Error: No object was returned from [\_SB_.PCI0.LPC_.COM1._STA] (Node df3a1200), AE_NOT_EXIST
ACPI: Interpreter enabled
ACPI: Using PIC for interrupt routing
ACPI: PCI Root Bridge [PCI0] (00:00)
PCI: Probing PCI hardware (bus 00)
PCI: Ignoring BAR0-3 of IDE controller 0000:00:00.1
Uncovering SIS18 that hid as a SIS503 (compatible=0)
Enabling SiS 96x SMBus.
ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
ACPI: Embedded Controller [EC0] (gpe 8)
ACPI: Power Resource [PUT1] (on)
ACPI: Power Resource [PUT1] (on)
ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 7 10 11 12) *0, disabled.
ACPI: PCI Interrupt Link [LNKB] (IRQs *5 10 12)
ACPI: PCI Interrupt Link [LNKC] (IRQs *10)
ACPI: PCI Interrupt Link [LNKD] (IRQs 10 *11 12)
Linux Plug and Play Support v0.97 (c) Adam Belay
pnp: PnP ACPI init
    ACPI-0169: *** Error: No object was returned from [\_SB_.PCI0.LPC_.LPT_._STA] (Node df3a1500), AE_NOT_EXIST
    ACPI-0169: *** Error: No object was returned from [\_SB_.PCI0.LPC_.COM1._STA] (Node df3a1200), AE_NOT_EXIST
pnp: PnP ACPI: found 10 devices
PnPBIOS: Disabled by ACPI PNP
PCI: Using ACPI for IRQ routing
** PCI interrupts are no longer routed automatically.  If this
** causes a device to stop working, it is probably because the
** driver failed to call pci_enable_device().  As a temporary
** workaround, the "pci=routeirq" argument restores the old
** behavior.  If this argument makes the device work again,
** please email the output of "lspci" to [email]bjorn.helgaas@hp.com[/email]
** so I can fix the driver.
pnp: 00:06: ioport range 0x4d0-0x4d1 has been reserved
pnp: 00:06: ioport range 0x1000-0x107f could not be reserved
pnp: 00:06: ioport range 0x1080-0x10ff has been reserved
pnp: 00:06: ioport range 0x480-0x48f has been reserved
Simple Boot Flag at 0x37 set to 0x1
audit: initializing netlink socket (disabled)
audit(1118213850.949:0): initialized
VFS: Disk quotas dquot_6.5.1
Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
devfs: 2004-01-31 Richard Gooch (rgooch@atnf.csiro.au)
devfs: boot_options: 0x0
Initializing Cryptographic API
isapnp: Scanning for PnP cards...
isapnp: No Plug & Play device found
serio: i8042 AUX port at 0x60,0x64 irq 12
serio: i8042 KBD port at 0x60,0x64 irq 1
Serial: 8250/16550 driver $Revision: 1.90 $ 54 ports, IRQ sharing enabled
ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 10
PCI: setting IRQ 10 as level-triggered
ACPI: PCI interrupt 0000:00:01.6[C] -> GSI 10 (level, low) -> IRQ 10
io scheduler noop registered
io scheduler anticipatory registered
io scheduler deadline registered
io scheduler cfq registered
RAMDISK driver initialized: 16 RAM disks of 8192K size 1024 blocksize
input: AT Translated Set 2 keyboard on isa0060/serio0
EISA: Probing bus 0 at eisa0
Cannot allocate resource for EISA slot 1
Cannot allocate resource for EISA slot 3
EISA: Detected 0 cards.
NET: Registered protocol family 2
IP: routing cache hash table of 4096 buckets, 32Kbytes
TCP: Hash tables configured (established 32768 bind 65536)
NET: Registered protocol family 8
NET: Registered protocol family 20
Restarting tasks...<6> Strange, kswapd0 not stopped
 Strange, kseriod not stopped
 done
ACPI wakeup devices: 
SLPB  LAN USB1 USB2 MODM 
ACPI: (supports S0 S1 S4 S4bios S5)
RAMDISK: cramfs filesystem found at block 0
RAMDISK: Loading 4300KiB [1 disk] into ram disk... 
VFS: Mounted root (cramfs filesystem) readonly.
Freeing unused kernel memory: 224k freed
ACPI: CPU0 (power states: C1[C1] C2[C2])
ACPI: Processor [CPU0] (supports 8 throttling states)
NET: Registered protocol family 1
Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
SIS5513: IDE controller at PCI slot 0000:00:00.1
ACPI: PCI interrupt 0000:00:00.1[A]: no GSI - using IRQ 0
SIS5513: chipset revision 208
SIS5513: not 100% native mode: will probe irqs later
SIS5513: SiS630 ATA 100 (1st gen) controller
    ide0: BM-DMA at 0x1100-0x1107, BIOS settings: hda:DMA, hdb:pio
    ide1: BM-DMA at 0x1108-0x110f, BIOS settings: hdc:DMA, hdd:pio
Probing IDE interface ide0...
hda: FUJITSU MHN2200AT, ATA DISK drive
elevator: using anticipatory as default io scheduler
ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
hda: max request size: 128KiB
hda: 39070080 sectors (20003 MB) w/2048KiB Cache, CHS=38760/16/63, UDMA(100)
hda: cache flushes supported
 /dev/ide/host0/bus0/target0/lun0: p1 p2 < p5 >
Probing IDE interface ide1...
hdc: TOSHIBA CD-ROM XM-7002Bc, ATAPI CD/DVD-ROM drive
ide1 at 0x170-0x177,0x376 on irq 15
Probing IDE interface ide2...
Probing IDE interface ide3...
Probing IDE interface ide4...
Probing IDE interface ide5...
EXT3-fs: mounted filesystem with ordered data mode.
kjournald starting.  Commit interval 5 seconds
Adding 500936k swap on /dev/hda5.  Priority:-1 extents:1
EXT3 FS on hda1, internal journal
input: PS/2 Generic Mouse on isa0060/serio1
mice: PS/2 mouse device common for all mice
hdc: ATAPI 24X CD-ROM drive, 128kB Cache
Uniform CD-ROM driver Revision: 3.20
ts: Compaq touchscreen protocol output
parport0: PC-style at 0x378 [PCSPP,EPP]
lp0: using parport0 (polling).
Capability LSM initialized
device-mapper: 4.3.0-ioctl (2004-09-30) initialised: [email]dm-devel@redhat.com[/email]
md: md driver 0.90.1 MAX_MD_DEVS=256, MD_SB_DISKS=27
hdc: packet command error: status=0x51 { DriveReady SeekComplete Error }
hdc: packet command error: error=0x50
ide: failed opcode was 100
cdrom: open failed.
hdc: packet command error: status=0x51 { DriveReady SeekComplete Error }
hdc: packet command error: error=0x50
ide: failed opcode was 100
cdrom: open failed.
Real Time Clock Driver v1.12
input: PC Speaker
inserting floppy driver for 2.6.10-5-386
Floppy drive(s): fd0 is 1.44M
FDC 0 is a post-1991 82077
irda_init()
NET: Registered protocol family 23
Linux agpgart interface v0.100 (c) Dave Jones
agpgart: Detected SiS 630 chipset
agpgart: Maximum main memory to use for agp memory: 431M
agpgart: AGP aperture is 64M @ 0x40000000
sis900.c: v1.08.07 11/02/2003
ACPI: PCI interrupt 0000:00:01.1[C] -> GSI 10 (level, low) -> IRQ 10
0000:00:01.1: ICS LAN PHY transceiver found at address 1.
0000:00:01.1: Using transceiver found at address 1 as default
eth0: SiS 900 PCI Fast Ethernet at 0x3200, IRQ 10, 00:90:f5:0c:85:39.
usbcore: registered new driver usbfs
usbcore: registered new driver hub
ohci_hcd: 2004 Nov 08 USB 1.1 'Open' Host Controller (OHCI) Driver (PCI)
ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 11
PCI: setting IRQ 11 as level-triggered
ACPI: PCI interrupt 0000:00:01.2[D] -> GSI 11 (level, low) -> IRQ 11
ohci_hcd 0000:00:01.2: Silicon Integrated Systems [SiS] USB 1.0 Controller
ohci_hcd 0000:00:01.2: irq 11, pci mem 0x44001000
ohci_hcd 0000:00:01.2: new USB bus registered, assigned bus number 1
hub 1-0:1.0: USB hub found
hub 1-0:1.0: 3 ports detected
ACPI: PCI interrupt 0000:00:01.3[D] -> GSI 11 (level, low) -> IRQ 11
ohci_hcd 0000:00:01.3: Silicon Integrated Systems [SiS] USB 1.0 Controller (#2)
ohci_hcd 0000:00:01.3: irq 11, pci mem 0x44002000
ohci_hcd 0000:00:01.3: new USB bus registered, assigned bus number 2
hub 2-0:1.0: USB hub found
hub 2-0:1.0: 3 ports detected
ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 5
PCI: setting IRQ 5 as level-triggered
ACPI: PCI interrupt 0000:00:01.4[B] -> GSI 5 (level, low) -> IRQ 5
AC'97 0 analog subsections not ready
cpci_hotplug: CompactPCI Hot Plug Core version: 0.2
pci_hotplug: PCI Hot Plug PCI Core version: 0.5
shpchp: acpi_shpchprm:\_SB_.PCI0 evaluate _BBN fail=0x5
shpchp: acpi_shpchprm:get_device PCI ROOT HID fail=0x5
pciehp: acpi_pciehprm:\_SB_.PCI0 evaluate _BBN fail=0x5
pciehp: acpi_pciehprm:get_device PCI ROOT HID fail=0x5
Linux Kernel Card Services
  options:  [pci] [cardbus] [pm]
ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 11
ACPI: PCI interrupt 0000:00:0a.0[A] -> GSI 11 (level, low) -> IRQ 11
Yenta: CardBus bridge found at 0000:00:0a.0 [1558:2202]
Yenta: Enabling burst memory read transactions
Yenta: Using INTVAL to route CSC interrupts to PCI
Yenta: Routing CardBus interrupts to PCI
Yenta TI: socket 0000:00:0a.0, mfunc 0x01d71c77, devctl 0x66
Yenta: ISA IRQ mask 0x0098, PCI irq 11
Socket status: 30000010
ieee1394: Initialized config rom entry `ip1394'
ohci1394: $Rev: 1223 $ Ben Collins <bcollins@debian.org>
ACPI: PCI interrupt 0000:00:0a.1[B] -> GSI 5 (level, low) -> IRQ 5
ohci1394: fw-host0: OHCI-1394 1.0 (PCI): IRQ=[5]  MMIO=[44004000-440047ff]  Max Packet=[2048]
ieee1394: Host added: ID:BUS[0-00:1023]  GUID[000090f5000000e9]
NET: Registered protocol family 17
ACPI: AC Adapter [AC] (on-line)
    ACPI-0169: *** Error: No object was returned from [\_SB_.PCI0.LPC_.LPT_._STA] (Node df3a1500), AE_NOT_EXIST
    ACPI-0169: *** Error: No object was returned from [\_SB_.PCI0.LPC_.COM1._STA] (Node df3a1200), AE_NOT_EXIST
ACPI: Battery Slot [BAT0] (battery present)
ACPI: Power Button (FF) [PWRF]
ACPI: Sleep Button (CM) [SLPB]
ibm_acpi: ec object not found
apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
apm: overridden by ACPI.
cs: IO port probe 0x0100-0x04ff: clean.
cs: IO port probe 0x0800-0x08ff: clean.
cs: IO port probe 0x0c00-0x0cff: clean.
cs: IO port probe 0x0a00-0x0aff: clean.
cs: memory probe 0xa0000000-0xa0ffffff: clean.
orinoco 0.13e (David Gibson <hermes@gibson.dropbear.id.au>, Pavel Roskin <proski@gnu.org>, et al)
orinoco_cs 0.13e (David Gibson <hermes@gibson.dropbear.id.au>, Pavel Roskin <proski@gnu.org>, et al)
eth1: Station identity 001f:0001:0008:0048
eth1: Looks like a Lucent/Agere firmware version 8.72
eth1: Ad-hoc demo mode supported
eth1: IEEE standard IBSS ad-hoc mode supported
eth1: WEP supported, 104-bit key
eth1: MAC address 00:02:2D:17:C5:E1
eth1: Station name "HERMES I"
eth1: ready
eth1: index 0x01: Vcc 5.0, irq 3, io 0x0100-0x013f
[drm] Initialized drm 1.0.0 20040925
[drm] Initialized sis 1.1.0 20030826 on minor 0: Silicon Integrated Systems [SiS] 630/730 PCI/AGP VGA Display Adapter
agpgart: Found an AGP 2.0 compliant device at 0000:00:00.0.
agpgart: Putting AGP V2 device at 0000:00:00.0 into 2x mode
agpgart: Putting AGP V2 device at 0000:01:00.0 into 2x mode
eth1: New link status: Connected (0001)
NET: Registered protocol family 10
Disabled Privacy Extensions on device c02f0500(lo)
IPv6 over IPv4 tunneling driver
eth1: no IPv6 routers present

---

