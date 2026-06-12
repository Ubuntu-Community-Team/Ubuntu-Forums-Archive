---
title: "man broken in 8.04 hardy heron"
date: 2008-07-11
forum: General Help
---

### Post by huffy318 on 2008-07-11
if I run man, i get this error:

~ $ man ssh
pager: error while loading shared libraries: libxfcegui4.so.3: cannot open shared object file: No such file or directory
man: command exited with status 32512: pager -s

I am not sure why pager relies on libxfcegui4.  I have libxfcegui4.so.4 in /usr/lib/, so it may be a version problem.

Any ideas?

Thanks.

---

### Post by jonlemur on 2008-07-12
You may try running ```
ldconfig
``` I don't know if this has anything to do with your problem, but it should "create, update, and remove the necessary links and cache (for use by the run-time linker, ld.so) to the  most recent shared libraries found in the directories specified on the command line, in the file /etc/ld.so.conf, and in the trusted directories (/usr/lib and /lib)." (taken from its man page).

---

### Post by huffy318 on 2008-07-12
Thanks for the suggestion.  It didn't work, but it gave me an idea.

I whiched pager, and it was a pager I had compiled and placed in my bin dir.  I used to use it a long time ago.  I moved it out of my path, and now man works fine.

I have no idea why man resulted in a call to pager.

---

