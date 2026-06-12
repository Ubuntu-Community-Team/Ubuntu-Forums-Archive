---
title: "Inspiron 1100"
date: 2008-05-12
forum: Hardware
---

### Post by Z_o-s-o on 2008-05-12
Hey guys I'm having some trouble with a Dell Inspiron 1100 and Ubuntu 8.04.

Ive finally got the screen to display 1024X768, but the whole system seems pretty slow and compiz fusion is slow as well.

Its got intel integrated graphics, which according to many, work fine with compiz. The problem is that its using Mesa (according to glxinfo | grep OpenGL) and I dont know how to fix it.

I went into xorg.conf, but the video device shows as "configured device" or something like that.

---

### Post by zenwalker on 2008-05-12
For nvidia, i think install nv drivers might solve, just give a try. Disable Compiz and see if it gets better.

---

### Post by Z_o-s-o on 2008-05-12
Its not the laptop in my signature..


This one has Intel graphics

---

