---
title: "Access Database in Ubuntu, OO doesn't work"
date: 2008-11-07
forum: General Help
---

### Post by monsieurdozier on 2008-11-07
I run a small business and I had a database made.  The database was made in Microsoft Access, and I run Ubuntu 8.04.1 .  I really don't want to have to run the database in Access through a virtual machine, but for some reason Open Office wants to open the database in the Word Processor, and all I see is garabage.

Can someone help me figure out how to get this working.

-Monsieur Dozier

---

### Post by tagbre on 2008-11-07
Kexi (Koffice's data base component) can import Access data bases. It doesn't import everything, but you could give it a try. It worked for me.

---

### Post by scouser73 on 2008-11-07
You may be able to run the MS Access database using WINE.

---

### Post by monsieurdozier on 2008-11-07
> **tagbre said:**
> Kexi (Koffice's data base component) can import Access data bases. It doesn't import everything, but you could give it a try. It worked for me.

I tried Kexi, it says that it cannot find the appropriate migration driver.

Monsieur Dozier

EDIT:

I found the migration driver, but nothing happens when I try to import it.

KCrash: Application 'kexi' crashing...
KCrash cannot reach kdeinit, launching directly.

---

