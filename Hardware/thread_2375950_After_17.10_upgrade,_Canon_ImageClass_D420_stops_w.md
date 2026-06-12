---
title: "After 17.10 upgrade, Canon ImageClass D420 stops working"
date: 2017-10-29
forum: Hardware
---

### Post by nathan15 on 2017-10-29
I just upgraded my Asus Zenbook from 17.04 to 17.10, using GNOME on both, and my Canon ImageClass D420, which was working perfectly well before, is no longer working. When I try to print, there's no error. The print job just stays in the print queue, where it says "Processing" indefinitely. No sign of activity from the printer. I tried reinstalling the drivers from the Canon website, restarting, removing and re-adding the printer in the GUI, but no luck.

The built-in scanner doesn't work either anymore, although it did before the upgrade. Now, when I open Simple Scan and try to run it, there are some noises from the scanner, as if it's working, but the circles just keep spinning in Simple Scan, and then an error comes up: "Failed to scan / Error communicating with scanner."

What changed in the upgrade that would cause this change in behavior? Any suggestions?

Thank you so much in advance for considering this.

---

### Post by momoxxl on 2017-11-16
I do have the same problem with my Samsung scanner (SCX-4833FD, multi-function device). With 17.04 the device was working without doing anything special. Just plug it in and use it. After upgrading to 17.10 the scanner isn´t working anymore. Printing is still possible.
When I start simple-scan the scanner was detected. But starting a scan gives an error message like "failed to scan".

I can not find any errors messages, neither on the console from where I started simple-scann, neither in any logs.

---

### Post by momoxxl on 2017-11-19
This problem occurs when connecting a usb2-devive to a usb3-port. Try setting SANE_USB_WORKAROUND=1 in ~/.bashrc. Start a new bash shell. From this run simple-scan. This worked for me.

---

