---
title: "Move Wubi install"
date: 2008-09-21
forum: General Help
---

### Post by crobruncato on 2008-09-21
I'm having trouble with my laptop running xp sp3 and ubuntu in a wubi "partition". I'm thinking of nuking the drive and rebuilding. If, once I've got XP up again, I use wubi to install ubuntu, could I just move the old .disk with my build on it to the new setup?

---

### Post by ago on 2008-09-21
backup the ubuntu folder, then copy it back once you reinstall XP, then modify boot.ini manually (backup that too)

---

### Post by crobruncato on 2008-09-21
Do I need to backup the c:\wu<something>.mbr and the other wu<something stuff?

Thanks

---

### Post by ago on 2008-09-21
they are also in c:\ubuntu\winboot you will have to copy them from there to c:\

---

