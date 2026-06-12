---
title: "update problme with Nautilus"
date: 2009-03-31
forum: Installation &amp; Upgrades
---

### Post by edward1000 on 2009-03-31
hi all,

I install Ubuntu 8.04 after some days the funny pop up messenger appear with some updates for the program, I click and all the updates were get them from the repository after trying to install them this message pop up;

dpkg: parse error, in file  '/var/lib/dpkg/available'  near line 20261 package 'libnautilus-extension1':
field name '(Nautilus" must be followed by colon
E: sub-process /usr/bin/dpkg returned an error code (2) 

I try apt-get update...and the same 

any help will be appreciated.

E1000

---

### Post by Partyboi2 on 2009-03-31
Hi, there seems to be a problem with /var/lib/dpkg/available around line 20261. Can you open /var/lib/dpkg/available and post back here line 20261 as well as about 5 lines prior and 5 lines after 20261 . To do this press Alt+F2 and enter in the box
```
gksu gedit /var/lib/dpkg/available
``` then when gedit has opened the file, select  Search>Go to line and enter 20261.

---

### Post by edward1000 on 2009-03-31
Partyboi2

seems that removing 'available' and rename 'available-old' works I already update using the program.

Thanks all!

---

