---
title: "USB keybord does not work"
date: 2021-08-24
forum: Hardware
---

### Post by verity3108 on 2021-08-24
[COLOR=#000000]Running server 20.04 LTS, I can not get any USB devices to work. First my keyboard does not work and I can not see a USB flash drive.[/COLOR]

[COLOR=#000000]The keyboard is good, tested it on another system. I can get to the systems BIOS with the same keyboard, and I can boot into another distro with a USB drive and the keyboard works.[/COLOR]

[COLOR=#000000]I plug in a USB drive an tail dmesg, and don't see anything related to the USB drive.[/COLOR]

---

### Post by T.J. on 2021-08-25
Hi Verity!

Did you make sure that legacy USB support is turned on in your BIOS firmware?  Another possible solution is seeing if your computer maker provides a firmware update.

I'm afraid that not every USB device is of the same quality as another.  Even Windows can have significant issues with USB devices if the system firmware does not iterate devices properly.

---

