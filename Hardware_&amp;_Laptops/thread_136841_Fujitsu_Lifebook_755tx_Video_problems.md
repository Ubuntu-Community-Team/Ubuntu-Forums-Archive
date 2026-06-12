---
title: "Fujitsu Lifebook 755tx Video problems"
date: 2006-02-26
forum: Hardware &amp; Laptops
---

### Post by ddock83 on 2006-02-26
When GNOME loads up, it is stuck at 640x480 and is way off to the right.  Took me forever to guess-click on the res. options and when I got there the only options were the res. I'm already running and 60hz.  From my Windows perspective, it's like I need a driver...but none exist, right?  Please help.
This is an old pentium 150 system and the only specs i know are found here:
[http://support.fujitsupc.com/CS/Portal/supportsearch.do?srch=TECHSPECS]("http://support.fujitsupc.com/CS/Portal/supportsearch.do?srch=TECHSPECS")

---

### Post by ddock83 on 2006-03-04
Why has no one responded?  Was my message unclear or not liked?:confused:

---

### Post by mips on 2006-03-05
You will most likely have to edit your xorg.conf file.

Post your current xorg.conf file here so we can have a look.


Display:
Built-in colour flat-panel DSTN passive matrix LCD Display.
Diagonal dimensions: 12.1"
800x600 resolution, 64K colours
640x480 resolution, 16M colours
Cant find anything on display frequencies.

There is also a option int the BIOS for display compensation when using resolutions lower than 800x600

---

