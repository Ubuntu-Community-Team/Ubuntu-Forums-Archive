---
title: "Intel X3100 integrated graphics"
date: 2008-07-20
forum: General Help
---

### Post by ChinaTownOne on 2008-07-20
I have a Dell Inspiron 1720 that runs Ubuntu, but I need graphics drivers for my Intel Integrated X3100 graphics.  Can anyone tell me where I can download it for 64-bit Ubuntu?

---

### Post by CatKiller on 2008-07-21
The open-source Intel drivers should be installed by default.

---

### Post by eragon100 on 2008-07-21
You don't need them, the open-source drivers come with the system and have full 2d/3d support.

To check if they are working correctly, simply try to activate desktop effects in system -> preferences -> appearance. If they work, you're in business :wink:

---

### Post by insane_alien on 2008-07-21
X3100 on my 1525 works fine under ubuntu out of the box. 64-bit too.

---

### Post by ChinaTownOne on 2008-07-21
are you sure?  I tried to change some of the settings on the preinstalled games and Ubuntu wouldn't play Chess in 3D on account of "improper drivers"

---

### Post by ChinaTownOne on 2008-07-21
Ok never mind, it doesn't work because I have "No Python OpenGL support and No Python GTKGLExt support"  So the question now is how do I get those?

---

### Post by fragos on 2008-07-21
Install "python-opengl" and "python-gtkglext1"

---

