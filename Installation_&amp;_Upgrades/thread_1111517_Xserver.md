---
title: "Xserver"
date: 2009-03-30
forum: Installation &amp; Upgrades
---

### Post by Linux000 on 2009-03-30
I have a small computer (400 MHz Celeron, 512 MB of ram, 66 MHz Graphics Card) and it has the terminal linux (from the Alternate Install) on it and I decided to try and install GNOME, after rebooting, I type ```
startx
```
and the screen flashes twice, then, nothing, not even numlock on the keyboard responds, I am pretty sure there is something wrong in xserver configuration, but I don't know where it is, or what to modify. Also, if I uninstall GNOME, and install xserver, type ```
startx
``` it does the same thing.

---

### Post by Sam Lars on 2009-03-31
Could you post what you find in the file
```
/var/log/Xorg.0.log
```
If you don't want to post everything,
```
cat /var/log/Xorg.0.log | grep EE
cat /var/log/Xorg.0.log | grep WW
```
would be useful.

---

