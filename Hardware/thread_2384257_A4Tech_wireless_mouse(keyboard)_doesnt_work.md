---
title: "A4Tech wireless mouse(/keyboard) doesnt work"
date: 2018-02-04
forum: Hardware
---

### Post by 0xde1e7e on 2018-02-04
Hello, 

first of all, im not an expert, just a regular linux user.
I just bought a wireless mouse and keyboard combo.
totally common devices, keyboard: a4tech gk-85, mouse a4tech g3-200n
nano receiver is plugged in a usb slot and keyboard is working well, but the mouse...
pisses me off, it all looks good to me.
any tip,trick or treat?
(note: another nanoreceiver is attached, but even if not, the mouse dosent work)

```
uname -a
===================

Linux xxxxxx 4.13.0-32-generic #35~16.04.1-Ubuntu SMP Thu Jan 25 10:13:43 UTC 2018 x86_64 x86_64 x86_64 GNU/Linux

lsmod:
===================
hid_generic            16384  0
usbhid                 49152  0
hid                   118784  3 hid_generic,usbhid,hid_a4tech
uas                    24576  1
usb_storage            69632  1 uas

dmesg | grep -i usb (un/replug the nanoreceiver)
====================
[12945.221426] usb 3-3: USB disconnect, device number 8
[12962.814777] usb 3-3: new full-speed USB device number 9 using xhci_hcd
[12962.956412] usb 3-3: New USB device found, idVendor=09da, idProduct=054f
[12962.956416] usb 3-3: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[12962.956418] usb 3-3: Product: USB Device
[12962.956420] usb 3-3: Manufacturer: A4TECH
[12962.959115] input: A4TECH USB Device as /devices/pci0000:00/0000:00:14.0/usb3/3-3/3-3:1.0/0003:09DA:054F.000F/input/input28
[12963.019165] hid-generic 0003:09DA:054F.000F: input,hiddev0,hidraw0: USB HID v1.11 Keyboard [A4TECH USB Device] on usb-0000:00:14.0-3/input0
[12963.020162] input: A4TECH USB Device as /devices/pci0000:00/0000:00:14.0/usb3/3-3/3-3:1.1/0003:09DA:054F.0010/input/input29
[12963.020266] hid-generic 0003:09DA:054F.0010: input,hidraw1: USB HID v1.11 Mouse [A4TECH USB Device] on usb-0000:00:14.0-3/input1


lsusb -vv:
====================
Bus 003 Device 008: ID 09da:054f A4Tech Co., Ltd. 
Couldn't open device, some information will be missing
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.10
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0         8
  idVendor           0x09da A4Tech Co., Ltd.
  idProduct          0x054f 
  bcdDevice            2.74
  iManufacturer           1 
  iProduct                2 
  iSerial                 0 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           59
    bNumInterfaces          2
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0xa0
      (Bus Powered)
      Remote Wakeup
    MaxPower              100mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         3 Human Interface Device
      bInterfaceSubClass      1 Boot Interface Subclass
      bInterfaceProtocol      1 Keyboard
      iInterface              0 
        HID Device Descriptor:
          bLength                 9
          bDescriptorType        33
          bcdHID               1.11
          bCountryCode            0 Not supported
          bNumDescriptors         1
          bDescriptorType        34 Report
          wDescriptorLength     139
         Report Descriptors: 
           ** UNAVAILABLE **
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x000d  1x 13 bytes
        bInterval               1
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        1
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         3 Human Interface Device
      bInterfaceSubClass      1 Boot Interface Subclass
      bInterfaceProtocol      2 Mouse
      iInterface              0 
        HID Device Descriptor:
          bLength                 9
          bDescriptorType        33
          bcdHID               1.11
          bCountryCode            0 Not supported
          bNumDescriptors         1
          bDescriptorType        34 Report
          wDescriptorLength      73
         Report Descriptors: 
           ** UNAVAILABLE **
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x82  EP 2 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0007  1x 7 bytes
        bInterval               1

```
(PS: the mouse dosent even light up, checked with two different battery, so maybe the device is faulty)
(PS2: the very first time I attached the mouse, it was recognized, but the pointer was jumping everywhere on the screen and i just rebooted the machine, but by that time the light was off as well)

any suggestion?

---

### Post by Autodave on 2018-02-04
Try them both on another machine. However, sounds like a defective mouse to me.

---

### Post by 0xde1e7e on 2018-02-04
Actually I have tried on a Win machine, result is the same. keyboard ok, mouse not.

---

### Post by Autodave on 2018-02-05
We need a moment of silence then for the mouse.

---

