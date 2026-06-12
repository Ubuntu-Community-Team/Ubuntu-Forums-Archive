---
title: "Cannot disable touchpad by synclient!  HELP!"
date: 2009-12-21
forum: Hardware
---

### Post by zggame on 2009-12-21
The touchpad in ubuntu is always frustrating.  I use ubuntu on various laptops for a while.  The latest is a Compaq CQ60-420US.  Its touchpad has an ON/OFF button,  which is very convenient in windows, but never works on Ubuntu.  :(  First of all, those In the 9.0.4, I setting about disable touchpad while using keyboard "syndaemon -i xXX" never works on me well.  I usually use an external mouse anyway.  So normally I just disable the touchpad.   But I cannot disable it on the start-up because occasionally I use the laptop without external mouse.  

I use "touchfreeze" program initially.  It gives me a icon on the tray and I can switch the touchpad on/off.  But 9.10 upgrade breaks it.  I wrote a script call "synclient TouchpadOff=1".  It works for about a month.  Probably one or two weeks ago, some update breaks it.  The script used to be able to run as normal user.  Now it has to be run as root.  And it does not work.  Sometimes it works for a short while, then touchpad suddenly comes back to alive.  I also tried the gsynaptics, which calls synclient as I believe and gives me similar thing.  Touchpad stays put for a short while after I disable it and comes back to life after maybe 2 minutes.  

What should I do? I really hate my cursors jumping around.

---

