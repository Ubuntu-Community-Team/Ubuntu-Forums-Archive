---
title: "Upgraded from 8.10 to 9 ...missing gnome panels"
date: 2009-04-25
forum: Installation &amp; Upgrades
---

### Post by evolx10 on 2009-04-25
I just spent the better half of this day upgrading my Ubuntu, from 8.04 to 8.10, then finally to 9.. 

9 loaded up for the first time and for some reason i have no gnome panels. 

I got a few applications up , and when i minimize them you see them scoot off to the bottom( where my old panels lived-ms style) i searched around the forums and only thing i found that made any difference was reseting the gnome panels to the original

```
gconftool-2 --shutdown
rm -rf ~/.gconf/apps/panel
pkill gnome-panel
```
now when i minimize an app it shoots off to the top. so im gussing the panels are living there now, all invisible. 

i have to use ctrl-alt-f1 to get to the terminal, or shell whatever, when i type **gnome-panel** i get a error returned  **cannot open display**..
My video card, and compiz all work, i can turn on desktop fx and all..
One thing i did notice that might not be anything at all but i guess worth mentioning. When i run top.. all of the running processes seem to start with a **k** i don't know why i noticed that , but im new to this OS and thought the **K** stood for kubuntu or w/e..

---

