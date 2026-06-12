---
title: "&quot;WacomOpenTablet: Invalid argument&quot; from wacdump?"
date: 2005-12-21
forum: Hardware &amp; Laptops
---

### Post by jejones3141 on 2005-12-21
I am now trying to install a Wacom Graphire 3 on my sister's computer, which is now upgraded to Breezy Badger. Following the Linux Wacom Project instructions, I plug it in; it's detected, the wacom module is loaded. "xxd /dev/input/mouse1" obligingly emits lots of output when I use the pen on the graphics pad. However, when I run

wacdump /dev/input/mouse1

I get the error message

WacomOpenTablet: Invalid argument

What am I overlooking, and what does that message mean?

---

### Post by 23meg on 2005-12-26
Try wacdump's -f parameter with the device code corresponding to your tablet, which I think you can find with the --help parameter or on the manpage.

---

### Post by jejones3141 on 2005-12-30
I was handing it the wrong device. /dev/input/wacom is linked to the right place, and after revising xorg.conf to use /dev/input/wacom instead of /dev/input/mouse1, GIMP recognizes the extended input device.

---

