---
title: "Problem with C compiler"
date: 2008-09-22
forum: General Help
---

### Post by R2D2! on 2008-09-22
Why can't I build programs, such as Pidgin?
```
ilhuitemoc@ilhuitemoc-laptop:~/Aplicaciones/pidgin-2.5.1$ ./configure
checking build system type... i686-pc-linux-gnulibc1
checking host system type... i686-pc-linux-gnulibc1
checking target system type... i686-pc-linux-gnulibc1
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking for sed... /bin/sed
checking for gcc... gcc
checking for C compiler default output file name... 
configure: error: C compiler cannot create executables
See `config.log' for more details.
ilhuitemoc@ilhuitemoc-laptop:~/Aplicaciones/pidgin-2.5.1$ 

```

---

### Post by overdrank on 2008-09-22
Moved :)

Have you installed build-essentials?

---

### Post by ju2wheels on 2008-09-23
You probably have unresolved dependencies. 

Take it from me on this one... pidgin is a pain the butt to compile, I wouldnt waste your time. It has tons of dependencies, youll be there at least an hr trying to resolve them all. Use this instead [http://www.getdeb.net/release.php?id=3140](http://www.getdeb.net/release.php?id=3140) and do dpkg -i [list all 3 packages separated by a space] after you download the 3 packages.

---

### Post by jespdj on 2008-09-23
> **overdrank said:**
> Moved :)

Have you installed build-essentials?
It's not build-essential**s**, but build-essential (without s at the end). You need to install that package to be able to compile software properly:
```
sudo apt-get install build-essential
```

---

