---
title: "WebGL on ATI Xpress 200"
date: 2011-01-05
forum: Hardware
---

### Post by prunc on 2011-01-05
Hi, this is my first post on the ubuntu forums.

I have a DELL Inspiron 1501 Laptop With ATI graphics (ATI Xpress 200M) and I am running Ubuntu 10.10. I want to be able to see WebGL powered websites like _[Google's Body Browser]("http://bodybrowser.googlelabs.com")_. I have tried Chrome Beta, and Firefox 4 beta 8 with webgl enabled, but WebGL doesn't work.

glxinfo sais:```

direct rendering: Yes
server glx vendor string: SGI
server glx version string: 1.4
OpenGL vendor string: DRI R300 Project
OpenGL renderer string: Mesa DRI R300 (RS400 5975) 20090101 x86/MMX+/3DNow!+/SSE2 NO-TCL DRI2
OpenGL version string: 1.5 Mesa 7.9-devel

```

So now I have OpenGL 1.5, but _[as I understand]("http://hacks.mozilla.org/2010/12/firefox4b8/comment-page-1/#comment-329645")_ I need OpenGL 2.1 to enjoy WebGL.

I also installed _[the new Gallium drivers]("https://launchpad.net/~xorg-edgers/+archive/ppa")_ and now glxinfo sais:
```
OpenGL vendor string: X.Org R300 Project
OpenGL renderer string: Gallium 0.4 on ATI RS482
OpenGL version string: 2.1 Mesa 7.10-devel
OpenGL shading language version string: 1.20
```

,but WebGL now only works sometimes, and **not** for the Body Browser.

My question is: how much time should I wait until the Gallium drivers are finalized for my particular graphics card? Will it be ready by 11.04?

Thanks. :D

---

### Post by erinbanwell on 2011-01-11
I had a similair problem with ATI Xpress 1100 card. I found out that intel doesnt upgrade a lot of their old drivers for new linux releases. The open source drivers i tried didnt deliver when trying to view 3d renderings.

---

