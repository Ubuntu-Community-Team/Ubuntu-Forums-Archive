---
title: "[SOLVED] Touchscreen working on HP Pavilion tx1000 series with Intrepid"
date: 2008-11-16
forum: Hardware
---

### Post by vishalrao on 2008-11-16
I posted this at [https://lists.ubuntu.com/archives/ubuntu-in/2008-November/004221.html](https://lists.ubuntu.com/archives/ubuntu-in/2008-November/004221.html)

In short:

> Run "sudo apt-get install xserver-xorg-input-evtouch" in a terminal and run the resulting "Calibrate Touchscreen" applet in the System->Administration menu to get touchscreen working!

Hope it helps.

---

### Post by creatureofthedark on 2008-12-13
im getting 

```
creature@creature-Tablet:~$ sudo apt-get install xserver-xorg-input-evtouch
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package xserver-xorg-input-evtouch
creature@creature-Tablet:~$ 

```


any idea why?

---

### Post by Alejandro Nova on 2008-12-16
Marvelous.

Let's hope they [add evtouch 0.8.8 to Intrepid repos]("http://https://bugs.launchpad.net/ubuntu/intrepid/+source/xf86-input-evtouch/+bug/222164"), to make our ROTATED touchscreen work flawlessly once and for all.

Thanks for the howto!

---

### Post by waspbr on 2008-12-27
@ creature, check if your repos are enables at System>Admin>Software sources
mu restricted, universe and multiverse are enabled... if that doesn't work try enabling the proposed updates at the updates tab. 


anyway has anyone managed to make the screen rotation work?

I mean, the method in my signature makes it rotate but it doesn't change the resolution for the mouse and touchscreen...

---

