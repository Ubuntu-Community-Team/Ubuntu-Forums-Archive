---
title: "USB power management - Kindle does not charge"
date: 2011-08-16
forum: Hardware
---

### Post by tomfrancart on 2011-08-16
Dear all,

I'm having trouble charging my Amazon Kindle 3 using my laptop running ubuntu Natty.

Using windows on the same laptop (same cable, usb port,...) the Kindle charges fine.
Using Ubuntu, it does not. I suspect it is a USB power issue. I tried the following, without success:

- Ejecting the Kindle
- Disabling usb power management:
-- lsusb, get bus and device ID, the Kindle appears to show up as "Lab126"
-- echo on > /sys/bus/usb/devices/M-N/power/level, with M the bus id from lsusb and N the device nr minus one from lsusb (not sure how the bus and device IDs map to the devices under sys, but idVendor is correct)

Mounting the kindle and using it as a storage device works fine. The yellow led lights up when it's connected, but it does not charge. The Kindle is notoriously picky when it comes to voltage and power to charge. It does however not appear to be a hardware issue, as it works fine under Windows.

This problem seems to have appeared after a recent system update, but I'm not sure at which point exactly.

best regards,
Tom

--
The full output of lsusb -v is:
"Self Powered" and "MaxPower 100mA" seem to be indicative of the problem
```

Bus 003 Device 003: ID 1949:0004 Lab126 
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  idVendor           0x1949 Lab126
  idProduct          0x0004 
  bcdDevice            1.00
  iManufacturer           1 Amazon
  iProduct                2 Amazon Kindle
  iSerial                 3 B00AA0A0114600K0
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           32
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          4 Self-powered
    bmAttributes         0xc0
      Self Powered
    MaxPower              100mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           2
      bInterfaceClass         8 Mass Storage
      bInterfaceSubClass      6 SCSI
      bInterfaceProtocol     80 Bulk (Zip)
      iInterface              5 Mass Storage
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               0
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
Device Qualifier (for other device speed):
  bLength                10
  bDescriptorType         6
  bcdUSB               2.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  bNumConfigurations      1
Device Status:     0x0001
  Self Powered

```

---

### Post by slimteufel on 2011-10-05
[QUOTE=tomfrancart] words [/QUOTE]

Bump.

---

### Post by BicyclerBoy on 2011-10-05
Work-around not a fix.
Over the last 9 months of Kindle use...
I have found with 11.04 & 10.04 that the kindle must be plugged in & ejected twice in succession for it to negotiate/charge correctly.

Use the USB type A jack for plug/unplugging...the kindle end is far too delicate.

The 11.04 box (kernel or mobo H55 chipset ?) allows charging with the PC shutdown (after initiating charge).

---

### Post by tomfrancart on 2011-10-16
> **BicyclerBoy said:**
> Work-around not a fix.
Over the last 9 months of Kindle use...
I have found with 11.04 & 10.04 that the kindle must be plugged in & ejected twice in succession for it to negotiate/charge correctly.


Surprisingly that works, thanks very much for the tip!

---

### Post by shecky on 2011-11-09
An easier way is to plug it in while it's in sleep-mode. It'll wake up and get mounted, then you can just unmount through Nautilus like normal. I tried this under 11.10 with a Kindle 4 and it works every time.

---

