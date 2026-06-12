---
title: "Netbook with normal desktop"
date: 2009-11-17
forum: Hardware
---

### Post by J V on 2009-11-17
I am creating a netbook remix for a very small screen thing...

Everything about it is fine, except the launcher, which doesn't react to mouse (And isn't very good compared to standard desktop anyway)

I removed the button for the launcher from the panel, and replaced it with a GNOME menu (Same icon, only it pops up a menu now)

The only problems are that:
* The files from the desktop still don't show up (And rightclicking doesn't work etc etc)
* The application switcher which showed the window decoration (X button etc) on the panel and opened windows next to it isn't working any more, it only shows some windows and the decoration is missing

Any help would be great thanks

---

### Post by davidryderuk on 2009-11-17
> * The files from the desktop still don't show up (And rightclicking doesn't work etc etc)


Try running the following command from terminal:

```
gconftool -s --type bool /apps/nautilus/preferences/show_desktop true

```

> * The application switcher which showed the window decoration (X button etc) on the panel and opened windows next to it isn't working any more, it only shows some windows and the decoration is missing

You need to have "Maximus window management" in the list of startup applications for the application switcher to work properly.

---

### Post by J V on 2009-11-17
Turns out I just didn't have a window open that maximus deemed maximizable, used gconf-editor to fix desktop, thanks!

---

