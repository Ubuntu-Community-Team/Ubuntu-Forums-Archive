---
title: "I can't su"
date: 2005-11-14
forum: General Help
---

### Post by mespork on 2005-11-14
hi,

for some reason my system just stopped letting me su. I can still sudo so it isn't a huge deal but I just was wondering how to fix this.

Thanks

---

### Post by Samuel on 2005-11-14
```
sudo -s
```
works like the su command,
if you do that to get root, then use the command   passwd   to set a new root password does it work?

---

### Post by uberlinux on 2005-11-15
from the command line:
sudo passwd
then:
su

---

### Post by Zwack on 2005-11-15
Does su give any error messages?  It's not all that common for commands to fail silently...

Can you do a strace su?  What does that look like?  (It will be a whole heap of debugging information, remeber to remove your password from the debugging read command...)

Z.

---

### Post by mespork on 2005-11-15
I just get the "Authentication failure sorry" message. It's polite, but fustrating

I just got it fixed with the passwd command, thanks guys.

---

