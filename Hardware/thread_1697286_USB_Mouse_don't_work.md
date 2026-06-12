---
title: "USB Mouse don't work"
date: 2011-02-28
forum: Hardware
---

### Post by bentan on 2011-02-28
Hello all,

I have an issue, my main mouse don't work with Ubuntu 10.10 (neither with OpenSuse, Fedore, Debian...)

blue in xorg.conf is my last try !

The mouse is [http://www.continentaledison.com/produits/produits.cfm?ref=401](http://www.continentaledison.com/produits/produits.cfm?ref=401)

Sory for my poor english, i'm french and it's late :)

Thx

Extract of Xorg.0.log

[    21.466] (II) config/udev: Adding input device Newman USB Gaming Mouse (/dev/input/event3)
[    21.466] (WW) Option "Ignore" requires a boolean value
[    21.466] (**) Newman USB Gaming Mouse: Applying InputClass "evdev keyboard catchall"
[    21.466] (**) Newman USB Gaming Mouse: Applying InputClass "My Class"
[    21.466] (**) Newman USB Gaming Mouse: always reports core events
[    21.466] (**) Newman USB Gaming Mouse: Device: "/dev/input/event3"
[    21.501] (II) Newman USB Gaming Mouse: Found keys
[    21.501] (II) Newman USB Gaming Mouse: Configuring as keyboard
[    21.501] (II) XINPUT: Adding extended input device "Newman USB Gaming Mouse" (type: KEYBOARD)

Extract of kern.log

Feb 28 22:05:34 XXXX kernel: [   14.659121] usbcore: registered new interface driver hiddev
Feb 28 22:05:34 XXXX kernel: [   14.664350] input: Newman USB Gaming Mouse as /devices/pci0000:00/0000:00:1d.1/usb3/3-2/3-2:1.0/input/input3
Feb 28 22:05:34 XXXX kernel: [   14.664516] generic-usb 0003:04D9:A04A.0001: input,hidraw0: USB HID v1.10 Keyboard [Newman USB Gaming Mouse] on usb-0000:00:1d.1-2/input0
Feb 28 22:05:34 XXXX kernel: [   14.673618] generic-usb: probe of 0003:04D9:A04A.0002 failed with error -22

lsusb -v

Bus 003 Device 002: ID 04d9:a04a Holtek Semiconductor, Inc.
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0
  bDeviceProtocol         0
  bMaxPacketSize0         8
  idVendor           0x04d9 Holtek Semiconductor, Inc.
  idProduct          0xa04a
  bcdDevice            0.35
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
          bcdHID               1.10
          bCountryCode            0 Not supported
          bNumDescriptors         1
          bDescriptorType        34 Report
          wDescriptorLength      63
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
        wMaxPacketSize     0x0008  1x 8 bytes
        bInterval               2
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        1
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         3 Human Interface Device
      bInterfaceSubClass      0 No Subclass
      bInterfaceProtocol      2 Mouse
      iInterface              0
        HID Device Descriptor:
          bLength                 9
          bDescriptorType        33
          bcdHID               1.10
          bCountryCode            0 Not supported
          bNumDescriptors         1
          bDescriptorType        34 Report
          wDescriptorLength     166
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
        wMaxPacketSize     0x0008  1x 8 bytes
        bInterval               2

Extract of xorg.conf

Section "Screen"
    Identifier    "Default Screen"
    DefaultDepth    24
EndSection

Section "Module"
    Load    "glx"
EndSection

Section "Device"
    Identifier    "Default Device"
    Driver    "nvidia"
    Option    "NoLogo"    "True"
EndSection

[COLOR=Blue]Section "InputClass"
               Identifier   "My Class"
               MatchUSBID "04d9:a04a|04D9:A04A"
           MatchProduct "Newman|newman|NEWMAN"
        MatchIsPointer "True"
EndSection[/COLOR]

---

### Post by cbender on 2012-07-31
There is a workaround, but you need to recompile the Kernel:

[http://forums.opensuse.org/english/get-technical-help-here/hardware/473200-usb-gaming-mouse-04d9-a078-not-working-linux-plus-workaround.html](http://forums.opensuse.org/english/get-technical-help-here/hardware/473200-usb-gaming-mouse-04d9-a078-not-working-linux-plus-workaround.html)

I have the same Problem, and the Sharkoon Support (They are selling the similar mice) said: "No Linux Support".

---

