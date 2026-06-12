---
title: "Firefox randomly quits"
date: 2008-08-03
forum: General Help
---

### Post by DJitalis on 2008-08-03
First a thank you to all who have put a lot of hard work and effort to helping people on these forums, I have made a lot of progress shedding my 'mortal windows coil' by reading these very forums. I wasn't able to find anything on my current problem (although its probably there I just can't find it as my gf would say). 

Just recently while surfing the firefox browser just quits. I think its when there is flash content on the page but I'm not sure. Making matters even weirder it doesn't do it consitantly. I have a suspiscion that it may be the the Flash beta I installed in oder to hear youtube videos on my USB headset (was not working with regular flash). 

Question is how do I revert to the earlier version of flash to check?

---

### Post by dexter.deepak on 2008-08-03
before blaming flash, try running firefox in safemode :
```
firefox --safe-mode

```
and see if it works.

---

### Post by silkstone on 2008-08-03
Generally Flash beta 1 works OK (although it doesn't support transparency.) Beta 2 has been giving people some problems.

You can revert to the flashplugin-nonfree in the repositries (via Synaptic or apt-get), but it may be wise to uninstall the existing one first. That depends on how you installed it - does it appear in Synaptic under Local packages?

The plugin is called libflashplayer.so and you could search for that. I think it is usually somewhere in /usr/lib/

---

