---
title: "Avant Windows Navigator Help"
date: 2008-11-10
forum: General Help
---

### Post by alex-stag on 2008-11-10
Hello.After upgrading to ubuntu 8.10 and reinstalling Avant windows Navigator , a weird vertical annoying white line appeared.It seems like a bug.I reinstalled AWN but it remains.I don't know ehat else to do.Any Help??
Thanks in advance!!!

---

### Post by constrictor on 2008-11-10
Check you launchers. It is very possible that one of them is not loading properly. Try right clicking on the line, it's very tricky I know but it could give you some options to sort it out.

---

### Post by broneo on 2008-11-10
> **alex-stag said:**
> Hello.After upgrading to ubuntu 8.10 and reinstalling Avant windows Navigator , a weird vertical annoying white line appeared.It seems like a bug.I reinstalled AWN but it remains.I don't know ehat else to do.Any Help??
Thanks in advance!!!

same with me, try to right click on vertical white line, nothing's happen..

---

### Post by DJ_Peng on 2008-11-11
I'm thinking it may be an applet that isn't loading properly. At least it's been my experience that a vertical line is usually an applet that's not working properly. Can you identify what applet it may be from its position on the dock?

---

### Post by reacocard on 2008-11-12
vertical lines generally mean a malfunctioning applet. Check your awn-manager and see whether you have an applet enabled that isn't loading correctly. Closing awn and then launching it from the command line with
```
avant-window-navigator
```
may give some useful output.

---

### Post by binbash on 2008-11-12
yes it is a malfunctioning applet.Open applet manager and remove non-working one(s) then restart awn

---

### Post by Bill.Scott on 2008-11-17
Hello,

Similarly I am setting up 8.10 and Avant in a dual screen configuration when I am at work (Laptop). The issue I am having is that Avant is not even displaying on the screen when I run it while docked.
The screen resolution hack has been tried with no success.
The desktop monitor is: 1280x1024 and the Laptop is 1920x1200.

Anyone that can assist with this resolving issue would be greatly appreciated...

---

### Post by Arcturus691 on 2008-11-17
> **alex-stag said:**
> Hello.After upgrading to ubuntu 8.10 and reinstalling Avant windows Navigator , a weird vertical annoying white line appeared.It seems like a bug.I reinstalled AWN but it remains.I don't know ehat else to do.Any Help??
Thanks in advance!!!

This is actually a bug, see: [https://bugs.launchpad.net/awn/+bug/273326](https://bugs.launchpad.net/awn/+bug/273326).  Also there is another thread on this topic but I cant find the link right now because the forum site is very slow at the moment.  

There is a workaround until this gets fixed:
-Launch AWN
-Click on applets (on left of screen)
-In the Applet Preferences screen, at the bottom click and drag 
the launcher all the way to the right.

On my system this eliminated the lines except for when I first log in.
Move the mouse cursor over the icons to make the line(s) disappear.

---

### Post by Arcturus691 on 2008-11-17
> **Bill.Scott said:**
> Hello,

Similarly I am setting up 8.10 and Avant in a dual screen configuration when I am at work (Laptop). The issue I am having is that Avant is not even displaying on the screen when I run it while docked.
The screen resolution hack has been tried with no success.
The desktop monitor is: 1280x1024 and the Laptop is 1920x1200.

Anyone that can assist with this resolving issue would be greatly appreciated...

Are you running avant-window-navigator?  On my system I had to go to System->Preferences->Sessions and create an entry to run avant-window-navigator when you log in.  Try running avant-window-navigator in a terminal first to see if that fixes the issue.

---

### Post by reacocard on 2008-11-17
> **Bill.Scott said:**
> Hello,

Similarly I am setting up 8.10 and Avant in a dual screen configuration when I am at work (Laptop). The issue I am having is that Avant is not even displaying on the screen when I run it while docked.
The screen resolution hack has been tried with no success.
The desktop monitor is: 1280x1024 and the Laptop is 1920x1200.

Anyone that can assist with this resolving issue would be greatly appreciated...

How are the monitors positioned when you're in dual-head? If they're side-by-side then AWN might be trying to display in the empty space inherent in such a setup. That wasn't very clear so let me try to draw it out:
```

+--------------++----------------------------+
|              ||                            |
|   Monitor    ||    Laptop                  |
|              ||                            |
|              ||                            |
|              ||                            |
+--------------+|                            |
  AWN (perhaps?)|                            |
                +----------------------------+

(diagram not to scale)

```

This particular configuration doesnt yield readily to the monitor hack due to the fact that AWN measures from the top left so when you add resolution on the left side it gets shifted over. If it's practical to switch so the the external is on the right then the monitor hack should work.

---

### Post by Bill.Scott on 2008-11-18
Well my screens are orientade lapttop bottom and 19" on above.
I see the animation of it loading and poof its gone.

Tried the suggestions above but no luck...

---

### Post by Arcturus691 on 2008-11-19
If you run the navigator from the terminal you should see some error messages.  If so what are they?

If not then you should check your System Log and see if you can find any errors.

---

### Post by aloasi on 2008-11-19
Screen is composited.
LOADED : /usr/share/applications/vlc.desktop
LOADED : /usr/share/applications/kde/amarok.desktop
LOADED : /usr/share/applications/amsn.desktop
LOADED : /usr/share/applications/firefox.desktop
LOADED : /usr/share/applications/azureus.desktop
APPLET : /usr/lib/awn/applets/taskman.desktop
APPLET : /usr/share/awn/applets/cairo_main_menu.desktop
APPLET : /usr/share/awn/applets/stacks.desktop
APPLET : /usr/share/awn/applets/awnsystemmonitor.desktop
APPLET : /usr/share/awn/applets/awnterm.desktop
APPLET : /usr/share/awn/applets/trash.desktop
APPLET : /usr/share/awn/applets/quit-applet.desktop
Awn Terminal applet alloc

(awn-applet-activation:8272): GLib-GObject-WARNING **: /build/buildd/glib2.0-2.18.2/gobject/gsignal.c:2346: handler `37' of instance `0x243c000' is not blocked

I also get the white lines and closed awn and started it in terminal this is what i get. Sorry but i don't know how to write the code in a box.

---

### Post by alex-stag on 2008-11-24
Just deactivated all applets and reactivated them.Problem solved!!

---

