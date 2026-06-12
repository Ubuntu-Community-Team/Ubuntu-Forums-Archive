---
title: "trying to install dymo driver 1.4.0.5"
date: 2014-08-03
forum: Hardware
---

### Post by jgw on 2014-08-03
I have downloaded the driver gz file and have unzipped it to /Dymo/dymo-cups-drivers-1.4.0.5     I have read the documentation and also a variety of dymo topics on this forum.  My problem is that when I do the ./configure I get errors:
greg@greg-desktop:~/Dymo/dymo-cups-drivers-1.4.0.5$ ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
/home/greg/Dymo/dymo-cups-drivers-1.4.0.5/missing: Unknown `--run' option
Try `/home/greg/Dymo/dymo-cups-drivers-1.4.0.5/missing --help' for more information
configure: WARNING: `missing' script is too old or missing
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking for cups-config... no
checking for style of include used by make... GNU
checking for gcc... gcc
checking whether the C compiler works... yes
checking for C compiler default output file name... a.out
checking for suffix of executables... 
checking whether we are cross compiling... no
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking dependency style of gcc... gcc3
checking for cupsMarkOptions in -lcups... no
configure: error: Can't find cups library

I also tried: Try `/home/greg/Dymo/dymo-cups-drivers-1.4.0.5/missing --help' for more information
which got me a running ">"

According to my reading this was supposed to work - it did not.  

thank you.................

---

### Post by jgw on 2014-08-03
I installed libcupsimage2-dev and changed my ./configure command to "sudo ./configure and it worked!  Now all I have to do is figure out how to use what I successfully installed.  Anyway, I am going to mark this as installed.

---

