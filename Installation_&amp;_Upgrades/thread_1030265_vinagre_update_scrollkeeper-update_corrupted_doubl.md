---
title: "vinagre update: scrollkeeper-update: corrupted double-linked list: 0x08052238"
date: 2009-01-04
forum: Installation &amp; Upgrades
---

### Post by Browser_ice on 2009-01-04
Did a system update on my 256Mb laptop and got an error on the update of vinagre. Anyone know what this is about ?

...
Setting up vinagre (0.5.1-0ubuntu1.1) ...
*** glibc detected *** scrollkeeper-update: corrupted double-linked list: 0x08052238 ***
===== Backtrace: ====
/lib/tls/i686/cmov/libc.so.6[0xb7cd2d0d]
/lib/tls/i686/cmov/libc.so.6(cfree+0x90)[0xb7cd64f0]
/lib/tls/i686/cmov/libc.so.6(fclose+0x134)[0xb7cc13e4]
scrollkeeper-update[0x804a37d]
/lib/tls/i686/cmov/libc.so.6(_libc_start_main+0xe0)[0b7c7d450]
scrollkeepr-update[0x8048f91]
===== Memory map: ===
...
dpkg: error processing vinagre (--configure):
 subprocess post-installation script returned error exit status 134
...
A package failed to install. Trying to recover:
Setting up vinagre (0.5.1-0ubuntu1.1) ...

---

### Post by Browser_ice on 2009-01-10
So after having posted this one week ago no one have any idea on this ?

---

