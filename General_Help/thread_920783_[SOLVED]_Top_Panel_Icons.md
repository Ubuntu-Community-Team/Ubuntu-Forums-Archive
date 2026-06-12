---
title: "[SOLVED] Top Panel Icons"
date: 2008-09-15
forum: General Help
---

### Post by Cuttysark on 2008-09-15
I'm running both AWN and Cairo (I know, overkill to some). I've removed the bottom panel, replacing the Trash with an AWN applett. I also have the applett that gives me the top panel menus. Before I remove the top panel however, I'd like to find a way to keep access to the icons there, screenlets, network connection, volume etc. I tried dragging them onto the desktop and on to AWN itself but with no success. Can anyone give me a pointer please?

---

### Post by Genius314 on 2008-09-15
You need a System Tray applet, either for Cairo-Dock or AWN.
For Cairo-Dock, it's called "systray."
I'm not sure of the name for AWN, but it should be something like System Tray or Notification Area.

Volume is separate from the System Tray. You'll need a volume applet for that.

---

### Post by Cuttysark on 2008-09-15
I did find one for AWN but all I get when I activate it is a white line. I'll have a look and see if there are any others, and for a Cairo equivalent.

---

### Post by Devon788 on 2008-09-15
hey...i was having that same problem a few days ago...if you remove the system tray from the top panel and restart AWN it should work

---

### Post by Cuttysark on 2008-09-16
Thanks for the advice guys. I tried what you suggested Devon and hey presto there it was. I'm not massively impressed with the icon and can't see how to change it yet but I'm working on it. I also want to check the Cairo offering when I can find it.

Is it impossible to get rid of both top and bottom standard panels? Now that the top one is gone, the option to delete the bottom one is greyed out.

---

### Post by Genius314 on 2008-09-16
You can't get rid of both panels, because then there'd be no way to get them back.

Are you using Compiz? If so, you can easily hide the panel.

In CCSM (sudo apt-get install compizconfig-settings-manager) go to the Widget Layer plugin, enable it, and click on the behaviour tab.
In the "Widget Windows" box, type in "(class=Gnome-panel & type=Dock)" (without the quotes).
Now you can toggle the panel on and off with a keybinding (F9 by default). It should be hidden by default.

Hope that helps. :)

---

### Post by Cuttysark on 2008-09-16
I already had CCSM installed and that did the trick nicely, thanks Genius.

---

