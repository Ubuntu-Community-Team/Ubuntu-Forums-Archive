---
title: "[SOLVED] Windows bigger then resolution"
date: 2008-07-24
forum: Hardware
---

### Post by WhizCas on 2008-07-24
Hi,

I've bought myself a mini-notebook and got ubuntu running almost perfectly with Compiz. Now there is only one problem, because it's a mini-notebook the resolution is only 1024x600@60hz. And most of the windows in ubuntu (i.e. gnome preferences windows) are higher than 600 pixels. Is there a solution that I can move the window all around with maybe alt+mousebutton with the top of the windows above the screen resolution so I can click next. Sorry for the cryptic description, but it's hard to explain :P. Thanks in advance!

---

### Post by andrewc6l on 2008-07-25
You'll want to set the Virtual option in the Display section of your xorg.conf file. man xorg.conf and searching for Virtual will give you more details.

I just tried adding this:

  Virtual 1920 1024

to the Display subsection of the Screen section of my xorg.conf. A few things I've learned:
  - if you use Virtual "1920x1024" instead, you'll regret it because X won't start properly
  - XFCE appears to scale the screen; I believe GNOME/KDE pan around
  - Make sure not to make your virtual screen too much larger than your existing one, or you might not see the login dialog

---

### Post by WhizCas on 2008-07-25
Problem solved :). Compiz constrains the top of the screen. You can turn this of by going to System > Pref. > Advanced Desktop Effects Settings > Move Windows > Turn off "Constrain Y"

---

