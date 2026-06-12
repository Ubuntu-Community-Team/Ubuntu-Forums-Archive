---
title: "Problems with USB-modem on Prolific PL2303"
date: 2008-05-25
forum: Hardware
---

### Post by romx on 2008-05-25
I have a GPRS/EDGE modem on USB. 
From interface's side it’s a simple and good known Prolific PL2303 (I saw an IC inside), which, as I know, bundled in current kernel.
Unfortunately it’s tweaked by firmware (as I think).
USB data is: VID_067B&PID_0611 (modem name is DT-611U, so PID is just from modem’s name).
It working fine in Windows, but I like to use it in Linux too.

Changing in VID/PID make it unknown for my Linux (eeeXubuntu 7.10, tweaked Gutsy Gibbon for ASUS eeePC), and, unfortunately, I can’t got a ttyUSB.
It’s discovered by system like “unknown full-speed USB device”

How can I make my modem usable in my Linux system? 
Can I add support for this PID without recompiling of pl2303 driver?

---additional diagnostics info:
```
/var/log/messages
... kernel: [  136.836000] usb 2-1: new full speed USB device using uhci_hcd and address 5
```
```
romx@romx-asus:~$ lsusb
...
Bus 002 Device 005: ID 067b:0611 Prolific Technology, Inc. 
...
```
```
lsusb -v -s002:005

Bus 002 Device 005: ID 067b:0611 Prolific Technology, Inc. 
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.10
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0         8
  idVendor           0x067b Prolific Technology, Inc.
  idProduct          0x0611 
  bcdDevice            0.00
  iManufacturer           0 
  iProduct                0 
  iSerial                 0 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           39
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
      bNumEndpoints           3
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass      0 
      bInterfaceProtocol      0 
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x000a  1x 10 bytes
        bInterval               1
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
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x83  EP 3 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               0
cannot read device status, Operation not permitted (1)
```

---

