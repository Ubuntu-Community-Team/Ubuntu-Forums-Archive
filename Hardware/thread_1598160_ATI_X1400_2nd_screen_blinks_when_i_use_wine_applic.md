---
title: "ATI X1400 2nd screen blinks when i use wine applications or totem!"
date: 2010-10-16
forum: Hardware
---

### Post by Opixel on 2010-10-16
Hi ,

I have a dell inspiron 6400 with ubuntu 10.10 32bit installed.
also i connected a HP w2228h monitor to it. i used Xrandr to have a big extended screen.
my primary monitor is set to be the external monitor.
 
i have open source ATI driver and i dont have xorg.conf file!
when i open application with wine(1.3.3) my screen blinks couple of times then it opens.
sometimes i see there is a noise on desktop but goes away after while.
totem is also blinks when i start it.
the applications which open with blinking they take the cpu usage up.
is there anyway to fix this issue?
or its just me who has this problem?

TNX

---

### Post by r4e on 2010-12-07
From commandline run wine regedit and add the following key:

HKEY_CURRENT_USER/Software/Wine/X11 Driver/UseXRandR = N

This will prevent wine from switching the resolution using XRandr extension. See here for more info:

[http://ubuntuforums.org/showpost.php?p=9476476&postcount=10](http://ubuntuforums.org/showpost.php?p=9476476&postcount=10)

This fixed the problem for me anyway.

---

