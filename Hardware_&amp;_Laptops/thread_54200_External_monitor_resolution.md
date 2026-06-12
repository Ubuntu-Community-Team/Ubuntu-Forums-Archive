---
title: "External monitor resolution"
date: 2005-08-03
forum: Hardware &amp; Laptops
---

### Post by FredTech on 2005-08-03
I need to connect my Dell Latitude X1 to a HP f2304 external LCD-monitor using the resolution 1900x1200, but System -> Preferences -> Screen Resolution only lists resolutions up to 1280x768 (the resolution of the laptop). This results in a poor, blurry image quality on the external monitor.

I have tried editing the xorg.conf file, but there's never any changes in the Resolution drop-down list. Can I somehow "force" the system to run 1900x1200 even though it's not listed as an option? Or is there a better way?

Thanks

---

### Post by TravisNewman on 2005-08-03
You need to get the specs of your monitor and change the Horiz Refresh and Vert Sync settings in xorg.conf, and then add 1900x1200 to the modes at the bottom (under 24 bit, and any other depth you use)

---

