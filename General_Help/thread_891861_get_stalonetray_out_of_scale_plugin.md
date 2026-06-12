---
title: "get stalonetray out of scale plugin"
date: 2008-08-16
forum: General Help
---

### Post by Sam Lars on 2008-08-16
I finally found the option to keep stalonetray from minimizing (and since it skips the task bar, disappearing), but how can I get it to not be a part of the scale plugin?  When I use that, I usually don't want to find my tray... I go to the desktop for that.
Here's my .stalonetrayrc


geometry 104x48-4-4
skip_taskbar true
sticky true
fuzzy_edges 3
tint_level 10
tint_color white
window_type dock
grow_gravity W
icon_gravity SE
ignore_icon_resize TRUE
respect_icon_hints false
max_height 48
icon_size 24
transparent
window_layer bottom

---

### Post by etherealpanda on 2008-09-27
You can fix this by blacklisting stalonetray in the compiz scale configuration.

Open up compizconfig-settings-manager and click the scale settings. In the "Scale Windows" text input on the General tab put the following text:

(Toolbar | Utility | Dialog | Normal | Unknown) & !(name=stalonetray)

This should stop the stalonetray window from scaling.

---

### Post by Sam Lars on 2008-09-27
Thanks for replying!  I just didn't know what to put in to target stalonetray, but I guess it wouldn't have been hard to figure out.

---

