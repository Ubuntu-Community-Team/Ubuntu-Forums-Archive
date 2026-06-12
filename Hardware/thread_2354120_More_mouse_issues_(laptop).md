---
title: "More mouse issues (laptop)"
date: 2017-02-28
forum: Hardware
---

### Post by klyxmaster on 2017-02-28
I have tried many mouse solutions, but none of the issues presented in most forums, fit my problem.

tap-to-click does not work - in most places.

Rig: dv7 HP laptop
Distro: Ubunutu 15.10 GNOME


Most, if not all distros I use, are ubuntu at the core. xubuntu,lubuntu, peppermint etc.. the touchpad works right out of the box w/o a hitch, scroll, touch-to-tap (t2t) etc. Yet every time I return to ubuntu, it stops working. Sorta.
[LIST]
[*]installer - fails, hard buttons only
[*]login - pass, can t2t and works fine
[*]desktop and general use - fails.
[/LIST]
under mouse and touchpad, it only has basic settings, not the advance settings I see in some screenshots, just has primary button (L/R) double click and pointer speed.
when testing, scroll works on the picture (girl with a kite) but t2t still fails, BOTH gnome and unity. I like gnome better
Yet, back on the desktop, surfing and other general use, scroll fails again as well as t2t.

any ideas?

---

### Post by klyxmaster on 2017-02-28
solved it by doing the following:

sudo synclient tapbutton1=1

once confirmed that worked, i added it to rc.local

[PHP]
synclient tapbutton1=1
exit 0
[/PHP]

not sure why that is not in ubuntu

---

### Post by bearlake on 2017-02-28
Hi,

If you are still using 15.10 you have another problem.

15.10 reached (EOL) end of life months a go.

You need to update or install a (LTS) long-term support version. 

[https://www.ubuntu.com/info/release-end-of-life](https://www.ubuntu.com/info/release-end-of-life)

---

### Post by klyxmaster on 2017-03-04
ok, 2 things, rc.local did not make the "fix" sticky
I got a new hdd, and now have ubuntu 16.04
prob still exists. see OP.

login = tap to click works
desktop and main usage, no tap to click. scroll works fine.

---

### Post by klyxmaster on 2017-03-07
OK, i have 3 laptops, HP DV7, COMPAQ 8510P and COMPAQ 6910 with ubuntu (and varying distros, ROSE, ubuntu gnome and ubuntu) none of them allow the touch to click unless I enter the command above. anyone else with laptops have this issue? if so, how did you resolve it.  ubuntu 16.04 on all of them.

---

### Post by efflandt on 2017-03-10
If that is something you need to do after X starts, in Ubuntu open Dash (Search your computer) at the top of the Unity bar, type in: **start**, and open **Startup Applications**. There you can add your: [COLOR=#000000][COLOR=#0000BB]synclient tapbutton1[/COLOR][COLOR=#007700]=[/COLOR][COLOR=#0000BB]1[/COLOR][/COLOR]

But not sure how to do that in gnome or ROSE.

---

