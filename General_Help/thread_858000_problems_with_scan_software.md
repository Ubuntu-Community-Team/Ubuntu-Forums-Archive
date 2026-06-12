---
title: "problems with scan software"
date: 2008-07-13
forum: General Help
---

### Post by Vinger on 2008-07-13
Hello,

I try to scan a document with my epson perfection 1670. I installed both Kooka and xsane but none works.
>  oen@kubuntu-desktop:~$ kooka
KCrash: Application 'kooka' crashing...
koen@kubuntu-desktop:~$ xsane
Segmentatiefout

when i try to run it as a root, everythings works fine (in the beginning)
I can scan documents, but i cannot save them...

What can i do???

Tx, grz

---

### Post by editrix on 2008-07-13
I'm no expert, but I've discovered that you have to add yourself to the scanner group.

Open up the Control Centre, then System Administration/User management.

If that doesn't work, then I don't know what else to do. But at least I've bumped the post :-)

---

### Post by Alec Fearon on 2008-07-13
Thank you for the advice - it works! I'm using Ubuntu and have been trying for weeks to get it to recognise my scanner. As you suggest, the answer is to go into User Admin, set the 'use scanner' priviledge in the root account and then in my own account, re-boot and hey presto.

---

### Post by Vinger on 2008-07-14
tx for the advice...
I'm already in the scanner group... (use scanner is activated...)

anyone else an idea?

grz

---

### Post by editrix on 2008-07-15
> **Vinger said:**
> tx for the advice...
I'm already in the scanner group... (use scanner is activated...)

anyone else an idea?

grz

Go to uboontu.com (link in my sig) and search the make and model of your scanner. Only other idea I can come up with :-)

---

