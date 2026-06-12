---
title: "Breezy upgrades break UDEV rules?"
date: 2006-04-03
forum: Hardware &amp; Laptops
---

### Post by Gowator on 2006-04-03
This is the second time I have broken UDEV ](*,) 

I did a update on Adept and I guess the UDEV rules got messed up and the first time I managed to fix them somehow... problem was I tried 20 different things and can't remember what I did exactly.. I was at the point of reinstalling and desperate!  

The thing is my USB key works fine and creates the device and USB mass storage plugged in works but my built in card reader doesn't.  
As regular user
```
Bus 003 Device 003: ID 07cc:0301 Carry Computer Eng., Co., Ltd 6-in-1 Card Reader

Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0
  bDeviceProtocol         0
  bMaxPacketSize0        64
  idVendor           0x07cc Carry Computer Eng., Co., Ltd
  idProduct          0x0301 6-in-1 Card Reader
  bcdDevice            0.05
  iManufacturer           1
  iProduct                2
  iSerial                 3
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           32
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0
    bmAttributes         0x80
    MaxPower              500mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           2
      bInterfaceClass         8 Mass Storage
      bInterfaceSubClass      6 SCSI
      bInterfaceProtocol     80 Bulk (Zip)
      iInterface              4
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x02  EP 2 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0
can't get device qualifier: Operation not permitted
can't get debug descriptor: Operation not permitted


```

as root I get an additional 
```

Device Qualifier (for other device speed):
  bLength                10
  bDescriptorType         6
  bcdUSB               2.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0
  bDeviceProtocol         0
  bMaxPacketSize0        64
  bNumConfigurations      1

```
In place of can't read.....

Im a bit worried about starting messing about with the rules though I managed last time because I need the PC and daren't break it right now :-k 

I can post any files if someone knows what I should do/edit!

---

### Post by Gowator on 2006-04-05
Never mind, fixed it by installing Debian unstable

---

