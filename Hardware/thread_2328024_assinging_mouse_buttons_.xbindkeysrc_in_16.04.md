---
title: "assinging mouse buttons: .xbindkeysrc in 16.04"
date: 2016-06-16
forum: Hardware
---

### Post by djtetsu on 2016-06-16
Hey guys, 

Trying to get the most out of my mouse.  Hopefully I can get some help.

I was able to assign my scroll button (button:2) as the enter key on Ubuntu 12.04 with adding this to my .xbindkeyrsc (under home):

"/usr/bin/xte 'key Return' &"
b:2

How to do this in **16.04**?? Or maybe I'm just forgetting something?

Thanks guys.

---

### Post by djtetsu on 2016-06-17
Solved! 

Just had to install xte:

sudo apt-get install xautomation

My mouse scroll button does RETURN's now. Woohoo!

---

