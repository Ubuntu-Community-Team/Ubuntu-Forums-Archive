---
title: "A question about backing up"
date: 2008-07-12
forum: General Help
---

### Post by hcclnoodles on 2008-07-12
If I were to write a script to take a copy of all the configuration I have applied to my LAMP ubuntu web server over the period I have had it so that I could restore it to its original state from the CD what would I need to back up  ....apart from data files of course

1) the whole /etc folder
2) a full list of packages installed (**PS how do I get this ??**)
3) disk layout
4) IP addressing details & routing tables
5) php.ini, httpd.conf, includes etc


????? is there anything else I would need

---

### Post by Vivaldi Gloria on 2008-07-12
```
dpkg --get-selections
```

lists all installed packages.

If I were you I would build on the script here:

[http://ubuntuforums.org/showthread.php?t=792639](http://ubuntuforums.org/showthread.php?t=792639)

---

