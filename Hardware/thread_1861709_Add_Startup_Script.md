---
title: "Add Startup Script"
date: 2011-10-15
forum: Hardware
---

### Post by ufarmer on 2011-10-15
Hi,

I am having trouble with syndaemon.  By default it is supposed to disable the touchpad for 2.0 seconds after every keystroke but mine is disabling the touchpad for only 0.5 seconds -- which is not enough.

I would like to be able to edit the script for syndaemon directly to change this behaviour but I can't find it.  Does anyone know where it is?

Alternatively I would like to be able to kill the default process and launch a new one at startup but I can't figure out how to do this.  I tried putting the script in init.d but it had no effect.  Am I missing something?

Lastly, I tried to look in System->Preferences->Startup Programs but I am having a problem displaying that menu.  It doesn't all fit on the screen so I have to scroll down to get to Startup Programs.  However, as soon as the mouse is no longer hovering over the down arrow for the scrolling, the menu jumps back to displaying its contents starting from the top -- which pushes Startup Programs off the bottom of the screen again.  This really seems like a bug with Ubuntu but I haven't been able to find a fix for it.

Any advice is appreciated.

Regards.

---

### Post by d4m1r on 2011-10-16
To edit a script, you could always do it in terminal <process name> -<settings>.

As for startup applications, if you are using Natty (11.04), you can add/remove them in System Settings>Startup Applications.

---

