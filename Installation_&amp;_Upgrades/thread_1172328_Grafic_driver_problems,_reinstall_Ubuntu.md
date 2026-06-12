---
title: "Grafic driver problems, reinstall Ubuntu?"
date: 2009-05-28
forum: Installation &amp; Upgrades
---

### Post by joppap on 2009-05-28
Hi!
When I start my computer and when Ubuntu is finnished loading I should get to the log in session. But after a installation of ATI catalyst all I get is strings and funny pattern of colors and cant do anything.
 
So I run the recovery mode and find a "try to autorepair grafic problem" or something like that in the recovery mode menu. But it didn't work.
 
Is it possible to back the system like microsoft windows? 
NOTE: I have to do this from the terminal in recovery mode "Drop to root shellprompt with network"
 
Or is it possible to reinstall ubuntu without losing my files in the home map?
or maybe get new drivers to my videocard and install it "apt-get install xxxxxx"
 
I'm a ubuntu noob =)
 
Thanks// Joppa

---

### Post by utnubuuser on 2009-05-28
I've heard the fglrx driver is not so good,  > apt-get remove fglrx --purge> apt-get install xserver-xorg-video-ati (or possibly radeonhd instead of ati. Then reboot.

---

