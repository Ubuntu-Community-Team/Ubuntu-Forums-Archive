---
title: "Touchpad has &quot;dead&quot; border on Ubuntu 14.04"
date: 2014-09-09
forum: Hardware
---

### Post by morphus2 on 2014-09-09
Hi all,

after the update to ubuntu 14.04 on my Acer Aspire E1 I have a small but annoying "dead" border on the right and on the bottom of my touchpad. xev doesn't show any events when scrolling, touching or stroking this area (about 5mm width).

grep -B 5 mouse /proc/bus/input/devices

echoes 
I: Bus=0011 Vendor=0002 Product=0008 Version=0000
N: Name="ALPS PS/2 Device"
P: Phys=isa0060/serio1/input1
S: Sysfs=/devices/platform/i8042/serio1/input/input7
U: Uniq=
H: Handlers=mouse0 event5 
--
I: Bus=0011 Vendor=0002 Product=0008 Version=0500
N: Name="AlpsPS/2 ALPS GlidePoint"
P: Phys=isa0060/serio1/input0
S: Sysfs=/devices/platform/i8042/serio1/input/input6
U: Uniq=
H: Handlers=mouse1 event6

Any ideas how to fix this?

Thanks in Advance
Morphus

---

