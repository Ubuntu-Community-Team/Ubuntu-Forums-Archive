---
title: "Compiz/Weird X setup issues"
date: 2016-08-09
forum: Hardware
---

### Post by netham45 on 2016-08-09
Hi, I have a complex configuration for my desktop. I have 3 monitors on a GTX970 and 2 on my Intel HD 3000 that's built into my CPU. I spent the better part of a week trying to figure out how to get it to work before almost giving up.

I found out that if I leave the intel card disabled in Xorg something on the nvidia drivers, I think it's in nvidia-prime as everything breaks when I remove it, loads to output to it. It extends the display of my prime monitor (HDMI0-) to be wider and simply copies that extra area over to the intel monitors. Once I use xrandr to disable panning on that monitor all seems to be working great, except for Compiz. Compiz is blanking the two intel cards for reasons unknown.

Here's my Xorg.conf

```

Section "ServerLayout"
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
    BusID "PCI:1@0:0:0"
    Option "ConstrainCursor" "off"
EndSection

Section "Screen"
    Identifier "nvidia"
    Device "nvidia"
    Option "AllowEmptyInitialConfiguration" "on"
    Option "IgnoreDisplayDevices" "CRT"
EndSection


```

And, once X is loaded I'm running this to position the screens. I'm planning on seeing if I can get this to work with nvidia's metamode option, but I haven't gotten there yet. When they come up all except DVI-I-0 have their viewports set to be 0x0xwidthxheight of the framebuffer meaning they all display a portion of HDMI-0's top-left.

```

echo HDMI-0
xrandr --output HDMI-0 --auto --pos 0x0 --panning 3840x2160
echo DVI-D-0
xrandr --output DVI-D-0 --auto --pos 3840x0 --panning 1920x1080+3840+0
echo DVI-I-0
xrandr --output DVI-I-0 --auto --pos 3840x1080 --panning 1920x1080+3840+1080
echo HDMI-1
xrandr --output HDMI-1 --auto --pos 5760x1080
echo HDMI-3
xrandr --output HDMI-3 --auto --pos 7680x1080

```

So, here are my main questions:
1) Why is my nvidia card seemingly outputting to the Intel card's ports on my mobo? I'm getting performance on those screens beyond what that card is capable of. I'm not complaining, I just want to know what's going on.
2) What do I need to do to get Compiz to quit blanking the last two cards?
Edit: I got Compiz to quit mucking with the displays. In the 'general options' section there's an 'auto-detect displays' box. I unchecked that and configured the displays in the list below.
3) Is there a better way to get the nvidia card and the intel card to play together? I can get the nvidia card and the intel card to cooperate as separate screens in my Xorg.conf but enabling xinerama leads to a hard freeze.

---

