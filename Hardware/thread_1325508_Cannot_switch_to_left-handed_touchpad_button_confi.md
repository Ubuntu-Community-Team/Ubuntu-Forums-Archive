---
title: "Cannot switch to left-handed touchpad button configuration in Karmic"
date: 2009-11-13
forum: Hardware
---

### Post by AndyCooll on 2009-11-13
I have an HP Advent 6553 laptop. Following the installation of Karmic Koala (in my case 64-bit) I can't seem to switch the touchpad buttons to the left-handed configuration. And for left-handed folk this becomes a pretty important and fundamental problem!

I can go to System > Preferences > Mouse and change that to display "Left-handed" mouse orientation, but it has no effect. Is anyone else having this problem? And if so, has anybody found a fix?
The only (sort of) fix I've found somewhere is typing the following in to the command line:
```
xinput set-button-map "SynPS/2 Synaptics TouchPad" 3 2 1
```
This does work! Obviously though this is an on-the-fly fix and has to be typed in each time I reboot, which isn't ideal.  

This is a regression introduced since Jaunty. I've used Ubuntu on various laptops over the years without these problems. I read somewhere that it was related to the gnome-settings-daemon. Again, can anyone confirm this (or not).

:cool:

---

### Post by studiowolff on 2009-11-16
Hi, same problem here....thanks for the tip.

---

### Post by Dr. C on 2009-11-21
I have the same problem also. Is there a way to make this permanent by editing a configuration file?

---

### Post by ChrisLovesit on 2009-11-23
You can automate AndyCooll's fix as follows:

Save the following two lines as a script (say, lefthandedtpad)

#!/bin/bash
xinput set-button-map "SynPS/2 Synaptics TouchPad" 3 2 1

Make the script executable (chmod +x lefthandedtpad) then add it
to your Startup Applications (System/Preferences/Startup Applications)

Reboot, and your mouse will be left-handed. It will also stay left-handed
every time you boot.

---

### Post by marcopl on 2009-11-24
chris you wouldnt know how to load a driver/ module automatically do u? see thread [http://ubuntuforums.org/showthread.php?p=8377110#post8377110](http://ubuntuforums.org/showthread.php?p=8377110#post8377110)

---

### Post by Don_Nadie on 2009-12-04
[LEFT]While *[ChrisLovesit]("http://ubuntuforums.org/member.php?u=963126")*'s script works, why should it be necessary? I didn't have this problem on my 32 bit Dell Inspiron 6400 when I was running Ubuntu 9.04 on it.
[/LEFT]
 
I'm no Window$ worshiper, but this is the just the sort of thing that keeps me away from Linux unless I'm feeling particularly masochistic. Window$ has shortcomings out the wazoo, but boy, does my touchpad ever work better in Window$ than in Linux!

---

### Post by caprilo on 2009-12-15
I can confirm this bug in Karmic.

---

