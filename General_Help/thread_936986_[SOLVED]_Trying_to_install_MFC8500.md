---
title: "[SOLVED] Trying to install MFC8500"
date: 2008-10-03
forum: General Help
---

### Post by rayboston on 2008-10-03
Hi Folks,

I'm new to Ubuntu but not so new to Unix.  I've installed Ubuntu on my Dell and I'm trying to install the printer drivers for my Brother MFC8500.  I've downloaded the LPR and CUPS .deb files from Brother, and I'm trying to install the LPR before the CUPS.  But when I try to install the LPR it appears that there is no LPD installed on this machine:
```

rays@office-ubuntu:~/Downloads$ sudo dpkg -i mfc8500lpr-1.1.2-1.i386.deb 
(Reading database ... 95938 files and directories currently installed.)
Preparing to replace mfc8500lpr 1.1.2-1 (using mfc8500lpr-1.1.2-1.i386.deb) ...
Unpacking replacement mfc8500lpr ...

Setting up mfc8500lpr (1.1.2-1) ...
mkdir: cannot create directory `/var/spool/lpd/MFC8500': No such file or directory
chown: cannot access `/var/spool/lpd/MFC8500': No such file or directory
chgrp: cannot access `/var/spool/lpd/MFC8500': No such file or directory
chmod: cannot access `/var/spool/lpd/MFC8500': No such file or directory


rays@office-ubuntu:~/Downloads$ cd /var/spool/lpd
bash: cd: /var/spool/lpd: No such file or directory

```

Any idea what I'm missing?

Thanks!

Ray

---

### Post by rayboston on 2008-10-03
I wonder if there is an LPR package I need to install?

---

### Post by rayboston on 2008-10-03
The solution was to go in and make all the missing directories before running the package tool.

---

