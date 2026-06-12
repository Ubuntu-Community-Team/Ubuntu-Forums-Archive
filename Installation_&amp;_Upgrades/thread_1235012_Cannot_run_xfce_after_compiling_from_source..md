---
title: "Cannot run xfce after compiling from source."
date: 2009-08-08
forum: Installation &amp; Upgrades
---

### Post by dE_logics on 2009-08-08
I compiled xfce, but I'm not able to successfully log into it...it says my session lasted for less than 10 seconds and all...you know.

I compiled all the packages of xfce.

What I did differed from what the xfce documentation told me cause.....what it said, apparently, did not work. For starters, there was no configure script in the parent directory.

---

### Post by kerry_s on 2009-08-08
why? there are debs.

---

### Post by dE_logics on 2009-08-08
Performance.

---

### Post by kerry_s on 2009-08-08
> **dE_logics said:**
> Performance.

:lolflag:

have you tried deleting some of the old settings?
looking in my home, i would probably delete ".Xauthority & .ICEauthority" as those have to do with log in, you should probably do it from fail safe terminal or rescue mode. in fail safe terminal you should be able to use your file manager to make things easy to locate.

---

### Post by dE_logics on 2009-08-10
Nope...it's not working.

---

### Post by dE_logics on 2009-08-25
So...no one knows what might be hapenning?

---

### Post by dE_logics on 2009-08-27
Pls man...I already compiled all the packages...if no one helps, I have to remove them all...and that's a separate issue.

---

### Post by dE_logics on 2009-08-28
There's absolutely no one who's tried all this so far?

Am I the first individual to do this?

---

### Post by dE_logics on 2009-08-28
Issue resolved...add
```
/usr/local/lib
```

to /etc/ld.so.conf and then run ldconfig as root.




So...can anyone tell me what did I do till now?

---

