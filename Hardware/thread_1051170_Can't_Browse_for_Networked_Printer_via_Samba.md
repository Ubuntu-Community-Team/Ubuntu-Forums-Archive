---
title: "Can't Browse for Networked Printer via Samba"
date: 2009-01-26
forum: Hardware
---

### Post by natewiebe13 on 2009-01-26
im having troubles browsing for a network printer over samba. i can view the networked computers through nautilus, but when i go to add a computer, i can't press browse, its greyed out.

any ideas?

---

### Post by cariboo on 2009-01-26
It sounds like you are trying to add a printer as a normal user. If the Printing utility doesn't work when you go to System-->Administration-->Printing, try using the cups web interface. Open Firefox and type in the address bar:

```
http://localhost:631
```

Jim

---

### Post by natewiebe13 on 2009-01-27
it worked! thanks for the help.. i had a bit of trouble though getting the correct samba path, but i figured it out.

---

