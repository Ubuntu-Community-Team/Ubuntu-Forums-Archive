---
title: "Laptop and Logitech mouse v470 - side scroll"
date: 2010-01-17
forum: Hardware
---

### Post by yobser on 2010-01-17
Hello.

I found old topic which is related to the subject [here]("http://ubuntuforums.org/showthread.php?t=542776").
I tried all explained there. I did not reach successful result.

I got following problems:
**1.** When I set bold into my xorg.conf
Section "InputDevice"
    Identifier     "Synaptics Touchpad"
    Driver         "synaptics"
    Option         "SendCoreEvents" "true"
    Option         "Device" "/dev/psaux"
    Option         "Protocol" "auto-dev"
    Option         "HorizEdgeScroll" "0"
    **Option         "CorePointer"**
after restarting Xserver my mouse pointer does not reflect my actions neither on touchpad nor on mouse

**2.** I cannot understand why I can see events on side scroll buttons here **sudo cat /dev/input/event9** and cannot see them here **sudo cat /dev/input/mouse2**?

As I can understand, I cannot get scroll events in Xserver because somehow mouse's side scroll events are disappeared.

How to fix this problem?

---

### Post by yobser on 2010-01-18
I tried to do it from here [Logitech bluetooth mouse]("http://ubuntuforums.org/archive/index.php/t-542776.html")

I added to /etc/modules
[B]evdev
usbhid[/B]

And to /etc/X11/xorg.conf
[B]Section "InputDevice"
    Identifier  "v470"
    Driver      "evdev"
    Option      "Name" "Logitech Bluetooth Mouse"
    Option      "Dev Name" "Bluetooth Laser Travel Mouse"
    Option      "Dev Phys" "00:1C:26:EB:F5:55"
    Option      "HWHEELRelativeAxisButtons" "7 6"
    Option      "SendCoreEvents" "true"
    Option      "Protocol" "evdev"[/B]
And when I added
[B]    Option      "Protocol" "evdev"
    Option      "Protocol" "evdev"[/B]
and restarted my laptop I got real problem with nvidia.
And I cannot start X with full resolution (only 640x480) until I removed all added lines from /etc/modules and /etc/X11/xorg.conf

Is there any solution how to make them (laptop + bluetooth mouse + sidescroll + nvidia) working together.

---

