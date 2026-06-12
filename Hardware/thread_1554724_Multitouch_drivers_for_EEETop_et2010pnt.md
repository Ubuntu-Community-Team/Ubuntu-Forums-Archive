---
title: "Multitouch drivers for EEETop et2010pnt"
date: 2010-08-17
forum: Hardware
---

### Post by korabio on 2010-08-17
Morning,
i have a Asus EEETOP et2010.
Ubunto 10.04 find all my drivers but don't find the multitouch.
if i execute a lsusb it don't show any touchscreen.
Anyone have a driver for my touchscreen?
thx

---

### Post by mose on 2010-08-23
I have the same model since last week, and everything works like a charm except, indeed, the touchscreen. I'm also very interested by any follow-up on that topic.
cheers

---

### Post by korabio on 2010-08-24
now my touch work.
The only thing that you need is:
nwfermi!

Install the package, restart xorg and the touch work!

[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-evdev/+bug/379313/+attachment/1455604/+files/nwfermi-0.2_i386.deb](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-evdev/+bug/379313/+attachment/1455604/+files/nwfermi-0.2_i386.deb)

---

### Post by mose on 2010-08-26
> **korabio said:**
> now my touch work.
The only thing that you need is:
nwfermi!

Install the package, restart xorg and the touch work!

[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-evdev/+bug/379313/+attachment/1455604/+files/nwfermi-0.2_i386.deb](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-evdev/+bug/379313/+attachment/1455604/+files/nwfermi-0.2_i386.deb)

wow, amazing, it really works with no pain !
thanks amigo

---

