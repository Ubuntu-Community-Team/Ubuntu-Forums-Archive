---
title: "Scrolling with the trackpoint"
date: 2009-01-26
forum: Hardware
---

### Post by zibi on 2009-01-26
There are already two threads on this topic:

[http://ubuntuforums.org/showthread.php?t=950006]("http://ubuntuforums.org/showthread.php?t=950006")

and 

[http://ubuntuforums.org/showthread.php?p=6051853]("http://ubuntuforums.org/showthread.php?p=6051853")

Still the commands

xinput set-int-prop "TPPS/2 IBM TrackPoint" "Wheel Emulation" 8 1
xinput set-int-prop "TPPS/2 IBM TrackPoint" "Wheel Emulation Button" 8 2

do not work on my lenovo x200 :(

I checked it and I'm sure it is that "TTPS/2 IBM TrackPoint" is the correct device name (in the output of $ xinput list i find also a strange "Machintosh mouse button emulation". Not sure if it is of any relevance)

Hope someone could help.

Thanks 
Luca

---

