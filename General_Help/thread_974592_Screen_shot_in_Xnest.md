---
title: "Screen shot in Xnest"
date: 2008-11-07
forum: General Help
---

### Post by fballem on 2008-11-07
I'm working my way through some documentation [http://www.gnome.org/projects/gdm/docs/2.16/thememanual.html](http://www.gnome.org/projects/gdm/docs/2.16/thememanual.html)

In that documentation, they mention using gdmthemetester, which does appear to be working. I get an xnest session with my GDM Theme showing on it. The documentation mentions that I should be able to use Alt-Printscreen to get a screenshot. That does not appear to be working at all.

I'm new at this, so I'm probably making a newbie mistake. Alt-Printscreen does work in my normal ubuntu session.

If anyone could point me in the right direction, I'd be most grateful.

Thanks,

---

### Post by bapoumba on 2008-11-07
Please install xnest, then
```
gdmflexiserver --xnest
```

But it seems I have the same problem with taking an active window screenshot.. Alt-print does not work, or does not save the file (i briefly see the wheel timer). Print works for the whole desktop, <super><left mouse button> too to select an area. I've tried to reconfigure the keyboard shortcut for the active window screenshot, but it does not work either..
I've been looking but nothing so far. I have a French azerty keyboard layout.
I have not done this in a long time, and it used to work..

Edit : [https://bugs.launchpad.net/ubuntu/+source/gnome-utils/+bug/269888](https://bugs.launchpad.net/ubuntu/+source/gnome-utils/+bug/269888)
I'm on hardy here, looks fixed on Intrepid. Will try later on Intrepid.

---

### Post by fballem on 2008-11-09
I'm running Ibex and it still is not fixed. My workaround was to use Print Screen key, then edit the resulting file in GIMP.

Good enough for now, but the bug still exists.

---

### Post by bapoumba on 2008-11-09
Talking about gimp, I forgot to mention that you can take screenshots directly from gimp.

I played around a little more with the shortcuts key and accidentally noticed that I could take a window screenshot from any window but xnest..
Please try alt-print (or change it, I'm using ctrl-print for now) on another window and see if you get the same behavior.

---

### Post by fballem on 2008-11-10
I did try earlier and Alt-Printscreen works from any window, except xnest. It sounds like there's a bug in here somewhere.

---

