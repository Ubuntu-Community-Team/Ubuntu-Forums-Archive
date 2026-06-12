---
title: "Problem with webcam in laptop HP easynote under Ubuntu 10.04"
date: 2010-07-09
forum: Hardware
---

### Post by fduran on 2010-07-09
I have a problem split in 2 parts:

First one:
I can't fins the way to install properly the webcam in my laptop HP easynote under Ubuntu 10.04

The output for "lsusb" contains this line
Bus 001 Device 004: ID 174f:8a12 Syntek Syntek 0.3MPixel USB 2.0 UVC PC Camera

Second one:
When I try to use the webcam from a Windows installed in a Virtualbox, I can't cause the Virtualbox don't recognize the USB and the webcam is on of the USB devices. I've tried several versions of VirtualBox but it doesn't work.

Anyone can help?

Thanks! :)

---

### Post by westie457 on 2011-11-18
> **fduran said:**
> I have a problem split in 2 parts:

First one:
I can't fins the way to install properly the webcam in my laptop HP easynote under Ubuntu 10.04

The output for "lsusb" contains this line
Bus 001 Device 004: ID 174f:8a12 Syntek Syntek 0.3MPixel USB 2.0 UVC PC Camera

Second one:
When I try to use the webcam from a Windows installed in a Virtualbox, I can't cause the Virtualbox don't recognize the USB and the webcam is on of the USB devices. I've tried several versions of VirtualBox but it doesn't work.


Anyone can help?

Thanks! :)

You have to add yourself to the vboxusrs group. System>Administration>Users and Groups. Also check that USB is enabled in the guest machine settings.


PS welcome to the Forum.

---

