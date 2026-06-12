---
title: "USB to SATA &amp; PATA Adapter (ID 152d:2338)"
date: 2008-11-01
forum: Hardware
---

### Post by kaefert66014235 on 2008-11-01
Hi there! I have some problems with a USB to SATA & PATA Adapter.
I plugged in a IDE harddisk, which should have some partitions on it. But i can't mount them, (there is only a /dev/sdb and no /dev/sdb1 after i plug the adapter)

lsusb gives me:
```
Bus 007 Device 003: ID 152d:2338 JMicron Technology Corp. / JMicron USA Technology Corp. JM20337 Hi-Speed USB to SATA & PATA Combo Bridge
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  idVendor           0x152d JMicron Technology Corp. / JMicron USA Technology Corp.
  idProduct          0x2338 JM20337 Hi-Speed USB to SATA & PATA Combo Bridge
  bcdDevice            1.00
  iManufacturer           1 JMicron
  iProduct                2 USB to ATA/ATAPI Bridge
  iSerial                 5 152D203380B6
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           32
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          4 USB Mass Storage
    bmAttributes         0xc0
      Self Powered
    MaxPower                2mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           2
      bInterfaceClass         8 Mass Storage
      bInterfaceSubClass      6 SCSI
      bInterfaceProtocol     80 Bulk (Zip)
      iInterface              6 MSC Bulk-Only Transfer
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x02  EP 2 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0
Device Qualifier (for other device speed):
  bLength                10
  bDescriptorType         6
  bcdUSB               2.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  bNumConfigurations      1
can't get debug descriptor: Connection timed out
Device Status:     0xd301
  Self Powered
```

udevmonitor gives the following (first plug-out, then plug in)
```
UEVENT[1225540844.626385] remove   /devices/pci0000:00/0000:00:1d.7/usb7/7-2/7-2:1.0/usb_endpoint/usbdev7.5_ep81 (usb_endpoint)
UEVENT[1225540844.626433] remove   /devices/pci0000:00/0000:00:1d.7/usb7/7-2/7-2:1.0/usb_endpoint/usbdev7.5_ep02 (usb_endpoint)
UEVENT[1225540844.626455] remove   /class/scsi_generic/sg2 (scsi_generic)
UEVENT[1225540844.627225] remove   /class/scsi_device/6:0:0:0 (scsi_device)
UEVENT[1225540844.627256] remove   /class/scsi_disk/6:0:0:0 (scsi_disk)
UEVENT[1225540844.627276] remove   /block/sdb (block)
UEVENT[1225540844.627294] remove   /devices/pci0000:00/0000:00:1d.7/usb7/7-2/7-2:1.0/host6/target6:0:0/6:0:0:0 (scsi)
UEVENT[1225540844.627313] remove   /class/scsi_host/host6 (scsi_host)
UEVENT[1225540844.627331] remove   /devices/pci0000:00/0000:00:1d.7/usb7/7-2/7-2:1.0 (usb)
UEVENT[1225540844.627640] remove   /devices/pci0000:00/0000:00:1d.7/usb7/7-2/usb_endpoint/usbdev7.5_ep00 (usb_endpoint)
UEVENT[1225540844.627668] remove   /devices/pci0000:00/0000:00:1d.7/usb7/7-2 (usb)
UDEV  [1225540844.629129] remove   /devices/pci0000:00/0000:00:1d.7/usb7/7-2/7-2:1.0/usb_endpoint/usbdev7.5_ep81 (usb_endpoint)
UDEV  [1225540844.630798] remove   /devices/pci0000:00/0000:00:1d.7/usb7/7-2/7-2:1.0/usb_endpoint/usbdev7.5_ep02 (usb_endpoint)
UDEV  [1225540844.632517] remove   /class/scsi_generic/sg2 (scsi_generic)
UDEV  [1225540844.651107] remove   /class/scsi_device/6:0:0:0 (scsi_device)
UDEV  [1225540844.652989] remove   /class/scsi_disk/6:0:0:0 (scsi_disk)
UDEV  [1225540844.708680] remove   /block/sdb (block)
UDEV  [1225540844.719389] remove   /devices/pci0000:00/0000:00:1d.7/usb7/7-2/7-2:1.0/host6/target6:0:0/6:0:0:0 (scsi)
UDEV  [1225540844.738326] remove   /class/scsi_host/host6 (scsi_host)
UDEV  [1225540844.738951] remove   /devices/pci0000:00/0000:00:1d.7/usb7/7-2/7-2:1.0 (usb)
UDEV  [1225540844.790744] remove   /devices/pci0000:00/0000:00:1d.7/usb7/7-2/usb_endpoint/usbdev7.5_ep00 (usb_endpoint)
UDEV  [1225540844.806742] remove   /devices/pci0000:00/0000:00:1d.7/usb7/7-2 (usb)
UEVENT[1225540845.119478] remove   /devices/pci0000:00/0000:00:1d.0/usb3/3-1/3-1:1.0/usb_endpoint/usbdev3.3_ep81 (usb_endpoint)
UEVENT[1225540845.119521] remove   /devices/pci0000:00/0000:00:1d.0/usb3/3-1/3-1:1.0/input/input13/mouse1 (input)
UDEV  [1225540845.121116] remove   /devices/pci0000:00/0000:00:1d.0/usb3/3-1/3-1:1.0/usb_endpoint/usbdev3.3_ep81 (usb_endpoint)
UDEV  [1225540845.122631] remove   /devices/pci0000:00/0000:00:1d.0/usb3/3-1/3-1:1.0/input/input13/mouse1 (input)
UEVENT[1225540845.130893] remove   /devices/pci0000:00/0000:00:1d.0/usb3/3-1/3-1:1.0/input/input13/event2 (input)
UDEV  [1225540845.134977] remove   /devices/pci0000:00/0000:00:1d.0/usb3/3-1/3-1:1.0/input/input13/event2 (input)
UEVENT[1225540845.163131] remove   /devices/pci0000:00/0000:00:1d.0/usb3/3-1/3-1:1.0/input/input13 (input)
UEVENT[1225540845.163175] remove   /devices/virtual/hidraw/hidraw0 (hidraw)
UEVENT[1225540845.163189] remove   /devices/pci0000:00/0000:00:1d.0/usb3/3-1/3-1:1.0 (usb)
UEVENT[1225540845.163202] remove   /devices/pci0000:00/0000:00:1d.0/usb3/3-1/usb_endpoint/usbdev3.3_ep00 (usb_endpoint)
UEVENT[1225540845.163216] remove   /devices/pci0000:00/0000:00:1d.0/usb3/3-1 (usb)
UDEV  [1225540845.164410] remove   /devices/pci0000:00/0000:00:1d.0/usb3/3-1/3-1:1.0/input/input13 (input)
UDEV  [1225540845.166676] remove   /devices/virtual/hidraw/hidraw0 (hidraw)
UDEV  [1225540845.168207] remove   /devices/pci0000:00/0000:00:1d.0/usb3/3-1/3-1:1.0 (usb)
UDEV  [1225540845.170840] remove   /devices/pci0000:00/0000:00:1d.0/usb3/3-1/usb_endpoint/usbdev3.3_ep00 (usb_endpoint)
UDEV  [1225540845.172200] remove   /devices/pci0000:00/0000:00:1d.0/usb3/3-1 (usb)
UEVENT[1225540845.450271] add      /devices/pci0000:00/0000:00:1d.0/usb3/3-1 (usb)
UEVENT[1225540845.450355] add      /devices/pci0000:00/0000:00:1d.0/usb3/3-1/usb_endpoint/usbdev3.4_ep00 (usb_endpoint)
UEVENT[1225540845.453223] add      /devices/pci0000:00/0000:00:1d.0/usb3/3-1/3-1:1.0 (usb)
UDEV  [1225540845.456892] add      /devices/pci0000:00/0000:00:1d.0/usb3/3-1 (usb)
UDEV  [1225540845.459870] add      /devices/pci0000:00/0000:00:1d.0/usb3/3-1/usb_endpoint/usbdev3.4_ep00 (usb_endpoint)
UEVENT[1225540845.467024] add      /devices/pci0000:00/0000:00:1d.0/usb3/3-1/3-1:1.0/input/input14 (input)
UEVENT[1225540845.485812] add      /devices/pci0000:00/0000:00:1d.0/usb3/3-1/3-1:1.0/input/input14/mouse1 (input)
UEVENT[1225540845.509840] add      /devices/pci0000:00/0000:00:1d.0/usb3/3-1/3-1:1.0/input/input14/event2 (input)
UEVENT[1225540845.509870] add      /devices/virtual/hidraw/hidraw0 (hidraw)
UEVENT[1225540845.509879] add      /devices/pci0000:00/0000:00:1d.0/usb3/3-1/3-1:1.0/usb_endpoint/usbdev3.4_ep81 (usb_endpoint)
UDEV  [1225540845.511070] add      /devices/virtual/hidraw/hidraw0 (hidraw)
UDEV  [1225540845.530890] add      /devices/pci0000:00/0000:00:1d.0/usb3/3-1/3-1:1.0 (usb)
UDEV  [1225540845.558787] add      /devices/pci0000:00/0000:00:1d.0/usb3/3-1/3-1:1.0/usb_endpoint/usbdev3.4_ep81 (usb_endpoint)
UDEV  [1225540845.574283] add      /devices/pci0000:00/0000:00:1d.0/usb3/3-1/3-1:1.0/input/input14 (input)
UDEV  [1225540845.581910] add      /devices/pci0000:00/0000:00:1d.0/usb3/3-1/3-1:1.0/input/input14/mouse1 (input)
UDEV  [1225540845.596828] add      /devices/pci0000:00/0000:00:1d.0/usb3/3-1/3-1:1.0/input/input14/event2 (input)
UEVENT[1225540883.310160] remove   /devices/pci0000:00/0000:00:1d.0/usb3/3-1/3-1:1.0/usb_endpoint/usbdev3.4_ep81 (usb_endpoint)
UEVENT[1225540883.310217] remove   /devices/pci0000:00/0000:00:1d.0/usb3/3-1/3-1:1.0/input/input14/mouse1 (input)
UDEV  [1225540883.312214] remove   /devices/pci0000:00/0000:00:1d.0/usb3/3-1/3-1:1.0/usb_endpoint/usbdev3.4_ep81 (usb_endpoint)
UDEV  [1225540883.314839] remove   /devices/pci0000:00/0000:00:1d.0/usb3/3-1/3-1:1.0/input/input14/mouse1 (input)
UEVENT[1225540883.321813] remove   /devices/pci0000:00/0000:00:1d.0/usb3/3-1/3-1:1.0/input/input14/event2 (input)
UDEV  [1225540883.324787] remove   /devices/pci0000:00/0000:00:1d.0/usb3/3-1/3-1:1.0/input/input14/event2 (input)
UEVENT[1225540883.339146] remove   /devices/pci0000:00/0000:00:1d.0/usb3/3-1/3-1:1.0/input/input14 (input)
UEVENT[1225540883.339188] remove   /devices/virtual/hidraw/hidraw0 (hidraw)
UEVENT[1225540883.339209] remove   /devices/pci0000:00/0000:00:1d.0/usb3/3-1/3-1:1.0 (usb)
UEVENT[1225540883.339228] remove   /devices/pci0000:00/0000:00:1d.0/usb3/3-1/usb_endpoint/usbdev3.4_ep00 (usb_endpoint)
UEVENT[1225540883.339248] remove   /devices/pci0000:00/0000:00:1d.0/usb3/3-1 (usb)
UDEV  [1225540883.340955] remove   /devices/pci0000:00/0000:00:1d.0/usb3/3-1/3-1:1.0/input/input14 (input)
UDEV  [1225540883.342709] remove   /devices/virtual/hidraw/hidraw0 (hidraw)
UDEV  [1225540883.348573] remove   /devices/pci0000:00/0000:00:1d.0/usb3/3-1/3-1:1.0 (usb)
UDEV  [1225540883.350653] remove   /devices/pci0000:00/0000:00:1d.0/usb3/3-1/usb_endpoint/usbdev3.4_ep00 (usb_endpoint)
UDEV  [1225540883.361309] remove   /devices/pci0000:00/0000:00:1d.0/usb3/3-1 (usb)
UEVENT[1225540883.683977] add      /devices/pci0000:00/0000:00:1d.0/usb3/3-1 (usb)
UEVENT[1225540883.684555] add      /devices/pci0000:00/0000:00:1d.0/usb3/3-1/usb_endpoint/usbdev3.5_ep00 (usb_endpoint)
UDEV  [1225540883.687292] add      /devices/pci0000:00/0000:00:1d.0/usb3/3-1 (usb)
UDEV  [1225540883.690219] add      /devices/pci0000:00/0000:00:1d.0/usb3/3-1/usb_endpoint/usbdev3.5_ep00 (usb_endpoint)
UEVENT[1225540883.708219] add      /devices/pci0000:00/0000:00:1d.0/usb3/3-1/3-1:1.0/input/input15 (input)
UEVENT[1225540883.725775] add      /devices/pci0000:00/0000:00:1d.0/usb3/3-1/3-1:1.0/input/input15/mouse1 (input)
UEVENT[1225540883.757713] add      /devices/pci0000:00/0000:00:1d.0/usb3/3-1/3-1:1.0/input/input15/event2 (input)
UEVENT[1225540883.757742] add      /devices/virtual/hidraw/hidraw0 (hidraw)
UEVENT[1225540883.758018] add      /devices/pci0000:00/0000:00:1d.0/usb3/3-1/3-1:1.0/usb_endpoint/usbdev3.5_ep81 (usb_endpoint)
UDEV  [1225540883.759090] add      /devices/virtual/hidraw/hidraw0 (hidraw)
UDEV  [1225540883.762549] add      /devices/pci0000:00/0000:00:1d.0/usb3/3-1/3-1:1.0 (usb)
UDEV  [1225540883.764465] add      /devices/pci0000:00/0000:00:1d.0/usb3/3-1/3-1:1.0/usb_endpoint/usbdev3.5_ep81 (usb_endpoint)
UDEV  [1225540883.834769] add      /devices/pci0000:00/0000:00:1d.0/usb3/3-1/3-1:1.0/input/input15 (input)
UDEV  [1225540883.842675] add      /devices/pci0000:00/0000:00:1d.0/usb3/3-1/3-1:1.0/input/input15/event2 (input)
UDEV  [1225540883.859208] add      /devices/pci0000:00/0000:00:1d.0/usb3/3-1/3-1:1.0/input/input15/mouse1 (input)

```

Also while plugout & plugin dmesg gives the following:
```
[ 1911.206073] usb 7-2: USB disconnect, address 6
[ 1911.704342] hub 3-0:1.0: port 1 disabled by hub (EMI?), re-enabling...
[ 1911.704350] usb 3-1: USB disconnect, address 5
[ 1911.840099] usb 3-1: new low speed USB device using uhci_hcd and address 6
[ 1911.921983] usb 3-1: configuration #1 chosen from 1 choice
[ 1911.945229] input: Logitech USB-PS/2 Optical Mouse as /devices/pci0000:00/0000:00:1d.0/usb3/3-1/3-1:1.0/input/input16
[ 1911.995264] input,hidraw0: USB HID v1.10 Mouse [Logitech USB-PS/2 Optical Mouse] on usb-0000:00:1d.0-1
[ 1930.385499] usb 7-2: new high speed USB device using ehci_hcd and address 7
[ 1930.443360] usb 7-2: configuration #1 chosen from 1 choice
[ 1930.455349] scsi8 : SCSI emulation for USB Mass Storage devices
[ 1930.456794] usb-storage: device found at 7
[ 1930.456801] usb-storage: waiting for device to settle before scanning
[ 1933.296079] usb-storage: device scan complete
[ 1933.296914] scsi 8:0:0:0: Direct-Access                                    PQ: 0 ANSI: 2 CCS
[ 1933.303973] sd 8:0:0:0: [sdb] Attached SCSI disk
[ 1933.304057] sd 8:0:0:0: Attached scsi generic sg2 type 0

```

And something really strange, in dmesg, while the adpater is plugged there sometimes come messages like
```
[  879.967209] FAT: utf8 is not a recommended IO charset for FAT filesystems, filesystem will be case sensitive!
[  879.967237] FAT: unable to read boot sector
[  879.969262] FAT: unable to read boot sector
[  880.108478] hfs: unable to find HFS+ superblock
[  880.111005] hfs: unable to find HFS+ superblock
[  880.141300] hfs: can't find a HFS filesystem on dev sdb.
[  880.143113] hfs: can't find a HFS filesystem on dev sdb.
[  880.232284] EXT3-fs: unable to read superblock
[  880.234519] EXT3-fs: unable to read superblock
[  880.277593] EXT2-fs: unable to read superblock
[  880.279645] EXT2-fs: unable to read superblock
[  880.281528] ReiserFS: sdb: warning: sh-2006: read_super_block: bread failed (dev sdb, block 2, size 4096)
[  880.281545] ReiserFS: sdb: warning: sh-2006: read_super_block: bread failed (dev sdb, block 16, size 4096)
[  880.281547] ReiserFS: sdb: warning: sh-2021: reiserfs_fill_super: can not find reiserfs on sdb
[  880.283191] ReiserFS: sdb: warning: sh-2006: read_super_block: bread failed (dev sdb, block 2, size 4096)
[  880.283206] ReiserFS: sdb: warning: sh-2006: read_super_block: bread failed (dev sdb, block 16, size 4096)
[  880.283209] ReiserFS: sdb: warning: sh-2021: reiserfs_fill_super: can not find reiserfs on sdb
[  880.404237] SGI XFS with ACLs, security attributes, realtime, large block numbers, no debug enabled
[  880.404700] SGI XFS Quota Management subsystem
[  880.404914] XFS: SB read failed
[  880.407166] XFS: SB read failed
[  880.443947] JFS: nTxBlock = 8192, nTxLock = 65536
[  893.209983] UDF-fs: No partition found (1)
[  893.218340] UDF-fs: No partition found (1)
[  893.223476] isofs_fill_super: bread failed, dev=sdb, iso_blknum=16, block=32
[  893.228766] isofs_fill_super: bread failed, dev=sdb, iso_blknum=16, block=32
[  893.233436] FAT: utf8 is not a recommended IO charset for FAT filesystems, filesystem will be case sensitive!
[  893.233640] FAT: unable to read boot sector
[  893.235491] FAT: unable to read boot sector
[  893.249983] hfs: unable to find HFS+ superblock
[  893.251869] hfs: unable to find HFS+ superblock
[  893.253770] hfs: can't find a HFS filesystem on dev sdb.
[  893.255696] hfs: can't find a HFS filesystem on dev sdb.
[  893.257640] EXT3-fs: unable to read superblock
[  893.259460] EXT3-fs: unable to read superblock
[  893.261143] EXT2-fs: unable to read superblock
[  893.262877] EXT2-fs: unable to read superblock
[  893.264567] ReiserFS: sdb: warning: sh-2006: read_super_block: bread failed (dev sdb, block 2, size 4096)
[  893.264583] ReiserFS: sdb: warning: sh-2006: read_super_block: bread failed (dev sdb, block 16, size 4096)
[  893.264585] ReiserFS: sdb: warning: sh-2021: reiserfs_fill_super: can not find reiserfs on sdb
[  893.266263] ReiserFS: sdb: warning: sh-2006: read_super_block: bread failed (dev sdb, block 2, size 4096)
[  893.266279] ReiserFS: sdb: warning: sh-2006: read_super_block: bread failed (dev sdb, block 16, size 4096)
[  893.266281] ReiserFS: sdb: warning: sh-2021: reiserfs_fill_super: can not find reiserfs on sdb
[  893.332551] XFS: SB read failed
[  893.334319] XFS: SB read failed

```

Since i would like to edit the defined partitions on that hard disk, i also opened gparted, but it only shows the hard disk sda.
fdisk also isn't able to look at sdb
```
kaefert@Mobulux:~$ sudo fdisk /dev/sdb

Konnte /dev/sdb nicht lesen
kaefert@Mobulux:~$ 

```

If anybody has a idea how to solve this problem, please tell me.

---

### Post by GoldWing on 2009-03-07
did you find a solution now for this one ?
I have exactly the same device (conceptronic USB connector for IDE & SATA drives), but the Jmicron seems to need a driver, I guess.
It recognizes a /dev/sdd with me, but I can't fdisk it.

---

### Post by camel1cz on 2009-03-31
Have the same problem? Any info?

For me it doesn't work even under WinXP, Vista... strange, it's already second device I try - different manufacturer, the same chip.

---

### Post by camel1cz on 2009-03-31
Hm, have now tried different hard drive and it simply works. So there seems to be some incompatibility between the adapter and some types of hard drives.

For me my old IBM DeskStar - Model IC35L060AVER07-0 ATA/IDE 60GB works but much newer Seagate Barracuda 7200.7 Model ST380011A ATA/IDE 80GB does not.

---

### Post by bryhhh on 2009-03-31
I've just had this exact problem, and it was caused by me plugging in the USB interface before connecting the disk.

Once I unplugged the USB device and reconnected it with the disk already connected, everything worked fine.

---

### Post by VitaLiNux on 2010-01-09
I got an adapter with that Jmicron chip. It's been giving me just headaches! Does anyone have come up with a solution?

---

### Post by georgeprout on 2010-01-15
I also have one of these, it's worked fine under Gutsy onwards (I'm currently running Koala).  There was a quality issue, the (UK) mains plug was not correctly fitted - the retaining screws hadn't been done up on either the earth or neutral pins.  Easily fixed and that solved the intermittent problem that I had initially.

Make sure you power the drive up first, let it settle for a short while and then plug the USB in.  No drivers needed, it just works with every disk that I've thrown at it (IDE/SATA/laptop).

(Even the one from my Sony HDD recorder, which is a non-standard file system that I couldn't mount for love nor money - but I was still able to dd an image from it.  That's another story anyway)


HTH
George

---

### Post by foxvan on 2010-09-12
I am havin the same problem. I'm using Ubuntu Lucid 10.4 kernel  2.6.32-25

I have a SATA disk of 1 TB and a JMicron USB adapter. The output of dmesg | tail is:

```

[ 2281.672832] usb 2-3: new high speed USB device using ehci_hcd and address 5
[ 2281.822614] usb 2-3: configuration #1 chosen from 1 choice
[ 2281.824017] scsi9 : SCSI emulation for USB Mass Storage devices
[ 2281.824374] usb-storage: device found at 5
[ 2281.824379] usb-storage: waiting for device to settle before scanning
[ 2286.820687] usb-storage: device scan complete
[ 2286.821540] scsi 9:0:0:0: Direct-Access                                    PQ: 0 ANSI: 2 CCS
[ 2286.822329] sd 9:0:0:0: Attached scsi generic sg2 type 0
[ 2286.825526] sd 9:0:0:0: [sdb] Attached SCSI disk

```

The disk utility recognizes the device but not any partition.

---

### Post by latz-twn on 2010-10-07
Hi,

I have exactly the same problem, the device I bought is a Freecom Hard Drive Dock and in lsusb it shows me the chip is the *JMicron Technology Corp. / JMicron USA Technology Corp. transcend storejet 25P*. I've a 1TB Western Digital Drive attached to it with an NTFS partition on it. In dmesg it only shows me that the drive sdb has been found but no partitions what so ever. cfdisk /dev/sdb gives me an error. Here are the details.

I am already happy that I am not the only one with this problem, although it's a shame it doesn't work, well hopefully with the next kernel release we'll be a bit luckier :).


**lshw** output
```

*-generic:0
                description: System peripheral
                product: SD/MMC Host Controller
                vendor: JMicron Technology Corp.
                physical id: 0
                bus info: pci@0000:02:00.0
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pm pciexpress msi bus_master cap_list rom
                configuration: driver=sdhci-pci latency=0
                resources: irq:16 memory:f4500000-f45000ff memory:c0000000-c000ffff(prefetchable)
           *-generic:1 UNCLAIMED
                description: SD Host controller
                product: Standard SD Host Controller
                vendor: JMicron Technology Corp.
                physical id: 0.2
                bus info: pci@0000:02:00.2
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pm pciexpress msi cap_list
                configuration: latency=0
                resources: memory:f4500400-f45004ff
           *-generic:2
                description: System peripheral
                product: MS Host Controller
                vendor: JMicron Technology Corp.
                physical id: 0.3
                bus info: pci@0000:02:00.3
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pm pciexpress msi bus_master cap_list
                configuration: driver=jmb38x_ms latency=0

```

**dmesg** output
```

[ 2141.343035] usb-storage: device found at 7
[ 2141.343039] usb-storage: waiting for device to settle before scanning
[ 2146.342927] usb-storage: device scan complete
[ 2159.089256] scsi 6:0:0:0: Direct-Access                                    PQ: 0 ANSI: 2 CCS
[ 2159.090011] sd 6:0:0:0: Attached scsi generic sg2 type 0
[ 2175.548640] sd 6:0:0:0: [sdb] Attached SCSI disk

```


**cfdisk** output
```

FATAL ERROR: Cannot read disk drive

```


Thx for your attention.

---

### Post by slashmax on 2010-11-15
I'm having the same problem, except with a SSD. Anyone find a fix? Thanks!

---

### Post by drave40 on 2010-12-28
Just in case anyone still has this problem ( I did, that's how i landed here)

disconnect from USB
find jmicron driver. on my system it's called "pata_jmicron"
load it, "modprobe pata_jmicron"
connect to USB gain

dahdah everything is visible. well, it is here

cheers

---

### Post by RedPenguin on 2011-10-09
Thank you **drave40**, I never thought I needed an extra module being that it "worked" but I noticed even the minute I added this module, the IDE/Busy light actually worked on SATA, so it definitely seems to have better support.

It was driving me crazy, I was trying to clone a 200GB to my new 2TB but I kept getting USB disconnects of echi_hcd on the 200GB but so far it appears to work now.

EDIT: LoL, I got a random reset message again but yet it must have "recovered" because data is still flowing.

EDIT #2: dmesg shows like 8 resets yet the drive is still "working", so I dunno.

---

### Post by reikred on 2011-11-25
Drave40, I used your recipe once with success, but thereafter I have not been able to bring up  my IDE drive (/dev/sdc, as it happens) viamy  jmicron usb-ide adapter again.

Are there any other details that need to be considered? I have tried a bunch of stuff, such as

modprobe -r pata_jmicron
modprobe    pata_jmicron

One observation I have made is that when I unplug/replug the Jmicron USB, there are no new messages from dmesg. However, if I unplug, then plug in some other USB device (a flash card reader in my case),  then unplug flashreader and replug the Jmicron usb device, then both the card reader and then the Jmicron will appear one after the other in dmesg and also successively in lsusb.

I have tried a bunch of permutations of unplug, modprobe -r pata_jmicron, plug/unplug  cardreader,  modprobe pata_jmicron and replug jmicron. None of the permutations I tried so far have made /dev/sdc appear in fdisk -l. It just worked that one time, an I do not understand what I did differently.

I did boot the machine once as well, but perhaps not in combination with ALL the other permutations that I tried.

Is the anything else I need to try? Does the usb_storage.ko module play a part? Are there any other ahci or ehci or ohci things I need to worry about? 

I have specifically (un)jumpered the IDE hard drive so that it is MASTER, as I have seen problems before with usb-ide adapters when drive is jumpered as cable-select or slave.

I should perhaps also mention that there is never a problem when I attach a SATA drive with the same Jmicron adapter. That always works, no problems of any kind. It is just the IDE that worked only that one time.

I'm running fedora core 14, but I don't think that matters in this context.

---

### Post by reikred on 2011-11-28
WOW, I just discovered something mind-blowingly simple and stupid that was causing 95% of my problems with usb-to-ide adapters:

IDE CONNECTOR MISALIGNMENT

Read that again: IDE connector misalignment. 

Here is the story. I have a number of these no-brand (but Jmicron-based)  usb/ide/sata adapters, and they all have three fundamental mechanical  flaws:

1. the IDE plug is about 2mm narrower than it should be

2. the IDE guide-tab is not tall enough to block misaligned or upside-down insertion
   
 and, MOST IMPORTANTLY,

3. the IDE pin-20 "key" position on the adapter (female side) is open, but should be filled/blocked to act as a "key" that blocks offset  or upside-down insertion.

Because of these three flaws, it is very easy to offset the connector by +-1 pin, and it happened to me all the time because I tended to align the connector with the outer edge of the drive-side connector sleeve.

Note that the usb side of the adapter will still work, and dmesg will happily report that drive sdc (say) is up an running. Even if the adapter is misaligned so that the IDE side of the adapter is not talking to the drive at all. The net result is that nothing works, no partitions are reported, etc, etc.

I wonder how many people are having a mechanical alignment problem, but think they are having a software problem?

Note also that on the mini-IDE side if the adapter, the ""key" hole is properly blocked/filled. Hence the mini-IDE always works, no misalignment is possible.

I also found that there never was a need for loading the module pata_jmicron.ko. It was a red herring. I just happened to plug a drive correctly aligned at the same time I tried to load the module, so it looked like the module had an effect.

Finally, for the other 5% trouble cases, the cause is that the IDE drive was not properly jumpered as MASTER.  The adapters (at least the JMicron-based ones)  do NOT accept drives jumpered as SLAVE or CABLE-SELECT. The interface will then repeatedly reset and so on.

Hope this helps.

---

