---
title: "Tv Out on ATI Mobility Radeon 9600?"
date: 2004-12-04
forum: Hardware &amp; Laptops
---

### Post by kris on 2004-12-04
Has anybody sucessfuly made tv out work on ATI Mobility Radeon 9600 (or any other Radeon based) card? If so, a _simple_ how-to would be greatly wellcome. 

I have the fglrx driver installed and OpenGL stuff works...
Here my fglrxinfo output:
```
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: MOBILITY RADEON 9600 Generic
OpenGL version string: 1.3.4510 (X4.3.0-3.12.0)
```
Please only post positive answers.

---

### Post by mattyh on 2004-12-04
I haven't tried getting that to work, but when I had an older ATI mobility, I got it to work with the gatos ati.2 drivers.  You could maybe do searching about on those, and see if you find a solution.  Hope that points you in the right direction.

---

### Post by lagartija on 2004-12-04
i've not a mobility card (mine is a 9600 aiw) but i think that the drivers from ATI are the same...if i'm not wrong
so, this is my experience....
I installed all the necessary packages following the How-To
I used the fglrxconfig program shipped with the ATI drivers to build the XF68Config-4 file...follow the instruction to activate the TV-out 
point your attention to your monitor timings and your mouse device when asked (in Ubuntu is /dev/input/mice) and anwer Y  when the program ask if you want to activate the TV-out
and make a backup of your XF86Config-4 file in case of pbms...

hope it helps

---

### Post by kris on 2004-12-06
So after doing that, your Tv-out works? Do you have to restart the computer when plugging S-Video cable, or do you restart X server only, or do you have no need to restart?
Does the ATI configuration pannel work as expected?

---

