---
title: "Youtube crashes firefox 3"
date: 2008-08-17
forum: General Help
---

### Post by Lan on 2008-08-17
Youtube or other flash video in the browswer crashes firefox, but mostly youtube. Sometimes the video plays all the way and sometimes it will just crash when clicking a new link for video.

Distributor ID:	Ubuntu
Description:	Ubuntu 8.04.1
Release:	8.04
Codename:	hardy

DELL D810:

model name      : Intel(R) Pentium(R) M processor 2.00GHz
MemTotal:      2075640 kB
MemFree:        737524 kB

SunJava 6

ATI accelerated graphic driver

Flash version: 9,0,142,0 - I think.

Compiz - Emerald theme.

-------------------------

I disabled Compiz. It got better but still crashed.

I removed that flash version and currently running: 9,0,48,0 with no compiz. Haven't experienced any crashes. 

Haven't tried with compiz on, but it probably won't crash. I have the same exact set up on my desktop pc with same flash version and compiz running. No crashes.

---

### Post by Lan on 2008-08-17
Ok, after about a half hour or so of flipping youtube, Firefox is now crashing again. Maybe I'll do the same to my desktop and see if it crashes.
I have yet to find a fix.

---

### Post by darco on 2008-08-17
try this ....

```
sudo apt-get install libflashsupport
```

good luck 

darco

---

### Post by Lan on 2008-08-17
> **darco said:**
> try this ....

```
sudo apt-get install libflashsupport
```

good luck 

darco

Thanks for the help. I tried that and it says that I already have the latest version.

--------------

Im on my desktop pc now. Im flippin over so many youtubes without a single crash.


Distributor ID:	Ubuntu
Description:	Ubuntu 8.04.1
Release:	8.04
Codename:	hardy

processor	: 0
model name	: Intel(R) Pentium(R) 4 CPU 3.00GHz
stepping	: 1
cpu MHz		: 2923.606
cache size	: 1024 KB

processor	: 1
model name	: Intel(R) Pentium(R) 4 CPU 3.00GHz
stepping	: 1
cpu MHz		: 2985.606
cache size	: 1024 KB

MemTotal:      1034560 kB
MemFree:         52304 kB

NVIDIA accelreatd graphics driver:
01:00.0 VGA compatible controller: nVidia Corporation NV44A [GeForce 6200] (rev a1)

Compiz on
Emaral on

No issues.

The DELL D810 keeps crashing still. hmm..

---

### Post by darco on 2008-08-17
type in about: plugins in the url area of FF....then scroll to see the ver number.
Did you ever have another ver of flash or did you always have ver 9?
I ask because I am using Mint KDE which has ver 10 and I had to downgrade to 9 to get FF to work w/youtube. I made sure to delete 10 completly added 9 and installed flashsupport and I have been fine ever since

darco

---

### Post by Lan on 2008-08-17
I had the version 9.0.142?.0 before. I not sure of the exact version.
I downgraded to the same version on my DesktopPc. 9.0.48.0

Laptop Info: - same exact as this DesktopPc
-------------
Firefox Version 1.9.0.1

# Copyright © 1998-2008 by contributors to the Mozilla Project.

#     Read the licensing information for this product.

    
#     See the build configuration used for this version.

#     Build identifier: Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.0.1) Gecko/2008072820 Firefox/3.0.1

I'm a bit 'blind' but I took some notes in case.
I have removed the following and it seems like it hasn't crashed.

libswfdec 0.6.90   0.6.4-2 SWF decoder library
libflash -swfplayer 0.4.13ubuntu1 GPL Flash Libray stand alone player
libflash -swfplayer 0.4.13-9ubuntu1 GPL Flash Library stand alone player

Also Downgraded flashversion to: 9,0,48,0 from 9.0,142??,0




Thanks,

---

### Post by domherre on 2008-08-17
Where did you find the old version of flash?

---

### Post by todak on 2008-08-17
This is my version of flash: **Shockwave Flash 9.0 r124**. I am using Firefox 3.0.1. I had to remove the **libflashsupport** file in order for Firefox not to crash on youtube. As a matter of fact, I do not have any flash-related crashes at all. If you remove **libflashsupport** and run into other problems, simply install it again! :)

---

### Post by Lan on 2008-08-17
> **domherre said:**
> Where did you find the old version of flash?
hmm. good question. On my laptop, I just removed the flashplugin-nonfree and I ended up with this 'old' version.
On my desktoppc, i don't remember. Looking around my tar/rpm directory, i found a flashinstaller but I don't remember if I used that or not haha and I don't know what version that installer is either.
Other than that, it seems like everything is working well....for now.

---

### Post by slatkin on 2008-08-17
> **todak said:**
> This is my version of flash: **Shockwave Flash 9.0 r124**. I am using Firefox 3.0.1. I had to remove the **libflashsupport** file in order for Firefox not to crash on youtube. As a matter of fact, I do not have any flash-related crashes at all. If you remove **libflashsupport** and run into other problems, simply install it again! :)

Thanks!

---

### Post by psyke83 on 2008-08-17
This is the bug: [https://bugs.launchpad.net/bugs/192888](https://bugs.launchpad.net/bugs/192888)
This thread contains the solution: [http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)

---

### Post by Lan on 2008-08-18
hmmm, i have removed libflashsupport before coming back here to report because I still get the crashes but not as bad. Since I have removed the libflashsupport, the first thing I noticed is that the audio got louder but I still gotta flip through youtubes for tests

Thanks for the link. I'll take a look now..

---

### Post by Lan on 2009-03-19
I forgot what I did but I think I removed flash-nonfree

I've upgraded to Intrepid and flash_player_10 since I lost audio on youtube after upgrade from 8.04 to 8.10

Distributor ID:	Ubuntu
Description:	Ubuntu 8.10
Release:	8.10
Codename:	intrepid

lspci: audio

00:1e.2 Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 03)


Thanks

---

### Post by w1ljam35 on 2009-03-22
I fixed this when I remove swfdec and gnash. Youtube works like a charm now.

---

### Post by satosh on 2009-03-28
Thanks you, thread! Firefox in intrepid crashed instantly when loading any youtube-video but opera played them with no problem. I removed libswfdec with synaptic and now firefox can play flash again!

---

