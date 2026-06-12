---
title: "Forcing a usb device to use HID driver"
date: 2008-07-12
forum: Hardware
---

### Post by randomhuman on 2008-07-12
Howdy,

I'm having some trouble getting a windows media centre remote to work. I think it could potentially work with the lirc_mceusb2 driver, but needs it's product code added to the module and a recompile. But, in windows it shows up as an HID device, so I'm wondering if there's a way to force it to do the same in linux? It reports a 'vendor specific' interface and isn't claimed by any driver when plugged in.

lsusb -v (some of it):

```
Bus 002 Device 009: ID 147a:e017 Formosa Industrial Computing, Inc. 
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0         8
  idVendor           0x147a Formosa Industrial Computing, Inc.
  idProduct          0xe017
.
.
.
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass    255 Vendor Specific Subclass
      bInterfaceProtocol    255 Vendor Specific Protocol
.
.
.
can't get device qualifier: Connection timed out
can't get debug descriptor: Connection timed out
cannot read device status, Connection timed out (110)
```

I'm not sure what those three errors are about either...

dmesg, after plugging in the receiver:

```
[ 5607.064000] usb 2-1: new low speed USB device using uhci_hcd and address 9
[ 5607.268000] usb 2-1: configuration #1 chosen from 1 choice
```

...and nothing else.

Thanks for any help you can give!

---

### Post by ProbablyX on 2008-07-12
Have you read this guide: [https://help.ubuntu.com/community/InstallLirc/Hardy](https://help.ubuntu.com/community/InstallLirc/Hardy) ? You probably have, but still :)

---

### Post by randomhuman on 2008-07-13
I had not read that guide, but I'd gotten most of the same info elsewhere.

It turns out the changes to support my remote are included in the latest version of the mceusb2 driver, so I think I'll just grab and compile that anyway :)

---

