---
title: "strange partition info"
date: 2007-10-24
forum: Hardware &amp; Laptops
---

### Post by brickbat on 2007-10-24
Hi, my home partition is 13.5 gb.  df and gparted report this correctly. BUT even though I have only used about 350mb in my folders, nautilus is reporting that I only have 2.2 GB available.  11 GB is MISSING from my home folders.

---

### Post by brickbat on 2007-10-24
ok, I figured it out.

Here was the problem.  Baobab - the disk usage analyser runs as the current user - so the information it gives is pure rubbish.  I ran it as root and found a .trash-root folder that had an old user home folder in it.

I went in and actually deleted those files permanently and it was fixed.

---

