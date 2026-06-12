---
title: "Backlight stays on when standby/suspend/off"
date: 2006-02-17
forum: Hardware &amp; Laptops
---

### Post by palomar on 2006-02-17
I have set in KDE powermanagement to let the screen of my laptop go standby/suspend/off after x minutes. But, after x minutes the screen goes blank and the backlight stays **on**. I have had this problem with several linux distributions and now it is the same with Ubuntu. I have found other topics in this forums about this problem, but no sollutions :( 

Other facts:
Laptop: Toshiba 1800/100 (celeron 800, trident cyberblade VGA)

The command "xset dpms force off" doesn't work (blank screen with backlight on). In xorg.conf there is still an option "DPMS" set.

Does anyone have a sollution for this?

---

### Post by palomar on 2006-02-20
Now I've found a tool in the repositories (toshset) wich I can use to turn off my LCD using the command "sudo toshset -bl off".

How can I use this command in combination whit a screensaver (or something like that) to turn off the screen after xx minutes and turn it on when I hit a key?

---

