---
title: "XRandR Dual screen with ATI Radeon 9600 (RV 350 AQ)"
date: 2009-03-10
forum: Hardware
---

### Post by torbjorn@nextline.no on 2009-03-10
Summary:
xrandr ends up positioning both outputs on the same coordinates, and hence, the outputs are always cloned.

I want to have a Xinerama / MergedFB work-a-like using XRandR.

```

Screen 0: minimum 320 x 200, current 1280 x 1024, maximum 2560 x 1024

```

I have increased the virtual screen size in xorg.conf, but it contains no settings except a Virtual line.

When I start up X, xrandr shows both outputs showing the same area on the virtual screen.

```

torbjorn@torbjorn-desktop:~$ xrandr | grep connected
VGA-0 connected 1280x1024+0+0 (normal left inverted right x axis y axis) 338mm x 270mm
DVI-0 connected 1280x1024+0+0 (normal left inverted right x axis y axis) 338mm x 270mm
S-video disconnected (normal left inverted right x axis y axis)

```

If I try to position my right output using xrandr, both screens get adjusted with an offset, and I end up only seeing the right part of the virtual screen.

```

torbjorn@torbjorn-desktop:~$ xrandr --dryrun --output DVI-0 --right-of VGA-0
screen 0: 2560x1024 675x270 mm  96.33dpi
crtc 0:    1280x1024   60.0 +1280+0 "DVI-0" "VGA-0"

```

The same offset is reported on both outputs.
```

torbjorn@torbjorn-desktop:~$ xrandr | grep connected
VGA-0 connected 1280x1024+1280+0 (normal left inverted right x axis y axis) 338mm x 270mm
DVI-0 connected 1280x1024+1280+0 (normal left inverted right x axis y axis) 338mm x 270mm
S-video disconnected (normal left inverted right x axis y axis)

```

When running like this, seeing only the right part of the virtual screen, I can see KDE seeing the whole virtual screen.
The virtual desktop selector on my taskbar indicates that there is space available to the left, and I can move my mouse in that area.
Alas, I can not configure a output to view that part of the virtual screen.

If I try to configure using --pos, I get pretty much the same results.

Does anyone have any pointers as to what I need to tell xrandr to get the outputs showing different parts of the virtual screen ?

In advance, thank you.

---

