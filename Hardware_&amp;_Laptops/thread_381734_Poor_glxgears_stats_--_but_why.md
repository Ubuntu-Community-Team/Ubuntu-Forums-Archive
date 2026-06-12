---
title: "Poor glxgears stats -- but why?"
date: 2007-03-11
forum: Hardware &amp; Laptops
---

### Post by cookfromfrozen on 2007-03-11
Ubuntu 6.10.  Radeon 9600 Pro with fglrx drivers installed.  fglrxinfo reports the following:

```
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON 9600 Generic
OpenGL version string: 2.0.6011 (8.28.8)
```

2D performance (such as the responsiveness of moving a window around) is fine, as well is 3D performance (UT2004 runs fine, *slightly* slower than with XP but more than acceptable).

However, glxgears reports only ~250 FPS:

```
1224 frames in 5.0 seconds = 244.607 FPS
1218 frames in 5.0 seconds = 243.456 FPS
1232 frames in 5.0 seconds = 246.281 FPS
```

I know from experience that I should be getting somewhere in the region of the thousands, and I did with Dapper and earlier versions.  I'm aware that glxgears is not specifically a benchmark, and 2D/3D performance is fine otherwise, but is there any specific reason why the framerate is that low?

---

### Post by yabbadabbadont on 2007-03-11
Are you runnning XGL or Beryl?  They are known to cause low readings.

---

### Post by cookfromfrozen on 2007-03-11
Not using Beryl etc.  I remember the number being well into the thousands with Dapper.

---

### Post by dejitarob on 2007-03-12
[http://wiki.cchtml.com/index.php/Glxgears_is_not_a_Benchmark](http://wiki.cchtml.com/index.php/Glxgears_is_not_a_Benchmark)

See [http://www.ubuntuforums.org/showthread.php?t=348634](http://www.ubuntuforums.org/showthread.php?t=348634) for an alternative.

---

### Post by cookfromfrozen on 2007-03-12
I'm fully aware it isn't a benchmark; I even stated as much in my first post.  The crux of my post is wanting to know *why* the number is so low specifically with the fglrx driver and Radeon 9600 Pro.

---

