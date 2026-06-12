---
title: "Toucpad problems"
date: 2007-12-15
forum: Hardware &amp; Laptops
---

### Post by linuxonbute on 2007-12-15
I have a Zepto Znote 3215W laptop.

It does not recognize the touchpad correctly.

```

cat /proc/bus/input/devices

I: Bus=0011 Vendor=0002 Product=0005 Version=0063
N: Name="ImPS/2 Logitech Wheel Mouse"
P: Phys=isa0060/serio1/input0
S: Sysfs=/class/input/input2
U: Uniq=
H: Handlers=mouse1 event2 
B: EV=7
B: KEY=70000 0 0 0 0 0 0 0 0
B: REL=103

```

After looking at the Windows Driver package i found this readme;
```


How to setup Fast Initialization:
1) Double click "Mouse" icon stored in task tray.
2) Select "Hardware" tab in "Mouse Properties".
3) Click "Properties" button.
4) Select "Advanced Settings" tab in "Elantech TouchPad Properties".
5) Click the check box next to "Fast Initialization" (Check the box).
6) When asked to restart in "System Settings Change" click the "Yes" button and restart the system.


```

After searching for information i have found that there is a patch for kernel 2.6.23.1
which is for the Elantech TouchPad 

As I am running Gutsy with kernel 2.6.22-14-generic I cannot use the patch.

I don't know enough to decide if I can get it to work with this kernel or not.

I have tried downloading the vanilla 2.6.23.1 source, patching it and compiling it.

This worked up to a point but the left and right mouse buttons no longer work and the kernel does not know anything about my wireless card Intel Pro 4965ABG whereas the original does.
I am guessing that the driver for this is an Ububtu added patch.

Is there any way I can sort this out?
Can I get a Ubuntu version of 2.6.23.1 to patch or is there some other way to solve the problem?

---

