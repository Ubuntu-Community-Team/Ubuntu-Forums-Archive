---
title: "Solved no CD sound problem."
date: 2005-04-29
forum: Hardware &amp; Laptops
---

### Post by map0598 on 2005-04-29
If you have the same problem try this:

From terminal enter: alsamixer
set PCM to "on" by toggling with m key

set IEC958 C to "on"  (ditto)

set VIA DXC control to volume (to find VIA DXC control I had to use > key to get all the way to the right side) and up key to set volume.

This worked for me after days of hunting for answers.  I have a M7VIG 400 motherboard with built in VIA 8233/8235/8237 AC97 Audio Controller.

Ubuntu is the greatest.

---

