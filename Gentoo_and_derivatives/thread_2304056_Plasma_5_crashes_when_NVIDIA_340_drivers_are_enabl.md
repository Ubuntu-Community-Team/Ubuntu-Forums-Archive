---
title: "Plasma 5 crashes when NVIDIA 340 drivers are enabled"
date: 2015-11-24
forum: Gentoo and derivatives
---

### Post by Zeikcied on 2015-11-24
I recently switched to Sabayon and use the KDE Plasma 5 desktop.  My NVIDIA graphics card runs on the 340 series of drivers, and after some fuss (including masking newer drivers) I got them installed.  However, when I have OpenGL set to NVIDIA (eselect opengl set nvidia), whenever I log in, Plasma 5 crashes.

The Breeze splash screen doesn't show up, it goes to a black screen, and I get three or four messages that Plasma crashed.  Other KDE apps, like Choqok and Akregator, still run and function without any trouble.  krunner also crashes as soon as I try to use it, and kdeinit crashes when I use ctrl+alt+delete to go back to the login screen.

If I have OpenGL set to xorg-x11, Plasma works just fine.  I'm stuck at 1024x768, but it works.  I would really like to get those drivers working properly, though.

I'm brand new to Sabayon after having used Kubuntu for nine years, so a few things are a little foreign to me.

---

