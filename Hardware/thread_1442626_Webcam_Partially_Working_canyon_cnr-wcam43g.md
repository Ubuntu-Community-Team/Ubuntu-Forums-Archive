---
title: "Webcam Partially Working canyon cnr-wcam43g"
date: 2010-03-30
forum: Hardware
---

### Post by Kangarooo on 2010-03-30
It has microphone that is working.
In cheese i can take pictures but not corretly they are cripled. look:
[IMG]http://kangarooo.times.lv/webcam/1.jpg[/IMG]
[IMG]http://kangarooo.times.lv/webcam/2.jpg[/IMG]
and also video is taken incoretly
[http://kangarooo.times.lv/webcam/1.ogv](http://kangarooo.times.lv/webcam/1.ogv)

But in skype totaly not working.

```
lsusb
``` shows 

```
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 04b4:0033 Cypress Semiconductor Corp. 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 0ac8:307b Z-Star Microelectronics Corp. USB 1.1 Webcam
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
```

its Z-star i tryd removing and inserting its Z-star

```
and lsusb -v
```

only about Z-Star is

```
Bus 002 Device 002: ID 0ac8:307b Z-Star Microelectronics Corp. USB 1.1 Webcam
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.10
  bDeviceClass          255 Vendor Specific Class
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0         8
  idVendor           0x0ac8 Z-Star Microelectronics Corp.
  idProduct          0x307b USB 1.1 Webcam
  bcdDevice            1.00
  iManufacturer           1 
  iProduct                2 
  iSerial                 0 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength          193
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0x80
      (Bus Powered)
    MaxPower              160mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           2
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass    255 Vendor Specific Subclass
      bInterfaceProtocol    255 Vendor Specific Protocol
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0000  1x 0 bytes
        bInterval               1
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x82  EP 2 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0008  1x 8 bytes
        bInterval              10
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       1
      bNumEndpoints           2
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass    255 Vendor Specific Subclass
      bInterfaceProtocol    255 Vendor Specific Protocol
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0080  1x 128 bytes
        bInterval               1
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x82  EP 2 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0008  1x 8 bytes
        bInterval              10
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       2
      bNumEndpoints           2
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass    255 Vendor Specific Subclass
      bInterfaceProtocol    255 Vendor Specific Protocol
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x00c0  1x 192 bytes
        bInterval               1
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x82  EP 2 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0008  1x 8 bytes
        bInterval              10
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       3
      bNumEndpoints           2
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass    255 Vendor Specific Subclass
      bInterfaceProtocol    255 Vendor Specific Protocol
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0100  1x 256 bytes
        bInterval               1
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x82  EP 2 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0008  1x 8 bytes
        bInterval              10
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       4
      bNumEndpoints           2
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass    255 Vendor Specific Subclass
      bInterfaceProtocol    255 Vendor Specific Protocol
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0180  1x 384 bytes
        bInterval               1
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x82  EP 2 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0008  1x 8 bytes
        bInterval              10
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       5
      bNumEndpoints           2
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass    255 Vendor Specific Subclass
      bInterfaceProtocol    255 Vendor Specific Protocol
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               1
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x82  EP 2 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0008  1x 8 bytes
        bInterval              10
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       6
      bNumEndpoints           2
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass    255 Vendor Specific Subclass
      bInterfaceProtocol    255 Vendor Specific Protocol
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0300  1x 768 bytes
        bInterval               1
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x82  EP 2 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0008  1x 8 bytes
        bInterval              10
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       7
      bNumEndpoints           2
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass    255 Vendor Specific Subclass
      bInterfaceProtocol    255 Vendor Specific Protocol
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0380  1x 896 bytes
        bInterval               1
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x82  EP 2 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0008  1x 8 bytes
        bInterval              10
cannot read device status, Operation not permitted (1)

```

---

### Post by Kangarooo on 2010-04-20
Another camera with the same name canyon cnr-wcam43g also has microphone but is different - it has only one wire - usb.
Camera with same name in first post has 2 wires - usb and microphone wire. Mic for 1st is working for 2nd nothing working and even making cheese to hang up- crash.

Heres some info

```
lsusb
```
shows
```
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 003: ID 046d:c016 Logitech, Inc. M-UV69a/HP M-UV96 Optical Wheel Mouse
Bus 002 Device 002: ID 093a:2620 Pixart Imaging, Inc. 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

Its Pixart Imaging, Inc. i tryd removing and inserting its Pixart Imaging, Inc.

```
and sudo lsusb -v
```

only about Pixart Imaging, Inc. is

```
Bus 002 Device 002: ID 093a:2620 Pixart Imaging, Inc.
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.10
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0
  bDeviceProtocol         0
  bMaxPacketSize0         8
  idVendor           0x093a Pixart Imaging, Inc.
  idProduct          0x2620
  bcdDevice            1.00
  iManufacturer           0
  iProduct                0
  iSerial                 0
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength          697
    bNumInterfaces          3
    bConfigurationValue     1
    iConfiguration          0
    bmAttributes         0x80
      (Bus Powered)
    MaxPower              100mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           6
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass    255 Vendor Specific Subclass
      bInterfaceProtocol    255 Vendor Specific Protocol
      iInterface              0
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
        wMaxPacketSize     0x0002  1x 2 bytes
        bInterval              50
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x04  EP 4 OUT
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0002  1x 2 bytes
        bInterval              50
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x85  EP 5 IN
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0000  1x 0 bytes
        bInterval               1
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x06  EP 6 OUT
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0000  1x 0 bytes
        bInterval               1
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       1
      bNumEndpoints           6
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass    255 Vendor Specific Subclass
      bInterfaceProtocol    255 Vendor Specific Protocol
      iInterface              0
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
        wMaxPacketSize     0x0002  1x 2 bytes
        bInterval              50
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x04  EP 4 OUT
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0002  1x 2 bytes
        bInterval              50
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x85  EP 5 IN
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0080  1x 128 bytes
        bInterval               1
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x06  EP 6 OUT
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0000  1x 0 bytes
        bInterval               1
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       2
      bNumEndpoints           6
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass    255 Vendor Specific Subclass
      bInterfaceProtocol    255 Vendor Specific Protocol
      iInterface              0
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
        wMaxPacketSize     0x0002  1x 2 bytes
        bInterval              50
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x04  EP 4 OUT
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0002  1x 2 bytes
        bInterval              50
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x85  EP 5 IN
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0100  1x 256 bytes
        bInterval               1
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x06  EP 6 OUT
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0000  1x 0 bytes
        bInterval               1
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       3
      bNumEndpoints           6
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass    255 Vendor Specific Subclass
      bInterfaceProtocol    255 Vendor Specific Protocol
      iInterface              0
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
        wMaxPacketSize     0x0002  1x 2 bytes
        bInterval              50
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x04  EP 4 OUT
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0002  1x 2 bytes
        bInterval              50
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x85  EP 5 IN
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0180  1x 384 bytes
        bInterval               1
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x06  EP 6 OUT
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0000  1x 0 bytes
        bInterval               1
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       4
      bNumEndpoints           6
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass    255 Vendor Specific Subclass
      bInterfaceProtocol    255 Vendor Specific Protocol
      iInterface              0
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
        wMaxPacketSize     0x0002  1x 2 bytes
        bInterval              50
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x04  EP 4 OUT
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0002  1x 2 bytes
        bInterval              50
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x85  EP 5 IN
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               1
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x06  EP 6 OUT
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0000  1x 0 bytes
        bInterval               1
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       5
      bNumEndpoints           6
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass    255 Vendor Specific Subclass
      bInterfaceProtocol    255 Vendor Specific Protocol
      iInterface              0
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
        wMaxPacketSize     0x0002  1x 2 bytes
        bInterval              50
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x04  EP 4 OUT
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0002  1x 2 bytes
        bInterval              50
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x85  EP 5 IN
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0280  1x 640 bytes
        bInterval               1
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x06  EP 6 OUT
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0000  1x 0 bytes
        bInterval               1
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       6
      bNumEndpoints           6
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass    255 Vendor Specific Subclass
      bInterfaceProtocol    255 Vendor Specific Protocol
      iInterface              0
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
        wMaxPacketSize     0x0002  1x 2 bytes
        bInterval              50
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x04  EP 4 OUT
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0002  1x 2 bytes
        bInterval              50
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x85  EP 5 IN
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0300  1x 768 bytes
        bInterval               1
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x06  EP 6 OUT
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0000  1x 0 bytes
        bInterval               1
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       7
      bNumEndpoints           6
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass    255 Vendor Specific Subclass
      bInterfaceProtocol    255 Vendor Specific Protocol
      iInterface              0
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
        wMaxPacketSize     0x0002  1x 2 bytes
        bInterval              50
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x04  EP 4 OUT
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0002  1x 2 bytes
        bInterval              50
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x85  EP 5 IN
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0380  1x 896 bytes
        bInterval               1
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x06  EP 6 OUT
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0000  1x 0 bytes
        bInterval               1
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       8
      bNumEndpoints           6
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass    255 Vendor Specific Subclass
      bInterfaceProtocol    255 Vendor Specific Protocol
      iInterface              0
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
        wMaxPacketSize     0x0002  1x 2 bytes
        bInterval              50
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x04  EP 4 OUT
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0002  1x 2 bytes
        bInterval              50
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x85  EP 5 IN
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x03ff  1x 1023 bytes
        bInterval               1
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x06  EP 6 OUT
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0000  1x 0 bytes
        bInterval               1
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        1
      bAlternateSetting       0
      bNumEndpoints           0
      bInterfaceClass         1 Audio
      bInterfaceSubClass      1 Control Device
      bInterfaceProtocol      0
      iInterface              0
      AudioControl Interface Descriptor:
        bLength                 9
        bDescriptorType        36
        bDescriptorSubtype      1 (HEADER)
        bcdADC               1.00
        wTotalLength           39
        bInCollection           1
        baInterfaceNr( 0)       2
      AudioControl Interface Descriptor:
        bLength                12
        bDescriptorType        36
        bDescriptorSubtype      2 (INPUT_TERMINAL)
        bTerminalID             1
        wTerminalType      0x0201 Microphone
        bAssocTerminal          0
        bNrChannels             1
        wChannelConfig     0x0000
        iChannelNames           0
        iTerminal               0
      AudioControl Interface Descriptor:
        bLength                 9
        bDescriptorType        36
        bDescriptorSubtype      6 (FEATURE_UNIT)
        bUnitID                 2
        bSourceID               1
        bControlSize            2
        bmaControls( 0)      0x03
        bmaControls( 0)      0x00
          Mute
          Volume
        iFeature                0
      AudioControl Interface Descriptor:
        bLength                 9
        bDescriptorType        36
        bDescriptorSubtype      3 (OUTPUT_TERMINAL)
        bTerminalID             3
        wTerminalType      0x0101 USB Streaming
        bAssocTerminal          0
        bSourceID               2
        iTerminal               0
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        2
      bAlternateSetting       0
      bNumEndpoints           0
      bInterfaceClass         1 Audio
      bInterfaceSubClass      2 Streaming
      bInterfaceProtocol      0
      iInterface              0
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        2
      bAlternateSetting       1
      bNumEndpoints           1
      bInterfaceClass         1 Audio
      bInterfaceSubClass      2 Streaming
      bInterfaceProtocol      0
      iInterface              0
      AudioStreaming Interface Descriptor:
        bLength                 7
        bDescriptorType        36
        bDescriptorSubtype      1 (AS_GENERAL)
        bTerminalLink           3
        bDelay                  1 frames
        wFormatTag              1 PCM
      AudioStreaming Interface Descriptor:
        bLength                11
        bDescriptorType        36
        bDescriptorSubtype      2 (FORMAT_TYPE)
        bFormatType             1 (FORMAT_TYPE_I)
        bNrChannels             1
        bSubframeSize           2
        bBitResolution         16
        bSamFreqType            1 Discrete
        tSamFreq[ 0]        16000
      Endpoint Descriptor:
        bLength                 9
        bDescriptorType         5
        bEndpointAddress     0x89  EP 9 IN
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0020  1x 32 bytes
        bInterval               1
        bRefresh                0
        bSynchAddress           0
        AudioControl Endpoint Descriptor:
          bLength                 7
          bDescriptorType        37
          bDescriptorSubtype      1 (EP_GENERAL)
          bmAttributes         0x00
          bLockDelayUnits         0 Undefined
          wLockDelay              0 Undefined
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        2
      bAlternateSetting       2
      bNumEndpoints           1
      bInterfaceClass         1 Audio
      bInterfaceSubClass      2 Streaming
      bInterfaceProtocol      0
      iInterface              0
      AudioStreaming Interface Descriptor:
        bLength                 7
        bDescriptorType        36
        bDescriptorSubtype      1 (AS_GENERAL)
        bTerminalLink           3
        bDelay                  1 frames
        wFormatTag              1 PCM
      AudioStreaming Interface Descriptor:
        bLength                11
        bDescriptorType        36
        bDescriptorSubtype      2 (FORMAT_TYPE)
        bFormatType             1 (FORMAT_TYPE_I)
        bNrChannels             1
        bSubframeSize           2
        bBitResolution         16
        bSamFreqType            1 Discrete
        tSamFreq[ 0]        48000
      Endpoint Descriptor:
        bLength                 9
        bDescriptorType         5
        bEndpointAddress     0x89  EP 9 IN
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0060  1x 96 bytes
        bInterval               1
        bRefresh                0
        bSynchAddress           0
        AudioControl Endpoint Descriptor:
          bLength                 7
          bDescriptorType        37
          bDescriptorSubtype      1 (EP_GENERAL)
          bmAttributes         0x00
          bLockDelayUnits         0 Undefined
          wLockDelay              0 Undefined
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        2
      bAlternateSetting       3
      bNumEndpoints           1
      bInterfaceClass         1 Audio
      bInterfaceSubClass      2 Streaming
      bInterfaceProtocol      0
      iInterface              0
      AudioStreaming Interface Descriptor:
        bLength                 7
        bDescriptorType        36
        bDescriptorSubtype      1 (AS_GENERAL)
        bTerminalLink           3
        bDelay                  1 frames
        wFormatTag              1 PCM
      AudioStreaming Interface Descriptor:
        bLength                11
        bDescriptorType        36
        bDescriptorSubtype      2 (FORMAT_TYPE)
        bFormatType             1 (FORMAT_TYPE_I)
        bNrChannels             1
        bSubframeSize           2
        bBitResolution         16
        bSamFreqType            1 Discrete
        tSamFreq[ 0]        16000
      Endpoint Descriptor:
        bLength                 9
        bDescriptorType         5
        bEndpointAddress     0x89  EP 9 IN
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0020  1x 32 bytes
        bInterval               1
        bRefresh                0
        bSynchAddress           0
        AudioControl Endpoint Descriptor:
          bLength                 7
          bDescriptorType        37
          bDescriptorSubtype      1 (EP_GENERAL)
          bmAttributes         0x00
          bLockDelayUnits         0 Undefined
          wLockDelay              0 Undefined
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        2
      bAlternateSetting       4
      bNumEndpoints           1
      bInterfaceClass         1 Audio
      bInterfaceSubClass      2 Streaming
      bInterfaceProtocol      0
      iInterface              0
      AudioStreaming Interface Descriptor:
        bLength                 7
        bDescriptorType        36
        bDescriptorSubtype      1 (AS_GENERAL)
        bTerminalLink           3
        bDelay                  1 frames
        wFormatTag              1 PCM
      AudioStreaming Interface Descriptor:
        bLength                11
        bDescriptorType        36
        bDescriptorSubtype      2 (FORMAT_TYPE)
        bFormatType             1 (FORMAT_TYPE_I)
        bNrChannels             1
        bSubframeSize           2
        bBitResolution         16
        bSamFreqType            1 Discrete
        tSamFreq[ 0]        16000
      Endpoint Descriptor:
        bLength                 9
        bDescriptorType         5
        bEndpointAddress     0x89  EP 9 IN
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0020  1x 32 bytes
        bInterval               1
        bRefresh                0
        bSynchAddress           0
        AudioControl Endpoint Descriptor:
          bLength                 7
          bDescriptorType        37
          bDescriptorSubtype      1 (EP_GENERAL)
          bmAttributes         0x00
          bLockDelayUnits         0 Undefined
          wLockDelay              0 Undefined
Device Status:     0x0000
  (Bus Powered)
```

---

### Post by Kangarooo on 2010-08-17
Bump?

---

### Post by WanderingAlbatross on 2010-08-21
Hey, same problem here.  Mine is in the Pixart Camera.
This is a long standing problem.  I found your comment on page of the ones working on this behind the scenes.  I wish they would try to pick up the project again.  Here is the link for reference:
[http://ubuntuforums.org/archive/index.php/t-900250.html](http://ubuntuforums.org/archive/index.php/t-900250.html)

It seems the process with these is a reverse engineering type of thing.  I would love advice on how to do that.  I have a functioning version of XP we can install it in and it works seamlessly.  I could even install Vista to experiment again, though I shudder at the thought.  It seems they try to watch what it does and get it working in Linux from that.

This problem stems back to 6.10 at least.  There have been a lot of these cameras that have been cracked, but this one has not.  In one of the files I looked in mine is also called an Apollo AC-905.  We do need to use the gspca PAC7311 driver, as opposed to the uvc one.  According to: [http://www.qbik.ch/usb/devices/search_res.php?pattern=2620](http://www.qbik.ch/usb/devices/search_res.php?pattern=2620) it does/does not work ???  That is as far as I've gotten.

I have 10.04.

---

### Post by WanderingAlbatross on 2010-08-22
I looked at some of the boot up logs and system messages.  It seems it is recognized for me when the system starts better than if I plug it in later.  Even Cheese seems to work better if I have the camera plugged in before I start.  But it only works for around 30 seconds and then quits.

---

### Post by Kangarooo on 2012-12-13
Is your camera Canyon cnr-wcam43g with one wire?
Can u post lsusb && lsusb -v ?

---

### Post by Kangarooo on 2012-12-13
Now update on Ubuntu 12.04 Lubuntu
Bug report [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1090108/](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1090108/)

[IMG]https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1090108/+attachment/3459400/+files/1.png[/IMG]
[IMG]https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1090108/+attachment/3459401/+files/2.png[/IMG]
[IMG]https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1090108/+attachment/3459402/+files/3.png[/IMG]

```

juris@juris-desk-1204-overinstall-1004:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 004: ID 079b:004a Sagem XG-760A 802.11bg
Bus 002 Device 002: ID 046d:c315 Logitech, Inc. Classic New Touch Keyboard
Bus 003 Device 003: ID 15d9:0a4d Trust International B.V. 
Bus 002 Device 005: ID 0ac8:307b Z-Star Microelectronics Corp. USB 1.1 Webcam

```

```

juris@juris-desk-1204-overinstall-1004:~$ lsusb -v

Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Couldn't open device, some information will be missing
Device Descriptor:
  bLength 18
  bDescriptorType 1
  bcdUSB 2.00
  bDeviceClass 9 Hub
  bDeviceSubClass 0 Unused
  bDeviceProtocol 0 Full speed (or root) hub
  bMaxPacketSize0 64
  idVendor 0x1d6b Linux Foundation
  idProduct 0x0002 2.0 root hub
  bcdDevice 3.02
  iManufacturer 3
  iProduct 2
  iSerial 1
  bNumConfigurations 1
  Configuration Descriptor:
    bLength 9
    bDescriptorType 2
    wTotalLength 25
    bNumInterfaces 1
    bConfigurationValue 1
    iConfiguration 0
    bmAttributes 0xe0
      Self Powered
      Remote Wakeup
    MaxPower 0mA
    Interface Descriptor:
      bLength 9
      bDescriptorType 4
      bInterfaceNumber 0
      bAlternateSetting 0
      bNumEndpoints 1
      bInterfaceClass 9 Hub
      bInterfaceSubClass 0 Unused
      bInterfaceProtocol 0 Full speed (or root) hub
      iInterface 0
      Endpoint Descriptor:
        bLength 7
        bDescriptorType 5
        bEndpointAddress 0x81 EP 1 IN
        bmAttributes 3
          Transfer Type Interrupt
          Synch Type None
          Usage Type Data
        wMaxPacketSize 0x0004 1x 4 bytes
        bInterval 12

Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Couldn't open device, some information will be missing
Device Descriptor:
  bLength 18
  bDescriptorType 1
  bcdUSB 1.10
  bDeviceClass 9 Hub
  bDeviceSubClass 0 Unused
  bDeviceProtocol 0 Full speed (or root) hub
  bMaxPacketSize0 64
  idVendor 0x1d6b Linux Foundation
  idProduct 0x0001 1.1 root hub
  bcdDevice 3.02
  iManufacturer 3
  iProduct 2
  iSerial 1
  bNumConfigurations 1
  Configuration Descriptor:
    bLength 9
    bDescriptorType 2
    wTotalLength 25
    bNumInterfaces 1
    bConfigurationValue 1
    iConfiguration 0
    bmAttributes 0xe0
      Self Powered
      Remote Wakeup
    MaxPower 0mA
    Interface Descriptor:
      bLength 9
      bDescriptorType 4
      bInterfaceNumber 0
      bAlternateSetting 0
      bNumEndpoints 1
      bInterfaceClass 9 Hub
      bInterfaceSubClass 0 Unused
      bInterfaceProtocol 0 Full speed (or root) hub
      iInterface 0
      Endpoint Descriptor:
        bLength 7
        bDescriptorType 5
        bEndpointAddress 0x81 EP 1 IN
        bmAttributes 3
          Transfer Type Interrupt
          Synch Type None
          Usage Type Data
        wMaxPacketSize 0x0002 1x 2 bytes
        bInterval 255

Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Couldn't open device, some information will be missing
Device Descriptor:
  bLength 18
  bDescriptorType 1
  bcdUSB 1.10
  bDeviceClass 9 Hub
  bDeviceSubClass 0 Unused
  bDeviceProtocol 0 Full speed (or root) hub
  bMaxPacketSize0 64
  idVendor 0x1d6b Linux Foundation
  idProduct 0x0001 1.1 root hub
  bcdDevice 3.02
  iManufacturer 3
  iProduct 2
  iSerial 1
  bNumConfigurations 1
  Configuration Descriptor:
    bLength 9
    bDescriptorType 2
    wTotalLength 25
    bNumInterfaces 1
    bConfigurationValue 1
    iConfiguration 0
    bmAttributes 0xe0
      Self Powered
      Remote Wakeup
    MaxPower 0mA
    Interface Descriptor:
      bLength 9
      bDescriptorType 4
      bInterfaceNumber 0
      bAlternateSetting 0
      bNumEndpoints 1
      bInterfaceClass 9 Hub
      bInterfaceSubClass 0 Unused
      bInterfaceProtocol 0 Full speed (or root) hub
      iInterface 0
      Endpoint Descriptor:
        bLength 7
        bDescriptorType 5
        bEndpointAddress 0x81 EP 1 IN
        bmAttributes 3
          Transfer Type Interrupt
          Synch Type None
          Usage Type Data
        wMaxPacketSize 0x0002 1x 2 bytes
        bInterval 255

Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Couldn't open device, some information will be missing
Device Descriptor:
  bLength 18
  bDescriptorType 1
  bcdUSB 1.10
  bDeviceClass 9 Hub
  bDeviceSubClass 0 Unused
  bDeviceProtocol 0 Full speed (or root) hub
  bMaxPacketSize0 64
  idVendor 0x1d6b Linux Foundation
  idProduct 0x0001 1.1 root hub
  bcdDevice 3.02
  iManufacturer 3
  iProduct 2
  iSerial 1
  bNumConfigurations 1
  Configuration Descriptor:
    bLength 9
    bDescriptorType 2
    wTotalLength 25
    bNumInterfaces 1
    bConfigurationValue 1
    iConfiguration 0
    bmAttributes 0xe0
      Self Powered
      Remote Wakeup
    MaxPower 0mA
    Interface Descriptor:
      bLength 9
      bDescriptorType 4
      bInterfaceNumber 0
      bAlternateSetting 0
      bNumEndpoints 1
      bInterfaceClass 9 Hub
      bInterfaceSubClass 0 Unused
      bInterfaceProtocol 0 Full speed (or root) hub
      iInterface 0
      Endpoint Descriptor:
        bLength 7
        bDescriptorType 5
        bEndpointAddress 0x81 EP 1 IN
        bmAttributes 3
          Transfer Type Interrupt
          Synch Type None
          Usage Type Data
        wMaxPacketSize 0x0002 1x 2 bytes
        bInterval 255

Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Couldn't open device, some information will be missing
Device Descriptor:
  bLength 18
  bDescriptorType 1
  bcdUSB 1.10
  bDeviceClass 9 Hub
  bDeviceSubClass 0 Unused
  bDeviceProtocol 0 Full speed (or root) hub
  bMaxPacketSize0 64
  idVendor 0x1d6b Linux Foundation
  idProduct 0x0001 1.1 root hub
  bcdDevice 3.02
  iManufacturer 3
  iProduct 2
  iSerial 1
  bNumConfigurations 1
  Configuration Descriptor:
    bLength 9
    bDescriptorType 2
    wTotalLength 25
    bNumInterfaces 1
    bConfigurationValue 1
    iConfiguration 0
    bmAttributes 0xe0
      Self Powered
      Remote Wakeup
    MaxPower 0mA
    Interface Descriptor:
      bLength 9
      bDescriptorType 4
      bInterfaceNumber 0
      bAlternateSetting 0
      bNumEndpoints 1
      bInterfaceClass 9 Hub
      bInterfaceSubClass 0 Unused
      bInterfaceProtocol 0 Full speed (or root) hub
      iInterface 0
      Endpoint Descriptor:
        bLength 7
        bDescriptorType 5
        bEndpointAddress 0x81 EP 1 IN
        bmAttributes 3
          Transfer Type Interrupt
          Synch Type None
          Usage Type Data
        wMaxPacketSize 0x0002 1x 2 bytes
        bInterval 255

Bus 001 Device 004: ID 079b:004a Sagem XG-760A 802.11bg
Couldn't open device, some information will be missing
Device Descriptor:
  bLength 18
  bDescriptorType 1
  bcdUSB 2.00
  bDeviceClass 255 Vendor Specific Class
  bDeviceSubClass 255 Vendor Specific Subclass
  bDeviceProtocol 255 Vendor Specific Protocol
  bMaxPacketSize0 64
  idVendor 0x079b Sagem
  idProduct 0x004a XG-760A 802.11bg
  bcdDevice 43.30
  iManufacturer 16
  iProduct 32
  iSerial 0
  bNumConfigurations 1
  Configuration Descriptor:
    bLength 9
    bDescriptorType 2
    wTotalLength 46
    bNumInterfaces 1
    bConfigurationValue 1
    iConfiguration 0
    bmAttributes 0x80
      (Bus Powered)
    MaxPower 500mA
    Interface Descriptor:
      bLength 9
      bDescriptorType 4
      bInterfaceNumber 0
      bAlternateSetting 0
      bNumEndpoints 4
      bInterfaceClass 255 Vendor Specific Class
      bInterfaceSubClass 0
      bInterfaceProtocol 0
      iInterface 0
      Endpoint Descriptor:
        bLength 7
        bDescriptorType 5
        bEndpointAddress 0x01 EP 1 OUT
        bmAttributes 2
          Transfer Type Bulk
          Synch Type None
          Usage Type Data
        wMaxPacketSize 0x0200 1x 512 bytes
        bInterval 0
      Endpoint Descriptor:
        bLength 7
        bDescriptorType 5
        bEndpointAddress 0x82 EP 2 IN
        bmAttributes 2
          Transfer Type Bulk
          Synch Type None
          Usage Type Data
        wMaxPacketSize 0x0200 1x 512 bytes
        bInterval 0
      Endpoint Descriptor:
        bLength 7
        bDescriptorType 5
        bEndpointAddress 0x83 EP 3 IN
        bmAttributes 3
          Transfer Type Interrupt
          Synch Type None
          Usage Type Data
        wMaxPacketSize 0x0040 1x 64 bytes
        bInterval 1
      Endpoint Descriptor:
        bLength 7
        bDescriptorType 5
        bEndpointAddress 0x04 EP 4 OUT
        bmAttributes 3
          Transfer Type Interrupt
          Synch Type None
          Usage Type Data
        wMaxPacketSize 0x0040 1x 64 bytes
        bInterval 1

Bus 002 Device 002: ID 046d:c315 Logitech, Inc. Classic New Touch Keyboard
Couldn't open device, some information will be missing
Device Descriptor:
  bLength 18
  bDescriptorType 1
  bcdUSB 1.10
  bDeviceClass 0 (Defined at Interface level)
  bDeviceSubClass 0
  bDeviceProtocol 0
  bMaxPacketSize0 8
  idVendor 0x046d Logitech, Inc.
  idProduct 0xc315 Classic New Touch Keyboard
  bcdDevice 28.00
  iManufacturer 1
  iProduct 2
  iSerial 0
  bNumConfigurations 1
  Configuration Descriptor:
    bLength 9
    bDescriptorType 2
    wTotalLength 34
    bNumInterfaces 1
    bConfigurationValue 1
    iConfiguration 0
    bmAttributes 0xa0
      (Bus Powered)
      Remote Wakeup
    MaxPower 100mA
    Interface Descriptor:
      bLength 9
      bDescriptorType 4
      bInterfaceNumber 0
      bAlternateSetting 0
      bNumEndpoints 1
      bInterfaceClass 3 Human Interface Device
      bInterfaceSubClass 1 Boot Interface Subclass
      bInterfaceProtocol 1 Keyboard
      iInterface 0
        HID Device Descriptor:
          bLength 9
          bDescriptorType 33
          bcdHID 1.10
          bCountryCode 0 Not supported
          bNumDescriptors 1
          bDescriptorType 34 Report
          wDescriptorLength 64
         Report Descriptors:
           ** UNAVAILABLE **
      Endpoint Descriptor:
        bLength 7
        bDescriptorType 5
        bEndpointAddress 0x81 EP 1 IN
        bmAttributes 3
          Transfer Type Interrupt
          Synch Type None
          Usage Type Data
        wMaxPacketSize 0x0008 1x 8 bytes
        bInterval 10

Bus 003 Device 003: ID 15d9:0a4d Trust International B.V.
Couldn't open device, some information will be missing
Device Descriptor:
  bLength 18
  bDescriptorType 1
  bcdUSB 1.10
  bDeviceClass 0 (Defined at Interface level)
  bDeviceSubClass 0
  bDeviceProtocol 0
  bMaxPacketSize0 8
  idVendor 0x15d9 Trust International B.V.
  idProduct 0x0a4d
  bcdDevice 1.00
  iManufacturer 0
  iProduct 1
  iSerial 0
  bNumConfigurations 1
  Configuration Descriptor:
    bLength 9
    bDescriptorType 2
    wTotalLength 34
    bNumInterfaces 1
    bConfigurationValue 1
    iConfiguration 0
    bmAttributes 0xa0
      (Bus Powered)
      Remote Wakeup
    MaxPower 100mA
    Interface Descriptor:
      bLength 9
      bDescriptorType 4
      bInterfaceNumber 0
      bAlternateSetting 0
      bNumEndpoints 1
      bInterfaceClass 3 Human Interface Device
      bInterfaceSubClass 1 Boot Interface Subclass
      bInterfaceProtocol 2 Mouse
      iInterface 0
        HID Device Descriptor:
          bLength 9
          bDescriptorType 33
          bcdHID 1.11
          bCountryCode 0 Not supported
          bNumDescriptors 1
          bDescriptorType 34 Report
          wDescriptorLength 66
         Report Descriptors:
           ** UNAVAILABLE **
      Endpoint Descriptor:
        bLength 7
        bDescriptorType 5
        bEndpointAddress 0x81 EP 1 IN
        bmAttributes 3
          Transfer Type Interrupt
          Synch Type None
          Usage Type Data
        wMaxPacketSize 0x0006 1x 6 bytes
        bInterval 10

Bus 002 Device 005: ID 0ac8:307b Z-Star Microelectronics Corp. USB 1.1 Webcam
Couldn't open device, some information will be missing
Device Descriptor:
  bLength 18
  bDescriptorType 1
  bcdUSB 1.10
  bDeviceClass 255 Vendor Specific Class
  bDeviceSubClass 0
  bDeviceProtocol 0
  bMaxPacketSize0 8
  idVendor 0x0ac8 Z-Star Microelectronics Corp.
  idProduct 0x307b USB 1.1 Webcam
  bcdDevice 1.00
  iManufacturer 1
  iProduct 2
  iSerial 0
  bNumConfigurations 1
  Configuration Descriptor:
    bLength 9
    bDescriptorType 2
    wTotalLength 193
    bNumInterfaces 1
    bConfigurationValue 1
    iConfiguration 0
    bmAttributes 0x80
      (Bus Powered)
    MaxPower 160mA
    Interface Descriptor:
      bLength 9
      bDescriptorType 4
      bInterfaceNumber 0
      bAlternateSetting 0
      bNumEndpoints 2
      bInterfaceClass 255 Vendor Specific Class
      bInterfaceSubClass 255 Vendor Specific Subclass
      bInterfaceProtocol 255 Vendor Specific Protocol
      iInterface 0
      Endpoint Descriptor:
        bLength 7
        bDescriptorType 5
        bEndpointAddress 0x81 EP 1 IN
        bmAttributes 1
          Transfer Type Isochronous
          Synch Type None
          Usage Type Data
        wMaxPacketSize 0x0000 1x 0 bytes
        bInterval 1
      Endpoint Descriptor:
        bLength 7
        bDescriptorType 5
        bEndpointAddress 0x82 EP 2 IN
        bmAttributes 3
          Transfer Type Interrupt
          Synch Type None
          Usage Type Data
        wMaxPacketSize 0x0008 1x 8 bytes
        bInterval 10
    Interface Descriptor:
      bLength 9
      bDescriptorType 4
      bInterfaceNumber 0
      bAlternateSetting 1
      bNumEndpoints 2
      bInterfaceClass 255 Vendor Specific Class
      bInterfaceSubClass 255 Vendor Specific Subclass
      bInterfaceProtocol 255 Vendor Specific Protocol
      iInterface 0
      Endpoint Descriptor:
        bLength 7
        bDescriptorType 5
        bEndpointAddress 0x81 EP 1 IN
        bmAttributes 1
          Transfer Type Isochronous
          Synch Type None
          Usage Type Data
        wMaxPacketSize 0x0080 1x 128 bytes
        bInterval 1
      Endpoint Descriptor:
        bLength 7
        bDescriptorType 5
        bEndpointAddress 0x82 EP 2 IN
        bmAttributes 3
          Transfer Type Interrupt
          Synch Type None
          Usage Type Data
        wMaxPacketSize 0x0008 1x 8 bytes
        bInterval 10
    Interface Descriptor:
      bLength 9
      bDescriptorType 4
      bInterfaceNumber 0
      bAlternateSetting 2
      bNumEndpoints 2
      bInterfaceClass 255 Vendor Specific Class
      bInterfaceSubClass 255 Vendor Specific Subclass
      bInterfaceProtocol 255 Vendor Specific Protocol
      iInterface 0
      Endpoint Descriptor:
        bLength 7
        bDescriptorType 5
        bEndpointAddress 0x81 EP 1 IN
        bmAttributes 1
          Transfer Type Isochronous
          Synch Type None
          Usage Type Data
        wMaxPacketSize 0x00c0 1x 192 bytes
        bInterval 1
      Endpoint Descriptor:
        bLength 7
        bDescriptorType 5
        bEndpointAddress 0x82 EP 2 IN
        bmAttributes 3
          Transfer Type Interrupt
          Synch Type None
          Usage Type Data
        wMaxPacketSize 0x0008 1x 8 bytes
        bInterval 10
    Interface Descriptor:
      bLength 9
      bDescriptorType 4
      bInterfaceNumber 0
      bAlternateSetting 3
      bNumEndpoints 2
      bInterfaceClass 255 Vendor Specific Class
      bInterfaceSubClass 255 Vendor Specific Subclass
      bInterfaceProtocol 255 Vendor Specific Protocol
      iInterface 0
      Endpoint Descriptor:
        bLength 7
        bDescriptorType 5
        bEndpointAddress 0x81 EP 1 IN
        bmAttributes 1
          Transfer Type Isochronous
          Synch Type None
          Usage Type Data
        wMaxPacketSize 0x0100 1x 256 bytes
        bInterval 1
      Endpoint Descriptor:
        bLength 7
        bDescriptorType 5
        bEndpointAddress 0x82 EP 2 IN
        bmAttributes 3
          Transfer Type Interrupt
          Synch Type None
          Usage Type Data
        wMaxPacketSize 0x0008 1x 8 bytes
        bInterval 10
    Interface Descriptor:
      bLength 9
      bDescriptorType 4
      bInterfaceNumber 0
      bAlternateSetting 4
      bNumEndpoints 2
      bInterfaceClass 255 Vendor Specific Class
      bInterfaceSubClass 255 Vendor Specific Subclass
      bInterfaceProtocol 255 Vendor Specific Protocol
      iInterface 0
      Endpoint Descriptor:
        bLength 7
        bDescriptorType 5
        bEndpointAddress 0x81 EP 1 IN
        bmAttributes 1
          Transfer Type Isochronous
          Synch Type None
          Usage Type Data
        wMaxPacketSize 0x0180 1x 384 bytes
        bInterval 1
      Endpoint Descriptor:
        bLength 7
        bDescriptorType 5
        bEndpointAddress 0x82 EP 2 IN
        bmAttributes 3
          Transfer Type Interrupt
          Synch Type None
          Usage Type Data
        wMaxPacketSize 0x0008 1x 8 bytes
        bInterval 10
    Interface Descriptor:
      bLength 9
      bDescriptorType 4
      bInterfaceNumber 0
      bAlternateSetting 5
      bNumEndpoints 2
      bInterfaceClass 255 Vendor Specific Class
      bInterfaceSubClass 255 Vendor Specific Subclass
      bInterfaceProtocol 255 Vendor Specific Protocol
      iInterface 0
      Endpoint Descriptor:
        bLength 7
        bDescriptorType 5
        bEndpointAddress 0x81 EP 1 IN
        bmAttributes 1
          Transfer Type Isochronous
          Synch Type None
          Usage Type Data
        wMaxPacketSize 0x0200 1x 512 bytes
        bInterval 1
      Endpoint Descriptor:
        bLength 7
        bDescriptorType 5
        bEndpointAddress 0x82 EP 2 IN
        bmAttributes 3
          Transfer Type Interrupt
          Synch Type None
          Usage Type Data
        wMaxPacketSize 0x0008 1x 8 bytes
        bInterval 10
    Interface Descriptor:
      bLength 9
      bDescriptorType 4
      bInterfaceNumber 0
      bAlternateSetting 6
      bNumEndpoints 2
      bInterfaceClass 255 Vendor Specific Class
      bInterfaceSubClass 255 Vendor Specific Subclass
      bInterfaceProtocol 255 Vendor Specific Protocol
      iInterface 0
      Endpoint Descriptor:
        bLength 7
        bDescriptorType 5
        bEndpointAddress 0x81 EP 1 IN
        bmAttributes 1
          Transfer Type Isochronous
          Synch Type None
          Usage Type Data
        wMaxPacketSize 0x0300 1x 768 bytes
        bInterval 1
      Endpoint Descriptor:
        bLength 7
        bDescriptorType 5
        bEndpointAddress 0x82 EP 2 IN
        bmAttributes 3
          Transfer Type Interrupt
          Synch Type None
          Usage Type Data
        wMaxPacketSize 0x0008 1x 8 bytes
        bInterval 10
    Interface Descriptor:
      bLength 9
      bDescriptorType 4
      bInterfaceNumber 0
      bAlternateSetting 7
      bNumEndpoints 2
      bInterfaceClass 255 Vendor Specific Class
      bInterfaceSubClass 255 Vendor Specific Subclass
      bInterfaceProtocol 255 Vendor Specific Protocol
      iInterface 0
      Endpoint Descriptor:
        bLength 7
        bDescriptorType 5
        bEndpointAddress 0x81 EP 1 IN
        bmAttributes 1
          Transfer Type Isochronous
          Synch Type None
          Usage Type Data
        wMaxPacketSize 0x0380 1x 896 bytes
        bInterval 1
      Endpoint Descriptor:
        bLength 7
        bDescriptorType 5
        bEndpointAddress 0x82 EP 2 IN
        bmAttributes 3
          Transfer Type Interrupt
          Synch Type None
          Usage Type Data
        wMaxPacketSize 0x0008 1x 8 bytes
        bInterval 10
```

---

