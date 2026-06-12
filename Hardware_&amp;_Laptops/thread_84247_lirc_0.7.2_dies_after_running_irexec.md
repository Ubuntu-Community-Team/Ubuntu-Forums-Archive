---
title: "lirc 0.7.2 dies after running irexec"
date: 2005-10-30
forum: Hardware &amp; Laptops
---

### Post by Blackie_Chan on 2005-10-30
I have been able to successful install lirc 0.7.2 on breezy (I ran **irw** and the buttons pressed on the remote were recognized). Anyhow, the problem is when I run **irexec -d** as a user, lirc dies.

How can I fix that problem so I can use my remote with tvtime?

---

### Post by Blackie_Chan on 2005-10-30
I fixed the problem. /dev/lirc is the default device used by lircd, but didn't exist after I installed lirc (/dev/lirc0 existed though), so I had to set the device to /dev/lirc0

---

