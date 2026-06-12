---
title: "want to use mediaGear Allcards II (Alcor Micro EMV Certified Smart Card Reader)"
date: 2009-11-13
forum: Hardware
---

### Post by semi-newbie on 2009-11-13
I have a mediaGear Allcards II device that has a SIM card socket and also sockets for various camera flash cards.  I would like to be able to use this device with Ubuntu Karmic.  However, I am not sure how to do so.

The relevant subset of what I get when I invoke "lsusb -v" indicates that internally it integrates some hardware from Alcor Micro:

Bus 006 Device 003: ID 058f:9520 Alcor Micro Corp. EMV Certified Smart Card Reader
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.10
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0         8
  idVendor           0x058f Alcor Micro Corp.
  idProduct          0x9520 EMV Certified Smart Card Reader
  bcdDevice           f0.33
  iManufacturer           1 ALCOR MICRO CORP
  iProduct                2 EMV Smartcard Reader
  iSerial                 0 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           93
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0x80
      (Bus Powered)
    MaxPower               50mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           3
      bInterfaceClass        11 Chip/SmartCard
      bInterfaceSubClass      0 
      bInterfaceProtocol      0 
      iInterface              0 
      ** UNRECOGNIZED:  36 21 00 01 00 03 03 00 00 00 74 0e 00 00 74 0e 00 00 01 da 26 00 00 48 db 04 00 35 fe 00 00 00 07 00 00 00 00 00 00 00 be 04 02 00 0f 01 00 00 ff ff 00 00 00 01
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0004  1x 4 bytes
        bInterval              32
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x02  EP 2 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0010  1x 16 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x83  EP 3 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0010  1x 16 bytes
        bInterval               0
Device Status:     0x0000
  (Bus Powered)

Invoking "lsscsi -v -v -lll" yields some data on the hard drives in my system, followed by:

[6:0:0:0]    disk    Generic  STORAGE DEVICE   9715  /dev/sdd
  device_blocked=0
  iocounterbits=32
  iodone_cnt=0x13
  ioerr_cnt=0x12
  iorequest_cnt=0x13
  queue_depth=1
  queue_type=none
  scsi_level=0
  state=running
  timeout=30
  type=0
  dir: /sys/bus/scsi/devices/6:0:0:0  [/sys/devices/pci0000:00/0000:00:1a.7/usb1/1-1/1-1:1.0/host6/target6:0:0/6:0:0:0]
[6:0:0:1]    disk    Generic  STORAGE DEVICE   9715  /dev/sde
  device_blocked=0
  iocounterbits=32
  iodone_cnt=0x13
  ioerr_cnt=0x12
  iorequest_cnt=0x13
  queue_depth=1
  queue_type=none
  scsi_level=0
  state=running
  timeout=30
  type=0
  dir: /sys/bus/scsi/devices/6:0:0:1  [/sys/devices/pci0000:00/0000:00:1a.7/usb1/1-1/1-1:1.0/host6/target6:0:0/6:0:0:1]
[6:0:0:2]    disk    Generic  STORAGE DEVICE   9715  /dev/sdf
  device_blocked=0
  iocounterbits=32
  iodone_cnt=0x5
  ioerr_cnt=0x4
  iorequest_cnt=0x5
  queue_depth=1
  queue_type=none
  scsi_level=0
  state=running
  timeout=30
  type=0
  dir: /sys/bus/scsi/devices/6:0:0:2  [/sys/devices/pci0000:00/0000:00:1a.7/usb1/1-1/1-1:1.0/host6/target6:0:0/6:0:0:2]
[6:0:0:3]    disk    Generic  STORAGE DEVICE   9715  /dev/sdg
  device_blocked=0
  iocounterbits=32
  iodone_cnt=0x5
  ioerr_cnt=0x4
  iorequest_cnt=0x5
  queue_depth=1
  queue_type=none
  scsi_level=0
  state=running
  timeout=30
  type=0
  dir: /sys/bus/scsi/devices/6:0:0:3  [/sys/devices/pci0000:00/0000:00:1a.7/usb1/1-1/1-1:1.0/host6/target6:0:0/6:0:0:3]
[6:0:0:4]    disk    Generic  STORAGE DEVICE   9715  /dev/sdh
  device_blocked=0
  iocounterbits=32
  iodone_cnt=0x5
  ioerr_cnt=0x4
  iorequest_cnt=0x5
  queue_depth=1
  queue_type=none
  scsi_level=0
  state=running
  timeout=30
  type=0
  dir: /sys/bus/scsi/devices/6:0:0:4  [/sys/devices/pci0000:00/0000:00:1a.7/usb1/1-1/1-1:1.0/host6/target6:0:0/6:0:0:4]

I don't really know what to do from here, though.  With a SIM card installed, attempting to mount either /dev/sdd or /dev/sde to /mnt didn't do anything useful.

Can anyone help?

---

