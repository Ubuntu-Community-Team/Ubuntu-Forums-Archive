---
title: "Installing drivers for AMD E-450 in 12.04.1 LTS"
date: 2012-09-07
forum: Hardware
---

### Post by lharwell on 2012-09-07
I recently installed Ubuntu 12.04.1 LTS on an HP Pavilion dm1z, and I need some help finding the right driver/configuration for its AMD E-450 APU.

The default VESA Wrangler works adequately for light use, but chokes pretty badly on any sort of flash/high def video.

I tried enabling fglrx via the Additional Drivers menu, but then the system performs unbearably slowly.
There is also an option for fglrx with (post-release updates), but it fails to install and also deactivates fglrx.

---

### Post by moteprime on 2012-09-29
Hi.
There are a newer proprietary driver 12.8 from the AMD support site, but i don't think it will be much faster.
There are a setting you can get to in ccsm -> openGL, "sync to Vblank", disable that and enable tearfree in catalyst centre. I think its the same thing from two different worlds. And they collide sometimes making the video real slow.
I use the open source Radeon driver (the default), the proprietary AMD driver freezes my Ideapad s205 2-3 times a day.

---

