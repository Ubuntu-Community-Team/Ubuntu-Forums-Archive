---
title: "Enable Direct Rendering on 945gm - Dapper"
date: 2007-06-04
forum: Hardware &amp; Laptops
---

### Post by embeemb on 2007-06-04
I have an Intel chipset 945gm on an HP pavilion dv1000 with Dapper running. I've been desperately trying to enable direct rendering to no avail. I'm not sure what kind of further info one would need to steer me in the right direction.

PLEASE help ! 

Thanks

---

### Post by Brinstar on 2007-06-04
i don't know about the version of xorg that comes w/ dapper, but xorg 7.2 should include full DRI support for your card.

[http://www.intellinuxgraphics.org/](http://www.intellinuxgraphics.org/)

---

### Post by embeemb on 2007-06-04
I have Xorg 7.0

Not too sure how to upgrade. Can you help please ?

---

### Post by Brinstar on 2007-06-04
i'm not on ubuntu (read my sig) but i'm guessing it's something like:

apt-get upgrade xorg-core 
 or
apt-get upgrade xserver-xorg-core

trial and error is your best teacher though :) actually that should be in my sig too lol

---

