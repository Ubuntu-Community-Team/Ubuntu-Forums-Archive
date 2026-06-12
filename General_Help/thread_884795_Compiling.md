---
title: "Compiling"
date: 2008-08-09
forum: General Help
---

### Post by dgcarter on 2008-08-09
I need some help, I've been at this for hours and I can't figure it out...

I'm trying to compile and install MaNGOS WoW Server on my ubuntu 6.06 box.
I've just checked out the source from svn, but when I run

autoreconf --install --force

I get this

> root@wow-host:/opt/mangos/sources/mangos# autoreconf --install --force
/usr/share/aclocal/libmcrypt.m4:17: warning: underquoted definition of AM_PATH_LIBMCRYPT
  run info '(automake)Extending aclocal'
  or see [http://sources.redhat.com/automake/automake.html#Extending-aclocal](http://sources.redhat.com/automake/automake.html#Extending-aclocal)
/usr/share/aclocal/libmcrypt.m4:17: warning: underquoted definition of AM_PATH_LIBMCRYPT
  run info '(automake)Extending aclocal'
  or see [http://sources.redhat.com/automake/automake.html#Extending-aclocal](http://sources.redhat.com/automake/automake.html#Extending-aclocal)
configure.ac:182: error: possibly undefined macro: AC_TYPE_UINT64_T
      If this token and others are legitimate, please use m4_pattern_allow.
      See the Autoconf documentation.
autoreconf: /usr/bin/autoconf failed with exit status: 1
root@wow-host:/opt/mangos/sources/mangos#


and ideas?

Thanks

---

### Post by Sycron on 2008-08-09
It is NOT advised to run commands on a terminal with root privileges. It seems that you messed some steps of your tut.

My suggestion is to try again BUT from another tutorial...

---

### Post by mikjp on 2008-08-09
> **Sycron said:**
> It is NOT advised to run commands on a terminal with root privileges. 

Yes, but one needs root privileges (or sudo rights) to install software.

m

---

### Post by Sycron on 2008-08-09
If a user installs program with a root account there might apear profile problems ... I mean the application was installed for root and the profile file is in there and if the user run as a normal account there may be alot of problems .. i have those problems very often when i use third party softwares...

---

