---
title: "Ati"
date: 2007-10-17
forum: Hardware &amp; Laptops
---

### Post by vlaeddy on 2007-10-17
I have just installed Ubuntu 7.10 and I don't know what kind of driver should I install for my graphic card ATI RV 370 Sapphire x550 Silent. Sure I can enable the restricted driver (system-administration-restricted driver manager), but then disappear all the effects of Compiz. (actually i would use only normal effects). If I use only the Generic driver, I can't use the graphic acceleration. There is of course a list of drivers in "screens and graphics'. Can I use one of them? (open source driver is of course desired)
Thanks a lot,
vlaeddy

---

### Post by bromix on 2007-10-17
Try installing xserver-xorg with apt in the command line, and keep the restricted driver enabled.  Then Control-ALT-Backspace and relog in.

---

### Post by bromix on 2007-10-17
The ati drivers are not compatible with AIGLX,  XGL is a layer that runs on top and uses OpenGL to display the effects of composite managers like Compiz.  When the new unified open source driver comes out from AMD, word is that it will support AIGLX, but until then we ATI's have to use XGL.

---

### Post by Bablefish on 2007-10-17
This is from a guy who is using Envy. You can use that and it works with most stuff including some 3D as long as you don't run anything to demanding.

---

