---
title: "Startx in the background?"
date: 2008-11-16
forum: General Help
---

### Post by JanusDuo on 2008-11-16
Here's the deal.  I've got a box I have setup to run this XWindows program, that's it.  I turn it on, it boots up and it runs it's global xinitrc which calls startx, then the program.  Thing is startx starts and I'm treated to the ugly grey background with the ugly X for a mouse for about 60secs while my program goes through its initialization back at the terminal.  I have no idea if it's even starting until it starts using the XServer.

How can I start the X service without using any windows manager so that when my program wants to use the XServer it will be there, but otherwise it'll stay hidden?

I tried adding a & to the end of startx but it didn't seem to do anything.

---

### Post by Th3Professor on 2008-11-16
> **JanusDuo said:**
> ...ugly grey background with the ugly X for a mouse...

Just a side-note, and this isn't directly addressing you question, though it sounds like it's loading FVWM. ;-) A really cool wm is WM2. :KS

---

### Post by kerry_s on 2008-11-16
> **JanusDuo said:**
> Here's the deal.  I've got a box I have setup to run this XWindows program, that's it.  I turn it on, it boots up and it runs it's global xinitrc which calls startx, then the program.  Thing is startx starts and I'm treated to the ugly grey background with the ugly X for a mouse for about 60secs while my program goes through its initialization back at the terminal.  I have no idea if it's even starting until it starts using the XServer.

How can I start the X service without using any windows manager so that when my program wants to use the XServer it will be there, but otherwise it'll stay hidden?

I tried adding a & to the end of startx but it didn't seem to do anything.

sounds like the gnome fail safe.
how are you auto logging in?
what window manager is it currently using?

---

### Post by spupy on 2008-11-16
> **kerry_s said:**
> sounds like the gnome fail safe.
how are you auto logging in?
what window manager is it currently using?

I think he means that his xinitrc is not starting a window manager, but his program. In this case nothing except that program is running on the xserver. The problem is that X without a window manager has an ugly white-black background and an 'x' for a cursor.

@JanusDuo: perhaps you can use **feh** to set the background of the root window (the gray bg) to some kind of wallpaper. The command is:
```
feh --bg-scale wallpaper.jpg
```

---

### Post by JanusDuo on 2008-11-17
spupy had the right of it.  I'm not using a window manager as that would be unnecessary.  I'm using this particular PC as the innards of an arcade game machine, so a window manager is just wasted resources.  I do need X however.

I made a big deal in the OP about X being ugly, but that was tounge-in-cheek mostly.  I know how to change the appearance of a blank X window, in fact my current solution is to call mplayer to play a little "loading" video I made.

Thing is I'd rather have it behave like my program does when I call it from a terminal window with an Xserver already running.  It goes through its initialization and outputs a bunch of log type stuff to the terminal, then once its done initializing it takes over an Xserver and starts displaying its graphic interface.

That's what I want.  I don't want to see X until my program is actually using it.

---

### Post by jpkotta on 2008-11-22
> **Th3Professor said:**
> Just a side-note, and this isn't directly addressing you question, though it sounds like it's loading FVWM. ;-) A really cool wm is WM2. :KS
Default FVWM is only ugly because default X is.  I prefer to think of it as a blank canvas that you can't wait to paint.

> **JanusDuo said:**
> spupy had the right of it.  I'm not using a window manager as that would be unnecessary.  I'm using this particular PC as the innards of an arcade game machine, so a window manager is just wasted resources.  I do need X however.

I made a big deal in the OP about X being ugly, but that was tounge-in-cheek mostly.  I know how to change the appearance of a blank X window, in fact my current solution is to call mplayer to play a little "loading" video I made.

Thing is I'd rather have it behave like my program does when I call it from a terminal window with an Xserver already running.  It goes through its initialization and outputs a bunch of log type stuff to the terminal, then once its done initializing it takes over an Xserver and starts displaying its graphic interface.

That's what I want.  I don't want to see X until my program is actually using it.
What if you started an xterm, and had that xterm call your program?
```
xterm -e your_program
```

---

