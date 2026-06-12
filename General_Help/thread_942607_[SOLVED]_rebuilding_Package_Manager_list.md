---
title: "[SOLVED] rebuilding Package Manager list"
date: 2008-10-09
forum: General Help
---

### Post by rMatey on 2008-10-09
I won't get into it, but I did something stoopid.  Anyhow in installing a program called pygtk, it didn't install.  So I was trying to manually install it, and screwed it up.

   Now whenever I try to run update or Synamptic Package Manager this is what I get. 
"..doctype not known on line 1 in sources.list /etc/apt/
sources.list.d/medibuntu.list
E: The list of sources could not be read
Goto the repository dialogue to correct the problem
E: cache->open()failed. please report.

  I tried to replace the /etc/apt/sources.list, with my backup, but that didn't work.

---

### Post by WWSmith36 on 2008-10-09
How did you try replacing with your backup sources.list
You need to do it as superuser.

---

### Post by rMatey on 2008-10-09
Yeah I tried that as a superuser.  Is there anyway to rebuild the Package Manager list from scratch???   I didn't have anything special in there, and the new version is coming out in a few weeks.  I was going to do a new install anyhow.

---

### Post by rMatey on 2008-10-09
:)

  This is how I learn  -  THE HARD WAY.

  Problem solved.  Somehow while on the internet and doing the changes that were necessary (Using Compiz cube)  I dragged something or whatever.  I had made another directory with a ".d" after it and had the internet pages stuck under the directory for /apt/etc/sources.list.d

  RM  the files and deleted the directory.  renamed the backup for sources.list.

  Works fine again.

:lolflag:

---

### Post by Sef on 2008-10-09
> Problem solved. 

For future reference, if your problem is solved, please go to Thread Tools > Mark this thread as solved.  (up at the top right above the first post of each page.)

---

