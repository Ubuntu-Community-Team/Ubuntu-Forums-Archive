---
title: "Zalman HD135 IR problem"
date: 2008-11-22
forum: Hardware
---

### Post by tpheiska on 2008-11-22
Hey all,

I've been trying to get my remote to work in my Zalman HD135 case with irserver according to [http://ubuntuforums.org/showthread.php?t=304807](http://ubuntuforums.org/showthread.php?t=304807) . My initial problem was that /dev/ttyUSB0 didn't exist. I noticed some disturbing kernel messages about brltty so I removed it. This caused the device node to appear. 

Now, when I try irserver with debug options (sudo irserver64 -codedump -debug_code -loglevel 4 /dev/ttyUSB0) I can see the results with changing numbers related to remote keypresses:

IRTRans Send status 0 - 
IRTRans Send status 1 - 77
IRTRans Send status 1 - 126
etc.

Still, in the end of the server initialization I get

Init communication
Error opening COM/USB Port / LAN device

Any ideas on how I should proceed?

---

