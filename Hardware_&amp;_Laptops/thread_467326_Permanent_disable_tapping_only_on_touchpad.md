---
title: "Permanent disable tapping only on touchpad"
date: 2007-06-07
forum: Hardware &amp; Laptops
---

### Post by chemisus on 2007-06-07
is there a way to completely disable the tapping on a touchpad, without disable scrolling or mouse movement? ive always hated the tapping on a touchpad, and in windows i was able to disable it without disabling scrolling or cursor movement.

i just hate that everytime i try to move the mouse, i end up highlighting everything. the only choices ive found so far are to either A) completely disable the touchpad, or B) disables tapping for supplied x seconds after typing. 

ive tried option (B) with: sudo syndaemon -d -i 999999999 -t, but it still disables scrolling.

any suggestions?

---

### Post by Bachstelze on 2007-06-07
If you're in KDE, you can install ksynaptics, which will let you disable only tapping. I don't know if there's a Gnome couterpart, though...

---

### Post by gmuloyaleagle on 2007-06-07
I too find this kind of annoying, but I can't find any menus or anything that would help with this.  I'm using a USB mouse for the meantime.

---

### Post by chemisus on 2007-06-21
found out how to do it here:
[http://www.arsgeek.com/?p=1862#comment-19748](http://www.arsgeek.com/?p=1862#comment-19748)

to quote:

> In Gnome:
sudo apt-get install gsynaptics
And go to System > Preferences > Touchpad

works for me.

edit: (7/29/2007)
full steps to do it from fresh install:
1) sudo apt-get install gsynaptics
2) gksu /etc/X11/xorg.conf
3) insert "Option" "SHMConfig" "true" at bottom of the "Synaptics Touchpad" device
4) save and restart gnome using ctrl+alt+backspace
5) login
6) can now run system > preferences > touchpad

---

