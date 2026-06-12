---
title: "Login Screen not appear"
date: 2008-11-06
forum: General Help
---

### Post by bimaljr on 2008-11-06
Hi
I have installed Ubuntu 8.10 and everything works fine. The compiz effects are also enabled by default.. thanks to all Ubuntu developers. 

But sometimes the loading screen becomes bad. I don't know why. Sometimes only the big half "Ubu" will be on screen, sometimes cutted the loading bar. So I decided to install "Startup Manager" to fix the screen resolution of loading screen. After set it to  800x600 the loading screen is working perfectly. But the Login Screen disappear. my CRT Monitor displays "Cable unplugged"

How to solve this ?

---

### Post by bimaljr on 2008-11-11
No one here...?

Please guys

---

### Post by L815 on 2008-11-11
Sounds like the startup manager messed up your video driver, or doesn't use it properly when booting. 

Try pressing CTRL + ALT + F1, if you get into a terminal, try typing
```
startx
```
or 
```
gdm
```


If nothing works, try uninstalling the startup manager.

---

### Post by bimaljr on 2008-11-14
I have uninstalled ubuntu 8.10 and reinstall it.
The the prob stil exits same.

I have tried alt+ctrl+F1 but nothing happens.

---

