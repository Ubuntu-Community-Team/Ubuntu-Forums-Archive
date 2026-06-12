---
title: "Google Earth text not right"
date: 2009-03-05
forum: Installation &amp; Upgrades
---

### Post by raymondvillain on 2009-03-05
Running 8.10.  Google Earth starts and works O. K. but place names, dates, altitudes, etc., anything with text appearing on the map is not working right.  Letters are missing, so that instead of "East Oak Lane", for example, all I see is "st  ak Lane" and so forth.

Any ideas?  I renamed libcrypto.so.0.9.8 to libcrypto.so.0.9.8bug so that version 5 would start correctly.  Everything else works, just the text won't cooperate.

---

### Post by brk3 on 2009-03-16
exact same problem, intrepid on dell inspiron 1525

---

### Post by _Herb_ on 2009-03-18
Same problem here on Xubuntu 8.10 with both GE 4.3 and 5.0.

---

### Post by augustos on 2009-03-18
The same problem here kubuntu intrepid googleearth 4.3

---

### Post by Donalb on 2009-03-19
There's a bunch of us out here with this problem on 8.10.
Ideas?

---

### Post by odin1965 on 2009-03-21
Same problem with the text here too. Running GE 5.0 on 8.10 on a Dell 1520 with the Intel embedded graphics with Compiz disabled.

---

### Post by odin1965 on 2009-03-21
Consensus seems to be that it is the intel vid driver causing the problem. More info at;
[http://bbs.archlinux.org/viewtopic.php?id=64944](http://bbs.archlinux.org/viewtopic.php?id=64944) 
and
[https://bugs.launchpad.net/ubuntu/intrepid/+source/xserver-xorg-video-intel/+bug/295934](https://bugs.launchpad.net/ubuntu/intrepid/+source/xserver-xorg-video-intel/+bug/295934)

Problem is possibly solved with the newer Intel 2.6.1 driver that ships with 9.04.

---

### Post by Donalb on 2009-04-30
Hey, Wondering if anyone with this problem has updated to jaunty and if it fixes the problem? 
I want to hold off on a Jaunty update for a mont after release to let some of the bugs get ironed out but this is one of the things pushing to do it sooner.
Regards

---

### Post by ubuntubrian on 2009-04-30
fonts are all fixed in Jaunty. GE still doesn't play well with any compiz effects though.

---

### Post by Donalb on 2009-05-01
Thanks Ubuntubrian. So what problems with GE & Compiz are cropping up in Jaunty, if you don't mind me asking?

---

### Post by ubuntubrian on 2009-05-01
I had the same problem in Intrepid and Hardy with GE and Compiz. Any desktop effects at all cause the graphics in GE to go haywire. The display breaks into quadrants of pixelated garbage and won't resolve. No desktop effects and GE works great. Maybe my graphics card?

---

### Post by Donalb on 2009-05-20
I've been hesitant about upgrading to Jaunty from Intrepid because of the various reported graphics problems.
However I'm wondering if any of you guy who had his problem upgraded and if so, what effect did it have on GE?

---

### Post by ubuntubrian on 2009-05-20
As I wrote I upgraded to Jaunty and the video issue is the same as in Hardy and Intrepid. My brother upgraded to Jaunty and had worse video problems in media players as well. I guess I was lucky as I am no worse off than I was before the upgrade.

---

### Post by joey-elijah on 2009-05-20
regarding the text issue, for those running jaunty go to a terminal and run

[I]googleearth -style GTK+

[/I]and see if that makes it better[I].
[/I]

---

### Post by PAcocaam on 2009-07-23
OKS If all of the above doesnt work you can try changing the 3d fonts on Tools>options>choose 3d fonts ; some fonts work well especially the least known ones

---

### Post by typo99 on 2009-07-23
Could you list some of the fonts that look alright? 

I'm on 8.10 and Intel graphics chips and the text is missing and garbled.

---

### Post by Donalb on 2009-07-23
Good idea. I've tried 10 or 12 of the "lesser-known" fonts to no effect.

---

### Post by Donalb on 2009-11-04
Karmic 9.10 solves this...finally!

---

### Post by ubuntubrian on 2009-11-04
It does and I'll mark solved.

---

