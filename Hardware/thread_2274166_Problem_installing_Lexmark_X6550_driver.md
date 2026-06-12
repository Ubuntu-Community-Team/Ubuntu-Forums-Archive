---
title: "Problem installing Lexmark X6550 driver"
date: 2015-04-18
forum: Hardware
---

### Post by orion_134 on 2015-04-18
Trying to install after unpacking tar:

jd@M4500:~$ sudo ./lexmark-08z-series-driver-1.0-1.i386.deb.sh 
Verifying archive integrity... All good.
Uncompressing nixstaller..............................................................
Collecting info for this system...
Operating system: linux
CPU Arch: x86_64
Warning: No installer for "x86_64" found, defaulting to x86...
Error opening terminal: xterm.

However, the command xterm opens the xterm terminal just fine.

Thoughts?

---

### Post by Vladlenin5000 on 2015-04-18
That printer is very old, the drivers is 32-bit only... No, you won't be able to install with that. It's either natively supported by now or you better start thinking about a new one.

---

### Post by orion_134 on 2015-04-19
Well that stinks...

---

### Post by mörgæs on 2015-04-19
Have you tried installing on a 32 bit system?

---

