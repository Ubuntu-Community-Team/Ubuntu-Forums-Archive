---
title: "Kubuntu+KDE4 download error"
date: 2008-09-17
forum: General Help
---

### Post by Franz84 on 2008-09-17
I tried to install Kubuntu+kde4, but it stops with "error download" after a few seconds. It happens just with this option selected. Is there any solution, please?
Thanks

---

### Post by Hyper Tails on 2008-09-17
try this
```
sudo apt-get update
```

then

```
sudo apt-get install kubuntu-kde4-desktop
```

hope this helps ;)

---

### Post by speed_pheak on 2008-09-21
She is correct. The WUBI installer will not download the image needed for Kubuntu-KDE 4. Apt-get command line tools will not assist in Windows. I am trying to manually download the image and place it in the same directory as WUBI to see if it will go...

---

### Post by IshusMedia on 2008-10-02
So, did it work? And where should the package be placed in the installation?

---

### Post by ago on 2008-10-03
Installing KDE should now give KDE4 and not KDE3.5 (or at least in wubi 8.10)

[http://wubi-installer.org/devel/minefield/Wubi-8.10-rev510.exe](http://wubi-installer.org/devel/minefield/Wubi-8.10-rev510.exe)

---

### Post by ago on 2008-10-03
If you are after KDE4, Wubi 8.10 is recommended. Link is above.

---

