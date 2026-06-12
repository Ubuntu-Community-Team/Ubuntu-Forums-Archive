---
title: "Three button mouse"
date: 2007-08-19
forum: Hardware &amp; Laptops
---

### Post by greatbuckets on 2007-08-19
I have a three button (wheel) USB mouse that I use on my Dell Inspiron 1420, and clicking on the mouse wheel doesn't work.  xorg.conf has

[INDENT]
[FONT="Fixedsys"]Section "InputDevice"
        [INDENT]Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"                "/dev/input/mice"
        Option          "Protocol"              "ImPS/2"
        Option          "ZAxisMapping"          "4 5"
        Option          "Emulate3Buttons"       "false"[/INDENT]
EndSection
[/FONT][/INDENT]

Originally the Emulate3Buttons was true, which makes sense for the touchpad.  As expected, changing it to false has stopped the 3 button emulation on the touchpad, but not the USB mouse.

There is no USB mouse section in xorg.conf.  Should I set one up?  If so, what should it look like?

Output from lsusb -v:

[FONT="Fixedsys"][INDENT]Bus 004 Device 005: ID 0458:0003 KYE Systems Corp. (Mouse Systems) Genius NetScroll+
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0
  bDeviceProtocol         0
  bMaxPacketSize0         8
  idVendor           0x0458 KYE Systems Corp. (Mouse Systems)
  idProduct          0x0003 Genius NetScroll+
  bcdDevice            0.00
  iManufacturer           1 KYE
  iProduct                2 Genius USB Wheel Mouse
  iSerial                 0
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           34
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          4 HID Mouse
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
      bInterfaceClass         3 Human Interface Devices
      bInterfaceSubClass      1 Boot Interface Subclass
      bInterfaceProtocol      2 Mouse
      iInterface              5 EP1 Interrupt
        HID Device Descriptor:
          bLength                 9
          bDescriptorType        33
          bcdHID               1.00
          bCountryCode            0 Not supported
          bNumDescriptors         1
          bDescriptorType        34 Report
          wDescriptorLength      52
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
        wMaxPacketSize     0x0004  1x 4 bytes
        bInterval              10
Device Status:     0x0000
  (Bus Powered)
[/INDENT][/FONT]

---

### Post by linuxwizard on 2007-08-19
[https://help.ubuntu.com/community/ManyButtonsMouseHowto](https://help.ubuntu.com/community/ManyButtonsMouseHowto)

---

