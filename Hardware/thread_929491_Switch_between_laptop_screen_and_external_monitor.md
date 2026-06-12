---
title: "Switch between laptop screen and external monitor?"
date: 2008-09-25
forum: Hardware
---

### Post by nonoitall on 2008-09-25
I have an Acer Aspire 5520-5290 laptop running Hardy and am wondering if it's possible to easily switch between an external monitor and the laptop's own screen.  The IGP is a GeForce 7000M, and the restricted drivers are installed.  Until my desktop PC is repaired, I have my laptop hooked up to my monitor.  While it's hooked up to the external monitor, I'd like to use that, and only that, monitor.  So far I have two rather imperfect solutions:

1. Leave everything as it is by default.  When using this method, the laptop happily uses only my external monitor *until X starts*.  Then it proudly displays Nvidia's logo on both screens and from there on out, it's two screens side-by-side.  I *can* turn off the laptop's screen using Fn+F6, but it still thinks there are two screens, and the mouse gets lost over in the oblivion that is my laptop's screen with annoying frequency.  (What I really love is typing out a sentence or so, only to realize that the cursor had drifted over to the laptop's screen, and taken the focus with it.)  Finally, those problems aside, if I *do* want to use my laptop's screen, none of my work gets moved over there when I disconnect the external monitor.  (It continues to display a rather naked-looking desktop, which also doesn't share my desired GNOME panel configuration.)

2. Manually disable the laptop's internal monitor in the Nvidia X Server Settings (nvidia-settings), and restart X.  This method works perfectly when I'm using the external monitor.  But, if I want to switch to the laptop's monitor, I have to restart X, which is a bit of a pain (especially if I'm working on something).  Plus, if a power outage occurs (which can happen fairly frequently here, and is one reason I really like laptops) I'm basically stuck with a slowly dying battery, and no way to switch back to the laptop's screen without blindly restarting X and killing all my work.

Is there an option #3?

---

### Post by nonoitall on 2008-09-25
Bump.

---

### Post by beyboo on 2008-10-17
I have the same issue with my acer laptop.Restart X seems the only option till now !!

---

