---
title: "Installed ubuntu, can only boot from recovery mode"
date: 2008-12-06
forum: Installation &amp; Upgrades
---

### Post by Silentzor on 2008-12-06
Hello,
I just installed ubuntu 8.10 on my laptop, and there seems to be an issue with my graphics card (NVIDIA Geforce 9300M GS). I entered the installation in safe graphics mode, because whenever i would enter it originally after the splash i was only seeing a black screen. Same thing happens now! Whenever i log ubuntu regularly i see a black screen after the splash, but when i log from recovery mode everything works fine (although i have low graphics). Any advice how to solve this? Thanks.

---

### Post by Sealbhach on 2008-12-06
I would suggest trying this. Boot up in normal mode. When you get to the black screen, hit Ctrl+F2.  Log in.

Type:

```
sudo /etc/init.d/gdm stop
sudo dpkg-reconfigure xserver-xorg
sudo /etc/init.d/gdm start

```
.

---

### Post by Silentzor on 2008-12-13
I tried hitting Ctrl+F2 but I still can't see anything

---

### Post by Partyboi2 on 2008-12-13
Ctrl+Alt+F2 is probably what Sealbhach meant.

---

