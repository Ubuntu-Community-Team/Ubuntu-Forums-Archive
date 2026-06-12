---
title: "unknown usbfs filesystem"
date: 2010-03-24
forum: Hardware
---

### Post by deusthe on 2010-03-24
Hello,

I'm trying to mount an USB camera for a custom application.
$sudo mount -t usbfs none /proc/bus/usb
mount: type inconnu de système de fichiers 'usbfs'
(unknown filesystem type 'usbfs')

Obviously, the USB camera is connected. lsusb correctly shows the peripheral.

I failed to find a package which includes the usbfs.
I have a minimal xubuntu distribution based on karmic.
The kernel is 2.6.31-20-generic.

This distribution should include a usbfs support but this one does not. Maybe I uninstalled something that matters ?

What is wrong ?

Best regards,
Richard

---

### Post by deusthe on 2010-03-26
up :'(

---

### Post by befeleme on 2010-05-11
The problem may be in the kernel you use. I also used to mount usbfs because of a USB programmer for PIC microcontrollers. Everything worked fine until I upgraded the kernel to  2.6.31-20. If you still have kernel 2.6.31-19, try this. At least for me it worked.

---

