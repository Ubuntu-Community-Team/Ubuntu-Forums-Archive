---
title: "Ascer Aspire One PyOpenGL Segfault"
date: 2009-06-08
forum: Hardware
---

### Post by mjrmua on 2009-06-08
I'm trying to run the Python Opengl example code on my Acer Aspire One and it is generating Segfaults ( when glutInitDisplayMode is called ).

The code works find on my desktop, and C++ openGL also work on the Aspire, so I'm assuming the problem is specific to PyOpenGL on the aspire.

Can anyone confirm this as happening on another aspire?
Are the any suggestions on how to debug this?

---

### Post by mjrmua on 2009-06-09
Seems this is a known bug in jaunty's PyOpenGL:
[https://bugs.launchpad.net/debian/+source/pyopengl/+bug/289925](https://bugs.launchpad.net/debian/+source/pyopengl/+bug/289925)

---

