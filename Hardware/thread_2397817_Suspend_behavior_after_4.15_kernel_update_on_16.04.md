---
title: "Suspend behavior after 4.15 kernel update on 16.04 LTS"
date: 2018-08-03
forum: Hardware
---

### Post by jimnms on 2018-08-03
The 4.15 kernel update has changed the suspend behavior of my laptop (HP DV6700).  The power light no longer flashes to indicate it's in sleep mode and just stays on.  The WiFi light stays on as well.  The first time after the update, it didn't resume when I opened the lid, but it did resume when I pressed the power button.  Since then though, it seems to be working, sleeping when I close the lid and waking when I open it.  The lights staying on is annoying, but now it takes a very long time to resume compared to the 4.13 kernel.

---

### Post by PaulW2U on 2018-08-04
With regards to the power switch and other indicators I saw similar when I was also using the 4.15 series kernel. 

I'm now running the 4.17 kernel in the development version (18.10) and the power switch is no longer illuminated while suspended, previously it was always on but one of the other indicators does now flash, previously it was steady. I don't know whether that counts as a bug in the 4.15 series or not as I've never paid too much attention to the changes between different versions of the  kernel.

I didn't notice any abnormal resume time while using the 4.15 kernel. It was always very quick on my relatively new laptop.

---

### Post by jimnms on 2018-08-11
Another Kernel update a few days ago made it worse.  Closing the lid doesn't fully suspend it, and opening the lid no longer wakes it.  When I close the lid, it seems like it's goes partially into suspend mode; the HD powers down, but the system fan stays running.  When I open the lid, all of the keyboard indicator lights are on and it doesn't wake.  I have to use the power button to wake it.

Manually suspending from the power menu does work properly.  The power light flashes and all other lights go out.

---

