---
title: "limited to UDMA/33 due to 40-wire cable on a 80 wire cable"
date: 2008-02-06
forum: Hardware &amp; Laptops
---

### Post by SunKing2 on 2008-02-06
In gutsy, I'm getting in my dmesg:
ata1.01: limited to UDMA/33 due to 40-wire cable

on a FUJITSU MPE3064AT 6GB hard drive.  Motherboard: is K7Som+ V5.2C with AMD Duron 1.2GHz

This drive was functioning fine under Windows XP at 66, and a newer drive on the same cable gets detected correctly.

The controller is fine, and the capabilities of the drive looks fine:
[   20.714392] ata1: PATA max UDMA/133 cmd 0x000101f0 ctl 0x000103f6 bmdma 0x0001ff00 irq 14
[   20.885501] ata1.01: ATA-4: FUJITSU MPE3064AT, ED-03-04, max UDMA/66


What I've tried: 
switching cables:  I tried to use a cable that read the CD-ROM at 66, but it made no difference
jumpers: I've tried Master - no difference
                    Cable Select - no difference
Additional drive: I've tried it with a second drive, and all combinations of master, slave, and cable selects using the Fujitsu drive as the master, and as a slave... no difference.

I've tried it with the CDROM drive which is UDMA/66 and is detected fine where the CD is master, and slave, and CS.  No difference.

I tried it with 2 different cables.  Both cables that I've tried clearly are 80 wire cables, and they have blue, grey, and black connectors where the blue is plugged into the motherboard blue connector

I've tried hdparm with c and d flag but get FAILED on all attempts to do this. (see output below)

I have a brand new 500GB WD Cavier drive, and it gets detected at UDMA/66

I'm guessing that gutsy has a problem with FUJITSU MPE3064AT drive.

By the way, what kind of hdparm -t would you expect on an old UDMA/66 hard drive like this?, mine was 17.79 MB/sec .

======================
here's a lot of detail:


pam@pam-desktop:~$ uname -a 
Linux pam-desktop 2.6.22-14-generic #1 SMP Tue Dec 18 08:02:57 UTC 2007 i686 GNU/Linux
pam@pam-desktop:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             5.7G  1.8G  3.6G  34% /
varrun                110M   72K  110M   1% /var/run
varlock               110M     0  110M   0% /var/lock
udev                  110M   52K  110M   1% /dev
devshm                110M     0  110M   0% /dev/shm
lrm                   110M   34M   76M  32% /lib/modules/2.6.22-14-generic/volatile
pam@pam-desktop:~$ sudo hdparm -aAcCiIgv --verbose /dev/sda

/dev/sda:
 IO_support    =  0 (default 16-bit)
 readonly      =  0 (off)
 readahead     = 256 (on)
 geometry      = 788/255/63, sectors = 12672450, start = 0
outgoing cdb:  85 06 20 00 00 00 00 00 00 00 00 00 00 40 e5 00
SG_IO: ATA_16 status=0x2, host_status=0x0, driver_status=0x8
      ATA_16 tf->status=0x50 tf->error=0x00
 drive state is:  active/idle

 Model=FUJITSU MPE3064AT                       , FwRev=ED-03-04, SerialNo=            05084213
 Config={ HardSect NotMFM HdSw>15uSec Fixed DTR>10Mbs }
 RawCHS=13410/15/63, TrkSize=0, SectSize=0, ECCbytes=4
 BuffType=unknown, BuffSize=512kB, MaxMultSect=16, MultSect=?16?
 CurCHS=13410/15/63, CurSects=12672450, LBA=yes, LBAsects=12672450
 IORDY=yes, tPIO={min:120,w/IORDY:120}, tDMA={min:120,rec:120}
 PIO modes:  pio0 pio1 pio2 pio3 pio4 
 DMA modes:  mdma0 mdma1 mdma2 
 UDMA modes: udma0 udma1 *udma2 udma3 udma4 
 AdvancedPM=yes: disabled (255) WriteCache=enabled
 Drive conforms to: Unspecified:  ATA/ATAPI-1,2,3,4

 * signifies the current active mode

outgoing cdb:  85 08 2e 00 00 00 00 00 00 00 00 00 00 40 ec 00
SG_IO: ATA_16 status=0x2, host_status=0x0, driver_status=0x8
      ATA_16 tf->status=0x50 tf->error=0x00

ATA device, with non-removable media
        Model Number:       FUJITSU MPE3064AT                       
        Serial Number:      05084213
        Firmware Revision:  ED-03-04
Standards:
        Supported: 4 3 2 
        Likely used: 4
Configuration:
        Logical         max     current
        cylinders       13410   13410
        heads           15      15
        sectors/track   63      63
        --
        CHS current addressable sectors:   12672450
        LBA    user addressable sectors:   12672450
        device size with M = 1024*1024:        6187 MBytes
        device size with M = 1000*1000:        6488 MBytes (6 GB)
Capabilities:
        LBA, IORDY(cannot be disabled)
        bytes avail on r/w long: 4
        Standby timer values: spec'd by Vendor
        R/W multiple sector transfer: Max = 16  Current = 16
        Advanced power management level: unknown setting (0x0000)
        DMA: mdma0 mdma1 mdma2 udma0 udma1 *udma2 udma3 udma4 
             Cycle time: min=120ns recommended=120ns
        PIO: pio0 pio1 pio2 pio3 pio4 
             Cycle time: no flow control=120ns  IORDY flow control=120ns
Commands/features:
        Enabled Supported:
                SMART feature set
                Security Mode feature set
                Power Management feature set
           *    Write cache
           *    Look-ahead
                Host Protected Area feature set
                WRITE_BUFFER command
                READ_BUFFER command
                Advanced Power Management feature set
Security: 
                supported
        not     enabled
        not     locked
                frozen
        not     expired: security count
        not     supported: enhanced erase
        12min for SECURITY ERASE UNIT. 
 look-ahead    =  1 (on)
pam@pam-desktop:~$ sudo hdparm -tT /dev/sda

/dev/sda:
 Timing cached reads:   310 MB in  2.01 seconds = 154.57 MB/sec
 Timing buffered disk reads:   54 MB in  3.04 seconds =  17.75 MB/sec
pam@pam-desktop:~$ sudo hdparm -tT /dev/sda

/dev/sda:
 Timing cached reads:   308 MB in  2.00 seconds = 153.98 MB/sec
 Timing buffered disk reads:   54 MB in  3.04 seconds =  17.79 MB/sec
pam@pam-desktop:~$ sudo hdparm -tT /dev/sda

/dev/sda:
 Timing cached reads:   310 MB in  2.01 seconds = 154.54 MB/sec
 Timing buffered disk reads:   54 MB in  3.00 seconds =  17.97 MB/sec


pam@pam-desktop:~$ sudo hdparm -c1 /dev/sda
[sudo] password for pam:

/dev/sda:
 setting 32-bit IO_support flag to 1
 HDIO_SET_32BIT failed: Invalid argument
 IO_support    =  0 (default 16-bit)
pam@pam-desktop:~$ sudo hdparm -c3 /dev/sda

/dev/sda:
 setting 32-bit IO_support flag to 3
 HDIO_SET_32BIT failed: Invalid argument
 IO_support    =  0 (default 16-bit)
pam@pam-desktop:~$ sudo hdparm -d1 /dev/sda

/dev/sda:
 setting using_dma to 1 (on)
 HDIO_SET_DMA failed: Inappropriate ioctl for device

pam@pam-desktop:~$ sudo fdisk -l
[sudo] password for pam:

Disk /dev/sda: 6488 MB, 6488294400 bytes
255 heads, 63 sectors/track, 788 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xdff7dff7



hwinfo output:


15: PCI 02.5: 0101 IDE interface
  [Created at pci.296]
  UDI: /org/freedesktop/Hal/devices/pci_1039_5513
  Unique ID: JCE+.zEvtq1atMeE
  SysFS ID: /devices/pci0000:00/0000:00:02.5
  SysFS BusID: 0000:00:02.5
  Hardware Class: storage
  Model: "Silicon Integrated 5513 [IDE]"
  Vendor: pci 0x1039 "Silicon Integrated Systems Corp."
  Device: pci 0x5513 "5513 [IDE]"
  Driver: "pata_sis"
  Driver Modules: "pata_sis"
  I/O Ports: 0x1f0-0x1f7 (rw)
  I/O Port: 0x3f6 (rw)
  I/O Ports: 0x170-0x177 (rw)
  I/O Port: 0x376 (rw)
  I/O Ports: 0xff00-0xff0f (rw)
  Module Alias: "pci:v00001039d00005513sv00000000sd00000000bc01sc01i80"
  Driver Info #0:
    Driver Status: pata_sis is active
    Driver Activation Cmd: "modprobe pata_sis"
  Driver Info #1:
    Driver Status: ata_generic is active
    Driver Activation Cmd: "modprobe ata_generic"
  Config Status: cfg=new, avail=yes, need=no, active=unknown

29: IDE 01.0: 10600 Disk
  [Created at block.222]
  UDI: /org/freedesktop/Hal/devices/storage_serial_1ATA_FUJITSU_MPE3064AT_05084213
  Unique ID: mE25.vjXgmN97cm8
  Parent ID: JCE+.zEvtq1atMeE
  SysFS ID: /block/sda
  SysFS BusID: 0:0:1:0
  SysFS Device Link: /devices/pci0000:00/0000:00:02.5/host0/target0:0:1/0:0:1:0
  Hardware Class: disk
  Model: "FUJITSU MPE3064A"
  Vendor: "FUJITSU"
  Device: "MPE3064A"
  Revision: "ED-0"
  Driver: "pata_sis", "sd"
  Driver Modules: "pata_sis"
  Device File: /dev/sda
  Device Files: /dev/sda, /dev/disk/by-id/scsi-1ATA_FUJITSU_MPE3064AT_05084213, /dev/disk/by-id/ata-FUJITSU_MPE3064AT_05084213, /dev/disk/by-path/pci-0000:00:02.5-scsi-0:0:1:0
  Device Number: block 8:0-8:15
  BIOS id: 0x80
  Drive status: no medium
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #15 (IDE interface)

30: None 00.0: 11300 Partition
  [Created at block.391]
  UDI: /org/freedesktop/Hal/devices/volume_uuid_2bb38858_67f8_4b52_960a_dff8647f671b
  Unique ID: 1tKY.SE1wIdpsiiC
  Parent ID: mE25.vjXgmN97cm8
  SysFS ID: /block/sda/sda1
  Hardware Class: partition
  Model: "Partition"
  Device File: /dev/sda1
  Device Files: /dev/sda1, /dev/disk/by-id/scsi-1ATA_FUJITSU_MPE3064AT_05084213-part1, /dev/disk/by-id/ata-FUJITSU_MPE3064AT_05084213-part1, /dev/disk/by-path/pci-0000:00:02.5-scsi-0:0:1:0-part1, /dev/disk/by-uuid/2bb38858-67f8-4b52-960a-dff8647f671b
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #29 (Disk)



   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         748     6008278+  83  Linux
/dev/sda2             749         788      321300    5  Extended
/dev/sda5             749         788      321268+  82  Linux swap / Solaris



-------------------------excerpts from dmsg (edited) ----------------------


[    0.000000] Linux version 2.6.22-14-generic (buildd@terranova) (gcc version 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)) #1 SMP Tue Dec 18 08:02:57 UTC 2007 (Ubuntu 2.6.22-14.47-generic)
[    0.000000] 0MB HIGHMEM available.
[    0.000000] 223MB LOWMEM available.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 1024 (order: 10, 4096 bytes)
[    0.000000] Detected 1194.974 MHz processor.
[   15.226553] Memory: 215820k/229312k available (2015k kernel code, 12920k reserved, 916k data, 364k init, 0k highmem)
[   15.226672] virtual kernel memory layout:
[   15.873964] CPU0: AMD Duron(tm) Processor stepping 01
[   15.874098] SMP motherboard not detected.
[   15.874162] Local APIC not detected. Using dummy APIC emulation.
[   15.874322] Brought up 1 CPUs
[   15.874673] Booting paravirtualized kernel on bare hardware
[   15.874901] Time: 14:38:33  Date: 01/06/108
[   15.875036] NET: Registered protocol family 16
[   15.875380] EISA bus registered
[   15.875466] ACPI: bus type pci registered
[   15.877432] PCI: PCI BIOS revision 2.10 entry at 0xfdb01, last bus=2
[   15.903853] Linux Plug and Play Support v0.97 (c) Adam Belay
[   15.903951] pnp: PnP ACPI init
[   15.904059] ACPI: bus type pnp registered
[   15.907408] pnp: PnP ACPI: found 7 devices
[   15.907488] ACPI: ACPI bus type pnp unregistered
[   15.907559] PnPBIOS: Disabled by ACPI PNP
[   18.060858] isapnp: Scanning for PnP cards...
[   18.414551] isapnp: No Plug & Play device found
[   20.701295] SCSI subsystem initialized
[   20.710843] libata version 2.21 loaded.
[   20.713501] pata_sis 0000:00:02.5: version 0.5.1
[   20.713929] scsi0 : pata_sis
[   20.714113] scsi1 : pata_sis
[   20.714392] ata1: PATA max UDMA/133 cmd 0x000101f0 ctl 0x000103f6 bmdma 0x0001ff00 irq 14
[   20.714488] ata2: PATA max UDMA/133 cmd 0x00010170 ctl 0x00010376 bmdma 0x0001ff08 irq 15
[   20.774699] usbcore: registered new interface driver usbfs
[   20.774829] usbcore: registered new interface driver hub
[   20.774951] usbcore: registered new device driver usb
[   20.776822] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
[   20.855890] sis900.c: v1.08.10 Apr. 2 2006
[   20.885501] ata1.01: ATA-4: FUJITSU MPE3064AT, ED-03-04, max UDMA/66
[   20.885590] ata1.01: 12672450 sectors, multi 16: LBA 
[   20.885668] ata1.01: limited to UDMA/33 due to 40-wire cable
[   20.901511] ata1.01: configured for UDMA/33
[   21.065078] scsi 0:0:1:0: Direct-Access     ATA      FUJITSU MPE3064A ED-0 PQ: 0 ANSI: 5
[   21.069382] ACPI: PCI Interrupt Link [LNKE] enabled at IRQ 5
[   21.069471] PCI: setting IRQ 5 as level-triggered
[   21.069477] ACPI: PCI Interrupt 0000:00:03.0[A] -> Link [LNKE] -> GSI 5 (level, low) -> IRQ 5
[   21.069655] ohci_hcd 0000:00:03.0: OHCI Host Controller
[   21.070216] ohci_hcd 0000:00:03.0: new USB bus registered, assigned bus number 1
[   21.070348] ohci_hcd 0000:00:03.0: irq 5, io mem 0xcfff9000
[   21.118132] sd 0:0:1:0: [sda] 12672450 512-byte hardware sectors (6488 MB)
[   21.118247] sd 0:0:1:0: [sda] Write Protect is off
[   21.118312] sd 0:0:1:0: [sda] Mode Sense: 00 3a 00 00
[   21.118342] sd 0:0:1:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   21.119260] sd 0:0:1:0: [sda] 12672450 512-byte hardware sectors (6488 MB)
[   21.119346] sd 0:0:1:0: [sda] Write Protect is off
[   21.119412] sd 0:0:1:0: [sda] Mode Sense: 00 3a 00 00
[   21.119436] sd 0:0:1:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   21.119533]  sda:<6>usb usb1: configuration #1 chosen from 1 choice
[   21.127302] hub 1-0:1.0: USB hub found
[   21.127388] hub 1-0:1.0: 3 ports detected
[   21.137121]  sda1 sda2 < sda5 >
[   21.158971] sd 0:0:1:0: [sda] Attached SCSI disk
[   21.169290] sd 0:0:1:0: Attached scsi generic sg0 type 0

  smbios.chassis.type = 'Desktop'
  smbios.system.uuid = 'Not Settable'
  smbios.system.serial = '00000000'
  smbios.bios.version = '07.00T'
  smbios.bios.vendor = 'American Megatrends Inc.'
  smbios.system.manufacturer = 'ECS'
  smbios.system.version = '1.0'
  smbios.chassis.manufacturer = 'ECS'
  smbios.bios.release_date = '04/02/01'
  smbios.system.product = 'K7SOM+'

---

### Post by whirleyes on 2008-02-07
You should try to disable the libata cabledetect... 
I solved mine by applying patch to the libata source.. 
and force cable to 80.. here  a simple step by step i wrote.. 

[http://pixca.net/2008/02/03/limited-to-udma33-due-to-40-wire-cable/]("http://pixca.net/2008/02/03/limited-to-udma33-due-to-40-wire-cable/")

hope it help:)

---

### Post by tgalati4 on 2008-02-07
It may not make a difference.  For drives that old, the buffer amount and controller speed will limit the throughput, not the IDE speed.  Running the drive at the higher speed may shorten the drive's life anyway because of aging of the bearings and the write head.

---

### Post by jap1968 on 2008-02-23
Can this be done just using kernel parameters? (i.e. without compiling)

---

