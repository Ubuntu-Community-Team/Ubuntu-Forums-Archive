---
title: "Can't turn off LCD Lisplay"
date: 2008-12-05
forum: Hardware
---

### Post by PeregrinGo on 2008-12-05
Hey all,

I have a Dell XPS m1530 that I've been running Hardy on for about 5 months. Even though I have the Power Manager set to shut off the screen when the laptop lid is closed, this function has NEVER worked. This is a major issue for me. Does ANYONE know how to fix this? All help is appreciated!!!

---

### Post by PeregrinGo on 2008-12-09
*bump*

---

### Post by razy60 on 2008-12-09
I usually tell my laptop to suspend, then close the screen, never quite trusted the, turn screen off when lid is closed, even in xp. (and that was using the Dell tools utility).
You could also try "lock  screen" with no screen saver just blank screen.
I know its not ideal but they work for me on a Dell 6400.

Raz

---

### Post by tarps87 on 2008-12-09
If you set to do something else like going to standby does this work? The screen should be controlled by the hardware not the OS, on all my laptops this is the case. If standby does not work it maybe that the lid sensor is broken.

Edit: Reading about your laptop it seems the screen is not hardware controlled and I can not make out if there is even a sensor. Setting it to standby will reveal if there is a sensor, if this is the case you may need to right/find a scrip to turn the screen off as I don't believe this is built in Ubuntu. It would appear there a third-party programs for windows as other users have found this problem. There should be a script somewhere so I suggest looking for one, I will post back if I find anything else out

---

### Post by PeregrinGo on 2008-12-12
Bump

---

### Post by stevoo on 2008-12-12
hey , i have the same problem ... 

nothing seemed to help me.

I closed the screen and it would turn of and back on immediately. In the end i wrote a small bash script that turned the screen off. I pressed that and i said do nothing when close screen as it would end up starting it again and that solve my problems

> #! /bin/bash
gnome-screensaver-command -l
sleep 1
/usr/bin/xset -display :0.0 dpms force off

Save it in a bash script make it executable and put it on your top screen and press it ! 

That worked for me ... nothing else. ... until i reinstalled fixed the issue... but i think it is slowly coming back !

---

### Post by PeregrinGo on 2008-12-12
> **stevoo said:**
> hey , i have the same problem ... 

nothing seemed to help me.

I closed the screen and it would turn of and back on immediately. In the end i wrote a small bash script that turned the screen off. I pressed that and i said do nothing when close screen as it would end up starting it again and that solve my problems



Save it in a bash script make it executable and put it on your top screen and press it ! 

That worked for me ... nothing else. ... until i reinstalled fixed the issue... but i think it is slowly coming back !
If you use that script, what do you do to turn the display back on short of restarting?

---

### Post by PeregrinGo on 2009-01-25
*bump*

---

