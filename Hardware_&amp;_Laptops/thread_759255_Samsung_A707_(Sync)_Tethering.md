---
title: "Samsung A707 (Sync) Tethering"
date: 2008-04-18
forum: Hardware &amp; Laptops
---

### Post by justotech on 2008-04-18
I just added tethering to my cell plan so that I can use my phone for a modem.  It's no big deal with XP, just install the drivers and then create a dial-up connection.  

The phone connects by USB.

------------

The problem I'm getting is that I don't have a clue how to make it work with Gutsy, or even if I can make it work right.  Anyone ever tried this or have an idea how to go about it?

---

### Post by justotech on 2008-04-19
I guess I should do a little more research on this.  I'm not even sure if it's detected by the OS as a modem or if the OS even knows what to call my phone.  It may actually see it is a flash drive or something like that because of it's card reader.  I'll check and see.

---

### Post by justotech on 2008-04-19
So here's what I get from running lsusb -v.  The OS knows that it's a phone but no matter what port I tell network manager to use for a modem it just sits there.  Anyone have an idea what to do next?

--------------------------------

Bus 002 Device 002: ID 04e8:6601 Samsung Electronics Co., Ltd Z100 Mobile Phone
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.10
  bDeviceClass            2 Communications
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  idVendor           0x04e8 Samsung Electronics Co., Ltd
  idProduct          0x6601 Z100 Mobile Phone
  bcdDevice            0.00
  iManufacturer           1 SAMSUNG Electronics Co.,Ltd.
  iProduct                2 SAMSUNG CDMA Technologies
  iSerial                 0 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           67
    bNumInterfaces          2
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
      bNumEndpoints           1
      bInterfaceClass         2 Communications
      bInterfaceSubClass      2 Abstract (modem)
      bInterfaceProtocol      1 AT-commands (v.25ter)
      iInterface              0 
      CDC Header:
        bcdCDC               1.09
      CDC Call Management:
        bmCapabilities       0x03
          call management
          use DataInterface
        bDataInterface          1
      CDC ACM:
        bmCapabilities       0x0f
          connection notifications
          sends break
          line coding and serial state
          get/set/clear comm features
      CDC Union:
        bMasterInterface        0
        bSlaveInterface         1 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0010  1x 16 bytes
        bInterval              32
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        1
      bAlternateSetting       0
      bNumEndpoints           2
      bInterfaceClass        10 CDC Data
      bInterfaceSubClass      0 Unused
      bInterfaceProtocol      0 
      iInterface              4 Data Interface
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
        bEndpointAddress     0x02  EP 2 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               0
Device Status:     0x0000
  (Bus Powered)

---

### Post by richardrblc on 2008-05-02
did you ever figure it out:popcorn:

---

