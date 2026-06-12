---
title: "Help with detecting keyboard input."
date: 2008-07-11
forum: General Help
---

### Post by DagMan on 2008-07-11
First off, this isn't for a keystroke logger.  I have an Elantech touchpad which isn't compatible with the synaptics driver and thus not with any of the synaptics related settings. It shows up as a wheel mouse and uses the mouse section of xorg.conf, so that's what I'm stuck with.  It works quite well except that the only way to disable the touchpad is to pull the kernel module.  I can't just set it up like the pads that use the synaptics drivers so it uses syndaemon to disable the pad when I type.

I have to go about this by having something run that will detect keyboard output, and then signal the script I wrote to pull the module (and hopefully reinsert it after typing stops which I think I will already have working).

Can someone please tell me how I would listen for keyboard output?

---

### Post by jonlemur on 2008-07-12
I don't know if this will help at all, but xev listens for anything to happen in the X session, like a mouse moving, or buttons being typed.  There may be a way to configure it to listen only for keyboard buttons being pressed, but I'm not certain if it can do what you want it to do.  It may be interesting to look into though.

---

### Post by DagMan on 2008-07-12
Thanks, it won't work though.  It was my first thought as well.  xev runs a window and only gets keycodes when it is in focus.

---

