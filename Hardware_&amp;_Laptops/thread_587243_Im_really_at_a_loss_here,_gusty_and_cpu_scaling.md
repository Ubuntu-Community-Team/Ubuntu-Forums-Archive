---
title: "Im really at a loss here, gusty and cpu scaling"
date: 2007-10-22
forum: Hardware &amp; Laptops
---

### Post by spotdog14 on 2007-10-22
Ok, so after a botched gusty upgrade i did a fresh install tonight. I either wrote down or saved everything i though i would need for a fresh install except for the little terminal command that i had to setup the cpu scaling for my Pentium-M lappy.

Anywho what i am talking about is when you have the cpu scaling gnome applet on your task bar, you should be able to left click on it to bring up the cpu frequency steps then at the bottom options like conservative, ondemand, powersaver etc. 

Anywho when i up in sudo modprobe speedstep-centrino i get "FATAL: Error inserting speedstep+centino etc etc etc, device or resource busy.

What to do? 

Thanks for any help you guys can give me!

---

### Post by spotdog14 on 2007-10-22
SWEET!!!!! It was on like page 10,000 of my search, i was just randomly clicking on posts and it came up, sorry to bother you guys, but here is the code that works for me.

> sudo dpkg-reconfigure gnome-applets

---

