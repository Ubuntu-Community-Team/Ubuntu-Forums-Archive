---
title: "What do I need to install before I can install dar?"
date: 2008-07-18
forum: General Help
---

### Post by Jordanwb on 2008-07-18
Ok so I heard about dar, and I want to give it a shot. With my short stint of trying to get Gentoo working on my PC, I've learned a bit about compiling and stuff like that. I downloaded the latest version of dar, extraced it to the desktop and opened a terminal to that folder. I ran "./configure" and I get this:

> jordanwb@JORDAN-CD3CDA3B:~/Desktop/dar-2.3.8$ ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking whether NLS is requested... yes
checking for msgfmt... no
checking for gmsgfmt... :
checking for xgettext... no
checking for msgmerge... no
checking for style of include used by make... GNU
checking for gcc... gcc
checking for C compiler default output file name...
configure: error: C compiler cannot create executables
See `config.log' for more details.
jordanwb@JORDAN-CD3CDA3B:~/Desktop/dar-2.3.8$


Now I probably have to install some extra packages but I don't know which ones. I read docs/index.html and it didn't tell me which ones.

---

### Post by jimv on 2008-07-18
do you have the build-essential package installed?

---

### Post by Jordanwb on 2008-07-18
Nope, installing now.

It's finished confugring:

>   LIBDAR parameters:
   Zlib compression (gzip)    : NO
   Libbz2 compression (bzip2) : NO
   Strong encryption support  : NO
   New blowfish implementation: NO
   Extended Attributes support: NO
   Large files support (> 2GB): YES
   ext2fs NODUMP flag support : NO
   Special allocation scheme  : YES
   Integer size used          : infinint
   Thread safe support        : YES

  DAR SUITE command line programs:
   Long options available : YES
   Building examples      : NO
   Building dar_static    : YES
   using upx at install   : NO
   building documentation : NO

jordanwb@JORDAN-CD3CDA3B:~/Desktop/dar-2.3.8$

How would I change the bzip2/gzip No's to Yes's? I'd prefer the one that compresses better.

---

