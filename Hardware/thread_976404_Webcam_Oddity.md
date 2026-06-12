---
title: "Webcam Oddity"
date: 2008-11-09
forum: Hardware
---

### Post by mrwilly on 2008-11-09
Hi, I've just installed Intrepid Xubuntu, and it's going great except for a weird webcam problem.

I have a laptop with a built-in webcam (Vimicro 0321), which did not like to work with Skype. Anytime I went to the options in Skype and clicked on test, the video would be all messed up and unuseable.

I have found a work-around. If I quit Skype, then start cheese (a Photobooth application [http://www.gnome.org/projects/cheese/](http://www.gnome.org/projects/cheese/)), cheese works perfectly with the webcam. Then if I quit cheese then start Skype again, Skype now works perfectly.

It's not the end of the world, but it would be nice to make it work from the get go...

On a side-note, Skype always starts automatically when my laptop boots, and for the life of me I can't find out how to stop it doing it!

Anyone got any good ideas?

Cheers!

---

### Post by El Viejo Lobo on 2008-11-09
Try this [http://ubuntuforums.org/showthread.php?t=945803&page=2](http://ubuntuforums.org/showthread.php?t=945803&page=2)

It works some time (not for me)

---

### Post by mrwilly on 2008-11-09
That does the trick nicely. Thanks! :)

---

### Post by aljoriz on 2009-09-08
Quick solution for skype users:

type
 	Code:
 	$ sudo mousepad /usr/local/bin/skype 
and paste the following 2 line
 	Code:
 	#!/bin/bash
LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so /usr/bin/skype 
save then make it executable at the terminal
 	Code:
 	$ sudo chmod a+x /usr/local/bin/skype

---

