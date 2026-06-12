---
title: "[SOLVED] how to get cairo-dock?"
date: 2008-08-03
forum: General Help
---

### Post by RajaAjmal on 2008-08-03
i've typed the following in terminal
**sudo apt-get update && sudo apt-get install cairo-dock cairo-dock-plug-ins**
thinking that this will install cairo-dock.After typing it, i can see some downloading and processing in the terminal. But after which i obtain an error message, i think like this (i did not note the error message)
**E: can't find cairo dock** 
Can anyone tell me how to obatain cairo-dock. should i have type something else in the terminal before typing the above command in terminal?
Please give me step-by-step instruction on how to install cairo-dock.

---

### Post by sayakb on 2008-08-03
Read here: [https://help.ubuntu.com/community/CairoDock](https://help.ubuntu.com/community/CairoDock)

---

### Post by billgoldberg on 2008-08-03
Download these two files.
[http://prdownload.berlios.de/cairo-dock/cairo-dock_v1.6.1.2_i686.deb](http://prdownload.berlios.de/cairo-dock/cairo-dock_v1.6.1.2_i686.deb)

[http://prdownload.berlios.de/cairo-dock/cairo-dock-plug-ins_v1.6.1.2_i686.deb](http://prdownload.berlios.de/cairo-dock/cairo-dock-plug-ins_v1.6.1.2_i686.deb)


Double click the first package to install, then the plugins package.

To start cairo dock when you start you pc, go to "system -> preferences -> session".

In the "command" box put in

```
cairo-dock
```

The rest of the entries in the session window you can make up.

---

### Post by RajaAjmal on 2008-08-03
thanks billgoldberg

---

### Post by ozspitt on 2008-08-21
this wouldn't download, it said to redo my preference settings. but like so much with linux it's 100% too vague. what preference setting needs to be rest???

---

### Post by Plasma_Snake on 2009-09-03
I've got it all working but few niggling issues remain.
1. How to get dock fixed to the edge, I have deselected the Auto Hide option but even then it hides automatically and when I press the shortcut button,F10, in my case to make it appear, instead of appearing back at the affixed position, like bottom edge of the screen, it appears wherever the cursor is.
I want it to remain at the bottom edge of the screen and remain there and do hide but appear as soon as I place the cursor near the edge of the screen. Please tell me what settings do I have to change and to what degree?

---

### Post by fabounet on 2009-09-03
that's the normal behavior (read the tooltip in the config panel)
also, see if the option "hide when a window is mawimized" is not activated, in the Taskbar

---

