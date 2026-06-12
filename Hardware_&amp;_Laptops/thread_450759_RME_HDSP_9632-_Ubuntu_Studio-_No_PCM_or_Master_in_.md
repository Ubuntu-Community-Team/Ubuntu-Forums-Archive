---
title: "RME HDSP 9632- Ubuntu Studio- No PCM or Master in Mixer"
date: 2007-05-21
forum: Hardware &amp; Laptops
---

### Post by neomad on 2007-05-21
Hello:

I've installed ubuntu studio, and everything works fine, except my RME HDSP 9632.

I've installed HDSP Alsa drivers, I've flashed card with last bios and everything should be ok... except that I do not have any way to sound. 

Any idea ? Thanks in advance.

neomad.

---

### Post by kkz on 2007-06-15
You should install (compile) latest alsa, because it supports bios version 1.52 and all of new functions. For volume control,  use hdspmixer from alsa tools, not standard mixer.

Good luck

---

