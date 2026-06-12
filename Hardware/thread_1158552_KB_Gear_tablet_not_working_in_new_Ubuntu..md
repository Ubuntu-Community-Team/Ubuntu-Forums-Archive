---
title: "KB Gear tablet not working in new Ubuntu."
date: 2009-05-13
forum: Hardware
---

### Post by Phazonx on 2009-05-13
Hi.  I have this old usb Tablet back from 1999.  I had ubuntu 8.04 and it worked wonderfully.  No problems at all.

But The new ubuntu, (and 8.10) don't seem to work with it after plugging it in.  

Image: [http://www.telecommander.com/pics/links/graphictablets/disneytabletrt/MSC-DS-SB20-unit.jpg](http://www.telecommander.com/pics/links/graphictablets/disneytabletrt/MSC-DS-SB20-unit.jpg)


lsusb:

Bus 003 Device 002: ID 084e:1001 KB Gear 
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0         8
  idVendor           0x084e KB Gear
  idProduct          0x1001 
  bcdDevice            0.01
  iManufacturer           0 
  iProduct                1 
  iSerial                 0 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           34
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
      bInterfaceClass         3 Human Interface Device
      bInterfaceSubClass      1 Boot Interface Subclass
      bInterfaceProtocol      2 Mouse
      iInterface              0 
        HID Device Descriptor:
          bLength                 9
          bDescriptorType        33
          bcdHID               1.00
          bCountryCode            0 Not supported
          bNumDescriptors         1
          bDescriptorType        34 Report
          wDescriptorLength      78
         Report Descriptors: 
           ** UNAVAILABLE **
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0008  1x 8 bytes
        bInterval              10
cannot read device status, Operation not permitted (1)


The ubuntu that worked just won't install on this comp, and the one I had it working on is way to slow to make use of it in Gimp.  

I'll get lsusb from that older comp and post it here.  

help?

---

