---
title: "Rage 128 times out with some opengl apps"
date: 2005-12-05
forum: Hardware &amp; Laptops
---

### Post by Jengu on 2005-12-05
With some opengl applications, they crash with this error:

```

Error: Rage 128 timed out... exiting

```

I can't figure out why. One of these apps is just trying to draw a transparent square and crashes on startup, so I don't think it's a performance issue. Slune on any detail setting higher than low gives the error when trying to start a mission. On the other hand, neverball, drawing a much more sophisticated scene, with all options turned up, runs fine.

dmesg output:

```

[4296135.613000] [drm:r128_cce_depth] *ERROR* r128_cce_depth called without lock held
[4296135.614000] [drm:r128_cce_idle] *ERROR* r128_cce_idle called without lock held

```

No errors show up in /var/log/Xorg.0.log. My xorg.conf is just as ubuntu automatically configured it with the sole exception that I changed color depth from 24 to 16 (24-bit opengl gives errors).

I'm running a Dell Inspiron 8000 laptop with an ATI Rage Mobility M4 32MB. glxinfo confirms that dri is enabled.

Any ideas?

---

