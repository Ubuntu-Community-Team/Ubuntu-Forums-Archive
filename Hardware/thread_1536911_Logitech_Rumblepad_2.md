---
title: "Logitech Rumblepad 2"
date: 2010-07-22
forum: Hardware
---

### Post by echo314 on 2010-07-22
To get this working in 10.04 x86-64, do I need to use a program such as "pSX" that I see mentioned in many threads? I am not looking to use it through wine, just to remap controls for linux games. 

I can't seem to get it recognized, I have no idea to see if the computer even sees it, much less if it can use it.

---

### Post by CyBerRatVM on 2010-09-09
I have the same controller and this is what i have done in Ubuntu 10.04 - Gnome.[INDENT]```
sudo apt-get update
sudo apt-get install joystick
```[/INDENT]Now you may have to restart(I did not). Find the device.[INDENT]```
ls /dev/input
```Looking for a js# device, mine was js0.

[/INDENT]I used;[INDENT]```
jstest /dev/input/js0    
```Leftstick = axis 0-1
Rightstick = axis 2-3
Leftpad = axis 4-5

Axis follow x,y ordering.
[/INDENT]use ```
'jscal -c /dev/input/js0' 
```to set each axis 0-5; min, max and center.

hope that helps since that is as far as i have been for now.

Cheers

---

