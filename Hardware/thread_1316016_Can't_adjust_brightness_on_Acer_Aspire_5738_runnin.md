---
title: "Can't adjust brightness on Acer Aspire 5738 running Karmic"
date: 2009-11-05
forum: Hardware
---

### Post by nechus on 2009-11-05
Can't adjust brightness on Acer Aspire 5738 running Karmic. The same happened under Jaunty. The screen never seems to reach its full brightness and it flickers.

The notify osd shows a bright bar indicating the screen brightness increasing or decreasing when I use the fn key + the corresponding keys for increasing or reducing the screen brightness, but the screen always stays the same.

I can move the arrow in the brightness applet in the Gnome panel up and down, but nothing happens, either.

I think I'll report a bug.

---

### Post by mrdigerati on 2010-02-15
I too still have the same problem.
Acer Aspire 5738.

Ubuntu 9.10.

possible options I saw were:

a) CompizFusion: Download and enable the Brightness/Contrast etc option. Use it for specific windows (you can make firefox glow alone) or add a class (nautilus) etc.
Keyboard shortcuts like ALT/CTRL/SUPER/SHIFT + Left/Right

b) echo 4 > /sys/devices/virtual/backlight/acpi_video0/brightness
Didn't work yet. I think I need to logout and get back to make changes.
[values from 1-8. 4 is mid range for many laptops]

c) If the above works fine you can make a two scripts.. for gradually decreasing/increasing the backlight value.. using above.

Hey if you get anything// then do post back.

PS: either (b) or System >> Preferences >> Power Management >> "Set display Brightness to" lets you set the brightness (uses the same file). but only When you restart system, the changes show [killing the x-server alone may not  help]

---

### Post by fbobraga on 2010-08-29
fixed here by [http://ubuntuforums.org/showpost.php?p=8411337&postcount=5](http://ubuntuforums.org/showpost.php?p=8411337&postcount=5)

---

