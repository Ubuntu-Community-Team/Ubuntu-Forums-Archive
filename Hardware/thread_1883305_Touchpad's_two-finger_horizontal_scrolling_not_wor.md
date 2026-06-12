---
title: "Touchpad's two-finger horizontal scrolling not working"
date: 2011-11-18
forum: Hardware
---

### Post by brAzzi64 on 2011-11-18
Hey!

I'm running Ubuntu 11.10 in my HP notebook and the horizontal (two-finger) scrolling  is not working.

The checkbox in Mouse and Touchpad -> Touchpad -> Enable horizontal scrolling is checked. The selected mode is Two-finger.

Wen I run xev, I do get events for buttons 4 and 5 when I scroll vertically, but nothing comes up when I do an horizontal scrolling.

Info about my touchpad:

```

$ xinput list | grep ouch
&#9116;   &#8627; SynPS/2 Synaptics TouchPad                  id=13    [slave  pointer  (2)]

$ cat /proc/bus/input/devices
(...)
I: Bus=0011 Vendor=0002 Product=0007 Version=01b1
N: Name="SynPS/2 Synaptics TouchPad"
P: Phys=isa0060/serio4/input0
S: Sysfs=/devices/platform/i8042/serio4/input/input13
U: Uniq=
H: Handlers=mouse1 event13 
B: PROP=d
B: EV=b
B: KEY=6420 10000 0 0 0 0
B: ABS=260800011000003

```I tried temporarily modifying /usr/share/X11/xorg.conf.d/50-synaptics.conf adding the line:

        Option "HorizTwoFingerScroll" "true"

But I didn't have any luck either.

Any ideas? Thanks a lot!

Bruno

---

