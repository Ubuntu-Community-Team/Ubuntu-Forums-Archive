---
title: "ok to remove thunderbird-locale-en-gb ?"
date: 2008-10-28
forum: General Help
---

### Post by meonkeys on 2008-10-28
I noticed my package update applet trying to update a package called thunderbird-locale-en-gb. I don't have thunderbird installed--would it hurt anything to remove this package instead of updating it?

```
$ sudo apt-get autoremove thunderbird-locale-en-gb
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  language-support-en language-support-translations-en
  thunderbird-locale-en-gb
0 upgraded, 0 newly installed, 3 to remove and 15 not upgraded.
After this operation, 1016kB disk space will be freed.
Do you want to continue [Y/n]? 
```

I'm using an almost completely up-to-date Ubuntu 8.04.1 w/GNOME desktop.

---

