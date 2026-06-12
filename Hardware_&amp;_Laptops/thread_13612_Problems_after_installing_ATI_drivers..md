---
title: "Problems after installing ATI drivers."
date: 2005-02-01
forum: Hardware &amp; Laptops
---

### Post by lord_sean on 2005-02-01
I just installed the flgrx driver and set it up per the instructions posted here. Upon reboot I can run fglrxinfo and I get this.

display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON 9500 Pro Generic
OpenGL version string: 1.3.4510 (X4.3.0-3.12.0)

So I guess I got the install right, but when I go to change resoultions ( it defaulted to 1600X1200) I get this error.

The X Server does not support the XRandR extension.  Runtime resolution changes to the display size are not available.

Any idea how to fix this? I'm a total *nix newbie. Also, it shows Radeon 9500 pro Generic but I have a 9700 pro, Any issues there.

---

### Post by CreeVal on 2005-02-03
I have the same issue... please anyone?

---

### Post by malegria on 2005-02-03
I suggest you refer to this site to get your fglrx driver going. 
[HTML]http://xoomer.virgilio.it/flavio.stanchina/debian/fglrx-installer.html[/HTML]
I did it, and it all came together like gravy. Sure, this way will take about 20 minutes to do, but it's worth the wait to get something going *right.*

And at step 4 use the "make-kpkg" option, not the previous two (4.1, 4.2)

And another thing. If you want to find out your current kernel type, at a terminal type:
 ```
uname -r 
```

Run into any trouble, hit me back.

---

