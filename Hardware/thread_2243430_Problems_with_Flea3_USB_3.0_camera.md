---
title: "Problems with Flea3 USB 3.0 camera"
date: 2014-09-08
forum: Hardware
---

### Post by maksim4 on 2014-09-08
Hello. I have a Flea3 USB 3.0 camera connected to Intel NUC DE3815TYKHE board. The camera provides 120fps and resolution 1.3Mpx. I've installed Ubuntu 14.04.1 LTS.

Usually camera works well and software is able to process all the 120 frames each second. But time to time the camera runs in low speed mode only (~35 fps). It happens randomly. If I run my software now it works in 120fps mode (flycap says that the camera is connected to USB 3.0), but in 5 minutes it may say that the only 35fps mode is available (this case flycap says that camera is connected to USB 2.0). But actually I didn't reconnect anything. 

I don't face with such problem when I connect the camera to PC Windows 7.

I tried to look at lsusb. It's completely unclear why it is connected to different busses.

[TABLE="width: 500"]
[TR]
[TD]bad lsusb[/TD]
[TD]good lsusb[/TD]
[/TR]
[TR]
[TD][SIZE=1]Bus 001 Device 003: ID 1e10:3006 Point Grey Research, Inc. Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.10
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  idVendor           0x1e10 Point Grey Research, Inc.
  idProduct          0x3006 
  bcdDevice            0.00
  iManufacturer           1 Point Grey Research
  iProduct                2 Flea3 FL3-U3-13S2C
  iSerial                 3 00BE234D
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           25
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
      bNumEndpoints           1
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass      0 
      bInterfaceProtocol      0 
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
        bInterval               0 [/SIZE][/TD]
[TD][SIZE=1]Bus 002 Device 002: ID 1e10:3006 Point Grey Research, Inc. Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               3.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0         9
  idVendor           0x1e10 Point Grey Research, Inc.
  idProduct          0x3006 
  bcdDevice            0.00
  iManufacturer           1 Point Grey Research
  iProduct                2 Flea3 FL3-U3-13S2C
  iSerial                 3 00BE234D
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           44
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0x80
      (Bus Powered)
    MaxPower              224mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           2
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass      0 
      bInterfaceProtocol      0 
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0400  1x 1024 bytes
        bInterval               0
        bMaxBurst              15
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x82  EP 2 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               1
        bMaxBurst               0 [/SIZE][/TD]
[/TR]
[/TABLE]

---

