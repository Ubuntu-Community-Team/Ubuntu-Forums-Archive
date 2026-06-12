---
title: "USB conflict between DSL modem and mouse"
date: 2007-11-28
forum: Hardware &amp; Laptops
---

### Post by Trucoto on 2007-11-28
I'm on Ubuntu 7.10 on an old Pentium 4 1.4GB box:

> uname -a

Linux leandro-desktop 2.6.22-14-generic #1 SMP Sun Oct 14 23:05:12 GMT 2007 i686 GNU/Linux

I have two USB devices: an ADSL modem (Huawei SmartAX 810), handled succesfully by the ueagle driver ([http://eagle-usb.org/](http://eagle-usb.org/)), and a Microsoft IntelliMouse. I have an USB extension for four additional USB ports, but it doesn't make a difference for this problem if it's plugged in or not, or whether the devices are plugged in the extension or directly to the mainboard ports.

> lsusb

Bus 002 Device 001: ID 0000:0000
Bus 001 Device 005: ID 1110:9031 Analog Devices Canada, Ltd (Allied Telesyn)  <- this is the modem
Bus 001 Device 004: ID 045e:0039 Microsoft Corp. IntelliMouse Optical
Bus 001 Device 002: ID 03eb:0902 Atmel Corp. <- this is the USB extension
Bus 001 Device 001: ID 0000:0000

When the modem loads the firmware (taken from [http://eagle-usb.org/ueagle-atm/non-free/](http://eagle-usb.org/ueagle-atm/non-free/)), the mouse stops working. If I unplug the modem, the mouse works OK. With the modem on, if I unplug the mouse and plug it back again, it works, but the modem stops working. In Windows XP, mouse and modem live together with no quarrels. The modem itself seems to work alright with its ueagle driver, connecting to internet and all. Problem is the modem seems to exclude the mouse, and vice versa. In dmesg (I don't know if it's related), I see several times a line saying "reset low speed USB device".
If there's any other information I can provide to solve this, I'll be happy to oblige. I wanted to switch from XP to Linux, but with this problem, the box is completely useless. Any help is really appreciated.

---

### Post by ralbert007 on 2007-12-06
Hi are you from argentina? i have the same problem..my mouse and my modem doesnt work if i plug them togheter..only if one is plug in works.. I search everywhere looking for a answer but i didnt find anything.. now..i dont know if this happens with all modems usb or just Hauwei MT810... i am tired of use the touch pad... did you find a answer for this problem? i have a Mt810 usb modem and a Genius Traveler 700 usb mouse... ok good luck!

---

