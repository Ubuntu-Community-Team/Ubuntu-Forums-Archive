---
title: "Cannot empty external HD trash can..."
date: 2008-09-20
forum: Hardware
---

### Post by wayneo on 2008-09-20
Hi All,
I have a Dell Insp.600 and a Buffalo external HD @320GB.
I cannot empty the items I deleted from my Buffalo.
Any help?
Thanks for your time.
All the best,
Wayneo

---

### Post by ladr0n on 2008-09-20
This is probably a permission issue.  Hit F2 and type "gksu nautilus" to open nautilus with root permissions.  Navigate to the drive's trash folder (you may have to hit ctrl + h to show hidden files, as it's probably the hidden file '.trash') and empty it that way.  If that doesn't work, this is a more complicated problem.

---

### Post by wayneo on 2008-09-21
Thanks Ladr0n,
that did the trick!
All the best, and thanks for your time!
Wayneo

---

