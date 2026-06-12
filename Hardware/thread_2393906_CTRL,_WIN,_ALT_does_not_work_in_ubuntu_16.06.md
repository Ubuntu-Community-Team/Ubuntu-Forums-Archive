---
title: "CTRL, WIN, ALT does not work in ubuntu 16.06"
date: 2018-06-09
forum: Hardware
---

### Post by maxleo.junior4 on 2018-06-09
Hi community is my first thread 'cause I have problem with my external usb keyboard.
Basically I'm running ubuntu 16.06 in asus K555LB i7, so CTRL, WIN and ALT does not work properly being mapped as SHIFT is totally weird 'cause native laptop's keyboard works fine and also external usb keyboard works fine in windows.

**here are some useful commands.**

```
ubuntu-drivers devices  
== /sys/devices/pci0000:00/0000:00:1c.4/0000:04:00.0 ==
modalias : pci:v000010DEd00001347sv00001043sd00001A6Dbc03sc02i00
vendor   : NVIDIA Corporation
model    : GM108M [GeForce 940M]
driver   : xserver-xorg-video-nouveau - distro free builtin
driver   : nvidia-384 - distro non-free recommended


```

```
sudo lsusb
[sudo] password for max: 
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 004: ID 0bda:0129 Realtek Semiconductor Corp. RTS5129 Card Reader Controller
Bus 001 Device 005: ID 13d3:3423 IMC Networks 
Bus 001 Device 002: ID 04f2:b483 Chicony Electronics Co., Ltd 
Bus 001 Device 008: ID 1c4f:0056 SiGma Micro 
Bus 001 Device 006: ID 045e:00cb Microsoft Corp. Basic Optical Mouse v2.0
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub



```
So let me know if someone has this problem before, I'll really appreciate.
Warm regards.

---

