---
title: "[resolved] thumb buttons/wheel functions reversed"
date: 2004-12-21
forum: Hardware &amp; Laptops
---

### Post by Glycerine on 2004-12-21
Unsure why this is appearing, but my mx700 mouse seems to have gone schitzo on me all the sudden.  The wheel no longer scrolls, it controls the "forward" and "back" functions of firefox, while the two thumb buttons now handle the scrolling.  

xmodmap -pp does show the buttons as correctly mapped (1-1, 2-2 etc) and with xev, i've confirmed that the scroll wheel is in fact 6 and 7, with the thumbs being buttons 4 and 5.

I have the standard code in my config file:
```
    Identifier	"Mouse1"
    Driver "mouse"
    Option "CorePointer"
    Option "Protocol"   "ExplorerPS/2"
    Option "Device"     "/dev/input/mice"
    Option "Buttons"	"7"
    Option "ZAxisMapping"	"6 7"
```

Tried swapping the ZAxis options for buttons 4 and 5 but no effect.  Removing the Buttons and ZAxis options does make the buttons unavailable tho.  It seems liek something else is waiting for X to enable the buttons and then takes over their mapping but I have no clue what.  Any help is appreciated as it's driving me nuts.

Thanks

---

### Post by Glycerine on 2004-12-29
[
 Well workaround found.  After some testing, the mouse seemed to go wonky after a hoary upgrade, using XFree86.  The workaround was to put the normal buttons=7 and zaxismapping=6 7 in the config file but run ```
xmodmap -e "pointer = 1 2 3 6 7 4 5"
``` at startup.

But just incase anyone else runs into the same issue, here ya go :)

---

### Post by frogman on 2005-01-09
Cheers, you've just saved me some work.

---

