---
title: "[SOLVED] Messed up hard drive, new partition table, no partitions, no work."
date: 2009-01-01
forum: Hardware
---

### Post by mrallaire on 2009-01-01
Happy holidays to all,

I really messed up my hard drive and need help.  I wanted to repartition my hard drive into two partitions.  I wanted a 7GB partition and reinstall Ubuntu there, keeping the rest of my files on the rest of my hard drive in the second partition.  That way when I reformat my computer I don't have to back up my files.  I've been experimenting a lot with the other Ubuntu flavors lately.  

I went into gparted, and could not resize my partition.  So I created a new partition table, knowing it would erase everything.  I was going to reinstall Ubuntu after all, and all my files were copied to a removable drive.  I selected the new partitions I wanted to create, and when I went to apply the changes, it would not work.  

I recently resolved this issue, I had to keep the drive connected, but unmounted.  Ubuntu however, would not let me unmount my currently used drive.  

So I exited everything rebooted my computer with my Puppylinux Live CD, this distro boots entirely into ram.  I had hoped it would work in there.  However with a new partition table on my drive, but no partitions, even Puppylinux would not boot up.

Now nothing I have will work, No Ubuntu, no Puppylinux, nothing.  

The only thing I could think of was connecting the drive to another computer, and as a secondary drive, I would easily be able to reformat it.  

My other computer does not support a SATA drive, so my only recourse was to take apart my removable SATA drive.  I installed my messed up drive in it's place, and now I can use my messed up drive as a removable usb drive.  

Now I'm stuck on trying to get the drive to mount.  It won't automount like all my usb external drives do.

I know I hooked it up properly due to the following:  Both the power and usb connection were unplugged.  I plugged in the power and could hear the drive power up.  After a few seconds, when settled down.  I plugged in the usb coard.  I could here the drive and computer running, so it obviously detected it.  It just won't automount.  

Fdisk -l which lists all drives mounted or unmounted did not show any new drives connected to my computer.  

I'm not too familiar with how to manually mount a drive, but I do know that once mounted the first external hard drive shows up as sdb.  I also recall that the drive was ext3 before I created a new partition.  So I tried:

mount -t ext3 /dev/sdb /mnt/sdb
special drive /dev/sdb does not exist

mount -t vfat /dev/sdb /mnt/sdb
/dev/sdb is not a valid block device

mount -t ext3 /dev/sdb1 /mnt/sdb
/dev/sdb is not a valid block device

I tried a bunch more, but I really don't know enough about mounting to make it work.  

I can't fix the drive unless I can get it mounted!!!

one person said to type dmesg to see what the error is, and I have no clue what any of it means.  But, dmesg was different before and after I connected the drive, and now it is full of errors, and I recognize sdb quite often.  Here is a copy of the dmesg output:

0: quirk: region 0880-08bf claimed by ICH4 GPIO
PCI: Transparent bridge - 0000:00:1e.0
ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCI1._PRT]
ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 9 10 *11 12 15)
ACPI: PCI Interrupt Link [LNKB] (IRQs *3 4 5 6 7 9 10 11 12 15)
ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 *5 6 7 9 10 11 12 15)
ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 9 *10 11 12 15)
ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 *9 10 11 12 15)
ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 9 10 11 12 15) *0, disabled.
ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 9 *10 11 12 15)
ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 *9 10 11 12 15)
Linux Plug and Play Support v0.97 (c) Adam Belay
pnp: PnP ACPI init
ACPI: bus type pnp registered
pnp: PnP ACPI: found 10 devices
ACPI: ACPI bus type pnp unregistered
PnPBIOS: Disabled by ACPI PNP
SCSI subsystem initialized
libata version 3.00 loaded.
PCI: Using ACPI for IRQ routing
PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
system 00:00: iomem range 0x0-0x9ffff could not be reserved
system 00:00: iomem range 0x100000-0xffffff could not be reserved
system 00:00: iomem range 0x1000000-0x1fe6ffff could not be reserved
system 00:00: iomem range 0xc0000-0xfffff could not be reserved
system 00:00: iomem range 0xfec00000-0xfec0ffff could not be reserved
system 00:00: iomem range 0xfee00000-0xfee0ffff could not be reserved
system 00:00: iomem range 0xfed20000-0xfed8ffff could not be reserved
system 00:00: iomem range 0xfecf0000-0xfecf0fff could not be reserved
system 00:00: iomem range 0xffb00000-0xffbfffff could not be reserved
system 00:00: iomem range 0xffc00000-0xffffffff could not be reserved
system 00:09: ioport range 0x800-0x85f has been reserved
system 00:09: ioport range 0xc00-0xc7f has been reserved
system 00:09: ioport range 0x860-0x8ff could not be reserved
PCI: Bridge: 0000:00:1e.0
  IO window: d000-dfff
  MEM window: 0xfea00000-0xfeafffff
  PREFETCH window: disabled.
PCI: Setting latency timer of device 0000:00:1e.0 to 64
NET: Registered protocol family 2
IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
TCP established hash table entries: 16384 (order: 5, 131072 bytes)
TCP bind hash table entries: 16384 (order: 4, 65536 bytes)
TCP: Hash tables configured (established 16384 bind 16384)
TCP reno registered
Unpacking initramfs... done
Simple Boot Flag at 0x7a set to 0x1
NTFS driver 2.1.29 [Flags: R/W].
io scheduler noop registered
io scheduler cfq registered (default)
pci 0000:00:02.0: Boot video device
pci 0000:01:08.0: Firmware left e100 interrupts enabled; disabling
isapnp: Scanning for PnP cards...
isapnp: No Plug & Play device found
Real Time Clock Driver v1.12ac
intel_rng: Firmware space is locked read-only. If you can't or
intel_rng: don't want to disable this in firmware setup, and if
intel_rng: you are certain that your system has a functional
intel_rng: RNG, try using the 'no_fwh_detect' option.
Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
00:07: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
ACPI: PCI Interrupt 0000:01:01.0[A] -> GSI 22 (level, low) -> IRQ 22
0000:01:01.0: ttyS1 at I/O 0xde08 (irq = 22) is a 16450
0000:01:01.0: ttyS2 at I/O 0xde10 (irq = 22) is a 8250
0000:01:01.0: ttyS3 at I/O 0xde18 (irq = 22) is a 16450
Couldn't register serial port 0000:01:01.0: -28
Floppy drive(s): fd0 is 1.44M
FDC 0 is a post-1991 82077
brd: module loaded
loop: module loaded
Driver 'sd' needs updating - please use bus_type methods
Driver 'sr' needs updating - please use bus_type methods
ata_piix 0000:00:1f.1: version 2.12
ACPI: PCI Interrupt 0000:00:1f.1[A] -> GSI 18 (level, low) -> IRQ 18
PCI: Setting latency timer of device 0000:00:1f.1 to 64
scsi0 : ata_piix
scsi1 : ata_piix
ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xffa0 irq 14
ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xffa8 irq 15
ata1.00: ATA-6: ST380011A, 8.16, max UDMA/100
ata1.00: 156250000 sectors, multi 8: LBA48 
ata1.00: configured for UDMA/100
ata2.00: ATAPI: TSST CD-RW/DVD-ROM TSH492B, TB06, max UDMA/33
ata2.01: ATAPI: HL-DT-STDVD-RAM GSA-H55N, 1.00, max UDMA/66
ata2.00: configured for UDMA/33
ata2.01: configured for UDMA/66
scsi 0:0:0:0: Direct-Access     ATA      ST380011A        8.16 PQ: 0 ANSI: 5
sd 0:0:0:0: [sda] 156250000 512-byte hardware sectors (80000 MB)
sd 0:0:0:0: [sda] Write Protect is off
sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
sd 0:0:0:0: [sda] 156250000 512-byte hardware sectors (80000 MB)
sd 0:0:0:0: [sda] Write Protect is off
sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
 sda: sda1 sda2 sda3
sd 0:0:0:0: [sda] Attached SCSI disk
scsi 1:0:0:0: CD-ROM            TSSTcorp CDRW/DVD TSH492B TB06 PQ: 0 ANSI: 5
sr0: scsi3-mmc drive: 48x/48x writer cd/rw xa/form2 cdda tray
Uniform CD-ROM driver Revision: 3.20
sr 1:0:0:0: Attached scsi CD-ROM sr0
scsi 1:0:1:0: CD-ROM            HL-DT-ST DVD-RAM GSA-H55N 1.00 PQ: 0 ANSI: 5
sr1: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
sr 1:0:1:0: Attached scsi CD-ROM sr1
PNP: No PS/2 controller found. Probing ports directly.
serio: i8042 KBD port at 0x60,0x64 irq 1
serio: i8042 AUX port at 0x60,0x64 irq 12
mice: PS/2 mouse device common for all mice
cpuidle: using governor ladder
TCP cubic registered
NET: Registered protocol family 1
NET: Registered protocol family 17
Using IPI Shortcut mode
Freeing unused kernel memory: 256k freed
squashfs: version 3.3 (2007/10/31) Phillip Lougher
usbcore: registered new interface driver usbfs
usbcore: registered new interface driver hub
usbcore: registered new device driver usb
USB Universal Host Controller Interface driver v3.0
ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 16 (level, low) -> IRQ 16
PCI: Setting latency timer of device 0000:00:1d.0 to 64
uhci_hcd 0000:00:1d.0: UHCI Host Controller
uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
uhci_hcd 0000:00:1d.0: irq 16, io base 0x0000ff80
usb usb1: configuration #1 chosen from 1 choice
hub 1-0:1.0: USB hub found
hub 1-0:1.0: 2 ports detected
ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 19 (level, low) -> IRQ 19
PCI: Setting latency timer of device 0000:00:1d.1 to 64
uhci_hcd 0000:00:1d.1: UHCI Host Controller
uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
uhci_hcd 0000:00:1d.1: irq 19, io base 0x0000ff60
usb usb2: configuration #1 chosen from 1 choice
hub 2-0:1.0: USB hub found
hub 2-0:1.0: 2 ports detected
ACPI: PCI Interrupt 0000:00:1d.3[A] -> GSI 16 (level, low) -> IRQ 16
PCI: Setting latency timer of device 0000:00:1d.3 to 64
uhci_hcd 0000:00:1d.3: UHCI Host Controller
uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 3
uhci_hcd 0000:00:1d.3: irq 16, io base 0x0000ff20
usb usb3: configuration #1 chosen from 1 choice
hub 3-0:1.0: USB hub found
hub 3-0:1.0: 2 ports detected
ACPI: PCI Interrupt 0000:00:1d.7[D] -> GSI 23 (level, low) -> IRQ 23
PCI: Setting latency timer of device 0000:00:1d.7 to 64
ehci_hcd 0000:00:1d.7: EHCI Host Controller
ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 4
ehci_hcd 0000:00:1d.7: debug port 1
PCI: cache line size of 128 is not supported by device 0000:00:1d.7
ehci_hcd 0000:00:1d.7: irq 23, io mem 0xffa80800
usb 1-2: new full speed USB device using uhci_hcd and address 2
ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
usb usb4: configuration #1 chosen from 1 choice
hub 4-0:1.0: USB hub found
hub 4-0:1.0: 8 ports detected
hub 1-0:1.0: unable to enumerate USB device on port 2
Initializing USB Mass Storage driver...
hub 4-0:1.0: unable to enumerate USB device on port 2
hub 4-0:1.0: unable to enumerate USB device on port 4
hub 4-0:1.0: unable to enumerate USB device on port 8
usbcore: registered new interface driver usb-storage
USB Mass Storage support registered.
usbcore: registered new interface driver hiddev
usb 1-2: new full speed USB device using uhci_hcd and address 3
usb 1-2: configuration #1 chosen from 1 choice
usb 2-2: new full speed USB device using uhci_hcd and address 2
usb 2-2: configuration #1 chosen from 1 choice
hub 2-2:1.0: USB hub found
hub 2-2:1.0: 3 ports detected
usb 3-2: new low speed USB device using uhci_hcd and address 2
usb 3-2: configuration #1 chosen from 1 choice
usb 2-2.1: new full speed USB device using uhci_hcd and address 3
usb 2-2.1: configuration #1 chosen from 1 choice
input: HID 413c:3010 as /devices/pci0000:00/0000:00:1d.3/usb3/3-2/3-2:1.0/input/input0
input: USB HID v1.10 Mouse [HID 413c:3010] on usb-0000:00:1d.3-2
input: Dell Dell USB Keyboard as /devices/pci0000:00/0000:00:1d.1/usb2/2-2/2-2.1/2-2.1:1.0/input/input1
input: USB HID v1.10 Keyboard [Dell Dell USB Keyboard] on usb-0000:00:1d.1-2.1
input: Dell Dell USB Keyboard as /devices/pci0000:00/0000:00:1d.1/usb2/2-2/2-2.1/2-2.1:1.1/input/input2
input: USB HID v1.10 Device [Dell Dell USB Keyboard] on usb-0000:00:1d.1-2.1
usbcore: registered new interface driver usbhid
drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
aufs 20080825
fuse init (API version 7.9)
ISO 9660 Extensions: RRIP_1991A
ISO 9660 Extensions: RRIP_1991A
aufs test_add:368:mount[1808]: uid/gid/perm /pup_ro2 0/0/0755, 0/0/01777
udevd version 124 started
ACPI: ACPI0007:00 is registered as cooling_device0
input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input3
ACPI: Power Button (FF) [PWRF]
input: Power Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input4
ACPI: Power Button (CM) [VBTN]
Linux agpgart interface v0.103
agpgart: Detected an Intel 865 Chipset.
agpgart: Detected 892K stolen memory.
agpgart: AGP aperture is 128M @ 0xe8000000
ACPI: PCI Interrupt 0000:00:1f.3[B] -> GSI 17 (level, low) -> IRQ 17
e100: Intel(R) PRO/100 Network Driver, 3.5.23-k4-NAPI
e100: Copyright(c) 1999-2006 Intel Corporation
ACPI: PCI Interrupt 0000:01:08.0[A] -> GSI 20 (level, low) -> IRQ 20
e100: eth0: e100_probe: addr 0xfeaff000, irq 20, MAC addr 00:13:20:8f:ff:61
input: PC Speaker as /devices/platform/pcspkr/input/input5
ACPI: PCI Interrupt 0000:00:1f.5[B] -> GSI 17 (level, low) -> IRQ 17
PCI: Setting latency timer of device 0000:00:1f.5 to 64
Linux video capture interface: v2.00
sn9c102: V4L2 driver for SN9C1xx PC Camera Controllers v1:1.47pre49
usb 1-2: SN9C105 PC Camera Controller detected (vid:pid 0x045E:0x00F5)
intel8x0_measure_ac97_clock: measured 55422 usecs
intel8x0: clocking to 48000
usb 1-2: No supported image sensor detected for this bridge
/usr/src/3rd-party-drivers-extra/misc/gspcav1-20071224/gspca_core.c: USB GSPCA camera found. SONIX JPEG (sn9c1xx) 
/usr/src/3rd-party-drivers-extra/misc/gspcav1-20071224/gspca_core.c: [spca5xx_probe:4275] Camera type JPEG 
/usr/src/3rd-party-drivers-extra/misc/gspcav1-20071224/gspca_core.c: [spca5xx_getcapability:1249] maxw 640 maxh 480 minw 160 minh 120
usbcore: registered new interface driver sn9c102
usbcore: registered new interface driver gspca
/usr/src/3rd-party-drivers-extra/misc/gspcav1-20071224/gspca_core.c: gspca driver 01.00.20 registered
e100: eth0: e100_watchdog: link up, 100Mbps, full-duplex
parport_pc 00:08: reported by Plug and Play ACPI
parport0: PC-style at 0x378 (0x778), irq 7 [PCSPP,TRISTATE]
lp0: using parport0 (interrupt-driven).
lp0: console ready
e100: eth0: e100_watchdog: link up, 100Mbps, full-duplex
usb 4-7: new high speed USB device using ehci_hcd and address 5
usb 4-7: configuration #1 chosen from 1 choice
scsi2 : SCSI emulation for USB Mass Storage devices
usb-storage: device found at 5
usb-storage: waiting for device to settle before scanning
input: Western Digital My Book as /devices/pci0000:00/0000:00:1d.7/usb4/4-7/4-7:1.1/input/input6
input: USB HID v1.11 Device [Western Digital My Book] on usb-0000:00:1d.7-7
scsi 2:0:0:0: Direct-Access     WD       My Book          1028 PQ: 0 ANSI: 4
sd 2:0:0:0: [sdb] 156301488 512-byte hardware sectors (80026 MB)
sd 2:0:0:0: [sdb] Write Protect is off
sd 2:0:0:0: [sdb] Mode Sense: 10 00 00 00
sd 2:0:0:0: [sdb] Assuming drive cache: write through
sd 2:0:0:0: [sdb] 156301488 512-byte hardware sectors (80026 MB)
sd 2:0:0:0: [sdb] Write Protect is off
sd 2:0:0:0: [sdb] Mode Sense: 10 00 00 00
sd 2:0:0:0: [sdb] Assuming drive cache: write through
 sdb:<6>usb 4-7: reset high speed USB device using ehci_hcd and address 5
usb 4-7: device descriptor read/64, error -110
usb 4-7: device descriptor read/64, error -110
usb 4-7: reset high speed USB device using ehci_hcd and address 5
usb 4-7: device descriptor read/64, error -110
usb 4-7: device descriptor read/64, error -110
usb 4-7: reset high speed USB device using ehci_hcd and address 5
usb 4-7: device descriptor read/8, error -110
usb 4-7: device descriptor read/8, error -110
usb 4-7: reset high speed USB device using ehci_hcd and address 5
usb 4-7: device descriptor read/8, error -110
usb 4-7: device descriptor read/8, error -110
usb 4-7: USB disconnect, address 5
sd 2:0:0:0: Device offlined - not ready after error recovery
sd 2:0:0:0: [sdb] Result: hostbyte=DID_ABORT driverbyte=DRIVER_OK,SUGGEST_OK
end_request: I/O error, dev sdb, sector 0
Buffer I/O error on device sdb, logical block 0
sd 2:0:0:0: rejecting I/O to offline device
Buffer I/O error on device sdb, logical block 0
sd 2:0:0:0: rejecting I/O to offline device
Buffer I/O error on device sdb, logical block 0
ldm_validate_partition_table(): Disk read failed.
sd 2:0:0:0: rejecting I/O to offline device
Buffer I/O error on device sdb, logical block 0
sd 2:0:0:0: rejecting I/O to offline device
Buffer I/O error on device sdb, logical block 0
sd 2:0:0:0: rejecting I/O to offline device
Buffer I/O error on device sdb, logical block 0
 unable to read partition table
sd 2:0:0:0: [sdb] Attached SCSI disk
usb-storage: device scan complete
usb 4-7: new high speed USB device using ehci_hcd and address 6
usb 4-7: device descriptor read/64, error -110
usb 4-7: device descriptor read/64, error -110
usb 4-7: new high speed USB device using ehci_hcd and address 7
usb 4-7: device descriptor read/64, error -110
usb 4-7: device descriptor read/64, error -110
usb 4-7: new high speed USB device using ehci_hcd and address 8
usb 4-7: device descriptor read/8, error -110
usb 4-7: device descriptor read/8, error -110
usb 4-7: new high speed USB device using ehci_hcd and address 9
usb 4-7: device descriptor read/8, error -110
usb 4-7: device descriptor read/8, error -110
hub 4-0:1.0: unable to enumerate USB device on port 7
usb 3-1: new full speed USB device using uhci_hcd and address 3
usb 3-1: device descriptor read/64, error -110
usb 3-1: device descriptor read/64, error -110
usb 3-1: new full speed USB device using uhci_hcd and address 4
usb 3-1: device descriptor read/64, error -110
usb 3-1: device descriptor read/64, error -110
usb 3-1: new full speed USB device using uhci_hcd and address 5
usb 3-1: device descriptor read/8, error -110
usb 3-1: device descriptor read/8, error -110
usb 3-1: new full speed USB device using uhci_hcd and address 6
usb 3-1: device descriptor read/8, error -110
usb 3-1: device descriptor read/8, error -110
hub 3-0:1.0: unable to enumerate USB device on port 1
end_request: I/O error, dev fd0, sector 0
end_request: I/O error, dev fd0, sector 0
end_request: I/O error, dev fd0, sector 0
end_request: I/O error, dev fd0, sector 0

I even tried Windows XP (ICK) to see if it would work.  It detected a device, but said that the device was not working properly.  I could unconnect it, but could not access the drive in any way.  Though one thing that was odd, was that it called the drive Western Digital My Book, which is the name of my removable hard drive, not the name of my hard drive that is messed up.  The external drive has a chip that you connect a hard drive to, so I think there is some programming in there.  Perhaps this is the problem.  If I cant resolve this issue I may buy an external enclosure for my drive to see if that solves anything.  Also the original drive in the removable drive was 3.5", my messed up hard drive is 2.5" but it has the same connection, so I didn't think it would be a problem.  

Please help if you can!!!

Michael

---

### Post by x22 on 2009-01-01
try this:
1. replace messed-up drive in machine then either
2. use "partition magic" to partition the drive
or
3. boot "knoppix" live CD and use fdisk
or
4. boot "systemrescue" live CD and use GParted (a
   P.Magic clone) 

[http://www.sysresccd.org/Main_Page](http://www.sysresccd.org/Main_Page)

an amazing system, lotsa goodies

---

### Post by caljohnsmith on 2009-01-01
How about posting the output of:
```
sudo fdisk -lu
```
Also, how big is the HDD in question? You have me totally confused about what you are trying to do at this point. Are you just trying to format the HDD and repartition it? When you say gparted "would not work" to make the partition changes, what errors did you get?

---

### Post by mrallaire on 2009-01-03
Problem solved.  Thank-you X22.  A boot-up disk just to partition the drive worked.  More specifically, I went to the gparted website, and they had their own live cd for download.  I was able to boot up with their program, format my drive, and now everything works.  

Thanks again for your help.

---

### Post by mrallaire on 2009-01-03
caljohnsmith,

I could not try:

sudo fdisk - lu

as my drive was working by the time I read your prompt reply.  

Just to clarify, when I said I could not resize my partition, there was no error message given.  When you click on a partition in gparted, you get the menu option to resize.  The menu option simply wasn't available for that partition.  Either it was because you can't resize an ext2 partition, or my drive was busy and would not allow me to unmount it.  Not sure which.

Anyway, thanks for your help.

---

