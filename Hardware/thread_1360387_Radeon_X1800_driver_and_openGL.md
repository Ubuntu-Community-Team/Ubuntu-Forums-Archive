---
title: "Radeon X1800 driver and openGL"
date: 2009-12-20
forum: Hardware
---

### Post by dvdhl89 on 2009-12-20
Hi,

I am currently on Karmic 9.10, using the default open source drivers. But the problem is that the drivers detects my graphic card as a R300 (I 9xxx series) gpu, when it should be R520 (X1xxx series). Because of that, I can't run any applications that require OpenGL 2, because R300 only supports 1.5.

LSPCI
```
01:00.0 VGA compatible controller: ATI Technologies Inc R520 [Radeon X1800
```

GLXINFO
```

OpenGL vendor string: DRI R300 Project
OpenGL renderer string: Mesa DRI R300 (R520 7100) 20090101 x86/MMX/SSE2 TCL
OpenGL version string: 1.5 Mesa 7.6

```

I had this problem since 8.10, hoping this could be fixed on the next distributions, but it hasn't.

Can anyone help me please?

---

### Post by Yellow Pasque on 2009-12-20
The mesa r300 driver covers r300-r500 cards. Nothing wrong there.

> I can't run any applications that require OpenGL 2
You and everyone else running open-source ATI. It's coming, though. (Gallium3D)

---

