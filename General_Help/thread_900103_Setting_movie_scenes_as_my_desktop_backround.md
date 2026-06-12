---
title: "Setting movie scenes as my desktop backround?"
date: 2008-08-25
forum: General Help
---

### Post by Pascal11110 on 2008-08-25
I was wondering if it would be possible to display some scenes from movies as my desktop image, like behind the icons and playing through the clips i put on their constantly. I know it will be a drain on my processer, but I have a nice home-built system, so no biggie. Know any good programs?

---

### Post by Vadi on 2008-08-25
xwinwrap is your friend... however it's terminal-only. Give gwinwrap ([click]("http://code.google.com/p/gwinwrap/")) a try, which is a GUI for it.

xwinwrap is pretty powerful itself too, you can even make it so it sets your webcam image as a background... here's the code for that:

> xwinwrap -ni -o 0.40 -fs -s -sp -st -b -nf -- mplayer -wid  WID -quiet -fps 15 tv://  -vf mirror

I don't remember what do all arguments there mean, but 0.40 means 40% transparency - you might need to play around with it to however it works best for you.

---

### Post by Pascal11110 on 2008-08-26
thanks a lot

---

