---
title: "Usb 3.0 + xhci_hcd + libusb problem"
date: 2012-06-06
forum: Hardware
---

### Post by dkottas on 2012-06-06
Hi all,
I am using a laptop with only USB 3.0 ports 
The ports work fine with Ubuntu. BUT,
I have a USB 2.0 device whose drivers use libusb 
Apparently there is a mis-compatibility between libusb and xhci_hcd module (USB 3.0 ports).
I get the exact same errors with this guy here who apparently tried to do the same thing

[https://groups.google.com/forum/#!msg/openkinect/VVSQzKI52bk/hY4ftuLM3mMJ]("https://groups.google.com/forum/#%21msg/openkinect/VVSQzKI52bk/hY4ftuLM3mMJ")

Use a USB 2.0 device (Kinect) through a driver that utilizes libusb and through a USB 3.0 port.

Also I think this guy ([https://bugs.launchpad.net/ubuntu/+source/libusb/+bug/979697](https://bugs.launchpad.net/ubuntu/+source/libusb/+bug/979697)) has the same problem with a USB 2.0 modem on a USB 3.0 port.

I am using a Pointgrey USB 2.0 camera.

Can I by-pass somehow xhci_hcd and enforce my ports to work as USB 2.0 through ehci_hcd or this is impossible since they are USB 3.0 ports?

I tried modprobe -r xhci_hcd but then the usb devices do not show up (although they get powered).

The USB controller of the laptop (ASUS G-55) is Intel® USB 3.0 eXtensible Host Controller Driver

Thank you,

[I had the problem with all recent Ubuntu versions ,  10.04 10.10 11.04 11.10  12.04]

---

