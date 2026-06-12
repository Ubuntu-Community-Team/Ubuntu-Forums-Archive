---
title: "Problems installing Airsnort"
date: 2008-07-24
forum: General Help
---

### Post by LaGzo on 2008-07-24
Hi, I'm fairly new to Ubuntu. I'm trying to install Airsnort on my machine but I get an error.

This is what I get when trying to configure. Please help?

```
tony@tony-laptop:~/Desktop/airsnort-0.2.7e$ ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking whether to enable maintainer-specific portions of Makefiles... no
checking for style of include used by make... GNU
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking dependency style of gcc... gcc3
checking for library containing strerror... none required
checking for gcc... (cached) gcc
checking whether we are using the GNU C compiler... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking for gcc option to accept ANSI C... (cached) none needed
checking dependency style of gcc... (cached) gcc3
checking for gcc... (cached) gcc
checking whether we are using the GNU C compiler... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking for gcc option to accept ANSI C... (cached) none needed
checking dependency style of gcc... (cached) gcc3
checking how to run the C preprocessor... gcc -E
checking for egrep... grep -E
checking for ANSI C header files... yes
checking for pkg-config... /usr/bin/pkg-config
checking for gtk+-2.0 >= 2.0.0... Package gtk+-2.0 was not found in the pkg-config search path. Perhaps you should add the directory containing `gtk+-2.0.pc' to the PKG_CONFIG_PATH environment variable No package 'gtk+-2.0' found
configure: error: Library requirements (gtk+-2.0 >= 2.0.0) not met; consider adjusting the PKG_CONFIG_PATH environment variable if your libraries are in a nonstandard prefix so pkg-config can find them.
tony@tony-laptop:~/Desktop/airsnort-0.2.7e$ make
make: *** No targets specified and no makefile found.  Stop.

```

---

### Post by iaculallad on 2008-07-24
Doing it the easy way as Airsnort is available in the Repo:

```
sudo apt-get install airsnort
```

---

### Post by LaGzo on 2008-07-24
I'm running Hardy and it's not available in the repo. I think it was only on Gutsy, not sure. Thanks though.

---

### Post by LaGzo on 2008-07-24
Ok, I got it to install. Now I think I've run into another problem. I have a broadcom based card. bcm4311 to be exact. Might that not work with Airsnort? I'm pressing "Start" but nothing happenns.

---

### Post by gpracer01 on 2008-07-24
> **LaGzo said:**
> Ok, I got it to install. Now I think I've run into another problem. I have a broadcom based card. bcm4311 to be exact. Might that not work with Airsnort? I'm pressing "Start" but nothing happenns.

How did you finally get it installed? I'm having this same problem right now.

Thanks,

---

