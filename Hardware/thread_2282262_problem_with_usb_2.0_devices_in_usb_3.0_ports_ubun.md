---
title: "problem with usb 2.0 devices in usb 3.0 ports ubuntu 14.04.2"
date: 2015-06-12
forum: Hardware
---

### Post by Hodor on 2015-06-12
Hi,
Was having troubles with usb 2.0 devices (mouse / keyboard) in usb 3.0 ports on ubuntu 14.04.2.
Solved by altering USB configurations in UEFI setup utility (ASrock z97 extreme 6) - nice.

---

### Post by Vladlenin5000 on 2015-06-14
What settings have you changed?

---

### Post by Hodor on 2015-06-22
I followed the hints in the uefi setup utility guide re 'usb configuration' for dealing with usb problems (27-28:disable usb legacy support, disable legacy usb 3.0 support, enable usb compatibility patch) - but since upgrading my bios to 2.30 I've reverted to the default settings and all seems well.
Edit: actually, for usb 3.0 support I think I had selected 'select UEFI setup only'.
Also, a warning: with these options I needed to use a ps2 keyboard in the uefi setup utility (but usb keyboard / mouse worked fine in windows 8.1 / ubuntu 14.404.2)!

---

