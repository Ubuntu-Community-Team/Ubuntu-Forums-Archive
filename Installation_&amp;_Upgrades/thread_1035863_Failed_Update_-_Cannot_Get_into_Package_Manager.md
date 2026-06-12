---
title: "Failed Update - Cannot Get into Package Manager"
date: 2009-01-10
forum: Installation &amp; Upgrades
---

### Post by scott29 on 2009-01-10
I tried to install the latest security updates and something has failed.  Now, I cannot even get into the Synaptic Package Manager.  I get this error:

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.
E: _cache->open() failed, please report.

When I run the command it also aborts:

dpkg: ../../src/packages.c:221:  process_queue:  Assertion 'dependtry <=4' failed.
Aborted

I am quite a newbie so I have no idea how to fix this.  Any thoughts?

---

### Post by scott29 on 2009-01-10
FYI, most of the security updates installed.  The only one left is for samba.  Version 2:3.2.3-1ubuntu3.4

I am not sure if that helps but I thought I would add that.

---

### Post by cdtech on 2009-01-10
Try running this command and let me know:
```
sudo dpkg --configure -a && sudo apt-get -f install
```

---

### Post by scott29 on 2009-01-10
Got the same error message.

---

### Post by cdtech on 2009-01-10
Try cleaning the cache:
```
sudo apt-get autoclean && sudo apt-get autoremove
```

---

### Post by scott29 on 2009-01-10
Clearing the cache seemed to have worked.  I can get into Package Manager and the system is saying it is up to date.  

Thank You!!!

---

### Post by cdtech on 2009-01-10
Your welcome. Good luck...........

---

### Post by scott29 on 2009-01-10
Well unfortunately the problem seems to be deeper.  I tried to install a new package and it errored out.  I am again getting a similar message.  I tried to flush the cache or whatever, and not sure that worked.  I am attaching a log file.

Anybody have any ideas?

Thanks!
Scott29

---

