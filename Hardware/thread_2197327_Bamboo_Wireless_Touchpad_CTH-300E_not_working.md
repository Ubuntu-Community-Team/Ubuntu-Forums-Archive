---
title: "Bamboo Wireless Touchpad CTH-300E not working"
date: 2014-01-03
forum: Hardware
---

### Post by v-skowronski86 on 2014-01-03
Hello!

This is my first post here and i hope someone can help me. I bought a new Bamboo Touchpad and it is working fine on Windows. As i am using Ubuntu for working matters, i would like to get it running on Ubuntu 13.10. Unfortunately Ubuntu is not recognizing any movement i do on the Tablet. It seems that the tablet must be noticed by the OS due to this: 

dmesg | grep [Ww]acom[    2.518472] usb 7-5: Manufacturer: Wacom Co.,Ltd.
[  190.249657] usb 7-5: Manufacturer: Wacom Co.,Ltd.
[  920.322956] usbcore: registered new interface driver wacom


When i enter
[FONT=Ubuntu Mono]lsmod | grep [Ww]acom it shows me this:
[/FONT] lsmod | grep [Ww]acom
wacom                  62341  0 

Maybe anyone has this tablet and can help me. 

Regards

---

### Post by jsalisbury2 on 2014-01-09
The driver is not in the linux kernel for that device id.  See Launchpad bug 1265714:


[http://pad.lv/1265714](http://pad.lv/1265714)

---

### Post by LillyDragon on 2014-01-10
You may have to consider compiling the latest Wacom drivers to get it to run, if it is a recent device that older kernel drivers don't support. I don't think the newest drivers will be included out of the box until 14.04, although I think that's for the Mint flavor of Ubuntu.

Here is a tutorial on getting the newest drivers compiled and working on your system. I am using these myself for my Pen and Touch CTH-480, and it works like a dream for that model.

[http://forums.linuxmint.com/viewtopic.php?f=42&t=110408](http://forums.linuxmint.com/viewtopic.php?f=42&t=110408)

---

