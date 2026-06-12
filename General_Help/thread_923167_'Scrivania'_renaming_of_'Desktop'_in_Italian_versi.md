---
title: "'Scrivania' renaming of 'Desktop' in Italian version"
date: 2008-09-18
forum: General Help
---

### Post by mizar001 on 2008-09-18
Hi. I'm having serious problem with the italian version of Ubuntu, and most of the problems come from the translation of a key word 'Desktop', translated as 'Scrivania'.

This is unacceptable, because many international application will place an icon in the standard 'Desktop' folder, and in an italian version, this icon does not appear on the effective desktop.

Other applications assume a link to 'Desktop' and this is not changeable. The only thing that italian version should do is to place a symlink to 'Desktop' or vice-versa.

Think if italian version had translated words like 'home','etc','usr'. The system will be completely unusable.

---

### Post by Pro-reason on 2008-09-18
The paths /usr, /etc and /home do not change, because they are fundamental parts of the Unix hierarchy, and not necessarily seen by the user.

~/Desktop is different because it is simply a directory in the user's home directory.  It makes sense for it to change.  The problem is with applications which wrongly assume that the desktop will be located there.  Such things ought to be handled by environment variables.

You could try writing to the creators of offending apps.  Meanwhile, a symbolic link is all you need to do.

---

