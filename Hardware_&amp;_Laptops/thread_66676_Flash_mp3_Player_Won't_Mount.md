---
title: "Flash mp3 Player Won't Mount"
date: 2005-09-18
forum: Hardware &amp; Laptops
---

### Post by palsyboy on 2005-09-18
I received my long-anticipated [Sandisk mp3 player](http://www.newegg.com/Product/Product.asp?Item=N82E16855125004)  in the mail today.  Unfortunately, it won't mount.  The Storage Media applet doesn't recognize it, even though it recognizes my old [MSI MegaStick 128](http://www.ciao.co.uk/MSI_MegaStick_128__6200789)  with no problem.  I've run dmesg to see about the device's possible address, but I can't find anything related to the player in the output:
```
# dmesg
ournald starting.  Commit interval 5 seconds
EXT3-fs: hda3: 1 orphan inode deleted
EXT3-fs: recovery complete.
EXT3-fs: mounted filesystem with ordered data mode.
Adding 979956k swap on /dev/hda2.  Priority:-1 extents:1
EXT3 FS on hda3, internal journal
hdc: ATAPI 48X DVD-ROM drive, 512kB Cache
Uniform CD-ROM driver Revision: 3.20
hdd: ATAPI 40X CD-ROM CD-R/RW drive, 4096kB Cache
parport: PnPBIOS parport detected.
parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
lp0: using parport0 (interrupt-driven).
mice: PS/2 mouse device common for all mice
input: ImPS/2 Generic Wheel Mouse on isa0060/serio1
ts: Compaq touchscreen protocol output
ieee1394: Initialized config rom entry `ip1394'
SCSI subsystem initialized
sbp2: $Rev: 1219 $ Ben Collins <bcollins@debian.org>
Capability LSM initialized
device-mapper: 4.3.0-ioctl (2004-09-30) initialised: dm-devel@redhat.com
md: md driver 0.90.1 MAX_MD_DEVS=256, MD_SB_DISKS=27
cdrom: open failed.
cdrom: open failed.
kjournald starting.  Commit interval 5 seconds
EXT3 FS on hda1, internal journal
EXT3-fs: mounted filesystem with ordered data mode.
kjournald starting.  Commit interval 5 seconds
EXT3 FS on hda5, internal journal
EXT3-fs: mounted filesystem with ordered data mode.
kjournald starting.  Commit interval 5 seconds
EXT3 FS on hda6, internal journal
EXT3-fs: mounted filesystem with ordered data mode.
Real Time Clock Driver v1.12
input: PC Speaker
inserting floppy driver for 2.6.10-5-386
Floppy drive(s): fd0 is 1.44M
FDC 0 is a post-1991 82077
Linux agpgart interface v0.100 (c) Dave Jones
agpgart: Detected VIA KT400/KT400A/KT600 chipset
agpgart: Maximum main memory to use for agp memory: 439M
agpgart: AGP aperture is 64M @ 0xf8000000
cpci_hotplug: CompactPCI Hot Plug Core version: 0.2
pci_hotplug: PCI Hot Plug PCI Core version: 0.5
shpchp: acpi_shpchprm:\_SB_.PCI0 evaluate _BBN fail=0x5
shpchp: acpi_shpchprm:get_device PCI ROOT HID fail=0x5
pciehp: acpi_pciehprm:\_SB_.PCI0 evaluate _BBN fail=0x5
pciehp: acpi_pciehprm:get_device PCI ROOT HID fail=0x5
PCI: Enabling device 0000:00:0e.0 (0004 -> 0005)
ACPI: PCI interrupt 0000:00:0e.0[A] -> GSI 17 (level, low) -> IRQ 17
PCI: Enabling device 0000:00:0e.1 (0004 -> 0005)
gameport: pci0000:00:0e.1 speed 1242 kHz
ohci1394: $Rev: 1223 $ Ben Collins <bcollins@debian.org>
PCI: Enabling device 0000:00:0e.2 (0014 -> 0016)
ACPI: PCI interrupt 0000:00:0e.2[B] -> GSI 18 (level, low) -> IRQ 18
ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[18]  MMIO=[ed800000-ed8007ff]  Max Packet=[2048]
libata version 1.10 loaded.
sata_via version 1.1
ACPI: PCI interrupt 0000:00:0f.0[B] -> GSI 20 (level, low) -> IRQ 20
sata_via(0000:00:0f.0): routed to hard irq line 4
ata1: SATA max UDMA/133 cmd 0xD000 ctl 0xB802 bmdma 0xA800 irq 20
ata2: SATA max UDMA/133 cmd 0xB400 ctl 0xB002 bmdma 0xA808 irq 20
ata1: no device found (phy stat 00000000)
scsi0 : sata_via
ata2: no device found (phy stat 00000000)
scsi1 : sata_via
usbcore: registered new driver usbfs
usbcore: registered new driver hub
USB Universal Host Controller Interface driver v2.2
ACPI: PCI interrupt 0000:00:10.0[A] -> GSI 21 (level, low) -> IRQ 21
uhci_hcd 0000:00:10.0: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller
uhci_hcd 0000:00:10.0: irq 21, io base 0x9800
uhci_hcd 0000:00:10.0: new USB bus registered, assigned bus number 1
hub 1-0:1.0: USB hub found
hub 1-0:1.0: 2 ports detected
ACPI: PCI interrupt 0000:00:10.1[A] -> GSI 21 (level, low) -> IRQ 21
uhci_hcd 0000:00:10.1: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (#2)
uhci_hcd 0000:00:10.1: irq 21, io base 0x9400
uhci_hcd 0000:00:10.1: new USB bus registered, assigned bus number 2
hub 2-0:1.0: USB hub found
hub 2-0:1.0: 2 ports detected
ACPI: PCI interrupt 0000:00:10.2[B] -> GSI 21 (level, low) -> IRQ 21
uhci_hcd 0000:00:10.2: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (#3)
ieee1394: Host added: ID:BUS[0-00:1023]  GUID[00023c00300495b2]
uhci_hcd 0000:00:10.2: irq 21, io base 0x9000
usb 1-1: new low speed USB device using uhci_hcd and address 2
uhci_hcd 0000:00:10.2: new USB bus registered, assigned bus number 3
hub 3-0:1.0: USB hub found
hub 3-0:1.0: 2 ports detected
ACPI: PCI interrupt 0000:00:10.3[B] -> GSI 21 (level, low) -> IRQ 21
uhci_hcd 0000:00:10.3: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (#4)
uhci_hcd 0000:00:10.3: irq 21, io base 0x8800
uhci_hcd 0000:00:10.3: new USB bus registered, assigned bus number 4
hub 4-0:1.0: USB hub found
hub 4-0:1.0: 2 ports detected
usb 1-2: new full speed USB device using uhci_hcd and address 3
usbcore: registered new driver hiddev
input: USB HID v1.11 Mouse [Logitech USB Receiver] on usb-0000:00:10.0-1
usbcore: registered new driver usbhid
drivers/usb/input/hid-core.c: v2.0:USB HID core driver
ACPI: PCI interrupt 0000:00:10.4[C] -> GSI 21 (level, low) -> IRQ 21
ehci_hcd 0000:00:10.4: VIA Technologies, Inc. USB 2.0
ehci_hcd 0000:00:10.4: irq 21, pci mem 0xec800000
ehci_hcd 0000:00:10.4: new USB bus registered, assigned bus number 5
ehci_hcd 0000:00:10.4: USB 2.0 initialized, EHCI 1.00, driver 26 Oct 2004
drivers/usb/input/hid-core.c: input irq status -84 received
drivers/usb/input/hid-core.c: input irq status -84 received
drivers/usb/input/hid-core.c: input irq status -84 received
drivers/usb/input/hid-core.c: input irq status -84 received
drivers/usb/input/hid-core.c: input irq status -84 received
drivers/usb/input/hid-core.c: input irq status -84 received
drivers/usb/class/usblp.c: can't set desired altsetting 1 on interface 0
usblp: probe of 1-2:1.0 failed with error -5
usbcore: registered new driver usblp
drivers/usb/class/usblp.c: v0.13: USB Printer Device Class driver
drivers/usb/input/hid-core.c: input irq status -84 received
usb 1-1: USB disconnect, address 2
hub 5-0:1.0: USB hub found
hub 5-0:1.0: 8 ports detected
PCI: Enabling device 0000:00:13.2 (0014 -> 0016)
ACPI: PCI interrupt 0000:00:13.2[C] -> GSI 16 (level, low) -> IRQ 16
ehci_hcd 0000:00:13.2: NEC Corporation USB 2.0
ehci_hcd 0000:00:13.2: irq 16, pci mem 0xea800000
ehci_hcd 0000:00:13.2: new USB bus registered, assigned bus number 6
ehci_hcd 0000:00:13.2: USB 2.0 initialized, EHCI 0.95, driver 26 Oct 2004
hub 6-0:1.0: USB hub found
hub 6-0:1.0: 5 ports detected
usb 1-2: USB disconnect, address 3
via82xx: Assuming DXS channels with 48k fixed sample rate.
         Please try dxs_support=1 or dxs_support=4 option
         and report if it works on your machine.
ACPI: PCI interrupt 0000:00:11.5[C] -> GSI 22 (level, low) -> IRQ 22
PCI: Setting latency timer of device 0000:00:11.5 to 64
codec_read: codec 0 is not valid [0xfe0000]
codec_read: codec 0 is not valid [0xfe0000]
codec_read: codec 0 is not valid [0xfe0000]
codec_read: codec 0 is not valid [0xfe0000]
via-rhine.c:v1.10-LK1.2.0-2.6 June-10-2004 Written by Donald Becker
ACPI: PCI interrupt 0000:00:12.0[A] -> GSI 23 (level, low) -> IRQ 23
eth0: VIA Rhine II at 0x8400, 00:11:2f:20:1a:eb, IRQ 23.
eth0: MII PHY found at address 1, status 0x786d advertising 01e1 Link 41e1.
usb 5-5: new high speed USB device using ehci_hcd and address 4
ohci_hcd: 2004 Nov 08 USB 1.1 'Open' Host Controller (OHCI) Driver (PCI)
PCI: Enabling device 0000:00:13.0 (0014 -> 0016)
ACPI: PCI interrupt 0000:00:13.0[A] -> GSI 18 (level, low) -> IRQ 18
ohci_hcd 0000:00:13.0: NEC Corporation USB
ohci_hcd 0000:00:13.0: irq 18, pci mem 0xeb800000
ohci_hcd 0000:00:13.0: new USB bus registered, assigned bus number 7
usb 1-1: new low speed USB device using uhci_hcd and address 4
eth0: link up, 100Mbps, full-duplex, lpa 0x41E1
Initializing USB Mass Storage driver...
input: USB HID v1.11 Mouse [Logitech USB Receiver] on usb-0000:00:10.0-1
usb 1-2: new full speed USB device using uhci_hcd and address 5
drivers/usb/class/usblp.c: usblp0: USB Bidirectional printer dev 5 if 0 alt 1 proto 2 vid 0x03F0 pid 0x0317
scsi2 : SCSI emulation for USB Mass Storage devices
usbcore: registered new driver usb-storage
USB Mass Storage support registered.
hub 7-0:1.0: USB hub found
hub 7-0:1.0: 3 ports detected
usb-storage: device found at 4
usb-storage: waiting for device to settle before scanning
NET: Registered protocol family 17
PCI: Enabling device 0000:00:13.1 (0014 -> 0016)
ACPI: PCI interrupt 0000:00:13.1[B] -> GSI 19 (level, low) -> IRQ 19
ohci_hcd 0000:00:13.1: NEC Corporation USB (#2)
ohci_hcd 0000:00:13.1: irq 19, pci mem 0xeb000000
ohci_hcd 0000:00:13.1: new USB bus registered, assigned bus number 8
hub 8-0:1.0: USB hub found
hub 8-0:1.0: 2 ports detected
NET: Registered protocol family 10
Disabled Privacy Extensions on device c02f0500(lo)
IPv6 over IPv4 tunneling driver
  Vendor: Generic   Model: STORAGE DEVICE    Rev: 0128
  Type:   Direct-Access                      ANSI SCSI revision: 00
  Vendor: Generic   Model: STORAGE DEVICE    Rev: 0128
  Type:   Direct-Access                      ANSI SCSI revision: 00
  Vendor: Generic   Model: STORAGE DEVICE    Rev: 0128
  Type:   Direct-Access                      ANSI SCSI revision: 00
  Vendor: Generic   Model: STORAGE DEVICE    Rev: 0128
  Type:   Direct-Access                      ANSI SCSI revision: 00
usb-storage: device scan complete
Attached scsi removable disk sda at scsi2, channel 0, id 0, lun 0
Attached scsi removable disk sdb at scsi2, channel 0, id 0, lun 1
Attached scsi removable disk sdc at scsi2, channel 0, id 0, lun 2
Attached scsi removable disk sdd at scsi2, channel 0, id 0, lun 3
ACPI: Power Button (FF) [PWRF]
ibm_acpi: ec object not found
apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
apm: overridden by ACPI.
drivers/usb/input/hid-input.c: event field not found
eth0: no IPv6 routers present
usb 5-4: new high speed USB device using ehci_hcd and address 5
scsi3 : SCSI emulation for USB Mass Storage devices
usb-storage: device found at 5
usb-storage: waiting for device to settle before scanning
  Vendor: Maxtor 6  Model: B300R0            Rev:  0 0
  Type:   Direct-Access                      ANSI SCSI revision: 00
SCSI device sde: 586114704 512-byte hdwr sectors (300091 MB)
sde: assuming drive cache: write through
SCSI device sde: 586114704 512-byte hdwr sectors (300091 MB)
sde: assuming drive cache: write through
 /dev/scsi/host3/bus0/target0/lun0: p1 p2 p3 < p5 p6 > p4
Attached scsi disk sde at scsi3, channel 0, id 0, lun 0
usb-storage: device scan complete
UDF-fs: No partition found (1)
UDF-fs: No partition found (1)
Unable to identify CD-ROM format.
Unable to identify CD-ROM format.
FAT: utf8 is not a recommended IO charset for FAT filesystems, filesystem will be case sensitive!
FAT: bogus number of reserved sectors
VFS: Can't find a valid FAT filesystem on dev sde6.
FAT: bogus number of reserved sectors
VFS: Can't find a valid FAT filesystem on dev sde6.
NTFS driver 2.1.22 [Flags: R/O MODULE].
NTFS-fs warning (device sde6): parse_options(): Option iocharset is deprecated. Please use option nls=<charsetname> in the future.
NTFS-fs error (device sde6): read_ntfs_boot_sector(): Primary boot sector is invalid.
NTFS-fs error (device sde6): read_ntfs_boot_sector(): Mount option errors=recover not used. Aborting without trying to recover.
NTFS-fs error (device sde6): ntfs_fill_super(): Not an NTFS volume.
NTFS-fs error (device sde6): read_ntfs_boot_sector(): Primary boot sector is invalid.
NTFS-fs error (device sde6): read_ntfs_boot_sector(): Mount option errors=recover not used. Aborting without trying to recover.
NTFS-fs error (device sde6): ntfs_fill_super(): Not an NTFS volume.
HFS+-fs: unable to find HFS+ superblock
HFS+-fs: unable to find HFS+ superblock
VFS: Can't find a HFS filesystem on dev sde6.
VFS: Can't find a HFS filesystem on dev sde6.
VFS: Can't find ext3 filesystem on dev sde6.
VFS: Can't find ext3 filesystem on dev sde6.
VFS: Can't find an ext2 filesystem on dev sde6.
VFS: Can't find an ext2 filesystem on dev sde6.
ReiserFS: sde6: found reiserfs format "3.6" with standard journal
ReiserFS: sde6: using ordered data mode
ReiserFS: sde6: journal params: device sde6, size 8192, journal first block 18, max trans len 1024, max batch 900, max commit age 30, max trans age 30
ReiserFS: sde6: checking transaction log (sde6)
ReiserFS: sde6: Using r5 hash to sort names
usb 5-4: USB disconnect, address 5
usb 5-4: new high speed USB device using ehci_hcd and address 6
scsi4 : SCSI emulation for USB Mass Storage devices
usb-storage: device found at 6
usb-storage: waiting for device to settle before scanning
  Vendor: Maxtor 6  Model: B300R0            Rev:  0 0
  Type:   Direct-Access                      ANSI SCSI revision: 00
SCSI device sde: 586114704 512-byte hdwr sectors (300091 MB)
sde: assuming drive cache: write through
SCSI device sde: 586114704 512-byte hdwr sectors (300091 MB)
sde: assuming drive cache: write through
 /dev/scsi/host4/bus0/target0/lun0: p1 p2 p3 < p5 p6 > p4
Attached scsi disk sde at scsi4, channel 0, id 0, lun 0
usb-storage: device scan complete
UDF-fs: No partition found (1)
UDF-fs: No partition found (1)
Unable to identify CD-ROM format.
Unable to identify CD-ROM format.
FAT: utf8 is not a recommended IO charset for FAT filesystems, filesystem will be case sensitive!
FAT: bogus number of reserved sectors
VFS: Can't find a valid FAT filesystem on dev sde6.
FAT: bogus number of reserved sectors
VFS: Can't find a valid FAT filesystem on dev sde6.
NTFS-fs warning (device sde6): parse_options(): Option iocharset is deprecated. Please use option nls=<charsetname> in the future.
NTFS-fs error (device sde6): read_ntfs_boot_sector(): Primary boot sector is invalid.
NTFS-fs error (device sde6): read_ntfs_boot_sector(): Mount option errors=recover not used. Aborting without trying to recover.
NTFS-fs error (device sde6): ntfs_fill_super(): Not an NTFS volume.
NTFS-fs error (device sde6): read_ntfs_boot_sector(): Primary boot sector is invalid.
NTFS-fs error (device sde6): read_ntfs_boot_sector(): Mount option errors=recover not used. Aborting without trying to recover.
NTFS-fs error (device sde6): ntfs_fill_super(): Not an NTFS volume.
HFS+-fs: unable to find HFS+ superblock
HFS+-fs: unable to find HFS+ superblock
VFS: Can't find a HFS filesystem on dev sde6.
VFS: Can't find a HFS filesystem on dev sde6.
VFS: Can't find ext3 filesystem on dev sde6.
VFS: Can't find ext3 filesystem on dev sde6.
VFS: Can't find an ext2 filesystem on dev sde6.
VFS: Can't find an ext2 filesystem on dev sde6.
ReiserFS: sde6: found reiserfs format "3.6" with standard journal
ReiserFS: sde6: using ordered data mode
ReiserFS: sde6: journal params: device sde6, size 8192, journal first block 18, max trans len 1024, max batch 900, max commit age 30, max trans age 30
ReiserFS: sde6: checking transaction log (sde6)
ReiserFS: sde6: Using r5 hash to sort names
usb 5-4: USB disconnect, address 6
usb 4-1: new full speed USB device using uhci_hcd and address 2
scsi5 : SCSI emulation for USB Mass Storage devices
usb-storage: device found at 2
usb-storage: waiting for device to settle before scanning
  Vendor: MSI       Model: MS-551X           Rev: 0100
  Type:   Direct-Access                      ANSI SCSI revision: 04
SCSI device sde: 250624 512-byte hdwr sectors (128 MB)
sde: Write Protect is off
sde: Mode Sense: 03 00 00 00
sde: assuming drive cache: write through
SCSI device sde: 250624 512-byte hdwr sectors (128 MB)
sde: Write Protect is off
sde: Mode Sense: 03 00 00 00
sde: assuming drive cache: write through
 /dev/scsi/host5/bus0/target0/lun0: p1
Attached scsi removable disk sde at scsi5, channel 0, id 0, lun 0
usb-storage: device scan complete
usb 4-1: USB disconnect, address 2
```
I don't have a big problem manually mounting things (even if the Storage Media applet has spoiled me since my Gentoo days), but I can't even figure out the device name.  I'm guessing that it uses a FAT32 filesystem, but that doesn't seem to be helping me out, either.

Can someone please point me in the right direction?

---

### Post by palsyboy on 2005-09-20
Nevermind.  It spontaneously started working several days later.

---

