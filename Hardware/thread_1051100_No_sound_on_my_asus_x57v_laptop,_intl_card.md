---
title: "No sound on my asus x57v laptop, intl card"
date: 2009-01-26
forum: Hardware
---

### Post by warelf on 2009-01-26
Hello, 

I have alittle problem on my new laptop, ubuntu dosnt give me any sounds, either from headphones or speakers. 

The card that is in the machine is:

warelf@abydos:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC663 Analog [ALC663 Analog]
Subdevices: 1/1
Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC663 Digital [ALC663 Digital]
Subdevices: 1/1
Subdevice #0: subdevice #0
warelf@abydos:~$

Anyone got any suggestion of how to fix this?

All the help i can get is appriciated :D

---

### Post by JaysonLean on 2009-03-11
Absolutely the same trouble. :-) Well, I definitely know the issue is ALSA. though I haven't still fixed the trouble due to encountering some problems with upgrading it. If U have Intrepid (well, so do I), U can type "alsamixer" in Terminal, U'll see it's 1.0.17 which doesn't work with our card cause it's old version (I know it from here: [http://ubuntuforums.org/showthread.php?t=972761](http://ubuntuforums.org/showthread.php?t=972761)). So U should see this: [http://ubuntuforums.org/showthread.php?t=962695](http://ubuntuforums.org/showthread.php?t=962695) - though looks like I make something wrong.
Also U can upgrade manually, if U can (I can't by now. :-)). U need alsa-driver, alsa-lib and alsa-utils. All 3 packages can be found here:[http://alsa-project.org/main/index.php/Main_Page](http://alsa-project.org/main/index.php/Main_Page) 

Good luck...! :-) And if U have solved, pls, write out. 

P.S. Btw, my first post on Ubuntu help. ))

---

### Post by warelf on 2009-03-11
Hey, 

Jepp i have solved the problem, the alsa upgrade to *.19 took care of it :)

Used the upgrade script from: [http://ubuntuforums.org/showthread.php?p=6589810](http://ubuntuforums.org/showthread.php?p=6589810)

---

