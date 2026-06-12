---
title: "Will X-media Model No. XM-EN3400-BK hard drive enclosure work with ubunut?"
date: 2016-09-15
forum: Hardware
---

### Post by AbleTassie on 2016-09-15
I bought an X-Media Model No. XM-EN3400-BK 3.5" Hard Drive Enclosure USB2.0 to IDE/SATA. I want to use it with an old 1TB Hard Drive for backup. Under Specs it says supported OS: Windows 98SE/ME/2000/XP/Vista/7/8/10/MAC9.0x or above.

I am wondering if it will work with Ubuntu.

Anybody have any opinions?

Thanks,

A.

---

### Post by Bucky Ball on 2016-09-15
Have you plugged it in and tried? Generally easiest way to find out if you have the device sitting there. If you haven't already, do so. When it is in and on, open Gparted (install if you haven't already) and there's a drop-box menu in the top right corner. Your internal disk should be sda. In that drop down list, do you see sdb? That is the external. (If you have two internal drives, sda and sdb, the external will be sdc.)

You can also run 'lsusb' in a terminal with the drive plugged in and switched on and you should see it there.

Unless this device is from a planet where they use a totally different protocol for USB devices and/or mass storage devices, then there's no reason why it shouldn't work. A USB external enclosure is a USB external enclosure is a ... etc. Wouldn't take a lot of notice that 'Supported on Linux' is not advertised. It generally isn't.

---

