---
title: "Use Menu instead of Alt as AltGr"
date: 2008-08-24
forum: General Help
---

### Post by HyperHacker on 2008-08-24
I set up the US altgr-intl keyboard layout, but I don't like that it uses one of the Alt keys as AltGr. Is it possible to use that useless Menu key instead?

---

### Post by mssever on 2008-08-24
In Keyboard Preferences, go to Layouts tab > Layout options > Third level choosers

---

### Post by HyperHacker on 2008-08-24
I don't see a Layout Options or Third Level. :confused: If I uncheck "Use X Configuration", something breaks. The window closes and my window decorations and icon theme change. When I open it again, they change back and the box is checked again.

---

### Post by mssever on 2008-08-24
Here are a couple screenshots on my system (Ubuntu Hardy; what are you running?)

---

### Post by HyperHacker on 2008-08-24
Xubuntu Hardy, so XFCE. I can get to that dialog in gnome-control-center, but it's empty (no layouts listed, unknown model, etc). Would it still work to change those settings?

---

### Post by mssever on 2008-08-24
> **HyperHacker said:**
> Xubuntu Hardy, so XFCE. I can get to that dialog in gnome-control-center, but it's empty (no layouts listed, unknown model, etc). Would it still work to change those settings?
Try it and see. I don't use Xfce, so I really don't know how it works, and I don't know how to modify the settings at a low level.

---

### Post by HyperHacker on 2008-08-24
Nope, didn't do anything.

---

### Post by HyperHacker on 2008-08-31
I just tried again and was able to uncheck "Use X configuration" and change layouts without breaking anything, but the layout I want doesn't seem to exist. How do I edit them? (Also, it randomly changed the keyboard model from Generic 105-key to Generic 104-key, and when I changed it back, the same crash happened as I described above.)

Also, I just noticed if I press the sleep button, the system powers off without even doing a clean shutdown. Would really like to disable that. >_> (It doesn't shut down *immediately*; it looks like it tries to go into sleep mode but doesn't.)

---

### Post by mssever on 2008-09-01
> **HyperHacker said:**
> the layout I want doesn't seem to exist. How do I edit them?I've been wondering the same thing, since I'd like to customize my layout(s).

> Also, I just noticed if I press the sleep button, the system powers off without even doing a clean shutdown. Would really like to disable that. >_> (It doesn't shut down *immediately*; it looks like it tries to go into sleep mode but doesn't.)If you were running Gnome, I'd suggest that you go to gconf-editor and uncheck /apps/gnome-power-manager/general/can_suspend. But alas, I don't know Xfce.

Of course, the proper thing is to find out what's going wrong when you try to suspend. That sounds to me like it'd be tricky to track down. My best suggestion is to examine the output of dmesg, as well as the contents of the relevant logfiles in /var/log.

---

### Post by HyperHacker on 2008-09-01
Well I'm not really concerned about that; I never use sleep mode anyway. I just don't want that button doing naughty things if I press it by accident.

---

### Post by MoxieAndWhimsy on 2009-03-18
I've been hopping between Xfce and Gnome recently and this very issue has been bugging me. In Gnome, I've played around with Keyboard settings, but well, gnome lacks some monitoring features. So, I hop over to Xfce again, and the keyboard settings are different.

If you want to change the power and sleep button behaviours in Xfce, just right-click the Battery icon on your Tray and select Preferences, or look under 'Power Management' under Settings or use Gnome-Do. Bring up the 'General' Tab and there are your options.

---

