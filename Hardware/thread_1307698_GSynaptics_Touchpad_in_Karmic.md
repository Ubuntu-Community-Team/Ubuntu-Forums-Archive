---
title: "GSynaptics Touchpad in Karmic"
date: 2009-10-31
forum: Hardware
---

### Post by mpcabd on 2009-10-31
Hello all,

I have an Asus U50gv and it has a multi-finger touch pad.
I wanted to make use of the gestures in Ubuntu 9.10, I searched the net and found that I must enable [**SHMConfig**]("https://help.ubuntu.com/community/SynapticsTouchpad#shmconfig").

I tried that but no use.

I found another [**thread**]("http://agoranetbook.kayno.net/2009/10/06/touchpad-configuration-for-ubuntu-9-10-grub-2/") talking about passing i8042.nomux to the kernel on boot time, I did as this blog says but also no use.

Any ideas? :)

---

### Post by asuastrophysics on 2009-11-15
SHM was based on HAL, which is no longer used in Ubuntu 9.10

now ubuntu uses udev. it will probably be a long time before someone gets around to writing a program for touchpad gestures, as they'll have to start from scratch now that ubuntu has a new hardware management engine.

---

