---
title: "external monitor not correctly detected by xrandr"
date: 2008-11-11
forum: Hardware
---

### Post by felixnine on 2008-11-11
i have a dell 22" lcd attached to my laptop's vga port. if i start x or unsuspend my laptop with it connected, there are no problems. but if i connect it after my laptop has been reconfigured to only use the laptop screen, xrandr doesn't detect the correct available resolutions. i run it in 1680x1050, but all i get from xrandr is this:

```

VGA-0 connected 1280x1024+0+0 (normal left inverted right x axis y axis) 473mm x 296mm
   1280x1024      75.0     59.9
   1152x864       74.8
   1024x768       75.1     60.0
   800x600        75.0     60.3
   640x480        75.0     60.0
   720x400        70.1
```

if i restart x, all the modes show up. is there a way to fix this?

---

