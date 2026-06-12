---
title: "ATI Radeon Xpress 200m running fglrx, but with really poor performance"
date: 2007-03-08
forum: Hardware &amp; Laptops
---

### Post by seodoa on 2007-03-08
Recently installed Edgy Eft on a newish Sharp Mebius PC-CH40N laptop (I know, it's cheap, but I already have a nice desktop back home and just needed something to get me by while I am overseas).  Everything seems to be working just fine, except for my ATI Xpress 200m card.  From what I can tell through Google and the Forums, the card seems to be plagued with problems in Linux... just my luck, I guess.  However, most people seem to be able to get it working acceptably, right?  Not in my case, I'm afraid.  I (correctly) installed both the versions of the driver in the repository and, when those failed to give me even close to adequate results, I tried the latest versions from ATI.  Both, when installed, give me Direct Rendering, fglrxinfo attests to that, but the performance is pathetic to say the least.  I know I cannot expect a lot from a 200m, but in Windows I can play UT2004 or Civilization IV perfectly.  In Ubuntu, even with fglrx installed and Direct Rendering on, I get poor framerate even from an OpenGL screensaver.  As for games, well, I'm lucky to get 5-10 fps from (native) UT2004.  Is there something I am missing?  Or is this just an example of ATI's notoriously poor performance under Linux and OpenGL?

Theodore

---

### Post by adam.tropics on 2007-03-08
I realise it's not intended as a benchmark as such, but what do you get if in terminal you do 'glxgears -info' ? (it will give you frame rates)

---

### Post by seodoa on 2007-03-08
I am not in Linux right now, but glxgears gives me between 150 and 300 frames per second, pretty abysmal, I remember my desktop back home easily giving 2000+ in glxgears, and its video card is only a GeForce FX5600, hardly a graphics powerhouse.  I have heard people report at least 900~1000fps with an Xpress 200m.  My cpu is only a Sempron, but I doubt it is the bottleneck, my desktop at home is hardly impressive: an AthlonXP 2600+

Theodore

---

### Post by adam.tropics on 2007-03-08
Well I have the same, ati radeonXpress 200m and get 698 fps, which is also not good, but even so yours doesn't sound good at all! Still if glxinfo is telling you that you have dri, and fglrx info is correctly identifying your card/driver, then I am a bit stumped! Sorry.

---

### Post by TTL on 2007-03-08
Did you test a game like ppracer? I have a 200m with a Sempron too and the game runs smooth (only if many objects are visible the framerate drops below 10 fps),
I had a very low framerate at tuxkart first, the solution was  to add
```

tmpfs  /dev/shm  tmpfs  defaults  0  0

```
to my fstab and mount it.

I read somewhere that the 200m has 2/3 the power of a 9600 and my personal experience agree with this.

---

