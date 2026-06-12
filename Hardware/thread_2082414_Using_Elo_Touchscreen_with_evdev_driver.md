---
title: "Using Elo Touchscreen with evdev driver"
date: 2012-11-09
forum: Hardware
---

### Post by jvdl on 2012-11-09
Hi all,

I am trying to setup Ubuntu (10.04) with a 3 screen configuration. And all 3 are touchscreens (Elo TouchSystem 2700). I am using the evdev touchscreen driver. But so far I can't get it to work properly.

Getting to use the evdev driver for the screens is no problem. It will kick in automatically and allows me to use the touch interfaces. The only problem is that the cursor will not jump to the screen which I touch. Instead it will show and move on the the screen where it was before. Which is off course not the desired situation.

I have been experimenting with separate x-screens, xinerama, calibration etc but nothing seems to fix this. The problem seems to be the fact that there is no option to tell the driver what x-screen should be used.

Is there a way to solve this? Or maybe some workaround? Or is the driver just too limited?

---

