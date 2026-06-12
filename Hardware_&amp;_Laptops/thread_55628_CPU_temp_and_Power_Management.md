---
title: "CPU temp and Power Management"
date: 2005-08-09
forum: Hardware &amp; Laptops
---

### Post by ux5b2 on 2005-08-09
Hello.

Ive been running Ubuntu for a little while now and everything is running pretty smoothly except for a few concerns I have.  I noticed that my laptop (Dell 700m) seem to run hotter in Ubuntu than it did when I ran WinXP.  I did a lot of searches through the forum and managed to get the laptop to suspend the RAM when the lid is shut.  I also disabled apmd due to some people's suggestions.  However, my computer still seems to run too hot.  One forum I found listed this command: cat /proc/acpi/thermal_zone/THRM/temperature  which prints out a temperature (Im not sure of what).  I tried it and but it turns out I do not have a THRM directory but instead have THRC and THRS.  I got the temperature readings from both and they seem a bit too high at time (~55C).  Could someone please explain to me what these two temperature readings represent and what I can do to help cool down my laptop.  Ive tried in the past find out the current temperature of my cpu but every tool I ran into told me that my motherboard does not support temperature reading which is also why I am confused about the results of the command I described (is there any way I can get an accurate reading of my current cpu temp?).  So basically I want some advice on getting my computer to run cooler and some explanation on whats going on.  Thank you very much for your time and any input is appreciated.

---

### Post by andmalc on 2005-08-09
I have the same problem as the OP, and in fact my laptop (ThinkPad R30 - Celeron Coppermine) is unable even to finish installing before a "critical temperature 82C exceeded" warning is printed to the console and it shuts down. 

Debian and WindowsXP run pretty hot on this computer but not as hot as Ubuntu.

Hope someone can help us here.

---

### Post by andmalc on 2005-08-09
Replying to my own post: Finallly got Ubuntu to finish installing.  

When idling,

cat /proc/acpi/thermal_zone/THR2/temperature shows 77 degrees C.

which is just short of the shutdown temperature.

---

### Post by andmalc on 2005-08-09
Replying to my own post: Finallly got Ubuntu to finish installing.  

When idling, the output of 

cat /proc/acpi/thermal_zone/THR2/temperature 

is 77 degrees C, just short of the shutdown temperature.

---

### Post by jepong on 2008-03-25
try to install powertop

> [http://www.ubuntugeek.com/saving-power-on-intel-hardware-using-powertop.html](http://www.ubuntugeek.com/saving-power-on-intel-hardware-using-powertop.html)

---

