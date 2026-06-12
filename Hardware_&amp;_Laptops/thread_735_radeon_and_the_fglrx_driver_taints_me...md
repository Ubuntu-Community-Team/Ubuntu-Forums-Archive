---
title: "radeon and the fglrx driver taints me.."
date: 2004-10-15
forum: Hardware &amp; Laptops
---

### Post by mardi on 2004-10-15
Hi, i got almost everything up and running, except *sigh* for my radeon 9600.. I have installed the fglrx driver and made a X conf using the fglrxconfig tool. All is good but glxinfo shows me:
```
GLX extensions&#58;
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_EXT_import_context
OpenGL vendor string&#58; Mesa project&#58; [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string&#58; Mesa GLX Indirect
OpenGL version string&#58; 1.3 Mesa 4.0.4
OpenGL extensions&#58;

```

So on ATIS homepage they suggest you uninstall the mesa glx, but when i mark anything with mesa for removal, synaptic feels like removing X and other quite important packages in my desktop distro :(
Anyone knows how to get hardware accelration? Perhaps a working X conf with a radeon board?

Thanks.. Mardi

---

### Post by HungSquirrel on 2004-10-15
[http://www.ubuntufaq.org/document_details.php?c=4&amp;d=3](http://www.ubuntufaq.org/document_details.php?c=4&amp;d=3)

You probably didn't do the step of getting the restricted kernel modules.  That's what I forgot to do and as soon as I did that I had wonderful 3D acceleration.

---

### Post by mardi on 2004-10-16
Ohh baby!! You just saved my day, got glxgears running ~2000 now  :) 

Didn't quite see that last bit with restricted modules.. Does "restricted" mean the package contains closed-source drivers?

---

### Post by HungSquirrel on 2004-10-16
Among other things.  By my understanding, the restricted packages have less than free licenses, i.e. they probably aren't GPL, LGPL, or BSD compatible.  I don't know for sure.  Might want to ask someone more knowledgeable about that.  :)

---

