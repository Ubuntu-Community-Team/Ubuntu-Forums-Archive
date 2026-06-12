---
title: "Where is pmount 0.9.6 ???"
date: 2005-12-03
forum: Hardware &amp; Laptops
---

### Post by jsonder on 2005-12-03
I've been trying to get the floppy access patched, but this was removed from the "Dapper" repository but doesn' t seem to be available yet for Breezy.

Anyone know where pmount 0.9.6 is located?  

Thanks,
John

---

### Post by hajk on 2005-12-03
In breezy-backports...

---

### Post by jsonder on 2005-12-03
I must be really dumb.  All that I find is 0.9.5

Any idea what is should be doing?

---

### Post by joess on 2005-12-03
read here...[http://www.ubuntuforums.org/showthread.php?t=85777&highlight=pmount]("http://www.ubuntuforums.org/showthread.php?t=85777&highlight=pmount")

EDit: go to system\administration then to snaptic package manger, then settings, then repositories, then add, then custom, copy paste this link  deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper main restricted, ok, ok, then search for pmount you will see it. when done remove the link you put in

---

### Post by jsonder on 2005-12-03
[QUOTE=joess]read here...[http://www.ubuntuforums.org/showthread.php?t=85777&highlight=pmount]("http://www.ubuntuforums.org/showthread.php?t=85777&highlight=pmount")

EDit: go to system\administration then to snaptic package manger, then settings, then repositories, then add, then custom, copy paste this link  deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper main restricted, ok, ok, then search for pmount you will see it. when done remove the link you put in[/QUOTE]


Nope, it's been removed accordong to your URL

---

### Post by jsonder on 2005-12-03
Well, I managed to download it so it had to be there.

Modified fstab and all is well now.

Thanks!!

John

---

