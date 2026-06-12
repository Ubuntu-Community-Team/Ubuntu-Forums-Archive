---
title: "HP Compaq L2105tm Multi Touch"
date: 2009-12-04
forum: Hardware
---

### Post by XDrive on 2009-12-04
I have a couple HP Compaq L2105tm Multi Touch monitors I'm trying to get going with ubuntu desktop x86_64 9.10.
[http://h10010.www1.hp.com/wwpc/us/en/sm/WF05a/382087-382087-64283-3181050-3181048-4031739.html](http://h10010.www1.hp.com/wwpc/us/en/sm/WF05a/382087-382087-64283-3181050-3181048-4031739.html)

They're very new, and as such I've found little to no info on setting the up in the linux community in general.

From what I can tell, HP doesn't currently offer linux drivers for them.
I haven't had much time to play with them yet (got them yesterday) so I don't know if they'll require third party drivers but I figured I'd start a thread to post my findings.

They're not detected as mouse input devices but rather generic HID devices:

generic-usb 0003:0408:3000.0001: hiddev96,hidraw0: USB HID v1.10 Device [Quanta Computer Inc. Optical Touch Screen] on usb-0000:00:1d.0-1/input0

So they don't work out of the box in X.
I'll post more info as I play with these things.

```
Bus 006 Device 002: ID 0408:3000 Quanta Computer, Inc. 
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.10
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  idVendor           0x0408 Quanta Computer, Inc.
  idProduct          0x3000 
  bcdDevice            0.00
  iManufacturer           1 Quanta Computer Inc.
  iProduct                2 Optical Touch Screen
  iSerial                 0 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           34
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
      bInterfaceClass         3 Human Interface Device
      bInterfaceSubClass      0 No Subclass
      bInterfaceProtocol      0 None
      iInterface              0 
      ** UNRECOGNIZED:  09 21 10 01 00 01 22 da 00
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x83  EP 3 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               8
Device Status:     0x0000
  (Bus Powered)
```

---

### Post by euxneks on 2010-01-05
> **XDrive said:**
> I have a couple HP Compaq L2105tm Multi Touch monitors I'm trying to get going with ubuntu desktop x86_64 9.10.
[http://h10010.www1.hp.com/wwpc/us/en/sm/WF05a/382087-382087-64283-3181050-3181048-4031739.html](http://h10010.www1.hp.com/wwpc/us/en/sm/WF05a/382087-382087-64283-3181050-3181048-4031739.html)

They're very new, and as such I've found little to no info on setting the up in the linux community in general.

From what I can tell, HP doesn't currently offer linux drivers for them.
I haven't had much time to play with them yet (got them yesterday) so I don't know if they'll require third party drivers but I figured I'd start a thread to post my findings.

They're not detected as mouse input devices but rather generic HID devices:

generic-usb 0003:0408:3000.0001: hiddev96,hidraw0: USB HID v1.10 Device [Quanta Computer Inc. Optical Touch Screen] on usb-0000:00:1d.0-1/input0

So they don't work out of the box in X.
I'll post more info as I play with these things.

```
Bus 006 Device 002: ID 0408:3000 Quanta Computer, Inc. 
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.10
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  idVendor           0x0408 Quanta Computer, Inc.
  idProduct          0x3000 
  bcdDevice            0.00
  iManufacturer           1 Quanta Computer Inc.
  iProduct                2 Optical Touch Screen
  iSerial                 0 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           34
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
      bInterfaceClass         3 Human Interface Device
      bInterfaceSubClass      0 No Subclass
      bInterfaceProtocol      0 None
      iInterface              0 
      ** UNRECOGNIZED:  09 21 10 01 00 01 22 da 00
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x83  EP 3 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               8
Device Status:     0x0000
  (Bus Powered)
```

I've got an Acer T230H which also has the Quanta Computer lsusb listing. Have you made any progress with your touchscreens yet?

---

### Post by euxneks on 2010-01-10
For further information, I was able to get an ACER T230H touchscreen working: [http://ubuntuforums.org/showthread.php?t=1375047](http://ubuntuforums.org/showthread.php?t=1375047)

---

### Post by StCh on 2010-01-11
I have just completed a kernel driver that fully handles the Quanta touch in the Acer T230H: multitouch events plus single touch emulation. I just read in this thread that the device is the same as the one in the L2105tm (same VendorID/ProductID) so the driver should work there are well.

When this kernel driver is activated, the device can be used as a touchscreen with the evdev X.org driver, and as a multitouch screen with a patched evdev driver, as explained at [http://lii-enac.fr/en/projects/shareit/xorg.html]("http://http://lii-enac.fr/en/projects/shareit/xorg.html")

The driver was submitted for inclusion in Linux 2.6.33. Meanwhile, it is available at [http://lii-enac.fr/en/projects/shareit/hid-acer.c]("http://lii-enac.fr/en/projects/shareit/hid-acer.c") and there are instructions at [http://lii-enac.fr/en/projects/shareit/linux-howto.html]("http://lii-enac.fr/en/projects/shareit/linux-howto.html")

When I wrote the driver I thought the device was specific to Acer. Now that I know about the HPs, the driver will probably be renamed into hid-quanta.c at some point in the future.

---

### Post by bruceleo on 2010-02-19
The link is broken, anyone know where we can get this driver?

---

### Post by Ayuthia on 2010-02-19
It looks like they have changed the name of the source to hid-quanta.c based on this [link]("http://www.lii-enac.fr/en/projects/shareit/multitouch-devices.html").  The link to the source should be [here]("http://www.lii-enac.fr/en/projects/shareit/hid-quanta.c").  I hope that helps.

---

### Post by teaker1s on 2010-08-27
[http://www.ramoonus.nl/2010/05/linux-kernel-2-6-34-installation-guide-for-ubuntu-linux-10-04/](http://www.ramoonus.nl/2010/05/linux-kernel-2-6-34-installation-guide-for-ubuntu-linux-10-04/)

---

