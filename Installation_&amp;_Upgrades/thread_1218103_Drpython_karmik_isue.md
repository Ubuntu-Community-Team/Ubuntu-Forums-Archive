---
title: "Drpython karmik isue"
date: 2009-07-20
forum: Installation &amp; Upgrades
---

### Post by Azyl on 2009-07-20
Srr for my post didn`t know were to post this.

i`m having problem instaling DrPython on the new ubuntu 9.10 after upgrading and working on the bug with the nvidia driver i was really wainting to finish some projects of my on but i can`t get dr py to work again i have uninstaled and instaled again and all i get is this error:  fatal eror : Bitmap Directory (/usr/share/pyshared/drpython/bitmaps) does Not Exist. and i`ed checked it doesn`t exist. where can i get some help and support sorry for my english.

---

### Post by Fantasio_I on 2009-11-01
Drpython try to find in pyshared, but the files are in python-support, only do a symbolic link:

sudo ln -s /usr/share/python-support/drpython/drpython/ /usr/share/pyshared

---

### Post by David1965 on 2009-11-03
I had the same problem so thank you Fantasio_I for the fix.

---

### Post by crustyBarnacle on 2010-02-22
Fixed here also. Thanks Fantasio_I.

---

### Post by sblanzio on 2010-04-24
me too. thank you very much

---

