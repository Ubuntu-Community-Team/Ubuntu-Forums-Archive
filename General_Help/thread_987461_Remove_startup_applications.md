---
title: "Remove startup applications"
date: 2008-11-19
forum: General Help
---

### Post by ravi.xolve on 2008-11-19
Kmix, adept notifier and knetworkmanager start automatically at very KDE startup in Kubuntu 8.10 . Even though I quit them before exiting KDE. Please help me. Obviously if they do not load I can save on startup time.

---

### Post by aysiu on 2008-11-19
I don't know if this applies to KDE 4, but this page might help you find where the startup programs are hiding:
[http://docs.kde.org/cgi-bin/desktopdig/search.cgi?show=stable/en/kdebase-workspace/kcontrol/autostart/index.html&collection=en&include=stable&q=autostart](http://docs.kde.org/cgi-bin/desktopdig/search.cgi?show=stable/en/kdebase-workspace/kcontrol/autostart/index.html&collection=en&include=stable&q=autostart)

Sorry. I don't have KDE on me.

---

### Post by ravi.xolve on 2008-11-20
I had already checked these and they are of no help :confused:

---

### Post by victor.cighir on 2009-03-14
My Autostart folder is empty....

I wonder how can it be, that searchin on the internet for something as simple as removing some startup application removal can yield so few results...

I've been using *Ubuntu distros for more than a year and as a normal user I feel satisfied with rather old HW.

But this kind of simple issues keep new users away from the fun of ubuntu. 

Please! Does anybody know how to remove apps from the startup. I got sick and tired to manually close them every time I boot my computer...

---

### Post by Thomasimov on 2009-07-31
Maybe it comes a little bit too late, but I'll still give it a try...
Try to type :
```
locate kmix
```
You should find an autostart file :
/usr/share/autostart/kmix_autostart.desktop
which you can modify (or delete, maybe saving it first) in order for Kmix not to be launched with KDE.
Have fun !
Thomas

---

