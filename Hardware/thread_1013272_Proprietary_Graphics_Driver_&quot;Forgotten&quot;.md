---
title: "Proprietary Graphics Driver &quot;Forgotten&quot;"
date: 2008-12-16
forum: Hardware
---

### Post by pbh on 2008-12-16
On multiple laptops, and I think one or two desktops, I've had the same thing happen with proprietary graphics drivers.

First, I'll install ubuntu, and have full support for things like desktop effects.
Second, I'll use my machine for a while, and have no problems.
Third, after a bad suspend or perhaps after installing some software (I have a default list of things, including some compiz things, I think.) suddenly the proprietary hardware applet (and my graphics card in that list) disappears.
Fourth, I no longer have desktop effects, and when I try to turn it on in the Appearance menu, it says that it cannot be enabled after searching for drivers.

I'm not quite sure how to phrase this question, but does anyone know what might be causing this?

---

### Post by pbh on 2008-12-16
My problem ended up being fglrx, which I had installed on a different machine and ended up replicating to other machines.  Apparently just having fglrx installed breaks DRI even if you're not using it.

See [https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/295018](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/295018) .

---

