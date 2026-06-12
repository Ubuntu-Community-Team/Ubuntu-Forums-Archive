---
title: "Mouse buttons don't work"
date: 2008-11-10
forum: General Help
---

### Post by spibou on 2008-11-10
The buttons on my mouse suddenly stopped working meaning when I click on something nothing happens. But I can move the pointer around as normal. If I go to console and start a second window session then on that session the mouse works fine. Any idea how I can get it to work on the first session? I know I can kill the session but I have several programmes running so it would be quite inconvenient. The desktop environment is Gnome and the window manager metacity. In case it is important, the window in focus on the session where the mouse buttons do not work is the GUI of vim.

---

### Post by spibou on 2008-11-10
Wow, this went to page 4 in no time at all.

---

### Post by spibou on 2008-11-10
1. Does metacity offer any way to switch between windows using the keyboard?

2. Is there a way to switch from metacity to a different window manager without stopping the applications running on top of metacity ? I am especially keen on not having the eterms terminated.

---

### Post by spibou on 2008-11-10
Pressing Alt+Tab fixed it 8)

But I'm not marking the thread solved yet because I'm hoping that someone will be able to come up with an idea on what caused it to begin with. Could it be that I accidentally pressed some combination of buttons and that caused metacity not to recognise mouse buttons anymore?

---

### Post by CatKiller on 2008-11-14
> **spibou said:**
> 2. Is there a way to switch from metacity to a different window manager without stopping the applications running on top of metacity ? I am especially keen on not having the eterms terminated.

Yes, with the --replace option. ```
compiz --replace
``` is the one that most people will use, since that turns on the fancy effects, and they would use metacity --replace to turn them off again, but AFAIK other window managers would work the same way.

---

### Post by AntonOlsen on 2008-11-17
This is also happening to me.  Fresh Intrepid install, no compiz, using two video cards, 3 monitors, and Xinerama.  The only thing I've changed from the stock install was to configure xorg for 3 screens and xinerama and add a few plugins to firefox.

Once in a while moving the mouse to a different usb port works, once plugging in a spare mouse worked, but I usually have to ctrl-alt-bkspc to get the mouse buttons to work again.

---

