---
title: "Jaunty upgrade broke my Filezilla"
date: 2009-04-29
forum: Installation &amp; Upgrades
---

### Post by rohitmp on 2009-04-29
HI All,
I recently upgraded from 8.10 to 9.04 (Jaunty).
The upgrade broke my Filezilla. During clean up stage, it asked saying to uninstall obsolete packages, Filezilla was included in this list.
I accepted the poop so it uninstalled the Filezilla.
But now when i want to reinstall it through "Add/Remove" i get a error saying "FileZilla FTP client cannot be installed on your computer type (i386)".
What i am confused is my hardware did not change only the OS was upgraded.
So is this a bug on Ubuntu or Filezilla, is filezilla not yet supported on Jaunty ?
Is there a way to fix this and get filezilla installed again.

---

### Post by kostkon on 2009-04-29
Try installing it from the terminal and see if you'll get an error or if the installation will complete fine. Open a terminal (Applications &#8594; Accessories &#8594; Terminal) and give
```
sudo apt-get install filezilla
```
and give your password when asked.

---

### Post by kpkeerthi on 2009-04-29
[http://ubuntuforums.org/showthread.php?t=1133633]("http://ubuntuforums.org/showthread.php?t=1133633")

---

### Post by rohitmp on 2009-04-29
using sudo apt-get install filezilla, works like a charm.
Thanks for the instructions.:guitar:

---

