---
title: "NVIDIA 9500 with twin view second monitor at 800X600"
date: 2014-12-27
forum: Hardware
---

### Post by Jbike on 2014-12-27
I've been running this 12.04 install for years, running two identical monitors at 1400 by 1050 running the recommended nvidia driver. Both monitors were recognized by name in the nvidia settings manager. Then one day, I'm assuming after an update a few weeks ago the second monitor kicked down to 800 by 600, and is no longer recognized by the nvidia settings manager.   All options to change my resolution on this second monitor to anything better are gone. Deleting xorg.conf and regenerating the file did not work either.  I even tried  to install Ubuntu MATE and could not get twin view to allow both monitors to operate at the same resolution.  Other things I have tried include reinstalling multiple versions of the NVIDIA drivers and reverting back to Nouveau drivers, which do not detect the second display. I know that the hardware is fine since windows works with both monitors at high resolutions.  Anyone have any ideas for me? 

Thanks, Jbike

---

### Post by Jbike on 2014-12-28
Well it turns out that the problem was with the NVIDIA 9500 graphics card. Switching this card out with a NVIDIA G210 solved the problem (Installing the card into a different  unaffected machine created the issue, ie it follows the 9500 video card) .  Keep in mind everyone that there is nothing wrong with the card. Windows works just fine with either card. Could this be a kernel issue?   In any event, I would think that the Ubuntu folks may want to know about problems like this one... I would like to thank my son for swapping the video cards when I was away today to solve the problem. Anyone else out there wanting to use twin view with the older 9500 card.... better not to try unless someone replies with a fix!   I'm off to find a new video card to buy... 
Jbike

---

