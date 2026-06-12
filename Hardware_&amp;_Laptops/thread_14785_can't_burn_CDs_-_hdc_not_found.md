---
title: "can't burn CDs - hdc not found"
date: 2005-02-09
forum: Hardware &amp; Laptops
---

### Post by jaybee99 on 2005-02-09
I have CDRW and DVDROM drives, hdc and hdd, well I should have, but /dev/hdc doesn't exist...hdc exists and burns CDs fine in fedora core 2, but there's no such file or dir in ubuntu. I am using 4.1 warty, kernel 2.6.8. I added the option hdc=ide-scsi to grub's menu.lst

in fstab:

```

/dev/hdc        /media/cdrom0   udf,iso9660 rw,user,noauto  0       0

```
(I changed ro to rw)

in dmesg | grep hdc:

```

Kernel command line: root=/dev/hda5 ro quiet splash hdc=ide-scsi
ide_setup: hdc=ide-scsi
    ide1: BM-DMA at 0xc008-0xc00f, BIOS settings: hdc:DMA, hdd:DMA
hdc: LITE-ON LTR-52327S, ATAPI CD/DVD-ROM drive

```

when I look in xcdroast setup hdc is listed as the burner but if I rescan devices it disappears and can't be added manually. Any ideas?

TIA

---

### Post by jaybee99 on 2005-02-10
*bump* anybody?

---

### Post by jaybee99 on 2005-02-12
As an update to this, I can't burn CDs in fedora either, although I definitely could a few weeks ago. Since then I added a 2nd hard drive, not the one that has ubuntu or fc2 installed...could this have caused the problem somehow?

---

### Post by grj on 2005-02-12
It would only have a negative affect, if you installed it where the cdrom was before. That is, did you install the new HD, where the CD used to be. If so, the drive would have changed.

---

### Post by jaybee99 on 2005-02-12
Thanks for your reply - no, the new hd is connected to the spare IDE connector between hda and hdc the CDRW drive. The bios recognises the two hds as primary master and slave and the CDRW/DVDROM drives as secondary master and slave. I checked that the cables are all OK after me fiddling around, and disconnected hdb just to check - no change...

---

### Post by hajo on 2005-02-13
I have a very similar problem with my new ubuntu installation.

My configuration (/devhdc=cd-writerLG CGE-8250B; /dev/hdd=no name DVD-ROM)
works fine using win98 or Suse9.0 (still available as alternative boot)

The "ro" in fstab is probably not the problem.
The fstab of Suse 9.0 sets the cdwriter to "ro" too, but k3b works well.

I seems, the hardware detection of ubuntu does not install the devices correctly.
I do not find any device like /dev/cdrecorder or /media/cdrecorder on my system
The cdwriter is installed as /dev/cdrom0.
Did these things change from kernel 2.4 to 2.6?

K3B lists the cd-writer as reading device with option "writes CD-RWs" selected (but "writes CD-R" deselectd). ??

---

### Post by grj on 2005-02-13
You said the dios sees the drives correctly. Are you sure that none of them, especially the new one is jumpered as cable select. I have had problems with linux in the past with that. Verify that the jumpers are set to master/slave.

---

### Post by jaybee99 on 2005-02-13
Tthe jumpers are set to master/slave and I disconnected 2nd hd for now - what's more, I can burn CDs from Knoppix - are there settings I can copy from Knoppix to fix ubuntu? fstab won't help me, cos it's not a problem in mounting the device, it doesn't exist in the first place.

To clarify, it's not just that I can't burn CDs in ubuntu, I can't use the CDRW drive at all...

---

### Post by jaybee99 on 2005-02-17
I have removed the option hdc=ide-scsi from grub's menu.lst after being told it's not needed with 2.6 kernel and just to see if that was having an effect and now dmesg has a line that says

ide-cd: ignoring drive hdc

why is this? here is dmesg in full:

```

Linux version 2.6.8.1-4-386 (buildd@terranova) (gcc version 3.3.4 (Debian 1:3.3.4-9ubuntu5)) #1 Tue Dec 14 12:10:51 UTC 2004
BIOS-provided physical RAM map:
 BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
 BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
 BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
 BIOS-e820: 0000000000100000 - 000000001dff0000 (usable)
 BIOS-e820: 000000001dff0000 - 000000001dff3000 (ACPI NVS)
 BIOS-e820: 000000001dff3000 - 000000001e000000 (ACPI data)
 BIOS-e820: 00000000ffff0000 - 0000000100000000 (reserved)
479MB LOWMEM available.
found SMP MP-table at 000f6640
On node 0 totalpages: 122864
  DMA zone: 4096 pages, LIFO batch:1
  Normal zone: 118768 pages, LIFO batch:16
  HighMem zone: 0 pages, LIFO batch:1
DMI 2.2 present.
ACPI: RSDP (v000 VIA694                                ) @ 0x000f8010
ACPI: RSDT (v001 VIA694 MSI ACPI 0x42302e31 AWRD 0x00000000) @ 0x1dff3000
ACPI: FADT (v001 VIA694 MSI ACPI 0x42302e31 AWRD 0x00000000) @ 0x1dff3040
ACPI: MADT (v001 VIA694 MSI ACPI 0x42302e31 AWRD 0x00000000) @ 0x1dff5f80
ACPI: DSDT (v001 VIA694 AWRDACPI 0x00001000 MSFT 0x0100000c) @ 0x00000000
ACPI: PM-Timer IO Port: 0x4008
ACPI: Local APIC address 0xfee00000
ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
Processor #0 6:8 APIC version 16
ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
IOAPIC[0]: Assigned apic_id 2
IOAPIC[0]: apic_id 2, version 17, address 0xfec00000, GSI 0-23
ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 dfl dfl)
ACPI: IRQ0 used by override.
ACPI: IRQ2 used by override.
ACPI: IRQ9 used by override.
ACPI: IRQ11 used by override.
Enabling APIC mode:  Flat.  Using 1 I/O APICs
Using ACPI (MADT) for SMP configuration information
Built 1 zonelists
Kernel command line: root=/dev/hda5 ro quiet splash
Initializing CPU#0
PID hash table entries: 2048 (order 11: 16384 bytes)
Detected 1800.859 MHz processor.
Using pmtmr for high-res timesource
Console: colour VGA+ 80x25
Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
Memory: 479740k/491456k available (1336k kernel code, 10928k reserved, 732k data, 204k init, 0k highmem)
Checking if this processor honours the WP bit even in supervisor mode... Ok.
Calibrating delay loop... 3563.52 BogoMIPS
Security Scaffold v1.0.0 initialized
Mount-cache hash table entries: 512 (order: 0, 4096 bytes)
CPU: After generic identify, caps: 0383fbff c1c3fbff 00000000 00000000
CPU: After vendor identify, caps:  0383fbff c1c3fbff 00000000 00000000
CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
CPU: L2 Cache: 256K (64 bytes/line)
CPU: After all inits, caps:        0383fbff c1c3fbff 00000000 00000020
CPU: AMD Athlon(tm) XP 2200+ stepping 00
Enabling fast FPU save and restore... done.
Enabling unmasked SIMD FPU exception support... done.
Checking 'hlt' instruction... OK.
Checking for popad bug... OK.
enabled ExtINT on CPU#0
ESR value before enabling vector: 00000000
ESR value after enabling vector: 00000000
ENABLING IO-APIC IRQs
init IO_APIC IRQs
 IO-APIC (apicid-pin) 2-0, 2-16, 2-17, 2-18, 2-19, 2-20, 2-21, 2-22, 2-23 not connected.
..TIMER: vector=0x31 pin1=2 pin2=-1
Using local APIC timer interrupts.
calibrating APIC timer ...
..... CPU clock speed is 1799.0634 MHz.
..... host bus clock speed is 266.0612 MHz.
checking if image is initramfs...it isn't (ungzip failed); looks like an initrd
Freeing initrd memory: 4136k freed
NET: Registered protocol family 16
EISA bus registered
PCI: PCI BIOS revision 2.10 entry at 0xfb8b0, last bus=1
PCI: Using configuration type 1
mtrr: v2.0 (20020519)
ACPI: Subsystem revision 20040816
ACPI: Interpreter enabled
ACPI: Using IOAPIC for interrupt routing
ACPI: PCI Root Bridge [PCI0] (00:00)
PCI: Probing PCI hardware (bus 00)
ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
ACPI: PCI Interrupt Link [LNKA] (IRQs 1 *3 4 5 6 7 10 11 12 14 15)
ACPI: PCI Interrupt Link [LNKB] (IRQs 1 3 4 5 6 7 *10 11 12 14 15)
ACPI: PCI Interrupt Link [LNKC] (IRQs 1 3 4 5 6 7 10 *11 12 14 15)
ACPI: PCI Interrupt Link [LNKD] (IRQs 1 3 4 5 6 7 10 11 12 14 15) *9
Linux Plug and Play Support v0.97 (c) Adam Belay
PnPBIOS: Scanning system for PnP BIOS support...
PnPBIOS: Found PnP BIOS installation structure at 0xc00fc370
PnPBIOS: PnP BIOS version 1.0, entry 0xf0000:0xc3a0, dseg 0xf0000
PnPBIOS: 14 nodes reported by PnP BIOS; 14 recorded by driver
PCI: Using ACPI for IRQ routing
ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 10
ACPI: PCI interrupt 0000:00:07.2[D] -> GSI 10 (level, low) -> IRQ 10
ACPI: PCI interrupt 0000:00:07.3[D] -> GSI 10 (level, low) -> IRQ 10
ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 11
ACPI: PCI interrupt 0000:00:07.5[C] -> GSI 11 (level, low) -> IRQ 11
ACPI: PCI interrupt 0000:00:08.0[A] -> GSI 16 (level, low) -> IRQ 169
ACPI: PCI interrupt 0000:00:09.0[A] -> GSI 17 (level, low) -> IRQ 177
ACPI: PCI interrupt 0000:00:0a.0[A] -> GSI 18 (level, low) -> IRQ 185
ACPI: PCI interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 169
number of MP IRQ sources: 15.
number of IO-APIC #2 registers: 24.
testing the IO APIC.......................
IO APIC #2......
.... register #00: 02000000
.......    : physical APIC id: 02
.......    : Delivery Type: 0
.......    : LTS          : 0
.... register #01: 00178011
.......     : max redirection entries: 0017
.......     : PRQ implemented: 1
.......     : IO APIC version: 0011
.... register #02: 00000000
.......     : arbitration: 00
.... IRQ redirection table:
 NR Log Phy Mask Trig IRR Pol Stat Dest Deli Vect:   
 00 000 00  1    0    0   0   0    0    0    00
 01 001 01  0    0    0   0   0    1    1    39
 02 001 01  0    0    0   0   0    1    1    31
 03 001 01  0    0    0   0   0    1    1    41
 04 001 01  0    0    0   0   0    1    1    49
 05 001 01  0    0    0   0   0    1    1    51
 06 001 01  0    0    0   0   0    1    1    59
 07 001 01  0    0    0   0   0    1    1    61
 08 001 01  0    0    0   0   0    1    1    69
 09 001 01  0    0    0   0   0    1    1    71
 0a 001 01  1    1    0   1   0    1    1    79
 0b 001 01  0    1    0   1   0    1    1    81
 0c 001 01  0    0    0   0   0    1    1    89
 0d 001 01  0    0    0   0   0    1    1    91
 0e 001 01  0    0    0   0   0    1    1    99
 0f 001 01  0    0    0   0   0    1    1    A1
 10 001 01  1    1    0   1   0    1    1    A9
 11 001 01  1    1    0   1   0    1    1    B1
 12 001 01  1    1    0   1   0    1    1    B9
 13 000 00  1    0    0   0   0    0    0    00
 14 000 00  1    0    0   0   0    0    0    00
 15 000 00  1    0    0   0   0    0    0    00
 16 000 00  1    0    0   0   0    0    0    00
 17 000 00  1    0    0   0   0    0    0    00
Using vector-based indexing
IRQ to pin mappings:
IRQ0 -> 0:2
IRQ1 -> 0:1
IRQ3 -> 0:3
IRQ4 -> 0:4
IRQ5 -> 0:5
IRQ6 -> 0:6
IRQ7 -> 0:7
IRQ8 -> 0:8
IRQ9 -> 0:9
IRQ10 -> 0:10
IRQ11 -> 0:11
IRQ12 -> 0:12
IRQ13 -> 0:13
IRQ14 -> 0:14
IRQ15 -> 0:15
IRQ169 -> 0:16
IRQ177 -> 0:17
IRQ185 -> 0:18
.................................... done.
VFS: Disk quotas dquot_6.5.1
Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
devfs: 2004-01-31 Richard Gooch (rgooch@atnf.csiro.au)
devfs: boot_options: 0x0
Initializing Cryptographic API
Applying VIA southbridge workaround.
PCI: Enabling Via external APIC routing
PCI: Via IRQ fixup for 0000:00:07.2, from 9 to 10
PCI: Via IRQ fixup for 0000:00:07.3, from 9 to 10
isapnp: Scanning for PnP cards...
isapnp: No Plug & Play device found
Serial: 8250/16550 driver $Revision: 1.90 $ 54 ports, IRQ sharing enabled
ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
ACPI: PCI interrupt 0000:00:08.0[A] -> GSI 16 (level, low) -> IRQ 169
ttyS53 at I/O 0xdc28 (irq = 169) is a 8250
ttyS1 at I/O 0xdc40 (irq = 169) is a 8250
ttyS2 at I/O 0xdc50 (irq = 169) is a 8250
ttyS3 at I/O 0xdc60 (irq = 169) is a 8250
ttyS4 at I/O 0xdc70 (irq = 169) is a 8250
RAMDISK driver initialized: 16 RAM disks of 8192K size 1024 blocksize
serio: i8042 AUX port at 0x60,0x64 irq 12
serio: i8042 KBD port at 0x60,0x64 irq 1
input: AT Translated Set 2 keyboard on isa0060/serio0
EISA: Probing bus 0 at eisa0
Cannot allocate resource for EISA slot 4
Cannot allocate resource for EISA slot 5
EISA: Detected 0 cards.
NET: Registered protocol family 2
IP: routing cache hash table of 4096 buckets, 32Kbytes
TCP: Hash tables configured (established 32768 bind 65536)
NET: Registered protocol family 8
NET: Registered protocol family 20
ACPI: (supports S0 S3 S4 S5)
ACPI wakeup devices: 
SLPB PCI0 USB0 USB1 MODM UAR1 LPT1 
RAMDISK: cramfs filesystem found at block 0
RAMDISK: Loading 4136 blocks [1 disk] into ram disk... |/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-done.
VFS: Mounted root (cramfs filesystem) readonly.
Freeing unused kernel memory: 204k freed
vesafb: probe of vesafb0 failed with error -6
ACPI: Processor [CPU0] (supports C1)
NET: Registered protocol family 1
Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
VP_IDE: IDE controller at PCI slot 0000:00:07.1
VP_IDE: chipset revision 6
VP_IDE: not 100% native mode: will probe irqs later
VP_IDE: VIA vt82c686b (rev 40) IDE UDMA100 controller on pci0000:00:07.1
    ide0: BM-DMA at 0xc000-0xc007, BIOS settings: hda:DMA, hdb:pio
    ide1: BM-DMA at 0xc008-0xc00f, BIOS settings: hdc:DMA, hdd:DMA
hda: ST3120020A, ATA DISK drive
Using anticipatory io scheduler
ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
hda: max request size: 128KiB
hda: Host Protected Area detected.
	current capacity is 231345088 sectors (118448 MB)
	native  capacity is 234441648 sectors (120034 MB)
hda: 231345088 sectors (118448 MB) w/1024KiB Cache, CHS=65535/16/63, UDMA(100)
 /dev/ide/host0/bus0/target0/lun0: p1 p2 < p5 p6 > p3 p4
hdc: LITE-ON LTR-52327S, ATAPI CD/DVD-ROM drive
hdd: ATAPI DVD-ROM 16XMax, ATAPI CD/DVD-ROM drive
ide1 at 0x170-0x177,0x376 on irq 15
kjournald starting.  Commit interval 5 seconds
EXT3-fs: mounted filesystem with ordered data mode.
Adding 1020076k swap on /dev/hda6.  Priority:-1 extents:1
EXT3 FS on hda5, internal journal
input: ImExPS/2 Generic Explorer Mouse on isa0060/serio1
mice: PS/2 mouse device common for all mice
ts: Compaq touchscreen protocol output
ide-cd: ignoring drive hdc
hdd: ATAPI 48X DVD-ROM drive, 512kB Cache, UDMA(33)
Uniform CD-ROM driver Revision: 3.20
parport0: PC-style at 0x378 [PCSPP,EPP]
parport_pc: Via 686A parallel port: io=0x378
lp0: using parport0 (polling).
Capability LSM initialized
device-mapper: 4.1.0-ioctl (2003-12-10) initialised: dm@uk.sistina.com
md: md driver 0.90.0 MAX_MD_DEVS=256, MD_SB_DISKS=27
cdrom: open failed.
kjournald starting.  Commit interval 5 seconds
EXT3 FS on hda4, internal journal
EXT3-fs: mounted filesystem with ordered data mode.
kjournald starting.  Commit interval 5 seconds
EXT3 FS on hda3, internal journal
EXT3-fs: mounted filesystem with ordered data mode.
Real Time Clock Driver v1.12
input: PC Speaker
inserting floppy driver for 2.6.8.1-4-386
Floppy drive(s): fd0 is 1.44M
FDC 0 is a post-1991 82077
Linux agpgart interface v0.100 (c) Dave Jones
agpgart: Detected VIA Twister-K/KT133x/KM133 chipset
agpgart: Maximum main memory to use for agp memory: 409M
agpgart: AGP aperture is 64M @ 0xd8000000
cpci_hotplug: CompactPCI Hot Plug Core version: 0.2
pci_hotplug: PCI Hot Plug PCI Core version: 0.5
shpchp: acpi_shpchprm:\_SB_.PCI0 evaluate _BBN fail=0x5
shpchp: acpi_shpchprm:get_device PCI ROOT HID fail=0x5
pciehp: acpi_pciehprm:\_SB_.PCI0 evaluate _BBN fail=0x5
pciehp: acpi_pciehprm:get_device PCI ROOT HID fail=0x5
usbcore: registered new driver usbfs
usbcore: registered new driver hub
USB Universal Host Controller Interface driver v2.2
ACPI: PCI interrupt 0000:00:07.2[D] -> GSI 10 (level, low) -> IRQ 10
uhci_hcd 0000:00:07.2: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller
uhci_hcd 0000:00:07.2: irq 10, io base 0000c400
uhci_hcd 0000:00:07.2: new USB bus registered, assigned bus number 1
hub 1-0:1.0: USB hub found
hub 1-0:1.0: 2 ports detected
ACPI: PCI interrupt 0000:00:07.3[D] -> GSI 10 (level, low) -> IRQ 10
uhci_hcd 0000:00:07.3: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (#2)
uhci_hcd 0000:00:07.3: irq 10, io base 0000c800
uhci_hcd 0000:00:07.3: new USB bus registered, assigned bus number 2
hub 2-0:1.0: USB hub found
hub 2-0:1.0: 2 ports detected
usb 1-1: new full speed USB device using address 2
drivers/usb/class/usblp.c: usblp0: USB Bidirectional printer dev 2 if 0 alt 0 proto 2 vid 0x03F0 pid 0x7004
usbcore: registered new driver usblp
drivers/usb/class/usblp.c: v0.13: USB Printer Device Class driver
ACPI: PCI interrupt 0000:00:07.5[C] -> GSI 11 (level, low) -> IRQ 11
PCI: Setting latency timer of device 0000:00:07.5 to 64
8139too Fast Ethernet driver 0.9.27
ACPI: PCI interrupt 0000:00:0a.0[A] -> GSI 18 (level, low) -> IRQ 185
eth0: RealTek RTL8139 at 0xe400, 00:50:fc:9d:4b:9a, IRQ 185
eth0:  Identified 8139 chip type 'RTL-8100B/8139D'
8139cp: 10/100 PCI Ethernet driver v1.2 (Mar 22, 2004)
ndiswrapper version 0.10 loaded (preempt=yes,smp=no)
ACPI: PCI interrupt 0000:00:09.0[A] -> GSI 17 (level, low) -> IRQ 177
ndiswrapper: using irq 177
wlan0: ndiswrapper ethernet device 00:30:bd:4f:c5:58 using driver rtl8180.sys
ndiswrapper device wlan0 supports WPA with AES/CCMP and TKIP ciphers
ndiswrapper: driver rtl8180.sys (Realtek,04/29/2004,5.169.0429.2004) added
NET: Registered protocol family 17
NET: Registered protocol family 10
Disabled Privacy Extensions on device c02cc0c0(lo)
IPv6 over IPv4 tunneling driver
ACPI: Power Button (FF) [PWRF]
ACPI: Sleep Button (CM) [SLPB]
wlan0: no IPv6 routers present

```

---

### Post by ametade on 2005-03-02
I'm having the same problem with a Lite-on LTR-32123S CD-RW drive...

---

### Post by jaybee99 on 2005-03-03
good luck pal, I'm afraid to say I ended up re-installing the OS  :???: it was the last thing I wanted to do, but I needed to fix it and it's fixed now...

---

