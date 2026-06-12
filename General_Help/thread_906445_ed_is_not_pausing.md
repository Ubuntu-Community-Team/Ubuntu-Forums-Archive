---
title: "ed is not pausing"
date: 2008-08-31
forum: General Help
---

### Post by Lary Grant on 2008-08-31
**ed** is supposed to pause for every screen of output when you give a command like
  ```
%p
```However it's not doing that on my Ubuntu Desktop (Hardy) system.... instead it never pauses and scrolls off the screen.

I also have a debian server machine which I access through ssh, and **ed** does the paging fine there, no matter what the size of the shell window is.

How do I get **ed** to pay attention to the window size?

---

### Post by Lary Grant on 2008-09-02
It turns out that **ed** is indeed paying attention to the terminal window size on Ubuntu, because the **z **command stops after every screenful.  However the **p** and **n **commands don't pause every screenful waiting for me to press <RETURN>, like they do on my Debian system.

I did:
```
# strings /bin/ed|grep -i return
Press <RETURN> to continue...
#
```on my Debian system, but on Ubuntu this same command returns nothing.  So it seems that there is a different version on Debian.  Why is that, and how do I get the version that pauses onto my Ubuntu system?

---

