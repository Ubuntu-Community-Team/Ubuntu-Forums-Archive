---
title: "Appearance settings/graphics driver reset on boot"
date: 2011-11-03
forum: Hardware
---

### Post by M1ke on 2011-11-03
I'm using Ubuntu 10.04 Lucid on a Lenovo G550 laptop which has a GeForce G210M graphics card, and I'm using the proprietary nVidia driver. My ubuntu/driver installations have not changed in about a year and I have a couple of compiz effects enabled (the cube, wobbly windows).

A few days ago on logging in I was greeted with a message from docky saying it required compositing to work properly, a screenlet was missing from my desktop and the tops of all windows (title bar, min/maximise/close etc in nautilus windows) were gone too.

I saw in my appearance settings that desktop effects were set to "none" instead of "custom", and on clicking "custom" Ubuntu searched for a driver for a moment and promptly restored all my settings - the dektop effects, window titles, everything that was missing. However, every time I restart Ubuntu now I have to go through the same process.

My limited understand of Ubuntu would lead me to believe there's something iffy with the graphics driver, but how can I check? And what could have caused this sudden inability to retain settings that Ubuntu has had no trouble with for a year or so? It happened from one day to the next without any system changes that I know of.

---

### Post by M1ke on 2011-11-07
No suggestions on this one? Hoping someone has an idea of where to begin!

---

### Post by M1ke on 2012-01-31
Alright, so after a long time of just tolerating this I stumbled upon the answer investigating something else entirely. Often the way! I'll leave the solution here in case anyone happens across the same problem someday and finds it helpful.

In the end, it seems my window manager wasn't loading correctly on boot. The fix was as simple as going in to **System > Preferences > Startup Applications** and adding a new one with the command **compiz --replace** to force compiz to start on every boot.

---

