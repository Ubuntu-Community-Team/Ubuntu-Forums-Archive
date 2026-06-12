---
title: "VMware and variable linux header file locations"
date: 2009-06-30
forum: Installation &amp; Upgrades
---

### Post by oregonbob on 2009-06-30
Whenever I upgrade my Ubuntu 8.10 kernel I have to recompile vmware 3.0 or it will not start. VMware compile script always asks for location of header files, and assumes a default of /usr/src/linux/include. It then tests for dependencies that always seem to fail and each time I wind up hacking on it for hours to figure out where the header files are now and get it to work.

Does anyone else have an easier way all figured out?

---

### Post by frenkel on 2009-06-30
Just make a symlink from /usr/srv/linux/ to /usr/src/linux-headers-<yourcurrentversion>/. It's as easy as that!

---

### Post by oregonbob on 2009-06-30
Thanks, your comments helped me dig in one more time, even though they are wrong but close. I figured it out at least. This worked:

ln -s /usr/src/linux-headers-2.6.27-14-server/include /usr/src/linux/include

I guess yours would have worked too, I can't figure out how to delete this reply.

---

