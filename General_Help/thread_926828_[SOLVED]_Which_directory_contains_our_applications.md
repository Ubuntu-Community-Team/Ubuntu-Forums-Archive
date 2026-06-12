---
title: "[SOLVED] Which directory contains our applications?"
date: 2008-09-22
forum: General Help
---

### Post by RonB123123 on 2008-09-22
Which directory contains our applications?

I tried looking for where Firefox resides by checking the properties of a shortcut but all the shortcut contained was the command "firefox".

---

### Post by John164918a on 2008-09-22
try /usr/bin

---

### Post by tuxxy on 2008-09-22
Try /usr/lib/

Also to locate an app yopu could use locate;

```
locate firefox
```

---

### Post by RonB123123 on 2008-09-22
Oh wow! Thank you very much!

---

### Post by kokkus on 2008-09-22
Execute files are located in the /bin directories
Icons are under /share/icons
help and sorce files are under /share
program files are under /lib.

You can locate all program files by using synatic package manager.
Search for the package (application) you would like to track, right-click and go to properties. You will then see all the files with locations listed under Installed files.

---

