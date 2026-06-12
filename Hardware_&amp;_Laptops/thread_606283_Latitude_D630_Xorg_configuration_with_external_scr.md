---
title: "Latitude D630 Xorg configuration with external screens"
date: 2007-11-07
forum: Hardware &amp; Laptops
---

### Post by qwill on 2007-11-07
I'm struggling to configure Gutsy Gibbon on a latitude D630 with Nvidia quadro 135M card.

I switched to the nvidia driver. everything is fine when I use the laptop undocked with the internal screen.

Its another game while trying to use ubuntu while docked :

* I have 2 external screens (Dell 2007fp) one via dvi; the other via vga.
* When X11 starts; my external display goes black. (no video input). I realized that the internal laptop screen was on; even if the lid is closed.

I tried to tweak the configuration with the nvidia-setting app; but no success. I guess I have to manually make 3 display sections inside the xorg.conf file; but have no clue...

Is there anyone that succeeded dealing with this issue ?

Thanks in advance;
Qwill:confused:

---

### Post by qwill on 2007-11-08
Uodate - Still struggling with displays.
There is a good tutorial on nvidia twinview available at : [http://www.ublug.org/howtos/ubuntu/twinview/twinview-howto-laptop.html](http://www.ublug.org/howtos/ubuntu/twinview/twinview-howto-laptop.html)

But still not working in my case.
When booting from the dock; I got the text display in my DFP-1 external monitor. 
When I start X; its the laptop internal DFP that displays the screen ....
With the Fn-F8 keys; I am able to switch my internal laptop display to the external CRT display; but the external DFP display still remains off...

Any Xorg wizards around here ?

-==Qwill==-

---

