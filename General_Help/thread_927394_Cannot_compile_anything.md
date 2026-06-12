---
title: "Cannot compile anything"
date: 2008-09-22
forum: General Help
---

### Post by chanklor on 2008-09-22
First of all, i'm newb.
When I try to compile something, this shows up

checking whether the C compiler (gcc  ) works... no
configure: error: installation or configuration problem: C compiler cannot create executables.

and it's is always the same.

sorry for my lack of english.

thanks for all.

---

### Post by pieoncar on 2008-09-22
Is gcc installed?

Try ```
sudo apt-get install gcc
``` and see if that installs it.

---

### Post by aragorn2909 on 2008-09-22
or perhaps a

```
sudo apt-get build-essential
```


But I must ask, what your attempting to build is not in the repositories?

---

### Post by MaxIBoy on 2008-09-22
```
sudo apt-get install build-essential automake fakeroot
```

Build-essential is just about required for everything. As far as I know, it includes make and gcc.

Automake and fakeroot aren't required by everything or even most things, but I've run into programs that require them to compile.

---

