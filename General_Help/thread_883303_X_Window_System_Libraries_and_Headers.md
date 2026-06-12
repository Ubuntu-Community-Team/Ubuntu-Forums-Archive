---
title: "X Window System Libraries and Headers"
date: 2008-08-07
forum: General Help
---

### Post by aalinovi on 2008-08-07
Can anyone tell me where in Ubuntu these are located?

I've searched the web and these forums to no avail. Apparently, I'm not the only Ubuntu user who has run into this problem but every suggestion I've come across has not helped.

checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking for style of include used by make... GNU
checking dependency style of gcc... gcc3
checking for a BSD-compatible install... /usr/bin/install -c
checking how to run the C preprocessor... gcc -E
checking for X... no
configure: error: BadWM requires the X Window System libraries and headers

---

### Post by damoxc on 2008-08-07
```
sudo apt-get install xserver-xorg-dev
```

That will install the xserver development files.

---

### Post by aalinovi on 2008-08-08
> **damoxc said:**
> ```
sudo apt-get install xserver-xorg-dev
```

That will install the xserver development files.

Tried it. No change. Same error message. Any other suggestions?
Thanks

---

### Post by ApEkV2 on 2009-09-21
Bump, I got the same problem.

Fixed it by installing libXxf86misc-dev from synaptic.

---

