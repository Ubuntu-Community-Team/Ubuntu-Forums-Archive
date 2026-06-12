---
title: "EasyCAP Not Recongnized"
date: 2012-03-31
forum: Hardware
---

### Post by LukeMasters on 2012-03-31
Hi everybody!

I purchased an EasyCAP from eBay, the listing didn't mention the model I figured it was it was a DC60 and it turns out to be a DC60++.

Anyway, I does not work with Ubuntu 11.10 (64-bit).

When I plug it won't list in lsusb this is all I get :
```

Bus 001 Device 016: ID 1b71:3002

```

I'm wondering if its a fake, the correct USB ID should be 05e1:0408

lsusb -v returns the following

```

Bus 001 Device 022: ID 1b71:3002  
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  idVendor           0x1b71 
  idProduct          0x3002 
  bcdDevice            1.00
  iManufacturer           3 fushicai
  iProduct                4 usbtv007
  iSerial                 2 300000000002
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           83
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
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass      0 
      bInterfaceProtocol    255 
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
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0
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
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x84  EP 4 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               4
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       1
      bNumEndpoints           4
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass      0 
      bInterfaceProtocol    255 
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            1
          Transfer Type            Isochronous
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x1400  3x 1024 bytes
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
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x83  EP 3 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0100  1x 256 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x84  EP 4 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               4
Device Qualifier (for other device speed):
  bLength                10
  bDescriptorType         6
  bcdUSB               2.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  bNumConfigurations      1
Device Status:     0x0000
  (Bus Powered)

```

dmesg give me the following:
```

[ 1128.776101] usb 1-1: new high speed USB device number 5 using ehci_hcd
[ 1128.912098] usb 1-1: config 1 interface 0 altsetting 1 bulk endpoint 0x83 has invalid maxpacket 256

```

Of course, I don't see video0 or easycap in /dev. 

The hardware is ok because it works on Windows.

I opened the device and the following inscriptions are on the main chip
```

UTV007
A614231.1
1136L1BK

```

The inscriptions on the board are : FSC VIDEO DVR

What is usbtv007? Are there any drivers for Ubuntu that work with usbtv007??

Any help is appreciated.

---

### Post by LukeMasters on 2012-04-01
I was wondering if it could be possible to hijack to usb-id in order to make it look like it's 05e1:0408 ?

This way it might be possible to use the easycap driver with it.

I could also try and change it in the kernel driver source file, but I can't find it. Could someone tell where is the source file located?

---

### Post by GuillaumeJ on 2012-06-02
> **LukeMasters said:**
> Hi everybody!

I purchased an EasyCAP from eBay, the listing didn't mention the model I figured it was it was a DC60 and it turns out to be a DC60++.
Anyway, I does not work with Ubuntu 11.10 (64-bit).

... Same chip / prob here, but on Kubuntu 12.04 (64 bits)

Did you get any clue ?

EDIT : found a webpage about this exact version :
[http://plaza.rakuten.co.jp/jashi/diary/201201210000/](http://plaza.rakuten.co.jp/jashi/diary/201201210000/)
...Unfortunately, I can't read it :( Seems Windows related...

---

