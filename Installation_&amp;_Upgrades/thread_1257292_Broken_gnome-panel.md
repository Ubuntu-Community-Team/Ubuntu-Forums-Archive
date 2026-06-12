---
title: "Broken gnome-panel"
date: 2009-09-03
forum: Installation &amp; Upgrades
---

### Post by tstorm007 on 2009-09-03
I was trying to upgrade some packages on my computer (running Hardy Heron) and I seem to have broken gnome-panel.  When I login, I get no toolbars, nothing happens when I right-click on the background.  I can ctrl+alt+f1 to go to a command prompt.  Anyway, I tried to do apt-get install --reinstall gnome-panel but I don't seem to be on the wireless either.  

Is there some way to access the network manager and get it working from the command line?  Is there a way to download these packages and install them off a cd or disk?  

Thanks,
Todd

---

### Post by imhotep59 on 2009-09-03
Hello,

Coul you give the result of: ```
nm-tool
```

---

### Post by bumanie on 2009-09-03
Your English is fine :). Try > sudo apt-get  --reinstall ubuntu-desktop followed by > sudo apt-get updateThen do > startx

---

### Post by imhotep59 on 2009-09-04
bumanie, I proposed the command nm-tool, because tstorm thought he had no wireless connection. But maybe you are right, he hasn't performed apt-get as a super user. However if he really has no network connection I am not sure that sudo apt-get will work ;)

tstorm, did you get error messages when trying to reinstall ?

---

