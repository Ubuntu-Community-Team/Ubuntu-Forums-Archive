---
title: "Kubuntu's quirky USB bus."
date: 2012-01-12
forum: Hardware
---

### Post by flyingchilli on 2012-01-12
Hi all,

I was wondering if anyone else has had a problem with the USB bus on installing Kubuntu 11.10.
Laptop = Dell Inspiron M5030.

Problem: I installed the system with the touchpad as the only mouse and all went well. I even had wifi wireless support. I then plugged a USB mouse into the bus and the  mouse moves very choppily across the desktop. I mangled with GRUB to include acpi=force irqpoll thinking there may be an interrupt problem. This did not help the chop. I noted on re-boot the system complained that there was no Synaptics driver installed during KDE desktop loading, however the touchpad still worked.

The re-install using the mouse on the USB bus:
The install went normally and with the mouse attached to the USB bus I now had lost wlan0. I imagine that this is due to a virtual USB driver for this device somewhere in the darkness.

The mouse was now gracefully smooth by the way.

I played with ifup, ifconfig etc. to no avail.
In addition I had lost my touchpad which now was now a dead doorstep to my keyboard.

I re-installed Kubuntu for the 3rd time and decided to go with network connectivity and a touchpad that is smooth and post on this forum. 

The USB mouse remains choppy as expected.

Any ideas around this issue would be appreciated.

I am a fan of all working properly and greedily wish for all usb devices to play properly.

Thank you,

---

