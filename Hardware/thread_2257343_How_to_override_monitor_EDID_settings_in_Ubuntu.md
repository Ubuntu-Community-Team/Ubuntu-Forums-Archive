---
title: "How to override monitor EDID settings in Ubuntu ?"
date: 2014-12-19
forum: Hardware
---

### Post by rcbutcher on 2014-12-19
Greetings, first post.
I have an old but perfectly serviceable montitor which I need to use on a Ubuntu 12.04 LTS system. The monitor seems to have lost the abaility to reliably communicate its default resolution (1366 x 768) to the PC via EDID. Hence Ubuntu tries to define it as 1024 x 768.
Previously, this monitor worked fine on an OpenSuse system which had xorg.conf modified to explicitly provide default resolution without the need for EDID.
Ubuntu does not appear to use xorg.conf and ignored it when I added it.
So.. how to explicitly provide default monitor resolution in Ubuntu when EDID is broken/unreliable ? Where are the Ubuntu monitor settings defined ? The monitor is otherwise perfect and not ready for trashing.
thanks
Rod

---

