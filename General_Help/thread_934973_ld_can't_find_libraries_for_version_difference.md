---
title: "ld can't find libraries for version difference"
date: 2008-10-01
forum: General Help
---

### Post by jutirain on 2008-10-01
For some reason (see [http://ubuntuforums.org/showthread.php?t=934925](http://ubuntuforums.org/showthread.php?t=934925)), I edit the /etc/ld.so.conf

After that, /usr/bin/ld can't find libraries if the name of the .so are slightly different.

e.g., if I use -lcv
Only should I rename libcv.so.1.0.0 to libcv will the /usr/bin/ld find them.
(I've tried sudo ldconfig but no help)

So, what's the problem? How can I restore the ability of linking .so files with a slightly difference?

My /etc/ld.so.conf look like this now:
/usr/lib
/usr/local/lib
include /etc/ld.so.conf.d/*.conf

And my libcv is located at:
/usr/lib/libcv.so.1.0.0
/usr/lib/libcv.so.1

---

