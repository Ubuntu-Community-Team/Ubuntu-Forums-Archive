---
title: "Installing nVidia GeForce FX 5200 on 2.6.30 kernel"
date: 2009-07-13
forum: Installation &amp; Upgrades
---

### Post by 0x845fed on 2009-07-13
Hello,

I'm trying to learn a bit about the kernel, have compiled and installed kernel 2.6.30 from source (Ubuntu 9.04, fully updated).

I have an nVidia GeForce FX5200 that works perfectly with 2.6.28, but I can't get the drivers installed on the 2.6.30 kernel.

Here's what I've done:
[LIST=1]
[*]Downloaded the module's source from nVidia (version 173.14.20)
[*]sh <file> -x (to extract only)
[*]make
[*]make module
[*]make install
[*]Everything makes and installs without error
[/LIST]

However, when I try to enable "Extra" Visual Effects, an error is returned, "Desktop effects could not be enabled."  

Minimum requirements for the module is kernel 2.4.xx so I'm fine there.  Is there anything else I'm missing?  I've checked the bug reports, but the solutions don't seem to work for me.

Cheers!

---

### Post by master_kernel on 2009-07-13
It would probably be easier to run the sh file with the -K option as root.

---

