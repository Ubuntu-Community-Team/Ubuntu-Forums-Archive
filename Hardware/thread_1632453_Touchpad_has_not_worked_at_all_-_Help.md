---
title: "Touchpad has not worked at all - Help"
date: 2010-11-28
forum: Hardware
---

### Post by diwakarss on 2010-11-28
Hello Everyone,

I'm new to Linux and Ubuntu. I'm currently using Lenovo G530 Laptop dual booting Win 7 and Ubuntu.

Maverick

1. Downloaded Ubuntu 10.10 - Synaptic Touchpad did not work in Live CD mode
2. Installed Ubuntu using a USB mouse, after installation, updated to latest using update manager
3. Touchpad did not work still, tried searching for solution tried some of them
4. I had once used Ubuntu 10.04 on a different laptop before, so i decided to go back to Lucid

Lucid

1. Same problem touchpad never worked in the Live CD
2. Installed Lucid, ran all updates
3. No change in touchpad 

I have tried the following from [https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-synaptics/+bug/549727?comments=all](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-synaptics/+bug/549727?comments=all)

Post #34
sudo modprobe -r psmouse
sudo modprobe psmouse proto=imps

post #40

rm -rf /home/ben/.gconf/desktop/gnome/peripherals/touchpad

post #42

sudo gedit /home/diwa/.gconf/desktop/gnome/peripherals/touchpad/%gconf.xml

the configuration file already has the value as true
<entry name="touchpad_enabled" mtime="1290922794" type="bool" value="true"/>

post #71

switch to false and ture does  not work either
gconftool -s /desktop/gnome/peripherals/touchpad/touchpad_enabled -t boolean false
gconftool -s /desktop/gnome/peripherals/touchpad/touchpad_enabled -t boolean true

None of these seem to work.

trying dmesg | egrep -i 'input|touch|track' gives the following

[   12.662710] Synaptics Touchpad, model: 1, fw: 6.5, id: 0x25c0b1, caps: 0xa04711/0xa00000
[   12.714170] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio4/input/input11
[   13.573991] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 1
[   14.685009] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 1
[   14.687731] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 1
[   14.690456] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 1
[   14.693180] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 1
[   14.695905] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 1

don't know what this means.

 Please let me know if there is any solution for this. Having no touchpad is very hard.

---

### Post by diwakarss on 2010-11-28
Update: Touchpad working now after installing gpointing-device-settings. 

After restarting I have to disable and enable the trackpad (Fn+F8 on my laptop) everytime to get the touchpad working. It also stops working after suspending the system and I have to restart. Anyway the basic functionality works, I'm much happier:)

---

