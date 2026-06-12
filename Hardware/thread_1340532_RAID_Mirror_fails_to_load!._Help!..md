---
title: "RAID Mirror fails to load!. Help!."
date: 2009-11-28
forum: Hardware
---

### Post by sunrex on 2009-11-28
I'm trying to get my RAID1 working after a reboot. A mirror fails to load, and I don't know how to fix it.

This thread explains part of the problem, but I dont think its whats wrong here since after the working mirror loads the system detects the other harddrive..

[http://ubuntuforums.org/showthread.php?t=1052987&page=4](http://ubuntuforums.org/showthread.php?t=1052987&page=4)

> 
cat /proc/mdstat
Personalities : [raid1] 
md0 : active raid1 sdb1[1]
      215037952 blocks [2/1] [_U]
      
unused devices: <none>


```

ATIIXP: simplex device: DMA disabled
ide1: ATIIXP Bus-Master DMA disabled (BIOS)
Probing IDE interface ide0...
Probing IDE interface ide1...
Probing IDE interface ide0...
Probing IDE interface ide1...
ide-floppy driver 0.99.newide
usbcore: registered new driver hiddev
usbcore: registered new driver usbhid
drivers/usb/input/hid-core.c: v2.6:USB HID core driver
PNP: No PS/2 controller found. Probing ports directly.
serio: i8042 KBD port at 0x60,0x64 irq 1
serio: i8042 AUX port at 0x60,0x64 irq 12
mice: PS/2 mouse device common for all mice
md: md driver 0.90.3 MAX_MD_DEVS=256, MD_SB_DISKS=27
md: bitmap version 4.39
TCP bic registered
Initializing IPsec netlink socket
NET: Registered protocol family 1
NET: Registered protocol family 17
ACPI: (supports S0 S3 S4 S5)
Initalizing network drop monitor service
Freeing unused kernel memory: 208k freed
Write protecting the kernel read-only data: 496k
ohci_hcd: 2005 April 22 USB 1.1 'Open' Host Controller (OHCI) Driver (PCI)
ACPI: PCI Interrupt 0000:00:12.0[A] -> GSI 16 (level, low) -> IRQ 193
ohci_hcd 0000:00:12.0: OHCI Host Controller
ohci_hcd 0000:00:12.0: new USB bus registered, assigned bus number 1
ohci_hcd 0000:00:12.0: irq 193, io mem 0xfe02e000
usb usb1: configuration #1 chosen from 1 choice
hub 1-0:1.0: USB hub found
hub 1-0:1.0: 3 ports detected
ACPI: PCI Interrupt 0000:00:12.1[A] -> GSI 16 (level, low) -> IRQ 193
ohci_hcd 0000:00:12.1: OHCI Host Controller
ohci_hcd 0000:00:12.1: new USB bus registered, assigned bus number 2
ohci_hcd 0000:00:12.1: irq 193, io mem 0xfe02d000
usb usb2: configuration #1 chosen from 1 choice
hub 2-0:1.0: USB hub found
hub 2-0:1.0: 3 ports detected
ACPI: PCI Interrupt 0000:00:13.0[A] -> GSI 18 (level, low) -> IRQ 169
ohci_hcd 0000:00:13.0: OHCI Host Controller
ohci_hcd 0000:00:13.0: new USB bus registered, assigned bus number 3
ohci_hcd 0000:00:13.0: irq 169, io mem 0xfe02c000
usb usb3: configuration #1 chosen from 1 choice
hub 3-0:1.0: USB hub found
hub 3-0:1.0: 3 ports detected
ACPI: PCI Interrupt 0000:00:13.1[A] -> GSI 18 (level, low) -> IRQ 169
ohci_hcd 0000:00:13.1: OHCI Host Controller
ohci_hcd 0000:00:13.1: new USB bus registered, assigned bus number 4
ohci_hcd 0000:00:13.1: irq 169, io mem 0xfe02b000
usb usb4: configuration #1 chosen from 1 choice
hub 4-0:1.0: USB hub found
hub 4-0:1.0: 3 ports detected
ACPI: PCI Interrupt 0000:00:14.5[C] -> GSI 18 (level, low) -> IRQ 169
ohci_hcd 0000:00:14.5: OHCI Host Controller
ohci_hcd 0000:00:14.5: new USB bus registered, assigned bus number 5
ohci_hcd 0000:00:14.5: irq 169, io mem 0xfe02a000
usb usb5: configuration #1 chosen from 1 choice
hub 5-0:1.0: USB hub found
hub 5-0:1.0: 2 ports detected
USB Universal Host Controller Interface driver v3.0
md: raid1 personality registered for level 1
SCSI subsystem initialized
libata version 3.00 loaded.
ahci 0000:00:11.0: version 3.0
GSI 18 sharing vector 0xC9 and IRQ 18
ACPI: PCI Interrupt 0000:00:11.0[A] -> GSI 22 (level, low) -> IRQ 201
ahci 0000:00:11.0: AHCI 0001.0100 32 slots 6 ports 3 Gbps 0x3f impl SATA mode
ahci 0000:00:11.0: flags: 64bit ncq sntf ilck pm led clo pmp pio slum part 
scsi0 : ahci
scsi1 : ahci
scsi2 : ahci
scsi3 : ahci
scsi4 : ahci
scsi5 : ahci
ata1: SATA max UDMA/133 abar m1024@0xfe02f000 port 0xfe02f100 irq 201
ata2: SATA max UDMA/133 abar m1024@0xfe02f000 port 0xfe02f180 irq 201
ata3: SATA max UDMA/133 abar m1024@0xfe02f000 port 0xfe02f200 irq 201
ata4: SATA max UDMA/133 abar m1024@0xfe02f000 port 0xfe02f280 irq 201
ata5: SATA max UDMA/133 abar m1024@0xfe02f000 port 0xfe02f300 irq 201
ata6: SATA max UDMA/133 abar m1024@0xfe02f000 port 0xfe02f380 irq 201
ata1: softreset failed (device not ready)
ata1: failed due to HW bug, retry pmp=0
ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
ata1.00: HPA detected: current 625140335, native 625142448
ata1.00: ATA-7: WDC WD3200KS-00PFB0, 21.00M21, max UDMA/133
ata1.00: 625140335 sectors, multi 0: LBA48 NCQ (depth 1)
ata1.00: configured for UDMA/133
ata2: SATA link down (SStatus 0 SControl 300)
ata3: softreset failed (device not ready)
ata3: failed due to HW bug, retry pmp=0
ata3: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
ata3.00: ATA-7: ST3250410AS, 3.AAF, max UDMA/133
ata3.00: 488397168 sectors, multi 0: LBA48 NCQ (depth 31/32)
ata3.00: configured for UDMA/133
ata4: softreset failed (device not ready)
ata4: failed due to HW bug, retry pmp=0
ata4: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
ata4.00: ATAPI: HP DVD Writer 1160d, AH21, max UDMA/100
ata4.00: configured for UDMA/100
ata5: SATA link down (SStatus 0 SControl 300)
ata6: SATA link down (SStatus 0 SControl 300)
  Vendor: ATA       Model: WDC WD3200KS-00P  Rev: 21.0
  Type:   Direct-Access                      ANSI SCSI revision: 05
SCSI device sda: 625140335 512-byte hdwr sectors (320072 MB)
sda: Write Protect is off
sda: Mode Sense: 00 3a 00 00
SCSI device sda: drive cache: write back
SCSI device sda: 625140335 512-byte hdwr sectors (320072 MB)
sda: Write Protect is off
sda: Mode Sense: 00 3a 00 00
SCSI device sda: drive cache: write back
 sda: unknown partition table
sd 0:0:0:0: Attached scsi disk sda
  Vendor: ATA       Model: ST3250410AS       Rev: 3.AA
  Type:   Direct-Access                      ANSI SCSI revision: 05
SCSI device sdb: 488397168 512-byte hdwr sectors (250059 MB)
sdb: Write Protect is off
sdb: Mode Sense: 00 3a 00 00
SCSI device sdb: drive cache: write back
SCSI device sdb: 488397168 512-byte hdwr sectors (250059 MB)
sdb: Write Protect is off
sdb: Mode Sense: 00 3a 00 00
SCSI device sdb: drive cache: write back
 sdb: sdb1
sd 2:0:0:0: Attached scsi disk sdb
  Vendor: HP        Model: DVD Writer 1160d  Rev: AH21
  Type:   CD-ROM                             ANSI SCSI revision: 05
Initializing USB Mass Storage driver...
usbcore: registered new driver usb-storage
USB Mass Storage support registered.
device-mapper: uevent: version 1.0.3
device-mapper: ioctl: 4.11.5-ioctl (2007-12-12) initialised: dm-devel@redhat.com
device-mapper: dm-raid45: initialized v0.2594l
md: Autodetecting RAID arrays.
md: autorun ...
md: considering sdb1 ...
md:  adding sdb1 ...
md: created md0
md: bind<sdb1>
md: running: <sdb1>
raid1: raid set md0 active with 1 out of 2 mirrors
md: ... autorun DONE.
EXT3-fs: INFO: recovery required on readonly filesystem.
EXT3-fs: write access will be enabled during recovery.
kjournald starting.  Commit interval 5 seconds
EXT3-fs: recovery complete.
EXT3-fs: mounted filesystem with ordered data mode.
type=1404 audit(1259421067.333:2): enforcing=1 old_enforcing=0 auid=4294967295 ses=4294967295
security:  3 users, 6 roles, 1871 types, 242 bools, 1 sens, 1024 cats
security:  61 classes, 69981 rules
SELinux:  Completing initialization.
SELinux:  Setting up existing superblocks.

```

Please help me!.

---

