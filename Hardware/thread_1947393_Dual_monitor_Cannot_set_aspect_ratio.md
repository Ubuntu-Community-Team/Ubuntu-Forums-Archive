---
title: "Dual monitor: Cannot set aspect ratio"
date: 2012-03-26
forum: Hardware
---

### Post by bigred1 on 2012-03-26
Using Ubuntu 11.10

I have a monitor connected to my laptop. Both are widescreen. I'd like to have the same picture on both screens. However, the laptop screen has black stripes on left and right -- in other words, it is at a 4:3 ratio. When I try to set resolution at 16:9, with "mirror" selected,  I get an error popup with dozens of lines, each saying it was trying a mode, as below.

How can I get both screens to show 16:9?

```

The selected configuration for displays could not be applied

Could not assign CRTCs to outputs:
Trying modes for CRTC64
CRTC 64: trying mode 1366x768@60Hz with...
```

---

### Post by Mark Phelps on 2012-03-26
In my experience, using "mirror" setting works like this:
1) Ubuntu displays the wallpaper on the screen with the higher resolution as well as can be expected.  If the wallpaper is the same resolution as the screen, it will fit well.
2) Ubuntu then "crops" the same wallpaper to make it fit on the screen with the smaller resolution.  No options are available to decide what to "crop".

---

### Post by bigred1 on 2012-03-26
Mark, thanks. I'm not interested in the wallpaper but rather in the entire desktop.  And the aspect ratio  of the two screens is the same, so there is no reason that the laptop screen should be reduced to 4:3 with black strips on the side while the  main screen shows in full.

---

