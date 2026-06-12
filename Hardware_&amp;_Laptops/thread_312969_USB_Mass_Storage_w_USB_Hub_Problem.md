---
title: "USB Mass Storage w/ USB Hub Problem"
date: 2006-12-05
forum: Hardware &amp; Laptops
---

### Post by HamCoder on 2006-12-05
I have a laptop drive in a separate usb case.  The computer has its own hard drive and USB1 ports.  When I plug the usb laptop drive into a usb port, everything looks/works OK.  (Although Edgy complains about a USB2.0 drive in a USB1.0 slot.) 

The problem is that when I plug a usb hub into the port and the laptop drive into the hub, the laptop drive never fully connects.  Lights blink and the drive sounds like it wants to power-up, but it never appears on the desktop or in output from lsbusb or sudo fdisk -l.

I get the same results on both a desktop (with 2 usb ports) and a laptop (1 port).  The desktop is a dual-boot box.  When I boot WinXP, it sees the usb drive through the hub.  How do I make Edgy see the through the hub?

Thanks.

---

### Post by Mike'sHardLinux on 2006-12-06
Does the usb drive use a power adapter, or get its power from the usb port? Also, is the hub a powered hub?

---

### Post by HamCoder on 2006-12-06
Mike, the usb drive has no separate power, so it comes from the hub or the PC depending on where I plug it in.  I've tried two different hubs.  One has only a single connection to the PC, so it must be an unpowered hub.  The other hub has a Y-cable with both red and black connectors that plug into the PC.  I get the same results whether I plug in the red or the black connector.  Both the laptop and the desktop only have USB1.0 ports; does that make a power difference?

---

