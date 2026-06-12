---
title: "dpkg interrupted / Firefox wont open"
date: 2008-09-28
forum: General Help
---

### Post by tonkers on 2008-09-28
First of all, I cannot login to GNOME or Xclient without it freezing, so I have to use failsafe GNOME. I was installing my updates, when all of a sudden, it froze, so I reboot my computer. I try to update again, but I got the error "E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. E: _cache->open() failed, please report.

So I go open terminal and type in "sudo dpkg --configure -a" and it says 
"dpkg: parse error, in file `/var/lib/dpkg/updates/0071' near like 15 package `gcalctool':
 E0F during value of field `Description' (missing final newline)

So that was the first problem. The second one is that when I try to open Firefox, the starting firefox thing comes up, and then after a while, it closes and nothing happens.

Help? Thanks.

---

### Post by nowshining on 2008-09-28
in a terminal start firefox and note the error messages if any...

---

