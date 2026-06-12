---
title: "Can't get OpenGL 2.0 with my ATI mobility 5470"
date: 2010-07-23
forum: Hardware
---

### Post by Zorgoth on 2010-07-23
With direct rendering off, glxinfo says I have OpenGL 1.4, and if I undet LIGL_ALWAYS_INDIRECT, I have OpenGL 1.5.  ATI cards should support at least OpenGL 3.0 if I'm not mistaken...  So what is the problem?

---

### Post by Zorgoth on 2010-07-23
I am using fglrx from "Hardware Drivers"

---

### Post by Zorgoth on 2010-07-24
Got it working by installing the latest opengl.  I still, however, can only get direct rendering by manually unsetting LIBGL_ALWAYS_INDIRECT...

---

### Post by Yellow Pasque on 2010-07-24
The drivers that come with Lucid might not be new enough for your chip. Try removing the current driver and installing Catalyst 10-6: [http://wiki.cchtml.com/index.php/Ubuntu_Lucid_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Lucid_Installation_Guide)

---

### Post by Zorgoth on 2010-07-24
Ooops, i already did that, but i said i installed the latest opengl instead of the latest fglrx.  typo...

---

### Post by Zorgoth on 2010-07-30
I have LIGGL_ALWAYS_INDIRECT not always set now that I've done this:

[http://www.webupd8.org/2010/07/fix-compiz-slowness-for-proprietary-ati.html](http://www.webupd8.org/2010/07/fix-compiz-slowness-for-proprietary-ati.html)

It also fixed a memory problem, and on my work computer a slowness problem.

---

