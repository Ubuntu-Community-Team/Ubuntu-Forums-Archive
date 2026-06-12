---
title: "Toshiba 4010 &amp; Ubuntu 9.04 screen size problem"
date: 2009-06-25
forum: Hardware
---

### Post by tedster4u on 2009-06-25
I've recently re-installed XP on the old [COLOR=RoyalBlue]Toshiba Portege 4010[/COLOR] laptop. While I was at it I added a partition on which I installed [COLOR=DarkOrange]Ubuntu 9.04[/COLOR] . It runs fine( all the software works, get online fine) BUT the display/screen size options are only up to 800 x 600 in the display choices.
This seems to be a problem on previous incarnations of linux distros and this computer but I find no references to how to fix this with this install (9.04).
I've scoured for something and tried with my [COLOR=SeaGreen]EXTREMELY[/COLOR] limited knowledge of linux to implement fixes that others have posted to no avail.
Can someone tell me (step by step please) how to tell the linux operating system to use the **1024 x 768** native screen resolution in full? Please assume I don't really have any foreknowledge of how to do this. 
I'm able to call up a terminal on screen and type in commands or select text and paste it into places in some(gulp) config file but this hasn't helped yet. Some mention VESA some mention "displayconfig-gtk" but no attaempt yet does anything to increase the choices.
I read one post that says to use the live cd option and do things then which I tried but the config file instructions  command was not recognized.

Toshiba Portege 4010 , trident cyberblade graphics, Pentium III 933, 512MB, 20GB partition for Linux
XP on other partition
Why is this  seemingly basic necessity (screen /display dimension choices) not covered the install? Isn't 800 x 600 kinda ancient? I can understand it as a default. For all its shortcomings and crashiness I've never had screen resolution concerns with Windows ... or Mac  or my Amiga .

---

### Post by riposte63 on 2009-07-07
A bit of hand editing of the file /etc/X11/xorg.conf might be required.

I found this link that shows how:
[http://free-linux-trick.blogspot.com/2009/06/linux-mint-gloria-on-toshiba-portege.html](http://free-linux-trick.blogspot.com/2009/06/linux-mint-gloria-on-toshiba-portege.html)

Hope that helps

PS Don't cut and paste it

---

