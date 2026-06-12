---
title: "Synatpic Touchpad not working"
date: 2005-09-27
forum: Hardware &amp; Laptops
---

### Post by azimzores on 2005-09-27
OK kinda a new comer to Ubuntu and so far the little i have seen i like, especially coming from freebsd.. My problem now is with this custom laptop is the touchpad does not work. I have tried multiple configs using the xorgconfig. Still nogo, read forum posts and bug tracks about pressing the shift key ect not working. Not sure whats going on. When i looked at the xorg log i see that it says synaptics touchpad for an input device but when ever X starts up just get the cursor in middle of screen no movement and no mouse clicks. I hope this is a simple fix so i can leave this dreaded windows enviroment. Its bad when you have to use windows as a last resort OS. All help and comments appreciated. Thanks in advance.

---

### Post by spd106 on 2005-09-28
Could you please post some more information, such as the relevent parts of **dmesg** and **xorg.conf** and what changes you've already tried?
Does a PS/2  or USB mouse work?
Do you know the make/model of any parts of the laptop?

---

### Post by azimzores on 2005-09-29
:o ok heres the only entry in DMesg that refers tothe mouse or synaptic touch pad:
mice: PS/2 mouse device common for all mice

and here is the listing from Xorg.0.log
(**) |-->Input Device "Configured Mouse"
(**) |-->Input Device "Synaptics Touchpad"

has some font error afterwards but owell.

Yes USB mice do work.. just the touchpad on this Laptop does not work.

---

### Post by darius_underhill on 2005-09-29
[QUOTE=azimzores]OK kinda a new comer to Ubuntu and so far the little i have seen i like, especially coming from freebsd.. My problem now is with this custom laptop is the touchpad does not work. I have tried multiple configs using the xorgconfig. Still nogo, read forum posts and bug tracks about pressing the shift key ect not working. Not sure whats going on. When i looked at the xorg log i see that it says synaptics touchpad for an input device but when ever X starts up just get the cursor in middle of screen no movement and no mouse clicks. I hope this is a simple fix so i can leave this dreaded windows enviroment. Its bad when you have to use windows as a last resort OS. All help and comments appreciated. Thanks in advance.[/QUOTE]

Have you tried disable a "Use Legacy USB devices" feature in your system's BIOS?

---

