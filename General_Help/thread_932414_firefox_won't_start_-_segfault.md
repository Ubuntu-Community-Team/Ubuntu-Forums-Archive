---
title: "firefox won't start - segfault"
date: 2008-09-28
forum: General Help
---

### Post by leith98b on 2008-09-28
I'm trying to launch firefox in xubuntu 8.04.  I've installed all the recent updates and it appears one of them broke firefox.

When I launch it from command line, I get a "Segmentation Fault" error.  Running strace on it has the following for the last few lines:

stat64("/usr/lib/xulrunner-1.9.0.3/components/websrvcs.xpt", {st_mode=S_IFREG|0644, st_size=14742, ...}) = 0
open("/usr/lib/xulrunner-1.9.0.3/components/websrvcs.xpt", O_RDONLY|O_LARGEFILE) = 14
read(14, "XPCOM\nTypeLib\r\n\32\1\2\0Q\0\0009\226\0\0\0\"\0\0\10"..., 14742) = 14742
brk(0x8137000)                          = 0x8137000
close(14)                               = 0
stat64("/usr/lib/xulrunner-1.9.0.3/components/pipnss.xpt", {st_mode=S_IFREG|0644, st_size=12844, ...}) = 0
open("/usr/lib/xulrunner-1.9.0.3/components/pipnss.xpt", O_RDONLY|O_LARGEFILE) = 14
read(14, "XPCOM\nTypeLib\r\n\32\1\2\0B\0\0002,\0\0\0\"\0\0\7Y"..., 12844) = 12844
--- SIGSEGV (Segmentation fault) @ 0 (0) ---
+++ killed by SIGSEGV +++


I know firefox itself was just recently updated, but I seem to recall some other recent updates (side question: is there a way to list the recent system updates?  Can I undo them?)

Any help would be appreciated.  Thanks!

---

### Post by leith98b on 2008-09-28
Got it working by completely removing xulrunner & firefox, then reinstalling them.

---

