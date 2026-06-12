---
title: "How to force DPI with Nvidia-prime ? xorg changes get overwritten when GPU switching"
date: 2016-05-31
forum: Hardware
---

### Post by interzoneuk on 2016-05-31
Hi.

I'm using nvidia-prime, when using nvidia (discrete) and I plug in a HDMI monitor the DPI automatically changes to 75x75 rather than 102x102.

I can force the DPI by adding 

    Option     "DPI" "102 x 102"

To the nvidia "Device" section of xorg.conf, this works fine until I switch GPU then my changes get overwritten automatically...

How can I ensure that my DPI line gets re-added when I use nvidia-prime to switch GPU ?

---

