---
title: "envyng: can neither install nor uninstall!"
date: 2009-03-19
forum: Installation &amp; Upgrades
---

### Post by anderssl on 2009-03-19
Hey,
I'm a newb and I guess I've been clumsy, but it'd be great if someone could help me. I tried to install envyng, but didn't realize that my hard drive was completely full. So I got a bunch of error messages half-way through the installation, and of course it didn't work. So then I made room on the drive, and tried to install again. But it says envyng-gtk is already at the latest version, so no new packages need to be installed. I tried to uninstall, by the descriptions on the envy website, but I guess I followed the instructions for the old version of envy... and it seems I am not managing to completely uninstall it (cause the machine still won't let me re-install it). So, it seems I got myself stuck... Anyone know how to get completely rid of envyng-gtk, so I can start over???

---

### Post by Partyboi2 on 2009-03-19
Open a terminal (Applications>Accessories>Terminal) and try
```
sudo apt-get remove envyng-gtk  envy envyng
```
then reinstall with
```
sudo apt-get install  envyng-gtk
```

---

