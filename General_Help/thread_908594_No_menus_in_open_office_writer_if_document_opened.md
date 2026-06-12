---
title: "No menus in open office writer if document opened"
date: 2008-09-02
forum: General Help
---

### Post by Zalbor on 2008-09-02
Basically as the title says... If I open OOwriter, there are no menus. Clicking the second X (which closes the document, but not the program) makes the menus appear. Starting a new blank document or opening one (of any type) makes them disappear again.
The other parts of OO aren't affected by this.

---

### Post by mike2357 on 2008-09-02
Very odd behavior.  Maybe one of your default files got corrupted.  You could rename the directory that contains your defaults, so that the next time you start openoffice, the directory will be re-created.  However, doing so will wipe out defaults that you've already set up.  The commands are:

```
cd
mv .openoffice.org2 .openoffice.org2.bak
```

If it doesn't help, post back.  Maybe someone else will have an idea.

---

### Post by Zalbor on 2008-09-04
No, that didn't help... Nor re-installing the openoffice-writer package. Thanks for the idea, however.

---

