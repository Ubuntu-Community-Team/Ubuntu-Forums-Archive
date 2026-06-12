---
title: "Mouse freezes/turns off"
date: 2012-04-07
forum: Hardware
---

### Post by bakkerthehacker on 2012-04-07
[FONT=Verdana]I have a laptop and I use a logitech wireless M505 mouse.  The cursor on the screen will occasionally freeze and stop responding when I try to move it.  This only occurs if I leave the mouse sitting still for a bit.  The touchpad on my laptop still responds instantly, even when the wireless mouse is not responding.  

I have a wired mouse that I tried on my laptop.  It too freezes after a small amount of inactivity.  However, it completely refuses to respond and the LED on the bottom of the mouse turns off.  Only when I click with this mouse does it respond.  h

Is there something that is putting my mouse to sleep and causing these issues? 

This problem occurs in bo[/FONT]th 11.10 and 12.04 beta 2.  If there is any other information that I should provide, let me know.

---

### Post by EmilyRose on 2012-04-17
Mine seems to do the same thing with 12.04, but only very recently. Thus far it seems to have happend when my computer went into suspend *while plugged in* - its very odd, as suspend has previously worked fine.

---

### Post by ekulasek on 2012-04-18
Try disabling laptop-mode tools. 
vim /etc/laptop-mode/laptop-mode.conf and set
ENABLE_LAPTOP_MODE_TOOLS=0

---

### Post by EmilyRose on 2012-05-01
I'm still having this problem, but I have found a way to 'fix it', sort of. If I uncheck "Disable touchpad while typing" in settings-Mouse and Touchpad then suspend works... but I get my typing screwed up w/ the mouse :p

---

