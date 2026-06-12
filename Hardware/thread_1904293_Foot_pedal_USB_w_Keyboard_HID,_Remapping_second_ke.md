---
title: "Foot pedal USB w/ Keyboard HID, Remapping second keyboard to custom keys"
date: 2012-01-04
forum: Hardware
---

### Post by fragged on 2012-01-04
Hey all,

I've recently purchased a foot pedal USB device from Ebay, and it appears to interface as a keyboard rather than a joystick. 

It appears that the device is using keyboard protocol (See lspci dump below). 

Currently, without any configuration, tapping the pedals results in the equivalent of pressing the keys a b or c depending on which pedal is pressed - which is fine for my needs. 

I'm wondering, how would I go about re-mapping the keys for one specific USB device to keys of my choice? I'm hoping to bind these to events in Ratpoison wm eventually, which means they can be pretty much any key, but given I need my current keyboards a, b and c keys to function correctly, things get a little complicated... I'm scratching my head as to where to start on this one, any advice would be appreciated :) 

- Fragged

EDIT: lspci dump

```
Bus 007 Device 003: ID 0c45:7403 Microdia 
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0         8
  idVendor           0x0c45 Microdia
  idProduct          0x7403 
  bcdDevice            0.01
  iManufacturer           1 RDing
  iProduct                2 FootSwitchV1.0
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
          wDescriptorLength     119
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
        bInterval              10
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
          bcdHID               1.10
          bCountryCode            0 Not supported
          bNumDescriptors         1
          bDescriptorType        34 Report
          wDescriptorLength      41
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
        bInterval              10
Device Status:     0x0000
  (Bus Powered)

```

---

### Post by archi02 on 2012-02-01
Did find now any answer ? I'm exactly in the same situation... thanks for help.

---

### Post by irritum on 2012-04-23
Greetings, I've ran across a similar problem with some defiant MCE remotes. There are a few things out there you can try. Option #2 and #1 may be the easiest to get things working for you, but I would strongly suggest looking into #3 as it provides a much cleaner solution without the need for 3rd party software.

1. [http://www.bedroomlan.org/projects/evrouter](http://www.bedroomlan.org/projects/evrouter) - a daemon which captures input from /dev/input/eventX device and generates X11 key events according to your custom configuration.

2. [http://forum.xbmc.org/showthread.php?tid=88560](http://forum.xbmc.org/showthread.php?tid=88560) - describes a similar solution using "hid_mapper" which also remaps events (or keys) but at a lower (HID) level. You should also read 1st comment to this post: [http://www.omcentre.com.au/hardware/m350-media-centre/wireless-multimedia-infrared-ir-remote-controller-deal-extreme-34435/#c471](http://www.omcentre.com.au/hardware/m350-media-centre/wireless-multimedia-infrared-ir-remote-controller-deal-extreme-34435/#c471) - it describes how to automate hid_mapper with udev.

3. [http://askubuntu.com/questions/69804/how-do-i-change-the-keymap-of-a-single-device-logitech-presenter](http://askubuntu.com/questions/69804/how-do-i-change-the-keymap-of-a-single-device-logitech-presenter) - this is by far the best way to go in the end. This method uses udev and thus much more likely to survive a release upgrade, kernel or library change than non-maintained (by Canonical or its partners) 3rd party software.

I hope this helps!

---

### Post by rgerganov on 2012-08-22
Hi,

Looking at the productId:vendorId combination, it seems that you are using the foot pedal sold by PCsensor. I have implemented command line utility to program this pedal and it runs on Linux. You can get it from here: [https://github.com/rgerganov/footswitch](https://github.com/rgerganov/footswitch)

Cheers!

---

### Post by ulrichard on 2013-05-02
Hi,
I don't have a foot pedal, but a small handheld keyboard with only six buttons:
[http://dx.com/p/6-key-usb-handle-hid-keyboard-173cm-cable-70892](http://dx.com/p/6-key-usb-handle-hid-keyboard-173cm-cable-70892)

It has the exact same vendor and device id as is listed above. 
I wanted to use it as chording keyboard:
[http://gkos.com/gkos/arduino/](http://gkos.com/gkos/arduino/)

But checking the output of "sudo /lib/udev/keymap -i input/event14", I'm not sure that's even possible. 
When I keep key one pressed, I keep getting "a"'s in the output. 
Now I add key two, I only get "b"'s in the output, and even when I release key one, there's no notice.

Assuming, the hardware supports it, is it possible to implement a chording keyboard with an udev keymap alone? Or would I have to write a driver for it?

---

