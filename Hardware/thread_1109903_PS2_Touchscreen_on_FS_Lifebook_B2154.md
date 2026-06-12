---
title: "PS/2 Touchscreen on FS Lifebook B2154"
date: 2009-03-29
forum: Hardware
---

### Post by takitaro on 2009-03-29
Hi everybody,
I've just installed [Ubuntu 8.10 + LXDE Special ]("http://streetcross.wordpress.com/2009/01/19/ubuntu810lxde-special/") on an old Fujitsu Siemens Lifebook B2154 with touchscreen that I'm now trying to calibrate.
I've followed [this]("http://forum.ubuntu-fr.org/viewtopic.php?id=177172") in French but still nothing happens when I tap on the crosses that appear on screen during calibration.
The only difference between my situation and the one explained in it is that while 
cat /proc/bus/input/devices
should give

I: Bus=0011 Vendor=0002 Product=0009 Version=0003
N: Name="LBPS/2 Fujitsu Lifebook TouchScreen"
P: Phys=isa0060/serio1/input0
S: Sysfs=/class/input/input4
U: Uniq=
H: Handlers=mouse3 event4 
B: EV=b
B: KEY=400 0 70000 0 0 0 0 0 0 0 0
B: ABS=3

on my b2154 it gives

I: Bus=0011 Vendor=0002 Product=0009 Version=0003
N: Name="LBPS/2 Fujitsu Lifebook TouchScreen"
P: Phys=isa0060/serio1/input0
S: Sysfs=/devices/platform/i8042/serio1/input/input7
U: Uniq=
H: Handlers=mouse2 event7
B: EV=b
B: KEY=400 0 70000 0 0 0 0 0 0 0 0
B: ABS=3

with a big difference in the sysfs line.

I've then run

sudo ./calibrator /dev/input/event7

and calibration starts, but nothing happens touching the screen with the stylus.

Can this difference in the sysfs line be the reason why I get no response when tapping on screen during calibration? Of course tapping and dragging in Ubuntu work but are not calibrated.

I'm a newbie, so any help is more than appreciated...

takitaro (italy)

---

