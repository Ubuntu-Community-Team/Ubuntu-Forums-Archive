---
title: "GCC C++ ABI Name Mangling"
date: 2008-11-25
forum: General Help
---

### Post by foufee on 2008-11-25
Hi,
  I'm trying to compile CppUnit on Kbuntu Intrepid, and during the configure step I'm getting this error, does any one have any idea why and how to solve it, it works fine on RHEL4.

"checking whether the compiler supports GCC C++ ABI name demangling... no"

Oh, it's a 64bit system too.

Cheers

Matthew

---

### Post by mali2297 on 2008-11-26
Why do you need to compile cppunit from source? There are already packages called **libcppunit-1.12-1** and **libcppunit-dev** in the repositories.

If you still want to compile cppunit (or anything else), check that you have **build-essential** installed.

---

