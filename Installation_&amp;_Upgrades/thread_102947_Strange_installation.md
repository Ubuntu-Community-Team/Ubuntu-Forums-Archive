---
title: "Strange installation"
date: 2005-12-13
forum: Installation &amp; Upgrades
---

### Post by Kalli on 2005-12-13
Everything basically worked fine until I booted the system and it boots to command line...which I found to be quite strange.  Any ideas of what may be going on?

There was also another thing though although I'm not sure if it effects this but I couldn't create a user account, everytime I would fill in the information it would just start over, again and again and again, so I just went on to the next step...

---

### Post by greenwom on 2005-12-13
did you do a server install?  Do you have a network connection?
try to type startx at the command line and see where your at with that.

i agree: add your hardware specs

---

### Post by 23meg on 2005-12-13
Please give details on your hardware, video hardware in special, and post your /var/log/Xorg.0.log file.

---

### Post by Kalli on 2005-12-13
Okay, it tells me that there is "no screens found"

My hardware is:

AMD XP 2500+ (barton)
on a Shuttle SK43G (with integrated graphics)

---

### Post by greenwom on 2005-12-13
This is kins of blind leading the blind but ---
Have you tried to  run 

sudo dpkg-reconfigure xserver-xorg 

this changes the settings in 
/etc/X11/xorg.conf

I had to get the specs from the manufacuter for my monitor

HorizSync 
VertRefresh 

it's a range number, do a search on xorg.conf and lo0ok at some others files to see an example.

---

### Post by Frymaster on 2005-12-16
kalli does the information here:

[http://www.ubuntuforums.org/showthread.php?t=89992](http://www.ubuntuforums.org/showthread.php?t=89992)

apply to you?

---

