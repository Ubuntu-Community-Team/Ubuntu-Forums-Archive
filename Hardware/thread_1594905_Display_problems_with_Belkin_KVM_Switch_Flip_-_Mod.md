---
title: "Display problems with Belkin KVM Switch Flip - Model F1DF102U"
date: 2010-10-12
forum: Hardware
---

### Post by NowDistracted on 2010-10-12
I just purchased a Belkin Flip F1DF102U KVM Switch.  The switch itself seems to work great.  

The problem I have is with Ubuntu not recognizing the monitor and setting the resolution outside the monitor's range, resulting in a what amounts to an error message.  Windows XP has no such issue.  I remove the KVM, issue goes away

I tried to find instructions on how to manually set the display resolution, but there seems to be no such function.  I always use the same display resolutions.  Any suggestions?

P.S. Not sure I have this in the correct forum...  Apologies if that is the case.

---

### Post by NowDistracted on 2010-10-14
No takers?  I still have the problem...

Eric

---

### Post by Ujoux on 2010-10-25
Learn 2 google, found the solution in 5 mins :p

[http://forums.fedoraforum.org/archive/index.php/t-229081.html](http://forums.fedoraforum.org/archive/index.php/t-229081.html)

1° get the name of the screen with : (i.e "VGA2") ```
xrandr
```
2° get new mode attributes with : (customize) ```
gtf 1600 1200 60
```
3° add the new resolution with : (adapt the numbers with output of 2°)
```
xrandr --newmode "1600x1200" 108.88 1280 1360 1496 1712 1024 1025 1028 1060 -HSync +Vsync
```
4° set the new mode for the screen ```
xrandr --addmode VGA2 1600x1200
```
5° go to System -> Prefs -> Monitors and select the new resolution

Worked fine for me

---

