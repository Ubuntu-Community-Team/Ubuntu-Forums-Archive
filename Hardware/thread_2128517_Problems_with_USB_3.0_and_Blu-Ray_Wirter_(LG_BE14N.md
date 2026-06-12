---
title: "Problems with USB 3.0 and Blu-Ray Wirter (LG BE14NU40)"
date: 2013-03-23
forum: Hardware
---

### Post by InformateIt on 2013-03-23
I have bought an LG BE14NU40 (External USB 3 Blu-Ray Disk Writer at 14x),
 it work fine under windows,
 but if I try to use it under linux it **writes** any kind of disk **very very slowly**.
For Blu Ray disks with usb 3 it should go at 14x but if I use it under linux/ubuntu
on the same machine in witch it works under windows, the transfer speed for any kind of CD/DVD/BD write
seems to be limited to something around 1200-1500KiB/sec that mean for BD-R 0,3x!
 (I think this is a speed near to a USB 1.1 conection)!

Why it works so bad under ubuntu? It works also faster on Windows with **USB 2** !!

It's a problem with the USB 3 driver?

I think it is not recognized in the coorect way beacuse lsusb says that is :


              Bus 004 Device 003: ID 067b:2771 Prolific Technology, Inc. 




Bus 004 Device 003: ID 067b:2771 Prolific Technology, Inc. 
Couldn't open device, some information will be missing
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               3.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0         9
  idVendor           0x067b Prolific Technology, Inc.
  idProduct          0x2771 
  bcdDevice            1.00
  iManufacturer           1 
  iProduct                2 
  iSerial                 3 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           44
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0xc0
      Self Powered
    MaxPower               24mA
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
        bEndpointAddress     0x84  EP 4 IN
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
        bEndpointAddress     0x01  EP 1 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0400  1x 1024 bytes
        bInterval               0
        bMaxBurst              15



Thanks to anyone!

---

