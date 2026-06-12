---
title: "Intel HD Grapics 3000 ~ GLX missing???"
date: 2011-11-16
forum: Hardware
---

### Post by danube on 2011-11-16
Hi geniuses!

I just got a brandnew laptop from my company with some Redmond stuff preinstalled. So first step of course, do some important installation.

So finally, Ubutnu was up and running, but with two issues. One I'd like to bring up is, that I experience some troubles with my graphic card (or driver...).

Google Earth says: Unknown graphic card.
Neverball says: Couldn't find matching GLX visual
Alt-Tab shows a static switcher instead of the Compiz switcher

glxinfo says:
```
$ glxinfo
name of display: :0.0
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't find RGB GLX visual or fbconfig

Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
```

The machine is a Fujitsu Lifebook E751 with a Intel HD Graphics 3000 installed (at least what the manufactor says).

Well... there anything else you wanna know? I really hope we can solve this issue! I really miss neverball... [-o<

---

### Post by veiovis on 2011-12-03
hi,

this worked for me on Thinkpad T520:
[http://theiszm.wordpress.com/2010/06/27/glx-missing-on-display/](http://theiszm.wordpress.com/2010/06/27/glx-missing-on-display/)

And reboot after that.

---

