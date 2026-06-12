---
title: "key satus monitor in Intrepid not working"
date: 2008-11-08
forum: General Help
---

### Post by heathenx on 2008-11-08
hello,

i used a key status monitor pretty regularly in hardy. it worked very well after adding the right devices for my keyboard and mouse. i have upgraded my desktop form hardy to intrepid and the key status monitor that i use no longer works. perhaps many of you would not think to use an app like this but it does come in handy for screencasts where i would like to show the viewer what keys and mouse clicks are being used.

the  app can be found here:
[http://www.programmer-art.org/projects/keystatus](http://www.programmer-art.org/projects/keystatus)

i run the python script "key-status" without any modifications except for adding my devices:

# Special for heathenx ;)
# locate with "sudo cat /proc/bus/input/devices"
KEYBOARD_LOCATION = "/dev/input/event1"
MOUSE_LOCATION 	  = "/dev/input/event5"

if you would like to see the key status monitor in action then head over to [http://screencasters.heathenx.org/wp-content/videos/ep071/ep071.html](http://screencasters.heathenx.org/wp-content/videos/ep071/ep071.html) and watch just a few minutes of the video.

anyway, if anyone can offer me some advice then i would really appreciate it. i can get the app to run but cannot get it to display which keys i'm pressing or which mouse button i press.

---

### Post by Daniel G. Taylor on 2008-11-09
I've confirmed the bug on Intrepid and am working on a fix. For now try adding your device lines to the script around line 98, just after the try/except clauses to automatically find the proper devices. That should override the automatically discovered devices.

I'll throw up a fix as soon as I figure out what to do.

---

### Post by heathenx on 2008-11-09
ah, thanks daniel. i'll take your advice regarding the "line 98" fix. i still have version 5 too and i have been testing that as well. version 5 and 6 seem to have the same behavior on intrepid though.

if you have confirmed this as a bug in intrepid then there may not be much i can do until there is a fix. please don't bend over backwards for me. i'm sure you are busy enough. i'll wait patiently.

thank-you. i appreciate it. :)

---

