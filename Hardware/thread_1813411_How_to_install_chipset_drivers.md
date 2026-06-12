---
title: "How to install chipset drivers"
date: 2011-07-27
forum: Hardware
---

### Post by unckybob on 2011-07-27
I am having intermittent trouble with recognizing USB devices on my Ubuntu partition with my ThinkPad T40p. A hardware repair book says that I should make sure the proper chipset drivers are installed (this is in Windows, but I think it makes sense to do the same in Ubuntu). An "lspci" at the command prompt yields: 

00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 01)

I assume this helps one know what kind of chipset I am using. Can someone please tell me how to install the proper drivers?

---

### Post by unckybob on 2011-08-01
Apparently, chipset drivers in linux are included with the kernel.

---

