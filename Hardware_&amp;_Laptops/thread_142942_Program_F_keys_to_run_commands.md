---
title: "Program F keys to run commands"
date: 2006-03-11
forum: Hardware &amp; Laptops
---

### Post by m.musashi on 2006-03-11
I found a nice little trick to get my touchpad to turn off when I use a bluetooth or wired usb mouse. It's manual but I just do ```
synclient touchpadoff=1
``` What I'd like to know is how I can teach an F key to do this when ever I want. Even better if it would toggle between ```
synclient touchpadoff=1
``` and ```
synclient touchpadoff=0
```
Any thought?
Thanks

---

### Post by Aewheros on 2006-03-11
Try install and use keylaunch. Haven't tried it myself, but it is supposed to be able to bind commands to hotkeys.

---

### Post by m.musashi on 2006-03-11
Yeah, that sounds like the thing. I've installed it (I think) but I can't figure out how to use it. I googled a bunch but can't find anything that explains how to use it. When I try and use it I get ```
jim@ubuntu:~$ keylaunch
Could not open the configuration.

keylaunch 1.3.3
2006 (c) Stefan Pfetzing <dreamind@dreamind.de>
Usage: (null)
keylaunch, has no Options at all.
You will need to create a ~/.keylaunchrc in order to use it.
```
I'm not sure what it means by "create a ~/.keylaunchrc". I assume it's some sort of config file but how to create it and what to put in it are the questions.

---

### Post by Liquid1101 on 2006-03-11
~/.keylaunchrc would refer to a hidden folder in your home directory.

---

### Post by ranf on 2006-03-12
There seems to be an example config file:
/usr/share/doc/keylaunch/examples/example_rc

Just copy it to your home directory as `.keylaunchrc' and edit to your liking.

---

### Post by engla on 2006-03-12
As an alternative, Metacity (The gnome window manager) can be used to bind commands to keys if you edit the gconf settings for metacity.

---

