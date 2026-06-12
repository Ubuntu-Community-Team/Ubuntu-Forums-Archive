---
title: "Problems with Avant Window Navigator Applets on Hardy x64"
date: 2008-08-10
forum: General Help
---

### Post by Sputz on 2008-08-10
Hey all,

First off apologies if this has been covered before, but I haven't been able to find an answer that has worked yet.

Basically I installed AWN which works fine, I followed all the instructions as to how to install the applets package, yet I receive the same error message every time...

   Some packages could not be installed. This may mean that you have
   requested an impossible situation or if you are using the unstable
   distribution that some required packages have not yet been created
   or been moved out of Incoming.

   Since you only requested a single operation it is extremely likely that
   the package is simply not installable and a bug report against
   package should be filed.
   The following information may help to resolve the situation:

   The following packages have unmet dependencies:
   awn-extras-applets-trunk: Depends: libawn0-trunk (>= 0.3.0) but it is not going to be installed
   Depends: libgnome-desktop-2-7 (>= 1:2.23.5) but it is not installable
   Depends: libgtk2.0-0 (>= 2.13.6) but 2.12.9-3ubuntu4 is to be installed
   Depends: libgtop2-7 (>= 2.23.2) but 2.22.0-0ubuntu1 is to be installed
   Depends: libpango1.0-0 (>= 1.21.3) but 1.20.5-0ubuntu1 is to be installed
   Depends: libpopt0 (>= 1.14) but 1.10-3build1 is to be installed
   Depends: libwebkit-1.0-1 (>= 0~svn31841) but it is not installable
   Depends: libxcb-render-util0 but it is not installable
E: Broken packages


...If anyone could help me out I would much grateful! I'm running Ubuntu Hardy Heron 64 bit, if you need anymore information just let me know.

Thanks in advance.

Jarred

Thanks in advance.

---

### Post by Sputz on 2008-08-13
Has anyone encountered this problem before? Any help would be much appreciated!

Ciao
Jarred

---

### Post by moonbeam on 2008-08-13
> **Sputz said:**
> Has anyone encountered this problem before? Any help would be much appreciated!

Ciao
Jarred

I believe you need to enable some additional Ubuntu repos for updated packages... I'm kind of tired so I'm not going to look them up but if you do a search for Reacocard's awn support thread the necessary settings are listed in the first post.

---

