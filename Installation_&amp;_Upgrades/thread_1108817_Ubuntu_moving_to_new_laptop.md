---
title: "Ubuntu moving to new laptop?"
date: 2009-03-28
forum: Installation &amp; Upgrades
---

### Post by PolloE on 2009-03-28
Hi, I might be getting a new laptop in april before the official release of Ubuntu 9.4, so i wanted to know if i could:

1st, UpGrade my current Ubutnu 8.10 to 9.4 on my laptop, so i'd keep all my setting, users and apps, then install ubuntu 9.4 on the new laptop after that move the whole thing (from old laptop), with my apps, setting and files to the new laptop without having to re-install all the applications.

i do have an external harddrive (if that helps) plz answer before the release (cuz then this forums will be full of questions, always think ahead ;P)

THX!

---

### Post by zvacet on 2009-03-28
If I understand you you want to backup all system and install it on new laptop.if that is what you want then try [remastersys.]("http://www.geekconnection.org/remastersys/remastersystool.html")

---

### Post by sgosnell on 2009-03-28
There are a number of ways to do what you want.  I would suggest putting /home on its own partition, so that you can upgrade the / partition without affecting it.  Make a backup of /home to the external drive before doing any upgrades, of course.

---

### Post by PolloE on 2009-03-29
> **sgosnell said:**
> There are a number of ways to do what you want.  I would suggest putting /home on its own partition, so that you can upgrade the / partition without affecting it.  Make a backup of /home to the external drive before doing any upgrades, of course.

But wait, if i do that... i will keep my settings, and i will be able to put them in ubuntu 9.4? Like, cuz u see how some stuff will probably upgrade, like OpenOffice, but if i copy my ubuntu 8.4 home, and paste it over my ubuntu 9.4 /home all this software ubdates like OpenOffice or Gimp or whoknows would be downgraded wouldn't they?

---

### Post by sgosnell on 2009-03-29
/home only contains user data, not programs, unless you've installed them incorrectly.  Program files should live in the / hierarchy.  It is possible to install programs such as Open Office in /home, if you don't do the install as root, but it's not optimal.

---

### Post by PolloE on 2009-03-30
> **sgosnell said:**
> /home only contains user data, not programs, unless you've installed them incorrectly.  Program files should live in the / hierarchy.  It is possible to install programs such as Open Office in /home, if you don't do the install as root, but it's not optimal.

OK, thx for the tip, just one question, i noticed that u r testing 9.4, so If i downloaded right now, to test it, and then they find out there was major bugs (im gonna install 9.4 in my 40gb spare partition... lol) will there be an upgrade the 23rd april to upgrade all the buggy 9.4 ???


Thx!

---

### Post by sgosnell on 2009-03-30
To be pedantic, it's 9.04, not 9.4.  8)

Yes, the official release should be sometime next month, and should take care of most bugs.  I've found none so far.

---

