---
title: "Connecting a projector to my desktop computer (nVidia)"
date: 2008-01-14
forum: Hardware &amp; Laptops
---

### Post by daller on 2008-01-14
Hi there,

I've just bought a projector, and can't wait to get it up and running...

My desktop-computer has both a VGA and a DVI output. The DVI is used for my pc-monitor, and I intend to use the VGA for the projector.

Ideally it should not just be a clone-image, but an independant session, that I can tell mplayer (example) to use...

The card is a GeForce 7600 GS

I've been suggested to use nvidia-settings, but it seems to remove the nvidia-glx package during installation...

How do I set things up?

---

### Post by jackflap on 2008-01-14
When you try to use nvidia-settings, are you doing the following?

1) Go to command line
2) Type: nvidia-settings
3) Press enter

Does the nvidia-settings panel appear? I don't see how it's removing the nvidia-glx, unless you're doing something else.

From the nvidia-settings you can fiddle with the gfx displays & options quite easily.

Let us know how it goes.

Alex

---

### Post by daller on 2008-01-14
Ah, I misunderstood some other instructions...

Installing the package "nvidia-settings" causes "nvidia-glx" to be removed...

Didn't realise until now, that nvidia-settings is part of nvidia-glx apparent&#314;y.

But it doesn't resolve my problem though!

Connection the projector to the VGA output, and restarting X (Ctrl+Alt+Backspace) causes my monitor på go into "Power savings mode" (standby) - and the projector says "Frequency out of range".

I then disconnect the projector, and restart X again, and my monitor comes back up...

What can I do to fix this?

My primary monitor is 1600x1200px, and the projector can't handle that resolution...

---

### Post by daller on 2008-01-14
I forgot to "save to xorg.conf" in the application...

I basically works now! - But my projector runs at 800x600, but should be 1280x720 - how do I fix that?

And what display-number does it have?

Earlier (when I used my TV to display movies) I used this command:

DISPLAY=:0.1 mplayer -fs MOVIE.AVI

I've tried a lot of different numbers, but nothing but 0.0 or just 0 works (my primary display)

---

### Post by jackflap on 2008-01-14
I haven't done this with an external vga port before, but in the nvidia-setting panel you should be able to configure a second display somewhere.

Choose your monitor as your primary display, and then choose to configure a secondary display. You can position it to the right (or left) of the first display, meaning that when you move your mouse cursor to the edge of the screen, it will appear on the 2nd display.

You should also be able to configure the resolution of the secondary display, and also, have it run a completely separate XWindow server for it if you want, so that it's almost like two separate computers, but with the bonus that u can move the cursor between the two.

Alex

---

