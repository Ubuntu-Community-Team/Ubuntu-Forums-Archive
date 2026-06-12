---
title: "USB mouse problems"
date: 2005-05-01
forum: Hardware &amp; Laptops
---

### Post by ZC3rr0r on 2005-05-01
After some initial problems with Ubuntu, I've run into another one ;)

Problem: When I use a USB mouse (Logitech MX300) with my laptop, my cursor freezes every now and then. The only way I found to fix it was to unplug and replug the mouse. This doesn't occur with my touchpad.

Output dmesg: Nothing, other than a message i get when I eject and replug it:

usb 1-2: USB disconnect, address 9
usb 1-2: new low speed USB device using uhci_hcd and address 10
input: USB HID v1.10 Mouse [B16_b_02 USB-PS/2 Optical Mouse] on usb-0000:00:11.2-2

output lspci: (so that you know what usb controller I have):

0000:00:11.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 23)
0000:00:11.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 23)
0000:00:11.4 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 23)

Question: 

Please, if anyone knows how to fix this, I'd be very pleased, since it's annoying as hell, and I often use my mouse quite often.
I can supply any output you may want to take a look at. Thanks in advance.

---

### Post by ZC3rr0r on 2005-05-01
Please, anyone? This is the singlemost annying problem I have at the moment, and I would love to see this fixed.

---

### Post by nad on 2005-05-01
Try any of the boot options acpi=off | noapic | pci=usepirqmask . Some of the new via controllers don't play nicely with these standards. You could also try adjusting your bios settings; no irq for your usb devices and/or set the pnp operating system to yes.

---

### Post by Dam on 2005-05-02
There's another thread with the same topic: [http://www.ubuntuforums.org/showthread.php?t=28173](http://www.ubuntuforums.org/showthread.php?t=28173)

Nobody could find a solution so far...  :-|

---

### Post by ZC3rr0r on 2005-05-02
Thanx alotfor the fast responses. Perhaps it has something to do with Logitech mouses, because my MX510 does the same thing on my pc....under windows....:S

<edit> Minor typo

---

### Post by camp on 2005-05-04
Hi,

Maybe not exactly what you want to hear... but my USB Logitech mouse started to work after I had put: acpi=off as a kernel parameter in grub.

Try it!

/Camp

---

