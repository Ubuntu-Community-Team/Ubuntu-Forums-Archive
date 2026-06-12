---
title: "fullscreen/windowed"
date: 2008-10-14
forum: General Help
---

### Post by LordPi on 2008-10-14
Hi all. I have an application(sauerbraten) that is supposed to be fullscreen, but occasionally goes to a window. I wonder if that is due to a key combination. I also wonder if there's a way to restore desktop resolution without a reboot. Is there a way to restore the application to fullscreen with another keypress?

---

### Post by Sam on 2008-10-14
System / Preferences / Screen Resolution.


But if a fullscreen application crashed or quited the fullscreen mode "uncleanly", it may not work. In this case use one of the following methods:

Press Ctrl+Alt then "+" or "-" from the numeric keypad (all together) to switch between all the available resolutions.

Or from a terminal:```
xrandr -s [COLOR="DimGray"]SIZE_X[/COLOR]x[COLOR="DimGray"]SIZE_Y[/COLOR]
# example: xrandr -s 1024x768
```
(replace SIZE_X and SIZE_Y with the desired resolution)

Find out the list of available resolutions by typing:```
xrandr
```

---

### Post by jerome1232 on 2008-10-14
I have noticed this happening to me with zsnes when compiz is on, I never recall sauerbraten (spell? lol) ever doing that to me.

It's odd I love compiz for all the extra wm actions it gives me (I can fullscreen pSX which has no other way to fullscreen it) yet other programs just won't behave well with compiz.

---

