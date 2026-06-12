---
title: "How to recover from a faulty package"
date: 2009-06-18
forum: Installation &amp; Upgrades
---

### Post by dcroxton on 2009-06-18
I ended up with my apt database corrupted (it's a long story), so when I run the update-manager, I get the following error:

E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem.

But when I run the command, it configures a lot of packages but always gets stuck at the sun report builder for openoffice.org.  Is there any way I can remove this package so that I can proceed reconfiguring the rest of my system?

Sincerely,
Derek
[A curious little blog]("http://acuriouslittleblog.blogspot.com")

---

### Post by raymondh on 2009-06-19
Hello Derek,

Do you remember what you were installing?  

If so, you could sudo apt-get remove 'packagename' and the re-install.  

Another way is to check synaptic (system >admin) and check for broken packages, etc (look at filters tab).

Good luck.

---

### Post by dcroxton on 2009-06-21
I do know what package is causing it to hang:  the sun report-builder extension for OpenOffice.org.  Unfortunately, trying to remove it via apt-get remove causes the same lock-up that I get in the upgrade process.  (It really is a weird one, too:  I can't even kill the process with kill -9, and eventually the computer becomes completely unresponsive.)

So, I need some manual way to get the package out of the database.

Sincerely,
Derek Croxton

---

