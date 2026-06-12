---
title: "Kworld 115 (getting Channels to work)"
date: 2008-10-24
forum: Hardware
---

### Post by elgreek84 on 2008-10-24
Hi there.
I hate to create this thread since I know there's a lot of "kworld 115 tv tuner" threads out there, but I just can't seem to get this thing working.  
I have very little linux experience, but I'm learning.   So far I followed the instructions on the mythtv (found here: [http://www.mythtv.org/wiki/index.php/Kworld_ATSC_110](http://www.mythtv.org/wiki/index.php/Kworld_ATSC_110) ) and loaded the nxt2004 firmware but that's it!  I haven't been able to tune to anything.  All I really want is analog cable.  Thanks for any advice.

Also I'm on Intrepid Ibex (oct 22 release)

---

### Post by cariboo on 2008-10-24
Have you had a look here?

[http://ubuntuforums.org/showthread.php?t=734867&highlight=kworld](http://ubuntuforums.org/showthread.php?t=734867&highlight=kworld)

It seems it is sovled here. Mythtv depends on a working tv tuner card, it will do nothing to get your tuner card working.

JIm

---

### Post by elgreek84 on 2008-10-24
> **cariboo907 said:**
> Have you had a look here?

[http://ubuntuforums.org/showthread.php?t=734867&highlight=kworld](http://ubuntuforums.org/showthread.php?t=734867&highlight=kworld)

It seems it is sovled here. Mythtv depends on a working tv tuner card, it will do nothing to get your tuner card working.

JIm


Yup,  everything was good (everything works hardwarewise -firmware is install correctly) until the last step:
"in terminal do this next line
scan /usr/share/doc/dvb-utils/examples/scan/atsc/us-ATSC-center-frequencies-8VSB > ~/.azap/channels.conf"

and no channels are found.  Do you have the tuner yourself?  Which one of the two slots is the one for analog cable? The one closest to the board or furthest?  I've tried both and nada. Thanks for response!

---

