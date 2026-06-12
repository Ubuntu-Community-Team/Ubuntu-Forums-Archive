---
title: "How to remove *.*~ files"
date: 2008-10-11
forum: General Help
---

### Post by silent contender on 2008-10-11
How do I delete files that are *.*~ files?

I think they are temporary files, and these files are scattered all over the place.  They seem to take a good deal of space on my hard drive.

Would a shell script work, or is this not necessary?

---

### Post by OutOfReach on 2008-10-11
You can delete them by hand, or you can do it from a terminal:
```
rm *.*~
```

*.*~ files are backups usually made by text editors.

---

### Post by silent contender on 2008-10-11
Thanks.

I assume nothing bad should happen (i.e. deleting important files maybe).  I planned to do it that way, but wasn't sure if it was safe.

---

### Post by bodhi.zazen on 2008-10-11
> **silent contender said:**
> How do I delete files that are *.*~ files?

I think they are temporary files, and these files are scattered all over the place.  They seem to take a good deal of space on my hard drive.

Would a shell script work, or is this not necessary?

Yes , those are back up files.

You can trun the auto back up feature off on gedit :

Open gedit

Go to Edit-> Preferences

Editor tab

remove the check from the two boxes under "File saving" (or at least "Create a backup copy of files before saving"

Other editors (nano, OOO, etc) use other methods ...

---

### Post by silent contender on 2008-10-11
Thanks.

Where could I find how to turn off these auto-back setting?  Would Google be good enough?

---

### Post by bodhi.zazen on 2008-10-11
what editor are you using ?

---

### Post by silent contender on 2008-10-11
I am using KEdit, Kate, OOo, and any in KDE.

---

