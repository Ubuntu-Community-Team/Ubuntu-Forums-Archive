---
title: "make and make install"
date: 2008-09-12
forum: General Help
---

### Post by dapim on 2008-09-12
when i install a package in linux

i run make then make install 

why for? what the objective of make and make install??

---

### Post by ajmorris on 2008-09-12
> **dapim said:**
> when i install a package in linux

i run make then make install 

why for? what the objective of make and make install??

What you are running these on, is the source code. In your source code, you will find a 'Makefile'. This file contains the information needed to compile the source (that which make calls) and the information needed to copy over the files to target directories that have been compiled (that which make install calls). So 'make' compiles the source, and 'make install' just copies the compiled files to a target directory (also known as installing)

AJ

---

### Post by WRDN on 2008-09-12
It is recommended now to run "make" and "checkinstall" rather than "make install".
The reason to use "checkinstall" is that, it will automatically add an entry for the application to the package manager(s), allowing for easy removal at a later date.

---

