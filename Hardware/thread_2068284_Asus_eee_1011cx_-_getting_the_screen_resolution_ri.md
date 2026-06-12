---
title: "Asus eee 1011cx - getting the screen resolution right"
date: 2012-10-08
forum: Hardware
---

### Post by troymius on 2012-10-08
Recently I bought Asus eee 1011cx. It is a nice little netbook without a fan which I really like - it is very quiet and has a good battery life. Better yet, it can be purchased without Windows which is exactly what I did.

Alas Xubuntu 12.04 would not set the screen resolution right out of the box. After some trial and error, this is what worked:

(0) Install Xubuntu.

(1) Install all system updates using update manager, then reboot. Repeat step (1) untill there are no updates available.

(2) Run this command in terminal:
[COLOR=Blue]sudo apt-get install cedarview-graphics-drivers[/COLOR]
After the command does its thing, do not reboot yet.

(3) Run this command in terminal:
[COLOR=Blue]sudo apt-get install  gdm [/COLOR]
During the installation of gdm, choose gdm as default (it will ask you.)

(4) Reboot.

Your Xubuntu should wake up in its full glory and with the right screen resolution. I hope this saves time to others.

---

### Post by troymius on 2012-10-13
Update: after the drivers were installed the screen resolution is fine but video playback is not very smooth (flash). Strangely and luckily, when I installed Fedora 17 (XFCE spin ofcourse) everything works ok out of box.

---

### Post by troymius on 2012-10-23
One more update: Xubuntu 12.10 uses kernel that should be supporting intel cedar trail but neither the live CD or installation succeeded to start X on the Asus 1011cx (it says "no screen found"). Strangely, if I switched to another run-level then startx would work fine. 

Reverting back to Fedora 17 and I guess staying there for some time. It probably does not use the graphics card capabilities but youtube plays ok and that's about all I need.

One more experience: the laptop's bus is quite slow; do not bother with an SSD (tested). If there is a desire I can post pictures how take the thing apart but again I would not do it: an SSD won't make it much faster and the 2Gb RAM is soldered in...

Still, it is a nice little laptop which is veeeery quiet (no fan) and good battery life (~6-7hrs). Thanks to Asus for the no-windows purchase option. It would be even better if intel supported this platform with an open source driver.

---

