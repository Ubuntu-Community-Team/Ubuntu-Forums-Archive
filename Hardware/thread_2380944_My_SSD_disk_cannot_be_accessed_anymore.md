---
title: "My SSD disk cannot be accessed anymore"
date: 2017-12-24
forum: Hardware
---

### Post by leolivier on 2017-12-24
Hello,
I  bought a while ago a small external SSD (Lexar Workflow256) connected through USB to my RaspberryPi.
Yesterday it started to freeze so I plugged it into my laptop (Linux Mint) and did an lsusb which showed it:
```
Bus 002 Device 008: ID 05dc:ba09 Lexar Media, Inc. 
```

But fdisk -l didn't show it.
Then lsusb -v on the device:
```
$ sudo lsusb -v -s 002:008

Bus 002 Device 008: ID 05dc:ba09 Lexar Media, Inc. 
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.10
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  idVendor           0x05dc Lexar Media, Inc.
  idProduct          0xba09 
  bcdDevice           91.02
  iManufacturer           2 Lexar
  iProduct                3 WorkflowD256
  iSerial                 1 24060350201386
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           85
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0x80
      (Bus Powered)
    MaxPower              498mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           2
      bInterfaceClass         8 Mass Storage
      bInterfaceSubClass      6 SCSI
      bInterfaceProtocol     80 Bulk-Only
      iInterface              0 
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
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       1
      bNumEndpoints           4
      bInterfaceClass         8 Mass Storage
      bInterfaceSubClass      6 SCSI
      bInterfaceProtocol     98 
      iInterface              0 
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
        Data-in pipe (0x03)
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
        Data-out pipe (0x04)
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x83  EP 3 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0
        Status pipe (0x02)
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x04  EP 4 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0
        Command pipe (0x01)
Binary Object Store Descriptor:
  bLength                 5
  bDescriptorType        15
  wTotalLength           22
  bNumDeviceCaps          2
  USB 2.0 Extension Device Capability:
    bLength                 7
    bDescriptorType        16
    bDevCapabilityType      2
    bmAttributes   0x00000002
      Link Power Management (LPM) Supported
  SuperSpeed USB Device Capability:
    bLength                10
    bDescriptorType        16
    bDevCapabilityType      3
    bmAttributes         0x00
    wSpeedsSupported   0x000e
      Device can operate at Full Speed (12Mbps)
      Device can operate at High Speed (480Mbps)
      Device can operate at SuperSpeed (5Gbps)
    bFunctionalitySupport   1
      Lowest fully-functional device speed is Full Speed (12Mbps)
    bU1DevExitLat          10 micro seconds
    bU2DevExitLat        2047 micro seconds
Device Status:     0x0000
  (Bus Powered)

```
So I looked at dmesg and this gives:

```
[42520.896981] sd 6:0:0:0: [sdc] Read Capacity(16) failed: Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[42520.896990] sd 6:0:0:0: [sdc] Sense Key : Not Ready [current] 
[42520.896994] sd 6:0:0:0: [sdc] Add. Sense: Logical unit is in process of becoming ready
[42541.747070] sd 6:0:0:0: [sdc] Read Capacity(10) failed: Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[42541.747078] sd 6:0:0:0: [sdc] Sense Key : Not Ready [current] 
[42541.747082] sd 6:0:0:0: [sdc] Add. Sense: Logical unit is in process of becoming ready
[42541.748129] sd 6:0:0:0: [sdc] 0 512-byte logical blocks: (0 B/0 B)
[42541.748134] sd 6:0:0:0: [sdc] 0-byte physical blocks
[42562.597233] sd 6:0:0:0: [sdc] Test WP failed, assume Write Enabled
[42569.547130] sd 6:0:0:0: [sdc] Asking for cache data failed
[42569.547136] sd 6:0:0:0: [sdc] Assuming drive cache: write through
[42569.548486] sd 6:0:0:0: [sdc] Spinning up disk...
[42569.549215] sd 6:0:0:0: [sdc] Spinning up disk...
[42570.556111] .
[42570.556126] .
[42571.580080] .
[42571.580090] .

```
and later again:
```
[43030.313646] sd 6:0:0:0: [sdc] Read Capacity(16) failed: Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[43030.313651] sd 6:0:0:0: [sdc] Sense Key : Not Ready [current] 
[43030.313653] sd 6:0:0:0: [sdc] Add. Sense: Logical unit is in process of becoming ready
[43051.159806] sd 6:0:0:0: [sdc] Read Capacity(10) failed: Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[43051.159813] sd 6:0:0:0: [sdc] Sense Key : Not Ready [current] 
[43051.159817] sd 6:0:0:0: [sdc] Add. Sense: Logical unit is in process of becoming ready
[43078.955171] sd 6:0:0:0: [sdc] Spinning up disk...


```

And just after plugin:
```

[46788.584192] usb 2-1.3: new high-speed USB device number 9 using ehci-pci
[46788.739443] usb 2-1.3: New USB device found, idVendor=05dc, idProduct=ba09
[46788.739451] usb 2-1.3: New USB device strings: Mfr=2, Product=3, SerialNumber=1
[46788.739457] usb 2-1.3: Product: WorkflowD256
[46788.739461] usb 2-1.3: Manufacturer: Lexar
[46788.739465] usb 2-1.3: SerialNumber: 24060350201386
[46788.741463] scsi host6: uas
[46788.743673] scsi 6:0:0:0: Direct-Access     Lexar    WorkflowD256     0    PQ: 0 ANSI: 6
[46788.808720] sd 6:0:0:0: Attached scsi generic sg3 type 0
[46788.809299] sd 6:0:0:0: [sdc] Spinning up disk...

```

Any idea of at least a way to dump it on another disk?

---

### Post by Autodave on 2017-12-24
You can try booting the machine with a USB or DVD install disc. Chose TRY ?BUNTU and see if you can then mount the disc and see anything on it. Be prepared to instantly transfer anything to another drive, USB stick, etc: it could be the last time you can access it.

---

### Post by leolivier on 2017-12-26
@Autodave, as I said, I plugged this disk on another Linux laptop and it  didn't show anything but the lsub stuff so no chance to get it working  this way...

---

