---
title: "HP Officejet Printing Errors"
date: 2010-05-15
forum: Hardware
---

### Post by jfleming9232 on 2010-05-15
Hey folks:

Just did a fresh install with Lucid about a week ago.  Today, I installed my printer and I can't get it to print.

HP Officejet J3680 which worked when I was running Karmic.
HPLIP installed, CUPS installed.

I am able to print test pages which shows me that the printer is recognized and communicating.  The installed showed no errors.  The results of hp-check are attached.

I noticed one item in particular:

error: User needs to be member of group 'lp' to enable print, scan & fax.
User member of group 'lpadmin'.


I'm not sure what groups are in reference to printing.  Any help would be greatly appreciated.

---

### Post by jfleming9232 on 2010-05-15
Another error I found was in the properties section of the printer and it reads:

Idle-Unable to read xref table

Hope this helps.

---

### Post by IcarusR on 2010-05-15
You need to add user to group 'lp'

```
sudo addgroup username groupname
```

---

### Post by jfleming9232 on 2010-05-15
Thanks....I'll give it a shot.

---

### Post by jfleming9232 on 2010-05-15
OK....now hpcheck shows that I am a member of that group, however, I am still unable to print.  Attached is the error log from my last print job.  I went ahead and did a complete purge and reinstall of hplip and cups. I now seem to be right back where I started.

Also, I am attaching the output of hp-check.

Any help would be greatly appreciated.

---

### Post by jfleming9232 on 2010-05-15
while perusing the error log, I came across this line:

D [15/May/2010:18:24:22 -0500] [Job 19] bc: error while loading shared libraries: libreadline.so.6: cannot open shared object file: No such file or directory

Interestingly, this is a similar error message I receive while trying to install medibuntu and getdep keys......

Does anyone know what "libreadline.so.6" is and where it should be located?

---

### Post by IcarusR on 2010-05-16
Libreadline description...

> The GNU readline library aids in the consistency of user interface
across discrete programs that need to provide a command line
interface.

The GNU history library provides a consistent user interface for
recalling lines of previously typed input.

libreadline.so.6 should be located /lib/libreadline.so.6

Search for libreadline in synaptics.

---

### Post by jfleming9232 on 2010-05-17
Results of locate libreadline:

> thad@thad-laptop:~$ locate readline
/usr/lib/libguilereadline-v-17.la
/usr/lib/libguilereadline-v-17.so.17
/usr/lib/libguilereadline-v-17.so.17.0.3
/usr/lib/python2.6/lib-dynload/readline.so
/usr/lib/python2.6/lib2to3/fixes/fix_xreadlines.py
/usr/lib/python2.6/lib2to3/fixes/fix_xreadlines.pyc
/usr/share/readline
/usr/share/doc/libreadline6
/usr/share/doc/readline-common
/usr/share/doc/libreadline6/README.Debian
/usr/share/doc/libreadline6/USAGE
/usr/share/doc/libreadline6/changelog.Debian.gz
/usr/share/doc/libreadline6/changelog.gz
/usr/share/doc/libreadline6/copyright
/usr/share/doc/libreadline6/examples
/usr/share/doc/libreadline6/inputrc.arrows
/usr/share/doc/libreadline6/examples/Inputrc
/usr/share/doc/readline-common/changelog.Debian.gz
/usr/share/doc/readline-common/copyright
/usr/share/doc/readline-common/inputrc.arrows
/usr/share/guile/1.8/ice-9/readline.scm
/usr/share/lintian/overrides/readline-common
/usr/share/man/man3/history.3readline.gz
/usr/share/man/man3/readline.3readline.gz
/usr/share/readline/inputrc
/var/lib/dpkg/info/libreadline6.list
/var/lib/dpkg/info/libreadline6.md5sums
/var/lib/dpkg/info/libreadline6.postinst
/var/lib/dpkg/info/libreadline6.postrm
/var/lib/dpkg/info/libreadline6.shlibs
/var/lib/dpkg/info/libreadline6.symbols
/var/lib/dpkg/info/readline-common.list
/var/lib/dpkg/info/readline-common.md5sums
/var/lib/dpkg/info/readline-common.postinst
/var/lib/dpkg/info/readline-common.postrm


No such file located in /lib/

---

### Post by jfleming9232 on 2010-05-17
Thanks for the help folks.  A quick search of synaptic and a reinstall of libread did the trick.

---

