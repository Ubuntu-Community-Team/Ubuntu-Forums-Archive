---
title: "fglrx big desktop help"
date: 2006-12-14
forum: Hardware &amp; Laptops
---

### Post by awry on 2006-12-14
Can anyone help me figure out how to set up fglrx drivers in big desktop mode optimized for my setup?

Here's my setup:

Lenovo Thinkpad T60p
FGL V5200/256MB
15" 1600x1200 (4:3)
Advanced MiniDock w/ DVI-D

Samsung 215TW
21" 1680x1050 (16:10)

I'd like to take full advantage of both displays' resolutions, but so far that doesn't seem possible.  I've experimented with various Virtual display options in xorg.conf to no avail.  Isn't "pair mode" supposed to allow to use two displays of different resolutions??

Does anyone know, theoretically, what the max framebuffer size I can get out of these resolutions is?  

I seem to get 3360x1050 or 3200x1200, neither of which really makes sense.  With either of these resolutions, one of the two displays' resolutions is exceeded, pushing content off the edges.

Both displays support 1280x1024 - is it possible to get a 2560x1024 framebuffer?  How?  How does xorg/fglrx calculate the "big desktop" resolutions available?

I'm pretty lost as to what the drivers are even SUPPOSED to be capable of, much less how to configure this.  Documentation is really sparse.

I've tried several versions of fglrx, 8.29.6, 8.31.5, and now 8.32.5.

Here's a sample [xorg.conf]("http://awry.ws/xorg.conf") and [Xorg.0.log]("http://awry.ws/Xorg.0.log"), and a [screenshot]("http://awry.ws/Screenshot.png") of a corruption problem I was having with this config.

HELP!!!!!

---

