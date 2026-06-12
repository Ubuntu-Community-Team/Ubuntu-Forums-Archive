---
title: "Effects on at startup rather than by hotkey?"
date: 2008-08-11
forum: General Help
---

### Post by rmflagg on 2008-08-11
Hi everyone,
   I was wondering if there is an easy way to have certain effects start on rather than have to activate them by hotkey.  For instance, I would really like to have the ADD helper startup when I log in rather than have to hotkey it on.

Thanks,
RM Flagg

---

### Post by Diabolis on 2008-08-11
You can start any application or execute any command at start up if you add it to your sessions.

Go to: **System / preferences / sessions**

---

### Post by krsmit0 on 2008-08-12
this worked for me.

[http://forum.compiz-fusion.org/showthread.php?t=7359](http://forum.compiz-fusion.org/showthread.php?t=7359)

save this script in your home directory.

do...
> chmod a+x compiz-dbus-send.py
   to make it executable

then run this in a terminal to try it out
> ~/compiz-dbus-send.py addhelper toggle_key

add it to the session manager if it works.

---

### Post by rmflagg on 2008-08-14
Thanks krsmit0, that works perfectly!

RMFlagg

---

### Post by krsmit0 on 2008-08-16
i did it for the ADD helper, but quickly got annoyed with it.  I missed seeing all of my windows.

---

