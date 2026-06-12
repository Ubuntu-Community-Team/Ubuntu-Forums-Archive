---
title: "*** No rule to make target"
date: 2009-01-16
forum: Installation &amp; Upgrades
---

### Post by fairy._.queen on 2009-01-16
Hi all!

I'm quite green on linux and getting quite desperate about a ndiswrapper-related make problem. I already posted in the "absolute beginner" section, but couldn't solve my problems and after searching all the forums I could find I think the only thing achieved was to corrupt my kernel. So, help me please! ;-((((

I'm trying to install ndiswrapper from source in a pc which has no internet connection of no kind. After doing the tar command I obtain a folder in which no .configure file is present.
When I run "make", as the readme say (the full sourceforge documentation is unavailable at the moment...), I get this error:

```
make[2]: *** No rule to make target `[name]/ndiswrapper-1.53/driver'.  Stop.
```

Can you please help me? Many thanks in advance!!!

---

### Post by taurus on 2009-01-16
Can you post the content of that readme or install file?

---

### Post by fairy._.queen on 2009-01-16
Sure:

```
The instructions below explain how to install ndiswrapper. This is
rather short version; more details about installation,
troubleshooting, FAQ etc. can be found in the Wiki at

http://ndiswrapper.sourceforge.net/wiki

Prerequisites 
=============

You need a recent kernel, at least 2.6.16, with header files for the
kernel. Make sure there is a link to the kernel source from the modules
directory. The command

  ls /lib/modules/`uname -r`/build

should have at least 'include' directory and '.config' file.

Downloading 
===========

Download the latest version of the ndiswrapper sources from here and
extract it with the command

  tar zxvf ndiswrapper-version.tar.gz

This will create ndiswrapper-version directory. Change to that
directory and run

  make uninstall
  make

Login as root and run
  make install
```

I have the prerequisites, the build-essential, source and headers.

---

### Post by taurus on 2009-01-16
Did you remember to change to the new directory first, **ndiswrapper-version**, before you ran the make command?

---

