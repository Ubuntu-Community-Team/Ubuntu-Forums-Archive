---
title: "Dual screen faulty in notebook with intel gma 965, ubuntu 9.04 x86"
date: 2009-05-01
forum: Hardware
---

### Post by mentat5kyu on 2009-05-01
Hi, I just made a fresh install of ubuntu 9.04.

Everything worked flawlessly except for the following issue:
Both screens work fine, but the exterior one, witch should be at 1920x1080 only gets to 1360x768. 

In win xp it works fine.

Is this a driver limitation issue or a configuration issue?

---

### Post by mentat5kyu on 2009-05-01
sudo dpkg-reconfigure -phigh xserver-xorg

this solved the problem. After running this and loging out, the gnome Screen Resolution tool showed the missing resolutions.

---

### Post by newenglandcs on 2009-06-03
Just wanted to note that this corrected a problem I was having with an Dell Latitude e6500 laptop.  A 19" monitor (4:3) was connected to the laptop, via docking station, which forced the resolution to be 1024x768 on both screens.  The highest resolution that was listed was 1024x768.

after using this command:

sudo dpkg-reconfigure -phigh xserver-xorg

(confirming, then restarting)

I was able to see the higher resolutions.  On a side note, when dragging a window from the laptop to the monitor, the window would get stuck halfway through.  To fix this, I set the refresh rate on both screens so that they are the same (60 Hz).  This corrected the problem.

Thanks for the fix!

---

