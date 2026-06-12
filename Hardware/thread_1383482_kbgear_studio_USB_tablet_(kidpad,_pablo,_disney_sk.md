---
title: "kbgear studio USB tablet (kidpad, pablo, disney sketchboard) not recognized in Karmic"
date: 2010-01-17
forum: Hardware
---

### Post by Michael K. on 2010-01-17
I'm having the same problem as this guy:

[http://ubuntuforums.org/showthread.php?t=1158552](http://ubuntuforums.org/showthread.php?t=1158552)

I have a USB graphics tablet that shows up under lsusb, but otherwise does nothing.  According to that post, this model worked fine under 8.04 (but not 8.10) so the knowledge is out there . . . somewhere.

It's known as the KB Gear Studio, KB Gear KidPad, Pablo, or Disney SketchBoard, but generally identifies as KBGear under the hood.  It's an inexpensive pressure sensitive graphics tablet, and I would dearly love to do some drawing with it.

Please help.  
Thank you.

lsusb -v:

Bus 002 Device 004: ID 084e:1001 KB Gear 
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0         8
  idVendor           0x084e KB Gear
  idProduct          0x1001 
  bcdDevice            0.02
  iManufacturer           0 
  iProduct                1 
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
      bInterfaceSubClass      1 Boot Interface Subclass
      bInterfaceProtocol      2 Mouse
      iInterface              0 
      ** UNRECOGNIZED:  09 21 00 01 00 01 22 4e 00
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0008  1x 8 bytes
        bInterval              10
cannot read device status, Operation not permitted (1)

---

### Post by Favux on 2010-01-17
Michael K.,

Welcome to Ubuntu forums!

What release are you using?  Karmic (9.10)?

The key question is was what driver was the tablet using in Hardy?  If we knew that we could see if it is still around and being updated.

In your lsusb -v it is identifying as:
```
idVendor 0x084e KB Gear
idProduct 0x1001 
```

You could also look at:
```
grep -i name /proc/bus/input/devices
```

If we knew the driver we could look at your lshal:
```
lshal>MichaelK_lshal.txt
```
Using the identifiers above in gedit you can use find to locate your tablet section(s) and then using that construct a .fdi to use the driver.

The other possibility is seeing if another tablet driver would "work".  Like the Aiptek, or WizardPen, or evdev.

---

### Post by Michael K. on 2010-01-24
Thanks for the step-by-step.  I'll give it a try (in my Copious Free Time) and let you know how it works.

---

