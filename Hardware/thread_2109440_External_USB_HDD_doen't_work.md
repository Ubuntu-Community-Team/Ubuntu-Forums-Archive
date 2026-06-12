---
title: "External USB HDD doen't work"
date: 2013-01-27
forum: Hardware
---

### Post by hammer_ortiz on 2013-01-27
I have Ubuntu 12.10 (using LXDE) installed in a Acer Aspire ZG5 and my external USB HDD it doesn't work.

The HDD is working perfectly in different computers using differents OS (Windows XP, Windows 7, Mandriva)

I have tried different solutions like change the autosuspend parameter in /sys/module/usbcore/parameters/autosuspend to -1 but nothing works.

My dmesg output when I plug the HDD is:

```
[18841.980126] usb 3-1: new full-speed USB device number 28 using uhci_hcd
[18842.396114] usb 3-1: device not accepting address 28, error -71
[18842.508078] usb 3-1: new full-speed USB device number 29 using uhci_hcd
[18842.924115] usb 3-1: device not accepting address 29, error -71
[18843.036172] usb 3-1: new full-speed USB device number 30 using uhci_hcd
[18843.156122] usb 3-1: device descriptor read/64, error -71
[18843.380096] usb 3-1: device descriptor read/64, error -71
[18843.596125] usb 3-1: new full-speed USB device number 31 using uhci_hcd
[18843.716096] usb 3-1: device descriptor read/64, error -71
[18843.944157] usb 3-1: device descriptor read/64, error -71
[18844.048126] hub 3-0:1.0: unable to enumerate USB device on port 1

```

lsusb and fdisk -l don't notice if the HDD is plugged.

Can anyone help me?

---

### Post by SuperFreak on 2013-01-27
Just a shot in the dark here, but are you using USB 3.0 connections. If so try connecting to a USB 2 connection on the computer

---

### Post by hammer_ortiz on 2013-01-27
> **SuperFreak said:**
> Just a shot in the dark here, but are you using USB 3.0 connections. If so try connecting to a USB 2 connection on the computer

Thanks for the attention but no, I'm using USB 2 connections

---

