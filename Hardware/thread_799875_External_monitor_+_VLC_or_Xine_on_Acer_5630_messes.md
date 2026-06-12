---
title: "External monitor + VLC or Xine on Acer 5630 messes up Gnome"
date: 2008-05-19
forum: Hardware
---

### Post by Jetze on 2008-05-19
Hi,

Two, probably related problems:

1) I had an external monitor attached to my Acer 5630 laptop. Using VLC or Xine full screen messed up Gnome seriously! After closing VLC or Xine, the desktop dit not redraw correctly. The drawing surface of the media players did not seem to be deleted properly, with the result that the screen was mostly black, except when another window had to be redraw, then it would flicker, but go back to being black instantly. The laptop screen was turned off in System->Preferences->Screen Resolution. Having detached the monitor, and working on just my laptop screen solved this problem. 

2) Also with external monitor. When my screen is reenabled after power management had turned it off (not just screensaver), Gnome is also messed up. Now, the process is a gradual break-down of the desktop surface: windows being draw in the wrong place, screen going black until windows are redrawn, the entire desktop wrap around shifted horizontally by about 50-100 pixels. Eventually crashing Gnome.

My guess is that somewhere in reinitializing the screen, Gnome/Ubuntu uses some parameters for the laptop screen, and draws to the external screen, which is obviously not correct.

The problem had been appearing from the get-go, so it is unlikly to be a conflicting software issue.
_________________________________________________________________________
Acer 5630 series
Hardy Heron 8.04
IIyama VMP 450 @ 1600x1200

---

