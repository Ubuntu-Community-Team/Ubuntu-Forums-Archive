---
title: "Terratec Cinergy DT XS - Digital Tuner questions..."
date: 2007-11-29
forum: Hardware &amp; Laptops
---

### Post by zopac on 2007-11-29
Ok, I bought that tuner and plugged it on my Ubuntu 7.10 and Ubuntu notices the tuner (see the end of message) but doesn't know drivers(?).
Is it possible to get this tuner work in ubuntu or can I somehow add it on vmware windows xp?

Dmesg:
```
[ 1261.724000] usb 5-8: new high speed USB device using ehci_hcd and address 9
[ 1261.856000] usb 5-8: configuration #1 chosen from 1 choice

```
lsusb:
```
Bus 005 Device 009: ID 0ccd:005a TerraTec Electronic Gmbh
```

lsusb -v:
```
Bus 005 Device 009: ID 0ccd:005a TerraTec Electronic GmbH 
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  idVendor           0x0ccd TerraTec Electronic GmbH
  idProduct          0x005a 
  bcdDevice            0.01
  iManufacturer           1 
  iProduct                2 
  iSerial                 3 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           46
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0xa0
      (Bus Powered)
      Remote Wakeup
    MaxPower              500mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           4
      bInterfaceClass       255 Vendor Specific Class
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
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               1
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               1
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x82  EP 2 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               1
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x83  EP 3 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               1

```

---

### Post by Chal on 2007-12-20
mybe you should look here:
[https://wiki.ubuntu.com/em28xx]("https://wiki.ubuntu.com/em28xx")

got my cinergy work with these drivers

---

