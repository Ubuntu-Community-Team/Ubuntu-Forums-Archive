---
title: "logitech g15 usb hub"
date: 2007-12-28
forum: Hardware &amp; Laptops
---

### Post by ppera on 2007-12-28
I have a Logitech G15 and have g15daemon & friends installed, however, the USB hub functionality is problematic (nothing I ever plug in appears, I tried different flash drives, bluetooth dongles, digital cameras, etc). I understand this is an USB 1.1 hub with only 100mA to give, but still... Anyone with similar problems ? The hub does show up nicely on lsusb:

Bus 002 Device 001: ID 0000:0000
Bus 001 Device 005: ID 0a12:0001 Cambridge Silicon Radio, Ltd Bluetooth Dongle (HCI mode)
Bus 001 Device 004: ID 046d:c222 Logitech, Inc.
Bus 001 Device 003: ID 046d:c221 Logitech, Inc.
Bus 001 Device 002: ID 046d:c223 Logitech, Inc.
Bus 001 Device 001: ID 0000:0000


Bus 001 Device 002: ID 046d:c223 Logitech, Inc.
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.10
  bDeviceClass            9 Hub
  bDeviceSubClass         0 Unused
  bDeviceProtocol         0 Full speed hub
  bMaxPacketSize0         8
  idVendor           0x046d Logitech, Inc.
  idProduct          0xc223
  bcdDevice            1.03
  iManufacturer           1
  iProduct                2
  iSerial                 0
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
    MaxPower              100mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         9 Hub
      bInterfaceSubClass      0 Unused
      bInterfaceProtocol      0 Full speed hub
      iInterface              0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0001  1x 1 bytes
        bInterval             255

---

