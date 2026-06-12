---
title: "New Elantech Touchpad multi-touch"
date: 2016-08-14
forum: Hardware
---

### Post by daniwaber on 2016-08-14
I'm running ubuntu gnome 16.04.1 on my hp pavilion ab048tx (ci5 5th) having an Elantech touchpad. I've tried various dkms fixes available on the internet (including psmouse-elantech-x551c and psmouse-elantech-v7), but nothing seems to get multi-touch into action. Basic functions work (move, click, tap and right-click). Any idea what to do?

My (partial) output for cat /proc/bus/input/devices is as follows: 

I: Bus=0011 Vendor=0002 Product=0001 Version=0000
N: Name="PS/2 Elantech Touchpad"
P: Phys=isa0060/serio1/input0
S: Sysfs=/devices/platform/i8042/serio1/input/input5
U: Uniq=
H: Handlers=mouse0 event6 
B: PROP=1
B: EV=7
B: KEY=70000 0 0 0 0
B: REL=3

---

