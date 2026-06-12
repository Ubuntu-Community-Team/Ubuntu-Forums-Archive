---
title: "video nuts on Thinkpad i1300"
date: 2005-02-09
forum: Hardware &amp; Laptops
---

### Post by amp_man on 2005-02-09
I just installed ubuntu today on my thinkpad i-series 1300 laptop, and for some reason, the left 1/3 or so of the screen (an external monitor, still waiting for a new tft to come in) is the same repeating image, about an inch in width (@1280x1024 on 15" monitor), and the colors are messed up, each line different. Also, when I try to change to other resolutions (which I will need to do, LCD only supports up to 800*600), the screen goes nuts, it's completely unusable. This display works fine under Windows XP, and also used to work fine with Fedora Core 3 (but that ran too damn slow to do anything with). Oh, probably should mention that the video card is an SM Lynx EM+.

---

### Post by amp_man on 2005-02-10
okay, more info:

the problem, at 1024x768 resolution, is attached

removing all instances of resolutions higher than 800x600 from the /etc/X11/XF86Config-4 gets rid of the problem completely (and setting to 1280x1024 increases it from 3 funky lines to 6), but I would like to have these available, as I will likely be using this later with a projector. changing the resolution to 640x480 using the res switcher util still makes the screen go completely crazy, lines running through everything. any ideas? (I now realize this appears to be an issue with X, not the laptop itself, so if a mod would like to move it, please do)

---

