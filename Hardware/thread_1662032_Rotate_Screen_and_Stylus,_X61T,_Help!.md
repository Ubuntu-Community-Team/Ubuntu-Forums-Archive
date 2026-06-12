---
title: "Rotate Screen and Stylus, X61T, Help!"
date: 2011-01-07
forum: Hardware
---

### Post by bradyboo222 on 2011-01-07
My dad bought an X61T off of craigslist for cheap but he could never start up Vista. Anyways it was sitting around the office for a while and so he let me have my way with it.

Background: The X61T has a wacom stylus that is currently working brilliantly. I wanted to get as much out of the tablet experience as possible so I got the rotate screen button to function properly. I am using Natty.

The Problem: When the screen is rotated the stylus to screen mapping doesn't rotate. So if I rotate the screen 180 degrees, the the cursor is on the opposite side of the screen as the stylus.

I have found only the following link on the topic:

[http://www.thinkwiki.org/wiki/Installing_Ubuntu_8.10_(Intrepid_Ibex)_on_a_ThinkPad_X61_Tablet#Rotate_screen_when_turning_into_slate_mode]("http://www.thinkwiki.org/wiki/Installing_Ubuntu_8.10_(Intrepid_Ibex)_on_a_ThinkPad_X61_Tablet#Rotate_screen_when_turning_into_slate_mode")

I am pretty new to this and I don't know how to execute the instructions on this page. Can someone translate these instructions into terminal code that I can copy and paste. 

Also I don't know if these instruction will work for Natty.

---

### Post by Favux on 2011-01-07
Hi bradyboo222,

That script won't work for you right now because it uses the old device names stylus and eraser.  I gather you don't have touch.  You'd need to find what your current "Device names" are by entering in a terminal:
```
xinput --list
```
and substituting the "Device names" that gives you, with quotes, for stylus and eraser.

Or you can use method 1 or 3 on the [Rotation HOW TO]("http://ubuntuforums.org/showpost.php?p=6274392&postcount=1").  Since you don't have touch in a method 1 script remove the xsetwacom touch lines.

---

### Post by bradyboo222 on 2011-01-07
Thanks a Million! I got it working.

---

### Post by Favux on 2011-01-07
Great!  Nice work.

---

