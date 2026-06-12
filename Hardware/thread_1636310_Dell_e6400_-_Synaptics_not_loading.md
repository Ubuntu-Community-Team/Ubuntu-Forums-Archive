---
title: "Dell e6400 - Synaptics not loading"
date: 2010-12-02
forum: Hardware
---

### Post by gxgung on 2010-12-02
I have a dell e6400 laptop and I have problems with the touchpad driver. I can always use my touchpad, but the touchpad configuration utility loads only at the first boot after reinstalling xserver-xorg-input-synaptics. I would prefer to find another method except always reinstalling and rebooting.

All I want to do is to disable the touchpad tap-to-click. Preferably always, not just while typing.

I tried to do this via terminal.

[I]~: syndaemon -d -i 5
Unable to find a synaptics device.
[/I]
but... look at this:
[I]~: cat /proc/bus/input/devices
...
I: Bus=0011 Vendor=0002 Product=0001 Version=6222
N: Name="PS/2 ALPS DualPoint TouchPad"
P: Phys=isa0060/serio1/input0
S: Sysfs=/devices/platform/i8042/serio1/input/input5
U: Uniq=
H: Handlers=mouse0 event5 
B: EV=7
B: KEY=70000 0 0 0 0 0 0 0 0
B: REL=3
[/I]

---

### Post by gxgung on 2010-12-04
bump

---

### Post by Aitaix on 2010-12-07
[http://ubuntuforums.org/showthread.php?t=1602047](http://ubuntuforums.org/showthread.php?t=1602047)

got the same issue. wish I had an an answer for you.

---

