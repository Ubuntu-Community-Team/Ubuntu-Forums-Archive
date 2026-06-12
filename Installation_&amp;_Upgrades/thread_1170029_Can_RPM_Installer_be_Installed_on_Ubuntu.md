---
title: "Can RPM Installer be Installed on Ubuntu"
date: 2009-05-25
forum: Installation &amp; Upgrades
---

### Post by jim628 on 2009-05-25
Hi:

I am new to Ubuntu and just found out recently that Ubuntu/Debian does not
support .rpm package.  I also read about alien program.

My question is, can the RPM installer itself be installed on Ubuntu?
I have a software package where the installer relies heavily on
rpm command and it would be difficult for me to edit and modify the
installation program.  Any advice would be appreciated.


Thanks,
Jim

---

### Post by elliotn on 2009-05-25
Install something named ALIEN search it in your parkage manager

---

### Post by Girl™ on 2009-05-26
Yes, you can use alien to convert .rpm to .deb. Hower, I wouldn't recommend doing so unless you really, really need this package and can't find it in ubuntu.

---

### Post by Mark Phelps on 2009-05-26
While you certainly CAN use alien to convert rpms to debs (I know, I've done it), the problem you're likely to run into is unsatisfiable dependencies. Have personally run into several instances where the .rpm package had a very different name from the .deb equivalent primarily because library names were very different.

---

