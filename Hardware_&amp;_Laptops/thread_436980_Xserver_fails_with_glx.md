---
title: "Xserver fails with glx"
date: 2007-05-08
forum: Hardware &amp; Laptops
---

### Post by Dano30 on 2007-05-08
Hi. I'm having a problem with glx. For some reason whenever I try to use a glx command ie "glxinfo" , X fails and I am sent to my login prompt.  I am using an old voodoo 3 graphics card with tdfx as the driver.  I've changed the driver to vesa in xconf and I can use the glx commands with no problem.  Also if i comment out "Load dri" in xconf the glx commands work normally . Anybody got any Ideas ??

---

### Post by Dano30 on 2007-05-08
Never Mind. I got it.  Just had to install libglide3 and it works fine with direct rendering and all.

---

