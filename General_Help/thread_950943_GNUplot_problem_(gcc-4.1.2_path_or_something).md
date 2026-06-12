---
title: "GNUplot problem (gcc-4.1.2 path or something?)"
date: 2008-10-17
forum: General Help
---

### Post by sippyCUP on 2008-10-17
Hey guys, I installed the Ubuntu package for GNUplot in Ubuntu 8.04, but the install seems to be botched:

```
sippy@sippy:~$ gnuplot
gnuplot: /home/sippy/OpenFOAM/linux/gcc-4.1.2/lib/libstdc++.so.6: version `GLIBCXX_3.4.9' not found (required by /usr/lib/libwx_baseu-2.6.so.0)
```

OpenFOAM is a computational fluid dynamics code that has some tentacles in my .bashrc file, but I don't know why GNUplot is pointing towards a copy of gcc in OpenFOAM's directory. Furthermore, I don't know how to direct GNUplot to look at a good copy of whatever it wants - heck, I don't even know what it wants. The error is basically saying that gcc can't find GLIBCXX, right?

I'm sort of a beginning to this stuff and just recently successfully installed/debugged a software install using make, so if I need to read up on some stuff don't hesitate to tell me so (and what I'm not understanding).

Thanks for your time,
Eric

---

