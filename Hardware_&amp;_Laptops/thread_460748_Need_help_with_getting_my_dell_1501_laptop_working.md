---
title: "Need help with getting my dell 1501 laptop working"
date: 2007-06-01
forum: Hardware &amp; Laptops
---

### Post by stealthbox on 2007-06-01
this is what im trying to do

[http://www.berthon.eu/wiki/foss:ubuntu:wikishelf:hal:feisty](http://www.berthon.eu/wiki/foss:ubuntu:wikishelf:hal:feisty)

basicly i cant adjust the brightness of my backlight because of a bug , so this is the solution , i have to create DEB packages for libsmbios which is taken from gutsy.

every thing works up till the "sudo dpkg-buildpackage"

i put all 3 files in my home directory like it said

the error was
"sudo dpkg-buildpackage command not found"

what am i doing wrong ? 

is there an easier way of doing this ? is it possible that someone could create these deb files for me ?

i cant keep ubuntu on my laptop unless im able to adjust the backlight for more battery life.

heeeeelp

---

### Post by nyvalbanat on 2007-06-01
You can get dpkg-buildpackage using

sudo apt-get install dpkg-dev

Can you post back if you have any luck? I have the same machine and same problem.

---

### Post by redDEADresolve on 2007-06-03
use bios 1.7, howto on my blog

[www.ubuntu1501.blogspot.com](www.ubuntu1501.blogspot.com)

---

### Post by sandervdv on 2007-06-11
i presume that there is a fix in Gutsy?

---

