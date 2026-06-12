---
title: "Vista Theme - No Change in Window Border"
date: 2008-11-14
forum: General Help
---

### Post by MTGap on 2008-11-14
In all of the screenshots I was led to believe that the window border changed as well with the installation of the theme, when I look at customize theme and the tab Window Border there is no Vista window border.

I'm using this theme: [http://gnomestyle.blogspot.com/2007/05/make-ubuntu-look-like-vista.html]("http://gnomestyle.blogspot.com/2007/05/make-ubuntu-look-like-vista.html")

Isn't window borders metacity? From what I've looked at in the other files the window bar is determined by a folder called metacity, the vista theme didn't come with one...

Gnome-looks is down right now so I can't download another file either. 




P.S. I have AWN running, but a portion of it is covered by my bottom panel is there anyway I can change it so that it rises above the bar?

---

### Post by ad_267 on 2008-11-14
That comes with an Emerald theme, not a Metacity theme. Read the sticky in this forum for information about Emerald: [http://ubuntuforums.org/showthread.php?t=809695](http://ubuntuforums.org/showthread.php?t=809695)

It's like metacity but allows more effects and requires compiz fusion.

---

### Post by MTGap on 2008-11-14
Thanks! Well I just installed Emerald and imported the aero_blue emerald theme into Emerald Theme Manager, how do I get it to display that now?

---

### Post by ad_267 on 2008-11-14
I should have said emerald is like gtk-window-decorator, not metacity. Compiz is like metacity, which is a window manager. And emerald is like gtk-window-decorator which controls window borders.

You have to replace gtk-window-decorator with emerald. To do that you can press Alt-F2 and run "emerald --replace".

---

### Post by MTGap on 2008-11-14
Well I got it to work, can't find good link of Segoe UI though, and gnome-look still down (anyone know why?) and is there a way for me to make it so that the minimize and maximize and close don't flash, I would just like it to glow when I highlight them not flash repeatedly.

---

### Post by ad_267 on 2008-11-14
To control the flashing you can go to "Emerald Settings" and untick "Use Button Fade Pulse" in the Emerald theme manager.

---

