---
title: "USB STICK Mount issue"
date: 2005-10-05
forum: Hardware &amp; Laptops
---

### Post by Shin_Gouki on 2005-10-05
Hello there!
I have an USB Stick Mount Issue(OTI flashdisk something model)! I'using ICE WM on a Ubuntu 5.04 Server install.
I tried varied mount commands i "think" i just need the right device number so that i may used it in the mount command here my mount command:
I want to use this example command:

mount -t /vfat/dev/sda1 /home/NAME/ORDNER" 

my problem is i dont know the device "name/nr" assigned from the system towards the disk.
excerpt from: ls -lisa on /dev directory:
5816 0 brw-r-----   1 root      plugdev     8,   0 2005-10-05 15:32 sdaount issue

someone nice told me yesterday that i may find this needed information through the command "dmesg" this is the out put:

Linux version 2.6.10-5-386 (buildd@terranova) (gcc version 3.3.5 (Debian 1:3.3.5-8ubuntu2)) #1 Tue Apr 5 12:12:40 UTC 2005
BIOS-provided physical RAM map:
 BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
 BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
 BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
 BIOS-e820: 0000000000100000 - 0000000008000000 (usable)
 BIOS-e820: 00000000ffff0000 - 0000000100000000 (reserved)
128MB LOWMEM available.
On node 0 totalpages: 32768
  DMA zone: 4096 pages, LIFO batch:1
  Normal zone: 28672 pages, LIFO batch:7
  HighMem zone: 0 pages, LIFO batch:1
DMI 2.0 present.
ACPI: Unable to locate RSDP
Built 1 zonelists
Kernel command line: root=/dev/hda1 ro quiet splash
No local APIC present or hardware disabled
mapped APIC to ffffd000 (01102000)
Initializing CPU#0
PID hash table entries: 1024 (order: 10, 16384 bytes)
Detected 233.888 MHz processor.
Using tsc for high-res timesource
Console: colour VGA+ 80x25
Dentry cache hash table entries: 32768 (order: 5, 131072 bytes)
Inode-cache hash table entries: 16384 (order: 4, 65536 bytes)
Memory: 122396k/131072k available (1436k kernel code, 8132k reserved, 754k data, 224k init, 0k highmem)
Checking if this processor honours the WP bit even in supervisor mode... Ok.
Calibrating delay loop... 460.80 BogoMIPS (lpj=230400)
Security Framework v1.0.0 initialized
SELinux:  Disabled at boot.
Mount-cache hash table entries: 512 (order: 0, 4096 bytes)
CPU: After generic identify, caps: 008001bf 00000000 00000000 00000000 00000000 00000000
CPU: After vendor identify, caps: 008001bf 00000000 00000000 00000000 00000000 00000000
Intel Pentium with F0 0F bug - workaround enabled.
CPU: After all inits, caps: 008001bf 00000000 00000000 00000000 00000000 00000000
CPU: Intel Pentium MMX stepping 03
Checking 'hlt' instruction... OK.
Checking for popad bug... OK.
checking if image is initramfs...it isn't (bad gzip magic numbers); looks like an initrd
Freeing initrd memory: 4248k freed
NET: Registered protocol family 16
EISA bus registered
PCI: PCI BIOS revision 2.10 entry at 0xf0510, last bus=0
PCI: Using configuration type 1
mtrr: v2.0 (20020519)
ACPI: Subsystem revision 20050211
ACPI: Interpreter disabled.
Linux Plug and Play Support v0.97 (c) Adam Belay
pnp: PnP ACPI: disabled
PnPBIOS: Scanning system for PnP BIOS support...
PnPBIOS: Found PnP BIOS installation structure at 0xc00fcf10
PnPBIOS: PnP BIOS version 1.0, entry 0xf0000:0xcf40, dseg 0xf0000
PnPBIOS: 15 nodes reported by PnP BIOS; 15 recorded by driver
PCI: Probing PCI hardware
PCI: Probing PCI hardware (bus 00)
PCI: Using IRQ router PIIX/ICH [8086/7110] at 0000:00:01.0
pnp: 00:0f: ioport range 0x290-0x297 has been reserved
pnp: 00:0f: ioport range 0xe400-0xe43f has been reserved
pnp: 00:0f: ioport range 0xe800-0xe83f could not be reserved
audit: initializing netlink socket (disabled)
audit(1128519097.546:0): initialized
VFS: Disk quotas dquot_6.5.1
Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
devfs: 2004-01-31 Richard Gooch (rgooch@atnf.csiro.au)
devfs: boot_options: 0x0
Initializing Cryptographic API
Limiting direct PCI/PCI transfers.
isapnp: Scanning for PnP cards...
isapnp: No Plug & Play device found
serio: i8042 AUX port at 0x60,0x64 irq 12
serio: i8042 KBD port at 0x60,0x64 irq 1
Serial: 8250/16550 driver $Revision: 1.90 $ 54 ports, IRQ sharing enabled
ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
io scheduler noop registered
io scheduler anticipatory registered
io scheduler deadline registered
io scheduler cfq registered
RAMDISK driver initialized: 16 RAM disks of 8192K size 1024 blocksize
input: AT Translated Set 2 keyboard on isa0060/serio0
EISA: Probing bus 0 at eisa0
EISA: Detected 0 cards.
NET: Registered protocol family 2
IP: routing cache hash table of 1024 buckets, 8Kbytes
TCP: Hash tables configured (established 8192 bind 16384)
NET: Registered protocol family 8
NET: Registered protocol family 20
Restarting tasks...<6> Strange, kswapd0 not stopped
 Strange, kpnpbiosd not stopped
 Strange, kseriod not stopped
 done
RAMDISK: cramfs filesystem found at block 0
RAMDISK: Loading 4248KiB [1 disk] into ram disk... |/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/-\|/done.
VFS: Mounted root (cramfs filesystem) readonly.
Freeing unused kernel memory: 224k freed
NET: Registered protocol family 1
Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
PIIX4: IDE controller at PCI slot 0000:00:01.1
PIIX4: chipset revision 1
PIIX4: not 100% native mode: will probe irqs later
    ide0: BM-DMA at 0xe000-0xe007, BIOS settings: hda:DMA, hdb:pio
    ide1: BM-DMA at 0xe008-0xe00f, BIOS settings: hdc:DMA, hdd:DMA
Probing IDE interface ide0...
hda: ST34311A, ATA DISK drive
elevator: using anticipatory as default io scheduler
ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
hda: max request size: 128KiB
hda: 8452080 sectors (4327 MB) w/256KiB Cache, CHS=8944/15/63, UDMA(33)
hda: cache flushes not supported
 /dev/ide/host0/bus0/target0/lun0: p1 p2 < p5 >
Probing IDE interface ide1...
hdc: CD-524EA, ATAPI CD/DVD-ROM drive
hdd: R/RW 4x4x32, ATAPI CD/DVD-ROM drive
ide1 at 0x170-0x177,0x376 on irq 15
Probing IDE interface ide2...
Probing IDE interface ide3...
Probing IDE interface ide4...
Probing IDE interface ide5...
Stopping tasks: ==|
Freeing memory...  -\|/done (457 pages freed)
Restarting tasks... done
EXT3-fs: INFO: recovery required on readonly filesystem.
EXT3-fs: write access will be enabled during recovery.
EXT3-fs: hda1: orphan cleanup on readonly fs
kjournald starting.  Commit interval 5 seconds
ext3_orphan_cleanup: deleting unreferenced inode 310829
ext3_orphan_cleanup: deleting unreferenced inode 310809
ext3_orphan_cleanup: deleting unreferenced inode 250266
ext3_orphan_cleanup: deleting unreferenced inode 250265
ext3_orphan_cleanup: deleting unreferenced inode 250264
ext3_orphan_cleanup: deleting unreferenced inode 311387
ext3_orphan_cleanup: deleting unreferenced inode 310848
ext3_orphan_cleanup: deleting unreferenced inode 311331
ext3_orphan_cleanup: deleting unreferenced inode 311327
ext3_orphan_cleanup: deleting unreferenced inode 311326
ext3_orphan_cleanup: deleting unreferenced inode 311325
ext3_orphan_cleanup: deleting unreferenced inode 245154
ext3_orphan_cleanup: deleting unreferenced inode 259623
EXT3-fs: hda1: 13 orphan inodes deleted
EXT3-fs: recovery complete.
EXT3-fs: mounted filesystem with ordered data mode.
Adding 208804k swap on /dev/hda5.  Priority:-1 extents:1
EXT3 FS on hda1, internal journal
hdc: ATAPI 24X CD-ROM drive, 128kB Cache
Uniform CD-ROM driver Revision: 3.20
hdd: ATAPI 32X CD-ROM CD-R/RW drive, 2048kB Cache
parport: PnPBIOS parport detected.
parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,EPP,ECP,DMA]
lp0: using parport0 (interrupt-driven).
mice: PS/2 mouse device common for all mice
input: ImPS/2 Generic Wheel Mouse on isa0060/serio1
ts: Compaq touchscreen protocol output
Capability LSM initialized
device-mapper: 4.3.0-ioctl (2004-09-30) initialised: [email]dm-devel@redhat.com[/email]
md: md driver 0.90.1 MAX_MD_DEVS=256, MD_SB_DISKS=27
cdrom: open failed.
cdrom: open failed.
inserting floppy driver for 2.6.10-5-386
Floppy drive(s): fd0 is 1.44M
FDC 0 is a post-1991 82077
Real Time Clock Driver v1.12
input: PC Speaker
usbcore: registered new driver usbfs
usbcore: registered new driver hub
USB Universal Host Controller Interface driver v2.2
PCI: Found IRQ 9 for device 0000:00:01.2
uhci_hcd 0000:00:01.2: Intel Corp. 82371AB/EB/MB PIIX4 USB
uhci_hcd 0000:00:01.2: irq 9, io base 0xd800
uhci_hcd 0000:00:01.2: new USB bus registered, assigned bus number 1
hub 1-0:1.0: USB hub found
hub 1-0:1.0: 2 ports detected
usb 1-1: new full speed USB device using uhci_hcd and address 2
usb 1-2: new full speed USB device using uhci_hcd and address 3
SCSI subsystem initialized
Initializing USB Mass Storage driver...
scsi0 : SCSI emulation for USB Mass Storage devices
usbcore: registered new driver usb-storage
USB Mass Storage support registered.
usb-storage: device found at 2
usb-storage: waiting for device to settle before scanning
drivers/usb/net/rtl8150.c: rtl8150 based usb-ethernet driver v0.6.2 (2004/08/27)
drivers/usb/net/rtl8150.c: eth%d: rtl8150 is detected
usbcore: registered new driver rtl8150
piix4_smbus 0000:00:01.3: Found 0000:00:01.3 device
NET: Registered protocol family 17
  Vendor: OTi       Model: Flash Disk        Rev: 2.00
  Type:   Direct-Access                      ANSI SCSI revision: 02
usb-storage: device scan complete
sda: Unit Not Ready, sense:
Current : sense key Unit Attention
Additional sense: Not ready to ready change, medium may have changed
sda : READ CAPACITY failed.
sda : status=1, message=00, host=0, driver=08 
Current sd: sense key Unit Attention
Additional sense: Not ready to ready change, medium may have changed
sda: test WP failed, assume Write Enabled
sda: assuming drive cache: write through
sda: Unit Not Ready, sense:
Current : sense key Unit Attention
Additional sense: Not ready to ready change, medium may have changed
sda : READ CAPACITY failed.
sda : status=1, message=00, host=0, driver=08 
Current sd: sense key Unit Attention
Additional sense: Not ready to ready change, medium may have changed
sda: test WP failed, assume Write Enabled
sda: assuming drive cache: write through
sda: Unit Not Ready, sense:
Current : sense key Unit Attention
Additional sense: Not ready to ready change, medium may have changed
sda : READ CAPACITY failed.
sda : status=1, message=00, host=0, driver=08 
Current sd: sense key Unit Attention
Additional sense: Not ready to ready change, medium may have changed
sda: test WP failed, assume Write Enabled
sda: assuming drive cache: write through
 /dev/scsi/host0/bus0/target0/lun0:end_request: I/O error, dev sda, sector 0
Buffer I/O error on device sda, logical block 0
Buffer I/O error on device sda, logical block 0
 unable to read partition table
Attached scsi removable disk sda at scsi0, channel 0, id 0, lun 0
PCI: Found IRQ 11 for device 0000:00:0c.0
NET: Registered protocol family 10
Disabled Privacy Extensions on device c02f0500(lo)
IPv6 over IPv4 tunneling driver
eth1: no IPv6 routers present
-----------------------------
so Who is able to tell me the device Number /name of my USB (OTI somehting..) disk, ? 
But it would be even more nice if someone could give me a hint on the, A Correct mount command.

wbr Shin Gouki

---

### Post by diebels on 2005-10-05
maybe some broken partition table, try {
sudo -s
fdisk /dev/sda
inside the fdisk program, remove all partitions, write and quit.
mkfs.vfat /dev/sda
mount -t vfat /dev/sda /what/ever/dir (should be automounted too)
}

---

### Post by Shin_Gouki on 2005-10-06
THX diebels for reply! i think thats it!

here the output eythian:
Disk /dev/sda: 127 MB, 127926272 bytes
16 heads, 32 sectors/track, 488 cylinders
Units = cylinders of 512 * 512 = 262144 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         488      124911+   6  FAT16
Partition 1 has different physical/logical endings:
     phys=(486, 15, 32) logical=(487, 15, 31)
Diffrent phy/log Endings not good eh? :/
wbr Shin Gouki

---

