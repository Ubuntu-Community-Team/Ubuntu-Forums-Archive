---
title: "Nvidia Dual Monitor Dell Laptop"
date: 2017-03-07
forum: Hardware
---

### Post by it.edsonjunior on 2017-03-07
Hi folks. I know that is an old question to Ubuntu community.
So, let's go.

What I did? I installed an Ubuntu Mate 16.04.2 alongside with Windows. Each OS has enough space to work. I did this way just because of the nvidia card.
I work with a second screen (Dell too).
At this time the nvidia driver installation works fine as you can see below:
[ATTACH=CONFIG]274026[/ATTACH]
[ATTACH=CONFIG]274027[/ATTACH]
[ATTACH=CONFIG]274028[/ATTACH]
So, the second screen does not work. And the nvidia card does not recognize my built in screen even if I press the "detect displays" button.
[ATTACH=CONFIG]274029[/ATTACH]

If I save to X Configuration File, the OS does not recognize the resolution anymore because I already tried it and only works in 640x480.
My xorg.conf file is below:

> cat /etc/X11/xorg.confSection "ServerLayout"
    Identifier "layout"
    Screen 0 "nvidia"
    Inactive "intel"
EndSection


Section "Device"
    Identifier "intel"
    Driver "modesetting"
    BusID "PCI:0@0:2:0"
    Option "AccelMethod" "None"
EndSection


Section "Screen"
    Identifier "intel"
    Device "intel"
EndSection


Section "Device"
    Identifier "nvidia"
    Driver "nvidia"
    BusID "PCI:8@0:0:0"
    Option "ConstrainCursor" "off"
EndSection


Section "Screen"
    Identifier "nvidia"
    Device "nvidia"
    Option "AllowEmptyInitialConfiguration" "on"
    Option "IgnoreDisplayDevices" "CRT"
EndSection

The second screen only appears if I connect the VGA and reboot the OS but only works in 1024x768 and this is not good for me.

I appreciate the help.

Thanks in advance.

---

