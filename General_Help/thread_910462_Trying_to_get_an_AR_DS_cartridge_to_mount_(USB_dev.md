---
title: "Trying to get an AR DS cartridge to mount (USB device.)"
date: 2008-09-04
forum: General Help
---

### Post by artanis00 on 2008-09-04
I have an Action Replay DS, and when I plug it into the computer, I can see it in lsusb and gnome-device-manager, but I can't get it to do anything else. And of course, the software it came with doesn't do much without the card.

Is there a way to mount the card and try to read or write to it? It doesn't seem to have acquired a /dev/sd* file like the other devices, and mount doesn't like the /dev/bus/usb file.

Thank you for any assistance you can provide.

```

:~$ sudo lsusb -d 05fd:eeae -v

Bus 005 Device 023: ID 05fd:eeae InterAct, Inc. 
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.10
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0         8
  idVendor           0x05fd InterAct, Inc.
  idProduct          0xeeae 
  bcdDevice            3.01
  iManufacturer           1 Datel
  iProduct                2 NDS Link
  iSerial                 0 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           32
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
      bNumEndpoints           2
      bInterfaceClass         0 (Defined at Interface level)
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
        wMaxPacketSize     0x0008  1x 8 bytes
        bInterval               1
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x02  EP 2 OUT
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0008  1x 8 bytes
        bInterval               1
Device Status:     0x0000
  (Bus Powered)

```

---

### Post by artanis00 on 2008-09-05
Dunno what this forum's stance on bumping threads is, so I'm only going to do it once.

Again, any assistance is greatly appreciated.

---

