---
title: "the apparmor's proplem"
date: 2009-08-23
forum: Installation &amp; Upgrades
---

### Post by fanglinyong on 2009-08-23
hello, everybody:
   today , i upgrade my kernel to 2.6.30,after i reboot my pc, the system say "the apparmor moudle faild", how to reslove my question?
i used ubuntu-desktop-9.04
   thanks everybody!!!

---

### Post by Kobalt on 2009-08-23
Try to relaunch AppArmor from the command line and tell us what's the ouput : 
```
/etc/init.d/apparmor restart
```

---

### Post by fanglinyong on 2009-08-24
> **Kobalt said:**
> Try to relaunch AppArmor from the command line and tell us what's the ouput : 
```
/etc/init.d/apparmor restart
```
first ,thanks your reply!
now, when i ex the code ,system says:
starting apprmor .....
loading apprmor moudle [faild]

---

### Post by stlsaint on 2009-08-24
alright be careful at this point...granted i dont know much about the app you are referring to but i have had issues once i updated my kernel to 30 or the "candela image" as my system showed it as!! i couldnt update or anything nor add any new programs due to this update to kernel...i ended up having to roll back to my previous kernel but i guess i did something wrong because after i did that not only could i not add any programs but i coulndt launch any either causing me to do a fresh install...this is the point when i tell you to do a backup of your system using the simple backup config tool...before you start trying to fix the kernel...and before you make a decision make sure you do lOTS of research on the issue!!

---

### Post by pawhtiobo on 2009-08-24
Hi :)

That's a normal error with the 2.6.30 Kernel, remember that Kernel not in production yet, so...some features are not available with it... i'm saying that because i had that same issue, and when i googled, that was the explanation that was given to me...

see ya...

---

### Post by fanglinyong on 2009-08-24
o ,it's a bad news to me !
but ,is there  haven't a good method to resloved this bug?

---

### Post by pawhtiobo on 2009-08-24
Hi :)

The bug is reported here:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/375422](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/375422)

see ya...

---

### Post by fanglinyong on 2009-08-24
its really  a bad news for whom used the kernel 2.6.30!
so when i view what your said,i decided to remove this kernel!
now ,it worked correctly!!

---

