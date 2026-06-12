---
title: "m200, two screens"
date: 2009-09-03
forum: Hardware
---

### Post by twinotter on 2009-09-03
Hi,

I'm trying to set up a box for running Boxee on an external Dell 2001FP with a Toshiba m200 under Jaunty with the gnome environment.  Nvidia video card on the m200 laptop.

I'm having a terribly hard time getting the screen stuff to work.  It seems to be a combination of the bios LCD setting and of course the annoying xorg.conf file.  

In order for boxee to work, I have to have the nvidia drivers working.  I have those up and can generally get them working.  But whenever I scale the screen in any way, boxee suddenly becomes glacially slow.  glxgears still gives an okay refresh rate, so there's probably something wrong with boxee... however, that doesn't change my screen problems.

Could anyone with a similar setup send me their xorg.conf file?  What's the best way to set this up?  Twinview seems bad because full screen seems to mean to attempt to put the program on both screens (perhaps not a bad approach if you were making a video wall...).  Xinerama doesn't seem to work for me - I can get both X screens running, but each has a menu bar and when my cursor goes from the first screen to the second, it can't go back.

What's the key to making to separate X displays work?  How do you switch between them?

Thanks!
twinotter

---

