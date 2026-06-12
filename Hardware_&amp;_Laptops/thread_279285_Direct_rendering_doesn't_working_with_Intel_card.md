---
title: "Direct rendering doesn't working with Intel card"
date: 2006-10-17
forum: Hardware &amp; Laptops
---

### Post by mula on 2006-10-17
Hi,

I've been trying these days to make Xgl work but with no success. The thing that annoys me the most and because of which, I'm really stuck is direct rendering which in my case is no.
```

libGL error: open DRM failed (Operation not permitted)
libGL error: reverting to (slow) indirect rendering
direct rendering: No

```

I have a Thinkpad R50e with an integrated Intel video card.

```
0000:00:02.0 VGA compatible controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
0000:00:02.1 Display controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
```

Modules drm and i910 are both loaded. Xorg configuration file contains the necessary section with the permissions.

Any ideas from your side guys? What else can I try?

---

