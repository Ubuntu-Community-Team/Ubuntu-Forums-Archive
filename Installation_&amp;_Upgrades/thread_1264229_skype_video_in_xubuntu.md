---
title: "skype video in xubuntu"
date: 2009-09-11
forum: Installation &amp; Upgrades
---

### Post by aljoriz on 2009-09-11
If your video in skype goes green try this command

$ sudo mousepad /usr/local/bin/skype 

and paste the following 2 line
 	Code:
 	#!/bin/bash
LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so /usr/bin/skype 

save it thengo back to terminal
 	Code:
 	$ sudo chmod a+x /usr/local/bin/skype 
the gedit = in xubuntu is MOUSEPAD

---

