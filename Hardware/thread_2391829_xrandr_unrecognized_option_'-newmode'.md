---
title: "xrandr: unrecognized option '-newmode'"
date: 2018-05-13
forum: Hardware
---

### Post by donnyjenkins on 2018-05-13
I've been trying to set the resolution for one of my monitors at startup. I've tried adding it to .xprofile and tried running it as a script. When I manually enter in the command in Terminal it puts my display in the correct resolution. When I put it either in a script or .xprofile it gives me an error message on logging in:
[CENTER][I]
xrandr: unrecognized option -'newmode'
Try 'xrandr --help' for more information
xrandr: cannot find mode "1280x1024_60"

As a result the session will not be configured correctly.
You should fix the problem as soon as feasible. [/I]
[/CENTER]
 

 I'm not sure how to make it persistent. 

```
xrandr --newmode "1280x1024_60.00"  109.00  1280 1368 1496 1712  1024 1027 1034 1063 -hsync +vsync
xrandr --addmode VGA-0 1280x1024_60.00
xrandr --output VGA-0 --mode 1280x1024_60.00
```

---

