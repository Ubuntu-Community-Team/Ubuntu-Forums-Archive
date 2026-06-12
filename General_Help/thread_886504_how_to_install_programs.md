---
title: "how to install programs"
date: 2008-08-11
forum: General Help
---

### Post by ravindukelum on 2008-08-11
When I tried to installed software packages that come compressed ,Extract them I found  some install,make , configure files when gone through readme files found "make , make install" those terminal commands to use.But I tried all, gave message like couldn't find target .Is there any gui program that helps to install different kind of files easily.

---

### Post by purplepaint on 2008-08-11
Those files are for compiling the program from the source code yourself.

What are you trying to install?  You might be able to find it in **Applications - Add/Remove...** or **System - Administration - Synaptic Package Manager**.  These download and install all necessary files from the Ubuntu repositories.

---

### Post by thirddeep on 2008-08-11
If you really want to compile a program from a tar ball, the _general_ method is :

./configure
make
make install

You will however need the build-essential package first.

Thd.

---

