---
title: "Emesene problems... Again!"
date: 2008-09-13
forum: General Help
---

### Post by Auximenes on 2008-09-13
Hi All

Today, I unsucessfully tried to install Emesene, and ended up having the same problems as this thread describes:

[http://ubuntuforums.org/showthread.php?t=510378]("http://ubuntuforums.org/showthread.php?t=510378")

As the thread dictated, I tried running:
> sudo dpkg -r --force-depends --force-remove-reinstreq emesene

but instead of the desired result I get:
> pontifex@augustus:~$ sudo dpkg -r --force-depends --force-remove-reinstreq emesene
dpkg - warning, overriding problem because --force enabled:
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
(Reading database ... 135286 files and directories currently installed.)
Removing emesene ...
The generated cache was invalid.
dpkg: error processing emesene (--remove):
 subprocess post-removal script returned error exit status 1
Errors were encountered while processing:
 emesene


And the problem is unresolved

Any help would be very much appreaciated as it locks up my entire dpkg, and makes me unable to neither install nor do upgrades

---

### Post by Sef on 2008-09-13
Why don't you down load it from the repositories?  

Applications > Add/Remove > show: change to 'All available Applications' > search: emesene > check the box next to emesene > apply changes > apply > close.

---

### Post by Auximenes on 2008-09-14
It's not on my list, and my problem is not downloading and installing it, but the broken package blocking my dpkg

---

