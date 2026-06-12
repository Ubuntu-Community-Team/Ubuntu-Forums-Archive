---
title: "USB front panel port disconnecting &amp; reconnecting"
date: 2007-04-13
forum: Hardware &amp; Laptops
---

### Post by elpaw on 2007-04-13
I have a In-Win CR-i100 USB front panel memory card reader. however, it keeps on disconnecting & reconnecting every 3 seconds. The LED on the reader flashes when it does this. 

This is an example *dmesg* output:

```
[ 1498.673508] usb 2-2: new full speed USB device using uhci_hcd and address 11
[ 1498.866367] usb 2-2: configuration #1 chosen from 1 choice
[ 1498.871436] scsi526 : SCSI emulation for USB Mass Storage devices
[ 1498.871516] usb-storage: device found at 11
[ 1498.871518] usb-storage: waiting for device to settle before scanning
[ 1500.445977] usb 2-2: USB disconnect, address 11
[ 1501.204425] usb 2-2: new full speed USB device using uhci_hcd and address 12
[ 1501.397775] usb 2-2: configuration #1 chosen from 1 choice
[ 1501.402835] scsi527 : SCSI emulation for USB Mass Storage devices
[ 1501.402916] usb-storage: device found at 12
[ 1501.402918] usb-storage: waiting for device to settle before scanning
[ 1502.976906] usb 2-2: USB disconnect, address 12
[ 1503.735352] usb 2-2: new full speed USB device using uhci_hcd and address 13
[ 1503.928158] usb 2-2: configuration #1 chosen from 1 choice
[ 1503.933233] scsi528 : SCSI emulation for USB Mass Storage devices
[ 1503.933313] usb-storage: device found at 13
[ 1503.933315] usb-storage: waiting for device to settle before scanning
[ 1505.507833] usb 2-2: USB disconnect, address 13
[ 1506.266280] usb 2-2: new full speed USB device using uhci_hcd and address 14
[ 1506.459549] usb 2-2: configuration #1 chosen from 1 choice
[ 1506.464625] scsi529 : SCSI emulation for USB Mass Storage devices
[ 1506.464704] usb-storage: device found at 14
[ 1506.464706] usb-storage: waiting for device to settle before scanning
```

and it repeats ad nauseam.

It also makes the Hardware Info run at 100% cpu and hang.

How can I fix this?

This isn't a problem in WinXP, so it's not the hardware that's at fault.

Also, it's not techincally ubuntu, as this problem has been present in every distibution of linux I've tried.

I'm on 7.04 beta

---

### Post by matgates on 2007-05-20
Setting up a machine for a friend I am seeing a similar thing.   don't get 100% CPU usage, but I get the excessive dmesg output and the device in un-usable.

lsusb output for device:

Bus 002 Device 125: ID 10df:0100 In-Win Development, Inc. 
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.10
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0         8
  idVendor           0x10df In-Win Development, Inc.
  idProduct          0x0100 
  bcdDevice            2.9c
  iManufacturer           1 
  iProduct                2 
  iSerial                 3 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           39
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          4 
    bmAttributes         0x80
      (Bus Powered)
    MaxPower              100mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           3
      bInterfaceClass         8 Mass Storage
      bInterfaceSubClass      6 SCSI
      bInterfaceProtocol     80 Bulk (Zip)
      iInterface              5 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x02  EP 2 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x83  EP 3 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0008  1x 8 bytes
        bInterval              10

---

