---
title: "Ubuntu on Gigabyte T1005P/M netbook/tablet"
date: 2011-02-16
forum: Hardware
---

### Post by Newbunty1 on 2011-02-16
[FONT=Courier 10 Pitch][SIZE=2]I am interested in buying Gigabyte netbook/tablet PC either model T1005P with resistive multi-touch Panel or T1005M with capacitive multi-touch panel. Does anyone know which one works better with Ubuntu Netbook Edition 10.10? Any installation problems, any tips, what works and what doesn't?[/SIZE][/FONT]
 

 [FONT=Courier 10 Pitch][SIZE=2]Thanks !!!   :)
[/SIZE][/FONT]

---

### Post by Newbunty1 on 2011-03-13
Did anyone try Ubuntu on T1005P with resistive screen?

---

### Post by mariusko on 2011-03-18
I would recommend the netbook. In Maverick, the touchscreen is probably possible to get working with:

[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-evdev/+bug/604097](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-evdev/+bug/604097)

In current Natty, touchscreen works fine, but touchpad does not work (works in Maverick):

[https://bugs.launchpad.net/ubuntu/+bug/737482](https://bugs.launchpad.net/ubuntu/+bug/737482)

I think those issues are easy to solve and many of them are general for all netbooks/tablets.

And why don't you want a capacitive screen? I have one and is satisfied  with the precision, it can even be better probably with styluses for  those screen (as for iPad). There also is work underway for support for  gestures/multi touch as on the Android/iPhone.

---

### Post by mariusko on 2011-03-18
See here:

[https://help.ubuntu.com/community/GigabyteT1005](https://help.ubuntu.com/community/GigabyteT1005)

Ah, I forgot (as the touchscreen worked) the workaround for the touchpad there is why it probably isn't working when I boot Natty.

---

