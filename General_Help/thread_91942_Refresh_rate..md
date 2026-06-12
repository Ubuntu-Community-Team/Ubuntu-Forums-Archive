---
title: "Refresh rate."
date: 2005-11-18
forum: General Help
---

### Post by ragtag on 2005-11-18
I'm running Ubuntu 5.10 have Nvidia GeForce 6800 and an SGI (Sony) 24" CRT screen (GDM-FW9011). I've got the nvidia drivers working, openGL and many different resolutions, but I can't get the refresh rate I want. In Windows on the machine I use 1920x1200 at 85hz, and would like to do the same in Ubuntu.

Set the horiz to 30-121 kHz and vert to 48-160 Hz in xorg.config. The numbers I got from a quick Google. According to the docs 1920x1200@85Hz is the recommended resolution for the screen, but I can only choose between 60Hz and 73Hz. Is there any way to get 85Hz in there. I'm a bit sceptical to just changing the horz/vert numbers, as I heard it could damage the screen. Anyone have any ideas how to solve this?

---

### Post by frodon on 2005-11-18
horz/vert parameters could damage your screen only if you don't use those which are specified in your screen spec.
You could try do add a modelline to get 85Hz refresh rate, all the details are here : [http://www.ubuntuforums.org/showthread.php?t=83973&highlight=refresh](http://www.ubuntuforums.org/showthread.php?t=83973&highlight=refresh)

---

