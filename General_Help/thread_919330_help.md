---
title: "help"
date: 2008-09-13
forum: General Help
---

### Post by adamant715 on 2008-09-13
Ok, whenever I open a Web Browser (Epiphany,Firefox) I watch youtube videos for like 10 min and the sound works just fine, but after that it stops working and then when i close the browser I try to open it again 

2nd Problem.After I close a web browser it doesn't open and just goes to Sleeping in the Processes...

---

### Post by kokkus on 2008-09-13
Ok I will help you out here. But first of all, do not name your thread HELP or something that doesn't tell people what the problem / point is.

OK, install flashplugin-nonfree from terminal
sudo apt-get install flashplugin-nonfree

You should either install the ubuntu-restricted-extras pack which includes everything you need like that flash plugin.
sudo apt-get install ubuntu-restricted-extras

The reason why your browser doesn't open again is because it's not really closed. Use killall firefox or killall epiphany to kill the process.
They didn't close because their bugged while you worked in them. In this case the flash problem on youtube.

---

### Post by mb_webguy on 2008-09-13
It sounds like he already had the Flash plugin installed.  Try installing the version of flashplugin-nonfree from the backports repository and see if it clears up the problem.  Check the link in my signature for instructions on how to do it.

---

### Post by adamant715 on 2008-09-13
Ok I'll make sure I change it, but do you know what I can do with the second part??

---

### Post by mb_webguy on 2008-09-13
It could all be the same problem.   Try the Flash 10 plugin first and see if that fixes it.  If not, then will look into other solutions.

---

### Post by ad_267 on 2008-09-13
Try installing libflashsupport

---

### Post by mb_webguy on 2008-09-13
I don't think you should install the Flash 10 plugin from the backports repository AND libflashsupport.  The libflashsupport package was designed to fix some incompatibilities between Flash and PulseAudio that have been rectified in Flash 10.

---

