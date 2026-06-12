---
title: "Need correct command for &quot;--with-apr&quot; option"
date: 2008-12-19
forum: Installation &amp; Upgrades
---

### Post by rpete on 2008-12-19
I downloaded apr  and apr-util in .tar.gz form and tried to configure them. At the end of the output for apr-util I got the message below about using a "--with" option.  Could someone please explain how to do this? 

richard@dell-desktop:~/Desktop$ cd apr-util-1.3.4
richard@dell-desktop:~/Desktop/apr-util-1.3.4$ ./configure
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking target system type... i686-pc-linux-gnu
checking for a BSD-compatible install... /usr/bin/install -c
checking for working mkdir -p... yes
APR-util Version: 1.3.4
checking for chosen layout... apr-util
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
Applying apr-util hints file rules for i686-pc-linux-gnu
checking for APR... no
configure: error: APR could not be located. Please use the --with-apr option.

---

### Post by taurus on 2008-12-19
Try compiling apr first since it looks like the apr-utils is looking for apr on your machine.  Otherwise, there is a libaprutils-dev in the repos.

---

### Post by rpete on 2008-12-19
> **taurus said:**
> Try compiling apr first since it looks like the apr-utils is looking for apr on your machine.  Otherwise, there is a libaprutils-dev in the repos.
Taurus, I tried both orders configuring, apr first and aprutil first and apr works but I still get the message above for aprutil.  It seems I need a special command? The libaprutil1-dev package is in the repository and has been applied. Any thoughts on what else to try?  I need apr because subversion won't install without it, I need subversion because something else I forget now won't install etc.

---

