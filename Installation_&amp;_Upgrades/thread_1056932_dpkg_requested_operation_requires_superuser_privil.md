---
title: "dpkg: requested operation requires superuser privilege"
date: 2009-02-01
forum: Installation &amp; Upgrades
---

### Post by LepricahnsGold on 2009-02-01
Hi. N00b here. I tried updating with the Update Manager. Most went fine. I think the signal was interrupted at some point because if I run Update Manager now, I get this message:

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

O.K. On part 2, not much I seem to can do. So, I open terminal and type:
dpkg --configure -a and press enter. I then get this message:

dpkg: requested operation requires superuser privilege

I am the only user. What do I need to do to correct this or is it not a problem and I should just ignore it?

---

### Post by sisco311 on 2009-02-01
run the command as root:
```
sudo dpkg --configure -a
```
[uhelp]community/RootSudo[/uhelp]

---

### Post by LepricahnsGold on 2009-02-06
Ah. sudo. I'm such a newbie. I didn't even think to try that. OK. I will try sudo dpkg --configure -a

---

### Post by LepricahnsGold on 2009-02-06
OK, I ran sudo dpkg --configure -a. Now I get this: 
dpkg: ../../src/packages.c:221: process_queue: Assertion `dependtry <= 4' failed.
Aborted

Now what?

---

### Post by LepricahnsGold on 2009-02-15
I'm still getting the message:

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.
E: _cache->open() failed, please report.

Even after running sudo dpkg --configure -a I have updates available but they won't install. I just get the 
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.
E: _cache->open() failed, please report. 
message each time. What do I do to correct this?

---

### Post by ugm6hr on 2009-02-15
Something got corrupted during an update / install:
[http://techxplorer.com/2006/05/21/resolving-an-odd-dpkg-error-in-ubuntu/](http://techxplorer.com/2006/05/21/resolving-an-odd-dpkg-error-in-ubuntu/)
[https://bugs.launchpad.net/ubuntu/+source/dpkg/+bug/46530](https://bugs.launchpad.net/ubuntu/+source/dpkg/+bug/46530)

libc6 has been implicated in the bug report.

---

