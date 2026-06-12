---
title: "ubuntu 10.10 and elo touch et1937l"
date: 2011-01-22
forum: Hardware
---

### Post by szpuni on 2011-01-22
Hey all,

I'm trying to use Elo touch screen in my desktop with ubuntu 10.10 and i have weird behavior when i use et1937l sceen.

Calibration seems to look perfect but problem is with X and Y coordinates.
They are upside down.
I found few things in google about it and it didn't work.

I know i can change coordinates by
> Option "swapX" "on"
But when i do this, my screen goes crazy and mouse nearly don't work.

I found this:
```
**Ubuntu 10.10:**

 sudo nano /usr/share/X11/xorg.conf.d/69-evtouch.conf
Section "InputClass"
        Identifier "Elo class"
        MatchProduct "Elo TouchSystems"
        MatchDevicePath "/dev/input/event*"
        Driver          "evtouch"
        Option          "minX"          "530"
        Option          "minY"          "570"
        Option          "maxX"          "3500"
        Option          "maxY"          "3500"
        Option          "swapY"         "1"
EndSection
```

and i want only swap option in there but when i'm adding this file screen goes crazy again and mouse is jumping from one edge to other edge of a screen

I have 1935 screen and when i connect usb cable to same computer everything works well.

Seems to 1937 touchscreen hardware is not supported well in ubuntu.

Anybody have any ideas what i can swap those coordinates to make it working?

---

