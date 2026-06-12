---
title: "Starting Terminal w/o menu?"
date: 2008-10-19
forum: General Help
---

### Post by flamey on 2008-10-19
I installed Linux (ubuntu) for the first time ever, was battling to get my wireless working and checking things out in general. I uninstalled the Evolution (?) mail client with it and a bunch of dependencies it decided to uninstall as well, and now I boot into a desktop with only my wallpaper and couple of files on it i saved there before.

I don't want to reinstall everything from scratch.

- is there a way to start Terminal in this state?
- once i'm in, how do I start that component management tool?
- what to I install back to get my normal desktop menues back?

:-) thanks in advance!

---

### Post by walkerk on 2008-10-19
Alt+F2

then run command:
```
gnome-terminal
```


now in terminal:
```
sudo apt-get install ubuntu-desktop
```

or simply try to run:
```
gnome-panel
```

Not sure what state your compuet is in...

---

### Post by scragar on 2008-10-19
press either alt+F2 and type ```
gnome-terminal
``` or use ctrl+alt+F1 to get a terminal(ctrl+alt+F7 to get back), and run
```
sudo apt-get install ubuntu-desktop
```
that should then ask you to reinstall all your dependencies.

Once that's done you will need to log out and in again(ctrl+alt+backspace = easiest way to do it)

---

### Post by flamey on 2008-10-19
thanks for quick reply guys. i got in with c+a+f1 (alt+f2 didn't do anything), but it wants to download 150 megs. im on a slow connections, its faster for me to reinstall ubuntu from scratch.

its pretty messed up that it uninstalls desktop when you trying to remove email app :-/

---

