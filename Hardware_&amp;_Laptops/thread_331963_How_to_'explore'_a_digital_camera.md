---
title: "How to 'explore' a digital camera ?"
date: 2007-01-05
forum: Hardware &amp; Laptops
---

### Post by 4nT0 on 2007-01-05
Hello everyone!

I have a Canon Ixus 50 and Ubuntu Edgy Eft. When I plug the the camera through USB link Ubuntu detects it and launches gThumb to allow photo downloading.

How can I access my camera's disk **without** gThumb, as it was a removable drive?

In particular, I want to mount my card somewhere in my filesystem.

Here's my dmesg output when I plug in the camera:
```
[17182585.648000] usb 3-3: new high speed USB device using ehci_hcd and address 9
[17182585.796000] usb 3-3: configuration #1 chosen from 1 choice
```

Thank you!!
Anto

---

### Post by az on 2007-01-05
Your camera only offers the files through the (I forget what it's called exactly) media tranfer protocol.  The libgphoto2 functions allow linux to talk to such a device and get thumbnails, download and upload to such a device, but it's not the same as mouting it as a USB mass strage device.

If you got a card reader and inserted the memory card into it, linux would mount it as a filesystem because the card reader would interface with your computer in that way.

You should be able to browse the camera's contents through the gthumb interface, though.

---

### Post by 4nT0 on 2007-01-05
You mean "PTP mode"? It appears when using F-Spot instead of gThumb to import photo.

> You should be able to browse the camera's contents through the gthumb interface, though.But I cannot delete or rename or move files into my card... :(

Thank you for reply!

---

