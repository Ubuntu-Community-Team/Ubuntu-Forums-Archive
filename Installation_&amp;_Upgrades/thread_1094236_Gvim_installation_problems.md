---
title: "Gvim installation problems"
date: 2009-03-12
forum: Installation &amp; Upgrades
---

### Post by coolraghuram on 2009-03-12
Hi all,
  When i try to install the gvimusing the following command
         sudo apt-get install gvim

after the installation, when i try invoke gvim , it is giving 

"gvim: error while loading shared libraries: libgailutil.so.18: cannot open shared object file: No such file or directory"

help me to overcome it.

Thanks in advance

---

### Post by cyfur01 on 2009-03-12
Which version of Ubuntu are you running? I run 32-bit Intrepid and when I try to install **gvim**, it complains that it's only a virtual package provided by **vim-gnome** and **vim-gtk**. The proper package is **vim-gnome** which is also installed by **vim-full** (I'm not sure if these exists for your version and whether or not they would properly include the missing library).

Regardless, to fix the error message you are getting, I believe you want to install **libgail18**:
```

sudo apt-get install libgail18

```

---

