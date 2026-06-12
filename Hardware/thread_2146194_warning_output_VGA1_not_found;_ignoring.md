---
title: "warning: output VGA1 not found; ignoring"
date: 2013-05-17
forum: Hardware
---

### Post by sirriffsalot on 2013-05-17
Hey all!The title command error had a simple fix, so I just thought I'd share it if anyone's having the same issue.I run a laptop with the lid closed, connecting it to a 1920 x 1200 Dell screen. But after an update today (see "written date") my xrandr command to turn off the laptop screen and send the screen output to another one with greater resolution gave me the title error message. I suppose the lowlatency kernel update had something to do with it (I use Ubuntu Studio 12.04). A simple copy-paste and edit to the line```
xrandr --output LVDS1 --off --output VGA1 --mode 1920x1200
```that has VGA2 instead VGA1 fixed the issue for me (I can't be bothered to check which of "1" and "2" is currently in use. I hope this helped anyone with similar issues (even the most obvious command error lines can be frustrating! :- )--> Riffsalot

---

