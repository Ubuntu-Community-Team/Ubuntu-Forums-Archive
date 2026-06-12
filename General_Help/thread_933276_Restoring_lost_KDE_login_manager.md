---
title: "Restoring lost KDE login manager"
date: 2008-09-29
forum: General Help
---

### Post by downlode on 2008-09-29
Hello,

I recently tried upgrading KDE to 4.1 but didn't really like the result, so I removed it and returned to 3.5.9. However, apt-get didn't remove it cleanly, and /usr/lib/kde4 was left over, so I deleted that. Unfortunately, in the upgrade the system was set to use the KDE4 login manager, and this setting wasn't changed back when I removed KDE4. So I'm now getting a terminal login at startup. What should I change to get the KDE 3.5 login manager working again?

Cheers,

Earle.

---

### Post by dagoss on 2008-09-29
check the file */etc/X11/default-display-manager*.  It should have one line that links to kdm.  Make sure that is referring to the proper location.  If it says something like /usr/sbin/kdm, then you probably need to remove /usr/sbin/kdm and make a link to whereever the binary is (use the whereis command to find it).

---

### Post by downlode on 2008-09-30
Ah - it was still set to /usr/lib/kde4/kdm. Thanks! That fixed it.

---

### Post by greyblitz on 2008-10-06
I seem to have a similar problem as well. However, when I am brought to the terminal at startup, I can tell it is trying to load KDE4 because I recognize the cursor, but after that it goes black and stays there. It goes black while I am in the middle of typing a command so I had no choice but to use the LiveCD. 

I checked and it seems to be pointing in the correct location of /usr/bin/kdm. What else is wrong?

---

