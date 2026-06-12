---
title: "Strange mouse issues on startup"
date: 2008-10-06
forum: Hardware
---

### Post by rafe101 on 2008-10-06
These problems are on a Thinkpad R60 running Hardy.  I blame the game Planeshift for these problems, mostly because they weren't there before I tried the game, and it did lots of other crazy stuff whenever it froze up.  

Anyway, it's hard to describe the issues I'm having with the cursor, but I'll try.  When the problem first started (on startups), when I moved the cursor, it was already dragging a select box like I had the button held down, and the box would not go away.  I learned quickly to move it only slightly, and click right away to keep the box small.  Later, I put an RSS screenlet in the center of the screen so all it was doing was moving that instead of making a box. Now, my screenlets are all on the second workspace and won't stay on the first one, but that's a different issue.  

The left click acts really weird now at startup.  It will only work on a certain portion of a certain window at a time (like just the bookmarks menus of Firefox, but not the tabs or links).  I can usually right click on things and it sort of changes the left clicks focus.  In this way, I right click on my taskbar, and by repeatedly clicking the log out/power button, finally get the window to pop up.  I then log off, back in, and everything is fine again.

Any ideas anyone?

---

### Post by rafe101 on 2008-10-06
Oh, the left mouse button on the second set of mouse buttons (the Thinkpad has buttons up higher for the Trackpoint and lower for the touchpad) doesn't work.  I don't know if this is related.

---

### Post by rafe101 on 2008-10-07
Alright, on playing around with the bottom set of mouse buttons (the touchpad ones), I have found that the left button sometimes acts as a right mouse button, but slower.  An option window will open up like from a right click, but it's delayed and sometimes takes a couple of clicks to do anything, but there it is.

---

### Post by rafe101 on 2008-10-08
Is the problem with the mouse driver or the startup?

---

### Post by rafe101 on 2008-10-12
I was planning on sticking with Hardy for a while, but maybe I'll do a fresh  install with 8.10.  I didn't want to do fresh installs every six months, but that's how it's turning out.

---

### Post by rafe101 on 2008-10-14
It has now started right-clicking on its own.  I could sit and watch the cursor on the desktop create folders and open their properties.  I turned off the Touchpad and just use the Trackpoint.  That seems to have stopped the bad behavior.

Is there a way to reinstall the mouse driver?

---

### Post by rafe101 on 2008-10-23
Not one suggestion?

---

### Post by jfacemyer on 2008-11-10
Hey,

It sounds like your hardware might be going bad.

It wasn't clear if you ever installed Intrepid or not, if so did that get you anywhere, or same problem?

To check out if it's a hardware problem, you could try booting a live CD (or maybe a couple different ones) to see if the problem persists.

You might also check dmesg for anything odd-looking WRT your mouse.

One last suggestion is making sure your /etc/X11/xorg.conf isn't borked.  To be sure you can copy the default backup (in the same dir) if you don't have any customization there.

---

### Post by rafe101 on 2012-01-20
Simply resolved itself over the course of updates.

---

