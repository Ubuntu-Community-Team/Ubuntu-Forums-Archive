---
title: "Problems with OpenOffice upgrade"
date: 2009-07-07
forum: Installation &amp; Upgrades
---

### Post by Jay--jay on 2009-07-07
Hello, 

I was trying to upgrade open office  and when installing the packages it all went black and my computer restarted. The installation was interrupted and to be able to install again I did: dpkg --configure -a as told. Then I got the following (in swedish, translation below): 

dpkg: tolkningsfel, i fil "/var/lib/dpkg/updates/0003" nära rad 6 paket "bsh":
 Filslut efter fältnamn "" 

swedish for (very freely translated) : 
dpkg: interpretation error in file "/var/lib/dpkg/updates/0003" close to row 6 package "bsh": file end after field name ""

How do I solve this? Seems to be some kind of deadlock. I can't reinstall until I have solved it but I must solve it in order to reinstall? The file is read only. Hope someone knows the solution.

---

### Post by Jay--jay on 2009-07-07
Solving my own problem by simply removing the files that caused the error. Beginners mistake, forgot the sudo before trying to rm the file.

---

