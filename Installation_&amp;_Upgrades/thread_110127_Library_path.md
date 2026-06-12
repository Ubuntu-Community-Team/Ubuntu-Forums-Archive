---
title: "Library_path"
date: 2005-12-30
forum: Installation &amp; Upgrades
---

### Post by o----o on 2005-12-30
hello

where are path to libraries defined in ubuntu?
I looked at /etc/ld.so.conf and this file is absoutly empty.

& how can I administrate them or change them.
I tried compile one opencv examle and it could not find library which is in usr/local/lib.> 

root@desire:~# /usr/local/share/opencv/samples/c/squares
/usr/local/share/opencv/samples/c/squares: error while loading shared libraries: libcxcore.so.0: cannot open shared object file: No such file or directory

thx jm

---

### Post by ant35mi on 2007-05-04
i have the same problem

ive installed a new library....the libray is in its directory 

libXp.so.6: cannot open shared object file: No such file or directory occurred..

/usr/X11R6

but i receive alway the same error.....library cant be found ...or something close to this.

How can i set LD_LIBRARY_PATH ...thx in advance

---

