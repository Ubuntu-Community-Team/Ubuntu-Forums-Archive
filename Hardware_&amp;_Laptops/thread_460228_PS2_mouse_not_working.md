---
title: "PS/2 mouse not working"
date: 2007-05-31
forum: Hardware &amp; Laptops
---

### Post by aporias on 2007-05-31
Hi,

I installed the alternate CD because I didn't want to bother with running the Live CD before getting to installation, and I find that my ps/2 mouse does not work in 7.04 as it did in 5.10 (that is, at all).  I tried changing the incorrect USB mouse settings in xorg.conf (/dev/input/mice) to the standard PS/2 settings (/dev/psaux) to no effect.  

"cat -f /dev/psaux" and moving the mouse does nothing.  Before doing this I messed with gpm too to try to get a mouse in the console.  There's a gpm-* (I don't remember the exact name) script to locate the mouse, but this was unsuccessful.  Has anyone else seen this or does anyone know how to handle it?

Thanks.

---

