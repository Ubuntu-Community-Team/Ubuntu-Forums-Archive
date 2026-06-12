---
title: "Nautilus"
date: 2008-09-10
forum: General Help
---

### Post by masoud23 on 2008-09-10
How do I give permanent permission to nautilus to crate map and copy file in to Filesystem.

---

### Post by kokkus on 2008-09-10
gksudo nautilus

---

### Post by masoud23 on 2008-09-10
This works only one time! I have to do this every time i start the camputer.

---

### Post by kokkus on 2008-09-10
It works every time. Open nautilus as root (gksudo) and change the directory promission settings to (read and write) and (create and delete files).
If you have to do stuff with root access everytime u start your pc, create a new starter in system > Administrator > sessions.
And then click Add, and add the command gksudo nautilus.

That's maybe a risk to take if many people are on your PC. Then you can login as root (shell) with username root and the password should be passwd.

Good Luck :)

---

