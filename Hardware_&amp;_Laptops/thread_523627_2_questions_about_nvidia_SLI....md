---
title: "2 questions about nvidia SLI..."
date: 2007-08-12
forum: Hardware &amp; Laptops
---

### Post by Guyver1 on 2007-08-12
Hi.

ok number 1

how can you confirm that SLI is actually enabed on your machine?

and No.2

How can you change the render modes?

I want to use split frame rendering.

cheers :)

---

### Post by Guyver1 on 2007-08-13
bump

anybody?

---

### Post by Guyver1 on 2007-08-16
last call for SLI on linux......

no-one got any experience with SLI?

---

### Post by Guyver1 on 2007-08-16
answered my own question :)

[http://www.kevinbridges.org/linuxWoW](http://www.kevinbridges.org/linuxWoW)

[http://http.download.nvidia.com/XFree86/Linux-x86/1.0-8774/README/appendix-d.html](http://http.download.nvidia.com/XFree86/Linux-x86/1.0-8774/README/appendix-d.html)


Option "SLI" "string"

This option controls the configuration of SLI rendering in supported configurations.Value Behavior
0, no, off, false, Single Use only a single GPU when rendering
1, yes, on, true, Auto Enable SLI and allow the driver to automatically select the appropriate rendering mode.
AFR Enable SLI and use the alternate frame rendering mode.
SFR Enable SLI and use the split frame rendering mode.
SLIAA Enable SLI and use SLI antialiasing. Use this in conjunction with full scene antialiasing to improve visual quality.

---

