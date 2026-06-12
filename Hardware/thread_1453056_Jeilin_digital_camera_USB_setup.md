---
title: "Jeilin digital camera USB setup"
date: 2010-04-12
forum: Hardware
---

### Post by Kimos on 2010-04-12
I've got an extremely inexpensive digital camera we got on vacation. It's water proof and has pretty much no markings on it and no software. I'm trying to get it to recognize.

Any help troubleshooting this is appreciated.

from dmesg:
```

[67353.395365] usb 5-1: new full speed USB device using uhci_hcd and address 3
[67353.629196] usb 5-1: configuration #1 chosen from 1 choice

```

from lsusb:


```

Bus 005 Device 003: ID 0979:0227 Jeilin Technology Corp., Ltd 
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.10
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0         8
  idVendor           0x0979 Jeilin Technology Corp., Ltd
  idProduct          0x0227 
  bcdDevice            1.00
  iManufacturer           1 Jeilin
  iProduct                2 USB 1.1 Device
  iSerial                 0 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           46
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0x80
      (Bus Powered)
    MaxPower              500mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           4
      bInterfaceClass         0 (Defined at Interface level)
      bInterfaceSubClass      0 
      bInterfaceProtocol      0 
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x01  EP 1 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x82  EP 2 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x03  EP 3 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0008  1x 8 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x84  EP 4 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0008  1x 8 bytes
        bInterval               0
Device Status:     0x0000
  (Bus Powered)


```

---

### Post by _patrice_ on 2010-10-26
Hi

This camera is supported with ubuntu 10.04.
This cam supports dual mode.

first mode, plug the USB cable, it will be recognized as a mass storage device.

Second mode, press button while plugging the USB cable, it will be recognized as a web cam.

bye

---

