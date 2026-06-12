---
title: "Linux is acting extremly slow"
date: 2010-01-29
forum: Hardware
---

### Post by sleepystoner420 on 2010-01-29
well basicly i noticed this problem since i got ubuntu apparently watching videos like youtube lags alot i cant go to full screen without extreme lag

on top of that i noticed that i have a lag problem inside games which i didn't have in windows i realize that drivers for linux aren't as complex as the 1's for windows but from all the talk on the forums and stuff people say that linux is supposed to be alot faster then windows in performance

i was wondering if it had to do with hardware like not having the optimal driver or something

I have these system specs:
Compaq - preserio model: GN578AA-ABA SR5233WM
Intel Pentium D 2.80 Ghz processors (x2)
1 GB of Ram 
3 GB of Virtual Memory
Running: Ubuntu 9.04 Jaunty Jackalope x86

---

### Post by Grenage on 2010-01-29
Some people do have issues with full-screen flash, a lot of them can be resolved by using the flashplugin-nonfree package (instead off the free version - look in the package manager).

As for games, are you running them through WINE?  Which games?

---

### Post by sleepystoner420 on 2010-01-29
alien areana is the 1 that i noticed it the most in windows it pretty smooth but in linux its hard to move and aim

---

### Post by Grenage on 2010-01-29
Are you using proprietary drivers?  They will help a lot.  Under System/Administration/Hardware Drivers, check what is enabled; failing that, post the results of:

```
lspci | grep VGA
```

---

### Post by sleepystoner420 on 2010-01-29
nothing is listed when i look under hardware and when i use the code you gave me in terminal it gives me this ```
00:02.0 VGA compatible controller: Intel Corporation 82945G/GZ Integrated Graphics Controller (rev 02)
```

---

### Post by Grenage on 2010-01-29
Intel's Linux drivers aren't great for 3D/acceleration, their Windows drivers are much better.  I can offer no advice there really; aside from adding something like an Nvidia card.

Try the non-free flash player, that might at least help with our full-screen issues.

---

