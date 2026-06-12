---
title: "Enabling Joystick"
date: 2005-04-20
forum: Hardware &amp; Laptops
---

### Post by mdbarton on 2005-04-20
I noticed a few threads on getting joysticks to work, but no answers.  I have an analog joystick plugged into the gameport on my soundcard.  Below are the few steps needed to get this working:
edit **/etc/modules** and add the following lines:
```
analog 
joydev
``` 
Now modprobe the two modules (type the following into a terminal):
```
modprobe analog
modprobe joydev
```
Now (install it first if you haven't already) run tuxracer and have hours of fun!

---

