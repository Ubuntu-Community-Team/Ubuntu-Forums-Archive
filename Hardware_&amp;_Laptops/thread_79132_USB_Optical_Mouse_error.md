---
title: "USB Optical Mouse error"
date: 2005-10-19
forum: Hardware &amp; Laptops
---

### Post by redemption on 2005-10-19
Hello,
I have an unbranded mini usb optical mouse.
When I first installed Hoary, I had no problems simply plugging this in and it worked.
however, now the laser keeps flashing and the mouse fails to work

here is the output from /var/log/messages after I plug it in:

Oct 19 21:06:17 localhost kernel: usb 1-2: new low speed USB device using uhci_hcd and address 3
Oct 19 21:06:17 localhost kernel: usb 1-2: new low speed USB device using uhci_hcd and address 4
Oct 19 21:06:18 localhost kernel: usb 1-2: new low speed USB device using uhci_hcd and address 5
Oct 19 21:06:20 localhost kernel: usb 1-2: new low speed USB device using uhci_hcd and address 8
Oct 19 21:06:21 localhost kernel: usb 1-2: new low speed USB device using uhci_hcd and address 11
Oct 19 21:06:23 localhost kernel: usb 1-2: new low speed USB device using uhci_hcd and address 13
Oct 19 21:06:24 localhost kernel: usb 1-2: new low speed USB device using uhci_hcd and address 14
Oct 19 21:06:24 localhost kernel: usb 1-2: new low speed USB device using uhci_hcd and address 15
Oct 19 21:06:36 localhost kernel: usb 1-2: new low speed USB device using uhci_hcd and address 18
Oct 19 21:06:37 localhost kernel: usb 1-2: new low speed USB device using uhci_hcd and address 20
Oct 19 21:06:38 localhost kernel: usb 1-2: new low speed USB device using uhci_hcd and address 21
Oct 19 21:06:40 localhost kernel: usb 1-2: new low speed USB device using uhci_hcd and address 24

etc..

/etc/X11/xorg.conf shows this entry under the touchpad entry:

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"                "/dev/input/mice"
        Option          "Protocol"              "ImPS/2"
        Option          "Emulate3Buttons"       "true"
        Option          "ZAxisMapping"          "4 5"
EndSection

---

