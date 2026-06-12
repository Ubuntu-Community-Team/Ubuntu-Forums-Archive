---
title: "C compiler cannot create executables"
date: 2009-04-21
forum: Installation &amp; Upgrades
---

### Post by rajashekar on 2009-04-21
hi, while i am installing the EMBOSS-6.0.1 it displays the following error:
 
biomics@biomics:~/Documents/EMBOSS-6.0.1$ ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking for gawk... (cached) mawk
checking for gcc... gcc
checking for C compiler default output file name...
configure: error: C compiler cannot create executables
See `config.log' for more details.

can you suggest me...

---

### Post by Mark Phelps on 2009-04-22
Check the log file, it should tell you specifically what is missing.

Also, check to see if you have the build-essential package installed.

---

### Post by oldos2er on 2009-04-22
> **rajashekar said:**
> hi, while i am installing the EMBOSS-6.0.1 it displays the following error:
 
biomics@biomics:~/Documents/EMBOSS-6.0.1$ ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking for gawk... (cached) mawk
checking for gcc... gcc
checking for C compiler default output file name...
configure: error: C compiler cannot create executables
See `config.log' for more details.

can you suggest me...

 Run this command in a terminal
```
sudo apt-get update && sudo apt-get install build-essential
```

---

