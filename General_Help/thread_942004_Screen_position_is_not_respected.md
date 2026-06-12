---
title: "Screen position is not respected"
date: 2008-10-08
forum: General Help
---

### Post by nikosapi on 2008-10-08
I have a smaller screen above a larger screen and I'd like to center the top one. I can do this easily in xrandr except that KDE doesn't re-center the desktop on top screen.

Here's the relevant bits of my xrandr output after positioning everything:
```
Screen 0: minimum 320 x 200, current 1920 x 2100, maximum 4000 x 4000
VGA-0 connected 1440x900+240+0 (normal left inverted right x axis y axis) 410mm x 257mm
   1440x900       59.9*+
DVI-I-0 connected 1920x1200+0+900 (normal left inverted right x axis y axis) 518mm x 324mm
   1920x1200      60.0*+
```
Notice that 240 = ( 1920 - 1440 ) / 2, so that it centers the top output (VGA-0) right in the middle, above the bottom output (DVI-I-0).

Perhaps a picture can explain this better...

This is what my current desktop looks like:
[IMG]http://i37.tinypic.com/8vq7if.png[/IMG]

What ends up happening is that the left side of the top screen gets cut off and the right side is just black. What I need is a way to move the "Desktop" 240 pixels to the right to match what I've set up physically and in xrandr. It *should* look like this (a quick gimp'd mockup):
[IMG]http://i37.tinypic.com/2vtpd2r.png[/IMG]

Any suggestions?

---

