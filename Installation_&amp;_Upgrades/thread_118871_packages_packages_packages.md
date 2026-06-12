---
title: "packages packages packages"
date: 2006-01-17
forum: Installation &amp; Upgrades
---

### Post by slowlearner on 2006-01-17
ie guyz!

does anyone here know how to list all installed packages
and write them to a text file????

thx :)

---

### Post by az on 2006-01-17
dpkg -l > file

---

### Post by rjwood on 2006-01-17
that's too technical for me

oops---azz to the rescue!!

---

### Post by gravediggers on 2006-01-17
Open terminal and at the command prompt type:
 
dpkg -l > filename
 
substituting for filename the file that you wish to ctreate, such as ~/pkglst which would create the file pkglst in your home directory.

---

### Post by slowlearner on 2006-01-17
thnx! :) btw, that was fast!

---

