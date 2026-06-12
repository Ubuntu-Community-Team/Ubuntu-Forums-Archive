---
title: "Intrepid &amp; HDTV vs compiz"
date: 2008-11-09
forum: General Help
---

### Post by DorianX on 2008-11-09
After a few hours of fighting with X, I finally managed to get my dual-head display working again after the upgrade to 8.10 -- I'd expected the display setup to be a problem, so I wasn't too bothered by this.

But I'm having a devil of a time getting compiz to do what I want.

In the past, I'd run into an issue where gtk-based menus would all be strange and unresponsive and I'd have a few focus issues. I was able to track the problem down to the fact that I was using compiz on a dual head system configured to be two separate X screens (ie. no nvidia TwinView, no Xinerama -- two completely independent displays. One of the displays is my television, so I emphatically do *not* want it to behave like I've got two full-time monitors hooked up.) My main display is a DFP monitor connected via DVI, and running at 1280x1024. The secondary display is a HDTV connected via VGA and running at 1920x1024 (ie. "full HD"). In Hardy, I'd had perfectly acceptable results running either two copies of compiz (one for each X screen) or one copy of metacity, or one metacity and one compiz.

In Ibex, the old solutions aren't working; I can get 1 copy of metacity to drive both displays fine, but if I try to start compiz ('compiz --replace --only-current-screen'), metacity dies, leaving the HDTV without a window manager. If I try to run two copies of compiz, it just flat-out doesn't work at all but if I run just one copy of compiz and have it handle both screens, the most bizarre thing of all happens:

It performs adequately, graphics and menus are responsive, but it seems like Compiz (and just compiz, not X) only "sees" half of the screen. I can move my mouse around the full area of the screen, but windows are "clamped" to the left half -- I can't drag one past abotu the midline of the screen. The gnome panel even resizes itself so to only take up half the screen, and if I try to maximize a window, it only grows to fill the left side of the screen.  Just by eyeballing it, it kinda seems like Compiz thinks the aspect ratio of the screen is 4:3 instead of 16:9, and just isn't handling the part of the screen that falls outside a 4:3 bounding box. 

I can live with metacity in the short term I guess, but I *really* like the desktop cube effect, and I want it back, even if it's only on one screen. (Like I said, I'd just leave metacity on one screen and compiz on the other, but --only-current-screen doesn't seem to work the way it used to)

Any ideas?

---

