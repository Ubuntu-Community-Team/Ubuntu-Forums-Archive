---
title: "Radeon R9 290 Display Issue w/Trusty"
date: 2014-10-25
forum: Hardware
---

### Post by aimless2 on 2014-10-25
Radeon driver in use.  Connected to 70 inch LED via HDMI.  Issue is that top, bottom, left, and right are all off screen a little.  

I dual boot with Windows 8 and everything displays properly.  So I know it isn't a defect with graphics card.

Additionally, the UEFI and boot print are all the same way.

Once in to Ubuntu I can change resolution to 1360x768(16:9) and get my edges back but everything else like apps all too big.

Any better way to control the scaling?  Are there driver settings perhaps?

---

### Post by Vladlenin5000 on 2014-10-26
You probably need proprietary drivers to achieve the maximum resolution. Radeon is the open source driver.

---

### Post by aimless2 on 2014-10-26
Ended up getting it to work by just changing a "view mode" setting to "dot by dot" which presumably matches pixels 1:1 with the graphics card output.  That fixed it.  Actually with 1360x768 selected it made the resolution really small, but once I went back to 1920x1080 it was all good and everything fit normal.  Even the boot print and UEFI stuff fits on the screen perfectly.

Thanks

EDIT: The "view mode" that I changed was on the TV.

---

### Post by Vladlenin5000 on 2014-10-26
I'm glad it's working now.
Please use the thread tools to mark this one as solved so others can benefit.

---

