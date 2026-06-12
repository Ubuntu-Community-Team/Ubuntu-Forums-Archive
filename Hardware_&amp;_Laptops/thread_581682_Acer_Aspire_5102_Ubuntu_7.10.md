---
title: "Acer Aspire 5102 Ubuntu 7.10"
date: 2007-10-19
forum: Hardware &amp; Laptops
---

### Post by vdox on 2007-10-19
Whether or not the proprietary drivers are in use I cant enable the other display nor desktop effects. Choosing only the laptop screen will result in showing the same pic in both display even tho the other one isnt supposed to be in use.

I got this working in Ubuntu 7.04 using BigDesktop but now that I have installed 7.10 I wouldve hoped that I could simply use the integrated screens and graphics option.

Anyone have any ideas?

Thanks in advance

---

### Post by dptxp on 2007-10-19
Do this:

First, run sudo gedit /etc/X11/xorg.conf

Put 1 instead of 0 in the last section so it looks like this:

EndSection
Section "Extensions"
Option "Composite" "1"
EndSection


Then try again.. if it doesn't work... then do:

sudo apt-get install xserver-xgl

Restart X by doing cntr-alt-backspace


I am assuming that you are using Proprietary drivers for your 

EDIT : I picked this up from some other thread, worked for me on ACER 5101.



__________________

---

### Post by vdox on 2007-10-19
The first one did nothing for me: Those options were not in the file and adding them doesn't help.

The latter however makes it possible to activate the desktop effects and they work like a charm. But the extended desktop still doesn't work :(

Tho the effects are cool I would take the extended desktop over them any time. So does anyone know a way how to enable it?


BTW: There's something wrong with the effects on, there's no close/maximize/minimize-buttons in the windows and they cannot be dragged....

---

