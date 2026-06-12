---
title: "Performance problems after upgrade"
date: 2006-06-06
forum: Hardware &amp; Laptops
---

### Post by SPENEN on 2006-06-06
Hi!

When I first installed ubuntu on this laptop I noticed that it was lagging when I, for example, switched tabbs in firefox or changed desktop.
But when I upgraded to ubuntu dapper drake and the newest xorg things started to work perfectly, nothing lagged.
I had it like that for about 2 weeks and then when I started my computer all of a sudden the lagg was back.
Does anyone know what could have happened?

Maybe it's the new shadows and ransparancy functions that is lagging, because when I got rid of the lagg I tried to install compiz (or what its called) and then it started lagging again, so I removed it (and I've reinstalled ubuntu since then).

Any kind of help would be greatly apreciated!

---

### Post by SPENEN on 2006-06-06
I found this in /var/log :

(II) LoadModule: "GLcore"
(II) Loading /usr/lib/xorg/modules/extensions/libGLcore.so
dlopen: /usr/lib/xorg/modules/extensions/libGLcore.so: undefined symbol: __glXLastContext
(EE) Failed to load /usr/lib/xorg/modules/extensions/libGLcore.so
(II) UnloadModule: "GLcore"
(EE) Failed to load module "GLcore" (loader failed, 7)

---

