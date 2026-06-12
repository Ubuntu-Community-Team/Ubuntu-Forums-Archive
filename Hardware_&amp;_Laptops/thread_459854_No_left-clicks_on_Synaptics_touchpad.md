---
title: "No left-clicks on Synaptics touchpad"
date: 2007-05-31
forum: Hardware &amp; Laptops
---

### Post by kenstad on 2007-05-31
After an automatic update (i think it was a kernel update) by the update manager in 7.04 Feisty Fawn my synaptics touchpad no longer recognises left-clicks - neither tap nor button. Other mouse events are registered - movement, scrolls and right-clicks, but not left-clicks. What is more the system seems to register the touchpad as an "ImPS/2 Logitech Wheel Mouse" rather than a Synaptics touchpad, which it is. This is the relevant output from cat /proc/bus/input/devices

I: Bus=0011 Vendor=0002 Product=0005 Version=0063
N: Name="ImPS/2 Logitech Wheel Mouse"
P: Phys=isa0060/serio2/input0
S: Sysfs=/class/input/input4
H: Handlers=mouse2 event4 ts2
B: EV=7
B: KEY=70000 0 0 0 0 0 0 0 0
B: REL=103

'dmesg | grep Logitech' confirms this:
[ 17.176000] input: ImPS/2 Logitech Wheel Mouse as /class/input/input4

Here is mouse-related info in xorg.conf

Section "InputDevice"
 Identifier "Configured Mouse"
 Driver "mouse"
 Option "CorePointer"
 Option "Device" "/dev/input/mice"
 Option "Protocol" "ExplorerPS/2"
 Option "ZAxisMapping" "4 5"
 Option "Emulate3Buttons" "true"
EndSection

Section "InputDevice"
 Identifier "Synaptics Touchpad"
 Driver "synaptics"
 Option "SendCoreEvents" "true"
 Option "Device" "/dev/psaux"
 Option "Protocol" "auto-dev"
 Option "HorizScrollDelta" "0"
EndSection

There is also a 'Load "synaptics"' entry under the "Module" section of xorg.conf, but lsmod shows no synaptics driver. (I don't know if it should, though...)

I have seen vaguely similar problems in this forum, for instance this:
[http://ubuntuforums.org/showthread.php?t=417492](http://ubuntuforums.org/showthread.php?t=417492)

Has anyone got any idea of what is going on here?

K.

---

### Post by jbernardo on 2007-05-31
Check this bug report - [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/112915](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/112915)
The problem seems to be with the kernel psmouse driver, which isn't identifying our touchpads as such.
Cat you try installing tpconfig and post the output of "tpconfig -i" here? I'm betting it will show something like what I and JohnRader get.

---

### Post by kenstad on 2007-05-31
You're quite right! the tpconfig -i identifies my touchpad as a synaptics touchpad:

Found Synaptics Touchpad.
Firmware: 8.96 (multiple-byte mode).
Sensor type: unknown (0).
Geometry: rectangular/landscape/up.
Packets: absolute, 80 packets per second.
Corner taps disabled;           no tap gestures.
Edge motion: none.
Z threshold: 6 of 7.
2 button mode; corner tap is right button click.

 I have posted my problem as a bug, too (since i didn't find the bug report you linked to). I guess we'll have to sit back and wait for the developers to get on it, then. It is very annoying, but USB mice still work correctly.

---

