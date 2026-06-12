---
title: "Silead Touchscreen"
date: 2019-07-29
forum: Hardware
---

### Post by pseudotheist2 on 2019-07-29
Hello, looking for help trying to get touchscreen working on a cheap 2-in-1.  It's got a Silead touchscreen, for which I downloaded the driver off of github.
With that I got the screen to register touch, but not in the proper locations.  In general, the input seemed to map to the top left, as though the output field only half the screen.  xinput_calibrator didn't seem to fix the issue so I dug a bit further.  Eventually i found the command to directly manipulate the translation matrix (input --set-prop).  At this point I discovered that the Y axis was pretty straightforward, but the X axis appears to be banded somehow.  I can get some columns to map pretty closely, but they have columns in-between (maybe an inch width per column) which map wildly differently.

Is anyone familiar with this sort of behavior, or has some idea if there's some other setting which might be adjustable to address this?

---

