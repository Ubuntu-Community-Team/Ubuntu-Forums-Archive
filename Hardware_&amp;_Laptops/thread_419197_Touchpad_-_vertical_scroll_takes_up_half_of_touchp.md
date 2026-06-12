---
title: "Touchpad - vertical scroll takes up half of touchpad in feisty"
date: 2007-04-22
forum: Hardware &amp; Laptops
---

### Post by bond00 on 2007-04-22
I was able to configure my Synaptic Touchpad in feisty, but after installing both qsynaptics and gsynaptics I don't see the setting to change how close to the right edge of the touchpad to use vertical scrolling. Vertical scrolling is being used for close to the right half of my touchpad. It's really annoying and makes the touchpad very difficult to use. I also tried adding Option 		"RightEdge" "1250", but whenever that line is enabled, the touchpad doesn't work at all. 

Are there any ideas out there how I can fix the touchpad to only use the last 1/4 inch on the right side of the touchpad as vertical scroll? Thanks for the help!!

---

### Post by bond00 on 2007-04-24
no ideas on how to fix this? There has to be a fix. Anyone?

---

### Post by strabes on 2007-04-24
It's a pretty easy fix. Go here: [http://gentoo-wiki.com/HARDWARE_Synaptics_Touchpad](http://gentoo-wiki.com/HARDWARE_Synaptics_Touchpad)

I believe the option you'll have to configure is "RightEdge." You can type "synclient -l" to find out what it is on your system right now. If I remember correctly you'll have to make it bigger to move the right edge to the right.

---

