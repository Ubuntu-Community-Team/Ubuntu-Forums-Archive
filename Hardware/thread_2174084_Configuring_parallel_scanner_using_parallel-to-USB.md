---
title: "Configuring parallel scanner using parallel-to-USB cable"
date: 2013-09-12
forum: Hardware
---

### Post by twb999 on 2013-09-12
I have a Plustek OpticPro 9636T parallel-port scanner.  I have made this scanner work in the past through a parallel port on an older PC.  My new PC has no parallel port, so I have connected it to the PC using a parallel-to-USB converter cable.  lsusb shows the parallel port converter, but no indication of what is behind it.  

Simple Scan does not detect any scanner.  I looked in the How-To docs and they explain how to make USB or parallel scanners work, but I could not find an example for my situation where the scanner is parallel and the connection is USB.  Please help.

Additional info added 16 Sept

lsusb -v -d 0x067b:0x2305   (the parallel port adapter found with lsusb)

Yields:
Bus 001 Device 005: ID 067b:2305 Prolific Technology, Inc. PL2305 Parallel Port
Couldn't open device, some information will be missing
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0         8
  idVendor           0x067b Prolific Technology, Inc.
  idProduct          0x2305 PL2305 Parallel Port
  bcdDevice            2.02
  iManufacturer           1 
  iProduct                2 
  iSerial                 0 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           78
    bNumInterfaces          1
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
      bNumEndpoints           1
      bInterfaceClass         7 Printer
      bInterfaceSubClass      1 Printer
      bInterfaceProtocol      1 Unidirectional
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
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       1
      bNumEndpoints           2
      bInterfaceClass         7 Printer
      bInterfaceSubClass      1 Printer
      bInterfaceProtocol      2 Bidirectional
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
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       2
      bNumEndpoints           3
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass      0 
      bInterfaceProtocol    255 
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
        bEndpointAddress     0x83  EP 3 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0004  1x 4 bytes
        bInterval               1


And dmesg output when the cable is plugged in is:

[ 1293.033284] usb 1-1.3: Product: IEEE-1284 Controller
[ 1293.033287] usb 1-1.3: Manufacturer: Prolific Technology Inc.
[ 1293.047998] usblp 1-1.3:1.0: usblp0: USB Bidirectional printer dev 5 if 0 alt 1 proto 2 vid 0x067B pid 0x2305


So, it looks like the system is automatically assuming that this is for a printer and configuring usblp0 for the port.

How can I change this and get this configured as a scanner?

---

