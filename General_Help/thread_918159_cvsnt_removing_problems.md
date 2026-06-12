---
title: "cvsnt removing problems"
date: 2008-09-12
forum: General Help
---

### Post by krav666 on 2008-09-12
I'm trying set up a cvs on my ubuntu 8.04, and i installed cvsnt, but since i cannot find decent documentation on how to actually start it up, i decided to remove it and go for "old" cvs.

Now the problem i have is that i cannot uninstall cvsnt.


Removing cvsnt ...
Stopping CVSNT Lock Server Daemon: invoke-rc.d: initscript cvsnt, action "stop" failed.
dpkg: error processing cvsnt (--purge):
 subprocess pre-removal script returned error exit status 1
Starting CVSNT Lock Server Daemon: cvslockd.
Errors were encountered while processing:
 cvsnt
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:


any suggestions?

---

### Post by krav666 on 2008-09-14
bump for fear of reinstalling ubuntu just cause of this :(

---

### Post by spacedoubtman on 2009-01-23
I get this same problem - don't suppose you found a fix.

---

### Post by spacedoubtman on 2009-01-23
I removed it - just after posting. For some reason you need to first start the service then it uninstalls fine.

sudo /etc/init.d/cvsnt start


Not that great if the problem you had was actually starting the service.

---

### Post by krav666 on 2009-01-26
I couldnt resolve the problem so easy... i reinstalled ubuntu...

later i found that i prolly setup everything wrong, and that i didnt need to reinstall everything, but, hey you learn the most by your mistakes :)

sorry for the lack of easier solution, i'm still not that well versed in linux(ubuntu) :/

---

