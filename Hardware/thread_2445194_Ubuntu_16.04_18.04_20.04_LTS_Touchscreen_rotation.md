---
title: "Ubuntu 16.04 18.04 20.04 LTS Touchscreen rotation"
date: 2020-06-10
forum: Hardware
---

### Post by djesloc on 2020-06-10
Since Ubuntu 16.04 LTS kernel 4.15:

Touchscreen and display and landscape -> works


1. After executing xrandr -o left  ->  Screens is in portrait mode but touchscreen (ELO touchscreen) stops working.
2. Screen in landscape and touchscreen in portrait (xinput -set-props ....)  -> Touchscreen still works

Every time xrandr commands is executed the touchscreen is not responding, ubuntu needs to restart in landscape mode before the touchscreen works again.

Xinput -> touchscreen is stille detected but not working

We use the same image with different touchscreens, so this issue is not related to the ELO touchscreen.

Info:

/var/log/Xorg.log:

[    45.766] (**) Touch Elo Touch Solutions ^MFB46WHD-EL-A1-10P: Applying InputClass "evdev touchscreen catchall"
[    45.766] (II) Using input driver 'evdev' for 'Touch Elo Touch Solutions ^MFB46WHD-EL-A1-10P'

Can somebody help me to debug this issue, Thanks

---

