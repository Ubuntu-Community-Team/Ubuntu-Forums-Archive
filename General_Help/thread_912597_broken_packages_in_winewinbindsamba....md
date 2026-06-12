---
title: "broken packages in wine/winbind/samba..."
date: 2008-09-06
forum: General Help
---

### Post by senectus on 2008-09-06
I've had this bugging me for weeks now and I want to get it fixed..
I've tried the edit -> fix broken packages -> mark all upgrades etc etc but it's not working.

If I look to see what is marked for upgrades it says it's wine 0.9.59-0ubuntu5 -> 1.0.0-1ubuntu4~hardy1

if I try to mark it for upgrades it says:
> wine:
 Depends: winbind but it is not going to be installed

So if I go mark winbind for install it says:
> winbind:
  Depends: samba-common (=3.0.28a-1ubuntu4) but 3.0.28a-1ubuntu4.5 is to be installed

If I look at samba-common it says it's already installed:
Samba-common   3.0.28a-1ubuntu4.5  ->  3.0.28a-1ubuntu4.5
So it's at the latest version...

can anyone help me fix this?

---

### Post by senectus on 2008-09-07
I'll only bump it once.. I promise :-)

---

### Post by SqRt7744 on 2008-09-13
Are you running a 64 bit system? I have the same problem when trying to install wine. I can install the version from winehq though...
[http://www.winehq.org/site/download-deb](http://www.winehq.org/site/download-deb)

---

### Post by senectus on 2008-09-14
nope i386 binaries only.

---

