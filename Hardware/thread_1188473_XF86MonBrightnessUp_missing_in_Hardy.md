---
title: "XF86MonBrightnessUp missing in Hardy"
date: 2009-06-15
forum: Hardware
---

### Post by duane-tech on 2009-06-15
I have Kubuntu Hardy installed with libx11-data-2:1.1.3-1ubuntu2.
This package contains /usr/share/X11/XKeysymDB.
This file however doesn't have an entry for XF86MonBrightnessUp.

So, if I enter:
$ xmodmap -e 'keycode 101=XF86MonBrightnessUp'

I get:
xmodmap:  commandline:1:  bad keysym name 'XF86MonBrightnessUp' in keysym list
xmodmap:  1 error encountered, aborting.


SunVideoLowerBrightness doesn't work.
How can I get brightness adjustment mapped to a keycode?

---

