---
title: "USB MP3 Recorder"
date: 2006-12-02
forum: Hardware &amp; Laptops
---

### Post by cabbage on 2006-12-02
Dear all,

I would like to get my mp3 player/recorder to work in Ubuntu. The device is a Perception Digital Fuxion Genie which connects via USB.

It comes with its own driver for Windows, and when attached it appears within device manager as a scsi disk, and within explorer as new drive formatted as fat12.

When I attach it to ubuntu (edgy) I get the following in messages/syslog:

[INDENT]kernel: [17181405.324000] usb 1-1: new full speed USB device using uhci_hcd and address 2
kernel: [17181405.484000] usb 1-1: configuration #1 chosen from 1 choice
[/INDENT]

But no new device files are created, so there is nothing for more me to mount. An "lsusb -v" gives:

[INDENT]Bus 001 Device 002: ID 0aa6:3410 Perception Digital, Ltd
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.10
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0
  bDeviceProtocol         0
  bMaxPacketSize0        64
  idVendor           0x0aa6 Perception Digital, Ltd
  idProduct          0x3410
  bcdDevice            0.83
  iManufacturer           1
  iProduct                2
  iSerial                 0
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           32
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0
    bmAttributes         0xc0
      Self Powered
    MaxPower              100mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           2
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass      1
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
cannot read device status, Operation not permitted (1)
[/INDENT]

I would love to get this device to work as its the only thing stopping me from wiping my Windows installation!


Thanks for your help,

Cabbage.

---

