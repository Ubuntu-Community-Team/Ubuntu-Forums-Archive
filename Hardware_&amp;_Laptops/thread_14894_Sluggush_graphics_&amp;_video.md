---
title: "Sluggush graphics &amp; video"
date: 2005-02-10
forum: Hardware &amp; Laptops
---

### Post by Napper on 2005-02-10
Hi everybody,

   after upgrading from Warty to Hoary I did face some display problems, regarding resolution etc with my built in Intel Extreme Graphics 2. I finally do seem to have resolved it to the point where X recognizes my hardware and puts me back to 1280 x 1024 but an issue remains: The graphics are awfully slow, especially movies. I do not want to reinstall Warty as Hoary did fix some issues for me (especially Tomboy) but I am beginning to despair over these slow graphics. Could somebody offer me some pointers, pieces of advice-like of where to start looking for the problem? I am using x.org as a server, though reinstalling xfree brought the same issues (worked fine when I did install it from CD, though.)

This issue aside, Ubuntu seems to be the holy grail of Linux at the moment (for me that is). Made me fall in love with Gnome... :)

In hopoe for reply,

Napper

---

### Post by ubuntu_demon on 2005-04-01
Does it work now ?

I'm thinking of getting :
Asrock 775i65GV / Intel 865GV chipset / Integrated Intel Extreme Graphics 2

see :
[http://www.ubuntuforums.org/showthread.php?t=22880](http://www.ubuntuforums.org/showthread.php?t=22880)

---

### Post by tyreth on 2005-04-13
Regarding playing dvd's, try:
hdparm -d 1 /dev/hdc

or whatever your dvd drive is.

---

