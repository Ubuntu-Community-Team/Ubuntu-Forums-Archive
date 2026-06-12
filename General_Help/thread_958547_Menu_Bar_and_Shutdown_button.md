---
title: "Menu Bar and Shutdown button?"
date: 2008-10-25
forum: General Help
---

### Post by BetaMaster on 2008-10-25
Okay, so, these are two very minor questions, but they're just immediate differences I noticed between the LiveCD of the Intrepid Ibex RC and the final install. The first is the apparently menubar transparency, which seemed to be done by it using the background image as an overlay. This is not present in my install of Ubuntu, though it was on the LiveCD. I tried to duplicate it in the settings, and it didn't look anything like it (instead of a degree of 'transparency,' it was entirely transparent. Maybe the LiveCD had a separate image file for this?).

The next thing is something I noticed with the LiveCD that I liked: the new shutdown button. Specifically, how it used a drop-down menu to log off/shut down/etc. After installing Intrepid, I noticed that the button had the same functionality as Hardy - bringing up a window. Any way to fix this?

Thanks!

---

### Post by BetaMaster on 2008-10-25
Not to bump my thread, but... bump. :p

---

### Post by drs305 on 2008-10-25
When you say 'menu bar', are you talking about the top and/or bottom panels? If so, you can right click, select Properties, Background, and move the Style slider to set the amount of transparency.

If you are talking about the window decoration (depending on the theme, the orange bar at the top of each app's window), one way to set the amount of opacity may be via gconf-editor:
```
gconf-editor /apps/gwd/metacity_theme_opacity
``` 
1 is opaque, .1 would be almost transparent.

---

### Post by BetaMaster on 2008-10-25
Thanks, I did mean the panel; I always forget the correct term for it.

I knew it wasn't the transparency setting though, I had tried that and it didn't look right. I rebooted back into the Live CD to find out, and it turns out there's an actual image that it uses (seems that it's a PNG with gradient transparency), called panel_bg.png. I didn't know if it was just in the LiveCD, or not, so I copied it onto a thumb drive. If anyone else wanted it, I've attached it to this reply.

As for the logout/restart/shutdown button, I figured out what that was too, it was just one of the launchers I'd never paid much attention to, or used, before: User Switcher. I find it immensely more appealing than the Shut Down or Log Out launchers!

---

